---
author: TylerMSFT
title: Behandeln einer abgebrochenen Hintergrundaufgabe
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die Abbruchanforderungen erkennt, die Ausführung beendet und den Abbruch mithilfe des beständigen Speichers an die App meldet.
ms.assetid: B7E23072-F7B0-4567-985B-737DD2A8728E
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 767280b3f3a073a55a4f489fd99229e42dd8140f
ms.sourcegitcommit: 54c2cd58fde08af889093a0c85e7297e33e6a0eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
ms.locfileid: "1664843"
---
# <a name="handle-a-cancelled-background-task"></a><span data-ttu-id="7a7e4-104">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-104">Handle a cancelled background task</span></span>


**<span data-ttu-id="7a7e4-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="7a7e4-105">Important APIs</span></span>**

-   [**<span data-ttu-id="7a7e4-106">BackgroundTaskCanceledEventHandler</span><span class="sxs-lookup"><span data-stu-id="7a7e4-106">BackgroundTaskCanceledEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224775)
-   [**<span data-ttu-id="7a7e4-107">IBackgroundTaskInstance</span><span class="sxs-lookup"><span data-stu-id="7a7e4-107">IBackgroundTaskInstance</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224797)
-   [**<span data-ttu-id="7a7e4-108">ApplicationData.Current</span><span class="sxs-lookup"><span data-stu-id="7a7e4-108">ApplicationData.Current</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241619)

<span data-ttu-id="7a7e4-109">Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die mithilfe des beständigen Speichers Abbruchanforderungen erkennt, die Ausführung beendet und den Abbruch an die App meldet.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-109">Learn how to make a background task that recognizes a cancellation request, stops work, and reports the cancellation to the app using persistent storage.</span></span>

<span data-ttu-id="7a7e4-110">Dieses Thema setzt voraus, dass Sie bereits eine Hintergrundaufgabenklasse erstellt haben, einschließlich der Run-Methode, die für die Hintergrundaufgabe als Einstiegspunkt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-110">This topic assumes you have already created a background task class, including the Run method that is used as the background task entry point.</span></span> <span data-ttu-id="7a7e4-111">Um schnell mit dem Erstellen einer Hintergrundaufgabe zu beginnen, lesen Sie [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="7a7e4-111">To get started quickly building a background task, see [Create and register an out-of-process background task](create-and-register-a-background-task.md) or [Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span> <span data-ttu-id="7a7e4-112">Ausführlichere Informationen zu Bedingungen und Triggern finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="7a7e4-112">For more in-depth information on conditions and triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

<span data-ttu-id="7a7e4-113">Dieses Thema gilt auch für Hintergrundaufgaben innerhalb von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-113">This topic is also applicable to in-process background tasks.</span></span> <span data-ttu-id="7a7e4-114">Ersetzen Sie die **Run()**-Methode jedoch durch **OnBackgroundActivated()**.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-114">But instead of the **Run()** method, substitute **OnBackgroundActivated()**.</span></span> <span data-ttu-id="7a7e4-115">Hintergrundaufgaben innerhalb von Prozessen benötigen keinen beständigen Speicher, um den Abbruch zu signalisieren, da dieser mithilfe des App-Status übermittelt werden kann, wenn die Hintergrundaufgabe im selben Prozess ausgeführt wird, wie die Vordergrund-App.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-115">In-process background tasks do not require you to use persistent storage to signal the cancellation because you can communicate the cancellation using app state since the background task is running in the same process as your foreground app.</span></span>

## <a name="use-the-oncanceled-method-to-recognize-cancellation-requests"></a><span data-ttu-id="7a7e4-116">Verwenden der Methode „OnCanceled“ zum Erkennen von Abbruchanforderungen</span><span class="sxs-lookup"><span data-stu-id="7a7e4-116">Use the OnCanceled method to recognize cancellation requests</span></span>

<span data-ttu-id="7a7e4-117">Schreiben Sie eine Methode für die Behandlung des Abbruchereignisses.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-117">Write a method to handle the cancellation event.</span></span>

