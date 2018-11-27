---
title: Kachelzugriffseinschränkungen bei doppelten Zuordnungen
description: Bei doppelten Zuordnungen gibt es Kachelzugriffseinschränkungen, wie z.B. beim Kopieren von Streamingressourcen mit Quellen- und Zielüberlappung oder beim Rendern von Kacheln innerhalb des Bereichs Rendern freigegeben.
ms.assetid: 6E40B1DC-BCF1-4B09-82A8-7B2D9B209A61
keywords:
- Kachelzugriffseinschränkungen bei doppelten Zuordnungen
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d5563a9909ba3d6cb3deaae43bcf9e55b4b2c880
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7699176"
---
# <a name="tile-access-limitations-with-duplicate-mappings"></a>Kachelzugriffseinschränkungen bei doppelten Zuordnungen


Bei doppelten Zuordnungen gibt es Kachelzugriffseinschränkungen, wie z.B. beim Kopieren von Streamingressourcen mit Quellen- und Zielüberlappung oder beim Rendern von Kacheln innerhalb des Bereichs Rendern freigegeben.

## <a name="span-idcopyingstreamingresourceswithoverlappingsourceanddestinationspanspan-idcopyingstreamingresourceswithoverlappingsourceanddestinationspanspan-idcopyingstreamingresourceswithoverlappingsourceanddestinationspancopying-streaming-resources-with-overlapping-source-and-destination"></a><span id="Copying_streaming_resources_with_overlapping_source_and_destination"></span><span id="copying_streaming_resources_with_overlapping_source_and_destination"></span><span id="COPYING_STREAMING_RESOURCES_WITH_OVERLAPPING_SOURCE_AND_DESTINATION"></span>Kopieren von Streamingressourcen mit überlappender Quelle und Ziel


Wenn Kacheln in den Bereichen Quelle und Ziel eines Vorgangs Copy\ * Zuordnungen im Kopierbereich dupliziert haben, die auch dann überlappen würden, wenn beide Ressourcen nicht Streamingressourcen sind und der Vorgang Copy\ * überlappende Kopien unterstützt, verhält sich der Vorgang Copy\ * einwandfrei (als wenn die Quelle zu einem temporären Speicherort kopiert wird, bevor Sie zum Ziel geleitet wird). Wenn die Überlappung nicht offensichtlich ist (bspw. sind die Quell- und Zielressourcen unterschiedlich, teilen jedoch Zuordnungen oder Zuordnungen werden über eine bestimmte Oberfläche dupliziert), sind Ergebnisse des Kopiervorgangs auf den Kacheln, die freigegeben werden, nicht definiert.

## <a name="span-idcopyingtostreamingresourcewithduplicatedtilesindestinationareaspanspan-idcopyingtostreamingresourcewithduplicatedtilesindestinationareaspanspan-idcopyingtostreamingresourcewithduplicatedtilesindestinationareaspancopying-to-streaming-resource-with-duplicated-tiles-in-destination-area"></a><span id="Copying_to_streaming_resource_with_duplicated_tiles_in_destination_area"></span><span id="copying_to_streaming_resource_with_duplicated_tiles_in_destination_area"></span><span id="COPYING_TO_STREAMING_RESOURCE_WITH_DUPLICATED_TILES_IN_DESTINATION_AREA"></span>Streamingressource mit duplizierten Kacheln im Zielbereich kopieren


Das Kopieren auf eine Streamingressource mit duplizierten Kacheln im Zielbereich erzeugt nicht definierte Ergebnisse in diesen Kacheln, es sei denn, die Daten selbst sind identisch. Verschiedene Kacheln können die Kacheln in einer anderen Reihenfolge schreiben.

## <a name="span-iduavaccessestoduplicatetilesmappingsspanspan-iduavaccessestoduplicatetilesmappingsspanspan-iduavaccessestoduplicatetilesmappingsspanuav-accesses-to-duplicate-tiles-mappings"></a><span id="UAV_accesses_to_duplicate_tiles_mappings"></span><span id="uav_accesses_to_duplicate_tiles_mappings"></span><span id="UAV_ACCESSES_TO_DUPLICATE_TILES_MAPPINGS"></span>UAV greift auf doppelte Kachelzuordnungen zu


