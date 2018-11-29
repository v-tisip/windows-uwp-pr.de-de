---
title: Blockkomprimierung
description: Blockkomprimierung ist ein verlustbehaftetes Texturkomprimierungsverfahren zum Reduzieren der Texturgröße und des Speicherbedarfs und zur Steigerung der Leistung. Eine blockkomprimierte Textur kann kleiner als eine Textur mit 32Bit pro Farbe sein.
ms.assetid: 2FAD6BE8-C6E4-4112-AF97-419CD27F7C73
keywords:
- Blockkomprimierung
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b7726067055b92ae51c01d4d056a2a11624204db
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7992497"
---
# <a name="block-compression"></a><span data-ttu-id="e38a0-105">Blockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="e38a0-105">Block compression</span></span>

<span data-ttu-id="e38a0-106">Blockkomprimierung ist ein verlustbehaftetes Texturkomprimierungsverfahren zum Reduzieren der Texturgröße und des Speicherbedarfs und zur Steigerung der Leistung.</span><span class="sxs-lookup"><span data-stu-id="e38a0-106">Block compression is a lossy texture-compression technique for reducing texture size and memory footprint, giving a performance increase.</span></span> <span data-ttu-id="e38a0-107">Eine blockkomprimierte Textur kann kleiner als eine Textur mit 32Bit pro Farbe sein.</span><span class="sxs-lookup"><span data-stu-id="e38a0-107">A block-compressed texture can be smaller than a texture with 32-bits per color.</span></span>

<span data-ttu-id="e38a0-108">Blockkomprimierung ist eine Texturkomprimierungstechnik zum Reduzieren der Texturgröße.</span><span class="sxs-lookup"><span data-stu-id="e38a0-108">Block compression is a texture compression technique for reducing texture size.</span></span> <span data-ttu-id="e38a0-109">Im Vergleich zu einer Textur mit 32Bit pro Farbe kann eine blockkomprimierte Textur bis zu 75Prozent kleiner sein.</span><span class="sxs-lookup"><span data-stu-id="e38a0-109">When compared to a texture with 32-bits per color, a block-compressed texture can be up to 75 percent smaller.</span></span> <span data-ttu-id="e38a0-110">Anwendungen sehen generell eine Leistungssteigerung beim Verwenden der Blockkomprimierung durch einen verringerten Speicherbedarf.</span><span class="sxs-lookup"><span data-stu-id="e38a0-110">Applications usually see a performance increase when using block compression because of the smaller memory footprint.</span></span>

<span data-ttu-id="e38a0-111">Obwohl sie verlustbehaftet ist, funktioniert die Blockkomprimierung und wird für alle Texturen empfohlen, die von der Pipeline transformiert und gefiltert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-111">While lossy, block compression works well and is recommended for all textures that get transformed and filtered by the pipeline.</span></span> <span data-ttu-id="e38a0-112">Texturen, die dem Bildschirm direkt zugeordnet werden (UI-Elemente wie Symbole und Text) eignen sich nicht für die Komprimierung, da Artefakte deutlich wahrnehmbar sind.</span><span class="sxs-lookup"><span data-stu-id="e38a0-112">Textures that are directly mapped to the screen (UI elements like icons and text) are not good choices for compression because artifacts are more noticeable.</span></span>

<span data-ttu-id="e38a0-113">Eine blockkomprimierte Textur muss als eine Potenz von4 in allen Dimensionen erstellt werden und darf nicht als Ausgabe der Pipeline verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-113">A block-compressed texture must be created as a multiple of size 4 in all dimensions and cannot be used as an output of the pipeline.</span></span>

## <a name="span-idbasicsspanspan-idbasicsspanspan-idbasicsspanhow-block-compression-works"></a><span data-ttu-id="e38a0-114"><span id="Basics"></span><span id="basics"></span><span id="BASICS"></span>So funktioniert die Blockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="e38a0-114"><span id="Basics"></span><span id="basics"></span><span id="BASICS"></span>How block compression works</span></span>

<span data-ttu-id="e38a0-115">Die Blockkomprimierung ist eine Methode zum Verringern des zum Speichern von Farbdaten benötigten Arbeitsspeicherbedarfs.</span><span class="sxs-lookup"><span data-stu-id="e38a0-115">Block compression is a technique for reducing the amount of memory required to store color data.</span></span> <span data-ttu-id="e38a0-116">Durch das Speichern von Farben in deren ursprünglichen Größe und von Farben mit einem Codierungsschema, können Sie den zum Speichern des Bildes benötigten Arbeitsspeicherbedarf erheblich reduzieren.</span><span class="sxs-lookup"><span data-stu-id="e38a0-116">By storing some colors in their original size, and other colors using an encoding scheme, you can dramatically reduce the amount of memory required to store the image.</span></span> <span data-ttu-id="e38a0-117">Da die Hardware automatisch komprimierte Daten entschlüsselt, besteht keine Leistungseinbuße für die Verwendung komprimierter Texturen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-117">Since the hardware automatically decodes compressed data, there is no performance penalty for using compressed textures.</span></span>

<span data-ttu-id="e38a0-118">Betrachten Sie die folgenden zwei Beispiele, um zu sehen, wie die Komprimierung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-118">To see how compression works, look at the following two examples.</span></span> <span data-ttu-id="e38a0-119">Das erste Beispiel zeigt den erforderlichen Speicherbedarf beim Speichern von nicht komprimierten Daten. Das zweite Beispiel zeigt den erforderlichen Speicherbedarf beim Speichern von komprimierten Daten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-119">The first example describes the amount of memory used when storing uncompressed data; the second example describes the amount of memory used when storing compressed data.</span></span>

