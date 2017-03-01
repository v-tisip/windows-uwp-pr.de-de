---
title: "Konfigurieren der Tiefenschablonenfunktionalität"
description: "In diesem Abschnitt werden die Schritte zum Einrichten des Tiefenschablonenpuffers und der Tiefenschablonenphase für die Ausgabezusammenführungsphase behandelt."
ms.assetid: B3F6CDAA-93ED-4DC1-8E69-972C557C7920
keywords:
- "Konfigurieren der Tiefenschablonenfunktionalität"
author: mtoepke
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 6814e5ee5aa99558830af4da3b43d102048f8bcb
ms.lasthandoff: 02/07/2017

---

# <a name="span-iddirect3dconceptsconfiguringdepth-stencilfunctionalityspanconfiguring-depth-stencil-functionality"></a><span id="direct3dconcepts.configuring_depth-stencil_functionality"></span>Konfigurieren der Tiefenschablonenfunktionalität


In diesem Abschnitt werden die Schritte zum Einrichten des Tiefenschablonenpuffers und der Tiefenschablonenphase für die Ausgabezusammenführungsphase behandelt.

Wenn Sie mit dem Tiefenschablonenpuffer und der entsprechenden Tiefenschablonenphase umgehen können, finden Sie weitere Informationen unter [erweiterte Schablonen-Techniken](#advanced-stencil-techniques).

## <a name="span-idcreatedepthstencilstatespanspan-idcreatedepthstencilstatespanspan-idcreatedepthstencilstatespancreate-depth-stencil-state"></a><span id="Create_Depth_Stencil_State"></span><span id="create_depth_stencil_state"></span><span id="CREATE_DEPTH_STENCIL_STATE"></span>Erstellen der Tiefenschablonenphase


Die Tiefenschablonenphase zeigt den Zustand der Ausgabezusammenführungsphase zum Ausführen des [Tiefenschablonen-Test](https://msdn.microsoft.com/library/windows/desktop/bb205120) an. Der Tiefenschablonen-Test bestimmt, ob eine gegebene Pixel gezeichnet werden soll oder nicht.

## <a name="span-idbinddepthstenciltotheomstagespanspan-idbinddepthstenciltotheomstagespanspan-idbinddepthstenciltotheomstagespanbind-depth-stencil-data-to-the-om-stage"></a><span id="Bind_Depth_Stencil_to_the_OM_Stage"></span><span id="bind_depth_stencil_to_the_om_stage"></span><span id="BIND_DEPTH_STENCIL_TO_THE_OM_STAGE"></span>Binden von Tiefenschablonendaten an die OM-Phase


Binden der Tiefenschablonenphase

Binden der Tiefenschablonen-Ressource mithilfe der Ansicht.

Renderziele müssen alle den gleichen Ressourcentyp verwenden. Wenn Multisampling-Antialiasing verwendet wird, müssen alle gebundenen Renderziele und Tiefenpuffer über die gleiche Beispielanzahl verfügen.

Wenn ein Puffer als Renderziel verwendet wird, werden Tiefenschablonen-Tests und mehrere Renderziele nicht unterstützt.

-   Es können bis zu 8 Renderziele gleichzeitig gebunden werden.
-   Alle Renderziele müssen die gleiche Größe für alle Dimensionen haben (Breite, Höhe und Tiefe für 3D oder Array-Größen für \*Array-Typen).
-   Jedes Renderziel kann ein anderes Datenformat haben.
-   Schreib-Masken überwachen, welche Daten in ein Renderziel geschrieben werden. Die Ausgabe-Schreib-Maske überwacht pro Renderziel und pro Komponentenebene, welche Daten in ein Renderziel geschrieben werden.

## <a name="span-idadvancedstenciltechniquesspanspan-idadvancedstenciltechniquesspanspan-idadvancedstenciltechniquesspanspan-idadvanced-stencil-techniquesspanadvanced-stencil-techniques"></a><span id="Advanced_Stencil_Techniques"></span><span id="advanced_stencil_techniques"></span><span id="ADVANCED_STENCIL_TECHNIQUES"></span><span id="advanced-stencil-techniques"></span>Erweiterte Schablonen-Techniken


Der Schablonen-Anteil des Tiefenschablonenpuffers kann zur Erstellung von Rendering-Effekten, wie Zusammensetzen, Decals und Gliedern verwendet werden.

-   [Zusammensetzen](#compositing)
-   [Decals verwenden](#decaling)
-   [Umrisse und Silhouetten](#outlines-and-silhouettes)
-   [Zweiseitige Schablone](#two-sided-stencil)
-   [Den Tiefenschablonenpuffers als Textur lesen](#reading-the-depth-stencil-buffer-as-a-texture)

### <a name="span-idcompositingspanspan-idcompositingspanspan-idcompositingspancompositing"></a><span id="Compositing"></span><span id="compositing"></span><span id="COMPOSITING"></span>Zusammensetzen

Ihre Anwendung kann die Schablonenpuffer verwenden, um 2D- oder 3D-Bilder mit einer 3D-Szene zu kombinieren. Im Schablonenpuffer wird eine Maske verwendet, um einen Bereich der Renderzieloberfläche zu verdecken. Gespeicherte 2D-Informationen, z. B. Text oder Bitmaps, können dann auf den verdeckten Bereich geschrieben werden. Alternativ kann die Anwendung zusätzliche 3D-Grundtypen auf den von der Schablone maskierten Bereich der Renderzieloberfläche rendern Es kann sogar eine ganze Szene gerendert werden.

Spiele fassen oft mehrere 3D-Szenen zusammen. Beispielsweise wird in Rennspielen oft ein Rückspiegel angezeigt. Der Spiegel enthält die Ansicht der 3D-Szene hinter der Fahrer. Es ist praktisch eine zweite 3D-Szene, die mit der Vorderansicht des Fahrers kombiniert wird.

### <a name="span-iddecalingspanspan-iddecalingspanspan-iddecalingspandecaling"></a><span id="Decaling"></span><span id="decaling"></span><span id="DECALING"></span>Verwenden von Decals

Direct3D-Apps legen mithilfe von Decals fest, welche Pixel eines bestimmten Grundbilds auf die Renderzieloberfläche gezeichnet werden. Anwendungen wenden Decals auf Bilder von Grundtypen an, damit koplanare Polygone korrekt rendern können.

Beim Erstellen von Reifenspuren und gelben Straßenlinien sollten die Spuren direkt auf der Straßenoberfläche angezeigt werden. Die Z-Werte für die Spuren und die Straße sind allerdings identisch. Der Tiefenpuffer kann daher keine klare Trennung zwischen den beiden erstellen. Es werden Pixel des hinteren Grundtyps möglicherweise über dem vorderen Grundtyp (und umgekehrt) gerendert. Das resultierende Bild scheint von Frame zu Frame zu flimmern. Dieser Effekt wird „Z-Konflikt” oder „Flimmern” genannt.

Um dieses Problem zu beheben, verwenden Sie eine Schablone, um den hinteren Grundtyp dort zu maskieren, wo das Decal angezeigt werden soll. Deaktivieren Sie die Z-Pufferung und rendern Sie das Bild des im Vordergrund stehenden Grundtyps auf den maskierten Bereich der Renderzieloberfläche.

Mischen Sie unterschiedliche Texturen, um das Problem zu lösen.

### <a name="span-idoutlinesandsilhouettesspanspan-idoutlinesandsilhouettesspanspan-idoutlinesandsilhouettesspanspan-idoutlines-and-silhouettesoutlines-and-silhouettes"></a><span id="Outlines_and_Silhouettes"></span><span id="outlines_and_silhouettes"></span><span id="OUTLINES_AND_SILHOUETTES"></span><span id="outlines-and-silhouettes">Umrisse und Silhouetten

Sie können die Schablonenpuffer für abstraktere Effekte wie Skizzieren und das Erstellen von Silhouetten verwenden.

Wenn Ihre Anwendung zwei Render-Durchgänge durchführt – einen zum Erstellen der Schablonenmaske und den zweiten zum Anwenden der Schablonenmaske auf das Bild, wobei die Grundtypen beim zweiten Durchgang etwas kleiner sind - enthält das resultierende Bild nur den Umriss des Grundtyps. Die Anwendung kann anschließend den von der Schablone maskierten Bereich des Bilds mit einer Volltonfarbe ausfüllen, um den Grundtyp mit Relief darzustellen.

Weist die Schablonenmaske die gleiche Größe und Form wie der gerenderte Grundtyp auf, enthält das resultierende Bild dort eine Lücke, wo der Grundtyp dargestellt werden sollte. Ihre Anwendung kann anschließend die Lücke mit Schwarz füllen, um eine Silhouette des Grundtyps zu erstellen.

### <a name="span-idtwosidedstencilspanspan-idtwosidedstencilspanspan-idtwosidedstencilspanspan-idtwo-sided-stencilspantwo-sided-stencil"></a><span id="Two_Sided_Stencil"></span><span id="two_sided_stencil"></span><span id="TWO_SIDED_STENCIL"></span><span id="two-sided-stencil"></span>Zweiseitige Schablone

Schattenvolumen dienen zum Zeichnen von Schatten mithilfe des Schablonenpuffers. Die Anwendung berechnet das Volume des geworfenen Schattens durch das Verdecken der Geometrie, indem die Ränder der Silhouette berechnet und diese vom Licht weg in eine Gruppe von 3D-Volumes extrahiert werden. Diese Volumes werden dann zweimal in den Schablonenpuffer gerendert.

Beim ersten Rendern werden nach vorn gerichtete Polygone gezeichnet und der Schablonenpufferwert erhöht. Beim zweiten Rendern werden die nach hinten gerichteten Polygone des Schattenvolumens gezeichnet und die Werte der Schablonenpuffer verringert.

In der Regel heben sich alle erhöhten oder verringerten Werte gegenseitig auf. Allerdings wurde die Szene bereits mit normaler Geometrie gerendert, wodurch bei einigen Pixeln beim Z-Puffer-Test Fehler auftraten, wenn das Schattenvolumen gerendert wird. Die Werte links im Schablonenpuffer entsprechen den Pixeln des Schattens. Die übrigen Schablonenpuffer-Inhalte dienen als Maske, um ein großes, übergreifendes schwarzes Viereck als Alpha in die Szene einzublenden. Da der Schablonenpuffer als Maske fungiert, werden die Pixel des Schattens dunkler gemacht.

Dies bedeutet, dass die Geometrie des Schattens zweimal pro Lichtquelle gezeichnet wird, was auf den Vertex-Durchsatz der GPU Druck ausübt. Die zweiseitige Schablonenfunktion wurde als Schutzmaßnahme gegen diese Situation entwickelt. Dabei stehen Ihnen zwei Sets an Schablonenphasen zur Verfügung (wie unten angegeben): eins für nach vorne gerichtete Dreiecke und das andere für nach hinten gerichtete Dreiecke. Auf diese Weise wird nur ein einziger Durchlauf pro Schattenvolumen pro Lichtquelle gezeichnet.

### <a name="span-idreadingthedepth-stencilbufferasatexturespanspan-idreadingthedepth-stencilbufferasatexturespanspan-idreadingthedepth-stencilbufferasatexturespanspan-idreading-the-depth-stencil-buffer-as-a-texturespanreading-the-depth-stencil-buffer-as-a-texture"></a><span id="Reading_the_Depth-Stencil_Buffer_as_a_Texture"></span><span id="reading_the_depth-stencil_buffer_as_a_texture"></span><span id="READING_THE_DEPTH-STENCIL_BUFFER_AS_A_TEXTURE"></span><span id="reading-the-depth-stencil-buffer-as-a-texture"></span>Den Tiefenschablonenpuffers als Textur lesen

Ein inaktiver Tiefenschablonenpuffer kann von einem Shader als Textur gelesen werden. Eine Anwendung, die einen Tiefenschablonenpuffer als Textur liest, rendert in zwei Durchgängen. Der erste Durchgang schreibt in den Tiefenschablonenpuffer und der zweite Durchgang liest aus dem Puffer. Dadurch kann der Shader die vorher in den Puffer geschriebenen Tiefen- oder Schablonenwerte mit dem aktuell gerenderten Pixelwert vergleichen. Das Ergebnis des Vergleichs kann zur Erstellung von Effekten wie Schattenabbildungen oder weichen Partikeln in einem bestimmten System verwendet werden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ausgabezusammenführungsphase (OM)](output-merger-stage--om-.md)

[Grafikpipeline](graphics-pipeline.md)

[Ausgabezusammenführungsphase](https://msdn.microsoft.com/library/windows/desktop/bb205120)

