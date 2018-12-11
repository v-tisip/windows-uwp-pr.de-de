---
title: Einfarbige Lichtzuordnungen
description: Die einfarbige Lichtzuordnung ermöglicht älteren Adaptern das Ausführen der Vermischung von mehrlagigen Texturen, wenn eine ältere 3D-Beschleunigungsplatine die Texturvermischung mit dem Alphawert des Zielpixels nicht unterstützt.
ms.assetid: 60F8F8F6-9DB7-452B-8DC0-407FFAA4BFE1
keywords:
- Einfarbige Lichtzuordnungen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b81838393d7b2692e6fd04b7ce535f58dc773780
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8930326"
---
# <a name="monochrome-light-maps"></a><span data-ttu-id="bb184-104">Einfarbige Lichtzuordnungen</span><span class="sxs-lookup"><span data-stu-id="bb184-104">Monochrome light maps</span></span>


<span data-ttu-id="bb184-105">Die einfarbige Lichtzuordnung ermöglicht älteren Adaptern das Ausführen der Vermischung von mehrlagigen Texturen, wenn eine ältere 3D-Beschleunigungsplatine die Texturvermischung mit dem Alphawert des Zielpixels nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bb184-105">Monochrome light mapping enables older adapters to perform multipass texture blending, when an older 3D accelerator board doesn't support texture blending using the alpha value of the destination pixel.</span></span>

<span data-ttu-id="bb184-106">Einige ältere 3D-Beschleunigungsplatinen unterstützen die Texturvermischung mit dem Alphawert des Zielpixels nicht.</span><span class="sxs-lookup"><span data-stu-id="bb184-106">Some older 3D accelerator boards do not support texture blending using the alpha value of the destination pixel.</span></span> <span data-ttu-id="bb184-107">Diese Adapter unterstützen in der Regel auch nicht mehrere Texturvermischungen.</span><span class="sxs-lookup"><span data-stu-id="bb184-107">These adapters also generally do not support multiple texture blending.</span></span> <span data-ttu-id="bb184-108">Wenn Ihre Anwendung auf einen Adapter wie diesem läuft, kann sie die Vermischung mehrlagiger Texturen verwenden, um eine einfarbige Lichtzuordnung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="bb184-108">If your application is running on an adapter such as this, it can use multipass texture blending to perform monochrome light mapping.</span></span>

<span data-ttu-id="bb184-109">Für eine einfarbige Lichtzuordnung speichert eine Anwendung die Beleuchtungsinformationen in die Alphadaten ihrer Lichtzuordnungstexturen.</span><span class="sxs-lookup"><span data-stu-id="bb184-109">To perform monochrome light mapping, an application stores the lighting information in the alpha data of its light map textures.</span></span> <span data-ttu-id="bb184-110">Die Anwendung verwendet die Texturfilterfunktionen von Direct3D, um jedes Pixel im Bild jeder Primitiven einem entsprechenden Texel in der Lichtzuordnung zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="bb184-110">The application uses the texture filtering capabilities of Direct3D to perform a mapping from each pixel in the primitive's image to a corresponding texel in the light map.</span></span> <span data-ttu-id="bb184-111">Sie setzt den Ursprungsvermischungsfaktor auf den Alphawert des entsprechenden Texels.</span><span class="sxs-lookup"><span data-stu-id="bb184-111">It sets the source blending factor to the alpha value of the corresponding texel.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="bb184-112"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bb184-112"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="bb184-113">Lichtzuordnung mit Texturen</span><span class="sxs-lookup"><span data-stu-id="bb184-113">Light mapping with textures</span></span>](light-mapping-with-textures.md)

 

 




