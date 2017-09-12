---
author: jnHs
Description: "Performance-Daten für die Anzeigeneinheiten in Ihren Apps können Sie mithilfe der Berichte zur Anzeigen-Performance auf App- und Kontoebene im WindowsDevCenter-Dashboard anzeigen."
title: Bericht zur Anzeigenleistung
ms.assetid: 32E555C3-C34D-4503-82BB-4C3F5CAE4500
ms.author: wdg-dev-content
ms.date: 07/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: c46533c6762ddd2f47a4dbd40c253bc3d8f346d7
ms.sourcegitcommit: 10f8dcf69d37cdb61562fc9f4d268ccb499c368f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2017
---
# <a name="advertising-performance-report"></a>Bericht zur Anzeigenleistung


Der **Bericht zur Anzeigenleistung** zeigt die Leistung Ihrer [Anzeigeneinheiten](monetize-with-ads.md#available-ad-units) an, einschließlich der Community-Anzeigen und Partneranzeige. Dieser Bericht enthält Daten mehrerer Anzeigenanbieter in UWP-Apps, die die [Anzeigenvermittlung](monetize-with-ads.md#mediation) verwenden. 

Erweitern Sie zum Anzeigen dieses Berichts im linken Navigationsmenü **Analysieren** und wählen Sie dann **Anzeigenleistung** aus. 

Um eine genauere Analyse der Daten durchzuführen, bieten wir den Link **Bericht herunterladen**, über den Sie eine CSV-Datei herunterladen können, die Sie in Microsoft Excel oder einem anderen Programm öffnen können. Sie können diese Daten auch programmgesteuert mit der Methode [get ad performance data](../monetize/get-ad-performance-data.md) der [Windows Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

Wenn Sie die Anzeigenvermittlungsberichte ansehen, ist es wichtig zu beachten, dass sich die Berichtsdaten für die letzten drei Tage sich unter Umständen ändern, wenn wir neue Daten aus verschiedenen Quellen erhalten und verarbeiten. Datenanpassungen können außerdem rückwirkend für bis zu 90Tage vorgenommen werden.


## <a name="overall-performance"></a>Gesamtleistung

Oben im Bericht können Sie die folgenden Filter verwenden, um den Umfang der Daten, die im Bericht angezeigten werden, anzupassen:

* **Datum**: Filtern Sie den Bericht für einen festgelegten Zeitraum oder einen benutzerdefinierten Datumsbereich. Standardmäßig werden im Bericht Daten für die letzten 30Tage angezeigt.
* **Aggregation**: Hier können Sie auswählen, wie diese Daten zusammengefasst werden und wie sie weitere gefiltert werden können. Standardmäßig zeigt der Bericht Daten aus allen Anzeigeeinheiten an, und Sie sehen ein Link **Anzeigeneinheiten auswählen** unten im Abschnitt, das Ihnen ermöglicht, bis zu sechs Anzeigeeinheiten zum Vergleich auszuwählen. Sie können optional **Aggregation** auf **Alle Apps** oder **Alle Ad-Anbieter** ändern. Dadurch wird die Verknüpfung in diesem Abschnitt entweder auf **Apps auswählen** oder **Ad-Anbieter auswählen** geändert, sodass Sie aus bis zu sechs Vergleichsdaten auswählen können. Sie können die Ergebnisse auch nach einer bestimmten App gruppieren, in der Sie die Werbung anzeigen.
* **Anzeigenanbieter**: Filtern Sie den Bericht nach Performance-Daten für bestimmte Anzeigenanbieter. Weitere Informationen zu den verfügbaren Anzeigenanbietern finden Sie im Abschnitt [Anzeigenvermittlung](monetize-with-ads.md#mediation) unter [Monetarisierung durch Anzeigen](monetize-with-ads.md). In der Standardeinstellung zeigt der Bericht Daten von allen Ad-Anbietern an. Diese Option wird deaktiviert, wenn Sie **Alle Ad-Anbieter** aus der Dropdownliste **Aggregation** auswählen.
* **Gerät**: Filtern Sie den Bericht nach Leistungsdaten für bestimmte Gerätetypen. In der Standardeinstellung zeigt der Bericht Daten für alle Gerätetypen an.


## <a name="report-views"></a>Berichtanzeigen

Unterhalb der Filter zeigt der Bericht Daten aus einer Vielzahl von Anzeigenleistungsmetriken in Diagramm-, Weltkarten- und Tabellenform für die Anzeigeneinheiten an, die in der aktuellen App verwendet werden.

Klicken Sie auf **Diagramm** oder **Karte**, um die Daten für eine dieser Metriken in einer Diagramm- oder Weltkartenansicht zu analysieren. Standardmäßig werden in den Diagramm- und Kartenansichten Leistungsdaten für alle Anzeigeneinheiten, Apps oder Werbeanbieter in Ihrer App angezeigt (je nach Ihrer Auswahl aus der Dropdownliste **Aggregation**, Sie haben allerdings die Wahl bis zu sechs einzelne Anzeigeneinheiten, Apps oder Werbeanzeiger auszuwählen, die verglichen werden sollen).

In der Kartenansicht stellen dunklere Schattierungen höhere Werte und hellere Schattierungen niedrigere Werte dar. Sie können mit der Maus auf ein bestimmtes Land oder eine Region auf der Karte zeigen, um den Wert der ausgewählten Metrik zu analysieren. Sie können auch einen beliebigen Bereich der Karte vergrößern, um Daten für kleinere Länder anzuzeigen.

Weitere Informationen zu den Leistungsmetriken für die Anzeigeneinheiten in Ihrer App finden Sie in der Tabelle unter der Diagramm- und Kartenansicht.

> [!NOTE]
> Wenn Sie Anzeigeneinheiten für eine App mit Microsoft pubCenter erstellt haben, kann es vorkommen, dass nicht alle erfolgreich Ihren Apps in Dev Center zugeordnet wurden. In diesem Bericht werden diese Anzeigeeinheiten App-Namen zugeordnet, die Sie in pubCenter angegeben haben, wobei die Zeichenfolge **(pubCenter)** an den App-Namen angehängt wird.


## <a name="performance-metrics"></a>Leistungsmetriken

Dieser Bericht kann Daten für die folgenden Leistungsmetriken enthalten. Die Metriken, die im Bericht angezeigt werden, variieren je nach Anzeigenanbieter.

|  Metrik  |  Beschreibung  |
|----------|---------------|
| Geschätzter Umsatz  |  Die geschätzten Einnahmen, die Sie mit den Anzeigen in Ihrer App erzielen. |
| eCPM  |  Die effektiven Kosten pro tausend Anzeigenaufrufen. |
| Anforderungen  | Die Anzahl der von Ihrer App gesendeten Anzeigenanforderungen.  |
| Aufrufe  | Gibt an, wie häufig eine Anzeige in Ihrer App angezeigt wurde.  |
| Füllrate  | Gibt den Prozentsatz der von Ihrer App gesendeten Anzeigenanforderungen an, bei denen eine Anzeige angezeigt wurde.  |
| Klicks  |  Gibt an, wie häufig in Ihrer App auf eine Anzeige geklickt wurde. |
| CTR  |  Gibt an, wie häufig auf eine Anzeige geklickt wurde – geteilt durch die Anzahl von Anzeigenaufrufen. |
| Erworbenes Guthaben  | Bei [Community-Anzeigen](https://docs.microsoft.com/windows/uwp/publish/about-community-ads) gibt dies das Guthaben an, das Sie durch Anzeigen von Community-Anzeigen in Ihrer App für Werbefläche erworben haben.  |
| Beanspruchtes Guthaben  | Bei [Community-Anzeigen](https://docs.microsoft.com/windows/uwp/publish/about-community-ads) gibt dies das für Ihre App beanspruchte Anzeigenguthaben an.  |


## <a name="affiliates-performance"></a>Partneranzeigen-Performance

Wenn Sie beim [Microsoft-Partneranzeigenprogramm registriert sind](about-affiliate-ads.md) können Sie die Leistungsdaten für Partneranzeigen ansehen, die in Ihrer App angezeigt werden. Diese Informationen werden täglich aktualisiert. 


Oben im Bericht können Sie die folgenden Filter verwenden, um den Umfang der Daten, die im Bericht angezeigten werden, anzupassen:
- **Datum**: Filtern Sie den Bericht für einen festgelegten Zeitraum oder einen benutzerdefinierten Datumsbereich. Standardmäßig werden im Bericht Daten für die letzten 30Tage angezeigt.
- **Gerät**: Filtern Sie den Bericht nach Leistungsdaten für bestimmte Gerätetypen. In der Standardeinstellung zeigt der Bericht Daten für alle Gerätetypen an.

Dieser Bericht enthält standardmäßig eine Zusammenfassung in Diagramm- und Tabellenform der Leistungsdaten für Partneranzeigen in allen Apps, die Sie beim Microsoft-Partneranzeigenprogramm registriert haben. Wählen Sie **Apps auswählen** aus, um bis zu sechs Apps zum Vergleichen auszuwählen.

Daten der Partneranzeigen-Performance werden aus den folgenden sieben Leistungsmetriken abgerufen, die für die Partneranzeige in Ihrer App nachverfolgt werden:

-   **Estimated earnings (approved)**: Die geschätzten Einnahmen, die Sie als Kommission für genehmigte Einkäufe von Benutzern erhalten haben, die in Ihrer App auf Partneranzeigen klicken.
-   **Estimated earnings (pending approval)**: Der ungefähre Betrag, den Sie als Kommission für die Einkäufe, für die eine Genehmigung noch aussteht, erhalten können.
-   **Aufrufe**: Gibt an, wie häufig eine Partneranzeige in Ihrer App angezeigt wurde.
-   **Klicks**: Gibt an, wie oft in Ihrer App auf eine Partneranzeige geklickt wurde.
-   **CTR** (Click-Through-Rate): Gibt an, wie oft auf eine Partneranzeige geklickt wurde (geteilt durch die Anzahl von Partneranzeigenaufrufen).
-   **Purchases (approved)**: Die Anzahl genehmigter Einkäufe von Benutzern, die in Ihrer App auf Partneranzeigen klicken.
-   **Purchases (pending approval)**: Die Anzahl von Einkäufen mit ausstehender Genehmigung, die von Benutzern getätigt wurden, die in Ihrer App auf Partneranzeigen klicken.

> [!NOTE]
> Nachdem ein Benutzer ein Produkt im Store gekauft hat, gibt es eine Wartezeit von 45 Tagen, ehe der Kauf für das Partneranzeigenprogramm genehmigt werden kann. Aufgrund dieser Wartezeit können sich die Daten für **Estimated earnings (approved)**, **Estimated earnings (pending approval)**, **Purchases (approved)** und **Purchases (pending approval)** für einen bestimmten Tag ändern, nachdem die Einkäufe genehmigt oder abgelehnt wurden.


 
