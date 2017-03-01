---
title: Ansichten
description: "Der Begriff \\ 0034;Ansicht \\ 0034; wird für \\ 0034;Daten im erforderlichen Format \\ 0034; verwendet. Eine Konstantenpufferansicht (CBV) ist beispielweise ein Satz ordnungsgemäß formatierter, konstanter Pufferdaten. Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten."
ms.assetid: 0C7FB99F-7391-472F-BA53-576888DFC171
keywords:
- Ansichten
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: beaed3bbaf6cab56c826788d0361b1200c73a003
ms.lasthandoff: 02/07/2017

---

# <a name="views"></a>Ansichten


Der Begriff „Ansicht“ wird für „Daten im erforderlichen Format“ verwendet. Eine Konstantenpufferansicht (CBV) ist beispielweise ein Satz ordnungsgemäß formatierter, konstanter Pufferdaten. Dieser Abschnitt beschreibt die gängigsten und hilfreichsten Ansichten.

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
<td align="left"><p>[Konstantenpufferansicht (CBV)](constant-buffer-view--cbv-.md)</p></td>
<td align="left"><p>Konstantenpuffer enthalten Konstantendaten für Shader. Ihr Nutzen besteht darin, dass die Daten erhalten bleiben und jeder GPU-Shader darauf zugreifen kann, bis eine Änderung der Daten erforderlich wird.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Scheitelpunktpuffer- (VBV) und Indexpufferansicht (IBV)](vertex-buffer-view--vbv-.md)</p></td>
<td align="left"><p>Ein Scheitelpunktpuffer enthält Daten für eine Liste von Scheitelpunkten. Die Daten für jeden Scheitelpunkt können Position, Farbe, Normalvektor, Texturkoordinaten u. dgl. beinhalten. Ein Indexpuffer enthält Ganzzahlindizes (Offsets) für einen Scheitelpunktpuffer und wird verwendet, um ein Objekt, das aus einem Teil der Liste aller Scheitelpunkte besteht, zu definieren und zu rendern.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Shaderressourcenansicht (SRV) und Unsortierte Zugriffsansicht (UAV)](shader-resource-view--srv-.md)</p></td>
<td align="left"><p>Shaderressourcenansichten verpacken Texturen in der Regel in einem Format, so dass die Shader darauf zugreifen können. Eine unsortierte Zugriffsansicht bietet ähnliche Funktionen, ermöglicht aber das Lesen und Schreiben der Textur (oder einer anderen Ressource) in beliebiger Reihenfolge.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Sampler](sampler.md)</p></td>
<td align="left"><p>Mit dem Begriff „Sampling“ wird der Prozess des Lesens von Eingabewerten aus einer Textur oder einer anderen Ressource bezeichnet. Ein &quot;Sampler&quot; ist ein beliebiges Objekt, das aus Ressourcen liest.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Renderzielansicht (RTV)](render-target-view--rtv-.md)</p></td>
<td align="left"><p>Renderziele ermöglichen das Rendern einer Szene, die auf dem Bildschirm gerendert werden soll, in einem temporären Zwischenpuffer statt im Hintergrundpuffer. Dieses Feature ermöglicht die Verwendung der komplexen Szene, die z. B. als eine Spiegelungstextur oder für andere Zwecke in der Grafikpipeline, oder vielleicht zum Hinzufügen von Pixelshader-Effekten zu der Szene vor dem Rendern gerendert werden kann.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Tiefenschablonenansicht (Depth Stencil View, DSV)](depth-stencil-view--dsv-.md)</p></td>
<td align="left"><p>Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit. Der Tiefenpuffer dient dazu, das Zeichnen von Pixeln zu vermeiden, die von einem näher liegenden Objekt verdeckt werden und so für den Betrachter nicht sichtbar wären. Der Schablonenpuffer kann zur Aussortierung aller Zeichnungsaktivitäten außerhalb einer definierten Form genutzt werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Streamausgabeansicht (SOV)](stream-output-view--sov-.md)</p></td>
<td align="left"><p>Streamausgabeansichten ermöglichen, dass die Scheitelpunktinformationen von den Scheitelpunkt-, Mosaik- und Geometrie-Shadern zur weiteren Verwendung zurück in die Anwendung gestreamt werden. Zum Beispiel könnte ein Objekt, das durch diese Shader verzerrt wurde, in die Anwendung zurückgeschrieben werden, um eine genauere Eingabe für eine Physik- oder eine andere Engine bereitzustellen. In der Praxis sind aber Streamausgabeansichten ein selten verwendetes Feature der Grafikpipeline.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Rasterizergesteuerte Ansicht (ROV)](rasterizer-ordered-view--rov-.md)</p></td>
<td align="left"><p>Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Direct3D-Grafik-Lernanleitung](index.md)

 

 





