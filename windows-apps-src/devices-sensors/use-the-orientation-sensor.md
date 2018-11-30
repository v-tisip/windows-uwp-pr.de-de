---
ms.assetid: 1889AC3A-A472-4294-89B8-A642668A8A6E
title: Verwenden des Ausrichtungssensors
description: Hier erfahren Sie, wie Sie mithilfe der Ausrichtungssensoren die Ausrichtung des Geräts ermitteln.
ms.date: 06/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 16d1ea6186cc8ccabacd1751db61e752a97930f7
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8324262"
---
# <a name="use-the-orientation-sensor"></a><span data-ttu-id="d6ee0-104">Verwenden des Ausrichtungssensors</span><span class="sxs-lookup"><span data-stu-id="d6ee0-104">Use the orientation sensor</span></span>


**<span data-ttu-id="d6ee0-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d6ee0-105">Important APIs</span></span>**

-   [**<span data-ttu-id="d6ee0-106">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="d6ee0-106">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="d6ee0-107">OrientationSensor</span><span class="sxs-lookup"><span data-stu-id="d6ee0-107">OrientationSensor</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206371)
-   [**<span data-ttu-id="d6ee0-108">SimpleOrientation</span><span class="sxs-lookup"><span data-stu-id="d6ee0-108">SimpleOrientation</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206399)

**<span data-ttu-id="d6ee0-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d6ee0-109">Samples</span></span>**

-   [<span data-ttu-id="d6ee0-110">Beispiel für einen Ausrichtungssensor</span><span class="sxs-lookup"><span data-stu-id="d6ee0-110">Orientation sensor sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/OrientationSensor)
-   [<span data-ttu-id="d6ee0-111">Beispiel für einen einfachen Ausrichtungssensor</span><span class="sxs-lookup"><span data-stu-id="d6ee0-111">Simple orientation sensor sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleOrientationSensor)

<span data-ttu-id="d6ee0-112">Hier erfahren Sie, wie Sie mithilfe der Ausrichtungssensoren die Ausrichtung des Geräts ermitteln.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-112">Learn how to use the orientation sensors to determine the device orientation.</span></span>

