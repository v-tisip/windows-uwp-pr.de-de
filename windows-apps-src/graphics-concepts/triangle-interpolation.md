---
title: Dreiecksinterpolation
description: "Während des Renderns interpoliert die Pipeline Scheitelpunktdaten über jedes Dreieck hinweg."
ms.assetid: 1A76DD78-CED7-42BE-BA81-B9050CD3AF9B
keywords:
- Dreiecksinterpolation
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 1adaa39d89be0245771a08273573e2ca06fa4b85
ms.lasthandoff: 02/07/2017

---

# <a name="triangle-interpolation"></a>Dreiecksinterpolation


Während des Renderns interpoliert die Pipeline Scheitelpunktdaten über jedes Dreieck hinweg. Die Scheitelpunktdaten können sehr unterschiedliche Daten sein; dazu können u. a. gehören: diffuse Farbe, Glanzfarbe, diffuser Alphawert (Dreiecksopazität), Glanz-Alphawert und ein Nebelfaktor. Für die programmierbare Scheitelpunkt-Pipeline wird der Nebelfaktor aus dem Nebelregister übernommen. Für die Scheitelpunkt-Pipeline mit fester Funktion wird der Nebelfaktor dem Glanz-Alphawert entnommen.

Bei manchen Scheitelpunktdaten hängt die Interpolation wie folgt vom aktuellen Schattierungsmodus ab:

| Schattierungsmodus | Beschreibung                                                                                                                                                                 |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Flach         | Im Flach-Schattierungsmodus wird nur der Nebelfaktor interpoliert. Für alle anderen interpolierten Werte wird die Farbe des ersten Scheitelpunkts des Dreiecks über die gesamte Fläche angewendet. |
| Gouraud      | Zwischen allen drei Scheitelpunkten wird eine lineare Interpolation durchgeführt.                                                                                                               |

 

Diffus- und Glanzfarbe werden je nach Farbmodell unterschiedlich behandelt. Im RGB-Farbmodell verwendet das System die Farbkomponenten Rot, Grün und Blau in der Interpolation.

Die Alpha-Komponente einer Farbe wird als separater interpolierter Wert behandelt, da Gerätetreiber Transparenz auf zwei unterschiedliche Weisen implementieren können: durch Strukturmischung oder durch Punktierung.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Koordinatensysteme und Geometrie](coordinate-systems-and-geometry.md)

 

 





