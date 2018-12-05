---
title: Transformationen
description: Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.
ms.assetid: 0DF2A99A-335C-4D14-9720-6D7996DD635A
keywords:
- Transformationen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a29d42a9254ca47402a38ea71c8c1ef69de5c6c7
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8744202"
---
# <a name="transforms"></a>Transformationen


Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine. Es ermittelt das Modell und die Anzeige im Raum, projiziert Scheitelpunkte für die Anzeige auf den Bildschirm und beschneidet Scheitelpunkte im Viewport. Darüber hinaus führt die Transformationsengine Beleuchtungsberechnungen durch, um diffuse und ausgeleuchtete Komponenten der einzelnen Scheitelpunkte festzulegen.

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
<td align="left"><p><a href="transform-overview.md">Übersicht über Transformationen</a></p></td>
<td align="left"><p>Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="world-transform.md">Welttransformationen</a></p></td>
<td align="left"><p>Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich. Im Weltbereich werden Scheitelpunkte relativ zu einem Ursprung definiert, der allen Objekten in einer Szene gemeinsam ist. Die Welt-Transformation platziert ein Modell in der Welt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="view-transform.md">Ansichtstransformation</a></p></td>
<td align="left"><p>Eine <em>Ansichtstransformation</em> lokalisiert den Betrachter im Weltbereich und transformiert dazu Scheitelpunkte in den Kamerabereich. Im Kamerabereich befindet sich die Kamera, bzw. der Betrachter, am Ursprungspunkt und blickt in die positive z-Richtung. Die Ansichtsmatrix verschiebt die Objekte in der Welt um die Position einer Kamera - den Ursprung des Kamerabereichs - und ihre Ausrichtung.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="projection-transform.md">Projektionstransformation</a></p></td>
<td align="left"><p>Eine <em>Projektionstransformation</em> steuert die internen Elemente der Kamera, z.B. die Auswahl eines Objektivs für eine Kamera. Dies ist der komplizierteste der drei Transformationstypen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 




