---
title: SRV-Verhalten bei nicht zugeordneten Kacheln
description: Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab.
ms.assetid: 0E1D64BE-EB09-4F9D-9800-BD23A3B374EE
keywords:
- SRV-Verhalten bei nicht zugeordneten Kacheln
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: cd5a5308504bda662ae3aff1968122fcfe020ca3
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5689375"
---
# <a name="span-iddirect3dconceptssrvbehaviorwithnon-mappedtilesspansrv-behavior-with-non-mapped-tiles"></a><span data-ttu-id="65bc9-104"><span id="direct3dconcepts.srv_behavior_with_non-mapped_tiles"></span>SRV-Verhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="65bc9-104"><span id="direct3dconcepts.srv_behavior_with_non-mapped_tiles"></span>SRV behavior with non-mapped tiles</span></span>


<span data-ttu-id="65bc9-105">Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="65bc9-105">Behavior of shader resource view (SRV) reads that involve non-mapped tiles depends on the level of hardware support.</span></span> <span data-ttu-id="65bc9-106">Eine Aufschlüsselung der Anforderungen finden Sie unter dem Leseverhalten für die [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="65bc9-106">For a breakdown of requirements, see read behavior for [Streaming resources features tiers](streaming-resources-features-tiers.md).</span></span> <span data-ttu-id="65bc9-107">In diesem Abschnitt wird das Idealverhalten, für das die [Ebene2](tier-2.md) benötigt wird, zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="65bc9-107">This section summarizes the ideal behavior, which [Tier 2](tier-2.md) requires.</span></span>

<span data-ttu-id="65bc9-108">Angenommen, ein Texturfilterungsvorgang liest eine Gruppe Texel in einer SRV.</span><span class="sxs-lookup"><span data-stu-id="65bc9-108">Consider a texture filter operation that reads from a set of texels in an SRV.</span></span> <span data-ttu-id="65bc9-109">Texel, die auf nicht zugeordnete Kacheln fallen, steuern in dem gesamten Filterungsvorgang0 zu allen nicht fehlenden Komponenten des Formats (und den Standardwert für fehlende Komponenten) zusammen mit Beiträgen aus zugeordneten Texeln bei.</span><span class="sxs-lookup"><span data-stu-id="65bc9-109">Texels that fall on non-mapped tiles contribute 0 in all non-missing components of the format (and the default for missing components) into the overall filter operation alongside contributions from mapped texels.</span></span> <span data-ttu-id="65bc9-110">Die Texel sind alle gewichtet und werden kombiniert, unabhängig davon, ob die Daten aus zugeordneten oder nicht zugeordneten Kacheln stammen.</span><span class="sxs-lookup"><span data-stu-id="65bc9-110">The texels are all weighted and combined together independent of whether the data came from mapped or non-mapped tiles.</span></span>

<span data-ttu-id="65bc9-111">Bestimmte Hardware der ersten Generation der [Ebene2](tier-2.md) erfüllt diese Spezifikationen nicht und gibt die0 mit den zuvor beschriebenen Standardwerten als Gesamtfilterungsergebnis zurück, wenn Texel (mit einer Gewichtung von ungleich NULL) auf nicht zugeordnete Kacheln fallen.</span><span class="sxs-lookup"><span data-stu-id="65bc9-111">Some first-generation [Tier 2](tier-2.md) level hardware does not meet this spec requirement, and returns the 0 with defaults described preceding as the overall filter result if any texels (with nonzero weight) fall on non-mapped tiles.</span></span> <span data-ttu-id="65bc9-112">Jede andere Hardware muss die Anforderung erfüllen, alle Texel (mit einer Gewichtung ungleich NULL) in den Filter einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="65bc9-112">No other hardware will be allowed to miss the requirement to include all (nonzero weight) texels in the filter.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="65bc9-113"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="65bc9-113"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="65bc9-114">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="65bc9-114">Pipeline access to streaming resources</span></span>](pipeline-access-to-streaming-resources.md)

 

 




