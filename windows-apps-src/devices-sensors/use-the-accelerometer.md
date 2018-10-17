---
author: muhsinking
ms.assetid: F90686F5-641A-42D9-BC44-EC6CA11B8A42
title: Verwenden des Beschleunigungsmessers
description: Hier erfahren Sie, wie Sie mithilfe des Beschleunigungsmessers auf Benutzerbewegungen reagieren können.
ms.author: mukin
ms.date: 06/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2848b9a7326bdac084120ec9b75f067718f14853
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4755911"
---
# <a name="use-the-accelerometer"></a><span data-ttu-id="16a66-104">Verwenden des Beschleunigungsmessers</span><span class="sxs-lookup"><span data-stu-id="16a66-104">Use the accelerometer</span></span>


**<span data-ttu-id="16a66-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="16a66-105">Important APIs</span></span>**

-   [**<span data-ttu-id="16a66-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="16a66-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="16a66-107">Beschleunigungsmesser</span><span class="sxs-lookup"><span data-stu-id="16a66-107">Accelerometer</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225687)

**<span data-ttu-id="16a66-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="16a66-108">Sample</span></span>**

-   <span data-ttu-id="16a66-109">Eine umfassendere Implementierung finden Sie unter [Beispiel für einen Beschleunigungsmesser](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Accelerometer).</span><span class="sxs-lookup"><span data-stu-id="16a66-109">For a more complete implementation, see the [accelerometer sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Accelerometer).</span></span>

<span data-ttu-id="16a66-110">Hier erfahren Sie, wie Sie mithilfe des Beschleunigungsmessers auf Benutzerbewegungen reagieren können.</span><span class="sxs-lookup"><span data-stu-id="16a66-110">Learn how to use the accelerometer to respond to user movement.</span></span>

<span data-ttu-id="16a66-111">Eine einfache Spiele-App verwendet als Eingabegerät einen einzigen Sensor: den Beschleunigungsmesser.</span><span class="sxs-lookup"><span data-stu-id="16a66-111">A simple game app relies on a single sensor, the accelerometer, as an input device.</span></span> <span data-ttu-id="16a66-112">Diese Apps verwenden für die Eingabe in der Regel nur eine oder zwei Achsen. Als weitere Eingabequelle kann aber auch das Schüttelereignis verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="16a66-112">These apps typically use only one or two axes for input; but they may also use the shake event as another input source.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16a66-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="16a66-113">Prerequisites</span></span>

<span data-ttu-id="16a66-114">Sie sollten mit XAML (Extensible Application Markup Language), Microsoft VisualC# und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="16a66-114">You should be familiar with Extensible Application Markup Language (XAML), Microsoft Visual C#, and events.</span></span>

<span data-ttu-id="16a66-115">Das verwendete Gerät oder der Emulator muss einen Beschleunigungsmesser unterstützen.</span><span class="sxs-lookup"><span data-stu-id="16a66-115">The device or emulator that you're using must support an accelerometer.</span></span>

## <a name="create-a-simple-accelerometer-app"></a><span data-ttu-id="16a66-116">Erstellen einer einfachen Beschleunigungsmesser-App</span><span class="sxs-lookup"><span data-stu-id="16a66-116">Create a simple accelerometer app</span></span>

<span data-ttu-id="16a66-117">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="16a66-117">This section is divided into two subsections.</span></span> <span data-ttu-id="16a66-118">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Beschleunigungsmesseranwendung.</span><span class="sxs-lookup"><span data-stu-id="16a66-118">The first subsection will take you through the steps necessary to create a simple accelerometer application from scratch.</span></span> <span data-ttu-id="16a66-119">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="16a66-119">The following subsection explains the app you have just created.</span></span>

### <a name="instructions"></a><span data-ttu-id="16a66-120">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="16a66-120">Instructions</span></span>

-   <span data-ttu-id="16a66-121">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="16a66-121">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="16a66-122">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="16a66-122">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

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

    // Required to support the core dispatcher and the accelerometer

    using Windows.UI.Core;
    using Windows.Devices.Sensors;

    namespace App1
    {

        public sealed partial class MainPage : Page
        {
            // Sensor and dispatcher variables
            private Accelerometer _accelerometer;

            // This event handler writes the current accelerometer reading to
            // the three acceleration text blocks on the app' s main page.

            private async void ReadingChanged(object sender, AccelerometerReadingChangedEventArgs e)
            {
                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    AccelerometerReading reading = e.Reading;
                    txtXAxis.Text = String.Format("{0,5:0.00}", reading.AccelerationX);
                    txtYAxis.Text = String.Format("{0,5:0.00}", reading.AccelerationY);
                    txtZAxis.Text = String.Format("{0,5:0.00}", reading.AccelerationZ);

                });
            }

            public MainPage()
            {
                this.InitializeComponent();
                _accelerometer = Accelerometer.GetDefault();

                if (_accelerometer != null)
                {
                    // Establish the report interval
                    uint minReportInterval = _accelerometer.MinimumReportInterval;
                    uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                    _accelerometer.ReportInterval = reportInterval;

                    // Assign an event handler for the reading-changed event
                    _accelerometer.ReadingChanged += new TypedEventHandler<Accelerometer, AccelerometerReadingChangedEventArgs>(ReadingChanged);
                }
            }
        }
    }
