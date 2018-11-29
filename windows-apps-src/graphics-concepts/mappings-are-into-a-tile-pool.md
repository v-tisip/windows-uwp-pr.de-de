---
title: Zuordnungen erfolgen in einen Kachelpool
description: Beim Erstellen einer Ressource als Streaming-Ressource stammen die Kacheln, die die Ressource bilden, aus Speicherorten in einem Kachelpool. Ein Kachelpool ist ein Speicherpool (gesichert durch eine oder mehrere Zuordnungen im Hintergrund – nicht sichtbar für die Anwendung).
ms.assetid: 58B8DBD5-62F5-4B94-8DD1-C7D57A812185
keywords:
- Zuordnungen erfolgen in einen Kachelpool
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a0474345e21161e76fbfeebe0086e5d433b2d219
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8191859"
---
# <a name="mappings-are-into-a-tile-pool"></a>Zuordnungen erfolgen in einen Kachelpool


Beim Erstellen einer Ressource als Streaming-Ressource stammen die Kacheln, die die Ressource bilden, aus Speicherorten in einem Kachelpool. Ein Kachelpool ist ein Speicherpool (gesichert durch eine oder mehrere Zuordnungen im Hintergrund – nicht sichtbar in der Anwendung). Das Betriebssystem und der Bildschirmtreiber verwalten diesen Speicherpool und der Speicherbedarf ist für eine Anwendung leicht verständlich. Streaming-Ressourcen ordnen 64-KB-Regionen zu, indem sie auf Speicherorte in einem Kachelpool verweisen. Eine negative Auswirkung dieser Einstellung ist, dass mehrere Ressourcen die gleichen Kacheln miteinander teilen und wiederverwenden und ferner die gleichen Kacheln an verschiedenen Stellen innerhalb einer Ressource wiederverwendet werden können, wenn gewünscht.

Die Kosten für die Flexibilität des Auffüllens der Kacheln für eine Ressource aus einem Kachelpool besteht darin, dass die Ressource die Zuordnung definieren und verwalten muss, welche der Kacheln im Kachelpool die für die Ressource benötigten Kacheln darstellen. Kachelzuordnungen können geändert werden. Darüber hinaus müssen nicht alle Kacheln in einer Ressource gleichzeitig zugeordnet werden; eine Ressource kann **NULL** Zuordnungen aufweisen. Eine **NULL**-Zuordnung definiert eine Kachel aus Sicht der auf diese zugreifenden Ressource als nicht verfügbar.

Mehrere Kachelpools können erstellt werden und eine beliebige Anzahl von Streaming-Ressourcen kann gleichzeitig in jeden beliebigen Kachelpool zuordnen. Kachelpools können auch vergrößert oder verkleinert werden. Weitere Informationen finden Sie unter [Ändern der Größe des Kachelpools](tile-pool-resizing.md). Eine Einschränkung zur Vereinfachung der Implementierung von Bildschirmtreibern und der Laufzeit liegt darin, dass eine Streaming-Ressource nur Zuordnungen in mindestens einem Kachelpool zu einem Zeitpunkt aufweisen kann (im Gegensatz zum gleichzeitigen Zuordnen in mehrere Kachelpools).

Die mit einer Streaming-Ressource assoziierte Speicherkapazität (d.h. unabhängig vom Kachelpoolspeicher) ist etwa proportional zur Anzahl der Kacheln, die tatsächlich zu einem bestimmten Zeitpunkt dem Pool zugeordnet sind. Hinsichtlich der Hardware läuft diese Tatsache auf eine Skalierung des Speicherbedarfs für Seitentabellen hinaus, ungefähr in der Größe der zugeordneten Kacheln (z.B. über ein Seitentabellenschema mit mehreren Ebenen, ggf.).

Den Kachelpool kann man sich als eine vollständige Software-Abstraktion vorstellen, durch die Direct3D-Anwendungen wirksam in die Lage versetzt werden, die Seitentabellen auf den Grafikprozessor (GPU) zu programmieren, ohne die Implementierungsdetails auf niedriger Ebene wissen zu müssen (oder mit Zeigeradressen direkt umgehen zu müssen). Kachelpools wenden keine zusätzlichen Ebenen der Dereferenzierung in der Hardware an. Optimierungen einer Seitentabelle mit einer Ebene, die Konstrukte wie Seitenverzeichnisse verwendet, sind unabhängig vom Kachelpoolkonzept.

Lassen Sie uns herausfinden, welchen Speicherplatz die Seitentabelle im ungünstigsten Fall benötigen könnte (wenngleich Implementierungen in der Praxis einen Speicherplatz benötigen, der nur etwa proportional zu den Zuordnungen ist).

