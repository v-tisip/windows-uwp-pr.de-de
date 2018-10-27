---
author: jwmsft
ms.assetid: 79CF3927-25DE-43DD-B41A-87E6768D5C35
title: Optimieren des XAML-Layouts
description: Das Layout kann einen aufwendigen Teil einer XAML-App darstellen, sowohl hinsichtlich der CPU-Nutzung als auch der Beanspruchung des Arbeitsspeichers. Hier sind einige einfache Schritte, mit denen Sie die Layoutleistung Ihrer XAML-App verbessern können.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b0dcb3e49bb35902a17f829c0222c570265be8b5
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5692597"
---
# <a name="optimize-your-xaml-layout"></a><span data-ttu-id="9d218-105">Optimieren des XAML-Layouts</span><span class="sxs-lookup"><span data-stu-id="9d218-105">Optimize your XAML layout</span></span>


**<span data-ttu-id="9d218-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9d218-106">Important APIs</span></span>**

-   [**<span data-ttu-id="9d218-107">Panel</span><span class="sxs-lookup"><span data-stu-id="9d218-107">Panel</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR227511)

<span data-ttu-id="9d218-108">Unter Layout wird das Definieren der visuellen Struktur der Benutzeroberfläche verstanden.</span><span class="sxs-lookup"><span data-stu-id="9d218-108">Layout is the process of defining the visual structure for your UI.</span></span> <span data-ttu-id="9d218-109">Der primäre Mechanismus zum Beschreiben des Layouts in XAML sind Bereiche, d. h. Containerobjekte, mit denen Sie UI-Elemente positionieren und anzuordnen können.</span><span class="sxs-lookup"><span data-stu-id="9d218-109">The primary mechanism for describing layout in XAML is through panels, which are container objects that enable you to position and arrange the UI elements within them.</span></span> <span data-ttu-id="9d218-110">Das Layout kann sowohl bezüglich der CPU-Auslastung als auch des Aufwands ein ressourcenintensiver Teil einer XAML-App sein.</span><span class="sxs-lookup"><span data-stu-id="9d218-110">Layout can be an expensive part of a XAML app—both in CPU usage and memory overhead.</span></span> <span data-ttu-id="9d218-111">Hier sind einige einfache Schritte, mit denen Sie die Layoutleistung Ihrer XAML-App verbessern können.</span><span class="sxs-lookup"><span data-stu-id="9d218-111">Here are some simple steps you can take to improve the layout performance of your XAML app.</span></span>

## <a name="reduce-layout-structure"></a><span data-ttu-id="9d218-112">Reduzieren der Layout-Struktur</span><span class="sxs-lookup"><span data-stu-id="9d218-112">Reduce layout structure</span></span>

<span data-ttu-id="9d218-113">Die größte Verbesserung der Layoutleistung lässt sich durch die Vereinfachung der hierarchischen Struktur der UI-Elementstruktur erzielen.</span><span class="sxs-lookup"><span data-stu-id="9d218-113">The biggest gain in layout performance comes from simplifying the hierarchical structure of the tree of UI elements.</span></span> <span data-ttu-id="9d218-114">Bereiche sind in der visuellen Struktur vorhanden, aber es sind Strukturelemente, keine *pixelerzeugenden Elemente*, wie ein [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)- oder ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="9d218-114">Panels exist in the visual tree, but they are structural elements, not *pixel producing elements* like a [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) or a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle).</span></span> <span data-ttu-id="9d218-115">Die Vereinfachung der Struktur durch die Verringerung der Anzahl der nicht pixelerzeugenden Elemente führt in der Regel zu einer deutlichen Leistungssteigerung.</span><span class="sxs-lookup"><span data-stu-id="9d218-115">Simplifying the tree by reducing the number of non-pixel-producing elements typically provides a significant performance increase.</span></span>

