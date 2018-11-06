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
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6047086"
---
# <a name="composition-brushes"></a>Kompositionspinsel
Alles, was von einer UWP-Anwendung auf dem Bildschirm sichtbar wird angezeigt, da es mit einem Pinsel gezeichnet wurde. Mithilfe von Pinseln können Sie Benutzer Objekte der Benutzeroberfläche (UI) mit Inhalt, angefangen bei einfachen, einfarbige Farben zu Bildern oder Zeichnungen für komplexe Effekte Kette zeichnen. In diesem Thema werden die Begriffe zum Zeichnen mit CompositionBrush.

Beachten Sie bei der Arbeit mit XAML-UWP-app können Sie sich entschieden, ein UIElement mit einem [XAML-Pinsel](/windows/uwp/design/style/brushes) oder ein [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush)zu zeichnen. In der Regel ist es einfacher und ratsam, einen XAML-Pinsel auswählen, wenn Ihr Szenario von einem XAML-Pinsel unterstützt wird. Animieren z. B. die Farbe einer Schaltfläche, die Füllung ein Text oder eine Form mit einem Bild ändern. Andererseits, wenn Sie versuchen, eine Aktion ausführen, die nicht von einem XAML-Pinsel wie Zeichnen mit eine animierte Maske oder eine animierte neun Raster Stretch oder einer effektkette unterstützt wird, können eine CompositionBrush Sie ein UIElement durch die Verwendung von [Zeichnen XamlCompositionBrushBase](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).

Bei der Arbeit mit der visuellen Ebene muss eine CompositionBrush verwendet werden, um den Bereich einer [SpriteVisual](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.SpriteVisual)zu zeichnen.

