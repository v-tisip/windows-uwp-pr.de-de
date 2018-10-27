---
title: BC7-Format
description: Das BC7-Format ist ein Format für die Texturkomprimierung, das für die hochwertige Komprimierung von RGB- und RGBA-Daten verwendet wird.
ms.assetid: 788B6E8C-9A1F-45F9-BE49-742285E8D8A6
keywords:
- BC7-Format
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 70380dd0bd07cfe0c81e8339f8606029663b47d4
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5687861"
---
# <a name="bc7-format"></a><span data-ttu-id="e3959-104">BC7-Format</span><span class="sxs-lookup"><span data-stu-id="e3959-104">BC7 format</span></span>


<span data-ttu-id="e3959-105">Das BC7-Format ist ein Format für die Texturkomprimierung, das für die hochwertige Komprimierung von RGB- und RGBA-Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3959-105">The BC7 format is a texture compression format used for high-quality compression of RGB and RGBA data.</span></span>

<span data-ttu-id="e3959-106">Informationen zu den Blockmodi des BC7-Formats finden Sie unter [Verweis auf den BC7-Format-Modus](https://msdn.microsoft.com/library/windows/desktop/hh308954).</span><span class="sxs-lookup"><span data-stu-id="e3959-106">For info about the block modes of the BC7 format, see [BC7 Format Mode Reference](https://msdn.microsoft.com/library/windows/desktop/hh308954).</span></span>

## <a name="span-idabout-bc7-dxgi-format-bc7spanspan-idabout-bc7-dxgi-format-bc7spanspan-idabout-bc7-dxgi-format-bc7spanabout-bc7dxgiformatbc7"></a><span data-ttu-id="e3959-107"><span id="About-BC7-DXGI-FORMAT-BC7"></span><span id="about-bc7-dxgi-format-bc7"></span><span id="ABOUT-BC7-DXGI-FORMAT-BC7"></span>Informationen zu BC7/DXGI\_FORMAT\_BC7</span><span class="sxs-lookup"><span data-stu-id="e3959-107"><span id="About-BC7-DXGI-FORMAT-BC7"></span><span id="about-bc7-dxgi-format-bc7"></span><span id="ABOUT-BC7-DXGI-FORMAT-BC7"></span>About BC7/DXGI\_FORMAT\_BC7</span></span>


<span data-ttu-id="e3959-108">BC7 wird durch die folgenden DXGI\_FORMAT-Enumerationswerte angegeben:</span><span class="sxs-lookup"><span data-stu-id="e3959-108">BC7 is specified by the following DXGI\_FORMAT enumeration values:</span></span>

-   <span data-ttu-id="e3959-109">**DXGI\_FORMAT\_BC7\_TYPELESS**.</span><span class="sxs-lookup"><span data-stu-id="e3959-109">**DXGI\_FORMAT\_BC7\_TYPELESS**.</span></span>
-   <span data-ttu-id="e3959-110">**DXGI\_FORMAT\_BC7\_UNORM**.</span><span class="sxs-lookup"><span data-stu-id="e3959-110">**DXGI\_FORMAT\_BC7\_UNORM**.</span></span>
-   <span data-ttu-id="e3959-111">**DXGI\_FORMAT\_BC7\_UNORM\_SRGB**.</span><span class="sxs-lookup"><span data-stu-id="e3959-111">**DXGI\_FORMAT\_BC7\_UNORM\_SRGB**.</span></span>

<span data-ttu-id="e3959-112">Das BC7-Format kann für Texturressourcen wie [Texture2D](https://msdn.microsoft.com/library/windows/desktop/bb205277) (einschließlich Arrays), Texture3D oder TextureCube (einschließlich Arrays) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3959-112">The BC7 format can be used for [Texture2D](https://msdn.microsoft.com/library/windows/desktop/bb205277) (including arrays), Texture3D, or TextureCube (including arrays) texture resources.</span></span> <span data-ttu-id="e3959-113">Das Format gilt ebenfalls für alle Mip-Map-Oberflächen, die mit diesen Ressourcen verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="e3959-113">Similarly, this format applies to any MIP-map surfaces associated with these resources.</span></span>

<span data-ttu-id="e3959-114">BC7 verwendet eine feste Blockgröße von 16Byte (128Bit) und eine feste Kachelgröße von 4×4-Texel.</span><span class="sxs-lookup"><span data-stu-id="e3959-114">BC7 uses a fixed block size of 16 bytes (128 bits) and a fixed tile size of 4x4 texels.</span></span> <span data-ttu-id="e3959-115">Genau wie mit vorherigen BC-Formaten werden Texturbilder, die größer als die unterstützte Kachelgröße (4×4) sind, durch die Verwendung mehrerer Blöcke komprimiert.</span><span class="sxs-lookup"><span data-stu-id="e3959-115">As with previous BC formats, texture images larger than the supported tile size (4x4) are compressed by using multiple blocks.</span></span> <span data-ttu-id="e3959-116">Diese Adressierungsidentität gilt auch für dreidimensionale Bilder, MIP-Maps, Cube-Zuordnungen und Texturarrays.</span><span class="sxs-lookup"><span data-stu-id="e3959-116">This addressing identity also applies to three-dimensional images and MIP-maps, cubemaps, and texture arrays.</span></span> <span data-ttu-id="e3959-117">Alle Bildkacheln müssen das gleiche Format aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e3959-117">All image tiles must be of the same format.</span></span>

<span data-ttu-id="e3959-118">BC7 komprimiert sowohl Drei-Kanal (RGB) und Vier-Kanal (RGBA) Datenimages mit Festpunkt.</span><span class="sxs-lookup"><span data-stu-id="e3959-118">BC7 compresses both three-channel (RGB) and four-channel (RGBA) fixed-point data images.</span></span> <span data-ttu-id="e3959-119">Normalerweise sind die Quelldaten 8Bit pro Farbkomponente (Kanal), obwohl das Format Quelldaten mit höheren Bits pro Farbkomponenten codieren kann.</span><span class="sxs-lookup"><span data-stu-id="e3959-119">Typically, source data is 8 bits per color component (channel), although the format is capable of encoding source data with higher bits per color component.</span></span> <span data-ttu-id="e3959-120">Alle Bildkacheln müssen das gleiche Format aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e3959-120">All image tiles must be of the same format.</span></span>

<span data-ttu-id="e3959-121">Der BC7-Decoder führt eine Dekomprimierung aus, bevor die Texturfilterung angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3959-121">The BC7 decoder performs decompression before texture filtering is applied.</span></span>

<span data-ttu-id="e3959-122">Die Hardware für die BC7-Dekomprimierung muss die Bit präzise wiedergeben. Das heißt, sie muss Ergebnisse zurückgeben, die mit dem in dieser Dokumentation beschriebenen Decoder übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="e3959-122">BC7 decompression hardware must be bit accurate; that is, the hardware must return results that are identical to the results returned by the decoder described in this document.</span></span>

## <a name="span-idbc7-implementationspanspan-idbc7-implementationspanspan-idbc7-implementationspanbc7-implementation"></a><span data-ttu-id="e3959-123"><span id="BC7-Implementation"></span><span id="bc7-implementation"></span><span id="BC7-IMPLEMENTATION"></span>Implementieren von BC7</span><span class="sxs-lookup"><span data-stu-id="e3959-123"><span id="BC7-Implementation"></span><span id="bc7-implementation"></span><span id="BC7-IMPLEMENTATION"></span>BC7 Implementation</span></span>


<span data-ttu-id="e3959-124">Eine BC7-Implementierung kann einen von 8 Modi bestimmen, inklusive den Modus des Bit mit dem unerheblichsten Wert des 16Byte-Blocks (128-Bit).</span><span class="sxs-lookup"><span data-stu-id="e3959-124">A BC7 implementation can specify one of 8 modes, with the mode specified in the least significant bit of the 16 byte (128 bit) block.</span></span> <span data-ttu-id="e3959-125">Der Modus wird mit Null oder mehr Bit mit einem Wert von 0 codiert, gefolgt von einer 1.</span><span class="sxs-lookup"><span data-stu-id="e3959-125">The mode is encoded by zero or more bits with a value of 0 followed by a 1.</span></span>

<span data-ttu-id="e3959-126">Ein BC7-Block kann mehrere Endpunktpaare enthalten.</span><span class="sxs-lookup"><span data-stu-id="e3959-126">A BC7 block can contain multiple endpoint pairs.</span></span> <span data-ttu-id="e3959-127">Der Satz von Indizes, die einem Endpunktpaar entsprechen, kann als „Teilmenge” bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="e3959-127">The set of indices that correspond to an endpoint pair may be referred to as a "subset."</span></span> <span data-ttu-id="e3959-128">In einigen Blockmodi wird die Darstellung der Endpunkte auch in einem Format codiert, das als „RBGP” bezeichnet wird, wobei das Bit „P” das gemeinsame Bit mit dem unerheblichsten Wert für die Farbkomponente des Endpunkts darstellt.</span><span class="sxs-lookup"><span data-stu-id="e3959-128">Also, in some block modes, the endpoint representation is encoded in a form that can be referred to as "RBGP," where the "P" bit represents a shared least significant bit for the color components of the endpoint.</span></span> <span data-ttu-id="e3959-129">Wenn beispielsweise die Darstellung des Endpunkts für das Format „RGB 5.5.5.1” ist, wird der Endpunkt als ein RGB-Wert von 6.6.6 interpretiert, wobei der Zustand des P-Bits das Bit mit dem unerheblichsten Wert jeder Komponente darstellt.</span><span class="sxs-lookup"><span data-stu-id="e3959-129">For example, if the endpoint representation for the format is "RGB 5.5.5.1," then the endpoint is interpreted as an RGB 6.6.6 value, where the state of the P-bit defines the least significant bit of each component.</span></span> <span data-ttu-id="e3959-130">Wenn die Darstellung für das Format für Quelldaten mit einem Alpha-Kanal „RGBAP 5.5.5.5.1” ist, wird der Endpunkt als RGBA 6.6.6.6 interpretiert.</span><span class="sxs-lookup"><span data-stu-id="e3959-130">Similarly, for source data with an alpha channel, if the representation for the format is "RGBAP 5.5.5.5.1," then the endpoint is interpreted as RGBA 6.6.6.6.</span></span> <span data-ttu-id="e3959-131">Je nach Blockmodus können Sie das gemeinsame Bit mit dem unerheblichsten Wert entweder für beide Endpunkten einer Teilmenge einzeln (2 P-Bit pro Teilmenge) oder zwischen Endpunkten einer Teilmenge gemeinsam (1 P-Bit pro Teilmenge) angeben.</span><span class="sxs-lookup"><span data-stu-id="e3959-131">Depending on the block mode, you can specify the shared least significant bit for either both endpoints of a subset individually (2 P-bits per subset), or shared between endpoints of a subset (1 P-bit per subset).</span></span>

<span data-ttu-id="e3959-132">Ein BC7-Block, der die Alpha-Komponente nicht explizit codiert, besteht aus Modus-Bit, Partition-Bit, komprimierten Endpunkten, komprimierten Indizes und einem optionalen P-Bit.</span><span class="sxs-lookup"><span data-stu-id="e3959-132">For BC7 blocks that don't explicitly encode the alpha component, a BC7 block consists of mode bits, partition bits, compressed endpoints, compressed indices, and an optional P-bit.</span></span> <span data-ttu-id="e3959-133">Die Endpunkte in den Blöcken haben eine reine RGB-Darstellung und die Alpha-Komponente wird als 1,0 für alle Texel in den Quelldaten decodiert.</span><span class="sxs-lookup"><span data-stu-id="e3959-133">In these blocks the endpoints have an RGB-only representation and the alpha component is decoded as 1.0 for all texels in the source data.</span></span>

<span data-ttu-id="e3959-134">Ein BC7-Block, der gemeinsame Farb- und Alphawertkomponenten hat, besteht aus Modus-Bit, komprimierten Endpunkten, komprimierten Indizes und optionalen Partition-Bit und einem P-Bit.</span><span class="sxs-lookup"><span data-stu-id="e3959-134">For BC7 blocks that have combined color and alpha components, a block consists of mode bits, compressed endpoints, compressed indices, and optional partition bits and a P-bit.</span></span> <span data-ttu-id="e3959-135">In diese Blöcken werden die Endpunktfarben im RGBA-Format dargestellt und die Alpha-Komponentenwerte werden zusammen mit den Werten der Farben interpoliert.</span><span class="sxs-lookup"><span data-stu-id="e3959-135">In these blocks, the endpoint colors are expressed in RGBA format, and alpha component values are interpolated alongside the color component values.</span></span>

<span data-ttu-id="e3959-136">Ein BC7-Block, der separate Farb- und Alpha-Komponenten hat, besteht aus Modus-Bit, Rotations-Bit, komprimierten Endpunkten, komprimierten Indizes und einem optionalen Index-Selektor-Bit.</span><span class="sxs-lookup"><span data-stu-id="e3959-136">For BC7 blocks that have separate color and alpha components, a block consists of mode bits, rotation bits, compressed endpoints, compressed indices, and an optional index selector bit.</span></span> <span data-ttu-id="e3959-137">Diese Blöcke haben einen separat codierten effektiven RGB-Vektor \[R, G, B\] und einen skalaren Alpha-Kanal \[A\].</span><span class="sxs-lookup"><span data-stu-id="e3959-137">These blocks have an effective RGB vector \[R, G, B\] and a scalar alpha channel \[A\] separately encoded.</span></span>

<span data-ttu-id="e3959-138">Die folgende Tabelle enthält die Komponenten der einzelnen Blocktypen.</span><span class="sxs-lookup"><span data-stu-id="e3959-138">The following table lists the components of each block type.</span></span>

| <span data-ttu-id="e3959-139">BC7-Block enthält...</span><span class="sxs-lookup"><span data-stu-id="e3959-139">BC7 block contains...</span></span>     | <span data-ttu-id="e3959-140">Modus-Bit</span><span class="sxs-lookup"><span data-stu-id="e3959-140">mode bits</span></span> | <span data-ttu-id="e3959-141">Rotations-Bit</span><span class="sxs-lookup"><span data-stu-id="e3959-141">rotation bits</span></span> | <span data-ttu-id="e3959-142">Index-Selektor-</span><span class="sxs-lookup"><span data-stu-id="e3959-142">index selector bit</span></span> | <span data-ttu-id="e3959-143">Partition-Bit</span><span class="sxs-lookup"><span data-stu-id="e3959-143">partition bits</span></span> | <span data-ttu-id="e3959-144">Komprimierte Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-144">compressed endpoints</span></span> | <span data-ttu-id="e3959-145">P-Bit</span><span class="sxs-lookup"><span data-stu-id="e3959-145">P-bit</span></span>    | <span data-ttu-id="e3959-146">Komprimierte Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-146">compressed indices</span></span> |
|---------------------------|-----------|---------------|--------------------|----------------|----------------------|----------|--------------------|
| <span data-ttu-id="e3959-147">Nur Farbkomponenten</span><span class="sxs-lookup"><span data-stu-id="e3959-147">color components only</span></span>     | <span data-ttu-id="e3959-148">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-148">required</span></span>  | <span data-ttu-id="e3959-149">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-149">N/A</span></span>           | <span data-ttu-id="e3959-150">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-150">N/A</span></span>                | <span data-ttu-id="e3959-151">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-151">required</span></span>       | <span data-ttu-id="e3959-152">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-152">required</span></span>             | <span data-ttu-id="e3959-153">Optional</span><span class="sxs-lookup"><span data-stu-id="e3959-153">optional</span></span> | <span data-ttu-id="e3959-154">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-154">required</span></span>           |
| <span data-ttu-id="e3959-155">Farb- + Alphawert kombiniert</span><span class="sxs-lookup"><span data-stu-id="e3959-155">color + alpha combined</span></span>    | <span data-ttu-id="e3959-156">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-156">required</span></span>  | <span data-ttu-id="e3959-157">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-157">N/A</span></span>           | <span data-ttu-id="e3959-158">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-158">N/A</span></span>                | <span data-ttu-id="e3959-159">Optional</span><span class="sxs-lookup"><span data-stu-id="e3959-159">optional</span></span>       | <span data-ttu-id="e3959-160">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-160">required</span></span>             | <span data-ttu-id="e3959-161">Optional</span><span class="sxs-lookup"><span data-stu-id="e3959-161">optional</span></span> | <span data-ttu-id="e3959-162">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-162">required</span></span>           |
| <span data-ttu-id="e3959-163">Separater Farb- und Alphawert</span><span class="sxs-lookup"><span data-stu-id="e3959-163">color and alpha separated</span></span> | <span data-ttu-id="e3959-164">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-164">required</span></span>  | <span data-ttu-id="e3959-165">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-165">required</span></span>      | <span data-ttu-id="e3959-166">Optional</span><span class="sxs-lookup"><span data-stu-id="e3959-166">optional</span></span>           | <span data-ttu-id="e3959-167">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-167">N/A</span></span>            | <span data-ttu-id="e3959-168">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-168">required</span></span>             | <span data-ttu-id="e3959-169">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="e3959-169">N/A</span></span>      | <span data-ttu-id="e3959-170">erforderlich</span><span class="sxs-lookup"><span data-stu-id="e3959-170">required</span></span>           |

 

<span data-ttu-id="e3959-171">BC7 definiert eine Farbpalette auf einer ungefähren Linie zwischen zwei Endpunkten.</span><span class="sxs-lookup"><span data-stu-id="e3959-171">BC7 defines a palette of colors on an approximate line between two endpoints.</span></span> <span data-ttu-id="e3959-172">Der Moduswert bestimmt die Anzahl der interpolierten Endpunktpaare pro Block.</span><span class="sxs-lookup"><span data-stu-id="e3959-172">The mode value determines the number of interpolating endpoint pairs per block.</span></span> <span data-ttu-id="e3959-173">BC7 speichert einen Farbpaletten-Index pro Texel.</span><span class="sxs-lookup"><span data-stu-id="e3959-173">BC7 stores one palette index per texel.</span></span>

<span data-ttu-id="e3959-174">Für jede Teilmenge an Indizes, die einem Endpunktpaar entsprechen, legt der Encoder den Zustand eines Bit der komprimierten Indexdaten für diese Teilmenge fest.</span><span class="sxs-lookup"><span data-stu-id="e3959-174">For each subset of indices that corresponds to a pair of endpoints, the encoder fixes the state of one bit of the compressed index data for that subset.</span></span> <span data-ttu-id="e3959-175">Dazu wird eine Reihenfolge der Endpunkte ausgewählt, mit der der Index für den angegebenen "korrigierten" Index das wichtigste Bit auf 0 festlegen kann. Dieses wird anschließend verworfen und es wird ein Bit pro Teilmenge gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e3959-175">It does so by choosing an endpoint order that allows the index for the designated "fix-up" index to set its most significant bit to 0, and which can then be discarded, saving one bit per subset.</span></span> <span data-ttu-id="e3959-176">Für Block-Modi mit nur einer einzigen Teilmenge ist der korrigierte Index immer der Index 0.</span><span class="sxs-lookup"><span data-stu-id="e3959-176">For block modes with only a single subset, the fix-up index is always index 0.</span></span>

## <a name="span-iddecoding-the-bc7-formatspanspan-iddecoding-the-bc7-formatspanspan-iddecoding-the-bc7-formatspandecoding-the-bc7-format"></a><span data-ttu-id="e3959-177"><span id="Decoding-the-BC7-Format"></span><span id="decoding-the-bc7-format"></span><span id="DECODING-THE-BC7-FORMAT"></span>Decodieren des BC7-Formats</span><span class="sxs-lookup"><span data-stu-id="e3959-177"><span id="Decoding-the-BC7-Format"></span><span id="decoding-the-bc7-format"></span><span id="DECODING-THE-BC7-FORMAT"></span>Decoding the BC7 Format</span></span>


<span data-ttu-id="e3959-178">Der folgende Pseudocode zeigt die Schritte zur Dekomprimierung der Pixel (x, y) bei einem 16-Byte BC7-Block an.</span><span class="sxs-lookup"><span data-stu-id="e3959-178">The following pseudocode outlines the steps to decompress the pixel at (x,y) given the 16 byte BC7 block.</span></span>

``` syntax
decompress_bc7(x, y, block)
{
    mode = extract_mode(block);
    
    //decode partition data from explicit partition bits
    subset_index = 0;
    num_subsets = 1;
    
    if (mode.type == 0 OR == 1 OR == 2 OR == 3 OR == 7)
    {
        num_subsets = get_num_subsets(mode.type);
        partition_set_id = extract_partition_set_id(mode, block);
        subset_index = get_partition_index(num_subsets, partition_set_id, x, y);
    }
    
    //extract raw, compressed endpoint bits
    UINT8 endpoint_array[num_subsets][4] = extract_endpoints(mode, block);
    
    //decode endpoint color and alpha for each subset
    fully_decode_endpoints(endpoint_array, mode, block);
    
    //endpoints are now complete.
    UINT8 endpoint_start[4] = endpoint_array[2 * subset_index];
    UINT8 endpoint_end[4]   = endpoint_array[2 * subset_index + 1];
        
    //Determine the palette index for this pixel
    alpha_index     = get_alpha_index(block, mode, x, y);
    alpha_bitcount  = get_alpha_bitcount(block, mode);
    color_index     = get_color_index(block, mode, x, y);
    color_bitcount  = get_color_bitcount(block, mode);

    //determine output
    UINT8 output[4];
    output.rgb = interpolate(endpoint_start.rgb, endpoint_end.rgb, color_index, color_bitcount);
    output.a   = interpolate(endpoint_start.a,   endpoint_end.a,   alpha_index, alpha_bitcount);
    
    if (mode.type == 4 OR == 5)
    {
        //Decode the 2 color rotation bits as follows:
        // 00 – Block format is Scalar(A) Vector(RGB) - no swapping
        // 01 – Block format is Scalar(R) Vector(AGB) - swap A and R
        // 10 – Block format is Scalar(G) Vector(RAB) - swap A and G
        // 11 - Block format is Scalar(B) Vector(RGA) - swap A and B
        rotation = extract_rot_bits(mode, block);
        output = swap_channels(output, rotation);
    }
    
}
```

<span data-ttu-id="e3959-179">Der folgende Pseudocode zeigt die Schritte an, um die Farbe eines Endpunkts und die Alpha-Komponenten für jede Teilmenge eines 16-Byte BC7-Blocks vollständig zu decodieren.</span><span class="sxs-lookup"><span data-stu-id="e3959-179">The followoing pseudocode outlines the steps to fully decode endpoint color and alpha components for each subset given a 16-byte BC7 block.</span></span>

``` syntax
fully_decode_endpoints(endpoint_array, mode, block)
{
    //first handle modes that have P-bits
    if (mode.type == 0 OR == 1 OR == 3 OR == 6 OR == 7)
    {
        for each endpoint i
        {
            //component-wise left-shift
            endpoint_array[i].rgba = endpoint_array[i].rgba << 1;
        }
        
        //if P-bit is shared
        if (mode.type == 1) 
        {
            pbit_zero = extract_pbit_zero(mode, block);
            pbit_one = extract_pbit_one(mode, block);
            
            //rgb component-wise insert pbits
            endpoint_array[0].rgb |= pbit_zero;
            endpoint_array[1].rgb |= pbit_zero;
            endpoint_array[2].rgb |= pbit_one;
            endpoint_array[3].rgb |= pbit_one;  
        }
        else //unique P-bit per endpoint
        {  
            pbit_array = extract_pbit_array(mode, block);
            for each endpoint i
            {
                endpoint_array[i].rgba |= pbit_array[i];
            }
        }
    }

    for each endpoint i
    {
        // Color_component_precision & alpha_component_precision includes pbit
        // left shift endpoint components so that their MSB lies in bit 7
        endpoint_array[i].rgb = endpoint_array[i].rgb << (8 - color_component_precision(mode));
        endpoint_array[i].a = endpoint_array[i].a << (8 - alpha_component_precision(mode));

        // Replicate each component's MSB into the LSBs revealed by the left-shift operation above
        endpoint_array[i].rgb = endpoint_array[i].rgb | (endpoint_array[i].rgb >> color_component_precision(mode));
        endpoint_array[i].a = endpoint_array[i].a | (endpoint_array[i].a >> alpha_component_precision(mode));
    }
        
    //If this mode does not explicitly define the alpha component
    //set alpha equal to 1.0
    if (mode.type == 0 OR == 1 OR == 2 OR == 3)
    {
        for each endpoint i
        {
            endpoint_array[i].a = 255; //i.e. alpha = 1.0f
        }
    }
}
```

<span data-ttu-id="e3959-180">Um jede interpolierte Komponente für jede Teilmenge zu generieren, verwenden Sie folgenden Algorithmus: „c” ist die generierende Komponente, „e0” ist die Komponente von Endpunkt 0 der Teilmenge und „e1” ist die entsprechende Komponente von Endpunkt 1 dieser Teilmenge.</span><span class="sxs-lookup"><span data-stu-id="e3959-180">To generate each interpolated component for each subset, use the following algorithm: let "c" be the component to generate; let "e0" be that component of endpoint 0 of the subset; and let "e1" be that component of endpoint 1 of the subset.</span></span>

``` syntax
UINT16 aWeight2[] = {0, 21, 43, 64};
UINT16 aWeight3[] = {0, 9, 18, 27, 37, 46, 55, 64};
UINT16 aWeight4[] = {0, 4, 9, 13, 17, 21, 26, 30, 34, 38, 43, 47, 51, 55, 60, 64};

UINT8 interpolate(UINT8 e0, UINT8 e1, UINT8 index, UINT8 indexprecision)
{
    if(indexprecision == 2)
        return (UINT8) (((64 - aWeights2[index])*UINT16(e0) + aWeights2[index]*UINT16(e1) + 32) >> 6);
    else if(indexprecision == 3)
        return (UINT8) (((64 - aWeights3[index])*UINT16(e0) + aWeights3[index]*UINT16(e1) + 32) >> 6);
    else // indexprecision == 4
        return (UINT8) (((64 - aWeights4[index])*UINT16(e0) + aWeights4[index]*UINT16(e1) + 32) >> 6);
}
```

<span data-ttu-id="e3959-181">Der folgende Pseudocode veranschaulicht, wie Sie Indizes und die Bit-Anzahl an Farb- und Alphawertkomponenten extrahieren.</span><span class="sxs-lookup"><span data-stu-id="e3959-181">The following pseudocode illustrates how to extract indices and bit counts for color and alpha components.</span></span> <span data-ttu-id="e3959-182">Blöcke mit separaten Farb- und Alphawerten verfügen auch über zwei Sätze an Indexdaten: eine für den Vektor-Kanal und eine für den skalaren Kanal.</span><span class="sxs-lookup"><span data-stu-id="e3959-182">Blocks with separate color and alpha also have two sets of index data: one for the vector channel, and one for the scalar channel.</span></span> <span data-ttu-id="e3959-183">Für Modus 4 sind diese Indizes unterschiedlich breit (2 oder 3Bit) und ein 1-Bit-Selektor gibt an, ob die Vektor- oder skalaren Daten die 3-Bit-Indizes verwenden.</span><span class="sxs-lookup"><span data-stu-id="e3959-183">For Mode 4, these indices are of differing widths (2 or 3 bits), and there is a one-bit selector which specifies whether the vector or scalar data uses the 3-bit indices.</span></span> <span data-ttu-id="e3959-184">(Das Extrahieren der Anzahl an Alpha-Bits ähnelt dem Extrahieren der Anzahl an Farb-Bits mit einem umgekehrtem Verhalten, das auf dem **IdxMode**-Bit basiert.)</span><span class="sxs-lookup"><span data-stu-id="e3959-184">(Extracting the alpha bit count is similar to extracting color bit count but with inverse behavior based on the **idxMode** bit.)</span></span>

``` syntax
bitcount get_color_bitcount(block, mode)
{
    if (mode.type == 0 OR == 1)
        return 3;
    
    if (mode.type == 2 OR == 3 OR == 5 OR == 7)
        return 2;
    
    if (mode.type == 6)
        return 4;
        
    //The only remaining case is Mode 4 with 1-bit index selector
    idxMode = extract_idxMode(block);
    if (idxMode == 0)
        return 2;
    else
        return 3;
}
```

## <a name="span-idbc7-format-mode-referencespanspan-idbc7-format-mode-referencespanspan-idbc7-format-mode-referencespanbc7-format-mode-reference"></a><span data-ttu-id="e3959-185"><span id="BC7-format-mode-reference"></span><span id="bc7-format-mode-reference"></span><span id="BC7-FORMAT-MODE-REFERENCE"></span>Verweis auf den BC7-Format-Modus</span><span class="sxs-lookup"><span data-stu-id="e3959-185"><span id="BC7-format-mode-reference"></span><span id="bc7-format-mode-reference"></span><span id="BC7-FORMAT-MODE-REFERENCE"></span>BC7 format mode reference</span></span>


<span data-ttu-id="e3959-186">Dieser Abschnitt enthält eine Liste der 8Block-Modi und Bit-Zuordnungen für BC7-Blöcke im Texturkomprimierungsformat.</span><span class="sxs-lookup"><span data-stu-id="e3959-186">This section contains a list of the 8 block modes and bit allocations for BC7 texture compression format blocks.</span></span>

<span data-ttu-id="e3959-187">Die Farben für jede Teilmenge in einem Block werden durch zwei explizite Endpunktfarben und ein Set an interpolierten Farben zwischen den beiden dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e3959-187">The colors for each subset within a block are represented by two explicit endpoint colors and a set of interpolated colors between them.</span></span> <span data-ttu-id="e3959-188">Je nach den der Genauigkeit des Block-Indexes kann jede Teilmenge über 4, 8 oder 16 mögliche Farben verfügen.</span><span class="sxs-lookup"><span data-stu-id="e3959-188">Depending on the block's index precision, each subset can have 4, 8 or 16 possible colors.</span></span>

### <a name="span-idmode-0spanspan-idmode-0spanspan-idmode-0spanmode-0"></a><span data-ttu-id="e3959-189"><span id="Mode-0"></span><span id="mode-0"></span><span id="MODE-0"></span>Modus 0</span><span class="sxs-lookup"><span data-stu-id="e3959-189"><span id="Mode-0"></span><span id="mode-0"></span><span id="MODE-0"></span>Mode 0</span></span>

<span data-ttu-id="e3959-190">BC7-Modus 0 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-190">BC7 Mode 0 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-191">Nur Farbkomponenten (kein Alpha)</span><span class="sxs-lookup"><span data-stu-id="e3959-191">Color components only (no alpha)</span></span>
-   <span data-ttu-id="e3959-192">3Teilmengen pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-192">3 subsets per block</span></span>
-   <span data-ttu-id="e3959-193">RGBP 4.4.4.1-Endpunkte mit einem eindeutigen P-Bit pro Endpunkt</span><span class="sxs-lookup"><span data-stu-id="e3959-193">RGBP 4.4.4.1 endpoints with a unique P-bit per endpoint</span></span>
-   <span data-ttu-id="e3959-194">3-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-194">3-bit indices</span></span>
-   <span data-ttu-id="e3959-195">16 Partitionen</span><span class="sxs-lookup"><span data-stu-id="e3959-195">16 partitions</span></span>

![Modus 0-Bit-Layout](images/bc7-mode0.png)

### <a name="span-idmode-1spanspan-idmode-1spanspan-idmode-1spanmode-1"></a><span data-ttu-id="e3959-197"><span id="Mode-1"></span><span id="mode-1"></span><span id="MODE-1"></span>Modus 1</span><span class="sxs-lookup"><span data-stu-id="e3959-197"><span id="Mode-1"></span><span id="mode-1"></span><span id="MODE-1"></span>Mode 1</span></span>

<span data-ttu-id="e3959-198">BC7-Modus 1 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-198">BC7 Mode 1 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-199">Nur Farbkomponenten (kein Alpha)</span><span class="sxs-lookup"><span data-stu-id="e3959-199">Color components only (no alpha)</span></span>
-   <span data-ttu-id="e3959-200">2Teilmengen pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-200">2 subsets per block</span></span>
-   <span data-ttu-id="e3959-201">RGBP 6.6.6.1 Endpunkte mit einem gemeinsamen P-Bit pro Teilmenge)</span><span class="sxs-lookup"><span data-stu-id="e3959-201">RGBP 6.6.6.1 endpoints with a shared P-bit per subset)</span></span>
-   <span data-ttu-id="e3959-202">3-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-202">3-bit indices</span></span>
-   <span data-ttu-id="e3959-203">64 Partitionen</span><span class="sxs-lookup"><span data-stu-id="e3959-203">64 partitions</span></span>

