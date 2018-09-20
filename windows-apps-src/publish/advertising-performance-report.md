---
author: jnHs
Description: To view performance data for the ad units in your apps, use the advertising performance report on the Windows Dev Center dashboard.
title: Bericht zur Anzeigenleistung
ms.assetid: 32E555C3-C34D-4503-82BB-4C3F5CAE4500
ms.author: wdg-dev-content
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a1a82c91aeafa253427d8e526b38b8ac304591a2
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4087435"
---
# <a name="advertising-performance-report"></a>Bericht zur Anzeigenleistung


Der **Bericht zur Anzeigenleistung** zeigt die Leistung Ihrer [Anzeigeneinheiten](in-app-ads.md) an, einschließlich der Community-Anzeigen. Dieser Bericht enthält Daten mehrerer Anzeigenanbieter in UWP-Apps, die die [Anzeigenvermittlung](in-app-ads.md#mediation) verwenden.

Erweitern Sie zum Anzeigen dieses Berichts im linken Navigationsmenü **Analysieren** und wählen Sie dann **Anzeigenleistung** aus. Sie können diese Daten in Ihrem Dashboard anzeigen, oder Sie können die Berichtsdaten offline anzeigen, indem Sie auf die Pfeilsymbole auf der Seite klicken. Sie können diese Daten alternativ auch programmgesteuert mit der Methode [Abrufen von Anzeigenleistungsdaten](../monetize/get-ad-performance-data.md) unserer [Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

Wenn Sie die Anzeigenvermittlungsberichte ansehen, ist es wichtig zu beachten, dass sich die Berichtsdaten für die letzten drei Tage sich unter Umständen ändern, wenn wir neue Daten aus verschiedenen Quellen erhalten und verarbeiten. Datenanpassungen können außerdem rückwirkend für bis zu 90Tage vorgenommen werden.

## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Daten angezeigt werden sollen. Die Standardeinstellung ist 30D (30Tage), aber Sie können Daten für 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.

Sie können ebenfalls **Filter** erweitern, um alle Daten auf dieser Seite nach Anzeigeneinheit, App, Anzeigenanbieter und Gerätetyp zu filtern. Folgende Optionen stehen zur Auswahl:

* **Aggregation**: Wählen Sie aus, wie diese Daten zusammengefasst werden und wie sie weitere gefiltert werden können. Standardmäßig ist dieser Filter auf **allen Anzeigeeinheiten** festgelegt. Sie können optional dieses Filter auf **alle Apps** oder **alle Anzeigenanbieter** festlegen, oder Sie können das Aggregieren nach einer bestimmten App auswählen, in der Sie Werbung verwenden.
* **Anzeigenanbieter**: Filtern Sie den Bericht nach Performance-Daten für bestimmte [Anzeigenanbieter](in-app-ads.md#paid-networks). In der Standardeinstellung zeigt der Bericht Daten von allen Ad-Anbietern an. Diese Option wird deaktiviert, wenn Sie **Alle Ad-Anbieter** aus der Dropdownliste **Aggregation** auswählen.
* **Gerät**: Filtern Sie den Bericht nach Leistungsdaten für bestimmte Gerätetypen. In der Standardeinstellung zeigt der Bericht Daten für alle Gerätetypen an.

## <a name="overall-performance"></a>Gesamtleistung

In diesem Abschnitt werden Anzeigenleistungsmetriken in n einer Diagramm- oder Weltkartenansicht für Anzeigeeinheiten, Apps und Anzeigenanbieter angezeigt, die Sie im Berichtsfilter ausgewählt haben.

Um zu einer anderen Ansicht der Daten zu wechseln, klicken Sie auf **Diagramm** oder **Karte** am oberen Rand des Abschnitts **Gesamtleistung**. In der Kartenansicht stellen dunklere Schattierungen höhere Werte und hellere Schattierungen niedrigere Werte dar. Sie können mit der Maus auf ein bestimmtes Land oder eine Region auf der Karte zeigen, um den Wert der ausgewählten Metrik zu analysieren. Sie können auch einen beliebigen Bereich der Karte vergrößern, um Daten für kleinere Länder anzuzeigen.

Die im Diagramm oder in der Karte angezeigten Daten können durch Klicken auf das Filtersymbol neben der Dropdownliste **Diagramm** oder **Karte** optimiert werden. Mit diesem Filter können Sie bis zu sechs verschiedene Anzeigeeinheiten, Apps oder Anzeigenanbieter in der Ansicht Diagramm oder Karte vergleichen. Der ausgewählte Datentyp in diesem Filter hängt von Ihrer für Auswahl des Filters **Aggregation** Filter am oberen Rand des Berichts der obersten Ebene ab.


## <a name="overall-performance-breakdown"></a>Gesamtleistungsübersicht

Dieser Abschnitt zeigt eine Tabelle mit allen Anzeigeneistungsmetriken für die angegebenen Daten mithilfe der Filter, die Sie im Bericht ausgewählt haben, an.

## <a name="performance-metrics"></a>Leistungsmetriken

Der Bericht **Anzeigenleistung** enthält Daten für die folgenden Leistungsmetriken. Einige Metriken werden nur für bestimmte Anzeigenanbieter angezeigt.

|  Metrik  |  Beschreibung  |
|----------|---------------|
| Geschätzter Umsatz  |  Die geschätzten Einnahmen, die Sie mit den Anzeigen in Ihrer App erzielen. |
| eCPM  |  Die effektiven Kosten pro tausend Anzeigenaufrufen. |
| Anforderungen  | Die Anzahl der von Ihrer App gesendeten Anzeigenanforderungen.  |
| Aufrufe  | Gibt an, wie häufig eine Anzeige in Ihrer App angezeigt wurde.  |
| Füllrate  | Gibt den Prozentsatz der von Ihrer App gesendeten Anzeigenanforderungen an, bei denen eine Anzeige angezeigt wurde.  |
| Klicks  |  Gibt an, wie häufig in Ihrer App auf eine Anzeige geklickt wurde. |
| CTR  |  Gibt an, wie häufig auf eine Anzeige geklickt wurde – geteilt durch die Anzahl von Anzeigenaufrufen. |
| Die Sichtbarkeit | Der Prozentsatz der anzeigenaufrufe, die in Ihrer app angezeigt werden. Weitere Informationen zu diesen Wert wie berechnet wird finden Sie unter [Optimieren der Sichtbarkeit von anzeigeneinheiten](../monetize/optimize-ad-unit-viewability.md). |
| Erworbenes Guthaben  | Bei [Community](https://docs.microsoft.com/windows/uwp/publish/about-community-ads)-Kampagnen gibt dies das Guthaben an, das Sie durch Anzeigen von Community-Anzeigen in Ihrer App für Werbefläche erworben haben.  |
| Beanspruchtes Guthaben  | Bei [Community](https://docs.microsoft.com/windows/uwp/publish/about-community-ads)-Kampagnen gibt dies das für Ihre App beanspruchte Anzeigenguthaben an.  |

## <a name="related-topics"></a>Verwandte Themen

* [In-App-Anzeigen](in-app-ads.md)
* [Zeigt Werbung mithilfe der Microsoft Advertising-SDK in Ihrer App an](../monetize/display-ads-in-your-app.md)
* [Optimieren der Sichtbarkeit von Anzeigeneinheiten](../monetize/optimize-ad-unit-viewability.md)


 
