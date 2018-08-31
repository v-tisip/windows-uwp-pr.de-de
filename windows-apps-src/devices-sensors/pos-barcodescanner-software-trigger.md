---
author: eliotcowley
title: Verwenden Sie einen Software-trigger
description: Hier erfahren Sie, wie Sie den Vorgang der Überprüfung von Software zu steuern.
ms.author: elcowle
ms.date: 08/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: ddd8ec979cb6d5a72b48b9b8b6a60adb73c35657
ms.sourcegitcommit: 1e5590dd10d606a910da6deb67b6a98f33235959
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "3228889"
---
# <a name="use-a-software-trigger"></a><span data-ttu-id="e3ec5-104">Verwenden Sie einen Software-trigger</span><span class="sxs-lookup"><span data-stu-id="e3ec5-104">Use a software trigger</span></span>

<span data-ttu-id="e3ec5-105">Es kann hilfreich sein, den Vorgang der Überprüfung von Software zu steuern, wenn Sie einen Strichcodescanner im Präsentationsmodus verwenden oder wenn der Scanner nicht über einen physischen Trigger wie einen Kamera-basierten Strichcodescanner verfügt.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-105">It can be useful to control the act of scanning from software if you are using a barcode scanner in presentation mode or if the scanner does not have a physical trigger such as a camera-based barcode scanner.</span></span> <span data-ttu-id="e3ec5-106">Sie können den Überprüfungsvorgang initiieren, indem Sie [StartSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-106">You can initiate the scan process by calling [StartSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync).</span></span>

<span data-ttu-id="e3ec5-107">Je nach Wert des [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) kann der Scanner nur einen Strichcode scannen und diesen beenden oder kontinuierlich bis zum Aufruf von [StopSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync) scannen.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-107">Depending on the value of [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) the scanner may scan only one barcode then stop or scan continuously until you call [StopSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync).</span></span>

<span data-ttu-id="e3ec5-108">Legen Sie den gewünschten Wert der [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) fest, um das Verhalten des Scanners zu steuern, wenn ein Strichcode decodiert wird.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-108">Set the desired value of [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) to control the scanner behavior when a barcode is decoded.</span></span>

| <span data-ttu-id="e3ec5-109">Wert</span><span class="sxs-lookup"><span data-stu-id="e3ec5-109">Value</span></span> | <span data-ttu-id="e3ec5-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3ec5-110">Description</span></span> |
| ----- | ----------- |
| <span data-ttu-id="e3ec5-111">Wahr</span><span class="sxs-lookup"><span data-stu-id="e3ec5-111">True</span></span>   | <span data-ttu-id="e3ec5-112">Nur einen Barcode scannen und dann beenden</span><span class="sxs-lookup"><span data-stu-id="e3ec5-112">Scan only one barcode then stop</span></span> |
| <span data-ttu-id="e3ec5-113">False</span><span class="sxs-lookup"><span data-stu-id="e3ec5-113">False</span></span>  | <span data-ttu-id="e3ec5-114">Scannen Sie Barcodes ohne Unterbrechung</span><span class="sxs-lookup"><span data-stu-id="e3ec5-114">Continuously scan barcodes without stopping</span></span> |


> [!Important]
> <span data-ttu-id="e3ec5-115">Stellen Sie sicher, dass Ihre Strichcodescanner die Verwendung des Software-Trigger unterstützt, indem Sie zunächst die Eigenschaft [IsSoftwareTriggerSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannercapabilities.issoftwaretriggersupported#Windows_Devices_PointOfService_BarcodeScannerCapabilities_IsSoftwareTriggerSupported) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-115">Confirm that your barcode scanner supports the use of software trigger by first checking the property [IsSoftwareTriggerSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannercapabilities.issoftwaretriggersupported#Windows_Devices_PointOfService_BarcodeScannerCapabilities_IsSoftwareTriggerSupported).</span></span>

<span data-ttu-id="e3ec5-116">Das folgende Beispiel zeigt, wie zum Initiieren der Überprüfung mithilfe eines Software-Triggers, der angehalten wird, nachdem sie einen Strichcode scannt Überprüfung:</span><span class="sxs-lookup"><span data-stu-id="e3ec5-116">The following example shows how to initiate scanning using a software trigger, which will stop scanning once it scans one barcode:</span></span>

```cs
private void SoftwareTrigger(BarcodeScanner barcodeScanner, ClaimedBarcodeScanner claimedBarcodeScanner) 
{
    if (barcodeScanner.Capabilities.IsSoftwareTriggerSupported)
    {
        claimedBarcodeScanner.IsDisabledOnDataReceived = true;
        await claimedBarcodeScanner.StartSoftwareTriggerAsync();
    }
}
```

[!INCLUDE [feedback](./includes/pos-feedback.md)]