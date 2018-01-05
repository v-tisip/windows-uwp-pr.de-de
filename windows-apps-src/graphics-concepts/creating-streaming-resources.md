---
title: Erstellen von Streamingressourcen
description: Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource laut Kennzeichen angeben, dass die Ressource eine Streamingressource ist.
ms.assetid: B3F3E43C-54D4-458C-9E16-E13CB382C83F
keywords: Erstellen von Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: a38cdd218fbca47bde00dc7395b3bf1b3e00606a
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-streaming-resources"></a>Erstellen von Streamingressourcen


Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource laut Kennzeichen angeben, dass die Ressource eine Streamingressource ist.

Einschränkungen für das Erstellen einer Ressource als Streamingressource werden unter [Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md) beschrieben.

Beim Erstellen der Ressource wird dem Grafiksystem ein Nicht-Streamingressourcenspeicher zugewiesen, z.B. bei der Zuordnung für ein Array von 2D-Texturen.

Wenn eine Streamingressource erstellt wird, weist das Grafiksystem dem Inhalt der Ressource keinen Speicher hinzu. Wenn eine Anwendung eine Streamingressource erstellt, reserviert das Grafiksystem stattdessen einen Adressbereich nur für die nebeneinander angeordnete Oberfläche und ermöglicht dann der Anwendung, die Zuordnung der Kacheln zu steuern. Die „Zuordnung” einer Kachel ist der physische Standort im Arbeitsspeicher, auf den die logische Kachel in einer Ressource verweist (oder **NULL** für eine nicht zugeordnete Kachel).

Verwechseln Sie dieses Konzept nicht mit der Zuordnung einer Direct3D-Ressource für den CPU-Zugriff - trotz des gleichen Namens sind diese komplett unabhängig voneinander. Sie können die Zuordnung jeder einzelnen Kachel nach Bedarf definieren und ändern. Nicht alle Kacheln für eine Oberfläche müssen zu einem bestimmten Zeitpunkt zugeordnet werden, wodurch die Größe des verfügbaren Arbeitsspeichers effektiv verwaltet wird.

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
<td align="left"><p>[Zuordnungen in einen Kachelpool](mappings-are-into-a-tile-pool.md)</p></td>
<td align="left"><p>Beim Erstellen einer Ressource als Streamingressource stammen die Kacheln, die die Ressource bilden, aus zugeordneten Speicherorten in einem Pool. Ein Kachelpool ist ein Arbeitsspeicherpool (der durch eine oder mehrere Zuordnungen hinter den Kulissen unterstützt wird und von der Anwendung nicht sichtbar ist).</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md)</p></td>
<td align="left"><p>Es gibt einige Einschränkungen für den Direct3D-Ressourcentyp, den Sie als Streamingressource erstellen können.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Parameter zum Erstellen des Kachelpools](tile-pool-creation-parameters.md)</p></td>
<td align="left"><p>Verwenden Sie die Parameter in diesem Abschnitt, um beim Erstellen eines Puffers den Kachelpool zu definieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Geräte- und prozessübergreifende Streamingressourcen](streaming-resource-cross-process-and-device-sharing.md)</p></td>
<td align="left"><p>Kachelpools können von anderen Prozessen wie herkömmliche Ressourcen freigegeben werden. Streamingressourcen, die auf Kachelpools verweisen, können nicht auf allen Geräten und Prozessen freigegeben werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Vorgänge für Streamingressourcen](operations-available-on-streaming-resources.md)</p></td>
<td align="left"><p>Dieser Abschnitt enthält Vorgänge, die Sie auf Streamingressourcen ausführen können.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Vorgänge in Kachelpools](operations-available-on-tile-pools.md)</p></td>
<td align="left"><p>Vorgänge im Kachelpool umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Speicherplatz vorübergehend für das System für den gesamten Kachelpool abgeben) und die Freigabe von Ressourcen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[So unterteilen Sie den Bereich einer Streamingressource](how-a-streaming-resource-s-area-is-tiled.md)</p></td>
<td align="left"><p>Wenn Sie eine Streamingressource erstellen, bestimmen Dimensionen, Größe des Formats und Anzahl der Mipmaps und/oder Array-Segmente (falls zutreffend) die Anzahl der erforderlichen Kacheln, um die gesamte Oberfläche zu sichern.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Streamingressourcen](streaming-resources.md)

 

 




