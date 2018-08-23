---
author: TylerMSFT
title: Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe
description: Erfahren Sie, wie Bedingungen festgelegt werden, die steuern, wann die Hintergrundaufgabe ausgeführt wird.
ms.assetid: 10ABAC9F-AA8C-41AC-A29D-871CD9AD9471
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrund Aufgabe
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 556a787eb1e92e4c8adb7457235afb45c02df2dc
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2813782"
---
# <a name="set-conditions-for-running-a-background-task"></a><span data-ttu-id="59187-104">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-104">Set conditions for running a background task</span></span>

**<span data-ttu-id="59187-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="59187-105">Important APIs</span></span>**

- [**<span data-ttu-id="59187-106">SystemCondition</span><span class="sxs-lookup"><span data-stu-id="59187-106">SystemCondition</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224834)
- [**<span data-ttu-id="59187-107">SystemConditionType</span><span class="sxs-lookup"><span data-stu-id="59187-107">SystemConditionType</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224835)
- [**<span data-ttu-id="59187-108">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="59187-108">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)

<span data-ttu-id="59187-109">Erfahren Sie, wie Bedingungen festgelegt werden, die steuern, wann die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59187-109">Learn how to set conditions that control when your background task will run.</span></span>

<span data-ttu-id="59187-110">In manchen Fällen erfordern Hintergrundaufgaben bestimmte Zustände, die für den Hintergrund Vorgang erfolgreich eingehalten werden.</span><span class="sxs-lookup"><span data-stu-id="59187-110">Sometimes, background tasks require certain conditions to be met for the background task to succeed.</span></span> <span data-ttu-id="59187-111">Wenn Sie Ihre Hintergrundaufgabe registrieren, können Sie mit [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) eine oder mehrere Bedingungen angeben.</span><span class="sxs-lookup"><span data-stu-id="59187-111">You can specify one or more of the conditions specified by [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) when registering your background task.</span></span> <span data-ttu-id="59187-112">Nach der Trigger ausgelöst wurde, wird die Bedingung überprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="59187-112">The condition will be checked after the trigger has been fired.</span></span> <span data-ttu-id="59187-113">Klicken Sie dann die Hintergrundaufgabe Warteschlange abgelegt werden, aber es wird nicht ausgeführt, bis alle erforderlichen Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="59187-113">The background task will then be queued, but it will not run until all the required conditions are satisfied.</span></span>

<span data-ttu-id="59187-114">Bedingungen auf Hintergrundaufgaben an speichert Akkulaufzeit und CPU indem verhindert, dass Aufgaben unnötig ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59187-114">Putting conditions on background tasks saves battery life and CPU by preventing tasks from running unnecessarily.</span></span> <span data-ttu-id="59187-115">Wenn Ihre Hintergrundaufgabe z. B. nach einem Timer ausgeführt wird und eine Internetverbindung benötigt, fügen Sie die **InternetAvailable**-Bedingung zum [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) hinzu, bevor Sie die Aufgabe registrieren.</span><span class="sxs-lookup"><span data-stu-id="59187-115">For example, if your background task runs on a timer and requires Internet connectivity, add the **InternetAvailable** condition to the [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) before registering the task.</span></span> <span data-ttu-id="59187-116">So wird verhindert, dass die Aufgabe unnötig Systemressourcen nutzt und Akkulaufzeit beansprucht, da nur die Hintergrundaufgabe ausgeführt wird, wenn der Timer abgelaufen *und* das Internet verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="59187-116">This will help prevent the task from using system resources and battery life unnecessarily by only running the background task when the timer has elapsed *and* the Internet is available.</span></span>

<span data-ttu-id="59187-117">Es ist auch möglich, mehrere Bedingungen durch Aufrufen von **AddCondition** mehrmals für den gleichen [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)kombinieren.</span><span class="sxs-lookup"><span data-stu-id="59187-117">It is also possible to combine multiple conditions by calling **AddCondition** multiple times on the same [**TaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768).</span></span> <span data-ttu-id="59187-118">Achten Sie darauf, keine in Konflikt stehenden Bedingungen wie **UserPresent** und **UserNotPresent** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="59187-118">Take care not to add conflicting conditions, such as **UserPresent** and **UserNotPresent**.</span></span>

## <a name="create-a-systemcondition-object"></a><span data-ttu-id="59187-119">Erstellen eines SystemCondition-Objekts</span><span class="sxs-lookup"><span data-stu-id="59187-119">Create a SystemCondition object</span></span>

