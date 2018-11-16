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
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6974585"
---
# <a name="line-lists"></a><span data-ttu-id="50b20-106">Zeilenlisten</span><span class="sxs-lookup"><span data-stu-id="50b20-106">Line lists</span></span>


<span data-ttu-id="50b20-107">Bei einer Zeilenliste handelt es sich um eine Liste isolierter, gerader Liniensegmente.</span><span class="sxs-lookup"><span data-stu-id="50b20-107">A line list is a list of isolated, straight line segments.</span></span> <span data-ttu-id="50b20-108">Zeilenlisten sind hilfreich für Aufgaben wie das Hinzufügen von Schneeregen oder Starkregen zu einer 3D-Szene.</span><span class="sxs-lookup"><span data-stu-id="50b20-108">Line lists are useful for such tasks as adding sleet or heavy rain to a 3D scene.</span></span> <span data-ttu-id="50b20-109">Anwendungen erstellen eine Zeilenliste, indem Sie eine Reihe von Vertizes ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="50b20-109">Applications create a line list by filling an array of vertices.</span></span> <span data-ttu-id="50b20-110">Beachten Sie, dass die Anzahl der Vertizes in einer Zeilenliste eine gerade Zahl größer oder gleich 2 sein muss.</span><span class="sxs-lookup"><span data-stu-id="50b20-110">Note that the number of vertices in a line list must be an even number greater than or equal to two.</span></span>

-   [<span data-ttu-id="50b20-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="50b20-111">Example</span></span>](#example)
-   [<span data-ttu-id="50b20-112">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="50b20-112">Related topics</span></span>](#related-topics)

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="50b20-113"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="50b20-113"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="50b20-114">Die folgende Abbildungzeigt eine gerenderte Zeilenliste.</span><span class="sxs-lookup"><span data-stu-id="50b20-114">The following illustration shows a rendered line list.</span></span>

![Abbildungeiner Zeilenliste](images/linelst.png)

<span data-ttu-id="50b20-116">Sie können einer Zeilenliste Materialien und Texturen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="50b20-116">You can apply materials and textures to a line list.</span></span> <span data-ttu-id="50b20-117">Die Farben des Materials oder der Textur erscheinen nur entlang der gezogenen Zeilen, nicht an einer beliebigen Stelle zwischen den Zeilen.</span><span class="sxs-lookup"><span data-stu-id="50b20-117">The colors in the material or texture appear only along the lines drawn, not at any point in between the lines.</span></span>

<span data-ttu-id="50b20-118">Der folgende Code zeigt, wie Vertizes für diese Zeilenliste erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="50b20-118">The following code shows how to create vertices for this line list.</span></span>

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

<span data-ttu-id="50b20-119">Im folgenden Codebeispiel wird veranschaulicht, wie Sie eine Zeilenliste in Direct3D rendern.</span><span class="sxs-lookup"><span data-stu-id="50b20-119">The code example below shows how to render a line list in Direct3D.</span></span>

```
//
// It is assumed that d3dDevice is a valid
// pointer to an IDirect3DDevice interface.
//
d3dDevice->DrawPrimitive( D3DPT_LINELIST, 0, 3 );
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="50b20-120"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="50b20-120"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="50b20-121">Grundtypen</span><span class="sxs-lookup"><span data-stu-id="50b20-121">Primitives</span></span>](primitives.md)

 

 




