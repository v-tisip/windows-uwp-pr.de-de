---
title: Tiefenschablonenansicht (Depth Stencil View, DSV)
description: Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.
ms.assetid: 2E8BFF7F-76F8-408E-B8E6-A71B9DF46281
keywords:
- Tiefenschablonenansicht (Depth Stencil View, DSV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 0a64af02bc62a5e7d605f752504027c66f5dc7f7
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7283248"
---
# <a name="depth-stencil-view-dsv"></a><span data-ttu-id="a3593-104">Tiefenschablonenansicht (Depth Stencil View, DSV)</span><span class="sxs-lookup"><span data-stu-id="a3593-104">Depth stencil view (DSV)</span></span>


<span data-ttu-id="a3593-105">Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.</span><span class="sxs-lookup"><span data-stu-id="a3593-105">A depth stencil view provides the format and buffer for holding depth and stencil information.</span></span> <span data-ttu-id="a3593-106">Der Tiefenpuffer dient dazu, das Zeichnen von Pixeln zu vermeiden, die von einem näher liegenden Objekt verdeckt werden und so für den Betrachter nicht sichtbar wären.</span><span class="sxs-lookup"><span data-stu-id="a3593-106">The depth buffer is used to cull the drawing of pixels that would be invisible to the viewer as they are occluded from view by a closer object.</span></span> <span data-ttu-id="a3593-107">Der Schablonenpuffer kann zur Aussortierung (Culling) aller Zeichnungsaktivitäten außerhalb einer definierten Form genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="a3593-107">The stencil buffer can be used to cull all drawing outside of a defined shape.</span></span>

<span data-ttu-id="a3593-108">Abgesehen von der Definition eines bestimmten Renderingbereiches gibt es noch eine Reihe erweiterter Einsatzmöglichkeiten für Schablonenpuffer.</span><span class="sxs-lookup"><span data-stu-id="a3593-108">There are a number of more advanced uses of stencil buffers beyond defining a rendering area.</span></span> <span data-ttu-id="a3593-109">Schablonenpufferwerte können so verändert werden, dass Effekte wie Ausblenden, Silhouetten, Decaling, Auflösen, Umrisse, Schattenvolumen, usw. möglich werden.</span><span class="sxs-lookup"><span data-stu-id="a3593-109">Stencil buffer values can be manipulated to give such effects as fades, silhouettes, decaling, dissolves, outlining, shadow volumes, and so on.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="a3593-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a3593-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="a3593-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="a3593-111">Views</span></span>](views.md)

 

 




