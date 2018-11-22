---
title: Grafikpipeline
description: Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele. Die Daten durchlaufen vom Eingang zum Ausgang jede der konfigurierbaren oder programmierbaren Stufen.
ms.assetid: C9519AD0-5425-48BD-9FF4-AED8959CA4AD
keywords:
- Grafikpipeline
- Pipelinestufen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d4a362a3a7be06e48c64ce3e4d43ff917b9b24c5
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "7580411"
---
# <a name="graphics-pipeline"></a>Grafikpipeline


Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele. Die Daten durchlaufen Eingang zum Ausgang jede der konfigurierbaren oder programmierbaren Stufen.

Alle Stufen können mithilfe der Direct3D-API konfiguriert werden. Stufen, die allgemeine Shaderkerne (die abgerundeten rechteckige Blöcke) bereitstellen, sind mit der [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561)-Programmiersprache programmierbar. Dadurch wird die Pipeline extrem flexibel und anpassbar.

Die am häufigsten verwendeten Stufen sind die Vertex-Shader-Stufe (VS-Stufe) und die Pixel-Shader-Stufe (PS-Stufe). Wenn Sie nicht einmal diese Shaderstufen bereitstellen, werden standardmäßige No-Op- und Pass-Through-Vertex- und Pixel-Shader verwendet.

![Diagramm des Datenflusses in der programmierbaren Pipeline für Direct3D 11](images/d3d11-pipeline-stages.jpg)

## <a name="input-assembler-stage"></a>Input Assembler-Stufe

|-|-| | Zweck | Die [Eingabe-Assembler (IA)](input-assembler-stage--ia-.md) liefert Grundtypen und angrenzende Daten an die Pipeline, wie beispielsweise Dreiecke, Linien und Punkte, einschließlich semantischer IDs, damit die Shader effizienter von Grundformen, die bereits wurde noch nicht verarbeitet. | | Eingabe | Daten von Grundformen (Dreiecke, Linien und/oder Punkte), vom Benutzer gefüllten Puffern im Speicher. Und möglicherweise zugehörige Daten. Ein Dreieck wären 3 Vertices für alle Dreiecke und möglicherweise 3 Vertices für angrenzende Dreieck. | | Ausgabe | Grundformen mit angefügten, systemgenerierten Werten (z. B. eine Grundtyp-ID, eine Instanz-ID oder eine Scheitelpunkt-ID). |

## <a name="vertex-shader-stage"></a>Vertex-Shader-Stufe

|-|-| | Zweck | Der [Vertex-Shader (VS) Phase](vertex-shader-stage--vs-.md) verarbeitet Scheitelpunkte in der Regel Vorgänge wie Transformationen, Anwenden von Skins und Beleuchtung durch. Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt. Einzelne Vertex-Vorgänge wie Transformationen, Anwenden von Skins, Morphing und Beleuchtung pro Vertex. | | Eingabe | Ein einzelner Vertex mit wie VertexID und InstanceID vom System generierten Werten. Jeder Scheitelpunkt-Shader-eingabescheitelpunkt kann bis zu 16 32-Bit-Vektoren (bis zu 4 Komponenten jedes) besteht. | | Ausgabe | Ein einzelner Vertex. Jeder ausgabescheitelpunkt kann bis zu 16 32-Bit-4 Komponente Vektoren besteht. |
 
## <a name="hull-shader-stage"></a>Hull-Shader-Stufe
 
|-|-| | Zweck | Die [Phase Hüllen-Shader (HS)](hull-shader-stage--hs-.md) ist eine der tesselationsstufen, eine einzelne Fläche eines Modells in viele Dreiecke effizient aufteilen. Ein Hull-Shader wird einmal pro Patch aufgerufen. Er transformiert Eingabekontrollpunkte, die eine Oberfläche niederer Ordnung definieren, in Kontrollpunkte, die einen Patch bilden. Er führt außerdem einige Berechnungen pro Patch aus, um Daten für die Tessellatorphase (TS) und den Domänen-Shaderphase (DS)-Phase bereitzustellen. | | Eingabe | 1 bis 32 eingabekontrollpunkte, die zusammen eine Fläche niederer Ordnung definieren. | | Ausgabe | Ausgabekontrollpunkte 1 bis 32, die zusammen einen Patch bilden. Der Hull-Shader deklariert den für die Tessellatorphase (TS), einschließlich der Anzahl der Kontrollpunkte, den Typ der patchfläche und die Art der beim tesselieren zu verwendenden Partitionierung. |