<span data-ttu-id="d6ee0-113">Der [**Windows.Devices.Sensors**](https://msdn.microsoft.com/library/windows/apps/BR206408)-Namespace enthält zwei unterschiedliche Arten von Ausrichtungssensor-APIs: [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) und [**SimpleOrientation**](https://msdn.microsoft.com/library/windows/apps/BR206399).</span><span class="sxs-lookup"><span data-stu-id="d6ee0-113">There are two different types of orientation sensor APIs included in the [**Windows.Devices.Sensors**](https://msdn.microsoft.com/library/windows/apps/BR206408) namespace: [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) and [**SimpleOrientation**](https://msdn.microsoft.com/library/windows/apps/BR206399).</span></span> <span data-ttu-id="d6ee0-114">Zwar handelt es sich bei beiden Sensoren um Ausrichtungssensoren, sie werden jedoch für vollkommen unterschiedliche Zwecke verwendet.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-114">While both of these sensors are orientation sensors, that term is overloaded and they are used for very different purposes.</span></span> <span data-ttu-id="d6ee0-115">Aber da beide Ausrichtungssensoren sind, werden auch beide in diesem Artikel behandelt.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-115">However, since both are orientation sensors, they are both covered in this article.</span></span>

<span data-ttu-id="d6ee0-116">Die [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371)-API wird in 3D-Apps verwendet, um eine Quaternionen- und eine Drehungsmatrix zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-116">The [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) API is used for 3-D apps two obtain a quaternion and a rotation matrix.</span></span> <span data-ttu-id="d6ee0-117">Eine Quaternion können Sie sich am einfachsten als Drehung eines Punkts \[x,y,z\] um eine beliebige Achse vorstellen (im Gegensatz zu einer Drehungsmatrix, die Drehungen um drei Achsen darstellt).</span><span class="sxs-lookup"><span data-stu-id="d6ee0-117">A quaternion can be most easily understood as a rotation of a point \[x,y,z\] about an arbitrary axis (contrasted with a rotation matrix, which represents rotations around three axes).</span></span> <span data-ttu-id="d6ee0-118">Die Mathematik hinter Quaternions ist recht exotisch, da sie die geometrischen Eigenschaften komplexer Zahlen und die mathematischen Eigenschaften imaginärer Zahlen umfasst. Das Arbeiten mit ihnen ist jedoch einfach, und sie werden von Frameworks wie DirectX unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-118">The mathematics behind quaternions is fairly exotic in that it involves the geometric properties of complex numbers and mathematical properties of imaginary numbers, but working with them is simple, and frameworks like DirectX support them.</span></span> <span data-ttu-id="d6ee0-119">Eine komplexe 3D-App kann mithilfe des Ausrichtungssensors die Perspektive des Benutzers anpassen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-119">A complex 3-D app can use the Orientation sensor to adjust the user's perspective.</span></span> <span data-ttu-id="d6ee0-120">Dieser Sensor kombiniert Eingaben von Beschleunigungssensor, Gyrometer und Kompass.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-120">This sensor combines input from the accelerometer, gyrometer, and compass.</span></span>

<span data-ttu-id="d6ee0-121">Die [**SimpleOrientation**](https://msdn.microsoft.com/library/windows/apps/BR206399)-API dient zum Ermitteln der aktuellen Ausrichtung des Geräts gemäß Definitionen wie „portrait up“, „portrait down“, „landscape left“ und „landscape right“.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-121">The [**SimpleOrientation**](https://msdn.microsoft.com/library/windows/apps/BR206399) API is used to determine the current device orientation in terms of definitions like portrait up, portrait down, landscape left, and landscape right.</span></span> <span data-ttu-id="d6ee0-122">Außerdem kann sie erkennen, ob die Oberseite des Geräts nach oben oder nach unten zeigt.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-122">It can also detect if a device is face-up or face-down.</span></span> <span data-ttu-id="d6ee0-123">Dieser Sensor gibt keine Eigenschaften wie „portrait up“ oder „landscape left“, sondern Rotationswerte wie „Not rotated“, „Rotated90DegreesCounterclockwise“ usw. zurück.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-123">Rather than returning properties like "portrait up" or "landscape left", this sensor returns a rotation value: "Not rotated", "Rotated90DegreesCounterclockwise", and so on.</span></span> <span data-ttu-id="d6ee0-124">In der folgenden Tabelle werden die allgemeinen Ausrichtungseigenschaften den entsprechenden Sensorwerten zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-124">The following table maps common orientation properties to the corresponding sensor reading.</span></span>

| <span data-ttu-id="d6ee0-125">Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="d6ee0-125">Orientation</span></span>     | <span data-ttu-id="d6ee0-126">Entsprechender Sensorwert</span><span class="sxs-lookup"><span data-stu-id="d6ee0-126">Corresponding sensor reading</span></span>      |
|-----------------|-----------------------------------|
| <span data-ttu-id="d6ee0-127">Portrait Up</span><span class="sxs-lookup"><span data-stu-id="d6ee0-127">Portrait Up</span></span>     | <span data-ttu-id="d6ee0-128">NotRotated</span><span class="sxs-lookup"><span data-stu-id="d6ee0-128">NotRotated</span></span>                        |
| <span data-ttu-id="d6ee0-129">Landscape Left</span><span class="sxs-lookup"><span data-stu-id="d6ee0-129">Landscape Left</span></span>  | <span data-ttu-id="d6ee0-130">Rotated90DegreesCounterclockwise</span><span class="sxs-lookup"><span data-stu-id="d6ee0-130">Rotated90DegreesCounterclockwise</span></span>  |
| <span data-ttu-id="d6ee0-131">Portrait Down</span><span class="sxs-lookup"><span data-stu-id="d6ee0-131">Portrait Down</span></span>   | <span data-ttu-id="d6ee0-132">Rotated180DegreesCounterclockwise</span><span class="sxs-lookup"><span data-stu-id="d6ee0-132">Rotated180DegreesCounterclockwise</span></span> |
| <span data-ttu-id="d6ee0-133">Landscape Right</span><span class="sxs-lookup"><span data-stu-id="d6ee0-133">Landscape Right</span></span> | <span data-ttu-id="d6ee0-134">Rotated270DegreesCounterclockwise</span><span class="sxs-lookup"><span data-stu-id="d6ee0-134">Rotated270DegreesCounterclockwise</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="d6ee0-135">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d6ee0-135">Prerequisites</span></span>

<span data-ttu-id="d6ee0-136">Sie sollten mit Extensible Application Markup Language (XAML), Microsoft für VisualC++ c# und Ereignissen vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-136">You should be familiar with Extensible Application Markup Language (XAML), Microsoft VisualC#, and events.</span></span>

<span data-ttu-id="d6ee0-137">Das verwendete Gerät oder der Emulator muss einen Ausrichtungssensor unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-137">The device or emulator that you're using must support a orientation sensor.</span></span>

## <a name="create-an-orientationsensor-app"></a><span data-ttu-id="d6ee0-138">Erstellen einer OrientationSensor-App</span><span class="sxs-lookup"><span data-stu-id="d6ee0-138">Create an OrientationSensor app</span></span>

<span data-ttu-id="d6ee0-139">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="d6ee0-139">This section is divided into two subsections.</span></span> <span data-ttu-id="d6ee0-140">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer Ausrichtungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-140">The first subsection will take you through the steps necessary to create an orientation application from scratch.</span></span> <span data-ttu-id="d6ee0-141">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-141">The following subsection explains the app you have just created.</span></span>

###  <a name="instructions"></a><span data-ttu-id="d6ee0-142">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d6ee0-142">Instructions</span></span>

-   <span data-ttu-id="d6ee0-143">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-143">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="d6ee0-144">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-144">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

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

    // The Blank Page item template is documented at http://go.microsoft.com/fwlink/p/?linkid=234238

    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            private OrientationSensor _sensor;

            private async void ReadingChanged(object sender, OrientationSensorReadingChangedEventArgs e)
            {
                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    OrientationSensorReading reading = e.Reading;

                    // Quaternion values
                    txtQuaternionX.Text = String.Format("{0,8:0.00000}", reading.Quaternion.X);
                    txtQuaternionY.Text = String.Format("{0,8:0.00000}", reading.Quaternion.Y);
                    txtQuaternionZ.Text = String.Format("{0,8:0.00000}", reading.Quaternion.Z);
                    txtQuaternionW.Text = String.Format("{0,8:0.00000}", reading.Quaternion.W);

                    // Rotation Matrix values
                    txtM11.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M11);
                    txtM12.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M12);
                    txtM13.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M13);
                    txtM21.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M21);
                    txtM22.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M22);
                    txtM23.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M23);
                    txtM31.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M31);
                    txtM32.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M32);
                    txtM33.Text = String.Format("{0,8:0.00000}", reading.RotationMatrix.M33);
                });
            }

            public MainPage()
            {
                this.InitializeComponent();
                _sensor = OrientationSensor.GetDefault();

                // Establish the report interval for all scenarios
                uint minReportInterval = _sensor.MinimumReportInterval;
                uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
                _sensor.ReportInterval = reportInterval;

                // Establish event handler
                _sensor.ReadingChanged += new TypedEventHandler<OrientationSensor, OrientationSensorReadingChangedEventArgs>(ReadingChanged);
            }
        }
    }
