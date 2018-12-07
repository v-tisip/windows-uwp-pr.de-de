---
title: Bluetooth GATT-Server
description: Dieser Artikel enthält eine Übersicht über Bluetooth Generic Attribute Profile (GATT)-Server für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine verwenden.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 551f8b925ffd56950ba893da7b81fefb4579f558
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8781019"
---
# <a name="bluetooth-gatt-server"></a><span data-ttu-id="97662-104">Bluetooth GATT-Server</span><span class="sxs-lookup"><span data-stu-id="97662-104">Bluetooth GATT Server</span></span>


**<span data-ttu-id="97662-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="97662-105">Important APIs</span></span>**
- [**<span data-ttu-id="97662-106">Windows.Devices.Bluetooth</span><span class="sxs-lookup"><span data-stu-id="97662-106">Windows.Devices.Bluetooth</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
- [**<span data-ttu-id="97662-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span><span class="sxs-lookup"><span data-stu-id="97662-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn297685)


<span data-ttu-id="97662-108">Dieser Artikel veranschaulicht die Bluetooth-Generic Attribut (GATT)-Server-APIs für universelle Windows-Plattform (UWP) apps, zusammen mit Beispielcode für allgemeine GATT-Server-Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="97662-108">This article demonstrates Bluetooth Generic Attribute (GATT) Server APIs for Universal Windows Platform (UWP) apps, along with sample code for common GATT server tasks:</span></span> 
- <span data-ttu-id="97662-109">Definieren Sie die unterstützten Dienste</span><span class="sxs-lookup"><span data-stu-id="97662-109">Define the supported services</span></span>
- <span data-ttu-id="97662-110">Veröffentlichen Sie Server, damit er von remote-Clients erkannt werden können</span><span class="sxs-lookup"><span data-stu-id="97662-110">Publish server so it can be discovered by remote clients</span></span>
- <span data-ttu-id="97662-111">Werben Sie Unterstützung für den Dienst</span><span class="sxs-lookup"><span data-stu-id="97662-111">Advertise support for service</span></span>
- <span data-ttu-id="97662-112">Zum Lesen und Schreiben von Anfragen reagieren</span><span class="sxs-lookup"><span data-stu-id="97662-112">Respond to read and write requests</span></span>
- <span data-ttu-id="97662-113">Senden von Benachrichtigungen an abonnierten clients</span><span class="sxs-lookup"><span data-stu-id="97662-113">Send notifications to subscribed clients</span></span>

## <a name="overview"></a><span data-ttu-id="97662-114">Übersicht</span><span class="sxs-lookup"><span data-stu-id="97662-114">Overview</span></span>
<span data-ttu-id="97662-115">Windows wird in der Regel in der Clientrolle.</span><span class="sxs-lookup"><span data-stu-id="97662-115">Windows usually operates in the client role.</span></span> <span data-ttu-id="97662-116">Dennoch gibt es auftreten viele Szenarien erfordern Windows, die als ein Bluetooth LE GATT-Server sowie fungieren.</span><span class="sxs-lookup"><span data-stu-id="97662-116">Nevertheless, many scenarios arise which require Windows to act as a Bluetooth LE GATT Server as well.</span></span> <span data-ttu-id="97662-117">Nahezu alle Szenarien für IoT-Geräte, zusammen mit den meisten plattformübergreifende BLE Kommunikation erfordern Windows GATT-Server zu sein.</span><span class="sxs-lookup"><span data-stu-id="97662-117">Almost all the scenarios for IoT devices, along with most cross-platform BLE communication will require Windows to be a GATT Server.</span></span> <span data-ttu-id="97662-118">Senden von Benachrichtigungen in der Nähe tragbare Geräte wurde außerdem ein gängiges Szenario werden, das diese Technologie sowie benötigt.</span><span class="sxs-lookup"><span data-stu-id="97662-118">Additionally, sending notifications to nearby wearable devices has become a popular scenario that requires this technology as well.</span></span>  
> <span data-ttu-id="97662-119">Stellen Sie sicher, dass die Konzepte für die in der [Dokumentation der GATT-Client](gatt-client.md) deaktivieren, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="97662-119">Make sure all the concepts in the [GATT Client docs](gatt-client.md) are clear before proceeding.</span></span>  

<span data-ttu-id="97662-120">Server-Vorgänge werden um der Dienstanbieter und die GattLocalCharacteristic drehen.</span><span class="sxs-lookup"><span data-stu-id="97662-120">Server operations will revolve around the Service Provider and the GattLocalCharacteristic.</span></span> <span data-ttu-id="97662-121">Diese beiden Klassen bietet die Funktionen zum Deklarieren, implementieren und eine Hierarchie von Daten auf einem Remotegerät zu machen.</span><span class="sxs-lookup"><span data-stu-id="97662-121">These two classes will provide the functionality needed to declare, implement and expose a hierarchy of data to a remote device.</span></span>

## <a name="define-the-supported-services"></a><span data-ttu-id="97662-122">Definieren Sie die unterstützten Dienste</span><span class="sxs-lookup"><span data-stu-id="97662-122">Define the supported services</span></span>
<span data-ttu-id="97662-123">Ihre app kann einen oder mehrere Dienste deklarieren, die von Windows veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="97662-123">Your app may declare one or more services that will be published by Windows.</span></span> <span data-ttu-id="97662-124">Jeder Dienst wird durch eine UUID eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="97662-124">Each service is uniquely identified by a UUID.</span></span> 

### <a name="attributes-and-uuids"></a><span data-ttu-id="97662-125">Attribute und UUID</span><span class="sxs-lookup"><span data-stu-id="97662-125">Attributes and UUIDs</span></span>
<span data-ttu-id="97662-126">Jeder Dienst, Merkmal und Deskriptor definiert ist durch eigene eindeutige 128-Bit-UUID ist.</span><span class="sxs-lookup"><span data-stu-id="97662-126">Each service, characteristic and descriptor is defined by it's own unique 128-bit UUID.</span></span>
> <span data-ttu-id="97662-127">Alle Windows-APIs verwenden den Begriff GUID, aber der Bluetooth-Standard definiert diese als UUIDs.</span><span class="sxs-lookup"><span data-stu-id="97662-127">The Windows APIs all use the term GUID, but the Bluetooth standard defines these as UUIDs.</span></span> <span data-ttu-id="97662-128">Diese beiden Begriffe sind für unsere Zwecke austauschbar, damit wir verwenden den Begriff UUID fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="97662-128">For our purposes, these two terms are interchangeable so we'll continue to use the term UUID.</span></span> 

<span data-ttu-id="97662-129">Wenn das Attribut standard und definiert durch die Bluetooth SIG definiert ist, wird es auch eine entsprechende kurze 16-Bit-ID haben (z. B. ist der Ebene UUID 0000**2A19**-0000-1000-8000-00805F9B34FB und die kurze-ID ist 0x2A19).</span><span class="sxs-lookup"><span data-stu-id="97662-129">If the attribute is standard and defined by the Bluetooth SIG-defined, it will also have a corresponding 16-bit short ID (e.g. Battery Level UUID  is 0000**2A19**-0000-1000-8000-00805F9B34FB and the short ID is 0x2A19).</span></span> <span data-ttu-id="97662-130">Diese standard UUIDs können in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) und [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx)angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="97662-130">These standard UUIDs can be seen in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) and [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx).</span></span>

