---
author: msatranjr
title: Bluetooth GATT-Client
description: Dieser Artikel enthält eine Übersicht über Bluetooth Generic Attribute Profile (GATT)-Client für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine Anwendungsfälle.
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 345e6f82ddf97c2595dad0029ca432f075a6190b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5555960"
---
# <a name="bluetooth-gatt-client"></a><span data-ttu-id="5f600-104">Bluetooth GATT-Client</span><span class="sxs-lookup"><span data-stu-id="5f600-104">Bluetooth GATT Client</span></span>


**<span data-ttu-id="5f600-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5f600-105">Important APIs</span></span>**

-   [**<span data-ttu-id="5f600-106">Windows.Devices.Bluetooth</span><span class="sxs-lookup"><span data-stu-id="5f600-106">Windows.Devices.Bluetooth</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
-   [**<span data-ttu-id="5f600-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span><span class="sxs-lookup"><span data-stu-id="5f600-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn297685)

<span data-ttu-id="5f600-108">Dieser Artikel veranschaulicht die Verwendung der Bluetooth-Generic Attribut (GATT)-Client-APIs für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine GATT-Client-Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="5f600-108">This article demonstrates usage of the Bluetooth Generic Attribute (GATT) Client APIs for Universal Windows Platform (UWP) apps, along with sample code for common GATT client tasks:</span></span>
- <span data-ttu-id="5f600-109">Abfrage von Geräten in der Nähe</span><span class="sxs-lookup"><span data-stu-id="5f600-109">Query for nearby devices</span></span>
- <span data-ttu-id="5f600-110">Verbinden mit Gerät</span><span class="sxs-lookup"><span data-stu-id="5f600-110">Connect to device</span></span>
- <span data-ttu-id="5f600-111">Auflisten der unterstützten Dienste und-Merkmale des Geräts</span><span class="sxs-lookup"><span data-stu-id="5f600-111">Enumerate the supported services and characteristics of the device</span></span>
- <span data-ttu-id="5f600-112">Lesen und Schreiben von einem Merkmal</span><span class="sxs-lookup"><span data-stu-id="5f600-112">Read and write to a characteristic</span></span>
- <span data-ttu-id="5f600-113">Abonnieren Sie für Benachrichtigungen bei charakteristische ändert Wert</span><span class="sxs-lookup"><span data-stu-id="5f600-113">Subscribe for notifications when characteristic value changes</span></span>

## <a name="overview"></a><span data-ttu-id="5f600-114">Übersicht</span><span class="sxs-lookup"><span data-stu-id="5f600-114">Overview</span></span>
<span data-ttu-id="5f600-115">Entwickler können die APIs im [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685) -Namespace verwenden, den Zugriff auf Bluetooth LE-Geräte.</span><span class="sxs-lookup"><span data-stu-id="5f600-115">Developers can use the APIs in the [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685) namespace to access Bluetooth LE devices.</span></span> <span data-ttu-id="5f600-116">Bluetooth LE-Geräte machen ihre Funktionen über eine Sammlung folgender Elemente verfügbar:</span><span class="sxs-lookup"><span data-stu-id="5f600-116">Bluetooth LE devices expose their functionality through a collection of:</span></span>

-   <span data-ttu-id="5f600-117">Dienste</span><span class="sxs-lookup"><span data-stu-id="5f600-117">Services</span></span>
-   <span data-ttu-id="5f600-118">Merkmale</span><span class="sxs-lookup"><span data-stu-id="5f600-118">Characteristics</span></span>
-   <span data-ttu-id="5f600-119">Deskriptoren</span><span class="sxs-lookup"><span data-stu-id="5f600-119">Descriptors</span></span>

<span data-ttu-id="5f600-120">Dienste definieren den funktionsvertrag des LE-Geräts und enthalten eine Sammlung der Merkmale, die den Dienst definieren.</span><span class="sxs-lookup"><span data-stu-id="5f600-120">Services define the functional contract of the LE device and contain a collection of characteristics that define the service.</span></span> <span data-ttu-id="5f600-121">Diese Merkmale wiederum enthalten Deskriptoren, von denen die Merkmale beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="5f600-121">Those characteristics, in turn, contain descriptors that describe the characteristics.</span></span> <span data-ttu-id="5f600-122">Diese 3 Begriffe werden allgemein als die Attribute eines Geräts bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5f600-122">These 3 terms are generically known as the attributes of a device.</span></span>

<span data-ttu-id="5f600-123">Bluetooth LE GATT-APIs machen Objekte und Funktionen verfügbar, statt den Zugriff auf den unformatierten Transport.</span><span class="sxs-lookup"><span data-stu-id="5f600-123">The Bluetooth LE GATT APIs expose objects and functions, rather than access to the raw transport.</span></span> <span data-ttu-id="5f600-124">Die GATT-APIs ermöglichen auch Entwicklern arbeiten mit Bluetooth LE-Geräte in die Möglichkeit, die folgenden Aufgaben ausführen:</span><span class="sxs-lookup"><span data-stu-id="5f600-124">The GATT APIs also enable developers to work with Bluetooth LE devices with the ability to perform the following tasks:</span></span>

-   <span data-ttu-id="5f600-125">Attributermittlung ausführen</span><span class="sxs-lookup"><span data-stu-id="5f600-125">Perform attribute discovery</span></span>
-   <span data-ttu-id="5f600-126">Lese- und Schreibzugriff Attributwerte</span><span class="sxs-lookup"><span data-stu-id="5f600-126">Read and Write attribute values</span></span>
-   <span data-ttu-id="5f600-127">Registrieren eines Rückrufs für Merkmal ValueChanged-Ereignis</span><span class="sxs-lookup"><span data-stu-id="5f600-127">Register a callback for Characteristic ValueChanged event</span></span>

<span data-ttu-id="5f600-128">Um eine sinnvolle Implementierung erstellen Sie ein Entwickler benötigen Vorkenntnisse bezüglich der GATT-Dienste und-Merkmale, die die Anwendung nutzen möchte, dass die spezifischen Merkmalswerte, so dass die von der API bereitgestellten Binärdaten in umgewandelt werden nützliche Daten vor dem Benutzer präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="5f600-128">To create a useful implementation a developer must have prior knowledge of the GATT services and characteristics the application intends to consume and to process the specific characteristic values such that the binary data provided by the API is transformed into useful data before being presented to the user.</span></span> <span data-ttu-id="5f600-129">Die Bluetooth GATT-APIs machen nur die Grundtypen verfügbar, die für die Kommunikation mit einem Bluetooth LE-Gerät erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="5f600-129">The Bluetooth GATT APIs expose only the basic primitives required to communicate with a Bluetooth LE device.</span></span> <span data-ttu-id="5f600-130">Zum Interpretieren der Daten muss ein Anwendungsprofil definiert werden, entweder durch ein Bluetooth SIG-Standardprofil oder mit einem benutzerdefinierten Profil, das von einem Geräteanbieter implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="5f600-130">To interpret the data, an application profile must be defined, either by a Bluetooth SIG standard profile, or a custom profile implemented by a device vendor.</span></span> <span data-ttu-id="5f600-131">Ein Profil begründet einen bindenden Vertrag zwischen Anwendung und Gerät darüber, was von den ausgetauschten Daten dargestellt wird und wie sie zu interpretieren sind.</span><span class="sxs-lookup"><span data-stu-id="5f600-131">A profile creates a binding contract between the application and the device, as to what the exchanged data represents and how to interpret it.</span></span>

<span data-ttu-id="5f600-132">Aus Gründen der Benutzerfreundlichkeit pflegt Bluetooth SIG eine [Liste der öffentlichen Profile](https://www.bluetooth.com/specifications/adopted-specifications#gattspec), die zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="5f600-132">For convenience the Bluetooth SIG maintains a [list of public profiles](https://www.bluetooth.com/specifications/adopted-specifications#gattspec) available.</span></span>

## <a name="query-for-nearby-devices"></a><span data-ttu-id="5f600-133">Abfrage von Geräten in der Nähe</span><span class="sxs-lookup"><span data-stu-id="5f600-133">Query for nearby devices</span></span>
<span data-ttu-id="5f600-134">Es gibt zwei wichtigste Methoden bei Geräten in der Nähe der Abfrage:</span><span class="sxs-lookup"><span data-stu-id="5f600-134">There are two main methods to query for nearby devices:</span></span>
- <span data-ttu-id="5f600-135">DeviceWatcher in Windows.Devices.Enumeration</span><span class="sxs-lookup"><span data-stu-id="5f600-135">DeviceWatcher in Windows.Devices.Enumeration</span></span>
- <span data-ttu-id="5f600-136">AdvertisementWatcher in Windows.Devices.Bluetooth.Advertisement</span><span class="sxs-lookup"><span data-stu-id="5f600-136">AdvertisementWatcher in Windows.Devices.Bluetooth.Advertisement</span></span>

<span data-ttu-id="5f600-137">2. Methode wird erläutert ausführlich in der [Ankündigung](ble-beacon.md) Dokumentation damit es erläutert wird nicht viel hier jedoch die grundlegende Idee besteht darin, die Adresse Bluetooth-Geräten in der Nähe zu finden, die bestimmten [Ankündigungsfilter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.advertisementfilter.aspx)erfüllen.</span><span class="sxs-lookup"><span data-stu-id="5f600-137">The 2nd method is discussed at length in the [Advertisement](ble-beacon.md) documentation so it won't be discussed much here but the basic idea is to find the Bluetooth address of nearby devices that satisfy the particular [Advertisement Filter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.advertisementfilter.aspx).</span></span> <span data-ttu-id="5f600-138">Wenn Sie die Adresse haben, können Sie [BluetoothLEDevice.FromBluetoothAddressAsync](https://msdn.microsoft.com/en-us/library/windows/apps/mt608819.aspx) zum Abrufen eines Verweises auf das Gerät aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5f600-138">Once you have the address, you can call [BluetoothLEDevice.FromBluetoothAddressAsync](https://msdn.microsoft.com/en-us/library/windows/apps/mt608819.aspx) to get a reference to the device.</span></span> 

<span data-ttu-id="5f600-139">Sichern Sie jetzt an die DeviceWatcher-Methode.</span><span class="sxs-lookup"><span data-stu-id="5f600-139">Now, back to the DeviceWatcher method.</span></span> <span data-ttu-id="5f600-140">Ein Bluetooth LE-Gerät verhält sich wie ein anderes Gerät unter Windows und unter Verwendung der [Enumerations-APIs](https://msdn.microsoft.com/library/windows/apps/BR225459)abgefragt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f600-140">A Bluetooth LE device is just like any other device in Windows and can be queried using the [Enumeration APIs](https://msdn.microsoft.com/library/windows/apps/BR225459).</span></span> <span data-ttu-id="5f600-141">Verwenden Sie die [DeviceWatcher](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher) -Klasse, und übergeben Sie eine Abfragezeichenfolge Angabe der Geräte zum Suchen nach:</span><span class="sxs-lookup"><span data-stu-id="5f600-141">Use the [DeviceWatcher](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher) class and pass a query string specifying the devices to look for:</span></span> 

```csharp
// Query for extra properties you want returned
string[] requestedProperties = { "System.Devices.Aep.DeviceAddress", "System.Devices.Aep.IsConnected" };

DeviceWatcher deviceWatcher =
            DeviceInformation.CreateWatcher(
                    BluetoothLEDevice.GetDeviceSelectorFromPairingState(false),
                    requestedProperties,
                    DeviceInformationKind.AssociationEndpoint);

// Register event handlers before starting the watcher.
// Added, Updated and Removed are required to get all nearby devices
deviceWatcher.Added += DeviceWatcher_Added;
deviceWatcher.Updated += DeviceWatcher_Updated;
deviceWatcher.Removed += DeviceWatcher_Removed;

// EnumerationCompleted and Stopped are optional to implement.
deviceWatcher.EnumerationCompleted += DeviceWatcher_EnumerationCompleted;
deviceWatcher.Stopped += DeviceWatcher_Stopped;

// Start the watcher.
deviceWatcher.Start();
```
<span data-ttu-id="5f600-142">Nachdem Sie die DeviceWatcher begonnen haben, erhalten Sie für jedes Gerät [DeviceInformation](https://msdn.microsoft.com/library/windows/apps/br225393) , die die Abfrage im Handler für das Ereignis [Added](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher.added) für die betreffenden Geräte erfüllt.</span><span class="sxs-lookup"><span data-stu-id="5f600-142">Once you've started the DeviceWatcher, you will receive [DeviceInformation](https://msdn.microsoft.com/library/windows/apps/br225393) for each device that satisfies the query in the handler for the [Added](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher.added) event for the devices in question.</span></span> <span data-ttu-id="5f600-143">Eine ausführlichere Betrachtung DeviceWatcher finden Sie in der vollständigen Beispiel [auf Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/DeviceEnumerationAndPairing).</span><span class="sxs-lookup"><span data-stu-id="5f600-143">For a more detailed look at DeviceWatcher see the complete sample [on Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/DeviceEnumerationAndPairing).</span></span> 

## <a name="connecting-to-the-device"></a><span data-ttu-id="5f600-144">Herstellen einer Verbindung mit dem Gerät</span><span class="sxs-lookup"><span data-stu-id="5f600-144">Connecting to the device</span></span>
<span data-ttu-id="5f600-145">Nachdem ein gewünschten Gerät erkannt wird, verwenden Sie die [DeviceInformation.Id](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.deviceinformation.id) , um das Objekt Bluetooth LE-Gerät für das Gerät betreffenden abzurufen:</span><span class="sxs-lookup"><span data-stu-id="5f600-145">Once a desired device is discovered, use the [DeviceInformation.Id](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.deviceinformation.id) to get the Bluetooth LE Device object for the device in question:</span></span> 

```csharp
async void ConnectDevice(DeviceInformation deviceInfo)
{
    // Note: BluetoothLEDevice.FromIdAsync must be called from a UI thread because it may prompt for consent.
    BluetoothLEDevice bluetoothLeDevice = await BluetoothLEDevice.FromIdAsync(deviceInfo.Id);
    // ...
}
```
<span data-ttu-id="5f600-146">Andererseits, Freigeben von alle Verweise auf ein BluetoothLEDevice-Objekt für ein Gerät zugeordnet ist (und keine andere app auf dem System einen Verweis auf das Gerät hat) löst ein automatisches nach Ablauf eines kleinen Timeouts zu trennen.</span><span class="sxs-lookup"><span data-stu-id="5f600-146">On the other hand, disposing of all references to a BluetoothLEDevice object for a device (and if no other app on the system has a reference to the device) will trigger an automatic disconnect after a small timeout period.</span></span> 

```csharp
bluetoothLeDevice.Dispose();
```
<span data-ttu-id="5f600-147">Wenn die app das Gerät erneut zugreifen muss, werden das Betriebssystem bei Bedarf wieder her einfach das Geräteobjekt neu zu erstellen und den Zugriff auf ein Merkmal (im nächsten Abschnitt erläutert) ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="5f600-147">If the app needs to access the device again, simply re-creating the device object and accessing a characteristic (discussed in the next section) will trigger the OS to re-connect when necessary.</span></span> <span data-ttu-id="5f600-148">Wenn das Gerät in Reichweite befindet, erhalten Sie Zugriff auf das Gerät andernfalls, die mit einem DeviceUnreachable Fehler zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f600-148">If the device is nearby, you'll get access to the device otherwise it will return w/ a DeviceUnreachable error.</span></span>  

## <a name="enumerating-supported-services-and-characteristics"></a><span data-ttu-id="5f600-149">Auflisten von unterstützten Dienste und-Merkmale</span><span class="sxs-lookup"><span data-stu-id="5f600-149">Enumerating supported services and characteristics</span></span>
<span data-ttu-id="5f600-150">Nun, da Sie ein Objekt BluetoothLEDevice haben, besteht der nächste Schritt, welche Daten zu erkennen des Geräts verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="5f600-150">Now that you have a BluetoothLEDevice object, the next step is to discover what data the device exposes.</span></span> <span data-ttu-id="5f600-151">Der erste Schritt zu diesem Zweck ist für Dienste Abfragen:</span><span class="sxs-lookup"><span data-stu-id="5f600-151">The first step to do this is to query for services:</span></span> 

```csharp
GattDeviceServicesResult result = await bluetoothLeDevice.GetGattServicesAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var services = result.Services;
    // ...
}
```
<span data-ttu-id="5f600-152">Nachdem der Dienst von Interesse identifiziert wurde, wird der nächste Schritt ist, zum Abfragen, um Merkmale.</span><span class="sxs-lookup"><span data-stu-id="5f600-152">Once the service of interest has been identified, the next step is to query for characteristics.</span></span> 

```csharp
GattCharacteristicsResult result = await service.GetCharacteristicsAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var characteristics = result.Characteristics;
    // ...
}
```  
<span data-ttu-id="5f600-153">Das Betriebssystem gibt, die eine schreibgeschützte Liste von GattCharacteristic-Objekten, die Sie Vorgänge durchführen können.</span><span class="sxs-lookup"><span data-stu-id="5f600-153">The OS returns a ReadOnly list of GattCharacteristic objects that you can then perform operations on.</span></span>

## <a name="perform-readwrite-operations-on-a-characteristic"></a><span data-ttu-id="5f600-154">Führen Sie Lese-/Schreibzugriff auf ein Merkmal</span><span class="sxs-lookup"><span data-stu-id="5f600-154">Perform Read/Write operations on a characteristic</span></span>

<span data-ttu-id="5f600-155">Das Merkmal ist, dass die grundlegende Einheit der GATT Kommunikation basiert.</span><span class="sxs-lookup"><span data-stu-id="5f600-155">The characteristic is the fundamental unit of GATT based communication.</span></span> <span data-ttu-id="5f600-156">Es enthält einen Wert, der einen unterschiedlichen Teil der Daten auf dem Gerät darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f600-156">It contains a value that represents a distinct piece of data on the device.</span></span> <span data-ttu-id="5f600-157">Beispielsweise hat das Level Akku-Merkmal einen Wert, der Akkustand des Geräts darstellt.</span><span class="sxs-lookup"><span data-stu-id="5f600-157">For example, the battery level characteristic has a value that represents the battery level of the device.</span></span>

<span data-ttu-id="5f600-158">Lesen Sie die charakteristischen Eigenschaften, um festzustellen, welche Vorgänge unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="5f600-158">Read the characteristic properties to determine what operations are supported:</span></span>
```csharp
GattCharacteristicProperties properties = characteristic.CharacteristicProperties

if(properties.HasFlag(GattCharacteristicProperties.Read))
{
    // This characteristic supports reading from it.
}
if(properties.HasFlag(GattCharacteristicProperties.Write))
{
    // This characteristic supports writing to it.
}
if(properties.HasFlag(GattCharacteristicProperties.Notify))
{
    // This characteristic supports subscribing to notifications.
}
```

<span data-ttu-id="5f600-159">Wenn lesen unterstützt wird, können Sie den Wert lesen:</span><span class="sxs-lookup"><span data-stu-id="5f600-159">If read is supported, you can read the value:</span></span> 
```csharp
GattReadResult result = await selectedCharacteristic.ReadValueAsync();
if (result.Status == GattCommunicationStatus.Success)
{
    var reader = DataReader.FromBuffer(result.Value);
    byte[] input = new byte[reader.UnconsumedBufferLength];
    reader.ReadBytes(input);
    // Utilize the data as needed
}
```
<span data-ttu-id="5f600-160">Schreiben in ein Merkmal folgt einem ähnlichen Muster:</span><span class="sxs-lookup"><span data-stu-id="5f600-160">Writing to a characteristic follows a similar pattern:</span></span> 
```csharp
var writer = new DataWriter();
// WriteByte used for simplicity. Other commmon functions - WriteInt16 and WriteSingle
writer.WriteByte(0x01);

GattReadResult result = await selectedCharacteristic.WriteValueAsync(writer.DetachBuffer());
if (result.Status == GattCommunicationStatus.Success)
{
    // Successfully wrote to device
}
```
> <span data-ttu-id="5f600-161">**Tipp**: Erste Schritte mit dem [DataReader](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datareader.aspx) und [DataWriter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datawriter.aspx)verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f600-161">**Tip**: Get comfortable with using [DataReader](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datareader.aspx) and [DataWriter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datawriter.aspx).</span></span> <span data-ttu-id="5f600-162">Die Funktionalität wird Anwendungsregistrierungsprüfpunkte, bei der Arbeit mit der unformatierten Puffer, die Sie aus vielen der die Bluetooth-APIs zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5f600-162">Their functionality will be indispensible when working with the raw buffers you get from many of the Bluetooth APIs.</span></span> 
## <a name="subscribing-for-notifications"></a><span data-ttu-id="5f600-163">Abonnieren für Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="5f600-163">Subscribing for notifications</span></span>

<span data-ttu-id="5f600-164">Stellen Sie sicher, das Merkmal unterstützt angeben oder benachrichtigen (Überprüfen Sie die charakteristischen Eigenschaften sicher).</span><span class="sxs-lookup"><span data-stu-id="5f600-164">Make sure the characteristic supports either Indicate or Notify (check the characteristic properties to make sure).</span></span> 

> <span data-ttu-id="5f600-165">**Reservieren**: angeben, wird eine zuverlässigere betrachtet, da jedes Ereignis geändert Wert mit einer Bestätigung durch den Client-Gerät gekoppelt ist.</span><span class="sxs-lookup"><span data-stu-id="5f600-165">**Aside**: Indicate is considered more reliable because each value changed event is coupled with an acknowledgement from the client device.</span></span> <span data-ttu-id="5f600-166">Benachrichtigen ist weiter verbreitet, da die meisten GATT-Transaktionen würden stattdessen Energie sparen, sondern äußerst zuverlässig.</span><span class="sxs-lookup"><span data-stu-id="5f600-166">Notify is more prevalent because most GATT transactions would rather conserve power rather than be extremely reliable.</span></span> <span data-ttu-id="5f600-167">In jedem Fall aller, erfolgt der Controller-Ebene, sodass die app nicht beteiligt sich ist.</span><span class="sxs-lookup"><span data-stu-id="5f600-167">In any case, all of that is handled at the controller layer so the app does not get involved.</span></span> <span data-ttu-id="5f600-168">Wir werden gemeinsam auf sie verweisen, als einfach "Notifications", aber Sie wissen jetzt.</span><span class="sxs-lookup"><span data-stu-id="5f600-168">We'll collectively refer to them as simply "notifications" but now you know.</span></span> 

<span data-ttu-id="5f600-169">Es gibt zwei Dinge zu erledigen vor dem Abrufen der Benachrichtigungen:</span><span class="sxs-lookup"><span data-stu-id="5f600-169">There are two things to take care of before getting notifications:</span></span>
- <span data-ttu-id="5f600-170">Schreiben Sie in Client charakteristische Konfiguration Deskriptor (CCCD)</span><span class="sxs-lookup"><span data-stu-id="5f600-170">Write to Client Characteristic Configuration Descriptor (CCCD)</span></span>
- <span data-ttu-id="5f600-171">Behandeln Sie das Characteristic.ValueChanged-Ereignis</span><span class="sxs-lookup"><span data-stu-id="5f600-171">Handle the Characteristic.ValueChanged event</span></span>

<span data-ttu-id="5f600-172">Schreiben in die CCCD weist dem Server-Gerät, dass dieser Client jedes Mal, bestimmten Merkmalen wertänderungen wissen möchte.</span><span class="sxs-lookup"><span data-stu-id="5f600-172">Writing to the CCCD tells the Server device that this client wants to know each time that particular characteristic value changes.</span></span> <span data-ttu-id="5f600-173">Gehen Sie dazu folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="5f600-173">To do this:</span></span> 

```csharp
GattCommunicationStatus status = await selectedCharacteristic.WriteClientCharacteristicConfigurationDescriptorAsync(
                        GattClientCharacteristicConfigurationDescriptorValue.Notify);
if(status == GattCommunicationStatus.Success)
{
    // Server has been informed of clients interest.
}
```
<span data-ttu-id="5f600-174">Nun die GattCharacteristic ValueChanged-Ereignis wird jedes Mal aufgerufen erhalten, der Wert auf dem Remotegerät geändert wird.</span><span class="sxs-lookup"><span data-stu-id="5f600-174">Now, the GattCharacteristic's ValueChanged event will get called each time the value gets changed on the remote device.</span></span> <span data-ttu-id="5f600-175">Nur noch ist den Ereignishandler implementiert:</span><span class="sxs-lookup"><span data-stu-id="5f600-175">All that's left is to implement the handler:</span></span> 

```csharp
characteristic.ValueChanged += Characteristic_ValueChanged;
// ... 

void Characteristic_ValueChanged(GattCharacteristic sender, 
                                    GattValueChangedEventArgs args)
{
    // An Indicate or Notify reported that the value has changed.
    var reader = DataReader.FromBuffer(args.CharacteristicValue)
    // Parse the data however required.
}
```


