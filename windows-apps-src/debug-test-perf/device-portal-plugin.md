---
author: PatrickFarley
ms.assetid: 82ab5fc9-3a7f-4d9e-9882-077ccfdd0ec9
title: Schreiben eines benutzerdefinierten Plug-Ins für das Device Portal
description: Hier erfahren Sie, wie Sie eine UWP-App schreiben, die mit dem Windows Device Portal eine Webseite hostet und Diagnoseinformationen bereitstellt.
ms.author: pafarley
ms.date: 03/24/2017
ms.topic: article
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: cceceae4b6b9bf4cecd3c3bee36344f4e5a1eed1
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5682576"
---
# <a name="write-a-custom-plugin-for-device-portal"></a><span data-ttu-id="54d09-104">Schreiben eines benutzerdefinierten Plug-Ins für das Device Portal</span><span class="sxs-lookup"><span data-stu-id="54d09-104">Write a custom plugin for Device Portal</span></span>

<span data-ttu-id="54d09-105">Hier erfahren Sie, wie Sie eine UWP-App schreiben, die mit dem Windows Device Portal eine Webseite hostet und Diagnoseinformationen bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="54d09-105">Learn how to write a UWP app that uses th Windows Device Portal to host a web page and provide diagnostic information.</span></span>

<span data-ttu-id="54d09-106">Ab dem Creators Update können Sie im Device Portal die Diagnoseschnittstellen Ihrer App hosten.</span><span class="sxs-lookup"><span data-stu-id="54d09-106">Starting with the Creators Update, you can use Device Portal to host your app's diagnostic interfaces.</span></span> <span data-ttu-id="54d09-107">Dieser Artikel beschreibt die drei Teile, die zum Erstellen eines DevicePortalProvider für Ihre App erforderlich sind – die Appxmanifest-Änderungen, das Einrichten der App-Verbindung zum Device Portal-Dienst und das Behandeln einer eingehenden Anforderung.</span><span class="sxs-lookup"><span data-stu-id="54d09-107">This article covers the three pieces needed to create a DevicePortalProvider for your app – the appxmanifest changes, setting up your app’s connection to the Device Portal service, and handling an incoming request.</span></span> <span data-ttu-id="54d09-108">Eine Beispiel-App wird auch bereitgestellt, um den Einstieg zu erleichtern (in Kürze verfügbar).</span><span class="sxs-lookup"><span data-stu-id="54d09-108">A sample app is also provided to get started (Coming soon) .</span></span> 

## <a name="create-a-new-uwp-app-project"></a><span data-ttu-id="54d09-109">Erstellen eines neuen UWP-App-Projekts</span><span class="sxs-lookup"><span data-stu-id="54d09-109">Create a new UWP app project</span></span>
<span data-ttu-id="54d09-110">In dieser Anleitung erstellen wir der Einfachheit halber alles in einer Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="54d09-110">In this guide, we'll create everything in one solution for simplicity.</span></span>

<span data-ttu-id="54d09-111">Erstellen Sie in Microsoft Visual Studio 2017 ein neues UWP-App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="54d09-111">In Microsoft Visual Studio 2017, create a new UWP app project.</span></span> <span data-ttu-id="54d09-112">Wechseln Sie zu „Datei“ > „Neues Projekt“, und wählen Sie „Vorlagen“ > „Visual C#“ > „Windows Universal“ > „Leere App (Windows Universal)“.</span><span class="sxs-lookup"><span data-stu-id="54d09-112">Go to File > New Project and select Templates > Visual C# > Windows Universal > Blank app (Windows Universal).</span></span> <span data-ttu-id="54d09-113">Nennen Sie die App „DevicePortalProvider”.</span><span class="sxs-lookup"><span data-stu-id="54d09-113">Name it "DevicePortalProvider".</span></span> <span data-ttu-id="54d09-114">Diese App soll den App-Dienst enthalten.</span><span class="sxs-lookup"><span data-stu-id="54d09-114">This will be the app that contains the app service.</span></span> <span data-ttu-id="54d09-115">Stellen Sie sicher, dass Sie die Unterstützung für das Creators Update-SDK auswählen.</span><span class="sxs-lookup"><span data-stu-id="54d09-115">Ensure that you choose the Creators Update SDK to support.</span></span>  <span data-ttu-id="54d09-116">Möglicherweise müssen Sie Visual Studio aktualisieren oder das neue SDK installieren – Details dazu finden Sie [hier](https://blogs.windows.com/buildingapps/2017/04/05/updating-tooling-windows-10-creators-update/).</span><span class="sxs-lookup"><span data-stu-id="54d09-116">You may need to update Visual Studio or install the new SDK - see [here](https://blogs.windows.com/buildingapps/2017/04/05/updating-tooling-windows-10-creators-update/) for details.</span></span> 

