---
title: Sampler
description: Mit Sampling wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet. Ein \ 0034;Sampler \ 0034; ist ein beliebiges Objekt, das aus Ressourcen liest.
ms.assetid: 7ECE13BB-9FC5-44A3-B1B2-2FE163F1D627
keywords: Sampler
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 919de99d9f0680ea63f70a027344c49f3fbd093e
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="sampler"></a>Sampler


Mit Sampling wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet. Ein „Sampler” ist ein beliebiges Objekt, das aus Ressourcen liest.

Es gibt viele Probleme und Artefakte beim Sampling aus einer Textur und Rendern auf einen Bildschirmbereich. Wenn z.B. der Bereich, der gerendert werden soll, 50x50 Pixel groß ist, die Textur aber 16x16 Pixel oder 256x256 Pixel groß ist, dann muss die Textur erheblich gestreckt bzw. verkleinert werden. Da diese Größenabweichung zu unerwünschten Artefakten führt, werden Filterungstechniken verwendet, um diese Artefakte zu minimieren. Eine häufige Filterungsart für die Verwendung kleiner Texturen für größere Renderingbereiche ist die „bilineare” Filterung.

Ein weiteres Problem tritt auf, wenn der Bereich, der gerendert wird, sich in einem sehr schrägen Winkel zur Ansicht befindet (z.B. wird eine 256x256-Textur auf einen Bereich in einer Breite von 100Pixel, aber aufgrund des Blickwinkels nur in einer Tiefe von 5Pixel gerendert). In diesem Fall wird häufig die „anisotropische” Filterung angewendet. Die anisotropische Filterung bietet eine bessere Bildqualität als die bilineare Filterung, weil dabei Antialiasingeffekte ohne übermäßiges Weichzeichnen entfernt werden. Diese Filterungsmethode ist aber rechenintensiver.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 




