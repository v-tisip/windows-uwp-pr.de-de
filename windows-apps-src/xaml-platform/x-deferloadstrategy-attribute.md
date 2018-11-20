---
author: jwmsft
title: xDeferLoadStrategy-Attribut
description: „xDeferLoadStrategy“ verzögert die Erstellung eines Elements und seiner untergeordneten Elemente, verkürzt die Startzeit, erhöht aber leicht die Arbeitsspeicherauslastung.Jedes betroffene Element erhöht die Arbeitsspeicherauslastung um ca. 600 Bytes.
ms.assetid: E763898E-13FF-4412-B502-B54DBFE2D4E4
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cd958ba5f9025430be2736329c5a909233461039
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7295962"
---
# <a name="xdeferloadstrategy-attribute"></a><span data-ttu-id="4a2a3-105">x:DeferLoadStrategy-Attribut</span><span class="sxs-lookup"><span data-stu-id="4a2a3-105">x:DeferLoadStrategy attribute</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a2a3-106">Ab Windows10, Version 1703 (Creators Update) wird **x:DeferLoadStrategy** durch das [**x:Load-Attribut**](x-load-attribute.md) ersetzt.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-106">Starting in Windows 10, version 1703 (Creators Update), **x:DeferLoadStrategy** is superseded by the [**x:Load attribute**](x-load-attribute.md).</span></span> <span data-ttu-id="4a2a3-107">Die Verwendung von `x:Load="False"` ist der von `x:DeferLoadStrategy="Lazy"` gleichzustellen, jedoch ermöglicht x:Load bei Bedarf das Entladen der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-107">Using `x:Load="False"` is equivalent to `x:DeferLoadStrategy="Lazy"`, but provides the ability to unload the UI if required.</span></span> <span data-ttu-id="4a2a3-108">Weitere Informationen finden Sie unter [x:Load-Attribut](x-load-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="4a2a3-108">See the [x:Load attribute](x-load-attribute.md) for more info.</span></span>

<span data-ttu-id="4a2a3-109">Sie können **x:DeferLoadStrategy = "Lazy"** zur Optimierung des Starts oder der Strukturerstellungsleistung Ihrer XAML-App.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-109">You can use **x:DeferLoadStrategy="Lazy"** to optimize the startup or tree creation performance of your XAML app.</span></span> <span data-ttu-id="4a2a3-110">Bei der Verwendung von **x:DeferLoadStrategy = "Lazy"** wird die Erstellung eines Elements und seiner untergeordneten Elemente verzögert, was zu einer verringerten Startzeit und Arbeitsspeicherkosten führt.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-110">When you use **x:DeferLoadStrategy="Lazy"**, creation of an element and its children is delayed, which decreases startup time and memory costs.</span></span> <span data-ttu-id="4a2a3-111">Dies ist zur Reduzierung der Kosten für Elemente nützlich, die selten oder nur bedingt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-111">This is useful to reduce the costs of elements that are shown infrequently or conditionally.</span></span> <span data-ttu-id="4a2a3-112">Das Element wird verwirklicht, wenn Code oder VisualStateManager darauf verweist.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-112">The element will be realized when it's referred to from code or VisualStateManager.</span></span>

<span data-ttu-id="4a2a3-113">Durch die Verfolgung von verzögerten Elementen durch das XAML-Framework werden ca. 600 Bytes zur Speicherverwendung für jedes betroffene Element hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-113">However, the tracking of deferred elements by the XAML framework adds about 600 bytes to the memory usage for each element affected.</span></span> <span data-ttu-id="4a2a3-114">Je größer die verzögerte Elementstruktur ist, desto mehr Startzeit sparen Sie – aber auf Kosten eines größeren Arbeitsspeicherbedarfs.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-114">The larger the element tree you defer, the more startup time you'll save, but at the cost of a greater memory footprint.</span></span> <span data-ttu-id="4a2a3-115">Daher ist es möglich, dass durch eine übermäßige Verwendung dieses Attributs die Leistung beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-115">Therefore, it's possible to overuse this attribute to the extent that your performance decreases.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="4a2a3-116">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="4a2a3-116">XAML attribute usage</span></span>

``` syntax
<object x:DeferLoadStrategy="Lazy" .../>
```

## <a name="remarks"></a><span data-ttu-id="4a2a3-117">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="4a2a3-117">Remarks</span></span>

<span data-ttu-id="4a2a3-118">Die Einschränkungen für die Verwendung von **x:DeferLoadStrategy** sind:</span><span class="sxs-lookup"><span data-stu-id="4a2a3-118">The restrictions for using **x:DeferLoadStrategy** are:</span></span>

