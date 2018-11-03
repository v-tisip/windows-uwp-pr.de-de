---
title: Dreieckstreifen
description: Ein Dreiecksstrip ist eine Reihe verbundener Dreiecke. Da die Dreiecke verbunden sind, muss die Anwendung nicht alle drei Scheitelpunkte für jedes Dreieck wiederholt angeben.
ms.assetid: BACC74C5-14E5-4ECC-9139-C2FD1808DB82
keywords:
- Dreieckstreifen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: f60f0f65868d4dec67bf77a329d4b952c20ec44a
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5996542"
---
# <a name="triangle-strips"></a><span data-ttu-id="61985-105">Dreieckstreifen</span><span class="sxs-lookup"><span data-stu-id="61985-105">Triangle strips</span></span>


<span data-ttu-id="61985-106">Ein Dreiecksstrip ist eine Reihe verbundener Dreiecke.</span><span class="sxs-lookup"><span data-stu-id="61985-106">A triangle strip is a series of connected triangles.</span></span> <span data-ttu-id="61985-107">Da die Dreiecke verbunden sind, muss die Anwendung nicht alle drei Scheitelpunkte für jedes Dreieck wiederholt angeben.</span><span class="sxs-lookup"><span data-stu-id="61985-107">Because the triangles are connected, the application does not need to repeatedly specify all three vertices for each triangle.</span></span> <span data-ttu-id="61985-108">So benötigen Sie beispielsweise nur sieben Scheitelpunkte zur Definition des folgenden Dreieckstreifens.</span><span class="sxs-lookup"><span data-stu-id="61985-108">For example, you need only seven vertices to define the following triangle strip.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="61985-109"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="61985-109"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


![Illustration eins Dreieckstreifens mit sieben Scheitelpunkten](images/tristrip.png)

<span data-ttu-id="61985-111">Das System verwendet die Scheitelpunkte v1, v2 und v3 zum Zeichnen des ersten Dreiecks, v2, v4 und v3 für das zweite v3, v4 und v5 für das dritte. v4, v6 und v5 für das vierte Dreieck und so weiter.</span><span class="sxs-lookup"><span data-stu-id="61985-111">The system uses vertices v1, v2, and v3 to draw the first triangle; v2, v4, and v3 to draw the second triangle; v3, v4, and v5 to draw the third; v4, v6, and v5 to draw the fourth; and so on.</span></span> <span data-ttu-id="61985-112">Beachten Sie, dass die Scheitelpunkte des zweiten und vierten Dreiecke die Reihenfolge verletzen. Dies ist notwendig, um sicherzustellen, dass alle Dreiecke im Uhrzeigersinn gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="61985-112">Notice that the vertices of the second and fourth triangles are out of order; this is required to make sure that all the triangles are drawn in a clockwise orientation.</span></span>

<span data-ttu-id="61985-113">Die meisten Objekte in 3D-Szenen bestehen aus Dreieckstreifen.</span><span class="sxs-lookup"><span data-stu-id="61985-113">Most objects in 3D scenes are composed of triangle strips.</span></span> <span data-ttu-id="61985-114">Der Grund dafür ist, dass mit Dreieckstreifen komplexe Objekte so zusammengesetzt werden können, dass Speicherplatz und Verarbeitungszeit dabei effizient genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="61985-114">This is because triangle strips can be used to specify complex objects in a way that makes efficient use of memory and processing time.</span></span>

<span data-ttu-id="61985-115">Die folgende Abbildungzeigt einen gerenderte Dreieckstreifen.</span><span class="sxs-lookup"><span data-stu-id="61985-115">The following illustration depicts a rendered triangle strip.</span></span>

![Illustration eines gerenderten Dreieckstreifens](images/tstrip2.png)

<span data-ttu-id="61985-117">Der folgende Code zeigt, wie Scheitelpunkte für diesen Dreieckstreifen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="61985-117">The following code shows how to create vertices for this triangle strip.</span></span>

```
struct CUSTOMVERTEX
{
float x,y,z;
};

CUSTOMVERTEX Vertices[] = 
{
    {-5.0, -5.0, 0.0},
    { 0.0,  5.0, 0.0},
    { 5.0, -5.0, 0.0},
    {10.0,  5.0, 0.0},
    {15.0, -5.0, 0.0},
    {20.0,  5.0, 0.0}
};
```

