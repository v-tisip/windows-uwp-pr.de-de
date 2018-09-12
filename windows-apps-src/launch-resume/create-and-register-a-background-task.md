---
author: TylerMSFT
title: Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe
description: Erstellen Sie eine Out-of-Process-Hintergrundaufgabenklasse, und registrieren Sie sie für die Ausführung, wenn Ihre App nicht im Vordergrund ausgeführt wird.
ms.assetid: 4F98F6A3-0D3D-4EFB-BA8E-30ED37AE098B
ms.author: twhitney
ms.date: 07/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: a599fdef47bb681ef4909fe5bba2a01a1687ba66
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3930072"
---
# <a name="create-and-register-an-out-of-process-background-task"></a><span data-ttu-id="8009b-104">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="8009b-104">Create and register an out-of-process background task</span></span>

**<span data-ttu-id="8009b-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="8009b-105">Important APIs</span></span>**

-   [**<span data-ttu-id="8009b-106">IBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="8009b-106">IBackgroundTask</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**<span data-ttu-id="8009b-107">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="8009b-107">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
-   [**<span data-ttu-id="8009b-108">BackgroundTaskCompletedEventHandler</span><span class="sxs-lookup"><span data-stu-id="8009b-108">BackgroundTaskCompletedEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224781)

<span data-ttu-id="8009b-109">Erstellen Sie eine Hintergrundaufgabenklasse, und registrieren Sie diese für die Ausführung, wenn sich die App nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="8009b-109">Create a background task class and register it to run when your app is not in the foreground.</span></span> <span data-ttu-id="8009b-110">In diesem Thema wird gezeigt, wie Sie eine Hintergrundaufgabe erstellen und registrieren, die in einem vom App-Prozess getrennten Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8009b-110">This topic demonstrates how to create and register a background task that runs in a separate process than your app's process.</span></span> <span data-ttu-id="8009b-111">Informationen zum Ausführen von Hintergrundarbeiten direkt in der Vordergrundanwendung finden Sie unter [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="8009b-111">To do background work directly in the foreground application, see [Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8009b-112">Wenn Sie eine Hintergrundaufgabe zur Medienwiedergabe im Hintergrund verwenden, finden Sie unter [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) Informationen zu Verbesserungen in Windows10, Version1607, die dies wesentlich erleichtern.</span><span class="sxs-lookup"><span data-stu-id="8009b-112">If you use a background task to play media in the background, see [Play media in the background](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) for information about improvements in Windows 10, version 1607, that make it much easier.</span></span>

## <a name="create-the-background-task-class"></a><span data-ttu-id="8009b-113">Erstellen einer Hintergrundaufgabenklasse</span><span class="sxs-lookup"><span data-stu-id="8009b-113">Create the Background Task class</span></span>

<span data-ttu-id="8009b-114">Sie können Code im Hintergrund ausführen, indem Sie Klassen schreiben, die die [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="8009b-114">You can run code in the background by writing classes that implement the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface.</span></span> <span data-ttu-id="8009b-115">Dieser Code wird ausgeführt, wenn ein bestimmtes Ereignis ausgelöst wird, verwenden, z. B. [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) oder [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517).</span><span class="sxs-lookup"><span data-stu-id="8009b-115">This code runs when a specific event is triggered by using, for example, [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) or [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517).</span></span>

<span data-ttu-id="8009b-116">Die folgenden Schritte zeigen, wie Sie eine neue Klasse zum Implementieren der [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle schreiben.</span><span class="sxs-lookup"><span data-stu-id="8009b-116">The following steps show you how to write a new class that implements the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface.</span></span>

1.  <span data-ttu-id="8009b-117">Erstellen Sie ein neues Projekt für Hintergrundaufgaben, und fügen Sie es zu Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="8009b-117">Create a new project for background tasks and add it to your solution.</span></span> <span data-ttu-id="8009b-118">Zu diesem Zweck mit der rechten Maustaste auf Ihren Projektmappenknoten im **Projektmappen-Explorer** , und wählen Sie **Hinzufügen** \> **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="8009b-118">To do this, right-click on your solution node in the **Solution Explorer** and select **Add** \> **New Project**.</span></span> <span data-ttu-id="8009b-119">Wählen Sie die **Komponente für Windows-Runtime** -Projekttyp, nennen Sie das Projekt, und klicken Sie auf OK.</span><span class="sxs-lookup"><span data-stu-id="8009b-119">Then select the **Windows Runtime Component** project type, name the project, and click OK.</span></span>
2.  <span data-ttu-id="8009b-120">Verweisen Sie auf das Hintergrundaufgabenprojekt aus dem Projekt für UWP-Apps (Universelle Windows-Plattform).</span><span class="sxs-lookup"><span data-stu-id="8009b-120">Reference the background tasks project from your Universal Windows Platform (UWP) app project.</span></span> <span data-ttu-id="8009b-121">Für eine c# oder C++-app in Ihrem app-Projekt mit der rechten Maustaste auf **Verweise** , und wählen Sie **Neuen Verweis hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="8009b-121">For a C# or C++ app, in your app project, right-click on **References** and select **Add New Reference**.</span></span> <span data-ttu-id="8009b-122">Wählen Sie unter **Projektmappe** die Option **Projekte**. Wählen Sie dann den Namen Ihres Hintergrundaufgabenprojekts aus, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="8009b-122">Under **Solution**, select **Projects** and then select the name of your background task project and click **Ok**.</span></span>
3.  <span data-ttu-id="8009b-123">Fügen Sie eine neue Klasse, die die [**IBackgroundTask**](/uwp/api/Windows.ApplicationModel.Background.IBackgroundTask) -Schnittstelle implementiert, auf das hintergrundaufgabenprojekt.</span><span class="sxs-lookup"><span data-stu-id="8009b-123">To the background tasks project, add a new class that implements the [**IBackgroundTask**](/uwp/api/Windows.ApplicationModel.Background.IBackgroundTask) interface.</span></span> <span data-ttu-id="8009b-124">Die [**IBackgroundTask.Run**](/uwp/api/windows.applicationmodel.background.ibackgroundtask.run) -Methode ist ein erforderlicher Einstiegspunkt und, die aufgerufen wird, wenn das angegebene Ereignis ausgelöst wird. Diese Methode ist in jeder Hintergrundaufgabe erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8009b-124">The [**IBackgroundTask.Run**](/uwp/api/windows.applicationmodel.background.ibackgroundtask.run) method is a required entry point that will be called when the specified event is triggered; this method is required in every background task.</span></span>

> [!NOTE]
> <span data-ttu-id="8009b-125">Die hintergrundaufgabenklasse selbst&mdash;und alle anderen Klassen im hintergrundaufgabenprojekt&mdash;müssen **Öffentliche** Klassen, die **versiegelt** (oder **endgültigen**) sind.</span><span class="sxs-lookup"><span data-stu-id="8009b-125">The background task class itself&mdash;and all other classes in the background task project&mdash;need to be **public** classes that are **sealed** (or **final**).</span></span>

<span data-ttu-id="8009b-126">Der folgende Beispielcode zeigt einen sehr einfachen Startpunkt für eine hintergrundaufgabenklasse.</span><span class="sxs-lookup"><span data-stu-id="8009b-126">The following sample code shows a very basic starting point for a background task class.</span></span>

```csharp
// ExampleBackgroundTask.cs
using Windows.ApplicationModel.Background;

namespace Tasks
{
    public sealed class ExampleBackgroundTask : IBackgroundTask
    {
        public void Run(IBackgroundTaskInstance taskInstance)
        {
            
        }        
    }
}
```

```cppwinrt
// First, add ExampleBackgroundTask.idl, and then build.
// ExampleBackgroundTask.idl
namespace Tasks
{
    [default_interface]
    runtimeclass ExampleBackgroundTask : Windows.ApplicationModel.Background.IBackgroundTask
    {
        ExampleBackgroundTask();
    }
}

// ExampleBackgroundTask.h
#pragma once

#include "ExampleBackgroundTask.g.h"

namespace winrt::Tasks::implementation
{
    struct ExampleBackgroundTask : ExampleBackgroundTaskT<ExampleBackgroundTask>
    {
        ExampleBackgroundTask() = default;

        void Run(Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance);
    };
}

namespace winrt::Tasks::factory_implementation
{
    struct ExampleBackgroundTask : ExampleBackgroundTaskT<ExampleBackgroundTask, implementation::ExampleBackgroundTask>
    {
    };
}

// ExampleBackgroundTask.cpp
#include "pch.h"
#include "ExampleBackgroundTask.h"

namespace winrt::Tasks::implementation
{
    void ExampleBackgroundTask::Run(Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance)
    {
        throw hresult_not_implemented();
    }
}
```

```cpp
// ExampleBackgroundTask.h
#pragma once

using namespace Windows::ApplicationModel::Background;

namespace Tasks
{
    public ref class ExampleBackgroundTask sealed : public IBackgroundTask
    {

    public:
        ExampleBackgroundTask();

        virtual void Run(IBackgroundTaskInstance^ taskInstance);
        void OnCompleted(
            BackgroundTaskRegistration^ task,
            BackgroundTaskCompletedEventArgs^ args
        );
    };
}

// ExampleBackgroundTask.cpp
#include "ExampleBackgroundTask.h"

using namespace Tasks;

void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
{
}
```

4.  <span data-ttu-id="8009b-127">Wenn asynchroner Code in der Hintergrundaufgabe ausgeführt wird, muss in der Hintergrundaufgabe eine Verzögerung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8009b-127">If you run any asynchronous code in your background task, then your background task needs to use a deferral.</span></span> <span data-ttu-id="8009b-128">Wenn Sie keine Verzögerung verwenden, können dann die Hintergrundaufgabe unerwartet beendet werden, wenn die **Run** -Methode zurückgegeben wird, bevor alle asynchronen Vorgänge bis zum Abschluss ausgeführt worden ist.</span><span class="sxs-lookup"><span data-stu-id="8009b-128">If you don't use a deferral, then the background task process can terminate unexpectedly if the **Run** method returns before any asynchronous work has run to completion.</span></span>

<span data-ttu-id="8009b-129">Fordern Sie die Verzögerung in der **Run** -Methode vor Aufruf der asynchronen Methode.</span><span class="sxs-lookup"><span data-stu-id="8009b-129">Request the deferral in the **Run** method before calling the asynchronous method.</span></span> <span data-ttu-id="8009b-130">Speichern Sie die Verzögerung auf einen Daten Klassenmember, damit es von der asynchronen Methode zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8009b-130">Save the deferral to a class data member so that it can be accessed from the asynchronous method.</span></span> <span data-ttu-id="8009b-131">Deklarieren Sie das Objekt so, dass die Verzögerung nach Abschluss des asynchronen Codes abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="8009b-131">Declare the deferral complete after the asynchronous code completes.</span></span>

<span data-ttu-id="8009b-132">Der folgende Beispielcode ruft die Verzögerung, speichert sie und gibt sie nach Abschluss des asynchronen Codes frei.</span><span class="sxs-lookup"><span data-stu-id="8009b-132">The following sample code gets the deferral, saves it, and releases it when the asynchronous code is complete.</span></span>

```csharp
BackgroundTaskDeferral _deferral; // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation
public async void Run(IBackgroundTaskInstance taskInstance)
{
    _deferral = taskInstance.GetDeferral()
    //
    // TODO: Insert code to start one or more asynchronous methods using the
    //       await keyword, for example:
    //
    // await ExampleMethodAsync();
    //

    _deferral.Complete();
}
```

```cppwinrt
// ExampleBackgroundTask.h
...
private:
    Windows::ApplicationModel::Background::BackgroundTaskDeferral m_deferral{ nullptr };

// ExampleBackgroundTask.cpp
...
Windows::Foundation::IAsyncAction ExampleBackgroundTask::Run(
    Windows::ApplicationModel::Background::IBackgroundTaskInstance const& taskInstance)
{
    m_deferral = taskInstance.GetDeferral(); // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation.
    // TODO: Modify the following line of code to call a real async function.
    co_await ExampleCoroutineAsync(); // Run returns at this point, and resumes when ExampleCoroutineAsync completes.
    m_deferral.Complete();
}
```

```cpp
void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
{
    m_deferral = taskInstance->GetDeferral(); // Note: defined at class scope so that we can mark it complete inside the OnCancel() callback if we choose to support cancellation.

    //
    // TODO: Modify the following line of code to call a real async function.
    //       Note that the task<void> return type applies only to async
    //       actions. If you need to call an async operation instead, replace
    //       task<void> with the correct return type.
    //
    task<void> myTask(ExampleFunctionAsync());

    myTask.then([=]() {
        m_deferral->Complete();
    });
}
```

> [!NOTE]
> <span data-ttu-id="8009b-133">In C# werden asynchrone Methoden für Hintergrundaufgaben mithilfe der Schlagwörter **async/await** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="8009b-133">In C#, your background task's asynchronous methods can be called using the **async/await** keywords.</span></span> <span data-ttu-id="8009b-134">In C++ / CX ein ähnliches Ergebnis kann mithilfe einer Aufgabenabfolge erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="8009b-134">In C++/CX, a similar result can be achieved by using a task chain.</span></span>

<span data-ttu-id="8009b-135">Weitere Informationen zu asynchronen Mustern finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/mt187335).</span><span class="sxs-lookup"><span data-stu-id="8009b-135">For more information about asynchronous patterns, see [Asynchronous programming](https://msdn.microsoft.com/library/windows/apps/mt187335).</span></span> <span data-ttu-id="8009b-136">Weitere Beispiele zum Verhindern der vorzeitigen Beendigung einer Hintergrundaufgabe mithilfe von Verzögerungen finden Sie im [Beispiel zu Hintergrundaufgaben](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="8009b-136">For additional examples of how to use deferrals to keep a background task from stopping early, see the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

<span data-ttu-id="8009b-137">Die folgenden Schritte werden in einer Ihrer App-Klassen durchgeführt (beispielsweise in "MainPage.xaml.cs").</span><span class="sxs-lookup"><span data-stu-id="8009b-137">The following steps are completed in one of your app classes (for example, MainPage.xaml.cs).</span></span>

> [!NOTE]
> <span data-ttu-id="8009b-138">Sie können auch eine Funktion für die Registrierung von Hintergrundaufgaben dedicated erstellen&mdash;finden Sie unter [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="8009b-138">You can also create a function dedicated to registering background tasks&mdash;see [Register a background task](register-a-background-task.md).</span></span> <span data-ttu-id="8009b-139">In diesem Fall anstelle der nächsten drei Schritte können einfach den Auslöser konstruieren und der Registrierungsfunktion zusammen mit den Tasknamen Einstiegspunkt und (optional) eine Bedingung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8009b-139">In that case, instead of using the next three steps, you can simply construct the trigger and provide it to the registration function along with the task name, task entry point, and (optionally) a condition.</span></span>

## <a name="register-the-background-task-to-run"></a><span data-ttu-id="8009b-140">Registrieren der auszuführenden Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-140">Register the background task to run</span></span>

1.  <span data-ttu-id="8009b-141">Erfahren Sie, ob die Hintergrundaufgabe bereits registriert ist, durch die Eigenschaft [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="8009b-141">Find out whether the background task is already registered by iterating through the [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) property.</span></span> <span data-ttu-id="8009b-142">Dieser Schritt ist sehr wichtig. Sollte Ihre App nicht überprüfen, ob Hintergrundaufgaberegistrierungen vorhanden sind, könnte es passieren, dass sie die Aufgabe mehrere Male registriert, was zu Leistungseinbrüchen führt und die verfügbare CPU-Zeit der Aufgabe maximiert, bevor die Arbeit abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8009b-142">This step is important; if your app doesn't check for existing background task registrations, it could easily register the task multiple times, causing issues with performance and maxing out the task's available CPU time before work can complete.</span></span>

<span data-ttu-id="8009b-143">Das folgende Beispiel durchläuft die **AllTasks** -Eigenschaft und legt eine kennzeichenvariable auf "true", wenn die Aufgabe bereits registriert ist.</span><span class="sxs-lookup"><span data-stu-id="8009b-143">The following example iterates on the **AllTasks** property and sets a flag variable to true if the task is already registered.</span></span>

```csharp
var taskRegistered = false;
var exampleTaskName = "ExampleBackgroundTask";

foreach (var task in BackgroundTaskRegistration.AllTasks)
{
    if (task.Value.Name == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }
}
```

```cppwinrt
std::wstring exampleTaskName{ L"ExampleBackgroundTask" };

auto allTasks{ Windows::ApplicationModel::Background::BackgroundTaskRegistration::AllTasks() };

bool taskRegistered{ false };
for (auto const& task : allTasks)
{
    if (task.Value().Name() == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }
}

// The code in the next step goes here.
```

```cpp
boolean taskRegistered = false;
Platform::String^ exampleTaskName = "ExampleBackgroundTask";

auto iter = BackgroundTaskRegistration::AllTasks->First();
auto hascur = iter->HasCurrent;

while (hascur)
{
    auto cur = iter->Current->Value;

    if(cur->Name == exampleTaskName)
    {
        taskRegistered = true;
        break;
    }

    hascur = iter->MoveNext();
}
```

2.  <span data-ttu-id="8009b-144">Wenn die Hintergrundaufgabe noch nicht registriert ist, verwenden Sie [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768), um eine Instanz Ihrer Hintergrundaufgabe zu generieren.</span><span class="sxs-lookup"><span data-stu-id="8009b-144">If the background task is not already registered, use [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) to create an instance of your background task.</span></span> <span data-ttu-id="8009b-145">Bei dem Einstiegspunkt der Aufgabe sollte es sich um den Namen der Hintergrundaufgabenklasse mit dem Namespace als Präfix handeln.</span><span class="sxs-lookup"><span data-stu-id="8009b-145">The task entry point should be the name of your background task class prefixed by the namespace.</span></span>

<span data-ttu-id="8009b-146">Der Hintergrundaufgabenauslöser bestimmt, ob die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8009b-146">The background task trigger controls when the background task will run.</span></span> <span data-ttu-id="8009b-147">Eine Liste mit möglichen Auslösern erhalten Sie unter [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).</span><span class="sxs-lookup"><span data-stu-id="8009b-147">For a list of possible triggers, see [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).</span></span>

<span data-ttu-id="8009b-148">Beispielsweise wird dieser Code erstellt eine neue Hintergrundaufgabe und des Auslösers **TimeZoneChanged** ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="8009b-148">For example, this code creates a new background task and sets it to run when the **TimeZoneChanged** trigger occurs:</span></span>

```csharp
var builder = new BackgroundTaskBuilder();

builder.Name = exampleTaskName;
builder.TaskEntryPoint = "Tasks.ExampleBackgroundTask";
builder.SetTrigger(new SystemTrigger(SystemTriggerType.TimeZoneChange, false));
```

```cppwinrt
if (!taskRegistered)
{
    Windows::ApplicationModel::Background::BackgroundTaskBuilder builder;
    builder.Name(exampleTaskName);
    builder.TaskEntryPoint(L"Tasks.ExampleBackgroundTask");
    builder.SetTrigger(Windows::ApplicationModel::Background::SystemTrigger{
        Windows::ApplicationModel::Background::SystemTriggerType::TimeZoneChange, false });
    // The code in the next step goes here.
}
```

```cpp
auto builder = ref new BackgroundTaskBuilder();

builder->Name = exampleTaskName;
builder->TaskEntryPoint = "Tasks.ExampleBackgroundTask";
builder->SetTrigger(ref new SystemTrigger(SystemTriggerType::TimeZoneChange, false));
```

3.  <span data-ttu-id="8009b-149">Sie können eine Bedingung hinzufügen, die bestimmt, wann Ihre Aufgabe ausgeführt wird, nachdem das Auslöseereignis eintritt (optional).</span><span class="sxs-lookup"><span data-stu-id="8009b-149">You can add a condition to control when your task will run after the trigger event occurs (optional).</span></span> <span data-ttu-id="8009b-150">Wenn Sie zum Beispiel möchten, dass die Aufgabe erst ausgeführt wird, wenn der Benutzer anwesend ist, verwenden Sie die Bedingung **UserPresent**.</span><span class="sxs-lookup"><span data-stu-id="8009b-150">For example, if you don't want the task to run until the user is present, use the condition **UserPresent**.</span></span> <span data-ttu-id="8009b-151">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="8009b-151">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

<span data-ttu-id="8009b-152">Der folgende Beispielcode weist eine Bedingung zu, die die Anwesenheit des Benutzers voraussetzt:</span><span class="sxs-lookup"><span data-stu-id="8009b-152">The following sample code assigns a condition requiring the user to be present:</span></span>

```csharp
builder.AddCondition(new SystemCondition(SystemConditionType.UserPresent));
```

```cppwinrt
builder.AddCondition(Windows::ApplicationModel::Background::SystemCondition{ Windows::ApplicationModel::Background::SystemConditionType::UserPresent });
// The code in the next step goes here.
```

```cpp
builder->AddCondition(ref new SystemCondition(SystemConditionType::UserPresent));
```

4.  <span data-ttu-id="8009b-153">Registrieren Sie die Hintergrundaufgabe, indem Sie die Register-Methode für das [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="8009b-153">Register the background task by calling the Register method on the [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) object.</span></span> <span data-ttu-id="8009b-154">Speichern Sie das [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Ergebnis, sodass es im nächsten Schritt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="8009b-154">Store the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786) result so it can be used in the next step.</span></span>

<span data-ttu-id="8009b-155">Der folgende Code registriert die Hintergrundaufgabe und speichert das Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="8009b-155">The following code registers the background task and stores the result:</span></span>

```csharp
BackgroundTaskRegistration task = builder.Register();
```

```cppwinrt
Windows::ApplicationModel::Background::BackgroundTaskRegistration task{ builder.Register() };
```

```cpp
BackgroundTaskRegistration^ task = builder->Register();
```

> [!NOTE]
> <span data-ttu-id="8009b-156">Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrundtriggertypen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="8009b-156">Universal Windows apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="8009b-157">Verwenden Sie den **ServicingComplete**-Trigger (siehe [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)) zum Ausführen von Konfigurationsänderungen nach dem Update wie Migrieren der Datenbank der App und Registrieren von Hintergrundaufgaben, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8009b-157">To ensure that your Universal Windows app continues to run properly after you release an update, use the **ServicingComplete** (see [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)) trigger to perform any post-update configuration changes such as migrating the app's database and registering background tasks.</span></span> <span data-ttu-id="8009b-158">Es empfiehlt sich, die Registrierung von Hintergrundaufgaben im Zusammenhang mit der vorherigen Version der App aufzuheben (siehe [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471)) und die Hintergrundaufgaben für die neue Version der App zu registrieren (siehe [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485)).</span><span class="sxs-lookup"><span data-stu-id="8009b-158">It is best practice to unregister background tasks associated with the previous version of the app (see [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471)) and register background tasks for the new version of the app (see [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485)) at this time.</span></span>

<span data-ttu-id="8009b-159">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="8009b-159">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

## <a name="handle-background-task-completion-using-event-handlers"></a><span data-ttu-id="8009b-160">Behandeln des Abschlusses der Hintergrundaufgabe mithilfe von Ereignishandlern</span><span class="sxs-lookup"><span data-stu-id="8009b-160">Handle background task completion using event handlers</span></span>

<span data-ttu-id="8009b-161">Sie sollten eine Methode mit dem [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element registrieren, damit Ihre App Ergebnisse von der Hintergrundaufgabe abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="8009b-161">You should register a method with the [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781), so that your app can get results from the background task.</span></span> <span data-ttu-id="8009b-162">Wenn die app gestartet oder fortgesetzt wird, wird die markierte Methode aufgerufen, wenn die Hintergrundaufgabe seit dem letzten abgeschlossen hat, die die app im Vordergrund befand.</span><span class="sxs-lookup"><span data-stu-id="8009b-162">When the app is launched or resumed, the marked method will be called if the background task has completed since the last time the app was in the foreground.</span></span> <span data-ttu-id="8009b-163">(Die OnCompleted-Methode wird sofort aufgerufen, wenn die Hintergrundaufgabe abgeschlossen wird, während sich Ihre App im Vordergrund befindet.)</span><span class="sxs-lookup"><span data-stu-id="8009b-163">(The OnCompleted method will be called immediately if the background task completes while your app is currently in the foreground.)</span></span>

1.  <span data-ttu-id="8009b-164">Schreiben Sie eine OnCompleted-Methode, um den Abschluss von Hintergrundaufgaben zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="8009b-164">Write an OnCompleted method to handle the completion of background tasks.</span></span> <span data-ttu-id="8009b-165">Das Ergebnis der Hintergrundaufgabe kann z.B. eine Aktualisierung der Benutzeroberfläche auslösen.</span><span class="sxs-lookup"><span data-stu-id="8009b-165">For example, the background task result might cause a UI update.</span></span> <span data-ttu-id="8009b-166">Das hier gezeigte Methodenprofil ist für die OnCompleted-Ereignishandlermethode erforderlich, obwohl dieses Beispiel nicht den *args*-Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="8009b-166">The method footprint shown here is required for the OnCompleted event handler method, even though this example does not use the *args* parameter.</span></span>

<span data-ttu-id="8009b-167">Der folgende Beispielcode erkennt den Abschluss der Hintergrundaufgabe und ruft eine Beispielmethode zur Aktualisierung der Benutzeroberfläche auf, die eine Meldungszeichenfolge erfordert.</span><span class="sxs-lookup"><span data-stu-id="8009b-167">The following sample code recognizes background task completion and calls an example UI update method that takes a message string.</span></span>

```csharp
private void OnCompleted(IBackgroundTaskRegistration task, BackgroundTaskCompletedEventArgs args)
{
    var settings = Windows.Storage.ApplicationData.Current.LocalSettings;
    var key = task.TaskId.ToString();
    var message = settings.Values[key].ToString();
    UpdateUI(message);
}
```

```cppwinrt
void UpdateUI(winrt::hstring const& message)
{
    MyTextBlock().Dispatcher().RunAsync(Windows::UI::Core::CoreDispatcherPriority::Normal, [=]()
    {
        MyTextBlock().Text(message);
    });
}

void OnCompleted(
    Windows::ApplicationModel::Background::BackgroundTaskRegistration const& sender,
    Windows::ApplicationModel::Background::BackgroundTaskCompletedEventArgs const& /* args */)
{
    // You'll previously have inserted this key into local settings.
    auto settings{ Windows::Storage::ApplicationData::Current().LocalSettings().Values() };
    auto key{ winrt::to_hstring(sender.TaskId()) };
    auto message{ winrt::unbox_value<winrt::hstring>(settings.Lookup(key)) };

    UpdateUI(message);
}
```

```cpp
void MainPage::OnCompleted(BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
{
    auto settings = ApplicationData::Current->LocalSettings->Values;
    auto key = task->TaskId.ToString();
    auto message = dynamic_cast<String^>(settings->Lookup(key));
    UpdateUI(message);
}
```

> [!NOTE]
> <span data-ttu-id="8009b-168">Aktualisierungen der Benutzeroberfläche sollten asynchron durchgeführt werden, um den Benutzeroberflächenthread nicht zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="8009b-168">UI updates should be performed asynchronously, to avoid holding up the UI thread.</span></span> <span data-ttu-id="8009b-169">Ein Beispiel dazu finden Sie in der UpdateUI-Methode im [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="8009b-169">For an example, see the UpdateUI method in the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

2.  <span data-ttu-id="8009b-170">Gehen Sie dorthin zurück, wo Sie die Hintergrundaufgabe registriert haben.</span><span class="sxs-lookup"><span data-stu-id="8009b-170">Go back to where you registered the background task.</span></span> <span data-ttu-id="8009b-171">Fügen Sie nach dieser Codezeile ein neues [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="8009b-171">After that line of code, add a new [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781) object.</span></span> <span data-ttu-id="8009b-172">Stellen Sie Ihre OnCompleted-Methode als Parameter für den **BackgroundTaskCompletedEventHandler**-Konstruktor zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8009b-172">Provide your OnCompleted method as the parameter for the **BackgroundTaskCompletedEventHandler** constructor.</span></span>

<span data-ttu-id="8009b-173">Der folgende Beispielcode fügt dem [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Element ein [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element hinzu:</span><span class="sxs-lookup"><span data-stu-id="8009b-173">The following sample code adds a [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781) to the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786):</span></span>

```csharp
task.Completed += new BackgroundTaskCompletedEventHandler(OnCompleted);
```

```cppwinrt
task.Completed({ this, &MainPage::OnCompleted });
```

```cpp
task->Completed += ref new BackgroundTaskCompletedEventHandler(this, &MainPage::OnCompleted);
```

## <a name="declare-in-the-app-manifest-that-your-app-uses-background-tasks"></a><span data-ttu-id="8009b-174">Deklarieren Sie im app-Manifest, dass Ihre app Hintergrundaufgaben verwendet</span><span class="sxs-lookup"><span data-stu-id="8009b-174">Declare in the app manifest that your app uses background tasks</span></span>

<span data-ttu-id="8009b-175">Bevor Ihre App Hintergrundaufgaben ausführen kann, müssen Sie alle Hintergrundaufgaben im App-Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8009b-175">Before your app can run background tasks, you must declare each background task in the app manifest.</span></span> <span data-ttu-id="8009b-176">Wenn Ihre app versucht, eine Hintergrundaufgabe mit einem Trigger zu registrieren, die nicht im Manifest aufgeführt ist, wird die Registrierung der Hintergrundaufgabe mit dem Fehler "-Runtime-Klasse nicht registriert" fehl.</span><span class="sxs-lookup"><span data-stu-id="8009b-176">If your app attempts to register a background task with a trigger that isn't listed in the manifest, the registration of the background task will fail with a "runtime class not registered" error.</span></span>

1.  <span data-ttu-id="8009b-177">Öffnen Sie den Paketmanifest-Designer durch Öffnen der Datei namens „Package.appxmanifest“.</span><span class="sxs-lookup"><span data-stu-id="8009b-177">Open the package manifest designer by opening the file named Package.appxmanifest.</span></span>
2.  <span data-ttu-id="8009b-178">Öffnen Sie die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="8009b-178">Open the **Declarations** tab.</span></span>
3.  <span data-ttu-id="8009b-179">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Hintergrundaufgaben** aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="8009b-179">From the **Available Declarations** drop-down, select **Background Tasks** and click **Add**.</span></span>
4.  <span data-ttu-id="8009b-180">Aktivieren Sie das Kontrollkästchen **Systemereignis**.</span><span class="sxs-lookup"><span data-stu-id="8009b-180">Select the **System event** checkbox.</span></span>
5.  <span data-ttu-id="8009b-181">In der **Einstiegspunkt:** Textbox, geben Sie den Namespace und den Namen der Hintergrundklasse in diesem Beispiel Tasks.ExampleBackgroundTask lautet.</span><span class="sxs-lookup"><span data-stu-id="8009b-181">In the **Entry point:** textbox, enter the namespace and name of your background class which is for this example is Tasks.ExampleBackgroundTask.</span></span>
6.  <span data-ttu-id="8009b-182">Schließen Sie den Manifest-Designer.</span><span class="sxs-lookup"><span data-stu-id="8009b-182">Close the manfiest designer.</span></span>

<span data-ttu-id="8009b-183">Das folgende Erweiterungselement wird zur Datei „Package.appxmanifest“ hinzugefügt, um die Hintergrundaufgabe zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="8009b-183">The following Extensions element is added to your Package.appxmanifest file to register the background task:</span></span>

```xml
<Extensions>
  <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.ExampleBackgroundTask">
    <BackgroundTasks>
      <Task Type="systemEvent" />
    </BackgroundTasks>
  </Extension>
</Extensions>
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="8009b-184">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8009b-184">Summary and next steps</span></span>

<span data-ttu-id="8009b-185">Sie sollten jetzt über die Grundlagen verfügen, um eine Hintergrundaufgabenklasse zu schreiben, die Hintergrundaufgabe in Ihrer App zu registrieren und Ihre App so zu konfigurieren, dass Sie den Abschluss der Hintergrundaufgabe erkennt.</span><span class="sxs-lookup"><span data-stu-id="8009b-185">You should now understand the basics of how to write a background task class, how to register the background task from within your app, and how to make your app recognize when the background task is complete.</span></span> <span data-ttu-id="8009b-186">Sie sollten auch mit der Aktualisierung des Anwendungsmanifests vertraut sein, damit Ihre App die Hintergrundaufgabe erfolgreich registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="8009b-186">You should also understand how to update the application manifest so that your app can successfully register the background task.</span></span>

> [!NOTE]
> <span data-ttu-id="8009b-187">Laden Sie das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunter, um ähnliche Codebeispiele im Kontext einer vollständigen und stabilen UWP-App (Universelle Windows-Plattform) mit Hintergrundaufgaben zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8009b-187">Download the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) to see similar code examples in the context of a complete and robust UWP app that uses background tasks.</span></span>

<span data-ttu-id="8009b-188">Eine API-Referenz, konzeptionelle Richtlinien zu Hintergrundaufgaben und ausführlichere Anweisungen zum Schreiben von Apps, die Hintergrundaufgaben verwenden, finden Sie unter den folgenden verwandten Themen:</span><span class="sxs-lookup"><span data-stu-id="8009b-188">See the following related topics for API reference, background task conceptual guidance, and more detailed instructions for writing apps that use background tasks.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8009b-189">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8009b-189">Related topics</span></span>

**<span data-ttu-id="8009b-190">Ausführliche Themen mit Anweisungen zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8009b-190">Detailed background task instructional topics</span></span>**

* [<span data-ttu-id="8009b-191">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8009b-191">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="8009b-192">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-192">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="8009b-193">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-193">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="8009b-194">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="8009b-194">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="8009b-195">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-195">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="8009b-196">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8009b-196">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="8009b-197">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="8009b-197">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* <span data-ttu-id="8009b-198">[Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="8009b-198">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="8009b-199">Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-199">Convert an out-of-process background task to an in-process background task</span></span>](convert-out-of-process-background-task.md)  

**<span data-ttu-id="8009b-200">Ratschläge zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8009b-200">Background task guidance</span></span>**

* [<span data-ttu-id="8009b-201">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="8009b-201">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="8009b-202">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="8009b-202">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="8009b-203">So wird’s gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="8009b-203">How to trigger suspend, resume, and background events in UWP apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)

**<span data-ttu-id="8009b-204">Hintergrundaufgabe – API-Referenz</span><span class="sxs-lookup"><span data-stu-id="8009b-204">Background Task API Reference</span></span>**

* [**<span data-ttu-id="8009b-205">Windows.ApplicationModel.Background</span><span class="sxs-lookup"><span data-stu-id="8009b-205">Windows.ApplicationModel.Background</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)
