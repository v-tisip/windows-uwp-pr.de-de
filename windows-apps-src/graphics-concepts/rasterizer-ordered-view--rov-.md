---
title: Rasterizergesteuerte Ansicht (ROV)
description: "Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten."
ms.assetid: BCB1EE0D-4C1D-4E17-BDB7-173F448E0A7B
keywords: Rasterizergesteuerte Ansicht (ROV)
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: bb75d903bee3990b13e261393f3801b4089ec1b0
ms.sourcegitcommit: c80b9e6589a1ee29c5032a0b942e6a024c224ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="rasterizer-ordered-view-rov"></a>Rasterizergesteuerte Ansicht (ROV)


Mit rasterizergesteuerten Ansichten können einige der Einschränkungen von Tiefenpuffern behandelt werden, insbesondere wenn mehrere Texturen mit Transparenz alle für dieselben Pixel gelten.

Mit rasterizergesteuerten Ansichten können OIT-Algorithmen (Order Independent Transparency) auf das Rendern von Pixeln angewendet werden. Mit einem Tiefenpuffer kann ein Pixel lediglich gezeichnet oder verdeckt werden; ein Konzept für ein teilweises Verdecken durch Transparenz ist nicht vorhanden. OIT-Algorithmen wenden transparente Texturen in der richtigen Reihenfolge an, damit das Endergebnis vorhersehbar richtig gezeichnet wird, wenn z.B. ein transparentes, gläsernes Objekt hinter einem Glasfenster angezeigt werden soll, das sich hinter etwas Vegetation befindet, die transparente Texturen verwendet. Ohne ROVs und OIT-Algorithmen war die Reihenfolge, mit der diese transparenten Objekte gezeichnet wurden, unvorhersehbar, und die gerenderte Szene konnte verwirrend und inkorrekt sein.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 




