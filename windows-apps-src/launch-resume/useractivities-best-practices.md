---
author: PatrickFarley
title: Bewährte Methoden für Benutzer Aktivitäten
description: In diesem Handbuch werden die empfohlenen Vorgehensweisen zum Erstellen und aktualisieren die Benutzeraktivitäten beschrieben.
keywords: benutzeraktivität, benutzeraktivitäten, zeitachse, cortana aufgaben weiterführen, cortana begonnene aufgaben bearbeiten, project rome
ms.author: pafarley
ms.date: 08/23/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: b11151df981a4b5ce233458581d21e405be9844c
ms.sourcegitcommit: 753dfcd0f9fdfc963579dd0b217b445c4b110a18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "2854983"
---
# <a name="user-activities-best-practices"></a>Bewährte Methoden für Benutzer Aktivitäten

In diesem Handbuch werden die empfohlenen Vorgehensweisen zum Erstellen und aktualisieren die Benutzeraktivitäten beschrieben. Eine Übersicht über die Benutzeraktivitäten-Feature für Windows finden Sie unter [Weiter Benutzeraktivität sogar über Geräte](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Oder finden Sie im [Abschnitt Benutzeraktivitäten](https://docs.microsoft.com/windows/project-rome/user-activities/) des Project-ROM für die Implementierung der Aktivitäten auf anderen Entwicklerplattformen.

## <a name="when-to-create-or-update-user-activities"></a>Zum Erstellen oder aktualisieren die Benutzeraktivitäten

Da jeder app unterscheidet, ist es auf jeder Entwickler ermitteln die beste Möglichkeit zum Zuordnen von Aktionen innerhalb der app auf die Benutzeraktivitäten. Ihre Benutzeraktivitäten wird in Cortana und Zeitachse auf einer steigenden Benutzer Produktivität und Effizienz durch Unterstützung bei der ähnliche Inhalte zu erhalten, die sie in der Vergangenheit besucht praxisorientierte präsentiert werden.

**Allgemeine Richtlinien**

* **Tragen Sie eine einzelne Aktivität für eine Gruppe von verwandten Benutzeraktionen.** Dies ist besonders relevant für Wiedergabelisten oder TV zeigt: eine einzelne Aktivität in regelmäßigen Abständen Fortschritt des Benutzers entsprechend aktualisiert werden kann. In diesem Fall müssen Sie eine einzelne Benutzeraktivität mit mehreren Verlaufselemente, die über mehrere Tage oder Wochen hinweg Zeiträume, in denen Engagements darstellt. Das gleiche gilt für Dokument-basierte Aktivitäten auf denen der Benutzer schrittweise Ihrer App Vorgangsfortschritts.
* **Speichern von Benutzerdaten in der Cloud.** Wenn Sie Aktivitäten Cross-Gerät unterstützen möchten, müssen Sie sicherstellen, dass der Inhalt erforderlich, um diese Aktivität erneut beteiligen an einen Speicherort für die Cloud gespeichert ist. Gerätespezifische Aktivitäten werden auf der Zeitachse auf dem Gerät angezeigt, in dem die Aktivität erstellt wurde, aber möglicherweise nicht auf anderen Geräten angezeigt.
* **Erstellen Sie keine Aktivitäten für Aktionen, die Benutzer nicht benötigen, um fortzusetzen.** Wenn Ihre Anwendung verwendet wird, um einfache, einmalige Vorgänge auszuführen, die Status nicht beibehalten, müssen wahrscheinlich nicht Sie eine Benutzeraktivität zu erstellen.
* **Für Aktionen, die von anderen Benutzern abgeschlossen werden keine Aktivitäten erstellt werden.** Wenn ein externes Konto dem Benutzer eine Nachricht sendet oder @-mentions sie Ihrer App sollte nicht erstellen Sie eine Aktivität für diese. Dieser Aktion wird besser durch Aktion Center-Benachrichtigungen verarbeitet.
  * Szenarien für die Zusammenarbeit sind eine Ausnahme: Wenn mehrere Benutzer auf der gleichen Aktivität (beispielsweise ein Word-Dokument) zusammen arbeiten, werden in der einen anderen Benutzer Änderungen, nachdem der Benutzer vorgenommen hat Fällen. In diesem Fall sollten Sie die vorhandene Aktivität, um die Änderungen widerzuspiegeln, die mit dem Dokument vorgenommen wurden aktualisiert. Aktualisieren die vorhandenen Benutzeraktivität Inhaltsdaten ohne Erstellen eines neuen Elements Verlauf darunter.

**Richtlinien für bestimmte Arten von apps**

Jede app unterscheidet, werden die meisten apps in einem der folgenden Interaktionsmuster zugeordnet werden.
* **Dokumentbasierter apps** – Erstellen einer Aktivität pro Dokument mit mindestens Verlaufselemente spiegeln Zeiträume, in denen verwenden. Es ist wichtig, die Aktivität aktualisieren, wie das Dokument geändert wird.
* **Spiele** – eine Aktivität für jeden Spiel speichern oder World erstellen. Wenn das Spiel nur eine einzelne Sequenz von Ebenen unterstützt, können Sie die gleiche Aktivität im Laufe der Zeit neu veröffentlichen, obwohl Sie möglicherweise die Content Daten zum Anzeigen der neuesten Fortschritt oder Erfolge aktualisieren möchten.
* **Dienstprogramm apps** – liegt nothing Ihrer App, die Benutzer müssen lassen und fortsetzen, müssen Sie nicht die Benutzeraktivitäten verwenden. Ein gutes Beispiel ist eine einfache app wie Rechner.
* **Branchen apps** – viele apps zum Verwalten von Workflows oder einfache Aufgaben vorhanden. Erstellen Sie eine Aktivität für jeden separate Workflow auf die Sie über Ihre app (beispielsweise Ausgaben meldet wäre jeweils eine separate-Aktivität, damit der Benutzer klicken Sie dann auf eine Aktivität, um festzustellen, ob Sie ein bestimmter Bericht genehmigt wurde konnte).
* **Media Wiedergabe apps** – Erstellen einer Aktivität pro logische Gruppierung des Inhalts (beispielsweise eine Wiedergabeliste, Programm oder eigenständigen Inhalte). Die zugrunde liegende Frage für app-Entwickler ist, gibt an, ob eine jedes Inhaltselement (TV-Teil, Titel) als eigenständige Inhalt oder einen Teil einer Auflistung zählt. Wenn der Benutzer entscheidet sich eine Auflistung oder sequenzielle Inhalte wiedergegeben werden sollen, ist die Auflistung als Ganzes als allgemeine Regel die Aktivität. Wenn sie die Möglichkeit, ein einzelnes Inhaltselement wiedergegeben werden sollen, ist diese einem Inhaltselement die Aktivität. Finden Sie unter folgenden spezifischeren Richtlinien.
  * **Musik: Album/Künstlers/Genre** – Wenn der Benutzer ein Album, Künstlers oder Genre wählt und Treffer **wiedergegeben werden sollen**, ist dieser Auflistung die Aktivität; Schreiben Sie eine separate Aktivität für jeden Musiktitel nicht. Für kurze Sammlungen wie einem einzelnen Album oder Sammlungen in zufälliger Reihenfolge wieder wiedergegeben wird müssen Sie nicht die Aktivität, um die aktuelle Position des Benutzers entsprechend aktualisieren. Für eine lange sequenziellen Wiedergabe wie ein Album oder Wiedergabeliste möglicherweise Ihre Position innerhalb der Album Aufzeichnung Sinn.
  * **Musik: smart Wiedergabelisten** – Anwendungen die Musik in zufälliger Reihenfolge wieder sollte eine einzelne Aktivität für diese Wiedergabeliste aufzeichnen. Wenn der Benutzer die Wiedergabeliste ein zweites Mal wiedergegeben wird, erstellen Sie zusätzliche History-Datensätze für die gleichen Aktivität. Aufzeichnen der aktuellen Position des Benutzers in der Wiedergabeliste ist nicht erforderlich, da die Sortierung zufällig ist.
  * **TV-Serie** – Wenn Ihre app konfiguriert ist, um die nächsten Teil nach Abschluss der aktuellen Unterhaltung wiedergegeben werden sollen, sollten Sie eine einzelne Aktivität für die Datenreihe TV schreiben. Wie Sie die verschiedenen folgen über mehrere Wiedergabe Sitzungen wiedergeben, aktualisieren Sie die aktuelle Position in der Datenreihe entsprechend Ihrer Aktivität, und mehrere Verlaufsdatensätze erstellt werden.
  * **Film** – ein Film ist ein einzelnes Inhaltselement und sollte einen eigene-Datensatz verfügen. Wenn der Benutzer nicht Film Teil-Wege über ansehen mehr, ist es wünschenswert, deren Position aufzuzeichnen. Wenn sie es in der Zukunft fortsetzen möchten, konnte die Aktivität Fortsetzen des Films, wo sie unterbrochen, oder sogar bitten Sie den Benutzer wieder aufgenommen oder am Anfang beginnen sollen.

## <a name="user-activity-design"></a>User Activity design

Die Benutzeraktivitäten bestehen aus drei Komponenten: eine Aktivierung URI, visuelle Daten und Metadaten.
* Die Aktivierung-URI ist ein URI, der an eine Anwendung oder ein wünschen, um die Anwendung mit einem bestimmten Kontext fortgesetzt werden kann. Normalerweise werden diese Links, das Formular oder den Protokollhandler für ein Schema (z. B. "Meine-app://page2?action=edit"). Es ist Aufgabe des Entwicklers, um zu bestimmen, wie die URI-Parameter von ihrer app behandelt werden sollen. Weitere Informationen finden Sie unter [behandeln URI Activation](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation) .
* Die Bilddaten, bestehend aus einer Gruppe von erforderlichen und optionalen Eigenschaften (zum Beispiel: Titel, Beschreibung oder-Elemente Adaptive Karte), zulassen, dass Benutzer eine Aktivität visuell zu identifizieren. Richtlinien zum Erstellen von visuellen Objekte Adaptive Karte für Ihre Aktivität finden Sie weiter unten.
* Die Metadaten ist JSON-Daten, die zum Gruppieren und Abrufen von Aktivitäten unter einem bestimmten Kontext verwendet werden können. Hat normalerweise das Format des http://schema.org Daten. Richtlinien zum Ausfüllen dieser Daten finden Sie weiter unten.

### <a name="adaptive-card-design-guidelines"></a>Adaptive Entwurfsrichtlinien für die Karte

Wenn Aktivitäten in Zeitachse angezeigt werden, werden sie von [Adaptive Karte Framework](https://docs.microsoft.com/adaptive-cards/)angezeigt. Wenn der Entwickler eine Adaptive Karte nicht für jede Aktivität bietet, erstellt Zeitachse automatisch eine einfache Karte basierend auf das app-Name/Symbol, das erforderliche Feld Titel und die optionalen Feld Beschreibung. 

App-Entwickler sollten benutzerdefinierte Karten mithilfe des einfachen Adaptive Karte JSON-Schemas bieten. Finden Sie unter [Adaptive Karten Dokumentation](https://docs.microsoft.com/adaptive-cards/authoring-cards/getting-started) für technische Anweisungen zum Erstellen adaptiver Karte-Objekten. Verweisen Sie auf die Richtlinien für das Entwerfen von Adaptive Karten in die Benutzeraktivitäten unten.
* Verwenden von Bildern
  * Verwenden Sie eine eindeutige Bild für jede Aktivität, falls möglich. Der Name der Anwendung und das Symbol werden automatisch neben der Aktivität Karte angezeigt. Zusätzliche Bilder helfen den Benutzern, die die Aktivität suchen gesucht werden.
  * Bilder darf keinen Text enthalten, die der Benutzer zum Lesen von erwartet wird. Der Text nicht verfügbar für Benutzer mit speziellen Bedürfnissen und kann nicht durchsucht werden.
  * Wenn das Bild Text nicht enthalten und zu einem 2:1-Verhältnis zugeschnitten werden kann, sollten Sie es als Hintergrundbild verwenden. Dies führt zu einer fett Aktivität-Karte die Zeitachse hervorgehoben wird. Das Bild wird etwas dunkler werden, um sicherzustellen, bleibt der Text auf der Visitenkarte angezeigt, und es wird empfohlen, den Namen der Aktivität nur in diesem Fall verwenden, wie kleinerer Text schwer gelesen werden kann.
  * Wenn das Bild auf 2:1 zugeschnitten ist nicht möglich, sollten Sie es innerhalb der Aktivität Karte einfügen.  
    * Wenn das Seitenverhältnis Quadrat oder Hochformat vorliegt, das Bild auf der rechten Seite der Karte ohne Ränder verankert werden.
    * Wenn das Seitenverhältnis Querformat Anker das Bild auf der oberen rechten Ecke der Karte ist.
* Jede Aktivität ist erforderlich, um einen Namen Aktivität angeben, die immer angezeigt werden sollen.
  * Dieser Name muss in der oberen linken Ecke der Karte mit der Option große fett angezeigt werden. Es ist wichtig, dass der Name leicht erkennbar ist, wie dies die einzige ist Teil die Benutzer sehen, wenn die Aktivität in Cortana Szenarien angezeigt wird. Mit dem gleichen Namen in Zeitachse erleichtert Benutzern, eine große Anzahl von Aktivitäten zu durchsuchen.
* Verwenden Sie das gleiche Grafikformat für alle Aktivitäten von Ihrer app aus, damit Benutzer Ihre app Aktivitäten auf einfache Weise in die Zeitachse finden können.
  * Beispielsweise sollte alle Aktivitäten dieselbe Hintergrundfarbe verwenden.
* Verwenden Sie die zusätzlichen Textinformationen möglichst selten. 
  * Zu verhindern, dass die Karte mit Text, und nur mit zusätzlichen Informationen, die Benutzer bei der Suche nach der richtigen Aktivität unterstützt oder Zustandsinformationen (beispielsweise den aktuellen Status eines bestimmten Vorgangs) widerspiegelt.

### <a name="content-metadata-guidelines"></a>Metadaten-Richtlinien

Die Benutzeraktivitäten können auch Inhaltsmetadaten, enthalten die Windows- und Cortana zum Kategorisieren Aktivitäten und zum Generieren von Rückschlüsse verwenden. Aktivitäten können dann gruppiert werden um ein bestimmtes Thema, wie ein Standort (wenn der Benutzer Urlaubszeiten untersucht wird), -Objekt (wenn der Benutzer ein Thema Recherchieren ist) oder Aktion (wenn der Benutzer über unterschiedliche apps und Websites für ein bestimmtes Produkt Einkauf ist). Es ist ratsam, die Substantive und die Aktivität beteiligt Verben darstellen. 

Im folgenden Beispiel stellt die Metadaten JSON, befolgen die Standards des [Schema.org](https://schema.org/), das Szenario: "John wiedergegeben Angry Vögel mit Steve."

```json
// John played angry birds with Steve.
{
  "@context": "http://schema.org",
  "@type": "PlayAction",
  "agent": {
    "@type": "Person",
    "name": "John"
  },
  "object": {
    "@type": "MobileApplication",
    "name": "Angry Birds."
  },
  "participant": {
    "@type": "Person",
    "name": "Steve"
  }
}
```

## <a name="key-apis"></a>Wichtige APIs

* [UserActivities-namespace](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities)

## <a name="related-topics"></a>Verwandte Themen

* [Die Benutzeraktivitäten (Project-ROM-Dokumente)](https://docs.microsoft.com/windows/project-rome/user-activities/)
* [Adaptive Karten](https://docs.microsoft.com/adaptive-cards/)
* [Adaptive Karten, Schnellansicht](http://adaptivecards.io/)
* [Behandeln der URI-Aktivierung](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
* [Mit Ihren Kunden auf jeder Plattform mit Microsoft Graph, Aktivitätenfeed und adaptiven Karten kommunizieren](https://channel9.msdn.com/Events/Connect/2017/B111)
* [Microsoft Graph](https://developer.microsoft.com/graph/)
