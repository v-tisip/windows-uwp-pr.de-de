---
title: Unterteilung von Texture2D- und Texture2DArray-Unterressourcen
description: Diese Tabellen zeigen die Unterteilung von Texture2D- und Texture2DArray-Unterressourcen.
ms.assetid: 2DC14DFC-5299-44D9-895F-5A223D3FD530
keywords:
- Unterteilung von Texture2D- und Texture2DArray-Unterressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 245581e4eb2a8526b242feadb5877590283e24f9
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6992583"
---
# <a name="texture2d-and-texture2darray-subresource-tiling"></a><span data-ttu-id="aff14-104">Unterteilung von Texture2D- und Texture2DArray-Unterressourcen</span><span class="sxs-lookup"><span data-stu-id="aff14-104">Texture2D and Texture2DArray subresource tiling</span></span>


<span data-ttu-id="aff14-105">Diese Tabellen zeigen die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen.</span><span class="sxs-lookup"><span data-stu-id="aff14-105">These tables show how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources are tiled.</span></span> <span data-ttu-id="aff14-106">Die Werte in dieser Tabelle beziehen keine Tail-MIP-Verpackung mit ein.</span><span class="sxs-lookup"><span data-stu-id="aff14-106">The values in these tables don't count tail mip packing.</span></span>

## <a name="span-idsubresources-with-multisample-counts-of-1spanspan-idsubresources-with-multisample-counts-of-1spanspan-idsubresources-with-multisample-counts-of-1spansubresources-with-multisample-counts-of-1"></a><span data-ttu-id="aff14-107"><span id="Subresources-with-multisample-counts-of-1"></span><span id="subresources-with-multisample-counts-of-1"></span><span id="SUBRESOURCES-WITH-MULTISAMPLE-COUNTS-OF-1"></span>Unterressourcen mit Multisampling (1)</span><span class="sxs-lookup"><span data-stu-id="aff14-107"><span id="Subresources-with-multisample-counts-of-1"></span><span id="subresources-with-multisample-counts-of-1"></span><span id="SUBRESOURCES-WITH-MULTISAMPLE-COUNTS-OF-1"></span>Subresources with multisample counts of 1</span></span>


<span data-ttu-id="aff14-108">Die folgende Tabelle zeigt die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen mit Multisampling (1).</span><span class="sxs-lookup"><span data-stu-id="aff14-108">This table shows how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources with multisample counts of 1 are tiled.</span></span>

| <span data-ttu-id="aff14-109">Bits/Pixel (1Beispiel/Pixel)</span><span class="sxs-lookup"><span data-stu-id="aff14-109">Bits/Pixel (1 sample/pixel)</span></span> | <span data-ttu-id="aff14-110">Kachelabmessungen (Pixel, B x H)</span><span class="sxs-lookup"><span data-stu-id="aff14-110">Tile Dimensions (Pixels, WxH)</span></span> |
|-----------------------------|-------------------------------|
| <span data-ttu-id="aff14-111">8</span><span class="sxs-lookup"><span data-stu-id="aff14-111">8</span></span>                           | <span data-ttu-id="aff14-112">256 x 256</span><span class="sxs-lookup"><span data-stu-id="aff14-112">256x256</span></span>                       |
| <span data-ttu-id="aff14-113">16</span><span class="sxs-lookup"><span data-stu-id="aff14-113">16</span></span>                          | <span data-ttu-id="aff14-114">256 x 128</span><span class="sxs-lookup"><span data-stu-id="aff14-114">256x128</span></span>                       |
| <span data-ttu-id="aff14-115">32</span><span class="sxs-lookup"><span data-stu-id="aff14-115">32</span></span>                          | <span data-ttu-id="aff14-116">128 x 128</span><span class="sxs-lookup"><span data-stu-id="aff14-116">128x128</span></span>                       |
| <span data-ttu-id="aff14-117">64</span><span class="sxs-lookup"><span data-stu-id="aff14-117">64</span></span>                          | <span data-ttu-id="aff14-118">128 x 64</span><span class="sxs-lookup"><span data-stu-id="aff14-118">128x64</span></span>                        |
| <span data-ttu-id="aff14-119">128</span><span class="sxs-lookup"><span data-stu-id="aff14-119">128</span></span>                         | <span data-ttu-id="aff14-120">64 x 64</span><span class="sxs-lookup"><span data-stu-id="aff14-120">64x64</span></span>                         |
| <span data-ttu-id="aff14-121">BC1, 4</span><span class="sxs-lookup"><span data-stu-id="aff14-121">BC1,4</span></span>                       | <span data-ttu-id="aff14-122">512 x 256</span><span class="sxs-lookup"><span data-stu-id="aff14-122">512x256</span></span>                       |
| <span data-ttu-id="aff14-123">BC2, 3, 5, 6, 7</span><span class="sxs-lookup"><span data-stu-id="aff14-123">BC2,3,5,6,7</span></span>                 | <span data-ttu-id="aff14-124">256 x 256</span><span class="sxs-lookup"><span data-stu-id="aff14-124">256x256</span></span>                       |

 

