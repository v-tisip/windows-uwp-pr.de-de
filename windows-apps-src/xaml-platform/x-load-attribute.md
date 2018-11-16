---
author: jwmsft
title: xLoad-Attribut
description: xLoad ermöglicht die dynamische Erstellung und Zerstörung eines Elements und seiner untergeordneten Elemente, verkürzt die Startzeit Zeit und Speicherverwendung. 
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d9659d183c020c579aa0a21fe179a69c1d9997c5
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6991721"
---
# <a name="xload-attribute"></a><span data-ttu-id="c4580-104">x:Load-Attribut</span><span class="sxs-lookup"><span data-stu-id="c4580-104">x:Load attribute</span></span>

<span data-ttu-id="c4580-105">**X: Load** können Sie um die Startzeit, visuelle Struktur Erstellung und Speicherverwendung Ihrer XAML-App zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c4580-105">You can use **x:Load** to optimize the startup, visual tree creation, and memory usage of your XAML app.</span></span> <span data-ttu-id="c4580-106">Verwendung von **X: Load** wirkt sich visual aus, **Sichtbarkeit**, mit der Ausnahme, dass, wenn das Element nicht geladen wird, der Speicher freigegeben wird ein kleiner Platzhalter wird intern verwendet, um seine Position in der visuellen Struktur markieren.</span><span class="sxs-lookup"><span data-stu-id="c4580-106">Using **x:Load** has a similar visual effect to **Visibility**, except that when the element is not loaded, its memory is released and internally a small placeholder is used to mark its place in the visual tree.</span></span>

<span data-ttu-id="c4580-107">Das UI-Element mit X: Load attributierte möglich geladen und entladen über Code oder mithilfe eines [X: Bind](x-bind-markup-extension.md) -Ausdrucks.</span><span class="sxs-lookup"><span data-stu-id="c4580-107">The UI element attributed with x:Load can be loaded and unloaded via code, or using an [x:Bind](x-bind-markup-extension.md) expression.</span></span> <span data-ttu-id="c4580-108">Dies ist zur Reduzierung der Kosten für Elemente nützlich, die selten oder nur bedingt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-108">This is useful to reduce the costs of elements that are shown infrequently or conditionally.</span></span> <span data-ttu-id="c4580-109">Wenn Sie X: Load auf einem Container wie Raster oder StackPanel verwenden, werden die Container und alle untergeordneten geladen oder als Gruppe entladen.</span><span class="sxs-lookup"><span data-stu-id="c4580-109">When you use x:Load on a container such as Grid or StackPanel, the container and all of its children are loaded or unloaded as a group.</span></span>

<span data-ttu-id="c4580-110">Die Verfolgung von verzögerten Elementen durch das XAML-Framework fügt ca. 600 Bytes zur Speicherverwendung für jedes Element attributierten mit X: Load, um den Platzhalter zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="c4580-110">The tracking of deferred elements by the XAML framework adds about 600 bytes to the memory usage for each element attributed with x:Load, to account for the placeholder.</span></span> <span data-ttu-id="c4580-111">Aus diesem Grund ist es möglich, dieses Attribut durch eine übermäßige Verwendung, dass tatsächlich die Leistung beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4580-111">Therefore, it's possible to overuse this attribute to the extent that your performance actually decreases.</span></span> <span data-ttu-id="c4580-112">Es wird empfohlen, mit denen Sie nur für Elemente, die ausgeblendet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="c4580-112">We recommend that you only use it on elements that need to be hidden.</span></span> <span data-ttu-id="c4580-113">Wenn Sie X: Load auf einem Container verwenden, wird der Aufwand nur für das Element mit dem X: Load-Attribut gezahlt.</span><span class="sxs-lookup"><span data-stu-id="c4580-113">If you use x:Load on a container, then the overhead is paid only for the element with the x:Load attribute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c4580-114">Das Attribut X: Load ist ab Windows 10, Version 1703 (Creators Update) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c4580-114">The x:Load attribute is available starting in Windows 10, version 1703 (Creators Update).</span></span> <span data-ttu-id="c4580-115">Die Mindestversion, auf die Ihr Visual Studio-Projekt abzielt, muss *Windows 10 Creators Update (10.0, Build 15063)* sein, damit x:Load verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c4580-115">The min version targeted by your Visual Studio project must be *Windows 10 Creators Update (10.0, Build 15063)* in order to use x:Load.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="c4580-116">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="c4580-116">XAML attribute usage</span></span>

``` syntax
<object x:Load="True" .../>
<object x:Load="False" .../>
<object x:Load="{x:Bind Path.to.a.boolean, Mode=OneWay}" .../>
```

## <a name="loading-elements"></a><span data-ttu-id="c4580-117">Laden von Elementen</span><span class="sxs-lookup"><span data-stu-id="c4580-117">Loading Elements</span></span>