![Modus 1-Bit-Layout](images/bc7-mode1.png)

### <a name="span-idmode-2spanspan-idmode-2spanspan-idmode-2spanmode-2"></a><span data-ttu-id="e3959-205"><span id="Mode-2"></span><span id="mode-2"></span><span id="MODE-2"></span>Modus 2</span><span class="sxs-lookup"><span data-stu-id="e3959-205"><span id="Mode-2"></span><span id="mode-2"></span><span id="MODE-2"></span>Mode 2</span></span>

<span data-ttu-id="e3959-206">BC7-Modus 2 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-206">BC7 Mode 2 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-207">Nur Farbkomponenten (kein Alpha)</span><span class="sxs-lookup"><span data-stu-id="e3959-207">Color components only (no alpha)</span></span>
-   <span data-ttu-id="e3959-208">3Teilmengen pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-208">3 subsets per block</span></span>
-   <span data-ttu-id="e3959-209">RGB 5.5.5-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-209">RGB 5.5.5 endpoints</span></span>
-   <span data-ttu-id="e3959-210">2-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-210">2-bit indices</span></span>
-   <span data-ttu-id="e3959-211">64 Partitionen</span><span class="sxs-lookup"><span data-stu-id="e3959-211">64 partitions</span></span>

![Modus 2-Bit-Layout](images/bc7-mode2.png)

