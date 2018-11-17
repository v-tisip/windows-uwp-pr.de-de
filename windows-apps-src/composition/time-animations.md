---
author: jwmsft
title: Zeitanimationen
description: Verwenden Sie die KeyFrameAnimation-Klassen, um Ihre Benutzeroberfläche mit der Zeit ändern.
ms.author: jimwalk
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: bf6d3f16c7b240ca370c01a787fef09862f35863
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7160155"
---
# <a name="time-based-animations"></a><span data-ttu-id="8600d-104">Zeitbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="8600d-104">Time based animations</span></span>

<span data-ttu-id="8600d-105">Wenn sich eine Komponente oder ein ganzes Benutzererlebnis ändert, sehen Endbenutzer diese häufig auf zwei Arten: zeitbasiert oder augenblicklich.</span><span class="sxs-lookup"><span data-stu-id="8600d-105">When a component in, or an entire user experience changes, end users often observe it in two ways: over time or instantaneously.</span></span> <span data-ttu-id="8600d-106">Auf der Windows-Plattform das Erstere dem letzteren vorgezogen – benutzererfahrungen, die sofort häufig ändern verwirrt und Endbenutzer verwirren, weil er nicht können durchführen, was passiert ist.</span><span class="sxs-lookup"><span data-stu-id="8600d-106">On the Windows platform, the former is preferred over the latter - user experiences that instantly change often confuse and surprise end users because they are not able to follow what happened.</span></span> <span data-ttu-id="8600d-107">Der Benutzer empfindet das Erlebnis dann als ruckelnd und unnatürlich.</span><span class="sxs-lookup"><span data-stu-id="8600d-107">The end user then perceives the experience as jarring and unnatural.</span></span>

<span data-ttu-id="8600d-108">Stattdessen können Sie Ihre Benutzeroberfläche im Laufe der Zeit ändern, um den Endbenutzer durch die Benutzeroberfläche zu führen oder ihn über Änderungen an der Erfahrung zu informieren.</span><span class="sxs-lookup"><span data-stu-id="8600d-108">Instead, you can change your UI over time to guide the end user through, or notify them of changes to the experience.</span></span> <span data-ttu-id="8600d-109">Unter der Windows-Plattform geschieht dies durch zeitbasierte Animationen, auch KeyFrameAnimations genannt.</span><span class="sxs-lookup"><span data-stu-id="8600d-109">On the Windows platform, this is done by using time-based animations, also known as KeyFrameAnimations.</span></span> <span data-ttu-id="8600d-110">Mit KeyFrameAnimations können Sie eine Benutzeroberfläche im Laufe der Zeit ändern und jeden Aspekt der Animation steuern, einschließlich wie und wann sie startet und wie sie ihren Endzustand erreicht.</span><span class="sxs-lookup"><span data-stu-id="8600d-110">KeyFrameAnimations let you change a UI over time and control each aspect of the animation, including how and when it starts, and how it reaches its end state.</span></span> <span data-ttu-id="8600d-111">Beispielsweise ist es angenehmer, ein Objekt über 300 Millisekunden hinweg auf eine neue Position zu animieren, als es dort sofort „teleportieren“.</span><span class="sxs-lookup"><span data-stu-id="8600d-111">For example, animating an object to a new position over 300 milliseconds is more pleasant than instantly "teleporting" it there.</span></span> <span data-ttu-id="8600d-112">Wenn Animationen anstelle von blitzschnellen Änderungen verwendet werden, ist das Endergebnis ein angenehmeres und ansprechenderes Erlebnis.</span><span class="sxs-lookup"><span data-stu-id="8600d-112">When using animations instead of instantaneous changes, the net result is a more pleasant and appealing experience.</span></span>

## <a name="types-of-time-based-animations"></a><span data-ttu-id="8600d-113">Arten von zeitbasierten Animationen</span><span class="sxs-lookup"><span data-stu-id="8600d-113">Types of time based Animations</span></span>

<span data-ttu-id="8600d-114">Es gibt zwei Kategorien von zeitbasierten Animationen, mit denen Sie unter Windows schöne Benutzererlebnisse erstellen können:</span><span class="sxs-lookup"><span data-stu-id="8600d-114">There are two categories of time-based animations you can use to build beautiful user experiences on Windows:</span></span>

<span data-ttu-id="8600d-115">**Explizite Animationen** – Wie der Name schon sagt, starten Sie die Animation explizit, um Updates durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="8600d-115">**Explicit Animations** – as the name signifies, you explicitly start the animation to make updates.</span></span>
<span data-ttu-id="8600d-116">**Implizite Animationen** – Diese Animationen werden vom System in Ihrem Namen ausgelöst, wenn eine Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="8600d-116">**Implicit Animations** – these animations are kicked off by the system on your behalf when a condition is met.</span></span>

