---
title: Shaderressourcenansicht (SRV) und Unsortierte Zugriffsansicht (UAV)
description: "Shaderressourcenansichten verpacken Texturen in der Regel in einem Format, sodass die Shader darauf zugreifen können. Eine unsortierte Zugriffsansicht bietet ähnlichen Funktionen, ermöglicht aber das Lesen und Schreiben der Textur (oder einer anderen Ressource) in beliebiger Reihenfolge."
ms.assetid: 4505BCD2-0EDA-40F2-887C-EC081FE32E8F
keywords: Shaderressourcenansicht (SRV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 213ff4e2a120c91211720d887ab8f777b9265106
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="shader-resource-view-srv-and-unordered-access-view-uav"></a><span data-ttu-id="f8a05-105">Shaderressourcenansicht (SRV) und Unsortierte Zugriffsansicht (UAV)</span><span class="sxs-lookup"><span data-stu-id="f8a05-105">Shader resource view (SRV) and Unordered Access view (UAV)</span></span>


<span data-ttu-id="f8a05-106">Shaderressourcenansichten verpacken Texturen in der Regel in einem Format, sodass die Shader darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="f8a05-106">Shader resource views typically wrap textures in a format that the shaders can access them.</span></span> <span data-ttu-id="f8a05-107">Eine unsortierte Zugriffsansicht bietet ähnlichen Funktionen, ermöglicht aber das Lesen und Schreiben der Textur (oder einer anderen Ressource) in beliebiger Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="f8a05-107">An unordered access view provides similar functionality, but enables the reading and writing to the texture (or other resource) in any order.</span></span>

<span data-ttu-id="f8a05-108">Das Verpacken einer einzelnen Textur ist wahrscheinlich die einfachste Form der Shaderressourcenansicht.</span><span class="sxs-lookup"><span data-stu-id="f8a05-108">Wrapping a single texture is probably the simplest form of shader resource view.</span></span> <span data-ttu-id="f8a05-109">Komplexere Beispiele wären eine Sammlung von Unterressourcen (einzelne Arrays, Ebenen oder Farben aus einer Mipmap-Textur), 3D-Texturen, 1D-Texturfarbverläufe usw.</span><span class="sxs-lookup"><span data-stu-id="f8a05-109">More complex examples would be a collection of subresources (individual arrays, planes, or colors from a mipmapped texture), 3D textures, 1D texture color gradients, and so on.</span></span>

<span data-ttu-id="f8a05-110">Unsortierte Zugriffsansichten sind in Bezug auf die Leistung etwas aufwändiger, ermöglichen aber z.B., dass in eine Textur geschrieben und diese gleichzeitig gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="f8a05-110">Unordered access views are slightly more costly in terms of performance, but allow, for example, a texture to be written to at the same time that it is being read from.</span></span> <span data-ttu-id="f8a05-111">Dadurch kann die aktualisierte Textur von der Grafikpipeline zu einem anderen Zweck wiederverwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f8a05-111">This enables the updated texture to be re-used by the graphics pipeline for some other purpose.</span></span> <span data-ttu-id="f8a05-112">Shaderressourcenansichten sind nur zum Lesen vorgesehen (das ist die gängigste Verwendung von Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="f8a05-112">Shader resource views are for read only use (which is the most common use of resources).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="f8a05-113"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="f8a05-113"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="f8a05-114">Ansichten</span><span class="sxs-lookup"><span data-stu-id="f8a05-114">Views</span></span>](views.md)

 

 




