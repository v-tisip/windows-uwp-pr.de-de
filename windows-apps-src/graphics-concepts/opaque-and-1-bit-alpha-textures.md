---
title: Undurchsichtige und 1-Bit-Alpha-Texturen
description: Das Texturformat BC1 ist für Texturen, die undurchsichtig sind oder eine transparente Farbe haben.
ms.assetid: 8C53ACDD-72ED-4307-B4F3-2FCF9A9F53EC
keywords:
- Undurchsichtige und 1-Bit-Alpha-Texturen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 672d7b2ddc913ea3a966fbd0a095367521a27d7c
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6657188"
---
# <a name="span-iddirect3dconceptsopaqueand1-bitalphatexturesspanopaque-and-1-bit-alpha-textures"></a><span id="direct3dconcepts.opaque_and_1-bit_alpha_textures"></span>Undurchsichtige und 1-Bit-Alpha-Texturen


Das Texturformat BC1 ist für Texturen, die undurchsichtig sind oder eine transparente Farbe haben.

Für jeden undurchsichtigen oder 1-Bit-Alpha-Block sind zwei 16-Bit-Werte (RGB-5:6:5-Format) und eine 4x4-Bitmap mit 2 Bits pro Pixel gespeichert. Dies ergibt insgesamt 64Bit für 16 Texel oder vier Bits pro Texel. Im Block Bitmap stehen 2 Bits pro Texel zwischen den vier Farben zur Auswahl, von denen zwei in den codierten Daten gespeichert sind. Die beiden anderen Farben werden von diesen gespeicherten Farben mittels linearer Interpolation abgeleitet. Dieser Aufbau ist im folgenden Diagramm dargestellt.

![Diagramm des Bitmap-Layouts](images/colors1.png)

Das 1-Bit-Alpha-Format unterscheidet sich vom undurchsichtigen Format durch einen Vergleich der zwei 16-Bit-Farbwerte, die im Block gespeichert sind. Sie werden als ganze Zahlen ohne Vorzeichen behandelt. Wenn die erste Farbe größer als die zweite ist, bedeutet dies, dass nur undurchsichtige Texel definiert sind. Dies bedeutet, dass vier Farben zum Darstellen der Texel verwendet werden. Bei der Codierung mit vier Farben gibt es zwei abgeleitete Farben und alle vier Farben werden in RGB-Farbraum gleichmäßig verteilt. Dieses Format ist vergleichbar mit dem RGB-5:6:5-Format. Andernfalls werden für die 1-Bit-Alpha-Transparenz drei Farben verwendet, und die vierte ist zum Darstellen von transparenten Texeln reserviert.

Bei der Codierung mit drei Farben gibt es eine abgeleitete Farbe und der vierte 2-Bit-Code ist zum Anzeigen eines transparenten Texels reserviert (Alpha-Informationen). Dieses Format ist analog zu RGBA-5:5:5:1, in dem das letzte Bit verwendet wird, um die Alphamaske zu codieren.

Das folgende Codebeispiel veranschaulicht den Algorithmus für die Entscheidung, ob eine Codierung mit drei oder vier Farben ausgewählt wird:

```
if (color_0 > color_1) 
{
    // Four-color block: derive the other two colors. 
    
    // 00 = color_0, 01 = color_1, 10 = color_2, 11 = color_3
    // These 2-bit codes correspond to the 2-bit fields 
    // stored in the 64-bit block.
    color_2 = (2 * color_0 + color_1 + 1) / 3;
    color_3 = (color_0 + 2 * color_1 + 1) / 3;
}    
else
{ 
    // Three-color block: derive the other color.
    // 00 = color_0,  01 = color_1,  10 = color_2,  
    // 11 = transparent.
    // These 2-bit codes correspond to the 2-bit fields 
    // stored in the 64-bit block. 
    color_2 = (color_0 + color_1) / 2;    
    color_3 = transparent;    

}
```

Es wird empfohlen, dass Sie die RGBA-Komponenten des Transparenzpixels vor dem Vermischen auf 0 (null) setzen.

Die folgenden Tabellen zeigen das Speicherlayout für den 8-Byte-Block. Es wird vorausgesetzt, dass der erste Index der Y-Koordinate entspricht und der zweite Index der X-Koordinate entspricht. Beispielsweise bezieht sich Texel\ [1\]\[2\] auf das Texturzuordnungspixel bei (x,y) = (2,1).

Im folgenden findet sich das Speicherlayout für den 8-Byte-Block (64-Bit):

| Word-Adresse | 16-Bit-Word    |
|--------------|----------------|
| 0            | Farbe\_0       |
| 1            | Farbe\_1       |
| 2            | Bitmap-Word\_0 |
| 3            | Bitmap Word\_1 |

 

Farbe\_0 und Farbe\_1, die Farben der beiden Extreme sind wie folgt angeordnet:

