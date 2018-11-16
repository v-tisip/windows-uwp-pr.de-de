---
author: stevewhims
description: Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.
title: Parallelität und asynchrone Vorgänge mit C++/WinRT
ms.author: stwhi
ms.date: 10/27/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, parallelität, async, asynchron, asynchronität
ms.localizationpriority: medium
ms.openlocfilehash: 18eddbc9356f126e887ae2731ea87381352ea061
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6981511"
---
# <a name="concurrency-and-asynchronous-operations-with-cwinrt"></a>Parallelität und asynchrone Vorgänge mit C++/WinRT

Dieses Thema zeigt, in denen Sie beide können, Methoden erstellen und nutzen asynchrone Windows-Runtime-Objekte mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a>Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen

Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet). Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert. Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt. Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge.

- [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),
- [**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),
- [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und
- [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).

Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert. C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur. Sie verwenden diese nicht direkt, aber Dank dieser Struktur können Sie können Schreiben einer `co_await` -Anweisung ein, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asychrone Vorgänge zurückgibt. Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.

Ein Beispiel für eine asynchrone Windows-Funktion ist [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), die ein Objekt für einen asynchronen Vorgang vom Typ [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgibt. Betrachten wir einige Methoden&mdash;ersten blockieren, und klicken Sie dann nicht blockierende&mdash;der Verwendung von C++ / WinRT, um eine solche API aufzurufen.

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
    SyndicationFeed syndicationFeed{ syndicationClient.RetrieveFeedAsync(rssFeedUri).get() };
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
> Die **get** -Funktion vorhanden ist, auf der C++ / WinRT-Projektion geben **Winrt::Windows::Foundation::IAsyncAction**, damit Sie die Funktion in jeder C++ aufrufen können / WinRT-Projekt. Nicht finden Sie die Funktion aufgeführt, die als Mitglied der [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) -Schnittstelle, da **erhalten** nicht der Application binary Interface (ABI) Fläche des tatsächlichen Windows-Runtime-Typs **IAsyncAction**gehört.

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

    auto processOp{ ProcessFeedAsync() };
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

    auto feedOp{ RetrieveBlogFeedAsync() };
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
        SyndicationFeed syndicationFeed{ syndicationClient.RetrieveFeedAsync(rssFeedUri).get() };
        return std::wstring{ syndicationFeed.Items().GetAt(0).Title().Text() };
    });
}

