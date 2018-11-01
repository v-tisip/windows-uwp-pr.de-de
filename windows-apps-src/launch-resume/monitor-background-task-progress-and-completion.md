---
author: TylerMSFT
title: Überwachen des Status und Abschlusses von Hintergrundaufgaben
description: Hier erfahren Sie, wie Ihre App den von einer Hintergrundaufgabe gemeldeten Status und Abschluss erkennt.
ms.assetid: 17544FD7-A336-4254-97DC-2BF8994FF9B2
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 9c71d8a42a71d221f6a20850f1d002be922517be
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5878955"
---
# <a name="monitor-background-task-progress-and-completion"></a><span data-ttu-id="a10c3-104">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="a10c3-104">Monitor background task progress and completion</span></span>

**<span data-ttu-id="a10c3-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="a10c3-105">Important APIs</span></span>**

- [**<span data-ttu-id="a10c3-106">BackgroundTaskRegistration</span><span class="sxs-lookup"><span data-stu-id="a10c3-106">BackgroundTaskRegistration</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224786)
- [**<span data-ttu-id="a10c3-107">BackgroundTaskProgressEventHandler</span><span class="sxs-lookup"><span data-stu-id="a10c3-107">BackgroundTaskProgressEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224785)
- [**<span data-ttu-id="a10c3-108">BackgroundTaskCompletedEventHandler</span><span class="sxs-lookup"><span data-stu-id="a10c3-108">BackgroundTaskCompletedEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224781)

<span data-ttu-id="a10c3-109">Erfahren Sie, wie Ihre App einen von einer ausgeführten Out-of-Process-Hintergrundaufgabe gemeldeten Status und Abschluss erkennt.</span><span class="sxs-lookup"><span data-stu-id="a10c3-109">Learn how your app can recognize progress and completion reported by a background task that runs out-of-process.</span></span> <span data-ttu-id="a10c3-110">(Für In-Process-Hintergrundaufgaben können Sie freigegebene Variablen festlegen, um Status und Abschluss anzugeben.)</span><span class="sxs-lookup"><span data-stu-id="a10c3-110">(For in-process background tasks, you can set shared variables to signify progress and completion.)</span></span>

<span data-ttu-id="a10c3-111">Der Status und Abschluss von Hintergrundaufgaben kann durch App-Code überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="a10c3-111">Background task progress and completion can be monitored by app code.</span></span> <span data-ttu-id="a10c3-112">Hierzu abonniert die App Ereignisse der Hintergrundaufgabe(n), die sie im System registriert hat.</span><span class="sxs-lookup"><span data-stu-id="a10c3-112">To do so, the app subscribes to events from the background task(s) it has registered with the system.</span></span>

- <span data-ttu-id="a10c3-113">In diesem Thema wird vorausgesetzt, dass Sie über eine App verfügen, die Hintergrundaufgaben registriert.</span><span class="sxs-lookup"><span data-stu-id="a10c3-113">This topic assumes that you have an app that registers background tasks.</span></span> <span data-ttu-id="a10c3-114">Um schnell mit dem Erstellen einer Hintergrundaufgabe zu beginnen, lesen Sie [Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md) oder [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses](create-and-register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="a10c3-114">To get started quickly building a background task, see [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) or [Create and register an out-of-process background task](create-and-register-a-background-task.md).</span></span> <span data-ttu-id="a10c3-115">Ausführlichere Informationen zu Bedingungen und Triggern finden Sie unter [Unterstützen der App mit Hintergrundaufgaben](support-your-app-with-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="a10c3-115">For more in-depth information on conditions and triggers, see [Support your app with background tasks](support-your-app-with-background-tasks.md).</span></span>

## <a name="create-an-event-handler-to-handle-completed-background-tasks"></a><span data-ttu-id="a10c3-116">Erstellen Sie einen Ereignishandler zum Behandeln abgeschlossener Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="a10c3-116">Create an event handler to handle completed background tasks</span></span>

### <a name="step-1"></a><span data-ttu-id="a10c3-117">Schritt 1</span><span class="sxs-lookup"><span data-stu-id="a10c3-117">Step 1</span></span>
<span data-ttu-id="a10c3-118">Erstellen Sie eine Ereignishandlerfunktion zum Behandeln abgeschlossener Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="a10c3-118">Create an event handler function to handle completed background tasks.</span></span> <span data-ttu-id="a10c3-119">Dieser Code muss einem bestimmten Profil folgen, die entweder ein Objekt [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224803) und ein [**BackgroundTaskCompletedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224778) -Objekt annimmt.</span><span class="sxs-lookup"><span data-stu-id="a10c3-119">This code needs to follow a specific footprint, which takes an [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224803) object and a [**BackgroundTaskCompletedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224778) object.</span></span>

<span data-ttu-id="a10c3-120">Verwenden Sie das folgende Profil für die **OnCompleted** Hintergrund Ereignishandlermethode.</span><span class="sxs-lookup"><span data-stu-id="a10c3-120">Use the following footprint for the **OnCompleted** background task event handler method.</span></span>

```csharp
private void OnCompleted(IBackgroundTaskRegistration task, BackgroundTaskCompletedEventArgs args)
{
    // TODO: Add code that deals with background task completion.
}
```

```cppwinrt
auto completed{ [this](
        Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
        Windows::ApplicationModel::Background::BackgroundTaskCompletedEventArgs const& /* args */)
{
    // TODO: Add code that deals with background task completion.
} };
```

```cpp
auto completed = [this](BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
{
    // TODO: Add code that deals with background task completion.
};
```

### <a name="step-2"></a><span data-ttu-id="a10c3-121">Schritt 2</span><span class="sxs-lookup"><span data-stu-id="a10c3-121">Step 2</span></span>
<span data-ttu-id="a10c3-122">Fügen Sie dem Ereignishandler Code zum Behandeln des Abschlusses der Hintergrundaufgabe hinzu.</span><span class="sxs-lookup"><span data-stu-id="a10c3-122">Add code to the event handler that deals with the background task completion.</span></span>

<span data-ttu-id="a10c3-123">Das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) aktualisiert z.B. die Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="a10c3-123">For example, the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) updates the UI.</span></span>

