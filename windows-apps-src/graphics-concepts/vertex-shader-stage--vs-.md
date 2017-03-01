---
title: Scheitelpunkt-Shader- (VS) Phase
description: "Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte und führt dabei in der Regel Vorgänge wie Transformationen, das Anwenden von Skins und Beleuchtung durch. Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt."
ms.assetid: 5133C4BB-B4E6-4697-9276-F718AD44869C
keywords:
- Scheitelpunkt-Shader- (VS) Phase
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 6819826d829036c6b2cb2de4f2f42025820de9fe
ms.lasthandoff: 02/07/2017

---

# <a name="vertex-shader-vs-stage"></a>Scheitelpunkt-Shader- (VS) Phase


Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte und führt dabei in der Regel Vorgänge wie Transformationen, das Anwenden von Skins und Beleuchtung durch. Ein Scheitelpunkt-Shader verarbeitet immer einen einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt.

## <a name="span-idpurposeandusesspanspan-idpurposeandusesspanspan-idpurposeandusesspanpurpose-and-uses"></a><span id="Purpose_and_uses"></span><span id="purpose_and_uses"></span><span id="PURPOSE_AND_USES"></span>Zweck und Verwendung


Die Scheitelpunkt-Shader- (VS) Phase wird für einzelne Scheitelpunktverarbeitungen verwendet, wie etwa:

-   Transformationen
-   Anwenden von Skins
-   Morphing
-   Scheitelpunktbeleuchtung

Die Scheitelpunkt-Shader-Stufe ist eine programmierbare Shader-Stufe. Sie wird im [Grafikpipeline](graphics-pipeline.md)- Diagramm als abgerundeter Block angezeigt. Dieser Shader-Stufe verwendet Shadermodell 4.0 [gemeinsamer Shaderkern](https://msdn.microsoft.com/library/windows/desktop/bb509580).

Die Scheitelpunkt-Shader- (VS) Phase verarbeitet Scheitelpunkte aus dem Eingabe-Assembler. Ein Scheitelpunkt-Shader operiert immer auf einem einzigen Eingabescheitelpunkt und erzeugt daraus einen einzigen Ausgabescheitelpunkt. Die Scheitelpunkt-Shader-Phase muss immer für auszuführende Pipeline aktiv sein. Wenn keine Scheitelpunktänderung oder -transformation erforderlich ist, muss ein Pass-Through-Scheitelpunkt-Shader erstellt und auf die Pipeline festgelegt werden.

Jeder Scheitelpunkt-Shader-Eingabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren (mit jeweils bis zu 4 Komponenten) bestehen. Jeder Ausgabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren mit jeweils 4 Komponenten bestehen. Alle Scheitelpunkt-Shader benötigen mindestens eine Eingabe und eine Ausgabe, die so klein wie ein Skalarwert sein können.

Der Scheitelpunkt-Shader-Phase kann zwei vom System generierte Werte vom Eingabe-Assembler verarbeiten: Scheitelpunkt-ID und Instanz-ID (vgl. Systemwerte und Semantik). Da Scheitelpunkt-ID und Instanz-ID auf Scheitelpunktebene bedeutsam sind und von der Hardware generierte IDs nur in di erste Phase eingegeben werden können, die sie versteht, können diese ID-Werte nur in die Scheitelpunkt-Shader-Phase eingegeben werden.

Scheitelpunkt-Shader werden immer auf allen Scheitelpunkten ausgeführt, einschließlich benachbarter Scheitelpunkte in Eingabe-Grundtyp-Topologien mit Nachbarschaft. Die Ausführungshäufigkeit des Scheitelpunkt-Shaders kann von der CPU mithilfe der VSInvocations-Pipelinestatistik abgefragt werden.

Ein Scheitelpunkt-Shader kann Lade- und Textursampling-Vorgänge durchführen, bei denen Bildschirmbereichsableitungen nicht erforderlich sind (mithilfe systeminterner HLSL-Funktionen: [Sample (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509695), [SampleCmpLevelZero (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509697) und [SampleGrad (DirectX HLSL Texture Object)](https://msdn.microsoft.com/library/windows/desktop/bb509698)).

## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span id="Input"></span><span id="input"></span><span id="INPUT"></span>Eingabe


Ein einzelner Scheitelpunkt- mit den vom System generierten Werten Scheitelpunkt-ID und Instanz-ID. Jeder Scheitelpunkt-Shader-Eingabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren (mit jeweils bis zu 4 Komponenten) bestehen.

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>Ausgabe


Ein einzelner Scheitelpunkt. Jeder Ausgabescheitelpunkt kann aus bis zu 16 32-Bit-Vektoren mit jeweils 4 Komponenten bestehen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Grafikpipeline](graphics-pipeline.md)

 

 





