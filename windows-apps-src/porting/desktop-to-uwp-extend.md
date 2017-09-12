---
author: normesta
Description: "Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten"
Search.Product: eADQiWindows 10XVcnh
title: "Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten"
ms.author: normesta
ms.date: 07/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: fce6076f07957b50e83cf80e8d12350630b99456
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a><span data-ttu-id="c9624-104">Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten</span><span class="sxs-lookup"><span data-stu-id="c9624-104">Extend your desktop application with modern UWP components</span></span>

<span data-ttu-id="c9624-105">Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c9624-105">Some Windows 10 experiences (For example: a touch-enabled UI page) must run inside of a modern app container .</span></span> <span data-ttu-id="c9624-106">Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um die UWP-Komponente.</span><span class="sxs-lookup"><span data-stu-id="c9624-106">If you want to add these experiences, extend your desktop application with UWP component.</span></span>

<span data-ttu-id="c9624-107">In vielen Fällen können Sie die UWP-APIs direkt aus Ihrer Desktopanwendung aufrufen. Bevor Sie dieses Handbuch lesen, lesen Sie [Für Windows10 verbessern](desktop-to-uwp-enhance.md).</span><span class="sxs-lookup"><span data-stu-id="c9624-107">In many cases you can call UWP APIs directly from your desktop application, so before you review this guide, see [Enhance for Windows 10](desktop-to-uwp-enhance.md).</span></span>

>[!NOTE]
><span data-ttu-id="c9624-108">Dieses Handbuch geht davon aus, dass Sie ein Windows-App-Paket mithilfe der Desktop-Brücke für Ihre Desktopanwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="c9624-108">This guide assumes that you've created a Windows app package for your desktop application by using the Desktop Bridge.</span></span> <span data-ttu-id="c9624-109">Falls dies noch nicht geschehen ist, lesen Sie [Desktop-Brücke](desktop-to-uwp-root.md).</span><span class="sxs-lookup"><span data-stu-id="c9624-109">If you haven't yet done this, see [Desktop Bridge](desktop-to-uwp-root.md).</span></span>

<span data-ttu-id="c9624-110">Wenn Sie bereit sind, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="c9624-110">If you're ready, let's start.</span></span>

## <a name="show-a-modern-xaml-ui"></a><span data-ttu-id="c9624-111">Anzeigen einer modernen XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="c9624-111">Show a modern XAML UI</span></span>

<span data-ttu-id="c9624-112">Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren.</span><span class="sxs-lookup"><span data-stu-id="c9624-112">As part of your application flow, you can incorporate modern XAML-based user interfaces into your desktop application.</span></span> <span data-ttu-id="c9624-113">Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="c9624-113">These user interfaces are naturally adaptive to different screen sizes and resolutions and support modern interactive models such as touch and ink.</span></span>

<span data-ttu-id="c9624-114">Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c9624-114">For example, with a small amount of XAML markup, you can give users with powerful map-related visualization features.</span></span>

<span data-ttu-id="c9624-115">Diese Abbildungzeigt eine VB6-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.</span><span class="sxs-lookup"><span data-stu-id="c9624-115">This image shows a VB6 application that opens a XAML-based modern UI that contains a map control.</span></span>

![adaptives Design](images\desktop-to-uwp\extend-xaml-ui.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="c9624-117">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="c9624-117">Have a closer look at this app</span></span>

<span data-ttu-id="c9624-118">:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Add-a-XAML-UI-and-Toast-Notification-to-a-VB6-Application-OsJHC7WhD_8006218965)</span><span class="sxs-lookup"><span data-stu-id="c9624-118">:heavy_check_mark: [Watch a video](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Add-a-XAML-UI-and-Toast-Notification-to-a-VB6-Application-OsJHC7WhD_8006218965)</span></span>

<span data-ttu-id="c9624-119">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/vb6-app-with-xaml-sample/9n191ncxf2f6)</span><span class="sxs-lookup"><span data-stu-id="c9624-119">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/vb6-app-with-xaml-sample/9n191ncxf2f6)</span></span>

<span data-ttu-id="c9624-120">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)</span><span class="sxs-lookup"><span data-stu-id="c9624-120">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="c9624-121">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="c9624-121">The design pattern</span></span>

<span data-ttu-id="c9624-122">Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="c9624-122">To show a XAML-based UI, do these things:</span></span>

