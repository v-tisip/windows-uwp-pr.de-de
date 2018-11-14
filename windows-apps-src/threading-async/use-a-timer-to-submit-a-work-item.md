---
author: normesta
ms.assetid: AAE467F9-B3C7-4366-99A2-8A880E5692BE
title: Senden einer Arbeitsaufgabe mithilfe eines Timers
description: Hier erfahren Sie, wie Sie eine Arbeitsaufgabe erstellen, die nach dem Ablaufen eines Timers ausgeführt wird.
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Timer, Threads
ms.localizationpriority: medium
ms.openlocfilehash: d65faebfc2be0e9ed254185d00932da9a57f718b
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6455300"
---
# <a name="use-a-timer-to-submit-a-work-item"></a><span data-ttu-id="69356-104">Timergesteuertes Übermitteln einer Arbeitsaufgabe</span><span class="sxs-lookup"><span data-stu-id="69356-104">Use a timer to submit a work item</span></span>


<span data-ttu-id="69356-105">\*\* Wichtige APIs \*\*</span><span class="sxs-lookup"><span data-stu-id="69356-105">\*\* Important APIs \*\*</span></span>

-   [**<span data-ttu-id="69356-106">Windows.UI.Core-Namespace</span><span class="sxs-lookup"><span data-stu-id="69356-106">Windows.UI.Core namespace</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR208383)
-   [**<span data-ttu-id="69356-107">Windows.System.Threading-Namespace</span><span class="sxs-lookup"><span data-stu-id="69356-107">Windows.System.Threading namespace</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR229642)

<span data-ttu-id="69356-108">Hier erfahren Sie, wie Sie eine Arbeitsaufgabe erstellen, die nach dem Ablaufen eines Timers ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="69356-108">Learn how to create a work item that runs after a timer elapses.</span></span>

## <a name="create-a-single-shot-timer"></a><span data-ttu-id="69356-109">Erstellen eines einmaligen Timers</span><span class="sxs-lookup"><span data-stu-id="69356-109">Create a single-shot timer</span></span>

<span data-ttu-id="69356-110">Verwenden Sie die [**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921)-Methode, um einen Timer für die Arbeitsaufgabe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="69356-110">Use the [**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921) method to create a timer for the work item.</span></span> <span data-ttu-id="69356-111">Stellen Sie eine Lambda-Funktion zum Ausführen der Arbeit bereit, und geben Sie mit dem *delay*-Parameter an, wie lange der Threadpool warten soll, bevor er die Arbeitsaufgabe einem verfügbaren Thread zuweist.</span><span class="sxs-lookup"><span data-stu-id="69356-111">Supply a lambda that accomplishes the work, and use the *delay* parameter to specify how long the thread pool waits before it can assign the work item to an available thread.</span></span> <span data-ttu-id="69356-112">Die Verzögerung wird mithilfe einer [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/BR225996)-Struktur angegeben.</span><span class="sxs-lookup"><span data-stu-id="69356-112">The delay is specified using a [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/BR225996) structure.</span></span>

