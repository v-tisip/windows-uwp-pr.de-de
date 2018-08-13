---
author: msatranjr
title: Bluetooth-GATT Server
description: Dieser Artikel enthält eine Übersicht über Bluetooth generische Attribut Profil (GATT) Server für apps mit Beispielcode für allgemeine Verwendungsszenarien universellen Windows-Plattform (UWP).
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 27154fbb535b76995fba97702e65a9c0b2a8291c
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "610769"
---
# <a name="bluetooth-gatt-server"></a>Bluetooth-GATT Server


**Wichtige APIs**
- [**Windows.Devices.Bluetooth**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
- [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685)


In diesem Artikel wird das Bluetooth generische Attribut (GATT)-Server-APIs für apps universellen Windows-Plattform (UWP), zusammen mit Beispielcode für allgemeine GATT Serveraufgaben veranschaulicht: 
- Definieren der unterstützten Dienste
- Veröffentlichen Sie Server, damit er von Remoteclients erkannt werden können
- Unterstützung für den Dienst kündigen
- Antworten Sie zum Lesen und Schreiben von Anfragen
- Senden von Benachrichtigungen an abonnierten clients

## <a name="overview"></a>Übersicht
Windows funktioniert in der Regel in der Clientrolle. Viele Szenarien auftreten dennoch als Bluetooth-LE GATT Server als auch für Windows erforderlich. Nahezu alle Szenarien für IoT-Geräten zusammen mit den meisten plattformübergreifende BLE Kommunikation erfordern die Windows Server GATT zu sein. Darüber hinaus Benachrichtigungen gesendet werden, in der Nähe wearable Geräte ein gängiges Szenario geworden, das diese Technologie sowie erforderlich sind.  
> Stellen Sie sicher, dass alle Konzepte in der [GATT Client Dokumente](gatt-client.md) löschen, bevor Sie fortfahren können.  

Server-Vorgänge werden um den Dienstanbieter und den GattLocalCharacteristic drehen. Diese zwei Klassen bietet die Funktionalität zum Deklarieren, implementieren und machen eine Hierarchie von Daten an ein remote-Gerät erforderlich.

## <a name="define-the-supported-services"></a>Definieren der unterstützten Dienste
Ihre app kann einen oder mehrere Dienste deklarieren, die von Windows veröffentlicht wird. Jeder Dienst wird durch eine UUID eindeutig identifiziert. 

### <a name="attributes-and-uuids"></a>Attribute und UUID
Jeder Dienst, Merkmale und Deskriptor wird definiert durch eigenen eindeutigen 128-Bit-UUID ist.
> Windows-APIs verwenden diesen Begriff GUID, aber der Bluetooth-Standard definiert diese als UUIDs. Für unsere Zwecke sind diese beiden Begriffe austauschbar, damit auch den Begriff UUID verwenden. 

Wenn das Attribut Standard- und definiert durch die Bluetooth SIG definiert ist, wird es auch eine entsprechende kurze 16-Bit-ID haben (z. B. Batterie Ebene UUID ist 0000**2A19**-0000-1000-8000-00805F9B34FB und die kurzen ID ist 0x2A19). Diese standard UUIDs können in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) und [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx)angezeigt werden.

Wenn Ihre app implementiert eigenen benutzerdefinierten Dienst, eine benutzerdefinierte UUID generiert werden müssen. Hierbei handelt es sich einfach in Visual Studio über Tools -> CreateGuid (Verwendung Option 5 für die abzurufenden im Format "Xxxxxxxx-Xxxx-... Xxxx"). Dieser Uuid kann jetzt verwendet werden, um neue lokale Dienste, Eigenschaften oder Deskriptoren zu deklarieren.

#### <a name="restricted-services"></a>Eingeschränkte Dienste
Die folgenden Dienste werden vom System reserviert und können zu diesem Zeitpunkt nicht veröffentlicht werden:
1. Gerät Informationsdienst (DIS)
2. Generische Attribut Profildienst (GATT)
3. Generische Access Profildienst (Abstand)
4. Human Interface Device Service (HOGP)
5. Scannen Sie Parameter Service (SCP)

> Versuchen, einen blockierten Dienst zu erstellen, führt zu BluetoothError.DisabledByPolicy aus dem Aufruf von CreateAsync zurückgegeben wird.

