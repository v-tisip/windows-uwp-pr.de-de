---
author: mijacobs
Description: Purposeful, well-designed motion brings your app to life and makes the experience feel crafted and polished. Help users understand context changes, and tie experiences together with visual transitions.
title: Bewegung und Animation in UWP-Apps
ms.assetid: 21AA1335-765E-433A-85D8-560B340AE966
label: Motion
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1423aeff139758c780dcecb079141744931cdd7b
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816535"
---
# <a name="motion-for-uwp-apps"></a>Bewegung für UWP-Apps

Gut gestaltete Bewegungen machen Apps lebhaft und lassen sie realistisch und perfekt erscheinen. Bewegung hilft Benutzern dabei, Kontextänderungen zu verstehen, und sie zeigt Benutzern auch an, wo diese sich in der App befinden. Interaktionen werden mit visuellen Übergängen verbunden. Bewegung fügt der Oberfläche Geschwindigkeit und Mehrdimensionalität hinzu.

## <a name="benefits-of-motion"></a>Vorteile von Bewegung

Bewegung bedeutet mehr, als nur Dinge beweglich zu machen. Bewegung ist ein Tool zum Erstellen eines physischen Ökosystems, das Benutzer mithilfe verschiedener Eingabetypen wie Maus, Tastatur, Toucheingabe und Stift aktiv bearbeiten können. Die Qualität der Erfahrung hängt davon ab, wie gut die App auf den Benutzer reagiert und welche Art von Persönlichkeit die Benutzeroberfläche vermittelt.

Stellen Sie sicher, dass die Bewegung einem Zweck in Ihrer App dient. Die besten UWP-Apps (Universelle Windows-Plattform) verwenden Bewegung, um die Benutzeroberfläche zum Leben zu erwecken. Bewegung sollte:

- Feedback basierend auf dem Verhalten des Benutzers geben.
- Dem Benutzer beibringen, wie er mit der Benutzeroberfläche interagieren kann.
- Angeben, wie zu vorherigen oder folgenden Ansichten navigiert werden kann.

Wenn ein Benutzer mehr Zeit in Ihrer App verbringt oder Aufgaben in Ihrer App komplexer werden, wird qualitativ hochwertige Bewegung immer wichtiger: Mit Bewegung kann die Art und Weise verändert werden, wie der Benutzer die kognitive Belastung und die Benutzerfreundlichkeit Ihrer App wahrnimmt. Bewegung bringt viele weitere direkte Vorteile mit sich:

- **Bewegung unterstützt die Interaktion und trägt dazu bei, dass sich Benutzer zurechtfinden.**

    Bewegung ist direktional: Sie bewegt sich vor und zurück, in den Inhalt hinein und aus ihm hinaus und hinterlässt gleichzeitig mentale „Brotkrümel“-Hinweise, wie der Benutzer zur aktuellen Ansicht gelangt ist. Übergänge können Benutzern beim Erlernen der Bedienung neuer Apps helfen, indem Analogien mit Aufgaben hergestellt werden, mit denen der Benutzer bereits vertraut ist.

- **Bewegung kann den Eindruck verbesserter Leistung vermitteln.**

    Wenn die Netzwerkgeschwindigkeit langsamer wird oder das System nicht reagiert, können Animationen dem Benutzer die Wartezeit kürzer erscheinen lassen. Durch Animationen kann dem Benutzer mitgeteilt werden, dass die App noch mit der Verarbeitung beschäftigt und nicht eingefroren ist, und es können passiv neue Informationen angezeigt werden, die den Benutzer möglicherweise interessieren.

- **Bewegung schafft Persönlichkeit.**

    Bewegung ist häufig der allgemeine Thread, der die Persönlichkeit der Apps abbildet, wenn Benutzer durch eine Oberfläche navigieren.

- **Bewegung schafft Eleganz.**

    Durch fließende, reaktionsfähige Bewegungen wirken Benutzeroberflächen natürlich, und sie sorgen dafür, dass emotionale Verbindungen mit der Oberfläche entstehen.

## <a name="examples-of-motion"></a>Beispiele für Bewegung

Im Folgenden finden Sie einige Beispiele für Bewegung in einer App.

Hier verwendet eine App eine verbundene Animation, um ein Elementbild zu animieren, wenn es als Teil der Überschrift der nächsten Seite weiterbesteht. Dieser Effekt trägt dazu bei, Benutzerkontext beim Übergang beizubehalten.