> <span data-ttu-id="69356-113">**Hinweis:** können Sie [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) verwenden, um auf die Benutzeroberfläche zuzugreifen und den Fortschritt der Arbeitsaufgabe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="69356-113">**Note**You can use [**CoreDispatcher.RunAsync**](https://msdn.microsoft.com/library/windows/apps/Hh750317) to access the UI and show progress from the work item.</span></span>

<span data-ttu-id="69356-114">Im folgenden Beispiel wird eine Arbeitsaufgabe erstellt, die in drei Minuten ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="69356-114">The following example creates a work item that runs in three minutes:</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> TimeSpan delay = TimeSpan.FromMinutes(3);
>             
> ThreadPoolTimer DelayTimer = ThreadPoolTimer.CreateTimer(
>     (source) =>
>     {
>         //
>         // TODO: Work
>         //
>         
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher.RunAsync(
>             CoreDispatcherPriority.High,
>             () =>
>             {
>                 //
>                 // UI components can be accessed within this scope.
>                 //
>
>             });
>
>     }, delay);
> ```
> ``` cpp
> TimeSpan delay;
> delay.Duration = 3 * 60 * 10000000; // 10,000,000 ticks per second
>
> ThreadPoolTimer ^ DelayTimer = ThreadPoolTimer::CreateTimer(
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
>                     ExampleUIUpdateMethod("Timer completed.");
>
>                 }));
>
>         }), delay);
> ```

## <a name="provide-a-completion-handler"></a><span data-ttu-id="69356-115">Bereitstellen eines Abschlusshandlers</span><span class="sxs-lookup"><span data-stu-id="69356-115">Provide a completion handler</span></span>

<span data-ttu-id="69356-116">Behandeln Sie den Abbruch und Abschluss der Arbeitsaufgabe ggf. mit einem [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926)-Element.</span><span class="sxs-lookup"><span data-stu-id="69356-116">If needed, handle cancellation and completion of the work item with a [**TimerDestroyedHandler**](https://msdn.microsoft.com/library/windows/apps/Hh967926).</span></span> <span data-ttu-id="69356-117">Stellen Sie mithilfe der [**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921)-Überladung eine zusätzliche Lambda-Funktion bereit.</span><span class="sxs-lookup"><span data-stu-id="69356-117">Use the [**CreateTimer**](https://msdn.microsoft.com/library/windows/apps/Hh967921) overload to supply an additional lambda.</span></span> <span data-ttu-id="69356-118">Diese Funktion wird ausgeführt, wenn der Timer abgebrochen oder die Arbeitsaufgabe abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="69356-118">This runs when the timer is cancelled or when the work item completes.</span></span>

<span data-ttu-id="69356-119">Das folgende Beispiel erstellt einen Zeitgeber, der die Arbeitsaufgabe sendet, und ruft eine Methode auf, wenn die Arbeitsaufgabe abgeschlossen oder der Zeitgeber abgebrochen wird:</span><span class="sxs-lookup"><span data-stu-id="69356-119">The following example creates a timer that submits the work item, and calls a method when the work item finishes or the timer is cancelled:</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> TimeSpan delay = TimeSpan.FromMinutes(3);
>             
> bool completed = false;
>
> ThreadPoolTimer DelayTimer = ThreadPoolTimer.CreateTimer(
>     (source) =>
>     {
>         //
>         // TODO: Work
>         //
>
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher.RunAsync(
>                 CoreDispatcherPriority.High,
>                 () =>
>                 {
>                     //
>                     // UI components can be accessed within this scope.
>                     //
>
>                 });
>
>         completed = true;
>     },
>     delay,
>     (source) =>
>     {
>         //
>         // TODO: Handle work cancellation/completion.
>         //
>
>
>         //
>         // Update the UI thread by using the UI core dispatcher.
>         //
>         Dispatcher.RunAsync(
>             CoreDispatcherPriority.High,
>             () =>
>             {
>                 //
>                 // UI components can be accessed within this scope.
>                 //
>
>                 if (completed)
>                 {
>                     // Timer completed.
>                 }
>                 else
>                 {
>                     // Timer cancelled.
>                 }
>
>             });
>     });
> ```
> ``` cpp
> TimeSpan delay;
> delay.Duration = 3 * 60 * 10000000; // 10,000,000 ticks per second
>
> completed = false;
>
> ThreadPoolTimer ^ DelayTimer = ThreadPoolTimer::CreateTimer(
>         ref new TimerElapsedHandler([&](ThreadPoolTimer ^ source)
>         {
>             //
>             // TODO: Work
>             //
>
>             //
>             // Update the UI thread by using the UI core dispatcher.
>             //
>             Dispatcher->RunAsync(CoreDispatcherPriority::High,
>                 ref new DispatchedHandler([&]()
>                 {
>                     //
>                     // UI components can be accessed within this scope.
>                     //
>
>                 }));
>
>             completed = true;
>
>         }),
>         delay,
>         ref new TimerDestroyedHandler([&](ThreadPoolTimer ^ source)
>         {
>             //
>             // TODO: Handle work cancellation/completion.
>             //
>
>             Dispatcher->RunAsync(CoreDispatcherPriority::High,
>                 ref new DispatchedHandler([&]()
>                 {
>                     //
>                     // Update the UI thread by using the UI core dispatcher.
>                     //
>
>                     if (completed)
>                     {
>                         // Timer completed.
>                     }
>                     else
>                     {
>                         // Timer cancelled.
>                     }
>
>                 }));
>         }));
> ```

