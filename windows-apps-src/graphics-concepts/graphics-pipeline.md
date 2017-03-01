---
title: Grafikpipeline
description: "Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele Die Daten durchlaufen vom Eingang zum Ausgang jede der konfigurierbaren oder programmierbaren Stufen."
ms.assetid: C9519AD0-5425-48BD-9FF4-AED8959CA4AD
keywords:
- Grafikpipeline
- Pipelinestufen
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 72e4985481f464cd45c13fd390d27c4ba0e7c618
ms.lasthandoff: 02/07/2017

---

# <a name="graphics-pipeline"></a>Grafikpipeline


Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele. Die Daten durchlaufen Eingang zum Ausgang jede der konfigurierbaren oder programmierbaren Stufen.

Alle Stufen können mithilfe der Direct3D-API konfiguriert werden. Stufen, die allgemeine Shaderkerne (die abgerundeten rechteckige Blöcke) bereitstellen, sind mit der [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561)-Programmiersprache programmierbar. Dadurch wird die Pipeline extrem flexibel und anpassbar.

Die am häufigsten verwendeten Stufen sind die Vertex-Shader-Stufe (VS-Stufe) und die Pixel-Shader-Stufe (PS-Stufe). Wenn Sie nicht einmal diese Shaderstufen bereitstellen, werden standardmäßige No-Op- und Pass-Through-Vertex- und Pixel-Shader verwendet.

![Diagramm des Datenflusses in der programmierbaren Pipeline für Direct3D 11](images/d3d11-pipeline-stages.jpg)

## <a name="input-assembler-stage"></a>Input Assembler-Stufe

 

| | |
|-|-|
|Zweck|Die [Input-Assembler-Stufe (IA-Stufe)](input-assembler-stage--ia-.md) stellt für die Pipeline die Daten der grafischen Grundformen (Dreiecke, Linien und Punkte) und zugehörige Daten bereit, einschließlich semantischer IDs, welche die Effizienz der Shader erhöhen, weil damit Grundformen identifiziert werden können, die noch nicht verarbeitet wurden, sodass nur diese verarbeitet werden müssen.|
|Eingabe|Daten von Grundformen (Dreiecke, Linien und/oder Punkte) aus Puffern im Speicher, die vom Benutzer gefüllt wurden Und möglicherweise zugehörige Daten. Für ein Dreieck wären 3 Vertices und möglicherweise 3 Vertices für jedes angrenzende Dreieck.|
|Ausgabe|Grundformen mit angefügten, systemgenerierten Werten (z. B. eine Grundform-ID, eine Instanz-ID oder einen Vertex-ID).|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Input Assembler (IA) stage](input-assembler-stage--ia-.md) supplies primitive and adjacency data to the pipeline, such as triangles, lines and points, including semantics IDs to help make shaders more efficient by reducing processing to primitives that haven't already been processed.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left"> Primitive data (triangles, lines, and/or points), from user-filled buffers in memory. And possibly adjacency data. A triangle would be 3 vertices for each triangle and possibly 3 vertices for adjacency data per triangle.  </td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">Primitives with attached system-generated values (such as a primitive ID, an instance ID, or a vertex ID). </td>
</tr>
</tbody>
</table>
 -->



## <a name="vertex-shader-stage"></a>Vertex-Shader-Stufe
 

| | |
|-|-|
|Zweck|Die [Vertex-Shader-Stufe](vertex-shader-stage--vs-.md) verarbeitet Vertices und führt dabei in der Regel Vorgänge wie Transformationen oder das Anwenden von Skins und Beleuchtungen aus. Ein Vertex-Shader verarbeitet immer nur einen Eingabevertex und erzeugt daraus einen Ausgabevertex. Einzelne Vorgänge pro Vertex wie Transformationen, Anwenden von Skins, Morphing und Beleuchtung pro Vertex.|
|Eingabe|Ein einzelner Vertex mit systemgenerierten Werten wie VertexID und InstanceID. Jeder Eingabevertex für einen Vertex-Shader kann aus mehreren 32-Bit-Vektoren bestehen (maximal 16, mit jeweils bis zu 4-Komponenten).|
|Ausgabe|Ein einzelner Vertex. Jeder Ausgabevertex kann aus mehreren 32-Bit-Vektoren bestehen (maximal 16 mit jeweils 4 Komponenten).|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Vertex Shader (VS) stage](vertex-shader-stage--vs-.md) processes vertices, typically performing operations such as transformations, skinning, and lighting. A vertex shader takes a single input vertex and produces a single output vertex. Individual per-vertex operations, such as:
<ul>
<li>Transformations</li>
<li>Skinning</li>
<li>Morphing</li>
<li>Per-vertex lighting</li>
</ul></td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">A single vertex, with VertexID and InstanceID system-generated values. Each vertex shader input vertex can be comprised of up to 16 32-bit vectors (up to 4 components each).</td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">A single vertex. Each output vertex can be comprised of as many as 16 32-bit 4-component vectors.</td>
</tr>
</tbody>
</table>
-->
 

