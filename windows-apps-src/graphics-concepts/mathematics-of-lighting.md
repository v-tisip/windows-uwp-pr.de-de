---
title: Beleuchtungsmathematik
description: Das Direct3D-Beleuchtungsmodell deckt Umgebungs-, diffuse, spiegelnde und ausstrahlende Beleuchtung ab. Dies bietet eine ausreichende Flexibilität zum Lösen einer breiten Palette an Beleuchtungssituationen. Die Gesamtmenge an Licht in einer Szene wird als globale Beleuchtung bezeichnet.
ms.assetid: D0521F56-050D-4EDF-9BD1-34748E94B873
keywords:
- Beleuchtungsmathematik
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 19734964c9b4ab087f7d5fd6ea749b57cccce26c
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5568469"
---
# <a name="mathematics-of-lighting"></a>Beleuchtungsmathematik


Das Direct3D-Beleuchtungsmodell deckt Umgebungs-, diffuse, spiegelnde und ausstrahlende Beleuchtung ab. Dies bietet eine ausreichende Flexibilität zum Lösen einer breiten Palette an Beleuchtungssituationen. Die Gesamtmenge an Licht in einer Szene wird als *globale Beleuchtung* bezeichnet.

Die globale Beleuchtung wird wie folgt berechnet:

```
Global Illumination = Ambient Light + Diffuse Light + Specular Light + Emissive Light 
```

[Umgebungsbeleuchtung](ambient-lighting.md) ist konstante Beleuchtung. Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch. Sie lässt sich schnell berechnen, bewirkt jedoch, dass Objekte flach und unrealistisch aussehen.

[Diffuse Beleuchtung](diffuse-lighting.md) hängt sowohl von der Richtung des Lichts als auch von der Flächennormalen des Objektes ab. Diffuse Beleuchtung ist auf der Oberfläche eines Objekts durch die Änderung der Richtung des Lichts und den sich ändernden Oberflächenzahlvektor unterschiedlich. Es dauert länger, diffuse Beleuchtung zu berechnen, da sie sich für jeden Eckpunkt des Objektes ändert; der Vorteil der Verwendung liegt jedoch darin, dass sie Objekten einen Schatten und eine dreidimensionale (3D) Tiefe verleiht.

[Spiegelnde Beleuchtung](specular-lighting.md) bezeichnet die hellen spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird. Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab. Die Berechnung von spiegelnder Beleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung; der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.

[Ausstrahlende Beleuchtung](emissive-lighting.md) ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten. Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend. Die Ausstrahlung wirkt sich auf die Farbe des Objekts aus und kann beispielsweise ein dunkles Material heller erscheinen lassen und einen Teil der ausgestrahlten Farbe annehmen.

Durch die Anwendung jedes dieser Beleuchtungstypen auf einer 3D-Szene kann eine realistische Beleuchtung erreicht werden. Die für Umgebungs-, ausstrahlende und diffuse Komponenten berechneten Werte werden als die diffuse Eckpunktfarbe ausgegeben; der Wert für die spiegelnde Beleuchtungskomponente wird als spiegelnde Eckpunktfarbe ausgegeben. Werte für Umgebungs-, diffuse und spiegelnde Beleuchtung können durch den Abschwächungs- und Spotlicht-Faktor eines bestimmten Lichts beeinflusst werden. Siehe [Abschwächungs- und Spotlicht-Faktor](attenuation-and-spotlight-factor.md).

Um einen realistischeren Beleuchtungseffekt zu erzielen, müssen Sie weitere Lampen hinzufügen, woraus jedoch eine längere Wiedergabe der Szene resultiert. Um alle durch einen Designer angestrebten Effekte zu erzielen, verwenden einige Spiele mehr CPU-Leistung als allgemein verfügbar. In diesem Fall es ist üblich, die Anzahl der Beleuchtungsberechnungen auf ein Minimum zu reduzieren, indem Beleuchtungskarten und Umgebungskarten eingesetzt werden, um eine Szene besser zu beleuchten, während Texturkarten verwendet werden.

Die Beleuchtung wird im Kameraraum berechnet. Siehe [Kameraraumtransformationen](camera-space-transformations.md). Optimierte Beleuchtung kann in einem Modellraum berechnet werden, in dem spezielle Bedingungen vorherrschen: die Normalvektoren sind bereits normalisiert, Eckpunktvermischung ist nicht erforderlich und Transformationsmatrizen sind orthogonal.

Alle Beleuchtungsberechnungen erfolgen im Modellraum durch Ändern von Position und Richtung der Lichtquelle, sowie der Kameraposition, um den Raum unter Verwendung des Gegenteils der Weltmatrix zu modellieren. Die resultierende Beleuchtung kann daher, wenn die Welt- oder Ansichtsmatrizen eine ungleichmäßige Skalierung einführen, unter Umständen ungenau sein.

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>Inhalt dieses Abschnitts


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="ambient-lighting.md">Umgebungslicht</a></p></td>
<td align="left"><p>Umgebungsbeleuchtung bietet konstante Beleuchtung für eine Szene. Sie leuchtet alle Objekteckpunkte gleich aus, da sie nicht von anderen Beleuchtungsfaktoren abhängig ist, wie der Eckpunktnormalen, der Richtung des Lichts, der Position der Lichtquelle, der Reichweite oder Abschwächung des Lichts. Umgebungsbeleuchtung ist in alle Richtungen konstant und färbt alle Pixel eines Objekts identisch. Sie lässt sich schnell berechnen, bewirkt jedoch, dass Objekte flach und unrealistisch aussehen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="diffuse-lighting.md">Diffuse Beleuchtung</a></p></td>
<td align="left"><p><em>Diffuse Beleuchtung</em> hängt sowohl von der Richtung des Lichts als auch von der Flächennormalen des Objekts ab. Diffuse Beleuchtung ist auf der Oberfläche eines Objekts durch die Änderung der Richtung des Lichts und den sich ändernden Oberflächenzahlvektor unterschiedlich. Es dauert länger, diffuse Beleuchtung zu berechnen, da sie sich für jeden Eckpunkt des Objektes ändert; der Vorteil der Verwendung liegt jedoch darin, dass sie Objekten einen Schatten und eine dreidimensionale (3D) Tiefe verleiht.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="specular-lighting.md">Spiegelnde Beleuchtung</a></p></td>
<td align="left"><p><em>Spiegelnde Beleuchtung</em> bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird. Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab. Die Berechnung von spiegelnder Beleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung; der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="emissive-lighting.md">Ausstrahlende Beleuchtung</a></p></td>
<td align="left"><p><em>Ausstrahlende Beleuchtung</em> ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten. Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend. Die Ausstrahlung wirkt sich auf die Farbe des Objekts aus und kann beispielsweise ein dunkles Material heller erscheinen lassen und einen Teil der ausgestrahlten Farbe annehmen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="camera-space-transformations.md">Kameraraumtransformationen</a></p></td>
<td align="left"><p>Eckpunkte im Kameraraum werden durch das Wandeln der Objekteckpunkte mit der Weltansichtsmatrix berechnet.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="attenuation-and-spotlight-factor.md">Abschwächungs- und Spotlicht-Faktor</a></p></td>
<td align="left"><p>Die diffusen und spiegelnden Beleuchtungskomponenten der globalen Beleuchtungsgleichung enthalten Begriffe, die die Abschwächung des Lichts und den Spotlicht-Kegel beschreiben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Lampen und Material](lights-and-materials.md)

 

 




