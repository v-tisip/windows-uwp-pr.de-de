---
author: jwmsft
ms.assetid: 569E8C27-FA01-41D8-80B9-1E3E637D5B99
title: Optimieren Ihres XAML-Markups
description: Die Analyse von XAML-Markup zum Erstellen von Objekten im Arbeitsspeicher kann für eine komplexe Benutzeroberfläche viel Zeit in Anspruch nehmen. Hier finden Sie einige Punkte, die Sie zur Optimierung der XAML-Markupanalyse, Ladezeit und Effizienz des Arbeitsspeichers für Ihre App vornehmen können.
ms.author: jimwalk
ms.date: 08/10/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 884825f2e9639f620d8db4e6110791fddf2d7e77
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6980287"
---
# <a name="optimize-your-xaml-markup"></a><span data-ttu-id="6395e-105">Optimieren Ihres XAML-Markups</span><span class="sxs-lookup"><span data-stu-id="6395e-105">Optimize your XAML markup</span></span>


<span data-ttu-id="6395e-106">Die Analyse von XAML-Markup zum Erstellen von Objekten im Arbeitsspeicher kann für eine komplexe Benutzeroberfläche viel Zeit in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="6395e-106">Parsing XAML markup to construct objects in memory is time-consuming for a complex UI.</span></span> <span data-ttu-id="6395e-107">Es folgen einige Vorschläge zur Optimierung der XAML-Markupanalyse, Ladezeit und Effizienz des Arbeitsspeichers Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="6395e-107">Here are some things you can do to improve the parse and load time of your XAML markup and the memory efficiency of your app.</span></span>

<span data-ttu-id="6395e-108">Beschränken Sie beim Start der App das zu ladende XAML-Markup auf die Elemente, die für die anfängliche Benutzeroberfläche erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="6395e-108">At app startup, limit the XAML markup that is loaded to only what you need for your initial UI.</span></span> <span data-ttu-id="6395e-109">Überprüfen Sie das Markup auf der ersten Seite (einschließlich Seitenressourcen), und stellen Sie sicher, dass Sie nicht zusätzliche Elemente laden, die nicht sofort benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-109">Examine the markup in your initial page (including page resources) and confirm that you aren't loading extra elements that aren't needed right away.</span></span> <span data-ttu-id="6395e-110">Diese Elemente können aus einer Vielzahl von Quellen stammen, z.B. aus Ressourcenverzeichnissen, oder es sind Elemente, die anfänglich reduziert sind oder über anderen Elementen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-110">These elements can come from a variety of sources, such as resource dictionaries, elements that are initially collapsed, and elements drawn over other elements.</span></span>

<span data-ttu-id="6395e-111">Ein möglichst effizienter XAML-Code erfordert Kompromisse. Oft gibt es in einer Situation mehrere Lösungsmöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="6395e-111">Optimizing your XAML for efficiency requires making trade-offs; there's not always a single solution for every situation.</span></span> <span data-ttu-id="6395e-112">Wir betrachten hier einige der häufigsten Probleme und stellen Richtlinien bereit, mit deren Hilfe Sie die richtige Entscheidung für Ihre App treffen können.</span><span class="sxs-lookup"><span data-stu-id="6395e-112">Here, we look at some common issues and provide guidelines you can use to make the right trade-offs for your app.</span></span>

## <a name="minimize-element-count"></a><span data-ttu-id="6395e-113">Minimieren der Elementanzahl</span><span class="sxs-lookup"><span data-stu-id="6395e-113">Minimize element count</span></span>

<span data-ttu-id="6395e-114">Obwohl die XAML-Plattform eine große Anzahl von Elementen anzeigen kann, können Sie das Layout und die Darstellung Ihrer App beschleunigen, indem Sie die geringste Anzahl von Elementen verwenden, um das gewünschte Erscheinungsbild zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="6395e-114">Although the XAML platform is capable of displaying large numbers of elements, you can make your app lay out and render faster by using the fewest number of elements to achieve the visuals you want.</span></span>

<span data-ttu-id="6395e-115">Das von Ihnen gewählte Layout für Ihre UI-Steuerelemente bedingt die Anzahl der UI-Elemente, die beim Start Ihrer App erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-115">The choices you make in how you lay out your UI controls will affect the number of UI elements that are created when your app starts.</span></span> <span data-ttu-id="6395e-116">Genauere Informationen zur Optimierung des Layouts finden Sie unter [Optimieren des XAML-Layouts](optimize-your-xaml-layout.md).</span><span class="sxs-lookup"><span data-stu-id="6395e-116">For more detailed information about optimizing layout, see [Optimize your XAML layout](optimize-your-xaml-layout.md).</span></span>

<span data-ttu-id="6395e-117">Die Anzahl der Elemente ist in Datenvorlagen äußerst wichtig, da jedes Element für jedes Datenelement erneut erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="6395e-117">Element count is extremely important in data templates because each element is created again for each data item.</span></span> <span data-ttu-id="6395e-118">Informationen zum Reduzieren der Anzahl der Elemente in einer Liste oder einem Raster finden Sie unter *Elementreduzierung pro Element* im Artikel [Optimieren von ListView- und GridView-Benutzeroberfläche](optimize-gridview-and-listview.md).</span><span class="sxs-lookup"><span data-stu-id="6395e-118">For info about reducing element count in a list or grid, see *Element reduction per item* in the [ListView and GridView UI optimization](optimize-gridview-and-listview.md) article.</span></span>

<span data-ttu-id="6395e-119">Hier betrachten wir einige weitere Möglichkeiten, um die Anzahl der Elemente zu verringern, die Ihre App beim Start laden muss.</span><span class="sxs-lookup"><span data-stu-id="6395e-119">Here, we look at some other ways you can reduce the number of elements your app has to load at startup.</span></span>

### <a name="defer-item-creation"></a><span data-ttu-id="6395e-120">Elementerstellung zurückstellen</span><span class="sxs-lookup"><span data-stu-id="6395e-120">Defer item creation</span></span>

<span data-ttu-id="6395e-121">Wenn Ihr XAML-Markup Elemente enthält, die nicht sofort angezeigt werden müssen, können Sie das Laden dieser Elemente zurückstellen, bis sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-121">If your XAML markup contains elements that you don't show right away, you can defer loading those elements until they are shown.</span></span> <span data-ttu-id="6395e-122">Verzögern Sie beispielsweise die Erstellung nicht sichtbarer Inhalte wie sekundäre Registerkarten in der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="6395e-122">For example, you can delay the creation of non-visible content such as a secondary tab in a tab-like UI.</span></span> <span data-ttu-id="6395e-123">Oder Sie zeigen Elemente in einer Rasteransicht standardmäßig an, geben aber dem Benutzer die Möglichkeit, die Daten stattdessen in einer Liste darzustellen.</span><span class="sxs-lookup"><span data-stu-id="6395e-123">Or, you might show items in a grid view by default, but provide an option for the user to view the data in a list instead.</span></span> <span data-ttu-id="6395e-124">Sie können das Laden der Liste verzögern, bis sie benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="6395e-124">You can delay loading the list until it's needed.</span></span>