-   [Voraussetzungen](./composition-brushes.md#prerequisites)
-   [Zeichnen mit CompositionBrush](./composition-brushes.md#paint-with-a-compositionbrush)
    -   [Zeichnen Sie mit einer Volltonfarbe.](./composition-brushes.md#paint-with-a-solid-color)
    -   [Zeichnen Sie mit einen linearen Farbverlauf](./composition-brushes.md#paint-with-a-linear-gradient)
    -   [Zeichnen Sie mit einem Bild](./composition-brushes.md#paint-with-an-image)
    -   [Zeichnen Sie mit einer benutzerdefinierten Zeichnung](./composition-brushes.md#paint-with-a-custom-drawing)
    -   [Zeichnen Sie mit einem video](./composition-brushes.md#paint-with-a-video)
    -   [Zeichnen Sie mit einem Filtereffekt](./composition-brushes.md#paint-with-a-filter-effect)
    -   [Zeichnen Sie mit einem CompositionBrush mit einer Deckkraftmaske](./composition-brushes.md#paint-with-a-compositionbrush-with-opacity-mask-applied)
    -   [Zeichnen Sie mit einer CompositionBrush mit NineGrid stretch](./composition-brushes.md#paint-with-a-compositionbrush-using-ninegrid-stretch)
    -   [Zeichnen mit Hintergrund Pixel](./composition-brushes.md#paint-using-background-pixels)
-   [Kombinieren von CompositionBrushes](./composition-brushes.md#combining-compositionbrushes)
-   [Verwenden eine XAML-Pinsel im Vergleich zu CompositionBrush](./composition-brushes.md#using-a-xaml-brush-vs-compositionbrush)
-   [Verwandte Themen](./composition-brushes.md#related-topics)

## <a name="prerequisites"></a>Voraussetzungen
In dieser Übersicht wird davon ausgegangen, dass Sie mit der Struktur einer einfachen kompositionsanwendung vertraut sind, wie in der [Übersicht über die visuelle Ebene](visual-layer.md)beschrieben.

## <a name="paint-with-a-compositionbrush"></a>Zeichnen mit einem CompositionBrush

Eine [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush) zeichnet"" einen Bereich mit der zugehörigen Ausgabe. Verschiedene Pinsel haben unterschiedliche Ausgabetypen. Einige Pinsel zeichnen einen Bereich mit einer Volltonfarbe, andere mit einem Farbverlauf, Bild, benutzerdefiniertes Zeichnen oder Effekt. Es gibt auch spezielle Pinsel, die das Verhalten des anderen Pinseln ändern. Z. B. Deckkraftmaske kann verwendet werden, um zu steuern, welche Bereich durch eine CompositionBrush gezeichnet wird, oder ein neun-Raster kann verwendet werden, um steuern, die Stretch auf eine CompositionBrush angewendet wird, wenn Sie einen Bereich zu zeichnen. CompositionBrush kann von einem der folgenden Typen sein:

|Klasse                                   |Details                                         |Eingeführt In|
|-------------------------------------|---------------------------------------------------------|--------------------------------------|
|[CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush)         |Zeichnet einen Bereich mit einer Volltonfarbe.                        |Windows 10 November-Update (SDK 10586)|
|[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush)       |Zeichnet einen Bereich mit den Inhalt einer [ICompositionSurface](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Composition.ICompositionSurface)|Windows 10 November-Update (SDK 10586)|
|[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)        |Zeichnet einen Bereich mit den Inhalten eines kompositionseffekts. |Windows 10 November-Update (SDK 10586)|
|[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)          |Zeichnet ein visuelles Element mit einer CompositionBrush mit einer Deckkraftmaske |Windows 10 Anniversary Update (SDK 14393)
|[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)      |Zeichnet einen Bereich mit einer CompositionBrush mit einem NineGrid stretch |Windows 10 Anniversary Update SDK (14393)
|[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)|Zeichnet einen Bereich mit einem linearen Farbverlauf                    |Windows 10 Fall Creators Update (Insider Preview SDK)
|[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)     |Zeichnet einen Bereich von sampling-Hintergrund Pixel aus der Anwendung oder Pixel direkt hinter das Fenster der Anwendung auf dem Desktop. Als Eingabe für eine andere CompositionBrush wie ein CompositionEffectBrush verwendet | Windows 10 Anniversary Update (SDK 14393)

### <a name="paint-with-a-solid-color"></a>Zeichnen Sie mit einer Volltonfarbe.

Eine [CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush) zeichnet einen Bereich mit einer Volltonfarbe. Es gibt eine Vielzahl von Möglichkeiten, um die Farbe eines SolidColorBrush angeben. Sie können z. B. angeben, seine Kanäle Alpha, Rot, Grün und Blau (ARGB) oder verwenden Sie eine der vordefinierten Farben durch die [Farben](https://docs.microsoft.com/uwp/api/windows.ui.colors) -Klasse bereitgestellt.

Die Abbildung und der Code zeigen im Folgenden eine kleine visuelle Struktur. Es wird ein Rechteck erstellt, dessen Konturen mit einem schwarzen Pinsel gezeichnet sind und das mit einem Pinsel in Volltonfarbe ausgefüllt ist, die den Farbwert „0x9ACD32“ hat.

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

### <a name="paint-with-a-linear-gradient"></a>Zeichnen Sie mit einen linearen Farbverlauf

Eine [CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush) zeichnet einen Bereich mit einem linearen Farbverlauf. Ein linearer Farbverlauf mischt zwei oder mehr Farben entlang einer Linie, der Farbverlaufsachse an. Sie verwenden GradientStop-Objekte, um die Farben in den Farbverlauf und ihre Positionen anzugeben.

Die folgende Abbildung und der Code zeigt ein SpriteVisual mit LinearGradientBrush 2 hindert, die mit einer roten und gelben Farbe gezeichnet.

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

### <a name="paint-with-an-image"></a>Zeichnen Sie mit einem Bild

Eine [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) zeichnet einen Bereich mit Pixeln auf einer ICompositionSurface gerendert. Z. B. kann eine CompositionSurfaceBrush verwendet werden, um einen Bereich mit einem Bild auf einer ICompositionSurface Oberfläche mit [Loadedimagesource](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.loadedimagesurface) API gerendert zu zeichnen.

Die folgende Abbildung und der Code zeigt, mit einer Bitmap einer lakritz gerendert auf eine ICompositionSurface Loadedimagesource mithilfe ein spritevisual-Elements gezeichnet. Die Eigenschaften des CompositionSurfaceBrush können die Bitmap innerhalb der Grenzen des visuellen Elements ausrichten und Strecken verwendet werden.

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

### <a name="paint-with-a-custom-drawing"></a>Zeichnen Sie mit einer benutzerdefinierten Zeichnung
Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, um einen Bereich mit Pixeln aus einer ICompositionSurface gerendert mithilfe von [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm) (oder D2D) zeichnen.

Der folgende Code zeigt, dass ein SpriteVisual mit einem führen Sie auf eine ICompositionSurface gerenderte Text gezeichnet mithilfe von Win2D. Beachten Sie, um Win2D zu verwenden, Sie das [Win2D-NuGet](http://www.nuget.org/packages/Win2D.uwp) -Paket in Ihr Projekt einschließen müssen.

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

Auf ähnliche Weise kann die CompositionSurfaceBrush auch zum Zeichnen eines spritevisual-Elements mit einem Win2D Interop verwenden Spielinhalte verwendet werden. [In diesem Beispiel](https://github.com/Microsoft/Win2D-Samples/tree/master/CompositionExample) enthält ein Beispiel zur Verwendung von Win2D zum Zeichnen eines spritevisual-Elements mit einem Spielinhalte.

### <a name="paint-with-a-video"></a>Zeichnen Sie mit einem video
Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, um einen Bereich mit Pixeln aus einer ICompositionSurface mit einem Video über der [MediaPlayer](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer) -Klasse geladen gerendert zu zeichnen.

Der folgende Code zeigt, dass ein SpriteVisual mit einem Video auf einer ICompositionSurface geladen gezeichnet.

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

### <a name="paint-with-a-filter-effect"></a>Zeichnen Sie mit einem Filtereffekt

Eine [CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush) zeichnet einen Bereich mit der Ausgabe von einem CompositionEffect. Effekte in der visuellen Ebene können als animierbaren auf eine Auflistung von Quellinhalt z. B. Farben, Farbverläufe, Bilder, Videos, Swapchains, Regionen der Benutzeroberfläche oder Strukturen von visuellen Elementen angewendeten Filtereffekte betrachtet werden. Der Inhalt der Quelle wird in der Regel mit einer anderen CompositionBrush angegeben.

Die folgende Abbildung und der Code zeigt ein spritevisual-Elements gezeichnet mit einem Bild einer Katze, die Sättigung Filtereffekt angewendet wurde.

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

Weitere Informationen zum Erstellen eines Effekts mit CompositionBrushes finden Sie unter [Effekte in der visuellen Ebene](https://docs.microsoft.com/en-us/windows/uwp/composition/composition-effects)

### <a name="paint-with-a-compositionbrush-with-opacity-mask-applied"></a>Zeichnen Sie mit einem CompositionBrush mit Deckkraftmaske angewendet

Eine [CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush) zeichnet einen Bereich mit einem CompositionBrush mit einer Deckkraftmaske angewendet wird. Die Quelle des die Deckkraftmaske kann alle CompositionBrush des Typs CompositionColorBrush, CompositionLinearGradientBrush, CompositionSurfaceBrush, CompositionEffectBrush oder CompositionNineGridBrush sein. Die Deckkraftmaske muss als eine CompositionSurfaceBrush angegeben werden.

Die folgende Abbildung und der Code zeigt ein Element, das mit einem CompositionMaskBrush SpriteVisual. Die Quelle der Maske ist ein CompositionLinearGradientBrush die maskiert wird, um einen Kreis mit einem Bild Kreises als Maske aussehen.

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

### <a name="paint-with-a-compositionbrush-using-ninegrid-stretch"></a>Zeichnen Sie mit einer CompositionBrush mit NineGrid stretch

Eine [CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush) zeichnet einen Bereich mit einem CompositionBrush, die mit der neun Raster-gestreckt wird. Die neun Raster-können Sie Rahmen und Ecken von einem "compositionbrush" anders als den Mittelpunkt gestreckt. Die Quelle des der neun Raster Stretch kann, indem Sie alle CompositionBrush des Typs CompositionColorBrush, CompositionSurfaceBrush oder CompositionEffectBrush.

Der folgende Code zeigt, dass ein SpriteVisual mit einem CompositionNineGridBrush gezeichnet. Die Quelle der Maske ist ein CompositionSurfaceBrush die gestreckt wird mit einem neun-Raster.

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

### <a name="paint-using-background-pixels"></a>Zeichnen mit Hintergrund Pixel

Eine [CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush) zeichnet einen Bereich mit den Inhalt hinter den Bereich. Eine CompositionBackdropBrush wird nie alleine verwendet, jedoch stattdessen als Eingabe für eine andere CompositionBrush wie ein EffectBrush verwendet wird. Beispielsweise können Sie einen Effekt Milchglas mithilfe einer CompositionBackdropBrush als Eingabe für einen Weichzeichnereffekt zu erzielen.

Der folgende Code zeigt eine kleine visuelle Struktur ein Bild mit CompositionSurfaceBrush und eine Überlagerung Milchglas über dem Bild erstellt. Die Überlagerung Milchglas wird durch das Platzieren eines spritevisual-Elements mit einem EffectBrush über dem Bild gefüllt erstellt. Die EffectBrush verwendet eine CompositionBackdropBrush als Eingabe für den Weichzeichnereffekt zu.

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

## <a name="combining-compositionbrushes"></a>Kombinieren von CompositionBrushes
Eine Reihe von CompositionBrushes verwenden Sie andere CompositionBrushes als Eingaben. Beispielsweise kann mithilfe der Methode SetSourceParameter verwendet werden zu einem anderen CompositionBrush als Eingabe für eine CompositionEffectBrush festgelegt. Die folgende Tabelle skizziert die unterstützten Kombinationen von CompositionBrushes. Beachten Sie, dass eine nicht unterstützte Kombination eine Ausnahme ausgelöst wird.

<table>
<tbody>
<tr>
<th>Brush</th>
<th>EffectBrush.SetSourceParameter()</th>
<th>MaskBrush.Mask</th>
<th>MaskBrush.Source</th>
<th>NineGridBrush.Source</th>
</tr>
<tr>
<td>CompositionColorBrush</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
</tr>
<tr>
<td>CompositionLinear<br />GradientBrush</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
<td>NO</td>
</tr>
<tr>
<td>CompositionSurfaceBrush</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
</tr>
<tr>
<td>CompositionEffectBrush</td>
<td>NEIN</td>
<td>NEIN</td>
<td>JA</td>
<td>NO</td>
</tr>
<tr>
<td>CompositionMaskBrush</td>
<td>NEIN</td>
<td>NEIN</td>
<td>NEIN</td>
<td>NEIN</td>
</tr>
<tr>
<td>CompositionNineGridBrush</td>
<td>JA</td>
<td>JA</td>
<td>JA</td>
<td>NO</td>
</tr>
<tr>
<td>CompositionBackdropBrush</td>
<td>JA</td>
<td>NEIN</td>
<td>NEIN</td>
<td>NEIN</td>
</tr>
</tbody>
</table>


## <a name="using-a-xaml-brush-vs-compositionbrush"></a>Verwenden eine XAML-Pinsel im Vergleich zu CompositionBrush

Die folgende Tabelle enthält eine Liste mit Szenarien und gibt an, ob XAML oder Komposition Pinsel verwenden beim Zeichnen von UIElement oder eines spritevisual-Elements in Ihrer Anwendung vorgeschrieben ist. 

> [!NOTE]
> Wenn ein CompositionBrush für ein XAML-UIElement vorgeschlagen wird, wird davon ausgegangen, dass die CompositionBrush verpackt ist eine XamlCompositionBrushBase verwenden.

|Szenario                                                                   | XAML-UIElement                                                                                                |Komposition SpriteVisual
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------
|Zeichnen eines Bereichs mit Volltonfarbe.                                             |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit animierten Farbe                                          |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit einem statischen Farbverlauf                                       |[LinearGradientBrush](https://msdn.microsoft.com/library/windows/apps/BR210108)                            |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit animierten Farbverlaufsstopps                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)                                                                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit einem Bild                                                |[ImageBrush](https://msdn.microsoft.com/library/windows/apps/BR210101)                                     |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415)
|Zeichnen eines Bereichs mit einer Webseite                                               |[WebViewBrush](https://msdn.microsoft.com/library/windows/apps/BR227703)                                   |n.a.
|Zeichnen eines Bereichs mit einem Bild mit NineGrid stretch                         |[Image-Steuerelement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Image)                   |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit animierten NineGrid stretch                               |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)                                                                                       |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit einem Spielinhalte                                             |[SwapChainPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel)                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Spielinhalte Interoperabilität
|Zeichnen eines Bereichs mit einem video                                                 |[MediaElement](https://msdn.microsoft.com/library/windows/apps/mt187272.aspx)                                                                                                  |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Media-Interoperabilität
|Zeichnen eines Bereichs mit benutzerdefinierten 2D Zeichnung                                       |[CanvasControl](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_UI_Xaml_CanvasControl.htm) von Win2D                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Win2D-Interoperabilität
|Zeichnen eines Bereichs mit nicht animierte Maske                                       |Verwenden Sie XAML- [Formen](https://docs.microsoft.com/windows/uwp/graphics/drawing-shapes) , um eine Maske definieren   |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit eine animierte Maske                                        |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)                                                                                           |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit einem Filtereffekt animierte                               |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)                                                                                         |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)
|Zeichnen eines Bereichs mit einem Effekt auf Hintergrund Pixel angewendet        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)                                                                                        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)

## <a name="related-topics"></a>Verwandte Themen

[Komposition native DirectX und Direct2D-Interoperabilität mit "beginDraw" und "EndDraw"](composition-native-interop.md)

[XAML-Pinsel-Interoperabilität mit XamlCompositionBrushBase](/windows/uwp/design/style/brushes#xamlcompositionbrushbase)
