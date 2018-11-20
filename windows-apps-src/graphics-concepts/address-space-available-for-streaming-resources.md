---
title: Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen
description: In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt.
ms.assetid: 145EB4A3-3910-4126-BC7E-A4CF53E2A098
keywords:
- Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 0b6e3f8080d33f9aadf22d5d5b1ebdd9a4739e16
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7417086"
---
# <a name="address-space-available-for-streaming-resources"></a>Zuordnen des verfügbaren Speicherplatzes für Streamingressourcen


In diesem Abschnitt wird der für Streamingressourcen verfügbare virtuelle Adressraum aufgeführt.

Bei 64-Bit-Betriebssystemen ist mindestens 40Bit virtueller Adressraum (1Terabyte) verfügbar.

Bei 32-Bit-Betriebssystemen beträgt der Adressraum 32Bit (4GB). Bei 32-Bit-Betriebssystemen kann das Erstellen einzelner Streamingressourcen zu Fehlern führen, wenn die Zuordnung des Adressraums (128MB) mehr als 27Bit beträgt. Dazu gehören alle ausgeblendeten Abstände im Adressraum, die die Hardware für Mipmaps, Abstände für aneinanderliegende Kacheln und möglicherweise Abstände für Oberflächengrößen mit Potenzen von2 verwendet.

Auf Grafiksystemen mit einer separaten Seitentabelle für den Grafikprozessor (GPU) wird der Adressraum hauptsächlich für die von der Anwendung erstellten GPU-Ressourcen verwendet, auch wenn die vom Anzeigetreiber vorgenommene GPU-Zuordnungen genauso viel Platz verwenden.

Bei zukünftigen Systemen, bei denen die Seitentabelle gemeinsam von CPU und GPU genutzt wird, wird der verfügbare Adressraum gemeinsam von CPU und GPU-Zuordnungen in einem Prozess genutzt.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Parameter für das Erstellen von Streamingressourcen](streaming-resource-creation-parameters.md)

 

 




