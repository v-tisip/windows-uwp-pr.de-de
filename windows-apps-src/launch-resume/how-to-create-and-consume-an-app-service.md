---
author: TylerMSFT
title: Erstellen und Verwenden eines App-Diensts
description: Hier erfahren Sie, wie Sie eine App für die Universelle Windows-Plattform (UWP) erstellen, die Dienste für andere UWP-Apps bereitstellen kann, und wie Sie diese Dienste nutzen.
ms.assetid: 6E48B8B6-D3BF-4AE2-85FB-D463C448C9D3
keywords: App-zu-App-Kommunikation, prozessübergreifende Kommunikation, IPC, Hintergrundnachrichten, Hintergrundkommunikation, App zu App
ms.author: twhitney
ms.date: 09/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: e119a161d054a88665494d76b03a3c5fd8f331d1
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1656155"
---
# <a name="create-and-consume-an-app-service"></a><span data-ttu-id="bf90a-104">Erstellen und Verwenden eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="bf90a-104">Create and consume an app service</span></span>


<span data-ttu-id="bf90a-105">Hier erfahren Sie, wie Sie eine App für die Universelle Windows-Plattform (UWP) erstellen, die einen Dienst für andere UWP-Apps bereitstellen kann, und wie Sie diesen Dienst nutzen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-105">Learn how to write a Universal Windows Platform (UWP) app that can provide a service to other UWP apps, and how to consume that service.</span></span>

<span data-ttu-id="bf90a-106">Ab Windows10, Version 1607, können Sie App-Dienste erstellen, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-106">Starting in Windows 10, version 1607, you can create app services that run in the same process as the host app.</span></span> <span data-ttu-id="bf90a-107">In diesem Artikel geht es um das Erstellen von App-Diensten, die in einem separaten Hintergrundprozess ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-107">This article focuses on creating app services that run in a separate background process.</span></span> <span data-ttu-id="bf90a-108">Unter [Konvertieren eines App-Diensts für die Ausführung im gleichen Prozess wie seine Host-App](convert-app-service-in-process.md) finden Sie weitere Informationen zum Ausführen eines App-Dienstes, der im gleichen Prozess wie der Anbieter ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-108">See [Convert an app service to run in the same process as its host app](convert-app-service-in-process.md) for more details about running an app service in the same process as the provider.</span></span>

<span data-ttu-id="bf90a-109">Weitere Beispiele für den App-Dienst finden Sie unter [Apps für die universelle Windows-Plattform (UWP): Beispiele](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).</span><span class="sxs-lookup"><span data-stu-id="bf90a-109">For more app service samples, see [Universal Windows Platform (UWP) app samples](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).</span></span>

## <a name="create-a-new-app-service-provider-project"></a><span data-ttu-id="bf90a-110">Erstellen eines neuen App-Dienstanbieterprojekts</span><span class="sxs-lookup"><span data-stu-id="bf90a-110">Create a new app service provider project</span></span>

<span data-ttu-id="bf90a-111">In dieser Anleitung erstellen wir der Einfachheit halber alles in einer Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="bf90a-111">In this how-to, we'll create everything in one solution for simplicity.</span></span>

-   <span data-ttu-id="bf90a-112">Erstellen Sie in Microsoft Visual Studio2015 ein neues UWP-App-Projekt mit dem Namen **AppServiceProvider**.</span><span class="sxs-lookup"><span data-stu-id="bf90a-112">In Microsoft Visual Studio, create a new UWP app project and name it **AppServiceProvider**.</span></span> <span data-ttu-id="bf90a-113">(Wählen Sie im Dialogfeld **Neues Projekt** **Vorlagen &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Blank App (Windows Universal)** aus.)</span><span class="sxs-lookup"><span data-stu-id="bf90a-113">(In the **New Project** dialog box, select **Templates &gt; Other Languages &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Blank app (Windows Universal)**).</span></span> <span data-ttu-id="bf90a-114">Dies ist die App, die den App-Dienst für andere UWP-Apps verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="bf90a-114">This will be the app that makes the app service available to other UWP apps.</span></span>
-   <span data-ttu-id="bf90a-115">Wenn Sie gefragt werden, wählen Sie eine **Zielversion** für das Projekt auszuwählen, wählen Sie mindestens **10.0.14393** aus.</span><span class="sxs-lookup"><span data-stu-id="bf90a-115">When asked to select a **Target Version** for the project, select at least **10.0.14393**.</span></span> <span data-ttu-id="bf90a-116">Wenn Sie das neue `SupportsMultipleInstances`-Attribut verwenden möchten, müssen Sie Visual Studio2017 verwenden und als Ziel **10.0.15063** (**Windows 10 Creators Update**) oder höher auswählen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-116">If you want to use the new `SupportsMultipleInstances` attribute, you must be using Visual Studio 2017 and target **10.0.15063** (**Windows 10 Creators Update**) or higher.</span></span>

<span id="appxmanifest"/>

## <a name="add-an-app-service-extension-to-packageappxmanifest"></a><span data-ttu-id="bf90a-117">Hinzufügen einer App-Diensterweiterung zu „package.appxmanifest”</span><span class="sxs-lookup"><span data-stu-id="bf90a-117">Add an app service extension to package.appxmanifest</span></span>

<span data-ttu-id="bf90a-118">Fügen Sie innerhalb der Datei „Package.appxmanifest” des Projekts „AppServiceProvider” die folgende AppService-Erweiterung zum `&lt;Application&gt;`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf90a-118">In the AppServiceProvider project's Package.appxmanifest file, add the following AppService extension inside the `&lt;Application&gt;` element.</span></span> <span data-ttu-id="bf90a-119">Durch dieses Beispiel wird der `com.Microsoft.Inventory`-Dienst angekündigt, und die App wird als App-Dienstanbieter identifiziert.</span><span class="sxs-lookup"><span data-stu-id="bf90a-119">This example advertises the `com.Microsoft.Inventory` service and is what identifies this app as an app service provider.</span></span> <span data-ttu-id="bf90a-120">Der eigentliche Dienst wird als Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="bf90a-120">The actual service will be implemented as a background task.</span></span> <span data-ttu-id="bf90a-121">Das Projekt, das den App-Dienst bereitstellt, macht den Dienst für andere Apps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bf90a-121">The app service project exposes the service to other apps.</span></span> <span data-ttu-id="bf90a-122">Wir empfehlen, einen umgekehrten Domänennamen für den Dienstnamen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-122">We recommend using a reverse domain name style for the service name.</span></span>

<span data-ttu-id="bf90a-123">Beachten Sie, dass der Namespacepräfix `xmlns:uap4` und das Attribut `uap4:SupportsMultipleInstances` nur dann gültig sind, wenn Sie die Windows SDK-Version 10.0.15063 oder höher als Ziel setzen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-123">Note that the `xmlns:uap4` namespace prefix and the `uap4:SupportsMultipleInstances` attribute are only valid if you are targeting Windows SDK version 10.0.15063 or higher.</span></span> <span data-ttu-id="bf90a-124">Sie können diese sicher entfernen, wenn Sie ältere SDK-Versionen als Zielgruppe setzen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-124">You can safely remove them if you are targeting older SDK versions.</span></span>