<span data-ttu-id="97662-131">Wenn Ihre app implementieren, ist es eigenen benutzerdefinierten Dienst entspricht, eine benutzerdefinierte UUID generiert werden.</span><span class="sxs-lookup"><span data-stu-id="97662-131">If your app is implementing it's own custom service, a custom UUID will have to be generated.</span></span> <span data-ttu-id="97662-132">Dies ist ganz einfach in Visual Studio über Tools -> CreateGuid (mit Option 5 für die abzurufenden im Format "Xxxxxxxx-Xxxx-... Xxxx").</span><span class="sxs-lookup"><span data-stu-id="97662-132">This is easily done in Visual Studio through Tools -> CreateGuid (use option 5 to get it in the "xxxxxxxx-xxxx-...xxxx" format).</span></span> <span data-ttu-id="97662-133">Dieser Uuid kann jetzt auf neue Dienste, Eigenschaften oder Deskriptoren deklarieren verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="97662-133">This uuid can now be used to declare new local services, characteristics or descriptors.</span></span>

#### <a name="restricted-services"></a><span data-ttu-id="97662-134">Eingeschränkte Dienste</span><span class="sxs-lookup"><span data-stu-id="97662-134">Restricted Services</span></span>
<span data-ttu-id="97662-135">Die folgenden Dienste werden vom System reserviert und können zu diesem Zeitpunkt nicht veröffentlicht werden:</span><span class="sxs-lookup"><span data-stu-id="97662-135">The following Services are reserved by the system and cannot be published at this time:</span></span>
1. <span data-ttu-id="97662-136">Gerät Information Service (DIS)</span><span class="sxs-lookup"><span data-stu-id="97662-136">Device Information Service (DIS)</span></span>
2. <span data-ttu-id="97662-137">Generisches Attribut Profil Service (GATT)</span><span class="sxs-lookup"><span data-stu-id="97662-137">Generic Attribute Profile Service (GATT)</span></span>
3. <span data-ttu-id="97662-138">Allgemeine Profil-Dienst (Abstand)</span><span class="sxs-lookup"><span data-stu-id="97662-138">Generic Access Profile Service (GAP)</span></span>
4. <span data-ttu-id="97662-139">Human Interface Device Service (HOGP)</span><span class="sxs-lookup"><span data-stu-id="97662-139">Human Interface Device Service (HOGP)</span></span>
5. <span data-ttu-id="97662-140">Scannen von Parametern Service (SCP)</span><span class="sxs-lookup"><span data-stu-id="97662-140">Scan Parameters Service (SCP)</span></span>