```

<span data-ttu-id="d6ee0-145">Sie müssen den Namespace im vorhergehenden Codeausschnitt durch den Namen ersetzen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-145">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="d6ee0-146">Wenn Sie z.B. ein Projekt mit dem Namen **OrientationSensorCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace OrientationSensorCS`.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-146">For example, if you created a project named **OrientationSensorCS**, you'd replace `namespace App1` with `namespace OrientationSensorCS`.</span></span>

-   <span data-ttu-id="d6ee0-147">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-147">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

```xml
        <Page
        x:Class="App1.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:App1"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid x:Name="LayoutRoot" Background="Black">
            <TextBlock HorizontalAlignment="Left" Height="28" Margin="4,4,0,0" TextWrapping="Wrap" Text="M11:" VerticalAlignment="Top" Width="46"/>
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="4,36,0,0" TextWrapping="Wrap" Text="M12:" VerticalAlignment="Top" Width="39"/>
            <TextBlock HorizontalAlignment="Left" Height="24" Margin="4,72,0,0" TextWrapping="Wrap" Text="M13:" VerticalAlignment="Top" Width="39"/>
            <TextBlock HorizontalAlignment="Left" Height="31" Margin="4,118,0,0" TextWrapping="Wrap" Text="M21:" VerticalAlignment="Top" Width="39"/>
            <TextBlock HorizontalAlignment="Left" Height="24" Margin="4,160,0,0" TextWrapping="Wrap" Text="M22:" VerticalAlignment="Top" Width="39"/>
            <TextBlock HorizontalAlignment="Left" Height="24" Margin="8,201,0,0" TextWrapping="Wrap" Text="M23:" VerticalAlignment="Top" Width="35"/>
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="4,234,0,0" TextWrapping="Wrap" Text="M31:" VerticalAlignment="Top" Width="39"/>
            <TextBlock HorizontalAlignment="Left" Height="28" Margin="4,274,0,0" TextWrapping="Wrap" Text="M32:" VerticalAlignment="Top" Width="46"/>
            <TextBlock HorizontalAlignment="Left" Height="21" Margin="4,322,0,0" TextWrapping="Wrap" Text="M33:" VerticalAlignment="Top" Width="39"/>
            <TextBlock x:Name="txtM11" HorizontalAlignment="Left" Height="19" Margin="43,4,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM12" HorizontalAlignment="Left" Height="23" Margin="43,36,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM13" HorizontalAlignment="Left" Height="15" Margin="43,72,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM21" HorizontalAlignment="Left" Height="20" Margin="43,114,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM22" HorizontalAlignment="Left" Height="19" Margin="43,156,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM23" HorizontalAlignment="Left" Height="16" Margin="43,197,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM31" HorizontalAlignment="Left" Height="17" Margin="43,230,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM32" HorizontalAlignment="Left" Height="19" Margin="43,270,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock x:Name="txtM33" HorizontalAlignment="Left" Height="21" Margin="43,322,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="53"/>
            <TextBlock HorizontalAlignment="Left" Height="15" Margin="194,8,0,0" TextWrapping="Wrap" Text="Quaternion X:" VerticalAlignment="Top" Width="81"/>
            <TextBlock HorizontalAlignment="Left" Height="23" Margin="194,36,0,0" TextWrapping="Wrap" Text="Quaternion Y:" VerticalAlignment="Top" Width="81"/>
            <TextBlock HorizontalAlignment="Left" Height="15" Margin="194,72,0,0" TextWrapping="Wrap" Text="Quaternion Z:" VerticalAlignment="Top" Width="81"/>
            <TextBlock x:Name="txtQuaternionX" HorizontalAlignment="Left" Height="15" Margin="279,8,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="104"/>
            <TextBlock x:Name="txtQuaternionY" HorizontalAlignment="Left" Height="12" Margin="275,36,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="108"/>
            <TextBlock x:Name="txtQuaternionZ" HorizontalAlignment="Left" Height="19" Margin="275,68,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="89"/>
            <TextBlock HorizontalAlignment="Left" Height="21" Margin="194,96,0,0" TextWrapping="Wrap" Text="Quaternion W:" VerticalAlignment="Top" Width="81"/>
            <TextBlock x:Name="txtQuaternionW" HorizontalAlignment="Left" Height="12" Margin="279,96,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="72"/>

        </Grid>
    </Page>
```

