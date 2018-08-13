---
author: jwmsft
ms.assetid: 79CF3927-25DE-43DD-B41A-87E6768D5C35
title: Optimieren des XAML-Layouts
description: Das Layout kann einen aufwendigen Teil einer XAML-App darstellen, sowohl hinsichtlich der CPU-Nutzung als auch der Beanspruchung des Arbeitsspeichers. Hier sind einige einfache Schritte, mit denen Sie die Layoutleistung Ihrer XAML-App verbessern können.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 40afd15da7e225ea82814ab2fa680a3c95e00488
ms.sourcegitcommit: ec18e10f750f3f59fbca2f6a41bf1892072c3692
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2017
ms.locfileid: "894750"
---
# <a name="optimize-your-xaml-layout"></a><span data-ttu-id="238d4-105">Optimieren des XAML-Layouts</span><span class="sxs-lookup"><span data-stu-id="238d4-105">Optimize your XAML layout</span></span>

<span data-ttu-id="238d4-106">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="238d4-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="238d4-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="238d4-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="238d4-108">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="238d4-108">Important APIs</span></span>**

-   [**<span data-ttu-id="238d4-109">Panel</span><span class="sxs-lookup"><span data-stu-id="238d4-109">Panel</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR227511)

<span data-ttu-id="238d4-110">Unter Layout wird das Definieren der visuellen Struktur der Benutzeroberfläche verstanden.</span><span class="sxs-lookup"><span data-stu-id="238d4-110">Layout is the process of defining the visual structure for your UI.</span></span> <span data-ttu-id="238d4-111">Der primäre Mechanismus zum Beschreiben des Layouts in XAML sind Bereiche, d. h. Containerobjekte, mit denen Sie UI-Elemente positionieren und anzuordnen können.</span><span class="sxs-lookup"><span data-stu-id="238d4-111">The primary mechanism for describing layout in XAML is through panels, which are container objects that enable you to position and arrange the UI elements within them.</span></span> <span data-ttu-id="238d4-112">Das Layout kann sowohl bezüglich der CPU-Auslastung als auch des Aufwands ein ressourcenintensiver Teil einer XAML-App sein.</span><span class="sxs-lookup"><span data-stu-id="238d4-112">Layout can be an expensive part of a XAML app—both in CPU usage and memory overhead.</span></span> <span data-ttu-id="238d4-113">Hier sind einige einfache Schritte, mit denen Sie die Layoutleistung Ihrer XAML-App verbessern können.</span><span class="sxs-lookup"><span data-stu-id="238d4-113">Here are some simple steps you can take to improve the layout performance of your XAML app.</span></span>

## <a name="reduce-layout-structure"></a><span data-ttu-id="238d4-114">Reduzieren der Layout-Struktur</span><span class="sxs-lookup"><span data-stu-id="238d4-114">Reduce layout structure</span></span>

<span data-ttu-id="238d4-115">Die größte Verbesserung der Layoutleistung lässt sich durch die Vereinfachung der hierarchischen Struktur der UI-Elementstruktur erzielen.</span><span class="sxs-lookup"><span data-stu-id="238d4-115">The biggest gain in layout performance comes from simplifying the hierarchical structure of the tree of UI elements.</span></span> <span data-ttu-id="238d4-116">Bereiche sind in der visuellen Struktur vorhanden, aber es sind Strukturelemente, keine *pixelerzeugenden Elemente*, wie ein [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)- oder ein [**Rectangle**](https://msdn.microsoft.com/library/windows/apps/BR243371)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="238d4-116">Panels exist in the visual tree, but they are structural elements, not *pixel producing elements* like a [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) or a [**Rectangle**](https://msdn.microsoft.com/library/windows/apps/BR243371).</span></span> <span data-ttu-id="238d4-117">Die Vereinfachung der Struktur durch die Verringerung der Anzahl der nicht pixelerzeugenden Elemente führt in der Regel zu einer deutlichen Leistungssteigerung.</span><span class="sxs-lookup"><span data-stu-id="238d4-117">Simplifying the tree by reducing the number of non-pixel-producing elements typically provides a significant performance increase.</span></span>

<span data-ttu-id="238d4-118">Viele Benutzeroberflächen werden durch eine Schachtelung von Bereichen implementiert, was zu tiefen, komplexen Strukturen von Bereichen und Elementen führt.</span><span class="sxs-lookup"><span data-stu-id="238d4-118">Many UIs are implemented by nesting panels which results in deep, complex trees of panels and elements.</span></span> <span data-ttu-id="238d4-119">Es ist komfortabel, Bereiche zu schachteln, aber in vielen Fällen kann die gleiche Benutzeroberfläche mit einem komplexeren einzelnen Bereich erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="238d4-119">It is convenient to nest panels, but in many cases the same UI can be achieved with a more complex single panel.</span></span> <span data-ttu-id="238d4-120">Die Verwendung eines einzelnen Bereichs sorgt für eine höhere Leistung.</span><span class="sxs-lookup"><span data-stu-id="238d4-120">Using a single panel provides better performance.</span></span>

### <a name="when-to-reduce-layout-structure"></a><span data-ttu-id="238d4-121">Gründe für die Reduzierung der Layoutstruktur</span><span class="sxs-lookup"><span data-stu-id="238d4-121">When to reduce layout structure</span></span>

<span data-ttu-id="238d4-122">Eine einfache Reduzierung der Layoutstruktur – z. B. indem ein verschachtelter Bereich aus der Seite der obersten Ebene entfernt wird – hat keinen merklichen Effekt.</span><span class="sxs-lookup"><span data-stu-id="238d4-122">Reducing layout structure in a trivial way—for example, reducing one nested panel from your top-level page—does not have a noticeable effect.</span></span>

<span data-ttu-id="238d4-123">Die größten Leistungsgewinne werden durch die Reduzierung von Layoutstrukturen erzielt, die in der Benutzeroberfläche wiederholt vorkommen, z. B. ein [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878)- oder [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="238d4-123">The largest performance gains come from reducing layout structure that's repeated in the UI, like in a [**ListView**](https://msdn.microsoft.com/library/windows/apps/BR242878) or [**GridView**](https://msdn.microsoft.com/library/windows/apps/BR242705).</span></span> <span data-ttu-id="238d4-124">Diese [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803)-Elemente verwenden eine [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348)-Vorlage, welche eine häufig instanziierte Unterstruktur der UI-Elemente definiert.</span><span class="sxs-lookup"><span data-stu-id="238d4-124">These [**ItemsControl**](https://msdn.microsoft.com/library/windows/apps/BR242803) elements use a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348), which defines a subtree of UI elements that is instantiated many times.</span></span> <span data-ttu-id="238d4-125">Wenn die gleiche Unterstruktur in Ihrer App oft repliziert wird, hat jede Leistungsverbesserung dieser Teilstruktur einen multiplikativen Effekt auf die allgemeine Leistung der App.</span><span class="sxs-lookup"><span data-stu-id="238d4-125">When the same subtree is being duplicated many times in your app, any improvements to the performance of that subtree has a multiplicative effect on the overall performance of your app.</span></span>

### <a name="examples"></a><span data-ttu-id="238d4-126">Beispiele</span><span class="sxs-lookup"><span data-stu-id="238d4-126">Examples</span></span>

<span data-ttu-id="238d4-127">Beachten Sie die folgende Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="238d4-127">Consider the following UI.</span></span>

![Beispiel für ein Formularlayout](images/layout-perf-ex1.png)

<span data-ttu-id="238d4-129">In diesen Beispielen werden drei Methoden zur Implementierung der gleichen Benutzeroberfläche gezeigt.</span><span class="sxs-lookup"><span data-stu-id="238d4-129">These examples shows 3 ways of implementing the same UI.</span></span> <span data-ttu-id="238d4-130">Die einzelnen Implementierungsoptionen resultieren in nahezu identischen Pixeln auf dem Bildschirm, unterscheidet sich jedoch grundlegend in den Implementierungsdetails.</span><span class="sxs-lookup"><span data-stu-id="238d4-130">Each implementation choice results in nearly identical pixels on the screen, but differs substantially in the implementation details.</span></span>

<span data-ttu-id="238d4-131">Option 1: Geschachtelte [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-Elemente</span><span class="sxs-lookup"><span data-stu-id="238d4-131">Option1: Nested [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) elements</span></span>

<span data-ttu-id="238d4-132">Obwohl dieses Modell am einfachsten ist, werden darin 5 Bereichselemente verwendet, was zu erheblichem Mehraufwand führt.</span><span class="sxs-lookup"><span data-stu-id="238d4-132">Although this is the simplest model, it uses 5 panel elements and results in significant overhead.</span></span>

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

<span data-ttu-id="238d4-133">Option 2: Ein einzelnes [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element</span><span class="sxs-lookup"><span data-stu-id="238d4-133">Option 2: A single [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)</span></span>

<span data-ttu-id="238d4-134">Das [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element erhöht die Komplexität, jedoch wird nur ein einzelnes Bereichselement verwendet.</span><span class="sxs-lookup"><span data-stu-id="238d4-134">The [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) adds some complexity, but uses only a single panel element.</span></span>

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

<span data-ttu-id="238d4-135">Option 3: Ein einzelnes [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546)-Element:</span><span class="sxs-lookup"><span data-stu-id="238d4-135">Option 3: A single [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546):</span></span>

<span data-ttu-id="238d4-136">Dieser einzelne Bereich ist etwas komplexer als die Verwendung der geschachtelten Bereiche, aber möglicherweise leichter zu verstehen und zu verwalten als ein [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element.</span><span class="sxs-lookup"><span data-stu-id="238d4-136">This single panel is also a bit more complex than using nested panels, but may be easier to understand and maintain than a [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704).</span></span>

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

<span data-ttu-id="238d4-137">Wie die folgenden Beispiele zeigen, gibt es viele Möglichkeiten, die gleiche Benutzeroberfläche zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="238d4-137">As these examples show, there are many ways of achieving the same UI.</span></span> <span data-ttu-id="238d4-138">Sie sollten bei der Wahl der Methode alle Nachteile, darunter die Aspekte Leistung, Lesbarkeit und Wartungsfreundlichkeit, sorgfältig prüfen.</span><span class="sxs-lookup"><span data-stu-id="238d4-138">You should choose by carefully considering all the tradeoffs, including performance, readability, and maintainability.</span></span>

## <a name="use-single-cell-grids-for-overlapping-ui"></a><span data-ttu-id="238d4-139">Verwenden von Rastern mit einzelnen Zellen für überlappende UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="238d4-139">Use single-cell grids for overlapping UI</span></span>

<span data-ttu-id="238d4-140">Eine allgemeine UI-Anforderung ist ein Layout, in dem Elemente einander überlappen.</span><span class="sxs-lookup"><span data-stu-id="238d4-140">A common UI requirement is to have a layout where elements overlap each other.</span></span> <span data-ttu-id="238d4-141">In der Regel werden Abstand, Rand, Ausrichtung und Transformationen verwendet, um Elementen in dieser Weise zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="238d4-141">Typically padding, margins, alignments, and transforms are used to position the elements this way.</span></span> <span data-ttu-id="238d4-142">Das [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Steuerelement in XAML wurde zur Verbesserung der Layoutleistung für sich überschneidende Elemente optimiert.</span><span class="sxs-lookup"><span data-stu-id="238d4-142">The XAML [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704) control is optimized to improve layout performance for elements that overlap.</span></span>

<span data-ttu-id="238d4-143">**Wichtig**  Um eine Verbesserung festzustellen, verwenden Sie ein einzelliges [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Element.</span><span class="sxs-lookup"><span data-stu-id="238d4-143">**Important**  To see the improvement, use a single-cell [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704).</span></span> <span data-ttu-id="238d4-144">Definieren Sie weder [**RowDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.rowdefinitions) noch [**ColumnDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.columndefinitions).</span><span class="sxs-lookup"><span data-stu-id="238d4-144">Do not define [**RowDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.rowdefinitions) or [**ColumnDefinitions**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.columndefinitions).</span></span>

### <a name="examples"></a><span data-ttu-id="238d4-145">Beispiele</span><span class="sxs-lookup"><span data-stu-id="238d4-145">Examples</span></span>

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

## <a name="use-a-panels-built-in-border-properties"></a><span data-ttu-id="238d4-148">Verwenden der integrierten Rahmeneigenschaften von Bereichen</span><span class="sxs-lookup"><span data-stu-id="238d4-148">Use a panel's built-in border properties</span></span>

<span data-ttu-id="238d4-149">[**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-, [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-, [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546)- und [**ContentPresenter**](https://msdn.microsoft.com/library/windows/apps/BR209378)-Steuerelemente besitzen integrierte Rahmeneigenschaften, mit denen Sie einen Rahmen um sie herum zeichnen können, ohne XAML ein zusätzliches [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250)-Element hinzufügen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="238d4-149">[**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635), [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546), and [**ContentPresenter**](https://msdn.microsoft.com/library/windows/apps/BR209378) controls have built-in border properties that let you draw a border around them without adding an additional [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250) element to your XAML.</span></span> <span data-ttu-id="238d4-150">Die neuen Eigenschaften, die den integrierten Rahmen unterstützen sind: **BorderBrush**, **BorderThickness**, **CornerRadius** und **Padding**.</span><span class="sxs-lookup"><span data-stu-id="238d4-150">The new properties that support the built-in border are: **BorderBrush**, **BorderThickness**, **CornerRadius**, and **Padding**.</span></span> <span data-ttu-id="238d4-151">Jede davon ist eine [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/BR242362)-Eigenschaft, sodass sie mit Bindungen und Animationen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="238d4-151">Each of these is a [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/BR242362), so you can use them with bindings and animations.</span></span> <span data-ttu-id="238d4-152">Sie sind als vollständiger Ersatz für ein separates **Border**-Element konzipiert.</span><span class="sxs-lookup"><span data-stu-id="238d4-152">They’re designed to be a full replacement for a separate **Border** element.</span></span>

<span data-ttu-id="238d4-153">Wenn Ihre Benutzeroberfläche über [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250)-Elemente um Bereiche verfügt, verwenden Sie stattdessen den integrierten Rahmen. Dadurch wird ein zusätzliches Element in der Layoutstruktur Ihrer App eingespart.</span><span class="sxs-lookup"><span data-stu-id="238d4-153">If your UI has [**Border**](https://msdn.microsoft.com/library/windows/apps/BR209250) elements around these panels, use the built-in border instead, which saves an extra element in the layout structure of your app.</span></span> <span data-ttu-id="238d4-154">Wie bereits erwähnt, kann die Struktur dadurch deutlich vereinfacht werden, insbesondere bei einer UI mit sich wiederholenden Elementen.</span><span class="sxs-lookup"><span data-stu-id="238d4-154">As mentioned previously, this can be a significant savings, especially in the case of repeated UI.</span></span>

### <a name="examples"></a><span data-ttu-id="238d4-155">Beispiele</span><span class="sxs-lookup"><span data-stu-id="238d4-155">Examples</span></span>

```xml
<RelativePanel BorderBrush="Red" BorderThickness="2" CornerRadius="10" Padding="12">
    <TextBox x:Name="textBox1" RelativePanel.AlignLeftWithPanel="True"/>
    <Button Content="Submit" RelativePanel.Below="textBox1"/>
</RelativePanel>
```

## <a name="use-sizechanged-events-to-respond-to-layout-changes"></a><span data-ttu-id="238d4-156">Verwendung von **SizeChanged**-Ereignissen infolge von Layoutänderungen</span><span class="sxs-lookup"><span data-stu-id="238d4-156">Use **SizeChanged** events to respond to layout changes</span></span>

<span data-ttu-id="238d4-157">Die [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706)-Klasse umfasst zwei ähnliche Ereignisse für die Reaktion auf Layoutänderungen: [**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) und [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged).</span><span class="sxs-lookup"><span data-stu-id="238d4-157">The [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706) class exposes two similar events for responding to layout changes: [**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) and [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged).</span></span> <span data-ttu-id="238d4-158">Möglicherweise verwenden Sie eines dieser Ereignisse, um Benachrichtigungen zu empfangen, wenn ein Element während des Layouts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="238d4-158">You might be using one of these events to receive notification when an element is resized during layout.</span></span> <span data-ttu-id="238d4-159">Die Semantik der beiden Ereignisse unterscheiden sich, und es gibt wichtige Leistungsaspekte, die bei der Auswahl zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="238d4-159">The semantics of the two events are different, and there are important performance considerations in choosing between them.</span></span>

<span data-ttu-id="238d4-160">Wenn eine gute Leistung Priorität hat, ist [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged) fast immer die richtige Wahl.</span><span class="sxs-lookup"><span data-stu-id="238d4-160">For good performance, [**SizeChanged**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.sizechanged) is almost always the right choice.</span></span> <span data-ttu-id="238d4-161">**SizeChanged** hat eine intuitive Semantik.</span><span class="sxs-lookup"><span data-stu-id="238d4-161">**SizeChanged** has intuitive semantics.</span></span> <span data-ttu-id="238d4-162">Es wird während des Layouts ausgelöst, wenn die Größe des [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706)-Objekts aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="238d4-162">It is raised during layout when the size of the [**FrameworkElement**](https://msdn.microsoft.com/library/windows/apps/BR208706) has been updated.</span></span>

<span data-ttu-id="238d4-163">[**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) wird auch während des Layouts ausgelöst, hat aber eine globale Semantik. Es wird für jedes Element ausgelöst, sobald ein Element aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="238d4-163">[**LayoutUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.layoutupdated) is also raised during layout, but it has global semantics—it is raised on every element whenever any element is updated.</span></span> <span data-ttu-id="238d4-164">Es ist üblich, Ereignishandler nur lokal zu verarbeiten, wodurch der Code häufiger als nötig ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="238d4-164">It is typical to only do local processing in the event handler, in which case the code is run more often than needed.</span></span> <span data-ttu-id="238d4-165">Verwenden Sie **LayoutUpdated** nur, wenn Sie wissen müssen, wann ein Element ohne Größenänderung neu angeordnet wird (was ungewöhnlich ist).</span><span class="sxs-lookup"><span data-stu-id="238d4-165">Use **LayoutUpdated** only if you need to know when an element is repositioned without changing size (which is uncommon).</span></span>

## <a name="choosing-between-panels"></a><span data-ttu-id="238d4-166">Auswahl von Bereichen</span><span class="sxs-lookup"><span data-stu-id="238d4-166">Choosing between panels</span></span>

<span data-ttu-id="238d4-167">Die Leistung wird bei der Wahl zwischen einzelnen Bereichen in der Regel nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="238d4-167">Performance is typically not a consideration when choosing between individual panels.</span></span> <span data-ttu-id="238d4-168">Die Auswahl erfolgt in der Regel erfolgt, indem betrachtet wird, welcher Bereich das Layoutverhalten bereitstellt, das der zu implementierenden UI am ähnlichsten ist.</span><span class="sxs-lookup"><span data-stu-id="238d4-168">That choice is typically made by considering which panel provides the layout behavior that is closest to the UI you’re implementing.</span></span> <span data-ttu-id="238d4-169">Wenn Sie z. B. zwischen [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) und [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546) wählen, sollten Sie den Bereich wählen, der am ehesten Ihrer Vorstellung von der Implementierung entspricht.</span><span class="sxs-lookup"><span data-stu-id="238d4-169">For example, if you’re choosing between [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704), [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) , and [**RelativePanel**](https://msdn.microsoft.com/library/windows/apps/Dn879546), you should choose the panel that provides the closest mapping to your mental model of the implementation.</span></span>

<span data-ttu-id="238d4-170">Jede XAML-Bereich ist hinsichtlich einer guten Leistung optimiert, und alle Bereiche stellen eine ähnliche Leistung für ähnliche UIs bereit.</span><span class="sxs-lookup"><span data-stu-id="238d4-170">Every XAML panel is optimized for good performance, and all the panels provide similar performance for similar UI.</span></span>

