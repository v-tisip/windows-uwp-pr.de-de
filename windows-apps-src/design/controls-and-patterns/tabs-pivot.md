---
author: serenaz
Description: Tabs and pivots enable users to navigate between frequently accessed content.
title: Registerkarten und Pivots
ms.assetid: 556BC70D-CF5D-4295-A655-D58163CC1824
label: Tabs and pivots
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: llongley
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 09e88fd070f7e7517e55d6f57563dd7608696770
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1675477"
---
# <a name="pivot-and-tabs"></a><span data-ttu-id="0631b-103">Pivot und Registerkarten</span><span class="sxs-lookup"><span data-stu-id="0631b-103">Pivot and tabs</span></span>



<span data-ttu-id="0631b-104">Das Pivot-Steuerelement und das verwandte Registerkartenmuster werden für die Navigation zwischen häufig genutzten verschiedenen Inhaltskategorien verwendet.</span><span class="sxs-lookup"><span data-stu-id="0631b-104">The Pivot control and related tabs pattern are used for navigating frequently accessed, distinct content categories.</span></span> <span data-ttu-id="0631b-105">Pivots ermöglichen die Navigation zwischen mindestens zwei Inhaltsbereichen und nutzen Textheader, um die verschiedenen Inhaltsabschnitte zu bezeichnen.</span><span class="sxs-lookup"><span data-stu-id="0631b-105">Pivots allow for navigation between two or more content panes and rely on text headers to label the different sections of content.</span></span>

> <span data-ttu-id="0631b-106">**Wichtige APIs**: [Pivot-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)</span><span class="sxs-lookup"><span data-stu-id="0631b-106">**Important APIs**: [Pivot class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)</span></span>

![Beispiel eines Pivot-Steuerelements](images/pivot_Hero_main.png)

