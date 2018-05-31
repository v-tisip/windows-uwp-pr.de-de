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
ms.openlocfilehash: ed0fa79f5bbdfdaf8ca1f3273fa8d741f17efe1d
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1833186"
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

## <a name="working-with-symbologies"></a>Verwenden von Fotos Symbologien
Eine [**Strichcode-Symbologie**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologies) ist die Zuordnung der Daten zu einem bestimmten Strichcode-Format. Einige allgemeinen Symbologien enthalten UPC, Code 128, QR-Code. Die UWP-Strichcodescanner-APIs ermöglichen einer Anwendung, zu steuern, wie der Scanner die Symbologien verarbeitet, ohne manuell den Scanner konfigurieren zu müssen. 

### <a name="determine-which-symbologies-are-supported"></a>Bestimmen Sie, welche Symbologien unterstützt werden 
Da die Anwendung unterschiedliche Strichcodescannermodelle verschiedener Hersteller verwenden kann, sollten Sie den Scanner befragen, um die Liste der Symbologien zu ermitteln, die er unterstützt.  Dies kann nützlich sein, wenn die Anwendung eine bestimmte Symbologie erfordert, die möglicherweise nicht von allen Scannern unterstützt wird oder Sie müssen Symbologien aktivieren, die entweder manuell oder programmgesteuert auf dem Scanner deaktiviert wurden.
Sobald Sie ein [**BarcodeScanner**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner)-Objekt mit [**BarcodeScanner.FromIdAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.fromidasync) haben, rufen Sie [**GetSupportedSymbologiesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.getsupportedsymbologiesasync#Windows_Devices_PointOfService_BarcodeScanner_GetSupportedSymbologiesAsync) auf, um eine Liste der Symbologien zu erhalten, die vom Gerät unterstützt werden.

### <a name="determine-if-a-specific-symbology-is-supported"></a>Bestimmen Sie, ob eine bestimmte Symbologie unterstützt wird
Um festzustellen, ob der Scanner eine bestimmte Symbologie unterstützt, rufen Sie [**IsSymbologySupportedAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.issymbologysupportedasync#Windows_Devices_PointOfService_BarcodeScanner_IsSymbologySupportedAsync_System_UInt32_) auf

### <a name="changing-which-symbologies-are-recognized"></a>Ändern, welche Symbologien erkannt werden
In einigen Fällen möchten Sie möglicherweise eine Teilmenge Symbologien verwenden, die der Strichcodescanner unterstützt.  Dies ist besonders nützlich, um Symbologien zu blockieren, die Sie nicht in Ihrer Anwendung verwenden möchten. Um sicherzustellen, dass ein Benutzer den richtigen Strichcode scannt, können Sie das Scannen auf UPC oder EAN beim Kauf von Element-SKUs beschränken und das Scannen auf Code 128 beim Kauf von Seriennummern beschränken.
Wenn Sie die Symbologien kennen, die der Scanner unterstützt, können Sie die Symbologien festlegen, die Sie erkennen möchten.  Dies ist möglich, nachdem Sie ein [**ClaimedBarcodeScanner**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner)-Objekt mithilfe von [**ClaimScannerAsyc**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodescanner.claimscannerasync#Windows_Devices_PointOfService_BarcodeScanner_ClaimScannerAsync) eingerichtet haben. Rufen Sie [**SetActiveSymbologiesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setactivesymbologiesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetActiveSymbologiesAsync_Windows_Foundation_Collections_IIterable_System_UInt32__) auf, um eine bestimmte Anzahl von Symbologien zu aktivieren, während andere aus der Liste deaktiviert werden.

### <a name="restricting-scan-data-by-data-length"></a>Einschränken von gescannten Daten nach Datenlänge
Einige Symbologien haben verschiedene Längen z.B. Code 39 oder Code 128.  Strichcodes mit dieser Symbologie können bestimmt werden, wobei jeder verschiedene Daten mit einer bestimmten Länge haben kann. Das Festlegen der bestimmten Länge der Daten, die Sie benötigen, kann ungültige Überprüfungen verhindern.

| Methode    | Beschreibung |
| :-------- | :---------- |
| [**SetSymbologyAttributesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetSymbologyAttributesAsync_System_UInt32_Windows_Devices_PointOfService_BarcodeSymbologyAttributes_) | Ermöglicht das Konfigurieren einer gewünschten Länge decodierter Daten und wie der Scanner die Prüfziffer überprüft. |
| [**GetSymbologyAttributesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.getsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_GetSymbologyAttributesAsync_System_UInt32_) | Ermöglicht das Abrufen der aktuellen Länge und das Überprüfen der Prüfziffer. |

> [!Important] 
> Stellen Sie sicher, dass Ihr Strichcodescanner die Verwendung von Symbologieattributen unterstützt, indem Sie zunächst die folgenden Eigenschaften prüfen: [**SetSymbologyAttributesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.setsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_SetSymbologyAttributesAsync_System_UInt32_Windows_Devices_PointOfService_BarcodeSymbologyAttributes_) oder [**GetSymbologyAttributesAsync**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedbarcodescanner.getsymbologyattributesasync#Windows_Devices_PointOfService_ClaimedBarcodeScanner_GetSymbologyAttributesAsync_System_UInt32_) | Ermöglicht das Abrufen der aktuellen Länge und das Überprüfen der Prüfziffer. :
> - [**IsDecodeLengthSupported**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.isdecodelengthsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsDecodeLengthSupported)
> - [**ICheckDigitTransmissionSupported**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigittransmissionsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsCheckDigitTransmissionSupported)
> - [**IsCheckDigitValidationSupported**](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.barcodesymbologyattributes.ischeckdigitvalidationsupported#Windows_Devices_PointOfService_BarcodeSymbologyAttributes_IsCheckDigitValidationSupported)

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
