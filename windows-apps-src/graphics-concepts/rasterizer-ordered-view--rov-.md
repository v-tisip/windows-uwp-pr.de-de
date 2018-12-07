---
title: Rasterizergesteuerte Ansicht (ROV)
description: Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.
ms.assetid: BCB1EE0D-4C1D-4E17-BDB7-173F448E0A7B
keywords:
- Rasterizergesteuerte Ansicht (ROV)
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ed49ba81c44a799e4d827d636f601c77d01333b3
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8795591"
---
# <a name="rasterizer-ordered-view-rov"></a><span data-ttu-id="059dd-104">Rasterizergesteuerte Ansicht (ROV)</span><span class="sxs-lookup"><span data-stu-id="059dd-104">Rasterizer ordered view (ROV)</span></span>


<span data-ttu-id="059dd-105">Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.</span><span class="sxs-lookup"><span data-stu-id="059dd-105">Rasterizer ordered views enable some of the limitations of a depth buffer to be addressed, in particular having multiple textures containing transparency all applying to the same pixels.</span></span>

<span data-ttu-id="059dd-106">Mit rasterizergesteuerten Ansichten können OIT-Algorithmen (Order Independent Transparency) auf das Rendern von Pixeln angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="059dd-106">Rasterizer ordered views enable "Order Independent Transparency" (OIT) algorithms to be applied to the rendering of pixels.</span></span> <span data-ttu-id="059dd-107">Mit einem Tiefenpuffer kann ein Pixel lediglich gezeichnet oder verdeckt werden; ein Konzept für ein teilweises Verdecken durch Transparenz ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="059dd-107">A depth buffer only enables a pixel to be drawn or occluded, there is no concept of partial occlusion through transparency.</span></span> <span data-ttu-id="059dd-108">OIT-Algorithmen wenden transparente Texturen in der richtigen Reihenfolge an, damit das Endergebnis vorhersehbar richtig gezeichnet wird, wenn z.B. ein transparentes, gläsernes Objekt hinter einem Glasfenster angezeigt werden soll, das sich hinter etwas Vegetation befindet, die transparente Texturen verwendet.</span><span class="sxs-lookup"><span data-stu-id="059dd-108">OIT algorithms apply transparent textures in the correct order, so if, for example, a transparent glass object should appear behind a glass window that is behind some vegetation that uses transparent textures, then the final result is drawn predictably correct.</span></span> <span data-ttu-id="059dd-109">Ohne ROVs und OIT-Algorithmen war die Reihenfolge, mit der diese transparenten Objekte gezeichnet wurden, unvorhersehbar, und die gerenderte Szene konnte verwirrend und inkorrekt sein.</span><span class="sxs-lookup"><span data-stu-id="059dd-109">Without ROVs and OIT algorithms, the order these transparent objects would be drawn was unpredictable and the rendered scene could simply be confusing and wrong.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="059dd-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="059dd-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="059dd-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="059dd-111">Views</span></span>](views.md)

 

 




