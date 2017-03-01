---
title: Streamingressourcen
description: "Streamingressourcen sind große logische Ressourcen, die wenig physischen Speicher belegen. Anstatt eine gesamte große Ressource zu übergeben, werden je nach Bedarf kleine Teile der Ressource gestreamt. Streamingressourcen wurden früher als unterteilte Ressourcen bezeichnet."
ms.assetid: 04F0486E-4B71-4073-88DA-2AF505F4F0C1
keywords:
- Streamingressourcen
- Ressourcen, Streaming
- Ressourcen, unterteilte
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 7bb706c94d26b1d27e7b9bf94ca3cfa7a57b41a6
ms.lasthandoff: 02/07/2017

---

# <a name="streaming-resources"></a>Streamingressourcen


*Streamingressourcen* sind große logische Ressourcen, die wenig physischen Speicher belegen.. Anstatt eine gesamte große Ressource zu übergeben, werden je nach Bedarf kleine Teile der Ressource gestreamt. Streamingressourcen wurden früher als *unterteilte Ressourcen* bezeichnet.

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
<td align="left"><p>[Die Notwendigkeit für Streamingressourcen](the-need-for-streaming-resources.md)</p></td>
<td align="left"><p>Streamingressourcen sind erforderlich, damit der GPU-Speicher nicht unnötig durch die Speicherung von Oberflächenbereichen belegt wird, auf die nicht zugegriffen wird, und um der Hardware mitzuteilen, wie angrenzende Kacheln gefiltert werden sollen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Erstellen von Streamingressourcen](creating-streaming-resources.md)</p></td>
<td align="left"><p>Streamingressourcen werden erstellt, indem Sie beim Erstellen einer Ressource ein Flag festlegen, das die Ressource als Streamingressource kennzeichnet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Pipelinezugriff auf Streamingressourcen](pipeline-access-to-streaming-resources.md)</p></td>
<td align="left"><p>Streamingressourcen können in Shaderressourcenansichten (SRV), Renderzielansichten (RTV), Tiefenschablonenansichten (DSV) und in unsortierten Zugriffsansichten (UAV) sowie in bestimmten Bindungen ohne Ansichten, z. B. Vertex-Pufferbindungen, verwendet werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md)</p></td>
<td align="left"><p>Direct3D unterstützt Streamingressourcen in drei Funktionsebenen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Lernanleitung für Direct3D-Grafiken](index.md)

[Ressourcen](resources.md)

 

 





