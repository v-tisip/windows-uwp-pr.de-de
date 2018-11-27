---
title: Geräte- und prozessübergreifende Streamingressourcen
description: Kachelpools können mit anderen Prozessen wie herkömmliche Ressourcen geteilt werden. Streamingressourcen, die auf Kachelpools verweisen, können nicht geräte- und prozessübergreifend geteilt werden.
ms.assetid: D035AF4B-D71B-4F20-9A98-7C360BF9B285
keywords:
- Geräte- und prozessübergreifende Streamingressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a0bff43cfd26c43bb5f75f37a66c55e556429470
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7703254"
---
# <a name="span-iddirect3dconceptsstreaming-resource-cross-process-and-device-sharingspanstreaming-resource-cross-process-and-device-sharing"></a><span data-ttu-id="78024-105"><span id="direct3dconcepts.streaming-resource-cross-process-and-device-sharing"></span>Geräte- und prozessübergreifende Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="78024-105"><span id="direct3dconcepts.streaming-resource-cross-process-and-device-sharing"></span>Streaming resource cross-process and device sharing</span></span>


<span data-ttu-id="78024-106">Kachelpools können mit anderen Prozessen wie herkömmliche Ressourcen geteilt werden.</span><span class="sxs-lookup"><span data-stu-id="78024-106">Tile pools can be shared with other processes just like traditional resources.</span></span> <span data-ttu-id="78024-107">Streamingressourcen, die auf Kachelpools verweisen, können nicht geräte- und prozessübergreifend geteilt werden.</span><span class="sxs-lookup"><span data-stu-id="78024-107">Streaming resources that reference tile pools can't be shared across devices and processes.</span></span> <span data-ttu-id="78024-108">Separate Prozesse können aber eigene Streamingressourcen erstellen, die den für diese Streamingressourcen freigegebenen Kachelpools zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="78024-108">But separate processes can create their own streaming resources that map to tile pools that are shared between those streaming resources.</span></span>

<span data-ttu-id="78024-109">Die Größe freigegebener Kachelpools kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="78024-109">Shared tile pools can't be resized.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="78024-110"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="78024-110"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="78024-111">Thema</span><span class="sxs-lookup"><span data-stu-id="78024-111">Topic</span></span></th>
<th align="left"><span data-ttu-id="78024-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78024-112">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="stencil-formats-not-supported-with-streaming-resources.md"><span data-ttu-id="78024-113">Von den Streamingressourcen nicht unterstützte Schablonenformate</span><span class="sxs-lookup"><span data-stu-id="78024-113">Stencil formats not supported with streaming resources</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="78024-114">Formate, die Schablonen enthalten, werden von Streamingressourcen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78024-114">Formats that contain stencil aren't supported with streaming resources.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="78024-115"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="78024-115"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="78024-116">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="78024-116">Creating streaming resources</span></span>](creating-streaming-resources.md)

 

 




