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
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7291207"
---
# <a name="bluetooth-gatt-client"></a>Bluetooth GATT-Client


**Wichtige APIs**

-   [**Windows.Devices.Bluetooth**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
-   [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685)

Dieser Artikel veranschaulicht die Verwendung der Bluetooth-Generic Attribut (GATT)-Client-APIs für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine GATT-Client-Aufgaben:
- Abfrage von Geräten in der Nähe
- Verbinden mit Gerät
- Auflisten der unterstützten Dienste und-Merkmale des Geräts
- Lesen und Schreiben von einem Merkmal
- Abonnieren Sie für Benachrichtigungen bei charakteristische ändert Wert

## <a name="overview"></a>Übersicht
Entwickler können die APIs im [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685) -Namespace verwenden, den Zugriff auf Bluetooth LE-Geräte. Bluetooth LE-Geräte machen ihre Funktionen über eine Sammlung folgender Elemente verfügbar:

-   Dienste
-   Merkmale
-   Deskriptoren

Dienste definieren den funktionsvertrag des LE-Geräts und enthalten eine Sammlung der Merkmale, die den Dienst definieren. Diese Merkmale wiederum enthalten Deskriptoren, von denen die Merkmale beschrieben werden. Diese 3 Begriffe werden allgemein als die Attribute eines Geräts bezeichnet.

Die Bluetooth LE-GATT-APIs machen Objekte und Funktionen, statt den Zugriff auf den unformatierten Transport. Die GATT-APIs ermöglichen auch Entwicklern arbeiten mit Bluetooth LE-Geräte in die Möglichkeit, die folgenden Aufgaben ausführen:

-   Attributermittlung ausführen
-   Lese- und Schreibzugriff Attributwerte
-   Registrieren eines Rückrufs für Merkmal ValueChanged-Ereignis

Wenn eine sinnvolle Implementierung Entwickler erstellen benötigen Vorkenntnisse bezüglich der GATT-Dienste und-Merkmale, die die Anwendung verwendet, dass die spezifischen Merkmalswerte, sodass die von der API bereitgestellten Binärdaten in umgewandelt werden nützliche Daten vor dem Benutzer präsentiert wird. Die Bluetooth GATT-APIs machen nur die Grundtypen verfügbar, die für die Kommunikation mit einem Bluetooth LE-Gerät erforderlich sind. Zum Interpretieren der Daten muss ein Anwendungsprofil definiert werden, entweder durch ein Bluetooth SIG-Standardprofil oder mit einem benutzerdefinierten Profil, das von einem Geräteanbieter implementiert wird. Ein Profil begründet einen bindenden Vertrag zwischen Anwendung und Gerät darüber, was von den ausgetauschten Daten dargestellt wird und wie sie zu interpretieren sind.

Aus Gründen der Benutzerfreundlichkeit pflegt Bluetooth SIG eine [Liste der öffentlichen Profile](https://www.bluetooth.com/specifications/adopted-specifications#gattspec), die zur Verfügung stehen.

## <a name="query-for-nearby-devices"></a>Abfrage von Geräten in der Nähe
Es gibt zwei wichtigste Methoden bei Geräten in der Nähe der Abfrage:
- DeviceWatcher in Windows.Devices.Enumeration
- AdvertisementWatcher in Windows.Devices.Bluetooth.Advertisement

Die 2. Methode erläutert wird ausführlich in der Dokumentation zu [Ankündigung](ble-beacon.md) damit es erläutert wird nicht viel hier jedoch die grundlegende Idee ist in den Bluetooth-Geräten in der Nähe suchen, die die bestimmten [Ankündigungsfilter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.advertisementfilter.aspx)erfüllen. Wenn Sie die Adresse haben, können Sie [BluetoothLEDevice.FromBluetoothAddressAsync](https://msdn.microsoft.com/en-us/library/windows/apps/mt608819.aspx) zum Abrufen eines Verweises auf das Gerät aufrufen. 

Sichern Sie jetzt an die DeviceWatcher-Methode. Ein Bluetooth LE-Gerät verhält sich wie ein anderes Gerät in Windows und kann unter Verwendung der [Enumerations-APIs](https://msdn.microsoft.com/library/windows/apps/BR225459)abgefragt werden. Verwenden Sie die [DeviceWatcher](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher) -Klasse, und übergeben Sie eine Abfragezeichenfolge Angabe der Geräte zum Suchen nach: 

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
Nachdem Sie die DeviceWatcher begonnen haben, erhalten [DeviceInformation](https://msdn.microsoft.com/library/windows/apps/br225393) Sie für jedes Gerät, die die Abfrage im Handler für das Ereignis [Added](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher.added) für die betreffenden Geräte erfüllt. Eine ausführlichere Betrachtung DeviceWatcher finden Sie in der vollständigen Beispiel [auf Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/DeviceEnumerationAndPairing). 

## <a name="connecting-to-the-device"></a>Herstellen einer Verbindung mit dem Gerät
Nachdem ein gewünschten Gerät erkannt wird, verwenden Sie die [DeviceInformation.Id](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.deviceinformation.id) das Objekt Bluetooth LE-Gerät für das Gerät betreffenden abrufen: 

```csharp
async void ConnectDevice(DeviceInformation deviceInfo)
{
    // Note: BluetoothLEDevice.FromIdAsync must be called from a UI thread because it may prompt for consent.
    BluetoothLEDevice bluetoothLeDevice = await BluetoothLEDevice.FromIdAsync(deviceInfo.Id);
    // ...
}
```
Andererseits, Freigeben von alle Verweise auf ein BluetoothLEDevice-Objekt für ein Gerät zugeordnet ist (und keine andere app auf dem System einen Verweis auf das Gerät hat) löst ein Automatisches Trennen nach einem kleinen Timeout-Zeitraum. 

```csharp
bluetoothLeDevice.Dispose();
```
Wenn die app das Gerät erneut zugreifen muss, werden einfach das Geräteobjekt neu zu erstellen und den Zugriff auf ein Merkmal (im nächsten Abschnitt erläutert) das Betriebssystem Verbindung bei Bedarf erneut auslösen. Wenn das Gerät in Reichweite befindet, erhalten Sie Zugriff auf das Gerät andernfalls, die mit einem DeviceUnreachable Fehler zurückgegeben wird.  

## <a name="enumerating-supported-services-and-characteristics"></a>Auflisten von unterstützten Dienste und-Merkmale
Nun, da Sie ein Objekt BluetoothLEDevice haben, besteht der nächste Schritt, welche Daten zu erkennen, das Gerät verfügbar macht. Der erste Schritt zu diesem Zweck ist für Dienste Abfragen: 

```csharp
GattDeviceServicesResult result = await bluetoothLeDevice.GetGattServicesAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var services = result.Services;
    // ...
}
```
Nachdem der Dienst von Interesse identifiziert wurde, wird der nächste Schritt ist, um Merkmale Abfragen. 

```csharp
GattCharacteristicsResult result = await service.GetCharacteristicsAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var characteristics = result.Characteristics;
    // ...
}
```  
Das Betriebssystem gibt, die eine schreibgeschützte Liste von GattCharacteristic-Objekten, die Sie Vorgänge durchführen können.

## <a name="perform-readwrite-operations-on-a-characteristic"></a>Führen Sie Lese-/Schreibzugriff auf ein Merkmal

Das Merkmal ist, dass die grundlegende Einheit der GATT Kommunikation basiert. Es enthält einen Wert, der auf dem Gerät ein eindeutiges Datenelements darstellt. Beispielsweise hat der Akku-Level-Merkmal einen Wert, der Akkustand des Geräts darstellt.

Lesen Sie die charakteristischen Eigenschaften, um festzustellen, welche Vorgänge unterstützt werden:
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

Wenn lesen unterstützt wird, können Sie den Wert lesen: 
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
Schreiben von einem Merkmal folgt einem ähnlichen Muster: 
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
> **Tipp**: Erste Schritte mit dem [DataReader](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datareader.aspx) und [DataWriter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datawriter.aspx)verwenden. Die Funktionalität wird Anwendungsregistrierungsprüfpunkte, bei der Arbeit mit der unformatierten Puffer, die Sie aus vielen der die Bluetooth-APIs zu erhalten. 
## <a name="subscribing-for-notifications"></a>Abonnieren für Benachrichtigungen

Stellen Sie sicher, das Merkmal unterstützt entweder angeben oder benachrichtigen (Überprüfen Sie die charakteristischen Eigenschaften sicher). 

> **Reservieren**: angeben, gilt als zuverlässiger, da jedes Ereignis Wert hat sich geändert, die mit einer Bestätigung durch den Client-Gerät gekoppelt ist. Benachrichtigen ist weiter verbreitet, da die meisten GATT-Transaktionen würden stattdessen Energie sparen, sondern äußerst zuverlässig. In jedem Fall aller, erfolgt der Controller-Ebene, sodass die app nicht beteiligt sich. Wir werden gemeinsam auf sie verweisen, als einfach "Notifications", aber Sie wissen jetzt. 

Es gibt zwei Dinge zu erledigen vor dem Abrufen der Benachrichtigungen:
- Schreiben Sie in Client charakteristische Konfiguration Deskriptor (CCCD)
- Behandeln Sie das Characteristic.ValueChanged-Ereignis

Schreiben in die CCCD weist dem Server-Gerät, dass dieser Client jedes Mal dieses bestimmten Merkmalen wertänderungen wissen möchte. Gehen Sie dazu folgendermaßen vor: 

```csharp
GattCommunicationStatus status = await selectedCharacteristic.WriteClientCharacteristicConfigurationDescriptorAsync(
                        GattClientCharacteristicConfigurationDescriptorValue.Notify);
if(status == GattCommunicationStatus.Success)
{
    // Server has been informed of clients interest.
}
```
Nun die GattCharacteristic ValueChanged-Ereignis wird jedes Mal aufgerufen erhalten, der Wert auf dem Remotegerät geändert wird. Übrig ist lediglich den Ereignishandler implementiert: 

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


