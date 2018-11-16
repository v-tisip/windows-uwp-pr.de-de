---
author: TylerMSFT
title: Behandeln einer abgebrochenen Hintergrundaufgabe
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die Abbruchanforderungen erkennt, die Ausführung beendet und den Abbruch mithilfe des beständigen Speichers an die App meldet.
ms.assetid: B7E23072-F7B0-4567-985B-737DD2A8728E
ms.author: twhitney
ms.date: 07/05/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 91de18af818113d79564ee8dfba7519a0f131246
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6993696"
---
# <a name="handle-a-cancelled-background-task"></a><span data-ttu-id="463b5-104">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-104">Handle a cancelled background task</span></span>

**<span data-ttu-id="463b5-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="463b5-105">Important APIs</span></span>**

-   [**<span data-ttu-id="463b5-106">BackgroundTaskCanceledEventHandler</span><span class="sxs-lookup"><span data-stu-id="463b5-106">BackgroundTaskCanceledEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224775)
-   [**<span data-ttu-id="463b5-107">IBackgroundTaskInstance</span><span class="sxs-lookup"><span data-stu-id="463b5-107">IBackgroundTaskInstance</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224797)
-   [**<span data-ttu-id="463b5-108">ApplicationData.Current</span><span class="sxs-lookup"><span data-stu-id="463b5-108">ApplicationData.Current</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241619)

<span data-ttu-id="463b5-109">Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die mithilfe des beständigen Speichers Abbruchanforderungen erkennt, die Ausführung beendet und den Abbruch an die App meldet.</span><span class="sxs-lookup"><span data-stu-id="463b5-109">Learn how to make a background task that recognizes a cancellation request, stops work, and reports the cancellation to the app using persistent storage.</span></span>

<span data-ttu-id="463b5-110">In diesem Thema wird davon ausgegangen, dass Sie bereits erstellt, haben eine hintergrundaufgabenklasse, einschließlich der **Run** -Methode, die als Einstiegspunkt der Hintergrundaufgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-110">This topic assumes you have already created a background task class, including the **Run** method that is used as the background task entry point.</span></span> <span data-ttu-id="463b5-111">Um schnell mit dem Erstellen einer Hintergrundaufgabe zu beginnen, lesen Sie [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](create-and-register-a-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb von Prozessen](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="463b5-111">To get started quickly building a background task, see [Create and register an out-of-process background task](create-and-register-a-background-task.md) or [Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span> <span data-ttu-id="463b5-112">Ausführlichere Informationen zu Bedingungen und Triggern finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="463b5-112">For more in-depth information on conditions and triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

<span data-ttu-id="463b5-113">Dieses Thema gilt auch für Hintergrundaufgaben innerhalb von Prozessen.</span><span class="sxs-lookup"><span data-stu-id="463b5-113">This topic is also applicable to in-process background tasks.</span></span> <span data-ttu-id="463b5-114">Aber anstatt die Methode **ausgeführt** , ersetzen Sie **OnBackgroundActivated**.</span><span class="sxs-lookup"><span data-stu-id="463b5-114">But instead of the **Run** method, substitute **OnBackgroundActivated**.</span></span> <span data-ttu-id="463b5-115">Hintergrundaufgaben innerhalb von Prozessen benötigen keinen beständigen Speicher, um den Abbruch zu signalisieren, da dieser mithilfe des App-Status übermittelt werden kann, wenn die Hintergrundaufgabe im selben Prozess ausgeführt wird, wie die Vordergrund-App.</span><span class="sxs-lookup"><span data-stu-id="463b5-115">In-process background tasks do not require you to use persistent storage to signal the cancellation because you can communicate the cancellation using app state since the background task is running in the same process as your foreground app.</span></span>

## <a name="use-the-oncanceled-method-to-recognize-cancellation-requests"></a><span data-ttu-id="463b5-116">Verwenden der Methode „OnCanceled“ zum Erkennen von Abbruchanforderungen</span><span class="sxs-lookup"><span data-stu-id="463b5-116">Use the OnCanceled method to recognize cancellation requests</span></span>

