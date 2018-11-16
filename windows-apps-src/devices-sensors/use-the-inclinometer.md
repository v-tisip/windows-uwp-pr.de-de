---
author: muhsinking
ms.assetid: 16AD53CA-1252-456C-8567-2263D3EC95F3
title: Verwenden des Neigungsmessers
description: Hier erfahren Sie, wie Sie mithilfe des Neigungsmessers Werte für Stampf-, Roll- und Gierwinkel ermitteln.
ms.author: mukin
ms.date: 06/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: dd335d56fb2a01ed1b9255f974bcaacd47f623f5
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7119205"
---
# <a name="use-the-inclinometer"></a><span data-ttu-id="8a7ee-104">Verwenden des Neigungsmessers</span><span class="sxs-lookup"><span data-stu-id="8a7ee-104">Use the inclinometer</span></span>


**<span data-ttu-id="8a7ee-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="8a7ee-105">Important APIs</span></span>**

-   [**<span data-ttu-id="8a7ee-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="8a7ee-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="8a7ee-107">Neigungsmesser</span><span class="sxs-lookup"><span data-stu-id="8a7ee-107">Inclinometer</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225766)

**<span data-ttu-id="8a7ee-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a7ee-108">Sample</span></span>**

-   <span data-ttu-id="8a7ee-109">Eine umfassendere Implementierung finden Sie unter [Beispiel für einen Neigungsmesser](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Inclinometer).</span><span class="sxs-lookup"><span data-stu-id="8a7ee-109">For a more complete implementation, see the [inclinometer sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Inclinometer).</span></span>

<span data-ttu-id="8a7ee-110">Hier erfahren Sie, wie Sie mithilfe des Neigungsmessers Werte für Gier-, Roll- und Nickwinkel ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-110">Learn how to use the inclinometer to determine pitch, roll, and yaw.</span></span>

<span data-ttu-id="8a7ee-111">Bei einigen 3D-Spielen wird ein Neigungsmesser als Eingabegerät benötigt.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-111">Some 3-D games require an inclinometer as an input device.</span></span> <span data-ttu-id="8a7ee-112">Ein gängiges Beispiel hierfür ist ein Flugsimulator, der die drei Achsen des Neigungsmessers (X, Y und Z) dem Höhenleitwerk sowie dem Quer- und Seitenruder eines Flugzeugs zuordnet.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-112">One common example is the flight simulator, which maps the three axes of the inclinometer (X, Y, and Z) to the elevator, aileron, and rudder inputs of the aircraft.</span></span>

 ## <a name="prerequisites"></a><span data-ttu-id="8a7ee-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8a7ee-113">Prerequisites</span></span>

<span data-ttu-id="8a7ee-114">Sie sollten mit Extensible Application Markup Language (XAML), Microsoft für VisualC++- und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-114">You should be familiar with Extensible Application Markup Language (XAML), Microsoft VisualC#, and events.</span></span>

<span data-ttu-id="8a7ee-115">Das verwendete Gerät oder der Emulator muss einen Neigungsmesser unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-115">The device or emulator that you're using must support a inclinometer.</span></span>

 ## <a name="create-a-simple-inclinometer-app"></a><span data-ttu-id="8a7ee-116">Erstellen einer einfachen Neigungsmesser-App</span><span class="sxs-lookup"><span data-stu-id="8a7ee-116">Create a simple inclinometer app</span></span>

<span data-ttu-id="8a7ee-117">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="8a7ee-117">This section is divided into two subsections.</span></span> <span data-ttu-id="8a7ee-118">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Neigungsmesseranwendung.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-118">The first subsection will take you through the steps necessary to create a simple inclinometer application from scratch.</span></span> <span data-ttu-id="8a7ee-119">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-119">The following subsection explains the app you have just created.</span></span>

###  <a name="instructions"></a><span data-ttu-id="8a7ee-120">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8a7ee-120">Instructions</span></span>

-   <span data-ttu-id="8a7ee-121">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-121">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="8a7ee-122">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-122">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

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

    using Windows.UI.Core;
    using Windows.Devices.Sensors;


    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            private Inclinometer _inclinometer;

            // This event handler writes the current inclinometer reading to
            // the three text blocks on the app' s main page.

            private async void ReadingChanged(object sender, InclinometerReadingChangedEventArgs e)
            {
                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    InclinometerReading reading = e.Reading;
                    txtPitch.Text = String.Format("{0,5:0.00}", reading.PitchDegrees);
                    txtRoll.Text = String.Format("{0,5:0.00}", reading.RollDegrees);
                    txtYaw.Text = String.Format("{0,5:0.00}", reading.YawDegrees);
                });
            }

            public MainPage()
            {
                this.InitializeComponent();
                _inclinometer = Inclinometer.GetDefault();


                if (_inclinometer != null)
                {
                    // Establish the report interval for all scenarios
                    uint minReportInterval = _inclinometer.MinimumReportInterval;
                    uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                    _inclinometer.ReportInterval = reportInterval;

                    // Establish the event handler
                    _inclinometer.ReadingChanged += new TypedEventHandler<Inclinometer, InclinometerReadingChangedEventArgs>(ReadingChanged);
                }
            }
        }
    }