## <a name="cancel-the-timer"></a><span data-ttu-id="69356-120">Abbrechen des Zeitgebers</span><span class="sxs-lookup"><span data-stu-id="69356-120">Cancel the timer</span></span>

<span data-ttu-id="69356-121">Wenn der Timer weiter läuft, die Arbeitsaufgabe aber nicht mehr benötigt wird, rufen Sie [**Cancel**](https://msdn.microsoft.com/library/windows/apps/BR230588) auf.</span><span class="sxs-lookup"><span data-stu-id="69356-121">If the timer is still counting down, but the work item is no longer needed, call [**Cancel**](https://msdn.microsoft.com/library/windows/apps/BR230588).</span></span> <span data-ttu-id="69356-122">Der Timer wird abgebrochen, und die Arbeitsaufgabe wird nicht an den Threadpool übermittelt.</span><span class="sxs-lookup"><span data-stu-id="69356-122">The timer is cancelled and the work item won't be submitted to the thread pool.</span></span>

> [!div class="tabbedCodeSnippets"]
> ``` csharp
> DelayTimer.Cancel();
> ```
> ``` cpp
> DelayTimer->Cancel();
> ```

## <a name="remarks"></a><span data-ttu-id="69356-123">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="69356-123">Remarks</span></span>

<span data-ttu-id="69356-124">UWP (Universelle Windows-Plattform)-Apps können **Thread.Sleep** nicht verwenden, da dies den UI-Thread blockieren kann.</span><span class="sxs-lookup"><span data-stu-id="69356-124">Universal Windows Platform (UWP) apps can't use **Thread.Sleep** because it can block the UI thread.</span></span> <span data-ttu-id="69356-125">Verwenden Sie zum Erstellen einer Arbeitsaufgabe stattdessen einen [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/BR230587). Dieser Timer verzögert die von der Arbeitsaufgabe ausgeführte Aufgabe, ohne den UI-Thread zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="69356-125">You can use a [**ThreadPoolTimer**](https://msdn.microsoft.com/library/windows/apps/BR230587) to create a work item instead, and this will delay the task accomplished by the work item without blocking the UI thread.</span></span>

<span data-ttu-id="69356-126">Ein vollständiges Codebeispiel für Arbeitsaufgaben, Arbeitsaufgaben mit Zeitgeber und regelmäßige Arbeitsaufgaben finden Sie im [Beispiel für den Threadpool](http://go.microsoft.com/fwlink/p/?linkid=255387).</span><span class="sxs-lookup"><span data-stu-id="69356-126">See the [thread pool sample](http://go.microsoft.com/fwlink/p/?linkid=255387) for a complete code sample that demonstrates work items, timer work items, and periodic work items.</span></span> <span data-ttu-id="69356-127">Das Codebeispiel wurde ursprünglich für Windows8.1 geschrieben, aber der Code kann Windows 10 wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="69356-127">The code sample was originally written for Windows8.1 but the code can be re-used in Windows10.</span></span>

<span data-ttu-id="69356-128">Informationen zu Wiederholungstimern finden Sie unter [Erstellen einer regelmäßigen Arbeitsaufgabe](create-a-periodic-work-item.md).</span><span class="sxs-lookup"><span data-stu-id="69356-128">For information about repeating timers, see [Create a periodic work item](create-a-periodic-work-item.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="69356-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="69356-129">Related topics</span></span>

* [<span data-ttu-id="69356-130">Senden einer Arbeitsaufgabe an den Threadpool</span><span class="sxs-lookup"><span data-stu-id="69356-130">Submit a work item to the thread pool</span></span>](submit-a-work-item-to-the-thread-pool.md)
* [<span data-ttu-id="69356-131">Bewährte Methoden zum Verwenden des Threadpools</span><span class="sxs-lookup"><span data-stu-id="69356-131">Best practices for using the thread pool</span></span>](best-practices-for-using-the-thread-pool.md)
* [<span data-ttu-id="69356-132">Senden einer Arbeitsaufgabe mithilfe eines Timers</span><span class="sxs-lookup"><span data-stu-id="69356-132">Use a timer to submit a work item</span></span>](use-a-timer-to-submit-a-work-item.md)
 

 