<span data-ttu-id="463b5-117">Schreiben Sie eine Methode für die Behandlung des Abbruchereignisses.</span><span class="sxs-lookup"><span data-stu-id="463b5-117">Write a method to handle the cancellation event.</span></span>

> [!NOTE]
> <span data-ttu-id="463b5-118">Für alle Gerätefamilien mit Ausnahme von Desktops können Hintergrundaufgaben beendet werden, wenn der Arbeitsspeicher des Geräts knapp wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-118">For all device families except desktop, if the device becomes low on memory, background tasks may be terminated.</span></span> <span data-ttu-id="463b5-119">Wenn eine Ausnahme über wenig Arbeitsspeicher wird nicht angezeigt, oder die app nicht wird behandelt, wird die Hintergrundaufgabe ohne Warnung und ohne Auslösen des OnCanceled-Ereignisses beendet.</span><span class="sxs-lookup"><span data-stu-id="463b5-119">If an out of memory exception is not surfaced, or the app doesn't handle it, then the background task will be terminated without warning and without raising the OnCanceled event.</span></span> <span data-ttu-id="463b5-120">Dadurch soll die Benutzerfreundlichkeit der App im Vordergrund sichergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="463b5-120">This helps to ensure the user experience of the app in the foreground.</span></span> <span data-ttu-id="463b5-121">Entwerfen Sie die Hintergrundaufgabe so, dass dieses Szenario behandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="463b5-121">Your background task should be designed to handle this scenario.</span></span>

<span data-ttu-id="463b5-122">Eine **OnCanceled**-Methode erstellen Sie wie folgt.</span><span class="sxs-lookup"><span data-stu-id="463b5-122">Create a method named **OnCanceled** as follows.</span></span> <span data-ttu-id="463b5-123">Diese Methode ist der Einstiegspunkt, der von der Windows-Runtime aufgerufen wird, wenn eine Abbruchanforderung für die Hintergrundaufgabe erfolgt.</span><span class="sxs-lookup"><span data-stu-id="463b5-123">This method is the entry point called by the Windows Runtime when a cancellation request is made against your background task.</span></span>

```csharp
private void OnCanceled(
    IBackgroundTaskInstance sender,
    BackgroundTaskCancellationReason reason)
{
    // TODO: Add code to notify the background task that it is cancelled.
}
```

```cppwinrt
void ExampleBackgroundTask::OnCanceled(
    Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance,
    Windows::ApplicationModel::Background::BackgroundTaskCancellationReason reason)
{
    // TODO: Add code to notify the background task that it is cancelled.
}
```

```cpp
void ExampleBackgroundTask::OnCanceled(
    IBackgroundTaskInstance^ taskInstance,
    BackgroundTaskCancellationReason reason)
{
    // TODO: Add code to notify the background task that it is cancelled.
}
```

<span data-ttu-id="463b5-124">Fügen Sie der Hintergrundaufgabenklasse eine Kennzeichenvariable mit dem Namen **\_CancelRequested** hinzu.</span><span class="sxs-lookup"><span data-stu-id="463b5-124">Add a flag variable called **\_CancelRequested** to the background task class.</span></span> <span data-ttu-id="463b5-125">Diese Variable wird verwendet, um anzuzeigen, ob eine Abbruchanforderung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="463b5-125">This variable will be used to indicate when a cancellation request has been made.</span></span>

```csharp
volatile bool _CancelRequested = false;
```

```cppwinrt
private:
    volatile bool m_cancelRequested;
```

```cpp
private:
    volatile bool CancelRequested;
```

<span data-ttu-id="463b5-126">Legen Sie in der **OnCanceled** -Methode, die Sie in Schritt 1 erstellt haben das Flag-Variable **\_CancelRequested** auf **"true"** fest.</span><span class="sxs-lookup"><span data-stu-id="463b5-126">In the **OnCanceled** method you created in step 1, set the flag variable **\_CancelRequested** to **true**.</span></span>

