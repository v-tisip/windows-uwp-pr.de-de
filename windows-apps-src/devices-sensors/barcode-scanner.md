---
author: mukin
title: Strichcodescanner
description: "Dieser Artikel enthält Informationen zur Gerätefamilie der Point of Service-Strichcodescanner."
ms.author: wdg-dev-content
ms.date: 02/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 8d9ef9bc08fa666c2af1348450f7a5fb0a0c7b65
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="barcode-scanner"></a>Strichcodescanner
Ermöglicht Anwendungsentwicklern den Zugriff auf [Strichcodescanner](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.barcodescanner), um decodierte Daten aus einer Vielzahl von Barcodesymbologien wie UPC- und QR-Codes abzurufen, je nach Unterstützung der Hardware. In der [BarcodeSymbologies](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.barcodesymbologies)-Klasse finden Sie eine vollständige Liste der unterstützten Symbologien.

## <a name="requirements"></a>Anforderungen
Für Anwendungen, die diesen Namespace erfordern, muss dem App-Paketmanifest die [DeviceCapability](https://msdn.microsoft.com/library/4353c4fd-f038-4986-81ed-d2ec0c6235ef) "pointOfService" hinzugefügt werden.

## <a name="device-support"></a>Unterstützung von Geräten

### <a name="usb"></a>USB

#### <a name="hidscanner"></a>HID.Scanner
Windows enthält einen Strichcodescanner-Klassentreiber, der auf der HID.Scanner (8C)-Nutzungsseite basiert, die von USB.org definiert wird. Dieser Klassentreiber unterstützt alle Strichcodescanner, die diesen Standard implementieren, wie etwa: Herstellermodelle Honeywell 1900GSR-2, 1200g-2 Intermec SG20

Im Handbuch für den Strichcodescanner oder beim Hersteller finden Sie heraus, ob er als USB.HID. Scanner konfiguriert werden kann.

#### <a name="hidvendor-specific"></a>HID.Vendor-spezifisch
Windows unterstützt die Implementierung Hersteller-spezifischer Treiber zur Unterstützung zusätzlicher Strichcodescanner. Überprüfen Sie Sie beim Hersteller Ihres Strichcodescanners die Verfügbarkeit, wenn das Gerät nicht vom mitgelieferten USB.HID.Scanner unterstützt wird.

### <a name="bluetooth"></a>Bluetooth
#### <a name="serial-port-protocol-spp--simple-serial-interface-ssi"></a>Serielles Port-Protokoll (SPP) – einfache serielle Schnittstelle (SSI)
Windows unterstützt SPP-SSI-basierte Bluetooth-Strichcodescanner.

| Hersteller |    Model(le) |
|--------------|-----------|
| Socket Mobile |    **CHS 7-Serie:** <br/> 7 Ci 1D Imager-Strichcodescanner <br/> 7Di 1D Durable, Imager-Strichcodescanner <br/> 7Mi 1D Laser-Strichcodescanner <br/> 7Pi 1D Durable, Laser-Strichcodescanner <br/> **DuraScan 700-Serie:** <br/> D700 1D Imager-Strichcodescanner <br/> D730 1D Laser-Strichcodescanner <br/> **SocketScan 800-Serie** <br/> S800 1D Imager-Strichcodescanner (ehemals CHS 8Ci) <br/> S850 2D Imager-Strichcodescanner (ehemals CHS 8Qi)

## <a name="examples"></a>Beispiele
Im Strichcodescanner-Beispiel finden Sie eine Beispiel-Implementierung.
+    [Beispiel für Strichcodescanner](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BarcodeScanner)
