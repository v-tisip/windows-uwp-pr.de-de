---
title: Streamingressourcen
description: Streamingressourcen sind große logische Ressourcen, die wenig physischen Speicher belegen. Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt. Streamingressourcen wurden früher als unterteilte Ressourcen bezeichnet.
ms.assetid: 04F0486E-4B71-4073-88DA-2AF505F4F0C1
keywords:
- Streamingressourcen
- Ressourcen, Streaming
- Ressourcen, unterteilte
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: f269b352dc3d7ea7c63c04fdbfc487fae490bf1e
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1653659"
---
# <a name="streaming-resources"></a>Streamingressourcen


*Streamingressourcen* sind große logische Ressourcen, die wenig physischen Speicher belegen.. Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt. Streamingressourcen wurden früher als *unterteilte Ressourcen* bezeichnet.

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
<td align="left"><p><a href="the-need-for-streaming-resources.md">Die Notwendigkeit für Streamingressourcen</a></p></td>
<td align="left"><p>Streamingressourcen sind erforderlich, damit der GPU-Speicher nicht unnötig durch die Speicherung von Oberflächenbereichen belegt wird, auf die nicht zugegriffen wird, und um der Hardware mitzuteilen, wie angrenzende Kacheln gefiltert werden sollen.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="creating-streaming-resources.md">Erstellen von Streamingressourcen</a></p></td>
<td align="left"><p>Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource ein Flag festlegen, das die Ressource als Streamingressource kennzeichnet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="pipeline-access-to-streaming-resources.md">Pipelinezugriff auf Streamingressourcen</a></p></td>
<td align="left"><p>Streamingressourcen können in Shaderressourcenansichten (SRV), Renderzielansichten (RTV), Tiefenschablonenansichten (DSV) und in unsortierten Zugriffsansichten (UAV) sowie in bestimmten Bindungen ohne Ansichten, z.B. Vertex-Pufferbindungen, verwendet werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="streaming-resources-features-tiers.md">Ebenen der Features von Streamingressourcen</a></p></td>
<td align="left"><p>Direct3D unterstützt Streamingressourcen in drei Funktionsebenen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Lernanleitung für Direct3D-Grafiken](index.md)

[Ressourcen](resources.md)

 

 




