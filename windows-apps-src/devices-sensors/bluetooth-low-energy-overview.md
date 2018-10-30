---
author: msatranjr
title: Bluetooth Low Energy
description: Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps.
ms.author: misatran
ms.date: 03/15/2017
ms.topic: article
keywords: Windows 10, Uwp, Bluetooth, Bluetooth LE, low Energy, Gatt, Lücke, Central, Peripheriegerät, Client, Server, Überwachung, publisher
ms.localizationpriority: medium
ms.openlocfilehash: 9e5bef16c76ee14c2abb7a5a41ab02d150a97333
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5815907"
---
# <a name="bluetooth-low-energy"></a>Bluetooth Low Energy
Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle zur Ermittlung und Kommunikation zwischen energieeffizienten Geräten definiert. Erkennung von Geräten erfolgt über das Protokoll generischer Zugriff Profil (Abstand). Nach der Erkennung erfolgt-Gerät-Kommunikation über das Generic Attribut (GATT)-Protokoll. Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps. Weitere Details zu Bluetooth LE finden Sie unter den [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification) Version 4.0, bei dem Bluetooth LE eingeführt wurde. 

![Bluetooth LE-Rollen](images/gatt-roles.png)

*GATT und Lücke Rollen wurden in Windows 10, Version 1703 eingeführt.*

GATT und Lücke Protokolle können mithilfe der folgenden Namespaces in Ihre UWP-app implementiert werden.
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)

## <a name="central-and-peripheral"></a>Zentrale und Peripheriegeräte
Die zwei primären Rollen für das Auffinden von heißen zentral- und Peripheriegeräte. Im allgemeinen Windows arbeitet im zentralen Modus und stellt eine Verbindung mit verschiedenen Peripheriegeräte. 

## <a name="attributes"></a>Attribute
Eine allgemeine Abkürzung sehen Sie in den Windows-Bluetooth-APIs ist Generic Attribut (GATT). Das GATT-Profil definiert die Struktur der Daten und Betriebsmodi über die beiden Bluetooth LE-Geräten kommunizieren. Das Attribut ist der wichtigste Baustein der GATT. Die Haupttypen von Attributen sind Diensten, Merkmalen und Deskriptoren. Diese Attribute führen unterschiedlich zwischen Clients und Servern, daher es sinnvoller ist, um ihre Interaktion in den entsprechenden Abschnitten erläutert. 

![Typische Attribut Hierarchie in ein gemeinsames Profil](images/gatt-service.png)

*Der Dienst Herzfrequenz wird im GATT-Server-API-Formular ausgedrückt.*

## <a name="client-and-server"></a>Clients und-Servers
Nachdem eine Verbindung hergestellt wurde, wird das Gerät mit den Daten (in der Regel einen kleinen IoT-Sensor oder Wearable) als Server bezeichnet. Das Gerät, das diese Daten zur Durchführung einer Funktion verwendet wird als Client bezeichnet. Einen Windows-PC (Client) liest z. B. Daten aus einem Herzfrequenz Monitor (Server), um nachzuverfolgen, ob ein Benutzer optimal funktioniert. Weitere Informationen finden Sie unter den Themen [GATT-Client](gatt-client.md) und [GATT-Server](gatt-server.md) .

## <a name="watchers-and-publishers-beacons"></a>Beobachter und Herausgeber (Beacons)
Zusätzlich zu den Rollen Central und Peripheriegerät stehen Observer und Sender Rollen. Sendeanstalten häufig als Beacons bezeichnet werden, kommunizieren nicht er über GATT, da sie für die Kommunikation in das Paket Ankündigung bereitgestellten begrenzten Rahmen zu verwenden. Auf ähnliche Weise eine Observer hat keinen zum Herstellen einer Verbindung zum Empfangen von Daten und scannt nach in der Nähe Werbung. Verwenden Sie die [BluetoothLEAdvertisementWatcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher) -Klasse, um Windows zu sehen, in der Nähe Werbung zu konfigurieren. Verwenden Sie die [BluetoothLEAdvertisementPublisher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher) -Klasse, um Beacon-Nutzlasten zu senden. Weitere Informationen finden Sie im Thema [Ankündigung](ble-beacon.md) .

## <a name="see-also"></a>Siehe auch
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification)