---
author: msatranjr
title: Bluetooth GATT-Server
description: Dieser Artikel enthält eine Übersicht über Bluetooth Generic Attribute Profile (GATT)-Server für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine Anwendungsfälle.
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b8a941b7b80bd5d34e88798ec586d9c1d52e2887
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6200739"
---
# <a name="bluetooth-gatt-server"></a>Bluetooth GATT-Server


**Wichtige APIs**
- [**Windows.Devices.Bluetooth**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
- [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685)


Dieser Artikel veranschaulicht die Bluetooth-Generic Attribut (GATT)-Server-APIs für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine GATT-Server-Aufgaben: 
- Definieren Sie die unterstützten Dienste
- Veröffentlichen Sie Server, damit er von Remoteclients erkannt werden können
- Werben Sie Unterstützung für den Dienst
- Zum Lesen und Schreiben von Anfragen reagieren
- Senden von Benachrichtigungen an abonnierter clients

## <a name="overview"></a>Übersicht
Windows wird in der Regel in der Clientrolle. Dennoch gibt es entstehen viele Szenarien erfordern Windows, die als Bluetooth LE GATT-Server sowie fungieren. Nahezu alle Szenarien für IoT-Geräte, zusammen mit den meisten plattformübergreifende BLE Kommunikation erfordern Windows Server GATT zu sein. Senden von Benachrichtigungen, in der Nähe tragbare Geräte wurde außerdem ein gängiges Szenario werden, das diese Technologie sowie erfordert.  
> Stellen Sie sicher, dass alle Konzepte in der [GATT-Client-Dokumente](gatt-client.md) löschen, bevor Sie fortfahren.  

Server-Operationen werden um der Dienstanbieter und die GattLocalCharacteristic drehen. Diese beiden Klassen werden benötigt, um zu deklarieren, implementieren und machen eine Hierarchie von Daten auf einem Remotegerät Funktionalität bieten.

## <a name="define-the-supported-services"></a>Definieren Sie die unterstützten Dienste
Ihre app kann einen oder mehrere Dienste deklarieren, die von Windows veröffentlicht wird. Jeder Dienst wird durch eine UUID eindeutig identifiziert. 

### <a name="attributes-and-uuids"></a>Attribute und UUID
Jeder Dienst, Merkmal und Deskriptor definiert durch eigene eindeutige 128-Bit-UUID ist.
> Alle Windows-APIs verwenden den Begriff GUID, aber der Bluetooth-Standard definiert diese als UUIDs. Für unsere Zwecke sind diese beiden Begriffe austauschbar, sodass wir weiterhin verwenden den Begriff UUID. 

Wenn das Attribut standard und von der Bluetooth SIG-definierten definiert ist, wird es auch eine entsprechende kurze 16-Bit-ID haben (z. B. Akku Ebene UUID 0000**2A19**ist-0000-1000-8000-00805F9B34FB und die kurze-ID ist 0x2A19). Dieser standard UUIDs können in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) und [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx)angezeigt werden.

Wenn Ihre app implementieren, wird er eigenen benutzerdefinierten Dienst, eine benutzerdefinierte UUID verfügen, die generiert werden. Dies ist ganz einfach in Visual Studio über Tools -> CreateGuid (Verwendung Option 5 für die abzurufenden im Format "Xxxxxxxx-Xxxx-... Xxxx"). Dieser Uuid kann nun neue lokale Dienste, Merkmale oder Deskriptoren deklarieren verwendet werden.

#### <a name="restricted-services"></a>Eingeschränkte Dienste
Die folgenden Dienste werden vom System reserviert und können zu diesem Zeitpunkt nicht veröffentlicht werden:
1. Gerät Information Service (DIS)
2. Generisches Attribut Profil Service (GATT)
3. Generische Profil-Dienst (Abstand)
4. Human Interface Device Service (HOGP)
5. Scannen von Parametern Service (SCP)

> So erstellen Sie einen blockierten Dienst führt BluetoothError.DisabledByPolicy zurückgegeben werden aus dem Aufruf von CreateAsync zu.

#### <a name="generated-attributes"></a>Erzeugte Attribute
Die folgenden Deskriptoren werden automatisch vom System, basierend auf der GattLocalCharacteristicParameters während der Erstellung des Merkmals bereitgestellt:
1. Merkmal Clientkonfiguration (wenn die Eigenschaft als indicatable oder gemeldet gekennzeichnet ist).
2. Charakteristische Benutzer-Beschreibung (wenn UserDescription Eigenschaft festgelegt ist). Siehe GattLocalCharacteristicParameters.UserDescription-Eigenschaft für Weitere Informationen.
3. Charakteristische Format (einen Deskriptor für jedes Präsentationsformat angegeben).  Siehe GattLocalCharacteristicParameters.PresentationFormats-Eigenschaft für Weitere Informationen.
4. Charakteristische aggregierte Format (sofern mehrere Präsentationsformat angegeben ist).  Weitere Informationen GattLocalCharacteristicParameters.See PresentationFormats-Eigenschaft.
5. Charakteristische erweiterten Eigenschaften (wenn die Eigenschaft mit dem erweiterten Eigenschaften Bit gekennzeichnet ist).

> Der Wert der erweiterte Eigenschaften Deskriptor wird über die ReliableWrites und WritableAuxiliaries charakteristischen Eigenschaften bestimmt.

