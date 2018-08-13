---
title: Einführung zu Puffern
description: Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden.
ms.assetid: 494FDF57-0FBE-434C-B568-06F977B40263
keywords:
- Einführung zu Puffern
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 677eea4757220320bc364fef20bf5a5c8d4daaa2
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1044339"
---
# <a name="introduction-to-buffers"></a>Einführung zu Puffern


Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden. Puffer speichern Daten, wie z.B. Texturkoordinaten in einem *Scheitelpunktpuffer*, Indizes in einem *Indexpuffer*, Shader-Konstantendaten in einem *Konstantenpuffer*, Positionsvektoren, normale Vektoren oder den Gerätezustand.

Ein Element Puffer 1 bis 4 Komponenten besteht. Pufferelemente können gepackte Datenwerten (wie R8G8B8A8-Oberflächenwerte), einzelne 8-Bit-Ganzahlen oder vier 32-Bit-Gleitkommawerte enthalten.

Puffer werden als unstrukturierte Ressource erstellt. Da es unstrukturierten ist, ein Puffer kann keine Mipmap-Ebenen enthalten, es kann nicht beim Lesen gefiltert erhalten möchten, und sie nicht Multisampling sein.

## <a name="span-idbuffertypesspanspan-idbuffertypesspanspan-idbuffertypesspanbuffer-types"></a><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Puffercache-Typen


Es folgen die Puffer Ressourcentypen von Direct3D 11 unterstützt.

-   [Vertexpuffer](#vertex-buffer)
-   [Indexpuffer](#index-buffer)
-   [Konstante Puffer](#shader-constant-buffer)

### <a name="span-idvertexbufferspanspan-idvertexbufferspanspan-idvertexbufferspanspan-idvertex-bufferspanvertex-buffer"></a><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Scheitelpunkt Puffer

Ein Scheitelpunkt-Puffer enthält die Scheitelpunkt Daten verwendet, um die Geometrie definieren. Zu den Scheitelpunktdaten gehören Positionskoordinaten, Farbdaten, Texturkoordinatendaten, Normale-Daten usw.

Das einfachste Beispiel eines Scheitelpunkts Puffers ist ein, die nur Positionsdaten enthält. Die folgende Abbildungverdeutlicht dieses Beispiel.

![Abbildung eines Vertexpuffers, der Positionsdaten enthält](images/d3d10-resources-single-element-vb2.png)

Häufiger enthält ein Vertexpuffer aber alle erforderlichen Daten, um 3D-Scheitelpunkte vollständig dazustellen. Ein Beispiel dazu könnte ein Vertexpuffer sein, der eine Position pro Scheitelpunkt sowie Normale und Texturkoordinaten enthält. Diese Daten sind in der Regel als Sätze der Elemente pro Scheitelpunkt organisiert, wie in der folgenden Abbildung dargestellt.

![Abbildungeines Vertexpuffers, der Position, Normale und Texturdaten enthält](images/d3d10-vertex-buffer-element.png)

Dieser Puffer Scheitelpunkts enthält Vertices Daten. Scheitelpunkte werden drei Elemente (Position, Normal und Textur Koordinaten) gespeichert. Position und Normale werden normalerweise mit drei 32-Bit-Gleitkommawerten und die Texturkoordinaten mit zwei 32-Bit-Gleitkommawerten angegeben.

Zugriff auf Daten aus einem Puffer Scheitelpunkts müssen Sie wissen, welche Scheitelpunkt zum Zugriff sowie die folgenden zusätzlichen Puffercache-Parameter:

-   Offset - Die Anzahl von Bytes vom Anfang des Puffers bis zu den Daten für den ersten Scheitelpunkt.
-   BaseVertexLocation - Die Anzahl der Bytes vom Offset bis zum ersten Scheitelpunkt, den der entsprechende Zeichnen-Aufruf verwendet.

Bevor Sie einen Scheitelpunkt Puffer erstellen, müssen Sie definieren des Layouts. Nachdem das Eingabe-Layout-Objekt erstellt wird, wird es in die [Phase Input Assembler (IA)](input-assembler-stage--ia-.md)binden.

### <a name="span-idindexbufferspanspan-idindexbufferspanspan-idindexbufferspanspan-idindex-bufferspanindex-buffer"></a><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Indexpuffer

Index-Puffer enthalten ganze Zahl Offsets in Scheitelpunkts Puffer und dienen zum Rendern von Primitives effizienter. Ein Indexpuffer enthält eine aufeinanderfolgende Reihe von 16-Bit- oder 32-Bit-Indizes; jeder Index wird verwendet, um einen Scheitelpunkt im Vertexpuffer zu kennzeichnen. Die folgende Abbildung enthält eine Darstellung eines Indexpuffers.

![Abbildung eines Indexpuffers](images/d3d10-index-buffer.png)

Die aufeinanderfolgenden Indizes in einem Indexpuffer werden mit den folgenden Parametern lokalisiert:

-   Offset - die Anzahl von Bytes aus der Basisadresse des Indexpuffers.
-   StartIndexLocation - gibt das erste Element der Index-Puffer aus der Basisadresse und der Offset an. Die Startposition stellt den ersten Index zu rendern.
-   IndexCount – Die Anzahl der zu berechnenden und auszugebenden Indizes.

Anfang des Indexpuffer = Index Puffer Basisadresse Offset (Bytes) + StartIndexLocation \ * ElementSize (Bytes).

In dieser Berechnung ist ElementSize die Größe der einzelnen Index-Puffer-Element, das zwei oder vier Bytes ist.

### <a name="span-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshader-constant-bufferspanconstant-buffer"></a><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Konstante Puffer

Ein konstanter Puffer können Sie effizient Shader-Konstanten Daten in der Pipeline bereitstellen. Sie können einen Konstanten Puffer zum Speichern der Ergebnisse im Freigabefenster Stream-Ausgabe verwenden. Konzept, sucht ein konstanter Puffer wie bei einem einzelnen Element Scheitelpunkts Puffer, wie in der folgenden Abbildung dargestellt.

![Abbildung eines Shader-Konstantenpuffers](images/d3d10-shader-resource-buffer.png)

Jedes Element speichert eine Konstante mit ein bis vier Komponenten, durch das Format der gespeicherten Daten bestimmt.

Ein konstanter Puffer kann nur ein einzelnes binden Flag verwenden, die mit einem anderen binden Flag kombiniert werden können.

Um einen Puffer Shader-Konstante aus einer Shader lesen, verwenden Sie eine HLSL Last-Funktion. Für jede Shader-Phase können bis zu 15 Shaderkonstantenpuffer vorhanden sein, die jeweils bis zu 4096 Konstanten umfassen können.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Vertex- und Indexpuffer](vertex-and-index-buffers.md)

 

 




