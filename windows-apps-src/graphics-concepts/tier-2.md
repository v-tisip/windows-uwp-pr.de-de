---
title: Ebene2
description: Der Support der Ebene2 für Streamingressourcen fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.
ms.assetid: 111A28EA-661A-4D29-921A-F2E376A46DC5
keywords:
- Ebene2
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: fac8780995231ce56d1264ea8a1a5cb52fd9a3d0
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5826284"
---
# <a name="tier-2"></a><span data-ttu-id="83c72-104">Ebene2</span><span class="sxs-lookup"><span data-stu-id="83c72-104">Tier 2</span></span>


<span data-ttu-id="83c72-105">Der Support der Ebene2 für Streamingressourcen fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</span><span class="sxs-lookup"><span data-stu-id="83c72-105">Tier 2 support for streaming resources adds capabilities beyond Tier 1, such as guaranteeing nonpacked texture mipmap when the size is at least one standard tile shape; shader instructions for clamping level-of-detail (LOD) and for obtaining status about the shader operation; also, reading from NULL-mapped tiles treat that sampled value as zero.</span></span>

## <a name="span-idtier2generalsupportspanspan-idtier2generalsupportspanspan-idtier2generalsupportspantier-2-general-support"></a><span data-ttu-id="83c72-106"><span id="Tier_2_general_support"></span><span id="tier_2_general_support"></span><span id="TIER_2_GENERAL_SUPPORT"></span>Allgemeiner Support der Ebene 2</span><span class="sxs-lookup"><span data-stu-id="83c72-106"><span id="Tier_2_general_support"></span><span id="tier_2_general_support"></span><span id="TIER_2_GENERAL_SUPPORT"></span>Tier 2 general support</span></span>


<span data-ttu-id="83c72-107">Der Support der Ebene 2 umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="83c72-107">Tier 2 support includes the following.</span></span>

-   <span data-ttu-id="83c72-108">Hardware mindestens auf Funktionsebene11.1.</span><span class="sxs-lookup"><span data-stu-id="83c72-108">Hardware at Feature Level 11.1 minimum.</span></span>
-   <span data-ttu-id="83c72-109">Alle Funktionen von der vorherigen Ebene (ohne [Ebene 1](tier-1.md) bestimmte Einschränkungen) sowie die Hinzufügungen in den folgenden Elementen:</span><span class="sxs-lookup"><span data-stu-id="83c72-109">All features of the previous tier (without [Tier 1](tier-1.md) specific limitations) plus the additions in these following items:</span></span>
-   <span data-ttu-id="83c72-110">Shader-Anweisungen für Klammerung-LOD und Feedback über den zugeordneten Status verfügbar.</span><span class="sxs-lookup"><span data-stu-id="83c72-110">Shader instructions for clamping LOD and mapped status feedback are available.</span></span> <span data-ttu-id="83c72-111">Siehe [Belichtung von HLSL-Streamingressourcen](hlsl-streaming-resources-exposure.md)</span><span class="sxs-lookup"><span data-stu-id="83c72-111">See [HLSL streaming resources exposure](hlsl-streaming-resources-exposure.md).</span></span>

<span data-ttu-id="83c72-112">Zusätzlich zu diesen gibt es einige bestimmte nachfolgende Supportfragen.</span><span class="sxs-lookup"><span data-stu-id="83c72-112">In addition to these, there are some specific support issues that follow.</span></span>

## <a name="span-idnon-mappedtilesspanspan-idnon-mappedtilesspanspan-idnon-mappedtilesspannon-mapped-tiles"></a><span data-ttu-id="83c72-113"><span id="Non-mapped_tiles"></span><span id="non-mapped_tiles"></span><span id="NON-MAPPED_TILES"></span>Nicht zugeordnete Kacheln</span><span class="sxs-lookup"><span data-stu-id="83c72-113"><span id="Non-mapped_tiles"></span><span id="non-mapped_tiles"></span><span id="NON-MAPPED_TILES"></span>Non-mapped tiles</span></span>


