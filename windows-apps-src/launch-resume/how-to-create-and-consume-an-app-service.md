---
title: Erstellen und Verwenden eines App-Diensts
description: Hier erfahren Sie, wie Sie eine App für die Universelle Windows-Plattform (UWP) erstellen, die Dienste für andere UWP-Apps bereitstellen kann, und wie Sie diese Dienste nutzen.
ms.assetid: 6E48B8B6-D3BF-4AE2-85FB-D463C448C9D3
keywords: App-zu-app-Kommunikation, prozessübergreifende Kommunikation, IPC, Hintergrund Kommunikation, app zu app-app-Dienst
ms.date: 1/16/2019
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9029c8ee3a930e66ebdbd0c4d0681d87486a8393
ms.sourcegitcommit: 6e2027f8ebc1d891d27ea6b2e4676d592871bcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "9011260"
---
# <a name="create-and-consume-an-app-service"></a><span data-ttu-id="c5fc6-104">Erstellen und Verwenden eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="c5fc6-104">Create and consume an app service</span></span>

<span data-ttu-id="c5fc6-105">App-Dienste sind UWP-Apps, die Dienste für andere UWP-Apps bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-105">App services are UWP apps that provide services to other UWP apps.</span></span> <span data-ttu-id="c5fc6-106">Sie entsprechen Webdiensten auf einem Gerät.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-106">They are analogous to web services, on a device.</span></span> <span data-ttu-id="c5fc6-107">Ein App-Dienst wird als Hintergrundaufgabe in der Host-App ausgeführt und kann seine Dienste auch anderen Apps bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-107">An app service runs as a background task in the host app and can provide its service to other apps.</span></span> <span data-ttu-id="c5fc6-108">Beispielsweise kann der Barcode-Scanner eines App-Dienstes auch anderen Apps nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-108">For example, an app service might provide a bar code scanner service that other apps could use.</span></span> <span data-ttu-id="c5fc6-109">Oder möglicherweise verfügt eine Enterprise-Suite von Apps über einen gemeinschaftlichen App-Dienst für die Rechtschreibprüfung, der auch den anderen Apps in der Suite zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-109">Or perhaps an Enterprise suite of apps has a common spell checking app service that is available to the other apps in the suite.</span></span>  <span data-ttu-id="c5fc6-110">App-Dienste ermöglichen Ihnen, Dienste ohne UI zu erstellen, die von Apps auf demselben Gerät aufgerufen werden können. Ab Windows 10, Version 1607 ist dies auch für Remote-Geräte möglich.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-110">App services let you create UI-less services that apps can call on the same device, and starting with Windows 10, version 1607, on remote devices.</span></span>

<span data-ttu-id="c5fc6-111">Ab Windows10, Version 1607, können Sie App-Dienste erstellen, die im gleichen Prozess wie die Vordergrund-App ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-111">Starting in Windows 10, version 1607, you can create app services that run in the same process as the host app.</span></span> <span data-ttu-id="c5fc6-112">In diesem Artikel geht es um das Erstellen und Verwenden von App-Diensten, die in einem separaten Hintergrundprozess ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-112">This article focuses on creating and consuming an app service that runs in a separate background process.</span></span> <span data-ttu-id="c5fc6-113">Unter [Konvertieren eines App-Diensts für die Ausführung im gleichen Prozess wie seine Host-App](convert-app-service-in-process.md) finden Sie weitere Informationen zum Ausführen eines App-Dienstes, der im gleichen Prozess wie der Anbieter ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-113">See [Convert an app service to run in the same process as its host app](convert-app-service-in-process.md) for more details about running an app service in the same process as the provider.</span></span>

