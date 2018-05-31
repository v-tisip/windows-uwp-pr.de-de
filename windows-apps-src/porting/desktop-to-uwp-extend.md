---
author: normesta
Description: Extend your desktop application with Windows UIs and components
Search.Product: eADQiWindows 10XVcnh
title: Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten
ms.author: normesta
ms.date: 03/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ef20366092a5f284c39f4e43d4412c69b60f12fa
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1691329"
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a><span data-ttu-id="435f2-103">Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten</span><span class="sxs-lookup"><span data-stu-id="435f2-103">Extend your desktop application with modern UWP components</span></span>

<span data-ttu-id="435f2-104">Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="435f2-104">Some Windows 10 experiences (For example: a touch-enabled UI page) must run inside of a modern app container .</span></span> <span data-ttu-id="435f2-105">Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um UWP-Projekte und die Komponente für Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="435f2-105">If you want to add these experiences, extend your desktop application with UWP projects and Windows Runtime Components.</span></span>

<span data-ttu-id="435f2-106">In vielen Fällen können Sie die UWP-APIs direkt aus Ihrer Desktopanwendung aufrufen. Bevor Sie dieses Handbuch lesen, lesen Sie [Für Windows10 verbessern](desktop-to-uwp-enhance.md).</span><span class="sxs-lookup"><span data-stu-id="435f2-106">In many cases you can call UWP APIs directly from your desktop application, so before you review this guide, see [Enhance for Windows 10](desktop-to-uwp-enhance.md).</span></span>

>[!NOTE]
><span data-ttu-id="435f2-107">Dieses Handbuch geht davon aus, dass Sie ein Windows-App-Paket mithilfe der Desktop-Brücke für Ihre Desktopanwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="435f2-107">This guide assumes that you've created a Windows app package for your desktop application by using the Desktop Bridge.</span></span> <span data-ttu-id="435f2-108">Falls dies noch nicht geschehen ist, lesen Sie [Desktop-Brücke](desktop-to-uwp-root.md).</span><span class="sxs-lookup"><span data-stu-id="435f2-108">If you haven't yet done this, see [Desktop Bridge](desktop-to-uwp-root.md).</span></span>

<span data-ttu-id="435f2-109">Wenn Sie bereit sind, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="435f2-109">If you're ready, let's start.</span></span>

## <a name="first-setup-your-solution"></a><span data-ttu-id="435f2-110">Ihre Projektmappe einrichten</span><span class="sxs-lookup"><span data-stu-id="435f2-110">First, setup your Solution</span></span>

<span data-ttu-id="435f2-111">Fügen Sie Ihrer Projektmappe ein oder mehrere UWP-Projekte und Laufzeitkomponenten hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-111">Add one or more UWP projects and runtime components to your solution.</span></span>

<span data-ttu-id="435f2-112">Beginnen Sie mit einer Projektmappe, die ein **Paketerstellungsprojekt für Windows-Anwendungen** mit einem Verweis auf Ihre Desktop-Anwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="435f2-112">Start with a solution that contains a **Windows Application Packaging Project** with a reference to your desktop application.</span></span>

<span data-ttu-id="435f2-113">Diese Abbildung zeigt ein Beispiel für eine Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="435f2-113">This image shows an example solution.</span></span>

![Erweitern des Startprojekts](images/desktop-to-uwp/extend-start-project.png)

