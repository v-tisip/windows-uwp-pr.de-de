---
title: Erstellung eines Kachelpools
description: Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße jedes kachelpools ist auf Direct3D11s Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMS entspricht beschränkt.
ms.assetid: BD51EDD3-4AD3-4733-B014-DD77B9D743BB
keywords:
- Erstellung eines Kachelpools
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: cbb8b61c8eeef1a842a7c6b61d09670f056bb409
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5593338"
---
# <a name="tile-pool-creation"></a><span data-ttu-id="a7a7d-105">Erstellung eines Kachelpools</span><span class="sxs-lookup"><span data-stu-id="a7a7d-105">Tile pool creation</span></span>


<span data-ttu-id="a7a7d-106">Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-106">Applications can create one or more tile pools per Direct3D device.</span></span> <span data-ttu-id="a7a7d-107">Die Gesamtgröße jedes kachelpools ist auf Direct3D11s Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMS entspricht beschränkt.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-107">The total size of each tile pool is restricted to Direct3D11's resource size limit, which is roughly 1/4 of graphics processing unit (GPU) RAM.</span></span>

<span data-ttu-id="a7a7d-108">Ein Kachelpool besteht aus 64KB großen Kacheln, aber das Betriebssystem (Anzeigetreiber) verwaltet im Hintergrund den gesamten Pool als ein oder mehrere Vergaben – die Aufteilung ist nicht für Anwendungen sichtbar.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-108">A tile pool is made of 64KB tiles, but the operating system (display driver) manages the entire pool as one or more allocations behind the scenes—the breakdown is not visible to applications.</span></span> <span data-ttu-id="a7a7d-109">Streamingressourcen definieren den Inhalt durch das Zeigen auf Kacheln in einem Kachelpool.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-109">Streaming resources define content by pointing at tiles within a tile pool.</span></span> <span data-ttu-id="a7a7d-110">Das Aufheben der Zuordnung einer Kachel über eine Streamingressource erfolgt durch das Zeigen der Kachel auf **NULL**.</span><span class="sxs-lookup"><span data-stu-id="a7a7d-110">Unmapping a tile from a streaming resource is done by pointing the tile to **NULL**.</span></span> <span data-ttu-id="a7a7d-111">Solche nicht zugeordneten Kacheln unterliegen Regeln, die über das Verhalten von Lese- und Schreibvorgängen bestimmen. Mehr Informationen finden Sie im [Vergleich von Kachelpoolressourcen und der Gefahrennachverfolgung](hazard-tracking-versus-tile-pool-resources.md).</span><span class="sxs-lookup"><span data-stu-id="a7a7d-111">Such unmapped tiles have rules about the behavior of reads or writes; see [Hazard tracking versus tile pool resources](hazard-tracking-versus-tile-pool-resources.md).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a7a7d-112"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a7a7d-112"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a7a7d-113">Zuordnungen erfolgen in einen Kachelpool</span><span class="sxs-lookup"><span data-stu-id="a7a7d-113">Mappings are into a tile pool</span></span>](mappings-are-into-a-tile-pool.md)

 

 




