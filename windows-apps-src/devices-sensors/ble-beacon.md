---
title: Bluetooth-Werbung
description: Dieser Abschnitt enthält Artikel zur Integration von Bluetooth Low Energy (LE)-Ankündigungen in Apps für die Universelle Windows-Plattform (UWP) mithilfe der AdvertisementWatcher- and AdvertisementPublisher-APIs.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: ff10bbc0-03a7-492c-b5fe-c5b9ce8ca32e
ms.localizationpriority: medium
ms.openlocfilehash: e9eafde0596ad3156f52a7a2f0a1566444a9836a
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7708480"
---
# <a name="bluetooth-le-advertisements"></a><span data-ttu-id="7d610-104">Bluetooth LE-Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="7d610-104">Bluetooth LE Advertisements</span></span>


**<span data-ttu-id="7d610-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="7d610-105">Important APIs</span></span>**

-   [**<span data-ttu-id="7d610-106">Windows.Devices.Bluetooth.Advertisement</span><span class="sxs-lookup"><span data-stu-id="7d610-106">Windows.Devices.Bluetooth.Advertisement</span></span>**](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.advertisement.aspx)

<span data-ttu-id="7d610-107">Dieser Artikel enthält eine Übersicht über Bluetooth Low Energy (LE)-Ankündigungsbeacons für Apps für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="7d610-107">This article provides an overview of Bluetooth Low Energy (LE) Advertisement beacons for Universal Windows Platform (UWP) apps.</span></span>  

## <a name="overview"></a><span data-ttu-id="7d610-108">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7d610-108">Overview</span></span>

<span data-ttu-id="7d610-109">Es gibt zwei Hauptfunktionen, die ein Entwickler mithilfe der LE-Ankündigungs-APIs ausführen kann:</span><span class="sxs-lookup"><span data-stu-id="7d610-109">There are two main functions that a developer can perform using the LE Advertisement APIs:</span></span>

-   <span data-ttu-id="7d610-110">[Ankündigungsüberwachung](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.aspx): Überwachung auf Beacons in der Nähe und deren Filterung auf der Basis von Nutzlast oder Nähe.</span><span class="sxs-lookup"><span data-stu-id="7d610-110">[Advertisement Watcher](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.aspx): listen for nearby beacons and filter them out based on payload or proximity.</span></span>  
-   <span data-ttu-id="7d610-111">[Ankündigung Publisher](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher.aspx): eine Nutzlast für Windows definieren, um im Auftrag eines Entwicklers zu werben.</span><span class="sxs-lookup"><span data-stu-id="7d610-111">[Advertisement Publisher](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher.aspx): define a payload for Windows to advertise on a developers behalf.</span></span>  

