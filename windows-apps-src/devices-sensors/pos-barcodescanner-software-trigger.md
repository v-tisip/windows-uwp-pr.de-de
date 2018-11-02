---
author: eliotcowley
title: Verwenden eines Software-Triggers
description: Hier erfahren Sie, wie Sie den Vorgang der Überprüfung von Software zu steuern.
ms.author: elcowle
ms.date: 08/29/2018
ms.topic: article
keywords: Windows 10, UWP, Point of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 03fbed5a0145a093b1e7a2535012077644aaf2e2
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5974128"
---
# <a name="use-a-software-trigger"></a>Verwenden eines Software-Triggers

Es kann hilfreich sein, den Vorgang der Überprüfung von Software zu steuern, wenn Sie einen Strichcodescanner im Präsentationsmodus verwenden oder wenn der Scanner nicht über einen physischen Trigger wie einen Kamera-basierten Strichcodescanner verfügt. Sie können den Überprüfungsvorgang initiieren, indem Sie [StartSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync) aufrufen.

Je nach Wert des [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) kann der Scanner nur einen Strichcode scannen und diesen beenden oder kontinuierlich bis zum Aufruf von [StopSoftwareTriggerAsync](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync) scannen.

Legen Sie den gewünschten Wert der [IsDisabledOnDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) fest, um das Verhalten des Scanners zu steuern, wenn ein Strichcode decodiert wird.

| Wert | Beschreibung |
| ----- | ----------- |
| Wahr   | Nur einen Barcode scannen und dann beenden |
| False  | Scannen Sie Barcodes ohne Unterbrechung |


> [!Important]
> Stellen Sie sicher, dass Ihre Strichcodescanner die Verwendung des Software-Trigger unterstützt, indem Sie zunächst die Eigenschaft [IsSoftwareTriggerSupported](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannercapabilities.issoftwaretriggersupported#Windows_Devices_PointOfService_BarcodeScannerCapabilities_IsSoftwareTriggerSupported) überprüfen.

Das folgende Beispiel zeigt, wie zum Initiieren der Überprüfung mithilfe eines Software-Triggers, das Scannen, nachdem sie einen Strichcode scannt beendet wird:

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