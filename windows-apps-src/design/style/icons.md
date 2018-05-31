---
author: mijacobs
Description: Good icons harmonize with typography and with the rest of the design language. They don’t mix metaphors, and they communicate only what’s needed, as speedily and simply as possible.
title: Symbole
ms.assetid: b90ac02d-5467-4304-99bd-292d6272a014
label: Icons
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 61157ad23eb55447137531922ea23fa0120e2b98
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1653919"
---
# <a name="icons-for-uwp-apps"></a>Symbole für UWP-Apps



Gute Symbole harmonieren mit der Typografie und der übrigen Gestaltungssprache. Sie verwenden keine Metaphern und geben einfach und schnell nur die erforderlichen Informationen weiter. 

## <a name="linear-scaling-size-ramps"></a>Größenabstufungen für lineare Skalierungen 

<table>
    <tr> 
        <td>16px x 16px</td>
        <td>24px x 24px</td>
        <td>32px x 32px</td>
        <td>48 x 48px</td>
    </tr>
    <tr> 
        <td><img src="images/icons-16x16.png" alt="Icons at 16x16 effective pixels" /></td>
        <td><img src="images/icons-24x24.png" alt="Icons at 24x24 effective pixels" /></td>
        <td><img src="images/icons-32x32.png" alt="Icons at 32x32 effective pixels" /></td>
        <td><img src="images/icons-48x48.png" alt="Icons at 48x48 effective pixels" /></td>
    </tr>
</table>

## <a name="common-shapes"></a>Häufige Formen

Grundsätzlich sollten Symbole den vorhandenen Platz mit geringem Abstand möglichst vollständig ausnutzen. Diese Formen sind Ausgangspunkte für die Bestimmung der Größe einfacher Formen. 

![Raster der Größe 32x32px](images/icons-common-shapes.png)

Verwenden Sie die Form, die der Ausrichtung des Symbols entspricht, und berücksichtigen Sie dabei diese grundlegenden Parameter. Symbole müssen die Form nicht unbedingt ausfüllen oder vollständig hinein passen. Sie können nach Bedarf angepasst werden, um ausgewogen zu wirken. 

<table class="uwpd-noborder">
    <tr>
        <td>Kreis<td>
        <td>Quadrat</td>
        <td>Dreieck</td>
    </tr>
    <tr>
        <td><img src="images/icons-common-shapes-examples-1.png" alt="A circle" /><td>
        <td><img src="images/icons-common-shapes-examples-2.png" alt="A square" /></td>
        <td><img src="images/icons-common-shapes-examples-3.png" alt="A triangle " /></td>
    </tr>
        <tr>
        <td>Horizontales Rechteck<td>
        <td colspan="2">Vertikales Rechteck</td>        
        </tr>
    <tr>
        <td><img src="images/icons-common-shapes-examples-4.png" alt="A horizontal rectangle" /><td>
        <td colspan="2"><img src="images/icons-common-shapes-examples-5.png" alt="A vertical rectangle" /></td>
         
    </tr>

</table>

## <a name="angles"></a>Winkel

Neben der Verwendung des gleichen Rasters und der gleichen Linienbreite werden Symbole mit einheitlichen Elementen erstellt. 

Wenn Sie beim Erstellen von Formen nur diese Winkel verwenden, sehen all Ihre Symbole einheitlich aus. Außerdem werden die Symbole dann richtig gerendert. 

Diese Linien können beim Erstellen von Symbolen kombiniert, verknüpft, gedreht und gespiegelt werden. 

<table>
    <tr>
        <td><b>1:1</b><br/>45°</td>
        <td><b>1:2</b><br />26,57° (vertikal)<br/>63,43° (horizontal)</td>
        <td><b>1:3</b><br/>18,43° (vertikal)<br/>71,57° (horizontal)</td>
        <td><b>1:4</b><br/>14,04° (vertikal)<br/>75,96° (horizontal)</td>
    </tr>
    <tr>
        
        <td><img src="images/icons-grid-1-1.png" alt="1:1" /></td>
        <td><img src="images/icons-grid-1-2.png" alt="1:2" /></td>
        <td><img src="images/icons-grid-1-3.png" alt="1:3" /></td>
        <td><img src="images/icons-grid-1-4.png" alt="1:4" /></td>
    </tr>  
</table>

<p>Einige Beispiele:</p>

