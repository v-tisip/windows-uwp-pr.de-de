---
author: Jwmsft
title: XAML-Eigenschaftenanimationen
description: XAML-Elemente mit kompositionsanimationen animieren.
ms.author: jimwalk
ms.date: 09/13/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: stmoy
design-contact: jeffarn
ms.localizationpriority: medium
ms.openlocfilehash: a03ffc8d5ea78ee6cbdf78feaae7ba1cd1448f37
ms.sourcegitcommit: 82c3fc0b06ad490c3456ad18180a6b23ecd9c1a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "5470719"
---
# <a name="animating-xaml-elements-with-composition-animations"></a><span data-ttu-id="e0b69-104">XAML-Elemente mit kompositionsanimationen animieren</span><span class="sxs-lookup"><span data-stu-id="e0b69-104">Animating XAML elements with composition animations</span></span>

<span data-ttu-id="e0b69-105">Dieser Artikel führt neue Eigenschaften, mit die Sie eine XAML-UIElement mit der Leistung von kompositionsanimationen und die einfache Einstellung XAML-Eigenschaften animieren können.</span><span class="sxs-lookup"><span data-stu-id="e0b69-105">This article introduces new properties that let you animate a XAML UIElement with the performance of composition animations and the ease of setting XAML properties.</span></span>

<span data-ttu-id="e0b69-106">Vor Windows 10, Version 1809, mussten Sie 2 Auswahlmöglichkeiten Animationen in Ihren UWP-apps zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="e0b69-106">Prior to Windows 10, version 1809, you had 2 choices to build animations in your UWP apps:</span></span>

