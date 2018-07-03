---
author: jwmsft
Description: Learn how Fluent motion uses timing and easing functions.
title: Timing und Geschwindigkeitsverlauf – Animation in UWP-Apps
label: Timing and easing
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 412ba7e36c2bb36562ceee13bb1e204ff402a882
ms.sourcegitcommit: 517c83baffd344d4c705bc644d7c6d2b1a4c7e1a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "1843817"
---
# <a name="timing-and-easing"></a><span data-ttu-id="12d34-103">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="12d34-103">Timing and easing</span></span>

<span data-ttu-id="12d34-104">Bewegung basiert zwar auf der realen Welt, aber auch in einem digitalen Medium werden Geschwindigkeit und Leistung erwartet.</span><span class="sxs-lookup"><span data-stu-id="12d34-104">While motion is based in the real world, we are also a digital medium, which comes with an expectation of speed and performance.</span></span> 

## <a name="how-fluent-motion-uses-time"></a><span data-ttu-id="12d34-105">Fluent-Bewegungen und Timing</span><span class="sxs-lookup"><span data-stu-id="12d34-105">How Fluent motion uses time</span></span>

<span data-ttu-id="12d34-106">Timing ist ein wichtiges Element, um die Bewegung von Objekten natürlich erscheinen zu lassen, die in die Benutzeroberfläche eintreten, sie verlassen oder sich darin bewegen.</span><span class="sxs-lookup"><span data-stu-id="12d34-106">Timing is an important element to making motion feel natural for objects entering, exiting, or moving within the UI.</span></span>

1. <span data-ttu-id="12d34-107">Objekte oder Szenen, die in das Sichtfeld eintreten, sind schnell und auffällig.</span><span class="sxs-lookup"><span data-stu-id="12d34-107">Objects or scenes entering the view are quick, but celebrated.</span></span> <span data-ttu-id="12d34-108">Die Animationen für diese Elemente dauern in der Regel längere als die für austretende Elemente, um den hierarchischen Aufbau einer Szene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="12d34-108">These animations are typically longer in duration than exits to allow for hierarchical build-up of a scene.</span></span>
1. <span data-ttu-id="12d34-109">Objekte oder Szenen, die das Sichtfeld verlassen, sind sehr schnell.</span><span class="sxs-lookup"><span data-stu-id="12d34-109">Objects or scenes exiting the view are very quick.</span></span> <span data-ttu-id="12d34-110">Der Benutzer sollte nachvollziehen können, wo die UI verbleibt.</span><span class="sxs-lookup"><span data-stu-id="12d34-110">The user should be able to understand where the UI went.</span></span> <span data-ttu-id="12d34-111">Nachdem die UI jedoch geschlossen wurde, sollte sie aus dem Weg gehen.</span><span class="sxs-lookup"><span data-stu-id="12d34-111">However, once the UI is dismissed, it should get out of the way.</span></span>
1. <span data-ttu-id="12d34-112">Objekte, die sich durch eine Szene bewegen, sollten dafür eine Dauer benötigen, die der zurückzulegenden Entfernung entspricht.</span><span class="sxs-lookup"><span data-stu-id="12d34-112">Objects translating across a scene should have a duration appropriate to the amount of distance they travel.</span></span>

## <a name="timing-in-fluent-motion"></a><span data-ttu-id="12d34-113">Timing für Fluent-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="12d34-113">Timing in Fluent motion</span></span>

<span data-ttu-id="12d34-114">Für das Timing von Fluent-Bewegungen gelten 500 ms (eine halbe Sekunde) als Grundeinheit, da dies die maximale Zeit ist, die ein Benutzer als unmittelbar empfindet.</span><span class="sxs-lookup"><span data-stu-id="12d34-114">The timing of motion in Fluent uses 500ms (or one-half second) as a baseline because this is the maximum amount of time that a user perceives as instant.</span></span>

![Favoritenbild](images/time.gif)

### <a name="150ms-exit"></a><span data-ttu-id="12d34-116">**150 ms** (Verlassen)</span><span class="sxs-lookup"><span data-stu-id="12d34-116">**150ms** (Exit)</span></span>

