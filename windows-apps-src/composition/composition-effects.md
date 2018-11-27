---
ms.assetid: 6e9b9ff2-234b-6f63-0975-1afb2d86ba1a
title: Kompositionseffekte
description: Mithilfe von Effekt-APIs können Entwickler anpassen, wie ihre Benutzeroberfläche gerendert wird.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 75af433d80364485b0c12a9540c0d7bb471c4e28
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7697343"
---
# <a name="composition-effects"></a><span data-ttu-id="68336-104">Kompositionseffekte</span><span class="sxs-lookup"><span data-stu-id="68336-104">Composition effects</span></span>

<span data-ttu-id="68336-105">Mit der API [**Windows.UI.Composition**](https://msdn.microsoft.com/library/windows/apps/Dn706878) können Echtzeiteffekte mithilfe animierbarer Effekteigenschaften auf Bilder und Benutzeroberflächen angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="68336-105">The [**Windows.UI.Composition**](https://msdn.microsoft.com/library/windows/apps/Dn706878) APIs allows real-time effects to be applied to images and UI with animatable effect properties.</span></span> <span data-ttu-id="68336-106">In dieser Übersicht erläutern wir die Funktionen, über die Effekte auf visuelle Kompositionselemente angewendet werden können.</span><span class="sxs-lookup"><span data-stu-id="68336-106">In this overview, we’ll run through the functionality available that allows effects to be applied to a composition visual.</span></span>

<span data-ttu-id="68336-107">Um die Konsistenz der [Universellen Windows-Plattform (UWP)](https://msdn.microsoft.com/library/windows/apps/dn726767.aspx) für Entwickler zu gewährleisten, die Effektbeschreibungen in ihren Anwendungen verwenden, nutzen Kompositionseffekte die „IGraphicsEffect“-Schnittstelle von Win2D, um die Effektbeschreibungen über den [Microsoft.Graphics.Canvas.Effects](http://microsoft.github.io/Win2D/html/N_Microsoft_Graphics_Canvas_Effects.htm)-Namespace anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="68336-107">To support [Universal Windows Platform (UWP)](https://msdn.microsoft.com/library/windows/apps/dn726767.aspx) consistency for developers describing effects in their applications, composition effects leverage Win2D’s IGraphicsEffect interface to use effect descriptions via the [Microsoft.Graphics.Canvas.Effects](http://microsoft.github.io/Win2D/html/N_Microsoft_Graphics_Canvas_Effects.htm) Namespace.</span></span>

<span data-ttu-id="68336-108">Pinseleffekte werden verwendet, um Bereiche einer Anwendung farbig zu gestalten. Dabei werden Effekte auf eine Gruppe vorhandener Bilder angewendet.</span><span class="sxs-lookup"><span data-stu-id="68336-108">Brush effects are used to paint areas of an application by applying effects to a set of existing images.</span></span> <span data-ttu-id="68336-109">Die Kompositionseffekt-APIs in Windows 10 sind auf visuelle Sprite-Elemente ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="68336-109">Windows 10 composition effect APIs are focused on Sprite Visuals.</span></span> <span data-ttu-id="68336-110">Das SpriteVisual-Element ermöglicht hohe Flexibilität und Interaktion bei der Farb-, Bild- und Effektgestaltung.</span><span class="sxs-lookup"><span data-stu-id="68336-110">The SpriteVisual allows for flexibility and interplay in color, image and effect creation.</span></span> <span data-ttu-id="68336-111">SpriteVisual ist ein visueller Kompositionstyp, der ein 2D-Rechteck mit einem Pinsel füllen kann.</span><span class="sxs-lookup"><span data-stu-id="68336-111">The SpriteVisual is a composition visual type that can fill a 2D rectangle with a brush.</span></span> <span data-ttu-id="68336-112">Das visuelle Element definiert die Grenzen des Rechtecks und der Pinsel die Pixel zum Zeichnen des Rechtecks.</span><span class="sxs-lookup"><span data-stu-id="68336-112">The visual defines the bounds of the rectangle and the brush defines the pixels used to paint the rectangle.</span></span>

<span data-ttu-id="68336-113">Effektpinsel werden für visuelle Elemente von Kompositionsstrukturen verwendet, deren Inhalt der Ausgabe eines Effektgraphen entnommen wird.</span><span class="sxs-lookup"><span data-stu-id="68336-113">Effect brushes are used on composition tree visuals whose content comes from the output of an effect graph.</span></span> <span data-ttu-id="68336-114">Effekte können auf vorhandene Oberflächen/Texturen verweisen, aber nicht auf die Ausgabe anderer Kompositionsstrukturen.</span><span class="sxs-lookup"><span data-stu-id="68336-114">Effects can reference existing surfaces/textures, but not the output of other composition trees.</span></span>

<span data-ttu-id="68336-115">Effekte können auch für XAML-UI-Elemente mit einem Effektpinsel mit [**XamlCompositionBrushBase**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase) angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="68336-115">Effects can also be applied to XAML UIElements using an effect brush with [**XamlCompositionBrushBase**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).</span></span>

## <a name="effect-features"></a><span data-ttu-id="68336-116">Effektfeatures</span><span class="sxs-lookup"><span data-stu-id="68336-116">Effect Features</span></span>

- [<span data-ttu-id="68336-117">Effektbibliothek</span><span class="sxs-lookup"><span data-stu-id="68336-117">Effect Library</span></span>](./composition-effects.md#effect-library)
- [<span data-ttu-id="68336-118">Verketten von Effekten</span><span class="sxs-lookup"><span data-stu-id="68336-118">Chaining Effects</span></span>](./composition-effects.md#chaining-effects)
- [<span data-ttu-id="68336-119">Animationsunterstützung</span><span class="sxs-lookup"><span data-stu-id="68336-119">Animation Support</span></span>](./composition-effects.md#animation-support)
- [<span data-ttu-id="68336-120">Konstante im Vergleich zu animierten Effekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="68336-120">Constant vs. Animated Effect Properties</span></span>](./composition-effects.md#constant-vs-animated-effect-properties)
- [<span data-ttu-id="68336-121">Mehrere Effektinstanzen mit unabhängigen Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="68336-121">Multiple Effect Instances with Independent Properties</span></span>](./composition-effects.md#multiple-effect-instances-with-independent-properties)

### <a name="effect-library"></a><span data-ttu-id="68336-122">Effektbibliothek</span><span class="sxs-lookup"><span data-stu-id="68336-122">Effect Library</span></span>

<span data-ttu-id="68336-123">Derzeit unterstützt die Komposition folgende Effekte:</span><span class="sxs-lookup"><span data-stu-id="68336-123">Currently composition supports the following effects:</span></span>

| <span data-ttu-id="68336-124">Effekt</span><span class="sxs-lookup"><span data-stu-id="68336-124">Effect</span></span>               | <span data-ttu-id="68336-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="68336-125">Description</span></span>                                                                                                                                                                                                                |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="68336-126">2D-affine Transformation</span><span class="sxs-lookup"><span data-stu-id="68336-126">2D affine transform</span></span>  | <span data-ttu-id="68336-127">Wendet eine 2D-affine Transformationsmatrix auf ein Bild an.</span><span class="sxs-lookup"><span data-stu-id="68336-127">Applies a 2D affine transform matrix to an image.</span></span> <span data-ttu-id="68336-128">Dieser Effekt wurde verwendet, um die Alphamaske in unseren [Effektbeispielen](http://go.microsoft.com/fwlink/?LinkId=785341) zu animieren.</span><span class="sxs-lookup"><span data-stu-id="68336-128">We used this effect to animate alpha mask in our effect [samples](http://go.microsoft.com/fwlink/?LinkId=785341).</span></span>       |
| <span data-ttu-id="68336-129">Arithmetische Komposition</span><span class="sxs-lookup"><span data-stu-id="68336-129">Arithmetic composite</span></span> | <span data-ttu-id="68336-130">Kombiniert zwei Bilder mittels einer flexiblen Gleichung.</span><span class="sxs-lookup"><span data-stu-id="68336-130">Combines two images using a flexible equation.</span></span> <span data-ttu-id="68336-131">Eine arithmetische Komposition wurde verwendet, um einen Überblendungseffekt in unseren [Beispielen](http://go.microsoft.com/fwlink/?LinkId=785341) zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="68336-131">We used arithmetic composite to create a crossfade effect in our [samples](http://go.microsoft.com/fwlink/?LinkId=785341).</span></span> |
| <span data-ttu-id="68336-132">Fülleffekt</span><span class="sxs-lookup"><span data-stu-id="68336-132">Blend effect</span></span>         | <span data-ttu-id="68336-133">Erzeugt einen Fülleffekt, der zwei Bilder kombiniert.</span><span class="sxs-lookup"><span data-stu-id="68336-133">Creates a blend effect that combines two images.</span></span> <span data-ttu-id="68336-134">Die Komposition stellt 21 der 26 in Win2D unterstützten [Füllmethoden](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_Effects_BlendEffectMode.htm) bereit.</span><span class="sxs-lookup"><span data-stu-id="68336-134">Composition provides 21 of the 26 [blend modes](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_Effects_BlendEffectMode.htm) supported in Win2D.</span></span>        |
| <span data-ttu-id="68336-135">Farbquelle</span><span class="sxs-lookup"><span data-stu-id="68336-135">Color source</span></span>         | <span data-ttu-id="68336-136">Generiert ein Bild, das eine Volltonfarbe enthält.</span><span class="sxs-lookup"><span data-stu-id="68336-136">Generates an image containing a solid color.</span></span>                                                                                                                                                                               |
| <span data-ttu-id="68336-137">Komposition</span><span class="sxs-lookup"><span data-stu-id="68336-137">Composite</span></span>            | <span data-ttu-id="68336-138">Kombiniert zwei Bilder.</span><span class="sxs-lookup"><span data-stu-id="68336-138">Combines two images.</span></span> <span data-ttu-id="68336-139">Die Komposition stellt alle 13 in Win2D unterstützten [Kompositionsmodi](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_CanvasComposite.htm) bereit.</span><span class="sxs-lookup"><span data-stu-id="68336-139">Composition provides all 13 [composite modes](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_CanvasComposite.htm) supported in Win2D.</span></span>                                              |
| <span data-ttu-id="68336-140">Kontrast</span><span class="sxs-lookup"><span data-stu-id="68336-140">Contrast</span></span>             | <span data-ttu-id="68336-141">Erhöht oder verringert den Kontrast eines Bilds.</span><span class="sxs-lookup"><span data-stu-id="68336-141">Increases or decreases the contrast of an image.</span></span>                                                                                                                                                                           |
| <span data-ttu-id="68336-142">Belichtung</span><span class="sxs-lookup"><span data-stu-id="68336-142">Exposure</span></span>             | <span data-ttu-id="68336-143">Erhöht oder verringert die Belichtung eines Bilds.</span><span class="sxs-lookup"><span data-stu-id="68336-143">Increases or decreases the exposure of an image.</span></span>                                                                                                                                                                           |
| <span data-ttu-id="68336-144">Graustufen</span><span class="sxs-lookup"><span data-stu-id="68336-144">Grayscale</span></span>            | <span data-ttu-id="68336-145">Konvertiert ein Bild in ein monochromes Graustufenbild.</span><span class="sxs-lookup"><span data-stu-id="68336-145">Converts an image to monochromatic gray.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="68336-146">Gammakorrektur</span><span class="sxs-lookup"><span data-stu-id="68336-146">Gamma transfer</span></span>       | <span data-ttu-id="68336-147">Ändert die Farben eines Bilds, indem die Gammakorrekturfunktion pro Kanal angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="68336-147">Alters the colors of an image by applying a per-channel gamma transfer function.</span></span>                                                                                                                                           |
| <span data-ttu-id="68336-148">Farbtondrehung</span><span class="sxs-lookup"><span data-stu-id="68336-148">Hue rotate</span></span>           | <span data-ttu-id="68336-149">Ändert die Farbe eines Bilds durch Rotation der Farbtonwerte.</span><span class="sxs-lookup"><span data-stu-id="68336-149">Alters the color of an image by rotating its hue values.</span></span>                                                                                                                                                                   |
| <span data-ttu-id="68336-150">Invertierung</span><span class="sxs-lookup"><span data-stu-id="68336-150">Invert</span></span>               | <span data-ttu-id="68336-151">Invertiert die Farben eines Bilds.</span><span class="sxs-lookup"><span data-stu-id="68336-151">Inverts the colors of an image.</span></span>                                                                                                                                                                                            |
| <span data-ttu-id="68336-152">Sättigung</span><span class="sxs-lookup"><span data-stu-id="68336-152">Saturate</span></span>             | <span data-ttu-id="68336-153">Ändert die Sättigung eines Bilds.</span><span class="sxs-lookup"><span data-stu-id="68336-153">Alters the saturation of an image.</span></span>                                                                                                                                                                                         |
| <span data-ttu-id="68336-154">Sepia</span><span class="sxs-lookup"><span data-stu-id="68336-154">Sepia</span></span>                | <span data-ttu-id="68336-155">Konvertiert ein Bild in Sepiatöne.</span><span class="sxs-lookup"><span data-stu-id="68336-155">Converts an image to sepia tones.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="68336-156">Temperatur und Farbton</span><span class="sxs-lookup"><span data-stu-id="68336-156">Temperature and tint</span></span> | <span data-ttu-id="68336-157">Passt die Temperatur und/oder den Farbton eines Bilds an.</span><span class="sxs-lookup"><span data-stu-id="68336-157">Adjusts the temperature and/or tint of an image.</span></span>                                                                                                                                                                           |

<span data-ttu-id="68336-158">Ausführliche Informationen finden Sie in der Beschreibung des Win2D-Namespaces [Microsoft.Graphics.Canvas.Effects](http://microsoft.github.io/Win2D/html/N_Microsoft_Graphics_Canvas_Effects.htm).</span><span class="sxs-lookup"><span data-stu-id="68336-158">See Win2D’s [Microsoft.Graphics.Canvas.Effects](http://microsoft.github.io/Win2D/html/N_Microsoft_Graphics_Canvas_Effects.htm) Namespace for more detailed information.</span></span> <span data-ttu-id="68336-159">In der Komposition nicht unterstützte Effekte sind mit \[NoComposition\] gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="68336-159">Effects not supported in composition are noted as \[NoComposition\].</span></span>

### <a name="chaining-effects"></a><span data-ttu-id="68336-160">Verketten von Effekten</span><span class="sxs-lookup"><span data-stu-id="68336-160">Chaining Effects</span></span>

<span data-ttu-id="68336-161">Effekte können verkettet werden, um einer Anwendung die gleichzeitige Nutzung mehrerer Effekte in einem Bild zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="68336-161">Effects can be chained, allowing an application to simultaneously use multiple effects on an image.</span></span> <span data-ttu-id="68336-162">Effektgraphen unterstützen mehrere Effekte, die aufeinander verweisen können.</span><span class="sxs-lookup"><span data-stu-id="68336-162">Effect graphs can support multiple effects that can refer to one and other.</span></span> <span data-ttu-id="68336-163">Bei der Beschreibung eines Effekts fügen Sie Ihrem Effekt einfach einen Effekt als Eingabe hinzu.</span><span class="sxs-lookup"><span data-stu-id="68336-163">When describing your effect, simply add an effect as input to your effect.</span></span>

```cs
IGraphicsEffect graphicsEffect =
new Microsoft.Graphics.Canvas.Effects.ArithmeticCompositeEffect
{
  Source1 = new CompositionEffectSourceParameter("source1"),
  Source2 = new SaturationEffect
  {
    Saturation = 0,
    Source = new CompositionEffectSourceParameter("source2")
  },
  MultiplyAmount = 0,
  Source1Amount = 0.5f,
  Source2Amount = 0.5f,
  Offset = 0
}
```

<span data-ttu-id="68336-164">Im obigen Beispiel wird der Effekt einer arithmetischen Komposition mit zwei Eingaben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="68336-164">The example above describes an arithmetic composite effect which has two inputs.</span></span> <span data-ttu-id="68336-165">Die zweite Eingabe hat einen Sättigungseffekt mit der Sättigungseigenschaft „0,5“.</span><span class="sxs-lookup"><span data-stu-id="68336-165">The second input has a saturation effect with a .5 saturation property.</span></span>

### <a name="animation-support"></a><span data-ttu-id="68336-166">Animationsunterstützung</span><span class="sxs-lookup"><span data-stu-id="68336-166">Animation Support</span></span>

<span data-ttu-id="68336-167">Effekteigenschaften bieten Unterstützung für Animationen. Während der Effektkompilierung können Sie angeben, welche Effekteigenschaften animiert und welche als Konstanten vorgegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="68336-167">Effect properties support animation, during effect compilation you can specify effect properties can be animated and which can be "baked in" as constants.</span></span> <span data-ttu-id="68336-168">Die animierbaren Eigenschaften werden über Zeichenfolgen im Format „Effektname.Eigenschaftenname“ angegeben.</span><span class="sxs-lookup"><span data-stu-id="68336-168">The animatable properties are specified through strings of the form “effect name.property name”.</span></span> <span data-ttu-id="68336-169">Diese Eigenschaften können unabhängig über mehrere Instanziierungen des Effekts animiert werden.</span><span class="sxs-lookup"><span data-stu-id="68336-169">These properties can be animated independently over multiple instantiations of the effect.</span></span>

### <a name="constant-vs-animated-effect-properties"></a><span data-ttu-id="68336-170">Konstante im Vergleich zu animierten Effekteigenschaften</span><span class="sxs-lookup"><span data-stu-id="68336-170">Constant vs Animated Effect Properties</span></span>

<span data-ttu-id="68336-171">Während der Effektkompilierung können Sie Effekteigenschaften als dynamisch oder als Eigenschaften angeben, die konstant fest sind.</span><span class="sxs-lookup"><span data-stu-id="68336-171">During effect compilation you can specify effect properties as dynamic or as properties that are "baked in" as constants.</span></span> <span data-ttu-id="68336-172">Die dynamischen Eigenschaften werden über Zeichenfolgen in folgendem Format angegeben: „<effect name>.<property name>“.</span><span class="sxs-lookup"><span data-stu-id="68336-172">The dynamic properties are specified through strings of the form “<effect name>.<property name>”.</span></span> <span data-ttu-id="68336-173">Die dynamischen Eigenschaften können auf einen bestimmten Wert festgelegt oder mithilfe des Kompositionsanimationssystems animiert werden.</span><span class="sxs-lookup"><span data-stu-id="68336-173">The dynamic properties can be set to a specific value or can be animated using the composition animation system.</span></span>

<span data-ttu-id="68336-174">Beim Kompilieren der oben angegebenen Effektbeschreibung können Sie die Sättigung entweder als Konstante mit dem Wert „0,5“ vorgeben oder sie dynamisch gestalten (sie also dynamisch festlegen oder animieren).</span><span class="sxs-lookup"><span data-stu-id="68336-174">When compiling the effect description above, you have the flexibility of either baking in saturation to be equal to 0.5 or making it dynamic and setting it dynamically or animating it.</span></span>

<span data-ttu-id="68336-175">Kompilieren eines Effekts mit als Konstante festgelegter Sättigung:</span><span class="sxs-lookup"><span data-stu-id="68336-175">Compiling an effect with saturation baked in:</span></span>

```cs
var effectFactory = _compositor.CreateEffectFactory(graphicsEffect);
```

<span data-ttu-id="68336-176">Kompilieren eines Effekts mit dynamischer Sättigung:</span><span class="sxs-lookup"><span data-stu-id="68336-176">Compiling an effect with dynamic saturation:</span></span>

```cs
var effectFactory = _compositor.CreateEffectFactory(graphicsEffect, new[]{"SaturationEffect.Saturation"});
_catEffect = effectFactory.CreateBrush();
_catEffect.SetSourceParameter("mySource", surfaceBrush);
_catEffect.Properties.InsertScalar("saturationEffect.Saturation", 0f);
```

<span data-ttu-id="68336-177">Die Sättigungseigenschaft des oben genannten Effekts kann dann entweder auf einen statischen Wert festgelegt oder mithilfe der Expression- oder ScalarKeyFrame-Animation animiert werden.</span><span class="sxs-lookup"><span data-stu-id="68336-177">The saturation property of the effect above can then be either set to a static value or animated using either Expression or ScalarKeyFrame animations.</span></span>

<span data-ttu-id="68336-178">Sie können ein ScalarKeyFrame-Element erstellen, das wie folgt zum Animieren der Sättigungseigenschaft eines Effekts verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="68336-178">You can create a ScalarKeyFrame that will be used to animate the Saturation property of an effect like this:</span></span>

```cs
ScalarKeyFrameAnimation effectAnimation = _compositor.CreateScalarKeyFrameAnimation();
            effectAnimation.InsertKeyFrame(0f, 0f);
            effectAnimation.InsertKeyFrame(0.50f, 1f);
            effectAnimation.InsertKeyFrame(1.0f, 0f);
            effectAnimation.Duration = TimeSpan.FromMilliseconds(2500);
            effectAnimation.IterationBehavior = AnimationIterationBehavior.Forever;
```

<span data-ttu-id="68336-179">Starten Sie wie folgt die Animation der Sättigungseigenschaft des Effekts:</span><span class="sxs-lookup"><span data-stu-id="68336-179">Start the animation on the Saturation property of the effect like this:</span></span>

```cs
catEffect.Properties.StartAnimation("saturationEffect.Saturation", effectAnimation);
```

<span data-ttu-id="68336-180">Im Beispiel [Entsättigung – Animation](http://go.microsoft.com/fwlink/?LinkId=785342) finden Sie mithilfe von Keyframes animierte Effekteigenschaften. Das [AlphaMask-Beispiel](http://go.microsoft.com/fwlink/?LinkId=785343) enthält Informationen zur Verwendung von Effekten und Ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="68336-180">See the [Desaturation - Animation sample](http://go.microsoft.com/fwlink/?LinkId=785342) for effect properties animated with key frames and the [AlphaMask sample](http://go.microsoft.com/fwlink/?LinkId=785343) for use of effects and expressions.</span></span>

### <a name="multiple-effect-instances-with-independent-properties"></a><span data-ttu-id="68336-181">Mehrere Effektinstanzen mit unabhängigen Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="68336-181">Multiple Effect Instances with Independent Properties</span></span>

<span data-ttu-id="68336-182">Wenn angegeben wird, dass ein Parameter während der Effektkompilierung dynamisch sein soll, kann der Parameter pro Effektinstanz geändert werden.</span><span class="sxs-lookup"><span data-stu-id="68336-182">By specifying that a parameter should be dynamic during effect compilation, the parameter can then be changed on a per-effect instance basis.</span></span> <span data-ttu-id="68336-183">Dadurch können zwei visuelle Elemente denselben Effekt verwenden, aber mit unterschiedlichen Effekteigenschaften gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="68336-183">This allows two Visuals to use the same effect but be rendered with different effect properties.</span></span> <span data-ttu-id="68336-184">Weitere Informationen finden Sie im [Beispiel](http://go.microsoft.com/fwlink/?LinkId=785344) zum ColorSource- und Blend-Effekt.</span><span class="sxs-lookup"><span data-stu-id="68336-184">See the ColorSource and Blend [sample](http://go.microsoft.com/fwlink/?LinkId=785344) for more information.</span></span>

## <a name="getting-started-with-composition-effects"></a><span data-ttu-id="68336-185">Erste Schritte mit Kompositionseffekten</span><span class="sxs-lookup"><span data-stu-id="68336-185">Getting Started with Composition Effects</span></span>

<span data-ttu-id="68336-186">In diesem Schnellstart-Lernprogramm erfahren Sie, wie Sie einige der grundlegenden Effektfunktionen nutzen.</span><span class="sxs-lookup"><span data-stu-id="68336-186">This quick start tutorial shows you how to make use of some of the basic capabilities of effects.</span></span>

- [<span data-ttu-id="68336-187">Installieren von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68336-187">Installing Visual Studio</span></span>](./composition-effects.md#installing-visual-studio)
- [<span data-ttu-id="68336-188">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="68336-188">Creating a new project</span></span>](./composition-effects.md#creating-a-new-project)
- [<span data-ttu-id="68336-189">Installieren von Win2D</span><span class="sxs-lookup"><span data-stu-id="68336-189">Installing Win2D</span></span>](./composition-effects.md#installing-win2d)
- [<span data-ttu-id="68336-190">Festlegen der Grundlagen für die Komposition</span><span class="sxs-lookup"><span data-stu-id="68336-190">Setting your Composition Basics</span></span>](./composition-effects.md#setting-your-composition-basics)
- [<span data-ttu-id="68336-191">Erstellen eines CompositionSurface-Pinsels</span><span class="sxs-lookup"><span data-stu-id="68336-191">Creating a CompositionSurface Brush</span></span>](./composition-effects.md#creating-a-compositionsurface-brush)
- [<span data-ttu-id="68336-192">Erstellen, Kompilieren und Anwenden von Effekten</span><span class="sxs-lookup"><span data-stu-id="68336-192">Creating, Compiling and Applying Effects</span></span>](./composition-effects.md#creating-compiling-and-applying-effects)

### <a name="installing-visual-studio"></a><span data-ttu-id="68336-193">Installieren von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68336-193">Installing Visual Studio</span></span>

- <span data-ttu-id="68336-194">Wenn Sie keine unterstützte Version von Visual Studio installiert haben, wechseln Sie [hier](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) zur Visual Studio-Downloadseite.</span><span class="sxs-lookup"><span data-stu-id="68336-194">If you don't have a supported version of Visual Studio installed, go to the Visual Studio Downloads page [here](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx).</span></span>

### <a name="creating-a-new-project"></a><span data-ttu-id="68336-195">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="68336-195">Creating a new project</span></span>

- <span data-ttu-id="68336-196">Wählen Sie „Datei->Neu->Projekt“ aus.</span><span class="sxs-lookup"><span data-stu-id="68336-196">Go to File->New->Project...</span></span>
- <span data-ttu-id="68336-197">Wählen Sie „Visual C#“ aus.</span><span class="sxs-lookup"><span data-stu-id="68336-197">Select 'Visual C#'</span></span>
- <span data-ttu-id="68336-198">Erstellen Sie eine App vom Typ „(Leere App (Windows – universell)“ (Visual Studio 2015).</span><span class="sxs-lookup"><span data-stu-id="68336-198">Create a 'Blank App (Windows Universal)' (Visual Studio 2015)</span></span>
- <span data-ttu-id="68336-199">Geben Sie einen Projektnamen Ihrer Wahl ein.</span><span class="sxs-lookup"><span data-stu-id="68336-199">Enter a project name of your choosing</span></span>
- <span data-ttu-id="68336-200">Klicken Sie auf „OK“.</span><span class="sxs-lookup"><span data-stu-id="68336-200">Click 'OK'</span></span>

### <a name="installing-win2d"></a><span data-ttu-id="68336-201">Installieren von Win2D</span><span class="sxs-lookup"><span data-stu-id="68336-201">Installing Win2D</span></span>

<span data-ttu-id="68336-202">Win2D wird als „Nuget.org“-Paket freigegeben und muss installiert werden, damit Sie Effekte nutzen können.</span><span class="sxs-lookup"><span data-stu-id="68336-202">Win2D is released as a Nuget.org package and needs to be installed before you can use effects.</span></span>

<span data-ttu-id="68336-203">Es gibt zwei Paketversionen: eine für Windows 10 und eine für Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="68336-203">There are two package versions, one for Windows 10 and one for Windows 8.1.</span></span> <span data-ttu-id="68336-204">Für Kompositionseffekte verwenden Sie die Windows10-Version.</span><span class="sxs-lookup"><span data-stu-id="68336-204">For Composition effects you’ll use the Windows 10 version.</span></span>

- <span data-ttu-id="68336-205">Starten Sie den NuGet-Paket-Manager, indem Sie „Extras → NuGet-Paket-Manager → NuGet-Pakete für Projektmappe verwalten“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="68336-205">Launch the NuGet Package Manager by going to Tools → NuGet Package Manager → Manage NuGet Packages for Solution.</span></span>
- <span data-ttu-id="68336-206">Suchen Sie nach „Win2D“, und wählen Sie das entsprechende Paket für die Zielversion von Windows aus.</span><span class="sxs-lookup"><span data-stu-id="68336-206">Search for "Win2D" and select the appropriate package for your target version of Windows.</span></span> <span data-ttu-id="68336-207">Da Windows.UI.</span><span class="sxs-lookup"><span data-stu-id="68336-207">Because Windows.UI.</span></span> <span data-ttu-id="68336-208">Composition Windows 10 (aber nicht 8.1) unterstützt, wählen Sie „Win2D.uwp“ aus.</span><span class="sxs-lookup"><span data-stu-id="68336-208">Composition supports Windows 10 (not 8.1), select Win2D.uwp.</span></span>
- <span data-ttu-id="68336-209">Akzeptieren Sie den Lizenzvertrag.</span><span class="sxs-lookup"><span data-stu-id="68336-209">Accept the license agreement</span></span>
- <span data-ttu-id="68336-210">Klicken Sie auf „Schließen“.</span><span class="sxs-lookup"><span data-stu-id="68336-210">Click 'Close'</span></span>

<span data-ttu-id="68336-211">In den nächsten Schritten verwenden wir Composition-APIs, um einen Sättigungseffekt auf dieses Katzenfoto anzuwenden, durch den die gesamte Sättigung entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="68336-211">In the next few steps we will use composition API’s to apply a saturation effect to this cat image which will remove all saturation.</span></span> <span data-ttu-id="68336-212">In diesem Modell wird der Effekt erstellt und dann auf ein Bild angewendet.</span><span class="sxs-lookup"><span data-stu-id="68336-212">In this model the effect is created and then applied to an image.</span></span>

![Quellbild](images/composition-cat-source.png)
### <a name="setting-your-composition-basics"></a><span data-ttu-id="68336-214">Festlegen der Grundlagen für die Komposition</span><span class="sxs-lookup"><span data-stu-id="68336-214">Setting your Composition Basics</span></span>

<span data-ttu-id="68336-215">Anhand des [Beispiels für die visuelle Kompositionsstruktur](http://go.microsoft.com/fwlink/?LinkId=785345) auf GitHub erfahren Sie, wie Sie den „Windows.UI.Composition“-Kompositor einrichten, den „ContainerVisual“-Stamm angeben und diesen dem Hauptfenster zuordnen.</span><span class="sxs-lookup"><span data-stu-id="68336-215">See the [Composition Visual Tree Sample](http://go.microsoft.com/fwlink/?LinkId=785345) on our GitHub for an example of how to set up Windows.UI.Composition Compositor, root ContainerVisual, and associate with the Core Window.</span></span>

```cs
_compositor = new Compositor();
_root = _compositor.CreateContainerVisual();
_target = _compositor.CreateTargetForCurrentView();
_target.Root = _root;
_imageFactory = new CompositionImageFactory(_compositor)
Desaturate();
```

### <a name="creating-a-compositionsurface-brush"></a><span data-ttu-id="68336-216">Erstellen eines CompositionSurface-Pinsels</span><span class="sxs-lookup"><span data-stu-id="68336-216">Creating a CompositionSurface Brush</span></span>

```cs
CompositionSurfaceBrush surfaceBrush = _compositor.CreateSurfaceBrush();
LoadImage(surfaceBrush);
```

### <a name="creating-compiling-and-applying-effects"></a><span data-ttu-id="68336-217">Erstellen, Kompilieren und Anwenden von Effekten</span><span class="sxs-lookup"><span data-stu-id="68336-217">Creating, Compiling and Applying Effects</span></span>

1. <span data-ttu-id="68336-218">Erstellen Sie den Grafikeffekt</span><span class="sxs-lookup"><span data-stu-id="68336-218">Create the graphics effect</span></span>

    ```cs
    var graphicsEffect = new SaturationEffect
    {
      Saturation = 0.0f,
      Source = new CompositionEffectSourceParameter("mySource")
    };
    ```

1. <span data-ttu-id="68336-219">Kompilieren Sie den Effekt, und erstellen Sie einen Effektpinsel</span><span class="sxs-lookup"><span data-stu-id="68336-219">Compile the effect and create effect brush</span></span>

    ```cs
    var effectFactory = _compositor.CreateEffectFactory(graphicsEffect);

    var catEffect = effectFactory.CreateBrush();
    catEffect.SetSourceParameter("mySource", surfaceBrush);
    ```

1. <span data-ttu-id="68336-220">Erstellen Sie ein SpriteVisual-Element in der Kompositionsstruktur, und wenden Sie den Effekt an</span><span class="sxs-lookup"><span data-stu-id="68336-220">Create a SpriteVisual in the composition tree and apply the effect</span></span>

    ```cs
    var catVisual = _compositor.CreateSpriteVisual();
      catVisual.Brush = catEffect;
      catVisual.Size = new Vector2(219, 300);
      _root.Children.InsertAtBottom(catVisual);
    }
    ```

1. <span data-ttu-id="68336-221">Erstellen Sie die zu ladende Bildquelle.</span><span class="sxs-lookup"><span data-stu-id="68336-221">Create your image source to load.</span></span>

    ```cs
    CompositionImage imageSource = _imageFactory.CreateImageFromUri(new Uri("ms-appx:///Assets/cat.png"));
    CompositionImageLoadResult result = await imageSource.CompleteLoadAsync();
    if (result.Status == CompositionImageLoadStatus.Success)
    ```

1. <span data-ttu-id="68336-222">Passen Sie die Größe der SpriteVisual-Oberfläche an, und füllen Sie sie</span><span class="sxs-lookup"><span data-stu-id="68336-222">Size and brush the surface on the SpriteVisual</span></span>

    ```cs
    brush.Surface = imageSource.Surface;
    ```

1. <span data-ttu-id="68336-223">Führen Sie die App aus, um ein Katzenfoto ohne Sättigung zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="68336-223">Run your app – your results should be a desaturated cat:</span></span>

![Bild ohne Sättigung](images/composition-cat-desaturated.png)

## <a name="more-information"></a><span data-ttu-id="68336-225">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="68336-225">More Information</span></span>

- [<span data-ttu-id="68336-226">Microsoft – GitHub-Seite zum Thema „Komposition“</span><span class="sxs-lookup"><span data-stu-id="68336-226">Microsoft – Composition GitHub</span></span>](https://github.com/Microsoft/composition)
- [**<span data-ttu-id="68336-227">Windows.UI.Composition</span><span class="sxs-lookup"><span data-stu-id="68336-227">Windows.UI.Composition</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn706878)
- [<span data-ttu-id="68336-228">Windows Composition-Team auf Twitter</span><span class="sxs-lookup"><span data-stu-id="68336-228">Windows Composition team on Twitter</span></span>](https://twitter.com/wincomposition)
- [<span data-ttu-id="68336-229">Kompositionsübersicht</span><span class="sxs-lookup"><span data-stu-id="68336-229">Composition Overview</span></span>](https://blogs.windows.com/buildingapps/2015/12/08/awaken-your-creativity-with-the-new-windows-ui-composition/)
- [<span data-ttu-id="68336-230">Grundlagen der visuellen Struktur</span><span class="sxs-lookup"><span data-stu-id="68336-230">Visual Tree Basics</span></span>](composition-visual-tree.md)
- [<span data-ttu-id="68336-231">Kompositionspinsel</span><span class="sxs-lookup"><span data-stu-id="68336-231">Composition Brushes</span></span>](composition-brushes.md)
- [<span data-ttu-id="68336-232">XamlCompositionBrushBase</span><span class="sxs-lookup"><span data-stu-id="68336-232">XamlCompositionBrushBase</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase)
- [<span data-ttu-id="68336-233">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="68336-233">Animation Overview</span></span>](composition-animation.md)
- [<span data-ttu-id="68336-234">Systemeigene DirectX- und Direct2D-Interoperabilität mit „BeginDraw“ und „EndDraw“</span><span class="sxs-lookup"><span data-stu-id="68336-234">Composition native DirectX and Direct2D interoperation with BeginDraw and EndDraw</span></span>](composition-native-interop.md)