<span data-ttu-id="463b5-127">Im vollständigen [Beispiel für eine Hintergrundaufgabe]( http://go.microsoft.com/fwlink/p/?linkid=227509) **OnCanceled** -Methode **\_CancelRequested** auf **"true"** fest, und gibt eine möglicherweise hilfreiche Debugmeldung aus.</span><span class="sxs-lookup"><span data-stu-id="463b5-127">The full [background task sample]( http://go.microsoft.com/fwlink/p/?linkid=227509) **OnCanceled** method sets **\_CancelRequested** to **true** and writes potentially useful debug output.</span></span>

```csharp
private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
{
    // Indicate that the background task is canceled.
    _cancelRequested = true;

    Debug.WriteLine("Background " + sender.Task.Name + " Cancel Requested...");
}
```

```cppwinrt
void ExampleBackgroundTask::OnCanceled(
    Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance,
    Windows::ApplicationModel::Background::BackgroundTaskCancellationReason reason)
{
    // Indicate that the background task is canceled.
    m_cancelRequested = true;
}
```

```cpp
void ExampleBackgroundTask::OnCanceled(IBackgroundTaskInstance^ taskInstance, BackgroundTaskCancellationReason reason)
{
    // Indicate that the background task is canceled.
    CancelRequested = true;
}
```

<span data-ttu-id="463b5-128">Registrieren Sie in der Hintergrundaufgabe **Run** -Methode die **OnCanceled** -Ereignishandlermethode, bevor Sie Arbeit beginnen.</span><span class="sxs-lookup"><span data-stu-id="463b5-128">In the background task's **Run** method, register the **OnCanceled** event handler method before starting work.</span></span> <span data-ttu-id="463b5-129">Für eine Hintergrundaufgabe innerhalb von Prozessen empfiehlt sich diese Registrierung im Rahmen der Anwendungsinitialisierung.</span><span class="sxs-lookup"><span data-stu-id="463b5-129">In an in-process background task, you might do this registration as part of your application initialization.</span></span> <span data-ttu-id="463b5-130">Verwenden Sie z. B. die folgende Codezeile aus.</span><span class="sxs-lookup"><span data-stu-id="463b5-130">For example, use the following line of code.</span></span>

```csharp
taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);
```

```cppwinrt
taskInstance.Canceled({ this, &ExampleBackgroundTask::OnCanceled });
```

```cpp
taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &ExampleBackgroundTask::OnCanceled);
```

## <a name="handle-cancellation-by-exiting-your-background-task"></a><span data-ttu-id="463b5-131">Behandeln des Abbruchs durch Beenden der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-131">Handle cancellation by exiting your background task</span></span>

<span data-ttu-id="463b5-132">Wenn eine Abbruchanforderung empfangen wird, muss die Methode für die Hintergrundverarbeitung angehalten und beendet werden, indem erkannt wird, dass **\_cancelRequested** auf **true** festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="463b5-132">When a cancellation request is received, your method that does background work needs to stop work and exit by recognizing when **\_cancelRequested** is set to **true**.</span></span> <span data-ttu-id="463b5-133">Für in-Process-Hintergrundaufgaben bedeutet dies ein Zurückwechseln aus der **OnBackgroundActivated** -Methode.</span><span class="sxs-lookup"><span data-stu-id="463b5-133">For in-process background tasks, this means returning from the **OnBackgroundActivated** method.</span></span> <span data-ttu-id="463b5-134">Für Out-of-Process-Hintergrundaufgaben bedeutet dies ein Zurückwechseln aus der **Run** -Methode.</span><span class="sxs-lookup"><span data-stu-id="463b5-134">For out-of-process background tasks, this means returning from the **Run** method.</span></span>

<span data-ttu-id="463b5-135">Ändern Sie den Code der Hintergrundaufgabenklasse, um die Kennzeichenvariable zu überprüfen, während die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-135">Modify the code of your background task class to check the flag variable while it's working.</span></span> <span data-ttu-id="463b5-136">Wenn **\_cancelRequested** auf "true" ist, Arbeit Geschäftsvorgänge festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-136">If **\_cancelRequested** becomes set to true, stop work from continuing.</span></span>

<span data-ttu-id="463b5-137">Das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) enthält eine Überprüfung, die den regelmäßigen Zeitgeberrückruf anhält, wenn die Hintergrundaufgabe abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-137">The [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) includes a check that stops the periodic timer callback if the background task is canceled.</span></span>

