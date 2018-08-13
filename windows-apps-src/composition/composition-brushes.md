---
author: jwmsft
ms.assetid: 03dd256f-78c0-e1b1-3d9f-7b3afab29b2f
title: Kompositionspinsel
description: Ein Pinsel zeichnet den Bereich eines Visual-Objekts mit der zugehörigen Ausgabe. Verschiedene Pinsel haben unterschiedliche Ausgabetypen.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 103ecd24c35d75d3ea1d305d7294048dc628d2e2
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1038570"
---
# <a name="composition-brushes"></a>Kompositionspinsel
Alles aus einer Anwendung UWP auf dem Bildschirm angezeigt wird angezeigt, da er von einem Pinsel gezeichnet wurde. Pinsel können Sie Benutzer mit Inhalten zwischen einfachen, einfarbige Farben und Bilder oder Zeichnungen komplexe Effekte verketten Objekte der Benutzeroberfläche (UI) zeichnen. In diesem Thema werden die Begriffe zum Zeichnen mit CompositionBrush vorgestellt.

Beachten Sie beim Arbeiten mit XAML UWP-app können Sie sich entschieden, "UIElement" mit einem [XAML-Pinsel](/windows/uwp/design/style/brushes) oder eine [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush)zeichnen. In der Regel ist es einfacher und ratsam, einen XAML-Pinsel wählen, wenn Ihr Szenario von einem XAML-Pinsel unterstützt wird. Beispielsweise Animieren der Farbe einer Schaltfläche, die Füllung eine Text- oder eine Form mit einem Bild ändern. Andererseits, wenn Sie versuchen, etwas, das von einem XAML-Pinsel wie wie Zeichnen mit eine animierte Maske oder eine animierte neun Raster dehnen oder eine Kette Effekt nicht unterstützt wird, können eine CompositionBrush Sie durch die Verwendung von ["UIElement" Zeichnen XamlCompositionBrushBase](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).

Bei der Arbeit mit dem Visual Layer muss ein CompositionBrush zum Zeichnen einer [SpriteVisual](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.SpriteVisual)im Bereichs verwendet werden.

