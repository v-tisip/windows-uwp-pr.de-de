---
title: Ausführen einer Hintergrundaufgabe beim Aktualisieren der UWP-App
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.date: 04/21/2017
ms.topic: article
keywords: Windows 10, Uwp, Update, Hintergrundaufgabe, Updatetask, Hintergrundaufgabe
ms.localizationpriority: medium
ms.openlocfilehash: 8cd7d4494340d1c5e617361f2e3d750b35ebabb9
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8933984"
---
# <a name="run-a-background-task-when-your-uwp-app-is-updated"></a><span data-ttu-id="fb789-104">Ausführen einer Hintergrundaufgabe beim Aktualisieren der UWP-App</span><span class="sxs-lookup"><span data-stu-id="fb789-104">Run a background task when your UWP app is updated</span></span>

<span data-ttu-id="fb789-105">Erfahren Sie, wie Sie eine Hintergrundaufgabe zu schreiben, die ausgeführt wird, nachdem die Store-app für universelle Windows-Plattform (UWP) aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="fb789-105">Learn how to write a background task that runs after your Universal Windows Platform (UWP) store app is updated.</span></span>

<span data-ttu-id="fb789-106">Die Hintergrundaufgabe aktualisieren Aufgabe wird vom Betriebssystem aufgerufen, nachdem der Benutzer zu einer app ein Update installiert, die auf dem Gerät installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fb789-106">The Update Task background task is invoked by the operating system after the user installs an update to an app that is installed on the device.</span></span> <span data-ttu-id="fb789-107">Dies kann Ihre app Initialisierung Aufgaben wie z. B. die Initialisierung eines neuen Kanals für Pushbenachrichtigungen, Datenbankschema usw., aktualisieren, bevor der Benutzer die aktualisierte app startet.</span><span class="sxs-lookup"><span data-stu-id="fb789-107">This allows your app to perform initialization tasks such as initializing a new push notification channel, updating database schema, and so on, before the user launches your updated app.</span></span>

<span data-ttu-id="fb789-108">Das Update Task unterscheidet sich von Starten einer Hintergrundaufgabe mithilfe des [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) Triggers, da in diesem Fall Ihre app mindestens einmal ausgeführt werden muss, bevor sie aktualisiert werden, um die Hintergrundaufgabe zu registrieren, die durch die **aktiviert werden ServicingComplete** Trigger.</span><span class="sxs-lookup"><span data-stu-id="fb789-108">The Update Task differs from launching a background task using the [ServicingComplete](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.SystemTriggerType) trigger because in that case your app must run at least once before it is updated in order to register the background task that will be activated by the **ServicingComplete** trigger.</span></span>  <span data-ttu-id="fb789-109">Die Aufgabe aktualisieren ist nicht registriert, und daher eine app, die nie ausgeführt wurde, jedoch, die aktualisiert wird, wird immer noch die Update-Aufgabe ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="fb789-109">The Update Task isn't registered and so an app that has never been run, but that is upgraded, will still have its update task triggered.</span></span>

## <a name="step-1-create-the-background-task-class"></a><span data-ttu-id="fb789-110">Schritt 1: Erstellen der hintergrundaufgabenklasse</span><span class="sxs-lookup"><span data-stu-id="fb789-110">Step 1: Create the background task class</span></span>

<span data-ttu-id="fb789-111">Als implementiert mit anderen Arten von Hintergrundaufgaben, die Hintergrundaufgabe Update-Task als Windows-Runtime-Komponente.</span><span class="sxs-lookup"><span data-stu-id="fb789-111">As with other types of background tasks, you implement the Update Task background task as a Windows Runtime component.</span></span> <span data-ttu-id="fb789-112">Führen Sie die Schritte im Abschnitt **zum Erstellen der Hintergrundaufgabe-Klasse** [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task), um diese Komponente zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fb789-112">To create this component, follow the steps in the **Create the Background Task class** section of [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).</span></span> <span data-ttu-id="fb789-113">Dazu gehören die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="fb789-113">The steps include:</span></span>

