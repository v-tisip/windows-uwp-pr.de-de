---
author: mcleanbyron
description: Dieser Artikel beschreibt allgemeine Fehlercodes für Store Vorgänge für apps und Add-ons, einschließlich-app-Erwerb, Lizenzierung und Installieren von Self-app-Updates.
title: Fehlercodes für Store-Vorgänge
ms.author: mcleans
ms.date: 08/24/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, in der app-Einkauf, IAPs, Add-ons, Fehlercodes
ms.localizationpriority: medium
ms.openlocfilehash: 0931397e24eaba44cdf04092f5f367c43a91dd82
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "959379"
---
# <a name="error-codes-for-store-operations"></a>Fehlercodes für Store-Vorgänge

<!-- confirm whether symbolic names are defined for app developers, or do they just handle direct error code values -->

Dieser Artikel beschreibt allgemeine Fehlercodes, die beim Entwickeln von oder Testen in Ihrer app Store-Vorgänge auftreten können.

## <a name="in-app-purchase-error-codes"></a>In app-Einkauf-Fehlercodes

Die folgenden Fehlercodes beziehen sich auf Vorgänge in app-Einkauf.

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F6100   | Der in-app-Erwerb konnte nicht abgeschlossen werden, da Kinderecke aktiv ist. Zum Ausführen des Erwerb an das Gerät mit Ihrem Microsoft-Konto melden Sie an, und führen Sie die Anwendung erneut.               |
| 0x803F6101   | Die angegebene App konnte nicht gefunden werden. Die app kann nicht mehr im Speicher, oder haben möglicherweise die falsche Speicherobjekt-ID für die app bereitgestellt.     |
| 0x803F6102   | Das angegebene Add-On konnte nicht gefunden werden. Das Add-on möglicherweise nicht mehr verfügbar in den Speicher oder Ihre möglicherweise die falsche Speicherobjekt-ID für das Add-on bereitgestellt haben.                                               |
| 0x803F6103   | Das angegebene Produkt konnte nicht gefunden werden. Das Produkt möglicherweise nicht mehr verfügbar im Speicher oder haben möglicherweise die falsche Speicherobjekt-ID für das Produkt bereitgestellt.                                          |
| 0x803F6104   | Der in-app-Erwerb konnte nicht abgeschlossen werden, da Sie eine Testversion der app ausgeführt werden. Um in app-Käufe erworben abgeschlossen haben, installieren Sie die Vollversion der app.               |
| 0x803F6105   | Der in-app-Erwerb konnte nicht abgeschlossen werden, da Sie nicht mit Ihrem Microsoft-Konto angemeldet sind.                                              |
| 0x803F6107   | Ein unerwarteter Fehler ist aufgetreten beim Verarbeiten des aktuellen Vorgangs.                                             |
| 0x803F6108   | Der in-app-Erwerb konnte nicht abgeschlossen werden, da die app-Lizenz Informationen fehlt. Dieser Fehler kann auftreten, wenn die Seite-laden Ihrer app. Um dieses Problem zu beheben, deinstallieren Sie die app aus, und klicken Sie dann aus dem Speicher zum Aktualisieren der app-Lizenzvertrags installieren.                                          |
| 0x803F6109   | Die Erfüllung verwendet Add-on konnte nicht abgeschlossen werden, da die angegebene Menge mehr als die restliche ist.        |
| 0x803F610A   | Die angegebene Providertyp für das Store-Benutzerkonto wird nicht unterstützt.                                            |
| 0x803F610B   | Der angegebene Informationsspeicher Vorgang wird nicht unterstützt.                                             |
| 0x803F610C   | Die app wird den angegebenen Hintergrund Aufgabe Vertrag nicht unterstützt.                                             |
| 0x80040001   | Die bereitgestellte Liste von Add-On-Produkt IDs ist ungültig.                        |
| 0x80040002   | Die angezeigten Liste von Schlüsselwörtern ist ungültig.                   |
| 0 x 80040003   | Das Ziel des Vorgangs Fulfillment ist ungültig.                       |

