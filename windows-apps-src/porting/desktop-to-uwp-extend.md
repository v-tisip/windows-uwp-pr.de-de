---
author: normesta
Description: Extend your desktop application with Windows UIs and components
Search.Product: eADQiWindows 10XVcnh
title: Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten
ms.author: normesta
ms.date: 06/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: bed06d5f9f43acd5aa4ec5ff7b2b7139ad0dd26f
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4353471"
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a><span data-ttu-id="7441a-103">Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten</span><span class="sxs-lookup"><span data-stu-id="7441a-103">Extend your desktop application with modern UWP components</span></span>

<span data-ttu-id="7441a-104">Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7441a-104">Some Windows 10 experiences (For example: a touch-enabled UI page) must run inside of a modern app container .</span></span> <span data-ttu-id="7441a-105">Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um UWP-Projekte und die Komponente für Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="7441a-105">If you want to add these experiences, extend your desktop application with UWP projects and Windows Runtime Components.</span></span>

<span data-ttu-id="7441a-106">In vielen Fällen können Sie die UWP-APIs direkt aus Ihrer Desktopanwendung aufrufen. Bevor Sie dieses Handbuch lesen, lesen Sie [Für Windows10 verbessern](desktop-to-uwp-enhance.md).</span><span class="sxs-lookup"><span data-stu-id="7441a-106">In many cases you can call UWP APIs directly from your desktop application, so before you review this guide, see [Enhance for Windows 10](desktop-to-uwp-enhance.md).</span></span>

>[!NOTE]
><span data-ttu-id="7441a-107">Dieses Handbuch wird davon ausgegangen, dass Sie ein Windows-app-Paket für Ihre desktop-Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7441a-107">This guide assumes that you've created a Windows app package for your desktop application.</span></span> <span data-ttu-id="7441a-108">Wenn Sie dies noch nicht geschehen, finden Sie unter [Paket-desktopanwendungen](desktop-to-uwp-root.md).</span><span class="sxs-lookup"><span data-stu-id="7441a-108">If you haven't yet done this, see [Package desktop applications](desktop-to-uwp-root.md).</span></span>

<span data-ttu-id="7441a-109">Wenn Sie bereit sind, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="7441a-109">If you're ready, let's start.</span></span>

<a id="setup" />

## <a name="first-setup-your-solution"></a><span data-ttu-id="7441a-110">Ihre Projektmappe einrichten</span><span class="sxs-lookup"><span data-stu-id="7441a-110">First, setup your Solution</span></span>

<span data-ttu-id="7441a-111">Fügen Sie Ihrer Projektmappe ein oder mehrere UWP-Projekte und Laufzeitkomponenten hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-111">Add one or more UWP projects and runtime components to your solution.</span></span>

<span data-ttu-id="7441a-112">Beginnen Sie mit einer Projektmappe, die ein **Paketerstellungsprojekt für Windows-Anwendungen** mit einem Verweis auf Ihre Desktop-Anwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="7441a-112">Start with a solution that contains a **Windows Application Packaging Project** with a reference to your desktop application.</span></span>

<span data-ttu-id="7441a-113">Diese Abbildung zeigt ein Beispiel für eine Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="7441a-113">This image shows an example solution.</span></span>

![Erweitern des Startprojekts](images/desktop-to-uwp/extend-start-project.png)

<span data-ttu-id="7441a-115">Wenn Ihre Projektmappe paketprojekt enthält, finden Sie unter [Package Ihrer desktop-Anwendung mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="7441a-115">If your solution doesn't contain a packaging project, see [Package your desktop application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

### <a name="add-a-uwp-project"></a><span data-ttu-id="7441a-116">Hinzufügen eines UWP-Projekts</span><span class="sxs-lookup"><span data-stu-id="7441a-116">Add a UWP project</span></span>

<span data-ttu-id="7441a-117">Fügen Sie der Projektmappe eine **Leere App (Universelle Windows-App)** hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-117">Add a **Blank App (Universal Windows)** to your solution.</span></span>

<span data-ttu-id="7441a-118">Hier erstellen Sie eine moderne XAML-Benutzeroberfläche oder verwenden APIs, die nur innerhalb eines UWP-Prozesses ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7441a-118">This is where you'll build a modern XAML UI or use APIs that run only within a UWP process.</span></span>

![UWP-Projekt](images/desktop-to-uwp/add-uwp-project-to-solution.png)

<span data-ttu-id="7441a-120">Klicken Sie in Ihrem Paketerstellungsprojekt mit der rechten Maustaste auf den Knoten **Anwendungen**, und klicken Sie dann auf **Verweis hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="7441a-120">In your packaging project, right-click the **Applications** node, and then click **Add Reference**.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/add-uwp-project-reference.png)

