---
title: Erstellen von Streamingressourcen
description: Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource laut Kennzeichen angeben, dass die Ressource eine Streamingressource ist.
ms.assetid: B3F3E43C-54D4-458C-9E16-E13CB382C83F
keywords:
- Erstellen von Streamingressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ec96f6245969d32357563c44107f539fb9043aac
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8689010"
---
# <a name="creating-streaming-resources"></a><span data-ttu-id="6f932-104">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6f932-104">Creating streaming resources</span></span>


<span data-ttu-id="6f932-105">Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource laut Kennzeichen angeben, dass die Ressource eine Streamingressource ist.</span><span class="sxs-lookup"><span data-stu-id="6f932-105">Streaming resources are created by specifying a flag when you create a resource, indicating that the resource is a streaming resource.</span></span>

<span data-ttu-id="6f932-106">Einschränkungen für das Erstellen einer Ressource als Streamingressource werden unter [Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6f932-106">Restrictions on when you can create a resource as a streaming resource are described in [Streaming resource creation parameters](streaming-resource-creation-parameters.md).</span></span>

<span data-ttu-id="6f932-107">Beim Erstellen der Ressource wird dem Grafiksystem ein Nicht-Streamingressourcenspeicher zugewiesen, z.B. bei der Zuordnung für ein Array von 2D-Texturen.</span><span class="sxs-lookup"><span data-stu-id="6f932-107">A non-streaming resource's storage is allocated in the graphics system when the resource is created, such as allocation for an array of 2D textures.</span></span>

<span data-ttu-id="6f932-108">Wenn eine Streamingressource erstellt wird, weist das Grafiksystem dem Inhalt der Ressource keinen Speicher hinzu.</span><span class="sxs-lookup"><span data-stu-id="6f932-108">When a streaming resource is created, the graphics system doesn't allocate the storage for the resource contents.</span></span> <span data-ttu-id="6f932-109">Wenn eine Anwendung eine Streamingressource erstellt, reserviert das Grafiksystem stattdessen einen Adressbereich nur für die nebeneinander angeordnete Oberfläche und ermöglicht dann der Anwendung, die Zuordnung der Kacheln zu steuern.</span><span class="sxs-lookup"><span data-stu-id="6f932-109">Instead, when an application creates a streaming resource, the graphics system makes an address space reservation for the tiled surface's area only, and then allows the mapping of the tiles to be controlled by the application.</span></span> <span data-ttu-id="6f932-110">Die „Zuordnung” einer Kachel ist der physische Standort im Arbeitsspeicher, auf den die logische Kachel in einer Ressource verweist (oder **NULL** für eine nicht zugeordnete Kachel).</span><span class="sxs-lookup"><span data-stu-id="6f932-110">The "mapping" of a tile is simply the physical location in memory that a logical tile in a resource points to (or **NULL** for an unmapped tile).</span></span>

<span data-ttu-id="6f932-111">Verwechseln Sie dieses Konzept nicht mit der Zuordnung einer Direct3D-Ressource für den CPU-Zugriff - trotz des gleichen Namens sind diese komplett unabhängig voneinander.</span><span class="sxs-lookup"><span data-stu-id="6f932-111">Don't confuse this concept with the notion of mapping a Direct3D resource for CPU access, which despite using the same name is completely independent.</span></span> <span data-ttu-id="6f932-112">Sie können die Zuordnung jeder einzelnen Kachel nach Bedarf definieren und ändern. Nicht alle Kacheln für eine Oberfläche müssen zu einem bestimmten Zeitpunkt zugeordnet werden, wodurch die Größe des verfügbaren Arbeitsspeichers effektiv verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="6f932-112">You will be able to define and change the mapping of each tile individually as needed, knowing that all tiles for a surface don't need to be mapped at a time, thereby making effective use of the amount of memory available.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="6f932-113"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="6f932-113"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6f932-114">Thema</span><span class="sxs-lookup"><span data-stu-id="6f932-114">Topic</span></span></th>
<th align="left"><span data-ttu-id="6f932-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6f932-115">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="mappings-are-into-a-tile-pool.md"><span data-ttu-id="6f932-116">Zuordnungen in einen Kachelpool</span><span class="sxs-lookup"><span data-stu-id="6f932-116">Mappings are into a tile pool</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-117">Beim Erstellen einer Ressource als Streaming-Ressource stammen die Kacheln, die die Ressource bilden, aus Speicherorten in einem Kachelpool.</span><span class="sxs-lookup"><span data-stu-id="6f932-117">When a resource is created as a streaming resource, the tiles that make up the resource come from pointing at locations in a tile pool.</span></span> <span data-ttu-id="6f932-118">Ein Kachelpool ist ein Arbeitsspeicherpool (der durch eine oder mehrere Zuordnungen hinter den Kulissen unterstützt wird und von der Anwendung nicht sichtbar ist).</span><span class="sxs-lookup"><span data-stu-id="6f932-118">A tile pool is a pool of memory (backed by one or more allocations behind the scenes - unseen by the application).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resource-creation-parameters.md"><span data-ttu-id="6f932-119">Parameter für das Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6f932-119">Streaming resource creation parameters</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-120">Es gibt einige Einschränkungen für den Direct3D-Ressourcentyp, den Sie als Streamingressource erstellen können.</span><span class="sxs-lookup"><span data-stu-id="6f932-120">There are some constraints on the type of Direct3D resources that you can create as a streaming resource.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="tile-pool-creation-parameters.md"><span data-ttu-id="6f932-121">Parameter zum Erstellen des Kachelpools</span><span class="sxs-lookup"><span data-stu-id="6f932-121">Tile pool creation parameters</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-122">Verwenden Sie die Parameter in diesem Abschnitt, um beim Erstellen eines Puffers den Kachelpool zu definieren.</span><span class="sxs-lookup"><span data-stu-id="6f932-122">Use the parameters in this section to define tile pools when creating a buffer.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resource-cross-process-and-device-sharing.md"><span data-ttu-id="6f932-123">Geräte- und prozessübergreifende Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6f932-123">Streaming resource cross-process and device sharing</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-124">Kachelpools können mit anderen Prozessen wie herkömmliche Ressourcen geteilt werden.</span><span class="sxs-lookup"><span data-stu-id="6f932-124">Tile pools can be shared with other processes just like traditional resources.</span></span> <span data-ttu-id="6f932-125">Streamingressourcen, die auf Kachelpools verweisen, können nicht auf allen Geräten und Prozessen freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6f932-125">Streaming resources that reference tile pools can't be shared across devices and processes.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="operations-available-on-streaming-resources.md"><span data-ttu-id="6f932-126">Vorgänge für Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6f932-126">Operations available on streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-127">Dieser Abschnitt enthält Vorgänge, die Sie auf Streamingressourcen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="6f932-127">This section lists operations that you can perform on streaming resources.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="operations-available-on-tile-pools.md"><span data-ttu-id="6f932-128">Vorgänge in Kachelpools</span><span class="sxs-lookup"><span data-stu-id="6f932-128">Operations available on tile pools</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-129">Vorgänge im Kachelpool umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Speicherplatz vorübergehend für das System für den gesamten Kachelpool abgeben) und die Freigabe von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="6f932-129">Operations on tile pools include resizing a tile pool, offering resources (yielding memory temporarily to the system for the entire tile pool), and reclaiming resources.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="how-a-streaming-resource-s-area-is-tiled.md"><span data-ttu-id="6f932-130">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="6f932-130">How a streaming resource's area is tiled</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f932-131">Wenn Sie eine Streamingressource erstellen, bestimmen Dimensionen, Größe des Formats und Anzahl der Mipmaps und/oder Array-Segmente (falls zutreffend) die Anzahl der erforderlichen Kacheln, um die gesamte Oberfläche zu sichern.</span><span class="sxs-lookup"><span data-stu-id="6f932-131">When you create a streaming resource, the dimensions, format element size, and number of mipmaps and/or array slices (if applicable) determine the number of tiles that are required to back the entire surface area.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6f932-132"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6f932-132"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6f932-133">Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6f932-133">Streaming resources</span></span>](streaming-resources.md)

 

 