<span data-ttu-id="6395e-125">Verwenden Sie das Attribut [x:Load](../xaml-platform/x-load-attribute.md) anstelle der Eigenschaft [Visibility](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.Visibility), um zu steuern, wann ein Element angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6395e-125">Use the [x:Load attribute](../xaml-platform/x-load-attribute.md) instead of the [Visibility](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.Visibility) property to control when an element is shown.</span></span> <span data-ttu-id="6395e-126">Wenn die Sichtbarkeit eines Elements auf **Collapsed** festgelegt ist, wird es zwar während des Renderns übersprungen, aber die Objektinstanz verbraucht trotzdem Arbeitsspeicher.</span><span class="sxs-lookup"><span data-stu-id="6395e-126">When an element's visibility is set to **Collapsed**, then it is skipped during the render pass, but you still pay the object instance costs in memory.</span></span> <span data-ttu-id="6395e-127">Durch die Verwendung von x:Load erstellt das Framework die Objektinstanz nur bei Bedarf, sodass der Speicherverbrauch geringer ist.</span><span class="sxs-lookup"><span data-stu-id="6395e-127">When you use x:Load instead, the framework does not create the object instance until it is needed, so the memory costs are even lower.</span></span> <span data-ttu-id="6395e-128">Der Nachteil ist etwas zusätzlicher Speicherverbrauch (ca. 600 Bytes), wenn die UI nicht geladen ist.</span><span class="sxs-lookup"><span data-stu-id="6395e-128">The drawback is you pay a small memory overhead (approx 600 bytes) when the UI is not loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="6395e-129">Um Elemente verzögert zu laden, verwenden Sie das Attribut [x:Load](../xaml-platform/x-load-attribute.md) oder [x:DeferLoadStrategy](../xaml-platform/x-deferloadstrategy-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="6395e-129">You can delay loading elements using the [x:Load](../xaml-platform/x-load-attribute.md) or [x:DeferLoadStrategy](../xaml-platform/x-deferloadstrategy-attribute.md) attribute.</span></span> <span data-ttu-id="6395e-130">Das Attribut x:Load ist ab Windows10 Creators Update (Version 1703, SDK-Build 15063) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6395e-130">The x:Load attribute is available starting in Windows 10 Creators Update (version 1703, SDK build 15063).</span></span> <span data-ttu-id="6395e-131">Die Mindestversion, auf die Ihr Visual Studio-Projekt abzielt, muss *Windows 10 Creators Update (10.0, Build 15063)* sein, damit x:Load verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6395e-131">The min version targeted by your Visual Studio project must be *Windows 10 Creators Update (10.0, Build 15063)* in order to use x:Load.</span></span> <span data-ttu-id="6395e-132">Für frühere Versionen verwenden Sie x:DeferLoadStrategy.</span><span class="sxs-lookup"><span data-stu-id="6395e-132">To target earlier versions, use x:DeferLoadStrategy.</span></span>

<span data-ttu-id="6395e-133">Die folgenden Beispiele zeigen den Unterschied zwischen der Anzahl von Elementen und der Speicherbelegung, wenn verschiedene Techniken verwendet werden, um UI-Elemente auszublenden.</span><span class="sxs-lookup"><span data-stu-id="6395e-133">The following examples show the difference in element count and memory use when different techniques are used to hide UI elements.</span></span> <span data-ttu-id="6395e-134">Ein ListView- und ein GridView-Steuerelement mit identischen Elementen werden in das Grundraster einer Seite platziert.</span><span class="sxs-lookup"><span data-stu-id="6395e-134">A ListView and a GridView containing identical items are placed in a page's root Grid.</span></span> <span data-ttu-id="6395e-135">Das ListView-Steuerelement ist nicht sichtbar, das GridView-Steuerelement wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6395e-135">The ListView is not visible, but the GridView is shown.</span></span> <span data-ttu-id="6395e-136">Mit dem XAML-Code in jedem dieser Beispiele wird die gleiche Benutzeroberfläche auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6395e-136">The XAML in each of these examples produces the same UI on the screen.</span></span> <span data-ttu-id="6395e-137">Wir verwenden die [Tools für Profilerstellung und Leistung](tools-for-profiling-and-performance.md) aus Visual Studio, um Elementanzahl und Speicherbelegung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="6395e-137">We use Visual Studio's [tools for profiling and performance](tools-for-profiling-and-performance.md) to check the element count and memory use.</span></span>

#### <a name="option-1---inefficient"></a><span data-ttu-id="6395e-138">Option 1: Ineffizient</span><span class="sxs-lookup"><span data-stu-id="6395e-138">Option 1 - Inefficient</span></span>

<span data-ttu-id="6395e-139">Hier wird das ListView-Steuerelement geladen, aber nicht angezeigt, da seine Breite 0 ist.</span><span class="sxs-lookup"><span data-stu-id="6395e-139">Here, the ListView is loaded, but is not visible because it's Width is 0.</span></span> <span data-ttu-id="6395e-140">Das ListView-Steuerelement und jedes seiner untergeordneten Elemente wird in der visuellen Struktur erstellt und in den Speicher geladen.</span><span class="sxs-lookup"><span data-stu-id="6395e-140">The ListView and each of its child elements is created in the visual tree and loaded into memory.</span></span>

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE.-->
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <ListView x:Name="List1" Width="0">
        <ListViewItem>Item 1</ListViewItem>
        <ListViewItem>Item 2</ListViewItem>
        <ListViewItem>Item 3</ListViewItem>
        <ListViewItem>Item 4</ListViewItem>
        <ListViewItem>Item 5</ListViewItem>
        <ListViewItem>Item 6</ListViewItem>
        <ListViewItem>Item 7</ListViewItem>
        <ListViewItem>Item 8</ListViewItem>
        <ListViewItem>Item 9</ListViewItem>
        <ListViewItem>Item 10</ListViewItem>
    </ListView>

    <GridView x:Name="Grid1">
        <GridViewItem>Item 1</GridViewItem>
        <GridViewItem>Item 2</GridViewItem>
        <GridViewItem>Item 3</GridViewItem>
        <GridViewItem>Item 4</GridViewItem>
        <GridViewItem>Item 5</GridViewItem>
        <GridViewItem>Item 6</GridViewItem>
        <GridViewItem>Item 7</GridViewItem>
        <GridViewItem>Item 8</GridViewItem>
        <GridViewItem>Item 9</GridViewItem>
        <GridViewItem>Item 10</GridViewItem>
    </GridView>
