---
title: Tiefen- und Schablonenpuffer
description: Ein Tiefenpuffer speichert Tiefeninformationen. Diese steuern, welche Bereiche von Polygonen dargestellt werden.
ms.assetid: 98B9D73A-04A7-4758-AC27-33CD4CB24216
keywords:
- Tiefen- und Schablonenpuffer
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e292e0c992edb26da2a92885e1f949d254d75da6
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6252794"
---
# <a name="depth-and-stencil-buffers"></a><span data-ttu-id="70f1c-104">Tiefen- und Schablonenpuffer</span><span class="sxs-lookup"><span data-stu-id="70f1c-104">Depth and stencil buffers</span></span>


<span data-ttu-id="70f1c-105">Ein *Tiefenpuffer* speichert Tiefeninformationen. Diese steuern, welche Bereiche von Polygonen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="70f1c-105">A *depth buffer* stores depth information to control which areas of polygons are rendered rather than hidden from view.</span></span> <span data-ttu-id="70f1c-106">Ein *Schablonenpuffer* wird Maskieren von Pixeln in einem Bild verwendet. So können Spezialeffekte erstellt werden (z. B. Stanzeffekte; Decaling; Transparenzen, Ausblenden und Verwischen; Außenlinien und Silhouetten und zweiseitige Schablonen).</span><span class="sxs-lookup"><span data-stu-id="70f1c-106">A *stencil buffer* is used to mask pixels in an image, to produce special effects, including compositing; decaling; dissolves, fades, and swipes; outlines and silhouettes; and two-sided stencil.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="70f1c-107"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="70f1c-107"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="70f1c-108">Thema</span><span class="sxs-lookup"><span data-stu-id="70f1c-108">Topic</span></span></th>
<th align="left"><span data-ttu-id="70f1c-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="70f1c-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="depth-buffers.md"><span data-ttu-id="70f1c-110">Tiefenpuffer</span><span class="sxs-lookup"><span data-stu-id="70f1c-110">Depth buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="70f1c-111">Ein <em>Tiefenpuffer</em> oder <em>Z-Puffer</em> speichert Tiefeninformationen. Diese steuern, welche Bereiche von Polygonen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="70f1c-111">A <em>depth buffer</em>, or <em>z-buffer</em>, stores depth information to control which areas of polygons are rendered rather than hidden from view.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="stencil-buffers.md"><span data-ttu-id="70f1c-112">Schablonenpuffer</span><span class="sxs-lookup"><span data-stu-id="70f1c-112">Stencil buffers</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="70f1c-113">Ein <em>Schablonenpuffer</em> wird verwendet, um die Pixel in einem Bild zu maskieren und Spezialeffekte zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="70f1c-113">A <em>stencil buffer</em> is used to mask pixels in an image, to produce special effects.</span></span> <span data-ttu-id="70f1c-114">Die Maske steuert, ob das Pixel gezeichnet wird oder nicht.</span><span class="sxs-lookup"><span data-stu-id="70f1c-114">The mask controls whether the pixel is drawn or not.</span></span> <span data-ttu-id="70f1c-115">Diese Spezialeffekte umfassen Stanzeffekte; Decaling; Transparenzen, Ausblenden und Verwischen; Außenlinien und Silhouetten und zweiseitige Schablonen.</span><span class="sxs-lookup"><span data-stu-id="70f1c-115">These special effects include compositing; decaling; dissolves, fades, and swipes; outlines and silhouettes; and two-sided stencil.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="70f1c-116"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="70f1c-116"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="70f1c-117">Direct3D-Grafik-Lernanleitung</span><span class="sxs-lookup"><span data-stu-id="70f1c-117">Direct3D Graphics Learning Guide</span></span>](index.md)

 

 




