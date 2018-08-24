---
author: TylerMSFT
title: Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 04/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Update, Hintergrund, Updatetask, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: fcba2cb736f86cebc6d2664e2ec3b557d47c86d7
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2831072"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a><span data-ttu-id="0e5ae-104">Ausführen einer Hintergrundaufgabe, wenn Ihre UWP-App aktualisiert wird</span><span class="sxs-lookup"><span data-stu-id="0e5ae-104">Run a background task when your UWP app is updated</span></span>

<span data-ttu-id="0e5ae-105">Erfahren Sie, wie eine Hintergrundaufgabe zu schreiben, die ausgeführt wird, nach der Aktualisierung Ihrer universellen Windows-Plattform (UWP) Store-app.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-105">Learn how to write a background task that runs after your Universal Windows Platform (UWP) store app is updated.</span></span>

<span data-ttu-id="0e5ae-106">Die Aufgabe aktualisieren Hintergrundaufgabe wird vom Betriebssystem aufgerufen, nachdem der Benutzer eine app, die auf dem Gerät installiert ist, ein Update installiert.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-106">The Update Task background task is invoked by the operating system after the user installs an update to an app that is installed on the device.</span></span> <span data-ttu-id="0e5ae-107">Dadurch kann Ihre app für Initialisierung Aufgaben wie die Initialisierung eines neuen Push Notification-Kanals, Datenbankschema usw., zu aktualisieren, bevor der Benutzer Ihre aktualisierte app startet.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-107">This allows your app to perform initialization tasks such as initializing a new push notification channel, updating database schema, and so on, before the user launches your updated app.</span></span>

<span data-ttu-id="0e5ae-108">Die Update-Aufgabe unterscheidet sich von Starten einer Hintergrundaufgabe den Auslöser [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) verwenden, da in diesem Fall Ihre app mindestens einmal ausgeführt werden muss, bevor sie aktualisiert werden, um die Hintergrundaufgabe zu registrieren, die durch die **aktiviert werden ServicingComplete** Trigger.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-108">The Update Task differs from launching a background task using the [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) trigger because in that case your app must run at least once before it is updated in order to register the background task that will be activated by the **ServicingComplete** trigger.</span></span>  <span data-ttu-id="0e5ae-109">Die Aufgabe aktualisieren ist nicht registriert, und eine app, die nie ausgeführt wurden, aber, die aktualisiert wird, muss also noch seine Update Aufgabe ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-109">The Update Task isn't registered and so an app that has never been run, but that is upgraded, will still have its update task triggered.</span></span>

## <a name="step-1-create-the-background-task-class"></a><span data-ttu-id="0e5ae-110">Schritt 1: Erstellen der Hintergrund Task-Klasse</span><span class="sxs-lookup"><span data-stu-id="0e5ae-110">Step 1: Create the background task class</span></span>

<span data-ttu-id="0e5ae-111">Als implementieren mit anderen Arten von Hintergrundaufgaben, Sie die Update-Task Hintergrundaufgabe als Windows-Runtime-Komponente.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-111">As with other types of background tasks, you implement the Update Task background task as a Windows Runtime component.</span></span> <span data-ttu-id="0e5ae-112">Wenn diese Komponente erstellen möchten, führen Sie die Schritte im Abschnitt **Erstellen der Hintergrundtask-Klasse** [Erstellen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)und Registrieren einer Hintergrundaufgabe Out-of-Process.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-112">To create this component, follow the steps in the **Create the Background Task class** section of [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).</span></span> <span data-ttu-id="0e5ae-113">Dazu gehören die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="0e5ae-113">The steps include:</span></span>

