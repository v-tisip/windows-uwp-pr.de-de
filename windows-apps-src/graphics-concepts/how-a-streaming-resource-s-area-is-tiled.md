---
title: So strukturieren Sie den Bereich einer Streamingressource
description: Wenn Sie eine Streamingressource erstellen, bestimmen die Dimensionen, die Formatelementgröße und die Anzahl der Mipmaps und/oder Array-Slices (falls zutreffend) die Anzahl der Tiles, die erforderlich sind, um die gesamte Oberfläche darzustellen.
ms.assetid: 3485FD8D-2A06-4B0A-8810-ECF37736F94B
keywords:
- So strukturieren Sie den Bereich einer Streamingressource
- Ressourcenbereich, strukturiert
- Größentabellen, Ressourcen, strukturiert
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 49ad096389c27fb65970424569c7c1d2ea0cb097
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6183535"
---
# <a name="how-a-streaming-resources-area-is-tiled"></a>So strukturieren Sie den Bereich einer Streamingressource


Wenn Sie eine Streamingressource erstellen, bestimmen die Dimensionen, die Formatelementgröße und die Anzahl der Mipmaps und/oder Array-Slices (falls zutreffend) die Anzahl der Tiles, die erforderlich sind, um die gesamte Oberfläche darzustellen. Das Pixel/Byte-Layout in den Tiles wird durch die Implementierung bestimmt. Die Anzahl von Pixeln, die in eine Tile passen, ist je nach Formatelementgröße konstant und identisch, ob Sie einen standardmäßigen Swizzle verwenden oder nicht.

Die Anzahl von Tiles, die bei einer bestimmten Oberflächengröße und Formatelementbreite verwendet wird, ist klar definiert und kann den Tabellen in den folgenden Abschnitten entnommen werden. Für Ressourcen, die Mipmaps enthalten, oder für Fälle, in denen eine Tile nicht von der Oberfläche ausgefüllt wird, gelten einige Einschränkungen. Informationen dazu finden Sie unter [Mipmap-Verpackung](mipmap-packing.md).

Verschiedene Streamingressourcen dürfen auf identische Speicher mit verschiedenen Formaten zeigen, solange sich Anwendungen nicht auf die Ergebnisse verlassen, wenn in einen Speicher mit einem Format geschrieben und mit einem anderen gelesen wird Anwendungen können sich jedoch auf die Ergebnisse verlassen, wenn in einen Speicher mit einem Format geschrieben und mit einem anderen gelesen wird, sofern die Formate zu derselben Formatfamilie gehören (also dasselbe typlose übergeordnete Format besitzen). Beispielsweise sind DXGI\_FORMAT\_R8G8B8A8\_UNORM und DXGI\_FORMAT\_R8G8B8A8\_UINT untereinander kompatible, aber nicht mit DXGI\_FORMAT\_R16G16\_UNORM.

Eine Ausnahme sind definierte Übergänge von Daten von einem Format in ein anderes: Wenn die Bits einer Tile alle den Wert 0 haben, kann die Tile mit jedem Format verwendet werden, das diese Speicherinhalte als 0 interpretiert (unabhängig vom Speicherlayout). Somit kann ein Tile-Inhalt, der mit dem Format DXGI\_FORMAT\_R8\_UNORM auf 0x00 gesetzt (gelöscht) wurde, mit einem Format wie DXGI\_FORMAT\_R32G32\_FLOAT verwendet werden, und der Inhalt scheint weiterhin (0.0f,0.0f) zu sein.

Das Layout der Daten in einer Tile ist nicht davon abhängig, wo sie in eine Ressource zugeordnet ist. Daher kann eine Tile beispielsweise gleichzeitig und mit einheitlichem Verhalten an verschiedenen Positionen einer Oberfläche verwendet werden.

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>Inhalt dieses Abschnitts


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Thema</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="texture2d-and-texture2darray-subresource-tiling.md">Strukturierung von Texture2D- und Texture2DArray-Unterressourcen</a></p></td>
<td align="left"><p>Diese Tabellen zeigen die Unterteilung von <a href="https://msdn.microsoft.com/library/windows/desktop/ff471525"><strong>Texture2D</strong></a>- und <a href="https://msdn.microsoft.com/library/windows/desktop/ff471526"><strong>Texture2DArray</strong></a>-Unterressourcen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="texture3d-subresource-tiling.md">Unterteilung von Texture3D-Unterressourcen</a></p></td>
<td align="left"><p>Diese Tabelle zeigt die Unterteilung von <a href="https://msdn.microsoft.com/library/windows/desktop/ff471562"><strong>Texture3D</strong></a>-Unterressourcen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="buffer-tiling.md">Pufferaufteilung</a></p></td>
<td align="left"><p>Eine <a href="introduction-to-buffers.md">Puffer</a>-Ressource ist in 64KB große Tiles unterteilt, mit Leerraum in der letzten Tile, wenn die Größe kein Vielfaches von 64KB ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="mipmap-packing.md">Mipmap-Verpackung</a></p></td>
<td align="left"><p>Eine Anzahl von Mips (pro Array-Slice) kann in eine Anzahl von Tiles verpackt werden, je nach den Dimensionen der Streamingressource, dem Format, der Anzahl der Mipmaps und der Array-Slices.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Erstellen von Streamingressourcen](creating-streaming-resources.md)

 

 