</Grid>
```

<span data-ttu-id="6395e-141">Visuelle Live-Struktur mit dem geladenen ListView-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="6395e-141">Live visual tree with the ListView loaded.</span></span> <span data-ttu-id="6395e-142">Die Seite enthält insgesamt 89 Elemente.</span><span class="sxs-lookup"><span data-stu-id="6395e-142">Total element count for the page is 89.</span></span>

![Visuelle Struktur mit Listenansicht](images/visual-tree-1.png)

<span data-ttu-id="6395e-144">Das ListView-Steuerelement und seine untergeordneten Elemente werden in den Speicher geladen.</span><span class="sxs-lookup"><span data-stu-id="6395e-144">ListView and its children are loaded into memory.</span></span>

![Visuelle Struktur mit Listenansicht](images/memory-use-1.png)

#### <a name="option-2---better"></a><span data-ttu-id="6395e-146">Option 2: Besser.</span><span class="sxs-lookup"><span data-stu-id="6395e-146">Option 2 - Better</span></span>

<span data-ttu-id="6395e-147">Hier wird die Sichtbarkeit des ListView-Steuerelements auf „Collapsed” festgelegt (der restliche XAML-Code ist mit dem Original identisch).</span><span class="sxs-lookup"><span data-stu-id="6395e-147">Here, the ListView's Visibility is set to collapsed (the other XAML is identical to the original).</span></span> <span data-ttu-id="6395e-148">Das ListView-Steuerelement wird in der visuellen Struktur erstellt, nicht aber seine untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="6395e-148">The ListView is created in the visual tree, but its child elements are not.</span></span> <span data-ttu-id="6395e-149">Allerdings werden sie in den Speicher geladen, und damit ist die Speicherbelegung identisch mit dem vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="6395e-149">However, they are loaded into memory, so memory use is identical to the previous example.</span></span>

```xaml
    <ListView x:Name="List1" Visibility="Collapsed">
```

<span data-ttu-id="6395e-150">Visuelle Live-Struktur mit dem reduzierten ListView-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="6395e-150">Live visual tree with the ListView collapsed.</span></span> <span data-ttu-id="6395e-151">Die Seite enthält insgesamt 46 Elemente.</span><span class="sxs-lookup"><span data-stu-id="6395e-151">Total element count for the page is 46.</span></span>

![Visuelle Struktur mit reduzierter Listenansicht](images/visual-tree-2.png)

<span data-ttu-id="6395e-153">Das ListView-Steuerelement und seine untergeordneten Elemente werden in den Speicher geladen.</span><span class="sxs-lookup"><span data-stu-id="6395e-153">ListView and its children are loaded into memory.</span></span>

![Visuelle Struktur mit Listenansicht](images/memory-use-1.png)

#### <a name="option-3---most-efficient"></a><span data-ttu-id="6395e-155">Option 3: Am effizientesten.</span><span class="sxs-lookup"><span data-stu-id="6395e-155">Option 3 - Most Efficient</span></span>

<span data-ttu-id="6395e-156">Hier ist für das ListView-Steuerelement das Attribut x:Load auf **False** festgelegt (der restliche XAML-Code ist mit dem Original identisch).</span><span class="sxs-lookup"><span data-stu-id="6395e-156">Here, the ListView has the x:Load attribute set to **False** (the other XAML is identical to the original).</span></span> <span data-ttu-id="6395e-157">Das ListView-Steuerelement wird nicht in der visuellen Struktur erstellt oder beim Start in den Speicher geladen.</span><span class="sxs-lookup"><span data-stu-id="6395e-157">The ListView is not created in the visual tree or loaded into memory at start up.</span></span>

```xaml
    <ListView x:Name="List1" Visibility="Collapsed" x:Load="False">
```

<span data-ttu-id="6395e-158">Visuelle Live-Struktur mit dem nicht geladenen ListView-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="6395e-158">Live visual tree with the ListView not loaded.</span></span> <span data-ttu-id="6395e-159">Die Seite enthält insgesamt 45 Elemente.</span><span class="sxs-lookup"><span data-stu-id="6395e-159">Total element count for the page is 45.</span></span>

![Visuelle Struktur mit dem nicht geladenen ListView-Steuerelement.](images/visual-tree-3.png)

<span data-ttu-id="6395e-161">Das ListView-Steuerelement und seine untergeordneten Elemente werden nicht in den Speicher geladen.</span><span class="sxs-lookup"><span data-stu-id="6395e-161">ListView and its children are not loaded into memory.</span></span>

![Visuelle Struktur mit Listenansicht](images/memory-use-3.png)

> [!NOTE]
> <span data-ttu-id="6395e-163">Anzahl der Elemente und Speicherbelegung sind in diesen Beispielen sehr gering und sollen nur das Konzept veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="6395e-163">The element counts and memory use in these examples are very small and are shown only to demonstrate the concept.</span></span> <span data-ttu-id="6395e-164">In diesen Beispielen ist der Aufwand für die Verwendung von x:Load größer als die Speicherplatzersparnis, sodass die App davon nicht profitieren würde.</span><span class="sxs-lookup"><span data-stu-id="6395e-164">In these examples, the overhead of using x:Load is greater than the memory savings, so the app would not benefit.</span></span> <span data-ttu-id="6395e-165">Sie sollten mit den Profilerstellungstools untersuchen, ob Ihre App von einem verzögerten Laden profitieren würde.</span><span class="sxs-lookup"><span data-stu-id="6395e-165">You should use the profiling tools on your app to determine whether or not your app will benefit from deferred loading.</span></span>

### <a name="use-layout-panel-properties"></a><span data-ttu-id="6395e-166">Verwenden von Layoutpaneleigenschaften</span><span class="sxs-lookup"><span data-stu-id="6395e-166">Use layout panel properties</span></span>

<span data-ttu-id="6395e-167">Layoutpanel verfügen über die Eigenschaft [Background](https://msdn.microsoft.com/library/windows/apps/BR227512), sodass zum Einfärben kein [Rectangle](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) vor dem Panel erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6395e-167">Layout panels have a [Background](https://msdn.microsoft.com/library/windows/apps/BR227512) property so there's no need to put a [Rectangle](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) in front of a Panel just to color it.</span></span>

**<span data-ttu-id="6395e-168">Ineffizient.</span><span class="sxs-lookup"><span data-stu-id="6395e-168">Inefficient</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Grid>
    <Rectangle Fill="Black"/>
</Grid>
```

**<span data-ttu-id="6395e-169">Effizient</span><span class="sxs-lookup"><span data-stu-id="6395e-169">Efficient</span></span>**

```xaml
<Grid Background="Black"/>
```

<span data-ttu-id="6395e-170">Layoutpanel verfügen auch über integrierte Rahmeneigenschaften, sodass Sie kein [Border](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.border)-Element um ein Layoutpanel platzieren müssen</span><span class="sxs-lookup"><span data-stu-id="6395e-170">Layout panels also have built-in border properties, so you don't need to put a [Border](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.border) element around a layout panel.</span></span> <span data-ttu-id="6395e-171">Beispiele und weitere Informationen finden Sie unter [Optimieren des XAML-Layouts](optimize-your-xaml-layout.md).</span><span class="sxs-lookup"><span data-stu-id="6395e-171">See [Optimize your XAML layout](optimize-your-xaml-layout.md) for more info and examples.</span></span>

