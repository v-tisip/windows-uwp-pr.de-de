---
title: Dreieckslisten
description: Eine Dreiecksliste ist eine Liste isolierter Dreiecke. Die isolierten Dreiecke können sich nahe beieinander befinden oder nicht. Eine Dreiecksliste muss mindestens drei Scheitelpunkte enthalten, und die Gesamtzahl der Scheitelpunkte muss durch drei teilbar sein.
ms.assetid: BC50D532-9E9C-4AAE-B466-9E8C4AD1862A
keywords:
- Dreieckslisten
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 4f5c8c7354ef0f7e9bd4878e4d78aa045ab7fbd0
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6260587"
---
# <a name="triangle-lists"></a><span data-ttu-id="77421-106">Dreieckslisten</span><span class="sxs-lookup"><span data-stu-id="77421-106">Triangle lists</span></span>


<span data-ttu-id="77421-107">Eine Dreiecksliste ist eine Liste isolierter Dreiecke.</span><span class="sxs-lookup"><span data-stu-id="77421-107">A triangle list is a list of isolated triangles.</span></span> <span data-ttu-id="77421-108">Die isolierten Dreiecke können sich nahe beieinander befinden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="77421-108">The isolated triangles might or might not be near each other.</span></span> <span data-ttu-id="77421-109">Eine Dreiecksliste muss mindestens drei Scheitelpunkte enthalten, und die Gesamtzahl der Scheitelpunkte muss durch drei teilbar sein.</span><span class="sxs-lookup"><span data-stu-id="77421-109">A triangle list must have at least three vertices and the total number of vertices must be divisible by three.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="77421-110"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="77421-110"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="77421-111">Verwenden Sie Dreieckslisten zur Erstellung eines Objekts, das aus nicht zusammenhängenden Teilen besteht.</span><span class="sxs-lookup"><span data-stu-id="77421-111">Use triangle lists to create an object that is composed of disjoint pieces.</span></span> <span data-ttu-id="77421-112">Beispielsweise ist eine Möglichkeit zur Erstellung einer Kraftfeldwand in einem 3D-Spiel eine umfangreiche Liste mit kleinen, nicht verbundenen Dreiecken.</span><span class="sxs-lookup"><span data-stu-id="77421-112">For instance, one way to create a force-field wall in a 3D game is to specify a large list of small, unconnected triangles.</span></span> <span data-ttu-id="77421-113">Wenden Sie dann ein Material und eine Struktur an, die den Eindruck erweckt, dass sie Licht zu der Dreiecksliste aussendet.</span><span class="sxs-lookup"><span data-stu-id="77421-113">Then apply a material and texture that appears to emit light to the triangle list.</span></span> <span data-ttu-id="77421-114">Jedes Dreieck in der Wand leuchtet jetzt auf.</span><span class="sxs-lookup"><span data-stu-id="77421-114">Each triangle in the wall appears to glow.</span></span> <span data-ttu-id="77421-115">Die Szene hinter der Wand wird teilweise durch die Lücken zwischen den Dreiecken sichtbar, was ein Spieler beim betrachten eines Kraftfelds auch erwartet.</span><span class="sxs-lookup"><span data-stu-id="77421-115">The scene behind the wall becomes partially visible through the gaps between the triangles, as a player might expect when looking at a force field.</span></span>

<span data-ttu-id="77421-116">Dreieckslisten sind auch nützlich für das Erstellen von Grundtypen, die scharfe Kanten haben und mit Gouraud-Schattierung versehen sind.</span><span class="sxs-lookup"><span data-stu-id="77421-116">Triangle lists are also useful for creating primitives that have sharp edges and are shaded with Gouraud shading.</span></span> <span data-ttu-id="77421-117">Vgl. [Seiten- und Scheitelpunkt-Normalvektoren](face-and-vertex-normal-vectors.md).</span><span class="sxs-lookup"><span data-stu-id="77421-117">See [Face and vertex normal vectors](face-and-vertex-normal-vectors.md).</span></span>

<span data-ttu-id="77421-118">Die folgende Abbildungzeigt eine gerenderte Dreiecksliste.</span><span class="sxs-lookup"><span data-stu-id="77421-118">The following illustration depicts a rendered triangle list.</span></span>

![Illustration einer gerenderten Dreiecksliste](images/trilist.png)

<span data-ttu-id="77421-120">Der folgende Code zeigt, wie Scheitelpunkte für diese Dreiecksliste erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="77421-120">The following code shows how to create vertices for this triangle list.</span></span>

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

<span data-ttu-id="77421-121">Im folgenden Codebeispiel wird veranschaulicht, wie Sie diese Dreiecksliste in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="77421-121">The code example below shows how to render this triangle list in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to a device interface.
//
d3dDevice->DrawPrimitive( D3DPT_TRIANGLELIST, 0, 2 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="77421-122"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="77421-122"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="77421-123">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="77421-123">Primitives</span></span>](primitives.md)

 

 




