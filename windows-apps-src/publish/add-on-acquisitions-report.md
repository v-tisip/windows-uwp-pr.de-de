---
author: jnHs
Description: The Add-on acquisitions report in the Windows Dev Center dashboard lets you see how many add-ons you've sold, along with demographic and platform details.
title: Bericht zu Add-On-Käufen
ms.assetid: F2DF9188-0A98-4AC3-81C0-3E2C37B15582
ms.author: wdg-dev-content
ms.date: 05/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-On-Verkäufe, Add-On-Käufe, IAP-Verkauf, In-App-Produkte, IAPS, Add-Ons
ms.localizationpriority: medium
ms.openlocfilehash: 019bb410e6ac65f9951f06052c78f40e9a5f32e2
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4962715"
---
# <a name="add-on-acquisitions-report"></a>Bericht zu Add-On-Käufen


Der Bericht " **Add-on-Käufe** " im Windows Dev Center-Dashboard können Sie sehen, wie viele Add-ons Sie, und Sie können demografische verkauft haben und plattformspezifische Details einsehen und zeigt Konvertierungsinformationen für Kunden unter Windows 10 (einschließlich Xbox). Sie können auch in der Nähe in Echtzeit Kaufdaten für den letzten oder 70-zwei Stunden-Zeitraum anzeigen.

Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen. Sie können diese Daten auch programmgesteuert mit der Methode [get add-on acquisitions](../monetize/get-in-app-acquisitions.md) der [Microsoft Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

In diesem Bericht bedeutet ein „Add-On-Kauf”, dass ein Kunde ein Add-On von Ihnen erworben hat (oder ohne dafür zu bezahlen, wenn Sie es kostenlos angeboten haben). Wenn ein Kunde mehrere Käufe desselben konsumierbaren Add-Ons getätigt hat, werden diese als separate Add-On-Käufe aufgeführt.

> [!IMPORTANT]
> Im Bericht **Add-On-Käufe** sind keine Daten über Erstattungen, Rückbuchungen, Rückvergütungen usw. enthalten. Besuchen Sie [Auszahlungszusammenfassung](payout-summary.md), um die Erträge aus Ihren Apps zu schätzen. Klicken Sie im Abschnitt **Reserviert** auf den Link **Reservierte Transaktionen herunterladen**.


## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben. Sie können auch **1 H** oder **72 Stunden** Kaufdaten für eine Stunde oder 70-zwei Stunden nahezu in Echtzeit anzeigen auswählen. Diese Zeiträume gelten nur auf der Registerkarte " **Add-on täglich** " des Diagramms **Add-on-Käufe** und auf der Registerkarte " **Käufe** " des Diagramms **Märkte** . 

Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach bestimmten Add-Ons, Markt und/oder Gerätetyp zu filtern.

-   **Add-On**: der Standardfilter lautet **Alle Add-Ons**, aber Sie können die Daten für ein oder mehrere Add-Ons der App begrenzen.
-   **Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten für Verkäufe auf einen oder mehrere Märkte begrenzen.
-   **Gerätetyp**: Die Standardeinstellung ist **Alle Geräte**. Wenn Daten für Käufe nur für einen bestimmten Gerätetyp angezeigt werden sollen (beispielsweise PCs, Konsolen oder Tablets), können Sie hier einen bestimmten angeben.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter. In einigen Abschnitten können Sie zusätzliche Filter anwenden.


## <a name="add-on-acquisitions"></a>Add-On-Käufe

Das Diagramm **Add-On-Käufe** zeigt, wie oft Ihre Add-Ons im ausgewählten Zeitraum pro Tag oder Woche gekauft wurde. (Wenn Sie die Daten über einen längeren Zeitraum mithilfe von **Filter anwenden** anzeigen, werden die Erwerbsdaten nach Woche gruppiert.)

Sie können auch anzeigen, wie oft die App während ihrer gesamten Lebensdauer gekauft wurde, indem Sie **Add-On Insgesamt** auswählen. Zeigt den kumulierten Gesamtwert aller Käufe an (ab der ersten Veröffentlichung Ihrer App).

Sie können optional die Ergebnisse danach filtern, ob der Erwerb der Add-On vom Client oder einem webbasierten Store und/oder Betriebssystemversion stammt.


## <a name="customer-demographic"></a>Kundendemografie

Das Diagramm **Kundendemografie** zeigt demografische Informationen zu den Kontakte, die Ihre Add-Ons erworben haben. Sie können sehen, wie viele Käufe (im ausgewählten Zeitraum) von Personen einer bestimmten Altersgruppe getätigt wurden und welches Geschlecht die Käufer hatten.

> [!NOTE]
> Einige Kunden haben festgelegt, dass sie diese Informationen nicht freigeben möchten. Falls die Altergruppe oder das Geschlecht nicht ermittelt werden konnten, wird der Kauf als **Unbekannt** kategorisiert.


## <a name="markets"></a>Märkte

Das Diagramm **Märkte** zeigt die Gesamtanzahl von Add-On-Käufen im ausgewählten Zeitraum für jeden Markt an, auf dem Ihre App erhältlich ist. 

Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen. Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Käufen oder Installationen sortiert sind. Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.


## <a name="add-on-page-views-and-conversions-by-campaign-id"></a>Add-On-Seitenaufrufe und -Konvertierungen nach Kampagnen-ID

Das Diagramm **Add-On-Seitenaufrufe und Konvertierungen nach Kampagnen-ID** zeigt die Gesamtanzahl der Add-On-Konvertierungen (Käufe) pro Kampagnen-ID im ausgewählten Zeitraum an und hilft Ihnen, Konvertierungen und Ansichten von Kunden unter Windows10 (einschließlich Xbox) für jede Seite der [benutzerdefinierte Werbekampagnen](create-a-custom-app-promotion-campaign.md) nachzuverfolgen. In diesem Diagramm werden nur die Add-On-Konvertierungen angezeigt.

> [!NOTE]
> Der Kunden gelangt möglicherweise zu dem Eintrag Ihrer App durch Klicken auf eine nicht von Ihnen erstellte, benutzerdefinierte Kampagne. Wir zählen jeden Seitenaufruf innerhalb einer Sitzung mit der Kampagnen-ID, die der Kunde zuerst im Store eingibt. Wir fügen der Kampagnen-ID anschließend Konvertierungen für alle Käufe innerhalb von 24 Stunden hinzu. Aus diesem Grund sehen Sie möglicherweise eine höhere Anzahl an Gesamtkonvertierungen als die Konvertierungen für Ihre Kampagnen-ID anzeigt, und Sie haben möglicherweise Konvertierungen oder Add-On-Konvertierungen, die keine Seitenansichten haben. 


## <a name="conversions-breakdown-by-campaign-id"></a>Aufschlüsselung der Konvertierungen nach Kampagnen-ID

Mit dem Diagramm **Aufschlüsselung der Konvertierungen nach Kampagnen-ID** können Sie Konvertierungen und Seitenaufrufe von Kunden unter Windows 10 wie oben beschrieben für jede Ihrer [benutzerdefinierten Werbekampagnen](create-a-custom-app-promotion-campaign.md) nachverfolgen,. Sowohl App- und Add-On-Konvertierungen werden nach Kampagnen-ID angezeigt.

In diesem Diagramm bedeutet eine *Seitenansicht*, dass sich ein Kunde den App-Store-Eintrag angesehen hat. *Konvertierung* bedeutet, dass ein Kunde eine Lizenz für die App oder Add-On (entweder für eine kostenpflichtige oder eine kostenlose App) oder für ein Add-On neu erworben hat.

Beachten Sie, dass die Seitenansicht und Konvertierungszahlen nicht die Anzahl an eindeutigen Kunden wiedergeben. 


## <a name="top-add-ons"></a>Wichtigste Add-Ons

Das Diagramm **Wichtigste Add-Ons** zeigt die Gesamtanzahl von Käufen für jedes Ihrer Add-Ons im ausgewählten Zeitraum nach Markt an, damit Sie sehen können, welche Add-Ons am beliebtesten sind. 



 

 
