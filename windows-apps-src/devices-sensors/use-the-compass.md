---
author: muhsinking
ms.assetid: 5B30E32F-27E0-4656-A834-391A559AC8BC
title: Verwenden des Kompasses
description: Hier erfahren Sie, wie Sie mithilfe des Kompasses die aktuelle Richtung ermitteln.
ms.author: mukin
ms.date: 06/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4af6b0fb339ba1fde3ea94f456eac98be8a1db9b
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5986328"
---
# <a name="use-the-compass"></a><span data-ttu-id="84c5c-104">Verwenden des Kompasses</span><span class="sxs-lookup"><span data-stu-id="84c5c-104">Use the compass</span></span>


**<span data-ttu-id="84c5c-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="84c5c-105">Important APIs</span></span>**

-   [**<span data-ttu-id="84c5c-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="84c5c-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="84c5c-107">Kompass</span><span class="sxs-lookup"><span data-stu-id="84c5c-107">Compass</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225705)

**<span data-ttu-id="84c5c-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="84c5c-108">Sample</span></span>**

-   <span data-ttu-id="84c5c-109">Eine umfassendere Implementierung finden Sie unter [Beispiel für einen Kompass](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Compass).</span><span class="sxs-lookup"><span data-stu-id="84c5c-109">For a more complete implementation, see the [compass sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Compass).</span></span>

<span data-ttu-id="84c5c-110">Hier erfahren Sie, wie Sie mithilfe des Kompasses die aktuelle Richtung ermitteln.</span><span class="sxs-lookup"><span data-stu-id="84c5c-110">Learn how to use the compass to determine the current heading.</span></span>

<span data-ttu-id="84c5c-111">Apps können die aktuelle Richtung anhand des magnetischen oder geografischen Nordpols bestimmen.</span><span class="sxs-lookup"><span data-stu-id="84c5c-111">An app can retrieve the current heading with respect to magnetic, or true, north.</span></span> <span data-ttu-id="84c5c-112">Navigations-Apps bestimmen mit dem Kompass die Richtung, in die das Gerät weist, und passen damit die Karte an.</span><span class="sxs-lookup"><span data-stu-id="84c5c-112">Navigation apps use the compass to determine the direction a device is facing and then orient the map accordingly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84c5c-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="84c5c-113">Prerequisites</span></span>

<span data-ttu-id="84c5c-114">Sie sollten mit Extensible Application Markup Language (XAML), Microsoft für VisualC++ c# und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="84c5c-114">You should be familiar with Extensible Application Markup Language (XAML), Microsoft VisualC#, and events.</span></span>

<span data-ttu-id="84c5c-115">Das verwendete Gerät oder der Emulator muss einen Kompass unterstützen.</span><span class="sxs-lookup"><span data-stu-id="84c5c-115">The device or emulator that you're using must support a compass.</span></span>

## <a name="create-a-simple-compass-app"></a><span data-ttu-id="84c5c-116">Erstellen einer einfachen Kompass-App</span><span class="sxs-lookup"><span data-stu-id="84c5c-116">Create a simple compass app</span></span>

<span data-ttu-id="84c5c-117">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="84c5c-117">This section is divided into two subsections.</span></span> <span data-ttu-id="84c5c-118">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Kompassanwendung.</span><span class="sxs-lookup"><span data-stu-id="84c5c-118">The first subsection will take you through the steps necessary to create a simple compass application from scratch.</span></span> <span data-ttu-id="84c5c-119">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="84c5c-119">The following subsection explains the app you have just created.</span></span>

### <a name="instructions"></a><span data-ttu-id="84c5c-120">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="84c5c-120">Instructions</span></span>

-   <span data-ttu-id="84c5c-121">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="84c5c-121">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="84c5c-122">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="84c5c-122">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

```csharp
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Linq;
    using Windows.Foundation;
    using Windows.Foundation.Collections;
    using Windows.UI.Xaml;
    using Windows.UI.Xaml.Controls;
    using Windows.UI.Xaml.Controls.Primitives;
    using Windows.UI.Xaml.Data;
    using Windows.UI.Xaml.Input;
    using Windows.UI.Xaml.Media;
    using Windows.UI.Xaml.Navigation;

    using Windows.UI.Core; // Required to access the core dispatcher object
    using Windows.Devices.Sensors; // Required to access the sensor platform and the compass


    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            private Compass _compass; // Our app' s compass object

            // This event handler writes the current compass reading to
            // the textblocks on the app' s main page.

            private async void ReadingChanged(object sender, CompassReadingChangedEventArgs e)
            {
               await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    CompassReading reading = e.Reading;
                    txtMagnetic.Text = String.Format("{0,5:0.00}", reading.HeadingMagneticNorth);
                    if (reading.HeadingTrueNorth.HasValue)
                        txtNorth.Text = String.Format("{0,5:0.00}", reading.HeadingTrueNorth);
                    else
                        txtNorth.Text = "No reading.";
                });
            }

            public MainPage()
            {
                this.InitializeComponent();
               _compass = Compass.GetDefault(); // Get the default compass object

                // Assign an event handler for the compass reading-changed event
                if (_compass != null)
                {
                    // Establish the report interval for all scenarios
                    uint minReportInterval = _compass.MinimumReportInterval;
                    uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                    _compass.ReportInterval = reportInterval;
                    _compass.ReadingChanged += new TypedEventHandler<Compass, CompassReadingChangedEventArgs>(ReadingChanged);
                }
            }
        }
    }
    ```

