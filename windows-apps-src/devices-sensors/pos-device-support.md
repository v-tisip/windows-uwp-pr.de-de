---
author: mukin
title: "Unterstützung für POS-Geräte"
description: "Dieser Artikel liefert Informationen zur Unterstützung für jede POS-Gerätefamilie"
ms.author: mukin
ms.date: 05/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 58018385082f7f7e49edba0351d919bc840ade05
ms.sourcegitcommit: 53930c9871461f6106f785ae4fabb2296eb359f1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2017
---
# <a name="pos-device-support"></a>Unterstützung für POS-Geräte

## <a name="barcode-scanner"></a>Strichcodescanner
| Konnektivität | Support |
| -------------|-------------|
| USB          | <p>Windows enthält für USB-verbundene Strichcodescanner einen integrierten Klassentreiber, dessen Spezifikation auf der von der [USB.org](http://www.usb.org/developers/hidpage/) definierten HID POS-Scanner-Nutzungstabelle (8c) basiert. Eine Liste bekannter kompatibler Geräte finden Sie in folgender Tabelle.  Sehen Sie im Handbuch Ihres Strichcodescanners nach oder wenden Sie sich an den Hersteller, um zu erfahren, ob Ihr Scanner im „USB.HID.POS“-Scannermodus konfiguriert werden kann. </p><p>Windows unterstützt auch die Implementierung von herstellerspezifischen Treibern für weitere Strichcodescanner, die den Scannerstandard „USB.HID.POS“ nicht unterstützen. Erfragen Sie beim Hersteller Ihres Strichcodescanners, ob ein herstellerspezifischer Treiber verfügbar ist.</p>|
| Bluetooth    | <p>Windows unterstützt SPP-SSI-basierte Bluetooth-Strichcodescanner. Eine Liste bekannter kompatibler Geräte finden Sie in folgender Tabelle.</p> |

### <a name="compatible-hardware"></a>Kompatible Hardware
| Kategorie | Konnektivität | Hersteller/ Modell |
|--------------|-----------|-----------|
| **1D-Handheld-Scanner** | **USB** |Honeywell Voyager 1200g<br/>Honeywell Voyager 1202g<br/>Honeywell Voyager 1202-bf<br/>Honeywell Voyager 145Xg (Aktualisierbar)|
| **1D-Handheld-Scanner** | **Bluetooth** |Socket Mobile CHS 7Ci<br/> Socket Mobile CHS 7Di<br/> Socket Mobile CHS 7Mi<br/> Socket Mobile CHS 7Pi<br/>Socket Mobile DuraScan D700<br/> Socket Mobile DuraScan D730<br/>Socket Mobile SocketScan S800 (ehemals CHS 8Ci) <br/>|
|**2D-Handheld-Scanner** | **USB** |Code Reader™ 950<br/>Code Reader™ 1021<br/>Code Reader™ 1421<br/> Honeywell Granit 198Xi<br/>Honeywell Granit 191Xi<br/>Honeywell Xenon 1900g<br/>Honeywell Xenon 1902g<br/>Honeywell Xenon 1902g-bf<br/>Honeywell Xenon 1900h<br/>Honeywell Xenon 1902h<br/>Honeywell Voyager 145Xg (Aktualisierbar)<br/>Honeywell Voyager 1602g<br/>Intermec SG20|
|**2D-Handheld-Scanner** | **Bluetooth** |Socket Mobile SocketScan S850 (ehemals CHS 8Qi)|
| **Präsentationsscanner** | **USB** |Code Reader™ 5000<br/>Honeywell Genesis 7580g<br/>Honeywell Orbit 7190g|
| **Kassentisch-Scanner** | **USB** |Honeywell Stratos 2700|
| **Scan-Module** | **USB** | Honeywell N5680<br/>Honeywell N3680|
| **Windows-Mobilgeräte**| **Integrierte** |Bluebird EF400<br/>Bluebird EF500<br/>Bluebird EF500R<br/>Honeywell CT50<br/>Honeywell D75e<br/>Janam XT2<br/>Panasonic FZ-E1<br/>Panasonic FZ-F1<br/>PointMobile PM80<br/>Zebra TC700j|
| **Windows-Mobilgeräte**| **„Benutzerdefiniert“** | HP Elite X3 mit Strichcodescannerhülle |

## <a name="cash-drawer"></a>Kassenschublade
| Konnektivität | Support |
| -------------|-------------|
| Netzwerk/Bluetooth | <p> Eine direkte Verbindung zur Kassenschublade kann über das Netzwerk oder über Bluetooth hergestellt werden, je nach den Funktionen der Kassenschublade. </p>|
| DK-Port | <p> Kassenschubladen ohne Netzwerk- oder Bluetooth-Funktionen können über den DK-Port auf unterstützten POS-Druckern oder das Star Micronics DK-AirCash-Zubehör verbunden werden. </p>
| OPOS    | <p> Unterstützt alle Kassenschubladengeräte, die OPOS-Treiber unterstützen und/oder OPOS-Objekte enthalten. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers. Dadurch werden USB- und andere auf Herstellerspezifikationen basierende Verbindungen ermöglicht. </p> |

**Hinweis:**  Weitere Informationen zu DK-AirCash erhalten Sie von Stern Micronics.

### <a name="networkbluetooth"></a>Netzwerk/Bluetooth
| Hersteller |    Model(le) |
|--------------|-----------|
| APG-Kassenschublade |    NetPRO, BluePRO |

## <a name="line-display"></a>Zeilenanzeige
Unterstützt alle Zeilenanzeigegeräte, die OPOS-Treiber unterstützen und/oder OPOS-Objekte enthalten. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers.

## <a name="magnetic-stripe-reader"></a>Magnetstreifenleser

Windows enthält für USB-verbundene Magnetstreifenleser einen integrierten Klassentreiber, dessen Spezifikation auf der von [USB.org](http://www.usb.org/developers/hidpage/) definierten HID POS-Scanner-Nutzungstabelle (8 c) basiert.

### <a name="vendor-specific-support"></a>Herstellerspezifische Unterstützung
Windows bietet Unterstützung für die folgenden Magnetstreifenleser von Magtek und IDTech, basierend auf deren Anbieter-ID und Produkt-ID (VID/PID).

| Hersteller |     Model(le) |    Teilenummer |
|--------------|-----------|--------------|
| IDTech | SecureMag (VID:0ACD PID:2010) | IDRE-3x5xxxx |
| |    MiniMag (VID:0ACD PID:0500) |    IDMB-3x5xxxx |
| Magtek | MagneSafe (VID:0801 PID:0011) |    210730xx |
| |    Dynamag (VID:0801 PID:0002) |    210401xx |

### <a name="custom-vendor-specific"></a>Spezifisch für benutzerdefinierten Anbieter
Windows unterstützt die Implementierung der zusätzlichen anbieterspezifischen Treiber zur Unterstützung von Magnetstreifenlesern. Bitte prüfen Sie die Verfügbarkeit des Magnetstreifenlesers bei Ihrem Hersteller.

## <a name="pos-printer"></a>POS-Drucker
Windows unterstützt die Möglichkeit, mit der Epson ESC/POS-Druckersteuerungssprache auf Belegdruckern über Netzwerk und Bluetooth zu drucken. Weitere Informationen zu ESC/POS finden Sie unter [Epson ESC/POS mit Formatierung](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/epson-esc-pos-with-formatting).

Obwohl die in der API angezeigten Klassen, Enumerationen und Schnittstellen alle Beleg-, Quittungs- und Journaldrucker unterstützen, werden von der Treiberschnittstelle nur Belegdrucker unterstützt. Der Versuch, andere Druckertypen zu verwenden, führt derzeit zu der Statusmeldung „nicht implementiert“.

| Konnektivität | Support |
| -------------|-------------|
| Netzwerk/Bluetooth | <p> Eine Direktverbindung zum POS-Drucker kann, abhängig von dessen Funktionen, über Netzwerk oder Bluetooth hergestellt werden. </p>|
| OPOS    | <p> Unterstützt alle POS-Drucker, die OPOS-Treiber unterstützen, und/oder stellt OPOS-Objekte bereit. Installieren Sie die OPOS-Treiber für das Gerät entsprechend den Anweisungen des Herstellers. Dadurch werden USB- und andere auf Herstellerspezifikationen basierende Verbindungen ermöglicht. </p> |

### <a name="stationary-pos-printers-networkbluetooth"></a>Stationäre POS-Drucker (Netzwerk/ Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |    TM-T88V, TM-T70, TM-T20, TM-U220 |

### <a name="mobile-pos-printers-bluetooth"></a>Mobile POS-Drucker (Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |    Mobilink P20 (TM-P20), Mobilink P60 (TM-P60), Mobilink P80 (TM-P80) |