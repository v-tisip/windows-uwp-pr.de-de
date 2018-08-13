---
author: msatranjr
title: Bluetooth-GATT-Client
description: Dieser Artikel enthält eine Übersicht über Bluetooth generische Attribut Profil (GATT) Client für apps mit Beispielcode für allgemeine Verwendungsszenarien universellen Windows-Plattform (UWP).
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 555fec6d534c07898acd911f9cd84a11ac66dcd8
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "305219"
---
# <a name="bluetooth-gatt-client"></a>Bluetooth-GATT-Client


**Wichtige APIs**

-   [**Windows.Devices.Bluetooth**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
-   [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685)

In diesem Artikel veranschaulicht die Verwendung der Bluetooth generische Attribut (GATT)-Client-APIs für apps universellen Windows-Plattform (UWP), zusammen mit Beispielcode für allgemeine Aufgaben von GATT-Client:
- Abfrage für Geräte in Reichweite
- Verbinden mit Gerät
- Auflisten der unterstützten Dienste und Merkmale des Geräts
- Lesen und Schreiben in ein Merkmal
- Abonnieren Sie für Benachrichtigungen, wenn charakteristische ändert Wert

## <a name="overview"></a>Übersicht
Entwickler können die APIs im Namespace [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685) Zugriff auf LE Bluetooth-Geräte verwenden. Bluetooth LE-Geräte machen ihre Funktionen über eine Sammlung folgender Elemente verfügbar:

-   Dienste
-   Merkmale
-   Deskriptoren

Dienste definieren den funktionalen Vertrag des Geräts LE und enthalten eine Auflistung von Eigenschaften, die den Dienst definiert. Diese Merkmale wiederum enthalten Deskriptoren, von denen die Merkmale beschrieben werden. Diese Begriffe 3 werden die Attribute eines Geräts generisch genannt.

Die Bluetooth-LE GATT APIs Objekte und Funktionen verfügbar machen, anstatt den Zugriff auf unformatierte Übertragungsprotokoll. Die GATT-APIs ermöglichen es auch Entwicklern LE Bluetooth-Geräten entwickelt, die Möglichkeit, die folgenden Aufgaben ausführen:

-   Attributermittlung ausführen
-   Lese- und Schreibzugriff Attributwerte
-   Registrieren eines Rückrufs für Merkmal ValueChanged-Ereignis

So erstellen Sie eine nützliche Implementierung ein Entwickler benötigen Vorkenntnisse GATT Dienste und Merkmale, die die Anwendung beabsichtigt, beanspruchen und an den Prozess, dass die bestimmte Merkmale Werte, die von der API bereitgestellten Binärdaten in umgewandelt wird nützliche Daten vor dem Benutzer angezeigt wird. Die Bluetooth GATT-APIs machen nur die Grundtypen verfügbar, die für die Kommunikation mit einem Bluetooth LE-Gerät erforderlich sind. Zum Interpretieren der Daten muss ein Anwendungsprofil definiert werden, entweder durch ein Bluetooth SIG-Standardprofil oder mit einem benutzerdefinierten Profil, das von einem Geräteanbieter implementiert wird. Ein Profil begründet einen bindenden Vertrag zwischen Anwendung und Gerät darüber, was von den ausgetauschten Daten dargestellt wird und wie sie zu interpretieren sind.

Aus Gründen der Benutzerfreundlichkeit pflegt Bluetooth SIG eine [Liste der öffentlichen Profile](https://www.bluetooth.com/specifications/adopted-specifications#gattspec), die zur Verfügung stehen.

## <a name="query-for-nearby-devices"></a>Abfrage für Geräte in Reichweite
Es gibt zwei Hauptmethoden für Geräte in Reichweite Abfragen:
- DeviceWatcher in Windows.Devices.Enumeration
- AdvertisementWatcher in Windows.Devices.Bluetooth.Advertisement

Die 2.-Methode erläutert wird ausführlich in der Dokumentation der [Ankündigung](ble-beacon.md) , damit es noch ausführlicher beleuchtet wird nicht viel hier aber die grundlegende Idee ist die Bluetooth-Adresse des benachbarten Geräte zu finden, die bestimmten [Ankündigung Filter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher.advertisementfilter.aspx)erfüllen. Nachdem Sie die Adresse haben, können Sie [BluetoothLEDevice.FromBluetoothAddressAsync](https://msdn.microsoft.com/en-us/library/windows/apps/mt608819.aspx) zum Abrufen eines Verweises auf das Gerät aufrufen. 

Nun, die zurück an die DeviceWatcher-Methode. Ein Gerät Bluetooth LE verhält sich wie jedes andere Gerät in Windows und mithilfe der [Enumeration APIs](https://msdn.microsoft.com/library/windows/apps/BR225459)abgefragt werden kann. Verwenden Sie die [DeviceWatcher](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher) -Klasse, und übergeben Sie eine Abfragezeichenfolge, suchen Sie nach der Geräte angeben: 

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
Nachdem Sie die DeviceWatcher gestartet haben, erhalten [DeviceInformation](https://msdn.microsoft.com/library/windows/apps/br225393) für jedes Gerät Sie, die die Abfrage im Ereignishandler für das Ereignis [hinzugefügt](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.devicewatcher.added) , für die betreffende Geräte erfüllt. Eine weitere detaillierte Aufstellung der DeviceWatcher finden Sie unter sample [auf Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/DeviceEnumerationAndPairing)abgeschlossen. 

## <a name="connecting-to-the-device"></a>Herstellen einer Verbindung mit dem Gerät
Sobald ein gewünschte Gerät erkannt wird, verwenden Sie die [DeviceInformation.Id](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.deviceinformation.id) um das Gerät LE-Objekt für das Gerät fraglichen abzurufen: 

```csharp
async void ConnectDevice(DeviceInformation deviceInfo)
{
    // Note: BluetoothLEDevice.FromIdAsync must be called from a UI thread because it may prompt for consent.
    BluetoothLEDevice bluetoothLeDevice = await BluetoothLEDevice.FromIdAsync(deviceInfo.Id);
    // ...
}
```
Andererseits, alle Verweise auf ein BluetoothLEDevice abstoßen-Objekt für ein Gerät (und wenn keine andere app auf dem System einen Verweis auf das Gerät verfügt) löst eine automatische nach Ablauf eines kleinen Timeout zu trennen. 

```csharp
bluetoothLeDevice.Dispose();
```
Wenn die app das Gerät erneut zugreifen muss, werden das Betriebssystem bei Bedarf wieder her einfach das Objekt neu zu erstellen und den Zugriff auf ein Merkmal (im nächsten Abschnitt erläutert) ausgelöst werden. Wenn das Gerät in der Nähe ist, erhalten Sie Zugriff auf das Gerät andernfalls, die mit einem DeviceUnreachable-Fehler zurückgegeben wird.  

## <a name="enumerating-supported-services-and-characteristics"></a>Aufzählen von unterstützten Dienste und Merkmale
Nun, da Sie ein Objekt BluetoothLEDevice haben, besteht der nächste Schritt ermitteln können, welche Daten das Gerät verfügbar macht. Im ersten Schritt dazu Abfragen für Dienste: 

```csharp
GattDeviceServicesResult result = await bluetoothLeDevice.GetGattServicesAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var services = result.Services;
    // ...
}
```
Nachdem der Dienst von Interesse identifiziert wurde, wird im nächste Schritt zum Abfragen nach Merkmale. 

```csharp
GattCharacteristicsResult result = await service.GetCharacteristicsAsync();
                
if (result.Status == GattCommunicationStatus.Success)
{
    var characteristics = result.Characteristics;
    // ...
}
```  
Das Betriebssystem gibt eine Liste ReadOnly GattCharacteristic-Objekten, die Sie Vorgänge durchführen können.

## <a name="perform-readwrite-operations-on-a-characteristic"></a>Ausführen von Lese-/Schreibvorgängen auf ein Merkmal

Die Eigenschaft ist, dass die Basiseinheit von GATT Kommunikation basiert. Es enthält einen Wert, der einen distinct Teil der Daten auf dem Gerät darstellt. Beispielsweise hat das Batterie Ebene Merkmal ein Werts, das den Batterie des Geräts darstellt.

Lesen Sie die charakteristischen Eigenschaften zum bestimmen, welche Vorgänge unterstützt werden:
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
Schreiben in ein Merkmal folgt einem ähnlichen Muster: 
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
> **Tipp**: machen Sie sich bei der Verwendung von [DataReader](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datareader.aspx) und [DataWriter](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.datawriter.aspx)vertraut. Die Funktionalität wird Anwendungsregistrierungsprüfpunkte, beim Arbeiten mit der Roh Puffer, die Sie aus der Bluetooth-APIs viele erhalten. 
## <a name="subscribing-for-notifications"></a>Für Benachrichtigungen abonnieren

Stellen Sie sicher, dass die Eigenschaft unterstützt, angeben oder benachrichtigen (Überprüfen Sie die charakteristischen Eigenschaften sicherstellen). 

> **Reserviert**: Geben Sie an, gilt als zuverlässiger, da jeder Wert geändert-Ereignis mit einer Bestätigung vom Clientgerät gekoppelt ist. Benachrichtigen Sie häufiger ist, da die meisten GATT Transaktionen würden vielmehr Strom sparen, sondern äußerst zuverlässigen werden. In jedem Fall all das erfolgt auf der Ebene der Domänencontroller so, dass die app nicht beteiligt abgerufen wird. Nun wissen, aber wir können zusammen auf diese verweisen, als einfach "Benachrichtigungen". 

Es gibt zwei Dinge zu erledigen bevor Benachrichtigungen abrufen:
- Schreiben Sie in Client charakteristische Konfiguration Deskriptor (CCCD)
- Behandeln Sie das Characteristic.ValueChanged-Ereignis

Schreiben in die CCCD weist dem Server-Gerät, dass dieser Client möchte wissen, jedes Mal, bestimmten charakteristischen Wert sich ändert. Gehen Sie dazu folgendermaßen vor: 

```csharp
GattCommunicationStatus status = await selectedCharacteristic.WriteClientCharacteristicConfigurationDescriptorAsync(
                        GattClientCharacteristicConfigurationDescriptorValue.Notify);
if(status == GattCommunicationStatus.Success)
{
    // Server has been informed of clients interest.
}
```
Nun, die GattCharacteristic ValueChanged-Ereignis wird jedes Mal aufgerufen erhalten möchten, der Wert auf dem entfernten Gerät geändert wird. Ist den Ereignishandler implementiert wird: 

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


