---
title: Anisotropische Texturfilterung
description: Anisotropie ist die sichtbare Verzerrung der Texel eines 3D-Objekts, dessen Oberfläche gegenüber der Bildschirmebene in einem Winkel ausgerichtet ist. Wenn der Pixel eines anisotropischen Grundtyps einem Texel zugeordnet ist, wird die Form verzerrt.
ms.assetid: 58923809-EF76-4C16-BCE7-922A66425F83
keywords:
- Anisotropische Texturfilterung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 6e91c707b31de859d61ae926518c40812758320e
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5836822"
---
# <a name="anisotropic-texture-filtering"></a><span data-ttu-id="2fa6d-105">Anisotropische Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="2fa6d-105">Anisotropic texture filtering</span></span>


<span data-ttu-id="2fa6d-106">*Anisotropie* ist die sichtbare Verzerrung bei Texeln eines 3D-Objekts, dessen Oberfläche gegenüber der Bildschirmebene in einem Winkel ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="2fa6d-106">*Anisotropy* is the distortion visible in the texels of a 3D object whose surface is oriented at an angle with respect to the plane of the screen.</span></span> <span data-ttu-id="2fa6d-107">Wenn der Pixel eines anisotropischen Grundtyps einem Texel zugeordnet ist, wird die Form verzerrt.</span><span class="sxs-lookup"><span data-stu-id="2fa6d-107">When a pixel from an anisotropic primitive is mapped to texels, its shape is distorted.</span></span> <span data-ttu-id="2fa6d-108">Direct3D misst die Anisotropie eines Pixels als Dehnung – d.h. die Länge geteilt durch die Breite - eines Bildschirm-Pixels, das dem Texturbereich entgegengesetzt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="2fa6d-108">Direct3D measures the anisotropy of a pixel as the elongation - that is, length divided by width - of a screen pixel that is inverse-mapped into texture space.</span></span>

<span data-ttu-id="2fa6d-109">Sie können die anisotropische Texturfilterung in Verbindung mit linearer Texturfilterung oder Mipmap-Texturfilterung verwenden, um das Rendering zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="2fa6d-109">You can use anisotropic texture filtering in conjunction with linear texture filtering or mipmap texture filtering to improve rendering results.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="2fa6d-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2fa6d-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="2fa6d-111">Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="2fa6d-111">Texture filtering</span></span>](texture-filtering.md)

 

 




