---
title: Texturen mit Alphakanälen
description: Es gibt zwei Möglichkeiten, Texturzuordnungen mit komplexer Transparenz zu kodieren.
ms.assetid: 768A774A-4F21-4DDE-B863-14211DA92926
keywords:
- Texturen mit Alphakanälen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 88d150383d2be219e7f382e0e690771acbc9d2ee
ms.sourcegitcommit: 231065c899d0de285584d41e6335251e0c2c4048
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8825170"
---
# <a name="textures-with-alpha-channels"></a><span data-ttu-id="afc74-104">Texturen mit Alphakanälen</span><span class="sxs-lookup"><span data-stu-id="afc74-104">Textures with alpha channels</span></span>


<span data-ttu-id="afc74-105">Es gibt zwei Möglichkeiten, Texturabbildungen mit komplexer Transparenz zu codieren.</span><span class="sxs-lookup"><span data-stu-id="afc74-105">There are two ways to encode texture maps that exhibit more complex transparency.</span></span> <span data-ttu-id="afc74-106">In jedem Fall geht ein Block, der die Transparenz beschreibt, dem bereits beschriebenen 64-Bit-Block voraus.</span><span class="sxs-lookup"><span data-stu-id="afc74-106">In each case, a block that describes the transparency precedes the 64-bit block already described.</span></span> <span data-ttu-id="afc74-107">Die Transparenz wird entweder als 4x4-Bitmap mit 4Bits pro Pixel (explizite Kodierung) oder mit weniger Bits und linearer Interpolation dargestellt, die mit der für Farben verwendeten Kodierung vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="afc74-107">The transparency is either represented as a 4x4 bitmap with 4 bits per pixel (explicit encoding), or with fewer bits and linear interpolation that is analogous to what is used for color encoding.</span></span>

<span data-ttu-id="afc74-108">Die Transparenzblock und der Farbblock sind wie in der folgenden Tabelle gezeigt angeordnet.</span><span class="sxs-lookup"><span data-stu-id="afc74-108">The transparency block and the color block are arranged as shown in the following table.</span></span>

| <span data-ttu-id="afc74-109">Wort-Adresse</span><span class="sxs-lookup"><span data-stu-id="afc74-109">Word address</span></span> | <span data-ttu-id="afc74-110">64-Bit-Block</span><span class="sxs-lookup"><span data-stu-id="afc74-110">64-bit block</span></span>                      |
|--------------|-----------------------------------|
| <span data-ttu-id="afc74-111">3:0</span><span class="sxs-lookup"><span data-stu-id="afc74-111">3:0</span></span>          | <span data-ttu-id="afc74-112">Transparenzblock</span><span class="sxs-lookup"><span data-stu-id="afc74-112">Transparency block</span></span>                |
| <span data-ttu-id="afc74-113">7:4</span><span class="sxs-lookup"><span data-stu-id="afc74-113">7:4</span></span>          | <span data-ttu-id="afc74-114">Zuvor beschriebener 64-Bit-Block</span><span class="sxs-lookup"><span data-stu-id="afc74-114">Previously described 64-bit block</span></span> |

 

## <a name="span-idexplicit-texture-encodingspanspan-idexplicit-texture-encodingspanspan-idexplicit-texture-encodingspanexplicit-texture-encoding"></a><span data-ttu-id="afc74-115"><span id="Explicit-Texture-Encoding"></span><span id="explicit-texture-encoding"></span><span id="EXPLICIT-TEXTURE-ENCODING"></span>Explizite Texturkodierung</span><span class="sxs-lookup"><span data-stu-id="afc74-115"><span id="Explicit-Texture-Encoding"></span><span id="explicit-texture-encoding"></span><span id="EXPLICIT-TEXTURE-ENCODING"></span>Explicit texture encoding</span></span>


<span data-ttu-id="afc74-116">Für die explizite Texturkodierung (Format BC2) werden die Alphakomponenten der Texel, die die Transparenz beschreiben, in einer 4 x 4-Bitmap mit 4 Bits pro Texel kodiert.</span><span class="sxs-lookup"><span data-stu-id="afc74-116">For explicit texture encoding (BC2 format), the alpha components of the texels that describe transparency are encoded in a 4x4 bitmap with 4 bits per texel.</span></span> <span data-ttu-id="afc74-117">Diese vier Bits kann können auf verschiedene Weise gewonnen werden, etwa durch Dithering oder durch Verwendung der vier wichtigsten Bits der Alphadaten.</span><span class="sxs-lookup"><span data-stu-id="afc74-117">These four bits can be achieved through a variety of means such as dithering or by using the four most significant bits of the alpha data.</span></span> <span data-ttu-id="afc74-118">Wie auch immer sie produziert werden, so sind sie, ohne irgendeine Art von Interpolation.</span><span class="sxs-lookup"><span data-stu-id="afc74-118">However they are produced, they are used just as they are, without any form of interpolation.</span></span>

