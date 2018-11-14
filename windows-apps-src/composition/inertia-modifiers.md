---
author: jwmsft
title: Verwenden von Inertia-Modifiern zum Erstellen von Einrastpunkten
description: Lernen Sie, wie man mit dem InertiaModifier-Feature eines InteractionTracker Bewegungserlebnisse erzeugen kann, die an einem bestimmten Punkt einrasten.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 20c10b1cc621da834a8a7c411e75eb92b1944b5a
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6665202"
---
# <a name="create-snap-points-with-inertia-modifiers"></a><span data-ttu-id="99d7e-104">Erstellen von Einrastpunkten mit Inertia-Modifiern</span><span class="sxs-lookup"><span data-stu-id="99d7e-104">Create snap points with inertia modifiers</span></span>

<span data-ttu-id="99d7e-105">In diesem Artikel gehen wir näher darauf ein, wie man mit dem InertiaModifier-Feature eines InteractionTracker Bewegungserlebnisse erzeugen kann, die an einem bestimmten Punkt einrasten.</span><span class="sxs-lookup"><span data-stu-id="99d7e-105">In this article, we take a deeper dive into how to use an InteractionTracker’s InertiaModifier feature to create motion experiences that snap to a specified point.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99d7e-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="99d7e-106">Prerequisites</span></span>

<span data-ttu-id="99d7e-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="99d7e-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="99d7e-108">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="99d7e-108">Input-driven animations</span></span>](input-driven-animations.md)
- [<span data-ttu-id="99d7e-109">Angepasste Manipulation mit InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="99d7e-109">Custom manipulation experiences with InteractionTracker</span></span>](interaction-tracker-manipulations.md)
- [<span data-ttu-id="99d7e-110">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="99d7e-110">Relation based animations</span></span>](relation-animations.md)

## <a name="what-are-snap-points-and-why-are-they-useful"></a><span data-ttu-id="99d7e-111">Was sind Einrastpunkte und warum sind sie nützlich?</span><span class="sxs-lookup"><span data-stu-id="99d7e-111">What are snap points and why are they useful?</span></span>

<span data-ttu-id="99d7e-112">Beim Erstellen benutzerdefinierter Manipulationserfahrungen ist es manchmal hilfreich, spezielle _Positionspunkte_ innerhalb der scrollbaren/zoomfähigen Canvas zu erstellen, an denen InteractionTracker immer zur Ruhe kommt.</span><span class="sxs-lookup"><span data-stu-id="99d7e-112">When building custom manipulation experiences, sometimes it is helpful to create specialized _position points_ within the scrollable/zoomable canvas that InteractionTracker will always come to rest at.</span></span> <span data-ttu-id="99d7e-113">Diese werden häufig als _Einrastpunkte_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="99d7e-113">These are often called _snap points_.</span></span>

<span data-ttu-id="99d7e-114">Beachten Sie im folgenden Beispiel, wie das Scrollen die Benutzeroberfläche zwischen den verschiedenen Bildern an einer ungünstigen Position belassen kann:</span><span class="sxs-lookup"><span data-stu-id="99d7e-114">Notice in the following example how the scrolling can leave the UI in an awkward position between the different images:</span></span>

![Scrollen ohne Einrastpunkte](images/animation/snap-points-none.gif)

<span data-ttu-id="99d7e-116">Wenn Sie Einrastpunkte hinzufügen, „rasten“ sie an einer bestimmten Position ein, wenn Sie das Scrollen zwischen den Bildern stoppen.</span><span class="sxs-lookup"><span data-stu-id="99d7e-116">If you add snap points, when you stop scrolling between the images, they "snap" to a specified position.</span></span> <span data-ttu-id="99d7e-117">Mit Einrastpunkten wird das Scrollen durch Bilder viel sauberer und schneller.</span><span class="sxs-lookup"><span data-stu-id="99d7e-117">With snap points, it makes the experience of scrolling through images much cleaner and more responsive.</span></span>

![Scrollen mit einem einzelnen Einrastpunkt](images/animation/snap-points-single.gif)

## <a name="interactiontracker-and-inertiamodifiers"></a><span data-ttu-id="99d7e-119">InteractionTracker und InertiaModifier</span><span class="sxs-lookup"><span data-stu-id="99d7e-119">InteractionTracker and InertiaModifiers</span></span>

<span data-ttu-id="99d7e-120">Wenn Sie mit InteractionTracker benutzerdefinierte Manipulationserfahrungen erstellen, können Sie mithilfe von InertiaModifiern Einrastpunkt-Erlebnisse erzeugen.</span><span class="sxs-lookup"><span data-stu-id="99d7e-120">When building customized manipulation experiences with InteractionTracker, you can create snap point motion experiences by utilizing InertiaModifiers.</span></span> <span data-ttu-id="99d7e-121">InertiaModifier sind im Wesentlichen eine Möglichkeit, um zu definieren, wo oder wie der InteractionTracker sein Ziel erreicht, wenn er in den Inertia-Zustand eintritt.</span><span class="sxs-lookup"><span data-stu-id="99d7e-121">InertiaModifiers are essentially a way for you to define where or how InteractionTracker reaches its destination when entering the Inertia state.</span></span> <span data-ttu-id="99d7e-122">Sie können InertiaModifier anwenden, um die X- oder Y-Position oder Scale Eigenschaften von InteractionTracker zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="99d7e-122">You can apply InertiaModifiers to impact the X or Y position or Scale properties of InteractionTracker.</span></span>

<span data-ttu-id="99d7e-123">Es gibt 3 Arten von InertiaModifiern:</span><span class="sxs-lookup"><span data-stu-id="99d7e-123">There are 3 types of InertiaModifiers:</span></span>

- <span data-ttu-id="99d7e-124">InteractionTrackerInertiaRestingValue – Eine Möglichkeit, die Endposition nach einer Interaktion oder programmatischen Beschleunigung zu verändern.</span><span class="sxs-lookup"><span data-stu-id="99d7e-124">InteractionTrackerInertiaRestingValue – a way to modify the final resting position after an interaction or programmatic velocity.</span></span> <span data-ttu-id="99d7e-125">Eine vordefinierte Bewegung bringt den InteractionTracker in diese Position.</span><span class="sxs-lookup"><span data-stu-id="99d7e-125">A predefined motion will take InteractionTracker to that position.</span></span>
- <span data-ttu-id="99d7e-126">InteractionTrackerInertiaMotion – Eine Möglichkeit zur Definition einer bestimmten Bewegung, die InteractionTracker nach einer Interaktion oder programmatische Beschleunigung durchführt.</span><span class="sxs-lookup"><span data-stu-id="99d7e-126">InteractionTrackerInertiaMotion – a way to define a specific motion InteractionTracker will perform after an interaction or programmatic velocity.</span></span> <span data-ttu-id="99d7e-127">Aus dieser Bewegung wird die endgültige Position abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="99d7e-127">The final position will be derived from this motion.</span></span>
- <span data-ttu-id="99d7e-128">InteractionTrackerInertiaNaturalMotion – Eine Möglichkeit, die endgültige Ruheposition nach einer Interaktion oder programmatischen Beschleunigung zu definieren, aber mit einer physikalisch basierten Animation (NaturalMotionAnimation).</span><span class="sxs-lookup"><span data-stu-id="99d7e-128">InteractionTrackerInertiaNaturalMotion – a way to define the final resting position after an interaction or programmatic velocity but with a physics based animation (NaturalMotionAnimation).</span></span>

<span data-ttu-id="99d7e-129">InteractionTracker wertet bei Inertia alle ihm zugeordneten InertiaModifier aus und stellt fest, ob einer von ihnen zutrifft.</span><span class="sxs-lookup"><span data-stu-id="99d7e-129">When entering Inertia, InteractionTracker evaluates each of the InertiaModifiers assigned to it and determines if any of them apply.</span></span> <span data-ttu-id="99d7e-130">Das bedeutet, dass Sie mehrere InertiaModifier anlegen und einem InteractionTracker zuweisen können:</span><span class="sxs-lookup"><span data-stu-id="99d7e-130">This means you can create and assign multiple InertiaModifiers to an InteractionTracker, But, when defining each, you need to do the following:</span></span>

1. <span data-ttu-id="99d7e-131">Definieren der Bedingung – Ein Ausdruck, der die bedingte Anweisung definiert, wann dieser spezifische InertiaModifier stattfinden soll.</span><span class="sxs-lookup"><span data-stu-id="99d7e-131">Define the Condition – an Expression that defines the conditional statement when this specific InertiaModifier should take place.</span></span> <span data-ttu-id="99d7e-132">Dies erfordert oft einen Blick auf die NaturalRestingPosition des InteractionTracker (Standard-Inertia des Ziels).</span><span class="sxs-lookup"><span data-stu-id="99d7e-132">This often requires looking at InteractionTracker’s NaturalRestingPosition (destination given default Inertia).</span></span>
1. <span data-ttu-id="99d7e-133">Definieren von RestingValue/Motion/NaturalMotion – Definieren Sie den tatsächlichen Resting Value Expression, Motion Expression oder NaturalMotionAnimation, der bei Erfüllung der Bedingung stattfindet.</span><span class="sxs-lookup"><span data-stu-id="99d7e-133">Define the RestingValue/Motion/NaturalMotion – define the actual Resting Value Expression, Motion Expression or NaturalMotionAnimation that takes place when the condition is met.</span></span>

> [!NOTE]
> <span data-ttu-id="99d7e-134">Der Zustandsaspekt des InertiaModifier wird nur einmalig ausgewertet, wenn der InteractionTracker in Inertia eintritt.</span><span class="sxs-lookup"><span data-stu-id="99d7e-134">The condition aspect of the InertiaModifiers are only evaluated once when InteractionTracker enters Inertia.</span></span> <span data-ttu-id="99d7e-135">Allerdings wird nur bei InertiaMotion der Motion-Expression für jeden Frame des Modifikators, dessen Bedingung wahr ist, ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="99d7e-135">However, only for InertiaMotion, the motion Expression is evaluated every frame for the modifier whose condition is true.</span></span>

## <a name="example"></a><span data-ttu-id="99d7e-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="99d7e-136">Example</span></span>

<span data-ttu-id="99d7e-137">Sehen wir uns nun an, wie Sie InertiaModifier verwenden können, um einige Einrastpunkte zu erzeugen, mit denen Sie die scrollende Canvas mit Bildern nachstellen können.</span><span class="sxs-lookup"><span data-stu-id="99d7e-137">Now let’s look at how you can use InertiaModifiers to create some snap point experiences to recreate the scrolling canvas of images.</span></span> <span data-ttu-id="99d7e-138">In diesem Beispiel soll jede Manipulation potentiell durch ein einzelnes Bild gehen – dies wird oft als „Single Mandatory Snap Points“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="99d7e-138">In this example, each manipulation is meant to potentially move through a single image – this is often referred to as Single Mandatory Snap Points.</span></span>

<span data-ttu-id="99d7e-139">Beginnen wir mit der Einrichtung von InteractionTracker, der VisualInteractionSource und dem Ausdruck, der die Position von InteractionTracker nutzen wird.</span><span class="sxs-lookup"><span data-stu-id="99d7e-139">Let’s start by setting up InteractionTracker, the VisualInteractionSource and the Expression that will leverage the position of InteractionTracker.</span></span>

```csharp
private void SetupInput()
{
    _tracker = InteractionTracker.Create(_compositor);
    _tracker.MinPosition = new Vector3(0f);
    _tracker.MaxPosition = new Vector3(3000f);

    _source = VisualInteractionSource.Create(_root);
    _source.ManipulationRedirectionMode =
        VisualInteractionSourceRedirectionMode.CapableTouchpadOnly;
    _source.PositionYSourceMode = InteractionSourceMode.EnabledWithInertia;
    _tracker.InteractionSources.Add(_source);

    var scrollExp = _compositor.CreateExpressionAnimation("-tracker.Position.Y");
    scrollExp.SetReferenceParameter("tracker", _tracker);
    ElementCompositionPreview.GetElementVisual(scrollPanel).StartAnimation("Offset.Y", scrollExp);
}
```

<span data-ttu-id="99d7e-140">Da ein einzelnes obligatorisches Einrastpunktverhalten den Inhalt entweder nach oben oder unten verschieben wird, benötigen Sie zwei verschiedene Inertia-Modifier: einen, der den Inhalt nach oben und einen, der nach unten bewegt.</span><span class="sxs-lookup"><span data-stu-id="99d7e-140">Next, because a Single Mandatory Snap Point behavior either will move the content up or down, you will need two different inertia modifiers: one that moves the Scrollable content up, and one that moves it down.</span></span>

```csharp
// Snap-Point to move the content up
var snapUpModifier = InteractionTrackerInertiaRestingValue.Create(_compositor);
// Snap-Point to move the content down
var snapDownModifier = InteractionTrackerInertiaRestingValue.Create(_compositor);
```

<span data-ttu-id="99d7e-141">Ob das Einrasten Auf- oder Abwärts erfolgen soll, hängt davon ab, wo der InteractionTracker im Verhältnis zum Einrastabstand – dem Abstand zwischen den Einrastpositionen – auf natürliche Weise landen würde.</span><span class="sxs-lookup"><span data-stu-id="99d7e-141">Whether to snap up or down is determined based on where InteractionTracker naturally would land within relative to the snap distance – the distance between the snap locations.</span></span> <span data-ttu-id="99d7e-142">Wenn die Hälfte der Strecke überschritten ist, geht es nach unten. Andernfalls nach oben.</span><span class="sxs-lookup"><span data-stu-id="99d7e-142">If past the halfway point, then snap down, otherwise snap up.</span></span> <span data-ttu-id="99d7e-143">(In diesem Beispiel speichern Sie den Einrastabstand in einem PropertySet)</span><span class="sxs-lookup"><span data-stu-id="99d7e-143">(In this example, you store the snap distance in a PropertySet)</span></span>

```csharp
// Is NaturalRestingPosition less than the halfway point between Snap Points?
snapUpModifier.Condition = _compositor.CreateExpressionAnimation(
"this.Target.NaturalRestingPosition.y < (this.StartingValue – ” + “mod(this.StartingValue, prop.snapDistance) + prop.snapDistance / 2)");
snapUpModifier.Condition.SetReferenceParameter("prop", _propSet);
// Is NaturalRestingPosition greater than the halfway point between Snap Points?
snapDownModifier.Condition = _compositor.CreateExpressionAnimation(
"this.Target.NaturalRestingPosition.y >= (this.StartingValue – ” + “mod(this.StartingValue, prop.snapDistance) + prop.snapDistance / 2)");
snapDownModifier.Condition.SetReferenceParameter("prop", _propSet);
```

<span data-ttu-id="99d7e-144">Dieses Diagramm gibt eine visuelle Beschreibung der Logik, die gerade geschieht:</span><span class="sxs-lookup"><span data-stu-id="99d7e-144">This diagram gives a visual description to the logic that is happening:</span></span>

![Inertia-Modifier-Diagramm](images/animation/inertia-modifier-diagram.png)

<span data-ttu-id="99d7e-146">Nun müssen Sie nur noch die Resting-Values für jeden InertiaModifier definieren: entweder bewegen Sie die Position des InteractionTracker in die vorherige oder die nächste Einrastposition.</span><span class="sxs-lookup"><span data-stu-id="99d7e-146">Now you just need to define the Resting Values for each InertiaModifier: either move the position of InteractionTracker to the previous snap position or the next one.</span></span>

```csharp
snapUpModifier.RestingValue = _compositor.CreateExpressionAnimation(
"this.StartingValue - mod(this.StartingValue, prop.snapDistance)");
snapUpModifier.RestingValue.SetReferenceParameter("prop", _propSet);
snapForwardModifier.RestingValue = _compositor.CreateExpressionAnimation(
"this.StartingValue + prop.snapDistance - mod(this.StartingValue, ” + “prop.snapDistance)");
snapForwardModifier.RestingValue.SetReferenceParameter("prop", _propSet);
```

<span data-ttu-id="99d7e-147">Fügen Sie schließlich die InertiaModifier zu InteractionTracker hinzu.</span><span class="sxs-lookup"><span data-stu-id="99d7e-147">Finally, add the InertiaModifiers to InteractionTracker.</span></span> <span data-ttu-id="99d7e-148">Wenn InteractionTracker nun in den InertiaState eintritt, wird er die Bedingungen Ihrer InertiaModifier prüfen, um zu sehen, ob seine Position geändert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="99d7e-148">Now when InteractionTracker enters it’s InertiaState, it will check the conditions of your InertiaModifiers to see if its position should be modified.</span></span>

```csharp
var modifiers = new InteractionTrackerInertiaRestingValue[] { 
snapUpModifier, snapDownModifier };
_tracker.ConfigurePositionYInertiaModifiers(modifiers);
```