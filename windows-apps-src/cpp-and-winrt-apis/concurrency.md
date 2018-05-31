---
author: stevewhims
description: Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.
title: Parallelität und asynchrone Vorgänge mit C++/WinRT
ms.author: stwhi
ms.date: 04/23/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, parallelität, async, asynchron, asynchronität
ms.localizationpriority: medium
ms.openlocfilehash: 3af9125abc3abf41327f5b49e6a05d81e214f89f
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1831834"
---
# <a name="concurrency-and-asynchronous-operations-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Parallelität und asynchrone Vorgänge mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)
Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a>Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen
Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet). Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert. Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt. Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge. Diese sind:

- [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),
- [**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),
- [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und
- [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).

Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert. C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur. Sie verwenden diese nicht direkt, aber dank dieser Struktur können Sie eine **co_await**-Anweisung schreiben, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asychrone Vorgänge zurückgibt. Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.

Ein Beispiel für eine asynchrone Windows-Funktion ist [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), die ein Objekt für einen asynchronen Vorgang vom Typ [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgibt. Betrachten wir einige (blockierende und nicht blockierende) Möglichkeiten der Verwendung von C++/WinRT, um eine solche API aufzurufen.

## <a name="block-the-calling-thread"></a>Den aufrufenden Thread blockieren
Das folgende Codebeispiel erhält ein Objekt für asynchronen Vorgänge von **RetrieveFeedAsync** und ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren, bis die Ergebnisse des asynchronen Vorgangs vorliegen.

```cppwinrt
// main.cpp

#include "pch.h"
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

void ProcessFeed()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
    // use syndicationFeed.
}

int main()
{
    winrt::init_apartment();
    ProcessFeed();
}
```

Der Aufruf von **get** ermöglicht eine bequeme Codeerstellung. Als kooperativ kann man ihn jedoch nicht bezeichnen. Es arbeitet weder gleichzeitig noch asynchron. Um Betriebssystem-Threads nicht daran zu hindern, andere nützliche Aufgaben zu erledigen, benötigen wir eine andere Technik.

## <a name="write-a-coroutine"></a>Schreiben einer Coroutine
C++/WinRT integriert C++ Coroutinen in das Programmiermodell, um eine natürliche Möglichkeit zu bieten, kooperativ auf ein Ergebnis zu warten. Sie können Ihre eigene asynchronen Windows-Runtime-Vorgänge erzeugen, indem Sie eine Coroutine schreiben. Im folgenden Codebeispiel ist **ProcessFeedAsync** die Coroutine.

```cppwinrt
// main.cpp

#include "pch.h"
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
#include <iostream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

void PrintFeed(SyndicationFeed syndicationFeed)
{
    for (SyndicationItem syndicationItem : syndicationFeed.Items())
    {
        std::wcout << syndicationItem.Title().Text().c_str() << std::endl;
    }
}

IAsyncAction ProcessFeedAsync()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    SyndicationFeed syndicationFeed = co_await syndicationClient.RetrieveFeedAsync(rssFeedUri);
    PrintFeed(syndicationFeed);
}

int main()
{
    winrt::init_apartment();

    auto processOp = ProcessFeedAsync();
    // do other work while the feed is being printed.
    processOp.get(); // no more work to do; call get() so that we see the printout before the application exits.
}
```

Eine Coroutine ist eine Funktion, die angehalten und wieder fortgesetzt werden kann. Wenn die **co_await**-Anweisung In der **ProcessFeedAsync**-Coroutine oben erreicht ist, initiiert die Coroutine asynchron den **RetrieveFeedAsync**-Aufruf und unterbricht sich dann sofort selbst und gibt die Kontrolle an den Aufrufer zurück (was im obigen Beispiel **main** ist). **main** kann dann weiterarbeiten, während der Feed abgerufen und ausgegeben wird. Wenn das erledigt ist (wenn der **RetrieveFeedAsync**-Aufruf abgeschlossen ist), wird die **ProcessFeedAsync**-Coroutine bei der nächsten Anweisung fortgesetzt.

Sie können eine Coroutine in anderen Coroutinen zusammenfassen. Oder Sie können **get** zur Blockierung aufrufen und warten, bis sie abgeschlossen ist (und das Ergebnis erhalten, wenn es eines gibt). Oder Sie können sie an eine andere Programmiersprache übergeben, die Windows-Runtime unterstützt.

Es ist auch möglich, die Completed- und/oder Progress-Ereignisse von asynchronen Aktionen und Vorgängen mit Hilfe von Delegaten zu verarbeiten. Details und Codebeispiele finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).

## <a name="asychronously-return-a-windows-runtime-type"></a>Asychrone Rückgabe eines Windows-Runtime-Typs
In diesem nächsten Beispiel verpacken wir einen Aufruf von **RetrieveFeedAsync** für eine bestimmte URI, um uns eine **RetrieveBlogFeedAsync**-Funktion zu holen, die asynchron ein [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed) zurückgibt.

```cppwinrt
// main.cpp

#include "pch.h"
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
#include <iostream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

void PrintFeed(SyndicationFeed syndicationFeed)
{
    for (SyndicationItem syndicationItem : syndicationFeed.Items())
    {
        std::wcout << syndicationItem.Title().Text().c_str() << std::endl;
    }
}

IAsyncOperationWithProgress<SyndicationFeed, RetrievalProgress> RetrieveBlogFeedAsync()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    return syndicationClient.RetrieveFeedAsync(rssFeedUri);
}

int main()
{
    winrt::init_apartment();

    auto feedOp = RetrieveBlogFeedAsync();
    // do other work.
    PrintFeed(feedOp.get());
}
```

Im obigen Beispiel gibt **RetrieveBlogFeedAsync** ein **IAsyncOperationWithProgress** zurück, das sowohl einen Progress- als auch einen Return-Wert hat. Wir können andere Arbeiten durchführen, während **RetrieveBlogFeedAsync** sein Ding macht und den Feed abruft. Dann rufen wir das **get**-Objekt des asynchronen Vorgangs auf, um es zu blockieren, warten, bis es abgeschlossen ist, und erhalten dann die Ergebnisse des Vorgangs.

Wenn Sie einen Windows-Runtime-Typ asynchron zurückgeben (unabhängig davon, ob es sich um einen internen oder einen Drittanbietertyp handelt), sollten Sie ein [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) oder ein [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgeben.

Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie versuchen, einen dieser Typen für asychrone Vorgänge mit einem Nicht-Windows-Runtime-Typ zu verwenden.

## <a name="asychronously-return-a-non-windows-runtime-type"></a>Asychrone Rückgabe eines Nicht-Windows-Runtime-Typs
Wenn Sie asynchron einen Typ zurückgeben, der *kein* Windows-Runtime-Typ ist, sollten Sie ein Parallel Patterns Library (PPL) [**Task**](https://msdn.microsoft.com/library/hh750113)zurückgeben. Wir empfehlen **task**, weil es eine bessere Performance (und später eine bessere Kompatibilität) bietet als **std::future**.

```cppwinrt
// main.cpp

#include "pch.h"
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
#include <iostream>
#include <ppltasks.h>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

concurrency::task<std::wstring> RetrieveFirstTitleAsync()
{
    return concurrency::create_task([]
    {
        Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
        SyndicationClient syndicationClient;
        SyndicationFeed syndicationFeed = syndicationClient.RetrieveFeedAsync(rssFeedUri).get();
        return std::wstring{ syndicationFeed.Items().GetAt(0).Title().Text() };
    });
}

int main()
{
    winrt::init_apartment();

    auto firstTitleOp = RetrieveFirstTitleAsync();
    // do other work.
    std::wcout << firstTitleOp.get() << std::endl;
}
```

## <a name="important-apis"></a>Wichtige APIs
* [concurrency::task](https://msdn.microsoft.com/library/hh750113)
* [IAsyncAction](/uwp/api/windows.foundation.iasyncaction)
* [IAsyncActionWithProgress&lt;TProgress&gt;](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [IAsyncOperation&lt;TResult&gt;](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [SyndicationClient::RetrieveFeedAsync](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [SyndicationFeed](/uwp/api/windows.web.syndication.syndicationfeed)
