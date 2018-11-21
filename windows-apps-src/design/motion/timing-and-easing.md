---
author: jwmsft
Description: Learn how Fluent motion uses timing and easing functions.
title: Timing und Geschwindigkeitsverlauf – Animation in UWP-Apps
label: Timing and easing
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
doc-status: Draft
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: bce437a9c9ba6bac8beb0ba705020065bad29b83
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7556909"
---
# <a name="timing-and-easing"></a><span data-ttu-id="1446d-103">Timing und Geschwindigkeitsverlauf</span><span class="sxs-lookup"><span data-stu-id="1446d-103">Timing and easing</span></span>

<span data-ttu-id="1446d-104">Bewegung basiert zwar auf der realen Welt, aber auch in einem digitalen Medium werden Geschwindigkeit und Leistung erwartet.</span><span class="sxs-lookup"><span data-stu-id="1446d-104">While motion is based in the real world, we are also a digital medium, which comes with an expectation of speed and performance.</span></span> 

## <a name="how-fluent-motion-uses-time"></a><span data-ttu-id="1446d-105">Fluent-Bewegungen und Timing</span><span class="sxs-lookup"><span data-stu-id="1446d-105">How Fluent motion uses time</span></span>

<span data-ttu-id="1446d-106">Timing ist ein wichtiges Element, um die Bewegung von Objekten natürlich erscheinen zu lassen, die in die Benutzeroberfläche eintreten, sie verlassen oder sich darin bewegen.</span><span class="sxs-lookup"><span data-stu-id="1446d-106">Timing is an important element to making motion feel natural for objects entering, exiting, or moving within the UI.</span></span>

1. <span data-ttu-id="1446d-107">Objekte oder Szenen, die in das Sichtfeld eintreten, sind schnell und auffällig.</span><span class="sxs-lookup"><span data-stu-id="1446d-107">Objects or scenes entering the view are quick, but celebrated.</span></span> <span data-ttu-id="1446d-108">Die Animationen für diese Elemente dauern in der Regel längere als die für austretende Elemente, um den hierarchischen Aufbau einer Szene zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1446d-108">These animations are typically longer in duration than exits to allow for hierarchical build-up of a scene.</span></span>
1. <span data-ttu-id="1446d-109">Objekte oder Szenen, die das Sichtfeld verlassen, sind sehr schnell.</span><span class="sxs-lookup"><span data-stu-id="1446d-109">Objects or scenes exiting the view are very quick.</span></span> <span data-ttu-id="1446d-110">Der Benutzer sollte nachvollziehen können, wo die UI verbleibt.</span><span class="sxs-lookup"><span data-stu-id="1446d-110">The user should be able to understand where the UI went.</span></span> <span data-ttu-id="1446d-111">Nachdem die UI jedoch geschlossen wurde, sollte sie aus dem Weg gehen.</span><span class="sxs-lookup"><span data-stu-id="1446d-111">However, once the UI is dismissed, it should get out of the way.</span></span>
1. <span data-ttu-id="1446d-112">Objekte, die sich durch eine Szene bewegen, sollten dafür eine Dauer benötigen, die der zurückzulegenden Entfernung entspricht.</span><span class="sxs-lookup"><span data-stu-id="1446d-112">Objects translating across a scene should have a duration appropriate to the amount of distance they travel.</span></span>

## <a name="timing-in-fluent-motion"></a><span data-ttu-id="1446d-113">Timing für Fluent-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="1446d-113">Timing in Fluent motion</span></span>

<span data-ttu-id="1446d-114">Für das Timing von Fluent-Bewegungen gelten 500 ms (eine halbe Sekunde) als Grundeinheit, da dies die maximale Zeit ist, die ein Benutzer als unmittelbar empfindet.</span><span class="sxs-lookup"><span data-stu-id="1446d-114">The timing of motion in Fluent uses 500ms (or one-half second) as a baseline because this is the maximum amount of time that a user perceives as instant.</span></span>

![Favoritenbild](images/time.gif)

### <a name="150ms-exit"></a><span data-ttu-id="1446d-116">**150 ms** (Verlassen)</span><span class="sxs-lookup"><span data-stu-id="1446d-116">**150ms** (Exit)</span></span>

:::row:::
    :::column:::
        Use for objects or pages that are exiting the scene or closing.
        Allows for very quick directional feedback of exiting UI where timing does not impede upon framerate to achieve a smooth animation.
    :::column-end:::
    :::column:::
        ![150ms motion](images/150msAlt.gif)
    :::column-end:::
:::row-end:::

### <a name="300ms-enter"></a><span data-ttu-id="1446d-117">**300 ms** (Eintreten)</span><span class="sxs-lookup"><span data-stu-id="1446d-117">**300ms** (Enter)</span></span>

:::row:::
    :::column:::
        Use for objects or pages that are entering the scene or opening.
        Allows a reasonable amount of time to celebrate content as it enters the scene.
    :::column-end:::
    :::column:::
        ![300ms motion](images/300ms.gif)
    :::column-end:::
:::row-end:::

### <a name="500ms-move"></a><span data-ttu-id="1446d-118">**≤ 500 ms** (Durchqueren)</span><span class="sxs-lookup"><span data-stu-id="1446d-118">**≤500ms** (Move)</span></span>

