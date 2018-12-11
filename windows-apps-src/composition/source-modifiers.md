---
title: Pull-to-Refresh mit Source-Modifiern
description: Erstellen Sie benutzerdefinierte Pull-to-Refresh-Steuerelemente mit SourceModifiern
ms.date: 10/10/2017
ms.topic: article
keywords: Windows10, Uwp, animation
ms.localizationpriority: medium
ms.openlocfilehash: 834f631cd5c4b8696e75f83f194b95f809b1cf8a
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8899807"
---
# <a name="pull-to-refresh-with-source-modifiers"></a><span data-ttu-id="68bf1-104">Pull-to-Refresh mit Source-Modifiern</span><span class="sxs-lookup"><span data-stu-id="68bf1-104">Pull-to-refresh with source modifiers</span></span>

<span data-ttu-id="68bf1-105">In diesem Artikel gehen wir näher auf die Verwendung des SourceModifier-Features von InteractionTracker ein und demonstrieren dessen Verwendung, indem wir ein benutzerdefiniertes Pull-to-Refresh-Steuerelement erstellen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-105">In this article, we take a deeper dive into how to use an InteractionTracker’s SourceModifier feature and demonstrate its use by creating a custom pull-to-refresh control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68bf1-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="68bf1-106">Prerequisites</span></span>

<span data-ttu-id="68bf1-107">Wir gehen hier davon aus, dass Sie mit den in diesen Artikeln behandelten Konzepten vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="68bf1-107">Here, we assume that you're familiar with the concepts discussed in these articles:</span></span>

- [<span data-ttu-id="68bf1-108">Eingabegesteuerte Animationen</span><span class="sxs-lookup"><span data-stu-id="68bf1-108">Input-driven animations</span></span>](input-driven-animations.md)
- [<span data-ttu-id="68bf1-109">Angepasste Manipulation mit InteractionTracker</span><span class="sxs-lookup"><span data-stu-id="68bf1-109">Custom manipulation experiences with InteractionTracker</span></span>](interaction-tracker-manipulations.md)
- [<span data-ttu-id="68bf1-110">Relationsbasierte Animationen</span><span class="sxs-lookup"><span data-stu-id="68bf1-110">Relation based animations</span></span>](relation-animations.md)

## <a name="what-is-a-sourcemodifier-and-why-are-they-useful"></a><span data-ttu-id="68bf1-111">Was sind SourceModifier und warum sind sie nützlich?</span><span class="sxs-lookup"><span data-stu-id="68bf1-111">What is a SourceModifier and why are they useful?</span></span>

<span data-ttu-id="68bf1-112">Wie [InertiaModifiers](inertia-modifiers.md) ermöglichen SourceModifiers eine feinere Kontrolle über die Bewegung eines InteractionTrackers.</span><span class="sxs-lookup"><span data-stu-id="68bf1-112">Like [InertiaModifiers](inertia-modifiers.md), SourceModifiers give you finer grain control over the motion of an InteractionTracker.</span></span> <span data-ttu-id="68bf1-113">Im Gegensatz zu InertiaModifiers, die die Bewegung definieren, nachdem der InteractionTracker die Trägheit angewendet hat, definieren SourceModifiers die Bewegung, während sich der InteractionTracker noch im Zustand der Interaktion befindet.</span><span class="sxs-lookup"><span data-stu-id="68bf1-113">But unlike InertiaModifiers that define the motion after InteractionTracker enters inertia, SourceModifiers define the motion while InteractionTracker is still in its interacting state.</span></span> <span data-ttu-id="68bf1-114">In diesen Fällen wünschen Sie sich ein anderes Erlebnis als das traditionelle "dem Finger folgen".</span><span class="sxs-lookup"><span data-stu-id="68bf1-114">In these cases, you want a different experience than the traditional "stick to the finger".</span></span>

