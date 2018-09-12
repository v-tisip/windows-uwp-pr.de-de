---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10 Uwp Update, Hintergrund, Updatetask, Hintergrund
ms.localizationpriority: medium
ms.openlocfilehash: fcba2cb736f86cebc6d2664e2ec3b557d47c86d7
ms.sourcegitcommit: 2a63ee6770413bc35ace09b14f56b60007be7433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2018
ms.locfileid: "3931282"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a><span data-ttu-id="b6322-104">Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird</span><span class="sxs-lookup"><span data-stu-id="b6322-104">Run a background task when your UWP app is updated</span></span>

<span data-ttu-id="b6322-105">Erfahren Sie, wie eine Hintergrundaufgabe schreiben, nachdem Ihre app universelle Windows-Plattform (UWP) Speicher aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="b6322-105">Learn how to write a background task that runs after your Universal Windows Platform (UWP) store app is updated.</span></span>

<span data-ttu-id="b6322-106">Hintergrundtask Aktualisierung wird vom Betriebssystem aufgerufen, nachdem ein Update auf eine Anwendung installiert, die auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b6322-106">The Update Task background task is invoked by the operating system after the user installs an update to an app that is installed on the device.</span></span> <span data-ttu-id="b6322-107">Dadurch wird Ihre app Initialisierung Aufgaben wie initialisieren einen neuen Kanal zur Push-Benachrichtigung, Datenbankschema usw., zu aktualisieren, bevor der Benutzer die aktualisierte Anwendung startet.</span><span class="sxs-lookup"><span data-stu-id="b6322-107">This allows your app to perform initialization tasks such as initializing a new push notification channel, updating database schema, and so on, before the user launches your updated app.</span></span>

