---
title: "Regeln für Gleitkommazahlen"
description: "Direct3D unterstützt mehrere Darstellungen für Gleitkommazahlen. Alle Gleitkommaberechnungen erfolgen gemäß einer bestimmten Teilmenge der IEEE 754-Regeln für 32-Bit-Gleitkommazahlen einfacher Genauigkeit."
ms.assetid: 3B0C95E2-1025-4F70-BF14-EBFF2BB53AFF
keywords:
- "Regeln für Gleitkommazahlen"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: c36ef44bf02e6bbfe7a201004b19b2e99c1c27ca
ms.lasthandoff: 02/07/2017

---

# <a name="span-iddirect3dconceptsfloating-pointrulesspanfloating-point-rules"></a><span id="direct3dconcepts.floating-point_rules"></span>Regeln für Gleitkommazahlen


Direct3D unterstützt mehrere Darstellungen für Gleitkommazahlen. Alle Gleitkommaberechnungen erfolgen gemäß einer bestimmten Teilmenge der IEEE 754-Regeln für 32-Bit-Gleitkommazahlen einfacher Genauigkeit.

## <a name="span-idalpha32bitspanspan-idalpha32bitspan32-bit-floating-point-rules"></a><span id="alpha_32_bit"></span><span id="ALPHA_32_BIT"></span>Regeln für 32-Bit-Gleitkommazahlen


Es gibt zwei Gruppen von Regeln – solche, die IEEE-754 entsprechen, und solche, die von diesem Standard abweichen.

### <a name="span-idalpha754rulesspanspan-idalpha754rulesspanspan-idalpha754rulesspanhonored-ieee-754-rules"></a><span id="alpha_754_Rules"></span><span id="alpha_754_rules"></span><span id="ALPHA_754_RULES"></span>Regeln gemäß IEEE-754

Einige dieser Regeln entsprechen nur einer einzigen der von IEEE-754 angebotenen Optionen.

-   Die Division durch 0 ergibt +/-INF. Ausnahme: 0/0 ergibt NaN.
-   Die Berechnung des Logarithmus von (+/-) 0 ergibt -INF.
     

    Die Berechnung des Logarithmus eines negativen Werts (außer -0) ergibt NaN.
-   Die Berechnung der reziproken Quadratwurzel (rsq) oder der Quadratwurzel (sqrt) einer negativen Zahl ergibt NaN.
     

    Die Ausnahme ist -0: sqrt(-0) ergibt -0, und rsq(-0) ergibt -INF.
-   INF - INF = NaN
-   (+/-)INF / (+/-)INF = NaN
-   (+/-)INF \* 0 = NaN
-   NaN (beliebiger Operand) beliebiger Wert = NaN
-   Die Vergleiche EQ, GT, GE, LT und LE liefern **FALSE**, wenn einer der Operanden der NaN-Wert ist oder beide diesen Wert besitzen.
-   Bei Vergleichen wird das Vorzeichen von 0 ignoriert (somit ist +0 gleich -0).
-   Der Vergleich NE ergibt **TRUE**, wenn einer der Operanden der NaN-Wert ist oder beide diesen Wert besitzen.
-   Vergleiche mit +/-INF ergeben für jeden Wert (außer NaN) das richtige Ergebnis.

### <a name="span-idalpha754deviationsspanspan-idalpha754deviationsspanspan-idalpha754deviationsspandeviations-or-additional-requirements-from-ieee-754-rules"></a><span id="alpha_754_Deviations"></span><span id="alpha_754_deviations"></span><span id="ALPHA_754_DEVIATIONS"></span>Abweichungen von IEEE-754-Regeln oder zusätzliche Voraussetzungen

