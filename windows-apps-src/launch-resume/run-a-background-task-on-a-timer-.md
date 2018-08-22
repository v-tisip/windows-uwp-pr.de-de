---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe für einen Timer
description: Hier erfahren Sie, wie Sie eine einmalige Hintergrundaufgabe planen oder eine regelmäßige Hintergrundaufgabe ausführen.
ms.assetid: 0B7F0BFF-535A-471E-AC87-783C740A61E9
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrund Aufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 25e3c76ae09ed6835f89f0d98c308f11c7a99624
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "2797448"
---
# <a name="run-a-background-task-on-a-timer"></a><span data-ttu-id="1213d-104">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="1213d-104">Run a background task on a timer</span></span>

<span data-ttu-id="1213d-105">Erfahren Sie, wie die [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) verwenden, um einen einmaligen Hintergrundtask planen, oder führen Sie eine periodische Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="1213d-105">Learn how to use the [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843) to schedule a one-time background task, or run a periodic background task.</span></span>

<span data-ttu-id="1213d-106">Finden Sie unter **Scenario4** im [Hintergrund Aktivierung Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundActivation) sehen Sie ein Beispiel zum Implementieren die Zeit ausgelöste Hintergrund beschrieben in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="1213d-106">See **Scenario4** in the [Background activation sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundActivation) to see an example of how to implement the time triggered background task described in this topic.</span></span>

<span data-ttu-id="1213d-107">In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die in regelmäßigen Abständen oder zu einem bestimmten Zeitpunkt ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1213d-107">This topic assumes that you have a background task that needs to run periodically, or at a specific time.</span></span> <span data-ttu-id="1213d-108">Wenn Sie bereits eine Hintergrundaufgabe ist, ist an vorhanden eine Beispiel Hintergrundaufgabe [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span><span class="sxs-lookup"><span data-stu-id="1213d-108">If you don't already have a background task, there is a sample background task at [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span></span> <span data-ttu-id="1213d-109">Oder führen Sie die Schritte in [Erstellen und Registrieren einer Hintergrundaufgabe in-Process](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](create-and-register-a-background-task.md) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1213d-109">Or, follow the steps in [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) or [Create and register an out-of-process background task](create-and-register-a-background-task.md) to create one.</span></span>

## <a name="create-a-time-trigger"></a><span data-ttu-id="1213d-110">Erstellen eines Zeitauslösers</span><span class="sxs-lookup"><span data-stu-id="1213d-110">Create a time trigger</span></span>

