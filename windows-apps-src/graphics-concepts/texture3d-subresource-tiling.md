---
title: Unterteilung von Texture3D-Unterressourcen
description: Diese Tabelle zeigt die Unterteilung von Texture3D-Unterressourcen.
ms.assetid: 210D03E4-CF12-47E0-BA2F-C8D059B17D3E
keywords:
- Unterteilung von Texture3D-Unterressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c9c232bc60bbbb3cccc16618d82ec23452c58ee8
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8709564"
---
# <a name="texture3d-subresource-tiling"></a><span data-ttu-id="9a6ce-104">Unterteilung von Texture3D-Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="9a6ce-104">Texture3D subresource tiling</span></span>


<span data-ttu-id="9a6ce-105">Diese Tabelle zeigt die Unterteilung von [**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562)-Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-105">This table shows how [**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562) subresources are tiled.</span></span> <span data-ttu-id="9a6ce-106">Die Werte in dieser Tabelle berücksichtigen keine Tail-MIP-Verpackungen.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-106">The values in this table don't count tail mip packing.</span></span>

<span data-ttu-id="9a6ce-107">Diese Tabelle nimmt die [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)-Unterteilung und dividiert die x/y-Dimensionen jeweils durch 4 und fügt 16 Tiefenebenen hinzu.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-107">This table takes the [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) tiling and divides the x/y dimensions by 4 each and adds 16 layers of depth.</span></span> <span data-ttu-id="9a6ce-108">Alle Kacheln für die erste Ebene (2D-Kachelebene, die die ersten 16 Tiefenebenen definiert) erscheinen vor allen folgenden Ebenen.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-108">All the tiles for the first plane (2D plane of tiles defining the first 16 layers of depth) appear before the subsequent planes.</span></span>

<span data-ttu-id="9a6ce-109">**Hinweis:** [**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562) -Unterstützung in Streamingressourcen ist in der ursprünglichen Implementierung der streaming-Ressourcen verfügbar, aber die gewünschten kachelformen werden hier aufgeführt, in einer zukünftigen Version möglicherweise unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-109">**Note**[**Texture3D**](https://msdn.microsoft.com/library/windows/desktop/ff471562) support in streaming resources isn't exposed in the initial implementation of streaming resources, but the desired tile shapes are listed here for possible support in a future release.</span></span>

 

| <span data-ttu-id="9a6ce-110">Bits/Pixel (1Sample/Pixel)</span><span class="sxs-lookup"><span data-stu-id="9a6ce-110">Bits/Pixel (1 sample/pixel)</span></span> | <span data-ttu-id="9a6ce-111">Kachelabmessungen (Pixel, B x H x T)</span><span class="sxs-lookup"><span data-stu-id="9a6ce-111">Tile Dimensions (Pixels, WxHxD)</span></span> |
|-----------------------------|---------------------------------|
| <span data-ttu-id="9a6ce-112">8</span><span class="sxs-lookup"><span data-stu-id="9a6ce-112">8</span></span>                           | <span data-ttu-id="9a6ce-113">64 x 32 x 32</span><span class="sxs-lookup"><span data-stu-id="9a6ce-113">64x32x32</span></span>                        |
| <span data-ttu-id="9a6ce-114">16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-114">16</span></span>                          | <span data-ttu-id="9a6ce-115">32 x 32 x 32</span><span class="sxs-lookup"><span data-stu-id="9a6ce-115">32x32x32</span></span>                        |
| <span data-ttu-id="9a6ce-116">32</span><span class="sxs-lookup"><span data-stu-id="9a6ce-116">32</span></span>                          | <span data-ttu-id="9a6ce-117">32 x 32 x 16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-117">32x32x16</span></span>                        |
| <span data-ttu-id="9a6ce-118">64</span><span class="sxs-lookup"><span data-stu-id="9a6ce-118">64</span></span>                          | <span data-ttu-id="9a6ce-119">32 x 16 x 16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-119">32x16x16</span></span>                        |
| <span data-ttu-id="9a6ce-120">128</span><span class="sxs-lookup"><span data-stu-id="9a6ce-120">128</span></span>                         | <span data-ttu-id="9a6ce-121">16 x 16 x 16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-121">16x16x16</span></span>                        |
| <span data-ttu-id="9a6ce-122">BC1, 4</span><span class="sxs-lookup"><span data-stu-id="9a6ce-122">BC1,4</span></span>                       | <span data-ttu-id="9a6ce-123">128 x 64 x 16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-123">128x64x16</span></span>                       |
| <span data-ttu-id="9a6ce-124">BC2, 3, 5, 6, 7</span><span class="sxs-lookup"><span data-stu-id="9a6ce-124">BC2,3,5,6,7</span></span>                 | <span data-ttu-id="9a6ce-125">64 x 64 x 16</span><span class="sxs-lookup"><span data-stu-id="9a6ce-125">64x64x16</span></span>                        |

 

<span data-ttu-id="9a6ce-126">Format-Bitanzahlen, die bei Streamingressourcen nicht unterstützt werden, sind 96-bpp-Formate, Videoformate, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span><span class="sxs-lookup"><span data-stu-id="9a6ce-126">Format bit counts not supported with streaming resources are 96 bpp formats, video formats, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="9a6ce-127"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9a6ce-127"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="9a6ce-128">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="9a6ce-128">How a streaming resource's area is tiled</span></span>](how-a-streaming-resource-s-area-is-tiled.md)

 

 




