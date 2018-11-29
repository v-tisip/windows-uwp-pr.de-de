---
title: Einfarbige Lichtzuordnungen
description: Die einfarbige Lichtzuordnung ermöglicht älteren Adaptern das Ausführen der Vermischung von mehrlagigen Texturen, wenn eine ältere 3D-Beschleunigungsplatine die Texturvermischung mit dem Alphawert des Zielpixels nicht unterstützt.
ms.assetid: 60F8F8F6-9DB7-452B-8DC0-407FFAA4BFE1
keywords:
- Einfarbige Lichtzuordnungen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b81838393d7b2692e6fd04b7ce535f58dc773780
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "7982918"
---
# <a name="monochrome-light-maps"></a>Einfarbige Lichtzuordnungen


Die einfarbige Lichtzuordnung ermöglicht älteren Adaptern das Ausführen der Vermischung von mehrlagigen Texturen, wenn eine ältere 3D-Beschleunigungsplatine die Texturvermischung mit dem Alphawert des Zielpixels nicht unterstützt.

Einige ältere 3D-Beschleunigungsplatinen unterstützen die Texturvermischung mit dem Alphawert des Zielpixels nicht. Diese Adapter unterstützen in der Regel auch nicht mehrere Texturvermischungen. Wenn Ihre Anwendung auf einen Adapter wie diesem läuft, kann sie die Vermischung mehrlagiger Texturen verwenden, um eine einfarbige Lichtzuordnung vorzunehmen.

Für eine einfarbige Lichtzuordnung speichert eine Anwendung die Beleuchtungsinformationen in die Alphadaten ihrer Lichtzuordnungstexturen. Die Anwendung verwendet die Texturfilterfunktionen von Direct3D, um jedes Pixel im Bild jeder Primitiven einem entsprechenden Texel in der Lichtzuordnung zuzuordnen. Sie setzt den Ursprungsvermischungsfaktor auf den Alphawert des entsprechenden Texels.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Lichtzuordnung mit Texturen](light-mapping-with-textures.md)

 

 




