---
title: Streamausgabeansicht (SOV)
description: Streamausgabeansichten ermöglichen, dass die Vertexinformationen von den Vertex-, Tessellation- und Hüllen-Shadern zur weiteren Verwendung zurück in die Anwendung gestreamt werden.
ms.assetid: F528A920-0EAD-4634-BA5F-CB34A8FAEFFA
keywords:
- Streamausgabeansicht (SOV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: f7d99aadb9f83d2820cd81fa3a4433c6fab8ee82
ms.sourcegitcommit: d0e836dfc937ebf7dfa9c424620f93f3c8e0a7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5654004"
---
# <a name="stream-output-view-sov"></a><span data-ttu-id="45baf-104">Streamausgabeansicht (SOV)</span><span class="sxs-lookup"><span data-stu-id="45baf-104">Stream output view (SOV)</span></span>


<span data-ttu-id="45baf-105">Streamausgabeansichten ermöglichen, dass die Scheitelpunktinformationen von den Scheitelpunkt-, Mosaik- und Geometrie-Shadern zur weiteren Verwendung zurück in die Anwendung gestreamt werden.</span><span class="sxs-lookup"><span data-stu-id="45baf-105">Stream output views enable the vertex information that the vertex, tessellation and geometry shaders have come up with to be streamed back out to the application for further use.</span></span> <span data-ttu-id="45baf-106">Zum Beispiel könnte ein Objekt, das durch diese Shader verzerrt wurde, in die Anwendung zurückgeschrieben werden, um eine genauere Eingabe für eine Physik- oder eine andere Engine bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="45baf-106">For example, an object that has been distorted by these shaders could be written back to the application to provide more accurate input to a physics or other engine.</span></span> <span data-ttu-id="45baf-107">In der Praxis sind aber Streamausgabeansichten ein selten verwendetes Feature der Grafikpipeline.</span><span class="sxs-lookup"><span data-stu-id="45baf-107">In practice though, stream output views are an infrequently used feature of the graphics pipeline.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="45baf-108"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="45baf-108"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="45baf-109">Ansichten</span><span class="sxs-lookup"><span data-stu-id="45baf-109">Views</span></span>](views.md)

 

 




