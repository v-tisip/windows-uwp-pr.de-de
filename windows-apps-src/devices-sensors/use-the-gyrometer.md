---
author: muhsinking
ms.assetid: 454953E1-DD8F-44B7-A614-7BAD8C683536
title: Verwenden des Gyrometers
description: Hier erfahren Sie, wie Sie mithilfe des Gyrometers Bewegungsänderungen des Benutzers erkennen.
ms.author: mukin
ms.date: 06/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 25be2cfab15378f14aed61dcaae1e7e85159f36e
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4747798"
---
# <a name="use-the-gyrometer"></a><span data-ttu-id="2440f-104">Verwenden des Gyrometers</span><span class="sxs-lookup"><span data-stu-id="2440f-104">Use the gyrometer</span></span>


**<span data-ttu-id="2440f-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2440f-105">Important APIs</span></span>**

-   [**<span data-ttu-id="2440f-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="2440f-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="2440f-107">Gyrometer</span><span class="sxs-lookup"><span data-stu-id="2440f-107">Gyrometer</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225718)

**<span data-ttu-id="2440f-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2440f-108">Sample</span></span>**

-   <span data-ttu-id="2440f-109">Eine umfassendere Implementierung finden Sie unter [Beispiel für ein Gyrometer](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/gyrometer).</span><span class="sxs-lookup"><span data-stu-id="2440f-109">For a more complete implementation, see the [gyrometer sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/gyrometer).</span></span>

<span data-ttu-id="2440f-110">Hier erfahren Sie, wie Sie mithilfe des Gyrometers Bewegungsänderungen des Benutzers erkennen.</span><span class="sxs-lookup"><span data-stu-id="2440f-110">Learn how to use the gyrometer to detect changes in user movement.</span></span>

<span data-ttu-id="2440f-111">Gyrometer und Beschleunigungssensoren ergänzen sich gegenseitig als Spielecontroller.</span><span class="sxs-lookup"><span data-stu-id="2440f-111">Gyrometers compliment accelerometers as game controllers.</span></span> <span data-ttu-id="2440f-112">Mit dem Beschleunigungsmesser können Sie die Bewegung in eine Richtung messen, während das Gyrometer die Winkelgeschwindigkeit (oder Drehbewegungen) misst.</span><span class="sxs-lookup"><span data-stu-id="2440f-112">The accelerometer can measure linear motion while the gyrometer measures angular velocity or rotational motion.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2440f-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2440f-113">Prerequisites</span></span>

<span data-ttu-id="2440f-114">Sie sollten mit XAML (Extensible Application Markup Language), Microsoft VisualC# und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="2440f-114">You should be familiar with Extensible Application Markup Language (XAML), Microsoft Visual C#, and events.</span></span>

<span data-ttu-id="2440f-115">Das verwendete Gerät oder der Emulator muss ein Gyrometer unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2440f-115">The device or emulator that you're using must support a gyrometer.</span></span>

## <a name="create-a-simple-gyrometer-app"></a><span data-ttu-id="2440f-116">Erstellen einer einfachen Gyrometer-App</span><span class="sxs-lookup"><span data-stu-id="2440f-116">Create a simple gyrometer app</span></span>

<span data-ttu-id="2440f-117">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="2440f-117">This section is divided into two subsections.</span></span> <span data-ttu-id="2440f-118">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Gyrometeranwendung.</span><span class="sxs-lookup"><span data-stu-id="2440f-118">The first subsection will take you through the steps necessary to create a simple gyrometer application from scratch.</span></span> <span data-ttu-id="2440f-119">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="2440f-119">The following subsection explains the app you have just created.</span></span>

###  <a name="instructions"></a><span data-ttu-id="2440f-120">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="2440f-120">Instructions</span></span>

-   <span data-ttu-id="2440f-121">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="2440f-121">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="2440f-122">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="2440f-122">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

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
    using Windows.Devices.Sensors; // Required to access the sensor platform and the gyrometer


    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            private Gyrometer _gyrometer; // Our app' s gyrometer object

            // This event handler writes the current gyrometer reading to
            // the three textblocks on the app' s main page.

            private async void ReadingChanged(object sender, GyrometerReadingChangedEventArgs e)
            {
                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    GyrometerReading reading = e.Reading;
                    txtXAxis.Text = String.Format("{0,5:0.00}", reading.AngularVelocityX);
                    txtYAxis.Text = String.Format("{0,5:0.00}", reading.AngularVelocityY);
                    txtZAxis.Text = String.Format("{0,5:0.00}", reading.AngularVelocityZ);
                });
            }

            public MainPage()
            {
                this.InitializeComponent();
                _gyrometer = Gyrometer.GetDefault(); // Get the default gyrometer sensor object

                if (_gyrometer != null)
                {
                    // Establish the report interval for all scenarios
                    uint minReportInterval = _gyrometer.MinimumReportInterval;
                    uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                    _gyrometer.ReportInterval = reportInterval;

                    // Assign an event handler for the gyrometer reading-changed event
                    _gyrometer.ReadingChanged += new TypedEventHandler<Gyrometer, GyrometerReadingChangedEventArgs>(ReadingChanged);
                }

            }
        }
    }
```

<span data-ttu-id="2440f-123">Ersetzen Sie den Namespace aus dem vorhergehenden Codeausschnitt durch den Namen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="2440f-123">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="2440f-124">Wenn Sie z.B. ein Projekt mit dem Namen **GyrometerCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace GyrometerCS`.</span><span class="sxs-lookup"><span data-stu-id="2440f-124">For example, if you created a project named **GyrometerCS**, you'd replace `namespace App1` with `namespace GyrometerCS`.</span></span>

