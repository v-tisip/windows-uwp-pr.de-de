---
author: TerryWarwick
title: Erste Schrittemit Strichcodescannern
description: Hier erfahren Sie, wie Sie mit einem Strichcodescanner von einer universellen Windows-Anwendung interagieren
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 0fddfa3aa78c274735634315b1230b0893020805
ms.sourcegitcommit: dc3389ef2e2c94b324872a086877314d6f963358
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
ms.locfileid: "1874198"
---
# <a name="getting-started-with-barcode-scanners"></a>Erste Schrittemit Strichcodescannern

Hier erfahren Sie, wie Sie mit einem Strichcodescanner von einer universellen Windows-Anwendung interagieren.  Dieses Thema enthält Informationen zu bestimmten Funktionen des Strichcodescanner.

## <a name="configuring-your-barcode-scanner"></a>Konfigurieren Ihres Strichcodescanners
Strichcodescanner können in mehreren verschiedenen Modi konfiguriert werden.  Es ist wichtig für Ihren Strichcodescanner, dass er für die Anwendung ordnungsgemäß konfiguriert ist.  Viele Strichcodescanner können im **Tastatur Wedge**-Modus konfiguriert werden. Dabei wird der Strichcodescanner als eine Tastatur auf Windows angezeigt.  Dadurch können Sie Strichcodes in Anwendungen scannen, die keine Strichcodescanner unterstützen, wie Notepad.  Wenn Sie einen Strichcode in diesem Modus scannen, werden die decodierten Daten aus dem Strichcodescanner an der Einfügemarke eingefügt, als ob Sie die Daten über die Tastatur eingegeben.  Wenn Sie mehr Kontrolle über Ihren Strichcodescanner von der UWP-App haben möchten, müssen Sie diesen in einem Modus ohne Tastatur-Wedge konfigurieren.

### <a name="usb-barcode-scanner"></a>USB-Strichcodescanner
Ein USB-verbundener Strichcodescanner muss im **HID POS-Scanner**-Modus mit den Strichcodescannertreiber konfiguriert werden, der in Windows enthalten ist. Dieser Treiber ist eine Implementierung der **HID Point of Sale Usage Tables**-Spezifikation, die auf [**USB-HID-**](http://www.usb.org/developers/hidpage/) veröffentlicht wird.  Weitere Informationen finden Sie in der Dokumentation der Strichcodescanner oder wenden Sie sich an den Hersteller des Scanners für weitere Anweisungen zum Aktivieren des **POS-HID-Scanner**-Modus.  Wenn der Strichcodescanner als **POS-HID-Scanner** konfiguriert ist, erscheint er im Geräte-Manager unter dem **POS-Strichcodescanner**-Knoten als **POS HID Strichcodescanner**.
Der Hersteller des Strichcodescanners hat möglicherweise einen anbieterspezifischen Treiber, der die UWP Strichcodescanner-APIs in einem anderen Modus als **POS-HID-Scanner** unterstützt.  Wenn Sie bereits einen anwenderspezifischen Treiber installiert haben, der mit UWP Strichcodescanner-APIs kompatibel ist , sehen Sie ein anwenderspezifisches Geräte unter **POS-Strichcodescanner** im Geräte-Manager.

### <a name="bluetooth-barcode-scanner"></a>Bluetooth-Strichcodescanner
Ein mit Bluetooth verbundener Scanner muss im **Seriellen Port-Protokoll – einfache serielle Schnittstelle (SPP-SSI)**-Modus für die Arbeit mit UWP Strichcodescanner-APIs konfiguriert sein.  Weitere Informationen finden Sie in der Dokumentation der Strichcodescanner oder wenden Sie sich an den Hersteller des Scanners für weitere Anweisungen zum Aktivieren des **SSI-SPP-Modus**.  
Vor der Verwendung Ihres Bluetooth-Strichcodescanners müssen Sie ihn mit Bluetooth koppeln – Geräte - Bluetooth & andere Geräte - Bluetooth oder ein anderes Gerät hinzufügen.  
Sie können die Kopplungszeremonie mit **Windows.Devices.Enumeration**-Namespace initiieren und steuern.  Weitere Informationen finden Sie unter [**Geräte koppeln**](https://docs.microsoft.com/windows/uwp/devices-sensors/pair-devices).

## <a name="using-software-trigger-with-barcode-scanners"></a>Verwenden von Software Trigger-Strichcodescannern
### <a name="initiate-scan-from-software"></a>Initiieren der Überprüfung von Software
Es kann hilfreich sein, den Vorgang der Überprüfung von Software zu steuern, wenn Sie einen Strichcodescanner im Präsentationsmodus verwenden oder wenn der Scanner nicht über einen physischen Trigger wie einen Kamera-basierten Strichcodescanner verfügt. Sie können den Überprüfungsvorgang initiieren, indem Sie [**StartSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.startsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StartSoftwareTriggerAsync) aufrufen.  
Je nach Wert des [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) kann der Scanner nur einen Strichcode scannen und diesen beenden oder kontinuierlich bis zum Aufruf von [**StopSoftwareTriggerAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.stopsoftwaretriggerasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_StopSoftwareTriggerAsync) scannen.

Legen Sie den gewünschten Wert der [**IsDisabledOnDataReceived**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.isdisabledondatareceived#Windows_Devices_PointOfService_ClaimedBarcodeScanner_IsDisabledOnDataReceived) fest, um das Verhalten des Scanners zu steuern, wenn ein Strichcode decodiert wird.

| Wert | Beschreibung |
| ----- | ----------- |
| Wahr   | Nur einen Barcode scannen und dann beenden |
| False  | Scannen Sie Barcodes ohne Unterbrechung |


> [!Important]
> Stellen Sie sicher, dass Ihre Strichcodescanner die Verwendung des Software-Trigger unterstützt, indem Sie zunächst die Eigenschaft [**IsSoftwareTriggerSupported**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescannercapabilities.issoftwaretriggersupported#Windows_Devices_PointOfService_BarcodeScannerCapabilities_IsSoftwareTriggerSupported) überprüfen.
