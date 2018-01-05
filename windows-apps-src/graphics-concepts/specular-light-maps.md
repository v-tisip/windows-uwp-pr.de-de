---
title: Glanzlichtzuordnungen
description: "Wenn glänzende Objekte aus stark reflektierenden Materialien von einer Lichtquelle beleuchtet werden, erhalten sie Glanzlichter."
ms.assetid: 9B3AC5EC-DDAA-4671-BC81-0E3C79D87A81
keywords: Glanzlichtzuordnungen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 6da5292396a334e50c61fb4638334aae27581d7d
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="specular-light-maps"></a><span data-ttu-id="bbb80-104">Glanzlichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="bbb80-104">Specular light maps</span></span>


<span data-ttu-id="bbb80-105">Wenn glänzende Objekte aus stark reflektierenden Materialien von einer Lichtquelle beleuchtet werden, erhalten sie Glanzlichter.</span><span class="sxs-lookup"><span data-stu-id="bbb80-105">When illuminated by a light source, shiny objects that use highly reflective materials receive specular highlights.</span></span> <span data-ttu-id="bbb80-106">In einigen Fällen erhalten Sie exaktere Glanzlichter, wenn Sie Glanzlichtzuordnungen auf Grundtypen anwenden, anstatt die vom Beleuchtungsmodul erzeugten Glanzlichter zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbb80-106">Sometimes you can get more accurate highlights by applying specular light maps to primitives, rather than using the specular highlights produced by the lighting module.</span></span>

<span data-ttu-id="bbb80-107">Um die Glanzlichtzuordnung durchzuführen, fügen Sie der Textur des Grundtyps die Glanzlichtzuordnung hinzu und modulieren dann die RGB-Lichtzuordnung (multiplizieren Sie das Ergebnis mit der RGB-Lichtzuordnung).</span><span class="sxs-lookup"><span data-stu-id="bbb80-107">To perform specular light mapping, add the specular light map to the primitive's texture, then modulate (multiply the result by) the RGB light map.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="bbb80-108"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bbb80-108"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="bbb80-109">Lichtzuordnung mit Texturen</span><span class="sxs-lookup"><span data-stu-id="bbb80-109">Light mapping with textures</span></span>](light-mapping-with-textures.md)

 

 




