---
author: shawjohn
Description: "Im Bericht „Installationen“ im Windows Dev Center-Dashboard sehen Sie, wie oft Ihre App erfolgreich auf Windows 10-Geräten installiert wurde."
title: "Bericht „Installationen“"
ms.author: johnshaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, App, Installationen, Installation, Bericht, Analysen
ms.assetid: 46c08fd2-00bd-4be5-b29f-01a3b5fea4c2
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 9e4dec61e275443db42b50ef9a231b5b3c46ffe4
ms.lasthandoff: 02/08/2017

---

# <a name="installs-report"></a>Bericht „Installationen“

Im Bericht **Installationen** im Windows Dev Center-Dashboard sehen Sie, wie oft Ihre App erfolgreich auf Windows 10-Geräten installiert wurde. Sie können diese Daten in Ihrem Dashboard anzeigen lassen, oder den [Bericht herunterladen](download-analytic-reports.md) und offline anzeigen.


## <a name="apply-filters"></a>Anwenden von Filtern


Im oberen Seitenbereich können Sie **Filter anwenden** erweitern, um alle Daten auf dieser Seite nach Datum, Gerätetyp und/oder Paketversion zu filtern.

-   **Datum**: Der Standardfilter ist **Letzte 30 Tage**, aber Sie können diesen Wert auf bis zu **Letzte 12 Monate** erweitern.
-   **Gerätetyp**: Der Standardfilter ist **Alle Geräte**, aber Sie können einen bestimmten Gerätetyp wählen (**PC**, **Smartphone**, **Tablet**, **Virtueller Computer**, **IoT**, **Hologramme**, **Konsole**, **Sonstige** oder **Unbekannt**).
-   **Paketversion**: Der Standardfilter ist **Alle Versionen**, aber Sie können eine bestimmte Paketversion wählen.


## <a name="installs-daily"></a>Tägliche Installationen


Im Diagramm **Tägliche Installationen** sehen Sie die Gesamtanzahl der täglichen Installationen Ihrer App über einen gewählten Zeitraum.

Zur Gesamtübersicht der Installationen gehören:
-   **Installationen auf mehreren Windows 10-Geräten.** Wenn ein Kunde Ihre App beispielsweise aus zwei Windows 10-PCs und einem Windows 10-Smartphone installiert, werden drei Installationen gezählt.
-   **Erneute Installationen.** Wenn eine Kunde Ihre App beispielsweise heute installiert, morgen deinstalliert und im nächsten Monat erneut installiert, werden zwei Installationen gezählt.

Von der Gesamtansicht der Installationen sind ausgenommen:
-   **Installationen auf Nicht-Windows 10-Geräten.** Wenn ein Kunden Ihre App beispielsweise auf einem Gerät installiert, das nicht unter Windows 10 ausgeführt wird, zählt diese Installation nicht.
-   **Deinstallationen.** Wenn ein Kunde Ihre App beispielsweise deinstalliert, wird diese nicht von der Gesamtanzahl der Installationen abgezogen.
-   **Aktualisierungen.** Wenn ein Kunde Ihre App beispielsweise heute installiert und eine Woche später eine App-Aktualisierung installiert, zählt dies nur als eine Installation (nicht zwei).
-   **Vorinstallationen.** Wenn ein Kunde beispielsweise ein Gerät kauft, auf dem Ihre App vorinstalliert wurde, zählt dies nicht als Installation.
-   **Vom System initiierte Installationen.** Wenn Windows beispielsweise aus irgendeinem Grund Ihre App automatisch installiert, zählt dies nicht als Installation.

> **Hinweis**  Aktuell können Sie die Daten aus **Tägliche Installationen** nicht programmgesteuert über eine API abrufen.

## <a name="markets"></a>Märkte


Im Diagramm **Märkte** sehen Sie die Gesamtanzahl der Installationen über einen gewählten Zeitraum pro Markt. Standardmäßig werden die Daten aller Märkte angezeigt. Sie können jedoch nach bestimmten Märkten filtern.


## <a name="package-version"></a>Paketversion


Im Diagramm **Paketversion** sehen Sie die Gesamtanzahl der Installationen über einen gewählten Zeitraum pro Paketversion.



 

 

