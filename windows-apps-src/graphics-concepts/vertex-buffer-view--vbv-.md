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
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8699424"
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

 

 




