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
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6672149"
---
# <a name="vertex-buffer-view-vbv-and-index-buffer-view-ibv"></a>Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)


Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten. Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten. Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.

Die Definition eines einzelnen Scheitelpunkts obliegt oft der Anwendung, zum Beispiel:

``` syntax
struct CUSTOMVERTEX { 
        FLOAT x, y, z;      // The position
        FLOAT nx, ny, nz;   // The normal
        DWORD color;        // RGBA color
        FLOAT tu, tv;       // The texture coordinates. 
}; 
```

Die Definition von CUSTOMVERTEX würde dann an den Grafiktreiber übergeben werden, wenn Scheitelpunktpuffer erstellt werden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 




