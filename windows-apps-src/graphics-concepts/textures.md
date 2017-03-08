---
title: Texturen
description: "Texturen sind ein leistungsstarkes Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen. Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern, einfach auf erweiterte Texturtechniken zuzugreifen."
ms.assetid: B9E85C9E-B779-4852-9166-6FA2240B7046
keywords:
- Texturen
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 4c78099f6bd30956c45a907a960a595288e0eaf4
ms.lasthandoff: 02/07/2017

---

# <a name="textures"></a>Texturen


Texturen sind ein leistungsstarkes Tool, um mit dem Computer realistische 3D-Bilder zu erzeugen. Direct3D unterstützt einen umfangreichen Texturfunktionssatz, und ermöglicht Entwicklern, einfach auf erweiterte Texturtechniken zuzugreifen.

Für bessere Leistung sollten Sie dynamische Texturen verwenden. Eine dynamische Textur kann für jeden Frame gesperrt, beschrieben und entsperrt werden.

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
<td align="left"><p>[Einführung zu Texturen](introduction-to-textures.md)</p></td>
<td align="left"><p>Eine Texturressource ist eine Datenstruktur zum Speichern von Texeln, den kleinsten Einheiten einer Textur, die gelesen oder geschrieben werden können. Wird eine Textur von einem Shader gelesen, kann sie durch Textursampler gefiltert werden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Grundlegende Texturkonzepte](basic-texturing-concepts.md)</p></td>
<td align="left"><p>Obwohl frühe computergenerierte 3D-Bilder generell hoch entwickelt waren, sahen diese künstlich glänzend aus. Es fehlte ihnen an Kennzeichen wie etwa Abnutzungen, Rissen, Fingerabdrücken oder Flecken, die 3D-Objekten eine realistische optische Komplexität verleihen. Texturen sind besonders für den verbesserten Realismus von computergenerierten 3D-Bilder beliebt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Texturadressierungsmodi](texture-addressing-modes.md)</p></td>
<td align="left"><p>Die Direct3D-Anwendung kann jedem Scheitelpunkt jedes Grundtyps Texturkoordinaten zuweisen. In der Regel liegen die u- und v-Texturkoordinaten, die Sie einem Scheitelpunkt zuweisen, im Bereich zwischen einschließlich 0,0 und 1,0. Durch die Zuweisung von Texturkoordinaten außerhalb dieses Bereichs können Sie jedoch bestimmte Textur-Spezialeffekte erzielen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Texturfilterung](texture-filtering.md)</p></td>
<td align="left"><p>Die Texturfilterung erzeugt eine Farbe für jedes Pixel im 2D-gerenderten Bild des Grundtyps, wenn dieser durch die Abbildung eines 3D-Grundtyps auf einem 2D-Bildschirm gerendert wird.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Texturressourcen](texture-resources.md)</p></td>
<td align="left"><p>Texturen sind eine Art von Ressource, die zum Rendern verwendet wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Texturumbruch](texture-wrapping.md)</p></td>
<td align="left"><p>Der Texturumbruch ändert die grundlegende Weise, in der Direct3D texturierte Vielecke rasterisiert, unter Verwendung der für jeden Scheitelpunkt angegebenen Texturkoordinaten. Beim Rastern eines Vielecks interpoliert das System zwischen den Texturkoordinaten an jedem der Scheitelpunkte des Vielecks, um die Texel zu bestimmen, die für jedes Pixel des Vielecks zu verwenden sind.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Texturmischung](texture-blending.md)</p></td>
<td align="left"><p>Direct3D kann bis zu acht Texturen auf Grundtypen in einem einzigen Durchlauf auf Grundtypen mischen. Die Verwendung von mehreren gemischten Texturen kann die Framerate einer Direct3D-Anwendung erheblich erhöhen. Eine Anwendung verwendet mehrere Texturmischungen zur Anwendung von Texturen, Schatten, glänzender Beleuchtung, diffuser Beleuchtung und anderer Spezialeffekte in einem einzigen Durchgang.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Lichtzuordnung mit Texturen](light-mapping-with-textures.md)</p></td>
<td align="left"><p>Eine Lichtzuordnung ist eine Textur oder Texturgruppe, die Informationen über das Licht in einer 3D-Szene enthält. Lichtzuordnungen ordnen Grundtypen Licht- und Schattenbereiche zu. Multipass und das Mischen mehrerer Texturen ermöglichen Ihrer Anwendung, Szenen mit einer realistischeren Darstellung zu rendern als mit Schattierungstechniken.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Komprimierte Texturressourcen](compressed-texture-resources.md)</p></td>
<td align="left"><p>Texturzuordnungen sind digitale Bilder, die auf dreidimensionale Formen gezeichnet werden, um diesen mehr Details zu verleihen. Sie werden während der Rasterung auf diese Formen abgebildet. Der Prozess kann große Mengen der Systembusressourcen und Speicher verbrauchen. Um den von den Texturen verbrauchten Speicherbedarf zu reduzieren, unterstützt Direct3D die Komprimierung von Texturoberflächen. Einige Direct3D-Geräte bieten eine systemeigene Unterstützung für komprimierte Texturoberflächen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Direct3D-Grafik-Lernanleitung](index.md)

 

 





