---
title: Zeilenstrips
description: "Ein Zeilenstrip ist ein Grundtyp, der aus verbundenen Zeilensegmenten besteht. Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen. Bei einem geschlossenes Polygon handelt es sich um ein Polygon, deren letzte Vertex über ein Liniensegment mit ihrem ersten Scheitelpunkt verbunden ist."
ms.assetid: 6E8C58E1-B463-44FD-A69F-81CCBF25D856
keywords:
- Zeilenstrips
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 5fe51d8e07f064da6ef3ba1ad32060a014a31d97
ms.lasthandoff: 02/07/2017

---

# <a name="line-strips"></a>Zeilenstrips


Ein Zeilenstrip ist eine Grundform, die aus verbundenen Zeilensegmenten besteht. Die Anwendung kann Zeilenstrips verwenden, um offene Polygone zu erstellen. Bei einem geschlossenes Polygon handelt es sich um ein Polygon, dessen letzter Vertex über ein Zeilensegment mit dem ersten Vertex verbunden ist. Wenn die Anwendung Polygone auf Zeilenstrips basiert erstellt, ist nicht sichergestellt, dass die Vertizes notwendigerweise komplanar sind.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


Die folgende Abbildung zeigt einen gerenderten Zeilenstrip.

![Abbildung eines Zeilenstrips](images/linstrip.gif)

Der folgende Code zeigt, wie Vertizes für diesen Zeilenstrip erstellt werden.

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

Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen Zeilenstrip in Direct3D rendern.

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_LINESTRIP, 0, 5 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Grundtypen](primitives.md)

 

 