-   Gemäß IEEE-754 muss ein Gleitkommavorgang als Ergebnis den einem unendlich genauen Ergebnis nächstliegenden darstellbaren Wert liefern (sog. mathematisches Runden).

    Direct3D 11 und höher definieren dieselben Anforderungen wie IEEE-754: 32-Bit-Gleitkommavorgänge müssen Resultate mit einer Genauigkeit von 0,5 ULP (Unit in Last Place) für unendlich genaue Ergebnisse liefern. Dies bedeutet beispielsweise, dass Hardware keine mathematische Rundung durchführen muss, sondern Ergebnisse nach 32 Bits abschneiden darf, da das zu einem Fehler von höchstens 0,5 ULP führen würde. Diese Regel gilt nur für Addition, Subtraktion und Multiplikation.

    Frühere Direct3D-Versionen definieren eine tolerantere Anforderung als IEEE-754: 32-Bit-Gleitkommavorgänge müssen Resultate mit einer Genauigkeit von 1 ULP (Unit in Last Place) für unendlich genaue Ergebnisse liefern. Dies bedeutet beispielsweise, dass Hardware keine mathematische Rundung durchführen muss, sondern Ergebnisse nach 32 Bits abschneiden darf, da das zu einem Fehler von höchstens 1 ULP führen würde.

-   Ausnahmen für Gleitkommaberechnungen, Statusbits oder Traps werden nicht unterstützt.
-   In allen mathematischen Gleitkommavorgängen werden Ein- oder Ausgabewerte, bei denen es sich um denormalisierte Werte (Denorms) handelt, auf Null gesetzt (Flush-To-Zero), wobei das Vorzeichen erhalten bleibt. Ausnahmen werden für alle E/A- oder Datenverschiebevorgänge gemacht, bei denen die Daten unverändert bleiben.
-   Zustände, die Gleitkommawerte enthalten, beispielsweise Werte für Viewport MinDepth/MaxDepth oder BorderColor, können als denormalisierte Werte bereitgestellt und möglicherweise auf Null gesetzt werden, bevor die Hardware sie verwendet.
-   Min- oder Max-Vorgänge setzen Denorms für den Vergleich auf Null, aber das Ergebnis muss nicht unbedingt ein solcher Denorm sein.
-   NaN als Eingabe für einen Vorgang ergibt immer NaN als Ausgabe. Jedoch muss das genaue Bitmuster des NaN-Werts dabei nicht erhalten bleiben (es sei denn, der Vorgang ist eine reine Verschiebeanweisung – eine solche ändert keine Daten).
-   Min- oder oder Max-Vorgänge, bei denen nur ein Operand der NaN-Wert ist, geben den anderen Operanden als Ergebnis zurück (im Gegensatz zu den weiter oben behandelten Vergleichsregeln). Dies ist eine IEEE 754R-Regel.

    Die IEEE-754R-Spezifikation für Min- und Max-Vorgänge mit Gleitkommazahlen legt Folgendes fest: Ist eine der Eingaben ein QNaN-Wert (Quiet NaN), muss das Ergebnis des Vorgangs der andere Parameter sein. Beispiel:

    ```ManagedCPlusPlus
    min(x,QNaN) == min(QNaN,x) == x (same for max)
    ```

    Die überarbeitete Version der IEEE-754R-Spezifikation definiert ein anderes Verhalten für die Min- und Max-Vorgänge, wenn in der Eingabe ein QNaN-Wert durch einen SNaN-Wert (Signaling NaN) ersetzt wird:

    ```ManagedCPlusPlus
    min(x,SNaN) == min(SNaN,x) == QNaN (same for max)
     
    ```

    In der Regel folgt Direct3D bezüglich der Arithmetik den Standards IEEE-754 und IEEE-754R. Aber in diesem Fall liegt eine Abweichung vor.

    Die arithmetischen Regeln in Direct3D 10 und höher unterscheiden nicht zwischen Quiet NaN-Werten und Signaling NaN-Werten (QNaN statt SNaN). Alle NaN-Werte werden in gleicher Weise behandelt. In Min- und Max-Vorgängen verhält sich Direct3D für jeden NaN-Wert so, wie es die IEEE-754R-Definition für einen QNaN-Wert vorschreibt. (Der Vollständigkeit halber: Sind beide Eingaben NaN-Werte, wird irgendein NaN-Wert zurückgegeben.)