-   <span data-ttu-id="2440f-125">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="2440f-125">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

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
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="8,8,0,0" TextWrapping="Wrap" Text="X-Axis:" VerticalAlignment="Top" Width="46" Foreground="#FFFDFDFD"/>
            <TextBlock x:Name="txtXAxis" HorizontalAlignment="Left" Height="23" Margin="67,8,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="88" Foreground="#FFFDFAFA"/>
            <TextBlock HorizontalAlignment="Left" Height="20" Margin="8,52,0,0" TextWrapping="Wrap" Text="Y Axis:" VerticalAlignment="Top" Width="46" Foreground="White"/>
            <TextBlock x:Name="txtYAxis" HorizontalAlignment="Left" Height="24" Margin="54,48,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="80" Foreground="#FFFBFBFB"/>
            <TextBlock HorizontalAlignment="Left" Height="21" Margin="8,93,0,0" TextWrapping="Wrap" Text="Z Axis:" VerticalAlignment="Top" Width="46" Foreground="#FFFEFBFB"/>
            <TextBlock x:Name="txtZAxis" HorizontalAlignment="Left" Height="21" Margin="54,93,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="63" Foreground="#FFF8F3F3"/>

        </Grid>
    </Page>
```

<span data-ttu-id="2440f-126">Der erste Teil des Klassennamens aus dem vorhergehenden Codeausschnitt muss durch den Namespace Ihrer App ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="2440f-126">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="2440f-127">Wenn Sie etwa ein Projekt mit dem Namen **GyrometerCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="GyrometerCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="2440f-127">For example, if you created a project named **GyrometerCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="GyrometerCS.MainPage"`.</span></span> <span data-ttu-id="2440f-128">Ersetzen Sie außerdem `xmlns:local="using:App1"` durch `xmlns:local="using:GyrometerCS"`.</span><span class="sxs-lookup"><span data-stu-id="2440f-128">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:GyrometerCS"`.</span></span>

-   <span data-ttu-id="2440f-129">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2440f-129">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="2440f-130">Wenn die App ausgeführt wird, können Sie die Gyrometerwerte ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="2440f-130">Once the app is running, you can change the gyrometer values by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="2440f-131">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="2440f-131">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

###  <a name="explanation"></a><span data-ttu-id="2440f-132">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="2440f-132">Explanation</span></span>

<span data-ttu-id="2440f-133">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Gyrometerangaben in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="2440f-133">The previous example demonstrates how little code you'll need to write in order to integrate gyrometer input in your app.</span></span>

<span data-ttu-id="2440f-134">Die App stellt eine Verbindung mit dem Standardgyrometer in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="2440f-134">The app establishes a connection with the default gyrometer in the **MainPage** method.</span></span>

```csharp
_gyrometer = Gyrometer.GetDefault(); // Get the default gyrometer sensor object
```

<span data-ttu-id="2440f-135">Die App legt das Berichtsintervall in der **MainPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="2440f-135">The app establishes the report interval within the **MainPage** method.</span></span> <span data-ttu-id="2440f-136">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16 Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="2440f-136">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="2440f-137">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="2440f-137">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="2440f-138">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2440f-138">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _gyrometer.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_gyrometer.ReportInterval = reportInterval;
```

<span data-ttu-id="2440f-139">Die neuen Gyrometerdaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="2440f-139">The new gyrometer data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="2440f-140">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="2440f-140">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="2440f-141">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="2440f-141">The app registers this event handler on the following line.</span></span>

```csharp
_gyrometer.ReadingChanged += new TypedEventHandler<Gyrometer,
GyrometerReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="2440f-142">Die neuen Werte werden in die TextBlock-Elemente des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="2440f-142">These new values are written to the TextBlocks found in the project's XAML.</span></span>

```xml
        <TextBlock HorizontalAlignment="Left" Height="23" Margin="8,8,0,0" TextWrapping="Wrap" Text="X-Axis:" VerticalAlignment="Top" Width="46" Foreground="#FFFDFDFD"/>
        <TextBlock x:Name="txtXAxis" HorizontalAlignment="Left" Height="23" Margin="67,8,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="88" Foreground="#FFFDFAFA"/>
        <TextBlock HorizontalAlignment="Left" Height="20" Margin="8,52,0,0" TextWrapping="Wrap" Text="Y Axis:" VerticalAlignment="Top" Width="46" Foreground="White"/>
        <TextBlock x:Name="txtYAxis" HorizontalAlignment="Left" Height="24" Margin="54,48,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="80" Foreground="#FFFBFBFB"/>
        <TextBlock HorizontalAlignment="Left" Height="21" Margin="8,93,0,0" TextWrapping="Wrap" Text="Z Axis:" VerticalAlignment="Top" Width="46" Foreground="#FFFEFBFB"/>
        <TextBlock x:Name="txtZAxis" HorizontalAlignment="Left" Height="21" Margin="54,93,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="63" Foreground="#FFF8F3F3"/>
```

 ## <a name="related-topics"></a><span data-ttu-id="2440f-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2440f-143">Related topics</span></span>

* [<span data-ttu-id="2440f-144">Gyrometerbeispiel</span><span class="sxs-lookup"><span data-stu-id="2440f-144">Gyrometer Sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=241379)