int main()
{
    winrt::init_apartment();

    auto firstTitleOp{ RetrieveFirstTitleAsync() };
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

Eine Coroutine ist eine Funktion wie jede andere darin, dass ein Aufrufer blockiert werden, bis eine Funktion ausführen, es zurückgegeben werden. Die erste Möglichkeit für eine Coroutine zurückgegeben wird das erste `co_await`, `co_return`, oder `co_yield`.

Bevor Sie dies tun also rechengebundene arbeiten in einer Coroutine, müssen Sie Ausführung an den Aufrufer zurückgegeben (anders ausgedrückt, sollte ein Anhaltepunkt), damit der Aufrufer nicht blockiert wird. Wenn Sie nicht bereits durch dies noch `co_await`- Wert einen anderen Vorgang, Sie können `co_await` die [**resume_background**](/uwp/cpp-ref-for-winrt/resume-background) -Funktion. Dadurch wird die Steuerung an den Aufrufer zurückgegeben, und unmittelbar danach wird die Ausführung auf einem Threadpoolthread fortgesetzt.

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

Der obige Code löst eine [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread)-Ausnahme aus, da ein **TextBlock** von dem Thread, der ihn erstellt hat (UI-Thread), aktualisiert werden muss. Eine Lösung besteht darin, den Threadkontext zu erfassen, in dem unsere Coroutine ursprünglich aufgerufen wurde. Dazu ein [**WinRT:: apartment_context**](/uwp/cpp-ref-for-winrt/apartment-context) -Objekt zu instanziieren, Hintergrundarbeiten, und klicken Sie dann `co_await` der **Apartment_context** zurück an den aufrufenden Kontext zu wechseln.

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

Für eine allgemeinere Lösung zur Aktualisierung der Benutzeroberfläche, die auch Fälle abdeckt, in denen Sie bezüglich des aufrufenden Threads unsicher sind, können Sie `co_await` die [**resume_foreground**](/uwp/cpp-ref-for-winrt/resume-foreground) -Funktion, die zu einem bestimmten Vordergrundthread zu wechseln. Im folgenden Codebeispiel geben Sie den Vordergrundthread durch Übergabe des Dispatcherobjekts an, das mit dem **TextBlock** verknüpft ist (durch Zugriff auf die zugehörige [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher)-Eigenschaft). Die Implementierung von **winrt::resume_foreground** ruft [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) für dieses Dispatcherobjekt auf, um die Aufgaben auszuführen, die danach in der Coroutine folgen.

```cppwinrt
#include <winrt/Windows.UI.Core.h> // necessary in order to use winrt::resume_foreground.
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    co_await winrt::resume_foreground(textblock.Dispatcher()); // Switch to the foreground thread associated with textblock.

    textblock.Text(L"Done!"); // Guaranteed to work.
}
```

## <a name="execution-contexts-resuming-and-switching-in-a-coroutine"></a>Ausführung Kontexten, fortsetzen und wechseln in einer coroutine

Nachdem ein Anhaltepunkt in einer Coroutine, der ursprüngliche Ausführungsthread möglicherweise verschwindet, und Wiederaufnahme auftreten auf jedem Thread Grob gesagt (anders ausgedrückt, jedem Thread möglicherweise die **Completed** -Methode aufrufen für den asynchronen Vorgang).

Wenn Sie allerdings Sie `co_await` keines der vier Windows-Runtime-Typen für asynchrone Vorgänge (**IAsyncXxx**), dann C++ / WinRT erfasst den aufrufenden Kontext an dem Punkt Sie `co_await`. Und es wird sichergestellt, dass Sie weiterhin auf diesen Kontext arbeiten, wenn die Fortsetzung fortgesetzt wird. C++ / WinRT dazu überprüfen, ob Sie bereits auf dem aufrufenden Kontext sind und, falls nicht, zu wechseln. Würden Sie in einem Singlethread-Apartment (STA) Thread vor dem `co_await`, und klicken Sie dann Sie auf das gleiche Konto aufwenden; werden würden Sie in einem Multithread-(MTA) Apartmentthread vor dem `co_await`, und Sie auf einem aufwenden werden.

```cppwinrt
IAsyncAction ProcessFeedAsync()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;

    // The thread context at this point is captured...
    SyndicationFeed syndicationFeed{ co_await syndicationClient.RetrieveFeedAsync(rssFeedUri) };
    // ...and is restored at this point.
}
```

Der Grund, Sie können dieses Verhalten abhängig ist, da C++ / WinRT stellt Code diese Typen für Windows-Runtime-asynchrone Vorgänge für die Unterstützung der C++-Coroutine-Sprache angepasst werden kann (diese Teile des Codes werden Wait Adapter genannt). Die restlichen awaitable Typen in C++ / WinRT sind einfach Threadpool Wrapper bzw. Helpers; So führen sie auf den Threadpool.

```cppwinrt
using namespace std::chrono;
IAsyncOperation<int> return_123_after_5s()
{
    // No matter what the thread context is at this point...
    co_await 5s;
    // ...we're on the thread pool at this point.
    co_return 123;
}
```

Wenn Sie `co_await` eine andere Art&mdash;sogar innerhalb einer C++ / WinRT-Coroutine-Implementierung&mdash;und dann eine andere Bibliothek die Adapter enthält, und um zu verstehen, was diese Adapter hinsichtlich der Wiederaufnahme und Kontext tun müssen.

Um Kontextwechsel auf ein Minimum zu halten, können Sie einige der Techniken verwenden, die wir bereits in diesem Thema gesehen haben. Betrachten wir einige Illustrationen an. In diesem nächsten Beispiel Pseudocode zeigen wir den Umriss des ein Ereignishandler, der Ruft eine Windows-Runtime-API, um ein Bild zu laden, fällt in einem Hintergrundthread, um das Bild zu verarbeiten und gibt anschließend an den UI-Thread, um das Bild in der Benutzeroberfläche anzuzeigen.

```cppwinrt
#include <winrt/Windows.UI.Core.h> // necessary in order to use winrt::resume_foreground.
IAsyncAction MainPage::ClickHandler(IInspectable /* sender */, RoutedEventArgs /* args */)
{
    // We begin in the UI context.

    // Call StorageFile::OpenAsync to load an image file.

    // The call to OpenAsync occurred on a background thread, but C++/WinRT has restored us to the UI thread by this point.

    co_await winrt::resume_background();

    // We're now on a background thread.

    // Process the image.

    co_await winrt::resume_foreground(this->Dispatcher());

    // We're back on MainPage's UI thread.

    // Display the image in the UI.
}
```

In diesem Szenario besteht ein wenig Ineffiency, um den Aufruf von **StorageFile::OpenAsync**. Es gibt ein erforderlichen Kontextwechsel in einen Hintergrund thread (so dass der Handler Ausführung an den Aufrufer zurückgegeben werden kann), bei Wiederaufnahme nach die C++ / WinRT den UI-Thread-Kontext wiederhergestellt. Aber in diesem Fall ist es nicht erforderlich, als dem UI-Thread, bis wir etwa zum Aktualisieren der Benutzeroberfläche sind. Weitere Windows-Runtime-APIs *vor dem* Aufruf an **resume_background**, die nicht mehr erforderlich und gleichzeitiges Kontextwechsel rufen wir, die wir erleiden. Die Lösung wird nicht *Alle* Windows-Runtime-APIs davor aufzurufen. Verschieben sie alle nach der **resume_background**.

```cppwinrt
#include <winrt/Windows.UI.Core.h> // necessary in order to use winrt::resume_foreground.
IAsyncAction MainPage::ClickHandler(IInspectable /* sender */, RoutedEventArgs /* args */)
{
    // We begin in the UI context.

    co_await winrt::resume_background();

    // We're now on a background thread.

    // Call StorageFile::OpenAsync to load an image file.

    // Process the image.

    co_await winrt::resume_foreground(this->Dispatcher());

    // We're back on MainPage's UI thread.

    // Display the image in the UI.
}
```

Wenn Sie etwas mehr erweitert, und Sie Ihre eigenen schreiben möchten await Adapter. Beispielsweise, wenn Sie möchten eine `co_await` auf demselben Thread fortgesetzt, die auf die Async-Aktion abgeschlossen ist (also, es ist keine Kontextwechsel), und klicken Sie dann durch das Schreiben begonnen werden konnte await-Adapter ähnlich wie unten dargestellt.

> [!NOTE]
> Im folgenden Codebeispiel wird nur Bildungseinrichtungen zu bereitgestellt. Es ist, die Ihnen den Einstieg erleichtern Kenntnisse await wie Adapter arbeiten. Wenn Sie dieses Verfahren in Ihre eigenen Codebasis verwenden möchten, dann wir empfehlen, dass Sie entwickeln und Testen Ihre eigenen await Adapter Struct(s). Sie könnten z. B. **Complete_on_any**, **Complete_on_current**und **complete_on(dispatcher)** schreiben. Berücksichtigen Sie auch die Vorlagen, die den Typ **IAsyncXxx** als Template-Parameter nutzen, sie zu gestalten.

```cppwinrt
struct no_switch
{
    no_switch(Windows::Foundation::IAsyncAction const& async) : m_async(async)
    {
    }

    bool await_ready() const
    {
        return m_async.Status() == Windows::Foundation::AsyncStatus::Completed;
    }

    void await_suspend(std::experimental::coroutine_handle<> handle) const
    {
        m_async.Completed([handle](Windows::Foundation::IAsyncAction const& /* asyncInfo */, Windows::Foundation::AsyncStatus const& /* asyncStatus */)
        {
            handle();
        });
    }

    auto await_resume() const
    {
        return m_async.GetResults();
    }

private:
    Windows::Foundation::IAsyncAction const& m_async;
};
```

Zu verstehen, wie die **Nicht_wechseln** verwenden await-Adapter, müssen zunächst, die wissen, wann der C++ Compiler eine `co_await` Ausdruck nach Funktionen sucht **Await_ready**, **Await_suspend**und **Await_resume**aufgerufen. C++ / WinRT-Bibliothek bietet diese Funktionen so, dass Sie angemessene Verhalten standardmäßig wie folgt aus.

```cppwinrt
IAsyncAction async{ ProcessFeedAsync() };
co_await async;
```

Verwenden der **Nicht_wechseln** "await"-Adapter, der gerade ändern die Art der, `co_await` Ausdruck zwischen **IAsyncXxx** und **Nicht_wechseln**wie folgt aus.

```cppwinrt
IAsyncAction async{ ProcessFeedAsync() };
co_await static_cast<no_switch>(async);
```

Anschließend sucht anstelle der Suche nach der drei **Await_xxx** -Funktionen, die **IAsyncXxx**entsprechen, der C++ Compiler Funktionen, die **Nicht_wechseln**entsprechen.

## <a name="canceling-an-asychronous-operation-and-cancellation-callbacks"></a>Abbrechen eines Vorgangs asychrone und Abbruch-Rückrufe

Die Windows-Runtime-Features für die asynchrone Programmierung können Sie eine Flight asynchrone Aktion oder den Vorgang abbrechen. Hier ist ein Beispiel, das [**StorageFolder::GetFilesAsync**](/uwp/api/windows.storage.storagefolder.getfilesasync) rufen Sie eine große Sammlung von Dateien aufruft, und es speichert das resultierende asynchronen Vorgangs-Objekt in einem Datenmember. Der Benutzer hat die Möglichkeit, den Vorgang abzubrechen.

```cppwinrt
// MainPage.xaml
...
<Button x:Name="workButton" Click="OnWork">Work</Button>
<Button x:Name="cancelButton" Click="OnCancel">Cancel</Button>
...

// MainPage.h
...
#include <winrt/Windows.Storage.Search.h>
...
struct MainPage : MainPageT<MainPage>
{
    MainPage()
    {
        InitializeComponent();
    }

    IAsyncAction OnWork(IInspectable /* sender */, RoutedEventArgs /* args */)
    {
        workButton().Content(winrt::box_value(L"Working..."));

        // Enable the Pictures Library capability in the app manifest file.
        StorageFolder picturesLibrary{ KnownFolders::PicturesLibrary() };

        m_async = picturesLibrary.GetFilesAsync(CommonFileQuery::OrderByDate, 0, 1000);

        IVectorView<StorageFile> filesInFolder{ co_await m_async };

        workButton().Content(box_value(L"Done!"));

        // Process the files in some way.
    }

    void OnCancel(IInspectable const& /* sender */, RoutedEventArgs const& /* args */)
    {
        if (m_async.Status() != AsyncStatus::Completed)
        {
            m_async.Cancel();
            workButton().Content(winrt::box_value(L"Canceled"));
        }
    }

private:
    IAsyncOperation<::IVectorView<StorageFile>> m_async;
};
```

Für die Implementierung Seite des Abbruchs beginnen wir mit einem einfachen Beispiel.

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"
using namespace winrt;
using namespace Windows::Foundation;
using namespace std::chrono_literals;

IAsyncAction ImplicitCancellationAsync()
{
    while (true)
    {
        std::cout << "ImplicitCancellationAsync: do some work for 1 second" << std::endl;
        co_await 1s;
    }
}

IAsyncAction MainCoroutineAsync()
{
    auto implicit_cancellation{ ImplicitCancellationAsync() };
    co_await 3s;
    implicit_cancellation.Cancel();
}

int main()
{
    winrt::init_apartment();
    MainCoroutineAsync().get();
}
```

Wenn Sie im obigen Beispiel ausführen, erscheint das **ImplicitCancellationAsync** Druck eine Nachricht pro Sekunde drei Sekunden lang, nach denen es automatisch Zeit beendet aufgrund abgebrochen wird. Dies funktioniert, da auf dieser eine `co_await` Ausdruck eine Coroutine überprüft, ob er abgebrochen wurde. Wenn dies der Fall, kurzgeschlossen wird dann es sich; und wenn dies nicht der Fall, dann angehalten normal.

Abbruch kann, natürlich auftreten, während die Coroutine angehalten ist. Nur, wenn die Coroutine fortgesetzt wird, oder eine andere prallt `co_await`, wird es nach einem Abbruch suchen. Das Problem ist der potenziell zu grob-differenziertere Latenz bei der Behandlung von Abbruch.

Daher ist eine andere Option explizit für den Abbruch von innerhalb Ihrer Coroutine ab. Aktualisieren Sie das obige Beispiel, mit der Code in den folgenden Eintrag. In diesem Beispiel neue **ExplicitCancellationAsync** Ruft das von der Funktion [**winrt::get_cancellation_token**](/uwp/cpp-ref-for-winrt/get-cancellation-token) zurückgegebene Objekt ab, und verwendet ihn zum Überprüfen Sie regelmäßig, ob die Coroutine abgebrochen wurde. Solange sie nicht abgebrochen wird, überblendanimation die Coroutine; Sobald der Vorgang abgebrochen wird, beenden Sie die Schleife und die Funktion normal. Das Ergebnis ist das gleiche wie das vorherige Beispiel, aber hier verlassen geschieht explizit und gesteuert.

```cppwinrt
...
IAsyncAction ExplicitCancellationAsync()
{
    auto cancellation_token{ co_await winrt::get_cancellation_token() };

    while (!cancellation_token())
    {
        std::cout << "ExplicitCancellationAsync: do some work for 1 second" << std::endl;
        co_await 1s;
    }
}

IAsyncAction MainCoroutineAsync()
{
    auto explicit_cancellation{ ExplicitCancellationAsync() };
    co_await 3s;
    explicit_cancellation.Cancel();
}
...
```

Warten auf **winrt::get_cancellation_token** Ruft ein Abbruchtoken mit Kenntnisse über die **IAsyncAction** , die die Coroutine liefern in Ihrem Auftrag ab. Sie können Funktionsaufrufoperators auf das Token verwenden, um den Abbruch Zustand Abfragen&mdash;im Wesentlichen für den Abbruch Abfragen. Wenn Sie bestimmte rechengebundene Vorgänge durchführen, oder einer großen Sammlung durchlaufen, ist dies eine angemessene Technik.

### <a name="register-a-cancellation-callback"></a>Registrieren eines Rückrufs Abbruch

Die Windows-Runtime Abbruch übergeben nicht automatisch auf andere asynchrone Objekte. Aber&mdash;eingeführt in Windows SDK-Version (Windows 10, Version 1809) 10.0.17763.0&mdash;können Sie einen Rückruf Abbruch registrieren. Hierbei handelt es sich um eine vorbeugenden Häkchen, Abbruch weitergegeben werden kann, und ermöglicht die Integration in vorhandene Concurrency-Bibliotheken.

In diesem nächsten Codebeispiel **NestedCoroutineAsync** funktioniert die, aber es weist keine spezielle Abbruchlogik auf. **CancellationPropagatorAsync** ist im Grunde ein Wrapper für die geschachtelte Coroutine. der Wrapper leitet Abbruch präventiven weiter.

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"
using namespace winrt;
using namespace Windows::Foundation;
using namespace std::chrono_literals;

IAsyncAction NestedCoroutineAsync()
{
    while (true)
    {
        std::cout << "NestedCoroutineAsync: do some work for 1 second" << std::endl;
        co_await 1s;
    }
}

IAsyncAction CancellationPropagatorAsync()
{
    auto cancellation_token{ co_await winrt::get_cancellation_token() };
    auto nested_coroutine{ NestedCoroutineAsync() };

    cancellation_token.callback([&]
    {
        nested_coroutine.Cancel();
    });

    co_await nested_coroutine;
}

IAsyncAction MainCoroutineAsync()
{
    auto cancellation_propagator{ CancellationPropagatorAsync() };
    co_await 3s;
    cancellation_propagator.Cancel();
}

int main()
{
    winrt::init_apartment();
    MainCoroutineAsync().get();
}
```

**CancellationPropagatorAsync** registriert eine Lambda-Funktion für eine eigene Abbruch Rückruf, und es anschließend wartet auf (angehalten) bis die geschachtelte Arbeit abgeschlossen ist. Wenn oder **CancellationPropagatorAsync** abgebrochen wird, wird es den Abbruch an die geschachtelte Coroutine weitergegeben. Es ist nicht erforderlich für den Abbruch ab. Außerdem ist Abbruch auf unbestimmte Zeit blockiert. Dieser Mechanismus ist flexibel genug, Sie es für die Interoperabilität mit einer Coroutine oder Concurrency-Bibliothek verwenden, die weiß nichts von C++ / WinRT.

## <a name="reporting-progress"></a>Melden des Status

Wenn Ihre Coroutine entweder [**IAsyncActionWithProgress**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)oder [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)zurückgegeben wird, können dann von der Funktion [**winrt::get_progress_token**](/uwp/cpp-ref-for-winrt/get-progress-token) zurückgegebene Objekt abzurufen, und verwenden, um den Fortschritt an einem Fortschritt Handler. Dies ist ein Codebeispiel:

```cppwinrt
// pch.h
#pragma once
#include <iostream>
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"
using namespace winrt;
using namespace Windows::Foundation;
using namespace std::chrono_literals;

IAsyncOperationWithProgress<double, double> CalcPiTo5DPs()
{
    auto progress{ co_await winrt::get_progress_token() };

    co_await 1s;
    double pi_so_far{ 3.1 };
    progress(0.2);

    co_await 1s;
    pi_so_far += 4.e-2;
    progress(0.4);

    co_await 1s;
    pi_so_far += 1.e-3;
    progress(0.6);

    co_await 1s;
    pi_so_far += 5.e-4;
    progress(0.8);

    co_await 1s;
    pi_so_far += 9.e-5;
    progress(1.0);
    co_return pi_so_far;
}

IAsyncAction DoMath()
{
    auto async_op_with_progress{ CalcPiTo5DPs() };
    async_op_with_progress.Progress([](auto const& /* sender */, double progress)
    {
        std::wcout << L"CalcPiTo5DPs() reports progress: " << progress << std::endl;
    });
    double pi{ co_await async_op_with_progress };
    std::wcout << L"CalcPiTo5DPs() is complete !" << std::endl;
    std::wcout << L"Pi is approx.: " << pi << std::endl;
}

int main()
{
    winrt::init_apartment();
    DoMath().get();
}
```

> [!NOTE]
> Es ist nicht korrekt auf mehr als ein *Abschlusshandler* für eine asynchrone Aktion oder Operation implementieren. Sie können entweder einen einzelnen Delegaten für das abgeschlossene Ereignis haben, oder Sie können `co_await` es. Wenn Sie beide haben, wird die zweite fehl. Entweder eine der folgenden zwei Arten von Abschlusshandler eignet sich; nicht beide für das gleiche Async-Objekt.

```cppwinrt
auto async_op_with_progress{ CalcPiTo5DPs() };
async_op_with_progress.Completed([](auto const& sender, AsyncStatus /* status */)
{
    double pi{ sender.GetResults() };
});
```

```cppwinrt
auto async_op_with_progress{ CalcPiTo5DPs() };
double pi{ co_await async_op_with_progress };
```

Weitere Informationen zu Abschlusshandler finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).