> <span data-ttu-id="7a7e4-118">**Hinweis:**  Mit Ausnahme von Desktopgeräten können Hintergrundaufgaben bei allen Gerätefamilien beendet werden, wenn der Arbeitsspeicher des Geräts knapp wird.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-118">**Note**  For all device families except desktop, if the device becomes low on memory, background tasks may be terminated.</span></span> <span data-ttu-id="7a7e4-119">Wenn eine Ausnahme über wenig Arbeitsspeicher nicht angezeigt oder von der App nicht behandelt wird, wird die Hintergrundaufgabe ohne Warnung und ohne Auslösen des OnCanceled-Ereignisses beendet.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-119">If an out of memory exception is not surfaced, or the app does not handle it, then the background task will be terminated without warning and without raising the OnCanceled event.</span></span> <span data-ttu-id="7a7e4-120">Dadurch soll die Benutzerfreundlichkeit der App im Vordergrund sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-120">This helps to ensure the user experience of the app in the foreground.</span></span> <span data-ttu-id="7a7e4-121">Entwerfen Sie die Hintergrundaufgabe so, dass dieses Szenario behandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-121">Your background task should be designed to handle this scenario.</span></span>

<span data-ttu-id="7a7e4-122">Eine **OnCanceled**-Methode erstellen Sie wie folgt.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-122">Create a method named **OnCanceled** as follows.</span></span> <span data-ttu-id="7a7e4-123">Diese Methode ist der Einstiegspunkt, der von der Windows-Runtime aufgerufen wird, wenn eine Abbruchanforderung für die Hintergrundaufgabe erfolgt.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-123">This method is the entry point called by the Windows Runtime when a cancellation request is made against your background task.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>    private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
>    {
>        // TODO: Add code to notify the background task that it is cancelled.
>    }
> ```
> ```cpp
>    void ExampleBackgroundTask::OnCanceled(IBackgroundTaskInstance^ taskInstance, BackgroundTaskCancellationReason reason)
>    {
>        // TODO: Add code to notify the background task that it is cancelled.
>    }
> ```

<span data-ttu-id="7a7e4-124">Fügen Sie der Hintergrundaufgabenklasse eine Kennzeichenvariable mit dem Namen **\_CancelRequested** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-124">Add a flag variable called **\_CancelRequested** to the background task class.</span></span> <span data-ttu-id="7a7e4-125">Diese Variable wird verwendet, um anzuzeigen, ob eine Abbruchanforderung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-125">This variable will be used to indicate when a cancellation request has been made.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>   volatile bool _CancelRequested = false;
> ```
> ```cpp
>   private:
>     volatile bool CancelRequested;
> ```

<span data-ttu-id="7a7e4-126">Legen Sie in der OnCanceled-Methode, die Sie in Schritt1 erstellt haben, die Kennzeichenvariable **\_CancelRequested** auf **true** fest.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-126">In the OnCanceled method you created in step 1, set the flag variable **\_CancelRequested** to **true**.</span></span>

