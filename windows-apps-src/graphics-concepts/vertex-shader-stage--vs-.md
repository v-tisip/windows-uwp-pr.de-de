---
title: Scheitelpunkt-Shader- (VS) Phase
description: Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte und führt dabei in der Regel Vorgänge wie Transformationen, das Anwenden von Skins und Beleuchtung durch. Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt.
ms.assetid: 5133C4BB-B4E6-4697-9276-F718AD44869C
keywords:
- Scheitelpunkt-Shader- (VS) Phase
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d6b9c67220c282ef1677559d586013c14366967a
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6204801"
---
# <a name="vertex-shader-vs-stage"></a><span data-ttu-id="c8e5c-105">Scheitelpunkt-Shader- (VS) Phase</span><span class="sxs-lookup"><span data-stu-id="c8e5c-105">Vertex Shader (VS) stage</span></span>


<span data-ttu-id="c8e5c-106">Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte und führt dabei in der Regel Vorgänge wie Transformationen, das Anwenden von Skins und Beleuchtung durch.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-106">The Vertex Shader (VS) stage processes vertices, typically performing operations such as transformations, skinning, and lighting.</span></span> <span data-ttu-id="c8e5c-107">Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-107">A vertex shader takes a single input vertex and produces a single output vertex.</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="c8e5c-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="c8e5c-108"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


<span data-ttu-id="c8e5c-109">Die Scheitelpunkt-Shader- (VS) Phase wird für einzelne Scheitelpunktverarbeitungen verwendet, wie etwa:</span><span class="sxs-lookup"><span data-stu-id="c8e5c-109">The Vertex Shader (VS) stage is used for individual per-vertex processing such as:</span></span>

-   <span data-ttu-id="c8e5c-110">Transformationen</span><span class="sxs-lookup"><span data-stu-id="c8e5c-110">Transformations</span></span>
-   <span data-ttu-id="c8e5c-111">Anwenden von Skins</span><span class="sxs-lookup"><span data-stu-id="c8e5c-111">Skinning</span></span>
-   <span data-ttu-id="c8e5c-112">Morphing</span><span class="sxs-lookup"><span data-stu-id="c8e5c-112">Morphing</span></span>
-   <span data-ttu-id="c8e5c-113">Scheitelpunktbeleuchtung</span><span class="sxs-lookup"><span data-stu-id="c8e5c-113">Per-vertex lighting</span></span>

<span data-ttu-id="c8e5c-114">Die Scheitelpunkt-Shader-Stufe ist eine programmierbare Shader-Stufe. Sie wird im [Grafikpipeline](graphics-pipeline.md)- Diagramm als abgerundeter Block angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-114">The Vertex Shader stage is a programmable-shader stage; it is shown as a rounded block in the [graphics pipeline](graphics-pipeline.md) diagram.</span></span> <span data-ttu-id="c8e5c-115">Dieser Shader-Stufe verwendet Shadermodell 4.0 [gemeinsamer Shaderkern](https://msdn.microsoft.com/library/windows/desktop/bb509580).</span><span class="sxs-lookup"><span data-stu-id="c8e5c-115">This shader stage uses shader model 4.0 [common-shader core](https://msdn.microsoft.com/library/windows/desktop/bb509580).</span></span>

<span data-ttu-id="c8e5c-116">Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte aus dem Eingabe-Assembler.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-116">The vertex-shader (VS) stage processes vertices from the input assembler.</span></span> <span data-ttu-id="c8e5c-117">Ein Scheitelpunkt-Shader operiert immer auf einem einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-117">Vertex shaders always operate on a single input vertex and produce a single output vertex.</span></span> <span data-ttu-id="c8e5c-118">Die Scheitelpunkt-Shader-Phase muss immer für auszuführende Pipeline aktiv sein.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-118">The vertex shader stage must always be active for the pipeline to execute.</span></span> <span data-ttu-id="c8e5c-119">Wenn keine Scheitelpunktänderung oder -transformation erforderlich ist, muss ein Pass-Through-Scheitelpunkt-Shader erstellt und auf die Pipeline festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-119">If no vertex modification or transformation is required, a pass-through vertex shader must be created and set to the pipeline.</span></span>