## <a name="licensing-error-codes"></a>Lizenzierung von Fehlercodes

Die folgenden Fehlercodes beziehen sich auf die Lizenzierung von Vorgängen für apps oder Add-ons.

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F700C   | Das Gerät ist zurzeit offline. Um diese app verwenden, während das Gerät offline ist, öffnen Sie Ihre Einstellungen gespeichert und wechseln Sie die Einstellung **Offline-Berechtigungen** zu.            |
| 0x803F8001   | Sie müssen sich nicht auf einen Anspruch, der für das Produkt aus. Sie verwenden möglicherweise ein anderes Microsoft-Konto als das, mit dem das Produkt erwerben.           |
| 0x803F8002   | Die Berechtigung für das Produkt ist abgelaufen.           |
| 0x803F8003   | Die Berechtigung für das Produkt ist in einem ungültigen Zustand, der verhindert, dass eine Lizenz erstellt werden.   |
| 0x803F8009<br/>0x803F800A   | Der Testzeitraum für die app ist abgelaufen.   |
| 0x803F8190   |  Die Lizenz kann nicht das Produkt in der aktuellen Land oder Region des Geräts verwendet werden.  |
| 0x803F81F5<br/>0x803F81F6<br/>0x803F81F7<br/>0x803F81F8<br/>0x803F81F9   |  Sie haben die maximale Anzahl von Geräten erreicht, die mit Spielen und apps aus dem Speicher verwendet werden können. Um diese Spiel oder app auf dem aktuellen Gerät zu verwenden, müssen Sie zuerst ein anderes Gerät von Ihrem Konto entfernt.  |
| 0x803F9000<br/>0x803F9001    |  Die Lizenz ist abgelaufen oder beschädigt. Um diesen Fehler zu beheben, führen Sie die [Problembehandlung für apps für Windows](https://support.microsoft.com/help/4027498/windows-run-the-troubleshooter-for-windows-apps) zum Zurücksetzen der Zwischenspeicher.     |
| 0x803F9006    |  Der Vorgang konnte nicht abgeschlossen werden, da der Benutzer auf dieses Produkt hat nicht an das Gerät mit ihrem Microsoft-Konto angemeldet ist.            |
| 0x803F9008<br/>0x803F9009    |  Ihr Gerät ist offline. Das Gerät muss für dieses Produkt online sein.            |
| 0x803F900A    |  Das Abonnement ist abgelaufen.            |


## <a name="self-install-update-error-codes"></a>Installieren Sie Self Update-Fehlercodes

Die folgenden Fehlercodes beziehen sich auf [Self Paket-Updates installieren](../packaging/self-install-package-updates.md).

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F6200   | Zustimmung des Benutzers ist erforderlich, um das Paket Update herunterzuladen.               |
| 0x803F6201   | Zustimmung des Benutzers ist zum Herunterladen und installieren Sie das Paket-Update erforderlich.                                                  |
| 0x803F6203   | Zustimmung des Benutzers ist erforderlich, um das Paket Update zu installieren.                                         |
| 0x803F6204   | Zustimmung des Benutzers ist erforderlich, um das Paket Update heruntergeladen werden, da die heruntergeladene Datei auf einer gemessenen-Verbindung erfolgt.                                             |
| 0x803F6206   | Zustimmung des Benutzers ist erforderlich, herunterladen und installieren das Paket Update, da die heruntergeladene Datei auf einer gemessenen-Verbindung erfolgt.     |


## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Produktinformationen zu Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md)
* [Abrufen von Lizenzinformationen zu Apps und Add-Ons](get-license-info-for-apps-and-add-ons.md)
* [Aktivieren von In-App-Käufen von Apps und Add-Ons](enable-in-app-purchases-of-apps-and-add-ons.md)
* [Unterstützen von Käufen konsumierbarer Add-Ons](enable-consumable-add-on-purchases.md)
* [Aktivieren von Abonnements für Add-Ons für Ihre App](enable-subscription-add-ons-for-your-app.md)
* [Implementieren einer Testversion Ihrer App](implement-a-trial-version-of-your-app.md)
