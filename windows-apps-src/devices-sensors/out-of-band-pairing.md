---
author: mukin
ms.assetid: E9ADC88F-BD4F-4721-8893-0E19EA94C8BA
title: Out-of-Band-Kopplung
description: "Mithilfe der Out-of-Band-Kopplung können Apps ohne Geräteermittlung eine Verbindung mit einem POS-Peripheriegerät (Point-of-Service) herstellen."
ms.author: mukin
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 25836204ca2942d4bbafc31e1c632c479ef3288f
ms.sourcegitcommit: ca060f051e696da2c1e26e9dd4d2da3fa030103d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2017
---
# <a name="out-of-band-pairing"></a><span data-ttu-id="e1868-104">Out-of-Band-Kopplung</span><span class="sxs-lookup"><span data-stu-id="e1868-104">Out-of-band pairing</span></span>

<span data-ttu-id="e1868-105">Mithilfe der Out-of-Band-Kopplung können Apps ohne Geräteermittlung eine Verbindung mit einem POS-Peripheriegerät (Point-of-Service) herstellen.</span><span class="sxs-lookup"><span data-stu-id="e1868-105">Out-of-band pairing allows apps to connect to a Point-of-Service peripheral without requiring discovery.</span></span> <span data-ttu-id="e1868-106">Apps müssen den [**Windows.Devices.PointOfService**](https://msdn.microsoft.com/library/windows/apps/windows.devices.pointofservice.aspx)-Namespace verwenden und eine speziell formatierte Zeichenfolge (Out-of-Band-Blob) an die entsprechende **FromIdAsync**-Methode für das gewünschte Peripheriegerät übergeben.</span><span class="sxs-lookup"><span data-stu-id="e1868-106">Apps must use the [**Windows.Devices.PointOfService**](https://msdn.microsoft.com/library/windows/apps/windows.devices.pointofservice.aspx) namespace and pass in a specifically formatted string (out-of-band blob) to the appropriate **FromIdAsync** method for the desired peripheral.</span></span> <span data-ttu-id="e1868-107">Bei Ausführung von **FromIdAsync** wird das Hostgerät mit dem Peripheriegerät gekoppelt und verbunden, bevor der Vorgang an den Aufrufer zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e1868-107">When **FromIdAsync** is executed, the host device pairs and connects to the peripheral before the operation returns to the caller.</span></span>

## <a name="out-of-band-blob-format"></a><span data-ttu-id="e1868-108">Out-of-Band-Blob-Format</span><span class="sxs-lookup"><span data-stu-id="e1868-108">Out-of-band blob format</span></span>

```json
    "connectionKind":"Network",
    "physicalAddress":"AA:BB:CC:DD:EE:FF",
    "connectionString":"192.168.1.1:9001",
    "peripheralKinds":"{C7BC9B22-21F0-4F0D-9BB6-66C229B8CD33}",
    "providerId":"{02FFF12E-7291-4A5D-ADFA-DA8FB7769CD2}",
    "providerName":"PrinterProtocolProvider.dll"
```

<span data-ttu-id="e1868-109">**connectionKind** – die Art der Verbindung.</span><span class="sxs-lookup"><span data-stu-id="e1868-109">**connectionKind** - The type of connection.</span></span> <span data-ttu-id="e1868-110">Gültige Werte sind „Network“ und „Bluetooth“.</span><span class="sxs-lookup"><span data-stu-id="e1868-110">Valid values are "Network" and "Bluetooth".</span></span>

<span data-ttu-id="e1868-111">**physicalAddress** – die MAC-Adresse des Peripheriegeräts.</span><span class="sxs-lookup"><span data-stu-id="e1868-111">**physicalAddress** - The MAC address of the peripheral.</span></span> <span data-ttu-id="e1868-112">Bei einem Netzwerkdrucker wäre dies z.B. die MAC-Adresse, die vom Testblatt des Druckers im Format AA:BB:CC:DD:EE:FF bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="e1868-112">For example, in case of a network printer, this would be the MAC address that is provided by the printer test sheet in AA:BB:CC:DD:EE:FF format.</span></span>

<span data-ttu-id="e1868-113">**connectionString** – die Verbindungszeichenfolge des Peripheriegeräts.</span><span class="sxs-lookup"><span data-stu-id="e1868-113">**connectionString** - The connection string of the peripheral.</span></span> <span data-ttu-id="e1868-114">Bei einem Netzwerkdrucker wäre dies z. B. die auf dem Testblatt im Format 192.168.1.1:9001 ausgegebene IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="e1868-114">For example, in the case of a network printer, this would be the IP address provided by the printer test sheet in 192.168.1.1:9001 format.</span></span> <span data-ttu-id="e1868-115">Dieses Feld wird bei allen Bluetooth-Peripheriegeräten weggelassen.</span><span class="sxs-lookup"><span data-stu-id="e1868-115">This field is omitted for all Bluetooth peripherals.</span></span>

<span data-ttu-id="e1868-116">**peripheralKinds** – Die GUID für den Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="e1868-116">**peripheralKinds** - The GUID for the device type.</span></span> <span data-ttu-id="e1868-117">Gültige Werte sind:</span><span class="sxs-lookup"><span data-stu-id="e1868-117">Valid values are:</span></span>

| <span data-ttu-id="e1868-118">Gerätetyp</span><span class="sxs-lookup"><span data-stu-id="e1868-118">Device type</span></span> | <span data-ttu-id="e1868-119">GUID</span><span class="sxs-lookup"><span data-stu-id="e1868-119">GUID</span></span> |
| ---- | ---- |
| *<span data-ttu-id="e1868-120">POSPrinter</span><span class="sxs-lookup"><span data-stu-id="e1868-120">POSPrinter</span></span>* | <span data-ttu-id="e1868-121">C7BC9B22-21F0-4F0D-9BB6-66C229B8CD33</span><span class="sxs-lookup"><span data-stu-id="e1868-121">C7BC9B22-21F0-4F0D-9BB6-66C229B8CD33</span></span> |
| *<span data-ttu-id="e1868-122">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="e1868-122">Barcode Scanner</span></span>* | <span data-ttu-id="e1868-123">C243FFBD-3AFC-45E9-B3D3-2BA18BC7EBC5</span><span class="sxs-lookup"><span data-stu-id="e1868-123">C243FFBD-3AFC-45E9-B3D3-2BA18BC7EBC5</span></span> |
| *<span data-ttu-id="e1868-124">Kassenschublade</span><span class="sxs-lookup"><span data-stu-id="e1868-124">Cash Drawer</span></span>* | <span data-ttu-id="e1868-125">772E18F2-8925-4229-A5AC-6453CB482FDA</span><span class="sxs-lookup"><span data-stu-id="e1868-125">772E18F2-8925-4229-A5AC-6453CB482FDA</span></span> |


<span data-ttu-id="e1868-126">**providerId** – die GUID für die Protokollanbieterklasse.</span><span class="sxs-lookup"><span data-stu-id="e1868-126">**providerId** - The GUID for the protocol provider class.</span></span> <span data-ttu-id="e1868-127">Gültige Werte sind:</span><span class="sxs-lookup"><span data-stu-id="e1868-127">Valid values are:</span></span>

| <span data-ttu-id="e1868-128">Protokollanbieterklasse</span><span class="sxs-lookup"><span data-stu-id="e1868-128">Protocol provider class</span></span> | <span data-ttu-id="e1868-129">GUID</span><span class="sxs-lookup"><span data-stu-id="e1868-129">GUID</span></span> |
| ---- | ---- |
| *<span data-ttu-id="e1868-130">POSPrinter: Network - Epson</span><span class="sxs-lookup"><span data-stu-id="e1868-130">POSPrinter: Network - Epson</span></span>* | <span data-ttu-id="e1868-131">9F0F8BE3-4E59-4520-BFBA-AF77614A31CE</span><span class="sxs-lookup"><span data-stu-id="e1868-131">9F0F8BE3-4E59-4520-BFBA-AF77614A31CE</span></span> |
| *<span data-ttu-id="e1868-132">POSPrinter: Network - Generic (nur ESC/POS)</span><span class="sxs-lookup"><span data-stu-id="e1868-132">POSPrinter: Network - Generic (ESC/POS only)</span></span>* | <span data-ttu-id="e1868-133">02FFF12E-7291-4A5D-ADFA-DA8FB7769CD2</span><span class="sxs-lookup"><span data-stu-id="e1868-133">02FFF12E-7291-4A5D-ADFA-DA8FB7769CD2</span></span> |
| *<span data-ttu-id="e1868-134">POSPrinter: Network - Star Micronics</span><span class="sxs-lookup"><span data-stu-id="e1868-134">POSPrinter: Network - Star Micronics</span></span>* | <span data-ttu-id="e1868-135">1E3A32C2-F411-4B8C-AC91-CC2C5FD21996</span><span class="sxs-lookup"><span data-stu-id="e1868-135">1E3A32C2-F411-4B8C-AC91-CC2C5FD21996</span></span> |
| *<span data-ttu-id="e1868-136">POSPrinter: Bluetooth - Epson</span><span class="sxs-lookup"><span data-stu-id="e1868-136">POSPrinter: Bluetooth - Epson</span></span>* | <span data-ttu-id="e1868-137">94917594-544F-4AF8-B53B-EC6D9F8A4464</span><span class="sxs-lookup"><span data-stu-id="e1868-137">94917594-544F-4AF8-B53B-EC6D9F8A4464</span></span> |
| *<span data-ttu-id="e1868-138">POSPrinter: Bluetooth - Generic (nur ESC/POS)</span><span class="sxs-lookup"><span data-stu-id="e1868-138">POSPrinter: Bluetooth - Generic (ESC/POS only)</span></span>* | <span data-ttu-id="e1868-139">CCD5B810-95B9-4320-BA7E-78C223CAF418</span><span class="sxs-lookup"><span data-stu-id="e1868-139">CCD5B810-95B9-4320-BA7E-78C223CAF418</span></span> |
| *<span data-ttu-id="e1868-140">Kassenschublade: Network - APG</span><span class="sxs-lookup"><span data-stu-id="e1868-140">Cash Drawer: Network - APG</span></span>* | <span data-ttu-id="e1868-141">E619E2FE-9489-4C74-BF57-70AED670B9B0</span><span class="sxs-lookup"><span data-stu-id="e1868-141">E619E2FE-9489-4C74-BF57-70AED670B9B0</span></span> |
| *<span data-ttu-id="e1868-142">Kassenschublade: Bluetooth - APG</span><span class="sxs-lookup"><span data-stu-id="e1868-142">Cash Drawer: Bluetooth - APG</span></span>* | <span data-ttu-id="e1868-143">332E6550-2E01-42EB-9401-C6A112D80185</span><span class="sxs-lookup"><span data-stu-id="e1868-143">332E6550-2E01-42EB-9401-C6A112D80185</span></span> |
| *<span data-ttu-id="e1868-144">Strichcodescanner: Bluetooth (SPP-SSI)</span><span class="sxs-lookup"><span data-stu-id="e1868-144">Barcode Scanner: Bluetooth (SPP-SSI)</span></span>* | <span data-ttu-id="e1868-145">6E7C8178-A006-405E-85C3-084244885AD2</span><span class="sxs-lookup"><span data-stu-id="e1868-145">6E7C8178-A006-405E-85C3-084244885AD2</span></span> |

<span data-ttu-id="e1868-146">**providerName** – die DLL mit dem Namen des Anbieters.</span><span class="sxs-lookup"><span data-stu-id="e1868-146">**providerName** - The name of the provider DLL.</span></span> <span data-ttu-id="e1868-147">Die Standardanbieter sind:</span><span class="sxs-lookup"><span data-stu-id="e1868-147">The default providers are:</span></span>

| <span data-ttu-id="e1868-148">Anbieter</span><span class="sxs-lookup"><span data-stu-id="e1868-148">Provider</span></span> | <span data-ttu-id="e1868-149">DLL-Name</span><span class="sxs-lookup"><span data-stu-id="e1868-149">DLL name</span></span> |
| ---- | ---- |
| <span data-ttu-id="e1868-150">POSPrinter</span><span class="sxs-lookup"><span data-stu-id="e1868-150">POSPrinter</span></span> | <span data-ttu-id="e1868-151">PrinterProtocolProvider.dll</span><span class="sxs-lookup"><span data-stu-id="e1868-151">PrinterProtocolProvider.dll</span></span> |
| <span data-ttu-id="e1868-152">Kassenschublade</span><span class="sxs-lookup"><span data-stu-id="e1868-152">Cash Drawer</span></span> | <span data-ttu-id="e1868-153">CashDrawerProtocolProvider.dll</span><span class="sxs-lookup"><span data-stu-id="e1868-153">CashDrawerProtocolProvider.dll</span></span> |
| <span data-ttu-id="e1868-154">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="e1868-154">Barcode Scanner</span></span> | <span data-ttu-id="e1868-155">BarcodeScannerProtocolProvider.dll</span><span class="sxs-lookup"><span data-stu-id="e1868-155">BarcodeScannerProtocolProvider.dll</span></span> |

## <a name="usage-example-network-posprinter"></a><span data-ttu-id="e1868-156">Verwendungsbeispiel: Netzwerk-POSPrinter</span><span class="sxs-lookup"><span data-stu-id="e1868-156">Usage example: Network POSPrinter</span></span>

```csharp
String oobBlobNetworkPrinter =
  "{\"connectionKind\":\"Network\"," +
  "\"physicalAddress\":\"AA:BB:CC:DD:EE:FF\"," +
  "\"connectionString\":\"192.168.1.1:9001\"," +
  "\"peripheralKinds\":\"{C7BC9B22-21F0-4F0D-9BB6-66C229B8CD33}\"," +
  "\"providerId\":\"{02FFF12E-7291-4A5D-ADFA-DA8FB7769CD2}\"," +
  "\"providerName\":\"PrinterProtocolProvider.dll\"}";

printer = await PosPrinter.FromIdAsync(oobBlobNetworkPrinter);
```

## <a name="usage-example-bluetooth-posprinter"></a><span data-ttu-id="e1868-157">Verwendungsbeispiel: Bluetooth-POSPrinter</span><span class="sxs-lookup"><span data-stu-id="e1868-157">Usage example: Bluetooth POSPrinter</span></span>

```csharp
string oobBlobBTPrinter =
    "{\"connectionKind\":\"Bluetooth\"," +
    "\"physicalAddress\":\"AA:BB:CC:DD:EE:FF\"," +
    "\"peripheralKinds\":\"{C7BC9B22-21F0-4F0D-9BB6-66C229B8CD33}\"," +
    "\"providerId\":\"{CCD5B810-95B9-4320-BA7E-78C223CAF418}\"," +
    "\"providerName\":\"PrinterProtocolProvider.dll\"}";

printer = await PosPrinter.FromIdAsync(oobBlobBTPrinter);

```