- <span data-ttu-id="fb789-114">Hinzufügen eines Projekts für eine Komponente für Windows-Runtime zu Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="fb789-114">Adding a Windows Runtime Component project to your solution.</span></span>
- <span data-ttu-id="fb789-115">Erstellen einen Verweis auf die Komponente von Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="fb789-115">Creating a reference from your app to the component.</span></span>
- <span data-ttu-id="fb789-116">Erstellen eine Klasse öffentliche und versiegelte in der Komponente, die wird [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)implementiert.</span><span class="sxs-lookup"><span data-stu-id="fb789-116">Creating a public, sealed class in the component that implements [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794).</span></span>
- <span data-ttu-id="fb789-117">Implementieren die Methode [**ausgeführt**](https://msdn.microsoft.com/library/windows/apps/br224811) , ist die der erforderlichen Einstiegspunkt, der aufgerufen wird, wenn die Update-Aufgabe ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fb789-117">Implementing the [**Run**](https://msdn.microsoft.com/library/windows/apps/br224811) method, which is the required entry point that is called when the Update Task is run.</span></span> <span data-ttu-id="fb789-118">Wenn Sie beabsichtigen, asynchrone Aufrufe über Ihre Hintergrundaufgabe auszuführen, erläutert [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) , wie Sie eine Verzögerung in der **Run** -Methode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb789-118">If you are going to make asynchronous calls from your background task, [Create and register an out-of-process background task](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task) explains how to use a deferral in your **Run** method.</span></span>

<span data-ttu-id="fb789-119">Sie müssen diese Hintergrundaufgabe (die "Registrieren der Hintergrundaufgabe ausführen" Abschnitt im Thema **Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen** ) zu registrieren, um die Update-Aufgabe zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fb789-119">You don't need to register this background task (the "Register the background task to run" section in the **Create and register an out-of-process background task** topic) to use the Update Task.</span></span> <span data-ttu-id="fb789-120">Dies ist der Hauptgrund für eine Aufgabe Update verwenden, da Sie keinen Code zu Ihrer app zum Registrieren der Aufgabe hinzufügen müssen und die app nicht ausgeführt mindestens einmal vor dem aktualisiert, um die Hintergrundaufgabe zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="fb789-120">This is the main reason to use an Update Task because you don't need to add any code to your app to register the task and the app doesn't have to at least run once before being updated to register the background task.</span></span>

<span data-ttu-id="fb789-121">Der folgende Beispielcode zeigt einen einfachen Startpunkt für eine hintergrundaufgabenklasse Aktualisierungsaufgabe in c#.</span><span class="sxs-lookup"><span data-stu-id="fb789-121">The following sample code shows a basic starting point for a Update Task background task class in C#.</span></span> <span data-ttu-id="fb789-122">Die hintergrundaufgabenklasse selbst- und alle anderen Klassen im hintergrundaufgabenprojekt - müssen **öffentlich** und **versiegelt**sein.</span><span class="sxs-lookup"><span data-stu-id="fb789-122">The background task class itself - and all other classes in the background task project - need to be **public** and **sealed**.</span></span> <span data-ttu-id="fb789-123">Die Klasse der Hintergrundaufgabe muss **IBackgroundTask** ableiten und verfügen über eine öffentliche **Run()** -Methode mit der Signatur unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="fb789-123">Your background task class must derive from **IBackgroundTask** and have a public **Run()** method with the signature shown below:</span></span>

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

## <a name="step-2-declare-your-background-task-in-the-package-manifest"></a><span data-ttu-id="fb789-124">Schritt 2: Deklarieren der Hintergrundaufgabe im Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="fb789-124">Step 2: Declare your background task in the package manifest</span></span>

<span data-ttu-id="fb789-125">Klicken Sie in Visual Studio-Projektmappen-Explorer mit der rechten Maustaste **"Package.appxmanifest"** , und klicken Sie auf **Code anzeigen** , um das Paketmanifest anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fb789-125">In the Visual Studio Solution Explorer, right-click **Package.appxmanifest** and click **View Code** to view the package manifest.</span></span> <span data-ttu-id="fb789-126">Fügen Sie die folgenden `<Extensions>` XML, Ihre Update-Aufgabe zu deklarieren:</span><span class="sxs-lookup"><span data-stu-id="fb789-126">Add the following `<Extensions>` XML to declare your update task:</span></span>

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

<span data-ttu-id="fb789-127">In der XML-Code, der oben genannten, stellen Sie sicher, dass die `EntryPoint` -Attribut auf den Namen namespace.class Ihre Update Task-Klasse festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="fb789-127">In the XML above, ensure that the `EntryPoint` attribute is set to the namespace.class name of your update task class.</span></span> <span data-ttu-id="fb789-128">Der Name ist die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="fb789-128">The name is case-sensitive.</span></span>

## <a name="step-3-debugtest-your-update-task"></a><span data-ttu-id="fb789-129">Schritt 3: Debug/Test Ihre Aufgabe Update</span><span class="sxs-lookup"><span data-stu-id="fb789-129">Step 3: Debug/test your Update task</span></span>

<span data-ttu-id="fb789-130">Stellen Sie sicher, dass Sie Ihre app auf Ihrem Computer bereitgestellt haben, damit etwas zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="fb789-130">Ensure that you have deployed your app to your machine so that there is something to update.</span></span>

<span data-ttu-id="fb789-131">Legen Sie einen Haltepunkt in der Methode Run() Ihrer Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="fb789-131">Set a breakpoint in the Run() method of your background task.</span></span>

![Set-Haltepunkt](images/run-func-breakpoint.png)

<span data-ttu-id="fb789-133">Als Nächstes im Projektmappen-Explorer mit der rechten Maustaste in der app Projekt (nicht das hintergrundaufgabenprojekt), und klicken Sie dann auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="fb789-133">Next, in the solution explorer, right-click your app's project (not the background task project) and then click **Properties**.</span></span> <span data-ttu-id="fb789-134">Klicken Sie im Eigenschaftenfenster Anwendung klicken Sie auf der linken Seite auf **Debuggen** , und wählen Sie **zunächst nicht starten, sondern Debuggen Sie eigenen Code beim Starten**:</span><span class="sxs-lookup"><span data-stu-id="fb789-134">In the application Properties window, click **Debug** on the left, then select **Do not launch, but debug my code when it starts**:</span></span>

![Legen Sie die Debugeinstellungen](images/do-not-launch-but-debug.png)

<span data-ttu-id="fb789-136">Um sicherzustellen, dass die UpdateTask ausgelöst wird, erhöhen Sie als Nächstes Versionsnummer des Pakets.</span><span class="sxs-lookup"><span data-stu-id="fb789-136">Next, to ensure that the UpdateTask is triggered, increase the package's version number.</span></span> <span data-ttu-id="fb789-137">Klicken Sie im Projektmappen-Explorer doppelklicken Sie auf der app **Datei "Package.appxmanifest** ", um den Designer zu öffnen, und aktualisieren Sie die **Build** -Nummer:</span><span class="sxs-lookup"><span data-stu-id="fb789-137">In the Solution Explorer, double-click your app's **Package.appxmanifest** file to open the package designer, and then update the **Build** number:</span></span>

![Aktualisieren Sie die version](images/bump-version.png)

<span data-ttu-id="fb789-139">Nun, in Visual Studio 2017, wenn Sie F5 drücken, wird Ihre app aktualisiert werden und das System wird die Komponente UpdateTask im Hintergrund aktivieren.</span><span class="sxs-lookup"><span data-stu-id="fb789-139">Now, in Visual Studio 2017 when you press F5, your app will be updated and the system will activate your UpdateTask component in the background.</span></span> <span data-ttu-id="fb789-140">Der Debugger wird automatisch mit um den Hintergrundprozess.</span><span class="sxs-lookup"><span data-stu-id="fb789-140">The debugger will automatically attach to the background process.</span></span> <span data-ttu-id="fb789-141">Wird der Haltepunkt erreicht erhalten und können Sie Ihre Update-Codelogik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="fb789-141">Your breakpoint will get hit and you can step through your update code logic.</span></span>

<span data-ttu-id="fb789-142">Wenn die Hintergrundaufgabe abgeschlossen ist, können Sie die Vordergrund-app aus dem Windows-Startmenü innerhalb der gleichen Debugsitzung starten.</span><span class="sxs-lookup"><span data-stu-id="fb789-142">When the background task completes, you can launch the foreground app from the Windows start menu within the same debug session.</span></span> <span data-ttu-id="fb789-143">Automatisch wieder der Debugger angehängt wird, wird dieses Mal im Vordergrund-Prozess, und Sie können Ihre app-Logik durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="fb789-143">The debugger will again automatically attach, this time to your foreground process, and you can step through your app's logic.</span></span>

> [!NOTE]
> <span data-ttu-id="fb789-144">Benutzer von Visual Studio 2015: die oben genannten Schritte gelten für Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fb789-144">Visual Studio 2015 users: The above steps apply to Visual Studio 2017.</span></span> <span data-ttu-id="fb789-145">Wenn Sie Visual Studio 2015 verwenden, können Sie die gleichen Techniken zur Trigger und Test UpdateTask, mit Ausnahme von Visual Studio keine Verbindung herstellen wird.</span><span class="sxs-lookup"><span data-stu-id="fb789-145">If you are using Visual Studio 2015, you can use the same techniques to trigger and test the UpdateTask, except Visual Studio will not attach to it.</span></span> <span data-ttu-id="fb789-146">Eine andere Möglichkeit ist, richten Sie eine [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) , die den Einstiegspunkt der UpdateTask festgelegt, und lösen Sie die Ausführung direkt von der Vordergrund-app in Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="fb789-146">An alternative procedure in VS 2015 is to setup an [ApplicationTrigger](https://docs.microsoft.com/windows/uwp/launch-resume/trigger-background-task-from-app) that sets the UpdateTask as its Entry Point, and trigger the execution directly from the foreground app.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb789-147">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="fb789-147">See also</span></span>

[<span data-ttu-id="fb789-148">Erstellen und Registrieren einer Out-of-Process-Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="fb789-148">Create and register an out-of-process background task</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)