<span data-ttu-id="7a7e4-127">Die vollständige OnCanceled-Methode des [Beispiels zur Hintergrundaufgabe]( http://go.microsoft.com/fwlink/p/?linkid=227509) legt **\_CancelRequested** auf **true** fest und gibt eine möglicherweise hilfreiche Debugmeldung aus:</span><span class="sxs-lookup"><span data-stu-id="7a7e4-127">The full [background task sample]( http://go.microsoft.com/fwlink/p/?linkid=227509) OnCanceled method sets **\_CancelRequested** to **true** and writes potentially useful debug output:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>     private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
>     {
>         //
>         // Indicate that the background task is canceled.
>         //
>
>         _cancelRequested = true;
>
>         Debug.WriteLine("Background " + sender.Task.Name + " Cancel Requested...");
>     }
> ```
> ```cpp
>     void SampleBackgroundTask::OnCanceled(IBackgroundTaskInstance^ taskInstance, BackgroundTaskCancellationReason reason)
>     {
>         //
>         // Indicate that the background task is canceled.
>         //
>
>         CancelRequested = true;
>     }
> ```

<span data-ttu-id="7a7e4-128">Registrieren Sie in der Run-Methode der Hintergrundaufgabe die **OnCanceled**-Ereignishandlermethode, bevor Sie mit der Arbeit beginnen.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-128">In the background task's Run method, register the **OnCanceled** event handler method before starting work.</span></span> <span data-ttu-id="7a7e4-129">Für eine Hintergrundaufgabe innerhalb von Prozessen empfiehlt sich diese Registrierung im Rahmen der Anwendungsinitialisierung.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-129">In an in-process background task, you might do this registration as part of your application initialization.</span></span> <span data-ttu-id="7a7e4-130">Verwenden Sie z.B. folgende Codezeile:</span><span class="sxs-lookup"><span data-stu-id="7a7e4-130">For example, use the following line of code:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>     taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);
> ```
> ```cpp
>     taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &SampleBackgroundTask::OnCanceled);
> ```

## <a name="handle-cancellation-by-exiting-your-background-task"></a><span data-ttu-id="7a7e4-131">Behandeln des Abbruchs durch Beenden der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-131">Handle cancellation by exiting your background task</span></span>

<span data-ttu-id="7a7e4-132">Wenn eine Abbruchanforderung empfangen wird, muss die Methode für die Hintergrundverarbeitung angehalten und beendet werden, indem erkannt wird, dass **\_cancelRequested** auf **true** festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-132">When a cancellation request is received, your method that does background work needs to stop work and exit by recognizing when **\_cancelRequested** is set to **true**.</span></span> <span data-ttu-id="7a7e4-133">Für Hintergrundaufgaben innerhalb von Prozessen bedeutet dies ein Zurückwechseln aus der **OnBackgroundActivated()**-Methode.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-133">For in-process background tasks, this means returning from the **OnBackgroundActivated()** method.</span></span> <span data-ttu-id="7a7e4-134">Bei Hintergrundaufgaben außerhalb von Prozessen bedeutet dies ein Zurückwechseln aus der **Run()**-Methode.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-134">For out-of-process background tasks, this means returning from the **Run()** method.</span></span>

<span data-ttu-id="7a7e4-135">Ändern Sie den Code der Hintergrundaufgabenklasse, um die Kennzeichenvariable zu überprüfen, während die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-135">Modify the code of your background task class to check the flag variable while it's working.</span></span> <span data-ttu-id="7a7e4-136">Wenn **\_cancelRequested** auf „true“ festgelegt ist, halten Sie die Fortsetzung der Arbeit an.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-136">If **\_cancelRequested** set to true, stop work from continuing.</span></span>

<span data-ttu-id="7a7e4-137">Das [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) enthält eine Überprüfung, die den regelmäßigen Zeitgeberrückruf anhält, wenn die Hintergrundaufgabe abgebrochen wird:</span><span class="sxs-lookup"><span data-stu-id="7a7e4-137">The [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) includes a check that stops the periodic timer callback if the background task is canceled:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         // TODO: Record whether the task completed or was cancelled.
>     }
> ```
> ```cpp
>     if ((CancelRequested == false) && (Progress < 100))
>     {
>         Progress += 10;
>         TaskInstance->Progress = Progress;
>     }
>     else
>     {
>         PeriodicTimer->Cancel();
>
>         // TODO: Record whether the task completed or was cancelled.
>     }
> ```

> <span data-ttu-id="7a7e4-138">**Hinweis**  Das oben gezeigte Codebeispiel verwendet die Eigenschaft [**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797).[**Progress**](https://msdn.microsoft.com/library/windows/apps/br224800), mit der der Fortschritt der Hintergrundaufgabe aufgezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-138">**Note**  The code sample shown above uses the [**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797).[**Progress**](https://msdn.microsoft.com/library/windows/apps/br224800) property being used to record background task progress.</span></span> <span data-ttu-id="7a7e4-139">Der Fortschritt wird der App mithilfe der [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782)-Klasse gemeldet.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-139">Progress is reported back to the app using the [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782) class.</span></span>

<span data-ttu-id="7a7e4-140">Ändern Sie die Run-Methode, damit sie nach dem Anhalten der Arbeit aufzeichnet, ob die Aufgabe ausgeführt oder abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-140">Modify the Run method so that after work has stopped, it records whether the task completed or was cancelled.</span></span> <span data-ttu-id="7a7e4-141">Dieser Schritt gilt für Hintergrundaufgaben außerhalb von Prozessen, da eine Möglichkeit für die Kommunikation zwischen Prozessen haben müssen, wenn die Hintergrundaufgabe abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-141">This step applies to out-of-process background tasks because you need a way to communicate between processes when the background task was cancelled.</span></span> <span data-ttu-id="7a7e4-142">Für Hintergrundaufgaben innerhalb von Prozessen können Sie den Status einfach mit der Anwendung teilen, um anzugeben, dass die Aufgabe abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-142">For in-process background tasks, you can simply share state with the application to indicate the task was cancelled.</span></span>

<span data-ttu-id="7a7e4-143">Das [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) zeichnet den Status in „LocalSettings“ auf:</span><span class="sxs-lookup"><span data-stu-id="7a7e4-143">The [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) records status in LocalSettings:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         var settings = ApplicationData.Current.LocalSettings;
>         var key = _taskInstance.Task.TaskId.ToString();
>
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>
>         if (_cancelRequested)
>         {
>             settings.Values[key] = "Canceled";
>         }
>         else
>         {
>             settings.Values[key] = "Completed";
>         }
>         
>         Debug.WriteLine("Background " + _taskInstance.Task.Name + (_cancelRequested ? " Canceled" : " Completed"));
>         
>         //
>         // Indicate that the background task has completed.
>         //
>
>         _deferral.Complete();
>     }
> ```
> ```cpp
>     if ((CancelRequested == false) && (Progress < 100))
>     {
>         Progress += 10;
>         TaskInstance->Progress = Progress;
>     }
>     else
>     {
>         PeriodicTimer->Cancel();
>         
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>         
>         auto settings = ApplicationData::Current->LocalSettings;
>         auto key = TaskInstance->Task->Name;
>         settings->Values->Insert(key, (Progress < 100) ? "Canceled" : "Completed");
>         
>         //
>         // Indicate that the background task has completed.
>         //
>         
>         Deferral->Complete();
>     }
> ```

