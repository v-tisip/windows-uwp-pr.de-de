---
title: Ebenen der Features von Streamingressourcen
description: Direct3D unterstützt Streamingressourcen in drei Featureebenen.
ms.assetid: 6AE7EA72-3929-4BB4-8780-F0CF26192D87
keywords:
- Ebenen der Features von Streamingressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c872d289c67161e414671d3d509401f0539a7675
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7983573"
---
# <a name="streaming-resources-features-tiers"></a><span data-ttu-id="612dd-104">Ebenen der Features von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="612dd-104">Streaming resources features tiers</span></span>


<span data-ttu-id="612dd-105">Direct3D unterstützt Streamingressourcen in drei Featureebenen.</span><span class="sxs-lookup"><span data-stu-id="612dd-105">Direct3D supports streaming resources in three tiers of capabilities.</span></span>

<span data-ttu-id="612dd-106">Ebene1 stellt grundlegende Funktionen für Streamingressourcen bereit.</span><span class="sxs-lookup"><span data-stu-id="612dd-106">Tier 1 provides basic capabilities for streaming resources.</span></span>

<span data-ttu-id="612dd-107">Ebene2 fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</span><span class="sxs-lookup"><span data-stu-id="612dd-107">Tier 2 adds capabilities beyond Tier 1, such as guaranteeing non-packed texture mipmap when the size is at least one standard tile shape; shader instructions for clamping level-of-detail (LOD) and for obtaining status about the shader operation; also, reading from NULL-mapped tiles treat that sampled value as zero.</span></span>

<span data-ttu-id="612dd-108">Ebene3 fügt über Ebene2 hinausgehende Texture3D-Funktionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="612dd-108">Tier 3 adds Texture3D capabilities, beyond Tier 2.</span></span>

<span data-ttu-id="612dd-109">In den Versionen von Direct3D sind Abfragefunktionen zum Überprüfen der Hardware und der Treiberunterstützung für Streamingressourcen sowie der Ebene verfügbar.</span><span class="sxs-lookup"><span data-stu-id="612dd-109">Query functions are available in the versions of Direct3D, to validate hardware and driver support for streaming resources, and at what tier level.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="612dd-110"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="612dd-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="612dd-111">Thema</span><span class="sxs-lookup"><span data-stu-id="612dd-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="612dd-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="612dd-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="tier-1.md"><span data-ttu-id="612dd-113">Ebene1</span><span class="sxs-lookup"><span data-stu-id="612dd-113">Tier 1</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="612dd-114">In diesem Abschnitt wird die Unterstützung für die Ebene1 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="612dd-114">This section describes tier 1 support.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="tier-2.md"><span data-ttu-id="612dd-115">Ebene2</span><span class="sxs-lookup"><span data-stu-id="612dd-115">Tier 2</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="612dd-116">Die Unterstützung der Ebene2 für Streamingressourcen fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</span><span class="sxs-lookup"><span data-stu-id="612dd-116">Tier 2 support for streaming resources adds capabilities beyond Tier 1, such as guaranteeing nonpacked texture mipmap when the size is at least one standard tile shape; shader instructions for clamping level-of-detail (LOD) and for obtaining status about the shader operation; also, reading from NULL-mapped tiles treat that sampled value as zero.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="tier-3.md"><span data-ttu-id="612dd-117">Ebene3</span><span class="sxs-lookup"><span data-stu-id="612dd-117">Tier 3</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="612dd-118">Ebene3 fügt zusätzlich zu den Funktionen der <a href="tier-2.md">Ebene2</a> die Unterstützung für Texture3D für Streamingressourcen hinzu.</span><span class="sxs-lookup"><span data-stu-id="612dd-118">Tier 3 adds support for Texture3D for streaming resources, in addition to the <a href="tier-2.md">Tier 2</a> capabilities.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="612dd-119"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="612dd-119"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="612dd-120">Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="612dd-120">Streaming resources</span></span>](streaming-resources.md)

 

 