<span data-ttu-id="0631b-108">Registerkarten stellen eine visuelle Variante eines Pivots dar, die eine Kombination aus Symbolen und Text oder nur Symbole verwenden, um Abschnittsinhalte zu gliedern.</span><span class="sxs-lookup"><span data-stu-id="0631b-108">Tabs are a visual variant of Pivot that use a combination of icons and text or just icons to articulate section content.</span></span> <span data-ttu-id="0631b-109">Registerkarten werden mit dem [Pivot](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.aspx)-Steuerelement erstellt.</span><span class="sxs-lookup"><span data-stu-id="0631b-109">Tabs are built using the [Pivot](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.aspx) control.</span></span> <span data-ttu-id="0631b-110">Das [Pivotbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619903) zeigt, wie das Pivot-Steuerelement an das Registerkartenmuster angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="0631b-110">The [Pivot sample](http://go.microsoft.com/fwlink/p/?LinkId=619903) shows how to customize the Pivot control into the tabs pattern.</span></span>

![Beispiel für Registerkartenmuster](images/tabs.png) 

## <a name="the-pivot-control"></a><span data-ttu-id="0631b-112">Das Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="0631b-112">The pivot control</span></span>

<span data-ttu-id="0631b-113">Wenn Sie eine App mit dem Pivot erstellen, sind einige wichtige Designelemente zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="0631b-113">When building an app with pivot, there are a few key design variables to consider.</span></span>

- **<span data-ttu-id="0631b-114">Headerbeschriftungen.</span><span class="sxs-lookup"><span data-stu-id="0631b-114">Header labels.</span></span>**  <span data-ttu-id="0631b-115">Header können über ein Symbol mit Text, nur über ein Symbol oder nur über Text verfügen.</span><span class="sxs-lookup"><span data-stu-id="0631b-115">Headers can have an icon with text, icon only, or text only.</span></span>
- **<span data-ttu-id="0631b-116">Headerausrichtung.</span><span class="sxs-lookup"><span data-stu-id="0631b-116">Header alignment.</span></span>**  <span data-ttu-id="0631b-117">Header können links ausgerichtet oder zentriert werden.</span><span class="sxs-lookup"><span data-stu-id="0631b-117">Headers can be left-justified or centered.</span></span>
- **<span data-ttu-id="0631b-118">Navigation auf oberster oder auf einer untergeordneten Ebene.</span><span class="sxs-lookup"><span data-stu-id="0631b-118">Top-level or sub-level navigation.</span></span>**  <span data-ttu-id="0631b-119">Pivots können für eine der Navigationsebenen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0631b-119">Pivots can be used for either level of navigation.</span></span> <span data-ttu-id="0631b-120">Optional kann die [Navigationsansicht](navigationview.md) als primäre Ebene dienen und das Pivot als sekundäre.</span><span class="sxs-lookup"><span data-stu-id="0631b-120">Optionally, [navigation view](navigationview.md) can serve as the primary level with pivot acting as secondary.</span></span>
- **<span data-ttu-id="0631b-121">Unterstützung für Touchbewegungen.</span><span class="sxs-lookup"><span data-stu-id="0631b-121">Touch gesture support.</span></span>**  <span data-ttu-id="0631b-122">Für Geräte, die Touchbewegungen unterstützen, können Sie zur Navigation zwischen Inhaltskategorien eine von zwei Interaktionen verwenden:</span><span class="sxs-lookup"><span data-stu-id="0631b-122">For devices that support touch gestures, you can use one of two interaction sets to navigate between content categories:</span></span>
    1. <span data-ttu-id="0631b-123">Tippen Sie auf einen Registerkarten-/Pivotheader, um zur gewünschten Kategorie zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="0631b-123">Tap on a tab/pivot header to navigate to that category.</span></span>
    2. <span data-ttu-id="0631b-124">Wischen Sie über dem Inhaltsbereich nach links oder rechts, um zur benachbarten Kategorie zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="0631b-124">Swipe left or right on the content area to navigate to the adjacent category.</span></span>

## <a name="examples"></a><span data-ttu-id="0631b-125">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0631b-125">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="0631b-126">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="0631b-126">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="0631b-127">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Pivot">die App zu öffnen und Pivot in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="0631b-127">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Pivot">open the app and see the Pivot in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="0631b-128">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="0631b-128">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="0631b-129">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="0631b-129">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="0631b-130">Pivot-Steuerelement auf dem Handy</span><span class="sxs-lookup"><span data-stu-id="0631b-130">Pivot control on phone.</span></span>

![Beispiel für ein Pivot](images/pivot_example.png)

<span data-ttu-id="0631b-132">Registerkartenmuster in der App „Alarm & Uhr“</span><span class="sxs-lookup"><span data-stu-id="0631b-132">Tabs pattern in the Alarms & Clock app.</span></span>

![Beispiel für ein Registerkartenmuster in „Alarm & Uhr“](images/tabs_alarms-and-clock.png)

## <a name="create-a-pivot-control"></a><span data-ttu-id="0631b-134">Erstellen eines Pivot-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="0631b-134">Create a pivot control</span></span>

<span data-ttu-id="0631b-135">Das [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)-Steuerelement enthält die in diesem Abschnitt beschriebenen grundlegenden Funktionen.</span><span class="sxs-lookup"><span data-stu-id="0631b-135">The [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot) control comes with the basic functionality described in this section.</span></span>

<span data-ttu-id="0631b-136">Dieser XAML-Code erzeugt ein grundlegendes Pivot-Steuerelement mit 3 Inhaltsbereichen.</span><span class="sxs-lookup"><span data-stu-id="0631b-136">This XAML creates a basic pivot control with 3 sections of content.</span></span>

```xaml
<Pivot x:Name="rootPivot" Title="Pivot Title">
    <PivotItem Header="Pivot Item 1">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 1."/>
    </PivotItem>
    <PivotItem Header="Pivot Item 2">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 2."/>
    </PivotItem>
    <PivotItem Header="Pivot Item 3">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of pivot item 3."/>
    </PivotItem>
</Pivot>
```

### <a name="pivot-items"></a><span data-ttu-id="0631b-137">Pivot-Elemente</span><span class="sxs-lookup"><span data-stu-id="0631b-137">Pivot items</span></span>

<span data-ttu-id="0631b-138">Das Pivot-Steuerelement ist ein [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx), daher kann es eine Sammlung von Elementen jeden Typs enthalten.</span><span class="sxs-lookup"><span data-stu-id="0631b-138">Pivot is an [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx), so it can contain a collection of items of any type.</span></span> <span data-ttu-id="0631b-139">Jedes zum Pivot-Steuerelement hinzugefügte Element, das nicht ausdrücklich ein [PivotItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivotitem.aspx)-Element ist, wird implizit in ein PivotItem eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="0631b-139">Any item you add to the Pivot that is not explicitly a [PivotItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivotitem.aspx) is implicitly wrapped in a PivotItem.</span></span> <span data-ttu-id="0631b-140">Da ein Pivot-Element häufig zum Navigieren zwischen Inhaltsseiten verwendet wird, ist es üblich, die Sammlung von [Elementen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.items.aspx) direkt mit XAML-UI-Elementen zu füllen.</span><span class="sxs-lookup"><span data-stu-id="0631b-140">Because a Pivot is often used to navigate between pages of content, it's common to populate the [Items](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.items.aspx) collection directly with XAML UI elements.</span></span> <span data-ttu-id="0631b-141">Alternativ können Sie die Eigenschaft [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) auf eine Datenquelle festlegen.</span><span class="sxs-lookup"><span data-stu-id="0631b-141">Or, you can set the [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a data source.</span></span> <span data-ttu-id="0631b-142">In der ItemsSource gebundene Elemente können beliebigen Typs sein, wenn es sich jedoch nicht explizit um PivotItems handelt, müssen Sie eine [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)- und eine [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.headertemplate.aspx)-Eigenschaft definieren, um festzulegen, wie die Elemente angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="0631b-142">Items bound in the ItemsSource can be of any type, but if they aren't explicitly PivotItems, you must define an [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) and [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.headertemplate.aspx) to specify how the items are displayed.</span></span>

<span data-ttu-id="0631b-143">Mit der Eigenschaft [SelectedItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selecteditem.aspx) können Sie das aktive Element des Pivot-Steuerelements abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="0631b-143">You can use the [SelectedItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selecteditem.aspx) property to get or set the Pivot's active item.</span></span> <span data-ttu-id="0631b-144">Mit der Eigenschaft [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selectedindex.aspx) können Sie den Index des aktiven Elements abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="0631b-144">Use the [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selectedindex.aspx) property to get or set the index of the active item.</span></span>

### <a name="pivot-headers"></a><span data-ttu-id="0631b-145">Pivotheader</span><span class="sxs-lookup"><span data-stu-id="0631b-145">Pivot headers</span></span>

<span data-ttu-id="0631b-146">Sie können die Eigenschaften [LeftHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.leftheader.aspx) und [RightHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.rightheader.aspx) verwenden, um weitere Steuerelemente zum Pivotheader hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0631b-146">You can use the [LeftHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.leftheader.aspx) and [RightHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.rightheader.aspx) properties to add other controls to the Pivot header.</span></span>

<span data-ttu-id="0631b-147">Sie können dem RightHeader des Pivot-Steuerelements z.B. eine [CommandBar](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/app-bars) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0631b-147">For example, you can add a [CommandBar](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/app-bars) in the Pivot's RightHeader.</span></span>

![Beispiel für eine Befehlsleiste im rechten Header des Pivotsteuerelements](images/PivotHeader.png)

```xaml
<Pivot>
    <Pivot.RightHeader>
        <CommandBar OverflowButtonVisibility="Collapsed" Background="Transparent">
                <AppBarButton Icon="Add"/>
                <AppBarSeparator/>
                <AppBarButton Icon="Edit"/>
                <AppBarButton Icon="Delete"/>
                <AppBarSeparator/>
                <AppBarButton Icon="Save"/>
        </CommandBar>
    </Pivot.RightHeader>
</Pivot>
```

### <a name="pivot-interaction"></a><span data-ttu-id="0631b-149">Pivot-Interaktion</span><span class="sxs-lookup"><span data-stu-id="0631b-149">Pivot interaction</span></span>

<span data-ttu-id="0631b-150">Das Steuerelement erkennt die folgenden Touchgesteninteraktionen:</span><span class="sxs-lookup"><span data-stu-id="0631b-150">The control features these touch gesture interactions:</span></span>

-   <span data-ttu-id="0631b-151">Durch Tippen auf den Header eines Pivotelements wird zum Abschnittsinhalt dieses Headers navigiert.</span><span class="sxs-lookup"><span data-stu-id="0631b-151">Tapping on a pivot item header navigates to that header's section content.</span></span>
-   <span data-ttu-id="0631b-152">Durch Wischen nach links oder rechts auf dem Header eines Pivotelements wird zum benachbarten Abschnitt navigiert.</span><span class="sxs-lookup"><span data-stu-id="0631b-152">Swiping left or right on a pivot item header navigates to the adjacent section.</span></span>
-   <span data-ttu-id="0631b-153">Durch Wischen nach links oder rechts auf einem Abschnittsinhalt wird zum benachbarten Abschnitt navigiert.</span><span class="sxs-lookup"><span data-stu-id="0631b-153">Swiping left or right on section content navigates to the adjacent section.</span></span>

![Beispiel für eine Wischbewegung nach links auf dem Abschnittsinhalt](images/pivot_w_hand.png)

<span data-ttu-id="0631b-155">Das Steuerelement ist in zwei Modi verfügbar:</span><span class="sxs-lookup"><span data-stu-id="0631b-155">The control comes in two modes:</span></span>

**<span data-ttu-id="0631b-156">Stationär</span><span class="sxs-lookup"><span data-stu-id="0631b-156">Stationary</span></span>**

-   <span data-ttu-id="0631b-157">Pivots werden nicht verschoben, wenn alle Pivotheader in den zulässigen Bereich passen.</span><span class="sxs-lookup"><span data-stu-id="0631b-157">Pivots are stationary when all pivot headers fit within the allowed space.</span></span>
-   <span data-ttu-id="0631b-158">Durch Tippen auf eine Pivotbeschriftung wird zur entsprechenden Seite navigiert. Das Pivot selbst wird jedoch nicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="0631b-158">Tapping on a pivot label navigates to the corresponding page, though the pivot itself will not move.</span></span> <span data-ttu-id="0631b-159">Das aktive Pivot wird hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="0631b-159">The active pivot is highlighted.</span></span>

**<span data-ttu-id="0631b-160">Karussell</span><span class="sxs-lookup"><span data-stu-id="0631b-160">Carousel</span></span>**

-   <span data-ttu-id="0631b-161">Falls nicht alle Pivotheader in den verfügbaren Bereich passen, werden Pivots in einer Karussellansicht dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0631b-161">Pivots carousel when all pivot headers don't fit within the allowed space.</span></span>
-   <span data-ttu-id="0631b-162">Durch Tippen auf eine Pivotbeschriftung wird die entsprechende Seite aufgerufen, und die aktive Pivotbeschriftung rückt an die erste Position.</span><span class="sxs-lookup"><span data-stu-id="0631b-162">Tapping a pivot label navigates to the corresponding page, and the active pivot label will carousel into the first position.</span></span>
-   <span data-ttu-id="0631b-163">Pivotelemente in einer Karussellschleife wechseln vom letzten zum ersten Pivotabschnitt.</span><span class="sxs-lookup"><span data-stu-id="0631b-163">Pivot items in a carousel loop from last to first pivot section.</span></span>

> <span data-ttu-id="0631b-164">**Hinweis** Pivotheader sollten in einer [10-Fuß-Umgebung](../devices/designing-for-tv.md) nicht in einer Karussellansicht dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0631b-164">**Note** Pivot headers should not carousel in a [10ft environment](../devices/designing-for-tv.md).</span></span> <span data-ttu-id="0631b-165">Legen Sie die [IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot.IsHeaderItemsCarouselEnabled)-Eigenschaft auf **false** fest, wenn Ihre App auf der Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0631b-165">Set the [IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot.IsHeaderItemsCarouselEnabled) property to **false** if your app will run on Xbox.</span></span>

### <a name="pivot-focus"></a><span data-ttu-id="0631b-166">Pivotfokus</span><span class="sxs-lookup"><span data-stu-id="0631b-166">Pivot focus</span></span>

<span data-ttu-id="0631b-167">Der Tastaturfokus wird bei einem Pivotheader standardmäßig mit einem Unterstrich dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0631b-167">By default, keyboard focus on a pivot header is represented with an underline.</span></span>

![Standardfokus als Unterstrich des ausgewählten Headers](images/pivot_focus_selectedHeader.png)

<span data-ttu-id="0631b-169">Apps, die über ein benutzerdefiniertes Pivot verfügen und den Unterstrich in visuelle Objekte zur Headerauswahl integrieren, können die [HeaderFocusVisualPlacement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pivot.HeaderFocusVisualPlacement)-Eigenschaft verwenden, um den Standardwert zu ändern.</span><span class="sxs-lookup"><span data-stu-id="0631b-169">Apps that have customized Pivot and incorporate the underline into header selection visuals can use the [HeaderFocusVisualPlacement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pivot.HeaderFocusVisualPlacement) property to change the default.</span></span> <span data-ttu-id="0631b-170">Wenn `HeaderFocusVisualPlacement="ItemHeaders"`, wird der Fokus um den gesamten Headerbereich gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="0631b-170">When `HeaderFocusVisualPlacement="ItemHeaders"`, focus will be drawn around the entire header panel.</span></span>

![Bei der ItemsHeader-Option wird das Fokusrechteck um alle Pivotheader gezeichnet.](images/pivot_focus_headers.png)

## <a name="recommendations"></a><span data-ttu-id="0631b-172">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="0631b-172">Recommendations</span></span>

- <span data-ttu-id="0631b-173">Die Ausrichtung der Registerkarten-/Pivotheader sollte auf der Bildschirmgröße basieren.</span><span class="sxs-lookup"><span data-stu-id="0631b-173">Base the alignment of tab/pivot headers on screen size.</span></span> <span data-ttu-id="0631b-174">Bei Bildschirmbreiten unter 720 epx ist die Zentrierung in der Regel besser geeignet. Bei Bildschirmbreiten über 720 epx ist in den meisten Fällen die Linksausrichtung empfehlenswert.</span><span class="sxs-lookup"><span data-stu-id="0631b-174">For screen widths below 720 epx, center-aligning usually works better, while left-aligning for screen widths above 720 epx is recommended in most cases.</span></span>
- <span data-ttu-id="0631b-175">Vermeiden Sie mehr als 5 Header bei Verwendung des Karussell-Modus (Roundtrip), da mehr als Schleifen verwirrend sein können.</span><span class="sxs-lookup"><span data-stu-id="0631b-175">Avoid using more than 5 headers when using carousel (round-trip) mode, as looping more than 5 can become confusing.</span></span>
- <span data-ttu-id="0631b-176">Verwenden Sie das Registerkartenmuster nur, wenn Ihre Pivotelemente unterschiedliche Symbole besitzen.</span><span class="sxs-lookup"><span data-stu-id="0631b-176">Use the tabs pattern only if your pivot items have distinct icons.</span></span>
- <span data-ttu-id="0631b-177">Fügen Sie Text in Pivotelementheader ein, damit Benutzer die Bedeutung der einzelnen Pivotabschnitte verstehen.</span><span class="sxs-lookup"><span data-stu-id="0631b-177">Include text in pivot item headers to help users understand the meaning of each pivot section.</span></span> <span data-ttu-id="0631b-178">Symbole sind nicht unbedingt für alle Benutzer selbsterklärend.</span><span class="sxs-lookup"><span data-stu-id="0631b-178">Icons are not necessarily self-explanatory to all users.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="0631b-179">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="0631b-179">Get the sample code</span></span>

- <span data-ttu-id="0631b-180">[Pivotbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619903) – Veranschaulicht, wie das Pivot-Steuerelement an das Registerkartenmuster angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="0631b-180">[Pivot sample](http://go.microsoft.com/fwlink/p/?LinkId=619903) - Demonstrates how to customize the Pivot control into the tabs pattern.</span></span>
- <span data-ttu-id="0631b-181">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0631b-181">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="0631b-182">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0631b-182">Related topics</span></span>

- [<span data-ttu-id="0631b-183">Pivot-Klasse</span><span class="sxs-lookup"><span data-stu-id="0631b-183">Pivot class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)
- [<span data-ttu-id="0631b-184">Navigationsdesigngrundlagen</span><span class="sxs-lookup"><span data-stu-id="0631b-184">Navigation design basics</span></span>](../basics/navigation-basics.md)
