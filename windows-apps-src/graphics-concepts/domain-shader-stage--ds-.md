---
title: Domainshaderphase (DS)
description: Die Domainshaderphase (DS) berechnet die Vertexposition eines unterteilten Punkts im Ausgabefeld. Sie Berechnet die Vertexposition, die dem jeweiligen Domainsample entspricht.
ms.assetid: 673CC04A-A74F-495F-AFB7-49157538749C
keywords:
- Domainshaderphase (DS)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 3bcad4a5e22249d4d7faed08fe9cc9af4c3fb338
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7150584"
---
# <a name="domain-shader-ds-stage"></a><span data-ttu-id="11199-104">Domainshaderphase (DS)</span><span class="sxs-lookup"><span data-stu-id="11199-104">Domain Shader (DS) stage</span></span>


<span data-ttu-id="11199-105">Die Domainshaderphase (DS) berechnet die Vertexposition eines unterteilten Punkts im Ausgabe-Patch. Sie berechnet die Vertexposition, die dem jeweiligen Domainsample entspricht.</span><span class="sxs-lookup"><span data-stu-id="11199-105">The Domain Shader (DS) stage calculates the vertex position of a subdivided point in the output patch; it calculates the vertex position that corresponds to each domain sample.</span></span> <span data-ttu-id="11199-106">Ein Domainshader wird einmal pro Tessellator-Phase-Ausgabepunkt ausgeführt und verfügt über schreibgeschützten Zugriff auf den Hull-Shader-Patch und die Ausgabe-Patch-Konstanten sowie die Tessellator-Phase-Ausgabe-UV-Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="11199-106">A domain shader is run once per tessellator stage output point and has read-only access to the hull shader output patch and output patch constants, and the tessellator stage output UV coordinates.</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="11199-107"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="11199-107"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


<span data-ttu-id="11199-108">Die Domainshaderphase (DS) gibt die Vertex-Position eines unterteilen Punkts im Ausgabe Patch aus (basierend auf der Eingabe der [Hull-Shader-Phase (HS)](hull-shader-stage--hs-.md) und der [Tessellator-Phase (TS)](tessellator-stage--ts-.md)).</span><span class="sxs-lookup"><span data-stu-id="11199-108">The Domain Shader (DS) stage outputs the vertex position of a subdivided point in the output patch, based on input from the [Hull Shader (HS) stage](hull-shader-stage--hs-.md) and the [Tessellator (TS) stage](tessellator-stage--ts-.md).</span></span>

![Diagramm der Domainshaderphase](images/d3d11-domain-shader.png)

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="11199-110"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="11199-110"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


-   <span data-ttu-id="11199-111">Ein Domainshader nimmt die Ausgabe-Kontrollpunkte aus der [Hull-Shader-Phase (HS)](hull-shader-stage--hs-.md) entgegen.</span><span class="sxs-lookup"><span data-stu-id="11199-111">A domain shader consumes output control points from the [Hull Shader (HS) stage](hull-shader-stage--hs-.md).</span></span> <span data-ttu-id="11199-112">Die Hull-Shader-Ausgaben umfassen:</span><span class="sxs-lookup"><span data-stu-id="11199-112">The hull shader outputs include:</span></span>
    -   <span data-ttu-id="11199-113">Kontrollpunkte.</span><span class="sxs-lookup"><span data-stu-id="11199-113">Control points.</span></span>
    -   <span data-ttu-id="11199-114">Patch-Konstantendaten.</span><span class="sxs-lookup"><span data-stu-id="11199-114">Patch constant data.</span></span>
    -   <span data-ttu-id="11199-115">Tessellation-Faktoren.</span><span class="sxs-lookup"><span data-stu-id="11199-115">Tessellation factors.</span></span> <span data-ttu-id="11199-116">Die Tesselation-Faktoren können die vom Fixed-Function-Tessellator verwendeten Werte und die Rohwerte (z. B. vor der Rundung durch die Integer-Tesselation) umfassen. Diese werden beispielsweise für das Geomorphing verwendet.</span><span class="sxs-lookup"><span data-stu-id="11199-116">The tessellation factors can include the values used by the fixed-function tessellator as well as the raw values (before rounding by integer tessellation, for example), which facilitates geomorphing, for example.</span></span>
-   <span data-ttu-id="11199-117">Ein Domainshader wird einmal pro Ausgabekoordinate über die [Tessellator-Phase (TS)](tessellator-stage--ts-.md) aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="11199-117">A domain shader is invoked once per output coordinate from the [Tessellator (TS) stage](tessellator-stage--ts-.md).</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="11199-118"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="11199-118"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


-   <span data-ttu-id="11199-119">Die Domainshaderphase (DS) gibt die Vertex-Position eines unterteilten Punkts im Ausgabe-Patch zurück.</span><span class="sxs-lookup"><span data-stu-id="11199-119">The Domain Shader (DS) stage outputs the vertex position of a subdivided point in the output patch.</span></span>

<span data-ttu-id="11199-120">Nachdem der Domainshader abgeschlossen ist, wird die Tesselation abgeschlossen und die Pipelinedaten werden an die nächste Pipelinephase weitergeleitet (z. B. die [Geometry-Shader-Phase (GS)](geometry-shader-stage--gs-.md) und die [Pixel-Shader-Phase (PS)](pixel-shader-stage--ps-.md)).</span><span class="sxs-lookup"><span data-stu-id="11199-120">After the domain shader completes, tessellation is finished and pipeline data continues to the next pipeline stage, such as the [Geometry Shader (GS) stage](geometry-shader-stage--gs-.md) and the [Pixel Shader (PS) stage](pixel-shader-stage--ps-.md).</span></span> <span data-ttu-id="11199-121">Ein Geometrieshader erwartet Primitiven mit strukturierten Daten (z. B. 6 Vertizes pro Dreieck). Er ist bei aktiver Tesselation nicht gültig (dies führt zu einem unerwartetem Verhalten, das einen Fehler der Debugschicht auslöst).</span><span class="sxs-lookup"><span data-stu-id="11199-121">A geometry shader that expects primitives with adjacency (for example, 6 vertices per triangle) is not valid when tessellation is active (this results in undefined behavior, which the debug layer will complain about).</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="11199-122"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="11199-122"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


```
void main( out    MyDSOutput result, 
           float2 myInputUV : SV_DomainPoint, 
           MyDSInput DSInputs,
           OutputPatch<MyOutPoint, 12> ControlPts, 
           MyTessFactors tessFactors)
{
     ...

     result.Position = EvaluateSurfaceUV(ControlPoints, myInputUV);
}
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="11199-123"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11199-123"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="11199-124">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="11199-124">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




