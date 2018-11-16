---
title: Pufferanordnung
description: Eine Puffer-Ressource ist in 64KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von64KB ist.
ms.assetid: 577DC6B0-F373-4748-AD80-2784C597C366
keywords:
- Pufferanordnung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 1817f501962ccae4cfaf9c0ce075724abd5e7672
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6984713"
---
# <a name="buffer-tiling"></a>Pufferanordnung


Eine [Puffer](introduction-to-buffers.md)-Ressource ist in 64KB große Kacheln unterteilt und verfügt über einen leeren Bereich in der letzten Kachel, wenn die Größe keine Potenz von64KB ist.

Strukturierte Puffer dürfen keine Einschränkung für die Breite haben, wenn sie als Kacheln angeordnet werden sollen. Es kann auf mögliche Leistungsoptimierungen in der Hardware bei der Verwendung von [**StructuredBuffers**](https://msdn.microsoft.com/library/windows/desktop/ff471514) verzichtet werden, indem sie von Anfang an als Kacheln angeordnet werden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[So unterteilen Sie den Bereich einer Streamingressource](how-a-streaming-resource-s-area-is-tiled.md)

 

 