<span data-ttu-id="59187-120">Dieses Thema setzt voraus, dass Sie Ihrer App bereits eine Hintergrundaufgabe zugeordnet haben und dass Ihre App Code enthält, der ein [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt namens **taskBuilder** erstellt.</span><span class="sxs-lookup"><span data-stu-id="59187-120">This topic assumes that you have a background task already associated with your app, and that your app already includes code that creates a [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) object named **taskBuilder**.</span></span>  <span data-ttu-id="59187-121">Wenn Sie zuerst eine Hintergrundaufgabe erstellen müssen, lesen Sie [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="59187-121">See [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) or [Create and register an out-of-process background task](create-and-register-a-background-task.md) if you need to create a background task first.</span></span>

<span data-ttu-id="59187-122">Dieses Thema gilt für Hintergrundaufgaben, die in einem Prozess außerhalb von Prozessen ausgeführt werden, sowie für solche, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="59187-122">This topic applies to background tasks that run out-of-process as well as those that run in the same process as the foreground app.</span></span>

<span data-ttu-id="59187-123">Erstellen Sie bevor Sie die Bedingung hinzufügen ein [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) -Objekt, um die Bedingung darstellen, die in Kraft für einen Vorgang Hintergrund ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="59187-123">Before adding the condition, create a [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) object to represent the condition that must be in effect for a background task to run.</span></span> <span data-ttu-id="59187-124">Geben Sie in den Konstruktor die Bedingung, die mit einer [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) -Enumerationswert erfüllt sein muss.</span><span class="sxs-lookup"><span data-stu-id="59187-124">In the constructor, specify the condition that must be met with a [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) enumeration value.</span></span>

<span data-ttu-id="59187-125">Der folgende Code erstellt ein [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) -Objekt, das die Bedingung **InternetAvailable** angibt:</span><span class="sxs-lookup"><span data-stu-id="59187-125">The following code creates a [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) object that specifies the **InternetAvailable** condition:</span></span>

```csharp
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };
```

```cpp
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable);
```

## <a name="add-the-systemcondition-object-to-your-background-task"></a><span data-ttu-id="59187-126">Hinzufügen des SystemCondition-Objekts zur Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-126">Add the SystemCondition object to your background task</span></span>

<span data-ttu-id="59187-127">Um die Bedingung hinzuzufügen, rufen Sie die [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769)-Methode für das [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt auf, und übergeben Sie das [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834)-Objekt an die Methode.</span><span class="sxs-lookup"><span data-stu-id="59187-127">To add the condition, call the [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769) method on the [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) object, and pass it the [**SystemCondition**](https://msdn.microsoft.com/library/windows/apps/br224834) object.</span></span>

<span data-ttu-id="59187-128">Der folgende Code verwendet **TaskBuilder** , um die Bedingung **InternetAvailable** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="59187-128">The following code uses **taskBuilder** to add the **InternetAvailable** condition.</span></span>

```csharp
taskBuilder.AddCondition(internetCondition);
```

```cppwinrt
taskBuilder.AddCondition(internetCondition);
```

```cpp
taskBuilder->AddCondition(internetCondition);
```

## <a name="register-your-background-task"></a><span data-ttu-id="59187-129">Registrieren Sie die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="59187-129">Register your background task</span></span>

<span data-ttu-id="59187-130">Sie können nun Ihre Hintergrundaufgabe registrieren, mit der [**Registrieren**](https://msdn.microsoft.com/library/windows/apps/br224772) -Methode und der Hintergrundtask wird nicht gestartet werden, bis die angegebene Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="59187-130">Now you can register your background task with the [**Register**](https://msdn.microsoft.com/library/windows/apps/br224772) method, and the background task will not start until the specified condition is met.</span></span>

<span data-ttu-id="59187-131">Der folgende Code registriert die Aufgabe und speichert das resultierende BackgroundTaskRegistration-Objekt:</span><span class="sxs-lookup"><span data-stu-id="59187-131">The following code registers the task and stores the resulting BackgroundTaskRegistration object:</span></span>

```csharp
BackgroundTaskRegistration task = taskBuilder.Register();
```

```cppwinrt
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ recurringTaskBuilder.Register() };
```

```cpp
BackgroundTaskRegistration ^ task = taskBuilder->Register();
```

> [!NOTE]
> <span data-ttu-id="59187-132">Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrund-Triggertypen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="59187-132">Universal Windows apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="59187-133">Rufen Sie [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) und anschließend [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) auf, wenn die App nach der Aktualisierung gestartet wird, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59187-133">To ensure that your Universal Windows app continues to run properly after you release an update, you must call [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471) and then call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) when your app launches after being updated.</span></span> <span data-ttu-id="59187-134">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="59187-134">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59187-135">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="59187-135">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="59187-136">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="59187-136">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="59187-137">Stellen Sie sicher, dass Ihre App Szenarien, in denen die Registrierung von Hintergrundaufgaben einen Fehler verursacht, problemlos verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="59187-137">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>

## <a name="place-multiple-conditions-on-your-background-task"></a><span data-ttu-id="59187-138">Einfügen mehrerer Bedingungen für die Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-138">Place multiple conditions on your background task</span></span>

<span data-ttu-id="59187-139">Zum Hinzufügen mehrerer Bedingungen ruft Ihre App die [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769) -Methode mehrmals auf.</span><span class="sxs-lookup"><span data-stu-id="59187-139">To add multiple conditions, your app makes multiple calls to the [**AddCondition**](https://msdn.microsoft.com/library/windows/apps/br224769) method.</span></span> <span data-ttu-id="59187-140">Diese Aufrufe müssen stattfinden, bevor die Aufgabenregistrierung wirksam wird.</span><span class="sxs-lookup"><span data-stu-id="59187-140">These calls must come before task registration to be effective.</span></span>

> [!NOTE]
> <span data-ttu-id="59187-141">Achten Sie darauf, einer Hintergrundaufgabe keine in Konflikt stehenden Bedingungen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="59187-141">Take care not to add conflicting conditions to a background task.</span></span>

<span data-ttu-id="59187-142">Der folgende Codeausschnitt zeigt mehrere Bedingungen im Kontext von erstellen und Registrieren einer Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="59187-142">The following snippet shows multiple conditions in the context of creating and registering a background task.</span></span>

```csharp
// Set up the background task.
TimeTrigger hourlyTrigger = new TimeTrigger(60, false);

var recurringTaskBuilder = new BackgroundTaskBuilder();

recurringTaskBuilder.Name           = "Hourly background task";
recurringTaskBuilder.TaskEntryPoint = "Tasks.ExampleBackgroundTaskClass";
recurringTaskBuilder.SetTrigger(hourlyTrigger);

// Begin adding conditions.
SystemCondition userCondition     = new SystemCondition(SystemConditionType.UserPresent);
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);

recurringTaskBuilder.AddCondition(userCondition);
recurringTaskBuilder.AddCondition(internetCondition);

// Done adding conditions, now register the background task.

BackgroundTaskRegistration task = recurringTaskBuilder.Register();
```

```cppwinrt
// Set up the background task.
Windows::ApplicationModel::Background::TimeTrigger hourlyTrigger{ 60, false };

Windows::ApplicationModel::Background::BackgroundTaskBuilder recurringTaskBuilder;

recurringTaskBuilder.Name(L"Hourly background task");
recurringTaskBuilder.TaskEntryPoint(L"Tasks.ExampleBackgroundTaskClass");
recurringTaskBuilder.SetTrigger(hourlyTrigger);

// Begin adding conditions.
Windows::ApplicationModel::Background::SystemCondition userCondition{
    Windows::ApplicationModel::Background::SystemConditionType::UserPresent };
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };

recurringTaskBuilder.AddCondition(userCondition);
recurringTaskBuilder.AddCondition(internetCondition);

// Done adding conditions, now register the background task.
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ recurringTaskBuilder.Register() };
```

```cpp
// Set up the background task.
TimeTrigger ^ hourlyTrigger = ref new TimeTrigger(60, false);

auto recurringTaskBuilder = ref new BackgroundTaskBuilder();

recurringTaskBuilder->Name           = "Hourly background task";
recurringTaskBuilder->TaskEntryPoint = "Tasks.ExampleBackgroundTaskClass";
recurringTaskBuilder->SetTrigger(hourlyTrigger);

// Begin adding conditions.
SystemCondition ^ userCondition     = ref new SystemCondition(SystemConditionType::UserPresent);
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable);

recurringTaskBuilder->AddCondition(userCondition);
recurringTaskBuilder->AddCondition(internetCondition);

// Done adding conditions, now register the background task.
BackgroundTaskRegistration ^ task = recurringTaskBuilder->Register();
```

## <a name="remarks"></a><span data-ttu-id="59187-143">Hinweise</span><span class="sxs-lookup"><span data-stu-id="59187-143">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="59187-144">Wählen Sie die Bedingungen für Ihre Hintergrundaufgabe, sodass er nur ausgeführt wird, wenn es erforderlich ist, und wird nicht ausgeführt, wenn es sollte nicht.</span><span class="sxs-lookup"><span data-stu-id="59187-144">Choose conditions for your background task so that it only runs when it's needed, and doesn't run when it shouldn't.</span></span> <span data-ttu-id="59187-145">Unter [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) finden Sie Beschreibungen der verschiedenen Bedingungen für Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="59187-145">See [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835) for descriptions of the different background task conditions.</span></span>

## <a name="related-topics"></a><span data-ttu-id="59187-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="59187-146">Related topics</span></span>

* [<span data-ttu-id="59187-147">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="59187-147">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="59187-148">Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="59187-148">Create and register an in-process background task</span></span>](create-and-register-an-inproc-background-task.md)
* [<span data-ttu-id="59187-149">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="59187-149">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="59187-150">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-150">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="59187-151">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="59187-151">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="59187-152">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-152">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="59187-153">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="59187-153">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="59187-154">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-154">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="59187-155">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="59187-155">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="59187-156">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="59187-156">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* [<span data-ttu-id="59187-157">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="59187-157">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="59187-158">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="59187-158">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="59187-159">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="59187-159">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