Nehmen wir an, dass jeder Seitentabelleneintrag 64 Bits umfasst.

Für die ungünstigste Tabelle enthält die Größe der Seitentabelle für eine einzelne Fläche, die Ressourcengrenzen in Direct3D11, nehmen streaming-Ressource mit einem Format von 128 Bit pro Element (z. B. eine RGBA-Gleitkommazahl), also eine 64 KB große Kachel nur 4096 Pixel. Die maximal unterstützte [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526)-Größe von 16384\*16384\*2048 (jedoch mit nur einer Mip-Map) würde etwa 1 GB Speicherplatz in der Seitentabelle erfordern, wenn vollständig gefüllt (ohne Mip-Maps), bei Verwendung von 64-Bit-Einträgen. Durch das Hinzufügen von Mip-Maps würde der Speicherbedarf der vollständig zugeordneten (ungünstigster Fall) Seitetabelle um etwa ein Drittel anwachsen, auf etwa 1,3 GB.

Dieser Fall würde einen Zugriff auf etwa 10,6 Terabyte adressierbaren Speicher erlauben. Möglicherweise gibt es jedoch eine Grenze für die Menge an adressierbarem Speicher, wodurch sich diese Mengen verringern würden, vielleicht auf einen Wert im Terabytebereich.

Ein weiterer zu berücksichtigender Fall ist eine einzelne [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) Streaming-Ressource von 16384\*16384 mit einem Format von 32 Bit pro Element, einschließlich Mip-Maps. Der Speicherplatz in einer vollständig ausgefüllten Seitentabelle läge bei etwa 170 KB, bei 64-Bit-Einträgen.

Abschließend sollten Sie ein Beispiel unter Verwendung eines BC-Formates betrachten, sagen wir BC7 mit 128 Bits pro Kachel von 4x4 Pixeln. Dies entspricht einem Byte pro Pixel. Ein [**Texture2DArray**](https://msdn.microsoft.com/library/windows/desktop/ff471526) von 16384\*16384\*2048, einschließlich Mip-Maps, würde etwa 85 MB erfordern, um diesen Speicherplatz in einer Seitentabelle vollständig auszufüllen. Das ist gar nicht schlecht, vor allem unter Berücksichtigung der Tatsache, dass dadurch eine Streaming-Ressource 550 Gigapixel umfassen kann (512 GB Speicherplatz in diesem Fall).

In der Praxis würden bei Weitem nicht so umfangreiche vollständige Zuordnungen definiert, angesichts der Tatsache, dass die Menge des verfügbaren physischen Speichers bei Weitem nicht zulassen würde, dass gleichzeitig so viel zugeordnet und verwiesen wird. Mit einem Kachelpool könnten die Anwendungen sich jedoch dafür entscheiden, Kacheln wiederzuverwenden (beispielsweise das einfache Wiederverwenden einer "schwarzen" Kachel für große schwarze Bereiche in einem Bild) – und dadurch den Kachelpool (d.h. Seitentabellenzuordnungen) als Tool für die Speicherkomprimierung effizient nutzen.

Der anfängliche Inhalt der Seitentabelle ist **NULL** für alle Einträge. Anwendungen können ferner keine anfänglichen Daten für die Speicherinhalte der Oberfläche weiterleiten, da dies ohne Speichersicherung beginnt.

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
<td align="left"><p><a href="tile-pool-creation.md">Erstellung eines Kachelpools</a></p></td>
<td align="left"><p>Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße jedes kachelpools ist auf Direct3D11s Ressourcengröße beschränkt, die ungefähr 1/4 GPU-Arbeitsspeicher beträgt beschränkt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="tile-pool-resizing.md">Ändern der Größe des Kachelpools</a></p></td>
<td align="left"><p>Ändern der Größe eines Kachelpools zum Vergrößern eines Kachelpools, wenn die Anwendung mehr Arbeit der Streaming-Ressourcen benötigt, welche in diese zuordnen, bzw. zum Verkleinern des Kachelpools, wenn weniger Speicherplatz benötigt wird.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="hazard-tracking-versus-tile-pool-resources.md">Gefahrennachverfolgung im Vergleich mit den Kachelpoolressourcen</a></p></td>
<td align="left"><p>Bei Nicht-Streaming-Ressourcen kann Direct3D bestimmte Gefahrenbedingungen während der Wiedergabe verhindern, da aber die Nachverfolgung von Gefahren auf einer Kachelebene für Streaming-Ressourcen erfolgen würde, kann das Nachverfolgen von Gefahrenbedingungen während der Wiedergabe von Streaming-Ressourcen möglicherweise zu teuer sein.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Erstellen von Streamingressourcen](creating-streaming-resources.md)

 

 




