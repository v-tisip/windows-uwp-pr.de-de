---
title: Vorgänge für Kachelpools
description: Vorgänge für Kachelpools umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Gewinnen von vorübergehendem Speicherplatz für das System für den gesamten Kachelpool) und das Zurückfordern von Ressourcen.
ms.assetid: 90347F7F-C991-4287-BD70-494533ECDC8A
keywords:
- Vorgänge für Kachelpools
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ec546d467f338bbbe2f4dbf89015a4487e001718
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7173723"
---
# <a name="operations-available-on-tile-pools"></a><span data-ttu-id="fbcbc-104">Vorgänge für Kachelpools</span><span class="sxs-lookup"><span data-stu-id="fbcbc-104">Operations available on tile pools</span></span>


<span data-ttu-id="fbcbc-105">Vorgänge für Kachelpools umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Gewinnen von vorübergehendem Speicherplatz für das System für den gesamten Kachelpool) und das Zurückfordern von Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-105">Operations on tile pools include resizing a tile pool, offering resources (yielding memory temporarily to the system for the entire tile pool), and reclaiming resources.</span></span>

-   <span data-ttu-id="fbcbc-106">Die Lebensdauer von Kachelpools funktioniert wie jede andere Direct3D-Ressource, die mittels Referenzzählung gesichert ist, in diesem Fall einschließlich der Nachverfolgung von Zuordnungen von Streaming-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-106">The lifetime of tile pools works like any other Direct3D Resource, backed by reference counting, including in this case tracking of mappings from streaming resources.</span></span> <span data-ttu-id="fbcbc-107">Wenn die Anwendung nicht mehr auf einen Kachelpool verweist und alle Kachelzuordnungen auf den Speicher nicht mehr vorhanden sind und die Zugriffe durch den Grafikprozessor (GPU) abgeschlossen sind, wird das Betriebssystem die Zuordnung des Kachelpools aufheben.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-107">When the application no longer references a tile pool and any tile mappings to the memory are gone and graphics processing unit (GPU) accesses completed, the operating system will deallocate the tile pool.</span></span>
-   <span data-ttu-id="fbcbc-108">API, die im Zusammenhang mit der gemeinsamen Nutzung und Synchronisierung von Oberflächen stehen, funktionieren für Kachelpools (jedoch nicht direkt auf Streaming-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="fbcbc-108">APIs related to surface sharing and synchronization work for tile pools (but not directly on streaming resources).</span></span> <span data-ttu-id="fbcbc-109">Ähnlich wie das Verhalten für angebotene Kachelpools werden Direct3D-Befehle, die auf Streaming-Ressourcen zugreifen, die auf einen Kachelpool verweisen, gelöscht, wenn die Kachelpool freigegeben wurde und derzeit von einem anderen Gerät und Prozess erworben wird.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-109">Similar to the behavior for offered tile pools, Direct3D commands that access streaming resources that point to a tile pool are dropped if the tile pool has been shared and is currently acquired by another device and process.</span></span>
-   <span data-ttu-id="fbcbc-110">Ändern der Größe eines Kachelpools.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-110">Resizing a tile pool.</span></span>
-   <span data-ttu-id="fbcbc-111">Anbieten von Ressourcen und Zurückfordern von Ressourcen - diese Vorgänge zum Gewinnen von vorübergehendem Speicherplatz für das System wirken auf den gesamten Kachelpool (und sind nicht für einzelne Streaming-Ressourcen verfügbar).</span><span class="sxs-lookup"><span data-stu-id="fbcbc-111">Offering resources and reclaiming resources - These operations for yielding memory temporarily to the system operate on the entire tile pool (and aren't available for individual streaming resources).</span></span> <span data-ttu-id="fbcbc-112">Verweist eine Streaming-Ressource auf eine Kachel in einem angebotenen Kachelpool, verhält sich die Streaming-Ressource als würde sie angeboten (z. B. die Runtime löscht Befehle, die darauf verweisen).</span><span class="sxs-lookup"><span data-stu-id="fbcbc-112">If a streaming resource points to a tile in an offered tile pool, the streaming resource behaves as if it is offered (for example, the runtime drops commands that reference it).</span></span>

<span data-ttu-id="fbcbc-113">Daten können nicht direkt in den und aus dem Kachelpoolspeicher kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-113">Data can't be copied to and from tile pool memory directly.</span></span> <span data-ttu-id="fbcbc-114">Zugriffe auf den Speicher erfolgen immer über Streaming-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="fbcbc-114">Accesses to the memory are always done through streaming resources.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="fbcbc-115"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fbcbc-115"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="fbcbc-116">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="fbcbc-116">Creating streaming resources</span></span>](creating-streaming-resources.md)

 

 




