---
title: Undurchsichtige und 1-Bit-Alpha-Texturen
description: Das Texturformat BC1 ist für Texturen, die undurchsichtig sind oder eine transparente Farbe haben.
ms.assetid: 8C53ACDD-72ED-4307-B4F3-2FCF9A9F53EC
keywords:
- Undurchsichtige und 1-Bit-Alpha-Texturen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 4227a3ad77eadaa40e47420a5fdab6d65c875da5
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8338537"
---
# <a name="span-iddirect3dconceptsopaqueand1-bitalphatexturesspanopaque-and-1-bit-alpha-textures"></a><span data-ttu-id="560d3-104"><span id="direct3dconcepts.opaque_and_1-bit_alpha_textures"></span>Undurchsichtige und 1-Bit-Alpha-Texturen</span><span class="sxs-lookup"><span data-stu-id="560d3-104"><span id="direct3dconcepts.opaque_and_1-bit_alpha_textures"></span>Opaque and 1-bit alpha textures</span></span>


<span data-ttu-id="560d3-105">Das Texturformat BC1 ist für Texturen, die undurchsichtig sind oder eine transparente Farbe haben.</span><span class="sxs-lookup"><span data-stu-id="560d3-105">Texture format BC1 is for textures that are opaque or have a single transparent color.</span></span>

<span data-ttu-id="560d3-106">Für jeden undurchsichtigen oder 1-Bit-Alpha-Block sind zwei 16-Bit-Werte (RGB-5:6:5-Format) und eine 4x4-Bitmap mit 2 Bits pro Pixel gespeichert.</span><span class="sxs-lookup"><span data-stu-id="560d3-106">For each opaque or 1-bit alpha block, two 16-bit values (RGB 5:6:5 format) and a 4x4 bitmap with 2 bits per pixel are stored.</span></span> <span data-ttu-id="560d3-107">Dies ergibt insgesamt 64Bit für 16 Texel oder vier Bits pro Texel.</span><span class="sxs-lookup"><span data-stu-id="560d3-107">This totals 64 bits for 16 texels, or four bits per texel.</span></span> <span data-ttu-id="560d3-108">Im Block Bitmap stehen 2 Bits pro Texel zwischen den vier Farben zur Auswahl, von denen zwei in den codierten Daten gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="560d3-108">In the block bitmap, there are 2 bits per texel to select between the four colors, two of which are stored in the encoded data.</span></span> <span data-ttu-id="560d3-109">Die beiden anderen Farben werden von diesen gespeicherten Farben mittels linearer Interpolation abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="560d3-109">The other two colors are derived from these stored colors by linear interpolation.</span></span> <span data-ttu-id="560d3-110">Dieser Aufbau ist im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="560d3-110">This layout is shown in the following diagram.</span></span>

![Diagramm des Bitmap-Layouts](images/colors1.png)

<span data-ttu-id="560d3-112">Das 1-Bit-Alpha-Format unterscheidet sich vom undurchsichtigen Format durch einen Vergleich der zwei 16-Bit-Farbwerte, die im Block gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="560d3-112">The 1-bit alpha format is distinguished from the opaque format by comparing the two 16-bit color values stored in the block.</span></span> <span data-ttu-id="560d3-113">Sie werden als ganze Zahlen ohne Vorzeichen behandelt.</span><span class="sxs-lookup"><span data-stu-id="560d3-113">They are treated as unsigned integers.</span></span> <span data-ttu-id="560d3-114">Wenn die erste Farbe größer als die zweite ist, bedeutet dies, dass nur undurchsichtige Texel definiert sind.</span><span class="sxs-lookup"><span data-stu-id="560d3-114">If the first color is greater than the second, it implies that only opaque texels are defined.</span></span> <span data-ttu-id="560d3-115">Dies bedeutet, dass vier Farben zum Darstellen der Texel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="560d3-115">This means four colors are used to represent the texels.</span></span> <span data-ttu-id="560d3-116">Bei der Codierung mit vier Farben gibt es zwei abgeleitete Farben und alle vier Farben werden in RGB-Farbraum gleichmäßig verteilt.</span><span class="sxs-lookup"><span data-stu-id="560d3-116">In four-color encoding, there are two derived colors and all four colors are equally distributed in RGB color space.</span></span> <span data-ttu-id="560d3-117">Dieses Format ist vergleichbar mit dem RGB-5:6:5-Format.</span><span class="sxs-lookup"><span data-stu-id="560d3-117">This format is analogous to RGB 5:6:5 format.</span></span> <span data-ttu-id="560d3-118">Andernfalls werden für die 1-Bit-Alpha-Transparenz drei Farben verwendet, und die vierte ist zum Darstellen von transparenten Texeln reserviert.</span><span class="sxs-lookup"><span data-stu-id="560d3-118">Otherwise, for 1-bit alpha transparency, three colors are used and the fourth is reserved to represent transparent texels.</span></span>