## <a name="hull-shader-stage"></a>Hull-Shader-Stufe
 

| | |
|-|-|
|Zweck|Die [Hull-Shader-Stufe](hull-shader-stage--hs-.md) ist eine der Tesselationsstufen, auf der eine durchgehende Fläche eines Modell effizient in vielen Dreiecke unterteilt wird. Ein Hull-Shader wird einmal pro Patch aufgerufen. Er transformiert Eingabekontrollpunkte, die eine Oberfläche niederer Ordnung definieren, in Kontrollpunkte, die einen Patch bilden. Er führt außerdem pro Patch einige Berechnungen aus, um der Tessellatorstufe (TS-Stufe) und der Domain-Shader-Stufe (DS-Stufe) Daten bereitzustellen.|
|Eingabe|1 bis 32 Eingabekontrollpunkte, die zusammen eine Fläche niederer Ordnung definieren.|
|Ausgabe|1 bis 32 Ausgabekontrollpunkte, die zusammen einen Patch bilden. Der Hull-Shader deklariert den für die Tessellatorstufe (TS-Stufe) erforderlichen Status. Dies schließt bestimmte Informationen ein, wie z. B. die Anzahl der Kontrollpunkte, den Typ der Patchfläche und die Art der Partitionierung, die bei der Tesselierung verwendet werden soll.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Hull Shader (HS) stage](hull-shader-stage--hs-.md) is one of the tessellation stages, which efficiently break up a single surface of a model into many triangles. A hull shader is invoked once per patch, and it transforms input control points that define a low-order surface into control points that make up a patch. It also does some per-patch calculations to provide data for the Tessellator (TS) stage and the Domain Shader (DS) stage.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">Between 1 and 32 input control points, which together define a low-order surface. </td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">Between 1 and 32 output control points, which together make up a patch. The hull shader declares the state for the Tessellator (TS) stage, including the number of control points, the type of patch face, and the type of partitioning to use when tessellating. </td>
</tr>
</tbody>
</table>
-->

## <a name="tessellator-stage"></a>Tessellatorstufe
 

| | |
|-|-|
|Zweck|Die [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md) erstellt ein Probemuster der Domäne, die den Geometriepatch darstellt, und generiert eine Reihe kleinerer Objekte (Dreiecke, Punkte oder Linien), die diese Proben verbinden.|
|Eingabe|Der Tessellator operiert einmal pro Patch und verwendet dabei die Tesselationsfaktoren (die angeben, wie fein die Domäne tesseliert wird) und den Partitionierungstyp (der den zum Aufteilen eines Patches in Slices verwendeten Algorithmus angibt), die von der Hull-Shader-Stufe übergeben werden. |
|Ausgabe|Die Tessellator übergibt die uv-Koordinaten (und optional die w-Koordinate) sowie die Oberflächentopologie an die Domain-Shader-Stufe.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Tessellator (TS) stage](tessellator-stage--ts-.md) creates a sampling pattern of the domain that represents the geometry patch and generates a set of smaller objects (triangles, points, or lines) that connect these samples.   </td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left"> The tessellator operates once per patch using the tessellation factors (which specify how finely the domain will be tessellated) and the type of partitioning (which specifies the algorithm used to slice up a patch) that are passed in from the hull-shader stage. </td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The tessellator outputs uv (and optionally w) coordinates and the surface topology to the domain-shader stage.     </td>
</tr>
</tbody>
</table>
 -->

## <a name="domain-shader-stage"></a>Domain-Shader-Stufe
 

