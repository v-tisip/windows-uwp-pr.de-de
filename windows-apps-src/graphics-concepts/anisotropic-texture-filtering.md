---
title: Anisotropische Texturfilterung
description: "Anisotropie ist die sichtbare Verzerrung der Texel eines 3D-Objekts, dessen Oberfläche gegenüber der Bildschirmebene in einem Winkel ausgerichtet ist. Wenn der Pixel eines anisotropischen Grundtyps einem Texel zugeordnet ist, wird die Form verzerrt."
ms.assetid: 58923809-EF76-4C16-BCE7-922A66425F83
keywords: Anisotropische Texturfilterung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: b6f4b74d64b7a3f9768697b5b6f495a322686c59
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="anisotropic-texture-filtering"></a><span data-ttu-id="9d9d5-105">Anisotropische Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="9d9d5-105">Anisotropic texture filtering</span></span>


<span data-ttu-id="9d9d5-106">*Anisotropie* ist die sichtbare Verzerrung bei Texeln eines 3D-Objekts, dessen Oberfläche gegenüber der Bildschirmebene in einem Winkel ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="9d9d5-106">*Anisotropy* is the distortion visible in the texels of a 3D object whose surface is oriented at an angle with respect to the plane of the screen.</span></span> <span data-ttu-id="9d9d5-107">Wenn der Pixel eines anisotropischen Grundtyps einem Texel zugeordnet ist, wird die Form verzerrt.</span><span class="sxs-lookup"><span data-stu-id="9d9d5-107">When a pixel from an anisotropic primitive is mapped to texels, its shape is distorted.</span></span> <span data-ttu-id="9d9d5-108">Direct3D misst die Anisotropie eines Pixels als Dehnung – d.h. die Länge geteilt durch die Breite - eines Bildschirm-Pixels, das dem Texturbereich entgegengesetzt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="9d9d5-108">Direct3D measures the anisotropy of a pixel as the elongation - that is, length divided by width - of a screen pixel that is inverse-mapped into texture space.</span></span>

<span data-ttu-id="9d9d5-109">Sie können die anisotropische Texturfilterung in Verbindung mit linearer Texturfilterung oder Mipmap-Texturfilterung verwenden, um das Rendering zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="9d9d5-109">You can use anisotropic texture filtering in conjunction with linear texture filtering or mipmap texture filtering to improve rendering results.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="9d9d5-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9d9d5-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="9d9d5-111">Texturfilterung</span><span class="sxs-lookup"><span data-stu-id="9d9d5-111">Texture filtering</span></span>](texture-filtering.md)

 

 




