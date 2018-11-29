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
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7983306"
---
# <a name="coordinate-systems"></a><span data-ttu-id="502aa-105">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="502aa-105">Coordinate systems</span></span>


<span data-ttu-id="502aa-106">Normalerweise verwenden 3D-Grafikanwendungen einen von zwei Typen an kartesischen Koordinatensystemen: rechts- oder linkshändig.</span><span class="sxs-lookup"><span data-stu-id="502aa-106">Typically 3D graphics applications use one of two types of Cartesian coordinate systems: left-handed or right-handed.</span></span> <span data-ttu-id="502aa-107">In beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben.</span><span class="sxs-lookup"><span data-stu-id="502aa-107">In both coordinate systems, the positive x-axis points to the right, and the positive y-axis points up.</span></span>

## <a name="span-idleftandrighthandedcoordinatesspanspan-idleftandrighthandedcoordinatesspanspan-idleftandrighthandedcoordinatesspanleft-and-right-handed-coordinates"></a><span data-ttu-id="502aa-108"><span id="Left_and_right_handed_coordinates"></span><span id="left_and_right_handed_coordinates"></span><span id="LEFT_AND_RIGHT_HANDED_COORDINATES"></span>Rechts- oder linkshändige Koordinaten</span><span class="sxs-lookup"><span data-stu-id="502aa-108"><span id="Left_and_right_handed_coordinates"></span><span id="left_and_right_handed_coordinates"></span><span id="LEFT_AND_RIGHT_HANDED_COORDINATES"></span>Left and right handed coordinates</span></span>


<span data-ttu-id="502aa-109">Sie können sich an die Richtung der positiven X-Achse dadurch erinnern, indem Sie Ihre Finger von der linken oder rechten Hand für die positive X-Richtung ausstrecken und für die positive Y-Richtung zusammen krümmen.</span><span class="sxs-lookup"><span data-stu-id="502aa-109">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x-direction and curling them into the positive y-direction.</span></span> <span data-ttu-id="502aa-110">Die Richtung, in die der Daumen zeigt, entweder auf Sie zu oder von Ihnen weg, ist die Richtung der positiven Z-Achse für das Koordinatensystem.</span><span class="sxs-lookup"><span data-stu-id="502aa-110">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="502aa-111">Die folgende Abbildung zeigt diese zwei Koordinatensysteme.</span><span class="sxs-lookup"><span data-stu-id="502aa-111">The following illustration shows these two coordinate systems.</span></span>

![Abbildung des linkshändigen und rechtshändigen kartesischen Koordinatensystems](images/leftrght.png)

<span data-ttu-id="502aa-113">Direct3D verwendet ein linkshändiges Koordinatensystem.</span><span class="sxs-lookup"><span data-stu-id="502aa-113">Direct3D uses a left-handed coordinate system.</span></span> <span data-ttu-id="502aa-114">Obwohl links- und rechtshändige Koordinaten die am häufigsten verwendeten Systeme sind, gibt es eine Vielzahl anderer Koordinatensysteme bei 3D-Software.</span><span class="sxs-lookup"><span data-stu-id="502aa-114">Although left-handed and right-handed coordinates are the most common systems, there is a variety of other coordinate systems used in 3D software.</span></span> <span data-ttu-id="502aa-115">Es ist für 3D-Modellierungs-Apps beispielsweise nicht ungewöhnlich, ein Koordinatensystem zu verwenden, bei dem die Y-Achse auf den Anwender zu oder von ihm hinweg zeigt und die Z-Achse nach oben zeigt.</span><span class="sxs-lookup"><span data-stu-id="502aa-115">For example, it is not unusual for 3D modeling applications to use a coordinate system in which the y-axis points toward or away from the viewer, and the z-axis points up.</span></span>

## <a name="span-idverticesandvectorsspanspan-idverticesandvectorsspanspan-idverticesandvectorsspanvertices-and-vectors"></a><span data-ttu-id="502aa-116"><span id="Vertices_and_vectors"></span><span id="vertices_and_vectors"></span><span id="VERTICES_AND_VECTORS"></span>Scheitelpunkte und Vektoren</span><span class="sxs-lookup"><span data-stu-id="502aa-116"><span id="Vertices_and_vectors"></span><span id="vertices_and_vectors"></span><span id="VERTICES_AND_VECTORS"></span>Vertices and vectors</span></span>


<span data-ttu-id="502aa-117">Je nach Koordinatensystem kann eine X-, Y- und Z-Koordinate einen Punkt im Raum definieren (einen „Scheitelpunkt”) oder eine 3D-Richtung (einen „Vektor”) definieren.</span><span class="sxs-lookup"><span data-stu-id="502aa-117">Given the coordinate system, an x, y and z coordinate can define a point in space (a "vertex"), or a 3D direction (a "vector").</span></span>

