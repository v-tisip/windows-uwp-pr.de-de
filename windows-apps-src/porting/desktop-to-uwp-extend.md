---
author: normesta
Description: Extend your desktop application with Windows UIs and components
Search.Product: eADQiWindows 10XVcnh
title: Erweitern Sie Ihre Desktopanwendung mit Windows-Benutzeroberflächen und -Komponenten
ms.author: normesta
ms.date: 06/08/2018
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 1806a24d2f84b5d3e1eeff6c5b3f7900360de3e4
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5888406"
---
# <a name="extend-your-desktop-application-with-modern-uwp-components"></a><span data-ttu-id="58498-103">Erweitern Sie Ihre Desktopanwendung mit modernen Windows-UWP-Komponenten</span><span class="sxs-lookup"><span data-stu-id="58498-103">Extend your desktop application with modern UWP components</span></span>

<span data-ttu-id="58498-104">Einige Windows 10-Funktionen (z. B. eine touchfähige UI-Seite) müssen innerhalb eines Modern-App-Containers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="58498-104">Some Windows 10 experiences (For example: a touch-enabled UI page) must run inside of a modern app container .</span></span> <span data-ttu-id="58498-105">Wenn Sie diese Funktionen hinzufügen möchten, erweitern Sie Ihre Desktopanwendung um UWP-Projekte und die Komponente für Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="58498-105">If you want to add these experiences, extend your desktop application with UWP projects and Windows Runtime Components.</span></span>

<span data-ttu-id="58498-106">In vielen Fällen können Sie Windows-Runtime-APIs direkt aus Ihrer Desktopanwendung aufrufen, also bevor Sie dieses Handbuch lesen, finden Sie unter [für Windows 10 verbessern](desktop-to-uwp-enhance.md).</span><span class="sxs-lookup"><span data-stu-id="58498-106">In many cases you can call Windows Runtime APIs directly from your desktop application, so before you review this guide, see [Enhance for Windows 10](desktop-to-uwp-enhance.md).</span></span>

>[!NOTE]
><span data-ttu-id="58498-107">Dieses Handbuch wird davon ausgegangen, dass Sie ein Windows-app-Paket für Ihre desktop-Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="58498-107">This guide assumes that you've created a Windows app package for your desktop application.</span></span> <span data-ttu-id="58498-108">Wenn Sie dies noch nicht geschehen, finden Sie unter [Paket-desktopanwendungen](desktop-to-uwp-root.md).</span><span class="sxs-lookup"><span data-stu-id="58498-108">If you haven't yet done this, see [Package desktop applications](desktop-to-uwp-root.md).</span></span>

<span data-ttu-id="58498-109">Wenn Sie bereit sind, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="58498-109">If you're ready, let's start.</span></span>

<a id="setup" />

## <a name="first-setup-your-solution"></a><span data-ttu-id="58498-110">Ihre Projektmappe einrichten</span><span class="sxs-lookup"><span data-stu-id="58498-110">First, setup your Solution</span></span>

<span data-ttu-id="58498-111">Fügen Sie Ihrer Projektmappe ein oder mehrere UWP-Projekte und Laufzeitkomponenten hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-111">Add one or more UWP projects and runtime components to your solution.</span></span>

<span data-ttu-id="58498-112">Beginnen Sie mit einer Projektmappe, die ein **Paketerstellungsprojekt für Windows-Anwendungen** mit einem Verweis auf Ihre Desktop-Anwendung enthält.</span><span class="sxs-lookup"><span data-stu-id="58498-112">Start with a solution that contains a **Windows Application Packaging Project** with a reference to your desktop application.</span></span>

<span data-ttu-id="58498-113">Diese Abbildung zeigt ein Beispiel für eine Projektmappe.</span><span class="sxs-lookup"><span data-stu-id="58498-113">This image shows an example solution.</span></span>

![Erweitern des Startprojekts](images/desktop-to-uwp/extend-start-project.png)