<span data-ttu-id="9d218-116">Viele Benutzeroberflächen werden durch eine Schachtelung von Bereichen implementiert, was zu tiefen, komplexen Strukturen von Bereichen und Elementen führt.</span><span class="sxs-lookup"><span data-stu-id="9d218-116">Many UIs are implemented by nesting panels which results in deep, complex trees of panels and elements.</span></span> <span data-ttu-id="9d218-117">Es ist komfortabel, Bereiche zu schachteln, aber in vielen Fällen kann die gleiche Benutzeroberfläche mit einem komplexeren einzelnen Bereich erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="9d218-117">It is convenient to nest panels, but in many cases the same UI can be achieved with a more complex single panel.</span></span> <span data-ttu-id="9d218-118">Die Verwendung eines einzelnen Bereichs sorgt für eine höhere Leistung.</span><span class="sxs-lookup"><span data-stu-id="9d218-118">Using a single panel provides better performance.</span></span>

### <a name="when-to-reduce-layout-structure"></a><span data-ttu-id="9d218-119">Gründe für die Reduzierung der Layoutstruktur</span><span class="sxs-lookup"><span data-stu-id="9d218-119">When to reduce layout structure</span></span>

<span data-ttu-id="9d218-120">Eine einfache Reduzierung der Layoutstruktur – z. B. indem ein verschachtelter Bereich aus der Seite der obersten Ebene entfernt wird – hat keinen merklichen Effekt.</span><span class="sxs-lookup"><span data-stu-id="9d218-120">Reducing layout structure in a trivial way—for example, reducing one nested panel from your top-level page—does not have a noticeable effect.</span></span>

