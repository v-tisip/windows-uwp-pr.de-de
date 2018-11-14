---
title: Emissive-Lighting
description: Beim Emissive-Lighting handelt es sich um eine Beleuchtung, die von einem Objekt ausgeht (z. B. ein Glühen).
ms.assetid: 262EB9E2-DF96-401F-93D6-51A7BB60074B
keywords:
- Emissive-Lighting
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9ce2082479261cd96fb1c5bafd5f2df06bf6f239
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6459515"
---
# <a name="emissive-lighting"></a>Emissive-Lighting


*Ausstrahlende Beleuchtung* ist Licht, das ein Objekt ausstrahlt; beispielsweise ein Leuchten. Durch das Ausstrahlen erscheint ein angezeigtes Objekt als selbstleuchtend. Die Emissionen wirken sich auf die Farbe eines Objektes aus. Sie können beispielsweise ein dunkles Material heller und teilweise in der emittierten Farbe erscheinen lassen.

Das Emissive-lighting wird durch einen einzigen Faktor beschrieben.

Emissive-Lighting = Cₑ

Dabei gilt Folgendes:

| Parameter | Standardwert | Typ                                                                 | Beschreibung     |
|-----------|---------------|----------------------------------------------------------------------|-----------------|
| Cₑ        | (0,0,0,0)     | Rot, Grün, Blau und Alphatransparenz (alle Gleitkommawerte) | Emissionsfarbe. |

 

Der Wert für Cₑ ist entweder Farbe 1 oder Farbe 2. Wenn die Vertex-Farbe nicht angegeben wird, wird das Emissive-Materialfarbe verwendet.

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


In diesem Beispiel wird das Objekt über die Ambiente-Beleuchtung der Szene und die Ambiente-Farbe des Materials eingefärbt.

Entsprechend der Gleichung ist die resultierende Farbe der Objekt-Vertizes die Materialfarbe.

Die folgende Abbildungzeigt die Materialfarbe (Grün). Die Emissive-Beleuchtung beleuchtet alle Objekt-Vertizes mit derselben Farbe. Sie ist nicht von der Vertex-Normalen oder der Beleuchtungsrichtung abhängig. Daher sieht die Kugel wie ein 2D-Kreis aus – denn es gibt keine Schattierung für die Oberfläche des Objekts.

![Abbildungeiner grünen Kugel](images/lighte.jpg)

Die folgende Abbildungzeigt, wie sich die Emissive-Beleuchtung mit den anderen drei Beleuchtungstypen mischt. Auf der rechten Seite der Kugel ist eine Mischung aus grüne Emissive- und roter Ambient-Beleuchtung sichtbar. Auf der linken Seite der Kugel mischt sich die grüne Emissive-Beleuchtung mit einer Diffuse-Beleuchtung und erzeugt so einen roten Farbverlauf. Das Glanzlicht in der Mitte ist Weiß. Es sorgt für einen gelben Ring, denn der Wert der Glanz-Beleuchtung fällt stark ab. Dies sorgt dafür, dass die Werte für die Ambiente-, Diffuse- und Emissions-Beleuchtung gemischt werden. So entsteht das Gelb.

![Abbildungeiner grüne Kugel mit Emissive-Beleuchtung](images/lightadse.jpg)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Beleuchtungsmathematik](mathematics-of-lighting.md)

 

 