You'll need to rename the namespace in the previous snippet with the name you gave your project. For example, if you created a project named **CompassCS**, you'd replace `namespace App1` with `namespace CompassCS`.

-   Open the file MainPage.xaml and replace the original contents with the following XML.

```xml
        <Page
        x:Class="App1.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:App1"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid x:Name="LayoutRoot" Background="#FF0C0C0C">
            <TextBlock HorizontalAlignment="Left" Height="22" Margin="8,18,0,0" TextWrapping="Wrap" Text="Magnetic Heading:" VerticalAlignment="Top" Width="104" Foreground="#FFFBF9F9"/>
            <TextBlock HorizontalAlignment="Left" Height="18" Margin="8,58,0,0" TextWrapping="Wrap" Text="True North Heading:" VerticalAlignment="Top" Width="104" Foreground="#FFF3F3F3"/>
            <TextBlock x:Name="txtMagnetic" HorizontalAlignment="Left" Height="22" Margin="130,18,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="116" Foreground="#FFFBF6F6"/>
            <TextBlock x:Name="txtNorth" HorizontalAlignment="Left" Height="18" Margin="130,58,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="116" Foreground="#FFF5F1F1"/>

         </Grid>
    </Page>
```

<span data-ttu-id="84c5c-123">Ersetzen Sie im obigen Codeausschnitt den ersten Teil des Klassennamens durch den Namespace Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="84c5c-123">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="84c5c-124">Wenn Sie z.B. ein Projekt mit dem Namen **CompassCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="CompassCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="84c5c-124">For example, if you created a project named **CompassCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="CompassCS.MainPage"`.</span></span> <span data-ttu-id="84c5c-125">Ersetzen Sie außerdem `xmlns:local="using:App1"` durch `xmlns:local="using:CompassCS"`.</span><span class="sxs-lookup"><span data-stu-id="84c5c-125">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:CompassCS"`.</span></span>

-   <span data-ttu-id="84c5c-126">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="84c5c-126">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="84c5c-127">Wenn die App ausgeführt wird, können Sie die Kompasswerte ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="84c5c-127">Once the app is running, you can change the compass values by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="84c5c-128">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="84c5c-128">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

### <a name="explanation"></a><span data-ttu-id="84c5c-129">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="84c5c-129">Explanation</span></span>

<span data-ttu-id="84c5c-130">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Kompasswerte in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="84c5c-130">The previous example demonstrates how little code you'll need to write in order to integrate compass input in your app.</span></span>

<span data-ttu-id="84c5c-131">Die App stellt eine Verbindung mit dem Standardkompass in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="84c5c-131">The app establishes a connection with the default compass in the **MainPage** method.</span></span>

```csharp
_compass = Compass.GetDefault(); // Get the default compass object
```

<span data-ttu-id="84c5c-132">Die App legt das Berichtsintervall in der **MainPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="84c5c-132">The app establishes the report interval within the **MainPage** method.</span></span> <span data-ttu-id="84c5c-133">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16 Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="84c5c-133">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="84c5c-134">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="84c5c-134">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="84c5c-135">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="84c5c-135">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _compass.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_compass.ReportInterval = reportInterval;
```

<span data-ttu-id="84c5c-136">Die neuen Kompassdaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="84c5c-136">The new compass data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="84c5c-137">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="84c5c-137">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="84c5c-138">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="84c5c-138">The app registers this event handler on the following line.</span></span>

```csharp
_compass.ReadingChanged += new TypedEventHandler<Compass,
CompassReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="84c5c-139">Die neuen Werte werden in die TextBlock-Elemente des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="84c5c-139">These new values are written to the TextBlocks found in the project's XAML.</span></span>

```xml
 <TextBlock HorizontalAlignment="Left" Height="22" Margin="8,18,0,0" TextWrapping="Wrap" Text="Magnetic Heading:" VerticalAlignment="Top" Width="104" Foreground="#FFFBF9F9"/>
 <TextBlock HorizontalAlignment="Left" Height="18" Margin="8,58,0,0" TextWrapping="Wrap" Text="True North Heading:" VerticalAlignment="Top" Width="104" Foreground="#FFF3F3F3"/>
 <TextBlock x:Name="txtMagnetic" HorizontalAlignment="Left" Height="22" Margin="130,18,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="116" Foreground="#FFFBF6F6"/>
 <TextBlock x:Name="txtNorth" HorizontalAlignment="Left" Height="18" Margin="130,58,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="116" Foreground="#FFF5F1F1"/>
```
 

 