<span data-ttu-id="58498-115">Wenn Ihre Lösung nicht paketprojekt enthält, finden Sie unter [Package Ihrer desktop-Anwendung mit Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span><span class="sxs-lookup"><span data-stu-id="58498-115">If your solution doesn't contain a packaging project, see [Package your desktop application by using Visual Studio](desktop-to-uwp-packaging-dot-net.md).</span></span>

### <a name="configure-the-desktop-application"></a><span data-ttu-id="58498-116">Konfigurieren Sie die desktop-Anwendung</span><span class="sxs-lookup"><span data-stu-id="58498-116">Configure the desktop application</span></span>

<span data-ttu-id="58498-117">Stellen Sie sicher, dass Ihre desktop-Anwendung Verweise auf die Dateien, die Sie benötigen verfügt, Windows-Runtime-APIs aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="58498-117">Make sure that your desktop application has references to the files that you need to call Windows Runtime APIs.</span></span>

<span data-ttu-id="58498-118">Zu diesem Zweck finden Sie im Abschnitt [zunächst richten Sie Ihr Projekt](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project) des Themas [Erweitern Ihrer desktop-Anwendung für Windows 10](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project).</span><span class="sxs-lookup"><span data-stu-id="58498-118">To do this, see the [First, setup your project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project) section of the topic [Enhance your desktop application for Windows 10](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-enhance#first-set-up-your-project).</span></span>

### <a name="add-a-uwp-project"></a><span data-ttu-id="58498-119">Hinzufügen eines UWP-Projekts</span><span class="sxs-lookup"><span data-stu-id="58498-119">Add a UWP project</span></span>

<span data-ttu-id="58498-120">Fügen Sie der Projektmappe eine **Leere App (Universelle Windows-App)** hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-120">Add a **Blank App (Universal Windows)** to your solution.</span></span>

<span data-ttu-id="58498-121">Hier erstellen Sie eine moderne XAML-Benutzeroberfläche oder verwenden APIs, die nur innerhalb eines UWP-Prozesses ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="58498-121">This is where you'll build a modern XAML UI or use APIs that run only within a UWP process.</span></span>

![UWP-Projekt](images/desktop-to-uwp/add-uwp-project-to-solution.png)

<span data-ttu-id="58498-123">Klicken Sie in Ihrem Paketerstellungsprojekt mit der rechten Maustaste auf den Knoten **Anwendungen**, und klicken Sie dann auf **Verweis hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="58498-123">In your packaging project, right-click the **Applications** node, and then click **Add Reference**.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/add-uwp-project-reference.png)

<span data-ttu-id="58498-125">Fügen Sie einen Verweis auf das UWP-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-125">Then, add a reference the UWP project.</span></span>

![Referenzieren des UWP-Projekts](images/desktop-to-uwp/choose-uwp-project.png)

<span data-ttu-id="58498-127">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="58498-127">Your solution will look something like this:</span></span>

![Projektmappe mit UWP-Projekt](images/desktop-to-uwp/uwp-project-reference.png)

### <a name="optional-add-a-windows-runtime-component"></a><span data-ttu-id="58498-129">(Optional) Komponente für Windows-Runtime hinzufügen</span><span class="sxs-lookup"><span data-stu-id="58498-129">(Optional) Add a Windows Runtime Component</span></span>

<span data-ttu-id="58498-130">Um einige Szenarien zu erreichen, müssen Sie einer Komponente für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-130">To accomplish some scenarios, you'll have to add code to a Windows Runtime Component.</span></span>

![Runtime-Komponente App-Dienst](images/desktop-to-uwp/add-runtime-component.png)

<span data-ttu-id="58498-132">Fügen Sie dann in Ihrem UWP-Projekt einen Verweis auf die Laufzeitkomponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-132">Then, from your UWP project, add a reference to the runtime component.</span></span> <span data-ttu-id="58498-133">Ihre Projektmappe sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="58498-133">Your solution will look something like this:</span></span>

![Verweis auf die Laufzeitkomponente](images/desktop-to-uwp/runtime-component-reference.png)

### <a name="build-your-solution"></a><span data-ttu-id="58498-135">Erstellen Sie die Projektmappe</span><span class="sxs-lookup"><span data-stu-id="58498-135">Build your solution</span></span>

<span data-ttu-id="58498-136">Erstellen Sie die Projektmappe, um sicherzustellen, dass keine Fehler angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="58498-136">Build your solution to ensure that no errors appear.</span></span> <span data-ttu-id="58498-137">Wenn Fehler angezeigt werden, öffnen Sie den **Konfigurations-Manager** und sicherzustellen Sie, dass Ihre Projekte derselben Plattform Ziel.</span><span class="sxs-lookup"><span data-stu-id="58498-137">If you receive errors, open **Configuration Manager** and ensure that your projects target the same platform.</span></span>

![Konfigurations-manager](images/desktop-to-uwp/config-manager.png)

<span data-ttu-id="58498-139">Werfen wir einen Blick auf einige Dinge, die Sie mit Ihren UWP-Projekten und Laufzeitkomponenten tun können.</span><span class="sxs-lookup"><span data-stu-id="58498-139">Let's take a look at a few things you can do with your UWP projects and runtime components.</span></span>

## <a name="show-a-modern-xaml-ui"></a><span data-ttu-id="58498-140">Anzeigen einer modernen XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="58498-140">Show a modern XAML UI</span></span>

<span data-ttu-id="58498-141">Als Teil Ihres Anwendungsflusses können Sie moderne XAML-basierte Benutzeroberflächen in Ihre Desktopanwendung integrieren.</span><span class="sxs-lookup"><span data-stu-id="58498-141">As part of your application flow, you can incorporate modern XAML-based user interfaces into your desktop application.</span></span> <span data-ttu-id="58498-142">Diese Benutzeroberflächen passen sich natürlich an unterschiedliche Bildschirmgrößen und Auflösungen an und unterstützen moderne, interaktive Modelle, z.B. Touch- und Freihandeingaben.</span><span class="sxs-lookup"><span data-stu-id="58498-142">These user interfaces are naturally adaptive to different screen sizes and resolutions and support modern interactive models such as touch and ink.</span></span>

<span data-ttu-id="58498-143">Mit etwas XAML-Markup-Code können Sie z.B. Benutzern leistungsstarke Kartenvisualisierungsfunktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="58498-143">For example, with a small amount of XAML markup, you can give users with powerful map-related visualization features.</span></span>

<span data-ttu-id="58498-144">Diese Abbildungzeigt eine Windows Forms-Anwendung, die eine XAML-basierte, moderne Benutzeroberfläche öffnet, die ein Kartensteuerelement enthält.</span><span class="sxs-lookup"><span data-stu-id="58498-144">This image shows a Windows Forms application that opens a XAML-based modern UI that contains a map control.</span></span>

![adaptives Design](images/desktop-to-uwp/extend-xaml-ui.png)

>[!NOTE]
><span data-ttu-id="58498-146">Dieses Beispiel zeigt eine XAML-UI durch ein UWP-Projekt der Projektmappe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-146">This example shows a XAML UI by adding a UWP project to the solution.</span></span> <span data-ttu-id="58498-147">Dies ist der stabil unterstützten Ansatz zum Anzeigen von XAML-Benutzeroberflächen in einer desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="58498-147">That is the stable supported approach to showing XAML UIs in a desktop application.</span></span> <span data-ttu-id="58498-148">Die Alternative dieses Ansatzes ist mithilfe einer XAML-Insel UWP-XAML-Steuerelemente direkt an Ihre desktop-Anwendung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-148">The alternative to this approach is to add UWP XAML controls directly to your desktop application by using a XAML Island.</span></span> <span data-ttu-id="58498-149">XAML-Inseln sind als Entwicklervorschau derzeit verfügbar.</span><span class="sxs-lookup"><span data-stu-id="58498-149">XAML Islands are currently available as a developer preview.</span></span> <span data-ttu-id="58498-150">Obwohl wir Sie Sie diese in Ihrem eigenen Code Prototyp ausprobieren können, jetzt dazu ermutigen, empfehlen wir nicht, dass Sie sie zu diesem Zeitpunkt in Produktionscode verwenden.</span><span class="sxs-lookup"><span data-stu-id="58498-150">Although we encourage you to try them out in your own prototype code now, we do not recommend that you use them in production code at this time.</span></span> <span data-ttu-id="58498-151">Diese APIs und Steuerelemente werden weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen.</span><span class="sxs-lookup"><span data-stu-id="58498-151">These APIs and controls will continue to mature and stabilize in future Windows releases.</span></span> <span data-ttu-id="58498-152">Weitere Informationen zu XAML-Inseln, finden Sie in [UWP-Steuerelemente in desktop-Apps](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)</span><span class="sxs-lookup"><span data-stu-id="58498-152">To learn more about XAML Islands, see [UWP controls in desktop applications](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="58498-153">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="58498-153">The design pattern</span></span>

<span data-ttu-id="58498-154">Um eine XAML-basierte Benutzeroberfläche anzuzeigen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="58498-154">To show a XAML-based UI, do these things:</span></span>

<span data-ttu-id="58498-155">:one: [Einrichten Ihrer Projektmappe](#solution-setup)</span><span class="sxs-lookup"><span data-stu-id="58498-155">:one: [Setup your Solution](#solution-setup)</span></span>

<span data-ttu-id="58498-156">:two: [Erstellen einer XAML-Benutzeroberfläche](#xaml-UI)</span><span class="sxs-lookup"><span data-stu-id="58498-156">:two: [Create a XAML UI](#xaml-UI)</span></span>

<span data-ttu-id="58498-157">:three: [Hinzufügen einer Protokollerweiterung zum UWP-Projekt](#protocol)</span><span class="sxs-lookup"><span data-stu-id="58498-157">:three: [Add a protocol extension to the UWP project](#protocol)</span></span>

<span data-ttu-id="58498-158">:four: [Starten der UWP-App aus Ihrer Desktop-App](#start)</span><span class="sxs-lookup"><span data-stu-id="58498-158">:four: [Start the UWP app from your desktop app](#start)</span></span>

<span data-ttu-id="58498-159">:five: [Anzeigen der gewünschten Seite im UWP-Projekt](#parse)</span><span class="sxs-lookup"><span data-stu-id="58498-159">:five: [In the UWP project, show the page that you want](#parse)</span></span>

<a id="solution-setup" />

### <a name="setup-your-solution"></a><span data-ttu-id="58498-160">Einrichten Ihrer Projektmappe</span><span class="sxs-lookup"><span data-stu-id="58498-160">Setup your Solution</span></span>

<span data-ttu-id="58498-161">Allgemeine Anleitungen zum Einrichten Ihrer Projektmappe finden Sie im Abschnitt [Ihre Projektmappe einrichten](#setup) am Anfang dieses Handbuchs.</span><span class="sxs-lookup"><span data-stu-id="58498-161">For general guidance on how to set your solution up, see the [First, setup your Solution](#setup) section at the beginning of this guide.</span></span>

<span data-ttu-id="58498-162">Ihre Projektmappe sieht in etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="58498-162">Your solution would look something like this:</span></span>

![Projektmappe für eine XAML-Benutzeroberfläche](images/desktop-to-uwp/xaml-ui-solution.png)

<span data-ttu-id="58498-164">In diesem Beispiel heißt das Windows Forms-Projekt **Landmarks**, und das UWP-Projekt, das die XAML-Benutzeroberfläche enthält, heißt **MapUI**.</span><span class="sxs-lookup"><span data-stu-id="58498-164">In this example, the Windows Forms project is named **Landmarks** and the UWP project that contains the XAML UI is named **MapUI**.</span></span>

<a id="xaml-UI" />

### <a name="create-a-xaml-ui"></a><span data-ttu-id="58498-165">Erstellen einer XAML-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="58498-165">Create a XAML UI</span></span>

<span data-ttu-id="58498-166">Fügen Sie Ihrem UWP-Projekt eine XAML-Benutzeroberfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-166">Add a XAML UI to your UWP project.</span></span> <span data-ttu-id="58498-167">Hier sehen Sie den XAML-Code für eine grundlegende Karte.</span><span class="sxs-lookup"><span data-stu-id="58498-167">Here's the XAML for a basic map.</span></span>

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

### <a name="add-a-protocol-extension"></a><span data-ttu-id="58498-168">Hinzufügen einer Protokollerweiterung</span><span class="sxs-lookup"><span data-stu-id="58498-168">Add a protocol extension</span></span>

<span data-ttu-id="58498-169">Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe, und fügen Sie diese Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-169">In **Solution Explorer**, open the **package.appxmanifest** file of the Packaging project in your solution, and add this extension.</span></span>

```xml
<Extensions>
  <uap:Extension Category="windows.protocol" Executable="MapUI.exe" EntryPoint="MapUI.App">
    <uap:Protocol Name="xamluidemo" />
  </uap:Extension>
</Extensions>    
```

<span data-ttu-id="58498-170">Benennen Sie dem Protokoll einen Namen, geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Name der Einstiegspunkt-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="58498-170">Give the protocol a name, provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span>

<span data-ttu-id="58498-171">Sie können auch das **Package.appxmanifest** im Designer öffnen, die **Deklarationen** Registerkarte wählen und dann dort die Erweiterung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-171">You can also open the **package.appxmanifest** in the designer, choose the **Declarations** tab, and then add the extension there.</span></span>

![Deklarationen-Registerkarte](images/desktop-to-uwp/protocol-properties.png)

> [!NOTE]
> <span data-ttu-id="58498-173">Kartensteuerelemente laden Daten aus dem Internet herunter. Wenn Sie eines verwenden, müssen Sie auch die Funktion „Internetclient“ in Ihrem Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-173">Map controls download data from the internet so if you use one, you'll have to add the "internet client" capability to your manifest as well.</span></span>

<a id="start" />

### <a name="start-the-uwp-app"></a><span data-ttu-id="58498-174">Starten der UWP-App</span><span class="sxs-lookup"><span data-stu-id="58498-174">Start the UWP app</span></span>

<span data-ttu-id="58498-175">Erstellen Sie zunächst in Ihrer Desktop-Anwendung eine [Uri](https://msdn.microsoft.com/library/system.uri.aspx), die den Protokollnamen und alle Parameter enthält, die an die UWP-App übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="58498-175">First, from your desktop application, create a [Uri](https://msdn.microsoft.com/library/system.uri.aspx) that includes the protocol name and any parameters you want to pass into the UWP app.</span></span> <span data-ttu-id="58498-176">Rufen Sie dann die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="58498-176">Then, call the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync) method.</span></span>

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

### <a name="parse-parameters-and-show-a-page"></a><span data-ttu-id="58498-177">Analysieren von Parametern und Anzeigen einer Seite</span><span class="sxs-lookup"><span data-stu-id="58498-177">Parse parameters and show a page</span></span>

<span data-ttu-id="58498-178">In der **App** Klasse des UWP-Projekts überschreiben den **OnActivated**-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="58498-178">In the **App** class of your UWP project, override the **OnActivated** event handler.</span></span> <span data-ttu-id="58498-179">Wenn die App durch Ihr Protokoll aktiviert wird, analysieren Sie die Parameter, und öffnen Sie die gewünschte Seite.</span><span class="sxs-lookup"><span data-stu-id="58498-179">If the app is activated by your protocol, parse the parameters and then open the page that you want.</span></span>

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

<span data-ttu-id="58498-180">Überschreiben Sie in der Code-behind der XAML-Seite, die ``OnNavigatedTo`` in die Seite übergebenen-Methode auf, um die Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="58498-180">In the code behind your XAML page, override the ``OnNavigatedTo`` method to use the parameters passed into the page.</span></span> <span data-ttu-id="58498-181">In diesem Fall verwenden wir den Breiten- und Längengrad, die in diese Seite übergeben wurden, um einen Standort in einer Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="58498-181">In this case, we'll use the latitude and longitude that were passed into this page to show a location in a map.</span></span>

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

## <a name="making-your-desktop-application-a-share-target"></a><span data-ttu-id="58498-182">Ihre Desktopanwendung als Freigabeziel gestalten</span><span class="sxs-lookup"><span data-stu-id="58498-182">Making your desktop application a share target</span></span>

<span data-ttu-id="58498-183">Sie können Ihre Desktopanwendung als Freigabeziel einrichten, damit Benutzer einfach Daten wie Bilder aus anderen Apps freigeben können, die Freigaben unterstützen.</span><span class="sxs-lookup"><span data-stu-id="58498-183">You can make your desktop application a share target so that users can easily share data such as pictures from other apps that support sharing.</span></span>

<span data-ttu-id="58498-184">Beispielsweise können Benutzer Ihre Anwendung zum Teilen von Bildern in Microsoft Edge, die Fotos-app auswählen.</span><span class="sxs-lookup"><span data-stu-id="58498-184">For example, users could choose your application to share pictures from Microsoft Edge, the Photos app.</span></span> <span data-ttu-id="58498-185">Hier ist eine WPF-beispielanwendung, die diese Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="58498-185">Here's a WPF sample application that has that capability.</span></span>

![Freigabeziel](images/desktop-to-uwp/share-target.png)<span data-ttu-id="58498-187">.</span><span class="sxs-lookup"><span data-stu-id="58498-187">.</span></span>

<span data-ttu-id="58498-188">Im vollständige Beispiel finden Sie [hier](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/ShareTarget)</span><span class="sxs-lookup"><span data-stu-id="58498-188">See the complete sample [here](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/ShareTarget)</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="58498-189">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="58498-189">The design pattern</span></span>

<span data-ttu-id="58498-190">Damit einer Anwendung als Freigabeziel arbeitet, führen Sie folgende Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="58498-190">To make your application a share target, do these things:</span></span>

<span data-ttu-id="58498-191">:one: [Hinzufügen der Freigabezielerweiterung](#share-extension)</span><span class="sxs-lookup"><span data-stu-id="58498-191">:one: [Add a share target extension](#share-extension)</span></span>

<span data-ttu-id="58498-192">: two: [Überschreiben des Ereignisses OnShareTargetActivated](#override)</span><span class="sxs-lookup"><span data-stu-id="58498-192">:two: [Override the OnShareTargetActivated event handler](#override)</span></span>

<span data-ttu-id="58498-193">: three: [desktop Extensions zum UWP-Projekt hinzufügen](#desktop-extensions)</span><span class="sxs-lookup"><span data-stu-id="58498-193">:three: [Add desktop extensions to the UWP project](#desktop-extensions)</span></span>

<span data-ttu-id="58498-194">: four: [Hinzufügen der Erweiterung voller Vertrauenswürdigkeit Prozess](#full-trust)</span><span class="sxs-lookup"><span data-stu-id="58498-194">:four: [Add the full trust process extension](#full-trust)</span></span>

<span data-ttu-id="58498-195">: five: [Ändern der desktop-Anwendung zum Abrufen der freigegebenen Datei](#modify-desktop)</span><span class="sxs-lookup"><span data-stu-id="58498-195">:five: [Modify the desktop application to get the shared file](#modify-desktop)</span></span>

<a id="share-extension" />

<span data-ttu-id="58498-196">Die folgenden Schritte</span><span class="sxs-lookup"><span data-stu-id="58498-196">The following steps</span></span>  

### <a name="add-a-share-target-extension"></a><span data-ttu-id="58498-197">Hinzufügen der Freigabezielerweiterung</span><span class="sxs-lookup"><span data-stu-id="58498-197">Add a share target extension</span></span>

<span data-ttu-id="58498-198">Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe und fügen Sie der Freigabe Ziel Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-198">In **Solution Explorer**, open the **package.appxmanifest** file of the Packaging project in your solution and add the share target extension.</span></span>

```xml
<Extensions>
      <uap:Extension
          Category="windows.shareTarget"
          Executable="ShareTarget.exe"
          EntryPoint="App">
        <uap:ShareTarget>
          <uap:SupportedFileTypes>
            <uap:SupportsAnyFileType />
          </uap:SupportedFileTypes>
          <uap:DataFormat>Bitmap</uap:DataFormat>
        </uap:ShareTarget>
      </uap:Extension>
</Extensions>  
```

<span data-ttu-id="58498-199">Geben Sie den Namen der ausführbaren Datei des UWP-Projekts an und den Namen der Einstiegspunkt-Klasse.</span><span class="sxs-lookup"><span data-stu-id="58498-199">Provide the name of the executable produced by the UWP project, and the name of the entry point class.</span></span> <span data-ttu-id="58498-200">Dieses Markup wird davon ausgegangen, dass der Name der ausführbaren Datei für Ihre UWP-app ist `ShareTarget.exe`.</span><span class="sxs-lookup"><span data-stu-id="58498-200">This markup assumes that the name of the executable for your UWP app is `ShareTarget.exe`.</span></span>

<span data-ttu-id="58498-201">Sie müssen außerdem angeben, welche Arten von Dateien mit Ihrer App freigegeben können.</span><span class="sxs-lookup"><span data-stu-id="58498-201">You'll also have to specify what types of files can be shared with your app.</span></span> <span data-ttu-id="58498-202">In diesem Beispiel Wir stellen der [WPF-PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) desktop-Anwendung als Freigabeziel für Bitmap images, damit wir angeben `Bitmap` für den unterstützten Dateityp.</span><span class="sxs-lookup"><span data-stu-id="58498-202">In this example, we are making the [WPF PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) desktop application a share target for bitmap images so we specify `Bitmap` for the supported file type.</span></span>

<a id="override" />

### <a name="override-the-onsharetargetactivated-event-handler"></a><span data-ttu-id="58498-203">Überschreiben des Ereignisses OnShareTargetActivated</span><span class="sxs-lookup"><span data-stu-id="58498-203">Override the OnShareTargetActivated event handler</span></span>

<span data-ttu-id="58498-204">Überschreiben Sie den **OnShareTargetActivated** -Ereignishandler in der **App** -Klasse des UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="58498-204">Override the **OnShareTargetActivated** event handler in the **App** class of your UWP project.</span></span>

<span data-ttu-id="58498-205">Dieser Ereignishandler wird aufgerufen, wenn Benutzer Ihre App zum Teilen von Dateien auswählen.</span><span class="sxs-lookup"><span data-stu-id="58498-205">This event handler is called when users choose your app to share their files.</span></span>

```csharp

protected override void OnShareTargetActivated(ShareTargetActivatedEventArgs args)
{
    shareWithDesktopApplication(args.ShareOperation);
}

private async void shareWithDesktopApplication(ShareOperation shareOperation)
{
    if (shareOperation.Data.Contains(StandardDataFormats.StorageItems))
    {
        var items = await shareOperation.Data.GetStorageItemsAsync();
        StorageFile file = items[0] as StorageFile;
        IRandomAccessStreamWithContentType stream = await file.OpenReadAsync();

        await file.CopyAsync(ApplicationData.Current.LocalFolder);
            shareOperation.ReportCompleted();

        await FullTrustProcessLauncher.LaunchFullTrustProcessForCurrentAppAsync();
    }
}
```
<span data-ttu-id="58498-206">In diesem Code speichern wir das Bild, das vom Benutzer in einem Ordner apps lokalen Speicher freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="58498-206">In this code, we save the image that is being shared by the user into a apps local storage folder.</span></span> <span data-ttu-id="58498-207">Ändern Sie später die desktop-Anwendung Pull-Images aus diesem Ordner.</span><span class="sxs-lookup"><span data-stu-id="58498-207">Later, we'll modify the desktop application to pull images from that same folder.</span></span> <span data-ttu-id="58498-208">Die desktop-Anwendung kann das tun, da es im gleichen Paket als UWP-app enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="58498-208">The desktop application can do that because it is included in the same package as the UWP app.</span></span>

<a id="desktop-extensions" />

### <a name="add-desktop-extensions-to-the-uwp-project"></a><span data-ttu-id="58498-209">Hinzufügen von desktop Extensions zum UWP-Projekt</span><span class="sxs-lookup"><span data-stu-id="58498-209">Add desktop extensions to the UWP project</span></span>

<span data-ttu-id="58498-210">Fügen Sie die **Windows Desktop Extensions für die UWP** -Erweiterung zum UWP-app-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-210">Add the **Windows Desktop Extensions for the UWP** extension to the UWP app project.</span></span>

![Desktop-Erweiterung](images/desktop-to-uwp/desktop-extensions.png)

<a id="full-trust" />

### <a name="add-the-full-trust-process-extension"></a><span data-ttu-id="58498-212">Hinzufügen der Erweiterung voller Vertrauenswürdigkeit Prozess</span><span class="sxs-lookup"><span data-stu-id="58498-212">Add the full trust process extension</span></span>

<span data-ttu-id="58498-213">Öffnen Sie im **Projektmappen-Explorer**die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Projektmappe, und dann fügen Sie die Erweiterung voller Vertrauenswürdigkeit Prozess neben der Freigabe Ziel-Erweiterung, dass Sie diese Datei zuvor hinzufügen hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-213">In **Solution Explorer**, open the **package.appxmanifest** file of the Packaging project in your solution, and then add the full trust process extension next to the share target extension that you add this file earlier.</span></span>

```xml
<Extensions>
  ...
      <desktop:Extension Category="windows.fullTrustProcess" Executable="PhotoStoreDemo\PhotoStoreDemo.exe" />
  ...
</Extensions>  
```

<span data-ttu-id="58498-214">Diese Erweiterung ermöglicht die UWP-app für die desktop-Anwendung starten, die Sie die Freigabe einer Datei möchten.</span><span class="sxs-lookup"><span data-stu-id="58498-214">This extension will enable the UWP app to start the desktop application to which you would like the share a file.</span></span> <span data-ttu-id="58498-215">Im Beispiel verweisen wir auf die ausführbare Datei von [WPF-PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) -desktop-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="58498-215">In example, we refer to the executable of the [WPF PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) desktop application.</span></span>

<a id="modify-desktop" />

### <a name="modify-the-desktop-application-to-get-the-shared-file"></a><span data-ttu-id="58498-216">Ändern Sie die desktop-Anwendung zum Abrufen der freigegebenen Datei</span><span class="sxs-lookup"><span data-stu-id="58498-216">Modify the desktop application to get the shared file</span></span>

<span data-ttu-id="58498-217">Ändern Sie Ihre desktop-Anwendung zu suchen und zu verarbeiten die freigegebene Datei.</span><span class="sxs-lookup"><span data-stu-id="58498-217">Modify your desktop application to find and process the shared file.</span></span> <span data-ttu-id="58498-218">In diesem Beispiel wird gespeichert, die UWP-app die freigegebene Datei im Ordner "lokalen app-Daten".</span><span class="sxs-lookup"><span data-stu-id="58498-218">In this example, the UWP app stored the shared file in the local app data folder.</span></span> <span data-ttu-id="58498-219">Aus diesem Grund würden wir die [PhotoStoreDemo WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) -Desktopanwendung in Pull Fotos aus diesem Ordner ändern.</span><span class="sxs-lookup"><span data-stu-id="58498-219">Therefore, we would modify the [WPF PhotoStoreDemo](https://github.com/Microsoft/WPF-Samples/tree/master/Sample%20Applications/PhotoStoreDemo) desktop application to pull photos from that folder.</span></span>

```csharp
Photos.Path = Windows.Storage.ApplicationData.Current.LocalFolder.Path;
```
<span data-ttu-id="58498-220">Für Instanzen der desktop-Anwendung, die bereits durch den Benutzer zu öffnen, können wir auch Behandeln des Ereignisses [FileSystemWatcher](https://docs.microsoft.com/dotnet/api/system.io.filesystemwatcher?view=netframework-4.7.2) und übergeben Sie den Pfad zum Speicherort Datei.</span><span class="sxs-lookup"><span data-stu-id="58498-220">For instances of the desktop application that are already open by the user, we might also handle the [FileSystemWatcher](https://docs.microsoft.com/dotnet/api/system.io.filesystemwatcher?view=netframework-4.7.2) event and pass in the path to the file location.</span></span> <span data-ttu-id="58498-221">Auf diese Weise werden alle Instanzen von desktop-Anwendung freigegebenen Fotos angezeigt.</span><span class="sxs-lookup"><span data-stu-id="58498-221">That way any open instances of the desktop application will show the shared photo.</span></span>

```csharp
...

   FileSystemWatcher watcher = new FileSystemWatcher(Photos.Path);

...

private void Watcher_Created(object sender, FileSystemEventArgs e)
{
    // new file got created, adding it to the list
    Dispatcher.BeginInvoke(System.Windows.Threading.DispatcherPriority.Normal, new Action(() =>
    {
        if (File.Exists(e.FullPath))
        {
            ImageFile item = new ImageFile(e.FullPath);
            Photos.Insert(0, item);
            PhotoListBox.SelectedIndex = 0;
            CurrentPhoto.Source = (BitmapSource)item.Image;
        }
    }));
}

```

## <a name="create-a-background-task"></a><span data-ttu-id="58498-222">Erstellen einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="58498-222">Create a background task</span></span>

<span data-ttu-id="58498-223">Sie fügen eine Hintergrundaufgaben hinzu, um selbst dann App-Code auszuführen, wenn die App angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="58498-223">You add a background task to run code even when the app is suspended.</span></span> <span data-ttu-id="58498-224">Hintergrundaufgaben sind ideal für kleine Aufgaben, die keine Benutzerinteraktion erfordern.</span><span class="sxs-lookup"><span data-stu-id="58498-224">Background tasks are great for small tasks that don't require the user interaction.</span></span> <span data-ttu-id="58498-225">Beispielsweise kann Ihre Aufgabe E-Mails herunterladen, eine Popupbenachrichtigung über eine eingehende Chatnachricht zeigen oder auf eine Änderung in einer Systembedingung reagieren.</span><span class="sxs-lookup"><span data-stu-id="58498-225">For example, your task can download mail, show a toast notification about an incoming chat message, or react to a change in a system condition.</span></span>

<span data-ttu-id="58498-226">Hier ist eine WPF-beispielanwendung, die eine Hintergrundaufgabe registriert.</span><span class="sxs-lookup"><span data-stu-id="58498-226">Here's a WPF sample application that registers a background task.</span></span>

![hintergrundaufgabe](images/desktop-to-uwp/sample-background-task.png)

<span data-ttu-id="58498-228">Die Aufgabe stellt eine HTTP-Anforderung und misst die Zeit, die die Anforderung benötigt, um eine Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="58498-228">The task makes an http request and measures the time that it takes for the request to return a response.</span></span> <span data-ttu-id="58498-229">Ihre Aufgaben werden wahrscheinlich viel interessanter sein, aber dieses Beispiel eignet sich gut, um die grundlegende Funktionsweise einer Hintergrundaufgabe zu lernen.</span><span class="sxs-lookup"><span data-stu-id="58498-229">Your tasks will likely be much more interesting, but this sample is great for learning the basic mechanics of a background task.</span></span>

<span data-ttu-id="58498-230">Im vollständige Beispiel finden Sie [hier](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask).</span><span class="sxs-lookup"><span data-stu-id="58498-230">See the complete sample [here](https://github.com/Microsoft/Windows-Packaging-Samples/tree/master/BGTask).</span></span>

### <a name="the-design-pattern"></a><span data-ttu-id="58498-231">Das Entwurfsmuster</span><span class="sxs-lookup"><span data-stu-id="58498-231">The design pattern</span></span>

<span data-ttu-id="58498-232">Um einen Hintergrunddienst zu erstellen, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="58498-232">To create a background service, do these things:</span></span>

<span data-ttu-id="58498-233">:one: [Implementieren der Hintergrundaufgabe](#implement-task)</span><span class="sxs-lookup"><span data-stu-id="58498-233">:one: [Implement the background task](#implement-task)</span></span>

<span data-ttu-id="58498-234">:two: [Konfigurieren der Hintergrundaufgabe](#configure-background-task)</span><span class="sxs-lookup"><span data-stu-id="58498-234">:two: [Configure the background task](#configure-background-task)</span></span>

<span data-ttu-id="58498-235">:three: [Registrieren der Hintergrundaufgabe](#register-background-task)</span><span class="sxs-lookup"><span data-stu-id="58498-235">:three: [Register the background task](#register-background-task)</span></span>

<a id="implement-task" />

### <a name="implement-the-background-task"></a><span data-ttu-id="58498-236">Implementieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="58498-236">Implement the background task</span></span>

<span data-ttu-id="58498-237">Implementieren Sie die Hintergrundaufgabe, indem Sie einem Komponentenprojekt für Windows-Runtime Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="58498-237">Implement the background task by adding code to a Windows Runtime component project.</span></span>

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

### <a name="configure-the-background-task"></a><span data-ttu-id="58498-238">Konfigurieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="58498-238">Configure the background task</span></span>

<span data-ttu-id="58498-239">Öffnen Sie im manifest-Designer die Datei **"Package.appxmanifest"** des Verpackung-Projekts in Ihrer Lösung.</span><span class="sxs-lookup"><span data-stu-id="58498-239">In the manifest designer, open the **package.appxmanifest** file of the Packaging project in your solution.</span></span>

<span data-ttu-id="58498-240">Fügen Sie auf der Registerkarte **Deklarationen** eine **Hintergrundaufgaben**-Deklaration hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-240">In the **Declarations** tab, add a **Background Tasks** declaration.</span></span>

![Hintergrundaufgaben-Option](images/desktop-to-uwp/background-task-option.png)

<span data-ttu-id="58498-242">Wählen Sie dann die gewünschten Eigenschaften aus.</span><span class="sxs-lookup"><span data-stu-id="58498-242">Then, choose the desired properties.</span></span> <span data-ttu-id="58498-243">Unser Beispiel verwendet die **Timer**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="58498-243">Our sample uses the **Timer** property.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/timer-property.png)

<span data-ttu-id="58498-245">Geben Sie den vollqualifizierten Namen der Klasse in der Komponente für Windows-Runtime, die die Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="58498-245">Provide the fully qualified name of the class in your Windows Runtime Component that implements the background task.</span></span>

![Time-Eigenschaft](images/desktop-to-uwp/background-task-entry-point.png)

<a id="register-background-task" />

### <a name="register-the-background-task"></a><span data-ttu-id="58498-247">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="58498-247">Register the background task</span></span>

<span data-ttu-id="58498-248">Fügen Sie Ihrem Projekt für die Desktop-Anwendung, das die Hintergrundaufgabe registriert, Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="58498-248">Add code to your desktop application project that registers the background task.</span></span>

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
## <a name="support-and-feedback"></a><span data-ttu-id="58498-249">Support und Feedback</span><span class="sxs-lookup"><span data-stu-id="58498-249">Support and feedback</span></span>

**<span data-ttu-id="58498-250">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="58498-250">Find answers to your questions</span></span>**

<span data-ttu-id="58498-251">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="58498-251">Have questions?</span></span> <span data-ttu-id="58498-252">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="58498-252">Ask us on Stack Overflow.</span></span> <span data-ttu-id="58498-253">Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="58498-253">Our team monitors these [tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="58498-254">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="58498-254">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="58498-255">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="58498-255">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="58498-256">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="58498-256">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
