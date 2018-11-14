---
author: PatrickFarley
ms.assetid: 67a46812-881c-404b-9f3b-c6786f39e72b
title: Anpassen des Druck-Workflows
description: Erstellen Sie angepasste Druck-Workflows entsprechend den Anforderungen Ihrer Organisation.
ms.author: pafarley
ms.date: 08/10/2017
ms.topic: article
keywords: Windows 10, Uwp, das Drucken
ms.localizationpriority: medium
ms.openlocfilehash: f58c0c8397831595c237b7bd9fe4eafb25594ab3
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6209812"
---
# <a name="customize-the-print-workflow"></a><span data-ttu-id="5a8e7-104">Anpassen des Druck-Workflows</span><span class="sxs-lookup"><span data-stu-id="5a8e7-104">Customize the print workflow</span></span>

## <a name="overview"></a><span data-ttu-id="5a8e7-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="5a8e7-105">Overview</span></span>
<span data-ttu-id="5a8e7-106">Entwickler können den Druck-Workflow durch die Verwendung einer Druck-Workflow-App individuell anpassen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-106">Developers can customize the printing workflow experience through the use of a print workflow app.</span></span> <span data-ttu-id="5a8e7-107">Druck-Workflow-Apps sind UWP-Apps, die die Funktionalität von [Microsoft Store Apps (WSDAs)](https://docs.microsoft.com/windows-hardware/drivers/devapps/) erweitern. Daher ist es hilfreich, sich mit WSDAs vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-107">Print workflow apps are UWP apps that expand on the functionality of [Microsoft Store devices apps (WSDAs)](https://docs.microsoft.com/windows-hardware/drivers/devapps/), so it will be helpful to have some familiarity with WSDAs before going further.</span></span> 

<span data-ttu-id="5a8e7-108">Ähnlich wie bei WSDAs prüft das System, ob eine Workflow-App mit dem Drucker verknüpft ist, wenn der Benutzer einer Quellanwendung etwas ausdruckt und durch den Druckdialog navigiert.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-108">Just as in the case of WSDAs, when the user of a source application elects to print something and navigates through the print dialog, the system checks whether a workflow app is associated with that printer.</span></span> <span data-ttu-id="5a8e7-109">Ist dies der Fall, startet die Druck-Workflow-App (hauptsächlich als Hintergrundaufgabe; mehr dazu weiter unten).</span><span class="sxs-lookup"><span data-stu-id="5a8e7-109">If it is, the print workflow app launches (primarily as a background task; more on this below).</span></span> <span data-ttu-id="5a8e7-110">Eine Workflow-App ist in der Lage, sowohl das Druckticket (das XML-Dokument, das die Druckereinstellungen für den aktuellen Druckauftrag konfiguriert) als auch den tatsächlich zu druckenden XPS-Inhalt zu ändern.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-110">A workflow app is able to alter both the print ticket (the XML document that configures the printer device settings for the current print task) and the actual XPS content to be printed.</span></span> <span data-ttu-id="5a8e7-111">Diese Funktionalität kann optional dem Benutzer zur Verfügung gestellt werden, indem im Prozess eine Benutzeroberfläche gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-111">It can optionally expose this functionality to the user by launching a UI midway through the process.</span></span> <span data-ttu-id="5a8e7-112">Nach ihrer Arbeit gibt sie den Druckinhalt und das Druckticket an den Treiber weiter.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-112">After doing its work, it passes the print content and print ticket on to the driver.</span></span>

<span data-ttu-id="5a8e7-113">Da es sich um Hintergrund- und Vordergrundkomponenten handelt und der Prozess funktional mit anderen Apps gekoppelt ist, kann eine Druck-Workflow-App für den Druck komplizierter zu implementieren sein als andere Kategorien von UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-113">Because it involves background and foreground components, and because it is functionally coupled with other app(s), a print workflow app can be more complicated to implement than other categories of UWP apps.</span></span> <span data-ttu-id="5a8e7-114">Es wird empfohlen, sich das [Workflow-App-Beispiel](https://github.com/Microsoft/print-oem-samples) anzusehen, während Sie dieses Handbuch lesen, um besser zu verstehen, wie die verschiedenen Funktionen implementiert werden können.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-114">It is recommended that you inspect the [Workflow app sample](https://github.com/Microsoft/print-oem-samples) while reading this guide to better understand how the different features can be implemented.</span></span> <span data-ttu-id="5a8e7-115">Einige Funktionen, wie z. B. verschiedene Fehlerprüfungen und die Verwaltung der Benutzeroberfläche, fehlen zur Vereinfachung in diesem Handbuch.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-115">Some features, such as various error checks and UI management, are absent from this guide for the sake of simplicity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="5a8e7-116">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="5a8e7-116">Getting started</span></span>

<span data-ttu-id="5a8e7-117">Die Workflow-App muss dem Drucksystem den Einstiegspunkt der Workflow-App angeben, damit sie zum richtigen Zeitpunkt gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-117">The workflow app must indicate its entry point to the print system so that it can be launched at the appropriate time.</span></span> <span data-ttu-id="5a8e7-118">Dies geschieht durch Einfügen der folgenden Deklaration in das `Application/Extensions`-Element der *package.appxmanifest*-Datei des UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-118">This is done by inserting the following declaration in the `Application/Extensions` element of the UWP project's *package.appxmanifest* file.</span></span> 

```xml
<uap:Extension Category="windows.printWorkflowBackgroundTask"  
    EntryPoint="WFBackgroundTasks.WfBackgroundTask" />
```

> [!IMPORTANT] 
> <span data-ttu-id="5a8e7-119">Es gibt viele Szenarien, in denen das Anpassen des Druck keine Benutzereingaben erfordert.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-119">There are many scenarios in which the print customization does not require user input.</span></span> <span data-ttu-id="5a8e7-120">Aus diesem Grund werden standardmäßig Workflow-Apps für den Druck als Hintergrundaufgaben ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-120">For this reason, Print workflow apps run as background tasks by default.</span></span>

<span data-ttu-id="5a8e7-121">Wenn eine Workflow-App mit der Quellanwendung verknüpft ist, die den Druckauftrag gestartet hat (siehe dazu weiter unten), prüft das Drucksystem seine Manifestdateien auf einen Einstiegspunkt für die Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-121">If a workflow app is associated with the source application that started the print job (see later section for instructions on this), the print system examines its manifest files for a background task entry point.</span></span>

## <a name="do-background-work-on-the-print-ticket"></a><span data-ttu-id="5a8e7-122">Hintergrundarbeiten am Druckticket durchführen</span><span class="sxs-lookup"><span data-stu-id="5a8e7-122">Do background work on the print ticket</span></span>

<span data-ttu-id="5a8e7-123">Das erste, was das Drucksystem mit der Workflow-App macht, ist die Aktivierung der Hintergrundaufgabe (in diesem Fall die Klasse `WfBackgroundTask` im Namenspace `WFBackgroundTasks`).</span><span class="sxs-lookup"><span data-stu-id="5a8e7-123">The first thing the print system does with the workflow app is activate its background task (In this case, the `WfBackgroundTask` class in the `WFBackgroundTasks` namespace).</span></span> <span data-ttu-id="5a8e7-124">In der `Run`-Methode der Hintergrundaufgabe sollten Sie die Trigger-Details des als **[PrintWorkflowTriggerDetails](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtriggerdetails)**-Instanz definieren.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-124">In the background task's `Run` method, you should cast the task's trigger details as a **[PrintWorkflowTriggerDetails](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtriggerdetails)** instance.</span></span> <span data-ttu-id="5a8e7-125">Damit steht Ihnen die spezielle Funktionalität für eine Hintergrundaufgabe eines Druck-Workflows zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-125">This will provide the special functionality for a print workflow background task.</span></span> <span data-ttu-id="5a8e7-126">Sie stellt die **[PrintWorkflowSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtriggerdetails.PrintWorkflowSession)**-Eigenschaft bereit, die eine Instanz von **[PrintWorkFlowBackgroundSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession)** ist.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-126">It exposes the **[PrintWorkflowSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtriggerdetails.PrintWorkflowSession)** property, which is an instance of **[PrintWorkFlowBackgroundSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession)**.</span></span> <span data-ttu-id="5a8e7-127">Die Session-Klassen des Druck-Workflows – sowohl die Varianten für den Hintergrund als auch für den Vordergrund – steuern die Ablaufschritte der Druck-Workflow-App.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-127">Print workflow session classes - both the background and foreground varieties - will control the sequential steps of the print workflow app.</span></span> 

<span data-ttu-id="5a8e7-128">Registrieren Sie dann Handler-Methoden für die beiden Ereignisse, die diese Session-Klasse auslösen wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-128">Then register handler methods for the two events that this session class will raise.</span></span> <span data-ttu-id="5a8e7-129">Diese Methoden werden Sie später definieren.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-129">You will define these methods later on.</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance) {
    // Take out a deferral here and complete once all the callbacks are done
    runDeferral = taskInstance.GetDeferral();

    // Associate a cancellation handler with the background task.
    taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);

    // cast the task's trigger details as PrintWorkflowTriggerDetails
    PrintWorkflowTriggerDetails workflowTriggerDetails = taskInstance.TriggerDetails as PrintWorkflowTriggerDetails;

    // Get the session manager, which is unique to this print job
    PrintWorkflowBackgroundSession sessionManager = workflowTriggerDetails.PrintWorkflowSession;

    // add the event handler callback routines
    sessionManager.SetupRequested += OnSetupRequested;
    sessionManager.Submitted += OnXpsOMPrintSubmitted;

    // Allow the event source to start
    // This call blocks until all of the workflow callbacks complete
    sessionManager.Start();
}
```

<span data-ttu-id="5a8e7-130">Wenn die `Start`-Methode aufgerufen wird, löst der Sitzungsmanager das Ereignis **[SetupRequested](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession.SetupRequested)** zuerst aus.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-130">When the `Start` method is called, the session manager will raise the **[SetupRequested](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession.SetupRequested)** event first.</span></span> <span data-ttu-id="5a8e7-131">Dieses Ereignis zeigt allgemeine Informationen über den Druckauftrag sowie das Druckticket an.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-131">This event exposes general information about the print task, as well as the print ticket.</span></span> <span data-ttu-id="5a8e7-132">In dieser Phase kann das Druckticket im Hintergrund bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-132">At this stage, the print ticket can be edited in the background.</span></span> 

```csharp
private void OnSetupRequested(PrintWorkflowBackgroundSession sessionManager, PrintWorkflowBackgroundSetupRequestedEventArgs printTaskSetupArgs) {
    // Take out a deferral here and complete once all the callbacks are done
    Deferral setupRequestedDeferral = printTaskSetupArgs.GetDeferral();

    // Get general information about the source application, print job title, and session ID
    string sourceApplicationName = printTaskSetupArgs.Configuration.SourceAppDisplayName;
    string jobTitle = printTaskSetupArgs.Configuration.JobTitle;
    string sessionId = printTaskSetupArgs.Configuration.SessionId;

    // edit the print ticket
    WorkflowPrintTicket printTicket = printTaskSetupArgs.GetUserPrintTicketAsync();

    // ...
```

<span data-ttu-id="5a8e7-133">Wichtig ist, dass die App bei der Verarbeitung von **SetupRequested** bestimmt, ob sie eine Vordergrundkomponente startet.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-133">Importantly, it is in the handling of the **SetupRequested** that the app will determine whether to launch a foreground component.</span></span> <span data-ttu-id="5a8e7-134">Dies kann von einer Einstellung abhängen, die zuvor lokal gespeichert wurde, oder von einem Ereignis, das während der Bearbeitung des Drucktickets aufgetreten ist, oder von einer statischen Einstellung Ihrer speziellen App.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-134">This could depend on a setting that was previously saved to local storage, or an event that occurred during the editing of the print ticket, or it may be a static setting of your particular app.</span></span>

```csharp
    // ...
    
    if (UIrequested) {
        printTaskSetupArgs.SetRequiresUI();

        // Any data that is to be passed to the foreground task must be stored the app's local storage.
        // It should be prefixed with the sourceApplicationName string and the SessionId string, so that
        // it can be identified as pertaining to this workflow app session.
    }

    // Complete the deferral taken out at the start of OnSetupRequested
    setupRequestedDeferral.Complete();
}
```

## <a name="do-foreground-work-on-the-print-job-optional"></a><span data-ttu-id="5a8e7-135">Vordergrundarbeit für den Druckjob verarbeiten (optional)</span><span class="sxs-lookup"><span data-stu-id="5a8e7-135">Do foreground work on the print job (optional)</span></span>

<span data-ttu-id="5a8e7-136">Wurde die Methode **[SetRequiresUI](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsetuprequestedeventargs.SetRequiresUI)** aufgerufen, dann überprüft das Drucksystem die Manifest-Datei für den Einstiegspunkt in die Vordergrund-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-136">If the **[SetRequiresUI](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsetuprequestedeventargs.SetRequiresUI)** method was called, then the print system will examine the manifest file for the entry point to the foreground application.</span></span> <span data-ttu-id="5a8e7-137">Das `Application/Extensions`-Element der Datei *package.appxmanifest* muss die folgenden Zeilen haben.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-137">The `Application/Extensions` element of your *package.appxmanifest* file must have the following lines.</span></span> <span data-ttu-id="5a8e7-138">Ersetzen Sie den Wert von `EntryPoint` durch den Namen der Vordergrund-App.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-138">Replace the value of `EntryPoint` with name of the foreground app.</span></span>

```xml
<uap:Extension Category="windows.printWorkflowForegroundTask"  
    EntryPoint="MyWorkFlowForegroundApp.App" /> 