### <a name="span-idmode-3spanspan-idmode-3spanspan-idmode-3spanmode-3"></a><span data-ttu-id="e3959-213"><span id="Mode-3"></span><span id="mode-3"></span><span id="MODE-3"></span>Modus 3</span><span class="sxs-lookup"><span data-stu-id="e3959-213"><span id="Mode-3"></span><span id="mode-3"></span><span id="MODE-3"></span>Mode 3</span></span>

<span data-ttu-id="e3959-214">BC7-Modus3 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-214">BC7 Mode 3 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-215">Nur Farbkomponenten (kein Alpha)</span><span class="sxs-lookup"><span data-stu-id="e3959-215">Color components only (no alpha)</span></span>
-   <span data-ttu-id="e3959-216">2Teilmengen pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-216">2 subsets per block</span></span>
-   <span data-ttu-id="e3959-217">RGBP 7.7.7.1 Endpunkte mit einem eindeutigen P-Bit pro Teilmenge)</span><span class="sxs-lookup"><span data-stu-id="e3959-217">RGBP 7.7.7.1 endpoints with a unique P-bit per subset)</span></span>
-   <span data-ttu-id="e3959-218">2-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-218">2-bit indices</span></span>
-   <span data-ttu-id="e3959-219">64 Partitionen</span><span class="sxs-lookup"><span data-stu-id="e3959-219">64 partitions</span></span>