- <span data-ttu-id="0e5ae-114">Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="0e5ae-114">Adding a Windows Runtime Component project to your solution.</span></span>
- <span data-ttu-id="0e5ae-115">Erstellen einen Verweis aus Ihrer app für die Komponente.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-115">Creating a reference from your app to the component.</span></span>
- <span data-ttu-id="0e5ae-116">Erstellen einer öffentlichen, versiegelten-Klasse in der Komponente implementiert [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span><span class="sxs-lookup"><span data-stu-id="0e5ae-116">Creating a public, sealed class in the component that implements [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span></span>
- <span data-ttu-id="0e5ae-117">Implementieren die [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) -Methode, ist die der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn die Update-Task ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-117">Implementing the [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method, which is the required entry point that is called when the Update Task is run.</span></span> <span data-ttu-id="0e5ae-118">Wenn Sie beabsichtigen, asynchrone Aufrufe von Ihrer Hintergrundaufgabe erläutert [Erstellen und Registrieren einer Hintergrundaufgabe Out-of-Process-](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) eine Rückstellung in die **Run** -Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-118">If you are going to make asynchronous calls from your background task, [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) explains how to use a deferral in your **Run** method.</span></span>

<span data-ttu-id="0e5ae-119">Sie müssen sich nicht für diese Hintergrundaufgabe (dem Bereich "Registrieren die Hintergrundtask ausgeführt" im Thema **Create and Register eine Hintergrundaufgabe Out-of-Process-** ) anmelden, um den Update-Vorgang verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-119">You don't need to register this background task (the "Register the background task to run" section in the **Create and register an out-of-process background task** topic) to use the Update Task.</span></span> <span data-ttu-id="0e5ae-120">Dies ist der Hauptgrund eine Update-Task verwendet werden, da Sie keinen Code Ihrer app brauchen so registrieren Sie die Aufgabe hinzufügen und die app muss nicht mindestens einmal aufrufen, bevor aktualisiert, um die Hintergrundaufgabe registrieren ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-120">This is the main reason to use an Update Task because you don't need to add any code to your app to register the task and the app doesn't have to at least run once before being updated to register the background task.</span></span>

<span data-ttu-id="0e5ae-121">Der folgende Beispielcode zeigt grundlegenden Ausgangspunkt für eine Update-Task Hintergrund Task-Klasse in c#.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-121">The following sample code shows a basic starting point for a Update Task background task class in C#.</span></span> <span data-ttu-id="0e5ae-122">Der Hintergrund Task-Klasse selbst- und alle anderen Klassen im Hintergrund Aufgabe Projekt - müssen **Öffentliche** und **versiegelt**sein.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-122">The background task class itself - and all other classes in the background task project - need to be **public** and **sealed**.</span></span> <span data-ttu-id="0e5ae-123">Die Hintergrund Task-Klasse muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** -Methode mit der Signatur der unten gezeigten:</span><span class="sxs-lookup"><span data-stu-id="0e5ae-123">Your background task class must derive from **IBackgroundTask** and have a public **Run()** method with the signature shown below:</span></span>

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

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a><span data-ttu-id="0e5ae-124">Schritt 2: Deklarieren Sie Ihrer Hintergrundaufgabe in der Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="0e5ae-124">Step 2: Declare your background task in the package manifest</span></span>

<span data-ttu-id="0e5ae-125">In Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **Package.appxmanifest** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-125">In the Visual Studio Solution Explorer, right-click **Package.appxmanifest** and click **View Code** to view the package manifest.</span></span> <span data-ttu-id="0e5ae-126">Fügen Sie die folgenden `<Extensions>` XML Update-Task deklariert:</span><span class="sxs-lookup"><span data-stu-id="0e5ae-126">Add the following `<Extensions>` XML to declare your update task:</span></span>

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

<span data-ttu-id="0e5ae-127">In den XML sicher, dass die `EntryPoint` -Attribut wird auf den Namen Namespace.Klasse Ihrer Update-Task-Klasse festgelegt.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-127">In the XML above, ensure that the `EntryPoint` attribute is set to the namespace.class name of your update task class.</span></span> <span data-ttu-id="0e5ae-128">Der Name ist die Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-128">The name is case-sensitive.</span></span>

## <a name="step-3-debugtest-your-update-task"></a><span data-ttu-id="0e5ae-129">Schritt 3: Debug/Test Update-task</span><span class="sxs-lookup"><span data-stu-id="0e5ae-129">Step 3: Debug/test your Update task</span></span>

<span data-ttu-id="0e5ae-130">Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, sodass etwas aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-130">Ensure that you have deployed your app to your machine so that there is something to update.</span></span>

<span data-ttu-id="0e5ae-131">Setzen Sie einen Haltepunkt in der Run()-Methode der Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-131">Set a breakpoint in the Run() method of your background task.</span></span>

![Haltepunkt festlegen](images/run-func-breakpoint.png)

<span data-ttu-id="0e5ae-133">Im nächsten Schritt im Projektmappen-Explorer mit der rechten Maustaste Ihrer app-Projekt (nicht das Vorgangsfeld Projekt Hintergrund), und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-133">Next, in the solution explorer, right-click your app's project (not the background task project) and then click **Properties**.</span></span> <span data-ttu-id="0e5ae-134">Klicken Sie im Fenster Eigenschaften Application auf der linken Seite auf **Debuggen** , und wählen Sie dann **nicht gestartet, aber mein Code beim Start zu debuggen**:</span><span class="sxs-lookup"><span data-stu-id="0e5ae-134">In the application Properties window, click **Debug** on the left, then select **Do not launch, but debug my code when it starts**:</span></span>

![Debug-Einstellungen](images/do-not-launch-but-debug.png)

<span data-ttu-id="0e5ae-136">Im nächsten Schritt, um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie das Paket Versionsnummer an.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-136">Next, to ensure that the UpdateTask is triggered, increase the package's version number.</span></span> <span data-ttu-id="0e5ae-137">Doppelklicken Sie im Projektmappen-Explorer auf Ihre app **Package.appxmanifest** Datei, um den Paketdesigner zu öffnen, und klicken Sie dann aktualisieren Sie **der Buildnummer** :</span><span class="sxs-lookup"><span data-stu-id="0e5ae-137">In the Solution Explorer, double-click your app's **Package.appxmanifest** file to open the package designer, and then update the **Build** number:</span></span>

![Aktualisieren der version](images/bump-version.png)

<span data-ttu-id="0e5ae-139">Nun in Visual Studio 2017 Wenn Sie F5 drücken, Ihre app werden aktualisiert, und das System wird die UpdateTask-Komponente im Hintergrund aktiviert.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-139">Now, in Visual Studio 2017 when you press F5, your app will be updated and the system will activate your UpdateTask component in the background.</span></span> <span data-ttu-id="0e5ae-140">Der Debugger wird automatisch an den Hintergrundprozess.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-140">The debugger will automatically attach to the background process.</span></span> <span data-ttu-id="0e5ae-141">Der Haltepunkt wird erreicht erhalten möchten, und können Sie Ihr Code Aktualisierungslogik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-141">Your breakpoint will get hit and you can step through your update code logic.</span></span>

<span data-ttu-id="0e5ae-142">Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Startmenü innerhalb der gleichen Sitzung Debuggen starten.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-142">When the background task completes, you can launch the foreground app from the Windows start menu within the same debug session.</span></span> <span data-ttu-id="0e5ae-143">Der Debugger wird automatisch erneut angefügt werden, diesmal den Prozess Vordergrund und können Sie Ihre app Logik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-143">The debugger will again automatically attach, this time to your foreground process, and you can step through your app's logic.</span></span>

> [!NOTE]
> <span data-ttu-id="0e5ae-144">Benutzer von Visual Studio 2015: die oben beschriebenen Schritte gelten für Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-144">Visual Studio 2015 users: The above steps apply to Visual Studio 2017.</span></span> <span data-ttu-id="0e5ae-145">Wenn Sie Visual Studio 2015 verwenden, können Sie dieselben Techniken Trigger und Testen der UpdateTask, mit Ausnahme von Visual Studio nicht darauf angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-145">If you are using Visual Studio 2015, you can use the same techniques to trigger and test the UpdateTask, except Visual Studio will not attach to it.</span></span> <span data-ttu-id="0e5ae-146">Ein alternatives Verfahren in VS 2015 ist zum Einrichten einer [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die die UpdateTask als ihr Einstiegspunkt festlegt, und lösen die Ausführung direkt in den Vordergrund-app.</span><span class="sxs-lookup"><span data-stu-id="0e5ae-146">An alternative procedure in VS 2015 is to setup an [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) that sets the UpdateTask as its Entry Point, and trigger the execution directly from the foreground app.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e5ae-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0e5ae-147">See also</span></span>

[<span data-ttu-id="0e5ae-148">Erstellen und Registrieren einer Hintergrundaufgabe außerhalb des Prozesses</span><span class="sxs-lookup"><span data-stu-id="0e5ae-148">Create and register an out-of-process background task</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