#### <a name="generated-attributes"></a>Erzeugte Attribute
Die folgenden Deskriptoren werden automatisch vom System, basierend auf der GattLocalCharacteristicParameters während der Erstellung der Merkmal bereitgestellt:
1. Merkmal-Clientkonfiguration (falls die Eigenschaft als indicatable oder gemeldet gekennzeichnet ist).
2. Charakteristische Benutzerbeschreibung (falls UserDescription-Eigenschaft festgelegt ist). Siehe GattLocalCharacteristicParameters.UserDescription-Eigenschaft für Weitere Informationen.
3. Charakteristische Format (eine Beschreibung für jede Präsentationsformat angegeben).  Siehe GattLocalCharacteristicParameters.PresentationFormats-Eigenschaft für Weitere Informationen.
4. Charakteristische Aggregate-Format (Wenn mehr als eine Präsentationsformat angegeben ist).  GattLocalCharacteristicParameters.See PresentationFormats-Eigenschaft für Weitere Informationen.
5. Charakteristische erweiterte Eigenschaften (wenn die Eigenschaft mit dem erweiterten Eigenschaften Bit markiert ist).

> Der Wert der Deskriptor erweiterte Eigenschaften wird über die charakteristischen Eigenschaften ReliableWrites und WritableAuxiliaries bestimmt.

> Versuch, einen reservierten Deskriptor erstellen führt zu einer Ausnahme.

> Beachten Sie, dass Broadcast zu diesem Zeitpunkt nicht unterstützt wird.  Angeben der Broadcast GattCharacteristicProperty führt zu einer Ausnahme.

### <a name="build-up-the-heirarchy-of-services-and-characteristics"></a>Erstellen Sie die Hierarchie der Dienste und Merkmale
Die GattServiceProvider dient zum Erstellen und die primäre Dienstdefinition Stamm ankündigen.  Jeder Dienst erfordert, dass sie eigene ServiceProvider-Objekt ist, die in eine GUID akzeptiert: 

```csharp
GattServiceProviderResult result = await GattServiceProvider.CreateAsync(uuid);

if (result.Error == BluetoothError.Success)
{
    serviceProvider = result.ServiceProvider;
    // 
}
```
> Primäre Dienste sind die oberste Ebene der Struktur des GATT. Primäre Services enthalten Merkmale als auch für andere Dienste (mit der Bezeichnung 'Included' oder sekundären Services). 

Nun, füllen Sie den Dienst mit den erforderlichen Merkmale und Deskriptoren:

```csharp
GattLocalCharacteristicResult characteristicResult = await serviceProvider.Service.CreateCharacteristicAsync(uuid1, ReadParameters);
if (characteristicResult.Error != BluetoothError.Success)
{
    // An error occurred.
    return;
}
_readCharacteristic = characteristicResult.Characteristic;
_readCharacteristic.ReadRequested += ReadCharacteristic_ReadRequested;

characteristicResult = await serviceProvider.Service.CreateCharacteristicAsync(uuid2, WriteParameters);
if (characteristicResult.Error != BluetoothError.Success)
{
    // An error occurred.
    return;
}
_writeCharacteristic = characteristicResult.Characteristic;
_writeCharacteristic.WriteRequested += WriteCharacteristic_WriteRequested;

characteristicResult = await serviceProvider.Service.CreateCharacteristicAsync(uuid3, NotifyParameters);
if (characteristicResult.Error != BluetoothError.Success)
{
    // An error occurred.
    return;
}
_notifyCharacteristic = characteristicResult.Characteristic;
_notifyCharacteristic.SubscribedClientsChanged += SubscribedClientsChanged;
```
Wie oben gezeigt, ist dies auch eine ausgezeichnete Quelle für den Ereignishandler für die Vorgänge zu deklarieren, jede Eigenschaft unterstützt.  Um die Anfrage ordnungsgemäß bearbeiten eine app muss definiert und einen Ereignishandler für die einzelnen Anforderung das Attribut unterstützt festgelegt.  Einen Handler registriert, die Fehler aufweisen führt die Anforderung wird unmittelbar vom System mit *UnlikelyError* abgeschlossen.

### <a name="constant-characteristics"></a>Konstante Merkmale
In einigen Fällen sind charakteristische Werte, die im Verlauf der Lebensdauer der app nicht geändert werden. In diesem Fall ist es ratsam, deklarieren Sie ein Merkmal Konstante verhindern Sie unnötige app-Aktivierung: 

```csharp
byte[] value = new byte[] {0x21};
var constantParameters = new GattLocalCharacteristicParameters
{
    CharacteristicProperties = (GattCharacteristicProperties.Read),
    StaticValue = value.AsBuffer(),
    ReadProtectionLevel = GattProtectionLevel.Plain,
};

var characteristicResult = await serviceProvider.Service.CreateCharacteristicAsync(uuid4, constantParameters);
if (characteristicResult.Error != BluetoothError.Success)
{
    // An error occurred.
    return;
}
```
## <a name="publish-the-service"></a>Veröffentlichen Sie den Dienst
Nachdem der Dienst vollständig definiert wurde, besteht der nächste Schritt Unterstützung für den Dienst veröffentlichen. Das Betriebssystem weiß, dass der Dienst zurückgegeben werden sollen, wenn remote-Geräte eine Suche ausführen.  Sie müssen zwei Eigenschaften - IsDiscoverable und IsConnectable festzulegen:  