![Modus 3-Bit-Layout](images/bc7-mode3.png)

### <a name="span-idmode-4spanspan-idmode-4spanspan-idmode-4spanmode-4"></a><span data-ttu-id="e3959-221"><span id="Mode-4"></span><span id="mode-4"></span><span id="MODE-4"></span>Modus 4</span><span class="sxs-lookup"><span data-stu-id="e3959-221"><span id="Mode-4"></span><span id="mode-4"></span><span id="MODE-4"></span>Mode 4</span></span>

<span data-ttu-id="e3959-222">BC7-Modus4 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-222">BC7 Mode 4 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-223">Farbkomponenten mit separater Alpha-Komponente</span><span class="sxs-lookup"><span data-stu-id="e3959-223">Color components with separate alpha component</span></span>
-   <span data-ttu-id="e3959-224">1Teilmenge pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-224">1 subset per block</span></span>
-   <span data-ttu-id="e3959-225">RGB 5.5.5-Farbendpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-225">RGB 5.5.5 color endpoints</span></span>
-   <span data-ttu-id="e3959-226">6-Bit-Alpha-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-226">6-bit alpha endpoints</span></span>
-   <span data-ttu-id="e3959-227">16x2-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-227">16 x 2-bit indices</span></span>
-   <span data-ttu-id="e3959-228">16x3-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-228">16 x 3-bit indices</span></span>
-   <span data-ttu-id="e3959-229">Rotation der 2-Bit-Komponente</span><span class="sxs-lookup"><span data-stu-id="e3959-229">2-bit component rotation</span></span>
-   <span data-ttu-id="e3959-230">1-Bit-Index-Selektor (unabhängig davon, ob 2- oder 3-Bit-Indizes verwendet werden)</span><span class="sxs-lookup"><span data-stu-id="e3959-230">1-bit index selector (whether the 2- or 3-bit indices are used)</span></span>

