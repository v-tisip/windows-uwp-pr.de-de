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
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6257057"
---
# <a name="motion-for-uwp-apps"></a><span data-ttu-id="bab30-103">Bewegung für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="bab30-103">Motion for UWP apps</span></span>

![Favoritenbild](images/header-motion2.svg)

<span data-ttu-id="bab30-105">In einer App sind fließende Bewegungen wichtig.</span><span class="sxs-lookup"><span data-stu-id="bab30-105">Fluent motion serves a purpose in your app.</span></span> <span data-ttu-id="bab30-106">Sie geben intelligentes Feedback basierend auf dem Verhalten des Benutzers, halten ein lebendiges Gefühl für die Benutzeroberfläche aufrecht und leiten die Navigation durch die App.</span><span class="sxs-lookup"><span data-stu-id="bab30-106">It gives intelligent feedback based on the user's behavior, keeps the UI feeling alive, and guides the user's navigation through your app.</span></span> <span data-ttu-id="bab30-107">Fließende Bewegung bewirkt eine emotionale Verbindung zwischen dem Benutzer und seiner digitalen Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="bab30-107">Fluent motion elicits an emotional connection between a user and their digital experience.</span></span> <span data-ttu-id="bab30-108">Wir gehen von grundlegenden natürlichen Bewegungen aus, die der Benutzer bereits aus der physischen Welt kennt, und wir erweitern unser System von dort aus.</span><span class="sxs-lookup"><span data-stu-id="bab30-108">We build on a foundation of natural movement the user already understands from the physical world, and we extend our system from there.</span></span>

## <a name="fluent-motion-principles"></a><span data-ttu-id="bab30-109">Prinzipien fließender Bewegungen</span><span class="sxs-lookup"><span data-stu-id="bab30-109">Fluent motion principles</span></span>

### <a name="physical"></a><span data-ttu-id="bab30-110">Physisch</span><span class="sxs-lookup"><span data-stu-id="bab30-110">Physical</span></span>

<span data-ttu-id="bab30-111">Bewegte Objekte verhalten sich wie Objekte in der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="bab30-111">Objects in motion exhibit behaviors of objects in the real world.</span></span> <span data-ttu-id="bab30-112">Durch fließende, reaktionsfähige Bewegungen wirken Benutzeroberflächen natürlich, und sie sorgen dafür, dass emotionale Verbindungen mit der Oberfläche entstehen.</span><span class="sxs-lookup"><span data-stu-id="bab30-112">Fluid, responsive movement makes the experience feel natural, creating emotional connections and adding personality.</span></span>

![UI-Beispiel für fließende Bewegung](images/Physical.gif)
> <span data-ttu-id="bab30-114">Wenn Sie per Toucheingabe mit der UI interagieren, entspricht die Bewegung auf der Benutzeroberfläche direkt der Geschwindigkeit der Interaktion.</span><span class="sxs-lookup"><span data-stu-id="bab30-114">When you interact with UI via touch, the movement of the UI is directly related to the velocity of the interaction.</span></span> <span data-ttu-id="bab30-115">Und weil die Toucheingabe eine direkte Manipulation ist, wirkt sich das Objekt, mit dem Sie interagieren, auf die umgebenden Objekte aus.</span><span class="sxs-lookup"><span data-stu-id="bab30-115">And because touch is direct manipulation, the object you interect with affects the objects around it.</span></span>

### <a name="functional"></a><span data-ttu-id="bab30-116">Funktionell</span><span class="sxs-lookup"><span data-stu-id="bab30-116">Functional</span></span>

<span data-ttu-id="bab30-117">Bewegung dient einem Zweck und muss überzeugend sein.</span><span class="sxs-lookup"><span data-stu-id="bab30-117">Motion serves a purpose and has conviction.</span></span> <span data-ttu-id="bab30-118">Sie führt den Benutzer durch die Komplexität und hilft beim Aufbau der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="bab30-118">It guides the user through complexity and helps establish hierarchy.</span></span> <span data-ttu-id="bab30-119">Bewegung vermittelt den Eindruck verbesserter Leistung und optimiert das Benutzererlebnis, da keine Latenz wahrgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="bab30-119">Movement gives the impression of enhanced performance and optimizes the user experience by hiding perceived latency.</span></span>