<span data-ttu-id="1213d-111">Erstellen Sie einen neuen Zeitauslöser ([**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843)).</span><span class="sxs-lookup"><span data-stu-id="1213d-111">Create a new [**TimeTrigger**](https://msdn.microsoft.com/library/windows/apps/br224843).</span></span> <span data-ttu-id="1213d-112">Der zweite Parameter (*OneShot*) gibt an, ob die Hintergrundaufgabe einmalig oder regelmäßig ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1213d-112">The second parameter, *OneShot*, specifies whether the background task will run only once or keep running periodically.</span></span> <span data-ttu-id="1213d-113">Wenn *OneShot* auf „true“ festgelegt ist, gibt der erste Parameter (*FreshnessTime*) an, wie lange mit der Planung der Hintergrundaufgabe gewartet werden soll (in Minuten).</span><span class="sxs-lookup"><span data-stu-id="1213d-113">If *OneShot* is set to true, the first parameter (*FreshnessTime*) specifies the number of minutes to wait before scheduling the background task.</span></span> <span data-ttu-id="1213d-114">Wenn *OneShot* auf „false“ festgelegt ist, gibt *FreshnessTime* die Häufigkeit an, mit der die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1213d-114">If *OneShot* is set to false, *FreshnessTime* specifies the frequency at which the background task will run.</span></span>

<span data-ttu-id="1213d-115">Der integrierte Timer für auf Desktop- oder Mobilgeräte ausgerichtete UWP-Apps führt Hintergrundaufgaben in einem 15-Minuten-Intervall aus.</span><span class="sxs-lookup"><span data-stu-id="1213d-115">The built-in timer for Universal Windows Platform (UWP) apps that target the desktop or mobile device family runs background tasks in 15-minute intervals.</span></span> <span data-ttu-id="1213d-116">(Der Timer führt alle 15 Minuten, sodass das System muss nur einmal alle 15 Minuten reaktivieren, um apps reaktivieren, die Power speichert TimerTriggers--angefordert haben.)</span><span class="sxs-lookup"><span data-stu-id="1213d-116">(The timer runs in 15-minute intervals so that the system only needs to wake once every 15 minutes to wake up the apps that have requested TimerTriggers--which saves power.)</span></span>

- <span data-ttu-id="1213d-117">Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.</span><span class="sxs-lookup"><span data-stu-id="1213d-117">If *FreshnessTime* is set to 15 minutes and *OneShot* is true, the task will be scheduled to run once starting between 15 and 30 minutes from the time it is registered.</span></span> <span data-ttu-id="1213d-118">Wenn sie auf 25Minuten und *OneShot* auf „true“ festgelegt ist, wird die Aufgabe einmalig innerhalb der ersten 25 und 40Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.</span><span class="sxs-lookup"><span data-stu-id="1213d-118">If it is set to 25 minutes and *OneShot* is true, the task will be scheduled to run once starting between 25 and 40 minutes from the time it is registered.</span></span>

- <span data-ttu-id="1213d-119">Wenn *FreshnessTime* auf 15Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle 15Minuten innerhalb der ersten 15 und 30Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.</span><span class="sxs-lookup"><span data-stu-id="1213d-119">If *FreshnessTime* is set to 15 minutes and *OneShot* is false, the task will be scheduled to run every 15 minutes starting between 15 and 30 minutes from the time it is registered.</span></span> <span data-ttu-id="1213d-120">Wenn sie auf „n” Minuten und *OneShot* auf „false“ festgelegt ist, wird die Aufgabe alle „n” Minuten innerhalb der ersten „n” und „n+15” Minuten nach dem Registrierungszeitpunkt zur Ausführung eingeplant.</span><span class="sxs-lookup"><span data-stu-id="1213d-120">If it is set to n minutes and *OneShot* is false, the task will be scheduled to run every n minutes starting between n and n + 15 minutes after it is registered.</span></span>

> [!NOTE]
> <span data-ttu-id="1213d-121">Wenn *FreshnessTime* auf weniger als 15 Minuten festgelegt ist, wird eine Ausnahme ausgelöst, wenn Sie versuchen, die Hintergrundaufgabe zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="1213d-121">If *FreshnessTime* is set to less than 15 minutes, an exception is thrown when attempting to register the background task.</span></span>
 
<span data-ttu-id="1213d-122">Angenommen, verursacht diese Trigger einen Hintergrundtask einmal pro Stunde ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1213d-122">For example, this trigger will cause a background task to run once an hour.</span></span>

```cs
TimeTrigger hourlyTrigger = new TimeTrigger(60, false);
```

```cppwinrt
Windows::ApplicationModel::Background::TimeTrigger hourlyTrigger{ 60, false };
```

```cpp
TimeTrigger ^ hourlyTrigger = ref new TimeTrigger(60, false);
```

## <a name="optional-add-a-condition"></a><span data-ttu-id="1213d-123">(Optional) Hinzufügen einer Bedingung</span><span class="sxs-lookup"><span data-stu-id="1213d-123">(Optional) Add a condition</span></span>

<span data-ttu-id="1213d-124">Sie können eine Bedingung Hintergrund Aufgabe Steuerelement erstellen, wenn der Task ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1213d-124">You can create a background task condition to control when the task runs.</span></span> <span data-ttu-id="1213d-125">Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausführt, bis die Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="1213d-125">A condition prevents the background task from running until the condition is met.</span></span> <span data-ttu-id="1213d-126">Weitere Informationen finden Sie unter [Festlegen von Bedingungen für die Ausführung einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="1213d-126">For more information, see [Set conditions for running a background task](set-conditions-for-running-a-background-task.md).</span></span>

<span data-ttu-id="1213d-127">In diesem Beispiel ist die Bedingung auf **UserPresent** festgelegt, damit die ausgelöste Aufgabe nur ausgeführt wird, wenn der Benutzer aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="1213d-127">In this example the condition is set to **UserPresent** so that, once triggered, the task only runs once the user is active.</span></span> <span data-ttu-id="1213d-128">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="1213d-128">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

```cs
SystemCondition userCondition = new SystemCondition(SystemConditionType.UserPresent);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition userCondition{
    Windows::ApplicationModel::Background::SystemConditionType::UserPresent };
```

```cpp
SystemCondition ^ userCondition = ref new SystemCondition(SystemConditionType::UserPresent);
```

<span data-ttu-id="1213d-129">Ausführlichere Informationen auf Bedingungen und Arten von Triggern Hintergrund finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="1213d-129">For more in-depth information on conditions and types of background triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

##  <a name="call-requestaccessasync"></a><span data-ttu-id="1213d-130">Aufrufen von RequestAccessAsync()</span><span class="sxs-lookup"><span data-stu-id="1213d-130">Call RequestAccessAsync()</span></span>

<span data-ttu-id="1213d-131">Rufen Sie vor der Registrierung der Aufgabe **ApplicationTrigger** Hintergrund [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Hintergrundaktivitäten bestimmen, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben, kann ein.</span><span class="sxs-lookup"><span data-stu-id="1213d-131">Before registering the **ApplicationTrigger** background task, call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) to determine the level of background activity the user allows because the user may have disabled background activity for your app.</span></span> <span data-ttu-id="1213d-132">Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.</span><span class="sxs-lookup"><span data-stu-id="1213d-132">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>

```cs
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
    // Depending on the value of requestStatus, provide an appropriate response
    // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a><span data-ttu-id="1213d-133">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-133">Register the background task</span></span>

<span data-ttu-id="1213d-134">Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1213d-134">Register the background task by calling your background task registration function.</span></span> <span data-ttu-id="1213d-135">Weitere Informationen zum Registrieren von Hintergrundaufgaben und sehen Sie die Definition der **RegisterBackgroundTask()** -Methode in der folgenden Beispielcode finden Sie unter [Registrieren eine Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="1213d-135">For more information on registering background tasks, and to see the definition of the **RegisterBackgroundTask()** method in the sample code below, see [Register a background task](register-a-background-task.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1213d-136">Für Hintergrund in demselben Prozess wie Ihre app ausgeführten Aufgaben, stellen Sie keine `entryPoint`.</span><span class="sxs-lookup"><span data-stu-id="1213d-136">For background tasks that run in the same process as your app, do not set `entryPoint`.</span></span> <span data-ttu-id="1213d-137">Legen Sie für Hintergrund, auf denen Ihre app in einem eigenen Prozess ausgeführt Aufgaben, `entryPoint` werden den Namespace '. ", und den Namen der Klasse, die Implementierung Ihrer Hintergrund Aufgabe enthält.</span><span class="sxs-lookup"><span data-stu-id="1213d-137">For background tasks that run in a separate process from your app, set `entryPoint` to be the namespace, '.', and the name of the class that contains your background task implementation.</span></span>

```cs
string entryPoint = "Tasks.ExampleBackgroundTaskClass";
string taskName   = "Example hourly background task";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" };
std::wstring taskName{ L"Example hourly background task" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass";
String ^ taskName   = "Example hourly background task";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, hourlyTrigger, userCondition);
```

<span data-ttu-id="1213d-138">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="1213d-138">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="1213d-139">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="1213d-139">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="1213d-140">Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="1213d-140">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>

## <a name="manage-resources-for-your-background-task"></a><span data-ttu-id="1213d-141">Verwalten von Ressourcen für Ihre Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-141">Manage resources for your background task</span></span>

<span data-ttu-id="1213d-142">Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="1213d-142">Use [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) to determine if the user has decided that your app’s background activity should be limited.</span></span> <span data-ttu-id="1213d-143">Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="1213d-143">Be aware of your battery usage and only run in the background when it is necessary to complete an action that the user wants.</span></span> <span data-ttu-id="1213d-144">Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.</span><span class="sxs-lookup"><span data-stu-id="1213d-144">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>

- <span data-ttu-id="1213d-145">Arbeitsspeicher: Zur Optimierung Ihrer app Arbeitsspeicher und weniger Energie Verwendung ist Grundvoraussetzung, dass das Betriebssystem Hintergrundtask ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1213d-145">Memory: Tuning your app's memory and energy use is key to ensuring that the operating system will allow your background task to run.</span></span> <span data-ttu-id="1213d-146">Verwenden Sie die [APIs für die Verwaltung von Arbeitsspeicher](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) , um wie viel Arbeitsspeicher finden Sie unter Ihrer Hintergrundaufgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1213d-146">Use the [Memory Management APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) to see how much memory your background task is using.</span></span> <span data-ttu-id="1213d-147">Mehr Arbeitsspeicher Ihrer Hintergrundaufgabe verwendet, desto mehr ist für das Betriebssystem aktiviert bleiben bei einer anderen Anwendung im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="1213d-147">The more memory your background task uses, the harder it is for the OS to keep it running when another app is in the foreground.</span></span> <span data-ttu-id="1213d-148">Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.</span><span class="sxs-lookup"><span data-stu-id="1213d-148">The user is ultimately in control of all background activity that your app can perform and has visibility on the impact your app has on battery use.</span></span>  
- <span data-ttu-id="1213d-149">CPU-Zeit: Hintergrundaufgaben werden durch die Zeitspanne Wand Uhr Usage erhalten sie Triggertyp Basis begrenzt.</span><span class="sxs-lookup"><span data-stu-id="1213d-149">CPU time: Background tasks are limited by the amount of wall-clock usage time they get based on trigger type.</span></span>

<span data-ttu-id="1213d-150">Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="1213d-150">See [Support your app with background tasks](support-your-app-with-background-tasks.md) for the resource constraints applied to background tasks.</span></span>

## <a name="remarks"></a><span data-ttu-id="1213d-151">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1213d-151">Remarks</span></span>

<span data-ttu-id="1213d-152">Beginnend mit Windows 10, ist es nicht mehr erforderlich für den Benutzer Ihre app auf dem Sperrbildschirm hinzufügen, um Hintergrundaufgaben nutzen.</span><span class="sxs-lookup"><span data-stu-id="1213d-152">Starting with Windows 10, it is no longer necessary for the user to add your app to the lock screen in order to utilize background tasks.</span></span>

<span data-ttu-id="1213d-153">Hintergrund läuft nur unter Verwendung einer **TimeTrigger** , wenn Sie zuerst [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="1213d-153">A background task will only run using a **TimeTrigger** if you have called [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) first.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1213d-154">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1213d-154">Related topics</span></span>

* [<span data-ttu-id="1213d-155">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="1213d-155">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="1213d-156">Hintergrund Task-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1213d-156">Background task code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* [<span data-ttu-id="1213d-157">Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen</span><span class="sxs-lookup"><span data-stu-id="1213d-157">Create and register an in-process background task</span></span>](create-and-register-an-inproc-background-task.md)
* [<span data-ttu-id="1213d-158">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="1213d-158">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="1213d-159">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-159">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="1213d-160">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="1213d-160">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="1213d-161">Geben Sie Speicher frei, wenn Ihre App in den Hintergrund verschoben wird</span><span class="sxs-lookup"><span data-stu-id="1213d-161">Free memory when your app moves to the background</span></span>](reduce-memory-usage.md)
* [<span data-ttu-id="1213d-162">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-162">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="1213d-163">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="1213d-163">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
* [<span data-ttu-id="1213d-164">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="1213d-164">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="1213d-165">Verschieben der angehaltenen App mithilfe der erweiterten Ausführung</span><span class="sxs-lookup"><span data-stu-id="1213d-165">Postpone app suspension with extended execution</span></span>](run-minimized-with-extended-execution.md)
* [<span data-ttu-id="1213d-166">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-166">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="1213d-167">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="1213d-167">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="1213d-168">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-168">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="1213d-169">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="1213d-169">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="1213d-170">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="1213d-170">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
