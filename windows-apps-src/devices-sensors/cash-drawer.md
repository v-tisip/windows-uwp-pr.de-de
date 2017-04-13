---
author: mukin
title: Kassenschublade
description: "Dieser Artikel enthält Informationen zur Gerätefamilie der Point of Service-Kassenschublade."
ms.author: wdg-dev-content
ms.date: 02/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 
ms.openlocfilehash: 376272356cf720ddd9519f0077e771a1016abb1e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="cash-drawer"></a>Kassenschublade

Ermöglicht Anwendungsentwicklern die Interaktion mit [Kassenschubladen](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.cashdrawer).

## <a name="requirements"></a>Anforderungen
Für Anwendungen, die diesen Namespace erfordern, muss dem App-Paketmanifest die [DeviceCapability](https://msdn.microsoft.com/library/4353c4fd-f038-4986-81ed-d2ec0c6235ef) "pointOfService" hinzugefügt werden.

## <a name="device-support"></a>Unterstützung von Geräten
Eine direkte Verbindung zur Kassenschublade kann über das Netzwerk oder über Bluetooth hergestellt werden, je nach den Funktionen der Kassenschublade. Darüber hinaus können Kassenschubladen, die über keine Netzwerk- oder Bluetooth-Funktion verfügen, über den DK-Port auf einem unterstützten POS-Drucker oder das Star Micronics DK-AirCash-Zubehör verbunden werden. Zurzeit besteht keine Unterstützung für Kassenschubladen, die über USB oder den seriellen Anschluss verbunden sind.

**Hinweis:** Bei Stern Micronics erhalten Sie weitere Informationen zu DK-AirCash.

### <a name="networkbluetooth"></a>Netzwerk/Bluetooth
| Hersteller |    Model(le) |
|--------------|-----------|
| APG-Kassenschublade |    NetPRO, BluePRO |

## <a name="examples"></a>Beispiele
Im Beispiel für Kassenschublade finden Sie ein Beispiel einer Implementierung.
+    [Beispiel für Kassenschublade](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CashDrawer)
