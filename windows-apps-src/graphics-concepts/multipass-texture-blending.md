---
title: Mehrstufige Texturvermischung
description: "Direct3D-Apps können durch die Anwendung verschiedener Texturen auf eine Primitive im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen."
ms.assetid: FB4D6E3F-4EF5-4D20-BF7E-1008E790E30C
keywords: Mehrstufige Texturvermischung
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 1ea0f10e4cec774a0b7d85bd813b8c4f720d0048
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="multipass-texture-blending"></a>Mehrstufige Texturvermischung


Direct3D-Apps können durch die Anwendung verschiedener Texturen auf eine Primitive im Laufe von mehreren Berechnungs- und Ausgabedurchläufen zahlreiche Spezialeffekte erzielen. Der allgemeine Begriff lautet *Mehrstufige Texturvermischung*. Eine typische Anwendung für die mehrstufige Texturvermischung liegt in der Nachbildung der Effekte von komplexen Beleuchtungs- und Verschattungsmodellen durch die Anwendung mehrerer Farben aus mehreren unterschiedlichen Texturen. Eine solche Anwendung heißt *Lichtzuordnung*. Siehe [Lichtzuordnung mit Texturen](light-mapping-with-textures.md).

+**Hinweis:**   Einige Geräte können mehrere Texturen auf Primitive in einem einzigen Durchgang anwenden. Siehe [Texturvermischung](texture-blending.md).

 

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

 

 




