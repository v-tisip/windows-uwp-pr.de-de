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
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919787"
---
# <a name="composition-brushes"></a>Kompositionspinsel
Alles aus einer Anwendung UWP auf dem Bildschirm sichtbar ist sichtbar, weil es mit einem Pinsel gezeichnet wurde. Pinsel können Sie Benutzer mit einfachen, einfarbige Farben Bilder oder Zeichnungen komplexer Effekte Kette von Benutzeroberflächen-Objekte zeichnen. Dieses Thema stellt die Konzepte mit CompositionBrush.

Beachten Sie beim Arbeiten mit XAML UWP app kann sich ein UIElement mit [XAML-Pinsel](/windows/uwp/design/style/brushes) oder [CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush)zu zeichnen. Normalerweise ist es einfacher und ratsam XAML Pinsel wählen, wenn Ihr Szenario eines Pinsels XAML unterstützt. Animieren z. B. die Farbe einer Schaltfläche Ändern der Füllung einen Text oder eine Form mit einem Bild. Andererseits, wenn Sie versuchen, etwas zu tun, die nicht von einem XAML-Pinsel wie zeichnen eine animierte Maske oder eine animierte neun Raster verlängern einer effektkette unterstützt wird, können eine CompositionBrush Sie ein UIElement durch [Zeichnen XamlCompositionBrushBase](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.xamlcompositionbrushbase).

Beim Arbeiten mit der visuellen Ebene muss ein CompositionBrush Bereich [SpriteVisual](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.SpriteVisual)Zeichnen verwendet werden.

