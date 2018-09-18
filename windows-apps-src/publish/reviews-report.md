---
author: jnHs
Description: The Reviews report in the Windows Dev Center dashboard lets you see the reviews (comments) that customers entered when rating your app in the Store.
title: Bericht „Rezensionen“
ms.assetid: E50C3A4D-1D8A-4E5B-8182-3FAD049F2A2D
ms.author: wdg-dev-content
ms.date: 08/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Überprüfung, Kommentar, Prüfer
ms.localizationpriority: medium
ms.openlocfilehash: 4500ebe7406db45a089f3ceba10c1d1e781ea679
ms.sourcegitcommit: f5321b525034e2b3af202709e9b942ad5557e193
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "4022368"
---
# <a name="reviews-report"></a>Bericht „Rezensionen“


Der Bericht **"Rezensionen"** im Windows Dev Center-Dashboard gibt Aufschluss über die Rezensionen (Kommentare), die Kunden beim Bewerten eingegeben haben Ihre app im Store.

Sie können diese Daten in Ihrem Dashboard anzeigen oder den [Bericht herunterladen](download-analytic-reports.md), um ihn offline anzuzeigen. Alternativ können Sie diese Daten programmgesteuert abrufen, mit der [app-Rezensionen get](../monetize/get-app-reviews.md) -Methode in der [Microsoft Store-Analyse-REST-API](../monetize/access-analytics-data-using-windows-store-services.md).

Sie können auch auf Kunden Rezensionen [direkt von dieser Seite](respond-to-customer-reviews.md), programmgesteuert [über die Microsoft Store-Rezensionen-API](../monetize/submit-responses-to-app-reviews.md), oder mithilfe der [Dev Center-app](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws)reagieren.

> [!TIP]
> Um Rezensionen, Bewertungen und Benutzerfeedback für alle Ihre Apps in den letzten 30Tagen anzusehen, erweitern Sie **Einbeziehen** im linken Navigationsmenü und wählen Sie **Kritiken und Feedback** aus. 


## <a name="apply-filters"></a>Anwenden von Filtern

Im oberen Bereich der Seite können Sie den Zeitraum auswählen, für den die Rezensionen angezeigt werden sollen. Die Standardeinstellung ist **Lebensdauer**, aber Sie können Rezensionen für 30 Tage, 3, 6 oder 12Monate anzeigen, oder für einen benutzerdefinierten Zeitraum, den Sie angeben.

Sie können **Filter** erweitern, um alle angezeigten Rezensionen auf dieser Seite mit den folgenden Optionen zu filtern. Diese Filter werden nicht auf die Diagramme **Rezensionsübersicht** und **Durchschnittliche Bewertung im Laufe der Zeit** angewandt.

