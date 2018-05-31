---
author: TerryWarwick
title: Unterstützung von PointofService (POS)-Hardware
description: Dieser Artikel enthält Informationen zur Unterstützung der Hardware für jede PointofService (POS)-Geräteklasse
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ecb2468497115c9595f6fd17ab61b30caed507ab
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832094"
---
# <a name="supported-point-of-service-peripherals"></a>Unterstützte Point of Service-Peripheriegeräte

## <a name="barcode-scanner"></a>Strichcodescanner
| Konnektivität | Support |
| -------------|-------------|
| USB          | <p>Windows enthält für USB-verbundene Strichcodescanner einen integrierten Klassentreiber, dessen Spezifikation auf der von der [USB.org](http://www.usb.org/developers/hidpage/) definierten HID POS-Scanner-Nutzungstabelle (8c) basiert. Eine Liste bekannter kompatibler Geräte finden Sie in folgender Tabelle.  Sehen Sie im Handbuch Ihres Strichcodescanners nach oder wenden Sie sich an den Hersteller, um zu erfahren, wie Sie Ihren Scanner im **USB.HID.POS Scanner**-Scannermodus konfigurieren. </p><p>Windows unterstützt auch die Implementierung von herstellerspezifischen Treibern für weitere Strichcodescanner, die den Scannerstandard „USB.HID.POS“ nicht unterstützen. Erfragen Sie beim Hersteller Ihres Strichcodescanners, ob ein herstellerspezifischer Treiber verfügbar ist.</p><p>Hersteller von Strichcodescannern sollten Sie sich an das [Strichcodescannertreiber-Entwurfshandbuch](https://aka.ms/pointofservice-drv) für weitere Informationen zum Erstellen eines benutzerdefinierten Strichcodescannertreibers wenden</p> |
| Bluetooth    | <p>Windows unterstützt den auf Seriellem Port-Protokoll – einfacher serieller Schnittstelle (SPP-SSI) basierten Bluetooth-Strichcodescanner. Eine Liste bekannter kompatibler Geräte finden Sie in folgender Tabelle. Sehen Sie im Handbuch Ihres Strichcodescanners nach oder wenden Sie sich an den Hersteller, um zu erfahren, wie Sie Ihren Scanner im **SPP-SSI**-Scannermodus konfigurieren.</p> |
| Webcam       | <p>Ab Windows10, Version 1803, können Sie Strichcodescanner über ein Standard-Kameraobjektiv von einer universellen Windows-Anwendung lesen. Es wird empfohlen, dass Sie eine Kamera verwenden, die Autofokus und eine Auflösung von mindestens 1920 x 1440 unterstützt.  Einige niedrigere Auflösungen bei Kameras können Standardstrichcodes lesen, wenn der Strichcode groß genug gedruckt wird.  Barcodes mit weniger umfangreichen Elementen benötigen möglicherweise höhere Auflösungen bei einer Kamera.</p>| 
|


### <a name="compatible-barcode-scanners"></a>Kompatible Strichcodescanner
| Kategorie | Konnektivität | Hersteller/ Modell |
|--------------|-----------|-----------|
| **1D-Handheld-Scanner** | **USB** |Honeywell Voyager 1200g<br/>Honeywell Voyager 1202g<br/>Honeywell Voyager 1202-bf<br/>Honeywell Voyager 145Xg (Aktualisierbar)|
| **1D-Handheld-Scanner** | **Bluetooth** |Socket Mobile CHS 7Ci<br/> Socket Mobile CHS 7Di<br/> Socket Mobile CHS 7Mi<br/> Socket Mobile CHS 7Pi<br/>Socket Mobile DuraScan D700<br/> Socket Mobile DuraScan D730<br/>Socket Mobile SocketScan S800 (ehemals CHS 8Ci) <br/>|
|**2D-Handheld-Scanner** | **USB** |Code Reader™ 950<br/>Code Reader™ 1021<br/>Code Reader™ 1421<br/> Honeywell Granit 198Xi<br/>Honeywell Granit 191Xi<br/>Honeywell Xenon 1900g<br/>Honeywell Xenon 1902g<br/>Honeywell Xenon 1902g-bf<br/>Honeywell Xenon 1900h<br/>Honeywell Xenon 1902h<br/>Honeywell Voyager 145Xg (Aktualisierbar)<br/>Honeywell Voyager 1602g<br/>Intermec SG20<br/>Zebra DS2278<br/>Zebra DS8108 ¹<hr><small>¹ Firmware mindestens 016 (2018.01.18) erforderlich. Upgrade mit [123Scan](http://www.zebra.com/123Scan)</small>|
|**2D-Handheld-Scanner** | **Bluetooth** |Socket Mobile SocketScan S850 (ehemals CHS 8Qi)|
| **Präsentationsscanner** | **USB** |Code Reader™ 5000<br/>Honeywell Genesis 7580g<br/>Honeywell Orbit 7190g|
| **Kassentisch-Scanner** | **USB** |Honeywell Stratos 2700|
| **Scan-Module** | **USB** | Honeywell N5680<br/>Honeywell N3680|
| **Windows-Mobilgeräte**| **Integrierte** |Bluebird EF400<br/>Bluebird EF500<br/>Bluebird EF500R<br/>Honeywell CT50<br/>Honeywell D75e<br/>Janam XT2<br/>Panasonic FZ-E1<br/>Panasonic FZ-F1<br/>PointMobile PM80<br/>Zebra TC700j|
| **Windows-Mobilgeräte**| **„Benutzerdefiniert“** | HP Elite X3 mit Strichcodescannerhülle |


## <a name="cash-drawer"></a>Kassenschublade
| Konnektivität | Support |
| -------------|-------------|
| Netzwerk/Bluetooth | <p> Eine direkte Verbindung zur Kassenschublade kann über das Netzwerk oder über Bluetooth hergestellt werden, je nach den Funktionen der Kassenschublade. </p><p>APG-Kassenschublade: NetPRO, BluePRO</p> |
| DK-Port | <p> Kassenschubladen ohne Netzwerk- oder Bluetooth-Funktionen können über den DK-Port auf unterstützten Belegdruckern oder das Star Micronics DK-AirCash-Zubehör verbunden werden. </p>
| OPOS    | <p> Unterstützt alle OPOS-kompatiblen Kassenschubladen über OPOS Service-Objekte, die vom Hersteller bereitgestellt werden. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers. </p> |


## <a name="customer-display-linedisplay"></a>Kunden-Anzeige (LineDisplay)
Unterstützt alle OPOS-kompatiblen Zeilenanzeigen über OPOS Service-Objekte, die vom Hersteller bereitgestellt werden. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers.

## <a name="magnetic-stripe-reader"></a>Magnetstreifenleser
Windows bietet Unterstützung für die folgenden Magnetstreifenleser von Magtek und IDTech, basierend auf deren Anbieter-ID und Produkt-ID (VID/PID).

| Hersteller |    Model(le) |  Teilenummer |
|--------------|-----------|--------------|
| IDTech | SecureMag (VID:0ACD PID:2010) | IDRE-3x5xxxx |
| | MiniMag (VID:0ACD PID:0500) |   IDMB-3x5xxxx |
| Magtek | MagneSafe (VID:0801 PID:0011) |  210730xx |
| | Dynamag (VID:0801 PID:0002) |   210401xx |

 Windows unterstützt die Implementierung der zusätzlichen anbieterspezifischen Treiber zur Unterstützung von Magnetstreifenlesern. Bitte prüfen Sie die Verfügbarkeit des Magnetstreifenlesers bei Ihrem Hersteller. Hersteller von Magnetstreifenlesers sollten sich an das [Magnetstreifenleser-Entwurfshandbuch](https://aka.ms/pointofservice-drv) für weitere Informationen zum Erstellen eines benutzerdefinierten Magnetstreifenlesers wenden.

## <a name="receipt-printer-posprinter"></a>Belegdrucker (POSPrinter)
| Konnektivität | Unterstützung |
| -------------|-------------|
| Netzwerk und Bluetooth | <p>Windows unterstützt die Möglichkeit, mit der Epson ESC/POS-Druckersteuerungssprache auf Belegdruckern über Netzwerk und Bluetooth zu drucken.  Die unten aufgeführten Drucker werden automatisch über POSPrinter-APIs ermittelt. Zusätzliche Belegdrucker, die eine ESC/POS-Emulation bieten, funktionieren auch, müssen aber über einen [Out-Band-Kopplungs](https://aka.ms/pointofservice-oobpairing)-Prozess verknüpft werden .</p><p>Hinweis: Kassenbelegstationen und Journalstationen werden von dieser Methode nicht unterstützt.</p> |
| OPOS    | <p> Unterstützt alle OPOS-kompatiblen Belegdrucker über OPOS-Dienstobjekte. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers. </p> |

### <a name="stationary-receipt-printers-networkbluetooth"></a>Stationäre Belegdrucker (Netzwerk/ Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |   TM-T88V, TM-T70, TM-T20, TM-U220 |

### <a name="mobile-receipt-printers-bluetooth"></a>Mobile Belegdrucker (Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |   Mobilink P20 (TM-P20), Mobilink P60 (TM-P60), Mobilink P80 (TM-P80) |