Nehmen wir an, dass eine unsortierte Access-Ansicht (UAV) auf einer Streamingressource doppelte Kachelzuordnungen in ihrem Gebiet oder mit anderen Ressourcen, die an die Pipeline gebunden sind, hat. Die Sortierung der Zugriffe auf diese dupliziert Kacheln ist nicht definiert, wenn sie durch verschiedene Threads durchgeführt wird. Jegliche Sortierung des Speicherzugriffs auf UAVs ist allgemein nicht sortiert.

## <a name="span-idrenderingaftertilemappingchangesorcontentupdatesfromoutsidemappingsspanspan-idrenderingaftertilemappingchangesorcontentupdatesfromoutsidemappingsspanspan-idrenderingaftertilemappingchangesorcontentupdatesfromoutsidemappingsspanrendering-after-tile-mapping-changes-or-content-updates-from-outside-mappings"></a><span id="Rendering_after_tile_mapping_changes_or_content_updates_from_outside_mappings"></span><span id="rendering_after_tile_mapping_changes_or_content_updates_from_outside_mappings"></span><span id="RENDERING_AFTER_TILE_MAPPING_CHANGES_OR_CONTENT_UPDATES_FROM_OUTSIDE_MAPPINGS"></span>Rendern nach Änderungen an der Kachelzuordnung oder Inhaltsaktualisierungen aus externen Zuordnungen


Wenn die Kachelzuordnungen einer Streamingressource geändert wurden oder Inhalte in zugeordneten, nebeneinander angeordneten Poolkacheln über die Zuordnungen einer anderen Streamingressource geändert wurden und die Streamingressource über die Renderzielansicht oder die Tiefen-Schablonen-Ansicht gerendert wird, muss die Anwendung die Kacheln (zugeordnete oder nicht zugeordnete), die innerhalb des Bereichs geändert wurden, löschen (mit fester Funktion Clear-APIs) oder vollständig mit Copy\*/Update\* APIs kopieren.

Scheitern der Anwendung beim Deaktivierungs- oder Kopiervorgang führt in diesen Fällen dazu, dass die Hardware-Optimierungsstrukturen für die angegebene Renderzielansicht oder Tiefenschablonen-Ansicht veralten. Außerdem führt es zu Garbage-Renderergebnisse und zu Inkonsistenzen in verschiedener Hardware. Diese ausgeblendeten Optimierungsdatenstrukturen, die von der Hardware verwendet werden, befinden sich möglicherweise lokal auf einzelne Zuordnungen und sind nicht für Zuordnungen zum gleichen Arbeitsspeicher sichtbar.

Wenn Sie eine Ressourcenansicht (durch Festlegen aller Elemente in einer Ressourcenansicht auf einen Wert) deaktivieren, können Sie Renderzielansichten mithilfe von Rechtecken deaktivieren. Für Hardware, das Streamingressourcen unterstützt, muss das Deaktivieren einer Ressourcenansicht auch das Deaktivieren von Tiefenschablonenansichten ausschließlich für Oberflächen (ohne Schablone) mithilfe von Rechtecken unterstützen. Dieser Vorgang ermöglicht es der Anwendung, nur den erforderlichen Bereich einer Oberfläche zu deaktivieren.

Wenn eine Anwendung den bestehenden Speicherinhalt der Bereiche in einer Streamingressource beibehalten muss, in denen Zuordnungen geändert wurden, muss diese Anwendungen die klare Anforderung umgehen. Die Anwendung kann die Anforderung erfolgreich umgehen, indem der Inhalt zunächst in den Bereichen gespeichert wird, in denen Kachelzuordnungen (durch das Kopieren in eine temporäre Oberfläche) geändert wurden, der erforderliche Deaktivierungsbefehl gegeben wird und der Inhalt zurück kopiert wird. Während dies die Aufgabe des Beibehalten von Oberflächeninhalten für das inkrementelle Rendern ausführen würde, besteht der Nachteil darin, dass nachfolgende Renderingleistung auf der Oberfläche beeinträchtigt werden kann, da Renderoptimierungen möglicherweise verloren gehen.