<span data-ttu-id="61985-118">Im folgenden Codebeispiel wird veranschaulicht, wie Sie diesen Dreieckstreifen in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="61985-118">The code example below shows how to render this triangle strip in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to a device interface.
//
d3dDevice->DrawPrimitive( D3DPT_TRIANGLESTRIP, 0, 4);
```

## <a name="span-idpolygonsspanspan-idpolygonsspanspan-idpolygonsspanpolygons"></a><span data-ttu-id="61985-119"><span id="Polygons"></span><span id="polygons"></span><span id="POLYGONS"></span>Vielecke</span><span class="sxs-lookup"><span data-stu-id="61985-119"><span id="Polygons"></span><span id="polygons"></span><span id="POLYGONS"></span>Polygons</span></span>


<span data-ttu-id="61985-120">Häufig werden Dreieckstreifen verwendet, um Vielecke zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="61985-120">Often, triangle strips are used to build polygons.</span></span> <span data-ttu-id="61985-121">Ein Vieleck ist eine geschlossene 3D-Figur, die von mindestens drei Scheitelpunkten begrenzt wird.</span><span class="sxs-lookup"><span data-stu-id="61985-121">A polygon is a closed 3D figure delineated by at least three vertices.</span></span> <span data-ttu-id="61985-122">Das einfachste Vieleck ist ein Dreieck.</span><span class="sxs-lookup"><span data-stu-id="61985-122">The simplest polygon is a triangle.</span></span> <span data-ttu-id="61985-123">Microsoft Direct3D verwendet Dreiecke zur Erstellung der meisten Vielecke, da alle drei Scheitelpunkte in einem Dreieck garantiert auf der gleichen Ebene liegen.</span><span class="sxs-lookup"><span data-stu-id="61985-123">Microsoft Direct3D uses triangles to compose most of its polygons because all three vertices in a triangle are guaranteed to be coplanar.</span></span> <span data-ttu-id="61985-124">Das Rendern von nicht-planaren Scheitelpunkten ist ineffizient.</span><span class="sxs-lookup"><span data-stu-id="61985-124">Rendering nonplanar vertices is inefficient.</span></span> <span data-ttu-id="61985-125">Sie können Dreiecke zu großen, komplexen Vielecken und Gittern kombinieren.</span><span class="sxs-lookup"><span data-stu-id="61985-125">You can combine triangles to form large, complex polygons and meshes.</span></span>

<span data-ttu-id="61985-126">Die folgende Abbildung zeigt einen Würfel.</span><span class="sxs-lookup"><span data-stu-id="61985-126">The following illustration shows a cube.</span></span> <span data-ttu-id="61985-127">Je zwei Dreiecke bilden die einzelnen Flächen des Würfels.</span><span class="sxs-lookup"><span data-stu-id="61985-127">Two triangles form each face of the cube.</span></span> <span data-ttu-id="61985-128">Der gesamte Satz von Dreiecken bildet einen kubischen Grundtyp.</span><span class="sxs-lookup"><span data-stu-id="61985-128">The entire set of triangles forms one cubic primitive.</span></span> <span data-ttu-id="61985-129">Sie können Texturen auf den Oberflächen von Grundtypen anwenden, um dafür zu sorgen, dass sie wie eine einzige massive Form wirken.</span><span class="sxs-lookup"><span data-stu-id="61985-129">You can apply textures to the surfaces of primitives to make them appear to be a single solid form.</span></span> <span data-ttu-id="61985-130">Weitere Informationen finden Sie unter [Texturen](textures.md).</span><span class="sxs-lookup"><span data-stu-id="61985-130">For details, see [Textures](textures.md).</span></span>

![Illustration eines Würfels mit zwei Dreiecken auf jeder Seite](images/cube3d.png)

<span data-ttu-id="61985-132">Sie können mit Dreiecken auch Grundtypen erstellen, deren Oberflächen wie glatte Kurven aussehen.</span><span class="sxs-lookup"><span data-stu-id="61985-132">You can also use triangles to create primitives whose surfaces appear to be smooth curves.</span></span> <span data-ttu-id="61985-133">Die folgende Abbildungzeigt die Simulation einer Kugel mithilfe von Dreiecken.</span><span class="sxs-lookup"><span data-stu-id="61985-133">The following illustration shows how a sphere can be simulated with triangles.</span></span> <span data-ttu-id="61985-134">Nach der Anwendung eines Materials kann die Kugel beim Rendern so gestaltet werden, dass sie rund wirkt.</span><span class="sxs-lookup"><span data-stu-id="61985-134">After a material is applied, the sphere can be made to look curved when it is rendered.</span></span>

![Illustration einer mithilfe von Dreiecken simulierten Kugel](images/sphere3d.png)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="61985-136"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="61985-136"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="61985-137">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="61985-137">Primitives</span></span>](primitives.md)

 

 