-   [Voraussetzungen](./composition-brushes.md#prerequisites)
-   [Zeichnen mit CompositionBrush](./composition-brushes.md#paint-with-a-compositionbrush)
    -   [Zeichnen Sie mit einer Volltonfarbe](./composition-brushes.md#paint-with-a-solid-color)
    -   [Zeichnen Sie mit der ein linearer Farbverlauf](./composition-brushes.md#paint-with-a-linear-gradient)
    -   [Zeichnen mit einem Bild](./composition-brushes.md#paint-with-an-image)
    -   [Zeichnen Sie mit einer benutzerdefinierten Zeichnung](./composition-brushes.md#paint-with-a-custom-drawing)
    -   [Zeichnen mit einem video](./composition-brushes.md#paint-with-a-video)
    -   [Zeichnen Sie mit einen Filtereffekt](./composition-brushes.md#paint-with-a-filter-effect)
    -   [Zeichnen Sie mit einem CompositionBrush mit einer Durchlässigkeitsmaske](./composition-brushes.md#paint-with-a-compositionbrush-with-opacity-mask-applied)
    -   [Zeichnen Sie mit einer CompositionBrush mit NineGrid Dehnen](./composition-brushes.md#paint-with-a-compositionbrush-using-ninegrid-stretch)
    -   [Zeichnen mit Hintergrund Pixel](./composition-brushes.md#paint-using-background-pixels)
-   [Kombinieren von CompositionBrushes](./composition-brushes.md#combining-compositionbrushes)
-   [Verwenden eine XAML-Pinsel im Vergleich zu CompositionBrush](./composition-brushes.md#using-a-xaml-brush-vs-compositionbrush)
-   [Verwandte Themen](./composition-brushes.md#related-topics)

## <a name="prerequisites"></a>Voraussetzungen
In dieser Übersicht wird davon ausgegangen, dass Sie mit der Struktur einer grundlegenden Zusammensetzung Anwendung vertraut sind, wie in der [Übersicht über die visuelle Ebene](visual-layer.md)beschrieben.

## <a name="paint-with-a-compositionbrush"></a>Zeichnen mit einem CompositionBrush

Eine [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush) zeichnet"" einen Bereich mit der zugehörigen Ausgabe. Verschiedene Pinsel haben unterschiedliche Ausgabetypen. Einige Pinsel zeichnen einen Bereich mit einer Volltonfarbe, andere mit einem Farbverlauf, Bild, benutzerdefiniertes Zeichnen oder Effekt. Es gibt auch spezielle Pinsel, die das Verhalten von anderen Pinsel ändern. Beispielsweise Durchlässigkeitsmaske kann verwendet werden, um das Steuerelement durch ein CompositionBrush der Bereich gezeichnet wird, oder ein neun-Raster zum Steuern der Strecken auf eine CompositionBrush angewendet wird, wenn Sie einen Bereich zeichnen verwendet werden. CompositionBrush kann einer der folgenden Objekttypen sein:

|Klasse                                   |Details                                         |Eingeführt In|
|-------------------------------------|---------------------------------------------------------|--------------------------------------|
|[CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush)         |Zeichnet einen Bereich mit einer Volltonfarbe                        |Update für Windows 10 November (SDK 10586)|
|[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush)       |Zeichnet einen Bereich mit dem Inhalt des ein [ICompositionSurface](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Composition.ICompositionSurface)|Update für Windows 10 November (SDK 10586)|
|[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)        |Zeichnet einen Bereich mit dem Inhalt des ein Effekt Zusammensetzung |Update für Windows 10 November (SDK 10586)|
|[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)          |Zeichnet ein visuelles mit einer CompositionBrush mit einer Durchlässigkeitsmaske |Update für Windows 10 Jahrestag (SDK 14393)
|[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)      |Zeichnet einen Bereich mit einer CompositionBrush mit einer NineGrid Dehnen |Update für Windows 10 Jahrestag SDK (14393)
|[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)|Zeichnet einen Bereich mit ein linearer Farbverlauf                    |Windows 10 fallen Ersteller Update (Insider Preview – SDK)
|[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)     |Zeichnet einen Bereich wird durch stichprobenziehung Hintergrund Pixel aus der Anwendung oder Pixel direkt hinter der Anwendung Fenster auf dem Desktop. Verwendet als Eingabe in eine andere CompositionBrush wie eine CompositionEffectBrush | Update für Windows 10 Jahrestag (SDK 14393)

### <a name="paint-with-a-solid-color"></a>Zeichnen Sie mit einer Volltonfarbe

Ein [CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush) zeichnet einen Bereich mit einer Volltonfarbe. Es gibt verschiedene Arten, um die Farbe von SolidColorBrush anzugeben. Sie können beispielsweise die Kanäle Alpha, Rot, Grün und Blau (ARGB) angeben oder verwenden Sie eine der vordefinierten Farben von [Colors](https://docs.microsoft.com/uwp/api/windows.ui.colors) -Klasse bereitgestellt.

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

### <a name="paint-with-a-linear-gradient"></a>Zeichnen Sie mit der ein linearer Farbverlauf

Ein [CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush) zeichnet einen Bereich mit einem linearen Farbverlauf. Ein linearer Farbverlauf mischt zwei oder mehr Farben entlang einer Linie der Farbverlauf Achse. GradientStop-Objekten können Sie die Farben des Farbverlaufs und ihre Positionen im festlegen.

Die folgende Abbildung und Code zeigt ein SpriteVisual mit LinearGradientBrush 2 reagiert, die mit einer Farbe Rot und Gelb gezeichnet.

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

### <a name="paint-with-an-image"></a>Zeichnen mit einem Bild

Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) zeichnet einen Bereich mit Pixel auf ein ICompositionSurface gerendert. Beispielsweise kann ein CompositionSurfaceBrush zum Zeichnen eines Bereichs mit einem Bild auf einer ICompositionSurface Oberfläche mit [LoadedImageSurface](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.loadedimagesurface) API gerendert verwendet werden.

Die folgende Abbildung und Code zeigt, dass eine SpriteVisual mit eine Bitmap mit einer Licorice auf eine ICompositionSurface mit LoadedImageSurface gerendert gezeichnet. Die Eigenschaften des CompositionSurfaceBrush können Dehnen und Ausrichten der Bitmap innerhalb der Grenzen des visuellen verwendet werden.

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
Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch zum Zeichnen eines Bereichs mit Pixeln aus einer ICompositionSurface mit [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm) (oder D2D) gerendert verwendet werden.

Der folgende Code zeigt, dass eine SpriteVisual mit eines gerenderten auf ein ICompositionSurface Textlaufs gezeichnet Win2D verwenden. Beachten Sie, um Win2D zu verwenden, Sie das [Win2D NuGet](http://www.nuget.org/packages/Win2D.uwp) -Paket in das Projekt einschließen müssen.

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

In ähnlicher Weise kann die CompositionSurfaceBrush auch zum Zeichnen einer SpriteVisual mit einer SwapChain mit Win2D-Interop verwendet werden. [Dieses Beispiel](https://github.com/Microsoft/Win2D-Samples/tree/master/CompositionExample) enthält ein Beispiel dafür, wie Sie Win2D verwenden, um eine SpriteVisual mit einem Swapchain zeichnen.

### <a name="paint-with-a-video"></a>Zeichnen mit einem video
Ein [CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, zum Zeichnen eines Bereichs mit Pixeln aus einer ICompositionSurface gerendert wird, verwenden ein Video über das [MediaPlayer](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer) -Klasse geladen.

Der folgende Code zeigt, dass eine SpriteVisual mit einem Video auf einer ICompositionSurface geladen gezeichnet.

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

### <a name="paint-with-a-filter-effect"></a>Zeichnen Sie mit einen Filtereffekt

Ein [CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush) zeichnet einen Bereich mit einer CompositionEffect-Ausgabe. Effekte in der visuellen Ebene möglicherweise als animierbaren auf eine Auflistung von Inhaltsquellen wie Farben, Verläufe, Bilder, Videos, Swapchains, Regionen der Benutzeroberfläche oder Strukturen von visuellen Elementen angewendete Filtereffekte betrachtet werden. Der Inhalt der Quelle ist in der Regel mit einem anderen CompositionBrush angegeben.

Die in der folgenden Abbildung und Code zeigt ein SpriteVisual mit einer Katze, die Sättigung Filtereffekts an angewendet hat ein Bild gezeichnet.

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

Weitere Informationen zum Erstellen von CompositionBrushes wirksam finden Sie unter [Effekte in Visual-Ebene](https://docs.microsoft.com/en-us/windows/uwp/composition/composition-effects)

### <a name="paint-with-a-compositionbrush-with-opacity-mask-applied"></a>Zeichnen Sie mit einem CompositionBrush mit Durchlässigkeitsmaske angewendet

Ein [CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush) zeichnet einen Bereich mit einer CompositionBrush mit einer Durchlässigkeitsmaske angewendet wird. Die Quelle der Durchlässigkeitsmaske kann eine beliebige CompositionBrush vom Typ CompositionColorBrush, CompositionLinearGradientBrush, CompositionSurfaceBrush, CompositionEffectBrush oder CompositionNineGridBrush sein. Die Durchlässigkeitsmaske muss als ein CompositionSurfaceBrush angegeben werden.

Die folgende Abbildung und Code zeigt ein SpriteVisual mit einem CompositionMaskBrush gezeichnet. Die Quelle des Codeformats ist eine CompositionLinearGradientBrush die maskiert ist ein Kreis mit einem Bild des Kreises als eine Maske aussehen.

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

### <a name="paint-with-a-compositionbrush-using-ninegrid-stretch"></a>Zeichnen Sie mit einer CompositionBrush mit NineGrid Dehnen

Ein [CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush) zeichnet einen Bereich mit einer CompositionBrush, die mithilfe des neun Grid-Prinzip gestreckt wird. Das Prinzip der neun-Raster können Sie Rahmen und Ecken, der ein CompositionBrush anders als seine Mitte gestreckt. Die Quelle der der neun Raster Strecken kann, indem Sie eine beliebige CompositionBrush vom Typ CompositionColorBrush, CompositionSurfaceBrush oder CompositionEffectBrush.

Der folgende Code zeigt, dass eine SpriteVisual mit einem CompositionNineGridBrush gezeichnet. Die Quelle des Codeformats ist eine CompositionSurfaceBrush die gestreckt wird mit einem neun-Raster.

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

Ein [CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush) zeichnet einen Bereich mit dem Inhalt hinter den Bereich. Eine CompositionBackdropBrush wird auf einem eigenen nie verwendet, aber stattdessen als Eingabe in eine andere CompositionBrush wie ein EffectBrush verwendet wird. Beispielsweise können Sie mithilfe einer CompositionBackdropBrush als Eingabe für einen Effekt Blur eine Glas Wirkung erzielen.

Der folgende Code zeigt eine kleine visuelle Struktur ein Bild mit CompositionSurfaceBrush und eine Überlagerung Glas über dem Bild zu erstellen. Die Überlagerung Glas wird durch ein SpriteVisual mit einer EffectBrush über dem Bild gefüllt platzieren erstellt. Die EffectBrush verwendet eine CompositionBackdropBrush als Eingabe für den Effekt "Weichzeichnen".

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
Eine Reihe von CompositionBrushes verwenden andere CompositionBrushes als Eingaben. Beispielsweise kann mithilfe der SetSourceParameter-Methode verwendet werden zu einer anderen CompositionBrush als Eingabe für eine CompositionEffectBrush festgelegt. In der folgenden Tabelle werden die unterstützten Kombinationen von CompositionBrushes beschrieben. Beachten Sie, dass eine nicht unterstützte Kombination eine Ausnahme ausgelöst.

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

Die folgende Tabelle enthält eine Liste der Szenarien und gibt an, ob Verwendung von XAML- oder Zusammensetzung Pinsel vorgeschrieben ist, beim Zeichnen "UIElement" oder ein SpriteVisual in der Anwendung. 

> [!NOTE]
> Wenn eine CompositionBrush für eine Verwendung von XAML-UIElement vorgeschlagen wird, wird davon ausgegangen, dass die CompositionBrush gepackt ist mit einer XamlCompositionBrushBase.

|Szenario                                                                   | XAML-UIElement                                                                                                |Zusammensetzung SpriteVisual
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------
|Zeichnen eines Bereichs mit Volltonfarbe                                             |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit animierte Farbe                                          |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit einem Farbverlauf statische                                       |[LinearGradientBrush](https://msdn.microsoft.com/library/windows/apps/BR210108)                            |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit animierte Farbverlaufstopps                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)                                                                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit einem Bild                                                |[ImageBrush](https://msdn.microsoft.com/library/windows/apps/BR210101)                                     |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415)
|Zeichnen eines Bereichs mit einer Webseite                                               |[WebViewBrush](https://msdn.microsoft.com/library/windows/apps/BR227703)                                   |n.v.
|Zeichnen eines Bereichs mit einem Bild mit NineGrid Dehnen                         |[Bild-Steuerelement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Image)                   |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit animierte NineGrid Dehnen                               |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)                                                                                       |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit einer swapchain                                             |[SwapChainPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel)                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Swapchain-interop
|Zeichnen eines Bereichs mit einem video                                                 |[MediaElement](https://msdn.microsoft.com/library/windows/apps/mt187272.aspx)                                                                                                  |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Media-interop
|Zeichnen eines Bereichs mit benutzerdefinierten 2D Zeichnung                                       |[CanvasControl](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_UI_Xaml_CanvasControl.htm) aus Win2D                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Win2D-interop
|Zeichnen eines Bereichs mit Maske nicht animiert                                       |Verwenden von XAML- [Shapes](https://docs.microsoft.com/windows/uwp/graphics/drawing-shapes) eine Maske definieren   |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit eine animierte Maske                                        |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)                                                                                           |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit einer animierte Filtereffekts an                               |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)                                                                                         |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)
|Zeichnen eines Bereichs mit einem Effekt in Pixel Hintergrund angewendet        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)                                                                                        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)

## <a name="related-topics"></a>Verwandte Themen

[Zusammensetzung systemeigenen DirectX und Direct2D Interop mit beginDraw- und EndDraw-](composition-native-interop.md)

[XAML-Pinsel Interop mit XamlCompositionBrushBase](/windows/uwp/design/style/brushes#xamlcompositionbrushbase)
