---
author: jnHs
Description: The Acquisitions report in the Windows Dev Center dashboard lets you see who has acquired and installed your app, along with demographic and platform details.
title: Bericht „Käufe“
ms.assetid: 21126362-F3CD-4006-AD3F-82FC88E3B862
ms.author: wdg-dev-content
ms.date: 02/13/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Käufe, App-Verkäufe, App-Downloads, Installationen, Trichter, Käufe, Konvertierungen, Kanal, App-Seitenaufrufe
ms.localizationpriority: high
ms.openlocfilehash: d1675b3a2ffe879585ea2fd3792b47e7bdc7a8af
ms.sourcegitcommit: 980e604c3767e7a73619d027bebd78cf4bfe9678
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="acquisitions-report"></a>Bericht „Käufe“


Im Bericht **Käufe** im Windows Dev Center-Dashboards können Sie sehen, wer Ihre App erworben und installiert hat. Außerdem können Sie demografische und plattformspezifische Details einsehen. Außerdem können Sie damit Informationen abrufen, wie Kunden unter Windows10 (einschließlich Xbox) zum Eintrag Ihrer App gelangt sind.

Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen. Sie können diese Daten aber auch programmgesteuert mit unseren [REST-API für Analysen](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

In diesem Bericht steht **Kauf** für einen neuen Kunden, der eine Lizenz Ihrer App erworben hat (entweder für eine kostenpflichtige oder eine kostenlose App). **Installieren** bezieht sich auf die App, die auf einem Windows10-Gerät installiert wird.

> [!IMPORTANT]
> Im Bericht **Käufe** sind keine Daten über Erstattungen, Rückbuchungen, Rückvergütungen usw. enthalten. Um die Erträge aus Ihren Apps zu schätzen, besuchen Sie [Auszahlungszusammenfassung](payout-summary.md). Klicken Sie im Abschnitt **Reserviert** auf den Link **Reservierte Transaktionen herunterladen**.
>
> Mit Ausnahme von Informationen zu den Seitenaufrufen (wie unten beschrieben) enthält dieser Bericht keine Daten im Zusammenhang mit Kunden, die eine App erwerben, ohne auf einem Microsoft-Konto angemeldet zu sein.


## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.

Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach Markt und/oder Gerätetyp zu filtern.

-   **Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten für Verkäufe auf einen oder mehrere Märkte begrenzen.
-   **Gerätetyp**: Die Standardeinstellung ist **Alle Geräte**. Wenn Daten für Käufe nur für einen bestimmten Gerätetyp angezeigt werden sollen (beispielsweise PCs, Konsolen oder Tablets), können Sie hier einen bestimmten angeben.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter. In einigen Abschnitten können Sie zusätzliche Filter anwenden.


## <a name="acquisitions"></a>Käufe

Das Diagramm **Käufe** zeigt, wie oft Ihre Käufe (ein neuer Kunde, der eine Lizenz für Ihre App ausgewählt hat) im ausgewählten Zeitraum pro Tag oder Woche gekauft wurde. (Wenn Sie **Filter anwenden** zum Anzeigen von Daten für eine längere Dauer verwenden, werden die Kaufdaten nach Woche gruppiert.) Nur Käufe von Kunden, die auf einem gültigen Microsoft-Konto angemeldet sind, sind in diesem Diagramm enthalten.

Sie können auch anzeigen, wie oft die App während ihrer gesamten Lebensdauer gekauft wurde, indem Sie **App Insgesamt** auswählen. Zeigt den kumulierten Gesamtwert aller Käufe an (ab der ersten Veröffentlichung Ihrer App).

Sie können optional die Ergebnisse danach filtern, ob die Übernahme vom Client oder einem webbasierten Store und/oder Betriebssystemversion stammt.

> [!NOTE]
> Sie können diese Daten auch programmgesteuert mit der Methode [Abrufen von App-Käufen](../monetize/get-app-acquisitions.md) unserer [Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

## <a name="installs"></a>Installiert

Das Diagramm **Installiert** zeigt an, wie häufig festgestellt wurde, dass ein Kunde Ihre App über den ausgewählten Zeitraum erfolgreich auf Windows10-Geräten (einschließlich Xbox One Konsolen) installiert hat. Es wird die Gesamtanzahl zusammen mit einem Diagramm dargestellt, das die Installation pro Tag oder Woche anzeigt (abhängig von der Dauer, die Sie ausgewählt haben). Optional können Sie die Ergebnisse nach Paketversion filtern.

Zur Gesamtübersicht der Installationen gehören:
-   **Installationen auf mehreren Windows 10-Geräten.** Wenn derselbe Kunde Ihre App beispielsweise aus zwei Windows 10-PCs und einer Xbox One Konsole installiert, werden drei Installationen gezählt.
-   **Erneute Installationen.** Wenn eine Kunde Ihre App beispielsweise heute installiert, morgen deinstalliert und im nächsten Monat erneut installiert, werden zwei Installationen gezählt.

Von der Gesamtansicht der Installationen sind ausgenommen:
-   **Installationen auf Nicht-Windows 10-Geräten.** Wenn Ihre App frühere Betriebssystemversionen z.B. Windows8.x oder Windows Phone8.x unterstützt, zählen wir keine Installationen auf diesen Geräten.
-   **Deinstallationen.** Wenn ein Kunde Ihre App vom Gerät deinstalliert, wird diese nicht von der Gesamtanzahl der Installationen abgezogen.
-   **Updates.** Wenn ein Kunde Ihre App beispielsweise heute installiert und eine Woche später eine App-Aktualisierung installiert, zählt dies nur als eine Installation.
-   **Vorinstallationen.** Wenn ein Kunde ein Gerät kauft, auf dem Ihre App vorinstalliert wurde, zählt dies nicht als Installation.
-   **Vom System initiierte Installationen.** Wenn Windows aus irgendeinem Grund Ihre App automatisch installiert, zählt dies nicht als Installation.

> [!NOTE]
> Sie können diese Daten auch programmgesteuert mit der Methode [Abrufen von App-Installationen](../monetize/get-app-installs.md) unserer [Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

## <a name="acquisition-funnel"></a>App-Erwerbstrichter

Der **Erwerbstrichter** zeigt an, wie viele Kunden jeden Schrittdes Trichters ausgeführt hat, von der Store-Seite mit der App bis hin zur Anzeige des Wechselkurses. Diese Daten helfen Ihnen Bereiche zu identifizieren, in denen Sie mehr investieren möchten, um die Käufe, Installationen oder Nutzung zu erhöhen.

> [!IMPORTANT]
> Der **Erwerbstrichter** zeigt nur Daten für Kunden auf Windows 10 (einschließlich Xbox) über die letzten 90 Tage an.

Die Schritte im Trichter sehen folgendermaßen aus:

- **Seitenaufrufe**: Dieser Wert gibt die Gesamtanzahl der Store-Einträge Ihrer App an, einschließlich der Kontakte, die nicht mit einem Microsoft-Konto angemeldet sind. Dies umfasst nicht die Daten von Kunden, die diese Informationen nicht an Microsoft weitergeben möchten.
- **Käufe**: die Anzahl der neuen Kunden, die eine Lizenz für Ihre App (Wenn sie mit ihrem Microsoft-Konto angemeldet sind) innerhalb von 48 Stunden nach Ansicht im Store-Eintrag erhalten haben.
- **Installiert**: die Anzahl der Kunden, die die App nach dem Erwerb installiert haben.
- **Verwendung**: die Anzahl der Kunden, die die App nach der Installation genutzt haben.

Sie können optional die Ergebnisse nach Geschlecht und/oder Altersgruppe filtern, sowie durch benutzerdefinierte Kampagnen-ID

> [!NOTE]
> Sie können diese Daten auch programmgesteuert mit der Methode [Abrufen von App-Erwerbstrichterdaten](../monetize/get-acquisition-funnel-data.md) unserer [Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

## <a name="markets"></a>Märkte

Das Diagramm **Märkte** zeigt die Gesamtanzahl von Käufen für die Installationen im ausgewählten Zeitraum für jeden Markt an, auf dem Ihre App erhältlich ist. Sie können auswählen, ob Sie Daten für **Käufe** oder **Installiert** anzeigen möchten.

Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen. Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Käufen oder Installationen sortiert sind. Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.


## <a name="customer-demographic"></a>Kundendemografie

Das Diagramm **Kundendemografie** zeigt demografische Informationen zu den Personen, die Ihre App erworben haben. Sie können sehen, wie viele Käufe (im ausgewählten Zeitraum) von Personen einer bestimmten Altersgruppe getätigt wurden und welches Geschlecht die Käufer hatten.

> [!NOTE]
> Einige Kunden haben festgelegt, dass sie diese Informationen nicht freigeben möchten. Falls die Altersgruppe oder das Geschlecht nicht ermittelt werden konnten, wird der Kauf als **Unbekannt** kategorisiert.

 

## <a name="app-page-views-and-conversions-by-channel"></a>App-Seitenaufrufe und Konvertierungen nach -Kanal

Mit dem Diagramm **App-Seitenaufrufe und Konvertierungen nach -Kanal** können Sie sehen, wie Kunden unter Windows 10 zu dem Eintrag Ihrer App im ausgewählten Zeitraum gelangt sind.

In diesem Diagramm bezieht sich ein *Kanal* auf die Methode, über die ein Kunde zu der Eintragsseite für Ihre App gelangt ist (z.B. durch Browsen und Suchen im Store, über einen Link von einer externen Website oder einen Link aus einer Ihrer benutzerdefinierten Kampagnen usw.). Die folgenden Kanaltypen sind enthalten:

-   **Store-Verkehr:** Der Kunde hat den Store durchsucht und ist dabei auf den Eintrag Ihrer App aufmerksam geworden.
-   **Benutzerdefinierte Kampagne:** Der Kunde ist einem Link gefolgt, der eine [benutzerdefinierte Kampagnen-ID](create-a-custom-app-promotion-campaign.md) verwendet.
-   **Sonstiges:** Der Kunde ist einem externen Link von einer Website (ohne benutzerdefinierte Kampagnen-ID) zu Ihrem App-Eintrag gefolgt oder der Kunde ist einem Link zu Ihrem App-Eintrag gefolgt, der von einer Onlinesuchmaschine zurückgegeben wurde.

Ein *Seitenaufruf* bedeutet, dass ein Kunde die Store-Eintragsseite für Ihre App über den webbasierten Store oder innerhalb der Store-App auf Windows10 angezeigt hat. Dies umfasst Kontakte, die nicht mit einem Microsoft-Konto angemeldet sind. Einige Kunden haben festgelegt, das sie Microsoft diese Informationen nicht zur Verfügung stellen möchten.

*Konvertierung* bedeutet, dass ein Kunde (der mit einem Microsoft-Konto angemeldet ist) eine Lizenz für Ihre App (entweder für eine kostenpflichtige oder eine kostenlose App) neu erworben hat.

Die Seitenansicht und Konvertierungszahlen geben nicht die Anzahl an eindeutigen Kunden wieder. Informationen für Konvertierungszahlen finden Sie im [Erwerbstrichter](#acquisition-funnel)-Diagramm.

> [!NOTE]
> Der Kunden gelangt möglicherweise zu dem Eintrag Ihrer App durch Klicken auf eine nicht von Ihnen erstellte, benutzerdefinierte Kampagne. Wir zählen jeden Seitenaufruf innerhalb einer Sitzung mit der Kampagnen-ID, die der Kunde zuerst im Store eingibt. Wir fügen der Kampagnen-ID anschließend Konvertierungen für alle Käufe innerhalb von 24 Stunden hinzu. Aus diesem Grund sehen Sie möglicherweise eine höhere Anzahl an Gesamtkonvertierungen als die Konvertierungen für Ihre Kampagnen-ID anzeigt, und Sie haben möglicherweise Konvertierungen oder Add-On-Konvertierungen, die keine Seitenansichten haben.

> [!NOTE]
> Sie können diese Daten auch programmgesteuert mit der Methode [Abrufen von App-Konvertierungen nach Kanal](../monetize/get-app-conversions-by-channel.md) unserer [Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

## <a name="app-page-views-and-conversions-by-campaign-id"></a>App-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID

Mit dem Diagramm **App-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID** können Sie Konvertierungen und Seitenaufrufe wie oben beschrieben für jede Ihrer [benutzerdefinierten Werbekampagnen](create-a-custom-app-promotion-campaign.md) nachverfolgen,. Die höchsten Kampagnen-IDs werden angezeigt, und mithilfe der Filter können Sie bestimmte Kampagnen-ID einbeziehen oder ausschließen.

## <a name="total-campaign-conversions"></a>Gesamtanzahl der Konvertierungen pro Kampagne

Das Diagramm der **Gesamtanzahl der Konvertierungen pro Kampagne** enthält die Gesamtanzahl der App- und Add-On-Konvertierungen aus allen Ihren benutzerdefinierten Kampagnen im ausgewählten Zeitraum.





 

 
