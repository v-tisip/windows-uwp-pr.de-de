---
title: Textursampling-Features für Streamingressourcen
description: 'Textursampling-Features für Streamingressourcen enthalten: Abrufen von Feedback zum Shaderstatus zugeordneter Bereiche, Überprüfen, ob alle Daten, auf die zugegriffen wird, in der Ressource zugeordnet wurden, Klammerung, damit Shader Bereiche in Mipmap-Streamingressourcen vermeiden, die nicht zugeordnet wurden, und Ermitteln der minimalen Detailtiefe (Level-of-Detail, LOD), die für den gesamten Speicherbedarf einer Texturfilterung vollständig zugeordnet ist.'
ms.assetid: C2B2DD69-8354-417A-894D-6235A8B48B53
keywords:
- Textursampling-Features für Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 0066d38aaa3f5802ff5b1d380d405e60d90cad49
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7558159"
---
# <a name="streaming-resources-texture-sampling-features"></a>Textursampling-Features für Streamingressourcen


Textursampling-Features für Streamingressourcen enthalten: Abrufen von Feedback zum Shaderstatus zugeordneter Bereiche, Überprüfen, ob alle Daten, auf die zugegriffen wird, in der Ressource zugeordnet wurden, Klammerung, damit Shader Bereiche in Mipmap-Streamingressourcen vermeiden, die nicht zugeordnet wurden, und Ermitteln der minimalen Detailtiefe (Level-of-Detail, LOD), die für den gesamten Speicherbedarf einer Texturfilterung vollständig zugeordnet ist.

## <a name="span-idrequirementsofstreamingresourcestexturesamplingfeaturesspanspan-idrequirementsofstreamingresourcestexturesamplingfeaturesspanspan-idrequirementsofstreamingresourcestexturesamplingfeaturesspanrequirements-of-streaming-resources-texture-sampling-features"></a><span id="Requirements_of_streaming_resources_texture_sampling_features"></span><span id="requirements_of_streaming_resources_texture_sampling_features"></span><span id="REQUIREMENTS_OF_STREAMING_RESOURCES_TEXTURE_SAMPLING_FEATURES"></span>Anforderungen von Textursampling-Features für Streamingressourcen


Die hier beschriebenen Textursampling-Features benötigen die [Ebene2](tier-2.md) der Streamingressourcenunterstützung.

## <a name="span-idshaderstatusfeedbackaboutmappedareasspanspan-idshaderstatusfeedbackaboutmappedareasspanspan-idshaderstatusfeedbackaboutmappedareasspanshader-status-feedback-about-mapped-areas"></a><span id="Shader_status_feedback_about_mapped_areas"></span><span id="shader_status_feedback_about_mapped_areas"></span><span id="SHADER_STATUS_FEEDBACK_ABOUT_MAPPED_AREAS"></span>Feedback zum Shaderstatus zugeordneter Bereiche


Alle Shaderanweisungen, die eine Streamingressource lesen oder in diese schreiben, führen dazu, dass Statusinformationen aufgezeichnet werden. Dieser Status wird als zusätzlicher optionaler Rückgabewert für jede Anweisung zum Zugreifen auf eine Ressource verfügbar gemacht, die in ein temporäres 32-Bit-Register übernommen wird. Der Inhalt des Rückgabewerts ist nicht transparent. Das heißt, ein direktes Lesen durch das Shaderprogramm ist nicht zulässig. Aber Sie können die Statusinformationen mit der Funktion [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) extrahieren.

## <a name="span-idfullymappedcheckspanspan-idfullymappedcheckspanspan-idfullymappedcheckspanfully-mapped-check"></a><span id="Fully_mapped_check"></span><span id="fully_mapped_check"></span><span id="FULLY_MAPPED_CHECK"></span>Überprüfen auf vollständige Zuordnung


