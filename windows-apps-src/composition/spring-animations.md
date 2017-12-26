---
author: jwmsft
title: Feder-Animationen
description: 
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: bba677ecaaf5e82f2b0d559ce86604925c546fb8
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="spring-animations"></a><span data-ttu-id="6441e-103">Feder-Animationen</span><span class="sxs-lookup"><span data-stu-id="6441e-103">Spring animations</span></span>

<span data-ttu-id="6441e-104">Der Artikel zeigt, wie man Feder-NaturalMotionAnimations verwendet.</span><span class="sxs-lookup"><span data-stu-id="6441e-104">The article shows how to use spring NaturalMotionAnimations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6441e-105">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="6441e-105">Prerequisites</span></span>

<span data-ttu-id="6441e-106">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="6441e-106">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="6441e-107">Natürliche Bewegungsanimationen</span><span class="sxs-lookup"><span data-stu-id="6441e-107">Natural motion animations</span></span>](natural-animations.md)

## <a name="why-springs"></a><span data-ttu-id="6441e-108">Warum Federanimationen?</span><span class="sxs-lookup"><span data-stu-id="6441e-108">Why springs?</span></span>

<span data-ttu-id="6441e-109">Federanimationen sind ein allgemeines Bewegungserlebnis, das wir alle irgendwann einmal in unserem Leben erlebt haben; von Spielzeug bis hin zum Physikunterricht mit einem Federblock.</span><span class="sxs-lookup"><span data-stu-id="6441e-109">Springs are a common motion experience we've all experienced at some point in our lives; ranging from slinky toys to Physics classroom experiences with a spring-tied block.</span></span> <span data-ttu-id="6441e-110">Die oszillierende Bewegung einer Feder löst oft eine spielerische und heitere emotionale Reaktion der Betrachter aus.</span><span class="sxs-lookup"><span data-stu-id="6441e-110">The oscillating motion of a spring often incites a playful and lighthearted emotional response from those who observe it.</span></span> <span data-ttu-id="6441e-111">Das Ergebnis ist, dass die Bewegung einer Feder sich gut in eine Benutzeroberfläche für die Anwendung übersetzen lässt, die ein lebendigeres Bewegungserlebnis schaffen möchte, das dem Endbenutzer mehr überzeugt als eine traditionelle Cubic-Bezier-Animation.</span><span class="sxs-lookup"><span data-stu-id="6441e-111">As a result, the motion of a spring translates well into application UI for those who are looking to create a livelier motion experience that "pops" more to the end user than a traditional Cubic Bezier.</span></span> <span data-ttu-id="6441e-112">In diesen Fällen sorgt die Federbewegung nicht nur für ein lebendigeres Bewegungserlebnis, sondern kann auch die Aufmerksamkeit auf neue oder gerade animierte Inhalte lenken.</span><span class="sxs-lookup"><span data-stu-id="6441e-112">In these cases, spring motion not only creates a livelier motion experience, but also can help draw attention to new or currently animating content.</span></span> <span data-ttu-id="6441e-113">Je nach Anwendungs-Branding oder Bewegungssprache ist die Federbewegung ausgeprägter und sichtbarer und in anderen Fällen subtiler.</span><span class="sxs-lookup"><span data-stu-id="6441e-113">Depending on the application branding or motion language, the oscillation is more pronounced and visible, but in other cases it is more subtle.</span></span>

![<span data-ttu-id="6441e-114">Bewegung mit Federanimation](images/animation/offset-spring.gif)
![Bewegung mit Cubic-Bezier-Animation</span><span class="sxs-lookup"><span data-stu-id="6441e-114">Motion with spring animation](images/animation/offset-spring.gif)
![Motion with Cubic Bezier animation</span></span>](images/animation/offset-cubic-bezier.gif)

## <a name="using-springs-in-your-ui"></a><span data-ttu-id="6441e-115">Verwendung von Federbewegungen in Ihrem UI</span><span class="sxs-lookup"><span data-stu-id="6441e-115">Using springs in your UI</span></span>

<span data-ttu-id="6441e-116">Wie bereits erwähnt, können Federanimationen eine nützliche Bewegung sein, um sich in Ihre App zu integrieren und ein sehr vertrautes und spielerisches UI-Erlebnis einzuführen.</span><span class="sxs-lookup"><span data-stu-id="6441e-116">As mentioned previously, springs can be a useful motion to integrate into your app to introduce a very familiar and playful UI experience.</span></span> <span data-ttu-id="6441e-117">Übliche Verwendung von Federanimationen in UIs sind:</span><span class="sxs-lookup"><span data-stu-id="6441e-117">Common usage of springs in UI are:</span></span>

| <span data-ttu-id="6441e-118">Beschreibung der Verwendung der Federanimation</span><span class="sxs-lookup"><span data-stu-id="6441e-118">Spring Usage Description</span></span> | <span data-ttu-id="6441e-119">Visuelles Beispiel</span><span class="sxs-lookup"><span data-stu-id="6441e-119">Visual Example</span></span> |
| ------------------------ | -------------- |
| <span data-ttu-id="6441e-120">Eine Bewegungserfahrung „herausstechen“ und lebendiger aussehen lassen.</span><span class="sxs-lookup"><span data-stu-id="6441e-120">Making a motion experience "pop" and look livelier.</span></span> <span data-ttu-id="6441e-121">(Animating Scale)</span><span class="sxs-lookup"><span data-stu-id="6441e-121">(Animating Scale)</span></span> | ![Skalierungsbewegung mit Federanimation](images/animation/scale-spring.gif) |
| <span data-ttu-id="6441e-123">Eine Bewegungserfahrung subtil energetischer wirken lassen (Animating Offset)</span><span class="sxs-lookup"><span data-stu-id="6441e-123">Making a motion experience subtly feel more energetic (Animating Offset)</span></span> | ![Offset-Bewegung mit Federanimation](images/animation/offset-spring.gif) |

<span data-ttu-id="6441e-125">In jedem dieser Fälle kann die Federbewegung entweder durch „Auffedern“ und Schwingen um einen neuen Wert oder Schwingen um den aktuellen Wert mit einer Anfangsgeschwindigkeit ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="6441e-125">In each of these cases, the spring motion can be triggered either by "springing to" and oscillating around a new value or oscillating around its current value with some initial velocity.</span></span>

![Federanimation-Schwingung](images/animation/spring-animation-diagram.png)

## <a name="defining-your-spring-motion"></a><span data-ttu-id="6441e-127">Definition Ihrer Federbewegung</span><span class="sxs-lookup"><span data-stu-id="6441e-127">Defining your spring motion</span></span>

<span data-ttu-id="6441e-128">Mit den NaturalMotionAnimation-APIs schaffen Sie eine Federbewegung.</span><span class="sxs-lookup"><span data-stu-id="6441e-128">You create a spring experience by using the NaturalMotionAnimation APIs.</span></span> <span data-ttu-id="6441e-129">Insbesondere erstellen Sie eine SpringNaturalMotionAnimation mit den Create*-Methoden des Compositors.</span><span class="sxs-lookup"><span data-stu-id="6441e-129">Specifically, you create a SpringNaturalMotionAnimation by using the Create* methods off the Compositor.</span></span> <span data-ttu-id="6441e-130">Anschließend können Sie die folgenden Eigenschaften der Bewegung definieren:</span><span class="sxs-lookup"><span data-stu-id="6441e-130">You are then able to define the following properties of the motion:</span></span>

- <span data-ttu-id="6441e-131">DampingRatio – Gibt den Dämpfungsgrad der in der Animation verwendeten Federbewegung an.</span><span class="sxs-lookup"><span data-stu-id="6441e-131">DampingRatio – expresses the level of damping of the spring motion used in the animation.</span></span>

| <span data-ttu-id="6441e-132">Damping-Ratio-Wert</span><span class="sxs-lookup"><span data-stu-id="6441e-132">Damping Ratio Value</span></span> | <span data-ttu-id="6441e-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6441e-133">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="6441e-134">DampingRatio = 0</span><span class="sxs-lookup"><span data-stu-id="6441e-134">DampingRatio = 0</span></span> | <span data-ttu-id="6441e-135">Nicht gedämpft – Feder wird für längere Zeit schwingen</span><span class="sxs-lookup"><span data-stu-id="6441e-135">Undamped – the spring will oscillate for a long time</span></span> |
| <span data-ttu-id="6441e-136">0 < DampingRatio < 1</span><span class="sxs-lookup"><span data-stu-id="6441e-136">0 < DampingRatio < 1</span></span> | <span data-ttu-id="6441e-137">Wenig gedämpft – Feder wird von leicht zu viel schwingen</span><span class="sxs-lookup"><span data-stu-id="6441e-137">Underdamped – spring will oscillate from a little to a lot.</span></span> |
| <span data-ttu-id="6441e-138">DampingRatio = 1</span><span class="sxs-lookup"><span data-stu-id="6441e-138">DampingRatio = 1</span></span> | <span data-ttu-id="6441e-139">Criticallydamped – Feder führ keine Schwingung aus</span><span class="sxs-lookup"><span data-stu-id="6441e-139">Criticallydamped – the spring will perform no oscillation.</span></span> |
| <span data-ttu-id="6441e-140">DampingRation > 1</span><span class="sxs-lookup"><span data-stu-id="6441e-140">DampingRation > 1</span></span> | <span data-ttu-id="6441e-141">Stark gedämpft – Feder erreicht schnell ihr Ziel mit einer abrupten Verlangsamung und keine Schwingung</span><span class="sxs-lookup"><span data-stu-id="6441e-141">Overdamped – the spring will quickly reach its destination with an abrupt deceleration and no oscillation</span></span> |

- <span data-ttu-id="6441e-142">Period – Die Zeit zum Ausführen eines einzelnen Schwingungsvorgangs.</span><span class="sxs-lookup"><span data-stu-id="6441e-142">Period – the time it takes the spring to perform a single oscillation.</span></span>
- <span data-ttu-id="6441e-143">Final-/Starting-Wert – Definierte Start- und Endpositionen der Federbewegung (wenn nicht definiert, wird Startwert bzw. Endwert aktueller Wert sein).</span><span class="sxs-lookup"><span data-stu-id="6441e-143">Final / Starting Value – defined starting and ending positions of the spring motion (if not defined, starting value and/or final value will be current value).</span></span>
- <span data-ttu-id="6441e-144">Initial Velocity – Programmatische Anfangsgeschwindigkeit für die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="6441e-144">Initial Velocity – programmatic initial velocity for the motion.</span></span>

<span data-ttu-id="6441e-145">Sie können auch eine Reihe von Eigenschaften der Bewegung definieren, die mit KeyFrameAnimations identisch sind:</span><span class="sxs-lookup"><span data-stu-id="6441e-145">You can also define a set of properties of the motion that are the same as KeyFrameAnimations:</span></span>

- <span data-ttu-id="6441e-146">DelayTime/Delay Behavior</span><span class="sxs-lookup"><span data-stu-id="6441e-146">DelayTime / Delay Behavior</span></span>
- <span data-ttu-id="6441e-147">StopBehavior</span><span class="sxs-lookup"><span data-stu-id="6441e-147">StopBehavior</span></span>

<span data-ttu-id="6441e-148">In den üblichen Fällen, in denen Offset und Skalierung/Größe animiert werden, werden die folgenden Werte für DampingRatio und Period für verschiedene Federtypen vom Windows Design Team empfohlen:</span><span class="sxs-lookup"><span data-stu-id="6441e-148">In the common cases of animating Offset and Scale/Size, the following values are recommended by the Windows Design team for DampingRatio and Period for different types of springs:</span></span>

| <span data-ttu-id="6441e-149">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6441e-149">Property</span></span> | <span data-ttu-id="6441e-150">Normal Federung</span><span class="sxs-lookup"><span data-stu-id="6441e-150">Normal Spring</span></span> | <span data-ttu-id="6441e-151">Gedämpfte Federung</span><span class="sxs-lookup"><span data-stu-id="6441e-151">Dampened Spring</span></span> | <span data-ttu-id="6441e-152">Weniger gedämpfte Federung</span><span class="sxs-lookup"><span data-stu-id="6441e-152">Less-Dampened Spring</span></span> |
| -------- | ------------- | --------------- | -------------------- |
| <span data-ttu-id="6441e-153">Offset</span><span class="sxs-lookup"><span data-stu-id="6441e-153">Offset</span></span> | <span data-ttu-id="6441e-154">Damping Ratio = 0,8</span><span class="sxs-lookup"><span data-stu-id="6441e-154">Damping Ratio = 0.8</span></span> <br/> <span data-ttu-id="6441e-155">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-155">Period = 50 ms</span></span> | <span data-ttu-id="6441e-156">Damping Ratio = 0,85</span><span class="sxs-lookup"><span data-stu-id="6441e-156">Damping Ratio = 0.85</span></span> <br/> <span data-ttu-id="6441e-157">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-157">Period = 50 ms</span></span> | <span data-ttu-id="6441e-158">Damping Ratio = 0,65</span><span class="sxs-lookup"><span data-stu-id="6441e-158">Damping Ratio = 0.65</span></span> <br/> <span data-ttu-id="6441e-159">Period = 60 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-159">Period = 60 ms</span></span> |
| <span data-ttu-id="6441e-160">Skalierung/Größe</span><span class="sxs-lookup"><span data-stu-id="6441e-160">Scale/Size</span></span> | <span data-ttu-id="6441e-161">Damping Ratio = 0,7</span><span class="sxs-lookup"><span data-stu-id="6441e-161">Damping Ratio = 0.7</span></span> <br/> <span data-ttu-id="6441e-162">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-162">Period = 50 ms</span></span> | <span data-ttu-id="6441e-163">Damping Ratio = 0,8</span><span class="sxs-lookup"><span data-stu-id="6441e-163">Damping Ratio = 0.8</span></span> <br/> <span data-ttu-id="6441e-164">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-164">Period = 50 ms</span></span> | <span data-ttu-id="6441e-165">Damping Ratio = 0,6</span><span class="sxs-lookup"><span data-stu-id="6441e-165">Damping Ratio = 0.6</span></span> <br/> <span data-ttu-id="6441e-166">Period = 60 ms</span><span class="sxs-lookup"><span data-stu-id="6441e-166">Period = 60 ms</span></span> |

<span data-ttu-id="6441e-167">Nachdem Sie die Eigenschaften definiert haben, können Sie Ihre Feder-NaturalMotionAnimation an die Methode StartAnimation eines CompositionObjects oder die Motion-Eigenschaft eines InteractionTracker InertiaModifier übergeben.</span><span class="sxs-lookup"><span data-stu-id="6441e-167">Once you have defined the properties, you can then pass in your spring NaturalMotionAnimation into the StartAnimation method of a CompositionObject or the Motion property of an InteractionTracker InertiaModifier.</span></span>

## <a name="example"></a><span data-ttu-id="6441e-168">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6441e-168">Example</span></span>

<span data-ttu-id="6441e-169">In diesem Beispiel erstellen Sie eine Navigations- und Canvas-Benutzeroberfläche, in der ein Navigationsbereich durch Klicken auf eine Erweitern-Schaltfläche mit einer federnden Pendelbewegung animiert wird.</span><span class="sxs-lookup"><span data-stu-id="6441e-169">In this example, you create a navigation and canvas UI experience in which, when the user clicks an expand button, a navigation pane is animated out with a springy, oscillation motion.</span></span>

![Federanimation per Klick](images/animation/spring-animation-on-click.gif)

<span data-ttu-id="6441e-171">Definieren Sie zunächst die Federanimation innerhalb des angeklickten Ereignisses für das Erscheinen des Navigationsbereichs.</span><span class="sxs-lookup"><span data-stu-id="6441e-171">Start by defining the spring animation within the clicked event for when the navigation pane appears.</span></span> <span data-ttu-id="6441e-172">Anschließend definieren Sie die Eigenschaften der Animation, indem Sie die Funktion InitialValueExpression verwenden, um einen Ausdruck zur Definition des FinalValue zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6441e-172">You then define the properties of the animation, using the InitialValueExpression feature to use an Expression to define the FinalValue.</span></span> <span data-ttu-id="6441e-173">Sie können außerdem verfolgen, ob der Bereich geöffnet ist oder nicht und die Animation starten.</span><span class="sxs-lookup"><span data-stu-id="6441e-173">You also keep track of whether the pane is opened or not and, when ready, start the animation.</span></span>

```csharp
private void Button_Clicked(object sender, RoutedEventArgs e)
{
 _springAnimation = _compositor.CreateSpringScalarAnimation();
 _springAnimation.DampingRatio = 0.75f;
 _springAnimation.Period = TimeSpan.FromSeconds(0.5);

 if (!_expanded)
 {
 _expanded = true;
 _propSet.InsertBoolean("expanded", true);
 _springAnimation.InitialValueExpression[“FinalValue”] = “this.StartingValue + 250”;
 } else
 {
 _expanded = false;
 _propSet.InsertBoolean("expanded", false);
_springAnimation.InitialValueExpression[“FinalValue”] = “this.StartingValue - 250”;
 }
 _naviPane.StartAnimation("Offset.X", _springAnimation);
}
```

<span data-ttu-id="6441e-174">Was wäre, wenn Sie diese Eingabe mit der Bewegung verknüpfen wollten?</span><span class="sxs-lookup"><span data-stu-id="6441e-174">Now what if you wanted to tie this motion to input?</span></span> <span data-ttu-id="6441e-175">Wenn der Endbenutzer heraus wischt, soll eine Federbewegung erscheinen.</span><span class="sxs-lookup"><span data-stu-id="6441e-175">So if the end user swipes out, the panes come out with a Spring motion?</span></span> <span data-ttu-id="6441e-176">Noch wichtiger ist, wenn der Benutzer härter oder schneller wischt, passt sich die Bewegung an die Geschwindigkeit des Endbenutzers an.</span><span class="sxs-lookup"><span data-stu-id="6441e-176">More importantly, if the user swipes harder or faster, the motion adapts based on the velocity from the end user.</span></span>

![Federanimation beim Wischen](images/animation/spring-animation-on-swipe.gif)

<span data-ttu-id="6441e-178">Dazu können Sie die gleiche Federanimation nehmen und in einen InertiaModifier mit InteractionTracker übergeben.</span><span class="sxs-lookup"><span data-stu-id="6441e-178">To do this, you can take our same Spring Animation and pass it into an InertiaModifier with InteractionTracker.</span></span> <span data-ttu-id="6441e-179">Weitere Informationen zu InputAnimations und InteractionTracker finden Sie unter [Benutzerdefinierte Manipulationserfahrungen mit InteractionTracker](interaction-tracker-manipulations.md).</span><span class="sxs-lookup"><span data-stu-id="6441e-179">For more information about InputAnimations and InteractionTracker, see [Custom manipulation experiences with InteractionTracker](interaction-tracker-manipulations.md).</span></span> <span data-ttu-id="6441e-180">Wir gehen davon aus, dass Sie für dieses Codebeispiel bereits Ihren InteractionTracker und VisualInteractionSource eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="6441e-180">We’ll assume for this code example, you have already setup your InteractionTracker and VisualInteractionSource.</span></span> <span data-ttu-id="6441e-181">Wir konzentrieren uns auf die Entwicklung der InertiaModifier, die eine NaturalMotionAnimation, in diesem Fall eine Feder, aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="6441e-181">We’ll focus on creating the InertiaModifiers that will take in a NaturalMotionAnimation, in this case a spring.</span></span>

