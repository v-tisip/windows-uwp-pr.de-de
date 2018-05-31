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
# <a name="concurrency-and-asynchronous-operations-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="6504e-104">Parallelität und asynchrone Vorgänge mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="6504e-104">Concurrency and asynchronous operations with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
<span data-ttu-id="6504e-105">Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.</span><span class="sxs-lookup"><span data-stu-id="6504e-105">This topic shows the ways in which you can both create and consume Windows Runtime asynchronous objects with C++/WinRT.</span></span>

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a><span data-ttu-id="6504e-106">Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen</span><span class="sxs-lookup"><span data-stu-id="6504e-106">Asynchronous operations and Windows Runtime "Async" functions</span></span>
<span data-ttu-id="6504e-107">Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet).</span><span class="sxs-lookup"><span data-stu-id="6504e-107">Any Windows Runtime API that has the potential to take more than 50 milliseconds to complete is implemented as an asynchronous function (with a name ending in "Async").</span></span> <span data-ttu-id="6504e-108">Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="6504e-108">The implementation of an asynchronous function initiates the work on another thread and returns immediately with an object that represents the asynchronous operation.</span></span> <span data-ttu-id="6504e-109">Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt.</span><span class="sxs-lookup"><span data-stu-id="6504e-109">When the asynchronous operation completes, that returned object contains any value that resulted from the work.</span></span> <span data-ttu-id="6504e-110">Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge. Diese sind:</span><span class="sxs-lookup"><span data-stu-id="6504e-110">The **Windows::Foundation** Windows Runtime namespace contains four types of asynchronous operation object, and they are</span></span>

- <span data-ttu-id="6504e-111">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span><span class="sxs-lookup"><span data-stu-id="6504e-111">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span></span>
- <span data-ttu-id="6504e-112">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span><span class="sxs-lookup"><span data-stu-id="6504e-112">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span></span>
- <span data-ttu-id="6504e-113">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und</span><span class="sxs-lookup"><span data-stu-id="6504e-113">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_), and</span></span>
- <span data-ttu-id="6504e-114">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span><span class="sxs-lookup"><span data-stu-id="6504e-114">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span>

<span data-ttu-id="6504e-115">Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert.</span><span class="sxs-lookup"><span data-stu-id="6504e-115">Each of these asynchronous operation types is projected into a corresponding type in the **winrt::Windows::Foundation** C++/WinRT namespace.</span></span> <span data-ttu-id="6504e-116">C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur.</span><span class="sxs-lookup"><span data-stu-id="6504e-116">C++/WinRT also contains an internal await adapter struct.</span></span> <span data-ttu-id="6504e-117">Sie verwenden diese nicht direkt, aber dank dieser Struktur können Sie eine **co_await**-Anweisung schreiben, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asychrone Vorgänge zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="6504e-117">You don't use it directly but, thanks to that struct, you can write a **co_await** statement to cooperatively await the result of any function that returns one of these asychronous operation types.</span></span> <span data-ttu-id="6504e-118">Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="6504e-118">And you can author your own coroutines that return these types.</span></span>

