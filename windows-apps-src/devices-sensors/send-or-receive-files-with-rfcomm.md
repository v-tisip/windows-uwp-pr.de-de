---
author: msatranjr
ms.assetid: 5B3A6326-15EE-4618-AA8C-F1C7FB5232FB
title: BluetoothRFCOMM
description: Dieser Artikel enthält eine Übersicht über Bluetooth RFCOMM in UWP-Apps (Universelle Windows-Plattform) sowie Beispielcode zum Senden oder Empfangen einer Datei.
ms.author: misatran
ms.date: 07/19/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- cppwinrt
- cpp
ms.openlocfilehash: 27002fed78356c9a93289d1ccabbada04ea5ed30
ms.sourcegitcommit: 310a4555fedd4246188a98b31f6c094abb33ec60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5126922"
---
# <a name="bluetooth-rfcomm"></a><span data-ttu-id="058f3-104">BluetoothRFCOMM</span><span class="sxs-lookup"><span data-stu-id="058f3-104">Bluetooth RFCOMM</span></span>

**<span data-ttu-id="058f3-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="058f3-105">Important APIs</span></span>**

-   [**<span data-ttu-id="058f3-106">Windows.Devices.Bluetooth</span><span class="sxs-lookup"><span data-stu-id="058f3-106">Windows.Devices.Bluetooth</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn263413)
-   [**<span data-ttu-id="058f3-107">Windows.Devices.Bluetooth.Rfcomm</span><span class="sxs-lookup"><span data-stu-id="058f3-107">Windows.Devices.Bluetooth.Rfcomm</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn263529)

<span data-ttu-id="058f3-108">Dieser Artikel enthält eine Übersicht über Bluetooth RFCOMM in UWP-Apps (Universelle Windows-Plattform) sowie Beispielcode zum Senden oder Empfangen einer Datei.</span><span class="sxs-lookup"><span data-stu-id="058f3-108">This article provides an overview of Bluetooth RFCOMM in Universal Windows Platform (UWP) apps, along with example code on how to send or receive a file..</span></span>

## <a name="overview"></a><span data-ttu-id="058f3-109">Übersicht</span><span class="sxs-lookup"><span data-stu-id="058f3-109">Overview</span></span>