```csharp
if ((_cancelRequested == false) && (_progress < 100))
{
    _progress += 10;
    _taskInstance.Progress = _progress;
}
else
{
    _periodicTimer.Cancel();
    // TODO: Record whether the task completed or was cancelled.
}
```

```cppwinrt
if (!m_cancelRequested && m_progress < 100)
{
    m_progress += 10;
    m_taskInstance.Progress(m_progress);
}
else
{
    m_periodicTimer.Cancel();
    // TODO: Record whether the task completed or was cancelled.
}
```

```cpp
if ((CancelRequested == false) && (Progress < 100))
{
    Progress += 10;
    TaskInstance->Progress = Progress;
}
else
{
    PeriodicTimer->Cancel();
    // TODO: Record whether the task completed or was cancelled.
}
```

> [!NOTE]
> <span data-ttu-id="463b5-138">Das oben gezeigte Codebeispiel verwendet die [**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797). [**Status**](https://msdn.microsoft.com/library/windows/apps/br224800) -Eigenschaft, die zum Aufzeichnen der Fortschritt der Hintergrundaufgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="463b5-138">The code sample shown above uses the [**IBackgroundTaskInstance**](https://msdn.microsoft.com/library/windows/apps/br224797).[**Progress**](https://msdn.microsoft.com/library/windows/apps/br224800) property being used to record background task progress.</span></span> <span data-ttu-id="463b5-139">Der Fortschritt wird der App mithilfe der [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782)-Klasse gemeldet.</span><span class="sxs-lookup"><span data-stu-id="463b5-139">Progress is reported back to the app using the [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782) class.</span></span>

<span data-ttu-id="463b5-140">Ändern Sie die **Run** -Methode, damit nach dem Anhalten der Arbeit aufzeichnet, ob die Aufgabe ausgeführt oder abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="463b5-140">Modify the **Run** method so that after work has stopped, it records whether the task completed or was cancelled.</span></span> <span data-ttu-id="463b5-141">Dieser Schritt gilt für Hintergrundaufgaben außerhalb von Prozessen, da eine Möglichkeit für die Kommunikation zwischen Prozessen haben müssen, wenn die Hintergrundaufgabe abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="463b5-141">This step applies to out-of-process background tasks because you need a way to communicate between processes when the background task was cancelled.</span></span> <span data-ttu-id="463b5-142">Für Hintergrundaufgaben innerhalb von Prozessen können Sie den Status einfach mit der Anwendung teilen, um anzugeben, dass die Aufgabe abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="463b5-142">For in-process background tasks, you can simply share state with the application to indicate the task was cancelled.</span></span>

<span data-ttu-id="463b5-143">[Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) zeichnet den Status in "localsettings".</span><span class="sxs-lookup"><span data-stu-id="463b5-143">The [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) records status in LocalSettings.</span></span>

```csharp
if ((_cancelRequested == false) && (_progress < 100))
{
    _progress += 10;
    _taskInstance.Progress = _progress;
}
else
{
    _periodicTimer.Cancel();

    var settings = ApplicationData.Current.LocalSettings;
    var key = _taskInstance.Task.TaskId.ToString();

    // Write to LocalSettings to indicate that this background task ran.
    if (_cancelRequested)
    {
        settings.Values[key] = "Canceled";
    }
    else
    {
        settings.Values[key] = "Completed";
    }
        
    Debug.WriteLine("Background " + _taskInstance.Task.Name + (_cancelRequested ? " Canceled" : " Completed"));
        
    // Indicate that the background task has completed.
    _deferral.Complete();
}
```

```cppwinrt
if (!m_cancelRequested && m_progress < 100)
{
    m_progress += 10;
    m_taskInstance.Progress(m_progress);
}
else
{
    m_periodicTimer.Cancel();

    // Write to LocalSettings to indicate that this background task ran.
    auto settings{ Windows::Storage::ApplicationData::Current().LocalSettings() };
    auto key{ m_taskInstance.Task().Name() };
    settings.Values().Insert(key, (m_progress < 100) ? winrt::box_value(L"Canceled") : winrt::box_value(L"Completed"));

    // Indicate that the background task has completed.
    m_deferral.Complete();
}
```

```cpp
if ((CancelRequested == false) && (Progress < 100))
{
    Progress += 10;
    TaskInstance->Progress = Progress;
}
else
{
    PeriodicTimer->Cancel();
        
    // Write to LocalSettings to indicate that this background task ran.
    auto settings = ApplicationData::Current->LocalSettings;
    auto key = TaskInstance->Task->Name;
    settings->Values->Insert(key, (Progress < 100) ? "Canceled" : "Completed");
        
    // Indicate that the background task has completed.
    Deferral->Complete();
}
```

## <a name="remarks"></a><span data-ttu-id="463b5-144">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="463b5-144">Remarks</span></span>

<span data-ttu-id="463b5-145">Sie können das [Beispiel zur Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunterladen, um diese Codebeispiele im Kontext von Methoden anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="463b5-145">You can download the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) to see these code examples in the context of methods.</span></span>

<span data-ttu-id="463b5-146">Zur Veranschaulichung zeigt der Beispielcode nur Teile der **Run** -Methode (und des rückruftimers) aus dem [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="463b5-146">For illustrative purposes, the sample code shows only portions of the **Run** method (and callback timer) from the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

## <a name="run-method-example"></a><span data-ttu-id="463b5-147">Beispiel der Run-Methode</span><span class="sxs-lookup"><span data-stu-id="463b5-147">Run method example</span></span>

<span data-ttu-id="463b5-148">Die **Run** -Methode und den timerrückruf-Code abgeschlossen ist, aus dem [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) sind unten aufgeführt, für den Kontext.</span><span class="sxs-lookup"><span data-stu-id="463b5-148">The complete **Run** method, and timer callback code, from the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) are shown below for context.</span></span>

```csharp
// The Run method is the entry point of a background task.
public void Run(IBackgroundTaskInstance taskInstance)
{
    Debug.WriteLine("Background " + taskInstance.Task.Name + " Starting...");

    // Query BackgroundWorkCost
    // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
    // of work in the background task and return immediately.
    var cost = BackgroundWorkCost.CurrentBackgroundWorkCost;
    var settings = ApplicationData.Current.LocalSettings;
    settings.Values["BackgroundWorkCost"] = cost.ToString();

    // Associate a cancellation handler with the background task.
    taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);

    // Get the deferral object from the task instance, and take a reference to the taskInstance;
    _deferral = taskInstance.GetDeferral();
    _taskInstance = taskInstance;

    _periodicTimer = ThreadPoolTimer.CreatePeriodicTimer(new TimerElapsedHandler(PeriodicTimerCallback), TimeSpan.FromSeconds(1));
}

// Simulate the background task activity.
private void PeriodicTimerCallback(ThreadPoolTimer timer)
{
    if ((_cancelRequested == false) && (_progress < 100))
    {
        _progress += 10;
        _taskInstance.Progress = _progress;
    }
    else
    {
        _periodicTimer.Cancel();

        var settings = ApplicationData.Current.LocalSettings;
        var key = _taskInstance.Task.Name;

        // Write to LocalSettings to indicate that this background task ran.
        settings.Values[key] = (_progress < 100) ? "Canceled with reason: " + _cancelReason.ToString() : "Completed";
        Debug.WriteLine("Background " + _taskInstance.Task.Name + settings.Values[key]);

        // Indicate that the background task has completed.
        _deferral.Complete();
    }
}
```

```cppwinrt
void ExampleBackgroundTask::Run(Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance)
{
    // Query BackgroundWorkCost
    // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
    // of work in the background task and return immediately.
    auto cost{ Windows::ApplicationModel::Background::BackgroundWorkCost::CurrentBackgroundWorkCost() };
    auto settings{ Windows::Storage::ApplicationData::Current().LocalSettings() };
    std::wstring costAsString{ L"Low" };
    if (cost == Windows::ApplicationModel::Background::BackgroundWorkCostValue::Medium) costAsString = L"Medium";
    else if (cost == Windows::ApplicationModel::Background::BackgroundWorkCostValue::High) costAsString = L"High";
    settings.Values().Insert(L"BackgroundWorkCost", winrt::box_value(costAsString));

    // Associate a cancellation handler with the background task.
    taskInstance.Canceled({ this, &ExampleBackgroundTask::OnCanceled });

    // Get the deferral object from the task instance, and take a reference to the taskInstance.
    m_deferral = taskInstance.GetDeferral();
    m_taskInstance = taskInstance;

    Windows::Foundation::TimeSpan period{ std::chrono::seconds{1} };
    m_periodicTimer = Windows::System::Threading::ThreadPoolTimer::CreatePeriodicTimer([this](Windows::System::Threading::ThreadPoolTimer timer)
    {
        if (!m_cancelRequested && m_progress < 100)
        {
            m_progress += 10;
            m_taskInstance.Progress(m_progress);
        }
        else
        {
            m_periodicTimer.Cancel();

            // Write to LocalSettings to indicate that this background task ran.
            auto settings{ Windows::Storage::ApplicationData::Current().LocalSettings() };
            auto key{ m_taskInstance.Task().Name() };
            settings.Values().Insert(key, (m_progress < 100) ? winrt::box_value(L"Canceled") : winrt::box_value(L"Completed"));

            // Indicate that the background task has completed.
            m_deferral.Complete();
        }
    }, period);
}
```

```cpp
void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
{
    // Query BackgroundWorkCost
    // Guidance: If BackgroundWorkCost is high, then perform only the minimum amount
    // of work in the background task and return immediately.
    auto cost = BackgroundWorkCost::CurrentBackgroundWorkCost;
    auto settings = ApplicationData::Current->LocalSettings;
    settings->Values->Insert("BackgroundWorkCost", cost.ToString());

    // Associate a cancellation handler with the background task.
    taskInstance->Canceled += ref new BackgroundTaskCanceledEventHandler(this, &ExampleBackgroundTask::OnCanceled);

    // Get the deferral object from the task instance, and take a reference to the taskInstance.
    TaskDeferral = taskInstance->GetDeferral();
    TaskInstance = taskInstance;

    auto timerDelegate = [this](ThreadPoolTimer^ timer)
    {
        if ((CancelRequested == false) &&
            (Progress < 100))
        {
            Progress += 10;
            TaskInstance->Progress = Progress;
        }
        else
        {
            PeriodicTimer->Cancel();

            // Write to LocalSettings to indicate that this background task ran.
            auto settings = ApplicationData::Current->LocalSettings;
            auto key = TaskInstance->Task->Name;
            settings->Values->Insert(key, (Progress < 100) ? "Canceled with reason: " + CancelReason.ToString() : "Completed");

            // Indicate that the background task has completed.
            TaskDeferral->Complete();
        }
    };

    TimeSpan period;
    period.Duration = 1000 * 10000; // 1 second
    PeriodicTimer = ThreadPoolTimer::CreatePeriodicTimer(ref new TimerElapsedHandler(timerDelegate), period);
}
```

## <a name="related-topics"></a><span data-ttu-id="463b5-149">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="463b5-149">Related topics</span></span>

- <span data-ttu-id="463b5-150">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="463b5-150">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
- [<span data-ttu-id="463b5-151">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="463b5-151">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
- [<span data-ttu-id="463b5-152">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="463b5-152">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
- [<span data-ttu-id="463b5-153">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="463b5-153">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
- [<span data-ttu-id="463b5-154">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="463b5-154">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
- [<span data-ttu-id="463b5-155">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-155">Register a background task</span></span>](register-a-background-task.md)
- [<span data-ttu-id="463b5-156">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="463b5-156">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
- [<span data-ttu-id="463b5-157">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="463b5-157">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
- [<span data-ttu-id="463b5-158">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-158">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
- [<span data-ttu-id="463b5-159">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-159">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
- [<span data-ttu-id="463b5-160">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="463b5-160">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
- [<span data-ttu-id="463b5-161">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="463b5-161">Debug a background task</span></span>](debug-a-background-task.md)
- [<span data-ttu-id="463b5-162">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="463b5-162">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
