---
author: jnHs
Description: Learn how your app's packages are made available to your customers, and how to manage specific package scenarios.
title: Leitfaden für die Verwaltung von App-Paketen
ms.assetid: 55405D0B-5C1E-43C8-91A1-4BFDD336E6AB
ms.author: wdg-dev-content
ms.date: 03/28/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9b0b6315b1177138c3ede7834e2dbc792ee106dd
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3404922"
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

In der Beispiel-App4 können Geräte unter Windows10 die App abrufen. Sie steht jedoch nicht für Kunden einer früheren Betriebssystemversion zur Verfügung. Da das UWP-Paket die universelle Gerätefamilie ausgerichtet ist, wird es für alle Windows 10-Gerät (pro Ihre [Gerät gerätefamilienverfügbarkeit Auswahl](device-family-availability.md)) zur Verfügung.


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

Wenn Sie über eine App im Store verfügen, die auf Windows 8.x und/oder Windows Phone 8.x ausgerichtet ist, und Sie die App für Windows10 aktualisieren möchten, müssen Sie eine neue Übermittlung erstellen und die UWP-Pakete „.appxupload“ während des Schritts [Pakete](upload-app-packages.md) hochladen. Nachdem Ihre app den Zertifizierungsprozess durchlaufen hat, werden Kunden, die Ihre app bereits und befinden sich jetzt auf Windows 10 die UWP-Pakete als Update aus dem Store abrufen. Das UWP-Paket steht auch für Käufe von Neukunden unter Windows 10 zur Verfügung.

> [!NOTE]
> Nachdem ein Kunde unter Windows 10 das UWP-Paket erhalten hat, können Sie für diesen Kunden kein Rollback für eine frühere Betriebssystemversion mehr ausführen. 

Die Versionsnummer des entsprechenden Windows10-Pakets muss höher sein als die der Pakete für Windows8, Windows8.1 bzw. WindowsPhone8.1, die Sie erhalten (oder der Pakete für diese Betriebssystemversionen, die Sie zuvor veröffentlicht haben). Weitere Informationen finden Sie unter [Paketversionsnummern](package-version-numbering.md).

Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken von Apps](../packaging/index.md).

> [!IMPORTANT]
> Beachten Sie beim Bereitstellen von Paketen für die universelle Gerätefamilie, dass jeder Kunde, der Ihre App bereits auf einem früheren Betriebssystem (WindowsPhone8, Windows8.1 usw.) verwendet hat und anschließend ein Upgrade auf Windows10 ausführt, auf Ihr Windows10-Paket aktualisiert wird.
> 
> Dies geschieht auch dann, wenn Sie eine bestimmte Gerätefamilie im Schritt [gerätefamilienverfügbarkeit](device-family-availability.md) der Übermittlung, seit ausgeschlossen haben, dass Abschnitt nur auf neue Käufe gilt. Wenn Sie nicht möchten, dass jeder vorherige Kunden Ihr universelles Windows10-Paket abrufen kann, müssen Sie das [**TargetDeviceFamily**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)-Element in Ihrem APPX-Manifest so aktualisieren, dass nur die bestimmte Gerätefamilie einbezogen wird, die Sie unterstützen möchten.
> 
> Angenommen Sie, Sie möchten Ihre Windows 8 und Windows 8.1-Kunden, die auf einem Windows 10-desktop-Gerät abzurufenden Ihre neue UWP-app aktualisiert haben, möchten aber bei Windows Phone-Kunden, die nun auf Windows 10 Mobile-Geräten weiterhin die Pakete, die Sie zuvor würde Availabl vorgenommen werden e (für Windows Phone 8 oder Windows Phone 8.1). Zu diesem Zweck müssen Sie zum Aktualisieren der [**TargetDeviceFamily**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) in Ihrem Appx-Manifest einzuschließende nur **Windows.Desktop** (für die Familie der Desktopgeräte), nicht als den **Windows.Universal** -Wert (für die universelle Gerätefamilie) dass Microsoft Visual Studio im Manifest standardmäßig enthält. Übermitteln Sie keine UWP-Pakete, die entweder auf universelle oder Mobilgerätefamilien (**Windows.Universal** oder **Windows.Universal**) abzielen. Auf diese Weise erhalten die Kunden von Windows10 Mobile überhaupt keine UWP-Pakete.


## <a name="maintaining-package-compatibility-for-windows-phone-81"></a>Verwalten der Paketkompatibilität für Windows Phone8.1

Beim Aktualisieren von Apps, die zuvor für Windows Phone 8.1 veröffentlicht wurden, gelten bestimmte Anforderungen für Pakettypen.

-   Nachdem eine App über ein veröffentlichtes WindowsPhone8.1-Paket verfügt, müssen alle nachfolgenden Updates ebenfalls über ein WindowsPhone8.1-Paket verfügen.
-   Nachdem eine App über eine veröffentlichte WindowsPhone8.1-XAP-Datei verfügt, müssen nachfolgende Updates über ein WindowsPhone8.1-XAP-, WindowsPhone8.1-APPX- oder ein WindowsPhone8.1-APPXBUNDLE-Format verfügen.
-   Wenn eine App über ein veröffentlichtes WindowsPhone8.1-APPX-Format verfügt, müssen nachfolgende Updates über ein WindowsPhone8.1-APPX- oder WindowsPhone8.1-APPXBUNDLE-Format verfügen. Ein WindowsPhone8.1-XAP-Format ist demnach nicht zulässig. Dies gilt für das Format "appxupload", das auch ein WindowsPhone8.1-APPX-Format enthält.
-   Nachdem eine App über ein veröffentlichtes WindowsPhone8.1-APPXBUNDLE-Format verfügt, müssen nachfolgende Updates über ein WindowsPhone8.1-APPXBUNDLE-Format verfügen. Somit ist weder ein WindowsPhone8.1-XAP- noch ein WindowsPhone8.1-APPX-Format zulässig. Dies gilt für das Format "appxupload", das auch ein WindowsPhone8.1-APPXBUNDLE-Format enthält.

Wenn diese Regeln nicht beachtet werden, führt dies möglicherweise zu Problemen beim Hochladen, die Sie daran hindern, Ihre Übermittlung abzuschließen.