<span data-ttu-id="d6ee0-148">Sie müssen den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-148">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="d6ee0-149">Wenn Sie z.B. ein Projekt mit dem Namen **OrientationSensorCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="OrientationSensorCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-149">For example, if you created a project named **OrientationSensorCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="OrientationSensorCS.MainPage"`.</span></span> <span data-ttu-id="d6ee0-150">Außerdem sollten Sie `xmlns:local="using:App1"` durch `xmlns:local="using:OrientationSensorCS"` ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-150">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:OrientationSensorCS"`.</span></span>

-   <span data-ttu-id="d6ee0-151">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-151">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="d6ee0-152">Wenn die App ausgeführt wird, können Sie die Ausrichtung ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-152">Once the app is running, you can change the orientation by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="d6ee0-153">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-153">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

###  <a name="explanation"></a><span data-ttu-id="d6ee0-154">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="d6ee0-154">Explanation</span></span>

<span data-ttu-id="d6ee0-155">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Angaben des Ausrichtungssensors in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-155">The previous example demonstrates how little code you'll need to write in order to integrate orientation-sensor input in your app.</span></span>

<span data-ttu-id="d6ee0-156">Die App stellt eine Verbindung mit dem Standardausrichtungssensor in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-156">The app establishes a connection with the default orientation sensor in the **MainPage** method.</span></span>

