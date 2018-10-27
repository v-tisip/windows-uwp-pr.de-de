---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe beim Aktualisieren der UWP-App
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
keywords: Windows 10, Uwp, Update, Hintergrundaufgabe, Updatetask, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 1ef6351bcf2ef57a1900c429ddcb65e5a2a4e67b
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5692439"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a><span data-ttu-id="a9538-104">Ausführen einer Hintergrundaufgabe beim Aktualisieren der UWP-App</span><span class="sxs-lookup"><span data-stu-id="a9538-104">Run a background task when your UWP app is updated</span></span>

<span data-ttu-id="a9538-105">Erfahren Sie, wie Sie eine Hintergrundaufgabe zu schreiben, die ausgeführt wird, nachdem Ihre Store-app (universelle Windows Plattform) aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="a9538-105">Learn how to write a background task that runs after your Universal Windows Platform (UWP) store app is updated.</span></span>

<span data-ttu-id="a9538-106">Die Hintergrundaufgabe Aufgabe aktualisieren wird vom Betriebssystem aufgerufen, nachdem der Benutzer zu einer app ein Update installiert, die auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="a9538-106">The Update Task background task is invoked by the operating system after the user installs an update to an app that is installed on the device.</span></span> <span data-ttu-id="a9538-107">Dadurch können Ihre app Initialisierung Aufgaben wie z. B. initialisieren einen neuen pushbenachrichtigungskanal, das Schema der Datenbank usw., zu aktualisieren, bevor der Benutzer die aktualisierte app startet.</span><span class="sxs-lookup"><span data-stu-id="a9538-107">This allows your app to perform initialization tasks such as initializing a new push notification channel, updating database schema, and so on, before the user launches your updated app.</span></span>

