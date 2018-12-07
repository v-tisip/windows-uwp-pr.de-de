---
title: Streamausgabephase (SO)
description: Die Streamausgabephase (Stream Output, SO) gibt (oder streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Phase an einen oder mehrere Puffer im Speicher aus. In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.
ms.assetid: DE89E99F-39BC-4B34-B80F-A7D373AA7C0A
keywords:
- Streamausgabephase (SO)
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 87eb6562c6ee66ca1d409d3748e688861d5f3920
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8783508"
---
# <a name="stream-output-so-stage"></a><span data-ttu-id="e5a84-105">Streamausgabephase (SO)</span><span class="sxs-lookup"><span data-stu-id="e5a84-105">Stream Output (SO) stage</span></span>


<span data-ttu-id="e5a84-106">Die Streamausgabephase (Stream Output, SO) gibt (oder streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Phase an einen oder mehrere Puffer im Speicher aus.</span><span class="sxs-lookup"><span data-stu-id="e5a84-106">The Stream Output (SO) stage continuously outputs (or streams) vertex data from the previous active stage to one or more buffers in memory.</span></span> <span data-ttu-id="e5a84-107">In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.</span><span class="sxs-lookup"><span data-stu-id="e5a84-107">Data streamed out to memory can be re-circulated back into the pipeline as input data, or read-back from the CPU.</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="e5a84-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="e5a84-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


![Diagramm der Position der Streamausgabephase in der Pipeline](images/d3d10-pipeline-stages-so.png)

<span data-ttu-id="e5a84-110">Die Streamausgabephase streamt Grundtypdaten auf dem Weg zum Rasterizer aus der Pipeline in den Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="e5a84-110">The stream-output stage streams primitive data from the pipeline to memory on its way to the rasterizer.</span></span> <span data-ttu-id="e5a84-111">Daten aus der vorherigen Phase können in den Arbeitsspeicher gestreamt und/oder in den Rasterizer übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="e5a84-111">Data from the previous stage can be streamed out to memory, and/or passed into the rasterizer.</span></span> <span data-ttu-id="e5a84-112">In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.</span><span class="sxs-lookup"><span data-stu-id="e5a84-112">Data streamed out to memory can be re-circulated back into the pipeline as input data, or read-back from the CPU.</span></span>

<span data-ttu-id="e5a84-113">In den Arbeitsspeicher gestreamte Daten können in einem nachfolgenden Renderingdurchlauf zurück in die Pipeline gelesen oder in eine Stagingressource kopiert werden (damit sie von der CPU gelesen werden können).</span><span class="sxs-lookup"><span data-stu-id="e5a84-113">Data streamed out to memory can be read back into the pipeline in a subsequent rendering pass, or can be copied to a staging resource (so it can be read by the CPU).</span></span> <span data-ttu-id="e5a84-114">Die Menge der gestreamten Daten kann variieren. Direct3D behandelt die Daten, ohne dass die GPU abgefragt werden muss, welche Menge an Daten geschrieben wurde.&gt;</span><span class="sxs-lookup"><span data-stu-id="e5a84-114">The amount of data streamed out can vary; Direct3D is designed to handle the data without the need to query (the GPU) about the amount of data written.--&gt;</span></span>

<span data-ttu-id="e5a84-115">Es gibt zwei Möglichkeiten, die Streamausgabedaten in die Pipeline zu stellen:</span><span class="sxs-lookup"><span data-stu-id="e5a84-115">There are two ways to feed stream-output data into the pipeline:</span></span>

-   <span data-ttu-id="e5a84-116">Streamausgabedaten können der Eingabeassemblerphase (IA) wieder zugeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e5a84-116">Stream-output data can be fed back into the Input Assembler (IA) stage.</span></span>
-   <span data-ttu-id="e5a84-117">Streamausgabedaten können von programmierbaren Shadern mit [Load](https://msdn.microsoft.com/library/windows/desktop/bb509694)-Funktionen gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="e5a84-117">Stream-output data can be read by programmable shaders using [Load](https://msdn.microsoft.com/library/windows/desktop/bb509694) functions.</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="e5a84-118"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="e5a84-118"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="e5a84-119">Vertexdaten aus einer vorherigen Shaderphase.</span><span class="sxs-lookup"><span data-stu-id="e5a84-119">Vertex data from a previous shader stage.</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="e5a84-120"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="e5a84-120"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="e5a84-121">Die Streamoutputstufe (SO-Stufe) liefert (streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Stufe (z.B. der Geometry-Shader-Stufe (GS-Stufe) ) in einen oder mehrere Puffer im Speicher.</span><span class="sxs-lookup"><span data-stu-id="e5a84-121">The Stream Output (SO) stage continuously outputs (or streams) vertex data from the previous active stage, such as the Geometry Shader (GS) stage, to one or more buffers in memory.</span></span> <span data-ttu-id="e5a84-122">Wenn die Geometrieshaderphase (GS) inaktiv ist, gibt die Streamoutputstufe (SO) kontinuierlich Vertexdaten aus der Domänen-Shaderphase (DS)-Phase in Puffer im Speicher (oder wenn DS auch inaktiv ist, aus der Vertex-Shader (VS) Phase ist).</span><span class="sxs-lookup"><span data-stu-id="e5a84-122">If the Geometry Shader (GS) stage is inactive, the Stream Output (SO) stage continuously outputs vertex data from the Domain Shader (DS) stage to buffers in memory (or if DS is also inactive, from the Vertex Shader (VS) stage).</span></span>

<span data-ttu-id="e5a84-123">Wenn ein Dreiecks- oder zeilenstrip an die Phase Eingabe-Assembler (IA) gebunden ist, wird jeder Strip in eine Liste konvertiert, bevor er gestreamt werden. Vertices werden immer als vollständige Grundtypen (z. B. 3 Vertices für Dreiecke gleichzeitig); ausgegeben. Unvollständige Grundtypen werden niemals gestreamt. Angrenzende Grundtypen verwerfen die angrenzenden Daten vor dem streaming.</span><span class="sxs-lookup"><span data-stu-id="e5a84-123">When a triangle or line strip is bound to the Input Assembler (IA) stage, each strip is converted into a list before they are streamed out. Vertices are always written out as complete primitives (for example, 3 vertices at a time for triangles); incomplete primitives are never streamed out. Primitive types with adjacency discard the adjacency data before streaming data out.</span></span>

<span data-ttu-id="e5a84-124">Die Streamausgabephase unterstützt gleichzeitig bis zu 4Puffer.</span><span class="sxs-lookup"><span data-stu-id="e5a84-124">The stream-output stage supports up to 4 buffers simultaneously.</span></span>

-   <span data-ttu-id="e5a84-125">Wenn Sie Daten in mehrere Puffer streamen, kann jeder Puffer nur ein einzelnes Element (bis zu 4Komponenten) pro Vertexdaten erfassen, mit einem impliziten Datenversatz, der der Elementbreite im jedem Puffer entspricht (kompatibel mit der Art, wie einzelne Elementpuffer für die Eingabe in Shaderphasen gebunden werden können).</span><span class="sxs-lookup"><span data-stu-id="e5a84-125">If you are streaming data into multiple buffers, each buffer can only capture a single element (up to 4 components) of per-vertex data, with an implied data stride equal to the element width in each buffer (compatible with the way single element buffers can be bound for input into shader stages).</span></span> <span data-ttu-id="e5a84-126">Wenn Puffer unterschiedliche Größen haben, wird darüber hinaus der Schreibvorgang angehalten, sobald einer der Puffer voll ist.</span><span class="sxs-lookup"><span data-stu-id="e5a84-126">Furthermore, if the buffers have different sizes, writing stops as soon as any one of the buffers is full.</span></span>
-   <span data-ttu-id="e5a84-127">Wenn Sie Daten in einen einzelnen Puffer streamen, kann der Puffer bis zu 64skalare Komponenten pro Vertexdaten erfassen (256Byte oder weniger) oder der Vertexversatz kann bis zu 2048Byte betragen.</span><span class="sxs-lookup"><span data-stu-id="e5a84-127">If you are streaming data into a single buffer, the buffer can capture up to 64 scalar components of per-vertex data (256 bytes or less) or the vertex stride can be up to 2048 bytes.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e5a84-128"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e5a84-128"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e5a84-129">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="e5a84-129">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