:::row:::
    :::column:::
        Use for objects which are translating across a single scene or multiple scenes. 
    :::column-end:::
    :::column:::
        ![500ms motion](images/500ms.gif)
    :::column-end:::
:::row-end:::

## <a name="easing-in-fluent-motion"></a><span data-ttu-id="1446d-119">Geschwindigkeitsverlauf in Fluent-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="1446d-119">Easing in Fluent motion</span></span>

<span data-ttu-id="1446d-120">Die Änderung des Geschwindigkeitsverlaufs ist eine Möglichkeit, die Bewegungsdauer eines Objekts anzupassen.</span><span class="sxs-lookup"><span data-stu-id="1446d-120">Easing is a way to manipulate the velocity of an object as it travels.</span></span> <span data-ttu-id="1446d-121">Der Geschwindigkeitsverlauf ist der Leim, der alle Fluent-Bewegungserfahrungen verbindet.</span><span class="sxs-lookup"><span data-stu-id="1446d-121">It's the glue that ties together all the Fluent motion experiences.</span></span> <span data-ttu-id="1446d-122">Die Verwendung eines Geschwindigkeitsverlaufs kann die Anmutung von Objekten vereinheitlichen, die sich durch das System bewegen.</span><span class="sxs-lookup"><span data-stu-id="1446d-122">While extreme, the easing used in the system helps unify the physical feel of objects moving throughout the system.</span></span> <span data-ttu-id="1446d-123">Dies ist eine Möglichkeit zum Simulieren der realen Welt und lässt bewegte Objekte in ihrer Umgebung natürlich aussehen.</span><span class="sxs-lookup"><span data-stu-id="1446d-123">This is one way to mimic the real world, and make objects in motion feel like they belong in their environment.</span></span>

![Favoritenbild](images/easing.gif)

## <a name="apply-easing-to-motion"></a><span data-ttu-id="1446d-125">Anwenden eines Geschwindigkeitsverlaufs auf Bewegungen</span><span class="sxs-lookup"><span data-stu-id="1446d-125">Apply easing to motion</span></span>

<span data-ttu-id="1446d-126">Die folgenden Geschwindigkeitsverläufe vermitteln ein natürliches Verhalten und sind die Grundwerte, die wird für Fluent-Bewegungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1446d-126">These easings will help you achieve a more natural feel, and are the baseline we use for Fluent motion.</span></span>

<span data-ttu-id="1446d-127">Die Codebeispiele zeigen, wie die empfohlene Werte auf Storyboardanimationen (XAML) oder Kompositionsanimationen (C#) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="1446d-127">The code examples show how to apply recommended easing values to Storyboard animations (XAML) or Composition animations (C#).</span></span>

### <a name="accelerate-exit"></a><span data-ttu-id="1446d-128">**Beschleunigen** (Verlassen)</span><span class="sxs-lookup"><span data-stu-id="1446d-128">**Accelerate** (Exit)</span></span>

:::row:::
    :::column:::
        Use for UI or objects that are exiting the scene.

        Objects become powered and gain momentum until they reach escape velocity.
        The resulting feel is that the object is trying its hardest to get out of the user's way and make room for new content to come in.
    :::column-end:::
    :::column:::
        ![accelerate easing](images/accelEase.gif)
    :::column-end:::
:::row-end:::

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

### <a name="decelerate-enter"></a><span data-ttu-id="1446d-129">**Verlangsamen** (Eintreten)</span><span class="sxs-lookup"><span data-stu-id="1446d-129">**Decelerate** (Enter)</span></span>

:::row:::
    :::column:::
        Use for objects or UI entering the scene, either navigating or spawning.

        Once on-scene, the object is met with extreme friction, which slows the object to rest.
        The resulting feel is that the object traveled from a long distance away and entered at an extreme velocity, or is quickly returning to a rest state.

        Even if it's preceded by a moment of unresponsiveness, the velocity of the incoming object has the effect of feeling fast and responsive.
    :::column-end:::
    :::column:::
        ![decelerate easing](images/decelEase.gif)
    :::column-end:::
:::row-end:::

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

### <a name="standard-easing-move"></a><span data-ttu-id="1446d-130">**Standard** (Durchqueren)</span><span class="sxs-lookup"><span data-stu-id="1446d-130">**Standard Easing** (Move)</span></span>

:::row:::
    :::column:::
        This is the baseline easing for any animated parameter change inside of the system.
        Use standard easing for objects that change from state to state on-screen, such as a simple position change. Also, use it for objects morphing in-scene, like an object that grows.

        The resulting feel is that objects changing state from A to B are overcoming, and taken over by, natural forces.
    :::column-end:::
    :::column:::
        ![standard easing](images/standardEase.gif)
    :::column-end:::
:::row-end:::

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

## <a name="related-articles"></a><span data-ttu-id="1446d-131">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="1446d-131">Related articles</span></span>

- [<span data-ttu-id="1446d-132">Übersicht über Bewegungen</span><span class="sxs-lookup"><span data-stu-id="1446d-132">Motion overview</span></span>](index.md)
- [<span data-ttu-id="1446d-133">Direktionalität und Schwerkraft</span><span class="sxs-lookup"><span data-stu-id="1446d-133">Directionality and gravity</span></span>](directionality-and-gravity.md)