-   [Voraussetzungen](./composition-brushes.md#prerequisites)
-   [Mit CompositionBrush](./composition-brushes.md#paint-with-a-compositionbrush)
    -   [Zeichnen Sie mit einer Volltonfarbe](./composition-brushes.md#paint-with-a-solid-color)
    -   [Zeichnen Sie mit einem linearen Farbverlauf](./composition-brushes.md#paint-with-a-linear-gradient)
    -   [Zeichnen mit einem Bild](./composition-brushes.md#paint-with-an-image)
    -   [Eine benutzerdefinierte Zeichnung zeichnen](./composition-brushes.md#paint-with-a-custom-drawing)
    -   [Zeichnen mit einem video](./composition-brushes.md#paint-with-a-video)
    -   [Zeichnen Sie mit einem Filtereffekt](./composition-brushes.md#paint-with-a-filter-effect)
    -   [Malen Sie mit einem CompositionBrush mit einer Deckkraftmaske](./composition-brushes.md#paint-with-a-compositionbrush-with-opacity-mask-applied)
    -   [Zeichnen Sie mit einer CompositionBrush mit NineGrid Dehnen](./composition-brushes.md#paint-with-a-compositionbrush-using-ninegrid-stretch)
    -   [Zeichnen mit Hintergrundpixel](./composition-brushes.md#paint-using-background-pixels)
-   [Kombinieren von CompositionBrushes](./composition-brushes.md#combining-compositionbrushes)
-   [Mithilfe einer XAML-Pinsel und CompositionBrush](./composition-brushes.md#using-a-xaml-brush-vs-compositionbrush)
-   [Verwandte Themen](./composition-brushes.md#related-topics)

## <a name="prerequisites"></a>Voraussetzungen
In dieser Übersicht wird davon ausgegangen, dass Sie mit einer einfachen Zusammensetzung Anwendung vertraut sind, wie in der [Übersicht über die visuelle Ebene](visual-layer.md).

## <a name="paint-with-a-compositionbrush"></a>Mit einem CompositionBrush

[CompositionBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBrush) zeichnet"" einen Bereich mit zugehöriger Ausgabe. Verschiedene Pinsel haben unterschiedliche Ausgabetypen. Einige Pinsel zeichnen einen Bereich mit einer Volltonfarbe, andere mit einem Farbverlauf, Bild, zeichnen oder Effekt. Es gibt auch spezielle Pinsel, die das Verhalten des anderen Pinsel ändern. Z. B. Deckkraftmaske dienen zur Kontrolle von einer CompositionBrush der Bereich gezeichnet wird oder 9-Raster kann zur Steuerung der Strecken auf eine CompositionBrush angewendet, wenn einen Bereich zeichnen. CompositionBrush kann einer der folgenden Typen sein:

|Klasse                                   |Details                                         |Eingeführt|
|-------------------------------------|---------------------------------------------------------|--------------------------------------|
|[CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush)         |Zeichnet einen Bereich mit einer Volltonfarbe                        |Windows10 November Update (SDK 10586)|
|[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush)       |Zeichnet einen Bereich mit einem [ICompositionSurface](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Composition.ICompositionSurface)|Windows10 November Update (SDK 10586)|
|[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)        |Zeichnet einen Bereich mit dem Inhalt der Komposition Effekt |Windows10 November Update (SDK 10586)|
|[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)          |Zeichnet ein visuelles mit einem CompositionBrush mit einer Deckkraftmaske |Windows10 Jubiläum Update (SDK 14393)
|[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)      |Zeichnet einen Bereich mit einer CompositionBrush mit einer NineGrid verlängern |Windows10 Jubiläum Update SDK (14393)
|[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)|Zeichnet einen Bereich mit einem linearen Farbverlauf                    |Windows 10 liegen Schöpfer Update (Insider Vorschau SDK)
|[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)     |Zeichnet einen Bereich stichprobenweise Hintergrundpixel aus der Anwendung oder Pixel direkt hinter dem Anwendungsfenster auf Desktop. Verwendet als Eingabe für eine andere CompositionBrush wie ein CompositionEffectBrush | Windows 10 Jahre Update (SDK 14393)

### <a name="paint-with-a-solid-color"></a>Zeichnen Sie mit einer Volltonfarbe

[CompositionColorBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush) zeichnet einen Bereich mit einer Volltonfarbe. Es gibt verschiedene Arten an die Farbe von SolidColorBrush. Beispielsweise können Sie die Kanäle Alpha, Rot, Blau und Grün (ARGB) angegeben oder verwenden Sie eine der [Farben](https://docs.microsoft.com/uwp/api/windows.ui.colors) -Klasse vordefinierten Farben.

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

### <a name="paint-with-a-linear-gradient"></a>Zeichnen Sie mit einem linearen Farbverlauf

[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush) zeichnet einen Bereich mit einem linearen Farbverlauf. Ein linearer Farbverlauf mischt zwei oder mehr Farben entlang einer Linie, der Farbverlaufsachse. GradientStop-Objekte verwenden Sie Farben im Farbverlauf und ihre Positionen an.

Die folgende Abbildung und Code zeigt ein SpriteVisual mit einem LinearGradientBrush 2 reagiert mit einer roten und gelben Farbe gezeichnet.

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

[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) zeichnet einen Bereich mit Pixeln auf einer ICompositionSurface gerendert. Eine CompositionSurfaceBrush kann beispielsweise verwendet werden, zum Zeichnen eines Bereichs mit einem Bild auf einer ICompositionSurface mit [LoadedImageSurface](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.loadedimagesurface) API gerendert.

Die folgende Abbildung und Code zeigt einen SpriteVisual mit einer Bitmap ein Süßholz dargestellt auf eine ICompositionSurface mit LoadedImageSurface gezeichnet. Die Eigenschaften des CompositionSurfaceBrush dienen und Ausrichten der Bitmaps innerhalb der Grenzen des visuellen.

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

### <a name="paint-with-a-custom-drawing"></a>Eine benutzerdefinierte Zeichnung zeichnen
[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, zum Zeichnen eines Bereichs mit Pixeln aus einem ICompositionSurface mit [Win2D](http://microsoft.github.io/Win2D/html/Introduction.htm) (oder D2D) gerendert.

Der folgende Code zeigt, dass eine SpriteVisual mit Lauftext gerenderten auf ein ICompositionSurface gezeichnet mit Win2D. Hinweis Um Win2D benötigen Sie [Win2D NuGet](http://www.nuget.org/packages/Win2D.uwp) -Paket in das Projekt einschließen.

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

Ebenso kann die CompositionSurfaceBrush auch zum Zeichnen einer SpriteVisual mit einer SwapChain mit Win2D-Interop verwendet werden. [Dieses Beispiel](https://github.com/Microsoft/Win2D-Samples/tree/master/CompositionExample) enthält ein Beispiel zur Verwendung Win2D SpriteVisual mit einem Swapchain gezeichnet.

### <a name="paint-with-a-video"></a>Zeichnen mit einem video
[CompositionSurfaceBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) kann auch verwendet werden, zum Zeichnen eines Bereichs mit Pixeln aus einer ICompositionSurface mit der [MediaPlayer](https://docs.microsoft.com/en-us/uwp/api/Windows.Media.Playback.MediaPlayer) -Klasse geladenen Videos gerendert.

Der folgende Code zeigt ein SpriteVisual mit einem Video auf einer ICompositionSurface geladen gezeichnet.

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

[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush) zeichnet einen Bereich mit einem CompositionEffect. Effekte in der visuellen Ebene können als animierbar Filtereffekte Sammlung Quellinhalt wie Farben, Verläufe, Bilder, Videos, Swapchains, Bereiche der Benutzeroberfläche oder Strukturen Visuals betrachtet werden. Inhalt der Quelle wird normalerweise mit einer anderen CompositionBrush angegeben.

Die folgende Abbildung und Code zeigt einen SpriteVisual mit einem Cat, die Sättigung Filtereffekt gezeichnet.

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

Weitere Informationen zum Erstellen eines Effekts mit CompositionBrushes finden Sie unter [Effekte auf visueller Ebene](https://docs.microsoft.com/en-us/windows/uwp/composition/composition-effects)

### <a name="paint-with-a-compositionbrush-with-opacity-mask-applied"></a>Malen Sie mit einem CompositionBrush mit Deckkraftmaske angewendet

[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush) zeichnet einen Bereich mit einem CompositionBrush mit einer Deckkraftmaske angewendet. Die Quelle der Deckkraftmaske kann alle CompositionBrush des Typs CompositionColorBrush, CompositionLinearGradientBrush, CompositionSurfaceBrush, CompositionEffectBrush oder CompositionNineGridBrush sein. Die Deckkraftmaske muss als ein CompositionSurfaceBrush angegeben werden.

Die folgende Abbildung und Code zeigt einen SpriteVisual mit einem CompositionMaskBrush gezeichnet. Die Maske ist ein CompositionLinearGradientBrush, wie einen Kreis mit einem Bild des Kreises als Maske maskiert.

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

[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush) zeichnet einen Bereich mit einer CompositionBrush 9-Raster Metapher gestreckt wird. 9-Raster Metapher können Sie Kanten und Ecken einer CompositionBrush anders als Mittelpunkt gestreckt. Die Quelle der neun Raster Strecken kann durch CompositionBrush des Typs CompositionColorBrush, CompositionSurfaceBrush oder CompositionEffectBrush.

Der folgende Code zeigt ein SpriteVisual mit einem CompositionNineGridBrush gezeichnet. Die Maske ist ein CompositionSurfaceBrush, mit einem 9-Raster gestreckt wird.

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

### <a name="paint-using-background-pixels"></a>Zeichnen mit Hintergrundpixel

[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush) zeichnet einen Bereich mit dem Inhalt hinter dem. Ein CompositionBackdropBrush wird nie verwendet, aber wird als Eingabe für eine andere CompositionBrush wie ein EffectBrush verwendet. Beispielsweise können Sie mithilfe einer CompositionBackdropBrush als Eingabe für einen Weichzeichner eine Milchglas Wirkung erzielen.

Der folgende Code zeigt eine kleine visuelle Struktur zum Erstellen eines Abbildes mit CompositionSurfaceBrush und ein Glas Overlay über dem Bild. Milchglas Overlay wird erstellt, mit einem SpriteVisual mit einem EffectBrush über dem Bild gefüllt. Die EffectBrush verwendet einen CompositionBackdropBrush als Eingabe für den Weichzeichnereffekt.

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
Anzahl der CompositionBrushes verwenden andere CompositionBrushes als Eingabe. Beispielsweise kann mithilfe der SetSourceParameter-Methode verwendet werden zu einem anderen CompositionBrush als Eingabe für eine CompositionEffectBrush festgelegt. In der folgenden Tabelle werden die unterstützten Kombinationen von CompositionBrushes. Beachten Sie, dass eine nicht unterstützte Kombination eine Ausnahme ausgelöst.

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


## <a name="using-a-xaml-brush-vs-compositionbrush"></a>Mithilfe einer XAML-Pinsel und CompositionBrush

Folgende Tabelle enthält eine Liste der Szenarien und beim "UIElement" oder eine SpriteVisual in der Anwendung, ob XAML oder Komposition Pinsel verwenden vorgeschrieben. 

> [!NOTE]
> Wenn ein CompositionBrush für ein UIElement XAML vorgeschlagen, davon aus, dass der CompositionBrush mit einer XamlCompositionBrushBase gepackt ist.

|Szenario                                                                   | XAML-UIElement                                                                                                |Komposition SpriteVisual
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------
|Zeichnen eines Bereichs mit Volltonfarbe                                             |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit animierten                                          |[SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962)                                |[CompositionColorBrush](https://msdn.microsoft.com/library/windows/apps/Mt589399)
|Zeichnen eines Bereichs mit einem statischen Farbverlauf                                       |[LinearGradientBrush](https://msdn.microsoft.com/library/windows/apps/BR210108)                            |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit animierten Farbverlaufsstopps                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)                                                                                 |[CompositionLinearGradientBrush](https://docs.microsoft.com/uwp/api/windows.ui.composition.compositionlineargradientbrush)
|Zeichnen eines Bereichs mit einem Bild                                                |[ImageBrush](https://msdn.microsoft.com/library/windows/apps/BR210101)                                     |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415)
|Zeichnen eines Bereichs mit einer Webseite                                               |[WebViewBrush](https://msdn.microsoft.com/library/windows/apps/BR227703)                                   |n.a.
|Zeichnen eines Bereichs mit einem Bild mit NineGrid Dehnen                         |[Bild-Steuerelement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Image)                   |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit animierten NineGrid                               |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)                                                                                       |[CompositionNineGridBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionNineGridBrush)
|Zeichnen eines Bereichs mit einem swapchain                                             |[SwapChainPanel](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SwapChainPanel)                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Swapchain interop
|Zeichnen eines Bereichs mit einem video                                                 |[MediaElement](https://msdn.microsoft.com/library/windows/apps/mt187272.aspx)                                                                                                  |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Medien interop
|Zeichnen eines Bereichs mit benutzerdefinierten 2D-Zeichnung                                       |[CanvasControl](http://microsoft.github.io/Win2D/html/T_Microsoft_Graphics_Canvas_UI_Xaml_CanvasControl.htm) von Win2D                                                                                                 |[CompositionSurfaceBrush](https://msdn.microsoft.com/library/windows/apps/Mt589415) mit Win2D-interop
|Zeichnen eines Bereichs mit nicht animierte Maske                                       |Verwenden Sie XAML- [Shapes](https://docs.microsoft.com/windows/uwp/graphics/drawing-shapes) , um eine Maske definieren   |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit eine animierte Maske                                        |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)                                                                                           |[CompositionMaskBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionMaskBrush)
|Zeichnen eines Bereichs mit einer animierten Filtereffekt                               |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)                                                                                         |[CompositionEffectBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush)
|Zeichnen eines Bereichs mit einem Hintergrundpixel angewendetem Effekt        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)                                                                                        |[CompositionBackdropBrush](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionBackdropBrush)

## <a name="related-topics"></a>Verwandte Themen

[Komposition systemeigenen DirectX und Direct2D Interop mit BeginDraw und EndDraw](composition-native-interop.md)

[XAML-Pinsel Interop mit XamlCompositionBrushBase](/windows/uwp/design/style/brushes#xamlcompositionbrushbase)