```

<span data-ttu-id="16a66-123">Sie müssen den Namespace im vorhergehenden Codeausschnitt durch den Namen ersetzen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="16a66-123">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="16a66-124">Wenn Sie z.B. ein Projekt mit dem Namen **AccelerometerCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace AccelerometerCS`.</span><span class="sxs-lookup"><span data-stu-id="16a66-124">For example, if you created a project named **AccelerometerCS**, you'd replace `namespace App1` with `namespace AccelerometerCS`.</span></span>

-   <span data-ttu-id="16a66-125">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="16a66-125">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

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
            <TextBlock HorizontalAlignment="Left" Height="25" Margin="8,20,0,0" TextWrapping="Wrap" Text="X-axis:" VerticalAlignment="Top" Width="62" Foreground="#FFEDE6E6"/>
            <TextBlock HorizontalAlignment="Left" Height="27" Margin="8,49,0,0" TextWrapping="Wrap" Text="Y-axis:" VerticalAlignment="Top" Width="62" Foreground="#FFF5F2F2"/>
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="8,80,0,0" TextWrapping="Wrap" Text="Z-axis:" VerticalAlignment="Top" Width="62" Foreground="#FFF6F0F0"/>
            <TextBlock x:Name="txtXAxis" HorizontalAlignment="Left" Height="15" Margin="70,16,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="61" Foreground="#FFF2F2F2"/>
            <TextBlock x:Name="txtYAxis" HorizontalAlignment="Left" Height="15" Margin="70,49,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53" Foreground="#FFF2EEEE"/>
            <TextBlock x:Name="txtZAxis" HorizontalAlignment="Left" Height="15" Margin="70,80,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53" Foreground="#FFFFF8F8"/>

        </Grid>
    </Page>
```

<span data-ttu-id="16a66-126">Sie müssen den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="16a66-126">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="16a66-127">Wenn Sie etwa ein Projekt mit dem Namen **AccelerometerCS**erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="AccelerometerCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="16a66-127">For example, if you created a project named **AccelerometerCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="AccelerometerCS.MainPage"`.</span></span> <span data-ttu-id="16a66-128">Ersetzen Sie außerdem `xmlns:local="using:App1"` durch `xmlns:local="using:AccelerometerCS"`.</span><span class="sxs-lookup"><span data-stu-id="16a66-128">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:AccelerometerCS"`.</span></span>

-   <span data-ttu-id="16a66-129">Drücken Sie F5, oder wählen Sie **Debuggen** &gt; **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="16a66-129">Press F5 or select **Debug** &gt; **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="16a66-130">Wenn die App ausgeführt wird, können Sie die Beschleunigungsmesserwerte ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="16a66-130">Once the app is running, you can change the accelerometer values by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="16a66-131">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** &gt; **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="16a66-131">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** &gt; **Stop Debugging** to stop the app.</span></span>

### <a name="explanation"></a><span data-ttu-id="16a66-132">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="16a66-132">Explanation</span></span>

<span data-ttu-id="16a66-133">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Beschleunigungsmesserwerte in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="16a66-133">The previous example demonstrates how little code you'll need to write in order to integrate accelerometer input in your app.</span></span>

<span data-ttu-id="16a66-134">Die App stellt eine Verbindung mit dem Standardbeschleunigungsmesser in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="16a66-134">The app establishes a connection with the default accelerometer in the **MainPage** method.</span></span>

```csharp
_accelerometer = Accelerometer.GetDefault();
```

<span data-ttu-id="16a66-135">Die App legt das Berichtsintervall in der **MainPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="16a66-135">The app establishes the report interval within the **MainPage** method.</span></span> <span data-ttu-id="16a66-136">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16 Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="16a66-136">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="16a66-137">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="16a66-137">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="16a66-138">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="16a66-138">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _accelerometer.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_accelerometer.ReportInterval = reportInterval;
```

<span data-ttu-id="16a66-139">Die neuen Beschleunigungsmesserdaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="16a66-139">The new accelerometer data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="16a66-140">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="16a66-140">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="16a66-141">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="16a66-141">The app registers this event handler on the following line.</span></span>

```csharp
_accelerometer.ReadingChanged += new TypedEventHandler<Accelerometer,
AccelerometerReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="16a66-142">Die neuen Werte werden in die TextBlock-Elemente des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="16a66-142">These new values are written to the TextBlocks found in the project's XAML.</span></span>

```xml
<TextBlock x:Name="txtXAxis" HorizontalAlignment="Left" Height="15" Margin="70,16,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="61" Foreground="#FFF2F2F2"/>
 <TextBlock x:Name="txtYAxis" HorizontalAlignment="Left" Height="15" Margin="70,49,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53" Foreground="#FFF2EEEE"/>
 <TextBlock x:Name="txtZAxis" HorizontalAlignment="Left" Height="15" Margin="70,80,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53" Foreground="#FFFFF8F8"/>
```
