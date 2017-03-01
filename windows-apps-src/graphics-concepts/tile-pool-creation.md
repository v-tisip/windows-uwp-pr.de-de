---
title: Erstellung eines Kachelpools
description: "Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße der einzelnen Kachelpools ist auf die Direct3D 11-Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMs entspricht."
ms.assetid: BD51EDD3-4AD3-4733-B014-DD77B9D743BB
keywords:
- Erstellung eines Kachelpools
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 5289bcb57572ede45c6853b0077f5baa82af7ca2
ms.lasthandoff: 02/07/2017

---

# <a name="tile-pool-creation"></a>Erstellung eines Kachelpools


Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße der einzelnen Kachelpools ist auf die Direct3D 11-Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMs entspricht.

Ein Kachelpool besteht aus 64 KB großen Kacheln, aber das Betriebssystem (Anzeigetreiber) verwaltet im Hintergrund den gesamten Pool als ein oder mehrere Vergaben – die Aufteilung ist nicht für Anwendungen sichtbar. Streamingressourcen definieren den Inhalt durch das Zeigen auf Kacheln in einem Kachelpool. Das Aufheben der Zuordnung einer Kachel über eine Streamingressource erfolgt durch das Zeigen der Kachel auf **NULL**. Solche nicht zugeordneten Kacheln unterliegen Regeln, die über das Verhalten von Lese- und Schreibvorgängen bestimmen. Mehr Informationen finden Sie im [Vergleich von Kachelpoolressourcen und der Gefahrennachverfolgung](hazard-tracking-versus-tile-pool-resources.md).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Zuordnungen erfolgen in einen Kachelpool](mappings-are-into-a-tile-pool.md)

 

 