<span data-ttu-id="c4580-118">Es gibt mehrere Möglichkeiten zum Laden der Elemente:</span><span class="sxs-lookup"><span data-stu-id="c4580-118">There are several different ways to load the elements:</span></span>

- <span data-ttu-id="c4580-119">Verwenden Sie ein [X: Bind](x-bind-markup-extension.md) -Ausdrucks, um den Zustand Load anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c4580-119">Use an [x:Bind](x-bind-markup-extension.md) expression to specify the load state.</span></span> <span data-ttu-id="c4580-120">Der Ausdruck sollte **"true"** zum Laden und **"false",** um das Element zu entladen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c4580-120">The expression should return **true** to load and **false** to unload the element.</span></span>
- <span data-ttu-id="c4580-121">Rufen Sie [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) mit dem Namen auf, der für das Element definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="c4580-121">Call [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) with the name that you defined on the element.</span></span>
- <span data-ttu-id="c4580-122">Rufen Sie [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) mit dem Namen auf, der für das Element definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="c4580-122">Call [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) with the name that you defined on the element.</span></span>
- <span data-ttu-id="c4580-123">Verwenden Sie in einer [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007)eine [**Setter**](https://msdn.microsoft.com/library/windows/apps/br208817) oder das **Storyboard** -Animation, die das X: Load-Element ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="c4580-123">In a [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007), use a [**Setter**](https://msdn.microsoft.com/library/windows/apps/br208817) or **Storyboard** animation that targets the x:Load element.</span></span>
- <span data-ttu-id="c4580-124">Ziel das Entladen Element in jeder **Storyboard**.</span><span class="sxs-lookup"><span data-stu-id="c4580-124">Target the unloaded element in any **Storyboard**.</span></span>

> <span data-ttu-id="c4580-125">HINWEIS: Nach Start der Instanziierung eines Elements wird es im Benutzeroberflächen-Thread erstellt. Dies kann ggf. bewirken, dass die Oberfläche ruckelt, wenn zu viele auf einmal erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-125">NOTE: Once the instantiation of an element has started, it is created on the UI thread, so it could cause the UI to stutter if too much is created at once.</span></span>

<span data-ttu-id="c4580-126">Wenn ein verzögertes Element mit einer der oben aufgeführten Methoden erstellt wurde, passiert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c4580-126">Once a deferred element is created in any of the ways listed previously, several things happen:</span></span>

- <span data-ttu-id="c4580-127">Das [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723)-Ereignis für das Element wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c4580-127">The [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723) event on the element is raised.</span></span>
- <span data-ttu-id="c4580-128">Das Feld für X: Name wird festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4580-128">The field for x:Name is set.</span></span>
- <span data-ttu-id="c4580-129">Alle X: Bind-Bindungen für das Element werden ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="c4580-129">Any x:Bind bindings on the element are evaluated.</span></span>
- <span data-ttu-id="c4580-130">Wenn Sie sich für den Empfang von Benachrichtigungen über Änderungen an der Eigenschaft, die die verzögerten Elemente enthält, registriert haben, wird die Benachrichtigung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c4580-130">If you have registered to receive property change notifications on the property containing the deferred element(s), the notification is raised.</span></span>

## <a name="unloading-elements"></a><span data-ttu-id="c4580-131">Entladen Elemente</span><span class="sxs-lookup"><span data-stu-id="c4580-131">Unloading elements</span></span>

<span data-ttu-id="c4580-132">Um ein Element zu entladen:</span><span class="sxs-lookup"><span data-stu-id="c4580-132">To unload an element:</span></span>

- <span data-ttu-id="c4580-133">Verwenden Sie ein X: Bind-Ausdrucks, um den Zustand Load anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c4580-133">Use an x:Bind expression to specify the load state.</span></span> <span data-ttu-id="c4580-134">Der Ausdruck sollte **"true"** zum Laden und **"false",** um das Element zu entladen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c4580-134">The expression should return **true** to load and **false** to unload the element.</span></span>
- <span data-ttu-id="c4580-135">Rufen Sie in eine Seiten- oder UserControl **UnloadObject auf** , und übergeben Sie den Objektverweis</span><span class="sxs-lookup"><span data-stu-id="c4580-135">In a Page or UserControl, call **UnloadObject** and pass in the object reference</span></span>
- <span data-ttu-id="c4580-136">Rufen Sie **Windows.UI.Xaml.Markup.XamlMarkupHelper.UnloadObject** und übergeben Sie den Objektverweis</span><span class="sxs-lookup"><span data-stu-id="c4580-136">Call **Windows.UI.Xaml.Markup.XamlMarkupHelper.UnloadObject** and pass in the object reference</span></span>

<span data-ttu-id="c4580-137">Wenn ein Objekt entladen wird, wird es mit einem Platzhalter in der Struktur ersetzt.</span><span class="sxs-lookup"><span data-stu-id="c4580-137">When an object is unloaded, it will be replaced in the tree with a placeholder.</span></span> <span data-ttu-id="c4580-138">Die Objektinstanz verbleibt im Arbeitsspeicher, bis alle Verweise freigegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="c4580-138">The object instance will remain in memory until all references have been released.</span></span> <span data-ttu-id="c4580-139">UnloadObject API auf einer Seite "/" UserControl "wurde entwickelt, die Verweise frei, Codegen für X: Name und X: Bind freizugeben.</span><span class="sxs-lookup"><span data-stu-id="c4580-139">The UnloadObject API on a Page/UserControl is designed to release the references held by codegen for x:Name and x:Bind.</span></span> <span data-ttu-id="c4580-140">Wenn Sie zusätzliche Verweise in app-Code enthalten, müssen sie auch freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-140">If you hold additional references in app code they will also need to be released.</span></span>

<span data-ttu-id="c4580-141">Wenn ein Element entladen wird, alle Zustände, die dem Element zugeordnete werden verworfen, also bei Verwendung von X: Load als eine optimierte Version von Sichtbarkeit, dann sicherstellen, dass alle Zustand über Bindungen angewendet wird, oder wird vom Code erneut angewendet, wenn das Loaded-Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="c4580-141">When an element is unloaded, all state associated with the element will be discarded, so if using x:Load as an optimized version of Visibility, then ensure all state is applied via bindings, or is re-applied by code when the Loaded event is fired.</span></span>

## <a name="restrictions"></a><span data-ttu-id="c4580-142">Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="c4580-142">Restrictions</span></span>

<span data-ttu-id="c4580-143">Die Einschränkungen für die Verwendung von **X: Load** sind:</span><span class="sxs-lookup"><span data-stu-id="c4580-143">The restrictions for using **x:Load** are:</span></span>

- <span data-ttu-id="c4580-144">Definieren Sie ein [X: Name](x-name-attribute.md)für das Element, da dieses muss das Element später gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-144">You must define an [x:Name](x-name-attribute.md)for the element, as there needs to be a way to find the element later.</span></span>
- <span data-ttu-id="c4580-145">Sie können nur X: Load auf Typen verwenden, die von [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) oder [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249)abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-145">You can only use x:Load on types that derive from [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) or [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249).</span></span>
- <span data-ttu-id="c4580-146">Sie können keine X: Load auf Stammelemente in einer [**Seite**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page)oder ein [**"UserControl"**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol), einem [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/br242348)verwenden.</span><span class="sxs-lookup"><span data-stu-id="c4580-146">You cannot use x:Load on root elements in a [**Page**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page), a [**UserControl**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol), or a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/br242348).</span></span>
- <span data-ttu-id="c4580-147">Sie können nicht auf Elemente in einem [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794)X: Load verwenden.</span><span class="sxs-lookup"><span data-stu-id="c4580-147">You cannot use x:Load on elements in a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span>
- <span data-ttu-id="c4580-148">X: Load können keine losen XAML mit [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048)geladen.</span><span class="sxs-lookup"><span data-stu-id="c4580-148">You cannot use x:Load on loose XAML loaded with [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048).</span></span>
- <span data-ttu-id="c4580-149">Verschieben eines übergeordneten Elements werden alle Elemente gelöscht, die nicht geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="c4580-149">Moving a parent element will clear out any elements that have not been loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4580-150">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c4580-150">Remarks</span></span>

