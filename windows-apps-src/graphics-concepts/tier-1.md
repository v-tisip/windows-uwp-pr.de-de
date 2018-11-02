---
title: Ebene1
description: In diesem Abschnitt wird die Unterstützung für die Ebene1 beschrieben.
ms.assetid: 153DA429-0C99-4691-AEB4-124FD9B17BE2
keywords:
- Ebene1
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 9aab54e23d59b21901e3aa4700581d2d7eeeee8e
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5942594"
---
# <a name="tier-1"></a>Ebene1


In diesem Abschnitt wird die Unterstützung für die Ebene1 beschrieben.

## <a name="span-idtier1generallimitationsspanspan-idtier1generallimitationsspanspan-idtier1generallimitationsspantier-1-general-limitations"></a><span id="Tier_1_general_limitations"></span><span id="tier_1_general_limitations"></span><span id="TIER_1_GENERAL_LIMITATIONS"></span>Allgemeine Einschränkungen Ebene 1


-   Hardware mindestens auf Funktionsebene11.0.
-   Quilting wird nicht unterstützt.
-   Keine Unterstützung für Texture1D oder Texture3D.
-   Keine Unterstützung für 2, 8 oder 16 Sample Multisampling Antialiasing (MSAA). Nur 4 x ist erforderlich, außer keine 128-BpP-Formate.
-   Kein Standard-Swizzlemuster (Layout innerhalb der 64KB großen Kacheln und die Tail-MIP-Verpackung liegen in der Verantwortung des Hardwareherstellers).
-   Zugriffseinschränkungen für die Kacheln, wenn doppelte Zuordnungen vorhanden sind. Siehe [Kachelzugriffseinschränkungen bei doppelten Zuordnungen](tile-access-limitations-with-duplicate-mappings.md)

## <a name="span-idspecificlimitationsaffectingtier1onlyspanspan-idspecificlimitationsaffectingtier1onlyspanspan-idspecificlimitationsaffectingtier1onlyspanspecific-limitations-affecting-tier-1-only"></a><span id="Specific_limitations_affecting_tier_1_only"></span><span id="specific_limitations_affecting_tier_1_only"></span><span id="SPECIFIC_LIMITATIONS_AFFECTING_TIER_1_ONLY"></span>Bestimmte Einschränkungen, die nur Ebene 1 beeinflussen


### <a name="span-idreadingwritingtostreamingresourcesthathavenullmappingsspanspan-idreadingwritingtostreamingresourcesthathavenullmappingsspanspan-idreadingwritingtostreamingresourcesthathavenullmappingsspanreadingwriting-to-streaming-resources-that-have-null-mappings"></a><span id="Reading_writing_to_streaming_resources_that_have_NULL_mappings"></span><span id="reading_writing_to_streaming_resources_that_have_null_mappings"></span><span id="READING_WRITING_TO_STREAMING_RESOURCES_THAT_HAVE_NULL_MAPPINGS"></span>Lesen/Schreiben auf Streamingressourcen mit NULL-Zuordnungen

Streamingressourcen können **NULL** Zuordnungen haben. Das Lesen von ihnen oder das Schreiben auf ihnen wird jedoch undefinierte Ergebnisse erzeugen, einschließlich der Entfernung des Geräts. Apps können dies umgehen, indem sie allen leeren Bereichen eine einzige Dummy-Seite zuordnen. Gehen Sie beim Schreiben und Rendern zu einer Seite, die mehreren Renderzielstandorten zugeordnet ist, vorsichtig vor, da die Reihenfolge der Schreibvorgänge nicht definiert sein wird.

### <a name="span-idnoshaderinstructionsforclampinglodandmappedstatusfeedbackspanspan-idnoshaderinstructionsforclampinglodandmappedstatusfeedbackspanspan-idnoshaderinstructionsforclampinglodandmappedstatusfeedbackspanno-shader-instructions-for-clamping-lod-and-mapped-status-feedback"></a><span id="No_shader_instructions_for_clamping_LOD_and_mapped_status_feedback"></span><span id="no_shader_instructions_for_clamping_lod_and_mapped_status_feedback"></span><span id="NO_SHADER_INSTRUCTIONS_FOR_CLAMPING_LOD_AND_MAPPED_STATUS_FEEDBACK"></span>Keine Shader-Anweisungen für Klammerung-LOD und zugeordneter Feedback zum Status

Shader-Anweisungen für Klammerung-LOD und Feedback zum zugeordneten Status sind nicht verfügbar. Siehe [Belichtung von HLSL-Streamingressourcen](hlsl-streaming-resources-exposure.md)

### <a name="span-idalignmentconstraintsforstandardtileshapesspanspan-idalignmentconstraintsforstandardtileshapesspanspan-idalignmentconstraintsforstandardtileshapesspanalignment-constraints-for-standard-tile-shapes"></a><span id="Alignment_constraints_for_standard_tile_shapes"></span><span id="alignment_constraints_for_standard_tile_shapes"></span><span id="ALIGNMENT_CONSTRAINTS_FOR_STANDARD_TILE_SHAPES"></span>Ausrichtungseinschränkungen für Standardkachelformen