<span data-ttu-id="435f2-115">Wenn Ihre Projektmappe kein Paketerstellungsprojekt enthält, lesen Sie [Verpacken Ihrer App mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="435f2-115">If your solution doesn't contain a packaging project, see [Package your app by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

### <a name="add-a-uwp-project"></a><span data-ttu-id="435f2-116">Hinzufügen eines UWP-Projekts</span><span class="sxs-lookup"><span data-stu-id="435f2-116">Add a UWP project</span></span>

<span data-ttu-id="435f2-117">Fügen Sie der Projektmappe eine **Leere App (Universelle Windows-App)** hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-117">Add a **Blank App (Universal Windows)** to your solution.</span></span>

<span data-ttu-id="435f2-118">Hier erstellen Sie eine moderne XAML-Benutzeroberfläche oder verwenden APIs, die nur innerhalb eines UWP-Prozesses ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="435f2-118">This is where you'll build a modern XAML UI or use APIs that run only within a UWP process.</span></span>

![UWP-Projekt](images/desktop-to-uwp/add-uwp-project-to-solution.png)

<span data-ttu-id="435f2-120">Klicken Sie in Ihrem Paketerstellungsprojekt mit der rechten Maustaste auf den Knoten **Anwendungen**, und klicken Sie dann auf **Verweis hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="435f2-120">In your packaging project, right-click the **Applications** node, and then click **Add Reference**.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/add-uwp-project-reference.png)

<span data-ttu-id="435f2-122">Fügen Sie einen Verweis auf das UWP-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-122">Then, add a reference the UWP project.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/choose-uwp-project.png)

<span data-ttu-id="435f2-124">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="435f2-124">Your solution will look something like this:</span></span>

![Projektmappe mit UWP-Projekt](images/desktop-to-uwp/uwp-project-reference.png)

### <a name="optional-add-a-windows-runtime-component"></a><span data-ttu-id="435f2-126">(Optional) Komponente für Windows-Runtime hinzufügen</span><span class="sxs-lookup"><span data-stu-id="435f2-126">(Optional) Add a Windows Runtime Component</span></span>

<span data-ttu-id="435f2-127">Um einige Szenarien zu erreichen, müssen Sie einer Komponente für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="435f2-127">To accomplish some scenarios, you'll have to add code to a Windows Runtime Component.</span></span>

![Runtime-Komponente App-Dienst](images/desktop-to-uwp/add-runtime-component.png)

<span data-ttu-id="435f2-129">Fügen Sie dann in Ihrem UWP-Projekt einen Verweis auf die Laufzeitkomponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-129">Then, from your UWP project, add a reference to the runtime component.</span></span> <span data-ttu-id="435f2-130">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="435f2-130">Your solution will look something like this:</span></span>

![Verweis auf die Laufzeitkomponente](images/desktop-to-uwp/runtime-component-reference.png)

<span data-ttu-id="435f2-132">Werfen wir einen Blick auf einige Dinge, die Sie mit Ihren UWP-Projekten und Laufzeitkomponenten tun können.</span><span class="sxs-lookup"><span data-stu-id="435f2-132">Let's take a look at a few things you can do with your UWP projects and runtime components.</span></span>

## <a name="show-a-modern-xaml-ui"></a><span data-ttu-id="435f2-133">Anzeigen einer modernen XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="435f2-133">Show a modern XAML UI</span></span>

<span data-ttu-id="435f2-134">Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren.</span><span class="sxs-lookup"><span data-stu-id="435f2-134">As part of your application flow, you can incorporate modern XAML-based user interfaces into your desktop application.</span></span> <span data-ttu-id="435f2-135">Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="435f2-135">These user interfaces are naturally adaptive to different screen sizes and resolutions and support modern interactive models such as touch and ink.</span></span>

<span data-ttu-id="435f2-136">Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="435f2-136">For example, with a small amount of XAML markup, you can give users with powerful map-related visualization features.</span></span>

<span data-ttu-id="435f2-137">Diese Abbildungzeigt eine VB6-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.</span><span class="sxs-lookup"><span data-stu-id="435f2-137">This image shows a VB6 application that opens a XAML-based modern UI that contains a map control.</span></span>

![adaptives Design](images/desktop-to-uwp/extend-xaml-ui.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="435f2-139">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="435f2-139">Have a closer look at this app</span></span>

<span data-ttu-id="435f2-140">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/vb6-app-with-xaml-sample/9n191ncxf2f6)</span><span class="sxs-lookup"><span data-stu-id="435f2-140">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/vb6-app-with-xaml-sample/9n191ncxf2f6)</span></span>