Die Funktion [**CheckAccessFullyMapped**](https://msdn.microsoft.com/library/windows/desktop/dn292083) interpretiert den von einem Speicherzugriff zurückgegebenen Status und gibt an, ob alle Daten, auf die zugegriffen wird, in der Ressource zugeordnet wurden. **CheckAccessFullyMapped** gibt „true” (0xFFFFFFFF) zurück, wenn Daten zugeordnet wurden, oder „false” (0x00000000), wenn Daten nicht zugeordnet wurden.

Bei Filterungsvorgängen ist die Gewichtung eines bestimmten Texels manchmal 0,0. Ein Beispiel ist ein lineares Muster mit Texturkoordinaten, die direkt auf die Mitte eines Texels fallen: 3andere Texel (welche das sind, variiert je nach Hardware) tragen zur Filterung bei, aber mit einer Gewichtung von0. Diese Texel mit der Gewichtung0 tragen nicht zum Filterungsergebnis bei. Wenn sie also auf **NULL**-Kacheln fallen, werden sie nicht als nicht zugeordneter Zugriff gezählt. Die gleiche Garantie gilt für Texturfilter, die mehrere Mip-Ebenen enthalten. Wenn die Texel für eines der Mipmaps nicht zugeordnet sind, aber die Gewichtung für diese Texel0 ist, zählen diese Texel nicht als nicht zugeordneter Zugriff.

Bei einem Sampling aus einem Format, das über weniger als 4Komponenten verfügt (z.B. DXGI\_FORMAT\_R8\_UNORM), führen alle Texel, die auf **NULL**-Kacheln fallen, zu einem **NULL**-zugeordneten Zugriff, unabhängig davon, welche Komponenten der Shader tatsächlich im Ergebnis untersucht. Zum Beispiel müsste beim Lesen aus R8\_UNORM und beim Maskieren des gelesenen Ergebnisses im Shader mit .gba/.yzw die Textur überhaupt nicht gelesen werden. Wenn die Adresse des Texels aber eine **NULL**-zugeordnete Kachel ist, wird der Vorgang trotzdem als **NULL**-Zuordnungszugriff gewertet.

Der Shader kann den Status überprüfen und bei einem Fehler alle gewünschten Vorgehensweise fortsetzen. Zum Beispiel kann eine Vorgehensweise die Protokollierung von „Fehlern” (z.B. über UAV-Schreibvorgänge) und/oder Ausführen eines weiteren Lesevorgangs mit der Klammerung an eine undifferenziertere zugeordnete LOD sein. Eine Anwendung könnte erfolgreiche Zugriffe auch nachverfolgen, um zu ermitteln, auf welchen Teil der zugeordneten Gruppe von Kacheln zugegriffen wurde.

Ein Problem für die Protokollierung besteht darin, dass kein Mechanismus vorhanden ist, um die genaue Gruppe von Kacheln zu erfassen, auf die zugegriffen worden wäre. Die Anwendung kann vorsichtige Schätzungen auf Basis der Kenntnis der Koordinaten vornehmen, die für den Zugriff verwendet wurden, sowie die LOD-Anweisung verwenden. Zum Beispiel gibt [**tex2Dlod**](https://msdn.microsoft.com/library/windows/desktop/bb509680)) die Hardware-LOD-Berechnung zurück.

Ein weiteres Problem besteht darin, dass viele Zugriffe auf dieselben Kacheln erfolgen, sodass viele redundante Protokolleinträge und möglicherweise Konflikte im Arbeitsspeicher auftreten. Es wäre praktisch, wenn die Hardware über eine Option verfügen würde, Kachelzugriffe nicht zu erfassen, wenn diese schon vorher an anderer Stelle erfasst wurden. Vielleicht könnte der Status einer derartigen Verfolgung von der API (wahrscheinlich an Framegrenzen) zurückgesetzt werden.

## <a name="span-idper-sampleminlodclampspanspan-idper-sampleminlodclampspanspan-idper-sampleminlodclampspanper-sample-minlod-clamp"></a><span id="Per-sample_MinLOD_clamp"></span><span id="per-sample_minlod_clamp"></span><span id="PER-SAMPLE_MINLOD_CLAMP"></span>MinLOD-Klammerung pro Sampling


Damit Shader Bereiche in Mipmap-Streamingressourcen vermeiden, die nicht zugeordnet wurden, verfügen die meisten Shaderanweisungen, bei denen ein Sampler (Filterung) verwendet wird, über einen Modus, in dem der Shader einen zusätzlichen float32-Parameter für die MinLOD-Klammerung an das Texturbeispiel übergeben kann. Dieser Wert befindet sich im Mipmap-Nummernraum der Ansicht, im Gegensatz zu der zugrunde liegenden Ressource.

Die Hardware führt` max(fShaderMinLODClamp,fComputedLOD) `an derselben Position in der LOD-Berechnung aus, an der die MinLOD-Klammerung pro Ressource auftritt, was auch ein [**max**](https://msdn.microsoft.com/library/windows/desktop/bb509624)() darstellt.

Ist das Ergebnis der LOD-Klammerung pro Sampling und anderer im Sampler definierten LOD-Klammerungen eine leere Gruppe, ist das Ergebnis der gleiche „Zugriff außerhalb der Grenzen” wie bei der MinLOD-Klammerung pro Ressource: 0für Komponenten im Oberflächenformat und Standardwerte für fehlende Komponenten.

Die LOD-Anweisung (z.B. [**tex2Dlod**](https://msdn.microsoft.com/library/windows/desktop/bb509680)), die der hier beschriebenen MinLOD-Klammerung pro Sampling zeitlich vorausgeht, gibt eine LOD mit und ohne Klammerung zurück. Die von dieser LOD-Anweisung zurückgegebene geklammerte LOD gibt die gesamte in der Klammerung pro Ressource enthaltene Klammerung zurück, aber keine Klammerung pro Sampling. Die Klammerung pro Sampling wird vom Shader gesteuert und ist ihm bekannt, daher kann der Autor des Shaders diese Klammerung bei Bedarf manuell auf den Rückgabewert der LOD-Anweisung anwenden.

## <a name="span-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanminmax-reduction-filtering"></a><span id="Min_Max_reduction_filtering"></span><span id="min_max_reduction_filtering"></span><span id="MIN_MAX_REDUCTION_FILTERING"></span>Min/Max-Reduzierungsfilterung


In Anwendungen können eigene Datenstrukturen verwaltet werden, die Informationen über die Zuordnungen für eine Streamingressource liefern. Ein Beispiel wäre eine Oberfläche, die ein Texel zum Speichern von Informationen für jede Kachel in einer Streamingressource enthält. Man könnte die erste LOD speichern, die einer bestimmten Kachelposition zugeordnet ist. Durch sorgfältiges Sampling dieser Datenstruktur auf ähnliche Weise, wie die Streamingressource gesampelt werden soll, kann die minimale LOD, die für den gesamten Speicherbedarf einer Texturfilterung vollständig zugeordnet ist, ermittelt werden. Um diesen Prozess zu vereinfachen, führt Direct3D11.2 einen neuen allgemeinen Samplermodus, die Min/Max-Filterung, ein.

Die Min/Max-Filterung für die LOD-Verfolgung kann auch für andere Zwecke nützlich sein, wie z.B. für das Filtern von Tiefenoberflächen.

Die Min/Max-Reduzierungsfilterung ist ein Modus für Sampler, der die gleiche Gruppe von Texeln abruft, die ein normaler Texturfilter abrufen würde. Aber anstatt die Werte zu mischen, um eine Antwort zu erstellen, gibt dieser Modus die abgerufenen min()- oder max()-Texel pro Komponente zurück (z.B. das Minimum aller R-Werte, getrennt vom Minimum aller G-Werte usw.).

Für Min/Max-Operationen gelten die arithmetischen Genauigkeitsregeln von Direct3D. Die Reihenfolge der Vergleiche spielt keine Rolle.

Bei Filterungsvorgängen, die keine Min/Max-Operationen sind, ist die Gewichtung eines bestimmten Texels manchmal 0,0. Ein Beispiel ist ein lineares Muster mit Texturkoordinaten, die direkt auf die Mitte eines Texels fallen: 3andere Texel (welche das sind, variiert je nach Hardware) tragen zur Filterung bei, aber mit einer Gewichtung von0. Für alle diese Texel, deren Gewichtung für eine andere als die Min/Max-Filterung0 wäre, würden diese Texel, auch wenn eine Min/Max-Filterung vorhanden wäre, trotzdem nicht zum Ergebnis beitragen (und die Gewichtungen wirken sich nicht anderweitig auf die Min/Max-Filterungsoperation aus).

Für die Unterstützung dieses Features wird die [Ebene2](tier-2.md) der Streamingressourcenunterstützung benötigt.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Pipelinezugriff auf Streamingressourcen](pipeline-access-to-streaming-resources.md)

 

 