-   **Bewertung**: Standardmäßig ist die Rezension „Alle Sterne“ aktiviert, Sie können jedoch einzelne Bewertungen (von 1 bis 5 Sternen) aktivieren bzw. deaktivieren, wenn Sie nur Rezensionen mit einer bestimmten Sternebewertung anzeigen möchten.
- **Rezensionsinhalt**: die Standardeinstellung ist **Bewertungen mit rezensionsinhalt**, was bedeutet, dass nur Bewertungen mit Rezension Inhalt angezeigt werden sollen. Sie können auswählen, **Alle** für die Anzeige aller Bewertungen, auch derjenigen, die keinen Text schriftliche Rezension enthalten. Beachten Sie, dass das Diagramm **eine Übersicht über** alle Rezensionen, unabhängig von der Auswahl immer angezeigt wird.
-   **Betriebssystemversion**: Die Standardeinstellung ist **Alle**. Sie können eine bestimmte Betriebssystemversion auswählen, wenn auf dieser Seite nur Rezensionen von Kunden angezeigt werden sollen, die diese Betriebssystemversion verwenden.
-   **Paketversion**: Die Standardeinstellung ist **Alle**. Wenn Ihre App mehr als ein Paket enthält, können Sie hier ein spezifisches Paket auswählen, um nur Rezensionen von Kunden anzuzeigen, die für die Rezension der App dieses Paket verwendet haben.
-   **Antworten**: Die Standardeinstellung ist **Alle**. Sie können die Rezensionen so filtern, dass nur die Kundenrezensionen angezeigt werden, auf die Sie [geantwortet](respond-to-customer-reviews.md) haben, oder nur die, auf die Sie noch nicht geantwortet haben.
-   **Updates**: Die Standardeinstellung ist **Alle**. Sie können die Rezensionen so filtern, dass nur diejenigen angezeigt werden, die vom Kunden aktualisiert wurden, nachdem Sie auf eine [Rezension geantwortet haben](respond-to-customer-reviews.md), oder nur die, die noch nicht vom Kunden aktualisiert wurden.
-   **Markt**: Die Standardeinstellung ist **Alle Märkte**. Sie können einen bestimmten Markt auswählen, wenn auf dieser Seite nur Rezensionen der in diesem Markt ansässigen Kunden angezeigt werden sollen.
-   **Gerätetyp**: Der Standardfilter ist **Alle Geräte**. Sie können einen bestimmten Gerätetyp auswählen, wenn auf dieser Seite nur Rezensionen von Kunden angezeigt werden sollen, die ein Gerät dieses Typs verwenden.
-   **Kategoriename**: Der Standardfilter ist **Immer**. Sie können eine bestimmte [Insight Kategorie](#review-insight-categories) auswählen, um nur Rezensionen anzuzeigen, die wir dieser Kategorie zugeordnet haben. 

> [!TIP]
> Wenn auf der Seite keine Rezensionen zu sehen sind, stellen Sie sicher, dass Sie mit Ihrer Filterauswahl nicht alle Rezensionen ausgeschlossen haben. Wenn Sie z.B. nach einem Zielbetriebssystem filtern, das von Ihrer App nicht unterstützt wird, werden keine Rezensionen angezeigt.


## <a name="ratings-breakdown"></a>Rezensionsübersicht

Das Diagramm **eine Übersicht über** wird am oberen Rand dieser Bericht angezeigt, sodass Sie einen kurzen Überblick über die folgenden erhalten können: 
- Den durchschnittlichen Bewertungsstern der Rezensionsübersicht für die App.
- Die Gesamtanzahl der Bewertungen Ihrer App in den letzten 12Monaten.
- Die Gesamtanzahl der Bewertungen für jede Bewertung von Sternen.
- Die Anzahl der Bewertungen für jeden Bewertungstyp (neu oder überarbeitet) pro Sterne-Bewertung in den letzten 12Monaten.
 - **Neue Bewertungen** sind Bewertungen, die Kunden abgegeben, aber nicht geändert haben.
 - **Überarbeitete Bewertungen** Bewertungen, die vom Kunden in keinster Weise geändert wurden, auch wenn es sich nur um Textänderungen handelt.

> [!TIP]
> Bei der durchschnittlichen Bewertung, die einem Kunden im Store angezeigt wird, werden der Markt und der Gerätetyp des Kunden berücksichtigt. Daher können die Inhalte in diesem Bericht davon abweichen.

Beachten Sie, dass dieses Diagramm immer alle Rezensionen enthält, auch wenn Sie in den Seitenfilter **Rezensionsinhalt** **Bewertungen mit Inhalt überprüfen** ausgewählt.

In diesem Diagramm kann auch im [Bericht "Bewertungen"](ratings-report.md)sowie weitere Informationen zu app Bewertungen angezeigt werden.


<span id = "review-insight-categories" />

## <a name="insight-categories"></a>Kategorien der rezensionsstatistik

Die **Kategorien der Rezensionsstatistik** Diagrammgruppen möglicherweise Rezensionen nach Kategorien zu gruppieren, für die wir haben den Rezension zugeordnet.

> [!NOTE]
> Rezensionen, die weniger als 24 Stunden alt sind bzw. in einer anderen Sprache als Englisch angegeben wurden, sind nicht darin enthalten, wenn Berichte nach Kategorien anzeigt werden.

Im oberen Bereich der Seite sehen Sie farbige Blöcke, die Berichte nach Kategorie darstellen. Wählen Sie eine der Kategorien aus, um nur Rezensionen anzeigen, die wir dieser Kategorie zugeordnet haben. Sie können auch die [Seite „Filter”](#apply-filters) nach Kategorie filtern.

Um eine Übersicht über die Anzahl der Rezensionen pro Kategorie anzuzeigen, wählen Sie **Details anzeigen**. 


## <a name="reviews"></a>Rezensionen

Jede Kundenrezension enthält Folgendes:

-   Den vom Kunden eingegebenen Titel und Rezensionstext. (Von Kunden unter Windows Phone 8.1 und früher verfasste Rezensionen haben keinen Titel.)
-   Das Datum der Rezension.
-   Der Name des Verfassers, wie wird im Microsoft Store angezeigt.
-   Das Land/die Region des Verfassers.
-   Die Paketversion der App, die auf dem Kundengerät installiert war, als die Rezension geschrieben wurde. (Für Rezensionen, die online abgegebenen oder von Kunden mit Windows 8.1 oder einem früheren Betriebssystem geschrieben wurden, ist diese Information nicht verfügbar.)
-   Die Betriebssystemversion des Geräts, das der Kunde beim Hinterlassen der Rezension verwendet hat.
-   Der Name des Geräts, das der Kunde beim Hinterlassen der Rezension verwendet hat. (Für Rezensionen, die online abgegebenen oder von Kunden mit Windows 8.1 oder einem früheren Betriebssystem geschrieben wurden, ist diese Information nicht verfügbar.)
-   Die von anderen Kunden, die die Rezension gelesen haben, abgegebene Bewertung für die Brauchbarkeit der Rezension. Sie wird in Form von zwei Zahlengruppen angezeigt: die erste Gruppe gibt an, wie viele Kunden die Rezension als hilfreich bewertet haben, und die zweite entspricht der Gesamtanzahl der Kunden, die die Rezension bewertet haben. 4/10 bedeutet z.B., dass vier von zehn Bewertern die Rezension hilfreich fanden und sechs nicht. (Wenn eine Rezension nicht bewertet wurde, ist auch kein Wert zur Brauchbarkeit angegeben.)

Beachten Sie, dass Kunden eine Bewertung für Ihre App abgeben können, ohne einen Kommentar zu schreiben. Daher sehen Sie normalerweise weniger Rezensionen als Bewertungen.

Sie können die Rezensionen auf der Seite nach Datum und/oder Bewertung in aufsteigender oder absteigender Reihenfolge sortieren. Klicken Sie auf den Link **Sortieren nach** , um Optionen zum Sortieren nach **Datum** und/oder **Bewertung**anzuzeigen.

Im Suchfeld können auch um nach bestimmten Wörtern oder Sätzen in Rezensionen zu Ihrer app zu suchen. Beachten Sie, dass nur der ursprüngliche Rezension Text geschrieben vom Kunden gesucht wird, auch wenn die Überprüfung in einer anderen Sprache geschrieben wurde. Übersetzte Rezension Text wird nicht durchsucht.

> [!NOTE]
> Es kann vorkommen, dass Rezensionen in diesem Bericht nicht mehr angezeigt werden. Dies kann passieren, da Microsoft Rezensionen aus dem Store entfernt, die von Kunden mit bestimmten Vorabversionen und Insider-Builds von Windows10 geschrieben werden. Wir tun dies, um die Möglichkeit einer negativen Rezension zu verringern, die durch ein Problem in einer Vorabversion des Windows-Builds verursacht wird. Unter Umständen entfernen wir auch Rezensionen aus dem Store, die als Spam erkannt wurden, unangemessene oder anstößige Inhalte enthalten oder anderweitig gegen die Richtlinien verstoßen. Diese Verfahrensweise soll die Benutzerfreundlichkeit für unsere Kunden erhöhen.


## <a name="translating-reviews"></a>Übersetzen von Rezensionen

Rezensionen, die nicht in Ihrer bevorzugten Sprache verfasst wurden, werden standardmäßig für Sie übersetzt. Falls gewünscht, können Sie die Übersetzung von Rezensionen deaktivieren, indem Sie das Kontrollkästchen **Rezensionen übersetzen** oben rechts über der Liste der Rezensionen deaktivieren.

Da die Rezensionen durch ein automatisches Übersetzungssystem übersetzt werden, sind die resultierenden Übersetzungen u.U. nicht immer exakt. Für den Fall, dass sie ihn mit der Übersetzung vergleichen oder auf andere Weise übersetzen lassen möchten, steht der Originaltext zur Verfügung.

Wie bereits erwähnt, beim Durchsuchen von Rezensionen nur auf der ursprüngliche links vom Kunden Text wird durchsucht (und keine übersetzten Text), auch wenn Sie die Option **"Rezensionen" übersetzen** aktiviert zu lassen.


## <a name="responding-to-customer-reviews"></a>Reagieren auf Kundenrezensionen

Sie können Microsoft Store Dev Center-Dashboard, die [Microsoft Store-Rezensionen-API](../monetize/submit-responses-to-app-reviews.md)oder die [Dev Center-app](https://www.microsoft.com/store/apps/dev-center/9nblggh4r5ws) verwenden, um Antworten auf zahlreiche kundenrezensionen zu senden. Weitere Informationen finden Sie unter [Reagieren auf Kundenrezensionen](respond-to-customer-reviews.md).

Im Folgenden finden Sie einige zusätzliche Aktionen, die Sie basierend auf den angezeigten Bewertungen und Rezensionen in Erwägung ziehen sollten.

-   Erhalten Sie zahlreiche Rezensionen, die eine neue oder geänderte Funktion vorschlagen oder ein Problem reklamieren, sollten Sie erwägen, eine neue Version zu veröffentlichen, in der die im Feedback angesprochenen Probleme behoben sind. (Achten Sie darauf, die [Beschreibung](create-app-descriptions.md) Ihrer App zu aktualisieren, um anzugeben, dass das Problem behoben wurde.)
-   Wenn die durchschnittliche Bewertung zwar hoch ist, die Anzahl der Downloads jedoch gering ausfällt, sollten Sie nach weiteren Methoden suchen, den [Bekanntheitsgrad Ihrer App zu steigern](attract-customers-and-promote-your-apps.md), da sie bei Benutzern, die sie getestet haben, gut angekommen ist.


 

 

 
