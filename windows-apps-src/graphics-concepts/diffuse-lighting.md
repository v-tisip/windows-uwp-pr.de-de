---
title: Diffuse Beleuchtung
description: "Die diffuse Beleuchtung arbeitet mit der Beleuchtungsrichtung und dem Normalvektor der Objektoberfläche."
ms.assetid: 8AF78742-76B1-4BBB-86E3-94AE6F48B847
keywords:
- Diffuse Beleuchtung
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 256d3ed1dd6236abe4ca93e362c52316eb548bda
ms.lasthandoff: 02/07/2017

---

# <a name="diffuse-lighting"></a>Diffuse Beleuchtung


Die *diffuse Beleuchtung* arbeitet mit der Beleuchtungsrichtung und der Normalen der Objektoberfläche. Die diffuse Beleuchtung ist je nach Oberfläche eines Objekte unterschiedlich. Dies liegt an der veränderten Beleuchtungsrichtung in dem veränderten Normalvektor der Oberfläche. Die Berechnung dauert bei der diffusen Beleuchtung länger. Dies liegt daran, dass jeder Objekt-Vertex verändert wird. Der Vorteil ist jedoch, dass sie für eine Schattierung des Objektes und somit für eine dreidimensionale Tiefe sorgt.

Nach dem Anpassen der Lichtintensität für Dämpfungseffekte berechnet die Beleuchtungs-Engine wie viel verbleibendes Licht entsprechend des Winkels des Vertex-Normalvektors und der Beleuchtungsrichtung durch einen Vertex reflektiert wird. Die Beleuchtungs-Engine überspringt diesen Schritt für direktionale Beleuchtungsquellen, denn diese werden nicht durch Entfernung gedämpft. Das System berücksichtigt zwei Reflektionstypen, die Diffuse- und Glanz-Reflektion. Es verwendet unterschiedliche Formeln zur Ermittlung des jeweils reflektierten Lichts.

Nachdem der Berechnung der reflektierten Lichtmenge wendet Direct3D die neuen Werte auf die Eigenschaften für die Diffuse- und Glanz-Reflektion des aktuellen Materials an. Die resultierenden Farbwerte sind Diffuse- und Glanz-Komponenten, die vom Rasterizer für das Gouraud-Shading und die Glanz-Hervorhebung genutzt werden.

Die diffuse Beleuchtung ist durch die folgende Gleichung definiert.

Diffuse Beleuchtung = sum\[C<sub>d</sub>\*L<sub>d</sub>\*(N<sup>.</sup>L<sub>dir</sub>)\*Atten\*Spot\]

| Parameter       | Standardwert | Type          | Beschreibung                                                                                      |
|-----------------|---------------|---------------|--------------------------------------------------------------------------------------------------|
| sum             | N/V           | N/V           | Summe der Diffuse-Komponente der einzelnen Lichtquellen.                                                     |
| C<sub>d</sub>   | (0,0,0,0)     | D3DCOLORVALUE | Diffuse-Farbe.                                                                                   |
| L<sub>d</sub>   | {0,0,0,0}     | D3DCOLORVALUE | Licht-Diffuse-Farbe.                                                                             |
| N               | N/V           | D3DVECTOR     | Vertexnormale                                                                                    |
| L<sub>Dir</sub> | N/V           | D3DVECTOR     | Richtungsvektor vom Objektvertext zur Lichtquelle                                                |
| Atten           | N/V           | FLOAT         | Lichtdämpfung Weitere Informationen unter [Dämpfung- und Spotlight-Faktor](attenuation-and-spotlight-factor.md). |
| Spot            | N/V           | FLOAT         | Spotlight Faktor. Weitere Informationen unter [Dämpfung- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).  |

 

Weitere Informationen zur Berechnung der Dämpfung- (Atten) oder Spotlight-Eigenschaften (Spot) finden Sie unter [Dämpfung- und Spotlight-Faktor](attenuation-and-spotlight-factor.md).

Nach der separaten Verarbeitung und Interpolation aller Lichtquellen werden Diffuse-Komponenten auf Werte zwischen 0 und 255 beschränkt. Der resultierende Diffuse-Beleuchtungswert ist eine Kombination aus der Ambiente-, Diffuse- und Emission-Lichtwerte.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


In diesem Beispiel wird das Objekt über die Diffuse-Lichtfarbe und die Diffuse-Materialfarbe eingefärbt.

Entsprechend der Gleichung ist die resultierende Farbe für die Objekt-Vertizes eine Kombination aus der Materialfarbe und der Lichtfarbe.

Die folgenden beiden Abbildungen zeigen die Materialfarbe (grau) und die Lichtfarbe (hellrot).

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer roten Kugel](images/lightred.jpg)

Die resultierende Szene ist in der folgenden Abbildung dargestellt. Das einzige Objekt in der Szene ist eine Kugel. Die Berechnung der diffusen Beleuchtung nimmt die Diffuse-Material- und die Diffuse-Lichtfarbe und ändert diese über das Skalarprodukt entsprechend des Winkels zwischen der Beleuchtungsrichtung und der Vertext-Normalen. Aus diesem Grund ist die Rückseite der Kugel dunkler. Denn hier zeigt die Oberfläche der Kugel vom Licht weg.

![Abbildung einer Kugel mit diffuser Beleuchtung](images/lightd.jpg)

Durch die Kombination von diffuser Beleuchtung und Abiente-Beleuchtung aus dem vorherigen Beispiel ist die gesamte Fläche des Objekts schattiert. Die Ambiente-Beleuchtung schattiert die gesamte Oberfläche. Die diffuse Beleuchtung hebt die 3D-Form des Objektes hervor (siehe nächste Abbildung).

![Abbildung einer Kugel mit diffuser Beleuchtung und Ambiente-Beleuchtung](images/lightad.jpg)

Die Berechnung der diffusen Beleuchtung ist aufwendig als die der Ambiente-Beleuchtung. Da sie von der Vertex-Normalen und die Beleuchtungsrichtung abhängig ist, können Sie die Geometrie des Objektes im 3D-Raum erkennen. Dies sorgt für eine realistischer Beleuchtung als bei der Ambiente-Beleuchtung. Sie können Glanzlichter nutzen, um ein realistischeres Erscheinungsbild zu erreichen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Beleuchtungsmathematik](mathematics-of-lighting.md)

 

 