``` xml
<Package
    ...
    xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    ...
    <Applications>
        <Application Id="AppServicesProvider.App"
          Executable="$targetnametoken$.exe"
          EntryPoint="AppServicesProvider.App">
          ...
          <Extensions>
            <uap:Extension Category="windows.appService" EntryPoint="MyAppService.Inventory">
              <uap3:AppService Name="com.microsoft.inventory" uap4:SupportsMultipleInstances="true"/>
            </uap:Extension>
          </Extensions>
          ...
        </Application>
    </Applications>
```

<span data-ttu-id="bf90a-125">Das **Category**-Attribut identifiziert die App als App-Dienstanbieter.</span><span class="sxs-lookup"><span data-stu-id="bf90a-125">The **Category** attribute identifies this application as an app service provider.</span></span>

<span data-ttu-id="bf90a-126">Das **EntryPoint**-Attribut identifiziert die Namespace-qualifizierte Klasse, die den Dienst implementiert. Den Dienst implementieren wir als Nächstes.</span><span class="sxs-lookup"><span data-stu-id="bf90a-126">The **EntryPoint** attribute identifies the namespace qualified class that implements the service, which we'll implement next.</span></span>

<span data-ttu-id="bf90a-127">Das **SupportsMultipleInstances** -Attribut gibt an, dass bei jedem Aufruf des App-Dienstes ein neuer Prozess ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bf90a-127">The **SupportsMultipleInstances** attribute indicates that each time the app service is called that it should run in a new process.</span></span> <span data-ttu-id="bf90a-128">Dies ist nicht erforderlich, aber verfügbar, wenn Sie diese Funktionalität erfordern und als Ziel `10.0.15063` SDK (**Windows10 Creators Update**) oder höher haben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-128">This is not required but is available to you if you need that functionality and are targeting the `10.0.15063` SDK (**Windows 10 Creators Update**) or higher.</span></span> <span data-ttu-id="bf90a-129">Der Präfix `uap4` Namespace sollte dabei angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-129">It also should be prefaced by the `uap4` namespace.</span></span>

## <a name="create-the-app-service"></a><span data-ttu-id="bf90a-130">Erstellen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="bf90a-130">Create the app service</span></span>

1.  <span data-ttu-id="bf90a-131">Ein App-Dienst kann als Hintergrundaufgabe implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-131">An app service can be implemented as a background task.</span></span> <span data-ttu-id="bf90a-132">Dadurch kann eine Vordergrund-App einen App-Dienst in einer anderen App aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-132">This enables a foreground application to invoke an app service in another application.</span></span> <span data-ttu-id="bf90a-133">Fügen Sie der Projektmappe ein neues Projekt vom Typ „Komponente für Windows-Runtime” (**Datei &gt; Hinzufügen &gt; Neues Projekt**) mit dem Namen „MyAppService” hinzu, um einen App-Dienst als Hintergrundaufgabe auszuführen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-133">To create an app service as a background task, add a new Windows Runtime Component project to the solution (**File &gt; Add &gt; New Project**) named MyAppService.</span></span> <span data-ttu-id="bf90a-134">(Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** **Installiert &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Komponente für Windows-Runtime (Windows Universal)** aus.)</span><span class="sxs-lookup"><span data-stu-id="bf90a-134">(In the **Add New Project** dialog box, choose **Installed &gt; Other Languages &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Windows Runtime Component (Windows Universal)**</span></span>
2.  <span data-ttu-id="bf90a-135">Fügen Sie im Projekt **"AppServiceProvider"** einen Projekt-zu-Projekt-Verweis auf das neue Projekt **"myappservice"** hinzu. (Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **"AppServiceProvider"** > **Hinzufügen** > **Verweis** > **Projekte** > **Lösung**. Anschließend wählen Sie **"myappservice"** > **OK** aus).</span><span class="sxs-lookup"><span data-stu-id="bf90a-135">In the **AppServiceProvider** project, add a project-to-project reference to the new **MyAppService** project (In the Solution Explorer, right-click on the **AppServiceProvider** project > **Add** > **Reference** > **Projects** > **Solution**, select **MyAppService** > **OK**).</span></span> <span data-ttu-id="bf90a-136">Dieser Schritt ist unerlässlich, da der App-Dienst ohne das Hinzufügen der Referenz keine Laufzeit damit verbindet.</span><span class="sxs-lookup"><span data-stu-id="bf90a-136">This step is critical because if you do not add the reference, the app service won't connect at runtime.</span></span>
3.  <span data-ttu-id="bf90a-137">Fügen Sie im Projekt „MyAppService” am Anfang von „Class1.cs” die folgenden **using**-Anweisungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="bf90a-137">In the MyappService project, add the following **using** statements to the top of Class1.cs:</span></span>
    ```cs
    using Windows.ApplicationModel.AppService;
    using Windows.ApplicationModel.Background;
    using Windows.Foundation.Collections;
    ```

