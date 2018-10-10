---
author: jaster
ms.assetid: b7a4ac8a-d91e-461b-a060-cc6fcea8e778
title: Benutzung des Visual Layer mit XAML
description: Lernen Sie Methoden für die Verwendung der Visual Layer APIs in Kombination mit existierendem XAML-Inhalten kennen, um Animationen und fortgeschrittene Effekte zu erzeugen.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d45881ace6be3b0af88f14692837e96ab9b58d18
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4502688"
---
# <a name="using-the-visual-layer-with-xaml"></a><span data-ttu-id="19c53-104">Benutzung des Visual Layer mit XAML</span><span class="sxs-lookup"><span data-stu-id="19c53-104">Using the Visual Layer with XAML</span></span>

<span data-ttu-id="19c53-105">Die meisten Apps, die die Visual-Layer-Funktionen nutzen, verwenden XAML, um den Hauptinhalt der Benutzeroberfläche zu definieren.</span><span class="sxs-lookup"><span data-stu-id="19c53-105">Most apps that consume Visual Layer capabilities will use XAML to define the main UI content.</span></span> <span data-ttu-id="19c53-106">Im Rahmen des Windows 10 Anniversary Update sind neue Features im XAML-Framework und dem Visual Layer erschienen, die es einfacher machen, diese beiden Technologien zum Erstellen beeindruckender Erlebnisse für den Benutzer kombinieren.</span><span class="sxs-lookup"><span data-stu-id="19c53-106">In the Windows 10 Anniversary Update, there are new features in the XAML framework and the Visual Layer that make it easier to combine these two technologies to create stunning user experiences.</span></span>
<span data-ttu-id="19c53-107">Funktionen von XAML und Visual Layer "Interop" kann zum Erstellen von erweiterten Animationen und Effekte nicht allein mithilfe von XAML-API verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="19c53-107">XAML and Visual Layer interop functionality can be used to create advanced animations and effects not available using XAML APIs alone.</span></span> <span data-ttu-id="19c53-108">Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="19c53-108">This includes:</span></span>

- <span data-ttu-id="19c53-109">Pinseleffekte wie Weichzeichnen und Milchglas</span><span class="sxs-lookup"><span data-stu-id="19c53-109">Brush effects like blur and frosted glass</span></span>
- <span data-ttu-id="19c53-110">Dynamische Beleuchtungseffekte</span><span class="sxs-lookup"><span data-stu-id="19c53-110">Dynamic lighting effects</span></span>
- <span data-ttu-id="19c53-111">Durch Scrollen gesteuerte Animationen und Parallax-Bildlauf</span><span class="sxs-lookup"><span data-stu-id="19c53-111">Scroll driven animations and parallax</span></span>
- <span data-ttu-id="19c53-112">Automatische Layout-Animationen</span><span class="sxs-lookup"><span data-stu-id="19c53-112">Automatic layout animations</span></span>
- <span data-ttu-id="19c53-113">Pixelperfekte Schlagschatten</span><span class="sxs-lookup"><span data-stu-id="19c53-113">Pixel-perfect drop shadows</span></span>

