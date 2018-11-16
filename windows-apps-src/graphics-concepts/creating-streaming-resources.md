---
title: Erstellen von Streamingressourcen
description: Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource laut Kennzeichen angeben, dass die Ressource eine Streamingressource ist.
ms.assetid: B3F3E43C-54D4-458C-9E16-E13CB382C83F
keywords:
- Erstellen von Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: a796897aa786283499c25b0f405e302feeb5f938
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6970308"
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
<td align="left"><p><a href="mappings-are-into-a-tile-pool.md">Zuordnungen in einen Kachelpool</a></p></td>
<td align="left"><p>Beim Erstellen einer Ressource als Streaming-Ressource stammen die Kacheln, die die Ressource bilden, aus Speicherorten in einem Kachelpool. Ein Kachelpool ist ein Arbeitsspeicherpool (der durch eine oder mehrere Zuordnungen hinter den Kulissen unterstützt wird und von der Anwendung nicht sichtbar ist).</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resource-creation-parameters.md">Parameter für das Erstellen von Streamingressourcen</a></p></td>
<td align="left"><p>Es gibt einige Einschränkungen für den Direct3D-Ressourcentyp, den Sie als Streamingressource erstellen können.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="tile-pool-creation-parameters.md">Parameter zum Erstellen des Kachelpools</a></p></td>
<td align="left"><p>Verwenden Sie die Parameter in diesem Abschnitt, um beim Erstellen eines Puffers den Kachelpool zu definieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resource-cross-process-and-device-sharing.md">Geräte- und prozessübergreifende Streamingressourcen</a></p></td>
<td align="left"><p>Kachelpools können mit anderen Prozessen wie herkömmliche Ressourcen geteilt werden. Streamingressourcen, die auf Kachelpools verweisen, können nicht auf allen Geräten und Prozessen freigegeben werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="operations-available-on-streaming-resources.md">Vorgänge für Streamingressourcen</a></p></td>
<td align="left"><p>Dieser Abschnitt enthält Vorgänge, die Sie auf Streamingressourcen ausführen können.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="operations-available-on-tile-pools.md">Vorgänge in Kachelpools</a></p></td>
<td align="left"><p>Vorgänge im Kachelpool umfassen das Ändern der Größe eines Kachelpools, das Anbieten von Ressourcen (Speicherplatz vorübergehend für das System für den gesamten Kachelpool abgeben) und die Freigabe von Ressourcen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="how-a-streaming-resource-s-area-is-tiled.md">So unterteilen Sie den Bereich einer Streamingressource</a></p></td>
<td align="left"><p>Wenn Sie eine Streamingressource erstellen, bestimmen Dimensionen, Größe des Formats und Anzahl der Mipmaps und/oder Array-Segmente (falls zutreffend) die Anzahl der erforderlichen Kacheln, um die gesamte Oberfläche zu sichern.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Streamingressourcen](streaming-resources.md)

 

 