```

<span data-ttu-id="8a7ee-123">Sie müssen den Namespace im vorhergehenden Codeausschnitt durch den Namen ersetzen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-123">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="8a7ee-124">Wenn Sie z.B. ein Projekt mit dem Namen **InclinometerCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace InclinometerCS`.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-124">For example, if you created a project named **InclinometerCS**, you'd replace `namespace App1` with `namespace InclinometerCS`.</span></span>

-   <span data-ttu-id="8a7ee-125">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-125">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

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
            <TextBlock HorizontalAlignment="Left" Height="21" Margin="0,8,0,0" TextWrapping="Wrap" Text="Pitch: " VerticalAlignment="Top" Width="45" Foreground="#FFF9F4F4"/>
            <TextBlock x:Name="txtPitch" HorizontalAlignment="Left" Height="21" Margin="59,8,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="71" Foreground="#FFFDF9F9"/>
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="0,29,0,0" TextWrapping="Wrap" Text="Roll:" VerticalAlignment="Top" Width="55" Foreground="#FFF7F1F1"/>
            <TextBlock x:Name="txtRoll" HorizontalAlignment="Left" Height="23" Margin="59,29,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="50" Foreground="#FFFCF9F9"/>
            <TextBlock HorizontalAlignment="Left" Height="19" Margin="0,56,0,0" TextWrapping="Wrap" Text="Yaw:" VerticalAlignment="Top" Width="55" Foreground="#FFF7F3F3"/>
            <TextBlock x:Name="txtYaw" HorizontalAlignment="Left" Height="19" Margin="55,56,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="54" Foreground="#FFF6F2F2"/>

        </Grid>
    </Page>
```

<span data-ttu-id="8a7ee-126">Sie müssen den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-126">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="8a7ee-127">Wenn Sie z.B. ein Projekt mit dem Namen **InclinometerCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="InclinometerCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-127">For example, if you created a project named **InclinometerCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="InclinometerCS.MainPage"`.</span></span> <span data-ttu-id="8a7ee-128">Ersetzen Sie außerdem `xmlns:local="using:App1"` durch `xmlns:local="using:InclinometerCS"`.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-128">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:InclinometerCS"`.</span></span>

-   <span data-ttu-id="8a7ee-129">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-129">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="8a7ee-130">Wenn die App ausgeführt wird, können Sie die Neigungsmesserwerte ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-130">Once the app is running, you can change the inclinometer values by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="8a7ee-131">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-131">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

###  <a name="explanation"></a><span data-ttu-id="8a7ee-132">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="8a7ee-132">Explanation</span></span>

<span data-ttu-id="8a7ee-133">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Neigungsmessereingaben in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-133">The previous example demonstrates how little code you'll need to write in order to integrate inclinometer input in your app.</span></span>

<span data-ttu-id="8a7ee-134">Die App stellt eine Verbindung mit dem Standardneigungsmesser in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-134">The app establishes a connection with the default inclinometer in the **MainPage** method.</span></span>

```csharp
_inclinometer = Inclinometer.GetDefault();
```

<span data-ttu-id="8a7ee-135">Die App legt das Berichtsintervall in der **MainPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-135">The app establishes the report interval within the **MainPage** method.</span></span> <span data-ttu-id="8a7ee-136">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16 Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="8a7ee-136">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="8a7ee-137">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-137">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="8a7ee-138">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-138">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _inclinometer.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_inclinometer.ReportInterval = reportInterval;
```

<span data-ttu-id="8a7ee-139">Die neuen Neigungsmesserdaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-139">The new inclinometer data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="8a7ee-140">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-140">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="8a7ee-141">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-141">The app registers this event handler on the following line.</span></span>

```csharp
_inclinometer.ReadingChanged += new TypedEventHandler<Inclinometer,
InclinometerReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="8a7ee-142">Die neuen Werte werden in die TextBlock-Elemente des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="8a7ee-142">These new values are written to the TextBlocks found in the project's XAML.</span></span>

```xml
<TextBlock HorizontalAlignment="Left" Height="21" Margin="0,8,0,0" TextWrapping="Wrap" Text="Pitch: " VerticalAlignment="Top" Width="45" Foreground="#FFF9F4F4"/>
 <TextBlock x:Name="txtPitch" HorizontalAlignment="Left" Height="21" Margin="59,8,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="71" Foreground="#FFFDF9F9"/>
 <TextBlock HorizontalAlignment="Left" Height="23" Margin="0,29,0,0" TextWrapping="Wrap" Text="Roll:" VerticalAlignment="Top" Width="55" Foreground="#FFF7F1F1"/>
 <TextBlock x:Name="txtRoll" HorizontalAlignment="Left" Height="23" Margin="59,29,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="50" Foreground="#FFFCF9F9"/>
 <TextBlock HorizontalAlignment="Left" Height="19" Margin="0,56,0,0" TextWrapping="Wrap" Text="Yaw:" VerticalAlignment="Top" Width="55" Foreground="#FFF7F3F3"/>
 <TextBlock x:Name="txtYaw" HorizontalAlignment="Left" Height="19" Margin="55,56,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="54" Foreground="#FFF6F2F2"/>
```

