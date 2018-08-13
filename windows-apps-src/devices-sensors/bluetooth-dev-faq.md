---
author: msatranjr
title: Bluetooth-Entwickler – Häufig gestellte Fragen
description: Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu den UWP-Bluetooth-APIs.
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: e7dee32d-3756-430d-a026-32c1ee288a85
ms.localizationpriority: medium
ms.openlocfilehash: c0af6a19e17a62ed82c32e68ea1732e1f51d4641
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "301930"
---
# <a name="bluetooth-developer-faq"></a>Bluetooth-Entwickler – Häufig gestellte Fragen

Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu UWP-Bluetooth-APIs.

## <a name="what-apis-do-i-use-bluetooth-classic-rfcomm-or-bluetooth-low-energy-gatt"></a>Welche APIs werden verwendet? Bluetooth-Classic (RFCOMM) oder Bluetooth niedriger Energie (GATT)?
Wir halten Sie über diese Antwort herum in den Unterschied im Hinblick auf Windows online verschiedenen Diskussionen, um diese allgemeinen Thema stehen. Es folgen einige allgemeinen Richtlinien:

### <a name="bluetooth-le-windowsdevicesbluetoothgenericattributeprofile"></a>Bluetooth LE (Windows.Devices.Bluetooth.GenericAttributeProfile)

Verwenden Sie die GATT-APIs, wenn Sie ein Gerät kommunizieren, die Bluetooth niedriger Energie unterstützt. Wenn Sie sind Fall seltene, niedriger Bandbreite oder Energiesparmodus erfordert, Bluetooth niedriger Energie ist die Antwort. Der wichtigste Namespace, der dieser Funktionalität gehören ist [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Bluetooth.GenericAttributeProfile). 

**Wann nicht Bluetooth LE verwenden**
- Hoher Bandbreite Szenarien besonders Häufigkeit. Sie müssen ständig mit großen Datenmengen synchronisieren lassen, sollten Sie Bluetooth klassische oder vielleicht gerade WiFi verwenden. 

### <a name="bluetooth-classic-windowsdevicesbluetoothrfcomm"></a>Bluetooth-Classic (Windows.Devices.Bluetooth.Rfcomm)

Die RFCOMM-APIs können Entwickler einen Socket Bi-Richtung seriellen Anschluss Formatvorlage Kommunikation ausführen. Nachdem Sie einen Socket haben, sind die Methoden zum Schreiben und Lesen von daraus relativ standard. Eine Implementierung dieses wird in der [Rfcomm Chat Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BluetoothRfcommChat)dargestellt. 

**Wann nicht Bluetooth Rfcomm verwenden** 
- Benachrichtigungen. Das Protokoll Bluetooth GATT wurde von einem bestimmten Befehl für diese und deutlich weniger Strom zeichnen und schnellere Antwortzeiten, bewirken. 
- Überprüfen für die Erkennung Nähe oder Anwesenheit. Verwenden Sie die [Ankündigung-APIs](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement) und eine Verbindung herstellen, über Bluetooth LE besser. 


## <a name="why-does-my-bluetooth-le-device-stop-responding-after-a-disconnect"></a>Warum reagiert mein Bluetooth LE-Gerät nach einem Trennvorgang nicht mehr?

Der häufigste Grund besteht darin, dass die Kopplungsinformationen auf dem Remotegerät verloren gegangen sind. Viele ältere Bluetooth-Geräte erfordern keine Authentifizierung. Zum Schutz des Benutzers erfordern alle über die Einstellungs-App ausgeführten Kopplungsversuche eine Authentifizierung. Einige Geräte sind dafür nicht ausgelegt. 

Ab Windows 10, Version 1511, haben Entwickler Kontrolle über den Kopplungsvorgang. Im [Beispiel für die Geräteenumeration und -kopplung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/DeviceEnumerationAndPairing) werden verschiedene Aspekte beim Zuordnen neuer Geräte erörtert.

In diesem Beispiel wird die Kopplung mit einem Gerät ohne Verschlüsselung initiiert. Dies funktioniert allerdings nur, wenn das Remotegerät keine Verschlüsselung oder Authentifizierung erfordert.

