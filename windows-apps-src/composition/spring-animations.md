---
title: Feder-Animationen
description: Lernen Sie, wie natürliche Spring-Bewegungsanimationen verwenden.
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 9e00aa383bcce17b7cd6b67514647c2f6137cc32
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8711188"
---
# <a name="spring-animations"></a><span data-ttu-id="0c214-104">Feder-Animationen</span><span class="sxs-lookup"><span data-stu-id="0c214-104">Spring animations</span></span>

<span data-ttu-id="0c214-105">Der Artikel zeigt, wie man Feder-NaturalMotionAnimations verwendet.</span><span class="sxs-lookup"><span data-stu-id="0c214-105">The article shows how to use spring NaturalMotionAnimations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c214-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0c214-106">Prerequisites</span></span>

<span data-ttu-id="0c214-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="0c214-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="0c214-108">Natürliche Bewegungsanimationen</span><span class="sxs-lookup"><span data-stu-id="0c214-108">Natural motion animations</span></span>](natural-animations.md)

## <a name="why-springs"></a><span data-ttu-id="0c214-109">Warum Federanimationen?</span><span class="sxs-lookup"><span data-stu-id="0c214-109">Why springs?</span></span>

<span data-ttu-id="0c214-110">Federanimationen sind ein allgemeines Bewegungserlebnis, das wir alle irgendwann einmal in unserem Leben erlebt haben; von Spielzeug bis hin zum Physikunterricht mit einem Federblock.</span><span class="sxs-lookup"><span data-stu-id="0c214-110">Springs are a common motion experience we've all experienced at some point in our lives; ranging from slinky toys to Physics classroom experiences with a spring-tied block.</span></span> <span data-ttu-id="0c214-111">Die oszillierende Bewegung einer Feder löst oft eine spielerische und heitere emotionale Reaktion der Betrachter aus.</span><span class="sxs-lookup"><span data-stu-id="0c214-111">The oscillating motion of a spring often incites a playful and lighthearted emotional response from those who observe it.</span></span> <span data-ttu-id="0c214-112">Das Ergebnis ist, dass die Bewegung einer Feder sich gut in eine Benutzeroberfläche für die Anwendung übersetzen lässt, die ein lebendigeres Bewegungserlebnis schaffen möchte, das dem Endbenutzer mehr überzeugt als eine traditionelle Cubic-Bezier-Animation.</span><span class="sxs-lookup"><span data-stu-id="0c214-112">As a result, the motion of a spring translates well into application UI for those who are looking to create a livelier motion experience that "pops" more to the end user than a traditional Cubic Bezier.</span></span> <span data-ttu-id="0c214-113">In diesen Fällen sorgt die Federbewegung nicht nur für ein lebendigeres Bewegungserlebnis, sondern kann auch die Aufmerksamkeit auf neue oder gerade animierte Inhalte lenken.</span><span class="sxs-lookup"><span data-stu-id="0c214-113">In these cases, spring motion not only creates a livelier motion experience, but also can help draw attention to new or currently animating content.</span></span> <span data-ttu-id="0c214-114">Je nach Anwendungs-Branding oder Bewegungssprache ist die Federbewegung ausgeprägter und sichtbarer und in anderen Fällen subtiler.</span><span class="sxs-lookup"><span data-stu-id="0c214-114">Depending on the application branding or motion language, the oscillation is more pronounced and visible, but in other cases it is more subtle.</span></span>

![<span data-ttu-id="0c214-115">Bewegung mit Federanimation](images/animation/offset-spring.gif)
![Bewegung mit Cubic-Bezier-Animation</span><span class="sxs-lookup"><span data-stu-id="0c214-115">Motion with spring animation](images/animation/offset-spring.gif)
![Motion with Cubic Bezier animation</span></span>](images/animation/offset-cubic-bezier.gif)

## <a name="using-springs-in-your-ui"></a><span data-ttu-id="0c214-116">Verwendung von Federbewegungen in Ihrem UI</span><span class="sxs-lookup"><span data-stu-id="0c214-116">Using springs in your UI</span></span>

<span data-ttu-id="0c214-117">Wie bereits erwähnt, können Federanimationen eine nützliche Bewegung sein, um sich in Ihre App zu integrieren und ein sehr vertrautes und spielerisches UI-Erlebnis einzuführen.</span><span class="sxs-lookup"><span data-stu-id="0c214-117">As mentioned previously, springs can be a useful motion to integrate into your app to introduce a very familiar and playful UI experience.</span></span> <span data-ttu-id="0c214-118">Übliche Verwendung von Federanimationen in UIs sind:</span><span class="sxs-lookup"><span data-stu-id="0c214-118">Common usage of springs in UI are:</span></span>

