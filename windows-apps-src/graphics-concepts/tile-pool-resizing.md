---
title: Ändern der Größe des Kachelpools
description: Ändern der Größe eines Kachelpools zum Vergrößern eines Kachelpools, wenn die Anwendung mehr Arbeit der Streamingressourcen benötigt, welche in diese zuordnen, bzw. zum Verkleinern des Kachelpools, wenn weniger Speicherplatz benötigt wird.
ms.assetid: A54A06DC-BDDB-42DC-85E8-C64241100ED5
keywords:
- Ändern der Größe des Kachelpools
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e676b28750375a353bb41ce8e14ec1d4c3371c4c
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7145527"
---
# <a name="tile-pool-resizing"></a><span data-ttu-id="cdc03-104">Ändern der Größe des Kachelpools</span><span class="sxs-lookup"><span data-stu-id="cdc03-104">Tile pool resizing</span></span>


<span data-ttu-id="cdc03-105">Ändern der Größe eines Kachelpools zum Vergrößern eines Kachelpools, wenn die Anwendung mehr Arbeit der Streamingressourcen benötigt, welche in diese zuordnen, bzw. zum Verkleinern des Kachelpools, wenn weniger Speicherplatz benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="cdc03-105">Resize a tile pool to grow a tile pool if the application needs more working set for the streaming resources mapping into it, or to shrink if less space is needed.</span></span> <span data-ttu-id="cdc03-106">Eine weitere Anwendungsmöglichkeit ist die Zuordnung zusätzlicher Kachelpools für neue Streamingressourcen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-106">Another option for applications is to allocate additional tile pools for new streaming resources.</span></span> <span data-ttu-id="cdc03-107">Wenn jedoch eine einzelne Streamingressource mehr Speicherplatz benötigt als anfangs im Kachelpool verfügbar ist, dann ist die Vergrößerung des Kachelpools eine gute Wahl.</span><span class="sxs-lookup"><span data-stu-id="cdc03-107">But if any single streaming resource needs more space than initially available in its tile pool, growing the tile pool is a good option.</span></span> <span data-ttu-id="cdc03-108">Eine Streamingressource kann nicht Zuordnungen in mehreren Kachel Pools gleichzeitig haben.</span><span class="sxs-lookup"><span data-stu-id="cdc03-108">A streaming resource can't have mappings into multiple tile pools at the same time.</span></span>

<span data-ttu-id="cdc03-109">Wenn ein Kachelpool vergrößert wurde, werden weitere Kacheln durch den Anzeigetreiber am Ende über eine oder mehrere neue Vergaben hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cdc03-109">When a tile pool is grown, additional tiles are added to the end via one or more new allocations by the display driver.</span></span> <span data-ttu-id="cdc03-110">Diese Aufschlüsselung der Vergaben ist in der Anwendung nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="cdc03-110">This breakdown into allocations isn't visible to the application.</span></span> <span data-ttu-id="cdc03-111">Vorhandener Speicher im Kachelpool bleibt unverändert, und vorhandene Zuordnungen der Streamingressourcen im Arbeitsspeicher bleiben erhalten.</span><span class="sxs-lookup"><span data-stu-id="cdc03-111">Existing memory in the tile pool is left untouched, and existing streaming resource mappings into that memory remain intact.</span></span>