<span data-ttu-id="7d610-112">Ein vollständiges Codebeispiel finden Sie unter [Beispiel für Bluetooth-Ankündigungen](http://go.microsoft.com/fwlink/p/?LinkId=619990) auf Github.</span><span class="sxs-lookup"><span data-stu-id="7d610-112">Full sample code is found in the [Bluetooth Advertisement Sample](http://go.microsoft.com/fwlink/p/?LinkId=619990) on Github</span></span>

## <a name="basic-setup"></a><span data-ttu-id="7d610-113">Grundlegende Einrichtung</span><span class="sxs-lookup"><span data-stu-id="7d610-113">Basic Setup</span></span>

<span data-ttu-id="7d610-114">Um Bluetooth LE-Grundfunktionalität in einer App für die Universelle Windows-Plattform zu verwenden, müssen Sie die Bluetooth-Funktion in „Package.appxmanifest“ aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7d610-114">To use basic Bluetooth LE functionality in a Universal Windows Platform app, you must check the Bluetooth capability in the Package.appxmanifest.</span></span>

1. <span data-ttu-id="7d610-115">Öffnen Sie „Package.appxmanifest“.</span><span class="sxs-lookup"><span data-stu-id="7d610-115">Open Package.appxmanifest</span></span>
2. <span data-ttu-id="7d610-116">Navigieren Sie zur Registerkarte „Funktionen“.</span><span class="sxs-lookup"><span data-stu-id="7d610-116">Go to the Capabilities tab</span></span>
3. <span data-ttu-id="7d610-117">Suchen Sie Bluetooth in der Liste auf der linken Seite, und aktivieren Sie das Kontrollkästchen daneben.</span><span class="sxs-lookup"><span data-stu-id="7d610-117">Find Bluetooth in the list on the left and check the box next to it.</span></span>

## <a name="publishing-advertisements"></a><span data-ttu-id="7d610-118">Veröffentlichen von Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="7d610-118">Publishing Advertisements</span></span>

<span data-ttu-id="7d610-119">Bluetooth LE-Ankündigungen ermöglichen Ihrem Gerät, konstant eine spezifische Nutzlast („Ankündigung“ genannt) zu signalisieren.</span><span class="sxs-lookup"><span data-stu-id="7d610-119">Bluetooth LE Advertisements allow your device to constantly beacon out a specific payload, called an advertisement.</span></span> <span data-ttu-id="7d610-120">Diese Ankündigung kann von jedem Bluetooth LE-kompatiblen Gerät in der Nähe erkannt werden, wenn es für den Empfang dieser spezifischen Ankündigung eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="7d610-120">This advertisement can be seen by any nearby Bluetooth LE capable device, if they are set up to listen for this specific advertisment.</span></span>

> <span data-ttu-id="7d610-121">**Hinweis**: für Datenschutz für Benutzer, die Lebensdauer von der Ankündigung an diejenige Ihrer App gebunden.</span><span class="sxs-lookup"><span data-stu-id="7d610-121">**Note**: For user privacy, the lifespan of your advertisement is tied to that of your app.</span></span> <span data-ttu-id="7d610-122">Sie können einen BluetoothLEAdvertisementPublisher erstellen und in einer Hintergrundaufgabe „Start“ aufrufen, um die Ankündigung im Hintergrund auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7d610-122">You can create a BluetoothLEAdvertisementPublisher and call Start in a background task for advertisement in the background.</span></span> <span data-ttu-id="7d610-123">Weitere Informationen zu Hintergrundaufgaben finden Sie unter [Starten, Fortsetzen und Hintergrundaufgaben](https://msdn.microsoft.com/windows/uwp/launch-resume/index).</span><span class="sxs-lookup"><span data-stu-id="7d610-123">For more information about background tasks, see [Launching, resuming, and background tasks](https://msdn.microsoft.com/windows/uwp/launch-resume/index).</span></span>

### <a name="basic-publishing"></a><span data-ttu-id="7d610-124">Grundlegende Veröffentlichung</span><span class="sxs-lookup"><span data-stu-id="7d610-124">Basic Publishing</span></span>

<span data-ttu-id="7d610-125">Es gibt viele verschiedene Arten, einer Ankündigung Daten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7d610-125">There are many different ways to add data to an Advertisement.</span></span> <span data-ttu-id="7d610-126">Dieses Beispiel zeigt ein häufig angewendetes Verfahren zum Erstellen einer unternehmensspezifischen Ankündigung.</span><span class="sxs-lookup"><span data-stu-id="7d610-126">This example shows a common way to create a company-specific advertisement.</span></span> 

<span data-ttu-id="7d610-127">Erstellen Sie zunächst den Ankündigungsherausgeber, der steuert, ob das Gerät eine spezifische Ankündigung signalisiert oder nicht.</span><span class="sxs-lookup"><span data-stu-id="7d610-127">First, create the advertisement publisher that controls whether or not the device is beaconing out a specific advertisement.</span></span>

```csharp
BluetoothLEAdvertisementPublisher publisher = new BluetoothLEAdvertisementPublisher();
```

<span data-ttu-id="7d610-128">Erstellen Sie anschließend einen benutzerdefinierten Datenabschnitt.</span><span class="sxs-lookup"><span data-stu-id="7d610-128">Second, create a custom data section.</span></span> <span data-ttu-id="7d610-129">In diesem Beispiel wird ein nicht zugewiesener **CompanyId**-Wert *0xFFFE* verwendet und der Ankündigung der Text *Hello World* hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7d610-129">This example uses an unassigned **CompanyId** value *0xFFFE* and adds the text *Hello World* to the advertisement.</span></span> 

```csharp
// Add custom data to the advertisement
var manufacturerData = new BluetoothLEManufacturerData();
manufacturerData.CompanyId = 0xFFFE;

var writer = new DataWriter();
writer.WriteString("Hello World");

// Make sure that the buffer length can fit within an advertisement payload (~20 bytes). 
// Otherwise you will get an exception.
manufacturerData.Data = writer.DetachBuffer();

// Add the manufacturer data to the advertisement publisher:
publisher.Advertisement.ManufacturerData.Add(manufacturerData);
```

<span data-ttu-id="7d610-130">Da der Herausgeber nun erstellt und eingerichtet wurde, können Sie **Start** aufrufen, um die Ankündigung zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="7d610-130">Now that the publisher has been created and setup, you can call **Start** to begin advertising.</span></span>

```csharp
publisher.Start();
```

## <a name="watching-for-advertisements"></a><span data-ttu-id="7d610-131">Überwachen auf Ankündigungen</span><span class="sxs-lookup"><span data-stu-id="7d610-131">Watching for Advertisements</span></span>

### <a name="basic-watching"></a><span data-ttu-id="7d610-132">Grundlegende Überwachung</span><span class="sxs-lookup"><span data-stu-id="7d610-132">Basic Watching</span></span>

<span data-ttu-id="7d610-133">Der folgende Code zeigt, wie Sie eine Bluetooth LE-Ankündigungsüberwachung erstellen, einen Rückruf einrichten und mit der Überwachung auf alle LE-Ankündigungen beginnen.</span><span class="sxs-lookup"><span data-stu-id="7d610-133">The following code demonstrates how to create a Bluetooth LE Advertisement watcher, set a callback, and start watching for all LE advertisements.</span></span>

```csharp
BluetoothLEAdvertisementWatcher watcher = new BluetoothLEAdvertisementWatcher();
watcher.Received += OnAdvertisementReceived;
watcher.Start();
``` 

```csharp
private async void OnAdvertisementReceived(BluetoothLEAdvertisementWatcher watcher, BluetoothLEAdvertisementReceivedEventArgs eventArgs)
{
    // Do whatever you want with the advertisement
}
```

#### <a name="active-scanning"></a><span data-ttu-id="7d610-134">Aktives Scannen</span><span class="sxs-lookup"><span data-stu-id="7d610-134">Active Scanning</span></span>
<span data-ttu-id="7d610-135">Um Scanantwortankündigungen ebenfalls zu erhalten, legen Sie nach dem Erstellen der Überwachung Folgendes fest.</span><span class="sxs-lookup"><span data-stu-id="7d610-135">To receive scan response advertisements as well, set the following after creating the watcher.</span></span> <span data-ttu-id="7d610-136">Beachten Sie, dass dies mehr Energie verbraucht und in Hintergrundmodi nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7d610-136">Note that this will cause greater power drain and is not available while in background modes.</span></span>

```csharp
watcher.ScanningMode = BluetoothLEScanningMode.Active;
```

### <a name="watching-for-a-specific-advertisement-pattern"></a><span data-ttu-id="7d610-137">Überwachung auf ein spezifisches Ankündigungsmuster</span><span class="sxs-lookup"><span data-stu-id="7d610-137">Watching for a Specific Advertisement Pattern</span></span>

<span data-ttu-id="7d610-138">Manchmal möchten Sie eine spezifische Ankündigung erhalten.</span><span class="sxs-lookup"><span data-stu-id="7d610-138">Sometimes you want to listen for a specific advertisement.</span></span> <span data-ttu-id="7d610-139">In diesem Fall überwachen Sie auf eine Ankündigung, die eine Nutzlast mit einem angenommenen Unternehmen (als 0xFFFE identifiziert) und die Zeichenfolge *Hello World* in der Ankündigung enthält.</span><span class="sxs-lookup"><span data-stu-id="7d610-139">In this case, listen for an advertisement containing a payload with a made up company (identified as 0xFFFE) and containing the string *Hello World* in the advertisement.</span></span> <span data-ttu-id="7d610-140">Dies kann mit dem Beispiel für die grundlegende Veröffentlichung kombiniert werden, sodass ein Windows-Computer die Ankündigung sendet und ein anderer auf diese Ankündigung überwacht.</span><span class="sxs-lookup"><span data-stu-id="7d610-140">This can be paired with the Basic Publishing example to have one Windows machine advertising and another watching.</span></span> <span data-ttu-id="7d610-141">Achten Sie darauf, diesen Ankündigungsfilter festzulegen, bevor Sie die Überwachung starten.</span><span class="sxs-lookup"><span data-stu-id="7d610-141">Be sure to set this advertisement filter before you start the watcher!</span></span>

```csharp
var manufacturerData = new BluetoothLEManufacturerData();
manufacturerData.CompanyId = 0xFFFE;

// Make sure that the buffer length can fit within an advertisement payload (~20 bytes). 
// Otherwise you will get an exception.
var writer = new DataWriter();
writer.WriteString("Hello World");
manufacturerData.Data = writer.DetachBuffer();

watcher.AdvertisementFilter.Advertisement.ManufacturerData.Add(manufacturerData);
```

### <a name="watching-for-a-nearby-advertisement"></a><span data-ttu-id="7d610-142">Überwachung auf eine Ankündigung in der Nähe</span><span class="sxs-lookup"><span data-stu-id="7d610-142">Watching for a Nearby Advertisement</span></span>

<span data-ttu-id="7d610-143">Manchmal möchten Sie die Überwachung nur auslösen, wenn das Gerät, das die Ankündigung sendet, in Reichweite ist.</span><span class="sxs-lookup"><span data-stu-id="7d610-143">Sometimes you only want to trigger your watcher when the device advertising has come in range.</span></span> <span data-ttu-id="7d610-144">Sie können einen eigenen Bereich definieren. Sie müssen lediglich beachten, dass die Werte auf zwischen 0 und -128 gekürzt werden.</span><span class="sxs-lookup"><span data-stu-id="7d610-144">You can define your own range, just note that values will be clipped to between 0 and -128.</span></span> 

```csharp
// Set the in-range threshold to -70dBm. This means advertisements with RSSI >= -70dBm 
// will start to be considered "in-range" (callbacks will start in this range).
watcher.SignalStrengthFilter.InRangeThresholdInDBm = -70;

// Set the out-of-range threshold to -75dBm (give some buffer). Used in conjunction 
// with OutOfRangeTimeout to determine when an advertisement is no longer 
// considered "in-range".
watcher.SignalStrengthFilter.OutOfRangeThresholdInDBm = -75;

// Set the out-of-range timeout to be 2 seconds. Used in conjunction with 
// OutOfRangeThresholdInDBm to determine when an advertisement is no longer 
// considered "in-range"
watcher.SignalStrengthFilter.OutOfRangeTimeout = TimeSpan.FromMilliseconds(2000);
```

### <a name="gauging-distance"></a><span data-ttu-id="7d610-145">Messen der Entfernung</span><span class="sxs-lookup"><span data-stu-id="7d610-145">Gauging Distance</span></span>

<span data-ttu-id="7d610-146">Wenn der Rückruf Ihrer Bluetooth LE-Überwachung ausgelöst wird, enthalten die „EventArgs“ einen RSSI-Wert, der Sie über die Stärke des empfangenen Signals informiert (d.h., wie stark das Bluetooth-Signal ist).</span><span class="sxs-lookup"><span data-stu-id="7d610-146">When your Bluetooth LE Watcher's callback is triggered, the eventArgs include an RSSI value telling you the received signal strength (how strong the Bluetooth signal is).</span></span>

```csharp
private async void OnAdvertisementReceived(BluetoothLEAdvertisementWatcher watcher, BluetoothLEAdvertisementReceivedEventArgs eventArgs)
{
    // The received signal strength indicator (RSSI)
    Int16 rssi = eventArgs.RawSignalStrengthInDBm;
}
```

<span data-ttu-id="7d610-147">Dieses kann zwar in eine ungefähre Entfernung übersetzt werden, sollte jedoch nicht zum Messen der echten Entfernung verwendet werden, da jeder Sender unterschiedlich ist.</span><span class="sxs-lookup"><span data-stu-id="7d610-147">This can be roughly translated into distance, but should not be used to measure true distances as each individual radio is different.</span></span> <span data-ttu-id="7d610-148">Unterschiedliche Umweltbedingungen können das Messen der Entfernung erschweren (wie Wände, Sendergehäuse oder sogar die Luftfeuchtigkeit).</span><span class="sxs-lookup"><span data-stu-id="7d610-148">Different environmental factors can make distance difficult to gauge (such as walls, cases around the radio, or even air humidity).</span></span>

<span data-ttu-id="7d610-149">Eine Alternative zur Beurteilung der reinen Entfernung besteht im Definieren von „Buckets“.</span><span class="sxs-lookup"><span data-stu-id="7d610-149">An alternative to judging pure distance is to define "buckets".</span></span> <span data-ttu-id="7d610-150">Sender tendieren dazu, 0–50dBm zu melden, wenn sie sehr nahe sind,-50–-90dBm, wenn sie sich in einem mittleren Abstand befinden, und weniger als -90dBm, wenn sie weit entfernt sind.</span><span class="sxs-lookup"><span data-stu-id="7d610-150">Radios tend to report 0 to -50 DBm when they are very close, -50 to -90 when they are a medium distance away, and below -90 when they are far away.</span></span> <span data-ttu-id="7d610-151">Tests sind die beste Möglichkeit, diese Buckets für Ihre App festzulegen.</span><span class="sxs-lookup"><span data-stu-id="7d610-151">Trial and error is best to determine what you want these buckets to be for your app.</span></span>