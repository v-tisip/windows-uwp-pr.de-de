---
author: mijacobs
title: "Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design"
description: .
ms.assetid: BF42E810-CDC8-47D2-9C30-BAA19DCBE2DA
label: Screen sizes and break points
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: b56cdeeb9a3c3d3ca89e19d8057e3d93241e6c3c
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
#  <a name="screen-sizes-and-break-points-for-responsive-design"></a>Bildschirmgrößen und Haltepunkte für reaktionsfähiges Design

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Die Anzahl der Geräteziele und Bildschirmgrößen bei Windows 10 ist zu groß, um alle beim Optimieren der Benutzeroberfläche zu bedenken. Stattdessen wird empfohlen, bei der Entwicklung einige wichtige Bildschirmbreiten (auch als „Haltepunkte“ bezeichnet) zu berücksichtigen: 360, 640, 1024 und 1366 epx.

> [!TIP]
> Bei der Entwicklung für bestimmte Haltepunkte sollten Sie den für Ihre App verfügbaren Bildschirmbereich (App-Fenster) berücksichtigen. Wenn die App im Vollbildmodus ausgeführt wird, hat das App-Fenster die gleiche Bildschirmgröße zur Verfügung, in anderen Fällen ist es jedoch kleiner.
 

In dieser Tabelle werden die verschiedenen Größenklassen beschrieben und allgemeine Empfehlungen für die Anpassung für diese Größenklassen aufgeführt.

![Reaktionsfähige Designhaltepunkte](images/rsp-design/rspd-breakpoints.png)

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Größenklasse</th>
<th align="left">klein</th>
<th align="left">mittel</th>
<th align="left">groß</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;">Normale Bildschirmgröße (diagonal)</td>
<td style="vertical-align:top;">4&quot; bis 6&quot;</td>
<td style="vertical-align:top;">7&quot; bis 12&quot;, oder TV-Geräte</td>
<td style="vertical-align:top;">13&quot; und größer</td>
</tr>
<tr class="even">
<td style="vertical-align:top;">Typische Geräte</td>
<td style="vertical-align:top;">Smartphones</td>
<td style="vertical-align:top;">Phablets, Tablets, TV-Geräte</td>
<td style="vertical-align:top;">PCs, Laptops, Surface Hubs</td>
</tr>
<tr class="odd">
<td style="vertical-align:top;">Übliche Fenstergrößen in effektiven Pixeln</td>
<td style="vertical-align:top;">320 x 569, 360 x 640, 480 x 854</td>
<td style="vertical-align:top;">960 x 540, 1024 x 640</td>
<td style="vertical-align:top;">1366 x 768, 1920 x 1080</td>
</tr>
<tr class="even">
<td style="vertical-align:top;">Fensterbreite-Haltepunkte in effektiven Pixeln</td>
<td style="vertical-align:top;">640 Pixel oder weniger</td>
<td style="vertical-align:top;">641 Pixel bis 1007 Pixel</td>
<td style="vertical-align:top;">1008 Pixel oder größer</td>
</tr>
<tr class="odd">
<td style="vertical-align:top;">Allgemeine Empfehlungen</td>
<td style="vertical-align:top;"><ul>
<li>Zentrieren Sie Registerkartenelemente.</li>
<li>Legen Sie den linken und den rechten Fensterrand auf 12px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</li>
<li>Docken Sie [App-Leisten](../controls-and-patterns/app-bars.md) für bessere Erreichbarkeit am unteren Fensterrand an.</li>
<li>Verwenden Sie jeweils eine Spalte/Region.</li>
<li>Verwenden Sie ein Symbol zum Darstellen der Suche (kein Suchfeld anzeigen).</li>
<li>Verwenden Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im Überlagerungsmodus, um Platz auf dem Bildschirm zu sparen.</li>
<li>Verwenden Sie für das [Master/Details-Modell](../controls-and-patterns/master-details.md) den gestapelten Darstellungsmodus, um Platz auf dem Bildschirm zu sparen.</li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li>Richten Sie Registerkartenelemente linksbündig aus.</li>
<li>Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</li>
<li>Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</li>
<li>Bis zu zwei Spalten/Regionen</li>
<li>Zeigen Sie das Suchfeld an.</li>
<li>Legen Sie für [Navigationsleiste](../controls-and-patterns/navigationview.md) den Streifenmodus fest, sodass immer ein schmaler Streifen mit Symbolen angezeigt wird.</li>
<li>Ziehen Sie weitere Anpassungen für [TV-Umgebungen](http://go.microsoft.com/fwlink/?LinkId=760736) in Erwägung.</li>
</ul></td>
<td style="vertical-align:top;"><ul>
<li>Richten Sie Registerkartenelemente linksbündig aus.</li>
<li>Legen Sie den linken und den rechten Fensterrand auf 24px fest, um eine visuelle Trennung zwischen dem linken und dem rechten Rand des App-Fensters zu erzielen.</li>
<li>Positionieren Sie Elemente wie [App-Leisten](../controls-and-patterns/app-bars.md) am oberen Rand des App-Fensters.</li>
<li>Bis zu drei Spalten/Regionen</li>
<li>Zeigen Sie das Suchfeld an.</li>
<li>Platzieren Sie den [Navigationsbereich](../controls-and-patterns/navigationview.md) im angedockten Modus so, dass er immer angezeigt wird.</li>
</ul></td>
</tr>
</tbody>
</table>

Mit [**Continuum for Phones**](http://go.microsoft.com/fwlink/p/?LinkID=699431), einer neuen Funktion für kompatible Windows 10-Mobilgeräte, können Benutzer ihre Smartphones mit einem Bildschirm, einer Maus und einer Tastatur verbinden und damit ihr Gerät wie einen Laptop nutzen. Berücksichtigen Sie diese neue Funktion beim Entwerfen für bestimmte Haltepunkte – ein Mobiltelefon bleibt nicht immer in einer Klasse mit geringer Größe.
 
