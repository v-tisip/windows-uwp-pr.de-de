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
ms.openlocfilehash: 85071fb28cb87c991e2f5ba7f64b681c6850c819
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3824794"
---
# <a name="concurrency-and-asynchronous-operations-with-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt"></a><span data-ttu-id="fc4a2-104">Parallelität und asynchrone Vorgänge mit [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span><span class="sxs-lookup"><span data-stu-id="fc4a2-104">Concurrency and asynchronous operations with [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)</span></span>
> [!NOTE]
> **<span data-ttu-id="fc4a2-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="fc4a2-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="fc4a2-107">Dieses Thema zeigt, wie Sie asynchrone Windows-Runtime-Objekte mit C++/WinRT erstellen und nutzen können.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-107">This topic shows the ways in which you can both create and consume Windows Runtime asynchronous objects with C++/WinRT.</span></span>

## <a name="asynchronous-operations-and-windows-runtime-async-functions"></a><span data-ttu-id="fc4a2-108">Asynchrone Vorgänge und Windows-Runtime-”Async”-Funktionen</span><span class="sxs-lookup"><span data-stu-id="fc4a2-108">Asynchronous operations and Windows Runtime "Async" functions</span></span>
<span data-ttu-id="fc4a2-109">Jede Windows-Runtime-API, die mehr als 50 Millisekunden dauern kann, ist als asynchrone Funktion implementiert (mit einem Namen, der auf „Async” endet).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-109">Any Windows Runtime API that has the potential to take more than 50 milliseconds to complete is implemented as an asynchronous function (with a name ending in "Async").</span></span> <span data-ttu-id="fc4a2-110">Die Implementierung einer asynchronen Funktion initiiert die Arbeit in einem anderen Thread und kehrt direkt mit einem Objekt zurück, das den asynchronen Vorgang repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-110">The implementation of an asynchronous function initiates the work on another thread and returns immediately with an object that represents the asynchronous operation.</span></span> <span data-ttu-id="fc4a2-111">Wenn der asynchrone Vorgang abgeschlossen ist, enthält das zurückgegebene Objekt einen Wert, der das Ergebnis darstellt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-111">When the asynchronous operation completes, that returned object contains any value that resulted from the work.</span></span> <span data-ttu-id="fc4a2-112">Der **Windows::Foundation**-Windows-Runtime-Namespace enthält vier Typen von Objekten für asynchrone Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-112">The **Windows::Foundation** Windows Runtime namespace contains four types of asynchronous operation object.</span></span>

- <span data-ttu-id="fc4a2-113">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span><span class="sxs-lookup"><span data-stu-id="fc4a2-113">[**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction),</span></span>
- <span data-ttu-id="fc4a2-114">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span><span class="sxs-lookup"><span data-stu-id="fc4a2-114">[**IAsyncActionWithProgress&lt;TProgress&gt;**](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_),</span></span>
- <span data-ttu-id="fc4a2-115">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) und</span><span class="sxs-lookup"><span data-stu-id="fc4a2-115">[**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_), and</span></span>
- <span data-ttu-id="fc4a2-116">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-116">[**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span>

<span data-ttu-id="fc4a2-117">Jeder dieser Typen für asynchrone Vorgänge wird auf einen entsprechenden Typ im C++/WinRT-Namespace **winrt::Windows::Foundation** projiziert.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-117">Each of these asynchronous operation types is projected into a corresponding type in the **winrt::Windows::Foundation** C++/WinRT namespace.</span></span> <span data-ttu-id="fc4a2-118">C++/WinRT enthält außerdem eine interne Await-Adapter-Struktur.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-118">C++/WinRT also contains an internal await adapter struct.</span></span> <span data-ttu-id="fc4a2-119">Sie verwenden diese nicht direkt, aber dank dieser Struktur können Sie eine „co_await“-Anweisung schreiben, um kooperativ auf das Ergebnis einer Funktion zu warten, die einen dieser Typen für asynchrone Vorgänge zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-119">You don't use it directly but, thanks to that struct, you can write a \`\`co_await\` statement to cooperatively await the result of any function that returns one of these asychronous operation types.</span></span> <span data-ttu-id="fc4a2-120">Und Sie können Ihre eigenen Coroutinen schreiben, die diese Typen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-120">And you can author your own coroutines that return these types.</span></span>

