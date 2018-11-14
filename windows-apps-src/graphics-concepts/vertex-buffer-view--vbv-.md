---
title: Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)
description: Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.
ms.assetid: 695115D2-9DA0-41F2-9416-33BFAB698129
keywords:
- Scheitelpunktpufferansicht (VBV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7956c7a03256da04e98a5b8f9a33951d7e0216d3
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6203955"
---
# <a name="vertex-buffer-view-vbv-and-index-buffer-view-ibv"></a><span data-ttu-id="b86d5-104">Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)</span><span class="sxs-lookup"><span data-stu-id="b86d5-104">Vertex buffer view (VBV) and Index buffer view (IBV)</span></span>


<span data-ttu-id="b86d5-105">Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.</span><span class="sxs-lookup"><span data-stu-id="b86d5-105">A vertex buffer holds data for a list of vertices.</span></span> <span data-ttu-id="b86d5-106">Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten.</span><span class="sxs-lookup"><span data-stu-id="b86d5-106">The data for each vertex can include position, color, normal vector, texture co-ordinates, and so on.</span></span> <span data-ttu-id="b86d5-107">Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.</span><span class="sxs-lookup"><span data-stu-id="b86d5-107">An index buffer holds integer indexes (offsets) into a vertex buffer, and is used to define and render an object made up of a subset of the full list of vertices.</span></span>

<span data-ttu-id="b86d5-108">Die Definition eines einzelnen Scheitelpunkts obliegt oft der Anwendung, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b86d5-108">The definition of a single vertex is often up to the application to define, such as:</span></span>

``` syntax
struct CUSTOMVERTEX { 
        FLOAT x, y, z;      // The position
        FLOAT nx, ny, nz;   // The normal
        DWORD color;        // RGBA color
        FLOAT tu, tv;       // The texture coordinates. 
}; 
```

<span data-ttu-id="b86d5-109">Die Definition von CUSTOMVERTEX würde dann an den Grafiktreiber übergeben werden, wenn Scheitelpunktpuffer erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b86d5-109">The definition of CUSTOMVERTEX would then be passed to the graphics driver when creating vertex buffers.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="b86d5-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b86d5-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="b86d5-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="b86d5-111">Views</span></span>](views.md)

 

 




