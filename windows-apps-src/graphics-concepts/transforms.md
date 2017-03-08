---
title: Transformationen
description: "Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine."
ms.assetid: 0DF2A99A-335C-4D14-9720-6D7996DD635A
keywords:
- Transformationen
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 2036573c0a5b2967bda38473b126b85f259c278c
ms.lasthandoff: 02/07/2017

---

# <a name="transforms"></a>Transformationen


Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine. Diese lokalisiert Modell und Betrachter in der Welt, projiziert Scheitelpunkte zur Anzeige auf dem Bildschirm und schneidet Scheitelpunkte für den Viewport zu. Darüber hinaus führt die Transformationsengine Beleuchtungsberechnungen durch, um diffuse und ausgeleuchtete Komponenten der einzelnen Scheitelpunkte festzulegen.

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
<td align="left"><p>[Übersicht über Transformationen](transform-overview.md)</p></td>
<td align="left"><p>Matrix-Transformationen kümmern sich um einen Großteil der einfachen Mathematik von 3D-Grafiken.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Welttransformationen](world-transform.md)</p></td>
<td align="left"><p>Eine Welttransformation ändert die Koordinaten vom Modellbereich, in dem Scheitelpunkte relativ zum lokalen Ursprung definiert sind, zum Weltbereich. Im Weltbereich werden Scheitelpunkte relativ zu einem Ursprung definiert, der allen Objekten in einer Szene gemeinsam ist. Die Welt-Transformation platziert ein Modell in der Welt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Ansichtstransformation](view-transform.md)</p></td>
<td align="left"><p>Eine <em>Ansichtstransformation</em> lokalisiert den Betrachter im Weltbereich und transformiert dazu Scheitelpunkte in den Kamerabereich. Im Kamerabereich befindet sich die Kamera, bzw. der Betrachter, am Ursprungspunkt und blickt in die positive z-Richtung. Die Ansichtsmatrix verschiebt die Objekte in der Welt um die Position einer Kamera - den Ursprung des Kamerabereichs - und ihre Ausrichtung.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Projektionstransformation](projection-transform.md)</p></td>
<td align="left"><p>Eine <em>Projektionstransformation</em> steuert die internen Elemente der Kamera, z. B. die Auswahl eines Objektivs für eine Kamera. Dies ist der komplizierteste der drei Transformationstypen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 