-   Eine andere IEEE 754R-Regel besagt: min(-0,+0) == min(+0,-0) == - 0 und max(-0,+0) == max(+0,-0) == +0. Es wird also das Vorzeichen berücksichtigt, im Gegensatz zu den weiter oben genannten Vergleichsregeln für eine vorzeichenbehaftete Null. Direct3D empfiehlt hier das IEEE 754R-Verhalten, erzwingt es jedoch nicht. Es ist zulässig, dass das Ergebnis eines Vergleichs von Nullen von der Reihenfolge der Parameter abhängig ist, wenn die Vergleichsmethode die Vorzeichen ignoriert.
-   x\*1.0f ergibt immer x (außer für auf Null gesetzte Denorms).
-   x/1.0f ergibt immer x (außer für auf Null gesetzte Denorms).
-   x +/- 0.0f ergibt immer x (außer für auf Null gesetzte Denorms). Es gilt aber -0 + 0 = +0.
-   Fused-Vorgänge (z. B. mad und dp3) liefern Ergebnisse, die nicht ungenauer sind als die denkbar schlechteste serielle Anordnung einer Auswertung der Unfused-Erweiterung des Vorgangs. Bezüglich der Toleranz ist die Definition der denkbar schlechtesten Anordnung keine feste Definition für einen bestimmten Fused-Vorgang, sondern sie ist von den jeweiligen Eingabewerten abhängig. Für jeden einzelnen Schritt in einer Unfused-Erweiterung ist eine Toleranz von 1 ULP zugelassen (oder für jede Anweisung, die Direct3D mit einer höheren Toleranz als 1 ULP aufruft, ist diese höhere Toleranz zulässig).
-   Für Fused-Vorgänge gelten dieselben NaN-Regeln wie für Unfused-Vorgänge.
-   Die Toleranz für sqrt und rcp beträgt 1 ULP. Für die Shader-Anweisungen [**rcp**](https://msdn.microsoft.com/library/windows/desktop/hh447205) zur Berechnung des Kehrwerts und [**rsq**](https://msdn.microsoft.com/library/windows/desktop/hh447221) zur Berechnung der reziproken Quadratwurzel gelten eigene, ebenfalls weniger strikte Genauigkeitsanforderungen.
-   Multiplizieren und Dividieren erfolgt jeweils auf der Genauigkeitsebene von 32-Bit-Gleitkommavorgängen (0,5 ULP Genauigkeit für das Multiplizieren und 1,0 ULP für reziproke Vorgänge). Wenn x/y direkt implementiert ist, muss die Genauigkeit der Ergebnisse größer oder gleich der Genauigkeit sein, die eine Methode mit zwei Schritten liefert.

## <a name="span-iddoubleprec64bitspanspan-iddoubleprec64bitspan64-bit-double-precision-floating-point-rules"></a><span id="double_prec_64_bit"></span><span id="DOUBLE_PREC_64_BIT"></span>Regeln für 64-Bit-Gleitkommazahlen (doppelte Genauigkeit)


Hardware und Anzeigetreiber unterstützen optional Gleitkommazahlen doppelter Genauigkeit. Wenn Sie [**ID3D11Device::CheckFeatureSupport**](https://msdn.microsoft.com/library/windows/desktop/ff476497) mit [**D3D11\_FEATURE\_DOUBLES**](https://msdn.microsoft.com/library/windows/desktop/ff476124#d3d11-feature-doubles) aufrufen, setzt der Treiber **DoublePrecisionFloatShaderOps** in [**D3D11\_FEATURE\_DATA\_DOUBLES**](https://msdn.microsoft.com/library/windows/desktop/ff476127) auf TRUE, um anzugeben, dass die Unterstützung verfügbar ist. Treiber und Hardware müssen dann alle Gleitkommaanweisungen mit doppelter Genauigkeit unterstützen.

Anweisungen mit doppelter Genauigkeit befolgen IEEE 754R-Verhaltensanforderungen.

Für Daten mit doppelter Genauigkeit ist Unterstützung zum Generieren denormalisierter Werte erforderlich (kein Flush-To-Zero-Verhalten). Entsprechend lesen Anweisungen denormalisierte Daten nicht als vorzeichenbehaftete Nullen, sondern berücksichtigen die Denorm-Werte.

## <a name="span-idalpha16bitspanspan-idalpha16bitspan16-bit-floating-point-rules"></a><span id="alpha_16_bit"></span><span id="ALPHA_16_BIT"></span>Regeln für 16-Bit-Gleitkommazahlen


Direct3D unterstützt auch 16-Bit-Darstellungen von Gleitkommazahlen.

Format:

-   1 Vorzeichenbit (s) an der MSB-Position
-   5 Bits für den Biased-Exponenten (e)
-   10 Fraktionsbits (f) mit einem zusätzliche Hidden-Bit

Für einen float16-Wert (v) gelten folgende Regeln:

-   Wenn e == 31 und f != 0, dann ist v unabhängig von s ein NaN-Wert.
-   Wenn e == 31 und f == 0, dann v = (-1)s\*Unendlich (vorzeichenbehaftetes Unendlich)
-   Wenn e zwischen 0 und 31 liegt, dann v = (-1)s\*2(e-15)\*(1.f)
-   Wenn e == 0 und f != 0, dann v = (-1)s\*2(e-14)\*(0.f) (denormalisierte Zahlen)
-   Wenn e == 0 und f == 0, dann v = (-1)s\*0 (vorzeichenbehaftete Null)

Die Regeln für 32-Bit-Gleitkommazahlen gelten auch für 16-Bit-Gleitkommazahlen, die an das weiter oben beschriebene Bitlayout angepasst sind. Dabei gibt es folgende Ausnahmen:

-   Genauigkeit: Unfused-Vorgänge mit 16-Bit-Gleitkommazahlen liefern als Ergebnis den einem unendlich genauen Ergebnis nächstliegenden darstellbaren Wert (mathematisches Runden gemäß IEEE-754, angewendet auf 16-Bit-Werte). Für 32-Bit-Gleitkommazahlen gilt eine Toleranz von 1 ULP. Für 16-Bit-Gleitkommazahlen gilt ein Toleranz von 0,5 ULP bei Unfused-Vorgängen und von 0,6 ULP bei Fused-Vorgängen.
-   16-Bit-Gleitkommazahlen erhalten Denorms.

## <a name="span-idalpha11bitspanspan-idalpha11bitspan11-bit-and-10-bit-floating-point-rules"></a><span id="alpha_11_bit"></span><span id="ALPHA_11_BIT"></span>Regeln für 11-Bit- und 10-Bit-Gleitkommazahlen


Direct3D unterstützt auch 11-Bit- und 10-Bit-Gleitkommazahlenformate.

Format:

-   Kein Vorzeichenbit
-   5 Bits für den Biased-Exponenten (e)
-   6 Fraktionsbits (f) für ein 11-Bit-Format, 5 Fraktionsbits (f) für ein 10-Bit-Format, dazu jeweils ein zusätzliches Hidden-Bit.

Für einen float11/float10-Wert (v) gelten folgende Regeln:

-   Wenn e == 31 und f != 0, dann ist v ein NaN-Wert.
-   Wenn e == 31 und f == 0, dann v = +Unendlich
-   Wenn e zwischen 0 und 31 liegt, dann v = 2(e-15)\*(1.f)
-   Wenn e == 0 und f != 0, dann v = \*2(e-14)\*(0.f) (denormalisierte Zahlen)
-   Wenn e == 0 und f == 0, dann v = 0 (Null)

Die Regeln für 32-Bit-Gleitkommazahlen gelten auch für 11-Bit- und 10-Bit-Gleitkommazahlen, die an das weiter oben beschriebene Bitlayout angepasst sind. Dabei gibt es folgende Ausnahmen:

-   Genauigkeit: Regeln für 32-Bit-Gleitkommazahlen definieren eine Genauigkeit 0,5 ULP.
-   10/11-Bit-Gleitkommazahlen erhalten Denorms.
-   Bei jedem Vorgang, der zu einer Zahl kleiner als Null führen würde, wird das Ergebnis auf Null beschränkt.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Anhänge](appendix.md)

[Ressourcen](https://msdn.microsoft.com/library/windows/desktop/ff476894)

[Texturen](https://msdn.microsoft.com/library/windows/desktop/ff476902)

 

 