| | |
|-|-|
|Zweck|Die [Domain-Shader-Stufe (DS-Stufe)](domain-shader-stage--ds-.md) berechnet die Vertexposition eines unterteilten Punkts im Ausgabepatch, also die Vertexposition, die jedem Domänenbeispiel entspricht. Ein Domain-Shader wird einmal pro Ausgabepunkt der Tessellatorstufe ausgeführt und hat schreibgeschützten Zugriff auf die UV-Koordinaten der Ausgabe der Tessellatorstufe, den Ausgabepatch des Hull-Shaders und dessen Ausgabepatchkonstanten.|
|Eingabe|Ein Domain-Shader übernimmt Ausgabekontrollpunkte [Hull-Shader-Stufe (HS-Stufe)](hull-shader-stage--hs-.md). Zur Ausgabe des Hull-Shader gehören: Kontrollpunkte, Patchkonstantendaten und Tesselationsfaktoren. Die Tesselationsfaktoren können die Werte enthalten, die vom Tessellator mit fester Funktion verwendet werden, sowie die Rohwerte (die Werte vor dem Runden durch ganzzahlige Tesselation), die beispielsweise das Geomorphing erleichtern. Ein Domain-Shader wird von der [Tessellatorstufe (TS-Stufe)](tessellator-stage--ts-.md) einmal pro Ausgabekoordinate aufgerufen.|
|Ausgabe|Die Domain-Shader-Stufe (DS-Stufe) gibt die Vertexposition eines unterteilten Punkts im Ausgabepatch aus.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Domain Shader (DS) stage](domain-shader-stage--ds-.md) calculates the vertex position of a subdivided point in the output patch; it calculates the vertex position that corresponds to each domain sample. A domain shader is run once per tessellator stage output point and has read-only access to the hull shader output patch and output patch constants, and the tessellator stage output UV coordinates.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left"><ul>
<li>A domain shader consumes output control points from the [Hull Shader (HS) stage](hull-shader-stage--hs-.md). The hull shader outputs include:
<ul>
<li>Control points.</li>
<li>Patch constant data.</li>
<li>Tessellation factors. The tessellation factors can include the values used by the fixed-function tessellator as well as the raw values (before rounding by integer tessellation, for example), which facilitates geomorphing, for example.</li>
</ul></li>
<li>A domain shader is invoked once per output coordinate from the [Tessellator (TS) stage](tessellator-stage--ts-.md).</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The Domain Shader (DS) stage outputs the vertex position of a subdivided point in the output patch.</td>
</tr>
</tbody>
</table>
-->
 

## <a name="geometry-shader-stage"></a>Geometry-Shader-Stufe (GS-Stufe)
 

| | |
|-|-|
|Zweck|Die [Geometry-Shader-Stufe (GS-Stufe)](geometry-shader-stage--gs-.md) verarbeitet vollständige Grundformen (Dreiecke, Linien und Punkt) zusammen mit deren angrenzenden Vertices. Sie unterstützt Geometrieverstärkung und -abschwächung. Sie ist nützlich für Algorithmen wie Point Sprite Expansion, Dynamic Particle Systems, Fur/Fin Generation, Shadow Volume Generation, Single Pass Render-to-Cubemap, Per-Primitive Material Swapping und Per-Primitive Material Setup (dazu gehört das Erstellen baryzentrischer Koordinaten als Daten für Grundformen, sodass ein Pixel-Shader allgemeine Attribute interpolieren kann). |
|Eingabe|Im Gegensatz zu den Eingaben für einen Vertex-Shader, der einen einzelnen Vertex verarbeitet, sind die Eingaben für einen Geometry-Shader die Vertices vollständiger Grundformen (drei Vertices für ein Dreieck, zwei Vertices für eine Linie oder ein Vertex für einen Punkt).|
|Ausgabe|Die Geometry-Shader-Stufe (GS-Stufe) kann mehrere Vertices ausgeben, die eine einzelne ausgewählte Topologie darstellen. Ausgabetopologien des Geometry-Shaders sind <strong>Tristrip</strong>, <strong>Linestrip</strong> und <strong>Pointlist</strong>. Die Anzahl der ausgegebenen Grundformen kann mit jedem Aufruf des Geometry-Shaders variieren. Die maximale Anzahl auszugebender Vertices muss allerdings statisch deklariert werden muss. Die nach einem Geometry-Shader-Aufruf ausgegeben Strips können beliebig lang sein. Neue Strips können mit der HLSL-Funktion [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) erstellt werden.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Geometry Shader (GS) stage](geometry-shader-stage--gs-.md) processes entire primitives: triangles, lines, and points, along with their adjacent vertices. It is useful for algorithms including Point Sprite Expansion, Dynamic Particle Systems, and Shadow Volume Generation. It supports geometry amplification and de-amplification.
<ul>
<li>Point Sprite Expansion</li>
<li>Dynamic Particle Systems</li>
<li>Fur/Fin Generation</li>
<li>Shadow Volume Generation</li>
<li>Single Pass Render-to-Cubemap</li>
<li>Per-Primitive Material Swapping</li>
<li>Per-Primitive Material Setup, including generation of barycentric coordinates as primitive data so that a pixel shader can perform custom attribute interpolation.</li>
</ul></td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">Unlike vertex shaders, which operate on a single vertex, the geometry shader's inputs are the vertices for a full primitive (three vertices for triangles, two vertices for lines, or single vertex for point).</td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The Geometry Shader (GS) stage is capable of outputting multiple vertices forming a single selected topology. Available geometry shader output topologies are <strong>tristrip</strong>, <strong>linestrip</strong>, and <strong>pointlist</strong>. The number of primitives emitted can vary freely within any invocation of the geometry shader, though the maximum number of vertices that could be emitted must be declared statically. Strip lengths emitted from a geometry shader invocation can be arbitrary, and new strips can be created via the [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) HLSL function.</td>
</tr>
</tbody>
</table>
-->
 

