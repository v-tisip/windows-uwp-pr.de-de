---
title: BC6H-Format
description: Das BC6H-Format ist ein Format für die Texturkomprimierung, das „High Dynamic Range“-Farbräume (HDR) in Quelldaten unterstützt.
ms.assetid: 6781D967-9262-4EE7-B354-7A6D0EA0498E
keywords:
- BC6H-Format
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: be88f06cd5893f2f67697a54754826440bdf7d18
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6272869"
---
# <a name="bc6h-format"></a><span data-ttu-id="1169f-104">BC6H-Format</span><span class="sxs-lookup"><span data-stu-id="1169f-104">BC6H format</span></span>


<span data-ttu-id="1169f-105">Das BC6H-Format ist ein Format für die Texturkomprimierung, das „High Dynamic Range“-Farbräume (HDR) in Quelldaten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-105">The BC6H format is a texture compression format designed to support high-dynamic range (HDR) color spaces in source data.</span></span>

## <a name="span-idabout-bc6h-dxgi-format-bc6hspanspan-idabout-bc6h-dxgi-format-bc6hspanspan-idabout-bc6h-dxgi-format-bc6hspanabout-bc6hdxgiformatbc6h"></a><span data-ttu-id="1169f-106"><span id="About-BC6H-DXGI-FORMAT-BC6H"></span><span id="about-bc6h-dxgi-format-bc6h"></span><span id="ABOUT-BC6H-DXGI-FORMAT-BC6H"></span>Informationen zu BC6H/DXGI\_FORMAT\_BC6H</span><span class="sxs-lookup"><span data-stu-id="1169f-106"><span id="About-BC6H-DXGI-FORMAT-BC6H"></span><span id="about-bc6h-dxgi-format-bc6h"></span><span id="ABOUT-BC6H-DXGI-FORMAT-BC6H"></span>About BC6H/DXGI\_FORMAT\_BC6H</span></span>


<span data-ttu-id="1169f-107">Das BC6H-Format bietet eine hochwertige Komprimierung für Bilder, die drei HDR-Farbkanäle mit jeweils 16-Bit-Werten für jeden Farbkanal des Farbwerts (16: 16:16) verwenden.</span><span class="sxs-lookup"><span data-stu-id="1169f-107">The BC6H format provides high-quality compression for images that use three HDR color channels, with a 16-bit value for each color channel of the value (16:16:16).</span></span> <span data-ttu-id="1169f-108">Alphakanäle werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-108">There is no support for an alpha channel.</span></span>

<span data-ttu-id="1169f-109">BC6H wird durch die folgenden DXGI\_FORMAT-Enumerationswerte angegeben:</span><span class="sxs-lookup"><span data-stu-id="1169f-109">BC6H is specified by the following DXGI\_FORMAT enumeration values:</span></span>

-   <span data-ttu-id="1169f-110">**DXGI\_FORMAT\_BC6H\_TYPELESS**.</span><span class="sxs-lookup"><span data-stu-id="1169f-110">**DXGI\_FORMAT\_BC6H\_TYPELESS**.</span></span>
-   <span data-ttu-id="1169f-111">**DXGI\_FORMAT\_BC6H\_UF16**.</span><span class="sxs-lookup"><span data-stu-id="1169f-111">**DXGI\_FORMAT\_BC6H\_UF16**.</span></span> <span data-ttu-id="1169f-112">Dieses BC6H-Format verwendet keine Bit mit Vorzeichen im 16-Bit-Gleitkommawert des Farbkanals.</span><span class="sxs-lookup"><span data-stu-id="1169f-112">This BC6H format does not use a sign bit in the 16-bit floating point color channel values.</span></span>
-   <span data-ttu-id="1169f-113">**DXGI\_FORMAT\_BC6H\_SF16**.</span><span class="sxs-lookup"><span data-stu-id="1169f-113">**DXGI\_FORMAT\_BC6H\_SF16**.</span></span> <span data-ttu-id="1169f-114">Dieses BC6H-Format verwendet eine Bit mit Vorzeichen im 16-Bit-Gleitkommawert des Farbkanals.</span><span class="sxs-lookup"><span data-stu-id="1169f-114">This BC6H format uses a sign bit in the 16-bit floating point color channel values.</span></span>

<span data-ttu-id="1169f-115">**Hinweis:**  der 16-Bit-Gleitkommaformat für Farbkanäle wird häufig bezeichnet als ein "halb"-Gleitkommaformat.</span><span class="sxs-lookup"><span data-stu-id="1169f-115">**Note** The 16 bit floating point format for color channels is often referred to as a "half" floating point format.</span></span> <span data-ttu-id="1169f-116">Dieses Format hat das folgende Bit-Layout:</span><span class="sxs-lookup"><span data-stu-id="1169f-116">This format has the following bit layout:</span></span>
|                       |                                                 |
|-----------------------|-------------------------------------------------|
| <span data-ttu-id="1169f-117">UF16 (Gleitkomma ohne Vorzeichen)</span><span class="sxs-lookup"><span data-stu-id="1169f-117">UF16 (unsigned float)</span></span> | <span data-ttu-id="1169f-118">5Bit Exponent + 11Bit Mantisse</span><span class="sxs-lookup"><span data-stu-id="1169f-118">5 exponent bits + 11 mantissa bits</span></span>              |
| <span data-ttu-id="1169f-119">SF16 (Gleitkomma mit Vorzeichen)</span><span class="sxs-lookup"><span data-stu-id="1169f-119">SF16 (signed float)</span></span>   | <span data-ttu-id="1169f-120">1Bit mit Vorzeichen + 5Bit Exponent + 10Bit Mantisse</span><span class="sxs-lookup"><span data-stu-id="1169f-120">1 sign bit + 5 exponent bits + 10 mantissa bits</span></span> |

 

 

