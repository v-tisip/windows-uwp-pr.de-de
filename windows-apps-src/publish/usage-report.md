---
author: jnHs
Description: The Usage report in the Windows Dev Center dashboard lets you see how customers are using your app.
title: Nutzungsbericht
ms.assetid: 5F0E7F94-D121-4AD3-A6E5-9C0DEC437BD3
ms.author: wdg-dev-content
ms.date: 06/01/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, Verwendung, benutzerdefiniertes Ereignis, Bericht, Telemetrie, Benutzersitzungen
ms.localizationpriority: medium
ms.openlocfilehash: 96d36ebbaa2b7f1a650e2b0f794a1976c1f525a6
ms.sourcegitcommit: 310a4555fedd4246188a98b31f6c094abb33ec60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5133669"
---
# <a name="usage-report"></a>Nutzungsbericht


Im Bericht **Nutzung** im Windows Dev Center-Dashboard erfahren Sie, wie Kunden mit Windows10 (inklusive Xbox) Ihre App verwenden, und erhalten Informationen zu den von Ihnen definierten benutzerdefinierten Ereignissen. Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen.


## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist **30D** (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.

Sie können ebenfalls **Filter** erweitern, um Daten auf dieser Seite nach Paketversion, Markt und/oder Gerätetyp zu filtern.

-   **Paketversion**: Die Standardeinstellung ist **Alle**. Wenn Ihre App mehr als ein Paket enthält, können Sie hier ein bestimmtes Paket auswählen.
-   **Markt**: der Standardfilter lautet **Alle Märkte**, aber Sie können die Daten auf einen oder mehrere Märkte begrenzen.
-   **Gerätetyp**: Die Standardeinstellung ist **Alle**, Sie können jedoch festlegen, dass nur Daten für einen bestimmten Gerätetyp (PC, Konsole, Tablet etc.) angezeigt werden.

Die Informationen in allen unten angezeigten Diagrammen spiegelt den Zeitraum und die ausgewählten Filter wider (mit Ausnahme von **Neue Benutzer** im Diagramm **Nutzung**, das nicht angezeigt wird, wenn keine Filter ausgewählt sind). In einigen Abschnitten können Sie zusätzliche Filter anwenden.

> [!IMPORTANT]
> Dieser Bericht enthält nur Nutzungsdaten von Kunden unter Windows10 (inklusive Xbox), die die Bereitstellung von Telemetriedaten nicht deaktiviert haben. Die Nutzungsdaten für Xbox-Spiele werden unabhängig von der Anmeldung des Kunden bei Xbox Live angezeigt. 


## <a name="usage"></a>Nutzung

Das Diagramm **Nutzung** zeigt im Detail, wie Kunden Ihre App über den ausgewählten Zeitraum verwenden. In diesem Diagramm werden individuelle Benutzer Ihrer App oder Benutzersitzungen nicht einzeln nachverfolgt (d.h., ein Benutzer wird in diesem Diagramm unabhängig davon dargestellt, ob er Ihre App nur einmal oder mehrmals verwendet hat).

Dieses Diagramm enthält vier separate Registerkarten, die die Nutzung pro Tag oder Woche anzeigen (abhängig von der Dauer, die Sie ausgewählt haben).

- **Benutzer**: Zeigt die Gesamtanzahl der **Benutzersitzungen** über den ausgewählten Zeitraum an. Jede Benutzersitzung stellt einen unterschiedlichen Zeitraum dar und beginnt, wenn die App gestartet wird (Prozessbeginn) und endet bei Prozessende oder nach einer bestimmten Zeit der Inaktivität. Aus diesem Grund kann ein einzelner Kunde mehrere Benutzersitzungen am gleichen Tag oder in der gleichen Woche haben. Die Gesamtanzahl der **aktiven Benutzer** (alle Kunden, die die App an diesem Tag oder in dieser Woche nutzen) und **neuen Benutzer** (ein Kunde, der Ihre App das erste Mal an diesem Tag oder in der Woche nutzt) wird ebenfalls angezeigt. Wenn Sie Filter auf der Seite angewendet haben, werden **neue Benutzer** in diesem Diagramm nicht angezeigt.
- **Geräte**: Zeigt die Anzahl der täglichen Geräte an, die von allen Benutzern zur Interaktion mit Ihrer App verwendet werden.
- **Dauer**: Zeigt die Gesamtanzahl der aktiven Stunden an (Stunden, in denen ein Benutzer aktiv Ihrer App verwendet).
- **Beibehaltung**: Zeigt die Gesamtanzahl der **DAU/MAU** (tägliche aktive Benutzer/monatliche aktive Benutzer) über den ausgewählten Zeitraum an.

