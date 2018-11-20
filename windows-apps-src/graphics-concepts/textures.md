---
title: Texturen
description: Texturen sind ein leistungsstarkes Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen. Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern, einfach auf erweiterte Texturtechniken zuzugreifen.
ms.assetid: B9E85C9E-B779-4852-9166-6FA2240B7046
keywords:
- Texturen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 516a15c17546d9f9b5e7cb7f8c0651f1372275ae
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7293115"
---
# <a name="textures"></a><span data-ttu-id="59b5d-105">Texturen</span><span class="sxs-lookup"><span data-stu-id="59b5d-105">Textures</span></span>


<span data-ttu-id="59b5d-106">Texturen sind ein leistungsstarkes Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-106">Textures are a powerful tool in creating realism in computer-generated 3D images.</span></span> <span data-ttu-id="59b5d-107">Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern, einfach auf erweiterte Texturtechniken zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-107">Direct3D supports an extensive texturing feature set, providing developers with easy access to advanced texturing techniques.</span></span>

<span data-ttu-id="59b5d-108">Für bessere Leistung sollten Sie dynamische Texturen verwenden.</span><span class="sxs-lookup"><span data-stu-id="59b5d-108">For improved performance, consider using dynamic textures.</span></span> <span data-ttu-id="59b5d-109">Eine dynamische Textur kann für jeden Frame gesperrt, beschrieben und entsperrt werden.</span><span class="sxs-lookup"><span data-stu-id="59b5d-109">A dynamic texture can be locked, written to, and unlocked each frame.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="59b5d-110"><span id="in-this-section"></span>In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="59b5d-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="59b5d-111">Thema</span><span class="sxs-lookup"><span data-stu-id="59b5d-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="59b5d-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="59b5d-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="introduction-to-textures.md"><span data-ttu-id="59b5d-113">Einführung zu Texturen</span><span class="sxs-lookup"><span data-stu-id="59b5d-113">Introduction to textures</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-114">Eine Texturressource ist eine Datenstruktur zum Speichern von Texeln, den kleinsten Einheiten einer Textur, die gelesen oder geschrieben werden können.</span><span class="sxs-lookup"><span data-stu-id="59b5d-114">A texture resource is a data structure to store texels, which are the smallest unit of a texture that can be read or written to.</span></span> <span data-ttu-id="59b5d-115">Wird eine Textur von einem Shader gelesen, kann sie durch Textursampler gefiltert werden.</span><span class="sxs-lookup"><span data-stu-id="59b5d-115">When the texture is read by a shader, it can be filtered by texture samplers.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="basic-texturing-concepts.md"><span data-ttu-id="59b5d-116">Grundlegende Texturkonzepte</span><span class="sxs-lookup"><span data-stu-id="59b5d-116">Basic texturing concepts</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-117">Obwohl frühe computergenerierte 3D-Bilder generell hoch entwickelt waren, sahen diese künstlich glänzend aus.</span><span class="sxs-lookup"><span data-stu-id="59b5d-117">Early computer-generated 3D images, although generally advanced for their time, tended to have a shiny plastic look.</span></span> <span data-ttu-id="59b5d-118">Es fehlte ihnen Kennzeichen – wie etwa Abnutzungen, Risse, Fingerabdrücke und Flecken -, die 3D-Objekten eine realistische optische Komplexität verleihen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-118">They lacked the types of markings-such as scuffs, cracks, fingerprints, and smudges-that give 3D objects realistic visual complexity.</span></span> <span data-ttu-id="59b5d-119">Texturen sind besonders für den verbesserten Realismus von computergenerierten 3D-Bilder beliebt.</span><span class="sxs-lookup"><span data-stu-id="59b5d-119">Textures have become popular for enhancing the realism of computer-generated 3D images.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="texture-addressing-modes.md"><span data-ttu-id="59b5d-120">Texturadressierungsmodi</span><span class="sxs-lookup"><span data-stu-id="59b5d-120">Texture addressing modes</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-121">Die Direct3D-Anwendung kann jedem Scheitelpunkt jedes Grundtyps Texturkoordinaten zuweisen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-121">Your Direct3D application can assign texture coordinates to any vertex of any primitive.</span></span> <span data-ttu-id="59b5d-122">In der Regel liegen die u- und v-Texturkoordinaten, die Sie einem Scheitelpunkt zuweisen, im Bereich zwischen einschließlich 0,0 und 1,0.</span><span class="sxs-lookup"><span data-stu-id="59b5d-122">Typically, the u- and v-texture coordinates that you assign to a vertex are in the range of 0.0 to 1.0 inclusive.</span></span> <span data-ttu-id="59b5d-123">Durch die Zuweisung von Texturkoordinaten außerhalb dieses Bereichs können Sie jedoch bestimmte Textur-Spezialeffekte erzielen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-123">However, by assigning texture coordinates outside that range, you can create certain special texturing effects.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture-filtering.md"><span data-ttu-id="59b5d-124">Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="59b5d-124">Texture filtering</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-125">Die Texturfilterung erzeugt eine Farbe für jedes Pixel im 2D-gerenderten Bild des Grundtyps, wenn dieser durch die Abbildung eines 3D-Grundtyps auf einem 2D-Bildschirm gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="59b5d-125">Texture filtering produces a color for each pixel in the primitive's 2D rendered image when a primitive is rendered by mapping a 3D primitive onto a 2D screen.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="texture-resources.md"><span data-ttu-id="59b5d-126">Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="59b5d-126">Texture resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-127">Texturen sind eine Art von Ressource, die zum Rendern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="59b5d-127">Textures are a type of resource used for rendering.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture-wrapping.md"><span data-ttu-id="59b5d-128">Texturumbruch</span><span class="sxs-lookup"><span data-stu-id="59b5d-128">Texture wrapping</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-129">Der Texturumbruch ändert die grundlegende Weise, in der Direct3D texturierte Vielecke rasterisiert, unter Verwendung der für jeden Scheitelpunkt angegebenen Texturkoordinaten.</span><span class="sxs-lookup"><span data-stu-id="59b5d-129">Texture wrapping changes the basic way that Direct3D rasterizes textured polygons using the texture coordinates specified for each vertex.</span></span> <span data-ttu-id="59b5d-130">Beim Rastern eines Vielecks interpoliert das System zwischen den Texturkoordinaten an jedem der Scheitelpunkte des Vielecks, um die Texel zu bestimmen, die für jedes Pixel des Vielecks zu verwenden sind.</span><span class="sxs-lookup"><span data-stu-id="59b5d-130">While rasterizing a polygon, the system interpolates between the texture coordinates at each of the polygon's vertices to determine the texels that should be used for every pixel of the polygon.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="texture-blending.md"><span data-ttu-id="59b5d-131">Texturmischung</span><span class="sxs-lookup"><span data-stu-id="59b5d-131">Texture blending</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-132">Direct3D kann bis zu acht Texturen auf Grundtypen in einem einzigen Durchlauf auf Grundtypen mischen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-132">Direct3D can blend as many as eight textures onto primitives in a single pass.</span></span> <span data-ttu-id="59b5d-133">Die Verwendung von mehreren gemischten Texturen kann die Framerate einer Direct3D-Anwendung erheblich erhöhen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-133">The use of multiple texture blending can profoundly increase the frame rate of a Direct3D application.</span></span> <span data-ttu-id="59b5d-134">Eine Anwendung verwendet mehrere Texturmischungen zur Anwendung von Texturen, Schatten, glänzender Beleuchtung, diffuser Beleuchtung und anderer Spezialeffekte in einem einzigen Durchgang.</span><span class="sxs-lookup"><span data-stu-id="59b5d-134">An application employs multiple texture blending to apply textures, shadows, specular lighting, diffuse lighting, and other special effects in a single pass.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="light-mapping-with-textures.md"><span data-ttu-id="59b5d-135">Lichtzuordnung mit Texturen</span><span class="sxs-lookup"><span data-stu-id="59b5d-135">Light mapping with textures</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-136">Eine Lichtzuordnung ist eine Textur oder Texturgruppe, die Informationen über das Licht in einer 3D-Szene enthält.</span><span class="sxs-lookup"><span data-stu-id="59b5d-136">A light map is a texture or group of textures that contains information about lighting in a 3D scene.</span></span> <span data-ttu-id="59b5d-137">Lichtzuordnungen ordnen Licht- und Schattenbereiche Grundtypen zu.</span><span class="sxs-lookup"><span data-stu-id="59b5d-137">Light maps map areas of light and shadow onto primitives.</span></span> <span data-ttu-id="59b5d-138">Multipass und das Mischen mehrerer Texturen ermöglichen Ihrer Anwendung, Szenen mit einer realistischeren Darstellung zu rendern als mit Schattierungstechniken.</span><span class="sxs-lookup"><span data-stu-id="59b5d-138">Multipass and multiple texture blending enable your application to render scenes with a more realistic appearance than shading techniques.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="compressed-texture-resources.md"><span data-ttu-id="59b5d-139">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="59b5d-139">Compressed texture resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="59b5d-140">Texturzuordnungen sind digitale Bilder, die auf dreidimensionale Formen gezeichnet werden, um diesen mehr Details zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-140">Texture maps are digitized images drawn on three-dimensional shapes to add visual detail.</span></span> <span data-ttu-id="59b5d-141">Sie werden während der Rasterung in diesen Formen wiedergegeben. Der Prozess kann große Mengen des Systembuses und des Speichers verbrauchen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-141">They are mapped into these shapes during rasterization, and the process can consume large amounts of both the system bus and memory.</span></span> <span data-ttu-id="59b5d-142">Um den von den Texturen verbrauchten Speicherplatz zu reduzieren, unterstützt Direct3D die Komprimierung von Texturoberflächen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-142">To reduce the amount of memory consumed by textures, Direct3D supports the compression of texture surfaces.</span></span> <span data-ttu-id="59b5d-143">Einige Direct3D-Geräte bieten eine systemeigene Unterstützung für komprimierte Texturoberflächen.</span><span class="sxs-lookup"><span data-stu-id="59b5d-143">Some Direct3D devices support compressed texture surfaces natively.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="59b5d-144"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="59b5d-144"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="59b5d-145">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="59b5d-145">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




