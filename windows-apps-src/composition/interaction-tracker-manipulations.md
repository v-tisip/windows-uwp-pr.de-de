---
author: jwmsft
title: Angepasste Manipulation mit InteractionTracker
description: In diesem Artikel zeigen wir Ihnen, wie Sie mit InteractionTracker benutzerdefinierte Manipulationserlebnisse erstellen können.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 0a991d692b4ba4c7a221932218a7d25e48fe16ca
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5764826"
---
# <a name="custom-manipulation-experiences-with-interactiontracker"></a><span data-ttu-id="352f7-104">Angepasste Manipulation mit InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="352f7-104">Custom manipulation experiences with InteractionTracker</span></span>

<span data-ttu-id="352f7-105">In diesem Artikel zeigen wir Ihnen, wie Sie mit InteractionTracker benutzerdefinierte Manipulationserlebnisse erstellen können.</span><span class="sxs-lookup"><span data-stu-id="352f7-105">In this article, we show how to use InteractionTracker to create custom manipulation experiences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="352f7-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="352f7-106">Prerequisites</span></span>

<span data-ttu-id="352f7-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="352f7-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="352f7-108">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="352f7-108">Input-driven animations</span></span>](input-driven-animations.md)
- [<span data-ttu-id="352f7-109">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="352f7-109">Relation based animations</span></span>](relation-animations.md)

## <a name="why-create-custom-manipulation-experiences"></a><span data-ttu-id="352f7-110">Warum benutzerdefinierte Manipulationserlebnisse erstellen?</span><span class="sxs-lookup"><span data-stu-id="352f7-110">Why create custom manipulation experiences?</span></span>

<span data-ttu-id="352f7-111">In den meisten Fällen ist die Verwendung der vorkonfigurierten Manipulationssteuerelementen ausreichend, um UI-Erlebnisse zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="352f7-111">In most cases, utilizing the pre-built manipulation controls are good enough to create UI experiences.</span></span> <span data-ttu-id="352f7-112">Aber was wäre, wenn Sie sich von den üblichen Steuerelementen unterscheiden wollten?</span><span class="sxs-lookup"><span data-stu-id="352f7-112">But what if you wanted to differentiate from the common controls?</span></span> <span data-ttu-id="352f7-113">Was wäre, wenn Sie ein spezifisches Erlebnis schaffen wollten, das durch Eingaben gesteuert wird oder eine Benutzeroberfläche haben wollten, in der eine traditionelle Manipulationsbewegung nicht ausreicht?</span><span class="sxs-lookup"><span data-stu-id="352f7-113">What if you wanted to create a specific experience driven by input or have a UI where a traditional manipulation motion is not sufficient?</span></span> <span data-ttu-id="352f7-114">Hier setzt das Erstellen benutzerdefinierter Erlebnisse an.</span><span class="sxs-lookup"><span data-stu-id="352f7-114">This is where creating custom experiences comes in.</span></span> <span data-ttu-id="352f7-115">Sie ermöglichen App-Entwicklern und Designern, kreativer zu sein – sie erwecken Bewegungserlebnisse zum Leben, die ihr Branding und ihre eigene Designsprache besser umsetzen.</span><span class="sxs-lookup"><span data-stu-id="352f7-115">They enable app developers and designers to be more creative – bring to life motion experiences that better exemplify their branding and custom design language.</span></span> <span data-ttu-id="352f7-116">Sie erhalten Zugang zu den richtigen Bausteinen, um das gesamte Manipulationserlebnis individuell gestalten zu können – von der Art und Weise, wie Bewegungen mit dem Finger auf dem Bildschirm reagieren sollen, bis hin zu Andockpunkten und der Verkettung von Eingaben.</span><span class="sxs-lookup"><span data-stu-id="352f7-116">From the ground up, you are given access to the right set of building blocks to completely customize a manipulation experience – from how motion should respond with the finger on and off the screen to snap points and input chaining.</span></span>

