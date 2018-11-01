---
author: TylerMSFT
title: Auslösen einer Hintergrundaufgabe in Ihrer App
description: Beschreibt, wie Sie eine Hintergrundaufgabe innerhalb einer Anwendung auslösen
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
keywords: Trigger Hintergrundaufgabe, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 6846cfe77272a78eff7ddc05c9a7e48dddd21fc2
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5874366"
---
# <a name="trigger-a-background-task-from-within-your-app"></a><span data-ttu-id="dfe23-104">Auslösen einer Hintergrundaufgabe in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="dfe23-104">Trigger a background task from within your app</span></span>

<span data-ttu-id="dfe23-105">Hier erfahren Sie, wie Sie den [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) zum Aktivieren einer Hintergrundaufgabe in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="dfe23-105">Learn how to use the [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) to activate a background task from within your app.</span></span>

<span data-ttu-id="dfe23-106">Ein Beispiel für So erstellen Sie einen Anwendungs-Trigger finden Sie in diesem [Beispiel](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="dfe23-106">For an example of how to create an Application trigger, see this [example](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).</span></span>

<span data-ttu-id="dfe23-107">In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die Sie von Ihrer Anwendung aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="dfe23-107">This topic assumes that you have a background task that you want to activate from your application.</span></span> <span data-ttu-id="dfe23-108">Wenn Sie bereits über eine Hintergrundaufgabe besitzen, wird eine Hintergrundaufgabe Beispiel am [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span><span class="sxs-lookup"><span data-stu-id="dfe23-108">If you don't already have a background task, there is a sample background task at [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span></span> <span data-ttu-id="dfe23-109">Oder führen Sie die Schritte in [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](create-and-register-a-background-task.md) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-109">Or, follow the steps in [Create and register an out-of-process background task](create-and-register-a-background-task.md) to create one.</span></span>

## <a name="why-use-an-application-trigger"></a><span data-ttu-id="dfe23-110">Gründe für die Verwendung eines Anwendung Triggers</span><span class="sxs-lookup"><span data-stu-id="dfe23-110">Why use an application trigger</span></span>

<span data-ttu-id="dfe23-111">Verwenden Sie eine **ApplicationTrigger** , Code in einem separaten Prozess von der Vordergrund-app auszuführen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-111">Use an **ApplicationTrigger** to run code in a separate process from the foreground app.</span></span> <span data-ttu-id="dfe23-112">Ein **ApplicationTrigger** ist geeignet, wenn Ihre app Arbeit, die im Hintergrund – ausgeführt werden soll verfügt, auch wenn der Benutzer die Vordergrund-app schließt.</span><span class="sxs-lookup"><span data-stu-id="dfe23-112">An **ApplicationTrigger** is appropriate if your app has work that needs to be done in the background--even if the user closes the foreground app.</span></span> <span data-ttu-id="dfe23-113">Wenn Hintergrundarbeiten anhalten sollten bei die app geschlossen wird oder wenn sollte in den Zustand des Prozesses Vordergrund gebunden werden, und klicken Sie dann [Extended Execution](run-minimized-with-extended-execution.md) soll, stattdessen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dfe23-113">If background work should halt when the app is closed, or should be tied to the state of the foreground process, then [Extended Execution](run-minimized-with-extended-execution.md) should be used, instead.</span></span>

## <a name="create-an-application-trigger"></a><span data-ttu-id="dfe23-114">Erstellen Sie einen Anwendungs-trigger</span><span class="sxs-lookup"><span data-stu-id="dfe23-114">Create an application trigger</span></span>

<span data-ttu-id="dfe23-115">Erstellen Sie eine neue [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger).</span><span class="sxs-lookup"><span data-stu-id="dfe23-115">Create a new [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger).</span></span> <span data-ttu-id="dfe23-116">Es könnte in einem Feld gespeichert werden, wie im folgenden Codeausschnitt abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="dfe23-116">You could store it in a field as is done in the snippet below.</span></span> <span data-ttu-id="dfe23-117">Dies ist aus praktischen Gründen, damit wir nicht später eine neue Instanz zu erstellen, wenn wir den Trigger signalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="dfe23-117">This is for convenience so that we don't have to create a new instance later when we want to signal the trigger.</span></span> <span data-ttu-id="dfe23-118">Aber Sie können jede Instanz **ApplicationTrigger** verwenden, um den Trigger zu signalisieren.</span><span class="sxs-lookup"><span data-stu-id="dfe23-118">But you can use any **ApplicationTrigger** instance to signal the trigger.</span></span>

```csharp
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
_AppTrigger = new ApplicationTrigger();
```

```cppwinrt
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
Windows::ApplicationModel::Background::ApplicationTrigger _AppTrigger;
```

```cpp
// _AppTrigger is an ApplicationTrigger field defined at a scope that will keep it alive
// as long as you need to trigger the background task.
// Or, you could create a new ApplicationTrigger instance and use that when you want to
// trigger the background task.
ApplicationTrigger ^ _AppTrigger = ref new ApplicationTrigger();
```

## <a name="optional-add-a-condition"></a><span data-ttu-id="dfe23-119">(Optional) Hinzufügen einer Bedingung</span><span class="sxs-lookup"><span data-stu-id="dfe23-119">(Optional) Add a condition</span></span>

<span data-ttu-id="dfe23-120">Sie können eine Bedingung für Hintergrundaufgaben Steuerelement erstellen, wenn die Aufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="dfe23-120">You can create a background task condition to control when the task runs.</span></span> <span data-ttu-id="dfe23-121">Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausgeführt wird, bis die Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="dfe23-121">A condition prevents the background task from running until the condition is met.</span></span> <span data-ttu-id="dfe23-122">Weitere Informationen finden Sie unter [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="dfe23-122">For more information, see [Set conditions for running a background task](set-conditions-for-running-a-background-task.md).</span></span>

<span data-ttu-id="dfe23-123">In diesem Beispiel wird die Bedingung auf **InternetAvailable** festgelegt ist, damit die ausgelöste, wird die Aufgabe nur ausgeführt, nachdem Zugriff auf das Internet verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="dfe23-123">In this example the condition is set to **InternetAvailable** so that, once triggered, the task only runs once internet access is available.</span></span> <span data-ttu-id="dfe23-124">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="dfe23-124">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

```csharp
SystemCondition internetCondition = new SystemCondition(SystemConditionType.InternetAvailable);
```

```cppwinrt
Windows::ApplicationModel::Background::SystemCondition internetCondition{
    Windows::ApplicationModel::Background::SystemConditionType::InternetAvailable };
```

```cpp
SystemCondition ^ internetCondition = ref new SystemCondition(SystemConditionType::InternetAvailable)
```

<span data-ttu-id="dfe23-125">Ausführlichere Informationen zu Bedingungen und Hintergrund Triggertypen finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="dfe23-125">For more in-depth information on conditions and types of background triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

##  <a name="call-requestaccessasync"></a><span data-ttu-id="dfe23-126">Aufrufen von RequestAccessAsync()</span><span class="sxs-lookup"><span data-stu-id="dfe23-126">Call RequestAccessAsync()</span></span>

<span data-ttu-id="dfe23-127">Rufen Sie vor der Registrierung der Hintergrundaufgabe **ApplicationTrigger** [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Ebene der Hintergrundaktivität zu ermitteln, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben kann.</span><span class="sxs-lookup"><span data-stu-id="dfe23-127">Before registering the **ApplicationTrigger** background task, call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) to determine the level of background activity the user allows because the user may have disabled background activity for your app.</span></span> <span data-ttu-id="dfe23-128">Sehen Sie, dass die Einstellungen für Hintergrundaktivitäten [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer gesteuert werden können.</span><span class="sxs-lookup"><span data-stu-id="dfe23-128">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>

```csharp
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
   // Depending on the value of requestStatus, provide an appropriate response
   // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a><span data-ttu-id="dfe23-129">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-129">Register the background task</span></span>

<span data-ttu-id="dfe23-130">Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-130">Register the background task by calling your background task registration function.</span></span> <span data-ttu-id="dfe23-131">Weitere Informationen zum Registrieren von Hintergrundaufgaben und die Definition der **RegisterBackgroundTask()** -Methode in der nachfolgende Beispielcode anzuzeigen finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="dfe23-131">For more information on registering background tasks, and to see the definition of the **RegisterBackgroundTask()** method in the sample code below, see [Register a background task](register-a-background-task.md).</span></span>

<span data-ttu-id="dfe23-132">Wenn Sie erwägen, verwenden eine Anwendung Trigger, um die Lebensdauer der Vordergrund-Prozess zu erweitern, sollten Sie stattdessen die Verwendung [Extended Execution](run-minimized-with-extended-execution.md) .</span><span class="sxs-lookup"><span data-stu-id="dfe23-132">If you are considering using an Application Trigger to extend the lifetime of your foreground process, consider using [Extended Execution](run-minimized-with-extended-execution.md) instead.</span></span> <span data-ttu-id="dfe23-133">Die Anwendungs-Trigger dient zum Erstellen eines separat gehosteten Prozess Aufgaben in.</span><span class="sxs-lookup"><span data-stu-id="dfe23-133">The Application Trigger is designed for creating a separately hosted process to do work in.</span></span> <span data-ttu-id="dfe23-134">Im folgenden Codeausschnitt wird einen Out-of-Process-Hintergrund-Trigger registriert.</span><span class="sxs-lookup"><span data-stu-id="dfe23-134">The following code snippet registers an out-of-process background trigger.</span></span>

```csharp
string entryPoint = "Tasks.ExampleBackgroundTaskClass";
string taskName   = "Example application trigger";

BackgroundTaskRegistration task = RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition);
```

```cppwinrt
std::wstring entryPoint{ L"Tasks.ExampleBackgroundTaskClass" };
std::wstring taskName{ L"Example application trigger" };

Windows::ApplicationModel::Background::BackgroundTaskRegistration task{
    RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition) };
```

```cpp
String ^ entryPoint = "Tasks.ExampleBackgroundTaskClass";
String ^ taskName   = "Example application trigger";

BackgroundTaskRegistration ^ task = RegisterBackgroundTask(entryPoint, taskName, appTrigger, internetCondition);
```

<span data-ttu-id="dfe23-135">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="dfe23-135">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="dfe23-136">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dfe23-136">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="dfe23-137">Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="dfe23-137">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>

## <a name="trigger-the-background-task"></a><span data-ttu-id="dfe23-138">Auslösen der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-138">Trigger the background task</span></span>

<span data-ttu-id="dfe23-139">Bevor Sie die Hintergrundaufgabe auslösen, verwenden Sie [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) , um sicherzustellen, dass die Hintergrundaufgabe registriert wird.</span><span class="sxs-lookup"><span data-stu-id="dfe23-139">Before you trigger the background task, use [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) to verify that the background task is registered.</span></span> <span data-ttu-id="dfe23-140">Stellen Sie sicher, dass alle Ihre Hintergrundaufgaben registriert sind ein guter Zeitpunkt ist während der Start der app.</span><span class="sxs-lookup"><span data-stu-id="dfe23-140">A good time to verify that all of your background tasks are registered is during app launch.</span></span>

<span data-ttu-id="dfe23-141">Auslösen der Hintergrundaufgabe durch Aufrufen von [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger).</span><span class="sxs-lookup"><span data-stu-id="dfe23-141">Trigger the background task by calling [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger).</span></span> <span data-ttu-id="dfe23-142">Jede Instanz **ApplicationTrigger** erledigt.</span><span class="sxs-lookup"><span data-stu-id="dfe23-142">Any **ApplicationTrigger** instance will do.</span></span>

<span data-ttu-id="dfe23-143">Beachten Sie, dass **ApplicationTrigger.RequestAsync** aufgerufen werden kann, von der Hintergrundaufgabe selbst, oder wenn die app im Hintergrund Zustand ausgeführt wird (siehe [App-Lebenszyklus](app-lifecycle.md) Weitere Informationen zur Anwendungszustände).</span><span class="sxs-lookup"><span data-stu-id="dfe23-143">Note that **ApplicationTrigger.RequestAsync** can't be called from the background task itself, or when the app is in the background running state (see [App lifecycle](app-lifecycle.md) for more information about application states).</span></span>
<span data-ttu-id="dfe23-144">Es kann [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) zurückgeben, wenn der Benutzer Energie oder Datenschutz-Richtlinien festgelegt hat, die verhindern, dass die app Hintergrundaktivitäten durchführen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-144">It may return [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) if the user has set energy or privacy policies that prevent the app from performing background activity.</span></span>
<span data-ttu-id="dfe23-145">Darüber hinaus kann nur ein AppTrigger zu einem Zeitpunkt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="dfe23-145">Also, only one AppTrigger can run at a time.</span></span> <span data-ttu-id="dfe23-146">Wenn Sie versuchen, eine AppTrigger ausgeführt werden, während ein anderes bereits ausgeführt wird, wird die Funktion [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult)zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="dfe23-146">If you attempt to run an AppTrigger while another is already running, the function will return [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult).</span></span>

```csharp
var result = await _AppTrigger.RequestAsync();
```

## <a name="manage-resources-for-your-background-task"></a><span data-ttu-id="dfe23-147">Verwalten von Ressourcen für die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="dfe23-147">Manage resources for your background task</span></span>

<span data-ttu-id="dfe23-148">Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="dfe23-148">Use [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) to determine if the user has decided that your app’s background activity should be limited.</span></span> <span data-ttu-id="dfe23-149">Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="dfe23-149">Be aware of your battery usage and only run in the background when it is necessary to complete an action that the user wants.</span></span> <span data-ttu-id="dfe23-150">Sehen Sie, dass die Einstellungen für Hintergrundaktivitäten [Optimieren von Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen über die Möglichkeiten Benutzer gesteuert werden können.</span><span class="sxs-lookup"><span data-stu-id="dfe23-150">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>  

- <span data-ttu-id="dfe23-151">Arbeitsspeicher: Optimieren Ihrer app Arbeitsspeicher und Energieverbrauch ist Schlüssel, um sicherzustellen, dass das Betriebssystem die Hintergrundaufgabe ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="dfe23-151">Memory: Tuning your app's memory and energy use is key to ensuring that the operating system will allow your background task to run.</span></span> <span data-ttu-id="dfe23-152">Verwenden Sie die [Speicherverwaltungs-APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) zu ermitteln, wie viel Arbeitsspeicher Ihre Hintergrundaufgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="dfe23-152">Use the [Memory Management APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) to see how much memory your background task is using.</span></span> <span data-ttu-id="dfe23-153">Je mehr Arbeitsspeicher Ihre Hintergrundaufgabe verwendet, desto schwieriger wird es für das Betriebssystem, weiter ausgeführt, wenn eine andere app im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="dfe23-153">The more memory your background task uses, the harder it is for the OS to keep it running when another app is in the foreground.</span></span> <span data-ttu-id="dfe23-154">Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-154">The user is ultimately in control of all background activity that your app can perform and has visibility on the impact your app has on battery use.</span></span>  
- <span data-ttu-id="dfe23-155">CPU-Zeit: Hintergrundaufgaben sind durch die gesamtbetrachtungszeit-Nutzung Zeit sie auf Triggertyp basierend erhalten eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="dfe23-155">CPU time: Background tasks are limited by the amount of wall-clock usage time they get based on trigger type.</span></span> <span data-ttu-id="dfe23-156">Durch die Anwendungs-Trigger ausgelöste Hintergrundaufgaben sind auf etwa 10 Minuten beschränkt.</span><span class="sxs-lookup"><span data-stu-id="dfe23-156">Background tasks triggered by the Application trigger are limited to about 10 minutes.</span></span>

<span data-ttu-id="dfe23-157">Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="dfe23-157">See [Support your app with background tasks](support-your-app-with-background-tasks.md) for the resource constraints applied to background tasks.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfe23-158">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dfe23-158">Remarks</span></span>

<span data-ttu-id="dfe23-159">Ab Windows 10, ist es nicht mehr erforderlich ist, damit der Benutzer Ihre app zum Sperrbildschirm hinzufügen, um Hintergrundaufgaben zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="dfe23-159">Starting with Windows10, it is no longer necessary for the user to add your app to the lock screen in order to utilize background tasks.</span></span>

<span data-ttu-id="dfe23-160">Eine Hintergrundaufgabe läuft nur eine **ApplicationTrigger** verwenden, wenn Sie vorher [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="dfe23-160">A background task will only run using an **ApplicationTrigger** if you have called [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) first.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dfe23-161">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="dfe23-161">Related topics</span></span>

* [<span data-ttu-id="dfe23-162">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="dfe23-162">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="dfe23-163">Beispiel für eine Hintergrundaufgabe code</span><span class="sxs-lookup"><span data-stu-id="dfe23-163">Background task code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* <span data-ttu-id="dfe23-164">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="dfe23-164">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="dfe23-165">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="dfe23-165">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="dfe23-166">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-166">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="dfe23-167">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="dfe23-167">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="dfe23-168">Freigeben von Speicher, wenn die App in den Hintergrund verschoben wird</span><span class="sxs-lookup"><span data-stu-id="dfe23-168">Free memory when your app moves to the background</span></span>](reduce-memory-usage.md)
* [<span data-ttu-id="dfe23-169">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-169">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="dfe23-170">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="dfe23-170">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
* [<span data-ttu-id="dfe23-171">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="dfe23-171">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="dfe23-172">Verschieben des Anhaltens der App mithilfe der erweiterten Ausführung</span><span class="sxs-lookup"><span data-stu-id="dfe23-172">Postpone app suspension with extended execution</span></span>](run-minimized-with-extended-execution.md)
* [<span data-ttu-id="dfe23-173">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-173">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="dfe23-174">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="dfe23-174">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="dfe23-175">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-175">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="dfe23-176">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="dfe23-176">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="dfe23-177">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="dfe23-177">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
