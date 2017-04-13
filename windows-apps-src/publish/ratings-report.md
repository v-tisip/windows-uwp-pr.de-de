---
author: jnHs
Description: "Dem Bericht „Bewertungen“ im Windows Dev Center-Dashboard können Sie entnehmen, wie Kunden Ihre App im Windows Store bewerten."
title: "Bericht „Bewertungen“"
ms.assetid: CAFEC20B-04FB-48C8-B663-1238C0B85ECD
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: fa9d9fcb7f82a5dbe75e3b7249b32226552422ad
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="ratings-report"></a>Bericht „Bewertungen“


Dem Bericht **Bewertungen** im Windows Dev Center-Dashboard können Sie entnehmen, wie Kunden Ihre App im Windows Store bewerten. Sie können diese Informationen in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um Ihre Daten offline anzuzeigen. Sie können diese Daten auch programmgesteuert mit der Methode [Abrufen von App-Bewertungen](../monetize/get-app-ratings.md) der [Windows Store-REST-API für Analysen](../monetize/access-analytics-data-using-windows-store-services.md) abrufen.

Eine Bewertung wird in diesem Bericht anhand der Anzahl von Sternen (von 1 bis 5) ausgedrückt, die ein Kunde Ihrer App bei der Bewertung im Store gegeben hat. Der Bericht **Bewertungen** enthält keine individuellen Kommentare, die als Rezensionen abgegeben wurden. Diese sind im [Bericht „Rezensionen“](reviews-report.md) enthalten.

## <a name="apply-filters"></a>Anwenden von Filtern


Im oberen Seitenbereich können Sie **Filter anwenden** erweitern, um alle Daten auf dieser Seite nach Datumsbereich und/oder Markt zu filtern.

-   **Datum**: Der Standardfilter lautet **Letzte 30 Tage**, aber er kann bis auf **Letzte 12 Monate** erweitert werden.
-   **Markt**: Der Standardfilter ist **Alle Märkte**. Sie können einen bestimmten Markt auswählen, wenn auf dieser Seite nur Bewertungen der in diesem Markt ansässigen Kunden angezeigt werden sollen.
-   **Gerätetyp**: Der Standardfilter ist **Alle Geräte**. Sie können einen bestimmten Gerätetyp auswählen, wenn auf dieser Seite nur Bewertungen von Kunden angezeigt werden sollen, die ein Gerät dieses Typs verwenden.

Die Informationen in allen unten aufgeführten Diagrammen beziehen sich auf den im Bereich **Filter anwenden** ausgewählten Zeitraum und entsprechen den von Ihnen hier ausgewählten Filtern.

## <a name="average-rating"></a>Durchschnittliche Bewertung


Das Diagramm **Durchschnittliche Bewertung** gibt Aufschluss über die durchschnittliche Bewertung Ihrer App im ausgewählten Zeitraum.

## <a name="number-of-ratings"></a>Anzahl der Bewertungen


Das Diagramm **Anzahl der Bewertungen** zeigt die Gesamtanzahl der App-Bewertungen im ausgewählten Zeitraum.

## <a name="new-and-revised-ratings"></a>Neue und überarbeitete Bewertungen


Das Diagramm **Neue und überarbeitete Bewertungen** enthält die Anzahl der Bewertungen für jeden Bewertungstyp (neu oder überarbeitet) im ausgewählten Zeitraum.

-   **Neue Bewertungen** sind Bewertungen, die Kunden abgegeben, aber nicht geändert haben.
-   **Überarbeitete Bewertungen** sind Bewertungen, die vom Kunden geändert wurden.

>**Hinweis**  Eine Bewertung wird hier selbst dann als überarbeitet angezeigt, wenn der Kunde nur den Text oder Titel seiner Rezension geändert oder hinzugefügt hat, die tatsächliche Bewertung aber unverändert ist.

## <a name="average-rating-over-time"></a>Durchschnittliche Bewertung im Laufe der Zeit


Das Diagramm **Durchschnittliche Bewertung im Laufe der Zeit** zeigt, wie sich die durchschnittliche App-Bewertung im ausgewählten Zeitraum geändert hat.

Anstatt den Durchschnitt aller Bewertungen zu berechnen, die im ausgewählten Zeitraum verbleiben (wie im Diagramm **Durchschnittliche Bewertung**), zeigt das Diagramm **Durchschnittliche Bewertung im Laufe der Zeit**, wie Kunden die App an einem bestimmten Tag oder in einer bestimmten Woche im genannten Zeitraum bewertet haben. Das hilft Ihnen bei der Ermittlung von Trends oder bei der Bestimmung, ob Bewertungen von Updates oder anderen Faktoren betroffen sind.

Wenn Sie die Informationen nach **Letzte 30 Tage** oder **Letzte 3 Monate** gefiltert haben, zeigt das Diagramm die durchschnittliche Bewertung nach Tagen an. Wenn Sie nach **Letzte 6 Monate** oder **Letzte 12 Monate** gefiltert haben, zeigt das Diagramm die durchschnittliche Bewertung nach Wochen an (dabei wird davon ausgegangen, dass eine neue Woche am Montag beginnt; die angezeigte durchschnittliche Bewertung bezieht sich auf die vorherige Woche).

## <a name="markets"></a>Märkte


Das Diagramm **Märkte** zeigt die durchschnittliche Bewertung und die Anzahl der Bewertungen im ausgewählten Zeitraum nach Markt.

> **Hinweis**  Wenn Sie mithilfe der **Seitenfilter** einen bestimmten Markt angegeben haben, wird dieses Diagramm im Bericht **Bewertungen** nicht angezeigt. Um dieses Diagramm anzuzeigen, ändern Sie die **Seitenfilter** so, dass alle Märkte angezeigt werden.

Standardmäßig wird der Markt mit den meisten Rezensionen zuerst angezeigt, gefolgt von weiteren Märkten in absteigender Reihenfolge. Sie können die Reihenfolge mithilfe des Pfeils in der Diagrammspalte **Anzahl der Bewertungen** aber auch umkehren. Sie können die Daten auch nach **Durchschnittliche Bewertung** oder **Markt** sortieren, indem Sie auf diese Spalten klicken.

> **Hinweis**  Wenn Sie den Bericht **Rezensionen** im Windows Dev Center mit dem Bericht „Rezensionen“ in der älteren mobilen Dev Center-App vergleichen, werden Sie wahrscheinlich eine unterschiedliche Anzahl von Bewertungen finden. Dies liegt daran, dass die App nur Daten für Rezensionen von Kunden unter Windows Phone 8.1 und früheren Versionen anzeigt. Eine weitere Möglichkeit besteht darin, dass Rezensionen mit Spam, unangemessenen oder beleidigenden Inhalten oder Rezensionen, die auf andere Weise Richtlinien verletzen, von Microsoft aus dem Windows Store entfernt wurden. Diese Verfahrensweise soll die Benutzerfreundlichkeit für unsere Kunden erhöhen.

 

 
