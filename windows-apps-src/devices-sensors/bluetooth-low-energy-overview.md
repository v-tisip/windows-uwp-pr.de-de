---
author: msatranjr
title: Bluetooth Low Energy
description: Dieses Thema enthält eine kurze Übersicht über Bluetooth LE UWP-Apps.
ms.author: misatran
ms.date: 03/15/2017
ms.topic: article
keywords: Windows 10 Uwp Bluetooth, Bluetooth LE, niedrige Energie, Gatt, Abstand, Central, Peripheriegeräte, Client, Server, Monitor, publisher
ms.localizationpriority: medium
ms.openlocfilehash: 9e5bef16c76ee14c2abb7a5a41ab02d150a97333
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919128"
---
# <a name="bluetooth-low-energy"></a>Bluetooth Low Energy
Bluetooth Low Energy (LE) ist eine Spezifikation, die Protokolle für die Erkennung und Kommunikation zwischen Strom sparenden Geräten definiert. Erkennung von Geräten erfolgt über das generische-Profil (GAP)-Protokoll. Gerät-Kommunikation erfolgt nach der Erkennung über generische Attribut GATT-Protokoll. Dieses Thema enthält eine kurze Übersicht über Bluetooth LE UWP-Apps. Weitere Informationen zu Bluetooth LE finden Sie [Bluetooth Core Specification](https://www.bluetooth.com/specifications/bluetooth-core-specification) Version 4.0, wo Bluetooth LE eingeführt wurde. 

![Bluetooth LE Rollen](images/gatt-roles.png)

*GATT und Lücke Rollen wurden in Windows 10 Version 1703 eingeführt.*

GATT und Lücke Protokolle können mithilfe der folgenden Namespaces in Ihrer UWP-Anwendung implementiert werden.
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)

## <a name="central-and-peripheral"></a>Mittel- und Peripheriegeräte
Die zwei primären Rollen Discovery heißen Mittel- und Peripheriegeräte. Im allgemeinen Windows arbeitet im zentralen Modus und verschiedene Peripheriegeräte verbindet. 

## <a name="attributes"></a>Attribute
Eine allgemeine finden Sie in der Windows-APIs Bluetooth ist generische Attribut (GATT). Das GATT-Profil definiert die Struktur der Daten und durch die zwei Bluetooth LE kommunizieren Betriebsmodi. Das Attribut ist der wichtigste Baustein des GATT. Die Haupttypen der Attribute sind Dienste, Merkmale und Deskriptoren. Diese Attribute ausführt anders zwischen Clients und Servern, sollten Sie ihre Aktivität in den entsprechenden Abschnitten erläutern. 

![Normale Attribut Hierarchie in einem allgemeinen Profil](images/gatt-service.png)

*Herzfrequenz Service wird im GATT Server API Formular ausgedrückt.*

## <a name="client-and-server"></a>Client und Server
Nach dem Herstellen einer Verbindung wird das Gerät mit den Daten (in der Regel kleine IoT-Sensor oder tragbar) als Server bezeichnet. Das Gerät, das diese Daten verwendet, um eine Funktion wird als Client bezeichnet. Windows-PC (Client) liest z. B. Daten aus Puls (Server) verfolgen, dass ein Benutzer optimal arbeitet. Weitere Informationen finden Sie in den Themen [GATT Client-](gatt-client.md) und [GATT](gatt-server.md) .

## <a name="watchers-and-publishers-beacons"></a>Beobachter und Herausgeber (Beacon)
Neben den zentralen und peripheren Rollen sind Rollen Beobachter und Sender. Sender häufig Beacons genannt, Kommunikation nicht sie GATT über da das begrenzte Raumangebot Advertisement-Paket für die Kommunikation verwendet. Ebenso Beobachter keinen herstellen eine Verbindung zum Empfangen von Daten und scannt nach benachbarten anzeigen. Konfigurieren Sie Windows zu benachbarten Werbung verwenden Sie die [BluetoothLEAdvertisementWatcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher) -Klasse. Um broadcast Beacon Nutzlasten verwenden Sie die [BluetoothLEAdvertisementPublisher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher) -Klasse. Weitere Informationen finden Sie auf [Werbung](ble-beacon.md) .

## <a name="see-also"></a>Siehe auch
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Bluetooth-Kern-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification)