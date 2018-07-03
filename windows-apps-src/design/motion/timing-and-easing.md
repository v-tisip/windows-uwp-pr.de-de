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
# <a name="timing-and-easing"></a>Timing und Geschwindigkeitsverlauf

Bewegung basiert zwar auf der realen Welt, aber auch in einem digitalen Medium werden Geschwindigkeit und Leistung erwartet. 

## <a name="how-fluent-motion-uses-time"></a>Fluent-Bewegungen und Timing

Timing ist ein wichtiges Element, um die Bewegung von Objekten natürlich erscheinen zu lassen, die in die Benutzeroberfläche eintreten, sie verlassen oder sich darin bewegen.

1. Objekte oder Szenen, die in das Sichtfeld eintreten, sind schnell und auffällig. Die Animationen für diese Elemente dauern in der Regel längere als die für austretende Elemente, um den hierarchischen Aufbau einer Szene zu ermöglichen.
1. Objekte oder Szenen, die das Sichtfeld verlassen, sind sehr schnell. Der Benutzer sollte nachvollziehen können, wo die UI verbleibt. Nachdem die UI jedoch geschlossen wurde, sollte sie aus dem Weg gehen.
1. Objekte, die sich durch eine Szene bewegen, sollten dafür eine Dauer benötigen, die der zurückzulegenden Entfernung entspricht.

## <a name="timing-in-fluent-motion"></a>Timing für Fluent-Bewegungen

Für das Timing von Fluent-Bewegungen gelten 500 ms (eine halbe Sekunde) als Grundeinheit, da dies die maximale Zeit ist, die ein Benutzer als unmittelbar empfindet.

![Favoritenbild](images/time.gif)

### <a name="150ms-exit"></a>**150 ms** (Verlassen)

:::row::: :::column::: Verwenden Sie diese Zeit für Objekte oder Seiten, die eine Szene verlassen oder schließen.
Sie ermöglicht eine sehr schnelle direktionale Rückmeldung der UI, bei der das Timing die Framerate nicht beeinträchtigt und so eine flüssige Animation unterstützt.
:::column-end::: :::column::: ![150 ms Bewegung](images/150msAlt.gif) :::column-end::: :::row-end:::

### <a name="300ms-enter"></a>**300 ms** (Eintreten)

:::row::: :::column::: Verwenden Sie diese Zeit für Objekte oder Seiten, die in eine Szene eintreten oder sie öffnen
Dies ist eine angemessene Zeitspanne, um Inhalte zu erkennen, wenn sie in die Szene eintreten.
:::column-end::: :::column::: ![300 ms Bewegung](images/300ms.gif) :::column-end::: :::row-end:::

### <a name="500ms-move"></a>**≤ 500 ms** (Durchqueren)

::: Zeile:::::: Spalte::: Verwenden Sie diese Zeit für Objekte, die eine einzelne Szene oder mehrere Szenen durchqueren. :::column-end::: :::column::: ![500 ms Bewegung](images/500ms.gif) :::column-end::: :::row-end:::

## <a name="easing-in-fluent-motion"></a>Geschwindigkeitsverlauf in Fluent-Bewegungen

Die Änderung des Geschwindigkeitsverlaufs ist eine Möglichkeit, die Bewegungsdauer eines Objekts anzupassen. Der Geschwindigkeitsverlauf ist der Leim, der alle Fluent-Bewegungserfahrungen verbindet. Die Verwendung eines Geschwindigkeitsverlaufs kann die Anmutung von Objekten vereinheitlichen, die sich durch das System bewegen. Dies ist eine Möglichkeit zum Simulieren der realen Welt und lässt bewegte Objekte in ihrer Umgebung natürlich aussehen.

![Favoritenbild](images/easing.gif)

## <a name="apply-easing-to-motion"></a>Anwenden eines Geschwindigkeitsverlaufs auf Bewegungen

Die folgenden Geschwindigkeitsverläufe vermitteln ein natürliches Verhalten und sind die Grundwerte, die wird für Fluent-Bewegungen verwenden.

Die Codebeispiele zeigen, wie die empfohlene Werte auf Storyboardanimationen (XAML) oder Kompositionsanimationen (C#) angewendet werden.

### <a name="accelerate-exit"></a>**Beschleunigen** (Verlassen)

:::row::: :::column::: Verwenden Sie dies für UI oder Objekte, die eine Szene verlassen.

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

### <a name="decelerate-enter"></a>**Verlangsamen** (Eintreten)

:::row::: :::column::: Verwenden Sie dies für Objekte oder Seiten, die in eine Szene eintreten oder sie öffnen

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

### <a name="standard-easing-move"></a>**Standard** (Durchqueren)

:::row::: :::column::: Dies ist der grundlegende Geschwindigkeitsverlauf für jede Änderung animierter Parameter innerhalb des Systems.
Verwenden Sie diesen Standard-Geschwindigkeitsverlauf für Objekte, die auf dem Bildschirm von Status zu Status wechseln, z. B. bei einer einfachen Positionsänderung. Verwenden Sie ihn zudem für Objekte, die sich in der Szene kontinuierlich verändern (Morphing), beispielsweise wachsen.

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

## <a name="related-articles"></a>Verwandte Artikel

- [Übersicht über Bewegungen](index.md)
- [Direktionalität und Schwerkraft](directionality-and-gravity.md)