> Versuchen, einen reservierten Deskriptor zu erstellen, führt zu einer Ausnahme.

> Beachten Sie, dass Broadcast zu diesem Zeitpunkt nicht unterstützt wird.  Angeben der übertragen GattCharacteristicProperty führt zu einer Ausnahme.

### <a name="build-up-the-heirarchy-of-services-and-characteristics"></a>Aufbau der Hierarchie der Dienste und-Merkmale
Die GattServiceProvider dient zum Erstellen und die Definition der Stamm primären Dienst ankündigen.  Jeder Dienst erfordert, dass es sich um eigene ServiceProvider Objekt handelt, die in eine GUID akzeptiert: 

```csharp
GattServiceProviderResult result = await GattServiceProvider.CreateAsync(uuid);

if (result.Error == BluetoothError.Success)
{
    serviceProvider = result.ServiceProvider;
    // 
}
```
> Primäre Dienste sind der obersten Ebene der GATT-Struktur. Primäre Dienste enthalten Merkmale als auch für andere Dienste ('Included' oder sekundäre Services bezeichnet). 

Füllen Sie nun den Dienst mit den erforderlichen Merkmalen und Deskriptoren:

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
Wie oben gezeigt, ist dies ein guter Ort zum Deklarieren Sie Ereignishandler für die Vorgänge an, die jede Merkmal unterstützt.  Um auf Anfragen ordnungsgemäß reagieren zu können, muss eine app definiert, und legen einen Ereignishandler für jeden Anforderungstyp das Attribut unterstützt.  Falls nicht, registrieren Sie einen Handler führt in der Anforderung wird sofort vom System mit *UnlikelyError* abgeschlossen.

### <a name="constant-characteristics"></a>Konstante Merkmale
In manchen Fällen sind charakteristische Werte, die nicht im Verlauf des app Lebensdauer geändert werden. In diesem Fall ist es ratsam, deklarieren Sie eine Konstante Merkmal nicht benötigte app-Aktivierung zu verhindern: 

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
## <a name="publish-the-service"></a>Den Dienst veröffentlichen
Nachdem Sie der Dienst vollständig definiert haben, besteht der nächste Schritt Unterstützung für den Dienst zu veröffentlichen. Dies informiert das Betriebssystem der Dienst beim Durchführen von Remotegeräten einer Dienstermittlung zurückgegeben werden sollen.  Sie haben zwei Eigenschaften - IsDiscoverable und IsConnectable fest:  

```csharp
GattServiceProviderAdvertisingParameters advParameters = new GattServiceProviderAdvertisingParameters
{
    IsDiscoverable = true,
    IsConnectable = true
};
serviceProvider.StartAdvertising(advParameters);
```
- **IsDiscoverable**: Ankündigung der Anzeigename auf remote-Geräte in der Anzeige befanden, das Gerät sichtbar zu machen.
- **IsConnectable**: eine Verbindbare Werbung für den Einsatz in Peripheriegeräte Rolle angekündigt.

> Wenn ein Dienst erkennbar sowohl Connectable ist, wird das System die Uuid-Dienst die Ankündigung Paket hinzufügen.  Es gibt nur 31 Byte im Paket Ankündigung und eine 128-Bit-UUID nimmt 16 von ihnen!

> Beachten Sie, dass bei ein Dienst im Vordergrund veröffentlicht wird, eine Anwendung StopAdvertising beim Aufrufen muss die Anwendung anhält.

## <a name="respond-to-read-and-write-requests"></a>Zum Lesen und Schreiben von Anfragen reagieren
Wie wir oben gesehen haben und die erforderlichen Merkmale deklarieren, haben GattLocalCharacteristics 3 Ereignistypen - ReadRequested, WriteRequested und SubscribedClientsChanged.

### <a name="read"></a>Lesen
Bei einem Remotegerät versucht, einen Wert ein Merkmal lesen (und es ist nicht um einen konstanten Wert), wird das Ereignis ReadRequested aufgerufen. Die Eigenschaft, die der Lesevorgang für sowie Args (mit Informationen über das Remotegerät) aufgerufen wurde, wird an den Delegaten übergeben: 

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
Wenn ein Remotegeräts versucht, einen Wert in ein Merkmal schreiben, wird das Ereignis WriteRequested mit Details zu dem Remotegerät, welche Merkmal zu schreiben und der Wert selbst aufgerufen: 

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
Es gibt 2 Schreibvorgänge - Typen mit und ohne Antwort. Verwenden Sie GattWriteOption (eine Eigenschaft für das GattWriteRequest-Objekt), um herausfinden, welche Art Schreibvorgang, der das Remotegerät ausführt. 

## <a name="send-notifications-to-subscribed-clients"></a>Senden von Benachrichtigungen an abonnierter clients
Die häufigsten GATT-Server-Vorgänge, Benachrichtigungen Durchführen der entscheidende Funktion Senden der Daten an die remote-Geräte. In manchen Fällen sollten Sie zu benachrichtigen, alle abonnierten Clients jedoch Othertimes wünschenswert, welche Geräte zum Senden von des neuen Werts auswählen: 

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
> Beachten Sie, dass eine Anwendung die Benachrichtigung maximale Größe für einen bestimmten Client mit der Eigenschaft MaxNotificationSize abrufen kann.  Alle Daten, die größer als die maximale Größe werden vom System abgeschnitten.
