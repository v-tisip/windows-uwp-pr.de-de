---
author: jwmsft
title: Relationsbasierte Animationen
description: Erstellen sie Bewegungen auf Basis einer Eigenschaft eines anderen Objekts.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: cde3868d1a554396bfda7c13ea0c71bd037416bc
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5748353"
---
# <a name="relation-based-animations"></a><span data-ttu-id="9dbaa-104">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="9dbaa-104">Relation based animations</span></span>

<span data-ttu-id="9dbaa-105">Dieser Artikel gibt einen kurzen Überblick darüber, wie man relationsbasierte Animationen mit Composition-ExpressionAnimations erstellt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-105">This article provides a brief overview of how to make relation-based animations using Composition ExpressionAnimations.</span></span>

## <a name="dynamic-relation-based-experiences"></a><span data-ttu-id="9dbaa-106">Erfahrungen auf Basis dynamischer Beziehungen</span><span class="sxs-lookup"><span data-stu-id="9dbaa-106">Dynamic Relation-based Experiences</span></span>

<span data-ttu-id="9dbaa-107">Beim Erstellen von Bewegungserlebnissen in einer App gibt es Zeiten, in denen die Bewegung nicht zeitabhängig, sondern von einer Eigenschaft eines anderen Objekts abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-107">When building out motion experiences in an app, there are times when the motion is not time-based, but rather dependent on a property on another object.</span></span> <span data-ttu-id="9dbaa-108">KeyFrameAnimations sind nicht besonders gut in der Lage, diese Art von Bewegungserlebnissen auszudrücken.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-108">KeyFrameAnimations are not able to express these types of motion experiences very easily.</span></span> <span data-ttu-id="9dbaa-109">In diesen speziellen Fällen muss die Bewegung nicht mehr diskret und vordefiniert sein.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-109">In these specific instances, motion no longer needs to be discrete and pre-defined.</span></span> <span data-ttu-id="9dbaa-110">Stattdessen kann sich die Bewegung dynamisch aufgrund ihrer Beziehung zu anderen Objekteigenschaften anpassen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-110">Instead, the motion can dynamically adapt based on its relationship to other object properties.</span></span> <span data-ttu-id="9dbaa-111">Beispielsweise können Sie die Deckkraft eines Objekts anhand seiner horizontalen Position animieren.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-111">For example, you can animate the opacity of an object based on its horizontal position.</span></span> <span data-ttu-id="9dbaa-112">Andere Beispiele sind Bewegungserlebnisse wie Sticky Header und Parallax.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-112">Other examples include motion experiences like Sticky Headers and Parallax.</span></span>

<span data-ttu-id="9dbaa-113">Diese Art von Bewegungserlebnissen ermöglicht es Ihnen, eine Benutzeroberfläche zu schaffen, die sich verbundener anstatt eigenständig und unabhängig anfühlt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-113">These types of motion experiences let you create UI that feels more connected, instead of feeling singular and independent.</span></span> <span data-ttu-id="9dbaa-114">Benutzern vermittelt dies den Eindruck eines dynamischen UI-Erlebnisses.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-114">To the user, this gives the impression of a dynamic UI experience.</span></span>

![Um Kreis umlaufend](images/animation/orbit.gif)

![Listenansicht mit Parallax](images/animation/parallax.gif)

## <a name="using-expressionanimations"></a><span data-ttu-id="9dbaa-117">Verwenden von ExpressionAnimations</span><span class="sxs-lookup"><span data-stu-id="9dbaa-117">Using ExpressionAnimations</span></span>

<span data-ttu-id="9dbaa-118">Um relationsbasierte Bewegungserlebnisse zu erstellen, verwenden Sie den Typ ExpressionAnimation.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-118">To create relation-based motion experiences, you use the ExpressionAnimation type.</span></span> <span data-ttu-id="9dbaa-119">ExpressionAnimations (oder kurz Expressions/Ausdrücke), ist eine neue Art der Animation, die es Ihnen erlaubt, eine mathematische Beziehung auszudrücken – eine Beziehung, die das System verwendet, um den Wert einer animierenden Eigenschaft jedes Frame zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-119">ExpressionAnimations (or Expressions for short), are a new type of animation that let you express a mathematical relationship – a relationship that the system uses to calculate the value of an animating property every frame.</span></span> <span data-ttu-id="9dbaa-120">Anders ausgedrückt: Ausdrücke sind einfach eine mathematische Gleichung, die den gewünschten Wert einer Animationseigenschaft pro Frame definiert.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-120">Put another way, Expressions are simply a mathematical equation that defines the desired value of an animating property per frame.</span></span> <span data-ttu-id="9dbaa-121">Ausdrücke sind eine sehr vielseitige Komponente, die in einer Vielzahl von Szenarien verwendet werden kann, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-121">Expressions are a very versatile component that can be used across a wide variety of scenarios, including:</span></span>

- <span data-ttu-id="9dbaa-122">Relative Größe, Offset-Animationen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-122">Relative Size, Offset animations.</span></span>
- <span data-ttu-id="9dbaa-123">Sticky Header, Parallax mit ScrollViewer.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-123">Sticky Headers, Parallax with ScrollViewer.</span></span> <span data-ttu-id="9dbaa-124">(Siehe [Erweitern vorhandener ScrollViewer-Erfahrungen](scroll-input-animations.md).)</span><span class="sxs-lookup"><span data-stu-id="9dbaa-124">(See [Enhance existing ScrollViewer experiences](scroll-input-animations.md).)</span></span>
- <span data-ttu-id="9dbaa-125">Andockpunkte mit InertiaModifiers und InteractionTracker.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-125">Snap Points with InertiaModifiers and InteractionTracker.</span></span> <span data-ttu-id="9dbaa-126">(Siehe [Erstellen von Andockpunkten mit Inertia-Modifiern](inertia-modifiers.md).)</span><span class="sxs-lookup"><span data-stu-id="9dbaa-126">(See [Create snap points with inertia modifiers](inertia-modifiers.md).)</span></span>

<span data-ttu-id="9dbaa-127">Bei der Arbeit mit ExpressionAnimations gibt es ein paar Dinge, die im Vorfeld erwähnenswert sind:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-127">When working with ExpressionAnimations, there are a couple of things worth mentioning up front:</span></span>

- <span data-ttu-id="9dbaa-128">Keine Beendigung – Im Gegensatz zu KeyFrameAnimation haben Ausdrücke keine endliche Dauer.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-128">Never Ending – unlike its KeyFrameAnimation sibling, Expressions don’t have a finite duration.</span></span> <span data-ttu-id="9dbaa-129">Da Ausdrücke mathematische Beziehungen sind, sind sie Animationen, die ständig „ablaufen“.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-129">Because Expressions are mathematical relationships, they are animations that are constantly "running".</span></span> <span data-ttu-id="9dbaa-130">Sie haben die Möglichkeit, diese Animationen zu stoppen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-130">You have the option to stop these animations if you choose.</span></span>
- <span data-ttu-id="9dbaa-131">Ausführung ohne ständige Auswertung – Leistung ist immer ein Anliegen bei ständig laufenden Animationen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-131">Running, but not always evaluating – performance is always a concern with animations that are constantly running.</span></span> <span data-ttu-id="9dbaa-132">Das System ist so intelligent, dass der Ausdruck nur dann neu bewertet wird, wenn sich irgendwelche Eingaben oder Parameter geändert haben.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-132">No need to worry though, the system is smart enough that the Expression will only re-evaluate if any of its inputs or parameters have changed.</span></span>
- <span data-ttu-id="9dbaa-133">Auflösen in den richtigen Objekttyp – Da Ausdrücke mathematische Beziehungen sind, ist es wichtig sicherzustellen, dass die Gleichung, die der Ausdruck definiert, in den Eigenschaftstyp aufgelöst wird, auf die die Animation abzielt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-133">Resolving to the right object type – Because Expressions are mathematical relationships, it is important to make sure that the equation that defines the Expression resolves to the same type of the property being targeted by the animation.</span></span> <span data-ttu-id="9dbaa-134">Wenn Sie beispielsweise Offset animieren, sollte Ihr Ausdruck in einen Vector3-Typ aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-134">For example, if animating Offset, your Expression should resolve to a Vector3 type.</span></span>

### <a name="components-of-an-expression"></a><span data-ttu-id="9dbaa-135">Bestandteile eines Ausdrucks</span><span class="sxs-lookup"><span data-stu-id="9dbaa-135">Components of an Expression</span></span>

<span data-ttu-id="9dbaa-136">Beim Aufbau der mathematischen Beziehung eines Ausdrucks gibt es mehrere Kernkomponenten:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-136">When building the mathematical relationship of an Expression, there are several core components:</span></span>

- <span data-ttu-id="9dbaa-137">Parameter – Werte, die konstante Werte darstellen oder Verweise auf andere Composition-Objekte.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-137">Parameters – values representing constant values or references to other Composition objects.</span></span>
- <span data-ttu-id="9dbaa-138">Mathematische Operatoren – Die typischen mathematischen Operatoren plus (+), minus (-), multiplizieren (\*), dividieren (/), die Parameter zu einer Gleichung zusammenfügen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-138">Mathematical Operators – the typical mathematical operators plus(+), minus(-), multiply(\*), divide(/) that join together parameters to form an equation.</span></span> <span data-ttu-id="9dbaa-139">Ebenfalls enthalten sind bedingte Operatoren wie Größer als (>), Gleich (==), ternärer Operator (Bedingung ?</span><span class="sxs-lookup"><span data-stu-id="9dbaa-139">Also included are conditional operators such as greater than(>), equal(==), ternary operator (condition ?</span></span> <span data-ttu-id="9dbaa-140">ifTrue : ifFalse) etc.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-140">ifTrue : ifFalse), etc.</span></span>
- <span data-ttu-id="9dbaa-141">Mathematische Funktionen – Mathematische Funktionen/Verknüpfungen basierend auf System.Numerik.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-141">Mathematical Functions – mathematical functions/shortcuts based on System.Numerics.</span></span> <span data-ttu-id="9dbaa-142">Eine vollständige Liste der unterstützten Funktionen finden Sie unter [ExpressionAnimation](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.ExpressionAnimation).</span><span class="sxs-lookup"><span data-stu-id="9dbaa-142">For a full list of supported functions, see [ExpressionAnimation](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.ExpressionAnimation).</span></span>

<span data-ttu-id="9dbaa-143">Ausdrücke unterstützen eine Reihe von Schlüsselwörtern – Spezielle Begriffe, die nur innerhalb des ExpressionAnimation-Systems eine eindeutige Bedeutung haben.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-143">Expressions also support a set of keywords – special phrases that have distinct meaning only within the ExpressionAnimation system.</span></span> <span data-ttu-id="9dbaa-144">Diese sind (zusammen mit der vollständigen Liste der mathematischen Funktionen) in der [ExpressionAnimation](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.ExpressionAnimation)-Dokumentation aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-144">These are listed (along with the full list of math functions) in the [ExpressionAnimation](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.ExpressionAnimation) documentation.</span></span>

### <a name="creating-expressions-with-expressionbuilder"></a><span data-ttu-id="9dbaa-145">Erstellen von Ausdrücken mit ExpressionBuilder</span><span class="sxs-lookup"><span data-stu-id="9dbaa-145">Creating Expressions with ExpressionBuilder</span></span>

<span data-ttu-id="9dbaa-146">Es gibt zwei Möglichkeiten, Expressions in der UWP-Apps zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-146">There are two options for building Expressions in their UWP app:</span></span>

1. <span data-ttu-id="9dbaa-147">Erstellen der Gleichung als Zeichenkette über die offizielle, öffentliche API.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-147">Building the equation as a string via the official, public API.</span></span>
1. <span data-ttu-id="9dbaa-148">Erstellen der Gleichung in einem typsicheren Objektmodell mit Hilfe des Open Source ExpressionBuilder-Tools.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-148">Building the equation in a type-safe object model via the open source ExpressionBuilder tool.</span></span> <span data-ttu-id="9dbaa-149">Siehe [Github-Quellcode und Dokumentation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/ExpressionBuilder).</span><span class="sxs-lookup"><span data-stu-id="9dbaa-149">See the [Github source and documentation](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/ExpressionBuilder).</span></span>