<span data-ttu-id="a9538-108">Die Update-Aufgabe unterscheidet sich von Starten einer Hintergrundaufgabe mithilfe des [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Triggers, da in diesem Fall Ihre app mindestens einmal ausführen muss, bevor er aktualisiert wird, um die Hintergrundaufgabe registrieren, die durch die **aktiviert werden ServicingComplete** Trigger.</span><span class="sxs-lookup"><span data-stu-id="a9538-108">The Update Task differs from launching a background task using the [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) trigger because in that case your app must run at least once before it is updated in order to register the background task that will be activated by the **ServicingComplete** trigger.</span></span>  <span data-ttu-id="a9538-109">Die Aufgabe aktualisieren ist nicht registriert, und eine app, die nie ausgeführt wurde, jedoch, die aktualisiert wird, muss daher noch seine Update Aufgabe ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a9538-109">The Update Task isn't registered and so an app that has never been run, but that is upgraded, will still have its update task triggered.</span></span>

## <a name="step-1-create-the-background-task-class"></a><span data-ttu-id="a9538-110">Schritt 1: Erstellen der hintergrundaufgabenklasse</span><span class="sxs-lookup"><span data-stu-id="a9538-110">Step 1: Create the background task class</span></span>

<span data-ttu-id="a9538-111">Als implementiert mit anderen Arten von Hintergrundaufgaben, die Hintergrundaufgabe Aktualisierungsaufgabe als Windows-Runtime-Komponente.</span><span class="sxs-lookup"><span data-stu-id="a9538-111">As with other types of background tasks, you implement the Update Task background task as a Windows Runtime component.</span></span> <span data-ttu-id="a9538-112">Um diese Komponente zu erstellen, führen Sie die Schritte im Abschnitt **zum Erstellen der Hintergrundaufgabe-Klasse** [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).</span><span class="sxs-lookup"><span data-stu-id="a9538-112">To create this component, follow the steps in the **Create the Background Task class** section of [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).</span></span> <span data-ttu-id="a9538-113">Dazu gehören die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="a9538-113">The steps include:</span></span>

- <span data-ttu-id="a9538-114">Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="a9538-114">Adding a Windows Runtime Component project to your solution.</span></span>
- <span data-ttu-id="a9538-115">Einen Verweis erstellen auf die Komponente von Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="a9538-115">Creating a reference from your app to the component.</span></span>
- <span data-ttu-id="a9538-116">Erstellen einer Klasse öffentlichen und versiegelten in der Komponente, wird [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)implementiert.</span><span class="sxs-lookup"><span data-stu-id="a9538-116">Creating a public, sealed class in the component that implements [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span></span>
- <span data-ttu-id="a9538-117">Implementieren die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) -Methode, d.h. der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn die Update-Aufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a9538-117">Implementing the [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method, which is the required entry point that is called when the Update Task is run.</span></span> <span data-ttu-id="a9538-118">Wenn Sie beabsichtigen, asynchrone Aufrufe über Ihre Hintergrundaufgabe auszuführen, erläutert [Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Verzögerung in der **Run** -Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="a9538-118">If you are going to make asynchronous calls from your background task, [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) explains how to use a deferral in your **Run** method.</span></span>

<span data-ttu-id="a9538-119">Sie müssen diese Hintergrundaufgabe (die "Registrieren der Hintergrundaufgabe ausführen" Abschnitt im Thema **Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe** ) zu registrieren, um den Update-Task zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a9538-119">You don't need to register this background task (the "Register the background task to run" section in the **Create and register an out-of-process background task** topic) to use the Update Task.</span></span> <span data-ttu-id="a9538-120">Dies ist der Hauptgrund für ein Update-Task verwenden, da Sie keinen Code zu Ihrer app zum Registrieren der Aufgabe hinzuzufügen müssen und die app keinen auf mindestens einmal vor dem aktualisiert, um die Hintergrundaufgabe registrieren ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a9538-120">This is the main reason to use an Update Task because you don't need to add any code to your app to register the task and the app doesn't have to at least run once before being updated to register the background task.</span></span>

<span data-ttu-id="a9538-121">Der folgende Beispielcode zeigt einen einfachen Startpunkt für eine Aufgabe Update-hintergrundaufgabenklasse in c#.</span><span class="sxs-lookup"><span data-stu-id="a9538-121">The following sample code shows a basic starting point for a Update Task background task class in C#.</span></span> <span data-ttu-id="a9538-122">Die hintergrundaufgabenklasse selbst- und alle anderen Klassen im hintergrundaufgabenprojekt - müssen **öffentlich** und **versiegelt**sein.</span><span class="sxs-lookup"><span data-stu-id="a9538-122">The background task class itself - and all other classes in the background task project - need to be **public** and **sealed**.</span></span> <span data-ttu-id="a9538-123">Die Klasse der Hintergrundaufgabe muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** Methode mit der Signatur unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="a9538-123">Your background task class must derive from **IBackgroundTask** and have a public **Run()** method with the signature shown below:</span></span>

```cs
using Windows.ApplicationModel.Background;

namespace BackgroundTasks
{
    public sealed class UpdateTask : IBackgroundTask
    {
        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // your app migration/update code here
        }
    }
}
```

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a><span data-ttu-id="a9538-124">Schritt 2: Deklarieren der Hintergrundaufgabe im Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="a9538-124">Step 2: Declare your background task in the package manifest</span></span>

<span data-ttu-id="a9538-125">Im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **"Package.appxmanifest"** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a9538-125">In the Visual Studio Solution Explorer, right-click **Package.appxmanifest** and click **View Code** to view the package manifest.</span></span> <span data-ttu-id="a9538-126">Fügen Sie die folgenden `<Extensions>` XML, Ihre Update-Task zu deklarieren:</span><span class="sxs-lookup"><span data-stu-id="a9538-126">Add the following `<Extensions>` XML to declare your update task:</span></span>

```XML
<Package ...>
    ...
  <Applications>  
    <Application ...>  
        ...
      <Extensions>  
        <Extension Category="windows.updateTask"  EntryPoint="BackgroundTasks.UpdateTask">  
        </Extension>  
      </Extensions>

    </Application>  
  </Applications>  
</Package>
```

<span data-ttu-id="a9538-127">Im obigen XML stellen sicher, dass die `EntryPoint` -Attribut auf den Namen namespace.class Ihre Update Task-Klasse festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a9538-127">In the XML above, ensure that the `EntryPoint` attribute is set to the namespace.class name of your update task class.</span></span> <span data-ttu-id="a9538-128">Der Name ist Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="a9538-128">The name is case-sensitive.</span></span>

## <a name="step-3-debugtest-your-update-task"></a><span data-ttu-id="a9538-129">Schritt 3: Debug/Test Ihre Aufgabe Update</span><span class="sxs-lookup"><span data-stu-id="a9538-129">Step 3: Debug/test your Update task</span></span>

<span data-ttu-id="a9538-130">Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, damit etwas zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a9538-130">Ensure that you have deployed your app to your machine so that there is something to update.</span></span>

<span data-ttu-id="a9538-131">Legen Sie einen Haltepunkt in der Methode Run() Ihrer Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="a9538-131">Set a breakpoint in the Run() method of your background task.</span></span>

![Set Haltepunkt](images/run-func-breakpoint.png)

<span data-ttu-id="a9538-133">Als Nächstes im Projektmappen-Explorer mit der rechten Maustaste in der app Projekt (nicht das hintergrundaufgabenprojekt), und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="a9538-133">Next, in the solution explorer, right-click your app's project (not the background task project) and then click **Properties**.</span></span> <span data-ttu-id="a9538-134">Klicken Sie im Eigenschaftenfenster Anwendung auf der linken Seite auf **Debuggen** , und wählen Sie dann **zunächst nicht starten, sondern Debuggen mein Code, der beim Start**:</span><span class="sxs-lookup"><span data-stu-id="a9538-134">In the application Properties window, click **Debug** on the left, then select **Do not launch, but debug my code when it starts**:</span></span>

![Legen Sie die Debugeinstellungen](images/do-not-launch-but-debug.png)

<span data-ttu-id="a9538-136">Um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie als Nächstes Versionsnummer des Pakets.</span><span class="sxs-lookup"><span data-stu-id="a9538-136">Next, to ensure that the UpdateTask is triggered, increase the package's version number.</span></span> <span data-ttu-id="a9538-137">Klicken Sie im Projektmappen-Explorer doppelklicken Sie auf der app **Datei "Package.appxmanifest** ", um den Designer zu öffnen, und aktualisieren Sie die **Build** -Nummer:</span><span class="sxs-lookup"><span data-stu-id="a9538-137">In the Solution Explorer, double-click your app's **Package.appxmanifest** file to open the package designer, and then update the **Build** number:</span></span>

![Aktualisieren Sie die version](images/bump-version.png)

<span data-ttu-id="a9538-139">Nun in Visual Studio 2017 Wenn Sie F5 drücken, wird Ihre app aktualisiert werden, und das System wird Ihre Komponente UpdateTask im Hintergrund aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a9538-139">Now, in Visual Studio 2017 when you press F5, your app will be updated and the system will activate your UpdateTask component in the background.</span></span> <span data-ttu-id="a9538-140">Der Debugger wird automatisch mit dem Hintergrundprozess um.</span><span class="sxs-lookup"><span data-stu-id="a9538-140">The debugger will automatically attach to the background process.</span></span> <span data-ttu-id="a9538-141">Ihre Haltepunkt wird erreicht abrufen und Sie können Ihre Codelogik Update schrittweise.</span><span class="sxs-lookup"><span data-stu-id="a9538-141">Your breakpoint will get hit and you can step through your update code logic.</span></span>

<span data-ttu-id="a9538-142">Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Menü "Start" in der gleichen Debugsitzung starten.</span><span class="sxs-lookup"><span data-stu-id="a9538-142">When the background task completes, you can launch the foreground app from the Windows start menu within the same debug session.</span></span> <span data-ttu-id="a9538-143">Automatisch wieder der Debugger angehängt wird, wird dieses Mal im Vordergrund-Prozess, und Sie können Ihre app-Logik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="a9538-143">The debugger will again automatically attach, this time to your foreground process, and you can step through your app's logic.</span></span>

> [!NOTE]
> <span data-ttu-id="a9538-144">Benutzer von Visual Studio 2015: die oben genannten Schritte gelten für Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a9538-144">Visual Studio 2015 users: The above steps apply to Visual Studio 2017.</span></span> <span data-ttu-id="a9538-145">Wenn Sie Visual Studio 2015 verwenden, können Sie die gleichen Techniken zur Trigger und Testen der UpdateTask, mit Ausnahme von Visual Studio keine Verbindung herstellen wird.</span><span class="sxs-lookup"><span data-stu-id="a9538-145">If you are using Visual Studio 2015, you can use the same techniques to trigger and test the UpdateTask, except Visual Studio will not attach to it.</span></span> <span data-ttu-id="a9538-146">Eine andere Möglichkeit ist, richten Sie eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask als Einsprungpunkt festlegt, und lösen Sie die Ausführung direkt von der Vordergrund-app in VS 2015.</span><span class="sxs-lookup"><span data-stu-id="a9538-146">An alternative procedure in VS 2015 is to setup an [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) that sets the UpdateTask as its Entry Point, and trigger the execution directly from the foreground app.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9538-147">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="a9538-147">See also</span></span>

[<span data-ttu-id="a9538-148">Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="a9538-148">Create and register an out-of-process background task</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