<span data-ttu-id="12d34-117">:::row::: :::column::: Verwenden Sie diese Zeit für Objekte oder Seiten, die eine Szene verlassen oder schließen.</span><span class="sxs-lookup"><span data-stu-id="12d34-117">:::row::: :::column::: Use for objects or pages that are exiting the scene or closing.</span></span>
<span data-ttu-id="12d34-118">Sie ermöglicht eine sehr schnelle direktionale Rückmeldung der UI, bei der das Timing die Framerate nicht beeinträchtigt und so eine flüssige Animation unterstützt.</span><span class="sxs-lookup"><span data-stu-id="12d34-118">Allows for very quick directional feedback of exiting UI where timing does not impede upon framerate to achieve a smooth animation.</span></span>
<span data-ttu-id="12d34-119">:::column-end::: :::column::: ![150 ms Bewegung](images/150msAlt.gif) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-119">:::column-end::: :::column::: ![150ms motion](images/150msAlt.gif) :::column-end::: :::row-end:::</span></span>

### <a name="300ms-enter"></a><span data-ttu-id="12d34-120">**300 ms** (Eintreten)</span><span class="sxs-lookup"><span data-stu-id="12d34-120">**300ms** (Enter)</span></span>

<span data-ttu-id="12d34-121">:::row::: :::column::: Verwenden Sie diese Zeit für Objekte oder Seiten, die in eine Szene eintreten oder sie öffnen</span><span class="sxs-lookup"><span data-stu-id="12d34-121">:::row::: :::column::: Use for objects or pages that are entering the scene or opening.</span></span>
<span data-ttu-id="12d34-122">Dies ist eine angemessene Zeitspanne, um Inhalte zu erkennen, wenn sie in die Szene eintreten.</span><span class="sxs-lookup"><span data-stu-id="12d34-122">Allows a reasonable amount of time to celebrate content as it enters the scene.</span></span>
<span data-ttu-id="12d34-123">:::column-end::: :::column::: ![300 ms Bewegung](images/300ms.gif) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-123">:::column-end::: :::column::: ![300ms motion](images/300ms.gif) :::column-end::: :::row-end:::</span></span>

### <a name="500ms-move"></a><span data-ttu-id="12d34-124">**≤ 500 ms** (Durchqueren)</span><span class="sxs-lookup"><span data-stu-id="12d34-124">**≤500ms** (Move)</span></span>

<span data-ttu-id="12d34-125">::: Zeile:::::: Spalte::: Verwenden Sie diese Zeit für Objekte, die eine einzelne Szene oder mehrere Szenen durchqueren.</span><span class="sxs-lookup"><span data-stu-id="12d34-125">:::row::: :::column::: Use for objects which are translating across a single scene or multiple scenes.</span></span> <span data-ttu-id="12d34-126">:::column-end::: :::column::: ![500 ms Bewegung](images/500ms.gif) :::column-end::: :::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-126">:::column-end::: :::column::: ![500ms motion](images/500ms.gif) :::column-end::: :::row-end:::</span></span>

## <a name="easing-in-fluent-motion"></a><span data-ttu-id="12d34-127">Geschwindigkeitsverlauf in Fluent-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="12d34-127">Easing in Fluent motion</span></span>

<span data-ttu-id="12d34-128">Die Änderung des Geschwindigkeitsverlaufs ist eine Möglichkeit, die Bewegungsdauer eines Objekts anzupassen.</span><span class="sxs-lookup"><span data-stu-id="12d34-128">Easing is a way to manipulate the velocity of an object as it travels.</span></span> <span data-ttu-id="12d34-129">Der Geschwindigkeitsverlauf ist der Leim, der alle Fluent-Bewegungserfahrungen verbindet.</span><span class="sxs-lookup"><span data-stu-id="12d34-129">It's the glue that ties together all the Fluent motion experiences.</span></span> <span data-ttu-id="12d34-130">Die Verwendung eines Geschwindigkeitsverlaufs kann die Anmutung von Objekten vereinheitlichen, die sich durch das System bewegen.</span><span class="sxs-lookup"><span data-stu-id="12d34-130">While extreme, the easing used in the system helps unify the physical feel of objects moving throughout the system.</span></span> <span data-ttu-id="12d34-131">Dies ist eine Möglichkeit zum Simulieren der realen Welt und lässt bewegte Objekte in ihrer Umgebung natürlich aussehen.</span><span class="sxs-lookup"><span data-stu-id="12d34-131">This is one way to mimic the real world, and make objects in motion feel like they belong in their environment.</span></span>

