---
author: daneuber
title: Komposition Schatten
description: Der Schatten APIs können Sie dynamische anpassbare Schatten UI-Inhalte hinzufügen.
ms.author: jimwalk
ms.date: 07/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 84e12d6c3e25a18902aaa55011949dd5b5ff97ca
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3822984"
---
# <a name="shadows-in-windows-ui"></a><span data-ttu-id="682e5-104">Schatten in Windows-UI</span><span class="sxs-lookup"><span data-stu-id="682e5-104">Shadows in Windows UI</span></span>

<span data-ttu-id="682e5-105">Die [DropShadow](/uwp/api/Windows.UI.Composition.DropShadow) -Klasse stellt Mittel zum Erstellen eines konfigurierbaren Schattens, der auf ein [SpriteVisual](/uwp/api/windows.ui.composition.spritevisual) oder [LayerVisual](/uwp/api/windows.ui.composition.layervisual) (Teilstruktur von visuellen Elementen) angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="682e5-105">The [DropShadow](/uwp/api/Windows.UI.Composition.DropShadow) class provides means of creating a configurable shadow that can be applied to a [SpriteVisual](/uwp/api/windows.ui.composition.spritevisual) or [LayerVisual](/uwp/api/windows.ui.composition.layervisual) (subtree of Visuals).</span></span> <span data-ttu-id="682e5-106">Wie üblich für Objekte in der visuellen Ebene ist, können alle Eigenschaften des der DropShadow mit CompositionAnimations animiert werden.</span><span class="sxs-lookup"><span data-stu-id="682e5-106">As is customary for objects in the Visual Layer, all properties of the DropShadow can be animated using CompositionAnimations.</span></span>

## <a name="basic-drop-shadow"></a><span data-ttu-id="682e5-107">Grundlegende Schlagschatten</span><span class="sxs-lookup"><span data-stu-id="682e5-107">Basic drop shadow</span></span>

<span data-ttu-id="682e5-108">Um eine grundlegende Schatten zu erstellen, erstellen Sie eine neue DropShadow und Ihre Visual zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="682e5-108">To create a basic shadow, simply create a new DropShadow and associate it to your visual.</span></span> <span data-ttu-id="682e5-109">Der Schatten sind standardmäßig rechteckig.</span><span class="sxs-lookup"><span data-stu-id="682e5-109">The shadow is rectangular by default.</span></span> <span data-ttu-id="682e5-110">Eine Reihe von Eigenschaften sind für das Aussehen und Verhalten von des Schattens Optimierungseigenschaften verfügbar.</span><span class="sxs-lookup"><span data-stu-id="682e5-110">A standard set of properties are available to tweak the look and feel of your shadow.</span></span>

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

## <a name="shaping-the-shadow"></a><span data-ttu-id="682e5-112">Gestaltung des Schattens</span><span class="sxs-lookup"><span data-stu-id="682e5-112">Shaping the shadow</span></span>

<span data-ttu-id="682e5-113">Es gibt verschiedene Möglichkeiten, die Form für Ihre DropShadow definieren:</span><span class="sxs-lookup"><span data-stu-id="682e5-113">There are a few ways to define the shape for your DropShadow:</span></span>