## <a name="stream-output-stage"></a>Streamoutputstufe (SO-Stufe)
 

| | |
|-|-|
|Zweck|Die [Streamoutputstufe (SO-Stufe)](stream-output-stage--so-.md) liefert (streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Stufe einen oder mehrere Puffer im Speicher. Die in den Speicher gestreamten Daten können der Pipeline wieder als Eingabedaten zugeführt oder von der CPU eingelesen werden.|
|Eingabe|Vertexdaten aus einer vorherigen Pipelinestufe.|
|Ausgabe|Die Streamoutputstufe (SO-Stufe) liefert (streamt) kontinuierlich Vertexdaten aus der vorherigen aktiven Stufe (z. B. der Geometry-Shader-Stufe (GS-Stufe) ) in einen oder mehrere Puffer im Speicher. Wenn die Geometry-Shader-Stufe (GS-Stufe) inaktiv ist und die Streamoutputstufe (SO-Stufe) aktiv ist, liefert diese kontinuierlich Vertexdaten der Domain-Shader-Stufe (DS-Stufe) in Puffer im Speicher. Wenn auch DS inaktiv ist, stammen die Daten aus der Vertex-Shader-Stufe (VS-Stufe).|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Stream Output (SO) stage](stream-output-stage--so-.md) continuously outputs (or streams) vertex data from the previous active stage to one or more buffers in memory. Data streamed out to memory can be recirculated back into the pipeline as input data, or read-back from the CPU.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">Vertex data from a previous pipeline stage.   </td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The Stream Output (SO) stage continuously outputs (or streams) vertex data from the previous active stage, such as the Geometry Shader (GS) stage, to one or more buffers in memory. If the Geometry Shader (GS) stage is inactive, and the Stream Output (SO) stage is active, it continuously outputs vertex data from the Domain Shader (DS) stage to buffers in memory (or if the DS is also inactive, from the Vertex Shader (VS) stage).</td>
</tr>
</tbody>
</table>
-->

## <a name="rasterizer-stage"></a>Rasterizerstufe (RS-Stufe)
 

| | |
|-|-|
|Zweck|Die [Rasterizerstufe](rasterizer-stage--rs-.md) blendet Grundformen aus, die nicht im Sichtfeld liegen, bereitet Grundformen für den Pixel-Shader vor und bestimmt, wie Pixel-Shader aufgerufen werden. Konvertiert Vektorinformationen (bestehend aus Formen oder Grundformen) in ein Rasterbild (bestehend aus Pixeln) zum Darstellen von 3D-Grafiken in Echtzeit.|
|Eingabe|Für Vertices (x,y,z,w), die in die Rasterizerstufe einfließen, wird angenommen, dass sie sich im homogenen Clipbereich befinden. In diesem Koordinatenraum zeigt die X-Achse nach rechts, die Y-Achse nach oben und die Z-Achse von der Kamera weg.|
|Ausgabe|Die Pixel, die momentan gerendert werden müssen. Enthält einige Vertexattribute zur Verwendung bei der Interpolation durch den Pixel-Shader.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Rasterizer (RS) stage](rasterizer-stage--rs-.md) clips primitives that aren't in view, prepares primitives for the Pixel Shader (PS) stage, and determines how to invoke pixel shaders. Converts vector information (composed of shapes or primitives) into a raster image (composed of pixels) for the purpose of displaying real-time 3D graphics.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left">Vertices (x,y,z,w) coming into the Rasterizer stage are assumed to be in homogeneous clip-space. In this coordinate space the X axis points right, Y points up and Z points away from camera.</td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The actual pixels that need to be rendered. Includes some vertex attributes for use in interpolation by the pixel Shader.</td>
</tr>
</tbody>
</table>
 -->