![Verbundene Animation](images/connected-animations/example.gif)

Hier werden bei einem Bildlauf oder Schwenken der UI verschiedene Objekte mithilfe eines Parallax-Effekts unterschiedlich schnell verschoben. Dadurch entsteht ein Gefühl von Tiefe, Perspektive und Bewegung.

![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](images/_Parallax_v2.gif)


## <a name="types-of-motion"></a>Arten von Bewegung

<table>
    <tr>
        <th align="left">Bewegungsart</th>
        <th align="left">Beschreibung</th>
    </tr>
    <tr>
        <td><a href="motion-list.md">Hinzufügen und Löschen</a>
        </td>
        <td>Mit Listenanimationen können Sie einzelne oder mehrere Elemente in einer Sammlung wie z. B. einem Fotoalbum oder einer Liste mit Suchergebnissen einfügen oder entfernen.
        </td>
    </tr>
    <tr>
        <td><a href="connected-animation.md">Verbundene Animation</a>
        </td>
        <td>Mit verbundenen Animationen können Sie eine dynamische und ansprechende Navigationsfunktionalität erstellen, indem Sie den Übergang eines Elements zwischen zwei verschiedenen Ansichten animieren. So können Benutzer den Kontext beibehalten, und es entsteht Kontinuität zwischen den Ansichten. In einer verbundenen Animation scheint ein Element zwischen zwei Ansichten weiterzubestehen, während sich der UI-Inhalt ändert. Dabei fliegt das Element von seinem Standort in der Quellansicht über den Bildschirm zu seinem Ziel in der neuen Ansicht herüber. Dadurch wird der gemeinsame Inhalt zwischen den beiden Ansichten unterstrichen, und es entsteht ein schöner, dynamischer Effekt als Teil eines Übergangs. 
        </td>
    </tr>
    <tr>
        <td><a href="content-transition-animations.md">Inhaltsübergang</a>
        </td>
        <td>Mithilfe von Inhaltsübergangsanimationen können Sie den Inhalt eines Bildschirmbereichs ändern und gleichzeitig den Container oder Hintergrund unverändert lassen. Neuer Inhalt wird eingeblendet. Muss vorhandener Inhalt ersetzt werden, wird dieser Inhalt ausgeblendet. </td>
    </tr>
    <tr>
        <td><a href="motion-fade.md">Ein- und Ausblenden</a>
        </td>
        <td>Verwenden Sie Ein- und Ausblendungsanimationen, um Elemente anzuzeigen oder nicht anzuzeigen. Die beiden üblichen Animationen dieser Art sind das Einblenden und das Ausblenden. </td>
    </tr>
    <tr>
        <td><a href="page-transitions.md">Seitenübergang</a>
        </td>
        <td>Seitenübergänge sind Animationen, die abgespielt werden, wenn Benutzer zwischen Seiten in einer App navigieren und Feedback als Beziehung zwischen Seiten liefern.
        </td>
    </tr>
    <tr>
        <td><a href="parallax.md">Parallax</a>
        </td>
        <td>Ein visueller Parallax-Effekt hilft dabei, ein Gefühl von Tiefe, Perspektive und Bewegung zu erzeugen. Dieser Effekt wird erzielt, indem bei einem Bildlauf oder Schwenken der UI verschiedene Objekte unterschiedlich schnell verschoben werden.
        </td>
    </tr> 
    <tr>
        <td><a href="motion-pointer.md">Feedback durch Drücken</a>
        </td>
        <td>Zeigerdruckanimationen stellen visuelles Feedback für Benutzer bereit, wenn diese auf ein Element tippen. Bei der Animation für „Zeiger nach unten“ wird das gedrückte Element leicht verkleinert und geneigt. Sie wird wiedergegeben, wenn erstmalig auf ein Element getippt wird. Die Animation für „Zeiger nach oben“, mit der der ursprüngliche Zustand des Elements wiederhergestellt wird, wird beim Loslassen des Zeigers wiedergegeben.
        </td>
    </tr>
</table>

## <a name="animations-in-xaml"></a>Animationen in XAML

Weitere Informationen zur Verwendung von integrierten Animationen in XAML oder zur Erstellung Ihrer eigenen finden Sie unter [Animationen in XAML](xaml-animation.md). 