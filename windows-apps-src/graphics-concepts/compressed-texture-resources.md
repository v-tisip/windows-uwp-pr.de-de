---
title: Komprimierte Texturressourcen
description: Texturabbildungen sind digitale Bilder, die auf dreidimensionale Formen gezeichnete werden, um diesen mehr Details zu verleihen.
ms.assetid: 2DD5FF94-A029-4694-B103-26946C8DFBC1
keywords:
- Komprimierte Texturressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9318479fffc415e94407166bd1be20a93691a179
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8945294"
---
# <a name="compressed-texture-resources"></a><span data-ttu-id="1b038-104">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="1b038-104">Compressed texture resources</span></span>


<span data-ttu-id="1b038-105">Texturzuordnungen sind digitale Bilder, die auf dreidimensionale Formen gezeichnet werden, um diesen mehr Details zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="1b038-105">Texture maps are digitized images drawn on three-dimensional shapes to add visual detail.</span></span> <span data-ttu-id="1b038-106">Sie werden während der Rasterung in diesen Formen wiedergegeben. Der Prozess kann große Mengen des Systembuses und des Speichers verbrauchen.</span><span class="sxs-lookup"><span data-stu-id="1b038-106">They are mapped into these shapes during rasterization, and the process can consume large amounts of both the system bus and memory.</span></span> <span data-ttu-id="1b038-107">Um den von den Texturen verbrauchten Speicherplatz zu reduzieren, unterstützt Direct3D die Komprimierung von Texturoberflächen.</span><span class="sxs-lookup"><span data-stu-id="1b038-107">To reduce the amount of memory consumed by textures, Direct3D supports the compression of texture surfaces.</span></span> <span data-ttu-id="1b038-108">Einige Direct3D-Geräte bieten eine systemeigene Unterstützung für komprimierte Texturoberflächen.</span><span class="sxs-lookup"><span data-stu-id="1b038-108">Some Direct3D devices support compressed texture surfaces natively.</span></span> <span data-ttu-id="1b038-109">Wenn Sie auf solchen Geräten eine komprimierte Oberfläche erstellt und die Daten geladen haben, kann die Oberfläche in Direct3D wie jede andere Texturoberfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1b038-109">On such devices, when you have created a compressed surface and loaded the data into it, the surface can be used in Direct3D like any other texture surface.</span></span> <span data-ttu-id="1b038-110">Direct3D verarbeitet die Dekomprimierung, wenn die Textur einem 3D-Objekt zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="1b038-110">Direct3D handles decompression when the texture is mapped to a 3D object.</span></span>

## <a name="span-idstorage-efficiency-and-texture-compressionspanspan-idstorage-efficiency-and-texture-compressionspanspan-idstorage-efficiency-and-texture-compressionspanstorage-efficiency-and-texture-compression"></a><span data-ttu-id="1b038-111"><span id="Storage-Efficiency-and-Texture-Compression"></span><span id="storage-efficiency-and-texture-compression"></span><span id="STORAGE-EFFICIENCY-AND-TEXTURE-COMPRESSION"></span>Speichereffizienz und Texturkomprimierung</span><span class="sxs-lookup"><span data-stu-id="1b038-111"><span id="Storage-Efficiency-and-Texture-Compression"></span><span id="storage-efficiency-and-texture-compression"></span><span id="STORAGE-EFFICIENCY-AND-TEXTURE-COMPRESSION"></span>Storage efficiency and texture compression</span></span>


<span data-ttu-id="1b038-112">Alle Formate für die Texturkomprimierung sind Potenzen von2.</span><span class="sxs-lookup"><span data-stu-id="1b038-112">All texture compression formats are powers of two.</span></span> <span data-ttu-id="1b038-113">Obwohl dies nicht bedeutet, dass eine Textur unbedingt quadratisch ist, bedeutet es, dass es sich bei x und y um eine Potenz von2 handelt.</span><span class="sxs-lookup"><span data-stu-id="1b038-113">While this does not mean that a texture is necessarily square, it does mean that both x and y are powers of two.</span></span> <span data-ttu-id="1b038-114">Wenn eine Textur z.B. ursprünglich 512x128Byte ist, wäre das nächsten Mipmapping 256x64 usw., wobei jede Ebene mit einer Potenz von2 verkleinert wird.</span><span class="sxs-lookup"><span data-stu-id="1b038-114">For example, if a texture is originally 512 by 128 bytes, the next mipmapping would be 256 by 64 and so on, with each level decreasing by a power of two.</span></span> <span data-ttu-id="1b038-115">Auf niedrigeren Ebenen, wenn die Textur auf 16x2 und 8x1 gefiltert wird, gibt es „verschwendete” Bits, da der Komprimierungsblock immer ein 4x4-Texelblock ist.</span><span class="sxs-lookup"><span data-stu-id="1b038-115">At lower levels, where the texture is filtered to 16 by 2 and 8 by 1, there will be wasted bits because the compression block is always a 4 by 4 block of texels.</span></span> <span data-ttu-id="1b038-116">Nicht genutzte Teile des Blocks werden aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="1b038-116">Unused portions of the block are padded.</span></span>

