---
title: Bilineare Texturfilterung
description: Die bilineare Filterung berechnet den gewichteten Mittelwert der 4Texel, die dem Sampling-Punkt am nächsten liegen.
ms.assetid: 0851AD28-8246-4547-A663-47884DDDFC3E
keywords:
- Bilineare Texturfilterung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 48e16162a76b1a599c1a43e763243be4348810af
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6667367"
---
# <a name="bilinear-texture-filtering"></a><span data-ttu-id="98e56-104">Bilineare Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="98e56-104">Bilinear texture filtering</span></span>


<span data-ttu-id="98e56-105">Die *bilineare Filterung* berechnet den gewichteten Durchschnitt der 4Texel, die dem Sampling-Punkt am nächsten liegen.</span><span class="sxs-lookup"><span data-stu-id="98e56-105">*Bilinear filtering* calculates the weighted average of the 4 texels closest to the sampling point.</span></span> <span data-ttu-id="98e56-106">Diese Filtermethode ist präziser und gängiger als das Filtern am nächstgelegenen Punkt.</span><span class="sxs-lookup"><span data-stu-id="98e56-106">This filtering approach is more accurate and common than nearest-point filtering.</span></span> <span data-ttu-id="98e56-107">Dieser Ansatz ist effizient, da er in moderner Grafikhardware implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="98e56-107">This approach is efficient because it is implemented in modern graphics hardware.</span></span>


## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span data-ttu-id="98e56-108"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel</span><span class="sxs-lookup"><span data-stu-id="98e56-108"><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Example</span></span>


<span data-ttu-id="98e56-109">Texturen werden immer linear behandelt, von (0,0, 0,0) in der oberen linken Ecke bis (1,0, 1,0) in der unteren rechten Ecke.</span><span class="sxs-lookup"><span data-stu-id="98e56-109">Textures are always linearly addressed from (0.0, 0.0) at the top-left corner to (1.0, 1.0) at the bottom-right corner.</span></span> <span data-ttu-id="98e56-110">Die lineare Texturadressierung wird in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="98e56-110">Linear addressing of a texture is shown in the following illustration.</span></span>

![Abbildung einer 4x4-Textur mit einfarbigen Farbblöcken](images/bilinear-fig7a.png)

<span data-ttu-id="98e56-112">Texturen werden in der Regel als einfarbige Farbblöcke dargestellt, obwohl man sich Texturen genauso wie Rasteranzeige vorstellen sollte: jedes Texel wird genau in der Mitte einer Rasterzelle definiert, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="98e56-112">Textures are usually represented as if they were composed of solid blocks of color, but it's actually more correct to think of textures the same way you should think of the raster display: Each texel is defined at the exact center of a grid cell, as shown in the following illustration.</span></span>

![Abbildung einer 4×4-Textur mit in der Mitte der Rasterzelle definierten Texels](images/bilinear-fig7b.png)