<span data-ttu-id="19c53-114">Diese Effekte und Animationen können auf vorhandenen XAML-Inhalt angewendet werden, damit Sie Ihre XAML-App nicht erheblich umstrukturieren müssen, um neue Funktionen nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="19c53-114">These effects and animations can be applied to existing XAML content, so you don't have to dramatically restructure your XAML app to take advantage of the new functionality.</span></span>
<span data-ttu-id="19c53-115">Layoutanimationen, Schatten und Effekte für Unschärfe werden im folgenden Rezepteabschnitt behandelt.</span><span class="sxs-lookup"><span data-stu-id="19c53-115">Layout animations, shadows, and blur effects are covered in the Recipes section below.</span></span> <span data-ttu-id="19c53-116">Ein Codebeispiel, das Parallax implementiert, finden Sie unter [ParallaxingListItems sample](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2010586/ParallaxingListItems).</span><span class="sxs-lookup"><span data-stu-id="19c53-116">For a code sample implementing parallax, see the [ParallaxingListItems sample](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2010586/ParallaxingListItems).</span></span> <span data-ttu-id="19c53-117">Die [WindowsUIDevLabs Repository](https://github.com/Microsoft/WindowsUIDevLabs) verfügt außerdem über weitere Beispiele für die Implementierung von Animationen, Schatten und Effekte.</span><span class="sxs-lookup"><span data-stu-id="19c53-117">The [WindowsUIDevLabs repository](https://github.com/Microsoft/WindowsUIDevLabs) also has several other samples for implementing animations, shadows and effects.</span></span>

## <a name="the-xamlcompositionbrushbase-class"></a><span data-ttu-id="19c53-118">Die XamlCompositionBrushBase-Klasse</span><span class="sxs-lookup"><span data-stu-id="19c53-118">The XamlCompositionBrushBase class</span></span>

<span data-ttu-id="19c53-119">**XamlCompositionBrush** bietet eine Basisklasse für XAML-Pinsel, die einen Bereich mit einem **CompositionBrush** zeichnen.</span><span class="sxs-lookup"><span data-stu-id="19c53-119">**XamlCompositionBrush** provides a base class for XAML brushes that paint an area with a **CompositionBrush**.</span></span> <span data-ttu-id="19c53-120">Damit können problemlos Kompositionseffekte wie Weichzeichnen oder Milchglas für XAML-UI-Elemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="19c53-120">This can be used to easily apply composition effects like blur or frosted glass to XAML UI elements.</span></span>

<span data-ttu-id="19c53-121">Weitere Informationen zum Verwenden von Pinseln mit XAML-UI finden Sie im Abschnitt [**Pinsel**](/windows/uwp/design/style/brushes#xamlcompositionbrushbase).</span><span class="sxs-lookup"><span data-stu-id="19c53-121">See the [**Brushes**](/windows/uwp/design/style/brushes#xamlcompositionbrushbase) section for more info on using brushes with XAML UI.</span></span>

<span data-ttu-id="19c53-122">Codebeispiele finden Sie auf der Referenzseite für [**XamlCompositionBrushBase**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).</span><span class="sxs-lookup"><span data-stu-id="19c53-122">For code examples, see the reference page for [**XamlCompositionBrushBase**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).</span></span>

## <a name="the-xamllight-class"></a><span data-ttu-id="19c53-123">Die XamlLight-Klasse</span><span class="sxs-lookup"><span data-stu-id="19c53-123">The XamlLight class</span></span>

<span data-ttu-id="19c53-124">**XamlLight** bietet eine Basisklasse für XAML-Beleuchtungseffekte, die dynamisch einen Bereich mit **CompositionLight** beleuchten.</span><span class="sxs-lookup"><span data-stu-id="19c53-124">**XamlLight** provides a base class for XAML lighting effects that dynamically light an area with a **CompositionLight**.</span></span>

<span data-ttu-id="19c53-125">Weitere Informationen zur Verwendung von Licht, einschließlich der Beleuchtung von XAML-UI-Elementen, finden Sie im Abschnitt [**Beleuchtung**](xaml-lighting.md).</span><span class="sxs-lookup"><span data-stu-id="19c53-125">See the [**Lighting**](xaml-lighting.md) section for more info on using lights, including lighting XAML UI elements.</span></span>

<span data-ttu-id="19c53-126">Codebeispiele finden Sie auf der Referenzseite für [**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight).</span><span class="sxs-lookup"><span data-stu-id="19c53-126">For code examples, see the reference page for [**XamlLight**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamllight).</span></span>

## <a name="the-elementcompositionpreview-class"></a><span data-ttu-id="19c53-127">Die ElementCompositionPreview-Klasse</span><span class="sxs-lookup"><span data-stu-id="19c53-127">The ElementCompositionPreview class</span></span>

<span data-ttu-id="19c53-128">[**ElementCompositionPreview**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.aspx) ist eine statische Klasse, die Kompatibilität mit XAML- und Visual Layer-Funktionalitäten bietet.</span><span class="sxs-lookup"><span data-stu-id="19c53-128">[**ElementCompositionPreview**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.aspx) is a static class that provides XAML and Visual Layer interop functionality.</span></span> <span data-ttu-id="19c53-129">Eine Übersicht über die visuelle Ebene und die zugehörige Funktionalität finden Sie unter [Visual Layer](https://msdn.microsoft.com/windows/uwp/graphics/visual-layer).</span><span class="sxs-lookup"><span data-stu-id="19c53-129">For an overview of the Visual Layer and its functionality, see [Visual Layer](https://msdn.microsoft.com/windows/uwp/graphics/visual-layer).</span></span> <span data-ttu-id="19c53-130">Die **ElementCompositionPreview** Klasse bietet die folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="19c53-130">The **ElementCompositionPreview** class provides the following methods:</span></span>

-   <span data-ttu-id="19c53-131">[**GetElementVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Erhalten Sie eine „Handout“-Grafik, die verwendet wurde, um dieses Element zu rendern</span><span class="sxs-lookup"><span data-stu-id="19c53-131">[**GetElementVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Get a "handout" Visual that is used to render this element</span></span>
-   <span data-ttu-id="19c53-132">[**SetElementChildVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.setelementchildvisual.aspx): Legt ein "handin" Visual als untersten Ordner in der Struktur dieses Elements fest.</span><span class="sxs-lookup"><span data-stu-id="19c53-132">[**SetElementChildVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.setelementchildvisual.aspx): Sets a "handin" Visual as the last child of this element’s visual tree.</span></span> <span data-ttu-id="19c53-133">Dieses Visual wird über den Rest des Elements gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="19c53-133">This Visual will draw on top of the rest of the element.</span></span> 
-   <span data-ttu-id="19c53-134">[**GetElementChildVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Rufen Sie das Visual Set ab, indem Sie **SetElementChildVisual** benutzen</span><span class="sxs-lookup"><span data-stu-id="19c53-134">[**GetElementChildVisual**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Retrieve the Visual set using **SetElementChildVisual**</span></span>
-   <span data-ttu-id="19c53-135">[**GetScrollViewerManipulationPropertySet**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Erhalten Sie ein Objekt, das zur Erstellung von Animationen mit 60fps basierend auf der Scrollposition in einem **ScrollViewer** verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="19c53-135">[**GetScrollViewerManipulationPropertySet**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.hosting.elementcompositionpreview.getelementvisual.aspx): Get an object that can be used to create 60fps animations based on scroll offset in a **ScrollViewer**</span></span>

## <a name="remarks-on-elementcompositionpreviewgetelementvisual"></a><span data-ttu-id="19c53-136">Hinweise auf ElementCompositionPreview.GetElementVisual</span><span class="sxs-lookup"><span data-stu-id="19c53-136">Remarks on ElementCompositionPreview.GetElementVisual</span></span>

<span data-ttu-id="19c53-137">**ElementCompositionPreview.GetElementVisual** gibt ein "handout" Visual aus, das benutzt wird, um das gegebene **UIElement** zu rendern.</span><span class="sxs-lookup"><span data-stu-id="19c53-137">**ElementCompositionPreview.GetElementVisual** returns a “handout” Visual that is used to render the given **UIElement**.</span></span> <span data-ttu-id="19c53-138">Eigenschaften wie z. B. **Visual.Opacity**, **Visual.Offset** und **Visual.Size** werden durch das XAML-Framework, das auf den Zustand des UIElements basiert, festgelegt.</span><span class="sxs-lookup"><span data-stu-id="19c53-138">Properties such as **Visual.Opacity**, **Visual.Offset**, and **Visual.Size** are set by the XAML framework based on the state of the UIElement.</span></span> <span data-ttu-id="19c53-139">Dies kann Techniken wie implizite Repositionierungsanimationen (siehe *Rezepte*) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="19c53-139">This enables techniques such as implicit reposition animations (see *Recipes*).</span></span>

<span data-ttu-id="19c53-140">Hinweis: Weil der **Offset** und die **Größe** als Ergebnis des Layouts des XAML-Frameworks festgelegt sind, Entwickler vorsichtig sein sollten, wenn sie diese Eigenschaften animieren oder ändern.</span><span class="sxs-lookup"><span data-stu-id="19c53-140">Note that since **Offset** and **Size** are set as the result of XAML framework layout, developers should be careful when modifying or animating these properties.</span></span> <span data-ttu-id="19c53-141">Entwickler sollten den Offset ändern oder animieren, wenn die obere linke Ecke des Elements dieselbe Position hat, wie die des übergeordneten Elements im Layout.</span><span class="sxs-lookup"><span data-stu-id="19c53-141">Developers should only modify or animate Offset when the element’s top-left corner has the same position as that of its parent in layout.</span></span> <span data-ttu-id="19c53-142">Die Größe sollte im Allgemeinen nicht geändert werden, jedoch kann der Zugriff auf die Eigenschaft hilfreich sein.</span><span class="sxs-lookup"><span data-stu-id="19c53-142">Size should generally not be modified, but accessing the property may be useful.</span></span> <span data-ttu-id="19c53-143">Beispielsweise verwenden die folgenden Schlagschatten und Milchglas-Samples unten die Größe eines Handout Visuals als Eingabe für eine Animation.</span><span class="sxs-lookup"><span data-stu-id="19c53-143">For example, the Drop Shadow and Frosted Glass samples below use Size of a handout Visual as input to an animation.</span></span>

<span data-ttu-id="19c53-144">Als weitere Sicherheit werden aktualisierte Eigenschaften des Handout Visuals nicht im entsprechenden UIElement widergespiegelt.</span><span class="sxs-lookup"><span data-stu-id="19c53-144">As an additional caveat, updated properties of the handout Visual will not be reflected in the corresponding UIElement.</span></span> <span data-ttu-id="19c53-145">Also wird beispielsweise das Einstellen der **UIElement.Opacity** auf 0,5 die Deckkraft des entsprechende Handout Visuals auf 0,5 festlegen.</span><span class="sxs-lookup"><span data-stu-id="19c53-145">So for example, setting **UIElement.Opacity** to 0.5 will set the corresponding handout Visual’s Opacity to 0.5.</span></span> <span data-ttu-id="19c53-146">Das Festlegen der Deckkraft das Handout Visuals **Opacity** auf 0,5 bewirkt, dass der Inhalt mit 50 % Deckkraft angezeigt wird, aber es wird sich nicht auf die entsprechende UIElement Opacity-Eigenschaft auswirken.</span><span class="sxs-lookup"><span data-stu-id="19c53-146">However, setting the handout Visual’s **Opacity** to 0.5 will cause the content to appear at 50% opacity, but will not change the value of the corresponding UIElement’s Opacity property.</span></span>

### <a name="example-of-offset-animation"></a><span data-ttu-id="19c53-147">Beispiel für **Offset** Animation</span><span class="sxs-lookup"><span data-stu-id="19c53-147">Example of **Offset** animation</span></span>

#### <a name="incorrect"></a><span data-ttu-id="19c53-148">Falsch</span><span class="sxs-lookup"><span data-stu-id="19c53-148">Incorrect</span></span>

```xaml
<Border>
      <Image x:Name="MyImage" Margin="5" />
</Border>
```

```csharp
// Doesn’t work because Image has a margin!
ElementCompositionPreview.GetElementVisual(MyImage).StartAnimation("Offset", parallaxAnimation);
```

#### <a name="correct"></a><span data-ttu-id="19c53-149">Richtig</span><span class="sxs-lookup"><span data-stu-id="19c53-149">Correct</span></span>

```xaml
<Border>
    <Canvas Margin="5">
        <Image x:Name="MyImage" />
    </Canvas>
</Border>
```

```csharp
// This works because the Canvas parent doesn’t generate a layout offset.
ElementCompositionPreview.GetElementVisual(MyImage).StartAnimation("Offset", parallaxAnimation);
```

## <a name="the-elementcompositionpreviewsetelementchildvisual-method"></a><span data-ttu-id="19c53-150">Die **ElementCompositionPreview.SetElementChildVisual** Methode</span><span class="sxs-lookup"><span data-stu-id="19c53-150">The **ElementCompositionPreview.SetElementChildVisual** method</span></span>

<span data-ttu-id="19c53-151">**ElementCompositionPreview.SetElementChildVisual** erlaubt es den Entwicklern, ein "Handin"-Visual zu einzubinden, welches als Teil des Visual Trees des Elements erscheinen wird.</span><span class="sxs-lookup"><span data-stu-id="19c53-151">**ElementCompositionPreview.SetElementChildVisual** allows the developer to supply a “handin” Visual that will appear as part of an element’s Visual Tree.</span></span> <span data-ttu-id="19c53-152">Dies ermöglicht Entwicklern das Erstellen einer "Kompositions-Insel", in denen Visual-basierter Inhalt innerhalb einer XAML-UI angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="19c53-152">This allows developers to create a “Composition Island” where Visual-based content can appear inside a XAML UI.</span></span> <span data-ttu-id="19c53-153">Entwickler sollten diese Technik jedoch vorsichtig einsetzen, da Visual-basierter Inhalt nicht dieselben Zugriffsmöglichkeiten und Garantien durch Benutzererfahrungen wie XAML-Inhalte haben.</span><span class="sxs-lookup"><span data-stu-id="19c53-153">Developers should be conservative about using this technique because Visual-based content will not have the same accessibility and user experience guarantees of XAML content.</span></span> <span data-ttu-id="19c53-154">Daher ist es im Allgemeinen empfehlenswert, dieses Verfahren nur bei Bedarf zur Implementierung benutzerdefinierter Effekte genutzt wird, wie die nachfolgend im Rezeptabschnitt enthaltenen.</span><span class="sxs-lookup"><span data-stu-id="19c53-154">Therefore, it is generally recommended that this technique only be used when necessary to implement custom effects such as those found in the Recipes section below.</span></span>

## <a name="getalphamask-methods"></a><span data-ttu-id="19c53-155">**GetAlphaMask** Methoden</span><span class="sxs-lookup"><span data-stu-id="19c53-155">**GetAlphaMask** methods</span></span>

<span data-ttu-id="19c53-156">[**Image**](https://msdn.microsoft.com/library/windows/apps/br242752), [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652), und [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) implementieren jede eine Methode, die **GetAlphaMask** genannt wird, welche eine **CompositionBrush** ausgibt, die ein Graustufenbild in der Form des Elements darstellt.</span><span class="sxs-lookup"><span data-stu-id="19c53-156">[**Image**](https://msdn.microsoft.com/library/windows/apps/br242752), [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652), and [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) each implement a method called **GetAlphaMask** that returns a **CompositionBrush** representing a grayscale image with the shape of the element.</span></span> <span data-ttu-id="19c53-157">Dieser **CompositionBrush** kann als Eingabe für eine Komposition **DropShadow** dienen, also kann der Schatten die Form des Elements anstelle eines Rechtecks haben.</span><span class="sxs-lookup"><span data-stu-id="19c53-157">This **CompositionBrush** can serve as an input for a Composition **DropShadow**, so the shadow can reflect the shape of the element instead of a rectangle.</span></span> <span data-ttu-id="19c53-158">Das ermöglicht auf Pixel abgestimmte, Konturbasierte Schatten für Text, Bilder mit Alpha und Formen.</span><span class="sxs-lookup"><span data-stu-id="19c53-158">This enables pixel perfect, contour-based shadows for text, images with alpha, and shapes.</span></span> <span data-ttu-id="19c53-159">Sie können unter *Schlagschatten* im Folgenden ein Beispiel für diese API finden.</span><span class="sxs-lookup"><span data-stu-id="19c53-159">See *Drop Shadow* below for an example of this API.</span></span>

## <a name="recipes"></a><span data-ttu-id="19c53-160">Rezepte</span><span class="sxs-lookup"><span data-stu-id="19c53-160">Recipes</span></span>

### <a name="reposition-animation"></a><span data-ttu-id="19c53-161">Repositionierungsanimation</span><span class="sxs-lookup"><span data-stu-id="19c53-161">Reposition animation</span></span>

<span data-ttu-id="19c53-162">Indem er die Komposition impliziter Animationen nutzt, kann Entwickler automatisch Änderungen im Layout eines Elements relativ zum übergeordneten Element animieren.</span><span class="sxs-lookup"><span data-stu-id="19c53-162">Using Composition Implicit Animations, a developer can automatically animate changes in an element’s layout relative to its parent.</span></span> <span data-ttu-id="19c53-163">Wenn Sie z.B. den **Rand** von der Taste unten ändern, wird es automatisch an die neue Layoutposition animieren.</span><span class="sxs-lookup"><span data-stu-id="19c53-163">For example, if you change the **Margin** of the button below, it will automatically animate to its new layout position.</span></span>

#### <a name="implementation-overview"></a><span data-ttu-id="19c53-164">Übersicht über die Implementierung</span><span class="sxs-lookup"><span data-stu-id="19c53-164">Implementation overview</span></span>

1. <span data-ttu-id="19c53-165">Rufen das Handout **Visual** für das Zielelement ab</span><span class="sxs-lookup"><span data-stu-id="19c53-165">Get the handout **Visual** for the target element</span></span>
1. <span data-ttu-id="19c53-166">Erstellen einer **ImplicitAnimationCollection** , die automatisch Änderungen der **Offset** Eigenschaft animiert</span><span class="sxs-lookup"><span data-stu-id="19c53-166">Create an **ImplicitAnimationCollection** that automatically animates changes in the **Offset** property</span></span>
1. <span data-ttu-id="19c53-167">Ordnen Sie die **ImplicitAnimationCollection** dem zugrunde liegenden Visual zu.</span><span class="sxs-lookup"><span data-stu-id="19c53-167">Associate the **ImplicitAnimationCollection** with the backing Visual</span></span>

```xaml
<Button x:Name="RepositionTarget" Content="Click Me" />
```

```csharp
public MainPage()
{
    InitializeComponent();
    InitializeRepositionAnimation(RepositionTarget);
}

private void InitializeRepositionAnimation(UIElement repositionTarget)
{
    var targetVisual = ElementCompositionPreview.GetElementVisual(repositionTarget);
    Compositor compositor = targetVisual.Compositor;

    // Create an animation to animate targetVisual's Offset property to its final value
    var repositionAnimation = compositor.CreateVector3KeyFrameAnimation();
    repositionAnimation.Duration = TimeSpan.FromSeconds(0.66);
    repositionAnimation.Target = "Offset";
    repositionAnimation.InsertExpressionKeyFrame(1.0f, "this.FinalValue");

    // Run this animation when the Offset Property is changed
    var repositionAnimations = compositor.CreateImplicitAnimationCollection();
    repositionAnimations["Offset"] = repositionAnimation;

    targetVisual.ImplicitAnimations = repositionAnimations;
}
```

### <a name="drop-shadow"></a><span data-ttu-id="19c53-168">Schlagschatten</span><span class="sxs-lookup"><span data-stu-id="19c53-168">Drop shadow</span></span>

<span data-ttu-id="19c53-169">Wenden Sie Pixelgenaue Schlagschatten auf ein **UIElement**, z. B. einer **Ellipse** an, die ein Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="19c53-169">Apply a pixel-perfect drop shadow to a **UIElement**, for example an **Ellipse** containing a picture.</span></span> <span data-ttu-id="19c53-170">Da der Schatten ein **SpriteVisual**, der durch die App erstellt wird, erfordert, müssen wir ein "Hostelement" erstellen, das die **SpriteVisual** enthält. Benutzt wird dazu **ElementCompositionPreview.SetElementChildVisual**.</span><span class="sxs-lookup"><span data-stu-id="19c53-170">Since the shadow requires a **SpriteVisual** created by the app, we need to create a “host” element which will contain the **SpriteVisual** using **ElementCompositionPreview.SetElementChildVisual**.</span></span>

#### <a name="implementation-overview"></a><span data-ttu-id="19c53-171">Übersicht über die Implementierung</span><span class="sxs-lookup"><span data-stu-id="19c53-171">Implementation overview</span></span>

1. <span data-ttu-id="19c53-172">Rufen Sie das Handout **Visual** für das Hostelement ab</span><span class="sxs-lookup"><span data-stu-id="19c53-172">Get the handout **Visual** for the host element</span></span>
2. <span data-ttu-id="19c53-173">Erstellen einer Windows.UI.Composition **DropShadow**</span><span class="sxs-lookup"><span data-stu-id="19c53-173">Create a Windows.UI.Composition **DropShadow**</span></span>
3. <span data-ttu-id="19c53-174">Konfigurieren Sie den **DropShadow**, damit er seine Form vom Zielelement über eine Maske bekommt</span><span class="sxs-lookup"><span data-stu-id="19c53-174">Configure the **DropShadow** to get its shape from the target element via a mask</span></span>
    - <span data-ttu-id="19c53-175">**DropShadow** ist in den Standarteinstellung rechteckig, sodass dies nicht nötig ist, wenn das Zielelement rechteckig ist</span><span class="sxs-lookup"><span data-stu-id="19c53-175">**DropShadow** is rectangular by default, so this is not necessary if the target is rectangular</span></span>
4. <span data-ttu-id="19c53-176">Fügen Sie einen Schatten an einen neuen **SpriteVisual** an, und legen Sie das **SpriteVisual** als untergeordnetes Element des Hostelements fest</span><span class="sxs-lookup"><span data-stu-id="19c53-176">Attach shadow to a new **SpriteVisual**, and set the **SpriteVisual** as the child of the host element</span></span>
5. <span data-ttu-id="19c53-177">Legen Sie die Größe des **SpriteVisual**-Elements auf die Größe des Hosts fest, indem Sie eine **ExpressionAnimation** verwenden</span><span class="sxs-lookup"><span data-stu-id="19c53-177">Bind size of the **SpriteVisual** to the size of the host using an **ExpressionAnimation**</span></span>

```xaml
<Grid Width="200" Height="200">
    <Canvas x:Name="ShadowHost" />
    <Ellipse x:Name="CircleImage">
        <Ellipse.Fill>
            <ImageBrush ImageSource="Assets/Images/2.jpg" Stretch="UniformToFill" />
        </Ellipse.Fill>
    </Ellipse>
</Grid>
```

```csharp
public MainPage()
{
    InitializeComponent();
    InitializeDropShadow(ShadowHost, CircleImage);
}

private void InitializeDropShadow(UIElement shadowHost, Shape shadowTarget)
{
    Visual hostVisual = ElementCompositionPreview.GetElementVisual(shadowHost);
    Compositor compositor = hostVisual.Compositor;

    // Create a drop shadow
    var dropShadow = compositor.CreateDropShadow();
    dropShadow.Color = Color.FromArgb(255, 75, 75, 80);
    dropShadow.BlurRadius = 15.0f;
    dropShadow.Offset = new Vector3(2.5f, 2.5f, 0.0f);
    // Associate the shape of the shadow with the shape of the target element
    dropShadow.Mask = shadowTarget.GetAlphaMask();

    // Create a Visual to hold the shadow
    var shadowVisual = compositor.CreateSpriteVisual();
    shadowVisual.Shadow = dropShadow;

    // Add the shadow as a child of the host in the visual tree
   ElementCompositionPreview.SetElementChildVisual(shadowHost, shadowVisual);

    // Make sure size of shadow host and shadow visual always stay in sync
    var bindSizeAnimation = compositor.CreateExpressionAnimation("hostVisual.Size");
    bindSizeAnimation.SetReferenceParameter("hostVisual", hostVisual);

    shadowVisual.StartAnimation("Size", bindSizeAnimation);
}
```

<span data-ttu-id="19c53-178">Die folgenden zwei Auflistungen zeigen die [C++/WinRT](https://aka.ms/cppwinrt)- und [C++/CX](https://docs.microsoft.com/cpp/cppcx/visual-c-language-reference-c-cx)-Entsprechungen des vorherigen C&#35;-Codes mit der gleichen XAML-Struktur.</span><span class="sxs-lookup"><span data-stu-id="19c53-178">The following two listings show the [C++/WinRT](https://aka.ms/cppwinrt) and [C++/CX](https://docs.microsoft.com/cpp/cppcx/visual-c-language-reference-c-cx) equivalents of the previous C&#35; code using the same XAML structure.</span></span>

```cppwinrt
#include <winrt/Windows.UI.Composition.h>
#include <winrt/Windows.UI.Xaml.h>
#include <winrt/Windows.UI.Xaml.Hosting.h>
#include <winrt/Windows.UI.Xaml.Shapes.h>
...
MainPage()
{
    InitializeComponent();
    InitializeDropShadow(ShadowHost(), CircleImage());
}

int32_t MyProperty();
void MyProperty(int32_t value);

void InitializeDropShadow(Windows::UI::Xaml::UIElement const& shadowHost, Windows::UI::Xaml::Shapes::Shape const& shadowTarget)
{
    auto hostVisual{ Windows::UI::Xaml::Hosting::ElementCompositionPreview::GetElementVisual(shadowHost) };
    auto compositor{ hostVisual.Compositor() };

    // Create a drop shadow
    auto dropShadow{ compositor.CreateDropShadow() };
    dropShadow.Color(Windows::UI::ColorHelper::FromArgb(255, 75, 75, 80));
    dropShadow.BlurRadius(15.0f);
    dropShadow.Offset(Windows::Foundation::Numerics::float3{ 2.5f, 2.5f, 0.0f });
    // Associate the shape of the shadow with the shape of the target element
    dropShadow.Mask(shadowTarget.GetAlphaMask());

    // Create a Visual to hold the shadow
    auto shadowVisual = compositor.CreateSpriteVisual();
    shadowVisual.Shadow(dropShadow);

    // Add the shadow as a child of the host in the visual tree
    Windows::UI::Xaml::Hosting::ElementCompositionPreview::SetElementChildVisual(shadowHost, shadowVisual);

    // Make sure size of shadow host and shadow visual always stay in sync
    auto bindSizeAnimation{ compositor.CreateExpressionAnimation(L"hostVisual.Size") };
    bindSizeAnimation.SetReferenceParameter(L"hostVisual", hostVisual);

    shadowVisual.StartAnimation(L"Size", bindSizeAnimation);
}
```

```cpp
#include "WindowsNumerics.h"

MainPage::MainPage()
{
    InitializeComponent();
    InitializeDropShadow(ShadowHost, CircleImage);
}

void MainPage::InitializeDropShadow(Windows::UI::Xaml::UIElement^ shadowHost, Windows::UI::Xaml::Shapes::Shape^ shadowTarget)
{
    auto hostVisual = Windows::UI::Xaml::Hosting::ElementCompositionPreview::GetElementVisual(shadowHost);
    auto compositor = hostVisual->Compositor;

    // Create a drop shadow
    auto dropShadow = compositor->CreateDropShadow();
    dropShadow->Color = Windows::UI::ColorHelper::FromArgb(255, 75, 75, 80);
    dropShadow->BlurRadius = 15.0f;
    dropShadow->Offset = Windows::Foundation::Numerics::float3(2.5f, 2.5f, 0.0f);
    // Associate the shape of the shadow with the shape of the target element
    dropShadow->Mask = shadowTarget->GetAlphaMask();

    // Create a Visual to hold the shadow
    auto shadowVisual = compositor->CreateSpriteVisual();
    shadowVisual->Shadow = dropShadow;

    // Add the shadow as a child of the host in the visual tree
    Windows::UI::Xaml::Hosting::ElementCompositionPreview::SetElementChildVisual(shadowHost, shadowVisual);

    // Make sure size of shadow host and shadow visual always stay in sync
    auto bindSizeAnimation = compositor->CreateExpressionAnimation("hostVisual.Size");
    bindSizeAnimation->SetReferenceParameter("hostVisual", hostVisual);

    shadowVisual->StartAnimation("Size", bindSizeAnimation);
}
```

### <a name="frosted-glass"></a><span data-ttu-id="19c53-179">Milchglas</span><span class="sxs-lookup"><span data-stu-id="19c53-179">Frosted glass</span></span>

<span data-ttu-id="19c53-180">Erstellen Sie einen Effekt, der den Inhalt verwischt und den Hintergrund färbt.</span><span class="sxs-lookup"><span data-stu-id="19c53-180">Create an effect that blurs and tints background content.</span></span> <span data-ttu-id="19c53-181">Beachten Sie, dass Entwickler das Win2D NuGet-Paket installieren müssen, um Effekte verwenden.</span><span class="sxs-lookup"><span data-stu-id="19c53-181">Note that developers need to install the Win2D NuGet package to use effects.</span></span> <span data-ttu-id="19c53-182">Sie finden unter der [Win2D Homepage](http://microsoft.github.io/Win2D/html/Introduction.htm) Installationsanweisungen.</span><span class="sxs-lookup"><span data-stu-id="19c53-182">See the [Win2D homepage](http://microsoft.github.io/Win2D/html/Introduction.htm) for installation instructions.</span></span>

#### <a name="implementation-overview"></a><span data-ttu-id="19c53-183">Übersicht über die Implementierung</span><span class="sxs-lookup"><span data-stu-id="19c53-183">Implementation overview</span></span>

1.  <span data-ttu-id="19c53-184">Rufen Sie das Handout **Visual** für das Hostelement ab</span><span class="sxs-lookup"><span data-stu-id="19c53-184">Get handout **Visual** for the host element</span></span>
2.  <span data-ttu-id="19c53-185">Erstellen Sie einen Unschärfeeffektstruktur, indem Sie die Win2D und **CompositionEffectSourceParameter** nutzen</span><span class="sxs-lookup"><span data-stu-id="19c53-185">Create a blur effect tree using Win2D and **CompositionEffectSourceParameter**</span></span>
3.  <span data-ttu-id="19c53-186">Erstellen Sie **CompositionEffectBrush**, basierend auf der Effekt-Struktur</span><span class="sxs-lookup"><span data-stu-id="19c53-186">Create a **CompositionEffectBrush** based on the effect tree</span></span>
4.  <span data-ttu-id="19c53-187">Legen Sie die Eingabe von der **CompositionEffectBrush** zu einer **CompositionBackdropBrush**, was ihnen einen Effekt ermöglicht, der auf den Inhalt hinter einem **SpriteVisual** angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="19c53-187">Set input of the **CompositionEffectBrush** to a **CompositionBackdropBrush**, which allows an effect to be applied to the content behind a **SpriteVisual**</span></span>
5.  <span data-ttu-id="19c53-188">Legen Sie **CompositionEffectBrush** als Inhalt eines neuen **SpriteVisual**-Elements fest, und legen Sie das **SpriteVisual**-Element als untergeordnetes Element des Hostelements fest.</span><span class="sxs-lookup"><span data-stu-id="19c53-188">Set the **CompositionEffectBrush** as the content of a new **SpriteVisual**, and set the **SpriteVisual** as the child of the host element.</span></span> <span data-ttu-id="19c53-189">Alternativ könnten Sie eine XamlCompositionBrushBase verwenden.</span><span class="sxs-lookup"><span data-stu-id="19c53-189">You could alternative use a XamlCompositionBrushBase.</span></span>
6.  <span data-ttu-id="19c53-190">Legen Sie die Größe des **SpriteVisual** auf die Größe des Hosts fest, mit einer **ExpressionAnimation**</span><span class="sxs-lookup"><span data-stu-id="19c53-190">Bind size of the **SpriteVisual** to the size of the host using an **ExpressionAnimation**</span></span>

```xaml
<Grid Width="300" Height="300" Grid.Column="1">
    <Image
        Source="Assets/Images/2.jpg"
        Width="200"
        Height="200" />
    <Canvas
        x:Name="GlassHost"
        Width="150"
        Height="300"
        HorizontalAlignment="Right" />
</Grid>
```

```csharp
public MainPage()
{
    InitializeComponent();
    InitializeFrostedGlass(GlassHost);
}

private void InitializeFrostedGlass(UIElement glassHost)
{
    Visual hostVisual = ElementCompositionPreview.GetElementVisual(glassHost);
    Compositor compositor = hostVisual.Compositor;

    // Create a glass effect, requires Win2D NuGet package
    var glassEffect = new GaussianBlurEffect
    { 
        BlurAmount = 15.0f,
        BorderMode = EffectBorderMode.Hard,
        Source = new ArithmeticCompositeEffect
        {
            MultiplyAmount = 0,
            Source1Amount = 0.5f,
            Source2Amount = 0.5f,
            Source1 = new CompositionEffectSourceParameter("backdropBrush"),
            Source2 = new ColorSourceEffect
            {
                Color = Color.FromArgb(255, 245, 245, 245)
            }
        }
    };

    //  Create an instance of the effect and set its source to a CompositionBackdropBrush
    var effectFactory = compositor.CreateEffectFactory(glassEffect);
    var backdropBrush = compositor.CreateBackdropBrush();
    var effectBrush = effectFactory.CreateBrush();

    effectBrush.SetSourceParameter("backdropBrush", backdropBrush);

    // Create a Visual to contain the frosted glass effect
    var glassVisual = compositor.CreateSpriteVisual();
    glassVisual.Brush = effectBrush;

    // Add the blur as a child of the host in the visual tree
    ElementCompositionPreview.SetElementChildVisual(glassHost, glassVisual);

    // Make sure size of glass host and glass visual always stay in sync
    var bindSizeAnimation = compositor.CreateExpressionAnimation("hostVisual.Size");
    bindSizeAnimation.SetReferenceParameter("hostVisual", hostVisual);

    glassVisual.StartAnimation("Size", bindSizeAnimation);
}
```

## <a name="additional-resources"></a><span data-ttu-id="19c53-191">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="19c53-191">Additional Resources</span></span>

- [<span data-ttu-id="19c53-192">Übersicht über die visuelle Ebene</span><span class="sxs-lookup"><span data-stu-id="19c53-192">Visual Layer overview</span></span>](https://msdn.microsoft.com/windows/uwp/composition/visual-layer)
- [<span data-ttu-id="19c53-193">**ElementCompositionPreview** Klasse</span><span class="sxs-lookup"><span data-stu-id="19c53-193">**ElementCompositionPreview** class</span></span>](https://msdn.microsoft.com/library/windows/apps/mt608976)
- <span data-ttu-id="19c53-194">Erweiterte UI und Kompositionsbeispiele in dem [WindowsUIDevLabs-GitHub](https://github.com/microsoft/windowsuidevlabs).</span><span class="sxs-lookup"><span data-stu-id="19c53-194">Advanced UI and Composition samples in the [WindowsUIDevLabs GitHub](https://github.com/microsoft/windowsuidevlabs)</span></span>
- [<span data-ttu-id="19c53-195">BasicXamlInterop-Beispiel</span><span class="sxs-lookup"><span data-stu-id="19c53-195">BasicXamlInterop sample</span></span>](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2010586/BasicXamlInterop)
- [<span data-ttu-id="19c53-196">ParallaxingListItems-Beispiel</span><span class="sxs-lookup"><span data-stu-id="19c53-196">ParallaxingListItems sample</span></span>](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SampleGallery/Samples/SDK%2010586/ParallaxingListItems)