> <span data-ttu-id="97662-141">Versuchen, einen blockierten Dienst zu erstellen, führt zu BluetoothError.DisabledByPolicy aus dem Aufruf von CreateAsync zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="97662-141">Attempting to create a blocked service will result in BluetoothError.DisabledByPolicy being returned from the call to CreateAsync.</span></span>

#### <a name="generated-attributes"></a><span data-ttu-id="97662-142">Generierten Attribute</span><span class="sxs-lookup"><span data-stu-id="97662-142">Generated Attributes</span></span>
<span data-ttu-id="97662-143">Die folgenden Deskriptoren werden automatisch vom System, basierend auf der GattLocalCharacteristicParameters während der Erstellung des Merkmals bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="97662-143">The following descriptors are autogenerated by the system, based on the GattLocalCharacteristicParameters provided during creation of the characteristic:</span></span>
1. <span data-ttu-id="97662-144">Client-Eigenschaft-Konfiguration (wenn die Eigenschaft als indicatable oder gemeldet gekennzeichnet ist).</span><span class="sxs-lookup"><span data-stu-id="97662-144">Client Characteristic Configuration (if the characteristic is marked as indicatable or notifiable).</span></span>
2. <span data-ttu-id="97662-145">Charakteristische Benutzer-Beschreibung (wenn UserDescription Eigenschaft festgelegt ist).</span><span class="sxs-lookup"><span data-stu-id="97662-145">Characteristic User Description (if UserDescription property is set).</span></span> <span data-ttu-id="97662-146">Finden Sie weitere Informationen GattLocalCharacteristicParameters.UserDescription Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="97662-146">See GattLocalCharacteristicParameters.UserDescription property for more info.</span></span>
3. <span data-ttu-id="97662-147">Charakteristische Format (eine Beschreibung für jede Präsentationsformat).</span><span class="sxs-lookup"><span data-stu-id="97662-147">Characteristic Format (one descriptor for each presentation format specified).</span></span>  <span data-ttu-id="97662-148">Finden Sie weitere Informationen GattLocalCharacteristicParameters.PresentationFormats Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="97662-148">See GattLocalCharacteristicParameters.PresentationFormats property for more info.</span></span>
4. <span data-ttu-id="97662-149">Charakteristische aggregierte Format (Wenn mehr als eine Präsentationsformat angegeben ist).</span><span class="sxs-lookup"><span data-stu-id="97662-149">Characteristic Aggregate Format (if more than one presentation format is specified).</span></span>  <span data-ttu-id="97662-150">Weitere Informationen GattLocalCharacteristicParameters.See PresentationFormats-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="97662-150">GattLocalCharacteristicParameters.See PresentationFormats property for more info.</span></span>
5. <span data-ttu-id="97662-151">Über erweiterte Eigenschaften (wenn die Eigenschaft mit dem erweiterten Eigenschaften Bit gekennzeichnet ist).</span><span class="sxs-lookup"><span data-stu-id="97662-151">Characteristic Extended Properties (if the characteristic is marked with the extended properties bit).</span></span>

