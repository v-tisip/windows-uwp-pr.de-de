---
author: TylerMSFT
title: Erstellen und Registrieren einer In-Process-Hintergrundaufgabe
description: Erstellen und registrieren Sie eine In-Process-Aufgabe, die im gleichen Prozess wie die Vordergrund-App ausgeführt wird.
ms.author: twhitney
ms.date: 11/03/2017
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.assetid: d99de93b-e33b-45a9-b19f-31417f1e9354
ms.localizationpriority: medium
ms.openlocfilehash: 1eeac0239bd0c6df38f82fa185c1ed6f7eb3f9dc
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6264520"
---
# <a name="create-and-register-an-in-process-background-task"></a><span data-ttu-id="3a74b-104">Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="3a74b-104">Create and register an in-process background task</span></span>

**<span data-ttu-id="3a74b-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="3a74b-105">Important APIs</span></span>**

-   [**<span data-ttu-id="3a74b-106">IBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="3a74b-106">IBackgroundTask</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**<span data-ttu-id="3a74b-107">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="3a74b-107">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
-   [**<span data-ttu-id="3a74b-108">BackgroundTaskCompletedEventHandler</span><span class="sxs-lookup"><span data-stu-id="3a74b-108">BackgroundTaskCompletedEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224781)

<span data-ttu-id="3a74b-109">In diesem Thema wird gezeigt, wie Sie eine Hintergrundaufgabe erstellen und registrieren, die im gleichen Prozess wie Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a74b-109">This topic demonstrates how to create and register a background task that runs in the same process as your app.</span></span>

<span data-ttu-id="3a74b-110">In-Process-Hintergrundaufgaben sind einfacher als Out-of-Process-Hintergrundaufgaben zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="3a74b-110">In-process background tasks are simpler to implement than out-of-process background tasks.</span></span> <span data-ttu-id="3a74b-111">Sie sind jedoch weniger stabil.</span><span class="sxs-lookup"><span data-stu-id="3a74b-111">However, they are less resilient.</span></span> <span data-ttu-id="3a74b-112">Wenn der in einer in-Process-Hintergrundaufgabe ausgeführte Code abstürzt, wirkt sich dies auf Ihre App aus.</span><span class="sxs-lookup"><span data-stu-id="3a74b-112">If the code running in an in-process background task crashes, it will take down your app.</span></span> <span data-ttu-id="3a74b-113">Beachten Sie außerdem, dass [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) und **IoTStartupTask** nicht mit dem In-Process-Modell verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="3a74b-113">Also note that [DeviceUseTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceusetrigger.aspx), [DeviceServicingTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.deviceservicingtrigger.aspx) and **IoTStartupTask** cannot be used with the in-process model.</span></span> <span data-ttu-id="3a74b-114">Zudem ist das Aktivieren einer VoIP-Hintergrundaufgabe innerhalb der Anwendung nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="3a74b-114">Activating a VoIP background task within your application is also not possible.</span></span> <span data-ttu-id="3a74b-115">Diese Trigger und Aufgaben werden bei Verwendung des Out-of-Process-Hintergrundaufgabenmodells weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a74b-115">These triggers and tasks are still supported using the out-of-process background task model.</span></span>

<span data-ttu-id="3a74b-116">Beachten Sie, dass Hintergrundaktivitäten auch bei Ausführung innerhalb des Vordergrundprozesses der App beendet werden können, wenn Ausführungszeitlimits überschritten werden.</span><span class="sxs-lookup"><span data-stu-id="3a74b-116">Be aware that background activity can be terminated even when running inside the app's foreground process if it runs past execution time limits.</span></span> <span data-ttu-id="3a74b-117">Für bestimmte Zwecke ist die Resilienz der Trennung von Arbeiten in eine Hintergrundaufgabe, die in einem separaten Prozess ausgeführt wird, weiterhin hilfreich.</span><span class="sxs-lookup"><span data-stu-id="3a74b-117">For some purposes the resiliency of separating work into a background task that runs in a separate process is still useful.</span></span> <span data-ttu-id="3a74b-118">Die Trennung von Hintergrundarbeiten als Aufgabe von der Vordergrundanwendung kann die beste Option für Arbeiten sein, die keine Kommunikation mit der Vordergrundanwendung erfordern.</span><span class="sxs-lookup"><span data-stu-id="3a74b-118">Keeping background work as a task separate from the foreground application may be the best option for work that does not require communication with the foreground application.</span></span>

## <a name="fundamentals"></a><span data-ttu-id="3a74b-119">Grundlagen</span><span class="sxs-lookup"><span data-stu-id="3a74b-119">Fundamentals</span></span>

<span data-ttu-id="3a74b-120">Das In-Process-Modell erweitert den Anwendungslebenszyklus um verbesserte Benachrichtigungen, wenn sich die App im Vordergrund oder im Hintergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="3a74b-120">The in-process model enhances the application lifecycle with improved notifications for when your app is in the foreground or in the background.</span></span> <span data-ttu-id="3a74b-121">Zwei neue Ereignisse sind vom Anwendungsobjekt für diese Übergänge verfügbar: [**EnteredBackground**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.Core.CoreApplication.EnteredBackground) und [**LeavingBackground**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.Core.CoreApplication.LeavingBackground).</span><span class="sxs-lookup"><span data-stu-id="3a74b-121">Two new events are available from the Application object for these transitions: [**EnteredBackground**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.Core.CoreApplication.EnteredBackground) and [**LeavingBackground**](https://msdn.microsoft.com/library/windows/apps/Windows.ApplicationModel.Core.CoreApplication.LeavingBackground).</span></span> <span data-ttu-id="3a74b-122">Diese Ereignisse passen je nach Sichtbarkeitszustand der Anwendung in den Anwendungslebenszyklus. Weitere Informationen zu diesen Ereignissen und deren Auswirkungen auf den Anwendungslebenszyklus finden Sie unter [App-Lebenszyklus](app-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="3a74b-122">These events fit into the application lifecycle based on the visibility state of your application Read more about these events and how they affect the application lifecycle at [App lifecycle](app-lifecycle.md).</span></span>

<span data-ttu-id="3a74b-123">Auf oberer Ebene behandeln Sie das **EnteredBackground**-Ereignis zum Ausführen von Code bei der Ausführung der App im Hintergrund und das **LeavingBackground**-Ereignis, um zu erfahren, wann Ihre App in den Vordergrund verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3a74b-123">At a high level, you will handle the **EnteredBackground** event to run your code that will execute while your app is running in the background, and handle **LeavingBackground** to know when your app has moved to the foreground.</span></span>

## <a name="register-your-background-task-trigger"></a><span data-ttu-id="3a74b-124">Registrieren des Triggers für die Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-124">Register your background task trigger</span></span>

<span data-ttu-id="3a74b-125">In-Process-Hintergrundaktivitäten werden ähnlich wie Out-of-Process-Hintergrundaktivitäten registriert.</span><span class="sxs-lookup"><span data-stu-id="3a74b-125">In-process background activity is registered much the same as out-of-process background activity.</span></span> <span data-ttu-id="3a74b-126">Alle Hintergrundtrigger werden mit der Registrierung mit [BackgroundTaskBuilder](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundtaskbuilder.aspx?f=255&MSPPError=-2147217396) gestartet.</span><span class="sxs-lookup"><span data-stu-id="3a74b-126">All background triggers start with registration using the [BackgroundTaskBuilder](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundtaskbuilder.aspx?f=255&MSPPError=-2147217396).</span></span> <span data-ttu-id="3a74b-127">Der Generator vereinfacht die Registrierung einer Hintergrundaufgabe, indem alle erforderlichen Werte an einem zentralen Ort festlegt werden:</span><span class="sxs-lookup"><span data-stu-id="3a74b-127">The builder makes it easy to register a background task by setting all required values in one place:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
> var builder = new BackgroundTaskBuilder();
> builder.Name = "My Background Trigger";
> builder.SetTrigger(new TimeTrigger(15, true));
> // Do not set builder.TaskEntryPoint for in-process background tasks
> // Here we register the task and work will start based on the time trigger.
> BackgroundTaskRegistration task = builder.Register();
> ```

> [!NOTE]
> <span data-ttu-id="3a74b-128">Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrundtrigger-Typen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="3a74b-128">Universal Windows apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>
> <span data-ttu-id="3a74b-129">Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a74b-129">To ensure that your Universal Windows app continues to run properly after you release an update, you must call [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) and then call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) when your app launches after being updated.</span></span> <span data-ttu-id="3a74b-130">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="3a74b-130">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

<span data-ttu-id="3a74b-131">In-Process-Hintergrundaktivitäten erfolgen ohne das Festlegen von `TaskEntryPoint.` Bleibt dieser Wert leer, wird der Standardeinstiegspunkt aktiviert, eine neue geschützte Methode für das Application-Objekt namens [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx).</span><span class="sxs-lookup"><span data-stu-id="3a74b-131">For in-process background activities you do not set `TaskEntryPoint.` Leaving it blank enables the default entry point, a new protected method on the Application object called [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx).</span></span>

<span data-ttu-id="3a74b-132">Sobald ein Trigger registriert ist, wird er basierend auf dem in der [SetTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundtaskbuilder.settrigger.aspx)-Methode festgelegten Triggertyp ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="3a74b-132">Once a trigger is registered, it will fire based on the type of trigger set in the [SetTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundtaskbuilder.settrigger.aspx) method.</span></span> <span data-ttu-id="3a74b-133">Im obigen Beispiel wird ein [TimeTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.timetrigger.aspx) verwendet, der 15Minuten nach dem Registrierungszeitpunkt ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="3a74b-133">In the example above a [TimeTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.timetrigger.aspx) is used, which will fire fifteen minutes from the time it was registered.</span></span>

## <a name="add-a-condition-to-control-when-your-task-will-run-optional"></a><span data-ttu-id="3a74b-134">Hinzufügen einer Bedingung, die bestimmt, wann Ihre Aufgabe ausgeführt wird (optional)</span><span class="sxs-lookup"><span data-stu-id="3a74b-134">Add a condition to control when your task will run (optional)</span></span>

<span data-ttu-id="3a74b-135">Sie können eine Bedingung hinzufügen, die bestimmt, wann Ihre Aufgabe ausgeführt wird, nachdem das Auslöseereignis eintritt.</span><span class="sxs-lookup"><span data-stu-id="3a74b-135">You can add a condition to control when your task will run after the trigger event occurs.</span></span> <span data-ttu-id="3a74b-136">Wenn Sie zum Beispiel möchten, dass die Aufgabe erst ausgeführt wird, wenn der Benutzer anwesend ist, verwenden Sie die Bedingung **UserPresent**.</span><span class="sxs-lookup"><span data-stu-id="3a74b-136">For example, if you don't want the task to run until the user is present, use the condition **UserPresent**.</span></span> <span data-ttu-id="3a74b-137">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="3a74b-137">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

<span data-ttu-id="3a74b-138">Der folgende Beispielcode weist eine Bedingung zu, die die Anwesenheit des Benutzers voraussetzt:</span><span class="sxs-lookup"><span data-stu-id="3a74b-138">The following sample code assigns a condition requiring the user to be present:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```cs
> builder.AddCondition(new SystemCondition(SystemConditionType.UserPresent));
> ```

## <a name="place-your-background-activity-code-in-onbackgroundactivated"></a><span data-ttu-id="3a74b-139">Platzieren des Codes der Hintergrundaktivität in „OnBackgroundActivated()“</span><span class="sxs-lookup"><span data-stu-id="3a74b-139">Place your background activity code in OnBackgroundActivated()</span></span>

<span data-ttu-id="3a74b-140">Platzieren Sie den Code der Hintergrundaktivität in [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) , auf dem Hintergrund-Trigger zu reagieren, wenn dieser ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="3a74b-140">Put your background activity code in [OnBackgroundActivated](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx) to respond to your background trigger when it fires.</span></span> <span data-ttu-id="3a74b-141">**OnBackgroundActivated** kann genau wie [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396)behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="3a74b-141">**OnBackgroundActivated** can be treated just like [IBackgroundTask.Run](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.ibackgroundtask.run.aspx?f=255&MSPPError=-2147217396).</span></span> <span data-ttu-id="3a74b-142">Die Methode verfügt über einen [BackgroundActivatedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.activation.backgroundactivatedeventargs.aspx) -Parameter, der alles enthält, die die **Run** -Methode bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="3a74b-142">The method has a [BackgroundActivatedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.activation.backgroundactivatedeventargs.aspx) parameter, which contains everything that the **Run** method delivers.</span></span> <span data-ttu-id="3a74b-143">Z. B. in "App.Xaml.cs":</span><span class="sxs-lookup"><span data-stu-id="3a74b-143">For example, in App.xaml.cs:</span></span>

``` cs
using Windows.ApplicationModel.Background;

...

sealed partial class App : Application
{
  ...

  protected override void OnBackgroundActivated(BackgroundActivatedEventArgs args)
  {
      base.OnBackgroundActivated(args);
      IBackgroundTaskInstance taskInstance = args.TaskInstance;
      DoYourBackgroundWork(taskInstance);  
  }
}
```

<span data-ttu-id="3a74b-144">Ein Beispiel für eine umfangreichere **OnBackgroundActivated** finden Sie unter [Konvertieren eines app-Diensts für die Ausführung im gleichen Prozess wie seine Host-app](convert-app-service-in-process.md).</span><span class="sxs-lookup"><span data-stu-id="3a74b-144">For a richer **OnBackgroundActivated** example, see [Convert an app service to run in the same process as its host app](convert-app-service-in-process.md).</span></span>

## <a name="handle-background-task-progress-and-completion"></a><span data-ttu-id="3a74b-145">Behandeln des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-145">Handle background task progress and completion</span></span>

<span data-ttu-id="3a74b-146">Der Aufgabenstatus und -abschluss kann genauso wie bei Multiprozess-Hintergrundaufgaben überwacht werden (siehe [Überwachen von Status und Durchführung von Hintergrundaufgaben](monitor-background-task-progress-and-completion.md)). Wahrscheinlich stellen Sie jedoch fest, dass die Überwachung mithilfe von Variablen zum Nachverfolgen von Status oder Abschluss in Ihrer App einfacher ist.</span><span class="sxs-lookup"><span data-stu-id="3a74b-146">Task progress and completion can be monitored the same way as for multi-process background tasks (see [Monitor background task progress and completion](monitor-background-task-progress-and-completion.md)) but you will likely find that you can more easily track them by using variables to track progress or completion status in your app.</span></span> <span data-ttu-id="3a74b-147">Dies ist einer der Vorteile, wenn der Code der Hintergrundaktivität im selben Prozess wie Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a74b-147">This is one of the advantages of having your background activity code running in the same process as your app.</span></span>

## <a name="handle-background-task-cancellation"></a><span data-ttu-id="3a74b-148">Behandeln des Abbruchs von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-148">Handle background task cancellation</span></span>

<span data-ttu-id="3a74b-149">In-Process-Hintergrundaufgaben werden auf die gleiche Weise abgebrochen wie Out-of-Process-Hintergrundaufgaben (siehe [Behandeln einer abgebrochenen Hintergrundaufgabe](handle-a-cancelled-background-task.md)).</span><span class="sxs-lookup"><span data-stu-id="3a74b-149">In-process background tasks are cancelled the same way as out-of-process background tasks are (see [Handle a cancelled background task](handle-a-cancelled-background-task.md)).</span></span> <span data-ttu-id="3a74b-150">Beachten Sie, dass der **BackgroundActivated**-Ereignishandler vor dem Abbruch beendet werden muss, oder der gesamte Prozess wird beendet.</span><span class="sxs-lookup"><span data-stu-id="3a74b-150">Be aware that your **BackgroundActivated** event handler must exit before the cancellation occurs, or the whole process will be terminated.</span></span> <span data-ttu-id="3a74b-151">Wenn die Vordergrund-App beim Abbrechen der Hintergrundaufgabe unerwartet geschlossen wird, überprüfen Sie, ob der Handler vor dem Abbruch beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3a74b-151">If your foreground app closes unexpectedly when you cancel the background task, verify that your handler exited before the cancellation occured.</span></span>

## <a name="the-manifest"></a><span data-ttu-id="3a74b-152">Das Manifest</span><span class="sxs-lookup"><span data-stu-id="3a74b-152">The manifest</span></span>

<span data-ttu-id="3a74b-153">Im Gegensatz zu Out-of-Process-Hintergrundaufgaben müssen Sie dem Paketmanifest keine Hintergrundaufgabeninformationen hinzufügen, um In-Process-Hintergrundaufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3a74b-153">Unlike out-of-process background tasks, you are not required to add background task information to the package manifest in order to run in-process background tasks.</span></span>

## <a name="summary-and-next-steps"></a><span data-ttu-id="3a74b-154">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3a74b-154">Summary and next steps</span></span>

<span data-ttu-id="3a74b-155">Sie sollten jetzt über die Grundlagen verfügen, um eine In-Process-Hintergrundaufgabe zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="3a74b-155">You should now understand the basics of how to write a in-process background task.</span></span>

<span data-ttu-id="3a74b-156">Eine API-Referenz, konzeptionelle Richtlinien zu Hintergrundaufgaben und ausführlichere Anweisungen zum Schreiben von Apps, die Hintergrundaufgaben verwenden, finden Sie unter den folgenden verwandten Themen:</span><span class="sxs-lookup"><span data-stu-id="3a74b-156">See the following related topics for API reference, background task conceptual guidance, and more detailed instructions for writing apps that use background tasks.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3a74b-157">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3a74b-157">Related topics</span></span>

**<span data-ttu-id="3a74b-158">Ausführliche Themen mit Anweisungen zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-158">Detailed background task instructional topics</span></span>**

* [<span data-ttu-id="3a74b-159">Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-159">Convert an out-of-process background task to an in-process background task</span></span>](convert-out-of-process-background-task.md)
* [<span data-ttu-id="3a74b-160">Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-160">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="3a74b-161">Wiedergeben von Medien im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="3a74b-161">Play media in the background</span></span>](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio)
* [<span data-ttu-id="3a74b-162">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-162">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="3a74b-163">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-163">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="3a74b-164">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-164">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="3a74b-165">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="3a74b-165">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="3a74b-166">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-166">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="3a74b-167">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-167">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="3a74b-168">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="3a74b-168">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)

**<span data-ttu-id="3a74b-169">Ratschläge zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-169">Background task guidance</span></span>**

* [<span data-ttu-id="3a74b-170">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="3a74b-170">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="3a74b-171">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="3a74b-171">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="3a74b-172">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="3a74b-172">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)

**<span data-ttu-id="3a74b-173">Hintergrundaufgabe – API-Referenz</span><span class="sxs-lookup"><span data-stu-id="3a74b-173">Background Task API Reference</span></span>**

* [**<span data-ttu-id="3a74b-174">Windows.ApplicationModel.Background</span><span class="sxs-lookup"><span data-stu-id="3a74b-174">Windows.ApplicationModel.Background</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)
