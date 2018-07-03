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
# <a name="bringing-it-together"></a><span data-ttu-id="f56ec-103">Alles zusammenführen</span><span class="sxs-lookup"><span data-stu-id="f56ec-103">Bringing it together</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f56ec-104">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe möglicherweise geändert werden.</span><span class="sxs-lookup"><span data-stu-id="f56ec-104">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="f56ec-105">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="f56ec-105">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="f56ec-106">Timing, Geschwindigkeitsverlauf, Direktionalität und Schwerkraft bilden zusammen die Grundlage für fließende Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="f56ec-106">Timing, easing, directionality, and gravity work together to form the foundation of Fluent motion.</span></span> <span data-ttu-id="f56ec-107">Jede Komponente muss im Zusammenhang mit den anderen betrachtet und dem Kontext Ihrer App entsprechend angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="f56ec-107">Each has to be considered in the context of the others, and applied appropriately in the context of your app.</span></span>

<span data-ttu-id="f56ec-108">Im Folgenden finden Sie 3 Möglichkeiten, die Grundlagen für fließende Bewegung in Ihrer App anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f56ec-108">Here are 3 ways to apply Fluent motion fundamentals in your app.</span></span>

<span data-ttu-id="f56ec-109">:::row::: :::column::: **Implizite Animation**</span><span class="sxs-lookup"><span data-stu-id="f56ec-109">:::row::: :::column::: **Implicit animation**</span></span>

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
<span data-ttu-id="f56ec-110">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="f56ec-110">:::row-end:::</span></span>

### **<a name="transition-example"></a><span data-ttu-id="f56ec-111">Beispielübergang</span><span class="sxs-lookup"><span data-stu-id="f56ec-111">Transition example</span></span>**

![funktionelle Animation](images/pageRefresh.gif)

<span data-ttu-id="f56ec-113">:::row::: :::column::: <b>Richtung vorwärts hinaus:</b></span><span class="sxs-lookup"><span data-stu-id="f56ec-113">:::row::: :::column::: <b>Direction Forward Out:</b></span></span><br>
        <span data-ttu-id="f56ec-114">Ausblenden: 150 ms; Geschwindigkeitsverlauf: Standardmäßige Beschleunigung</span><span class="sxs-lookup"><span data-stu-id="f56ec-114">Fade out: 150m; Easing: Default Accelerate</span></span>

        <b>Direction Forward In:</b><br>
        Slide up 150px: 300ms; Easing: Default Decelerate
    :::column-end:::
    :::column:::
         <b>Direction Backward Out:</b><br>
        Slide down 150px: 150ms; Easing: Default Accelerate
      
        <b>Direction Backward In:</b><br>
        Fade in: 300ms; Easing: Default Decelerate
    :::column-end:::
<span data-ttu-id="f56ec-115">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="f56ec-115">:::row-end:::</span></span>

 ### **<a name="object-example"></a><span data-ttu-id="f56ec-116">Objektbeispiel</span><span class="sxs-lookup"><span data-stu-id="f56ec-116">Object example</span></span>**

 ![300 ms Bewegung](images/control.gif)
 
<span data-ttu-id="f56ec-118">:::row::: :::column::: <b>Expansionsrichtung:</b></span><span class="sxs-lookup"><span data-stu-id="f56ec-118">:::row::: :::column::: <b>Direction Expand:</b></span></span><br>
        <span data-ttu-id="f56ec-119">Vergrößern: 300 ms; Geschwindigkeitsverlauf: Standard :::column-end::: :::column::: <b>Kontraktionsrichtung:</b></span><span class="sxs-lookup"><span data-stu-id="f56ec-119">Grow: 300ms; Easing: Standard :::column-end::: :::column::: <b>Direction Contract:</b></span></span><br>
        <span data-ttu-id="f56ec-120">Vergrößern: 150 ms; Geschwindigkeitsverlauf: Standardmäßige Beschleunigung :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="f56ec-120">Grow: 150ms; Easing: Default Accelerate :::column-end::: :::row-end:::</span></span>

## <a name="related-articles"></a><span data-ttu-id="f56ec-121">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="f56ec-121">Related articles</span></span>

- [<span data-ttu-id="f56ec-122">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="f56ec-122">Motion overview</span></span>](index.md)
- [<span data-ttu-id="f56ec-123">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="f56ec-123">Timing and easing</span></span>](timing-and-easing.md)
- [<span data-ttu-id="f56ec-124">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="f56ec-124">Directionality and gravity</span></span>](directionality-and-gravity.md)