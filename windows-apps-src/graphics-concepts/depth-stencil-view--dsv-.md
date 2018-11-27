---
title: Tiefenschablonenansicht (Depth Stencil View, DSV)
description: Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.
ms.assetid: 2E8BFF7F-76F8-408E-B8E6-A71B9DF46281
keywords:
- Tiefenschablonenansicht (Depth Stencil View, DSV)
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 69e726291cc9bd79cb96b1b1460c4027aee9c0b7
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7705439"
---
# <a name="depth-stencil-view-dsv"></a><span data-ttu-id="a3593-104">Tiefenschablonenansicht (Depth Stencil View, DSV)</span><span class="sxs-lookup"><span data-stu-id="a3593-104">Depth stencil view (DSV)</span></span>


<span data-ttu-id="a3593-105">Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.</span><span class="sxs-lookup"><span data-stu-id="a3593-105">A depth stencil view provides the format and buffer for holding depth and stencil information.</span></span> <span data-ttu-id="a3593-106">Der Tiefenpuffer dient dazu, das Zeichnen von Pixeln zu vermeiden, die von einem näher liegenden Objekt verdeckt werden und so für den Betrachter nicht sichtbar wären.</span><span class="sxs-lookup"><span data-stu-id="a3593-106">The depth buffer is used to cull the drawing of pixels that would be invisible to the viewer as they are occluded from view by a closer object.</span></span> <span data-ttu-id="a3593-107">Der Schablonenpuffer kann zur Aussortierung (Culling) aller Zeichnungsaktivitäten außerhalb einer definierten Form genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="a3593-107">The stencil buffer can be used to cull all drawing outside of a defined shape.</span></span>

<span data-ttu-id="a3593-108">Abgesehen von der Definition eines bestimmten Renderingbereiches gibt es noch eine Reihe erweiterter Einsatzmöglichkeiten für Schablonenpuffer.</span><span class="sxs-lookup"><span data-stu-id="a3593-108">There are a number of more advanced uses of stencil buffers beyond defining a rendering area.</span></span> <span data-ttu-id="a3593-109">Schablonenpufferwerte können so verändert werden, dass Effekte wie Ausblenden, Silhouetten, Decaling, Auflösen, Umrisse, Schattenvolumen, usw. möglich werden.</span><span class="sxs-lookup"><span data-stu-id="a3593-109">Stencil buffer values can be manipulated to give such effects as fades, silhouettes, decaling, dissolves, outlining, shadow volumes, and so on.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a3593-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a3593-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a3593-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="a3593-111">Views</span></span>](views.md)

 

 