<span data-ttu-id="1169f-121">Das BC6H-Format kann für Texturressourcen wie [Texture2D](https://msdn.microsoft.com/library/windows/desktop/bb205277) (einschließlich Arrays), Texture3D oder TextureCube (einschließlich Arrays verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1169f-121">The BC6H format can be used for [Texture2D](https://msdn.microsoft.com/library/windows/desktop/bb205277) (including arrays), Texture3D, or TextureCube (including arrays) texture resources.</span></span> <span data-ttu-id="1169f-122">Das Format gilt ebenfalls für alle Mip-Map-Oberflächen, die mit diesen Ressourcen verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="1169f-122">Similarly, this format applies to any MIP-map surfaces associated with these resources.</span></span>

<span data-ttu-id="1169f-123">BC6H verwendet eine feste Blockgröße von 16 Byte (128Bit) und eine feste Kachelgröße von 4×4-Texel.</span><span class="sxs-lookup"><span data-stu-id="1169f-123">BC6H uses a fixed block size of 16 bytes (128 bits) and a fixed tile size of 4x4 texels.</span></span> <span data-ttu-id="1169f-124">Genau wie mit vorherigen BC-Formaten werden Texturbilder, die größer als die unterstützte Kachelgröße (4×4) sind, durch die Verwendung mehrerer Blöcke komprimiert.</span><span class="sxs-lookup"><span data-stu-id="1169f-124">As with previous BC formats, texture images larger than the supported tile size (4x4) are compressed by using multiple blocks.</span></span> <span data-ttu-id="1169f-125">Diese Adressierungsidentität gilt auch für dreidimensionale Bilder, MIP-Maps, Cube-Zuordnungen und Texturarrays.</span><span class="sxs-lookup"><span data-stu-id="1169f-125">This addressing identity applies also to three-dimensional images, MIP-maps, cube maps, and texture arrays.</span></span> <span data-ttu-id="1169f-126">Alle Bildkacheln müssen das gleiche Format aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1169f-126">All image tiles must be of the same format.</span></span>

<span data-ttu-id="1169f-127">Einschränkungen des BC6H-Formats:</span><span class="sxs-lookup"><span data-stu-id="1169f-127">Caveats with the BC6H format:</span></span>

-   <span data-ttu-id="1169f-128">BC6H unterstützt die Denormalisierung der Gleitkommazahl. INF (unendlich) und NaN (keine Zahl) werden allerdings nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-128">BC6H supports floating point denormalization, but does not support INF (infinity) and NaN (not a number).</span></span> <span data-ttu-id="1169f-129">Die einzige Ausnahme ist BC6H im Vorzeichenmodus (DXGI\_FORMAT\_BC6H\_SF16), die -INF (negativ Unendlich) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-129">The exception is the signed mode of BC6H (DXGI\_FORMAT\_BC6H\_SF16), which supports -INF (negative infinity).</span></span> <span data-ttu-id="1169f-130">Diese Unterstützung für -INF ist lediglich ein Artefakt des Formats selbst und wird nicht speziell von Encodern für dieses Format unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-130">This support for -INF is merely an artifact of the format itself, and is not specifically supported by encoders for this format.</span></span> <span data-ttu-id="1169f-131">Wenn ein Encoder auf INF- (positiv oder negativ) oder NaN-Eingabedaten trifft, sollte der Encoder diese Daten auf den Wert der maximal zulässigen Nicht-INF-Darstellung konvertieren und NaN vor der Komprimierung „0” zuordnen.</span><span class="sxs-lookup"><span data-stu-id="1169f-131">In general, when an encoder encounters INF (positive or negative) or NaN input data, the encoder should convert that data to the maximum allowable non-INF representation value, and map NaN to 0 prior to compression.</span></span>
-   <span data-ttu-id="1169f-132">Alphakanäle werden nicht von BC6H unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1169f-132">BC6H does not support an alpha channel.</span></span>
-   <span data-ttu-id="1169f-133">Der BC6H-Decoder führt vor der Texturfilterung eine Dekomprimierung durch.</span><span class="sxs-lookup"><span data-stu-id="1169f-133">The BC6H decoder performs decompression before it performs texture filtering.</span></span>
-   <span data-ttu-id="1169f-134">Die BC6H-Dekomprimierung muss die Bit präzise wiedergeben. Das heißt, die Hardware muss Ergebnisse zurückgeben, die mit dem in dieser Dokumentation beschriebenen Decoder übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="1169f-134">BC6H decompression must be bit-accurate; that is, the hardware must return results that are identical to the decoder described in this documentation.</span></span>

## <a name="span-idbc6h-implementationspanspan-idbc6h-implementationspanspan-idbc6h-implementationspanbc6h-implementation"></a><span data-ttu-id="1169f-135"><span id="BC6H-implementation"></span><span id="bc6h-implementation"></span><span id="BC6H-IMPLEMENTATION"></span>Implementieren von BC6H</span><span class="sxs-lookup"><span data-stu-id="1169f-135"><span id="BC6H-implementation"></span><span id="bc6h-implementation"></span><span id="BC6H-IMPLEMENTATION"></span>BC6H implementation</span></span>


<span data-ttu-id="1169f-136">Ein BC6H-Block besteht aus Modus-Bit, komprimierten Endpunkten, komprimierten Indizes und einem optionalen Partitionsindex.</span><span class="sxs-lookup"><span data-stu-id="1169f-136">A BC6H block consists of mode bits, compressed endpoints, compressed indices, and an optional partition index.</span></span> <span data-ttu-id="1169f-137">Dieses Format legt 14 verschiedenen Modi fest.</span><span class="sxs-lookup"><span data-stu-id="1169f-137">This format specifies 14 different modes.</span></span>

<span data-ttu-id="1169f-138">Die Farbe eines Endpunkts wird als eine RGB-Dreiergruppe gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1169f-138">An endpoint color is stored as an RGB triplet.</span></span> <span data-ttu-id="1169f-139">BC6H definiert eine Farbpalette auf einer ungefähren Linie für eine Anzahl von definierten Farbendpunkten.</span><span class="sxs-lookup"><span data-stu-id="1169f-139">BC6H defines a palette of colors on an approximate line across a number of defined color endpoints.</span></span> <span data-ttu-id="1169f-140">Je nach gewähltem Modus kann eine Kachel darüber hinaus in zwei Regionen unterteilt oder als Einzelregion behandelt werden. Dabei verfügt eine Kachel mit zwei Regionen über eine separate Reihe von Farben für den Endpunkte jeder Region.</span><span class="sxs-lookup"><span data-stu-id="1169f-140">Also, depending on the mode, a tile can be divided into two regions or treated as a single region, where a two-region tile has a separate set of color endpoints for each region.</span></span> <span data-ttu-id="1169f-141">BC6H speichert einen Farbpaletten-Index pro Texel.</span><span class="sxs-lookup"><span data-stu-id="1169f-141">BC6H stores one palette index per texel.</span></span>

<span data-ttu-id="1169f-142">Im Fall von zwei Regionen sind 32 Partitionen möglich.</span><span class="sxs-lookup"><span data-stu-id="1169f-142">In the two-region case, there are 32 possible partitions.</span></span>

## <a name="span-iddecoding-the-bc6h-formatspanspan-iddecoding-the-bc6h-formatspanspan-iddecoding-the-bc6h-formatspandecoding-the-bc6h-format"></a><span data-ttu-id="1169f-143"><span id="Decoding-the-BC6H-format"></span><span id="decoding-the-bc6h-format"></span><span id="DECODING-THE-BC6H-FORMAT"></span>Decodieren des BC6H-Formats</span><span class="sxs-lookup"><span data-stu-id="1169f-143"><span id="Decoding-the-BC6H-format"></span><span id="decoding-the-bc6h-format"></span><span id="DECODING-THE-BC6H-FORMAT"></span>Decoding the BC6H format</span></span>


<span data-ttu-id="1169f-144">Der folgende Pseudocode zeigt die Schritte zur Dekomprimierung der Pixel (x, y) bei einem 16-Byte BC6H-Block an.</span><span class="sxs-lookup"><span data-stu-id="1169f-144">The pseudocode below shows the steps to decompress the pixel at (x,y) given the 16 byte BC6H block.</span></span>

``` syntax
decompress_bc6h(x, y, block)
{
    mode = extract_mode(block);
    endpoints;
    index;
    
    if(mode.type == ONE)
    {
        endpoints = extract_compressed_endpoints(mode, block);
        index = extract_index_ONE(x, y, block);
    }
    else //mode.type == TWO
    {
        partition = extract_partition(block);
        region = get_region(partition, x, y);
        endpoints = extract_compressed_endpoints(mode, region, block);
        index = extract_index_TWO(x, y, partition, block);
    }
    
    unquantize(endpoints);
    color = interpolate(index, endpoints);
    finish_unquantize(color);
}
```

<span data-ttu-id="1169f-145">Die folgende Tabelle enthält die Anzahl und Werte der Bit für jedes der 14 möglichen Formate für BC6H-Blöcke.</span><span class="sxs-lookup"><span data-stu-id="1169f-145">The following table contains the bit count and values for each of the 14 possible formats for BC6H blocks.</span></span>

| <span data-ttu-id="1169f-146">Modus</span><span class="sxs-lookup"><span data-stu-id="1169f-146">Mode</span></span> | <span data-ttu-id="1169f-147">Partitionsindizes</span><span class="sxs-lookup"><span data-stu-id="1169f-147">Partition Indices</span></span> | <span data-ttu-id="1169f-148">Partition</span><span class="sxs-lookup"><span data-stu-id="1169f-148">Partition</span></span> | <span data-ttu-id="1169f-149">Farbendpunkte</span><span class="sxs-lookup"><span data-stu-id="1169f-149">Color Endpoints</span></span>                  | <span data-ttu-id="1169f-150">Modus-Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-150">Mode Bits</span></span>      |
|------|-------------------|-----------|----------------------------------|----------------|
| <span data-ttu-id="1169f-151">1</span><span class="sxs-lookup"><span data-stu-id="1169f-151">1</span></span>    | <span data-ttu-id="1169f-152">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-152">46 bits</span></span>           | <span data-ttu-id="1169f-153">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-153">5 bits</span></span>    | <span data-ttu-id="1169f-154">75Bit (10.555, 10.555, 10.555)</span><span class="sxs-lookup"><span data-stu-id="1169f-154">75 bits (10.555, 10.555, 10.555)</span></span> | <span data-ttu-id="1169f-155">2Bit (00)</span><span class="sxs-lookup"><span data-stu-id="1169f-155">2 bits (00)</span></span>    |
| <span data-ttu-id="1169f-156">2</span><span class="sxs-lookup"><span data-stu-id="1169f-156">2</span></span>    | <span data-ttu-id="1169f-157">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-157">46 bits</span></span>           | <span data-ttu-id="1169f-158">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-158">5 bits</span></span>    | <span data-ttu-id="1169f-159">75Bit (7666, 7666, 7666)</span><span class="sxs-lookup"><span data-stu-id="1169f-159">75 bits (7666, 7666, 7666)</span></span>       | <span data-ttu-id="1169f-160">2Bit (01)</span><span class="sxs-lookup"><span data-stu-id="1169f-160">2 bits (01)</span></span>    |
| <span data-ttu-id="1169f-161">3</span><span class="sxs-lookup"><span data-stu-id="1169f-161">3</span></span>    | <span data-ttu-id="1169f-162">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-162">46 bits</span></span>           | <span data-ttu-id="1169f-163">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-163">5 bits</span></span>    | <span data-ttu-id="1169f-164">72Bit (11.555, 11.444, 11.444)</span><span class="sxs-lookup"><span data-stu-id="1169f-164">72 bits (11.555, 11.444, 11.444)</span></span> | <span data-ttu-id="1169f-165">5Bit (00010)</span><span class="sxs-lookup"><span data-stu-id="1169f-165">5 bits (00010)</span></span> |
| <span data-ttu-id="1169f-166">4</span><span class="sxs-lookup"><span data-stu-id="1169f-166">4</span></span>    | <span data-ttu-id="1169f-167">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-167">46 bits</span></span>           | <span data-ttu-id="1169f-168">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-168">5 bits</span></span>    | <span data-ttu-id="1169f-169">72Bit (11.444, 11.555, 11.444)</span><span class="sxs-lookup"><span data-stu-id="1169f-169">72 bits (11.444, 11.555, 11.444)</span></span> | <span data-ttu-id="1169f-170">5Bit (00110)</span><span class="sxs-lookup"><span data-stu-id="1169f-170">5 bits (00110)</span></span> |
| <span data-ttu-id="1169f-171">5</span><span class="sxs-lookup"><span data-stu-id="1169f-171">5</span></span>    | <span data-ttu-id="1169f-172">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-172">46 bits</span></span>           | <span data-ttu-id="1169f-173">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-173">5 bits</span></span>    | <span data-ttu-id="1169f-174">72Bit (11.444, 11.444, 11.555)</span><span class="sxs-lookup"><span data-stu-id="1169f-174">72 bits (11.444, 11.444, 11.555)</span></span> | <span data-ttu-id="1169f-175">5Bit (01010)</span><span class="sxs-lookup"><span data-stu-id="1169f-175">5 bits (01010)</span></span> |
| <span data-ttu-id="1169f-176">6</span><span class="sxs-lookup"><span data-stu-id="1169f-176">6</span></span>    | <span data-ttu-id="1169f-177">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-177">46 bits</span></span>           | <span data-ttu-id="1169f-178">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-178">5 bits</span></span>    | <span data-ttu-id="1169f-179">72Bit (9555, 9555, 9555)</span><span class="sxs-lookup"><span data-stu-id="1169f-179">72 bits (9555, 9555, 9555)</span></span>       | <span data-ttu-id="1169f-180">5Bit (01110)</span><span class="sxs-lookup"><span data-stu-id="1169f-180">5 bits (01110)</span></span> |
| <span data-ttu-id="1169f-181">7</span><span class="sxs-lookup"><span data-stu-id="1169f-181">7</span></span>    | <span data-ttu-id="1169f-182">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-182">46 bits</span></span>           | <span data-ttu-id="1169f-183">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-183">5 bits</span></span>    | <span data-ttu-id="1169f-184">72Bit (8666, 8555, 8555)</span><span class="sxs-lookup"><span data-stu-id="1169f-184">72 bits (8666, 8555, 8555)</span></span>       | <span data-ttu-id="1169f-185">5Bit (10010)</span><span class="sxs-lookup"><span data-stu-id="1169f-185">5 bits (10010)</span></span> |
| <span data-ttu-id="1169f-186">8</span><span class="sxs-lookup"><span data-stu-id="1169f-186">8</span></span>    | <span data-ttu-id="1169f-187">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-187">46 bits</span></span>           | <span data-ttu-id="1169f-188">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-188">5 bits</span></span>    | <span data-ttu-id="1169f-189">72Bit (8555, 8666, 8555)</span><span class="sxs-lookup"><span data-stu-id="1169f-189">72 bits (8555, 8666, 8555)</span></span>       | <span data-ttu-id="1169f-190">5Bit (10110)</span><span class="sxs-lookup"><span data-stu-id="1169f-190">5 bits (10110)</span></span> |
| <span data-ttu-id="1169f-191">9</span><span class="sxs-lookup"><span data-stu-id="1169f-191">9</span></span>    | <span data-ttu-id="1169f-192">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-192">46 bits</span></span>           | <span data-ttu-id="1169f-193">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-193">5 bits</span></span>    | <span data-ttu-id="1169f-194">72Bit (8555, 8555, 8666)</span><span class="sxs-lookup"><span data-stu-id="1169f-194">72 bits (8555, 8555, 8666)</span></span>       | <span data-ttu-id="1169f-195">5Bit (11010)</span><span class="sxs-lookup"><span data-stu-id="1169f-195">5 bits (11010)</span></span> |
| <span data-ttu-id="1169f-196">10</span><span class="sxs-lookup"><span data-stu-id="1169f-196">10</span></span>   | <span data-ttu-id="1169f-197">46Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-197">46 bits</span></span>           | <span data-ttu-id="1169f-198">5Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-198">5 bits</span></span>    | <span data-ttu-id="1169f-199">72Bit (6666, 6666, 6666)</span><span class="sxs-lookup"><span data-stu-id="1169f-199">72 bits (6666, 6666, 6666)</span></span>       | <span data-ttu-id="1169f-200">5Bit (11110)</span><span class="sxs-lookup"><span data-stu-id="1169f-200">5 bits (11110)</span></span> |
| <span data-ttu-id="1169f-201">11</span><span class="sxs-lookup"><span data-stu-id="1169f-201">11</span></span>   | <span data-ttu-id="1169f-202">63Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-202">63 bits</span></span>           | <span data-ttu-id="1169f-203">0Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-203">0 bits</span></span>    | <span data-ttu-id="1169f-204">60Bit (10.10, 10.10, 10.10)</span><span class="sxs-lookup"><span data-stu-id="1169f-204">60 bits (10.10, 10.10, 10.10)</span></span>    | <span data-ttu-id="1169f-205">5Bit (00011)</span><span class="sxs-lookup"><span data-stu-id="1169f-205">5 bits (00011)</span></span> |
| <span data-ttu-id="1169f-206">12</span><span class="sxs-lookup"><span data-stu-id="1169f-206">12</span></span>   | <span data-ttu-id="1169f-207">63Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-207">63 bits</span></span>           | <span data-ttu-id="1169f-208">0Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-208">0 bits</span></span>    | <span data-ttu-id="1169f-209">60Bit (11.9, 11.9, 11.9)</span><span class="sxs-lookup"><span data-stu-id="1169f-209">60 bits (11.9, 11.9, 11.9)</span></span>       | <span data-ttu-id="1169f-210">5Bit (00111)</span><span class="sxs-lookup"><span data-stu-id="1169f-210">5 bits (00111)</span></span> |
| <span data-ttu-id="1169f-211">13</span><span class="sxs-lookup"><span data-stu-id="1169f-211">13</span></span>   | <span data-ttu-id="1169f-212">63Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-212">63 bits</span></span>           | <span data-ttu-id="1169f-213">0Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-213">0 bits</span></span>    | <span data-ttu-id="1169f-214">60Bit (12.8, 12.8, 12.8)</span><span class="sxs-lookup"><span data-stu-id="1169f-214">60 bits (12.8, 12.8, 12.8)</span></span>       | <span data-ttu-id="1169f-215">5Bit (01011)</span><span class="sxs-lookup"><span data-stu-id="1169f-215">5 bits (01011)</span></span> |
| <span data-ttu-id="1169f-216">14</span><span class="sxs-lookup"><span data-stu-id="1169f-216">14</span></span>   | <span data-ttu-id="1169f-217">63Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-217">63 bits</span></span>           | <span data-ttu-id="1169f-218">0Bit</span><span class="sxs-lookup"><span data-stu-id="1169f-218">0 bits</span></span>    | <span data-ttu-id="1169f-219">60Bit (16.4, 16.4, 16.4)</span><span class="sxs-lookup"><span data-stu-id="1169f-219">60 bits (16.4, 16.4, 16.4)</span></span>       | <span data-ttu-id="1169f-220">5Bit (01111)</span><span class="sxs-lookup"><span data-stu-id="1169f-220">5 bits (01111)</span></span> |

 

<span data-ttu-id="1169f-221">Jedes Format dieser Tabelle kann durch Modus-Bits eindeutig identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="1169f-221">Each format in this table can be uniquely identified by the mode bits.</span></span> <span data-ttu-id="1169f-222">Die ersten zehn Modi werden für Kacheln mit zwei Regionen verwendet, wobei das Modus-Bitfeld entweder 2 oder 5Bit lang sein kann.</span><span class="sxs-lookup"><span data-stu-id="1169f-222">The first ten modes are used for two-region tiles, and the mode bit field can be either two or five bits long.</span></span> <span data-ttu-id="1169f-223">Diese Blöcke haben ebenfalls Felder für die komprimierten Farbendpunkte (72 oder 75Bit), die Partition (5Bit) und die Partitionsindizes (46Bit).</span><span class="sxs-lookup"><span data-stu-id="1169f-223">These blocks also have fields for the compressed color endpoints (72 or 75 bits), the partition (5 bits), and the partition indices (46 bits).</span></span>

<span data-ttu-id="1169f-224">Für die komprimierten Farbendpunkte geben die Werte der obigen Tabelle die Genauigkeit der gespeicherten RGB-Endpunkte und die verwendete Anzahl der Bit für jeden Farbwert an.</span><span class="sxs-lookup"><span data-stu-id="1169f-224">For the compressed color endpoints, the values in the preceding table note the precision of the stored RGB endpoints, and the number of bits used for each color value.</span></span> <span data-ttu-id="1169f-225">Modus 3 gibt z.B. einen Endpunkt der Farbe der Präzisionsebene 11 an sowie die Anzahl der Bit, die zur Speicherung der Deltawerte der transformierten Farbendpunkte Rot, Blau und Grün (je 5, 4 und 4) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1169f-225">For example, mode 3 specifies a color endpoint precision level of 11, and the number of bits used to store the delta values of the transformed endpoints for the red, blue and green colors (5, 4, and 4 respectively).</span></span> <span data-ttu-id="1169f-226">Modus 10 verwendet keine Delta-Komprimierung und speichert stattdessen explizit alle vier Farbendpunkte.</span><span class="sxs-lookup"><span data-stu-id="1169f-226">Mode 10 does not use delta compression, and instead stores all four color endpoints explicitly.</span></span>

<span data-ttu-id="1169f-227">Die letzten vier Textblock-Modi werden für Kacheln mit einer Region verwendet, wobei das Modusfeld 5Bit ist.</span><span class="sxs-lookup"><span data-stu-id="1169f-227">The last four block modes are used for one-region tiles, where the mode field is 5 bits.</span></span> <span data-ttu-id="1169f-228">Diese Blöcke verfügen über 5 Felder für die Endpunkte (60Bit) und die komprimierten Indizes (63Bit).</span><span class="sxs-lookup"><span data-stu-id="1169f-228">These blocks have fields for the endpoints (60 bits) and the compressed indices (63 bits).</span></span> <span data-ttu-id="1169f-229">Modus 11 (wie auch Modus 10) verwendet keine Delta-Komprimierung und speichert stattdessen explizit beide Farbendpunkte.</span><span class="sxs-lookup"><span data-stu-id="1169f-229">Mode 11 (like Mode 10) does not use delta compression, and instead stores both color endpoints explicitly.</span></span>

<span data-ttu-id="1169f-230">Modi 10011, 10111, 11011 und 11111 (nicht dargestellt) sind reserviert.</span><span class="sxs-lookup"><span data-stu-id="1169f-230">Modes 10011, 10111, 11011, and 11111 (not shown) are reserved.</span></span> <span data-ttu-id="1169f-231">Verwenden Sie diese nicht in Ihrem Encoder.</span><span class="sxs-lookup"><span data-stu-id="1169f-231">Do not use these in your encoder.</span></span> <span data-ttu-id="1169f-232">Wenn die Hardware in einem dieser angegebenen Modi ausgeführt wird, darf der resultierende dekomprimierte Block nur Nullen in allen Kanälen - mit Ausnahme des Alphakanals - enthalten.</span><span class="sxs-lookup"><span data-stu-id="1169f-232">If the hardware is passed blocks with one of these modes specified, the resulting decompressed block must contain all zeroes in all channels except for the alpha channel.</span></span>

<span data-ttu-id="1169f-233">Für BC6H muss der Alphakanal - unabhängig vom Modus - immer 1,0 zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="1169f-233">For BC6H, the alpha channel must always return 1.0 regardless of the mode.</span></span>

### <a name="span-idbc6h-partition-setspanspan-idbc6h-partition-setspanspan-idbc6h-partition-setspanbc6h-partition-set"></a><span data-ttu-id="1169f-234"><span id="BC6H-partition-set"></span><span id="bc6h-partition-set"></span><span id="BC6H-PARTITION-SET"></span>Festlegen der BC6H-Partition</span><span class="sxs-lookup"><span data-stu-id="1169f-234"><span id="BC6H-partition-set"></span><span id="bc6h-partition-set"></span><span id="BC6H-PARTITION-SET"></span>BC6H partition set</span></span>

<span data-ttu-id="1169f-235">Es gibt 32 mögliche Partitionen für eine Kachel mit zwei Regionen. Diese werden in der folgenden Tabelle definiert.</span><span class="sxs-lookup"><span data-stu-id="1169f-235">There are 32 possible partition sets for a two-region tile, and which are defined in the table below.</span></span> <span data-ttu-id="1169f-236">Jeder 4×4-Block stellt eine einzelne Form dar.</span><span class="sxs-lookup"><span data-stu-id="1169f-236">Each 4x4 block represents a single shape.</span></span>

![Tabelle mit Sätzen von BC6H-Partitionen](images/bc6h-partition-sets.png)

<span data-ttu-id="1169f-238">In dieser Tabelle mit Sätzen von Partitionen ist der fett formatierte und unterstrichene Eintrag der Speicherort des korrigierten Indexes für die Teilmenge1 (diese wird mit einer Bit weniger angegeben).</span><span class="sxs-lookup"><span data-stu-id="1169f-238">In this table of partition sets, the bolded and underlined entry is the location of the fix-up index for subset 1 (which is specified with one less bit).</span></span> <span data-ttu-id="1169f-239">Der korrigierte Index der Teilmenge0 ist immer 0, da die Partitionierung immer so angeordnet ist, dass der Index0 sich immer in der Teilmenge0 befindet.</span><span class="sxs-lookup"><span data-stu-id="1169f-239">The fix-up index for subset 0 is always index 0, as the partitioning is always arranged such that index 0 is always in subset 0.</span></span> <span data-ttu-id="1169f-240">Die Partitionsreihenfolge wird von oben links nach unten rechts und von links nach rechts und dann von oben nach unten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1169f-240">Partition order goes from top-left to bottom-right, moving left to right and then top to bottom.</span></span>

## <a name="span-idbc6h-compressed-endpoint-formatspanspan-idbc6h-compressed-endpoint-formatspanspan-idbc6h-compressed-endpoint-formatspanbc6h-compressed-endpoint-format"></a><span data-ttu-id="1169f-241"><span id="BC6H-compressed-endpoint-format"></span><span id="bc6h-compressed-endpoint-format"></span><span id="BC6H-COMPRESSED-ENDPOINT-FORMAT"></span>Komprimiertes Endpunktformat für BC6H</span><span class="sxs-lookup"><span data-stu-id="1169f-241"><span id="BC6H-compressed-endpoint-format"></span><span id="bc6h-compressed-endpoint-format"></span><span id="BC6H-COMPRESSED-ENDPOINT-FORMAT"></span>BC6H compressed endpoint format</span></span>


![Bitfelder für komprimierte BC6H-Endpunktformate](images/bc6h-headers-med.png)

<span data-ttu-id="1169f-243">Diese Tabelle zeigt die Bitfelder für die komprimierten Endpunkte als Funktion des Endpunktformats an, wobei jede Spalte eine Codierung und jede Zeile ein Bitfeld angibt.</span><span class="sxs-lookup"><span data-stu-id="1169f-243">This table shows the bit fields for the compressed endpoints as a function of the endpoint format, with each column specifying an encoding and each row specifying a bit field.</span></span> <span data-ttu-id="1169f-244">Dieser Ansatz nimmt 82Bit für Kacheln mit zwei Regionen und 65Bit für Kacheln mit einer Region in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="1169f-244">This approach takes up 82 bits for two-region tiles and 65 bits for one-region tiles.</span></span> <span data-ttu-id="1169f-245">Beispiel: die ersten 5Bit für die Codierung \[16 4\] einer Region (genauer gesagt: die Spalte ganz rechts) sind die Bit m\ [4:0\], die nächsten 10Bit sind die Bit rw\ [9:0\] usw., wobei die letzten 6Bit bw\ [10:15\] sind.</span><span class="sxs-lookup"><span data-stu-id="1169f-245">As an example, the first 5 bits for the one-region \[16 4\] encoding above (specifically the right-most column) are bits m\[4:0\], the next 10 bits are bits rw\[9:0\], and so on with the last 6 bits containing bw\[10:15\].</span></span>

<span data-ttu-id="1169f-246">Die Feldnamen in der obigen Tabelle sind wie folgt definiert:</span><span class="sxs-lookup"><span data-stu-id="1169f-246">The field names in the table above are defined as follows:</span></span>

| <span data-ttu-id="1169f-247">Feld</span><span class="sxs-lookup"><span data-stu-id="1169f-247">Field</span></span> | <span data-ttu-id="1169f-248">Variable</span><span class="sxs-lookup"><span data-stu-id="1169f-248">Variable</span></span>          |
|-------|-------------------|
| <span data-ttu-id="1169f-249">m</span><span class="sxs-lookup"><span data-stu-id="1169f-249">m</span></span>     | <span data-ttu-id="1169f-250">mode</span><span class="sxs-lookup"><span data-stu-id="1169f-250">mode</span></span>              |
| <span data-ttu-id="1169f-251">d</span><span class="sxs-lookup"><span data-stu-id="1169f-251">d</span></span>     | <span data-ttu-id="1169f-252">shape index</span><span class="sxs-lookup"><span data-stu-id="1169f-252">shape index</span></span>       |
| <span data-ttu-id="1169f-253">rw</span><span class="sxs-lookup"><span data-stu-id="1169f-253">rw</span></span>    | <span data-ttu-id="1169f-254">endpt\[0\].A\[0\]</span><span class="sxs-lookup"><span data-stu-id="1169f-254">endpt\[0\].A\[0\]</span></span> |
| <span data-ttu-id="1169f-255">rx</span><span class="sxs-lookup"><span data-stu-id="1169f-255">rx</span></span>    | <span data-ttu-id="1169f-256">endpt\[0\].B\[0\]</span><span class="sxs-lookup"><span data-stu-id="1169f-256">endpt\[0\].B\[0\]</span></span> |
| <span data-ttu-id="1169f-257">ry</span><span class="sxs-lookup"><span data-stu-id="1169f-257">ry</span></span>    | <span data-ttu-id="1169f-258">endpt\[1\].A\[0\]</span><span class="sxs-lookup"><span data-stu-id="1169f-258">endpt\[1\].A\[0\]</span></span> |
| <span data-ttu-id="1169f-259">rz</span><span class="sxs-lookup"><span data-stu-id="1169f-259">rz</span></span>    | <span data-ttu-id="1169f-260">endpt\[1\].B\[0\]</span><span class="sxs-lookup"><span data-stu-id="1169f-260">endpt\[1\].B\[0\]</span></span> |
| <span data-ttu-id="1169f-261">gw</span><span class="sxs-lookup"><span data-stu-id="1169f-261">gw</span></span>    | <span data-ttu-id="1169f-262">endpt\[0\].A\[1\]</span><span class="sxs-lookup"><span data-stu-id="1169f-262">endpt\[0\].A\[1\]</span></span> |
| <span data-ttu-id="1169f-263">gx</span><span class="sxs-lookup"><span data-stu-id="1169f-263">gx</span></span>    | <span data-ttu-id="1169f-264">endpt\[0\].B\[1\]</span><span class="sxs-lookup"><span data-stu-id="1169f-264">endpt\[0\].B\[1\]</span></span> |
| <span data-ttu-id="1169f-265">gy</span><span class="sxs-lookup"><span data-stu-id="1169f-265">gy</span></span>    | <span data-ttu-id="1169f-266">endpt\[1\].A\[1\]</span><span class="sxs-lookup"><span data-stu-id="1169f-266">endpt\[1\].A\[1\]</span></span> |
| <span data-ttu-id="1169f-267">gz</span><span class="sxs-lookup"><span data-stu-id="1169f-267">gz</span></span>    | <span data-ttu-id="1169f-268">endpt\[1\].B\[1\]</span><span class="sxs-lookup"><span data-stu-id="1169f-268">endpt\[1\].B\[1\]</span></span> |
| <span data-ttu-id="1169f-269">bw</span><span class="sxs-lookup"><span data-stu-id="1169f-269">bw</span></span>    | <span data-ttu-id="1169f-270">endpt\[0\].A\[2\]</span><span class="sxs-lookup"><span data-stu-id="1169f-270">endpt\[0\].A\[2\]</span></span> |
| <span data-ttu-id="1169f-271">bx</span><span class="sxs-lookup"><span data-stu-id="1169f-271">bx</span></span>    | <span data-ttu-id="1169f-272">endpt\[0\].B\[2\]</span><span class="sxs-lookup"><span data-stu-id="1169f-272">endpt\[0\].B\[2\]</span></span> |
| <span data-ttu-id="1169f-273">by</span><span class="sxs-lookup"><span data-stu-id="1169f-273">by</span></span>    | <span data-ttu-id="1169f-274">endpt\[1\].A\[2\]</span><span class="sxs-lookup"><span data-stu-id="1169f-274">endpt\[1\].A\[2\]</span></span> |
| <span data-ttu-id="1169f-275">bz</span><span class="sxs-lookup"><span data-stu-id="1169f-275">bz</span></span>    | <span data-ttu-id="1169f-276">endpt\[1\].B\[2\]</span><span class="sxs-lookup"><span data-stu-id="1169f-276">endpt\[1\].B\[2\]</span></span> |

 

<span data-ttu-id="1169f-277">Endpt\[i\], wobei i entweder 0 oder 1 ist und sich auf den 0. oder 1. Satz von Endpunkten bezieht.</span><span class="sxs-lookup"><span data-stu-id="1169f-277">Endpt\[i\], where i is either 0 or 1, refers to the 0th or 1st set of endpoints respectively.</span></span>
## <a name="span-idsign-extension-for-endpoint-valuesspanspan-idsign-extension-for-endpoint-valuesspanspan-idsign-extension-for-endpoint-valuesspansign-extension-for-endpoint-values"></a><span data-ttu-id="1169f-278"><span id="Sign-extension-for-endpoint-values"></span><span id="sign-extension-for-endpoint-values"></span><span id="SIGN-EXTENSION-FOR-ENDPOINT-VALUES"></span>Zeichenerweiterung für Endpunktwerte</span><span class="sxs-lookup"><span data-stu-id="1169f-278"><span id="Sign-extension-for-endpoint-values"></span><span id="sign-extension-for-endpoint-values"></span><span id="SIGN-EXTENSION-FOR-ENDPOINT-VALUES"></span>Sign extension for endpoint values</span></span>


<span data-ttu-id="1169f-279">Bei Kacheln mit zwei Regionen gibt es vier Endpunktwerte, für die eine Sign-Erweiterung möglich ist.</span><span class="sxs-lookup"><span data-stu-id="1169f-279">For two-region tiles, there are four endpoint values that can be sign extended.</span></span> <span data-ttu-id="1169f-280">Endpt\[0\].A wird nur dann signiert, wenn das Format ein Vorzeichen enthält. Die andere Endpunkte werden nur dann signiert, wenn der Endpunkt transformiert wurde oder das Format ein Format mit Vorzeichen ist.</span><span class="sxs-lookup"><span data-stu-id="1169f-280">Endpt\[0\].A is signed only if the format is a signed format; the other endpoints are signed only if the endpoint was transformed, or if the format is a signed format.</span></span> <span data-ttu-id="1169f-281">Der folgende Code veranschaulicht den Algorithmus für das Erweitern der Vorzeichen für Endpunktwerte mit zwei Regionen.</span><span class="sxs-lookup"><span data-stu-id="1169f-281">The code below demonstrates the algorithm for extending the sign of two-region endpoint values.</span></span>

``` syntax
static void sign_extend_two_region(Pattern &p, IntEndpts endpts[NREGIONS_TWO])
{
    for (int i=0; i<NCHANNELS; ++i)
    {
      if (BC6H::FORMAT == SIGNED_F16)
        endpts[0].A[i] = SIGN_EXTEND(endpts[0].A[i], p.chan[i].prec);
      if (p.transformed || BC6H::FORMAT == SIGNED_F16)
      {
        endpts[0].B[i] = SIGN_EXTEND(endpts[0].B[i], p.chan[i].delta[0]);
        endpts[1].A[i] = SIGN_EXTEND(endpts[1].A[i], p.chan[i].delta[1]);
        endpts[1].B[i] = SIGN_EXTEND(endpts[1].B[i], p.chan[i].delta[2]);
      }
    }
}
```

<span data-ttu-id="1169f-282">Für eine Kachel mit einer Region ist das Verhalten identisch, wobei endpt\ [1\] entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="1169f-282">For one-region tiles, the behavior is the same, only with endpt\[1\] removed.</span></span>

``` syntax
static void sign_extend_one_region(Pattern &p, IntEndpts endpts[NREGIONS_ONE])
{
    for (int i=0; i<NCHANNELS; ++i)
    {
    if (BC6H::FORMAT == SIGNED_F16)
        endpts[0].A[i] = SIGN_EXTEND(endpts[0].A[i], p.chan[i].prec);
    if (p.transformed || BC6H::FORMAT == SIGNED_F16) 
        endpts[0].B[i] = SIGN_EXTEND(endpts[0].B[i], p.chan[i].delta[0]);
    }
}
```

## <a name="span-idtransform-inversion-for-endpoint-valuesspanspan-idtransform-inversion-for-endpoint-valuesspanspan-idtransform-inversion-for-endpoint-valuesspantransform-inversion-for-endpoint-values"></a><span data-ttu-id="1169f-283"><span id="Transform-inversion-for-endpoint-values"></span><span id="transform-inversion-for-endpoint-values"></span><span id="TRANSFORM-INVERSION-FOR-ENDPOINT-VALUES"></span>Inversionstransformation der Endpunktwerte</span><span class="sxs-lookup"><span data-stu-id="1169f-283"><span id="Transform-inversion-for-endpoint-values"></span><span id="transform-inversion-for-endpoint-values"></span><span id="TRANSFORM-INVERSION-FOR-ENDPOINT-VALUES"></span>Transform inversion for endpoint values</span></span>


<span data-ttu-id="1169f-284">Bei Kacheln mit zwei Regionen wendet die Transformation den umgekehrten Wert der Codierungsdifferenz an, wobei der Basiswert von endpt\ [0\].A den drei anderen Einträgen hinzugefügt wird und insgesamt 9 hinzugefügte Vorgänge ergibt.</span><span class="sxs-lookup"><span data-stu-id="1169f-284">For two-region tiles, the transform applies the inverse of the difference encoding, adding the base value at endpt\[0\].A to the three other entries for a total of 9 add operations.</span></span> <span data-ttu-id="1169f-285">In der folgenden Abbildung wird der Basiswert als „A0” dargestellt und weist die höchste Gleitkommapräzision auf.</span><span class="sxs-lookup"><span data-stu-id="1169f-285">In the image below, the base value is represented as "A0" and has the highest floating point precision.</span></span> <span data-ttu-id="1169f-286">"A1", "B0" und "B1" sind alle vom Anchor-Wert berechnete Deltas. Diese Deltawerte werden mit geringerer Präzision dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1169f-286">"A1," "B0," and "B1" are all deltas calculated from the anchor value, and these delta values are represented with lower precision.</span></span> <span data-ttu-id="1169f-287">(A0 entspricht endpt\[0\].A, B0 entspricht endpt\[0\].B, A1 entspricht endpt\[1\].A und B1 entspricht endpt\[1\].B.)</span><span class="sxs-lookup"><span data-stu-id="1169f-287">(A0 corresponds to endpt\[0\].A, B0 corresponds to endpt\[0\].B, A1 corresponds to endpt\[1\].A, and B1 corresponds to endpt\[1\].B.)</span></span>

![Berechnung der Inversionstransformation der Endpunktwerte](images/bc6h-transform-inverse.png)

<span data-ttu-id="1169f-289">Für Kacheln mit einer Region gibt es nur eine Delta-Abweichung und daher nur 3 hinzugefügte Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="1169f-289">For one-region tiles there is only one delta offset, and therefore only 3 add operations.</span></span>

<span data-ttu-id="1169f-290">Das Dekomprimierprogramm muss sicherstellen, dass die Ergebnisse der Inversionstransformation nicht die Genauigkeit von endpt\[0\].a überschreiten.</span><span class="sxs-lookup"><span data-stu-id="1169f-290">The decompressor must ensure that that the results of the inverse transform will not overflow the precision of endpt\[0\].a.</span></span> <span data-ttu-id="1169f-291">Im Falle eines Überlaufs müssen die durch die Inversionstransformation enthaltenen Werte innerhalb der gleichen Anzahl von Bits umbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="1169f-291">In the case of an overflow, the values resulting from the inverse transform must wrap within the same number of bits.</span></span> <span data-ttu-id="1169f-292">Wenn die Genauigkeit von A0 „p” Bit ist, ist der Transformationsalgorithmus wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1169f-292">If the precision of A0 is "p" bits, then the transform algorithm is:</span></span>

`B0 = (B0 + A0) & ((1 << p) - 1)`

<span data-ttu-id="1169f-293">Für Formate mit Vorzeichen müssen die Ergebnisse der Delta-Berechnung ebenfalls eine Zeichenerweiterung enthalten.</span><span class="sxs-lookup"><span data-stu-id="1169f-293">For signed formats, the results of the delta calculation must be sign extended as well.</span></span> <span data-ttu-id="1169f-294">Wenn der Zeichenerweiterungsvorgang die Erweiterung beider Anzeichen berücksichtigt, wobei 0 positiv und 1 negativ ist, übernimmt die Zeichenerweiterung von 0 den vorherigen „Clamp”.</span><span class="sxs-lookup"><span data-stu-id="1169f-294">If the sign extension operation considers extending both signs, where 0 is positive and 1 is negative, then the sign extension of 0 takes care of the clamp above.</span></span> <span data-ttu-id="1169f-295">Außerdem muss nach dem vorigen „Clamp” nur der Wert 1 (negativ) mit einem Zeichen erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="1169f-295">Equivalently, after the clamp above, only a value of 1 (negative) needs to be sign extended.</span></span>

## <a name="span-idunquantization-of-color-endpointsspanspan-idunquantization-of-color-endpointsspanspan-idunquantization-of-color-endpointsspanunquantization-of-color-endpoints"></a><span data-ttu-id="1169f-296"><span id="Unquantization-of-color-endpoints"></span><span id="unquantization-of-color-endpoints"></span><span id="UNQUANTIZATION-OF-COLOR-ENDPOINTS"></span>Entquantisierung von Farbendpunkten</span><span class="sxs-lookup"><span data-stu-id="1169f-296"><span id="Unquantization-of-color-endpoints"></span><span id="unquantization-of-color-endpoints"></span><span id="UNQUANTIZATION-OF-COLOR-ENDPOINTS"></span>Unquantization of color endpoints</span></span>


<span data-ttu-id="1169f-297">Angesichts der nicht komprimierten Endpunkte ist der nächste Schritt die Ausführung einer anfänglichen Entquantisierung der Farbendpunkte.</span><span class="sxs-lookup"><span data-stu-id="1169f-297">Given the uncompressed endpoints, the next step is to perform an initial unquantization of the color endpoints.</span></span> <span data-ttu-id="1169f-298">Dies umfasst drei Schritte:</span><span class="sxs-lookup"><span data-stu-id="1169f-298">This involves three steps:</span></span>

-   <span data-ttu-id="1169f-299">Entquantisierung der Farbpaletten</span><span class="sxs-lookup"><span data-stu-id="1169f-299">An unquantization of the color palettes</span></span>
-   <span data-ttu-id="1169f-300">Interpolation der Paletten</span><span class="sxs-lookup"><span data-stu-id="1169f-300">Interpolation of the palettes</span></span>
-   <span data-ttu-id="1169f-301">Abschließen der Entquantisierung</span><span class="sxs-lookup"><span data-stu-id="1169f-301">Unquantization finalization</span></span>

<span data-ttu-id="1169f-302">Das Trennen des Entquantisierungsprozesses in zwei Schritte (Entquantisieren der Farbpalette vor der Interpolation und endgültiges Entquantisieren der Farbpalette nach der Interpolation) reduziert die Anzahl der Multiplikationsvorgänge im Vergleich zu einem vollständigen Entquantisierungsprozess vor der Interpolation der Palette.</span><span class="sxs-lookup"><span data-stu-id="1169f-302">Separating the unquantization process into two parts (color palette unquantization before interpolation and final unquantization after interpolation) reduces the number of multiplication operations required when compared to a full unquantization process before palette interpolation.</span></span>

<span data-ttu-id="1169f-303">Der folgende Code veranschaulicht das Verfahren zum Abrufen von Schätzungen der ursprünglichen 16-Bit-Farbwerte und die anschließende Nutzung der angegebenen Gewichtungswerte, um der Palette 6 weitere Farbwerte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1169f-303">The code below illustrates the process for retrieving estimates of the original 16-bit color values, and then using the supplied weight values to add 6 additional color values to the palette.</span></span> <span data-ttu-id="1169f-304">Der gleiche Vorgang wird auf jedem Kanal durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="1169f-304">The same operation is performed on each channel.</span></span>

``` syntax
int aWeight3[] = {0, 9, 18, 27, 37, 46, 55, 64};
int aWeight4[] = {0, 4, 9, 13, 17, 21, 26, 30, 34, 38, 43, 47, 51, 55, 60, 64};

// c1, c2: endpoints of a component
void generate_palette_unquantized(UINT8 uNumIndices, int c1, int c2, int prec, UINT16 palette[NINDICES])
{
    int* aWeights;
    if(uNumIndices == 8)
        aWeights = aWeight3;
    else  // uNumIndices == 16
        aWeights = aWeight4;

    int a = unquantize(c1, prec); 
    int b = unquantize(c2, prec);

    // interpolate
    for(int i = 0; i < uNumIndices; ++i)
        palette[i] = finish_unquantize((a * (64 - aWeights[i]) + b * aWeights[i] + 32) >> 6);
}
```

<span data-ttu-id="1169f-305">Im nächsten Codebeispiel wird der Interpolationsprozess veranschaulicht, mit folgender Erläuterung:</span><span class="sxs-lookup"><span data-stu-id="1169f-305">The next code sample demonstrates the interpolation process, with the following observations:</span></span>

-   <span data-ttu-id="1169f-306">Da der vollständige Bereich der Farbwerte der Funktion **Entquantisierung** (siehe unten) zwischen -32768 und 65535 liegt, wird der Interpolator mithilfe der Arithmetik-Berechnungen von 17-Bit mit Vorzeichen implementiert.</span><span class="sxs-lookup"><span data-stu-id="1169f-306">Since the full range of color values for the **unquantize** function (below) are from -32768 to 65535, the interpolator is implemented using 17-bit signed arithmetic.</span></span>
-   <span data-ttu-id="1169f-307">Nach der Interpolation werden die Werte an die Funktion **finish\_unquantize** übergeben (wie im dritten Beispiel in diesem Abschnitt beschrieben), die die endgültigen Skalierung anwendet.</span><span class="sxs-lookup"><span data-stu-id="1169f-307">After interpolation, the values are passed to the **finish\_unquantize** function (described in the third sample in this section), which applies the final scaling.</span></span>
-   <span data-ttu-id="1169f-308">Alle Hardware Dekomprimierprogramme müssen mithilfe dieser Funktion die Bit präzise wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="1169f-308">All hardware decompressors are required to return bit-accurate results with these functions.</span></span>

``` syntax
int unquantize(int comp, int uBitsPerComp)
{
    int unq, s = 0;
    switch(BC6H::FORMAT)
    {
    case UNSIGNED_F16:
        if(uBitsPerComp >= 15)
            unq = comp;
        else if(comp == 0)
            unq = 0;
        else if(comp == ((1 << uBitsPerComp) - 1))
            unq = 0xFFFF;
        else
            unq = ((comp << 16) + 0x8000) >> uBitsPerComp;
        break;

    case SIGNED_F16:
        if(uBitsPerComp >= 16)
            unq = comp;
        else
        {
            if(comp < 0)
            {
                s = 1;
                comp = -comp;
            }

            if(comp == 0)
                unq = 0;
            else if(comp >= ((1 << (uBitsPerComp - 1)) - 1))
                unq = 0x7FFF;
            else
                unq = ((comp << 15) + 0x4000) >> (uBitsPerComp-1);

            if(s)
                unq = -unq;
        }
        break;
    }
    return unq;
}
```

<span data-ttu-id="1169f-309">**finish\_unquantize** wird nach der Interpolation der Palette aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1169f-309">**finish\_unquantize** is called after palette interpolation.</span></span> <span data-ttu-id="1169f-310">Die Funktion **Entquantisierung** verschiebt die Skalierung von 31/32 für signierte und von 31/64 für nicht-signierte Zeichen.</span><span class="sxs-lookup"><span data-stu-id="1169f-310">The **unquantize** function postpones the scaling by 31/32 for signed, 31/64 for unsigned.</span></span> <span data-ttu-id="1169f-311">Dieses Verhalten ist erforderlich, um den Endwert in einem gültigen Halb-Bereich zu erhalten (-0x7BFF ~ 0x7BFF), nachdem die Interpolation der Palette abgeschlossen ist, um die Anzahl der erforderlichen Multiplikationen zu verringern.</span><span class="sxs-lookup"><span data-stu-id="1169f-311">This behavior is required to get the final value into valid half range(-0x7BFF ~ 0x7BFF) after the palette interpolation is completed in order to reduce the number of necessary multiplications.</span></span> <span data-ttu-id="1169f-312">**finish\_unquantize** wendet die endgültigen Skalierung an und gibt einen **kurzen Wert ohne Vorzeichen** wieder, der **halb** neu interpretiert.</span><span class="sxs-lookup"><span data-stu-id="1169f-312">**finish\_unquantize** applies the final scaling and returns an **unsigned short** value that gets reinterpreted into **half**.</span></span>

``` syntax
unsigned short finish_unquantize(int comp)
{
    if(BC6H::FORMAT == UNSIGNED_F16)
    {
        comp = (comp * 31) >> 6;                                         // scale the magnitude by 31/64
        return (unsigned short) comp;
    }
    else // (BC6H::FORMAT == SIGNED_F16)
    {
        comp = (comp < 0) ? -(((-comp) * 31) >> 5) : (comp * 31) >> 5;   // scale the magnitude by 31/32
        int s = 0;
        if(comp < 0)
        {
            s = 0x8000;
            comp = -comp;
        }
        return (unsigned short) (s | comp);
    }
}
```

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1169f-313"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1169f-313"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1169f-314">Texturblockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="1169f-314">Texture block compression</span></span>](texture-block-compression.md)

 

 