<span data-ttu-id="1b038-117">Obwohl auf der untersten Ebene verschwendete Bits existieren, ist der Gesamtgewinn erheblich.</span><span class="sxs-lookup"><span data-stu-id="1b038-117">Although there are wasted bits at the lowest levels, the overall gain is still significant.</span></span> <span data-ttu-id="1b038-118">Der schlimmste Fall ist theoretisch eine 2000x1 Textur (2⁰ Potenz).</span><span class="sxs-lookup"><span data-stu-id="1b038-118">The worst case is, in theory, a 2K by 1 texture (2⁰ power).</span></span> <span data-ttu-id="1b038-119">Dabei wird nur eine einzelne Zeile der Pixel pro Block codiert, während der Rest des Blocks nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1b038-119">Here, only a single row of pixels is encoded per block, while the rest of the block is unused.</span></span>

## <a name="span-idmixing-formats-within-a-single-texturespanspan-idmixing-formats-within-a-single-texturespanspan-idmixing-formats-within-a-single-texturespanmixing-formats-within-a-single-texture"></a><span data-ttu-id="1b038-120"><span id="Mixing-Formats-Within-a-Single-Texture"></span><span id="mixing-formats-within-a-single-texture"></span><span id="MIXING-FORMATS-WITHIN-A-SINGLE-TEXTURE"></span>Kombinieren von Formaten innerhalb einer einzigen Textur</span><span class="sxs-lookup"><span data-stu-id="1b038-120"><span id="Mixing-Formats-Within-a-Single-Texture"></span><span id="mixing-formats-within-a-single-texture"></span><span id="MIXING-FORMATS-WITHIN-A-SINGLE-TEXTURE"></span>Mixing formats within a single texture</span></span>


<span data-ttu-id="1b038-121">Es muss beachtet werden, dass jede einzelne Textur angeben muss, ob ihre Daten als 64 oder 128Bit pro Gruppe von 16Texeln gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="1b038-121">It is important to note that any single texture must specify that its data is stored as 64 or 128 bits per group of 16 texels.</span></span> <span data-ttu-id="1b038-122">Wenn 64-Bit-Blöcke - im BC1-Blockkomprimierungformat – für die Textur verwendet werden, ist es möglich, undurchsichtige und 1-Bit-Alpha-Kanal-Formate auf einer pro-Block-Basis innerhalb der gleichen Textur zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="1b038-122">If 64-bit blocks - that is, block compression format BC1 - are used for the texture, it is possible to mix the opaque and 1-bit alpha formats on a per-block basis within the same texture.</span></span> <span data-ttu-id="1b038-123">Anders ausgedrückt wird der Vergleich der Größe der Ganzzahl ohne Vorzeichen für die Farbe\_0 und Farbe\_1 eindeutig für jeden Block mit 16 Texeln ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1b038-123">In other words, the comparison of the unsigned integer magnitude of color\_0 and color\_1 is performed uniquely for each block of 16 texels.</span></span>

<span data-ttu-id="1b038-124">Wenn 128-Bit-Blöcke verwendet werden, muss der Alphakanal entweder im expliziten ( BC2-Format) oder interpolierten Modus (BC3-Format) für die gesamte Textur angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="1b038-124">Once the 128-bit blocks are used, the alpha channel must be specified in either explicit (format BC2) or interpolated mode (format BC3) for the entire texture.</span></span> <span data-ttu-id="1b038-125">Was die Farbe anbetrifft, können beim aktiven interpolierten Modus (BC3-Modus) entweder acht interpolierte Alphamodi oder sechs interpolierte Alphamodi auf einer nach Blöcken gestaffelten Basis verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1b038-125">As with color, when interpolated mode (format BC3) is selected, then either eight interpolated alphas or six interpolated alphas mode can be used on a block-by-block basis.</span></span> <span data-ttu-id="1b038-126">Bei einem Größenvergleich von alpha\_0 und alpha\_1 wird ein einzig nach Blöcken gestaffelter Größenvergleich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1b038-126">Again the magnitude comparison of alpha\_0 and alpha\_1 is done uniquely on a block-by-block basis.</span></span>