> <span data-ttu-id="97662-152">Der Wert der Beschreibung erweiterte Eigenschaften wird über die ReliableWrites und WritableAuxiliaries über Eigenschaften bestimmt.</span><span class="sxs-lookup"><span data-stu-id="97662-152">The value of the Extended Properties descriptor is determined via the ReliableWrites and WritableAuxiliaries characteristic properties.</span></span>

> <span data-ttu-id="97662-153">Zum Erstellen einer reservierten führt zu einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="97662-153">Attempting to create a reserved descriptor will result in an exception.</span></span>

> <span data-ttu-id="97662-154">Beachten Sie, dass Broadcast zu diesem Zeitpunkt nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="97662-154">Note that broadcast is not supported at this time.</span></span>  <span data-ttu-id="97662-155">Angeben der GattCharacteristicProperty übertragen, führt zu einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="97662-155">Specifying the Broadcast GattCharacteristicProperty will result in an exception.</span></span>

### <a name="build-up-the-hierarchy-of-services-and-characteristics"></a><span data-ttu-id="97662-156">Um die Hierarchie der Dienste und-Merkmale erstellen</span><span class="sxs-lookup"><span data-stu-id="97662-156">Build up the hierarchy of services and characteristics</span></span>
<span data-ttu-id="97662-157">Die GattServiceProvider dient zum Erstellen und die Definition der Stamm primären Dienst ankündigen.</span><span class="sxs-lookup"><span data-stu-id="97662-157">The GattServiceProvider is used to create and advertise the root primary service definition.</span></span>  <span data-ttu-id="97662-158">Jeder Dienst erfordert, dass es sich um eigene ServiceProvider Objekt handelt, die in eine GUID akzeptiert:</span><span class="sxs-lookup"><span data-stu-id="97662-158">Each service requires it's own ServiceProvider object that takes in a GUID:</span></span> 

