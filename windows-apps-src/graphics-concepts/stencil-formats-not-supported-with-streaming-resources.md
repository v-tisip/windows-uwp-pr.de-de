---
title: "Von den Streamingressourcen nicht unterstützte Schablonenformate"
description: "Formate, die Schablonen enthalten, werden von Streamingressourcen nicht unterstützt."
ms.assetid: 90A572A4-3C76-4795-BAE9-FCC72B5F07AD
keywords: "Von den Streamingressourcen nicht unterstützte Schablonenformate"
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 330b768c0f00f36ce8ce539b9ce41c7ac812e6fc
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="stencil-formats-not-supported-with-streaming-resources"></a><span data-ttu-id="28a72-104">Von den Streamingressourcen nicht unterstützte Schablonenformate</span><span class="sxs-lookup"><span data-stu-id="28a72-104">Stencil formats not supported with streaming resources</span></span>


<span data-ttu-id="28a72-105">Formate, die Schablonen enthalten, werden von Streamingressourcen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="28a72-105">Formats that contain stencil aren't supported with streaming resources.</span></span>

<span data-ttu-id="28a72-106">Zu den Formaten, die Schablonen enthalten, gehören DXGI\_FORMAT\_D24\_UNORM\_S8\_UINT (sowie zugehörige Formate in der R24G8-Familie) und DXGI\_FORMAT\_D32\_FLOAT\_S8X24\_UINT (sowie zugehörige Formate in der R32G8X24-Familie).</span><span class="sxs-lookup"><span data-stu-id="28a72-106">Formats that contain stencil include DXGI\_FORMAT\_D24\_UNORM\_S8\_UINT (and related formats in the R24G8 family) and DXGI\_FORMAT\_D32\_FLOAT\_S8X24\_UINT (and related formats in the R32G8X24 family).</span></span>

<span data-ttu-id="28a72-107">Einige Implementierungen speichern Tiefen- und Schabloneninformationen in separaten Zuordnungen, andere speichern sie zusammen.</span><span class="sxs-lookup"><span data-stu-id="28a72-107">Some implementations store depth and stencil in separate allocations while others store them together.</span></span> <span data-ttu-id="28a72-108">Die Kachelverwaltung für die beiden Schemas müsste unterschiedlich sein, und keine API kann die Unterschiede abstrahieren oder rationalisieren.</span><span class="sxs-lookup"><span data-stu-id="28a72-108">Tile management for the two schemes would have to be different, and no single API can abstract or rationalize the differences.</span></span> <span data-ttu-id="28a72-109">Wir empfehlen für zukünftige Hardware die Unterstützung unabhängiger Tiefen- und Schablonenoberflächen, die voneinander unabhängige Kacheln verwenden.</span><span class="sxs-lookup"><span data-stu-id="28a72-109">We recommend for future hardware to support independent depth and stencil surfaces, each independently tiled.</span></span>

<span data-ttu-id="28a72-110">Die 32-Bit-Tiefe müsste 128x128Kacheln und die 8-BitSchablone müsste 256x256 Kacheln haben.</span><span class="sxs-lookup"><span data-stu-id="28a72-110">32-bit depth would have 128x128 tiles, and 8-bit stencil would have 256x256 tiles.</span></span> <span data-ttu-id="28a72-111">Daher würde es Anwendungen mit einer Diskrepanz in der Kachelform zwischen Tiefe und Schablone geben.</span><span class="sxs-lookup"><span data-stu-id="28a72-111">Therefore, applications would have to live with tile shape misalignment between depth and stencil.</span></span> <span data-ttu-id="28a72-112">Aber das gleiche Problem besteht bereits bei anderen Formaten von Renderzieloberflächen.</span><span class="sxs-lookup"><span data-stu-id="28a72-112">But the same problem exists with different render target surface formats already.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="28a72-113"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="28a72-113"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="28a72-114">Geräte- und prozessübergreifende Streamingressourcen</span><span class="sxs-lookup"><span data-stu-id="28a72-114">Streaming resource cross-process and device sharing</span></span>](streaming-resource-cross-process-and-device-sharing.md)

 

 




