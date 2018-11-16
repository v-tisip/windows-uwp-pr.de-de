---
title: Ebenen der Features von Streamingressourcen
description: Direct3D unterstützt Streamingressourcen in drei Featureebenen.
ms.assetid: 6AE7EA72-3929-4BB4-8780-F0CF26192D87
keywords:
- Ebenen der Features von Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: bc7d04a826bd8be0947e8d84ab8dbff6f67e8027
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6993748"
---
# <a name="streaming-resources-features-tiers"></a><span data-ttu-id="e4265-104">Ebenen der Features von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e4265-104">Streaming resources features tiers</span></span>


<span data-ttu-id="e4265-105">Direct3D unterstützt Streamingressourcen in drei Featureebenen.</span><span class="sxs-lookup"><span data-stu-id="e4265-105">Direct3D supports streaming resources in three tiers of capabilities.</span></span>

<span data-ttu-id="e4265-106">Ebene1 stellt grundlegende Funktionen für Streamingressourcen bereit.</span><span class="sxs-lookup"><span data-stu-id="e4265-106">Tier 1 provides basic capabilities for streaming resources.</span></span>

<span data-ttu-id="e4265-107">Ebene2 fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</span><span class="sxs-lookup"><span data-stu-id="e4265-107">Tier 2 adds capabilities beyond Tier 1, such as guaranteeing non-packed texture mipmap when the size is at least one standard tile shape; shader instructions for clamping level-of-detail (LOD) and for obtaining status about the shader operation; also, reading from NULL-mapped tiles treat that sampled value as zero.</span></span>

<span data-ttu-id="e4265-108">Ebene3 fügt über Ebene2 hinausgehende Texture3D-Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="e4265-108">Tier 3 adds Texture3D capabilities, beyond Tier 2.</span></span>

<span data-ttu-id="e4265-109">In den Versionen von Direct3D sind Abfragefunktionen zum Überprüfen der Hardware und der Treiberunterstützung für Streamingressourcen sowie der Ebene verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e4265-109">Query functions are available in the versions of Direct3D, to validate hardware and driver support for streaming resources, and at what tier level.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="e4265-110"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="e4265-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e4265-111">Thema</span><span class="sxs-lookup"><span data-stu-id="e4265-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="e4265-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e4265-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="tier-1.md"><span data-ttu-id="e4265-113">Ebene1</span><span class="sxs-lookup"><span data-stu-id="e4265-113">Tier 1</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="e4265-114">In diesem Abschnitt wird die Unterstützung für die Ebene1 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e4265-114">This section describes tier 1 support.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="tier-2.md"><span data-ttu-id="e4265-115">Ebene2</span><span class="sxs-lookup"><span data-stu-id="e4265-115">Tier 2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="e4265-116">Die Unterstützung der Ebene2 für Streamingressourcen fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</span><span class="sxs-lookup"><span data-stu-id="e4265-116">Tier 2 support for streaming resources adds capabilities beyond Tier 1, such as guaranteeing nonpacked texture mipmap when the size is at least one standard tile shape; shader instructions for clamping level-of-detail (LOD) and for obtaining status about the shader operation; also, reading from NULL-mapped tiles treat that sampled value as zero.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="tier-3.md"><span data-ttu-id="e4265-117">Ebene3</span><span class="sxs-lookup"><span data-stu-id="e4265-117">Tier 3</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="e4265-118">Ebene3 fügt zusätzlich zu den Funktionen der <a href="tier-2.md">Ebene2</a> die Unterstützung für Texture3D für Streamingressourcen hinzu.</span><span class="sxs-lookup"><span data-stu-id="e4265-118">Tier 3 adds support for Texture3D for streaming resources, in addition to the <a href="tier-2.md">Tier 2</a> capabilities.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e4265-119"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e4265-119"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e4265-120">Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="e4265-120">Streaming resources</span></span>](streaming-resources.md)

 

 