```csharp
// Get ceremony type and protection level selections
// You must select at least ConfirmOnly or the pairing attempt will fail
    DevicePairingKinds ceremonySelected = DevicePairingKinds.ConfirmOnly;

//  Workaround remote devices losing pairing information
    DevicePairingProtectionLevel protectionLevel = DevicePairingProtectionLevel.None

    DeviceInformationCustomPairing customPairing = deviceInfoDisp.DeviceInformation.Pairing.Custom;

// Declare an event handler - you don't need to do much in PairingRequestedHandler since the ceremony is "None"
    customPairing.PairingRequested += PairingRequestedHandler;
    DevicePairingResult result = await customPairing.PairAsync(ceremonySelected, protectionLevel);
```

## <a name="do-i-have-to-pair-bluetooth-devices-before-using-them"></a>Muss ich Bluetooth-Geräte vor der Verwendung koppeln?

Bei Bluetooth RFCOMM (Classic)-Geräten ist dies nicht erforderlich. Ab Windows 10, Version 1607, können Sie einfach Geräte in der Nähe suchen und eine Verbindung herstellen. Das aktualisierte [RFCOMM Chat-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BluetoothRfcommChat) veranschaulicht diese Funktionalität. 

**(14393 und unten)** Dieses Feature ist nicht verfügbar für Bluetooth niedriger Energie (GATT-Client), damit Sie weiterhin Paar entweder über die Einstellungsseite oder verwenden die [Windows.Devices.Enumeration](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.aspx) APIs in Reihenfolge Access diese Geräte verfügen.

**(15030 und höher)** Eine Kopplung Bluetooth-Geräte ist nicht mehr erforderlich. Verwendung der neuen Async APIs wie GetGattServicesAsync und GetCharacteristicsAsync, um den aktuellen Status des Geräts, remote abgefragt wird. Finden Sie weitere Details der [Client-Dokumente](gatt-client.md) . 

## <a name="when-should-i-pair-with-a-device-before-communicating-with-it"></a>Wann sollte ich mit einem Gerät Kopplung, vor der Kommunikation mit es?
Im Allgemeinen, wenn Sie einen vertrauenswürdigen, langfristige Wertpapier mit einem Gerät benötigen, Paarung (leitet den Benutzer zur Einstellungsseite oder unter Verwendung des Geräte-Enumeration und eine Kopplung APIs). Wenn Sie lediglich zum Lesen von Informationen aus werden Sie das Gerät, die verfügbar gemacht öffentlich (Temperatursensor oder Signal), eine Verbindung herstellen Sie oder warten Sie anzeigen, ohne dass eine beliebige Aufwand mit dem Gerät ein. Dies verhindert Interoperabilitätsprobleme langfristig, da eine Vielzahl von Geräten unterstützen keine Verbindung. 

## <a name="do-all-windows-devices-support-peripheral-role"></a>Werden alle Windows-Geräte peripherer Rolle unterstützt?

Nein – dies ist ein abhängigen Hardware-Feature, aber eine Methode dient (BluetoothAdapter.IsPeripheralRoleSupported) zur Abfrage, ob es oder nicht unterstützt wird.  Derzeit unterstützte Geräten zählen Windows Phone 8992 + und RPi3 (Windows IoT). 

## <a name="can-i-access-these-apis-from-win32"></a>Kann ich diese APIs in Win32 zugreifen?

Ja, sollte alle diese APIs funktionieren. In diesem Blog werden die Möglichkeit zum Aufrufen von [Windows-APIs von desktopanwendungen](https://blogs.windows.com/buildingapps/2017/01/25/calling-windows-10-apis-desktop-application/). 
## <a name="is-this-functionality-supposed-to-exist-on--insert-sku-here-"></a>Sollte diese Funktionalität auf *- Hier einfügen SKU -* vorhanden?

**Bluetooth-LE**: Ja, alle Funktionen in OneCore ist und auf die letzte Geräte mit einer funktionierenden LE Bluetooth-Stapel verfügbar sein sollten. 
> Einschränkung: Peripherer Rolle ist abhängig von der Hardware, und einige Editionen von Windows Server unterstützen keine Bluetooth. 

**Bluetooth-BR/EDR (klassisch)**: großen und sehr ähnlich Profil Unterstützung verfügen jedoch einige Variationen vorhanden. Finden Sie die Dokumente auf [RFCOMM](send-or-receive-files-with-rfcomm.md) und diese Dokumente unterstützte Profil für [PC](https://support.microsoft.com/en-us/help/10568/windows-10-supported-bluetooth-profiles) und [Telefon](https://support.microsoft.com/en-us/help/10569/windows-10-mobile-supported-bluetooth-profiles)