![Modus 4-Bit-Layout](images/bc7-mode4.png)

### <a name="span-idmode-5spanspan-idmode-5spanspan-idmode-5spanmode-5"></a><span data-ttu-id="e3959-232"><span id="Mode-5"></span><span id="mode-5"></span><span id="MODE-5"></span>Modus 5</span><span class="sxs-lookup"><span data-stu-id="e3959-232"><span id="Mode-5"></span><span id="mode-5"></span><span id="MODE-5"></span>Mode 5</span></span>

<span data-ttu-id="e3959-233">BC7-Modus5 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-233">BC7 Mode 5 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-234">Farbkomponenten mit separater Alpha-Komponente</span><span class="sxs-lookup"><span data-stu-id="e3959-234">Color components with separate alpha component</span></span>
-   <span data-ttu-id="e3959-235">1Teilmenge pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-235">1 subset per block</span></span>
-   <span data-ttu-id="e3959-236">RGB 7.7.7-Farbendpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-236">RGB 7.7.7 color endpoints</span></span>
-   <span data-ttu-id="e3959-237">6-Bit-Alpha-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="e3959-237">6-bit alpha endpoints</span></span>
-   <span data-ttu-id="e3959-238">16x2-Bit-Farbindizes</span><span class="sxs-lookup"><span data-stu-id="e3959-238">16 x 2-bit color indices</span></span>
-   <span data-ttu-id="e3959-239">16x2-Bit-Alpha-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-239">16 x 2-bit alpha indices</span></span>
-   <span data-ttu-id="e3959-240">Rotation der 2-Bit-Komponente</span><span class="sxs-lookup"><span data-stu-id="e3959-240">2-bit component rotation</span></span>