### <a name="use-images-in-place-of-vector-based-elements"></a><span data-ttu-id="6395e-172">Verwenden von Bildern anstelle von vektorbasierten Elementen</span><span class="sxs-lookup"><span data-stu-id="6395e-172">Use images in place of vector-based elements</span></span>

<span data-ttu-id="6395e-173">Wenn Sie das gleiche vektorbasierte Element häufig wiederverwenden, kann es effizienter sein, stattdessen ein [Image](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.image)-Element zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6395e-173">If you reuse the same vector-based element enough times, it becomes more efficient to use an [Image](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.image) element instead.</span></span> <span data-ttu-id="6395e-174">Vektorbasierte Elemente können aufwendiger sein, da die CPU jedes einzelne Element separat erstellen muss.</span><span class="sxs-lookup"><span data-stu-id="6395e-174">Vector-based elements can be more expensive because the CPU must create each individual element separately.</span></span> <span data-ttu-id="6395e-175">Die Bilddatei muss hingegen nur einmal decodiert werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-175">The image file needs to be decoded only once.</span></span>

## <a name="optimize-resources-and-resource-dictionaries"></a><span data-ttu-id="6395e-176">Optimieren von Ressourcen und Ressourcenwörterbücher</span><span class="sxs-lookup"><span data-stu-id="6395e-176">Optimize resources and resource dictionaries</span></span>

<span data-ttu-id="6395e-177">Verwenden Sie möglichst [Ressourcenwörterbücher](../design/controls-and-patterns/resourcedictionary-and-xaml-resource-references.md), um Ressourcen, auf die an mehreren Stellen in Ihrer App verwiesen werden soll, auf einer Art globalen Ebene zu speichern.</span><span class="sxs-lookup"><span data-stu-id="6395e-177">You typically use [resource dictionaries](../design/controls-and-patterns/resourcedictionary-and-xaml-resource-references.md) to store, at a somewhat global level, resources that you want to reference in multiple places in your app.</span></span> <span data-ttu-id="6395e-178">Beispielsweise Stile, Pinsel, Vorlagen usw.</span><span class="sxs-lookup"><span data-stu-id="6395e-178">For example, styles, brushes, templates, and so on.</span></span>

<span data-ttu-id="6395e-179">Wir haben [ResourceDictionary](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.ResourceDictionary) dahingehend optimiert, dass nur angeforderte Ressourcen instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-179">In general, we have optimized [ResourceDictionary](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.ResourceDictionary) to not instantiate resources unless they're asked for.</span></span> <span data-ttu-id="6395e-180">Aber es gibt Situationen, die Sie vermeiden sollten, damit Ressourcen nicht unnötig instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-180">But there are situations you should avoid so that resources aren’t instantiated unnecessarily.</span></span>

### <a name="resources-with-xname"></a><span data-ttu-id="6395e-181">Ressource mit „x:Name“</span><span class="sxs-lookup"><span data-stu-id="6395e-181">Resources with x:Name</span></span>

<span data-ttu-id="6395e-182">Verwenden Sie das [x:Key-Attribut](../xaml-platform/x-key-attribute.md), um Ihre Ressourcen zu referenzieren.</span><span class="sxs-lookup"><span data-stu-id="6395e-182">Use the [x:Key attribute](../xaml-platform/x-key-attribute.md) to reference your resources.</span></span> <span data-ttu-id="6395e-183">Ressourcen mit dem [x:Name-Attribut](../xaml-platform/x-name-attribute.md) profitieren nicht von der Plattformoptimierung, sondern werden sofort bei der Erstellung von ResourceDictionary instanziiert.</span><span class="sxs-lookup"><span data-stu-id="6395e-183">Any resource with the [x:Name attribute](../xaml-platform/x-name-attribute.md) will not benefit from the platform optimization; instead, it is instantiated as soon as the ResourceDictionary is created.</span></span> <span data-ttu-id="6395e-184">Der Grund: „x:Name“ teilt der Plattform mit, dass Ihre App Feldzugriff auf diese Ressource benötigt. Daher muss die Plattform etwas erstellen, für das ein Verweis eingerichtet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6395e-184">This happens because x:Name tells the platform that your app needs field access to this resource, so the platform needs to create something to create a reference to.</span></span>

### <a name="resourcedictionary-in-a-usercontrol"></a><span data-ttu-id="6395e-185">ResourceDictionary in einem UserControl-Element</span><span class="sxs-lookup"><span data-stu-id="6395e-185">ResourceDictionary in a UserControl</span></span>

<span data-ttu-id="6395e-186">Ein innerhalb von [UserControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol) definiertes ResourceDictionary führt zu Leistungseinbußen.</span><span class="sxs-lookup"><span data-stu-id="6395e-186">A ResourceDictionary defined inside of a [UserControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol) carries a penalty.</span></span> <span data-ttu-id="6395e-187">Die Plattform erstellt für jede Instanz von UserControl eine Kopie von ResourceDictionary.</span><span class="sxs-lookup"><span data-stu-id="6395e-187">The platform creates a copy of such a ResourceDictionary for every instance of the UserControl.</span></span> <span data-ttu-id="6395e-188">Bei einem häufig verwendeten Benutzersteuerelement empfiehlt es sich daher, ResourceDictionary aus UserControl zu entfernen und auf der Seitenebene zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="6395e-188">If you have a UserControl that is used a lot, then move the ResourceDictionary out of the UserControl and put it the page level.</span></span>

### <a name="resource-and-resourcedictionary-scope"></a><span data-ttu-id="6395e-189">Ressourcen und ResourceDictionary-Bereich</span><span class="sxs-lookup"><span data-stu-id="6395e-189">Resource and ResourceDictionary scope</span></span>

<span data-ttu-id="6395e-190">Falls eine Seite auf ein Steuerelement oder eine Ressource in einer anderen Datei verweist, wird auch diese Datei vom Framework analysiert.</span><span class="sxs-lookup"><span data-stu-id="6395e-190">If a page references a user control or a resource defined in a different file, then the framework parses that file, too.</span></span>

<span data-ttu-id="6395e-191">Da _InitialPage.xaml_ in diesem Beispiel eine Ressource von _ExampleResourceDictionary.xaml_ verwendet, muss die gesamte Datei _ExampleResourceDictionary.xaml_ beim Start analysiert werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-191">Here, because _InitialPage.xaml_ uses one resource from _ExampleResourceDictionary.xaml_, the whole of _ExampleResourceDictionary.xaml_ must be parsed at startup.</span></span>

**<span data-ttu-id="6395e-192">InitialPage.xaml</span><span class="sxs-lookup"><span data-stu-id="6395e-192">InitialPage.xaml.</span></span>**

