---
title: Zeilenstrips
description: Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Liniensegmenten besteht. Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen. Bei einem geschlossenes Polygon handelt es sich um ein Polygon, deren letzte Vertex über ein Liniensegment mit ihrem ersten Scheitelpunkt verbunden ist.
ms.assetid: 6E8C58E1-B463-44FD-A69F-81CCBF25D856
keywords:
- Zeilenstrips
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 869f0ac2b255c0dee231828f6d9064a917668821
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8197645"
---
# <a name="line-strips"></a><span data-ttu-id="65d3e-106">Zeilenstrips</span><span class="sxs-lookup"><span data-stu-id="65d3e-106">Line strips</span></span>


<span data-ttu-id="65d3e-107">Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Liniensegmenten besteht.</span><span class="sxs-lookup"><span data-stu-id="65d3e-107">A line strip is a primitive that is composed of connected line segments.</span></span> <span data-ttu-id="65d3e-108">Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="65d3e-108">Your application can use line strips for creating polygons that are not closed.</span></span> <span data-ttu-id="65d3e-109">Bei einem geschlossenes Polygon handelt es sich um ein Polygon, dessen letzter Vertex über ein Zeilensegment mit dem ersten Vertex verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="65d3e-109">A closed polygon is a polygon whose last vertex is connected to its first vertex by a line segment.</span></span> <span data-ttu-id="65d3e-110">Wenn die Anwendung Polygone auf Zeilenstrips basiert erstellt, ist nicht sichergestellt, dass die Vertizes notwendigerweise komplanar sind.</span><span class="sxs-lookup"><span data-stu-id="65d3e-110">If your application makes polygons based on line strips, the vertices are not guaranteed to be coplanar.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="65d3e-111"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="65d3e-111"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="65d3e-112">Die folgende Abbildungzeigt einen gerenderten Zeilenstrip.</span><span class="sxs-lookup"><span data-stu-id="65d3e-112">The following illustration shows a rendered line strip.</span></span>

![Abbildung eines Zeilenstrips](images/linstrip.gif)

<span data-ttu-id="65d3e-114">Der folgende Code zeigt, wie Vertizes für diesen Zeilenstrip erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="65d3e-114">The following code shows how to create vertices for this line strip.</span></span>

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

<span data-ttu-id="65d3e-115">Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen Zeilenstrip in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="65d3e-115">The code example below shows how to render a line strip in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_LINESTRIP, 0, 5 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="65d3e-116"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="65d3e-116"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="65d3e-117">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="65d3e-117">Primitives</span></span>](primitives.md)

 

 