<span data-ttu-id="9dbaa-150">In diesem Dokument werden wir unsere Ausdrücke mit Hilfe von ExpressionBuilder definieren.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-150">For the sake of this document, we will define our Expressions using ExpressionBuilder.</span></span>

### <a name="parameters"></a><span data-ttu-id="9dbaa-151">Parameter</span><span class="sxs-lookup"><span data-stu-id="9dbaa-151">Parameters</span></span>

<span data-ttu-id="9dbaa-152">Parameter bilden das Kernstück eines Ausdrucks.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-152">Parameters make up the core of an Expression.</span></span> <span data-ttu-id="9dbaa-153">Zwei Parametertypen stehen zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-153">There are two types of parameters:</span></span>

- <span data-ttu-id="9dbaa-154">Konstanten: Dies sind Parameter, die System.Numeric-Variablen repräsentieren.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-154">Constants: these are parameters representing typed System.Numeric variables.</span></span> <span data-ttu-id="9dbaa-155">Diese Parameter werden beim Start der Animation einmalig mit Werten belegt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-155">These parameters get their values assigned once when the animation is started.</span></span>
- <span data-ttu-id="9dbaa-156">Referenzen: Dies sind Parameter, die Verweise auf CompositionObjects darstellen – diese Parameter werden nach dem Start einer Animation fortlaufend aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-156">References: these are parameters representing references to CompositionObjects – these parameters continuously get their values updated after an animation is started.</span></span>

<span data-ttu-id="9dbaa-157">Im Allgemeinen sind Referenzen dafür verantwortlich, wie sich die Ausgabe eines Ausdrucks dynamisch ändern kann.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-157">In general, References are the main aspect for how an Expression’s output can dynamically change.</span></span> <span data-ttu-id="9dbaa-158">Wenn sich diese Referenzen ändern, ändert sich dadurch die Ausgabe des Ausdrucks.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-158">As these references change, the output of the Expression changes as a result.</span></span> <span data-ttu-id="9dbaa-159">Wenn Sie Ihren Ausdruck mit Zeichenfolgen erstellen oder in einem Templating-Szenario verwenden (mit Ihrem Ausdruck für mehrere CompositionObjects), müssen Sie die Werte Ihrer Parameter benennen und festlegen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-159">If you create your Expression with Strings or use them in a templating scenario (using your Expression to target multiple CompositionObjects), you will need to name and set the values of your parameters.</span></span> <span data-ttu-id="9dbaa-160">Weitere Informationen finden Sie im Abschnitt „Beispiel“.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-160">See the Example section for more info.</span></span>

### <a name="working-with-keyframeanimations"></a><span data-ttu-id="9dbaa-161">Arbeiten mit KeyFrameAnimations</span><span class="sxs-lookup"><span data-stu-id="9dbaa-161">Working with KeyFrameAnimations</span></span>

<span data-ttu-id="9dbaa-162">Ausdrücke können auch mit KeyFrameAnimations verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-162">Expressions can also be used with KeyFrameAnimations.</span></span> <span data-ttu-id="9dbaa-163">In diesen Fällen möchten Sie einen Ausdruck verwenden, um den Wert eines KeyFrames zu einem bestimmten Zeitpunkt zu definieren – diese KeyFrame-Typen werden als ExpressionKeyFrames bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-163">In these instances, you want to use an Expression to define the value of a KeyFrame at a time spot – these types KeyFrames are called ExpressionKeyFrames.</span></span>

```csharp
KeyFrameAnimation.InsertExpressionKeyFrame(Single, String)
KeyFrameAnimation.InsertExpressionKeyFrame(Single, ExpressionNode)
```