4.  <span data-ttu-id="bf90a-138">Ersetzen Sie den Stubcode für **Class1** durch eine neue Hintergrundaufgabenklasse mit dem Namen **Inventory**:</span><span class="sxs-lookup"><span data-stu-id="bf90a-138">Replace the stub code for **Class1** with a new background task class named **Inventory**:</span></span>

    ```cs
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            this.backgroundTaskDeferral = taskInstance.GetDeferral(); // Get a deferral so that the service isn't terminated.
            taskInstance.Canceled += OnTaskCanceled; // Associate a cancellation handler with the background task.

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // This function is called when the app service receives a request
        }

        private void OnTaskCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            if (this.backgroundTaskDeferral != null)
            {
                // Complete the service deferral.
                this.backgroundTaskDeferral.Complete();
            }
        }
    }
    ```

    <span data-ttu-id="bf90a-139">In dieser Klasse wird der App-Dienst ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-139">This class is where the app service will do its work.</span></span>

    <span data-ttu-id="bf90a-140">**Run()** wird aufgerufen, wenn die Hintergrundaufgabe erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="bf90a-140">**Run()** is called when the background task is created.</span></span> <span data-ttu-id="bf90a-141">Da Hintergrundaufgaben nach Abschluss von **Run** beendet werden, implementiert der Code eine Verzögerung, damit die Hintergrundaufgabe zum Verarbeiten von Anforderungen aktiv bleibt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-141">Because background tasks are terminated after **Run** completes, the code takes out a deferral so that the background task will stay up to serve requests.</span></span> <span data-ttu-id="bf90a-142">Ein App-Dienst, der als Hintergrundaufgabe implementiert ist, bleibt für ungefähr 30Sekunden aktiv, nachdem er einen Anruf erhält, es sei denn, er wird innerhalb dieses Zeitraums erneut aufgerufen oder es wird eine Verzögerung entnommen. Wenn der App-Dienst im gleichen Prozess wie der Aufrufer implementiert ist, ist die Lebensdauer des App-Diensts an die Lebensdauer des Aufrufers gebunden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-142">An app service that is implemented as a background task will stay alive for about 30 seconds after it receives a call unless it is called again within that time window or a deferral is taken out. If the app service is implemented in the same process as the caller, the lifetime of the app service is tied to the lifetime of the caller.</span></span>

    <span data-ttu-id="bf90a-143">Die Lebensdauer des App-Diensts hängt vom Aufrufer ab:</span><span class="sxs-lookup"><span data-stu-id="bf90a-143">The lifetime of the app service depends on the caller:</span></span>

    1. <span data-ttu-id="bf90a-144">Wenn der Aufrufer im Vordergrund ausgeführt wird, entspricht die Lebensdauer der App-Dienst der Lebensdauer des Aufrufers.</span><span class="sxs-lookup"><span data-stu-id="bf90a-144">If the caller is in foreground, the app service lifetime is the same as the caller.</span></span>
    2. <span data-ttu-id="bf90a-145">Wenn der Aufrufer im Hintergrund ausgeführt wird, wird der App-Dienst nach 30Sekunden ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-145">If the caller is in background, the app service gets 30 seconds to run.</span></span> <span data-ttu-id="bf90a-146">Das Entfernen einer Verzögerung stellt ein Mal zusätzlich 5Sekunden bereit.</span><span class="sxs-lookup"><span data-stu-id="bf90a-146">Taking out a deferral provides an additional one time 5 seconds.</span></span>

    <span data-ttu-id="bf90a-147">**OnTaskCanceled()** wird aufgerufen, wenn die Aufgabe abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="bf90a-147">**OnTaskCanceled()** is called when the task is canceled.</span></span> <span data-ttu-id="bf90a-148">Die Aufgabe wird abgebrochen, wenn die Client-App die [**AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704) löscht, die Client-App angehalten wird, das Betriebssystem heruntergefahren oder in den Ruhezustand geschaltet wird oder im Betriebssystem nicht genügend Ressourcen zum Ausführen der Aufgabe verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bf90a-148">The task is cancelled when the client app disposes the [**AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704), the client app is suspended, the OS is shut down or sleeps, or the OS runs out of resources to run the task.</span></span>

## <a name="write-the-code-for-the-app-service"></a><span data-ttu-id="bf90a-149">Schreiben des Codes für den App-Dienst</span><span class="sxs-lookup"><span data-stu-id="bf90a-149">Write the code for the app service</span></span>

<span data-ttu-id="bf90a-150">Der Code für den App-Service wird unter **OnRequestReceived()** ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-150">**OnRequestReceived()** is where the code for the app service goes.</span></span> <span data-ttu-id="bf90a-151">Ersetzen Sie den Platzhalter **OnRequestedReceived()** in der Datei „Class1.cs” von „MyAppService” mit dem Code aus dem folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="bf90a-151">Replace the stub **OnRequestReceived()** in MyAppService's Class1.cs with the code from this example.</span></span> <span data-ttu-id="bf90a-152">Dieser Code ruft einen Index für ein Bestandselement ab und übergibt ihn zusammen mit einer Befehlszeichenfolge an den Dienst, um den Namen und Preis des angegebenen Bestandselements abzurufen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-152">This code gets an index for an inventory item and passes it, along with a command string, to the service to retrieve the name and the price of the specified inventory item.</span></span> <span data-ttu-id="bf90a-153">Fügen Sie Ihren eigenen Projekten einen Code zur Fehlerbehandlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf90a-153">For your own projects, add error handling code.</span></span>

```cs
private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
{
    // Get a deferral because we use an awaitable API below to respond to the message
    // and we don't want this call to get cancelled while we are waiting.
    var messageDeferral = args.GetDeferral();

    ValueSet message = args.Request.Message;
    ValueSet returnData = new ValueSet();

    string command = message["Command"] as string;
    int? inventoryIndex = message["ID"] as int?;

    if ( inventoryIndex.HasValue &&
         inventoryIndex.Value >= 0 &&
         inventoryIndex.Value < inventoryItems.GetLength(0))
    {
        switch (command)
        {
            case "Price":
            {
                returnData.Add("Result", inventoryPrices[inventoryIndex.Value]);
                returnData.Add("Status", "OK");
                break;
            }

            case "Item":
            {
                returnData.Add("Result", inventoryItems[inventoryIndex.Value]);
                returnData.Add("Status", "OK");
                break;
            }

            default:
            {
                returnData.Add("Status", "Fail: unknown command");
                break;
            }
        }
    }
    else
    {
        returnData.Add("Status", "Fail: Index out of range");
    }

    try
    {
        await args.Request.SendResponseAsync(returnData); // Return the data to the caller.
    }
    catch (Exception e)
    {
        // your exception handling code here
    }
    finally
    {
        // Complete the deferral so that the platform knows that we're done responding to the app service call.
        // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
        messageDeferral.Complete();
    }
}
```

