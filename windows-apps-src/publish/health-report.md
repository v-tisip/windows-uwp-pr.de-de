---
author: jnHs
Description: "Über den Bericht „Integrität“ im Windows Dev Center-Dashboard können Sie Daten zur Leistung und Qualität Ihrer App einschließlich App-Abstürzen abrufen."
title: "Bericht „Integrität“"
ms.assetid: 4F671543-1E91-4E59-88A3-638E3E64539A
translationtype: Human Translation
ms.sourcegitcommit: 2481343772a6cf8af0667dc0796ed455dba1eaee
ms.openlocfilehash: a92a2ab8f11c46217d1d7b63f86c5bf68757d3fb

---

# Bericht „Integrität“


Über den Bericht **Integrität** im Windows Dev Center-Dashboard können Sie Daten zur Leistung und Qualität Ihrer App, einschließlich App-Abstürzen, abrufen. Sie können diese Daten in Ihrem Dashboard (**Analyse** > **Integrität**) anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen. Bei Bedarf können Sie Stapelüberwachungen für weitere Debugzwecke anzeigen. Sie können diese Daten jedoch auch programmgesteuert mit der [Windows Store-REST-API für Analysen](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.


> **Hinweis**  Wenn Sie bereits Apps veröffentlicht und Leistungsdaten angezeigt haben, werden Sie möglicherweise feststellen, dass hier eine höhere Anzahl von Abstürzen und Ereignissen gemeldet wird. Das liegt daran, dass wir in diesem Bericht mehr Daten angeben können, sodass Sie ein vollständiges Bild erhalten.

## Anwenden von Filtern


Im oberen Seitenbereich können Sie **Filter anwenden** erweitern, um alle Daten auf dieser Seite nach Datumsbereich, Paketversion, Gerätetyp und/oder Betriebssystemversion zu filtern.

-   **Datum**: Der Standardfilter lautet **Letzte 72Stunden**, er kann jedoch bis auf **Letzte 30Tage** erweitert werden.
-   **Paketversion**: Die Standardeinstellung ist **Alle Versionen**. Wenn Ihre App mehr als eine Paketversion enthält, können Sie eine spezifische Version auswählen.
-   **Gerätetyp**: Der Standardwert lautet **Alle Geräte**, Sie können jedoch ein bestimmtes Gerät auswählen (**PC**, **Telefon**, **Konsole**, **IoT**, **Hologramm** oder **Unbekannt**).
-   **Betriebssystemversion**: Die Standardeinstellung lautet **Alle BS-Versionen**, Sie können jedoch eine bestimmte Version des Betriebssystems auswählen.

Die Informationen in allen unten angezeigten Diagrammen beziehen sich auf den im Abschnitt **Filter anwenden** ausgewählten Zeitraum. Standardmäßig gehören dazu Daten für alle Paketversionen, sofern Sie nicht mithilfe von **Filter anwenden** eine Version herausgefiltert haben.

## Gesamtanzahl der Abstürze und Ereignisse


Das Diagramm **Failure hits** (zuvor: **Gesamtanzahl der Abstürze und Ereignisse**) zeigt die Anzahl von täglichen Abstürzen und Ereignissen an, die Kunden bei der Nutzung Ihrer App im ausgewählten Zeitraum festgestellt haben. Jeder Ereignistyp, der in der App aufgetreten ist, wird separat überwacht: Abstürze, Blockaden, JavaScript-Ausnahmen oder Speicherfehler.

Optional können Sie die Ergebnisse nach Markt und/oder Betriebssystemversion filtern.

## Märkte


Das Diagramm **Märkte** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Markt an. In der Standardeinstellung wird der Markt mit den meisten Treffern an oberster Stelle vor den Märkten mit weniger Treffern angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken.

## Paketversion


Das Diagramm **Paketversion** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Paketversion an. In der Standardeinstellung wird die Paketversion mit den meisten Treffern an oberster Stelle vor den Märkten mit weniger Treffern angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken.

## Fehler


Das Diagramm **Fehler** zeigt die Gesamtanzahl von Abstürzen und Ereignissen im ausgewählten Zeitraum nach Fehlername an. In der Standardeinstellung wird der Fehler mit den meisten Treffern an oberster Stelle vor den Fehlern mit weniger Treffern angezeigt. Sie können die Reihenfolge umkehren, indem Sie auf den Pfeil in der Spalte **Treffer** des Diagramms klicken. Außerdem wird für die einzelnen Fehler der Prozentsatz der Gesamtanzahl von Fehlern angezeigt.

Wählen Sie zum Anzeigen der **Fehlerdetails** für einen bestimmten Fehler den Fehlernamen aus. Wenn Sie PDB-Symboldateien eingefügt haben, beinhaltet der Bericht **Fehlerdetails** die Anzahl der Fehlertreffer im letzten Monat sowie ein Fehlerprotokoll, in dem die entsprechenden Details (Datum, Paketversion, Gerätetyp, Gerätemodell, Betriebssystembuild) sowie ein Link zu der Ablaufverfolgung aufgeführt werden.

 

 



<!--HONumber=Nov16_HO1-->


