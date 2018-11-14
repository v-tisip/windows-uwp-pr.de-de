---
title: So strukturieren Sie den Bereich einer Streamingressource
description: Wenn Sie eine Streamingressource erstellen, bestimmen die Dimensionen, die Formatelementgröße und die Anzahl der Mipmaps und/oder Array-Slices (falls zutreffend) die Anzahl der Tiles, die erforderlich sind, um die gesamte Oberfläche darzustellen.
ms.assetid: 3485FD8D-2A06-4B0A-8810-ECF37736F94B
keywords:
- So strukturieren Sie den Bereich einer Streamingressource
- Ressourcenbereich, strukturiert
- Größentabellen, Ressourcen, strukturiert
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 49ad096389c27fb65970424569c7c1d2ea0cb097
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6183535"
---
# <a name="how-a-streaming-resources-area-is-tiled"></a><span data-ttu-id="830f3-106">So strukturieren Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="830f3-106">How a streaming resource's area is tiled</span></span>


<span data-ttu-id="830f3-107">Wenn Sie eine Streamingressource erstellen, bestimmen die Dimensionen, die Formatelementgröße und die Anzahl der Mipmaps und/oder Array-Slices (falls zutreffend) die Anzahl der Tiles, die erforderlich sind, um die gesamte Oberfläche darzustellen.</span><span class="sxs-lookup"><span data-stu-id="830f3-107">When you create a streaming resource, the dimensions, format element size, and number of mipmaps and/or array slices (if applicable) determine the number of tiles that are required to back the entire surface area.</span></span> <span data-ttu-id="830f3-108">Das Pixel/Byte-Layout in den Tiles wird durch die Implementierung bestimmt.</span><span class="sxs-lookup"><span data-stu-id="830f3-108">The pixel/byte layout within tiles is determined by the implementation.</span></span> <span data-ttu-id="830f3-109">Die Anzahl von Pixeln, die in eine Tile passen, ist je nach Formatelementgröße konstant und identisch, ob Sie einen standardmäßigen Swizzle verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="830f3-109">The number of pixels that fit in a tile, depending on the format element size, is fixed and identical whether you use a standard swizzle or not.</span></span>

<span data-ttu-id="830f3-110">Die Anzahl von Tiles, die bei einer bestimmten Oberflächengröße und Formatelementbreite verwendet wird, ist klar definiert und kann den Tabellen in den folgenden Abschnitten entnommen werden.</span><span class="sxs-lookup"><span data-stu-id="830f3-110">The number of tiles that will be used by a given surface size and format element width is well defined and predictable based on the tables in the following sections.</span></span> <span data-ttu-id="830f3-111">Für Ressourcen, die Mipmaps enthalten, oder für Fälle, in denen eine Tile nicht von der Oberfläche ausgefüllt wird, gelten einige Einschränkungen. Informationen dazu finden Sie unter [Mipmap-Verpackung](mipmap-packing.md).</span><span class="sxs-lookup"><span data-stu-id="830f3-111">For resources that contain mipmaps or cases where surface dimensions don't fill a tile, some constraints exist; see [Mipmap packing](mipmap-packing.md).</span></span>

<span data-ttu-id="830f3-112">Verschiedene Streamingressourcen dürfen auf identische Speicher mit verschiedenen Formaten zeigen, solange sich Anwendungen nicht auf die Ergebnisse verlassen, wenn in einen Speicher mit einem Format geschrieben und mit einem anderen gelesen wird</span><span class="sxs-lookup"><span data-stu-id="830f3-112">Different streaming resources can point to identical memory with different formats as long as applications don't rely on the results of writing to the memory with one format and reading with another.</span></span> <span data-ttu-id="830f3-113">Anwendungen können sich jedoch auf die Ergebnisse verlassen, wenn in einen Speicher mit einem Format geschrieben und mit einem anderen gelesen wird, sofern die Formate zu derselben Formatfamilie gehören (also dasselbe typlose übergeordnete Format besitzen).</span><span class="sxs-lookup"><span data-stu-id="830f3-113">But applications can rely on the results of writing to the memory with one format and reading with another if the formats are in the same format family (that is, they have the same typeless parent format).</span></span> <span data-ttu-id="830f3-114">Beispielsweise sind DXGI\_FORMAT\_R8G8B8A8\_UNORM und DXGI\_FORMAT\_R8G8B8A8\_UINT untereinander kompatible, aber nicht mit DXGI\_FORMAT\_R16G16\_UNORM.</span><span class="sxs-lookup"><span data-stu-id="830f3-114">For example, DXGI\_FORMAT\_R8G8B8A8\_UNORM and DXGI\_FORMAT\_R8G8B8A8\_UINT are compatible with each other but not with DXGI\_FORMAT\_R16G16\_UNORM.</span></span>

