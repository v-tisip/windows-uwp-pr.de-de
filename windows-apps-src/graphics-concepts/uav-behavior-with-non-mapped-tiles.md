---
title: UAV-Verhalten bei nicht zugeordneten Kacheln
description: Das Verhalten der Lese- und Schreibvorgänge der unsortierten Zugriffsansicht (Unordered Access View, UAV) hängt von der Hardwareunterstützung ab.
ms.assetid: CDB224E2-CC07-4568-9AAC-C8DC74536561
keywords:
- UAV-Verhalten bei nicht zugeordneten Kacheln
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a5418de3646f70a815f5c482f9063ea3e48ddfa1
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5872538"
---
# <a name="span-iddirect3dconceptsuavbehaviorwithnon-mappedtilesspanuav-behavior-with-non-mapped-tiles"></a><span data-ttu-id="646d1-104"><span id="direct3dconcepts.uav_behavior_with_non-mapped_tiles"></span>UAV-Verhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="646d1-104"><span id="direct3dconcepts.uav_behavior_with_non-mapped_tiles"></span>UAV behavior with non-mapped tiles</span></span>


<span data-ttu-id="646d1-105">Das Verhalten der Lese- und Schreibvorgänge der unsortierten Zugriffsansicht (Unordered Access View, UAV) hängt von der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="646d1-105">Behavior of unordered access view (UAV) reads and writes depends on the level of hardware support.</span></span> <span data-ttu-id="646d1-106">Eine Aufschlüsselung der Anforderungen finden Sie im Thema zum allgemeinen Lese- und Schreibverhalten unter [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="646d1-106">For a breakdown of requirements, see overall read and write behavior for [Streaming resources features tiers](streaming-resources-features-tiers.md).</span></span> <span data-ttu-id="646d1-107">In diesem Abschnittwird das ideale Verhalten zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="646d1-107">This section summarizes the ideal behavior.</span></span>

<span data-ttu-id="646d1-108">Shader-Operationen, die von einer nicht-zugeordneten Kachel in einer UAV lesen, geben in allen nicht-fehlenden Komponenten des Formats und im Standard für fehlende Komponenten 0 zurück.</span><span class="sxs-lookup"><span data-stu-id="646d1-108">Shader operations that read from a non-mapped tile in a UAV return 0 in all non-missing components of the format, and the default for missing components.</span></span>

<span data-ttu-id="646d1-109">Wenn Shader-Operationen versuchen, auf eine nicht-zugeordnete Kachel zu schreiben, wird nichts in den nicht-zugeordneten Bereich geschrieben (während die Schreibvorgänge in einen zugeordneten Bereich fortgesetzt werden).</span><span class="sxs-lookup"><span data-stu-id="646d1-109">Shader operations that attempt to write to a non-mapped tile cause nothing to be written to the non-mapped area (while writes to a mapped area proceed).</span></span> <span data-ttu-id="646d1-110">Diese ideale Definition für die Behandlung von Schreibvorgängen ist für [Ebene 2](tier-2.md) nicht erforderlich. Schreibvorgänge an nicht zugeordnete Kacheln können zu einem Cache führen, den nachfolgende Lesevorgänge aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="646d1-110">This ideal definition for write handling is not required by [Tier 2](tier-2.md); writes to non-mapped tiles can end up in a cache that subsequent reads could pick up.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="646d1-111"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="646d1-111"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="646d1-112">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="646d1-112">Pipeline access to streaming resources</span></span>](pipeline-access-to-streaming-resources.md)

 

 