- [<span data-ttu-id="e38a0-120">Speichern von nicht komprimierten Daten</span><span class="sxs-lookup"><span data-stu-id="e38a0-120">Storing uncompressed data</span></span>](#storing-uncompressed-data)
- [<span data-ttu-id="e38a0-121">Speichern von komprimierten Daten</span><span class="sxs-lookup"><span data-stu-id="e38a0-121">Storing compressed data</span></span>](#storing-compressed-data)

### <a name="span-idstoringuncompresseddataspanspan-idstoringuncompresseddataspanspan-idstoringuncompresseddataspanspan-idstoring-uncompressed-dataspanstoring-uncompressed-data"></a><span data-ttu-id="e38a0-122"><span id="Storing_Uncompressed_Data"></span><span id="storing_uncompressed_data"></span><span id="STORING_UNCOMPRESSED_DATA"></span><span id="storing-uncompressed-data"></span>Speichern von nicht komprimierten Daten</span><span class="sxs-lookup"><span data-stu-id="e38a0-122"><span id="Storing_Uncompressed_Data"></span><span id="storing_uncompressed_data"></span><span id="STORING_UNCOMPRESSED_DATA"></span><span id="storing-uncompressed-data"></span>Storing uncompressed data</span></span>

<span data-ttu-id="e38a0-123">Die folgende Abbildung zeigt eine nicht komprimierte 4×4-Textur.</span><span class="sxs-lookup"><span data-stu-id="e38a0-123">The following illustration represents an uncompressed 4×4 texture.</span></span> <span data-ttu-id="e38a0-124">Angenommen, jede Farbe enthält eine einzelne Farbkomponente (z.B. rot) und wird in einem Byte Arbeitsspeicher gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-124">Assume that each color contains a single color component (red for instance) and is stored in one byte of memory.</span></span>

![eine nicht komprimierte 4x4-Textur](images/d3d10-block-compress-1.png)

<span data-ttu-id="e38a0-126">Die nicht komprimierten Daten werden im Arbeitsspeicher nacheinander verteilt und erfordern 16Byte, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-126">The uncompressed data is laid out in memory sequentially and requires 16 bytes, as shown in the following illustration.</span></span>

![nicht komprimierte Daten im sequenziellen Arbeitsspeicher](images/d3d10-block-compress-2.png)

### <a name="span-idstoringcompresseddataspanspan-idstoringcompresseddataspanspan-idstoringcompresseddataspanspan-idstoring-compressed-dataspanstoring-compressed-data"></a><span data-ttu-id="e38a0-128"><span id="Storing_Compressed_Data"></span><span id="storing_compressed_data"></span><span id="STORING_COMPRESSED_DATA"></span><span id="storing-compressed-data"></span>Speichern von komprimierten Daten</span><span class="sxs-lookup"><span data-stu-id="e38a0-128"><span id="Storing_Compressed_Data"></span><span id="storing_compressed_data"></span><span id="STORING_COMPRESSED_DATA"></span><span id="storing-compressed-data"></span>Storing compressed data</span></span>

<span data-ttu-id="e38a0-129">Da Sie jetzt gesehen haben, wie viel Arbeitsspeicher ein nicht komprimiertes Bild verwendet, betrachten wir einmal, wie viel Arbeitsspeicher ein komprimiertes Bild erfordert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-129">Now that you've seen how much memory an uncompressed image uses, take a look at how much memory a compressed image saves.</span></span> <span data-ttu-id="e38a0-130">Das [BC1](#bc1)-Komprimierungsformat speichert 2Farben (jeweils 1Byte) und 16 3-Bit-Indizes (48Bit oder 6Bytes), die zum Interpolieren der ursprünglichen Farben in der Textur verwendet werden, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-130">The [BC1](#bc1) compression format stores 2 colors (1 byte each) and 16 3-bit indices (48 bits, or 6 bytes) that are used to interpolate the original colors in the texture, as shown in the following illustration.</span></span>

![das BC1-Komprimierungsformat](images/d3d10-block-compress-3.png)

<span data-ttu-id="e38a0-132">Der insgesamt benötigte Speicherplatz für die komprimierten Daten ist 8Byte, also eine Arbeitsspeichereinsparungen von 50Prozent im Gegensatz zum nicht komprimierten Beispiel.</span><span class="sxs-lookup"><span data-stu-id="e38a0-132">The total space required to store the compressed data is 8 bytes which is a 50-percent memory savings over the uncompressed example.</span></span> <span data-ttu-id="e38a0-133">Die Einsparungen sind dann noch größer, wenn mehr als eine Farbkomponente verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e38a0-133">The savings are even larger when more than one color component is used.</span></span>

<span data-ttu-id="e38a0-134">Die durch Blockkomprimierung erhaltenen wesentlichen Arbeitsspeichereinsparungen können zu einer Leistungssteigerung führen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-134">The substantial memory savings provided by block compression can lead to an increase in performance.</span></span> <span data-ttu-id="e38a0-135">Diese Leistung geht zu Lasten der Bildqualität (aufgrund der Farbinterpolation); die geringere Qualität ist jedoch häufig nicht erkennbar.</span><span class="sxs-lookup"><span data-stu-id="e38a0-135">This performance comes at the cost of image quality (due to color interpolation); however, the lower quality is often not noticeable.</span></span>

<span data-ttu-id="e38a0-136">Im nächste Abschnitt wird gezeigt, wie Direct3D das Verwenden der Blockkomprimierung in einer Anwendung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="e38a0-136">The next section shows how Direct3D enables using block compression in an application.</span></span>

## <a name="span-idusingblockcompressionspanspan-idusingblockcompressionspanspan-idusingblockcompressionspanusing-block-compression"></a><span data-ttu-id="e38a0-137"><span id="Using_Block_Compression"></span><span id="using_block_compression"></span><span id="USING_BLOCK_COMPRESSION"></span>Verwenden der Blockkomprimierung</span><span class="sxs-lookup"><span data-stu-id="e38a0-137"><span id="Using_Block_Compression"></span><span id="using_block_compression"></span><span id="USING_BLOCK_COMPRESSION"></span>Using block compression</span></span>

<span data-ttu-id="e38a0-138">Eine blockkomprimierte Textur kann genau wie eine nicht komprimierte Textur erstellt werden, außer dass Sie dabei ein blockkomprimiertes Format angeben.</span><span class="sxs-lookup"><span data-stu-id="e38a0-138">Create a block-compressed texture just like an uncompressed texture except that you specify a block-compressed format.</span></span>

<span data-ttu-id="e38a0-139">Erstellen Sie dann eine Ansicht, um die Textur an die Pipeline zu binden. Da eine blockkomprimierte Textur nur als Eingabe für eine Shaderphase verwendet werden kann, müssen Sie eine Shaderressourcenansicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-139">Next, create a view to bind the texture to the pipeline Since a block-compressed texture can be used only as an input to a shader-stage, you want to create a shader-resource view.</span></span>

<span data-ttu-id="e38a0-140">Verwenden Sie eine blockkomprimierte Textur genau wie eine nicht komprimierte Textur.</span><span class="sxs-lookup"><span data-stu-id="e38a0-140">Use a block compressed texture the same way you would use an uncompressed texture.</span></span> <span data-ttu-id="e38a0-141">Wenn Ihre Anwendung einen Speicherzeiger für blockkomprimierte Daten erhält, müssen Sie den Speicherabstand in einer Mipmap berücksichtigen, durch die sich die deklarierte Größe von der tatsächlichen Größe unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="e38a0-141">If your application will get a memory pointer to block-compressed data, you need to account for the memory padding in a mipmap that causes the declared size to differ from the actual size.</span></span>

- [<span data-ttu-id="e38a0-142">Virtuelle Größe im Vergleich zur physischen Größe</span><span class="sxs-lookup"><span data-stu-id="e38a0-142">Virtual size versus physical size</span></span>](#virtual-size-versus-physical-size)

### <a name="span-idvirtualsizespanspan-idvirtualsizespanspan-idvirtualsizespanspan-idvirtual-size-versus-physical-sizespanvirtual-size-versus-physical-size"></a><span data-ttu-id="e38a0-143"><span id="Virtual_Size"></span><span id="virtual_size"></span><span id="VIRTUAL_SIZE"></span><span id="virtual-size-versus-physical-size"></span>Virtuelle Größe im Vergleich zur physischen Größe</span><span class="sxs-lookup"><span data-stu-id="e38a0-143"><span id="Virtual_Size"></span><span id="virtual_size"></span><span id="VIRTUAL_SIZE"></span><span id="virtual-size-versus-physical-size"></span>Virtual size versus physical size</span></span>

<span data-ttu-id="e38a0-144">Wenn Sie einen App-Code besitzen, der einen Speicherzeiger zur Anzeige des Speichers einer blockkomprimierten Textur besitzt, gibt es einen wichtigen Aspekt, der eventuell eine Änderung im Anwendungscode erfordert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-144">If you have application code that uses a memory pointer to walk the memory of a block compressed texture, there is one important consideration that may require a modification in your application code.</span></span> <span data-ttu-id="e38a0-145">Eine blockkomprimierte Textur muss als eine Potenz von4 in allen Dimensionen erstellt werden, da die Algorithmen für die Blockkomprimierung auf 4x4-Texel-Blöcken funktionieren.</span><span class="sxs-lookup"><span data-stu-id="e38a0-145">A block-compressed texture must be a multiple of 4 in all dimensions because the block-compression algorithms operate on 4x4 texel blocks.</span></span> <span data-ttu-id="e38a0-146">Das ist ein Problem für eine Mipmap, da deren anfängliche Dimensionen zwar durch 4 teilbar sind, doch deren unterteilten Ebenen nicht.</span><span class="sxs-lookup"><span data-stu-id="e38a0-146">This will be a problem for a mipmap whose initial dimensions are divisible by 4, but subdivided levels are not.</span></span> <span data-ttu-id="e38a0-147">Das folgende Diagramm zeigt die Differenz zwischen der virtuellen (deklarierten) und der physischen (aktuellen) Größe aller Mipmap-Ebenen an.</span><span class="sxs-lookup"><span data-stu-id="e38a0-147">The following diagram shows the difference in area between the virtual (declared) size and the physical (actual) size of each mipmap level.</span></span>

![Nicht komprimiert und komprimierte Mipmap-Ebenen](images/d3d10-block-compress-pad.png)

<span data-ttu-id="e38a0-149">Auf der linken Seite des Diagramms sehen Sie die Mipmap-Ebenengrößen, die für eine nicht komprimierte 60x40 Textur generiert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-149">The left side of the diagram shows the mipmap level sizes that are generated for an uncompressed 60×40 texture.</span></span> <span data-ttu-id="e38a0-150">Die Größe der obersten Ebene stammt vom API-Aufruf, der die Textur generiert. Jeder nachfolgende Ebene ist halb so groß wie die vorherige Ebene.</span><span class="sxs-lookup"><span data-stu-id="e38a0-150">The top level size is taken from the API call that generates the texture; each subsequent level is half the size of the previous level.</span></span> <span data-ttu-id="e38a0-151">Für eine nicht komprimierte Textur besteht kein Unterschied zwischen der virtuellen (deklarierten) und der physischen (tatsächlichen) Größe.</span><span class="sxs-lookup"><span data-stu-id="e38a0-151">For an uncompressed texture, there is no difference between the virtual (declared) size and the physical (actual) size.</span></span>

<span data-ttu-id="e38a0-152">Auf der rechten Seite des Diagramms sehen Sie die Mipmap-Ebenengrößen, die für die gleiche 60x40 Textur durch Komprimierung generiert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-152">The right side of the diagram shows the mipmap level sizes that are generated for the same 60×40 texture with compression.</span></span> <span data-ttu-id="e38a0-153">Beachten Sie, dass die zweiten und dritten Ebenen einen Arbeitsspeicherabstand aufweisen, um die Größen auf jeder Ebene als ein Vierfaches festzulegen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-153">Notice that both the second and third levels have memory padding to make the sizes factors of 4 on every level.</span></span> <span data-ttu-id="e38a0-154">Dies ist erforderlich, damit die Algorithmen für 4×4-Texel-Blöcke verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="e38a0-154">This is necessary so that the algorithms can operate on 4×4 texel blocks.</span></span> <span data-ttu-id="e38a0-155">Dies wird besonders dann deutlich, wenn Sie Mipmap-Ebenen in Betracht ziehen, die kleiner als 4×4 sind. Die Größe dieser sehr kleinen Mipmap-Ebenen werden bei der Zuordnung des Arbeitsspeichers für die Textur auf das nächste Vierfache aufgerundet.</span><span class="sxs-lookup"><span data-stu-id="e38a0-155">This is expecially evident if you consider mipmap levels that are smaller than 4×4; the size of these very small mipmap levels will be rounded up to the nearest factor of 4 when texture memory is allocated.</span></span>

<span data-ttu-id="e38a0-156">Sampling-Hardware verwendet die virtuelle Größe. Wenn die Textur ermittelt wird, wird der Speicherabstand ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-156">Sampling hardware uses the virtual size; when the texture is sampled, the memory padding is ignored.</span></span> <span data-ttu-id="e38a0-157">Für Mipmap-Ebenen, die kleiner als 4×4 sind, werden nur die ersten vier Texel für eine 2x2-Karte und nur der erste Texel für einen 1x1-Block verwendet.</span><span class="sxs-lookup"><span data-stu-id="e38a0-157">For mipmap levels that are smaller than 4×4, only the first four texels will be used for a 2×2 map, and only the first texel will be used by a 1×1 block.</span></span> <span data-ttu-id="e38a0-158">Es gibt jedoch keine API-Struktur, die die physische Größe (einschließlich des Arbeitsspeicherabstands) anzeigt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-158">However, there is no API structure that exposes the physical size (including the memory padding).</span></span>

<span data-ttu-id="e38a0-159">Zusammenfassung: Seien Sie bei der Verwendung von ausgerichteten Speicherblöcken vorsichtig, wenn Sie Regionen kopieren, die blockkomprimierte Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-159">In summary, be careful to use aligned memory blocks when copying regions that contain block-compressed data.</span></span> <span data-ttu-id="e38a0-160">Um dies in einer Anwendung mit Speicherzeiger zu verwenden, stellen Sie sicher, dass der Zeiger den Neigungswinkel der Oberfläche verwendet, um die Größe des physischen Speichers zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-160">To do this in an application that gets a memory pointer, make sure that the pointer uses the surface pitch to account for the physical memory size.</span></span>

## <a name="span-idcompressionalgorithmsspanspan-idcompressionalgorithmsspanspan-idcompressionalgorithmsspancompression-algorithms"></a><span data-ttu-id="e38a0-161"><span id="Compression_Algorithms"></span><span id="compression_algorithms"></span><span id="COMPRESSION_ALGORITHMS"></span>Komprimierungsalgorithmus</span><span class="sxs-lookup"><span data-stu-id="e38a0-161"><span id="Compression_Algorithms"></span><span id="compression_algorithms"></span><span id="COMPRESSION_ALGORITHMS"></span>Compression algorithms</span></span>

<span data-ttu-id="e38a0-162">Blockkomprimierungstechniken in Direct3D teilen nicht komprimierte Texturdaten in 4×4 Blöcke auf, komprimieren jeden Block und speichern anschließend die Daten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-162">Block compression techniques in Direct3D break up uncompressed texture data into 4×4 blocks, compress each block, and then store the data.</span></span> <span data-ttu-id="e38a0-163">Aus diesem Grund müssen Texturen, die komprimiert werden, Texturdimensionen aufweisen, die eine Potenz von4 sind.</span><span class="sxs-lookup"><span data-stu-id="e38a0-163">For this reason, textures are expected to be compressed must have texture dimensions that are multiples of 4.</span></span>

![Blockkomprimierung](images/d3d10-compression-1.png)

<span data-ttu-id="e38a0-165">Die obige Abbildung zeigt eine in Texel-Blöcke aufgeteilte Textur.</span><span class="sxs-lookup"><span data-stu-id="e38a0-165">The preceding diagram shows a texture partitioned into texel blocks.</span></span> <span data-ttu-id="e38a0-166">Der erste Block zeigt das Layout der 16Texel mit der Bezeichnung „a-p”, doch jeder Block verfügt über die gleiche Organisation der Daten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-166">The first block shows the layout of the 16 texels labeled a-p, but every block has the same organization of data.</span></span>

<span data-ttu-id="e38a0-167">Direct3D implementiert mehrere Komprimierungsmethoden. Jede Methode implementiert einen unterschiedlichen Kompromiss zwischen der Anzahl an gespeicherten Komponenten und der Anzahl an Bit pro Komponente und dem erforderlichen Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="e38a0-167">Direct3D implements several compression schemes, each implements a different tradeoff between number of components stored, the number of bits per component, and the amount of memory consumed.</span></span> <span data-ttu-id="e38a0-168">Verwenden Sie die Tabelle zur Auswahl des Formats, das am besten mit der Art von Daten und der Datenauflösung funktioniert, die Ihrer Anwendung entspricht.</span><span class="sxs-lookup"><span data-stu-id="e38a0-168">Use this table to help choose the format that works best with the type of data and the data resolution that best fits your application.</span></span>

| <span data-ttu-id="e38a0-169">Datenquelle</span><span class="sxs-lookup"><span data-stu-id="e38a0-169">Source Data</span></span>                     | <span data-ttu-id="e38a0-170">Auflösung der Datenkomprimierung (in Bit)</span><span class="sxs-lookup"><span data-stu-id="e38a0-170">Data Compression Resolution (in bits)</span></span> | <span data-ttu-id="e38a0-171">Wählen Sie dieses Komprimierungsformat</span><span class="sxs-lookup"><span data-stu-id="e38a0-171">Choose this compression format</span></span> |
|---------------------------------|---------------------------------------|--------------------------------|
| <span data-ttu-id="e38a0-172">Farb- und Alphawert mit drei Komponenten</span><span class="sxs-lookup"><span data-stu-id="e38a0-172">Three-component color and alpha</span></span> | <span data-ttu-id="e38a0-173">Farbe (5:6:5), Alpha (1) oder kein Alpha</span><span class="sxs-lookup"><span data-stu-id="e38a0-173">Color (5:6:5), Alpha (1) or no alpha</span></span>  | [<span data-ttu-id="e38a0-174">BC1</span><span class="sxs-lookup"><span data-stu-id="e38a0-174">BC1</span></span>](#bc1)                    |
| <span data-ttu-id="e38a0-175">Farb- und Alphawert mit drei Komponenten</span><span class="sxs-lookup"><span data-stu-id="e38a0-175">Three-component color and alpha</span></span> | <span data-ttu-id="e38a0-176">Farbe (5:6:5), Alpha (4)</span><span class="sxs-lookup"><span data-stu-id="e38a0-176">Color (5:6:5), Alpha (4)</span></span>              | [<span data-ttu-id="e38a0-177">BC2</span><span class="sxs-lookup"><span data-stu-id="e38a0-177">BC2</span></span>](#bc2)                    |
| <span data-ttu-id="e38a0-178">Farb- und Alphawert mit drei Komponenten</span><span class="sxs-lookup"><span data-stu-id="e38a0-178">Three-component color and alpha</span></span> | <span data-ttu-id="e38a0-179">Farbe (5:6:5), Alpha (8)</span><span class="sxs-lookup"><span data-stu-id="e38a0-179">Color (5:6:5), Alpha (8)</span></span>              | [<span data-ttu-id="e38a0-180">BC3</span><span class="sxs-lookup"><span data-stu-id="e38a0-180">BC3</span></span>](#bc3)                    |
| <span data-ttu-id="e38a0-181">Farbe mit einer Komponente</span><span class="sxs-lookup"><span data-stu-id="e38a0-181">One-component color</span></span>             | <span data-ttu-id="e38a0-182">Eine Komponente (8)</span><span class="sxs-lookup"><span data-stu-id="e38a0-182">One component (8)</span></span>                     | [<span data-ttu-id="e38a0-183">BC4</span><span class="sxs-lookup"><span data-stu-id="e38a0-183">BC4</span></span>](#bc4)                    |
| <span data-ttu-id="e38a0-184">Farbe mit zwei Komponenten</span><span class="sxs-lookup"><span data-stu-id="e38a0-184">Two-component color</span></span>             | <span data-ttu-id="e38a0-185">Zwei Komponenten (8:8)</span><span class="sxs-lookup"><span data-stu-id="e38a0-185">Two components (8:8)</span></span>                  | [<span data-ttu-id="e38a0-186">BC5</span><span class="sxs-lookup"><span data-stu-id="e38a0-186">BC5</span></span>](#bc5)                    |

- [<span data-ttu-id="e38a0-187">BC1</span><span class="sxs-lookup"><span data-stu-id="e38a0-187">BC1</span></span>](#bc1)
- [<span data-ttu-id="e38a0-188">BC2</span><span class="sxs-lookup"><span data-stu-id="e38a0-188">BC2</span></span>](#bc2)
- [<span data-ttu-id="e38a0-189">BC3</span><span class="sxs-lookup"><span data-stu-id="e38a0-189">BC3</span></span>](#bc3)
- [<span data-ttu-id="e38a0-190">BC4</span><span class="sxs-lookup"><span data-stu-id="e38a0-190">BC4</span></span>](#bc4)
- [<span data-ttu-id="e38a0-191">BC5</span><span class="sxs-lookup"><span data-stu-id="e38a0-191">BC5</span></span>](#bc5)

### <a name="span-idbc1spanspan-idbc1spanbc1"></a><span data-ttu-id="e38a0-192"><span id="BC1"></span><span id="bc1"></span>BC1</span><span class="sxs-lookup"><span data-stu-id="e38a0-192"><span id="BC1"></span><span id="bc1"></span>BC1</span></span>

<span data-ttu-id="e38a0-193">Verwenden Sie das erste Blockkomprimierungsformat (BC1) (entweder DXGI\_FORMAT\_BC1\_TYPELESS, DXGI\_FORMAT\_BC1\_UNORM oder DXGI\_BC1\_UNORM\_SRGB) zum Speichern von Farbdaten mit drei Komponenten, die 5:6:5 Farbe verwenden (5Bit Rot, 6Bit Grün, 5 Bit Blau).</span><span class="sxs-lookup"><span data-stu-id="e38a0-193">Use the first block compression format (BC1) (either DXGI\_FORMAT\_BC1\_TYPELESS, DXGI\_FORMAT\_BC1\_UNORM, or DXGI\_BC1\_UNORM\_SRGB) to store three-component color data using a 5:6:5 color (5 bits red, 6 bits green, 5 bits blue).</span></span> <span data-ttu-id="e38a0-194">Dies gilt auch, wenn die Daten ebenfalls 1Bit Alpha enthalten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-194">This is true even if the data also contains 1-bit alpha.</span></span> <span data-ttu-id="e38a0-195">Bei einer 4×4-Textur mit dem größtmöglichen Datenformat reduziert das Format BC1 den erforderlichen Speicherplatz von 48Byte (16Farben × 3-Komponenten/Farben × 1Byte/Komponente) auf 8Byte Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="e38a0-195">Assuming a 4×4 texture using the largest data format possible, the BC1 format reduces the memory required from 48 bytes (16 colors × 3 components/color × 1 byte/component) to 8 bytes of memory.</span></span>

<span data-ttu-id="e38a0-196">Der Algorithmus funktioniert auf 4×4-Texelblöcken.</span><span class="sxs-lookup"><span data-stu-id="e38a0-196">The algorithm works on 4×4 blocks of texels.</span></span> <span data-ttu-id="e38a0-197">Anstatt 16 Farben zu speichern, speichert der Algorithmus 2 Referenzfarben (color\_0 und color\_1) und 16 2-Bit-Farbindizes (Blöcke a‑p), wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-197">Instead of storing 16 colors, the algorithm saves 2 reference colors (color\_0 and color\_1) and 16 2-bit color indices (blocks a–p), as shown in the following diagram.</span></span>

![das Layout für eine BC1-Komprimierung](images/d3d10-compression-bc1.png)

<span data-ttu-id="e38a0-199">Die Farbindizes (a-p) werden verwendet, um die ursprünglichen Farben aus einer Farbtabelle anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-199">The color indices (a–p) are used to look up the original colors from a color table.</span></span> <span data-ttu-id="e38a0-200">Die Farbtabelle enthält 4 Farben.</span><span class="sxs-lookup"><span data-stu-id="e38a0-200">The color table contains 4 colors.</span></span> <span data-ttu-id="e38a0-201">Die ersten beiden Farben – color\_0 und color\_1 – sind die minimalen und maximalen Farben.</span><span class="sxs-lookup"><span data-stu-id="e38a0-201">The first two colors—color\_0 and color\_1—are the minimum and maximum colors.</span></span> <span data-ttu-id="e38a0-202">Die anderen zwei Farben, color\_2 und color\_3, sind Zwischenfarben, die durch lineare Interpolation berechnet wurden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-202">The other two colors, color\_2 and color\_3, are intermediate colors calculated with linear interpolation.</span></span>

```cpp
color_2 = 2/3*color_0 + 1/3*color_1
color_3 = 1/3*color_0 + 2/3*color_1
```

<span data-ttu-id="e38a0-203">Den vier Farben werden 2-Bit-Indexwerte zugewiesen, die in den Blöcke a-p gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-203">The four colors are assigned 2-bit index values that will be saved in blocks a–p.</span></span>

```cpp
color_0 = 00
color_1 = 01
color_2 = 10
color_3 = 11
```

<span data-ttu-id="e38a0-204">Anschließend werden die Farben in den Blöcken a-p mit den vier Farben der Tabelle verglichen und der Index für die ähnlichste Farbe wird in den 2-Bit-Blöcken gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-204">Finally, each of the colors in blocks a–p are compared with the four colors in the color table, and the index for the closest color is stored in the 2-bit blocks.</span></span>

<span data-ttu-id="e38a0-205">Dieser Algorithmus eignet sich für ebenfalls für Daten, die 1Bit Alpha enthalten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-205">This algorithm lends itself to data that contains 1-bit alpha also.</span></span> <span data-ttu-id="e38a0-206">Der einzige Unterschied ist, dass color\_3 auf 0 (eine transparente Farbe) festgelegt ist und color\_2 eine lineare Mischung aus color\_0 und color\_1 ist.</span><span class="sxs-lookup"><span data-stu-id="e38a0-206">The only difference is that color\_3 is set to 0 (which represents a transparent color) and color\_2 is a linear blend of color\_0 and color\_1.</span></span>

```cpp
color_2 = 1/2*color_0 + 1/2*color_1;
color_3 = 0;
```

### <a name="span-idbc2spanspan-idbc2spanbc2"></a><span data-ttu-id="e38a0-207"><span id="BC2"></span><span id="bc2"></span>BC2</span><span class="sxs-lookup"><span data-stu-id="e38a0-207"><span id="BC2"></span><span id="bc2"></span>BC2</span></span>

<span data-ttu-id="e38a0-208">Verwenden Sie das BC2-Format (DXGI\_FORMAT\_BC2\_TYPELESS, DXGI\_FORMAT\_BC2\_UNORM oder DXGI\_BC2\_UNORM\_SRGB) zum Speichern von Daten, die Farb- und Alphawerte mit niedriger Kohärenz enthalten (verwenden Sie [BC3](#bc3) für sehr kohärente Alpha-Daten).</span><span class="sxs-lookup"><span data-stu-id="e38a0-208">Use the BC2 format (either DXGI\_FORMAT\_BC2\_TYPELESS, DXGI\_FORMAT\_BC2\_UNORM, or DXGI\_BC2\_UNORM\_SRGB) to store data that contains color and alpha data with low coherency (use [BC3](#bc3) for highly-coherent alpha data).</span></span> <span data-ttu-id="e38a0-209">Das BC2-Format speichert RGB-Daten als eine „5:6:5” Farbe (5 Bit Rot, 6 Bit Grün, 5 Bit Blau) und Alpha als einen separaten 4-Bit-Wert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-209">The BC2 format stores RGB data as a 5:6:5 color (5 bits red, 6 bits green, 5 bits blue) and alpha as a separate 4-bit value.</span></span> <span data-ttu-id="e38a0-210">Bei einer 4×4-Textur mit dem größtmöglichen Datenformat reduziert diese Komprimierungstechnik den erforderlichen Speicherplatz von 64Byte (16Farben × 4-Komponenten/Farben × 1Byte/Komponente) auf 16Byte Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="e38a0-210">Assuming a 4×4 texture using the largest data format possible, this compression technique reduces the memory required from 64 bytes (16 colors × 4 components/color × 1 byte/component) to 16 bytes of memory.</span></span>

<span data-ttu-id="e38a0-211">Das BC2-Format speichert Farben mit der gleichen Anzahl von Bit und Daten-Layout wie das [BC1](#bc1)-Format. BC2 erfordert allerdings 64-Bit zusätzlichen Speicher zum Speichern der Alpha-Daten, wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-211">The BC2 format stores colors with the same number of bits and data layout as the [BC1](#bc1) format; however, BC2 requires an additional 64-bits of memory to store the alpha data, as shown in the following diagram.</span></span>

![das Layout für eine BC2-Komprimierung](images/d3d10-compression-bc2.png)

### <a name="span-idbc3spanspan-idbc3spanbc3"></a><span data-ttu-id="e38a0-213"><span id="BC3"></span><span id="bc3"></span>BC3</span><span class="sxs-lookup"><span data-stu-id="e38a0-213"><span id="BC3"></span><span id="bc3"></span>BC3</span></span>

<span data-ttu-id="e38a0-214">Verwenden Sie das BC3-Format (DXGI\_FORMAT\_BC3\_TYPELESS, DXGI\_FORMAT\_BC3\_UNORM oder DXGI\_BC3\_UNORM\_SRGB) zum Speichern von sehr kohärenten Farben (verwenden Sie [BC2](#bc2) für weniger kohärente Alpha-Daten).</span><span class="sxs-lookup"><span data-stu-id="e38a0-214">Use the BC3 format (either DXGI\_FORMAT\_BC3\_TYPELESS, DXGI\_FORMAT\_BC3\_UNORM, or DXGI\_BC3\_UNORM\_SRGB) to store highly coherent color data (use [BC2](#bc2) with less coherent alpha data).</span></span> <span data-ttu-id="e38a0-215">Die BC3-Format speichert Farbdaten mit „5:6:5” Farbe ( Bit Rot, 6 Bit Grün, 5 Bit Blau) und Alpha-Daten mit einem Byte.</span><span class="sxs-lookup"><span data-stu-id="e38a0-215">The BC3 format stores color data using 5:6:5 color (5 bits red, 6 bits green, 5 bits blue) and alpha data using one byte.</span></span> <span data-ttu-id="e38a0-216">Bei einer 4×4-Textur mit dem größtmöglichen Datenformat reduziert diese Komprimierungstechnik den erforderlichen Speicherplatz von 64Byte (16Farben × 4-Komponenten/Farben × 1Byte/Komponente) auf 16Byte Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="e38a0-216">Assuming a 4×4 texture using the largest data format possible, this compression technique reduces the memory required from 64 bytes (16 colors × 4 components/color × 1 byte/component) to 16 bytes of memory.</span></span>

<span data-ttu-id="e38a0-217">Die BC3-Format speichert Farben mit der gleichen Anzahl von Bit und Daten-Layout wie das [BC1](#bc1)-Format. BC3 erfordert allerdings 64-Bit zusätzlichen Speicher zum Speichern der Alpha-Daten, wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-217">The BC3 format stores colors with the same number of bits and data layout as the [BC1](#bc1) format; however, BC3 requires an additional 64-bits of memory to store the alpha data.</span></span> <span data-ttu-id="e38a0-218">Das BC3-Format verarbeitet Alpha, indem es zwei Referenzdaten speichert und die Werte zwischen ihnen interpoliert (ähnlich wie BC1 RGB-Farbe speichert).</span><span class="sxs-lookup"><span data-stu-id="e38a0-218">The BC3 format handles alpha by storing two reference values and interpolating between them (similarly to how BC1 stores RGB color).</span></span>

<span data-ttu-id="e38a0-219">Der Algorithmus funktioniert auf 4×4-Texelblöcken.</span><span class="sxs-lookup"><span data-stu-id="e38a0-219">The algorithm works on 4×4 blocks of texels.</span></span> <span data-ttu-id="e38a0-220">Anstatt 16 Alpha-Werte zu speichern, speichert der Algorithmus 2 Alpha-Referenzen (alpha\_0 und alpha\_1) und 16 3-Bit-Farbindizes (Alpha a bis p), wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-220">Instead of storing 16 alpha values, the algorithm stores 2 reference alphas (alpha\_0 and alpha\_1) and 16 3-bit color indices (alpha a through p), as shown in the following diagram.</span></span>

![das Layout für eine BC3-Komprimierung](images/d3d10-compression-bc3.png)

<span data-ttu-id="e38a0-222">Das BC3-Format verwendet die Alpha-Indizes (a-p), um die ursprünglichen Farben in einer Suchtabelle zu finden, die 8 Werte enthält.</span><span class="sxs-lookup"><span data-stu-id="e38a0-222">The BC3 format uses the alpha indices (a–p) to look up the original colors from a lookup table that contains 8 values.</span></span> <span data-ttu-id="e38a0-223">Die ersten beiden Werte – alpha\_0 und alpha\_1 – sind die minimalen und maximalen Werte. Die anderen sechs Zwischenwerte werden mithilfe der linearen Interpolation berechnet.</span><span class="sxs-lookup"><span data-stu-id="e38a0-223">The first two values—alpha\_0 and alpha\_1—are the minimum and maximum values; the other six intermediate values are calculated using linear interpolation.</span></span>

<span data-ttu-id="e38a0-224">Der Algorithmus bestimmt die Anzahl der interpolierten Alphawerte anhand von zwei Alpha-Referenzen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-224">The algorithm determines the number of interpolated alpha values by examining the two reference alpha values.</span></span> <span data-ttu-id="e38a0-225">Wenn alpha\_0 größer als alpha\_1 ist, interpoliert BC3 6 Alphawerte; andernfalls interpoliert es 4.</span><span class="sxs-lookup"><span data-stu-id="e38a0-225">If alpha\_0 is greater than alpha\_1, then BC3 interpolates 6 alpha values; otherwise, it interpolates 4.</span></span> <span data-ttu-id="e38a0-226">Wenn BC3 nur 4 Alphawerte interpoliert, werden zwei zusätzliche Alphawerte festgelegt (0 für vollständig transparent und 255 für vollständig undurchsichtig).</span><span class="sxs-lookup"><span data-stu-id="e38a0-226">When BC3 interpolates only 4 alpha values, it sets two additional alpha values (0 for fully transparent and 255 for fully opaque).</span></span> <span data-ttu-id="e38a0-227">BC3 komprimiert die Alphawerte in 4×4-Texel-Bereiche, indem der Bit-Code gespeichert wird, der dem interpolierten Alpha-Wert entspricht, der dem ursprünglichen Alpha-Wert für ein bestimmtes Texel am ehesten entspricht.</span><span class="sxs-lookup"><span data-stu-id="e38a0-227">BC3 compresses the alpha values in the 4×4 texel area by storing the bit code corresponding to the interpolated alpha values which most closely matches the original alpha for a given texel.</span></span>

```cpp
if( alpha_0 > alpha_1 )
{
  // 6 interpolated alpha values.
  alpha_2 = 6/7*alpha_0 + 1/7*alpha_1; // bit code 010
  alpha_3 = 5/7*alpha_0 + 2/7*alpha_1; // bit code 011
  alpha_4 = 4/7*alpha_0 + 3/7*alpha_1; // bit code 100
  alpha_5 = 3/7*alpha_0 + 4/7*alpha_1; // bit code 101
  alpha_6 = 2/7*alpha_0 + 5/7*alpha_1; // bit code 110
  alpha_7 = 1/7*alpha_0 + 6/7*alpha_1; // bit code 111
}
else
{
  // 4 interpolated alpha values.
  alpha_2 = 4/5*alpha_0 + 1/5*alpha_1; // bit code 010
  alpha_3 = 3/5*alpha_0 + 2/5*alpha_1; // bit code 011
  alpha_4 = 2/5*alpha_0 + 3/5*alpha_1; // bit code 100
  alpha_5 = 1/5*alpha_0 + 4/5*alpha_1; // bit code 101
  alpha_6 = 0;                         // bit code 110
  alpha_7 = 255;                       // bit code 111
}
```

### <a name="span-idbc4spanspan-idbc4spanbc4"></a><span data-ttu-id="e38a0-228"><span id="BC4"></span><span id="bc4"></span>BC4</span><span class="sxs-lookup"><span data-stu-id="e38a0-228"><span id="BC4"></span><span id="bc4"></span>BC4</span></span>

<span data-ttu-id="e38a0-229">Verwenden Sie das BC4-Format, um Einzelkomponent-Farbdaten mit 8Bit pro Farbe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e38a0-229">Use the BC4 format to store one-component color data using 8 bits for each color.</span></span> <span data-ttu-id="e38a0-230">Aufgrund der höheren Genauigkeit (im Vergleich zu [BC1](#bc1)), eignet sich BC4 perfekt zum Speichern von Gleitkomma-Daten im Bereich von \[0 bis 1\] mithilfe des DXGI\_FORMAT\_BC4\_UNORM-Formats und von \[-1 bis +1\] mithilfe des DXGI\_FORMAT\_BC4\_SNORM-Formats.</span><span class="sxs-lookup"><span data-stu-id="e38a0-230">As a result of the increased accuracy (compared to [BC1](#bc1)), BC4 is ideal for storing floating-point data in the range of \[0 to 1\] using the DXGI\_FORMAT\_BC4\_UNORM format and \[-1 to +1\] using the DXGI\_FORMAT\_BC4\_SNORM format.</span></span> <span data-ttu-id="e38a0-231">Bei einer 4×4-Textur mit dem größtmöglichen Datenformat reduziert diese Komprimierungstechnik den erforderlichen Speicherplatz von 16Byte (16Farben × 1-Komponenten/Farben × 1Byte/Komponente) auf 8Byte.</span><span class="sxs-lookup"><span data-stu-id="e38a0-231">Assuming a 4×4 texture using the largest data format possible, this compression technique reduces the memory required from 16 bytes (16 colors × 1 components/color × 1 byte/component) to 8 bytes.</span></span>

<span data-ttu-id="e38a0-232">Der Algorithmus funktioniert auf 4×4-Texelblöcken.</span><span class="sxs-lookup"><span data-stu-id="e38a0-232">The algorithm works on 4×4 blocks of texels.</span></span> <span data-ttu-id="e38a0-233">Anstatt 16 Farben zu speichern, speichert der Algorithmus 2 Referenzfarben (rot\_0 und rot\_1) und 16 3-Bit-Farbindizes (Rot a bis p), wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-233">Instead of storing 16 colors, the algorithm stores 2 reference colors (red\_0 and red\_1) and 16 3-bit color indices (red a through red p), as shown in the following diagram.</span></span>

![das Layout für eine BC4-Komprimierung](images/d3d10-compression-bc4.png)

<span data-ttu-id="e38a0-235">Der Algorithmus verwendet die 3-Bit-Indizes um Farben aus einer Farbtabelle mit 8 Farben herauszufinden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-235">The algorithm uses the 3-bit indices to look up colors from a color table that contains 8 colors.</span></span> <span data-ttu-id="e38a0-236">Die ersten beiden Farben – rot\_0 und rot\_1 – sind die minimalen und maximalen Farben.</span><span class="sxs-lookup"><span data-stu-id="e38a0-236">The first two colors—red\_0 and red\_1—are the minimum and maximum colors.</span></span> <span data-ttu-id="e38a0-237">Der Algorithmus berechnet die restlichen Farben mithilfe der linearen Interpolation.</span><span class="sxs-lookup"><span data-stu-id="e38a0-237">The algorithm calculates the remaining colors using linear interpolation.</span></span>

<span data-ttu-id="e38a0-238">Der Algorithmus bestimmt die Anzahl der interpolierten Farbwerte anhand von zwei Referenzwerten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-238">The algorithm determines the number of interpolated color values by examining the two reference values.</span></span> <span data-ttu-id="e38a0-239">Wenn rot\_0 größer als red\_1 ist, interpoliert BC4 6 Farbwerte; andernfalls werden nur 4 interpoliert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-239">If red\_0 is greater than red\_1, then BC4 interpolates 6 color values; otherwise, it interpolates 4.</span></span> <span data-ttu-id="e38a0-240">Wenn BC4 nur 4 Farbwerte interpoliert, werden zwei zusätzliche Farbwerte festgelegt (0,0f ist vollständig transparent und 1,0f ist vollständig undurchsichtig).</span><span class="sxs-lookup"><span data-stu-id="e38a0-240">When BC4 interpolates only 4 color values, it sets two additional color values (0.0f for fully transparent and 1.0f for fully opaque).</span></span> <span data-ttu-id="e38a0-241">BC4 komprimiert die Alphawerte in 4×4-Texel-Bereiche, indem der Bit-Code gespeichert wird, der dem interpolierten Alpha-Wert entspricht, der mit dem ursprünglichen Alpha-Wert für ein bestimmtes Texel am ehesten übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-241">BC4 compresses the alpha values in the 4×4 texel area by storing the bit code corresponding to the interpolated alpha values that most closely matches the original alpha for a given texel.</span></span>

- [<span data-ttu-id="e38a0-242">BC4\_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-242">BC4\_UNORM</span></span>](#bc4-unorm)
- [<span data-ttu-id="e38a0-243">BC4\_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-243">BC4\_SNORM</span></span>](#bc4-snorm)

### <a name="span-idbc4unormspanspan-idbc4unormspanspan-idbc4-unormspanbc4unorm"></a><span data-ttu-id="e38a0-244"><span id="BC4_UNORM"></span><span id="bc4_unorm"></span><span id="bc4-unorm"></span>BC4\_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-244"><span id="BC4_UNORM"></span><span id="bc4_unorm"></span><span id="bc4-unorm"></span>BC4\_UNORM</span></span>

<span data-ttu-id="e38a0-245">Die Interpolation bei Daten mit einer einzelnen Komponente erfolgt wie im folgenden Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-245">The interpolation of the single-component data is done as in the following code sample.</span></span>

```cpp
unsigned word red_0, red_1;

if( red_0 > red_1 )
{
  // 6 interpolated color values
  red_2 = (6*red_0 + 1*red_1)/7.0f; // bit code 010
  red_3 = (5*red_0 + 2*red_1)/7.0f; // bit code 011
  red_4 = (4*red_0 + 3*red_1)/7.0f; // bit code 100
  red_5 = (3*red_0 + 4*red_1)/7.0f; // bit code 101
  red_6 = (2*red_0 + 5*red_1)/7.0f; // bit code 110
  red_7 = (1*red_0 + 6*red_1)/7.0f; // bit code 111
}
else
{
  // 4 interpolated color values
  red_2 = (4*red_0 + 1*red_1)/5.0f; // bit code 010
  red_3 = (3*red_0 + 2*red_1)/5.0f; // bit code 011
  red_4 = (2*red_0 + 3*red_1)/5.0f; // bit code 100
  red_5 = (1*red_0 + 4*red_1)/5.0f; // bit code 101
  red_6 = 0.0f;                     // bit code 110
  red_7 = 1.0f;                     // bit code 111
}
```

<span data-ttu-id="e38a0-246">Den Referenzfarben sind 3-Bit-Indizes zugewiesen (000 – 111, da 8 Werte vorhanden sind), die während der Komprimierung in Blöcken von „Rot a” bis „Rot p” gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-246">The reference colors are assigned 3-bit indices (000–111 since there are 8 values), which will be saved in blocks red a through red p during compression.</span></span>

### <a name="span-idbc4snormspanspan-idbc4snormspanspan-idbc4-snormspanbc4snorm"></a><span data-ttu-id="e38a0-247"><span id="BC4_SNORM"></span><span id="bc4_snorm"></span><span id="bc4-snorm"></span>BC4\_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-247"><span id="BC4_SNORM"></span><span id="bc4_snorm"></span><span id="bc4-snorm"></span>BC4\_SNORM</span></span>

<span data-ttu-id="e38a0-248">DXGI\_FORMAT\_BC4\_SNORM ist identisch, mit Ausnahme der Codierung der Daten im Bereich SNORM und wenn 4 Farbwerte interpoliert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-248">The DXGI\_FORMAT\_BC4\_SNORM is exactly the same, except that the data is encoded in SNORM range and when 4 color values are interpolated.</span></span> <span data-ttu-id="e38a0-249">Die Interpolation bei Daten mit einer einzelnen Komponente erfolgt wie im folgenden Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-249">The interpolation of the single-component data is done as in the following code sample.</span></span>

```cpp
signed word red_0, red_1;

if( red_0 > red_1 )
{
  // 6 interpolated color values
  red_2 = (6*red_0 + 1*red_1)/7.0f; // bit code 010
  red_3 = (5*red_0 + 2*red_1)/7.0f; // bit code 011
  red_4 = (4*red_0 + 3*red_1)/7.0f; // bit code 100
  red_5 = (3*red_0 + 4*red_1)/7.0f; // bit code 101
  red_6 = (2*red_0 + 5*red_1)/7.0f; // bit code 110
  red_7 = (1*red_0 + 6*red_1)/7.0f; // bit code 111
}
else
{
  // 4 interpolated color values
  red_2 = (4*red_0 + 1*red_1)/5.0f; // bit code 010
  red_3 = (3*red_0 + 2*red_1)/5.0f; // bit code 011
  red_4 = (2*red_0 + 3*red_1)/5.0f; // bit code 100
  red_5 = (1*red_0 + 4*red_1)/5.0f; // bit code 101
  red_6 = -1.0f;                    // bit code 110
  red_7 =  1.0f;                    // bit code 111
}
```

<span data-ttu-id="e38a0-250">Den Referenzfarben sind 3-Bit-Indizes zugewiesen (000 – 111, da 8 Werte vorhanden sind), die während der Komprimierung in Blöcken von „Rot a” bis „Rot p” gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-250">The reference colors are assigned 3-bit indices (000–111 since there are 8 values), which will be saved in blocks red a through red p during compression.</span></span>

### <a name="span-idbc5spanspan-idbc5spanbc5"></a><span data-ttu-id="e38a0-251"><span id="BC5"></span><span id="bc5"></span>BC5</span><span class="sxs-lookup"><span data-stu-id="e38a0-251"><span id="BC5"></span><span id="bc5"></span>BC5</span></span>

<span data-ttu-id="e38a0-252">Verwenden Sie das BC5-Format, um Zweikomponent-Farbdaten mit 8Bit pro Farbe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e38a0-252">Use the BC5 format to store two-component color data using 8 bits for each color.</span></span> <span data-ttu-id="e38a0-253">Aufgrund der höheren Genauigkeit (im Vergleich zu [BC1](#bc1)), eignet sich BC5 perfekt zum Speichern von Gleitkommadaten im Bereich von \[0 bis 1\] mithilfe des DXGI\_FORMAT\_BC5\_UNORM-Formats und von \[-1 bis +1\] mithilfe des DXGI\_FORMAT\_BC5\_SNORM-Formats.</span><span class="sxs-lookup"><span data-stu-id="e38a0-253">As a result of the increased accuracy (compared to [BC1](#bc1)), BC5 is ideal for storing floating-point data in the range of \[0 to 1\] using the DXGI\_FORMAT\_BC5\_UNORM format and \[-1 to +1\] using the DXGI\_FORMAT\_BC5\_SNORM format.</span></span> <span data-ttu-id="e38a0-254">Bei einer 4×4-Textur mit dem größtmöglichen Datenformat reduziert diese Komprimierungstechnik den erforderlichen Speicherplatz von 32Byte (16Farben × 2-Komponenten/Farben × 1Byte/Komponente) auf 16Byte.</span><span class="sxs-lookup"><span data-stu-id="e38a0-254">Assuming a 4×4 texture using the largest data format possible, this compression technique reduces the memory required from 32 bytes (16 colors × 2 components/color × 1 byte/component) to 16 bytes.</span></span>

- [<span data-ttu-id="e38a0-255">BC5\_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-255">BC5\_UNORM</span></span>](#bc5-unorm)
- [<span data-ttu-id="e38a0-256">BC5\_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-256">BC5\_SNORM</span></span>](#bc5-snorm)

<span data-ttu-id="e38a0-257">Der Algorithmus funktioniert auf 4×4-Texelblöcken.</span><span class="sxs-lookup"><span data-stu-id="e38a0-257">The algorithm works on 4×4 blocks of texels.</span></span> <span data-ttu-id="e38a0-258">Anstatt 16 Farben für die beiden Komponenten zu speichern, speichert der Algorithmus 2 Referenzfarben für jede Komponente (rot\_0, rot\_1, grün\_0 und grün\_1) und 16 3-Bit-Farbindizes für jede Komponente (Rot „a” bis „p” und Grün „a” bis Grün „p”), wie im folgenden Diagramm dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-258">Instead of storing 16 colors for both components, the algorithm stores 2 reference colors for each component (red\_0, red\_1, green\_0, and green\_1) and 16 3-bit color indices for each component (red a through red p and green a through green p), as shown in the following diagram.</span></span>

![das Layout für eine BC5-Komprimierung](images/d3d10-compression-bc5.png)

<span data-ttu-id="e38a0-260">Der Algorithmus verwendet die 3-Bit-Indizes um Farben aus einer Farbtabelle mit 8 Farben herauszufinden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-260">The algorithm uses the 3-bit indices to look up colors from a color table that contains 8 colors.</span></span> <span data-ttu-id="e38a0-261">Die ersten beiden Farben – rot\_0 und tot\_1 (oder grün\_0 und grün\_1) sind die minimalen und maximalen Farben.</span><span class="sxs-lookup"><span data-stu-id="e38a0-261">The first two colors—red\_0 and red\_1 (or green\_0 and green\_1)—are the minimum and maximum colors.</span></span> <span data-ttu-id="e38a0-262">Der Algorithmus berechnet die restlichen Farben mithilfe der linearen Interpolation.</span><span class="sxs-lookup"><span data-stu-id="e38a0-262">The algorithm calculates the remaining colors using linear interpolation.</span></span>

<span data-ttu-id="e38a0-263">Der Algorithmus bestimmt die Anzahl der interpolierten Farbwerte anhand von zwei Referenzwerten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-263">The algorithm determines the number of interpolated color values by examining the two reference values.</span></span> <span data-ttu-id="e38a0-264">Wenn rot\_0 größer als red\_1 ist, interpoliert BC5 6 Farbwerte; andernfalls werden nur 4 interpoliert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-264">If red\_0 is greater than red\_1, then BC5 interpolates 6 color values; otherwise, it interpolates 4.</span></span> <span data-ttu-id="e38a0-265">Wenn BC5 nur 4 Farbwerte interpoliert, legt es die verbleibenden zwei Farbwerte auf 0,0f und 1,0f fest.</span><span class="sxs-lookup"><span data-stu-id="e38a0-265">When BC5 interpolates only 4 color values, it sets the remaining two color values at 0.0f and 1.0f.</span></span>

### <a name="span-idbc5unormspanspan-idbc5unormspanspan-idbc5-unormspanbc5unorm"></a><span data-ttu-id="e38a0-266"><span id="BC5_UNORM"></span><span id="bc5_unorm"></span><span id="bc5-unorm"></span>BC5\_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-266"><span id="BC5_UNORM"></span><span id="bc5_unorm"></span><span id="bc5-unorm"></span>BC5\_UNORM</span></span>

<span data-ttu-id="e38a0-267">Die Interpolation bei Daten mit einer einzelnen Komponente erfolgt wie im folgenden Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-267">The interpolation of the single-component data is done as in the following code sample.</span></span> <span data-ttu-id="e38a0-268">Die Berechnungen für die grünen Komponenten sind ähnlich.</span><span class="sxs-lookup"><span data-stu-id="e38a0-268">The calculations for the green components are similar.</span></span>

```cpp
unsigned word red_0, red_1;

if( red_0 > red_1 )
{
  // 6 interpolated color values
  red_2 = (6*red_0 + 1*red_1)/7.0f; // bit code 010
  red_3 = (5*red_0 + 2*red_1)/7.0f; // bit code 011
  red_4 = (4*red_0 + 3*red_1)/7.0f; // bit code 100
  red_5 = (3*red_0 + 4*red_1)/7.0f; // bit code 101
  red_6 = (2*red_0 + 5*red_1)/7.0f; // bit code 110
  red_7 = (1*red_0 + 6*red_1)/7.0f; // bit code 111
}
else
{
  // 4 interpolated color values
  red_2 = (4*red_0 + 1*red_1)/5.0f; // bit code 010
  red_3 = (3*red_0 + 2*red_1)/5.0f; // bit code 011
  red_4 = (2*red_0 + 3*red_1)/5.0f; // bit code 100
  red_5 = (1*red_0 + 4*red_1)/5.0f; // bit code 101
  red_6 = 0.0f;                     // bit code 110
  red_7 = 1.0f;                     // bit code 111
}
```

<span data-ttu-id="e38a0-269">Den Referenzfarben sind 3-Bit-Indizes zugewiesen (000 – 111, da 8 Werte vorhanden sind), die während der Komprimierung in Blöcken von „Rot a” bis „Rot p” gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-269">The reference colors are assigned 3-bit indices (000–111 since there are 8 values), which will be saved in blocks red a through red p during compression.</span></span>

### <a name="span-idbc5snormspanspan-idbc5snormspanspan-idbc5-snormspanbc5snorm"></a><span data-ttu-id="e38a0-270"><span id="BC5_SNORM"></span><span id="bc5_snorm"></span><span id="bc5-snorm"></span>BC5\_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-270"><span id="BC5_SNORM"></span><span id="bc5_snorm"></span><span id="bc5-snorm"></span>BC5\_SNORM</span></span>

<span data-ttu-id="e38a0-271">Das DXGI\_FORMAT\_BC4\_SNORM ist identisch, mit Ausnahme der Codierung der Daten im Bereich SNORM. Wenn 4 Farbwerte interpoliert werden, sind die zwei zusätzlichen Werte -1,0f and 1,0f.</span><span class="sxs-lookup"><span data-stu-id="e38a0-271">The DXGI\_FORMAT\_BC5\_SNORM is exactly the same, except that the data is encoded in SNORM range and when 4 data values are interpolated, the two additional values are -1.0f and 1.0f.</span></span> <span data-ttu-id="e38a0-272">Die Interpolation bei Daten mit einer einzelnen Komponente erfolgt wie im folgenden Codebeispiel dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e38a0-272">The interpolation of the single-component data is done as in the following code sample.</span></span> <span data-ttu-id="e38a0-273">Die Berechnungen für die grünen Komponenten sind ähnlich.</span><span class="sxs-lookup"><span data-stu-id="e38a0-273">The calculations for the green components are similar.</span></span>

```cpp
signed word red_0, red_1;

if( red_0 > red_1 )
{
  // 6 interpolated color values
  red_2 = (6*red_0 + 1*red_1)/7.0f; // bit code 010
  red_3 = (5*red_0 + 2*red_1)/7.0f; // bit code 011
  red_4 = (4*red_0 + 3*red_1)/7.0f; // bit code 100
  red_5 = (3*red_0 + 4*red_1)/7.0f; // bit code 101
  red_6 = (2*red_0 + 5*red_1)/7.0f; // bit code 110
  red_7 = (1*red_0 + 6*red_1)/7.0f; // bit code 111
}
else
{
  // 4 interpolated color values
  red_2 = (4*red_0 + 1*red_1)/5.0f; // bit code 010
  red_3 = (3*red_0 + 2*red_1)/5.0f; // bit code 011
  red_4 = (2*red_0 + 3*red_1)/5.0f; // bit code 100
  red_5 = (1*red_0 + 4*red_1)/5.0f; // bit code 101
  red_6 = -1.0f;                    // bit code 110
  red_7 =  1.0f;                    // bit code 111
}
```

<span data-ttu-id="e38a0-274">Den Referenzfarben sind 3-Bit-Indizes zugewiesen (000 – 111, da 8 Werte vorhanden sind), die während der Komprimierung in Blöcken von „Rot a” bis „Rot p” gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="e38a0-274">The reference colors are assigned 3-bit indices (000–111 since there are 8 values), which will be saved in blocks red a through red p during compression.</span></span>

## <a name="span-iddifferencesspanspan-iddifferencesspanspan-iddifferencesspanformat-conversion"></a><span data-ttu-id="e38a0-275"><span id="Differences"></span><span id="differences"></span><span id="DIFFERENCES"></span>Konvertieren des Formats</span><span class="sxs-lookup"><span data-stu-id="e38a0-275"><span id="Differences"></span><span id="differences"></span><span id="DIFFERENCES"></span>Format conversion</span></span>

<span data-ttu-id="e38a0-276">Direct3D ermöglicht Kopien zwischen vorstrukturierten, typisierten Texturen und blockkomprimierten Texturen für die gleiche Bit-Breite.</span><span class="sxs-lookup"><span data-stu-id="e38a0-276">Direct3D enables copies between prestructured-typed textures and block-compressed textures of the same bit widths.</span></span>

<span data-ttu-id="e38a0-277">Sie können Ressourcen zwischen verschiedenen Formattypen kopieren.</span><span class="sxs-lookup"><span data-stu-id="e38a0-277">You can copy resources between a few format types.</span></span> <span data-ttu-id="e38a0-278">Diese Art von Kopiervorgang führt eine Formatkonvertierung durch, die Ressourcendaten als einen neuen Formattyp neu interpretiert.</span><span class="sxs-lookup"><span data-stu-id="e38a0-278">This type of copy operation performs a type of format conversion that reinterprets resource data as a different format type.</span></span> <span data-ttu-id="e38a0-279">Betrachten Sie in diesem Beispiel den Unterschied zwischen neu interpretierten Daten mit der Funktionsweise einer typischen Art der Konvertierung:</span><span class="sxs-lookup"><span data-stu-id="e38a0-279">Consider this example that shows the difference between reinterpreting data with the way a more typical type of conversion behaves:</span></span>

```cpp
FLOAT32 f = 1.0f;
UINT32 u;
```

<span data-ttu-id="e38a0-280">Um „f” als Typ „u” neu zu interpretieren, verwenden Sie [memcpy](http://msdn.microsoft.com/library/dswaw1wk.aspx):</span><span class="sxs-lookup"><span data-stu-id="e38a0-280">To reinterpret 'f' as the type of 'u', use [memcpy](http://msdn.microsoft.com/library/dswaw1wk.aspx):</span></span>

```cpp
memcpy( &u, &f, sizeof( f ) ); // 'u' becomes equal to 0x3F800000.
```

<span data-ttu-id="e38a0-281">In der vorherigen neuen Interpretation ändert sich der zugrunde liegende Wert der Daten nicht. [memcpy](http://msdn.microsoft.com/library/dswaw1wk.aspx) interpretiert den Float-Wert als Ganzzahl ohne Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="e38a0-281">In the preceding reinterpretation, the underlying value of the data doesn’t change; [memcpy](http://msdn.microsoft.com/library/dswaw1wk.aspx) reinterprets the float as an unsigned integer.</span></span>

<span data-ttu-id="e38a0-282">Verwenden Sie zum Ausführen der typischen Art der Konvertierung foglende Zuweisung:</span><span class="sxs-lookup"><span data-stu-id="e38a0-282">To perform the more typical type of conversion, use assignment:</span></span>

```cpp
u = f; // 'u' becomes 1.
```

<span data-ttu-id="e38a0-283">In der vorherigen Konvertierung ändert sich der zugrunde liegende Wert der Daten.</span><span class="sxs-lookup"><span data-stu-id="e38a0-283">In the preceding conversion, the underlying value of the data changes.</span></span>

<span data-ttu-id="e38a0-284">Die folgende Tabelle enthält die zulässigen Quell- und Zielformate, die Sie in dieser neu interpretierten Art der Formatkonvertierung verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e38a0-284">The following table lists the allowable source and destination formats that you can use in this reinterpretation type of format conversion.</span></span> <span data-ttu-id="e38a0-285">Sie müssen die Werte ordnungsgemäß codieren, damit die Neuinterpretation wie gewünscht ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e38a0-285">You must encode the values properly for the reinterpretation to work as expected.</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e38a0-286">Bit-Breite</span><span class="sxs-lookup"><span data-stu-id="e38a0-286">Bit Width</span></span></th>
<th align="left"><span data-ttu-id="e38a0-287">Nicht komprimierte Ressource</span><span class="sxs-lookup"><span data-stu-id="e38a0-287">Uncompressed Resource</span></span></th>
<th align="left"><span data-ttu-id="e38a0-288">Blockkomprimierte Ressource</span><span class="sxs-lookup"><span data-stu-id="e38a0-288">Block-Compressed Resource</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e38a0-289">32</span><span class="sxs-lookup"><span data-stu-id="e38a0-289">32</span></span></td>
<td align="left"><p><span data-ttu-id="e38a0-290">DXGI_FORMAT_R32_UINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-290">DXGI_FORMAT_R32_UINT</span></span></p>
<p><span data-ttu-id="e38a0-291">DXGI_FORMAT_R32_SINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-291">DXGI_FORMAT_R32_SINT</span></span></p></td>
<td align="left"><span data-ttu-id="e38a0-292">DXGI_FORMAT_R9G9B9E5_SHAREDEXP</span><span class="sxs-lookup"><span data-stu-id="e38a0-292">DXGI_FORMAT_R9G9B9E5_SHAREDEXP</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e38a0-293">64</span><span class="sxs-lookup"><span data-stu-id="e38a0-293">64</span></span></td>
<td align="left"><p><span data-ttu-id="e38a0-294">DXGI_FORMAT_R16G16B16A16_UINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-294">DXGI_FORMAT_R16G16B16A16_UINT</span></span></p>
<p><span data-ttu-id="e38a0-295">DXGI_FORMAT_R16G16B16A16_SINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-295">DXGI_FORMAT_R16G16B16A16_SINT</span></span></p>
<p><span data-ttu-id="e38a0-296">DXGI_FORMAT_R32G32_UINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-296">DXGI_FORMAT_R32G32_UINT</span></span></p>
<p><span data-ttu-id="e38a0-297">DXGI_FORMAT_R32G32_SINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-297">DXGI_FORMAT_R32G32_SINT</span></span></p></td>
<td align="left"><p><span data-ttu-id="e38a0-298">DXGI_FORMAT_BC1_UNORM[_SRGB]</span><span class="sxs-lookup"><span data-stu-id="e38a0-298">DXGI_FORMAT_BC1_UNORM[_SRGB]</span></span></p>
<p><span data-ttu-id="e38a0-299">DXGI_FORMAT_BC4_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-299">DXGI_FORMAT_BC4_UNORM</span></span></p>
<p><span data-ttu-id="e38a0-300">DXGI_FORMAT_BC4_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-300">DXGI_FORMAT_BC4_SNORM</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e38a0-301">128</span><span class="sxs-lookup"><span data-stu-id="e38a0-301">128</span></span></td>
<td align="left"><p><span data-ttu-id="e38a0-302">DXGI_FORMAT_R32G32B32A32_UINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-302">DXGI_FORMAT_R32G32B32A32_UINT</span></span></p>
<p><span data-ttu-id="e38a0-303">DXGI_FORMAT_R32G32B32A32_SINT</span><span class="sxs-lookup"><span data-stu-id="e38a0-303">DXGI_FORMAT_R32G32B32A32_SINT</span></span></p></td>
<td align="left"><p><span data-ttu-id="e38a0-304">DXGI_FORMAT_BC2_UNORM[_SRGB]</span><span class="sxs-lookup"><span data-stu-id="e38a0-304">DXGI_FORMAT_BC2_UNORM[_SRGB]</span></span></p>
<p><span data-ttu-id="e38a0-305">DXGI_FORMAT_BC3_UNORM[_SRGB]</span><span class="sxs-lookup"><span data-stu-id="e38a0-305">DXGI_FORMAT_BC3_UNORM[_SRGB]</span></span></p>
<p><span data-ttu-id="e38a0-306">DXGI_FORMAT_BC5_UNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-306">DXGI_FORMAT_BC5_UNORM</span></span></p>
<p><span data-ttu-id="e38a0-307">DXGI_FORMAT_BC5_SNORM</span><span class="sxs-lookup"><span data-stu-id="e38a0-307">DXGI_FORMAT_BC5_SNORM</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e38a0-308"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e38a0-308"><span id="related-topics"></span>Related topics</span></span>

[<span data-ttu-id="e38a0-309">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="e38a0-309">Compressed texture resources</span></span>](compressed-texture-resources.md)