<span data-ttu-id="560d3-119">Bei der Codierung mit drei Farben gibt es eine abgeleitete Farbe und der vierte 2-Bit-Code ist zum Anzeigen eines transparenten Texels reserviert (Alpha-Informationen).</span><span class="sxs-lookup"><span data-stu-id="560d3-119">In three-color encoding, there is one derived color and the fourth 2-bit code is reserved to indicate a transparent texel (alpha information).</span></span> <span data-ttu-id="560d3-120">Dieses Format ist analog zu RGBA-5:5:5:1, in dem das letzte Bit verwendet wird, um die Alphamaske zu codieren.</span><span class="sxs-lookup"><span data-stu-id="560d3-120">This format is analogous to RGBA 5:5:5:1, where the final bit is used for encoding the alpha mask.</span></span>

<span data-ttu-id="560d3-121">Das folgende Codebeispiel veranschaulicht den Algorithmus für die Entscheidung, ob eine Codierung mit drei oder vier Farben ausgewählt wird:</span><span class="sxs-lookup"><span data-stu-id="560d3-121">The following code example illustrates the algorithm for deciding whether three- or four-color encoding is selected:</span></span>

```
if (color_0 > color_1) 
{
    // Four-color block: derive the other two colors. 
    
    // 00 = color_0, 01 = color_1, 10 = color_2, 11 = color_3
    // These 2-bit codes correspond to the 2-bit fields 
    // stored in the 64-bit block.
    color_2 = (2 * color_0 + color_1 + 1) / 3;
    color_3 = (color_0 + 2 * color_1 + 1) / 3;
}    
else
{ 
    // Three-color block: derive the other color.
    // 00 = color_0,  01 = color_1,  10 = color_2,  
    // 11 = transparent.
    // These 2-bit codes correspond to the 2-bit fields 
    // stored in the 64-bit block. 
    color_2 = (color_0 + color_1) / 2;    
    color_3 = transparent;    

}
```

<span data-ttu-id="560d3-122">Es wird empfohlen, dass Sie die RGBA-Komponenten des Transparenzpixels vor dem Vermischen auf 0 (null) setzen.</span><span class="sxs-lookup"><span data-stu-id="560d3-122">It is recommended that you set the RGBA components of the transparency pixel to zero before blending.</span></span>

<span data-ttu-id="560d3-123">Die folgenden Tabellen zeigen das Speicherlayout für den 8-Byte-Block.</span><span class="sxs-lookup"><span data-stu-id="560d3-123">The following tables show the memory layout for the 8-byte block.</span></span> <span data-ttu-id="560d3-124">Es wird vorausgesetzt, dass der erste Index der Y-Koordinate entspricht und der zweite Index der X-Koordinate entspricht.</span><span class="sxs-lookup"><span data-stu-id="560d3-124">It is assumed that the first index corresponds to the y-coordinate and the second corresponds to the x-coordinate.</span></span> <span data-ttu-id="560d3-125">Beispielsweise bezieht sich Texel\ [1\]\[2\] auf das Texturzuordnungspixel bei (x,y) = (2,1).</span><span class="sxs-lookup"><span data-stu-id="560d3-125">For example, Texel\[1\]\[2\] refers to the texture map pixel at (x,y) = (2,1).</span></span>

<span data-ttu-id="560d3-126">Im folgenden findet sich das Speicherlayout für den 8-Byte-Block (64-Bit):</span><span class="sxs-lookup"><span data-stu-id="560d3-126">The following is the memory layout for the 8-byte (64-bit) block:</span></span>

