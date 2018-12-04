---
title: Bluetooth Low Energy
description: Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps.
ms.date: 03/15/2017
ms.topic: article
keywords: Windows 10, Uwp, Bluetooth, Bluetooth LE, low Energy, Gatt, Lücke, Central, Peripheriegerät, Client, Server, Überwachung, publisher
ms.localizationpriority: medium
ms.openlocfilehash: 3853003e54e58b3949c248fb03cb0a83e2d6d112
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8466413"
---
# <a name="bluetooth-low-energy"></a>Bluetooth Low Energy
Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle für die Erkennung und Kommunikation zwischen energieeffizienten Geräten definiert. Erkennung von Geräten erfolgt über das Protokoll generischer Zugriff Profil (Abstand). Nach der Erkennung erfolgt-Gerät-Kommunikation über das Generic Attribut (GATT)-Protokoll. Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps. Weitere Details zu Bluetooth LE finden Sie unter den [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification) Version 4.0, bei dem Bluetooth LE eingeführt wurde. 

![Bluetooth LE-Rollen](images/gatt-roles.png)

*GATT und Abstand Rollen wurden in Windows 10, Version 1703 eingeführt.*

GATT und Abstand Protokolle können mithilfe der folgenden Namespaces in Ihre UWP-app implementiert werden.
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)

## <a name="central-and-peripheral"></a>Zentrale und Peripheriegeräte
Die zwei primären Rollen der Erkennung werden Central und Peripheriegerät bezeichnet. Im allgemeinen Windows wird im zentralen Modus ausgeführt und stellt eine Verbindung mit verschiedenen Peripheriegeräte. 

## <a name="attributes"></a>Attribute
Eine allgemeine Abkürzung sehen Sie in den Windows-Bluetooth-APIs ist Generic Attribut (GATT). Das GATT-Profil definiert die Struktur der Daten und Betriebsmodi, die über die beiden Bluetooth LE-Geräten kommunizieren. Das Attribut ist der wichtigste Baustein der GATT. Die wichtigsten Attribute sind Diensten, Merkmalen und Deskriptoren. Diese Attribute führen unterschiedlich zwischen Clients und Servern, daher es sinnvoller ist, um ihre Interaktion in den entsprechenden Abschnitten erläutert. 

![Typische Attribut Hierarchie in ein gemeinsames Profil](images/gatt-service.png)

*Der Herzfrequenz-Dienst wird im GATT-Server-API-Formular ausgedrückt.*

## <a name="client-and-server"></a>Client und Server
Nachdem eine Verbindung hergestellt wurde, wird der Server das Gerät mit den Daten (in der Regel eine kleine IoT-Sensor oder Wearable) genannt. Das Gerät, das diese Daten verwendet, um eine Funktion wird als Client bezeichnet. Ein Windows-PC (Client) liest z. B. Daten aus einem Herzfrequenz Monitor (Server), um nachzuverfolgen, ob ein Benutzer optimal funktioniert. Weitere Informationen finden Sie unter den Themen [GATT-Client](gatt-client.md) und [GATT-Server](gatt-server.md) .

## <a name="watchers-and-publishers-beacons"></a>Beobachter und Herausgeber (Beacons)
Zusätzlich zu den Rollen Central und Peripheriegeräte werden Observer und Sender Rollen. Sendeanstalten häufig als Beacons bezeichnet werden, kommunizieren nicht sie über GATT, da sie im Paket Ankündigung bereitgestellt, für die Kommunikation begrenzten Rahmen zu verwenden. Auf ähnliche Weise eine Observer hat keinen zum Herstellen einer Verbindung zum Empfangen von Daten und scannt nach in der Nähe Werbung. Verwenden Sie die [BluetoothLEAdvertisementWatcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher) -Klasse, um Windows zu sehen, in der Nähe Werbung zu konfigurieren. Verwenden Sie die [BluetoothLEAdvertisementPublisher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher) -Klasse, um die Beacon-Nutzlasten zu senden. Weitere Informationen finden Sie im Thema [Ankündigung](ble-beacon.md) .

## <a name="see-also"></a>Siehe auch
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification)