---
author: TylerMSFT
title: Auslösen einer Hintergrundaufgabe in Ihrer App
description: Beschreibt das Auslösen der Hintergrundaufgabe von innerhalb einer Anwendung
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Hintergrund Aufgabe Trigger, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 5ccd171f53795ef71830ffb022d0468facb3ac4f
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2882748"
---
# <a name="trigger-a-background-task-from-within-your-app"></a><span data-ttu-id="0cae8-104">Auslösen einer Hintergrundaufgabe in Ihrer App</span><span class="sxs-lookup"><span data-stu-id="0cae8-104">Trigger a background task from within your app</span></span>

<span data-ttu-id="0cae8-105">Hier erfahren Sie, wie Sie den [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) zum Aktivieren einer Hintergrundaufgabe in Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="0cae8-105">Learn how to use the [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger) to activate a background task from within your app.</span></span>

<span data-ttu-id="0cae8-106">Ein Beispiel dafür, wie Sie zum Erstellen eines Anwendung Triggers finden in diesem [Beispiel](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="0cae8-106">For an example of how to create an Application trigger, see this [example](https://github.com/Microsoft/Windows-universal-samples/blob/v2.0.0/Samples/BackgroundTask/cs/BackgroundTask/Scenario5_ApplicationTriggerTask.xaml.cs).</span></span>

<span data-ttu-id="0cae8-107">In diesem Thema wird davon ausgegangen, dass Sie eine Hintergrundaufgabe verfügen, die Sie in Ihrer Anwendung aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="0cae8-107">This topic assumes that you have a background task that you want to activate from your application.</span></span> <span data-ttu-id="0cae8-108">Wenn Sie bereits eine Hintergrundaufgabe ist, ist an vorhanden eine Beispiel Hintergrundaufgabe [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span><span class="sxs-lookup"><span data-stu-id="0cae8-108">If you don't already have a background task, there is a sample background task at [BackgroundActivity.cs](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackgroundActivation/cs/BackgroundActivity.cs).</span></span> <span data-ttu-id="0cae8-109">Oder führen Sie die Schritte in [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](create-and-register-a-background-task.md) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-109">Or, follow the steps in [Create and register an out-of-process background task](create-and-register-a-background-task.md) to create one.</span></span>

## <a name="why-use-an-application-trigger"></a><span data-ttu-id="0cae8-110">Gründe für die Verwendung eines Anwendung Triggers</span><span class="sxs-lookup"><span data-stu-id="0cae8-110">Why use an application trigger</span></span>

<span data-ttu-id="0cae8-111">Verwenden Sie ein **ApplicationTrigger** zum Ausführen von Code in einem gesonderten Prozess von der Vordergrund-app.</span><span class="sxs-lookup"><span data-stu-id="0cae8-111">Use an **ApplicationTrigger** to run code in a separate process from the foreground app.</span></span> <span data-ttu-id="0cae8-112">Ein **ApplicationTrigger** ist geeignet, wenn Ihre app Arbeit, die im Hintergrund – ausgeführt werden soll verfügt, auch wenn der Benutzer die Vordergrund-app wird geschlossen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-112">An **ApplicationTrigger** is appropriate if your app has work that needs to be done in the background--even if the user closes the foreground app.</span></span> <span data-ttu-id="0cae8-113">Wenn Hintergrund Arbeit anhalten sollte Wenn die app wird geschlossen oder sollte auf den Status des Prozesses Vordergrund gebunden, und klicken Sie dann [Erweitert Ausführung](run-minimized-with-extended-execution.md) soll, stattdessen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0cae8-113">If background work should halt when the app is closed, or should be tied to the state of the foreground process, then [Extended Execution](run-minimized-with-extended-execution.md) should be used, instead.</span></span>

## <a name="create-an-application-trigger"></a><span data-ttu-id="0cae8-114">Erstellen Sie einen Anwendung trigger</span><span class="sxs-lookup"><span data-stu-id="0cae8-114">Create an application trigger</span></span>

<span data-ttu-id="0cae8-115">Erstellen Sie eine neue [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger).</span><span class="sxs-lookup"><span data-stu-id="0cae8-115">Create a new [ApplicationTrigger](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.ApplicationTrigger).</span></span> <span data-ttu-id="0cae8-116">Es konnte in einem Feld gespeichert werden, wie im folgenden Codeausschnitt erfolgt.</span><span class="sxs-lookup"><span data-stu-id="0cae8-116">You could store it in a field as is done in the snippet below.</span></span> <span data-ttu-id="0cae8-117">Dies ist der Einfachheit, damit es nicht um eine neue Instanz später erstellen, wenn wir den Auslöser signalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="0cae8-117">This is for convenience so that we don't have to create a new instance later when we want to signal the trigger.</span></span> <span data-ttu-id="0cae8-118">Aber Sie können jede Instanz **ApplicationTrigger** verwenden, um den Auslöser signalisieren.</span><span class="sxs-lookup"><span data-stu-id="0cae8-118">But you can use any **ApplicationTrigger** instance to signal the trigger.</span></span>

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

## <a name="optional-add-a-condition"></a><span data-ttu-id="0cae8-119">(Optional) Hinzufügen einer Bedingung</span><span class="sxs-lookup"><span data-stu-id="0cae8-119">(Optional) Add a condition</span></span>

<span data-ttu-id="0cae8-120">Sie können eine Bedingung Hintergrund Aufgabe Steuerelement erstellen, wenn der Task ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0cae8-120">You can create a background task condition to control when the task runs.</span></span> <span data-ttu-id="0cae8-121">Eine Bedingung wird verhindert, dass die Hintergrundaufgabe ausführt, bis die Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="0cae8-121">A condition prevents the background task from running until the condition is met.</span></span> <span data-ttu-id="0cae8-122">Weitere Informationen finden Sie unter [Festlegen von Bedingungen für die Ausführung einer Hintergrundaufgabe](set-conditions-for-running-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="0cae8-122">For more information, see [Set conditions for running a background task](set-conditions-for-running-a-background-task.md).</span></span>

<span data-ttu-id="0cae8-123">In diesem Beispiel wird die Bedingung auf **InternetAvailable** festgelegt ist, sodass einmal ausgelöst, die Aufgabe nur einmal ausgeführt Internetzugang verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="0cae8-123">In this example the condition is set to **InternetAvailable** so that, once triggered, the task only runs once internet access is available.</span></span> <span data-ttu-id="0cae8-124">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="0cae8-124">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

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

<span data-ttu-id="0cae8-125">Ausführlichere Informationen auf Bedingungen und Arten von Triggern Hintergrund finden Sie unter [Unterstützung Ihrer app mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="0cae8-125">For more in-depth information on conditions and types of background triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

##  <a name="call-requestaccessasync"></a><span data-ttu-id="0cae8-126">Aufrufen von RequestAccessAsync()</span><span class="sxs-lookup"><span data-stu-id="0cae8-126">Call RequestAccessAsync()</span></span>

<span data-ttu-id="0cae8-127">Rufen Sie vor der Registrierung der Aufgabe **ApplicationTrigger** Hintergrund [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) , um die Hintergrundaktivitäten bestimmen, die dem Benutzer ermöglicht, da der Benutzer Hintergrundaktivitäten für Ihre app deaktiviert haben, kann ein.</span><span class="sxs-lookup"><span data-stu-id="0cae8-127">Before registering the **ApplicationTrigger** background task, call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700494) to determine the level of background activity the user allows because the user may have disabled background activity for your app.</span></span> <span data-ttu-id="0cae8-128">Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.</span><span class="sxs-lookup"><span data-stu-id="0cae8-128">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>

```csharp
var requestStatus = await Windows.ApplicationModel.Background.BackgroundExecutionManager.RequestAccessAsync();
if (requestStatus != BackgroundAccessStatus.AlwaysAllowed)
{
   // Depending on the value of requestStatus, provide an appropriate response
   // such as notifying the user which functionality won't work as expected
}
```

## <a name="register-the-background-task"></a><span data-ttu-id="0cae8-129">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-129">Register the background task</span></span>

<span data-ttu-id="0cae8-130">Registrieren Sie die Hintergrundaufgabe, indem Sie die Funktion zum Registrieren der Hintergrundaufgabe aufrufen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-130">Register the background task by calling your background task registration function.</span></span> <span data-ttu-id="0cae8-131">Weitere Informationen zum Registrieren von Hintergrundaufgaben und sehen Sie die Definition der **RegisterBackgroundTask()** -Methode in der folgenden Beispielcode finden Sie unter [Registrieren eine Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="0cae8-131">For more information on registering background tasks, and to see the definition of the **RegisterBackgroundTask()** method in the sample code below, see [Register a background task](register-a-background-task.md).</span></span>

<span data-ttu-id="0cae8-132">Sie verwenden eine Anwendung Trigger zum Erweitern der Lebensdauer des Upgradevorgangs Vordergrund erwägen, sollten Sie [Erweiterte Ausführung](run-minimized-with-extended-execution.md) stattdessen verwenden.</span><span class="sxs-lookup"><span data-stu-id="0cae8-132">If you are considering using an Application Trigger to extend the lifetime of your foreground process, consider using [Extended Execution](run-minimized-with-extended-execution.md) instead.</span></span> <span data-ttu-id="0cae8-133">Die Anwendung Trigger dient zum Erstellen eines Prozesses separat gehosteten Aufgaben in.</span><span class="sxs-lookup"><span data-stu-id="0cae8-133">The Application Trigger is designed for creating a separately hosted process to do work in.</span></span> <span data-ttu-id="0cae8-134">Im folgenden Codeausschnitt wird einen Out-of-Process Hintergrund Trigger registriert.</span><span class="sxs-lookup"><span data-stu-id="0cae8-134">The following code snippet registers an out-of-process background trigger.</span></span>

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

<span data-ttu-id="0cae8-135">Parameter für die Registrierung von Hintergrundaufgaben werden zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="0cae8-135">Background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="0cae8-136">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="0cae8-136">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="0cae8-137">Stellen Sie sicher, dass Ihre App problemlos mit Szenarien ohne erfolgreiche Registrierung von Hintergrundaufgaben zurechtkommt. Andernfalls stürzt die App unter Umständen ab, wenn sie so konzipiert ist, dass nach dem Versuch, eine Aufgabe zu registrieren, ein gültiges Registrierungsobjekt vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="0cae8-137">Ensure that your app gracefully handles scenarios where background task registration fails - if instead your app depends on having a valid registration object after attempting to register a task, it may crash.</span></span>

## <a name="trigger-the-background-task"></a><span data-ttu-id="0cae8-138">Auslösen der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-138">Trigger the background task</span></span>

<span data-ttu-id="0cae8-139">Bevor Sie den Vorgang Hintergrund auslösen, verwenden Sie [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) , um sicherzustellen, dass die Hintergrundaufgabe registriert ist.</span><span class="sxs-lookup"><span data-stu-id="0cae8-139">Before you trigger the background task, use [BackgroundTaskRegistration](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskRegistration) to verify that the background task is registered.</span></span> <span data-ttu-id="0cae8-140">Stellen Sie sicher, dass alle von Vorgängen Hintergrund registriert werden sollten Sie jetzt ist während der app-Start.</span><span class="sxs-lookup"><span data-stu-id="0cae8-140">A good time to verify that all of your background tasks are registered is during app launch.</span></span>

<span data-ttu-id="0cae8-141">Auslösen der Hintergrundaufgabe durch Aufrufen von [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger).</span><span class="sxs-lookup"><span data-stu-id="0cae8-141">Trigger the background task by calling [ApplicationTrigger.RequestAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtrigger).</span></span> <span data-ttu-id="0cae8-142">Jede Instanz **ApplicationTrigger** geschieht.</span><span class="sxs-lookup"><span data-stu-id="0cae8-142">Any **ApplicationTrigger** instance will do.</span></span>

<span data-ttu-id="0cae8-143">Beachten Sie, dass **ApplicationTrigger.RequestAsync** aus dem Hintergrund Vorgang selbst, oder wenn die app im Hintergrund Zustand "aktiv" ist nicht aufgerufen werden können (Weitere Informationen zum Anwendungsstatus finden Sie unter [App-Lebenszyklus](app-lifecycle.md) ).</span><span class="sxs-lookup"><span data-stu-id="0cae8-143">Note that **ApplicationTrigger.RequestAsync** can't be called from the background task itself, or when the app is in the background running state (see [App lifecycle](app-lifecycle.md) for more information about application states).</span></span>
<span data-ttu-id="0cae8-144">Es kann [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) zurück, wenn der Benutzer Energie oder private Richtlinien festgelegt hat, die verhindern, dass die app Hintergrundaktivität ausführen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-144">It may return [DisabledByPolicy](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult) if the user has set energy or privacy policies that prevent the app from performing background activity.</span></span>
<span data-ttu-id="0cae8-145">Darüber hinaus kann nur eine AppTrigger zu einem Zeitpunkt ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0cae8-145">Also, only one AppTrigger can run at a time.</span></span> <span data-ttu-id="0cae8-146">Wenn Sie versuchen, ein AppTrigger auszuführen, während eine andere bereits ausgeführt wird, gibt die Funktion [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult)zurück.</span><span class="sxs-lookup"><span data-stu-id="0cae8-146">If you attempt to run an AppTrigger while another is already running, the function will return [CurrentlyRunning](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.applicationtriggerresult).</span></span>

```csharp
var result = await _AppTrigger.RequestAsync();
```

## <a name="manage-resources-for-your-background-task"></a><span data-ttu-id="0cae8-147">Verwalten von Ressourcen für Ihre Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-147">Manage resources for your background task</span></span>

<span data-ttu-id="0cae8-148">Um zu ermitteln, ob der Benutzer die Hintergrundaktivität Ihrer App begrenzt hat, verwenden Sie [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="0cae8-148">Use [BackgroundExecutionManager.RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.aspx) to determine if the user has decided that your app’s background activity should be limited.</span></span> <span data-ttu-id="0cae8-149">Achten Sie auf die Akkunutzung, und führen Sie Ihre App nur dann im Hintergrund aus, wenn dies zum Ausführen einer vom Benutzer gewünschten Aktion notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="0cae8-149">Be aware of your battery usage and only run in the background when it is necessary to complete an action that the user wants.</span></span> <span data-ttu-id="0cae8-150">Finden Sie unter [Optimieren Hintergrundaktivitäten](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) für Weitere Informationen zu den Arten Benutzern die Einstellungen für Hintergrundaktivitäten steuern können.</span><span class="sxs-lookup"><span data-stu-id="0cae8-150">See [Optimize background activity](https://docs.microsoft.com/windows/uwp/debug-test-perf/optimize-background-activity) for more information about the ways users can control the settings for background activity.</span></span>  

- <span data-ttu-id="0cae8-151">Arbeitsspeicher: Zur Optimierung Ihrer app Arbeitsspeicher und weniger Energie Verwendung ist Grundvoraussetzung, dass das Betriebssystem Hintergrundtask ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0cae8-151">Memory: Tuning your app's memory and energy use is key to ensuring that the operating system will allow your background task to run.</span></span> <span data-ttu-id="0cae8-152">Verwenden Sie die [APIs für die Verwaltung von Arbeitsspeicher](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) , um wie viel Arbeitsspeicher finden Sie unter Ihrer Hintergrundaufgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0cae8-152">Use the [Memory Management APIs](https://msdn.microsoft.com/library/windows/apps/windows.system.memorymanager.aspx) to see how much memory your background task is using.</span></span> <span data-ttu-id="0cae8-153">Mehr Arbeitsspeicher Ihrer Hintergrundaufgabe verwendet, desto mehr ist für das Betriebssystem aktiviert bleiben bei einer anderen Anwendung im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="0cae8-153">The more memory your background task uses, the harder it is for the OS to keep it running when another app is in the foreground.</span></span> <span data-ttu-id="0cae8-154">Der Benutzer hat letztendlich die Kontrolle über alle Hintergrundaktivitäten, die Ihre App ausführen kann, und kann die Auswirkungen Ihrer App auf den Akkuverbrauch erkennen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-154">The user is ultimately in control of all background activity that your app can perform and has visibility on the impact your app has on battery use.</span></span>  
- <span data-ttu-id="0cae8-155">CPU-Zeit: Hintergrundaufgaben werden durch die Zeitspanne Wand Uhr Usage erhalten sie Triggertyp Basis begrenzt.</span><span class="sxs-lookup"><span data-stu-id="0cae8-155">CPU time: Background tasks are limited by the amount of wall-clock usage time they get based on trigger type.</span></span> <span data-ttu-id="0cae8-156">Hintergrundaufgaben, die von der Anwendung Trigger ausgelöst können nur etwa 10 Minuten.</span><span class="sxs-lookup"><span data-stu-id="0cae8-156">Background tasks triggered by the Application trigger are limited to about 10 minutes.</span></span>

<span data-ttu-id="0cae8-157">Die für Hintergrundaufgaben geltenden Ressourcenbeschränkungen finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="0cae8-157">See [Support your app with background tasks](support-your-app-with-background-tasks.md) for the resource constraints applied to background tasks.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cae8-158">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0cae8-158">Remarks</span></span>

<span data-ttu-id="0cae8-159">Beginnend mit Windows 10, ist es nicht mehr erforderlich für den Benutzer Ihre app auf dem Sperrbildschirm hinzufügen, um Hintergrundaufgaben nutzen.</span><span class="sxs-lookup"><span data-stu-id="0cae8-159">Starting with Windows 10, it is no longer necessary for the user to add your app to the lock screen in order to utilize background tasks.</span></span>

<span data-ttu-id="0cae8-160">Hintergrund läuft nur unter Verwendung einer **ApplicationTrigger** , wenn Sie zuerst [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="0cae8-160">A background task will only run using an **ApplicationTrigger** if you have called [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) first.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0cae8-161">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0cae8-161">Related topics</span></span>

* [<span data-ttu-id="0cae8-162">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="0cae8-162">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="0cae8-163">Hintergrund Task-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="0cae8-163">Background task code sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BackgroundTask)
* <span data-ttu-id="0cae8-164">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="0cae8-164">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="0cae8-165">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="0cae8-165">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="0cae8-166">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-166">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="0cae8-167">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="0cae8-167">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="0cae8-168">Geben Sie Speicher frei, wenn Ihre App in den Hintergrund verschoben wird</span><span class="sxs-lookup"><span data-stu-id="0cae8-168">Free memory when your app moves to the background</span></span>](reduce-memory-usage.md)
* [<span data-ttu-id="0cae8-169">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-169">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="0cae8-170">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="0cae8-170">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
* [<span data-ttu-id="0cae8-171">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="0cae8-171">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="0cae8-172">Verschieben der angehaltenen App mithilfe der erweiterten Ausführung</span><span class="sxs-lookup"><span data-stu-id="0cae8-172">Postpone app suspension with extended execution</span></span>](run-minimized-with-extended-execution.md)
* [<span data-ttu-id="0cae8-173">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-173">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="0cae8-174">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="0cae8-174">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="0cae8-175">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-175">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="0cae8-176">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="0cae8-176">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="0cae8-177">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="0cae8-177">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
