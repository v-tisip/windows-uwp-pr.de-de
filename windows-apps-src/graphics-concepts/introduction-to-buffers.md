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
ms.localizationpriority: medium
ms.openlocfilehash: 14e78aec9afa361b2627d62d92f0ee7d7ab0565b
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6140261"
---
# <a name="introduction-to-buffers"></a>Einführung zu Puffern


Eine Pufferressource ist eine Sammlung vollständig typisierter Daten, die zu Elementen gruppiert werden. Puffer speichern Daten, wie z.B. Texturkoordinaten in einem *Scheitelpunktpuffer*, Indizes in einem *Indexpuffer*, Shader-Konstantendaten in einem *Konstantenpuffer*, Positionsvektoren, normale Vektoren oder den Gerätezustand.

Ein Puffer-Element besteht aus 1 bis 4 Komponenten. Pufferelemente können gepackte Datenwerten (wie R8G8B8A8-Oberflächenwerte), einzelne 8-Bit-Ganzahlen oder vier 32-Bit-Gleitkommawerte enthalten.

Puffer werden als unstrukturierte Ressource erstellt. Da es unstrukturierte handelt, ein Puffer kann keine Mipmap-Ebenen enthalten, es kann nicht beim Lesen gefiltert abzurufen, und es nicht mit Multisampling.

## <a name="span-idbuffertypesspanspan-idbuffertypesspanspan-idbuffertypesspanbuffer-types"></a><span id="Buffer_Types"></span><span id="buffer_types"></span><span id="BUFFER_TYPES"></span>Puffertypen


Im folgenden werden die Puffer-Ressourcentypen, die von Direct3D 11 unterstützt.

-   [Vertexpuffer](#vertex-buffer)
-   [Indexpuffer](#index-buffer)
-   [Konstantenpuffer](#shader-constant-buffer)

### <a name="span-idvertexbufferspanspan-idvertexbufferspanspan-idvertexbufferspanspan-idvertex-bufferspanvertex-buffer"></a><span id="Vertex_Buffer"></span><span id="vertex_buffer"></span><span id="VERTEX_BUFFER"></span><span id="vertex-buffer"></span>Vertexpuffer

Ein Vertexpuffer enthält Scheitelpunktdaten, die zur Definition Ihrer Geometrie verwendet. Zu den Scheitelpunktdaten gehören Positionskoordinaten, Farbdaten, Texturkoordinatendaten, Normale-Daten usw.

Das einfachste Beispiel für einen Vertexpuffer ist eine, die nur Positionsdaten enthält. Die folgende Abbildungverdeutlicht dieses Beispiel.

![Abbildung eines Vertexpuffers, der Positionsdaten enthält](images/d3d10-resources-single-element-vb2.png)

Häufiger enthält ein Vertexpuffer aber alle erforderlichen Daten, um 3D-Scheitelpunkte vollständig dazustellen. Ein Beispiel dazu könnte ein Vertexpuffer sein, der eine Position pro Scheitelpunkt sowie Normale und Texturkoordinaten enthält. Diese Daten sind in der Regel als Sätze der Elemente pro Scheitelpunkt organisiert, wie in der folgenden Abbildung dargestellt.

![Abbildungeines Vertexpuffers, der Position, Normale und Texturdaten enthält](images/d3d10-vertex-buffer-element.png)

Dieser Vertexpuffer enthält Daten pro Vertex; Jeder Scheitelpunkt speichert drei Elemente (Position, normale und Texturkoordinaten). Position und Normale werden normalerweise mit drei 32-Bit-Gleitkommawerten und die Texturkoordinaten mit zwei 32-Bit-Gleitkommawerten angegeben.

Um Daten aus einem Vertexpuffer zugreifen müssen Sie wissen, welche Scheitelpunkt zu Zugriff sowie die folgenden zusätzlichen Puffer-Parameter:

-   Offset - Die Anzahl von Bytes vom Anfang des Puffers bis zu den Daten für den ersten Scheitelpunkt.
-   BaseVertexLocation - Die Anzahl der Bytes vom Offset bis zum ersten Scheitelpunkt, den der entsprechende Zeichnen-Aufruf verwendet.

Bevor Sie einen Vertexpuffer erstellen, müssen Sie das Layout definieren. Nachdem das eingabelayout Objekt erstellt wurde, wird es auf die [Eingabe-Assembler (IA)-Phase](input-assembler-stage--ia-.md)binden.

### <a name="span-idindexbufferspanspan-idindexbufferspanspan-idindexbufferspanspan-idindex-bufferspanindex-buffer"></a><span id="Index_Buffer"></span><span id="index_buffer"></span><span id="INDEX_BUFFER"></span><span id="index-buffer"></span>Indexpuffer

Indexpuffer enthalten Ganzzahl-Offsets in Vertexpuffern und werden zum effizienteren Rendern von Grundtypen verwendet. Ein Indexpuffer enthält eine aufeinanderfolgende Reihe von 16-Bit- oder 32-Bit-Indizes; jeder Index wird verwendet, um einen Scheitelpunkt im Vertexpuffer zu kennzeichnen. Die folgende Abbildung enthält eine Darstellung eines Indexpuffers.

![Abbildung eines Indexpuffers](images/d3d10-index-buffer.png)

Die aufeinanderfolgenden Indizes in einem Indexpuffer werden mit den folgenden Parametern lokalisiert:

-   Offset - die Anzahl der Bytes aus der Basis-Adresse des Indexpuffers.
-   StartIndexLocation - gibt das erste Index-Puffer-Element aus der Basis Adresse und den Offset an. Ausgangspfad stellt den ersten Index zu rendern.
-   IndexCount – Die Anzahl der zu berechnenden und auszugebenden Indizes.

Beginn der Indexpuffer = Index Puffer Base Adresse + Offset (Bytes) + StartIndexLocation \ * ElementSize (Bytes).

Bei der Berechnung ist ElementSize die Größe der einzelnen Elemente der Index-Puffer, d. h. zwei oder vier Bytes.

### <a name="span-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshaderconstantbufferspanspan-idshader-constant-bufferspanconstant-buffer"></a><span id="Shader_Constant_Buffer"></span><span id="shader_constant_buffer"></span><span id="SHADER_CONSTANT_BUFFER"></span><span id="shader-constant-buffer"></span>Konstantenpuffer

Ein Konstantenpuffer können Sie Shader-Konstanten-Daten an die Pipeline effizient zu liefern. Sie können einen Konstantenpuffer zum Speichern der Ergebnisse der Stream-Ausgabe-Stufe verwenden. Vom Konzept her sieht ein Konstantenpuffer wie ein Vertexpuffer mit einem Element, wie in der folgenden Abbildung dargestellt.

![Abbildung eines Shader-Konstantenpuffers](images/d3d10-shader-resource-buffer.png)

Jedes Element speichert eine Konstante mit ein bis vier Komponenten, durch das Format der gespeicherten Daten bestimmt.

Ein konstanter Puffer kann nur ein bindungskennzeichen mit einzelnen verwenden, die mit allen anderen bindungskennzeichen kombiniert werden kann.

Um Shaderkonstanten Puffer von einem Shader zu lesen, verwenden Sie eine HLSL-Load-Funktion. Für jede Shader-Phase können bis zu 15 Shaderkonstantenpuffer vorhanden sein, die jeweils bis zu 4096 Konstanten umfassen können.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Vertex- und Indexpuffer](vertex-and-index-buffers.md)

 

 