<span data-ttu-id="8600d-117">In diesem Artikel werden wir erklären, wie man _explizite_ zeitbasierte Animationen mit KeyFrameAnimations erstellt und verwendet.</span><span class="sxs-lookup"><span data-stu-id="8600d-117">For this article, we will discuss how to create and use _explicit_ time-based animations with KeyFrameAnimations.</span></span>

<span data-ttu-id="8600d-118">Für explizite und implizite zeitbasierte Animationen gibt es verschiedene Arten von Animationen, die den verschiedenen Eigenschaften von CompositionObjects entsprechen, die Sie animieren können.</span><span class="sxs-lookup"><span data-stu-id="8600d-118">For both explicit and implicit time based animations, there are different types, corresponding to the different types of properties of CompositionObjects you can animate.</span></span>

- <span data-ttu-id="8600d-119">ColorKeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-119">ColorKeyFrameAnimation</span></span>
- <span data-ttu-id="8600d-120">QuaternionKeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-120">QuaternionKeyFrameAnimation</span></span>
- <span data-ttu-id="8600d-121">ScalarKeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-121">ScalarKeyFrameAnimation</span></span>
- <span data-ttu-id="8600d-122">Vector2KeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-122">Vector2KeyFrameAnimation</span></span>
- <span data-ttu-id="8600d-123">Vector3KeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-123">Vector3KeyFrameAnimation</span></span>
- <span data-ttu-id="8600d-124">Vector4KeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="8600d-124">Vector4KeyFrameAnimation</span></span>

## <a name="create-time-based-animations-with-keyframeanimations"></a><span data-ttu-id="8600d-125">Zeitbasierte Animationen mit KeyFrameAnimations erstellen</span><span class="sxs-lookup"><span data-stu-id="8600d-125">Create time based animations with KeyFrameAnimations</span></span>

<span data-ttu-id="8600d-126">Bevor wir beschreiben, wie man explizit zeitbasierte Animationen mit KeyFrameAnimations erstellt, gehen wir ein paar Konzepte durch.</span><span class="sxs-lookup"><span data-stu-id="8600d-126">Before describing how to create explicit time-based animations with KeyFrameAnimations, let’s go over a few concepts.</span></span>

- <span data-ttu-id="8600d-127">KeyFrames – Das sind die einzelnen „Schnappschüsse“, die eine Animation durchlaufen soll.</span><span class="sxs-lookup"><span data-stu-id="8600d-127">KeyFrames – These are the individual "snapshots" that an animation will animate through.</span></span>
  - <span data-ttu-id="8600d-128">Definiert als Schlüssel- und Wertepaar.</span><span class="sxs-lookup"><span data-stu-id="8600d-128">Defined as key & value pairs.</span></span> <span data-ttu-id="8600d-129">Der Schlüssel stellt den Fortschritt zwischen 0 und 1 dar, auch bekannt Animationsdauer für diesen „Schnappschuss“.</span><span class="sxs-lookup"><span data-stu-id="8600d-129">The key represents the progress between 0 and 1, aka where in the animation lifetime this “snapshot” takes places.</span></span> <span data-ttu-id="8600d-130">Der andere Parameter stellt den Eigenschaftswert zu diesem Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="8600d-130">The other parameter represents the property value at this time.</span></span>
