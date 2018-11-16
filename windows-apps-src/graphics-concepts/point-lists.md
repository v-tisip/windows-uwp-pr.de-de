---
title: Punktelisten
description: Eine Punkteliste ist eine Sammlung von Scheitelpunkten, die als isolierte Punkte dargestellt werden. Die Anwendung kann Punktelisten in 3D-Szenen für Sternenfelder oder gepunktete Linien auf der Oberfläche eines Polygons verwenden.
ms.assetid: 332954AE-019F-4A91-B773-E3A7C92F3297
keywords:
- Punktelisten
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b4c2e0f6e99099df4bdda9452521acf3b0cd2b8f
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6855797"
---
# <a name="point-lists"></a><span data-ttu-id="f9536-105">Punktelisten</span><span class="sxs-lookup"><span data-stu-id="f9536-105">Point lists</span></span>


<span data-ttu-id="f9536-106">Eine Punkteliste ist eine Sammlung von Scheitelpunkten, die als isolierte Punkte dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f9536-106">A point list is a collection of vertices that are rendered as isolated points.</span></span> <span data-ttu-id="f9536-107">Die Anwendung kann Punktelisten in 3D-Szenen für Sternenfelder oder gepunktete Linien auf der Oberfläche eines Polygons verwenden.</span><span class="sxs-lookup"><span data-stu-id="f9536-107">Your application can use point lists in 3D scenes for star fields, or dotted lines on the surface of a polygon.</span></span>

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="f9536-108"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="f9536-108"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="f9536-109">Die folgende Abbildungzeigt eine gerenderte Punkteliste.</span><span class="sxs-lookup"><span data-stu-id="f9536-109">The following illustration depicts a rendered point list.</span></span>

![Abbildungeiner Punkteliste](images/pointlst.png)

<span data-ttu-id="f9536-111">Die Anwendung kann Materialien und Texturen auf eine Punkteliste anwenden.</span><span class="sxs-lookup"><span data-stu-id="f9536-111">Your application can apply materials and textures to a point list.</span></span> <span data-ttu-id="f9536-112">Die Farben im Material oder der Textur werden nur bei dem gezeichneten Punkt angezeigt, nicht an anderen Stellen zwischen den Punkten.</span><span class="sxs-lookup"><span data-stu-id="f9536-112">The colors in the material or texture appear only at the points drawn, and not anywhere between the points.</span></span>

<span data-ttu-id="f9536-113">Der folgende Code zeigt, wie Scheitelpunkte für diese Punkteliste erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="f9536-113">The following code shows how to create vertices for this point list.</span></span>

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

<span data-ttu-id="f9536-114">Im folgenden Codebeispiel wird veranschaulicht, wie Sie diese Punkteliste in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="f9536-114">The code example below shows how to render this point list in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_POINTLIST, 0, 6 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="f9536-115"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f9536-115"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="f9536-116">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="f9536-116">Primitives</span></span>](primitives.md)

 

 




