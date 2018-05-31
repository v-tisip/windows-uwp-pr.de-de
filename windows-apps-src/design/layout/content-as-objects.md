---
author: mijacobs
description: ''
title: Inhalte als Objekte
template: detail.hbs
ms.localizationpriority: medium
ms.openlocfilehash: 9b69eb48bc52784b52c069af4f091808d706ae16
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
ms.locfileid: "1392849"
---
# <a name="content-as-objects"></a>Inhalte als Objekte

 

Sie können die Tiefe oder z-Reihenfolge von Elementen manipulieren, um eine visuelle Hierarchie zu erstellen, die die Bedienung Ihrer Anwendung erleichtert.  

> Hinweis: Dieser Artikel ist ein früher Entwurf für eine neue Funktion von Windows 10 RS2. Featurenamen, Terminologie und Funktionen sind nicht endgültig. 

## <a name="why-visual-hierarchy-is-important"></a>Warum visuelle Hierarchie wichtig ist

Die Benutzer werden ständig mit Anfragen nach ihrer Aufmerksamkeit bombardiert. Jedes Element auf dem Bildschirm bittet darum, betrachtet zu werden, jeder Text will gelesen werden, jeder Button angeklickt werden. Da die visuelle Umgebung immer chaotischer und chaotischer wird, erfordert es mehr Mühe, die Szene zu analysieren und herauszufinden, was vor sich geht.  

Deshalb ist es so wichtig, die Elemente Ihrer Benutzeroberfläche sorgfältig auszuwählen und ein Layout zu erstellen, das eine klare visuelle Hierarchie zwischen Ihren UI-Elementen herstellt. <!-- Every element is competing for the user's attention, and every time you add an element, you add a mental tax to the user. -->

Eine klare visuelle Hierarchie sagt dem Benutzer, welche Elemente am wichtigsten sind und schafft Beziehungen zwischen den Elementen. Mit einer guten visuellen Hierarchie versteht der Benutzer das Layout der Seite auf einen Blick und kann sich auf seine Aufgabe konzentrieren. 

<p></p>


<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  <p>Wie schafft man also eine klare visuelle Hierarchie? In früheren Versionen von Windows 10 konnten Sie Leerraum, Position und Typografie verwenden, um eine visuelle Hierarchie zu definieren. </p>
  </div>
  <div class="side-by-side-content-right">
    ![Ein flaches Layout](images/content-as-objects/flat-layout.png)
    
  </div>
</div>
</div>

Mit Windows 10 RS2 haben wir buchstäblich eine weitere Dimension hinzugefügt: die Tiefe. 

![Tiefe im Layout](images/content-as-objects/depth-in-layout2.png)


## <a name="use-depth-to-establish-a-hierarchy"></a>Aufbau einer Hierarchie über Tiefe 

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
     <p>Sie können die Tiefe (z-Reihenfolge) zusammen mit Ihren anderen Designtools (Leerraum, Position, Typografie) verwenden, um eine Hierarchie aufzubauen. Heben Sie Ihre wichtigsten Elemente auf die vorderste Ebene; verwenden Sie die unteren Ebenen, um eine weniger kritische Benutzeroberfläche anzuzeigen. 

    The relative importance of an element can change throughout an experience, so you can bring elements forward as they become more important and backward as they become less important. 
    </p>
  </div>
  <div class="side-by-side-content-right">
    ![Tiefe im Layout](images/content-as-objects/elements-forward-backward.png) 
    
  </div>
</div>
</div>

## <a name="how-does-it-work"></a>Wie funktioniert das?
> TODO: Kurze Beschreibung, wie Sie die z-Reihenfolge der Elemente steuern können. Ist die z-Reihenfolge explizit fest implementiert, oder gibt es ein semantisches Ranking-System? Wie bewegen sich Objekte von einer Ebene zur anderen? Was macht das System automatisch, und worüber müssen sich Designer/Entwickler Gedanken machen? 

## <a name="the-four-layers-of-a-typical-app-layers"></a>Die vier Ebenen einer typischen App

<p>Eine typische App besteht aus 4 Ebenen.</p>
<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **Hinter dem Hintergrund** <br/>
Diese Ebene liegt hinter der App.  Wenn Elemente auf diese Ebene verschoben werden, empfehlen wir, sie nicht interaktiv zu gestalten. Elemente auf dieser Ebene haben den langsamsten Parallax-Effekt und werden auf das App-Fenster beschnitten. TODO: Ist diese Ebene skalierbar? 

<p>Beispiele für Hintergrundelemente sind das Bild hinter dem Inhalt, TODO: Beispiel, TODO: Beispiel.</p>
  </div>
  <div class="side-by-side-content-right">
    ![Die Hintergrundebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **Passive Ebene** <br/>
Dies ist die Basisebene der App, in der sich standardmäßig die UI-Elemente befinden.  Elemente bewegen sich auf dieser Ebene in Echtzeit (keine Parallax-Effekt). Sie werden auf das App-Fenster beschnitten und auf 100 % skaliert. 

<p>Beispielelemente: Der App-Hintergrund, der Text, das sekundäre UI, wie z. B. das App-Navigations-UI.</p>
  </div>
  <div class="side-by-side-content-right">
    ![Die passive Ebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **Handlungsaufforderungen** <br/>
Diese Ebene ist für interaktive Elemente bestimmt, die Sie über Elemente auf der passiven Ebene priorisieren. Elemente auf dieser Ebene haben einen mittleren Parallax-Effekt und werden auf das App-Fenster beschnitten. TODO: Skalieren Elemente auf dieser Ebene oder haben sie einen Schlagschatten?

<p>Beispielelemente: Listen, Raster, primäre Befehle (TODO: z.B.....).</p> 
  </div>
  <div class="side-by-side-content-right">
    ![Die Call-to-Action-Schicht einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>

<p></p>
<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  **Hero-Ebene** <br/>
Diese Ebene ist für das Element mit der höchsten Priorität auf dem Bildschirm.  Elemente auf dieser Ebene können die Grenzen des App-Fensters sprengen, sie können skalieren, und sie erhalten automatisch einen Schlagschatten.

<p>Beispielelemente: fotografische Elemente, das aktuell ausgewählte Element.</p>  
  </div>
  <div class="side-by-side-content-right">
    ![Die Hero-Ebene einer App](images/content-as-objects/elements-forward-backward.png)
    
  </div>
</div>
</div>



<!--
Depth is meaningful; it establishes visual and interactive hierarchy for users to efficiently complete tasks. Depth orients users in our system. 
-->

## <a name="example-tbd"></a>Beispiel: TBD
> TODO: Zeigen, wie man ein gemeinsames UI-Muster für die Verwendung der z-Reihenfolge anpasst. Wir sollten Illustrationen und Code zeigen. 

## <a name="download-the-code-samples"></a>Codebeispiele herunterladen
>TODO: Link zu Beispielen, die diese Funktion demonstrieren. 


## <a name="related-articles"></a>Verwandte Artikel
* [Inhaltsgrundlagen](../basics/content-basics.md)
