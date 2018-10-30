---
title: Eingabeassemblerphase (IA)
description: Die Eingabeassemblerphase (IA) liefert Grundtypen und angrenzende Daten an die Pipeline, wie beispielsweise Dreiecke, Linien und Punkte mit Semantik-IDs, damit die Shader effizienter arbeiten können, da die Verarbeitung von noch nicht verarbeiteten Grundtypen reduziert wird.
ms.assetid: AF1DC611-C872-47F1-BF1A-92C68C8903E6
keywords:
- Eingabeassemblerphase (IA)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: def755f868c7ea30679f19877cec84b20faa44f5
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5765866"
---
# <a name="input-assembler-ia-stage"></a><span data-ttu-id="6ec6a-104">Eingabeassemblerphase (IA)</span><span class="sxs-lookup"><span data-stu-id="6ec6a-104">Input Assembler (IA) stage</span></span>


<span data-ttu-id="6ec6a-105">Die Eingabeassemblerphase (IA) liefert Grundtypen und angrenzende Daten an die Pipeline, wie beispielsweise Dreiecke, Linien und Punkte mit Semantik-IDs, damit die Shader effizienter arbeiten können, da die Verarbeitung von noch nicht verarbeiteten Grundtypen reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-105">The Input Assembler (IA) stage supplies primitive and adjacency data to the pipeline, such as triangles, lines and points, including semantics IDs to help make shaders more efficient by reducing processing to primitives that haven't already been processed.</span></span>

## <a name="span-idpurpose-and-usesspanspan-idpurpose-and-usesspanspan-idpurpose-and-usesspanpurpose-and-uses"></a><span data-ttu-id="6ec6a-106"><span id="Purpose-and-uses"></span><span id="purpose-and-uses"></span><span id="PURPOSE-AND-USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="6ec6a-106"><span id="Purpose-and-uses"></span><span id="purpose-and-uses"></span><span id="PURPOSE-AND-USES"></span>Purpose and uses</span></span>


