---
ms.assetid: f1297b7d-1a10-52ae-dd84-6d1ad2ae2fe6
title: Visuelle Kompositionselemente
description: Visuelle Kompositionselemente bilden die visuelle Struktur, die die Grundlage für alle anderen Features der Composition-API bildet und von diesen verwendet wird. Die API ermöglicht es Entwicklern, visuelle Objekte zu definieren und zu erstellen, die jeweils für einen einzelnen Knoten in einer visuellen Struktur stehen.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6b1c0b78ca45d98428f38518b337b5889f595c49
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8783604"
---
# <a name="composition-visual"></a><span data-ttu-id="75e4d-105">Visuelle Komposition</span><span class="sxs-lookup"><span data-stu-id="75e4d-105">Composition visual</span></span>

<span data-ttu-id="75e4d-106">Visuelle Kompositionselemente bilden die visuelle Struktur, die die Grundlage für alle anderen Features der Composition-API bildet und von diesen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="75e4d-106">Composition Visuals make up the visual tree structure which all other features of the composition API use and build on.</span></span> <span data-ttu-id="75e4d-107">Die API ermöglicht es Entwicklern, visuelle Objekte zu definieren und zu erstellen, die jeweils für einen einzelnen Knoten in einer visuellen Struktur stehen.</span><span class="sxs-lookup"><span data-stu-id="75e4d-107">The API allows developers to define and create one or many visual objects each representing a single node in a visual tree.</span></span>

## <a name="visuals"></a><span data-ttu-id="75e4d-108">Visuelle Elemente</span><span class="sxs-lookup"><span data-stu-id="75e4d-108">Visuals</span></span>

<span data-ttu-id="75e4d-109">Es gibt drei Arten visueller Elemente, aus denen sich die visuelle Struktur zusammensetzt, sowie eine grundlegende Pinselklasse mit mehreren Unterklassen, die Einfluss auf den Inhalt eines visuellen Elements hat:</span><span class="sxs-lookup"><span data-stu-id="75e4d-109">There are three visual types that make up the visual tree structure plus a base brush class with multiple subclasses that affect the content of a visual:</span></span>