<span data-ttu-id="b6322-108">Unterscheidet sich der Update-Task starten eine Hintergrundaufgabe [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Trigger verwenden, da in diesem Fall Ihre Anwendung mindestens einmal ausgeführt werden muss vor der Aktualisierung den Hintergrundtask registrieren, der von der **aktiviert werden ServicingComplete** Trigger.</span><span class="sxs-lookup"><span data-stu-id="b6322-108">The Update Task differs from launching a background task using the [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) trigger because in that case your app must run at least once before it is updated in order to register the background task that will be activated by the **ServicingComplete** trigger.</span></span>  <span data-ttu-id="b6322-109">Update-Task ist nicht registriert und so eine app, die nie ausgeführt wurden aber, die aktualisiert wird, wird weiterhin der Update-Task ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b6322-109">The Update Task isn't registered and so an app that has never been run, but that is upgraded, will still have its update task triggered.</span></span>

## <a name="step-1-create-the-background-task-class"></a><span data-ttu-id="b6322-110">Schritt 1: Erstellen der hintergrundaufgabenklasse</span><span class="sxs-lookup"><span data-stu-id="b6322-110">Step 1: Create the background task class</span></span>

<span data-ttu-id="b6322-111">Als implementiert mit anderen Hintergrundaufgaben Hintergrundtask Aktualisierungstask als Windows-Runtime-Komponente.</span><span class="sxs-lookup"><span data-stu-id="b6322-111">As with other types of background tasks, you implement the Update Task background task as a Windows Runtime component.</span></span> <span data-ttu-id="b6322-112">Um diese Komponente zu erstellen, führen Sie die Schritte im Abschnitt **Erstellen Hintergrundtask Klasse** [Erstellen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)und einen prozessexternen der Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="b6322-112">To create this component, follow the steps in the **Create the Background Task class** section of [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).</span></span> <span data-ttu-id="b6322-113">Dazu gehören die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="b6322-113">The steps include:</span></span>

- <span data-ttu-id="b6322-114">Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="b6322-114">Adding a Windows Runtime Component project to your solution.</span></span>
- <span data-ttu-id="b6322-115">Erstellen eines Verweises auf die Komponente Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b6322-115">Creating a reference from your app to the component.</span></span>
- <span data-ttu-id="b6322-116">Öffentliche, versiegelte Klasse in der Komponente erstellen, die implementiert [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span><span class="sxs-lookup"><span data-stu-id="b6322-116">Creating a public, sealed class in the component that implements [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span></span>
- <span data-ttu-id="b6322-117">Implementieren der Methode [**ausgeführt**](https://msdn.microsoft.com/library/windows/apps/br224811) , ist die erforderlichen Einstiegspunkt, der aufgerufen wird, wenn der Update-Task ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b6322-117">Implementing the [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method, which is the required entry point that is called when the Update Task is run.</span></span> <span data-ttu-id="b6322-118">Wenn Sie asynchrone Aufrufe von der Hintergrundaufgabe möchten, erläutert [Erstellen und Registrieren einer prozessexternen der Hintergrundtask](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Rückstellung in der **Run** -Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="b6322-118">If you are going to make asynchronous calls from your background task, [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) explains how to use a deferral in your **Run** method.</span></span>

<span data-ttu-id="b6322-119">Sie müssen diese Hintergrundaufgabe (dem Bereich "Registrieren der Hintergrundtask ausgeführt" im Thema **Erstellen und Registrieren einer Hintergrundaufgabe von prozessexternen** ) anmelden den Update-Task.</span><span class="sxs-lookup"><span data-stu-id="b6322-119">You don't need to register this background task (the "Register the background task to run" section in the **Create and register an out-of-process background task** topic) to use the Update Task.</span></span> <span data-ttu-id="b6322-120">Dies ist der Hauptgrund, einen Update-Task verwenden, da Sie Code für Ihre Anwendung registrieren die Aufgabe hinzufügen müssen und die app nicht mindestens einmal vor der Aktualisierung registrieren Hintergrundtask ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b6322-120">This is the main reason to use an Update Task because you don't need to add any code to your app to register the task and the app doesn't have to at least run once before being updated to register the background task.</span></span>

<span data-ttu-id="b6322-121">Der folgende Beispielcode zeigt grundlegenden Ausgangspunkt für eine Update-Task hintergrundaufgabenklasse in C#.</span><span class="sxs-lookup"><span data-stu-id="b6322-121">The following sample code shows a basic starting point for a Update Task background task class in C#.</span></span> <span data-ttu-id="b6322-122">Hintergrundaufgabenklasse selbst- und andere Klassen im Projekt Aufgabe Hintergrund - müssen **Öffentliche** und **versiegelt**sein.</span><span class="sxs-lookup"><span data-stu-id="b6322-122">The background task class itself - and all other classes in the background task project - need to be **public** and **sealed**.</span></span> <span data-ttu-id="b6322-123">Die Hintergrund Aufgabenklasse muss **IBackgroundTask** ableiten und öffentliche **Run()** Methode mit der Signatur unten:</span><span class="sxs-lookup"><span data-stu-id="b6322-123">Your background task class must derive from **IBackgroundTask** and have a public **Run()** method with the signature shown below:</span></span>

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

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a><span data-ttu-id="b6322-124">Schritt 2: Deklarieren der Hintergrundtask im Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="b6322-124">Step 2: Declare your background task in the package manifest</span></span>

<span data-ttu-id="b6322-125">Im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **Package.appxmanifest** und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6322-125">In the Visual Studio Solution Explorer, right-click **Package.appxmanifest** and click **View Code** to view the package manifest.</span></span> <span data-ttu-id="b6322-126">Fügen Sie den folgenden `<Extensions>` XML der Aktualisierungstask deklarieren:</span><span class="sxs-lookup"><span data-stu-id="b6322-126">Add the following `<Extensions>` XML to declare your update task:</span></span>

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

<span data-ttu-id="b6322-127">Im obigen XML stellen sicher, dass die `EntryPoint` Attributsatz namespace.class Namen der Klasse Aufgabe aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b6322-127">In the XML above, ensure that the `EntryPoint` attribute is set to the namespace.class name of your update task class.</span></span> <span data-ttu-id="b6322-128">Der Namen beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="b6322-128">The name is case-sensitive.</span></span>

## <a name="step-3-debugtest-your-update-task"></a><span data-ttu-id="b6322-129">Schritt 3: Debug/Test der Update-task</span><span class="sxs-lookup"><span data-stu-id="b6322-129">Step 3: Debug/test your Update task</span></span>

<span data-ttu-id="b6322-130">Stellen Sie sicher, dass Sie Ihre Anwendung auf Ihrem Computer bereitgestellt haben, damit etwas aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b6322-130">Ensure that you have deployed your app to your machine so that there is something to update.</span></span>

<span data-ttu-id="b6322-131">Legen Sie einen Haltepunkt in der Run() der Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="b6322-131">Set a breakpoint in the Run() method of your background task.</span></span>

![Haltepunkt festlegen](images/run-func-breakpoint.png)

<span data-ttu-id="b6322-133">Anschließend im Projektmappen-Explorer klicken Sie app Projekt (nicht der Hintergrund Task) und dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="b6322-133">Next, in the solution explorer, right-click your app's project (not the background task project) and then click **Properties**.</span></span> <span data-ttu-id="b6322-134">Im Eigenschaftenfenster Anwendung **Debuggen** links klicken **nicht gestartet, aber mein Code beim Start zu debuggen**:</span><span class="sxs-lookup"><span data-stu-id="b6322-134">In the application Properties window, click **Debug** on the left, then select **Do not launch, but debug my code when it starts**:</span></span>

![Festlegen von Debuggereinstellungen](images/do-not-launch-but-debug.png)

<span data-ttu-id="b6322-136">Weiter, um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie das Paket Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="b6322-136">Next, to ensure that the UpdateTask is triggered, increase the package's version number.</span></span> <span data-ttu-id="b6322-137">Doppelklicken Sie im Projektmappen-Explorer auf Ihre app **Package.appxmanifest** im Paket-Designer öffnen und aktualisieren Sie **der Buildnummer** :</span><span class="sxs-lookup"><span data-stu-id="b6322-137">In the Solution Explorer, double-click your app's **Package.appxmanifest** file to open the package designer, and then update the **Build** number:</span></span>

![Aktualisieren Sie die version](images/bump-version.png)

<span data-ttu-id="b6322-139">Nun Visual Studio 2017 Wenn Sie F5 drücken, Ihre app aktualisiert und das System aktivieren UpdateTask Komponente im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="b6322-139">Now, in Visual Studio 2017 when you press F5, your app will be updated and the system will activate your UpdateTask component in the background.</span></span> <span data-ttu-id="b6322-140">Der Debugger wird automatisch im Hintergrundprozess zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b6322-140">The debugger will automatically attach to the background process.</span></span> <span data-ttu-id="b6322-141">Der Haltepunkt getroffen wird und der Aktualisierungslogik Code durchgehen.</span><span class="sxs-lookup"><span data-stu-id="b6322-141">Your breakpoint will get hit and you can step through your update code logic.</span></span>

<span data-ttu-id="b6322-142">Wenn der Hintergrundtask können Sie die Vordergrund-app im Windows-Startmenü innerhalb derselben Debugsitzung starten.</span><span class="sxs-lookup"><span data-stu-id="b6322-142">When the background task completes, you can launch the foreground app from the Windows start menu within the same debug session.</span></span> <span data-ttu-id="b6322-143">Debugger wird automatisch angefügt, diesmal der Vordergrundprozess und der Anwendungslogik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="b6322-143">The debugger will again automatically attach, this time to your foreground process, and you can step through your app's logic.</span></span>

> [!NOTE]
> <span data-ttu-id="b6322-144">Visual Studio 2015 Benutzer: die oben beschriebenen Schritte gelten für Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b6322-144">Visual Studio 2015 users: The above steps apply to Visual Studio 2017.</span></span> <span data-ttu-id="b6322-145">Wenn Sie Visual Studio 2015 verwenden, können Sie dasselbe Trigger und Test UpdateTask mit Ausnahme von Visual Studio nicht anfügen wird.</span><span class="sxs-lookup"><span data-stu-id="b6322-145">If you are using Visual Studio 2015, you can use the same techniques to trigger and test the UpdateTask, except Visual Studio will not attach to it.</span></span> <span data-ttu-id="b6322-146">Eine andere Möglichkeit ist eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask als Einsprungpunkt festlegt, zu lösen die Ausführung direkt von der Vordergrund-app VS 2015.</span><span class="sxs-lookup"><span data-stu-id="b6322-146">An alternative procedure in VS 2015 is to setup an [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) that sets the UpdateTask as its Entry Point, and trigger the execution directly from the foreground app.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6322-147">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="b6322-147">See also</span></span>

[<span data-ttu-id="b6322-148">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="b6322-148">Create and register an out-of-process background task</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
