---
title: Spiegelbeleuchtung
description: Spiegelbeleuchtung bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird.
ms.assetid: 71F87137-B00F-48CE-8E6A-F98A139A742A
keywords:
- Spiegelbeleuchtung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 283ea63d118f9a61fe745dd3eb60b68594c32279
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6976372"
---
# <a name="specular-lighting"></a>Spiegelbeleuchtung


*Spiegelnde Beleuchtung* bezeichnet die glänzenden spiegelnden hellsten Bildteile, die auftreten, wenn Licht auf eine Objektfläche trifft und in Richtung der Kamera reflektiert wird. Spiegelnde Beleuchtung ist intensiver als diffuses Licht und fällt über die Objektoberfläche schneller ab. Die Berechnung der Spiegelbeleuchtung ist zeitaufwendiger als die für diffuse Beleuchtung. Der Vorteil der Anwendung liegt jedoch darin, dass die Oberfläche erheblich detailreicher wird.

Für das Modellieren einer spiegelnden Reflektion muss dem System die Bewegungsrichtung des Lichts und der Blickwinkel des Betrachters bekannt sein. Das System verwendet eine vereinfachte Version des Phong-Beleuchtungsmodells, das mit einer Winkelhalbierenden die Intensität der spiegelnden Reflektion angleicht.

Für den Standardzustand der Beleuchtung werden keine Glanzlichter berechnet.

## <a name="span-idspecularlightingequationspanspan-idspecularlightingequationspanspan-idspecularlightingequationspanspecular-lighting-equation"></a><span id="Specular_Lighting_Equation"></span><span id="specular_lighting_equation"></span><span id="SPECULAR_LIGHTING_EQUATION"></span>Formel der Spiegelbeleuchtung


Spiegelbeleuchtung wird durch die folgende Formel beschrieben:

|                                                                             |
|-----------------------------------------------------------------------------|
| Spiegelbeleuchtung = Cₛ \* Summe\[Lₛ \* (N · H)<sup>P</sup> \* Dämpfung \* Spotlight\] |

 

Variablen, Typen und Bereiche:

| Parameter    | Standardwert | Typ                                                             | Beschreibung                                                                                            |
|--------------|---------------|------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Cₛ           | (0,0,0,0)     | Rot, Grün, Blau und Alpha-Transparenz (Gleitkommawerte) | Glanzfarbe                                                                                        |
| Summe          | Nicht zutreffend           | N/V                                                              | Summe aller Glanzkomponenten des Lichts                                                          |
| N            | Nicht zutreffend           | 3D-Vektor (X-, Y- und Z-Gleitkommawerte)                    | Vertexnormale                                                                                         |
| H            | N/V           | 3D-Vektor (X-, Y- und Z-Gleitkommawerte)                    | Winkelhalbierende. Siehe den Abschnitt zur Winkelhalbierenden                                                |
| <sup>P</sup> | 0,0           | Gleitkomma                                                   | Stärke der spiegelnden Reflektion. Von 0 bis plus unendlich                                                     |
| Lₛ           | (0,0,0,0)     | Rot, Grün, Blau und Alpha-Transparenz (Gleitkommawerte) | Glanzfarbe des Lichts                                                                                  |
| Dämpfung        | N/V           | Gleitkomma                                                   | Lichtdämpfungswert. Siehe [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md) |
| Spotlight         | N/V           | Gleitkomma                                                   | Spotlight-Faktor. Siehe [Dämpfungs- und Spotlight-Faktor](attenuation-and-spotlight-factor.md)        |

 

Cₛ ist einer der folgenden Werte:

-   Vertexfarbe1, wenn die Glanzmaterialquelle die diffuse Vertexfarbe ist und die erste Vertexfarbe in der Vertexdeklaration angegeben ist
-   Vertexfarbe2, wenn die Glanzmaterialquelle die Glanzvertexfarbe ist und die zweite Vertexfarbe in der Vertexdeklaration angegeben ist
-   Materialglanzfarbe

**Hinweis:**  Wenn Option glanzmaterialquelle verwendet wird und die Vertexfarbe nicht angegeben, wird die materialglanzfarbe verwendet.

 

