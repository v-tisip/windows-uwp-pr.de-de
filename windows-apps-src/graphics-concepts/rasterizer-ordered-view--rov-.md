---
title: Rasterizergesteuerte Ansicht (ROV)
description: Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.
ms.assetid: BCB1EE0D-4C1D-4E17-BDB7-173F448E0A7B
keywords:
- Rasterizergesteuerte Ansicht (ROV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: bb75d903bee3990b13e261393f3801b4089ec1b0
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1042999"
---
# <a name="rasterizer-ordered-view-rov"></a><span data-ttu-id="e3203-104">Rasterizergesteuerte Ansicht (ROV)</span><span class="sxs-lookup"><span data-stu-id="e3203-104">Rasterizer ordered view (ROV)</span></span>


<span data-ttu-id="e3203-105">Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.</span><span class="sxs-lookup"><span data-stu-id="e3203-105">Rasterizer ordered views enable some of the limitations of a depth buffer to be addressed, in particular having multiple textures containing transparency all applying to the same pixels.</span></span>

<span data-ttu-id="e3203-106">Mit rasterizergesteuerten Ansichten können OIT-Algorithmen (Order Independent Transparency) auf das Rendern von Pixeln angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3203-106">Rasterizer ordered views enable "Order Independent Transparency" (OIT) algorithms to be applied to the rendering of pixels.</span></span> <span data-ttu-id="e3203-107">Mit einem Tiefenpuffer kann ein Pixel lediglich gezeichnet oder verdeckt werden; ein Konzept für ein teilweises Verdecken durch Transparenz ist nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="e3203-107">A depth buffer only enables a pixel to be drawn or occluded, there is no concept of partial occlusion through transparency.</span></span> <span data-ttu-id="e3203-108">OIT-Algorithmen wenden transparente Texturen in der richtigen Reihenfolge an, damit das Endergebnis vorhersehbar richtig gezeichnet wird, wenn z.B. ein transparentes, gläsernes Objekt hinter einem Glasfenster angezeigt werden soll, das sich hinter etwas Vegetation befindet, die transparente Texturen verwendet.</span><span class="sxs-lookup"><span data-stu-id="e3203-108">OIT algorithms apply transparent textures in the correct order, so if, for example, a transparent glass object should appear behind a glass window that is behind some vegetation that uses transparent textures, then the final result is drawn predictably correct.</span></span> <span data-ttu-id="e3203-109">Ohne ROVs und OIT-Algorithmen war die Reihenfolge, mit der diese transparenten Objekte gezeichnet wurden, unvorhersehbar, und die gerenderte Szene konnte verwirrend und inkorrekt sein.</span><span class="sxs-lookup"><span data-stu-id="e3203-109">Without ROVs and OIT algorithms, the order these transparent objects would be drawn was unpredictable and the rendered scene could simply be confusing and wrong.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="e3203-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e3203-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="e3203-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="e3203-111">Views</span></span>](views.md)

 

 




