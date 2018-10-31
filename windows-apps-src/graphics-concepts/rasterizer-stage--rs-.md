---
title: Rasterizerphase (RS)
description: Der Rasterizer beschneidet Grundtypen, die nicht angezeigt werden, bereitet Grundtypen für die Pixelshaderphase (PS) vor und bestimmt, wie Pixelshader aufgerufen werden.
ms.assetid: 7E80724B-5696-4A99-91AF-49744B5CD3A9
keywords:
- Rasterizerphase (RS)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 17d58a05a57fa833003b7c229db91473f6cde3d4
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5814916"
---
# <a name="rasterizer-rs-stage"></a><span data-ttu-id="f244b-104">Rasterizerphase (RS)</span><span class="sxs-lookup"><span data-stu-id="f244b-104">Rasterizer (RS) stage</span></span>


<span data-ttu-id="f244b-105">Der Rasterizer beschneidet Grundtypen, die nicht angezeigt werden, bereitet Grundtypen für die [Pixelshaderphase (PS)](pixel-shader-stage--ps-.md) vor und bestimmt, wie Pixelshader aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f244b-105">The rasterizer clips primitives that aren't in view, prepares primitives for the [Pixel Shader (PS) stage](pixel-shader-stage--ps-.md), and determines how to invoke pixel shaders.</span></span> <span data-ttu-id="f244b-106">Die Rasterizerphase konvertiert Vektorinformationen (bestehend aus Formen oder Grundtypen) in ein Rasterbild (bestehend aus Pixeln) zum Anzeigen von 3D-Grafiken in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="f244b-106">The rasterization stage converts vector information (composed of shapes or primitives) into a raster image (composed of pixels) for the purpose of displaying real-time 3D graphics.</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="f244b-107"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="f244b-107"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


<span data-ttu-id="f244b-108">Im Verlauf der Rasterung wird jeder Grundtyp in Pixel konvertiert, wobei Pro-Vertex-Werte für jeden Grundtyp interpoliert werden.</span><span class="sxs-lookup"><span data-stu-id="f244b-108">During rasterization, each primitive is converted into pixels, while interpolating per-vertex values across each primitive.</span></span> <span data-ttu-id="f244b-109">Bei der Rasterung erfolgt der Beschnitt von Vertices auf das Frustum, eine Division durch Z zum Erhalt der Perspektive, die Zuordnung von Grundtypen zu einem 2D Viewport und das Festlegen, wie der Pixelshader aufgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="f244b-109">Rasterization includes clipping vertices to the view frustum, performing a divide by z to provide perspective, mapping primitives to a 2D viewport, and determining how to invoke the pixel shader.</span></span> <span data-ttu-id="f244b-110">Das Verwenden eines Pixelshader ist optional, aber die Rasterizerphase umfasst immer einen Beschnitt, eine perspektivische Division, um die Punkte in homogenen Raum zu transformieren Rasterizer-Stufe immer und ordnet die Scheitelpunkte der Viewport.</span><span class="sxs-lookup"><span data-stu-id="f244b-110">While using a pixel shader is optional, the rasterizer stage always performs clipping, a perspective divide to transform the points into homogeneous space, and maps the vertices to the viewport.</span></span>

<span data-ttu-id="f244b-111">Sie können die Rasterung deaktivieren, indem Sie der Pipeline sagen, dass kein Pixelshader vorhanden ist (Einstellen der [Pixelshaderphase (PS)](pixel-shader-stage--ps-.md) auf **NULL** und Deaktivieren von Tiefen- und Schablonentests).</span><span class="sxs-lookup"><span data-stu-id="f244b-111">You may disable rasterization by telling the pipeline there is no pixel shader (set the [Pixel Shader (PS) stage](pixel-shader-stage--ps-.md) to **NULL** and disable depth and stencil testing).</span></span> <span data-ttu-id="f244b-112">Wenn die Rasterung deaktiviert ist, werden damit zusammenhängende Pipelinezähler nicht aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="f244b-112">While disabled, rasterization-related pipeline counters will not update.</span></span>

<span data-ttu-id="f244b-113">Bei Hardware, die hierarchische Z-Puffer-Optimierungen implementiert, können Sie das Vorabladen des Z-Puffers aktivieren, indem Sie die Pixelshaderphase (PS) auf **NULL** stellen und Tiefen- und Schablonentests aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f244b-113">On hardware that implements hierarchical Z-buffer optimizations, you may enable preloading the z-buffer by setting the Pixel Shader (PS) stage to **NULL** while enabling depth and stencil testing.</span></span>

<span data-ttu-id="f244b-114">Siehe [Regeln für die Rasterung](rasterization-rules.md).</span><span class="sxs-lookup"><span data-stu-id="f244b-114">See [Rasterization rules](rasterization-rules.md).</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="f244b-115"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="f244b-115"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="f244b-116">Vertices (x,y,z,w), die in die Rasterizerphase gelangen, werden als in einem homogenen Clipraum angesehen.</span><span class="sxs-lookup"><span data-stu-id="f244b-116">Vertices (x,y,z,w), coming into the Rasterizer stage are assumed to be in homogeneous clip-space.</span></span> <span data-ttu-id="f244b-117">In diesem Koordinatenbereich weist die x-Achse nach rechts, Y nach oben und Z von der Kamera weg.</span><span class="sxs-lookup"><span data-stu-id="f244b-117">In this coordinate space the X axis points right, Y points up and Z points away from camera.</span></span>

<span data-ttu-id="f244b-118">Die Rasterizerphase (RS) ist eine feste Funktion und speist sich aus der Streamausgabephase und/oder der vorherigen Pipelinephase, z.B. der [Geometrieshaderphase (GS)](geometry-shader-stage--gs-.md).</span><span class="sxs-lookup"><span data-stu-id="f244b-118">The fixed-function Rasterizer (RS) stage is fed by the Stream Output (SO) stage and/or by the previous pipeline stage, such as the [Geometry Shader (GS) stage](geometry-shader-stage--gs-.md).</span></span> <span data-ttu-id="f244b-119">Wenn die GS nicht verwendet wird, wird die RS aus der [Domänenshaderphase (DS)](domain-shader-stage--ds-.md) gespeist.</span><span class="sxs-lookup"><span data-stu-id="f244b-119">If GS isn't used, RS is fed by the [Domain Shader (DS) stage](domain-shader-stage--ds-.md).</span></span> <span data-ttu-id="f244b-120">Wenn auch die DS nicht verwendet wird, speist sich die RS aus der [Vertexshaderphase (VS)](vertex-shader-stage--vs-.md).</span><span class="sxs-lookup"><span data-stu-id="f244b-120">If DS also isn't used, RS is fed by the [Vertex Shader (VS) stage](vertex-shader-stage--vs-.md).</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="f244b-121"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="f244b-121"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="f244b-122">Die Verwendung der Pixelshaderphase (PS) ist optional. Von der Rasterizerphase kann die Ausgabe stattdessen direkt an die [Ausgabemergerphase (OM)](output-merger-stage--om-.md) erfolgen.</span><span class="sxs-lookup"><span data-stu-id="f244b-122">Using the Pixel Shader (PS) stage is optional; the rasterizer stage can output directly to the [Output Merger (OM) stage](output-merger-stage--om-.md) instead.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="f244b-123"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f244b-123"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="f244b-124">Regeln für die Rasterung</span><span class="sxs-lookup"><span data-stu-id="f244b-124">Rasterization rules</span></span>](rasterization-rules.md)

[<span data-ttu-id="f244b-125">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="f244b-125">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




