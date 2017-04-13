---
title: Konstantenpufferansicht (CBV)
description: "Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird."
ms.assetid: 99AEC6B0-A43B-4B61-8C3A-ECC8DE1B69A7
keywords: Konstantenpufferansicht (CBV)
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 755c80e895281b93e9e37144526ed1790c63199f
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="constant-buffer-view-cbv"></a>Konstantenpufferansicht (CBV)


Konstantenpuffer enthalten Konstantendaten für Shader. Der Nutzen ist, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.

Typische Daten für einen Konstantenpuffer sind globale, Ansichts- und Projektionsmatrizen, die während des Zeichnens eines Frames konstant bleiben.

Das Konstantenpuffer-Layout sollte mit dem HLSL-Layout übereinstimmen (weitere Informationen finden Sie unter [Regeln für das Packen von Konstantenvariablen](https://msdn.microsoft.com/library/windows/desktop/bb509632.aspx)).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 




