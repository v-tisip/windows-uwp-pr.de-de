---
title: Dreiecksinterpolation
description: Während des Renderns interpoliert die Pipeline Scheitelpunktdaten über jedes Dreieck hinweg.
ms.assetid: 1A76DD78-CED7-42BE-BA81-B9050CD3AF9B
keywords:
- Dreiecksinterpolation
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e8017cd75ed3dfd4129d6c15d668648792cc8d0a
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8191713"
---
# <a name="triangle-interpolation"></a>Dreiecksinterpolation


Während des Renderns interpoliert die Pipeline Vertexdaten bei jedem Dreieck. Die Scheitelpunktdaten können sehr unterschiedliche Daten sein; dazu können u.a. gehören: diffuse Farbe, Glanzfarbe, diffuser Alphawert (Dreiecksopazität), Glanz-Alphawert und ein Nebelfaktor. Für die programmierbare Scheitelpunkt-Pipeline wird der Nebelfaktor aus dem Nebelregister übernommen. Für die Scheitelpunkt-Pipeline mit fester Funktion wird der Nebelfaktor dem Glanz-Alphawert entnommen.

Bei manchen Scheitelpunktdaten hängt die Interpolation wie folgt vom aktuellen Schattierungsmodus ab:

| Schattierungsmodus | Beschreibung                                                                                                                                                                 |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Flach         | Im Flach-Schattierungsmodus wird nur der Nebelfaktor interpoliert. Für alle anderen interpolierten Werte wird die Farbe des ersten Scheitelpunkts des Dreiecks über die gesamte Fläche angewendet. |
| Gouraud      | Zwischen allen drei Scheitelpunkten wird eine lineare Interpolation durchgeführt.                                                                                                               |

 

Diffus- und Glanzfarbe werden je nach Farbmodell unterschiedlich behandelt. Im RGB-Farbmodell verwendet das System die Farbkomponenten Rot, Grün und Blau in der Interpolation.

Die Alpha-Komponente einer Farbe wird als separater interpolierter Wert behandelt, da Gerätetreiber Transparenz auf zwei unterschiedliche Weisen implementieren können: durch Strukturmischung oder durch Punktierung.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 