```csharp
_sensor = OrientationSensor.GetDefault();
```

<span data-ttu-id="d6ee0-157">Die App legt das Berichtsintervall in der **MainPage**-Methode fest.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-157">The app establishes the report interval within the **MainPage** method.</span></span> <span data-ttu-id="d6ee0-158">Mit diesem Code wird das vom Gerät unterstützte Mindestintervall abgerufen und mit einem angeforderten Intervall von 16 Millisekunden verglichen (entspricht etwa einer Aktualisierungsrate von 60Hz).</span><span class="sxs-lookup"><span data-stu-id="d6ee0-158">This code retrieves the minimum interval supported by the device and compares it to a requested interval of 16 milliseconds (which approximates a 60-Hz refresh rate).</span></span> <span data-ttu-id="d6ee0-159">Wenn das unterstützte Mindestintervall größer als das angeforderte Intervall ist, legt der Code den Wert auf das Minimum fest.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-159">If the minimum supported interval is greater than the requested interval, the code sets the value to the minimum.</span></span> <span data-ttu-id="d6ee0-160">Andernfalls wird der Wert auf das angeforderte Intervall festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-160">Otherwise, it sets the value to the requested interval.</span></span>

```csharp
uint minReportInterval = _sensor.MinimumReportInterval;
uint reportInterval = minReportInterval > 16 ? minReportInterval : 16;
_sensor.ReportInterval = reportInterval;
```

<span data-ttu-id="d6ee0-161">Die neuen Sensordaten werden in der **ReadingChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-161">The new sensor data is captured in the **ReadingChanged** method.</span></span> <span data-ttu-id="d6ee0-162">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-162">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="d6ee0-163">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-163">The app registers this event handler on the following line.</span></span>

```csharp
_sensor.ReadingChanged += new TypedEventHandler<OrientationSensor,
OrientationSensorReadingChangedEventArgs>(ReadingChanged);
```

<span data-ttu-id="d6ee0-164">Die neuen Werte werden in die TextBlock-Elemente des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-164">These new values are written to the TextBlocks found in the project's XAML.</span></span>

## <a name="create-a-simpleorientation-app"></a><span data-ttu-id="d6ee0-165">Erstellen einer SimpleOrientation-App</span><span class="sxs-lookup"><span data-stu-id="d6ee0-165">Create a SimpleOrientation app</span></span>

<span data-ttu-id="d6ee0-166">Dieser Abschnitt ist in zwei Unterabschnitte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="d6ee0-166">This section is divided into two subsections.</span></span> <span data-ttu-id="d6ee0-167">Der erste Unterabschnitt enthält die Schritte zum Erstellen einer einfachen Ausrichtungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-167">The first subsection will take you through the steps necessary to create a simple orientation application from scratch.</span></span> <span data-ttu-id="d6ee0-168">Im zweiten Unterabschnitt wird die erstellte App dann näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-168">The following subsection explains the app you have just created.</span></span>