## <a name="pixel-shader-stage"></a>Pixel-Shader-Stufe
 

| | |
|-|-|
|Zweck|Die [Pixel-Shader-Stufe (PS-Stufe)](pixel-shader-stage--ps-.md) empfängt interpolierte Daten einer Grundform und generiert pixelbezogene Daten wie z. B. Farben.|
|Eingabe|Wenn die Pipeline ohne einen Geometry-Shader konfiguriert wurde, ist ein Pixel-Shader auf 16 Eingaben mit je 32 Bits und 4 Komponenten beschränkt. Andernfalls kann ein Pixel-Shader bis zu 32 Eingaben mit je 32 Bits und 4 Komponente verarbeiten. Zu den Eingabedaten für den Pixel-Shader gehören Vertexattribute, die mit oder ohne perspektivische Korrekturen interpoliert werden können oder als Konstanten pro Grundform behandelt werden können. Pixel-Shader-Eingaben werden anhand der Vertexattribute der zu rasternden Grundform interpoliert, basierend auf dem deklarierten Interpolationsmodus. Wenn eine Grundform vor der Rasterung gekappt wird, wird der Interpolationsmodus auch während des Clippingvorgangs Clipping berücksichtigt. |
|Ausgabe|Ein Pixel-Shader kann bis zu 8 Farben mit je 32 Bits und 4 Komponente ausgeben oder keine Farbe, wenn das Pixel verworfen wird. Registerkomponenten für die Pixel-Shader-Ausgabe müssen deklariert werden, bevor sie verwendet werden können. Jedes Register kann eine unterschiedliche Ausgabeschreibmaske besitzen.|
| | |

<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Pixel Shader (PS) stage](pixel-shader-stage--ps-.md) receives interpolated data for a primitive and generates per-pixel data such as color.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left"><p>When the pipeline is configured without a geometry shader, a pixel shader is limited to 16, 32-bit, 4-component inputs. Otherwise, a pixel shader can take up to 32, 32-bit, 4-component inputs.</p>
<p>Pixel shader input data includes vertex attributes (that can be interpolated with or without perspective correction) or can be treated as per-primitive constants. Pixel shader inputs are interpolated from the vertex attributes of the primitive being rasterized, based on the interpolation mode declared. If a primitive gets clipped before rasterization, the interpolation mode is honored during the clipping process as well.</p></td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left"><p>A pixel shader can output up to 8, 32-bit, 4-component colors, or no color if the pixel is discarded. Pixel shader output register components must be declared before they can be used; each register is allowed a distinct output-write mask.</p></td>
</tr>
</tbody>
</table>
-->
 

## <a name="output-merger-stage"></a>Output-Merger-Stufe
 

| | |
|-|-|
|Zweck|Die [Output-Merger-Stufe](output-merger-stage--om-.md) kombiniert verschiedene Ausgabedaten (Pixel-Shader-Werte, Tiefen- und Schabloneninformationen) mit dem Inhalt des Renderziels und Tiefen-/Schablonenpuffern, um das endgültige Pipelineergebnis zu generieren.|
|Eingabe|Eingaben für Output-Merger sind der Pipelinezustand, die vom Pixel-Shader generierten Pixeldaten, die Inhalte der Renderziele und die Inhalte des Tiefen-/Schablonenpuffers.|
|Ausgabe|Die endgültige gerenderte Pixelfarbe.|
| | |


<!---
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left">Purpose</td>
<td align="left">The [Output Merger (OM) stage](output-merger-stage--om-.md) combines various types of output data (pixel shader values, depth and stencil information) with the contents of the render target and depth/stencil buffers to generate the final pipeline result.</td>
</tr>
<tr class="even">
<td align="left">Input</td>
<td align="left"><ul>
<li>Pipeline state</li>
<li>The pixel data generated by the pixel shaders</li>
<li>The contents of the render targets</li>
<li>The contents of the depth/stencil buffers.</li>
</ul></td>
</tr>
<tr class="odd">
<td align="left">Output</td>
<td align="left">The final rendered pixel color.</td>
</tr>
</tbody>
</table>


| | |
|-|-|
|Purpose|xxxx|
|Input|yyyy|
|Output|zzzz|
| | |
-->

## <a name="related-topics"></a>Verwandte Themen


[Lernanleitung für Direct3D-Grafiken](index.md)

[Compute-Pipeline](compute-pipeline.md)

 

 