<span data-ttu-id="fc4a2-121">Ein Beispiel für eine asynchrone Windows-Funktion ist [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), die ein Objekt für einen asynchronen Vorgang vom Typ [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-121">An example of an asynchronous Windows function is [**SyndicationClient::RetrieveFeedAsync**](https://docs.microsoft.com/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync), which returns an asynchronous operation object of type [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span> <span data-ttu-id="fc4a2-122">Betrachten wir einige (blockierende und nicht blockierende) Möglichkeiten der Verwendung von C++/WinRT, um eine solche API aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-122">Let's look at some ways&mdash;blocking and non-blocking&mdash;of using C++/WinRT to call an API such as that.</span></span>

## <a name="block-the-calling-thread"></a><span data-ttu-id="fc4a2-123">Den aufrufenden Thread blockieren</span><span class="sxs-lookup"><span data-stu-id="fc4a2-123">Block the calling thread</span></span>
<span data-ttu-id="fc4a2-124">Das folgende Codebeispiel erhält ein Objekt für asynchronen Vorgänge von **RetrieveFeedAsync** und ruft **get** für dieses Objekt auf, um den aufrufenden Thread zu blockieren, bis die Ergebnisse des asynchronen Vorgangs vorliegen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-124">The code example below receives an asynchronous operation object from **RetrieveFeedAsync**, and it calls **get** on that object to block the calling thread until the results of the asynchronous operation are available.</span></span>

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

<span data-ttu-id="fc4a2-125">Der Aufruf von **get** ermöglicht eine bequeme Codeerstellung und eignet sich perfekt für Konsolenapps oder Hintergrundthreads, in denen Sie möglicherweise keine Coroutine verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-125">Calling **get** makes for convenient coding, and it's ideal for console apps or background threads where you may not want to use a coroutine for whatever reason.</span></span> <span data-ttu-id="fc4a2-126">Sie ist jedoch weder parallel noch asynchron und folglich eignet sie sich nicht für einen UI-Thread (außerdem wird eine Assertion in nicht optimierten Builds ausgelöst, wenn Sie versuchen, sie dafür zu verwenden).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-126">But it's not concurrent nor asynchronous, so it's not appropriate for a UI thread (and an assertion will fire in unoptimized builds if you attempt to use it on one).</span></span> <span data-ttu-id="fc4a2-127">Um Betriebssystem-Threads nicht daran zu hindern, andere nützliche Aufgaben zu erledigen, benötigen wir eine andere Technik.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-127">To avoid holding up OS threads from doing other useful work, we need a different technique.</span></span>

## <a name="write-a-coroutine"></a><span data-ttu-id="fc4a2-128">Schreiben einer Coroutine</span><span class="sxs-lookup"><span data-stu-id="fc4a2-128">Write a coroutine</span></span>
<span data-ttu-id="fc4a2-129">C++/WinRT integriert C++ Coroutinen in das Programmiermodell, um eine natürliche Möglichkeit zu bieten, kooperativ auf ein Ergebnis zu warten.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-129">C++/WinRT integrates C++ coroutines into the programming model to provide a natural way to cooperatively wait for a result.</span></span> <span data-ttu-id="fc4a2-130">Sie können Ihre eigene asynchronen Windows-Runtime-Vorgänge erzeugen, indem Sie eine Coroutine schreiben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-130">You can produce your own Windows Runtime asynchronous operation by writing a coroutine.</span></span> <span data-ttu-id="fc4a2-131">Im folgenden Codebeispiel ist **ProcessFeedAsync** die Coroutine.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-131">In the code example below, **ProcessFeedAsync** is the coroutine.</span></span>

> [!NOTE]
> <span data-ttu-id="fc4a2-132">Die **get** -Funktion vorhanden ist, auf der C++ / WinRT-Projektion geben **Winrt::Windows::Foundation::IAsyncAction**, sodass rufen Sie die Funktion in jeder C++ / WinRT-Projekt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-132">The **get** function exists on the C++/WinRT projection type **winrt::Windows::Foundation::IAsyncAction**, so you can call the function from within any C++/WinRT project.</span></span> <span data-ttu-id="fc4a2-133">Die Funktion als Mitglied der [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) -Schnittstelle, aufgeführt werden nicht gefunden werden, da **erhalten** nicht der Application binary Interface (ABI) Fläche des tatsächlichen Windows-Runtime-Typs **IAsyncAction**gehört.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-133">You will not find the function listed as a member of the [**IAsyncAction**](/uwp/api/windows.foundation.iasyncaction) interface, because **get** is not part of the application binary interface (ABI) surface of the actual Windows Runtime type **IAsyncAction**.</span></span>

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

<span data-ttu-id="fc4a2-134">Eine Coroutine ist eine Funktion, die angehalten und wieder fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-134">A coroutine is a function that can be suspended and resumed.</span></span> <span data-ttu-id="fc4a2-135">Wenn die `co_await`-Anweisung In der **ProcessFeedAsync**-Coroutine oben erreicht ist, initiiert die Coroutine asynchron den **RetrieveFeedAsync**-Aufruf und unterbricht sich dann sofort selbst und gibt die Kontrolle an den Aufrufer zurück (was im obigen Beispiel **main** ist).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-135">In the **ProcessFeedAsync** coroutine above, when the `co_await` statement is reached, the coroutine asynchronously initiates the **RetrieveFeedAsync** call and then it immediately suspends itself and returns control back to the caller (which is **main** in the example above).</span></span> <span data-ttu-id="fc4a2-136">**main** kann dann weiterarbeiten, während der Feed abgerufen und ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-136">**main** can then continue to do work while the feed is being retrieved and printed.</span></span> <span data-ttu-id="fc4a2-137">Wenn das erledigt ist (wenn der **RetrieveFeedAsync**-Aufruf abgeschlossen ist), wird die **ProcessFeedAsync**-Coroutine bei der nächsten Anweisung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-137">When that's done (when the **RetrieveFeedAsync** call completes), the **ProcessFeedAsync** coroutine resumes at the next statement.</span></span>

<span data-ttu-id="fc4a2-138">Sie können eine Coroutine in anderen Coroutinen zusammenfassen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-138">You can aggregate a coroutine into other coroutines.</span></span> <span data-ttu-id="fc4a2-139">Oder Sie können **get** zur Blockierung aufrufen und warten, bis sie abgeschlossen ist (und das Ergebnis erhalten, wenn es eines gibt).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-139">Or you can call **get** to block and wait for it to complete (and get the result if there is one).</span></span> <span data-ttu-id="fc4a2-140">Oder Sie können sie an eine andere Programmiersprache übergeben, die Windows-Runtime unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-140">Or you can pass it to another programming language that supports the Windows Runtime.</span></span>

<span data-ttu-id="fc4a2-141">Es ist auch möglich, die Completed- und/oder Progress-Ereignisse von asynchronen Aktionen und Vorgängen mit Hilfe von Delegaten zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-141">It's also possible to handle the completed and/or progress events of asynchronous actions and operations by using delegates.</span></span> <span data-ttu-id="fc4a2-142">Details und Codebeispiele finden Sie unter [Delegattypen für asynchrone Aktionen und Vorgänge](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-142">For details, and code examples, see [Delegate types for asynchronous actions and operations](handle-events.md#delegate-types-for-asynchronous-actions-and-operations).</span></span>

## <a name="asychronously-return-a-windows-runtime-type"></a><span data-ttu-id="fc4a2-143">Asychrone Rückgabe eines Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="fc4a2-143">Asychronously return a Windows Runtime type</span></span>
<span data-ttu-id="fc4a2-144">In diesem nächsten Beispiel verpacken wir einen Aufruf von **RetrieveFeedAsync** für eine bestimmte URI, um uns eine **RetrieveBlogFeedAsync**-Funktion zu holen, die asynchron ein [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed) zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-144">In this next example we wrap a call to **RetrieveFeedAsync**, for a specific URI, to give us a **RetrieveBlogFeedAsync** function that asynchronously returns a [**SyndicationFeed**](/uwp/api/windows.web.syndication.syndicationfeed).</span></span>

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

<span data-ttu-id="fc4a2-145">Im obigen Beispiel gibt **RetrieveBlogFeedAsync** ein **IAsyncOperationWithProgress** zurück, das sowohl einen Progress- als auch einen Return-Wert hat.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-145">In the example above, **RetrieveBlogFeedAsync** returns an **IAsyncOperationWithProgress**, which has both progress and a return value.</span></span> <span data-ttu-id="fc4a2-146">Wir können andere Arbeiten durchführen, während **RetrieveBlogFeedAsync** sein Ding macht und den Feed abruft.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-146">We can do other work while **RetrieveBlogFeedAsync** is doing its thing and retrieving the feed.</span></span> <span data-ttu-id="fc4a2-147">Dann rufen wir das **get**-Objekt des asynchronen Vorgangs auf, um es zu blockieren, warten, bis es abgeschlossen ist, und erhalten dann die Ergebnisse des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-147">Then, we call **get** on that asynchronous operation object to block, wait for it to complete, and then obtain the results of the operation.</span></span>

<span data-ttu-id="fc4a2-148">Wenn Sie einen Windows-Runtime-Typ asynchron zurückgeben, sollten Sie ein [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) oder ein [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-148">If you're asynchronously returning a Windows Runtime type, then you should return an [**IAsyncOperation&lt;TResult&gt;**](/uwp/api/windows.foundation.iasyncoperation_tresult_) or an [**IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_).</span></span> <span data-ttu-id="fc4a2-149">Alle Erst- oder Drittanbieter-Laufzeitklassen sind qualifiziert, oder ein anderer Typ, der an oder von einer Windows-Runtime-Funktion übergeben werden kann (z.B. `int` oder **winrt::hstring**).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-149">Any first- or third-party runtime class qualifies, or any type that can be passed to or from a Windows Runtime function (for example, `int`, or **winrt::hstring**).</span></span> <span data-ttu-id="fc4a2-150">Der Compiler hilft Ihnen mit einem „*WinRT-Typ erforderlich*”-Fehler, wenn Sie versuchen, einen dieser Typen für asychrone Vorgänge mit einem Nicht-Windows-Runtime-Typ zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-150">The compiler will help you with a "*must be WinRT type*" error if you try to use one of these asychronous operation types with a non-Windows Runtime type.</span></span>

<span data-ttu-id="fc4a2-151">Wenn eine Coroutine nicht mindestens eine `co_await`-Anweisung enthält, benötigt sie mindestens eine `co_return`- oder `co_yield`-Anweisung, um sich als Coroutine zu qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-151">If a coroutine doesn't have at least one `co_await` statement then, in order to qualify as a coroutine, it must have at least one `co_return` or one `co_yield` statement.</span></span> <span data-ttu-id="fc4a2-152">Es gibt Fälle, in denen Ihre Coroutine einen Wert zurückgeben kann, ohne dass es zur Asynchronität kommt und ohne dass Kontext blockiert oder gewechselt wird.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-152">There will be cases where your coroutine can return a value without introducing any asynchrony, and therefore without blocking nor switching context.</span></span> <span data-ttu-id="fc4a2-153">Hier ist ein solches Beispiel, das (beim zweiten oder nachfolgenden Aufruf) dafür einen Wert zwischenspeichert.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-153">Here's an example that does that (the second and subsequent times it's called) by caching a value.</span></span>

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

## <a name="asychronously-return-a-non-windows-runtime-type"></a><span data-ttu-id="fc4a2-154">Asychrone Rückgabe eines Nicht-Windows-Runtime-Typs</span><span class="sxs-lookup"><span data-stu-id="fc4a2-154">Asychronously return a non-Windows-Runtime type</span></span>
<span data-ttu-id="fc4a2-155">Wenn Sie asynchron einen Typ zurückgeben, der *kein* Windows-Runtime-Typ ist, sollten Sie ein Parallel Patterns Library (PPL) [**concurrency::task**](/cpp/parallel/concrt/reference/task-class) zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-155">If you're asynchronously returning a type that's *not* a Windows Runtime type, then you should return a Parallel Patterns Library (PPL) [**concurrency::task**](/cpp/parallel/concrt/reference/task-class).</span></span> <span data-ttu-id="fc4a2-156">Wir empfehlen **concurrency::task**, weil es eine bessere Performance (und später eine bessere Kompatibilität) bietet als **std::future**.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-156">We recommend **concurrency::task** because it gives you better performance (and better compatibility going forward) than **std::future** does.</span></span>

> [!TIP]
> <span data-ttu-id="fc4a2-157">Wenn Sie `<pplawait.h>` einschließen, können Sie **concurrency::task** als Coroutinentyp verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-157">If you include `<pplawait.h>`, then you can use **concurrency::task** as a coroutine type.</span></span>

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

## <a name="parameter-passing"></a><span data-ttu-id="fc4a2-158">Parameterübergabe</span><span class="sxs-lookup"><span data-stu-id="fc4a2-158">Parameter-passing</span></span>
<span data-ttu-id="fc4a2-159">Für synchrone Funktionen sollten Sie standardmäßig `const&`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-159">For synchronous functions, you should use `const&` parameters by default.</span></span> <span data-ttu-id="fc4a2-160">Dadurch wird der Aufwand für Kopien vermieden (wozu Referenzzählung gehört, die zu miteinander verbundenen Erhöhungen und Verringerungen führt).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-160">That will avoid the overhead of copies (which involve reference counting, and that means interlocked increments and decrements).</span></span>

```cppwinrt
// Synchronous function.
void DoWork(Param const& value);
```

<span data-ttu-id="fc4a2-161">Sie können jedoch auf Probleme stoßen, wenn Sie einen Referenzparameter an eine Coroutine übergeben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-161">But you can run into problems if you pass a reference parameter to a coroutine.</span></span>

```cppwinrt
// NOT the recommended way to pass a value to a coroutine!
IASyncAction DoWorkAsync(Param const& value)
{
    // While it's ok to access value here...
    
    co_await DoOtherWorkAsync();

    // ...accessing value here carries no guarantees of safety.
}
```

<span data-ttu-id="fc4a2-162">In einer Coroutine verläuft die Ausführung bis zum ersten Anhaltepunkt synchron, wobei die Steuerung an den Aufrufer zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-162">In a coroutine, execution is synchronous up until the first suspension point, where control is returned to the caller.</span></span> <span data-ttu-id="fc4a2-163">Wenn die Coroutine fortgesetzt wird, kann alles Mögliche mit dem Quellwert passiert sein, auf den ein Referenzparameter verweist.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-163">By the time the coroutine resumes, anything might have happened to the source value that a reference parameter references.</span></span> <span data-ttu-id="fc4a2-164">Aus Sicht der Coroutine hat ein Referenzparameter eine unkontrollierte Lebensdauer.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-164">From the coroutine's perspective, a reference parameter has uncontrolled lifetime.</span></span> <span data-ttu-id="fc4a2-165">Im obigen Beispiel können wir also problemlos auf *value* bis `co_await` zugreifen, nicht jedoch danach.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-165">So, in the example above, we're safe to access *value* up until the `co_await`, but not after it.</span></span> <span data-ttu-id="fc4a2-166">Wir können *value* nicht problemlos an **DoOtherWorkAsync** übergeben, wenn das Risiko besteht, dass diese Funktion ihrerseits angehalten wird und bei Fortsetzen dann versucht, *value* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-166">Nor can we safely pass *value* to **DoOtherWorkAsync** if there's any risk that that function will in turn suspend and then try to use *value* after it resumes.</span></span> <span data-ttu-id="fc4a2-167">Damit die Parameter nach dem Anhalten und Fortsetzen ohne Probleme verwendet werden können, sollten Ihre Coroutinen standardmäßig „pass-by-value“ verwenden, um sicherzustellen, dass die Erfassung nach Wert erfolgt, und um Probleme mit der Lebensdauer zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-167">To make parameters safe to use after suspending and resuming, your coroutines should use pass-by-value by default to ensure that they capture by value and avoid lifetime issues.</span></span> <span data-ttu-id="fc4a2-168">Fälle, in denen Sie von dieser Vorgehensweise abweichen können, da Sie sicher sind, dass keine Probleme entstehen, sind eher selten.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-168">Cases when you can deviate from that guidance because you're certain that it's safe to do so are going to be rare.</span></span>

```cppwinrt
// Coroutine
IASyncAction DoWorkAsync(Param value);
```

<span data-ttu-id="fc4a2-169">Es ist auch fraglich, ob die Übergabe nach Konstantenwert empfehlenswert ist (es sei denn, Sie möchten den Wert verschieben).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-169">It's also arguable that (unless you want to move the value) passing by const value is good practice.</span></span> <span data-ttu-id="fc4a2-170">Dies hat keine Auswirkungen auf den Quellwert, von dem Sie eine Kopie erstellen, es macht aber die Intention klar und hilft, wenn Sie die Kopie versehentlich ändern.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-170">It won't have any effect on the source value from which you're making a copy, but it makes the intent clear, and helps if you inadvertently modify the copy.</span></span>
    
```cppwinrt
// coroutine with strictly unnecessary const (but arguably good practice).
IASyncAction DoWorkAsync(Param const value);
```

<span data-ttu-id="fc4a2-171">Weitere Informationen finden Sie unter [Standard-Arrays und -Vektoren](std-cpp-data-types.md#standard-arrays-and-vectors). Hier wird beschrieben, wie Sie einen Standardvektor in einem asynchronen Aufrufer übergeben.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-171">Also see [Standard arrays and vectors](std-cpp-data-types.md#standard-arrays-and-vectors), which deals with how to pass a standard vector into an asynchronous callee.</span></span>

## <a name="offloading-work-onto-the-windows-thread-pool"></a><span data-ttu-id="fc4a2-172">Auslagern von Aufgaben an den Windows-Threadpool</span><span class="sxs-lookup"><span data-stu-id="fc4a2-172">Offloading work onto the Windows thread pool</span></span>
<span data-ttu-id="fc4a2-173">Bevor Sie rechengebundene Arbeiten in einer Coroutine ausführen, müssen Sie die Ausführung an den Aufrufer zurückgegeben, damit der Aufrufer nicht blockiert wird (anders ausgedrückt, sollte ein Anhaltepunkt eingefügt werden).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-173">Before you do compute-bound work in a coroutine, you need to return execution to the caller so that the caller isn't blocked (in other words, introduce a suspension point).</span></span> <span data-ttu-id="fc4a2-174">Wenn Sie dies noch nicht durch ein `co-await` anderer Vorgänge tun, können Sie ein `co-await` für die Funktion **winrt::resume_background** ausführen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-174">If you're not already doing that by `co-await`-ing some other operation, then you can `co-await` the **winrt::resume_background** function.</span></span> <span data-ttu-id="fc4a2-175">Dadurch wird die Steuerung an den Aufrufer zurückgegeben, und unmittelbar danach wird die Ausführung auf einem Threadpoolthread fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-175">That returns control to the caller, and then immediately resumes execution on a thread pool thread.</span></span>

<span data-ttu-id="fc4a2-176">Der in der Implementierung verwendete Threadpool wird auf niedriger Ebene ausgeführt [Windows-Threadpool](https://msdn.microsoft.com/library/windows/desktop/ms686766), sodass er optimal effizient ist.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-176">The thread pool being used in the implementation is the low-level [Windows thread pool](https://msdn.microsoft.com/library/windows/desktop/ms686766), so it's optimially efficient.</span></span>

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

## <a name="programming-with-thread-affinity-in-mind"></a><span data-ttu-id="fc4a2-177">Programmieren mit Threadaffinität</span><span class="sxs-lookup"><span data-stu-id="fc4a2-177">Programming with thread affinity in mind</span></span>
<span data-ttu-id="fc4a2-178">Dieses Szenario erweitert das vorherige.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-178">This scenario expands on the previous one.</span></span> <span data-ttu-id="fc4a2-179">Sie lagern einige Aufgaben an den Threadpool aus, möchten dann aber den Fortschritt auf der Benutzeroberfläche anzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-179">You offload some work onto the thread pool, but then you want to display progress in the user interface (UI).</span></span>

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    textblock.Text(L"Done!"); // Error: TextBlock has thread affinity.
}
```

<span data-ttu-id="fc4a2-180">Der obige Code löst eine [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread)-Ausnahme aus, da ein **TextBlock** von dem Thread, der ihn erstellt hat (UI-Thread), aktualisiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-180">The code above throws a [**winrt::hresult_wrong_thread**](/uwp/cpp-ref-for-winrt/hresult-wrong-thread) exception, because a **TextBlock** must be updated from the thread that created it, which is the UI thread.</span></span> <span data-ttu-id="fc4a2-181">Eine Lösung besteht darin, den Threadkontext zu erfassen, in dem unsere Coroutine ursprünglich aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-181">One solution is to capture the thread context within which our coroutine was originally called.</span></span> <span data-ttu-id="fc4a2-182">Instanziieren Sie ein **winrt::apartment_context**-Objekt, und führen Sie dann ein `co_await` dafür aus.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-182">Instantiate a **winrt::apartment_context** object, and then `co_await` it.</span></span>

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

<span data-ttu-id="fc4a2-183">Solange die oben genannte Coroutine vom UI-Thread aufgerufen wird, der den **TextBlock** erstellt hat, funktioniert dieses Verfahren.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-183">As long as the coroutine above is called from the UI thread that created the **TextBlock**, then this technique works.</span></span> <span data-ttu-id="fc4a2-184">Es wird einige Fälle in Ihrer App geben, in denen Sie dessen sicher sind.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-184">There will be many cases in your app where you're certain of that.</span></span>

> [!NOTE]
> **<span data-ttu-id="fc4a2-185">Das folgende Codebeispiel bezieht sich auf die Vorabversion, die vor der kommerziellen Freigabe grundlegend geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-185">The following code example relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="fc4a2-186">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-186">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>**

<span data-ttu-id="fc4a2-187">Für eine allgemeinere Lösung zur Aktualisierung der Benutzeroberfläche, die auch Fälle abdeckt, in denen Sie bezüglich des aufrufenden Threads unsicher sind, können Sie das [Windows10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-187">For a more general solution to updating UI, which covers cases where you're uncertain about the calling thread, you can install the [Windows 10 SDK Preview Build 17661](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK), or later.</span></span> <span data-ttu-id="fc4a2-188">Sie können dann ein `co-await` für die Funktion **winrt::resume_foreground** ausführen, um zu einem bestimmten Vordergrundthread zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-188">Then, you can `co-await` the **winrt::resume_foreground** function to switch to a specific foreground thread.</span></span> <span data-ttu-id="fc4a2-189">Im folgenden Codebeispiel geben Sie den Vordergrundthread durch Übergabe des Dispatcherobjekts an, das mit dem **TextBlock** verknüpft ist (durch Zugriff auf die zugehörige [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher)-Eigenschaft).</span><span class="sxs-lookup"><span data-stu-id="fc4a2-189">In the code example below, we specify the foreground thread by passing the dispatcher object associated with the **TextBlock** (by accessing its [**Dispatcher**](/uwp/api/windows.ui.xaml.dependencyobject.dispatcher#Windows_UI_Xaml_DependencyObject_Dispatcher) property).</span></span> <span data-ttu-id="fc4a2-190">Die Implementierung von **winrt::resume_foreground** ruft [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) für dieses Dispatcherobjekt auf, um die Aufgaben auszuführen, die danach in der Coroutine folgen.</span><span class="sxs-lookup"><span data-stu-id="fc4a2-190">The implementation of **winrt::resume_foreground** calls [**CoreDispatcher.RunAsync**](/uwp/api/windows.ui.core.coredispatcher.runasync) on that dispatcher object to execute the work that comes after it in the coroutine.</span></span>

```cppwinrt
IAsyncAction DoWorkAsync(TextBlock textblock)
{
    co_await winrt::resume_background();
    // Do compute-bound work here.

    co_await winrt::resume_foreground(textblock.Dispatcher()); // Switch to the foreground thread associated with textblock.

    textblock.Text(L"Done!"); // Guaranteed to work.
}
```

## <a name="important-apis"></a><span data-ttu-id="fc4a2-191">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="fc4a2-191">Important APIs</span></span>
* [<span data-ttu-id="fc4a2-192">Concurrency:: Task-Klasse</span><span class="sxs-lookup"><span data-stu-id="fc4a2-192">concurrency::task class</span></span>](/cpp/parallel/concrt/reference/task-class)
* [<span data-ttu-id="fc4a2-193">IAsyncAction-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fc4a2-193">IAsyncAction interface</span></span>](/uwp/api/windows.foundation.iasyncaction)
* [<span data-ttu-id="fc4a2-194">IAsyncActionWithProgress&lt;TProgress&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fc4a2-194">IAsyncActionWithProgress&lt;TProgress&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncactionwithprogress_tprogress_)
* [<span data-ttu-id="fc4a2-195">IAsyncOperation&lt;TResult&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fc4a2-195">IAsyncOperation&lt;TResult&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncoperation_tresult_)
* [<span data-ttu-id="fc4a2-196">IAsyncOperationWithProgress&lt;TResult, TProgress&gt; Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="fc4a2-196">IAsyncOperationWithProgress&lt;TResult, TProgress&gt; interface</span></span>](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)
* [<span data-ttu-id="fc4a2-197">Syndicationclient:: Retrievefeedasync-Methode</span><span class="sxs-lookup"><span data-stu-id="fc4a2-197">SyndicationClient::RetrieveFeedAsync method</span></span>](/uwp/api/windows.web.syndication.syndicationclient.retrievefeedasync)
* [<span data-ttu-id="fc4a2-198">SyndicationFeed-Klasse</span><span class="sxs-lookup"><span data-stu-id="fc4a2-198">SyndicationFeed class</span></span>](/uwp/api/windows.web.syndication.syndicationfeed)

## <a name="related-topics"></a><span data-ttu-id="fc4a2-199">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fc4a2-199">Related topics</span></span>
* [<span data-ttu-id="fc4a2-200">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="fc4a2-200">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
* [<span data-ttu-id="fc4a2-201">Standard C++ Datentypen und C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="fc4a2-201">Standard C++ data types and C++/WinRT</span></span>](std-cpp-data-types.md)