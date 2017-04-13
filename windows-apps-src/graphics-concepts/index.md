---
title: "Lernanleitung für Direct3D-Grafiken"
description: Beschreibt das Grafikkonzept, auf dem Microsoft Direct3D aufgebaut ist.
ms.assetid: c3850a92-4d05-4f72-bf0f-6a0c79e841eb
keywords: "Lernanleitung für Direct3D-Grafiken"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: 9d46a13844fafc5f517fce16c39e33257ff8e9a5
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="direct3d-graphics-learning-guide"></a>Lernanleitung für Direct3D-Grafiken


Beschreibt das Grafikkonzept, auf dem Microsoft Direct3D aufgebaut ist. Dieser Dokumentationssatz ist weitgehend unabhängig von der Direct3D-Version. Er wurde für Grafik-Entwickler erstellt, die mehr Hintergrundinformationen benötigen, als in der versionsspezifischen API-Dokumentation bereit gestellt wird.

## <a name="span-idin-this-sectionspanin-this-section"></a><span id="in-this-section"></span>In diesem Abschnitt


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
<td align="left"><p>[Koordinatensystem und Geometrie](coordinate-systems-and-geometry.md)</p></td>
<td align="left"><p>Das Programmieren von Direct3D-Anwendungen setzt Kenntnisse von geometrischen 3D-Prinzipien voraus. Dieser Abschnitt stellt die wichtigsten geometrischen Konzepte zum Erstellen von 3D-Szenen vor.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Vertex- und Indexpuffer](vertex-and-index-buffers.md)</p></td>
<td align="left"><p><em>Scheitelpunktpuffer</em> sind Speicherpuffer, die Scheitelpunktdaten enthalten. Scheitelpunkte in einem Scheitelpunktpuffer werden verarbeitet, um Transformation, Beleuchtung und Zuschneiden auszuführen. <em>Indexpuffer</em> sind Speicherpuffer mit Indexdaten, die Ganzzahl-Offsets in Vertexpuffer darstellen, und zum Rendern von Grundtypen verwendet werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Geräte](devices.md)</p></td>
<td align="left"><p>Ein Direct3D-Gerät stellt die Rendering-Komponente von Direct3D dar. Ein Gerät kapselt und speichert den Renderstatus, führt Transformationen und Beleuchtungsvorgänge aus, und rastert ein Bild zu einer Oberfläche.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Beleuchtung](lights-and-materials.md)</p></td>
<td align="left"><p>Licht wird zum Beleuchten von Objekten in einer Szene verwendet. Die Farbe jedes Objektscheitelpunkts basiert auf der aktuellen Texturzuordnung, Scheitelpunktfarben und Lichtquellen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Tiefen- und Schablonenpuffer](depth-and-stencil-buffers.md)</p></td>
<td align="left"><p>Ein <em>Tiefenpuffer</em> speichert Tiefeninformationen, um zu steuern, welche Bereiche eines Polygons gerendert oder verborgen werden. Ein <em>Schablonenpuffer</em> wird verwendet, um Pixel in einem Bild zu maskieren und um Spezialeffekte, wie Zusammensetzung, Auflösungen, Rasterungen, Ein- und Ausblenden und Streifbewegungen, Umrisse und Silhouetten sowie das Feature „zweitseitige Schablone“ zu erzeugen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Texturen](textures.md)</p></td>
<td align="left"><p>Texturen sind ein mächtiges Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen. Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern einfach auf erweiterte Texturtechniken zuzugreifen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Grafik-Pipeline](graphics-pipeline.md)</p></td>
<td align="left"><p>Die Direct3D-Grafik-Pipeline wurde entwickelt, um Grafiken für Gaming-Anwendungen in Echtzeit zu generieren. Datenflüsse vom Eingang zum Ausgang durch jede konfigurierbare oder programmierbare Phase</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Ansichten](views.md)</p></td>
<td align="left"><p>Der Begriff &quot;Ansicht&quot; wird für &quot;Daten im erforderlichen Format&quot; verwendet. Eine Konstantenpufferansicht (CBV) beispielweise, sind ordnungsgemäß formatierte, konstante Pufferdaten. Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Berechnungs-Pipeline](compute-pipeline.md)</p></td>
<td align="left"><p>Die Direct3D-Berechnungs-Pipeline wurde entwickelt, um Berechnungen zu erledigen, die meist parallel mit der Grafik-Pipeline ausgeführt werden können.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Ressourcen](resources.md)</p></td>
<td align="left"><p>Eine Ressource ist ein Bereich im Speicher, auf den die Direct3D-Pipeline zugreifen kann. Damit die Pipeline effizient auf den Speicher zugreifen kann, müssen für die Pipeline bereitgestellte Daten (wie z.B. Input-Geometrie, Shader-Ressourcen und Texturen) in einer Ressource gespeichert werden. Es gibt zwei Arten von Ressourcen, aus denen alle Direct3D-Ressourcen abgeleitet sind: ein Puffer oder eine Textur. Bis zu 128 Ressourcen können für jede Pipeline-Phase aktiv sein.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Streaming-Ressourcen](streaming-resources.md)</p></td>
<td align="left"><p><em>Streamingressourcen</em> sind große logische Ressourcen, die wenig physischen Speicher belegen.. Anstatt die gesamte große Ressource zu übergeben, werden nur kleine Teile der Ressource bei Bedarf gestreamt. Streaming-Ressourcen wurden vorher als <em>unterteilte Ressourcen</em> bezeichnet.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Anhänge](appendix.md)</p></td>
<td align="left"><p>Diese Abschnitte enthalten tiefergehende technische Details.</p></td>
</tr>
</tbody>
</table>

 

 

 