| Bits        | Farbe                 |
|-------------|-----------------------|
| 4:0 (LSB\*) | Blau-Komponente  |
| 10:5        | Grün-Komponente |
| 15:11       | Rot-Komponente   |

 

\*niederwertigstes Bit

Bitmap-Word\_0 wird wie folgt dargestellt:

| Bits          | Texel           |
|---------------|-----------------|
| 1:0 (LSB)     | Texel\[0\]\[0\] |
| 3:2           | Texel\[0\]\[1\] |
| 5:4           | Texel\[0\]\[2\] |
| 7:6           | Texel\[0\]\[3\] |
| 9:8           | Texel\[1\]\[0\] |
| 11:10         | Texel\[1\]\[1\] |
| 13:12         | Texel\[1\]\[2\] |
| 15:14 (MSB\*) | Texel\[1\]\[3\] |

 

\*höchstwertiges Bit (MSB)

Bitmap-Word\_1 wird wie folgt dargestellt:

| Bits        | Texel           |
|-------------|-----------------|
| 1:0 (LSB)   | Texel\[2\]\[0\] |
| 3:2         | Texel\[2\]\[1\] |
| 5:4         | Texel\[2\]\[2\] |
| 7:6         | Texel\[2\]\[3\] |
| 9:8         | Texel\[3\]\[0\] |
| 11:10       | Texel\[3\]\[1\] |
| 13:12       | Texel\[3\]\[2\] |
| 15:14 (MSB) | Texel\[3\]\[3\] |

 

## <a name="span-idexampleofopaquecolorencodingspanspan-idexampleofopaquecolorencodingspanspan-idexampleofopaquecolorencodingspanexample-of-opaque-color-encoding"></a><span id="Example_of_Opaque_Color_Encoding"></span><span id="example_of_opaque_color_encoding"></span><span id="EXAMPLE_OF_OPAQUE_COLOR_ENCODING"></span>Beispiel für eine undurchsichtige Codierung


Als Beispiel für die undurchsichtige Codierung wird davon ausgegangen, dass die Farben rot und schwarz an den Extremen liegen. Rot ist Farbe\_0 und schwarz ist Farbe\_1. Es gibt vier interpolierte Farben, die den einheitlich verteilten Verlauf dazwischen bilden. Um die Werte für die 4x4-Bitmap zu ermitteln, werden die folgenden Berechnungen verwendet:

```
00 ? color_0
01 ? color_1
10 ? 2/3 color_0 + 1/3 color_1
11 ? 1/3 color_0 + 2/3 color_1
```

Die Bitmap sieht dann wie im folgenden Diagramm aus.

![Diagramm des erweiterten Bitmap Layouts](images/colors2.png)

Dies sieht wie die nachstehend dargestellten Reihe von Farben aus.

**Hinweis:**  In einem Bild wird Pixel (0,0) oben links angezeigt.

 

![Abbildungeines undurchsichtig codierten Farbverlaufs](images/redsquares.png)

## <a name="span-idexampleof1bitalphaencodingspanspan-idexampleof1bitalphaencodingspanspan-idexampleof1bitalphaencodingspanexample-of-1-bit-alpha-encoding"></a><span id="Example_of_1_Bit_Alpha_Encoding"></span><span id="example_of_1_bit_alpha_encoding"></span><span id="EXAMPLE_OF_1_BIT_ALPHA_ENCODING"></span>Beispiel einer 1-Bit-Alpha-Kodierung


Dieses Format wird ausgewählt, wenn die vorzeichenlose 16-Bit-Ganzzahl, Farbe\_0, kleiner ist als die vorzeichenlose 16-Bit-Ganzzahl, Farbe\_1. Ein Beispiel, in dem dieses Format verwendet werden kann, sind Blätter an einem Baum, dargestellt gegen einen blauen Himmel. Während drei Grünabstufungen weiterhin für die Blätter verfügbar sind, können einige Texel als transparent gekennzeichnet werden. Zwei Farben fixieren die Extreme und die dritte Farbe ist eine interpolierte Farbe.

Die nachstehende Abbildung ist ein Beispiel für ein solches Bild.

![Abbildungder 1-Bit-Alpha-Codierung](images/greenthing.png)

Wird das Bild weiß dargestellt, wäre das Texel als transparent codiert. Die RGBA-Komponenten der transparenten Texel sollten vor dem Vermischen auf NULL gesetzt werden.

Die Bitmap-Codierung für die Farben und die Transparenz wird unter Anwendung der folgenden Berechnungen bestimmt.

```
00 ? color_0
01 ? color_1
10 ? 1/2 color_0 + 1/2 color_1
11   ?   Transparent
```

Die Bitmap sieht dann wie im folgenden Diagramm aus.

![Diagramm des erweiterten Bitmap Layouts](images/colors3.png)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Komprimierte Texturressourcen](compressed-texture-resources.md)

 

 




