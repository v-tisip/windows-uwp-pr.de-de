---
title: Streamausgabephase (SO)
description: Die Streamausgabephase (Stream Output, SO) gibt (oder streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Phase an einen oder mehrere Puffer im Speicher aus. In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.
ms.assetid: DE89E99F-39BC-4B34-B80F-A7D373AA7C0A
keywords:
- Streamausgabephase (SO)
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 12a0c59942eefd2ab9625b1b442043a1868230a1
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8214702"
---
# <a name="stream-output-so-stage"></a><span data-ttu-id="7a9fb-105">Streamausgabephase (SO)</span><span class="sxs-lookup"><span data-stu-id="7a9fb-105">Stream Output (SO) stage</span></span>


<span data-ttu-id="7a9fb-106">Die Streamausgabephase (Stream Output, SO) gibt (oder streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Phase an einen oder mehrere Puffer im Speicher aus.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-106">The Stream Output (SO) stage continuously outputs (or streams) vertex data from the previous active stage to one or more buffers in memory.</span></span> <span data-ttu-id="7a9fb-107">In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-107">Data streamed out to memory can be re-circulated back into the pipeline as input data, or read-back from the CPU.</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="7a9fb-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="7a9fb-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


![Diagramm der Position der Streamausgabephase in der Pipeline](images/d3d10-pipeline-stages-so.png)

<span data-ttu-id="7a9fb-110">Die Streamausgabephase streamt Grundtypdaten auf dem Weg zum Rasterizer aus der Pipeline in den Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-110">The stream-output stage streams primitive data from the pipeline to memory on its way to the rasterizer.</span></span> <span data-ttu-id="7a9fb-111">Daten aus der vorherigen Phase können in den Arbeitsspeicher gestreamt und/oder in den Rasterizer übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-111">Data from the previous stage can be streamed out to memory, and/or passed into the rasterizer.</span></span> <span data-ttu-id="7a9fb-112">In den Arbeitsspeicher gestreamte Daten können als Eingabedaten der Pipeline wieder zugeführt oder von der CPU eingelesen werden.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-112">Data streamed out to memory can be re-circulated back into the pipeline as input data, or read-back from the CPU.</span></span>

<span data-ttu-id="7a9fb-113">In den Arbeitsspeicher gestreamte Daten können in einem nachfolgenden Renderingdurchlauf zurück in die Pipeline gelesen oder in eine Stagingressource kopiert werden (damit sie von der CPU gelesen werden können).</span><span class="sxs-lookup"><span data-stu-id="7a9fb-113">Data streamed out to memory can be read back into the pipeline in a subsequent rendering pass, or can be copied to a staging resource (so it can be read by the CPU).</span></span> <span data-ttu-id="7a9fb-114">Die Menge der gestreamten Daten kann variieren. Direct3D behandelt die Daten, ohne dass die GPU abgefragt werden muss, welche Menge an Daten geschrieben wurde.&gt;</span><span class="sxs-lookup"><span data-stu-id="7a9fb-114">The amount of data streamed out can vary; Direct3D is designed to handle the data without the need to query (the GPU) about the amount of data written.--&gt;</span></span>

<span data-ttu-id="7a9fb-115">Es gibt zwei Möglichkeiten, die Streamausgabedaten in die Pipeline zu stellen:</span><span class="sxs-lookup"><span data-stu-id="7a9fb-115">There are two ways to feed stream-output data into the pipeline:</span></span>

-   <span data-ttu-id="7a9fb-116">Streamausgabedaten können der Eingabeassemblerphase (IA) wieder zugeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-116">Stream-output data can be fed back into the Input Assembler (IA) stage.</span></span>
-   <span data-ttu-id="7a9fb-117">Streamausgabedaten können von programmierbaren Shadern mit [Load](https://msdn.microsoft.com/library/windows/desktop/bb509694)-Funktionen gelesen werden.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-117">Stream-output data can be read by programmable shaders using [Load](https://msdn.microsoft.com/library/windows/desktop/bb509694) functions.</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="7a9fb-118"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="7a9fb-118"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="7a9fb-119">Vertexdaten aus einer vorherigen Shaderphase.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-119">Vertex data from a previous shader stage.</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="7a9fb-120"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="7a9fb-120"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="7a9fb-121">Die Streamausgabephase (SO) gibt (oder streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Phase, z.B. der Geometry-Shaderphase (GS), in einen oder mehrere Puffer im Arbeitsspeicher aus.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-121">The Stream Ouput (SO) stage continuously outputs (or streams) vertex data from the previous active stage, such as the Geometry Shader (GS) stage, to one or more buffers in memory.</span></span> <span data-ttu-id="7a9fb-122">Wenn die Geometry-Shaderphase (GS) inaktiv ist, gibt die Streamausgabephase (SO) kontinuierlich Vertexdaten aus der Domänen-Shaderphase (DS) an Puffer im Arbeitsspeicher aus (oder wenn DS auch inaktiv ist, aus der Vertex-Shaderphase (VS)).</span><span class="sxs-lookup"><span data-stu-id="7a9fb-122">If the Geometry Shader (GS) stage is inactive, the Stream Ouput (SO) stage continuously outputs vertex data from the Domain Shader (DS) stage to buffers in memory (or if DS is also inactive, from the Vertex Shader (VS) stage).</span></span>

<span data-ttu-id="7a9fb-123">Wenn ein Dreiecks- oder zeilenstrip an die Phase Eingabe-Assembler (IA) gebunden ist, wird jeder Strip in eine Liste konvertiert, bevor er gestreamt werden. Vertices werden immer als vollständige Grundtypen (z. B. 3 Vertices für Dreiecke gleichzeitig); ausgegeben. Unvollständige Grundtypen werden niemals gestreamt. Angrenzende Grundtypen verwerfen die angrenzenden Daten vor dem streaming von Daten.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-123">When a triangle or line strip is bound to the Input Assembler (IA) stage, each strip is converted into a list before they are streamed out. Vertices are always written out as complete primitives (for example, 3 vertices at a time for triangles); incomplete primitives are never streamed out. Primitive types with adjacency discard the adjacency data before streaming data out.</span></span>

<span data-ttu-id="7a9fb-124">Die Streamausgabephase unterstützt gleichzeitig bis zu 4Puffer.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-124">The stream-output stage supports up to 4 buffers simultaneously.</span></span>

-   <span data-ttu-id="7a9fb-125">Wenn Sie Daten in mehrere Puffer streamen, kann jeder Puffer nur ein einzelnes Element (bis zu 4Komponenten) pro Vertexdaten erfassen, mit einem impliziten Datenversatz, der der Elementbreite im jedem Puffer entspricht (kompatibel mit der Art, wie einzelne Elementpuffer für die Eingabe in Shaderphasen gebunden werden können).</span><span class="sxs-lookup"><span data-stu-id="7a9fb-125">If you are streaming data into multiple buffers, each buffer can only capture a single element (up to 4 components) of per-vertex data, with an implied data stride equal to the element width in each buffer (compatible with the way single element buffers can be bound for input into shader stages).</span></span> <span data-ttu-id="7a9fb-126">Wenn Puffer unterschiedliche Größen haben, wird darüber hinaus der Schreibvorgang angehalten, sobald einer der Puffer voll ist.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-126">Furthermore, if the buffers have different sizes, writing stops as soon as any one of the buffers is full.</span></span>
-   <span data-ttu-id="7a9fb-127">Wenn Sie Daten in einen einzelnen Puffer streamen, kann der Puffer bis zu 64skalare Komponenten pro Vertexdaten erfassen (256Byte oder weniger) oder der Vertexversatz kann bis zu 2048Byte betragen.</span><span class="sxs-lookup"><span data-stu-id="7a9fb-127">If you are streaming data into a single buffer, the buffer can capture up to 64 scalar components of per-vertex data (256 bytes or less) or the vertex stride can be up to 2048 bytes.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="7a9fb-128"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7a9fb-128"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="7a9fb-129">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="7a9fb-129">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