<span data-ttu-id="c5fc6-114">Den Code für einen App-Dienst finden Sie unter [Beispiel-Apps für die Universelle Windows-Plattform (UWP)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-114">For an app service code sample, see [Universal Windows Platform (UWP) app samples](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices).</span></span>

## <a name="create-a-new-app-service-provider-project"></a><span data-ttu-id="c5fc6-115">Erstellen eines neuen App-Dienstanbieterprojekts</span><span class="sxs-lookup"><span data-stu-id="c5fc6-115">Create a new app service provider project</span></span>

<span data-ttu-id="c5fc6-116">In dieser Anleitung erstellen wir der Einfachheit halber alles in einer Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-116">In this how-to, we'll create everything in one solution for simplicity.</span></span>

1. <span data-ttu-id="c5fc6-117">Erstellen Sie in Visual Studio 2015 oder höher ein neues UWP-app-Projekt, und nennen Sie sie **"AppServiceProvider"**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-117">In Visual Studio 2015 or later, create a new UWP app project and name it **AppServiceProvider**.</span></span>
    1. <span data-ttu-id="c5fc6-118">Wählen Sie die **Datei > neue > Projekt...**</span><span class="sxs-lookup"><span data-stu-id="c5fc6-118">Select **File > New > Project...**</span></span> 
    2. <span data-ttu-id="c5fc6-119">Wählen Sie im Dialogfeld " **Neues Projekt** " **installiert > Visual C#-> leere App (Universal Windows)**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-119">In the **New Project** dialog box, select **Installed > Visual C# > Blank App (Universal Windows)**.</span></span> <span data-ttu-id="c5fc6-120">Dies ist die App, die den App-Dienst für andere UWP-Apps verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-120">This will be the app that makes the app service available to other UWP apps.</span></span>
    3. <span data-ttu-id="c5fc6-121">Geben Sie dem Projekt **"AppServiceProvider"**, wählen Sie einen Speicherort für sie, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-121">Name the project **AppServiceProvider**, choose a location for it, and click **OK**.</span></span>

2. <span data-ttu-id="c5fc6-122">Wenn Sie gefragt werden, wählen eine **Ziel-** und **Mindestversion** für das Projekt, wählen Sie mindestens **10.0.14393**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-122">When asked to select a **Target** and **Minimum version** for the project, select at least **10.0.14393**.</span></span> <span data-ttu-id="c5fc6-123">Wenn Sie das neuen Attribut **"supportsmultipleinstances"** verwenden möchten, Sie müssen werden mithilfe von Visual Studio 2017 und Ziel **10.0.15063** (**Windows 10 Creators Update**) oder höher.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-123">If you want to use the new **SupportsMultipleInstances** attribute, you must be using Visual Studio 2017 and target **10.0.15063** (**Windows 10 Creators Update**) or higher.</span></span>

<span id="appxmanifest"/>

## <a name="add-an-app-service-extension-to-packageappxmanifest"></a><span data-ttu-id="c5fc6-124">Hinzufügen einer app-diensterweiterung zu "Package.appxmanifest"</span><span class="sxs-lookup"><span data-stu-id="c5fc6-124">Add an app service extension to Package.appxmanifest</span></span>

<span data-ttu-id="c5fc6-125">Öffnen Sie im Projekt **"AppServiceProvider"** die Datei **"Package.appxmanifest"** in einem Text-Editor:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-125">In the **AppServiceProvider** project, open the **Package.appxmanifest** file in a text editor:</span></span> 

1. <span data-ttu-id="c5fc6-126">Maustaste darauf im **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-126">Right-click it in the **Solution Explorer**.</span></span> 
2. <span data-ttu-id="c5fc6-127">Wählen Sie **Öffnen mit**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-127">Select **Open With**.</span></span> 
3. <span data-ttu-id="c5fc6-128">Wählen Sie den **XML (Text) Editor**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-128">Select **XML (Text) Editor**.</span></span> 

<span data-ttu-id="c5fc6-129">Fügen Sie die folgenden `AppService` Erweiterung innerhalb der `<Application>` Element.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-129">Add the following `AppService` extension inside the `<Application>` element.</span></span> <span data-ttu-id="c5fc6-130">Durch dieses Beispiel wird der `com.microsoft.inventory`-Dienst angekündigt, und die App wird als App-Dienstanbieter identifiziert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-130">This example advertises the `com.microsoft.inventory` service and is what identifies this app as an app service provider.</span></span> <span data-ttu-id="c5fc6-131">Der eigentliche Dienst wird als Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-131">The actual service will be implemented as a background task.</span></span> <span data-ttu-id="c5fc6-132">Das Projekt, das den App-Dienst bereitstellt, macht den Dienst für andere Apps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-132">The app service project exposes the service to other apps.</span></span> <span data-ttu-id="c5fc6-133">Wir empfehlen, einen umgekehrten Domänennamen für den Dienstnamen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-133">We recommend using a reverse domain name style for the service name.</span></span>

<span data-ttu-id="c5fc6-134">Beachten Sie, dass der Namespacepräfix `xmlns:uap4` und das Attribut `uap4:SupportsMultipleInstances` nur dann gültig sind, wenn Sie die Windows SDK-Version 10.0.15063 oder höher als Ziel setzen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-134">Note that the `xmlns:uap4` namespace prefix and the `uap4:SupportsMultipleInstances` attribute are only valid if you are targeting Windows SDK version 10.0.15063 or higher.</span></span> <span data-ttu-id="c5fc6-135">Sie können diese sicher entfernen, wenn Sie ältere SDK-Versionen als Zielgruppe setzen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-135">You can safely remove them if you are targeting older SDK versions.</span></span>

``` xml
<Package
    ...
    xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    ...
    <Applications>
        <Application Id="AppServiceProvider.App"
          Executable="$targetnametoken$.exe"
          EntryPoint="AppServiceProvider.App">
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

<span data-ttu-id="c5fc6-136">Das `Category`-Attribut identifiziert die App als App-Dienstanbieter.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-136">The `Category` attribute identifies this application as an app service provider.</span></span>

<span data-ttu-id="c5fc6-137">Die `EntryPoint` -Attribut identifiziert die Namespace-qualifizierte Klasse, die den Dienst wir als Nächstes implementieren implementiert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-137">The `EntryPoint` attribute identifies the namespace qualified class that implements the service, which we'll implement next.</span></span>

<span data-ttu-id="c5fc6-138">Die `SupportsMultipleInstances` -Attribut gibt an, dass es sich bei jedem Aufruf des app-Diensts, die sie in einem neuen Prozess ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-138">The `SupportsMultipleInstances` attribute indicates that each time the app service is called that it should run in a new process.</span></span> <span data-ttu-id="c5fc6-139">Dies ist nicht erforderlich, jedoch ist Sie verfügbar, wenn Sie diese Funktionalität erfordern und die 10.0.15063 Ziel als SDK (**Windows 10 Creators Update**) oder höher.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-139">This is not required but is available to you if you need that functionality and are targeting the 10.0.15063 SDK (**Windows 10 Creators Update**) or higher.</span></span> <span data-ttu-id="c5fc6-140">Der Präfix `uap4` Namespace sollte dabei angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-140">It also should be prefaced by the `uap4` namespace.</span></span>

## <a name="create-the-app-service"></a><span data-ttu-id="c5fc6-141">Erstellen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="c5fc6-141">Create the app service</span></span>

1.  <span data-ttu-id="c5fc6-142">Ein App-Dienst kann als Hintergrundaufgabe implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-142">An app service can be implemented as a background task.</span></span> <span data-ttu-id="c5fc6-143">Dadurch kann eine Vordergrund-App einen App-Dienst in einer anderen App aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-143">This enables a foreground application to invoke an app service in another application.</span></span> <span data-ttu-id="c5fc6-144">Um ein app-Dienst als Hintergrundaufgabe zu erstellen, fügen Sie ein neues Komponente für Windows-Runtime-Projekt der Projektmappe (**Datei &gt; hinzufügen &gt; neues Projekt**) mit dem Namen **"myappservice"**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-144">To create an app service as a background task, add a new Windows Runtime Component project to the solution (**File &gt; Add &gt; New Project**) named **MyAppService**.</span></span> <span data-ttu-id="c5fc6-145">Wählen Sie im Dialogfeld " **Neues Projekt hinzufügen** " **installiert > Visual C#-> Komponente für Windows-Runtime (Universal Windows)**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-145">In the **Add New Project** dialog box, choose **Installed > Visual C# > Windows Runtime Component (Universal Windows)**.</span></span>
2.  <span data-ttu-id="c5fc6-146">Fügen Sie im Projekt **"AppServiceProvider"** einen Projekt-zu-Projekt-Verweis auf das neue **Projekt "myappservice"** hinzu (klicken Sie im **Projektmappen-Explorer**mit der Maustaste auf das **"AppServiceProvider"** Projekt > **Hinzufügen**  >  \*\* Verweisen auf\*\* > **Projekte** > **Lösung**, wählen Sie **"myappservice"** > **OK**).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-146">In the **AppServiceProvider** project, add a project-to-project reference to the new **MyAppService** project (in the **Solution Explorer**, right-click on the **AppServiceProvider** project > **Add** > **Reference** > **Projects** > **Solution**, select **MyAppService** > **OK**).</span></span> <span data-ttu-id="c5fc6-147">Dieser Schritt ist unerlässlich, da der App-Dienst ohne das Hinzufügen der Referenz keine Laufzeit damit verbindet.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-147">This step is critical because if you do not add the reference, the app service won't connect at runtime.</span></span>
3.  <span data-ttu-id="c5fc6-148">Fügen Sie die folgenden Anweisungen zur **Verwendung** im Projekt **"myappservice"** am Anfang von **"Class1.cs"**:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-148">In the **MyAppService** project, add the following **using** statements to the top of **Class1.cs**:</span></span>
    ```cs
    using Windows.ApplicationModel.AppService;
    using Windows.ApplicationModel.Background;
    using Windows.Foundation.Collections;
    ```

4.  <span data-ttu-id="c5fc6-149">Benennen Sie **"Class1.cs"** in **Inventory.cs**, und Ersetzen Sie den Stubcode für **Class1** durch eine neue hintergrundaufgabenklasse **mit dem Namen**:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-149">Rename **Class1.cs** to **Inventory.cs**, and replace the stub code for **Class1** with a new background task class named **Inventory**:</span></span>

    ```cs
    public sealed class Inventory : IBackgroundTask
    {
        private BackgroundTaskDeferral backgroundTaskDeferral;
        private AppServiceConnection appServiceconnection;
        private String[] inventoryItems = new string[] { "Robot vacuum", "Chair" };
        private double[] inventoryPrices = new double[] { 129.99, 88.99 };

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get a deferral so that the service isn't terminated.
            this.backgroundTaskDeferral = taskInstance.GetDeferral();

            // Associate a cancellation handler with the background task.
            taskInstance.Canceled += OnTaskCanceled;

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // This function is called when the app service receives a request.
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

    <span data-ttu-id="c5fc6-150">In dieser Klasse wird der App-Dienst ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-150">This class is where the app service will do its work.</span></span>

    <span data-ttu-id="c5fc6-151">**Führen Sie** wird aufgerufen, wenn die Hintergrundaufgabe erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-151">**Run** is called when the background task is created.</span></span> <span data-ttu-id="c5fc6-152">Da Hintergrundaufgaben nach Abschluss von **Run** beendet werden, implementiert der Code eine Verzögerung, damit die Hintergrundaufgabe zum Verarbeiten von Anforderungen aktiv bleibt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-152">Because background tasks are terminated after **Run** completes, the code takes out a deferral so that the background task will stay up to serve requests.</span></span> <span data-ttu-id="c5fc6-153">Ein App-Dienst, der als Hintergrundaufgabe implementiert ist, bleibt für ungefähr 30Sekunden aktiv, nachdem er einen Anruf erhält, es sei denn, er wird innerhalb dieses Zeitraums erneut aufgerufen oder es wird eine Verzögerung entnommen. Wenn der App-Dienst im gleichen Prozess wie der Aufrufer implementiert ist, ist die Lebensdauer des App-Diensts an die Lebensdauer des Aufrufers gebunden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-153">An app service that is implemented as a background task will stay alive for about 30 seconds after it receives a call unless it is called again within that time window or a deferral is taken out. If the app service is implemented in the same process as the caller, the lifetime of the app service is tied to the lifetime of the caller.</span></span>

    <span data-ttu-id="c5fc6-154">Die Lebensdauer des App-Diensts hängt vom Aufrufer ab:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-154">The lifetime of the app service depends on the caller:</span></span>

    * <span data-ttu-id="c5fc6-155">Wenn der Aufrufer im Vordergrund ausgeführt wird, ist die app-Dienst-Lebensdauer des Aufrufers.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-155">If the caller is in the foreground, the app service lifetime is the same as the caller.</span></span>
    * <span data-ttu-id="c5fc6-156">Wenn der Aufrufer im Hintergrund ist, erhält der app-Dienst nach 30 Sekunden ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-156">If the caller is in the background, the app service gets 30 seconds to run.</span></span> <span data-ttu-id="c5fc6-157">Das Entfernen einer Verzögerung stellt ein Mal zusätzlich 5Sekunden bereit.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-157">Taking out a deferral provides an additional one time 5 seconds.</span></span>

    <span data-ttu-id="c5fc6-158">**OnTaskCanceled** wird aufgerufen, wenn die Aufgabe abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-158">**OnTaskCanceled** is called when the task is canceled.</span></span> <span data-ttu-id="c5fc6-159">Die Aufgabe wird abgebrochen, wenn die Client-app gibt den [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704)frei, die Client-app angehalten wird, das Betriebssystem heruntergefahren oder in den Ruhemodus geht oder das Betriebssystem nicht Ressourcen zum Ausführen der Aufgabe genügend.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-159">The task is canceled when the client app disposes the [AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704), the client app is suspended, the OS is shut down or sleeps, or the OS runs out of resources to run the task.</span></span>

## <a name="write-the-code-for-the-app-service"></a><span data-ttu-id="c5fc6-160">Schreiben des Codes für den App-Dienst</span><span class="sxs-lookup"><span data-stu-id="c5fc6-160">Write the code for the app service</span></span>

<span data-ttu-id="c5fc6-161">**OnRequestReceived** wird in der Code für den app-Dienst.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-161">**OnRequestReceived** is where the code for the app service goes.</span></span> <span data-ttu-id="c5fc6-162">Ersetzen Sie den Stub **OnRequestReceived** im **Projekt "myappservice"** **Inventory.cs** , mit dem Code aus diesem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-162">Replace the stub **OnRequestReceived** in **MyAppService**'s **Inventory.cs** with the code from this example.</span></span> <span data-ttu-id="c5fc6-163">Dieser Code ruft einen Index für ein Bestandselement ab und übergibt ihn zusammen mit einer Befehlszeichenfolge an den Dienst, um den Namen und Preis des angegebenen Bestandselements abzurufen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-163">This code gets an index for an inventory item and passes it, along with a command string, to the service to retrieve the name and the price of the specified inventory item.</span></span> <span data-ttu-id="c5fc6-164">Fügen Sie Ihren eigenen Projekten einen Code zur Fehlerbehandlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-164">For your own projects, add error handling code.</span></span>

```cs
private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
{
    // Get a deferral because we use an awaitable API below to respond to the message
    // and we don't want this call to get canceled while we are waiting.
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

    try
    {
        // Return the data to the caller.
        await args.Request.SendResponseAsync(returnData);
    }
    catch (Exception e)
    {
        // Your exception handling code here.
    }
    finally
    {
        // Complete the deferral so that the platform knows that we're done responding to the app service call.
        // Note for error handling: this must be called even if SendResponseAsync() throws an exception.
        messageDeferral.Complete();
    }
}
```

<span data-ttu-id="c5fc6-165">Beachten Sie, dass **OnRequestReceived** **Async** ist, da wir eine awaitable [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) in diesem Beispiel Methodenaufruf.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-165">Note that **OnRequestReceived** is **async** because we make an awaitable method call to [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) in this example.</span></span>

<span data-ttu-id="c5fc6-166">Damit der Dienst **asynchronen** Methoden im **OnRequestReceived** -Handler verwenden kann, wird eine Verzögerung entnommen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-166">A deferral is taken so that the service can use **async** methods in the **OnRequestReceived** handler.</span></span> <span data-ttu-id="c5fc6-167">Dadurch wird sichergestellt, dass der Aufruf von **OnRequestReceived** erst abgeschlossen wird, wenn die Nachricht verarbeitet wurde.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-167">It ensures that the call to **OnRequestReceived** does not complete until it is done processing the message.</span></span>  <span data-ttu-id="c5fc6-168">[SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) sendet das Ergebnis an den Aufrufer.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-168">[SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) sends the result to the caller.</span></span> <span data-ttu-id="c5fc6-169">**SendResponseAsync** signalisiert nicht den Abschluss des Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-169">**SendResponseAsync** does not signal the completion of the call.</span></span> <span data-ttu-id="c5fc6-170">[SendMessageAsync](https://msdn.microsoft.com/library/windows/apps/dn921712) wird durch den Abschluss der Verzögerung signalisiert, dass **OnRequestReceived** abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-170">It is the completion of the deferral that signals to [SendMessageAsync](https://msdn.microsoft.com/library/windows/apps/dn921712) that **OnRequestReceived** has completed.</span></span> <span data-ttu-id="c5fc6-171">Der Aufruf von **SendResponseAsync** ist in einem Versuch/final-Block eingeschlossen, da die Verzögerung abgeschlossen werden muss, auch wenn **SendResponseAsync** eine Ausnahme auslöst.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-171">The call to **SendResponseAsync** is wrapped in a try/finally block because you must complete the deferral even if **SendResponseAsync** throws an exception.</span></span>

<span data-ttu-id="c5fc6-172">App-Dienste verwenden [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) Objekte zum Austauschen von Informationen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-172">App services use [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) objects to exchange information.</span></span> <span data-ttu-id="c5fc6-173">Die Größe der Daten, die übergeben werden können, ist nur durch die Systemressourcen begrenzt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-173">The size of the data you may pass is only limited by system resources.</span></span> <span data-ttu-id="c5fc6-174">Es gibt keine vordefinierten Schlüssel zur Verwendung in Ihrem **ValueSet**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-174">There are no predefined keys for you to use in your **ValueSet**.</span></span> <span data-ttu-id="c5fc6-175">Sie müssen bestimmen, welche Schlüsselwerte Sie zum Definieren des Protokolls für Ihren App-Dienst verwenden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-175">You must determine which key values you will use to define the protocol for your app service.</span></span> <span data-ttu-id="c5fc6-176">Dieses Protokoll muss beim Schreiben des Aufrufers berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-176">The caller must be written with that protocol in mind.</span></span> <span data-ttu-id="c5fc6-177">In diesem Beispiel haben wir einen Schlüssel namens `Command` ausgewählt, dessen Wert angibt, ob der App-Dienst den Namen des Bestandselements oder seinen Preis bereitstellen soll.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-177">In this example, we have chosen a key named `Command` that has a value that indicates whether we want the app service to provide the name of the inventory item or its price.</span></span> <span data-ttu-id="c5fc6-178">Der Index des Bestandsnamens wird unter dem Schlüssel `ID` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-178">The index of the inventory name is stored under the `ID` key.</span></span> <span data-ttu-id="c5fc6-179">Der Rückgabewert wird unter dem Schlüssel `Result` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-179">The return value is stored under the `Result` key.</span></span>

<span data-ttu-id="c5fc6-180">An den Aufrufer wird eine [AppServiceClosedStatus](https://msdn.microsoft.com/library/windows/apps/dn921703)-Enumeration zurückgegeben, um anzugeben, ob der Aufruf des App-Diensts erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-180">An [AppServiceClosedStatus](https://msdn.microsoft.com/library/windows/apps/dn921703) enum is returned to the caller to indicate whether the call to the app service succeeded or failed.</span></span> <span data-ttu-id="c5fc6-181">Beim Aufruf des App-Diensts könnte z.B. ein Fehler auftreten, wenn das Betriebssystem den Dienstendpunkt abbricht, da keine Ressourcen mehr verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-181">An example of how the call to the app service could fail is if the OS aborts the service endpoint because its resources have been exceeded.</span></span> <span data-ttu-id="c5fc6-182">Sie können über [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) zusätzliche Fehlerinformationen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-182">You can return additional error information via the [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131).</span></span> <span data-ttu-id="c5fc6-183">In diesem Beispiel verwenden wir einen Schlüssel mit dem Namen `Status`, um detailliertere Fehlerinformationen an den Aufrufer zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-183">In this example, we use a key named `Status` to return more detailed error information to the caller.</span></span>

<span data-ttu-id="c5fc6-184">Der Aufruf von [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) gibt [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) an den Aufrufer zurück.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-184">The call to [SendResponseAsync](https://msdn.microsoft.com/library/windows/apps/dn921722) returns the [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) to the caller.</span></span>

## <a name="deploy-the-service-app-and-get-the-package-family-name"></a><span data-ttu-id="c5fc6-185">Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens</span><span class="sxs-lookup"><span data-stu-id="c5fc6-185">Deploy the service app and get the package family name</span></span>

<span data-ttu-id="c5fc6-186">Die app-Dienstanbieter muss bereitgestellt werden, bevor Sie sie von einem Client aus aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-186">The app service provider must be deployed before you can call it from a client.</span></span> <span data-ttu-id="c5fc6-187">Sie benötigen auch den paketfamiliennamen des app-Diensts, um sie aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-187">You will also need the package family name of the app service in order to call it.</span></span>

<span data-ttu-id="c5fc6-188">Eine Möglichkeit zum Abrufen der paketfamilienname der app-Service-Anwendung ist [Windows.ApplicationModel.Package.Current.Id.FamilyName](https://msdn.microsoft.com/library/windows/apps/br224670) von innerhalb des Projekts **"AppServiceProvider"** (z. B. von der **App** -Konstruktor in **aufrufen "App.Xaml.cs"**) und das Ergebnis zu notieren.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-188">One way to get the package family name of the app service application is to call [Windows.ApplicationModel.Package.Current.Id.FamilyName](https://msdn.microsoft.com/library/windows/apps/br224670) from within the **AppServiceProvider** project (for example, from the **App** constructor in **App.xaml.cs**) and note the result.</span></span> <span data-ttu-id="c5fc6-189">Zum Ausführen von **"AppServiceProvider"** in Visual Studio im **Projektmappen** -Explorer als Startprojekt festlegen Sie, und führen Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-189">To run **AppServiceProvider** in Visual Studio, set it as the startup project in the **Solution Explorer** window and run the project.</span></span>

<span data-ttu-id="c5fc6-190">Eine weitere Möglichkeit zum Abrufen des paketfamiliennamens ist die Lösung bereitstellen (**Erstellen &gt; Projektmappe bereitstellen**), und notieren Sie den vollständigen Paketnamens im **Ausgabefenster** (**Ansicht &gt; Ausgabe**).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-190">Another way to get the package family name is to deploy the solution (**Build &gt; Deploy Solution**) and note the full package name in the **Output** window (**View &gt; Output**).</span></span> <span data-ttu-id="c5fc6-191">Sie müssen die Plattforminformationen aus der Zeichenfolge im **Ausgabefenster auf den Paketnamen abzuleiten** entfernen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-191">You must remove the platform information from the string in the **Output** window to derive the package name.</span></span> <span data-ttu-id="c5fc6-192">Beispielsweise, wenn im **Ausgabefenster** der vollständige Paketname gemeldet wurden:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-192">For example, if the full package name reported in the **Output** window were:</span></span>

`Microsoft.SDKSamples.AppServicesProvider.CPP_1.0.0.0_x86__8wekyb3d8bbwe`

<span data-ttu-id="c5fc6-193">Und extrahieren Sie Sie würden `1.0.0.0\_x86\_\_`, verlassen die folgenden als den paketfamiliennamen:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-193">Then you would extract `1.0.0.0\_x86\_\_`, leaving the following as the package family name:</span></span>

`Microsoft.SDKSamples.AppServicesProvider.CPP_8wekyb3d8bbwe`

## <a name="write-a-client-to-call-the-app-service"></a><span data-ttu-id="c5fc6-194">Schreiben eines Clients zum Aufrufen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="c5fc6-194">Write a client to call the app service</span></span>

1.  <span data-ttu-id="c5fc6-195">Fügen Sie der Projektmappe ein neues leeres Projekt für eine Universelle Windows-App mit dem Namen **Datei &gt; Hinzufügen &gt; Neues Projekt** hinzu.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-195">Add a new blank Windows Universal app project to the solution with **File &gt; Add &gt; New Project**.</span></span> <span data-ttu-id="c5fc6-196">Klicken Sie im Dialogfeld " **Neues Projekt hinzufügen** " Wählen Sie **installiert > Visual C#-> leere App (Universal Windows)** , und nennen Sie sie **"ClientApp"**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-196">In the **Add New Project** dialog box, choose **Installed > Visual C# > Blank App (Universal Windows)** and name it **ClientApp**.</span></span>

2.  <span data-ttu-id="c5fc6-197">Fügen Sie im Projekt **"ClientApp"** am Anfang der **Datei "MainPage.Xaml.cs"** die folgende Anweisung **verwenden** hinzu:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-197">In the **ClientApp** project, add the following **using** statement to the top of **MainPage.xaml.cs**:</span></span>
    ```cs
    using Windows.ApplicationModel.AppService;
    ```

3.  <span data-ttu-id="c5fc6-198">Fügen Sie ein Textfeld **TextBox** und eine Schaltfläche, um **"MainPage.xaml"** genannt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-198">Add a text box called **textBox** and a button to **MainPage.xaml**.</span></span>

4.  <span data-ttu-id="c5fc6-199">Fügen Sie eine Schaltfläche click-Ereignishandler für die Schaltfläche **Button_Click**aufgerufen und Signatur des schaltflächenhandlers das Schlüsselwort **Async** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-199">Add a button click handler for the button called **button_Click**, and add the keyword **async** to the button handler's signature.</span></span>

5. <span data-ttu-id="c5fc6-200">Ersetzen Sie den Stub des Klickhandlers für die Schaltfläche durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-200">Replace the stub of your button click handler with the following code.</span></span> <span data-ttu-id="c5fc6-201">Vergessen Sie nicht die `inventoryService`-Felddeklaration.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-201">Be sure to include the `inventoryService` field declaration.</span></span>
    ```cs
   private AppServiceConnection inventoryService;

   private async void button_Click(object sender, RoutedEventArgs e)
   {
       // Add the connection.
       if (this.inventoryService == null)
       {
           this.inventoryService = new AppServiceConnection();

           // Here, we use the app service name defined in the app service 
           // provider's Package.appxmanifest file in the <Extension> section.
           this.inventoryService.AppServiceName = "com.microsoft.inventory";

           // Use Windows.ApplicationModel.Package.Current.Id.FamilyName 
           // within the app service provider to get this value.
           this.inventoryService.PackageFamilyName = "Replace with the package family name";

           var status = await this.inventoryService.OpenAsync();

           if (status != AppServiceConnectionStatus.Success)
           {
               textBox.Text= "Failed to connect";
               this.inventoryService = null;
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
           // Get the data  that the service sent to us.
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
    
    <span data-ttu-id="c5fc6-202">Ersetzen Sie den Paketfamiliennamen in der Zeile `this.inventoryService.PackageFamilyName = "Replace with the package family name";` durch den Paketfamiliennamen des **AppServiceProvider**-Projekts, das Sie in [Bereitstellen der Dienstanbieter-App und Abrufen des Paketfamiliennamens](#deploy-the-service-app-and-get-the-package-family-name) erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-202">Replace the package family name in the line `this.inventoryService.PackageFamilyName = "Replace with the package family name";` with the package family name of the **AppServiceProvider** project that you obtained above in [Deploy the service app and get the package family name](#deploy-the-service-app-and-get-the-package-family-name).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c5fc6-203">Achten Sie darauf, dass Sie in das String-Literal, anstatt sie in einer Variablen einfügen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-203">Make sure to paste in the string literal, rather than putting it in a variable.</span></span> <span data-ttu-id="c5fc6-204">Es wird nicht funktionieren, wenn Sie eine Variable verwenden.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-204">It will not work if you use a variable.</span></span>

    <span data-ttu-id="c5fc6-205">Der Code richtet zunächst eine Verbindung mit dem App-Dienst ein.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-205">The code first establishes a connection with the app service.</span></span> <span data-ttu-id="c5fc6-206">Die Verbindung bleibt offen, bis Sie `this.inventoryService` verwerfen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-206">The connection will remain open until you dispose `this.inventoryService`.</span></span> <span data-ttu-id="c5fc6-207">Name des app-Dienst muss übereinstimmen die `AppService` des Elements `Name` -Attribut, das Sie die **Datei "Package.appxmanifest** " des Projekts **"AppServiceProvider"** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-207">The app service name must match the `AppService` element's `Name` attribute that you added to the **AppServiceProvider** project's **Package.appxmanifest** file.</span></span> <span data-ttu-id="c5fc6-208">In diesem Beispiel ist dies `<uap3:AppService Name="com.microsoft.inventory"/>`.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-208">In this example, it is `<uap3:AppService Name="com.microsoft.inventory"/>`.</span></span>

    <span data-ttu-id="c5fc6-209">Ein [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) mit dem Namen `message` wird erstellt, um den Befehl angeben, die wir an der app-Dienst senden möchten.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-209">A [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) named `message` is created to specify the command that we want to send to the app service.</span></span> <span data-ttu-id="c5fc6-210">Der Beispiel-App-Dienst erwartet einen Befehl, der angibt, welche der beiden Aktionen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-210">The example app service expects a command to indicate which of two actions to take.</span></span> <span data-ttu-id="c5fc6-211">Wir erhalten den Index aus dem Textfeld in der Client-app, und rufen Sie dann den Dienst mit den `Item` Befehl aus, um die Beschreibung des Elements zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-211">We get the index from the text box in the client app, and then call the service with the `Item` command to get the description of the item.</span></span> <span data-ttu-id="c5fc6-212">Anschließend wird der Aufruf mit dem Befehl `Price` ausgeführt, um den Preis des Artikels zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-212">Then, we make the call with the `Price` command to get the item's price.</span></span> <span data-ttu-id="c5fc6-213">Der Text der Schaltfläche wird auf das Ergebnis festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-213">The button text is set to the result.</span></span>

    <span data-ttu-id="c5fc6-214">Da [AppServiceResponseStatus](https://msdn.microsoft.com/library/windows/apps/dn921724) nur angibt, ob das Betriebssystem den Aufruf mit dem App-Dienst verknüpfen konnte, muss der Schlüssel `Status` im [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) geprüft werden, den wir vom App-Dienst erhalten, um sicherzustellen, dass die Anforderung erfüllt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-214">Because [AppServiceResponseStatus](https://msdn.microsoft.com/library/windows/apps/dn921724) only indicates whether the operating system was able to connect the call to the app service, we check the `Status` key in the [ValueSet](https://msdn.microsoft.com/library/windows/apps/dn636131) we receive from the app service to ensure that it was able to fulfill the request.</span></span>

6. <span data-ttu-id="c5fc6-215">Das Projekt **"ClientApp"** als Startprojekt festlegen (mit der rechten Maustaste im **Projektmappen-Explorer**- > **als Startprojekt festlegen**), und führen Sie die Lösung.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-215">Set the **ClientApp** project to be the startup project (right-click it in the **Solution Explorer** > **Set as StartUp Project**) and run the solution.</span></span> <span data-ttu-id="c5fc6-216">Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-216">Enter the number 1 into the text box and click the button.</span></span> <span data-ttu-id="c5fc6-217">Der Dienst sollte „Stuhl: Preis = 88,99“ zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-217">You should get "Chair : Price = 88.99" back from the service.</span></span>

    ![Beispiel-App, die Stuhlpreis = 88,99 anzeigt](images/appserviceclientapp.png)

<span data-ttu-id="c5fc6-219">Wenn der Aufruf des app-Diensts ein Fehler auftritt, überprüfen Sie in das Projekt **"ClientApp"** Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-219">If the app service call fails, check the following in the **ClientApp** project:</span></span>

1.  <span data-ttu-id="c5fc6-220">Stellen Sie sicher, dass der paketfamilienname, der der bestandsdienstverbindung zugewiesen den paketfamiliennamen der app **"AppServiceProvider"** übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-220">Verify that the package family name assigned to the inventory service connection matches the package family name of the **AppServiceProvider** app.</span></span> <span data-ttu-id="c5fc6-221">Finden Sie unter der Zeile in **Button\_Click** mit `this.inventoryService.PackageFamilyName = "...";`.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-221">See the line in **button\_Click** with `this.inventoryService.PackageFamilyName = "...";`.</span></span>
2.  <span data-ttu-id="c5fc6-222">In **Button\_Click**stellen Sie sicher, dass der Name der app-Dienst, der der bestandsdienstverbindung zugewiesen ist den Namen des app-Diensts in der **"AppServiceProvider"** **Datei "Package.appxmanifest** " entspricht.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-222">In **button\_Click**, verify that the app service name that is assigned to the inventory service connection matches the app service name in the **AppServiceProvider**'s **Package.appxmanifest** file.</span></span> <span data-ttu-id="c5fc6-223">Weitere Informationen finden Sie unter `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-223">See: `this.inventoryService.AppServiceName = "com.microsoft.inventory";`.</span></span>
3.  <span data-ttu-id="c5fc6-224">Stellen Sie sicher, dass die app **"AppServiceProvider"** bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-224">Ensure that the **AppServiceProvider** app has been deployed.</span></span> <span data-ttu-id="c5fc6-225">(Im **Projektmappen-Explorer**mit der rechten Maustaste der Projektmappe, und wählen Sie die **Projektmappe bereitstellen**).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-225">(In the **Solution Explorer**, right-click the solution and choose **Deploy Solution**).</span></span>

## <a name="debug-the-app-service"></a><span data-ttu-id="c5fc6-226">Debuggen des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="c5fc6-226">Debug the app service</span></span>

1.  <span data-ttu-id="c5fc6-227">Stellen Sie vor dem Debuggen sicher, dass die Projektmappe bereitgestellt wurde. Die App Dienstanbieter-App muss bereitgestellt werden, bevor der Dienst aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-227">Ensure that the solution is deployed before debugging because the app service provider app must be deployed before the service can be called.</span></span> <span data-ttu-id="c5fc6-228">(Klicken Sie in Visual Studio auf **Erstellen &gt; Projektmappe bereitstellen**.)</span><span class="sxs-lookup"><span data-stu-id="c5fc6-228">(In Visual Studio, **Build &gt; Deploy Solution**).</span></span>
2.  <span data-ttu-id="c5fc6-229">Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste in des Projekts **"AppServiceProvider"** , und wählen Sie **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-229">In the **Solution Explorer**, right-click the **AppServiceProvider** project and choose **Properties**.</span></span> <span data-ttu-id="c5fc6-230">Ändern Sie auf der Registerkarte **Debuggen** die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-230">From the **Debug** tab, change the **Start action** to **Do not launch, but debug my code when it starts**.</span></span> <span data-ttu-id="c5fc6-231">(Hinweis: wenn Sie nicht C++ zum Implementieren Ihres App-Dienstanbieters verwenden, müssen Sie auf der Registerkarte **Debuggen** die Option **Anwendung starten** auf **Nein** ändern).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-231">(Note, if you were using C++ to implement your app service provider, from the **Debugging** tab you would change **Launch Application** to **No**).</span></span>
3.  <span data-ttu-id="c5fc6-232">Legen Sie im Projekt **"myappservice"** in der Datei **Inventory.cs** einen Haltepunkt im **OnRequestReceived**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-232">In the **MyAppService** project, in the **Inventory.cs** file, set a breakpoint in **OnRequestReceived**.</span></span>
4.  <span data-ttu-id="c5fc6-233">Legen Sie das Projekt **"AppServiceProvider"** Startprojekt aus, und drücken **F5**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-233">Set the **AppServiceProvider** project to be the startup project and press **F5**.</span></span>
5.  <span data-ttu-id="c5fc6-234">Starten Sie **"ClientApp"** über das Startmenü (nicht über Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-234">Start **ClientApp** from the Start menu (not from Visual Studio).</span></span>
6.  <span data-ttu-id="c5fc6-235">Geben Sie 1 in das Textfeld ein, und klicken Sie auf die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-235">Enter the number 1 into the text box and press the button.</span></span> <span data-ttu-id="c5fc6-236">Der Debugger stoppt im App-Dienstaufruf am Haltepunkt in Ihrem App-Dienst.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-236">The debugger will stop in the app service call on the breakpoint in your app service.</span></span>

## <a name="debug-the-client"></a><span data-ttu-id="c5fc6-237">Debuggen des Clients</span><span class="sxs-lookup"><span data-stu-id="c5fc6-237">Debug the client</span></span>

1.  <span data-ttu-id="c5fc6-238">Folgen Sie zum Debuggen des Clients, der den App-Dienst aufruft, den Anweisungen im vorherigen Schritt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-238">Follow the instructions in the preceding step to debug the client that calls the app service.</span></span>
2.  <span data-ttu-id="c5fc6-239">Starten Sie **"ClientApp"** über das Startmenü.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-239">Launch **ClientApp** from the Start menu.</span></span>
3.  <span data-ttu-id="c5fc6-240">Fügen Sie den Debugger an den Prozess **ClientApp.exe** (nicht der Prozess " **ApplicationFrameHost.exe** ").</span><span class="sxs-lookup"><span data-stu-id="c5fc6-240">Attach the debugger to the **ClientApp.exe** process (not the **ApplicationFrameHost.exe** process).</span></span> <span data-ttu-id="c5fc6-241">(Klicken Sie in Visual Studio auf **Debuggen &gt; An den Prozess anhängen**.)</span><span class="sxs-lookup"><span data-stu-id="c5fc6-241">(In Visual Studio, choose **Debug &gt; Attach to Process...**.)</span></span>
4.  <span data-ttu-id="c5fc6-242">Legen Sie im Projekt **"ClientApp"** einen Haltepunkt in **Button\_Click**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-242">In the **ClientApp** project, set a breakpoint in **button\_Click**.</span></span>
5.  <span data-ttu-id="c5fc6-243">Die Haltepunkte in der Client und der app-Dienst werden jetzt erreicht werden, wenn Sie geben Sie 1 in das Textfeld von **"ClientApp"** , und klicken Sie auf die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-243">The breakpoints in both the client and the app service will now be hit when you enter the number 1 into the text box of **ClientApp** and click the button.</span></span>

## <a name="general-app-service-troubleshooting"></a><span data-ttu-id="c5fc6-244">Allgemeine Problembehandlung von App-Diensten</span><span class="sxs-lookup"><span data-stu-id="c5fc6-244">General app service troubleshooting</span></span>

<span data-ttu-id="c5fc6-245">Wenn nach einem app-Dienst herstellen einer Verbindung mit den Status **AppUnavailable** auftritt, überprüfen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-245">If you encounter an **AppUnavailable** status after trying to connect to an app service, check the following:</span></span>

- <span data-ttu-id="c5fc6-246">Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-246">Ensure that the app service provider project and app service project are deployed.</span></span> <span data-ttu-id="c5fc6-247">Beide müssen bereitgestellt werden, bevor der Client ausgeführt werden kann, da andernfalls der Client keine Verbindung zulassen kann.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-247">Both need to be deployed before running the client because otherwise the client won't have anything to connect to.</span></span> <span data-ttu-id="c5fc6-248">Sie können von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-248">You can deploy from Visual Studio by using **Build** > **Deploy Solution**.</span></span>
- <span data-ttu-id="c5fc6-249">Klicken Sie im **Projektmappen-Explorer**sicher, dass Ihr app-dienstanbieterprojekt einen Projekt-zu-Projekt-Verweis auf das Projekt hat, das den app-Dienst implementiert.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-249">In the **Solution Explorer**, ensure that your app service provider project has a project-to-project reference to the project that implements the app service.</span></span>
- <span data-ttu-id="c5fc6-250">Überprüfen Sie, ob die `<Extensions>` Eintrag, und die untergeordneten Elemente der Datei **"Package.appxmanifest"** in der app-dienstanbieterprojekts wie oben [Hinzufügen einer app-diensterweiterung zu "Package.appxmanifest"](#appxmanifest)angegeben hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-250">Verify that the `<Extensions>` entry, and its child elements, have been added to the **Package.appxmanifest** file belonging to the app service provider project as specified above in [Add an app service extension to Package.appxmanifest](#appxmanifest).</span></span>
- <span data-ttu-id="c5fc6-251">Stellen Sie sicher, dass die [AppServiceConnection.AppServiceName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.appservicename) -Zeichenfolge in Ihrem Client, der die app-Dienstanbieter aufruft entspricht der `<uap3:AppService Name="..." />` in der app-dienstanbieterprojekt der **Datei "Package.appxmanifest** " angegeben.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-251">Ensure that the [AppServiceConnection.AppServiceName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.appservicename) string in your client that calls the app service provider matches the `<uap3:AppService Name="..." />` specified in the app service provider project's **Package.appxmanifest** file.</span></span>
- <span data-ttu-id="c5fc6-252">Stellen Sie sicher, dass die [AppServiceConnection.PackageFamilyName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.packagefamilyname) der paketfamilienname, der die app-dienstanbieterkomponente wie oben angegeben [Hinzufügen eine app-diensterweiterung zu "Package.appxmanifest"](#appxmanifest) entspricht</span><span class="sxs-lookup"><span data-stu-id="c5fc6-252">Ensure that the [AppServiceConnection.PackageFamilyName](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appservice.appserviceconnection.packagefamilyname) matches the package family name of the app service provider component as specified above in [Add an app service extension to Package.appxmanifest](#appxmanifest)</span></span>
- <span data-ttu-id="c5fc6-253">Für Out-of-Proc app-Diensten wie in diesem Beispiel wird, überprüfen Sie, dass die `EntryPoint` Angabe in der `<uap:Extension ...>` Element der Ihr app-dienstanbieterprojekt der **Datei "Package.appxmanifest** " entspricht den Namespace und Klassennamen der öffentliche Klasse, die implementiert [IBackgroundTask](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.ibackgroundtask) in Ihrem app-Dienst-Projekt.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-253">For out-of-proc app services such as the one in this example, validate that the `EntryPoint` specified in the `<uap:Extension ...>` element of your app service provider project's **Package.appxmanifest** file matches the namespace and class name of the public class that implements [IBackgroundTask](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.ibackgroundtask) in your app service project.</span></span>

### <a name="troubleshoot-debugging"></a><span data-ttu-id="c5fc6-254">Problembehandlung beim Debuggen</span><span class="sxs-lookup"><span data-stu-id="c5fc6-254">Troubleshoot debugging</span></span>

<span data-ttu-id="c5fc6-255">Wenn der Debugger nicht an Haltepunkten in Ihrem App-Dienstanbieter oder App-Dienst-Projekte beendet wird, überprüfen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-255">If the debugger does not stop at breakpoints in your app service provider or app service projects, check the following:</span></span>

- <span data-ttu-id="c5fc6-256">Stellen Sie sicher, dass das App-Dienstanbieterprojekt und das App-Dienstprojekt bereitgestellt sind.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-256">Ensure that the app service provider project and app service project are deployed.</span></span> <span data-ttu-id="c5fc6-257">Beide müssen bereitgestellt werden, bevor der Client ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-257">Both need to be deployed before running the client.</span></span> <span data-ttu-id="c5fc6-258">Sie können diese von Visual Studio aus mithilfe von **Erstellen** > **Projektmappe bereitstellen** bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-258">You can deploy them from Visual Studio by using **Build** > **Deploy Solution**.</span></span>
- <span data-ttu-id="c5fc6-259">Stellen Sie sicher, dass das Projekt, das Sie debuggen möchten als Startprojekt festgelegt ist und dass die debugging-Eigenschaften für das Projekt festgelegt sind, um das Projekt nicht ausgeführt, wenn **F5** gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-259">Ensure that the project you want to debug is set as the startup project and that the debugging properties for that project are set to not run the project when **F5** is pressed.</span></span> <span data-ttu-id="c5fc6-260">Klicken Sie mit der rechten Maustaste auf **Eigenschaften** und dann **Debug** (oder **Debugging** in C++).</span><span class="sxs-lookup"><span data-stu-id="c5fc6-260">Right-click the project, then click **Properties**, and then **Debug** (or **Debugging** in C++).</span></span> <span data-ttu-id="c5fc6-261">In C#, ändern Sie die **Startaktion** in **Eigenen Code zunächst nicht starten, sondern debuggen**.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-261">In C#, change the **Start action** to **Do not launch, but debug my code when it starts**.</span></span> <span data-ttu-id="c5fc6-262">Legen Sie in C++ **Anwendung starten** auf **Nein** fest.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-262">In C++, set **Launch Application** to **No**.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5fc6-263">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="c5fc6-263">Remarks</span></span>

<span data-ttu-id="c5fc6-264">Dieses Beispiel ist eine Einführung in das Erstellen eines App-Diensts, das als Hintergrundaufgabe ausgeführt wird, und Aufrufen des Diensts in einer anderen App.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-264">This example provides an introduction to creating an app service that runs as a background task and calling it from another app.</span></span> <span data-ttu-id="c5fc6-265">Die wichtigsten Punkte zu beachten sind:</span><span class="sxs-lookup"><span data-stu-id="c5fc6-265">The key things to note are:</span></span>

* <span data-ttu-id="c5fc6-266">Erstellen Sie eine Hintergrundaufgabe zum Hosten des app-Diensts.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-266">Create a background task to host the app service.</span></span>
* <span data-ttu-id="c5fc6-267">Hinzufügen der `windows.appService` Erweiterung für die **Datei "Package.appxmanifest** " des app-Dienstanbieters.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-267">Add the `windows.appService` extension to the app service provider's **Package.appxmanifest** file.</span></span>
* <span data-ttu-id="c5fc6-268">Erhalten Sie den paketfamiliennamen des app-Dienstanbieters, damit wir von der Client-app herstellen können.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-268">Obtain the package family name of the app service provider so that we can connect to it from the client app.</span></span>
* <span data-ttu-id="c5fc6-269">Fügen Sie einen Projekt-zu-Projekt-Verweis von der app-dienstanbieterprojekt auf das app-Dienst-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-269">Add a project-to-project reference from the app service provider project to the app service project.</span></span>
* <span data-ttu-id="c5fc6-270">Verwenden Sie [Windows.ApplicationModel.AppService.AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704) zum Aufrufen des Diensts.</span><span class="sxs-lookup"><span data-stu-id="c5fc6-270">Use [Windows.ApplicationModel.AppService.AppServiceConnection](https://msdn.microsoft.com/library/windows/apps/dn921704) to call the service.</span></span>

## <a name="full-code-for-myappservice"></a><span data-ttu-id="c5fc6-271">Vollständiger Code für „MyAppService”</span><span class="sxs-lookup"><span data-stu-id="c5fc6-271">Full code for MyAppService</span></span>

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
            // Get a deferral so that the service isn't terminated.
            this.backgroundTaskDeferral = taskInstance.GetDeferral();

            // Associate a cancellation handler with the background task.
            taskInstance.Canceled += OnTaskCanceled;

            // Retrieve the app service connection and set up a listener for incoming app service requests.
            var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
            appServiceconnection = details.AppServiceConnection;
            appServiceconnection.RequestReceived += OnRequestReceived;
        }

        private async void OnRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            // Get a deferral because we use an awaitable API below to respond to the message
            // and we don't want this call to get canceled while we are waiting.
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

            // Return the data to the caller.
            await args.Request.SendResponseAsync(returnData);

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

## <a name="related-topics"></a><span data-ttu-id="c5fc6-272">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c5fc6-272">Related topics</span></span>

* [<span data-ttu-id="c5fc6-273">Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App</span><span class="sxs-lookup"><span data-stu-id="c5fc6-273">Convert an app service to run in the same process as its host app</span></span>](convert-app-service-in-process.md)
* [<span data-ttu-id="c5fc6-274">Unterstützen Ihrer App mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="c5fc6-274">Support your app with background tasks</span></span>](support-your-app-with-background-tasks.md)
* [<span data-ttu-id="c5fc6-275">Codebeispiel für App-Dienst (C#, C++ und VB)</span><span class="sxs-lookup"><span data-stu-id="c5fc6-275">App service code sample (C#, C++, and VB)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AppServices)