![Modus 5-Bit-Layout](images/bc7-mode5.png)

### <a name="span-idmode-6spanspan-idmode-6spanspan-idmode-6spanmode-6"></a><span data-ttu-id="e3959-242"><span id="Mode-6"></span><span id="mode-6"></span><span id="MODE-6"></span>Modus 6</span><span class="sxs-lookup"><span data-stu-id="e3959-242"><span id="Mode-6"></span><span id="mode-6"></span><span id="MODE-6"></span>Mode 6</span></span>

<span data-ttu-id="e3959-243">BC7-Modus6 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-243">BC7 Mode 6 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-244">Kombinierte Farb- und Alpha-Komponenten</span><span class="sxs-lookup"><span data-stu-id="e3959-244">Combined color and alpha components</span></span>
-   <span data-ttu-id="e3959-245">Eine Teilmenge pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-245">One subset per block</span></span>
-   <span data-ttu-id="e3959-246">RGBAP 7.7.7.7.1-Farb- (und Alpha)-Endpunkte (eindeutiger P-Bit pro Endpunkt)</span><span class="sxs-lookup"><span data-stu-id="e3959-246">RGBAP 7.7.7.7.1 color (and alpha) endpoints (unique P-bit per endpoint)</span></span>
-   <span data-ttu-id="e3959-247">16x3-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-247">16 x 4-bit indices</span></span>

