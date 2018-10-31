---
author: normesta
ms.assetid: 1B077801-0A58-4A34-887C-F1E85E9A37B0
title: Erstellen einer regelmäßigen Arbeitsaufgabe
description: Hier erfahren Sie, wie Sie eine Arbeitsaufgabe erstellen, die regelmäßig wiederholt wird.
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, regelmäßige Arbeitsaufgabe, Threading, Timer
ms.localizationpriority: medium
ms.openlocfilehash: 4afa137b01738c42f8e15c95ef09ec921d1e44ae
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5838516"
---
# <a name="create-a-periodic-work-item"></a><span data-ttu-id="4cab2-104">Erstellen einer regelmäßigen Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="4cab2-104">Create a periodic work item</span></span>


<span data-ttu-id="4cab2-105">\*\* Wichtige APIs \*\*</span><span class="sxs-lookup"><span data-stu-id="4cab2-105">\*\* Important APIs \*\*</span></span>

-   [**<span data-ttu-id="4cab2-106">CreatePeriodicTimer</span><span class="sxs-lookup"><span data-stu-id="4cab2-106">CreatePeriodicTimer</span></span>**](https://msdn.microsoft.com/library/windows/apps/Hh967915)
-   [**<span data-ttu-id="4cab2-107">ThreadPoolTimer</span><span class="sxs-lookup"><span data-stu-id="4cab2-107">ThreadPoolTimer</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR230587)

<span data-ttu-id="4cab2-108">Hier erfahren Sie, wie Sie eine Arbeitsaufgabe erstellen, die regelmäßig wiederholt wird.</span><span class="sxs-lookup"><span data-stu-id="4cab2-108">Learn how to create a work item that repeats periodically.</span></span>

## <a name="create-the-periodic-work-item"></a><span data-ttu-id="4cab2-109">Erstellen der regelmäßigen Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="4cab2-109">Create the periodic work item</span></span>

<span data-ttu-id="4cab2-110">Verwenden Sie die [**CreatePeriodicTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967915)-Methode, um eine regelmäßige Arbeitsaufgabe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4cab2-110">Use the [**CreatePeriodicTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967915) method to create a periodic work item.</span></span> <span data-ttu-id="4cab2-111">Stellen Sie eine Lambda-Funktion zum Ausführen der Arbeit bereit, und geben Sie mit dem *period*-Parameter das Intervall zwischen den Übermittlungen an.</span><span class="sxs-lookup"><span data-stu-id="4cab2-111">Supply a lambda that accomplishes the work, and use the *period* parameter to specify the interval between submissions.</span></span> <span data-ttu-id="4cab2-112">Das Intervall wird anhand einer [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/BR225996)-Struktur angegeben.</span><span class="sxs-lookup"><span data-stu-id="4cab2-112">The period is specified using a [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/BR225996) structure.</span></span> <span data-ttu-id="4cab2-113">Nach jedem Verstreichen des Intervalls wird die Arbeitsaufgabe erneut gesendet. Stellen Sie daher sicher, dass es lang genug ist, um die Arbeit auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4cab2-113">The work item will be resubmitted every time the period elapses, so make sure the period is long enough for work to complete.</span></span>

<span data-ttu-id="4cab2-114">[**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.createtimer.aspx) gibt ein [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/BR230587)-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="4cab2-114">[**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.createtimer.aspx) returns a [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/BR230587) object.</span></span> <span data-ttu-id="4cab2-115">Speichern Sie das Objekt für den Fall, dass der Timer abgebrochen werden muss.</span><span class="sxs-lookup"><span data-stu-id="4cab2-115">Store this object in case the timer needs to be canceled.</span></span>

> <span data-ttu-id="4cab2-116">**Hinweis:** vermeiden Sie den Wert 0 (null) angeben (oder ein Wert kleiner als eine Millisekunde) für das Intervall.</span><span class="sxs-lookup"><span data-stu-id="4cab2-116">**Note**Avoid specifying a value of zero (or any value less than one millisecond) for the interval.</span></span> <span data-ttu-id="4cab2-117">Andernfalls verhält sich der regelmäßige Timer wie ein einmaliger Timer.</span><span class="sxs-lookup"><span data-stu-id="4cab2-117">This causes the periodic timer to behave as a single-shot timer instead.</span></span>

> <span data-ttu-id="4cab2-118">**Hinweis:** können Sie [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) verwenden, um auf die Benutzeroberfläche zuzugreifen und den Fortschritt der Arbeitsaufgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4cab2-118">**Note**You can use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to access the UI and show progress from the work item.</span></span>

<span data-ttu-id="4cab2-119">Das folgende Beispiel erstellt eine Arbeitsaufgabe, die alle 60Sekunden ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="4cab2-119">The following example creates a work item that runs once every 60 seconds:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> TimeSpan period = TimeSpan.FromSeconds(60);
>
> ThreadPoolTimer PeriodicTimer = ThreadPoolTimer.CreatePeriodicTimer((source) =>
>     {
>         //
>         // TODO: Work
>         //
>         
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher.RunAsync(CoreDispatcherPriority.High,
>             () =>
>             {
>                 //
>                 // UI components can be accessed within this scope.
>                 //
>
>             });
>
>     }, period);
> ```
> ``` cpp
> TimeSpan period;
> period.Duration = 60 * 10000000; // 10,000,000 ticks per second
>
> ThreadPoolTimer ^ PeriodicTimer = ThreadPoolTimer::CreatePeriodicTimer(
>         ref new TimerElapsedHandler([this](ThreadPoolTimer^ source)
>         {
>             //
>             // TODO: Work
>             //
>             
>             //
>             // Update the UI thread by using the UI core dispatcher.
>             //
>             Dispatcher->RunAsync(CoreDispatcherPriority::High,
>                 ref new DispatchedHandler([this]()
>                 {
>                     //
>                     // UI components can be accessed within this scope.
>                     //
>                         
>                 }));
>
>         }), period);
> ```

## <a name="handle-cancellation-of-the-periodic-work-item-optional"></a><span data-ttu-id="4cab2-120">Behandeln des Abbruchs der regelmäßigen Arbeitsaufgabe (optional)</span><span class="sxs-lookup"><span data-stu-id="4cab2-120">Handle cancellation of the periodic work item (optional)</span></span>

<span data-ttu-id="4cab2-121">Bei Bedarf können Sie den Abbruch des regelmäßigen Timers mit einem [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926)-Element verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="4cab2-121">If needed, you can handle cancellation of the periodic timer with a [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926).</span></span> <span data-ttu-id="4cab2-122">Stellen Sie mithilfe der [**CreatePeriodicTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967915)-Überladung eine zusätzliche Lambda-Funktion bereit, die den Abbruch der regelmäßigen Arbeitsaufgabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="4cab2-122">Use the [**CreatePeriodicTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967915) overload to supply an additional lambda that handles cancellation of the periodic work item.</span></span>

<span data-ttu-id="4cab2-123">Das folgende Beispiel erstellt eine regelmäßige Arbeitsaufgabe, die alle 60Sekunden wiederholt wird, und stellt außerdem einen Abbruchhandler bereit:</span><span class="sxs-lookup"><span data-stu-id="4cab2-123">The following example creates a periodic work item that repeats every 60 seconds and it also supplies a cancellation handler:</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> using Windows.System.Threading;
>
>     TimeSpan period = TimeSpan.FromSeconds(60);
>
>     ThreadPoolTimer PeriodicTimer = ThreadPoolTimer.CreatePeriodicTimer((source) =>
>     {
>         //
>         // TODO: Work
>         //
>         
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher.RunAsync(CoreDispatcherPriority.High,
>             () =>
>             {
>                 //
>                 // UI components can be accessed within this scope.
>                 //
>
>             });
>     },
>     period,
>     (source) =>
>     {
>         //
>         // TODO: Handle periodic timer cancellation.
>         //
>
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher->RunAsync(CoreDispatcherPriority.High,
>             ()=>
>             {
>                 //
>                 // UI components can be accessed within this scope.
>                 //                 
>
>                 // Periodic timer cancelled.
>
>             }));
>     });
> ```
> ``` cpp
> using namespace Windows::System::Threading;
> using namespace Windows::UI::Core;
>
> TimeSpan period;
> period.Duration = 60 * 10000000; // 10,000,000 ticks per second
>
> ThreadPoolTimer ^ PeriodicTimer = ThreadPoolTimer::CreatePeriodicTimer(
>         ref new TimerElapsedHandler([this](ThreadPoolTimer^ source)
>         {
>             //
>             // TODO: Work
>             //
>                 
>             //
>             // Update the UI thread by using the UI core dispatcher.
>             //
>             Dispatcher->RunAsync(CoreDispatcherPriority::High,
>                 ref new DispatchedHandler([this]()
>                 {
>                     //
>                     // UI components can be accessed within this scope.
>                     //
>
>                 }));
>
>         }),
>         period,
>         ref new TimerDestroyedHandler([&](ThreadPoolTimer ^ source)
>         {
>             //
>             // TODO: Handle periodic timer cancellation.
>             //
>
>             Dispatcher->RunAsync(CoreDispatcherPriority::High,
>                 ref new DispatchedHandler([&]()
>                 {
>                     //
>                     // UI components can be accessed within this scope.
>                     //
>
>                     // Periodic timer cancelled.
>
>                 }));
>         }));
> ```

## <a name="cancel-the-timer"></a><span data-ttu-id="4cab2-124">Abbrechen des Timers</span><span class="sxs-lookup"><span data-stu-id="4cab2-124">Cancel the timer</span></span>

<span data-ttu-id="4cab2-125">Rufen Sie ggf. die [**Cancel**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.cancel.aspx)-Methode auf, um die Wiederholung der regelmäßigen Arbeitsaufgabe zu beenden.</span><span class="sxs-lookup"><span data-stu-id="4cab2-125">When necessary, call the [**Cancel**](https://msdn.microsoft.com/library/windows/apps/windows.system.threading.threadpooltimer.cancel.aspx) method to stop the periodic work item from repeating.</span></span> <span data-ttu-id="4cab2-126">Falls die Arbeitsaufgabe beim Abbruch des regelmäßigen Timers ausgeführt wird, kann sie noch abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="4cab2-126">If the work item is running when the periodic timer is cancelled it is allowed to complete.</span></span> <span data-ttu-id="4cab2-127">Das [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926)-Element (sofern verwendet) wird aufgerufen, wenn alle Instanzen der regelmäßigen Arbeitsaufgabe abgeschlossen wurden.</span><span class="sxs-lookup"><span data-stu-id="4cab2-127">The [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926) (if provided) is called when all instances of the periodic work item have completed.</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> PeriodicTimer.Cancel();
> ```
> ``` cpp
> PeriodicTimer->Cancel();
> ```

## <a name="remarks"></a><span data-ttu-id="4cab2-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4cab2-128">Remarks</span></span>

<span data-ttu-id="4cab2-129">Informationen zu einmaligen Timern finden Sie unter [Senden einer Arbeitsaufgabe mithilfe eines Timers](use-a-timer-to-submit-a-work-item.md).</span><span class="sxs-lookup"><span data-stu-id="4cab2-129">For information about single-use timers, see [Use a timer to submit a work item](use-a-timer-to-submit-a-work-item.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="4cab2-130">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="4cab2-130">Related topics</span></span>

* [<span data-ttu-id="4cab2-131">Senden einer Arbeitsaufgabe an den Threadpool</span><span class="sxs-lookup"><span data-stu-id="4cab2-131">Submit a work item to the thread pool</span></span>](submit-a-work-item-to-the-thread-pool.md)
* [<span data-ttu-id="4cab2-132">Bewährte Methoden zum Verwenden des Threadpools</span><span class="sxs-lookup"><span data-stu-id="4cab2-132">Best practices for using the thread pool</span></span>](best-practices-for-using-the-thread-pool.md)
* [<span data-ttu-id="4cab2-133">Senden einer Arbeitsaufgabe mithilfe eines Timers</span><span class="sxs-lookup"><span data-stu-id="4cab2-133">Use a timer to submit a work item</span></span>](use-a-timer-to-submit-a-work-item.md)
 