<span data-ttu-id="83c72-114">Lesevorgänge von nicht zugeordneten Kacheln geben den Wert 0 in allen nicht fehlenden Komponenten des Formats und den Standardwert für fehlende Komponenten zurück.</span><span class="sxs-lookup"><span data-stu-id="83c72-114">Reads from non-mapped tiles return 0 in all non-missing components of the format, and the default for missing components.</span></span>

<span data-ttu-id="83c72-115">Schreibvorgänge auf nicht zugeordnete Kacheln werden beim Wechsel in den Speicher angehalten. Sie könnten jedoch unter Umständen in Anwendungscaches enden, die möglicherweise von nachfolgenden Lesevorgängen auf die gleiche Adresse erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="83c72-115">Writes to non-mapped tiles are stopped from going to memory but might end up in caches that subsequent reads to the same address might or might not pick up.</span></span>

## <a name="span-idtexturefilteringspanspan-idtexturefilteringspanspan-idtexturefilteringspantexture-filtering"></a><span data-ttu-id="83c72-116"><span id="Texture_filtering"></span><span id="texture_filtering"></span><span id="TEXTURE_FILTERING"></span>Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="83c72-116"><span id="Texture_filtering"></span><span id="texture_filtering"></span><span id="TEXTURE_FILTERING"></span>Texture filtering</span></span>


<span data-ttu-id="83c72-117">Filtern mit einem Abbild, welches die **NULL** und nicht-**NULL** Kacheln überspannt und 0 (standardmäßig nach fehlenden Format) für Texel auf **NULL** Kacheln in der gesamten Ausführung beiträgt.</span><span class="sxs-lookup"><span data-stu-id="83c72-117">Texture filtering with a footprint that straddles **NULL** and non-**NULL** tiles contributes 0 (with defaults for missing format components) for texels on **NULL** tiles into the overall filter operation.</span></span> <span data-ttu-id="83c72-118">Ältere Hardware erfüllt diese Anforderung nicht und gibt 0 (mit standardmäßig nach fehlenden Format) für das vollständige Filterergebnis zurück, wenn jegliche Texel (mit ungleich NULL Breite) sich auf einer **NULL** Kachel befinden.</span><span class="sxs-lookup"><span data-stu-id="83c72-118">Some early hardware don't meet this requirement and returns 0 (with defaults for missing format components) for the full filter result if any texels (with nonzero weight) fall on a **NULL** tile.</span></span> <span data-ttu-id="83c72-119">Jede andere Hardware muss die Anforderung erfüllen, alle Texel (mit einer Gewichtung ungleich NULL) in den Filtervorgang einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="83c72-119">No other hardware will be allowed to miss the requirement to include all (nonzero weighted) texels in the filter operation.</span></span>

<span data-ttu-id="83c72-120">**NULL** Texelzugriffe haben zur Folge, dass durch den [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) Vorgang der Feedbackstatus des Texturlesevorgangs mit „false” zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="83c72-120">**NULL** texel accesses cause the [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) operation on the status feedback for a texture read to return false.</span></span> <span data-ttu-id="83c72-121">Dies ist unabhängig davon, wie die Schreibmaske des Texturzugriffsergebnisses im Shader erfolgt, und wie viele Komponenten im Texturformat vorhanden sind (deren Kombination möglicherweise den Eindruck vermittelt, dass auf die Textur nicht zugegriffen werden muss).</span><span class="sxs-lookup"><span data-stu-id="83c72-121">This is regardless of how the texture access result might get write masked in the shader and how many components are in the texture format (the combination of which might make it appear that the texture does not need to be accessed).</span></span>

## <a name="span-idalignmentconstraintsspanspan-idalignmentconstraintsspanspan-idalignmentconstraintsspanalignment-constraints"></a><span data-ttu-id="83c72-122"><span id="Alignment_constraints"></span><span id="alignment_constraints"></span><span id="ALIGNMENT_CONSTRAINTS"></span>Ausrichtungseinschränkungen</span><span class="sxs-lookup"><span data-stu-id="83c72-122"><span id="Alignment_constraints"></span><span id="alignment_constraints"></span><span id="ALIGNMENT_CONSTRAINTS"></span>Alignment constraints</span></span>