<span data-ttu-id="afc74-119">Das folgende Diagramm zeigt einen 64-Bit-Transparenzblock.</span><span class="sxs-lookup"><span data-stu-id="afc74-119">The following diagram shows a 64-bit transparency block.</span></span>

![Diagramm eines 64-Bit-Transparenzblocks](images/colors4.png)

<span data-ttu-id="afc74-121">**Hinweis:**  die Komprimierungsmethode von Direct3D verwendet die vier wichtigsten Bits.</span><span class="sxs-lookup"><span data-stu-id="afc74-121">**Note** The compression method of Direct3D uses the four most significant bits.</span></span>

 

<span data-ttu-id="afc74-122">Die folgenden Tabellen illustrieren, wie die Alpha-Informationen für jedes 16-Bit-Wort im Speicher repräsentiert sind.</span><span class="sxs-lookup"><span data-stu-id="afc74-122">The following tables illustrate how the alpha information is laid out in memory, for each 16-bit word.</span></span>

<span data-ttu-id="afc74-123">Layout für Wort 0:</span><span class="sxs-lookup"><span data-stu-id="afc74-123">Layout for word 0:</span></span>

| <span data-ttu-id="afc74-124">Bits</span><span class="sxs-lookup"><span data-stu-id="afc74-124">Bits</span></span>          | <span data-ttu-id="afc74-125">Alpha</span><span class="sxs-lookup"><span data-stu-id="afc74-125">Alpha</span></span>      |
|---------------|------------|
| <span data-ttu-id="afc74-126">3:0 (LSB\*)</span><span class="sxs-lookup"><span data-stu-id="afc74-126">3:0 (LSB\*)</span></span>   | <span data-ttu-id="afc74-127">\[0\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-127">\[0\]\[0\]</span></span> |
| <span data-ttu-id="afc74-128">7:4</span><span class="sxs-lookup"><span data-stu-id="afc74-128">7:4</span></span>           | <span data-ttu-id="afc74-129">\[0\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="afc74-129">\[0\]\[1\]</span></span> |
| <span data-ttu-id="afc74-130">11:8</span><span class="sxs-lookup"><span data-stu-id="afc74-130">11:8</span></span>          | <span data-ttu-id="afc74-131">\[0\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="afc74-131">\[0\]\[2\]</span></span> |
| <span data-ttu-id="afc74-132">15:12 (MSB\*)</span><span class="sxs-lookup"><span data-stu-id="afc74-132">15:12 (MSB\*)</span></span> | <span data-ttu-id="afc74-133">\[0\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="afc74-133">\[0\]\[3\]</span></span> |

 

<span data-ttu-id="afc74-134">\*am wenigsten wichtigstes Bit, wichtigstes Bit (MSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-134">\*least-significant bit, most significant bit (MSB)</span></span>

<span data-ttu-id="afc74-135">Layout für Wort 1:</span><span class="sxs-lookup"><span data-stu-id="afc74-135">Layout for word 1:</span></span>

| <span data-ttu-id="afc74-136">Bits</span><span class="sxs-lookup"><span data-stu-id="afc74-136">Bits</span></span>        | <span data-ttu-id="afc74-137">Alpha</span><span class="sxs-lookup"><span data-stu-id="afc74-137">Alpha</span></span>      |
|-------------|------------|
| <span data-ttu-id="afc74-138">3:0 (LSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-138">3:0 (LSB)</span></span>   | <span data-ttu-id="afc74-139">\[1\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-139">\[1\]\[0\]</span></span> |
| <span data-ttu-id="afc74-140">7:4</span><span class="sxs-lookup"><span data-stu-id="afc74-140">7:4</span></span>         | <span data-ttu-id="afc74-141">\[1\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="afc74-141">\[1\]\[1\]</span></span> |
| <span data-ttu-id="afc74-142">11:8</span><span class="sxs-lookup"><span data-stu-id="afc74-142">11:8</span></span>        | <span data-ttu-id="afc74-143">\[1\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="afc74-143">\[1\]\[2\]</span></span> |
| <span data-ttu-id="afc74-144">15:12 (MSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-144">15:12 (MSB)</span></span> | <span data-ttu-id="afc74-145">\[1\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="afc74-145">\[1\]\[3\]</span></span> |

 

<span data-ttu-id="afc74-146">Layout für Wort 2:</span><span class="sxs-lookup"><span data-stu-id="afc74-146">Layout for word 2:</span></span>

| <span data-ttu-id="afc74-147">Bits</span><span class="sxs-lookup"><span data-stu-id="afc74-147">Bits</span></span>        | <span data-ttu-id="afc74-148">Alpha</span><span class="sxs-lookup"><span data-stu-id="afc74-148">Alpha</span></span>      |
|-------------|------------|
| <span data-ttu-id="afc74-149">3:0 (LSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-149">3:0 (LSB)</span></span>   | <span data-ttu-id="afc74-150">\[2\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-150">\[2\]\[0\]</span></span> |
| <span data-ttu-id="afc74-151">7:4</span><span class="sxs-lookup"><span data-stu-id="afc74-151">7:4</span></span>         | <span data-ttu-id="afc74-152">\[2\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="afc74-152">\[2\]\[1\]</span></span> |
| <span data-ttu-id="afc74-153">11:8</span><span class="sxs-lookup"><span data-stu-id="afc74-153">11:8</span></span>        | <span data-ttu-id="afc74-154">\[2\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="afc74-154">\[2\]\[2\]</span></span> |
| <span data-ttu-id="afc74-155">15:12 (MSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-155">15:12 (MSB)</span></span> | <span data-ttu-id="afc74-156">\[2\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="afc74-156">\[2\]\[3\]</span></span> |

 

<span data-ttu-id="afc74-157">Layout für Wort 3:</span><span class="sxs-lookup"><span data-stu-id="afc74-157">Layout for word 3:</span></span>

| <span data-ttu-id="afc74-158">Bits</span><span class="sxs-lookup"><span data-stu-id="afc74-158">Bits</span></span>        | <span data-ttu-id="afc74-159">Alpha</span><span class="sxs-lookup"><span data-stu-id="afc74-159">Alpha</span></span>      |
|-------------|------------|
| <span data-ttu-id="afc74-160">3:0 (LSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-160">3:0 (LSB)</span></span>   | <span data-ttu-id="afc74-161">\[3\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-161">\[3\]\[0\]</span></span> |
| <span data-ttu-id="afc74-162">7:4</span><span class="sxs-lookup"><span data-stu-id="afc74-162">7:4</span></span>         | <span data-ttu-id="afc74-163">\[3\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="afc74-163">\[3\]\[1\]</span></span> |
| <span data-ttu-id="afc74-164">11:8</span><span class="sxs-lookup"><span data-stu-id="afc74-164">11:8</span></span>        | <span data-ttu-id="afc74-165">\[3\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="afc74-165">\[3\]\[2\]</span></span> |
| <span data-ttu-id="afc74-166">15:12 (MSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-166">15:12 (MSB)</span></span> | <span data-ttu-id="afc74-167">\[3\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="afc74-167">\[3\]\[3\]</span></span> |

 

<span data-ttu-id="afc74-168">Der Farbvergleich, der in BC1 verwendet wird, um festzustellen, ob der Texel transparent ist, wird in diesem Format nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="afc74-168">The color compare used in BC1 to determine if the texel is transparent is not used in this format.</span></span> <span data-ttu-id="afc74-169">Es wird angenommen, dass die Farbdaten ohne den Farbvergleich immer wie im 4-Farben-Modus behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="afc74-169">It is assumed that without the color compare the color data is always treated as if in 4-color mode.</span></span>

## <a name="span-idthree-bit-linear-alpha-interpolationspanspan-idthree-bit-linear-alpha-interpolationspanspan-idthree-bit-linear-alpha-interpolationspanthree-bit-linear-alpha-interpolation"></a><span data-ttu-id="afc74-170"><span id="Three-Bit-Linear-Alpha-Interpolation"></span><span id="three-bit-linear-alpha-interpolation"></span><span id="THREE-BIT-LINEAR-ALPHA-INTERPOLATION"></span>Lineare Drei-Bit-Alpha-Interpolation</span><span class="sxs-lookup"><span data-stu-id="afc74-170"><span id="Three-Bit-Linear-Alpha-Interpolation"></span><span id="three-bit-linear-alpha-interpolation"></span><span id="THREE-BIT-LINEAR-ALPHA-INTERPOLATION"></span>Three-bit linear alpha interpolation</span></span>


<span data-ttu-id="afc74-171">Die Kodierung der Transparenz für das Format BC3 basiert auf einem Konzept, das der für Farbe verwendeten linearen Kodierung ähnelt.</span><span class="sxs-lookup"><span data-stu-id="afc74-171">The encoding of transparency for the BC3 format is based on a concept similar to the linear encoding used for color.</span></span> <span data-ttu-id="afc74-172">Zwei 8-Bit-Alphawerte und eine 4 x 4-Bitmap mit drei Bits pro Pixel sind in den ersten acht Bytes des Blocks gespeichert.</span><span class="sxs-lookup"><span data-stu-id="afc74-172">Two 8-bit alpha values and a 4x4 bitmap with three bits per pixel are stored in the first eight bytes of the block.</span></span> <span data-ttu-id="afc74-173">Die repräsentativen Alphawerte werden zum Interpolieren der Alpha-Zwischenwerte verwendet.</span><span class="sxs-lookup"><span data-stu-id="afc74-173">The representative alpha values are used to interpolate intermediate alpha values.</span></span> <span data-ttu-id="afc74-174">Die Art und Weise der beiden Alphawerte bietet weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="afc74-174">Additional information is available in the way the two alpha values are stored.</span></span> <span data-ttu-id="afc74-175">Wenn alpha\_0 größer als alpha\_1 ist, erstellt die Interpolation sechs Alpha-Zwischenwerte.</span><span class="sxs-lookup"><span data-stu-id="afc74-175">If alpha\_0 is greater than alpha\_1, then six intermediate alpha values are created by the interpolation.</span></span> <span data-ttu-id="afc74-176">Andernfalls werden vier Alpha-Zwischenwerte zwischen den angegebenen Alpha-Extremen interpoliert.</span><span class="sxs-lookup"><span data-stu-id="afc74-176">Otherwise, four intermediate alpha values are interpolated between the specified alpha extremes.</span></span> <span data-ttu-id="afc74-177">Die zwei zusätzlichen impliziten Alphawerte sind 0 (vollständig transparent) und 255 (vollständig opak).</span><span class="sxs-lookup"><span data-stu-id="afc74-177">The two additional implicit alpha values are 0 (fully transparent) and 255 (fully opaque).</span></span>

<span data-ttu-id="afc74-178">Das folgende Codebeispiel veranschaulicht diesen Algorithmus.</span><span class="sxs-lookup"><span data-stu-id="afc74-178">The following code example illustrates this algorithm.</span></span>

```
// 8-alpha or 6-alpha block?    
if (alpha_0 > alpha_1) {    
    // 8-alpha block:  derive the other six alphas.    
    // Bit code 000 = alpha_0, 001 = alpha_1, others are interpolated.
    alpha_2 = (6 * alpha_0 + 1 * alpha_1 + 3) / 7;    // bit code 010
    alpha_3 = (5 * alpha_0 + 2 * alpha_1 + 3) / 7;    // bit code 011
    alpha_4 = (4 * alpha_0 + 3 * alpha_1 + 3) / 7;    // bit code 100
    alpha_5 = (3 * alpha_0 + 4 * alpha_1 + 3) / 7;    // bit code 101
    alpha_6 = (2 * alpha_0 + 5 * alpha_1 + 3) / 7;    // bit code 110
    alpha_7 = (1 * alpha_0 + 6 * alpha_1 + 3) / 7;    // bit code 111  
}    
else {  
    // 6-alpha block.    
    // Bit code 000 = alpha_0, 001 = alpha_1, others are interpolated.
    alpha_2 = (4 * alpha_0 + 1 * alpha_1 + 2) / 5;    // Bit code 010
    alpha_3 = (3 * alpha_0 + 2 * alpha_1 + 2) / 5;    // Bit code 011
    alpha_4 = (2 * alpha_0 + 3 * alpha_1 + 2) / 5;    // Bit code 100
    alpha_5 = (1 * alpha_0 + 4 * alpha_1 + 2) / 5;    // Bit code 101
    alpha_6 = 0;                                      // Bit code 110
    alpha_7 = 255;                                    // Bit code 111
}
```

<span data-ttu-id="afc74-179">Das Speicherlayout des Alphablocks ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="afc74-179">The memory layout of the alpha block is as follows:</span></span>

| <span data-ttu-id="afc74-180">Byte</span><span class="sxs-lookup"><span data-stu-id="afc74-180">Byte</span></span> | <span data-ttu-id="afc74-181">Alpha</span><span class="sxs-lookup"><span data-stu-id="afc74-181">Alpha</span></span>                                                          |
|------|----------------------------------------------------------------|
| <span data-ttu-id="afc74-182">0</span><span class="sxs-lookup"><span data-stu-id="afc74-182">0</span></span>    | <span data-ttu-id="afc74-183">Alpha\_0</span><span class="sxs-lookup"><span data-stu-id="afc74-183">Alpha\_0</span></span>                                                       |
| <span data-ttu-id="afc74-184">1</span><span class="sxs-lookup"><span data-stu-id="afc74-184">1</span></span>    | <span data-ttu-id="afc74-185">Alpha\_1</span><span class="sxs-lookup"><span data-stu-id="afc74-185">Alpha\_1</span></span>                                                       |
| <span data-ttu-id="afc74-186">2</span><span class="sxs-lookup"><span data-stu-id="afc74-186">2</span></span>    | <span data-ttu-id="afc74-187">\[0\]\[2\] (2 MSBs), \[0\]\[1\], \[0\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-187">\[0\]\[2\] (2 MSBs), \[0\]\[1\], \[0\]\[0\]</span></span>                    |
| <span data-ttu-id="afc74-188">3</span><span class="sxs-lookup"><span data-stu-id="afc74-188">3</span></span>    | <span data-ttu-id="afc74-189">\[1\]\[1\] (1 MSB), \[1\]\[0\], \[0\]\[3\], \[0\]\[2\] (1 LSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-189">\[1\]\[1\] (1 MSB), \[1\]\[0\], \[0\]\[3\], \[0\]\[2\] (1 LSB)</span></span> |
| <span data-ttu-id="afc74-190">4</span><span class="sxs-lookup"><span data-stu-id="afc74-190">4</span></span>    | <span data-ttu-id="afc74-191">\[1\]\[3\], \[1\]\[2\], \[1\]\[1\] (2 LSBs)</span><span class="sxs-lookup"><span data-stu-id="afc74-191">\[1\]\[3\], \[1\]\[2\], \[1\]\[1\] (2 LSBs)</span></span>                    |
| <span data-ttu-id="afc74-192">5</span><span class="sxs-lookup"><span data-stu-id="afc74-192">5</span></span>    | <span data-ttu-id="afc74-193">\[2\]\[2\] (2 MSBs), \[2\]\[1\], \[2\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="afc74-193">\[2\]\[2\] (2 MSBs), \[2\]\[1\], \[2\]\[0\]</span></span>                    |
| <span data-ttu-id="afc74-194">6</span><span class="sxs-lookup"><span data-stu-id="afc74-194">6</span></span>    | <span data-ttu-id="afc74-195">\[3\]\[1\] (1 MSB), \[3\]\[0\], \[2\]\[3\], \[2\]\[2\] (1 LSB)</span><span class="sxs-lookup"><span data-stu-id="afc74-195">\[3\]\[1\] (1 MSB), \[3\]\[0\], \[2\]\[3\], \[2\]\[2\] (1 LSB)</span></span> |
| <span data-ttu-id="afc74-196">7</span><span class="sxs-lookup"><span data-stu-id="afc74-196">7</span></span>    | <span data-ttu-id="afc74-197">\[3\]\[3\], \[3\]\[2\], \[3\]\[1\] (2 LSBs)</span><span class="sxs-lookup"><span data-stu-id="afc74-197">\[3\]\[3\], \[3\]\[2\], \[3\]\[1\] (2 LSBs)</span></span>                    |

 

<span data-ttu-id="afc74-198">Der Farbvergleich, der in BC1 verwendet wird, um festzustellen, ob der Texel transparent ist, wird in diesen Formaten nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="afc74-198">The color compare used in BC1 to determine if the texel is transparent is not used with these formats.</span></span> <span data-ttu-id="afc74-199">Es wird angenommen, dass die Farbdaten ohne den Farbvergleich immer wie im 4-Farben-Modus behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="afc74-199">It is assumed that without the color compare the color data is always treated as if in 4-color mode.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="afc74-200"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="afc74-200"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="afc74-201">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="afc74-201">Compressed texture resources</span></span>](compressed-texture-resources.md)

 

 




