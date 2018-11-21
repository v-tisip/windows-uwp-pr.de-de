---
author: TylerMSFT
title: Deklarieren von Hintergrundaufgaben im Anwendungsmanifest
description: Sie können die Verwendung von Hintergrundaufgaben aktivieren, indem Sie diese im App-Manifest als Erweiterungen deklarieren.
ms.assetid: 6B4DD3F8-3C24-4692-9084-40999A37A200
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
ms.openlocfilehash: 343cca5b89dbe5fd7e1309b9487e8939218203d0
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7559666"
---
# <a name="declare-background-tasks-in-the-application-manifest"></a><span data-ttu-id="31aea-104">Deklarieren von Hintergrundaufgaben im Anwendungsmanifest</span><span class="sxs-lookup"><span data-stu-id="31aea-104">Declare background tasks in the application manifest</span></span>




**<span data-ttu-id="31aea-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="31aea-105">Important APIs</span></span>**

-   [**<span data-ttu-id="31aea-106">BackgroundTasks-Schema</span><span class="sxs-lookup"><span data-stu-id="31aea-106">BackgroundTasks Schema</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**<span data-ttu-id="31aea-107">Windows.ApplicationModel.Background</span><span class="sxs-lookup"><span data-stu-id="31aea-107">Windows.ApplicationModel.Background</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224847)

<span data-ttu-id="31aea-108">Sie können die Verwendung von Hintergrundaufgaben aktivieren, indem Sie diese im App-Manifest als Erweiterungen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="31aea-108">Enable the use of background tasks by declaring them as extensions in the app manifest.</span></span>

> [!Important]
>  <span data-ttu-id="31aea-109">Dieser Artikel befasst sich speziell mit Out-of-Process-Hintergrundaufgaben.</span><span class="sxs-lookup"><span data-stu-id="31aea-109">This article is specific to out-of-process background tasks.</span></span> <span data-ttu-id="31aea-110">In-Process-Hintergrundaufgaben werden nicht im Manifest deklariert.</span><span class="sxs-lookup"><span data-stu-id="31aea-110">In-process background tasks are not declared in the manifest.</span></span>

<span data-ttu-id="31aea-111">Out-of-Process-Hintergrundaufgaben müssen im Anwendungsmanifest deklariert sein, da Ihre App diese ansonsten nicht registrieren kann (eine Ausnahme wird ausgelöst).</span><span class="sxs-lookup"><span data-stu-id="31aea-111">Out-of-process background tasks must be declared in the app manifest or else your app will not be able to register them (an exception will be thrown).</span></span> <span data-ttu-id="31aea-112">Zudem müssen Out-of-Process-Hintergrundaufgaben im Anwendungsmanifest deklariert werden, um zertifiziert werden zu können.</span><span class="sxs-lookup"><span data-stu-id="31aea-112">Additionally, out-of-process background tasks must be declared in the application manifest to pass certification.</span></span>

<span data-ttu-id="31aea-113">In diesem Thema wird davon ausgegangen, dass Sie eine oder mehrere Hintergrundaufgabenklassen erstellt haben und dass Ihre App die Hintergrundaufgabe so registriert, dass sie als Reaktion auf mindestens einen Auslöser ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="31aea-113">This topic assumes you have a created one or more background task classes, and that your app registers each background task to run in response to at least one trigger.</span></span>

## <a name="add-extensions-manually"></a><span data-ttu-id="31aea-114">Manuelles Hinzufügen von Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="31aea-114">Add Extensions Manually</span></span>


