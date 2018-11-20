---
title: Texturfilterung
description: Die Texturfilterung erzeugt eine Farbe für jedes Pixel im 2D-gerenderten Bild des Grundtyps, wenn dieser durch die Abbildung eines 3D-Grundtyps auf einem 2D-Bildschirm gerendert wird.
ms.assetid: 1CCF4138-5D48-4B07-9490-996844F994D8
keywords:
- Texturfilterung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ce80bc0f64e1aba8328880203f22ea3909fdb3e3
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7284133"
---
# <a name="texture-filtering"></a><span data-ttu-id="10bea-104">Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="10bea-104">Texture filtering</span></span>


<span data-ttu-id="10bea-105">Die Texturfilterung erzeugt eine Farbe für jedes Pixel im 2D-gerenderten Bild des Grundtyps, wenn dieser durch die Abbildung eines 3D-Grundtyps auf einem 2D-Bildschirm gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="10bea-105">Texture filtering produces a color for each pixel in the primitive's 2D rendered image when a primitive is rendered by mapping a 3D primitive onto a 2D screen.</span></span>

<span data-ttu-id="10bea-106">Wenn Direct3D einen Grundtyp rendert, bildet es einen 3D-Grundtyp auf einem 2D-Bildschirm ab.</span><span class="sxs-lookup"><span data-stu-id="10bea-106">When Direct3D renders a primitive, it maps the 3D primitive onto a 2D screen.</span></span> <span data-ttu-id="10bea-107">Wenn Grundtyp eine Textur hat, muss Direct3D diese Textur verwenden, um eine Farbe für jedes Pixel im gerenderten 2D-Bild des Grundtyps zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="10bea-107">If the primitive has a texture, Direct3D must use that texture to produce a color for each pixel in the primitive's 2D rendered image.</span></span> <span data-ttu-id="10bea-108">Für jeden Pixel im Bildschirmbild des Grundtyps muss ein Farbwert aus der Textur abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="10bea-108">For every pixel in the primitive's on-screen image, it must obtain a color value from the texture.</span></span> <span data-ttu-id="10bea-109">Dieser Prozess wird als *Texturfilterung* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="10bea-109">This process is called *texture filtering*.</span></span>

<span data-ttu-id="10bea-110">Wenn ein Texturfilterungsvorgang durchgeführt wird, wird die verwendete Textur typischerweise auch vergrößert oder verkleinert.</span><span class="sxs-lookup"><span data-stu-id="10bea-110">When a texture filter operation is performed, the texture being used is typically also being magnified or minified.</span></span> <span data-ttu-id="10bea-111">Anders ausgedrückt: Sie wird einem Grundtypenbild zugeordnet, das kleiner oder größer ist als sie selbst.</span><span class="sxs-lookup"><span data-stu-id="10bea-111">In other words, it is being mapped into a primitive image that is larger or smaller than itself.</span></span> <span data-ttu-id="10bea-112">Die Vergrößerung einer Textur kann dazu führen, dass viele Pixel einem Texel zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="10bea-112">Magnification of a texture can result in many pixels being mapped to one texel.</span></span> <span data-ttu-id="10bea-113">Das Ergebnis kann dann eine ungleichmäßige Darstellung sein.</span><span class="sxs-lookup"><span data-stu-id="10bea-113">The result can be a chunky appearance.</span></span> <span data-ttu-id="10bea-114">Die Verkleinerung einer Textur bedeutet häufig, dass ein Pixel mehreren Texeln zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="10bea-114">Minification of a texture often means that a single pixel is mapped to many texels.</span></span> <span data-ttu-id="10bea-115">Das resultierende Bild kann dann verschwommen aussehen.</span><span class="sxs-lookup"><span data-stu-id="10bea-115">The resulting image can be blurry or aliased.</span></span> <span data-ttu-id="10bea-116">Um diese Probleme zu beheben, muss eine gewisse Mischung der Texelfarben durchgeführt werden, um zu einer Farbe für das Pixel zu kommen.</span><span class="sxs-lookup"><span data-stu-id="10bea-116">To resolve these problems, some blending of the texel colors must be performed to arrive at a color for the pixel.</span></span>