<span data-ttu-id="502aa-118">Zum Definieren von Linien und Formen kann eine Sammlung von Scheitelpunkten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="502aa-118">A collection of vertices can be used to define lines and shapes.</span></span> <span data-ttu-id="502aa-119">Die einfachsten, von Scheitelpunkten definierbaren Objekte heißen [Grundtypen](primitives.md) und ein komplexeres, durch eine Reihe von Grundtypen definiertes Objekt heißt „Gitter”.</span><span class="sxs-lookup"><span data-stu-id="502aa-119">The simplest objects definable by vertices are called [Primitives](primitives.md), and a more complex object defined by a set of primitives is called a "mesh."</span></span>

<span data-ttu-id="502aa-120">Die grundlegenden Operationen auf in einem 3D-Koordinatensystem definierten Gittern sind Übersetzung, Drehung und Skalierung.</span><span class="sxs-lookup"><span data-stu-id="502aa-120">The essential operations performed on meshes defined in a 3D coordinate system are translation, rotation, and scaling.</span></span> <span data-ttu-id="502aa-121">Sie können diese einfachen Transformationen kombinieren, um eine Transformationsmatrix zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="502aa-121">You can combine these basic transformations to create a transform matrix.</span></span> <span data-ttu-id="502aa-122">Weitere Informationen finden Sie unter [Transformationen](transforms.md).</span><span class="sxs-lookup"><span data-stu-id="502aa-122">For details, see [Transforms](transforms.md).</span></span>

<span data-ttu-id="502aa-123">Wenn Sie diese Vorgänge kombinieren, sind die Ergebnisse nicht kommutativ. Die Reihenfolge, in der Sie Matrizen multiplizieren, ist wichtig.</span><span class="sxs-lookup"><span data-stu-id="502aa-123">When you combine these operations, the results are not commutative; the order in which you multiply matrices is important.</span></span>

## <a name="span-idportingfromaright-handedcoordinatesystemspanspan-idportingfromaright-handedcoordinatesystemspanspan-idportingfromaright-handedcoordinatesystemspanporting-from-a-right-handed-coordinate-system"></a><span data-ttu-id="502aa-124"><span id="Porting_from_a_right-handed_coordinate_system"></span><span id="porting_from_a_right-handed_coordinate_system"></span><span id="PORTING_FROM_A_RIGHT-HANDED_COORDINATE_SYSTEM"></span>Portieren von einem rechtshändigen Koordinatensystem</span><span class="sxs-lookup"><span data-stu-id="502aa-124"><span id="Porting_from_a_right-handed_coordinate_system"></span><span id="porting_from_a_right-handed_coordinate_system"></span><span id="PORTING_FROM_A_RIGHT-HANDED_COORDINATE_SYSTEM"></span>Porting from a right-handed coordinate system</span></span>


<span data-ttu-id="502aa-125">Wenn Sie eine auf einem rechtshändigen Koordinatensystem basierende Anwendung portieren, müssen Sie zwei Änderungen an den auf Direct3D übergebenen Daten vornehmen:</span><span class="sxs-lookup"><span data-stu-id="502aa-125">If you are porting an application that is based on a right-handed coordinate system, you must make two changes to the data passed to Direct3D:</span></span>

-   <span data-ttu-id="502aa-126">Spiegeln Sie die Reihenfolge von Dreieckscheitelpunkten, sodass sie vom System von vorne im Uhrzeigersinn durchlaufen werden.</span><span class="sxs-lookup"><span data-stu-id="502aa-126">Flip the order of triangle vertices so that the system traverses them clockwise from the front.</span></span> <span data-ttu-id="502aa-127">Mit anderen Worten: Wenn die Scheitelpunkte v0, v1, v2 sind, übergeben sie diese als als v0, v2, v1 an Direct3D.</span><span class="sxs-lookup"><span data-stu-id="502aa-127">In other words, if the vertices are v0, v1, v2, pass them to Direct3D as v0, v2, v1.</span></span>
-   <span data-ttu-id="502aa-128">Verwenden Sie die Ansichtsmatrix, um Raum um -1 in der Z-Richtung zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="502aa-128">Use the view matrix to scale world space by -1 in the z-direction.</span></span> <span data-ttu-id="502aa-129">Kehren Sie dazu das Vorzeichen der Elemente \_31, \_32, \_33 und \_34 der Matrix-Struktur um, die Sie für die Ansichtsmatrix verwenden.</span><span class="sxs-lookup"><span data-stu-id="502aa-129">To do this, flip the sign of the \_31, \_32, \_33, and \_34 member of the matrix structure that you use for your view matrix.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="502aa-130"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="502aa-130"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="502aa-131">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="502aa-131">Coordinate systems and geometry</span></span>](coordinate-systems-and-geometry.md)

 

 