<span data-ttu-id="352f7-117">Nachfolgend finden Sie einige Beispiele, wann Sie eine benutzerdefinierte Manipulation erstellen könnten:</span><span class="sxs-lookup"><span data-stu-id="352f7-117">Below are some common examples of when you’d create a custom manipulation experience:</span></span>

- <span data-ttu-id="352f7-118">Hinzufügen eines benutzerdefinierten Wisch-, Lösch-/Schließen-Verhaltens</span><span class="sxs-lookup"><span data-stu-id="352f7-118">Adding a custom swipe, delete/dismiss behavior</span></span>
- <span data-ttu-id="352f7-119">Eingabegesteuerte Effekte (Schwenken führt zu unscharfen Inhalten)</span><span class="sxs-lookup"><span data-stu-id="352f7-119">Input driven effects (panning causes content to blur)</span></span>
- <span data-ttu-id="352f7-120">Benutzerdefinierte Steuerelemente mit maßgeschneiderten Manipulationsbewegungen (angepasstes ListView, ScrollViewer usw.).</span><span class="sxs-lookup"><span data-stu-id="352f7-120">Custom Controls with tailored manipulation motions (custom ListView, ScrollViewer, etc.)</span></span>

![Beispiel zum Scrollen durch Wischen](images/animation/swipe-scroller.gif)

![Beispiel zum Ziehen zum Animieren](images/animation/pull-to-animate.gif)

## <a name="why-use-interactiontracker"></a><span data-ttu-id="352f7-123">Warum die InteractionTracker-Klasse verwenden?</span><span class="sxs-lookup"><span data-stu-id="352f7-123">Why use InteractionTracker?</span></span>

<span data-ttu-id="352f7-124">InteractionTracker wurde in der 10586 SDK-Version im Namespace Windows.UI.Composition.Interactions eingeführt.</span><span class="sxs-lookup"><span data-stu-id="352f7-124">InteractionTracker was introduced to the Windows.UI.Composition.Interactions namespace in the 10586 SDK version.</span></span> <span data-ttu-id="352f7-125">InteractionTracker ermöglicht folgendes:</span><span class="sxs-lookup"><span data-stu-id="352f7-125">InteractionTracker enables:</span></span>

- <span data-ttu-id="352f7-126">**Absolute Flexibilität** – Wir möchten, dass Sie in der Lage sind, jeden Aspekt eines Manipulationserlebnisses individuell anzupassen. Insbesondere die genauen Bewegungen, die während oder in Reaktion auf Eingaben auftreten.</span><span class="sxs-lookup"><span data-stu-id="352f7-126">**Complete Flexibility** – we want you to be able to customize and tailor every aspect of a manipulation experience; specifically, the exact motions that occur during, or in response to, input.</span></span> <span data-ttu-id="352f7-127">Wenn Sie mit InteractionTracker ein benutzerdefiniertes Manipulationserlebnis erstellen, stehen Ihnen alle Möglichkeiten zur Verfügung, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="352f7-127">When building a custom manipulation experience with InteractionTracker, all the knobs you need are at your disposal.</span></span>
- <span data-ttu-id="352f7-128">**Flüssige Ausführung** – Eine der Herausforderungen bei Manipulationserfahrungen ist, dass ihre Performance vom UI-Thread abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="352f7-128">**Smooth Performance** – one of the challenges with manipulation experiences is that their performance is dependent on the UI thread.</span></span> <span data-ttu-id="352f7-129">Dies kann sich negativ auf jede Manipulationserfahrung auswirken, wenn die Benutzeroberfläche beschäftigt ist.</span><span class="sxs-lookup"><span data-stu-id="352f7-129">This can negatively impact any manipulation experience when the UI is busy.</span></span> <span data-ttu-id="352f7-130">InteractionTracker wurde entwickelt, um die neue Animationsengine zu nutzen, die mit einem unabhängigen Thread mit 60 FPS arbeitet, was zu einer flüssigen Darstellung führt.</span><span class="sxs-lookup"><span data-stu-id="352f7-130">InteractionTracker was built to utilize the new Animation engine that operates on an independent thread at 60 FPS,resulting in smooth motion.</span></span>

