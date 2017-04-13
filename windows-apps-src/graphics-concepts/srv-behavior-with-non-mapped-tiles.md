---
title: SRV-Verhalten bei nicht zugeordneten Kacheln
description: "Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab."
ms.assetid: 0E1D64BE-EB09-4F9D-9800-BD23A3B374EE
keywords: SRV-Verhalten bei nicht zugeordneten Kacheln
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.openlocfilehash: e6c4334446ef3bc302602d0b59b81164c9a28f3d
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="span-iddirect3dconceptssrvbehaviorwithnon-mappedtilesspansrv-behavior-with-non-mapped-tiles"></a><span id="direct3dconcepts.srv_behavior_with_non-mapped_tiles"></span>SRV-Verhalten bei nicht zugeordneten Kacheln


Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab. Eine Aufschlüsselung der Anforderungen finden Sie unter dem Leseverhalten für die [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md). In diesem Abschnitt wird das Idealverhalten, für das die [Ebene2](tier-2.md) benötigt wird, zusammengefasst.

Angenommen, ein Texturfilterungsvorgang liest eine Gruppe Texel in einer SRV. Texel, die auf nicht zugeordnete Kacheln fallen, steuern in dem gesamten Filterungsvorgang0 zu allen nicht fehlenden Komponenten des Formats (und den Standardwert für fehlende Komponenten) zusammen mit Beiträgen aus zugeordneten Texeln bei. Die Texel sind alle gewichtet und werden kombiniert, unabhängig davon, ob die Daten aus zugeordneten oder nicht zugeordneten Kacheln stammen.

Bestimmte Hardware der ersten Generation der [Ebene2](tier-2.md) erfüllt diese Spezifikationen nicht und gibt die0 mit den zuvor beschriebenen Standardwerten als Gesamtfilterungsergebnis zurück, wenn Texel (mit einer Gewichtung von ungleich NULL) auf nicht zugeordnete Kacheln fallen. Jede andere Hardware muss die Anforderung erfüllen, alle Texel (mit einer Gewichtung ungleich NULL) in den Filter einzubeziehen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Pipelinezugriff auf Streamingressourcen](pipeline-access-to-streaming-resources.md)

 

 




