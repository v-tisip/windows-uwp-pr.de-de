---
title: Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen
description: In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt.
ms.assetid: 145EB4A3-3910-4126-BC7E-A4CF53E2A098
keywords:
- Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 35a591d805870df97ee03169b20e664316e094a7
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7697533"
---
# <a name="address-space-available-for-streaming-resources"></a><span data-ttu-id="af589-104">Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="af589-104">Address space available for streaming resources</span></span>


<span data-ttu-id="af589-105">In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="af589-105">This section specifies the virtual address space that is available for streaming resources.</span></span>

<span data-ttu-id="af589-106">Bei 64-Bit-Betriebssystemen ist mindestens 40Bit virtueller Adressraum (1Terabyte) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="af589-106">On 64-bit operating systems, at least 40 bits of virtual address space (1 Terabyte) is available.</span></span>

<span data-ttu-id="af589-107">Bei 32-Bit-Betriebssystemen beträgt der Adressraum 32Bit (4GB).</span><span class="sxs-lookup"><span data-stu-id="af589-107">For 32-bit operating systems, the address space is 32 bit (4 GB).</span></span> <span data-ttu-id="af589-108">Bei 32-Bit-Betriebssystemen kann das Erstellen einzelner Streamingressourcen zu Fehlern führen, wenn die Zuordnung des Adressraums (128MB) mehr als 27Bit beträgt.</span><span class="sxs-lookup"><span data-stu-id="af589-108">For 32-bit ARM systems, individual streaming resource creation can fail if the allocation would use more than 27 bits of address space (128 MB).</span></span> <span data-ttu-id="af589-109">Dazu gehören alle ausgeblendeten Abstände im Adressraum, die die Hardware für Mipmaps, Abstände für aneinanderliegende Kacheln und möglicherweise Abstände für Oberflächengrößen mit Potenzen von2 verwendet.</span><span class="sxs-lookup"><span data-stu-id="af589-109">This includes any hidden padding in the address space the hardware may use for mipmaps, packed tile padding, and possibly padding surface dimensions to powers of 2.</span></span>

<span data-ttu-id="af589-110">Auf Grafiksystemen mit einer separaten Seitentabelle für den Grafikprozessor (GPU) wird der Adressraum hauptsächlich für die von der Anwendung erstellten GPU-Ressourcen verwendet, auch wenn die vom Anzeigetreiber vorgenommene GPU-Zuordnungen genauso viel Platz verwenden.</span><span class="sxs-lookup"><span data-stu-id="af589-110">On graphics systems with a separate page table for the graphics processing unit (GPU), most of this address space will be available to GPU resources made by the application, though GPU allocations made by the display driver fit in the same space.</span></span>

<span data-ttu-id="af589-111">Bei zukünftigen Systemen, bei denen die Seitentabelle gemeinsam von CPU und GPU genutzt wird, wird der verfügbare Adressraum gemeinsam von CPU und GPU-Zuordnungen in einem Prozess genutzt.</span><span class="sxs-lookup"><span data-stu-id="af589-111">On future systems with a page table shared between the CPU and GPU, the available address space is shared between all CPU and GPU allocations in a process.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="af589-112"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="af589-112"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="af589-113">Parameter für das Erstellen von Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="af589-113">Streaming resource creation parameters</span></span>](streaming-resource-creation-parameters.md)

 

 