Wenn eine Kachel gleichzeitig in mehreren Streamingressourcen zugeordnet ist und der Kachelinhalt auf irgendeine Weise (Rendern, Kopieren und so weiter) über eine der Streamingressourcen geändert wurden, und die gleiche Kachel über eine andere Streamingressource gerendert wird, muss zunächst wie zuvor beschrieben die Kachel gelöscht werden.

## <a name="span-idrenderingtotilessharedoutsiderenderareaspanspan-idrenderingtotilessharedoutsiderenderareaspanspan-idrenderingtotilessharedoutsiderenderareaspanrendering-to-tiles-shared-outside-render-area"></a><span id="Rendering_to_tiles_shared_outside_render_area"></span><span id="rendering_to_tiles_shared_outside_render_area"></span><span id="RENDERING_TO_TILES_SHARED_OUTSIDE_RENDER_AREA"></span>Rendern auf Kacheln außerhalb des freigegeben Renderbereichs


Nehmen Sie an, dass ein Bereich in einer Streamingressource gerendert wird und die Poolkacheln, die vom Renderbereich verwiesen werden, auch von außerhalb des Renderbereichs zugeordnet werden (auch über andere Streamingressourcen, zur gleichen Zeit oder nicht). Die Daten, die für diese Kacheln gerendert werden, werden möglicherweise nicht richtig über die anderen Zuordnungen angezeigt, obwohl das zugrunde liegende Speicherlayout kompatibel ist. Dies ergibt sich aus der Tatsache, dass die Optimierungsdatenstrukturen, die manche Hardware-Typen verwenden, auf einzelne lokale Zuordnungen für darstellbare Oberflächen sein können und möglicherweise für andere Zuordnungen an demselben Speicherort nicht angezeigt werden.

Sie können diese Einschränkung umgehen, indem Sie von der gerenderten Zuordnung auf alle anderen Zuordnungen des gleichen Speichers kopieren, auf dem zugegriffen werden kann (oder indem Sie den Arbeitsspeicher löschen oder andere Daten auf den Speicher kopieren, wenn der alte Inhalt nicht mehr benötigt wird). Während diese Umgehung redundant erscheint, ermöglicht es allen anderen Zuordnungen des gleichen Speichers den ordnungsgemäßen Zugriff auf seine Inhalte. Zumindest bleiben die Speichereinsparungen mit nur einem einzelnen physischen Speichersicherung erhalten.

Außerdem, wenn Sie zwischen verschiedenen Streamingressourcen wechseln, die Zuordnungen teilen (es sei denn, es sind nur lesbare), müssen Sie eine Einschränkung der Datenzugriffsreihenfolge (eine Barriere) zwischen Ressourcen mit mehreren Kacheln und zwischen den Switches angeben.

## <a name="span-idrenderingtotilessharedwithinrenderareaspanspan-idrenderingtotilessharedwithinrenderareaspanspan-idrenderingtotilessharedwithinrenderareaspanrendering-to-tiles-shared-within-render-area"></a><span id="Rendering_to_tiles_shared_within_render_area"></span><span id="rendering_to_tiles_shared_within_render_area"></span><span id="RENDERING_TO_TILES_SHARED_WITHIN_RENDER_AREA"></span>Rendern auf Kacheln innerhalb des freigegeben Renderbereichs


Wenn ein Bereich in einer Streamingressource gerendert zu und innerhalb des Renderbereichs gerendert wird und mehrere Kacheln am selben Speicherort des Kachelpools zugeordnet werden, sind die Renderingergebnisse auf diesen Kacheln nicht definiert.

