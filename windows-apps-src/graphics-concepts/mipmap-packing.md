---
title: Mip-Map-Verpackung
description: Eine gewisse Anzahl an Mips (pro Array-Segment) kann in einer gewissen Anzahl von Kacheln verpackt sein, in Abhängigkeit von den Dimensionen der Streaming-Ressource, dem Format, der Anzahl der Mip-Maps und Array-Segmente.
ms.assetid: 906C3CAC-4E84-4947-B508-06788551BE85
keywords:
- Mip-Map-Verpackung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ec3d091d7cc5aca82aeef9a3e7f29a8d363705a3
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5740602"
---
# <a name="mipmap-packing"></a><span data-ttu-id="1efdb-104">Mip-Map-Verpackung</span><span class="sxs-lookup"><span data-stu-id="1efdb-104">Mipmap packing</span></span>


<span data-ttu-id="1efdb-105">Eine gewisse Anzahl an Mips (pro Array-Segment) kann in einer gewissen Anzahl von Kacheln verpackt sein, in Abhängigkeit von den Dimensionen der Streaming-Ressource, dem Format, der Anzahl der Mip-Maps und Array-Segmente.</span><span class="sxs-lookup"><span data-stu-id="1efdb-105">Some number of mips (per array slice) can be packed into some number of tiles, depending on a streaming resource's dimensions, format, number of mipmaps, and array slices.</span></span>

<span data-ttu-id="1efdb-106">Je nach [Ebene](streaming-resources-features-tiers.md) des Streaming-Ressourcen-Supports folgen Mip-Maps mit bestimmten Dimensionen nicht den Standard-Kachel Formen und gelten als in einer für die Anwendung unverständlichen Weise miteinander verpackt.</span><span class="sxs-lookup"><span data-stu-id="1efdb-106">Depending on the [tier](streaming-resources-features-tiers.md) of streaming resources support, mipmaps with certain dimensions don't follow the standard tile shapes and are considered to all be packed together with one another in a manner that is opaque to the application.</span></span> <span data-ttu-id="1efdb-107">Höhere Supportebenen zeichnen sich durch breiter gefasste Garantien darüber aus, welche Arten an Oberflächendimensionen in die Standard-Kachel Formen passen (und können daher einzeln durch Anwendungen zugeordnet werden).</span><span class="sxs-lookup"><span data-stu-id="1efdb-107">Higher tiers of support have broader guarantees about what types of surface dimensions fit in the standard tile shapes (and can therefore be individually mapped by applications).</span></span>

<span data-ttu-id="1efdb-108">Die möglichen Unterschiede zwischen Implementierungen bestehen darin, dass – angesichts der Dimensionen der Streaming-Ressource, des Formates, der Anzahl an Mip-Maps und Array-Segmente – eine Anzahl M an Mips (pro Array-Segment) in eine bestimmte Anzahl N an Kacheln gepackt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1efdb-108">What can vary between implementations is that—given a streaming resource's dimensions, format, number of mipmaps, and array slices—some number M of mips (per array slice) can be packed into some number N tiles.</span></span> <span data-ttu-id="1efdb-109">Wenn Sie die Ressourcenkachelinformationen für ein Gerät erhalten, meldet der Treiber an die Anwendung die Werte für M und N (neben anderen Informationen über die Oberfläche, die standardmäßig sind und nicht zwischen Hardwareherstellern variieren).</span><span class="sxs-lookup"><span data-stu-id="1efdb-109">When you get the resource tiling information for a device, the driver reports to the application what M and N are (among other details about the surface that are standard and don't vary by hardware vendor).</span></span> <span data-ttu-id="1efdb-110">Die Kacheln für die verpackten Mips sind weiterhin 64KB groß und können einzeln verschiedenen Positionen in einem Kachelpool zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="1efdb-110">The set of tiles for the packed mips are still 64KB and can be individually mapped into disparate locations in a tile pool.</span></span>

<span data-ttu-id="1efdb-111">Jedoch sind die Pixelform der Kacheln und wie die Mip-Maps in die Kacheln passen für einen Hardware-Anbieter spezifisch und zu komplex zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="1efdb-111">But the pixel shape of the tiles and how the mipmaps fit across the set of tiles is specific to a hardware vendor and too complex to expose.</span></span> <span data-ttu-id="1efdb-112">Daher müssen Anwendungen entweder gleichzeitig alle Kacheln zuordnen, welche als verpackt festgelegt sind, oder keine.</span><span class="sxs-lookup"><span data-stu-id="1efdb-112">So, applications are required to either map all of the tiles that are designated as packed, or none of them, at a time.</span></span> <span data-ttu-id="1efdb-113">Andernfalls ist das Verhalten für den Zugriff auf die Streaming-Ressource nicht definiert.</span><span class="sxs-lookup"><span data-stu-id="1efdb-113">Otherwise, the behavior for accessing the streaming resource is undefined.</span></span>

<span data-ttu-id="1efdb-114">Für angeordnete Oberflächen gelten die Anzahl an verpackten Mips und die Anzahl an verpackten Kacheln, welche diese Mips speichern (M und N, wie vorstehend beschrieben) einzeln für jedes Array-Segment.</span><span class="sxs-lookup"><span data-stu-id="1efdb-114">For arrayed surfaces, the set of packed mips and the number of packed tiles storing those mips (M and N described preceding) applies individually for each array slice.</span></span>

<span data-ttu-id="1efdb-115">Dedizierte API für das Kopieren von Kacheln können nicht auf verpackte Mips zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1efdb-115">Dedicated APIs for copying tiles can't access packed mips.</span></span> <span data-ttu-id="1efdb-116">Anwendungen, die Daten in und aus verpackten Mips kopieren möchten, können dazu alle Nicht-Streaming-Ressourcenspezifische API zum Kopieren und zum Rendern von Oberflächen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1efdb-116">Applications that want to copy data to and from packed mips can do so using all the non-streaming resource-specific APIs for copying and rendering to surfaces.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1efdb-117"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1efdb-117"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1efdb-118">So unterteilen Sie den Bereich einer Streamingressource</span><span class="sxs-lookup"><span data-stu-id="1efdb-118">How a streaming resource's area is tiled</span></span>](how-a-streaming-resource-s-area-is-tiled.md)

 

 




