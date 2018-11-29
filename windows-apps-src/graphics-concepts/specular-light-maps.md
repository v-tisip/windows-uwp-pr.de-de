---
title: Glanzlichtzuordnungen
description: Wenn glänzende Objekte aus stark reflektierenden Materialien von einer Lichtquelle beleuchtet werden, erhalten sie Glanzlichter.
ms.assetid: 9B3AC5EC-DDAA-4671-BC81-0E3C79D87A81
keywords:
- Glanzlichtzuordnungen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7d88989be04704395c056f1bae058e2aefd1a2a4
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8199328"
---
# <a name="specular-light-maps"></a><span data-ttu-id="6628a-104">Glanzlichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="6628a-104">Specular light maps</span></span>


<span data-ttu-id="6628a-105">Glänzende Objekte aus hochreflektieRendern Materialien erhalten durch das Beleuchten mit einer Lichtquelle Glanzlichter.</span><span class="sxs-lookup"><span data-stu-id="6628a-105">When illuminated by a light source, shiny objects that use highly reflective materials receive specular highlights.</span></span> <span data-ttu-id="6628a-106">In einigen Fällen erhalten Sie exaktere Glanzlichter, wenn Sie Glanzlichtzuordnungen auf Grundtypen anwenden, anstatt die vom Beleuchtungsmodul erzeugten Glanzlichter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6628a-106">Sometimes you can get more accurate highlights by applying specular light maps to primitives, rather than using the specular highlights produced by the lighting module.</span></span>

<span data-ttu-id="6628a-107">Um die Glanzlichtzuordnung durchzuführen, fügen Sie der Textur des Grundtyps die Glanzlichtzuordnung hinzu und modulieren dann die RGB-Lichtzuordnung (multiplizieren Sie das Ergebnis mit der RGB-Lichtzuordnung).</span><span class="sxs-lookup"><span data-stu-id="6628a-107">To perform specular light mapping, add the specular light map to the primitive's texture, then modulate (multiply the result by) the RGB light map.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="6628a-108"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6628a-108"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="6628a-109">Lichtzuordnung mit Texturen</span><span class="sxs-lookup"><span data-stu-id="6628a-109">Light mapping with textures</span></span>](light-mapping-with-textures.md)

 

 