## <a name="fire-and-forget"></a>Auslösen und vergessen

In manchen Fällen Sie haben eine Aufgabe, die gleichzeitig mit anderen Vorgängen ausgeführt werden kann, und Sie müssen nicht warten, dass dieser Vorgang abschließen (keine anderen Vorgängen abhängig es), auch nicht erforderlich, um einen Wert zurückgeben. In diesem Fall können Sie aus der Aufgabe ausgelöst und vergessen. Sie können dies tun, durch das Schreiben einer Coroutine, deren Rückgabetyp [**winrt::fire_and_forget**](/uwp/cpp-ref-for-winrt/fire-and-forget) (anstelle eines der Windows-Runtime-Typen für asynchrone Vorgänge, oder **Concurrency:: Task**) ist.

```cppwinrt
// pch.h
#pragma once
#include <winrt/Windows.Foundation.h>

// main.cpp : Defines the entry point for the console application.
#include "pch.h"
using namespace winrt;
using namespace std::chrono_literals;

winrt::fire_and_forget CompleteInFiveSeconds()
{
    co_await 5s;
}

int main()
{
    winrt::init_apartment();
    CompleteInFiveSeconds();
    // Do other work here.
}
```

## <a name="important-apis"></a>Wichtige APIs
* [Concurrency:: Task-Klasse](/cpp/parallel/concrt/reference/task-class)
* [IAsyncAction-Schnittstelle](/uwp/api/windows.foundation.iasyncaction)
* [IAsyncActionWithProgress&lt;TProgress&gt; Schnittstelle](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [IAsyncOperation&lt;TResult&gt; Schnittstelle](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [IAsyncOperationWithProgress&lt;TResult, TProgress&gt; Schnittstelle](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [Syndicationclient:: Retrievefeedasync-Methode](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [SyndicationFeed-Klasse](/uwp/api/windows.web.syndication.syndicationfeed)
* [WinRT::get_cancellation_token](/uwp/cpp-ref-for-winrt/get-cancellation-token)
* [WinRT::get_progress_token](/uwp/cpp-ref-for-winrt/get-progress-token)
* [WinRT::fire_and_forget](/uwp/cpp-ref-for-winrt/fire-and-forget)

## <a name="related-topics"></a>Verwandte Themen
* [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md)
* [Standard C++ Datentypen und C++/WinRT](std-cpp-data-types.md)