- <span data-ttu-id="4a2a3-119">Definieren Sie ein [X: Name](x-name-attribute.md)für das Element, da dieses muss das Element später gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-119">You must define an [x:Name](x-name-attribute.md)for the element, as there needs to be a way to find the element later.</span></span>
- <span data-ttu-id="4a2a3-120">Sie können nur Typen ableiten, die von einem [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) oder [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249) abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-120">You can only defer types that derive from [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) or [**FlyoutBase**](https://msdn.microsoft.com/library/windows/apps/dn279249).</span></span>
- <span data-ttu-id="4a2a3-121">Die können keine Stammelemente in einer [**Page**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page), [**UserControls**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol) oder [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/br242348) zurückstellen.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-121">You cannot defer root elements in a [**Page**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page), a [**UserControl**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.usercontrol), or a [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/br242348).</span></span>
- <span data-ttu-id="4a2a3-122">Sie können keine Elemente in einem [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) zurückstellen.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-122">You cannot defer elements in a [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794).</span></span>
- <span data-ttu-id="4a2a3-123">Sie können keine losen XAML zurückstellen, die mit [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048) geladen wurden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-123">You cannot defer loose XAML loaded with [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048).</span></span>
- <span data-ttu-id="4a2a3-124">Durch das Verschieben eines übergeordneten Elements werden alle Elemente gelöscht, die nicht erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-124">Moving a parent element will clear out any elements that have not been realized.</span></span>

<span data-ttu-id="4a2a3-125">Es gibt mehrere Möglichkeiten, verzögerte Elementen zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="4a2a3-125">There are several different ways to realize the deferred elements:</span></span>

