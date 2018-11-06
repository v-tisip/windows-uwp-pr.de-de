---
title: Koordinatensysteme und Geometrie
description: Für das Programmieren von Direct3D-Anwendungen muss der Anwender mit geometrischen 3D-Prinzipien vertraut sein. In diesem Abschnitt werden die wichtigsten geometrischen Konzepte für das Erstellen von 3D-Szenen eingeführt.
ms.assetid: E82EB0A9-0678-496B-96B3-8993BA580099
keywords:
- Koordinatensysteme und Geometrie
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ce3b1ebfc2f18a06ff4fa960c91749f61f5011d9
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6041610"
---
# <a name="coordinate-systems-and-geometry"></a><span data-ttu-id="5aa0a-105">Koordinatensysteme und Geometrie</span><span class="sxs-lookup"><span data-stu-id="5aa0a-105">Coordinate systems and geometry</span></span>


<span data-ttu-id="5aa0a-106">Für das Programmieren von Direct3D-Anwendungen muss der Anwender mit geometrischen 3D-Prinzipien vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-106">Programming Direct3D applications requires a working familiarity with 3D geometric principles.</span></span> <span data-ttu-id="5aa0a-107">In diesem Abschnitt werden die wichtigsten geometrischen Konzepte für das Erstellen von 3D-Szenen eingeführt.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-107">This section introduces the most important geometric concepts for creating 3D scenes.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="5aa0a-108"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="5aa0a-108"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5aa0a-109">Thema</span><span class="sxs-lookup"><span data-stu-id="5aa0a-109">Topic</span></span></th>
<th align="left"><span data-ttu-id="5aa0a-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5aa0a-110">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="coordinate-systems.md"><span data-ttu-id="5aa0a-111">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="5aa0a-111">Coordinate systems</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-112">Normalerweise verwenden 3D-Grafikanwendungen einen von zwei Typen an kartesischen Koordinatensystemen: rechts- oder linkshändig.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-112">Typically 3D graphics applications use one of two types of Cartesian coordinate systems: left-handed or right-handed.</span></span> <span data-ttu-id="5aa0a-113">In beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-113">In both coordinate systems, the positive x-axis points to the right, and the positive y-axis points up.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="primitives.md"><span data-ttu-id="5aa0a-114">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="5aa0a-114">Primitives</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-115">Ein 3D- <em>Grundtyp</em> ist eine Sammlung von Scheitelpunkten, die eine 3D Einheit bilden.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-115">A 3D <em>primitive</em> is a collection of vertices that form a single 3D entity.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="face-and-vertex-normal-vectors.md"><span data-ttu-id="5aa0a-116">Seiten- und Scheitelnormalenvektoren</span><span class="sxs-lookup"><span data-stu-id="5aa0a-116">Face and vertex normal vectors</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-117">Jede Fläche in einem Gitter verfügt über einen normalen Einheitsvektor im rechten Winkel.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-117">Each face in a mesh has a perpendicular unit normal vector.</span></span> <span data-ttu-id="5aa0a-118">Die Richtung des Vektors wird von der Reihenfolge bestimmt, in der die Scheitelpunkte definiert sind und ist abhängig davon, ob das Koordinatensystem rechts - oder linkshändig ist.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-118">The vector's direction is determined by the order in which the vertices are defined and by whether the coordinate system is right- or left-handed.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="rectangles.md"><span data-ttu-id="5aa0a-119">Rechtecke</span><span class="sxs-lookup"><span data-stu-id="5aa0a-119">Rectangles</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-120">In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm als umgebende Rechtecke bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-120">Throughout Direct3D and Windows programming, objects on the screen are referred to in terms of bounding rectangles.</span></span> <span data-ttu-id="5aa0a-121">Die Seiten des umgebenden Rechtecks sind immer parallel zu den Seiten des Bildschirms, damit das Rechteck durch zwei Punkte, der oberen linken Ecke und der unteren rechten Ecke, definiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-121">The sides of a bounding rectangle are always parallel to the sides of the screen, so the rectangle can be described by two points, the upper-left corner and lower-right corner.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="triangle-interpolation.md"><span data-ttu-id="5aa0a-122">Dreiecksinterpolation</span><span class="sxs-lookup"><span data-stu-id="5aa0a-122">Triangle interpolation</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-123">Während des Renderns interpoliert die Pipeline Vertexdaten bei jedem Dreieck.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-123">During rendering, the pipeline interpolates vertex data across each triangle.</span></span> <span data-ttu-id="5aa0a-124">Vertexdaten können eine Vielzahl von Daten sein und enthalten (sind aber nicht beschränkt auf): diffuse Farbe, Glanzfarbe, diffuse Alpha(Transparenz des Dreiecks), Glanzlicht Alpha und Nebelfaktor.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-124">Vertex data can be a broad variety of data and can include (but is not limited to): diffuse color, specular color, diffuse alpha (triangle opacity), specular alpha, and a fog factor.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="vectors--vertices--and-quaternions.md"><span data-ttu-id="5aa0a-125">Vektoren, Scheitelpunkte und Quaternionen</span><span class="sxs-lookup"><span data-stu-id="5aa0a-125">Vectors, vertices, and quaternions</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-126">In Direct3D beschreiben Scheitelpunkte die Position und Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-126">Throughout Direct3D, vertices describe position and orientation.</span></span> <span data-ttu-id="5aa0a-127">Jeder Scheitelpunkt in einen Grundtyp wird durch einen Vektor beschrieben, der die Positions-, Farb-, Texturkoordinaten angibt sowie durch einen normalen Vektor, der die Ausrichtung angibt.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-127">Each vertex in a primitive is described by a vector that gives its position, color, texture coordinates, and a normal vector that gives its orientation.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="transforms.md"><span data-ttu-id="5aa0a-128">Transformationen</span><span class="sxs-lookup"><span data-stu-id="5aa0a-128">Transforms</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-129">Der Teil von Direct3D, der die Geometrie über die Geometrie-Pipeline mit fester Funktion überträgt, ist die Transformationsengine.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-129">The part of Direct3D that pushes geometry through the fixed function geometry pipeline is the transform engine.</span></span> <span data-ttu-id="5aa0a-130">Es ermittelt das Modell und die Anzeige im Raum, projiziert Scheitelpunkte für die Anzeige auf den Bildschirm und beschneidet Scheitelpunkte im Viewport.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-130">It locates the model and viewer in the world, projects vertices for display on the screen, and clips vertices to the viewport.</span></span> <span data-ttu-id="5aa0a-131">Das Transformationsmodul führt ebenfalls Beleuchtungsberechnungen durch, um diffuse und Glanzlichtkomponenten bei jedem Scheitelpunkt zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-131">The transform engine also performs lighting computations to determine diffuse and specular components at each vertex.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="viewports-and-clipping.md"><span data-ttu-id="5aa0a-132">Ansichten und Zuschneiden</span><span class="sxs-lookup"><span data-stu-id="5aa0a-132">Viewports and clipping</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5aa0a-133">Ein <em>Viewport</em> ist ein zweidimensionales (2D) Rechteck, auf das eine 3D-Szene projiziert wird.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-133">A <em>viewport</em> is a two-dimensional (2D) rectangle into which a 3D scene is projected.</span></span> <span data-ttu-id="5aa0a-134">In Direct3D ist das Rechteck eine Koordinate innerhalb einer Direct3D-Oberfläche, die das System als Renderziel verwendet.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-134">In Direct3D, the rectangle exists as coordinates within a Direct3D surface that the system uses as a rendering target.</span></span> <span data-ttu-id="5aa0a-135">Die Projektionstransformation konvertiert Scheitelpunkte in das Koordinatensystem, das vom Viewport verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-135">The projection transformation converts vertices into the coordinate system used for the viewport.</span></span> <span data-ttu-id="5aa0a-136">Ein Viewport wird auch verwendet, um den Bereich der Tiefenwerte auf einer Renderzieloberfläche festzulegen, auf die eine Szene (in der Regel zwischen 0,0 und 1,0) gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="5aa0a-136">A viewport is also used to specify the range of depth values on a render-target surface into which a scene will be rendered (usually 0.0 to 1.0).</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="5aa0a-137"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5aa0a-137"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="5aa0a-138">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="5aa0a-138">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