## <a name="add-the-deviceportalprovider-extension-to-your-packageappxmanifest-file"></a><span data-ttu-id="54d09-117">Hinzufügen der devicePortalProvider-Erweiterung zur package.appxmanifest-Datei</span><span class="sxs-lookup"><span data-stu-id="54d09-117">Add the devicePortalProvider extension to your package.appxmanifest file</span></span>
<span data-ttu-id="54d09-118">Sie müssen der *package.appxmanifest*-Datei Code hinzufügen, damit Sie Ihre App als Device Portal-Plug-In nutzen können.</span><span class="sxs-lookup"><span data-stu-id="54d09-118">You will need to add some code to your *package.appxmanifest* file in order to make your app functional as a Device Portal plugin.</span></span> <span data-ttu-id="54d09-119">Fügen Sie zunächst die folgenden Namespace-Definitionen am Beginn der Datei ein.</span><span class="sxs-lookup"><span data-stu-id="54d09-119">First, add the following namespace definitions at the top of the file.</span></span> <span data-ttu-id="54d09-120">Fügen Sie auch das `IgnorableNamespaces`-Attribut hinzu.</span><span class="sxs-lookup"><span data-stu-id="54d09-120">Also add them to the `IgnorableNamespaces` attribute.</span></span>

```xml
<Package
    ... 
    xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
    xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
    IgnorableNamespaces="uap mp rescap uap4">
    ...
```

<span data-ttu-id="54d09-121">Um zu deklarieren, dass die App ein Device Portal-Anbieter ist, müssen Sie einen App-Dienst und eine neue Device Portal-Anbietererweiterung, die den Dienst verwendet, hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="54d09-121">In order to declare that your app is a Device Portal Provider, you need to create an app service and a new Device Portal Provider extension that uses it.</span></span> <span data-ttu-id="54d09-122">Fügen Sie dem `Extensions`-Element unter `Application` die Erweiterungen windows.appService und windows.devicePortalProvider hinzu.</span><span class="sxs-lookup"><span data-stu-id="54d09-122">Add both the windows.appService extension and the windows.devicePortalProvider extension in the `Extensions` element under `Application`.</span></span> <span data-ttu-id="54d09-123">Stellen Sie sicher, dass die `AppServiceName`-Attribute in allen Erweiterungen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="54d09-123">Make sure the `AppServiceName` attributes match in each extension.</span></span> <span data-ttu-id="54d09-124">Damit wird dem Device Portal-Dienst mitgeteilt, dass dieser App-Dienst zur Behandlung von Anforderungen für den Ereignishandler-Namespace gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="54d09-124">This indicates to the Device Portal service that this app service can be launched to handle requests on the handler namespace.</span></span> 

```xml
...   
<Application 
    Id="App" 
    Executable="$targetnametoken$.exe"
    EntryPoint="DevicePortalProvider.App">
    ...
    <Extensions>
        <uap:Extension Category="windows.appService" EntryPoint="MySampleProvider.SampleProvider">
            <uap:AppService Name="com.sampleProvider.wdp" />
        </uap:Extension>
        <uap4:Extension Category="windows.devicePortalProvider">
            <uap4:DevicePortalProvider 
                DisplayName="My Device Portal Provider Sample App" 
                AppServiceName="com.sampleProvider.wdp" 
                HandlerRoute="/MyNamespace/api/" />
        </uap4:Extension>
    </Extensions>
</Application>
...
```

