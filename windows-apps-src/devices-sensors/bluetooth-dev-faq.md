---
title: Bluetooth-Entwickler – Häufig gestellte Fragen
description: Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu den UWP-Bluetooth-APIs.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: e7dee32d-3756-430d-a026-32c1ee288a85
ms.localizationpriority: medium
ms.openlocfilehash: 4cc1bafb90b20083d55a622873dea7be5efbf5b7
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8789511"
---
# <a name="bluetooth-developer-faq"></a>Bluetooth-Entwickler – Häufig gestellte Fragen

Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu UWP-Bluetooth-APIs.

## <a name="what-apis-do-i-use-bluetooth-classic-rfcomm-or-bluetooth-low-energy-gatt"></a>Welche APIs können werden verwendet? Bluetooth-klassische (RFCOMM) oder Bluetooth Low Energy (GATT)?
Wir halten diese Antwort weisen auf den Unterschied in Bezug auf die Windows sind verschiedene Diskussionen online um allgemeine in diesem Thema. Hier sind einige allgemeinen Richtlinien:

### <a name="bluetooth-le-windowsdevicesbluetoothgenericattributeprofile"></a>Bluetooth LE (Windows.Devices.Bluetooth.GenericAttributeProfile)

Verwenden Sie die GATT-APIs, wenn Sie mit einem Gerät kommunizieren, die von Bluetooth Low Energy unterstützt. Wenn Sie sind selten, geringer Bandbreite ist oder mit geringem Energieverbrauch erfordert, Bluetooth Low Energy die Antwort ist. Die wichtigste Namespace, der diese Funktion enthält, [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Bluetooth.GenericAttributeProfile)ist. 

**Wenn nicht auf Bluetooth LE**
- Hohe Bandbreite und hoher Frequenz Szenarien. Wenn Sie ständig mit großen Mengen von Daten synchron halten müssen, sollten Sie Bluetooth klassische oder vielleicht sogar WLAN in Betracht ziehen. 

### <a name="bluetooth-classic-windowsdevicesbluetoothrfcomm"></a>Bluetooth-klassische (Windows.Devices.Bluetooth.Rfcomm)

Die RFCOMM-APIs können Entwickler einen Socket Bi-Richtung seriellen Anschluss Stil Kommunikation durchführen. Nachdem Sie einen Socket haben, sind die Methoden zum Schreiben und Lesen von daraus relativ standard. Eine Implementierung dieser wird in das [Rfcomm Chat-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/BluetoothRfcommChat)dargestellt. 

**Wenn nicht, um Bluetooth Rfcomm verwenden.** 
- Benachrichtigungen. Die Bluetooth GATT-Protokoll verfügt über einen bestimmten Befehl für dieses und führt zu deutlich weniger Leistungsaufnahme und kürzere Antwortzeiten. 
- Überprüfen die Näherung oder Vorhandensein zur Erkennung. Verwenden Sie die [Ankündigungs-APIs](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement) und Herstellen einer Verbindung über Bluetooth LE besser. 


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

**(14393 und unten)** Dieses Feature ist nicht verfügbar für Bluetooth Low Energy (GATT-Client), so dass Sie weiterhin auf Paar über die Einstellungsseite oder mithilfe der [Windows.Devices.Enumeration](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.aspx) APIs in der Reihenfolge Zugriff auf diesen Geräten.

**(15030 und höher)** Bluetooth-Geräte koppeln ist nicht mehr erforderlich. Verwenden Sie die neuen asynchronen APIs wie GetGattServicesAsync und GetCharacteristicsAsync, um den aktuellen Zustand des Geräts remote Abfragen. Finden Sie in der [Client-Dokumentation](gatt-client.md) für Weitere Informationen. 

## <a name="when-should-i-pair-with-a-device-before-communicating-with-it"></a>Wann sollte ich mit einem Gerät koppeln, bevor Sie mit ihm zu kommunizieren?
In der Regel, wenn Sie eine vertrauenswürdige, Long-term-Verbindung mit einem Gerät benötigen, Koppeln Sie, (Weiterleiten des Benutzers die Seite "Einstellungen" oder mithilfe der Geräteenumeration und die Kopplung APIs). Wenn Sie lediglich zum Lesen von Informationen aus Gerät öffentlich verfügbar gemacht (ein Temperatursensor oder Beacon), verbinden oder Lauschen Werbung ohne jegliches Zutun mit dem Gerät zu koppeln. Dies verhindert Probleme hinsichtlich der Interoperabilität langfristig, da eine Vielzahl von Geräten unterstützen nicht die Kopplung. 

## <a name="do-all-windows-devices-support-peripheral-role"></a>Werden alle Windows-Geräte werden Peripheriegeräte Rolle unterstützt?

Nein – dies ist eine abhängige Hardware-Funktion, sondern eine Methode wird (BluetoothAdapter.IsPeripheralRoleSupported) abgefragt, ob sie oder nicht unterstützt wird.  Aktuell unterstützte Geräte sind, Windows Phone 8992 + und RPi3 (Windows IoT). 

## <a name="can-i-access-these-apis-from-win32"></a>Kann ich diese APIs von Win32 zugreifen?

Ja, sollten alle diese APIs funktionieren. Die Möglichkeit zum Aufrufen der [Windows-APIs von Desktop-Apps](https://blogs.windows.com/buildingapps/2017/01/25/calling-windows-10-apis-desktop-application/)von diesem Blog details. 
## <a name="is-this-functionality-supposed-to-exist-on--insert-sku-here-"></a>Sollte diese Funktion auf *- Hier einfügen-SKU -* vorhanden?

**Bluetooth LE**: Ja, alle Funktionen in OneCore ist, und sollte auf die neuesten Geräte mit einem funktionierenden Bluetooth LE-Stapel verfügbar sein. 
> Einschränkung: Peripheriegeräte Rolle ist abhängig von der Hardware, und einige Editionen von Windows Server nicht Bluetooth unterstützt. 

**Bluetooth-BR/EDR (Classic)**: im großen und sehr ähnlich Ebene profilunterstützung verfügen jedoch einige Varianten vorhanden sind. Lesen Sie die Dokumentation auf [RFCOMM](send-or-receive-files-with-rfcomm.md) und diese Dokumente unterstütztes Profil für [PC](https://support.microsoft.com/en-us/help/10568/windows-10-supported-bluetooth-profiles) und [Telefon](https://support.microsoft.com/en-us/help/10569/windows-10-mobile-supported-bluetooth-profiles)

