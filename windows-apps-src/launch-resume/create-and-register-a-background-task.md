---
author: TylerMSFT
title: Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe
description: "Erstellen Sie eine Out-of-Process-Hintergrundaufgabenklasse, und registrieren Sie sie für die Ausführung, wenn Ihre App nicht im Vordergrund ausgeführt wird."
ms.assetid: 4F98F6A3-0D3D-4EFB-BA8E-30ED37AE098B
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 1974c90b89a34f3252face47b9f18786b638adf8
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="create-and-register-an-out-of-process-background-task"></a><span data-ttu-id="665cf-104">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="665cf-104">Create and register an out-of-process background task</span></span>

<span data-ttu-id="665cf-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="665cf-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="665cf-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="665cf-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="665cf-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="665cf-107">Important APIs</span></span>**

-   [**<span data-ttu-id="665cf-108">IBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="665cf-108">IBackgroundTask</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**<span data-ttu-id="665cf-109">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="665cf-109">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
-   [**<span data-ttu-id="665cf-110">BackgroundTaskCompletedEventHandler</span><span class="sxs-lookup"><span data-stu-id="665cf-110">BackgroundTaskCompletedEventHandler</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224781)

<span data-ttu-id="665cf-111">Erstellen Sie eine Hintergrundaufgabenklasse, und registrieren Sie diese für die Ausführung, wenn sich die App nicht im Vordergrund befindet.</span><span class="sxs-lookup"><span data-stu-id="665cf-111">Create a background task class and register it to run when your app is not in the foreground.</span></span> <span data-ttu-id="665cf-112">In diesem Thema wird gezeigt, wie Sie eine Hintergrundaufgabe erstellen und registrieren, die in einem vom App-Prozess getrennten Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="665cf-112">This topic demonstrates how to create and register a background task that runs in a separate process than your app's process.</span></span> <span data-ttu-id="665cf-113">Informationen zum Ausführen von Hintergrundarbeiten direkt in der Vordergrundanwendung finden Sie unter [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="665cf-113">To do background work directly in the foreground application, see [Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>

> [!Note]
> <span data-ttu-id="665cf-114">Wenn Sie eine Hintergrundaufgabe zur Medienwiedergabe im Hintergrund verwenden, finden Sie unter [Wiedergeben von Medien im Hintergrund](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) Informationen zu Verbesserungen in Windows10, Version1607, die dies wesentlich erleichtern.</span><span class="sxs-lookup"><span data-stu-id="665cf-114">If you use a background task to play media in the background, see [Play media in the background](https://msdn.microsoft.com/windows/uwp/audio-video-camera/background-audio) for information about improvements in Windows 10, version 1607, that make it much easier.</span></span>

## <a name="create-the-background-task-class"></a><span data-ttu-id="665cf-115">Erstellen einer Hintergrundaufgabenklasse</span><span class="sxs-lookup"><span data-stu-id="665cf-115">Create the Background Task class</span></span>

<span data-ttu-id="665cf-116">Sie können Code im Hintergrund ausführen, indem Sie Klassen schreiben, die die [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="665cf-116">You can run code in the background by writing classes that implement the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface.</span></span> <span data-ttu-id="665cf-117">Dieser Code wird ausgeführt, wenn ein bestimmtes Ereignis beispielsweise durch [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) oder [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517) ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="665cf-117">This code will run when a specific event is triggered by using, for example, [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839) or [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/hh700517).</span></span>

<span data-ttu-id="665cf-118">Die folgenden Schritte zeigen, wie Sie eine neue Klasse zum Implementieren der [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle schreiben.</span><span class="sxs-lookup"><span data-stu-id="665cf-118">The following steps show you how to write a new class that implements the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface.</span></span> <span data-ttu-id="665cf-119">Erstellen Sie zunächst ein neues Projekt in Ihrer Projektmappe für Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="665cf-119">Before getting started, create a new project in your solution for background tasks.</span></span> <span data-ttu-id="665cf-120">Fügen Sie zu Ihrer Hintergrundaufgabe eine neue leere Klasse hinzu, und importieren Sie den Namespace [Windows.ApplicationModel.Background](https://msdn.microsoft.com/library/windows/apps/br224847).</span><span class="sxs-lookup"><span data-stu-id="665cf-120">Add a new empty class for your background task and import the [Windows.ApplicationModel.Background](https://msdn.microsoft.com/library/windows/apps/br224847) namespace.</span></span>

1.  <span data-ttu-id="665cf-121">Erstellen Sie ein neues Projekt für Hintergrundaufgaben, und fügen Sie es zu Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="665cf-121">Create a new project for background tasks and add it to your solution.</span></span> <span data-ttu-id="665cf-122">Klicken Sie zu diesem Zweck mit der rechten Maustaste auf Ihren Projektmappenknoten im **Projektmappen-Explorer**, und wählen Sie „Hinzufügen &gt; Neues Projekt“ aus.</span><span class="sxs-lookup"><span data-stu-id="665cf-122">To do this, right-click on your solution node in the **Solution Explorer** and select Add-&gt;New Project.</span></span> <span data-ttu-id="665cf-123">Wählen Sie dann den Projekttyp **Komponente für Windows-Runtime (Universal Windows)** aus, geben Sie dem Projekt einen Namen, und klicken Sie auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="665cf-123">Then select the **Windows Runtime Component (Universal Windows)** project type, name the project, and click OK.</span></span>
2.  <span data-ttu-id="665cf-124">Verweisen Sie auf das Hintergrundaufgabenprojekt aus dem Projekt für UWP-Apps (Universelle Windows-Plattform).</span><span class="sxs-lookup"><span data-stu-id="665cf-124">Reference the background tasks project from your Universal Windows Platform (UWP) app project.</span></span>

    <span data-ttu-id="665cf-125">Klicken Sie für eine C++-App mit der rechten Maustaste auf Ihr App-Projekt, und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="665cf-125">For a C++ app, right-click on your app project and select **Properties**.</span></span> <span data-ttu-id="665cf-126">Gehen Sie dann zu **Allgemeine Eigenschaften**, und klicken Sie auf **Neuen Verweis hinzufügen**. Aktivieren Sie das Kontrollkästchen neben Ihrem Hintergrundaufgabenprojekt, und klicken Sie in beiden Dialogfeldern auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="665cf-126">Then go to **Common Properties** and click **Add New Reference**, check the box next to your background tasks project, and click **OK** on both dialogs.</span></span>

    <span data-ttu-id="665cf-127">Klicken Sie für eine C#-App in Ihrem App-Projekt mit der rechten Maustaste auf **Verweise**, und wählen Sie **Neuen Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="665cf-127">For a C# app, in your app project, right click on **References** and select **Add New Reference**.</span></span> <span data-ttu-id="665cf-128">Wählen Sie unter **Projektmappe** die Option **Projekte**. Wählen Sie dann den Namen Ihres Hintergrundaufgabenprojekts aus, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="665cf-128">Under **Solution**, select **Projects** and then select the name of your background task project and click **Ok**.</span></span>

3.  <span data-ttu-id="665cf-129">Erstellen Sie eine neue Klasse zum Implementieren der Schnittstelle [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span><span class="sxs-lookup"><span data-stu-id="665cf-129">Create a new class that implements the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface.</span></span> <span data-ttu-id="665cf-130">Die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811)-Methode ist ein erforderlicher Einstiegspunkt und wird aufgerufen, wenn das angegebene Ereignis ausgelöst wird. Diese Methode ist in jeder Hintergrundaufgabe erforderlich.</span><span class="sxs-lookup"><span data-stu-id="665cf-130">The [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method is a required entry point that will be called when the specified event is triggered; this method is required in every background task.</span></span>

    > [!NOTE]
    > <span data-ttu-id="665cf-131">Die Hintergrundaufgabenklasse selbst sowie alle anderen Klassen im Hintergrundaufgabenprojekt müssen **öffentliche** Klassen und **versiegelt** sein.</span><span class="sxs-lookup"><span data-stu-id="665cf-131">The background task class itself - and all other classes in the background task project - need to be **public** classes that are **sealed**.</span></span>

    <span data-ttu-id="665cf-132">Der folgende Beispielcode zeigt einen sehr einfachen Startpunkt für eine Hintergrundaufgabenklasse:</span><span class="sxs-lookup"><span data-stu-id="665cf-132">The following sample code shows a very basic starting point for a background task class:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     //
    >     // ExampleBackgroundTask.cs
    >     //
    >
    >     using Windows.ApplicationModel.Background;
    >
    >     namespace Tasks
    >     {
    >         public sealed class ExampleBackgroundTask : IBackgroundTask
    >         {
    >             public void Run(IBackgroundTaskInstance taskInstance)
    >             {
    >                 
    >             }        
    >         }
    >     }
    > ```
    > ```cpp
    >     //
    >     // ExampleBackgroundTask.h
    >     //
    >
    >     #pragma once
    >
    >     using namespace Windows::ApplicationModel::Background;
    >
    >     namespace RuntimeComponent1
    >     {
    >         public ref class ExampleBackgroundTask sealed : public IBackgroundTask
    >         {
    >
    >         public:
    >             ExampleBackgroundTask();
    >
    >             virtual void Run(IBackgroundTaskInstance^ taskInstance);
    >             void OnCompleted(
    >                     BackgroundTaskRegistration^ task,
    >                     BackgroundTaskCompletedEventArgs^ args
    >                     );
    >         };
    >     }
    >
    >     //
    >     // ExampleBackgroundTask.cpp
    >     //
    >
    >     #include "ExampleBackgroundTask.h"
    >
    >     using namespace Tasks;
    >
    >     void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
    >     {
    >
    >     }
    >  ```

4.  <span data-ttu-id="665cf-133">Wenn asynchroner Code in der Hintergrundaufgabe ausgeführt wird, muss in der Hintergrundaufgabe eine Verzögerung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="665cf-133">If you run any asynchronous code in your background task, then your background task needs to use a deferral.</span></span> <span data-ttu-id="665cf-134">Wenn Sie keine Verzögerung verwenden, kann die Ausführung der Hintergrundaufgabe unerwartet beendet werden, wenn die Run-Methode vor dem Aufruf der asynchronen Methode abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="665cf-134">If you don't use a deferral, then the background task process can terminate unexpectedly if the Run method completes before your asynchronous method call has completed.</span></span>

    <span data-ttu-id="665cf-135">Implementieren Sie die Verzögerung in der Run-Methode vor Aufruf der asynchronen Methode.</span><span class="sxs-lookup"><span data-stu-id="665cf-135">Request the deferral in the Run method before calling the asynchronous method.</span></span> <span data-ttu-id="665cf-136">Speichern Sie die Verzögerung in einer globalen Variable, sodass die asynchrone Methode darauf zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="665cf-136">Save the deferral to a global variable so it can be accessed from the asynchronous method.</span></span> <span data-ttu-id="665cf-137">Deklarieren Sie das Objekt so, dass die Verzögerung nach Abschluss des asynchronen Codes abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="665cf-137">Declare the deferral complete after the asynchronous code completes.</span></span>

    <span data-ttu-id="665cf-138">Der folgende Beispielcode ruft die Verzögerung auf, speichert sie und gibt sie nach Abschluss des asynchronen Codes frei:</span><span class="sxs-lookup"><span data-stu-id="665cf-138">The following sample code gets the deferral, saves it, and releases it when the asynchronous code is complete:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     BackgroundTaskDeferral _deferral; // Note: defined at class scope so we can mark it complete inside the OnCancel() callback if we choose to support cancellation
    >     public async void Run(IBackgroundTaskInstance taskInstance)
    >     {
    >         _deferral = taskInstance.GetDeferral()
    >         //
    >         // TODO: Insert code to start one or more asynchronous methods using the
    >         //       await keyword, for example:
    >         //
    >         // await ExampleMethodAsync();
    >         //
    >         
    >         _deferral.Complete();
    >     }
    > ```
    > ```cpp
    >     BackgroundTaskDeferral^ deferral = taskInstance->GetDeferral(); // Note: defined at class scope so we can mark it complete inside the OnCancel() callback if we choose to support cancellation
    >     void ExampleBackgroundTask::Run(IBackgroundTaskInstance^ taskInstance)
    >     {
    >         //
    >         // TODO: Modify the following line of code to call a real async function.
    >         //       Note that the task<void> return type applies only to async
    >         //       actions. If you need to call an async operation instead, replace
    >         //       task<void> with the correct return type.
    >         //
    >         task<void> myTask(ExampleFunctionAsync());
    >         
    >         myTask.then([=] () {
    >             deferral->Complete();
    >         });
    >     }
    > ```

> [!NOTE]
> <span data-ttu-id="665cf-139">In C# werden asynchrone Methoden für Hintergrundaufgaben mithilfe der Schlagwörter **async/await** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="665cf-139">In C#, your background task's asynchronous methods can be called using the **async/await** keywords.</span></span> <span data-ttu-id="665cf-140">In C++ kann mit einer Aufgabenfolge ein ähnliches Ergebnis erzielt werden.</span><span class="sxs-lookup"><span data-stu-id="665cf-140">In C++, a similar result can be achieved by using a task chain.</span></span>

<span data-ttu-id="665cf-141">Weitere Informationen zu asynchronen Mustern finden Sie unter [Asynchrone Programmierung](https://msdn.microsoft.com/library/windows/apps/mt187335).</span><span class="sxs-lookup"><span data-stu-id="665cf-141">For more information about asynchronous patterns, see [Asynchronous programming](https://msdn.microsoft.com/library/windows/apps/mt187335).</span></span> <span data-ttu-id="665cf-142">Weitere Beispiele zum Verhindern der vorzeitigen Beendigung einer Hintergrundaufgabe mithilfe von Verzögerungen finden Sie im [Beispiel zu Hintergrundaufgaben](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="665cf-142">For additional examples of how to use deferrals to keep a background task from stopping early, see the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>

<span data-ttu-id="665cf-143">Die folgenden Schritte werden in einer Ihrer App-Klassen durchgeführt (beispielsweise in "MainPage.xaml.cs").</span><span class="sxs-lookup"><span data-stu-id="665cf-143">The following steps are completed in one of your app classes (for example, MainPage.xaml.cs).</span></span>

> [!NOTE]
> <span data-ttu-id="665cf-144">Sie können auch eine Funktion erstellen, die sich nur um das Registrieren von Hintergrundaufgaben kümmert. Siehe dazu [Registrieren einer Hintergrundaufgabe](register-a-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="665cf-144">You can also create a function dedicated to registering background tasks - see [Register a background task](register-a-background-task.md).</span></span> <span data-ttu-id="665cf-145">In einem solchen Fall können Sie die nächsten drei Schritte überspringen, einfach den Auslöser konstruieren und der Registrierungsfunktion zur Verfügung stellen, zusammen mit dem Aufgabennamen, dem entsprechenden Einstiegspunkt und, optional, einer Bedingung.</span><span class="sxs-lookup"><span data-stu-id="665cf-145">In that case, instead of using the next 3 steps, you can simply construct the trigger and provide it to the registration function along with the task name, task entry point, and (optionally) a condition.</span></span>

## <a name="register-the-background-task-to-run"></a><span data-ttu-id="665cf-146">Registrieren der auszuführenden Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-146">Register the background task to run</span></span>

1.  <span data-ttu-id="665cf-147">Finden Sie heraus, ob die Hintergrundaufgabe bereits registriert ist, indem Sie die [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787)-Eigenschaft durchlaufen lassen.</span><span class="sxs-lookup"><span data-stu-id="665cf-147">Find out if the background task is already registered by iterating through the [**BackgroundTaskRegistration.AllTasks**](https://msdn.microsoft.com/library/windows/apps/br224787) property.</span></span> <span data-ttu-id="665cf-148">Dieser Schritt ist sehr wichtig. Sollte Ihre App nicht überprüfen, ob Hintergrundaufgaberegistrierungen vorhanden sind, könnte es passieren, dass sie die Aufgabe mehrere Male registriert, was zu Leistungseinbrüchen führt und die verfügbare CPU-Zeit der Aufgabe maximiert, bevor die Arbeit abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="665cf-148">This step is important; if your app doesn't check for existing background task registrations, it could easily register the task multiple times, causing issues with performance and maxing out the task's available CPU time before work can complete.</span></span>

    <span data-ttu-id="665cf-149">Das folgende Beispiel durchläuft die AllTasks-Eigenschaft und legt eine Kennzeichenvariable auf „true“ fest, wenn die Aufgabe bereits registriert ist:</span><span class="sxs-lookup"><span data-stu-id="665cf-149">The following example iterates on the AllTasks property and sets a flag variable to true if the task is already registered:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     var taskRegistered = false;
    >     var exampleTaskName = "ExampleBackgroundTask";
    >
    >     foreach (var task in BackgroundTaskRegistration.AllTasks)
    >     {
    >         if (task.Value.Name == exampleTaskName)
    >         {
    >             taskRegistered = true;
    >             break;
    >         }
    >     }
    > ```
    > ```cpp
    >     boolean taskRegistered = false;
    >     Platform::String^ exampleTaskName = "ExampleBackgroundTask";
    >
    >     auto iter = BackgroundTaskRegistration::AllTasks->First();
    >     auto hascur = iter->HasCurrent;
    >
    >     while (hascur)
    >     {
    >         auto cur = iter->Current->Value;
    >
    >         if(cur->Name == exampleTaskName)
    >         {
    >             taskRegistered = true;
    >             break;
    >         }
    >
    >         hascur = iter->MoveNext();
    >     }
    > ```

2.  <span data-ttu-id="665cf-150">Wenn die Hintergrundaufgabe noch nicht registriert ist, verwenden Sie [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768), um eine Instanz Ihrer Hintergrundaufgabe zu generieren.</span><span class="sxs-lookup"><span data-stu-id="665cf-150">If the background task is not already registered, use [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) to create an instance of your background task.</span></span> <span data-ttu-id="665cf-151">Bei dem Einstiegspunkt der Aufgabe sollte es sich um den Namen der Hintergrundaufgabenklasse mit dem Namespace als Präfix handeln.</span><span class="sxs-lookup"><span data-stu-id="665cf-151">The task entry point should be the name of your background task class prefixed by the namespace.</span></span>

    <span data-ttu-id="665cf-152">Der Hintergrundaufgabenauslöser bestimmt, ob die Hintergrundaufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="665cf-152">The background task trigger controls when the background task will run.</span></span> <span data-ttu-id="665cf-153">Eine Liste mit möglichen Auslösern erhalten Sie unter [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).</span><span class="sxs-lookup"><span data-stu-id="665cf-153">For a list of possible triggers, see [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/br224839).</span></span>

    <span data-ttu-id="665cf-154">Dieser Code generiert beispielsweise eine neue Hintergrundaufgabe, die beim Aktivieren des **TimeZoneChanged**-Auslösers ausgelöst wird:</span><span class="sxs-lookup"><span data-stu-id="665cf-154">For example, this code creates a new background task and sets it to run when the **TimeZoneChanged** trigger is fired:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     var builder = new BackgroundTaskBuilder();
    >
    >     builder.Name = exampleTaskName;
    >     builder.TaskEntryPoint = "RuntimeComponent1.ExampleBackgroundTask";
    >     builder.SetTrigger(new SystemTrigger(SystemTriggerType.TimeZoneChange, false));
    > ```
    > ```cpp
    >     auto builder = ref new BackgroundTaskBuilder();
    >
    >     builder->Name = exampleTaskName;
    >     builder->TaskEntryPoint = "RuntimeComponent1.ExampleBackgroundTask";
    >     builder->SetTrigger(ref new SystemTrigger(SystemTriggerType::TimeZoneChange, false));
    > ```

3.  <span data-ttu-id="665cf-155">Sie können eine Bedingung hinzufügen, die bestimmt, wann Ihre Aufgabe ausgeführt wird, nachdem das Auslöseereignis eintritt (optional).</span><span class="sxs-lookup"><span data-stu-id="665cf-155">You can add a condition to control when your task will run after the trigger event occurs (optional).</span></span> <span data-ttu-id="665cf-156">Wenn Sie zum Beispiel möchten, dass die Aufgabe erst ausgeführt wird, wenn der Benutzer anwesend ist, verwenden Sie die Bedingung **UserPresent**.</span><span class="sxs-lookup"><span data-stu-id="665cf-156">For example, if you don't want the task to run until the user is present, use the condition **UserPresent**.</span></span> <span data-ttu-id="665cf-157">Eine Liste mit möglichen Bedingungen finden Sie in [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span><span class="sxs-lookup"><span data-stu-id="665cf-157">For a list of possible conditions, see [**SystemConditionType**](https://msdn.microsoft.com/library/windows/apps/br224835).</span></span>

    <span data-ttu-id="665cf-158">Der folgende Beispielcode weist eine Bedingung zu, die die Anwesenheit des Benutzers voraussetzt:</span><span class="sxs-lookup"><span data-stu-id="665cf-158">The following sample code assigns a condition requiring the user to be present:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     builder.AddCondition(new SystemCondition(SystemConditionType.UserPresent));
    > ```
    > ```cpp
    >     builder->AddCondition(ref new SystemCondition(SystemConditionType::UserPresent));
    > ```

4.  <span data-ttu-id="665cf-159">Registrieren Sie die Hintergrundaufgabe, indem Sie die Register-Methode für das [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="665cf-159">Register the background task by calling the Register method on the [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) object.</span></span> <span data-ttu-id="665cf-160">Speichern Sie das [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Ergebnis, sodass es im nächsten Schritt verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="665cf-160">Store the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786) result so it can be used in the next step.</span></span>

    <span data-ttu-id="665cf-161">Der folgende Code registriert die Hintergrundaufgabe und speichert das Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="665cf-161">The following code registers the background task and stores the result:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     BackgroundTaskRegistration task = builder.Register();
    > ```
    > ```cpp
    >     BackgroundTaskRegistration^ task = builder->Register();
    > ```

> [!NOTE]
> <span data-ttu-id="665cf-162">Universelle Windows-Apps müssen jedoch [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) aufrufen, bevor Hintergrundtriggertypen registriert werden.</span><span class="sxs-lookup"><span data-stu-id="665cf-162">Universal Windows apps must call [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485) before registering any of the background trigger types.</span></span>

<span data-ttu-id="665cf-163">Verwenden Sie den **ServicingComplete**-Trigger (siehe [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)) zum Ausführen von Konfigurationsänderungen nach dem Update wie Migrieren der Datenbank der App und Registrieren von Hintergrundaufgaben, um sicherzustellen, dass Ihre universelle Windows-App nach der Veröffentlichung eines Updates weiterhin ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="665cf-163">To ensure that your Universal Windows app continues to run properly after you release an update, use the **ServicingComplete** (see [SystemTriggerType](https://msdn.microsoft.com/library/windows/apps/br224839)) trigger to perform any post-update configuration changes such as migrating the app's database and registering background tasks.</span></span> <span data-ttu-id="665cf-164">Es empfiehlt sich, die Registrierung von Hintergrundaufgaben im Zusammenhang mit der vorherigen Version der App aufzuheben (siehe [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471)) und die Hintergrundaufgaben für die neue Version der App zu registrieren (siehe [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485)).</span><span class="sxs-lookup"><span data-stu-id="665cf-164">It is best practice to unregister background tasks associated with the previous version of the app (see [**RemoveAccess**](https://msdn.microsoft.com/library/windows/apps/hh700471)) and register background tasks for the new version of the app (see [**RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/hh700485)) at this time.</span></span>

<span data-ttu-id="665cf-165">Weitere Informationen finden Sie unter [Richtlinien für Hintergrundaufgaben](guidelines-for-background-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="665cf-165">For more information, see [Guidelines for background tasks](guidelines-for-background-tasks.md).</span></span>

## <a name="handle-background-task-completion-using-event-handlers"></a><span data-ttu-id="665cf-166">Behandeln des Abschlusses der Hintergrundaufgabe mithilfe von Ereignishandlern</span><span class="sxs-lookup"><span data-stu-id="665cf-166">Handle background task completion using event handlers</span></span>

<span data-ttu-id="665cf-167">Sie sollten eine Methode mit dem [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element registrieren, damit Ihre App Ergebnisse von der Hintergrundaufgabe abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="665cf-167">You should register a method with the [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781), so that your app can get results from the background task.</span></span> <span data-ttu-id="665cf-168">Beim Starten oder Fortsetzen der App wird die mark-Methode aufgerufen, wenn die Hintergrundaufgabe abgeschlossen wurde, seit sich die App zum letzten Mal im Vordergrund befand.</span><span class="sxs-lookup"><span data-stu-id="665cf-168">When the app is launched or resumed, the mark method will be called if the background task has completed since the last time the app was in the foreground.</span></span> <span data-ttu-id="665cf-169">(Die OnCompleted-Methode wird sofort aufgerufen, wenn die Hintergrundaufgabe abgeschlossen wird, während sich Ihre App im Vordergrund befindet.)</span><span class="sxs-lookup"><span data-stu-id="665cf-169">(The OnCompleted method will be called immediately if the background task completes while your app is currently in the foreground.)</span></span>

1.  <span data-ttu-id="665cf-170">Schreiben Sie eine OnCompleted-Methode, um den Abschluss von Hintergrundaufgaben zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="665cf-170">Write an OnCompleted method to handle the completion of background tasks.</span></span> <span data-ttu-id="665cf-171">Das Ergebnis der Hintergrundaufgabe kann z.B. eine Aktualisierung der Benutzeroberfläche auslösen.</span><span class="sxs-lookup"><span data-stu-id="665cf-171">For example, the background task result might cause a UI update.</span></span> <span data-ttu-id="665cf-172">Das hier gezeigte Methodenprofil ist für die OnCompleted-Ereignishandlermethode erforderlich, obwohl dieses Beispiel nicht den *args*-Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="665cf-172">The method footprint shown here is required for the OnCompleted event handler method, even though this example does not use the *args* parameter.</span></span>

    <span data-ttu-id="665cf-173">Der folgende Beispielcode erkennt den Abschluss der Hintergrundaufgabe und ruft eine Beispielmethode zur Aktualisierung der Benutzeroberfläche auf, die eine Meldungszeichenfolge erfordert.</span><span class="sxs-lookup"><span data-stu-id="665cf-173">The following sample code recognizes background task completion and calls an example UI update method that takes a message string.</span></span>

     > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     private void OnCompleted(IBackgroundTaskRegistration task, BackgroundTaskCompletedEventArgs args)
    >     {
    >         var settings = Windows.Storage.ApplicationData.Current.LocalSettings;
    >         var key = task.TaskId.ToString();
    >         var message = settings.Values[key].ToString();
    >         UpdateUI(message);
    >     }
    > ```
    > ```cpp
    >     void ExampleBackgroundTask::OnCompleted(BackgroundTaskRegistration^ task, BackgroundTaskCompletedEventArgs^ args)
    >     {
    >         auto settings = ApplicationData::Current->LocalSettings->Values;
    >         auto key = task->TaskId.ToString();
    >         auto message = dynamic_cast<String^>(settings->Lookup(key));
    >         UpdateUI(message);
    >     }
    > ```

    > [!NOTE]
    > <span data-ttu-id="665cf-174">Aktualisierungen der Benutzeroberfläche sollten asynchron durchgeführt werden, um den Benutzeroberflächenthread nicht zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="665cf-174">UI updates should be performed asynchronously, to avoid holding up the UI thread.</span></span> <span data-ttu-id="665cf-175">Ein Beispiel dazu finden Sie in der UpdateUI-Methode im [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span><span class="sxs-lookup"><span data-stu-id="665cf-175">For an example, see the UpdateUI method in the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666).</span></span>


2.  <span data-ttu-id="665cf-176">Gehen Sie dorthin zurück, wo Sie die Hintergrundaufgabe registriert haben.</span><span class="sxs-lookup"><span data-stu-id="665cf-176">Go back to where you registered the background task.</span></span> <span data-ttu-id="665cf-177">Fügen Sie nach dieser Codezeile ein neues [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="665cf-177">After that line of code, add a new [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781) object.</span></span> <span data-ttu-id="665cf-178">Stellen Sie Ihre OnCompleted-Methode als Parameter für den **BackgroundTaskCompletedEventHandler**-Konstruktor zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="665cf-178">Provide your OnCompleted method as the parameter for the **BackgroundTaskCompletedEventHandler** constructor.</span></span>

    <span data-ttu-id="665cf-179">Der folgende Beispielcode fügt dem [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786)-Element ein [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781)-Element hinzu:</span><span class="sxs-lookup"><span data-stu-id="665cf-179">The following sample code adds a [**BackgroundTaskCompletedEventHandler**](https://msdn.microsoft.com/library/windows/apps/br224781) to the [**BackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/br224786):</span></span>

     > [!div class="tabbedCodeSnippets"]
    > ```cs
    >     task.Completed += new BackgroundTaskCompletedEventHandler(OnCompleted);
    > ```
    > ```cpp
    >     task->Completed += ref new BackgroundTaskCompletedEventHandler(this, &ExampleBackgroundTask::OnCompleted);
    > ```

## <a name="declare-that-your-app-uses-background-tasks-in-the-app-manifest"></a><span data-ttu-id="665cf-180">Deklarieren, dass die App Hintergrundaufgaben verwendet (im App-Manifest)</span><span class="sxs-lookup"><span data-stu-id="665cf-180">Declare that your app uses background tasks in the app manifest</span></span>

<span data-ttu-id="665cf-181">Bevor Ihre App Hintergrundaufgaben ausführen kann, müssen Sie alle Hintergrundaufgaben im App-Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="665cf-181">Before your app can run background tasks, you must declare each background task in the app manifest.</span></span> <span data-ttu-id="665cf-182">Wenn Ihre App versucht, eine Hintergrundaufgabe mit einem Trigger zu registrieren, der nicht im Manifest aufgeführt ist, schlägt die Registrierung fehl.</span><span class="sxs-lookup"><span data-stu-id="665cf-182">If your app attempts to register a background task with a trigger that isn't listed in the manifest, the registration will fail.</span></span>

1.  <span data-ttu-id="665cf-183">Öffnen Sie den Paketmanifest-Designer durch Öffnen der Datei namens „Package.appxmanifest“.</span><span class="sxs-lookup"><span data-stu-id="665cf-183">Open the package manifest designer by opening the file named Package.appxmanifest.</span></span>
2.  <span data-ttu-id="665cf-184">Öffnen Sie die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="665cf-184">Open the **Declarations** tab.</span></span>
3.  <span data-ttu-id="665cf-185">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Hintergrundaufgaben** aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="665cf-185">From the **Available Declarations** drop-down, select **Background Tasks** and click **Add**.</span></span>
4.  <span data-ttu-id="665cf-186">Aktivieren Sie das Kontrollkästchen **Systemereignis**.</span><span class="sxs-lookup"><span data-stu-id="665cf-186">Select the **System event** checkbox.</span></span>
5.  <span data-ttu-id="665cf-187">Geben Sie in das Textfeld **Einstiegspunkt:** den Namespace und Namen der Hintergrundklasse ein, die in diesem Beispiel „RuntimeComponent1.ExampleBackgroundTask“ lautet.</span><span class="sxs-lookup"><span data-stu-id="665cf-187">In the **Entry point:** textbox, enter the namespace and name of your background class which is for this example is RuntimeComponent1.ExampleBackgroundTask.</span></span>
6.  <span data-ttu-id="665cf-188">Schließen Sie den Manifest-Designer.</span><span class="sxs-lookup"><span data-stu-id="665cf-188">Close the manfiest designer.</span></span>

    <span data-ttu-id="665cf-189">Das folgende Erweiterungselement wird zur Datei „Package.appxmanifest“ hinzugefügt, um die Hintergrundaufgabe zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="665cf-189">The following Extensions element is added to your Package.appxmanifest file to register the background task:</span></span>

    ```xml
    <Extensions>
      <Extension Category="windows.backgroundTasks" EntryPoint="RuntimeComponent1.ExampleBackgroundTask">
        <BackgroundTasks>
          <Task Type="systemEvent" />
        </BackgroundTasks>
      </Extension>
    </Extensions>
    ```

## <a name="summary-and-next-steps"></a><span data-ttu-id="665cf-190">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="665cf-190">Summary and next steps</span></span>

<span data-ttu-id="665cf-191">Sie sollten jetzt über die Grundlagen verfügen, um eine Hintergrundaufgabenklasse zu schreiben, die Hintergrundaufgabe in Ihrer App zu registrieren und Ihre App so zu konfigurieren, dass Sie den Abschluss der Hintergrundaufgabe erkennt.</span><span class="sxs-lookup"><span data-stu-id="665cf-191">You should now understand the basics of how to write a background task class, how to register the background task from within your app, and how to make your app recognize when the background task is complete.</span></span> <span data-ttu-id="665cf-192">Sie sollten auch mit der Aktualisierung des Anwendungsmanifests vertraut sein, damit Ihre App die Hintergrundaufgabe erfolgreich registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="665cf-192">You should also understand how to update the application manifest so that your app can successfully register the background task.</span></span>

> [!NOTE]
> <span data-ttu-id="665cf-193">Laden Sie das [Beispiel für eine Hintergrundaufgabe](http://go.microsoft.com/fwlink/p/?LinkId=618666) herunter, um ähnliche Codebeispiele im Kontext einer vollständigen und stabilen UWP-App (Universelle Windows-Plattform) mit Hintergrundaufgaben zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="665cf-193">Download the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666) to see similar code examples in the context of a complete and robust UWP app that uses background tasks.</span></span>

<span data-ttu-id="665cf-194">Eine API-Referenz, konzeptionelle Richtlinien zu Hintergrundaufgaben und ausführlichere Anweisungen zum Schreiben von Apps, die Hintergrundaufgaben verwenden, finden Sie unter den folgenden verwandten Themen:</span><span class="sxs-lookup"><span data-stu-id="665cf-194">See the following related topics for API reference, background task conceptual guidance, and more detailed instructions for writing apps that use background tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="665cf-195">Dieser Artikel ist für Windows10-Entwickler bestimmt, die UWP-Apps (Universelle Windows-Plattform) schreiben.</span><span class="sxs-lookup"><span data-stu-id="665cf-195">This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="665cf-196">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="665cf-196">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

## <a name="related-topics"></a><span data-ttu-id="665cf-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="665cf-197">Related topics</span></span>

**<span data-ttu-id="665cf-198">Ausführliche Themen mit Anweisungen zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="665cf-198">Detailed background task instructional topics</span></span>**

* [<span data-ttu-id="665cf-199">Reagieren auf Systemereignisse mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="665cf-199">Respond to system events with background tasks</span></span>](respond-to-system-events-with-background-tasks.md)
* [<span data-ttu-id="665cf-200">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-200">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="665cf-201">Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-201">Set conditions for running a background task</span></span>](set-conditions-for-running-a-background-task.md)
* [<span data-ttu-id="665cf-202">Verwenden eines Wartungsauslösers</span><span class="sxs-lookup"><span data-stu-id="665cf-202">Use a maintenance trigger</span></span>](use-a-maintenance-trigger.md)
* [<span data-ttu-id="665cf-203">Behandeln einer abgebrochenen Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-203">Handle a cancelled background task</span></span>](handle-a-cancelled-background-task.md)
* [<span data-ttu-id="665cf-204">Überwachen des Status und Abschlusses von Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="665cf-204">Monitor background task progress and completion</span></span>](monitor-background-task-progress-and-completion.md)
* [<span data-ttu-id="665cf-205">Ausführen einer Hintergrundaufgabe für einen Timer</span><span class="sxs-lookup"><span data-stu-id="665cf-205">Run a background task on a timer</span></span>](run-a-background-task-on-a-timer-.md)
* <span data-ttu-id="665cf-206">[Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="665cf-206">[Create and register an in-process background task](create-and-register-an-inproc-background-task.md).</span></span>
* [<span data-ttu-id="665cf-207">Konvertieren einer Out-of-Process-Hintergrundaufgabe in eine In-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-207">Convert an out-of-process background task to an in-process background task</span></span>](convert-out-of-process-background-task.md)  

**<span data-ttu-id="665cf-208">Ratschläge zu Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="665cf-208">Background task guidance</span></span>**

* [<span data-ttu-id="665cf-209">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="665cf-209">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
* [<span data-ttu-id="665cf-210">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="665cf-210">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="665cf-211">So wird's gemacht: Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in Windows Store-Apps (beim Debuggen)</span><span class="sxs-lookup"><span data-stu-id="665cf-211">How to trigger suspend, resume, and background events in Windows Store apps (when debugging)</span></span>](http://go.microsoft.com/fwlink/p/?linkid=254345)

**<span data-ttu-id="665cf-212">Hintergrundaufgabe – API-Referenz</span><span class="sxs-lookup"><span data-stu-id="665cf-212">Background Task API Reference</span></span>**

* [**<span data-ttu-id="665cf-213">Windows.ApplicationModel.Background</span><span class="sxs-lookup"><span data-stu-id="665cf-213">Windows.ApplicationModel.Background</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)