<span data-ttu-id="54d09-125">Das `HandlerRoute`-Attribut verweist auf den REST-Namespace, der von Ihrer App in Anspruch genommen wird.</span><span class="sxs-lookup"><span data-stu-id="54d09-125">The `HandlerRoute` attribute references the REST namespace claimed by your app.</span></span> <span data-ttu-id="54d09-126">Alle HTTP-Anforderungen für diesen Namespace (implizit gefolgt von einem Platzhalter), die der Device Portal-Dienst empfängt, werden zur Behandlung an Ihre App gesendet.</span><span class="sxs-lookup"><span data-stu-id="54d09-126">Any HTTP requests on that namespace (implicitly followed by a wildcard) received by the Device Portal service will be sent to your app to be handled.</span></span> <span data-ttu-id="54d09-127">In diesem Fall wird jede erfolgreich authentifizierte HTTP-Anforderung für `<ip_address>/MyNamespace/api/*` an Ihre App gesendet.</span><span class="sxs-lookup"><span data-stu-id="54d09-127">In this case, any successfully authenticated HTTP request to `<ip_address>/MyNamespace/api/*` will be sent to your app.</span></span> <span data-ttu-id="54d09-128">Konflikte zwischen Handler-Routen werden anhand einer Überprüfung nach dem Prinzip „die längste gewinnt“ aufgelöst: die Route mit der größten Übereinstimmung mit den Anforderungen wird ausgewählt. Eine Anforderung für „/MyNamespace/api/foo“ wird also z.B. dem Anbieter „/MyNamespace/api“ anstatt „/MyNamespace“ zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="54d09-128">Conflicts between handler routes are settled via a "longest wins" check: whichever route matches more of the requests is selected, meaning that a request to "/MyNamespace/api/foo" will match against a provider with "/MyNamespace/api" rather than one with "/MyNamespace".</span></span>  

<span data-ttu-id="54d09-129">Damit dies ausgeführt werden kann, sind zwei neue Funktionen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54d09-129">Two new capabilities are required for this functionality.</span></span> <span data-ttu-id="54d09-130">Diese Funktionen müssen ebenfalls der *package.appxmanifest*-Datei hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="54d09-130">they must also be added to your *package.appxmanifest* file.</span></span>

```xml
...
<Capabilities>
    ...
    <Capability Name="privateNetworkClientServer" />
    <rescap:Capability Name="devicePortalProvider" />
</Capabilities>
...
```