<span data-ttu-id="6ec6a-107">Die Eingabeassemblerphase (IA) dient dem Zweck, Grundtypendaten (Punkte, Linien und Dreiecke) aus den von Benutzer gefüllten Puffern zu lesen und die Daten zu Grundtypen zusammenzusetzen, die dann von den anderen Pipeline-Phasen verwendet werden, und [systemgenerierte Werte](https://msdn.microsoft.com/library/windows/desktop/bb509647) anzuhängen, damit die Shader effizienter arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-107">The purpose of the Input Assembler (IA) stage is to read primitive data (points, lines and triangles) from user-filled buffers and assemble the data into primitives that will be used by the other pipeline stages, and to attach [system-generated values](https://msdn.microsoft.com/library/windows/desktop/bb509647) to help make shaders more efficient.</span></span> <span data-ttu-id="6ec6a-108">Bei systemgenerierten Werten handelt es sich um Textzeichenfolgen, die auch als Semantiken bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-108">System-generated values are text strings that are also called semantics.</span></span> <span data-ttu-id="6ec6a-109">Die programmierbaren Shader-Phasen werden aus einem herkömmlichen Shader-Kern konstruiert, der systemgenerierte Werte (wie Grundtyp-ID, Instanz-ID oder eine Scheitelpunkt-ID) verwendet, so dass die Shader-Phase die Verarbeitung auf diese Grundtypen, Instanzen und Scheitelpunkte reduzieren kann, die noch nicht verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-109">The programmable shader stages are constructed from a common shader core, which uses system-generated values (such as a primitive ID, an instance ID, or a vertex ID), so that the shader stage can reduce processing to only those primitives, instances, or vertices that have not already been processed.</span></span>

<span data-ttu-id="6ec6a-110">Eine IA-Phase kann Scheitelpunkte zu mehreren verschiedenen [Grundtypen](primitive-topologies.md) (wie Linienlisten, Dreieckstreifen oder Grundtypen mit angrenzenden Daten) zusammenstellen.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-110">The IA stage can assemble vertices into several different [primitive types](primitive-topologies.md) (such as line lists, triangle strips, or primitives with adjacency).</span></span> <span data-ttu-id="6ec6a-111">Grundtypen wie Dreiecklisten mit angrenzenden Daten und eine Linienliste mit angrenzenden Daten unterstützten die [Geometrieshaderphase (GS)](geometry-shader-stage--gs-.md).</span><span class="sxs-lookup"><span data-stu-id="6ec6a-111">Primitive types such as a triangle list with adjacency, and a line list with adjacency, support the [Geometry Shader (GS) stage](geometry-shader-stage--gs-.md).</span></span>

<span data-ttu-id="6ec6a-112">Angrenzende Informationen sind für die Anwendung nur in einem Geometrieshader sichtbar.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-112">Adjacency information is visible to an application only in a geometry shader.</span></span> <span data-ttu-id="6ec6a-113">Wenn beispielsweise ein Geometrieshader mit einem Dreieck mit angrenzenden Daten aufgerufen wurde, enthalten die Eingabedaten drei Scheitelpunkte für jedes Dreieck und drei Scheitelpunkte für angrenzende Daten pro Dreieck.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-113">If a geometry shader were invoked with a triangle including adjacency, for instance, the input data would contain 3 vertices for each triangle and 3 vertices for adjacency data per triangle.</span></span>

<span data-ttu-id="6ec6a-114">Wird die IA-Phase aufgefordert, die angrenzenden Daten auszugeben, müssen die Eingabedaten angrenzende Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-114">When the IA stage is requested to output adjacency data, the input data must include adjacency data.</span></span> <span data-ttu-id="6ec6a-115">Dazu muss möglicherweise ein Dummy-Scheitelpunkt bereitgestellt werden (der ein fehlerhaftes Dreieck darstellt) oder vielleicht durch Kennzeichnung eines der Scheitelpunktattribute, ob der Scheitelpunkt vorhanden ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-115">This may require providing a dummy vertex (forming a degenerate triangle), or perhaps by flagging in one of the vertex attributes whether the vertex exists or not.</span></span> <span data-ttu-id="6ec6a-116">Die müsste dann auch von einem Geometrieshader erkannt und bearbeitet werden, obwohl das Culling von fehlerhafter Geometrie in der Rasterizerphase stattfindet.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-116">This would also need to be detected and handled by a geometry shader, although culling of degenerate geometry will happen in the rasterizer stage.</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="6ec6a-117"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="6ec6a-117"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="6ec6a-118">Die IA-Phase liest Daten aus dem Speicher: Grundtypendaten (Punkte, Linien und/oder Dreiecke) aus vom Benutzer gefüllten Puffern.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-118">The IA stage reads data from memory: primitive data (points, lines and/or triangles), from user-filled buffers.</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="6ec6a-119"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="6ec6a-119"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="6ec6a-120">Die IA-Phase stellt die Daten zu Grundtypen zusammen und hängt systemgenerierte Werte an, und gibt diese als Grundtypen aus, die in der [Vertexshaderphase (VS)](vertex-shader-stage--vs-.md) und danach in anderen Pipelinephasen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-120">The IA stage assembles the data into primitives and attaches system-generated values, and outputs that as primitives that will be used by the [Vertex Shader (VS) stage](vertex-shader-stage--vs-.md) and then other pipeline stages.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="6ec6a-121"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="6ec6a-121"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6ec6a-122">Thema</span><span class="sxs-lookup"><span data-stu-id="6ec6a-122">Topic</span></span></th>
<th align="left"><span data-ttu-id="6ec6a-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6ec6a-123">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="primitive-topologies.md"><span data-ttu-id="6ec6a-124">Primitive Topologien</span><span class="sxs-lookup"><span data-stu-id="6ec6a-124">Primitive topologies</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6ec6a-125">Direct3D unterstützt mehrere primitive Topologien, die definieren, wie Scheitelpunkte, z.B. Punktlisten, Linienlisten und Dreieckstreifen von der Pipeline interpretiert und gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-125">Direct3D supports several primitive topologies, which define how vertices are interpreted and rendered by the pipeline, such as point lists, line lists, and triangle strips.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="using-system-generated-values.md"><span data-ttu-id="6ec6a-126">Verwenden von systemgenerierten Werten</span><span class="sxs-lookup"><span data-stu-id="6ec6a-126">Using system-generated values</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6ec6a-127">Systemgenerierte Werte werden von der Eingabeassemblerphase (IA) generiert (basierend auf vom Benutzer bereitgestellten Eingaben <a href="https://msdn.microsoft.com/library/windows/desktop/bb509647">Semantiken</a>), um bestimmte Effizienzvorteile in Shaderabläufen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-127">System-generated values are generated by the Input Assembler (IA) stage (based on user-supplied input <a href="https://msdn.microsoft.com/library/windows/desktop/bb509647">semantics</a>) to allow certain efficiencies in shader operations.</span></span> <span data-ttu-id="6ec6a-128">Durch das Anhängen von Daten, wie beispielsweise der Instanz-ID (sichtbar für die <a href="vertex-shader-stage--vs-.md">Vertexshaderphase (VS)</a>), einer Scheitelpunkt-ID (sichtbar für VS) oder einer Grundtypen-ID (sichtbar für die <a href="geometry-shader-stage--gs-.md">Geometrieshaderphase (GS)</a>/<a href="pixel-shader-stage--ps-.md">Pixelshaderphase (PS)</a>), kann eine nachfolgende Shaderphase nach diesen Systemwerten suchen, um die Verarbeitung in dieser Phase zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="6ec6a-128">By attaching data, such as an instance ID (visible to the <a href="vertex-shader-stage--vs-.md">Vertex Shader (VS) stage</a>), a vertex ID (visible to VS), or a primitive ID (visible to <a href="geometry-shader-stage--gs-.md">Geometry Shader (GS) stage</a>/<a href="pixel-shader-stage--ps-.md">Pixel Shader (PS) stage</a>), a subsequent shader stage may look for these system values to optimize processing in that stage.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6ec6a-129"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6ec6a-129"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6ec6a-130">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="6ec6a-130">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