## <a name="tessellator-stage"></a>Tessellatorstufe

|-|-| | Zweck | Die [Tessellatorphase (TS)](tessellator-stage--ts-.md) erstellt ein samplingmuster der Domäne, das den geometriepatch darstellt und generiert eine Reihe kleinerer Objekte (Dreiecke, Punkte oder Linien), die diese Samplings verbinden. | | Eingabe | Der Tessellator operiert einmal pro Patch und verwendet dabei die tesselationsfaktoren (die angeben, wie fein die Domäne tesseliert wird) und die Art der Partitionierung (die den zum Aufteilen eines Patches verwendeten Algorithmus angibt), die von der Hull-Shader-Stufe übergeben werden. | | Ausgabe | Die Tessellator übergibt die uv (und optional die w)-Koordinaten und die oberflächentopologie an die Domain-Shader-Stufe. |

## <a name="domain-shader-stage"></a>Domain-Shader-Stufe

|-|-| | Zweck | Die [Domänenshaderphase (DS)](domain-shader-stage--ds-.md) berechnet die Vertexposition eines unterteilten Punkts im Ausgabe-Patch; Sie berechnet die Vertexposition, die dem jeweiligen domainsample entspricht. Ein Domain-Shader wird einmal pro Tessellator Phase-Ausgabepunkt verfügt über schreibgeschützten Zugriff auf den Hull-Shader Patch und die Ausgabe Patch-Konstanten und der tessellatorphase-UV-Koordinaten Ausgabe ausgeführt. | | Eingabe | Ein Domain-Shader nutzt Ausgabe Kontrollpunkte von der [Phase Hüllen-Shader (HS)](hull-shader-stage--hs-.md). Zur Ausgabe des Hull-Shader gehören: Kontrollpunkte, Patchkonstantendaten und Tesselationsfaktoren. Die Tesselationsfaktoren können die Werte enthalten, die vom Tessellator mit fester Funktion verwendet werden, sowie die Rohwerte (die Werte vor dem Runden durch ganzzahlige Tesselation), die beispielsweise das Geomorphing erleichtern. Ein Domain-Shader wird einmal pro ausgabekoordinate aus der [Tessellatorphase (TS)](tessellator-stage--ts-.md)aufgerufen. | | Ausgabe | Die Domäne Shader domainshaderphase (DS) gibt die Vertexposition eines unterteilten Punkts im Ausgabe-Patch. |

## <a name="geometry-shader-stage"></a>Geometry-Shader-Stufe (GS-Stufe)

|-|-| | Zweck | Die [Geometry-Shader (GS)-Phase](geometry-shader-stage--gs-.md) verarbeitet vollständige Grundformen: Dreiecke, Linien und Punkte, zusammen mit deren angrenzenden Vertices. Sie unterstützt Geometrieverstärkung und -abschwächung. Sie ist nützlich für Algorithmen wie Point Sprite Expansion, Dynamic Particle Systems, Fur/Fin Generation, Shadow Volume Generation, Single Pass Render-to-Cubemap, Per-Primitive Material Swapping und Per-Primitive Material Setup (dazu gehört das Erstellen baryzentrischer Koordinaten als Daten für Grundformen, sodass ein Pixel-Shader allgemeine Attribute interpolieren kann). | | Eingabe | Im Gegensatz zu Vertex-Shader, der einen einzelnen Vertex verarbeitet, sind die Geometry-Shader-Eingaben Scheitelpunkte für ein vollständiger Grundformen (drei Vertices für Dreiecke, zwei Vertices für eine Linie oder einzelnen Vertex für einen Punkt). | | Ausgabe | Die Geometrieshaderphase (GS) kann mehrere Vertices ausgeben, eine einzelne ausgewählte Topologie darstellen. Ausgabetopologien des Geometry-Shaders sind <strong>Tristrip</strong>, <strong>Linestrip</strong> und <strong>Pointlist</strong>. Die Anzahl der ausgegebenen Grundformen kann mit jedem Aufruf des Geometry-Shaders variieren. Die maximale Anzahl auszugebender Vertices muss allerdings statisch deklariert werden muss. Ein Geometry-Shader-Aufruf ausgegeben können beliebige, und neue Strips können über die [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) HLSL-Funktion erstellt werden. |

## <a name="stream-output-stage"></a>Streamoutputstufe (SO-Stufe)