- <span data-ttu-id="e0b69-107">Verwenden Sie XAML-Konstrukte wie [storyboardanimationen](storyboarded-animations.md), oder die _\* ThemeTransition_ und _\* ThemeAnimation_ Klassen im Namespace [Windows.UI.Xaml.Media.Animation](/uwp/api/windows.ui.xaml.media.animation) .</span><span class="sxs-lookup"><span data-stu-id="e0b69-107">use XAML constructs like [Storyboarded animations](storyboarded-animations.md), or the _\*ThemeTransition_ and _\*ThemeAnimation_ classes in the [Windows.UI.Xaml.Media.Animation](/uwp/api/windows.ui.xaml.media.animation) namespace.</span></span>
- <span data-ttu-id="e0b69-108">Verwenden Sie kompositionsanimationen, wie in [der visuellen Ebene mit XAML mit](../../composition/using-the-visual-layer-with-xaml.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e0b69-108">use composition animations as described in [Using the Visual Layer with XAML](../../composition/using-the-visual-layer-with-xaml.md).</span></span>

<span data-ttu-id="e0b69-109">Mit der visuellen Ebene bietet eine bessere Leistung als mit der XAML-Code erstellt.</span><span class="sxs-lookup"><span data-stu-id="e0b69-109">Using the visual layer provides better performance than using the XAML constructs.</span></span> <span data-ttu-id="e0b69-110">Aber mit [ElementCompositionPreview](/uwp/api/Windows.UI.Xaml.Hosting.ElementCompositionPreview) des Elements zugrunde liegenden Composition [Visual](/uwp/api/windows.ui.composition.visual) -Objekt abzurufen, und dann Animieren des visuellen Elements mit kompositionsanimationen, ist schwieriger zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e0b69-110">But using [ElementCompositionPreview](/uwp/api/Windows.UI.Xaml.Hosting.ElementCompositionPreview) to get the element's underlying composition [Visual](/uwp/api/windows.ui.composition.visual) object, and then animating the Visual with composition animations, is more complex to use.</span></span>

<span data-ttu-id="e0b69-111">Ab Windows 10, Version 1809, können Sie Eigenschaften für ein UIElement direkt mit kompositionsanimationen ohne die Anforderung zum Abrufen der zugrunde liegenden Kompositions Visual animieren.</span><span class="sxs-lookup"><span data-stu-id="e0b69-111">Starting in Windows 10, version 1809, you can animate properties on a UIElement directly using composition animations without the requirement to get the underlying composition Visual.</span></span>

> [!NOTE]
> <span data-ttu-id="e0b69-112">Um diese Eigenschaften auf UIElement verwenden, muss die Zielversion des UWP-Projekts 1809 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="e0b69-112">To use these properties on UIElement, your UWP project target version must be 1809 or later.</span></span> <span data-ttu-id="e0b69-113">Weitere Informationen zum Konfigurieren von Ihrem Projektversion finden Sie unter [versionsadaptive apps](../../debug-test-perf/version-adaptive-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e0b69-113">For more info about configuring your project version, see [Version adaptive apps](../../debug-test-perf/version-adaptive-apps.md).</span></span>

## <a name="new-rendering-properties-replace-old-rendering-properties"></a><span data-ttu-id="e0b69-114">Neue Renderingeigenschaften ersetzen alte Renderingeigenschaften</span><span class="sxs-lookup"><span data-stu-id="e0b69-114">New rendering properties replace old rendering properties</span></span>

<span data-ttu-id="e0b69-115">Diese Tabelle zeigt die Eigenschaften, mit denen Sie das Rendering ein UIElement ändern, die auch mit einem [CompositionAnimation](/uwp/api/windows.ui.composition.compositionanimation)animiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e0b69-115">This table shows the properties you can use to modify the rendering of a UIElement, that can also be animated with a [CompositionAnimation](/uwp/api/windows.ui.composition.compositionanimation).</span></span>

| <span data-ttu-id="e0b69-116">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e0b69-116">Property</span></span> | <span data-ttu-id="e0b69-117">Typ</span><span class="sxs-lookup"><span data-stu-id="e0b69-117">Type</span></span> | <span data-ttu-id="e0b69-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0b69-118">Description</span></span> |
| -- | -- | -- |
| [<span data-ttu-id="e0b69-119">Opacity</span><span class="sxs-lookup"><span data-stu-id="e0b69-119">Opacity</span></span>](/uwp/api/windows.ui.xaml.uielement.opacity) | <span data-ttu-id="e0b69-120">Double</span><span class="sxs-lookup"><span data-stu-id="e0b69-120">Double</span></span> | <span data-ttu-id="e0b69-121">Der Grad der Deckkraft des Objekts</span><span class="sxs-lookup"><span data-stu-id="e0b69-121">The degree of the object's opacity</span></span> |
| [<span data-ttu-id="e0b69-122">Translation</span><span class="sxs-lookup"><span data-stu-id="e0b69-122">Translation</span></span>](/uwp/api/windows.ui.xaml.uielement.translation) | <span data-ttu-id="e0b69-123">Vector3</span><span class="sxs-lookup"><span data-stu-id="e0b69-123">Vector3</span></span> | <span data-ttu-id="e0b69-124">Die X/Y/Z-Position des Elements zu verschieben</span><span class="sxs-lookup"><span data-stu-id="e0b69-124">Shift the X/Y/Z position of the element</span></span> |
| [<span data-ttu-id="e0b69-125">TransformMatrix</span><span class="sxs-lookup"><span data-stu-id="e0b69-125">TransformMatrix</span></span>](/uwp/api/windows.ui.xaml.uielement.transformmatrix) | <span data-ttu-id="e0b69-126">Matrix4x4</span><span class="sxs-lookup"><span data-stu-id="e0b69-126">Matrix4x4</span></span> | <span data-ttu-id="e0b69-127">Die Transformationsmatrix auf das Element anwenden</span><span class="sxs-lookup"><span data-stu-id="e0b69-127">The transform matrix to apply to the element</span></span> |
| [<span data-ttu-id="e0b69-128">Scale</span><span class="sxs-lookup"><span data-stu-id="e0b69-128">Scale</span></span>](/uwp/api/windows.ui.xaml.uielement.scale) | <span data-ttu-id="e0b69-129">Vector3</span><span class="sxs-lookup"><span data-stu-id="e0b69-129">Vector3</span></span> | <span data-ttu-id="e0b69-130">Skalieren Sie das Element, auf die CenterPoint zentriert</span><span class="sxs-lookup"><span data-stu-id="e0b69-130">Scale the element, centered on the CenterPoint</span></span> |
| [<span data-ttu-id="e0b69-131">Drehung</span><span class="sxs-lookup"><span data-stu-id="e0b69-131">Rotation</span></span>](/uwp/api/windows.ui.xaml.uielement.rotation) | <span data-ttu-id="e0b69-132">Gleitkomma</span><span class="sxs-lookup"><span data-stu-id="e0b69-132">Float</span></span> | <span data-ttu-id="e0b69-133">Das Element, um die Drehachse und Mittelpunkt drehen</span><span class="sxs-lookup"><span data-stu-id="e0b69-133">Rotate the element around the RotationAxis and CenterPoint</span></span> |
| [<span data-ttu-id="e0b69-134">RotationAxis</span><span class="sxs-lookup"><span data-stu-id="e0b69-134">RotationAxis</span></span>](/uwp/api/windows.ui.xaml.uielement.rotationaxis) | <span data-ttu-id="e0b69-135">Vector3</span><span class="sxs-lookup"><span data-stu-id="e0b69-135">Vector3</span></span> | <span data-ttu-id="e0b69-136">Die Drehachse</span><span class="sxs-lookup"><span data-stu-id="e0b69-136">THe axis of rotation</span></span> |
| [<span data-ttu-id="e0b69-137">CenterPoint</span><span class="sxs-lookup"><span data-stu-id="e0b69-137">CenterPoint</span></span>](/uwp/api/windows.ui.xaml.uielement.centerpoint) | <span data-ttu-id="e0b69-138">Vector3</span><span class="sxs-lookup"><span data-stu-id="e0b69-138">Vector3</span></span> | <span data-ttu-id="e0b69-139">Der Mittelpunkt der Skalierung und Drehung</span><span class="sxs-lookup"><span data-stu-id="e0b69-139">The center point of scale and rotation</span></span> |

<span data-ttu-id="e0b69-140">Der Wert der TransformMatrix-Eigenschaft ist in Kombination mit der Skalierung, Drehung und Übersetzung Eigenschaften in der folgenden Reihenfolge: TransformMatrix, Skalierung, Drehung, Translation.</span><span class="sxs-lookup"><span data-stu-id="e0b69-140">The TransformMatrix property value is combined with the Scale, Rotation, and Translation properties in the following order:  TransformMatrix, Scale, Rotation, Translation.</span></span>

<span data-ttu-id="e0b69-141">Diese Eigenschaften wirken sich nicht auf das Element Layout, also ändern diese Eigenschaften nicht dazu, dass ein neues [Measure](/uwp/api/windows.ui.xaml.uielement.measure)/[Anordnungsübergabe](/uwp/api/windows.ui.xaml.uielement.arrange) .</span><span class="sxs-lookup"><span data-stu-id="e0b69-141">These properties don't affect the element's layout, so modifying these properties does not cause a new [Measure](/uwp/api/windows.ui.xaml.uielement.measure)/[Arrange](/uwp/api/windows.ui.xaml.uielement.arrange) pass.</span></span>

<span data-ttu-id="e0b69-142">Diese Eigenschaften haben den gleichen Zweck und Verhalten, als der gleichnamigen Eigenschaften für die Komposition [Visual](/uwp/api/windows.ui.composition.visual) -Klasse (mit Ausnahme von Übersetzung Visual nicht ist).</span><span class="sxs-lookup"><span data-stu-id="e0b69-142">These properties have the same purpose and behavior as the like-named properties on the composition [Visual](/uwp/api/windows.ui.composition.visual) class (except for Translation, which isn't on Visual).</span></span>

### <a name="example-setting-the-scale-property"></a><span data-ttu-id="e0b69-143">Beispiel: Festlegen der Scale-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e0b69-143">Example: Setting the Scale property</span></span>

<span data-ttu-id="e0b69-144">In diesem Beispiel wird veranschaulicht, wie die Scale-Eigenschaft auf einer Schaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="e0b69-144">This example shows how to set the Scale property on a Button.</span></span>

```xaml
<Button Scale="2,2,1" Content="I am a large button" />
```

```csharp
var button = new Button();
button.Content = "I am a large button";
button.Scale = new Vector3(2.0f,2.0f,1.0f);
```

### <a name="mutual-exclusivity-between-new-and-old-properties"></a><span data-ttu-id="e0b69-145">Gegenseitigen Ausschließlichkeit zwischen neuen und alten Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e0b69-145">Mutual exclusivity between new and old properties</span></span>

> [!NOTE]
> <span data-ttu-id="e0b69-146">Die **Opacity** -Eigenschaft wird die in diesem Abschnitt beschriebenen gegenseitigen Ausschließlichkeit nicht erzwungen.</span><span class="sxs-lookup"><span data-stu-id="e0b69-146">The **Opacity** property does not enforce the mutual exclusivity described in this section.</span></span> <span data-ttu-id="e0b69-147">Sie verwenden die gleiche Opacity-Eigenschaft, ob Sie die Verwendung von XAML oder Komposition Animationen.</span><span class="sxs-lookup"><span data-stu-id="e0b69-147">You use the same Opacity property whether you use XAML or composition animations.</span></span>

<span data-ttu-id="e0b69-148">Die Eigenschaften, die mit einem CompositionAnimation animiert werden können sind Ersatz für mehrere vorhandene UIElement-Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="e0b69-148">The properties that can be animated with a CompositionAnimation are replacements for several existing UIElement properties:</span></span>

- [<span data-ttu-id="e0b69-149">RenderTransform</span><span class="sxs-lookup"><span data-stu-id="e0b69-149">RenderTransform</span></span>](/uwp/api/windows.ui.xaml.uielement.rendertransform)
- [<span data-ttu-id="e0b69-150">RenderTransformOrigin</span><span class="sxs-lookup"><span data-stu-id="e0b69-150">RenderTransformOrigin</span></span>](/uwp/api/windows.ui.xaml.uielement.rendertransformorigin)
- [<span data-ttu-id="e0b69-151">Projection</span><span class="sxs-lookup"><span data-stu-id="e0b69-151">Projection</span></span>](/uwp/api/windows.ui.xaml.uielement.projection)
- [<span data-ttu-id="e0b69-152">Transform3D</span><span class="sxs-lookup"><span data-stu-id="e0b69-152">Transform3D</span></span>](/uwp/api/windows.ui.xaml.uielement.transform3d)

<span data-ttu-id="e0b69-153">Wenn Sie festlegen (oder animieren) der neuen Eigenschaften, können nicht Sie die alten Eigenschaften verwenden.</span><span class="sxs-lookup"><span data-stu-id="e0b69-153">When you set (or animate) any of the new properties, you cannot use the old properties.</span></span> <span data-ttu-id="e0b69-154">Wenn Sie festgelegt (oder animieren) der alten Eigenschaften, können nicht Sie dagegen die neuen Eigenschaften verwenden.</span><span class="sxs-lookup"><span data-stu-id="e0b69-154">Conversely, if you set (or animate) any of the old properties, you cannot use the new properties.</span></span>

<span data-ttu-id="e0b69-155">Sie können nicht die neuen Eigenschaften auch verwenden, wenn Sie ElementCompositionPreview zum Abrufen und Verwalten des visuellen Elements selbst mithilfe der folgenden Methoden verwenden:</span><span class="sxs-lookup"><span data-stu-id="e0b69-155">You also cannot use the new properties if you use ElementCompositionPreview to get and manage the Visual yourself using these methods:</span></span>

- [<span data-ttu-id="e0b69-156">ElementCompositionPreview.GetElementVisual</span><span class="sxs-lookup"><span data-stu-id="e0b69-156">ElementCompositionPreview.GetElementVisual</span></span>](/uwp/api/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual)
- [<span data-ttu-id="e0b69-157">ElementCompositionPreview.SetIsTranslationEnabled</span><span class="sxs-lookup"><span data-stu-id="e0b69-157">ElementCompositionPreview.SetIsTranslationEnabled</span></span>](/uwp/api/windows.ui.xaml.hosting.elementcompositionpreview.setistranslationenabled)

> [!IMPORTANT]
> <span data-ttu-id="e0b69-158">Wenn Sie versuchen, die Verwendung von zwei Gruppen von Eigenschaften mischen bewirkt, dass den API-Aufruf fehl, und erstellen eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e0b69-158">Attempting to mix the use of the two sets of properties will cause the API call to fail and produce an error message.</span></span>

<span data-ttu-id="e0b69-159">Es ist möglich, wechseln aus einer Reihe von Eigenschaften durch deaktivieren, obwohl der Einfachheit halber es nicht empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="e0b69-159">It’s possible to switch from one set of properties by clearing them, though for simplicity it's not recommended.</span></span> <span data-ttu-id="e0b69-160">Wenn die Eigenschaft durch eine "DependencyProperty" unterstützt wird (z. B. UIElement.Projection durch UIElement.ProjectionProperty gesichert ist), rufen Sie dann ClearValue, um sie in den Zustand "nicht verwendete" wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="e0b69-160">If the property is backed by a DependencyProperty (for example, UIElement.Projection is backed by UIElement.ProjectionProperty), then call ClearValue to restore it to its "unused" state.</span></span> <span data-ttu-id="e0b69-161">Andernfalls (z. B. die Scale-Eigenschaft), festlegen die Eigenschaft auf den Standardwert.</span><span class="sxs-lookup"><span data-stu-id="e0b69-161">Otherwise (for example, the Scale property), set the property to its default value.</span></span>

## <a name="animating-uielement-properties-with-compositionanimation"></a><span data-ttu-id="e0b69-162">Animieren von UIElement Eigenschaften mit CompositionAnimation</span><span class="sxs-lookup"><span data-stu-id="e0b69-162">Animating UIElement properties with CompositionAnimation</span></span>

<span data-ttu-id="e0b69-163">Sie können in der Tabelle mit einer CompositionAnimation aufgeführten Renderingeigenschaften animieren.</span><span class="sxs-lookup"><span data-stu-id="e0b69-163">You can animate the rendering properties listed in the table with a CompositionAnimation.</span></span> <span data-ttu-id="e0b69-164">Diese Eigenschaften können auch von einer [ExpressionAnimation](/uwp/api/windows.ui.composition.expressionanimation)verwiesen werden.</span><span class="sxs-lookup"><span data-stu-id="e0b69-164">These properties can also be referenced by an [ExpressionAnimation](/uwp/api/windows.ui.composition.expressionanimation).</span></span>

<span data-ttu-id="e0b69-165">Verwenden Sie die Methoden [StartAnimation](/uwp/api/windows.ui.xaml.uielement.startanimation) und ["stopanimation"](/uwp/api/windows.ui.xaml.uielement.stopanimation) auf UIElement die UIElement-Eigenschaften animieren.</span><span class="sxs-lookup"><span data-stu-id="e0b69-165">Use the [StartAnimation](/uwp/api/windows.ui.xaml.uielement.startanimation) and [StopAnimation](/uwp/api/windows.ui.xaml.uielement.stopanimation) methods on UIElement to animate the UIElement properties.</span></span>

### <a name="example-animating-the-scale-property-with-a-vector3keyframeanimation"></a><span data-ttu-id="e0b69-166">Beispiel: Animieren der Skalierungseigenschaft mit einem Vector3KeyFrameAnimation</span><span class="sxs-lookup"><span data-stu-id="e0b69-166">Example: Animating the Scale property with a Vector3KeyFrameAnimation</span></span>

<span data-ttu-id="e0b69-167">In diesem Beispiel wird veranschaulicht, wie die Skalierung einer Schaltfläche animieren.</span><span class="sxs-lookup"><span data-stu-id="e0b69-167">This example shows how to animate the scale of a Button.</span></span>

```csharp
var compositor = Window.Current.Compositor;
var animation = compositor.CreateVector3KeyFrameAnimation();

animation.InsertKeyFrame(1.0f, new Vector3(2.0f,2.0f,1.0f));
animation.Duration = TimeSpan.FromSeconds(1);
animation.Target = "Scale";

button.StartAnimation(animation);
```

### <a name="example-animating-the-scale-property-with-an-expressionanimation"></a><span data-ttu-id="e0b69-168">Beispiel: Animieren der Skalierungseigenschaft mit einer ExpressionAnimation</span><span class="sxs-lookup"><span data-stu-id="e0b69-168">Example: Animating the Scale property with an ExpressionAnimation</span></span>

<span data-ttu-id="e0b69-169">Eine Seite verfügt über zwei Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="e0b69-169">A page has two buttons.</span></span> <span data-ttu-id="e0b69-170">Die zweite Schaltfläche animiert, um doppelt so groß (über Skalierung) sein wie die erste Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e0b69-170">The second button animates to be twice as large (via scale) as the first button.</span></span>

```xaml
<Button x:Name="sourceButton" Content="Source"/>
<Button x:Name="destinationButton" Content="Destination"/>
```

```csharp
var compositor = Window.Current.Compositor;
var animation = compositor.CreateExpressionAnimation("sourceButton.Scale*2");
animation.SetExpressionReferenceParameter("sourceButton", sourceButton);
animation.Target = "Scale";
destinationButton.StartAnimation(animation);
```

## <a name="related-topics"></a><span data-ttu-id="e0b69-171">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e0b69-171">Related topics</span></span>

- [<span data-ttu-id="e0b69-172">Storyboard-Animationen</span><span class="sxs-lookup"><span data-stu-id="e0b69-172">Storyboarded animations</span></span>](storyboarded-animations.md)
- [<span data-ttu-id="e0b69-173">Benutzung des Visual Layer mit XAML</span><span class="sxs-lookup"><span data-stu-id="e0b69-173">Using the Visual Layer with XAML</span></span>](../../composition/using-the-visual-layer-with-xaml.md)
- [<span data-ttu-id="e0b69-174">Transformationen – Übersicht</span><span class="sxs-lookup"><span data-stu-id="e0b69-174">Transforms overview</span></span>](../layout/transforms.md)