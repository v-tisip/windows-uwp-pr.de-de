---
author: Jwmsft
ms.assetid: 54CC0BD4-1961-44D7-AB40-6E8B58E42D65
title: Zeichnen von Formen
description: Erfahren Sie, wie Sie Formen wie Ellipsen, Rechtecke, Polygone und Pfade zeichnen. Mithilfe der Klasse Path visualisieren Sie eine ziemlich komplexe vektorbasierte Zeichnungssprache in einer XAML-Benutzeroberfläche. Beispielsweise können Sie auf diese Weise Bézierkurven zeichnen.
ms.author: jimwalk
ms.date: 11/16/2017
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 984653ad20fc40035528ab7e32b904e64d6ff8c5
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "5753857"
---
# <a name="draw-shapes"></a><span data-ttu-id="75a92-105">Zeichnen von Formen</span><span class="sxs-lookup"><span data-stu-id="75a92-105">Draw shapes</span></span>

<span data-ttu-id="75a92-106">Erfahren Sie, wie Sie Formen wie Ellipsen, Rechtecke, Polygone und Pfade zeichnen.</span><span class="sxs-lookup"><span data-stu-id="75a92-106">Learn how to draw shapes, such as ellipses, rectangles, polygons, and paths.</span></span> <span data-ttu-id="75a92-107">Mithilfe der Klasse [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path) visualisieren Sie eine ziemlich komplexe vektorbasierte Zeichnungssprache in einer XAML-Benutzeroberfläche. Beispielsweise können Sie auf diese Weise Bézierkurven zeichnen.</span><span class="sxs-lookup"><span data-stu-id="75a92-107">The [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path) class is the way to visualize a fairly complex vector-based drawing language in a XAML UI; for example, you can draw Bezier curves.</span></span>

> <span data-ttu-id="75a92-108">**Wichtige APIs**: [Path-Klasse](/uwp/api/Windows.UI.Xaml.Shapes.Path), [Windows.UI.Xaml.Shapes namespace](/uwp/api/Windows.UI.Xaml.Shapes), [Windows.UI.Xaml.Media namespace](/uwp/api/Windows.UI.Xaml.Media)</span><span class="sxs-lookup"><span data-stu-id="75a92-108">**Important APIs**: [Path class](/uwp/api/Windows.UI.Xaml.Shapes.Path), [Windows.UI.Xaml.Shapes namespace](/uwp/api/Windows.UI.Xaml.Shapes), [Windows.UI.Xaml.Media namespace](/uwp/api/Windows.UI.Xaml.Media)</span></span>


<span data-ttu-id="75a92-109">Zwei Sätze von Klassen definieren einen Bereich in der XAML-Benutzeroberfläche: [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape)-Klassen und [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry)-Klassen.</span><span class="sxs-lookup"><span data-stu-id="75a92-109">Two sets of classes define a region of space in XAML UI: [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) classes and [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry) classes.</span></span> <span data-ttu-id="75a92-110">Der Hauptunterschied zwischen diesen Klassen besteht darin, dass einer **Shape**-Klasse ein Pinsel zugeordnet ist und diese auf dem Bildschirm gerendert werden kann, während eine **Geometry**-Klasse einfach einen Bereich definiert und nur gerendert wird, wenn sie Informationen zu einer anderen UI-Eigenschaft beiträgt.</span><span class="sxs-lookup"><span data-stu-id="75a92-110">The main difference between these classes is that a **Shape** has a brush associated with it and can be rendered to the screen, and a **Geometry** simply defines a region of space and is not rendered unless it helps contribute information to another UI property.</span></span> <span data-ttu-id="75a92-111">Sie können sich eine **Shape**-Klasse als [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911) vorstellen, dessen Umrandung durch eine **Geometry**-Klasse definiert ist.</span><span class="sxs-lookup"><span data-stu-id="75a92-111">You can think of a **Shape** as a [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911) with its boundary defined by a **Geometry**.</span></span> <span data-ttu-id="75a92-112">In diesem Thema werden hauptsächlich die **Shape**-Klassen behandelt.</span><span class="sxs-lookup"><span data-stu-id="75a92-112">This topic covers mainly the **Shape** classes.</span></span>

