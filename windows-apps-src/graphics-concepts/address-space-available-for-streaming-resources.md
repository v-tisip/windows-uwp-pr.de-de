---
title: "Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen"
description: "In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt."
ms.assetid: 145EB4A3-3910-4126-BC7E-A4CF53E2A098
keywords:
- "Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen"
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: c120e79518abfed35cbb6b0da6fc659b13602a3f
ms.lasthandoff: 02/07/2017

---

# <a name="address-space-available-for-streaming-resources"></a>Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen


In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt.

Bei 64-Bit-Betriebssystemen ist mindestens 40 Bit virtueller Adressraum (1 Terabyte) verfügbar.

Bei 32-Bit-Betriebssystemen beträgt der Adressraum 32 Bit (4 GB). Bei 32-Bit-Betriebssystemen kann das Erstellen einzelner Streamingressourcen zu Fehlern führen, wenn die Zuordnung des Adressraums (128 MB) mehr als 27 Bit beträgt. Dazu gehören alle ausgeblendeten Abstände im Adressraum, die die Hardware für Mipmaps, Abstände für aneinanderliegende Kacheln und möglicherweise Abstände für Oberflächengrößen mit Potenzen von 2 verwendet.

Auf Grafiksystemen mit einer separaten Seitentabelle für den Grafikprozessor (GPU) wird der Adressraum hauptsächlich für die von der Anwendung erstellten GPU-Ressourcen verwendet, auch wenn die vom Anzeigetreiber vorgenommene GPU-Zuordnungen genauso viel Platz verwenden.

Bei zukünftigen Systemen, bei denen die Seitentabelle gemeinsam von CPU und GPU genutzt wird, wird der verfügbare Adressraum gemeinsam von CPU und GPU-Zuordnungen in einem Prozess genutzt.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md)

 

 





