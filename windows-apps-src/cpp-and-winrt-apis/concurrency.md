---
author: stevewhims
description: Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.
title: Parallelität und asynchrone Vorgänge mit C++/WinRT
ms.author: stwhi
ms.date: 10/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projektion, parallelität, async, asynchron, asynchronität
ms.localizationpriority: medium
ms.openlocfilehash: 9f29828a800795aba70c17bcab19b56b85d56382
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4536463"
---
# <a name="concurrency-and-asynchronous-operations-with-cwinrt"></a><span data-ttu-id="14b71-104">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="14b71-104">Concurrency and asynchronous operations with C++/WinRT</span></span>

<span data-ttu-id="14b71-105">Dieses Thema zeigt, in denen Sie beide können, Methoden erstellen und nutzen asynchrone Windows-Runtime-Objekte mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span><span class="sxs-lookup"><span data-stu-id="14b71-105">This topic shows the ways in which you can both create and consume Windows Runtime asynchronous objects with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span></span>

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a><span data-ttu-id="14b71-106">Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen</span><span class="sxs-lookup"><span data-stu-id="14b71-106">Asynchronous operations and Windows Runtime "Async" functions</span></span>
<span data-ttu-id="14b71-107">Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet).</span><span class="sxs-lookup"><span data-stu-id="14b71-107">Any Windows Runtime API that has the potential to take more than 50 milliseconds to complete is implemented as an asynchronous function (with a name ending in "Async").</span></span> <span data-ttu-id="14b71-108">Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="14b71-108">The implementation of an asynchronous function initiates the work on another thread and returns immediately with an object that represents the asynchronous operation.</span></span> <span data-ttu-id="14b71-109">Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt.</span><span class="sxs-lookup"><span data-stu-id="14b71-109">When the asynchronous operation completes, that returned object contains any value that resulted from the work.</span></span> <span data-ttu-id="14b71-110">Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="14b71-110">The **Windows::Foundation** Windows Runtime namespace contains four types of asynchronous operation object.</span></span>

- <span data-ttu-id="14b71-111">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span><span class="sxs-lookup"><span data-stu-id="14b71-111">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span></span>
- <span data-ttu-id="14b71-112">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span><span class="sxs-lookup"><span data-stu-id="14b71-112">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span></span>
- <span data-ttu-id="14b71-113">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und</span><span class="sxs-lookup"><span data-stu-id="14b71-113">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_), and</span></span>
- <span data-ttu-id="14b71-114">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span><span class="sxs-lookup"><span data-stu-id="14b71-114">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span>

<span data-ttu-id="14b71-115">Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert.</span><span class="sxs-lookup"><span data-stu-id="14b71-115">Each of these asynchronous operation types is projected into a corresponding type in the **winrt::Windows::Foundation** C++/WinRT namespace.</span></span> <span data-ttu-id="14b71-116">C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur.</span><span class="sxs-lookup"><span data-stu-id="14b71-116">C++/WinRT also contains an internal await adapter struct.</span></span> <span data-ttu-id="14b71-117">Sie verwenden diese nicht direkt, aber Dank dieser Struktur können Sie können auch Schreiben einer `co_await` -Anweisung ein, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asychrone Vorgänge zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="14b71-117">You don't use it directly but, thanks to that struct, you can write a `co_await` statement to cooperatively await the result of any function that returns one of these asychronous operation types.</span></span> <span data-ttu-id="14b71-118">Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-118">And you can author your own coroutines that return these types.</span></span>

