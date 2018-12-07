---
ms.assetid: 15BAB25C-DA8C-4F13-9B8F-EA9E4270BCE9
title: Verwenden des Lichtsensors
description: Hier erfahren Sie, wie Sie mithilfe des Umgebungslichtsensors veränderte Lichtverhältnisse erkennen.
ms.date: 06/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 47092c128fe3a3855d7e32706451545b357c39c4
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8780711"
---
# <a name="use-the-light-sensor"></a><span data-ttu-id="352a6-104">Verwenden des Lichtsensors</span><span class="sxs-lookup"><span data-stu-id="352a6-104">Use the light sensor</span></span>


**<span data-ttu-id="352a6-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="352a6-105">Important APIs</span></span>**

-   [**<span data-ttu-id="352a6-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="352a6-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="352a6-107">LightSensor</span><span class="sxs-lookup"><span data-stu-id="352a6-107">LightSensor</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225790)

**<span data-ttu-id="352a6-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="352a6-108">Sample</span></span>**

-   <span data-ttu-id="352a6-109">Eine umfassendere Implementierung finden Sie unter [Beispiel für einen Lichtsensor](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LightSensor).</span><span class="sxs-lookup"><span data-stu-id="352a6-109">For a more complete implementation, see the [light sensor sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/LightSensor).</span></span>

<span data-ttu-id="352a6-110">Hier erfahren Sie, wie Sie mithilfe des Umgebungslichtsensors veränderte Lichtverhältnisse erkennen.</span><span class="sxs-lookup"><span data-stu-id="352a6-110">Learn how to use the ambient light sensor to detect changes in lighting.</span></span>

<span data-ttu-id="352a6-111">Der Umgebungslichtsensor ist einer von vielen Sensoren, mit denen Apps auf Veränderungen in der Umgebung des Benutzers reagieren können.</span><span class="sxs-lookup"><span data-stu-id="352a6-111">An ambient light sensor is one of the several types of environmental sensors that allow apps to respond to changes in the user's environment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="352a6-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="352a6-112">Prerequisites</span></span>

<span data-ttu-id="352a6-113">Sie sollten mit Extensible Application Markup Language (XAML), Microsoft für VisualC++ c# und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="352a6-113">You should be familiar with Extensible Application Markup Language (XAML), Microsoft VisualC#, and events.</span></span>

<span data-ttu-id="352a6-114">Das verwendete Gerät oder der Emulator muss einen Umgebungslichtsensor unterstützen.</span><span class="sxs-lookup"><span data-stu-id="352a6-114">The device or emulator that you're using must support an ambient light sensor.</span></span>

## <a name="create-a-simple-light-sensor-app"></a><span data-ttu-id="352a6-115">Erstellen einer einfachen Lichtsensor-App</span><span class="sxs-lookup"><span data-stu-id="352a6-115">Create a simple light-sensor app</span></span>

<span data-ttu-id="352a6-116">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="352a6-116">This section is divided into two subsections.</span></span> <span data-ttu-id="352a6-117">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Lichtsensoranwendung.</span><span class="sxs-lookup"><span data-stu-id="352a6-117">The first subsection will take you through the steps necessary to create a simple light-sensor application from scratch.</span></span> <span data-ttu-id="352a6-118">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="352a6-118">The following subsection explains the app you have just created.</span></span>

###  <a name="instructions"></a><span data-ttu-id="352a6-119">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="352a6-119">Instructions</span></span>

-   <span data-ttu-id="352a6-120">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="352a6-120">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="352a6-121">Öffnen Sie die Datei "BlankPage.xaml.cs" des Projekts, und ersetzen Sie den vorhandenen Code durch den folgenden.</span><span class="sxs-lookup"><span data-stu-id="352a6-121">Open your project's BlankPage.xaml.cs file and replace the existing code with the following.</span></span>

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
    using Windows.Devices.Sensors; // Required to access the sensor platform and the ALS

    // The Blank Page item template is documented at http://go.microsoft.com/fwlink/p/?linkid=234238

    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class BlankPage : Page
        {
            private LightSensor _lightsensor; // Our app' s lightsensor object

            // This event handler writes the current light-sensor reading to
            // the textbox named "txtLUX" on the app' s main page.

            private void ReadingChanged(object sender, LightSensorReadingChangedEventArgs e)
            {
                Dispatcher.RunAsync(CoreDispatcherPriority.Normal, (s, a) =>
                {
                    LightSensorReading reading = (a.Context as LightSensorReadingChangedEventArgs).Reading;
                    txtLuxValue.Text = String.Format("{0,5:0.00}", reading.IlluminanceInLux);
                });
            }

            public BlankPage()
            {
                InitializeComponent();
                _lightsensor = LightSensor.GetDefault(); // Get the default light sensor object

                // Assign an event handler for the ALS reading-changed event
                if (_lightsensor != null)
                {
                    // Establish the report interval for all scenarios
                    uint minReportInterval = _lightsensor.MinimumReportInterval;
                    uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                    _lightsensor.ReportInterval = reportInterval;

                    // Establish the even thandler
                    _lightsensor.ReadingChanged += new TypedEventHandler<LightSensor, LightSensorReadingChangedEventArgs>(ReadingChanged);
                }

            }

        }
    }
