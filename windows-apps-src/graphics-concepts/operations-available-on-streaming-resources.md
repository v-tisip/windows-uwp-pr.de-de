---
title: Vorgänge für Streaming-Ressourcen
description: Dieser Abschnittenthält Vorgänge, die Sie auf Streaming-Ressourcen ausführen können.
ms.assetid: 700D8C54-0E20-4B2B-BEA3-20F6F72B8E24
keywords:
- Vorgänge für Streaming-Ressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 922798fad97754421541297a5434a81e9c660b2b
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8480752"
---
# <a name="operations-available-on-streaming-resources"></a><span data-ttu-id="eedb4-104">Vorgänge für Streaming-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="eedb4-104">Operations available on streaming resources</span></span>


<span data-ttu-id="eedb4-105">Dieser Abschnittenthält Vorgänge, die Sie auf Streaming-Ressourcen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="eedb4-105">This section lists operations that you can perform on streaming resources.</span></span>

-   <span data-ttu-id="eedb4-106">Aktualisieren von Kachelzuordnungen, die "ungültig" zurückgeben, und Kopiere von Kachelzuordnungen, die "ungültig" zurückgeben - diese Vorgänge verweisen Kachelspeicherorte in einer Streaming-Ressource auf Speicherorte in Kachelpools oder auf NULL oder auf beide.</span><span class="sxs-lookup"><span data-stu-id="eedb4-106">Update Tile Mappings operations that return void, and Copy Tile Mappings operations that return void - These operations point tile locations in a streaming resource to locations in tile pools, or to NULL, or to both.</span></span> <span data-ttu-id="eedb4-107">Diese Vorgänge können eine getrennte Teilmenge der Kachelverweise aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="eedb4-107">These operations can update a disjoint subset of the tile pointers.</span></span>
-   <span data-ttu-id="eedb4-108">Kopieren und Aktualisieren von Vorgängen - Alle API, die Daten in eine und aus einer Standard-Pooloberfläche kopieren können, arbeiten für Streaming-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="eedb4-108">Copy and Update operations - All the APIs that can copy data to and from a default pool surface work for streaming resources.</span></span> <span data-ttu-id="eedb4-109">Lesen von nicht zugeordneten Kacheln erzeugt 0 und Einträge in nicht zugeordnete Kacheln werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="eedb4-109">Reading from unmapped tiles produces 0 and writes to unmapped tiles are dropped.</span></span>
-   <span data-ttu-id="eedb4-110">Kopieren von Kacheln und Aktualisieren von Kachelvorgängen - diese Vorgänge dienen dem Kopieren von Kacheln mit einer Granularität von 64 KB in eine und aus einer Streaming-Ressource und Puffer-Ressource in einem kanonischen Speicherlayout.</span><span class="sxs-lookup"><span data-stu-id="eedb4-110">Copy Tiles and Update Tiles operations - These operations exist for copying tiles at 64KB granularity to and from any streaming resource and a buffer resource in a canonical memory layout.</span></span> <span data-ttu-id="eedb4-111">Der Bildschirmtreiber und die Hardware durchmischen den Speicher so, wie dies für die Streaming-Ressource erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="eedb4-111">The display driver and hardware perform any memory "swizzling" necessary for the streaming resource.</span></span>
-   <span data-ttu-id="eedb4-112">Direct3D-Rohrbindungen und Anzeigen von Kreationen/Bindungen, die auf Nicht-Streaming-Ressourcen funktionieren, würden auch auf Streaming-Ressourcen funktionieren.</span><span class="sxs-lookup"><span data-stu-id="eedb4-112">Direct3D pipeline bindings and view creations / bindings that would work on non-streaming resources work on streaming resources as well.</span></span>

<span data-ttu-id="eedb4-113">Kachelsteuerelemente sind auf unmittelbare oder verzögerte Kontexte verfügbar (wie Aktualisierungen auf typische Ressourcen) und wirken sich nach der Ausführung auf nachfolgende Zugriffe auf die Kacheln aus (nicht zuvor eingereichte Vorgänge).</span><span class="sxs-lookup"><span data-stu-id="eedb4-113">Tile controls are available on immediate or deferred contexts (just like updates to typical resources) and upon execution impact subsequent accesses to the tiles (not previously submitted operations).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="eedb4-114"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="eedb4-114"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="eedb4-115">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="eedb4-115">Creating streaming resources</span></span>](creating-streaming-resources.md)

 

 