<span data-ttu-id="9dbaa-164">Im Gegensatz zu ExpressionAnimations werden ExpressionKeyFrames jedoch nur einmalig beim Start der KeyFrameAnimation ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-164">However, unlike ExpressionAnimations, ExpressionKeyFrames are evaluated only once when the KeyFrameAnimation is started.</span></span> <span data-ttu-id="9dbaa-165">Beachten Sie, dass Sie in einer ExpressionAnimation nicht den Wert des KeyFrame übergeben, sondern eine Zeichenfolge (oder einen ExpressionNode, wenn Sie ExpressionBuilder verwenden).</span><span class="sxs-lookup"><span data-stu-id="9dbaa-165">Keep in mind, you do not pass in an ExpressionAnimation as the value of the KeyFrame, rather a string (or an ExpressionNode, if you're using ExpressionBuilder).</span></span>

## <a name="example"></a><span data-ttu-id="9dbaa-166">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9dbaa-166">Example</span></span>

<span data-ttu-id="9dbaa-167">Gehen wir nun ein Beispiel für die Verwendung von Ausdrücken durch. Es handelt sich um das PropertySet-Beispiel aus der Windows UI-Beispielgalerie.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-167">Let's now walk through an example of using Expressions, specifically the PropertySet sample from the Windows UI Sample Gallery.</span></span> <span data-ttu-id="9dbaa-168">Wir betrachten den Ausdruck, der das Orbit-Bewegungsverhalten der blauen Kugel steuert.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-168">We'll look at the Expression managing the orbit motion behavior of the blue ball.</span></span>

![Um Kreis umlaufend](images/animation/orbit.gif)

<span data-ttu-id="9dbaa-170">Für die Gesamterfahrung spielen drei Komponenten eine Rolle:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-170">There are three components at play for the total experience:</span></span>

1. <span data-ttu-id="9dbaa-171">Eine KeyFrameAnimation, die den Y-Offset des roten Balls animiert.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-171">A KeyFrameAnimation, animating the Y Offset of the red ball.</span></span>
1. <span data-ttu-id="9dbaa-172">Ein PropertySet mit einer **Rotation**-Eigenschaft, die den Orbit steuert, animiert durch eine andere KeyFrameAnimation.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-172">A PropertySet with a **Rotation** property that helps drives the orbit, animated by another KeyFrameAnimation.</span></span>
1. <span data-ttu-id="9dbaa-173">Eine ExpressionAnimation, die den Offset der blauen Kugel mit Bezug auf den Offset der roten Kugel und die Rotation-Eigenschaft steuert, um eine perfekte Umlaufbahn aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-173">An ExpressionAnimation that drives the Offset of the blue ball referencing the Red Ball Offset and the Rotation property to maintain a perfect orbit.</span></span>

<span data-ttu-id="9dbaa-174">Wir konzentrieren uns auf die in Schritt 3 definierte ExpressionAnimation.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-174">We’ll be focusing on the ExpressionAnimation defined in #3.</span></span> <span data-ttu-id="9dbaa-175">Wir werden auch die ExpressionBuilder-Klassen verwenden, um diesen Ausdruck zu konstruieren.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-175">We will also be using the ExpressionBuilder classes to construct this Expression.</span></span> <span data-ttu-id="9dbaa-176">Eine Kopie des Codes, der verwendet wird, um dieses Erlebnis über Zeichenfolgen zu erzeugen, ist am Ende zu finden.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-176">A copy of the code used to build this experience via Strings is listed at the end.</span></span>

<span data-ttu-id="9dbaa-177">In dieser Gleichung gibt es zwei Eigenschaften, die Sie aus dem PropertySet referenzieren müssen: die eine ist ein Mittelpunktversatz und die andere die Rotation.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-177">In this equation, there are two properties you need to reference from the PropertySet; one is a centerpoint offset and the other is the rotation.</span></span>

```
var propSetCenterPoint =
_propertySet.GetReference().GetVector3Property("CenterPointOffset");

// This rotation value will animate via KFA from 0 -> 360 degrees
var propSetRotation = _propertySet.GetReference().GetScalarProperty("Rotation");
```

<span data-ttu-id="9dbaa-178">Als nächstes müssen Sie die Vector3-Komponente definieren, die die tatsächliche Rotation der Umlaufbahn berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-178">Next, you need to define the Vector3 component that accounts for the actual orbiting rotation.</span></span>