<span data-ttu-id="c8e5c-120">Jeder Scheitelpunkt-Shader-Eingabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren (mit jeweils bis zu 4 Komponenten) bestehen.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-120">Each vertex shader input vertex can be comprised of up to 16 32-bit vectors (up to 4 components each).</span></span> <span data-ttu-id="c8e5c-121">Jeder Ausgabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren mit jeweils 4 Komponenten bestehen.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-121">Each output vertex can be comprised of as many as 16 32-bit 4-component vectors.</span></span> <span data-ttu-id="c8e5c-122">Alle Scheitelpunkt-Shader benötigen mindestens eine Eingabe und eine Ausgabe, die so klein wie ein Skalarwert sein können.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-122">All vertex shaders must have a minimum of one input and one output, which can be as little as one scalar value.</span></span>

<span data-ttu-id="c8e5c-123">Der Scheitelpunkt-Shader-Phase kann zwei vom System generierte Werte vom Eingabe-Assembler verarbeiten: Scheitelpunkt-ID und Instanz-ID (vgl. Systemwerte und Semantik).</span><span class="sxs-lookup"><span data-stu-id="c8e5c-123">The vertex-shader stage can consume two system-generated values from the input assembler: VertexID and InstanceID (see System Values and Semantics).</span></span> <span data-ttu-id="c8e5c-124">Da Scheitelpunkt-ID und Instanz-ID auf Scheitelpunktebene bedeutsam sind und von der Hardware generierte IDs nur in di erste Phase eingegeben werden können, die sie versteht, können diese ID-Werte nur in die Scheitelpunkt-Shader-Phase eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-124">Since VertexID and InstanceID are both meaningful at a vertex level, and IDs generated by hardware can only be fed into the first stage that understands them, these ID values can only be fed into the vertex-shader stage.</span></span>

<span data-ttu-id="c8e5c-125">Scheitelpunkt-Shader werden immer auf allen Scheitelpunkten ausgeführt, einschließlich benachbarter Scheitelpunkte in Eingabe-Grundtyp-Topologien mit Nachbarschaft.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-125">Vertex shaders are always run on all vertices, including adjacent vertices in input primitive topologies with adjacency.</span></span> <span data-ttu-id="c8e5c-126">Die Ausführungshäufigkeit des Scheitelpunkt-Shaders kann von der CPU mithilfe der VSInvocations-Pipelinestatistik abgefragt werden.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-126">The number of times that the vertex shader has been executed can be queried from the CPU using the VSInvocations pipeline statistic.</span></span>

<span data-ttu-id="c8e5c-127">Ein Scheitelpunkt-Shader kann Lade- und Textursampling-Vorgänge durchführen, bei denen Bildschirmbereichsableitungen nicht erforderlich sind (mithilfe systeminterner HLSL-Funktionen: [Sample (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509695), [SampleCmpLevelZero (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509697) und [SampleGrad (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509698)).</span><span class="sxs-lookup"><span data-stu-id="c8e5c-127">A vertex shader can perform load and texture sampling operations where screen-space derivatives are not required (using HLSL intrinsic functions: [Sample (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509695), [SampleCmpLevelZero (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509697), and [SampleGrad (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509698)).</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="c8e5c-128"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="c8e5c-128"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="c8e5c-129">Ein einzelner Scheitelpunkt- mit den vom System generierten Werten Scheitelpunkt-ID und Instanz-ID.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-129">A single vertex, with VertexID and InstanceID system-generated values.</span></span> <span data-ttu-id="c8e5c-130">Jeder Eingabevertex für einen Vertex-Shader kann aus mehreren 32-Bit-Vektoren bestehen (maximal 16, mit jeweils bis zu 4-Komponenten).</span><span class="sxs-lookup"><span data-stu-id="c8e5c-130">Each vertex shader input vertex can be comprised of up to 16 32-bit vectors (up to 4 components each).</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="c8e5c-131"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="c8e5c-131"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="c8e5c-132">Ein einzelner Vertex.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-132">A single vertex.</span></span> <span data-ttu-id="c8e5c-133">Jeder Ausgabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren mit jeweils 4 Komponenten bestehen.</span><span class="sxs-lookup"><span data-stu-id="c8e5c-133">Each output vertex can be comprised of as many as 16 32-bit 4-component vectors.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="c8e5c-134"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c8e5c-134"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="c8e5c-135">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="c8e5c-135">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




