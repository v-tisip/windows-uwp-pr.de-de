---
title: Pufferanordnung
description: Eine Puffer-Ressource ist in 64KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von64KB ist.
ms.assetid: 577DC6B0-F373-4748-AD80-2784C597C366
keywords:
- Pufferanordnung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1817f501962ccae4cfaf9c0ce075724abd5e7672
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5682094"
---
# <a name="buffer-tiling"></a><span data-ttu-id="564ba-104">Pufferanordnung</span><span class="sxs-lookup"><span data-stu-id="564ba-104">Buffer tiling</span></span>


<span data-ttu-id="564ba-105">Eine [Puffer](introduction-to-buffers.md)-Ressource ist in 64KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von64KB ist.</span><span class="sxs-lookup"><span data-stu-id="564ba-105">A [Buffer](introduction-to-buffers.md) resource is divided into 64KB tiles, with some empty space in the last tile if the size is not a multiple of 64KB.</span></span>

<span data-ttu-id="564ba-106">Strukturierte Puffer dürfen keine Einschränkung für die Breite haben, wenn sie als Kacheln angeordnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="564ba-106">Structured buffers must have no constraint on the stride to be tiled.</span></span> <span data-ttu-id="564ba-107">Es kann auf mögliche Leistungsoptimierungen in der Hardware bei der Verwendung von [**StructuredBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff471514) verzichtet werden, indem sie von Anfang an als Kacheln angeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="564ba-107">But possible performance optimizations in hardware for using [**StructuredBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff471514) can be sacrificed by making them tiled in the first place.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="564ba-108"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="564ba-108"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="564ba-109">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="564ba-109">How a streaming resource's area is tiled</span></span>](how-a-streaming-resource-s-area-is-tiled.md)

 

 