## <a name="overview-interactiontracker"></a><span data-ttu-id="352f7-131">Übersicht: InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="352f7-131">Overview: InteractionTracker</span></span>

<span data-ttu-id="352f7-132">Bei der Erstellung angepasster Manipulationserlebnisse gibt es zwei Hauptkomponenten, mit denen Sie interagieren.</span><span class="sxs-lookup"><span data-stu-id="352f7-132">When creating custom manipulation experiences, there are two primary components you interact with.</span></span> <span data-ttu-id="352f7-133">Wir besprechen diese zuerst:</span><span class="sxs-lookup"><span data-stu-id="352f7-133">We’ll discuss these first:</span></span>

- <span data-ttu-id="352f7-134">[InteractionTracker](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.interactiontracker) – Das Kernobjekt, das eine State-Machine verwaltet, deren Eigenschaften durch aktive Benutzereingaben oder direkte Updates und Animationen gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="352f7-134">[InteractionTracker](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.interactiontracker) – the core object maintaining a state machine whose properties are driven by active user input or direct updates and animations.</span></span> <span data-ttu-id="352f7-135">Diese wird an eine CompositionAnimation gebunden, um die Manipulationsbewegung zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="352f7-135">It is intended to then tie to a CompositionAnimation to create the custom manipulation motion.</span></span>
- <span data-ttu-id="352f7-136">[VisualInteractionSource](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.visualinteractionsource) – Ein Ergänzungsobjekt, das definiert, wann und unter welchen Bedingungen Eingaben an InteractionTracker gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="352f7-136">[VisualInteractionSource](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.visualinteractionsource) – a complement object that defines when and under what conditions input gets sent to InteractionTracker.</span></span> <span data-ttu-id="352f7-137">Es definiert sowohl CompositionVisual, die für das Hit-Testen verwendet wird, als auch andere Eigenschaften der Eingabekonfiguration.</span><span class="sxs-lookup"><span data-stu-id="352f7-137">It defines both the CompositionVisual used for Hit-testing as well as other input configuration properties.</span></span>

<span data-ttu-id="352f7-138">Als State-Machine können die Eigenschaften von InteractionTracker durch eine der folgenden Optionen gesteuert werden:</span><span class="sxs-lookup"><span data-stu-id="352f7-138">As a state machine, properties of InteractionTracker can be driven by any of the following:</span></span>

- <span data-ttu-id="352f7-139">Direkte Benutzerinteraktion – Der Endanwender manipuliert direkt innerhalb der VisualInteractionSource-Hit-Testregion</span><span class="sxs-lookup"><span data-stu-id="352f7-139">Direct User Interaction – the end user is directly manipulating within the VisualInteractionSource hit-test region</span></span>
- <span data-ttu-id="352f7-140">Trägheit – Entweder durch programmgesteuerte Beschleunigung oder eine Geste des Benutzers werden Eigenschaften von InteractionTracker über eine Trägheitskurve animiert</span><span class="sxs-lookup"><span data-stu-id="352f7-140">Inertia – either from programmatic velocity or a user gesture, properties of InteractionTracker animate under an inertia curve</span></span>
- <span data-ttu-id="352f7-141">CustomAnimation – Eine angepasste Animation für eine Eigenschaft von InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="352f7-141">CustomAnimation – a custom animation directly targeting a property of InteractionTracker</span></span>

### <a name="interactiontracker-state-machine"></a><span data-ttu-id="352f7-142">InteractionTracker-State-Machine</span><span class="sxs-lookup"><span data-stu-id="352f7-142">InteractionTracker State Machine</span></span>