<span data-ttu-id="68bf1-115">Ein klassisches Beispiel dafür ist das Pull-to-Refresh-Erlebnis: Wenn der Benutzer die Liste zieht, um den Inhalt und die Liste mit der Geschwindigkeit des Fingers zu aktualisieren und nach einer bestimmten Strecke stoppt, würde sich die Bewegung abrupt und mechanisch anfühlen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-115">A classic example of this is the pull-to-refresh experience - when the user pulls the list to refresh the contents and the list pans at the same speed as the finger and stops after a certain distance, the motion would feel abrupt and mechanical.</span></span> <span data-ttu-id="68bf1-116">Ein natürlicheres Erlebnis wäre es, ein Gefühl des Widerstands zu erzeugen, während der Benutzer aktiv mit der Liste interagiert.</span><span class="sxs-lookup"><span data-stu-id="68bf1-116">A more natural experience would be to introduce a feel of resistance while the user actively interacts with the list.</span></span> <span data-ttu-id="68bf1-117">Diese kleine Nuance trägt dazu bei, dass die Interaktion mit einer Liste dynamischer und ansprechender wird.</span><span class="sxs-lookup"><span data-stu-id="68bf1-117">This small nuance helps make the overall end user experience of interacting with a list more dynamic and appealing.</span></span> <span data-ttu-id="68bf1-118">Im Abschnitt „Beispiel“ gehen wir detaillierter darauf ein, wie man dies umsetzen kann.</span><span class="sxs-lookup"><span data-stu-id="68bf1-118">In the Example section, we go into more detail about how to build this.</span></span>

<span data-ttu-id="68bf1-119">Es gibt 2 SourceModifier-Typen:</span><span class="sxs-lookup"><span data-stu-id="68bf1-119">There are 2 types of Source Modifiers:</span></span>

- <span data-ttu-id="68bf1-120">DeltaPosition – Das Delta zwischen der aktuellen Frame-Position und der vorherigen Frame-Position des Fingers während der Schwenken-Interaktion per Touch.</span><span class="sxs-lookup"><span data-stu-id="68bf1-120">DeltaPosition – is the delta between the current frame position and the previous frame position of the finger during the touch pan interaction.</span></span> <span data-ttu-id="68bf1-121">Mit diesem Source-Modifier können Sie die Delta-Position der Interaktion verändern, bevor Sie sie zur weiteren Verarbeitung senden.</span><span class="sxs-lookup"><span data-stu-id="68bf1-121">This source modifier allows you to modify the delta position of the interaction before sending it for further processing.</span></span> <span data-ttu-id="68bf1-122">Dies ist ein Parameter vom Typ Vector3 und der Entwickler kann wählen, ob er die X-, Y- oder Z-Attribute der Position ändern will, bevor er sie an den InteractionTracker übergibt.</span><span class="sxs-lookup"><span data-stu-id="68bf1-122">This is a Vector3 type parameter and the developer can choose to modify any of the X or Y or Z attributes of the position before passing it to the InteractionTracker.</span></span>
- <span data-ttu-id="68bf1-123">DeltaScale - Das Delta zwischen dem aktuellen Frame-Maßstab und dem vorherigen Frame-Maßstab, das während der Touch-Zoom-Interaktion angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="68bf1-123">DeltaScale - is the delta between the current frame scale and the previous frame scale that was applied during the touch zoom interaction.</span></span> <span data-ttu-id="68bf1-124">Mit diesem Source-Modifier können Sie die Zoomstufe der Interaktion verändern.</span><span class="sxs-lookup"><span data-stu-id="68bf1-124">This source modifier allows you to modify the zooming level of the interaction.</span></span> <span data-ttu-id="68bf1-125">Dies ist ein Float-Attribut, das der Entwickler modifizieren kann, bevor er es an den InteractionTracker übergibt.</span><span class="sxs-lookup"><span data-stu-id="68bf1-125">This is a float type attribute that the developer can modify before passing it to the InteractionTracker.</span></span>

<span data-ttu-id="68bf1-126">Wenn sich InteractionTracker im Zustand „Interacting“ befindet, wertet er jeden ihm zugeordneten Source-Modifier aus und stellt fest, ob einer von ihnen zutrifft.</span><span class="sxs-lookup"><span data-stu-id="68bf1-126">When InteractionTracker is in its Interacting state, it evaluates each of the Source Modifiers assigned to it and determines if any of them apply.</span></span> <span data-ttu-id="68bf1-127">Das bedeutet, dass Sie mehrere Source-Modifier erstellen und einem InteractionTracker zuweisen können.</span><span class="sxs-lookup"><span data-stu-id="68bf1-127">This means you can create and assign multiple Source Modifiers to an InteractionTracker.</span></span> <span data-ttu-id="68bf1-128">Bei der Definition eines jeden müssen Sie jedoch Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="68bf1-128">But, when defining each, you need to do the following:</span></span>

1. <span data-ttu-id="68bf1-129">Definieren Sie die Bedingung – ein Ausdruck, der die bedingte Anweisung definiert, bei der dieser spezifische Source-Modifier angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="68bf1-129">Define the Condition – an Expression that defines the conditional statement when this specific Source Modifier should be applied.</span></span>
1. <span data-ttu-id="68bf1-130">Definieren Sie DeltaPosition/DeltaScale – Der Source-Modifier, der die DeltaPosition oder DeltaScale ändert, wenn die oben definierte Bedingung erfüllt ist.</span><span class="sxs-lookup"><span data-stu-id="68bf1-130">Define the DeltaPosition/DeltaScale – The source modifier expression that alters the DeltaPosition or DeltaScale when the above defined condition is met.</span></span>