```xaml
<Page x:Class="ExampleNamespace.InitialPage" ...>
    <Page.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <ResourceDictionary Source="ExampleResourceDictionary.xaml"/>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Page.Resources>

    <Grid>
        <TextBox Foreground="{StaticResource TextBrush}"/>
    </Grid>
</Page>
```

**<span data-ttu-id="6395e-193">ExampleResourceDictionary.xaml</span><span class="sxs-lookup"><span data-stu-id="6395e-193">ExampleResourceDictionary.xaml.</span></span>**

```xaml
<ResourceDictionary>
    <SolidColorBrush x:Key="TextBrush" Color="#FF3F42CC"/>

    <!--This ResourceDictionary contains many other resources that
        are used in the app, but are not needed during startup.-->
</ResourceDictionary>
```

<span data-ttu-id="6395e-194">Wenn Sie eine Ressource in der gesamten App auf vielen Seiten verwenden, ist es eine bewährte Methode, diese in der Datei _App.xaml_ zu speichern, um eine Duplizierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6395e-194">If you use a resource on many pages throughout your app, then storing it in _App.xaml_ is a good practice, and avoids duplication.</span></span> <span data-ttu-id="6395e-195">Aber _App.xaml_ wird beim Starten der App analysiert. Daher sollte jede Ressource, die nur auf einer Seite verwendet wird (es sei denn, diese Seite ist die Ausgangsseite), unter den lokalen Ressourcen der Seite gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="6395e-195">But _App.xaml_ is parsed at app startup so any resource that is used in only one page (unless that page is the initial page) should be put into the page's local resources.</span></span> <span data-ttu-id="6395e-196">In diesem Beispiel enthält die Datei _App.xaml_ Ressourcen, die nur von einer Seite verwendet werden (bei der es sich nicht um die Ausgangsseite handelt).</span><span class="sxs-lookup"><span data-stu-id="6395e-196">This example shows _App.xaml_ containing resources that are used by only one page (that's not the initial page).</span></span> <span data-ttu-id="6395e-197">Dadurch wird die Startzeit der App unnötigerweise erhöht.</span><span class="sxs-lookup"><span data-stu-id="6395e-197">This needlessly increases app startup time.</span></span>

**<span data-ttu-id="6395e-198">App.xaml</span><span class="sxs-lookup"><span data-stu-id="6395e-198">App.xaml</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Application ...>
     <Application.Resources>
        <SolidColorBrush x:Key="DefaultAppTextBrush" Color="#FF3F42CC"/>
        <SolidColorBrush x:Key="InitialPageTextBrush" Color="#FF3F42CC"/>
        <SolidColorBrush x:Key="SecondPageTextBrush" Color="#FF3F42CC"/>
        <SolidColorBrush x:Key="ThirdPageTextBrush" Color="#FF3F42CC"/>
    </Application.Resources>
</Application>
```

**<span data-ttu-id="6395e-199">InitialPage.xaml</span><span class="sxs-lookup"><span data-stu-id="6395e-199">InitialPage.xaml.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Page x:Class="ExampleNamespace.InitialPage" ...>
    <StackPanel>
        <TextBox Foreground="{StaticResource InitialPageTextBrush}"/>
    </StackPanel>
</Page>
```

**<span data-ttu-id="6395e-200">SecondPage.xaml</span><span class="sxs-lookup"><span data-stu-id="6395e-200">SecondPage.xaml.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Page x:Class="ExampleNamespace.SecondPage" ...>
    <StackPanel>
        <Button Content="Submit" Foreground="{StaticResource SecondPageTextBrush}" />
    </StackPanel>
</Page>
```

<span data-ttu-id="6395e-201">Um dieses Beispiel effizienter zu gestalten, verschieben Sie `SecondPageTextBrush` in _SecondPage.xaml_ und `ThirdPageTextBrush` in _ThirdPage.xaml_.</span><span class="sxs-lookup"><span data-stu-id="6395e-201">To make this example more efficient, move `SecondPageTextBrush` into _SecondPage.xaml_ and move `ThirdPageTextBrush` into _ThirdPage.xaml_.</span></span> `InitialPageTextBrush` <span data-ttu-id="6395e-202">kann in _App.xaml_ verbleiben, da Anwendungsressourcen beim Start der App analysiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="6395e-202">can remain in _App.xaml_ because application resources must be parsed at app startup in any case.</span></span>

### <a name="consolidate-multiple-brushes-that-look-the-same-into-one-resource"></a><span data-ttu-id="6395e-203">Zusammenfassen mehrerer gleichartiger Pinsel in einer Ressource</span><span class="sxs-lookup"><span data-stu-id="6395e-203">Consolidate multiple brushes that look the same into one resource</span></span>

<span data-ttu-id="6395e-204">Die XAML-Plattform speichert allgemein verwendete Objekte zwischen, um eine möglichst häufige Wiederverwendung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6395e-204">The XAML platform tries to cache commonly-used objects so that they can be reused as often as possible.</span></span> <span data-ttu-id="6395e-205">XAML kann jedoch nicht ohne Weiteres feststellen, ob es sich bei einem Pinsel, der in zwei unterschiedlichen Markupkomponenten deklariert ist, um denselben Pinsel handelt.</span><span class="sxs-lookup"><span data-stu-id="6395e-205">But XAML cannot easily tell if a brush declared in one piece of markup is the same as a brush declared in another.</span></span> <span data-ttu-id="6395e-206">Dieses Beispiel verwendet [SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962) zur Veranschaulichung, aber die Wahrscheinlichkeit und Bedeutung von [GradientBrush](https://msdn.microsoft.com/library/windows/apps/BR210068) ist höher.</span><span class="sxs-lookup"><span data-stu-id="6395e-206">The example here uses [SolidColorBrush](https://msdn.microsoft.com/library/windows/apps/BR242962) to demonstrate, but the case is more likely and more important with [GradientBrush](https://msdn.microsoft.com/library/windows/apps/BR210068).</span></span> <span data-ttu-id="6395e-207">Prüfen Sie auch auf Pinsel, die vordefinierte Farben verwenden – beispielsweise bezeichnen `"Orange"` und `"#FFFFA500"` dieselbe Farbe.</span><span class="sxs-lookup"><span data-stu-id="6395e-207">Also check for brushes that use predefined colors; for example, `"Orange"` and `"#FFFFA500"` are the same color.</span></span>

**<span data-ttu-id="6395e-208">Ineffizient.</span><span class="sxs-lookup"><span data-stu-id="6395e-208">Inefficient.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Page ... >
    <StackPanel>
        <TextBlock>
            <TextBlock.Foreground>
                <SolidColorBrush Color="#FFFFA500"/>
            </TextBlock.Foreground>
        </TextBox>
        <Button Content="Submit">
            <Button.Foreground>
                <SolidColorBrush Color="#FFFFA500"/>
            </Button.Foreground>
        </Button>
    </StackPanel>
</Page>
```