| <span data-ttu-id="560d3-127">Word-Adresse</span><span class="sxs-lookup"><span data-stu-id="560d3-127">Word address</span></span> | <span data-ttu-id="560d3-128">16-Bit-Word</span><span class="sxs-lookup"><span data-stu-id="560d3-128">16-bit word</span></span>    |
|--------------|----------------|
| <span data-ttu-id="560d3-129">0</span><span class="sxs-lookup"><span data-stu-id="560d3-129">0</span></span>            | <span data-ttu-id="560d3-130">Farbe\_0</span><span class="sxs-lookup"><span data-stu-id="560d3-130">Color\_0</span></span>       |
| <span data-ttu-id="560d3-131">1</span><span class="sxs-lookup"><span data-stu-id="560d3-131">1</span></span>            | <span data-ttu-id="560d3-132">Farbe\_1</span><span class="sxs-lookup"><span data-stu-id="560d3-132">Color\_1</span></span>       |
| <span data-ttu-id="560d3-133">2</span><span class="sxs-lookup"><span data-stu-id="560d3-133">2</span></span>            | <span data-ttu-id="560d3-134">Bitmap-Word\_0</span><span class="sxs-lookup"><span data-stu-id="560d3-134">Bitmap Word\_0</span></span> |
| <span data-ttu-id="560d3-135">3</span><span class="sxs-lookup"><span data-stu-id="560d3-135">3</span></span>            | <span data-ttu-id="560d3-136">Bitmap Word\_1</span><span class="sxs-lookup"><span data-stu-id="560d3-136">Bitmap Word\_1</span></span> |

 

<span data-ttu-id="560d3-137">Farbe\_0 und Farbe\_1, die Farben der beiden Extreme sind wie folgt angeordnet:</span><span class="sxs-lookup"><span data-stu-id="560d3-137">Color\_0 and Color\_1, the colors at the two extremes, are laid out as follows:</span></span>

| <span data-ttu-id="560d3-138">Bits</span><span class="sxs-lookup"><span data-stu-id="560d3-138">Bits</span></span>        | <span data-ttu-id="560d3-139">Farbe</span><span class="sxs-lookup"><span data-stu-id="560d3-139">Color</span></span>                 |
|-------------|-----------------------|
| <span data-ttu-id="560d3-140">4:0 (LSB\*)</span><span class="sxs-lookup"><span data-stu-id="560d3-140">4:0 (LSB\*)</span></span> | <span data-ttu-id="560d3-141">Blau-Komponente</span><span class="sxs-lookup"><span data-stu-id="560d3-141">Blue color component</span></span>  |
| <span data-ttu-id="560d3-142">10:5</span><span class="sxs-lookup"><span data-stu-id="560d3-142">10:5</span></span>        | <span data-ttu-id="560d3-143">Grün-Komponente</span><span class="sxs-lookup"><span data-stu-id="560d3-143">Green color component</span></span> |
| <span data-ttu-id="560d3-144">15:11</span><span class="sxs-lookup"><span data-stu-id="560d3-144">15:11</span></span>       | <span data-ttu-id="560d3-145">Rot-Komponente</span><span class="sxs-lookup"><span data-stu-id="560d3-145">Red color component</span></span>   |

 

<span data-ttu-id="560d3-146">\*niederwertigstes Bit</span><span class="sxs-lookup"><span data-stu-id="560d3-146">\*least-significant bit</span></span>

<span data-ttu-id="560d3-147">Bitmap-Word\_0 wird wie folgt dargestellt:</span><span class="sxs-lookup"><span data-stu-id="560d3-147">Bitmap Word\_0 is laid out as follows:</span></span>

