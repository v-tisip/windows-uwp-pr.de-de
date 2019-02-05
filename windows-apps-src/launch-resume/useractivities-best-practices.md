---
title: Bewährte Methoden für Benutzeraktivitäten
description: Dieser Leitfaden zeigt die empfohlenen Methoden zum Erstellen und Aktualisieren von Aktivitäten des Benutzers.
keywords: benutzeraktivität, benutzeraktivitäten, zeitachse, cortana aufgaben weiterführen, cortana begonnene aufgaben bearbeiten, project rome
ms.date: 08/23/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e98f5d73cf2d1afb26a823ed417c8980d118485c
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9046879"
---
# <a name="user-activities-best-practices"></a>Bewährte Methoden für Benutzeraktivitäten

Dieser Leitfaden zeigt die empfohlenen Methoden zum Erstellen und Aktualisieren von Aktivitäten des Benutzers. Eine Übersicht über die Aktivitäten des Benutzers Feature unter Windows finden Sie [Weiter Benutzeraktivitäten geräteübergreifend](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Alternativ finden Sie im [Abschnitt Benutzeraktivitäten](https://docs.microsoft.com/windows/project-rome/user-activities/) Projekt "ROME" für die Implementierung der Aktivitäten auf anderen Entwicklungsplattformen.

## <a name="when-to-create-or-update-user-activities"></a>Zum Erstellen oder Aktualisieren von Benutzeraktivitäten

Da jede app unterscheidet, ist es an alle Entwickler, um zu bestimmen, die beste Möglichkeit, die Aktionen innerhalb der app die Aktivitäten des Benutzers zugeordnet. Die Aktivitäten des Benutzers wird in Cortana und Zeitachse konzentriert sind Effizienz und Produktivität erhöhen der Benutzer wieder Inhalt abrufen, die sie in der Vergangenheit besucht Ihnen helfen präsentiert.

**Allgemeine Richtlinien**

* **Notieren Sie eine einzelne Aktivität für eine Gruppe von verwandten Benutzeraktionen.** Dies ist besonders wichtig für Wiedergabelisten oder Fernsehsendungen: eine einzelne Aktivität kann in regelmäßigen Abständen der Fortschritt des Benutzers entsprechend aktualisiert werden. In diesem Fall müssen Sie eine einzelne Benutzeraktivität mit mehreren Verlauf Elementen, die Zeiträume Engagement über mehrere Tage oder Wochen darstellt. Das gleiche gilt für Dokument-basierte Aktivitäten auf denen der Benutzer schrittweisen Fortschritt in Ihre app macht.
* **Speichern von Benutzerdaten in der Cloud.** Wenn Sie Geräteübergreifende Aktivitäten unterstützen möchten, müssen Sie sicherstellen, dass der Inhalt erforderlich, um diese Aktivität erneut Kontakt an einen Cloud-Speicherort gespeichert wird. Gerätespezifische Aktivitäten werden auf der Zeitachse auf dem Gerät, in dem die Aktivität erstellt wurde aber nicht auf anderen Geräten angezeigt werden.
* **Erstellen Sie Aktivitäten nicht für Aktionen, die Benutzer nicht benötigen, um fortzusetzen.** Wenn Ihre Anwendung verwendet wird, um einfachen, einmaligen Vorgänge ausführen, die nicht Status beibehalten, müssen wahrscheinlich nicht Sie eine Aktivität des Benutzers zu erstellen.
* **Für Aktionen, die von anderen Benutzern abgeschlossen werden keine Aktivitäten erstellt werden.** Wenn ein externes Konto des Benutzers eine Nachricht sendet oder @-mentions sie innerhalb Ihrer app, sollten Sie keine Aktivität für dieses erstellen. Diese Art von Aktion wird vom Info-Center-Benachrichtigungen besser bereitgestellt.
  * Szenarien für die Zusammenarbeit sind eine Ausnahme: Wenn mehrere Benutzer auf der gleichen Aktivität (z. B. einem Word-Dokument) zusammen arbeiten, es werden Fälle, in denen ein anderer Benutzer nach der Benutzer bearbeitet hat. In diesem Fall sollten Sie die vorhandene Aktivität entsprechend Änderungen, die auf das Dokument vorgenommen wurden aktualisiert. Dies beinhaltet Aktualisieren der vorhandenen Aktivität des Benutzers-Content-Daten ohne ein neues Element Verlauf erstellen.

**Richtlinien für bestimmte Arten von apps**

Während jeder app unterscheidet, fallen die meisten apps in einem der folgenden Interaktionsmuster.
* **Dokument-basierte apps** – Erstellen einer Aktivität pro Dokument, das mit mindestens ein Verlauf Elemente reflektieren Zeiträume verwenden. Es ist wichtig, die Aktivität zu aktualisieren, sobald das Dokument geändert wird.
* **Spiele** – erstellen Sie eine Aktivität für jeden Spiel speichern oder Welt. Wenn Ihr Spiel nur eine einzelne Sequenz von Ebenen unterstützt, können Sie dieselbe Aktivität im Laufe der Zeit erneut veröffentlichen, obwohl die Content-Daten zum Anzeigen der aktuelle Status oder Erfolge aktualisieren möchten.
* **Hilfsprogramm-apps** – ist nichts in Ihrer app, die Benutzer müssen lassen und fortsetzen, müssen Sie nicht Aktivitäten des Benutzers zu verwenden. Ein gutes Beispiel ist eine einfache app wie Rechner.
* **Branchen - apps** – viele apps, die für die Verwaltung von einfachen Aufgaben oder Workflows vorhanden sind. Erstellen Sie eine Aktivität für jeden separaten Workflow durch die app zugegriffen (z. B. Ausgaben meldet wäre jeweils eine separate Aktivität, damit der Benutzer klicken kann eine Aktivität, um festzustellen, ob Sie ein bestimmter Bericht genehmigt wurde).
* **Medien-Wiedergabe-apps** – Erstellen einer Aktivität pro logische Gruppierung von Inhalt (z. B. eine Wiedergabeliste, Programm oder eigenständigen Inhalt). Die zugrunde liegende Frage für app-Entwickler ist ein jedes Inhaltselement (TV-Folge, Titel) gibt an, ob als eigenständige Inhalt oder als Teil einer Sammlung zählt. Wenn der Benutzer entscheidet, um eine Sammlung oder sequenzielle Inhalte wiederzugeben, ist die Auflistung als Ganzes Regel die Aktivität. Wenn sie ablehnen, um einen einzelnen Teilinhalt wiederzugeben, ist diese einem Inhaltselement die Aktivität. Finden Sie unter folgenden spezifischere Richtlinien.
  * **Musik: Alben/Künstler/Genre** – Wenn der Benutzer ein Album, Künstler oder Genre wählt und Treffer **Wiedergeben**, ist diese Sammlung der Aktivität Schreiben Sie eine separate Aktivität für jeden Musiktitel nicht. Kurze Sammlungen wie einem einzelnen Album oder Sammlungen werden in zufälliger Reihenfolge wiedergegeben müssen Sie möglicherweise nicht die Aktivität, um die aktuelle Position des Benutzers entsprechend aktualisieren. Für eine lange sequenziellen Wiedergabe z. B. einem Album oder die Wiedergabeliste möglicherweise Ihre Position innerhalb des Albums Aufzeichnung sinnvoll.
  * **Musik: smart-Wiedergabelisten** – Anwendungen, die Musik wiedergegeben werden in zufälliger Reihenfolge aufzeichnen eine einzelne Aktivität für diese Wiedergabeliste. Wenn der Benutzer die Wiedergabeliste ein zweites Mal wiedergegeben wird, erstellen Sie zusätzliche Verlaufsdatensätze für die gleiche Aktivität. Aufzeichnen der aktuellen Position des Benutzers in der Wiedergabeliste ist nicht erforderlich, da die Reihenfolge zufällige ist.
  * **TV-Serie** – Wenn Ihre app konfiguriert ist, um die nächsten Folge wiedergegeben, nachdem der aktuellen abgeschlossen ist, sollten Sie eine einzelne Aktivität für die TV-Serie schreiben. Wie Sie die verschiedenen folgen über mehrere anzeigen Sitzungen hinweg spielen, aktualisieren Sie Ihre Aktivität entsprechend die aktuelle Position in der Reihe und mehrere Verlaufsdatensätze erstellt werden.
  * **Film** – ein Films ist eine einzelne Inhalt und sollte eine eigene Verlaufsdatensatz. Wenn der Benutzer Film Teil-Angebotspreis ansehen beendet, ist es wünschenswert, notieren Sie ihre Position. Wenn sie es in der Zukunft fortsetzen möchten, kann die Aktivität Fortsetzen des Films, wo sie haben aufgehört, oder bitten Sie den Benutzer auch verwenden, um fortsetzen oder am Anfang.

## <a name="user-activity-design"></a>Benutzer Aktivität design

Benutzeraktivitäten bestehen aus drei Komponenten: ein URI-Aktivierung visual-Daten und Content-Metadaten.
* Die Aktivierung URI ist ein URI, der an eine Anwendung oder Erfahrung, um die Anwendung in einem bestimmten Kontext fortzusetzen übergeben werden kann. In der Regel sind diese Links Protokollhandler für ein Schema (z. B. "Eigene-app://page2?action=edit"). Es ist Aufgabe den Entwickler bestimmen, wie URI-Parameter von ihrer app behandelt werden. Weitere Informationen finden Sie unter [Behandeln der URI-Aktivierung](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation) .
* Die Bilddaten, bestehend aus einer Reihe von erforderlichen und optionalen Eigenschaften (z. B.: Titel, Beschreibung oder Adaptive Karten-Elementen), können Benutzer eine Aktivität visuell identifizieren. Nachfolgend finden Sie Richtlinien zum Erstellen von adaptiven Karte visuelle Elemente für Ihre Aktivität.
* Die Content-Metadaten ist JSON-Daten, die zum Gruppieren und Abrufen von Aktivitäten in einem bestimmten Kontext verwendet werden können. In der Regel handelt es sich hierbei der http://schema.org Daten. Nachfolgend finden Sie Richtlinien auf diese Daten ausfüllen.

### <a name="adaptive-card-design-guidelines"></a>Adaptive Karte-Entwurfsrichtlinien

Wenn Aktivitäten in der Zeitachse angezeigt werden, werden sie mit [adaptiven Karte Framework](https://docs.microsoft.com/adaptive-cards/)angezeigt. Wenn der Entwickler nicht für jede Aktivität eine Adaptive Karte bereitstellt, erstellt die Zeitachse automatisch eine einfache Karte basierend auf Name/Symbol für die app, die erforderlichen Titelfeld und optional Beschreibungsfeld. 

App-Entwicklern werden empfohlen, benutzerdefinierte Karten, die mithilfe des einfachen Adaptive Karte JSON-Schemas bereitzustellen. Finden Sie in der [Dokumentation Adaptive Karten](https://docs.microsoft.com/adaptive-cards/authoring-cards/getting-started) technische Informationen zum Erstellen von adaptiven Karte-Objekten. Finden Sie in den Richtlinien unten zum Entwerfen von Adaptive Karten in Aktivitäten des Benutzers.
* Verwenden Sie Bilder
  * Mithilfe eines eindeutigen für jede Aktivität, wenn möglich. Der Name der Anwendung und das Symbol werden automatisch neben Ihrer Aktivität Karte angezeigt. Zusätzliche Bilder hilft den Benutzern, die die Aktivität suchen sie suchen.
  * Bilder sollten nicht Text enthalten, die der Benutzer muss zum Lesen. Dieser Text wird nicht verfügbar sein, um Benutzer mit speziellen Bedürfnissen und kann nicht durchsucht werden.
  * Wenn das Bild nicht Text enthalten und zu einem 2:1-Verhältnis zugeschnitten werden kann, sollten Sie es als Hintergrundbild verwenden. Dies führt eine fett aktivitätskarte, die in der Zeitachse hebt wird. Das Bild wird etwas dunkler werden, um sicherzustellen, dass der Text auf der Karte sichtbar bleibt, und es wird empfohlen, den Namen der Aktivität nur in diesem Fall verwenden, wie kleinerer Text schwer lesbar sein kann.
  * Wenn das Bild kann nicht auf 2:1 zugeschnitten werden, sollten Sie es die Aktivität-Karte speichern.  
    * Ist das Seitenverhältnis Quadrat oder Hochformat entsprechen, verankern Sie das Bild auf der rechten Seite der Karte ohne Ränder.
    * Wenn das Seitenverhältnis Querformat, Anchor das Bild an der oberen rechten Ecke der Karte ist.
* Jede Aktivität ist erforderlich, um den Namen einer Aktivität, bereitzustellen, der immer angezeigt werden soll.
  * Dieser Name sollte in der oberen linken Ecke der Karte mit der Option große fett formatierter Text angezeigt werden. Es ist wichtig, dass der Name leicht erkennbar, da dies die einzigen Teil Benutzern wird angezeigt, wenn die Aktivität in Cortana Szenarien angezeigt wird. Mit dem gleichen Namen in der Zeitachse erleichtert es Benutzern, eine große Anzahl von Aktivitäten zu durchsuchen.
* Verwenden Sie den gleichen visuellen Stil für alle Aktivitäten aus Ihrer app, sodass Benutzer Ihre app Aktivitäten leicht auf der Zeitachse finden können.
  * Beispielsweise sollten alle Aktivitäten dieselbe Hintergrundfarbe verwenden.
* Verwenden Sie zusätzliche Textinformationen sparsam ein. 
  * Zu verhindern, dass die Karte mit Text, und nur ergänzende Informationen, die Benutzer bei der Suche nach der richtigen Aktivität unterstützt oder reflektiert Statusinformationen (z. B. den aktuellen Fortschritt in einer bestimmten Aufgabe).

### <a name="content-metadata-guidelines"></a>Content-Metadaten-Richtlinien

Aktivitäten des Benutzers können auch Content-Metadaten enthalten, die Windows und Cortana verwenden, um Aktivitäten kategorisieren und Rückschlüsse zu generieren. Aktivitäten können dann gruppiert werden, um ein bestimmtes Thema, z. B. eine Position (wenn der Benutzer Ferienreisen untersucht wird), Objekt (wenn der Benutzer etwas untersucht ist) oder eine Aktion, (wenn der Benutzer für ein bestimmtes Produkt auf verschiedenen apps und Websites shopping-ist). Es ist sinnvoll, sowohl die Substantiven und die eine Aktivität beteiligt Verben darstellen. 

Im folgenden Beispiel wird die Content-Metadaten JSON, nach den Standards der [Schema.org](https://schema.org/), das Szenario darstellt: "John wird wiedergegeben, verärgert Tiere mit Steve."

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

* [Aktivitäten des Benutzers (Projekt "ROME" Dokumente)](https://docs.microsoft.com/windows/project-rome/user-activities/)
* [Adaptive Karten](https://docs.microsoft.com/adaptive-cards/)
* [Adaptive Karten, Schnellansicht](https://adaptivecards.io/)
* [Behandeln der URI-Aktivierung](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation)
* [Mit Ihren Kunden auf jeder Plattform mit Microsoft Graph, Aktivitätenfeed und adaptiven Karten kommunizieren](https://channel9.msdn.com/Events/Connect/2017/B111)
* [Microsoft Graph](https://developer.microsoft.com/graph/)
