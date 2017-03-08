---
author: jnHs
Description: "Im Bericht „Käufe” des Windows Dev Center-Dashboards können Sie sehen, wer Ihre App erworben hat. Außerdem können Sie demografische und plattformspezifische Details einsehen."
title: "Bericht „Käufe“"
ms.assetid: 21126362-F3CD-4006-AD3F-82FC88E3B862
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: a668c3d03c11ac4c6c27cddeefafeb3c42caf1e3
ms.lasthandoff: 02/07/2017

---

# <a name="acquisitions-report"></a>Bericht „Käufe“


Im Bericht **Käufe** des Windows Dev Center-Dashboards können Sie sehen, wer Ihre App erworben hat. Außerdem können Sie demografische und plattformspezifische Details einsehen. Sie können diese Informationen in Ihrem Dashboard anzeigen oder [den Bericht herunterladen](download-analytic-reports.md), um die Daten offline anzuzeigen. Sie können diese Daten auch programmgesteuert mit der Methode [get app acquisitions](../monetize/get-app-acquisitions.md) der [Windows Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

In diesem Bericht steht „Kauf“ für einen neuen Kunden, der eine Lizenz Ihrer App erworben hat (entweder für eine kostenpflichtige oder eine kostenlose App).

> **Wichtig**  Im Bericht **Käufe** sind keine Daten über Erstattungen, Rückbuchungen, Rückvergütungen usw. enthalten. Besuchen Sie [Auszahlungszusammenfassung](payout-summary.md), um die Erträge aus Ihren Apps zu schätzen. Klicken Sie im Abschnitt **Reserviert** auf den Link **Reservierte Transaktionen herunterladen**.



## <a name="apply-filters"></a>Anwenden von Filtern


Im oberen Seitenbereich können Sie **Filter anwenden** erweitern, um alle Daten auf dieser Seite nach Datumsbereich und/oder Gerätetyp zu filtern.

-   **Datum**: Der Standardfilter lautet **Letzte 30 Tage**, aber er kann bis auf **Letzte 12 Monate** erweitert werden.
-   **Gerätetyp**: Die Standardeinstellung ist **Alle Geräte**. Wenn Daten für Käufe nur für einen bestimmten Gerätetyp angezeigt werden sollen, können Sie hier einen bestimmten auswählen.

Die Informationen in den unten angezeigten Diagrammen beziehen sich auf den unter **Filter anwenden** ausgewählten Zeitraum.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den im Abschnitt **Filter anwenden** ausgewählten Zeitraum. Standardmäßig gehören dazu Daten für alle Gerätetypen, sofern Sie nicht mithilfe von **Filter anwenden** einen bestimmten Gerätetyp herausgefiltert haben.

## <a name="acquisitions"></a>Käufe


Das Diagramm **Käufe** zeigt, wie oft Ihre App im ausgewählten Zeitraum pro Tag oder Woche gekauft wurde. (Wenn Sie die Daten über einen längeren Zeitraum mithilfe von **Filter anwenden** filtern, werden die Daten nach Woche gruppiert.)

Sie können auch anzeigen, wie oft die App während ihrer gesamten Lebensdauer gekauft wurde. Zeigt den kumulierten Gesamtwert aller Käufe an (ab der ersten Veröffentlichung Ihrer App).

Optional können Sie die Ergebnisse nach Markt und/oder Betriebssystemversion filtern.

## <a name="customer-demographic"></a>Kundendemografie


Das Diagramm **Kundendemografie** zeigt demografische Informationen zu den Personen, die Ihre App erworben haben. Sie können sehen, wie viele Käufe (im ausgewählten Zeitraum) von Personen einer bestimmten Altersgruppe getätigt wurden und welches Geschlecht die Käufer hatten.

> **Hinweis**  Einige Kunden haben festgelegt, dass sie diese Informationen nicht freigeben möchten. Falls die Altersgruppe oder das Geschlecht nicht ermittelt werden konnten, wird der Kauf als **Unbekannt** kategorisiert.

 

## <a name="markets"></a>Märkte


Das Diagramm **Märkte** zeigt die Gesamtanzahl von Käufen im ausgewählten Zeitraum nach Markt. Standardmäßig wird der Markt mit den meisten Käufen an oberster Stelle vor den Märkten mit weniger Käufen angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Käufe** des Diagramms klicken.

## <a name="os-version"></a>Betriebssystemversion


Im Diagramm **Betriebssystemversion** wird die Gesamtzahl der Käufe entsprechend dem Betriebssystem des Kunden angezeigt (bzw. über [großvolumige Käufe durch Organisationen](organizational-licensing.md)). In einigen Fällen können diese Informationen jedoch nicht ermittelt werden. Die Betriebssystemversion wird dann als **Unbekannt** angegeben.



 

 

