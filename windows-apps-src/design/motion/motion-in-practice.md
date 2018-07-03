---
author: jwmsft
Description: Learn how Fluent motion fundamentals come together in your app.
title: Bewegung in der Praxis – Animationen in UWP-Apps
label: Motion in practice
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 87a17d3f73887c9b1b5029e2096c5b41c9444c4e
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1843813"
---
# <a name="bringing-it-together"></a>Alles zusammenführen

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe möglicherweise geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Timing, Geschwindigkeitsverlauf, Direktionalität und Schwerkraft bilden zusammen die Grundlage für fließende Bewegungen. Jede Komponente muss im Zusammenhang mit den anderen betrachtet und dem Kontext Ihrer App entsprechend angewendet werden.

Im Folgenden finden Sie 3 Möglichkeiten, die Grundlagen für fließende Bewegung in Ihrer App anzuwenden.

:::row::: :::column::: **Implizite Animation**

        Automatic tween and timing between values in a parameter change to achieve very simple Fluent motion using the standardized values.
    :::column-end:::
    :::column:::
        **Built-in animation**

        System components, such as common controls and shared motion, are "Fluent by default". Fundamentals have been applied in a manner consistent with their implied usage.
    :::column-end:::
    :::column:::
        **Custom animation following guidance recommendations**

        There may be times when the system does not yet provide an exact motion solution for your scenario. In those cases, use the baseline fundamental recommendations as a starting point for your experiences.
    :::column-end:::
:::row-end:::

### **<a name="transition-example"></a>Beispielübergang**

![funktionelle Animation](images/pageRefresh.gif)

:::row::: :::column::: <b>Richtung vorwärts hinaus:</b><br>
        Ausblenden: 150 ms; Geschwindigkeitsverlauf: Standardmäßige Beschleunigung

        <b>Direction Forward In:</b><br>
        Slide up 150px: 300ms; Easing: Default Decelerate
    :::column-end:::
    :::column:::
         <b>Direction Backward Out:</b><br>
        Slide down 150px: 150ms; Easing: Default Accelerate
      
        <b>Direction Backward In:</b><br>
        Fade in: 300ms; Easing: Default Decelerate
    :::column-end:::
:::row-end:::

 ### **<a name="object-example"></a>Objektbeispiel**

 ![300 ms Bewegung](images/control.gif)
 
:::row::: :::column::: <b>Expansionsrichtung:</b><br>
        Vergrößern: 300 ms; Geschwindigkeitsverlauf: Standard :::column-end::: :::column::: <b>Kontraktionsrichtung:</b><br>
        Vergrößern: 150 ms; Geschwindigkeitsverlauf: Standardmäßige Beschleunigung :::column-end::: :::row-end:::

## <a name="related-articles"></a>Verwandte Artikel

- [Übersicht über Bewegungen](index.md)
- [Timing und Geschwindigkeitsverlauf](timing-and-easing.md)
- [Direktionalität und Schwerkraft](directionality-and-gravity.md)