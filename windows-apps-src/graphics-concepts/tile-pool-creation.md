---
title: Erstellung eines Kachelpools
description: Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße jedes kachelpools ist auf Direct3D11s Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMS entspricht beschränkt.
ms.assetid: BD51EDD3-4AD3-4733-B014-DD77B9D743BB
keywords:
- Erstellung eines Kachelpools
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: cbb8b61c8eeef1a842a7c6b61d09670f056bb409
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6856247"
---
# <a name="tile-pool-creation"></a>Erstellung eines Kachelpools


Anwendungen können einen oder mehrere Kachelpools pro Direct3D-Gerät erstellen. Die Gesamtgröße jedes kachelpools ist auf Direct3D11s Ressourcengröße beschränkt, die ungefähr 1/4 des Grafikprozessor (GPU) RAMS entspricht beschränkt.

Ein Kachelpool besteht aus 64KB großen Kacheln, aber das Betriebssystem (Anzeigetreiber) verwaltet im Hintergrund den gesamten Pool als ein oder mehrere Vergaben – die Aufteilung ist nicht für Anwendungen sichtbar. Streamingressourcen definieren den Inhalt durch das Zeigen auf Kacheln in einem Kachelpool. Das Aufheben der Zuordnung einer Kachel über eine Streamingressource erfolgt durch das Zeigen der Kachel auf **NULL**. Solche nicht zugeordneten Kacheln unterliegen Regeln, die über das Verhalten von Lese- und Schreibvorgängen bestimmen. Mehr Informationen finden Sie im [Vergleich von Kachelpoolressourcen und der Gefahrennachverfolgung](hazard-tracking-versus-tile-pool-resources.md).

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Zuordnungen erfolgen in einen Kachelpool](mappings-are-into-a-tile-pool.md)

 

 