<span data-ttu-id="c4580-151">X: Load können auf geschachtelte Elemente jedoch müssen Sie vom äußersten Element im erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-151">You can use x:Load on nested elements, however they have to be realized from the outer-most element in.</span></span> <span data-ttu-id="c4580-152">Wenn Sie versuchen, ein untergeordnetes Element zu erkennen, bevor das übergeordnete Element erkannt wurde, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c4580-152">If you try to realize a child element before the parent has been realized, an exception is raised.</span></span>

<span data-ttu-id="c4580-153">In der Regel wird empfohlen, dass Sie Elemente zurückstellen, die nicht im ersten Frame angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-153">Typically, we recommend that you defer elements that are not viewable in the first frame.</span></span><span data-ttu-id="c4580-154">Bei der Suche nach zu verzögernden Kandidaten empfiehlt es sich, nach Elementen zu suchen, die mit reduzierter [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="c4580-154">A good guideline for finding candidates to be deferred is to look for elements that are being created with collapsed [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992).</span></span> <span data-ttu-id="c4580-155">Eine Benutzeroberfläche, die durch eine Benutzerinteraktion ausgelöst wird, ist außerdem ein guter Ort zum Suchen nach Elementen, die zurückgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="c4580-155">Also, UI that is triggered by user interaction is a good place to look for elements that you can defer.</span></span>