- <span data-ttu-id="4a2a3-126">Rufen Sie [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) mit dem Namen auf, der für das Element definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-126">Call [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) with the name that you defined on the element.</span></span>
- <span data-ttu-id="4a2a3-127">Rufen Sie [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) mit dem Namen auf, der für das Element definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-127">Call [**GetTemplateChild**](https://msdn.microsoft.com/library/windows/apps/br209416) with the name that you defined on the element.</span></span>
- <span data-ttu-id="4a2a3-128">Verwenden Sie in [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007) eine [**Setter**](https://msdn.microsoft.com/library/windows/apps/br208817)- oder **Storyboard**-Animation, die auf das verzögerte Element ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-128">In a [**VisualState**](https://msdn.microsoft.com/library/windows/apps/br209007), use a [**Setter**](https://msdn.microsoft.com/library/windows/apps/br208817) or **Storyboard** animation that targets the deferred element.</span></span>
- <span data-ttu-id="4a2a3-129">Legen Sie das verzögerte Elemente in allen **Storyboards** als Ziel fest.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-129">Target the deferred element in any **Storyboard**.</span></span>
- <span data-ttu-id="4a2a3-130">Verwenden Sie eine Bindung, die auf das verzögerte Element ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-130">Use a binding that targets the deferred element.</span></span>

> <span data-ttu-id="4a2a3-131">HINWEIS: Nach Start der Instanziierung eines Elements wird es im Benutzeroberflächen-Thread erstellt. Dies kann ggf. bewirken, dass die Oberfläche ruckelt, wenn zu viele auf einmal erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-131">NOTE: Once the instantiation of an element has started, it is created on the UI thread, so it could cause the UI to stutter if too much is created at once.</span></span>

<span data-ttu-id="4a2a3-132">Wenn ein verzögertes Element mit einer der oben aufgeführten Methoden erstellt wurde, passiert Folgendes:</span><span class="sxs-lookup"><span data-stu-id="4a2a3-132">Once a deferred element is created in any of the ways listed previously, several things happen:</span></span>

- <span data-ttu-id="4a2a3-133">Das [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723)-Ereignis für das Element wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-133">The [**Loaded**](https://msdn.microsoft.com/library/windows/apps/br208723) event on the element is raised.</span></span>
- <span data-ttu-id="4a2a3-134">Alle Bindungen für das Element werden ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-134">Any bindings on the element are evaluated.</span></span>
- <span data-ttu-id="4a2a3-135">Wenn Sie sich für den Empfang von Benachrichtigungen über Änderungen an der Eigenschaft, die die verzögerten Elemente enthält, registriert haben, wird die Benachrichtigung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-135">If you have registered to receive property change notifications on the property containing the deferred element(s), the notification is raised.</span></span>

<span data-ttu-id="4a2a3-136">Sie können verzögerte Elemente verschachteln, jedoch müssen Sie vom äußersten Element aus nach innen erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-136">You can nest deferred elements, however they have to be realized from the outer-most element in.</span></span> <span data-ttu-id="4a2a3-137">Wenn Sie versuchen, ein untergeordnetes Element zu erkennen, bevor das übergeordnete Element erkannt wurde, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-137">If you try to realize a child element before the parent has been realized, an exception is raised.</span></span>

<span data-ttu-id="4a2a3-138">In der Regel wird empfohlen, dass Sie Elemente zurückstellen, die nicht im ersten Frame angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-138">Typically, we recommend that you defer elements that are not viewable in the first frame.</span></span><span data-ttu-id="4a2a3-139">Bei der Suche nach zu verzögernden Kandidaten empfiehlt es sich, nach Elementen zu suchen, die mit reduzierter [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-139">A good guideline for finding candidates to be deferred is to look for elements that are being created with collapsed [**Visibility**](https://msdn.microsoft.com/library/windows/apps/br208992).</span></span> <span data-ttu-id="4a2a3-140">Eine Benutzeroberfläche, die durch eine Benutzerinteraktion ausgelöst wird, ist außerdem ein guter Ort zum Suchen nach Elementen, die zurückgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-140">Also, UI that is triggered by user interaction is a good place to look for elements that you can defer.</span></span>

<span data-ttu-id="4a2a3-141">Seien Sie vorsichtig beim Verzögern von Elementen in einem [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), da so die Startzeit verringert, aber auch die Leistung beim Verschieben reduziert werden kann – je nachdem, was Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-141">Be wary of deferring elements in a [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878), as it will decrease your startup time, but could also decrease your panning performance depending on what you're creating.</span></span> <span data-ttu-id="4a2a3-142">Wenn Sie die Leistung beim Verschieben erhöhen möchten, finden Sie in den Dokumentationen [{x:Bind}-Markuperweiterung](x-bind-markup-extension.md) und [x:Phase-Attribut](x-phase-attribute.md) weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-142">If you are looking to increase panning performance, see the [{x:Bind} markup extension](x-bind-markup-extension.md) and [x:Phase attribute](x-phase-attribute.md) documentation.</span></span>

<span data-ttu-id="4a2a3-143">Wenn das [x:Phase-Attribut](x-phase-attribute.md) zusammen mit **x:DeferLoadStrategy** verwendet wird und ein Element oder eine Elementstruktur realisiert wird, werden die Bindungen bis einschließlich zur aktuellen Phase angewendet.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-143">If the [x:Phase attribute](x-phase-attribute.md) is used in conjunction with **x:DeferLoadStrategy** then, when an element or an element tree is realized, the bindings are applied up to and including the current phase.</span></span> <span data-ttu-id="4a2a3-144">Die für **x:Phase** angegebene Phase wirkt sich nicht auf die Verzögerung des Elements aus und diese lässt sich darüber nicht steuern.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-144">The phase specified for **x:Phase** does not affect or control the deferral of the element.</span></span> <span data-ttu-id="4a2a3-145">Wenn ein Listenelement beim Schwenken wiederverwendet wird, verhalten sich realisierte Elemente wie andere Elemente, und kompilierte Bindungen (**{x:Bind}**-Bindungen) werden unter Verwendung der gleichen Regeln einschließlich Phasing verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-145">When a list item is recycled as part of panning, realized elements behave in the same way as other active elements, and compiled bindings (**{x:Bind}** bindings) are processed using the same rules, including phasing.</span></span>

<span data-ttu-id="4a2a3-146">Eine allgemeine Richtlinie besteht darin, die Leistung Ihrer App vorher und nachher zu messen, um sicherzustellen, das Sie die gewünschte Leistung erhalten.</span><span class="sxs-lookup"><span data-stu-id="4a2a3-146">A general guideline is to measure the performance of your app before and after to make sure you are getting the performance that you want.</span></span>

## <a name="example"></a><span data-ttu-id="4a2a3-147">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4a2a3-147">Example</span></span>

```xml
<Grid x:Name="DeferredGrid" x:DeferLoadStrategy="Lazy">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition Height="Auto" />
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="Auto" />
        <ColumnDefinition Width="Auto" />
    </Grid.ColumnDefinitions>

    <Rectangle Height="100" Width="100" Fill="#F65314" Margin="0,0,4,4" />
    <Rectangle Height="100" Width="100" Fill="#7CBB00" Grid.Column="1" Margin="4,0,0,4" />
    <Rectangle Height="100" Width="100" Fill="#00A1F1" Grid.Row="1" Margin="0,4,4,0" />
    <Rectangle Height="100" Width="100" Fill="#FFBB00" Grid.Row="1" Grid.Column="1" Margin="4,4,0,0" />
</Grid>
<Button x:Name="RealizeElements" Content="Realize Elements" Click="RealizeElements_Click"/>
```

```csharp
private void RealizeElements_Click(object sender, RoutedEventArgs e)
{
    // This will realize the deferred grid.
    this.FindName("DeferredGrid");
}
```