## <a name="example"></a><span data-ttu-id="68bf1-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="68bf1-131">Example</span></span>

<span data-ttu-id="68bf1-132">Sehen wir uns nun an, wie Sie Source-Modifier verwenden können, um ein benutzerdefiniertes Pull-to-Refresh-Erlebnis mit einem bestehenden XAML ListView-Steuerelement zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-132">Now let’s look at how you can use Source Modifiers to create a custom pull-to-refresh experience with an existing XAML ListView Control.</span></span> <span data-ttu-id="68bf1-133">Wir werden ein Canvas als „Refresh-Panel“ verwenden, das auf einem XAML ListView gestapelt wird.</span><span class="sxs-lookup"><span data-stu-id="68bf1-133">We will be using a Canvas as the “Refresh Panel” that will be stacked on top of a XAML ListView to build this experience.</span></span>

<span data-ttu-id="68bf1-134">Für die Endbenutzererfahrung möchten wir den Effekt des „Widerstandes“ erzeugen, da der Benutzer die Liste aktiv (mit Berührung) schwenkt und das Schwenken stoppt, nachdem die Position einen bestimmten Punkt überschritten hat.</span><span class="sxs-lookup"><span data-stu-id="68bf1-134">For the end user experience, we want to create the effect of "resistance" as the user is actively panning the list (with touch) and stop panning after the position goes beyond a certain point.</span></span>

![Liste mit Pull-to-Refresh](images/animation/city-list.gif)

