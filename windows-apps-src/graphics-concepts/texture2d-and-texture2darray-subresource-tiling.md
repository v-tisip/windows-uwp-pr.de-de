---
title: Unterteilung von Texture2D- und Texture2DArray-Unterressourcen
description: Diese Tabellen zeigen die Unterteilung von Texture2D- und Texture2DArray-Unterressourcen.
ms.assetid: 2DC14DFC-5299-44D9-895F-5A223D3FD530
keywords:
- Unterteilung von Texture2D- und Texture2DArray-Unterressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 2175ce19824068a850ff70340b467f09e5c76540
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7966400"
---
# <a name="texture2d-and-texture2darray-subresource-tiling"></a><span data-ttu-id="40a62-104">Unterteilung von Texture2D- und Texture2DArray-Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="40a62-104">Texture2D and Texture2DArray subresource tiling</span></span>


<span data-ttu-id="40a62-105">Diese Tabellen zeigen die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="40a62-105">These tables show how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources are tiled.</span></span> <span data-ttu-id="40a62-106">Die Werte in dieser Tabelle beziehen keine Tail-MIP-Verpackung mit ein.</span><span class="sxs-lookup"><span data-stu-id="40a62-106">The values in these tables don't count tail mip packing.</span></span>

## <a name="span-idsubresources-with-multisample-counts-of-1spanspan-idsubresources-with-multisample-counts-of-1spanspan-idsubresources-with-multisample-counts-of-1spansubresources-with-multisample-counts-of-1"></a><span data-ttu-id="40a62-107"><span id="Subresources-with-multisample-counts-of-1"></span><span id="subresources-with-multisample-counts-of-1"></span><span id="SUBRESOURCES-WITH-MULTISAMPLE-COUNTS-OF-1"></span>Unterressourcen mit Multisampling (1)</span><span class="sxs-lookup"><span data-stu-id="40a62-107"><span id="Subresources-with-multisample-counts-of-1"></span><span id="subresources-with-multisample-counts-of-1"></span><span id="SUBRESOURCES-WITH-MULTISAMPLE-COUNTS-OF-1"></span>Subresources with multisample counts of 1</span></span>


<span data-ttu-id="40a62-108">Die folgende Tabelle zeigt die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen mit Multisampling (1).</span><span class="sxs-lookup"><span data-stu-id="40a62-108">This table shows how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources with multisample counts of 1 are tiled.</span></span>

| <span data-ttu-id="40a62-109">Bits/Pixel (1Beispiel/Pixel)</span><span class="sxs-lookup"><span data-stu-id="40a62-109">Bits/Pixel (1 sample/pixel)</span></span> | <span data-ttu-id="40a62-110">Kachelabmessungen (Pixel, B x H)</span><span class="sxs-lookup"><span data-stu-id="40a62-110">Tile Dimensions (Pixels, WxH)</span></span> |
|-----------------------------|-------------------------------|
| <span data-ttu-id="40a62-111">8</span><span class="sxs-lookup"><span data-stu-id="40a62-111">8</span></span>                           | <span data-ttu-id="40a62-112">256 x 256</span><span class="sxs-lookup"><span data-stu-id="40a62-112">256x256</span></span>                       |
| <span data-ttu-id="40a62-113">16</span><span class="sxs-lookup"><span data-stu-id="40a62-113">16</span></span>                          | <span data-ttu-id="40a62-114">256 x 128</span><span class="sxs-lookup"><span data-stu-id="40a62-114">256x128</span></span>                       |
| <span data-ttu-id="40a62-115">32</span><span class="sxs-lookup"><span data-stu-id="40a62-115">32</span></span>                          | <span data-ttu-id="40a62-116">128 x 128</span><span class="sxs-lookup"><span data-stu-id="40a62-116">128x128</span></span>                       |
| <span data-ttu-id="40a62-117">64</span><span class="sxs-lookup"><span data-stu-id="40a62-117">64</span></span>                          | <span data-ttu-id="40a62-118">128 x 64</span><span class="sxs-lookup"><span data-stu-id="40a62-118">128x64</span></span>                        |
| <span data-ttu-id="40a62-119">128</span><span class="sxs-lookup"><span data-stu-id="40a62-119">128</span></span>                         | <span data-ttu-id="40a62-120">64 x 64</span><span class="sxs-lookup"><span data-stu-id="40a62-120">64x64</span></span>                         |
| <span data-ttu-id="40a62-121">BC1, 4</span><span class="sxs-lookup"><span data-stu-id="40a62-121">BC1,4</span></span>                       | <span data-ttu-id="40a62-122">512 x 256</span><span class="sxs-lookup"><span data-stu-id="40a62-122">512x256</span></span>                       |
| <span data-ttu-id="40a62-123">BC2, 3, 5, 6, 7</span><span class="sxs-lookup"><span data-stu-id="40a62-123">BC2,3,5,6,7</span></span>                 | <span data-ttu-id="40a62-124">256 x 256</span><span class="sxs-lookup"><span data-stu-id="40a62-124">256x256</span></span>                       |

 