<span data-ttu-id="10bea-117">Direct3D vereinfacht den komplexen Vorgang der Texturfilterung.</span><span class="sxs-lookup"><span data-stu-id="10bea-117">Direct3D simplifies the complex process of texture filtering.</span></span> <span data-ttu-id="10bea-118">Es bietet Ihnen drei Arten der Texturfilterung: lineare Filterung, anisotropische Filterung und Mipmap-Filterung.</span><span class="sxs-lookup"><span data-stu-id="10bea-118">It provides you with three types of texture filtering - linear filtering, anisotropic filtering, and mipmap filtering.</span></span> <span data-ttu-id="10bea-119">Wenn Sie sich für keine Texturfilterung entscheiden, verwendet Direct3D die als „Sampling am nächstgelegenen Punkt“ bezeichnete Technik.</span><span class="sxs-lookup"><span data-stu-id="10bea-119">If you select no texture filtering, Direct3D uses a technique called nearest-point sampling.</span></span>

<span data-ttu-id="10bea-120">Jede Art der Texturfilterung hat Vor- und Nachteile.</span><span class="sxs-lookup"><span data-stu-id="10bea-120">Each type of texture filtering has advantages and disadvantages.</span></span> <span data-ttu-id="10bea-121">So kann die lineare Texturfilterung etwa zu gezackten Rändern oder einem ungleichmäßigen Erscheinungsbild des fertigen Biĺdes führen.</span><span class="sxs-lookup"><span data-stu-id="10bea-121">For instance, linear texture filtering can produce jagged edges or a chunky appearance in the final image.</span></span> <span data-ttu-id="10bea-122">Andererseits ist dies eine Texturfilterungsmethode, die nur geringe Rechenleistung erfordert.</span><span class="sxs-lookup"><span data-stu-id="10bea-122">However, it is a computationally low-overhead method of texture filtering.</span></span> <span data-ttu-id="10bea-123">Die Filterung mit Mipmaps liefert gewöhnlich die besten Ergebnisse, besonders wenn dazu noch die anisotropische Filterung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="10bea-123">Filtering with mipmaps usually produces the best results, especially when combined with anisotropic filtering.</span></span> <span data-ttu-id="10bea-124">Dies ist jedoch von allen Techniken, die Direct3D unterstützt, die mit dem größten Speicherbedarf.</span><span class="sxs-lookup"><span data-stu-id="10bea-124">However, it requires the most memory of the techniques that Direct3D supports.</span></span>

## <a name="span-idtypes-of-texture-filteringspanspan-idtypes-of-texture-filteringspanspan-idtypes-of-texture-filteringspantypes-of-texture-filtering"></a><span data-ttu-id="10bea-125"><span id="Types-of-texture-filtering"></span><span id="types-of-texture-filtering"></span><span id="TYPES-OF-TEXTURE-FILTERING"></span>Arten der Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="10bea-125"><span id="Types-of-texture-filtering"></span><span id="types-of-texture-filtering"></span><span id="TYPES-OF-TEXTURE-FILTERING"></span>Types of texture filtering</span></span>


