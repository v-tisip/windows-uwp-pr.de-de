---
title: Mehrstufige Texturvermischung
description: Direct3D-Apps können durch die Anwendung verschiedener Texturen auf eine Primitive im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen.
ms.assetid: FB4D6E3F-4EF5-4D20-BF7E-1008E790E30C
keywords:
- Mehrstufige Texturvermischung
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c55f371e97daba5f81945812f8179eb708bbadd6
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5922046"
---
# <a name="multipass-texture-blending"></a>Mehrstufige Texturvermischung


Direct3D-Anwendungen können durch die Anwendung verschiedener Texturen auf einen Grundtyp im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen. Der allgemeine Begriff dafür ist *Mehrstufige Texturmischung*. Eine typische Anwendung der mehrstufigen Texturmischung ist die Nachbildung der Effekte komplexer Beleuchtungs- und Schattierungsmodelle durch die Anwendung mehrerer Farben aus mehreren unterschiedlichen Texturen. Eine solche Anwendung heißt *Lichtzuordnung*. Siehe [Lichtzuordnung mit Texturen](light-mapping-with-textures.md).

**Hinweis:**  einige Geräte können mehrere Texturen auf primitive in einem einzigen Durchgang anwenden. Siehe [Texturvermischung](texture-blending.md).

 

Wenn die Hardware des Benutzers die Vermischung mehrerer Texturen nicht unterstützt, kann Ihre Anwendung die mehrstufige Texturvermischung verwenden, um die gleichen visuellen Effekte zu erzielen. Die Anwendung kann jedoch nicht die Bildwechselfrequenzen erhalten, die bei Verwendung der Vermischung mehrerer Texturen möglich sind.

Durchführen der mehrstufigen Texturvermischung in einer C/C++-Anwendung:

1.  Setzen Sie eine Textur in Texturphase 0.
2.  Wählen Sie die gewünschte Farb- und Alphavermischungsargumente und -abläufe. Die Standardeinstellungen eignen sich hinlänglich für die mehrstufige Texturvermischung.
3.  Berechnen Sie die entsprechenden 3D-Objekte in der Szene und geben Sie diese aus.
4.  Setzen Sie die nächste Textur in Texturphase 0.
5.  Setzen Sie die Berechnungs- und Ausgabezustände, um die Ursprungs- und Zielvermischungsfaktoren nach Bedarf anzupassen. Das System vermischt die neuen Texturen mit den vorhandenen Pixeln in der Ziel-Ausgeben-Oberfläche gemäß dieser Parameter.
6.  Wiederholen Sie die Schritte3, 4 und 5 mit so vielen Texturen wie gewünscht.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Texturvermischung](texture-blending.md)

 

 