|-|-| | Zweck | Die [Streamoutputstufe (SO)-Stufe](stream-output-stage--so-.md) kontinuierlich Ausgaben (oder streamt) Vertexdaten aus der vorherigen aktiven Phase an einen oder mehrere Puffer im Speicher. In den Arbeitsspeicher gestreamte Daten können der Pipeline wieder als Eingabedaten oder zugeführt von der CPU eingelesen werden. | | Eingabe | Vertexdaten aus einer vorherigen Pipelinestufe. | | Ausgabe | Die Phase des Streamoutputstufe (SO) kontinuierlich Ausgaben (oder streamt) Vertexdaten aus der vorherigen aktiven Phase, z. B. die Geometrie Shader (GS), um einen oder mehrere Puffer im Speicher. Wenn die Geometrieshaderphase (GS) inaktiv ist und die Streamoutputstufe (SO)-Phase aktiv ist, gibt es kontinuierlich Vertexdaten aus der Phase Domänenshaderphase (DS) an Puffer im Speicher (oder wenn DS auch inaktiv ist, aus der Vertex-Shader (VS) Phase). |

## <a name="rasterizer-stage"></a>Rasterizerstufe (RS-Stufe)

|-|-| | Zweck | Die [Rasterizerphase (RS)](rasterizer-stage--rs-.md) beschneidet Grundtypen, die in nicht angezeigt werden, bereitet Grundtypen für den Pixel-Shader (PS) vor und bestimmt, wie PixelShader aufgerufen. Konvertiert Vektorinformationen (bestehend aus Formen oder Grundformen) in ein Rasterbild (bestehend aus Pixeln) klicken, zum Darstellen von 3D-Grafiken in Echtzeit. | | Eingabe | Vertices (X, y, Z, w), die in den Rasterizer wird angenommen, dass im homogenen Clipbereich befinden. In diesem Koordinatenraum, in dem die x-Achse nach rechts verweist, Y nach oben und Z verweist, von der Kamera weg. | | Ausgabe | Die tatsächliche Pixel, die gerendert werden müssen. Enthält einige vertexattribute zur Verwendung bei der Interpolation durch den Pixel-Shader. |

## <a name="pixel-shader-stage"></a>Pixel-Shader-Stufe
 
|-|-| | Zweck | Die [Phase Pixel-Shader (PS)](pixel-shader-stage--ps-.md) empfängt interpolierte Daten einer Grundform und generiert pixelbezogene Daten wie z. B. Farben. | | Eingabe | Wenn die Pipeline ohne einen Geometrieshader konfiguriert ist, ist ein Pixel-Shader auf 16, 32 Bits und 4 Komponente Eingaben beschränkt. Andernfalls kann ein Pixel-Shader bis zu 32 Eingaben mit je 32 Bits und 4 Komponente verarbeiten. Zu den Eingabedaten für den Pixel-Shader gehören Vertexattribute, die mit oder ohne perspektivische Korrekturen interpoliert werden können oder als Konstanten pro Grundform behandelt werden können. Pixel-Shader-Eingaben werden anhand der Vertexattribute der zu rasternden Grundform interpoliert, basierend auf dem deklarierten Interpolationsmodus. Wenn ein Grundtyp vor der Rasterung abgeschnitten wird, wird der Interpolationsmodus auch während des Zuschneidevorgangs berücksichtigt. | | Ausgabe | Ein Pixel-Shader kann bis zu 8 32-Bit-Ausgabe, 4 Komponente ausgeben oder keine Farbe, wenn das Pixel verworfen wird. Registrierkomponenten für Shader-Ausgabe müssen deklariert werden, bevor sie verwendet werden können. jedes Register ist eine unterschiedliche Ausgabe-Schreibmaske zulässig. |

## <a name="output-merger-stage"></a>Output-Merger-Stufe
 
|-|-| | Zweck | Die [Ausgabe Ausgabezusammenführungsphase (OM)](output-merger-stage--om-.md) kombiniert verschiedene Ausgabedaten (pixelshaderwerte, Tiefen-und Schabloneninformationen) mit dem Inhalt des Renderziels und Tiefen-/Schablonenpuffern das endgültige pipelineergebnis zu generieren. | | Eingabe | Eingaben für Output-Merger sind der pipelinezustand, die vom Pixel-Shader, den Inhalt der Renderziele und den Inhalt der Tiefe/Schablone-Puffer generierten Pixeldaten. | | Ausgabe | Die endgültige gerenderte Pixelfarbe. |

## <a name="related-topics"></a>Verwandte Themen

- [Lernanleitung für Direct3D-Grafiken](index.md)

- [Compute-Pipeline](compute-pipeline.md)
