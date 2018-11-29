---
title: Bluetooth GATT-Server
description: Dieser Artikel enthält eine Übersicht über Bluetooth Generic Attribute Profile (GATT)-Server für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine Anwendungsfälle.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 551f8b925ffd56950ba893da7b81fefb4579f558
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7987421"
---
# <a name="bluetooth-gatt-server"></a>Bluetooth GATT-Server


**Wichtige APIs**
- [**Windows.Devices.Bluetooth**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
- [**Windows.Devices.Bluetooth.GenericAttributeProfile**](https://msdn.microsoft.com/library/windows/apps/Dn297685)


Dieser Artikel veranschaulicht die Bluetooth-Generic Attribut (GATT)-Server-APIs für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine GATT-Server-Aufgaben: 
- Definieren Sie die unterstützten Dienste
- Veröffentlichen Sie Server, damit er von remote-Clients erkannt werden können
- Unterstützung für den Dienst ankündigen
- Zum Lesen und Schreiben von Anfragen reagieren
- Senden von Benachrichtigungen an abonnierten clients

## <a name="overview"></a>Übersicht
Windows wird in der Regel in der Clientrolle. Viele Szenarien auftreten dennoch die Windows als ein Bluetooth LE GATT Server sowie erfordern. Nahezu alle Szenarien für IoT-Geräte, zusammen mit den meisten plattformübergreifende BLE Kommunikation benötigen Windows ein GATT-Server ist. Senden von Benachrichtigungen in der Nähe tragbare Geräte wurde außerdem ein gängiges Szenario werden, das diese Technologie sowie benötigt.  
> Stellen Sie sicher, dass alle Konzepte in der [GATT-Client-Dokumente](gatt-client.md) löschen, bevor Sie fortfahren.  

Server-Vorgänge werden um der Dienstanbieter und die GattLocalCharacteristic drehen. Diese beiden Klassen bietet die Funktionen zum Deklarieren, implementieren und machen eine Hierarchie von Daten auf einem Remotegerät.

## <a name="define-the-supported-services"></a>Definieren Sie die unterstützten Dienste
Ihre app kann einen oder mehrere Dienste deklarieren, die von Windows veröffentlicht wird. Jeder Dienst wird durch eine UUID eindeutig identifiziert. 

### <a name="attributes-and-uuids"></a>Attribute und UUID
Jeder Dienst, Merkmal und Deskriptor definiert ist es ist mit eigenen eindeutigen 128-Bit-UUID.
> Alle Windows-APIs verwenden den Begriff GUID, aber der Bluetooth-Standard definiert diese als UUIDs. Für unsere Zwecke sind diese beiden Begriffe austauschbar, damit wir verwenden den Begriff UUID fortgesetzt wird. 

Wenn das Attribut standard und von der Bluetooth SIG-definierten definiert ist, es wird verfügen auch über eine entsprechende kurze 16-Bit-ID (Akku Ebene UUID ist z. B. 0000**2A19**-0000-1000-8000-00805F9B34FB und die kurze ID 0x2A19 ist). Diese standard UUIDs können in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) und [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx)angezeigt werden.

Wenn Ihre app implementieren, ist es eigenen benutzerdefinierten Dienst entspricht, eine benutzerdefinierte UUID generiert werden. Hierbei handelt es sich leicht in Visual Studio über Tools -> CreateGuid (mit Option 5 für die abzurufenden im Format "Xxxxxxxx-Xxxx-... Xxxx"). Dieser Uuid kann jetzt auf neue Dienste, Eigenschaften oder Deskriptoren deklarieren verwendet werden.

#### <a name="restricted-services"></a>Eingeschränkte Dienste
Die folgenden Dienste werden vom System reserviert und können zu diesem Zeitpunkt nicht veröffentlicht werden:
1. Gerät Information Service (DIS)
2. Generic Attribute Profile Service (GATT)
3. Generische Profil-Dienst (Abstand)
4. Human Interface Device Service (HOGP)
5. Scannen von Parametern Service (SCP)

> So erstellen Sie einen blockierten Dienst führt BluetoothError.DisabledByPolicy zurückgegeben werden aus dem Aufruf von CreateAsync zu.

#### <a name="generated-attributes"></a>Erzeugte Attribute
Die folgenden Deskriptoren werden automatisch vom System, basierend auf der GattLocalCharacteristicParameters während der Erstellung des Merkmals bereitgestellt:
1. Merkmal Clientkonfiguration (wenn die Eigenschaft als indicatable oder gemeldet gekennzeichnet ist).
2. Charakteristische Benutzer-Beschreibung (wenn UserDescription Eigenschaft festgelegt ist). Siehe GattLocalCharacteristicParameters.UserDescription-Eigenschaft für Weitere Informationen.
3. Charakteristische Format (eine Beschreibung für jedes Präsentationsformat angegeben).  Siehe GattLocalCharacteristicParameters.PresentationFormats-Eigenschaft für Weitere Informationen.
4. Charakteristische aggregierte Format (sofern mehrere Präsentationsformat angegeben ist).  Weitere Informationen GattLocalCharacteristicParameters.See PresentationFormats-Eigenschaft.
5. Charakteristische erweiterten Eigenschaften (wenn die Eigenschaft mit dem erweiterten Eigenschaften Bit markiert ist).

> Der Wert der erweiterte Eigenschaften Deskriptor wird über die Eigenschaft Eigenschaften ReliableWrites und WritableAuxiliaries bestimmt.

> Versuchen, einen reservierten Deskriptor zu erstellen, führt zu einer Ausnahme.

> Beachten Sie, dass Broadcast zu diesem Zeitpunkt nicht unterstützt wird.  Angeben der Übertragung GattCharacteristicProperty führt zu einer Ausnahme.

### <a name="build-up-the-hierarchy-of-services-and-characteristics"></a>Um die Hierarchie der Dienste und-Merkmale erstellen
Die GattServiceProvider dient zum Erstellen und die Definition der Stamm primären Dienst ankündigen.  Jeder Dienst erfordert, dass es sich um eigene ServiceProvider Objekt handelt, die in eine GUID akzeptiert: 

```csharp
GattServiceProviderResult result = await GattServiceProvider.CreateAsync(uuid);

if (result.Error == BluetoothError.Success)
{
    serviceProvider = result.ServiceProvider;
    // 
}
```
> Primäre Dienste sind der obersten Ebene der GATT-Struktur. Primäre Dienste enthalten Merkmale als auch für andere Dienste ("Einschließen" oder sekundäre Services bezeichnet). 

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
Wie oben gezeigt, ist dies ein guter Ort zum Deklarieren Sie Ereignishandler für die Vorgänge an, die jede Merkmal unterstützt.  Um auf Anfragen ordnungsgemäß reagieren zu können, muss eine app definiert, und legen einen Ereignishandler für jeden Anforderungstyp, der das Attribut unterstützt.  Registrieren Sie einen Handler fehlschlagen führt in der Anforderung wird sofort vom System mit *UnlikelyError* abgeschlossen.

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
Nachdem Sie der Dienst vollständig definiert haben, besteht der nächste Schritt Unterstützung für den Dienst zu veröffentlichen. Dies informiert das Betriebssystem der Dienst zurückgegeben werden sollen, wenn Remotegeräten eine Dienstermittlung ausführen.  Sie haben zwei Eigenschaften - IsDiscoverable und IsConnectable fest:  

```csharp
GattServiceProviderAdvertisingParameters advParameters = new GattServiceProviderAdvertisingParameters
{
    IsDiscoverable = true,
    IsConnectable = true
};
serviceProvider.StartAdvertising(advParameters);
```
- **IsDiscoverable**: Ankündigung der Anzeigename auf remote-Geräte in der Anzeige befanden, indem das Gerät sichtbar.
- **IsConnectable**: eine Verbindbare Werbung für den Einsatz in Peripheriegeräte Rolle angekündigt.

> Wenn ein Dienst erkennbar und Connectable ist, wird das System die Uuid-Dienst die Ankündigung Paket hinzufügen.  Es gibt nur 31 Byte im Paket Werbung und eine 128-Bit-UUID benötigt 16 von ihnen!

> Beachten Sie, dass bei ein Dienst im Vordergrund veröffentlicht wird, eine Anwendung StopAdvertising beim Aufrufen muss die Anwendung anhält.

## <a name="respond-to-read-and-write-requests"></a>Zum Lesen und Schreiben von Anfragen reagieren
Wie wir oben gesehen haben, während durch die erforderlichen Merkmale deklarieren, haben GattLocalCharacteristics 3 Arten von Ereignissen - ReadRequested, WriteRequested und SubscribedClientsChanged.

### <a name="read"></a>Lesen
Wenn ein Remotegeräts versucht, einen Wert ein Merkmal lesen (und es ist nicht um einen konstanten Wert), wird das Ereignis ReadRequested aufgerufen. Die Eigenschaft, die der Lesevorgang für sowie Args (mit Informationen über das Remotegerät) aufgerufen wurde, wird an den Delegaten übergeben: 

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
Wenn ein Remotegeräts versucht, einen Wert in ein Merkmal schreiben, wird das Ereignis WriteRequested mit Details zu dem Remotegerät, welche Eigenschaft zum Schreiben in und der Wert selbst aufgerufen: 

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
Es gibt 2 Arten von Schreibvorgängen - mit und ohne Antwort. Verwenden Sie GattWriteOption (eine Eigenschaft für das Objekt GattWriteRequest), um herausfinden, welche Art Schreibvorgang, der das remote-Gerät ausgeführt wird. 

## <a name="send-notifications-to-subscribed-clients"></a>Senden von Benachrichtigungen an abonnierten clients
Die häufigsten GATT-Server-Vorgänge, Benachrichtigungen durchführen die entscheidende Funktion Senden der Daten an die remote-Geräte. In manchen Fällen sollten Sie zu benachrichtigen, alle abonnierten Clients jedoch Othertimes wünschenswert, welche Geräte zum Senden von des neuen Werts auswählen: 

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