<span data-ttu-id="40a62-125">Format-Bitanzahlen, die bei Streamingressourcen nicht unterstützt werden, sind 96-bpp-Formate, Videoformate, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span><span class="sxs-lookup"><span data-stu-id="40a62-125">Format bit counts not supported with streaming resources are 96 bpp formats, video formats, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span></span>

## <a name="span-idsubresources-with-various-multisample-countsspanspan-idsubresources-with-various-multisample-countsspanspan-idsubresources-with-various-multisample-countsspansubresources-with-various-multisample-counts"></a><span data-ttu-id="40a62-126"><span id="Subresources-with-various-multisample-counts"></span><span id="subresources-with-various-multisample-counts"></span><span id="SUBRESOURCES-WITH-VARIOUS-MULTISAMPLE-COUNTS"></span>Unterressourcen mit verschiedenen Multisampling-Anzahlen</span><span class="sxs-lookup"><span data-stu-id="40a62-126"><span id="Subresources-with-various-multisample-counts"></span><span id="subresources-with-various-multisample-counts"></span><span id="SUBRESOURCES-WITH-VARIOUS-MULTISAMPLE-COUNTS"></span>Subresources with various multisample counts</span></span>


<span data-ttu-id="40a62-127">Die folgende Tabelle zeigt die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen mit verschiedenen Multisampling-Anzahlen.</span><span class="sxs-lookup"><span data-stu-id="40a62-127">This table shows how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources with various multisample counts are tiled.</span></span>

| <span data-ttu-id="40a62-128">Bits/Pixel (1Beispiel/Pixel)</span><span class="sxs-lookup"><span data-stu-id="40a62-128">Bits/Pixel (1 sample/pixel)</span></span> | <span data-ttu-id="40a62-129">Kachelabmessungen (Pixel, B x H)</span><span class="sxs-lookup"><span data-stu-id="40a62-129">Tile Dimensions (Pixels, WxH)</span></span> |
|-----------------------------|-------------------------------|
| <span data-ttu-id="40a62-130">1</span><span class="sxs-lookup"><span data-stu-id="40a62-130">1</span></span>                           | <span data-ttu-id="40a62-131">1 x 1</span><span class="sxs-lookup"><span data-stu-id="40a62-131">1x1</span></span>                           |
| <span data-ttu-id="40a62-132">2</span><span class="sxs-lookup"><span data-stu-id="40a62-132">2</span></span>                           | <span data-ttu-id="40a62-133">2 x 1</span><span class="sxs-lookup"><span data-stu-id="40a62-133">2x1</span></span>                           |
| <span data-ttu-id="40a62-134">4</span><span class="sxs-lookup"><span data-stu-id="40a62-134">4</span></span>                           | <span data-ttu-id="40a62-135">2 x 2</span><span class="sxs-lookup"><span data-stu-id="40a62-135">2x2</span></span>                           |
| <span data-ttu-id="40a62-136">8</span><span class="sxs-lookup"><span data-stu-id="40a62-136">8</span></span>                           | <span data-ttu-id="40a62-137">4 x 2</span><span class="sxs-lookup"><span data-stu-id="40a62-137">4x2</span></span>                           |
| <span data-ttu-id="40a62-138">16</span><span class="sxs-lookup"><span data-stu-id="40a62-138">16</span></span>                          | <span data-ttu-id="40a62-139">4 x 4</span><span class="sxs-lookup"><span data-stu-id="40a62-139">4x4</span></span>                           |

 

<span data-ttu-id="40a62-140">Es sind ausschließlich Beispielanzahlen von 1 und 4 erforderlich (und zulässig), um mit Streamingressourcen unterstützt zu werden.</span><span class="sxs-lookup"><span data-stu-id="40a62-140">Only sample counts 1 and 4 are required (and allowed) to be supported with streaming resources.</span></span> <span data-ttu-id="40a62-141">Anzahlen von 2, 8 und 16 werden derzeit von Streamingressourcen nicht unterstützt, auch wenn sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="40a62-141">Streaming resources don't currently support 2, 8, and 16 even though they are shown.</span></span>

<span data-ttu-id="40a62-142">In Implementierungen kann der Multiple Sample Antialiasing-Modus (MSAA) mit 2, 8 und/oder 16Beispielen für Nicht-Streamingressourcen unterstützt werden, auch wenn dies von der Streamingressource nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="40a62-142">Implementations can choose to support 2, 8, and/or 16 sample multisample antialiasing (MSAA) mode for non-streaming resources even though streaming resource don't support them.</span></span>

<span data-ttu-id="40a62-143">128-BpP-Formate können von Streamingressourcen mit Beispielanzahlen von mehr als 1 nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="40a62-143">Streaming resources with sample counts larger than 1 can't use 128 bpp formats.</span></span>

<span data-ttu-id="40a62-144">Die Einschränkungen bei der Anzahl unterstützter Beispiele und Formate gehen auf Hardwareinkonsistenzen in der Spezifikation zurück.</span><span class="sxs-lookup"><span data-stu-id="40a62-144">The constraints on supported sample counts and formats are due to hardware inconsistencies from the specification.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="40a62-145"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="40a62-145"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="40a62-146">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="40a62-146">How a streaming resource's area is tiled</span></span>](how-a-streaming-resource-s-area-is-tiled.md)

 

 




