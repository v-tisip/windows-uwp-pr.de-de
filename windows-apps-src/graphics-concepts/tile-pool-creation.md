---
title: Erstellung eines Kachelpools
description: "Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße der einzelnen Kachelpools ist auf die Direct3D11-Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMs entspricht."
ms.assetid: BD51EDD3-4AD3-4733-B014-DD77B9D743BB
keywords: Erstellung eines Kachelpools
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 4336d38bca354da3c30cfe2d7e4b092cff15af83
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="tile-pool-creation"></a><span data-ttu-id="1f2b2-105">Erstellung eines Kachelpools</span><span class="sxs-lookup"><span data-stu-id="1f2b2-105">Tile pool creation</span></span>


<span data-ttu-id="1f2b2-106">Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen.</span><span class="sxs-lookup"><span data-stu-id="1f2b2-106">Applications can create one or more tile pools per Direct3D device.</span></span> <span data-ttu-id="1f2b2-107">Die Gesamtgröße der einzelnen Kachelpools ist auf die Direct3D11-Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMs entspricht.</span><span class="sxs-lookup"><span data-stu-id="1f2b2-107">The total size of each tile pool is restricted to Direct3D 11's resource size limit, which is roughly 1/4 of graphics processing unit (GPU) RAM.</span></span>

<span data-ttu-id="1f2b2-108">Ein Kachelpool besteht aus 64KB großen Kacheln, aber das Betriebssystem (Anzeigetreiber) verwaltet im Hintergrund den gesamten Pool als ein oder mehrere Vergaben – die Aufteilung ist nicht für Anwendungen sichtbar.</span><span class="sxs-lookup"><span data-stu-id="1f2b2-108">A tile pool is made of 64KB tiles, but the operating system (display driver) manages the entire pool as one or more allocations behind the scenes—the breakdown is not visible to applications.</span></span> <span data-ttu-id="1f2b2-109">Streamingressourcen definieren den Inhalt durch das Zeigen auf Kacheln in einem Kachelpool.</span><span class="sxs-lookup"><span data-stu-id="1f2b2-109">Streaming resources define content by pointing at tiles within a tile pool.</span></span> <span data-ttu-id="1f2b2-110">Das Aufheben der Zuordnung einer Kachel über eine Streamingressource erfolgt durch das Zeigen der Kachel auf **NULL**.</span><span class="sxs-lookup"><span data-stu-id="1f2b2-110">Unmapping a tile from a streaming resource is done by pointing the tile to **NULL**.</span></span> <span data-ttu-id="1f2b2-111">Solche nicht zugeordneten Kacheln unterliegen Regeln, die über das Verhalten von Lese- und Schreibvorgängen bestimmen. Mehr Informationen finden Sie im [Vergleich von Kachelpoolressourcen und der Gefahrennachverfolgung](hazard-tracking-versus-tile-pool-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1f2b2-111">Such unmapped tiles have rules about the behavior of reads or writes; see [Hazard tracking versus tile pool resources](hazard-tracking-versus-tile-pool-resources.md).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1f2b2-112"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1f2b2-112"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1f2b2-113">Zuordnungen erfolgen in einen Kachelpool</span><span class="sxs-lookup"><span data-stu-id="1f2b2-113">Mappings are into a tile pool</span></span>](mappings-are-into-a-tile-pool.md)

 

 




