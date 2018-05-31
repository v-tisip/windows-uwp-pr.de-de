---
title: Koordinatensysteme und Geometrie
description: Für das Programmieren von Direct3D-Anwendungen muss der Anwender mit geometrischen 3D-Prinzipien vertraut sein. In diesem Abschnitt werden die wichtigsten geometrischen Konzepte für das Erstellen von 3D-Szenen eingeführt.
ms.assetid: E82EB0A9-0678-496B-96B3-8993BA580099
keywords:
- Koordinatensysteme und Geometrie
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: cea4368ce995ce50726499b6c1c6875f83b72e7b
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1652329"
---
# <a name="coordinate-systems-and-geometry"></a>Koordinatensysteme und Geometrie


Für das Programmieren von Direct3D-Anwendungen muss der Anwender mit geometrischen 3D-Prinzipien vertraut sein. In diesem Abschnitt werden die wichtigsten geometrischen Konzepte für das Erstellen von 3D-Szenen eingeführt.

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
<td align="left"><p><a href="coordinate-systems.md">Koordinatensysteme</a></p></td>
<td align="left"><p>Normalerweise verwenden 3D-Grafikanwendungen einen von zwei Typen an kartesischen Koordinatensystemen: rechts- oder linkshändig. In beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="primitives.md">Grundtypen</a></p></td>
<td align="left"><p>Ein 3D- <em>Grundtyp</em> ist eine Sammlung von Scheitelpunkten, die eine 3D Einheit bilden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="face-and-vertex-normal-vectors.md">Seiten- und Scheitelnormalenvektoren</a></p></td>
<td align="left"><p>Jede Fläche in einem Gitter verfügt über einen normalen Einheitsvektor im rechten Winkel. Die Richtung des Vektors wird von der Reihenfolge bestimmt, in der die Scheitelpunkte definiert sind und ist abhängig davon, ob das Koordinatensystem rechts - oder linkshändig ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="rectangles.md">Rechtecke</a></p></td>
<td align="left"><p>In Direct3D und in der Windows-Programmierung werden Objekte auf dem Bildschirm als umgebende Rechtecke bezeichnet. Die Seiten des umgebenden Rechtecks sind immer parallel zu den Seiten des Bildschirms, damit das Rechteck durch zwei Punkte, der oberen linken Ecke und der unteren rechten Ecke, definiert werden kann.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="triangle-interpolation.md">Dreiecksinterpolation</a></p></td>
<td align="left"><p>Während des Renderns interpoliert die Pipeline Vertexdaten bei jedem Dreieck. Vertexdaten können eine Vielzahl von Daten sein und enthalten (sind aber nicht beschränkt auf): diffuse Farbe, Glanzfarbe, diffuse Alpha(Transparenz des Dreiecks), Glanzlicht Alpha und Nebelfaktor.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="vectors--vertices--and-quaternions.md">Vektoren, Scheitelpunkte und Quaternionen</a></p></td>
<td align="left"><p>In Direct3D beschreiben Scheitelpunkte die Position und Ausrichtung. Jeder Scheitelpunkt in einen Grundtyp wird durch einen Vektor beschrieben, der die Positions-, Farb-, Texturkoordinaten angibt sowie durch einen normalen Vektor, der die Ausrichtung angibt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="transforms.md">Transformationen</a></p></td>
<td align="left"><p>Das Transformationsmodul ist der Teil von Direct3D, der die Geometrie über die Geometriepipeline mit fester Funktion mithilfe von Push überträgt. Es ermittelt das Modell und die Anzeige im Raum, projiziert Scheitelpunkte für die Anzeige auf den Bildschirm und beschneidet Scheitelpunkte im Viewport. Das Transformationsmodul führt ebenfalls Beleuchtungsberechnungen durch, um diffuse und Glanzlichtkomponenten bei jedem Scheitelpunkt zu ermitteln.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="viewports-and-clipping.md">Ansichten und Zuschneiden</a></p></td>
<td align="left"><p>Ein <em>Viewport</em> ist ein zweidimensionales (2D) Rechteck, auf das eine 3D-Szene projiziert wird. In Direct3D ist das Rechteck eine Koordinate innerhalb einer Direct3D-Oberfläche, die das System als Renderziel verwendet. Die Projektionstransformation konvertiert Scheitelpunkte in das Koordinatensystem, das vom Viewport verwendet wird. Ein Viewport wird auch verwendet, um den Bereich der Tiefenwerte auf einer Renderzieloberfläche festzulegen, auf die eine Szene (in der Regel zwischen 0,0 und 1,0) gerendert wird.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Lernanleitung für Direct3D-Grafiken](index.md)

 

 




