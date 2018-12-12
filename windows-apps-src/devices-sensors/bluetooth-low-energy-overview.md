---
title: Bluetooth Low Energy
description: Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps.
ms.date: 03/15/2017
ms.topic: article
keywords: Windows 10, Uwp, Bluetooth, Bluetooth LE, low Energy, Gatt, Lücke, zentralen, Peripheriegerät, Client, Server, Überwachung, publisher
ms.localizationpriority: medium
ms.openlocfilehash: ecc78bd4bb079adbaaa58c981ce55457c522764b
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8938122"
---
# <a name="bluetooth-low-energy"></a>Bluetooth Low Energy
Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle zur Ermittlung und die Kommunikation zwischen energieeffizienten Geräten definiert. Erkennung von Geräten erfolgt über das generische Zugriff Profil (Abstand)-Protokoll. Nach der Erkennung erfolgt Gerät-Kommunikation über das Generic Attribut (GATT)-Protokoll. Dieses Thema enthält eine kurze Übersicht über Bluetooth LE in UWP-apps. Weitere Details zu Bluetooth LE finden Sie unter den [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification) Version 4.0, bei dem Bluetooth LE eingeführt wurde. 

![Bluetooth LE-Rollen](images/gatt-roles.png)

*GATT und Lücke Rollen wurden in Windows 10, Version 1703 eingeführt.*

GATT und Lücke Protokolle können mit den folgenden Namespaces in Ihre UWP-app implementiert werden.
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)

## <a name="central-and-peripheral"></a>Zentralen und Peripheriegeräte
Die zwei primären Rollen der Erkennung werden zentral- und Peripheriegerät aufgerufen. Im allgemeinen Windows wird im zentralen Modus ausgeführt und stellt eine Verbindung mit verschiedenen Peripheriegeräte. 

## <a name="attributes"></a>Attribute
Eine allgemeine Abkürzung, die Sie in der Windows-Bluetooth-APIs sehen können, ist Generic Attribut (GATT). Das GATT-Profil definiert die Struktur der Daten und Betriebsmodi, die über die beiden Bluetooth LE-Geräten kommunizieren. Das Attribut ist der wichtigsten Baustein der GATT. Die wichtigsten Attribute sind Diensten, Merkmalen und Deskriptoren. Diese Attribute führen unterschiedlich zwischen Clients und Servern, daher es sinnvoller ist, die Aktivität in den entsprechenden Abschnitten erläutert. 

![Typische Attributhierarchie in ein gemeinsames Profil](images/gatt-service.png)

*Der Dienst Herzfrequenz wird in Form von GATT-Server-API ausgedrückt.*

## <a name="client-and-server"></a>Client und Server
Nachdem eine Verbindung hergestellt wurde, wird das Gerät mit den Daten (in der Regel eine kleine IoT-Sensor oder Wearable) als Server bezeichnet. Das Gerät, das diese Daten verwendet, um eine Funktion wird wie der Client bezeichnet. Ein Windows-PC (Client) liest z. B. Daten aus einem Herzfrequenz Monitor (Server), um nachzuverfolgen, ob ein Benutzer optimal funktioniert. Weitere Informationen finden Sie unter den Themen [GATT-Client](gatt-client.md) und [GATT-Server](gatt-server.md) .

## <a name="watchers-and-publishers-beacons"></a>Beobachter und Herausgeber (Beacons)
Zusätzlich zu der zentralen und Peripheriegerät Rollen sind Observer und Sender Rollen. Sendeanstalten häufig als Beacons bezeichnet werden, kommunizieren nicht sie über GATT, da sie in der Ankündigung-Paket bereitgestellt werden, für die Kommunikation begrenzten Rahmen zu verwenden. Auf ähnliche Weise eine Helligkeitsstufen hat keinen zum Herstellen einer Verbindung zum Empfangen von Daten aus, und in der Nähe Ankündigungen scannt. Verwenden Sie die [BluetoothLEAdvertisementWatcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher) -Klasse, um Windows zu sehen, in der Nähe Werbung zu konfigurieren. Verwenden Sie die [BluetoothLEAdvertisementPublisher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher) -Klasse, um die Beacon-Nutzlasten zu übertragen. Weitere Informationen finden Sie unter dem Thema [Ankündigung](ble-beacon.md) .

## <a name="see-also"></a>Siehe auch
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Bluetooth-Core-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification)