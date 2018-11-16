---
author: daneuber
title: Kompositionsschatten
description: Der Schatten APIs können Sie dynamische anpassbare Schatten UI-Inhalte hinzufügen.
ms.author: jimwalk
ms.date: 07/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2c2f42235e6a74747059723841d3082037b558c7
ms.sourcegitcommit: 9f8010fe67bb3372db1840de9f0be36097ed6258
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7128840"
---
# <a name="shadows-in-windows-ui"></a><span data-ttu-id="79be2-104">Schatten in Windows-UI</span><span class="sxs-lookup"><span data-stu-id="79be2-104">Shadows in Windows UI</span></span>

<span data-ttu-id="79be2-105">Die [DropShadow](/uwp/api/Windows.UI.Composition.DropShadow) -Klasse stellt Mittel zum Erstellen eines konfigurierbaren Schattens, der auf ein [SpriteVisual](/uwp/api/windows.ui.composition.spritevisual) oder [LayerVisual](/uwp/api/windows.ui.composition.layervisual) (Teilstruktur von visuellen Elementen) angewendet werden können.</span><span class="sxs-lookup"><span data-stu-id="79be2-105">The [DropShadow](/uwp/api/Windows.UI.Composition.DropShadow) class provides means of creating a configurable shadow that can be applied to a [SpriteVisual](/uwp/api/windows.ui.composition.spritevisual) or [LayerVisual](/uwp/api/windows.ui.composition.layervisual) (subtree of Visuals).</span></span> <span data-ttu-id="79be2-106">Wie üblich für Objekte in der visuellen Ebene ist, können alle Eigenschaften des der DropShadow mit CompositionAnimations animiert werden.</span><span class="sxs-lookup"><span data-stu-id="79be2-106">As is customary for objects in the Visual Layer, all properties of the DropShadow can be animated using CompositionAnimations.</span></span>

## <a name="basic-drop-shadow"></a><span data-ttu-id="79be2-107">Grundlegende Schlagschatten</span><span class="sxs-lookup"><span data-stu-id="79be2-107">Basic drop shadow</span></span>

<span data-ttu-id="79be2-108">Um eine einfache Schatten zu erstellen, erstellen Sie eine neue DropShadow und Ihre Visual zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="79be2-108">To create a basic shadow, simply create a new DropShadow and associate it to your visual.</span></span> <span data-ttu-id="79be2-109">Der Schatten sind standardmäßig rechteckig.</span><span class="sxs-lookup"><span data-stu-id="79be2-109">The shadow is rectangular by default.</span></span> <span data-ttu-id="79be2-110">Eine Reihe von Eigenschaften sind für das Erscheinungsbild des Schattens Optimierungseigenschaften verfügbar.</span><span class="sxs-lookup"><span data-stu-id="79be2-110">A standard set of properties are available to tweak the look and feel of your shadow.</span></span>

```cs
var basicRectVisual = _compositor.CreateSpriteVisual();
basicRectVisual.Brush = _compositor.CreateColorBrush(Colors.Blue);
basicRectVisual.Offset = new Vector3(100, 100, 20);
basicRectVisual.Size = new Vector2(300, 300);

var basicShadow = _compositor.CreateDropShadow();
basicShadow.BlurRadius = 25f;
basicShadow.Offset = new Vector3(20, 20, 20);

basicRectVisual.Shadow = basicShadow;
```

![Rechteckige visuelles Element mit grundlegenden DropShadow](images/rectangular-dropshadow.png)

## <a name="shaping-the-shadow"></a><span data-ttu-id="79be2-112">Gestaltung des Schattens</span><span class="sxs-lookup"><span data-stu-id="79be2-112">Shaping the shadow</span></span>

<span data-ttu-id="79be2-113">Es gibt verschiedene Möglichkeiten, die Form für Ihre DropShadow definieren:</span><span class="sxs-lookup"><span data-stu-id="79be2-113">There are a few ways to define the shape for your DropShadow:</span></span>

- <span data-ttu-id="79be2-114">**Verwenden Sie den vorgegebenen** - wird standardmäßig die DropShadow Form durch den Modus "Default" CompositionDropShadowSourcePolicy definiert.</span><span class="sxs-lookup"><span data-stu-id="79be2-114">**Use the default** - By default the DropShadow shape is defined by the ‘Default’ mode on CompositionDropShadowSourcePolicy.</span></span> <span data-ttu-id="79be2-115">Für SpriteVisual wird standardmäßig rechteckig, es sei denn, eine Maske bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="79be2-115">For SpriteVisual, the Default is Rectangular unless a mask is provided.</span></span> <span data-ttu-id="79be2-116">Für LayerVisual wird standardmäßig eine Maske mit dem Alphawert von den visuellen Pinsel erben.</span><span class="sxs-lookup"><span data-stu-id="79be2-116">For LayerVisual, Default is to inherit a mask using the alpha of the visual’s brush.</span></span>
- <span data-ttu-id="79be2-117">**Eine Maske festlegen** – Sie können die [Maske](/uwp/api/windows.ui.composition.dropshadow.mask) -Eigenschaft zum Definieren einer Deckkraftmaske für den Schatten festlegen.</span><span class="sxs-lookup"><span data-stu-id="79be2-117">**Set a mask** – You may set the [Mask](/uwp/api/windows.ui.composition.dropshadow.mask) property to define an opacity mask for the shadow.</span></span>
- <span data-ttu-id="79be2-118">**Geben Sie mit dem vererbt Maske** – legen Sie die [SourcePolicy](/uwp/api/windows.ui.composition.dropshadow.sourcepolicy) -Eigenschaft [CompositionDropShadowSourcePolicy](/uwp/api/windows.ui.composition.compositiondropshadowsourcepolicy)verwenden.</span><span class="sxs-lookup"><span data-stu-id="79be2-118">**Specify to use Inherited mask** – Set the [SourcePolicy](/uwp/api/windows.ui.composition.dropshadow.sourcepolicy) property to use [CompositionDropShadowSourcePolicy](/uwp/api/windows.ui.composition.compositiondropshadowsourcepolicy).</span></span> <span data-ttu-id="79be2-119">InheritFromVisualContent verwenden Sie die Maske aus dem Alpha-Wert von den visuellen Pinsel generiert.</span><span class="sxs-lookup"><span data-stu-id="79be2-119">InheritFromVisualContent to use the mask generated from the alpha of the visual’s brush.</span></span>

## <a name="masking-to-match-your-content"></a><span data-ttu-id="79be2-120">Um Ihre Inhalte zu vergleichen Maskierung</span><span class="sxs-lookup"><span data-stu-id="79be2-120">Masking to match your content</span></span>

<span data-ttu-id="79be2-121">Wenn Sie möchten Ihre Schatten entsprechen den visuellen Inhalt des visuellen Pinsel für Ihre Shadow Mask-Eigenschaft verwenden, können oder festlegen den Schatten Maske automatisch vom Inhalt erben.</span><span class="sxs-lookup"><span data-stu-id="79be2-121">If you want your shadow to match the Visual’s content you can either use the Visual’s brush for your Shadow mask property, or set the shadow to automatically inherit mask from the content.</span></span> <span data-ttu-id="79be2-122">Wenn Sie eine LayerVisual verwenden, wird der Schatten die Maske standardmäßig erben.</span><span class="sxs-lookup"><span data-stu-id="79be2-122">If using a LayerVisual, the shadow will inherit the mask by default.</span></span>

```cs
var imageSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/myImage.png"));
var imageBrush = _compositor.CreateSurfaceBrush(imageSurface);

var imageSpriteVisual = _compositor.CreateSpriteVisual();
imageSpriteVisual.Size = new Vector2(400,400);
imageSpriteVisual.Offset = new Vector3(100, 500, 20);
imageSpriteVisual.Brush = imageBrush;

var shadow = _compositor.CreateDropShadow();
shadow.Mask = imageBrush;
// or use shadow.SourcePolicy = CompositionDropShadowSourcePolicy.InheritFromVisualContent;
shadow.BlurRadius = 25f;
shadow.Offset = new Vector3(20, 20, 20);

imageSpriteVisual.Shadow = shadow;
```

![Verbundenen Webbild mit maskierten Schlagschatten](images/ms-brand-web-dropshadow.png)

## <a name="using-an-alternative-mask"></a><span data-ttu-id="79be2-124">Verwenden eine alternative Maske</span><span class="sxs-lookup"><span data-stu-id="79be2-124">Using an alternative mask</span></span>

<span data-ttu-id="79be2-125">In einigen Fällen möchten möglicherweise den Schatten Form, sodass keine des visuellen Inhalt Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="79be2-125">In some cases, you may want to shape the shadow such that it doesn’t match your Visual’s content.</span></span> <span data-ttu-id="79be2-126">Um diesen Effekt zu erzielen, müssen Sie explizit die Maske Eigenschaft Alpha mit einem Pinsel festgelegt.</span><span class="sxs-lookup"><span data-stu-id="79be2-126">To achieve this effect, you’ll need to explicitly set the Mask property using a brush with alpha.</span></span>

<span data-ttu-id="79be2-127">In dem Beispiel unten haben wir zwei Oberflächen - eine für den visuellen Inhalt und eine für den Volumeschattenkopie-Maske laden:</span><span class="sxs-lookup"><span data-stu-id="79be2-127">In the below example, we load two surfaces - one for the Visual content and one for the Shadow mask:</span></span>

```cs
var imageSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/myImage.png"));
var imageBrush = _compositor.CreateSurfaceBrush(imageSurface);

var circleSurface = LoadedImageSurface.StartLoadFromUri(new Uri("ms-appx:///Assets/myCircleImage.png"));
var customMask = _compositor.CreateSurfaceBrush(circleSurface);

var imageSpriteVisual = _compositor.CreateSpriteVisual();
imageSpriteVisual.Size = new Vector2(400,400);
imageSpriteVisual.Offset = new Vector3(100, 500, 20);
imageSpriteVisual.Brush = imageBrush;

var shadow = _compositor.CreateDropShadow();
shadow.Mask = customMask;
shadow.BlurRadius = 25f;
shadow.Offset = new Vector3(20, 20, 20);

imageSpriteVisual.Shadow = shadow;
```

![Verbundene Webbild mit Kreis maskiert Schlagschatten](images/ms-brand-web-masked-dropshadow.png)

## <a name="animating"></a><span data-ttu-id="79be2-129">Animieren</span><span class="sxs-lookup"><span data-stu-id="79be2-129">Animating</span></span>

<span data-ttu-id="79be2-130">Als standard in der visuellen Ebene ist, können mit Kompositionsanimationen DropShadow Eigenschaften animiert werden.</span><span class="sxs-lookup"><span data-stu-id="79be2-130">As is standard in the Visual Layer, DropShadow properties can be animated using Composition Animations.</span></span> <span data-ttu-id="79be2-131">Unten ändern wir den Code aus dem wenig Präsentationslogik Beispiel oben aus, um den Weichzeichnerradius für den Schatten zu animieren.</span><span class="sxs-lookup"><span data-stu-id="79be2-131">Below, we modify the code from the sprinkles sample above to animate the blur radius for the shadow.</span></span>

```cs
ScalarKeyFrameAnimation blurAnimation = _compositor.CreateScalarKeyFrameAnimation();
blurAnimation.InsertKeyFrame(0.0f, 25.0f);
blurAnimation.InsertKeyFrame(0.7f, 50.0f);
blurAnimation.InsertKeyFrame(1.0f, 25.0f);
blurAnimation.Duration = TimeSpan.FromSeconds(4);
blurAnimation.IterationBehavior = AnimationIterationBehavior.Forever;
shadow.StartAnimation("BlurRadius", blurAnimation);
```

## <a name="shadows-in-xaml"></a><span data-ttu-id="79be2-132">Schatten in XAML</span><span class="sxs-lookup"><span data-stu-id="79be2-132">Shadows in XAML</span></span>

<span data-ttu-id="79be2-133">Wenn Sie einen Schatten komplexere Frameworkelemente hinzufügen möchten, gibt es verschiedene Möglichkeiten, um Interoperabilität mit Schatten zwischen XAML und Komposition:</span><span class="sxs-lookup"><span data-stu-id="79be2-133">If you want to add a shadow to more complex framework elements, there are a couple ways to interop with shadows between XAML and Composition:</span></span>

1. <span data-ttu-id="79be2-134">Verwenden Sie die [DropShadowPanel](https://github.com/Microsoft/UWPCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/DropShadowPanel/DropShadowPanel.Properties.cs) in der Windows-Community-Toolkit verfügbar.</span><span class="sxs-lookup"><span data-stu-id="79be2-134">Use the [DropShadowPanel](https://github.com/Microsoft/UWPCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/DropShadowPanel/DropShadowPanel.Properties.cs) available in the Windows Community Toolkit.</span></span> <span data-ttu-id="79be2-135">Einzelheiten finden Sie die [Dokumentation DropShadowPanel](https://docs.microsoft.com/windows/uwpcommunitytoolkit/controls/DropShadowPanel) auf Ihre Verwendung.</span><span class="sxs-lookup"><span data-stu-id="79be2-135">See the [DropShadowPanel documentation](https://docs.microsoft.com/windows/uwpcommunitytoolkit/controls/DropShadowPanel) for details on how to use it.</span></span>
1. <span data-ttu-id="79be2-136">Erstellen Sie eine visuelle um & verknüpfen es auf die XAML-Handout Visuals als Host Schatten verwenden.</span><span class="sxs-lookup"><span data-stu-id="79be2-136">Create a Visual to use as the shadow host & tie it to the XAML handout Visual.</span></span>
1. <span data-ttu-id="79be2-137">Verwenden der Komposition-Beispielgalerie [SamplesCommon](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SamplesCommon/SamplesCommon) benutzerdefinierten CompositionShadow-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="79be2-137">Use the Composition Sample Gallery’s [SamplesCommon](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SamplesCommon/SamplesCommon) custom CompositionShadow control.</span></span> <span data-ttu-id="79be2-138">Siehe Beispiel für die Verwendung.</span><span class="sxs-lookup"><span data-stu-id="79be2-138">See the example here for usage.</span></span>

## <a name="performance"></a><span data-ttu-id="79be2-139">Leistung</span><span class="sxs-lookup"><span data-stu-id="79be2-139">Performance</span></span>

<span data-ttu-id="79be2-140">Obwohl sich die visuelle Ebene viele Optimierungen eingeführt, um Effekte effiziente und nutzbar zu machen, möglich generieren Schatten eine relativ aufwendig je nachdem, welche Optionen, die Sie festlegen.</span><span class="sxs-lookup"><span data-stu-id="79be2-140">Although the Visual Layer has many optimizations in place to make effects efficient and usable, generating shadows can be a relatively expensive operation depending on what options you set.</span></span> <span data-ttu-id="79be2-141">Im folgenden sind high Level "Kosten" für verschiedene Arten von Schatten.</span><span class="sxs-lookup"><span data-stu-id="79be2-141">Below are high level 'costs' for different types of shadows.</span></span> <span data-ttu-id="79be2-142">Beachten Sie, dass zwar möglicherweise bestimmte Schatten teuer sie weiterhin können werden in bestimmten Szenarien sparsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="79be2-142">Note that although certain shadows may be expensive they may still be appropriate to use sparingly in certain scenarios.</span></span>

<span data-ttu-id="79be2-143">Schatten Merkmale</span><span class="sxs-lookup"><span data-stu-id="79be2-143">Shadow Characteristics</span></span>| <span data-ttu-id="79be2-144">Kosten</span><span class="sxs-lookup"><span data-stu-id="79be2-144">Cost</span></span>
------------- | -------------
<span data-ttu-id="79be2-145">„Rechteckiges Ausschneiden“</span><span class="sxs-lookup"><span data-stu-id="79be2-145">Rectangular</span></span>    | <span data-ttu-id="79be2-146">Niedrig</span><span class="sxs-lookup"><span data-stu-id="79be2-146">Low</span></span>
<span data-ttu-id="79be2-147">Shadow.Mask</span><span class="sxs-lookup"><span data-stu-id="79be2-147">Shadow.Mask</span></span>      | <span data-ttu-id="79be2-148">Hoch </span><span class="sxs-lookup"><span data-stu-id="79be2-148">High</span></span>
<span data-ttu-id="79be2-149">CompositionDropShadowSourcePolicy.InheritFromVisualContent</span><span class="sxs-lookup"><span data-stu-id="79be2-149">CompositionDropShadowSourcePolicy.InheritFromVisualContent</span></span> | <span data-ttu-id="79be2-150">Hoch </span><span class="sxs-lookup"><span data-stu-id="79be2-150">High</span></span>
<span data-ttu-id="79be2-151">Statische Weichzeichnerradius</span><span class="sxs-lookup"><span data-stu-id="79be2-151">Static Blur Radius</span></span> | <span data-ttu-id="79be2-152">Niedrig</span><span class="sxs-lookup"><span data-stu-id="79be2-152">Low</span></span>
<span data-ttu-id="79be2-153">Animieren von Weichzeichnerradius</span><span class="sxs-lookup"><span data-stu-id="79be2-153">Animating Blur Radius</span></span> | <span data-ttu-id="79be2-154">Hoch </span><span class="sxs-lookup"><span data-stu-id="79be2-154">High</span></span>

## <a name="additional-resources"></a><span data-ttu-id="79be2-155">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="79be2-155">Additional Resources</span></span>

- [<span data-ttu-id="79be2-156">Komposition DropShadow API</span><span class="sxs-lookup"><span data-stu-id="79be2-156">Composition DropShadow API</span></span>](/uwp/api/Windows.UI.Composition.DropShadow)
- [<span data-ttu-id="79be2-157">WindowsUIDevLabs-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="79be2-157">WindowsUIDevLabs GitHub Repo</span></span>](https://github.com/Microsoft/WindowsUIDevLabs)