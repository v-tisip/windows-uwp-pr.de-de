---
title: Grundtypen
description: "Ein 3D-Grundtyp ist eine Sammlung von Scheitelpunkten, die eine einzelne 3D-Entität bilden."
ms.assetid: A1FE6F49-B0D4-4665-90E1-40AD98E668B1
keywords:
- Grundtypen
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: e6734ff8534302d3866374adba45c34d70ae440a
ms.lasthandoff: 02/07/2017

---

# <a name="primitives"></a>Grundtypen


Ein 3D-*Grundtyp* ist eine Sammlung von Scheitelpunkten, die eine einzelne 3D-Entität bilden.

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[Punktelisten](point-lists.md)</p></td>
<td align="left"><p>Eine Punkteliste ist eine Sammlung von Scheitelpunkten, die als isolierte Punkte dargestellt werden. Die Anwendung kann Punktelisten in 3D-Szenen für Sternenfelder oder gepunktete Linien auf der Oberfläche eines Polygons verwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Zeilenlisten](line-lists.md)</p></td>
<td align="left"><p>Bei einer Zeilenliste handelt es sich um eine Liste isolierter, gerader Liniensegmente. Zeilenlisten sind hilfreich für Aufgaben wie das Hinzufügen von Schneeregen oder Starkregen zu einer 3D-Szene. Anwendungen erstellen eine Zeilenliste, indem sie eine Reihe von Scheitelpunkten ausfüllen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Zeilenstrips](line-strips.md)</p></td>
<td align="left"><p>Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Liniensegmenten besteht. Die Anwendung kann Linienstrips verwenden, um offene Polygone zu erstellen. Bei einem geschlossenes Polygon handelt es sich um ein Polygon, dessen letzter Scheitelpunkt über ein Liniensegment mit dem ersten Scheitelpunkt verbunden ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Dreieckslisten](triangle-lists.md)</p></td>
<td align="left"><p>Eine Dreiecksliste ist eine Liste isolierter Dreiecke. Die isolierten Dreiecke können sich nahe beieinander befinden oder nicht. Eine Dreiecksliste muss mindestens drei Scheitelpunkte enthalten, und die Gesamtzahl der Scheitelpunkte muss durch drei teilbar sein.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Dreiecksstrips](triangle-strips.md)</p></td>
<td align="left"><p>Ein Dreiecksstrip ist eine Reihe verbundener Dreiecke. Da die Dreiecke verbunden sind, muss die Anwendung nicht immer wieder alle drei Scheitelpunkte für alle Dreiecke angeben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 