- <span data-ttu-id="8600d-131">KeyFrameAnimation-Eigenschaften – Anpassungsoptionen, die Sie anwenden können, um die Anforderungen der Benutzeroberfläche zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="8600d-131">KeyFrameAnimation Properties – customization options you can apply to meet the needs of the UI.</span></span>
  - <span data-ttu-id="8600d-132">DelayTime – Zeit vor dem Starten einer Animation, nachdem StartAnimation aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8600d-132">DelayTime – time before an animation starts after StartAnimation is called.</span></span>
  - <span data-ttu-id="8600d-133">Duration – Dauer der Animation.</span><span class="sxs-lookup"><span data-stu-id="8600d-133">Duration – duration of the animation.</span></span>
  - <span data-ttu-id="8600d-134">Iterationsverhalten – Anzahl bzw. unendliches Wiederholungsverhalten einer Animation.</span><span class="sxs-lookup"><span data-stu-id="8600d-134">IterationBehavior – count or infinite repeat behavior for an animation.</span></span>
  - <span data-ttu-id="8600d-135">Iterationsanzahl – Anzahl der finiten Wiederholungen einer Keyframeanimation.</span><span class="sxs-lookup"><span data-stu-id="8600d-135">IterationCount – number of finite times a KeyFrame Animation will repeat.</span></span>
  - <span data-ttu-id="8600d-136">Keyframeanzahl – Anzahl von Keyframes in einer bestimmten Keyframeanimation.</span><span class="sxs-lookup"><span data-stu-id="8600d-136">KeyFrame Count – read of how many KeyFrames in a particular KeyFrame Animation.</span></span>
  - <span data-ttu-id="8600d-137">Stoppverhalten – legt das Verhalten eines Animationseigenschaftswerts fest, wenn „StopAnimation“ aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8600d-137">StopBehavior – specifies the behavior of an animating property value when StopAnimation is called.</span></span>
  - <span data-ttu-id="8600d-138">Direction – Gibt die Richtung der Animation für die Wiedergabe an.</span><span class="sxs-lookup"><span data-stu-id="8600d-138">Direction – specifies the direction of the animation for playback.</span></span>
- <span data-ttu-id="8600d-139">Animation Group – Mehrere Animationen gleichzeitig starten.</span><span class="sxs-lookup"><span data-stu-id="8600d-139">Animation Group – starting multiple animations at the same time.</span></span>
  - <span data-ttu-id="8600d-140">Wird häufig verwendet, wenn mehrere Eigenschaften gleichzeitig animiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8600d-140">Often used when wanting to animate multiple properties at the same time.</span></span>

<span data-ttu-id="8600d-141">Weitere Informationen finden Sie unter [CompositionAnimationGroup](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionanimationgroup).</span><span class="sxs-lookup"><span data-stu-id="8600d-141">For more info, see [CompositionAnimationGroup](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionanimationgroup).</span></span>

<span data-ttu-id="8600d-142">Mit diesen Konzepten im Hinterkopf, lassen Sie uns die allgemeine Formel für die Konstruktion einer KeyFrameAnimation durchsprechen:</span><span class="sxs-lookup"><span data-stu-id="8600d-142">With these concepts in mind, let’s talk through the general formula for constructing a KeyFrameAnimation:</span></span>

1. <span data-ttu-id="8600d-143">Identifizieren Sie das CompositionObject und seine jeweilige Eigenschaft, die Sie animieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8600d-143">Identify the CompositionObject and its respective property that you need to animate.</span></span>
1. <span data-ttu-id="8600d-144">Erstellen Sie eine KeyFrameAnimation-Vorlage des Compositors, die dem Typ der zu animierenden Eigenschaft entspricht.</span><span class="sxs-lookup"><span data-stu-id="8600d-144">Create a KeyFrameAnimation Type template of the compositor that matches the type of property you want to animate.</span></span>
1. <span data-ttu-id="8600d-145">Verwenden Sie die Animationsvorlage und fügen Sie KeyFrames hinzu und definieren Sie die Eigenschaften der Animation.</span><span class="sxs-lookup"><span data-stu-id="8600d-145">Using the animation template, start adding KeyFrames and defining properties of the animation.</span></span>
    - <span data-ttu-id="8600d-146">Mindestens ein KeyFrame (das 100%- oder 1f-KeyFrame) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8600d-146">At least one KeyFrame is required (the 100% or 1f keyframe).</span></span>
    - <span data-ttu-id="8600d-147">Es wird empfohlen, auch eine Dauer zu definieren.</span><span class="sxs-lookup"><span data-stu-id="8600d-147">It is recommended to define a duration as well.</span></span>
1. <span data-ttu-id="8600d-148">Sobald Sie bereit sind, diese Animation auszuführen, rufen Sie StartAnimation(...) für das CompositionObject auf, um die Eigenschaft auszuwählen, die Sie animieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8600d-148">Once you are ready to run this animation then call StartAnimation(…) on the CompositionObject, targeting the property which you want to animate.</span></span> <span data-ttu-id="8600d-149">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8600d-149">Specifically:</span></span>
    - `Visual.StartAnimation("targetProperty", CompositionAnimation animation);`
    - `Visual.StartAnimationGroup(AnimationGroup animationGroup);`
1. <span data-ttu-id="8600d-150">Wenn Sie eine laufende Animation haben und die Animation oder Animationsgruppe anhalten möchten, können Sie diese APIs verwenden:</span><span class="sxs-lookup"><span data-stu-id="8600d-150">If you have a running animation and you will like to stop the Animation or Animation Group you can use these APIs:</span></span>
    - `Visual.StopAnimation("targetProperty");`
    - `Visual.StopAnimationGroup(AnimationGroup AnimationGroup);`