```csharp
private void OnCompleted(IBackgroundTaskRegistration task, BackgroundTaskCompletedEventArgs args)
{
    UpdateUI();
}
```

```cppwinrt
auto completed{ [this](
        Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
        Windows::ApplicationModel::Background::BackgroundTaskCompletedEventArgs const& /* args */)
{
    UpdateUI();
} };
```

```cpp
auto completed = [this](BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
{    
    UpdateUI();
};
```

## <a name="create-an-event-handler-function-to-handle-background-task-progress"></a><span data-ttu-id="a10c3-124">Erstellen einer Ereignishandlerfunktion zum Behandeln des Hintergrundaufgabenfortschritts</span><span class="sxs-lookup"><span data-stu-id="a10c3-124">Create an event handler function to handle background task progress</span></span>

### <a name="step-1"></a><span data-ttu-id="a10c3-125">Schritt 1</span><span class="sxs-lookup"><span data-stu-id="a10c3-125">Step 1</span></span>
<span data-ttu-id="a10c3-126">Erstellen Sie eine Ereignishandlerfunktion zum Behandeln abgeschlossener Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="a10c3-126">Create an event handler function to handle completed background tasks.</span></span> <span data-ttu-id="a10c3-127">Dieser Code muss einem bestimmten Profil entsprechen und ein [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224803)-Objekt sowie ein [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782)-Objekt enthalten:</span><span class="sxs-lookup"><span data-stu-id="a10c3-127">This code needs to follow a specific footprint, which takes in an [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224803) object and a [**BackgroundTaskProgressEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224782) object:</span></span>

<span data-ttu-id="a10c3-128">Verwenden Sie das folgende Profil für die Ereignishandlermethode für die OnProgress-Hintergrundaufgabe:</span><span class="sxs-lookup"><span data-stu-id="a10c3-128">Use the following footprint for the OnProgress background task event handler method:</span></span>

```csharp
private void OnProgress(IBackgroundTaskRegistration task, BackgroundTaskProgressEventArgs args)
{
    // TODO: Add code that deals with background task progress.
}
```

```cppwinrt
auto progress{ [this](
    Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
    Windows::ApplicationModel::Background::BackgroundTaskProgressEventArgs const& /* args */)
{
    // TODO: Add code that deals with background task progress.
} };
```

```cpp
auto progress = [this](BackgroundTaskRegistration^ task, BackgroundTaskProgressEventArgs^ args)
{
    // TODO: Add code that deals with background task progress.
};
```

### <a name="step-2"></a><span data-ttu-id="a10c3-129">Schritt 2</span><span class="sxs-lookup"><span data-stu-id="a10c3-129">Step 2</span></span>
<span data-ttu-id="a10c3-130">Fügen Sie dem Ereignishandler Code zum Behandeln des Abschlusses der Hintergrundaufgabe hinzu.</span><span class="sxs-lookup"><span data-stu-id="a10c3-130">Add code to the event handler that deals with the background task completion.</span></span>