<span data-ttu-id="c4580-156">Seien Sie vorsichtig beim Verzögern von Elementen in einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), da so die Startzeit verringert, aber auch die Leistung beim Verschieben reduziert werden kann – je nachdem, was Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4580-156">Be wary of deferring elements in a [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), as it will decrease your startup time, but could also decrease your panning performance depending on what you're creating.</span></span> <span data-ttu-id="c4580-157">Wenn Sie die Leistung beim Verschieben erhöhen möchten, finden Sie in den Dokumentationen [{x:Bind}-Markuperweiterung](x-bind-markup-extension.md) und [x:Phase-Attribut](x-phase-attribute.md) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="c4580-157">If you are looking to increase panning performance, see the [{x:Bind} markup extension](x-bind-markup-extension.md) and [x:Phase attribute](x-phase-attribute.md) documentation.</span></span>

<span data-ttu-id="c4580-158">Wenn das [X: Phase-Attribut](x-phase-attribute.md) in Verbindung mit **X: Load** dann verwendet wird, wenn ein Element oder eine Elementstruktur realisiert wird, werden die Bindungen bis hin zur aktuellen Phase angewendet.</span><span class="sxs-lookup"><span data-stu-id="c4580-158">If the [x:Phase attribute](x-phase-attribute.md) is used in conjunction with **x:Load** then, when an element or an element tree is realized, the bindings are applied up to and including the current phase.</span></span> <span data-ttu-id="c4580-159">Die Phase für **X: Phase** angegeben auswirken oder steuern den Zustand beim Laden des Elements.</span><span class="sxs-lookup"><span data-stu-id="c4580-159">The phase specified for **x:Phase** does affect or control the loading state of the element.</span></span> <span data-ttu-id="c4580-160">Wenn ein Listenelement beim wiederverwendet als Teil der Verschiebung, realisierte Elemente verhält sich auf die gleiche Weise wie andere Elemente, und kompilierte Bindungen (**{X: Bind}** Bindungen) werden unter Verwendung der gleichen Regeln einschließlich phasing verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="c4580-160">When a list item is recycled as part of panning, realized elements will behave in the same way as other active elements, and compiled bindings (**{x:Bind}** bindings) are processed using the same rules, including phasing.</span></span>

<span data-ttu-id="c4580-161">Eine allgemeine Richtlinie besteht darin, die Leistung Ihrer App vorher und nachher zu messen, um sicherzustellen, das Sie die gewünschte Leistung erhalten.</span><span class="sxs-lookup"><span data-stu-id="c4580-161">A general guideline is to measure the performance of your app before and after to make sure you are getting the performance that you want.</span></span>

## <a name="example"></a><span data-ttu-id="c4580-162">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c4580-162">Example</span></span>

```xml
<StackPanel>
    <Grid x:Name="DeferredGrid" x:Load="False">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>

        <Rectangle Height="100" Width="100" Fill="Orange" Margin="0,0,4,4"/>
        <Rectangle Height="100" Width="100" Fill="Green" Grid.Column="1" Margin="4,0,0,4"/>
        <Rectangle Height="100" Width="100" Fill="Blue" Grid.Row="1" Margin="0,4,4,0"/>
        <Rectangle Height="100" Width="100" Fill="Gold" Grid.Row="1" Grid.Column="1" Margin="4,4,0,0"
                   x:Name="one" x:Load="{x:Bind (x:Boolean)CheckBox1.IsChecked, Mode=OneWay}"/>
        <Rectangle Height="100" Width="100" Fill="Silver" Grid.Row="1" Grid.Column="1" Margin="4,4,0,0"
                   x:Name="two" x:Load="{x:Bind Not(CheckBox1.IsChecked), Mode=OneWay}"/>
    </Grid>

    <Button Content="Load elements" Click="LoadElements_Click"/>
    <Button Content="Unload elements" Click="UnloadElements_Click"/>
    <CheckBox x:Name="CheckBox1" Content="Swap Elements" />
</StackPanel>
```

```csharp
// This is used by the bindings between the rectangles and check box.
private bool Not(bool? value) { return !(value==true); }

private void LoadElements_Click(object sender, RoutedEventArgs e)
{
    // This will load the deferred grid, but not the nested
    // rectangles that have x:Load attributes.
    this.FindName("DeferredGrid"); 
}

private void UnloadElements_Click(object sender, RoutedEventArgs e)
{
     // This will unload the grid and all its child elements.
     this.UnloadObject(DeferredGrid);
}
```

