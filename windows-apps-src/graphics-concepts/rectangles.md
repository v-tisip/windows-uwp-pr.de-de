---
title: Rechtecke
description: In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm in Bezug auf die umgebenden Rechtecke bezeichnet.
ms.assetid: 3B78AE66-2C1A-4191-BDCA-D737E33460BA
keywords: Rechtecke
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 2128dd8fa6ff22e20cd8a25dea0fd44431c1fae2
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="rectangles"></a>Rechtecke


In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm in Bezug auf die umgebenden Rechtecke bezeichnet. Die Seiten des umgebenden Rechtecks sind immer parallel zu den Seiten des Bildschirms. So kann das Rechteck mit zwei Punkten, nämlich der obere linke Ecke und der unteren rechten Ecke, beschrieben werden.

## <a name="span-idboundingrectanglesspanspan-idboundingrectanglesspanspan-idboundingrectanglesspanbounding-rectangles"></a><span id="Bounding_rectangles"></span><span id="bounding_rectangles"></span><span id="BOUNDING_RECTANGLES"></span>Umgebende Rechtecke


Die meisten Anwendungen verwenden die [**RECT**](https://msdn.microsoft.com/library/windows/desktop/dd162897)-Struktur (oder ein Typedef-Alias) als Träger von Informationen über ein umgebendes Rechteck, die beim Blitten auf den Bildschirm oder bei der Trefferermittlung verwendet werden. In C++ die **RECT** Struktur hat folgende Definition.

```
typedef struct tagRECT { 
    LONG    left;    // This is the upper-left corner x-coordinate.
    LONG    top;     // The upper-left corner y-coordinate.
    LONG    right;   // The lower-right corner x-coordinate.
    LONG    bottom;  // The lower-right corner y-coordinate.
} RECT, *PRECT, NEAR *NPRECT, FAR *LPRECT; 
```

In diesem Beispiel bilden die linken und oberen Elemente die x- und y-Koordinaten für die linke obere Ecke des umgebenden Rechtecks. Entsprechend bilden die rechten und unteren Elemente die Koordinaten der unteren rechten Ecke. Die folgende Abbildungzeigt, wie Sie diese Werte darstellen können.

![Abbildungdes durch die linken, oberen, rechten und unteren Werte begrenzten umgebenden Rechtecks](images/rect.png)

Die Pixelspalte am rechten Rand sowie die Pixelzeile am unteren Rand sind nicht im RECT enthalten. Das Sperren eines RECT mit den Elementen {10, 10, 138, 138} ergibt ein Objekt, das 128Pixel breit und hoch ist.

Für erhöhte Effizienz, Konsistenz und Bedienerfreundlichkeit arbeiten alle Direct3D-Darstellungsfunktionen mit Rechtecken.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensystem und Geometrie](coordinate-systems-and-geometry.md)

 

 