![UI-Beispiel für funktionelle Bewegung](images/functional.gif)
> <span data-ttu-id="bab30-121">Seitenübergänge sind bewusst gestaltet.</span><span class="sxs-lookup"><span data-stu-id="bab30-121">Page transitions are purpose-built.</span></span> <span data-ttu-id="bab30-122">Sie geben Hinweise darauf, wie Seiten miteinander in Beziehung stehen sind.</span><span class="sxs-lookup"><span data-stu-id="bab30-122">They give hints about how pages are related to each other.</span></span> <span data-ttu-id="bab30-123">Sie verschieben Seiten in einer Weise, die selbst dann als schnell empfunden wird, wenn die Leistung nicht optimal ist.</span><span class="sxs-lookup"><span data-stu-id="bab30-123">They move in a manner that's perceived as fast even when performance is not optimal.</span></span>

### <a name="continuous"></a><span data-ttu-id="bab30-124">Kontinuierlich</span><span class="sxs-lookup"><span data-stu-id="bab30-124">Continuous</span></span>

<span data-ttu-id="bab30-125">Eine fließende Bewegung von Punkt zu Punkt zieht auf natürliche Weise den Blick auf sich und führt den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="bab30-125">Fluid movement from point to point naturally draws the eye and guides the user.</span></span> <span data-ttu-id="bab30-126">Sie fügt die Aufgabe eines Benutzers elegant zusammen, so dass sie sich konsumierbarer und freundlicher anfühlt.</span><span class="sxs-lookup"><span data-stu-id="bab30-126">It elegantly stitches together a user’s task, making it feel more consumable and friendly.</span></span>

![UI-Beispiel für kontinuierliche Bewegung](images/continuous3.gif)
> <span data-ttu-id="bab30-128">Objekte können von Szene zu Szene wandern oder in einer Szene morphen, um Kontinuität zu schaffen und dem Benutzer dabei zu helfen, den Kontext zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bab30-128">Objects can travel from scene to scene or morph within a scene to provide continuity and help the user maintain context.</span></span>

### <a name="contextual"></a><span data-ttu-id="bab30-129">Kontextbezogen</span><span class="sxs-lookup"><span data-stu-id="bab30-129">Contextual</span></span>

<span data-ttu-id="bab30-130">Intelligente Bewegung liefert dem Benutzer eine Rückmeldung in einer Weise, die sich danach richtet, wie der Benutzer die Benutzeroberfläche manipuliert hat.</span><span class="sxs-lookup"><span data-stu-id="bab30-130">Intelligent motion provides feedback to the user in a manner that's aligned with how they manipulated the UI.</span></span> <span data-ttu-id="bab30-131">Interaktion ist um den Benutzer herum zentriert.</span><span class="sxs-lookup"><span data-stu-id="bab30-131">Interaction is centered around the user.</span></span> <span data-ttu-id="bab30-132">Bewegung muss dem Formfaktor angemessen und dem Szenario entsprechend gestaltet sein.</span><span class="sxs-lookup"><span data-stu-id="bab30-132">The movement feels appropriate to the form-factor and designed around the scenario.</span></span> <span data-ttu-id="bab30-133">Sie sollte für jeden Benutzer vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="bab30-133">It should be comfortable for each user.</span></span>

![UI-Beispiel für kontextuelle Bewegung](images/Contextual.gif)
> <span data-ttu-id="bab30-135">Eine Animation sollte mit der Benutzerinteraktion verknüpft sein.</span><span class="sxs-lookup"><span data-stu-id="bab30-135">Animation should tie back to the user interaction.</span></span> <span data-ttu-id="bab30-136">Ein Kontextmenü wird an dem Punkt bereitgestellt, an dem es der Benutzer aktiviert.</span><span class="sxs-lookup"><span data-stu-id="bab30-136">A context menu is deployed from a point where the user activated it.</span></span> 

## <a name="motion-articles"></a><span data-ttu-id="bab30-137">Artikel zu Bewegungen</span><span class="sxs-lookup"><span data-stu-id="bab30-137">Motion articles</span></span>

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
