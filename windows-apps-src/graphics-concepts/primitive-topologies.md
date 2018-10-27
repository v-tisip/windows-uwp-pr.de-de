---
title: Primitive Topologien
description: Direct3D unterstützt mehrere primitive Topologien, die definieren, wie Scheitelpunkte, z.B. Punktelisten, Zeilenlisten und Dreieckstrips von der Pipeline interpretiert und gerendert werden.
ms.assetid: 7AA5A4A2-0B7C-431D-B597-684D58C02BA5
keywords:
- Primitive Topologien
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d7456cd773196520e066062c664f5e3073941dfe
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5704441"
---
# <a name="primitive-topologies"></a><span data-ttu-id="77d26-104">Primitive Topologien</span><span class="sxs-lookup"><span data-stu-id="77d26-104">Primitive topologies</span></span>


<span data-ttu-id="77d26-105">Direct3D unterstützt mehrere primitive Topologien, die definieren, wie Scheitelpunkte, z.B. Punktelisten, Linienlisten und Dreieckstrips von der Pipeline interpretiert und gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="77d26-105">Direct3D supports several primitive topologies, which define how vertices are interpreted and rendered by the pipeline, such as point lists, line lists, and triangle strips.</span></span>

## <a name="span-idprimitivetypesspanspan-idprimitivetypesspanspan-idprimitivetypesspanbasic-primitive-topologies"></a><span data-ttu-id="77d26-106"><span id="Primitive_Types"></span><span id="primitive_types"></span><span id="PRIMITIVE_TYPES"></span>Grundlegende primitive Topologien</span><span class="sxs-lookup"><span data-stu-id="77d26-106"><span id="Primitive_Types"></span><span id="primitive_types"></span><span id="PRIMITIVE_TYPES"></span>Basic primitive topologies</span></span>


<span data-ttu-id="77d26-107">Die folgenden grundlegenden primitiven Topologien (bzw. Grundtypen) werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="77d26-107">The following basic primitive topologies (or primitive types) are supported:</span></span>

-   [<span data-ttu-id="77d26-108">Punktelisten</span><span class="sxs-lookup"><span data-stu-id="77d26-108">Point lists</span></span>](point-lists.md)
-   [<span data-ttu-id="77d26-109">Zeilenlisten</span><span class="sxs-lookup"><span data-stu-id="77d26-109">Line lists</span></span>](line-lists.md)
-   [<span data-ttu-id="77d26-110">Zeilenstrips</span><span class="sxs-lookup"><span data-stu-id="77d26-110">Line strips</span></span>](line-strips.md)
-   [<span data-ttu-id="77d26-111">Dreieckslisten</span><span class="sxs-lookup"><span data-stu-id="77d26-111">Triangle lists</span></span>](triangle-lists.md)
-   [<span data-ttu-id="77d26-112">Dreiecksstrips</span><span class="sxs-lookup"><span data-stu-id="77d26-112">Triangle strips</span></span>](triangle-strips.md)

