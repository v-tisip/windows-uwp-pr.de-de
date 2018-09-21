---
author: Karl-Bridge-Microsoft
ms.author: kbridge
title: Interaktionen über Anvisieren
Description: Learn how to design and optimize your UWP apps to provide the best experience possible for users who rely on gaze input from eye and head trackers.
label: Gaze interactions
template: detail.hbs
keywords: Anvisieren, Eye Tracking, Head Tracking, Anvisierungspunkt, Eingabe, Benutzerinteraktion, Bedienungshilfen, Benutzerfreundlichkeit
ms.date: 05/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: Jake Cohen
dev-contact: Austin Hodges
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 3d716bf25c4df41af32084190522e3c5fcd4885b
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4091864"
---
# <a name="gaze-interactions-and-eye-tracking-in-uwp-apps"></a><span data-ttu-id="d066c-103">Interaktionen via Blick und Eye Tracking in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="d066c-103">Gaze interactions and eye tracking in UWP apps</span></span>

![Eye Tracking Hero](images/gaze/eyecontrolbanner1.png)

<span data-ttu-id="d066c-105">Bieten Sie Unterstützung für die Verfolgung des Blicks, der Aufmerksamkeit und der Anwesenheit eines Benutzers basierend auf der Position und den Bewegungen seiner Augen.</span><span class="sxs-lookup"><span data-stu-id="d066c-105">Provide support for tracking a user's gaze, attention, and presence based on the location and movement of their eyes.</span></span>

