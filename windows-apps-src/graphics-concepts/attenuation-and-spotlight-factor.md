---
title: Dämpfungs- und Spotlight-Faktor
description: Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben.
ms.assetid: F61D4ACB-09AB-4087-9E2D-224E472D6196
keywords:
- Dämpfungs- und Spotlight-Faktor
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 18746ef231f7d2b387866fba82e4f12a44476001
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1044619"
---
# <a name="attenuation-and-spotlight-factor"></a>Dämpfungs- und Spotlight-Faktor


Die Komponenten für diffuse und Glanzlichtbeleuchtung der globalen Beleuchtungsgleichung enthalten Begriffe, die die Lichtdämpfung und den Blickpunkt-Kegel beschreiben. Diese Begriffe werden nachfolgend beschrieben.

## <a name="span-idattenuationspanspan-idattenuationspanspan-idattenuationspanattenuation"></a><span id="Attenuation"></span><span id="attenuation"></span><span id="ATTENUATION"></span>Dämpfung


Die Lichtdämpfung hängt vom Typ des Lichts und dem Abstand zwischen dem Licht und der Vertexposition ab. Verwenden Sie eine der folgenden Formeln, um die Dämpfung zu berechnen.

Atten = 1/( att0<sub>i</sub> + att1<sub>i</sub> \* d + att2<sub>i</sub> \* d²)

Dabei gilt:

| Parameter        | Standardwert | Typ           | Beschreibung                                     | Bereich          |
|------------------|---------------|----------------|-------------------------------------------------|----------------|
| att0<sub>i</sub> | 0,0           | Gleitkomma | Konstanter Dämpfungsfaktor                     | 0 bis +unendlich |
| att1<sub>i</sub> | 0,0           | Gleitkomma | Linearer Dämpfungsfaktor                       | 0 bis +unendlich |
| att2<sub>i</sub> | 0,0           | Gleitkomma | Quadratischer Dämpfungsfaktor                    | 0 bis +unendlich |
| d                | Nicht zutreffend           | Gleitkomma | Abstand zwischen Vertexposition und Position der Lichtquelle | Nicht zutreffend            |

 

-   Dämpfung = 1, wenn das Licht ein gerichtetes Licht ist.
-   Dämpfung = 0, wenn der Abstand zwischen Licht und Vertex die Reichweite des Lichts überschreitet.

Der Abstand zwischen Lichtquelle und Vertexposition ist immer positiv.

d = | L<sub>dir</sub> |

Dabei gilt:

| Parameter       | Standardwert | Typ                                             | Beschreibung                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| L<sub>dir</sub> | Nicht zutreffend           | 3D-Vektor mit X-, Y- und Z-Gleitkommawerten | Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle |

 

Wenn d größer als die Reichweite des Lichts ist, nimmt Direct3D keine weiteren abnehmenden Berechnungen vor und wendet keine Effekte von der Lichtquelle bis zum Vertex an.

Die Dämpfungskonstanten fungieren in der Formel als Koeffizient – Sie können eine Vielzahl von Dämpfungskurven erstellen, indem Sie diese einfach anpassen. Sie können Dämpfung1 auf 1,0 einstellen, um ein Licht zu erstellen, das sich nicht dämpfen lässt aber trotzdem von der Reichweite begrenzt ist. Sie können ebenfalls mit verschiedenen Werten experimentieren, um verschiedene Dämpfungseffekte zu erzielen.

Die Dämpfung bei maximaler Reichweite des Lichts ist 0,0. Um zu verhindern, dass Lichter plötzlich angezeigt werden, wenn sie sich in Reichweite des Lichts befinden, kann eine Anwendung die Reichweite des Lichts erhöhen. Die Anwendung kann ebenfalls Dämpfungskonstanten so einrichten, dass der Dämpfungsfaktor nahe an der Reichweite 0,0 des Lichts liegt. Der Dämpfungswert wird mit den roten, grünen und blauen Komponenten der Farbe des Lichts multipliziert, um die Intensität des Lichts als Faktor der Distanz zu skalieren, die das Licht bis zum Vertex zurücklegt.

## <a name="span-idspotlight-factorspanspan-idspotlight-factorspanspan-idspotlight-factorspanspotlight-factor"></a><span id="Spotlight-Factor"></span><span id="spotlight-factor"></span><span id="SPOTLIGHT-FACTOR"></span>Spotlight-Faktor


Die folgende Gleichung legt den Spotlight-Faktor fest.

![Gleichung für den Spotlight-Faktor](images/dx8light9.png)

| Parameter         | Standardwert | Typ           | Beschreibung                              | Bereich                    |
|-------------------|---------------|----------------|------------------------------------------|--------------------------|
| rho<sub>i</sub>   | Nicht zutreffend           | Gleitkomma | Kosinus(Winkel) für Spotlight i            | Nicht zutreffend                      |
| phi<sub>i</sub>   | 0,0           | Gleitkomma | Halbschatten-Winkel für Spotlight i nach Bogenmaß | \[theta<sub>i</sub>, pi) |
| theta<sub>i</sub> | 0,0           | Gleitkomma | Kernschatten-Winkel für Spotlight i nach Bogenmaß    | \[0, pi)                 |
| Farbverlauf           | 0,0           | Gleitkomma | Farbverlaufsfaktor                           | (-unendlich +unendlich)   |

 

Dabei gilt:

rho = norm(L<sub>dcs</sub>)<sup>.</sup>norm(L<sub>dir</sub>)

und

| Parameter       | Standardwert | Typ                                             | Beschreibung                                                 |
|-----------------|---------------|--------------------------------------------------|-------------------------------------------------------------|
| L<sub>dcs</sub> | Nicht zutreffend           | 3D-Vektor mit X-, Y- und Z-Gleitkommawerten | Der negativen Wert der Lichteinfallsrichtung im Kamerabereich         |
| L<sub>dir</sub> | Nicht zutreffend           | 3D-Vektor mit X-, Y- und Z-Gleitkommawerten | Richtungsvektor von der Vertexposition bis zur Position der Lichtquelle |

 

Nach dem Berechnen der Lichtdämpfung berücksichtigt Direct3D auch eventuelle Spotlight-Effekte, den vom Licht von der Oberfläche reflektierten Winkel und den Reflexionsgrad des aktuellen Materials, um die diffusen und Glanzlichtkomponenten für den Vertex zu berechnen. Siehe auch Spotlight unter [Lichttypen](light-types.md).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Beleuchtungsmathematik](mathematics-of-lighting.md)

 

 




