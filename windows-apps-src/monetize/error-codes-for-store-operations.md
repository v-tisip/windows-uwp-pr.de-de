---
description: Dieser Artikel beschreibt allgemeine Fehlercodes für Store-Vorgänge für apps und Add-ons, einschließlich in-app-Kauf, Lizenzierung und sich selbst installieren Sie app-Updates.
title: Fehlercodes für Store-Vorgänge
ms.date: 08/24/2017
ms.topic: article
keywords: Windows 10, Uwp, in-app-Einkäufe, IAPs, Add-ons, Fehlercodes
ms.localizationpriority: medium
ms.openlocfilehash: ba505b30076c356a39ae195e1d187cbc49d8a66a
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8349340"
---
# <a name="error-codes-for-store-operations"></a>Fehlercodes für Store-Vorgänge

<!-- confirm whether symbolic names are defined for app developers, or do they just handle direct error code values -->

Dieser Artikel beschreibt allgemeine Fehlercodes, die auftreten können, während Sie entwickeln oder Store-bezogene Vorgänge in Ihrer app testen.

## <a name="in-app-purchase-error-codes"></a>In-app-Kauf-Fehlercodes

Die folgenden Fehlercodes beziehen sich auf in-app-Kauf-Vorgänge.

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F6100   | Der in-app-Kauf konnte nicht abgeschlossen werden, da Kinderecke aktiv ist. Um den Kauf abgeschlossen haben, melden Sie sich an das Gerät mit Ihrem Microsoft-Konto, und führen Sie die Anwendung erneut aus.               |
| 0x803F6101   | Die angegebene App konnte nicht gefunden werden. Die app kann nicht mehr im Store, oder haben möglicherweise die falsche Store-ID für die app bereitgestellt.     |
| 0x803F6102   | Das angegebene Add-On konnte nicht gefunden werden. Das Add-on möglicherweise nicht mehr verfügbar in den Store oder Ihre möglicherweise die falsche Store-ID für das Add-on bereitgestellt haben.                                               |
| 0x803F6103   | Das angegebene Produkt konnte nicht gefunden werden. Das Produkt kann nicht mehr im Store, oder Sie möglicherweise bereitgestellt haben die falsche Store-ID für das Produkt.                                          |
| 0x803F6104   | Der in-app-Kauf konnte nicht abgeschlossen werden, da Sie eine Testversion der app ausgeführt werden. Um in-app-Käufe abzuschließen, installieren Sie die Vollversion der app.               |
| 0x803F6105   | Der in-app-Kauf konnte nicht abgeschlossen werden, da Sie nicht mit Ihrem Microsoft-Konto angemeldet sind.                                              |
| 0x803f6107 fest   | Ein unerwarteter Fehler ist aufgetreten während der Verarbeitung des aktuellen Vorgangs.                                             |
| 0x803F6108   | Der in-app-Kauf konnte nicht abgeschlossen werden, da die app-Lizenz Informationen fehlt. Dieser Fehler kann auftreten, wenn Sie Ihre app-querzuladen. Um dieses Problem zu beheben, deinstallieren Sie die app, und installieren sie aus dem Speicher die app-Lizenz zu aktualisieren.                                          |
| 0x803F6109   | Die Erfüllung konsumierbare Add-on konnte nicht abgeschlossen werden, da die angegebene Menge mehr als den Restbetrag ist.        |
| 0x803F610A   | Der angegebene Anbieter-Typ für das Benutzerkonto Store wird nicht unterstützt.                                            |
| 0x803F610B   | Der angegebene Store-Vorgang wird nicht unterstützt.                                             |
| 0x803F610C   | Den angegebenen Hintergrund Aufgabe Vertrag unterstützt die app nicht.                                             |
| 0x80040001   | Die bereitgestellte Liste von Add-On-Produkt IDs ist ungültig.                        |
| 0x80040002   | Die bereitgestellte Liste der Schlüsselwörter ist ungültig.                   |
| 0 x 80040003   | Das Ziel Erfüllung ist ungültig.                       |

## <a name="licensing-error-codes"></a>Lizenzierung-Fehlercodes

