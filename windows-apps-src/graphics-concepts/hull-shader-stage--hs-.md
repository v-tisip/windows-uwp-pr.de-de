---
title: Hull-Shader-Stufe (HS-Stufe))
description: Die Hull-Shader-Stufe ist eine der Tesselationsstufen, auf der eine durchgehende Fläche eines Modell effizient in vielen Dreiecke unterteilt wird.
ms.assetid: C62F6F15-CAD7-4C72-9735-00762E346C4C
keywords:
- Hull-Shader-Stufe (HS-Stufe)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d2aed18d476f966e644fa095aa6a5a518ebbe959
ms.sourcegitcommit: d0e836dfc937ebf7dfa9c424620f93f3c8e0a7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5638411"
---
# <a name="hull-shader-hs-stage"></a><span data-ttu-id="8b8c8-104">Hull-Shader-Stufe (HS-Stufe)</span><span class="sxs-lookup"><span data-stu-id="8b8c8-104">Hull Shader (HS) stage</span></span>


<span data-ttu-id="8b8c8-105">Die Hull-Shader-Stufe ist eine der Tesselationsstufen, auf der eine durchgehende Fläche eines Modells effizient in viele Dreiecke unterteilt wird.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-105">The Hull Shader (HS) stage is one of the tessellation stages, which efficiently break up a single surface of a model into many triangles.</span></span> <span data-ttu-id="8b8c8-106">Die Hull-Shader-Stufe (HS-Stufe) erzeugt einen Geometriepatch (und Patchkonstanten), der jedem Eingabepatch (Quadrat, Dreieck oder Linie) entspricht.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-106">The Hull Shader (HS) stage produces a geometry patch (and patch constants) that correspond to each input patch (quad, triangle, or line).</span></span> <span data-ttu-id="8b8c8-107">Ein Hull-Shader wird einmal pro Patch aufgerufen. Er transformiert Eingabekontrollpunkte, die eine Oberfläche niederer Ordnung definieren, in Kontrollpunkte, die einen Patch bilden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-107">A hull shader is invoked once per patch, and it transforms input control points that define a low-order surface into control points that make up a patch.</span></span> <span data-ttu-id="8b8c8-108">Er führt außerdem pro Patch einige Berechnungen aus, um der [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md) und der [Domain-Shader-Stufe (DS-Stufe)](domain-shader-stage--ds-.md) Daten bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-108">It also does some per-patch calculations to provide data for the [Tessellator (TS) stage](tessellator-stage--ts-.md) and the [Domain Shader (DS) stage](domain-shader-stage--ds-.md).</span></span>

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span data-ttu-id="8b8c8-109"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung</span><span class="sxs-lookup"><span data-stu-id="8b8c8-109"><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Purpose and uses</span></span>


![Diagramm der Hull-Shader-Stufe](images/d3d11-hull-shader.png)

<span data-ttu-id="8b8c8-111">Die drei Tesselationsstufen arbeiten zusammen, um Oberflächen höherer Ordnung (die das Modell einfach und effizient halten) in viele Dreiecke umzuwandeln, die in der Grafikpipeline detailliert gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-111">The three tessellation stages work together to convert higher-order surfaces (which keep the model simple and efficient) to many triangles for detailed rendering within the graphics pipeline.</span></span> <span data-ttu-id="8b8c8-112">Die Tesselationsstufen sind die Hull-Shader-Stufe (HS-Stufe), die [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md) und die [Domain-Shader-Stufe (DS-Stufe).](domain-shader-stage--ds-.md).</span><span class="sxs-lookup"><span data-stu-id="8b8c8-112">The tessellation stages include the Hull Shader (HS) stage, [Tessellator (TS) stage](tessellator-stage--ts-.md), and [Domain Shader (DS) stage](domain-shader-stage--ds-.md).</span></span>

<span data-ttu-id="8b8c8-113">Die Hull-Shader-Stufe (HS-Stufe) ist eine programmierbare Shaderstufe.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-113">The Hull Shader (HS) stage is a programmable shader stage.</span></span> <span data-ttu-id="8b8c8-114">Ein Hull-Shader wird mit einer HLSL-Funktion implementiert.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-114">A hull shader is implemented with an HLSL function.</span></span>

<span data-ttu-id="8b8c8-115">Ein Hull-Shader arbeitet in zwei Stufen – einer Kontrollpunktstufe und einer Patchkonstantenstufe, die von der Hardware parallel ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-115">A hull shader operates in two phases: a control-point phase and a patch-constant phase, which are run in parallel by the hardware.</span></span> <span data-ttu-id="8b8c8-116">Der HLSL-Compiler extrahiert die parallelen Hull-Shader-Ergebnisse und wandelt sie in Bytecode um, der von der Hardware verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-116">The HLSL compiler extracts the parallelism in a hull shader and encodes it into bytecode that drives the hardware.</span></span>