<span data-ttu-id="6395e-209">Definieren Sie den Pinsel als Ressource, um die Duplizierung zu beheben.</span><span class="sxs-lookup"><span data-stu-id="6395e-209">To fix the duplication, define the brush as a resource.</span></span> <span data-ttu-id="6395e-210">Wenn Steuerelemente auf anderen Seiten denselben Pinsel verwenden, verschieben Sie diese in die Datei _App.xaml_.</span><span class="sxs-lookup"><span data-stu-id="6395e-210">If controls in other pages use the same brush, move it to _App.xaml_.</span></span>

**<span data-ttu-id="6395e-211">Effizient</span><span class="sxs-lookup"><span data-stu-id="6395e-211">Efficient.</span></span>**

```xaml
<Page ... >
    <Page.Resources>
        <SolidColorBrush x:Key="BrandBrush" Color="#FFFFA500"/>
    </Page.Resources>

    <StackPanel>
        <TextBlock Foreground="{StaticResource BrandBrush}" />
        <Button Content="Submit" Foreground="{StaticResource BrandBrush}" />
    </StackPanel>
</Page>
```

## <a name="minimize-overdrawing"></a><span data-ttu-id="6395e-212">Minimieren der Überzeichnung</span><span class="sxs-lookup"><span data-stu-id="6395e-212">Minimize overdrawing</span></span>

<span data-ttu-id="6395e-213">Eine Überzeichnung tritt dort auf, wo mehrere Objekte dieselben Bildschirmpixel beanspruchen.</span><span class="sxs-lookup"><span data-stu-id="6395e-213">Overdrawing occurs where more than one object is drawn in the same screen pixels.</span></span> <span data-ttu-id="6395e-214">Beachten Sie, dass Sie manchmal einen Kompromiss zwischen dieser Richtlinie und dem Wunsch zur Minimierung der Elementanzahl eingehen müssen.</span><span class="sxs-lookup"><span data-stu-id="6395e-214">Note that there is sometimes a trade-off between this guidance and the desire to minimize element count.</span></span>