<span data-ttu-id="352f7-143">Wie bereits erwähnt, ist InteractionTracker eine State-Machine mit 4 Zuständen, von die jeder in eines der anderen Fourstates übergehen kann.</span><span class="sxs-lookup"><span data-stu-id="352f7-143">As mentioned previously, InteractionTracker is a state machine with 4 states – each of which can transition to any of the other fourstates.</span></span> <span data-ttu-id="352f7-144">(Weitere Informationen darüber, wie InteractionTracker zwischen diesen Zuständen übergeht, finden Sie in der [InteractionTracker](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.interactiontracker)-Klassendokumentation.)</span><span class="sxs-lookup"><span data-stu-id="352f7-144">(For more info about how InteractionTracker transitions between these states, see the [InteractionTracker](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.interactiontracker) class documentation.)</span></span>

| <span data-ttu-id="352f7-145">Zustand</span><span class="sxs-lookup"><span data-stu-id="352f7-145">State</span></span> | <span data-ttu-id="352f7-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="352f7-146">Description</span></span> |
|-------|-------------|
| <span data-ttu-id="352f7-147">Idle</span><span class="sxs-lookup"><span data-stu-id="352f7-147">Idle</span></span> | <span data-ttu-id="352f7-148">Nicht aktiv, keine Eingaben oder Animationen</span><span class="sxs-lookup"><span data-stu-id="352f7-148">No active, driving inputs or animations</span></span> |
| <span data-ttu-id="352f7-149">Interacting</span><span class="sxs-lookup"><span data-stu-id="352f7-149">Interacting</span></span> | <span data-ttu-id="352f7-150">Aktive Benutzereingaben erkannt</span><span class="sxs-lookup"><span data-stu-id="352f7-150">Active user input detected</span></span> |
| <span data-ttu-id="352f7-151">Inertia</span><span class="sxs-lookup"><span data-stu-id="352f7-151">Inertia</span></span> | <span data-ttu-id="352f7-152">Aktive Bewegung aus aktiver Eingabe oder programmgesteuerter Beschleunigung</span><span class="sxs-lookup"><span data-stu-id="352f7-152">Active motion resulting from active input or programmatic velocity</span></span> |
| <span data-ttu-id="352f7-153">CustomAnimation</span><span class="sxs-lookup"><span data-stu-id="352f7-153">CustomAnimation</span></span> | <span data-ttu-id="352f7-154">Aktive Bewegung, die durch eine angepasste Animation entsteht</span><span class="sxs-lookup"><span data-stu-id="352f7-154">Active motion resulting from a custom animation</span></span> |

