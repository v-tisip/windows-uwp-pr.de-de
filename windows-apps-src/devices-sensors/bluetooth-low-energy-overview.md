---
author: msatranjr
title: Bluetooth Low Energy
description: Dieses Thema bietet einen schnellen Überblick über Bluetooth LE in UWP apps.
ms.author: misatran
ms.date: 03/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Bluetooth, Bluetooth LE, niedrige Energie-, Gatt, Abstand, Central, Peripheriegeräte, Client, Server, Watcher, publisher
ms.localizationpriority: medium
ms.openlocfilehash: 0d6cc1fb5a0b3cb96748b99c490b23a9e1df128f
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "305195"
---
# <a name="bluetooth-low-energy"></a>Bluetooth Low Energy
Bluetooth-niedriger Energie (LE) ist eine Spezifikation, die Protokolle für die Suche und Kommunikation zwischen Power effiziente Geräten definiert. Erkennung von Geräten erfolgt über das Protokoll generische Access Profil (GAP). Nach der Erkennung erfolgt Ad-hoc Kommunikation über das Protokoll generische Attribut (GATT). Dieses Thema bietet einen schnellen Überblick über Bluetooth LE in UWP apps. Ausführlichere Informationen zu Bluetooth LE finden Sie unter der [Bluetooth-Kern-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification) , Version 4.0, wobei Bluetooth LE eingeführt wurde. 

![Bluetooth-LE Rollen](images/gatt-roles.png)

*GATT und Lücke Rollen wurden in Windows 10 1703 Version eingeführt.*

GATT und Lücke Protokolle können mithilfe der folgenden Namespaces in Ihrer app UWP implementiert werden.
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)

## <a name="central-and-peripheral"></a>Zentrale und Peripheriegeräte
Die zwei primären Rollen der Ermittlung werden Central und Peripheriegeräte bezeichnet. Im allgemeinen Windows arbeitet im zentralen-Modus und stellt eine Verbindung mit verschiedenen Peripheriegeräte. 

## <a name="attributes"></a>Attribute
Eine allgemeine Akronym sehen Sie in den Windows-Bluetooth-APIs ist generische Attribut (GATT). Das Profil GATT definiert die Struktur der Daten und Betriebsmodi über die zwei LE Bluetooth-Geräten kommunizieren. Das Attribut ist der wichtigste Baustein GATT. Die wichtigsten Typen der Attribute sind Services, Merkmale und Deskriptoren. Diese Attribute führen unterschiedlich zwischen Clients und Servern, damit ihre Aktivität in den entsprechenden Abschnitten besprechen mehr eignet. 

![Typische Attribut Hierarchie in einem allgemeinen Profil](images/gatt-service.png)

*Der Dienst Herz Rate wird im Formular GATT-Server-API ausgedrückt.*

## <a name="client-and-server"></a>Client und Server
Nachdem eine Verbindung hergestellt wurde, wird das Gerät, das Daten (in der Regel eine kleine IoT Sensor oder tragbar) enthält, wie der Server bezeichnet. Das Gerät, das diese Daten verwendet, um eine Funktion ausgeführt wird als Client bezeichnet. Beispielsweise liest ein Windows-PC (Client), dass ein Benutzer optimal funktionsfähig ist Daten aus einem Monitor Herz Rate (Server) zum Nachverfolgen. Weitere Informationen finden Sie unter den Themen [GATT Client-](gatt-client.md) und [GATT](gatt-server.md) .

## <a name="watchers-and-publishers-beacons"></a>Beobachter und Herausgeber (Beacons)
Zusätzlich zu den Rollen Central und Peripheriegeräte sind Beobachter und Sender Rollen. Sendeanstalten im Allgemeinen als Beacons bezeichnet werden, kommunizieren nicht sie über GATT, da sie dem beschränkt vorgegebenen im Paket Ankündigung für die Kommunikation verwenden. In ähnlicher Weise Beobachter keinen zum Herstellen einer Verbindung zum Empfangen von Daten, scannt nach in der Nähe anzeigen. Verwenden Sie zum Konfigurieren von Windows auf, in der Nähe Werbung einzuhalten, die [BluetoothLEAdvertisementWatcher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementwatcher) -Klasse. Um Signal Nutzlast zu übertragen, verwenden Sie die [BluetoothLEAdvertisementPublisher](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.advertisement.bluetoothleadvertisementpublisher) -Klasse. Weitere Informationen finden Sie unter dem Thema [Ankündigung](ble-beacon.md) .

## <a name="see-also"></a>Siehe auch
- [Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Windows.Devices.Bluetooth.Advertisement](https://docs.microsoft.com/en-us/uwp/api/windows.devices.bluetooth.genericattributeprofile)
- [Bluetooth-Kern-Spezifikation](https://www.bluetooth.com/specifications/bluetooth-core-specification)