![Modus 6-Bit-Layout](images/bc7-mode6.png)

### <a name="span-idmode-7spanspan-idmode-7spanspan-idmode-7spanmode-7"></a><span data-ttu-id="e3959-249"><span id="Mode-7"></span><span id="mode-7"></span><span id="MODE-7"></span>Modus 7</span><span class="sxs-lookup"><span data-stu-id="e3959-249"><span id="Mode-7"></span><span id="mode-7"></span><span id="MODE-7"></span>Mode 7</span></span>

<span data-ttu-id="e3959-250">BC7-Modus7 weist folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="e3959-250">BC7 Mode 7 has the following characteristics:</span></span>

-   <span data-ttu-id="e3959-251">Kombinierte Farb- und Alpha-Komponenten</span><span class="sxs-lookup"><span data-stu-id="e3959-251">Combined color and alpha components</span></span>
-   <span data-ttu-id="e3959-252">2Teilmengen pro Block</span><span class="sxs-lookup"><span data-stu-id="e3959-252">2 subsets per block</span></span>
-   <span data-ttu-id="e3959-253">RGBAP 5.5.5.5.1-Farb- (und Alpha)-Endpunkte (eindeutiger P-Bit pro Endpunkt)</span><span class="sxs-lookup"><span data-stu-id="e3959-253">RGBAP 5.5.5.5.1 color (and alpha) endpoints (unique P-bit per endpoint)</span></span>
-   <span data-ttu-id="e3959-254">2-Bit-Indizes</span><span class="sxs-lookup"><span data-stu-id="e3959-254">2-bit indices</span></span>
-   <span data-ttu-id="e3959-255">64 Partitionen</span><span class="sxs-lookup"><span data-stu-id="e3959-255">64 partitions</span></span>

![Modus7-Bit-Layout](images/bc7-mode7.png)

### <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span data-ttu-id="e3959-257"><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Hinweise</span><span class="sxs-lookup"><span data-stu-id="e3959-257"><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>Remarks</span></span>