<span data-ttu-id="14b71-119">Ein Beispiel für eine asynchrone Windows-Funktion ist [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), die ein Objekt für einen asynchronen Vorgang vom Typ [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="14b71-119">An example of an asynchronous Windows function is [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), which returns an asynchronous operation object of type [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span> <span data-ttu-id="14b71-120">Betrachten wir einige (blockierende und nicht blockierende) Möglichkeiten der Verwendung von C++/WinRT, um eine solche API aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="14b71-120">Let's look at some ways&mdash;blocking and non-blocking&mdash;of using C++/WinRT to call an API such as that.</span></span>

## <a name="block-the-calling-thread"></a><span data-ttu-id="14b71-121">Den aufrufenden Thread blockieren</span><span class="sxs-lookup"><span data-stu-id="14b71-121">Block the calling thread</span></span>
<span data-ttu-id="14b71-122">Das folgende Codebeispiel erhält ein Objekt für asynchronen Vorgänge von **RetrieveFeedAsync** und ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren, bis die Ergebnisse des asynchronen Vorgangs vorliegen.</span><span class="sxs-lookup"><span data-stu-id="14b71-122">The code example below receives an asynchronous operation object from **RetrieveFeedAsync**, and it calls **get** on that object to block the calling thread until the results of the asynchronous operation are available.</span></span>

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

<span data-ttu-id="14b71-123">Der Aufruf von **get** ermöglicht eine bequeme Codeerstellung und eignet sich perfekt für Konsolenapps oder Hintergrundthreads, in denen Sie möglicherweise keine Coroutine verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="14b71-123">Calling **get** makes for convenient coding, and it's ideal for console apps or background threads where you may not want to use a coroutine for whatever reason.</span></span> <span data-ttu-id="14b71-124">Sie ist jedoch weder parallel noch asynchron und folglich eignet sie sich nicht für einen UI-Thread (außerdem wird eine Assertion in nicht optimierten Builds ausgelöst, wenn Sie versuchen, sie dafür zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="14b71-124">But it's not concurrent nor asynchronous, so it's not appropriate for a UI thread (and an assertion will fire in unoptimized builds if you attempt to use it on one).</span></span> <span data-ttu-id="14b71-125">Um Betriebssystem-Threads nicht daran zu hindern, andere nützliche Aufgaben zu erledigen, benötigen wir eine andere Technik.</span><span class="sxs-lookup"><span data-stu-id="14b71-125">To avoid holding up OS threads from doing other useful work, we need a different technique.</span></span>

## <a name="write-a-coroutine"></a><span data-ttu-id="14b71-126">Schreiben einer Coroutine</span><span class="sxs-lookup"><span data-stu-id="14b71-126">Write a coroutine</span></span>
<span data-ttu-id="14b71-127">C++/WinRT integriert C++ Coroutinen in das Programmiermodell, um eine natürliche Möglichkeit zu bieten, kooperativ auf ein Ergebnis zu warten.</span><span class="sxs-lookup"><span data-stu-id="14b71-127">C++/WinRT integrates C++ coroutines into the programming model to provide a natural way to cooperatively wait for a result.</span></span> <span data-ttu-id="14b71-128">Sie können Ihre eigene asynchronen Windows-Runtime-Vorgänge erzeugen, indem Sie eine Coroutine schreiben.</span><span class="sxs-lookup"><span data-stu-id="14b71-128">You can produce your own Windows Runtime asynchronous operation by writing a coroutine.</span></span> <span data-ttu-id="14b71-129">Im folgenden Codebeispiel ist **ProcessFeedAsync** die Coroutine.</span><span class="sxs-lookup"><span data-stu-id="14b71-129">In the code example below, **ProcessFeedAsync** is the coroutine.</span></span>

> [!NOTE]
> <span data-ttu-id="14b71-130">Die **get** -Funktion vorhanden ist, auf der C++ / WinRT-Projektion geben **Winrt::Windows::Foundation::IAsyncAction**, damit Sie aufrufen können, die Funktion in jeder C++ / WinRT-Projekt.</span><span class="sxs-lookup"><span data-stu-id="14b71-130">The **get** function exists on the C++/WinRT projection type **winrt::Windows::Foundation::IAsyncAction**, so you can call the function from within any C++/WinRT project.</span></span> <span data-ttu-id="14b71-131">Die Funktion, die als Mitglied der [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) -Schnittstelle, aufgeführt werden nicht gefunden werden, da **erhalten** nicht Teil der Application binary Interface (ABI) Fläche des tatsächlichen Windows-Runtime-Typs **IAsyncAction**ist.</span><span class="sxs-lookup"><span data-stu-id="14b71-131">You will not find the function listed as a member of the [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) interface, because **get** is not part of the application binary interface (ABI) surface of the actual Windows Runtime type **IAsyncAction**.</span></span>

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

<span data-ttu-id="14b71-132">Eine Coroutine ist eine Funktion, die angehalten und wieder fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="14b71-132">A coroutine is a function that can be suspended and resumed.</span></span> <span data-ttu-id="14b71-133">Wenn die `co_await`-Anweisung In der **ProcessFeedAsync**-Coroutine oben erreicht ist, initiiert die Coroutine asynchron den **RetrieveFeedAsync**-Aufruf und unterbricht sich dann sofort selbst und gibt die Kontrolle an den Aufrufer zurück (was im obigen Beispiel **main** ist).</span><span class="sxs-lookup"><span data-stu-id="14b71-133">In the **ProcessFeedAsync** coroutine above, when the `co_await` statement is reached, the coroutine asynchronously initiates the **RetrieveFeedAsync** call and then it immediately suspends itself and returns control back to the caller (which is **main** in the example above).</span></span> <span data-ttu-id="14b71-134">**main** kann dann weiterarbeiten, während der Feed abgerufen und ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="14b71-134">**main** can then continue to do work while the feed is being retrieved and printed.</span></span> <span data-ttu-id="14b71-135">Wenn das erledigt ist (wenn der **RetrieveFeedAsync**-Aufruf abgeschlossen ist), wird die **ProcessFeedAsync**-Coroutine bei der nächsten Anweisung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="14b71-135">When that's done (when the **RetrieveFeedAsync** call completes), the **ProcessFeedAsync** coroutine resumes at the next statement.</span></span>

<span data-ttu-id="14b71-136">Sie können eine Coroutine in anderen Coroutinen zusammenfassen.</span><span class="sxs-lookup"><span data-stu-id="14b71-136">You can aggregate a coroutine into other coroutines.</span></span> <span data-ttu-id="14b71-137">Oder Sie können **get** zur Blockierung aufrufen und warten, bis sie abgeschlossen ist (und das Ergebnis erhalten, wenn es eines gibt).</span><span class="sxs-lookup"><span data-stu-id="14b71-137">Or you can call **get** to block and wait for it to complete (and get the result if there is one).</span></span> <span data-ttu-id="14b71-138">Oder Sie können sie an eine andere Programmiersprache übergeben, die Windows-Runtime unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14b71-138">Or you can pass it to another programming language that supports the Windows Runtime.</span></span>

<span data-ttu-id="14b71-139">Es ist auch möglich, die Completed- und/oder Progress-Ereignisse von asynchronen Aktionen und Vorgängen mit Hilfe von Delegaten zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="14b71-139">It's also possible to handle the completed and/or progress events of asynchronous actions and operations by using delegates.</span></span> <span data-ttu-id="14b71-140">Details und Codebeispiele finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span><span class="sxs-lookup"><span data-stu-id="14b71-140">For details, and code examples, see [Delegate types for asynchronous actions and operations](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span></span>

## <a name="asychronously-return-a-windows-runtime-type"></a><span data-ttu-id="14b71-141">Asychrone Rückgabe eines Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="14b71-141">Asychronously return a Windows Runtime type</span></span>
<span data-ttu-id="14b71-142">In diesem nächsten Beispiel verpacken wir einen Aufruf von **RetrieveFeedAsync** für eine bestimmte URI, um uns eine **RetrieveBlogFeedAsync**-Funktion zu holen, die asynchron ein [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="14b71-142">In this next example we wrap a call to **RetrieveFeedAsync**, for a specific URI, to give us a **RetrieveBlogFeedAsync** function that asynchronously returns a [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed).</span></span>

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

<span data-ttu-id="14b71-143">Im obigen Beispiel gibt **RetrieveBlogFeedAsync** ein **IAsyncOperationWithProgress** zurück, das sowohl einen Progress- als auch einen Return-Wert hat.</span><span class="sxs-lookup"><span data-stu-id="14b71-143">In the example above, **RetrieveBlogFeedAsync** returns an **IAsyncOperationWithProgress**, which has both progress and a return value.</span></span> <span data-ttu-id="14b71-144">Wir können andere Arbeiten durchführen, während **RetrieveBlogFeedAsync** sein Ding macht und den Feed abruft.</span><span class="sxs-lookup"><span data-stu-id="14b71-144">We can do other work while **RetrieveBlogFeedAsync** is doing its thing and retrieving the feed.</span></span> <span data-ttu-id="14b71-145">Dann rufen wir das **get**-Objekt des asynchronen Vorgangs auf, um es zu blockieren, warten, bis es abgeschlossen ist, und erhalten dann die Ergebnisse des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="14b71-145">Then, we call **get** on that asynchronous operation object to block, wait for it to complete, and then obtain the results of the operation.</span></span>

<span data-ttu-id="14b71-146">Wenn Sie einen Windows-Runtime-Typ asynchron zurückgeben, sollten Sie ein [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) oder ein [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-146">If you're asynchronously returning a Windows Runtime type, then you should return an [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) or an [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span> <span data-ttu-id="14b71-147">Alle Erst- oder Drittanbieter-Laufzeitklassen sind qualifiziert, oder ein anderer Typ, der an oder von einer Windows-Runtime-Funktion übergeben werden kann (z.B. `int` oder **winrt::hstring**).</span><span class="sxs-lookup"><span data-stu-id="14b71-147">Any first- or third-party runtime class qualifies, or any type that can be passed to or from a Windows Runtime function (for example, `int`, or **winrt::hstring**).</span></span> <span data-ttu-id="14b71-148">Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie versuchen, einen dieser Typen für asychrone Vorgänge mit einem Nicht-Windows-Runtime-Typ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b71-148">The compiler will help you with a "*must be WinRT type*" error if you try to use one of these asychronous operation types with a non-Windows Runtime type.</span></span>

<span data-ttu-id="14b71-149">Wenn eine Coroutine nicht mindestens eine `co_await`-Anweisung enthält, benötigt sie mindestens eine `co_return`- oder `co_yield`-Anweisung, um sich als Coroutine zu qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="14b71-149">If a coroutine doesn't have at least one `co_await` statement then, in order to qualify as a coroutine, it must have at least one `co_return` or one `co_yield` statement.</span></span> <span data-ttu-id="14b71-150">Es gibt Fälle, in denen Ihre Coroutine einen Wert zurückgeben kann, ohne dass es zur Asynchronität kommt und ohne dass Kontext blockiert oder gewechselt wird.</span><span class="sxs-lookup"><span data-stu-id="14b71-150">There will be cases where your coroutine can return a value without introducing any asynchrony, and therefore without blocking nor switching context.</span></span> <span data-ttu-id="14b71-151">Hier ist ein solches Beispiel, das (beim zweiten oder nachfolgenden Aufruf) dafür einen Wert zwischenspeichert.</span><span class="sxs-lookup"><span data-stu-id="14b71-151">Here's an example that does that (the second and subsequent times it's called) by caching a value.</span></span>

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

## <a name="asychronously-return-a-non-windows-runtime-type"></a><span data-ttu-id="14b71-152">Asychrone Rückgabe eines Nicht-Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="14b71-152">Asychronously return a non-Windows-Runtime type</span></span>
<span data-ttu-id="14b71-153">Wenn Sie asynchron einen Typ zurückgeben, der *kein* Windows-Runtime-Typ ist, sollten Sie ein Parallel Patterns Library (PPL) [**concurrency::task**](/cpp/parallel/concrt/reference/task-class) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-153">If you're asynchronously returning a type that's *not* a Windows Runtime type, then you should return a Parallel Patterns Library (PPL) [**concurrency::task**](/cpp/parallel/concrt/reference/task-class).</span></span> <span data-ttu-id="14b71-154">Wir empfehlen **concurrency::task**, weil es eine bessere Performance (und später eine bessere Kompatibilität) bietet als **std::future**.</span><span class="sxs-lookup"><span data-stu-id="14b71-154">We recommend **concurrency::task** because it gives you better performance (and better compatibility going forward) than **std::future** does.</span></span>

> [!TIP]
> <span data-ttu-id="14b71-155">Wenn Sie `<pplawait.h>` einschließen, können Sie **concurrency::task** als Coroutinentyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b71-155">If you include `<pplawait.h>`, then you can use **concurrency::task** as a coroutine type.</span></span>

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

## <a name="parameter-passing"></a><span data-ttu-id="14b71-156">Parameterübergabe</span><span class="sxs-lookup"><span data-stu-id="14b71-156">Parameter-passing</span></span>
<span data-ttu-id="14b71-157">Für synchrone Funktionen sollten Sie standardmäßig `const&`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b71-157">For synchronous functions, you should use `const&` parameters by default.</span></span> <span data-ttu-id="14b71-158">Dadurch wird der Aufwand für Kopien vermieden (wozu Referenzzählung gehört, die zu miteinander verbundenen Erhöhungen und Verringerungen führt).</span><span class="sxs-lookup"><span data-stu-id="14b71-158">That will avoid the overhead of copies (which involve reference counting, and that means interlocked increments and decrements).</span></span>

```cppwinrt
// Synchronous function.
void DoWork(Param const& value);
```

<span data-ttu-id="14b71-159">Sie können jedoch auf Probleme stoßen, wenn Sie einen Referenzparameter an eine Coroutine übergeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-159">But you can run into problems if you pass a reference parameter to a coroutine.</span></span>

```cppwinrt
// NOT the recommended way to pass a value to a coroutine!
IASyncAction DoWorkAsync(Param const& value)
{
    // While it's ok to access value here...
    
    co_await DoOtherWorkAsync();

    // ...accessing value here carries no guarantees of safety.
}
```

<span data-ttu-id="14b71-160">In einer Coroutine verläuft die Ausführung bis zum ersten Anhaltepunkt synchron, wobei die Steuerung an den Aufrufer zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="14b71-160">In a coroutine, execution is synchronous up until the first suspension point, where control is returned to the caller.</span></span> <span data-ttu-id="14b71-161">Wenn die Coroutine fortgesetzt wird, kann alles Mögliche mit dem Quellwert passiert sein, auf den ein Referenzparameter verweist.</span><span class="sxs-lookup"><span data-stu-id="14b71-161">By the time the coroutine resumes, anything might have happened to the source value that a reference parameter references.</span></span> <span data-ttu-id="14b71-162">Aus Sicht der Coroutine hat ein Referenzparameter eine unkontrollierte Lebensdauer.</span><span class="sxs-lookup"><span data-stu-id="14b71-162">From the coroutine's perspective, a reference parameter has uncontrolled lifetime.</span></span> <span data-ttu-id="14b71-163">Im obigen Beispiel können wir also problemlos auf *value* bis `co_await` zugreifen, nicht jedoch danach.</span><span class="sxs-lookup"><span data-stu-id="14b71-163">So, in the example above, we're safe to access *value* up until the `co_await`, but not after it.</span></span> <span data-ttu-id="14b71-164">Wir können *value* nicht problemlos an **DoOtherWorkAsync** übergeben, wenn das Risiko besteht, dass diese Funktion ihrerseits angehalten wird und bei Fortsetzen dann versucht, *value* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b71-164">Nor can we safely pass *value* to **DoOtherWorkAsync** if there's any risk that that function will in turn suspend and then try to use *value* after it resumes.</span></span> <span data-ttu-id="14b71-165">Damit die Parameter nach dem Anhalten und Fortsetzen ohne Probleme verwendet werden können, sollten Ihre Coroutinen standardmäßig „pass-by-value“ verwenden, um sicherzustellen, dass die Erfassung nach Wert erfolgt, und um Probleme mit der Lebensdauer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="14b71-165">To make parameters safe to use after suspending and resuming, your coroutines should use pass-by-value by default to ensure that they capture by value and avoid lifetime issues.</span></span> <span data-ttu-id="14b71-166">Fälle, in denen Sie von dieser Vorgehensweise abweichen können, da Sie sicher sind, dass keine Probleme entstehen, sind eher selten.</span><span class="sxs-lookup"><span data-stu-id="14b71-166">Cases when you can deviate from that guidance because you're certain that it's safe to do so are going to be rare.</span></span>

```cppwinrt
// Coroutine
IASyncAction DoWorkAsync(Param value);
```

<span data-ttu-id="14b71-167">Es ist auch fraglich, ob die Übergabe nach Konstantenwert empfehlenswert ist (es sei denn, Sie möchten den Wert verschieben).</span><span class="sxs-lookup"><span data-stu-id="14b71-167">It's also arguable that (unless you want to move the value) passing by const value is good practice.</span></span> <span data-ttu-id="14b71-168">Dies hat keine Auswirkungen auf den Quellwert, von dem Sie eine Kopie erstellen, es macht aber die Intention klar und hilft, wenn Sie die Kopie versehentlich ändern.</span><span class="sxs-lookup"><span data-stu-id="14b71-168">It won't have any effect on the source value from which you're making a copy, but it makes the intent clear, and helps if you inadvertently modify the copy.</span></span>
    
```cppwinrt
// coroutine with strictly unnecessary const (but arguably good practice).
IASyncAction DoWorkAsync(Param const value);
```

<span data-ttu-id="14b71-169">Weitere Informationen finden Sie unter [Standard-Arrays und -Vektoren](std-cpp-data-types.md#standard-arrays-and-vectors). Hier wird beschrieben, wie Sie einen Standardvektor in einem asynchronen Aufrufer übergeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-169">Also see [Standard arrays and vectors](std-cpp-data-types.md#standard-arrays-and-vectors), which deals with how to pass a standard vector into an asynchronous callee.</span></span>

## <a name="offloading-work-onto-the-windows-thread-pool"></a><span data-ttu-id="14b71-170">Auslagern von Aufgaben an den Windows-Threadpool</span><span class="sxs-lookup"><span data-stu-id="14b71-170">Offloading work onto the Windows thread pool</span></span>
<span data-ttu-id="14b71-171">Bevor Sie rechengebundene Arbeiten in einer Coroutine ausführen, müssen Sie die Ausführung an den Aufrufer zurückgegeben, damit der Aufrufer nicht blockiert wird (anders ausgedrückt, sollte ein Anhaltepunkt eingefügt werden).</span><span class="sxs-lookup"><span data-stu-id="14b71-171">Before you do compute-bound work in a coroutine, you need to return execution to the caller so that the caller isn't blocked (in other words, introduce a suspension point).</span></span> <span data-ttu-id="14b71-172">Wenn Sie dies noch nicht durch ein `co-await` anderer Vorgänge tun, können Sie ein `co-await` für die Funktion **winrt::resume_background** ausführen.</span><span class="sxs-lookup"><span data-stu-id="14b71-172">If you're not already doing that by `co-await`-ing some other operation, then you can `co-await` the **winrt::resume_background** function.</span></span> <span data-ttu-id="14b71-173">Dadurch wird die Steuerung an den Aufrufer zurückgegeben, und unmittelbar danach wird die Ausführung auf einem Threadpoolthread fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="14b71-173">That returns control to the caller, and then immediately resumes execution on a thread pool thread.</span></span>

<span data-ttu-id="14b71-174">Der in der Implementierung verwendete Threadpool wird auf niedriger Ebene ausgeführt [Windows-Threadpool](https://msdn.microsoft.com/library/windows/desktop/ms686766), sodass er optimal effizient ist.</span><span class="sxs-lookup"><span data-stu-id="14b71-174">The thread pool being used in the implementation is the low-level [Windows thread pool](https://msdn.microsoft.com/library/windows/desktop/ms686766), so it's optimially efficient.</span></span>

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

## <a name="programming-with-thread-affinity-in-mind"></a><span data-ttu-id="14b71-175">Programmieren mit Threadaffinität</span><span class="sxs-lookup"><span data-stu-id="14b71-175">Programming with thread affinity in mind</span></span>
<span data-ttu-id="14b71-176">Dieses Szenario erweitert das vorherige.</span><span class="sxs-lookup"><span data-stu-id="14b71-176">This scenario expands on the previous one.</span></span> <span data-ttu-id="14b71-177">Sie lagern einige Aufgaben an den Threadpool aus, möchten dann aber den Fortschritt auf der Benutzeroberfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="14b71-177">You offload some work onto the thread pool, but then you want to display progress in the user interface (UI).</span></span>

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    textblock.Text(L"Done!"); // Error: TextBlock has thread affinity.
}
```

<span data-ttu-id="14b71-178">Der obige Code löst eine [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread)-Ausnahme aus, da ein **TextBlock** von dem Thread, der ihn erstellt hat (UI-Thread), aktualisiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="14b71-178">The code above throws a [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread) exception, because a **TextBlock** must be updated from the thread that created it, which is the UI thread.</span></span> <span data-ttu-id="14b71-179">Eine Lösung besteht darin, den Threadkontext zu erfassen, in dem unsere Coroutine ursprünglich aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="14b71-179">One solution is to capture the thread context within which our coroutine was originally called.</span></span> <span data-ttu-id="14b71-180">Instanziieren Sie ein **winrt::apartment_context**-Objekt, und führen Sie dann ein `co_await` dafür aus.</span><span class="sxs-lookup"><span data-stu-id="14b71-180">Instantiate a **winrt::apartment_context** object, and then `co_await` it.</span></span>

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

<span data-ttu-id="14b71-181">Solange die oben genannte Coroutine vom UI-Thread aufgerufen wird, der den **TextBlock** erstellt hat, funktioniert dieses Verfahren.</span><span class="sxs-lookup"><span data-stu-id="14b71-181">As long as the coroutine above is called from the UI thread that created the **TextBlock**, then this technique works.</span></span> <span data-ttu-id="14b71-182">Es wird einige Fälle in Ihrer App geben, in denen Sie dessen sicher sind.</span><span class="sxs-lookup"><span data-stu-id="14b71-182">There will be many cases in your app where you're certain of that.</span></span>

<span data-ttu-id="14b71-183">Für eine allgemeinere Lösung zur Aktualisierung der Benutzeroberfläche, die auch Fälle abdeckt, in denen Sie bezüglich des aufrufenden Threads unsicher sind, können Sie `co-await` die **resume_foreground** -Funktion, die zu einem bestimmten Vordergrundthread zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="14b71-183">For a more general solution to updating UI, which covers cases where you're uncertain about the calling thread, you can `co-await` the **winrt::resume_foreground** function to switch to a specific foreground thread.</span></span> <span data-ttu-id="14b71-184">Im folgenden Codebeispiel geben Sie den Vordergrundthread durch Übergabe des Dispatcherobjekts an, das mit dem **TextBlock** verknüpft ist (durch Zugriff auf die zugehörige [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher)-Eigenschaft).</span><span class="sxs-lookup"><span data-stu-id="14b71-184">In the code example below, we specify the foreground thread by passing the dispatcher object associated with the **TextBlock** (by accessing its [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher) property).</span></span> <span data-ttu-id="14b71-185">Die Implementierung von **winrt::resume_foreground** ruft [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) für dieses Dispatcherobjekt auf, um die Aufgaben auszuführen, die danach in der Coroutine folgen.</span><span class="sxs-lookup"><span data-stu-id="14b71-185">The implementation of **winrt::resume_foreground** calls [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) on that dispatcher object to execute the work that comes after it in the coroutine.</span></span>

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    co_await winrt::resume_foreground(textblock.Dispatcher()); // Switch to the foreground thread associated with textblock.

    textblock.Text(L"Done!"); // Guaranteed to work.
}
```

## <a name="canceling-an-asychronous-operation-and-cancellation-callbacks"></a><span data-ttu-id="14b71-186">Abbrechen eines Vorgangs asychrone und Abbruch-Rückrufe</span><span class="sxs-lookup"><span data-stu-id="14b71-186">Canceling an asychronous operation, and cancellation callbacks</span></span>

<span data-ttu-id="14b71-187">Die Windows-Runtime-Features für die asynchrone Programmierung können Sie ein Flight asynchrone Aktion oder einen Vorgang abbrechen.</span><span class="sxs-lookup"><span data-stu-id="14b71-187">The Windows Runtime's features for asynchronous programming allow you to cancel an in-flight asynchronous action or operation.</span></span> <span data-ttu-id="14b71-188">Beginnen wir mit einem einfachen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="14b71-188">Let's begin with a simple example.</span></span>

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

<span data-ttu-id="14b71-189">Wenn Sie im obigen Beispiel ausführen, erscheint das **ImplicitCancellationAsync** Druck eine Nachricht pro Sekunde drei Sekunden lang, nach denen er automatisch Zeit beendet als Folge abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="14b71-189">If you run the example above, then you'll see **ImplicitCancellationAsync** print one message per second for three seconds, after which time it automatically terminates as a result of being canceled.</span></span> <span data-ttu-id="14b71-190">Dies funktioniert, da auf Auftreten einer `co_await` Ausdruck eine Coroutine überprüft, ob sie abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="14b71-190">This works because, on encountering a `co_await` expression, a coroutine checks whether it has been cancelled.</span></span> <span data-ttu-id="14b71-191">Wenn dies der Fall, kurzgeschlossen wird dann es sich; und wenn dies nicht der Fall, dann angehalten wie gewohnt.</span><span class="sxs-lookup"><span data-stu-id="14b71-191">If it has, then it short-circuits out; and if it hasn't, then it suspends as normal.</span></span>

<span data-ttu-id="14b71-192">Kündigung kann, natürlich auftreten, während die Coroutine angehalten ist.</span><span class="sxs-lookup"><span data-stu-id="14b71-192">Cancellation can, of course, happen while the coroutine is suspended.</span></span> <span data-ttu-id="14b71-193">Nur, wenn die Coroutine fortgesetzt wird, oder Treffer ein anderes `co_await`, wird es nach einem Abbruch suchen.</span><span class="sxs-lookup"><span data-stu-id="14b71-193">Only when the coroutine resumes, or hits another `co_await`, will it check for cancellation.</span></span> <span data-ttu-id="14b71-194">Das Problem ist eine der potenziell zu grob-differenziertere Latenz bei der Behandlung von Abbruch.</span><span class="sxs-lookup"><span data-stu-id="14b71-194">The issue is one of potentially too-coarse-grained latency in responding to cancellation.</span></span>

<span data-ttu-id="14b71-195">Daher ist eine weitere Möglichkeit explizit für den Abbruch von innerhalb der Coroutine abgefragt werden soll.</span><span class="sxs-lookup"><span data-stu-id="14b71-195">So, another option is to explicitly poll for cancellation from within your coroutine.</span></span> <span data-ttu-id="14b71-196">Aktualisieren Sie das obige Beispiel, mit der Code in den folgenden Eintrag.</span><span class="sxs-lookup"><span data-stu-id="14b71-196">Update the example above with the code in the listing below.</span></span> <span data-ttu-id="14b71-197">In diesem Beispiel neue **ExplicitCancellationAsync** Ruft das von der Funktion [**winrt::get_cancellation_token**](/uwp/cpp-ref-for-winrt/get-cancellation-token) zurückgegebene Objekt ab, und verwendet ihn zum Überprüfen Sie regelmäßig, ob die Coroutine abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="14b71-197">In this new example, **ExplicitCancellationAsync** retrieves the object returned by the [**winrt::get_cancellation_token**](/uwp/cpp-ref-for-winrt/get-cancellation-token) function, and uses it to periodically check whether the coroutine has been canceled.</span></span> <span data-ttu-id="14b71-198">Solange sie nicht abgebrochen wird, überblendanimation die Coroutine; nach der Vorgang abgebrochen wird, beenden Sie die Schleife und die Funktion in der Regel.</span><span class="sxs-lookup"><span data-stu-id="14b71-198">As long as it's not canceled, the coroutine loops indefinitely; once it is canceled, the loop and the function exit normally.</span></span> <span data-ttu-id="14b71-199">Das Ergebnis ist identisch mit dem vorherigen Beispiel, aber hier beenden geschieht explizit und gesteuert.</span><span class="sxs-lookup"><span data-stu-id="14b71-199">The outcome is the same as the previous example, but here exiting happens explicitly, and under control.</span></span>

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

<span data-ttu-id="14b71-200">Warten auf **winrt::get_cancellation_token** Ruft ein Abbruchtoken mit Kenntnisse über die **IAsyncAction** , die die Coroutine vorliegt in Ihrem Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="14b71-200">Waiting on **winrt::get_cancellation_token** retrieves a cancellation token with knowledge of the **IAsyncAction** that the coroutine is producing on your behalf.</span></span> <span data-ttu-id="14b71-201">Können Sie Funktionsaufrufoperators auf diesem Token Abfragen, den Abbruch Zustand&mdash;im Wesentlichen Abbruch abrufen.</span><span class="sxs-lookup"><span data-stu-id="14b71-201">You can use the function call operator on that token to query the cancellation state&mdash;essentially polling for cancellation.</span></span> <span data-ttu-id="14b71-202">Wenn Sie einige rechengebundene Vorgang, oder einer großen Sammlung durchlaufen, ist dies eine angemessene Technik.</span><span class="sxs-lookup"><span data-stu-id="14b71-202">If you're performing some compute-bound operation, or iterating through a large collection, then this is a reasonable technique.</span></span>

### <a name="register-a-cancellation-callback"></a><span data-ttu-id="14b71-203">Registrieren eines Rückrufs Abbruch</span><span class="sxs-lookup"><span data-stu-id="14b71-203">Register a cancellation callback</span></span>
<span data-ttu-id="14b71-204">Der Windows-Runtime Abbruch übertragen nicht automatisch auf andere asynchrone Objekte.</span><span class="sxs-lookup"><span data-stu-id="14b71-204">The Windows Runtime's cancellation doesn't automatically flow to other asynchronous objects.</span></span> <span data-ttu-id="14b71-205">Aber&mdash;eingeführt, in dem Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809)&mdash;können Sie einen Rückruf Abbruch registrieren.</span><span class="sxs-lookup"><span data-stu-id="14b71-205">But&mdash;introduced in version 10.0.17763.0 (Windows 10, version 1809) of the Windows SDK&mdash;you can register a cancellation callback.</span></span> <span data-ttu-id="14b71-206">Hierbei handelt es sich um eine vorbeugenden Häkchen mit dem Abbruch weitergegeben werden kann, und ermöglicht die Integration in vorhandene Concurrency-Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="14b71-206">This is a pre-emptive hook by which cancellation can be propagated, and makes it possible to integrate with existing concurrency libraries.</span></span>

<span data-ttu-id="14b71-207">In dieses nächste Codebeispiel **NestedCoroutineAsync** funktioniert, aber es weist keine spezielle Abbruchlogik auf.</span><span class="sxs-lookup"><span data-stu-id="14b71-207">In this next code example, **NestedCoroutineAsync** does the work, but it has no special cancellation logic in it.</span></span> <span data-ttu-id="14b71-208">**CancellationPropagatorAsync** ist im Grunde ein Wrapper für die geschachtelte Coroutine. der Wrapper leitet Abbruch präventiven.</span><span class="sxs-lookup"><span data-stu-id="14b71-208">**CancellationPropagatorAsync** is essentially a wrapper on the nested coroutine; the wrapper forwards cancellation pre-emptively.</span></span>

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

<span data-ttu-id="14b71-209">**CancellationPropagatorAsync** registriert eine Lambda-Funktion für eine eigene Abbruch Rückruf, und es anschließend wartet auf (angehalten) erst die geschachtelte Arbeit abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="14b71-209">**CancellationPropagatorAsync** registers a lambda function for its own cancellation callback, and then it awaits (it suspends) until the nested work completes.</span></span> <span data-ttu-id="14b71-210">Wenn oder **CancellationPropagatorAsync** abgebrochen wird, wird der Abbruch an die geschachtelte Coroutine weitergegeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-210">When or if **CancellationPropagatorAsync** is canceled, it propagates the cancellation to the nested coroutine.</span></span> <span data-ttu-id="14b71-211">Es ist nicht erforderlich für den Abbruch abgefragt werden soll. Außerdem ist Abbruch auf unbestimmte Zeit blockiert.</span><span class="sxs-lookup"><span data-stu-id="14b71-211">There's no need to poll for cancellation; nor is cancellation blocked indefinitely.</span></span> <span data-ttu-id="14b71-212">Dieser Mechanismus ist flexibel genug für Sie es auf der Interoperabilität mit einer Coroutine oder Concurrency-Bibliothek verwenden, die weiß nichts von C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="14b71-212">This mechanism is flexible enough for you to use it to interop with a coroutine or concurrency library that knows nothing of C++/WinRT.</span></span>

## <a name="reporting-progress"></a><span data-ttu-id="14b71-213">Melden des Status</span><span class="sxs-lookup"><span data-stu-id="14b71-213">Reporting progress</span></span>

<span data-ttu-id="14b71-214">Wenn Ihre Coroutine [**IAsyncActionWithProgress**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)oder [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)zurückgegeben wird, können dann das von der Funktion [**winrt::get_progress_token**](/uwp/cpp-ref-for-winrt/get-progress-token) zurückgegebene Objekt abzurufen, und verwenden, um den Fortschritt an einem Fortschritt Handler.</span><span class="sxs-lookup"><span data-stu-id="14b71-214">If your coroutine returns either [**IAsyncActionWithProgress**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_), or [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_), then you can retrieve the object returned by the [**winrt::get_progress_token**](/uwp/cpp-ref-for-winrt/get-progress-token) function, and use it to report progress back to a progress handler.</span></span> <span data-ttu-id="14b71-215">Dies ist ein Codebeispiel:</span><span class="sxs-lookup"><span data-stu-id="14b71-215">Here's a code example.</span></span>

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
> <span data-ttu-id="14b71-216">Es ist nicht korrekt mehrere *Abschlusshandler* für eine asynchrone Aktion oder eines Vorgangs zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="14b71-216">It's not correct to implement more than one *completion handler* for an asynchronous action or operation.</span></span> <span data-ttu-id="14b71-217">Sie können entweder einen einzelnen Delegaten für das abgeschlossene Ereignis haben, oder Sie können `co_await` es.</span><span class="sxs-lookup"><span data-stu-id="14b71-217">You can have either a single delegate for its completed event, or you can `co_await` it.</span></span> <span data-ttu-id="14b71-218">Wenn Sie beide haben, wird die zweite fehl.</span><span class="sxs-lookup"><span data-stu-id="14b71-218">If you have both, then the second will fail.</span></span> <span data-ttu-id="14b71-219">Entweder die folgenden zwei Arten von Abschlusshandler eignet sich; nicht beide für das gleiche Async-Objekt.</span><span class="sxs-lookup"><span data-stu-id="14b71-219">Either one of the following two kinds of completion handlers is appropriate; not both for the same async object.</span></span>

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

<span data-ttu-id="14b71-220">Weitere Informationen zur Abschlusshandler finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span><span class="sxs-lookup"><span data-stu-id="14b71-220">For more info about completion handlers, see [Delegate types for asynchronous actions and operations](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span></span>

## <a name="fire-and-forget"></a><span data-ttu-id="14b71-221">Auslösen und vergessen</span><span class="sxs-lookup"><span data-stu-id="14b71-221">Fire and forget</span></span>

<span data-ttu-id="14b71-222">In manchen Fällen Sie haben eine Aufgabe, die gleichzeitig mit anderen Vorgängen ausgeführt werden kann, und Sie müssen nicht warten, dass dieser Vorgang abschließen (keine anderen Vorgängen hängt es), auch nicht erforderlich, um einen Wert zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="14b71-222">Sometimes, you have a task that can be done concurrently with other work, and you don't need to wait for that task to complete (no other work depends on it), nor do you need it to return a value.</span></span> <span data-ttu-id="14b71-223">In diesem Fall können Sie aus der Aufgabe ausgelöst und vergessen.</span><span class="sxs-lookup"><span data-stu-id="14b71-223">In that case, you can fire off the task and forget it.</span></span> <span data-ttu-id="14b71-224">Sie können dies tun, durch das Schreiben einer Coroutine, deren Rückgabetyp [**winrt::fire_and_forget**](/uwp/cpp-ref-for-winrt/fire-and-forget) (anstelle eines der Windows-Runtime-Typen für asynchrone Vorgänge, oder **Concurrency:: Task**) ist.</span><span class="sxs-lookup"><span data-stu-id="14b71-224">You can do that by writing a coroutine whose return type is [**winrt::fire_and_forget**](/uwp/cpp-ref-for-winrt/fire-and-forget) (instead of one of the Windows Runtime asynchronous operation types, or **concurrency::task**).</span></span>

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

## <a name="important-apis"></a><span data-ttu-id="14b71-225">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="14b71-225">Important APIs</span></span>
* [<span data-ttu-id="14b71-226">Concurrency:: Task-Klasse</span><span class="sxs-lookup"><span data-stu-id="14b71-226">concurrency::task class</span></span>](/cpp/parallel/concrt/reference/task-class)
* [<span data-ttu-id="14b71-227">IAsyncAction-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="14b71-227">IAsyncAction interface</span></span>](/uwp/api/windows.foundation.iasyncaction)
* [<span data-ttu-id="14b71-228">IAsyncActionWithProgress&lt;TProgress&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="14b71-228">IAsyncActionWithProgress&lt;TProgress&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [<span data-ttu-id="14b71-229">IAsyncOperation&lt;TResult&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="14b71-229">IAsyncOperation&lt;TResult&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [<span data-ttu-id="14b71-230">IAsyncOperationWithProgress&lt;TResult, TProgress&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="14b71-230">IAsyncOperationWithProgress&lt;TResult, TProgress&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [<span data-ttu-id="14b71-231">Syndicationclient:: Retrievefeedasync-Methode</span><span class="sxs-lookup"><span data-stu-id="14b71-231">SyndicationClient::RetrieveFeedAsync method</span></span>](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [<span data-ttu-id="14b71-232">SyndicationFeed-Klasse</span><span class="sxs-lookup"><span data-stu-id="14b71-232">SyndicationFeed class</span></span>](/uwp/api/windows.web.syndication.syndicationfeed)
* [<span data-ttu-id="14b71-233">WinRT::get_cancellation_token</span><span class="sxs-lookup"><span data-stu-id="14b71-233">winrt::get_cancellation_token</span></span>](/uwp/cpp-ref-for-winrt/get-cancellation-token)
* [<span data-ttu-id="14b71-234">WinRT::get_progress_token</span><span class="sxs-lookup"><span data-stu-id="14b71-234">winrt::get_progress_token</span></span>](/uwp/cpp-ref-for-winrt/get-progress-token)
* [<span data-ttu-id="14b71-235">WinRT::fire_and_forget</span><span class="sxs-lookup"><span data-stu-id="14b71-235">winrt::fire_and_forget</span></span>](/uwp/cpp-ref-for-winrt/fire-and-forget)

## <a name="related-topics"></a><span data-ttu-id="14b71-236">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="14b71-236">Related topics</span></span>
* [<span data-ttu-id="14b71-237">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="14b71-237">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
* [<span data-ttu-id="14b71-238">Standard C++ Datentypen und C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="14b71-238">Standard C++ data types and C++/WinRT</span></span>](std-cpp-data-types.md)