<span data-ttu-id="830f3-115">Eine Ausnahme sind definierte Übergänge von Daten von einem Format in ein anderes: Wenn die Bits einer Tile alle den Wert 0 haben, kann die Tile mit jedem Format verwendet werden, das diese Speicherinhalte als 0 interpretiert (unabhängig vom Speicherlayout).</span><span class="sxs-lookup"><span data-stu-id="830f3-115">An exception is where bleeding data from one format aliasing to another is well defined: if a tile completely contains 0 for all its bits, that tile can be used with any format that interprets those memory contents as 0 (regardless of memory layout).</span></span> <span data-ttu-id="830f3-116">Somit kann ein Tile-Inhalt, der mit dem Format DXGI\_FORMAT\_R8\_UNORM auf 0x00 gesetzt (gelöscht) wurde, mit einem Format wie DXGI\_FORMAT\_R32G32\_FLOAT verwendet werden, und der Inhalt scheint weiterhin (0.0f,0.0f) zu sein.</span><span class="sxs-lookup"><span data-stu-id="830f3-116">So, a tile could be cleared to 0x00 with the format DXGI\_FORMAT\_R8\_UNORM and then used with a format like DXGI\_FORMAT\_R32G32\_FLOAT and it would appear the contents are still (0.0f,0.0f).</span></span>

<span data-ttu-id="830f3-117">Das Layout der Daten in einer Tile ist nicht davon abhängig, wo sie in eine Ressource zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="830f3-117">The layout of data within a tile doesn't depend on where the tile is mapped in a resource overall.</span></span> <span data-ttu-id="830f3-118">Daher kann eine Tile beispielsweise gleichzeitig und mit einheitlichem Verhalten an verschiedenen Positionen einer Oberfläche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="830f3-118">So, for example, a tile can be reused in different locations of a surface at once with consistent behavior in all locations.</span></span>

## <a name="span-idin-this-sectionspanin-this-section"></a><span data-ttu-id="830f3-119"><span id="in-this-section"></span>Inhalt dieses Abschnitts</span><span class="sxs-lookup"><span data-stu-id="830f3-119"><span id="in-this-section"></span>In this section</span></span>


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="830f3-120">Thema</span><span class="sxs-lookup"><span data-stu-id="830f3-120">Topic</span></span></th>
<th align="left"><span data-ttu-id="830f3-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="830f3-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="texture2d-and-texture2darray-subresource-tiling.md"><span data-ttu-id="830f3-122">Strukturierung von Texture2D- und Texture2DArray-Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="830f3-122">Texture2D and Texture2DArray subresource tiling</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="830f3-123">Diese Tabellen zeigen die Unterteilung von <a href="https://msdn.microsoft.com/library/windows/desktop/ff471525"><strong>Texture2D</strong></a>- und <a href="https://msdn.microsoft.com/library/windows/desktop/ff471526"><strong>Texture2DArray</strong></a>-Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="830f3-123">These tables show how <a href="https://msdn.microsoft.com/library/windows/desktop/ff471525"><strong>Texture2D</strong></a> and <a href="https://msdn.microsoft.com/library/windows/desktop/ff471526"><strong>Texture2DArray</strong></a> subresources are tiled.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture3d-subresource-tiling.md"><span data-ttu-id="830f3-124">Unterteilung von Texture3D-Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="830f3-124">Texture3D subresource tiling</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="830f3-125">Diese Tabelle zeigt die Unterteilung von <a href="https://msdn.microsoft.com/library/windows/desktop/ff471562"><strong>Texture3D</strong></a>-Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="830f3-125">This table shows how <a href="https://msdn.microsoft.com/library/windows/desktop/ff471562"><strong>Texture3D</strong></a> subresources are tiled.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="buffer-tiling.md"><span data-ttu-id="830f3-126">Pufferaufteilung</span><span class="sxs-lookup"><span data-stu-id="830f3-126">Buffer tiling</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="830f3-127">Eine <a href="introduction-to-buffers.md">Puffer</a>-Ressource ist in 64KB große Tiles unterteilt, mit Leerraum in der letzten Tile, wenn die Größe kein Vielfaches von 64KB ist.</span><span class="sxs-lookup"><span data-stu-id="830f3-127">A <a href="introduction-to-buffers.md">Buffer</a> resource is divided into 64KB tiles, with some empty space in the last tile if the size is not a multiple of 64KB.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="mipmap-packing.md"><span data-ttu-id="830f3-128">Mipmap-Verpackung</span><span class="sxs-lookup"><span data-stu-id="830f3-128">Mipmap packing</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="830f3-129">Eine Anzahl von Mips (pro Array-Slice) kann in eine Anzahl von Tiles verpackt werden, je nach den Dimensionen der Streamingressource, dem Format, der Anzahl der Mipmaps und der Array-Slices.</span><span class="sxs-lookup"><span data-stu-id="830f3-129">Some number of mips (per array slice) can be packed into some number of tiles, depending on a streaming resource's dimensions, format, number of mipmaps, and array slices.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="830f3-130"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="830f3-130"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="830f3-131">Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="830f3-131">Creating streaming resources</span></span>](creating-streaming-resources.md)

 

 




