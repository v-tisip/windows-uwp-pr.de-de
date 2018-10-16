---
author: jnHs
Description: The Health report in the Windows Dev Center dashboard lets you get data related to the performance and quality of your app, including crashes and unresponsive events.
title: Integritätsbericht
ms.assetid: 4F671543-1E91-4E59-88A3-638E3E64539A
ms.author: wdg-dev-content
ms.date: 06/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Integrität, Abstürze, reagiert nicht, App-Integrität, Integritätsdaten, Stapelüberwachung, CAB-Datei, Fehler, Fehler, Pdb, Symbole
ms.localizationpriority: medium
ms.openlocfilehash: 5f5bf63eae4b1504642e764265a7936bcd67c645
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4616284"
---
# <a name="health-report"></a>Integritätsbericht

Über den Bericht **Integrität** im Windows Dev Center-Dashboard können Sie Daten zur Leistung und Qualität Ihrer App, einschließlich App-Abstürzen, abrufen. Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen. Bei Bedarf können Sie Stapelüberwachungen und/oder CAB-Dateien für weitere Debugzwecke anzeigen.

Sie können die Daten in diesem Bericht aber auch programmgesteuert mit der [Microsoft Store-REST-API für Analysen](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.


## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist **72 H** (72 Stunden), Sie können stattdessen aber auch **30D** auswählen, um die Daten der letzten 30Tage anzuzeigen. Beachten Sie, dass Daten in Ihre lokale Zeitzone für die Ansicht **72 H** und in UTC für die **30d** -Ansicht angezeigt werden.

Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach Paketversion, Markt und/oder Gerätetyp zu filtern.

-   **Paketversion**: Die Standardeinstellung ist **Alle**. Wenn Ihre App mehr als ein Paket enthält, können Sie hier ein bestimmtes Paket auswählen.
-   **Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten auf einen oder mehrere Märkte begrenzen.
-   **Gerätetyp**: Die Standardeinstellung ist **Alle**, Sie können jedoch festlegen, dass nur Daten für einen bestimmten Gerätetyp angezeigt werden. Beachten Sie, dass die Kategorie **Andere** Geräte enthält, für die der Hersteller/ das Modell erkannt wird, wir diese allerdings nicht in eine der vordefinierten Kategorien einbeziehen, die in diesem Filter angezeigt werden. Für diese Geräte kann das Modells im Abschnitt **Fehlerprotokoll** des Berichts **Fehlerdetails** angezeigt werden.  
-   **Betriebssystemversion**: Die Standardeinstellung lautet **Alle BS-Versionen**, Sie können jedoch eine bestimmte Version des Betriebssystems auswählen.
-   **Betriebssystemversion**: Die Standardeinstellung lautet **Alle BS-Versionen**. Sie können jedoch eine bestimmte Version des **Betriebssystems** auswählen.
-   **Sandbox**: der Standardwert ist **Einzelhandel**. Für Produkte, die eine Sandbox mit mehreren Entwicklungen verwenden (z.B. Spiele mit Xbox Live), können Sie hier einen spezifischen Wert auswählen. (Wenn Ihr Produkt keine Sandboxes verwendet, zeigt dieser Filter nur **Einzelhandel** an und ist nicht anwendbar.)
-   **Architektur**: Die Standardeinstellung lautet **Alle Architekturen**. Sie können jedoch einen bestimmten Typ der Systemarchitektur auswählen. Dieser Filter ist nur verfügbar, wenn **30D** ausgewählt ist.
-   **PRAID**: die Standardeinstellung ist **Alle**. Wenn Sie bei der Erstellung Ihres App-Pakets mehrere App-IDs relativ zu den Paketen definieren (PRAIDs), können Sie festlegen, dass nur Daten im Zusammenhang mit einem PRAID angezeigt werden. Dieser Filter wird nicht angezeigt, wenn Sie nicht mehrere PRAIDs definiert haben.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den ausgewählten Zeitraum und alle von Ihnen ausgewählten Filter. In einigen Abschnitten können Sie zusätzliche Filter anwenden.


## <a name="failure-hits"></a>Fehlertreffer

Das Diagramm **Fehlertreffer** zeigt die Anzahl von täglichen Abstürzen und Ereignissen, die Kunden bei der Nutzung Ihrer App im ausgewählten Zeitraum festgestellt haben. Jeder Ereignistyp, der in der App aufgetreten ist, wird separat überwacht: Abstürze, Blockaden, JavaScript-Ausnahmen und Speicherfehler.

Wenn die **30d** Zeitraum aktiviert ist, sehen Sie Kreis Marker. Diese darstellen eine erhebliche Erhöhung oder in einem bestimmten Wert, den wir glauben, dass Sie kennen sollten verringern. Das Datum, an dem die Kreis angezeigt wird, steht das Ende der Woche, in der wir eine erhebliche Erhöhung oder Verringerung im Vergleich zur vorherigen Woche davor erkannt. Um weitere Informationen zu Änderungen zu sehen, zeigen Sie auf den Kreis.  

> [!TIP]
> Sie können weitere Einblicke im Zusammenhang mit erhebliche Änderungen an der letzten 30 Tage im [Bericht](insights-report.md)anzeigen.

## <a name="failure-hits-by-market"></a>Fehlertreffer nach Markt

Das Diagramm **Fehlertreffer nach Markt** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Markt an.

Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen. Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Anwendersitzungen sortiert sind. Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.


## <a name="package-version"></a>Paketversion

Das Diagramm **Paketversion** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Paketversion an. In der Standardeinstellung wird die Paketversion mit den meisten Treffern an oberster Stelle vor den Märkten mit weniger Treffern angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken.

## <a name="failures"></a>Fehler

Das Diagramm **Fehler** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Fehlername an. Jeder Fehlername besteht aus vier Teilen: eine oder mehrere Problemklassen, Ausnahme/Fehlerprüfcode, der Name des Image/Treibers, in dem der Fehler aufgetreten ist, und der zugehörige Funktionsname. In der Standardeinstellung wird der Fehler mit den meisten Treffern an oberster Stelle vor den Fehlern mit weniger Treffern angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken. Außerdem wird für die einzelnen Fehler der Prozentsatz der Gesamtanzahl von Fehlern angezeigt.

> [!TIP]
> Von Zeit zu Zeit sehen Sie in diesem Abschnitt einen Eintrag **Unbekannt**. Dies passiert, wenn wir trotz aller Bemühungen, keine vollständigen Detailinformationen für einen oder mehrere Fehler erfassen können. Diese werden alle zusammen unter **Unbekannt** gruppiert. In den meisten Fällen tritt dies aufgrund von Speichereinschränkungen auf. Dies kann jedoch auch aufgrund von Datenschutzeinstellungen des Geräts, Netzwerkverbindungsproblemen, teilweise/beschädigten Absturzabbildern und anderen Faktoren auftreten.
>
> Wenn **!unbekannt** im Rahmen seines Fehlernamens angezeigt wird, bedeutet dies, dass keine Symbole vorhanden waren und wir den Fehlernamen daher nicht identifizieren konnten. Stellen Sie sicher, dass Ihr Paket Symbole zum Abrufen des genauen Fehlers bei der Analyse enthält. Weitere Informationen finden Sie unter [Konfigurieren eines App-Pakets](../packaging/packaging-uwp-apps.md#configure-an-app-package). Im Gegensatz dazu bedeuten Fehlernamen, die **!unknown_error_in_** und **!unknown_function** enthalten, dass das Sammeln der Informationen aus verschiedenen anderen Gründen nicht durchgeführt werden konnte.

Wählen Sie zum Anzeigen der **Fehlerdetails** für einen bestimmten Fehler den Fehlernamen aus. Wenn Sie Symboldateien eingefügt haben, beinhaltet der Bericht **Fehlerdetails** die Anzahl der Fehlertreffer im letzten Monat sowie ein Fehlerprotokoll, in dem die entsprechenden Details (Datum, Paketversion, Gerätetyp, Gerätemodell, Betriebssystembuild) sowie ein Link zu der Ablaufverfolgung und/oder einer CAB-Datei, wenn verfügbar, aufgeführt werden.

> [!TIP]
> CAB-Dateien sind nur verfügbar, wenn Fehler auf einem Computer mit einer Windows-Insider-Build auftreten, daher haben nicht alle Fehler die Option zum Herunterladen einer CAB-Datei. Um nur Fehler anzuzeigen, die CAB-Dateien verfügen, select- **Fehler mit Downloads** im Abschnitt Filter. Sie können auch klicken Sie auf die **Links** im **Fehlerprotokoll** zum Sortieren der Ergebnisse, sodass Fehler, die CAB-Dateien enthalten am oberen Rand der Liste angezeigt werden.

Auf der Seite " **Fehlerdetails** " Sie sehen außerdem das **Stapel Verbreitung** Diagramm, der angezeigt wird, im oberen Bereich dasteht, die auf den Fehler beigetragen, sortiert nach dem Prozentsatz, und das Diagramm **Gerätekonfiguration (30 D)** , die Details zu den Konfiguration von Geräten, die der Fehler aufgetreten ist. 


## <a name="crash-free-sessions-and-devices-30d"></a>Absturz-freie Sitzungen und Geräte (30d)

Das **Sitzungen Absturz frei und Geräte** Diagramm zeigt den Prozentsatz der Geräte oder benutzersitzungen, die nicht in den letzten 30 Tagen abgestürzt ist. Diese Informationen können Sie die zu verstehen, wie Allgemein Ihrer Abstürze Ihre Benutzer auswirken. Beispielsweise könnte eine app 10.000 Abstürze in einem Tag haben. Wenn 90 % der Geräte betroffen sind, dann können Sie wahrscheinlich, die als kritische klassifizieren und handeln, um es sofort zu beheben. Allerdings, die nur 5 % von Geräten mit Ihrer app darstellt, möglicherweise niedriger Priorität sein.

Dieses Diagramm enthält zwei Registerkarten:
- **Absturz-freie Geräte**: Zeigt den Prozentsatz der eindeutigen Geräte, die jedoch auf jeden Tag (in den letzten 30 Tagen) tritt kein Fehler auf.
- **Absturz-freie Sitzungen**: Zeigt den Prozentsatz von benutzersitzungen, die jedoch auf jeden Tag (in den letzten 30 Tagen) tritt kein Fehler auf.


 

 
