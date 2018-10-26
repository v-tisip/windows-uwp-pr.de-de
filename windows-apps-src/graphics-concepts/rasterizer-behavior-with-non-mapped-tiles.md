---
title: Rasterizerverhalten bei nicht zugeordneten Kacheln
description: Dieser Abschnittbeschreibt Rasterizerverhalten bei nicht zugeordneten Kacheln.
ms.assetid: AC7B818D-E52B-4727-AEA2-39CFDC279CE7
keywords:
- Rasterizerverhalten bei nicht zugeordneten Kacheln
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: f56e8051c8a66cf579a7c3dbcddc738b3a10bcaf
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5562420"
---
# <a name="span-iddirect3dconceptsrasterizerbehaviorwithnon-mappedtilesspanrasterizer-behavior-with-non-mapped-tiles"></a><span data-ttu-id="6ece6-104"><span id="direct3dconcepts.rasterizer_behavior_with_non-mapped_tiles"></span>Rasterizerverhalten bei nicht zugeordneten Kacheln</span><span class="sxs-lookup"><span data-stu-id="6ece6-104"><span id="direct3dconcepts.rasterizer_behavior_with_non-mapped_tiles"></span>Rasterizer behavior with non-mapped tiles</span></span>


<span data-ttu-id="6ece6-105">Dieser Abschnittbeschreibt Rasterizerverhalten bei nicht zugeordneten Kacheln.</span><span class="sxs-lookup"><span data-stu-id="6ece6-105">This section describes rasterizer behavior with non-mapped tiles.</span></span>

## <a name="span-iddepthstencilviewspanspan-iddepthstencilviewspanspan-iddepthstencilviewspandepthstencilview"></a><span data-ttu-id="6ece6-106"><span id="DepthStencilView"></span><span id="depthstencilview"></span><span id="DEPTHSTENCILVIEW"></span>DepthStencilView</span><span class="sxs-lookup"><span data-stu-id="6ece6-106"><span id="DepthStencilView"></span><span id="depthstencilview"></span><span id="DEPTHSTENCILVIEW"></span>DepthStencilView</span></span>


<span data-ttu-id="6ece6-107">Verhalten der DSV-Lese- und Schreibvorgänge (Depth Stencil View) hängt von der Ebene der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="6ece6-107">Behavior of depth stencil view (DSV) reads and writes depends on the level of hardware support.</span></span> <span data-ttu-id="6ece6-108">Eine Aufschlüsselung der Anforderungen finden Sie im Thema zum allgemeinen Lese- und Schreibverhalten unter [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="6ece6-108">For a breakdown of requirements, see overall read and write behavior for [Streaming resources features tiers](streaming-resources-features-tiers.md).</span></span>

<span data-ttu-id="6ece6-109">Hier ist das ideale Verhalten:</span><span class="sxs-lookup"><span data-stu-id="6ece6-109">Here is the ideal behavior:</span></span>

<span data-ttu-id="6ece6-110">Wenn eine Kachel in der DepthStencilView-Ansicht nicht zugeordnet wird, ist der Rückgabewert aus dem Lesen der Tiefe 0, der dann in die Vorgänge, die für den Tiefenlesewert konfiguriert sind, übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="6ece6-110">If a tile isn't mapped in the DepthStencilView, the return value from reading depth is 0, which is then fed into whatever operations are configured for the depth read value.</span></span> <span data-ttu-id="6ece6-111">Schreibvorgänge in die fehlende Tiefenkachel werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="6ece6-111">Writes to the missing depth tile are dropped.</span></span> <span data-ttu-id="6ece6-112">Diese ideale Definition für die Behandlung von Schreibvorgängen ist für [Ebene 2](tier-2.md) nicht erforderlich. Schreibvorgänge an nicht zugeordnete Kacheln können zu einem Cache führen, den nachfolgende Lesevorgänge aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="6ece6-112">This ideal definition for write handling is not required by [Tier 2](tier-2.md); writes to non-mapped tiles can end up in a cache that subsequent reads could pick up.</span></span>

## <a name="span-idrendertargetviewspanspan-idrendertargetviewspanspan-idrendertargetviewspanrendertargetview"></a><span data-ttu-id="6ece6-113"><span id="RenderTargetView"></span><span id="rendertargetview"></span><span id="RENDERTARGETVIEW"></span>RenderTargetView</span><span class="sxs-lookup"><span data-stu-id="6ece6-113"><span id="RenderTargetView"></span><span id="rendertargetview"></span><span id="RENDERTARGETVIEW"></span>RenderTargetView</span></span>


<span data-ttu-id="6ece6-114">Verhalten der RTV-Lese- und Schreibvorgänge (Render Target View, Renderzielansicht) hängt von der Ebene der Hardwareunterstützung ab.</span><span class="sxs-lookup"><span data-stu-id="6ece6-114">Behavior of render target view (RTV) reads and writes depends on the level of hardware support.</span></span> <span data-ttu-id="6ece6-115">Eine Aufschlüsselung der Anforderungen finden Sie im Thema zum allgemeinen Lese- und Schreibverhalten unter [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="6ece6-115">For a breakdown of requirements, see overall read and write behavior for [Streaming resources features tiers](streaming-resources-features-tiers.md).</span></span>

<span data-ttu-id="6ece6-116">Für alle Implementierungen können verschiedene RTVs (und DSVs), die gleichzeitig gebunden werden, verschiedene zugeordnete und nicht zugeordnete Bereiche sowie Oberflächenformate unterschiedlicher Größen (was unterschiedliche Kachelformen bedeutet) aufweisen.</span><span class="sxs-lookup"><span data-stu-id="6ece6-116">On all implementations, different RTVs (and DSV) bound simultaneously can have different areas mapped versus non-mapped and can have different sized surface formats (which means different tile shapes).</span></span>

<span data-ttu-id="6ece6-117">Hier ist das ideale Verhalten:</span><span class="sxs-lookup"><span data-stu-id="6ece6-117">Here is the ideal behavior:</span></span>

<span data-ttu-id="6ece6-118">Lesevorgänge aus RTVs geben 0 für fehlende Kacheln zurück, und Schreibvorgänge werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="6ece6-118">Reads from RTVs return 0 in missing tiles and writes are dropped.</span></span> <span data-ttu-id="6ece6-119">Diese ideale Definition für die Behandlung von Schreibvorgängen ist für [Ebene 2](tier-2.md) nicht erforderlich. Schreibvorgänge an nicht zugeordnete Kacheln können zu einem Cache führen, den nachfolgende Lesevorgänge aufnehmen können.</span><span class="sxs-lookup"><span data-stu-id="6ece6-119">This ideal definition for write handling is not required by [Tier 2](tier-2.md); writes to non-mapped tiles can end up in a cache that subsequent reads could pick up.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6ece6-120"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6ece6-120"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6ece6-121">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="6ece6-121">Pipeline access to streaming resources</span></span>](pipeline-access-to-streaming-resources.md)

 

 