### <a name="instructions"></a><span data-ttu-id="d6ee0-169">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d6ee0-169">Instructions</span></span>

-   <span data-ttu-id="d6ee0-170">Erstellen Sie ein neues Projekt. Wählen Sie dabei unter den Projektvorlagen für **VisualC#** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-170">Create a new project, choosing a **Blank App (Universal Windows)** from the **Visual C#** project templates.</span></span>

-   <span data-ttu-id="d6ee0-171">Öffnen Sie die Projektdatei „MainPage.xaml.cs“, und ersetzen Sie den vorhandenen Code durch den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-171">Open your project's MainPage.xaml.cs file and replace the existing code with the following.</span></span>

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
    // The Blank Page item template is documented at http://go.microsoft.com/fwlink/p/?linkid=234238

    namespace App1
    {
        /// <summary>
        /// An empty page that can be used on its own or navigated to within a Frame.
        /// </summary>
        public sealed partial class MainPage : Page
        {
            // Sensor and dispatcher variables
            private SimpleOrientationSensor _simpleorientation;

            // This event handler writes the current sensor reading to
            // a text block on the app' s main page.

            private async void OrientationChanged(object sender, SimpleOrientationSensorOrientationChangedEventArgs e)
            {
                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    SimpleOrientation orientation = e.Orientation;
                    switch (orientation)
                    {
                        case SimpleOrientation.NotRotated:
                            txtOrientation.Text = "Not Rotated";
                            break;
                        case SimpleOrientation.Rotated90DegreesCounterclockwise:
                            txtOrientation.Text = "Rotated 90 Degrees Counterclockwise";
                            break;
                        case SimpleOrientation.Rotated180DegreesCounterclockwise:
                            txtOrientation.Text = "Rotated 180 Degrees Counterclockwise";
                            break;
                        case SimpleOrientation.Rotated270DegreesCounterclockwise:
                            txtOrientation.Text = "Rotated 270 Degrees Counterclockwise";
                            break;
                        case SimpleOrientation.Faceup:
                            txtOrientation.Text = "Faceup";
                            break;
                        case SimpleOrientation.Facedown:
                            txtOrientation.Text = "Facedown";
                            break;
                        default:
                            txtOrientation.Text = "Unknown orientation";
                            break;
                    }
                });
            }

            public MainPage()
            {
                this.InitializeComponent();
                _simpleorientation = SimpleOrientationSensor.GetDefault();

                // Assign an event handler for the sensor orientation-changed event
                if (_simpleorientation != null)
                {
                    _simpleorientation.OrientationChanged += new TypedEventHandler<SimpleOrientationSensor, SimpleOrientationSensorOrientationChangedEventArgs>(OrientationChanged);
                }
            }
        }
    }
```

<span data-ttu-id="d6ee0-172">Sie müssen den Namespace im vorhergehenden Codeausschnitt durch den Namen ersetzen, den Sie für Ihr Projekt angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-172">You'll need to rename the namespace in the previous snippet with the name you gave your project.</span></span> <span data-ttu-id="d6ee0-173">Wenn Sie z.B. ein Projekt mit dem Namen **SimpleOrientationCS** erstellt haben, ersetzen Sie `namespace App1` durch `namespace SimpleOrientationCS`.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-173">For example, if you created a project named **SimpleOrientationCS**, you'd replace `namespace App1` with `namespace SimpleOrientationCS`.</span></span>

-   <span data-ttu-id="d6ee0-174">Öffnen Sie die Datei „MainPage.xaml“, und ersetzen Sie den ursprünglichen Inhalt durch den folgenden XML-Code.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-174">Open the file MainPage.xaml and replace the original contents with the following XML.</span></span>

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
            <TextBlock HorizontalAlignment="Left" Height="24" Margin="8,8,0,0" TextWrapping="Wrap" Text="Current Orientation:" VerticalAlignment="Top" Width="101" Foreground="#FFF8F7F7"/>
            <TextBlock x:Name="txtOrientation" HorizontalAlignment="Left" Height="24" Margin="118,8,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="175" Foreground="#FFFEFAFA"/>

        </Grid>
    </Page>
```