<span data-ttu-id="058f3-110">Die APIs im [**Windows.Devices.Bluetooth.Rfcomm**](https://msdn.microsoft.com/library/windows/apps/Dn263529)-Namespace setzen auf vorhandenen Mustern für „Windows.Devices“ auf, einschließlich [**enumeration**](https://msdn.microsoft.com/library/windows/apps/BR225459) und [**instantiation**](https://msdn.microsoft.com/library/windows/apps/BR225654).</span><span class="sxs-lookup"><span data-stu-id="058f3-110">The APIs in the [**Windows.Devices.Bluetooth.Rfcomm**](https://msdn.microsoft.com/library/windows/apps/Dn263529) namespace build on existing patterns for Windows.Devices, including [**enumeration**](https://msdn.microsoft.com/library/windows/apps/BR225459) and [**instantiation**](https://msdn.microsoft.com/library/windows/apps/BR225654).</span></span> <span data-ttu-id="058f3-111">Beim Lesen und Schreiben von Daten werden die Vorteile von [**etablierten Datenstrommustern**](https://msdn.microsoft.com/library/windows/apps/BR208119) und Objekten in [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/BR241791) genutzt.</span><span class="sxs-lookup"><span data-stu-id="058f3-111">Data reading and writing is designed to take advantage of [**established data stream patterns**](https://msdn.microsoft.com/library/windows/apps/BR208119) and objects in [**Windows.Storage.Streams**](https://msdn.microsoft.com/library/windows/apps/BR241791).</span></span> <span data-ttu-id="058f3-112">SDP-Attribute (Service Discovery Protocol) besitzen einen Wert und einen erwarteten Typ.</span><span class="sxs-lookup"><span data-stu-id="058f3-112">Service Discovery Protocol (SDP) attributes have a value and an expected type.</span></span> <span data-ttu-id="058f3-113">Einige gängige Geräte verfügen jedoch über fehlerhafte Implementierungen von SDP-Attributen, bei denen der Wert nicht dem erwarteten Typ entspricht.</span><span class="sxs-lookup"><span data-stu-id="058f3-113">However, some common devices have faulty implementations of SDP attributes where the value is not of the expected type.</span></span> <span data-ttu-id="058f3-114">Darüber hinaus sind für viele Verwendungen von RFCOMM zusätzliche SDP-Attribute überhaupt nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="058f3-114">Additionally, many usages of RFCOMM do not require additional SDP attributes at all.</span></span> <span data-ttu-id="058f3-115">Daher bietet diese API Zugriff auf die nicht analysierten SDP-Daten, aus denen Entwickler die erforderlichen Informationen abrufen können.</span><span class="sxs-lookup"><span data-stu-id="058f3-115">For these reasons, this API offers access to the unparsed SDP data, from which developers can obtain the information they need.</span></span>

<span data-ttu-id="058f3-116">Die RFCOMM-APIs stützen sich auf das Konzept der Dienst-IDs (Service Identifiers, SIDs).</span><span class="sxs-lookup"><span data-stu-id="058f3-116">The RFCOMM APIs use the concept of service identifiers.</span></span> <span data-ttu-id="058f3-117">Obwohl es sich bei einer SID lediglich um eine 128-Bit-GUID handelt, wird sie im Allgemeinen als 16-Bit-Ganzzahl oder als 32-Bit-Ganzzahl angegeben.</span><span class="sxs-lookup"><span data-stu-id="058f3-117">Although a service identifier is simply a 128-bit GUID, it is also commonly specified as either a 16- or 32-bit integer.</span></span> <span data-ttu-id="058f3-118">Die RFCOMM-API bietet einen Wrapper für SIDs, der deren Angabe und Verwendung als 128-Bit-GUIDs und als 32-Bit-Ganzzahlen zulässt, jedoch keine 16-Bit-Ganzzahlen bietet.</span><span class="sxs-lookup"><span data-stu-id="058f3-118">The RFCOMM API offers a wrapper for service identifiers that allows them be specified and consumed as 128-bit GUIDs as well as 32-bit integers but does not offer 16-bit integers.</span></span> <span data-ttu-id="058f3-119">Dies stellt für die API kein Problem dar, da in den Sprachen automatisch eine Erweiterung auf eine 32-Bit-Ganzzahl erfolgt und die ID immer noch ordnungsgemäß generiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="058f3-119">This is not an issue for the API because languages will automatically upsize to a 32-bit integer and the identifier can still be correctly generated.</span></span>

<span data-ttu-id="058f3-120">Apps können mehrere Schritte umfassende Gerätevorgänge als Hintergrundaufgabe ausführen, sodass sie bis zum Abschluss ausgeführt werden können, selbst wenn die App in den Hintergrund verschoben und ausgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="058f3-120">Apps can perform multi-step device operations in a background task so that they can run to completion even if the app is moved to the background and suspended.</span></span> <span data-ttu-id="058f3-121">Dies ermöglicht zuverlässige Gerätewartungen, z.B. Änderungen an dauerhaften Einstellungen oder Firmware sowie Synchronisierung von Inhalten, ohne dass der Benutzer in der Zwischenzeit eine Statusanzeige beobachten muss.</span><span class="sxs-lookup"><span data-stu-id="058f3-121">This allows for reliable device servicing such as changes to persistent settings or firmware, and content synchronization, without requiring the user to sit and watch a progress bar.</span></span> <span data-ttu-id="058f3-122">Verwenden Sie den [**DeviceServicingTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn297315) für Gerätewartungen und den [**DeviceUseTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn297337) für die Synchronisierung von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="058f3-122">Use the [**DeviceServicingTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn297315) for device servicing and the [**DeviceUseTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn297337) for content synchronization.</span></span> <span data-ttu-id="058f3-123">Beachten Sie Folgendes: Diese Hintergrundaufgaben können den Zeitraum begrenzen, in dem die App im Hintergrund ausgeführt werden kann, und sie sollen nicht den zeitlich unbefristeten Betrieb oder eine unendliche Synchronisierung ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="058f3-123">Note that these background tasks constrain the amount of time the app can run in the background, and are not intended to allow indefinite operation or infinite synchronization.</span></span>

<span data-ttu-id="058f3-124">Ein vollständiges Codebeispiel mit Details über den RFCOMM-Vorgang finden Sie im [**Bluetooth Rfcomm Chat-Beispiel**](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) oder auf Github.</span><span class="sxs-lookup"><span data-stu-id="058f3-124">For a complete code sample that details RFCOMM operation, see the [**Bluetooth Rfcomm Chat Sample**](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) on Github.</span></span>  

## <a name="send-a-file-as-a-client"></a><span data-ttu-id="058f3-125">Senden einer Datei als Client</span><span class="sxs-lookup"><span data-stu-id="058f3-125">Send a file as a client</span></span>

<span data-ttu-id="058f3-126">Beim Senden einer Datei besteht das einfachste App-Szenario darin, auf Basis eines gewünschten Dienstes eine Verbindung mit einem gekoppelten Gerät herzustellen.</span><span class="sxs-lookup"><span data-stu-id="058f3-126">When sending a file, the most basic scenario is to connect to a paired device based on a desired service.</span></span> <span data-ttu-id="058f3-127">Dies umfasst die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="058f3-127">This involves the following steps:</span></span>

-   <span data-ttu-id="058f3-128">Verwenden Sie die **RfcommDeviceService.GetDeviceSelector\***-Funktionen, um eine AQS-Abfrage zu generieren, die verwendet werden kann, um gekoppelte Geräteinstanzen des gewünschten Diensts aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="058f3-128">Use the **RfcommDeviceService.GetDeviceSelector\*** functions to help generate an AQS query that can be used to enumerated paired device instances of the desired service.</span></span>
-   <span data-ttu-id="058f3-129">Wählen Sie ein aufgelistetes Gerät aus, erstellen Sie einen [**RfcommDeviceService**](https://msdn.microsoft.com/library/windows/apps/Dn263463), und lesen Sie bei Bedarf die SDP-Attribute (mit [**established data helpers**](https://msdn.microsoft.com/library/windows/apps/BR208119) zum Analysieren der Attributdaten).</span><span class="sxs-lookup"><span data-stu-id="058f3-129">Pick an enumerated device, create an [**RfcommDeviceService**](https://msdn.microsoft.com/library/windows/apps/Dn263463), and read the SDP attributes as needed (using [**established data helpers**](https://msdn.microsoft.com/library/windows/apps/BR208119) to parse the attribute's data).</span></span>
-   <span data-ttu-id="058f3-130">Erstellen Sie einen Socket, und verwenden die Eigenschaften [**RfcommDeviceService.ConnectionHostName**](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.rfcomm.rfcommdeviceservice.connectionhostname.aspx) und [**RfcommDeviceService.ConnectionServiceName**](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.rfcomm.rfcommdeviceservice.connectionservicename.aspx) für [**StreamSocket.ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/Hh701504) und für den Remotegerätedienst mit den entsprechenden Parametern.</span><span class="sxs-lookup"><span data-stu-id="058f3-130">Create a socket and use the [**RfcommDeviceService.ConnectionHostName**](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.rfcomm.rfcommdeviceservice.connectionhostname.aspx) and [**RfcommDeviceService.ConnectionServiceName**](https://msdn.microsoft.com/library/windows/apps/windows.devices.bluetooth.rfcomm.rfcommdeviceservice.connectionservicename.aspx) properties to [**StreamSocket.ConnectAsync**](https://msdn.microsoft.com/library/windows/apps/Hh701504) to the remote device service with the appropriate parameters.</span></span>
-   <span data-ttu-id="058f3-131">Folgen die etablierten Datenstrommuster, um Datenblöcke der Datei auszulesen und sie über [**StreamSocket.OutputStream**](https://msdn.microsoft.com/library/windows/apps/BR226920) an das Gerät zu senden.</span><span class="sxs-lookup"><span data-stu-id="058f3-131">Follow established data stream patterns to read chunks of data from the file and send it on the socket's [**StreamSocket.OutputStream**](https://msdn.microsoft.com/library/windows/apps/BR226920) to the device.</span></span>

```csharp
Windows.Devices.Bluetooth.Rfcomm.RfcommDeviceService _service;
Windows.Networking.Sockets.StreamSocket _socket;

async void Initialize()
{
    // Enumerate devices with the object push service
    var services =
        await Windows.Devices.Enumeration.DeviceInformation.FindAllAsync(
            RfcommDeviceService.GetDeviceSelector(
                RfcommServiceId.ObexObjectPush));

    if (services.Count > 0)
    {
        // Initialize the target Bluetooth BR device
        var service = await RfcommDeviceService.FromIdAsync(services[0].Id);

        // Check that the service meets this App's minimum requirement
        if (SupportsProtection(service) && IsCompatibleVersion(service))
        {
            _service = service;

            // Create a socket and connect to the target
            _socket = new StreamSocket();
            await _socket.ConnectAsync(
                _service.ConnectionHostName,
                _service.ConnectionServiceName,
                SocketProtectionLevel
                    .BluetoothEncryptionAllowNullAuthentication);

            // The socket is connected. At this point the App can wait for
            // the user to take some action, e.g. click a button to send a
            // file to the device, which could invoke the Picker and then
            // send the picked file. The transfer itself would use the
            // Sockets API and not the Rfcomm API, and so is omitted here for
            // brevity.
        }
    }
}

// This App requires a connection that is encrypted but does not care about
// whether it's authenticated.
bool SupportsProtection(RfcommDeviceService service)
{
    switch (service.ProtectionLevel)
    {
    case SocketProtectionLevel.PlainSocket:
        if ((service.MaxProtectionLevel == SocketProtectionLevel
                .BluetoothEncryptionWithAuthentication)
            || (service.MaxProtectionLevel == SocketProtectionLevel
                .BluetoothEncryptionAllowNullAuthentication))
        {
            // The connection can be upgraded when opening the socket so the
            // App may offer UI here to notify the user that Windows may
            // prompt for a PIN exchange.
            return true;
        }
        else
        {
            // The connection cannot be upgraded so an App may offer UI here
            // to explain why a connection won't be made.
            return false;
        }
    case SocketProtectionLevel.BluetoothEncryptionWithAuthentication:
        return true;
    case SocketProtectionLevel.BluetoothEncryptionAllowNullAuthentication:
        return true;
    }
    return false;
}

// This App relies on CRC32 checking available in version 2.0 of the service.
const uint SERVICE_VERSION_ATTRIBUTE_ID = 0x0300;
const byte SERVICE_VERSION_ATTRIBUTE_TYPE = 0x0A;   // UINT32
const uint MINIMUM_SERVICE_VERSION = 200;
bool IsCompatibleVersion(RfcommDeviceService service)
{
    var attributes = await service.GetSdpRawAttributesAsync(
        BluetothCacheMode.Uncached);
    var attribute = attributes[SERVICE_VERSION_ATTRIBUTE_ID];
    var reader = DataReader.FromBuffer(attribute);

    // The first byte contains the attribute's type
    byte attributeType = reader.ReadByte();
    if (attributeType == SERVICE_VERSION_ATTRIBUTE_TYPE)
    {
        // The remainder is the data
        uint version = reader.ReadUInt32();
        return version >= MINIMUM_SERVICE_VERSION;
    }
}
```

```cppwinrt
...
#include <winrt/Windows.Devices.Bluetooth.Rfcomm.h>
#include <winrt/Windows.Devices.Enumeration.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
...
Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService m_service{ nullptr };
Windows::Networking::Sockets::StreamSocket m_socket;

Windows::Foundation::IAsyncAction Initialize()
{
    // Enumerate devices with the object push service.
    Windows::Devices::Enumeration::DeviceInformationCollection services{
        co_await Windows::Devices::Enumeration::DeviceInformation::FindAllAsync(
            Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService::GetDeviceSelector(
                Windows::Devices::Bluetooth::Rfcomm::RfcommServiceId::ObexObjectPush())) };

    if (services.Size() > 0)
    {
        // Initialize the target Bluetooth BR device.
        Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService service{
            co_await Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService::FromIdAsync(services.GetAt(0).Id()) };

        // Check that the service meets this App's minimum
        // requirement
        if (SupportsProtection(service)
            && co_await IsCompatibleVersion(service))
        {
            m_service = service;

            // Create a socket and connect to the target
            co_await m_socket.ConnectAsync(
                m_service.ConnectionHostName(),
                m_service.ConnectionServiceName(),
                Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionAllowNullAuthentication);

            // The socket is connected. At this point the App can
            // wait for the user to take some action, e.g. click
            // a button to send a file to the device, which could
            // invoke the Picker and then send the picked file.
            // The transfer itself would use the Sockets API and
            // not the Rfcomm API, and so is omitted here for
            //brevity.
        }
    }
}

// This App requires a connection that is encrypted but does not care about
// whether it's authenticated.
bool SupportsProtection(Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService const& service)
{
    switch (service.ProtectionLevel())
    {
    case Windows::Networking::Sockets::SocketProtectionLevel::PlainSocket:
        if ((service.MaxProtectionLevel() == Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionWithAuthentication)
            || (service.MaxProtectionLevel() == Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionAllowNullAuthentication))
        {
            // The connection can be upgraded when opening the socket so the
            // App may offer UI here to notify the user that Windows may
            // prompt for a PIN exchange.
            return true;
        }
        else
        {
            // The connection cannot be upgraded so an App may offer UI here
            // to explain why a connection won't be made.
            return false;
        }
    case Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionWithAuthentication:
        return true;
    case Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionAllowNullAuthentication:
        return true;
    }
    return false;
}

// This application relies on CRC32 checking available in version 2.0 of the service.
const uint32_t SERVICE_VERSION_ATTRIBUTE_ID{ 0x0300 };
const byte SERVICE_VERSION_ATTRIBUTE_TYPE{ 0x0A }; // UINT32.
const uint32_t MINIMUM_SERVICE_VERSION{ 200 };

Windows::Foundation::IAsyncOperation<bool> IsCompatibleVersion(Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService const& service)
{
    auto attributes{
        co_await service.GetSdpRawAttributesAsync(Windows::Devices::Bluetooth::BluetoothCacheMode::Uncached) };

    auto attribute{ attributes.Lookup(SERVICE_VERSION_ATTRIBUTE_ID) };
    auto reader{ Windows::Storage::Streams::DataReader::FromBuffer(attribute) };

    // The first byte contains the attribute's type.
    byte attributeType{ reader.ReadByte() };
    if (attributeType == SERVICE_VERSION_ATTRIBUTE_TYPE)
    {
        // The remainder is the data
        uint32_t version{ reader.ReadUInt32() };
        co_return (version >= MINIMUM_SERVICE_VERSION);
    }
}
...
```

```cpp
Windows::Devices::Bluetooth::Rfcomm::RfcommDeviceService^ _service;
Windows::Networking::Sockets::StreamSocket^ _socket;

void Initialize()
{
    // Enumerate devices with the object push service
    create_task(
        Windows::Devices::Enumeration::DeviceInformation::FindAllAsync(
            RfcommDeviceService::GetDeviceSelector(
                RfcommServiceId::ObexObjectPush)))
    .then([](DeviceInformationCollection^ services)
    {
        if (services->Size > 0)
        {
            // Initialize the target Bluetooth BR device
            create_task(RfcommDeviceService::FromIdAsync(services[0]->Id))
            .then([](RfcommDeviceService^ service)
            {
                // Check that the service meets this App's minimum
                // requirement
                if (SupportsProtection(service)
                    && IsCompatibleVersion(service))
                {
                    _service = service;

                    // Create a socket and connect to the target
                    _socket = ref new StreamSocket();
                    create_task(_socket->ConnectAsync(
                        _service->ConnectionHostName,
                        _service->ConnectionServiceName,
                        SocketProtectionLevel
                            ::BluetoothEncryptionAllowNullAuthentication)
                    .then([](void)
                    {
                        // The socket is connected. At this point the App can
                        // wait for the user to take some action, e.g. click
                        // a button to send a file to the device, which could
                        // invoke the Picker and then send the picked file.
                        // The transfer itself would use the Sockets API and
                        // not the Rfcomm API, and so is omitted here for
                        //brevity.
                    });
                }
            });
        }
    });
}

// This App requires a connection that is encrypted but does not care about
// whether it's authenticated.
bool SupportsProtection(RfcommDeviceService^ service)
{
    switch (service->ProtectionLevel)
    {
    case SocketProtectionLevel->PlainSocket:
        if ((service->MaxProtectionLevel == SocketProtectionLevel
                ::BluetoothEncryptionWithAuthentication)
            || (service->MaxProtectionLevel == SocketProtectionLevel
                ::BluetoothEncryptionAllowNullAuthentication))
        {
            // The connection can be upgraded when opening the socket so the
            // App may offer UI here to notify the user that Windows may
            // prompt for a PIN exchange.
            return true;
        }
        else
        {
            // The connection cannot be upgraded so an App may offer UI here
            // to explain why a connection won't be made.
            return false;
        }
    case SocketProtectionLevel::BluetoothEncryptionWithAuthentication:
        return true;
    case SocketProtectionLevel::BluetoothEncryptionAllowNullAuthentication:
        return true;
    }
    return false;
}

// This App relies on CRC32 checking available in version 2.0 of the service.
const uint SERVICE_VERSION_ATTRIBUTE_ID = 0x0300;
const byte SERVICE_VERSION_ATTRIBUTE_TYPE = 0x0A;   // UINT32
const uint MINIMUM_SERVICE_VERSION = 200;
bool IsCompatibleVersion(RfcommDeviceService^ service)
{
    auto attributes = await service->GetSdpRawAttributesAsync(
        BluetoothCacheMode::Uncached);
    auto attribute = attributes[SERVICE_VERSION_ATTRIBUTE_ID];
    auto reader = DataReader.FromBuffer(attribute);

    // The first byte contains the attribute's type
    byte attributeType = reader->ReadByte();
    if (attributeType == SERVICE_VERSION_ATTRIBUTE_TYPE)
    {
        // The remainder is the data
        uint version = reader->ReadUInt32();
        return version >= MINIMUM_SERVICE_VERSION;
    }
}
```

## <a name="receive-file-as-a-server"></a><span data-ttu-id="058f3-132">Empfangen einer Datei als Server</span><span class="sxs-lookup"><span data-stu-id="058f3-132">Receive File as a Server</span></span>

<span data-ttu-id="058f3-133">Ein weiteres allgemeines RFCOMM-App-Szenario besteht darin, einen Dienst auf einem PC zu hosten und ihn anderen Geräten zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="058f3-133">Another common RFCOMM App scenario is to host a service on the PC and expose it for other devices.</span></span>

-   <span data-ttu-id="058f3-134">Erstellen eines [**RfcommServiceProvider**](https://msdn.microsoft.com/library/windows/apps/Dn263511) zum Ankündigen des gewünschten Diensts.</span><span class="sxs-lookup"><span data-stu-id="058f3-134">Create a [**RfcommServiceProvider**](https://msdn.microsoft.com/library/windows/apps/Dn263511) to advertise the desired service.</span></span>
-   <span data-ttu-id="058f3-135">Legen Sie die SDP-Attribute nach Bedarf fest (mit [**verbreiteten Datenhilfsfunktionen**](https://msdn.microsoft.com/library/windows/apps/BR208119) zum Erstellen der Attributdaten), und beginnen Sie damit, die SDP-Datensätze anzukündigen, damit sie andere Geräte abrufen können.</span><span class="sxs-lookup"><span data-stu-id="058f3-135">Set the SDP attributes as needed (using [**established data helpers**](https://msdn.microsoft.com/library/windows/apps/BR208119) to generate the attribute’s Data) and starts advertising the SDP records for other devices to retrieve.</span></span>
-   <span data-ttu-id="058f3-136">Zur Herstellung einer Verbindung zu einem Clientgerät erstellen Sie einen Socketlistener, um mit dem Überwachen eingehender Verbindungsanforderungen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="058f3-136">To connect to a client device, create a socket listener to start listening for incoming connection requests.</span></span>
-   <span data-ttu-id="058f3-137">Sobald eine Verbindung hergestellt ist, können Sie das verbundene Socket zur späteren Verarbeitung speichern.</span><span class="sxs-lookup"><span data-stu-id="058f3-137">When a connection is received, store the connected socket for later processing.</span></span>
-   <span data-ttu-id="058f3-138">Folgen Sie etablierten Datenstrommustern, um Datenblöcke aus dem InputStream des Sockets zu lesen und in einer Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="058f3-138">Follow established data stream patterns to read chunks of data from the socket's InputStream and save it to a file.</span></span>

<span data-ttu-id="058f3-139">Um einen RFCOMM-Dienst im Hintergrund beizubehalten, verwenden Sie [**RfcommConnectionTrigger**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.rfcommconnectiontrigger.aspx).</span><span class="sxs-lookup"><span data-stu-id="058f3-139">In order to persist an RFCOMM service in the background, use the [**RfcommConnectionTrigger**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.rfcommconnectiontrigger.aspx).</span></span> <span data-ttu-id="058f3-140">Die Hintergrundaufgabe wird bei der Verbindungsherstellung mit dem Dienst ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="058f3-140">The background task is triggered on connection to the service.</span></span> <span data-ttu-id="058f3-141">Der Entwickler erhält einen Handle für den Socket in der Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="058f3-141">The developer receives a handle to the socket in the background task.</span></span> <span data-ttu-id="058f3-142">Die Hintergrundaufgabe wird wird lange ausgeführt und so lange beibehalten, wie der Socket verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="058f3-142">The background task is long running and persists for as long as the socket is in use.</span></span>    

```csharp
Windows.Devices.Bluetooth.Rfcomm.RfcommServiceProvider _provider;

async void Initialize()
{
    // Initialize the provider for the hosted RFCOMM service
    _provider = await Windows.Devices.Bluetooth.
        RfcommServiceProvider.CreateAsync(RfcommServiceId.ObexObjectPush);

    // Create a listener for this service and start listening
    StreamSocketListener listener = new StreamSocketListener();
    listener.ConnectionReceived += OnConnectionReceived;
    await listener.BindServiceNameAsync(
        _provider.ServiceId.AsString(),
        SocketProtectionLevel
            .BluetoothEncryptionAllowNullAuthentication);

    // Set the SDP attributes and start advertising
    InitializeServiceSdpAttributes(_provider);
    _provider.StartAdvertising(listener);
}

const uint SERVICE_VERSION_ATTRIBUTE_ID = 0x0300;
const byte SERVICE_VERSION_ATTRIBUTE_TYPE = 0x0A;   // UINT32
const uint SERVICE_VERSION = 200;
void InitializeServiceSdpAttributes(RfcommServiceProvider provider)
{
    auto writer = new Windows.Storage.Streams.DataWriter();

    // First write the attribute type
    writer.WriteByte(SERVICE_VERSION_ATTRIBUTE_TYPE);
    // Then write the data
    writer.WriteUInt32(SERVICE_VERSION);

    auto data = writer.DetachBuffer();
    provider.SdpRawAttributes.Add(SERVICE_VERSION_ATTRIBUTE_ID, data);
}

void OnConnectionReceived(
    StreamSocketListener listener,
    StreamSocketListenerConnectionReceivedEventArgs args)
{
    // Stop advertising/listening so that we're only serving one client
    _provider.StopAdvertising();
    await listener.Close();
    _socket = args.Socket;

    // The client socket is connected. At this point the App can wait for
    // the user to take some action, e.g. click a button to receive a file
    // from the device, which could invoke the Picker and then save the
    // received file to the picked location. The transfer itself would use
    // the Sockets API and not the Rfcomm API, and so is omitted here for
    // brevity.
}
```

```cppwinrt
...
#include <winrt/Windows.Devices.Bluetooth.Rfcomm.h>
#include <winrt/Windows.Networking.Sockets.h>
#include <winrt/Windows.Storage.Streams.h>
...
Windows::Devices::Bluetooth::Rfcomm::RfcommServiceProvider m_provider{ nullptr };
Windows::Networking::Sockets::StreamSocket m_socket;

Windows::Foundation::IAsyncAction Initialize()
{
    // Initialize the provider for the hosted RFCOMM service.
    auto provider{ co_await Windows::Devices::Bluetooth::Rfcomm::RfcommServiceProvider::CreateAsync(
        Windows::Devices::Bluetooth::Rfcomm::RfcommServiceId::ObexObjectPush()) };

    m_provider = provider;

    // Create a listener for this service and start listening.
    Windows::Networking::Sockets::StreamSocketListener listener;
    listener.ConnectionReceived({ this, &MainPage::OnConnectionReceived });

    co_await listener.BindServiceNameAsync(m_provider.ServiceId().AsString(),
        Windows::Networking::Sockets::SocketProtectionLevel::BluetoothEncryptionAllowNullAuthentication);

    // Set the SDP attributes and start advertising
    InitializeServiceSdpAttributes();
    m_provider.StartAdvertising(listener);
}

const uint32_t SERVICE_VERSION_ATTRIBUTE_ID{ 0x0300 };
const byte SERVICE_VERSION_ATTRIBUTE_TYPE{ 0x0A };   // UINT32.
const uint32_t SERVICE_VERSION{ 200 };

void InitializeServiceSdpAttributes()
{
    Windows::Storage::Streams::DataWriter writer;

    // First write the attribute type
    writer.WriteByte(SERVICE_VERSION_ATTRIBUTE_TYPE);
    // Then write the data
    writer.WriteUInt32(SERVICE_VERSION);

    auto data{ writer.DetachBuffer() };
    m_provider.SdpRawAttributes().Insert(SERVICE_VERSION_ATTRIBUTE_ID, data);
}

void OnConnectionReceived(
    Windows::Networking::Sockets::StreamSocketListener const& listener,
    Windows::Networking::Sockets::StreamSocketListenerConnectionReceivedEventArgs const& args)
{
    // Stop advertising/listening so that we're only serving one client
    m_provider.StopAdvertising();
    listener.Close();
    m_socket = args.Socket();

    // The client socket is connected. At this point the application can wait for
    // the user to take some action, e.g. click a button to receive a
    // file from the device, which could invoke the Picker and then save
    // the received file to the picked location. The transfer itself
    // would use the Sockets API and not the Rfcomm API, and so is
    // omitted here for brevity.
}
...
```

```cpp
Windows::Devices::Bluetooth::Rfcomm::RfcommServiceProvider^ _provider;
Windows::Networking::Sockets::StreamSocket^ _socket;

void Initialize()
{
    // Initialize the provider for the hosted RFCOMM service
    create_task(Windows::Devices::Bluetooth.
        RfcommServiceProvider::CreateAsync(
            RfcommServiceId::ObexObjectPush))
    .then([](RfcommServiceProvider^ provider) -> task<void> {
        _provider = provider;

        // Create a listener for this service and start listening
        auto listener = ref new StreamSocketListener();
        listener->ConnectionReceived += ref new TypedEventHandler<
                StreamSocketListener^,
                StreamSocketListenerConnectionReceivedEventArgs^>
           (&OnConnectionReceived);
        return create_task(listener->BindServiceNameAsync(
            _provider->ServiceId->AsString(),
            SocketProtectionLevel
                ::BluetoothEncryptionAllowNullAuthentication));
    }).then([listener](void) {
        // Set the SDP attributes and start advertising
        InitializeServiceSdpAttributes(_provider);
        _provider->StartAdvertising(listener);
    });
}

const uint SERVICE_VERSION_ATTRIBUTE_ID = 0x0300;
const byte SERVICE_VERSION_ATTRIBUTE_TYPE = 0x0A;   // UINT32
const uint SERVICE_VERSION = 200;
void InitializeServiceSdpAttributes(RfcommServiceProvider^ provider)
{
    auto writer = ref new Windows::Storage::Streams::DataWriter();

    // First write the attribute type
    writer->WriteByte(SERVICE_VERSION_ATTRIBUTE_TYPE);
    // Then write the data
    writer->WriteUInt32(SERVICE_VERSION);

    auto data = writer->DetachBuffer();
    provider->SdpRawAttributes->Add(SERVICE_VERSION_ATTRIBUTE_ID, data);
}

void OnConnectionReceived(
    StreamSocketListener^ listener,
    StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    // Stop advertising/listening so that we're only serving one client
    _provider->StopAdvertising();
    create_task(listener->Close())
    .then([args](void) {
        _socket = args->Socket;

        // The client socket is connected. At this point the App can wait for
        // the user to take some action, e.g. click a button to receive a
        // file from the device, which could invoke the Picker and then save
        // the received file to the picked location. The transfer itself
        // would use the Sockets API and not the Rfcomm API, and so is
        // omitted here for brevity.
    });
}
```
