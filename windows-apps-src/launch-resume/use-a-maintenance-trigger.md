---
author: TylerMSFT
title: Verwenden eines Wartungsauslösers
description: Hier erfahren Sie, wie Sie die MaintenanceTrigger-Klasse zum Ausführen von einfachem Code im Hintergrund verwenden, während das Gerät eingesteckt ist.
ms.assetid: 727D9D84-6C1D-4DF3-B3B0-2204EA4D76DD
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 5f11afbafc424a4ed7f2c973f0417c792ab7da65
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "6050206"
---
# <a name="use-a-maintenance-trigger"></a><span data-ttu-id="5e9a0-104">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="5e9a0-104">Use a maintenance trigger</span></span>

**<span data-ttu-id="5e9a0-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5e9a0-105">Important APIs</span></span>**

- [**<span data-ttu-id="5e9a0-106">MaintenanceTrigger</span><span class="sxs-lookup"><span data-stu-id="5e9a0-106">MaintenanceTrigger</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh700517)
- [**<span data-ttu-id="5e9a0-107">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="5e9a0-107">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
- [**<span data-ttu-id="5e9a0-108">SystemCondition</span><span class="sxs-lookup"><span data-stu-id="5e9a0-108">SystemCondition</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224834)

<span data-ttu-id="5e9a0-109">Hier erfahren Sie, wie Sie die [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517)-Klasse zum Ausführen von einfachem Code im Hintergrund verwenden, während das Gerät eingesteckt ist.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-109">Learn how to use the [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517) class to run lightweight code in the background while the device is plugged in.</span></span>

## <a name="create-a-maintenance-trigger-object"></a><span data-ttu-id="5e9a0-110">Erstellen eines MaintenanceTrigger-Objekts</span><span class="sxs-lookup"><span data-stu-id="5e9a0-110">Create a maintenance trigger object</span></span>

<span data-ttu-id="5e9a0-111">In diesem Beispiel wird davon ausgegangen, dass Sie über einfachen Code verfügen, den Sie im Hintergrund ausführen können, um Ihre App zu optimieren, wenn das Gerät eingesteckt ist.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-111">This example assumes that you have lightweight code you can run in the background to enhance your app while the device is plugged in.</span></span> <span data-ttu-id="5e9a0-112">Der Schwerpunkt dieses Themas liegt auf der [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517)-Klasse, die der [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839)-Klasse ähnelt.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-112">This topic focuses on the [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517), which is similar to [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).</span></span>

<span data-ttu-id="5e9a0-113">Weitere Informationen zum Schreiben einer Hintergrundaufgabenklasse finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-113">More information on writing a background task class is available in [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) or [Create and register an out-of-process background task](create-and-register-a-background-task.md).</span></span>

<span data-ttu-id="5e9a0-114">Erstellen Sie ein neues [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-114">Create a new [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) object.</span></span> <span data-ttu-id="5e9a0-115">Der zweite Parameter *OneShot* gibt an, ob die Wartungsaufgabe nur einmal oder regelmäßig ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-115">The second parameter, *OneShot*, specifies whether the maintenance task will run only once or continue to run periodically.</span></span> <span data-ttu-id="5e9a0-116">Wenn *OneShot* auf „true“ festgelegt ist, gibt der erste Parameter (*FreshnessTime*) an, wie lange mit der Planung der Hintergrundaufgabe gewartet werden soll (in Minuten).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-116">If *OneShot* is set to true, the first parameter (*FreshnessTime*) specifies the number of minutes to wait before scheduling the background task.</span></span> <span data-ttu-id="5e9a0-117">Wenn *OneShot* auf „false“ festgelegt ist, gibt *FreshnessTime* an, wie oft die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-117">If *OneShot* is set to false, *FreshnessTime* specifies how often the background task will run.</span></span>

> [!NOTE]
> <span data-ttu-id="5e9a0-118">Wenn *FreshnessTime* auf weniger als 15 Minuten festgelegt ist, wird eine Ausnahme ausgelöst, wenn Sie versuchen, die Hintergrundaufgabe zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-118">If *FreshnessTime* is set to less than 15 minutes, an exception is thrown when attempting to register the background task.</span></span>

<span data-ttu-id="5e9a0-119">Dieser Beispielcode erstellt einen Trigger, der einmal pro Stunde ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-119">This example code creates a trigger that runs once an hour.</span></span>

```csharp
uint waitIntervalMinutes = 60;
MaintenanceTrigger taskTrigger = new MaintenanceTrigger(waitIntervalMinutes, false);
```

```cppwinrt
uint32_t waitIntervalMinutes{ 60 };
Windows::ApplicationModel::Background::MaintenanceTrigger taskTrigger{ waitIntervalMinutes, false };
```

```cpp
unsigned int waitIntervalMinutes = 60;
MaintenanceTrigger ^ taskTrigger = ref new MaintenanceTrigger(waitIntervalMinutes, false);
```

## <a name="optional-add-a-condition"></a><span data-ttu-id="5e9a0-120">(Optional) Hinzufügen einer Bedingung</span><span class="sxs-lookup"><span data-stu-id="5e9a0-120">(Optional) Add a condition</span></span>

- <span data-ttu-id="5e9a0-121">Erstellen Sie bei Bedarf eine Hintergrundaufgabenbedingung, um zu steuern, wann die Aufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-121">If necessary, create a background task condition to control when the task runs.</span></span> <span data-ttu-id="5e9a0-122">Eine Bedingung sorgt dafür, dass die Hintergrundaufgabe erst ausgeführt wird, wenn die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [Festlegen von Bedingungen für die Ausführung einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-122">A condition prevents your background task from running until the condition is met - for more information, see [Set conditions for running a background task](set-conditions-for-running-a-background-task.md)</span></span>

<span data-ttu-id="5e9a0-123">In diesem Beispiel wird die Bedingung auf **InternetAvailable** festgelegt, damit die Wartung ausgeführt wird, wenn eine Internetverbindung verfügbar ist (oder wird).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-123">In this example, the condition is set to **InternetAvailable** so that maintenance runs when the Internet is available (or when it becomes available).</span></span> <span data-ttu-id="5e9a0-124">Eine Liste mit möglichen Hintergrundaufgabenbedingungen finden Sie unter [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-124">For a list of possible background task conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

<span data-ttu-id="5e9a0-125">Der folgende Code fügt dem Hintergrundaufgaben-Generator eine Bedingung hinzu:</span><span class="sxs-lookup"><span data-stu-id="5e9a0-125">The following code adds a condition to the maintenance task builder:</span></span>

```csharp
SystemCondition exampleCondition = new SystemCondition(SystemConditionType.InternetAvailable);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition exampleCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };
```

```cpp
SystemCondition ^ exampleCondition = ref new SystemCondition(SystemConditionType::InternetAvailable);
```

## <a name="register-the-background-task"></a><span data-ttu-id="5e9a0-126">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-126">Register the background task</span></span>

- <span data-ttu-id="5e9a0-127">Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-127">Register the background task by calling your background task registration function.</span></span> <span data-ttu-id="5e9a0-128">Weitere Informationen zum Registrieren von Hintergrundaufgaben finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-128">For more information on registering background tasks, see [Register a background task](register-a-background-task.md).</span></span>

<span data-ttu-id="5e9a0-129">Der folgende Code registriert die Wartungsaufgabe.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-129">The following code registers the maintenance task.</span></span> <span data-ttu-id="5e9a0-130">Beachten Sie, dass davon ausgegangen wird, dass die Hintergrundaufgaben in einem von Ihrer App getrennten Prozess ausgeführt wird, da `entryPoint` angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-130">Note that it assumes your background task runs in a separate process from your app because it specifies `entryPoint`.</span></span> <span data-ttu-id="5e9a0-131">Wenn die Hintergrundaufgabe in demselben Prozess wie Ihre App ausgeführt wird, wird `entryPoint` nicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-131">If your background task runs in the same process as your app, you do not specify `entryPoint`.</span></span>

```csharp
string entryPoint = "Tasks.ExampleBackgroundTaskClass";
string taskName   = "Maintenance background task example";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, taskTrigger, exampleCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" };
std::wstring taskName{ L"Maintenance background task example" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, taskTrigger, exampleCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass";
String ^ taskName   = "Maintenance background task example";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, taskTrigger, exampleCondition);
```

> [!NOTE]
> <span data-ttu-id="5e9a0-132">Für alle Gerätefamilien mit Ausnahme von Desktops können Hintergrundaufgaben beendet werden, wenn der Arbeitsspeicher des Geräts knapp wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-132">For all device families except desktop, if the device becomes low on memory, background tasks may be terminated.</span></span> <span data-ttu-id="5e9a0-133">Wenn eine Ausnahme über wenig Arbeitsspeicher nicht angezeigt oder von der App nicht behandelt wird, wird die Hintergrundaufgabe ohne Warnung und ohne Auslösen des OnCanceled-Ereignisses beendet.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-133">If an out of memory exception is not surfaced, or the app does not handle it, then the background task will be terminated without warning and without raising the OnCanceled event.</span></span> <span data-ttu-id="5e9a0-134">Dadurch soll die Benutzerfreundlichkeit der App im Vordergrund sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-134">This helps to ensure the user experience of the app in the foreground.</span></span> <span data-ttu-id="5e9a0-135">Entwerfen Sie die Hintergrundaufgabe so, dass dieses Szenario behandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-135">Your background task should be designed to handle this scenario.</span></span>

> [!NOTE]
> <span data-ttu-id="5e9a0-136">Universelle Windows-Plattform-apps müssen [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor hintergrundtrigger-Typen.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-136">Universal Windows Platform apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="5e9a0-137">Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates der App weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-137">To ensure that your Universal Windows app continues to run properly after you release an update to your app, you must call [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) and then call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) when your app launches after being updated.</span></span> <span data-ttu-id="5e9a0-138">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="5e9a0-138">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5e9a0-139">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-139">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="5e9a0-140">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-140">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="5e9a0-141">Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="5e9a0-141">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5e9a0-142">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5e9a0-142">Related topics</span></span>

* <span data-ttu-id="5e9a0-143">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="5e9a0-143">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="5e9a0-144">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="5e9a0-144">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="5e9a0-145">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="5e9a0-145">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="5e9a0-146">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-146">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="5e9a0-147">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="5e9a0-147">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="5e9a0-148">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-148">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="5e9a0-149">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="5e9a0-149">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="5e9a0-150">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-150">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="5e9a0-151">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-151">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="5e9a0-152">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="5e9a0-152">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* [<span data-ttu-id="5e9a0-153">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="5e9a0-153">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="5e9a0-154">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="5e9a0-154">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="5e9a0-155">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="5e9a0-155">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