<span data-ttu-id="83c72-123">Ausrichtungseinschränkungen für Standardkachelformen: Mipmaps, die mindestens eine Standardkachel in allen Abmessungen ausfüllen, ist die Verwendung der Standardkacheln gewährleistet. Der Rest wird als eine **Einheit** in N-Kacheln (N an die Anwendung gemeldet) betrachtet.</span><span class="sxs-lookup"><span data-stu-id="83c72-123">Alignment constraints for standard tile shapes: Mipmaps that fill at least one standard tile in all dimensions are guaranteed to use the standard tiling, with the remainder considered packed as a **unit** into N tiles (N reported to the application).</span></span> <span data-ttu-id="83c72-124">Die Anwendung kann die N-Kacheln in willkürlich getrennte Orte in einem Kachelpool zuordnen. Sie muss jedoch entweder oder keine der gepackten Kacheln zuordnen.</span><span class="sxs-lookup"><span data-stu-id="83c72-124">The application can map the N tiles into arbitrarily disjoint locations in a tile pool, but must either map all or none of the packed tiles.</span></span> <span data-ttu-id="83c72-125">Die Mip-Verpackung ist ein einzigartiger Satz von gepackten Kacheln pro Array-Segment.</span><span class="sxs-lookup"><span data-stu-id="83c72-125">The mip packing is a unique set of packed tiles per array slice.</span></span>

## <a name="span-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanminmax-reduction-filtering"></a><span data-ttu-id="83c72-126"><span id="Min_Max_reduction_filtering"></span><span id="min_max_reduction_filtering"></span><span id="MIN_MAX_REDUCTION_FILTERING"></span>Min/Max-Reduzierungsfilterung</span><span class="sxs-lookup"><span data-stu-id="83c72-126"><span id="Min_Max_reduction_filtering"></span><span id="min_max_reduction_filtering"></span><span id="MIN_MAX_REDUCTION_FILTERING"></span>Min/Max reduction filtering</span></span>


<span data-ttu-id="83c72-127">Min/Max-Reduzierungsfilterung wird unterstützt.</span><span class="sxs-lookup"><span data-stu-id="83c72-127">Min/Max reduction filtering is supported.</span></span> <span data-ttu-id="83c72-128">Siehe [Textursampling-Features für Streamingressourcen](streaming-resources-texture-sampling-features.md)</span><span class="sxs-lookup"><span data-stu-id="83c72-128">See [Streaming resources texture sampling features](streaming-resources-texture-sampling-features.md).</span></span>

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span data-ttu-id="83c72-129"><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="83c72-129"><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Limitations</span></span>


<span data-ttu-id="83c72-130">Streamingressourcen mit Mipmaps, die in jeglicher Dimension kleiner sind als die Standardkachelgröße, dürfen keine Arraygröße größer als 1 aufweisen.</span><span class="sxs-lookup"><span data-stu-id="83c72-130">Streaming resources with any mipmaps less than standard tile size in any dimension are not allowed to have an array size larger than 1.</span></span>

<span data-ttu-id="83c72-131">Die Einschränkungen der Kachelzugriffe gelten weiterhin, wenn doppelte Zuordnungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="83c72-131">Limitations on how tiles can be accessed when there are duplicate mappings continue to apply.</span></span> <span data-ttu-id="83c72-132">Siehe [Kachelzugriffseinschränkungen bei doppelten Zuordnungen](tile-access-limitations-with-duplicate-mappings.md)</span><span class="sxs-lookup"><span data-stu-id="83c72-132">See [Tile access limitations with duplicate mappings](tile-access-limitations-with-duplicate-mappings.md).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="83c72-133"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="83c72-133"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="83c72-134">Ebenen der Features von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="83c72-134">Streaming resources features tiers</span></span>](streaming-resources-features-tiers.md)

 

 