<span data-ttu-id="435f2-141">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)</span><span class="sxs-lookup"><span data-stu-id="435f2-141">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="435f2-142">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="435f2-142">The design pattern</span></span>

<span data-ttu-id="435f2-143">Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="435f2-143">To show a XAML-based UI, do these things:</span></span>

<span data-ttu-id="435f2-144">:one: [Eine Protokollerweiterung zum Projekt hinzufügen](#protocol)</span><span class="sxs-lookup"><span data-stu-id="435f2-144">:one: [Add a protocol extension to that project](#protocol)</span></span>

<span data-ttu-id="435f2-145">:two: [Starten der UWP-App aus Ihrer Desktop-App](#start)</span><span class="sxs-lookup"><span data-stu-id="435f2-145">:two: [Start the UWP app from your desktop app](#start)</span></span>

<span data-ttu-id="435f2-146">:three: [Im UWP-Projekt gewünschte Seite anzeigen](#parse)</span><span class="sxs-lookup"><span data-stu-id="435f2-146">:three: [In the UWP project, show the page that you want](#parse)</span></span>

<a id="protocol" />

### <a name="add-a-protocol-extension"></a><span data-ttu-id="435f2-147">Hinzufügen einer Protokollerweiterung</span><span class="sxs-lookup"><span data-stu-id="435f2-147">Add a protocol extension</span></span>

<span data-ttu-id="435f2-148">Öffnen Sie im **Projektmappen-Explorer** die **package.appxmanifest**-Datei des UWP-Projekts in Ihrer Projektmappe und fügen Sie diese Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-148">In **Solution Explorer**, open the **package.appxmanifest** file of the UWP project in your solution, and add this extension.</span></span>

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

<span data-ttu-id="435f2-149">Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="435f2-149">Give the protocol a name, provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span>

<span data-ttu-id="435f2-150">Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="435f2-150">You can also open the **package.appxmanifest** in the designer, choose the **Declarations** tab, and then add the extension there.</span></span>

![Deklarationen-Registerkarte](images/desktop-to-uwp/protocol-properties.png)



> [!NOTE]
> <span data-ttu-id="435f2-152">Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="435f2-152">Map controls download data from the internet so if you use one, you'll have to add the "internet client" capability to your manifest as well.</span></span>

<a id="start" />

### <a name="start-the-uwp-app"></a><span data-ttu-id="435f2-153">Starten der UWP-App</span><span class="sxs-lookup"><span data-stu-id="435f2-153">Start the UWP app</span></span>

<span data-ttu-id="435f2-154">Erstellen Sie zunächst in Ihrer Desktop-Anwendung eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx), die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="435f2-154">First, from your desktop application, create a [Uri](https://msdn.microsoft.com/library/system.uri.aspx) that includes the protocol name and any parameters you want to pass into the UWP app.</span></span> <span data-ttu-id="435f2-155">Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="435f2-155">Then, call the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync) method.</span></span>

<span data-ttu-id="435f2-156">Hier ist ein einfaches Beispiel in C#.</span><span class="sxs-lookup"><span data-stu-id="435f2-156">Here's a basic example in C#.</span></span>

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
In unserem Beispiel gehen wir etwas indirekter vor. Wir haben den Aufruf in eine über VB6-aufrufbare Interop-Funktion mit dem Namen ``LaunchMap`` verpackt. <span data-ttu-id="435f2-159">Diese Funktion ist in C++ geschrieben.</span><span class="sxs-lookup"><span data-stu-id="435f2-159">That function is written by using C++.</span></span>

<span data-ttu-id="435f2-160">Hier ist der VB-Block:</span><span class="sxs-lookup"><span data-stu-id="435f2-160">Here's the VB block:</span></span>

```VB
Private Declare Function LaunchMap Lib "UWPWrappers.dll" _
  (ByVal lat As Double, ByVal lon As Double) As Boolean
 
Private Sub EiffelTower_Click()
    LaunchMap 48.858222, 2.2945
End Sub
```

<span data-ttu-id="435f2-161">Dies ist die C++-Funktion:</span><span class="sxs-lookup"><span data-stu-id="435f2-161">Here's the C++ function:</span></span>

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

<a id="parse" />

### <a name="parse-parameters-and-show-a-page"></a><span data-ttu-id="435f2-162">Analysieren von Parametern und Anzeigen einer Seite</span><span class="sxs-lookup"><span data-stu-id="435f2-162">Parse parameters and show a page</span></span>

<span data-ttu-id="435f2-163">In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="435f2-163">In the **App** class of your UWP project, override the **OnActivated** event handler.</span></span> <span data-ttu-id="435f2-164">Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter und öffnen Sie die Seite, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="435f2-164">If the app is activated by your protocol, parse the parameters and then open the page that you want.</span></span>

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

### <a name="similar-samples"></a><span data-ttu-id="435f2-165">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="435f2-165">Similar Samples</span></span>

[<span data-ttu-id="435f2-166">Northwind-Beispiel: End-to-end-Beispiel für UWA-UI- und Win32-Legacy-Code</span><span class="sxs-lookup"><span data-stu-id="435f2-166">Northwind sample: End-to-end example for UWA UI & Win32 legacy code</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/NorthwindSample)

[<span data-ttu-id="435f2-167">Northwind-Beispiel: UWP-App, die eine Verbindung zu SQL Server herstellt</span><span class="sxs-lookup"><span data-stu-id="435f2-167">Northwind sample: UWP app connecting to SQL Server</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SQLServer)

## <a name="provide-services-to-other-apps"></a><span data-ttu-id="435f2-168">Dienste für andere Apps</span><span class="sxs-lookup"><span data-stu-id="435f2-168">Provide services to other apps</span></span>

<span data-ttu-id="435f2-169">Sie fügen einen Dienst hinzu, der von anderen Apps genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="435f2-169">You add a service that other apps can consume.</span></span> <span data-ttu-id="435f2-170">Beispielsweise können Sie einen Dienst hinzufügen, der anderen Apps kontrollierten Zugriff auf die Datenbank hinter der App bietet.</span><span class="sxs-lookup"><span data-stu-id="435f2-170">For example, you can add a service that gives other apps controlled access to the database behind your app.</span></span> <span data-ttu-id="435f2-171">Durch die Implementierung einer Hintergrundaufgabe können Apps den Dienst erreichen, selbst wenn Ihre Desktop-App nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="435f2-171">By implementing a background task, apps can reach the service even if your desktop app is not running.</span></span>

<span data-ttu-id="435f2-172">Hier ist ein Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="435f2-172">Here's a sample that does this.</span></span>

![adaptives Design](images/desktop-to-uwp/winforms-app-service.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="435f2-174">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="435f2-174">Have a closer look at this app</span></span>

<span data-ttu-id="435f2-175">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span><span class="sxs-lookup"><span data-stu-id="435f2-175">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span></span>

<span data-ttu-id="435f2-176">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span><span class="sxs-lookup"><span data-stu-id="435f2-176">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="435f2-177">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="435f2-177">The design pattern</span></span>

<span data-ttu-id="435f2-178">Um einen Dienst bereitzustellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="435f2-178">To show provide a service, do these things:</span></span>

<span data-ttu-id="435f2-179">:one: [Implementieren des App-Diensts](#appservice)</span><span class="sxs-lookup"><span data-stu-id="435f2-179">:one: [Implement the app service](#appservice)</span></span>

<span data-ttu-id="435f2-180">:two: [Hinzufügen einer App-Diensterweiterung](#extension)</span><span class="sxs-lookup"><span data-stu-id="435f2-180">:two: [Add an app service extension](#extension)</span></span>

<span data-ttu-id="435f2-181">:three: [Testen des App-Dienstes](#test)</span><span class="sxs-lookup"><span data-stu-id="435f2-181">:three: [Test the app service](#test)</span></span>

<a id="appservice" />

### <a name="implement-the-app-service"></a><span data-ttu-id="435f2-182">Implementieren des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="435f2-182">Implement the app service</span></span>

<span data-ttu-id="435f2-183">Hier erfahren Sie, wo Sie Anforderungen von anderen Apps überprüfen und behandeln.</span><span class="sxs-lookup"><span data-stu-id="435f2-183">Here's where you'll validate and handle requests from other apps.</span></span> <span data-ttu-id="435f2-184">Fügen Sie diesen Code einer Komponente für Windows-Runtime in Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-184">Add this code to a Windows Runtime Component in your solution.</span></span>

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

<a id="extension" />

### <a name="add-an-app-service-extension-to-the-uwp-project"></a><span data-ttu-id="435f2-185">Hinzufügen einer App-Diensterweiterung zum UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="435f2-185">Add an app service extension to the UWP project</span></span>

<span data-ttu-id="435f2-186">Öffnen Sie die **package.appxmanifest**-Datei des UWP-Projekts und fügen Sie dem ``<Application>``-Element eine App-Diensterweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-186">Open the **package.appxmanifest** file of the UWP project, and add an app service extension to the ``<Application>`` element.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.appService"
          EntryPoint="AppServiceComponent.AppServiceTask">
        <uap:AppService Name="com.microsoft.samples.winforms" />
      </uap:Extension>
    </Extensions>    
```
<span data-ttu-id="435f2-187">Benennen Sie den App-Dienst und geben Sie den Namen der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="435f2-187">Give the app service a name and provide the name of the entry point class.</span></span> <span data-ttu-id="435f2-188">Dies ist die Klasse, in der Sie den Dienst implementiert haben.</span><span class="sxs-lookup"><span data-stu-id="435f2-188">This is the class in which you implemented the service.</span></span>

<a id="test" />

### <a name="test-the-app-service"></a><span data-ttu-id="435f2-189">Testen des App-Dienstes</span><span class="sxs-lookup"><span data-stu-id="435f2-189">Test the app service</span></span>

<span data-ttu-id="435f2-190">Testen Sie Ihren Dienst durch Aufrufen aus einer anderen App.</span><span class="sxs-lookup"><span data-stu-id="435f2-190">Test your service by calling it from another app.</span></span> <span data-ttu-id="435f2-191">Dieser Code kann eine Desktop-Anwendung wie z.B. eine Windows Forms-App oder eine andere UWP-App sein.</span><span class="sxs-lookup"><span data-stu-id="435f2-191">This code can be a desktop application such as a Windows forms app or another UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="435f2-192">Dieser Code funktioniert nur, wenn Sie die ``PackageFamilyName``-Eigenschaft der ``AppServiceConnection``-Klasse richtig festlegen.</span><span class="sxs-lookup"><span data-stu-id="435f2-192">This code only works if you properly set the ``PackageFamilyName`` property of the ``AppServiceConnection`` class.</span></span> <span data-ttu-id="435f2-193">Sie erhalten diesen Namen, wenn Sie ``Windows.ApplicationModel.Package.Current.Id.FamilyName`` im Kontext des UWP-Projekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="435f2-193">You can get that name by calling ``Windows.ApplicationModel.Package.Current.Id.FamilyName`` in the context of the UWP project.</span></span> <span data-ttu-id="435f2-194">Siehe [Erstellen und Verwenden eines App-Dienstes](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="435f2-194">See [Create and consume an app service](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>

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

<span data-ttu-id="435f2-195">Erfahren Sie hier mehr über App-Dienste: [Erstellen und Verwenden eines App-Diensts](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="435f2-195">Learn more about app services here: [Create and consume an app service](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>

### <a name="similar-samples"></a><span data-ttu-id="435f2-196">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="435f2-196">Similar Samples</span></span>

[<span data-ttu-id="435f2-197">Beispiel für App-Dienst-Brücke</span><span class="sxs-lookup"><span data-stu-id="435f2-197">App service bridge sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample)

[<span data-ttu-id="435f2-198">Beispiel für App-Dienst Brücke mit eine C++ Win32-App</span><span class="sxs-lookup"><span data-stu-id="435f2-198">App service bridge sample with C++ win32 app</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample_C%2B%2B)

[<span data-ttu-id="435f2-199">MFC-Anwendung, die Pushbenachrichtigungen empfängt.</span><span class="sxs-lookup"><span data-stu-id="435f2-199">MFC application that receives push notifications</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/MFCwithPush)


## <a name="making-your-desktop-application-a-share-target"></a><span data-ttu-id="435f2-200">Ihre Desktopanwendung als Freigabeziel gestalten</span><span class="sxs-lookup"><span data-stu-id="435f2-200">Making your desktop application a share target</span></span>

<span data-ttu-id="435f2-201">Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.</span><span class="sxs-lookup"><span data-stu-id="435f2-201">You can make your desktop application a share target so that users can easily share data such as pictures from other apps that support sharing.</span></span>

<span data-ttu-id="435f2-202">Beispielsweise können Benutzer Ihre App zum Teilen von Bildern in Microsoft Edge auswählen.</span><span class="sxs-lookup"><span data-stu-id="435f2-202">For example, users could choose your app to share pictures from Microsoft Edge, the Photos app.</span></span> <span data-ttu-id="435f2-203">Hier ist eine WPF-Beispiel-App, die diese Funktion nutzt.</span><span class="sxs-lookup"><span data-stu-id="435f2-203">Here's a WPF sample app that has that capability.</span></span>

![Freigabeziel](images/desktop-to-uwp/share-target.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="435f2-205">Sehen Sie sich diese App näher an</span><span class="sxs-lookup"><span data-stu-id="435f2-205">Have a closer look at this app</span></span>

<span data-ttu-id="435f2-206">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span><span class="sxs-lookup"><span data-stu-id="435f2-206">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span></span>

<span data-ttu-id="435f2-207">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span><span class="sxs-lookup"><span data-stu-id="435f2-207">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="435f2-208">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="435f2-208">The design pattern</span></span>

<span data-ttu-id="435f2-209">Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="435f2-209">To make your application a share target, do these things:</span></span>

<span data-ttu-id="435f2-210">:one: [Hinzufügen der Freigabezielerweiterung](#share-extension)</span><span class="sxs-lookup"><span data-stu-id="435f2-210">:one: [Add a share target extension](#share-extension)</span></span>

<span data-ttu-id="435f2-211">:two: [Überschreiben des OnNavigatedTo-Ereignishandlers](#override)</span><span class="sxs-lookup"><span data-stu-id="435f2-211">:two: [Override the OnNavigatedTo event handler](#override)</span></span>

<a id="share-extension" />

### <a name="add-a-share-target-extension"></a><span data-ttu-id="435f2-212">Hinzufügen der Freigabezielerweiterung</span><span class="sxs-lookup"><span data-stu-id="435f2-212">Add a share target extension</span></span>

<span data-ttu-id="435f2-213">Öffnen Sie im **Projektmappen-Explorer** die **package.appxmanifest**-Datei des UWP-Projekts in Ihrer Projektmappe und fügen Sie die Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-213">In **Solution Explorer**, open the **package.appxmanifest** file of the UWP project in your solution and add the extension.</span></span>

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

<span data-ttu-id="435f2-214">Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse.</span><span class="sxs-lookup"><span data-stu-id="435f2-214">Provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span> <span data-ttu-id="435f2-215">Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können.</span><span class="sxs-lookup"><span data-stu-id="435f2-215">You'll also have to specify what types of files can be shared with your app.</span></span>

<a id="override" />

### <a name="override-the-onnavigatedto-event-handler"></a><span data-ttu-id="435f2-216">Überschreiben des OnNavigatedTo-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="435f2-216">Override the OnNavigatedTo event handler</span></span>

<span data-ttu-id="435f2-217">Überschreiben Sie den **OnNavigatedTo**-Ereignishandler in der **App** Klasse des UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="435f2-217">Override the **OnNavigatedTo** event handler in the **App** class of your UWP project.</span></span>

<span data-ttu-id="435f2-218">Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.</span><span class="sxs-lookup"><span data-stu-id="435f2-218">This event handler is called when users choose your app to share their files.</span></span>

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

## <a name="create-a-background-task"></a><span data-ttu-id="435f2-219">Erstellen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="435f2-219">Create a background task</span></span>

<span data-ttu-id="435f2-220">Sie fügen eine Hintergrundaufgaben hinzu, um selbst dann App-Code auszuführen, wenn die App angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="435f2-220">You add a background task to run code even when the app is suspended.</span></span> <span data-ttu-id="435f2-221">Hintergrundaufgaben sind ideal für kleine Aufgaben, die keine Benutzerinteraktion erfordern.</span><span class="sxs-lookup"><span data-stu-id="435f2-221">Background tasks are great for small tasks that don't require the user interaction.</span></span> <span data-ttu-id="435f2-222">Beispielsweise kann Ihre Aufgabe E-Mails herunterladen, eine Popupbenachrichtigung über eine eingehende Chatnachricht zeigen oder auf eine Änderung in einer Systembedingung reagieren.</span><span class="sxs-lookup"><span data-stu-id="435f2-222">For example, your task can download mail, show a toast notification about an incoming chat message, or react to a change in a system condition.</span></span>

<span data-ttu-id="435f2-223">Hier sehen Sie ein Beispiel einer WPF-App, die eine Hintergrundaufgabe registriert.</span><span class="sxs-lookup"><span data-stu-id="435f2-223">Here's a WPF sample app that registers a background task.</span></span>

![hintergrundaufgabe](images/desktop-to-uwp/sample-background-task.png)

<span data-ttu-id="435f2-225">Die Aufgabe stellt eine HTTP-Anforderung und misst die Zeit, die die Anforderung benötigt, um eine Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="435f2-225">The task makes an http request and measures the time that it takes for the request to return a response.</span></span> <span data-ttu-id="435f2-226">Ihre Aufgaben werden wahrscheinlich viel interessanter sein, aber dieses Beispiel eignet sich gut, um die grundlegende Funktionsweise einer Hintergrundaufgabe zu lernen.</span><span class="sxs-lookup"><span data-stu-id="435f2-226">Your tasks will likely be much more interesting, but this sample is great for learning the basic mechanics of a background task.</span></span>

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="435f2-227">Sehen Sie sich diese App näher an</span><span class="sxs-lookup"><span data-stu-id="435f2-227">Have a closer look at this app</span></span>

<span data-ttu-id="435f2-228">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask)</span><span class="sxs-lookup"><span data-stu-id="435f2-228">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="435f2-229">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="435f2-229">The design pattern</span></span>

<span data-ttu-id="435f2-230">Um einen Hintergrunddienst zu erstellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="435f2-230">To create a background service, do these things:</span></span>

<span data-ttu-id="435f2-231">:one: [Implementieren der Hintergrundaufgabe](#implement-task)</span><span class="sxs-lookup"><span data-stu-id="435f2-231">:one: [Implement the background task](#implement-task)</span></span>

<span data-ttu-id="435f2-232">:two: [Konfigurieren der Hintergrundaufgabe](#configure-background-task)</span><span class="sxs-lookup"><span data-stu-id="435f2-232">:two: [Configure the background task](#configure-background-task)</span></span>

<span data-ttu-id="435f2-233">:three: [Registrieren der Hintergrundaufgabe](#register-background-task)</span><span class="sxs-lookup"><span data-stu-id="435f2-233">:three: [Register the background task](#register-background-task)</span></span>

<a id="implement-task" />

### <a name="implement-the-background-task"></a><span data-ttu-id="435f2-234">Implementieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="435f2-234">Implement the background task</span></span>

<span data-ttu-id="435f2-235">Implementieren Sie die Hintergrundaufgabe, indem Sie einem Komponentenprojekt für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="435f2-235">Implement the background task by adding code to a Windows Runtime component project.</span></span>

```csharp
public sealed class SiteVerifier : IBackgroundTask
{
    public async void Run(IBackgroundTaskInstance taskInstance)
    {

        taskInstance.Canceled += TaskInstance_Canceled;
        BackgroundTaskDeferral deferral = taskInstance.GetDeferral();
        var msg = await MeasureRequestTime();
        ShowToast(msg);
        deferral.Complete();
    }

    private async Task<string> MeasureRequestTime()
    {
        string msg;
        try
        {
            var url = ApplicationData.Current.LocalSettings.Values["UrlToVerify"] as string;
            var http = new HttpClient();
            Stopwatch clock = Stopwatch.StartNew();
            var response = await http.GetAsync(new Uri(url));
            response.EnsureSuccessStatusCode();
            var elapsed = clock.ElapsedMilliseconds;
            clock.Stop();
            msg = $"{url} took {elapsed.ToString()} ms";
        }
        catch (Exception ex)
        {
            msg = ex.Message;
        }
        return msg;
    }
```

<a id="configure-background-task" />

### <a name="configure-the-background-task"></a><span data-ttu-id="435f2-236">Konfigurieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="435f2-236">Configure the background task</span></span>

<span data-ttu-id="435f2-237">Öffnen Sie im Manifest-Designer die **package.appxmanifest**-Datei des UWP-Projekts in Ihrer Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="435f2-237">In the manifest designer, open the **package.appxmanifest** file of the UWP project in your solution.</span></span>

<span data-ttu-id="435f2-238">Fügen Sie auf der Registerkarte **Deklarationen** eine **Hintergrundaufgaben**-Deklaration hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-238">In the **Declarations** tab, add a **Background Tasks** declaration.</span></span>

![Hintergrundaufgaben-Option](images/desktop-to-uwp/background-task-option.png)

<span data-ttu-id="435f2-240">Wählen Sie dann die gewünschten Eigenschaften aus.</span><span class="sxs-lookup"><span data-stu-id="435f2-240">Then, choose the desired properties.</span></span> <span data-ttu-id="435f2-241">Unser Beispiel verwendet die **Timer**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="435f2-241">Our sample uses the **Timer** property.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/timer-property.png)

<span data-ttu-id="435f2-243">Geben Sie den vollqualifizierten Namen der Klasse in der Komponente für Windows-Runtime, die die Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="435f2-243">Provide the fully qualified name of the class in your Windows Runtime Component that implements the background task.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/background-task-entry-point.png)

<a id="register-background-task" />

### <a name="register-the-background-task"></a><span data-ttu-id="435f2-245">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="435f2-245">Register the background task</span></span>

<span data-ttu-id="435f2-246">Fügen Sie Ihrem Projekt für die Desktop-Anwendung, das die Hintergrundaufgabe registriert, Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="435f2-246">Add code to your desktop application project that registers the background task.</span></span>

```csharp
public void RegisterBackgroundTask(String triggerName)
{
    var current = BackgroundTaskRegistration.AllTasks
        .Where(b => b.Value.Name == triggerName).FirstOrDefault().Value;

    if (current is null)
    {
        BackgroundTaskBuilder builder = new BackgroundTaskBuilder();
        builder.Name = triggerName;
        builder.SetTrigger(new MaintenanceTrigger(15, false));
        builder.TaskEntryPoint = "HttpPing.SiteVerifier";
        builder.Register();
        System.Diagnostics.Debug.WriteLine("BGTask registered:" + triggerName);
    }
    else
    {
        System.Diagnostics.Debug.WriteLine("Task already:" + triggerName);
    }
}
```
## <a name="support-and-feedback"></a><span data-ttu-id="435f2-247">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="435f2-247">Support and feedback</span></span>

**<span data-ttu-id="435f2-248">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="435f2-248">Find answers to your questions</span></span>**

<span data-ttu-id="435f2-249">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="435f2-249">Have questions?</span></span> <span data-ttu-id="435f2-250">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="435f2-250">Ask us on Stack Overflow.</span></span> <span data-ttu-id="435f2-251">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="435f2-251">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="435f2-252">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="435f2-252">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="435f2-253">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="435f2-253">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="435f2-254">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="435f2-254">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