Nachdem alle Lichter verarbeitet und getrennt interpoliert wurden, sollten Glanzkomponenten auf Werte zwischen0 bis255 festgelegt sein.

## <a name="span-idthehalfwayvectorspanspan-idthehalfwayvectorspanspan-idthehalfwayvectorspanthe-halfway-vector"></a><span id="The_Halfway_Vector"></span><span id="the_halfway_vector"></span><span id="THE_HALFWAY_VECTOR"></span>Die Winkelhalbierende


Die Winkelhalbierende (H) befindet sich in der Mitte zwischen zwei Vektoren: dem Vektor von einem Objektvertex zur Lichtquelle und dem Vektor von einem Objektvertex zur Kameraposition. Direct3D bietet zwei Möglichkeiten zur Berechnung der Winkelhalbierenden. Wenn Glanzlichter relativ zur Kamera aktiviert sind (anstelle von orthogonalen Glanzlichtern), berechnet das System die Winkelhalbierende anhand der Position der Kamera und der Position des Vertex zusammen mit dem Richtungsvektor des Lichts. Die folgende Formel veranschaulicht dies:

|                                           |
|-------------------------------------------|
| H = norm(norm(Cₚ - Vₚ) + L<sub>dir</sub>) |

 

| Parameter       | Standardwert | Typ                                          | Beschreibung                                                  |
|-----------------|---------------|-----------------------------------------------|--------------------------------------------------------------|
| Cₚ              | N/V           | 3D-Vektor (X-, Y- und Z-Gleitkommawerte) | Kameraposition                                             |
| Vₚ              | N/V           | 3D-Vektor (X-, Y- und Z-Gleitkommawerte) | Vertexposition                                             |
| L<sub>dir</sub> | Nicht zutreffend           | 3D-Vektor (X-, Y- und Z-Gleitkommawerte) | Richtungsvektor von der Vertexposition zur Lichtposition |

 

Die Bestimmung der Winkelhalbierenden auf diese Weise kann rechenintensiv sein. Als Alternative wird bei der Verwendung orthogonaler Glanzlichter (anstelle von Glanzlichtern relativ zur Kamera) das System angewiesen, sich so zu verhalten, als ob sich der Blickpunkt unendlich entfernt auf der Z-Achse befinden würde. Die Formel für diese Berechnung sieht folgendermaßen aus:

|                                     |
|-------------------------------------|
| H = norm((0,0,1) + L<sub>dir</sub>) |

 

Diese Einstellung ist weniger rechenintensiv, aber auch viel unpräziser, daher sollte sie am besten in Anwendungen mit orthogonalen Projektion verwendet werden.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


In diesem Beispiel wird ein Objekt mit der Glanzlichtfarbe der Szene und einer Materialglanzfarbe eingefärbt.

Gemäß der Gleichung ist die resultierende Farbe für die Objektvertices eine Kombination aus der Materialfarbe und der Lichtfarbe.

Die beiden folgenden Abbildungen zeigen die Glanzmaterialfarbe grau und die Glanzlichtfarbe weiß.

![Abbildung einer grauen Kugel](images/amb1.jpg)![Abbildung einer weißen Kugel](images/lightwhite.jpg)

Das resultierende Glanzlicht ist in der folgenden Abbildung gezeigt.

![Abbildung des Glanzlichts](images/lights.jpg)

Durch Kombination des Glanzlichts mit der Umgebungs- und diffusen Beleuchtung wird ein Ergebnis wie in der folgenden Abbildung erzeugt. Die Anwendung aller drei Beleuchtungsarten liefert ein sehr realistisches Objekt.

![Abbildung der Kombination des Glanzlichts, des Umgebungslichts und des diffusen Lichts](images/lightads.jpg)

Für die Spiegelbeleuchtung ist eine intensivere Berechnung als für die diffuse Beleuchtung erforderlich. Sie wird normalerweise verwendet, um visuelle Hinweise zu dem Oberflächenmaterial zu geben. Das Glanzlicht ändert sich in Größe und Farbe entsprechend dem Material der Oberfläche.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Beleuchtungsmathematik](mathematics-of-lighting.md)

 

 




