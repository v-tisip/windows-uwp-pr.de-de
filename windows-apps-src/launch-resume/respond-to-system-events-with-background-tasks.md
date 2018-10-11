---
author: TylerMSFT
title: Reagieren auf Systemereignisse mit Hintergrundaufgaben
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen können, die auf SystemTrigger-Ereignisse reagiert.
ms.assetid: 43C21FEA-28B9-401D-80BE-A61B71F01A89
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 45f6e10bc355e3a2dc054d54fef35fbeb1095dc7
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4533442"
---
# <a name="respond-to-system-events-with-background-tasks"></a><span data-ttu-id="9b6fd-104">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="9b6fd-104">Respond to system events with background tasks</span></span>

**<span data-ttu-id="9b6fd-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9b6fd-105">Important APIs</span></span>**

- [**<span data-ttu-id="9b6fd-106">IBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="9b6fd-106">IBackgroundTask</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
- [**<span data-ttu-id="9b6fd-107">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="9b6fd-107">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
- [**<span data-ttu-id="9b6fd-108">SystemTrigger</span><span class="sxs-lookup"><span data-stu-id="9b6fd-108">SystemTrigger</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224838)

<span data-ttu-id="9b6fd-109">Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen können, die auf [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839)-Ereignisse reagiert.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-109">Learn how to create a background task that responds to [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) events.</span></span>

<span data-ttu-id="9b6fd-110">Dieses Thema setzt voraus, dass Sie für Ihre App eine Hintergrundaufgabenklasse geschrieben haben und dass diese Aufgabe als Reaktion auf ein vom System ausgelöstes Ereignis ausgeführt werden muss, z.B. wenn sich die Internetverfügbarkeit ändert oder sich der Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-110">This topic assumes that you have a background task class written for your app, and that this task needs to run in response to an event triggered by the system such as when internet availability changes or the user logging in.</span></span> <span data-ttu-id="9b6fd-111">Der Schwerpunkt dieses Themas liegt auf der [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-111">This topic focuses on the [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) class.</span></span> <span data-ttu-id="9b6fd-112">Weitere Informationen zum Schreiben einer Hintergrundaufgabenklasse finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="9b6fd-112">More information on writing a background task class is available in [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) or [Create and register an out-of-process background task](create-and-register-a-background-task.md).</span></span>

## <a name="create-a-systemtrigger-object"></a><span data-ttu-id="9b6fd-113">Erstellen eines SystemTrigger-Objekts</span><span class="sxs-lookup"><span data-stu-id="9b6fd-113">Create a SystemTrigger object</span></span>

<span data-ttu-id="9b6fd-114">Erstellen Sie in Ihrem App-Code ein neues [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-114">In your app code, create a new [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838) object.</span></span> <span data-ttu-id="9b6fd-115">*triggerType* ist der erste Parameter und gibt den Typ des Systemereignis-Triggers zur Aktivierung der Hintergrundaufgabe an.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-115">The first parameter, *triggerType*, specifies the type of system event trigger that will activate this background task.</span></span> <span data-ttu-id="9b6fd-116">Eine Liste mit Ereignistypen finden Sie unter [**SystemTriggerType**](https://msdn.microsoft.com/library/windows/apps/br224839).</span><span class="sxs-lookup"><span data-stu-id="9b6fd-116">For a list of event types, see [**SystemTriggerType**](https://msdn.microsoft.com/library/windows/apps/br224839).</span></span>

<span data-ttu-id="9b6fd-117">Der zweite Parameter (*OneShot*) gibt an, ob die Hintergrundaufgabe nur einmal ausgeführt wird, wenn das Systemereignis das nächste Mal eintritt, oder ob die Hintergrundaufgabe beim Auslösen des Systemereignisses immer ausgeführt wird, bis die Registrierung der Aufgabe aufgehoben wird.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-117">The second parameter, *OneShot*, specifies whether the background task will run only once the next time the system event occurs or every time the system event occurs until the task is unregistered.</span></span>

<span data-ttu-id="9b6fd-118">Der folgende Code gibt an, dass die Hintergrundaufgabe immer ausgeführt wird, wenn das Internet verfügbar wird:</span><span class="sxs-lookup"><span data-stu-id="9b6fd-118">The following code specifies that the background task runs whenever the Internet becomes available:</span></span>

```csharp
SystemTrigger internetTrigger = new SystemTrigger(SystemTriggerType.InternetAvailable, false);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemTrigger internetTrigger{
    Windows::ApplicationModel::Background::SystemTriggerType::InternetAvailable, false};
```

```cpp
SystemTrigger ^ internetTrigger = ref new SystemTrigger(SystemTriggerType::InternetAvailable, false);
```

## <a name="register-the-background-task"></a><span data-ttu-id="9b6fd-119">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-119">Register the background task</span></span>

<span data-ttu-id="9b6fd-120">Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-120">Register the background task by calling your background task registration function.</span></span> <span data-ttu-id="9b6fd-121">Weitere Informationen zum Registrieren von Hintergrundaufgaben finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="9b6fd-121">For more information on registering background tasks, see [Register a background task](register-a-background-task.md).</span></span>

<span data-ttu-id="9b6fd-122">Der folgende Code registriert die Hintergrundaufgabe für einen Hintergrundprozess, der außerhalb des Prozesses ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-122">The following code registers the background task for a background process that runs out-of-process.</span></span> <span data-ttu-id="9b6fd-123">Wenn Sie eine Hintergrundaufgabe aufrufen, die im gleichen Prozess wie die Host-App ausgeführt wird, legen Sie nicht `entrypoint` fest:</span><span class="sxs-lookup"><span data-stu-id="9b6fd-123">If you were calling a background task that runs in the same process as the host app, you would not set `entrypoint`:</span></span>

```csharp
string entryPoint = "Tasks.ExampleBackgroundTaskClass"; // Namespace name, '.', and the name of the class containing the background task
string taskName   = "Internet-based background task";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, internetTrigger, exampleCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" }; // don't set for in-process background tasks.
std::wstring taskName{ L"Internet-based background task" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, internetTrigger, exampleCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass"; // don't set for in-process background tasks
String ^ taskName   = "Internet-based background task";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, internetTrigger, exampleCondition);
```

> [!NOTE]
> <span data-ttu-id="9b6fd-124">Universelle Windows-Plattform-apps müssen [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor hintergrundtrigger-Typen.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-124">Universal Windows Platform apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="9b6fd-125">Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-125">To ensure that your Universal Windows app continues to run properly after you release an update, you must call [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) and then call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) when your app launches after being updated.</span></span> <span data-ttu-id="9b6fd-126">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="9b6fd-126">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9b6fd-127">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-127">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="9b6fd-128">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-128">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="9b6fd-129">Stellen Sie sicher, dass Ihre App Szenarien, in denen die Registrierung von Hintergrundaufgaben einen Fehler verursacht, problemlos verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-129">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>
 
## <a name="remarks"></a><span data-ttu-id="9b6fd-130">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="9b6fd-130">Remarks</span></span>

<span data-ttu-id="9b6fd-131">Laden Sie das [Beispiel zu Hintergrundaufgaben](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunter, um die Registrierung der Hintergrundaufgabe in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-131">To see background task registration in action, download the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

<span data-ttu-id="9b6fd-132">Hintergrundaufgaben können als Reaktion auf die Ereignisse [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838) und [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517) ausgeführt werden. Dennoch ist das [Deklarieren von Hintergrundaufgaben im Anwendungsmanifest](declare-background-tasks-in-the-application-manifest.md) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-132">Background tasks can run in response to [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224838) and [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517) events, but you still need to [Declare background tasks in the application manifest](declare-background-tasks-in-the-application-manifest.md).</span></span> <span data-ttu-id="9b6fd-133">Vor dem Registrieren einer Hintergrundaufgabe müssen Sie außerdem [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-133">You must also call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any background task type.</span></span>

<span data-ttu-id="9b6fd-134">Apps können Hintergrundaufgaben registrieren, die auf die Ereignisse [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843), [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543) und [**NetworkOperatorNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/br224831) reagieren. So können die Apps eine Echtzeitkommunikation mit dem Benutzer bereitstellen, auch wenn die App sich nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="9b6fd-134">Apps can register background tasks that respond to [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843), [**PushNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700543), and [**NetworkOperatorNotificationTrigger**](https://msdn.microsoft.com/library/windows/apps/br224831) events, enabling them to provide real-time communication with the user even when the app is not in the foreground.</span></span> <span data-ttu-id="9b6fd-135">Weitere Informationen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="9b6fd-135">For more information, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="9b6fd-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9b6fd-136">Related topics</span></span>

* [<span data-ttu-id="9b6fd-137">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="9b6fd-137">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="9b6fd-138">Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="9b6fd-138">Create and register an in-process background task</span></span>](create-and-register-an-inproc-background-task.md)
* [<span data-ttu-id="9b6fd-139">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="9b6fd-139">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="9b6fd-140">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-140">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="9b6fd-141">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="9b6fd-141">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="9b6fd-142">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-142">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="9b6fd-143">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-143">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="9b6fd-144">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-144">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="9b6fd-145">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="9b6fd-145">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="9b6fd-146">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="9b6fd-146">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* [<span data-ttu-id="9b6fd-147">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="9b6fd-147">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="9b6fd-148">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="9b6fd-148">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="9b6fd-149">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="9b6fd-149">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