<span data-ttu-id="e3959-258">Modus8 (das Bit mit dem unerheblichsten Wert ist auf 0x00 Byte festgelegt) ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="e3959-258">Mode 8 (the least significant byte is set to 0x00) is reserved.</span></span> <span data-ttu-id="e3959-259">Verwenden Sie es nicht für den Encoder.</span><span class="sxs-lookup"><span data-stu-id="e3959-259">Don't use it in your encoder.</span></span> <span data-ttu-id="e3959-260">Wenn Sie diesen Modus an die Hardware übergeben, wird ein initialisierter Block mit nur Nullen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="e3959-260">If you pass this mode to the hardware, a block initialized to all zeroes is returned.</span></span>

<span data-ttu-id="e3959-261">In BC7 können Sie die Alpha-Komponente auf eine der folgenden Weisen codieren:</span><span class="sxs-lookup"><span data-stu-id="e3959-261">In BC7, you can encode the alpha component in one of the following ways:</span></span>

-   <span data-ttu-id="e3959-262">Blocktypen ohne explizite Alpha-Komponenten-Codierung.</span><span class="sxs-lookup"><span data-stu-id="e3959-262">Block types without explicit alpha component encoding.</span></span> <span data-ttu-id="e3959-263">In diesen Blöcken enthalten die Farbendpunkte eine reine RGB-Codierung, wobei die Alpha-Komponente auf 1,0 für alle Texel decodiert ist.</span><span class="sxs-lookup"><span data-stu-id="e3959-263">In these blocks, the color endpoints have an RGB-only encoding, with the alpha component decoded to 1.0 for all texels.</span></span>
-   <span data-ttu-id="e3959-264">Blocktypen mit kombinierten Farb- und Alpha-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="e3959-264">Block types with combined color and alpha components.</span></span> <span data-ttu-id="e3959-265">Die Endpunkt-Farbwerte in diesen Blöcken werden im RGBA-Format angegeben und die Werte der Alpha-Komponente werden zusammen mit den Farbwerten interpoliert.</span><span class="sxs-lookup"><span data-stu-id="e3959-265">In these blocks, the endpoint color values are specified in the RGBA format, and the alpha component values are interpolated along with the color values.</span></span>
-   <span data-ttu-id="e3959-266">Blocktypen mit separaten Farb- und Alpha-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="e3959-266">Block types with separated color and alpha components.</span></span> <span data-ttu-id="e3959-267">Die Farb- und Alphawerte dieser Blöcke werden separat angegeben und enthalten jeweils ihr eigenes Set an Indizes.</span><span class="sxs-lookup"><span data-stu-id="e3959-267">In these blocks the color and alpha values are specified separately, each with their own set of indices.</span></span> <span data-ttu-id="e3959-268">Daher verfügen sie über einen separat codierten effektiven Vektor- und einen skalaren Kanal, in dem der Vektor häufig die Farbkanäle \[R, G, B\] angibt und der skalare Kanal den Alpha-Kanal angibt \[A\].</span><span class="sxs-lookup"><span data-stu-id="e3959-268">As a result, they have an effective vector and a scalar channel separately encoded, where the vector commonly specifies the color channels \[R, G, B\] and the scalar specifies the alpha channel \[A\].</span></span> <span data-ttu-id="e3959-269">Zur Unterstützung dieses Ansatzes wird ein eigenes 2-Bitfeld in der Codierung bereitgestellt, das die Spezifikation der separaten Kanal-Codierung als skalaren Wert zulässt.</span><span class="sxs-lookup"><span data-stu-id="e3959-269">To support this approach, a separate 2-bit field is provided in the encoding, which permits the specification of the separate channel encoding as a scalar value.</span></span> <span data-ttu-id="e3959-270">Daher kann der Block eine der folgenden vier verschiedenen Darstellungen dieser Alpha-Codierung haben (wie durch das 2-Bitfeld angezeigt):</span><span class="sxs-lookup"><span data-stu-id="e3959-270">As a result, the block can have one of the following four different representations of this alpha encoding (as indicated by the 2-bit field):</span></span>
    -   <span data-ttu-id="e3959-271">RGB|A: separater Alpha-Kanal</span><span class="sxs-lookup"><span data-stu-id="e3959-271">RGB|A: alpha channel separate</span></span>
    -   <span data-ttu-id="e3959-272">AGB|R: „roter” separater Alpha-Kanal</span><span class="sxs-lookup"><span data-stu-id="e3959-272">AGB|R: "red" color channel separate</span></span>
    -   <span data-ttu-id="e3959-273">RAB|G: „grüner” separater Alpha-Kanal</span><span class="sxs-lookup"><span data-stu-id="e3959-273">RAB|G: "green" color channel separate</span></span>
    -   <span data-ttu-id="e3959-274">RGA|B: „blauer” separater Alpha-Kanal</span><span class="sxs-lookup"><span data-stu-id="e3959-274">RGA|B: "blue" color channel separate</span></span>

    <span data-ttu-id="e3959-275">Der Decoder ordnet die Kanalreihenfolge nach der Decodierung wieder auf RGBA an, damit das interne Blockformat für den Entwickler unsichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="e3959-275">The decoder reorders the channel order back to RGBA after decoding, so the internal block format is invisible to the developer.</span></span> <span data-ttu-id="e3959-276">Schwarze Kanäle mit eigenen Farb- und Alpha-Komponenten verfügen auch über zwei Sätze an Indexdaten: einen für den Satz an Vektor-Kanälen und einen für den skalaren Kanal.</span><span class="sxs-lookup"><span data-stu-id="e3959-276">Blacks with separate color and alpha components also have two sets of index data: one for the vectored set of channels, and one for the scalar channel.</span></span> <span data-ttu-id="e3959-277">(Im Modus4 sind diese Indizes unterschiedlich breit\[2 oder 3Bit\].</span><span class="sxs-lookup"><span data-stu-id="e3959-277">(In the case of Mode 4, these indices are of differing widths \[2 or 3 bits\].</span></span> <span data-ttu-id="e3959-278">Modus4 enthält auch einen 1-Bit-Selektor, der angibt, ob der Vektor- oder der skalare Kanal die 3-Bit-Indizes verwendet.)</span><span class="sxs-lookup"><span data-stu-id="e3959-278">Mode 4 also contains a 1-bit selector that specifies whether the vector or the scalar channel uses the 3-bit indices.)</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e3959-279"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e3959-279"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e3959-280">Texturblockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="e3959-280">Texture block compression</span></span>](texture-block-compression.md)

 

 