```csharp
// InteractionTracker and the VisualInteractionSource previously setup
// The open and close ScalarSpringAnimations defined earlier
private void SetupInput()
{
 // Define the InertiaModifier to manage the open motion
 var openMotionModifer = InteractionTrackerInertiaNaturalMotion.Create(compositor);

 // Condition defines to use open animation if panes in non-expanded view
 // Property set value to track if open or closed is managed in other part of code
 openMotionModifer.Condition = _compositor.CreateExpressionAnimation(
"propset.expanded == false");
 openMotionModifer.Condition.SetReferenceParameter("propSet", _propSet);
 openMotionModifer.NaturalMotion = _openSpringAnimation;

 // Define the InertiaModifer to manage the close motion
 var closeMotionModifier = InteractionTrackerInertiaNaturalMotion.Create(_compositor);

 // Condition defines to use close animation if panes in expanded view
 // Property set value to track if open or closed is managed in other part of code
 closeMotionModifier.Condition = 
_compositor.CreateExpressionAnimation("propSet.expanded == true");
 closeMotionModifier.Condition.SetReferenceParameter("propSet", _propSet);
 closeMotionModifier.NaturalMotion = _closeSpringAnimation;

 _tracker.ConfigurePositionXInertiaModifiers(new 
InteractionTrackerInertiaNaturalMotion[] { openMotionModifer, closeMotionModifier});

 // Take output of InteractionTracker and assign to the pane
 var exp = _compositor.CreateExpressionAnimation("-tracker.Position.X");
 exp.SetReferenceParameter("tracker", _tracker);
 ElementCompositionPreview.GetElementVisual(pageNavigation).
StartAnimation("Translation.X", exp);
}
```

<span data-ttu-id="6441e-182">Jetzt haben Sie sowohl eine programmatische als auch eine eingabegesteuerte Federanimation in Ihrer Benutzeroberfläche!</span><span class="sxs-lookup"><span data-stu-id="6441e-182">Now you have both a programmatic and input-driven spring animation in your UI!</span></span>

<span data-ttu-id="6441e-183">Zusammenfassend sehen die Schritte zur Verwendung von Federanimationen so aus:</span><span class="sxs-lookup"><span data-stu-id="6441e-183">In summary, the steps to using a spring animation in your app:</span></span>

1. <span data-ttu-id="6441e-184">Erstellen Sie Ihre SpringAnimation aus Ihrem Compositor.</span><span class="sxs-lookup"><span data-stu-id="6441e-184">Create your SpringAnimation off your Compositor.</span></span>
1. <span data-ttu-id="6441e-185">Definieren Sie Eigenschaften der SpringAnimation, wenn Sie nicht die Standardwerte wünschen:</span><span class="sxs-lookup"><span data-stu-id="6441e-185">Define properties of the SpringAnimation if you wanted non-default values:</span></span>
    - <span data-ttu-id="6441e-186">DampingRatio</span><span class="sxs-lookup"><span data-stu-id="6441e-186">DampingRatio</span></span>
    - <span data-ttu-id="6441e-187">Period</span><span class="sxs-lookup"><span data-stu-id="6441e-187">Period</span></span>
    - <span data-ttu-id="6441e-188">Final Value</span><span class="sxs-lookup"><span data-stu-id="6441e-188">Final Value</span></span>
    - <span data-ttu-id="6441e-189">Initial Value</span><span class="sxs-lookup"><span data-stu-id="6441e-189">Initial Value</span></span>
    - <span data-ttu-id="6441e-190">Initial Velocity</span><span class="sxs-lookup"><span data-stu-id="6441e-190">Initial Velocity</span></span>
1. <span data-ttu-id="6441e-191">Zum Ziel zuweisen.</span><span class="sxs-lookup"><span data-stu-id="6441e-191">Assign to target.</span></span>
    - <span data-ttu-id="6441e-192">Wenn Sie eine CompositionObject-Eigenschaft animieren, übergeben Sie SpringAnimation als Parameter an StartAnimation.</span><span class="sxs-lookup"><span data-stu-id="6441e-192">If you're animating a CompositionObject property, pass in SpringAnimation as parameter to StartAnimation.</span></span>
    - <span data-ttu-id="6441e-193">Wenn Sie mit Eingaben arbeiten wollen, setzen Sie die NaturalMotion-Eigenschaft eines InertiaModifier auf SpringAnimation.</span><span class="sxs-lookup"><span data-stu-id="6441e-193">If you want to use with input, set NaturalMotion property of an InertiaModifier to SpringAnimation.</span></span>