<span data-ttu-id="7441a-122">Fügen Sie einen Verweis auf das UWP-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-122">Then, add a reference the UWP project.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/choose-uwp-project.png)

<span data-ttu-id="7441a-124">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7441a-124">Your solution will look something like this:</span></span>

![Projektmappe mit UWP-Projekt](images/desktop-to-uwp/uwp-project-reference.png)

### <a name="optional-add-a-windows-runtime-component"></a><span data-ttu-id="7441a-126">(Optional) Komponente für Windows-Runtime hinzufügen</span><span class="sxs-lookup"><span data-stu-id="7441a-126">(Optional) Add a Windows Runtime Component</span></span>

<span data-ttu-id="7441a-127">Um einige Szenarien zu erreichen, müssen Sie einer Komponente für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-127">To accomplish some scenarios, you'll have to add code to a Windows Runtime Component.</span></span>

![Runtime-Komponente App-Dienst](images/desktop-to-uwp/add-runtime-component.png)

<span data-ttu-id="7441a-129">Fügen Sie dann in Ihrem UWP-Projekt einen Verweis auf die Laufzeitkomponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-129">Then, from your UWP project, add a reference to the runtime component.</span></span> <span data-ttu-id="7441a-130">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7441a-130">Your solution will look something like this:</span></span>

![Verweis auf die Laufzeitkomponente](images/desktop-to-uwp/runtime-component-reference.png)

<span data-ttu-id="7441a-132">Werfen wir einen Blick auf einige Dinge, die Sie mit Ihren UWP-Projekten und Laufzeitkomponenten tun können.</span><span class="sxs-lookup"><span data-stu-id="7441a-132">Let's take a look at a few things you can do with your UWP projects and runtime components.</span></span>

## <a name="show-a-modern-xaml-ui"></a><span data-ttu-id="7441a-133">Anzeigen einer modernen XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="7441a-133">Show a modern XAML UI</span></span>

<span data-ttu-id="7441a-134">Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren.</span><span class="sxs-lookup"><span data-stu-id="7441a-134">As part of your application flow, you can incorporate modern XAML-based user interfaces into your desktop application.</span></span> <span data-ttu-id="7441a-135">Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="7441a-135">These user interfaces are naturally adaptive to different screen sizes and resolutions and support modern interactive models such as touch and ink.</span></span>

<span data-ttu-id="7441a-136">Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7441a-136">For example, with a small amount of XAML markup, you can give users with powerful map-related visualization features.</span></span>

<span data-ttu-id="7441a-137">Diese Abbildungzeigt eine Windows Forms-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.</span><span class="sxs-lookup"><span data-stu-id="7441a-137">This image shows a Windows Forms application that opens a XAML-based modern UI that contains a map control.</span></span>

![adaptives Design](images/desktop-to-uwp/extend-xaml-ui.png)

>[!NOTE]
><span data-ttu-id="7441a-139">Dieses Beispiel zeigt eine XAML-UI durch ein UWP-Projekt der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-139">This example shows a XAML UI by adding a UWP project to the solution.</span></span> <span data-ttu-id="7441a-140">Dies ist der stabil unterstützten Ansatz zum Anzeigen von XAML-Benutzeroberflächen in einer desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="7441a-140">That is the stable supported approach to showing XAML UIs in a desktop application.</span></span> <span data-ttu-id="7441a-141">Die Alternative dieses Ansatzes ist Sie UWP-XAML-Steuerelemente mithilfe von einer XAML-Insel direkt an Ihre desktop-Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-141">The alternative to this approach is to add UWP XAML controls directly to your desktop application by using a XAML Island.</span></span> <span data-ttu-id="7441a-142">XAML-Inseln sind als Entwicklervorschau derzeit verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7441a-142">XAML Islands are currently available as a developer preview.</span></span> <span data-ttu-id="7441a-143">Obwohl wir Sie Sie diese in Ihrem eigenen Code Prototyp ausprobieren können, jetzt dazu ermutigen, empfohlen nicht, dass Sie sie in Produktionscode zu diesem Zeitpunkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="7441a-143">Although we encourage you to try them out in your own prototype code now, we do not recommend that you use them in production code at this time.</span></span> <span data-ttu-id="7441a-144">Diese APIs und Steuerelemente werden weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen.</span><span class="sxs-lookup"><span data-stu-id="7441a-144">These APIs and controls will continue to mature and stabilize in future Windows releases.</span></span> <span data-ttu-id="7441a-145">Weitere Informationen zu XAML-Inseln, finden Sie in [UWP-Steuerelemente in desktop-Apps](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)</span><span class="sxs-lookup"><span data-stu-id="7441a-145">To learn more about XAML Islands, see [UWP controls in desktop applications](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="7441a-146">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="7441a-146">The design pattern</span></span>

