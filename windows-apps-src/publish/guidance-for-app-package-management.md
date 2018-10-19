---
author: jnHs
Description: Learn how your app's packages are made available to your customers, and how to manage specific package scenarios.
title: Leitfaden für die Verwaltung von App-Paketen
ms.assetid: 55405D0B-5C1E-43C8-91A1-4BFDD336E6AB
ms.author: wdg-dev-content
ms.date: 10/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a43f3b4c5684d93ea6986c4d1f1e4dae46c1a959
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4963283"
---
# <a name="guidance-for-app-package-management"></a>Leitfaden für die Verwaltung von App-Paketen

Erfahren Sie, wie App-Pakete für Ihre Kunden verfügbar gemacht werden und bestimmte Paketszenarien verwaltet werden.

-   [Betriebssystemversionen und Paketverteilung](#os-versions-and-package-distribution)
-   [Hinzufügen von Paketen für Windows10 zu einer zuvor veröffentlichten App](#adding-packages-for-windows-10-to-a-previously-published-app)
-   [Verwalten der Paketkompatibilität für Windows Phone8.1](#maintaining-package-compatibility-for-windows-phone-81)
-   [Entfernen einer App aus dem Store](#removing-an-app-from-the-store)
-   [Entfernen von Paketen für eine zuvor unterstützte Gerätefamilie](#removing-packages-for-a-previously-supported-device-family)


## <a name="os-versions-and-package-distribution"></a>Betriebssystemversionen und Paketverteilung

Auf unterschiedlichen Betriebssystemen können unterschiedliche Pakettypen ausgeführt werden. Wenn mindestens zwei Pakete auf dem Gerät eines Kunden ausgeführt werden können, stellt der Microsoft Store die beste verfügbare Übereinstimmung bereit.

Im Allgemeinen können höhere Betriebssystemversionen Pakete ausführen, die auf frühere Betriebssystemversionen für dieselbe Gerätefamilie abzielen. Allerdings erhalten Kunden nur die Pakete, wenn die app kein Paket enthält, die ihre aktuelle Betriebssystemversion abzielt.

Beispielsweise können Geräte unter Windows10 alle zuvor unterstützten Betriebssystemversionen (pro Gerätefamilie) ausführen. Auf Desktopgeräten unter Windows10 können Apps ausgeführt werden, die für Windows8.1 oder Windows8 erstellt wurden. Auf Mobilgeräten unter Windows10 können Apps ausgeführt werden, die für Windows Phone8.1, WindowsPhone8 und sogar Windows Phone7.x erstellt wurden. 

In den folgenden Beispielen werden verschiedene Szenarien für eine App veranschaulicht, die das Abzielen auf unterschiedliche Betriebssystemversionen umfasst (in einigen Fällen führen bestimmte Einschränkungen der Pakete dazu, dass sie möglicherweise nicht auf allen hier aufgelisteten Betriebssystemversionen und Gerätetypen verwenden können. Beispielsweise muss die Architektur des Pakets für den Gerätetyp angemessen sein). 

### <a name="example-app-1"></a>Beispiel-App 1

| Zielbetriebssystem des Pakets | Dieses Paket abrufende Betriebssysteme |
|-------------------------------------|----------------------------------------------|
| Windows 8.1                         | Desktopgeräte unter Windows10, Windows8.1      |
| Windows Phone 8.1                   | Mobilgeräte unter Windows10, Windows Phone8.1 |
| Windows Phone 8                     | Windows Phone 8                              |
| Windows Phone7.1                   | Windows Phone7.x                            |

In der Beispiel-App1 verfügt die App noch nicht über UWP-Pakete (Universelle Windows-Plattform), die speziell für Geräte unter Windows10 erstellt wurden. Kunden von Windows10 können die App jedoch weiterhin abrufen. Diese Kunden erhalten je nach Gerätetyp die besten verfügbaren Pakete.

### <a name="example-app-2"></a>Beispiel-App 2

| Zielbetriebssystem des Pakets  | Dieses Paket abrufende Betriebssysteme |
|--------------------------------------|----------------------------------------------|
| Windows10 (universelle Gerätefamilie) | Windows10 (alle Gerätefamilien)             |
| Windows 8.1                          | Windows 8.1                                  |
| WindowsPhone8.1                    | WindowsPhone8.1                            |
| Windows Phone7.1                    | Windows Phone 7.x, Windows Phone 8           |

In der Beispiel-App2 ist kein Paket vorhanden, das unter Windows8 ausgeführt werden kann. Kunden, die eine andere Betriebssystemversion ausführen, können die App abrufen. Alle Kunden mit Windows10 erhalten dasselbe Paket.

### <a name="example-app-3"></a>Beispiel-App 3

| Zielbetriebssystem des Pakets | Dieses Paket abrufende Betriebssysteme                  |
|-------------------------------------|---------------------------------------------------------------|
| Windows10 (Desktopgerätefamilie)  | Desktopgeräte unter Windows10                                    |
| Windows Phone 8                     | Mobilgeräte unter Windows10, WindowsPhone8, Windows Phone 8.1 |

In der Beispiel-App3 erhalten Kunden von Mobilgeräten unter Windows10 das Windows Phone8-Paket, da kein UWP-Paket auf die Mobilgerätefamilie abzielt. Wenn in dieser App später ein Paket hinzugefügt wird, das auf die Mobilgerätefamilie (oder die universelle Gerätefamilie) abzielt, steht dieses Paket für Kunden von Mobilgeräten unter Windows10 anstelle des WindowsPhone8-Pakets zur Verfügung.

Beachten Sie zudem, dass diese Beispiel-App kein Paket enthält, das auf Windows Phone7.x ausgeführt werden kann.

### <a name="example-app-4"></a>Beispiel-App 4

| Zielbetriebssystem des Pakets  | Dieses Paket abrufende Betriebssysteme |
|--------------------------------------|----------------------------------------------|
| Windows10 (universelle Gerätefamilie) | Windows10 (alle Gerätefamilien)             |

In der Beispiel-App4 können Geräte unter Windows10 die App abrufen. Sie steht jedoch nicht für Kunden einer früheren Betriebssystemversion zur Verfügung. Da das UWP-Paket die universelle Gerätefamilie ausgerichtet ist, wird es für alle Windows 10-Gerät (pro [gerätefamilienverfügbarkeit von gerätefamilien Auswahl](device-family-availability.md)) zur Verfügung.


## <a name="removing-an-app-from-the-store"></a>Entfernen einer App aus dem Store

Manchmal möchten Sie Kunden eine App vielleicht überhaupt nicht mehr anbieten, d.h. Sie heben die Veröffentlichung der App auf. Klicken Sie hierzu auf der Seite **App-Übersicht** auf **Make app unavailable**. Nachdem Sie bestätigt haben, dass die App nicht mehr verfügbar sein soll, wird sie innerhalb weniger Stunden nicht mehr im Store angezeigt, und neue Kunden haben keine Möglichkeit, sie herunterzuladen (es sei denn, Sie verfügen über einen [Werbecode](generate-promotional-codes.md) und verfügen über ein Windows 10-Gerät).

> [!IMPORTANT]
> Durch diese Option werden alle in den Übermittlungen ausgewählten Einstellungen für [Sichtbarkeit](choose-visibility-options.md#discoverability) außer Kraft gesetzt. 

Diese Option hat dieselbe Wirkung, als ob Sie eine Übermittlung erstellt haben und **Make this product available but not discoverable in the Store** mit der Option **Erwerb beenden** auswählen. Allerdings ist das Erstellen einer neuen Übermittlung nicht erforderlich.

Beachten Sie, dass Kunden, die die App bereits besitzen, sie weiterhin verwenden und neu herunterladen können (und sogar Updates erhalten können, wenn Sie zu einem späteren Zeitpunkt neue Pakete übermitteln).

Nachdem die Bereitstellung der App aufgehoben wurde, wird sie weiterhin in Ihrem Dashboard angezeigt. Wenn Sie die App Kunden erneut anbieten möchten, klicken Sie in der App-Übersicht auf **Make app available**. Nach dem Bestätigen ist die App für Neukunden innerhalb weniger Stunden verfügbar (es sei denn, es liegen Einschränkungen durch Einstellungen in der letzten Übermittlung vor).

> [!NOTE]
> Wenn die App verfügbar bleiben, neuen Kunden mit bestimmten Betriebssystemversionen jedoch nicht mehr angeboten werden soll, können Sie eine neue Übermittlung erstellen und alle Pakete für die Betriebssystemversion entfernen, unter der Sie neue Verkäufe verhindern möchten. Wenn Sie beispielsweise bisher Pakete für Windows Phone 8.1 und Windows 10 hatten, die App jedoch keinen Neukunden mit WindowsPhone8.1 mehr anbieten möchten, entfernen Sie alle Ihre WindowsPhone8.1-Pakete aus der Übermittlung. Nach der Veröffentlichung des Updates können keine neuen Kunden unter WindowsPhone8.1 die App mehr erwerben (Kunden, die sie bereits haben, können sie jedoch weiterhin nutzen). Für neue Kunden unter Windows10 ist die App allerdings weiterhin verfügbar.


## <a name="removing-packages-for-a-previously-supported-device-family"></a>Entfernen von Paketen für eine zuvor unterstützte Gerätefamilie

Wenn Sie alle Pakete für eine bestimmte [Gerätefamilie](https://docs.microsoft.com/uwp/extension-sdks/device-families-overview) entfernen, die Ihre app zuvor werden Sie aufgefordert unterstützt um zu bestätigen, dass dies beabsichtigt ist, bevor Sie Ihre Änderungen auf der Seite " **Pakete** " speichern können.

Wenn Sie eine Übermittlung, die alle Pakete entfernt, die von einer Gerätefamilie ausgeführt werden kann, die Ihre app zuvor unterstützt veröffentlichen, werden neue Kunden nicht um die app auf diese Gerätefamilie erwerben können. Sie können jederzeit ein weiteres Update veröffentlichen, um erneut Pakete für diese Gerätefamilie anzubieten.

Hinweis: Auch wenn Sie alle Pakete entfernen, die eine bestimmte Gerätefamilie unterstützen, können vorhandene Kunden, die die App auf diesem Gerätetyp bereits installiert haben, diese weiterhin verwenden und erhalten alle Updates, die Sie später zur Verfügung stellen.


<a name="adding-packages-for-windows-10-to-a-previously-published-app"></a>

## <a name="adding-packages-for-windows-10-to-a-previously-published-app"></a>Hinzufügen von Paketen für Windows10 zu einer zuvor veröffentlichten App

Wenn Sie eine app im Store verfügen, das nur Pakete für Windows 8.x und/oder Windows Phone 8.x, und aktualisieren Sie Ihre app für Windows 10, eine neue Übermittlung erstellen und Ihre Pakete UWP, .msixupload oder ".appxupload" während des Schritts [Pakete](upload-app-packages.md) hinzufügen möchten. Nachdem Ihre app den Zertifizierungsprozess durchlaufen hat, wird das UWP-Paket auch für Käufe von Neukunden unter Windows 10 verfügbar.

> [!NOTE]
> Nachdem ein Kunde unter Windows 10 das UWP-Paket erhalten hat, können Sie für diesen Kunden kein Rollback für eine frühere Betriebssystemversion mehr ausführen. 

Beachten Sie, dass die Versionsnummer des Ihrer Windows 10-Pakete höher sein als die für alle Windows 8, Windows 8.1 und/oder Windows Phone 8.1-Pakete muss, die Sie verwendet haben. Weitere Informationen finden Sie unter [Paketversionsnummern](package-version-numbering.md).

Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken von Apps](../packaging/index.md).