-   <span data-ttu-id="8b8c8-117">Die Kontrollpunktstufe liest jeden Kontrollpunkt für einen Patch und generiert daraus einen Ausgabekontrollpunkt (gekennzeichnet durch eine **ControlPointID**).</span><span class="sxs-lookup"><span data-stu-id="8b8c8-117">The control-point phase operates once for each control-point, reading the control points for a patch, and generating one output control point (identified by a **ControlPointID**).</span></span>
-   <span data-ttu-id="8b8c8-118">Die Patchkonstantenstufe generiert pro Patch Randtesselationsfaktoren und andere Patchkonstanten.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-118">The patch-constant phase operates once per patch to generate edge tessellation factors and other per-patch constants.</span></span> <span data-ttu-id="8b8c8-119">Intern können viele Patchkonstantenstufen gleichzeitig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-119">Internally, many patch-constant phases may run at the same time.</span></span> <span data-ttu-id="8b8c8-120">Die Patchkonstantenstufe verfügt über schreibgeschützten Zugriff auf alle Eingabe- und Ausgabekontrollpunkte.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-120">The patch-constant phase has read-only access to all input and output control points.</span></span>

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span data-ttu-id="8b8c8-121"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe</span><span class="sxs-lookup"><span data-stu-id="8b8c8-121"><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Input</span></span>


<span data-ttu-id="8b8c8-122">1 bis 32 Eingabekontrollpunkte, die zusammen eine Fläche niederer Ordnung definieren.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-122">Between 1 and 32 input control points, which together define a low-order surface.</span></span>

-   <span data-ttu-id="8b8c8-123">Der Hull-Shader deklariert den erforderlichen Zustand für die [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md).</span><span class="sxs-lookup"><span data-stu-id="8b8c8-123">The hull shader declares the state required by the [Tessellator (TS) stage](tessellator-stage--ts-.md).</span></span> <span data-ttu-id="8b8c8-124">Dazu gehören Informationen wie die Anzahl der Kontrollpunkte, die Art der Patchfläche und die Art der beim Tesselieren zu verwendenden Partitionierung.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-124">This includes information such as the number of control points, the type of patch face and the type of partitioning to use when tessellating.</span></span> <span data-ttu-id="8b8c8-125">Diese Informationen stehen als Deklarationen in der Regel am Anfang des Shadercodes.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-125">This information appears as declarations typically at the front of the shader code.</span></span>
-   <span data-ttu-id="8b8c8-126">Tesselationsfaktoren bestimmen, wie oft jeder Patch unterteilt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-126">Tessellation factors determine how much to subdivide each patch.</span></span>

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span data-ttu-id="8b8c8-127"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe</span><span class="sxs-lookup"><span data-stu-id="8b8c8-127"><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Output</span></span>


<span data-ttu-id="8b8c8-128">1 bis 32 Ausgabekontrollpunkte, die zusammen einen Patch bilden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-128">Between 1 and 32 output control points, which together make up a patch.</span></span>

-   <span data-ttu-id="8b8c8-129">Die Shaderausgabe umfasst 1 bis 32 Kontrollpunkte, unabhängig von der Anzahl der Tesselationsfaktoren.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-129">The shader output is between 1 and 32 control points, regardless of the number of tessellation factors.</span></span> <span data-ttu-id="8b8c8-130">Die Kontrollpunktausgabe eines Hull-Shaders kann von der Domain-Shader-Stufe weiterverarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-130">The control-points output from a hull shader can be consumed by the domain-shader stage.</span></span> <span data-ttu-id="8b8c8-131">Patchkonstanten können von einem Domain-Shader weiterverarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-131">Patch constant data can be consumed by a domain shader.</span></span> <span data-ttu-id="8b8c8-132">Tesselationsfaktoren können von der [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md) und der [Domain-Shader-Stufe (DS-Stufe) weiterverarbeitet werden](domain-shader-stage--ds-.md).</span><span class="sxs-lookup"><span data-stu-id="8b8c8-132">Tessellation factors can be consumed by the [Tessellator (TS) stage](tessellator-stage--ts-.md) and the [Domain Shader (DS) stage](domain-shader-stage--ds-.md).</span></span>
-   <span data-ttu-id="8b8c8-133">Wenn der Hull-Shader Randtesselationsfaktoren auf Werte ≤ 0 oder NaN setzt, wird der Patch nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-133">If the hull shader sets any edge tessellation factor to ≤ 0 or NaN, the patch will be culled (omitted).</span></span> <span data-ttu-id="8b8c8-134">Somit wird die Tessellatorstufe nur manchmal ausgeführt, der Domain-Shader nicht, und für den Patch wird keine sichtbare Ausgabe erstellt.</span><span class="sxs-lookup"><span data-stu-id="8b8c8-134">As a result, the tessellator stage may or may not run, the domain shader will not run, and no visible output will be produced for that patch.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="8b8c8-135"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="8b8c8-135"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


```
[patchsize(12)]
[patchconstantfunc(MyPatchConstantFunc)]
MyOutPoint main(uint Id : SV_ControlPointID,
     InputPatch<MyInPoint, 12> InPts)
{
     MyOutPoint result;
     
     ...
     
     result = TransformControlPoint( InPts[Id] );

     return result;
}
```

<span data-ttu-id="8b8c8-136">Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Hull-Shaders](https://msdn.microsoft.com/library/windows/desktop/ff476338).</span><span class="sxs-lookup"><span data-stu-id="8b8c8-136">See [How To: Create a Hull Shader](https://msdn.microsoft.com/library/windows/desktop/ff476338).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="8b8c8-137"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8b8c8-137"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="8b8c8-138">Grafikpipeline</span><span class="sxs-lookup"><span data-stu-id="8b8c8-138">Graphics pipeline</span></span>](graphics-pipeline.md)

 

 




