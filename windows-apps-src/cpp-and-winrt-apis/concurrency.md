---
author: stevewhims
description: Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.
title: Parallelität und asynchrone Vorgänge mit C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, parallelität, async, asynchron, asynchronität
ms.localizationpriority: medium
ms.openlocfilehash: fe43eaa233d3384eecb5e8755190efc1a109bbb9
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2855856"
---
# <a name="concurrency-and-asynchronous-operations-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a>Parallelität und asynchrone Vorgänge mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)
> [!NOTE]
> **Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a>Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen
Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet). Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert. Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt. Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge.

- [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),
- [**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),
- [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und
- [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).

Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert. C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur. Sie verwenden diese nicht direkt, aber dank dieser Struktur können Sie eine „co_await“-Anweisung schreiben, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asynchrone Vorgänge zurückgibt. Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.

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

Der Aufruf von **get** ermöglicht eine bequeme Codeerstellung und eignet sich perfekt für Konsolenapps oder Hintergrundthreads, in denen Sie möglicherweise keine Coroutine verwenden möchten. Sie ist jedoch weder parallel noch asynchron und folglich eignet sie sich nicht für einen UI-Thread (außerdem wird eine Assertion in nicht optimierten Builds ausgelöst, wenn Sie versuchen, sie dafür zu verwenden). Um Betriebssystem-Threads nicht daran zu hindern, andere nützliche Aufgaben zu erledigen, benötigen wir eine andere Technik.

## <a name="write-a-coroutine"></a>Schreiben einer Coroutine
C++/WinRT integriert C++ Coroutinen in das Programmiermodell, um eine natürliche Möglichkeit zu bieten, kooperativ auf ein Ergebnis zu warten. Sie können Ihre eigene asynchronen Windows-Runtime-Vorgänge erzeugen, indem Sie eine Coroutine schreiben. Im folgenden Codebeispiel ist **ProcessFeedAsync** die Coroutine.

> [!NOTE]
> **Get** -Funktion vorhanden ist, auf die C + / WinRT Projektion geben **Winrt::Windows::Foundation::IAsyncAction**, damit Sie die Funktion in eine beliebige C + anrufen können / WinRT-Projekt. Nicht finden Sie die Funktion als Mitglied der Schnittstelle [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) aufgeführt, da **Abrufen** nicht Teil der Anwendung binary-Schnittstelle (ABI) Fläche des tatsächlichen Windows-Runtime Typs **IAsyncAction**ist.

```cppwinrt
// main.cpp

#include "pch.h"
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Web.Syndication.h>
#include <iostream>

using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

void PrintFeed(SyndicationFeed const& syndicationFeed)
{
    for (SyndicationItem const& syndicationItem : syndicationFeed.Items())
    {
        std::wcout << syndicationItem.Title().Text().c_str() << std::endl;
    }
}

IAsyncAction ProcessFeedAsync()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;
    SyndicationFeed syndicationFeed{ co_await syndicationClient.RetrieveFeedAsync(rssFeedUri) };
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

Eine Coroutine ist eine Funktion, die angehalten und wieder fortgesetzt werden kann. Wenn die `co_await`-Anweisung In der **ProcessFeedAsync**-Coroutine oben erreicht ist, initiiert die Coroutine asynchron den **RetrieveFeedAsync**-Aufruf und unterbricht sich dann sofort selbst und gibt die Kontrolle an den Aufrufer zurück (was im obigen Beispiel **main** ist). **main** kann dann weiterarbeiten, während der Feed abgerufen und ausgegeben wird. Wenn das erledigt ist (wenn der **RetrieveFeedAsync**-Aufruf abgeschlossen ist), wird die **ProcessFeedAsync**-Coroutine bei der nächsten Anweisung fortgesetzt.

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

void PrintFeed(SyndicationFeed const& syndicationFeed)
{
    for (SyndicationItem const& syndicationItem : syndicationFeed.Items())
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

Wenn Sie einen Windows-Runtime-Typ asynchron zurückgeben, sollten Sie ein [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) oder ein [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgeben. Alle Erst- oder Drittanbieter-Laufzeitklassen sind qualifiziert, oder ein anderer Typ, der an oder von einer Windows-Runtime-Funktion übergeben werden kann (z.B. `int` oder **winrt::hstring**). Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie versuchen, einen dieser Typen für asychrone Vorgänge mit einem Nicht-Windows-Runtime-Typ zu verwenden.

Wenn eine Coroutine nicht mindestens eine `co_await`-Anweisung enthält, benötigt sie mindestens eine `co_return`- oder `co_yield`-Anweisung, um sich als Coroutine zu qualifizieren. Es gibt Fälle, in denen Ihre Coroutine einen Wert zurückgeben kann, ohne dass es zur Asynchronität kommt und ohne dass Kontext blockiert oder gewechselt wird. Hier ist ein solches Beispiel, das (beim zweiten oder nachfolgenden Aufruf) dafür einen Wert zwischenspeichert.

```cppwinrt
winrt::hstring m_cache;
 
IAsyncOperation<winrt::hstring> ReadAsync()
{
    if (m_cache.empty())
    {
        // Asynchronously download and cache the string.
    }
    co_return m_cache;
}
``` 

## <a name="asychronously-return-a-non-windows-runtime-type"></a>Asychrone Rückgabe eines Nicht-Windows-Runtime-Typs
Wenn Sie asynchron einen Typ zurückgeben, der *kein* Windows-Runtime-Typ ist, sollten Sie ein Parallel Patterns Library (PPL) [**concurrency::task**](/cpp/parallel/concrt/reference/task-class) zurückgeben. Wir empfehlen **concurrency::task**, weil es eine bessere Performance (und später eine bessere Kompatibilität) bietet als **std::future**.

> [!TIP]
> Wenn Sie `<pplawait.h>` einschließen, können Sie **concurrency::task** als Coroutinentyp verwenden.

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
    // Do other work here.
    std::wcout << firstTitleOp.get() << std::endl;
}
```

## <a name="parameter-passing"></a>Parameterübergabe
Für synchrone Funktionen sollten Sie standardmäßig `const&`-Parameter verwenden. Dadurch wird der Aufwand für Kopien vermieden (wozu Referenzzählung gehört, die zu miteinander verbundenen Erhöhungen und Verringerungen führt).

```cppwinrt
// Synchronous function.
void DoWork(Param const& value);
```

Sie können jedoch auf Probleme stoßen, wenn Sie einen Referenzparameter an eine Coroutine übergeben.

```cppwinrt
// NOT the recommended way to pass a value to a coroutine!
IASyncAction DoWorkAsync(Param const& value)
{
    // While it's ok to access value here...
    
    co_await DoOtherWorkAsync();

    // ...accessing value here carries no guarantees of safety.
}
```

In einer Coroutine verläuft die Ausführung bis zum ersten Anhaltepunkt synchron, wobei die Steuerung an den Aufrufer zurückgegeben wird. Wenn die Coroutine fortgesetzt wird, kann alles Mögliche mit dem Quellwert passiert sein, auf den ein Referenzparameter verweist. Aus Sicht der Coroutine hat ein Referenzparameter eine unkontrollierte Lebensdauer. Im obigen Beispiel können wir also problemlos auf *value* bis `co_await` zugreifen, nicht jedoch danach. Wir können *value* nicht problemlos an **DoOtherWorkAsync** übergeben, wenn das Risiko besteht, dass diese Funktion ihrerseits angehalten wird und bei Fortsetzen dann versucht, *value* zu verwenden. Damit die Parameter nach dem Anhalten und Fortsetzen ohne Probleme verwendet werden können, sollten Ihre Coroutinen standardmäßig „pass-by-value“ verwenden, um sicherzustellen, dass die Erfassung nach Wert erfolgt, und um Probleme mit der Lebensdauer zu vermeiden. Fälle, in denen Sie von dieser Vorgehensweise abweichen können, da Sie sicher sind, dass keine Probleme entstehen, sind eher selten.

```cppwinrt
// Coroutine
IASyncAction DoWorkAsync(Param value);
```

Es ist auch fraglich, ob die Übergabe nach Konstantenwert empfehlenswert ist (es sei denn, Sie möchten den Wert verschieben). Dies hat keine Auswirkungen auf den Quellwert, von dem Sie eine Kopie erstellen, es macht aber die Intention klar und hilft, wenn Sie die Kopie versehentlich ändern.
    
```cppwinrt
// coroutine with strictly unnecessary const (but arguably good practice).
IASyncAction DoWorkAsync(Param const value);
```

Weitere Informationen finden Sie unter [Standard-Arrays und -Vektoren](std-cpp-data-types.md#standard-arrays-and-vectors). Hier wird beschrieben, wie Sie einen Standardvektor in einem asynchronen Aufrufer übergeben.

## <a name="offloading-work-onto-the-windows-thread-pool"></a>Auslagern von Aufgaben an den Windows-Threadpool
Bevor Sie rechengebundene Arbeiten in einer Coroutine ausführen, müssen Sie die Ausführung an den Aufrufer zurückgegeben, damit der Aufrufer nicht blockiert wird (anders ausgedrückt, sollte ein Anhaltepunkt eingefügt werden). Wenn Sie dies noch nicht durch ein `co-await` anderer Vorgänge tun, können Sie ein `co-await` für die Funktion **winrt::resume_background** ausführen. Dadurch wird die Steuerung an den Aufrufer zurückgegeben, und unmittelbar danach wird die Ausführung auf einem Threadpoolthread fortgesetzt.

Der in der Implementierung verwendete Threadpool wird auf niedriger Ebene ausgeführt [Windows-Threadpool](https://msdn.microsoft.com/library/windows/desktop/ms686766), sodass er optimal effizient ist.

```cppwinrt
IAsyncOperation<uint32_t> DoWorkOnThreadPoolAsync()
{
    co_await winrt::resume_background(); // Return control; resume on thread pool.

    uint32_t result;
    for (uint32_t y = 0; y < height; ++y)
    for (uint32_t x = 0; x < width; ++x)
    {
        // Do compute-bound work here.
    }
    co_return result;
}
```

## <a name="programming-with-thread-affinity-in-mind"></a>Programmieren mit Threadaffinität
Dieses Szenario erweitert das vorherige. Sie lagern einige Aufgaben an den Threadpool aus, möchten dann aber den Fortschritt auf der Benutzeroberfläche anzeigen.

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    textblock.Text(L"Done!"); // Error: TextBlock has thread affinity.
}
```

Der obige Code löst eine [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread)-Ausnahme aus, da ein **TextBlock** von dem Thread, der ihn erstellt hat (UI-Thread), aktualisiert werden muss. Eine Lösung besteht darin, den Threadkontext zu erfassen, in dem unsere Coroutine ursprünglich aufgerufen wurde. Instanziieren Sie ein **winrt::apartment_context**-Objekt, und führen Sie dann ein `co_await` dafür aus.

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    winrt::apartment_context ui_thread; // Capture calling context.

    co_await winrt::resume_background();
    // Do compute-bound work here.

    co_await ui_thread; // Switch back to calling context.

    textblock.Text(L"Done!"); // Ok if we really were called from the UI thread.
}
```

Solange die oben genannte Coroutine vom UI-Thread aufgerufen wird, der den **TextBlock** erstellt hat, funktioniert dieses Verfahren. Es wird einige Fälle in Ihrer App geben, in denen Sie dessen sicher sind.

> [!NOTE]
> **Das folgende Codebeispiel bezieht sich auf die Vorabversion, die vor der kommerziellen Freigabe grundlegend geändert werden kann. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.**

Für eine allgemeinere Lösung zur Aktualisierung der Benutzeroberfläche, die auch Fälle abdeckt, in denen Sie bezüglich des aufrufenden Threads unsicher sind, können Sie das [Windows10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) oder höher installieren. Sie können dann ein `co-await` für die Funktion **winrt::resume_foreground** ausführen, um zu einem bestimmten Vordergrundthread zu wechseln. Im folgenden Codebeispiel geben Sie den Vordergrundthread durch Übergabe des Dispatcherobjekts an, das mit dem **TextBlock** verknüpft ist (durch Zugriff auf die zugehörige [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher)-Eigenschaft). Die Implementierung von **winrt::resume_foreground** ruft [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) für dieses Dispatcherobjekt auf, um die Aufgaben auszuführen, die danach in der Coroutine folgen.

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    co_await winrt::resume_foreground(textblock.Dispatcher()); // Switch to the foreground thread associated with textblock.

    textblock.Text(L"Done!"); // Guaranteed to work.
}
```

## <a name="important-apis"></a>Wichtige APIs
* [concurrency::task](/cpp/parallel/concrt/reference/task-class)
* [IAsyncAction](/uwp/api/windows.foundation.iasyncaction)
* [IAsyncActionWithProgress&lt;TProgress&gt;](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [IAsyncOperation&lt;TResult&gt;](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [SyndicationClient::RetrieveFeedAsync](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [SyndicationFeed](/uwp/api/windows.web.syndication.syndicationfeed)

## <a name="related-topics"></a>Verwandte Themen
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
* [Standard C++ Datentypen und C++/WinRT](std-cpp-data-types.md)