<span data-ttu-id="75a92-113">Die [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape)-Klassen sind [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line), [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse), [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon), [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) und [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span><span class="sxs-lookup"><span data-stu-id="75a92-113">The [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) classes are [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line), [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse), [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon), [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline), and [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span></span> <span data-ttu-id="75a92-114">**Path** ist interessant, da Sie mit dieser Klasse beliebige Geometrien definieren können, und die Klasse [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry) stellt eine Möglichkeit zum Definieren der Teile eines **Path** dar.</span><span class="sxs-lookup"><span data-stu-id="75a92-114">**Path** is interesting because it can define an arbitrary geometry, and the [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry) class is involved here because that's one way to define the parts of a **Path**.</span></span>

## <a name="fill-and-stroke-for-shapes"></a><span data-ttu-id="75a92-115">Füllungen und Striche für Formen</span><span class="sxs-lookup"><span data-stu-id="75a92-115">Fill and Stroke for shapes</span></span>

<span data-ttu-id="75a92-116">Damit eine [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape)-Klasse auf dem App-Canvas gerendert wird, müssen Sie ihr einen [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush) zuweisen.</span><span class="sxs-lookup"><span data-stu-id="75a92-116">For a [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) to render to the app canvas, you must associate a [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush) with it.</span></span> <span data-ttu-id="75a92-117">Legen Sie die [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill)-Eigenschaft der **Shape**-Klasse auf den gewünschten **Brush** fest.</span><span class="sxs-lookup"><span data-stu-id="75a92-117">Set the [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) property of the **Shape** to the **Brush** you want.</span></span> <span data-ttu-id="75a92-118">Weitere Informationen zu Pinseln finden Sie unter [Verwenden von Pinseln](../style/brushes.md).</span><span class="sxs-lookup"><span data-stu-id="75a92-118">For more info about brushes, see [Using brushes](../style/brushes.md).</span></span>

<span data-ttu-id="75a92-119">Eine [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape)-Klasse kann auch einen [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) aufweisen. Dies ist eine Linie, die um den Rand der Form gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="75a92-119">A [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) can also have a [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke), which is a line that is drawn around the shape's perimeter.</span></span> <span data-ttu-id="75a92-120">Ein **Stroke** erfordert auch einen [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush). Dieser definiert die Darstellung und sollte einen Wert ungleich Null für [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness) aufweisen.</span><span class="sxs-lookup"><span data-stu-id="75a92-120">A **Stroke** also requires a [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush) that defines its appearance, and should have a non-zero value for [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness).</span></span> <span data-ttu-id="75a92-121">**StrokeThickness** ist eine Eigenschaft, die die Stärke des Rands um die Form definiert.</span><span class="sxs-lookup"><span data-stu-id="75a92-121">**StrokeThickness** is a property that defines the perimeter's thickness around the shape edge.</span></span> <span data-ttu-id="75a92-122">Wenn Sie keinen **Brush**-Wert für **Stroke** angeben oder **StrokeThickness** auf 0 festlegen, wird kein Rahmen um die Form gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="75a92-122">If you don't specify a **Brush** value for **Stroke**, or if you set **StrokeThickness** to 0, then the border around the shape is not drawn.</span></span>

## <a name="ellipse"></a><span data-ttu-id="75a92-123">Ellipse</span><span class="sxs-lookup"><span data-stu-id="75a92-123">Ellipse</span></span>

<span data-ttu-id="75a92-124">Eine [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) ist eine Form mit einem kurvenförmigen Rand.</span><span class="sxs-lookup"><span data-stu-id="75a92-124">An [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) is a shape with a curved perimeter.</span></span> <span data-ttu-id="75a92-125">Zum Erstellen einer einfachen **Ellipse** geben Sie [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) und einen [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush) für [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) an.</span><span class="sxs-lookup"><span data-stu-id="75a92-125">To create a basic **Ellipse**, specify a [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height), and a [**Brush**](/uwp/api/Windows.UI.Xaml.Media.Brush) for the [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill).</span></span>

<span data-ttu-id="75a92-126">Im nächsten Beispiel wird eine [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) mit einer [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) von 200 und einer [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) von 200 erstellt, die die Farbe [**SteelBlue**](https://msdn.microsoft.com/library/windows/apps/Hh748056) für [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) als [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) verwendet.</span><span class="sxs-lookup"><span data-stu-id="75a92-126">The next example creates an [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) with a [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) of 200 and a [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) of 200, and uses a [**SteelBlue**](https://msdn.microsoft.com/library/windows/apps/Hh748056) colored [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) as its [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill).</span></span>

```xaml
<Ellipse Fill="SteelBlue" Height="200" Width="200" />
```

```csharp
var ellipse1 = new Ellipse();
ellipse1.Fill = new SolidColorBrush(Windows.UI.Colors.SteelBlue);
ellipse1.Width = 200;
ellipse1.Height = 200;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(ellipse1);
```

<span data-ttu-id="75a92-127">Dies ist die gerenderte [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse).</span><span class="sxs-lookup"><span data-stu-id="75a92-127">Here's the rendered [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse).</span></span>

![Eine gerenderte Ellipse](images/shapes-ellipse.jpg)

<span data-ttu-id="75a92-129">In diesem Fall ist die [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) das, was die meisten Menschen als einen Kreis bezeichnen würden. So werden Kreisformen in XAML definiert: Sie verwenden eine **Ellipse** mit gleicher [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) und [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height).</span><span class="sxs-lookup"><span data-stu-id="75a92-129">In this case the [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) is what most people would consider a circle, but that's how you declare a circle shape in XAML: use an **Ellipse** with equal [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) and [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height).</span></span>

<span data-ttu-id="75a92-130">Wenn eine [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) in einem UI-Layout positioniert wird, wird davon ausgegangen, dass ihre Größe einem Rechteck dieser [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) und [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) entspricht. Der Bereich außerhalb des Rands weist kein Rendering auf, gehört jedoch weiterhin zur Größe des Layoutschlitzes.</span><span class="sxs-lookup"><span data-stu-id="75a92-130">When an [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) is positioned in a UI layout, its size is assumed to be the same as a rectangle with that [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) and [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height); the area outside the perimeter does not have rendering but still is part of its layout slot size.</span></span>

<span data-ttu-id="75a92-131">Eine Gruppe von 6 [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse)-Elementen ist Teil der Steuerelementvorlage für das [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/BR227538)-Steuerelement. 2konzentrische **Ellipse**-Elemente sind Teil eines [**RadioButton**](https://msdn.microsoft.com/library/windows/apps/BR227544).</span><span class="sxs-lookup"><span data-stu-id="75a92-131">A set of 6 [**Ellipse**](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) elements are part of the control template for the [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/BR227538) control, and 2 concentric **Ellipse** elements are part of a [**RadioButton**](https://msdn.microsoft.com/library/windows/apps/BR227544).</span></span>

## <a name="span-idrectanglespanspan-idrectanglespanspan-idrectanglespanrectangle"></a><span data-ttu-id="75a92-132"><span id="Rectangle"></span><span id="rectangle"></span><span id="RECTANGLE"></span>Rectangle</span><span class="sxs-lookup"><span data-stu-id="75a92-132"><span id="Rectangle"></span><span id="rectangle"></span><span id="RECTANGLE"></span>Rectangle</span></span>

<span data-ttu-id="75a92-133">Ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) ist eine vierseitige Form, bei der die gegenüberliegenden Seiten gleich sind.</span><span class="sxs-lookup"><span data-stu-id="75a92-133">A [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) is a four-sided shape with its opposite sides being equal.</span></span> <span data-ttu-id="75a92-134">Um ein einfaches **Rectangle** zu erstellen, geben Sie eine [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), eine [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) und einen Wert für [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) an.</span><span class="sxs-lookup"><span data-stu-id="75a92-134">To create a basic **Rectangle**, specify a [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width), a [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height), and a [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill).</span></span>

<span data-ttu-id="75a92-135">Sie können die Ecken eines [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) abrunden.</span><span class="sxs-lookup"><span data-stu-id="75a92-135">You can round the corners of a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle).</span></span> <span data-ttu-id="75a92-136">Um abgerundete Ecken zu erstellen, geben Sie einen Wert für die Eigenschaften [**RadiusX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusx.aspx) und [**RadiusY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusy) an.</span><span class="sxs-lookup"><span data-stu-id="75a92-136">To create rounded corners, specify a value for the [**RadiusX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusx.aspx) and [**RadiusY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusy) properties.</span></span> <span data-ttu-id="75a92-137">Diese Eigenschaften geben die x-Achse und die y-Achse einer Ellipse an, die die Kurven der Ecken angibt.</span><span class="sxs-lookup"><span data-stu-id="75a92-137">These properties specify the x-axis and y-axis of an ellipse that defines the curve of the corners.</span></span> <span data-ttu-id="75a92-138">Der zulässige Maximalwert für **RadiusX** ist [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) geteilt durch zwei. Der zulässige Maximalwert für **RadiusY** ist [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) geteilt durch zwei.</span><span class="sxs-lookup"><span data-stu-id="75a92-138">The maximum allowed value of **RadiusX** is the [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) divided by two and the maximum allowed value of **RadiusY** is the [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) divided by two.</span></span>

<span data-ttu-id="75a92-139">Im nächsten Beispiel wird ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) mit einer [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) von 200 und einer [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) von100 erstellt.</span><span class="sxs-lookup"><span data-stu-id="75a92-139">The next example creates a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) with a [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) of 200 and a [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) of 100.</span></span> <span data-ttu-id="75a92-140">Es verwendet den Wert [**Blue**](https://msdn.microsoft.com/library/windows/apps/Hh747837) von [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) als [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) und den Wert [**Black**](https://msdn.microsoft.com/library/windows/apps/Hh747833) von **SolidColorBrush** als [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke).</span><span class="sxs-lookup"><span data-stu-id="75a92-140">It uses a [**Blue**](https://msdn.microsoft.com/library/windows/apps/Hh747837) value of [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) for its [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) and a [**Black**](https://msdn.microsoft.com/library/windows/apps/Hh747833) value of **SolidColorBrush** for its [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke).</span></span> <span data-ttu-id="75a92-141">Die [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness) wird als 3 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="75a92-141">We set the [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness) to 3.</span></span> <span data-ttu-id="75a92-142">Die [**RadiusX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusx.aspx)-Eigenschaft wird auf 50, und die [**RadiusY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusy)-Eigenschaft wird auf 10 festgelegt. Damit erhält das **Rectangle** abgerundete Ecken.</span><span class="sxs-lookup"><span data-stu-id="75a92-142">We set the [**RadiusX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusx.aspx) property to 50 and the [**RadiusY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.radiusy) property to 10, which gives the **Rectangle** rounded corners.</span></span>

```xaml
<Rectangle Fill="Blue"
           Width="200"
           Height="100"
           Stroke="Black"
           StrokeThickness="3"
           RadiusX="50"
           RadiusY="10" />
```

```csharp
var rectangle1 = new Rectangle();
rectangle1.Fill = new SolidColorBrush(Windows.UI.Colors.Blue);
rectangle1.Width = 200;
rectangle1.Height = 100;
rectangle1.Stroke = new SolidColorBrush(Windows.UI.Colors.Black);
rectangle1.StrokeThickness = 3;
rectangle1.RadiusX = 50;
rectangle1.RadiusY = 10;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(rectangle1);
```

<span data-ttu-id="75a92-143">Hier die gerenderte [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="75a92-143">Here's the rendered [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle).</span></span>

![Ein gerendertes Rechteck](images/shapes-rectangle.jpg)

<span data-ttu-id="75a92-145">**Tipp:** es gibt einige Szenarien für UI-Definitionen anstelle eines [**Rechtecks**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), einen [**Rahmen**](https://msdn.microsoft.com/library/windows/apps/BR209250) möglicherweise besser geeignet.</span><span class="sxs-lookup"><span data-stu-id="75a92-145">**Tip**There are some scenarios for UI definitions where instead of using a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), a [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250) might be more appropriate.</span></span> <span data-ttu-id="75a92-146">Wenn Sie eine rechteckige Form um anderen Inhalt zeichnen möchten, ist **Border** u.U. besser geeignet. Rahmen können untergeordnete Elemente enthalten, und ihre Größe passt sich automatisch an den Inhalt an. Dagegen sind die Breite und Höhe von **Rectangle**-Elementen auf feste Werte festgelegt.</span><span class="sxs-lookup"><span data-stu-id="75a92-146">If your intention is to create a rectangle shape around other content, it might be better to use **Border** because it can have child content and will automatically size around that content, rather than using the fixed dimensions for height and width like **Rectangle** does.</span></span> <span data-ttu-id="75a92-147">Die Ecken von **Border** können durch Festlegen der [**CornerRadius**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.border.cornerradius)-Eigenschaft auch abgerundet werden.</span><span class="sxs-lookup"><span data-stu-id="75a92-147">A **Border** also has the option of having rounded corners if you set the [**CornerRadius**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.border.cornerradius) property.</span></span>

<span data-ttu-id="75a92-148">Andererseits ist [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) wahrscheinlich eine bessere Wahl für die Steuerelementkomposition.</span><span class="sxs-lookup"><span data-stu-id="75a92-148">On the other hand, a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) is probably a better choice for control composition.</span></span> <span data-ttu-id="75a92-149">Eine **Rectangle**-Form wird in vielen Steuerelementvorlagen verwendet, da sie als FocusVisual-Teil für fokussierbare Steuerelemente verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="75a92-149">A **Rectangle** shape is seen in many control templates because it's used as a "FocusVisual" part for focusable controls.</span></span> <span data-ttu-id="75a92-150">Befindet sich das Steuerelement in einem fokussierten Ansichtszustand, wird dieses Rechteck sichtbar gemacht; in anderen Zuständen ist es ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="75a92-150">Whenever the control is in a "Focused" visual state, this rectangle is made visible, in other states it's hidden.</span></span>

## <a name="polygon"></a><span data-ttu-id="75a92-151">Polygon</span><span class="sxs-lookup"><span data-stu-id="75a92-151">Polygon</span></span>

<span data-ttu-id="75a92-152">Ein [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) ist eine Form, deren Grenze durch eine beliebige Anzahl von Punkten angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="75a92-152">A [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) is a shape with a boundary defined by an arbitrary number of points.</span></span> <span data-ttu-id="75a92-153">Die Grenze wir erstellt, indem eine Linie von einem Punkt zum nächsten gezeichnet wird, bis der letzte Punkt wieder mit dem ersten abschließt.</span><span class="sxs-lookup"><span data-stu-id="75a92-153">The boundary is created by connecting a line from one point to the next, with the last point connected to the first point.</span></span> <span data-ttu-id="75a92-154">Die [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polygon.points.aspx)-Eigenschaft definiert die Sammlung von Punkten, die zusammen die Grenze ergeben.</span><span class="sxs-lookup"><span data-stu-id="75a92-154">The [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polygon.points.aspx) property defines the collection of points that make up the boundary.</span></span> <span data-ttu-id="75a92-155">In XAML definieren Sie die Punkte mit einer durch Trennzeichen getrennten Liste.</span><span class="sxs-lookup"><span data-stu-id="75a92-155">In XAML, you define the points with a comma-separated list.</span></span> <span data-ttu-id="75a92-156">Verwenden Sie im CodeBehind eine [**PointCollection**](https://msdn.microsoft.com/library/windows/apps/BR210220), um die Punkte zu definieren, und fügen Sie der Sammlung jeden einzelnen Punkt als [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870)-Wert hinzu.</span><span class="sxs-lookup"><span data-stu-id="75a92-156">In code-behind you use a [**PointCollection**](https://msdn.microsoft.com/library/windows/apps/BR210220) to define the points and you add each individual point as a [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870) value to the collection.</span></span>

<span data-ttu-id="75a92-157">Die einzelnen Punkte müssen nicht explizit so deklariert werden, dass der Anfangs- und der Endpunkt als derselbe [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870)-Wert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="75a92-157">You don't need to explicitly declare the points such that the start point and end point are both specified as the same [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870) value.</span></span> <span data-ttu-id="75a92-158">Die Renderinglogik für ein [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) geht davon aus, dass Sie eine geschlossene Form definieren, und verbindet den Anfangspunkt implizit mit dem Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="75a92-158">The rendering logic for a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) assumes that you are defining a closed shape and will connect the end point to the start point implicitly.</span></span>

<span data-ttu-id="75a92-159">Im nächsten Beispiel wird ein [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) mit 4 Punkten bei `(10,200)`, `(60,140)`, `(130,140)`und `(180,200)` erstellt.</span><span class="sxs-lookup"><span data-stu-id="75a92-159">The next example creates a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) with 4 points set to `(10,200)`, `(60,140)`, `(130,140)`, and `(180,200)`.</span></span> <span data-ttu-id="75a92-160">Für [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) wird der [**LightBlue**](https://msdn.microsoft.com/library/windows/apps/Hh747960)-Wert [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) verwendet. Da kein [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke)-Wert vorhanden ist, wird keine Umrandung erstellt.</span><span class="sxs-lookup"><span data-stu-id="75a92-160">It uses a [**LightBlue**](https://msdn.microsoft.com/library/windows/apps/Hh747960) value of [**SolidColorBrush**](https://msdn.microsoft.com/library/windows/apps/BR242962) for its [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill), and has no value for [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) so it has no perimeter outline.</span></span>

```xaml
<Polygon Fill="LightBlue"
         Points="10,200,60,140,130,140,180,200" />
```

```csharp
var polygon1 = new Polygon();
polygon1.Fill = new SolidColorBrush(Windows.UI.Colors.LightBlue);

var points = new PointCollection();
points.Add(new Windows.Foundation.Point(10, 200));
points.Add(new Windows.Foundation.Point(60, 140));
points.Add(new Windows.Foundation.Point(130, 140));
points.Add(new Windows.Foundation.Point(180, 200));
polygon1.Points = points;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(polygon1);
```

<span data-ttu-id="75a92-161">Dies ist das gerenderte [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon).</span><span class="sxs-lookup"><span data-stu-id="75a92-161">Here's the rendered [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon).</span></span>

![Ein gerendertes Polygon](images/shapes-polygon.jpg)

<span data-ttu-id="75a92-163">**Tipp:** Wert eines [**Punktes**](https://msdn.microsoft.com/library/windows/apps/BR225870) wird häufig in XAML als Typ für andere Szenarien als das Deklarieren der Scheitelpunkte von Formen verwendet.</span><span class="sxs-lookup"><span data-stu-id="75a92-163">**Tip**A [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870) value is often used as a type in XAML for scenarios other than declaring the vertices of shapes.</span></span> <span data-ttu-id="75a92-164">Ein **Point** ist beispielsweise Teil der Ereignisdaten für Fingereingabeereignisse, damit Sie ermitteln können, wo genau in Koordinatenbereich die Fingereingabeaktion stattgefunden hat.</span><span class="sxs-lookup"><span data-stu-id="75a92-164">For example, a **Point** is part of the event data for touch events, so you can know exactly where in a coordinate space the touch action occurred.</span></span> <span data-ttu-id="75a92-165">Weitere Informationen zu **Point** und dessen Verwendung in XAML oder Code finden Sie in der API-Referenz für [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870).</span><span class="sxs-lookup"><span data-stu-id="75a92-165">For more info about **Point** and how to use it in XAML or code, see the API reference topic for [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870).</span></span>

## <a name="line"></a><span data-ttu-id="75a92-166">Linie</span><span class="sxs-lookup"><span data-stu-id="75a92-166">Line</span></span>

<span data-ttu-id="75a92-167">Eine [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line) ist eine einfache Verbindung zweier Punkte in einem Koordinatenbereich.</span><span class="sxs-lookup"><span data-stu-id="75a92-167">A [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line) is simply a line drawn between two points in coordinate space.</span></span> <span data-ttu-id="75a92-168">Eine **Line** ignoriert alle Werte für [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill), da sie keinen Innenbereich hat.</span><span class="sxs-lookup"><span data-stu-id="75a92-168">A **Line** ignores any value provided for [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill), because it has no interior space.</span></span> <span data-ttu-id="75a92-169">Geben Sie bei einer **Line** Werte für die Eigenschaften [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) und [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness) an, da die **Line** andernfalls nicht gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="75a92-169">For a **Line**, make sure to specify values for the [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) and [**StrokeThickness**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.strokethickness) properties, because otherwise the **Line** won't render.</span></span>

<span data-ttu-id="75a92-170">Sie verwenden keine [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870)-Werte, um eine [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line)-Form anzugeben, sondern diskrete [**Double**](https://msdn.microsoft.com/library/windows/apps/xaml/system.double.aspx)-Werte für [**X1**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.x1.aspx), [**Y1**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.y1.aspx), [**X2**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.x2.aspx) und [**Y2**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.y2.aspx).</span><span class="sxs-lookup"><span data-stu-id="75a92-170">You don't use [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870) values to specify a [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line) shape, instead you use discrete [**Double**](https://msdn.microsoft.com/library/windows/apps/xaml/system.double.aspx) values for [**X1**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.x1.aspx), [**Y1**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.y1.aspx), [**X2**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.x2.aspx) and [**Y2**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.line.y2.aspx).</span></span> <span data-ttu-id="75a92-171">Dadurch wird das Markup für horizontale oder vertikale Linien minimiert.</span><span class="sxs-lookup"><span data-stu-id="75a92-171">This enables minimal markup for horizontal or vertical lines.</span></span> <span data-ttu-id="75a92-172">Beispielsweise definiert `<Line Stroke="Red" X2="400"/>` eine horizontale Linie mit einer Länge von 400 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="75a92-172">For example, `<Line Stroke="Red" X2="400"/>` defines a horizontal line that is 400 pixels long.</span></span> <span data-ttu-id="75a92-173">Die anderen X,Y-Eigenschaften sind standardmäßig 0. Mit diesem XAML wird daher bei Punkten eine Linie von `(0,0)` bis `(400,0)` gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="75a92-173">The other X,Y properties are 0 by default, so in terms of points this XAML would draw a line from `(0,0)` to `(400,0)`.</span></span> <span data-ttu-id="75a92-174">Anschließend können Sie [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/BR243027) zum Verschieben der gesamten **Line** verwenden, wenn sie an einem anderen Punkt als (0,0) beginnen soll.</span><span class="sxs-lookup"><span data-stu-id="75a92-174">You could then use a [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/BR243027) to move the entire **Line**, if you wanted it to start at a point other than (0,0).</span></span>

```xaml
<Line Stroke="Red" X2="400"/>
```

```csharp
var line1 = new Line();
line1.Stroke = new SolidColorBrush(Windows.UI.Colors.Red);
line1.X2 = 400;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(line1);
```

## <a name="span-idpolylinespanspan-idpolylinespanspan-idpolylinespan-polyline"></a><span data-ttu-id="75a92-175"><span id="_Polyline"></span><span id="_polyline"></span><span id="_POLYLINE"></span> Polyline</span><span class="sxs-lookup"><span data-stu-id="75a92-175"><span id="_Polyline"></span><span id="_polyline"></span><span id="_POLYLINE"></span> Polyline</span></span>

<span data-ttu-id="75a92-176">Eine [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) ähnelt einem [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon), da bei beiden die Grenze der Form durch eine Reihe von Punkten definiert wird. Bei einer **Polyline** wird jedoch der letzte Punkt nicht mit dem ersten verbunden.</span><span class="sxs-lookup"><span data-stu-id="75a92-176">A [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) is similar to a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) in that the boundary of the shape is defined by a set of points, except the last point in a **Polyline** is not connected to the first point.</span></span>

<span data-ttu-id="75a92-177">**Hinweis:**  Sie möglicherweise explizit einen identischen Anfangs- und Endpunkt in der [**Punkte**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx) für die [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline)festgelegt, aber in diesem Fall Sie wahrscheinlich hätte verwendet ein [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) stattdessen.</span><span class="sxs-lookup"><span data-stu-id="75a92-177">**Note** You could explicitly have an identical start point and end point in the [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx) set for the [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline), but in that case you probably could have used a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) instead.</span></span>

<span data-ttu-id="75a92-178">Wenn Sie die [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) einer [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) angeben, füllt **Fill** den Innenraum der Form. Dies gilt auch, wenn der Anfangs- und Endpunkt der [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx), die für **Polyline** festgelegt wurden, keine Überschneidungen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="75a92-178">If you specify a [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill) of a [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline), the **Fill** paints the interior space of the shape, even if the start point and end point of the [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx) set for the **Polyline** do not intersect.</span></span> <span data-ttu-id="75a92-179">Wenn Sie keine **Fill** angeben, ähnelt die **Polyline** dem Rendering für mehrere einzelne [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line)-Elemente, bei denen sich die Anfangs- und Endpunkte aufeinander folgender Linien überschneiden.</span><span class="sxs-lookup"><span data-stu-id="75a92-179">If you do not specify a **Fill**, then the **Polyline** is similar to what would have rendered if you had specified several individual [**Line**](/uwp/api/Windows.UI.Xaml.Shapes.Line) elements where the start points and end points of consecutive lines intersected.</span></span>

<span data-ttu-id="75a92-180">Wie bei einem [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon) definiert die [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx)-Eigenschaft die Sammlung von Punkten, die zusammen die Grenze ergeben.</span><span class="sxs-lookup"><span data-stu-id="75a92-180">As with a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon), the [**Points**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.polyline.points.aspx) property defines the collection of points that make up the boundary.</span></span> <span data-ttu-id="75a92-181">In XAML definieren Sie die Punkte mit einer durch Trennzeichen getrennten Liste.</span><span class="sxs-lookup"><span data-stu-id="75a92-181">In XAML, you define the points with a comma-separated list.</span></span> <span data-ttu-id="75a92-182">Im CodeBehind verwenden Sie eine [**PointCollection**](https://msdn.microsoft.com/library/windows/apps/BR210220), um die Punkte zu definieren, und fügen der Sammlung jeden einzelnen Punkt als eine [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870)-Struktur hinzu.</span><span class="sxs-lookup"><span data-stu-id="75a92-182">In code-behind, you use a [**PointCollection**](https://msdn.microsoft.com/library/windows/apps/BR210220) to define the points and you add each individual point as a [**Point**](https://msdn.microsoft.com/library/windows/apps/BR225870) structure to the collection.</span></span>

<span data-ttu-id="75a92-183">Im nächsten Beispiel wird eine [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) mit vierPunkten bei `(10,200)`, `(60,140)`, `(130,140)` und `(180,200)` erstellt.</span><span class="sxs-lookup"><span data-stu-id="75a92-183">This example creates a [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline) with four points set to `(10,200)`, `(60,140)`, `(130,140)`, and `(180,200)`.</span></span> <span data-ttu-id="75a92-184">Es ist ein [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) definiert, jedoch keine [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill).</span><span class="sxs-lookup"><span data-stu-id="75a92-184">A [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) is defined but not a [**Fill**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.fill).</span></span>

```xaml
<Polyline Stroke="Black"
        StrokeThickness="4"
        Points="10,200,60,140,130,140,180,200" />
```

```csharp
var polyline1 = new Polyline();
polyline1.Stroke = new SolidColorBrush(Windows.UI.Colors.Black);
polyline1.StrokeThickness = 4;

var points = new PointCollection();
points.Add(new Windows.Foundation.Point(10, 200));
points.Add(new Windows.Foundation.Point(60, 140));
points.Add(new Windows.Foundation.Point(130, 140));
points.Add(new Windows.Foundation.Point(180, 200));
polyline1.Points = points;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(polyline1);
```

Dies ist die gerenderte [**Polyline**](/uwp/api/Windows.UI.Xaml.Shapes.Polyline). <span data-ttu-id="75a92-186">Beachten Sie, dass der erste und letzte Punkt nicht durch die [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke)-Umrandung miteinander verbunden sind, anders als bei einem [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon).</span><span class="sxs-lookup"><span data-stu-id="75a92-186">Notice that the first and last points are not connected by the [**Stroke**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.shape.stroke) outline as they are in a [**Polygon**](/uwp/api/Windows.UI.Xaml.Shapes.Polygon).</span></span>

![Eine gerenderte Polylinie](images/shapes-polyline.jpg)

## <a name="path"></a><span data-ttu-id="75a92-188">Path</span><span class="sxs-lookup"><span data-stu-id="75a92-188">Path</span></span>

<span data-ttu-id="75a92-189">Ein [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path) ist die vielseitigste [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape)-Klasse, da Sie mit dieser beliebige Geometrien definieren können.</span><span class="sxs-lookup"><span data-stu-id="75a92-189">A [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path) is the most versatile [**Shape**](/uwp/api/Windows.UI.Xaml.Shapes.Shape) because you can use it to define an arbitrary geometry.</span></span> <span data-ttu-id="75a92-190">Diese Vielseitigkeit führt jedoch auch zu Komplexität.</span><span class="sxs-lookup"><span data-stu-id="75a92-190">But with this versatility comes complexity.</span></span> <span data-ttu-id="75a92-191">Betrachten wir nun, wie ein einfacher **Path** in XAML erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="75a92-191">Let's now look at how to create a basic **Path** in XAML.</span></span>

<span data-ttu-id="75a92-192">Sie definieren die Geometrie des Pfads mit der [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="75a92-192">You define the geometry of a path with the [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) property.</span></span> <span data-ttu-id="75a92-193">Es gibt zwei Techniken zum Festlegen von **Data**:</span><span class="sxs-lookup"><span data-stu-id="75a92-193">There are two techniques for setting **Data**:</span></span>

- <span data-ttu-id="75a92-194">Sie können einen Zeichenfolgenwert für [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) in XAML festlegen.</span><span class="sxs-lookup"><span data-stu-id="75a92-194">You can set a string value for [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) in XAML.</span></span> <span data-ttu-id="75a92-195">In diesem Format verwendet der **Path.Data**-Wert ein Serialisierungsformat für Grafiken.</span><span class="sxs-lookup"><span data-stu-id="75a92-195">In this form, the **Path.Data** value is consuming a serialization format for graphics.</span></span> <span data-ttu-id="75a92-196">Nachdem er einmal festgelegt wurde, wird dieser Wert normalerweise nicht mehr als Zeichenfolge bearbeitet.</span><span class="sxs-lookup"><span data-stu-id="75a92-196">You typically don't text-edit this value in string form after it is first established.</span></span> <span data-ttu-id="75a92-197">Stattdessen arbeiten Sie mit Entwicklungstools in einer Entwurfs- oder Zeichnungsmetapher auf einer Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="75a92-197">Instead, you use design tools that enable you to work in a design or drawing metaphor on a surface.</span></span> <span data-ttu-id="75a92-198">Anschließend speichern oder exportieren Sie die Ausgabe und erhalten eine XAML-Datei oder ein XAML-Zeichenfolgenfragment mit **Path.Data**-Informationen.</span><span class="sxs-lookup"><span data-stu-id="75a92-198">Then you save or export the output, and this gives you a XAML file or XAML string fragment with **Path.Data** information.</span></span>
- <span data-ttu-id="75a92-199">Sie können die [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data)-Eigenschaft für ein einzelnes [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry)-Objekt festlegen.</span><span class="sxs-lookup"><span data-stu-id="75a92-199">You can set the [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) property to a single [**Geometry**](/uwp/api/Windows.UI.Xaml.Media.Geometry) object.</span></span> <span data-ttu-id="75a92-200">Die kann im Code oder in XAML erfolgen.</span><span class="sxs-lookup"><span data-stu-id="75a92-200">This can be done in code or in XAML.</span></span> <span data-ttu-id="75a92-201">Diese einzelne **Geometry** ist typischerweise eine [**GeometryGroup**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.geometrygroup), die als Container dient und mehrere Geometriedefinitionen für das Objektmodell in einem Objekt zusammenfassen kann.</span><span class="sxs-lookup"><span data-stu-id="75a92-201">That single **Geometry** is typically a [**GeometryGroup**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.geometrygroup), which acts as a container that can composite multiple geometry definitions into a single object for purposes of the object model.</span></span> <span data-ttu-id="75a92-202">In aller Regel wird diese Vorgehensweise gewählt, um mindestens eine der Kurven und komplexen Formen, die als [**Segments**](https://msdn.microsoft.com/library/windows/apps/BR210164)-Werte definiert werden können, für ein [**PathFigure**](https://msdn.microsoft.com/library/windows/apps/BR210143) zu verwenden, beispielsweise [**BezierSegment**](https://msdn.microsoft.com/library/windows/apps/BR228068).</span><span class="sxs-lookup"><span data-stu-id="75a92-202">The most common reason for doing this is because you want to use one or more of the curves and complex shapes that can be defined as [**Segments**](https://msdn.microsoft.com/library/windows/apps/BR210164) values for a [**PathFigure**](https://msdn.microsoft.com/library/windows/apps/BR210143), for example [**BezierSegment**](https://msdn.microsoft.com/library/windows/apps/BR228068).</span></span>

<span data-ttu-id="75a92-203">Dieses Beispiel zeigt einen [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path), der möglicherweise daraus entstanden ist, dass Blend für Visual Studio zur Erzeugung einiger Vektorformen verwendet wurde und das Ergebnis als XAML gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="75a92-203">This example shows a [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path) that might have resulted from using Blend for Visual Studio to produce just a few vector shapes and then saving the result as XAML.</span></span> <span data-ttu-id="75a92-204">Der vollständige **Path** besteht aus einem Bézierkurven- und einem Liniensegment.</span><span class="sxs-lookup"><span data-stu-id="75a92-204">The total **Path** consists of a Bezier curve segment and a line segment.</span></span> <span data-ttu-id="75a92-205">Dieses Beispiel soll in erster Linie die Elemente im [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data)-Serialisierungsformat zeigen und verstehen helfen, wofür die Zahlen stehen.</span><span class="sxs-lookup"><span data-stu-id="75a92-205">The example is mainly intended to give you some examples of what elements exist in the [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) serialization format and what the numbers represent.</span></span>

<span data-ttu-id="75a92-206">Diese [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) beginnen mit dem move-Befehl, der durch „M“ gekennzeichnet ist und einen Anfangspunkt für den Pfad erstellt.</span><span class="sxs-lookup"><span data-stu-id="75a92-206">This [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) begins with the move command, indicated by "M", which establishes an absolute start point for the path.</span></span>

<span data-ttu-id="75a92-207">Das erste Segment ist eine kubische Bézierkurve, die bei `(100,200)` beginnt und bei `(400,175)` endet. Sie wird mit zwei Kontrollpunkten bei `(100,25)` und `(400,350)` gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="75a92-207">The first segment is a cubic Bezier curve that begins at `(100,200)` and ends at `(400,175)`, which is drawn by using the two control points `(100,25)` and `(400,350)`.</span></span> <span data-ttu-id="75a92-208">Dieses Segment wird durch den „C“-Befehl in der Zeichenfolge des [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data)-Attributs angegeben.</span><span class="sxs-lookup"><span data-stu-id="75a92-208">This segment is indicated by the "C" command in the [**Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) attribute string.</span></span>

<span data-ttu-id="75a92-209">Das zweite Segment beginnt mit dem Befehl „H“ für eine absolute horizontale Linie. Dieser gibt an, dass eine Linie vom bisherigen Endpunkt des Pfads, `(400,175)`, zum neuen Endpunkt, `(280,175)`, gezeichnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="75a92-209">The second segment begins with an absolute horizontal line command "H", which specifies a line drawn from the preceding subpath endpoint `(400,175)` to a new endpoint `(280,175)`.</span></span> <span data-ttu-id="75a92-210">Da es sich um einen Befehl für eine horizontale Linie handelt, ist der angegebene Wert eine x-Koordinate.</span><span class="sxs-lookup"><span data-stu-id="75a92-210">Because it's a horizontal line command, the value specified is an x-coordinate.</span></span>

```xaml
<Path Stroke="DarkGoldenRod" 
      StrokeThickness="3"
      Data="M 100,200 C 100,25 400,350 400,175 H 280" />
```

<span data-ttu-id="75a92-211">Hier ist der gerenderte [**Pfad**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span><span class="sxs-lookup"><span data-stu-id="75a92-211">Here's the rendered [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span></span>

![Ein gerenderter Pfad](images/shapes-path.jpg)

<span data-ttu-id="75a92-213">Das nächste Beispiel zeigt die Verwendung der anderen vorgestellten Technik: [**GeometryGroup**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.geometrygroup) mit [**PathGeometry**](https://msdn.microsoft.com/library/windows/apps/BR210168).</span><span class="sxs-lookup"><span data-stu-id="75a92-213">The next example shows a usage of the other technique we discussed: a [**GeometryGroup**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.geometrygroup) with a [**PathGeometry**](https://msdn.microsoft.com/library/windows/apps/BR210168).</span></span> <span data-ttu-id="75a92-214">Dieses Beispiel zeigt einige der beitragenden Geometrietypen, die als Teil von **PathGeometry** verwendet werden können: [**PathFigure**](https://msdn.microsoft.com/library/windows/apps/BR210143) und die verschiedenen Elemente, die ein Segment in [**PathFigure.Segments**](https://msdn.microsoft.com/library/windows/apps/BR210164) darstellen können.</span><span class="sxs-lookup"><span data-stu-id="75a92-214">This example exercises some of the contributing geometry types that can be used as part of a **PathGeometry**: [**PathFigure**](https://msdn.microsoft.com/library/windows/apps/BR210143) and the various elements that can be a segment in [**PathFigure.Segments**](https://msdn.microsoft.com/library/windows/apps/BR210164).</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1" Fill="#CCCCFF">
    <Path.Data>
        <GeometryGroup>
            <RectangleGeometry Rect="50,5 100,10" />
            <RectangleGeometry Rect="5,5 95,180" />
            <EllipseGeometry Center="100, 100" RadiusX="20" RadiusY="30"/>
            <RectangleGeometry Rect="50,175 100,10" />
            <PathGeometry>
                <PathGeometry.Figures>
                    <PathFigureCollection>
                        <PathFigure IsClosed="true" StartPoint="50,50">
                            <PathFigure.Segments>
                                <PathSegmentCollection>
                                    <BezierSegment Point1="75,300" Point2="125,100" Point3="150,50"/>
                                    <BezierSegment Point1="125,300" Point2="75,100"  Point3="50,50"/>
                                </PathSegmentCollection>
                            </PathFigure.Segments>
                        </PathFigure>
                    </PathFigureCollection>
                </PathGeometry.Figures>
            </PathGeometry>
        </GeometryGroup>
    </Path.Data>
</Path>
```

```csharp
var path1 = new Windows.UI.Xaml.Shapes.Path();
path1.Fill = new SolidColorBrush(Windows.UI.Color.FromArgb(255, 204, 204, 255));
path1.Stroke = new SolidColorBrush(Windows.UI.Colors.Black);
path1.StrokeThickness = 1;

var geometryGroup1 = new GeometryGroup();
var rectangleGeometry1 = new RectangleGeometry();
rectangleGeometry1.Rect = new Rect(50, 5, 100, 10);
var rectangleGeometry2 = new RectangleGeometry();
rectangleGeometry2.Rect = new Rect(5, 5, 95, 180);
geometryGroup1.Children.Add(rectangleGeometry1);
geometryGroup1.Children.Add(rectangleGeometry2);

var ellipseGeometry1 = new EllipseGeometry();
ellipseGeometry1.Center = new Point(100, 100);
ellipseGeometry1.RadiusX = 20;
ellipseGeometry1.RadiusY = 30;
geometryGroup1.Children.Add(ellipseGeometry1);

var pathGeometry1 = new PathGeometry();
var pathFigureCollection1 = new PathFigureCollection();
var pathFigure1 = new PathFigure();
pathFigure1.IsClosed = true;
pathFigure1.StartPoint = new Windows.Foundation.Point(50, 50);
pathFigureCollection1.Add(pathFigure1);
pathGeometry1.Figures = pathFigureCollection1;

var pathSegmentCollection1 = new PathSegmentCollection();
var pathSegment1 = new BezierSegment();
pathSegment1.Point1 = new Point(75, 300);
pathSegment1.Point2 = new Point(125, 100);
pathSegment1.Point3 = new Point(150, 50);
pathSegmentCollection1.Add(pathSegment1);

var pathSegment2 = new BezierSegment();
pathSegment2.Point1 = new Point(125, 300);
pathSegment2.Point2 = new Point(75, 100);
pathSegment2.Point3 = new Point(50, 50);
pathSegmentCollection1.Add(pathSegment2);
pathFigure1.Segments = pathSegmentCollection1;

geometryGroup1.Children.Add(pathGeometry1);
path1.Data = geometryGroup1;

// When you create a XAML element in code, you have to add
// it to the XAML visual tree. This example assumes you have
// a panel named 'layoutRoot' in your XAML file, like this:
// <Grid x:Name="layoutRoot>
layoutRoot.Children.Add(path1);
```

<span data-ttu-id="75a92-215">Hier ist der gerenderte [**Pfad**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span><span class="sxs-lookup"><span data-stu-id="75a92-215">Here's the rendered [**Path**](/uwp/api/Windows.UI.Xaml.Shapes.Path).</span></span>

![Ein gerenderter Pfad](images/shapes-path-2.png)

<span data-ttu-id="75a92-217">Durch die Verwendung von [**PathGeometry**](https://msdn.microsoft.com/library/windows/apps/BR210168) wird das Ergebnis lesbarer als durch das Ausfüllen einer [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data)-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="75a92-217">Using [**PathGeometry**](https://msdn.microsoft.com/library/windows/apps/BR210168) may be more readable than populating a [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) string.</span></span> <span data-ttu-id="75a92-218">Andererseits verwendet [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) eine Syntax, die mit Imagepfaddefinitionen für skalierbare Vektorgrafiken (SVG) kompatibel ist. Daher kann es nützlich sein, Grafiken aus SVG oder als Ausgabe von einem Tool wie etwa Blend zu portieren.</span><span class="sxs-lookup"><span data-stu-id="75a92-218">On the other hand, [**Path.Data**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.path.data) uses a syntax compatible with Scalable Vector Graphics (SVG) image path definitions so it may be useful for porting graphics from SVG, or as output from a tool like Blend.</span></span>
