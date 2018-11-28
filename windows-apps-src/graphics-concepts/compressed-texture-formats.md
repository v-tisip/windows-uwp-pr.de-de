---
title: Komprimierte Texturformate
description: Dieser Abschnitt enthält Informationen über die interne Organisation komprimierter Texturformate.
ms.assetid: 24D17B9F-8CA7-4006-9E0F-178C6B3CAEC9
keywords:
- Komprimierte Texturformate
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 3171eba376911157a6ad2687fe3879df751615ac
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7993496"
---
# <a name="compressed-texture-formats"></a><span data-ttu-id="906be-104">Komprimierte Texturformate</span><span class="sxs-lookup"><span data-stu-id="906be-104">Compressed texture formats</span></span>


<span data-ttu-id="906be-105">Dieser Abschnitt enthält Informationen über die interne Organisation komprimierter Texturformate.</span><span class="sxs-lookup"><span data-stu-id="906be-105">This section contains information about the internal organization of compressed texture formats.</span></span> <span data-ttu-id="906be-106">Diese Informationen sind nicht zur Verwendung von komprimierten Texturen notwendig, da Sie die Direct3D-Funktionen für eine Konvertierung in und von komprimierten Formate verwenden können.</span><span class="sxs-lookup"><span data-stu-id="906be-106">You do not need these details to use compressed textures, because you can use Direct3D functions for conversion to and from compressed formats.</span></span> <span data-ttu-id="906be-107">Sie sind jedoch hilfreich, wenn Sie direkt auf komprimierten Oberflächendaten arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="906be-107">However, this information is useful if you want to operate on compressed surface data directly.</span></span>

<span data-ttu-id="906be-108">Direct3D verwendet ein Komprimierungsformat, das Texturabbildungen in 4x4-Texel-Blöcke unterteilt.</span><span class="sxs-lookup"><span data-stu-id="906be-108">Direct3D uses a compression format that divides texture maps into 4x4 texel blocks.</span></span> <span data-ttu-id="906be-109">Wenn die Textur keine Transparenz enthält - wenn sie undurchsichtig ist - oder die Transparenz von einem 1-Bit-Alpha angegeben wird, stellt ein 8-Byte-Block den Texturabbildungsblock dar.</span><span class="sxs-lookup"><span data-stu-id="906be-109">If the texture contains no transparency - is opaque - or if the transparency is specified by a 1-bit alpha, an 8-byte block represents the texture map block.</span></span> <span data-ttu-id="906be-110">Enthält die Texturabbildung transparente Texel, stellt ein 16-Byte-Block mittels eines Alpha-Kanals den Block dar.</span><span class="sxs-lookup"><span data-stu-id="906be-110">If the texture map does contain transparent texels, using an alpha channel, a 16-byte block represents it.</span></span>

<span data-ttu-id="906be-111">Jede einzelne Textur muss angeben, dass die Daten als 64 oder 128Bit pro Gruppe von 16Texeln gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="906be-111">Any single texture must specify that its data is stored as 64 or 128 bits per group of 16 texels.</span></span> <span data-ttu-id="906be-112">Wenn 64-Bit-Blöcke - im BC1-Format – für die Textur verwendet werden, ist es möglich, undurchsichtige und 1-Bit-Alpha-Kanal-Formate auf einer pro-Block-Basis innerhalb der gleichen Textur zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="906be-112">If 64-bit blocks - that is, format BC1 - are used for the texture, it is possible to mix the opaque and 1-bit alpha formats on a per-block basis within the same texture.</span></span> <span data-ttu-id="906be-113">Der Vergleich der Größe der Ganzzahl ohne Vorzeichen für die Farbe\_0 und Farbe\_1 wird eindeutig für jeden Block mit 16 Texeln ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="906be-113">In other words, the comparison of the unsigned integer magnitude of color\_0 and color\_1 is performed uniquely for each block of 16 texels.</span></span>

<span data-ttu-id="906be-114">Wenn 128-Bit-Blöcke verwendet werden, muss der Alphakanal entweder im expliziten ( BC2-Format) oder interpolierten Modus (BC3-Format) für die gesamte Textur angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="906be-114">When 128-bit blocks are used, the alpha channel must be specified in either explicit (format BC2) or interpolated mode (format BC3) for the entire texture.</span></span> <span data-ttu-id="906be-115">Was die Farbe anbetrifft, können beim aktiven interpolierten Modus entweder acht interpolierte Alphamodi oder sechs interpolierte Alphamodi auf einer nach Blöcken gestaffelten Basis verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="906be-115">As with color, when interpolated mode is selected, either eight interpolated alphas or six interpolated alphas mode can be used on a block-by-block basis.</span></span> <span data-ttu-id="906be-116">Bei einem Größenvergleich von alpha\_0 und alpha\_1 wird ein einzig nach Blöcken gestaffelter Größenvergleich ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="906be-116">Again the magnitude comparison of alpha\_0 and alpha\_1 is done uniquely on a block-by-block basis.</span></span>

<span data-ttu-id="906be-117">Der Neigungswinkel für BCn-Formate wird in Bytes (nicht Blöcken) gemessen.</span><span class="sxs-lookup"><span data-stu-id="906be-117">The pitch for BCn formats is measured in bytes (not blocks).</span></span> <span data-ttu-id="906be-118">Wenn beispielsweise eine Breite von 16 vorliegt, haben Sie einen Neigungswinkel von vier Blöcken (4\*8 für BC1, 4\*16 für BC2 oder BC3).</span><span class="sxs-lookup"><span data-stu-id="906be-118">For example, if you have a width of 16, then you will have a pitch of four blocks (4\*8 for BC1, 4\*16 for BC2 or BC3).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="906be-119"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="906be-119"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="906be-120">Komprimierte Texturressourcen</span><span class="sxs-lookup"><span data-stu-id="906be-120">Compressed texture resources</span></span>](compressed-texture-resources.md)

 

 




