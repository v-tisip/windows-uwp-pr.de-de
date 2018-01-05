---
title: UAV-Verhalten bei nicht zugeordneten Kacheln
description: "Das Verhalten der Lese- und Schreibvorgänge der unsortierten Zugriffsansicht (Unordered Access View, UAV) hängt von der Hardwareunterstützung ab."
ms.assetid: CDB224E2-CC07-4568-9AAC-C8DC74536561
keywords: UAV-Verhalten bei nicht zugeordneten Kacheln
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: c1429579ddd896d5c717968f509ddf578a79f2e0
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="span-iddirect3dconceptsuavbehaviorwithnon-mappedtilesspanuav-behavior-with-non-mapped-tiles"></a><span data-ttu-id="5337a-104"><span id="direct3dconcepts.uav_behavior_with_non-mapped_tiles"></span>UAV-Verhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="5337a-104"><span id="direct3dconcepts.uav_behavior_with_non-mapped_tiles"></span>UAV behavior with non-mapped tiles</span></span>


<span data-ttu-id="5337a-105">Das Verhalten der Lese- und Schreibvorgänge der unsortierten Zugriffsansicht (Unordered Access View, UAV) hängt von der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="5337a-105">Behavior of unordered access view (UAV) reads and writes depends on the level of hardware support.</span></span> <span data-ttu-id="5337a-106">Eine Aufschlüsselung der Anforderungen finden Sie im Thema zum allgemeinen Lese- und Schreibverhalten unter [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="5337a-106">For a breakdown of requirements, see overall read and write behavior for [Streaming resources features tiers](streaming-resources-features-tiers.md).</span></span> <span data-ttu-id="5337a-107">In diesem Abschnittwird das ideale Verhalten zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="5337a-107">This section summarizes the ideal behavior.</span></span>

<span data-ttu-id="5337a-108">Shader-Operationen, die von einer nicht-zugeordneten Kachel in einer UAV lesen, geben in allen nicht-fehlenden Komponenten des Formats und im Standard für fehlende Komponenten 0 zurück.</span><span class="sxs-lookup"><span data-stu-id="5337a-108">Shader operations that read from a non-mapped tile in a UAV return 0 in all non-missing components of the format, and the default for missing components.</span></span>

<span data-ttu-id="5337a-109">Wenn Shader-Operationen versuchen, auf eine nicht-zugeordnete Kachel zu schreiben, wird nichts in den nicht-zugeordneten Bereich geschrieben (während die Schreibvorgänge in einen zugeordneten Bereich fortgesetzt werden).</span><span class="sxs-lookup"><span data-stu-id="5337a-109">Shader operations that attempt to write to a non-mapped tile cause nothing to be written to the non-mapped area (while writes to a mapped area proceed).</span></span> <span data-ttu-id="5337a-110">Diese ideale Definition für die Behandlung von Schreibvorgängen ist für [Ebene 2](tier-2.md) nicht erforderlich. Schreibvorgänge an nicht zugeordnete Kacheln können zu einem Cache führen, den nachfolgende Lesevorgänge aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="5337a-110">This ideal definition for write handling is not required by [Tier 2](tier-2.md); writes to non-mapped tiles can end up in a cache that subsequent reads could pick up.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="5337a-111"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5337a-111"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="5337a-112">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="5337a-112">Pipeline access to streaming resources</span></span>](pipeline-access-to-streaming-resources.md)

 

 