## <a name="span-iddatacompatibilityacrossstreamingresourcessharingtilesspanspan-iddatacompatibilityacrossstreamingresourcessharingtilesspanspan-iddatacompatibilityacrossstreamingresourcessharingtilesspandata-compatibility-across-streaming-resources-sharing-tiles"></a><span id="Data_compatibility_across_streaming_resources_sharing_tiles"></span><span id="data_compatibility_across_streaming_resources_sharing_tiles"></span><span id="DATA_COMPATIBILITY_ACROSS_STREAMING_RESOURCES_SHARING_TILES"></span>Kompatibilität der Daten für das Streamen von Ressourcen, die Kacheln freigeben


Nehmen wir an, dass mehrere Streamingressourcen Zuordnungen auf die gleichen Speicherorte der Kachelpools haben und jede Ressource dazu verwendet wird, um auf dieselben Daten zuzugreifen. Dieses Szenario gilt nur, wenn die anderen Regeln zum Vermeiden von Problemen mit Hardwareoptimierungsstrukturen vermieden werden, entsprechende Hindernisse angegeben werden (Angeben einer Einschränkung der Datenzugriffsreihenfolge zwischen Ressourcen mit mehreren Kacheln) und die Streamingressourcen miteinander kompatibel sind.

Die zweite Option wird hier in Bezug auf die Bedeutung für die Streamingressourcen beschrieben, die Kacheln freigeben, um inkompatibel zu sein. Die Inkompatibilitätsbedingungen für den Zugriff auf dieselben Daten über doppelte Kachelzuordnungen ergeben sich aus der Verwendung der verschiedenen Oberflächenabmessungen oder des Formats, oder aus Differenzen der Bindungskennzeichen für Renderziele oder Tiefenschablonen auf den Ressourcen. Das Schreiben im Speicher mit einem Zuordnungstyp erzeugt undefinierte Ergebnisse, wenn Sie anschließend über eine Zuordnung von einer nicht kompatiblen Ressource lesen oder rendern.

Wenn die anderen freigegebenen Ressourcenzuordnungen zuerst mit neuen Daten initialisiert werden (Wiederverwendung des Speichers für einen anderen Zweck), ist der nachfolgende Lese- oder Rendervorgang geeignet, da Daten nicht über inkompatible Interpretationen übertragen werden. Beim Wechseln zwischen den Zugriffen auf inkompatible Zuordnungen wie hier müssen Sie jedoch Barrieren angeben (Angeben einer Einschränkung der Datenzugriffsreihenfolge zwischen Ressourcen mit mehreren Kacheln).

Wenn das Bindungskennzeichen für das Renderziel oder die Tiefenschablone nicht auf eine der Ressourcen festgelegt ist, die miteinander Zuordnungen teilen, gibt es sehr viel weniger Einschränkungen. Solange die Format- und Surface-Typen (z.B. Texture2D) identisch sind, können Kacheln freigegeben werden. Kompatible Formate ergeben sich unter anderem in Fällen wie z.B. BC\ * Oberflächen und entsprechend großes, unkomprimiertes 32-Bit- oder 16-Bit-Format pro Komponente, wie z.B. BC6H und R32G32B32A32. Viele 32-Bit-pro-Element-Formate können einen Alias mit R32\_\ * sowie (R10G10B10A2\_\ *, R8G8B8A8\_\ *, B8G8R8A8\_\ *, B8G8R8X8\_\ *, R16G16\_\ *); haben. Dieser Vorgang wurde schon immer für Nicht-Streamingressourcen zugelassen.

Das Freigeben zwischen verpackten und nicht verpackten Kacheln ist geeignet, wenn die Formate kompatibel und die Kacheln mit Volltonfarbe gefüllt sind.

Wenn die Zuordnungen der Ressourcenfreigabekachel keine Ähnlichkeiten aufweisen, abgesehen davon, dass keine Bindungskennzeichen für Renderziel oder Tiefenschablone festgelegt wurden, kann nur mit 0 gefüllter Speicher problemlos geteilt werden. Die Zuordnung wird als das angezeigt, was aus 0 für die Definition des gegebenen Ressourcenformats (in der Regel nur 0) dekodiert wird.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Pipelinezugriff auf Streamingressourcen](pipeline-access-to-streaming-resources.md)

 

 