Wenn **30d** Zeitraum aktiviert ist, sehen Sie Kreis Marker, wenn der **Benutzer**oder **Geräte**, **Dauer** Registerkarten angezeigt. Diese darstellen eine erhebliche Erhöhung oder in einem bestimmten Wert, den wir glauben, dass Sie kennen sollten verringern. Das Datum, an dem die Kreis angezeigt wird, steht das Ende der Woche, in der wir eine erhebliche Erhöhung oder Verringerung im Vergleich zur vorherigen Woche davor erkannt. Um weitere Informationen zu Änderungen zu sehen, zeigen Sie auf den Kreis.  

> [!TIP]
> Sie können weitere Einblicke im Zusammenhang mit erhebliche Änderungen an der letzten 30 Tage im [Bericht](insights-report.md)anzeigen.


## <a name="user-sessions"></a>Benutzersitzungen

Das Diagramm **Benutzersitzungen** zeigt die Gesamtzahl der Benutzersitzungen pro Markt für die App über den ausgewählten Zeitraum an.

Genau wie in den Infos für die **Benutzersitzungen** stellen die Infos im Diagramm **Nutzung** eine Sitzung des Benutzers für einen bestimmten Zeitraum dar, wenn der Kunde mit der App interagiert. Dieses Diagramm verfolgt keine individuellen Benutzer Ihrer App.

Sie können diese Daten in einer visuellen **Karte** anzeigen, oder die Einstellung auf eine Anzeige in Form einer **Tabelle** festlegen. Die Tabellenform zeigt jeweils fünf Märkten an, die alphabetisch oder nach der höchsten/niedrigst möglichen Anzahl von Anwendersitzungen sortiert sind. Sie können auch die Daten zum Anzeigen von Informationen für alle Märkte zusammen herunterladen.


## <a name="package-version"></a>Paketversion

Das Diagramm **Benutzersitzungen** zeigt die Gesamtzahl täglicher Benutzersitzungen pro Paketversion für die App über den ausgewählten Zeitraum an.

Genau wie im Diagramm **Benutzersitzungen** stellen die Infos eine Sitzung des Benutzers für einen bestimmten Zeitraum dar, wenn der Kunde mit der App interagiert. Dieses Diagramm verfolgt keine individuellen Benutzer Ihrer App.


## <a name="custom-events"></a>Benutzerdefinierte Ereignisse

Das Diagramm **Benutzerdefinierte Ereignisse** zeigt, wie häufig die für Ihre App definierten benutzerdefinierten Ereignisse insgesamt aufgetreten sind. Dazu können mehrere Vorkommen für denselben Kunden gehören. Mithilfe der Filter können Sie die benutzerdefinierten Ereignisse auswählen, für die Daten angezeigt werden sollen.

Benutzerdefinierte Ereignisse werden unter Verwendung der [StoreServicesCustomEventLogger.Log](https://docs.microsoft.com/en-us/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Methode im [Microsoft Store Services SDK](../monetize/microsoft-store-services-sdk.md) implementiert.

Weitere Informationen finden Sie unter [Protokollieren benutzerdefinierter Ereignisse für Dev Center](../monetize/log-custom-events-for-dev-center.md).


## <a name="custom-events-breakdown"></a>Übersicht über benutzerdefinierte Ereignisse

Das Diagramm **Übersicht über benutzerdefinierte Ereignisse** enthält weitere Details, wie oft jedes Ihre benutzerdefinierten Ereignisse aufgetreten ist. Dadurch können Sie ermitteln, ob Ereignisse für einen bestimmten Markt, Gerätetyp oder eine Paketversionen häufiger auftreten.

Für jedes Ereignis wird der Name des Ereignisses und ein Ereignisanzahl angezeigt, die einer bestimmte Kombination von Markt, Gerätetyp und Paketversion des Benutzers entsprechen. In der Regel wird ein Ereignis mehrmals angezeigt, zusammen mit verschiedenen Kombinationen dieser Faktoren. 




 