<span data-ttu-id="352f7-155">In jedem der Fälle, in denen sich der Zustand des InteractionTracker ändert, wird ein Ereignis (oder Callback) generiert, auf das Sie warten können.</span><span class="sxs-lookup"><span data-stu-id="352f7-155">In each of the cases where the state of InteractionTracker changes, an event (or callback) is generated that you can listen for.</span></span> <span data-ttu-id="352f7-156">Damit Sie auf diese Ereignisse warten können, müssen sie die Schnittstelle [IInteractionTrackerOwner](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.iinteractiontrackerowner) implementieren und ihr InteractionTracker-Objekt mit der Methode CreateWithOwner erzeugen.</span><span class="sxs-lookup"><span data-stu-id="352f7-156">In order for you to listen for these events, they must implement the [IInteractionTrackerOwner](https://docs.microsoft.com/uwp/api/windows.ui.composition.interactions.iinteractiontrackerowner) interface and create their InteractionTracker object with the CreateWithOwner method.</span></span> <span data-ttu-id="352f7-157">Das folgende Diagramm zeigt auch, wann die verschiedenen Ereignisse ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="352f7-157">The following diagram also outlines when the different events get triggered.</span></span>

![InteractionTracker-State-Machine](images/animation/interaction-tracker-diagram.png)

## <a name="using-the-visualinteractionsource"></a><span data-ttu-id="352f7-159">Verwendung der VisualInteractionSource</span><span class="sxs-lookup"><span data-stu-id="352f7-159">Using the VisualInteractionSource</span></span>

<span data-ttu-id="352f7-160">Damit InteractionTracker von Eingaben gesteuert werden kann, müssen Sie eine VisualInteractionSource (VIS) verbinden.</span><span class="sxs-lookup"><span data-stu-id="352f7-160">For InteractionTracker to be driven by Input, you need to connect a VisualInteractionSource (VIS) to it.</span></span> <span data-ttu-id="352f7-161">Die VIS wird als Ergänzungsobjekt mit Hilfe eines CompositionVisual erstellt. Es definiert folgendes:</span><span class="sxs-lookup"><span data-stu-id="352f7-161">The VIS is created as a complement object using a CompositionVisual to define:</span></span>

1. <span data-ttu-id="352f7-162">Die Hit-Test-Region, in der die Eingabe verfolgt wird, und der Koordinatenraum, in dem Gesten erkannt werden</span><span class="sxs-lookup"><span data-stu-id="352f7-162">The hit-test region that input will be tracked, and the coordinate space gestures are detected in</span></span>
1. <span data-ttu-id="352f7-163">Die Konfigurationen der Eingaben, die erkannt und geroutet werden. Einige von diesen sind:</span><span class="sxs-lookup"><span data-stu-id="352f7-163">The configurations of input that will get detected and routed, a few include:</span></span>
    - <span data-ttu-id="352f7-164">Erkennbare Gesten: Position X und Y (horizontales und vertikales Schwenken), die Skalierung (Zusammendrücken)</span><span class="sxs-lookup"><span data-stu-id="352f7-164">Detectable gestures: Position X and Y (horizontal and vertical panning), Scale (pinch)</span></span>
    - <span data-ttu-id="352f7-165">Trägheit</span><span class="sxs-lookup"><span data-stu-id="352f7-165">Inertia</span></span>
    - <span data-ttu-id="352f7-166">Führungsschienen und Verkettung</span><span class="sxs-lookup"><span data-stu-id="352f7-166">Rails & Chaining</span></span>
    - <span data-ttu-id="352f7-167">Umleitungsmodi: Welche Eingaben von Daten werden automatisch an InteractionTracker umgeleitet?</span><span class="sxs-lookup"><span data-stu-id="352f7-167">Redirection Modes: what input data is redirected automatically to InteractionTracker</span></span>

> [!NOTE]
> <span data-ttu-id="352f7-168">Da VisualInteractionSource auf der Grundlage der Hit-Test-Position und des Koordinatenraumes eines Visual erstellt wird, wird empfohlen, kein Visual zu verwenden, das sich in Bewegung befindet oder seine Position ändert.</span><span class="sxs-lookup"><span data-stu-id="352f7-168">Because the VisualInteractionSource is created based off the hit-test position and coordinate space of a Visual, it recommended not to use a Visual that will be in motion or changing position.</span></span>

> [!NOTE]
> <span data-ttu-id="352f7-169">Sie können mehrere VisualInteractionSource-Instanzen mit dem gleichen InteractionTracker verwenden, wenn es mehrere Hit-Test-Regionen gibt.</span><span class="sxs-lookup"><span data-stu-id="352f7-169">You can use multiple VisualInteractionSource instances with the same InteractionTracker if there are multiple hit-test regions.</span></span> <span data-ttu-id="352f7-170">Der häufigste Fall ist jedoch, dass nur ein einziges VIS verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="352f7-170">However, the most common case is to use only one VIS.</span></span>

<span data-ttu-id="352f7-171">Die VisualInteractionSource ist auch für die Verwaltung zuständig, wenn Eingabedaten aus verschiedenen Modalitäten (Touch, PTP, Pen) an den InteractionTracker geroutet werden.</span><span class="sxs-lookup"><span data-stu-id="352f7-171">The VisualInteractionSource is also responsible for managing when input data from different modalities (touch, PTP, Pen) get routed to InteractionTracker.</span></span> <span data-ttu-id="352f7-172">Dieses Verhalten wird durch die ManipulationRedirectionMode-Eigenschaft definiert.</span><span class="sxs-lookup"><span data-stu-id="352f7-172">This behavior is defined by the ManipulationRedirectionMode property.</span></span> <span data-ttu-id="352f7-173">Standardmäßig werden alle Pointer-Eingaben an den UI-Thread und Precision-Touchpad-Eingaben an VisualInteractionSource und den InteractionTracker gesendet.</span><span class="sxs-lookup"><span data-stu-id="352f7-173">By default, all Pointer input is sent to the UI thread and Precision Touchpad input goes to the VisualInteractionSource and InteractionTracker.</span></span>

<span data-ttu-id="352f7-174">Wenn Sie also Touch und Pen (Creators Update) benötigen, um eine Manipulation durch VisualInteractionSource und InteractionTracker zu steuern, müssen Sie die Methode VisualInteractionSource.TryRedirectForManipulation aufrufen.</span><span class="sxs-lookup"><span data-stu-id="352f7-174">Thus, if you want to have Touch and Pen (Creators Update) to drive a manipulation through a VisualInteractionSource and InteractionTracker, you must call the VisualInteractionSource.TryRedirectForManipulation method.</span></span> <span data-ttu-id="352f7-175">Im kurzen Codeausschnitt unten aus einer XAML-App wird die Methode aufgerufen, wenn ein Touch-Pressed-Ereignis im obersten UIElement-Grid auftritt:</span><span class="sxs-lookup"><span data-stu-id="352f7-175">In the short snippet below from a XAML app, the method is called when a touch pressed event occurs at the top most UIElement Grid:</span></span>

```csharp
private void root_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    if (e.Pointer.PointerDeviceType == Windows.Devices.Input.PointerDeviceType.Touch)
    {
        _source.TryRedirectForManipulation(e.GetCurrentPoint(root));
    }
}
```

## <a name="tie-in-with-expressionanimations"></a><span data-ttu-id="352f7-176">Binden an ExpressionAnimations</span><span class="sxs-lookup"><span data-stu-id="352f7-176">Tie-in with ExpressionAnimations</span></span>

<span data-ttu-id="352f7-177">Wenn Sie InteractionTracker verwenden, um Manipulationserfahrungen zu erstellen, interagieren Sie hauptsächlich mit den Scale- und Positions-Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="352f7-177">When utilizing InteractionTracker to drive a manipulation experience, you interact primarily with the Scale and Position properties.</span></span> <span data-ttu-id="352f7-178">Wie andere CompositionObject-Eigenschaften können diese Eigenschaften sowohl das Zielobjekt als auch eine CompositionAnimation-Referenz sein. Am häufigsten referenzieren Sie ExpressionAnimations.</span><span class="sxs-lookup"><span data-stu-id="352f7-178">Like other CompositionObject properties, these properties can be both the target and referenced in a CompositionAnimation, most commonly ExpressionAnimations.</span></span>

<span data-ttu-id="352f7-179">Um InteractionTracker innerhalb eines Ausdrucks zu verwenden, verweisen Sie auf die Position- oder Scale-Eigenschaft des Trackers, wie im Beispiel unten.</span><span class="sxs-lookup"><span data-stu-id="352f7-179">To use InteractionTracker within an Expression, reference the tracker’s Position (or Scale) property like in the example below.</span></span> <span data-ttu-id="352f7-180">Da die Eigenschaft von InteractionTracker aufgrund einer der zuvor beschriebenen Bedingungen geändert wird, ändert sich auch die Ausgabe des Ausdrucks.</span><span class="sxs-lookup"><span data-stu-id="352f7-180">As the property of InteractionTracker is modified due to any of the conditions described earlier, the output of the Expression changes as well.</span></span>

```csharp
// With Strings
var opacityExp = _compositor.CreateExpressionAnimation("-tracker.Position");
opacityExp.SetReferenceParameter("tracker", _tracker);

// With ExpressionBuilder
var opacityExp = -_tracker.GetReference().Position;
```

> [!NOTE]
> <span data-ttu-id="352f7-181">Wenn Sie die Position des InteractionTracker in einem Ausdruck referenzieren, müssen Sie den Wert negieren, damit der resultierende Ausdruck in die richtige Richtung bewegt wird.</span><span class="sxs-lookup"><span data-stu-id="352f7-181">When referencing InteractionTracker’s position in an Expression, you must negate the value for the resulting Expression to move in the correct direction.</span></span> <span data-ttu-id="352f7-182">Dies liegt daran, dass die Bewegung von InteractionTracker vom Ursprung auf einem Graphen basiert und es Ihnen erlaubt, zur Bewegung von InteractionTracker echte Koordinaten zu nutzen (wie z. B. den Abstand von seinem Ursprung).</span><span class="sxs-lookup"><span data-stu-id="352f7-182">This is because InteractionTracker’s progression from origin on a graph and allow you to think about InteractionTracker’s progression in "real world" coordinates, such as distance from its origin.</span></span>

## <a name="get-started"></a><span data-ttu-id="352f7-183">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="352f7-183">Get Started</span></span>

<span data-ttu-id="352f7-184">Gehen Sie folgendermaßen vor, um mit der Verwendung von InteractionTracker zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="352f7-184">To get started with using InteractionTracker to create custom manipulation experiences:</span></span>

1. <span data-ttu-id="352f7-185">Erstellen Sie Ihr InteractionTracker-Objekt mit InteractionTracker.Create oder InteractionTracker.CreateWithOwner.</span><span class="sxs-lookup"><span data-stu-id="352f7-185">Create your InteractionTracker object using InteractionTracker.Create or InteractionTracker.CreateWithOwner.</span></span>
    - <span data-ttu-id="352f7-186">(Wenn Sie CreateWithOwner verwenden, stellen Sie sicher, dass Sie die Schnittstelle IInteractionTrackerOwner implementieren.)</span><span class="sxs-lookup"><span data-stu-id="352f7-186">(If you use CreateWithOwner, ensure you implement the IInteractionTrackerOwner interface.)</span></span>
1. <span data-ttu-id="352f7-187">Legen Sie die Min- und Max-Position des neu erstellten InteractionTracker fest.</span><span class="sxs-lookup"><span data-stu-id="352f7-187">Set the Min and Max position of your newly created InteractionTracker.</span></span>
1. <span data-ttu-id="352f7-188">Erstellen Sie Ihre VisualInteractionSource mit einem CompositionVisual.</span><span class="sxs-lookup"><span data-stu-id="352f7-188">Create your VisualInteractionSource with a CompositionVisual.</span></span>
    - <span data-ttu-id="352f7-189">Stellen Sie sicher, dass das von Ihnen übergebene Visual eine Größe ungleich Null hat.</span><span class="sxs-lookup"><span data-stu-id="352f7-189">Ensure the visual you pass in has a non-zero size.</span></span> <span data-ttu-id="352f7-190">Andernfalls wird es nicht korrekt auf Treffer geprüft.</span><span class="sxs-lookup"><span data-stu-id="352f7-190">Otherwise, it will not get hit-tested correctly.</span></span>
1. <span data-ttu-id="352f7-191">Legen Sie die Eigenschaften der VisualInteractionSource fest.</span><span class="sxs-lookup"><span data-stu-id="352f7-191">Set the properties of the VisualInteractionSource.</span></span>
    - <span data-ttu-id="352f7-192">VisualInteractionSourceRedirectionMode</span><span class="sxs-lookup"><span data-stu-id="352f7-192">VisualInteractionSourceRedirectionMode</span></span>
    - <span data-ttu-id="352f7-193">PositionXSourceMode, PositionYSourceMode, ScaleSourceMode</span><span class="sxs-lookup"><span data-stu-id="352f7-193">PositionXSourceMode, PositionYSourceMode, ScaleSourceMode</span></span>
    - <span data-ttu-id="352f7-194">Führungsschienen und Verkettung</span><span class="sxs-lookup"><span data-stu-id="352f7-194">Rails & Chaining</span></span>
1. <span data-ttu-id="352f7-195">Fügen Sie die VisualInteractionSource über InteractionTracker.InteractionSources.Add zum InteractionTracker hinzu.</span><span class="sxs-lookup"><span data-stu-id="352f7-195">Add the VisualInteractionSource to InteractionTracker using InteractionTracker.InteractionSources.Add.</span></span>
1. <span data-ttu-id="352f7-196">Richten Sie TryRedirectForManipulation für die Touch- und Pen-Eingabe ein.</span><span class="sxs-lookup"><span data-stu-id="352f7-196">Setup TryRedirectForManipulation for when Touch and Pen input is detected.</span></span>
    - <span data-ttu-id="352f7-197">Für XAML geschieht dies typischerweise im PointerPressed-Ereignis des UIElements.</span><span class="sxs-lookup"><span data-stu-id="352f7-197">For XAML, this is typically done on the UIElement’s PointerPressed event.</span></span>
1. <span data-ttu-id="352f7-198">Erstellen Sie eine ExpressionAnimation, die die Position von InteractionTracker referenziert und deren Ziel eine CompositionObject Eigenschaft ist.</span><span class="sxs-lookup"><span data-stu-id="352f7-198">Create an ExpressionAnimation that references InteractionTracker’s position and target a CompositionObject’s property.</span></span>

<span data-ttu-id="352f7-199">Hier ist ein kurzes Codestück, das die Schritte 1-5 in Aktion zeigt:</span><span class="sxs-lookup"><span data-stu-id="352f7-199">Here is a short code snippet that shows #1 – 5 in action:</span></span>

```csharp
private void InteractionTrackerSetup(Compositor compositor, Visual hitTestRoot)
{ 
    // #1 Create InteractionTracker object
    var tracker = InteractionTracker.Create(compositor);

    // #2 Set Min and Max positions
    tracker.MinPosition = new Vector3(-1000f);
    tracker.MaxPosition = new Vector3(1000f);

    // #3 Setup the VisualInteractionSourc
    var source = VisualInteractionSource.Create(hitTestRoot);

    // #4 Set the properties for the VisualInteractionSource
    source.ManipulationRedirectionMode =
        VisualInteractionSourceRedirectionMode.CapableTouchpadOnly;
    source.PositionXSourceMode = InteractionSourceMode.EnabledWithInertia;
    source.PositionYSourceMode = InteractionSourceMode.EnabledWithInertia;

    // #5 Add the VisualInteractionSource to InteractionTracker
    tracker.InteractionSources.Add(source);
}
```

<span data-ttu-id="352f7-200">Für weiterführende Anwendungen von InteractionTracker lesen Sie bitte die folgenden Artikel:</span><span class="sxs-lookup"><span data-stu-id="352f7-200">For more advanced usages of InteractionTracker, see the following articles:</span></span>

- [<span data-ttu-id="352f7-201">Erstellen von Andockpunkten mit InertiaModifiern</span><span class="sxs-lookup"><span data-stu-id="352f7-201">Create snap points with InertiaModifiers</span></span>](inertia-modifiers.md)
- [<span data-ttu-id="352f7-202">Pull-to-Refresh mit SourceModifiern</span><span class="sxs-lookup"><span data-stu-id="352f7-202">Pull-to-refresh with SourceModifiers</span></span>](source-modifiers.md)
