---
title: Koordinatensysteme
description: 'Normalerweise verwenden 3D-Grafikanwendungen einen von zwei Typen an kartesischen Koordinatensystemen: rechts- oder linkshändig. In beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben.'
ms.assetid: 138D9B81-146F-4E9F-B742-1EDED8FBF2AE
keywords:
- Koordinatensysteme
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: f85bf490bd1dd68e2d0ba31335f2fc0f89fe27b0
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8323812"
---
# <a name="coordinate-systems"></a>Koordinatensysteme


Normalerweise verwenden 3D-Grafikanwendungen einen von zwei Typen an kartesischen Koordinatensystemen: rechts- oder linkshändig. In beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben.

## <a name="span-idleftandrighthandedcoordinatesspanspan-idleftandrighthandedcoordinatesspanspan-idleftandrighthandedcoordinatesspanleft-and-right-handed-coordinates"></a><span id="Left_and_right_handed_coordinates"></span><span id="left_and_right_handed_coordinates"></span><span id="LEFT_AND_RIGHT_HANDED_COORDINATES"></span>Rechts- oder linkshändige Koordinaten


Sie können sich an die Richtung der positiven X-Achse dadurch erinnern, indem Sie Ihre Finger von der linken oder rechten Hand für die positive X-Richtung ausstrecken und für die positive Y-Richtung zusammen krümmen. Die Richtung, in die der Daumen zeigt, entweder auf Sie zu oder von Ihnen weg, ist die Richtung der positiven Z-Achse für das Koordinatensystem. Die folgende Abbildung zeigt diese zwei Koordinatensysteme.

![Abbildung des linkshändigen und rechtshändigen kartesischen Koordinatensystems](images/leftrght.png)

Direct3D verwendet ein linkshändiges Koordinatensystem. Obwohl links- und rechtshändige Koordinaten die am häufigsten verwendeten Systeme sind, gibt es eine Vielzahl anderer Koordinatensysteme bei 3D-Software. Es ist für 3D-Modellierungs-Apps beispielsweise nicht ungewöhnlich, ein Koordinatensystem zu verwenden, bei dem die Y-Achse auf den Anwender zu oder von ihm hinweg zeigt und die Z-Achse nach oben zeigt.

## <a name="span-idverticesandvectorsspanspan-idverticesandvectorsspanspan-idverticesandvectorsspanvertices-and-vectors"></a><span id="Vertices_and_vectors"></span><span id="vertices_and_vectors"></span><span id="VERTICES_AND_VECTORS"></span>Scheitelpunkte und Vektoren


Je nach Koordinatensystem kann eine X-, Y- und Z-Koordinate einen Punkt im Raum definieren (einen „Scheitelpunkt”) oder eine 3D-Richtung (einen „Vektor”) definieren.

Zum Definieren von Linien und Formen kann eine Sammlung von Scheitelpunkten verwendet werden. Die einfachsten, von Scheitelpunkten definierbaren Objekte heißen [Grundtypen](primitives.md) und ein komplexeres, durch eine Reihe von Grundtypen definiertes Objekt heißt „Gitter”.

Die grundlegenden Operationen auf in einem 3D-Koordinatensystem definierten Gittern sind Übersetzung, Drehung und Skalierung. Sie können diese einfachen Transformationen kombinieren, um eine Transformationsmatrix zu erstellen. Weitere Informationen finden Sie unter [Transformationen](transforms.md).

Wenn Sie diese Vorgänge kombinieren, sind die Ergebnisse nicht kommutativ. Die Reihenfolge, in der Sie Matrizen multiplizieren, ist wichtig.

## <a name="span-idportingfromaright-handedcoordinatesystemspanspan-idportingfromaright-handedcoordinatesystemspanspan-idportingfromaright-handedcoordinatesystemspanporting-from-a-right-handed-coordinate-system"></a><span id="Porting_from_a_right-handed_coordinate_system"></span><span id="porting_from_a_right-handed_coordinate_system"></span><span id="PORTING_FROM_A_RIGHT-HANDED_COORDINATE_SYSTEM"></span>Portieren von einem rechtshändigen Koordinatensystem


Wenn Sie eine auf einem rechtshändigen Koordinatensystem basierende Anwendung portieren, müssen Sie zwei Änderungen an den auf Direct3D übergebenen Daten vornehmen:

-   Spiegeln Sie die Reihenfolge von Dreieckscheitelpunkten, sodass sie vom System von vorne im Uhrzeigersinn durchlaufen werden. Mit anderen Worten: Wenn die Scheitelpunkte v0, v1, v2 sind, übergeben sie diese als als v0, v2, v1 an Direct3D.
-   Verwenden Sie die Ansichtsmatrix, um Raum um -1 in der Z-Richtung zu skalieren. Kehren Sie dazu das Vorzeichen der Elemente \_31, \_32, \_33 und \_34 der Matrix-Struktur um, die Sie für die Ansichtsmatrix verwenden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 




