---
title: Direct3D-Grafiken Glossar
description: Definiert die Grafiken Begriffe, die von Microsoft Direct3D verwendet.
ms.assetid: c3850a92-4d05-4f72-bf0f-6a0c79e841eb
keywords:
- Direct3D-Grafiken Glossar
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 0e325494cefeab4cf3ed40939f5b24de5e921b68
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6466882"
---
# <a name="direct3d-graphics-glossary"></a><span data-ttu-id="c12ab-104">Direct3D-Grafiken Glossar</span><span class="sxs-lookup"><span data-stu-id="c12ab-104">Direct3D graphics glossary</span></span>


<span data-ttu-id="c12ab-105">Microsoft Direct3D-Grafiken Begriffe definiert.</span><span class="sxs-lookup"><span data-stu-id="c12ab-105">Defines Microsoft Direct3D graphics terms.</span></span> <span data-ttu-id="c12ab-106">In diesem Glossar definiert, auf ein high-Level, allgemeine 3D Computer Grafiken Begriffe, die in der Direct3D-Spiel und app-Entwicklung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c12ab-106">This glossary defines, at a high level, general 3D computer graphics terms that are used in Direct3D game and app development.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="c12ab-107"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="c12ab-107"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="c12ab-108">Thema</span><span class="sxs-lookup"><span data-stu-id="c12ab-108">Topic</span></span></th>
<th align="left"><span data-ttu-id="c12ab-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c12ab-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="coordinate-systems-and-geometry.md"><span data-ttu-id="c12ab-110">Koordinatensystem und Geometrie</span><span class="sxs-lookup"><span data-stu-id="c12ab-110">Coordinate systems and geometry</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-111">Für das Programmieren von Direct3D-Anwendungen muss der Anwender mit geometrischen 3D-Prinzipien vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="c12ab-111">Programming Direct3D applications requires a working familiarity with 3D geometric principles.</span></span> <span data-ttu-id="c12ab-112">Dieser Abschnitt stellt die wichtigsten geometrischen Konzepte zum Erstellen von 3D-Szenen vor.</span><span class="sxs-lookup"><span data-stu-id="c12ab-112">This section introduces the most important geometric concepts for creating 3D scenes.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="vertex-and-index-buffers.md"><span data-ttu-id="c12ab-113">Vertex- und Indexpuffer</span><span class="sxs-lookup"><span data-stu-id="c12ab-113">Vertex and index buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-114"><em>Scheitelpunktpuffer</em> sind Speicherpuffer, die Scheitelpunktdaten enthalten. Scheitelpunkte in einem Scheitelpunktpuffer werden verarbeitet, um Transformation, Beleuchtung und Zuschneiden auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c12ab-114"><em>Vertex buffers</em> are memory buffers that contain vertex data; vertices in a vertex buffer are processed to perform transformation, lighting, and clipping.</span></span> <span data-ttu-id="c12ab-115"><em>Indexpuffer</em> sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Vertexpuffer darstellen, und zum Rendern von Grundtypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c12ab-115"><em>Index buffers</em> are memory buffers that contain index data, which are integer offsets into vertex buffers, used to render primitives.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="devices.md"><span data-ttu-id="c12ab-116">Geräte</span><span class="sxs-lookup"><span data-stu-id="c12ab-116">Devices</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-117">Ein Direct3D-Gerät ist die Komponente zum Rendern von Direct3D.</span><span class="sxs-lookup"><span data-stu-id="c12ab-117">A Direct3D device is the rendering component of Direct3D.</span></span> <span data-ttu-id="c12ab-118">Ein Gerät kapselt und speichert den Renderstatus, führt Transformationen und Beleuchtungsvorgänge aus, und rastert ein Bild zu einer Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="c12ab-118">A device encapsulates and stores the rendering state, performs transformations and lighting operations, and rasterizes an image to a surface.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="lights-and-materials.md"><span data-ttu-id="c12ab-119">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="c12ab-119">Lighting</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-120">Lichter werden verwendet, um Objekte in einer Szene zu beleuchten.</span><span class="sxs-lookup"><span data-stu-id="c12ab-120">Lights are used to illuminate objects in a scene.</span></span> <span data-ttu-id="c12ab-121">Die Farbe jedes Objektscheitelpunkts basiert auf der aktuellen Texturzuordnung, Scheitelpunktfarben und Lichtquellen.</span><span class="sxs-lookup"><span data-stu-id="c12ab-121">The color of each object vertex is based on the current texture map, vertex colors, and light sources.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="depth-and-stencil-buffers.md"><span data-ttu-id="c12ab-122">Tiefen- und Schablonenpuffer</span><span class="sxs-lookup"><span data-stu-id="c12ab-122">Depth and stencil buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-123">Ein <em>Tiefenpuffer</em> speichert Tiefeninformationen. Diese steuern, welche Bereiche von Polygonen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="c12ab-123">A <em>depth buffer</em> stores depth information to control which areas of polygons are rendered rather than hidden from view.</span></span> <span data-ttu-id="c12ab-124">Ein <em>Schablonenpuffer</em> wird Maskieren von Pixeln in einem Bild verwendet. So können Spezialeffekte erstellt werden (z. B. Stanzeffekte; Decaling; Transparenzen, Ausblenden und Verwischen; Außenlinien und Silhouetten und zweiseitige Schablonen).</span><span class="sxs-lookup"><span data-stu-id="c12ab-124">A <em>stencil buffer</em> is used to mask pixels in an image, to produce special effects, including compositing; decaling; dissolves, fades, and swipes; outlines and silhouettes; and two-sided stencil.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="textures.md"><span data-ttu-id="c12ab-125">Texturen</span><span class="sxs-lookup"><span data-stu-id="c12ab-125">Textures</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-126">Texturen sind ein leistungsstarkes Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="c12ab-126">Textures are a powerful tool in creating realism in computer-generated 3D images.</span></span> <span data-ttu-id="c12ab-127">Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern einfach auf erweiterte Texturtechniken zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="c12ab-127">Direct3D supports an extensive texturing feature set, providing developers with easy access to advanced texturing techniques.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="graphics-pipeline.md"><span data-ttu-id="c12ab-128">Grafik-Pipeline</span><span class="sxs-lookup"><span data-stu-id="c12ab-128">Graphics pipeline</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-129">Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele.</span><span class="sxs-lookup"><span data-stu-id="c12ab-129">The Direct3D graphics pipeline is designed for generating graphics for realtime gaming applications.</span></span> <span data-ttu-id="c12ab-130">Datenflüsse vom Eingang zum Ausgang durch jede konfigurierbare oder programmierbare Phase</span><span class="sxs-lookup"><span data-stu-id="c12ab-130">Data flows from input to output through each of the configurable or programmable stages.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="views.md"><span data-ttu-id="c12ab-131">Ansichten</span><span class="sxs-lookup"><span data-stu-id="c12ab-131">Views</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-132">Der Begriff &quot;Ansicht&quot; wird für &quot;Daten im erforderlichen Format&quot; verwendet.</span><span class="sxs-lookup"><span data-stu-id="c12ab-132">The term &quot;view&quot; is used to mean &quot;data in the required format&quot;.</span></span> <span data-ttu-id="c12ab-133">Eine Konstantenpufferansicht (CBV) beispielweise, sind ordnungsgemäß formatierte, konstante Pufferdaten.</span><span class="sxs-lookup"><span data-stu-id="c12ab-133">For example, a Constant Buffer View (CBV) would be constant buffer data correctly formatted.</span></span> <span data-ttu-id="c12ab-134">Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten.</span><span class="sxs-lookup"><span data-stu-id="c12ab-134">This section describes the most common and useful views.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="compute-pipeline.md"><span data-ttu-id="c12ab-135">Berechnungs-Pipeline</span><span class="sxs-lookup"><span data-stu-id="c12ab-135">Compute pipeline</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-136">Die Direct3D-Berechnungs-Pipeline wurde entwickelt, um Berechnungen zu erledigen, die meist parallel mit der Grafik-Pipeline ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="c12ab-136">The Direct3D compute pipeline is designed to handle calculations that can be done mostly in parallel with the graphics pipeline.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="resources.md"><span data-ttu-id="c12ab-137">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c12ab-137">Resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-138">Eine Ressource ist ein Bereich im Speicher, auf den die Direct3D-Pipeline zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="c12ab-138">A resource is an area in memory that can be accessed by the Direct3D pipeline.</span></span> <span data-ttu-id="c12ab-139">Damit die Pipeline effizient auf den Speicher zugreifen kann, müssen für die Pipeline bereitgestellte Daten (wie z.B. Input-Geometrie, Shader-Ressourcen und Texturen) in einer Ressource gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="c12ab-139">In order for the pipeline to access memory efficiently, data that is provided to the pipeline (such as input geometry, shader resources, and textures) must be stored in a resource.</span></span> <span data-ttu-id="c12ab-140">Es gibt zwei Arten von Ressourcen, aus denen alle Direct3D-Ressourcen abgeleitet sind: ein Puffer oder eine Textur.</span><span class="sxs-lookup"><span data-stu-id="c12ab-140">There are two types of resources from which all Direct3D resources derive: a buffer or a texture.</span></span> <span data-ttu-id="c12ab-141">Bis zu 128 Ressourcen können für jede Pipeline-Phase aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="c12ab-141">Up to 128 resources can be active for each pipeline stage.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="streaming-resources.md"><span data-ttu-id="c12ab-142">Streaming-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c12ab-142">Streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-143"><em>Streamingressourcen</em> sind große logische Ressourcen, die wenig physischen Speicher belegen..</span><span class="sxs-lookup"><span data-stu-id="c12ab-143"><em>Streaming resources</em> are large logical resources that use small amounts of physical memory.</span></span> <span data-ttu-id="c12ab-144">Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt.</span><span class="sxs-lookup"><span data-stu-id="c12ab-144">Instead of passing an entire large resource, small parts of the resource are streamed as needed.</span></span> <span data-ttu-id="c12ab-145">Streaming-Ressourcen wurden vorher als <em>unterteilte Ressourcen</em> bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c12ab-145">Streaming resources were previously called <em>tiled resources</em>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="appendix.md"><span data-ttu-id="c12ab-146">Anhänge</span><span class="sxs-lookup"><span data-stu-id="c12ab-146">Appendices</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="c12ab-147">Diese Abschnitte enthalten tiefergehende technische Details.</span><span class="sxs-lookup"><span data-stu-id="c12ab-147">These sections provide in-depth technical details.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 