<table>
    <tr>
        <td><img src="images/icons-angles-examples-1.png" alt="A 1:1 angle example" /></td>
        <td><img src="images/icons-angles-examples-2.png" alt="A 1:2 angle example" /></td>
        <td><img src="images/icons-angles-examples-3.png" alt="A 1:3 angle example" /></td>
        <td><img src="images/icons-angles-examples-4.png" alt="A 1:4 angle example" /></td>
    </tr>
</table>

## <a name="curves"></a>Kurven

Kurvenlinien entstehen aus Abschnitten eines ganzen Kreises und sollten nur dann verzerrt werden, wenn dies für die Verankerung am Pixelraster erforderlich ist. 

<table>
    <tr>
        <td>1/4-Kreis</td>
        <td>1/8-Kreis</td>
    </tr>
    <tr>
        <td><img src="images/icons-curves-14circle.png" alt="1/4 circle" /></td>
        <td><img src="images/icons-curves-18circle.png" alt="1/8 circle" /></td>
    </tr>
    <tr>
        <td><img src="images/icons-curves-examples-1.png" alt="1/4 cirlce example" /></td>
        <td><img src="images/icons-curves-examples-2.png" alt="1/8 circle example" /></td>
    </tr>    
</table>

## <a name="geometric-construction"></a>Geometrische Konstruktion

Wir empfehlen, beim Erstellen von Symbolen ausschließlich rein geometrische Formen zu verwenden.

![Gitarrensymbol mit geometrischer Überlagerung ](images/icons-geometric-construction.png)

## <a name="filled-shapes"></a>Gefüllte Formen 

Bei Bedarf können Symbole gefüllte Formen enthalten, aber sie sollten bei einer Rastergröße von 32×32px maximal 4px groß sein. Gefüllte Kreise dürfen maximal 6×6px groß sein. 

![Füllung mit 5pxx8px ](images/icons-filled-shapes.png)

## <a name="badges"></a>Signale

Ein „Signal“ ist ein allgemeiner Begriff zur Beschreibung eines Elements, das einem Symbol hinzugefügt wird, das nicht in das Ausgangselement des Symbols integriert werden soll. Diese enthalten in der Regel andere Informationen über das Symbol wie Status oder Aktion. Andere gängige Begriffe sind beispielsweise Überlagerung, Anmerkung oder Modifizierer. 

![Statussignal ](images/icons-badge-status.png)

![Aktionssignal ](images/icons-badge-action.png)

Statussignale nutzen ein ausgefülltes, farbiges Objekt, das sich auf dem Symbol befindet, während Aktionssignale im gleichen monochromen Stil und mit der gleichen Linienstärke in das Symbol integriert sind.

<table>
<tr>
    <td>Häufig verwendete Statussignale</td>
    <td>Gängige Aktionssignale</td>
</tr>
<tr>
    <td><img src="images/icons-badge-common-states-1.png" alt="Status badge " /></td>
    <td><img src="images/icons-badge-common-states-2.png" alt="Action badge " /></td>
</tr>
</table>
<p></p>

### <a name="badge-color"></a>Signalfarbe 

Farbsignale sollten nur zur Angabe des Status eines Symbols verwendet werden. Die Farben für Statussignale übermitteln dem Benutzer bestimmte emotionale Botschaften. 

<table>
<tr><td>Grün: #128B44</td><td>Blau: #2C71B9</td><td>Gelb: #FDC214</td></tr>
<tr><td>Positiv: fertig, abgeschlossen </td><td>Neutral: Hilfe, Benachrichtigung </td><td>Warnend: Hinweis, Warnung </td></tr>
<tr><td><img src="images/icons-color-inbadging-1.png" alt="Green status" /></td><td><img src="images/icons-color-inbadging-2.png" alt="Blue status" /></td>
<td><img src="images/icons-color-inbadging-3.png" alt="Yellow status" /></td></tr>
</table>
<p></p>

### <a name="badge-position"></a>Signalposition

Die Standardposition für jeden Status bzw. jede Aktion ist unten rechts. Verwenden Sie die anderen Positionen nur dann, wenn das Design die Standardposition nicht zulässt. 

### <a name="badge-sizing"></a>Signalgröße

Signale sollten bei einem Raster der Größe 32×32px 10 bis 18px umfassen. 

## <a name="related-articles"></a>Verwandte Artikel

* [Richtlinien für die Ressourcen für Kacheln und Symbole](../shell/tiles-and-notifications/app-assets.md)