![Favoritenbild](images/easing.gif)

## <a name="apply-easing-to-motion"></a><span data-ttu-id="12d34-133">Anwenden eines Geschwindigkeitsverlaufs auf Bewegungen</span><span class="sxs-lookup"><span data-stu-id="12d34-133">Apply easing to motion</span></span>

<span data-ttu-id="12d34-134">Die folgenden Geschwindigkeitsverläufe vermitteln ein natürliches Verhalten und sind die Grundwerte, die wird für Fluent-Bewegungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="12d34-134">These easings will help you achieve a more natural feel, and are the baseline we use for Fluent motion.</span></span>

<span data-ttu-id="12d34-135">Die Codebeispiele zeigen, wie die empfohlene Werte auf Storyboardanimationen (XAML) oder Kompositionsanimationen (C#) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="12d34-135">The code examples show how to apply recommended easing values to Storyboard animations (XAML) or Composition animations (C#).</span></span>

### <a name="accelerate-exit"></a><span data-ttu-id="12d34-136">**Beschleunigen** (Verlassen)</span><span class="sxs-lookup"><span data-stu-id="12d34-136">**Accelerate** (Exit)</span></span>

<span data-ttu-id="12d34-137">:::row::: :::column::: Verwenden Sie dies für UI oder Objekte, die eine Szene verlassen.</span><span class="sxs-lookup"><span data-stu-id="12d34-137">:::row::: :::column::: Use for UI or objects that are exiting the scene.</span></span>

        Objects become powered and gain momentum until they reach escape velocity.
        The resulting feel is that the object is trying its hardest to get out of the user's way and make room for new content to come in.
    :::column-end:::
    :::column:::
        ![accelerate easing](images/accelEase.gif)
    :::column-end:::
<span data-ttu-id="12d34-138">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-138">:::row-end:::</span></span>

```
cubic-bezier(0.7 , 0 , 1 , 0.5)
```

```xaml
<!-- Use for XAML Storyboard animations. -->
<Storyboard x:Name="Storyboard">
    <DoubleAnimation Storyboard.TargetName="Translation" Storyboard.TargetProperty="X" From="0" To="200" Duration="0:0:0.15">
        <DoubleAnimation.EasingFunction>
            <ExponentialEase Exponent="4.5" EasingMode="EaseIn" />
        </DoubleAnimation.EasingFunction>
    </DoubleAnimation>
</Storyboard>
```

```csharp
// Use for Composition animations.
CubicBezierEasingFunction accelerate =
    _compositor.CreateCubicBezierEasingFunction(new Vector2(0.7f, 0.0f), new Vector2(1.0f, 0.5f));
_exitAnimation = _compositor.CreateScalarKeyFrameAnimation();
_exitAnimation.InsertKeyFrame(0.0f, _startValue);
_exitAnimation.InsertKeyFrame(1.0f, _endValue, accelerate);
_exitAnimation.Duration = TimeSpan.FromMilliseconds(150);
```

### <a name="decelerate-enter"></a><span data-ttu-id="12d34-139">**Verlangsamen** (Eintreten)</span><span class="sxs-lookup"><span data-stu-id="12d34-139">**Decelerate** (Enter)</span></span>

<span data-ttu-id="12d34-140">:::row::: :::column::: Verwenden Sie dies für Objekte oder Seiten, die in eine Szene eintreten oder sie öffnen</span><span class="sxs-lookup"><span data-stu-id="12d34-140">:::row::: :::column::: Use for objects or UI entering the scene, either navigating or spawning.</span></span>

        Once on-scene, the object is met with extreme friction, which slows the object to rest.
        The resulting feel is that the object traveled from a long distance away and entered at an extreme velocity, or is quickly returning to a rest state.

        Even if it's preceded by a moment of unresponsiveness, the velocity of the incoming object has the effect of feeling fast and responsive.
    :::column-end:::
    :::column:::
        ![decelerate easing](images/decelEase.gif)
    :::column-end:::
<span data-ttu-id="12d34-141">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-141">:::row-end:::</span></span>

```
cubic-bezier(0.1 , 0.9 , 0.2 , 1)
```

```xaml
<!-- Use for XAML Storyboard animations. -->
<Storyboard x:Name="Storyboard">
    <DoubleAnimation Storyboard.TargetName="Translation" Storyboard.TargetProperty="X" From="0" To="200" Duration="0:0:0.3">
        <DoubleAnimation.EasingFunction>
            <ExponentialEase Exponent="7" EasingMode="EaseOut" />
        </DoubleAnimation.EasingFunction>
    </DoubleAnimation>
</Storyboard>
```

```csharp
// Use for Composition animations.
CubicBezierEasingFunction decelerate =
    _compositor.CreateCubicBezierEasingFunction(new Vector2(0.1f, 0.9f), new Vector2(0.2f, 1.0f));
_enterAnimation = _compositor.CreateScalarKeyFrameAnimation();
_enterAnimation.InsertKeyFrame(0.0f, _startValue);
_enterAnimation.InsertKeyFrame(1.0f, _endValue, decelerate);
_enterAnimation.Duration = TimeSpan.FromMilliseconds(300);
```

### <a name="standard-easing-move"></a><span data-ttu-id="12d34-142">**Standard** (Durchqueren)</span><span class="sxs-lookup"><span data-stu-id="12d34-142">**Standard Easing** (Move)</span></span>

<span data-ttu-id="12d34-143">:::row::: :::column::: Dies ist der grundlegende Geschwindigkeitsverlauf für jede Änderung animierter Parameter innerhalb des Systems.</span><span class="sxs-lookup"><span data-stu-id="12d34-143">:::row::: :::column::: This is the baseline easing for any animated parameter change inside of the system.</span></span>
<span data-ttu-id="12d34-144">Verwenden Sie diesen Standard-Geschwindigkeitsverlauf für Objekte, die auf dem Bildschirm von Status zu Status wechseln, z. B. bei einer einfachen Positionsänderung.</span><span class="sxs-lookup"><span data-stu-id="12d34-144">Use standard easing for objects that change from state to state on-screen, such as a simple position change.</span></span> <span data-ttu-id="12d34-145">Verwenden Sie ihn zudem für Objekte, die sich in der Szene kontinuierlich verändern (Morphing), beispielsweise wachsen.</span><span class="sxs-lookup"><span data-stu-id="12d34-145">Also, use it for objects morphing in-scene, like an object that grows.</span></span>

        The resulting feel is that objects changing state from A to B are overcoming, and taken over by, natural forces.
    :::column-end:::
    :::column:::
        ![standard easing](images/standardEase.gif)
    :::column-end:::
<span data-ttu-id="12d34-146">:::row-end:::</span><span class="sxs-lookup"><span data-stu-id="12d34-146">:::row-end:::</span></span>

```
cubic-bezier(0.8 , 0 , 0.2 , 1)
```

```xaml
<!-- Use for XAML Storyboard animations. -->
<Storyboard x:Name="Storyboard">
    <DoubleAnimation Storyboard.TargetName="Translation" Storyboard.TargetProperty="X" From="0" To="200" Duration="0:0:0.5">
        <DoubleAnimation.EasingFunction>
            <CircleEase EasingMode="EaseInOut" />
        </DoubleAnimation.EasingFunction>
    </DoubleAnimation>
</Storyboard>
```

```csharp
// Use for Composition animations.
CubicBezierEasingFunction standard =
    _compositor.CreateCubicBezierEasingFunction(new Vector2(0.8f, 0.0f), new Vector2(0.2f, 1.0f));
 _moveAnimation = _compositor.CreateScalarKeyFrameAnimation();
 _moveAnimation.InsertKeyFrame(0.0f, _startValue);
 _moveAnimation.InsertKeyFrame(1.0f, _endValue, standard);
 _moveAnimation.Duration = TimeSpan.FromMilliseconds(500);
```

## <a name="related-articles"></a><span data-ttu-id="12d34-147">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="12d34-147">Related articles</span></span>

- [<span data-ttu-id="12d34-148">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="12d34-148">Motion overview</span></span>](index.md)
- [<span data-ttu-id="12d34-149">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="12d34-149">Directionality and gravity</span></span>](directionality-and-gravity.md)