<span data-ttu-id="9d218-121">Die größten Leistungsgewinne werden durch die Reduzierung von Layoutstrukturen erzielt, die in der Benutzeroberfläche wiederholt vorkommen, z. B. ein [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)- oder [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="9d218-121">The largest performance gains come from reducing layout structure that's repeated in the UI, like in a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) or [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705).</span></span> <span data-ttu-id="9d218-122">Diese [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803)-Elemente verwenden eine [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348)-Vorlage, welche eine häufig instanziierte Unterstruktur der UI-Elemente definiert.</span><span class="sxs-lookup"><span data-stu-id="9d218-122">These [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803) elements use a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348), which defines a subtree of UI elements that is instantiated many times.</span></span> <span data-ttu-id="9d218-123">Wenn die gleiche Unterstruktur in Ihrer App oft repliziert wird, hat jede Leistungsverbesserung dieser Teilstruktur einen multiplikativen Effekt auf die allgemeine Leistung der App.</span><span class="sxs-lookup"><span data-stu-id="9d218-123">When the same subtree is being duplicated many times in your app, any improvements to the performance of that subtree has a multiplicative effect on the overall performance of your app.</span></span>

### <a name="examples"></a><span data-ttu-id="9d218-124">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9d218-124">Examples</span></span>

<span data-ttu-id="9d218-125">Beachten Sie die folgende Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="9d218-125">Consider the following UI.</span></span>

![Beispiel für ein Formularlayout](images/layout-perf-ex1.png)

<span data-ttu-id="9d218-127">In diesen Beispielen werden drei Methoden zur Implementierung der gleichen Benutzeroberfläche gezeigt.</span><span class="sxs-lookup"><span data-stu-id="9d218-127">These examples shows 3 ways of implementing the same UI.</span></span> <span data-ttu-id="9d218-128">Die einzelnen Implementierungsoptionen resultieren in nahezu identischen Pixeln auf dem Bildschirm, unterscheidet sich jedoch grundlegend in den Implementierungsdetails.</span><span class="sxs-lookup"><span data-stu-id="9d218-128">Each implementation choice results in nearly identical pixels on the screen, but differs substantially in the implementation details.</span></span>

<span data-ttu-id="9d218-129">Option 1: Geschachtelte [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-Elemente</span><span class="sxs-lookup"><span data-stu-id="9d218-129">Option1: Nested [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) elements</span></span>

<span data-ttu-id="9d218-130">Obwohl dieses Modell am einfachsten ist, werden darin 5 Bereichselemente verwendet, was zu erheblichem Mehraufwand führt.</span><span class="sxs-lookup"><span data-stu-id="9d218-130">Although this is the simplest model, it uses 5 panel elements and results in significant overhead.</span></span>

```xml
  <StackPanel>
  <TextBlock Text="Options:" />
  <StackPanel Orientation="Horizontal">
      <CheckBox Content="Power User" />
      <CheckBox Content="Admin" Margin="20,0,0,0" />
  </StackPanel>
  <TextBlock Text="Basic information:" />
  <StackPanel Orientation="Horizontal">
      <TextBlock Text="Name:" Width="75" />
      <TextBox Width="200" />
  </StackPanel>
  <StackPanel Orientation="Horizontal">
      <TextBlock Text="Email:" Width="75" />
      <TextBox Width="200" />
  </StackPanel>
  <StackPanel Orientation="Horizontal">
      <TextBlock Text="Password:" Width="75" />
      <TextBox Width="200" />
  </StackPanel>
  <Button Content="Save" />
</StackPanel>
```

<span data-ttu-id="9d218-131">Option 2: Ein einzelnes [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element</span><span class="sxs-lookup"><span data-stu-id="9d218-131">Option 2: A single [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)</span></span>

<span data-ttu-id="9d218-132">Das [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element erhöht die Komplexität, jedoch wird nur ein einzelnes Bereichselement verwendet.</span><span class="sxs-lookup"><span data-stu-id="9d218-132">The [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) adds some complexity, but uses only a single panel element.</span></span>

```xml
  <Grid>
  <Grid.RowDefinitions>
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
      <RowDefinition Height="Auto" />
  </Grid.RowDefinitions>
  <Grid.ColumnDefinitions>
      <ColumnDefinition Width="Auto" />
      <ColumnDefinition Width="Auto" />
  </Grid.ColumnDefinitions>
  <TextBlock Text="Options:" Grid.ColumnSpan="2" />
  <CheckBox Content="Power User" Grid.Row="1" Grid.ColumnSpan="2" />
  <CheckBox Content="Admin" Margin="150,0,0,0" Grid.Row="1" Grid.ColumnSpan="2" />
  <TextBlock Text="Basic information:" Grid.Row="2" Grid.ColumnSpan="2" />
  <TextBlock Text="Name:" Width="75" Grid.Row="3" />
  <TextBox Width="200" Grid.Row="3" Grid.Column="1" />
  <TextBlock Text="Email:" Width="75" Grid.Row="4" />
  <TextBox Width="200" Grid.Row="4" Grid.Column="1" />
  <TextBlock Text="Password:" Width="75" Grid.Row="5" />
  <TextBox Width="200" Grid.Row="5" Grid.Column="1" />
  <Button Content="Save" Grid.Row="6" />
</Grid>
```

<span data-ttu-id="9d218-133">Option 3: Ein einzelnes [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546)-Element:</span><span class="sxs-lookup"><span data-stu-id="9d218-133">Option 3: A single [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546):</span></span>

<span data-ttu-id="9d218-134">Dieser einzelne Bereich ist etwas komplexer als die Verwendung der geschachtelten Bereiche, aber möglicherweise leichter zu verstehen und zu verwalten als ein [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element.</span><span class="sxs-lookup"><span data-stu-id="9d218-134">This single panel is also a bit more complex than using nested panels, but may be easier to understand and maintain than a [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704).</span></span>

```xml
<RelativePanel>
  <TextBlock Text="Options:" x:Name="Options" />
  <CheckBox Content="Power User" x:Name="PowerUser" RelativePanel.Below="Options" />
  <CheckBox Content="Admin" Margin="20,0,0,0" 
            RelativePanel.RightOf="PowerUser" RelativePanel.Below="Options" />
  <TextBlock Text="Basic information:" x:Name="BasicInformation"
           RelativePanel.Below="PowerUser" />
  <TextBlock Text="Name:" RelativePanel.AlignVerticalCenterWith="NameBox" />
  <TextBox Width="200" Margin="75,0,0,0" x:Name="NameBox"               
           RelativePanel.Below="BasicInformation" />
  <TextBlock Text="Email:"  RelativePanel.AlignVerticalCenterWith="EmailBox" />
  <TextBox Width="200" Margin="75,0,0,0" x:Name="EmailBox"
           RelativePanel.Below="NameBox" />
  <TextBlock Text="Password:" RelativePanel.AlignVerticalCenterWith="PasswordBox" />
  <TextBox Width="200" Margin="75,0,0,0" x:Name="PasswordBox"
           RelativePanel.Below="EmailBox" />
  <Button Content="Save" RelativePanel.Below="PasswordBox" />
</RelativePanel>
```

<span data-ttu-id="9d218-135">Wie die folgenden Beispiele zeigen, gibt es viele Möglichkeiten, die gleiche Benutzeroberfläche zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="9d218-135">As these examples show, there are many ways of achieving the same UI.</span></span> <span data-ttu-id="9d218-136">Sie sollten bei der Wahl der Methode alle Nachteile, darunter die Aspekte Leistung, Lesbarkeit und Wartungsfreundlichkeit, sorgfältig prüfen.</span><span class="sxs-lookup"><span data-stu-id="9d218-136">You should choose by carefully considering all the tradeoffs, including performance, readability, and maintainability.</span></span>

## <a name="use-single-cell-grids-for-overlapping-ui"></a><span data-ttu-id="9d218-137">Verwenden von Rastern mit einzelnen Zellen für überlappende UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="9d218-137">Use single-cell grids for overlapping UI</span></span>

<span data-ttu-id="9d218-138">Eine allgemeine UI-Anforderung ist ein Layout, in dem Elemente einander überlappen.</span><span class="sxs-lookup"><span data-stu-id="9d218-138">A common UI requirement is to have a layout where elements overlap each other.</span></span> <span data-ttu-id="9d218-139">In der Regel werden Abstand, Rand, Ausrichtung und Transformationen verwendet, um Elementen in dieser Weise zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="9d218-139">Typically padding, margins, alignments, and transforms are used to position the elements this way.</span></span> <span data-ttu-id="9d218-140">Das [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Steuerelement in XAML wurde zur Verbesserung der Layoutleistung für sich überschneidende Elemente optimiert.</span><span class="sxs-lookup"><span data-stu-id="9d218-140">The XAML [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) control is optimized to improve layout performance for elements that overlap.</span></span>

<span data-ttu-id="9d218-141">**Wichtige**verwenden, um eine Verbesserung festzustellen, einem einzelnen Zellen [**Raster**](https://msdn.microsoft.com/library/windows/apps/BR242704).</span><span class="sxs-lookup"><span data-stu-id="9d218-141">**Important**To see the improvement, use a single-cell [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704).</span></span> <span data-ttu-id="9d218-142">Definieren Sie weder [**RowDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.rowdefinitions) noch [**ColumnDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.columndefinitions).</span><span class="sxs-lookup"><span data-stu-id="9d218-142">Do not define [**RowDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.rowdefinitions) or [**ColumnDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.columndefinitions).</span></span>

### <a name="examples"></a><span data-ttu-id="9d218-143">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9d218-143">Examples</span></span>

```xml
<Grid>
    <Ellipse Fill="Red" Width="200" Height="200" />
    <TextBlock Text="Test" 
               HorizontalAlignment="Center" 
               VerticalAlignment="Center" />
</Grid>
```

![Überlagerter Text auf einem Kreis](images/layout-perf-ex2.png)

```xml
<Grid Width="200" BorderBrush="Black" BorderThickness="1">
    <TextBlock Text="Test1" HorizontalAlignment="Left" />
    <TextBlock Text="Test2" HorizontalAlignment="Right" />
</Grid>
```

![Zwei Textblöcke in einem Raster](images/layout-perf-ex3.png)

## <a name="use-a-panels-built-in-border-properties"></a><span data-ttu-id="9d218-146">Verwenden der integrierten Rahmeneigenschaften von Bereichen</span><span class="sxs-lookup"><span data-stu-id="9d218-146">Use a panel's built-in border properties</span></span>

<span data-ttu-id="9d218-147">[**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-, [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-, [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546)- und [**ContentPresenter**](https://msdn.microsoft.com/library/windows/apps/BR209378)-Steuerelemente besitzen integrierte Rahmeneigenschaften, mit denen Sie einen Rahmen um sie herum zeichnen können, ohne XAML ein zusätzliches [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250)-Element hinzufügen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="9d218-147">[**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635), [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546), and [**ContentPresenter**](https://msdn.microsoft.com/library/windows/apps/BR209378) controls have built-in border properties that let you draw a border around them without adding an additional [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250) element to your XAML.</span></span> <span data-ttu-id="9d218-148">Die neuen Eigenschaften, die den integrierten Rahmen unterstützen sind: **BorderBrush**, **BorderThickness**, **CornerRadius** und **Padding**.</span><span class="sxs-lookup"><span data-stu-id="9d218-148">The new properties that support the built-in border are: **BorderBrush**, **BorderThickness**, **CornerRadius**, and **Padding**.</span></span> <span data-ttu-id="9d218-149">Jede davon ist eine [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/BR242362)-Eigenschaft, sodass sie mit Bindungen und Animationen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9d218-149">Each of these is a [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/BR242362), so you can use them with bindings and animations.</span></span> <span data-ttu-id="9d218-150">Sie sind als vollständiger Ersatz für ein separates **Border**-Element konzipiert.</span><span class="sxs-lookup"><span data-stu-id="9d218-150">They’re designed to be a full replacement for a separate **Border** element.</span></span>

<span data-ttu-id="9d218-151">Wenn Ihre Benutzeroberfläche über [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250)-Elemente um Bereiche verfügt, verwenden Sie stattdessen den integrierten Rahmen. Dadurch wird ein zusätzliches Element in der Layoutstruktur Ihrer App eingespart.</span><span class="sxs-lookup"><span data-stu-id="9d218-151">If your UI has [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250) elements around these panels, use the built-in border instead, which saves an extra element in the layout structure of your app.</span></span> <span data-ttu-id="9d218-152">Wie bereits erwähnt, kann die Struktur dadurch deutlich vereinfacht werden, insbesondere bei einer UI mit sich wiederholenden Elementen.</span><span class="sxs-lookup"><span data-stu-id="9d218-152">As mentioned previously, this can be a significant savings, especially in the case of repeated UI.</span></span>

### <a name="examples"></a><span data-ttu-id="9d218-153">Beispiele</span><span class="sxs-lookup"><span data-stu-id="9d218-153">Examples</span></span>

```xml
<RelativePanel BorderBrush="Red" BorderThickness="2" CornerRadius="10" Padding="12">
    <TextBox x:Name="textBox1" RelativePanel.AlignLeftWithPanel="True"/>
    <Button Content="Submit" RelativePanel.Below="textBox1"/>
</RelativePanel>
```

## <a name="use-sizechanged-events-to-respond-to-layout-changes"></a><span data-ttu-id="9d218-154">Verwendung von **SizeChanged**-Ereignissen infolge von Layoutänderungen</span><span class="sxs-lookup"><span data-stu-id="9d218-154">Use **SizeChanged** events to respond to layout changes</span></span>

<span data-ttu-id="9d218-155">Die [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706)-Klasse umfasst zwei ähnliche Ereignisse für die Reaktion auf Layoutänderungen: [**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) und [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged).</span><span class="sxs-lookup"><span data-stu-id="9d218-155">The [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706) class exposes two similar events for responding to layout changes: [**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) and [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged).</span></span> <span data-ttu-id="9d218-156">Möglicherweise verwenden Sie eines dieser Ereignisse, um Benachrichtigungen zu empfangen, wenn ein Element während des Layouts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="9d218-156">You might be using one of these events to receive notification when an element is resized during layout.</span></span> <span data-ttu-id="9d218-157">Die Semantik der beiden Ereignisse unterscheiden sich, und es gibt wichtige Leistungsaspekte, die bei der Auswahl zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="9d218-157">The semantics of the two events are different, and there are important performance considerations in choosing between them.</span></span>

<span data-ttu-id="9d218-158">Wenn eine gute Leistung Priorität hat, ist [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged) fast immer die richtige Wahl.</span><span class="sxs-lookup"><span data-stu-id="9d218-158">For good performance, [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged) is almost always the right choice.</span></span> <span data-ttu-id="9d218-159">**SizeChanged** hat eine intuitive Semantik.</span><span class="sxs-lookup"><span data-stu-id="9d218-159">**SizeChanged** has intuitive semantics.</span></span> <span data-ttu-id="9d218-160">Es wird während des Layouts ausgelöst, wenn die Größe des [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706)-Objekts aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="9d218-160">It is raised during layout when the size of the [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706) has been updated.</span></span>

<span data-ttu-id="9d218-161">[**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) wird auch während des Layouts ausgelöst, hat aber eine globale Semantik. Es wird für jedes Element ausgelöst, sobald ein Element aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="9d218-161">[**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) is also raised during layout, but it has global semantics—it is raised on every element whenever any element is updated.</span></span> <span data-ttu-id="9d218-162">Es ist üblich, Ereignishandler nur lokal zu verarbeiten, wodurch der Code häufiger als nötig ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9d218-162">It is typical to only do local processing in the event handler, in which case the code is run more often than needed.</span></span> <span data-ttu-id="9d218-163">Verwenden Sie **LayoutUpdated** nur, wenn Sie wissen müssen, wann ein Element ohne Größenänderung neu angeordnet wird (was ungewöhnlich ist).</span><span class="sxs-lookup"><span data-stu-id="9d218-163">Use **LayoutUpdated** only if you need to know when an element is repositioned without changing size (which is uncommon).</span></span>

## <a name="choosing-between-panels"></a><span data-ttu-id="9d218-164">Auswahl von Bereichen</span><span class="sxs-lookup"><span data-stu-id="9d218-164">Choosing between panels</span></span>

<span data-ttu-id="9d218-165">Die Leistung wird bei der Wahl zwischen einzelnen Bereichen in der Regel nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="9d218-165">Performance is typically not a consideration when choosing between individual panels.</span></span> <span data-ttu-id="9d218-166">Die Auswahl erfolgt in der Regel erfolgt, indem betrachtet wird, welcher Bereich das Layoutverhalten bereitstellt, das der zu implementierenden UI am ähnlichsten ist.</span><span class="sxs-lookup"><span data-stu-id="9d218-166">That choice is typically made by considering which panel provides the layout behavior that is closest to the UI you’re implementing.</span></span> <span data-ttu-id="9d218-167">Wenn Sie z. B. zwischen [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) und [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546) wählen, sollten Sie den Bereich wählen, der am ehesten Ihrer Vorstellung von der Implementierung entspricht.</span><span class="sxs-lookup"><span data-stu-id="9d218-167">For example, if you’re choosing between [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) , and [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546), you should choose the panel that provides the closest mapping to your mental model of the implementation.</span></span>

<span data-ttu-id="9d218-168">Jede XAML-Bereich ist hinsichtlich einer guten Leistung optimiert, und alle Bereiche stellen eine ähnliche Leistung für ähnliche UIs bereit.</span><span class="sxs-lookup"><span data-stu-id="9d218-168">Every XAML panel is optimized for good performance, and all the panels provide similar performance for similar UI.</span></span>