| <span data-ttu-id="0c214-119">Beschreibung der Verwendung der Federanimation</span><span class="sxs-lookup"><span data-stu-id="0c214-119">Spring Usage Description</span></span> | <span data-ttu-id="0c214-120">Visuelles Beispiel</span><span class="sxs-lookup"><span data-stu-id="0c214-120">Visual Example</span></span> |
| ------------------------ | -------------- |
| <span data-ttu-id="0c214-121">Eine Bewegungserfahrung „herausstechen“ und lebendiger aussehen lassen.</span><span class="sxs-lookup"><span data-stu-id="0c214-121">Making a motion experience "pop" and look livelier.</span></span> <span data-ttu-id="0c214-122">(Animating Scale)</span><span class="sxs-lookup"><span data-stu-id="0c214-122">(Animating Scale)</span></span> | ![Skalierungsbewegung mit Federanimation](images/animation/scale-spring.gif) |
| <span data-ttu-id="0c214-124">Eine Bewegungserfahrung subtil energetischer wirken lassen (Animating Offset)</span><span class="sxs-lookup"><span data-stu-id="0c214-124">Making a motion experience subtly feel more energetic (Animating Offset)</span></span> | ![Offset-Bewegung mit Federanimation](images/animation/offset-spring.gif) |

<span data-ttu-id="0c214-126">In jedem dieser Fälle kann die Federbewegung entweder durch „Auffedern“ und Schwingen um einen neuen Wert oder Schwingen um den aktuellen Wert mit einer Anfangsgeschwindigkeit ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="0c214-126">In each of these cases, the spring motion can be triggered either by "springing to" and oscillating around a new value or oscillating around its current value with some initial velocity.</span></span>

![Federanimation-Schwingung](images/animation/spring-animation-diagram.png)

## <a name="defining-your-spring-motion"></a><span data-ttu-id="0c214-128">Definition Ihrer Federbewegung</span><span class="sxs-lookup"><span data-stu-id="0c214-128">Defining your spring motion</span></span>

<span data-ttu-id="0c214-129">Mit den NaturalMotionAnimation-APIs schaffen Sie eine Federbewegung.</span><span class="sxs-lookup"><span data-stu-id="0c214-129">You create a spring experience by using the NaturalMotionAnimation APIs.</span></span> <span data-ttu-id="0c214-130">Insbesondere erstellen Sie eine SpringNaturalMotionAnimation mit den Create\*-Methoden des Compositors.</span><span class="sxs-lookup"><span data-stu-id="0c214-130">Specifically, you create a SpringNaturalMotionAnimation by using the Create\* methods off the Compositor.</span></span> <span data-ttu-id="0c214-131">Anschließend können Sie die folgenden Eigenschaften der Bewegung definieren:</span><span class="sxs-lookup"><span data-stu-id="0c214-131">You are then able to define the following properties of the motion:</span></span>

- <span data-ttu-id="0c214-132">DampingRatio – Gibt den Dämpfungsgrad der in der Animation verwendeten Federbewegung an.</span><span class="sxs-lookup"><span data-stu-id="0c214-132">DampingRatio – expresses the level of damping of the spring motion used in the animation.</span></span>

| <span data-ttu-id="0c214-133">Damping-Ratio-Wert</span><span class="sxs-lookup"><span data-stu-id="0c214-133">Damping Ratio Value</span></span> | <span data-ttu-id="0c214-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0c214-134">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="0c214-135">DampingRatio = 0</span><span class="sxs-lookup"><span data-stu-id="0c214-135">DampingRatio = 0</span></span> | <span data-ttu-id="0c214-136">Nicht gedämpft – Feder wird für längere Zeit schwingen</span><span class="sxs-lookup"><span data-stu-id="0c214-136">Undamped – the spring will oscillate for a long time</span></span> |
| <span data-ttu-id="0c214-137">0 < DampingRatio < 1</span><span class="sxs-lookup"><span data-stu-id="0c214-137">0 < DampingRatio < 1</span></span> | <span data-ttu-id="0c214-138">Wenig gedämpft – Feder wird von leicht zu viel schwingen</span><span class="sxs-lookup"><span data-stu-id="0c214-138">Underdamped – spring will oscillate from a little to a lot.</span></span> |
| <span data-ttu-id="0c214-139">DampingRatio = 1</span><span class="sxs-lookup"><span data-stu-id="0c214-139">DampingRatio = 1</span></span> | <span data-ttu-id="0c214-140">Criticallydamped – Feder führ keine Schwingung aus</span><span class="sxs-lookup"><span data-stu-id="0c214-140">Criticallydamped – the spring will perform no oscillation.</span></span> |
| <span data-ttu-id="0c214-141">DampingRation > 1</span><span class="sxs-lookup"><span data-stu-id="0c214-141">DampingRation > 1</span></span> | <span data-ttu-id="0c214-142">Stark gedämpft – Feder erreicht schnell ihr Ziel mit einer abrupten Verlangsamung und keine Schwingung</span><span class="sxs-lookup"><span data-stu-id="0c214-142">Overdamped – the spring will quickly reach its destination with an abrupt deceleration and no oscillation</span></span> |

- <span data-ttu-id="0c214-143">Period – Die Zeit zum Ausführen eines einzelnen Schwingungsvorgangs.</span><span class="sxs-lookup"><span data-stu-id="0c214-143">Period – the time it takes the spring to perform a single oscillation.</span></span>
- <span data-ttu-id="0c214-144">Final-/Starting-Wert – Definierte Start- und Endpositionen der Federbewegung (wenn nicht definiert, wird Startwert bzw. Endwert aktueller Wert sein).</span><span class="sxs-lookup"><span data-stu-id="0c214-144">Final / Starting Value – defined starting and ending positions of the spring motion (if not defined, starting value and/or final value will be current value).</span></span>
- <span data-ttu-id="0c214-145">Initial Velocity – Programmatische Anfangsgeschwindigkeit für die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="0c214-145">Initial Velocity – programmatic initial velocity for the motion.</span></span>

<span data-ttu-id="0c214-146">Sie können auch eine Reihe von Eigenschaften der Bewegung definieren, die mit KeyFrameAnimations identisch sind:</span><span class="sxs-lookup"><span data-stu-id="0c214-146">You can also define a set of properties of the motion that are the same as KeyFrameAnimations:</span></span>

- <span data-ttu-id="0c214-147">DelayTime/Delay Behavior</span><span class="sxs-lookup"><span data-stu-id="0c214-147">DelayTime / Delay Behavior</span></span>
- <span data-ttu-id="0c214-148">StopBehavior</span><span class="sxs-lookup"><span data-stu-id="0c214-148">StopBehavior</span></span>

<span data-ttu-id="0c214-149">In den üblichen Fällen, in denen Offset und Skalierung/Größe animiert werden, werden die folgenden Werte für DampingRatio und Period für verschiedene Federtypen vom Windows Design Team empfohlen:</span><span class="sxs-lookup"><span data-stu-id="0c214-149">In the common cases of animating Offset and Scale/Size, the following values are recommended by the Windows Design team for DampingRatio and Period for different types of springs:</span></span>

| <span data-ttu-id="0c214-150">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0c214-150">Property</span></span> | <span data-ttu-id="0c214-151">Normal Federung</span><span class="sxs-lookup"><span data-stu-id="0c214-151">Normal Spring</span></span> | <span data-ttu-id="0c214-152">Gedämpfte Federung</span><span class="sxs-lookup"><span data-stu-id="0c214-152">Dampened Spring</span></span> | <span data-ttu-id="0c214-153">Weniger gedämpfte Federung</span><span class="sxs-lookup"><span data-stu-id="0c214-153">Less-Dampened Spring</span></span> |
| -------- | ------------- | --------------- | -------------------- |
| <span data-ttu-id="0c214-154">Offset</span><span class="sxs-lookup"><span data-stu-id="0c214-154">Offset</span></span> | <span data-ttu-id="0c214-155">Damping Ratio = 0,8</span><span class="sxs-lookup"><span data-stu-id="0c214-155">Damping Ratio = 0.8</span></span> <br/> <span data-ttu-id="0c214-156">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-156">Period = 50 ms</span></span> | <span data-ttu-id="0c214-157">Damping Ratio = 0,85</span><span class="sxs-lookup"><span data-stu-id="0c214-157">Damping Ratio = 0.85</span></span> <br/> <span data-ttu-id="0c214-158">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-158">Period = 50 ms</span></span> | <span data-ttu-id="0c214-159">Damping Ratio = 0,65</span><span class="sxs-lookup"><span data-stu-id="0c214-159">Damping Ratio = 0.65</span></span> <br/> <span data-ttu-id="0c214-160">Period = 60 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-160">Period = 60 ms</span></span> |
| <span data-ttu-id="0c214-161">Skalierung/Größe</span><span class="sxs-lookup"><span data-stu-id="0c214-161">Scale/Size</span></span> | <span data-ttu-id="0c214-162">Damping Ratio = 0,7</span><span class="sxs-lookup"><span data-stu-id="0c214-162">Damping Ratio = 0.7</span></span> <br/> <span data-ttu-id="0c214-163">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-163">Period = 50 ms</span></span> | <span data-ttu-id="0c214-164">Damping Ratio = 0,8</span><span class="sxs-lookup"><span data-stu-id="0c214-164">Damping Ratio = 0.8</span></span> <br/> <span data-ttu-id="0c214-165">Period = 50 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-165">Period = 50 ms</span></span> | <span data-ttu-id="0c214-166">Damping Ratio = 0,6</span><span class="sxs-lookup"><span data-stu-id="0c214-166">Damping Ratio = 0.6</span></span> <br/> <span data-ttu-id="0c214-167">Period = 60 ms</span><span class="sxs-lookup"><span data-stu-id="0c214-167">Period = 60 ms</span></span> |

<span data-ttu-id="0c214-168">Nachdem Sie die Eigenschaften definiert haben, können Sie Ihre Feder-NaturalMotionAnimation an die Methode StartAnimation eines CompositionObjects oder die Motion-Eigenschaft eines InteractionTracker InertiaModifier übergeben.</span><span class="sxs-lookup"><span data-stu-id="0c214-168">Once you have defined the properties, you can then pass in your spring NaturalMotionAnimation into the StartAnimation method of a CompositionObject or the Motion property of an InteractionTracker InertiaModifier.</span></span>

## <a name="example"></a><span data-ttu-id="0c214-169">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0c214-169">Example</span></span>

<span data-ttu-id="0c214-170">In diesem Beispiel erstellen Sie eine Navigations- und Canvas-Benutzeroberfläche, in der ein Navigationsbereich durch Klicken auf eine Erweitern-Schaltfläche mit einer federnden Pendelbewegung animiert wird.</span><span class="sxs-lookup"><span data-stu-id="0c214-170">In this example, you create a navigation and canvas UI experience in which, when the user clicks an expand button, a navigation pane is animated out with a springy, oscillation motion.</span></span>

![Federanimation per Klick](images/animation/spring-animation-on-click.gif)

<span data-ttu-id="0c214-172">Definieren Sie zunächst die Federanimation innerhalb des angeklickten Ereignisses für das Erscheinen des Navigationsbereichs.</span><span class="sxs-lookup"><span data-stu-id="0c214-172">Start by defining the spring animation within the clicked event for when the navigation pane appears.</span></span> <span data-ttu-id="0c214-173">Anschließend definieren Sie die Eigenschaften der Animation, indem Sie die Funktion InitialValueExpression verwenden, um einen Ausdruck zur Definition des FinalValue zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0c214-173">You then define the properties of the animation, using the InitialValueExpression feature to use an Expression to define the FinalValue.</span></span> <span data-ttu-id="0c214-174">Sie können außerdem verfolgen, ob der Bereich geöffnet ist oder nicht und die Animation starten.</span><span class="sxs-lookup"><span data-stu-id="0c214-174">You also keep track of whether the pane is opened or not and, when ready, start the animation.</span></span>

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

<span data-ttu-id="0c214-175">Was wäre, wenn Sie diese Eingabe mit der Bewegung verknüpfen wollten?</span><span class="sxs-lookup"><span data-stu-id="0c214-175">Now what if you wanted to tie this motion to input?</span></span> <span data-ttu-id="0c214-176">Wenn der Endbenutzer heraus wischt, soll eine Federbewegung erscheinen.</span><span class="sxs-lookup"><span data-stu-id="0c214-176">So if the end user swipes out, the panes come out with a Spring motion?</span></span> <span data-ttu-id="0c214-177">Noch wichtiger ist, wenn der Benutzer härter oder schneller wischt, passt sich die Bewegung an die Geschwindigkeit des Endbenutzers an.</span><span class="sxs-lookup"><span data-stu-id="0c214-177">More importantly, if the user swipes harder or faster, the motion adapts based on the velocity from the end user.</span></span>

![Federanimation beim Wischen](images/animation/spring-animation-on-swipe.gif)

<span data-ttu-id="0c214-179">Dazu können Sie die gleiche Federanimation nehmen und in einen InertiaModifier mit InteractionTracker übergeben.</span><span class="sxs-lookup"><span data-stu-id="0c214-179">To do this, you can take our same Spring Animation and pass it into an InertiaModifier with InteractionTracker.</span></span> <span data-ttu-id="0c214-180">Weitere Informationen zu InputAnimations und InteractionTracker finden Sie unter [Benutzerdefinierte Manipulationserfahrungen mit InteractionTracker](interaction-tracker-manipulations.md).</span><span class="sxs-lookup"><span data-stu-id="0c214-180">For more information about InputAnimations and InteractionTracker, see [Custom manipulation experiences with InteractionTracker](interaction-tracker-manipulations.md).</span></span> <span data-ttu-id="0c214-181">Wir gehen davon aus, dass Sie für dieses Codebeispiel bereits Ihren InteractionTracker und VisualInteractionSource eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="0c214-181">We’ll assume for this code example, you have already setup your InteractionTracker and VisualInteractionSource.</span></span> <span data-ttu-id="0c214-182">Wir konzentrieren uns auf die Entwicklung der InertiaModifier, die eine NaturalMotionAnimation, in diesem Fall eine Feder, aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="0c214-182">We’ll focus on creating the InertiaModifiers that will take in a NaturalMotionAnimation, in this case a spring.</span></span>

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

<span data-ttu-id="0c214-183">Jetzt haben Sie sowohl eine programmatische als auch eine eingabegesteuerte Federanimation in Ihrer Benutzeroberfläche!</span><span class="sxs-lookup"><span data-stu-id="0c214-183">Now you have both a programmatic and input-driven spring animation in your UI!</span></span>

<span data-ttu-id="0c214-184">Zusammenfassend sehen die Schritte zur Verwendung von Federanimationen so aus:</span><span class="sxs-lookup"><span data-stu-id="0c214-184">In summary, the steps to using a spring animation in your app:</span></span>

1. <span data-ttu-id="0c214-185">Erstellen Sie Ihre SpringAnimation aus Ihrem Compositor.</span><span class="sxs-lookup"><span data-stu-id="0c214-185">Create your SpringAnimation off your Compositor.</span></span>
1. <span data-ttu-id="0c214-186">Definieren Sie Eigenschaften der SpringAnimation, wenn Sie nicht die Standardwerte wünschen:</span><span class="sxs-lookup"><span data-stu-id="0c214-186">Define properties of the SpringAnimation if you wanted non-default values:</span></span>
    - <span data-ttu-id="0c214-187">DampingRatio</span><span class="sxs-lookup"><span data-stu-id="0c214-187">DampingRatio</span></span>
    - <span data-ttu-id="0c214-188">Period</span><span class="sxs-lookup"><span data-stu-id="0c214-188">Period</span></span>
    - <span data-ttu-id="0c214-189">Final Value</span><span class="sxs-lookup"><span data-stu-id="0c214-189">Final Value</span></span>
    - <span data-ttu-id="0c214-190">Initial Value</span><span class="sxs-lookup"><span data-stu-id="0c214-190">Initial Value</span></span>
    - <span data-ttu-id="0c214-191">Initial Velocity</span><span class="sxs-lookup"><span data-stu-id="0c214-191">Initial Velocity</span></span>
1. <span data-ttu-id="0c214-192">Zum Ziel zuweisen.</span><span class="sxs-lookup"><span data-stu-id="0c214-192">Assign to target.</span></span>
    - <span data-ttu-id="0c214-193">Wenn Sie eine CompositionObject-Eigenschaft animieren, übergeben Sie SpringAnimation als Parameter an StartAnimation.</span><span class="sxs-lookup"><span data-stu-id="0c214-193">If you're animating a CompositionObject property, pass in SpringAnimation as parameter to StartAnimation.</span></span>
    - <span data-ttu-id="0c214-194">Wenn Sie mit Eingaben arbeiten wollen, setzen Sie die NaturalMotion-Eigenschaft eines InertiaModifier auf SpringAnimation.</span><span class="sxs-lookup"><span data-stu-id="0c214-194">If you want to use with input, set NaturalMotion property of an InertiaModifier to SpringAnimation.</span></span>