<span data-ttu-id="10bea-126">Direct3D unterstützt die folgenden Verfahren für die Texturfilterung.</span><span class="sxs-lookup"><span data-stu-id="10bea-126">Direct3D supports the following texture filtering approaches.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="10bea-127"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="10bea-127"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="10bea-128">Thema</span><span class="sxs-lookup"><span data-stu-id="10bea-128">Topic</span></span></th>
<th align="left"><span data-ttu-id="10bea-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="10bea-129">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="nearest-point-sampling.md"><span data-ttu-id="10bea-130">Sampling am nächstgelegenen Punkt</span><span class="sxs-lookup"><span data-stu-id="10bea-130">Nearest-point sampling</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="10bea-131">Anwendungen müssen nicht die Texturfilterung verwenden.</span><span class="sxs-lookup"><span data-stu-id="10bea-131">Applications are not required to use texture filtering.</span></span> <span data-ttu-id="10bea-132">Direct3D kann so eingerichtet werden, dass es die Texeladresse berechnet, die häufig nicht auf ganze Zahlen geschätzt wird, und die Farbe des Texels mit der nächstgelegenen ganzzahligen Adresse kopiert.</span><span class="sxs-lookup"><span data-stu-id="10bea-132">Direct3D can be set so that it computes the texel address, which often does not evaluate to integers, and copies the color of the texel with the closest integer address.</span></span> <span data-ttu-id="10bea-133">Dieser Prozess wird bezeichnet als <em>Sampling am nächstgelegenen Punkt</em>.</span><span class="sxs-lookup"><span data-stu-id="10bea-133">This process is called <em>nearest-point sampling</em>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="bilinear-texture-filtering.md"><span data-ttu-id="10bea-134">Bilineare Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="10bea-134">Bilinear texture filtering</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="10bea-135">Die <em>bilineare Filterung</em> berechnet den gewichteten Durchschnitt der 4Texel, die dem Sampling-Punkt am nächsten liegen.</span><span class="sxs-lookup"><span data-stu-id="10bea-135"><em>Bilinear filtering</em> calculates the weighted average of the 4 texels closest to the sampling point.</span></span> <span data-ttu-id="10bea-136">Diese Filtermethode ist präziser und gängiger als das Filtern am nächstgelegenen Punkt.</span><span class="sxs-lookup"><span data-stu-id="10bea-136">This filtering approach is more accurate and common than nearest-point filtering.</span></span> <span data-ttu-id="10bea-137">Dieser Ansatz ist effizient, da er in moderner Grafikhardware implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="10bea-137">This approach is efficient because it is implemented in modern graphics hardware.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="anisotropic-texture-filtering.md"><span data-ttu-id="10bea-138">Anisotropische Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="10bea-138">Anisotropic texture filtering</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="10bea-139"><em>Anisotropie</em> ist die sichtbare Verzerrung bei Texeln eines 3D-Objekts, dessen Oberfläche gegenüber der Bildschirmebene in einem Winkel ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="10bea-139"><em>Anisotropy</em> is the distortion visible in the texels of a 3D object whose surface is oriented at an angle with respect to the plane of the screen.</span></span> <span data-ttu-id="10bea-140">Wenn ein Pixel eines anisotropischen Grundtyps einem Texel zugeordnet ist, wird die Form verzerrt.</span><span class="sxs-lookup"><span data-stu-id="10bea-140">When a pixel from an anisotropic primitive is mapped to texels, its shape is distorted.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture-filtering-with-mipmaps.md"><span data-ttu-id="10bea-141">Texturfilterung mit Mipmaps</span><span class="sxs-lookup"><span data-stu-id="10bea-141">Texture filtering with mipmaps</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="10bea-142">Ein <em>Mipmap</em> ist eine Sequenz von Texturen, von denen jede eine Darstellung desselben Bildes mit schrittweise niedrigerer Auflösung ist.</span><span class="sxs-lookup"><span data-stu-id="10bea-142">A <em>mipmap</em> is a sequence of textures, each of which is a progressively lower resolution representation of the same image.</span></span> <span data-ttu-id="10bea-143">Höhe und Breite der einzelnen Bilder bzw. Ebenen des Mipmaps sind jeweils um eine Zweierpotenz geringer als die der vorherigen Ebene.</span><span class="sxs-lookup"><span data-stu-id="10bea-143">The height and width of each image, or level, in the mipmap is a power-of-two smaller than the previous level.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="10bea-144"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="10bea-144"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="10bea-145">Texturen</span><span class="sxs-lookup"><span data-stu-id="10bea-145">Textures</span></span>](textures.md)

 

 