<span data-ttu-id="a10c3-131">So aktualisiert beispielsweise das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) die Benutzeroberfläche mit dem Fortschrittsstatus, der mithilfe des *args*-Parameters übergeben wird:</span><span class="sxs-lookup"><span data-stu-id="a10c3-131">For example, the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) updates the UI with the progress status passed in via the *args* parameter:</span></span>

```csharp
private void OnProgress(IBackgroundTaskRegistration task, BackgroundTaskProgressEventArgs args)
{
    var progress = "Progress: " + args.Progress + "%";
    BackgroundTaskSample.SampleBackgroundTaskProgress = progress;
    UpdateUI();
}
```

```cppwinrt
auto progress{ [this](
    Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
    Windows::ApplicationModel::Background::BackgroundTaskProgressEventArgs const& args)
{
    winrt::hstring progress{ L"Progress: " + winrt::to_hstring(args.Progress()) + L"%" };
    BackgroundTaskSample::SampleBackgroundTaskProgress = progress;
    UpdateUI();
} };
```

```cpp
auto progress = [this](BackgroundTaskRegistration^ task, BackgroundTaskProgressEventArgs^ args)
{
    auto progress = "Progress: " + args->Progress + "%";
    BackgroundTaskSample::SampleBackgroundTaskProgress = progress;
    UpdateUI();
};
```

## <a name="register-the-event-handler-functions-with-new-and-existing-background-tasks"></a><span data-ttu-id="a10c3-132">Registrieren der Ereignishandlerfunktionen mit neuen und vorhandenen Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="a10c3-132">Register the event handler functions with new and existing background tasks</span></span>

### <a name="step-1"></a><span data-ttu-id="a10c3-133">Schritt 1</span><span class="sxs-lookup"><span data-stu-id="a10c3-133">Step 1</span></span>
<span data-ttu-id="a10c3-134">Wenn die App erstmals eine Hintergrundaufgabe registriert, muss sie sich für den Empfang von Status- und Abschlussupdates registrieren, falls die Aufgabe ausgeführt wird, während die App im Vordergrund noch aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="a10c3-134">When the app registers a background task for the first time, it should register to receive progress and completion updates for it, in case the task runs while the app is still active in the foreground.</span></span>

<span data-ttu-id="a10c3-135">So ruft beispielsweise das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) für jede Hintergrundaufgabe, die es registriert, die folgende Funktion auf:</span><span class="sxs-lookup"><span data-stu-id="a10c3-135">For example, the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) calls the following function on each background task that it registers:</span></span>

```csharp
private void AttachProgressAndCompletedHandlers(IBackgroundTaskRegistration task)
{
    task.Progress += new BackgroundTaskProgressEventHandler(OnProgress);
    task.Completed += new BackgroundTaskCompletedEventHandler(OnCompleted);
}
```

```cppwinrt
void SampleBackgroundTask::AttachProgressAndCompletedHandlers(Windows::ApplicationModel::Background::IBackgroundTaskRegistration const& task)
{
    auto progress{ [this](
        Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
        Windows::ApplicationModel::Background::BackgroundTaskProgressEventArgs const& args)
    {
        winrt::hstring progress{ L"Progress: " + winrt::to_hstring(args.Progress()) + L"%" };
        BackgroundTaskSample::SampleBackgroundTaskProgress = progress;
        UpdateUI();
    } };

    task.Progress(progress);

    auto completed{ [this](
        Windows::ApplicationModel::Background::BackgroundTaskRegistration const& /* sender */,
        Windows::ApplicationModel::Background::BackgroundTaskCompletedEventArgs const& /* args */)
    {
        UpdateUI();
    } };

    task.Completed(completed);
}
```

```cpp
void SampleBackgroundTask::AttachProgressAndCompletedHandlers(IBackgroundTaskRegistration^ task)
{
    auto progress = [this](BackgroundTaskRegistration^ task, BackgroundTaskProgressEventArgs^ args)
    {
        auto progress = "Progress: " + args->Progress + "%";
        BackgroundTaskSample::SampleBackgroundTaskProgress = progress;
        UpdateUI();
    };

    task->Progress += ref new BackgroundTaskProgressEventHandler(progress);

    auto completed = [this](BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
    {
        UpdateUI();
    };

    task->Completed += ref new BackgroundTaskCompletedEventHandler(completed);
}
```

