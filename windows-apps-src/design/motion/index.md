---
author: mijacobs
Description: Purposeful, well-designed motion brings your app to life and makes the experience feel crafted and polished. Help users understand context changes, and tie experiences together with visual transitions.
title: Bewegung und Animation in UWP-Apps
ms.assetid: 21AA1335-765E-433A-85D8-560B340AE966
label: Motion
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: def37c31ef0a64a9b1017d40d281457513fba0db
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6035609"
---
# <a name="motion-for-uwp-apps"></a>Bewegung für UWP-Apps

![Favoritenbild](images/header-motion2.svg)

In einer App sind fließende Bewegungen wichtig. Sie geben intelligentes Feedback basierend auf dem Verhalten des Benutzers, halten ein lebendiges Gefühl für die Benutzeroberfläche aufrecht und leiten die Navigation durch die App. Fließende Bewegung bewirkt eine emotionale Verbindung zwischen dem Benutzer und seiner digitalen Erfahrung. Wir gehen von grundlegenden natürlichen Bewegungen aus, die der Benutzer bereits aus der physischen Welt kennt, und wir erweitern unser System von dort aus.

## <a name="fluent-motion-principles"></a>Prinzipien fließender Bewegungen

### <a name="physical"></a>Physisch

Bewegte Objekte verhalten sich wie Objekte in der realen Welt. Durch fließende, reaktionsfähige Bewegungen wirken Benutzeroberflächen natürlich, und sie sorgen dafür, dass emotionale Verbindungen mit der Oberfläche entstehen.

![UI-Beispiel für fließende Bewegung](images/Physical.gif)
> Wenn Sie per Toucheingabe mit der UI interagieren, entspricht die Bewegung auf der Benutzeroberfläche direkt der Geschwindigkeit der Interaktion. Und weil die Toucheingabe eine direkte Manipulation ist, wirkt sich das Objekt, mit dem Sie interagieren, auf die umgebenden Objekte aus.

### <a name="functional"></a>Funktionell

Bewegung dient einem Zweck und muss überzeugend sein. Sie führt den Benutzer durch die Komplexität und hilft beim Aufbau der Hierarchie. Bewegung vermittelt den Eindruck verbesserter Leistung und optimiert das Benutzererlebnis, da keine Latenz wahrgenommen wird.

![UI-Beispiel für funktionelle Bewegung](images/functional.gif)
> Seitenübergänge sind bewusst gestaltet. Sie geben Hinweise darauf, wie Seiten miteinander in Beziehung stehen sind. Sie verschieben Seiten in einer Weise, die selbst dann als schnell empfunden wird, wenn die Leistung nicht optimal ist.

### <a name="continuous"></a>Kontinuierlich

Eine fließende Bewegung von Punkt zu Punkt zieht auf natürliche Weise den Blick auf sich und führt den Benutzer. Sie fügt die Aufgabe eines Benutzers elegant zusammen, so dass sie sich konsumierbarer und freundlicher anfühlt.

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)
> Objekte können von Szene zu Szene wandern oder in einer Szene morphen, um Kontinuität zu schaffen und dem Benutzer dabei zu helfen, den Kontext zu erhalten.

### <a name="contextual"></a>Kontextbezogen

Intelligente Bewegung liefert dem Benutzer eine Rückmeldung in einer Weise, die sich danach richtet, wie der Benutzer die Benutzeroberfläche manipuliert hat. Interaktion ist um den Benutzer herum zentriert. Bewegung muss dem Formfaktor angemessen und dem Szenario entsprechend gestaltet sein. Sie sollte für jeden Benutzer vertraut sein.

![UI-Beispiel für kontextuelle Bewegung](images/Contextual.gif)
> Eine Animation sollte mit der Benutzerinteraktion verknüpft sein. Ein Kontextmenü wird an dem Punkt bereitgestellt, an dem es der Benutzer aktiviert. 

## <a name="motion-articles"></a>Artikel zu Bewegungen

:::row:::
    :::column:::
        ### [Timing and easing](timing-and-easing.md)
        Timing and easing are important elements that make motion feel natural for objects entering, exiting, or moving within the UI.
    :::column-end:::
    :::column:::
        ### [Directionality and gravity](directionality-and-gravity.md)
        Directional signals help provide a solid mental model of the journey a user takes across experiences. Directional movement is subject to forces like gravity, which reinforces the natural feel of the movement.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        ### [Page transitions](page-transitions.md)
        Page transitions navigate users between pages in an app, providing feedback about the relationship between pages. They help users understand where they are in the navigation hierarchy.
    :::column-end:::
    :::column:::
        ### [Connected animation](connected-animation.md)
        Connected animations let you create a dynamic and compelling navigation experience by animating the transition of an element between two different views.
    :::column-end:::
:::row-end:::