```
var orbitRotation = EF.Vector3(
    EF.Cos(EF.ToRadians(propSetRotation)) * 150,
    EF.Sin(EF.ToRadians(propSetRotation)) * 75, 0);
```

> [!NOTE]
> `EF` <span data-ttu-id="9dbaa-179">ist eine Abkürzung für die „using“-Notation zur Definition von ExpressionBuilder.ExpressionFunctions.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-179">is a shorthand “using” notation to define ExpressionBuilder.ExpressionFunctions.</span></span>

<span data-ttu-id="9dbaa-180">Schließlich kombinieren Sie diese Komponenten und referenzieren die Position der roten Kugel, um die mathematische Beziehung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-180">Finally, combine these components together and reference the position of the Red Ball to define the mathematical relationship.</span></span>

```
var orbitExpression = redSprite.GetReference().Offset + propSetCenterPoint + orbitRotation;
blueSprite.StartAnimation("Offset", orbitExpression);
```

<span data-ttu-id="9dbaa-181">Was wäre, wenn Sie denselben Ausdruck verwenden wollten, aber mit zwei anderen Visuals 2 Sätze von kreisenden Kugel verwenden möchten?</span><span class="sxs-lookup"><span data-stu-id="9dbaa-181">In a hypothetical situation, what if you wanted to use this same Expression but with two other Visuals, meaning 2 sets of orbiting circles.</span></span> <span data-ttu-id="9dbaa-182">Mit CompositionAnimations können Sie die Animation wiederverwenden und mehrere CompositionObjects als Zielobjekt auswählen.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-182">With CompositionAnimations, you can re-use the animation and target multiple CompositionObjects.</span></span> <span data-ttu-id="9dbaa-183">Das einzige, was Sie ändern müssen, wenn Sie diesen Ausdruck für den zusätzlichen Orbit verwenden, ist der Verweis auf das Visual.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-183">The only thing you need to change when you use this Expression for the additional orbit case is the reference to the Visual.</span></span> <span data-ttu-id="9dbaa-184">Wir nennen das „Templating“.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-184">We call this templating.</span></span>

<span data-ttu-id="9dbaa-185">In diesem Fall modifizieren Sie den zuvor erstellten Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-185">In this case, you modify the Expression you built earlier.</span></span> <span data-ttu-id="9dbaa-186">Anstatt eine Referenz auf das CompositionObject zu „abzurufen“, erstellen Sie eine Referenz mit einem Namen und vergeben dann andere Werte:</span><span class="sxs-lookup"><span data-stu-id="9dbaa-186">Rather than "getting" a reference to the CompositionObject, you create a reference with a name and then assign different values:</span></span>

```
var orbitExpression = ExpressionValues.Reference.CreateVisualReference("orbitRoundVisual");
orbitExpression.SetReferenceParameter("orbitRoundVisual", redSprite);
blueSprite.StartAnimation("Offset", orbitExpression);
// Later on … use same Expression to assign to another orbiting Visual
orbitExpression.SetReferenceParameter("orbitRoundVisual", yellowSprite);
greenSprite.StartAnimation("Offset", orbitExpression);
```

<span data-ttu-id="9dbaa-187">Hier ist der Code, wenn Sie Ihren Ausdruck mit Zeichenfolgen über die öffentliche API definiert haben.</span><span class="sxs-lookup"><span data-stu-id="9dbaa-187">Here is the code if you defined your Expression with Strings via the public API.</span></span>

```
ExpressionAnimation expressionAnimation =
compositor.CreateExpressionAnimation("visual.Offset + " +
"propertySet.CenterPointOffset + " +
"Vector3(cos(ToRadians(propertySet.Rotation)) * 150," + "sin(ToRadians(propertySet.Rotation)) * 75, 0)");
 var propSetCenterPoint = _propertySet.GetReference().GetVector3Property("CenterPointOffset");
 var propSetRotation = _propertySet.GetReference().GetScalarProperty("Rotation");
expressionAnimation.SetReferenceParameter("propertySet", _propertySet);
expressionAnimation.SetReferenceParameter("visual", redSprite);
```