<span data-ttu-id="c9624-123">:one: [Hinzufügen eines UWP-Projekts zur Lösung](#project)</span><span class="sxs-lookup"><span data-stu-id="c9624-123">:one: [Add a UWP project to your solution](#project)</span></span>

<span data-ttu-id="c9624-124">:two: [Eine Protokollerweiterung zum Projekt hinzufügen](#protocol)</span><span class="sxs-lookup"><span data-stu-id="c9624-124">:two: [Add a protocol extension to that project](#protocol)</span></span>

<span data-ttu-id="c9624-125">:three: [Starten der UWP-App aus Ihrer Desktop-App](#start)</span><span class="sxs-lookup"><span data-stu-id="c9624-125">:three: [Start the UWP app from your desktop app](#start)</span></span>

<span data-ttu-id="c9624-126">:four: [Im UWP-Projekt gewünschte Seite anzeigen](#parse)</span><span class="sxs-lookup"><span data-stu-id="c9624-126">:four: [In the UWP project, show the page that you want](#parse)</span></span>

<span id="project" />
### <a name="add-a-uwp-project"></a><span data-ttu-id="c9624-127">Hinzufügen eines UWP-Projekts</span><span class="sxs-lookup"><span data-stu-id="c9624-127">Add a UWP project</span></span>

<span data-ttu-id="c9624-128">Fügen Sie der Projektmappe ein **Leere App (Universal Windows)**-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-128">Add a **Blank App (Universal Windows)** project to your solution.</span></span>

<span id="protocol" />
### <a name="add-a-protocol-extension"></a><span data-ttu-id="c9624-129">Fügen Sie eine Protokollerweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-129">Add a protocol extension</span></span>

<span data-ttu-id="c9624-130">In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Projekts und fügen die Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-130">In **Solution Explorer**, open the **package.appxmanifest** file of the project and add the extension.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.protocol"
          Executable="MapUI.exe"
          EntryPoint=" MapUI.App">
        <uap:Protocol Name="desktopbridgemapsample" />
      </uap:Extension>
    </Extensions>     
```

<span data-ttu-id="c9624-131">Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="c9624-131">Give the protocol a name, provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span>

<span data-ttu-id="c9624-132">Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c9624-132">You can also open the **package.appxmanifest** in the designer, choose the **Declarations** tab, and then add the extension there.</span></span>

![Deklarationen-Registerkarte](images\desktop-to-uwp\protocol-properties.png)



> [!NOTE]
> <span data-ttu-id="c9624-134">Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c9624-134">Map controls download data from the internet so if you use one, you'll have to add the "internet client" capability to your manifest as well.</span></span>

<span id="start" />
### <a name="start-the-uwp-app"></a><span data-ttu-id="c9624-135">Starten Sie UWP-App</span><span class="sxs-lookup"><span data-stu-id="c9624-135">Start the UWP app</span></span>

<span data-ttu-id="c9624-136">Erstellen Sie zunächst eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx) die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c9624-136">First, create a [Uri](https://msdn.microsoft.com/library/system.uri.aspx) that includes the protocol name and any parameters you want to pass into the UWP app.</span></span> <span data-ttu-id="c9624-137">Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="c9624-137">Then, call the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method.</span></span>

<span data-ttu-id="c9624-138">Hier ist ein einfaches Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="c9624-138">Here's a basic example in C#.</span></span>

```csharp

private async void showMap(double lat, double lon)
{
    string str = "desktopbridgemapsample://";

    Uri uri = new Uri(str + "location?lat=" +
        lat.ToString() + "&?lon=" + lon.ToString());

    var success = await Windows.System.Launcher.LaunchUriAsync(uri);

    if (success)
    {
        // URI launched
    }
    else
    {
        // URI launch failed
    }
}
```
In unserem Beispiel gehen wir etwas indirekter vor. Wir haben den Aufruf in eine über VB6-aufrufbare Interop-Funktion mit dem Namen ``LaunchMap`` verpackt. <span data-ttu-id="c9624-141">Diese Funktion ist in C++ geschrieben.</span><span class="sxs-lookup"><span data-stu-id="c9624-141">That function is written by using C++.</span></span>

<span data-ttu-id="c9624-142">Hier ist der VB-Block:</span><span class="sxs-lookup"><span data-stu-id="c9624-142">Here's the VB block:</span></span>

```VB
Private Declare Function LaunchMap Lib "UWPWrappers.dll" _
  (ByVal lat As Double, ByVal lon As Double) As Boolean
 
Private Sub EiffelTower_Click()
    LaunchMap 48.858222, 2.2945
End Sub
```

<span data-ttu-id="c9624-143">Dies ist die C++-Funktion:</span><span class="sxs-lookup"><span data-stu-id="c9624-143">Here's the C++ function:</span></span>

```C++

DllExport bool __stdcall LaunchMap(double lat, double lon)
{
  try
  {
    String ^str = ref new String(L"desktopbridgemapsample://");
    Uri ^uri = ref new Uri(
      str + L"location?lat=" + lat.ToString() + L"&?lon=" + lon.ToString());
 
    // now launch the UWP component
    Launcher::LaunchUriAsync(uri);
  }
  catch (Exception^ ex) { return false; }
  return true;
}

```

<span id="parse" />
### <a name="parse-parameters-and-show-a-page"></a><span data-ttu-id="c9624-144">Analysieren von Parametern und Anzeigen einer Seite</span><span class="sxs-lookup"><span data-stu-id="c9624-144">Parse parameters and show a page</span></span>

<span data-ttu-id="c9624-145">In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="c9624-145">In the **App** class of your UWP project, override the **OnActivated** event handler.</span></span> <span data-ttu-id="c9624-146">Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter und öffnen Sie die Seite, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="c9624-146">If the app is activated by your protocol, parse the parameters and then open the page that you want.</span></span>

```C++
void App::OnActivated(Windows::ApplicationModel::Activation::IActivatedEventArgs^ e)
{
  if (e->Kind == ActivationKind::Protocol)
  {
    ProtocolActivatedEventArgs^ protocolArgs = (ProtocolActivatedEventArgs^)e;
    Uri ^uri = protocolArgs->Uri;
    if (uri->SchemeName == "desktopbridgemapsample")
    {
      Frame ^rootFrame = ref new Frame();
      Window::Current->Content = rootFrame;
      rootFrame->Navigate(TypeName(MainPage::typeid), uri->Query);
      Window::Current->Activate();
    }
  }
}
```

### <a name="similar-samples"></a><span data-ttu-id="c9624-147">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="c9624-147">Similar Samples</span></span>

[<span data-ttu-id="c9624-148">Northwind-Beispiel: End-to-end-Beispiel für UWA-UI- und Win32-Legacy-Code</span><span class="sxs-lookup"><span data-stu-id="c9624-148">Northwind sample: End-to-end example for UWA UI & Win32 legacy code</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/NorthwindSample)

[<span data-ttu-id="c9624-149">Northwind-Beispiel: UWP-App, die eine Verbindung zu SQL Server herstellt</span><span class="sxs-lookup"><span data-stu-id="c9624-149">Northwind sample: UWP app connecting to SQL Server</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SQLServer)

## <a name="provide-services-to-other-apps"></a><span data-ttu-id="c9624-150">Dienste für andere Apps</span><span class="sxs-lookup"><span data-stu-id="c9624-150">Provide services to other apps</span></span>

<span data-ttu-id="c9624-151">Sie fügen einen Dienst hinzu, der von anderen Apps genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c9624-151">You add a service that other apps can consume.</span></span> <span data-ttu-id="c9624-152">Beispielsweise können Sie einen Dienst hinzufügen, der anderen Apps kontrollierten Zugriff auf die Datenbank hinter der App bietet.</span><span class="sxs-lookup"><span data-stu-id="c9624-152">For example, you can add a service that gives other apps controlled access to the database behind your app.</span></span> <span data-ttu-id="c9624-153">Durch die Implementierung einer Hintergrundaufgabe können Apps den Dienst erreichen, selbst wenn Ihre Desktop-App nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c9624-153">By implementing a background task, apps can reach the service even if your desktop app is not running.</span></span>

<span data-ttu-id="c9624-154">Hier ist ein Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="c9624-154">Here's a sample that does this.</span></span>

![adaptives Design](images\desktop-to-uwp\winforms-app-service.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="c9624-156">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="c9624-156">Have a closer look at this app</span></span>

<span data-ttu-id="c9624-157">:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Expose-an-AppService-from-a-Windows-Forms-Data-Application-GiqNS7WhD_706218965)</span><span class="sxs-lookup"><span data-stu-id="c9624-157">:heavy_check_mark: [Watch a video](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Expose-an-AppService-from-a-Windows-Forms-Data-Application-GiqNS7WhD_706218965)</span></span>

<span data-ttu-id="c9624-158">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span><span class="sxs-lookup"><span data-stu-id="c9624-158">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span></span>

<span data-ttu-id="c9624-159">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span><span class="sxs-lookup"><span data-stu-id="c9624-159">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="c9624-160">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="c9624-160">The design pattern</span></span>

<span data-ttu-id="c9624-161">Um einen Dienst bereitzustellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="c9624-161">To show provide a service, do these things:</span></span>

<span data-ttu-id="c9624-162">:one: [Komponente für Windows-Runtime hinzufügen](#component)</span><span class="sxs-lookup"><span data-stu-id="c9624-162">:one: [Add a Windows Runtime Component](#component)</span></span>

<span data-ttu-id="c9624-163">:two: [Hinzufügen einer App-Diensterweiterung](#extension)</span><span class="sxs-lookup"><span data-stu-id="c9624-163">:two: [Add an app service extension](#extension)</span></span>

<span data-ttu-id="c9624-164">:three: [Implementieren des App-Diensts](#appservice)</span><span class="sxs-lookup"><span data-stu-id="c9624-164">:three: [Implement the app service](#appservice)</span></span>

<span data-ttu-id="c9624-165">:four: [Testen des App-Dienstes](#test)</span><span class="sxs-lookup"><span data-stu-id="c9624-165">:four: [Test the app service](#test)</span></span>

<span id="component" />

### <a name="add-a-windows-runtime-component"></a><span data-ttu-id="c9624-166">Komponente für Windows-Runtime hinzufügen</span><span class="sxs-lookup"><span data-stu-id="c9624-166">Add a Windows Runtime component</span></span>

<span data-ttu-id="c9624-167">Fügen Sie der Projektmappe ein **Komponente für Windows-Runtime (Universal-Windows)**-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-167">Add a **Windows Runtime Component (Universal Windows)** project to your solution.</span></span>

<span data-ttu-id="c9624-168">Verweisen Sie dann auf das Projekt der Runtime-Komponente Ihres UWP-Packaging-Projektes.</span><span class="sxs-lookup"><span data-stu-id="c9624-168">Then, reference the project of that runtime component from your UWP packaging project.</span></span>

<span id="extension" />
### <a name="add-an-app-service-extension"></a><span data-ttu-id="c9624-169">Hinzufügen einer App-Diensterweiterung</span><span class="sxs-lookup"><span data-stu-id="c9624-169">Add an app service extension</span></span>

<span data-ttu-id="c9624-170">In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Verpackungs-Projekts und fügen die App-Diensterweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-170">In **Solution Explorer**, open the **package.appxmanifest** file of your packaging project and add an app service extension.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.appService"
          EntryPoint="MyAppService.AppServiceTask">
        <uap:AppService Name="com.microsoft.samples.winforms" />
      </uap:Extension>
    </Extensions>    
```

<span data-ttu-id="c9624-171">Benennen Sie den App-Dienst und geben Sie den Namen der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="c9624-171">Give the app service a name and provide the name of the entry point class.</span></span> <span data-ttu-id="c9624-172">Dies ist die Klasse, die Sie zum Implementieren Ihres App-Diensts verwenden.</span><span class="sxs-lookup"><span data-stu-id="c9624-172">This is the class that you'll use to implement your app service.</span></span>

<span id="appservice" />
### <a name="implement-the-app-service"></a><span data-ttu-id="c9624-173">Implementieren des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="c9624-173">Implement the app service</span></span>

<span data-ttu-id="c9624-174">Hier erfahren Sie, wo Sie Anforderungen von anderen Apps überprüfen und behandeln.</span><span class="sxs-lookup"><span data-stu-id="c9624-174">Here's where you'll validate and handle requests from other apps.</span></span>

```csharp
public sealed class AppServiceTask : IBackgroundTask
{
    private BackgroundTaskDeferral backgroundTaskDeferral;
 
    public void Run(IBackgroundTaskInstance taskInstance)
    {
        this.backgroundTaskDeferral = taskInstance.GetDeferral();
        taskInstance.Canceled += OnTaskCanceled;
        var details = taskInstance.TriggerDetails as AppServiceTriggerDetails;
        details.AppServiceConnection.RequestReceived += OnRequestReceived;
    }
 
    private async void OnRequestReceived(AppServiceConnection sender,
                                         AppServiceRequestReceivedEventArgs args)
    {
        var messageDeferral = args.GetDeferral();
        ValueSet message = args.Request.Message;
        string id = message["ID"] as string;
        ValueSet returnData = DataBase.GetData(id);
        await args.Request.SendResponseAsync(returnData);
        messageDeferral.Complete();
    }
 
 
    private void OnTaskCanceled(IBackgroundTaskInstance sender,
                                BackgroundTaskCancellationReason reason)
    {
        if (this.backgroundTaskDeferral != null)
        {
            this.backgroundTaskDeferral.Complete();
        }
    }
}
```

<span id="test" />
### <a name="test-the-app-service"></a><span data-ttu-id="c9624-175">Testen des App-Dienstes</span><span class="sxs-lookup"><span data-stu-id="c9624-175">Test the app service</span></span>

<span data-ttu-id="c9624-176">Testen Sie Ihren Dienst durch Aufrufen aus einer anderen App.</span><span class="sxs-lookup"><span data-stu-id="c9624-176">Test your service by calling it from another app.</span></span>

```csharp
private async void button_Click(object sender, RoutedEventArgs e)
{
    AppServiceConnection dataService = new AppServiceConnection();
    dataService.AppServiceName = "com.microsoft.samples.winforms";
    dataService.PackageFamilyName = "Microsoft.SDKSamples.WinformWithAppService";
 
    var status = await dataService.OpenAsync();
    if (status == AppServiceConnectionStatus.Success)
    {
        string id = int.Parse(textBox.Text);
        var message = new ValueSet();
        message.Add("ID", id);
        AppServiceResponse response = await dataService.SendMessageAsync(message);
        string result = "";
 
        if (response.Status == AppServiceResponseStatus.Success)
        {
            if (response.Message["Status"] as string == "OK")
            {
                DisplayResult(response.Message["Result"]);
            }
        }
    }
}
```

<span data-ttu-id="c9624-177">Erfahren Sie hier mehr über App-Dienste: [Erstellen und Verwenden eines App-Diensts](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="c9624-177">Learn more about app services here: [Create and consume an app service](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>

### <a name="similar-samples"></a><span data-ttu-id="c9624-178">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="c9624-178">Similar Samples</span></span>

[<span data-ttu-id="c9624-179">Beispiel für App-Dienst-Brücke</span><span class="sxs-lookup"><span data-stu-id="c9624-179">App service bridge sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample)

[<span data-ttu-id="c9624-180">Beispiel für App-Dienst Brücke mit eine C++ Win32-App</span><span class="sxs-lookup"><span data-stu-id="c9624-180">App service bridge sample with C++ win32 app</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample_C%2B%2B)

[<span data-ttu-id="c9624-181">MFC-Anwendung, die Pushbenachrichtigungen empfängt.</span><span class="sxs-lookup"><span data-stu-id="c9624-181">MFC application that receives push notifications</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/MFCwithPush)


## <a name="making-your-desktop-application-a-share-target"></a><span data-ttu-id="c9624-182">Ihre Desktopanwendung als Freigabeziel gestalten</span><span class="sxs-lookup"><span data-stu-id="c9624-182">Making your desktop application a share target</span></span>

<span data-ttu-id="c9624-183">Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c9624-183">You can make your desktop application a share target so that users can easily share data such as pictures from other apps that support sharing.</span></span>

<span data-ttu-id="c9624-184">Beispielsweise können Benutzer Ihre App zum Teilen von Bildern in Microsoft Edge auswählen.</span><span class="sxs-lookup"><span data-stu-id="c9624-184">For example, users could choose your app to share pictures from Microsoft Edge, the Photos app.</span></span> <span data-ttu-id="c9624-185">Hier ist eine WPF-Beispiel-App, die diese Funktion nutzt.</span><span class="sxs-lookup"><span data-stu-id="c9624-185">Here's a WPF sample app that has that capability.</span></span>

![Freigabeziel](images\desktop-to-uwp\share-target.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="c9624-187">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="c9624-187">Have a closer look at this app</span></span>

<span data-ttu-id="c9624-188">:heavy_check_mark: [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Make-a-WPF-Application-a-Share-Target-xd6Fu6WhD_8406218965)</span><span class="sxs-lookup"><span data-stu-id="c9624-188">:heavy_check_mark: [Watch a video](https://mva.microsoft.com/en-US/training-courses/developers-guide-to-the-desktop-bridge-17373/Demo-Make-a-WPF-Application-a-Share-Target-xd6Fu6WhD_8406218965)</span></span>

<span data-ttu-id="c9624-189">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span><span class="sxs-lookup"><span data-stu-id="c9624-189">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span></span>

<span data-ttu-id="c9624-190">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span><span class="sxs-lookup"><span data-stu-id="c9624-190">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="c9624-191">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="c9624-191">The design pattern</span></span>

<span data-ttu-id="c9624-192">Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="c9624-192">To make your application a share target, do these things:</span></span>

<span data-ttu-id="c9624-193">:one: [Hinzufügen eines UWP-Projekts zur Lösung](#project2)</span><span class="sxs-lookup"><span data-stu-id="c9624-193">:one: [Add a UWP project to your solution](#project2)</span></span>

<span data-ttu-id="c9624-194">:two: [Fügen Sie die Freigabezielerweiterung hinzu](#share-extension)</span><span class="sxs-lookup"><span data-stu-id="c9624-194">:two: [Add a share target extension](#share-extension)</span></span>

<span data-ttu-id="c9624-195">:three: [Überschreiben des OnNavigatedTo-Ereignisses](#override)</span><span class="sxs-lookup"><span data-stu-id="c9624-195">:three: [Override the OnNavigatedTo event handler](#override)</span></span>

<span id="project2" />
### <a name="add-a-uwp-project-to-your-solution"></a><span data-ttu-id="c9624-196">Hinzufügen eines UWP-Projekts zur Lösung</span><span class="sxs-lookup"><span data-stu-id="c9624-196">Add a UWP project to your solution</span></span>

<span data-ttu-id="c9624-197">Fügen Sie der Projektmappe ein **Leere App (Universal Windows)**-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-197">Add a **Blank App (Universal Windows)** project to your solution.</span></span>

<span id="share-extension" />
### <a name="add-a-share-target-extension"></a><span data-ttu-id="c9624-198">Fügen Sie die Freigabezielerweiterung hinzu</span><span class="sxs-lookup"><span data-stu-id="c9624-198">Add a share target extension</span></span>

<span data-ttu-id="c9624-199">In **Projektmappen-Explorer** öffnen Sie die **package.appxmanifest** Datei des Projekts und fügen die Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="c9624-199">In **Solution Explorer**, open the **package.appxmanifest** file of the project and add the extension.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.shareTarget"
          Executable="ShareTarget.exe"
          EntryPoint="ShareTarget.App">
        <uap:ShareTarget>
          <uap:SupportedFileTypes>
            <uap:SupportsAnyFileType />
          </uap:SupportedFileTypes>
          <uap:DataFormat>Bitmap</uap:DataFormat>
        </uap:ShareTarget>
      </uap:Extension>
</Extensions>  
```

<span data-ttu-id="c9624-200">Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c9624-200">Provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span> <span data-ttu-id="c9624-201">Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können.</span><span class="sxs-lookup"><span data-stu-id="c9624-201">You'll also have to specify what types of files can be shared with your app.</span></span>

<span id="override" />
### <a name="override-the-onnavigatedto-event-handler"></a><span data-ttu-id="c9624-202">Überschreiben des OnNavigatedTo-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="c9624-202">Override the OnNavigatedTo event handler</span></span>

<span data-ttu-id="c9624-203">Überschreiben Sie den **OnNavigatedTo**-Ereignishandler in der **App** Klasse des UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="c9624-203">Override the **OnNavigatedTo** event handler in the **App** class of your UWP project.</span></span>

<span data-ttu-id="c9624-204">Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.</span><span class="sxs-lookup"><span data-stu-id="c9624-204">This event handler is called when users choose your app to share their files.</span></span>

```csharp
protected override async void OnNavigatedTo(NavigationEventArgs e)
{
  this.shareOperation = (ShareOperation)e.Parameter;
  if (this.shareOperation.Data.Contains(StandardDataFormats.StorageItems))
  {
      this.sharedStorageItems =
        await this.shareOperation.Data.GetStorageItemsAsync();
       
      foreach (StorageFile item in this.sharedStorageItems)
      {
          ProcessSharedFile(item);
      }
  }
}
```

## <a name="support-and-feedback"></a><span data-ttu-id="c9624-205">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="c9624-205">Support and feedback</span></span>

**<span data-ttu-id="c9624-206">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="c9624-206">Find answers to specific questions</span></span>**

<span data-ttu-id="c9624-207">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="c9624-207">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="c9624-208">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="c9624-208">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="c9624-209">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="c9624-209">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial)</span></span>

**<span data-ttu-id="c9624-210">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="c9624-210">Give feedback about this article</span></span>**

<span data-ttu-id="c9624-211">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="c9624-211">Use the comments section below.</span></span>