```csharp
GattServiceProviderResult result = await GattServiceProvider.CreateAsync(uuid);

if (result.Error == BluetoothError.Success)
{
    serviceProvider = result.ServiceProvider;
    // 
}
```
> <span data-ttu-id="97662-159">Primäre Dienste sind der obersten Ebene der GATT-Struktur.</span><span class="sxs-lookup"><span data-stu-id="97662-159">Primary services are the top level of the GATT tree.</span></span> <span data-ttu-id="97662-160">Primäre Dienste enthalten Merkmale als auch für andere Dienste ("Einschließen" oder sekundäre Services bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="97662-160">Primary services contain characteristics as well as other services (called 'Included' or secondary services).</span></span> 

<span data-ttu-id="97662-161">Füllen Sie nun den Dienst mit den erforderlichen Merkmalen und Deskriptoren:</span><span class="sxs-lookup"><span data-stu-id="97662-161">Now, populate the service with the required characteristics and descriptors:</span></span>

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
<span data-ttu-id="97662-162">Wie oben gezeigt, ist dies ein guter Ort zum Deklarieren Sie Ereignishandler für die Vorgänge an, die jede Eigenschaft unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97662-162">As shown above, this is also a good place to declare event handlers for the operations each characteristic supports.</span></span>  <span data-ttu-id="97662-163">Um korrekt auf Anforderungen zu reagieren, muss eine app definiert, und legen einen Ereignishandler für die einzelnen Anforderung das Attribut unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97662-163">To respond to requests correctly, an app must defined and set an event handler for each request type the attribute supports.</span></span>  <span data-ttu-id="97662-164">Falls nicht, registrieren Sie einen Handler führt in der Anforderung wird sofort durch das System mit *UnlikelyError* abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="97662-164">Failing to register a handler will result in the request being completed immediately with *UnlikelyError* by the system.</span></span>

### <a name="constant-characteristics"></a><span data-ttu-id="97662-165">Konstante Merkmale</span><span class="sxs-lookup"><span data-stu-id="97662-165">Constant characteristics</span></span>
<span data-ttu-id="97662-166">In manchen Fällen sind über Werte, die nicht im Verlauf der Lebensdauer der app geändert werden.</span><span class="sxs-lookup"><span data-stu-id="97662-166">Sometimes, there are characteristic values that will not change during the course of the app's lifetime.</span></span> <span data-ttu-id="97662-167">In diesem Fall ist es ratsam, deklarieren Sie eine Konstante Merkmal nicht benötigte app-Aktivierung zu verhindern:</span><span class="sxs-lookup"><span data-stu-id="97662-167">In that case, it is advisable to declare a constant characteristic to prevent unnecessary app activation:</span></span> 

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
## <a name="publish-the-service"></a><span data-ttu-id="97662-168">Den Dienst veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="97662-168">Publish the service</span></span>
<span data-ttu-id="97662-169">Nachdem Sie der Dienst vollständig definiert haben, besteht der nächste Schritt Unterstützung für den Dienst zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="97662-169">Once the service has been fully defined, the next step is to publish support for the service.</span></span> <span data-ttu-id="97662-170">Dies informiert das Betriebssystem der Dienst zurückgegeben werden sollen, wenn Remotegeräten eine Dienstermittlung ausführen.</span><span class="sxs-lookup"><span data-stu-id="97662-170">This informs the OS that the service should be returned when remote devices perform a service discovery.</span></span>  <span data-ttu-id="97662-171">Sie haben zwei Eigenschaften - IsDiscoverable und IsConnectable fest:</span><span class="sxs-lookup"><span data-stu-id="97662-171">You will have to set two properties - IsDiscoverable and IsConnectable:</span></span>  

```csharp
GattServiceProviderAdvertisingParameters advParameters = new GattServiceProviderAdvertisingParameters
{
    IsDiscoverable = true,
    IsConnectable = true
};
serviceProvider.StartAdvertising(advParameters);
```
- <span data-ttu-id="97662-172">**IsDiscoverable**: Gibt den Anzeigenamen auf remote-Geräte in der Anzeige befanden, indem das Gerät sichtbar.</span><span class="sxs-lookup"><span data-stu-id="97662-172">**IsDiscoverable**: Advertises the friendly name to remote devices in the advertisement, making the device discoverable.</span></span>
- <span data-ttu-id="97662-173">**IsConnectable**: eine Verbindbare Werbung für die Verwendung in Peripheriegeräte Rolle angekündigt.</span><span class="sxs-lookup"><span data-stu-id="97662-173">**IsConnectable**:  Advertises a connectable advertisement for use in peripheral role.</span></span>

> <span data-ttu-id="97662-174">Wenn ein Dienst erkennbar und Connectable ist, wird das System die Uuid-Dienst die Ankündigung Paket hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="97662-174">When a service is both Discoverable and Connectable, the system will add the Service Uuid to the advertisement packet.</span></span>  <span data-ttu-id="97662-175">Es gibt nur 31 Byte im Paket Ankündigung und eine 128-Bit-UUID nimmt 16 von ihnen!</span><span class="sxs-lookup"><span data-stu-id="97662-175">There are only 31 bytes in the Advertisement packet and a 128-bit UUID takes up 16 of them!</span></span>

> <span data-ttu-id="97662-176">Beachten Sie, dass bei ein Dienst im Vordergrund veröffentlicht wird, eine Anwendung StopAdvertising aufgerufen werden muss, wenn die Anwendung anhält.</span><span class="sxs-lookup"><span data-stu-id="97662-176">Note that when a service is published in the foreground, an application must call StopAdvertising when the application suspends.</span></span>

## <a name="respond-to-read-and-write-requests"></a><span data-ttu-id="97662-177">Zum Lesen und Schreiben von Anfragen reagieren</span><span class="sxs-lookup"><span data-stu-id="97662-177">Respond to Read and Write requests</span></span>
<span data-ttu-id="97662-178">Wie wir oben gesehen haben und die erforderlichen Merkmale deklarieren, haben GattLocalCharacteristics 3 Arten von Ereignissen - ReadRequested, WriteRequested und SubscribedClientsChanged.</span><span class="sxs-lookup"><span data-stu-id="97662-178">As we saw above while declaring the required characteristics, GattLocalCharacteristics have 3 types of events - ReadRequested, WriteRequested and SubscribedClientsChanged.</span></span>

### <a name="read"></a><span data-ttu-id="97662-179">Lesen</span><span class="sxs-lookup"><span data-stu-id="97662-179">Read</span></span>
<span data-ttu-id="97662-180">Wenn ein Remotegeräts versucht, einen Wert ein Merkmal lesen (und es ist nicht um einen konstanten Wert), wird das Ereignis ReadRequested aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="97662-180">When a remote device tries to read a value from a characteristic (and it's not a constant value), the ReadRequested event is called.</span></span> <span data-ttu-id="97662-181">Die Eigenschaft, die der Lesevorgang für sowie Args (mit Informationen über das remote-Gerät) aufgerufen wurde, wird an den Delegaten übergeben:</span><span class="sxs-lookup"><span data-stu-id="97662-181">The characteristic the read was called on as well as args (containing information about the remote device) is passed to the delegate:</span></span> 

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

### <a name="write"></a><span data-ttu-id="97662-182">Schreiben</span><span class="sxs-lookup"><span data-stu-id="97662-182">Write</span></span>
<span data-ttu-id="97662-183">Wenn ein Remotegeräts versucht, einen Wert für eine Eigenschaft zu schreiben, wird das Ereignis WriteRequested mit Details zum Remotegerät, welche Eigenschaft zum Schreiben in und der Wert selbst aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="97662-183">When a remote device tries to write a value to a characteristic, the WriteRequested event is called with details about the remote device, which characteristic to write to and the value itself:</span></span> 

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
<span data-ttu-id="97662-184">Es gibt 2 Schreibvorgänge - Typen mit und ohne Antwort.</span><span class="sxs-lookup"><span data-stu-id="97662-184">There are 2 types of Writes - with and without response.</span></span> <span data-ttu-id="97662-185">Verwenden Sie GattWriteOption (eine Eigenschaft für das Objekt GattWriteRequest), um herausfinden, welche Art Schreibvorgang, der das remote-Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="97662-185">Use GattWriteOption (a property on the GattWriteRequest object) to figure out which type of write the remote device is performing.</span></span> 

## <a name="send-notifications-to-subscribed-clients"></a><span data-ttu-id="97662-186">Senden von Benachrichtigungen an abonnierten clients</span><span class="sxs-lookup"><span data-stu-id="97662-186">Send notifications to subscribed clients</span></span>
<span data-ttu-id="97662-187">Die häufigsten GATT-Server-Vorgänge, Benachrichtigungen Durchführen der entscheidende Funktion zum Senden der Daten an die remote-Geräte.</span><span class="sxs-lookup"><span data-stu-id="97662-187">The most frequent of the GATT Server operations, notifications perform the critical function of pushing data to the remote devices.</span></span> <span data-ttu-id="97662-188">In manchen Fällen sollten Sie zu benachrichtigen, alle abonnierten Clients jedoch Othertimes, die Sie ggf. auf welchen Geräten zum Senden von des neuen Werts auswählen:</span><span class="sxs-lookup"><span data-stu-id="97662-188">Sometimes, you'll want to notify all subscribed clients but othertimes you may want to pick which devices to send the new value to:</span></span> 

```csharp
async void NotifyValue()
{
    var writer = new DataWriter();
    // Populate writer with data
    // ...
    
    await notifyCharacteristic.NotifyValueAsync(writer.DetachBuffer());
}
```

<span data-ttu-id="97662-189">Wenn ein neues Gerät für Benachrichtigungen abonniert, ruft das Ereignis SubscribedClientsChanged aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="97662-189">When a new device subscribes for notifications, the SubscribedClientsChanged event gets called:</span></span> 

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
> <span data-ttu-id="97662-190">Beachten Sie, dass eine Anwendung die Benachrichtigung maximale Größe für einen bestimmten Client mit der Eigenschaft MaxNotificationSize abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="97662-190">Note that an application can get the maximum notification size for a particular client with the MaxNotificationSize property.</span></span>  <span data-ttu-id="97662-191">Alle Daten, die größer als die maximale Größe werden vom System abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="97662-191">Any data larger than the maximum size will be truncated by the system.</span></span>