<span data-ttu-id="68bf1-136">Den Arbeitscode für diese Erfahrung finden Sie im [Window UI Dev Labs-Repo auf GitHub](https://github.com/Microsoft/WindowsUIDevLabs).</span><span class="sxs-lookup"><span data-stu-id="68bf1-136">The working code for this experience can be found in the [Window UI Dev Labs repo on GitHub](https://github.com/Microsoft/WindowsUIDevLabs).</span></span> <span data-ttu-id="68bf1-137">Hier ist die exemplarische Vorgehensweise zum Erstellen der Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="68bf1-137">Here is the step-by-step walk through of building that experience.</span></span>
<span data-ttu-id="68bf1-138">In Ihrem XAML-Markup-Code haben Sie folgendes:</span><span class="sxs-lookup"><span data-stu-id="68bf1-138">In your XAML markup code, you have the following:</span></span>

```xaml
<StackPanel Height="500" MaxHeight="500" x:Name="ContentPanel" HorizontalAlignment="Left" VerticalAlignment="Top" >
 <Canvas Width="400" Height="100" x:Name="RefreshPanel" >
<Image x:Name="FirstGear" Source="ms-appx:///Assets/Loading.png" Width="20" Height="20" Canvas.Left="200" Canvas.Top="70"/>
 </Canvas>
 <ListView x:Name="ThumbnailList"
 MaxWidth="400"
 Height="500"
ScrollViewer.VerticalScrollMode="Enabled" ScrollViewer.IsScrollInertiaEnabled="False" ScrollViewer.IsVerticalScrollChainingEnabled="True" >
 <ListView.ItemTemplate>
 ……
 </ListView.ItemTemplate>
 </ListView>
</StackPanel>
```

<span data-ttu-id="68bf1-139">Da es sich bei dem ListView (`ThumbnailList`) um ein XAML-Steuerelement handelt, das bereits scrollt, müssen Sie das Scrolling mit dem übergeordneten Element (`ContentPanel`) verknüpfen, wenn es das oberste Element erreicht und nicht mehr scrollen kann.</span><span class="sxs-lookup"><span data-stu-id="68bf1-139">Because the ListView (`ThumbnailList`) is a XAML control that already scrolls, you need the scrolling to be chained up to its parent (`ContentPanel`) when it reaches the topmost item and can’t scroll anymore.</span></span> <span data-ttu-id="68bf1-140">(ContentPanel ist der Ort, an dem Sie die Source-Modifier anwenden werden.) Dazu müssen Sie ScrollViewer.IsVerticalScrollChainingEnabled im ListView-Markup auf **true** setzen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-140">(ContentPanel is where you will apply the Source Modifiers.) For this to happen you need to set ScrollViewer.IsVerticalScrollChainingEnabled to **true** in the ListView markup.</span></span> <span data-ttu-id="68bf1-141">Außerdem müssen Sie den Verkettungsmodus in VisualInteractionSource auf **Always** setzen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-141">You will also need to set the chaining mode on the VisualInteractionSource to **Always**.</span></span>

<span data-ttu-id="68bf1-142">Sie müssen den PointerPressedEvent-Handler mit dem _handlingEventsToo_-Parameter auf **true** setzen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-142">You need to set PointerPressedEvent handler with the _handledEventsToo_ parameter as **true**.</span></span> <span data-ttu-id="68bf1-143">Ohne diese Option wird PointerPressedEvent nicht mit ContentPanel verkettet, da das ListView-Steuerelement diese Ereignisse als behandelt markiert und sie nicht über die visuelle Verkettung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="68bf1-143">Without this option, the PointerPressedEvent will not be chained to the ContentPanel as the ListView control will mark those events as handled and they will not be sent up the visual chain.</span></span>

```csharp
//The PointerPressed handler needs to be added using AddHandler method with the //handledEventsToo boolean set to "true"
//instead of the XAML element's "PointerPressed=Window_PointerPressed",
//because the list view needs to chain PointerPressed handled events as well.
ContentPanel.AddHandler(PointerPressedEvent, new PointerEventHandler( Window_PointerPressed), true);
```

<span data-ttu-id="68bf1-144">Jetzt sind Sie bereit, dies mit InteractionTracker zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-144">Now, you're ready to tie this with InteractionTracker.</span></span> <span data-ttu-id="68bf1-145">Beginnen Sie mit der Einrichtung von InteractionTracker, VisualInteractionSource und dem Ausdruck, der die Position von InteractionTracker nutzt.</span><span class="sxs-lookup"><span data-stu-id="68bf1-145">Start by setting up InteractionTracker, the VisualInteractionSource and the Expression that will leverage the position of InteractionTracker.</span></span>

```csharp
// InteractionTracker and VisualInteractionSource setup.
_root = ElementCompositionPreview.GetElementVisual(Root);
_compositor = _root.Compositor;
_tracker = InteractionTracker.Create(_compositor);
_interactionSource = VisualInteractionSource.Create(_root);
_interactionSource.PositionYSourceMode = InteractionSourceMode.EnabledWithInertia;
_interactionSource.PositionYChainingMode = InteractionChainingMode.Always;
_tracker.InteractionSources.Add(_interactionSource);
float refreshPanelHeight = (float)RefreshPanel.ActualHeight;
_tracker.MaxPosition = new Vector3((float)Root.ActualWidth, 0, 0);
_tracker.MinPosition = new Vector3(-(float)Root.ActualWidth, -refreshPanelHeight, 0);

// Use the Tacker's Position (negated) to apply to the Offset of the Image.
// The -{refreshPanelHeight} is to hide the refresh panel
m_positionExpression = _compositor.CreateExpressionAnimation($"-tracker.Position.Y - {refreshPanelHeight} ");
m_positionExpression.SetReferenceParameter("tracker", _tracker);
_contentPanelVisual.StartAnimation("Offset.Y", m_positionExpression);
```

<span data-ttu-id="68bf1-146">Bei dieser Einstellung befindet sich das Refresh-Panel außerhalb des Ansichtsfensters in seiner Ausgangsposition und alles was der Benutzer sieht ist das ListView. Wenn das Schwenken das ContentPanel erreicht, wird das PointerPressed-Ereignis ausgelöst, bei dem Sie das System auffordern, InteractionTracker zu verwenden, um das Manipulationserlebnis zu steuern.</span><span class="sxs-lookup"><span data-stu-id="68bf1-146">With this set up, the refresh panel is out of the viewport in its starting position and all the user sees is the listView When the panning reaches the ContentPanel, the PointerPressed event will be fired, where you ask the System to use InteractionTracker to drive the manipulation experience.</span></span>

```csharp
private void Window_PointerPressed(object sender, PointerRoutedEventArgs e)
{
if (e.Pointer.PointerDeviceType == Windows.Devices.Input.PointerDeviceType.Touch) {
 // Tell the system to use the gestures from this pointer point (if it can).
 _interactionSource.TryRedirectForManipulation(e.GetCurrentPoint(null));
 }
}
```

> [!NOTE]
> <span data-ttu-id="68bf1-147">Wenn das Verketten von behandelten Ereignissen nicht benötigt wird, kann der PointerPressedEvent-Handler mit dem Attribut (`PointerPressed="Window_PointerPressed"`) direkt über das XAML-Markup hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="68bf1-147">If chaining Handled events is not needed, adding PointerPressedEvent handler can be done directly through XAML markup using the attribute (`PointerPressed="Window_PointerPressed"`).</span></span>

<span data-ttu-id="68bf1-148">Der nächste Schritt ist das Einrichten der Source-Modifier.</span><span class="sxs-lookup"><span data-stu-id="68bf1-148">The next step is to set up the source modifiers.</span></span> <span data-ttu-id="68bf1-149">Sie werden zwei Source-Modifier verwenden, um dieses Verhalten zu erreichen: _Resistance_ und _Stop_.</span><span class="sxs-lookup"><span data-stu-id="68bf1-149">You will be using 2 source modifiers to get this behavior; _Resistance_ and _Stop_.</span></span>

- <span data-ttu-id="68bf1-150">Resistance – Bewegen Sie die DeltaPosition Y mit halber Geschwindigkeit, bis sie die Höhe des RefreshPanels erreicht.</span><span class="sxs-lookup"><span data-stu-id="68bf1-150">Resistance – Move the DeltaPosition.Y at half the speed until it reaches the height of the RefreshPanel.</span></span>

```csharp
CompositionConditionalValue resistanceModifier = CompositionConditionalValue.Create (_compositor);
ExpressionAnimation resistanceCondition = _compositor.CreateExpressionAnimation(
 $"-tracker.Position.Y < {pullToRefreshDistance}");
resistanceCondition.SetReferenceParameter("tracker", _tracker);
ExpressionAnimation resistanceAlternateValue = _compositor.CreateExpressionAnimation(
 "source.DeltaPosition.Y / 3");
resistanceAlternateValue.SetReferenceParameter("source", _interactionSource);
resistanceModifier.Condition = resistanceCondition;
resistanceModifier.Value = resistanceAlternateValue;
```

- <span data-ttu-id="68bf1-151">Stop – Stoppen Sie die Bewegung, nachdem das gesamte RefreshPanel auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="68bf1-151">Stop – Stop moving after the entire RefreshPanel is on the screen.</span></span>

```csharp
CompositionConditionalValue stoppingModifier = CompositionConditionalValue.Create (_compositor);
ExpressionAnimation stoppingCondition = _compositor.CreateExpressionAnimation(
 $"-tracker.Position.Y >= {pullToRefreshDistance}");
stoppingCondition.SetReferenceParameter("tracker", _tracker);
ExpressionAnimation stoppingAlternateValue = _compositor.CreateExpressionAnimation("0");
stoppingModifier.Condition = stoppingCondition;
stoppingModifier.Value = stoppingAlternateValue;
Now add the 2 source modifiers to the InteractionTracker.
List<CompositionConditionalValue> modifierList = new List<CompositionConditionalValue>()
{ resistanceModifier, stoppingModifier };
_interactionSource.ConfigureDeltaPositionYModifiers(modifierList);
```

<span data-ttu-id="68bf1-152">Dieses Diagramm zeigt eine Visualisierung des SourceModifiers-Setups.</span><span class="sxs-lookup"><span data-stu-id="68bf1-152">This diagram gives a visualization of the SourceModifiers setup.</span></span>

![Schwenken-Diagramm](images/animation/source-modifiers-diagram.png)

<span data-ttu-id="68bf1-154">Mit den SourceModifiers werden Sie beim Schwenken der ListView nach unten und dem Erreichen des obersten Elemente bemerken, dass das Refresh-Panel mit der halben Geschwindigkeit des Schwenkens heruntergezogen wird, bis es die Höhe von RefreshPanels erreicht. Dann stoppt die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="68bf1-154">Now with the SourceModifiers, you will notice when panning the ListView down and reach the topmost item, the refresh panel is pulled down at half the pace of the pan until it reaches the RefreshPanel height and then stops moving.</span></span>

<span data-ttu-id="68bf1-155">Im vollständigen Beispiel wird eine Keyframe-Animation verwendet, um ein Symbol während der Interaktion im RefreshPanel zu drehen.</span><span class="sxs-lookup"><span data-stu-id="68bf1-155">In the full sample, a keyframe animation is used to spin an icon during interaction in the RefreshPanel canvas.</span></span> <span data-ttu-id="68bf1-156">Jeder Inhalt kann stattdessen werden oder die Position von InteractionTracker nutzen, um diese Animation separat zu steuern.</span><span class="sxs-lookup"><span data-stu-id="68bf1-156">Any content can be used in its place or utilize InteractionTracker’s position to drive that animation separately.</span></span>
