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
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7157625"
---
# <a name="shadows-in-windows-ui"></a>Schatten in Windows-UI

Die [DropShadow](/uwp/api/Windows.UI.Composition.DropShadow) -Klasse stellt Mittel zum Erstellen eines konfigurierbaren Schattens, der auf ein [SpriteVisual](/uwp/api/windows.ui.composition.spritevisual) oder [LayerVisual](/uwp/api/windows.ui.composition.layervisual) (Teilstruktur von visuellen Elementen) angewendet werden können. Wie üblich für Objekte in der visuellen Ebene ist, können alle Eigenschaften des der DropShadow mit CompositionAnimations animiert werden.

## <a name="basic-drop-shadow"></a>Grundlegende Schlagschatten

Um eine einfache Schatten zu erstellen, erstellen Sie eine neue DropShadow und Ihre Visual zuzuordnen. Der Schatten sind standardmäßig rechteckig. Eine Reihe von Eigenschaften sind für das Erscheinungsbild des Schattens Optimierungseigenschaften verfügbar.

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

## <a name="shaping-the-shadow"></a>Gestaltung des Schattens

Es gibt verschiedene Möglichkeiten, die Form für Ihre DropShadow definieren:

- **Verwenden Sie den vorgegebenen** - wird standardmäßig die DropShadow Form durch den Modus "Default" CompositionDropShadowSourcePolicy definiert. Für SpriteVisual wird standardmäßig rechteckig, es sei denn, eine Maske bereitgestellt wird. Für LayerVisual wird standardmäßig eine Maske mit dem Alphawert von den visuellen Pinsel erben.
- **Eine Maske festlegen** – Sie können die [Maske](/uwp/api/windows.ui.composition.dropshadow.mask) -Eigenschaft zum Definieren einer Deckkraftmaske für den Schatten festlegen.
- **Geben Sie mit dem vererbt Maske** – legen Sie die [SourcePolicy](/uwp/api/windows.ui.composition.dropshadow.sourcepolicy) -Eigenschaft [CompositionDropShadowSourcePolicy](/uwp/api/windows.ui.composition.compositiondropshadowsourcepolicy)verwenden. InheritFromVisualContent verwenden Sie die Maske aus dem Alpha-Wert von den visuellen Pinsel generiert.

## <a name="masking-to-match-your-content"></a>Um Ihre Inhalte zu vergleichen Maskierung

Wenn Sie möchten Ihre Schatten entsprechen den visuellen Inhalt des visuellen Pinsel für Ihre Shadow Mask-Eigenschaft verwenden, können oder festlegen den Schatten Maske automatisch vom Inhalt erben. Wenn Sie eine LayerVisual verwenden, wird der Schatten die Maske standardmäßig erben.

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

## <a name="using-an-alternative-mask"></a>Verwenden eine alternative Maske

In einigen Fällen möchten möglicherweise den Schatten Form, sodass keine des visuellen Inhalt Übereinstimmung. Um diesen Effekt zu erzielen, müssen Sie explizit die Maske Eigenschaft Alpha mit einem Pinsel festgelegt.

In dem Beispiel unten haben wir zwei Oberflächen - eine für den visuellen Inhalt und eine für den Volumeschattenkopie-Maske laden:

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

## <a name="animating"></a>Animieren

Als standard in der visuellen Ebene ist, können mit Kompositionsanimationen DropShadow Eigenschaften animiert werden. Unten ändern wir den Code aus dem wenig Präsentationslogik Beispiel oben aus, um den Weichzeichnerradius für den Schatten zu animieren.

```cs
ScalarKeyFrameAnimation blurAnimation = _compositor.CreateScalarKeyFrameAnimation();
blurAnimation.InsertKeyFrame(0.0f, 25.0f);
blurAnimation.InsertKeyFrame(0.7f, 50.0f);
blurAnimation.InsertKeyFrame(1.0f, 25.0f);
blurAnimation.Duration = TimeSpan.FromSeconds(4);
blurAnimation.IterationBehavior = AnimationIterationBehavior.Forever;
shadow.StartAnimation("BlurRadius", blurAnimation);
```

## <a name="shadows-in-xaml"></a>Schatten in XAML

Wenn Sie einen Schatten komplexere Frameworkelemente hinzufügen möchten, gibt es verschiedene Möglichkeiten, um Interoperabilität mit Schatten zwischen XAML und Komposition:

1. Verwenden Sie die [DropShadowPanel](https://github.com/Microsoft/UWPCommunityToolkit/blob/master/Microsoft.Toolkit.Uwp.UI.Controls/DropShadowPanel/DropShadowPanel.Properties.cs) in der Windows-Community-Toolkit verfügbar. Einzelheiten finden Sie die [Dokumentation DropShadowPanel](https://docs.microsoft.com/windows/uwpcommunitytoolkit/controls/DropShadowPanel) auf Ihre Verwendung.
1. Erstellen Sie eine visuelle um & verknüpfen es auf die XAML-Handout Visuals als Host Schatten verwenden.
1. Verwenden der Komposition-Beispielgalerie [SamplesCommon](https://github.com/Microsoft/WindowsUIDevLabs/tree/master/SamplesCommon/SamplesCommon) benutzerdefinierten CompositionShadow-Steuerelements. Siehe Beispiel für die Verwendung.

## <a name="performance"></a>Leistung

Obwohl sich die visuelle Ebene viele Optimierungen eingeführt, um Effekte effiziente und nutzbar zu machen, möglich generieren Schatten eine relativ aufwendig je nachdem, welche Optionen, die Sie festlegen. Im folgenden sind high Level "Kosten" für verschiedene Arten von Schatten. Beachten Sie, dass zwar möglicherweise bestimmte Schatten teuer sie weiterhin können werden in bestimmten Szenarien sparsam verwendet.

Schatten Merkmale| Kosten
------------- | -------------
„Rechteckiges Ausschneiden“    | Niedrig
Shadow.Mask      | Hoch 
CompositionDropShadowSourcePolicy.InheritFromVisualContent | Hoch 
Statische Weichzeichnerradius | Niedrig
Animieren von Weichzeichnerradius | Hoch 

## <a name="additional-resources"></a>Weitere Ressourcen

- [Komposition DropShadow API](/uwp/api/Windows.UI.Composition.DropShadow)
- [WindowsUIDevLabs-GitHub-Repository](https://github.com/Microsoft/WindowsUIDevLabs)