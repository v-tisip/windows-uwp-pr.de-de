---
title: Transformationen
description: Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.
ms.assetid: 0DF2A99A-335C-4D14-9720-6D7996DD635A
keywords:
- Transformationen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 9f456d6d3fc1b1300e80c39b01eaed1b654159cd
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1652879"
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

 

 




