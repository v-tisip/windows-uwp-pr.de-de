---
title: Zeilenlisten
description: Bei einer Zeilenliste handelt es sich um eine Liste isolierter, gerader Liniensegmente. Zeilenlisten sind hilfreich für Aufgaben wie das Hinzufügen von Schneeregen oder Starkregen zu einer 3D-Szene. Anwendungen erstellen eine Zeilenliste, indem Sie eine Reihe von Vertizes ausfüllen.
ms.assetid: 42BF32A1-3535-42A3-82C5-3945CB309F2C
keywords:
- Zeilenlisten
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 5a514fb072dd95b9de2c29e097e8387c0f1068a4
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7295913"
---
# <a name="line-lists"></a>Zeilenlisten


Bei einer Zeilenliste handelt es sich um eine Liste isolierter, gerader Liniensegmente. Zeilenlisten sind hilfreich für Aufgaben wie das Hinzufügen von Schneeregen oder Starkregen zu einer 3D-Szene. Anwendungen erstellen eine Zeilenliste, indem Sie eine Reihe von Vertizes ausfüllen. Beachten Sie, dass die Anzahl der Vertizes in einer Zeilenliste eine gerade Zahl größer oder gleich 2 sein muss.

-   [Beispiel](#example)
-   [Verwandte Themen](#related-topics)

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


Die folgende Abbildungzeigt eine gerenderte Zeilenliste.

![Abbildungeiner Zeilenliste](images/linelst.png)

Sie können einer Zeilenliste Materialien und Texturen zuweisen. Die Farben des Materials oder der Textur erscheinen nur entlang der gezogenen Zeilen, nicht an einer beliebigen Stelle zwischen den Zeilen.

Der folgende Code zeigt, wie Vertizes für diese Zeilenliste erstellt werden.

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

Im folgenden Codebeispiel wird veranschaulicht, wie Sie eine Zeilenliste in Direct3D rendern.

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_LINELIST, 0, 3 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Grundtypen](primitives.md)

 

 




