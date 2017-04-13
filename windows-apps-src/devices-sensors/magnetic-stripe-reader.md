---
author: mukin
title: Magnetstreifenleser
description: "Dieser Artikel enthält Informationen über die Magnetstreifenleser-Point of Service-Gerätefamilie"
ms.author: wdg-dev-content
ms.date: 02/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: a11fe7a63c0444ac986e7bfe0d50472249e5196e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="magnetic-stripe-reader"></a>Magnetstreifenleser

Ermöglicht Anwendungsentwicklern den Zugriff auf [Magnetstreifenleser](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.magneticstripereader) zum Abrufen von Daten aus für Magnetstreifen aktivierten Karten, z.B. Kreditkarten, Treuekarten, Zugangskarten usw.

## <a name="requirements"></a>Anforderungen
Für Anwendungen, die diesen Namespace erfordern, muss dem App-Paketmanifest der „pointOfService“ [DeviceCapability](https://msdn.microsoft.com/library/4353c4fd-f038-4986-81ed-d2ec0c6235ef) hinzugefügt werden.

## <a name="device-support"></a>Unterstützung von Geräten
### <a name="usb"></a>USB
### <a name="supported-vendor-specific"></a>Wird anbieterspezifisch unterstützt
Windows bietet Unterstützung für die folgenden Magnetstreifenleser von Magtek und IDTech basierend auf der Anbieter-ID und der Produkt-ID (VID/PID).

| Hersteller |     Model(le) |    Teilenummer |
|--------------|-----------|--------------|
| IDTech | SecureMag (VID:0ACD PID:2010) | IDRE-3x5xxxx |
| |    MiniMag (VID:0ACD PID:0500) |    IDMB-3x5xxxx |
| Magtek | MagneSafe (VID:0801 PID:0011) |    210730xx |
| |    Dynamag (VID:0801 PID:0002) |    210401xx |

### <a name="custom-vendor-specific"></a>Spezifisch für benutzerdefinierten Anbieter
Windows unterstützt die Implementierung der zusätzlichen anbieterspezifischen Treiber zur Unterstützung von Magnetstreifenlesern. Überprüfen Sie die Verfügbarkeit beim Hersteller des Magnetstreifenlesers.

## <a name="examples"></a>Beispiele
Sehen Sie sich das Beispiel des Magnetstreifenlesers und eine Beispielimplementierung an.
+    [Magnetstreifenleserbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
