---
title: Sampler
description: Mit Sampling wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet. Ein \ 0034;Sampler \ 0034; ist ein beliebiges Objekt, das aus Ressourcen liest.
ms.assetid: 7ECE13BB-9FC5-44A3-B1B2-2FE163F1D627
keywords:
- Sampler
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e80e160e1225e510ab95f52cbd9f21049c890457
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8942471"
---
# <a name="sampler"></a><span data-ttu-id="bc2fe-105">Sampler</span><span class="sxs-lookup"><span data-stu-id="bc2fe-105">Sampler</span></span>


<span data-ttu-id="bc2fe-106">Mit Sampling wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-106">Sampling is the process of reading input values from a texture, or other resource.</span></span> <span data-ttu-id="bc2fe-107">Ein „Sampler” ist ein beliebiges Objekt, das aus Ressourcen liest.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-107">A "sampler" is any object that reads from resources.</span></span>

<span data-ttu-id="bc2fe-108">Es gibt viele Probleme und Artefakte beim Sampling aus einer Textur und Rendern auf einen Bildschirmbereich.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-108">There are many issues and artifacts from sampling from a texture and rendering to a screen area.</span></span> <span data-ttu-id="bc2fe-109">Wenn z.B. der Bereich, der gerendert werden soll, 50x50 Pixel groß ist, die Textur aber 16x16 Pixel oder 256x256 Pixel groß ist, dann muss die Textur erheblich gestreckt bzw. verkleinert werden.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-109">For example, if the area to be rendered to is 50 by 50 pixels, and the texture is 16 by 16 pixels or 256 by 256 pixels, then some considerable stretching or shrinking of the texture needs to be applied.</span></span> <span data-ttu-id="bc2fe-110">Da diese Größenabweichung zu unerwünschten Artefakten führt, werden Filterungstechniken verwendet, um diese Artefakte zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-110">Because this mismatch in size leads to unwelcome artifacts, filtering techniques are used to mitigate these artifacts.</span></span> <span data-ttu-id="bc2fe-111">Eine häufige Filterungsart für die Verwendung kleiner Texturen für größere Renderingbereiche ist die „bilineare” Filterung.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-111">A common filtering approach to using small textures for larger rendering areas is "bilinear" filtering.</span></span>

<span data-ttu-id="bc2fe-112">Ein weiteres Problem tritt auf, wenn der Bereich, der gerendert wird, sich in einem sehr schrägen Winkel zur Ansicht befindet (z.B. wird eine 256x256-Textur auf einen Bereich in einer Breite von 100Pixel, aber aufgrund des Blickwinkels nur in einer Tiefe von 5Pixel gerendert).</span><span class="sxs-lookup"><span data-stu-id="bc2fe-112">Another issue occurs when the area being rendered to is at a very oblique angle to the view (for example, a 256 by 256 texture being rendered to a area 100 pixels wide but only 5 pixels deep because of the viewing angle).</span></span> <span data-ttu-id="bc2fe-113">In diesem Fall wird häufig die „anisotropische” Filterung angewendet.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-113">In this case "anisotropic" filtering is often applied.</span></span> <span data-ttu-id="bc2fe-114">Die anisotropische Filterung bietet eine bessere Bildqualität als die bilineare Filterung, weil dabei Antialiasingeffekte ohne übermäßiges Weichzeichnen entfernt werden. Diese Filterungsmethode ist aber rechenintensiver.</span><span class="sxs-lookup"><span data-stu-id="bc2fe-114">Anisotropic filtering provides better image quality than bilinear filtering, as it removes aliasing effects without excessive blurring, but is more computationally expensive.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="bc2fe-115"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bc2fe-115"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="bc2fe-116">Ansichten</span><span class="sxs-lookup"><span data-stu-id="bc2fe-116">Views</span></span>](views.md)

 

 




