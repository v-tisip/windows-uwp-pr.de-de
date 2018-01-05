---
title: Konstantenpufferansicht (CBV)
description: "Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird."
ms.assetid: 99AEC6B0-A43B-4B61-8C3A-ECC8DE1B69A7
keywords: Konstantenpufferansicht (CBV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 9e26a446bdd1e5a692e826d2c0ba303688bbd3d7
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="constant-buffer-view-cbv"></a><span data-ttu-id="ce957-105">Konstantenpufferansicht (CBV)</span><span class="sxs-lookup"><span data-stu-id="ce957-105">Constant buffer view (CBV)</span></span>


<span data-ttu-id="ce957-106">Konstantenpuffer enthalten Konstantendaten für Shader.</span><span class="sxs-lookup"><span data-stu-id="ce957-106">Constant buffers contain shader constant data.</span></span> <span data-ttu-id="ce957-107">Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.</span><span class="sxs-lookup"><span data-stu-id="ce957-107">The value of them is that the data persists, and can be accessed by any GPU shader, until it is necessary to change the data.</span></span>

<span data-ttu-id="ce957-108">Typische Daten für einen Konstantenpuffer sind globale, Ansichts- und Projektionsmatrizen, die während des Zeichnens eines Frames konstant bleiben.</span><span class="sxs-lookup"><span data-stu-id="ce957-108">Typical data for a constant buffer would be world, projection and view matrices, which remain constant throughout the drawing of one frame.</span></span>

<span data-ttu-id="ce957-109">Das Konstantenpuffer-Layout sollte mit dem HLSL-Layout übereinstimmen (weitere Informationen finden Sie unter [Regeln für das Packen von Konstantenvariablen](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).</span><span class="sxs-lookup"><span data-stu-id="ce957-109">Constant buffer layout should match the HLSL layout (refer to [Packing Rules for Constant Variables](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="ce957-110"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ce957-110"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="ce957-111">Ansichten</span><span class="sxs-lookup"><span data-stu-id="ce957-111">Views</span></span>](views.md)

 

 