<span data-ttu-id="d6ee0-175">Sie müssen den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-175">You'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="d6ee0-176">Wenn Sie z.B. ein Projekt mit dem Namen **SimpleOrientationCS** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="SimpleOrientationCS.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-176">For example, if you created a project named **SimpleOrientationCS**, you'd replace `x:Class="App1.MainPage"` with `x:Class="SimpleOrientationCS.MainPage"`.</span></span> <span data-ttu-id="d6ee0-177">Außerdem sollten Sie `xmlns:local="using:App1"` durch `xmlns:local="using:SimpleOrientationCS"` ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-177">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:SimpleOrientationCS"`.</span></span>

-   <span data-ttu-id="d6ee0-178">Drücken Sie F5 oder wählen Sie **Debuggen** > **Debugging starten** aus, um die App zu erstellen, bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-178">Press F5 or select **Debug** > **Start Debugging** to build, deploy, and run the app.</span></span>

<span data-ttu-id="d6ee0-179">Wenn die App ausgeführt wird, können Sie die Ausrichtung ändern, indem Sie das Gerät bewegen oder die Emulatortools verwenden.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-179">Once the app is running, you can change the orientation by moving the device or using the emulator tools.</span></span>

-   <span data-ttu-id="d6ee0-180">Beenden Sie die App, indem Sie zu Visual Studio zurückkehren und UMSCHALT+F5 drücken oder **Debuggen** > **Debugging beenden** auswählen.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-180">Stop the app by returning to Visual Studio and pressing Shift+F5 or select **Debug** > **Stop Debugging** to stop the app.</span></span>

### <a name="explanation"></a><span data-ttu-id="d6ee0-181">Erläuterung</span><span class="sxs-lookup"><span data-stu-id="d6ee0-181">Explanation</span></span>

<span data-ttu-id="d6ee0-182">Das vorherige Beispiel zeigt, wie wenig Code Sie schreiben müssen, um Angaben des SimpleOrientation-Sensors in eine App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-182">The previous example demonstrates how little code you'll need to write in order to integrate simple-orientation sensor input in your app.</span></span>

<span data-ttu-id="d6ee0-183">Die App stellt eine Verbindung mit dem Standardsensor in der **MainPage**-Methode her.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-183">The app establishes a connection with the default sensor in the **MainPage** method.</span></span>

```csharp
_simpleorientation = SimpleOrientationSensor.GetDefault();
```

<span data-ttu-id="d6ee0-184">Die neuen Sensordaten werden in der **OrientationChanged**-Methode erfasst.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-184">The new sensor data is captured in the **OrientationChanged** method.</span></span> <span data-ttu-id="d6ee0-185">Wenn der Sensortreiber neue Daten vom Sensor empfängt, übergibt er die Werte mithilfe dieses Ereignishandlers an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-185">Each time the sensor driver receives new data from the sensor, it passes the values to your app using this event handler.</span></span> <span data-ttu-id="d6ee0-186">Die App registriert diesen Ereignishandler in der folgenden Zeile.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-186">The app registers this event handler on the following line.</span></span>

```csharp
_simpleorientation.OrientationChanged += new TypedEventHandler<SimpleOrientationSensor,
SimpleOrientationSensorOrientationChangedEventArgs>(OrientationChanged);
```

<span data-ttu-id="d6ee0-187">Diese neuen Werte werden in ein TextBlock-Element des XAML-Projektcodes geschrieben.</span><span class="sxs-lookup"><span data-stu-id="d6ee0-187">These new values are written to a TextBlock found in the project's XAML.</span></span>

```csharp
<TextBlock HorizontalAlignment="Left" Height="24" Margin="8,8,0,0" TextWrapping="Wrap" Text="Current Orientation:" VerticalAlignment="Top" Width="101" Foreground="#FFF8F7F7"/>
 <TextBlock x:Name="txtOrientation" HorizontalAlignment="Left" Height="24" Margin="118,8,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top" Width="175" Foreground="#FFFEFAFA"/>
```