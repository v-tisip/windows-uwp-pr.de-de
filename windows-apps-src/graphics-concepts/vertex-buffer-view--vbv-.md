---
title: Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)
description: "Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten."
ms.assetid: 695115D2-9DA0-41F2-9416-33BFAB698129
keywords: Scheitelpunktpufferansicht (VBV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: da0b8e8841e7c9df88ea22ba637d7236090e7ee5
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vertex-buffer-view-vbv-and-index-buffer-view-ibv"></a><span data-ttu-id="2414a-104">Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)</span><span class="sxs-lookup"><span data-stu-id="2414a-104">Vertex buffer view (VBV) and Index buffer view (IBV)</span></span>


<span data-ttu-id="2414a-105">Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.</span><span class="sxs-lookup"><span data-stu-id="2414a-105">A vertex buffer holds data for a list of vertices.</span></span> <span data-ttu-id="2414a-106">Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten.</span><span class="sxs-lookup"><span data-stu-id="2414a-106">The data for each vertex can include position, color, normal vector, texture co-ordinates, and so on.</span></span> <span data-ttu-id="2414a-107">Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.</span><span class="sxs-lookup"><span data-stu-id="2414a-107">An index buffer holds integer indexes (offsets) into a vertex buffer, and is used to define and render an object made up of a subset of the full list of vertices.</span></span>

<span data-ttu-id="2414a-108">Die Definition eines einzelnen Scheitelpunkts obliegt oft der Anwendung, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2414a-108">The definition of a single vertex is often up to the application to define, such as:</span></span>

``` syntax
struct CUSTOMVERTEX { 
        FLOAT x, y, z;      // The position
        FLOAT nx, ny, nz;   // The normal
        DWORD color;        // RGBA color
        FLOAT tu, tv;       // The texture coordinates. 
}; 
```

<span data-ttu-id="2414a-109">Die Definition von CUSTOMVERTEX würde dann an den Grafiktreiber übergeben werden, wenn Scheitelpunktpuffer erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="2414a-109">The definition of CUSTOMVERTEX would then be passed to the graphics driver when creating vertex buffers.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="2414a-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2414a-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="2414a-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="2414a-111">Views</span></span>](views.md)

 

 