<span data-ttu-id="7441a-147">Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="7441a-147">To show a XAML-based UI, do these things:</span></span>

<span data-ttu-id="7441a-148">:one: [Einrichten Ihrer Projektmappe](#solution-setup)</span><span class="sxs-lookup"><span data-stu-id="7441a-148">:one: [Setup your Solution](#solution-setup)</span></span>

<span data-ttu-id="7441a-149">:two: [Erstellen einer XAML-Benutzeroberfläche](#xaml-UI)</span><span class="sxs-lookup"><span data-stu-id="7441a-149">:two: [Create a XAML UI](#xaml-UI)</span></span>

<span data-ttu-id="7441a-150">:three: [Hinzufügen einer Protokollerweiterung zum UWP-Projekt](#protocol)</span><span class="sxs-lookup"><span data-stu-id="7441a-150">:three: [Add a protocol extension to the UWP project](#protocol)</span></span>

<span data-ttu-id="7441a-151">:four: [Starten der UWP-App aus Ihrer Desktop-App](#start)</span><span class="sxs-lookup"><span data-stu-id="7441a-151">:four: [Start the UWP app from your desktop app](#start)</span></span>

<span data-ttu-id="7441a-152">:five: [Anzeigen der gewünschten Seite im UWP-Projekt](#parse)</span><span class="sxs-lookup"><span data-stu-id="7441a-152">:five: [In the UWP project, show the page that you want](#parse)</span></span>

<a id="solution-setup" />

### <a name="setup-your-solution"></a><span data-ttu-id="7441a-153">Einrichten Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="7441a-153">Setup your Solution</span></span>

<span data-ttu-id="7441a-154">Allgemeine Anleitungen zum Einrichten Ihrer Projektmappe finden Sie im Abschnitt [Ihre Projektmappe einrichten](#setup) am Anfang dieses Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="7441a-154">For general guidance on how to set your solution up, see the [First, setup your Solution](#setup) section at the beginning of this guide.</span></span>

<span data-ttu-id="7441a-155">Ihre Projektmappe sieht in etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7441a-155">Your solution would look something like this:</span></span>

![Projektmappe für eine XAML-Benutzeroberfläche](images/desktop-to-uwp/xaml-ui-solution.png)

<span data-ttu-id="7441a-157">In diesem Beispiel heißt das Windows Forms-Projekt **Landmarks**, und das UWP-Projekt, das die XAML-Benutzeroberfläche enthält, heißt **MapUI**.</span><span class="sxs-lookup"><span data-stu-id="7441a-157">In this example, the Windows Forms project is named **Landmarks** and the UWP project that contains the XAML UI is named **MapUI**.</span></span>

<a id="xaml-UI" />

### <a name="create-a-xaml-ui"></a><span data-ttu-id="7441a-158">Erstellen einer XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="7441a-158">Create a XAML UI</span></span>

<span data-ttu-id="7441a-159">Fügen Sie Ihrem UWP-Projekt eine XAML-Benutzeroberfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-159">Add a XAML UI to your UWP project.</span></span> <span data-ttu-id="7441a-160">Hier sehen Sie den XAML-Code für eine grundlegende Karte.</span><span class="sxs-lookup"><span data-stu-id="7441a-160">Here's the XAML for a basic map.</span></span>

```xml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" Margin="12,20,12,14">
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto"/>
        <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <maps:MapControl x:Name="myMap" Grid.Column="0" Width="500" Height="500"
                     ZoomLevel="{Binding ElementName=zoomSlider,Path=Value, Mode=TwoWay}"
                     Heading="{Binding ElementName=headingSlider,Path=Value, Mode=TwoWay}"
                     DesiredPitch="{Binding ElementName=desiredPitchSlider,Path=Value, Mode=TwoWay}"    
                     HorizontalAlignment="Left"               
                     MapServiceToken="<Your Key Goes Here" />
    <Grid Grid.Column="1" Margin="12">
        <StackPanel>
            <Slider Minimum="1" Maximum="20" Header="ZoomLevel" Name="zoomSlider" Value="17.5"/>
            <Slider Minimum="0" Maximum="360" Header="Heading" Name="headingSlider" Value="0"/>
            <Slider Minimum="0" Maximum="64" Header=" DesiredPitch" Name="desiredPitchSlider" Value="32"/>
        </StackPanel>
    </Grid>
</Grid>
```

### <a name="add-a-protocol-extension"></a><span data-ttu-id="7441a-161">Hinzufügen einer Protokollerweiterung</span><span class="sxs-lookup"><span data-stu-id="7441a-161">Add a protocol extension</span></span>

<span data-ttu-id="7441a-162">Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie diese Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-162">In **Solution Explorer**, open the **package.appxmanifest** file of the Packaging project in your solution, and add this extension.</span></span>

```xml
<Extensions>
  <uap:Extension Category="windows.protocol" Executable="MapUI.exe" EntryPoint="MapUI.App">
    <uap:Protocol Name="xamluidemo" />
  </uap:Extension>
</Extensions>    
```

<span data-ttu-id="7441a-163">Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="7441a-163">Give the protocol a name, provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span>

<span data-ttu-id="7441a-164">Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-164">You can also open the **package.appxmanifest** in the designer, choose the **Declarations** tab, and then add the extension there.</span></span>

![Deklarationen-Registerkarte](images/desktop-to-uwp/protocol-properties.png)

> [!NOTE]
> <span data-ttu-id="7441a-166">Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-166">Map controls download data from the internet so if you use one, you'll have to add the "internet client" capability to your manifest as well.</span></span>

<a id="start" />

### <a name="start-the-uwp-app"></a><span data-ttu-id="7441a-167">Starten der UWP-App</span><span class="sxs-lookup"><span data-stu-id="7441a-167">Start the UWP app</span></span>

<span data-ttu-id="7441a-168">Erstellen Sie zunächst in Ihrer Desktop-Anwendung eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx), die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7441a-168">First, from your desktop application, create a [Uri](https://msdn.microsoft.com/library/system.uri.aspx) that includes the protocol name and any parameters you want to pass into the UWP app.</span></span> <span data-ttu-id="7441a-169">Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="7441a-169">Then, call the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync) method.</span></span>

```csharp

private void Statue_Of_Liberty_Click(object sender, EventArgs e)
{
    ShowMap(40.689247, -74.044502);
}

private async void ShowMap(double lat, double lon)
{
    string str = "xamluidemo://";

    Uri uri = new Uri(str + "location?lat=" +
        lat.ToString() + "&?lon=" + lon.ToString());

    var success = await Windows.System.Launcher.LaunchUriAsync(uri);

}
```

<a id="parse" />

### <a name="parse-parameters-and-show-a-page"></a><span data-ttu-id="7441a-170">Analysieren von Parametern und Anzeigen einer Seite</span><span class="sxs-lookup"><span data-stu-id="7441a-170">Parse parameters and show a page</span></span>

<span data-ttu-id="7441a-171">In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="7441a-171">In the **App** class of your UWP project, override the **OnActivated** event handler.</span></span> <span data-ttu-id="7441a-172">Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter, und öffnen Sie die gewünschte Seite.</span><span class="sxs-lookup"><span data-stu-id="7441a-172">If the app is activated by your protocol, parse the parameters and then open the page that you want.</span></span>

```csharp
protected override void OnActivated(Windows.ApplicationModel.Activation.IActivatedEventArgs e)
{
    if (e.Kind == ActivationKind.Protocol)
    {
        ProtocolActivatedEventArgs protocolArgs = (ProtocolActivatedEventArgs)e;
        Uri uri = protocolArgs.Uri;
        if (uri.Scheme == "xamluidemo")
        {
            Frame rootFrame = new Frame();
            Window.Current.Content = rootFrame;
            rootFrame.Navigate(typeof(MainPage), uri.Query);
            Window.Current.Activate();
        }
    }
}
```

<span data-ttu-id="7441a-173">Überschreiben Sie die Methode ``OnNavigatedTo``, um die in die Seite übergebenen Parameter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7441a-173">Override the ``OnNavigatedTo`` method to use the parameters passed into the page.</span></span> <span data-ttu-id="7441a-174">In diesem Fall verwenden wir den Breiten- und Längengrad, die in diese Seite übergeben wurden, um einen Standort in einer Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7441a-174">In this case, we'll use the latitude and longitude that were passed into this page to show a location in a map.</span></span>

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
 {
     if (e.Parameter != null)
     {
         WwwFormUrlDecoder decoder = new WwwFormUrlDecoder(e.Parameter.ToString());

         double lat = Convert.ToDouble(decoder[0].Value);
         double lon = Convert.ToDouble(decoder[1].Value);

         BasicGeoposition pos = new BasicGeoposition();

         pos.Latitude = lat;
         pos.Longitude = lon;

         myMap.Center = new Geopoint(pos);

         myMap.Style = MapStyle.Aerial3D;

     }

     base.OnNavigatedTo(e);
 }
```

### <a name="similar-samples"></a><span data-ttu-id="7441a-175">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="7441a-175">Similar Samples</span></span>

[<span data-ttu-id="7441a-176">Hinzufügen einer UWP-XAML-Benutzererfahrung zu einer VB6-Anwendung</span><span class="sxs-lookup"><span data-stu-id="7441a-176">Adding a UWP XAML user experience to VB6 Application</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/VB6withXaml)

[<span data-ttu-id="7441a-177">Northwind-Beispiel: End-to-end-Beispiel für UWA-UI- und Win32-Legacy-Code</span><span class="sxs-lookup"><span data-stu-id="7441a-177">Northwind sample: End-to-end example for UWA UI & Win32 legacy code</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/NorthwindSample)

[<span data-ttu-id="7441a-178">Northwind-Beispiel: UWP-App, die eine Verbindung zu SQL Server herstellt</span><span class="sxs-lookup"><span data-stu-id="7441a-178">Northwind sample: UWP app connecting to SQL Server</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SQLServer)

## <a name="provide-services-to-other-apps"></a><span data-ttu-id="7441a-179">Dienste für andere Apps</span><span class="sxs-lookup"><span data-stu-id="7441a-179">Provide services to other apps</span></span>

<span data-ttu-id="7441a-180">Sie fügen einen Dienst hinzu, der von anderen Apps genutzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7441a-180">You add a service that other apps can consume.</span></span> <span data-ttu-id="7441a-181">Beispielsweise können Sie einen Dienst hinzufügen, der anderen Apps kontrollierten Zugriff auf die Datenbank hinter der App bietet.</span><span class="sxs-lookup"><span data-stu-id="7441a-181">For example, you can add a service that gives other apps controlled access to the database behind your app.</span></span> <span data-ttu-id="7441a-182">Durch die Implementierung einer Hintergrundaufgabe, können apps den Dienst erreichen, selbst wenn Ihre desktop-Anwendung nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7441a-182">By implementing a background task, apps can reach the service even if your desktop application is not running.</span></span>

<span data-ttu-id="7441a-183">Hier ist ein Beispiel dafür.</span><span class="sxs-lookup"><span data-stu-id="7441a-183">Here's a sample that does this.</span></span>

![adaptives Design](images/desktop-to-uwp/winforms-app-service.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="7441a-185">Sehen Sie sich die App näher an</span><span class="sxs-lookup"><span data-stu-id="7441a-185">Have a closer look at this app</span></span>

<span data-ttu-id="7441a-186">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span><span class="sxs-lookup"><span data-stu-id="7441a-186">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/winforms-appservice/9p7d9b6nk5tn)</span></span>

<span data-ttu-id="7441a-187">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span><span class="sxs-lookup"><span data-stu-id="7441a-187">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinformsAppService)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="7441a-188">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="7441a-188">The design pattern</span></span>

<span data-ttu-id="7441a-189">Um einen Dienst bereitzustellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="7441a-189">To show provide a service, do these things:</span></span>

<span data-ttu-id="7441a-190">:one: [Implementieren des App-Diensts](#appservice)</span><span class="sxs-lookup"><span data-stu-id="7441a-190">:one: [Implement the app service](#appservice)</span></span>

<span data-ttu-id="7441a-191">:two: [Hinzufügen einer App-Diensterweiterung](#extension)</span><span class="sxs-lookup"><span data-stu-id="7441a-191">:two: [Add an app service extension](#extension)</span></span>

<span data-ttu-id="7441a-192">:three: [Testen des App-Dienstes](#test)</span><span class="sxs-lookup"><span data-stu-id="7441a-192">:three: [Test the app service](#test)</span></span>

<a id="appservice" />

### <a name="implement-the-app-service"></a><span data-ttu-id="7441a-193">Implementieren des App-Diensts</span><span class="sxs-lookup"><span data-stu-id="7441a-193">Implement the app service</span></span>

<span data-ttu-id="7441a-194">Hier erfahren Sie, wo Sie Anforderungen von anderen Apps überprüfen und behandeln.</span><span class="sxs-lookup"><span data-stu-id="7441a-194">Here's where you'll validate and handle requests from other apps.</span></span> <span data-ttu-id="7441a-195">Fügen Sie diesen Code einer Komponente für Windows-Runtime in Ihrer Projektmappe hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-195">Add this code to a Windows Runtime Component in your solution.</span></span>

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

### <a name="add-an-app-service-extension-to-the-packaging-project"></a><span data-ttu-id="7441a-196">Hinzufügen einer app-diensterweiterung zum verpackungsprojekt</span><span class="sxs-lookup"><span data-stu-id="7441a-196">Add an app service extension to the Packaging project</span></span>

<span data-ttu-id="7441a-197">Öffnen Sie die Datei **"Package.appxmanifest"** des Verpackung-Projekts, und fügen Sie eine app-diensterweiterung zu den ``<Application>`` Element.</span><span class="sxs-lookup"><span data-stu-id="7441a-197">Open the **package.appxmanifest** file of the Packaging project, and add an app service extension to the ``<Application>`` element.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.appService"
          EntryPoint="AppServiceComponent.AppServiceTask">
        <uap:AppService Name="com.microsoft.samples.winforms" />
      </uap:Extension>
    </Extensions>    
```
<span data-ttu-id="7441a-198">Benennen Sie den App-Dienst und geben Sie den Namen der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="7441a-198">Give the app service a name and provide the name of the entry point class.</span></span> <span data-ttu-id="7441a-199">Dies ist die Klasse, in der Sie den Dienst implementiert haben.</span><span class="sxs-lookup"><span data-stu-id="7441a-199">This is the class in which you implemented the service.</span></span>

<a id="test" />

### <a name="test-the-app-service"></a><span data-ttu-id="7441a-200">Testen des App-Dienstes</span><span class="sxs-lookup"><span data-stu-id="7441a-200">Test the app service</span></span>

<span data-ttu-id="7441a-201">Testen Sie Ihren Dienst durch Aufrufen aus einer anderen App.</span><span class="sxs-lookup"><span data-stu-id="7441a-201">Test your service by calling it from another app.</span></span> <span data-ttu-id="7441a-202">Dieser Code kann eine desktop-Anwendung wie z. B. eine Windows Forms-Anwendung oder eine andere UWP-app sein.</span><span class="sxs-lookup"><span data-stu-id="7441a-202">This code can be a desktop application such as a Windows forms application or another UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="7441a-203">Dieser Code funktioniert nur, wenn Sie die ``PackageFamilyName``-Eigenschaft der ``AppServiceConnection``-Klasse richtig festlegen.</span><span class="sxs-lookup"><span data-stu-id="7441a-203">This code only works if you properly set the ``PackageFamilyName`` property of the ``AppServiceConnection`` class.</span></span> <span data-ttu-id="7441a-204">Sie erhalten diesen Namen, wenn Sie ``Windows.ApplicationModel.Package.Current.Id.FamilyName`` im Kontext des UWP-Projekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7441a-204">You can get that name by calling ``Windows.ApplicationModel.Package.Current.Id.FamilyName`` in the context of the UWP project.</span></span> <span data-ttu-id="7441a-205">Siehe [Erstellen und Verwenden eines App-Dienstes](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="7441a-205">See [Create and consume an app service](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>

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

<span data-ttu-id="7441a-206">Erfahren Sie hier mehr über App-Dienste: [Erstellen und Verwenden eines App-Diensts](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="7441a-206">Learn more about app services here: [Create and consume an app service](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>

### <a name="similar-samples"></a><span data-ttu-id="7441a-207">Ähnliche Beispiele</span><span class="sxs-lookup"><span data-stu-id="7441a-207">Similar Samples</span></span>

[<span data-ttu-id="7441a-208">Beispiel für App-Dienst-Brücke</span><span class="sxs-lookup"><span data-stu-id="7441a-208">App service bridge sample</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample)

[<span data-ttu-id="7441a-209">Beispiel für App-Dienst Brücke mit eine C++ Win32-App</span><span class="sxs-lookup"><span data-stu-id="7441a-209">App service bridge sample with C++ win32 app</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/AppServiceBridgeSample_C%2B%2B)

[<span data-ttu-id="7441a-210">MFC-Anwendung, die Pushbenachrichtigungen empfängt.</span><span class="sxs-lookup"><span data-stu-id="7441a-210">MFC application that receives push notifications</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/MFCwithPush)


## <a name="making-your-desktop-application-a-share-target"></a><span data-ttu-id="7441a-211">Ihre Desktopanwendung als Freigabeziel gestalten</span><span class="sxs-lookup"><span data-stu-id="7441a-211">Making your desktop application a share target</span></span>

<span data-ttu-id="7441a-212">Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7441a-212">You can make your desktop application a share target so that users can easily share data such as pictures from other apps that support sharing.</span></span>

<span data-ttu-id="7441a-213">Beispielsweise können Benutzer Ihre Anwendung zum Teilen von Bildern in Microsoft Edge, die Fotos-app auswählen.</span><span class="sxs-lookup"><span data-stu-id="7441a-213">For example, users could choose your application to share pictures from Microsoft Edge, the Photos app.</span></span> <span data-ttu-id="7441a-214">Hier ist eine WPF-Beispiel-Anwendung, die diese Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="7441a-214">Here's a WPF sample application that has that capability.</span></span>

![Freigabeziel](images/desktop-to-uwp/share-target.png)

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="7441a-216">Sehen Sie sich diese App näher an</span><span class="sxs-lookup"><span data-stu-id="7441a-216">Have a closer look at this app</span></span>

<span data-ttu-id="7441a-217">:heavy_check_mark: [App abrufen](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span><span class="sxs-lookup"><span data-stu-id="7441a-217">:heavy_check_mark: [Get the app](https://www.microsoft.com/en-us/store/p/wpf-app-as-sharetarget/9pjcjljlck37)</span></span>

<span data-ttu-id="7441a-218">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span><span class="sxs-lookup"><span data-stu-id="7441a-218">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WPFasShareTarget)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="7441a-219">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="7441a-219">The design pattern</span></span>

<span data-ttu-id="7441a-220">Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="7441a-220">To make your application a share target, do these things:</span></span>

<span data-ttu-id="7441a-221">:one: [Hinzufügen der Freigabezielerweiterung](#share-extension)</span><span class="sxs-lookup"><span data-stu-id="7441a-221">:one: [Add a share target extension](#share-extension)</span></span>

<span data-ttu-id="7441a-222">:two: [Überschreiben des OnNavigatedTo-Ereignishandlers](#override)</span><span class="sxs-lookup"><span data-stu-id="7441a-222">:two: [Override the OnNavigatedTo event handler](#override)</span></span>

<a id="share-extension" />

### <a name="add-a-share-target-extension"></a><span data-ttu-id="7441a-223">Hinzufügen der Freigabezielerweiterung</span><span class="sxs-lookup"><span data-stu-id="7441a-223">Add a share target extension</span></span>

<span data-ttu-id="7441a-224">Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie die Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-224">In **Solution Explorer**, open the **package.appxmanifest** file of the Packaging project in your solution and add the extension.</span></span>

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

<span data-ttu-id="7441a-225">Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse.</span><span class="sxs-lookup"><span data-stu-id="7441a-225">Provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span> <span data-ttu-id="7441a-226">Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können.</span><span class="sxs-lookup"><span data-stu-id="7441a-226">You'll also have to specify what types of files can be shared with your app.</span></span>

<a id="override" />

### <a name="override-the-onnavigatedto-event-handler"></a><span data-ttu-id="7441a-227">Überschreiben des OnNavigatedTo-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="7441a-227">Override the OnNavigatedTo event handler</span></span>

<span data-ttu-id="7441a-228">Überschreiben Sie den **OnNavigatedTo**-Ereignishandler in der **App** Klasse des UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="7441a-228">Override the **OnNavigatedTo** event handler in the **App** class of your UWP project.</span></span>

<span data-ttu-id="7441a-229">Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.</span><span class="sxs-lookup"><span data-stu-id="7441a-229">This event handler is called when users choose your app to share their files.</span></span>

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

## <a name="create-a-background-task"></a><span data-ttu-id="7441a-230">Erstellen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7441a-230">Create a background task</span></span>

<span data-ttu-id="7441a-231">Sie fügen eine Hintergrundaufgaben hinzu, um selbst dann App-Code auszuführen, wenn die App angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="7441a-231">You add a background task to run code even when the app is suspended.</span></span> <span data-ttu-id="7441a-232">Hintergrundaufgaben sind ideal für kleine Aufgaben, die keine Benutzerinteraktion erfordern.</span><span class="sxs-lookup"><span data-stu-id="7441a-232">Background tasks are great for small tasks that don't require the user interaction.</span></span> <span data-ttu-id="7441a-233">Beispielsweise kann Ihre Aufgabe E-Mails herunterladen, eine Popupbenachrichtigung über eine eingehende Chatnachricht zeigen oder auf eine Änderung in einer Systembedingung reagieren.</span><span class="sxs-lookup"><span data-stu-id="7441a-233">For example, your task can download mail, show a toast notification about an incoming chat message, or react to a change in a system condition.</span></span>

<span data-ttu-id="7441a-234">Hier ist eine WPF-Beispiel-Anwendung, die eine Hintergrundaufgabe registriert.</span><span class="sxs-lookup"><span data-stu-id="7441a-234">Here's a WPF sample application that registers a background task.</span></span>

![hintergrundaufgabe](images/desktop-to-uwp/sample-background-task.png)

<span data-ttu-id="7441a-236">Die Aufgabe stellt eine HTTP-Anforderung und misst die Zeit, die die Anforderung benötigt, um eine Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="7441a-236">The task makes an http request and measures the time that it takes for the request to return a response.</span></span> <span data-ttu-id="7441a-237">Ihre Aufgaben werden wahrscheinlich viel interessanter sein, aber dieses Beispiel eignet sich gut, um die grundlegende Funktionsweise einer Hintergrundaufgabe zu lernen.</span><span class="sxs-lookup"><span data-stu-id="7441a-237">Your tasks will likely be much more interesting, but this sample is great for learning the basic mechanics of a background task.</span></span>

### <a name="have-a-closer-look-at-this-app"></a><span data-ttu-id="7441a-238">Sehen Sie sich diese App näher an</span><span class="sxs-lookup"><span data-stu-id="7441a-238">Have a closer look at this app</span></span>

<span data-ttu-id="7441a-239">:heavy_check_mark: [Code anzeigen](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask)</span><span class="sxs-lookup"><span data-stu-id="7441a-239">:heavy_check_mark: [Browse the code](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="7441a-240">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="7441a-240">The design pattern</span></span>

<span data-ttu-id="7441a-241">Um einen Hintergrunddienst zu erstellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="7441a-241">To create a background service, do these things:</span></span>

<span data-ttu-id="7441a-242">:one: [Implementieren der Hintergrundaufgabe](#implement-task)</span><span class="sxs-lookup"><span data-stu-id="7441a-242">:one: [Implement the background task](#implement-task)</span></span>

<span data-ttu-id="7441a-243">:two: [Konfigurieren der Hintergrundaufgabe](#configure-background-task)</span><span class="sxs-lookup"><span data-stu-id="7441a-243">:two: [Configure the background task](#configure-background-task)</span></span>

<span data-ttu-id="7441a-244">:three: [Registrieren der Hintergrundaufgabe](#register-background-task)</span><span class="sxs-lookup"><span data-stu-id="7441a-244">:three: [Register the background task](#register-background-task)</span></span>

<a id="implement-task" />

### <a name="implement-the-background-task"></a><span data-ttu-id="7441a-245">Implementieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7441a-245">Implement the background task</span></span>

<span data-ttu-id="7441a-246">Implementieren Sie die Hintergrundaufgabe, indem Sie einem Komponentenprojekt für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7441a-246">Implement the background task by adding code to a Windows Runtime component project.</span></span>

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

### <a name="configure-the-background-task"></a><span data-ttu-id="7441a-247">Konfigurieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7441a-247">Configure the background task</span></span>

<span data-ttu-id="7441a-248">Öffnen Sie im manifest-Designer die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Lösung.</span><span class="sxs-lookup"><span data-stu-id="7441a-248">In the manifest designer, open the **package.appxmanifest** file of the Packaging project in your solution.</span></span>

<span data-ttu-id="7441a-249">Fügen Sie auf der Registerkarte **Deklarationen** eine **Hintergrundaufgaben**-Deklaration hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-249">In the **Declarations** tab, add a **Background Tasks** declaration.</span></span>

![Hintergrundaufgaben-Option](images/desktop-to-uwp/background-task-option.png)

<span data-ttu-id="7441a-251">Wählen Sie dann die gewünschten Eigenschaften aus.</span><span class="sxs-lookup"><span data-stu-id="7441a-251">Then, choose the desired properties.</span></span> <span data-ttu-id="7441a-252">Unser Beispiel verwendet die **Timer**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="7441a-252">Our sample uses the **Timer** property.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/timer-property.png)

<span data-ttu-id="7441a-254">Geben Sie den vollqualifizierten Namen der Klasse in der Komponente für Windows-Runtime, die die Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="7441a-254">Provide the fully qualified name of the class in your Windows Runtime Component that implements the background task.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/background-task-entry-point.png)

<a id="register-background-task" />

### <a name="register-the-background-task"></a><span data-ttu-id="7441a-256">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="7441a-256">Register the background task</span></span>

<span data-ttu-id="7441a-257">Fügen Sie Ihrem Projekt für die Desktop-Anwendung, das die Hintergrundaufgabe registriert, Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="7441a-257">Add code to your desktop application project that registers the background task.</span></span>

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
## <a name="support-and-feedback"></a><span data-ttu-id="7441a-258">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="7441a-258">Support and feedback</span></span>

**<span data-ttu-id="7441a-259">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="7441a-259">Find answers to your questions</span></span>**

<span data-ttu-id="7441a-260">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="7441a-260">Have questions?</span></span> <span data-ttu-id="7441a-261">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="7441a-261">Ask us on Stack Overflow.</span></span> <span data-ttu-id="7441a-262">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="7441a-262">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="7441a-263">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="7441a-263">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="7441a-264">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="7441a-264">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="7441a-265">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="7441a-265">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
