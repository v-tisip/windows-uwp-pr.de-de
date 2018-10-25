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
ms.sourcegitcommit: 2c4daa36fb9fd3e8daa83c2bd0825f3989d24be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5521161"
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

Windows 10-Geräte können z. B. alle zuvor unterstützte Betriebssystemversionen (pro Gerätefamilie) ausführen. Desktopgeräte unter Windows 10 können apps ausgeführt werden, die für Windows8.1 oder Windows8 erstellt wurden. Windows 10 mobile Geräte können apps, die für Windows Phone 8.1, WindowsPhone8 und sogar Windows Phone erstellt wurden ausführen 7.x. 

In den folgenden Beispielen werden verschiedene Szenarien für eine App veranschaulicht, die das Abzielen auf unterschiedliche Betriebssystemversionen umfasst (in einigen Fällen führen bestimmte Einschränkungen der Pakete dazu, dass sie möglicherweise nicht auf allen hier aufgelisteten Betriebssystemversionen und Gerätetypen verwenden können. Beispielsweise muss die Architektur des Pakets für den Gerätetyp angemessen sein). 

### <a name="example-app-1"></a>Beispiel-App 1

| Zielbetriebssystem des Pakets | Dieses Paket abrufende Betriebssysteme |
|-------------------------------------|----------------------------------------------|
| Windows8.1                         | Windows 10-Desktopgeräte, Windows8.1      |
| Windows Phone 8.1                   | Windows 10 mobile-Geräte, Windows Phone 8.1 |
| WindowsPhone8                     | WindowsPhone8                              |
| Windows Phone7.1                   | Windows Phone7.x                            |

Im Beispiel-app 1 die app noch keine universelle Windows-Plattform (UWP)-Pakete, die speziell für Windows 10-Geräte erstellt wurden, aber Kunden unter Windows 10 können Sie die app weiterhin abrufen. Diese Kunden erhalten je nach Gerätetyp die besten verfügbaren Pakete.

### <a name="example-app-2"></a>Beispiel-App 2

| Zielbetriebssystem des Pakets  | Dieses Paket abrufende Betriebssysteme |
|--------------------------------------|----------------------------------------------|
| Windows 10 (universelle Gerätefamilie) | Windows 10 (alle gerätefamilien)             |
| Windows8.1                          | Windows8.1                                  |
| WindowsPhone8.1                    | WindowsPhone8.1                            |
| Windows Phone7.1                    | Windows Phone 7.x, WindowsPhone8           |

Im Beispiel-app 2 ist kein Paket, das auf Windows8 ausgeführt werden kann. Kunden, die eine andere Betriebssystemversion ausführen, können die App abrufen. Alle Kunden mit Windows10 erhalten dasselbe Paket.

### <a name="example-app-3"></a>Beispiel-App 3

| Zielbetriebssystem des Pakets | Dieses Paket abrufende Betriebssysteme                  |
|-------------------------------------|---------------------------------------------------------------|
| Windows 10 (desktopgerätefamilie)  | Desktopgeräte unter Windows 10                                    |
| WindowsPhone8                     | Windows 10 mobile-Geräte WindowsPhone8, Windows Phone 8.1 |

Im Beispiel-app 3 erhalten Kunden unter Windows 10 mobile Geräte da ist kein UWP-Paket, die die mobile Gerätefamilie ausgerichtet ist das Paket WindowsPhone8. Wenn dieser app später ein Paket, die auf die mobilgerätefamilie (oder die universelle Gerätefamilie) abzielt hinzugefügt, wird dieses Paket dann für Kunden unter Windows 10 mobile Geräte anstelle des Pakets WindowsPhone8 verfügbar sein.

Beachten Sie zudem, dass diese Beispiel-App kein Paket enthält, das auf Windows Phone7.x ausgeführt werden kann.

### <a name="example-app-4"></a>Beispiel-App 4

| Zielbetriebssystem des Pakets  | Dieses Paket abrufende Betriebssysteme |
|--------------------------------------|----------------------------------------------|
| Windows 10 (universelle Gerätefamilie) | Windows 10 (alle gerätefamilien)             |

Im Beispiel-app 4 können Geräte unter Windows 10 ist die app abrufen, aber es wird nicht für Kunden auf eine frühere Betriebssystemversion verfügbar sein. Da das UWP-Paket die universelle Gerätefamilie abzielt, steht es auf einem Gerät mit Windows 10 (pro [Gerät gerätefamilienverfügbarkeit Auswahl](device-family-availability.md)) zur Verfügung.


## <a name="removing-an-app-from-the-store"></a>Entfernen einer App aus dem Store

Manchmal möchten Sie Kunden eine App vielleicht überhaupt nicht mehr anbieten, d.h. Sie heben die Veröffentlichung der App auf. Klicken Sie hierzu auf der Seite **App-Übersicht** auf **Make app unavailable**. Nachdem Sie bestätigt haben, dass die App nicht mehr verfügbar sein soll, wird sie innerhalb weniger Stunden nicht mehr im Store angezeigt, und neue Kunden haben keine Möglichkeit, sie herunterzuladen (es sei denn, Sie verfügen über einen [Werbecode](generate-promotional-codes.md) und verfügen über ein Windows 10-Gerät).

