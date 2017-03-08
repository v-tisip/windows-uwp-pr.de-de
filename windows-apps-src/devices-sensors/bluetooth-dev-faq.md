---
author: msatranjr
title: "Bluetooth-Entwickler – Häufig gestellte Fragen"
description: "Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu den UWP-Bluetooth-APIs."
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
ms.assetid: e7dee32d-3756-430d-a026-32c1ee288a85
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 7394d211b580ad82689a79e7cbe4eb4dbf545f46
ms.lasthandoff: 02/08/2017

---
# <a name="bluetooth-developer-faq"></a>Bluetooth-Entwickler – Häufig gestellte Fragen

Dieser Artikel bietet Antworten auf häufig gestellte Fragen zu UWP-Bluetooth-APIs.

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

Da dieses Feature für Bluetooth Low Energy (GATT-Client) nicht verfügbar ist, müssen diese Geräte immer noch über die Einstellungsseite oder mithilfe der [Windows.Devices.Enumeration](https://msdn.microsoft.com/en-us/library/windows/apps/windows.devices.enumeration.aspx)-APIs gekoppelt werden, damit Sie darauf zugreifen können.