<span data-ttu-id="98e56-114">Wenn Sie den Texturen-Sampler nach der Farbe dieser Textur in UV-Koordinaten fragen, (0,375, 0,375) erhalten Sie die Volltonfarbe Rot (255, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="98e56-114">If you ask the texture sampler for this texture's color at UV coordinates (0.375, 0.375) you'll get solid red (255, 0, 0).</span></span> <span data-ttu-id="98e56-115">Das ergibt daher Sinn, da die Mitte der roten Texel-Zelle bei UV (0,375, 0,375) liegt.</span><span class="sxs-lookup"><span data-stu-id="98e56-115">That makes sense because the center of the red texel cell is at UV (0.375, 0.375).</span></span> <span data-ttu-id="98e56-116">Was aber, wenn Sie den Sampler nach der Texturfarbe auf UV (0,25, 0,25) fragen?</span><span class="sxs-lookup"><span data-stu-id="98e56-116">What if you ask the sampler for the texture's color at UV (0.25, 0.25)?</span></span> <span data-ttu-id="98e56-117">Dies ist nicht einfach, da der Punkt auf UV (0,25, 0,25) genau an der Grenze von 4 Texeln liegt.</span><span class="sxs-lookup"><span data-stu-id="98e56-117">That's not as easy, because the point at UV (0.25, 0.25) lies at the exact corner of 4 texels.</span></span>

<span data-ttu-id="98e56-118">Die einfachste Methode ist hier, dass der Sampler die Farbe des nächstliegenden Texel zurück gibt. Dies wird als Punktfilterung bezeichnet (Infos finden Sie unter [Sampling am nächstgelegenen Punkt](nearest-point-sampling.md)). Dies ist generell aufgrund von körnigen oder „eckigen” Ergebnisse unerwünscht.</span><span class="sxs-lookup"><span data-stu-id="98e56-118">The simplest scheme is simply to have the sampler return the color of the closest texel; this is called Point filtering (see [Nearest-point sampling](nearest-point-sampling.md)), and is usually undesirable due to grainy or blocky results.</span></span> <span data-ttu-id="98e56-119">Beim Filtern am nächstgelegenen Punkt stellen Punktsamples der Textur bei UV (0,25, 0,25) ein ganz anderes Problem dar: es gibt vier Texel mit dem gleichen Abstand vom Samplingpunkt, daher gibt es kein einziges naheliegendes Texel.</span><span class="sxs-lookup"><span data-stu-id="98e56-119">Point-sampling our texture at UV (0.25, 0.25) shows another subtle problem with nearest-point filtering: there are four texels equidistant from the sampling point, so there's no single nearest texel.</span></span> <span data-ttu-id="98e56-120">Eines dieser vier Texel wird als die zurückgegebene Farbe ausgewählt, doch die Auswahl hängt der Abrundung der Koordinate ab, was störende Artefakte einbringen kann (lesen Sie den Artikel „Sampling am nächstgelegenen Punkt” in SDK).</span><span class="sxs-lookup"><span data-stu-id="98e56-120">One of those four texels will be chosen as the returned color, but the selection depends on how the coordinate is rounded, which may introduce tearing artifacts (see the Nearest-Point Sampling article in the SDK).</span></span>

<span data-ttu-id="98e56-121">Eine etwas genauere und häufiger verwendete Filtermethode ist das Berechnen des gewichteten Mittelwerts der 4Texel, die dem Samplingpunkt am nächsten liegen. Dies wird als *Bilineare Filterung* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="98e56-121">A slightly more accurate and more common filtering scheme is to calculate the weighted average of the 4 texels closest to the sampling point; this is called *Bilinear filtering*.</span></span> <span data-ttu-id="98e56-122">Der zusätzliche Rechenaufwand für die bilineare Filterung ist in der Regel unerheblich, da diese Routine in moderner Grafikhardware verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="98e56-122">The extra computational cost for Bilinear filtering is usually negligible because this routine is implemented in modern graphics hardware.</span></span> <span data-ttu-id="98e56-123">Hier sind die Farben, die wir an verschiedenen Sampling-Punkten mit bilinearer Filterung erhalten:</span><span class="sxs-lookup"><span data-stu-id="98e56-123">Here are the colors we get at a few different sample points using bilinear filtering:</span></span>

```
UV: (0.5, 0.5)
```

<span data-ttu-id="98e56-124">Dieser Punkt liegt genau an der Grenze zwischen roten, grünen, blauen und weißen Texel.</span><span class="sxs-lookup"><span data-stu-id="98e56-124">This point is at the exact border between red, green, blue, and white texels.</span></span> <span data-ttu-id="98e56-125">Die vom Sampler zurückgegebene Farbe ist Grau:</span><span class="sxs-lookup"><span data-stu-id="98e56-125">The color the sampler returns is gray:</span></span>

```
  0.25 * (255, 0, 0)
  0.25 * (0, 255, 0) 
  0.25 * (0, 0, 255) 
## + 0.25 * (255, 255, 255) 
------------------------
= (128, 128, 128)
```

```
UV: (0.5, 0.375)
```

<span data-ttu-id="98e56-126">Dieser Punkt liegt im Mittelwert des Grenzpunkts zwischen roten und grünen Texel.</span><span class="sxs-lookup"><span data-stu-id="98e56-126">This point is at the midpoint of the border between red and green texels.</span></span> <span data-ttu-id="98e56-127">Die vom Sampler zurückgegebene Farbe ist gelb-grau (beachten Sie, dass der blaue und weiße Texel auf 0 skaliert werden):</span><span class="sxs-lookup"><span data-stu-id="98e56-127">The color the sampler returns is yellow-gray (note that the contributions of the blue and white texels are scaled to 0):</span></span>

```
  0.5 * (255, 0, 0)
  0.5 * (0, 255, 0) 
  0.0 * (0, 0, 255) 
## + 0.0 * (255, 255, 255) 
------------------------
= (128, 128, 0)
```

```
UV: (0.375, 0.375)
```

<span data-ttu-id="98e56-128">Dies ist die Adresse des rote Texels in der zurückgegebene Farbe (alle anderen Texel in der Filterberechnung werden auf 0 angepasst):</span><span class="sxs-lookup"><span data-stu-id="98e56-128">This is the address of the red texel, which is the returned color (all other texels in the filtering calculation are weighted to 0):</span></span>

```
  1.0 * (255, 0, 0)
  0.0 * (0, 255, 0) 
  0.0 * (0, 0, 255) 
## + 0.0 * (255, 255, 255) 
------------------------
= (255, 0, 0)
```

<span data-ttu-id="98e56-129">Vergleichen Sie diese Berechnungen mit der folgenden Abbildung, auf der angezeigt wird, was geschieht, wenn die bilineare Filterberechnung bei jeder Textur auf der 4x4-Textur durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="98e56-129">Compare these calculations against the following illustration, which shows what happens if the bilinear filtering calculation is performed at every texture address across the 4x4 texture.</span></span>

![Abbildung einer 4x4-Textur mit bilinearer Filterung, die bei jeder Textur-Adresse ausgeführt wird](images/bilinear-fig7c.jpg)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="98e56-131"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="98e56-131"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="98e56-132">Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="98e56-132">Texture filtering</span></span>](texture-filtering.md)

 

 