```

<span data-ttu-id="5a8e7-139">Als nächstes ruft das Drucksystem die **OnActivated**-Methode für den angegebenen App-Einsprungspunkt auf.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-139">Next, the print system calls the **OnActivated** method for the given app entry point.</span></span> <span data-ttu-id="5a8e7-140">In der **OnActivated**-Methode ihrer _App. xaml.cs_-Datei sollte die Workflow-Anwendung die Aktivierungsart prüfen, um zu überprüfen, ob es sich um eine Workflow-Aktivierung handelt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-140">In the **OnActivated** method of its _App.xaml.cs_ file, the workflow app should check the activation kind to verify that it is a workflow activation.</span></span> <span data-ttu-id="5a8e7-141">Wenn ja, kann die Workflow-Anwendung die Aktivierungsargumente in ein **[PrintWorkflowUIActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowuiactivatedeventargs)**-Objekt umwandeln, das ein **[PrintWorkflowForegroundSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession)**-Objekt als Eigenschaft ausgibt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-141">If so, the workflow app can cast the activation arguments to a **[PrintWorkflowUIActivatedEventArgs](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowuiactivatedeventargs)** object, which exposes a **[PrintWorkflowForegroundSession](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession)** object as a property.</span></span> <span data-ttu-id="5a8e7-142">Dieses Objekt enthält, wie sein Gegenstück im vorherigen Abschnitt, Ereignisse, die vom Drucksystem ausgelöst werden, und Sie können diesen Handler zuordnen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-142">This object, like its background counterpart in the previous section, contains events that are raised by the print system, and you can assign handlers to these.</span></span> <span data-ttu-id="5a8e7-143">In diesem Fall wird die Ereignisbehandlungsfunktionalität in einer eigenen Klasse namens `WorkflowPage` implementiert.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-143">In this case, the event-handling functionality will be implemented in a separate class called `WorkflowPage`.</span></span>

<span data-ttu-id="5a8e7-144">Zuerst in der Datei _App.xaml.cs_:</span><span class="sxs-lookup"><span data-stu-id="5a8e7-144">First, in the _App.xaml.cs_ file:</span></span>

```csharp
protected override void OnActivated(IActivatedEventArgs args){

    if (args.Kind == ActivationKind.PrintWorkflowForegroundTask) {

        // the app should instantiate a new UI view so that it can properly handle the case when 
        // several print jobs are active at the same time.
        Frame rootFrame = new Frame();
        if (null == Window.Current.Content)
        {
            rootFrame.Navigate(typeof(WorkflowPage));
            Window.Current.Content = rootFrame;
        }

        // Get the main page
        WorkflowPage workflowPage = (WorkflowPage)rootFrame.Content;

        // Make sure the page knows it's handling a foreground task activation
        workflowPage.LaunchType = WorkflowPage.WorkflowPageLaunchType.ForegroundTask;

        // Get the activation arguments
        PrintWorkflowUIActivatedEventArgs printTaskUIEventArgs = args as PrintWorkflowUIActivatedEventArgs;

        // Get the session manager
        PrintWorkflowForegroundSession taskSessionManager = printTaskUIEventArgs.PrintWorkflowSession;

        // Add the callback handlers - these methods are in the workflowPage class
        taskSessionManager.SetupRequested += workflowPage.OnSetupRequested;
        taskSessionManager.XpsDataAvailable += workflowPage.OnXpsDataAvailable;

        // start raising the print workflow events
        taskSessionManager.Start();
    }
}
```

<span data-ttu-id="5a8e7-145">Sobald das UI-Ereignis-Handler angehängt und die **OnActivated**-Methode beendet hat, löst das Drucksystem das **[SetupRequested](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession.SetupRequested)**-Ereignis für das zu behandelnde UI aus.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-145">Once the UI has attached event handlers and the **OnActivated** method has exited, the print system will fire the **[SetupRequested](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession.SetupRequested)** event for the UI to handle.</span></span> <span data-ttu-id="5a8e7-146">Dieses Ereignis liefert die gleichen Daten wie das Setup-Ereignis der Hintergrundaufgabe, einschließlich der Druckauftragsinfo und des Druckticketdokuments, jedoch ohne die Möglichkeit, den Start eine zusätzlichen UIs anzufordern.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-146">This event provides the same data that the background task setup event provided, including the print job info and print ticket document, but without the ability to request the launch of additional UI.</span></span> <span data-ttu-id="5a8e7-147">In der Datei _WorkflowPage.xaml.cs_:</span><span class="sxs-lookup"><span data-stu-id="5a8e7-147">In the _WorkflowPage.xaml.cs_ file:</span></span>

```csharp
internal void OnSetupRequested(PrintWorkflowForegroundSession sessionManager, PrintWorkflowForegroundSetupRequestedEventArgs printTaskSetupArgs) {
    // If anything asynchronous is going to be done, you need to take out a deferral here,
    // since otherwise the next callback happens once this one exits, which may be premature
    Deferral setupRequestedDeferral = printTaskSetupArgs.GetDeferral();

    // Get information about the source application, print job title, and session ID
    string sourceApplicationName = printTaskSetupArgs.Configuration.SourceAppDisplayName;
    string jobTitle = printTaskSetupArgs.Configuration.JobTitle;
    string sessionId = printTaskSetupArgs.Configuration.SessionId;
    // the following string should be used when storing data that pertains to this workflow session
    // (such as user input data that is meant to change the print content later on)
    string localStorageVariablePrefix = string.Format("{0}::{1}::", sourceApplicationName, sessionID);
    
    try
    {
        // receive and store user input
        // ...
    }
    catch (Exception ex)
    {
        string errorMessage = ex.Message;
        Debug.WriteLine(errorMessage);
    }
    finally
    {
        // Complete the deferral taken out at the start of OnSetupRequested
        setupRequestedDeferral.Complete();
    }
}
```

<span data-ttu-id="5a8e7-148">Als nächstes wird das Drucksystem das **[XpsDataAvailable](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession.XpsDataAvailable)**-Ereignis für das UI auslösen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-148">Next, the print system will raise the **[XpsDataAvailable](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowforegroundsession.XpsDataAvailable)** event for the UI.</span></span> <span data-ttu-id="5a8e7-149">Im Handler für dieses Ereignis kann die Workflow-App auf alle dem Setup-Ereignis zur Verfügung stehenden Daten zugreifen und zusätzlich die XPS-Daten direkt lesen, entweder als Raw-Byte-Strom oder als Objektmodell.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-149">In the handler for this event, the workflow app can access all of the data available to the setup event and can additionally read the XPS data directly, either as a stream of raw bytes or as an object model.</span></span> <span data-ttu-id="5a8e7-150">Der Zugriff auf die XPS-Daten ermöglicht es dem UI, Druckvorschau-Dienste zur Verfügung zu stellen und dem Benutzer zusätzliche Informationen über die Operationen zur Verfügung zu stellen, die die Workflow-App für die Daten ausführen wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-150">Access to the XPS data allows the UI to provide print preview services and to provide additional information to the user about the operations that the workflow app will execute on the data.</span></span> 

<span data-ttu-id="5a8e7-151">Im Rahmen dieses Ereignis-Handlers muss die Workflow-App ein Deferral-Objekt erhalten, wenn sie weiterhin mit dem Benutzer interagieren soll.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-151">As part of this event handler, the workflow app must acquire a deferral object if it will continue to interact with the user.</span></span> <span data-ttu-id="5a8e7-152">Ohne eine Verzögerung betrachtet das Drucksystem den UI-Task als erledigt, wenn der **XpsDataAvailable**-Ereignis-Handler beendet wird oder eine asynchrone Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-152">Without a deferral, the print system will consider the UI task complete when the **XpsDataAvailable** event handler exits or when it calls an async method.</span></span> <span data-ttu-id="5a8e7-153">Wenn die App alle erforderlichen Informationen aus der Interaktion des Benutzers mit dem UI gesammelt hat, sollte sie die Verzögerung abschließen, damit das Drucksystem fortfahren kann.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-153">When the app has gathered all required information from the user's interaction with the UI, it should complete the deferral so that the print system can then advance.</span></span>

```csharp
internal async void OnXpsDataAvailable(PrintWorkflowForegroundSession sessionManager, PrintWorkflowXpsDataAvailableEventArgs printTaskXpsAvailableEventArgs)
{
    // Take out a deferral
    Deferral xpsDataAvailableDeferral = printTaskXpsAvailableEventArgs.GetDeferral();

    SpoolStreamContent xpsStream = printTaskXpsAvailableEventArgs.Operation.XpsContent.GetSourceSpoolDataAsStreamContent(); 
 
    IInputStream inputStream = xpsStream.GetInputSpoolStream(); 
 
    using (var inputReader = new Windows.Storage.Streams.DataReader(inputStream)) 
    { 
        // Read the XPS data from input stream 
        byte[] xpsData = new byte[inputReader.UnconsumedBufferLength]; 
        while (inputReader.UnconsumedBufferLength > 0) 
        { 
            inputReader.ReadBytes(xpsData); 
            // Do something with the XPS data, e.g. preview 
            // ...                  
        } 
    } 

    // Complete the deferral taken out at the start of this method
    xpsDataAvailableDeferral.Complete();
}
```

<span data-ttu-id="5a8e7-154">Zusätzlich bietet die Instanz **[PrintWorkflowSubmittedOperation](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedoperation)**, die durch die Ereignisargumente bereitgestellt wird, die Option, den Druckauftrag abzubrechen oder anzuzeigen, dass der Auftrag erfolgreich ist, aber kein Ausgabedruckauftrag erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-154">Additionally, the **[PrintWorkflowSubmittedOperation](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedoperation)** instance exposed by the event args provides the option to cancel the print job or to indicate that the job is successful but that no output print job will be needed.</span></span> <span data-ttu-id="5a8e7-155">Dazu wird die **[Complete](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedoperation.Complete)**-Methode mit dem Wert **[PrintWorkflowSubmittedStatus](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedstatus)** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-155">This is done by calling the **[Complete](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedoperation.Complete)** method with a **[PrintWorkflowSubmittedStatus](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowsubmittedstatus)** value.</span></span>

> [!NOTE]
> <span data-ttu-id="5a8e7-156">Wenn die Workflow-App den Druckauftrag abbricht, empfiehlt es sich dringend, eine Popup-Benachrichtigung zu senden, aus der hervorgeht, warum der Druckauftrag abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-156">If the workflow app cancels the print job, it is highly recommended that it provide a toast notification indicating why the job was cancelled.</span></span> 


## <a name="do-final-background-work-on-the-print-content"></a><span data-ttu-id="5a8e7-157">Abschließende Hintergrundarbeiten am Druckinhalt durchführen</span><span class="sxs-lookup"><span data-stu-id="5a8e7-157">Do final background work on the print content</span></span>

<span data-ttu-id="5a8e7-158">Nachdem das UI die Verzögerung des Ereignisses **PrintTaskXpsDataAvailable** abgeschlossen hat (oder wenn der Schritt des UIs umgangen wurde), löst das Drucksystem das Ereignis **[Submitted](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession.Submitted)** für die Hintergrundaufgabe aus.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-158">Once the UI has completed the deferral in the **PrintTaskXpsDataAvailable** event (or if the UI step was bypassed), the print system will fire the **[Submitted](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowbackgroundsession.Submitted)** event for the background task.</span></span> <span data-ttu-id="5a8e7-159">Im Handler für dieses Ereignis kann die Workflow-App auf alle Daten zugreifen, die das Ereignis **XpsDataAvailable** zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-159">In the handler for this event, the workflow app can get access to all of the same data provided by the **XpsDataAvailable** event.</span></span> <span data-ttu-id="5a8e7-160">Im Gegensatz zu den vorherigen Ereignissen bietet **Submitted** jedoch auch *Schreibzugriff* auf den Inhalt des endgültigen Druckauftrags über eine **[PrintWorkflowTarget](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtarget)**-Instanz.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-160">However, unlike any of the previous events, **Submitted** also provides *write* access to the final print job content through a **[PrintWorkflowTarget](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow.printworkflowtarget)** instance.</span></span> 

<span data-ttu-id="5a8e7-161">Das Objekt, mit dem die Daten für den endgültigen Druck gespoolt werden, hängt davon ab, ob auf die Quelldaten als Raw-Bity-Strom oder als XPS-Objektmodell zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-161">The object that is used to spool the data for final printing depends on whether the source data is accessed as a raw byte stream or as the XPS object model.</span></span> <span data-ttu-id="5a8e7-162">Wenn die Workflow-App über einen Byte-Stream auf die Quelldaten zugreift, wird ein Ausgabe-Byte-Stream bereitgestellt, in den die endgültigen Auftragsdaten geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-162">When the workflow app accesses the source data through a byte stream, an output byte stream is provided to write the final job data to.</span></span> <span data-ttu-id="5a8e7-163">Wenn die Workflow-App über das Objektmodell auf die Quelldaten zugreift, wird ein Document-Writer bereitgestellt, um Objekte in den Ausgabeauftrag zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-163">When the workflow app accesses the source data through the object model, a document writer is provided to write objects to the output job.</span></span> <span data-ttu-id="5a8e7-164">In jedem Fall sollte die Workflow-App alle Quelldaten lesen, die erforderlichen Daten modifizieren und die geänderten Daten in das Ausgabeziel schreiben.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-164">In either case, the workflow app should read all of the source data, modify any data required, and write the modified data to the output target.</span></span>

<span data-ttu-id="5a8e7-165">Wenn die Hintergrundaufgabe das Schreiben der Daten beendet hat, sollte sie **Complete** für das entsprechende **PrintWorkflowSubmittedOperation**-Objekt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-165">When the background task finishes writing the data, it should call **Complete** on the corresponding **PrintWorkflowSubmittedOperation** object.</span></span> <span data-ttu-id="5a8e7-166">Sobald die Workflow-App diesen Schritt abgeschlossen hat und der Eventhandler **Submitted** beendet wurde, wird die Workflow-Sitzung geschlossen und der Benutzer kann den Status des endgültigen Druckauftrags über die Standard-Druckdialoge überwachen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-166">Once the workflow app completes this step and the **Submitted** event handler exits, the workflow session is closed and the user can monitor the status of the final print job through the standard print dialogs.</span></span>

## <a name="final-steps"></a><span data-ttu-id="5a8e7-167">Letzte Schritte</span><span class="sxs-lookup"><span data-stu-id="5a8e7-167">Final steps</span></span>

### <a name="register-the-print-workflow-app-to-the-printer"></a><span data-ttu-id="5a8e7-168">Druck-Workflow-App beim Drucker registrieren</span><span class="sxs-lookup"><span data-stu-id="5a8e7-168">Register the print workflow app to the printer</span></span>

<span data-ttu-id="5a8e7-169">Ihre Workflow-App ist mit einem Drucker verbunden, der die gleiche Art der Übermittlung von Metadaten wie bei WSDAs verwendet.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-169">Your workflow app is associated with a printer using the same type of metadata file submission as for WSDAs.</span></span> <span data-ttu-id="5a8e7-170">Tatsächlich kann eine einzelne UWP-Anwendung sowohl als Workflow-App als auch als WSDA fungieren, die Druckaufgabeeinstellungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-170">In fact, a single UWP application can act as both a workflow app and a WSDA that provides print task settings functionality.</span></span> <span data-ttu-id="5a8e7-171">Führen Sie die entsprechenden [WSDA-Schritte zum Anlegen der Metadaten-Zuordnung](https://docs.microsoft.com/windows-hardware/drivers/devapps/step-2--create-device-metadata) aus.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-171">Follow the corresponding [WSDA steps for creating the metadata association](https://docs.microsoft.com/windows-hardware/drivers/devapps/step-2--create-device-metadata).</span></span>

<span data-ttu-id="5a8e7-172">Der Unterschied besteht darin, dass WSDAs zwar automatisch für den Benutzer aktiviert werden (die App wird immer gestartet, wenn der Benutzer über das zugehörige Gerät druckt), Workflow-Apps jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-172">The difference is that while WSDAs are automatically activated for the user (the app will always launch when that user prints on the associated device), workflow apps are not.</span></span> <span data-ttu-id="5a8e7-173">Sie haben eine eigene Richtlinie, die festgelegt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-173">They have a separate policy that must be set.</span></span>

### <a name="set-the-workflow-apps-policy"></a><span data-ttu-id="5a8e7-174">Festlegen der Richtlinien für die Workflow-App</span><span class="sxs-lookup"><span data-stu-id="5a8e7-174">Set the workflow app's policy</span></span>
<span data-ttu-id="5a8e7-175">Die Workflow-App-Richtlinie wird durch Powershell-Befehle auf dem Gerät festgelegt, das die Workflow-App ausführen soll.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-175">The workflow app policy is set by Powershell commands on the device that is to run the workflow app.</span></span> <span data-ttu-id="5a8e7-176">Die Befehle Set-Printer, Add-Printer (bestehender Port) und Add-Printer (neuer WSD-Port) werden modifiziert, um das Festen von Workflow-Richtlinien zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-176">The Set-Printer, Add-Printer (existing port) and Add-Printer (new WSD port) commands will be modified to allow Workflow policies to be set.</span></span> 
* `Disabled`<span data-ttu-id="5a8e7-177">: Workflow-Apps werden nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-177">: Workflow apps will not be activated.</span></span>
* `Uninitialized`<span data-ttu-id="5a8e7-178">: Workflow-Apps werden aktiviert, wenn der Workflow-DCA auf dem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-178">: Workflow apps will be activated if the Workflow DCA is installed in the system.</span></span> <span data-ttu-id="5a8e7-179">Wenn die App nicht installiert ist, wird trotzdem gedruckt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-179">If the app is not installed, printing will still proceed.</span></span> 
* `Enabled`<span data-ttu-id="5a8e7-180">: Workflow-Contract wird aktiviert, wenn der Workflow-DCA auf dem System installiert ist.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-180">: Workflow contract will be activated if the Workflow DCA is installed in the system.</span></span> <span data-ttu-id="5a8e7-181">Wenn die App nicht installiert ist, schlägt das Drucken fehl.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-181">If the app is not installed, printing will fail.</span></span> 

<span data-ttu-id="5a8e7-182">Mit dem folgenden Befehl wird die Workflow-App auf dem angegebenen Drucker als erforderlich festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-182">The following command makes the workflow app required on the specified printer.</span></span>
```Powershell
Set-Printer –Name "Microsoft XPS Document Writer" -WorkflowPolicy On
```

<span data-ttu-id="5a8e7-183">Ein lokaler Benutzer kann diese Richtlinie auf einem lokalen Drucker ausführen, oder der Druckeradministrator kann diese Richtlinie auf dem Druckerserver ausführen.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-183">A local user can run this policy on a local printer, or, for enterprise implementation, the printer administrator can run this policy on the Print Server.</span></span> <span data-ttu-id="5a8e7-184">Die Richtlinie wird dann mit allen Client-Verbindungen synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-184">The policy will then be synchronized to all client connections.</span></span> <span data-ttu-id="5a8e7-185">Der Druckeradministrator kann diese Richtlinie immer dann verwenden, wenn ein neuer Drucker hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="5a8e7-185">The printer admin can use this policy whenever a new printer is added.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a8e7-186">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5a8e7-186">See also</span></span>

[<span data-ttu-id="5a8e7-187">Beispiel zur Workflow-App</span><span class="sxs-lookup"><span data-stu-id="5a8e7-187">Workflow app sample</span></span>](https://github.com/Microsoft/print-oem-samples)

[<span data-ttu-id="5a8e7-188">Namespace Windows.Graphics.Printing.Workflow</span><span class="sxs-lookup"><span data-stu-id="5a8e7-188">Windows.Graphics.Printing.Workflow namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.printing.workflow)