<span data-ttu-id="8600d-151">Schauen wir uns ein Beispiel an, um diese Formel in Aktion zu sehen.</span><span class="sxs-lookup"><span data-stu-id="8600d-151">Let’s take a look an example to see this formula in action.</span></span>

## <a name="example"></a><span data-ttu-id="8600d-152">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8600d-152">Example</span></span>

<span data-ttu-id="8600d-153">In diesem Beispiel wird den Offset eines visuellen Elements von <0,0,0> zu <20,20,20> über 1Sekunde animiert.</span><span class="sxs-lookup"><span data-stu-id="8600d-153">In this example, you want to animate the offset of a visual from <0,0,0> to <20,20,20> over 1 seconds.</span></span> <span data-ttu-id="8600d-154">Zusätzlich möchten Sie die visuelle Animation zwischen diesen Positionen 10 mal sehen.</span><span class="sxs-lookup"><span data-stu-id="8600d-154">In addition, you want to see the visual animate between these positions 10 times.</span></span>

![Keyframe-Animation](images/animation/animated-rectangle.gif)

<span data-ttu-id="8600d-156">Sie beginnen zunächst mit der Auswahl des CompositionObjects und der Eigenschaft, die Sie animieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8600d-156">You first start by identifying the CompositionObject and property you want to animate.</span></span> <span data-ttu-id="8600d-157">In diesem Fall wird das rote Quadrat durch ein Composition-Visual mit dem Namen `redSquare` dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8600d-157">In this case, the red square is represented by a Composition Visual named `redSquare`.</span></span> <span data-ttu-id="8600d-158">Sie starten Ihre Animation von diesem Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="8600d-158">You start your animation from this object.</span></span>

<span data-ttu-id="8600d-159">Als nächstes müssen Sie eine Vector3KeyFrameAnimation (Offset ist vom Typ Vector3) erstellen, da Sie die Offset-Eigenschaft animieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8600d-159">Next, because you want to animate the Offset property, you need to create a Vector3KeyFrameAnimation (Offset is of type Vector3).</span></span> <span data-ttu-id="8600d-160">Zusätzlich definieren Sie die entsprechenden KeyFrames für die KeyFrameAnimation.</span><span class="sxs-lookup"><span data-stu-id="8600d-160">You also define the corresponding KeyFrames for the KeyFrameAnimation.</span></span>

```csharp
    Vector3KeyFrameAnimation animation = compositor.CreateVector3KeyFrameAnimation();
    animation.InsertKeyFrame(1f, new Vector3(200f, 0f, 0f));
```

<span data-ttu-id="8600d-161">Anschließend definieren wir die Eigenschaften der KeyFrameAnimation, um dessen Dauer sowie das Animationsverhalten zwischen den zwei Positionen 10 mal zu beschreiben (aktuelle und < 200,0,0 >).</span><span class="sxs-lookup"><span data-stu-id="8600d-161">Then we will define the properties of the KeyFrameAnimation to describe it’s duration along with the behavior to animate between the two positions (current and <200,0,0>) 10 times.</span></span>

```csharp
    animation.Duration = TimeSpan.FromSeconds(2);
    animation.Direction = Windows.UI.Composition.AnimationDirection.Alternate;
    // Run animation for 10 times
    animation.IterationCount = 10;
```

<span data-ttu-id="8600d-162">Um schließlich eine Animation auszuführen, müssen Sie diese auf einer Eigenschaft eines CompositionObjects starten.</span><span class="sxs-lookup"><span data-stu-id="8600d-162">Finally, in order to run an animation, you need to start it on a property of a CompositionObject.</span></span>

```csharp
redVisual.StartAnimation("Offset.X", animation);
```

<span data-ttu-id="8600d-163">Hier ist der komplette Code.</span><span class="sxs-lookup"><span data-stu-id="8600d-163">Here's the full code.</span></span>

```csharp
private void AnimateSquare(Compositor compositor, SpriteVisual redSquare)
{ 
    Vector3KeyFrameAnimation animation = compositor.CreateVector3KeyFrameAnimation();
    animation.InsertKeyFrame(1f, new Vector3(200f, 0f, 0f));
    animation.Duration = TimeSpan.FromSeconds(2);
    animation.Direction = Windows.UI.Composition.AnimationDirection.Alternate;
    // Run animation for 10 times
    animation.IterationCount = 10;
    visual.StartAnimation("Offset.X", animation);
} 
```
