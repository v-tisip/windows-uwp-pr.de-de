---
title: Konstantenpufferansicht (CBV)
description: Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.
ms.assetid: 99AEC6B0-A43B-4B61-8C3A-ECC8DE1B69A7
keywords:
- Konstantenpufferansicht (CBV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: cca90c705c7bb4dd1c7e283a9c3ed267cd282b56
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5839283"
---
# <a name="constant-buffer-view-cbv"></a><span data-ttu-id="1577d-105">Konstantenpufferansicht (CBV)</span><span class="sxs-lookup"><span data-stu-id="1577d-105">Constant buffer view (CBV)</span></span>


<span data-ttu-id="1577d-106">Konstantenpuffer enthalten Konstantendaten für Shader.</span><span class="sxs-lookup"><span data-stu-id="1577d-106">Constant buffers contain shader constant data.</span></span> <span data-ttu-id="1577d-107">Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.</span><span class="sxs-lookup"><span data-stu-id="1577d-107">The value of them is that the data persists, and can be accessed by any GPU shader, until it is necessary to change the data.</span></span>

<span data-ttu-id="1577d-108">Typische Daten für einen Konstantenpuffer sind globale, Ansichts- und Projektionsmatrizen, die während des Zeichnens eines Frames konstant bleiben.</span><span class="sxs-lookup"><span data-stu-id="1577d-108">Typical data for a constant buffer would be world, projection and view matrices, which remain constant throughout the drawing of one frame.</span></span>

<span data-ttu-id="1577d-109">Das Konstantenpuffer-Layout sollte mit dem HLSL-Layout übereinstimmen (weitere Informationen finden Sie unter [Regeln für das Packen von Konstantenvariablen](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).</span><span class="sxs-lookup"><span data-stu-id="1577d-109">Constant buffer layout should match the HLSL layout (refer to [Packing Rules for Constant Variables](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="1577d-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1577d-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="1577d-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="1577d-111">Views</span></span>](views.md)

 

 




