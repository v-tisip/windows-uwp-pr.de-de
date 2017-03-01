---
author: shawjohn
Description: "Im Bericht zu Kanälen und Konvertierungen im Windows Dev Center-Dashboard können Sie sehen, wie Kunden unter Windows 10 zu dem Eintrag Ihrer App gelangt sind."
title: "Bericht zu Kanälen und Abschlüssen"
ms.assetid: C359B9FB-A17B-4A8E-B8EE-19F2F98AA4FF
ms.author: johnshaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Kanäle, Konvertierungen, Bericht, Analysen"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 60f639c6bad73273a6cc7f83cf65fdf321211ba1
ms.lasthandoff: 02/07/2017

---

# <a name="channels-and-conversions-report"></a>Bericht zu Kanälen und Abschlüssen


Im Bericht zu **Kanälen und Konvertierungen** im Windows Dev Center-Dashboard können Sie sehen, wie Kunden unter Windows 10 zu dem Eintrag Ihrer App gelangt sind. Sie können [benutzerdefinierte Werbekampagnen](create-a-custom-app-promotion-campaign.md) für Ihre App oder deren Add-Ons nachverfolgen und sehen, wie viele dieser Besuche zu neuen Käufen führen. Sie können diese Informationen in Ihrem Dashboard anzeigen oder [den Bericht herunterladen](download-analytic-reports.md), um die Daten offline anzuzeigen.

> **Wichtig**  In diesem Bericht werden nur Seitenaufrufe und Konvertierungsinformationen von Kunden unter Windows 10 angezeigt.

 

In diesem Bericht bezieht sich ein *Kanal* auf die Methode, über die ein Kunde zu der Eintragsseite für Ihre App gelangt ist (z. B. durch Browsen und Suchen im Store, über einen Link von einer externen Website oder einen Link aus einer Ihrer benutzerdefinierten Kampagnen usw.). Die folgenden Kanaltypen sind enthalten:

-   **Store-Verkehr:** Der Kunde hat den Store durchsucht und ist dabei auf den Eintrag Ihrer App aufmerksam geworden.
-   **Benutzerdefinierte Kampagne:** Der Kunde ist einem Link gefolgt, der eine [benutzerdefinierte Kampagnen-ID](create-a-custom-app-promotion-campaign.md) verwendet.
-   **Sonstiges:** Der Kunde ist einem externen Link von einer Website (ohne benutzerdefinierte Kampagnen-ID) zu Ihrem App-Eintrag gefolgt oder der Kunde ist einem Link zu Ihrem App-Eintrag gefolgt, der von einer Onlinesuchmaschine zurückgegeben wurde.

Ein *Seitenaufruf* bedeutet, dass ein Kunde die Store-Eintragsseite für Ihre App über den webbasierten Store oder innerhalb der Store-App auf Windows 10 angezeigt hat.

*Konvertierung* bedeutet, dass ein Kunde eine Lizenz für Ihre App (entweder für eine kostenpflichtige oder eine kostenlose App) oder für ein Add-On neu erworben hat.

Wir zeigen in diesem Bericht keine Umwandlungsquote an, da die Seitenaufrufe und Konvertierungszahlen nicht die Anzahl an eindeutigen Kunden wiedergibt.

Konvertierungsinformationen werden nur für Ihre benutzerdefinierten Kampagnen bereitgestellt. Für andere Kanaltypen sind nur Informationen zu den Seitenaufrufen in diesem Bericht enthalten.

> **Hinweis:** Der Kunden gelangt möglicherweise zu dem Eintrag Ihrer App durch Klicken auf eine nicht von Ihnen erstellte, benutzerdefinierte Kampagne. Um diese Möglichkeit zu berücksichtigen, zählen wir jeden Seitenaufruf innerhalb einer Sitzung mit der Kampagnen-ID, die der Benutzer zuerst im Store eingibt. Anschließend ordnen wir der Kampagnen-ID eine Konvertierung hinzu, wenn innerhalb von 24 Stunden ein Kauf Ihrer App vorgenommen wird. Wenn Sie den Bericht anzeigen, sehen Sie aus diesem Grunde möglicherweise Konvertierungen für Kampagnen, die Ihnen nicht bekannt vorkommen, eine höhere Gesamtanzahl der Konvertierungen als in der Aufschlüsselung der Konvertierungen und warum Sie Konvertierungen oder Add-On-Konvertierungen sehen, die keine Seitenaufrufe enthalten. Sie können die Aufschlüsselung der Konvertierungen nach Kampagnen-ID anzeigen, um nur die von Ihnen erstellen Kampagnen anzuzeigen und ihre Effektivität zu bewerten.


## <a name="apply-filters"></a>Anwenden von Filtern


Im oberen Seitenbereich können Sie **Filter anwenden** erweitern, um alle Daten auf dieser Seite nach Datumsbereich und/oder Markt zu filtern.

