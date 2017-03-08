---
title: SRV-Verhalten bei nicht zugeordneten Kacheln
description: "Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab."
ms.assetid: 0E1D64BE-EB09-4F9D-9800-BD23A3B374EE
keywords:
- SRV-Verhalten bei nicht zugeordneten Kacheln
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: a8faa6e8b9bdbb3917ce79b6a83080f8a9df79a8
ms.lasthandoff: 02/07/2017

---

# <a name="span-iddirect3dconceptssrvbehaviorwithnon-mappedtilesspansrv-behavior-with-non-mapped-tiles"></a><span id="direct3dconcepts.srv_behavior_with_non-mapped_tiles"></span>SRV-Verhalten bei nicht zugeordneten Kacheln


Das Verhalten der Lesevorgänge der Shaderressourcenansicht (SRV), die nicht zugeordnete Kacheln umfassen, hängt von der Ebene der Hardwareunterstützung ab. Eine Aufschlüsselung der Anforderungen finden Sie unter dem Leseverhalten für die [Ebenen der Features von Streamingressourcen](streaming-resources-features-tiers.md). In diesem Abschnitt wird das Idealverhalten, für das die [Ebene 2](tier-2.md) benötigt wird, zusammengefasst.

Angenommen, ein Texturfilterungsvorgang liest eine Gruppe Texel in einer SRV. Texel, die auf nicht zugeordnete Kacheln fallen, steuern in dem gesamten Filterungsvorgang 0 zu allen nicht fehlenden Komponenten des Formats (und den Standardwert für fehlende Komponenten) zusammen mit Beiträgen aus zugeordneten Texeln bei. Die Texel sind alle gewichtet und werden kombiniert, unabhängig davon, ob die Daten aus zugeordneten oder nicht zugeordneten Kacheln stammen.

Bestimmte Hardware der ersten Generation der [Ebene 2](tier-2.md) erfüllt diese Spezifikationen nicht und gibt die 0 mit den zuvor beschriebenen Standardwerten als Gesamtfilterungsergebnis zurück, wenn Texel (mit einer Gewichtung von ungleich NULL) auf nicht zugeordnete Kacheln fallen. Jede andere Hardware muss die Anforderung erfüllen, alle Texel (mit einer Gewichtung ungleich NULL) in den Filter einzubeziehen.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Pipelinezugriff auf Streamingressourcen](pipeline-access-to-streaming-resources.md)

 

 