### <a name="step-2"></a><span data-ttu-id="a10c3-136">Schritt 2</span><span class="sxs-lookup"><span data-stu-id="a10c3-136">Step 2</span></span>
<span data-ttu-id="a10c3-137">Wenn die App startet oder zu einer neuen Seite navigiert, für die der Hintergrundaufgabenstatus relevant ist, muss sie eine Liste mit den derzeit registrierten Hintergrundaufgaben abrufen und diese den Status- und Abschlussereignishandlerfunktionen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="a10c3-137">When the app launches, or navigates to a new page where background task status is relevant, it should get a list of background tasks currently registered and associate them with the progress and completion event handler functions.</span></span> <span data-ttu-id="a10c3-138">Die Liste mit den derzeit von der Anwendung registrierten Hintergrundaufgaben ist in der [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786).[**AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787)-Eigenschaft gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a10c3-138">The list of background tasks currently registered by the application is kept in the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786).[**AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) property.</span></span>

<span data-ttu-id="a10c3-139">So verwendet beispielsweise das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) den folgenden Code, um Ereignishandler anzufügen, wenn zur Seite „SampleBackgroundTask“ navigiert wird:</span><span class="sxs-lookup"><span data-stu-id="a10c3-139">For example, the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) uses the following code to attach event handlers when the SampleBackgroundTask page is navigated to:</span></span>

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    foreach (var task in BackgroundTaskRegistration.AllTasks)
    {
        if (task.Value.Name == BackgroundTaskSample.SampleBackgroundTaskName)
        {
            AttachProgressAndCompletedHandlers(task.Value);
            BackgroundTaskSample.UpdateBackgroundTaskStatus(BackgroundTaskSample.SampleBackgroundTaskName, true);
        }
    }

    UpdateUI();
}
```

```cppwinrt
void SampleBackgroundTask::OnNavigatedTo(Windows::UI::Xaml::Navigation::NavigationEventArgs const& /* e */)
{
    // A pointer back to the main page. This is needed if you want to call methods in MainPage such
    // as NotifyUser().
    m_rootPage = MainPage::Current;

    // Attach progress and completed handlers to any existing tasks.
    auto allTasks{ Windows::ApplicationModel::Background::BackgroundTaskRegistration::AllTasks() };

    for (auto const& task : allTasks)
    {
        if (task.Value().Name() == SampleBackgroundTaskName)
        {
            AttachProgressAndCompletedHandlers(task.Value());
            break;
        }
    }

    UpdateUI();
}
```

```cpp
void SampleBackgroundTask::OnNavigatedTo(NavigationEventArgs^ e)
{
    // A pointer back to the main page.  This is needed if you want to call methods in MainPage such
    // as NotifyUser().
    rootPage = MainPage::Current;

    // Attach progress and completed handlers to any existing tasks.
    auto iter = BackgroundTaskRegistration::AllTasks->First();
    auto hascur = iter->HasCurrent;
    while (hascur)
    {
        auto cur = iter->Current->Value;

        if (cur->Name == SampleBackgroundTaskName)
        {
            AttachProgressAndCompletedHandlers(cur);
            break;
        }

        hascur = iter->MoveNext();
    }

    UpdateUI();
}
```

## <a name="related-topics"></a><span data-ttu-id="a10c3-140">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a10c3-140">Related topics</span></span>

* <span data-ttu-id="a10c3-141">[Erstellen und Registrieren einer Hintergrundaufgabe innerhalb des Prozesses](create-and-register-an-inproc-background-task.md)</span><span class="sxs-lookup"><span data-stu-id="a10c3-141">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="a10c3-142">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="a10c3-142">Create and register an out-of-process background task</span></span>](create-and-register-a-background-task.md)
* [<span data-ttu-id="a10c3-143">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="a10c3-143">Declare background tasks in the application manifest</span></span>](declare-background-tasks-in-the-application-manifest.md)
* [<span data-ttu-id="a10c3-144">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a10c3-144">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="a10c3-145">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a10c3-145">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="a10c3-146">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="a10c3-146">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="a10c3-147">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a10c3-147">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="a10c3-148">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a10c3-148">Update a live tile from a background task</span></span>](update-a-live-tile-from-a-background-task.md)
* [<span data-ttu-id="a10c3-149">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="a10c3-149">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="a10c3-150">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="a10c3-150">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* [<span data-ttu-id="a10c3-151">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="a10c3-151">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="a10c3-152">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a10c3-152">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="a10c3-153">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="a10c3-153">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)