> [!NOTE]
> <span data-ttu-id="d066c-106">Informationen zur Eingabe via Anvisieren in [Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/) finden Sie unter [Anvisieren](https://docs.microsoft.com/windows/mixed-reality/gaze).</span><span class="sxs-lookup"><span data-stu-id="d066c-106">For gaze input in [Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/), see [Gaze](https://docs.microsoft.com/windows/mixed-reality/gaze).</span></span>

<span data-ttu-id="d066c-107">**Wichtige APIs**: [Windows.Devices.Input.Preview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview), [GazeDevicePreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicepreview), [GazePointPreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazepointpreview), [GazeInputSourcePreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview)</span><span class="sxs-lookup"><span data-stu-id="d066c-107">**Important APIs**: [Windows.Devices.Input.Preview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview), [GazeDevicePreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicepreview), [GazePointPreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazepointpreview), [GazeInputSourcePreview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview)</span></span>

## <a name="overview"></a><span data-ttu-id="d066c-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d066c-108">Overview</span></span>

<span data-ttu-id="d066c-109">Die Eingabe über Anvisieren ist eine tolle Möglichkeit, mit Windows- und UWP-Anwendungen zu interagieren. Sie eignet sich insbesondere als Hilfstechnologe für Benutzer mit neuromuskulären Erkrankungen (z.B. ALS) und anderen Einschränkungen, die mit einer beeinträchtigten Muskel- oder Nervenfunktion einhergehen.</span><span class="sxs-lookup"><span data-stu-id="d066c-109">Gaze input is a powerful way to interact and use Windows and UWP applications that is especially useful as an assistive technology for users with neuro-muscular diseases (such as ALS) and other disabilities involving impaired muscle or nerve functions.</span></span>

<span data-ttu-id="d066c-110">Darüber hinaus bietet die Eingabe über Anvisieren gleichermaßen attraktive Möglichkeiten für Spiele (z.B. Zielbestimmung und Nachverfolgung) und herkömmliche Produktivitätsanwendungen, Kiosks und andere interaktiven Szenarien, bei denen herkömmliche Eingabegeräte (z.B. Tastatur, Maus, Touch) nicht verfügbar sind oder es hilfreich wäre, dass der Benutzer die Hände frei hat für andere Aufgaben (z.B. zum Halten von Einkaufstüten).</span><span class="sxs-lookup"><span data-stu-id="d066c-110">In addition, gaze input offers equally compelling opportunities for both gaming (including target acquisition and tracking) and traditional productivity applications, kiosks, and other interactive scenarios where traditional input devices (keyboard, mouse, touch) are not available, or where it might be useful/helpful to free up the user's hands for other tasks (such as holding shopping bags).</span></span>

> [!NOTE]
> <span data-ttu-id="d066c-111">Die Unterstützung für Eye Tracking-Hardware wurde mit dem **Windows10 Fall Creators Update** zusammen mit der [Augensteuerung](https://support.microsoft.com/en-us/help/4043921/windows-10-get-started-eye-control) eingeführt, einem integrierten Feature, mit dem Sie Ihre Augen nutzen können, um den Bildschirmzeiger zu steuern, Text über die Bildschirmtastatur einzugeben und mit Personen über Text-zu-Sprache zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="d066c-111">Support for eye tracking hardware was introduced in **Windows 10 Fall Creators Update** along with [Eye control](https://support.microsoft.com/en-us/help/4043921/windows-10-get-started-eye-control), a built-in feature that lets you use your eyes to control the on-screen pointer, type with the on-screen keyboard, and communicate with people using text-to-speech.</span></span> <span data-ttu-id="d066c-112">Eine Reihe von [UWP-APIs]([Windows.Devices.Input.Preview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview)) zum Erstellen von Anwendungen, die mit der Eye Tracking-Hardware interagieren können, ist im Lieferumfang des **Windows 10-Update April 2018 (Version 1803, Build 17134)** und höher enthalten.</span><span class="sxs-lookup"><span data-stu-id="d066c-112">A set of [UWP APIs]([Windows.Devices.Input.Preview](https://docs.microsoft.com/uwp/api/windows.devices.input.preview)) for building applications that can interact with eye tracking hardware is available with **Windows 10 April 2018 Update (Version 1803, build 17134)** and newer.</span></span>

## <a name="privacy"></a><span data-ttu-id="d066c-113">Privatsphäre</span><span class="sxs-lookup"><span data-stu-id="d066c-113">Privacy</span></span>

<span data-ttu-id="d066c-114">Aufgrund der potenziell vertraulichen persönlichen Daten, die von Eye Tracking-Geräten gesammelt werden, müssen Sie die `gazeInput`-Funktion im App-Manifest Ihrer UWP-Anwendung deklarieren (siehe den folgenden Abschnitt **Setup**).</span><span class="sxs-lookup"><span data-stu-id="d066c-114">Due to the potentially sensitive personal data collected by eye tracking devices, you are required to declare the `gazeInput` capability in the app manifest of your UWP application (see the following **Setup** section).</span></span> <span data-ttu-id="d066c-115">Sofern deklariert, fordert Windows die Benutzer (bei erstmaliger Ausführung der App) automatisch über ein Dialogfeld auf, ihre Zustimmung zu geben, dass die App mit dem Eye Tracking-Gerät kommuniziert und auf diese Daten zugreift.</span><span class="sxs-lookup"><span data-stu-id="d066c-115">When declared, Windows automatically prompts users with a consent dialog (when the app is first run), where the user must grant permission for the app to communicate with the eye-tracking device and access this data.</span></span>

<span data-ttu-id="d066c-116">Wenn Ihre App darüber hinaus Eye Tracking-Daten erfasst, speichert oder überträgt, müssen Sie dies in den Datenschutzbestimmungen für die App darlegen und alle sonstigen Anforderungen an **personenbezogene Informationen** in der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) und den [Microsoft Store-Richtlinien ](https://docs.microsoft.com/legal/windows/agreements/store-policies) erfüllen.</span><span class="sxs-lookup"><span data-stu-id="d066c-116">In addition, if your app collects, stores, or transfers eye tracking data, you must describe this in your app's privacy statement and follow all other requirements for **Personal Information** in the [App Developer Agreement](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) and the [Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies).</span></span>

## <a name="setup"></a><span data-ttu-id="d066c-117">Setup</span><span class="sxs-lookup"><span data-stu-id="d066c-117">Setup</span></span>

<span data-ttu-id="d066c-118">Um die APIs für die Eingabe über Anvisieren in Ihrer UWP-App zu verwenden, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="d066c-118">To use the gaze input APIs in your UWP app you'll need to:</span></span> 

- <span data-ttu-id="d066c-119">Geben Sie die `gazeInput`-Funktion im Appmanifest an.</span><span class="sxs-lookup"><span data-stu-id="d066c-119">Specify the `gazeInput` capability in the app manifest.</span></span>

    <span data-ttu-id="d066c-120">Öffnen Sie die Datei **Package.appxmanifest** mit dem Manifest-Designer von Visual Studio, oder fügen Sie die Funktion manuell hinzu, indem Sie **Code anzeigen** auswählen und die folgende `DeviceCapability` in den Knoten `Capabilities` einfügen:</span><span class="sxs-lookup"><span data-stu-id="d066c-120">Open the **Package.appxmanifest** file with the Visual Studio manifest designer, or add the capability manually by selecting **View code**, and inserting the following `DeviceCapability` into the `Capabilities` node:</span></span>

    ```xaml
    <Capabilities>
       <DeviceCapability Name="gazeInput" />
    </Capabilities>
    ```

- <span data-ttu-id="d066c-121">Ein Windows-kompatibles Eye Tracking-Gerät (entweder integriertes Gerät oder Peripheriegerät) muss an Ihr System angeschlossen und eingeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="d066c-121">A Windows-compatible eye-tracking device connected to your system (either built-in or peripheral) and turned on.</span></span>

    <span data-ttu-id="d066c-122">Unter [Erste Schritte mit der Augensteuerung in Windows10](https://support.microsoft.com/help/4043921/windows-10-get-started-eye-control#supported-devices ) finden Sie eine Liste der unterstützten Eye Tracking-Geräte.</span><span class="sxs-lookup"><span data-stu-id="d066c-122">See [Get started with eye control in Windows 10](https://support.microsoft.com/help/4043921/windows-10-get-started-eye-control#supported-devices ) for a list of supported eye-tracking devices.</span></span>

## <a name="basic-eye-tracking"></a><span data-ttu-id="d066c-123">Grundlegendes Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="d066c-123">Basic eye tracking</span></span>

<span data-ttu-id="d066c-124">In diesem Beispiel wird veranschaulicht, wie Sie den Blick der Benutzer in einer UWP-Anwendung verfolgen und eine Timing-Funktion mit grundlegenden Treffertests verwenden, um anzugeben, wie gut sie ihren Blick auf ein bestimmtes Element fokussieren können.</span><span class="sxs-lookup"><span data-stu-id="d066c-124">In this example, we demonstrate how to track the user's gaze within a UWP application and use a timing function with basic hit testing to indicate how well they can maintain their gaze focus on a specific element.</span></span>

<span data-ttu-id="d066c-125">Eine kleine Ellipse wird verwendet, um anzuzeigen, wo der Anvisierungspunkt sich im Viewport der Anwendung befindet, während eine [RadialProgressBar](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/controls/radialprogressbar) aus dem [Windows-Community Toolkit](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/) nach dem Zufallsprinzip im Zeichenbereich platziert wird.</span><span class="sxs-lookup"><span data-stu-id="d066c-125">A small ellipse is used to show where the gaze point is within the application viewport, while a [RadialProgressBar](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/controls/radialprogressbar) from the [Windows Community Toolkit](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/) is placed randomly on the canvas.</span></span> <span data-ttu-id="d066c-126">Wenn der Anvisierungspunkt auf der Fortschrittsleiste erkannt wird, wird ein Timer gestartet und die Fortschrittsleiste wird im Zeichenbereich nach dem Zufallsprinzip verschoben, wenn sie 100% erreicht.</span><span class="sxs-lookup"><span data-stu-id="d066c-126">When gaze focus is detected on the progress bar, a timer is started and the progress bar is randomly relocated on the canvas when the progress bar reaches 100%.</span></span>

![Blickverfolgung mit Timer-Beispiel](images/gaze/gaze-input-timed2.gif)

*<span data-ttu-id="d066c-128">Blickverfolgung mit Timer-Beispiel</span><span class="sxs-lookup"><span data-stu-id="d066c-128">Gaze tracking with timer sample</span></span>*

**<span data-ttu-id="d066c-129">Laden Sie dieses Beispiel von [Beispiel für die Eingabe via Anvisieren (einfach)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-gazeinput-basic.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="d066c-129">Download this sample from [Gaze input sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-gazeinput-basic.zip)</span></span>**

1. <span data-ttu-id="d066c-130">Zunächst richten wir die Benutzeroberfläche ein (MainPage.xaml).</span><span class="sxs-lookup"><span data-stu-id="d066c-130">First, we set up the UI (MainPage.xaml).</span></span>

    ```xaml
    <Page
        x:Class="gazeinput.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:gazeinput"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:controls="using:Microsoft.Toolkit.Uwp.UI.Controls"    
        mc:Ignorable="d">
    
        <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
            <Grid x:Name="containerGrid">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition Height="*"/>
                </Grid.RowDefinitions>
                <StackPanel x:Name="HeaderPanel" 
                        Orientation="Horizontal" 
                        Grid.Row="0">
                    <StackPanel.Transitions>
                        <TransitionCollection>
                            <AddDeleteThemeTransition/>
                        </TransitionCollection>
                    </StackPanel.Transitions>
                    <TextBlock x:Name="Header" 
                           Text="Gaze tracking sample" 
                           Style="{ThemeResource HeaderTextBlockStyle}" 
                           Margin="10,0,0,0" />
                    <TextBlock x:Name="TrackerCounterLabel"
                           VerticalAlignment="Center"                 
                           Style="{ThemeResource BodyTextBlockStyle}"
                           Text="Number of trackers: " 
                           Margin="50,0,0,0"/>
                    <TextBlock x:Name="TrackerCounter"
                           VerticalAlignment="Center"                 
                           Style="{ThemeResource BodyTextBlockStyle}"
                           Text="0" 
                           Margin="10,0,0,0"/>
                    <TextBlock x:Name="TrackerStateLabel"
                           VerticalAlignment="Center"                 
                           Style="{ThemeResource BodyTextBlockStyle}"
                           Text="State: " 
                           Margin="50,0,0,0"/>
                    <TextBlock x:Name="TrackerState"
                           VerticalAlignment="Center"                 
                           Style="{ThemeResource BodyTextBlockStyle}"
                           Text="n/a" 
                           Margin="10,0,0,0"/>
                </StackPanel>
                <Canvas x:Name="gazePositionCanvas" Grid.Row="1">
                    <controls:RadialProgressBar
                        x:Name="GazeRadialProgressBar" 
                        Value="0"
                        Foreground="Blue" 
                        Background="White"
                        Thickness="4"
                        Minimum="0"
                        Maximum="100"
                        Width="100"
                        Height="100"
                        Outline="Gray"
                        Visibility="Collapsed"/>
                    <Ellipse 
                        x:Name="eyeGazePositionEllipse"
                        Width="20" Height="20"
                        Fill="Blue" 
                        Opacity="0.5" 
                        Visibility="Collapsed">
                    </Ellipse>
                </Canvas>
            </Grid>
        </Grid>
    </Page>
    ```

2. <span data-ttu-id="d066c-131">Als Nächstes initialisieren wir unsere App.</span><span class="sxs-lookup"><span data-stu-id="d066c-131">Next, we initialize our app.</span></span>

    <span data-ttu-id="d066c-132">In diesem Codeausschnitt deklarieren wir unsere globalen Objekte und überschreiben das Seitenereignis [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto), um unseren [Gaze Device Watcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview) und das Seitenereignis [OnNavigatedFrom](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedfrom) zu starten, um unseren [Gaze Device Watcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview) zu beenden.</span><span class="sxs-lookup"><span data-stu-id="d066c-132">In this snippet, we declare our global objects and override the [OnNavigatedTo](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedto) page event to start our [gaze device watcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview) and the [OnNavigatedFrom](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.page.onnavigatedfrom) page event to stop our [gaze device watcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview).</span></span>

    ```csharp
    using System;
    using Windows.Devices.Input.Preview;
    using Windows.UI.Xaml.Controls;
    using Windows.UI.Xaml;
    using Windows.Foundation;
    using System.Collections.Generic;
    using Windows.UI.Xaml.Media;
    using Windows.UI.Xaml.Navigation;
    
    namespace gazeinput
    {
        public sealed partial class MainPage : Page
        {
            /// <summary>
            /// Reference to the user's eyes and head as detected
            /// by the eye-tracking device.
            /// </summary>
            private GazeInputSourcePreview gazeInputSource;
    
            /// <summary>
            /// Dynamic store of eye-tracking devices.
            /// </summary>
            /// <remarks>
            /// Receives event notifications when a device is added, removed, 
            /// or updated after the initial enumeration.
            /// </remarks>
            private GazeDeviceWatcherPreview gazeDeviceWatcher;
    
            /// <summary>
            /// Eye-tracking device counter.
            /// </summary>
            private int deviceCounter = 0;
    
            /// <summary>
            /// Timer for gaze focus on RadialProgressBar.
            /// </summary>
            DispatcherTimer timerGaze = new DispatcherTimer();
    
            /// <summary>
            /// Tracker used to prevent gaze timer restarts.
            /// </summary>
            bool timerStarted = false;
    
            /// <summary>
            /// Initialize the app.
            /// </summary>
            public MainPage()
            {
                InitializeComponent();
            }

            /// <summary>
            /// Override of OnNavigatedTo page event starts GazeDeviceWatcher.
            /// </summary>
            /// <param name="e">Event args for the NavigatedTo event</param>
            protected override void OnNavigatedTo(NavigationEventArgs e)
            {
                // Start listening for device events on navigation to eye-tracking page.
                StartGazeDeviceWatcher();
            }
    
            /// <summary>
            /// Override of OnNavigatedFrom page event stops GazeDeviceWatcher.
            /// </summary>
            /// <param name="e">Event args for the NavigatedFrom event</param>
            protected override void OnNavigatedFrom(NavigationEventArgs e)
            {
                // Stop listening for device events on navigation from eye-tracking page.
                StopGazeDeviceWatcher();
            }
        }
    }
    ```

3. <span data-ttu-id="d066c-133">Als Nächstes fügen wir unsere Gaze Device Watcher-Methoden hinzu.</span><span class="sxs-lookup"><span data-stu-id="d066c-133">Next, we add our gaze device watcher methods.</span></span> 
    
    <span data-ttu-id="d066c-134">In `StartGazeDeviceWatcher` rufen wir [CreateWatcher](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.createwatcher) auf und deklarieren die Ereignislistener des Eye Tracking-Geräts ([DeviceAdded](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.added), [DeviceUpdated](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.updated) und [DeviceRemoved](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.removed)).</span><span class="sxs-lookup"><span data-stu-id="d066c-134">In `StartGazeDeviceWatcher`, we call [CreateWatcher](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.createwatcher) and declare the eye-tracking device event listeners ([DeviceAdded](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.added), [DeviceUpdated](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.updated), and [DeviceRemoved](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazedevicewatcherpreview.removed)).</span></span>

    <span data-ttu-id="d066c-135">In `DeviceAdded` überprüfen wir den Status des Eye Tracking-Geräts.</span><span class="sxs-lookup"><span data-stu-id="d066c-135">In `DeviceAdded`, we check the state of the eye-tracking device.</span></span> <span data-ttu-id="d066c-136">Bei einem geeigneten Gerät erhöhen wir die Gerätezahl und aktivieren die Blickverfolgung.</span><span class="sxs-lookup"><span data-stu-id="d066c-136">If a viable device, we increment our device count and enable gaze tracking.</span></span> <span data-ttu-id="d066c-137">Einzelheiten erfahren Sie im nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="d066c-137">See next step for details.</span></span>

    <span data-ttu-id="d066c-138">In `DeviceUpdated` aktivieren wir außerdem die Blickverfolgung, da dieses Ereignis ausgelöst wird, wenn ein Gerät neu kalibriert wird.</span><span class="sxs-lookup"><span data-stu-id="d066c-138">In `DeviceUpdated`, we also enable gaze tracking as this event is triggered if a device is recalibrated.</span></span>

    <span data-ttu-id="d066c-139">In `DeviceRemoved` verringern wir die Gerätezahl und entfernen die Gerätereignishandler.</span><span class="sxs-lookup"><span data-stu-id="d066c-139">In `DeviceRemoved`, we decrement our device counter and remove the device event handlers.</span></span>

    <span data-ttu-id="d066c-140">In `StopGazeDeviceWatcher` beenden wir den Gaze Device Watcher.</span><span class="sxs-lookup"><span data-stu-id="d066c-140">In `StopGazeDeviceWatcher`, we shut down the gaze device watcher.</span></span> 

```csharp
    /// <summary>
    /// Start gaze watcher and declare watcher event handlers.
    /// </summary>
    private void StartGazeDeviceWatcher()
    {
        if (gazeDeviceWatcher == null)
        {
            gazeDeviceWatcher = GazeInputSourcePreview.CreateWatcher();
            gazeDeviceWatcher.Added += this.DeviceAdded;
            gazeDeviceWatcher.Updated += this.DeviceUpdated;
            gazeDeviceWatcher.Removed += this.DeviceRemoved;
            gazeDeviceWatcher.Start();
        }
    }

    /// <summary>
    /// Shut down gaze watcher and stop listening for events.
    /// </summary>
    private void StopGazeDeviceWatcher()
    {
        if (gazeDeviceWatcher != null)
        {
            gazeDeviceWatcher.Stop();
            gazeDeviceWatcher.Added -= this.DeviceAdded;
            gazeDeviceWatcher.Updated -= this.DeviceUpdated;
            gazeDeviceWatcher.Removed -= this.DeviceRemoved;
            gazeDeviceWatcher = null;
        }
    }

    /// <summary>
    /// Eye-tracking device connected (added, or available when watcher is initialized).
    /// </summary>
    /// <param name="sender">Source of the device added event</param>
    /// <param name="e">Event args for the device added event</param>
    private void DeviceAdded(GazeDeviceWatcherPreview source, 
        GazeDeviceWatcherAddedPreviewEventArgs args)
    {
        if (IsSupportedDevice(args.Device))
        {
            deviceCounter++;
            TrackerCounter.Text = deviceCounter.ToString();
        }
        // Set up gaze tracking.
        TryEnableGazeTrackingAsync(args.Device);
    }

    /// <summary>
    /// Initial device state might be uncalibrated, 
    /// but device was subsequently calibrated.
    /// </summary>
    /// <param name="sender">Source of the device updated event</param>
    /// <param name="e">Event args for the device updated event</param>
    private void DeviceUpdated(GazeDeviceWatcherPreview source,
        GazeDeviceWatcherUpdatedPreviewEventArgs args)
    {
        // Set up gaze tracking.
        TryEnableGazeTrackingAsync(args.Device);
    }

    /// <summary>
    /// Handles disconnection of eye-tracking devices.
    /// </summary>
    /// <param name="sender">Source of the device removed event</param>
    /// <param name="e">Event args for the device removed event</param>
    private void DeviceRemoved(GazeDeviceWatcherPreview source,
        GazeDeviceWatcherRemovedPreviewEventArgs args)
    {
        // Decrement gaze device counter and remove event handlers.
        if (IsSupportedDevice(args.Device))
        {
            deviceCounter--;
            TrackerCounter.Text = deviceCounter.ToString();

            if (deviceCounter == 0)
            {
                gazeInputSource.GazeEntered -= this.GazeEntered;
                gazeInputSource.GazeMoved -= this.GazeMoved;
                gazeInputSource.GazeExited -= this.GazeExited;
            }
        }
    }
```

4. <span data-ttu-id="d066c-141">Hier wird überprüft, ob das Gerät in `IsSupportedDevice` funktionsbereit ist. Ist dies der Fall, versuchen Sie, die Blickverfolgung in `TryEnableGazeTrackingAsync` zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d066c-141">Here, we check if the device is viable in `IsSupportedDevice` and, if so, attempt to enable gaze tracking in `TryEnableGazeTrackingAsync`.</span></span>

    <span data-ttu-id="d066c-142">In `TryEnableGazeTrackingAsync` deklarieren wir die Blickereignishandler und rufen [GazeInputSourcePreview.GetForCurrentView()](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.getforcurrentview) auf, um einen Verweis zur Eingabequelle zu erhalten (Aufruf muss über den UI-Thread erfolgen, siehe [Aufrechterhalten der Reaktionsfähigkeit des UI-Threads](https://docs.microsoft.com/windows/uwp/debug-test-perf/keep-the-ui-thread-responsive)).</span><span class="sxs-lookup"><span data-stu-id="d066c-142">In `TryEnableGazeTrackingAsync`, we declare the gaze event handlers, and call [GazeInputSourcePreview.GetForCurrentView()](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.getforcurrentview) to get a reference to the input source (this must be called on the UI thread, see [Keep the UI thread responsive](https://docs.microsoft.com/windows/uwp/debug-test-perf/keep-the-ui-thread-responsive)).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d066c-143">Sie sollten [GazeInputSourcePreview.GetForCurrentView()](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.getforcurrentview) nur aufrufen, wenn ein kompatibles Eye Tracking-Gerät angeschlossen ist und für Ihre Anwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="d066c-143">You should call [GazeInputSourcePreview.GetForCurrentView()](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeinputsourcepreview.getforcurrentview) only when a compatible eye-tracking device is connected and required by your application.</span></span> <span data-ttu-id="d066c-144">Andernfalls ist das Zustimmungsdialogfeld nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d066c-144">Otherwise, the consent dialog is unnecessary.</span></span>

```csharp
    /// <summary>
    /// Initialize gaze tracking.
    /// </summary>
    /// <param name="gazeDevice"></param>
    private async void TryEnableGazeTrackingAsync(GazeDevicePreview gazeDevice)
    {
        // If eye-tracking device is ready, declare event handlers and start tracking.
        if (IsSupportedDevice(gazeDevice))
        {
            timerGaze.Interval = new TimeSpan(0, 0, 0, 0, 20);
            timerGaze.Tick += TimerGaze_Tick;

            SetGazeTargetLocation();

            // This must be called from the UI thread.
            gazeInputSource = GazeInputSourcePreview.GetForCurrentView();

            gazeInputSource.GazeEntered += GazeEntered;
            gazeInputSource.GazeMoved += GazeMoved;
            gazeInputSource.GazeExited += GazeExited;
        }
        // Notify if device calibration required.
        else if (gazeDevice.ConfigurationState ==
                    GazeDeviceConfigurationStatePreview.UserCalibrationNeeded ||
                    gazeDevice.ConfigurationState ==
                    GazeDeviceConfigurationStatePreview.ScreenSetupNeeded)
        {
            // Device isn't calibrated, so invoke the calibration handler.
            System.Diagnostics.Debug.WriteLine(
                "Your device needs to calibrate. Please wait for it to finish.");
            await gazeDevice.RequestCalibrationAsync();
        }
        // Notify if device calibration underway.
        else if (gazeDevice.ConfigurationState == 
            GazeDeviceConfigurationStatePreview.Configuring)
        {
            // Device is currently undergoing calibration.  
            // A device update is sent when calibration complete.
            System.Diagnostics.Debug.WriteLine(
                "Your device is being configured. Please wait for it to finish"); 
        }
        // Device is not viable.
        else if (gazeDevice.ConfigurationState == GazeDeviceConfigurationStatePreview.Unknown)
        {
            // Notify if device is in unknown state.  
            // Reconfigure/recalbirate the device.  
            System.Diagnostics.Debug.WriteLine(
                "Your device is not ready. Please set up your device or reconfigure it."); 
        }
    }

    /// <summary>
    /// Check if eye-tracking device is viable.
    /// </summary>
    /// <param name="gazeDevice">Reference to eye-tracking device.</param>
    /// <returns>True, if device is viable; otherwise, false.</returns>
    private bool IsSupportedDevice(GazeDevicePreview gazeDevice)
    {
        TrackerState.Text = gazeDevice.ConfigurationState.ToString();
        return (gazeDevice.CanTrackEyes &&
                    gazeDevice.ConfigurationState == 
                    GazeDeviceConfigurationStatePreview.Ready);
    }
```

5. <span data-ttu-id="d066c-145">Als Nächstes richten wir unsere Blickereignishandler ein.</span><span class="sxs-lookup"><span data-stu-id="d066c-145">Next, we set up our gaze event handlers.</span></span>

    <span data-ttu-id="d066c-146">Wir blenden die Blickverfolgungsellipse in `GazeEntered` und `GazeExited` ein bzw. aus.</span><span class="sxs-lookup"><span data-stu-id="d066c-146">We display and hide the gaze tracking ellipse in `GazeEntered` and `GazeExited`, respectively.</span></span>

    <span data-ttu-id="d066c-147">In `GazeMoved` verschieben wir unsere Blickverfolgungsellipse basierend auf der [EyeGazePosition](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazepointpreview.eyegazeposition), die vom [CurrentPoint](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeenteredprevieweventargs.currentpoint) der [GazeEnteredPreviewEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeenteredprevieweventargs) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d066c-147">In `GazeMoved`, we move our gaze tracking ellipse based on the [EyeGazePosition](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazepointpreview.eyegazeposition) provided by the [CurrentPoint](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeenteredprevieweventargs.currentpoint) of the [GazeEnteredPreviewEventArgs](https://docs.microsoft.com/uwp/api/windows.devices.input.preview.gazeenteredprevieweventargs).</span></span> <span data-ttu-id="d066c-148">Wir verwalten auch den Blickfokus-Timer in der [RadialProgressBar](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/controls/radialprogressbar), der die Neupositionierung der Fortschrittsleiste auslöst.</span><span class="sxs-lookup"><span data-stu-id="d066c-148">We also manage the gaze focus timer on the [RadialProgressBar](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/controls/radialprogressbar), which triggers repositioning of the progress bar.</span></span> <span data-ttu-id="d066c-149">Einzelheiten erfahren Sie im nächsten Schritt.</span><span class="sxs-lookup"><span data-stu-id="d066c-149">See next step for details.</span></span>

    ```csharp
    /// <summary>
    /// GazeEntered handler.
    /// </summary>
    /// <param name="sender">Source of the gaze entered event</param>
    /// <param name="e">Event args for the gaze entered event</param>
    private void GazeEntered(
        GazeInputSourcePreview sender, 
        GazeEnteredPreviewEventArgs args)
    {
        // Show ellipse representing gaze point.
        eyeGazePositionEllipse.Visibility = Visibility.Visible;

        // Mark the event handled.
        args.Handled = true;
    }

    /// <summary>
    /// GazeExited handler.
    /// Call DisplayRequest.RequestRelease to conclude the 
    /// RequestActive called in GazeEntered.
    /// </summary>
    /// <param name="sender">Source of the gaze exited event</param>
    /// <param name="e">Event args for the gaze exited event</param>
    private void GazeExited(
        GazeInputSourcePreview sender, 
        GazeExitedPreviewEventArgs args)
    {
        // Hide gaze tracking ellipse.
        eyeGazePositionEllipse.Visibility = Visibility.Collapsed;

        // Mark the event handled.
        args.Handled = true;
    }

    /// <summary>
    /// GazeMoved handler translates the ellipse on the canvas to reflect gaze point.
    /// </summary>
    /// <param name="sender">Source of the gaze moved event</param>
    /// <param name="e">Event args for the gaze moved event</param>
    private void GazeMoved(GazeInputSourcePreview sender, GazeMovedPreviewEventArgs args)
    {
        // Update the position of the ellipse corresponding to gaze point.
        if (args.CurrentPoint.EyeGazePosition != null)
        {
            double gazePointX = args.CurrentPoint.EyeGazePosition.Value.X;
            double gazePointY = args.CurrentPoint.EyeGazePosition.Value.Y;

            double ellipseLeft = 
                gazePointX - 
                (eyeGazePositionEllipse.Width / 2.0f);
            double ellipseTop = 
                gazePointY - 
                (eyeGazePositionEllipse.Height / 2.0f) - 
                (int)Header.ActualHeight;

            // Translate transform for moving gaze ellipse.
            TranslateTransform translateEllipse = new TranslateTransform
            {
                X = ellipseLeft,
                Y = ellipseTop
            };

            eyeGazePositionEllipse.RenderTransform = translateEllipse;

            // The gaze point screen location.
            Point gazePoint = new Point(gazePointX, gazePointY);

            // Basic hit test to determine if gaze point is on progress bar.
            bool hitRadialProgressBar = 
                DoesElementContainPoint(
                    gazePoint, 
                    GazeRadialProgressBar.Name, 
                    GazeRadialProgressBar); 

            // Use progress bar thickness for visual feedback.
            if (hitRadialProgressBar)
            {
                GazeRadialProgressBar.Thickness = 10;
            }
            else
            {
                GazeRadialProgressBar.Thickness = 4;
            }

            // Mark the event handled.
            args.Handled = true;
        }
    }
    ```
6. <span data-ttu-id="d066c-150">Hier folgen schließlich die Methoden zum Verwalten des Blickfokus-Timers für diese App.</span><span class="sxs-lookup"><span data-stu-id="d066c-150">Finally, here are the methods used to manage the gaze focus timer for this app.</span></span>

    `DoesElementContainPoint` <span data-ttu-id="d066c-151">Überprüft, ob der Blickzeiger über der Statusanzeige ist.</span><span class="sxs-lookup"><span data-stu-id="d066c-151">checks if the gaze pointer is over the progress bar.</span></span> <span data-ttu-id="d066c-152">Wenn ja, wird der Timer gestartet, und die Statusanzeige wird bei jedem Zeitgebertakt erhöht.</span><span class="sxs-lookup"><span data-stu-id="d066c-152">If so, it starts the gaze timer and increments the progress bar on each gaze timer tick.</span></span>

    `SetGazeTargetLocation` <span data-ttu-id="d066c-153">Legt die ursprüngliche Position der Statusanzeige fest und verschiebt die Statusanzeige, wenn die Statusanzeige abgeschlossen wird (je nach Blickfokus-Timer) an eine zufällige Stelle.</span><span class="sxs-lookup"><span data-stu-id="d066c-153">sets the initial location of the progress bar and, if the progress bar completes (depending on the gaze focus timer), moves the progress bar to a random location.</span></span>

    ```csharp
    /// <summary>
    /// Return whether the gaze point is over the progress bar.
    /// </summary>
    /// <param name="gazePoint">The gaze point screen location</param>
    /// <param name="elementName">The progress bar name</param>
    /// <param name="uiElement">The progress bar UI element</param>
    /// <returns></returns>
    private bool DoesElementContainPoint(
        Point gazePoint, string elementName, UIElement uiElement)
    {
        // Use entire visual tree of progress bar.
        IEnumerable<UIElement> elementStack = 
            VisualTreeHelper.FindElementsInHostCoordinates(gazePoint, uiElement, true);
        foreach (UIElement item in elementStack)
        {
            //Cast to FrameworkElement and get element name.
            if (item is FrameworkElement feItem)
            {
                if (feItem.Name.Equals(elementName))
                {
                    if (!timerStarted)
                    {
                        // Start gaze timer if gaze over element.
                        timerGaze.Start();
                        timerStarted = true;
                    }
                    return true;
                }
            }
        }

        // Stop gaze timer and reset progress bar if gaze leaves element.
        timerGaze.Stop();
        GazeRadialProgressBar.Value = 0;
        timerStarted = false;
        return false;
    }

    /// <summary>
    /// Tick handler for gaze focus timer.
    /// </summary>
    /// <param name="sender">Source of the gaze entered event</param>
    /// <param name="e">Event args for the gaze entered event</param>
    private void TimerGaze_Tick(object sender, object e)
    {
        // Increment progress bar.
        GazeRadialProgressBar.Value += 1;

        // If progress bar reaches maximum value, reset and relocate.
        if (GazeRadialProgressBar.Value == 100)
        {
            SetGazeTargetLocation();
        }
    }

    /// <summary>
    /// Set/reset the screen location of the progress bar.
    /// </summary>
    private void SetGazeTargetLocation()
    {
        // Ensure the gaze timer restarts on new progress bar location.
        timerGaze.Stop();
        timerStarted = false;

        // Get the bounding rectangle of the app window.
        Rect appBounds = Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().VisibleBounds;

        // Translate transform for moving progress bar.
        TranslateTransform translateTarget = new TranslateTransform();

        // Calculate random location within gaze canvas.
            Random random = new Random();
            int randomX = 
                random.Next(
                    0, 
                    (int)appBounds.Width - (int)GazeRadialProgressBar.Width);
            int randomY = 
                random.Next(
                    0, 
                    (int)appBounds.Height - (int)GazeRadialProgressBar.Height - (int)Header.ActualHeight);

        translateTarget.X = randomX;
        translateTarget.Y = randomY;

        GazeRadialProgressBar.RenderTransform = translateTarget;

        // Show progress bar.
        GazeRadialProgressBar.Visibility = Visibility.Visible;
        GazeRadialProgressBar.Value = 0;
    }
    ```

## <a name="see-also"></a><span data-ttu-id="d066c-154">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="d066c-154">See also</span></span>

### <a name="resources"></a><span data-ttu-id="d066c-155">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d066c-155">Resources</span></span>

- [<span data-ttu-id="d066c-156">Windows-Community-Toolkit Bibliothek für Anvisieren</span><span class="sxs-lookup"><span data-stu-id="d066c-156">Windows Community Toolkit Gaze library</span></span>](https://docs.microsoft.com/en-us/windows/uwpcommunitytoolkit/gaze/gazeinteractionlibrary)

### <a name="topic-samples"></a><span data-ttu-id="d066c-157">Themenbeispiele</span><span class="sxs-lookup"><span data-stu-id="d066c-157">Topic samples</span></span>

- [<span data-ttu-id="d066c-158">Beispiel für Anvisieren (einfach) (C#)</span><span class="sxs-lookup"><span data-stu-id="d066c-158">Gaze sample (basic) (C#)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-gazeinput-basic.zip)