```csharp
GattServiceProviderAdvertisingParameters advParameters = new GattServiceProviderAdvertisingParameters
{
    IsDiscoverable = true,
    IsConnectable = true
};
serviceProvider.StartAdvertising(advParameters);
```
- **IsDiscoverable**: Gibt den Anzeigenamen für remote-Geräte in die Ankündigung, die das Gerät sichtbar zu machen.
- **IsConnectable**: Gibt eine Verbindbare Werbung für die Verwendung in peripherer Rolle bekannt.

> Wenn ein Dienst erkennbar und Connectable ist, wird das System den Dienst Uuid das Paket Ankündigung hinzufügen.  Es gibt nur 31 Bytes im Paket Ankündigung und eine UUID 128-Bit-benötigt 16 davon!

> Beachten Sie, dass bei ein Dienst im Vordergrund veröffentlicht wird, eine Anwendung StopAdvertising beim Aufrufen muss die Anwendung angehalten.

## <a name="respond-to-read-and-write-requests"></a>Antworten Sie zum Lesen und Schreiben von Anfragen
Wie wir oben gezeigt, während durch die erforderlichen Merkmale deklarieren, haben GattLocalCharacteristics 3 Arten von Ereignissen - ReadRequested, WriteRequested und SubscribedClientsChanged.

### <a name="read"></a>Lesen
Wenn ein Gerät remote versucht, einen Wert ein Merkmal lesen (und es ist nicht um einen konstanten Wert), wird das ReadRequested-Ereignis aufgerufen. Die Merkmale das Lesen auf sowie Args (mit Informationen zu dem entfernten Gerät) aufgerufen wurde, wird an des Delegaten übergeben: 

```csharp
characteristic.ReadRequested += Characteristic_ReadRequested;
// ... 

async void ReadCharacteristic_ReadRequested(GattLocalCharacteristic sender, GattReadRequestedEventArgs args)
{
    var deferral = args.GetDeferral();
    
    // Our familiar friend - DataWriter.
    var writer = new DataWriter();
    // populate writer w/ some data. 
    // ... 

    var request = await args.GetRequestAsync();
    request.RespondWithValue(writer.DetachBuffer());
    
    deferral.Complete();
}
``` 

### <a name="write"></a>Schreiben
Wenn ein Gerät remote versucht, einen Wert in ein Merkmal schreiben, wird das Ereignis WriteRequested mit Details zu dem entfernten Gerät, welche Merkmal geschrieben und den Wert selbst aufgerufen: 

```csharp
characteristic.ReadRequested += Characteristic_ReadRequested;
// ...

async void WriteCharacteristic_WriteRequested(GattLocalCharacteristic sender, GattWriteRequestedEventArgs args)
{
    var deferral = args.GetDeferral();
    
    var request = await args.GetRequestAsync();
    var reader = DataReader.FromBuffer(request.Value);
    // Parse data as necessary. 

    if (request.Option == GattWriteOption.WriteWithResponse)
    {
        request.Respond();
    }
    
    deferral.Complete();
}
```
2 Schreibvorgänge - Typen mit und ohne Antwort sind vorhanden. Verwenden Sie GattWriteOption (eine Eigenschaft für das Objekt GattWriteRequest), um herauszufinden, welche Art von Schreibzugriff auf das entfernte Gerät ausgeführt wird. 

## <a name="send-notifications-to-subscribed-clients"></a>Senden von Benachrichtigungen an abonnierten clients
Häufigste GATT Servervorgänge Benachrichtigungen führen Sie die entscheidende Funktion pushen von Daten für die remote-Geräte. In einigen Fällen sollten Sie benachrichtigen alle abonnierten Clients jedoch Othertimes, die Sie möglicherweise auf welchen Geräten zum Senden des neuen Werts mit auswählen möchten: 

```csharp
async void NotifyValue()
{
    var writer = new DataWriter();
    // Populate writer with data
    // ...
    
    await notifyCharacteristic.NotifyValueAsync(writer.DetachBuffer());
}
```

Wenn ein neues Gerät für Benachrichtigungen abonniert, ruft das SubscribedClientsChanged-Ereignis aufgerufen: 

```csharp
characteristic.SubscribedClientsChanged += SubscribedClientsChanged;
// ...

void _notifyCharacteristic_SubscribedClientsChanged(GattLocalCharacteristic sender, object args)
{
    List<GattSubscribedClient> clients = sender.SubscribedClients;
    // Diff the new list of clients from a previously saved one 
    // to get which device has subscribed for notifications. 

    // You can also just validate that the list of clients is expected for this app.  
}

```
> Beachten Sie, dass eine Anwendung die Benachrichtigung maximale Größe für einen bestimmten Client mit der MaxNotificationSize-Eigenschaft abrufen kann.  Alle Daten, die größer als die maximale Größe vom System abgeschnitten wird.