<span data-ttu-id="cdc03-112">Wenn ein Kachelpool verkleinert wird, werden die Kacheln ab dem Ende entfernt.</span><span class="sxs-lookup"><span data-stu-id="cdc03-112">When a tile pool is shrunk, tiles are removed from the end.</span></span> <span data-ttu-id="cdc03-113">Kacheln werden auch bis auf 0, d.h. bis auf die ursprüngliche Vergabegröße, entfernt. Das bedeutet, dass über die neue Größe hinaus keine neuen Zuordnungen hergestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="cdc03-113">Tiles are removed even below the initial allocation size, down to 0, which means new mappings can't be made past the new size.</span></span> <span data-ttu-id="cdc03-114">Bestehende Zuordnung über das Ende der neuen Größe hinaus bleiben jedoch unverändert und verwendbar.</span><span class="sxs-lookup"><span data-stu-id="cdc03-114">But, existing mappings past the end of the new size remain intact and useable.</span></span> <span data-ttu-id="cdc03-115">Der Anzeigetreiber wird den Arbeitsspeicher behalten, so lange Zuordnungen zu einem Teil der Vergaben, die der Treiber für die Kachelpoolspeicher verwendet, bestehen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-115">The display driver will keep the memory around as long as mappings to any part of the allocations that the driver uses for the tile pool memory remains.</span></span> <span data-ttu-id="cdc03-116">Wenn nach dem Verkleinern ein Teil des Speichers aktiv gehalten wird, da Kachelzuordnungen darauf zeigen und der Kachelpool erneut (mit beliebiger Menge) vergrößert wurde, wird der vorhandene Arbeitsspeicher zunächst wiederverwendet, bevor jegliche zusätzlichen Vergaben für den Vergrößerungsvorgang erfolgen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-116">If after shrinking some memory has been kept alive because tile mappings are pointing to it and then the tile pool is regrown again (by any amount), the existing memory is reused first before any additional allocations occur to service the size of the grow operation.</span></span>

<span data-ttu-id="cdc03-117">Um Speicherplatz sparen zu können, muss eine Anwendung nicht nur einen Kachelpool verkleinern, sondern auch bestehende Zuordnungen über dem Ende der neuen, kleineren Kachelpoolgröße hinaus entfernen/erneut zuordnen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-117">To be able to save memory, an application has to not only shrink a tile pool but also remove/remap existing mappings past the end of the new smaller tile pool size.</span></span>

<span data-ttu-id="cdc03-118">Der Vorgang zur Verkleinerung (und Entfernen von Zuordnungen) resultiert nicht unbedingt sofort in Arbeitsspeichereinsparungen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-118">The act of shrinking (and removing mappings) doesn't necessarily produce immediate memory savings.</span></span> <span data-ttu-id="cdc03-119">Das Freigeben von Arbeitsspeicher hängt davon ab, wie präzise die dem Anzeigetreiber zugrunde liegenden Freigaben für den Kachelpool sind.</span><span class="sxs-lookup"><span data-stu-id="cdc03-119">Freeing of memory depends on how granular the display driver's underlying allocations for the tile pool are.</span></span> <span data-ttu-id="cdc03-120">Wenn die Verkleinerung dafür ausreicht, die Vergabe des Anzeigetreibers überflüssig zu machen, kann der Anzeigetreiber sie freigeben.</span><span class="sxs-lookup"><span data-stu-id="cdc03-120">When shrinking happens to be enough to make a display driver allocation unused, the display driver can free it.</span></span> <span data-ttu-id="cdc03-121">Wurde ein Kachel-Pool vergrößert, ist das Verkleinern auf bisherige Größen (und das entsprechende Entfernen/Neuzuordnen der Kachelzuordnungen) die beste Option, um Arbeitsspeicher einzusparen. Dies ist jedoch nicht gewährleistet, falls die Größen nicht genau mit den zugrunde liegenden und vom Anzeigetreiber ausgewählten Vergabegrößen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="cdc03-121">If a tile pool was grown, shrinking to previous sizes (and removing/remapping tile mappings correspondingly) is most likely to yield memory savings, though not guaranteed in the case that the sizes don't exactly align with the underlying allocation sizes chosen by the display driver.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="cdc03-122"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cdc03-122"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="cdc03-123">Zuordnungen erfolgen in einen Kachelpool</span><span class="sxs-lookup"><span data-stu-id="cdc03-123">Mappings are into a tile pool</span></span>](mappings-are-into-a-tile-pool.md)

 

 




