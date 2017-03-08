---
title: Pufferanordnung
description: "Eine Puffer-Ressource ist in 64 KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von 64 KB ist."
ms.assetid: 577DC6B0-F373-4748-AD80-2784C597C366
keywords:
- Pufferanordnung
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 2382974de7146f4ba64c2422a01c4d3d297a8977
ms.lasthandoff: 02/07/2017

---

# <a name="buffer-tiling"></a>Pufferanordnung


Eine [Puffer](introduction-to-buffers.md)-Ressource ist in 64 KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von 64 KB ist.

Strukturierte Puffer dürfen keine Einschränkung für die Breite haben, wenn sie als Kacheln angeordnet werden sollen. Es kann auf mögliche Leistungsoptimierungen in der Hardware bei der Verwendung von [**StructuredBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff471514) verzichtet werden, indem sie von Anfang an als Kacheln angeordnet werden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[So unterteilen Sie den Bereich einer Streamingressource](how-a-streaming-resource-s-area-is-tiled.md)

 

 