Es ist nur sichergestellt, dass Mips (beginnend mit den besten), deren Abmessungen alles Vielfache der standardmäßigen Kachelgröße sind, die standardmäßigen Kachelformen unterstützen und einzelne willkürlich zugeordnete/nicht zugeordnete Kacheln haben können. Die erste Mipmap in einer Streamingressource, die eine Abmessung hat, die kein Vielfaches einer der standardmäßigen Kachelgröße ist, zusammen mit allen grobkörnigen Mipmaps, kann über eine nicht standardmäßige Kachelform verfügen. Dadurch passt sie sofort in N 64KB große Kacheln für diesen Satz von Mips (N an die Anwendung gemeldet). Diese N-Kacheln gelten als eine verpackte Einheit, die von der Anwendung zu jeder Zeit entweder vollständig zugeordnet oder vollständig nicht zugeordnet werden muss. Die Zuordnung der einzelnen N-Kacheln können sich an willkürlich getrennten Orten in einem Kachelpool befinden.

### <a name="span-idarrayofmipmapsthatarentamultipleofstandardtilesizespanspan-idarrayofmipmapsthatarentamultipleofstandardtilesizespanspan-idarrayofmipmapsthatarentamultipleofstandardtilesizespanarray-of-mipmaps-that-arent-a-multiple-of-standard-tile-size"></a><span id="Array_of_mipmaps_that_aren_t_a_multiple_of_standard_tile_size"></span><span id="array_of_mipmaps_that_aren_t_a_multiple_of_standard_tile_size"></span><span id="ARRAY_OF_MIPMAPS_THAT_AREN_T_A_MULTIPLE_OF_STANDARD_TILE_SIZE"></span>Array von Mipmaps, die kein Vielfaches der standardmäßigen Kachelgröße sind

Das Streamen von Ressourcen mit jeglichen Mipmaps, die kein Vielfaches der standardmäßigen Kachelgröße in allen Abmessungen sind, dürfen keine Arraygröße größer als 1 aufweisen.

### <a name="span-idswitchingbetweenreferencingtilesinatilepoolviaabufferandtextureresourcespanspan-idswitchingbetweenreferencingtilesinatilepoolviaabufferandtextureresourcespanspan-idswitchingbetweenreferencingtilesinatilepoolviaabufferandtextureresourcespanswitching-between-referencing-tiles-in-a-tile-pool-via-a-buffer-and-texture-resource"></a><span id="Switching_between_referencing_tiles_in_a_tile_pool_via_a_Buffer_and_Texture_resource"></span><span id="switching_between_referencing_tiles_in_a_tile_pool_via_a_buffer_and_texture_resource"></span><span id="SWITCHING_BETWEEN_REFERENCING_TILES_IN_A_TILE_POOL_VIA_A_BUFFER_AND_TEXTURE_RESOURCE"></span>Das Wechseln zwischen Verweisen auf Kacheln in einem Kachelpool über eine Puffer- und Strukturressource.

Zum Wechseln zwischen dem Verweisen auf Kacheln in einem Kachelpool über eine [Puffer](introduction-to-buffers.md) Ressource und dem Verweisen auf die gleichen Kacheln über eine [Textur](introduction-to-textures.md) Ressource oder umgekehrt, muss die letzte Aktualisierung der Kachelzuordnungen bzw. des Kopiervorgangs von Kachelzuordnungen, der die Zuordnungen zu diesen Kachelpool-Kacheln definiert, für dieselbe Ressourcenabmessung (Vergleich von Puffer und Textur\*) sein wie die Ressourcenabmessung, die für den Zugriff auf die Kacheln verwendet wird. Andernfalls ist das Verhalten nicht definiert ist, einschließlich der Wahrscheinlichkeit des Zurücksetzens des Geräts.

Es also bspw. nicht zulässig, die Kachelzuordnungen so zu aktualisieren, dass sie Kachelzuordnungen für einen Puffer festlegen, die Kachelzuordnungen an die gleichen Kacheln im Kachelpool über eine [**Texture2D**](https://msdn.microsoft.com/library/windows/desktop/ff471525) Ressource zu aktualisieren und dann auf die Kacheln über den Puffer zuzugreifen. Dies kann entweder mit einer erneuten Definition der Kachelzuordnungen für eine Ressource beim Wechsel zwischen Puffer- und Texturfreigabekacheln (oder umgekehrt) umgangen werden, oder indem einfach die Kacheln in einem Kachelpool zwischen Puffer und Textur-Ressourcen nicht freigegeben werden.

### <a name="span-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanspan-idminmaxreductionfilteringspanminmax-reduction-filtering"></a><span id="Min_Max_reduction_filtering"></span><span id="min_max_reduction_filtering"></span><span id="MIN_MAX_REDUCTION_FILTERING"></span>Min/Max-Reduzierungsfilterung

Min/Max-Reduzierungsfilterung wird nicht unterstützt. Siehe [Textursampling-Features für Streamingressourcen](streaming-resources-texture-sampling-features.md)

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md)

 

 