```

<span data-ttu-id="352a6-122">Sie müssen den Namespace im vorhergehenden Codeausschnitt durch den Namen ersetzen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="352a6-122">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="352a6-123">Wenn Sie z.B. ein Projekt mit dem Namen **LightingCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace LightingCS`.</span><span class="sxs-lookup"><span data-stu-id="352a6-123">For example, if you created a project named **LightingCS**, you'd replace `namespace App1` with `namespace LightingCS`.</span></span>

-   <span data-ttu-id="352a6-124">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="352a6-124">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

```xml
    <Page
        x:Class="App1.BlankPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:App1"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid x:Name="LayoutRoot" Background="Black">
            <TextBlock HorizontalAlignment="Left" Height="44" Margin="52,38,0,0" TextWrapping="Wrap" Text="LUX Reading" VerticalAlignment="Top" Width="150"/>
            <TextBlock x:Name="txtLuxValue" HorizontalAlignment="Left" Height="44" Margin="224,38,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="217"/>


        </Grid>

    </Page>
```

<span data-ttu-id="352a6-125">Sie müssen den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="352a6-125">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="352a6-126">Wenn Sie etwa ein Projekt mit dem Namen **LightingCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="LightingCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="352a6-126">For example, if you created a project named **LightingCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="LightingCS.MainPage"`.</span></span> <span data-ttu-id="352a6-127">Ersetzen Sie außerdem `xmlns:local="using:App1"` durch `xmlns:local="using:LightingCS"`.</span><span class="sxs-lookup"><span data-stu-id="352a6-127">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:LightingCS"`.</span></span>

-   <span data-ttu-id="352a6-128">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="352a6-128">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="352a6-129">Sobald die App ausgeführt wird, können Sie die Lichtsensorwerte ändern, indem das für den Sensor verfügbare Licht verändern oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="352a6-129">Once the app is running, you can change the light sensor values by altering the light available to the sensor or using the emulator tools.</span></span>

-   <span data-ttu-id="352a6-130">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="352a6-130">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

###  <a name="explanation"></a><span data-ttu-id="352a6-131">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="352a6-131">Explanation</span></span>

<span data-ttu-id="352a6-132">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Werte des Umgebungslichtsensors in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="352a6-132">The previous example demonstrates how little code you'll need to write in order to integrate light-sensor input in your app.</span></span>

<span data-ttu-id="352a6-133">Die App stellt eine Verbindung mit dem Standardsensor in der **BlankPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="352a6-133">The app establishes a connection with the default sensor in the **BlankPage** method.</span></span>

```csharp
_lightsensor = LightSensor.GetDefault(); // Get the default light sensor object
```

<span data-ttu-id="352a6-134">Die App legt das Berichtsintervall in der **BlankPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="352a6-134">The app establishes the report interval within the **BlankPage** method.</span></span> <span data-ttu-id="352a6-135">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="352a6-135">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="352a6-136">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="352a6-136">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="352a6-137">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="352a6-137">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _lightsensor.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_lightsensor.ReportInterval = reportInterval;
```
<span data-ttu-id="352a6-138">Die neuen Lichtsensordaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="352a6-138">The new light-sensor data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="352a6-139">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er den Wert mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="352a6-139">Each time the sensor driver receives new data from the sensor, it passes the value to your app using this event handler.</span></span> <span data-ttu-id="352a6-140">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="352a6-140">The app registers this event handler on the following line.</span></span>

```csharp
_lightsensor.ReadingChanged += new TypedEventHandler<LightSensor,
LightSensorReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="352a6-141">Diese neuen Werte werden in ein TextBlock-Element des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="352a6-141">These new values are written to a TextBlock found in the project's XAML.</span></span>

```xml
<TextBlock HorizontalAlignment="Left" Height="44" Margin="52,38,0,0" TextWrapping="Wrap" Text="LUX Reading" VerticalAlignment="Top" Width="150"/>
 <TextBlock x:Name="txtLuxValue" HorizontalAlignment="Left" Height="44" Margin="224,38,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="217"/>
```