<span data-ttu-id="77d26-113">Eine Visualisierung der einzelnen Grundtypen finden Sie im Diagramm weiter unten in diesem Thema unter [Wicklungsrichtung und führende Scheitelpunktpositionen](#winding-direction-and-leading-vertex-positions).</span><span class="sxs-lookup"><span data-stu-id="77d26-113">For a visualization of each primitive type, see the diagram later in this topic in [Winding direction and leading vertex positions](#winding-direction-and-leading-vertex-positions).</span></span>

<span data-ttu-id="77d26-114">Die [Eingabeassemblerphase (IA)](input-assembler-stage--ia-.md) liest Daten aus Vertex- und Indexpuffern, setzt die Daten in diesen Grundtypen zusammen und sendet die Daten dann an die verbleibenden Pipelinephasen.</span><span class="sxs-lookup"><span data-stu-id="77d26-114">The [Input Assembler (IA) stage](input-assembler-stage--ia-.md) reads data from vertex and index buffers, assembles the data into these primitives, and then sends the data to the remaining pipeline stages.</span></span>

## <a name="span-idprimitiveadjacencyspanspan-idprimitiveadjacencyspanspan-idprimitiveadjacencyspanprimitive-adjacency"></a><span data-ttu-id="77d26-115"><span id="Primitive_Adjacency"></span><span id="primitive_adjacency"></span><span id="PRIMITIVE_ADJACENCY"></span>Grundtypen mit angrenzenden Daten</span><span class="sxs-lookup"><span data-stu-id="77d26-115"><span id="Primitive_Adjacency"></span><span id="primitive_adjacency"></span><span id="PRIMITIVE_ADJACENCY"></span>Primitive adjacency</span></span>


<span data-ttu-id="77d26-116">Alle Direct3D-Grundtypen (mit Ausnahme der Punkteliste) sind in zwei Versionen verfügbar: einem Grundtyp mit angrenzenden Daten und einen Grundtyp ohne angrenzende Daten.</span><span class="sxs-lookup"><span data-stu-id="77d26-116">All Direct3D primitive types (except the point list) are available in two versions: one primitive type with adjacency and one primitive type without adjacency.</span></span> <span data-ttu-id="77d26-117">Grundtypen mit angrenzenden Daten enthalten einige der umgebenden Scheitelpunkte, während Grundtypen ohne angrenzende Daten nur die Scheitelpunkte des Zielgrundtyps enthalten.</span><span class="sxs-lookup"><span data-stu-id="77d26-117">Primitives with adjacency contain some of the surrounding vertices, while primitives without adjacency contain only the vertices of the target primitive.</span></span> <span data-ttu-id="77d26-118">Beispielsweise ist für den Grundtyp „Zeilenliste“ ein entsprechender Grundtyp vorhanden, der angrenzende Daten umfasst.</span><span class="sxs-lookup"><span data-stu-id="77d26-118">For example, the line list primitive has a corresponding line list primitive that includes adjacency.</span></span>

<span data-ttu-id="77d26-119">Grundtypen mit angrenzenden Daten stellen weitere Informationen über die Geometrie bereit und können nur über einen Geometrieshader angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="77d26-119">Adjacent primitives are intended to provide more information about your geometry and are only visible through a geometry shader.</span></span> <span data-ttu-id="77d26-120">Angrenzende Daten eignen sich für Geometrieshader, die Silhouettenerkennung, Schattenvolumenextrusion usw. verwenden.</span><span class="sxs-lookup"><span data-stu-id="77d26-120">Adjacency is useful for geometry shaders that use silhouette detection, shadow volume extrusion, and so on.</span></span>

<span data-ttu-id="77d26-121">Beispiel: Sie möchten eine Dreiecksliste mit angrenzenden Daten zeichnen.</span><span class="sxs-lookup"><span data-stu-id="77d26-121">For example, suppose you want to draw a triangle list with adjacency.</span></span> <span data-ttu-id="77d26-122">Eine Dreiecksliste, die 36 Scheitelpunkte (mit angrenzenden Daten) enthält, ergibt 6 abgeschlossene Grundtypen.</span><span class="sxs-lookup"><span data-stu-id="77d26-122">A triangle list that contains 36 vertices (with adjacency) will yield 6 completed primitives.</span></span> <span data-ttu-id="77d26-123">Grundtypen mit angrenzenden Daten (außer Zeilenstrips) enthalten genau doppelt so viele Scheitelpunkte wie der entsprechende Grundtyp ohne angrenzende Daten, wobei jeder zusätzliche Scheitelpunkt ein angrenzender Scheitelpunkt ist.</span><span class="sxs-lookup"><span data-stu-id="77d26-123">Primitives with adjacency (except line strips) contain exactly twice as many vertices as the equivalent primitive without adjacency, where each additional vertex is an adjacent vertex.</span></span>

## <a name="span-idwindingdirectionandleadingvertexpositionsspanspan-idwindingdirectionandleadingvertexpositionsspanspan-idwindingdirectionandleadingvertexpositionsspanspan-idwinding-direction-and-leading-vertex-positionsspanwinding-direction-and-leading-vertex-positions"></a><span data-ttu-id="77d26-124"><span id="Winding_Direction_and_Leading_Vertex_Positions"></span><span id="winding_direction_and_leading_vertex_positions"></span><span id="WINDING_DIRECTION_AND_LEADING_VERTEX_POSITIONS"></span><span id="winding-direction-and-leading-vertex-positions"></span>Wicklungsrichtung und führende Scheitelpunktpositionen</span><span class="sxs-lookup"><span data-stu-id="77d26-124"><span id="Winding_Direction_and_Leading_Vertex_Positions"></span><span id="winding_direction_and_leading_vertex_positions"></span><span id="WINDING_DIRECTION_AND_LEADING_VERTEX_POSITIONS"></span><span id="winding-direction-and-leading-vertex-positions"></span>Winding direction and leading vertex positions</span></span>


<span data-ttu-id="77d26-125">Wie in der folgenden Abbildunggezeigt, ist ein führender Scheitelpunkt der nicht erste nicht angrenzende Scheitelpunkt in einen Grundtyp.</span><span class="sxs-lookup"><span data-stu-id="77d26-125">As shown in the following illustration, a leading vertex is the first non-adjacent vertex in a primitive.</span></span> <span data-ttu-id="77d26-126">Für einen Grundtyp können mehrere führende Scheitelpunkte definiert sein, vorausgesetzt, jeder wird für einen anderen Grundtyp verwendet.</span><span class="sxs-lookup"><span data-stu-id="77d26-126">A primitive type can have multiple leading vertices defined, as long as each one is used for a different primitive.</span></span>

-   <span data-ttu-id="77d26-127">Für einen Dreiecksstrip mit angrenzenden Daten sind die führenden Scheitelpunkte 0, 2, 4, 6 usw.</span><span class="sxs-lookup"><span data-stu-id="77d26-127">For a triangle strip with adjacency, the leading vertices are 0, 2, 4, 6, and so on.</span></span>
-   <span data-ttu-id="77d26-128">Für einen Zeilenstrip mit angrenzenden Daten sind die führenden Scheitelpunkte 1, 2, 3 usw.</span><span class="sxs-lookup"><span data-stu-id="77d26-128">For a line strip with adjacency, the leading vertices are 1, 2, 3, and so on.</span></span>
-   <span data-ttu-id="77d26-129">Andererseits hat ein Grundtyp mit angrenzenden Daten keinen führenden Scheitelpunkt.</span><span class="sxs-lookup"><span data-stu-id="77d26-129">An adjacent primitive, on the other hand, has no leading vertex.</span></span>

<span data-ttu-id="77d26-130">Die folgende Abbildungzeigt die Scheitelpunktanordnung für alle Grundtypen, die der Eingabeassembler erzeugen kann.</span><span class="sxs-lookup"><span data-stu-id="77d26-130">The following illustration shows the vertex ordering for all of the primitive types that the input assembler can produce.</span></span>

![Diagramm der Scheitelpunktanordnungen für Grundtypen](images/d3d10-primitive-topologies.png)

<span data-ttu-id="77d26-132">In der folgenden Tabelle werden die Symbole aus der obigen Abbildungbeschrieben.</span><span class="sxs-lookup"><span data-stu-id="77d26-132">The symbols in the preceding illustration are described in the following table.</span></span>

| <span data-ttu-id="77d26-133">Symbol</span><span class="sxs-lookup"><span data-stu-id="77d26-133">Symbol</span></span>                                                                                   | <span data-ttu-id="77d26-134">Name</span><span class="sxs-lookup"><span data-stu-id="77d26-134">Name</span></span>              | <span data-ttu-id="77d26-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77d26-135">Description</span></span>                                                                         |
|------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|
| ![Symbol für einen Scheitelpunkt](images/d3d10-primitive-topologies-vertex.png)                     | <span data-ttu-id="77d26-137">Scheitelpunkt</span><span class="sxs-lookup"><span data-stu-id="77d26-137">Vertex</span></span>            | <span data-ttu-id="77d26-138">Ein Punkt im 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="77d26-138">A point in 3D space.</span></span>                                                                |
| ![Symbol für Wicklungsrichtung](images/d3d10-primitive-topologies-winding-direction.png) | <span data-ttu-id="77d26-140">Wicklungsrichtung</span><span class="sxs-lookup"><span data-stu-id="77d26-140">Winding Direction</span></span> | <span data-ttu-id="77d26-141">Die Scheitelpunktanordnung beim Zusammensetzen eines Grundtyps.</span><span class="sxs-lookup"><span data-stu-id="77d26-141">The vertex order when assembling a primitive.</span></span> <span data-ttu-id="77d26-142">Kann im Uhrzeigersinn oder gegen den Uhrzeigersinn verlaufen.</span><span class="sxs-lookup"><span data-stu-id="77d26-142">Can be clockwise or counterclockwise.</span></span> |
| ![Symbol für führenden Scheitelpunkt](images/d3d10-primitive-topologies-leading-vertex.png)       | <span data-ttu-id="77d26-144">Führender Scheitelpunkt</span><span class="sxs-lookup"><span data-stu-id="77d26-144">Leading Vertex</span></span>    | <span data-ttu-id="77d26-145">Der erste Scheitelpunkt ohne angrenzende Daten in einem Grundtyp, der Daten pro Konstante enthält.</span><span class="sxs-lookup"><span data-stu-id="77d26-145">The first non-adjacent vertex in a primitive that contains per-constant data.</span></span>       |

 

## <a name="span-idgeneratingmultiplestripsspanspan-idgeneratingmultiplestripsspanspan-idgeneratingmultiplestripsspangenerating-multiple-strips"></a><span data-ttu-id="77d26-146"><span id="Generating_Multiple_Strips"></span><span id="generating_multiple_strips"></span><span id="GENERATING_MULTIPLE_STRIPS"></span>Generieren mehrerer Strips</span><span class="sxs-lookup"><span data-stu-id="77d26-146"><span id="Generating_Multiple_Strips"></span><span id="generating_multiple_strips"></span><span id="GENERATING_MULTIPLE_STRIPS"></span>Generating multiple strips</span></span>


<span data-ttu-id="77d26-147">Mehrere Strips lassen sich mittels Schneiden von Strips generieren.</span><span class="sxs-lookup"><span data-stu-id="77d26-147">You can generate multiple strips through strip cutting.</span></span> <span data-ttu-id="77d26-148">Sie können einen Stripschnitt durchführen, indem Sie ausdrücklich die HSLS-Funktion [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) aufrufen, oder indem Sie einen besonderen Indexwert in den Indexpuffer einfügen.</span><span class="sxs-lookup"><span data-stu-id="77d26-148">You can perform a strip cut by explicitly calling the [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) HLSL function, or by inserting a special index value into the index buffer.</span></span> <span data-ttu-id="77d26-149">Dieser Wert ist-1, was 0xffffffff für 32-Bit-Indizes oder 0xffff für 16-Bit-Indizes entspricht.</span><span class="sxs-lookup"><span data-stu-id="77d26-149">This value is –1, which is 0xffffffff for 32-bit indices or 0xffff for 16-bit indices.</span></span>

<span data-ttu-id="77d26-150">Ein Index von -1 gibt ein explizites „Ausschneiden“ oder „Neustarten“ des aktuellen Strips an.</span><span class="sxs-lookup"><span data-stu-id="77d26-150">An index of –1 indicates an explicit 'cut' or 'restart' of the current strip.</span></span> <span data-ttu-id="77d26-151">Der vorherige Index schließt den vorherigen Grundtyp oder Strip ab, und der nächsten Index beginnt einen neuen Grundtyp oder Strip.</span><span class="sxs-lookup"><span data-stu-id="77d26-151">The previous index completes the previous primitive or strip and the next index starts a new primitive or strip.</span></span>

<span data-ttu-id="77d26-152">Weitere Informationen zum Generieren von mehreren Strips finden Sie unter [Geometryshaderphase (GS)](geometry-shader-stage--gs-.md).</span><span class="sxs-lookup"><span data-stu-id="77d26-152">For more info about generating multiple strips, see [Geometry Shader (GS) stage](geometry-shader-stage--gs-.md).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="77d26-153"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="77d26-153"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="77d26-154">Eingabeassemblerphase (IA)</span><span class="sxs-lookup"><span data-stu-id="77d26-154">Input-Assembler (IA) stage</span></span>](input-assembler-stage--ia-.md)

[<span data-ttu-id="77d26-155">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="77d26-155">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