<span data-ttu-id="1b038-127">Direct3D bietet Services zum Komprimieren von Oberflächen, die für das Anwenden von Texturen bei 3D-Modellen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1b038-127">Direct3D provides services to compress surfaces that are used for texturing 3D models.</span></span> <span data-ttu-id="1b038-128">Dieser Abschnitt enthält Informationen zum Erstellen und Bearbeiten der Daten in einer komprimierten Texturoberfläche.</span><span class="sxs-lookup"><span data-stu-id="1b038-128">This section provides information about creating and manipulating the data in a compressed texture surface.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="1b038-129"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="1b038-129"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1b038-130">Thema</span><span class="sxs-lookup"><span data-stu-id="1b038-130">Topic</span></span></th>
<th align="left"><span data-ttu-id="1b038-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1b038-131">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="opaque-and-1-bit-alpha-textures.md"><span data-ttu-id="1b038-132">Undurchsichtige und 1-Bit-Alpha-Texturen</span><span class="sxs-lookup"><span data-stu-id="1b038-132">Opaque and 1-bit alpha textures</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1b038-133">Das BC1-Texturformat ist für Texturen, die undurchsichtig sind oder eine transparente Farbe haben.</span><span class="sxs-lookup"><span data-stu-id="1b038-133">Texture format BC1 is for textures that are opaque or have a single transparent color.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="textures-with-alpha-channels.md"><span data-ttu-id="1b038-134">Texturen mit Alphakanälen</span><span class="sxs-lookup"><span data-stu-id="1b038-134">Textures with alpha channels</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1b038-135">Es gibt zwei Möglichkeiten, Texturabbildungen mit komplexer Transparenz zu codieren.</span><span class="sxs-lookup"><span data-stu-id="1b038-135">There are two ways to encode texture maps that exhibit more complex transparency.</span></span> <span data-ttu-id="1b038-136">In jedem Fall geht ein Block, der die Transparenz beschreibt, dem bereits beschriebenen 64-Bit-Block voraus.</span><span class="sxs-lookup"><span data-stu-id="1b038-136">In each case, a block that describes the transparency precedes the 64-bit block already described.</span></span> <span data-ttu-id="1b038-137">Die Transparenz wird entweder als 4x4-Bitmap mit 4Bits pro Pixel (explizite Codierung) oder mit weniger Bits und linearer Interpolation dargestellt, die mit der verwendeten Codierung von Farben vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="1b038-137">The transparency is either represented as a 4x4 bitmap with 4 bits per pixel (explicit encoding), or with fewer bits and linear interpolation that is analogous to what is used for color encoding.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="block-compression.md"><span data-ttu-id="1b038-138">Blockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="1b038-138">Block compression</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1b038-139">Blockkomprimierung ist ein verlustbehaftetes Texturkomprimierungsverfahren zum Reduzieren der Texturgröße und des Speicherbedarfs und zur Steigerung der Leistung.</span><span class="sxs-lookup"><span data-stu-id="1b038-139">Block compression is a lossy texture-compression technique for reducing texture size and memory footprint, giving a performance increase.</span></span> <span data-ttu-id="1b038-140">Eine blockkomprimierte Textur kann kleiner als eine Textur mit 32Bit pro Farbe sein.</span><span class="sxs-lookup"><span data-stu-id="1b038-140">A block-compressed texture can be smaller than a texture with 32-bits per color.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="compressed-texture-formats.md"><span data-ttu-id="1b038-141">Komprimierte Texturformate</span><span class="sxs-lookup"><span data-stu-id="1b038-141">Compressed texture formats</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="1b038-142">Dieser Abschnitt enthält Informationen über die interne Organisation komprimierter Texturformate.</span><span class="sxs-lookup"><span data-stu-id="1b038-142">This section contains information about the internal organization of compressed texture formats.</span></span> <span data-ttu-id="1b038-143">Diese Informationen sind nicht zur Verwendung von komprimierten Texturen notwendig, da Sie die Direct3D-Funktionen für eine Konvertierung in und von komprimierten Formate verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1b038-143">You do not need these details to use compressed textures, because you can use Direct3D functions for conversion to and from compressed formats.</span></span> <span data-ttu-id="1b038-144">Sie sind jedoch hilfreich, wenn Sie direkt auf komprimierten Oberflächendaten arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="1b038-144">However, this information is useful if you want to operate on compressed surface data directly.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1b038-145"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b038-145"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1b038-146">Texturen</span><span class="sxs-lookup"><span data-stu-id="1b038-146">Textures</span></span>](textures.md)

 

 