> [!NOTE]
> <span data-ttu-id="54d09-131">Die Funktion „devicePortalProvider” ist eingeschränkt („rescap”), das heißt, Sie müssen zuerst die Zustimmung vom Store erhalten, bevor Sie Ihre App dort veröffentlichen können.</span><span class="sxs-lookup"><span data-stu-id="54d09-131">The capability "devicePortalProvider" is restricted ("rescap"), which means you must get prior approval from the Store before your app can be published there.</span></span> <span data-ttu-id="54d09-132">Dies hindert Sie jedoch nicht daran, Ihre App lokal per Querladen zu testen.</span><span class="sxs-lookup"><span data-stu-id="54d09-132">However, this does not prevent you from testing your app locally through sideloading.</span></span> <span data-ttu-id="54d09-133">Weitere Informationen zu eingeschränkten Funktionen finden Sie unter [Deklarationen von App-Funktionen](https://msdn.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations#special-and-restricted-capabilities).</span><span class="sxs-lookup"><span data-stu-id="54d09-133">For more information about restricted capabilities, see [App capability declarations](https://msdn.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations#special-and-restricted-capabilities).</span></span>

## <a name="set-up-your-background-task-and-winrt-component"></a><span data-ttu-id="54d09-134">Einrichten der Hintergrundaufgabe und der WinRT-Komponente</span><span class="sxs-lookup"><span data-stu-id="54d09-134">Set up your background task and WinRT Component</span></span>
<span data-ttu-id="54d09-135">Um die Device Portal-Verbindung einzurichten, muss Ihre App eine App-Dienstverbindung aus dem Device Portal-Dienst mit der in Ihrer App ausgeführten Instanz des Device Portal herstellen.</span><span class="sxs-lookup"><span data-stu-id="54d09-135">In order to set up the Device Portal connection, your app must hook up an app service connection from the Device Portal service with the instance of Device Portal running within your app.</span></span> <span data-ttu-id="54d09-136">Fügen Sie zu diesem Zweck Ihrer Anwendung eine neue WinRT-Komponente mit einer Klasse hinzu, die [**IBackgroundTask**](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.background.ibackgroundtask) implementiert.</span><span class="sxs-lookup"><span data-stu-id="54d09-136">To do this, add a new WinRT Component to your application with a class that implements [**IBackgroundTask**](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.background.ibackgroundtask).</span></span>

```csharp
namespace MySampleProvider {
    // Implementing a DevicePortalConnection in a background task
    public sealed class SampleProvider : IBackgroundTask {
        //...
    }
```

<span data-ttu-id="54d09-137">Stellen Sie sicher, dass der Name mit dem Namespace und dem Klassennamen übereinstimmt, die von AppService EntryPoint („MySampleProvider.SampleProvider”) eingerichtet wurden.</span><span class="sxs-lookup"><span data-stu-id="54d09-137">Make sure that its name matches the namespace and class name set up by the AppService EntryPoint ("MySampleProvider.SampleProvider").</span></span> <span data-ttu-id="54d09-138">Wenn Sie die erste Anforderung an Ihren Device Portal-Anbieter richten, speichert das Device Portal die Anforderung, startet die Hintergrundaufgabe Ihrer App, ruft die Methode **Run** auf und übergibt eine [**IBackgroundTaskInstance**](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.background.ibackgroundtaskinstance).</span><span class="sxs-lookup"><span data-stu-id="54d09-138">When you make your first request to your Device Portal provider, Device Portal will stash the request, launch your app's background task, call its **Run** method, and pass in an [**IBackgroundTaskInstance**](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.background.ibackgroundtaskinstance).</span></span> <span data-ttu-id="54d09-139">Damit richtet Ihre App dann eine [**DevicePortalConnection**](https://docs.microsoft.com/en-us/uwp/api/windows.system.diagnostics.deviceportal.deviceportalconnection)-Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="54d09-139">Your app then uses it to set up a [**DevicePortalConnection**](https://docs.microsoft.com/en-us/uwp/api/windows.system.diagnostics.deviceportal.deviceportalconnection) instance.</span></span>

```csharp
// Implement background task handler with a DevicePortalConnection
public void Run(IBackgroundTaskInstance taskInstance) {
    // Take a deferral to allow the background task to continue executing 
    this.taskDeferral = taskInstance.GetDeferral();
    taskInstance.Canceled += TaskInstance_Canceled;

    // Create a DevicePortal client from an AppServiceConnection 
    var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
    var appServiceConnection = details.AppServiceConnection;
    this.devicePortalConnection = DevicePortalConnection.GetForAppServiceConnection(appServiceConnection);

    // Add Closed, RequestReceived handlers 
    devicePortalConnection.Closed += DevicePortalConnection_Closed;
    devicePortalConnection.RequestReceived += DevicePortalConnection_RequestReceived;
}
```

<span data-ttu-id="54d09-140">Es gibt zwei Ereignisse, die von der App behandelt werden müssen, um die Anforderungsbehandlungsschleife abzuschließen: **Closed** bei jedem Beenden des Device Portal-Diensts und [**RequestRecieved**](https://docs.microsoft.com/en-us/uwp/api/windows.system.diagnostics.deviceportal.deviceportalconnectionrequestreceivedeventargs), das eingehende HTTP-Anforderungen übernimmt und die Hauptfunktionen des Device Portal-Anbieters bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="54d09-140">There are two events that must be handled by the app to complete the request handling loop: **Closed**, for whenever the Device Portal service shuts down, and [**RequestRecieved**](https://docs.microsoft.com/en-us/uwp/api/windows.system.diagnostics.deviceportal.deviceportalconnectionrequestreceivedeventargs), which surfaces incoming HTTP requests and provides the main functionality of the Device Portal provider.</span></span> 

## <a name="handle-the-requestreceived-event"></a><span data-ttu-id="54d09-141">Behandeln des „RequestReceived“-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="54d09-141">Handle the RequestReceived event</span></span>
<span data-ttu-id="54d09-142">Das **RequestReceived**-Ereignis wird einmal für jede HTTP-Anforderung ausgelöst, die für die angegebene Handler-Route Ihres Plug-Ins erfolgt.</span><span class="sxs-lookup"><span data-stu-id="54d09-142">The **RequestReceived** event will be raised once for every HTTP request that is made on your plugin's specified Handler Route.</span></span> <span data-ttu-id="54d09-143">Die Anforderungsbehandlungsschleife für Device Portal-Anbieter ähnelt der in NodeJS Express: die Anforderungs- und Antwortobjekte werden zusammen mit dem Ereignis bereitgestellt, und der Handler reagiert, indem er das Antwortobjekt ausfüllt.</span><span class="sxs-lookup"><span data-stu-id="54d09-143">The request handling loop for Device Portal providers is similar to that in NodeJS Express: the request and response objects are provided together with the event, and the handler responds by filling in the response object.</span></span> <span data-ttu-id="54d09-144">In Device Portal-Anbietern verwenden das **RequestReceived**-Ereignis und seine Handler [**Windows.Web.Http.HttpRequestMessage**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httprequestmessage)- und [**HttpResponseMessage**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httpresponsemessage)-Objekte.</span><span class="sxs-lookup"><span data-stu-id="54d09-144">In Device Portal providers, the **RequestReceived** event and its handlers use [**Windows.Web.Http.HttpRequestMessage**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httprequestmessage) and [**HttpResponseMessage**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httpresponsemessage) objects.</span></span>   

```csharp
// Sample RequestReceived echo handler: respond with an HTML page including the query and some additional process information. 
private void DevicePortalConnection_RequestReceived(DevicePortalConnection sender, DevicePortalConnectionRequestReceivedEventArgs args)
{
    var req = args.RequestMessage;
    var res = args.ResponseMessage;

    if (req.RequestUri.AbsolutePath.EndsWith("/echo"))
    {
        // construct an html response message
        string con = "<h1>" + req.RequestUri.AbsoluteUri + "</h1><br/>";
        var proc = Windows.System.Diagnostics.ProcessDiagnosticInfo.GetForCurrentProcess();
        con += String.Format("This process is consuming {0} bytes (Working Set)<br/>", proc.MemoryUsage.GetReport().WorkingSetSizeInBytes);
        con += String.Format("The process PID is {0}<br/>", proc.ProcessId);
        con += String.Format("The executable filename is {0}", proc.ExecutableFileName);
        res.Content = new HttpStringContent(con);
        res.Content.Headers.ContentType = new HttpMediaTypeHeaderValue("text/html");
        res.StatusCode = HttpStatusCode.Ok;            
    }
    //...
}
```

<span data-ttu-id="54d09-145">In diesem Beispiel für einen Anforderungshandler rufen wir zunächst die Anforderungs- und Antwortobjekte aus dem *Args*-Parameter ab, erstellen dann eine Zeichenfolge mit der Anforderungs-URL und einige weitere HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="54d09-145">In this sample request handler, we first pull the request and response objects out of the *args* parameter, then create a string with the request URL and some additional HTML formatting.</span></span> <span data-ttu-id="54d09-146">Dies wird in das Antwortobjekt als [**HttpStringContent**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httpstringcontent)-Instanz eingefügt.</span><span class="sxs-lookup"><span data-stu-id="54d09-146">This is added into the Response object as an [**HttpStringContent**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.httpstringcontent) instance.</span></span> <span data-ttu-id="54d09-147">Andere [**IHttpContent**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.ihttpcontent)-Klassen, z.B. diejenigen für „String” und „Buffer”, sind ebenfalls zulässig.</span><span class="sxs-lookup"><span data-stu-id="54d09-147">Other [**IHttpContent**](https://docs.microsoft.com/en-us/uwp/api/windows.web.http.ihttpcontent) classes, such as those for "String" and "Buffer," are also allowed.</span></span>

<span data-ttu-id="54d09-148">Die Antwort wird dann als HTTP-Antwort festgelegt und der Statuscode 200 (OK) zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="54d09-148">The response is then set as an HTTP response and given a 200 (OK) status code.</span></span> <span data-ttu-id="54d09-149">In dem Browser, der den ursprünglichen Aufruf vorgenommen hat, sollte dies wie erwartet gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="54d09-149">It should render as expected in the browser that made the original call.</span></span> <span data-ttu-id="54d09-150">Wenn der **RequestReceived**-Ereignishandler zurückkehrt, wird die Antwortnachricht automatisch an den Benutzer-Agent zurückgegeben: es ist keine zusätzliche „send“-Methode erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54d09-150">Note that when the **RequestReceived** event handler returns, the response message is automatically returned to the user agent: no additional "send" method is needed.</span></span>

![Antwortnachricht des Device Portal](images/device-portal/plugin-response-message.png)

## <a name="providing-static-content"></a><span data-ttu-id="54d09-152">Bereitstellen von statischem Inhalt</span><span class="sxs-lookup"><span data-stu-id="54d09-152">Providing static content</span></span>
<span data-ttu-id="54d09-153">Statischer Inhalt kann direkt aus einem Ordner in Ihrem Paket bereitgestellt werden. Dadurch können Sie Ihrem Anbieter sehr einfach eine Benutzeroberfläche hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="54d09-153">Static content can be served directly from a folder within your package, making it very easy to add a UI to your provider.</span></span>  <span data-ttu-id="54d09-154">Die einfachste Möglichkeit zur Bereitstellung von statischem Inhalt ist, einen Inhaltsordner in Ihrem Projekt zu erstellen, der einer URL zugeordnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="54d09-154">The easiest way to serve static content is to create a content folder in your project that can map to a URL.</span></span>

![Statischer Inhaltsordner im Device Portal](images/device-portal/plugin-static-content.png)
 
<span data-ttu-id="54d09-156">Fügen Sie dann Ihrem **RequestReceived**-Ereignishandler einen Routenereignishandler hinzu, der statische Inhaltsrouten erkennt und eine Anforderung entsprechend zuordnet.</span><span class="sxs-lookup"><span data-stu-id="54d09-156">Then, add a route handler in your **RequestReceived** event handler that detects static content routes and maps a request appropriately.</span></span>  

```csharp
if (req.RequestUri.LocalPath.ToLower().Contains("/www/")) {
    var filePath = req.RequestUri.AbsolutePath.Replace('/', '\\').ToLower();
    filePath = filePath.Replace("\\backgroundprovider", "")
    try {
        var fileStream = Windows.ApplicationModel.Package.Current.InstalledLocation.OpenStreamForReadAsync(filePath).GetAwaiter().GetResult();
        res.StatusCode = HttpStatusCode.Ok;
        res.Content = new HttpStreamContent(fileStream.AsInputStream());
        res.Content.Headers.ContentType = new HttpMediaTypeHeaderValue("text/html");
    } catch(FileNotFoundException e) {
        string con = String.Format("<h1>{0} - not found</h1>\r\n", filePath);
        con += "Exception: " + e.ToString();
        res.Content = new HttpStringContent(con);
        res.StatusCode = HttpStatusCode.NotFound;
        res.Content.Headers.ContentType = new HttpMediaTypeHeaderValue("text/html");
    }
}
```
<span data-ttu-id="54d09-157">Stellen Sie sicher, dass alle Dateien in dem Inhaltsordner als „Inhalt“ gekennzeichnet sind und im Eigenschaftenmenü von Visual Studio auf „Kopieren, wenn neuer“ oder „Immer kopieren“ festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="54d09-157">Make sure that all files inside of the content folder are marked as "Content" and set to "Copy if newer" or "Copy always" in Visual Studio’s Properties menu.</span></span>  <span data-ttu-id="54d09-158">Damit stellen Sie sicher, dass die Dateien sich bei der Bereitstellung in Ihrem AppX-Paket befinden.</span><span class="sxs-lookup"><span data-stu-id="54d09-158">This ensures that the files will be inside your AppX Package when you deploy it.</span></span>  

![Konfigurieren des Kopierens statischer Inhaltsdateien](images/device-portal/plugin-file-copying.png)

## <a name="using-existing-device-portal-resources-and-apis"></a><span data-ttu-id="54d09-160">Verwenden vorhandener Device Portal-Ressourcen und APIs</span><span class="sxs-lookup"><span data-stu-id="54d09-160">Using existing Device Portal resources and APIs</span></span>
<span data-ttu-id="54d09-161">Statischer, von einem Device Portal-Anbieter bereitgestellter Inhalt wird auf demselben Port wie der Kerndienst des Device Portal bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="54d09-161">Static content served by a Device Portal provider is served on the same port as the core Device Portal service.</span></span>  <span data-ttu-id="54d09-162">Dies bedeutet, dass Sie mit einfachen `<link>`- und `<script>`-Tags im HTML-Code auf das im Device Portal vorhandene JS und CSS verweisen können.</span><span class="sxs-lookup"><span data-stu-id="54d09-162">This means that you can reference the existing JS and CSS included with Device Portal with simple `<link>` and `<script>` tags in your HTML.</span></span> <span data-ttu-id="54d09-163">Im Allgemeinen empfehlen wir die Verwendung von *rest.js*, das alle Kern-REST-APIs des Device Portal in einem geeigneten webbRest-Objekt einschließt, und die *common.css*-Datei, mit der Sie Ihren Inhalt entsprechend der Device Portal-Benutzeroberfläche formatieren können.</span><span class="sxs-lookup"><span data-stu-id="54d09-163">In general, we suggest the use of *rest.js*, which wraps all the core Device Portal REST APIs in a convenient webbRest object, and the *common.css* file, which will allow you to style your content to fit with the rest of Device Portal's UI.</span></span> <span data-ttu-id="54d09-164">Ein Beispiel hierzu finden Sie auf der *index.html*-Seite in der Beispiel-App.</span><span class="sxs-lookup"><span data-stu-id="54d09-164">You can see an example of this in the *index.html* page included in the sample.</span></span> <span data-ttu-id="54d09-165">Hier werden mit *rest.js* der Name des Geräts und die ausgeführten Prozesse von Device Portal abgerufen.</span><span class="sxs-lookup"><span data-stu-id="54d09-165">It uses *rest.js* to retrieve the device name and running processes from Device Portal.</span></span> 

![Ausgabe des Device Portal-Plug-Ins](images/device-portal/plugin-output.png)
 
<span data-ttu-id="54d09-167">Wichtig: Bei Verwendung der HttpPost/DeleteExpect200-Methoden für webbRest erfolgt die [CSRF-Behandlung](https://docs.microsoft.com/en-us/aspnet/web-api/overview/security/preventing-cross-site-request-forgery-csrf-attacks) automatisch, wodurch Ihre Webseite zustandsverändernde REST-APIs aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="54d09-167">Importantly, use of the HttpPost/DeleteExpect200 methods on webbRest will automatically do the [CSRF handling](https://docs.microsoft.com/en-us/aspnet/web-api/overview/security/preventing-cross-site-request-forgery-csrf-attacks) for you, which allows your webpage to call state-changing REST APIs.</span></span>  

> [!NOTE] 
> <span data-ttu-id="54d09-168">Der statische, im Device Portal enthaltene Inhalt kann Änderungen unterworfen sein.</span><span class="sxs-lookup"><span data-stu-id="54d09-168">The static content included with Device Portal does not come with a guarantee against breaking changes.</span></span> <span data-ttu-id="54d09-169">APIs werden im Allgemeinen nicht häufig geändert, aber es kann vorkommen, insbesondere können die Dateien *common.js* und *controls.js* Änderungen unterworfen sein. Daher sollte Ihr Anbieter diese Dateien nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="54d09-169">While the APIs are not expected to change often, they may, especially in the *common.js* and *controls.js* files, which your provider should not use.</span></span> 

## <a name="debugging-the-device-portal-connection"></a><span data-ttu-id="54d09-170">Debuggen der Device Portal-Verbindung</span><span class="sxs-lookup"><span data-stu-id="54d09-170">Debugging the Device Portal connection</span></span>
<span data-ttu-id="54d09-171">Um die Hintergrundaufgabe zu debuggen, müssen Sie die Art und Weise ändern, wie Visual Studio Ihren Code ausführt.</span><span class="sxs-lookup"><span data-stu-id="54d09-171">In order to debug your background task, you must change the way Visual Studio runs your code.</span></span> <span data-ttu-id="54d09-172">Führen Sie die folgenden Schritte für das Debuggen einer App-Dienstverbindung aus, um zu überprüfen, wie Ihr Anbieter die HTTP-Anforderungen behandelt:</span><span class="sxs-lookup"><span data-stu-id="54d09-172">Follow the steps below for debugging an app service connection to inspect how your provider is handling the HTTP requests:</span></span>

1.  <span data-ttu-id="54d09-173">Wählen Sie im Debuggermenü die DevicePortalProvider-Eigenschaften aus.</span><span class="sxs-lookup"><span data-stu-id="54d09-173">From the Debug menu, select DevicePortalProvider Properties.</span></span> 
2.  <span data-ttu-id="54d09-174">Aktivieren Sie auf der Registerkarte „Debuggen“ im Abschnitt „Startaktion“ das Kontrollkästchen „Eigenen Code zunächst nicht starten, sondern debuggen“.</span><span class="sxs-lookup"><span data-stu-id="54d09-174">Under the Debugging tab, in the Start action section, select “Do not launch, but debug my code when it starts”.</span></span>  
![Versetzen des Plug-Ins in den Debugmodus](images/device-portal/plugin-debug-mode.png)
3.  <span data-ttu-id="54d09-176">Setzen Sie in der RequestReceived-Handlerfunktion einen Haltepunkt.</span><span class="sxs-lookup"><span data-stu-id="54d09-176">Set a breakpoint in your RequestReceived handler function.</span></span>
![Haltepunkt beim requestreceived-Handler](images/device-portal/plugin-requestreceived-breakpoint.png)
> [!NOTE] 
> <span data-ttu-id="54d09-178">Stellen Sie sicher, dass die Build-Architektur genau mit der Architektur des Ziels übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="54d09-178">Make sure the build architecture matches the architecture of the target exactly.</span></span> <span data-ttu-id="54d09-179">Wenn Sie einen 64-Bit-PC verwenden, müssen Sie einen AMD64-Build bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="54d09-179">If you are using a 64-bit PC, you must deploy using an AMD64 build.</span></span> 
4.  <span data-ttu-id="54d09-180">Drücken Sie F5, um Ihre App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="54d09-180">Press F5 to deploy your app</span></span>
5.  <span data-ttu-id="54d09-181">Deaktivieren Sie das Device Portal, und aktivieren Sie es wieder, damit es Ihre App findet (nur erforderlich, wenn Sie Ihr App-Manifest ändern – ansonsten können Sie einfach erneut bereitstellen und diesen Schritt überspringen).</span><span class="sxs-lookup"><span data-stu-id="54d09-181">Turn Device Portal off, then turn it back on so that it finds your app (only needed when you change your app manifest – the rest of the time you can simply re-deploy and skip this step).</span></span> 
6.  <span data-ttu-id="54d09-182">Öffnen Sie in Ihrem Browser den Namespace des Anbieters, und der Haltepunkt sollte erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="54d09-182">In your browser, access the provider's namespace, and the breakpoint should be hit.</span></span>

## <a name="related-topics"></a><span data-ttu-id="54d09-183">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="54d09-183">Related topics</span></span>
* [<span data-ttu-id="54d09-184">Übersicht über das Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="54d09-184">Windows Device Portal overview</span></span>](device-portal.md)
* [<span data-ttu-id="54d09-185">Erstellen und Verwenden eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="54d09-185">Create and consume an app service</span></span>](https://docs.microsoft.com/en-us/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)


