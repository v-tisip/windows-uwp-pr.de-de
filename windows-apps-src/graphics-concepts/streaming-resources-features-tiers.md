---
title: Ebenen der Features von Streamingressourcen
description: Direct3D unterstützt Streamingressourcen in drei Featureebenen.
ms.assetid: 6AE7EA72-3929-4BB4-8780-F0CF26192D87
keywords:
- Ebenen der Features von Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: bc7d04a826bd8be0947e8d84ab8dbff6f67e8027
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7569715"
---
# <a name="streaming-resources-features-tiers"></a>Ebenen der Features von Streamingressourcen


Direct3D unterstützt Streamingressourcen in drei Featureebenen.

Ebene1 stellt grundlegende Funktionen für Streamingressourcen bereit.

Ebene2 fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.

Ebene3 fügt über Ebene2 hinausgehende Texture3D-Funktionen hinzu.

In den Versionen von Direct3D sind Abfragefunktionen zum Überprüfen der Hardware und der Treiberunterstützung für Streamingressourcen sowie der Ebene verfügbar.

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
<td align="left"><p><a href="tier-1.md">Ebene1</a></p></td>
<td align="left"><p>In diesem Abschnitt wird die Unterstützung für die Ebene1 beschrieben.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="tier-2.md">Ebene2</a></p></td>
<td align="left"><p>Die Unterstützung der Ebene2 für Streamingressourcen fügt über die Ebene1 hinausgehende Funktionen hinzu, z.B. Garantieren eines nicht gepackten Textur-Mipmap, wenn die Größe mindestens eine Standardkachelform beträgt, Shaderanweisungen zur Klammerung der Detailebene (Level-of-Detail, LOD) und zum Abrufen des Status des Shadervorgangs sowie das Lesen aus NULL-zugeordneten Kacheln behandeln, deren Samplingwert null ergab.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="tier-3.md">Ebene3</a></p></td>
<td align="left"><p>Ebene3 fügt zusätzlich zu den Funktionen der <a href="tier-2.md">Ebene2</a> die Unterstützung für Texture3D für Streamingressourcen hinzu.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Streamingressourcen](streaming-resources.md)

 

 