-   **Datum**: Der Standardfilter lautet **Letzte 30 Tage**, aber er kann bis auf **Letzte 12 Monate** erweitert werden.
-   **Markt**: Die Standardeinstellung ist **Alle Märkte**. Sie können einen bestimmten Markt auswählen, wenn auf dieser Seite nur Details der in diesem Markt ansässigen Kunden angezeigt werden sollen.
-   **Gerätetyp**: Der Standardfilter ist **Alle Geräte**. Sie können einen bestimmten Gerätetyp auswählen, wenn auf dieser Seite nur Daten von Kunden angezeigt werden sollen, die ein Gerät dieses Typs verwenden.

Die Informationen in allen unten aufgeführten Diagrammen beziehen sich auf den im Bereich **Filter anwenden** ausgewählten Zeitraum und entsprechen den von Ihnen hier ausgewählten Filtern.

## <a name="app-page-views-and-conversions-by-channel"></a>App-Seitenaufrufe und Konvertierungen nach -Kanal


In dem Diagramm **App-Seitenaufrufe und -Konvertierungen nach Kanal** ist dargestellt, wie häufig die Eintragsseite für Ihre App aufgerufen wurde und wie Kunden zu dieser Seite gelangt sind. Es enthält außerdem die Anzahl der Konvertierungen von benutzerdefinierten Kampagnen über den ausgewählten Zeitraum.

Auf der Registerkarte **Seitenaufrufe** dieses Diagramms ist dargestellt, wie oft die Eintragsseite für Ihre App über den ausgewählten Zeitraum angezeigt wurde. Aufrufe sind nach dem Kanaltyp gruppiert, über den der Kunde Ihren App-Eintrag gefunden hat.

Auf der Registerkarte **Konvertierungen** dieses Diagramms ist die Anzahl von Konvertierungen (neuer Käufe) über den ausgewählten Zeitraum für Kunden dargestellt, die über eine benutzerdefinierte Kampagne zu Ihrem App-Eintrag gelangt sind.

Weitere Informationen über Ihre gesamten App-Käufe, einschließlich der Käufe, die nicht über Links von einer benutzerdefinierten Kampagne erfolgten, und Käufe von Kunden mit anderen Betriebssystemversionen finden Sie im [Bericht „Käufe“](acquisitions-report.md).

 

## <a name="total-campaign-conversions"></a>Gesamtanzahl der Konvertierungen pro Kampagne


Das Diagramm der **Gesamtanzahl der Konvertierungen pro Kampagne** enthält die Gesamtanzahl der App- und Add-On-Konvertierungen aus Ihren benutzerdefinierten Kampagnen im ausgewählten Zeitraum.

## <a name="app-page-views-and-conversions-by-campaign-id"></a>App-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID


Im Diagramm **App-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID** wird die Anzahl von Seitenaufrufen und Konvertierungen für alle [Kampagnen-ID](create-a-custom-app-promotion-campaign.md) im ausgewählten Zeitraum angezeigt.

##  <a name="add-on-conversions-by-campaign-id"></a>Add-On-Konvertierungen nach Kampagnen-ID


Im Diagramm **Add-On-Konvertierungen nach Kampagnen-ID** wird die Anzahl von Add-On-Konvertierungen pro benutzerdefinierter Kampagnen-ID angezeigt.

Wenn eine App-Installation als Konvertierung für eine benutzerdefinierte Kampagne gezählt wird, werden Add-On-Einkäufe in der App ebenfalls als Konvertierungen für dieselbe benutzerdefinierte Kampagne gezählt.

Standardmäßig enthält der Bericht alle Add-Ons, deren Konvertierung über einen Link mit einer benutzerdefinierten Kampagnen-ID im ausgewählten Zeitraum erfolgt ist. Um Daten für ein bestimmtes Add-On anzuzeigen, wählen Sie es aus den **Abschnittsfiltern** aus.

## <a name="conversions-breakdown-by-campaign-id"></a>Aufschlüsselung der Konvertierungen nach Kampagnen-ID


Das Diagramm **Aufschlüsselung der Konvertierungen** zeigt folgende Details zu den Seitenaufrufen und Konvertierungen, die von benutzerdefinierten Kampagnen erzeugt wurden.

-   **ID:** Zeigt die spezifischen Kampagnen-IDs an.
-   **Seitenaufrufe:** Zeigt die Anzahl der Seitenaufrufe an, die mit der Kampagnen-ID des Kunden beim ersten Eintrag im Store gezählt wurden.
-   **App-Konvertierungen:** Zeigt die Anzahl der App-Konvertierungen aus der benutzerdefinierten Kampagne an.
-   **Add-On-Konvertierungen:** Zeigt die Anzahl der Add-On-Konvertierungen aus der benutzerdefinierten Kampagne an.


 

 