Die folgenden Fehlercodes beziehen sich auf Vorgänge für apps oder Add-ons Lizenzierung.

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F700C   | Das Gerät ist zurzeit offline. Um diese app verwenden, während das Gerät offline ist, öffnen Sie die Store-Einstellungen, und schalten Sie **Offlineberechtigungen** .            |
| 0x803F8001   | Sie müssen sich nicht auf eine Berechtigung für das Produkt aus. Möglicherweise verwenden Sie ein anderes Microsoft-Konto als die, die das Produkt kaufen verwendet wurde.           |
| 0x803F8002   | Ihre Berechtigung für das Produkt ist abgelaufen.           |
| 0x803F8003   | Ihre Berechtigung für das Produkt wird in einen ungültigen Zustand, der verhindert, dass eine Lizenz erstellt werden.   |
| 0x803F8009<br/>0x803F800A   | Der Testzeitraum für die app ist abgelaufen.   |
| 0x803F8190   |  Die Lizenz kann nicht mit das Produkt in der aktuellen Land oder Region des Geräts verwendet werden.  |
| 0x803F81F5<br/>0x803F81F6<br/>0x803F81F7<br/>0x803F81F8<br/>0x803F81F9   |  Sie haben die maximale Anzahl von Geräten erreicht, die mit Spiele und apps aus dem Store verwendet werden kann. Um dieses Spiel oder die app auf dem aktuellen Gerät zu verwenden, müssen Sie zunächst entfernen Sie ein anderes Gerät aus dem Konto.  |
| 0x803F9000<br/>0x803F9001    |  Die Lizenz ist abgelaufen oder beschädigt. Um diesen Fehler zu beheben, führen Sie die [Problembehandlung für Windows-apps](https://support.microsoft.com/help/4027498/windows-run-the-troubleshooter-for-windows-apps) zum Zurücksetzen der Store-Caches.     |
| 0x803F9006    |  Der Vorgang konnte nicht abgeschlossen werden, da der Benutzer, die für dieses Produkt berechtigt ist nicht an das Gerät mit ihrem Microsoft-Konto angemeldet ist.            |
| 0x803F9008<br/>0x803F9009    |  Das Gerät ist offline. Das Gerät muss für dieses Produkt online sein.            |
| 0x803F900A    |  Das Abonnement ist abgelaufen.            |


## <a name="self-install-update-error-codes"></a>Selbst installieren Update-Fehlercodes

Die folgenden Fehlercodes beziehen sich auf [sich selbst installieren von paketupdates](../packaging/self-install-package-updates.md).

|  Fehlercode  |  Beschreibung  |
|--------------|---------------|
| 0x803F6200   | Zustimmung des Benutzers ist erforderlich, um das paketupdate herunterladen.               |
| 0x803F6201   | Zustimmung des Benutzers wird zum Herunterladen und installieren Sie das paketupdate erforderlich.                                                  |
| 0x803F6203   | Zustimmung des Benutzers ist erforderlich, um das paketupdate zu installieren.                                         |
| 0x803F6204   | Zustimmung des Benutzers ist erforderlich, um das paketupdate heruntergeladen werden, da der Download auf einem getakteten Netzwerk-Verbindung durchgeführt wird.                                             |
| 0x803F6206   | Zustimmung des Benutzers ist erforderlich, herunterladen und installieren das paketupdate, da der Download auf einem getakteten Netzwerk-Verbindung durchgeführt wird.     |


## <a name="related-topics"></a>Verwandte Themen

* [In-App-Käufe und Testversionen](in-app-purchases-and-trials.md)
* [Abrufen von Produktinformationen zu Apps und Add-Ons](get-product-info-for-apps-and-add-ons.md)
* [Abrufen von Lizenzinformationen zu Apps und Add-Ons](get-license-info-for-apps-and-add-ons.md)
* [Aktivieren von In-App-Käufen von Apps und Add-Ons](enable-in-app-purchases-of-apps-and-add-ons.md)
* [Unterstützen von Käufen konsumierbarer Add-Ons](enable-consumable-add-on-purchases.md)
* [Aktivieren von Abonnement-Add-Ons für die App](enable-subscription-add-ons-for-your-app.md)
* [Implementieren einer Testversion Ihrer App](implement-a-trial-version-of-your-app.md)