- <span data-ttu-id="682e5-114">**Verwenden Sie den vorgegebenen** - wird standardmäßig die DropShadow Form durch den Modus "Default" CompositionDropShadowSourcePolicy definiert.</span><span class="sxs-lookup"><span data-stu-id="682e5-114">**Use the default** - By default the DropShadow shape is defined by the ‘Default’ mode on CompositionDropShadowSourcePolicy.</span></span> <span data-ttu-id="682e5-115">Für SpriteVisual wird standardmäßig rechteckig, es sei denn, eine Maske bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="682e5-115">For SpriteVisual, the Default is Rectangular unless a mask is provided.</span></span> <span data-ttu-id="682e5-116">Für LayerVisual wird standardmäßig eine Maske mit dem Alphawert von des visuellen Pinsel erben.</span><span class="sxs-lookup"><span data-stu-id="682e5-116">For LayerVisual, Default is to inherit a mask using the alpha of the visual’s brush.</span></span>
- <span data-ttu-id="682e5-117">**Legen Sie eine Maske** – Sie können die [Maske](/uwp/api/windows.ui.composition.dropshadow.mask) Eigenschaft zum Definieren einer Deckkraftmaske für den Schatten festlegen.</span><span class="sxs-lookup"><span data-stu-id="682e5-117">**Set a mask** – You may set the [Mask](/uwp/api/windows.ui.composition.dropshadow.mask) property to define an opacity mask for the shadow.</span></span>
- <span data-ttu-id="682e5-118">**Geben Sie mit dem vererbt Maske** – legen Sie die [SourcePolicy](/uwp/api/windows.ui.composition.dropshadow.sourcepolicy) -Eigenschaft [CompositionDropShadowSourcePolicy](/uwp/api/windows.ui.composition.compositiondropshadowsourcepolicy)verwenden.</span><span class="sxs-lookup"><span data-stu-id="682e5-118">**Specify to use Inherited mask** – Set the [SourcePolicy](/uwp/api/windows.ui.composition.dropshadow.sourcepolicy) property to use [CompositionDropShadowSourcePolicy](/uwp/api/windows.ui.composition.compositiondropshadowsourcepolicy).</span></span> <span data-ttu-id="682e5-119">InheritFromVisualContent, verwenden Sie die Maske aus dem Alpha-Wert von der Visual-Pinsel generiert.</span><span class="sxs-lookup"><span data-stu-id="682e5-119">InheritFromVisualContent to use the mask generated from the alpha of the visual’s brush.</span></span>

## <a name="masking-to-match-your-content"></a><span data-ttu-id="682e5-120">Maskierung entsprechend Ihren Inhalt</span><span class="sxs-lookup"><span data-stu-id="682e5-120">Masking to match your content</span></span>

<span data-ttu-id="682e5-121">Wenn Sie möchten Ihre Schatten entsprechend des visuellen Inhalt des visuellen Pinsel für Ihre Schatten Maske-Eigenschaft verwenden, können oder festlegen den Schatten Maske vom Inhalt automatisch erben.</span><span class="sxs-lookup"><span data-stu-id="682e5-121">If you want your shadow to match the Visual’s content you can either use the Visual’s brush for your Shadow mask property, or set the shadow to automatically inherit mask from the content.</span></span> <span data-ttu-id="682e5-122">Wenn Sie eine LayerVisual verwenden zu können, wird der Schatten die Maske standardmäßig erben.</span><span class="sxs-lookup"><span data-stu-id="682e5-122">If using a LayerVisual, the shadow will inherit the mask by default.</span></span>

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

## <a name="using-an-alternative-mask"></a><span data-ttu-id="682e5-124">Verwenden eine alternative Maske</span><span class="sxs-lookup"><span data-stu-id="682e5-124">Using an alternative mask</span></span>

<span data-ttu-id="682e5-125">In einigen Fällen möchten möglicherweise den Schatten Form, sodass keine des visuellen Inhalt Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="682e5-125">In some cases, you may want to shape the shadow such that it doesn’t match your Visual’s content.</span></span> <span data-ttu-id="682e5-126">Um diesen Effekt zu erzielen, müssen Sie die Maske-Eigenschaft Alpha mit einem Pinsel explizit festlegen.</span><span class="sxs-lookup"><span data-stu-id="682e5-126">To achieve this effect, you’ll need to explicitly set the Mask property using a brush with alpha.</span></span>

<span data-ttu-id="682e5-127">In dem Beispiel unten haben wir zwei Oberflächen - eine für den visuellen Inhalt und eine für die Schatten Maske laden:</span><span class="sxs-lookup"><span data-stu-id="682e5-127">In the below example, we load two surfaces - one for the Visual content and one for the Shadow mask:</span></span>

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

## <a name="animating"></a><span data-ttu-id="682e5-129">Animieren</span><span class="sxs-lookup"><span data-stu-id="682e5-129">Animating</span></span>

<span data-ttu-id="682e5-130">Als standard in der visuellen Ebene ist, können mit Kompositionsanimationen DropShadow Eigenschaften animiert werden.</span><span class="sxs-lookup"><span data-stu-id="682e5-130">As is standard in the Visual Layer, DropShadow properties can be animated using Composition Animations.</span></span> <span data-ttu-id="682e5-131">Unten ändern wir den Code aus wenig Präsentationslogik obigem Beispiel ergibt sich für den Weichzeichnerradius für den Schatten zu animieren.</span><span class="sxs-lookup"><span data-stu-id="682e5-131">Below, we modify the code from the sprinkles sample above to animate the blur radius for the shadow.</span></span>

```cs
ScalarKeyFrameAnimation blurAnimation = _compositor.CreateScalarKeyFrameAnimation();
blurAnimation.InsertKeyFrame(0.0f, 25.0f);
blurAnimation.InsertKeyFrame(0.7f, 50.0f);
blurAnimation.InsertKeyFrame(1.0f, 25.0f);
blurAnimation.Duration = TimeSpan.FromSeconds(4);
blurAnimation.IterationBehavior = AnimationIterationBehavior.Forever;
shadow.StartAnimation("BlurRadius", blurAnimation);
```

## <a name="shadows-in-xaml"></a><span data-ttu-id="682e5-132">Schatten in XAML</span><span class="sxs-lookup"><span data-stu-id="682e5-132">Shadows in XAML</span></span>

<span data-ttu-id="682e5-133">Wenn Sie einen Schatten komplexere Frameworkelemente hinzufügen möchten, gibt es verschiedene Möglichkeiten, um Interoperabilität mit Schatten zwischen XAML und Komposition:</span><span class="sxs-lookup"><span data-stu-id="682e5-133">If you want to add a shadow to more complex framework elements, there are a couple ways to interop with shadows between XAML and Composition:</span></span>

1. <span data-ttu-id="682e5-134">Verwenden Sie die [DropShadowPanel](https://github.com/Microsoft/UWPCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/DropShadowPanel/DropShadowPanel.Properties.cs) im Windows Community Toolkit verfügbar.</span><span class="sxs-lookup"><span data-stu-id="682e5-134">Use the [DropShadowPanel](https://github.com/Microsoft/UWPCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/DropShadowPanel/DropShadowPanel.Properties.cs) available in the Windows Community Toolkit.</span></span> <span data-ttu-id="682e5-135">Einzelheiten finden Sie die [DropShadowPanel Dokumentation](https://docs.microsoft.com/windows/uwpcommunitytoolkit/controls/DropShadowPanel) zur Verwendung von es.</span><span class="sxs-lookup"><span data-stu-id="682e5-135">See the [DropShadowPanel documentation](https://docs.microsoft.com/windows/uwpcommunitytoolkit/controls/DropShadowPanel) for details on how to use it.</span></span>
1. <span data-ttu-id="682e5-136">Erstellen eines visuellen Elements als Schatten Host verwenden, und verknüpfen es auf die XAML-Handout Visuals an.</span><span class="sxs-lookup"><span data-stu-id="682e5-136">Create a Visual to use as the shadow host & tie it to the XAML handout Visual.</span></span>
1. <span data-ttu-id="682e5-137">Verwenden Sie die Komposition-Beispielgalerie [SamplesCommon](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SamplesCommon/SamplesCommon) benutzerdefinierte CompositionShadow Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="682e5-137">Use the Composition Sample Gallery’s [SamplesCommon](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SamplesCommon/SamplesCommon) custom CompositionShadow control.</span></span> <span data-ttu-id="682e5-138">Beispiel für die Verwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="682e5-138">See the example here for usage.</span></span>

## <a name="performance"></a><span data-ttu-id="682e5-139">Leistung</span><span class="sxs-lookup"><span data-stu-id="682e5-139">Performance</span></span>

<span data-ttu-id="682e5-140">Obwohl sich die visuelle Ebene viele Optimierungen Designfeatures zum Effekte effiziente und nutzbar zu machen, möglich generieren Schatten relativ aufwendig je nachdem, welche Optionen, die Sie festlegen.</span><span class="sxs-lookup"><span data-stu-id="682e5-140">Although the Visual Layer has many optimizations in place to make effects efficient and usable, generating shadows can be a relatively expensive operation depending on what options you set.</span></span> <span data-ttu-id="682e5-141">Im folgenden sind high Level "Kosten" für verschiedene Arten von Schatten.</span><span class="sxs-lookup"><span data-stu-id="682e5-141">Below are high level 'costs' for different types of shadows.</span></span> <span data-ttu-id="682e5-142">Beachten Sie, dass obwohl bestimmte Schatten teuer möglicherweise sie weiterhin können werden in bestimmten Szenarien sparsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="682e5-142">Note that although certain shadows may be expensive they may still be appropriate to use sparingly in certain scenarios.</span></span>

<span data-ttu-id="682e5-143">Schatten Merkmale</span><span class="sxs-lookup"><span data-stu-id="682e5-143">Shadow Characteristics</span></span>| <span data-ttu-id="682e5-144">Kosten</span><span class="sxs-lookup"><span data-stu-id="682e5-144">Cost</span></span>
------------- | -------------
<span data-ttu-id="682e5-145">„Rechteckiges Ausschneiden“</span><span class="sxs-lookup"><span data-stu-id="682e5-145">Rectangular</span></span>    | <span data-ttu-id="682e5-146">Niedrig</span><span class="sxs-lookup"><span data-stu-id="682e5-146">Low</span></span>
<span data-ttu-id="682e5-147">Shadow.Mask</span><span class="sxs-lookup"><span data-stu-id="682e5-147">Shadow.Mask</span></span>      | <span data-ttu-id="682e5-148">Hoch </span><span class="sxs-lookup"><span data-stu-id="682e5-148">High</span></span>
<span data-ttu-id="682e5-149">CompositionDropShadowSourcePolicy.InheritFromVisualContent</span><span class="sxs-lookup"><span data-stu-id="682e5-149">CompositionDropShadowSourcePolicy.InheritFromVisualContent</span></span> | <span data-ttu-id="682e5-150">Hoch </span><span class="sxs-lookup"><span data-stu-id="682e5-150">High</span></span>
<span data-ttu-id="682e5-151">Statische Weichzeichnerradius</span><span class="sxs-lookup"><span data-stu-id="682e5-151">Static Blur Radius</span></span> | <span data-ttu-id="682e5-152">Niedrig</span><span class="sxs-lookup"><span data-stu-id="682e5-152">Low</span></span>
<span data-ttu-id="682e5-153">Animieren von Weichzeichnerradius</span><span class="sxs-lookup"><span data-stu-id="682e5-153">Animating Blur Radius</span></span> | <span data-ttu-id="682e5-154">Hoch </span><span class="sxs-lookup"><span data-stu-id="682e5-154">High</span></span>

## <a name="additional-resources"></a><span data-ttu-id="682e5-155">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="682e5-155">Additional Resources</span></span>

- [<span data-ttu-id="682e5-156">Komposition DropShadow API</span><span class="sxs-lookup"><span data-stu-id="682e5-156">Composition DropShadow API</span></span>](/uwp/api/Windows.UI.Composition.DropShadow)
- [<span data-ttu-id="682e5-157">WindowsUIDevLabs-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="682e5-157">WindowsUIDevLabs GitHub Repo</span></span>](https://github.com/Microsoft/WindowsUIDevLabs)