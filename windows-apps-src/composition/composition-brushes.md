---
author: jwmsft
ms.assetid: 03dd256f-78c0-e1b1-3d9f-7b3afab29b2f
title: Kompositionspinsel
description: Ein Pinsel zeichnet den Bereich eines Visual-Objekts mit der zugehörigen Ausgabe. Verschiedene Pinsel haben unterschiedliche Ausgabetypen.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 730d5ae9062fe39533cd615facaf5beaa7d02ffd
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5980321"
---
# <a name="composition-brushes"></a><span data-ttu-id="03735-105">Kompositionspinsel</span><span class="sxs-lookup"><span data-stu-id="03735-105">Composition brushes</span></span>
<span data-ttu-id="03735-106">Alles, was von einer UWP-Anwendung auf dem Bildschirm sichtbar wird angezeigt, da es mit einem Pinsel gezeichnet wurde.</span><span class="sxs-lookup"><span data-stu-id="03735-106">Everything visible on your screen from a UWP application is visible because it was painted by a Brush.</span></span> <span data-ttu-id="03735-107">Mithilfe von Pinseln können Sie Benutzer Objekte der Benutzeroberfläche (UI) mit Inhalt, angefangen bei einfachen, einfarbige Farben zu Bildern oder Zeichnungen für komplexe Effekte Kette zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-107">Brushes enable you to paint user interface (UI) objects with content ranging from simple, solid colors to images or drawings to complex effects chain.</span></span> <span data-ttu-id="03735-108">In diesem Thema werden die Begriffe zum Zeichnen mit CompositionBrush.</span><span class="sxs-lookup"><span data-stu-id="03735-108">This topic introduces the concepts of painting with CompositionBrush.</span></span>

<span data-ttu-id="03735-109">Beachten Sie bei der Arbeit mit XAML-UWP-app können Sie sich entschieden, ein UIElement mit einem [XAML-Pinsel](/windows/uwp/design/style/brushes) oder ein [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush)zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-109">Note, when working with XAML UWP app, you can chose to paint a UIElement with a [XAML Brush](/windows/uwp/design/style/brushes) or a [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush).</span></span> <span data-ttu-id="03735-110">In der Regel ist es einfacher und ratsam, einen XAML-Pinsel auswählen, wenn Ihr Szenario von einem XAML-Pinsel unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="03735-110">Typically, it is easier and advisable to choose a XAML brush if your scenario is supported by a XAML Brush.</span></span> <span data-ttu-id="03735-111">Animieren z. B. die Farbe einer Schaltfläche, die Füllung ein Text oder eine Form mit einem Bild ändern.</span><span class="sxs-lookup"><span data-stu-id="03735-111">For example, animating the color of a button, changing the fill of a text or a shape with an image.</span></span> <span data-ttu-id="03735-112">Andererseits, wenn Sie versuchen, eine Aktion ausführen, die nicht von einem XAML-Pinsel wie Zeichnen mit eine animierte Maske oder eine animierte neun Raster Stretch oder einer effektkette unterstützt wird, können eine CompositionBrush Sie ein UIElement durch die Verwendung von [Zeichnen XamlCompositionBrushBase](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).</span><span class="sxs-lookup"><span data-stu-id="03735-112">On the other hand, if you are trying to do something that is not supported by a XAML brush like painting with an animated mask or an animated nine-grid stretch or an effect chain, you can use a CompositionBrush to paint a UIElement through the use of [XamlCompositionBrushBase](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).</span></span>

<span data-ttu-id="03735-113">Bei der Arbeit mit der visuellen Ebene muss eine CompositionBrush verwendet werden, um den Bereich einer [SpriteVisual](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.SpriteVisual)zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-113">When working with the Visual layer, a CompositionBrush must be used to paint the area of a [SpriteVisual](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.SpriteVisual).</span></span>

-   [<span data-ttu-id="03735-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="03735-114">Prerequisites</span></span>](./composition-brushes.md#prerequisites)
-   [<span data-ttu-id="03735-115">Zeichnen mit CompositionBrush</span><span class="sxs-lookup"><span data-stu-id="03735-115">Paint with CompositionBrush</span></span>](./composition-brushes.md#paint-with-a-compositionbrush)
    -   [<span data-ttu-id="03735-116">Zeichnen Sie mit einer Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="03735-116">Paint with a solid color</span></span>](./composition-brushes.md#paint-with-a-solid-color)
    -   [<span data-ttu-id="03735-117">Zeichnen Sie mit einen linearen Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="03735-117">Paint with a linear gradient</span></span>](./composition-brushes.md#paint-with-a-linear-gradient)
    -   [<span data-ttu-id="03735-118">Zeichnen Sie mit einem Bild</span><span class="sxs-lookup"><span data-stu-id="03735-118">Paint with an image</span></span>](./composition-brushes.md#paint-with-an-image)
    -   [<span data-ttu-id="03735-119">Zeichnen Sie mit einer benutzerdefinierten Zeichnung</span><span class="sxs-lookup"><span data-stu-id="03735-119">Paint with a custom drawing</span></span>](./composition-brushes.md#paint-with-a-custom-drawing)
    -   [<span data-ttu-id="03735-120">Zeichnen Sie mit einem video</span><span class="sxs-lookup"><span data-stu-id="03735-120">Paint with a video</span></span>](./composition-brushes.md#paint-with-a-video)
    -   [<span data-ttu-id="03735-121">Zeichnen Sie mit einem Filtereffekt</span><span class="sxs-lookup"><span data-stu-id="03735-121">Paint with a filter effect</span></span>](./composition-brushes.md#paint-with-a-filter-effect)
    -   [<span data-ttu-id="03735-122">Zeichnen Sie mit einem CompositionBrush mit einer Deckkraftmaske</span><span class="sxs-lookup"><span data-stu-id="03735-122">Paint with a CompositionBrush with an opacity mask</span></span>](./composition-brushes.md#paint-with-a-compositionbrush-with-opacity-mask-applied)
    -   [<span data-ttu-id="03735-123">Zeichnen Sie mit einer CompositionBrush mit NineGrid stretch</span><span class="sxs-lookup"><span data-stu-id="03735-123">Paint with a CompositionBrush using NineGrid stretch</span></span>](./composition-brushes.md#paint-with-a-compositionbrush-using-ninegrid-stretch)
    -   [<span data-ttu-id="03735-124">Zeichnen mit Hintergrund Pixel</span><span class="sxs-lookup"><span data-stu-id="03735-124">Paint using Background Pixels</span></span>](./composition-brushes.md#paint-using-background-pixels)
-   [<span data-ttu-id="03735-125">Kombinieren von CompositionBrushes</span><span class="sxs-lookup"><span data-stu-id="03735-125">Combining CompositionBrushes</span></span>](./composition-brushes.md#combining-compositionbrushes)
-   [<span data-ttu-id="03735-126">Verwenden eine XAML-Pinsel im Vergleich zu CompositionBrush</span><span class="sxs-lookup"><span data-stu-id="03735-126">Using a XAML Brush vs. CompositionBrush</span></span>](./composition-brushes.md#using-a-xaml-brush-vs-compositionbrush)
-   [<span data-ttu-id="03735-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="03735-127">Related Topics</span></span>](./composition-brushes.md#related-topics)

## <a name="prerequisites"></a><span data-ttu-id="03735-128">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="03735-128">Prerequisites</span></span>
<span data-ttu-id="03735-129">In dieser Übersicht wird davon ausgegangen, dass Sie mit der Struktur einer einfachen kompositionsanwendung vertraut sind, wie in der [Übersicht über die visuelle Ebene](visual-layer.md)beschrieben.</span><span class="sxs-lookup"><span data-stu-id="03735-129">This overview assumes that you are familiar with the structure of a basic Composition application, as described in the [Visual layer overview](visual-layer.md).</span></span>

## <a name="paint-with-a-compositionbrush"></a><span data-ttu-id="03735-130">Zeichnen mit einem CompositionBrush</span><span class="sxs-lookup"><span data-stu-id="03735-130">Paint with a CompositionBrush</span></span>

<span data-ttu-id="03735-131">Eine [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush) zeichnet"" einen Bereich mit der zugehörigen Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="03735-131">A [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush) "paints" an area with its output.</span></span> <span data-ttu-id="03735-132">Verschiedene Pinsel haben unterschiedliche Ausgabetypen.</span><span class="sxs-lookup"><span data-stu-id="03735-132">Different brushes have different types of output.</span></span> <span data-ttu-id="03735-133">Einige Pinsel zeichnen einen Bereich mit einer Volltonfarbe, andere mit einem Farbverlauf, Bild, benutzerdefiniertes Zeichnen oder Effekt.</span><span class="sxs-lookup"><span data-stu-id="03735-133">Some brushes paint an area with a solid color, others with a gradient, image, custom drawing, or effect.</span></span> <span data-ttu-id="03735-134">Es gibt auch spezielle Pinsel, die das Verhalten des anderen Pinseln ändern.</span><span class="sxs-lookup"><span data-stu-id="03735-134">There are also specialized brushes that modify the behavior of other brushes.</span></span> <span data-ttu-id="03735-135">Z. B. Deckkraftmaske kann verwendet werden, um zu steuern, welche Bereich durch eine CompositionBrush gezeichnet wird, oder ein neun-Raster kann verwendet werden, um steuern, die Stretch auf eine CompositionBrush angewendet wird, wenn Sie einen Bereich zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-135">For example, opacity mask can be used to control which area is painted by a CompositionBrush, or a nine-grid can be used to control the stretch applied to a CompositionBrush when painting an area.</span></span> <span data-ttu-id="03735-136">CompositionBrush kann von einem der folgenden Typen sein:</span><span class="sxs-lookup"><span data-stu-id="03735-136">CompositionBrush can be of one of the following types:</span></span>

|<span data-ttu-id="03735-137">Klasse</span><span class="sxs-lookup"><span data-stu-id="03735-137">Class</span></span>                                   |<span data-ttu-id="03735-138">Details</span><span class="sxs-lookup"><span data-stu-id="03735-138">Details</span></span>                                         |<span data-ttu-id="03735-139">Eingeführt In</span><span class="sxs-lookup"><span data-stu-id="03735-139">Introduced In</span></span>|
|-------------------------------------|---------------------------------------------------------|--------------------------------------|
|[<span data-ttu-id="03735-140">CompositionColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-140">CompositionColorBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush)         |<span data-ttu-id="03735-141">Zeichnet einen Bereich mit einer Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="03735-141">Paints an area with a solid color</span></span>                        |<span data-ttu-id="03735-142">Windows 10 November-Update (SDK 10586)</span><span class="sxs-lookup"><span data-stu-id="03735-142">Windows10 November Update (SDK 10586)</span></span>|
|[<span data-ttu-id="03735-143">CompositionSurfaceBrush</span><span class="sxs-lookup"><span data-stu-id="03735-143">CompositionSurfaceBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush)       |<span data-ttu-id="03735-144">Zeichnet einen Bereich mit den Inhalt einer [ICompositionSurface](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Composition.ICompositionSurface)</span><span class="sxs-lookup"><span data-stu-id="03735-144">Paints an area with the contents of an [ICompositionSurface](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Composition.ICompositionSurface)</span></span>|<span data-ttu-id="03735-145">Windows 10 November-Update (SDK 10586)</span><span class="sxs-lookup"><span data-stu-id="03735-145">Windows10 November Update (SDK 10586)</span></span>|
|[<span data-ttu-id="03735-146">CompositionEffectBrush</span><span class="sxs-lookup"><span data-stu-id="03735-146">CompositionEffectBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)        |<span data-ttu-id="03735-147">Zeichnet einen Bereich mit den Inhalten eines kompositionseffekts.</span><span class="sxs-lookup"><span data-stu-id="03735-147">Paints an area with the contents of a composition effect</span></span> |<span data-ttu-id="03735-148">Windows 10 November-Update (SDK 10586)</span><span class="sxs-lookup"><span data-stu-id="03735-148">Windows10 November Update (SDK 10586)</span></span>|
|[<span data-ttu-id="03735-149">CompositionMaskBrush</span><span class="sxs-lookup"><span data-stu-id="03735-149">CompositionMaskBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)          |<span data-ttu-id="03735-150">Zeichnet ein visuelles Element mit einer CompositionBrush mit einer Deckkraftmaske</span><span class="sxs-lookup"><span data-stu-id="03735-150">Paints a visual with a CompositionBrush with an opacity mask</span></span> |<span data-ttu-id="03735-151">Windows 10 Anniversary Update (SDK 14393)</span><span class="sxs-lookup"><span data-stu-id="03735-151">Windows10 Anniversary Update (SDK 14393)</span></span>
|[<span data-ttu-id="03735-152">CompositionNineGridBrush</span><span class="sxs-lookup"><span data-stu-id="03735-152">CompositionNineGridBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)      |<span data-ttu-id="03735-153">Zeichnet einen Bereich mit einer CompositionBrush mit einem NineGrid stretch</span><span class="sxs-lookup"><span data-stu-id="03735-153">Paints an area with a CompositionBrush using a NineGrid stretch</span></span> |<span data-ttu-id="03735-154">Windows 10 Anniversary Update SDK (14393)</span><span class="sxs-lookup"><span data-stu-id="03735-154">Windows10 Anniversary Update SDK (14393)</span></span>
|[<span data-ttu-id="03735-155">CompositionLinearGradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-155">CompositionLinearGradientBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)|<span data-ttu-id="03735-156">Zeichnet einen Bereich mit einem linearen Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="03735-156">Paints an area with a linear gradient</span></span>                    |<span data-ttu-id="03735-157">Windows 10 Fall Creators Update (Insider Preview SDK)</span><span class="sxs-lookup"><span data-stu-id="03735-157">Windows 10 Fall Creators Update (Insider Preview SDK)</span></span>
|[<span data-ttu-id="03735-158">CompositionBackdropBrush</span><span class="sxs-lookup"><span data-stu-id="03735-158">CompositionBackdropBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)     |<span data-ttu-id="03735-159">Zeichnet einen Bereich von sampling-Hintergrund Pixel aus der Anwendung oder Pixel direkt hinter das Fenster der Anwendung auf dem Desktop.</span><span class="sxs-lookup"><span data-stu-id="03735-159">Paints an area by sampling background pixels from either the application or pixels directly behind the application's window on desktop.</span></span> <span data-ttu-id="03735-160">Als Eingabe für eine andere CompositionBrush wie ein CompositionEffectBrush verwendet</span><span class="sxs-lookup"><span data-stu-id="03735-160">Used as an input to another CompositionBrush like a CompositionEffectBrush</span></span> | <span data-ttu-id="03735-161">Windows 10 Anniversary Update (SDK 14393)</span><span class="sxs-lookup"><span data-stu-id="03735-161">Windows 10 Anniversary Update (SDK 14393)</span></span>

### <a name="paint-with-a-solid-color"></a><span data-ttu-id="03735-162">Zeichnen Sie mit einer Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="03735-162">Paint with a solid color</span></span>

<span data-ttu-id="03735-163">Eine [CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush) zeichnet einen Bereich mit einer Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="03735-163">A [CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush) paints an area with a solid color.</span></span> <span data-ttu-id="03735-164">Es gibt eine Vielzahl von Möglichkeiten, um die Farbe eines SolidColorBrush angeben.</span><span class="sxs-lookup"><span data-stu-id="03735-164">There are a variety of ways to specify the color of a SolidColorBrush.</span></span> <span data-ttu-id="03735-165">Sie können z. B. angeben, seine Kanäle Alpha, Rot, Grün und Blau (ARGB) oder verwenden Sie eine der vordefinierten Farben durch die [Farben](https://docs.microsoft.com/uwp/api/windows.ui.colors) -Klasse bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="03735-165">For example, you can specify its alpha, red, blue, and green (ARGB) channels or use one of the predefined colors provided by the [Colors](https://docs.microsoft.com/uwp/api/windows.ui.colors) class.</span></span>

<span data-ttu-id="03735-166">Die Abbildung und der Code zeigen im Folgenden eine kleine visuelle Struktur. Es wird ein Rechteck erstellt, dessen Konturen mit einem schwarzen Pinsel gezeichnet sind und das mit einem Pinsel in Volltonfarbe ausgefüllt ist, die den Farbwert „0x9ACD32“ hat.</span><span class="sxs-lookup"><span data-stu-id="03735-166">The following illustration and code shows a small visual tree to create a rectangle that is stroked with a black color brush and painted with a solid color brush that has the color value of 0x9ACD32.</span></span>

![CompositionColorBrush](images/composition-compositioncolorbrush.png)

```cs
Compositor _compositor;
ContainerVisual _container;
SpriteVisual _colorVisual1, _colorVisual2;
CompositionColorBrush _blackBrush, _greenBrush;

_compositor = Window.Current.Compositor;
_container = _compositor.CreateContainerVisual();

_blackBrush = _compositor.CreateColorBrush(Colors.Black);
_colorVisual1= _compositor.CreateSpriteVisual();
_colorVisual1.Brush = _blackBrush;
_colorVisual1.Size = new Vector2(156, 156);
_colorVisual1.Offset = new Vector3(0, 0, 0);
_container.Children.InsertAtBottom(_colorVisual1);

_ greenBrush = _compositor.CreateColorBrush(Color.FromArgb(0xff, 0x9A, 0xCD, 0x32));
_colorVisual2 = _compositor.CreateSpriteVisual();
_colorVisual2.Brush = _greenBrush;
_colorVisual2.Size = new Vector2(150, 150);
_colorVisual2.Offset = new Vector3(3, 3, 0);
_container.Children.InsertAtBottom(_colorVisual2);
```

### <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="03735-168">Zeichnen Sie mit einen linearen Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="03735-168">Paint with a linear gradient</span></span>

<span data-ttu-id="03735-169">Eine [CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush) zeichnet einen Bereich mit einem linearen Farbverlauf.</span><span class="sxs-lookup"><span data-stu-id="03735-169">A [CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush) paints an area with a linear gradient.</span></span> <span data-ttu-id="03735-170">Ein linearer Farbverlauf mischt zwei oder mehr Farben entlang einer Linie, der Farbverlaufsachse an.</span><span class="sxs-lookup"><span data-stu-id="03735-170">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="03735-171">Sie verwenden GradientStop-Objekte, um die Farben in den Farbverlauf und ihre Positionen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="03735-171">You use GradientStop objects to specify the colors in the gradient and their positions.</span></span>

<span data-ttu-id="03735-172">Die folgende Abbildung und der Code zeigt ein SpriteVisual mit LinearGradientBrush 2 hindert, die mit einer roten und gelben Farbe gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="03735-172">The following illustration and code shows a SpriteVisual painted with a LinearGradientBrush with 2 stops using a red and yellow color.</span></span>

![CompositionLinearGradientBrush](images/composition-compositionlineargradientbrush.png)

```cs
Compositor _compositor;
SpriteVisual _gradientVisual;
CompositionLinearGradientBrush _redyellowBrush;

_compositor = Window.Current.Compositor;

_redyellowBrush = _compositor.CreateLinearGradientBrush();
_redyellowBrush.ColorStops.Add(_compositor.CreateColorGradientStop(0, Colors.Red));
_redyellowBrush.ColorStops.Add(_compositor.CreateColorGradientStop(1, Colors.Yellow));
_gradientVisual = _compositor.CreateSpriteVisual();
_gradientVisual.Brush = _redyellowBrush;
_gradientVisual.Size = new Vector2(156, 156);
```

### <a name="paint-with-an-image"></a><span data-ttu-id="03735-174">Zeichnen Sie mit einem Bild</span><span class="sxs-lookup"><span data-stu-id="03735-174">Paint with an image</span></span>

<span data-ttu-id="03735-175">Eine [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) zeichnet einen Bereich mit Pixeln auf einer ICompositionSurface gerendert.</span><span class="sxs-lookup"><span data-stu-id="03735-175">A [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) paints an area with pixels rendered onto an ICompositionSurface.</span></span> <span data-ttu-id="03735-176">Z. B. kann eine CompositionSurfaceBrush verwendet werden, um einen Bereich mit einem Bild auf einer ICompositionSurface Oberfläche mit [Loadedimagesource](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.loadedimagesurface) API gerendert zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-176">For example, a CompositionSurfaceBrush can be used to paint an area with an image rendered onto an ICompositionSurface surface using [LoadedImageSurface](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.loadedimagesurface) API.</span></span>

<span data-ttu-id="03735-177">Die folgende Abbildung und der Code zeigt, mit einer Bitmap einer lakritz gerendert auf eine ICompositionSurface Loadedimagesource mithilfe ein spritevisual-Elements gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="03735-177">The following illustration and code shows a SpriteVisual painted with a bitmap of a licorice rendered onto an ICompositionSurface using LoadedImageSurface.</span></span> <span data-ttu-id="03735-178">Die Eigenschaften des CompositionSurfaceBrush können die Bitmap innerhalb der Grenzen des visuellen Elements ausrichten und Strecken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="03735-178">The properties of CompositionSurfaceBrush can be used to stretch and align the bitmap within the bounds of the visual.</span></span>

![CompositionSurfaceBrush](images/composition-compositionsurfacebrush.png)

```cs
Compositor _compositor;
SpriteVisual _imageVisual;
CompositionSurfaceBrush _imageBrush;

_compositor = Window.Current.Compositor;

_imageBrush = _compositor.CreateSurfaceBrush();

// The loadedSurface has a size of 0x0 till the image has been been downloaded, decoded and loaded to the surface. We can assign the surface to the CompositionSurfaceBrush and it will show up once the image is loaded to the surface.
LoadedImageSurface _loadedSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/licorice.jpg"));
_imageBrush.Surface = _loadedSurface;

_imageVisual = _compositor.CreateSpriteVisual();
_imageVisual.Brush = _imageBrush;
_imageVisual.Size = new Vector2(156, 156);
```

### <a name="paint-with-a-custom-drawing"></a><span data-ttu-id="03735-180">Zeichnen Sie mit einer benutzerdefinierten Zeichnung</span><span class="sxs-lookup"><span data-stu-id="03735-180">Paint with a custom drawing</span></span>
<span data-ttu-id="03735-181">Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, um einen Bereich mit Pixeln aus einer ICompositionSurface gerendert mithilfe von [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm) (oder D2D) zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-181">A [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) can also be used to paint an area with pixels from an ICompositionSurface rendered using [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm) (or D2D).</span></span>

<span data-ttu-id="03735-182">Der folgende Code zeigt, dass ein SpriteVisual mit einem führen Sie auf eine ICompositionSurface gerenderte Text gezeichnet mithilfe von Win2D.</span><span class="sxs-lookup"><span data-stu-id="03735-182">The following code shows a SpriteVisual painted with a text run rendered onto an ICompositionSurface using Win2D.</span></span> <span data-ttu-id="03735-183">Beachten Sie, um Win2D zu verwenden, Sie das [Win2D-NuGet](http://www.nuget.org/packages/Win2D.uwp) -Paket in Ihr Projekt einschließen müssen.</span><span class="sxs-lookup"><span data-stu-id="03735-183">Note, in order to use Win2D you need to include the [Win2D NuGet](http://www.nuget.org/packages/Win2D.uwp) package into your project.</span></span>

```cs
Compositor _compositor;
CanvasDevice _device;
CompositionGraphicsDevice _compositionGraphicsDevice;
SpriteVisual _drawingVisual;
CompositionSurfaceBrush _drawingBrush;

_device = CanvasDevice.GetSharedDevice();
_compositionGraphicsDevice = CanvasComposition.CreateCompositionGraphicsDevice(_compositor, _device);

_drawingBrush = _compositor.CreateSurfaceBrush();
CompositionDrawingSurface _drawingSurface = _compositionGraphicsDevice.CreateDrawingSurface(new Size(256, 256), DirectXPixelFormat.B8G8R8A8UIntNormalized, DirectXAlphaMode.Premultiplied);

using (var ds = CanvasComposition.CreateDrawingSession(_drawingSurface))
{
     ds.Clear(Colors.Transparent);
     var rect = new Rect(new Point(2, 2), (_drawingSurface.Size.ToVector2() - new Vector2(4, 4)).ToSize());
     ds.FillRoundedRectangle(rect, 15, 15, Colors.LightBlue);
     ds.DrawRoundedRectangle(rect, 15, 15, Colors.Gray, 2);
     ds.DrawText("This is a composition drawing surface", rect, Colors.Black, new CanvasTextFormat()
     {
          FontFamily = "Comic Sans MS",
          FontSize = 32,
          WordWrapping = CanvasWordWrapping.WholeWord,
          VerticalAlignment = CanvasVerticalAlignment.Center,
          HorizontalAlignment = CanvasHorizontalAlignment.Center
     }
);

_drawingBrush.Surface = _drawingSurface;

_drawingVisual = _compositor.CreateSpriteVisual();
_drawingVisual.Brush = _drawingBrush;
_drawingVisual.Size = new Vector2(156, 156);
```

<span data-ttu-id="03735-184">Auf ähnliche Weise kann die CompositionSurfaceBrush auch zum Zeichnen eines spritevisual-Elements mit einem Win2D Interop verwenden Spielinhalte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="03735-184">Similarly, the CompositionSurfaceBrush can also be used to paint a SpriteVisual with a SwapChain using Win2D interop.</span></span> <span data-ttu-id="03735-185">[In diesem Beispiel](https://github.com/Microsoft/Win2D-Samples/tree/master/CompositionExample) enthält ein Beispiel zur Verwendung von Win2D zum Zeichnen eines spritevisual-Elements mit einem Spielinhalte.</span><span class="sxs-lookup"><span data-stu-id="03735-185">[This sample](https://github.com/Microsoft/Win2D-Samples/tree/master/CompositionExample) provides an example of how to use Win2D to paint a SpriteVisual with a swapchain.</span></span>

### <a name="paint-with-a-video"></a><span data-ttu-id="03735-186">Zeichnen Sie mit einem video</span><span class="sxs-lookup"><span data-stu-id="03735-186">Paint with a video</span></span>
<span data-ttu-id="03735-187">Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, um einen Bereich mit Pixeln aus einer ICompositionSurface mit einem Video über der [MediaPlayer](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer) -Klasse geladen gerendert zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="03735-187">A [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) can also be used to paint an area with pixels from an ICompositionSurface rendered using a video loaded through the [MediaPlayer](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer) class.</span></span>

<span data-ttu-id="03735-188">Der folgende Code zeigt, dass ein SpriteVisual mit einem Video auf einer ICompositionSurface geladen gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="03735-188">The following code shows a SpriteVisual painted with a video loaded onto an ICompositionSurface.</span></span>

```cs
Compositor _compositor;
SpriteVisual _videoVisual;
CompositionSurfaceBrush _videoBrush;

// MediaPlayer set up with a create from URI

_mediaPlayer = new MediaPlayer();

// Get a source from a URI. This could also be from a file via a picker or a stream
var source = MediaSource.CreateFromUri(new Uri("http://go.microsoft.com/fwlink/?LinkID=809007&clcid=0x409"));
var item = new MediaPlaybackItem(source);
_mediaPlayer.Source = item;
_mediaPlayer.IsLoopingEnabled = true;

// Get the surface from MediaPlayer and put it on a brush
_videoSurface = _mediaPlayer.GetSurface(_compositor);
_videoBrush = _compositor.CreateSurfaceBrush(_videoSurface.CompositionSurface);

_videoVisual = _compositor.CreateSpriteVisual();
_videoVisual.Brush = _videoBrush;
_videoVisual.Size = new Vector2(156, 156);
```

### <a name="paint-with-a-filter-effect"></a><span data-ttu-id="03735-189">Zeichnen Sie mit einem Filtereffekt</span><span class="sxs-lookup"><span data-stu-id="03735-189">Paint with a filter effect</span></span>

<span data-ttu-id="03735-190">Eine [CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush) zeichnet einen Bereich mit der Ausgabe von einem CompositionEffect.</span><span class="sxs-lookup"><span data-stu-id="03735-190">A [CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush) paints an area with output of a CompositionEffect.</span></span> <span data-ttu-id="03735-191">Effekte in der visuellen Ebene können als animierbaren auf eine Auflistung von Quellinhalt z. B. Farben, Farbverläufe, Bilder, Videos, Swapchains, Regionen der Benutzeroberfläche oder Strukturen von visuellen Elementen angewendeten Filtereffekte betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="03735-191">Effects in the Visual Layer may be thought of as animatable filter effects applied to a collection of source content such as colors, gradients, images, videos, swapchains, regions of your UI, or trees of Visuals.</span></span> <span data-ttu-id="03735-192">Der Inhalt der Quelle wird in der Regel mit einer anderen CompositionBrush angegeben.</span><span class="sxs-lookup"><span data-stu-id="03735-192">The source content is typically specified using another CompositionBrush.</span></span>

<span data-ttu-id="03735-193">Die folgende Abbildung und der Code zeigt ein spritevisual-Elements gezeichnet mit einem Bild einer Katze, die Sättigung Filtereffekt angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="03735-193">The following illustration and code shows a SpriteVisual painted with an image of a cat that has desaturation filter effect applied.</span></span>

![CompositionEffectBrush](images/composition-cat-desaturated.png)

```cs
Compositor _compositor;
SpriteVisual _effectVisual;
CompositionEffectBrush _effectBrush;

_compositor = Window.Current.Compositor;

var graphicsEffect = new SaturationEffect {
                              Saturation = 0.0f,
                              Source = new CompositionEffectSourceParameter("mySource")
                         };

var effectFactory = _compositor.CreateEffectFactory(graphicsEffect);
_effectBrush = effectFactory.CreateBrush();

CompositionSurfaceBrush surfaceBrush =_compositor.CreateSurfaceBrush();
LoadedImageSurface loadedSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/cat.jpg"));
SurfaceBrush.surface = loadedSurface;

_effectBrush.SetSourceParameter("mySource", surfaceBrush);

_effectVisual = _compositor.CreateSpriteVisual();
_effectVisual.Brush = _effectBrush;
_effectVisual.Size = new Vector2(156, 156);
```

<span data-ttu-id="03735-195">Weitere Informationen zum Erstellen eines Effekts mit CompositionBrushes finden Sie unter [Effekte in der visuellen Ebene](https://docs.microsoft.com/en-us/windows/uwp/composition/composition-effects)</span><span class="sxs-lookup"><span data-stu-id="03735-195">For more information on creating an Effect using CompositionBrushes see [Effects in Visual layer](https://docs.microsoft.com/en-us/windows/uwp/composition/composition-effects)</span></span>

### <a name="paint-with-a-compositionbrush-with-opacity-mask-applied"></a><span data-ttu-id="03735-196">Zeichnen Sie mit einem CompositionBrush mit Deckkraftmaske angewendet</span><span class="sxs-lookup"><span data-stu-id="03735-196">Paint with a CompositionBrush with opacity mask applied</span></span>

<span data-ttu-id="03735-197">Eine [CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush) zeichnet einen Bereich mit einem CompositionBrush mit einer Deckkraftmaske angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="03735-197">A [CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush) paints an area with a CompositionBrush with an opacity mask applied to it.</span></span> <span data-ttu-id="03735-198">Die Quelle des die Deckkraftmaske kann alle CompositionBrush des Typs CompositionColorBrush, CompositionLinearGradientBrush, CompositionSurfaceBrush, CompositionEffectBrush oder CompositionNineGridBrush sein.</span><span class="sxs-lookup"><span data-stu-id="03735-198">The source of the opacity mask can be any CompositionBrush of type CompositionColorBrush, CompositionLinearGradientBrush, CompositionSurfaceBrush, CompositionEffectBrush, or CompositionNineGridBrush.</span></span> <span data-ttu-id="03735-199">Die Deckkraftmaske muss als eine CompositionSurfaceBrush angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="03735-199">The opacity mask must be specified as a CompositionSurfaceBrush.</span></span>

<span data-ttu-id="03735-200">Die folgende Abbildung und der Code zeigt ein Element, das mit einem CompositionMaskBrush SpriteVisual.</span><span class="sxs-lookup"><span data-stu-id="03735-200">The following illustration and code shows a SpriteVisual painted with a CompositionMaskBrush.</span></span> <span data-ttu-id="03735-201">Die Quelle der Maske ist ein CompositionLinearGradientBrush die maskiert wird, um einen Kreis mit einem Bild Kreises als Maske aussehen.</span><span class="sxs-lookup"><span data-stu-id="03735-201">The source of the mask is a CompositionLinearGradientBrush which is masked to look like a circle using an image of circle as a mask.</span></span>

![CompositionMaskBrush](images/composition-compositionmaskbrush.png)

```cs
Compositor _compositor;
SpriteVisual _maskVisual;
CompositionMaskBrush _maskBrush;

_compositor = Window.Current.Compositor;

_maskBrush = _compositor.CreateMaskBrush();

CompositionLinearGradientBrush _sourceGradient = _compositor.CreateLinearGradientBrush();
_sourceGradient.ColorStops.Add(_compositor.CreateColorGradientStop(0,Colors.Red));
_sourceGradient.ColorStops.Add(_compositor.CreateColorGradientStop(1,Colors.Yellow));
_maskBrush.Source = _sourceGradient;

LoadedImageSurface loadedSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/circle.png"), new Size(156.0, 156.0));
_maskBrush.Mask = _compositor.CreateSurfaceBrush(loadedSurface);

_maskVisual = _compositor.CreateSpriteVisual();
_maskVisual.Brush = _maskBrush;
_maskVisual.Size = new Vector2(156, 156);
```

### <a name="paint-with-a-compositionbrush-using-ninegrid-stretch"></a><span data-ttu-id="03735-203">Zeichnen Sie mit einer CompositionBrush mit NineGrid stretch</span><span class="sxs-lookup"><span data-stu-id="03735-203">Paint with a CompositionBrush using NineGrid stretch</span></span>

<span data-ttu-id="03735-204">Eine [CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush) zeichnet einen Bereich mit einem CompositionBrush, die mit der neun Raster-gestreckt wird.</span><span class="sxs-lookup"><span data-stu-id="03735-204">A [CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush) paints an area with a CompositionBrush that is stretched using the nine-grid metaphor.</span></span> <span data-ttu-id="03735-205">Die neun Raster-können Sie Rahmen und Ecken von einem "compositionbrush" anders als den Mittelpunkt gestreckt.</span><span class="sxs-lookup"><span data-stu-id="03735-205">The nine-grid metaphor enables you to stretch edges and corners of a CompositionBrush differently than its center.</span></span> <span data-ttu-id="03735-206">Die Quelle des der neun Raster Stretch kann, indem Sie alle CompositionBrush des Typs CompositionColorBrush, CompositionSurfaceBrush oder CompositionEffectBrush.</span><span class="sxs-lookup"><span data-stu-id="03735-206">The source of the nine-grid stretch can by any CompositionBrush of type CompositionColorBrush, CompositionSurfaceBrush, or CompositionEffectBrush.</span></span>

<span data-ttu-id="03735-207">Der folgende Code zeigt, dass ein SpriteVisual mit einem CompositionNineGridBrush gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="03735-207">The following code shows a SpriteVisual painted with a CompositionNineGridBrush.</span></span> <span data-ttu-id="03735-208">Die Quelle der Maske ist ein CompositionSurfaceBrush die gestreckt wird mit einem neun-Raster.</span><span class="sxs-lookup"><span data-stu-id="03735-208">The source of the mask is a CompositionSurfaceBrush which is stretched using a Nine-Grid.</span></span>

```cs
Compositor _compositor;
SpriteVisual _nineGridVisual;
CompositionNineGridBrush _nineGridBrush;

_compositor = Window.Current.Compositor;

_ninegridBrush = _compositor.CreateNineGridBrush();

// nineGridImage.png is 50x50 pixels; nine-grid insets, as measured relative to the actual size of the image, are: left = 1, top = 5, right = 10, bottom = 20 (in pixels)

LoadedImageSurface _imageSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/nineGridImage.png"));
_nineGridBrush.Source = _compositor.CreateSurfaceBrush(_imageSurface);

// set Nine-Grid Insets

_ninegridBrush.SetInsets(1, 5, 10, 20);

// set appropriate Stretch on SurfaceBrush for Center of Nine-Grid

sourceBrush.Stretch = CompositionStretch.Fill;

_nineGridVisual = _compositor.CreateSpriteVisual();
_nineGridVisual.Brush = _ninegridBrush;
_nineGridVisual.Size = new Vector2(100, 75);
```

### <a name="paint-using-background-pixels"></a><span data-ttu-id="03735-209">Zeichnen mit Hintergrund Pixel</span><span class="sxs-lookup"><span data-stu-id="03735-209">Paint using Background Pixels</span></span>

<span data-ttu-id="03735-210">Eine [CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush) zeichnet einen Bereich mit den Inhalt hinter den Bereich.</span><span class="sxs-lookup"><span data-stu-id="03735-210">A [CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)  paints an area with the content behind the area.</span></span> <span data-ttu-id="03735-211">Eine CompositionBackdropBrush wird nie alleine verwendet, jedoch stattdessen als Eingabe für eine andere CompositionBrush wie ein EffectBrush verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="03735-211">A CompositionBackdropBrush is never used on its own, but instead is used as an input to another CompositionBrush like an EffectBrush.</span></span> <span data-ttu-id="03735-212">Beispielsweise können Sie einen Effekt Milchglas mithilfe einer CompositionBackdropBrush als Eingabe für einen Weichzeichnereffekt zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="03735-212">For example, by using a CompositionBackdropBrush as an input to a Blur effect, you can achieve a frosted glass effect.</span></span>

<span data-ttu-id="03735-213">Der folgende Code zeigt eine kleine visuelle Struktur ein Bild mit CompositionSurfaceBrush und eine Überlagerung Milchglas über dem Bild erstellt.</span><span class="sxs-lookup"><span data-stu-id="03735-213">The following code shows a small visual tree to create an image using CompositionSurfaceBrush and a frosted glass overlay above the image.</span></span> <span data-ttu-id="03735-214">Die Überlagerung Milchglas wird durch das Platzieren eines spritevisual-Elements mit einem EffectBrush über dem Bild gefüllt erstellt.</span><span class="sxs-lookup"><span data-stu-id="03735-214">The frosted glass overlay is created by placing a SpriteVisual filled with an EffectBrush above the image.</span></span> <span data-ttu-id="03735-215">Die EffectBrush verwendet eine CompositionBackdropBrush als Eingabe für den Weichzeichnereffekt zu.</span><span class="sxs-lookup"><span data-stu-id="03735-215">The EffectBrush uses a CompositionBackdropBrush as an input to the blur effect.</span></span>

```cs
Compositor _compositor;
SpriteVisual _containerVisual;
SpriteVisual _imageVisual;
SpriteVisual _backdropVisual;

_compositor = Window.Current.Compositor;

// Create container visual to host the visual tree
_containerVisual = _compositor.CreateContainerVisual();

// Create _imageVisual and add it to the bottom of the container visual.
// Paint the visual with an image.

CompositionSurfaceBrush _licoriceBrush = _compositor.CreateSurfaceBrush();

LoadedImageSurface loadedSurface = 
    LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/licorice.jpg"));
_licoriceBrush.Surface = loadedSurface;

_imageVisual = _compositor.CreateSpriteVisual();
_imageVisual.Brush = _licoriceBrush;
_imageVisual.Size = new Vector2(156, 156);
_imageVisual.Offset = new Vector3(0, 0, 0);
_containerVisual.Children.InsertAtBottom(_imageVisual)

// Create a SpriteVisual and add it to the top of the containerVisual.
// Paint the visual with an EffectBrush that applies blur to the content
// underneath the Visual to create a frosted glass effect.

GaussianBlurEffect blurEffect = new GaussianBlurEffect(){
                                    Name = "Blur",
                                    BlurAmount = 1.0f,
                                    BorderMode = EffectBorderMode.Hard,
                                    Source = new CompositionEffectSourceParameter("source");
                                    };

CompositionEffectFactory blurEffectFactory = _compositor.CreateEffectFactory(blurEffect);
CompositionEffectBrush _backdropBrush = blurEffectFactory.CreateBrush();

// Create a BackdropBrush and bind it to the EffectSourceParameter source

_backdropBrush.SetSourceParameter("source", _compositor.CreateBackdropBrush());
_backdropVisual = _compositor.CreateSpriteVisual();
_backdropVisual.Brush = _licoriceBrush;
_backdropVisual.Size = new Vector2(78, 78);
_backdropVisual.Offset = new Vector3(39, 39, 0);
_containerVisual.Children.InsertAtTop(_backdropVisual);
```

## <a name="combining-compositionbrushes"></a><span data-ttu-id="03735-216">Kombinieren von CompositionBrushes</span><span class="sxs-lookup"><span data-stu-id="03735-216">Combining CompositionBrushes</span></span>
<span data-ttu-id="03735-217">Eine Reihe von CompositionBrushes verwenden Sie andere CompositionBrushes als Eingaben.</span><span class="sxs-lookup"><span data-stu-id="03735-217">A number of CompositionBrushes use other CompositionBrushes as inputs.</span></span> <span data-ttu-id="03735-218">Beispielsweise kann mithilfe der Methode SetSourceParameter verwendet werden zu einem anderen CompositionBrush als Eingabe für eine CompositionEffectBrush festgelegt.</span><span class="sxs-lookup"><span data-stu-id="03735-218">For example, using the SetSourceParameter method can be used to set another CompositionBrush as an input to a CompositionEffectBrush.</span></span> <span data-ttu-id="03735-219">Die folgende Tabelle skizziert die unterstützten Kombinationen von CompositionBrushes.</span><span class="sxs-lookup"><span data-stu-id="03735-219">The table below outlines the supported combinations of CompositionBrushes.</span></span> <span data-ttu-id="03735-220">Beachten Sie, dass eine nicht unterstützte Kombination eine Ausnahme ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="03735-220">Note, that using an unsupported combination will throw an exception.</span></span>

<table>
<tbody>
<tr>
<th><span data-ttu-id="03735-221">Brush</span><span class="sxs-lookup"><span data-stu-id="03735-221">Brush</span></span></th>
<th><span data-ttu-id="03735-222">EffectBrush.SetSourceParameter()</span><span class="sxs-lookup"><span data-stu-id="03735-222">EffectBrush.SetSourceParameter()</span></span></th>
<th><span data-ttu-id="03735-223">MaskBrush.Mask</span><span class="sxs-lookup"><span data-stu-id="03735-223">MaskBrush.Mask</span></span></th>
<th><span data-ttu-id="03735-224">MaskBrush.Source</span><span class="sxs-lookup"><span data-stu-id="03735-224">MaskBrush.Source</span></span></th>
<th><span data-ttu-id="03735-225">NineGridBrush.Source</span><span class="sxs-lookup"><span data-stu-id="03735-225">NineGridBrush.Source</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="03735-226">CompositionColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-226">CompositionColorBrush</span></span></td>
<td><span data-ttu-id="03735-227">JA</span><span class="sxs-lookup"><span data-stu-id="03735-227">YES</span></span></td>
<td><span data-ttu-id="03735-228">JA</span><span class="sxs-lookup"><span data-stu-id="03735-228">YES</span></span></td>
<td><span data-ttu-id="03735-229">JA</span><span class="sxs-lookup"><span data-stu-id="03735-229">YES</span></span></td>
<td><span data-ttu-id="03735-230">JA</span><span class="sxs-lookup"><span data-stu-id="03735-230">YES</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-231">CompositionLinear</span><span class="sxs-lookup"><span data-stu-id="03735-231">CompositionLinear</span></span><br /><span data-ttu-id="03735-232">GradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-232">GradientBrush</span></span></td>
<td><span data-ttu-id="03735-233">JA</span><span class="sxs-lookup"><span data-stu-id="03735-233">YES</span></span></td>
<td><span data-ttu-id="03735-234">JA</span><span class="sxs-lookup"><span data-stu-id="03735-234">YES</span></span></td>
<td><span data-ttu-id="03735-235">JA</span><span class="sxs-lookup"><span data-stu-id="03735-235">YES</span></span></td>
<td><span data-ttu-id="03735-236">NO</span><span class="sxs-lookup"><span data-stu-id="03735-236">NO</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-237">CompositionSurfaceBrush</span><span class="sxs-lookup"><span data-stu-id="03735-237">CompositionSurfaceBrush</span></span></td>
<td><span data-ttu-id="03735-238">JA</span><span class="sxs-lookup"><span data-stu-id="03735-238">YES</span></span></td>
<td><span data-ttu-id="03735-239">JA</span><span class="sxs-lookup"><span data-stu-id="03735-239">YES</span></span></td>
<td><span data-ttu-id="03735-240">JA</span><span class="sxs-lookup"><span data-stu-id="03735-240">YES</span></span></td>
<td><span data-ttu-id="03735-241">JA</span><span class="sxs-lookup"><span data-stu-id="03735-241">YES</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-242">CompositionEffectBrush</span><span class="sxs-lookup"><span data-stu-id="03735-242">CompositionEffectBrush</span></span></td>
<td><span data-ttu-id="03735-243">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-243">NO</span></span></td>
<td><span data-ttu-id="03735-244">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-244">NO</span></span></td>
<td><span data-ttu-id="03735-245">JA</span><span class="sxs-lookup"><span data-stu-id="03735-245">YES</span></span></td>
<td><span data-ttu-id="03735-246">NO</span><span class="sxs-lookup"><span data-stu-id="03735-246">NO</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-247">CompositionMaskBrush</span><span class="sxs-lookup"><span data-stu-id="03735-247">CompositionMaskBrush</span></span></td>
<td><span data-ttu-id="03735-248">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-248">NO</span></span></td>
<td><span data-ttu-id="03735-249">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-249">NO</span></span></td>
<td><span data-ttu-id="03735-250">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-250">NO</span></span></td>
<td><span data-ttu-id="03735-251">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-251">NO</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-252">CompositionNineGridBrush</span><span class="sxs-lookup"><span data-stu-id="03735-252">CompositionNineGridBrush</span></span></td>
<td><span data-ttu-id="03735-253">JA</span><span class="sxs-lookup"><span data-stu-id="03735-253">YES</span></span></td>
<td><span data-ttu-id="03735-254">JA</span><span class="sxs-lookup"><span data-stu-id="03735-254">YES</span></span></td>
<td><span data-ttu-id="03735-255">JA</span><span class="sxs-lookup"><span data-stu-id="03735-255">YES</span></span></td>
<td><span data-ttu-id="03735-256">NO</span><span class="sxs-lookup"><span data-stu-id="03735-256">NO</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="03735-257">CompositionBackdropBrush</span><span class="sxs-lookup"><span data-stu-id="03735-257">CompositionBackdropBrush</span></span></td>
<td><span data-ttu-id="03735-258">JA</span><span class="sxs-lookup"><span data-stu-id="03735-258">YES</span></span></td>
<td><span data-ttu-id="03735-259">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-259">NO</span></span></td>
<td><span data-ttu-id="03735-260">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-260">NO</span></span></td>
<td><span data-ttu-id="03735-261">NEIN</span><span class="sxs-lookup"><span data-stu-id="03735-261">NO</span></span></td>
</tr>
</tbody>
</table>


## <a name="using-a-xaml-brush-vs-compositionbrush"></a><span data-ttu-id="03735-262">Verwenden eine XAML-Pinsel im Vergleich zu CompositionBrush</span><span class="sxs-lookup"><span data-stu-id="03735-262">Using a XAML Brush vs. CompositionBrush</span></span>

<span data-ttu-id="03735-263">Die folgende Tabelle enthält eine Liste mit Szenarien und gibt an, ob XAML oder Komposition Pinsel verwenden beim Zeichnen von UIElement oder eines spritevisual-Elements in Ihrer Anwendung vorgeschrieben ist.</span><span class="sxs-lookup"><span data-stu-id="03735-263">The following table provides a list of scenarios and whether XAML or Composition brush use is prescribed when painting a UIElement or a SpriteVisual in your application.</span></span> 

> [!NOTE]
> <span data-ttu-id="03735-264">Wenn ein CompositionBrush für ein XAML-UIElement vorgeschlagen wird, wird davon ausgegangen, dass die CompositionBrush verpackt ist eine XamlCompositionBrushBase verwenden.</span><span class="sxs-lookup"><span data-stu-id="03735-264">If a CompositionBrush is suggested for a XAML UIElement, it is assumed that the CompositionBrush is packaged using a XamlCompositionBrushBase.</span></span>

|<span data-ttu-id="03735-265">Szenario</span><span class="sxs-lookup"><span data-stu-id="03735-265">Scenario</span></span>                                                                   | <span data-ttu-id="03735-266">XAML-UIElement</span><span class="sxs-lookup"><span data-stu-id="03735-266">XAML UIElement</span></span>                                                                                                |<span data-ttu-id="03735-267">Komposition SpriteVisual</span><span class="sxs-lookup"><span data-stu-id="03735-267">Composition SpriteVisual</span></span>
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------
|<span data-ttu-id="03735-268">Zeichnen eines Bereichs mit Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="03735-268">Paint an area with solid color</span></span>                                             |[<span data-ttu-id="03735-269">SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-269">SolidColorBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[<span data-ttu-id="03735-270">CompositionColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-270">CompositionColorBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|<span data-ttu-id="03735-271">Zeichnen eines Bereichs mit animierten Farbe</span><span class="sxs-lookup"><span data-stu-id="03735-271">Paint an area with animated color</span></span>                                          |[<span data-ttu-id="03735-272">SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-272">SolidColorBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[<span data-ttu-id="03735-273">CompositionColorBrush</span><span class="sxs-lookup"><span data-stu-id="03735-273">CompositionColorBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|<span data-ttu-id="03735-274">Zeichnen eines Bereichs mit einem statischen Farbverlauf</span><span class="sxs-lookup"><span data-stu-id="03735-274">Paint an area with a static gradient</span></span>                                       |[<span data-ttu-id="03735-275">LinearGradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-275">LinearGradientBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/BR210108)                            |[<span data-ttu-id="03735-276">CompositionLinearGradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-276">CompositionLinearGradientBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|<span data-ttu-id="03735-277">Zeichnen eines Bereichs mit animierten Farbverlaufsstopps</span><span class="sxs-lookup"><span data-stu-id="03735-277">Paint an area with animated gradient stops</span></span>                                 |[<span data-ttu-id="03735-278">CompositionLinearGradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-278">CompositionLinearGradientBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)                                                                                 |[<span data-ttu-id="03735-279">CompositionLinearGradientBrush</span><span class="sxs-lookup"><span data-stu-id="03735-279">CompositionLinearGradientBrush</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|<span data-ttu-id="03735-280">Zeichnen eines Bereichs mit einem Bild</span><span class="sxs-lookup"><span data-stu-id="03735-280">Paint an area with an image</span></span>                                                |[<span data-ttu-id="03735-281">ImageBrush</span><span class="sxs-lookup"><span data-stu-id="03735-281">ImageBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/BR210101)                                     |[<span data-ttu-id="03735-282">CompositionSurfaceBrush</span><span class="sxs-lookup"><span data-stu-id="03735-282">CompositionSurfaceBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/Mt589415)
|<span data-ttu-id="03735-283">Zeichnen eines Bereichs mit einer Webseite</span><span class="sxs-lookup"><span data-stu-id="03735-283">Paint an area with a webpage</span></span>                                               |[<span data-ttu-id="03735-284">WebViewBrush</span><span class="sxs-lookup"><span data-stu-id="03735-284">WebViewBrush</span></span>](https://msdn.microsoft.com/library/windows/apps/BR227703)                                   |<span data-ttu-id="03735-285">n.a.</span><span class="sxs-lookup"><span data-stu-id="03735-285">N/A</span></span>
|<span data-ttu-id="03735-286">Zeichnen eines Bereichs mit einem Bild mit NineGrid stretch</span><span class="sxs-lookup"><span data-stu-id="03735-286">Paint an area with an image using NineGrid stretch</span></span>                         |[<span data-ttu-id="03735-287">Image-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="03735-287">Image Control</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Image)                   |[<span data-ttu-id="03735-288">CompositionNineGridBrush</span><span class="sxs-lookup"><span data-stu-id="03735-288">CompositionNineGridBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|<span data-ttu-id="03735-289">Zeichnen eines Bereichs mit animierten NineGrid stretch</span><span class="sxs-lookup"><span data-stu-id="03735-289">Paint an area with animated NineGrid stretch</span></span>                               |[<span data-ttu-id="03735-290">CompositionNineGridBrush</span><span class="sxs-lookup"><span data-stu-id="03735-290">CompositionNineGridBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)                                                                                       |[<span data-ttu-id="03735-291">CompositionNineGridBrush</span><span class="sxs-lookup"><span data-stu-id="03735-291">CompositionNineGridBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|<span data-ttu-id="03735-292">Zeichnen eines Bereichs mit einem Spielinhalte</span><span class="sxs-lookup"><span data-stu-id="03735-292">Paint an area with a swapchain</span></span>                                             |[<span data-ttu-id="03735-293">SwapChainPanel</span><span class="sxs-lookup"><span data-stu-id="03735-293">SwapChainPanel</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel)                                                                                                 |<span data-ttu-id="03735-294">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Spielinhalte Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="03735-294">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) w/ swapchain interop</span></span>
|<span data-ttu-id="03735-295">Zeichnen eines Bereichs mit einem video</span><span class="sxs-lookup"><span data-stu-id="03735-295">Paint an area with a video</span></span>                                                 |[<span data-ttu-id="03735-296">MediaElement</span><span class="sxs-lookup"><span data-stu-id="03735-296">MediaElement</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187272.aspx)                                                                                                  |<span data-ttu-id="03735-297">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Media-Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="03735-297">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) w/ media interop</span></span>
|<span data-ttu-id="03735-298">Zeichnen eines Bereichs mit benutzerdefinierten 2D Zeichnung</span><span class="sxs-lookup"><span data-stu-id="03735-298">Paint an area with custom 2D drawing</span></span>                                       |<span data-ttu-id="03735-299">[CanvasControl](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_UI_Xaml_CanvasControl.htm) von Win2D</span><span class="sxs-lookup"><span data-stu-id="03735-299">[CanvasControl](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_UI_Xaml_CanvasControl.htm) from Win2D</span></span>                                                                                                 |<span data-ttu-id="03735-300">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Win2D-Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="03735-300">[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) w/ Win2D interop</span></span>
|<span data-ttu-id="03735-301">Zeichnen eines Bereichs mit nicht animierte Maske</span><span class="sxs-lookup"><span data-stu-id="03735-301">Paint an area with non-animated mask</span></span>                                       |<span data-ttu-id="03735-302">Verwenden Sie XAML- [Formen](https://docs.microsoft.com/windows/uwp/graphics/drawing-shapes) , um eine Maske definieren</span><span class="sxs-lookup"><span data-stu-id="03735-302">Use XAML [shapes](https://docs.microsoft.com/windows/uwp/graphics/drawing-shapes) to define a mask</span></span>   |[<span data-ttu-id="03735-303">CompositionMaskBrush</span><span class="sxs-lookup"><span data-stu-id="03735-303">CompositionMaskBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|<span data-ttu-id="03735-304">Zeichnen eines Bereichs mit eine animierte Maske</span><span class="sxs-lookup"><span data-stu-id="03735-304">Paint an area with an animated mask</span></span>                                        |[<span data-ttu-id="03735-305">CompositionMaskBrush</span><span class="sxs-lookup"><span data-stu-id="03735-305">CompositionMaskBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)                                                                                           |[<span data-ttu-id="03735-306">CompositionMaskBrush</span><span class="sxs-lookup"><span data-stu-id="03735-306">CompositionMaskBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|<span data-ttu-id="03735-307">Zeichnen eines Bereichs mit einem Filtereffekt animierte</span><span class="sxs-lookup"><span data-stu-id="03735-307">Paint an area with an animated filter effect</span></span>                               |[<span data-ttu-id="03735-308">CompositionEffectBrush</span><span class="sxs-lookup"><span data-stu-id="03735-308">CompositionEffectBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)                                                                                         |[<span data-ttu-id="03735-309">CompositionEffectBrush</span><span class="sxs-lookup"><span data-stu-id="03735-309">CompositionEffectBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)
|<span data-ttu-id="03735-310">Zeichnen eines Bereichs mit einem Effekt auf Hintergrund Pixel angewendet</span><span class="sxs-lookup"><span data-stu-id="03735-310">Paint an area with an effect applied to background pixels</span></span>        |[<span data-ttu-id="03735-311">CompositionBackdropBrush</span><span class="sxs-lookup"><span data-stu-id="03735-311">CompositionBackdropBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)                                                                                        |[<span data-ttu-id="03735-312">CompositionBackdropBrush</span><span class="sxs-lookup"><span data-stu-id="03735-312">CompositionBackdropBrush</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)

## <a name="related-topics"></a><span data-ttu-id="03735-313">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="03735-313">Related Topics</span></span>

[<span data-ttu-id="03735-314">Komposition native DirectX und Direct2D-Interoperabilität mit "beginDraw" und "EndDraw"</span><span class="sxs-lookup"><span data-stu-id="03735-314">Composition native DirectX and Direct2D interop with BeginDraw and EndDraw</span></span>](composition-native-interop.md)

[<span data-ttu-id="03735-315">XAML-Pinsel-Interoperabilität mit XamlCompositionBrushBase</span><span class="sxs-lookup"><span data-stu-id="03735-315">XAML brush interop with XamlCompositionBrushBase</span></span>](/windows/uwp/design/style/brushes#xamlcompositionbrushbase)
