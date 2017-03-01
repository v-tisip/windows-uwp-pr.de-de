---
title: Konstantenpufferansicht (CBV)
description: "Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird."
ms.assetid: 99AEC6B0-A43B-4B61-8C3A-ECC8DE1B69A7
keywords:
- Konstantenpufferansicht (CBV)
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 84d97f1d03c396ba379ad0a83bb094c09b769924
ms.lasthandoff: 02/07/2017

---

# <a name="constant-buffer-view-cbv"></a>Konstantenpufferansicht (CBV)


Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.

Typische Daten für einen Konstantenpuffer sind globale, Ansichts- und Projektionsmatrizen, die während des Zeichnens eines Frames konstant bleiben.

Das Konstantenpuffer-Layout sollte mit dem HLSL-Layout übereinstimmen (weitere Informationen finden Sie unter [Regeln für das Packen von Konstantenvariablen](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 