<span data-ttu-id="bf90a-154">**OnRequestReceived()** ist **async**, da wir in diesem Beispiel einen await-fähigen Methodenaufruf von [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-154">Note that **OnRequestReceived()** is **async** because we make an awaitable method call to [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) in this example.</span></span>

<span data-ttu-id="bf90a-155">Es wird eine Verzögerung implementiert, damit der Dienst **async**-Methoden im OnRequestReceived-Handler verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="bf90a-155">A deferral is taken so that the service can use **async** methods in the OnRequestReceived handler.</span></span> <span data-ttu-id="bf90a-156">Dadurch wird sichergestellt, dass der Aufruf von **OnRequestReceived** erst abgeschlossen wird, wenn die Nachricht verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="bf90a-156">It ensures that the call to **OnRequestReceived** does not complete until it is done processing the message.</span></span>  <span data-ttu-id="bf90a-157">[**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) sendet das Ergebnis an den Aufrufer.</span><span class="sxs-lookup"><span data-stu-id="bf90a-157">[**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) sends the result to the caller.</span></span> <span data-ttu-id="bf90a-158">**SendResponseAsync** signalisiert nicht den Abschluss des Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="bf90a-158">**SendResponseAsync** does not signal the completion of the call.</span></span> <span data-ttu-id="bf90a-159">[**SendMessageAsync**](https://msdn.microsoft.com/library/windows/apps/dn921712) wird durch den Abschluss der Verzögerung signalisiert, dass **OnRequestReceived** abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="bf90a-159">It is the completion of the deferral that signals to [**SendMessageAsync**](https://msdn.microsoft.com/library/windows/apps/dn921712) that **OnRequestReceived** has completed.</span></span> <span data-ttu-id="bf90a-160">**SendMessageAsync()** wird in einem Versuch/Final-Block aufgerufen, da die Verzögerung abgeschlossen werden muss, auch wenn **SendMessageAsync()** eine Ausnahme auslöst.</span><span class="sxs-lookup"><span data-stu-id="bf90a-160">The call to **SendResponseAsync()** is wrapped in a try/finally block because you must complete the deferral even if **SendResponseAsync()** throws an exception.</span></span>

<span data-ttu-id="bf90a-161">App-Dienste verwenden zum Austauschen von Informationen ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131).</span><span class="sxs-lookup"><span data-stu-id="bf90a-161">App services use a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) to exchange information.</span></span> <span data-ttu-id="bf90a-162">Die Größe der Daten, die übergeben werden können, ist nur durch die Systemressourcen begrenzt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-162">The size of the data you may pass is only limited by system resources.</span></span> <span data-ttu-id="bf90a-163">Es gibt keine vordefinierten Schlüssel zur Verwendung in Ihrem **ValueSet**.</span><span class="sxs-lookup"><span data-stu-id="bf90a-163">There are no predefined keys for you to use in your **ValueSet**.</span></span> <span data-ttu-id="bf90a-164">Sie müssen bestimmen, welche Schlüsselwerte Sie zum Definieren des Protokolls für Ihren App-Dienst verwenden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-164">You must determine which key values you will use to define the protocol for your app service.</span></span> <span data-ttu-id="bf90a-165">Dieses Protokoll muss beim Schreiben des Aufrufers berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="bf90a-165">The caller must be written with that protocol in mind.</span></span> <span data-ttu-id="bf90a-166">In diesem Beispiel haben wir einen Schlüssel namens `Command` ausgewählt, dessen Wert angibt, ob der App-Dienst den Namen des Bestandselements oder seinen Preis bereitstellen soll.</span><span class="sxs-lookup"><span data-stu-id="bf90a-166">In this example, we have chosen a key named `Command` that has a value that indicates whether we want the app service to provide the name of the inventory item or its price.</span></span> <span data-ttu-id="bf90a-167">Der Index des Bestandsnamens wird unter dem Schlüssel `ID` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bf90a-167">The index of the inventory name is stored under the `ID` key.</span></span> <span data-ttu-id="bf90a-168">Der Rückgabewert wird unter dem Schlüssel `Result` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bf90a-168">The return value is stored under the `Result` key.</span></span>