<span data-ttu-id="aff14-125">Format-Bitanzahlen, die bei Streamingressourcen nicht unterstützt werden, sind 96-bpp-Formate, Videoformate, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span><span class="sxs-lookup"><span data-stu-id="aff14-125">Format bit counts not supported with streaming resources are 96 bpp formats, video formats, DXGI\_FORMAT\_R1\_UNORM, DXGI\_FORMAT\_R8G8\_B8G8\_UNORM, and DXGI\_FORMAT\_R8R8\_G8B8\_UNORM.</span></span>

## <a name="span-idsubresources-with-various-multisample-countsspanspan-idsubresources-with-various-multisample-countsspanspan-idsubresources-with-various-multisample-countsspansubresources-with-various-multisample-counts"></a><span data-ttu-id="aff14-126"><span id="Subresources-with-various-multisample-counts"></span><span id="subresources-with-various-multisample-counts"></span><span id="SUBRESOURCES-WITH-VARIOUS-MULTISAMPLE-COUNTS"></span>Unterressourcen mit verschiedenen Multisampling-Anzahlen</span><span class="sxs-lookup"><span data-stu-id="aff14-126"><span id="Subresources-with-various-multisample-counts"></span><span id="subresources-with-various-multisample-counts"></span><span id="SUBRESOURCES-WITH-VARIOUS-MULTISAMPLE-COUNTS"></span>Subresources with various multisample counts</span></span>


<span data-ttu-id="aff14-127">Die folgende Tabelle zeigt die Unterteilung von [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525)- und [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Unterressourcen mit verschiedenen Multisampling-Anzahlen.</span><span class="sxs-lookup"><span data-stu-id="aff14-127">This table shows how [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) and [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) subresources with various multisample counts are tiled.</span></span>

| <span data-ttu-id="aff14-128">Bits/Pixel (1Beispiel/Pixel)</span><span class="sxs-lookup"><span data-stu-id="aff14-128">Bits/Pixel (1 sample/pixel)</span></span> | <span data-ttu-id="aff14-129">Kachelabmessungen (Pixel, B x H)</span><span class="sxs-lookup"><span data-stu-id="aff14-129">Tile Dimensions (Pixels, WxH)</span></span> |
|-----------------------------|-------------------------------|
| <span data-ttu-id="aff14-130">1</span><span class="sxs-lookup"><span data-stu-id="aff14-130">1</span></span>                           | <span data-ttu-id="aff14-131">1 x 1</span><span class="sxs-lookup"><span data-stu-id="aff14-131">1x1</span></span>                           |
| <span data-ttu-id="aff14-132">2</span><span class="sxs-lookup"><span data-stu-id="aff14-132">2</span></span>                           | <span data-ttu-id="aff14-133">2 x 1</span><span class="sxs-lookup"><span data-stu-id="aff14-133">2x1</span></span>                           |
| <span data-ttu-id="aff14-134">4</span><span class="sxs-lookup"><span data-stu-id="aff14-134">4</span></span>                           | <span data-ttu-id="aff14-135">2 x 2</span><span class="sxs-lookup"><span data-stu-id="aff14-135">2x2</span></span>                           |
| <span data-ttu-id="aff14-136">8</span><span class="sxs-lookup"><span data-stu-id="aff14-136">8</span></span>                           | <span data-ttu-id="aff14-137">4 x 2</span><span class="sxs-lookup"><span data-stu-id="aff14-137">4x2</span></span>                           |
| <span data-ttu-id="aff14-138">16</span><span class="sxs-lookup"><span data-stu-id="aff14-138">16</span></span>                          | <span data-ttu-id="aff14-139">4 x 4</span><span class="sxs-lookup"><span data-stu-id="aff14-139">4x4</span></span>                           |

 

<span data-ttu-id="aff14-140">Es sind ausschließlich Beispielanzahlen von 1 und 4 erforderlich (und zulässig), um mit Streamingressourcen unterstützt zu werden.</span><span class="sxs-lookup"><span data-stu-id="aff14-140">Only sample counts 1 and 4 are required (and allowed) to be supported with streaming resources.</span></span> <span data-ttu-id="aff14-141">Anzahlen von 2, 8 und 16 werden derzeit von Streamingressourcen nicht unterstützt, auch wenn sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aff14-141">Streaming resources don't currently support 2, 8, and 16 even though they are shown.</span></span>

<span data-ttu-id="aff14-142">In Implementierungen kann der Multiple Sample Antialiasing-Modus (MSAA) mit 2, 8 und/oder 16Beispielen für Nicht-Streamingressourcen unterstützt werden, auch wenn dies von der Streamingressource nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="aff14-142">Implementations can choose to support 2, 8, and/or 16 sample multisample antialiasing (MSAA) mode for non-streaming resources even though streaming resource don't support them.</span></span>

<span data-ttu-id="aff14-143">128-BpP-Formate können von Streamingressourcen mit Beispielanzahlen von mehr als 1 nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aff14-143">Streaming resources with sample counts larger than 1 can't use 128 bpp formats.</span></span>

<span data-ttu-id="aff14-144">Die Einschränkungen bei der Anzahl unterstützter Beispiele und Formate gehen auf Hardwareinkonsistenzen in der Spezifikation zurück.</span><span class="sxs-lookup"><span data-stu-id="aff14-144">The constraints on supported sample counts and formats are due to hardware inconsistencies from the specification.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="aff14-145"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="aff14-145"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="aff14-146">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="aff14-146">How a streaming resource's area is tiled</span></span>](how-a-streaming-resource-s-area-is-tiled.md)

 

 




