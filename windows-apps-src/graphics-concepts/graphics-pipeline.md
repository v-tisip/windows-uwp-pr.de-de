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
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 6cb50af5facdbf4271c9911f0e1f536dead0b8b8
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1044909"
---
# <a name="graphics-pipeline"></a>Grafikpipeline


Die Direct3D-Grafikpipeline dient zum Generieren von Grafiken für Echtzeitspiele. Die Daten durchlaufen Eingang zum Ausgang jede der konfigurierbaren oder programmierbaren Stufen.

Alle Stufen können mithilfe der Direct3D-API konfiguriert werden. Stufen, die allgemeine Shaderkerne (die abgerundeten rechteckige Blöcke) bereitstellen, sind mit der [HLSL](https://msdn.microsoft.com/library/windows/desktop/bb509561)-Programmiersprache programmierbar. Dadurch wird die Pipeline extrem flexibel und anpassbar.

Die am häufigsten verwendeten Stufen sind die Vertex-Shader-Stufe (VS-Stufe) und die Pixel-Shader-Stufe (PS-Stufe). Wenn Sie nicht einmal diese Shaderstufen bereitstellen, werden standardmäßige No-Op- und Pass-Through-Vertex- und Pixel-Shader verwendet.

![Diagramm des Datenflusses in der programmierbaren Pipeline für Direct3D 11](images/d3d11-pipeline-stages.jpg)

## <a name="input-assembler-stage"></a>Input Assembler-Stufe

|-|-| | Zweck | Die [Eingabe Assembler (IA) Phase](input-assembler-stage--ia-.md) Netzteile primitiven und Nähe Daten in der Pipeline, wie Dreiecke, Linien und Punkte, einschließlich Semantik machen Shader effizienter durch die Reduzierung von Verarbeitung für primitive, die bereits wurde noch nicht-IDs verarbeitet. | | Eingabe | Primitiven Daten (Dreiecke, Linien und/oder Punkt), aus dem Puffer im Arbeitsspeicher Benutzer ausgefüllt. Und möglicherweise zugehörige Daten. Ein Dreieck wäre 3 Scheitelpunkte für jedes Dreieck und möglicherweise 3 Scheitelpunkte für Nähe Daten pro Dreieck. | | Ausgabe | Primitives mit angefügten vom System generierte Werte (beispielsweise eine primitive-ID, eine Instanz-ID oder eine ID Scheitelpunkts). |

## <a name="vertex-shader-stage"></a>Vertex-Shader-Stufe

|-|-| | Zweck | Der [Scheitelpunkt Shader (VS) Phase](vertex-shader-stage--vs-.md) verarbeitet Scheitelpunkte, in der Regel Vorgängen wie Transformationen, Designs und Beleuchtung. Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt. Einzelne Vertices-Vorgänge, wie Transformationen, Skinning, Morphing und Vertices Beleuchtung. | | Eingabe | Einen einzelnen Scheitelpunkt mit VertexID und InstanceID vom System generierte Werte. Kann jeden Scheitelpunkt Shader input Scheitelpunkt bis zu 16 32-Bit-Vektoren (bis zu 4 Komponenten jedes) bestehend. | | Ausgabe | Einen einzelnen Scheitelpunkt. Kann jeder Ausgabe Scheitelpunkts bis zu 16 32-Bit-4-Komponente Vektoren bestehend. |
 
## <a name="hull-shader-stage"></a>Hull-Shader-Stufe
 
|-|-| | Zweck | Die [Phase Hülle Shader (HS)](hull-shader-stage--hs-.md) ist eine der Mosaik Phasen, die eine einzelne Fläche eines Modells in vielen Dreiecke effizient zu unterteilen. Ein Hull-Shader wird einmal pro Patch aufgerufen. Er transformiert Eingabekontrollpunkte, die eine Oberfläche niederer Ordnung definieren, in Kontrollpunkte, die einen Patch bilden. Ist es auch einige Patch-Berechnungen, um Daten für die Phase Tessellator (TS) und die Domäne Shader (DS) Phase bereitzustellen. | | Eingabe | Zwischen 1 und 32 Eingabesteuerelement Punkte, die eine niederwertige Fläche gemeinsam definieren,. | | Ausgabe | Zwischen 1 und 32 Ausgabe Steuerpunkte können die ein Patch zusammen bilden. Der Hülle Shader deklariert den Status für die Phase Tessellator (TS), einschließlich der Anzahl der Steuerpunkte, den Typ des Patch-Oberfläche und den Typ der Partitionierung um verwenden, wenn tessellating. |

## <a name="tessellator-stage"></a>Tessellatorstufe

|-|-| | Zweck | Die [Phase Tessellator (TS)](tessellator-stage--ts-.md) erstellt ein Muster Sampling der Domäne, die stellt des Geometrie Patches und generiert eine Reihe von kleineren Objekten (Dreiecke, Punkt oder Zeilen), die diese Beispiele zu verbinden. | | Eingabe | Die Tessellator wird einmal pro Patch mithilfe der Mosaik Faktoren (die angeben, wie fein die Domäne tesselierten wird) und die Art der Partitionierung (gibt an, den Algorithmus verwendet, um von einem Patch slice), die aus der Hülle Shader-Phase übergeben werden. | | Ausgabe | Die Tessellator gibt uv (und optional w) Koordinaten und die Fläche Topologie in die Domäne Shader Phase. |

## <a name="domain-shader-stage"></a>Domain-Shader-Stufe

|-|-| | Zweck | Die [Domäne Shader (DS) Phase](domain-shader-stage--ds-.md) berechnet die Scheitelpunkt Position eines Punkts unterteilt in der Ausgabe Patch; berechnet die Scheitelpunkt Position, die jede Domäne Beispiel entspricht. Ein Domäne Shader wird einmal pro Tessellator Phase Punkt Ausgabe und schreibgeschützten Zugriff auf die Hülle Shader Ausgabe Patch Ausgabe Patch-Konstanten, hat und die Tessellator Phase UV-Koordinaten Ausgabe ausgeführt werden. | | Eingabe | Ein Domäne Shader verbraucht Ausgabe Steuerpunkte von der [Phase Hülle Shader (HS)](hull-shader-stage--hs-.md). Zur Ausgabe des Hull-Shader gehören: Kontrollpunkte, Patchkonstantendaten und Tesselationsfaktoren. Die Tesselationsfaktoren können die Werte enthalten, die vom Tessellator mit fester Funktion verwendet werden, sowie die Rohwerte (die Werte vor dem Runden durch ganzzahlige Tesselation), die beispielsweise das Geomorphing erleichtern. Ein Domäne Shader wird einmal pro Ausgabe Koordinate von der [Tessellator (TS) Phase](tessellator-stage--ts-.md)aufgerufen. | | Ausgabe | Die Domäne Shader (DS) Phase gibt die Position Scheitelpunkts eines Punkts unterteilt in der Ausgabe Patch. |

## <a name="geometry-shader-stage"></a>Geometry-Shader-Stufe (GS-Stufe)

|-|-| | Zweck | Der [Geometrie Shader (GS) Phase](geometry-shader-stage--gs-.md) verarbeitet die gesamte Primitives: Dreiecke, Linien und Punkt zusammen mit ihren benachbarten Scheitelpunkten. Sie unterstützt Geometrieverstärkung und -abschwächung. Sie ist nützlich für Algorithmen wie Point Sprite Expansion, Dynamic Particle Systems, Fur/Fin Generation, Shadow Volume Generation, Single Pass Render-to-Cubemap, Per-Primitive Material Swapping und Per-Primitive Material Setup (dazu gehört das Erstellen baryzentrischer Koordinaten als Daten für Grundformen, sodass ein Pixel-Shader allgemeine Attribute interpolieren kann). | | Eingabe | Im Gegensatz zu Scheitelpunkts Shader, die auf einen einzelnen Scheitelpunkt arbeiten, die Geometrieshader-Eingaben sind die Scheitelpunkte für ein vollständige Basiselement (drei Dreiecke Scheitelpunkte, zwei Scheitelpunkte für Zeilen oder einzelne Scheitelpunkt für Punkt). | | Ausgabe | Die Geometrie Shader (GS) Phase kann mehrere Scheitelpunkte bilden eine einzelne ausgewählte Topologie ausgeben. Ausgabetopologien des Geometry-Shaders sind <strong>Tristrip</strong>, <strong>Linestrip</strong> und <strong>Pointlist</strong>. Die Anzahl der ausgegebenen Grundformen kann mit jedem Aufruf des Geometry-Shaders variieren. Die maximale Anzahl auszugebender Vertices muss allerdings statisch deklariert werden muss. Streifen Längen Geometrie Shader Aufrufs von ausgegebene können beliebige, und neue Streifen können erstellt werden, über die Funktion [RestartStrip](https://msdn.microsoft.com/library/windows/desktop/bb509660) HLSL. |

## <a name="stream-output-stage"></a>Streamoutputstufe (SO-Stufe)

|-|-| | Zweck | Der [Stream Ausgabe (SO) Phase](stream-output-stage--so-.md) kontinuierlich ausgegeben (oder als Stream) Scheitelpunkt und Daten aus der vorherigen aktiven Phase in eine oder mehrere Puffer im Arbeitsspeicher. In den Arbeitsspeicher übertragene Daten wieder in die Pipeline als Eingabedaten oder Lesen-zurück, von der CPU recirculated werden können. | | Eingabe | Scheitelpunkt und Daten aus einer früheren Pipeline Phase. | | Ausgabe | Die Stream-Ausgabe (SO) Phase kontinuierlich ausgegeben (oder als Stream) Scheitelpunkt und Daten aus der vorherigen aktiven Phase wie die Phase Geometrie Shader (GS) in eine oder mehrere Puffer im Arbeitsspeicher. Wenn das Freigabefenster Geometrie Shader (GS) inaktiv ist und die Phase Stream Ausgabe (SO) aktiv ist, gibt es kontinuierlich Scheitelpunkt und Daten aus der Domäne Shader (DS) Phase Puffer im Arbeitsspeicher (oder wenn die DS auch inaktiv, von der Stufe Scheitelpunkts Shader (VS) ist). |

## <a name="rasterizer-stage"></a>Rasterizerstufe (RS-Stufe)

|-|-| | Zweck | Das [Rasterprogramm (RS) Phase](rasterizer-stage--rs-.md) Clips Primitives, die nicht in der Ansicht sind bereitet Primitives für die Phase Pixel Shader (PS) und bestimmt, wie Pixel Shader aufzurufen. Konvertiert Vektor (bestehend aus Shapes- oder Primitives) Informationen in einer Raster-Bild (aus Pixeln) zum Anzeigen von Real-Time 3D Graphics. | | Eingabe | Scheitelpunkte (X, y, Z, w) eingehen Rasterprogramm Phase wird angenommen, dass in homogene Clip Leerzeichen werden. In diesem Koordinatenstelle steht die x-Achse rechts zeigt, Y nach oben und Z verweist, von der Kamera. | | Ausgabe | Die tatsächliche Pixel, die gerendert werden müssen. Enthält einige Scheitelpunkt und Attribute für die Verwendung in Interpolation durch die Pixel Shader. |

## <a name="pixel-shader-stage"></a>Pixel-Shader-Stufe
 
|-|-| | Zweck | [Pixel Shader (PS) Phase](pixel-shader-stage--ps-.md) empfängt interpolierte Daten für ein Element und generiert pro Pixel Daten wie Farbe. | | Eingabe | Wenn die Pipeline ohne Geometrieshader konfiguriert ist, ist ein PixelShader auf 16, 32-Bit, 4-Komponente Eingaben beschränkt. Andernfalls kann ein Pixel-Shader bis zu 32 Eingaben mit je 32 Bits und 4 Komponente verarbeiten. Zu den Eingabedaten für den Pixel-Shader gehören Vertexattribute, die mit oder ohne perspektivische Korrekturen interpoliert werden können oder als Konstanten pro Grundform behandelt werden können. Pixel-Shader-Eingaben werden anhand der Vertexattribute der zu rasternden Grundform interpoliert, basierend auf dem deklarierten Interpolationsmodus. Wenn ein Grundtyp vor der Rasterung abgeschnitten wird, wird der Interpolationsmodus auch während des Zuschneidevorgangs berücksichtigt. | | Ausgabe | Ein PixelShader kann bis zu 32-Bit, 8 ausgeben, 4-Komponente Farben oder keine Farbe wenn Pixels verworfen wird. Pixel Shader Ausgabe registrieren Komponenten müssen deklariert werden, bevor sie verwendet werden können. jedes Register ist eine unterschiedliche Ausgabe-Write Maske zulässig. |

## <a name="output-merger-stage"></a>Output-Merger-Stufe
 
|-|-| | Zweck | Die [Ausgabe Fusion (OM) Phase](output-merger-stage--om-.md) kombiniert verschiedene Arten von Ausgabedaten (Pixel Shader Werte, Tiefe und Schablone Informationen) mit dem Inhalt der Render Ziel und Tiefe-Schablone Puffer zum Generieren des endgültigen Pipeline Ergebnisses. | | Eingabe | Ausgabe Fusion Eingaben sind der Pipeline Zustand, die Pixeldaten von Pixel Shader, den Inhalt der Renderingziele und den Inhalt der Tiefe-Schablone Puffer generierte. | | Ausgabe | Die endgültige gerenderte Pixelfarbe. |

## <a name="related-topics"></a>Verwandte Themen

- [Lernanleitung für Direct3D-Grafiken](index.md)

- [Compute-Pipeline](compute-pipeline.md)