- <span data-ttu-id="75e4d-110">[**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858) – Basisobjekt; umfasst den Großteil der Eigenschaften. Diese werden von anderen visuellen Objekten geerbt.</span><span class="sxs-lookup"><span data-stu-id="75e4d-110">[**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858) – base object, the majority of the properties are here, and inherited by the other Visual objects.</span></span>
- <span data-ttu-id="75e4d-111">[**ContainerVisual**](https://msdn.microsoft.com/library/windows/apps/Dn706810) – Abgeleitet von [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858). Fügt die Fähigkeit zum Erstellen von untergeordneten Elementen hinzu.</span><span class="sxs-lookup"><span data-stu-id="75e4d-111">[**ContainerVisual**](https://msdn.microsoft.com/library/windows/apps/Dn706810) – derives from [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858), and adds the ability to create children.</span></span>
- <span data-ttu-id="75e4d-112">[**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433) – Abgeleitet von [**ContainerVisual**](https://msdn.microsoft.com/library/windows/apps/Dn706810). Bietet zudem die Möglichkeit, einen Pinsel zuzuordnen, sodass das Visual-Element Pixel, einschließlich Bilder, Effekte oder Volltonfarbe, rendern kann.</span><span class="sxs-lookup"><span data-stu-id="75e4d-112">[**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433) – derives from [**ContainerVisual**](https://msdn.microsoft.com/library/windows/apps/Dn706810) and adds the ability to associate a brush so that the Visual can render pixels including images, effects or a solid color.</span></span>

<span data-ttu-id="75e4d-113">Sie können Inhalte und Effekte für SpriteVisuals mit [**CompositionBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589398) und deren Unterklassen, wie [**CompositionColorBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush),[**CompositionSurfaceBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) und [**CompositionEffectBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush), festlegen.</span><span class="sxs-lookup"><span data-stu-id="75e4d-113">You can apply content and effects to SpriteVisuals using the [**CompositionBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589398) and its subclasses including the [**CompositionColorBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionColorBrush), [**CompositionSurfaceBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionSurfaceBrush) and [**CompositionEffectBrush**](https://docs.microsoft.com/uwp/api/Windows.UI.Composition.CompositionEffectBrush).</span></span> <span data-ttu-id="75e4d-114">Weitere Informationen zu Pinseln finden Sie unter [**CompositionBrush-Überblick**](https://docs.microsoft.com/windows/uwp/composition/composition-brushes).</span><span class="sxs-lookup"><span data-stu-id="75e4d-114">To learn more about brushes see our [**CompositionBrush Overview**](https://docs.microsoft.com/windows/uwp/composition/composition-brushes).</span></span>

## <a name="the-compositionvisual-sample"></a><span data-ttu-id="75e4d-115">Das CompositionVisual-Beispiel</span><span class="sxs-lookup"><span data-stu-id="75e4d-115">The CompositionVisual Sample</span></span>

<span data-ttu-id="75e4d-116">Hier betrachten wir einige Codebeispiele für die zuvor aufgeführten drei Arten visueller Elemente.</span><span class="sxs-lookup"><span data-stu-id="75e4d-116">Here, we'll look at some sample code that demonstrates the three different visual types listed previously.</span></span> <span data-ttu-id="75e4d-117">Dieses Beispiel veranschaulicht keine Konzepte wie Animationen oder komplexere Effekte. Es enthält die Bausteine, die alle diese Systeme verwenden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-117">While this sample doesn’t cover concepts like Animations or more complex effects, it contains the building blocks that all of those systems use.</span></span> <span data-ttu-id="75e4d-118">(Den vollständigen Beispielcode finden Sie am Ende dieses Artikels.)</span><span class="sxs-lookup"><span data-stu-id="75e4d-118">(The full sample code is listed at the end of this article.)</span></span>

<span data-ttu-id="75e4d-119">Im Beispiel sehen Sie eine Reihe farbiger Quadrate, die Sie anklicken und über den Bildschirm ziehen können.</span><span class="sxs-lookup"><span data-stu-id="75e4d-119">In the sample are a number of solid color squares that can be clicked on and dragged about the screen.</span></span> <span data-ttu-id="75e4d-120">Durch Klicken auf ein Quadrat gelangt dieses in den Vordergrund, dreht sich um 45Grad und wird während der Bewegung undurchsichtig.</span><span class="sxs-lookup"><span data-stu-id="75e4d-120">When a square is clicked on, it will come to the front, rotate 45 degrees, and become opaque when dragged about.</span></span>

<span data-ttu-id="75e4d-121">Es zeigt einige grundlegenden Konzepte für die Arbeit mit der API, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="75e4d-121">This shows a number of basic concepts for working with the API including:</span></span>

- <span data-ttu-id="75e4d-122">Erstellen eines Kompositors</span><span class="sxs-lookup"><span data-stu-id="75e4d-122">Creating a compositor</span></span>
- <span data-ttu-id="75e4d-123">Erstellen eines SpriteVisual-Elements mit „CompositionColorBrush“</span><span class="sxs-lookup"><span data-stu-id="75e4d-123">Creating a SpriteVisual with a CompositionColorBrush</span></span>
- <span data-ttu-id="75e4d-124">Beschneiden des visuellen Elements</span><span class="sxs-lookup"><span data-stu-id="75e4d-124">Clipping the Visual</span></span>
- <span data-ttu-id="75e4d-125">Drehen des visuellen Elements</span><span class="sxs-lookup"><span data-stu-id="75e4d-125">Rotating the Visual</span></span>
- <span data-ttu-id="75e4d-126">Festlegen der Deckkraft</span><span class="sxs-lookup"><span data-stu-id="75e4d-126">Setting Opacity</span></span>
- <span data-ttu-id="75e4d-127">Ändern der Position des visuellen Elements in der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="75e4d-127">Changing the Visual’s position in the collection.</span></span>

## <a name="creating-a-compositor"></a><span data-ttu-id="75e4d-128">Erstellen eines Kompositors</span><span class="sxs-lookup"><span data-stu-id="75e4d-128">Creating a Compositor</span></span>

<span data-ttu-id="75e4d-129">Es ist einfach, ein neues [**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789)-Objekt zu erstellen und diese für die Verwendung als Factory in einer Variable zu speichern.</span><span class="sxs-lookup"><span data-stu-id="75e4d-129">Creating a [**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789) and storing it in a variable for use as a factory is a simple task.</span></span> <span data-ttu-id="75e4d-130">Der folgende Codeausschnitt veranschaulicht das Erstellen eines neuen **Compositor**-Objekts:</span><span class="sxs-lookup"><span data-stu-id="75e4d-130">The following snippet shows creating a new **Compositor**:</span></span>

```cs
_compositor = new Compositor();
```

## <a name="creating-a-spritevisual-and-colorbrush"></a><span data-ttu-id="75e4d-131">Erstellen eines „SpriteVisual“- und eines „ColorBrush“-Elements</span><span class="sxs-lookup"><span data-stu-id="75e4d-131">Creating a SpriteVisual and ColorBrush</span></span>

<span data-ttu-id="75e4d-132">Mit dem [**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789)-Objekt können Sie auf einfache Weise Objekte erstellen, wenn Sie sie benötigen, wie etwa ein [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433)- und ein [**CompositionColorBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589399)-Element:</span><span class="sxs-lookup"><span data-stu-id="75e4d-132">Using the [**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789) it's easy to create objects whenever you need them, such as a [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433) and a [**CompositionColorBrush**](https://msdn.microsoft.com/library/windows/apps/Mt589399):</span></span>

```cs
var visual = _compositor.CreateSpriteVisual();
visual.Brush = _compositor.CreateColorBrush(Color.FromArgb(0xFF, 0xFF, 0xFF, 0xFF));
```

<span data-ttu-id="75e4d-133">Diese wenigen Zeilen Code veranschaulichen ein leistungsfähiges Konzept: [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433)-Objekte sind das Herzstück des Effektesystems.</span><span class="sxs-lookup"><span data-stu-id="75e4d-133">While this is only a few lines of code, it demonstrates a powerful concept: [**SpriteVisual**](https://msdn.microsoft.com/library/windows/apps/Mt589433) objects are the heart of the effects system.</span></span> <span data-ttu-id="75e4d-134">Das **SpriteVisual**-Element ermöglicht hohe Flexibilität und Interaktion bei der Farb-, Bild- und Effektgestaltung.</span><span class="sxs-lookup"><span data-stu-id="75e4d-134">The **SpriteVisual** allows for great flexibility and interplay in color, image and effect creation.</span></span> <span data-ttu-id="75e4d-135">**SpriteVisual** ist das einzige visuelle Element, das ein 2D-Rechteck mit einem Pinsel füllen kann, in diesem Fall mit einer Volltonfarbe.</span><span class="sxs-lookup"><span data-stu-id="75e4d-135">The **SpriteVisual** is a single visual type that can fill a 2D rectangle with a brush, in this case, a solid color.</span></span>

## <a name="clipping-a-visual"></a><span data-ttu-id="75e4d-136">Beschneiden eines visuellen Elements</span><span class="sxs-lookup"><span data-stu-id="75e4d-136">Clipping a Visual</span></span>

<span data-ttu-id="75e4d-137">[**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789) kann auch zum Beschneiden eines [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858)-Objekts verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-137">The [**Compositor**](https://msdn.microsoft.com/library/windows/apps/Dn706789) can also be used to create clips to a [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858).</span></span> <span data-ttu-id="75e4d-138">Im folgenden Beispiel werden mit [**InsetClip**](https://msdn.microsoft.com/library/windows/apps/Dn706825) die Seiten des visuellen Elements gekürzt:</span><span class="sxs-lookup"><span data-stu-id="75e4d-138">Below is an example from the sample of using the [**InsetClip**](https://msdn.microsoft.com/library/windows/apps/Dn706825) to trim each side of the visual:</span></span>

```cs
var clip = _compositor.CreateInsetClip();
clip.LeftInset = 1.0f;
clip.RightInset = 1.0f;
clip.TopInset = 1.0f;
clip.BottomInset = 1.0f;
_currentVisual.Clip = clip;
```

<span data-ttu-id="75e4d-139">Auf die Eigenschaften von [**InsetClip**](https://msdn.microsoft.com/library/windows/apps/Dn706825) können wie auch auf andere Objekte in der API Animationen angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-139">Like other objects in the API, [**InsetClip**](https://msdn.microsoft.com/library/windows/apps/Dn706825) can have animations applied to its properties.</span></span>

## <a name="span-idrotatingaclipspanspan-idrotatingaclipspanspan-idrotatingaclipspanrotating-a-clip"></a><span data-ttu-id="75e4d-140"><span id="Rotating_a_Clip"></span><span id="rotating_a_clip"></span><span id="ROTATING_A_CLIP"></span>Drehen von Clips</span><span class="sxs-lookup"><span data-stu-id="75e4d-140"><span id="Rotating_a_Clip"></span><span id="rotating_a_clip"></span><span id="ROTATING_A_CLIP"></span>Rotating a Clip</span></span>

<span data-ttu-id="75e4d-141">Ein [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858)-Objekt kann mit einer Drehung transformiert werden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-141">A [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858) can be transformed with a rotation.</span></span> <span data-ttu-id="75e4d-142">Beachten Sie, dass [**RotationAngle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visual.rotationangle) Radianten und Grad unterstützt.</span><span class="sxs-lookup"><span data-stu-id="75e4d-142">Note that [**RotationAngle**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visual.rotationangle) supports both radians and degrees.</span></span> <span data-ttu-id="75e4d-143">Der Standardwert ist „Radianten“. Wie im folgenden Codeausschnitt dargestellt, ist es jedoch ganz einfach, einen Wert in Grad anzugeben:</span><span class="sxs-lookup"><span data-stu-id="75e4d-143">It defaults to radians, but it’s easy to specify degrees as shown in the following snippet:</span></span>

```cs
child.RotationAngleInDegrees = 45.0f;
```

<span data-ttu-id="75e4d-144">Drehung ist nur ein Beispiel für eine Reihe von Transformationskomponenten, die von der API bereitgestellt werden, um diese Aufgaben zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="75e4d-144">Rotation is just one example of a set of transform components provided by the API to make these tasks easier.</span></span> <span data-ttu-id="75e4d-145">Dazu gehören auch Offset, Skalieren, Ausrichtung, Drehachse und eine 4x4-Transformationsmatrix.</span><span class="sxs-lookup"><span data-stu-id="75e4d-145">Others include Offset, Scale, Orientation, RotationAxis, and 4x4 TransformMatrix.</span></span>

## <a name="setting-opacity"></a><span data-ttu-id="75e4d-146">Festlegen der Deckkraft</span><span class="sxs-lookup"><span data-stu-id="75e4d-146">Setting Opacity</span></span>

<span data-ttu-id="75e4d-147">Das Festlegen der Deckkraft eines visuellen Elements ist mit einem Float-Wert unproblematisch.</span><span class="sxs-lookup"><span data-stu-id="75e4d-147">Setting the opacity of a visual is a simple operation using a float value.</span></span> <span data-ttu-id="75e4d-148">In diesem Beispiel haben alle Quadrate anfangs eine Deckkraft von0,8:</span><span class="sxs-lookup"><span data-stu-id="75e4d-148">For example, in the sample all the squares start at .8 opacity:</span></span>

```cs
visual.Opacity = 0.8f;
```

<span data-ttu-id="75e4d-149">Wie die Drehung kann auch die [**Opacity**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visual.opacity)-Eigenschaft animiert werden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-149">Like rotation, the [**Opacity**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visual.opacity) property can be animated.</span></span>

## <a name="changing-the-visuals-position-in-the-collection"></a><span data-ttu-id="75e4d-150">Ändern der Position des visuellen Elements in der Auflistung</span><span class="sxs-lookup"><span data-stu-id="75e4d-150">Changing the Visual's position in the collection</span></span>

<span data-ttu-id="75e4d-151">Die Composition-API ermöglicht es, dass die Position eines visuellen Elements in [**VisualCollection**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection) auf vielfältige Weise geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="75e4d-151">The Composition API allows for a Visual's position in a [**VisualCollection**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection) to be changed in a number of ways.</span></span> <span data-ttu-id="75e4d-152">Es kann mit [**InsertAbove**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertabove) über einem anderen visuellen Element und mit [**InsertBelow**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertbelow) darunter platziert werden. An die oberste Position wird es mit [**InsertAtTop**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertattop) und an die unterste mit [**InsertAtBottom**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertatbottom) verschoben.</span><span class="sxs-lookup"><span data-stu-id="75e4d-152">It can be placed above another Visual with [**InsertAbove**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertabove), placed below with [**InsertBelow**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertbelow), moved to the top with [**InsertAtTop**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertattop), or the bottom with [**InsertAtBottom**](https://msdn.microsoft.com/library/windows/apps/windows.ui.composition.visualcollection.insertatbottom).</span></span>

<span data-ttu-id="75e4d-153">In dem Beispiel wird ein [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858)-Objekt, auf das geklickt wurde, oben platziert:</span><span class="sxs-lookup"><span data-stu-id="75e4d-153">In the sample, a [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858) that has been clicked is sorted to the top:</span></span>

```cs
parent.Children.InsertAtTop(_currentVisual);
```

## <a name="full-example"></a><span data-ttu-id="75e4d-154">Vollständiges Beispiel</span><span class="sxs-lookup"><span data-stu-id="75e4d-154">Full Example</span></span>

<span data-ttu-id="75e4d-155">Im vollständigen Beispiel werden alle oben beschriebenen Konzepte zusammen verwendet, um eine einfache Struktur von [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858)-Objekten zu erstellen und vorzuführen. Die Deckkraft wird ohne Verwendung von XAML, WWA oder DirectX geändert.</span><span class="sxs-lookup"><span data-stu-id="75e4d-155">In the full sample, all of the concepts above are used together to construct and walk a simple tree of [**Visual**](https://msdn.microsoft.com/library/windows/apps/Dn706858) objects to change opacity without using XAML, WWA, or DirectX.</span></span> <span data-ttu-id="75e4d-156">Dieses Beispiel zeigt, wie untergeordnete **Visual**-Objekte erstellt und hinzugefügt und Eigenschaften geändert werden.</span><span class="sxs-lookup"><span data-stu-id="75e4d-156">This sample shows how child **Visual** objects are created and added and how properties are changed.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Numerics;
using System.Text;
using System.Threading.Tasks;
using Windows.ApplicationModel.Core;
using Windows.Foundation;
using Windows.UI;
using Windows.UI.Composition;
using Windows.UI.Core;

namespace compositionvisual
{
    class VisualProperties : IFrameworkView
    {
        //------------------------------------------------------------------------------
        //
        // VisualProperties.Initialize
        //
        // This method is called during startup to associate the IFrameworkView with the
        // CoreApplicationView.
        //
        //------------------------------------------------------------------------------

        void IFrameworkView.Initialize(CoreApplicationView view)
        {
            _view = view;
            _random = new Random();
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.SetWindow
        //
        // This method is called when the CoreApplication has created a new CoreWindow,
        // allowing the application to configure the window and start producing content
        // to display.
        //
        //------------------------------------------------------------------------------

        void IFrameworkView.SetWindow(CoreWindow window)
        {
            _window = window;
            InitNewComposition();
            _window.PointerPressed += OnPointerPressed;
            _window.PointerMoved += OnPointerMoved;
            _window.PointerReleased += OnPointerReleased;
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.OnPointerPressed
        //
        // This method is called when the user touches the screen, taps it with a stylus
        // or clicks the mouse.
        //
        //------------------------------------------------------------------------------

        void OnPointerPressed(CoreWindow window, PointerEventArgs args)
        {
            Point position = args.CurrentPoint.Position;

            //
            // Walk our list of visuals to determine who, if anybody, was selected
            //
            foreach (var child in _root.Children)
            {
                //
                // Did we hit this child?
                //
                Vector3 offset = child.Offset;
                Vector2 size = child.Size;

                if ((position.X >= offset.X) &&
                    (position.X < offset.X + size.X) &&
                    (position.Y >= offset.Y) &&
                    (position.Y < offset.Y + size.Y))
                {
                    //
                    // This child was hit. Since the children are stored back to front,
                    // the last one hit is the front-most one so it wins
                    //
                    _currentVisual = child as ContainerVisual;
                    _offsetBias = new Vector2((float)(offset.X - position.X),
                                              (float)(offset.Y - position.Y));
                }
            }

            //
            // If a visual was hit, bring it to the front of the Z order
            //
            if (_currentVisual != null)
            {
                ContainerVisual parent = _currentVisual.Parent as ContainerVisual;
                parent.Children.Remove(_currentVisual);
                parent.Children.InsertAtTop(_currentVisual);
            }
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.OnPointerMoved
        //
        // This method is called when the user moves their finger, stylus or mouse with
        // a button pressed over the screen.
        //
        //------------------------------------------------------------------------------

        void OnPointerMoved(CoreWindow window, PointerEventArgs args)
        {
            //
            // If a visual is selected, drag it with the pointer position and
            // make it opaque while we drag it
            //
            if (_currentVisual != null)
            {
                //
                // Set up the properties of the visual the first time it is
                // dragged. This will last for the duration of the drag
                //
                if (!_dragging)
                {
                    _currentVisual.Opacity = 1.0f;

                    //
                    // Transform the first child of the current visual so that
                    // the image is rotated
                    //
                    foreach (var child in _currentVisual.Children)
                    {
                        child.RotationAngleInDegrees = 45.0f;
                        child.CenterPoint = new Vector3(_currentVisual.Size.X / 2, _currentVisual.Size.Y / 2, 0);
                        break;
                    }

                    //
                    // Clip the visual to its original layout rect by using an inset
                    // clip with a one-pixel margin all around
                    //
                    var clip = _compositor.CreateInsetClip();
                    clip.LeftInset = 1.0f;
                    clip.RightInset = 1.0f;
                    clip.TopInset = 1.0f;
                    clip.BottomInset = 1.0f;
                    _currentVisual.Clip = clip;

                    _dragging = true;
                }

                Point position = args.CurrentPoint.Position;
                _currentVisual.Offset = new Vector3((float)(position.X + _offsetBias.X),
                                                    (float)(position.Y + _offsetBias.Y),
                                                    0.0f);
            }
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.OnPointerReleased
        //
        // This method is called when the user lifts their finger or stylus from the
        // screen, or lifts the mouse button.
        //
        //------------------------------------------------------------------------------

        void OnPointerReleased(CoreWindow window, PointerEventArgs args)
        {
            //
            // If a visual was selected, make it transparent again when it is
            // released and restore the transform and clip
            //
            if (_currentVisual != null)
            {
                if (_dragging)
                {
                    //
                    // Remove the transform from the first child
                    //
                    foreach (var child in _currentVisual.Children)
                    {
                        child.RotationAngle = 0.0f;
                        child.CenterPoint = new Vector3(0.0f, 0.0f, 0.0f);
                        break;
                    }

                    _currentVisual.Opacity = 0.8f;
                    _currentVisual.Clip = null;
                    _dragging = false;
                }

                _currentVisual = null;
            }
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.Load
        //
        // This method is called when a specific page is being loaded in the
        // application.  It is not used for this application.
        //
        //------------------------------------------------------------------------------

        void IFrameworkView.Load(string unused)
        {

        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.Run
        //
        // This method is called by CoreApplication.Run() to actually run the
        // dispatcher's message pump.
        //
        //------------------------------------------------------------------------------

        void IFrameworkView.Run()
        {
            _window.Activate();
            _window.Dispatcher.ProcessEvents(CoreProcessEventsOption.ProcessUntilQuit);
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.Uninitialize
        //
        // This method is called during shutdown to disconnect the CoreApplicationView,
        // and CoreWindow from the IFrameworkView.
        //
        //------------------------------------------------------------------------------

        void IFrameworkView.Uninitialize()
        {
            _window = null;
            _view = null;
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.InitNewComposition
        //
        // This method is called by SetWindow(), where we initialize Composition after
        // the CoreWindow has been created.
        //
        //------------------------------------------------------------------------------

        void InitNewComposition()
        {
            //
            // Set up Windows.UI.Composition Compositor, root ContainerVisual, and associate with
            // the CoreWindow.
            //

            _compositor = new Compositor();

            _root = _compositor.CreateContainerVisual();



            _compositionTarget = _compositor.CreateTargetForCurrentView();
            _compositionTarget.Root = _root;

            //
            // Create a few visuals for our window
            //
            for (int index = 0; index < 20; index++)
            {
                _root.Children.InsertAtTop(CreateChildElement());
            }
        }

        //------------------------------------------------------------------------------
        //
        // VisualProperties.CreateChildElement
        //
        // Creates a small sub-tree to represent a visible element in our application.
        //
        //------------------------------------------------------------------------------

        Visual CreateChildElement()
        {
            //
            // Each element consists of three visuals, which produce the appearance
            // of a framed rectangle
            //
            var element = _compositor.CreateContainerVisual();
            element.Size = new Vector2(100.0f, 100.0f);

            //
            // Position this visual randomly within our window
            //
            element.Offset = new Vector3((float)(_random.NextDouble() * 400), (float)(_random.NextDouble() * 400), 0.0f);

            //
            // The outer rectangle is always white
            //
            //Note to preview API users - SpriteVisual and Color Brush replace SolidColorVisual
            //for example instead of doing
            //var visual = _compositor.CreateSolidColorVisual() and
            //visual.Color = Color.FromArgb(0xFF, 0xFF, 0xFF, 0xFF);
            //we now use the below

            var visual = _compositor.CreateSpriteVisual();
            element.Children.InsertAtTop(visual);
            visual.Brush = _compositor.CreateColorBrush(Color.FromArgb(0xFF, 0xFF, 0xFF, 0xFF));
            visual.Size = new Vector2(100.0f, 100.0f);

            //
            // The inner rectangle is inset from the outer by three pixels all around
            //
            var child = _compositor.CreateSpriteVisual();
            visual.Children.InsertAtTop(child);
            child.Offset = new Vector3(3.0f, 3.0f, 0.0f);
            child.Size = new Vector2(94.0f, 94.0f);

            //
            // Pick a random color for every rectangle
            //
            byte red = (byte)(0xFF * (0.2f + (_random.NextDouble() / 0.8f)));
            byte green = (byte)(0xFF * (0.2f + (_random.NextDouble() / 0.8f)));
            byte blue = (byte)(0xFF * (0.2f + (_random.NextDouble() / 0.8f)));
            child.Brush = _compositor.CreateColorBrush(Color.FromArgb(0xFF, red, green, blue));

            //
            // Make the subtree root visual partially transparent. This will cause each visual in the subtree
            // to render partially transparent, since a visual's opacity is multiplied with its parent's
            // opacity
            //
            element.Opacity = 0.8f;

            return element;
        }

        // CoreWindow / CoreApplicationView
        private CoreWindow _window;
        private CoreApplicationView _view;

        // Windows.UI.Composition
        private Compositor _compositor;
        private CompositionTarget _compositionTarget;
        private ContainerVisual _root;
        private ContainerVisual _currentVisual;
        private Vector2 _offsetBias;
        private bool _dragging;

        // Helpers
        private Random _random;
    }


    public sealed class VisualPropertiesFactory : IFrameworkViewSource
    {
        //------------------------------------------------------------------------------
        //
        // VisualPropertiesFactory.CreateView
        //
        // This method is called by CoreApplication to provide a new IFrameworkView for
        // a CoreWindow that is being created.
        //
        //------------------------------------------------------------------------------

        IFrameworkView IFrameworkViewSource.CreateView()
        {
            return new VisualProperties();
        }


        //------------------------------------------------------------------------------
        //
        // main
        //
        //------------------------------------------------------------------------------

        static int Main(string[] args)
        {
            CoreApplication.Run(new VisualPropertiesFactory());

            return 0;
        }
    }
}
```