<span data-ttu-id="6504e-119">Ein Beispiel für eine asynchrone Windows-Funktion ist [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), die ein Objekt für einen asynchronen Vorgang vom Typ [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="6504e-119">An example of an asynchronous Windows function is [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), which returns an asynchronous operation object of type [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span> <span data-ttu-id="6504e-120">Betrachten wir einige (blockierende und nicht blockierende) Möglichkeiten der Verwendung von C++/WinRT, um eine solche API aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="6504e-120">Let's look at some ways&mdash;blocking and non-blocking&mdash;of using C++/WinRT to call an API such as that.</span></span>

## <a name="block-the-calling-thread"></a><span data-ttu-id="6504e-121">Den aufrufenden Thread blockieren</span><span class="sxs-lookup"><span data-stu-id="6504e-121">Block the calling thread</span></span>
<span data-ttu-id="6504e-122">Das folgende Codebeispiel erhält ein Objekt für asynchronen Vorgänge von **RetrieveFeedAsync** und ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren, bis die Ergebnisse des asynchronen Vorgangs vorliegen.</span><span class="sxs-lookup"><span data-stu-id="6504e-122">The code example below receives an asynchronous operation object from **RetrieveFeedAsync**, and it calls **get** on that object to block the calling thread until the results of the asynchronous operation are available.</span></span>

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

<span data-ttu-id="6504e-123">Der Aufruf von **get** ermöglicht eine bequeme Codeerstellung. Als kooperativ kann man ihn jedoch nicht bezeichnen.</span><span class="sxs-lookup"><span data-stu-id="6504e-123">Calling **get** makes for convenient coding, but it's not what you'd call cooperative.</span></span> <span data-ttu-id="6504e-124">Es arbeitet weder gleichzeitig noch asynchron.</span><span class="sxs-lookup"><span data-stu-id="6504e-124">It's not concurrent nor asynchronous.</span></span> <span data-ttu-id="6504e-125">Um Betriebssystem-Threads nicht daran zu hindern, andere nützliche Aufgaben zu erledigen, benötigen wir eine andere Technik.</span><span class="sxs-lookup"><span data-stu-id="6504e-125">To avoid holding up OS threads from doing other useful work, we need a different technique.</span></span>

## <a name="write-a-coroutine"></a><span data-ttu-id="6504e-126">Schreiben einer Coroutine</span><span class="sxs-lookup"><span data-stu-id="6504e-126">Write a coroutine</span></span>
<span data-ttu-id="6504e-127">C++/WinRT integriert C++ Coroutinen in das Programmiermodell, um eine natürliche Möglichkeit zu bieten, kooperativ auf ein Ergebnis zu warten.</span><span class="sxs-lookup"><span data-stu-id="6504e-127">C++/WinRT integrates C++ coroutines into the programming model to provide a natural way to cooperatively wait for a result.</span></span> <span data-ttu-id="6504e-128">Sie können Ihre eigene asynchronen Windows-Runtime-Vorgänge erzeugen, indem Sie eine Coroutine schreiben.</span><span class="sxs-lookup"><span data-stu-id="6504e-128">You can produce your own Windows Runtime asynchronous operation by writing a coroutine.</span></span> <span data-ttu-id="6504e-129">Im folgenden Codebeispiel ist **ProcessFeedAsync** die Coroutine.</span><span class="sxs-lookup"><span data-stu-id="6504e-129">In the code example below, **ProcessFeedAsync** is the coroutine.</span></span>

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

<span data-ttu-id="6504e-130">Eine Coroutine ist eine Funktion, die angehalten und wieder fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6504e-130">A coroutine is a function that can be suspended and resumed.</span></span> <span data-ttu-id="6504e-131">Wenn die **co_await**-Anweisung In der **ProcessFeedAsync**-Coroutine oben erreicht ist, initiiert die Coroutine asynchron den **RetrieveFeedAsync**-Aufruf und unterbricht sich dann sofort selbst und gibt die Kontrolle an den Aufrufer zurück (was im obigen Beispiel **main** ist).</span><span class="sxs-lookup"><span data-stu-id="6504e-131">In the **ProcessFeedAsync** coroutine above, when the **co_await** statement is reached, the coroutine asynchronously initiates the **RetrieveFeedAsync** call and then it immediately suspends itself and returns control back to the caller (which is **main** in the example above).</span></span> <span data-ttu-id="6504e-132">**main** kann dann weiterarbeiten, während der Feed abgerufen und ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="6504e-132">**main** can then continue to do work while the feed is being retrieved and printed.</span></span> <span data-ttu-id="6504e-133">Wenn das erledigt ist (wenn der **RetrieveFeedAsync**-Aufruf abgeschlossen ist), wird die **ProcessFeedAsync**-Coroutine bei der nächsten Anweisung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="6504e-133">When that's done (when the **RetrieveFeedAsync** call completes), the **ProcessFeedAsync** coroutine resumes at the next statement.</span></span>

<span data-ttu-id="6504e-134">Sie können eine Coroutine in anderen Coroutinen zusammenfassen.</span><span class="sxs-lookup"><span data-stu-id="6504e-134">You can aggregate a couroutine into other coroutines.</span></span> <span data-ttu-id="6504e-135">Oder Sie können **get** zur Blockierung aufrufen und warten, bis sie abgeschlossen ist (und das Ergebnis erhalten, wenn es eines gibt).</span><span class="sxs-lookup"><span data-stu-id="6504e-135">Or you can call **get** to block and wait for it to complete (and get the result if there is one).</span></span> <span data-ttu-id="6504e-136">Oder Sie können sie an eine andere Programmiersprache übergeben, die Windows-Runtime unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6504e-136">Or you can pass it to another programming language that supports the Windows Runtime.</span></span>

<span data-ttu-id="6504e-137">Es ist auch möglich, die Completed- und/oder Progress-Ereignisse von asynchronen Aktionen und Vorgängen mit Hilfe von Delegaten zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="6504e-137">It's also possible to handle the completed and/or progress events of asynchronous actions and operations by using delegates.</span></span> <span data-ttu-id="6504e-138">Details und Codebeispiele finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span><span class="sxs-lookup"><span data-stu-id="6504e-138">For details, and code examples, see [Delegate types for asynchronous actions and operations](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span></span>

## <a name="asychronously-return-a-windows-runtime-type"></a><span data-ttu-id="6504e-139">Asychrone Rückgabe eines Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="6504e-139">Asychronously return a Windows Runtime type</span></span>
<span data-ttu-id="6504e-140">In diesem nächsten Beispiel verpacken wir einen Aufruf von **RetrieveFeedAsync** für eine bestimmte URI, um uns eine **RetrieveBlogFeedAsync**-Funktion zu holen, die asynchron ein [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="6504e-140">In this next example we wrap a call to **RetrieveFeedAsync**, for a specific URI, to give us a **RetrieveBlogFeedAsync** function that asynchronously returns a [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed).</span></span>

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

<span data-ttu-id="6504e-141">Im obigen Beispiel gibt **RetrieveBlogFeedAsync** ein **IAsyncOperationWithProgress** zurück, das sowohl einen Progress- als auch einen Return-Wert hat.</span><span class="sxs-lookup"><span data-stu-id="6504e-141">In the example above, **RetrieveBlogFeedAsync** returns an **IAsyncOperationWithProgress**, which has both progress and a return value.</span></span> <span data-ttu-id="6504e-142">Wir können andere Arbeiten durchführen, während **RetrieveBlogFeedAsync** sein Ding macht und den Feed abruft.</span><span class="sxs-lookup"><span data-stu-id="6504e-142">We can do other work while **RetrieveBlogFeedAsync** is doing its thing and retrieving the feed.</span></span> <span data-ttu-id="6504e-143">Dann rufen wir das **get**-Objekt des asynchronen Vorgangs auf, um es zu blockieren, warten, bis es abgeschlossen ist, und erhalten dann die Ergebnisse des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="6504e-143">Then, we call **get** on that asynchronous operation object to block, wait for it to complete, and then obtain the results of the operation.</span></span>

<span data-ttu-id="6504e-144">Wenn Sie einen Windows-Runtime-Typ asynchron zurückgeben (unabhängig davon, ob es sich um einen internen oder einen Drittanbietertyp handelt), sollten Sie ein [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) oder ein [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="6504e-144">If you're asynchronously returning a Windows Runtime type (whether that's a first-party or a third-party type), then you should return an [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) or an [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span>

<span data-ttu-id="6504e-145">Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie versuchen, einen dieser Typen für asychrone Vorgänge mit einem Nicht-Windows-Runtime-Typ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6504e-145">The compiler will help you with a "*must be WinRT type*" error if you try to use one of these asychronous operation types with a non-Windows Runtime type.</span></span>

## <a name="asychronously-return-a-non-windows-runtime-type"></a><span data-ttu-id="6504e-146">Asychrone Rückgabe eines Nicht-Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="6504e-146">Asychronously return a non-Windows-Runtime type</span></span>
<span data-ttu-id="6504e-147">Wenn Sie asynchron einen Typ zurückgeben, der *kein* Windows-Runtime-Typ ist, sollten Sie ein Parallel Patterns Library (PPL) [**Task**](https://msdn.microsoft.com/library/hh750113)zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="6504e-147">If you're asynchronously returning a type that's *not* a Windows Runtime type, then you should return a Parallel Patterns Library (PPL) [**task**](https://msdn.microsoft.com/library/hh750113).</span></span> <span data-ttu-id="6504e-148">Wir empfehlen **task**, weil es eine bessere Performance (und später eine bessere Kompatibilität) bietet als **std::future**.</span><span class="sxs-lookup"><span data-stu-id="6504e-148">We recommend **task** because it gives you better performance (and better compatibility going forward) than **std::future** does.</span></span>

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

## <a name="important-apis"></a><span data-ttu-id="6504e-149">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="6504e-149">Important APIs</span></span>
* [<span data-ttu-id="6504e-150">concurrency::task</span><span class="sxs-lookup"><span data-stu-id="6504e-150">concurrency::task</span></span>](https://msdn.microsoft.com/library/hh750113)
* [<span data-ttu-id="6504e-151">IAsyncAction</span><span class="sxs-lookup"><span data-stu-id="6504e-151">IAsyncAction</span></span>](/uwp/api/windows.foundation.iasyncaction)
* [<span data-ttu-id="6504e-152">IAsyncActionWithProgress&lt;TProgress&gt;</span><span class="sxs-lookup"><span data-stu-id="6504e-152">IAsyncActionWithProgress&lt;TProgress&gt;</span></span>](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [<span data-ttu-id="6504e-153">IAsyncOperation&lt;TResult&gt;</span><span class="sxs-lookup"><span data-stu-id="6504e-153">IAsyncOperation&lt;TResult&gt;</span></span>](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [<span data-ttu-id="6504e-154">IAsyncOperationWithProgress&lt;TResult, TProgress&gt;</span><span class="sxs-lookup"><span data-stu-id="6504e-154">IAsyncOperationWithProgress&lt;TResult, TProgress&gt;</span></span>](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [<span data-ttu-id="6504e-155">SyndicationClient::RetrieveFeedAsync</span><span class="sxs-lookup"><span data-stu-id="6504e-155">SyndicationClient::RetrieveFeedAsync</span></span>](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [<span data-ttu-id="6504e-156">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="6504e-156">SyndicationFeed</span></span>](/uwp/api/windows.web.syndication.syndicationfeed)
