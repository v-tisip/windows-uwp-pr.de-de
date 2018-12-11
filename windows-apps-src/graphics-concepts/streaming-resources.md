---
title: Streamingressourcen
description: Streamingressourcen sind große logische Ressourcen, die wenig physischen Speicher belegen. Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt. Streamingressourcen wurden früher als unterteilte Ressourcen bezeichnet.
ms.assetid: 04F0486E-4B71-4073-88DA-2AF505F4F0C1
keywords:
- Streamingressourcen
- Ressourcen, Streaming
- Ressourcen, unterteilte
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c15c8a82219109a96d0a9ca192c4dfff5d86c9aa
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8893006"
---
# <a name="streaming-resources"></a><span data-ttu-id="591f9-108">Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-108">Streaming resources</span></span>


<span data-ttu-id="591f9-109">*Streamingressourcen* sind große logische Ressourcen, die wenig physischen Speicher belegen..</span><span class="sxs-lookup"><span data-stu-id="591f9-109">*Streaming resources* are large logical resources that use small amounts of physical memory.</span></span> <span data-ttu-id="591f9-110">Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt.</span><span class="sxs-lookup"><span data-stu-id="591f9-110">Instead of passing an entire large resource, small parts of the resource are streamed as needed.</span></span> <span data-ttu-id="591f9-111">Streamingressourcen wurden früher als *unterteilte Ressourcen* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="591f9-111">Streaming resources were previously called *tiled resources*.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="591f9-112"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="591f9-112"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="591f9-113">Thema</span><span class="sxs-lookup"><span data-stu-id="591f9-113">Topic</span></span></th>
<th align="left"><span data-ttu-id="591f9-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="591f9-114">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="the-need-for-streaming-resources.md"><span data-ttu-id="591f9-115">Die Notwendigkeit für Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-115">The need for streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="591f9-116">Streamingressourcen sind erforderlich, damit der GPU-Speicher nicht unnötig durch die Speicherung von Oberflächenbereichen belegt wird, auf die nicht zugegriffen wird, und um der Hardware mitzuteilen, wie angrenzende Kacheln gefiltert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="591f9-116">Streaming resources are needed so GPU memory isn't wasted storing regions of surfaces that won't be accessed, and to tell the hardware how to filter across adjacent tiles.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="creating-streaming-resources.md"><span data-ttu-id="591f9-117">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-117">Creating streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="591f9-118">Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource ein Flag festlegen, das die Ressource als Streamingressource kennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="591f9-118">Streaming resources are created by specifying a flag when you create a resource, indicating that the resource is a streaming resource.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="pipeline-access-to-streaming-resources.md"><span data-ttu-id="591f9-119">Pipelinezugriff auf Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-119">Pipeline access to streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="591f9-120">Streamingressourcen können in Shaderressourcenansichten (SRV), Renderzielansichten (RTV), Tiefenschablonenansichten (DSV) und in unsortierten Zugriffsansichten (UAV) sowie in bestimmten Bindungen ohne Ansichten, z.B. Vertex-Pufferbindungen, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="591f9-120">Streaming resources can be used in shader resource views (SRV), render target views (RTV), depth stencil views (DSV) and unordered access views (UAV), as well as some bind points where views aren't used, such as vertex buffer bindings.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resources-features-tiers.md"><span data-ttu-id="591f9-121">Ebenen der Features von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-121">Streaming resources features tiers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="591f9-122">Direct3D unterstützt Streamingressourcen in drei Funktionsebenen.</span><span class="sxs-lookup"><span data-stu-id="591f9-122">Direct3D supports streaming resources in three tiers of capabilities.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="591f9-123"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="591f9-123"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="591f9-124">Lernanleitung für Direct3D-Grafiken</span><span class="sxs-lookup"><span data-stu-id="591f9-124">Direct3D Graphics Learning Guide</span></span>](index.md)

[<span data-ttu-id="591f9-125">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="591f9-125">Resources</span></span>](resources.md)

 

 