> [!IMPORTANT]
> Durch diese Option werden alle in den Übermittlungen ausgewählten Einstellungen für [Sichtbarkeit](choose-visibility-options.md#discoverability) außer Kraft gesetzt. 

Diese Option hat dieselbe Wirkung, als ob Sie eine Übermittlung erstellt haben und **Make this product available but not discoverable in the Store** mit der Option **Erwerb beenden** auswählen. Allerdings ist das Erstellen einer neuen Übermittlung nicht erforderlich.

Beachten Sie, dass Kunden, die die App bereits besitzen, sie weiterhin verwenden und neu herunterladen können (und sogar Updates erhalten können, wenn Sie zu einem späteren Zeitpunkt neue Pakete übermitteln).

Nachdem die Bereitstellung der App aufgehoben wurde, wird sie weiterhin in Ihrem Dashboard angezeigt. Wenn Sie die App Kunden erneut anbieten möchten, klicken Sie in der App-Übersicht auf **Make app available**. Nach dem Bestätigen ist die App für Neukunden innerhalb weniger Stunden verfügbar (es sei denn, es liegen Einschränkungen durch Einstellungen in der letzten Übermittlung vor).

> [!NOTE]
> Wenn die App verfügbar bleiben, neuen Kunden mit bestimmten Betriebssystemversionen jedoch nicht mehr angeboten werden soll, können Sie eine neue Übermittlung erstellen und alle Pakete für die Betriebssystemversion entfernen, unter der Sie neue Verkäufe verhindern möchten. Wenn Sie bisher Pakete für Windows Phone 8.1 und Windows 10 hatten, und nicht die app auf WindowsPhone8.1 mehr anbieten beibehalten möchten, entfernen Sie alle Pakete WindowsPhone8.1 z. B. aus der Übermittlung. Nach der Veröffentlichung des Updates kann keine neuen Kunden unter WindowsPhone8.1 die app erwerben können Kunden, die bereits haben weiterhin verwenden). Die app wird jedoch weiterhin für neue Kunden unter Windows 10 verfügbar sein.


## <a name="removing-packages-for-a-previously-supported-device-family"></a>Entfernen von Paketen für eine zuvor unterstützte Gerätefamilie

Wenn Sie alle Pakete für eine bestimmte [Gerätefamilie](https://docs.microsoft.com/uwp/extension-sdks/device-families-overview) entfernen, die Ihre app zuvor werden Sie aufgefordert unterstützt um zu bestätigen, dass dies beabsichtigt ist, bevor Sie Ihre Änderungen auf der Seite " **Pakete** " speichern können.

Wenn Sie eine Übermittlung, die alle Pakete entfernt, die von einer Gerätefamilie ausgeführt werden kann, die Ihre app zuvor unterstützt veröffentlichen, werden neue Kunden nicht um die app auf diese Gerätefamilie erwerben können. Sie können jederzeit ein weiteres Update veröffentlichen, um erneut Pakete für diese Gerätefamilie anzubieten.

Hinweis: Auch wenn Sie alle Pakete entfernen, die eine bestimmte Gerätefamilie unterstützen, können vorhandene Kunden, die die App auf diesem Gerätetyp bereits installiert haben, diese weiterhin verwenden und erhalten alle Updates, die Sie später zur Verfügung stellen.


<a name="adding-packages-for-windows-10-to-a-previously-published-app"></a>

## <a name="adding-packages-for-windows10-to-a-previously-published-app"></a>Hinzufügen von Paketen für Windows 10 zu einer zuvor veröffentlichten app

Wenn Sie eine app im Store verfügen, das nur Pakete für Windows 8.x und/oder Windows Phone 8.x, und Aktualisieren Ihrer app für Windows 10, eine neue Übermittlung erstellen und Ihre Pakete UWP, .msixupload oder ".appxupload" während des Schritts [Pakete](upload-app-packages.md) hinzufügen möchten. Nachdem Ihre app den Zertifizierungsprozess durchlaufen hat, wird das UWP-Paket auch für Käufe von Kunden unter Windows 10 verfügbar.

> [!NOTE]
> Nachdem ein Kunde unter Windows 10 das UWP-Paket erhalten hat, können nicht Sie diesen Kunden auf ein Paket für eine frühere Betriebssystemversion ausführen. 

Beachten Sie, dass die Versionsnummer des Ihre Windows 10-Pakete höher sein als die für alle Windows8, Windows8.1 und/oder Windows Phone 8.1-Pakete werden muss, die Sie verwendet haben. Weitere Informationen finden Sie unter [Paketversionsnummern](package-version-numbering.md).

Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken von Apps](../packaging/index.md).