<span data-ttu-id="31aea-115">Öffnen Sie das Anwendungsmanifest (Package.appxmanifest), und wechseln Sie zum „Application“-Element.</span><span class="sxs-lookup"><span data-stu-id="31aea-115">Open the application manifest (Package.appxmanifest) and go to the Application element.</span></span> <span data-ttu-id="31aea-116">Erstellen Sie ein "Extensions"-Element (sofern nicht bereits eines vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="31aea-116">Create an Extensions element (if one doesn't already exist).</span></span>

<span data-ttu-id="31aea-117">Der folgende Ausschnitt stammt aus dem [Hintergrundaufgabenbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=618666):</span><span class="sxs-lookup"><span data-stu-id="31aea-117">The following snippet is taken from the [background task sample](http://go.microsoft.com/fwlink/p/?LinkId=618666):</span></span>

```xml
<Application Id="App"
   ...
   <Extensions>
     <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.SampleBackgroundTask">
       <BackgroundTasks>
         <Task Type="systemEvent" />
         <Task Type="timer" />
       </BackgroundTasks>
     </Extension>
     <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.ServicingComplete">
       <BackgroundTasks>
         <Task Type="systemEvent"/>
       </BackgroundTasks>
     </Extension>
   </Extensions>
 </Application>
```

## <a name="add-a-background-task-extension"></a><span data-ttu-id="31aea-118">Hinzufügen einer Erweiterung für eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="31aea-118">Add a Background Task Extension</span></span>  

<span data-ttu-id="31aea-119">Deklarieren Sie Ihre erste Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="31aea-119">Declare your first background task.</span></span>

<span data-ttu-id="31aea-120">Kopieren Sie diesen Code in das "Extensions"-Element (Attribute werden in den folgenden Schritten hinzugefügt).</span><span class="sxs-lookup"><span data-stu-id="31aea-120">Copy this code into the Extensions element (you will add attributes in the following steps).</span></span>

```xml
<Extensions>
    <Extension Category="windows.backgroundTasks" EntryPoint="">
      <BackgroundTasks>
        <Task Type="" />
      </BackgroundTasks>
    </Extension>
</Extensions>
```

1.  <span data-ttu-id="31aea-121">Ändern Sie das EntryPoint-Attribut so, dass diese Zeichenfolge von Ihrem Code bei der Registrierung Ihrer Hintergrundaufgabe als Einstiegspunkt verwendet wird (**namespace.classname**).</span><span class="sxs-lookup"><span data-stu-id="31aea-121">Change the EntryPoint attribute to have the same string used by your code as the entry point when registering your background task (**namespace.classname**).</span></span>

    <span data-ttu-id="31aea-122">In diesem Beispiel ist „ExampleBackgroundTaskNameSpace.ExampleBackgroundTaskClassName“ der Einstiegspunkt:</span><span class="sxs-lookup"><span data-stu-id="31aea-122">In this example, the entry point is ExampleBackgroundTaskNameSpace.ExampleBackgroundTaskClassName:</span></span>

```xml
<Extensions>
    <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.ExampleBackgroundTaskClassName">
       <BackgroundTasks>
         <Task Type="" />
       </BackgroundTasks>
    </Extension>
</Extensions>
```

2.  <span data-ttu-id="31aea-123">Ändern Sie die Liste der Aufgabentypenattribute, um den für diese Hintergrundaufgabe verwendeten Typ der Aufgabenregistrierung anzugeben.</span><span class="sxs-lookup"><span data-stu-id="31aea-123">Change the list of Task Type attribute to indicate the type of task registration used with this background task.</span></span> <span data-ttu-id="31aea-124">Wenn die Hintergrundaufgabe mit mehreren Triggertypen registriert wird, fügen Sie für jeden Typ zusätzliche Task-Elemente und Type-Attribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="31aea-124">If the background task is registered with multiple trigger types, add additional Task elements and Type attributes for each one.</span></span>

    <span data-ttu-id="31aea-125">**Hinweis:** Vergewissern Sie sich zum Auflisten aller Triggertypen Sie, oder wenn die Hintergrundaufgabe wird nicht mit Triggertypen (die [**Register**](https://msdn.microsoft.com/library/windows/apps/br224772) -Methode wird fehl und löst eine Ausnahme) registrieren.</span><span class="sxs-lookup"><span data-stu-id="31aea-125">**Note**Make sure to list each of the trigger types you're using, or the background task will not register with the undeclared trigger types (the [**Register**](https://msdn.microsoft.com/library/windows/apps/br224772) method will fail and throw an exception).</span></span>

    <span data-ttu-id="31aea-126">Dieses Beispiel veranschaulicht die Verwendung von Systemereignistriggern und Pushbenachrichtigungen:</span><span class="sxs-lookup"><span data-stu-id="31aea-126">This snippet example indicates the use of system event triggers and push notifications:</span></span>

```xml
<Extension Category="windows.backgroundTasks" EntryPoint="Tasks.BackgroundTaskClass">
    <BackgroundTasks>
        <Task Type="systemEvent" />
        <Task Type="pushNotification" />
    </BackgroundTasks>
</Extension>
```

### <a name="add-multiple-background-task-extensions"></a><span data-ttu-id="31aea-127">Hinzufügen von weiteren Hintergrundaufgabenerweiterungen</span><span class="sxs-lookup"><span data-stu-id="31aea-127">Add multiple background task extensions</span></span>

<span data-ttu-id="31aea-128">Wiederholen Sie Schritt 2 für alle weiteren, von Ihrer App registrierten Hintergrundaufgabenklassen.</span><span class="sxs-lookup"><span data-stu-id="31aea-128">Repeat step 2 for each additional background task class registered by your app.</span></span>

<span data-ttu-id="31aea-129">Das folgende Beispiel zeigt das vollständige "Application"-Element aus dem [Hintergrundaufgabenbeispiel]( http://go.microsoft.com/fwlink/p/?linkid=227509):</span><span class="sxs-lookup"><span data-stu-id="31aea-129">The following example is the complete Application element from the [background task sample]( http://go.microsoft.com/fwlink/p/?linkid=227509).</span></span> <span data-ttu-id="31aea-130">Es zeigt die Verwendung von zwei Hintergrundaufgabenklassen mit insgesamt drei Triggertypen.</span><span class="sxs-lookup"><span data-stu-id="31aea-130">This shows the use of 2 background task classes with a total of 3 trigger types.</span></span> <span data-ttu-id="31aea-131">Kopieren Sie den Abschnitt „Extensions“ aus diesem Beispiel, und ändern Sie ihn nach Bedarf, um Hintergrundaufgaben im Anwendungsmanifest zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="31aea-131">Copy the Extensions section of this example, and modify it as needed, to declare background tasks in your application manifest.</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="BackgroundTask.App">
        <uap:VisualElements
          DisplayName="BackgroundTask"
          Square150x150Logo="Assets\StoreLogo-sdk.png"
          Square44x44Logo="Assets\SmallTile-sdk.png"
          Description="BackgroundTask"

          BackgroundColor="#00b2f0">
          <uap:LockScreen Notification="badgeAndTileText" BadgeLogo="Assets\smalltile-Windows-sdk.png" />
            <uap:SplashScreen Image="Assets\Splash-sdk.png" />
            <uap:DefaultTile DefaultSize="square150x150Logo" Wide310x150Logo="Assets\tile-sdk.png" >
                <uap:ShowNameOnTiles>
                    <uap:ShowOn Tile="square150x150Logo" />
                    <uap:ShowOn Tile="wide310x150Logo" />
                </uap:ShowNameOnTiles>
            </uap:DefaultTile>
        </uap:VisualElements>

      <Extensions>
        <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.SampleBackgroundTask">
          <BackgroundTasks>
            <Task Type="systemEvent" />
            <Task Type="timer" />
          </BackgroundTasks>
        </Extension>
        <Extension Category="windows.backgroundTasks" EntryPoint="Tasks.ServicingComplete">
          <BackgroundTasks>
            <Task Type="systemEvent"/>
          </BackgroundTasks>
        </Extension>
      </Extensions>
    </Application>
</Applications>
```

## <a name="declare-where-your-background-task-will-run"></a><span data-ttu-id="31aea-132">Deklarieren Sie die Position, an der Ihre Hintergrundaufgabe ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="31aea-132">Declare where your background task will run</span></span>

<span data-ttu-id="31aea-133">Sie können angeben, wo Ihre Hintergrundaufgaben ausführt werden sollen:</span><span class="sxs-lookup"><span data-stu-id="31aea-133">You can specify where your background tasks run:</span></span>

* <span data-ttu-id="31aea-134">Standardmäßig werden sie im Prozess „BackgroundTaskHost.exe“ ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="31aea-134">By default, they run in the BackgroundTaskHost.exe process.</span></span>
* <span data-ttu-id="31aea-135">Im gleichen Prozess wie Ihre Anwendung im Vordergrund.</span><span class="sxs-lookup"><span data-stu-id="31aea-135">In the same process as your foreground application.</span></span>
* <span data-ttu-id="31aea-136">Verwenden Sie `ResourceGroup`, um mehrere Hintergrundaufgaben im gleichen Hostprozess einzufügen, oder diese in verschiedene Prozesse aufzuspalten.</span><span class="sxs-lookup"><span data-stu-id="31aea-136">Use `ResourceGroup` to place multiple background tasks into the same hosting process, or to separate them into different processes.</span></span>
* <span data-ttu-id="31aea-137">Verwenden Sie `SupportsMultipleInstances`, um den Hintergrundprozess in einem neuen Prozess auszuführen, der, jedes Mal, wenn ein neuer Trigger ausgelöst wird, eigene Ressourcenbeschränkungen (Arbeitsspeicher, CPU) erhält.</span><span class="sxs-lookup"><span data-stu-id="31aea-137">Use `SupportsMultipleInstances` to run the background process in a new process that gets its own resource limits (memory, cpu) each time a new trigger is fired.</span></span>

### <a name="run-in-the-same-process-as-your-foreground-application"></a><span data-ttu-id="31aea-138">Die Ausführung erfolgt im gleichen Prozess wie Ihre Anwendung im Vordergrund.</span><span class="sxs-lookup"><span data-stu-id="31aea-138">Run in the same process as your foreground application</span></span>

<span data-ttu-id="31aea-139">In diesem XML-Beispiel wird eine Hintergrundaufgabe deklariert, die im gleichen Prozess wie die Anwendung im Vordergrund ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="31aea-139">Here is example XML that declares a background task that runs in the same process as the foreground application.</span></span>

```xml
<Extensions>
    <Extension Category="windows.backgroundTasks" EntryPoint="ExecModelTestBackgroundTasks.ApplicationTriggerTask">
        <BackgroundTasks>
            <Task Type="systemEvent" />
        </BackgroundTasks>
    </Extension>
</Extensions>
```

<span data-ttu-id="31aea-140">Wenn Sie den **Einsprungpunkt** festlegen, erhält Ihre Anwendung einen Rückruf an die angegebene Methode, sobald der Trigger ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="31aea-140">When you specify **EntryPoint**, your application receives a callback to the specified method when the trigger fires.</span></span> <span data-ttu-id="31aea-141">Wenn Sie den **Einsprungpunkt** nicht festlegen, erhält Ihre Anwendung den Rückruf über  [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx).</span><span class="sxs-lookup"><span data-stu-id="31aea-141">If you do not specify an **EntryPoint**, your application receives the callback via  [OnBackgroundActivated()](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.onbackgroundactivated.aspx).</span></span>  <span data-ttu-id="31aea-142">Weitere Informationen finden Sie unter [Erstellen und Registrieren einer In-Process-Hintergrundaufgabe](create-and-register-an-inproc-background-task.md).</span><span class="sxs-lookup"><span data-stu-id="31aea-142">See [Create and register an in-process background task](create-and-register-an-inproc-background-task.md) for details.</span></span>

### <a name="specify-where-your-background-task-runs-with-the-resourcegroup-attribute"></a><span data-ttu-id="31aea-143">Legen Sie fest, wo Ihre Hintergrundaufgabe mit dem Attribut „ResourceGroup“ ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="31aea-143">Specify where your background task runs with the ResourceGroup attribute.</span></span>

<span data-ttu-id="31aea-144">Hier finden Sie ein XML-Beispiel, mit dem eine Hintergrundaufgabe deklariert wird, die zwar in einem „BackgroundTaskHost.exe“-Prozess ausgeführt wird, der jedoch von anderen Hintergrundaufgabeninstanzen derselben App getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="31aea-144">Here is example XML that declares a background task that runs in a BackgroundTaskHost.exe process, but in a separate one than other instances of background tasks from the same app.</span></span> <span data-ttu-id="31aea-145">Beachten Sie das Attribut `ResourceGroup`, das festlegt, welche Hintergrundaufgaben gemeinsam ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="31aea-145">Note the `ResourceGroup` attribute, which identifies which background tasks will run together.</span></span>

```xml
<Extensions>
    <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.SessionConnectedTriggerTask" ResourceGroup="foo">
      <BackgroundTasks>
        <Task Type="systemEvent" />
      </BackgroundTasks>
    </Extension>
    <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.TimeZoneTriggerTask" ResourceGroup="foo">
      <BackgroundTasks>
        <Task Type="systemEvent" />
      </BackgroundTasks>
    </Extension>
    <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.TimerTriggerTask" ResourceGroup="bar">
      <BackgroundTasks>
        <Task Type="timer" />
      </BackgroundTasks>
    </Extension>
    <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.ApplicationTriggerTask" ResourceGroup="bar">
      <BackgroundTasks>
        <Task Type="general" />
      </BackgroundTasks>
    </Extension>
    <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.MaintenanceTriggerTask" ResourceGroup="foobar">
      <BackgroundTasks>
        <Task Type="general" />
      </BackgroundTasks>
    </Extension>
</Extensions>
```

### <a name="run-in-a-new-process-each-time-a-trigger-fires-with-the-supportsmultipleinstances-attribute"></a><span data-ttu-id="31aea-146">Ausführen in einem neuen Prozess, jedes Mal, wenn ein Trigger mit dem Attribut „SupportsMultipleInstances“ ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="31aea-146">Run in a new process each time a trigger fires with the SupportsMultipleInstances attribute</span></span>

<span data-ttu-id="31aea-147">In diesem Beispiel wird eine Hintergrundaufgabe deklariert, die in einem neuen Prozess ausgeführt wird, der, jedes Mal, wenn ein neuer Trigger ausgelöst wird, eigene Ressourcenbeschränkungen (Arbeitsspeicher und CPU) erhält.</span><span class="sxs-lookup"><span data-stu-id="31aea-147">This example declares a background task that runs in a new process that gets its own resource limits (memory and CPU) every time a new trigger is fired.</span></span> <span data-ttu-id="31aea-148">Beachten Sie die Verwendung von `SupportsMultipleInstances`, zur Aktivierung dieses Verhalten.</span><span class="sxs-lookup"><span data-stu-id="31aea-148">Note the use of `SupportsMultipleInstances` which enables this behavior.</span></span> <span data-ttu-id="31aea-149">Um dieses Attribut verwenden, Sie müssen als Ziel die SDK-Version "10.0.15063" (Windows 10 Creators Update) oder höher.</span><span class="sxs-lookup"><span data-stu-id="31aea-149">In order to use this attribute you must target SDK version '10.0.15063' (Windows 10 Creators Update) or higher.</span></span>

```xml
<Package
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    ...
    <Applications>
        <Application ...>
            ...
            <Extensions>
                <Extension Category="windows.backgroundTasks" EntryPoint="BackgroundTasks.TimerTriggerTask">
                    <BackgroundTasks uap4:SupportsMultipleInstances=“True”>
                        <Task Type="timer" />
                    </BackgroundTasks>
                </Extension>
            </Extensions>
        </Application>
    </Applications>
```

> [!NOTE]
> <span data-ttu-id="31aea-150">`ResourceGroup` oder `ServerName` können in Verbindung mit `SupportsMultipleInstances` nicht festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="31aea-150">You cannot specify `ResourceGroup` or `ServerName` in conjunction with `SupportsMultipleInstances`.</span></span>

## <a name="related-topics"></a><span data-ttu-id="31aea-151">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="31aea-151">Related topics</span></span>

* [<span data-ttu-id="31aea-152">Debuggen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="31aea-152">Debug a background task</span></span>](debug-a-background-task.md)
* [<span data-ttu-id="31aea-153">Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="31aea-153">Register a background task</span></span>](register-a-background-task.md)
* [<span data-ttu-id="31aea-154">Richtlinien für Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="31aea-154">Guidelines for background tasks</span></span>](guidelines-for-background-tasks.md)