<span data-ttu-id="6395e-215">Verwenden Sie [**DebugSettings.IsOverdrawHeatMapEnabled**](https://msdn.microsoft.com/library/windows/apps/Hh701823) als visuelle Diagnose.</span><span class="sxs-lookup"><span data-stu-id="6395e-215">Use [**DebugSettings.IsOverdrawHeatMapEnabled**](https://msdn.microsoft.com/library/windows/apps/Hh701823) as a visual diagnostic.</span></span> <span data-ttu-id="6395e-216">Möglicherweise erkennen Sie, dass Objekte dargestellt werden, von denen Sie sich nicht wussten, dass sie in der Szene auftreten.</span><span class="sxs-lookup"><span data-stu-id="6395e-216">You might find objects being drawn that you didn't know were in the scene.</span></span>

### <a name="transparent-or-hidden-elements"></a><span data-ttu-id="6395e-217">Transparente oder ausgeblendeten Elemente</span><span class="sxs-lookup"><span data-stu-id="6395e-217">Transparent or hidden elements</span></span>

<span data-ttu-id="6395e-218">Wenn ein Element nicht angezeigt wird, da es transparent ist oder von anderen Elementen verdeckt wird, löschen Sie es einfach, wenn es nicht zum Layout beiträgt.</span><span class="sxs-lookup"><span data-stu-id="6395e-218">If an element isn't visible because it's transparent or hidden behind other elements, and it's not contributing to layout, then delete it.</span></span> <span data-ttu-id="6395e-219">Wenn das Element nicht in seinem visuellen Anfangszustand, aber in anderen visuellen Zuständen sichtbar ist, können Sie den Zustand mit „x:Load“ steuern oder [Visibility](https://msdn.microsoft.com/library/windows/apps/BR208992) auf den Wert **Collapsed** für das Element selbst festlegen und in den entsprechenden Zuständen in **Visible** ändern.</span><span class="sxs-lookup"><span data-stu-id="6395e-219">If the element is not visible in the initial visual state but it is visible in other visual states, then use x:Load to control its state or set [Visibility](https://msdn.microsoft.com/library/windows/apps/BR208992) to **Collapsed** on the element itself and change the value to **Visible** in the appropriate states.</span></span> <span data-ttu-id="6395e-220">Es gibt Ausnahmen von dieser Heuristik: In der Regel wird der Wert, den eine Eigenschaft in den meisten visuellen Zuständen aufweist, am besten lokal für das Element festgelegt.</span><span class="sxs-lookup"><span data-stu-id="6395e-220">There will be exceptions to this heuristic: in general, the value a property has in the majority of visual states is best set locally on the element.</span></span>

### <a name="composite-elements"></a><span data-ttu-id="6395e-221">Zusammengesetzte Elemente</span><span class="sxs-lookup"><span data-stu-id="6395e-221">Composite elements</span></span>

<span data-ttu-id="6395e-222">Verwenden Sie ein Verbundelement, anstatt mehrere Elemente übereinander zu stapeln, um einen Effekt zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="6395e-222">Use a composite element instead of layering multiple elements to create an effect.</span></span> <span data-ttu-id="6395e-223">In diesem Beispiel ist das Ergebnis eine zweifarbige Form, wobei die obere Hälfte schwarz (vom Hintergrund von [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704)) und die untere Hälfte grau ist (vom halbtransparenten weißen [Rectangle](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)-Objekt, das mit einer Alpha-Überblendung über den schwarzen Hintergrund von **Grid** gelegt wird).</span><span class="sxs-lookup"><span data-stu-id="6395e-223">In this example, the result is a two-toned shape where the top half is black (from the background of the [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704)) and the bottom half is gray (from the semi-transparent white [Rectangle](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) alpha-blended over the black background of the **Grid**).</span></span> <span data-ttu-id="6395e-224">Hier werden 150 % der Pixel gefüllt, die erforderlich sind, um das Ergebnis zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="6395e-224">Here, 150% of the pixels necessary to achieve the result are being filled.</span></span>

**<span data-ttu-id="6395e-225">Ineffizient</span><span class="sxs-lookup"><span data-stu-id="6395e-225">Inefficient.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Grid Background="Black">
    <Grid.RowDefinitions>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Rectangle Grid.Row="1" Fill="White" Opacity=".5"/>
</Grid>
```

**<span data-ttu-id="6395e-226">Effizient.</span><span class="sxs-lookup"><span data-stu-id="6395e-226">Efficient.</span></span>**

```xaml
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="*"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Rectangle Fill="Black"/>
    <Rectangle Grid.Row="1" Fill="#FF7F7F7F"/>
</Grid>
```

### <a name="layout-panels"></a><span data-ttu-id="6395e-227">Layoutpanels</span><span class="sxs-lookup"><span data-stu-id="6395e-227">Layout panels</span></span>

<span data-ttu-id="6395e-228">Ein Layoutpanel kann für zwei Zwecke verwendet werden – um einem Bereich einzufärben und um untergeordnete Elemente darzustellen.</span><span class="sxs-lookup"><span data-stu-id="6395e-228">A layout panel can have two purposes: to color an area, and to lay out child elements.</span></span> <span data-ttu-id="6395e-229">Wenn ein Element, das sich in der Z-Ordnung weiter hinten befindet, einem Bereich bereits eine Farbe zuweist, dann muss ein darüber befindliches Layoutpanel diesem Bereich keine Farbe zuweisen. Stattdessen kann es sich darauf konzentrieren, seine untergeordneten Elemente zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="6395e-229">If an element further back in z-order is already coloring an area then a layout panel in front does not need to paint that area: instead it can just focus on laying out its children.</span></span> <span data-ttu-id="6395e-230">Im Folgenden finden Sie ein Beispiel hierfür.</span><span class="sxs-lookup"><span data-stu-id="6395e-230">Here's an example.</span></span>

**<span data-ttu-id="6395e-231">Ineffizient</span><span class="sxs-lookup"><span data-stu-id="6395e-231">Inefficient.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<GridView Background="Blue">
    <GridView.ItemTemplate>
        <DataTemplate>
            <Grid Background="Blue"/>
        </DataTemplate>
    </GridView.ItemTemplate>
</GridView>
```

**<span data-ttu-id="6395e-232">Effizient</span><span class="sxs-lookup"><span data-stu-id="6395e-232">Efficient.</span></span>**

```xaml
<GridView Background="Blue">
    <GridView.ItemTemplate>
        <DataTemplate>
            <Grid/>
        </DataTemplate>
    </GridView.ItemTemplate>
</GridView>
```

<span data-ttu-id="6395e-233">Wenn für das [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704) Treffertests durchgeführt werden müssen, legen Sie für den Hintergrund einen transparenten Wert fest.</span><span class="sxs-lookup"><span data-stu-id="6395e-233">If the [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704) has to be hit-testable then set a background value of transparent on it.</span></span>

### <a name="borders"></a><span data-ttu-id="6395e-234">Umrandung</span><span class="sxs-lookup"><span data-stu-id="6395e-234">Borders</span></span>

<span data-ttu-id="6395e-235">Verwenden Sie ein [Border](https://msdn.microsoft.com/library/windows/apps/BR209253)-Element, um einen Rahmen um ein Objekt zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="6395e-235">Use a [Border](https://msdn.microsoft.com/library/windows/apps/BR209253) element to draw a border around an object.</span></span> <span data-ttu-id="6395e-236">In diesem Beispiel wird ein [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704) als provisorischer Rahmen für eine [TextBox](https://msdn.microsoft.com/library/windows/apps/BR209683) verwendet.</span><span class="sxs-lookup"><span data-stu-id="6395e-236">In this example, a [Grid](https://msdn.microsoft.com/library/windows/apps/BR242704) is used as a makeshift border around a [TextBox](https://msdn.microsoft.com/library/windows/apps/BR209683).</span></span> <span data-ttu-id="6395e-237">Allerdings werden alle Pixel in der Mitte der Zelle überzeichnet.</span><span class="sxs-lookup"><span data-stu-id="6395e-237">But all the pixels in the center cell are overdrawn.</span></span>

**<span data-ttu-id="6395e-238">Ineffizient</span><span class="sxs-lookup"><span data-stu-id="6395e-238">Inefficient.</span></span>**

```xaml
<!-- NOTE: EXAMPLE OF INEFFICIENT CODE; DO NOT COPY-PASTE. -->
<Grid Background="Blue" Width="300" Height="45">
    <Grid.RowDefinitions>
        <RowDefinition Height="5"/>
        <RowDefinition/>
        <RowDefinition Height="5"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="5"/>
        <ColumnDefinition/>
        <ColumnDefinition Width="5"/>
    </Grid.ColumnDefinitions>
    <TextBox Grid.Row="1" Grid.Column="1"></TextBox>
</Grid>
```

**<span data-ttu-id="6395e-239">Effizient.</span><span class="sxs-lookup"><span data-stu-id="6395e-239">Efficient.</span></span>**

```xaml
 <Border BorderBrush="Blue" BorderThickness="5" Width="300" Height="45">
     <TextBox/>
</Border>
```

### <a name="margins"></a><span data-ttu-id="6395e-240">Ränder</span><span class="sxs-lookup"><span data-stu-id="6395e-240">Margins</span></span>

<span data-ttu-id="6395e-241">Achten Sie auf die Ränder.</span><span class="sxs-lookup"><span data-stu-id="6395e-241">Be aware of margins.</span></span> <span data-ttu-id="6395e-242">Zwei benachbarte Elemente überlappen sich (möglicherweise versehentlich), wenn negative Ränder in die Rendergrenzen hineinreichen und eine Überzeichnung verursachen.</span><span class="sxs-lookup"><span data-stu-id="6395e-242">Two neighboring elements will overlap (possibly accidentally) if negative margins extend into another’s render bounds and cause overdrawing.</span></span>

### <a name="cache-static-content"></a><span data-ttu-id="6395e-243">Zwischenspeichern statischer Inhalte</span><span class="sxs-lookup"><span data-stu-id="6395e-243">Cache static content</span></span>

<span data-ttu-id="6395e-244">Eine andere Quelle für die Überzeichnung ist eine Form, die aus vielen überlappenden Elementen besteht.</span><span class="sxs-lookup"><span data-stu-id="6395e-244">Another source of overdrawing is a shape made from many overlapping elements.</span></span> <span data-ttu-id="6395e-245">Wenn Sie [CacheMode](https://msdn.microsoft.com/library/windows/apps/BR228084) für die [UIElement](https://msdn.microsoft.com/library/windows/apps/BR208911)-Klasse mit der Verbundform auf **BitmapCache** festlegen, rendert die Plattform das Element für eine Bitmap einmalig und verwendet dann diese Bitmap für jeden Frame (anstelle der Überzeichnung).</span><span class="sxs-lookup"><span data-stu-id="6395e-245">If you set [CacheMode](https://msdn.microsoft.com/library/windows/apps/BR228084) to **BitmapCache** on the [UIElement](https://msdn.microsoft.com/library/windows/apps/BR208911) that contains the composite shape then the platform renders the element to a bitmap once and then uses that bitmap each frame instead of overdrawing.</span></span>

**<span data-ttu-id="6395e-246">Ineffizient</span><span class="sxs-lookup"><span data-stu-id="6395e-246">Inefficient.</span></span>**

```xaml
<Canvas Background="White">
    <Ellipse Height="40" Width="40" Fill="Blue"/>
    <Ellipse Canvas.Left="21" Height="40" Width="40" Fill="Blue"/>
    <Ellipse Canvas.Top="13" Canvas.Left="10" Height="40" Width="40" Fill="Blue"/>
</Canvas>
```

![Venn-Diagramm mit drei farbigen Kreisen](images/solidvenn.png)

<span data-ttu-id="6395e-248">Das obige Bild ist das Ergebnis, aber hier folgt eine Karte der überzeichneten Bereiche.</span><span class="sxs-lookup"><span data-stu-id="6395e-248">The image above is the result, but here's a map of the overdrawn regions.</span></span> <span data-ttu-id="6395e-249">Ein dunkleres Rot deutet auf ein höheres Maß an Überzeichnung hin.</span><span class="sxs-lookup"><span data-stu-id="6395e-249">Darker red indicates higher amounts of overdraw.</span></span>

![Venn-Diagramm mit Überschneidungsbereichen](images/translucentvenn.png)

**<span data-ttu-id="6395e-251">Effizient</span><span class="sxs-lookup"><span data-stu-id="6395e-251">Efficient.</span></span>**

```xaml
<Canvas Background="White" CacheMode="BitmapCache">
    <Ellipse Height="40" Width="40" Fill="Blue"/>
    <Ellipse Canvas.Left="21" Height="40" Width="40" Fill="Blue"/>
    <Ellipse Canvas.Top="13" Canvas.Left="10" Height="40" Width="40" Fill="Blue"/>
</Canvas>
```

<span data-ttu-id="6395e-252">Beachten Sie die Verwendung von [CacheMode](https://msdn.microsoft.com/library/windows/apps/BR228084).</span><span class="sxs-lookup"><span data-stu-id="6395e-252">Note the use of [CacheMode](https://msdn.microsoft.com/library/windows/apps/BR228084).</span></span> <span data-ttu-id="6395e-253">Verwenden Sie dieses Verfahren nicht, wenn eine der Teilformen animiert ist, da der Bitmapcache wahrscheinlich bei jedem Frame neu generiert werden muss, was dem Zweck widerspricht.</span><span class="sxs-lookup"><span data-stu-id="6395e-253">Don't use this technique if any of the sub-shapes animate because the bitmap cache will likely need to be regenerated every frame, defeating the purpose.</span></span>

## <a name="use-xbf2"></a><span data-ttu-id="6395e-254">Verwendung von XBF2</span><span class="sxs-lookup"><span data-stu-id="6395e-254">Use XBF2</span></span>

<span data-ttu-id="6395e-255">Bei XBF2 handelt es sich um eine binäre Darstellung des XAML-Markups, die sämtliche Nachteile der Textanalyse zur Laufzeit vermeidet.</span><span class="sxs-lookup"><span data-stu-id="6395e-255">XBF2 is a binary representation of XAML markup that avoids all text-parsing costs at runtime.</span></span> <span data-ttu-id="6395e-256">Darüber hinaus optimiert sie den Binärcode für das Laden und die Strukturerstellung und ermöglicht die Verwendung von Fast-Path für XAML-Typen, um die Effizienz bei der Heap- und Objekterstellung (VSM, ResourceDictionary, Stile usw.) zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="6395e-256">It also optimizes your binary for load and tree creation, and allows "fast-path" for XAML types to improve heap and object creation costs, for example VSM, ResourceDictionary, Styles, and so on.</span></span> <span data-ttu-id="6395e-257">Dank vollständiger Abbildung im Speicher entsteht beim Laden und Lesen einer XAML-Seite keinerlei Heap-Bedarf.</span><span class="sxs-lookup"><span data-stu-id="6395e-257">It is completely memory-mapped so there is no heap footprint for loading and reading a XAML Page.</span></span> <span data-ttu-id="6395e-258">Des Weiteren verringert sich der Datenträgerbedarf gespeicherter XAML-Seiten in einem APPX-Element.</span><span class="sxs-lookup"><span data-stu-id="6395e-258">In addition, it reduces the disk footprint of stored XAML pages in an appx.</span></span> <span data-ttu-id="6395e-259">XBF2 zeichnet sich durch eine kompaktere Darstellung aus und kann den Datenträgerbedarf im Vergleich zu XAML/XBF1-Dateien um bis zu 50Prozent reduzieren.</span><span class="sxs-lookup"><span data-stu-id="6395e-259">XBF2 is a more compact representation and it can reduce disk footprint of comparative XAML/XBF1 files by up to 50%.</span></span> <span data-ttu-id="6395e-260">So wurde bei der integrierten Foto-App etwa eine Reduzierung um rund 60Prozent erreicht – von ehemals rund 1MB (XBF1-Ressourcen) auf ca. 400KB (XBF2-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="6395e-260">For example, the built-in Photos app saw around a 60% reduction after conversion to XBF2 dropping from around ~1mb of XBF1 assets to ~400kb of XBF2 assets.</span></span> <span data-ttu-id="6395e-261">Darüber hinaus wurden für Apps auch Verbesserungen bei CPU (15 bis 20Prozent) und Win32-Heap (10 bis 15Prozent) verzeichnet.</span><span class="sxs-lookup"><span data-stu-id="6395e-261">We have also seen apps benefit anywhere from 15 to 20% in CPU and 10 to 15% in Win32 heap.</span></span>

<span data-ttu-id="6395e-262">Integrierte XAML-Steuerelemente und vom Framework bereitgestellte Wörterbücher sind bereits vollständig XBF2-fähig.</span><span class="sxs-lookup"><span data-stu-id="6395e-262">XAML built-in controls and dictionaries that the framework provides are already fully XBF2-enabled.</span></span> <span data-ttu-id="6395e-263">Achten Sie bei Ihrer eigenen App darauf, dass Ihre Projektdatei mindestens „TargetPlatformVersion8.2“ deklariert.</span><span class="sxs-lookup"><span data-stu-id="6395e-263">For your own app, ensure that your project file declares TargetPlatformVersion 8.2 or later.</span></span>

<span data-ttu-id="6395e-264">Wenn Sie wissen möchten, ob Sie über XBF2 verfügen, öffnen Sie Ihre App in einem Binär-Editor. Falls das 12. und 13.Byte „00 02“ ist, haben Sie XBF2.</span><span class="sxs-lookup"><span data-stu-id="6395e-264">To check whether you have XBF2, open your app in a binary editor; the 12th and 13th bytes are 00 02 if you have XBF2.</span></span>

## <a name="related-articles"></a><span data-ttu-id="6395e-265">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="6395e-265">Related articles</span></span>

- [<span data-ttu-id="6395e-266">Bewährte Methoden für die Leistung Ihrer App beim Starten</span><span class="sxs-lookup"><span data-stu-id="6395e-266">Best practices for your app's startup performance</span></span>](best-practices-for-your-app-s-startup-performance.md)
- [<span data-ttu-id="6395e-267">Optimieren des XAML-Layouts</span><span class="sxs-lookup"><span data-stu-id="6395e-267">Optimize your XAML layout</span></span>](optimize-your-xaml-layout.md)
- [<span data-ttu-id="6395e-268">Optimieren der ListView- und GridView-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="6395e-268">ListView and GridView UI optimization</span></span>](optimize-gridview-and-listview.md)
- [<span data-ttu-id="6395e-269">Tools für Profilerstellung und Leistung</span><span class="sxs-lookup"><span data-stu-id="6395e-269">Tools for profiling and performance</span></span>](tools-for-profiling-and-performance.md)
