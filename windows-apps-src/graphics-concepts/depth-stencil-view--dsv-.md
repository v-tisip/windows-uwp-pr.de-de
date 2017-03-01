---
title: Tiefenschablonenansicht (Depth Stencil View, DSV)
description: Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit.
ms.assetid: 2E8BFF7F-76F8-408E-B8E6-A71B9DF46281
keywords:
- Tiefenschablonenansicht (Depth Stencil View, DSV)
author: PeterTurcan
ms.author: pettur
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 222fb2705d89cce547b4d7685d839fcee3a402b3
ms.lasthandoff: 02/07/2017

---

# <a name="depth-stencil-view-dsv"></a>Tiefenschablonenansicht (Depth Stencil View, DSV)


Eine Tiefenschablonenansicht stellt das Format und den Puffer zur Speicherung von Tiefen- und Schabloneninformationen bereit. Der Tiefenpuffer dient dazu, das Zeichnen von Pixeln zu vermeiden, die von einem näher liegenden Objekte verdeckt werden und so für den Betrachter nicht sichtbar wären. Der Schablonenpuffer kann zur Aussortierung (Culling) aller Zeichnungsaktivitäten außerhalb einer definierten Form genutzt werden.

Abgesehen von der Definition eines bestimmten Renderingbereiches gibt es noch eine Reihe erweiterter Einsatzmöglichkeiten für Schablonenpuffer. Schablonenpufferwerte können so verändert werden, dass Effekte wie Ausblenden, Silhouetten, Decaling, Auflösen, Umrisse, Schattenvolumen, usw. möglich werden.

## <a name="span-idrelated-topicsspanrelated-topics"></a><span id="related-topics"></span>Verwandte Themen


[Ansichten](views.md)

 

 





