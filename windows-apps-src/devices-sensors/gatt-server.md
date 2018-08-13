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
# <a name="bluetooth-gatt-server"></a><span data-ttu-id="be6a9-104">Bluetooth-GATT Server</span><span class="sxs-lookup"><span data-stu-id="be6a9-104">Bluetooth GATT Server</span></span>


**<span data-ttu-id="be6a9-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="be6a9-105">Important APIs</span></span>**
- [**<span data-ttu-id="be6a9-106">Windows.Devices.Bluetooth</span><span class="sxs-lookup"><span data-stu-id="be6a9-106">Windows.Devices.Bluetooth</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
- [**<span data-ttu-id="be6a9-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span><span class="sxs-lookup"><span data-stu-id="be6a9-107">Windows.Devices.Bluetooth.GenericAttributeProfile</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn297685)


<span data-ttu-id="be6a9-108">In diesem Artikel wird das Bluetooth generische Attribut (GATT)-Server-APIs für apps universellen Windows-Plattform (UWP), zusammen mit Beispielcode für allgemeine GATT Serveraufgaben veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="be6a9-108">This article demonstrates Bluetooth Generic Attribute (GATT) Server APIs for Universal Windows Platform (UWP) apps, along with sample code for common GATT server tasks:</span></span> 
- <span data-ttu-id="be6a9-109">Definieren der unterstützten Dienste</span><span class="sxs-lookup"><span data-stu-id="be6a9-109">Define the supported services</span></span>
- <span data-ttu-id="be6a9-110">Veröffentlichen Sie Server, damit er von Remoteclients erkannt werden können</span><span class="sxs-lookup"><span data-stu-id="be6a9-110">Publish server so it can be discovered by remote clients</span></span>
- <span data-ttu-id="be6a9-111">Unterstützung für den Dienst kündigen</span><span class="sxs-lookup"><span data-stu-id="be6a9-111">Advertise support for service</span></span>
- <span data-ttu-id="be6a9-112">Antworten Sie zum Lesen und Schreiben von Anfragen</span><span class="sxs-lookup"><span data-stu-id="be6a9-112">Respond to read and write requests</span></span>
- <span data-ttu-id="be6a9-113">Senden von Benachrichtigungen an abonnierten clients</span><span class="sxs-lookup"><span data-stu-id="be6a9-113">Send notifications to subscribed clients</span></span>

## <a name="overview"></a><span data-ttu-id="be6a9-114">Übersicht</span><span class="sxs-lookup"><span data-stu-id="be6a9-114">Overview</span></span>
<span data-ttu-id="be6a9-115">Windows funktioniert in der Regel in der Clientrolle.</span><span class="sxs-lookup"><span data-stu-id="be6a9-115">Windows usually operates in the client role.</span></span> <span data-ttu-id="be6a9-116">Viele Szenarien auftreten dennoch als Bluetooth-LE GATT Server als auch für Windows erforderlich.</span><span class="sxs-lookup"><span data-stu-id="be6a9-116">Nevertheless, many scenarios arise which require Windows to act as a Bluetooth LE GATT Server as well.</span></span> <span data-ttu-id="be6a9-117">Nahezu alle Szenarien für IoT-Geräten zusammen mit den meisten plattformübergreifende BLE Kommunikation erfordern die Windows Server GATT zu sein.</span><span class="sxs-lookup"><span data-stu-id="be6a9-117">Almost all the scenarios for IoT devices, along with most cross-platform BLE communication will require Windows to be a GATT Server.</span></span> <span data-ttu-id="be6a9-118">Darüber hinaus Benachrichtigungen gesendet werden, in der Nähe wearable Geräte ein gängiges Szenario geworden, das diese Technologie sowie erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="be6a9-118">Additionally, sending notifications to nearby wearable devices has become a popular scenario that requires this technology as well.</span></span>  
> <span data-ttu-id="be6a9-119">Stellen Sie sicher, dass alle Konzepte in der [GATT Client Dokumente](gatt-client.md) löschen, bevor Sie fortfahren können.</span><span class="sxs-lookup"><span data-stu-id="be6a9-119">Make sure all the concepts in the [GATT Client docs](gatt-client.md) are clear before proceeding.</span></span>  

<span data-ttu-id="be6a9-120">Server-Vorgänge werden um den Dienstanbieter und den GattLocalCharacteristic drehen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-120">Server operations will revolve around the Service Provider and the GattLocalCharacteristic.</span></span> <span data-ttu-id="be6a9-121">Diese zwei Klassen bietet die Funktionalität zum Deklarieren, implementieren und machen eine Hierarchie von Daten an ein remote-Gerät erforderlich.</span><span class="sxs-lookup"><span data-stu-id="be6a9-121">These two classes will provide the functionality needed to declare, implement and expose a heirarchy of data to a remote device.</span></span>

## <a name="define-the-supported-services"></a><span data-ttu-id="be6a9-122">Definieren der unterstützten Dienste</span><span class="sxs-lookup"><span data-stu-id="be6a9-122">Define the supported services</span></span>
<span data-ttu-id="be6a9-123">Ihre app kann einen oder mehrere Dienste deklarieren, die von Windows veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="be6a9-123">Your app may declare one or more services that will be published by Windows.</span></span> <span data-ttu-id="be6a9-124">Jeder Dienst wird durch eine UUID eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="be6a9-124">Each service is uniquely identified by a UUID.</span></span> 

### <a name="attributes-and-uuids"></a><span data-ttu-id="be6a9-125">Attribute und UUID</span><span class="sxs-lookup"><span data-stu-id="be6a9-125">Attributes and UUIDs</span></span>
<span data-ttu-id="be6a9-126">Jeder Dienst, Merkmale und Deskriptor wird definiert durch eigenen eindeutigen 128-Bit-UUID ist.</span><span class="sxs-lookup"><span data-stu-id="be6a9-126">Each service, characteristic and descriptor is defined by it's own unique 128-bit UUID.</span></span>
> <span data-ttu-id="be6a9-127">Windows-APIs verwenden diesen Begriff GUID, aber der Bluetooth-Standard definiert diese als UUIDs.</span><span class="sxs-lookup"><span data-stu-id="be6a9-127">The Windows APIs all use the term GUID, but the Bluetooth standard defines these as UUIDs.</span></span> <span data-ttu-id="be6a9-128">Für unsere Zwecke sind diese beiden Begriffe austauschbar, damit auch den Begriff UUID verwenden.</span><span class="sxs-lookup"><span data-stu-id="be6a9-128">For our purposes, these two terms are interchangeable so we'll continue to use the term UUID.</span></span> 

<span data-ttu-id="be6a9-129">Wenn das Attribut Standard- und definiert durch die Bluetooth SIG definiert ist, wird es auch eine entsprechende kurze 16-Bit-ID haben (z. B. Batterie Ebene UUID ist 0000**2A19**-0000-1000-8000-00805F9B34FB und die kurzen ID ist 0x2A19).</span><span class="sxs-lookup"><span data-stu-id="be6a9-129">If the attribute is standard and defined by the Bluetooth SIG-defined, it will also have a corresponding 16-bit short ID (e.g. Battery Level UUID  is 0000**2A19**-0000-1000-8000-00805F9B34FB and the short ID is 0x2A19).</span></span> <span data-ttu-id="be6a9-130">Diese standard UUIDs können in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) und [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx)angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="be6a9-130">These standard UUIDs can be seen in [GattServiceUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattserviceuuids.aspx) and [GattCharacteristicUuids](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.bluetooth.genericattributeprofile.gattcharacteristicuuids.aspx).</span></span>

<span data-ttu-id="be6a9-131">Wenn Ihre app implementiert eigenen benutzerdefinierten Dienst, eine benutzerdefinierte UUID generiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-131">If your app is implementing it's own custom service, a custom UUID will have to be generated.</span></span> <span data-ttu-id="be6a9-132">Hierbei handelt es sich einfach in Visual Studio über Tools -> CreateGuid (Verwendung Option 5 für die abzurufenden im Format "Xxxxxxxx-Xxxx-... Xxxx").</span><span class="sxs-lookup"><span data-stu-id="be6a9-132">This is easily done in Visual Studio through Tools -> CreateGuid (use option 5 to get it in the "xxxxxxxx-xxxx-...xxxx" format).</span></span> <span data-ttu-id="be6a9-133">Dieser Uuid kann jetzt verwendet werden, um neue lokale Dienste, Eigenschaften oder Deskriptoren zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="be6a9-133">This uuid can now be used to declare new local services, characteristics or descriptors.</span></span>

#### <a name="restricted-services"></a><span data-ttu-id="be6a9-134">Eingeschränkte Dienste</span><span class="sxs-lookup"><span data-stu-id="be6a9-134">Restricted Services</span></span>
<span data-ttu-id="be6a9-135">Die folgenden Dienste werden vom System reserviert und können zu diesem Zeitpunkt nicht veröffentlicht werden:</span><span class="sxs-lookup"><span data-stu-id="be6a9-135">The following Services are reserved by the system and cannot be published at this time:</span></span>
1. <span data-ttu-id="be6a9-136">Gerät Informationsdienst (DIS)</span><span class="sxs-lookup"><span data-stu-id="be6a9-136">Device Information Service (DIS)</span></span>
2. <span data-ttu-id="be6a9-137">Generische Attribut Profildienst (GATT)</span><span class="sxs-lookup"><span data-stu-id="be6a9-137">Generic Attribute Profile Service (GATT)</span></span>
3. <span data-ttu-id="be6a9-138">Generische Access Profildienst (Abstand)</span><span class="sxs-lookup"><span data-stu-id="be6a9-138">Generic Access Profile Service (GAP)</span></span>
4. <span data-ttu-id="be6a9-139">Human Interface Device Service (HOGP)</span><span class="sxs-lookup"><span data-stu-id="be6a9-139">Human Interface Device Service (HOGP)</span></span>
5. <span data-ttu-id="be6a9-140">Scannen Sie Parameter Service (SCP)</span><span class="sxs-lookup"><span data-stu-id="be6a9-140">Scan Parameters Service (SCP)</span></span>

> <span data-ttu-id="be6a9-141">Versuchen, einen blockierten Dienst zu erstellen, führt zu BluetoothError.DisabledByPolicy aus dem Aufruf von CreateAsync zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="be6a9-141">Attempting to create a blocked service will result in BluetoothError.DisabledByPolicy being returned from the call to CreateAsync.</span></span>

#### <a name="generated-attributes"></a><span data-ttu-id="be6a9-142">Erzeugte Attribute</span><span class="sxs-lookup"><span data-stu-id="be6a9-142">Generated Attributes</span></span>
<span data-ttu-id="be6a9-143">Die folgenden Deskriptoren werden automatisch vom System, basierend auf der GattLocalCharacteristicParameters während der Erstellung der Merkmal bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="be6a9-143">The following descriptors are autogenerated by the system, based on the GattLocalCharacteristicParameters provided during creation of the characteristic:</span></span>
1. <span data-ttu-id="be6a9-144">Merkmal-Clientkonfiguration (falls die Eigenschaft als indicatable oder gemeldet gekennzeichnet ist).</span><span class="sxs-lookup"><span data-stu-id="be6a9-144">Client Characteristic Configuration (if the characteristic is marked as indicatable or notifiable).</span></span>
2. <span data-ttu-id="be6a9-145">Charakteristische Benutzerbeschreibung (falls UserDescription-Eigenschaft festgelegt ist).</span><span class="sxs-lookup"><span data-stu-id="be6a9-145">Characteristic User Description (if UserDescription property is set).</span></span> <span data-ttu-id="be6a9-146">Siehe GattLocalCharacteristicParameters.UserDescription-Eigenschaft für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-146">See GattLocalCharacteristicParameters.UserDescription property for more info.</span></span>
3. <span data-ttu-id="be6a9-147">Charakteristische Format (eine Beschreibung für jede Präsentationsformat angegeben).</span><span class="sxs-lookup"><span data-stu-id="be6a9-147">Characteristic Format (one descriptor for each presentation format specified).</span></span>  <span data-ttu-id="be6a9-148">Siehe GattLocalCharacteristicParameters.PresentationFormats-Eigenschaft für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-148">See GattLocalCharacteristicParameters.PresentationFormats property for more info.</span></span>
4. <span data-ttu-id="be6a9-149">Charakteristische Aggregate-Format (Wenn mehr als eine Präsentationsformat angegeben ist).</span><span class="sxs-lookup"><span data-stu-id="be6a9-149">Characteristic Aggregate Format (if more than one presentation format is specified).</span></span>  <span data-ttu-id="be6a9-150">GattLocalCharacteristicParameters.See PresentationFormats-Eigenschaft für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-150">GattLocalCharacteristicParameters.See PresentationFormats property for more info.</span></span>
5. <span data-ttu-id="be6a9-151">Charakteristische erweiterte Eigenschaften (wenn die Eigenschaft mit dem erweiterten Eigenschaften Bit markiert ist).</span><span class="sxs-lookup"><span data-stu-id="be6a9-151">Characteristic Extended Properties (if the characteristic is marked with the extended properties bit).</span></span>

> <span data-ttu-id="be6a9-152">Der Wert der Deskriptor erweiterte Eigenschaften wird über die charakteristischen Eigenschaften ReliableWrites und WritableAuxiliaries bestimmt.</span><span class="sxs-lookup"><span data-stu-id="be6a9-152">The value of the Extended Properties descriptor is determined via the ReliableWrites and WritableAuxiliaries characteristic properties.</span></span>

> <span data-ttu-id="be6a9-153">Versuch, einen reservierten Deskriptor erstellen führt zu einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="be6a9-153">Attempting to create a reserved descriptor will result in an exception.</span></span>

> <span data-ttu-id="be6a9-154">Beachten Sie, dass Broadcast zu diesem Zeitpunkt nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="be6a9-154">Note that broadcast is not supported at this time.</span></span>  <span data-ttu-id="be6a9-155">Angeben der Broadcast GattCharacteristicProperty führt zu einer Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="be6a9-155">Specifying the Broadcast GattCharacteristicProperty will result in an exception.</span></span>

### <a name="build-up-the-heirarchy-of-services-and-characteristics"></a><span data-ttu-id="be6a9-156">Erstellen Sie die Hierarchie der Dienste und Merkmale</span><span class="sxs-lookup"><span data-stu-id="be6a9-156">Build up the heirarchy of services and characteristics</span></span>
<span data-ttu-id="be6a9-157">Die GattServiceProvider dient zum Erstellen und die primäre Dienstdefinition Stamm ankündigen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-157">The GattServiceProvider is used to create and advertise the root primary service definition.</span></span>  <span data-ttu-id="be6a9-158">Jeder Dienst erfordert, dass sie eigene ServiceProvider-Objekt ist, die in eine GUID akzeptiert:</span><span class="sxs-lookup"><span data-stu-id="be6a9-158">Each service requires it's own ServiceProvider object that takes in a GUID:</span></span> 

```csharp
GattServiceProviderResult result = await GattServiceProvider.CreateAsync(uuid);

if (result.Error == BluetoothError.Success)
{
    serviceProvider = result.ServiceProvider;
    // 
}
```
> <span data-ttu-id="be6a9-159">Primäre Dienste sind die oberste Ebene der Struktur des GATT.</span><span class="sxs-lookup"><span data-stu-id="be6a9-159">Primary services are the top level of the GATT tree.</span></span> <span data-ttu-id="be6a9-160">Primäre Services enthalten Merkmale als auch für andere Dienste (mit der Bezeichnung 'Included' oder sekundären Services).</span><span class="sxs-lookup"><span data-stu-id="be6a9-160">Primary services contain characteristics as well as other services (called 'Included' or secondary services).</span></span> 

<span data-ttu-id="be6a9-161">Nun, füllen Sie den Dienst mit den erforderlichen Merkmale und Deskriptoren:</span><span class="sxs-lookup"><span data-stu-id="be6a9-161">Now, populate the service with the required characteristics and descriptors:</span></span>

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
<span data-ttu-id="be6a9-162">Wie oben gezeigt, ist dies auch eine ausgezeichnete Quelle für den Ereignishandler für die Vorgänge zu deklarieren, jede Eigenschaft unterstützt.</span><span class="sxs-lookup"><span data-stu-id="be6a9-162">As shown above, this is also a good place to declare event handlers for the operations each characteristic supports.</span></span>  <span data-ttu-id="be6a9-163">Um die Anfrage ordnungsgemäß bearbeiten eine app muss definiert und einen Ereignishandler für die einzelnen Anforderung das Attribut unterstützt festgelegt.</span><span class="sxs-lookup"><span data-stu-id="be6a9-163">To respond to requests correctly, an app must defined and set an event handler for each request type the attribute supports.</span></span>  <span data-ttu-id="be6a9-164">Einen Handler registriert, die Fehler aufweisen führt die Anforderung wird unmittelbar vom System mit *UnlikelyError* abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-164">Failing to register a handler will result in the request being completed immediately with *UnlikelyError* by the system.</span></span>

### <a name="constant-characteristics"></a><span data-ttu-id="be6a9-165">Konstante Merkmale</span><span class="sxs-lookup"><span data-stu-id="be6a9-165">Constant characteristics</span></span>
<span data-ttu-id="be6a9-166">In einigen Fällen sind charakteristische Werte, die im Verlauf der Lebensdauer der app nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="be6a9-166">Sometimes, there are characteristic values that will not change during the course of the app's lifetime.</span></span> <span data-ttu-id="be6a9-167">In diesem Fall ist es ratsam, deklarieren Sie ein Merkmal Konstante verhindern Sie unnötige app-Aktivierung:</span><span class="sxs-lookup"><span data-stu-id="be6a9-167">In that case, it is advisable to declare a constant characteristic to prevent unnecessary app activation:</span></span> 

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
## <a name="publish-the-service"></a><span data-ttu-id="be6a9-168">Veröffentlichen Sie den Dienst</span><span class="sxs-lookup"><span data-stu-id="be6a9-168">Publish the service</span></span>
<span data-ttu-id="be6a9-169">Nachdem der Dienst vollständig definiert wurde, besteht der nächste Schritt Unterstützung für den Dienst veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-169">Once the service has been fully defined, the next step is to publish support for the service.</span></span> <span data-ttu-id="be6a9-170">Das Betriebssystem weiß, dass der Dienst zurückgegeben werden sollen, wenn remote-Geräte eine Suche ausführen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-170">This informs the OS that the service should be returned when remote devices perform a service discovery.</span></span>  <span data-ttu-id="be6a9-171">Sie müssen zwei Eigenschaften - IsDiscoverable und IsConnectable festzulegen:</span><span class="sxs-lookup"><span data-stu-id="be6a9-171">You will have to set two properties - IsDiscoverable and IsConnectable:</span></span>  

```csharp
GattServiceProviderAdvertisingParameters advParameters = new GattServiceProviderAdvertisingParameters
{
    IsDiscoverable = true,
    IsConnectable = true
};
serviceProvider.StartAdvertising(advParameters);
```
- <span data-ttu-id="be6a9-172">**IsDiscoverable**: Gibt den Anzeigenamen für remote-Geräte in die Ankündigung, die das Gerät sichtbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-172">**IsDiscoverable**: Advertises the friendly name to remote devices in the advertisement, making the device discoverable.</span></span>
- <span data-ttu-id="be6a9-173">**IsConnectable**: Gibt eine Verbindbare Werbung für die Verwendung in peripherer Rolle bekannt.</span><span class="sxs-lookup"><span data-stu-id="be6a9-173">**IsConnectable**:  Advertises a connectable advertisement for use in peripheral role.</span></span>

> <span data-ttu-id="be6a9-174">Wenn ein Dienst erkennbar und Connectable ist, wird das System den Dienst Uuid das Paket Ankündigung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-174">When a service is both Discoverable and Connectable, the system will add the Service Uuid to the advertisement packet.</span></span>  <span data-ttu-id="be6a9-175">Es gibt nur 31 Bytes im Paket Ankündigung und eine UUID 128-Bit-benötigt 16 davon!</span><span class="sxs-lookup"><span data-stu-id="be6a9-175">There are only 31 bytes in the Advertisement packet and a 128-bit UUID takes up 16 of them!</span></span>

> <span data-ttu-id="be6a9-176">Beachten Sie, dass bei ein Dienst im Vordergrund veröffentlicht wird, eine Anwendung StopAdvertising beim Aufrufen muss die Anwendung angehalten.</span><span class="sxs-lookup"><span data-stu-id="be6a9-176">Note that when a service is published in the foreground, an application must call StopAdvertising when the application suspends.</span></span>

## <a name="respond-to-read-and-write-requests"></a><span data-ttu-id="be6a9-177">Antworten Sie zum Lesen und Schreiben von Anfragen</span><span class="sxs-lookup"><span data-stu-id="be6a9-177">Respond to Read and Write requests</span></span>
<span data-ttu-id="be6a9-178">Wie wir oben gezeigt, während durch die erforderlichen Merkmale deklarieren, haben GattLocalCharacteristics 3 Arten von Ereignissen - ReadRequested, WriteRequested und SubscribedClientsChanged.</span><span class="sxs-lookup"><span data-stu-id="be6a9-178">As we saw above while declaring the required characteristics, GattLocalCharacteristics have 3 types of events - ReadRequested, WriteRequested and SubscribedClientsChanged.</span></span>

### <a name="read"></a><span data-ttu-id="be6a9-179">Lesen</span><span class="sxs-lookup"><span data-stu-id="be6a9-179">Read</span></span>
<span data-ttu-id="be6a9-180">Wenn ein Gerät remote versucht, einen Wert ein Merkmal lesen (und es ist nicht um einen konstanten Wert), wird das ReadRequested-Ereignis aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="be6a9-180">When a remote device tries to read a value from a characteristic (and it's not a constant value), the ReadRequested event is called.</span></span> <span data-ttu-id="be6a9-181">Die Merkmale das Lesen auf sowie Args (mit Informationen zu dem entfernten Gerät) aufgerufen wurde, wird an des Delegaten übergeben:</span><span class="sxs-lookup"><span data-stu-id="be6a9-181">The characteristic the read was called on as well as args (containing information about the remote device) is passed to the delegate:</span></span> 

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

### <a name="write"></a><span data-ttu-id="be6a9-182">Schreiben</span><span class="sxs-lookup"><span data-stu-id="be6a9-182">Write</span></span>
<span data-ttu-id="be6a9-183">Wenn ein Gerät remote versucht, einen Wert in ein Merkmal schreiben, wird das Ereignis WriteRequested mit Details zu dem entfernten Gerät, welche Merkmal geschrieben und den Wert selbst aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="be6a9-183">When a remote device tries to write a value to a characteristic, the WriteRequested event is called with details about the remote device, which characteristic to write to and the value itself:</span></span> 

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
<span data-ttu-id="be6a9-184">2 Schreibvorgänge - Typen mit und ohne Antwort sind vorhanden.</span><span class="sxs-lookup"><span data-stu-id="be6a9-184">There are 2 types of Writes - with and without response.</span></span> <span data-ttu-id="be6a9-185">Verwenden Sie GattWriteOption (eine Eigenschaft für das Objekt GattWriteRequest), um herauszufinden, welche Art von Schreibzugriff auf das entfernte Gerät ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="be6a9-185">Use GattWriteOption (a property on the GattWriteRequest object) to figure out which type of write the remote device is performing.</span></span> 

## <a name="send-notifications-to-subscribed-clients"></a><span data-ttu-id="be6a9-186">Senden von Benachrichtigungen an abonnierten clients</span><span class="sxs-lookup"><span data-stu-id="be6a9-186">Send notifications to subscribed clients</span></span>
<span data-ttu-id="be6a9-187">Häufigste GATT Servervorgänge Benachrichtigungen führen Sie die entscheidende Funktion pushen von Daten für die remote-Geräte.</span><span class="sxs-lookup"><span data-stu-id="be6a9-187">The most frequent of the GATT Server operations, notifications perform the critical function of pushing data to the remote devices.</span></span> <span data-ttu-id="be6a9-188">In einigen Fällen sollten Sie benachrichtigen alle abonnierten Clients jedoch Othertimes, die Sie möglicherweise auf welchen Geräten zum Senden des neuen Werts mit auswählen möchten:</span><span class="sxs-lookup"><span data-stu-id="be6a9-188">Sometimes, you'll want to notify all subscribed clients but othertimes you may want to pick which devices to send the new value to:</span></span> 

```csharp
async void NotifyValue()
{
    var writer = new DataWriter();
    // Populate writer with data
    // ...
    
    await notifyCharacteristic.NotifyValueAsync(writer.DetachBuffer());
}
```

<span data-ttu-id="be6a9-189">Wenn ein neues Gerät für Benachrichtigungen abonniert, ruft das SubscribedClientsChanged-Ereignis aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="be6a9-189">When a new device subscribes for notifications, the SubscribedClientsChanged event gets called:</span></span> 

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
> <span data-ttu-id="be6a9-190">Beachten Sie, dass eine Anwendung die Benachrichtigung maximale Größe für einen bestimmten Client mit der MaxNotificationSize-Eigenschaft abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="be6a9-190">Note that an application can get the maximum notification size for a particular client with the MaxNotificationSize property.</span></span>  <span data-ttu-id="be6a9-191">Alle Daten, die größer als die maximale Größe vom System abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="be6a9-191">Any data larger than the maximum size will be truncated by the system.</span></span>
