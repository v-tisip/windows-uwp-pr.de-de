---
title: Zeilenstrips
description: "Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Zeilensegmenten besteht. Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen. Bei einem geschlossenes Polygon handelt es sich um ein Polygon, deren letzte Vertex über ein Liniensegment mit ihrem ersten Scheitelpunkt verbunden ist."
ms.assetid: 6E8C58E1-B463-44FD-A69F-81CCBF25D856
keywords: Zeilenstrips
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 7eec406faf1f695a473154dd23322bcdf9189049
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="line-strips"></a><span data-ttu-id="0b838-106">Zeilenstrips</span><span class="sxs-lookup"><span data-stu-id="0b838-106">Line strips</span></span>


<span data-ttu-id="0b838-107">Ein Zeilenstrip ist eine Grundform, die aus verbundenen Zeilensegmenten besteht.</span><span class="sxs-lookup"><span data-stu-id="0b838-107">A line strip is a primitive that is composed of connected line segments.</span></span> <span data-ttu-id="0b838-108">Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0b838-108">Your application can use line strips for creating polygons that are not closed.</span></span> <span data-ttu-id="0b838-109">Bei einem geschlossenes Polygon handelt es sich um ein Polygon, dessen letzter Vertex über ein Zeilensegment mit dem ersten Vertex verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="0b838-109">A closed polygon is a polygon whose last vertex is connected to its first vertex by a line segment.</span></span> <span data-ttu-id="0b838-110">Wenn die Anwendung Polygone auf Zeilenstrips basiert erstellt, ist nicht sichergestellt, dass die Vertizes notwendigerweise komplanar sind.</span><span class="sxs-lookup"><span data-stu-id="0b838-110">If your application makes polygons based on line strips, the vertices are not guaranteed to be coplanar.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="0b838-111"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="0b838-111"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="0b838-112">Die folgende Abbildungzeigt einen gerenderten Zeilenstrip.</span><span class="sxs-lookup"><span data-stu-id="0b838-112">The following illustration shows a rendered line strip.</span></span>

![Abbildung eines Zeilenstrips](images/linstrip.gif)

<span data-ttu-id="0b838-114">Der folgende Code zeigt, wie Vertizes für diesen Zeilenstrip erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0b838-114">The following code shows how to create vertices for this line strip.</span></span>

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

<span data-ttu-id="0b838-115">Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen Zeilenstrip in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="0b838-115">The code example below shows how to render a line strip in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_LINESTRIP, 0, 5 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="0b838-116"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0b838-116"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="0b838-117">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="0b838-117">Primitives</span></span>](primitives.md)

 

 