<span data-ttu-id="bf90a-169">An den Aufrufer wird eine [**AppServiceClosedStatus**](https://msdn.microsoft.com/library/windows/apps/dn921703)-Enumeration zurückgegeben, um anzugeben, ob der Aufruf des App-Diensts erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="bf90a-169">An [**AppServiceClosedStatus**](https://msdn.microsoft.com/library/windows/apps/dn921703) enum is returned to the caller to indicate whether the call to the app service succeeded or failed.</span></span> <span data-ttu-id="bf90a-170">Beim Aufruf des App-Diensts könnte z.B. ein Fehler auftreten, wenn das Betriebssystem den Dienstendpunkt abbricht, da keine Ressourcen mehr verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bf90a-170">An example of how the call to the app service could fail is if the OS aborts the service endpoint because its resources have been exceeded.</span></span> <span data-ttu-id="bf90a-171">Sie können über [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) zusätzliche Fehlerinformationen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-171">You can return additional error information via the [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131).</span></span> <span data-ttu-id="bf90a-172">In diesem Beispiel verwenden wir einen Schlüssel mit dem Namen `Status`, um detailliertere Fehlerinformationen an den Aufrufer zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-172">In this example, we use a key named `Status` to return more detailed error information to the caller.</span></span>

<span data-ttu-id="bf90a-173">Der Aufruf von [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) gibt [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) an den Aufrufer zurück.</span><span class="sxs-lookup"><span data-stu-id="bf90a-173">The call to [**SendResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn921722) returns the [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) to the caller.</span></span>

## <a name="deploy-the-service-app-and-get-the-package-family-name"></a><span data-ttu-id="bf90a-174">Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens</span><span class="sxs-lookup"><span data-stu-id="bf90a-174">Deploy the service app and get the package family name</span></span>

<span data-ttu-id="bf90a-175">Die Dienstanbieter-App muss bereitgestellt werden, bevor Sie sie von einem Client aus aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="bf90a-175">The app service provider app must be deployed before you can call it from a client.</span></span> <span data-ttu-id="bf90a-176">Außerdem benötigen Sie den Paketfamiliennamen der Dienstanbieter-App, um sie aufrufen zu können.</span><span class="sxs-lookup"><span data-stu-id="bf90a-176">You will also need the package family name of the app service app in order to call it.</span></span>

<span data-ttu-id="bf90a-177">Eine Möglichkeit zum Abrufen des Paketfamiliennamens der Dienstanbieter-App besteht darin, [**Windows.ApplicationModel.Package.Current.Id.FamilyName**](https://msdn.microsoft.com/library/windows/apps/br224670) im Projekt **AppServiceProvider** aufzurufen (z.B. in `public App()` in „App.xaml.cs”) und das Ergebnis zu notieren.</span><span class="sxs-lookup"><span data-stu-id="bf90a-177">One way to get the package family name of the app service application is to call [**Windows.ApplicationModel.Package.Current.Id.FamilyName**](https://msdn.microsoft.com/library/windows/apps/br224670) from within the **AppServiceProvider** project (for example, from `public App()` in App.xaml.cs) and note the result.</span></span> <span data-ttu-id="bf90a-178">Um das Projekt „AppServiceProvider” in Microsoft Visual Studio auszuführen, legen Sie es im Projektmappen-Explorer als Startprojekt fest, und führen Sie das Projekt aus.</span><span class="sxs-lookup"><span data-stu-id="bf90a-178">To run AppServiceProvider in Microsoft Visual Studio, set it as the startup project in the Solution Explorer window and run the project.</span></span>

<span data-ttu-id="bf90a-179">Eine weitere Möglichkeit zum Abrufen des Paketfamiliennamens ist das Bereitstellen der Projektmappe (**Erstellen &gt; Projektmappe bereitstellen**) und Notieren des vollständigen Paketnamens im Ausgabefenster (**Ansicht &gt; Ausgabe**).</span><span class="sxs-lookup"><span data-stu-id="bf90a-179">Another way to get the package family name is to deploy the solution (**Build &gt; Deploy solution**) and note the full package name in the output window (**View &gt; Output**).</span></span> <span data-ttu-id="bf90a-180">Sie müssen die Plattforminformationen aus der Zeichenfolge im Ausgabefenster entfernen, um den Paketnamen abzuleiten.</span><span class="sxs-lookup"><span data-stu-id="bf90a-180">You must remove the platform information from the string in the output window to derive the package name.</span></span> <span data-ttu-id="bf90a-181">Wenn beispielsweise im Ausgabefenster der vollständige Paketname `Microsoft.SDKSamples.AppServicesProvider.CPP_1.0.0.0_x86__8wekyb3d8bbwe` ist, extrahieren Sie `1.0.0.0\_x86\_\_" leaving "Microsoft.SDKSamples.AppServicesProvider.CPP_8wekyb3d8bbwe` als Paketfamilienname.</span><span class="sxs-lookup"><span data-stu-id="bf90a-181">For example, if the full package name reported in the output window was `Microsoft.SDKSamples.AppServicesProvider.CPP_1.0.0.0_x86__8wekyb3d8bbwe`, you would extract `1.0.0.0\_x86\_\_" leaving "Microsoft.SDKSamples.AppServicesProvider.CPP_8wekyb3d8bbwe` as the package family name.</span></span>

## <a name="write-a-client-to-call-the-app-service"></a><span data-ttu-id="bf90a-182">Schreiben eines Clients zum Aufrufen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="bf90a-182">Write a client to call the app service</span></span>

1.  <span data-ttu-id="bf90a-183">Fügen Sie der Projektmappe ein neues leeres Projekt für eine Universelle Windows-App mit dem Namen **Datei &gt; Hinzufügen &gt; Neues Projekt** hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf90a-183">Add a new blank Windows Universal app project to the solution with **File &gt; Add &gt; New Project**.</span></span> <span data-ttu-id="bf90a-184">Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf **Installiert &gt; Andere Sprachen &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Leere App (Windows Universal)** und nennen Sie es **ClientApp**.</span><span class="sxs-lookup"><span data-stu-id="bf90a-184">In the **Add New Project** dialog box, choose **Installed &gt; Other languages &gt; Visual C# &gt; Windows &gt; Windows Universal &gt; Blank App (Windows Universal)** and name it **ClientApp**.</span></span>
2.  <span data-ttu-id="bf90a-185">Fügen Sie im Projekt „ClientApp” am Anfang von „MainPage.xaml.cs” die folgende **using**-Anweisung hinzu:</span><span class="sxs-lookup"><span data-stu-id="bf90a-185">In the ClientApp project, add the following **using** statement to the top of MainPage.xaml.cs:</span></span>
    ```cs
    >using Windows.ApplicationModel.AppService;
    ```
3.  <span data-ttu-id="bf90a-186">Fügen Sie „MainPage.xaml” ein Textfeld und eine Schaltfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf90a-186">Add a text box and a button to MainPage.xaml.</span></span>
4.  <span data-ttu-id="bf90a-187">Fügen Sie einen Klickhandler für die Schaltfläche hinzu, und fügen Sie der Signatur des Schaltflächenhandlers das Schlüsselwort **async** hinzu.</span><span class="sxs-lookup"><span data-stu-id="bf90a-187">Add a button click handler for the button and add the keyword **async** to the button handler's signature.</span></span>
5.  <span data-ttu-id="bf90a-188">Ersetzen Sie den Stub des Klickhandlers für die Schaltfläche durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="bf90a-188">Replace the stub of your button click handler with the following code.</span></span> <span data-ttu-id="bf90a-189">Vergessen Sie nicht die `inventoryService`-Felddeklaration.</span><span class="sxs-lookup"><span data-stu-id="bf90a-189">Be sure to include the `inventoryService` field declaration.</span></span>

   ```cs
   private AppServiceConnection inventoryService;
   private async void button_Click(object sender, RoutedEventArgs e)
   {
       // Add the connection.
       if (this.inventoryService == null)
       {
           this.inventoryService = new AppServiceConnection();

           // Here, we use the app service name defined in the app service provider's Package.appxmanifest file in the <Extension> section.
           this.inventoryService.AppServiceName = "com.microsoft.inventory";

           // Use Windows.ApplicationModel.Package.Current.Id.FamilyName within the app service provider to get this value.
           this.inventoryService.PackageFamilyName = "replace with the package family name";

           var status = await this.inventoryService.OpenAsync();
           if (status != AppServiceConnectionStatus.Success)
           {
               textBox.Text= "Failed to connect";
               return;
           }
       }

       // Call the service.
       int idx = int.Parse(textBox.Text);
       var message = new ValueSet();
       message.Add("Command", "Item");
       message.Add("ID", idx);
       AppServiceResponse response = await this.inventoryService.SendMessageAsync(message);
       string result = "";

       if (response.Status == AppServiceResponseStatus.Success)
       {
           // Get the data  that the service sent  to us.
           if (response.Message["Status"] as string == "OK")
           {
               result = response.Message["Result"] as string;
           }
       }

       message.Clear();
       message.Add("Command", "Price");
       message.Add("ID", idx);
       response = await this.inventoryService.SendMessageAsync(message);

       if (response.Status == AppServiceResponseStatus.Success)
       {
           // Get the data that the service sent to us.
           if (response.Message["Status"] as string == "OK")
           {
               result += " : Price = " + response.Message["Result"] as string;
           }
       }

       textBox.Text = result;
   }
   ```
<span data-ttu-id="bf90a-190">Ersetzen Sie den Paketfamiliennamen in der Zeile `this.inventoryService.PackageFamilyName = "replace with the package family name";` durch den Paketfamiliennamen des **AppServiceProvider**-Projekts, das Sie in [Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens](#deploy-the-service-app-and-get-the-package-family-name) erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-190">Replace the package family name in the line `this.inventoryService.PackageFamilyName = "replace with the package family name";` with the package family name of the **AppServiceProvider** project that you obtained above in [Deploy the service app and get the package family name](#deploy-the-service-app-and-get-the-package-family-name).</span></span>

<span data-ttu-id="bf90a-191">Der Code richtet zunächst eine Verbindung mit dem App-Dienst ein.</span><span class="sxs-lookup"><span data-stu-id="bf90a-191">The code first establishes a connection with the app service.</span></span> <span data-ttu-id="bf90a-192">Die Verbindung bleibt offen, bis Sie `this.inventoryService` verwerfen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-192">The connection will remain open until you dispose `this.inventoryService`.</span></span> <span data-ttu-id="bf90a-193">Der Name des App-Diensts muss mit dem Attribut **AppService-Name** übereinstimmen, das Sie der Package.appxmanifest-Datei des AppServiceProvider-Projekts hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-193">The app service name must match the **AppService Name** attribute that you added to the AppServiceProvider project's Package.appxmanifest file.</span></span> <span data-ttu-id="bf90a-194">In diesem Beispiel ist dies `<uap:AppService Name="com.microsoft.inventory"/>`.</span><span class="sxs-lookup"><span data-stu-id="bf90a-194">In this example, it is `<uap:AppService Name="com.microsoft.inventory"/>`.</span></span>

<span data-ttu-id="bf90a-195">Es wird ein [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) mit dem Namen **message** erstellt, um den Befehl anzugeben, der an den App-Dienst gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="bf90a-195">A [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) named **message** is created to specify the command that we want to send to the app service.</span></span> <span data-ttu-id="bf90a-196">Der Beispiel-App-Dienst erwartet einen Befehl, der angibt, welche der beiden Aktionen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bf90a-196">The example app service expects a command to indicate which of two actions to take.</span></span> <span data-ttu-id="bf90a-197">Sie erhalten den Index aus dem Textfeld in der Client-App. Anschließend wird der Dienst mithilfe des Befehls `Item` aufgerufen, um die Beschreibung des Elements zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bf90a-197">We get the index from the textbox in the client app, and then call the service with the `Item` command to get the description of the item.</span></span> <span data-ttu-id="bf90a-198">Anschließend wird der Aufruf mit dem Befehl `Price` ausgeführt, um den Preis des Artikels zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bf90a-198">Then, we make the call with the `Price` command to get the item's price.</span></span> <span data-ttu-id="bf90a-199">Der Text der Schaltfläche wird auf das Ergebnis festgelegt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-199">The button text is set to the result.</span></span>

<span data-ttu-id="bf90a-200">Da [**AppServiceResponseStatus**](https://msdn.microsoft.com/library/windows/apps/dn921724) nur angibt, ob das Betriebssystem den Aufruf mit dem App-Dienst verknüpfen konnte, muss der Schlüssel `Status` im [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) geprüft werden, den wir vom App-Dienst erhalten, um sicherzustellen, dass die Anforderung erfüllt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="bf90a-200">Because [**AppServiceResponseStatus**](https://msdn.microsoft.com/library/windows/apps/dn921724) only indicates whether the operating system was able to connect the call to the app service, we check the `Status` key in the [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/dn636131) we receive from the app service to ensure that it was able to fulfill the request.</span></span>

6.  <span data-ttu-id="bf90a-201">Legen Sie das Projekt „ClientApp” in Visual Studio im Projektmappen-Explorer als Startprojekt fest, und führen Sie die Projektmappe aus.</span><span class="sxs-lookup"><span data-stu-id="bf90a-201">In Visual Studio, set the ClientApp project to be the startup project in the Solution Explorer window and run the solution.</span></span> <span data-ttu-id="bf90a-202">Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="bf90a-202">Enter the number 1 into the text box and click the button.</span></span> <span data-ttu-id="bf90a-203">Der Dienst sollte „Stuhl: Preis = 88,99“ zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="bf90a-203">You should get "Chair : Price = 88.99" back from the service.</span></span>

    ![Beispiel-App, die Stuhlpreis = 88,99 anzeigt](images/appserviceclientapp.png)

<span data-ttu-id="bf90a-205">Wenn beim Aufruf des App-Diensts ein Fehler auftritt, überprüfen Sie in „ClientApp” Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bf90a-205">If the app service call fails, check the following in the ClientApp:</span></span>

1.  <span data-ttu-id="bf90a-206">Stellen Sie sicher, dass der Paketfamilienname, der der Bestandsdienstverbindung zugewiesen ist, mit dem Paketfamiliennamen der App „AppServiceProvider” übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-206">Verify that the package family name assigned to the inventory service connection matches the package family name of the AppServiceProvider app.</span></span> <span data-ttu-id="bf90a-207">Weitere Informationen finden Sie unter **button\_Click()**`this.inventoryService.PackageFamilyName = "...";`).</span><span class="sxs-lookup"><span data-stu-id="bf90a-207">See: **button\_Click()**`this.inventoryService.PackageFamilyName = "...";`).</span></span>
2.  <span data-ttu-id="bf90a-208">Überprüfen Sie in **button\_Click()**, ob der App-Dienstname, der der Bestandsdienstverbindung zugewiesen ist, dem in der Datei „Package.appxmanifest” von „AppServiceProvider” angegebenen Namen des App-Diensts entspricht.</span><span class="sxs-lookup"><span data-stu-id="bf90a-208">In **button\_Click()**, verify that the app service name that is assigned to the inventory service connection matches the app service name in the AppServiceProvider's Package.appxmanifest file.</span></span> <span data-ttu-id="bf90a-209">Weitere Informationen finden Sie unter `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.</span><span class="sxs-lookup"><span data-stu-id="bf90a-209">See: `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.</span></span>
3.  <span data-ttu-id="bf90a-210">Stellen Sie sicher, dass die App „AppServiceProvider” bereitgestellt wurde (klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Bereitstellen** aus).</span><span class="sxs-lookup"><span data-stu-id="bf90a-210">Ensure that the AppServiceProvider app has been deployed (In the Solution Explorer, right-click the solution and choose **Deploy**).</span></span>

## <a name="debug-the-app-service"></a><span data-ttu-id="bf90a-211">Debuggen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="bf90a-211">Debug the app service</span></span>

1.  <span data-ttu-id="bf90a-212">Stellen Sie vor dem Debuggen sicher, dass die Projektmappe bereitgestellt wurde. Die App Dienstanbieter-App muss bereitgestellt werden, bevor der Dienst aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="bf90a-212">Ensure that the solution is deployed before debugging because the app service provider app must be deployed before the service can be called.</span></span> <span data-ttu-id="bf90a-213">(Klicken Sie in Visual Studio auf **Erstellen &gt; Projektmappe bereitstellen**.)</span><span class="sxs-lookup"><span data-stu-id="bf90a-213">(In Visual Studio, **Build &gt; Deploy Solution**).</span></span>
2.  <span data-ttu-id="bf90a-214">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt **AppServiceProvider**, und wählen Sie **Properties** aus.</span><span class="sxs-lookup"><span data-stu-id="bf90a-214">In the Solution Explorer, right-click the **AppServiceProvider** project and choose **Properties**.</span></span> <span data-ttu-id="bf90a-215">Ändern Sie auf der Registerkarte **Debuggen** die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**.</span><span class="sxs-lookup"><span data-stu-id="bf90a-215">From the **Debug** tab, change the **Start action** to **Do not launch, but debug my code when it starts**.</span></span> <span data-ttu-id="bf90a-216">(Hinweis: wenn Sie nicht C++ zum Implementieren Ihres App-Dienstanbieters verwenden, müssen Sie auf der Registerkarte **Debuggen** die Option **Anwendung starten** auf **Nein** ändern).</span><span class="sxs-lookup"><span data-stu-id="bf90a-216">(Note, if you were using C++ to implement your app service provider, from the **Debugging** tab you would change **Launch Application** to **No**).</span></span>
3.  <span data-ttu-id="bf90a-217">Legen Sie im Projekt „MyAppService” in der Datei „Class1.cs” einen Haltepunkt in `OnRequestReceived()` fest.</span><span class="sxs-lookup"><span data-stu-id="bf90a-217">In the MyAppService project, in the Class1.cs file, set a breakpoint in `OnRequestReceived()`.</span></span>
4.  <span data-ttu-id="bf90a-218">Legen Sie das Projekt „AppServiceProvider” als Startprojekt fest, und drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="bf90a-218">Set the AppServiceProvider project to be the startup project and press F5.</span></span>
5.  <span data-ttu-id="bf90a-219">Starten Sie „ClientApp” über das Startmenü (nicht über Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="bf90a-219">Start ClientApp from the Start menu (not from Visual Studio).</span></span>
6.  <span data-ttu-id="bf90a-220">Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="bf90a-220">Enter the number 1 into the text box and press the button.</span></span> <span data-ttu-id="bf90a-221">Der Debugger stoppt im App-Dienstaufruf am Haltepunkt in Ihrem App-Dienst.</span><span class="sxs-lookup"><span data-stu-id="bf90a-221">The debugger will stop in the app service call on the breakpoint in your app service.</span></span>

## <a name="debug-the-client"></a><span data-ttu-id="bf90a-222">Debuggen des Clients</span><span class="sxs-lookup"><span data-stu-id="bf90a-222">Debug the client</span></span>

1.  <span data-ttu-id="bf90a-223">Folgen Sie zum Debuggen des Clients, der den App-Dienst aufruft, den Anweisungen im vorherigen Schritt.</span><span class="sxs-lookup"><span data-stu-id="bf90a-223">Follow the instructions in the preceding step to debug the client that calls the app service.</span></span>
2.  <span data-ttu-id="bf90a-224">Starten Sie „ClientApp” über das Startmenü.</span><span class="sxs-lookup"><span data-stu-id="bf90a-224">Launch ClientApp from the Start menu.</span></span>
3.  <span data-ttu-id="bf90a-225">Hängen Sie den Debugger an den Prozess „ClientApp.exe” an (nicht an den Prozess „ApplicationFrameHost.exe”).</span><span class="sxs-lookup"><span data-stu-id="bf90a-225">Attach the debugger to the ClientApp.exe process (not the ApplicationFrameHost.exe process).</span></span> <span data-ttu-id="bf90a-226">(Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.)</span><span class="sxs-lookup"><span data-stu-id="bf90a-226">(In Visual Studio, choose **Debug &gt; Attach to Process...**.)</span></span>
4.  <span data-ttu-id="bf90a-227">Legen Sie im Projekt „ClientApp” einen Haltepunkt in **button\_Click()** fest.</span><span class="sxs-lookup"><span data-stu-id="bf90a-227">In the ClientApp project, set a breakpoint in **button\_Click()**.</span></span>
5.  <span data-ttu-id="bf90a-228">Die Haltepunkte in der Client-App und im App-Dienst werden jetzt erreicht, wenn Sie 1 in das Textfeld von „ClientApp” eingeben und auf die Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="bf90a-228">The breakpoints in both the client and the app service will now be hit when you enter the number 1 into the text box of the ClientApp and click the button.</span></span>

## <a name="general-app-service-troubleshooting"></a><span data-ttu-id="bf90a-229">Allgemeine Problembehandlung von App-Diensten</span><span class="sxs-lookup"><span data-stu-id="bf90a-229">General app service troubleshooting</span></span> ##

<span data-ttu-id="bf90a-230">Wenn beim Versuch, eine App mit einem Dienst zu verbinden der Status **AppUnavailable** auftritt, überprüfen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bf90a-230">If you encounter a **AppUnavailable** status after trying to connect to an app service, check the following:</span></span>

- <span data-ttu-id="bf90a-231">Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind.</span><span class="sxs-lookup"><span data-stu-id="bf90a-231">Ensure that the app service provider project and app service project are deployed.</span></span> <span data-ttu-id="bf90a-232">Beide müssen bereitgestellt werden, bevor der Client ausgeführt werden kann, da andernfalls der Client keine Verbindung zulassen kann.</span><span class="sxs-lookup"><span data-stu-id="bf90a-232">Both need to be deployed before running the client because otherwise the client won't have anything to connect to.</span></span> <span data-ttu-id="bf90a-233">Sie können von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-233">You can deploy from Visual Studio by using **Build** > **Deploy Solution**.</span></span>
- <span data-ttu-id="bf90a-234">Stellen Sie im Projektmappen-Explorer sicher, dass Ihr App-Dienstanbieterprojekt einen Projekt-zu-Projekt-Verweis auf das Projekt hat, das den App-Dienst implementiert.</span><span class="sxs-lookup"><span data-stu-id="bf90a-234">In the solution explorer, ensure that your app service provider project has a project-to-project reference to the project that implements the app service.</span></span>
- <span data-ttu-id="bf90a-235">Vergewissern Sie sich, dass der Eintrag `<Extensions>` und sein untergeordnetes Elemente zur Datei "Package.appxmanifest" des App-Dienstanbieterprojekts wie oben angegeben hinzugefügt wurden [Hinzufügen einer App-Diensterweiterung zu „package.appxmanifest”](#appxmanifest).</span><span class="sxs-lookup"><span data-stu-id="bf90a-235">Verify that the `<Extensions>` entry, and its child elements, have been added to the Package.appxmanifest file belonging to the app service provider project as specified above in [Add an app service extension to package.appxmanifest](#appxmanifest).</span></span>
- <span data-ttu-id="bf90a-236">Vergewissern Sie sich, dass die Zeichenfolge `AppServiceConnection.AppServiceName` in Ihrem Client, das den App-Dienstanbieter aufruft der Zeichenfolge `<uap3:AppService Name="..." />` der „Package.appxmanifest”-Datei des App-Dienstanbieterprojekts entspricht.</span><span class="sxs-lookup"><span data-stu-id="bf90a-236">Ensure that the `AppServiceConnection.AppServiceName` string in your client that calls the app service provider matches the `<uap3:AppService Name="..." />` specified in the app service provider project's Package.appxmanifest file.</span></span>
- <span data-ttu-id="bf90a-237">Stellen Sie sicher, dass `AppServiceConnection.PackageFamilyName` dem Paketfamiliennamen der App-Dienstanbieterkomponente wie in [Hinzufügen eine App-Diensterweiterung zu "Package.appxmanifest"](#appxmanifest) angegeben entspricht.</span><span class="sxs-lookup"><span data-stu-id="bf90a-237">Ensure that the `AppServiceConnection.PackageFamilyName` matches the package family name of the app service provider component as specified above in [Add an app service extension to package.appxmanifest](#appxmanifest)</span></span>
- <span data-ttu-id="bf90a-238">Für App-Dienste außerhalb des Prozesses wie in diesem Beispiel wird ein, überprüfen Sie, dass der `EntryPoint` des `<uap:Extension ...>` Elements „Package.appxmanifest”-Datei des App-Dienstanbieterprojekts dem Namespace und dem Klassennamen der öffentliche Klasse entspricht, das der `IBackgroundTask` in Ihrem App-Dienst-Projekt entspricht.</span><span class="sxs-lookup"><span data-stu-id="bf90a-238">For out-of-proc app services such as the one in this example, validate that the `EntryPoint` specified in the `<uap:Extension ...>` element of your app service provider project's Package.appxmanifest file matches the namespace and class name of the public class that implements `IBackgroundTask` in your app service project.</span></span>

### <a name="troubleshoot-debugging"></a><span data-ttu-id="bf90a-239">Problembehandlung beim Debuggen</span><span class="sxs-lookup"><span data-stu-id="bf90a-239">Troubleshoot debugging</span></span>

<span data-ttu-id="bf90a-240">Wenn der Debugger nicht an Haltepunkten in Ihrem App-Dienstanbieter oder App-Dienst-Projekte beendet wird, überprüfen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="bf90a-240">If the debugger does not stop at breakpoints in your app service provider or app service projects, check the following:</span></span>

- <span data-ttu-id="bf90a-241">Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind.</span><span class="sxs-lookup"><span data-stu-id="bf90a-241">Ensure that the app service provider project and app service project are deployed.</span></span> <span data-ttu-id="bf90a-242">Beide müssen bereitgestellt werden, bevor der Client ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bf90a-242">Both need to be deployed before running the client.</span></span> <span data-ttu-id="bf90a-243">Sie können diese von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bf90a-243">You can deploy them from Visual Studio by using **Build** > **Deploy Solution**.</span></span>
- <span data-ttu-id="bf90a-244">Stellen Sie sicher, dass das Projekt, das Sie debuggen möchten, als Startprojekt festgelegt ist und dass die Debugging-Eigenschaften für das Projekt so festgelegt sind, das das Projekt nicht ausgeführt wird, wenn F5 gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="bf90a-244">Ensure that the project you want to debug is set as the startup project and that the debugging properties for that project are set to not run the project when F5 is pressed.</span></span> <span data-ttu-id="bf90a-245">Klicken Sie mit der rechten Maustaste auf **Eigenschaften** und dann **Debug** (oder **Debugging** in C++).</span><span class="sxs-lookup"><span data-stu-id="bf90a-245">Right-click the project, then click **Properties**, and then **Debug** (or **Debugging** in C++).</span></span> <span data-ttu-id="bf90a-246">In C#, ändern Sie die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**.</span><span class="sxs-lookup"><span data-stu-id="bf90a-246">In C#, change the **Start action** to **Do not launch, but debug my code when it starts**.</span></span> <span data-ttu-id="bf90a-247">Legen Sie in C++ **Anwendung starten** auf **Nein** fest.</span><span class="sxs-lookup"><span data-stu-id="bf90a-247">In C++, set **Launch Application** to **No**.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf90a-248">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="bf90a-248">Remarks</span></span>

<span data-ttu-id="bf90a-249">Dieses Beispiel ist eine Einführung in das Erstellen eines App-Diensts, das als Hintergrundaufgabe ausgeführt wird, und Aufrufen des Diensts in einer anderen App.</span><span class="sxs-lookup"><span data-stu-id="bf90a-249">This example provides an introduction to creating an app service that runs as a background task and calling it from another app.</span></span> <span data-ttu-id="bf90a-250">Die wichtigsten Punkte sind das Erstellen einer Hintergrundaufgabe zum Hosten des App-Diensts, das Hinzufügen der Erweiterung „windows.appservice” zur Datei „Package.appxmanifest” der App des App-Dienstanbieters, das Abrufen des Paketfamiliennamens der App des App-Dienstanbieters, sodass in der Client-App eine Verbindung damit hergestellt werden kann, indem ein Projekt-zu-Projekt-Verweis vom App-Dienstanbieterprojekt auf das App-Dienst-Projekt hergestellt wird und das Verwenden von [**Windows.ApplicationModel.AppService.AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704) zum Aufrufen des Diensts.</span><span class="sxs-lookup"><span data-stu-id="bf90a-250">The key things to note are the creation of a background task to host the app service, the addition of the windows.appservice extension to the app service provider app's Package.appxmanifest file, obtaining the package family name of the app service provider app so that we can connect to it from the client app, adding a project-to-project reference from the app service provider project to the app service project, and using [**Windows.ApplicationModel.AppService.AppServiceConnection**](https://msdn.microsoft.com/library/windows/apps/dn921704) to call the service.</span></span>

## <a name="full-code-for-myappservice"></a><span data-ttu-id="bf90a-251">Vollständiger Code für „MyAppService”</span><span class="sxs-lookup"><span data-stu-id="bf90a-251">Full code for MyAppService</span></span>

```cs
using System;
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
using Windows.Foundation.Collections;

namespace MyAppService
{
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            this.backgroundTaskDeferral = taskInstance.GetDeferral(); // Get a deferral so that the service isn't terminated.
            taskInstance.Canceled += OnTaskCanceled; // Associate a cancellation handler with the background task.

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // Get a deferral because we use an awaitable API below to respond to the message
            // and we don't want this call to get cancelled while we are waiting.
            var messageDeferral = args.GetDeferral();

            ValueSet message = args.Request.Message;
            ValueSet returnData = new ValueSet();

            string command = message["Command"] as string;
            int? inventoryIndex = message["ID"] as int?;

            if (inventoryIndex.HasValue &&
                 inventoryIndex.Value >= 0 &&
                 inventoryIndex.Value < inventoryItems.GetLength(0))
            {
                switch (command)
                {
                    case "Price":
                        {
                            returnData.Add("Result", inventoryPrices[inventoryIndex.Value]);
                            returnData.Add("Status", "OK");
                            break;
                        }

                    case "Item":
                        {
                            returnData.Add("Result", inventoryItems[inventoryIndex.Value]);
                            returnData.Add("Status", "OK");
                            break;
                        }

                    default:
                        {
                            returnData.Add("Status", "Fail: unknown command");
                            break;
                        }
                }
            }
            else
            {
                returnData.Add("Status", "Fail: Index out of range");
            }

            await args.Request.SendResponseAsync(returnData); // Return the data to the caller.
            // Complete the deferral so that the platform knows that we're done responding to the app service call.
            // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
            messageDeferral.Complete();
        }


        private void OnTaskCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            if (this.backgroundTaskDeferral != null)
            {
                // Complete the service deferral.
                this.backgroundTaskDeferral.Complete();
            }
        }
    }
}
```

## <a name="related-topics"></a><span data-ttu-id="bf90a-252">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bf90a-252">Related topics</span></span>

* [<span data-ttu-id="bf90a-253">Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App</span><span class="sxs-lookup"><span data-stu-id="bf90a-253">Convert an app service to run in the same process as its host app</span></span>](convert-app-service-in-process.md)
* [<span data-ttu-id="bf90a-254">Unterstützen Ihrer App mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="bf90a-254">Support your app with background tasks</span></span>](support-your-app-with-background-tasks.md)
* [<span data-ttu-id="bf90a-255">Codebeispiel für App-Dienst (C#, C++ und VB)</span><span class="sxs-lookup"><span data-stu-id="bf90a-255">App service code sample (C#, C++, and VB)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices)
