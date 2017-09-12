---
author: mukin
ms.assetid: B4A550E7-1639-4C9A-A229-31E22B1415E7
title: Sensorausrichtung
description: "Sensordaten der Klassen Accelerometer, Gyrometer, Compass, Inclinometer und OrientationSensor sind durch ihre Referenzachsen definiert. Diese Achsen werden durch das Querformat des Geräts bestimmt und drehen sich mit dem Gerät, wenn es vom Benutzer gedreht wird."
ms.author: mukin
ms.date: 05/24/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: a91e38aa11f7fa25804d6d6f11cc030ee1613311
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="sensor-orientation"></a><span data-ttu-id="73456-105">Sensorausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-105">Sensor orientation</span></span>

<span data-ttu-id="73456-106">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="73456-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="73456-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="73456-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="73456-108">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="73456-108">Important APIs</span></span>**

-   [**<span data-ttu-id="73456-109">Windows.Devices.Sensors</span><span class="sxs-lookup"><span data-stu-id="73456-109">Windows.Devices.Sensors</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR206408)
-   [**<span data-ttu-id="73456-110">Windows.Devices.Sensors.Custom</span><span class="sxs-lookup"><span data-stu-id="73456-110">Windows.Devices.Sensors.Custom</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn895032)

<span data-ttu-id="73456-111">Sensordaten der Klassen [**Accelerometer**](https://msdn.microsoft.com/library/windows/apps/BR225687), [**Gyrometer**](https://msdn.microsoft.com/library/windows/apps/BR225718), [**Compass**](https://msdn.microsoft.com/library/windows/apps/BR225705), [**Inclinometer**](https://msdn.microsoft.com/library/windows/apps/BR225766) und [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) sind durch ihre Referenzachsen definiert.</span><span class="sxs-lookup"><span data-stu-id="73456-111">Sensor data from the [**Accelerometer**](https://msdn.microsoft.com/library/windows/apps/BR225687), [**Gyrometer**](https://msdn.microsoft.com/library/windows/apps/BR225718), [**Compass**](https://msdn.microsoft.com/library/windows/apps/BR225705), [**Inclinometer**](https://msdn.microsoft.com/library/windows/apps/BR225766), and [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) classes is defined by their reference axes.</span></span> <span data-ttu-id="73456-112">Diese Achsen werden durch den Referenzrahmen des Geräts bestimmt und drehen sich mit dem Gerät, wenn es vom Benutzer gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="73456-112">These axes are defined by the device's reference frame and rotate with the device as the user turns it.</span></span> <span data-ttu-id="73456-113">Falls Ihre App die automatische Drehung unterstützt und sie sich selbst entsprechend der Drehung des Geräts neu ausrichtet, müssen Sie die Sensordaten für die Drehung anpassen, bevor Sie sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="73456-113">If your app supports automatic rotation and reorients itself to accommodate the device as the user rotates it, you must adjust your sensor data for the rotation before using it.</span></span>

## <a name="display-orientation-vs-device-orientation"></a><span data-ttu-id="73456-114">Bildschirmausrichtung und Geräteausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-114">Display orientation vs device orientation</span></span>

<span data-ttu-id="73456-115">Um die Referenzachse für Sensoren begreifen zu können, muss zwischen Bildschirmausrichtung und Geräteausrichtung unterschieden werden.</span><span class="sxs-lookup"><span data-stu-id="73456-115">In order to understand the reference axes for sensors, you need to distinguish display orientation from device orientation.</span></span> <span data-ttu-id="73456-116">Bei der Bildschirmausrichtung handelt es sich um die Richtung, in der Text und Bilder auf dem Bildschirm angezeigt werden, wohingegen es sich bei der Geräteausrichtung um die physische Position des Geräts handelt.</span><span class="sxs-lookup"><span data-stu-id="73456-116">Display orientation is the direction text and images are displayed on the screen whereas device orientation is the physical positioning of the device.</span></span> <span data-ttu-id="73456-117">Im folgenden Bild sind sowohl das Gerät als auch die Anzeige im **Querformat** ausgerichtet. (Beachten Sie, dass die abgebildeten Sensorachsen nur für Geräte gelten, die für das Querformat ausgelegt sind).</span><span class="sxs-lookup"><span data-stu-id="73456-117">In the following picture, both the device and display orientation are in **Landscape** (note that the sensor axes shown are only applicable to landscape-first devices).</span></span>

![Bildschirm- und Geräteausrichtung im Querformat](images/sensor-orientation-a.PNG)

<span data-ttu-id="73456-119">Im folgenden Bild sind sowohl Bildschirm- als auch Geräteausrichtung im **LandscapeFlipped**-Format.</span><span class="sxs-lookup"><span data-stu-id="73456-119">The following picture shows both the display and device orientation in **LandscapeFlipped**.</span></span>

![Bildschirm- und Geräteausrichtung im LandscapeFlipped-Format](images/sensor-orientation-b.PNG)

<span data-ttu-id="73456-121">Das nächste Bild zeigt die Anzeigeausrichtung im Querformat und die Geräteausrichtung im LandscapeFlipped-Format.</span><span class="sxs-lookup"><span data-stu-id="73456-121">The next picture shows the display orientation in Landscape while the device orientation is LandscapeFlipped.</span></span>

![Bildschirmausrichtung im Querformat und Geräteausrichtung im LandscapeFlipped-Format](images/sensor-orientation-c.PNG)

<span data-ttu-id="73456-123">Sie können die Ausrichtungswerte mithilfe der [**DisplayInformation**](https://msdn.microsoft.com/library/windows/apps/Dn264258)-Klasse abfragen, indem Sie die [**GetForCurrentView**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.getforcurrentview.aspx)-Methode mit der [**CurrentOrientation**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.currentorientation.aspx)-Eigenschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="73456-123">You can query the orientation values through the [**DisplayInformation**](https://msdn.microsoft.com/library/windows/apps/Dn264258) class by using the [**GetForCurrentView**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.getforcurrentview.aspx) method with the [**CurrentOrientation**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayinformation.currentorientation.aspx) property.</span></span> <span data-ttu-id="73456-124">Anschließend können Sie durch einen Vergleich mit der [**DisplayOrientations**](https://msdn.microsoft.com/library/windows/apps/BR226142)-Enumeration eine Logik erstellen.</span><span class="sxs-lookup"><span data-stu-id="73456-124">Then you can create logic by comparing against the [**DisplayOrientations**](https://msdn.microsoft.com/library/windows/apps/BR226142) enumeration.</span></span> <span data-ttu-id="73456-125">Bedenken Sie, dass Sie für jede unterstützte Ausrichtung eine Konvertierung der Referenzachsen in die jeweilige Ausrichtung unterstützen müssen.</span><span class="sxs-lookup"><span data-stu-id="73456-125">Remember that for every orientation you support, you have to support a conversion of the reference axes to that orientation.</span></span>

## <a name="landscape-first-vs-portrait-first-devices"></a><span data-ttu-id="73456-126">Für Querformat und für Hochformat ausgelegte Geräte</span><span class="sxs-lookup"><span data-stu-id="73456-126">Landscape-first vs portrait-first devices</span></span>

<span data-ttu-id="73456-127">Hersteller bieten Geräte an, die sowohl für das Quer- als auch das Hochformat ausgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="73456-127">Manufacturers produce both landscape-first and portrait-first devices.</span></span> <span data-ttu-id="73456-128">Der Referenzrahmen weicht zwischen Geräten ab, die für das Querformat (z.B. Desktops und Laptops) und das Hochformat (z.B. Smartphones und einige Tablets) ausgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="73456-128">The reference frame varies between landscape-first devices (like desktops and laptops) and portrait-first devices (like phones and some tablets).</span></span> <span data-ttu-id="73456-129">Die folgende Tabelle enthält die Gerätesensorachsen für Geräte, die jeweils für Hoch- oder Querformat ausgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="73456-129">The following table shows the sensor axes for both landscape-first and portrait-first devices.</span></span>

| <span data-ttu-id="73456-130">Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-130">Orientation</span></span> | <span data-ttu-id="73456-131">Für Querformat ausgelegt</span><span class="sxs-lookup"><span data-stu-id="73456-131">Landscape-first</span></span> | <span data-ttu-id="73456-132">Für Hochformat ausgelegt</span><span class="sxs-lookup"><span data-stu-id="73456-132">Portrait-first</span></span> |
|-------------|-----------------|----------------|
| **<span data-ttu-id="73456-133">Querformat</span><span class="sxs-lookup"><span data-stu-id="73456-133">Landscape</span></span>** | ![Querformatgerät im Querformat](images/sensor-orientation-0.PNG) | ![Hochformatgerät im Querformat](images/sensor-orientation-1.PNG) |
| **<span data-ttu-id="73456-136">Hochformat</span><span class="sxs-lookup"><span data-stu-id="73456-136">Portrait</span></span>** | ![Querformatgerät im Hochformat](images/sensor-orientation-2.PNG) | ![Hochformatgerät im Hochformat](images/sensor-orientation-3.PNG) |
| **<span data-ttu-id="73456-139">LandscapeFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-139">LandscapeFlipped</span></span>** | ![Querformatgerät in LandscapeFlipped-Ausrichtung](images/sensor-orientation-4.PNG) | ![Hochformatgerät in LandscapeFlipped-Ausrichtung](images/sensor-orientation-5.PNG) | 
| **<span data-ttu-id="73456-142">PortraitFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-142">PortraitFlipped</span></span>** | ![Querformatgerät in PortraitFlipped-Ausrichtung](images/sensor-orientation-6.PNG)| ![Hochformatgerät in PortraitFlipped-Ausrichtung](images/sensor-orientation-7.PNG) |

## <a name="devices-broadcasting-display-and-headless-devices"></a><span data-ttu-id="73456-145">Geräte, die die Anzeige übertragen, und monitorlose Geräte</span><span class="sxs-lookup"><span data-stu-id="73456-145">Devices broadcasting display and headless devices</span></span>

<span data-ttu-id="73456-146">Manche Geräte können die Anzeige auf ein anderes Gerät übertragen.</span><span class="sxs-lookup"><span data-stu-id="73456-146">Some devices have the ability to broadcast the display to another device.</span></span> <span data-ttu-id="73456-147">Sie können z.B. ein Tablet verwenden und die Anzeige auf einen Projektor im Querformat übertragen.</span><span class="sxs-lookup"><span data-stu-id="73456-147">For example, you could take a tablet and broadcast the display to a projector that will be in landscape orientation.</span></span> <span data-ttu-id="73456-148">In diesem Szenario müssen Sie bedenken, dass die Geräteausrichtung auf dem ursprünglichen Gerät basiert, und nicht auf dem Gerät, das die Anzeige darstellt.</span><span class="sxs-lookup"><span data-stu-id="73456-148">In this scenario, it is important to keep in mind that the device orientation is based on the original device, not the one presenting the display.</span></span> <span data-ttu-id="73456-149">Ein Beschleunigungsmesser würde daher Daten für das Tablet melden.</span><span class="sxs-lookup"><span data-stu-id="73456-149">So an accelerometer would report data for the tablet.</span></span>

<span data-ttu-id="73456-150">Außerdem verfügen einige Geräte nicht über eine Anzeige.</span><span class="sxs-lookup"><span data-stu-id="73456-150">Furthermore, some devices do not have a display.</span></span> <span data-ttu-id="73456-151">Die Standardausrichtung für diese Geräte ist das Hochformat.</span><span class="sxs-lookup"><span data-stu-id="73456-151">With these devices, the default orientation for these devices is portrait.</span></span>

## <a name="display-orientation-and-compass-heading"></a><span data-ttu-id="73456-152">Bildschirmausrichtung und Kompassrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-152">Display orientation and compass heading</span></span>


<span data-ttu-id="73456-153">Die Kompassrichtung hängt von den Referenzachsen ab und ändert sich daher mit der Geräteausrichtung.</span><span class="sxs-lookup"><span data-stu-id="73456-153">Compass heading depends upon the reference axes and so it changes with the device orientation.</span></span> <span data-ttu-id="73456-154">Sie kompensieren dies entsprechend den Angaben in der folgenden Tabelle (unter der Annahme, dass der Benutzer nach Norden ausgerichtet ist).</span><span class="sxs-lookup"><span data-stu-id="73456-154">You compensate based on the this table (assume the user is facing north).</span></span>

| <span data-ttu-id="73456-155">Bildschirmausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-155">Display orientation</span></span> | <span data-ttu-id="73456-156">Referenzachse für Kompassrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-156">Reference axis for compass heading</span></span> | <span data-ttu-id="73456-157">API-Kompassrichtung bei Ausrichtung nach Norden</span><span class="sxs-lookup"><span data-stu-id="73456-157">API compass heading when facing north</span></span> | <span data-ttu-id="73456-158">Kompensation der Kompassrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-158">Compass heading compensation</span></span> | 
|---------------------|------------------------------------|---------------------------------------|------------------------------|
| <span data-ttu-id="73456-159">Querformat</span><span class="sxs-lookup"><span data-stu-id="73456-159">Landscape</span></span>           | <span data-ttu-id="73456-160">-Z</span><span class="sxs-lookup"><span data-stu-id="73456-160">-Z</span></span> | <span data-ttu-id="73456-161">0</span><span class="sxs-lookup"><span data-stu-id="73456-161">0</span></span>   | <span data-ttu-id="73456-162">Richtung</span><span class="sxs-lookup"><span data-stu-id="73456-162">Heading</span></span>               |
| <span data-ttu-id="73456-163">Hochformat</span><span class="sxs-lookup"><span data-stu-id="73456-163">Portrait</span></span>            |  <span data-ttu-id="73456-164">Y</span><span class="sxs-lookup"><span data-stu-id="73456-164">Y</span></span> | <span data-ttu-id="73456-165">90</span><span class="sxs-lookup"><span data-stu-id="73456-165">90</span></span>  | <span data-ttu-id="73456-166">(Richtung + 270) % 360</span><span class="sxs-lookup"><span data-stu-id="73456-166">(Heading + 270) % 360</span></span> | 
| <span data-ttu-id="73456-167">LandscapeFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-167">LandscapeFlipped</span></span>    |  <span data-ttu-id="73456-168">Z</span><span class="sxs-lookup"><span data-stu-id="73456-168">Z</span></span> | <span data-ttu-id="73456-169">180</span><span class="sxs-lookup"><span data-stu-id="73456-169">180</span></span> | <span data-ttu-id="73456-170">(Richtung + 180) % 360</span><span class="sxs-lookup"><span data-stu-id="73456-170">(Heading + 180) % 360</span></span> |
| <span data-ttu-id="73456-171">PortraitFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-171">PortraitFlipped</span></span>     |  <span data-ttu-id="73456-172">Y</span><span class="sxs-lookup"><span data-stu-id="73456-172">Y</span></span> | <span data-ttu-id="73456-173">270</span><span class="sxs-lookup"><span data-stu-id="73456-173">270</span></span> | <span data-ttu-id="73456-174">(Richtung + 90) % 360</span><span class="sxs-lookup"><span data-stu-id="73456-174">(Heading + 90) % 360</span></span>  |

<span data-ttu-id="73456-175">Ändern Sie die Kompassrichtung entsprechend den Angaben in der Tabelle, um die Richtung korrekt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="73456-175">Modify the compass heading as shown in the table in order to correctly display the heading.</span></span> <span data-ttu-id="73456-176">Der folgende Codeausschnitt veranschaulicht die Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="73456-176">The following code snippet demonstrates how to do this.</span></span>

```csharp
private void ReadingChanged(object sender, CompassReadingChangedEventArgs e)
{
    double heading = e.Reading.HeadingMagneticNorth;        
    double displayOffset;
    
    // Calculate the compass heading offset based on
    // the current display orientation.
    DisplayInformation displayInfo = DisplayInformation.GetForCurrentView();
    
    switch (displayInfo.CurrentOrientation) 
    { 
        case DisplayOrientations.Landscape: 
            displayOffset = 0; 
            break;
        case DisplayOrientations.Portrait: 
            displayOffset = 270; 
            break; 
        case DisplayOrientations.LandscapeFlipped: 
            displayOffset = 180; 
            break; 
        case DisplayOrientations.PortraitFlipped: 
            displayOffset = 90; 
            break; 
     } 
    

    double displayCompensatedHeading = (heading + displayOffset) % 360;
    
    // Update the UI...
}
```

## <a name="display-orientation-with-the-accelerometer-and-gyrometer"></a><span data-ttu-id="73456-177">Bildschirmausrichtung mit Beschleunigungsmesser und Gyrometer</span><span class="sxs-lookup"><span data-stu-id="73456-177">Display orientation with the accelerometer and gyrometer</span></span>

<span data-ttu-id="73456-178">Die folgende Tabelle zeigt, wie Beschleunigungsmesser- und Gyrometerdaten für die Bildschirmausrichtung konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="73456-178">This table converts accelerometer and gyrometer data for display orientation.</span></span>

| <span data-ttu-id="73456-179">Referenzachsen</span><span class="sxs-lookup"><span data-stu-id="73456-179">Reference axes</span></span>        |  <span data-ttu-id="73456-180">X</span><span class="sxs-lookup"><span data-stu-id="73456-180">X</span></span> |  <span data-ttu-id="73456-181">Y</span><span class="sxs-lookup"><span data-stu-id="73456-181">Y</span></span> | <span data-ttu-id="73456-182">Z</span><span class="sxs-lookup"><span data-stu-id="73456-182">Z</span></span> |
|-----------------------|----|----|---|
| **<span data-ttu-id="73456-183">Querformat</span><span class="sxs-lookup"><span data-stu-id="73456-183">Landscape</span></span>**         |  <span data-ttu-id="73456-184">X</span><span class="sxs-lookup"><span data-stu-id="73456-184">X</span></span> |  <span data-ttu-id="73456-185">Y</span><span class="sxs-lookup"><span data-stu-id="73456-185">Y</span></span> | <span data-ttu-id="73456-186">Z</span><span class="sxs-lookup"><span data-stu-id="73456-186">Z</span></span> |
| **<span data-ttu-id="73456-187">Hochformat</span><span class="sxs-lookup"><span data-stu-id="73456-187">Portrait</span></span>**          |  <span data-ttu-id="73456-188">Y</span><span class="sxs-lookup"><span data-stu-id="73456-188">Y</span></span> | <span data-ttu-id="73456-189">-X</span><span class="sxs-lookup"><span data-stu-id="73456-189">-X</span></span> | <span data-ttu-id="73456-190">Z</span><span class="sxs-lookup"><span data-stu-id="73456-190">Z</span></span> |
| **<span data-ttu-id="73456-191">LandscapeFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-191">LandscapeFlipped</span></span>**  | <span data-ttu-id="73456-192">-X</span><span class="sxs-lookup"><span data-stu-id="73456-192">-X</span></span> | <span data-ttu-id="73456-193">-Y</span><span class="sxs-lookup"><span data-stu-id="73456-193">-Y</span></span> | <span data-ttu-id="73456-194">Z</span><span class="sxs-lookup"><span data-stu-id="73456-194">Z</span></span> |
| **<span data-ttu-id="73456-195">PortraitFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-195">PortraitFlipped</span></span>**   | <span data-ttu-id="73456-196">-Y</span><span class="sxs-lookup"><span data-stu-id="73456-196">-Y</span></span> |  <span data-ttu-id="73456-197">X</span><span class="sxs-lookup"><span data-stu-id="73456-197">X</span></span> | <span data-ttu-id="73456-198">Z</span><span class="sxs-lookup"><span data-stu-id="73456-198">Z</span></span> |

<span data-ttu-id="73456-199">Das folgende Codebeispiel wendet diese Konvertierungen auf das Gyrometer an.</span><span class="sxs-lookup"><span data-stu-id="73456-199">The following code example applies these conversions to the gyrometer.</span></span>

```csharp
private void ReadingChanged(object sender, GyrometerReadingChangedEventArgs e)
{
    double x_Axis;
    double y_Axis;
    double z_Axis;

    GyrometerReading reading = e.Reading;  
    
    // Calculate the gyrometer axes based on
    // the current display orientation.
    DisplayInformation displayInfo = DisplayInformation.GetForCurrentView();
    switch (displayInfo.CurrentOrientation) 
    { 
        case DisplayOrientations.Landscape: 
            x_Axis = reading.AngularVelocityX;
            y_Axis = reading.AngularVelocityY;
            z_Axis = reading.AngularVelocityZ;
            break;
        case DisplayOrientations.Portrait: 
            x_Axis = reading.AngularVelocityY;
            y_Axis = -1 * reading.AngularVelocityX;
            z_Axis = reading.AngularVelocityZ;
            break; 
        case DisplayOrientations.LandscapeFlipped: 
            x_Axis = -1 * reading.AngularVelocityX;
            y_Axis = -1 * reading.AngularVelocityY;
            z_Axis = reading.AngularVelocityZ;
            break; 
        case DisplayOrientations.PortraitFlipped: 
            x_Axis = -1 * reading.AngularVelocityY;
            y_Axis = reading.AngularVelocityX;
            z_Axis = reading.AngularVelocityZ;
            break; 
     } 
    
    
    // Update the UI...
}
```

## <a name="display-orientation-and-device-orientation"></a><span data-ttu-id="73456-200">Bildschirmausrichtung und Geräteausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-200">Display orientation and device orientation</span></span>

<span data-ttu-id="73456-201">Die [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371)-Daten müssen auf andere Weise geändert werden.</span><span class="sxs-lookup"><span data-stu-id="73456-201">The [**OrientationSensor**](https://msdn.microsoft.com/library/windows/apps/BR206371) data must be changed in a different way.</span></span> <span data-ttu-id="73456-202">Stellen Sie sich diese unterschiedlichen Ausrichtungen als Drehungen um die Z-Achse entgegen dem Uhrzeigersinn vor. Folglich müssen wir die Drehung umkehren, um wieder die Ausrichtung des Benutzers zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="73456-202">Think of these different orientations as rotations counterclockwise to the Z axis, so we need to reverse the rotation to get back the user’s orientation.</span></span> <span data-ttu-id="73456-203">Für Quaterniondaten können wir anhand der eulerschen Formel eine Drehung mit einer Referenzquaternion definieren, und außerdem können wir eine Referenzdrehungsmatrix verwenden.</span><span class="sxs-lookup"><span data-stu-id="73456-203">For quaternion data, we can use Euler’s formula to define a rotation with a reference quaternion, and we can also use a reference rotation matrix.</span></span>

![Eulersche Formel](images/eulers-formula.png)

<span data-ttu-id="73456-205">Um die gewünschte relative Ausrichtung zu erhalten, multiplizieren Sie das Referenzobjekt mit dem absoluten Objekt.</span><span class="sxs-lookup"><span data-stu-id="73456-205">To get the relative orientation you want, multiply the reference object against the absolute object.</span></span> <span data-ttu-id="73456-206">Beachten Sie, dass diese Berechnung nicht kommutativ ist.</span><span class="sxs-lookup"><span data-stu-id="73456-206">Note that this math is not commutative.</span></span>

![Multiplizieren des Referenzobjekts mit dem absoluten Objekt](images/orientation-formula.png)

<span data-ttu-id="73456-208">Im vorangehenden Ausdruck wird das absolute Objekt von den Sensordaten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="73456-208">In the preceding expression, the absolute object is returned by the sensor data.</span></span>


| <span data-ttu-id="73456-209">Bildschirmausrichtung</span><span class="sxs-lookup"><span data-stu-id="73456-209">Display orientation</span></span>  | <span data-ttu-id="73456-210">Drehung gegen den Uhrzeigersinn um Z</span><span class="sxs-lookup"><span data-stu-id="73456-210">Counterclockwise rotation around Z</span></span> | <span data-ttu-id="73456-211">Referenzquaternion (Drehung in umgekehrter Richtung)</span><span class="sxs-lookup"><span data-stu-id="73456-211">Reference quaternion (reverse rotation)</span></span> | <span data-ttu-id="73456-212">Referenzdrehungsmatrix (Drehung in umgekehrter Richtung)</span><span class="sxs-lookup"><span data-stu-id="73456-212">Reference rotation matrix (reverse rotation)</span></span> | 
|----------------------|------------------------------------|-----------------------------------------|----------------------------------------------|
| **<span data-ttu-id="73456-213">Querformat</span><span class="sxs-lookup"><span data-stu-id="73456-213">Landscape</span></span>**        | <span data-ttu-id="73456-214">0</span><span class="sxs-lookup"><span data-stu-id="73456-214">0</span></span>                                  | <span data-ttu-id="73456-215">1 + 0i + 0j + 0k</span><span class="sxs-lookup"><span data-stu-id="73456-215">1 + 0i + 0j + 0k</span></span>                        | <span data-ttu-id="73456-216">\[1 0 0</span><span class="sxs-lookup"><span data-stu-id="73456-216">\[1 0 0</span></span><br/> <span data-ttu-id="73456-217">0 1 0</span><span class="sxs-lookup"><span data-stu-id="73456-217">0 1 0</span></span><br/> <span data-ttu-id="73456-218">0 0 1\]</span><span class="sxs-lookup"><span data-stu-id="73456-218">0 0 1\]</span></span>               |
| **<span data-ttu-id="73456-219">Hochformat</span><span class="sxs-lookup"><span data-stu-id="73456-219">Portrait</span></span>**         | <span data-ttu-id="73456-220">90</span><span class="sxs-lookup"><span data-stu-id="73456-220">90</span></span>                                 | <span data-ttu-id="73456-221">cos(-45⁰) + (i + j + k)*sin(-45⁰)</span><span class="sxs-lookup"><span data-stu-id="73456-221">cos(-45⁰) + (i + j + k)*sin(-45⁰)</span></span>       | <span data-ttu-id="73456-222">\[0 1 0</span><span class="sxs-lookup"><span data-stu-id="73456-222">\[0 1 0</span></span><br/><span data-ttu-id="73456-223">-1 0 0</span><span class="sxs-lookup"><span data-stu-id="73456-223">-1 0 0</span></span><br/><span data-ttu-id="73456-224">0 0 1]</span><span class="sxs-lookup"><span data-stu-id="73456-224">0 0 1]</span></span>              |
| **<span data-ttu-id="73456-225">LandscapeFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-225">LandscapeFlipped</span></span>** | <span data-ttu-id="73456-226">180</span><span class="sxs-lookup"><span data-stu-id="73456-226">180</span></span>                                | <span data-ttu-id="73456-227">0 - i - j - k</span><span class="sxs-lookup"><span data-stu-id="73456-227">0 - i - j - k</span></span>                           | <span data-ttu-id="73456-228">\[1 0 0</span><span class="sxs-lookup"><span data-stu-id="73456-228">\[1 0 0</span></span><br/> <span data-ttu-id="73456-229">0 1 0</span><span class="sxs-lookup"><span data-stu-id="73456-229">0 1 0</span></span><br/> <span data-ttu-id="73456-230">0 0 1]</span><span class="sxs-lookup"><span data-stu-id="73456-230">0 0 1]</span></span>               |
| **<span data-ttu-id="73456-231">PortraitFlipped</span><span class="sxs-lookup"><span data-stu-id="73456-231">PortraitFlipped</span></span>**  | <span data-ttu-id="73456-232">270</span><span class="sxs-lookup"><span data-stu-id="73456-232">270</span></span>                                | <span data-ttu-id="73456-233">cos(-135⁰) + (i + j + k)*sin(-135⁰)</span><span class="sxs-lookup"><span data-stu-id="73456-233">cos(-135⁰) + (i + j + k)*sin(-135⁰)</span></span>     | <span data-ttu-id="73456-234">\[0 -1 0</span><span class="sxs-lookup"><span data-stu-id="73456-234">\[0 -1 0</span></span><br/> <span data-ttu-id="73456-235">1 0 0</span><span class="sxs-lookup"><span data-stu-id="73456-235">1  0 0</span></span><br/> <span data-ttu-id="73456-236">0 0 1]</span><span class="sxs-lookup"><span data-stu-id="73456-236">0  0 1]</span></span>             |

