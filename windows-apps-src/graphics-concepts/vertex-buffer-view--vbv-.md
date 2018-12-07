---
title: Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)
description: Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.
ms.assetid: 695115D2-9DA0-41F2-9416-33BFAB698129
keywords:
- Scheitelpunktpufferansicht (VBV)
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: cfb92c4f876d85388ce325f151408fe7b9e8d8b4
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8790521"
---
# <a name="vertex-buffer-view-vbv-and-index-buffer-view-ibv"></a><span data-ttu-id="3f094-104">Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)</span><span class="sxs-lookup"><span data-stu-id="3f094-104">Vertex buffer view (VBV) and Index buffer view (IBV)</span></span>


<span data-ttu-id="3f094-105">Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten.</span><span class="sxs-lookup"><span data-stu-id="3f094-105">A vertex buffer holds data for a list of vertices.</span></span> <span data-ttu-id="3f094-106">Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten.</span><span class="sxs-lookup"><span data-stu-id="3f094-106">The data for each vertex can include position, color, normal vector, texture co-ordinates, and so on.</span></span> <span data-ttu-id="3f094-107">Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.</span><span class="sxs-lookup"><span data-stu-id="3f094-107">An index buffer holds integer indexes (offsets) into a vertex buffer, and is used to define and render an object made up of a subset of the full list of vertices.</span></span>

<span data-ttu-id="3f094-108">Die Definition eines einzelnen Scheitelpunkts obliegt oft der Anwendung, zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3f094-108">The definition of a single vertex is often up to the application to define, such as:</span></span>

``` syntax
struct CUSTOMVERTEX { 
        FLOAT x, y, z;      // The position
        FLOAT nx, ny, nz;   // The normal
        DWORD color;        // RGBA color
        FLOAT tu, tv;       // The texture coordinates. 
}; 
```

<span data-ttu-id="3f094-109">Die Definition von CUSTOMVERTEX würde dann an den Grafiktreiber übergeben werden, wenn Scheitelpunktpuffer erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="3f094-109">The definition of CUSTOMVERTEX would then be passed to the graphics driver when creating vertex buffers.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="3f094-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3f094-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="3f094-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="3f094-111">Views</span></span>](views.md)

 

 