| <span data-ttu-id="560d3-148">Bits</span><span class="sxs-lookup"><span data-stu-id="560d3-148">Bits</span></span>          | <span data-ttu-id="560d3-149">Texel</span><span class="sxs-lookup"><span data-stu-id="560d3-149">Texel</span></span>           |
|---------------|-----------------|
| <span data-ttu-id="560d3-150">1:0 (LSB)</span><span class="sxs-lookup"><span data-stu-id="560d3-150">1:0 (LSB)</span></span>     | <span data-ttu-id="560d3-151">Texel\[0\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="560d3-151">Texel\[0\]\[0\]</span></span> |
| <span data-ttu-id="560d3-152">3:2</span><span class="sxs-lookup"><span data-stu-id="560d3-152">3:2</span></span>           | <span data-ttu-id="560d3-153">Texel\[0\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="560d3-153">Texel\[0\]\[1\]</span></span> |
| <span data-ttu-id="560d3-154">5:4</span><span class="sxs-lookup"><span data-stu-id="560d3-154">5:4</span></span>           | <span data-ttu-id="560d3-155">Texel\[0\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="560d3-155">Texel\[0\]\[2\]</span></span> |
| <span data-ttu-id="560d3-156">7:6</span><span class="sxs-lookup"><span data-stu-id="560d3-156">7:6</span></span>           | <span data-ttu-id="560d3-157">Texel\[0\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="560d3-157">Texel\[0\]\[3\]</span></span> |
| <span data-ttu-id="560d3-158">9:8</span><span class="sxs-lookup"><span data-stu-id="560d3-158">9:8</span></span>           | <span data-ttu-id="560d3-159">Texel\[1\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="560d3-159">Texel\[1\]\[0\]</span></span> |
| <span data-ttu-id="560d3-160">11:10</span><span class="sxs-lookup"><span data-stu-id="560d3-160">11:10</span></span>         | <span data-ttu-id="560d3-161">Texel\[1\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="560d3-161">Texel\[1\]\[1\]</span></span> |
| <span data-ttu-id="560d3-162">13:12</span><span class="sxs-lookup"><span data-stu-id="560d3-162">13:12</span></span>         | <span data-ttu-id="560d3-163">Texel\[1\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="560d3-163">Texel\[1\]\[2\]</span></span> |
| <span data-ttu-id="560d3-164">15:14 (MSB\*)</span><span class="sxs-lookup"><span data-stu-id="560d3-164">15:14 (MSB\*)</span></span> | <span data-ttu-id="560d3-165">Texel\[1\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="560d3-165">Texel\[1\]\[3\]</span></span> |

 

<span data-ttu-id="560d3-166">\*höchstwertiges Bit (MSB)</span><span class="sxs-lookup"><span data-stu-id="560d3-166">\*most significant bit (MSB)</span></span>

<span data-ttu-id="560d3-167">Bitmap-Word\_1 wird wie folgt dargestellt:</span><span class="sxs-lookup"><span data-stu-id="560d3-167">Bitmap Word\_1 is laid out as follows:</span></span>

| <span data-ttu-id="560d3-168">Bits</span><span class="sxs-lookup"><span data-stu-id="560d3-168">Bits</span></span>        | <span data-ttu-id="560d3-169">Texel</span><span class="sxs-lookup"><span data-stu-id="560d3-169">Texel</span></span>           |
|-------------|-----------------|
| <span data-ttu-id="560d3-170">1:0 (LSB)</span><span class="sxs-lookup"><span data-stu-id="560d3-170">1:0 (LSB)</span></span>   | <span data-ttu-id="560d3-171">Texel\[2\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="560d3-171">Texel\[2\]\[0\]</span></span> |
| <span data-ttu-id="560d3-172">3:2</span><span class="sxs-lookup"><span data-stu-id="560d3-172">3:2</span></span>         | <span data-ttu-id="560d3-173">Texel\[2\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="560d3-173">Texel\[2\]\[1\]</span></span> |
| <span data-ttu-id="560d3-174">5:4</span><span class="sxs-lookup"><span data-stu-id="560d3-174">5:4</span></span>         | <span data-ttu-id="560d3-175">Texel\[2\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="560d3-175">Texel\[2\]\[2\]</span></span> |
| <span data-ttu-id="560d3-176">7:6</span><span class="sxs-lookup"><span data-stu-id="560d3-176">7:6</span></span>         | <span data-ttu-id="560d3-177">Texel\[2\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="560d3-177">Texel\[2\]\[3\]</span></span> |
| <span data-ttu-id="560d3-178">9:8</span><span class="sxs-lookup"><span data-stu-id="560d3-178">9:8</span></span>         | <span data-ttu-id="560d3-179">Texel\[3\]\[0\]</span><span class="sxs-lookup"><span data-stu-id="560d3-179">Texel\[3\]\[0\]</span></span> |
| <span data-ttu-id="560d3-180">11:10</span><span class="sxs-lookup"><span data-stu-id="560d3-180">11:10</span></span>       | <span data-ttu-id="560d3-181">Texel\[3\]\[1\]</span><span class="sxs-lookup"><span data-stu-id="560d3-181">Texel\[3\]\[1\]</span></span> |
| <span data-ttu-id="560d3-182">13:12</span><span class="sxs-lookup"><span data-stu-id="560d3-182">13:12</span></span>       | <span data-ttu-id="560d3-183">Texel\[3\]\[2\]</span><span class="sxs-lookup"><span data-stu-id="560d3-183">Texel\[3\]\[2\]</span></span> |
| <span data-ttu-id="560d3-184">15:14 (MSB)</span><span class="sxs-lookup"><span data-stu-id="560d3-184">15:14 (MSB)</span></span> | <span data-ttu-id="560d3-185">Texel\[3\]\[3\]</span><span class="sxs-lookup"><span data-stu-id="560d3-185">Texel\[3\]\[3\]</span></span> |

 

## <a name="span-idexampleofopaquecolorencodingspanspan-idexampleofopaquecolorencodingspanspan-idexampleofopaquecolorencodingspanexample-of-opaque-color-encoding"></a><span data-ttu-id="560d3-186"><span id="Example_of_Opaque_Color_Encoding"></span><span id="example_of_opaque_color_encoding"></span><span id="EXAMPLE_OF_OPAQUE_COLOR_ENCODING"></span>Beispiel für eine undurchsichtige Codierung</span><span class="sxs-lookup"><span data-stu-id="560d3-186"><span id="Example_of_Opaque_Color_Encoding"></span><span id="example_of_opaque_color_encoding"></span><span id="EXAMPLE_OF_OPAQUE_COLOR_ENCODING"></span>Example of opaque color encoding</span></span>


<span data-ttu-id="560d3-187">Als Beispiel für die undurchsichtige Codierung wird davon ausgegangen, dass die Farben rot und schwarz an den Extremen liegen.</span><span class="sxs-lookup"><span data-stu-id="560d3-187">As an example of opaque encoding, assume that the colors red and black are at the extremes.</span></span> <span data-ttu-id="560d3-188">Rot ist Farbe\_0 und schwarz ist Farbe\_1.</span><span class="sxs-lookup"><span data-stu-id="560d3-188">Red is color\_0, and black is color\_1.</span></span> <span data-ttu-id="560d3-189">Es gibt vier interpolierte Farben, die den einheitlich verteilten Verlauf dazwischen bilden.</span><span class="sxs-lookup"><span data-stu-id="560d3-189">There are four interpolated colors that form the uniformly distributed gradient between them.</span></span> <span data-ttu-id="560d3-190">Um die Werte für die 4x4-Bitmap zu ermitteln, werden die folgenden Berechnungen verwendet:</span><span class="sxs-lookup"><span data-stu-id="560d3-190">To determine the values for the 4x4 bitmap, the following calculations are used:</span></span>

```
00 ? color_0
01 ? color_1
10 ? 2/3 color_0 + 1/3 color_1
11 ? 1/3 color_0 + 2/3 color_1
```

<span data-ttu-id="560d3-191">Die Bitmap sieht dann wie im folgenden Diagramm aus.</span><span class="sxs-lookup"><span data-stu-id="560d3-191">The bitmap then looks like the following diagram.</span></span>

![Diagramm des erweiterten Bitmap Layouts](images/colors2.png)

<span data-ttu-id="560d3-193">Dies sieht wie die nachstehend dargestellten Reihe von Farben aus.</span><span class="sxs-lookup"><span data-stu-id="560d3-193">This looks like the following illustrated series of colors.</span></span>

<span data-ttu-id="560d3-194">**Hinweis:**  In einem Bild wird Pixel (0,0) oben links angezeigt.</span><span class="sxs-lookup"><span data-stu-id="560d3-194">**Note** In an image, pixel (0,0) appears on the top left.</span></span>

 

![Abbildungeines undurchsichtig codierten Farbverlaufs](images/redsquares.png)

## <a name="span-idexampleof1bitalphaencodingspanspan-idexampleof1bitalphaencodingspanspan-idexampleof1bitalphaencodingspanexample-of-1-bit-alpha-encoding"></a><span data-ttu-id="560d3-196"><span id="Example_of_1_Bit_Alpha_Encoding"></span><span id="example_of_1_bit_alpha_encoding"></span><span id="EXAMPLE_OF_1_BIT_ALPHA_ENCODING"></span>Beispiel einer 1-Bit-Alpha-Kodierung</span><span class="sxs-lookup"><span data-stu-id="560d3-196"><span id="Example_of_1_Bit_Alpha_Encoding"></span><span id="example_of_1_bit_alpha_encoding"></span><span id="EXAMPLE_OF_1_BIT_ALPHA_ENCODING"></span>Example of 1-bit alpha encoding</span></span>


<span data-ttu-id="560d3-197">Dieses Format wird ausgewählt, wenn die vorzeichenlose 16-Bit-Ganzzahl, Farbe\_0, kleiner ist als die vorzeichenlose 16-Bit-Ganzzahl, Farbe\_1.</span><span class="sxs-lookup"><span data-stu-id="560d3-197">This format is selected when the unsigned 16-bit integer, color\_0, is less than the unsigned 16-bit integer, color\_1.</span></span> <span data-ttu-id="560d3-198">Ein Beispiel, in dem dieses Format verwendet werden kann, sind Blätter an einem Baum, dargestellt gegen einen blauen Himmel.</span><span class="sxs-lookup"><span data-stu-id="560d3-198">An example of where this format can be used is leaves on a tree, shown against a blue sky.</span></span> <span data-ttu-id="560d3-199">Während drei Grünabstufungen weiterhin für die Blätter verfügbar sind, können einige Texel als transparent gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="560d3-199">Some texels can be marked as transparent while three shades of green are still available for the leaves.</span></span> <span data-ttu-id="560d3-200">Zwei Farben fixieren die Extreme und die dritte Farbe ist eine interpolierte Farbe.</span><span class="sxs-lookup"><span data-stu-id="560d3-200">Two colors fix the extremes, and the third is an interpolated color.</span></span>

<span data-ttu-id="560d3-201">Die nachstehende Abbildung ist ein Beispiel für ein solches Bild.</span><span class="sxs-lookup"><span data-stu-id="560d3-201">The following illustration is an example of such a picture.</span></span>

![Abbildungder 1-Bit-Alpha-Codierung](images/greenthing.png)

<span data-ttu-id="560d3-203">Wird das Bild weiß dargestellt, wäre das Texel als transparent codiert.</span><span class="sxs-lookup"><span data-stu-id="560d3-203">Where the image is shown as white, the texel would be encoded as transparent.</span></span> <span data-ttu-id="560d3-204">Die RGBA-Komponenten der transparenten Texel sollten vor dem Vermischen auf NULL gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="560d3-204">The RGBA components of the transparent texels should be set to zero before blending.</span></span>

<span data-ttu-id="560d3-205">Die Bitmap-Codierung für die Farben und die Transparenz wird unter Anwendung der folgenden Berechnungen bestimmt.</span><span class="sxs-lookup"><span data-stu-id="560d3-205">The bitmap encoding for the colors and the transparency is determined using the following calculations.</span></span>

```
00 ? color_0
01 ? color_1
10 ? 1/2 color_0 + 1/2 color_1
11   ?   Transparent
```

<span data-ttu-id="560d3-206">Die Bitmap sieht dann wie im folgenden Diagramm aus.</span><span class="sxs-lookup"><span data-stu-id="560d3-206">The bitmap then looks like the following diagram.</span></span>

![Diagramm des erweiterten Bitmap Layouts](images/colors3.png)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="560d3-208"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="560d3-208"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="560d3-209">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="560d3-209">Compressed texture resources</span></span>](compressed-texture-resources.md)

 

 




