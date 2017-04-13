---
author: mukin
title: POS-Drucker
description: "Dieser Artikel enthält Informationen zur Gerätefamilie der Point of Service-Drucker."
ms.author: wdg-dev-content
ms.date: 02/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: d8340af651157bb6fae82785812f259c16d0a6c0
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="pos-printer"></a>POS-Drucker

Ermöglicht Anwendungsentwicklern das Drucken auf über das Netzwerk und Bluetooth verbundenen [Belegdruckern](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.posprinter) mithilfe der Epson ESC/POS-Druckersteuerungssprache.

## <a name="requirements"></a>Anforderungen
Für Anwendungen, die diesen Namespace erfordern, muss dem App-Paketmanifest die [DeviceCapability](https://msdn.microsoft.com/library/4353c4fd-f038-4986-81ed-d2ec0c6235ef) “pointOfService” hinzugefügt werden.

## <a name="device-support"></a>Unterstützung von Geräten
Windows unterstützt die Möglichkeit, auf über das Netzwerk und Bluetooth verbundenen Belegdruckern mithilfe der Epson ESC/POS-Druckersteuerungssprache zu drucken. Weitere Informationen zu ESC/POS finden Sie unter [Epson ESC/POS mit Formatierung](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/epson-esc-pos-with-formatting).

Während die Klassen, Enumerationen und Schnittstellen, die in der API verfügbar gemacht werden, sowohl Belegdrucker als auch Kassenbelegdrucker und Journaldrucker unterstützen, unterstützt die Treiberschnittstelle nur Belegdrucker. Der Versuch, zu diesem Zeitpunkt einen Kassenbelegdrucker oder Journaldrucker zu verwenden, gibt einen Nicht implementiert-Status zurück.

Der Support ist derzeit auf die Netzwerk- und Bluetooth-Gerätemodellen in den folgenden Tabellen beschränkt. Über USB verbundene Drucker werden derzeit nicht unterstützt. Überprüfen Sie zu einem späteren Zeitpunkt, ob weiterer Support hinzugefügt wurde.

### <a name="stationary-pos-printers-network-bluetooth"></a>Stationäre POS-Drucker (Netzwerk, Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |    TM-T88V, TM-T70, TM-T20, TM-U220 |

### <a name="mobile-pos-printers-bluetooth"></a>Mobile POS-Drucker (Bluetooth)
| Hersteller |    Model(le) |
|--------------|-----------|
| Epson |    Mobilink P20 (TM-P20), Mobilink P60 (TM-P60), Mobilink P80 (TM-P80) |

## <a name="examples"></a>Beispiele
Zeigen Sie das POS-Druckerbeispiel für eine Beispielimplementierung an.
+ [POS-Druckerbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/PosPrinter)