## <a name="remarks"></a><span data-ttu-id="7a7e4-144">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="7a7e4-144">Remarks</span></span>

<span data-ttu-id="7a7e4-145">Sie können das [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunterladen, um diese Codebeispiele im Kontext von Methoden anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7a7e4-145">You can download the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) to see these code examples in the context of methods.</span></span>

<span data-ttu-id="7a7e4-146">Zu Demonstrationszwecken enthält der Beispielcode nur Teile der Run-Methode (und des Rückruftimers) aus dem [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="7a7e4-146">For illustrative purposes, the sample code shows only portions of the Run method (and callback timer) from the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

## <a name="run-method-example"></a><span data-ttu-id="7a7e4-147">Beispiel der Run-Methode</span><span class="sxs-lookup"><span data-stu-id="7a7e4-147">Run method example</span></span>

<span data-ttu-id="7a7e4-148">Im Folgenden sind die vollständige Run-Methode und den Timerrückruf-Code aus dem [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7a7e4-148">The complete Run method, and timer callback code, from the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) are shown below for context:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
> //
> // The Run method is the entry point of a background task.
> //
> public void Run(IBackgroundTaskInstance taskInstance)
> {
>     Debug.WriteLine("Background " + taskInstance.Task.Name + " Starting...");
>
>     //
>     // Query BackgroundWorkCost
>     // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
>     // of work in the background task and return immediately.
>     //
>     var cost = BackgroundWorkCost.CurrentBackgroundWorkCost;
>     var settings = ApplicationData.Current.LocalSettings;
>     settings.Values["BackgroundWorkCost"] = cost.ToString();
>
>     //
>     // Associate a cancellation handler with the background task.
>     //
>     taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);
>
>     //
>     // Get the deferral object from the task instance, and take a reference to the taskInstance;
>     //
>     _deferral = taskInstance.GetDeferral();
>     _taskInstance = taskInstance;
>
>     _periodicTimer = ThreadPoolTimer.CreatePeriodicTimer(new TimerElapsedHandler(PeriodicTimerCallback), TimeSpan.FromSeconds(1));
> }
>
> //
> // Simulate the background task activity.
> //
> private void PeriodicTimerCallback(ThreadPoolTimer timer)
> {
>     if ((_cancelRequested == false) && (_progress < 100))
>     {
>         _progress += 10;
>         _taskInstance.Progress = _progress;
>     }
>     else
>     {
>         _periodicTimer.Cancel();
>
>         var settings = ApplicationData.Current.LocalSettings;
>         var key = _taskInstance.Task.Name;
>
>         //
>         // Write to LocalSettings to indicate that this background task ran.
>         //
>         settings.Values[key] = (_progress < 100) ? "Canceled with reason: " + _cancelReason.ToString() : "Completed";
>         Debug.WriteLine("Background " + _taskInstance.Task.Name + settings.Values[key]);
>
>         //
>         // Indicate that the background task has completed.
>         //
>         _deferral.Complete();
>     }
> }
> ```
> ```cpp
> void SampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
> {
>     //
>     // Query BackgroundWorkCost
>     // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
>     // of work in the background task and return immediately.
>     //
>     auto cost = BackgroundWorkCost::CurrentBackgroundWorkCost;
>     auto settings = ApplicationData::Current->LocalSettings;
>     settings->Values->Insert("BackgroundWorkCost", cost.ToString());
>
>     //
>     // Associate a cancellation handler with the background task.
>     //
>     taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &SampleBackgroundTask::OnCanceled);
>
>     //
>     // Get the deferral object from the task instance, and take a reference to the taskInstance.
>     //
>     TaskDeferral = taskInstance->GetDeferral();
>     TaskInstance = taskInstance;
>
>     auto timerDelegate = [this](ThreadPoolTimer^ timer)
>     {
>         if ((CancelRequested == false) &&
>             (Progress < 100))
>         {
>             Progress += 10;
>             TaskInstance->Progress = Progress;
>         }
>         else
>         {
>             PeriodicTimer->Cancel();
>
>             //
>             // Write to LocalSettings to indicate that this background task ran.
>             //
>             auto settings = ApplicationData::Current->LocalSettings;
>             auto key = TaskInstance->Task->Name;
>             settings->Values->Insert(key, (Progress < 100) ? "Canceled with reason: " + CancelReason.ToString() : "Completed");
>
>             //
>             // Indicate that the background task has completed.
>             //
>             TaskDeferral->Complete();
>         }
>     };
>
>     TimeSpan period;
>     period.Duration = 1000 * 10000; // 1 second
>     PeriodicTimer = ThreadPoolTimer::CreatePeriodicTimer(ref new TimerElapsedHandler(timerDelegate), period);
> }
> ```

## <a name="related-topics"></a><span data-ttu-id="7a7e4-149">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7a7e4-149">Related topics</span></span>

- <span data-ttu-id="7a7e4-150">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="7a7e4-150">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
- [<span data-ttu-id="7a7e4-151">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="7a7e4-151">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
- [<span data-ttu-id="7a7e4-152">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="7a7e4-152">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
- [<span data-ttu-id="7a7e4-153">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="7a7e4-153">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
- [<span data-ttu-id="7a7e4-154">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="7a7e4-154">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
- [<span data-ttu-id="7a7e4-155">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-155">Register a background task</span></span>](register-a-background-task.md)
- [<span data-ttu-id="7a7e4-156">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="7a7e4-156">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
- [<span data-ttu-id="7a7e4-157">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="7a7e4-157">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
- [<span data-ttu-id="7a7e4-158">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-158">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
- [<span data-ttu-id="7a7e4-159">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-159">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
- [<span data-ttu-id="7a7e4-160">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="7a7e4-160">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
- [<span data-ttu-id="7a7e4-161">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7a7e4-161">Debug a background task</span></span>](debug-a-background-task.md)
- [<span data-ttu-id="7a7e4-162">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="7a7e4-162">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)