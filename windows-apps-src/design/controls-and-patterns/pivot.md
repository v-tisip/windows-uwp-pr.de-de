---
author: QuinnRadich
Description: The Pivot control enables touch-swiping between a small set of content sections.
title: Pivot
template: detail.hbs
ms.author: quradic
ms.date: 06/19/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: llongley
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 386fba3cec00de6c443daa60409fe3bb74621fa1
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5973815"
---
# <a name="pivot"></a><span data-ttu-id="ddf0d-103">Pivot</span><span class="sxs-lookup"><span data-stu-id="ddf0d-103">Pivot</span></span>

<span data-ttu-id="ddf0d-104">Das [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot) -Steuerelement kann zwischen einer kleinen Gruppe Inhaltsabschnitte Touch Wischen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-104">The [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot) control enables touch-swiping between a small set of content sections.</span></span>

> <span data-ttu-id="ddf0d-105">**Wichtige APIs**: [Pivot-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot), [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.NavigationView)</span><span class="sxs-lookup"><span data-stu-id="ddf0d-105">**Important APIs**: [Pivot class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot), [NavigationView class](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.NavigationView)</span></span>

## <a name="examples"></a><span data-ttu-id="ddf0d-106">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ddf0d-106">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="ddf0d-107">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="ddf0d-107">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="ddf0d-108">Wenn Sie die <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> -app installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Pivot">die app zu öffnen und das Pivot-Steuerelement in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-108">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Pivot">open the app and see the Pivot control in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="ddf0d-109">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="ddf0d-109">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="ddf0d-110">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="ddf0d-110">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="ddf0d-111">Das Pivot-Steuerelement, genau wie [NavigationView](navigationview.md), unterstreicht das ausgewählte Element.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-111">The Pivot control, just like [NavigationView](navigationview.md), underlines the selected item.</span></span>

![Standardfokus als Unterstrich des ausgewählten Headers](images/pivot_focus_selectedHeader.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="ddf0d-113">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="ddf0d-113">Is this the right control?</span></span>

<span data-ttu-id="ddf0d-114">Um allgemeine oberen Navigationsleiste und Registerkarten Muster zu erreichen, empfehlen wir die Verwendung von [NavigationView](navigationview.md), die automatisch an verschiedene Bildschirmgrößen anpasst und für eine umfassendere Anpassung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-114">To achieve common top navigation and tabs patterns, we recommend using [NavigationView](navigationview.md), which automatically adapts to different screen sizes and allows for greater customization.</span></span>

<span data-ttu-id="ddf0d-115">Jedoch, wenn die Navigation Touch-Wischen erforderlich ist, empfehlen wir die Verwendung Pivot.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-115">However, if your navigation requires touch-swiping, we recommend using Pivot.</span></span>

<span data-ttu-id="ddf0d-116">Die wichtigsten Unterschiede zwischen den Steuerelementen NavigationView und Pivot gibt das Standardverhalten Überlauf und die Navigation API:</span><span class="sxs-lookup"><span data-stu-id="ddf0d-116">The other key differences between the NavigationView and Pivot controls are the default overflow behavior and the navigation API:</span></span>

- <span data-ttu-id="ddf0d-117">Pivot-Karussells Überlauf, die Elemente, während NavigationView eine Dropdown-Menü Liste verwendet overflow, damit Benutzer alle Elemente sehen können.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-117">Pivot carousels overflow items, while NavigationView uses a menu dropdown overflow so that users can see all items.</span></span>
- <span data-ttu-id="ddf0d-118">Pivot steuert die Navigation zwischen Inhaltsabschnitte, während NavigationView mehr Kontrolle über Navigationsverhalten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-118">Pivot handles navigation between content sections, while NavigationView allows for more control over navigation behavior.</span></span>

## <a name="use-navigationview-instead-of-pivot"></a><span data-ttu-id="ddf0d-119">Pivot anstelle von NavigationView</span><span class="sxs-lookup"><span data-stu-id="ddf0d-119">Use NavigationView instead of Pivot</span></span>

<span data-ttu-id="ddf0d-120">Wenn Benutzeroberfläches Ihrer app das Pivot-Steuerelement verwendet, können Sie Pivot in NavigationView durch den folgenden Code konvertieren.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-120">If your app's UI uses the Pivot control, then you can convert Pivot to NavigationView with the code below.</span></span>

<span data-ttu-id="ddf0d-121">Dieser XAML-Code erstellt ein NavigationView mit 3 Inhaltsbereichen, wie im Beispiel Pivot in [ein Pivot-Steuerelement erstellen](#create-a-pivot-control).</span><span class="sxs-lookup"><span data-stu-id="ddf0d-121">This XAML creates a NavigationView with 3 sections of content, like the example Pivot in [Create a pivot control](#create-a-pivot-control).</span></span>

```xaml
<NavigationView x:Name="rootNavigationView" Header="Category Title"
 ItemInvoked="NavView_ItemInvoked">
    <NavigationView.MenuItems>
        <NavigationViewItem Content="Section 1" x:Name="Section1Content" />
        <NavigationViewItem Content="Section 2" x:Name="Section2Content" />
        <NavigationViewItem Content="Section 3" x:Name="Section3Content" />
    </NavigationView.MenuItems>
</NavigationView>

<Page x:Class="AppName.Section1Page">
    <TextBlock Text="Content of section 1."/>
</Page>

<Page x:Class="AppName.Section2Page">
    <TextBlock Text="Content of section 2."/>
</Page>

<Page x:Class="AppName.Section3Page">
    <TextBlock Text="Content of section 3."/>
</Page>
```

<span data-ttu-id="ddf0d-122">NavigationView bietet mehr Kontrolle über die Anpassung der Navigation und entsprechende Code-Behind erfordert.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-122">NavigationView provides more control over navigation customization and requires corresponding code-behind.</span></span> <span data-ttu-id="ddf0d-123">Um die oben genannten XAML begleiten, verwenden Sie die folgende Code-Behind-Datei:</span><span class="sxs-lookup"><span data-stu-id="ddf0d-123">To accompany the above XAML, use the following code-behind:</span></span>

```csharp
private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{
    FrameNavigationOptions navOptions = new FrameNavigationOptions();
    navOptions.TransitionInfoOverride = new SlideNavigationTransitionInfo() {
         SlideNavigationTransitionDirection=args.RecommendedNavigationTransitionInfo
    };

    navOptions.IsNavigationStackEnabled = False;

    switch (item.Name)
    {
        case "Section1Content":
            ContentFrame.NavigateToType(typeof(Section1Page), null, navOptions);
            break;

        case "Section2Content":
            ContentFrame.NavigateToType(typeof(Section2Page), null, navOptions);
            break;

        case "Section3Content":
            ContentFrame.NavigateToType(typeof(Section3Page), null, navOptions);
            break;
    }  
}
```

<span data-ttu-id="ddf0d-124">Dieser Code wird das Pivot-Steuerelement integrierte Navigationsfunktionalität, abzüglich der Touch-Wischen Erfahrung zwischen Inhaltsabschnitte imitiert.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-124">This code mimics the Pivot control's built-in navigation experience, minus the touch-swiping experience between content sections.</span></span> <span data-ttu-id="ddf0d-125">Wie Sie sehen können, könnten Sie einige Punkte, einschließlich der animierten Übergang, Navigation Parameter und Stapel Funktionen auch anpassen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-125">However, as you can see, you could also customize several points, including the animated transition, navigation parameters, and stack capabilities.</span></span>

## <a name="create-a-pivot-control"></a><span data-ttu-id="ddf0d-126">Erstellen eines Pivot-Steuerelements</span><span class="sxs-lookup"><span data-stu-id="ddf0d-126">Create a pivot control</span></span>

<span data-ttu-id="ddf0d-127">Dieser Code erstellt ein einfaches Pivotsteuerelement mit 3 Inhaltsbereichen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-127">This code creates a basic Pivot control with 3 sections of content.</span></span>

```xaml
<Pivot x:Name="rootPivot" Title="Category Title">
    <PivotItem Header="Section 1">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of section 1."/>
    </PivotItem>
    <PivotItem Header="Section 2">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of section 2."/>
    </PivotItem>
    <PivotItem Header="Section 3">
        <!--Pivot content goes here-->
        <TextBlock Text="Content of section 3."/>
    </PivotItem>
</Pivot>
```

### <a name="pivot-items"></a><span data-ttu-id="ddf0d-128">Pivot-Elemente</span><span class="sxs-lookup"><span data-stu-id="ddf0d-128">Pivot items</span></span>

<span data-ttu-id="ddf0d-129">Das Pivot-Steuerelement ist ein [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx), daher kann es eine Sammlung von Elementen jeden Typs enthalten.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-129">Pivot is an [ItemsControl](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.aspx), so it can contain a collection of items of any type.</span></span> <span data-ttu-id="ddf0d-130">Jedes zum Pivot-Steuerelement hinzugefügte Element, das nicht ausdrücklich ein [PivotItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivotitem.aspx)-Element ist, wird implizit in ein PivotItem eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-130">Any item you add to the Pivot that is not explicitly a [PivotItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivotitem.aspx) is implicitly wrapped in a PivotItem.</span></span> <span data-ttu-id="ddf0d-131">Da ein Pivot-Element häufig zum Navigieren zwischen Inhaltsseiten verwendet wird, ist es üblich, die Sammlung von [Elementen](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.items.aspx) direkt mit XAML-UI-Elementen zu füllen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-131">Because a Pivot is often used to navigate between pages of content, it's common to populate the [Items](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.items.aspx) collection directly with XAML UI elements.</span></span> <span data-ttu-id="ddf0d-132">Alternativ können Sie die Eigenschaft [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) auf eine Datenquelle festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-132">Or, you can set the [ItemsSource](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemssource.aspx) property to a data source.</span></span> <span data-ttu-id="ddf0d-133">In der ItemsSource gebundene Elemente können beliebigen Typs sein, wenn es sich jedoch nicht explizit um PivotItems handelt, müssen Sie eine [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx)- und eine [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.headertemplate.aspx)-Eigenschaft definieren, um festzulegen, wie die Elemente angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-133">Items bound in the ItemsSource can be of any type, but if they aren't explicitly PivotItems, you must define an [ItemTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.itemscontrol.itemtemplate.aspx) and [HeaderTemplate](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.headertemplate.aspx) to specify how the items are displayed.</span></span>

<span data-ttu-id="ddf0d-134">Mit der Eigenschaft [SelectedItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selecteditem.aspx) können Sie das aktive Element des Pivot-Steuerelements abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-134">You can use the [SelectedItem](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selecteditem.aspx) property to get or set the Pivot's active item.</span></span> <span data-ttu-id="ddf0d-135">Mit der Eigenschaft [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selectedindex.aspx) können Sie den Index des aktiven Elements abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-135">Use the [SelectedIndex](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.selectedindex.aspx) property to get or set the index of the active item.</span></span>

### <a name="pivot-headers"></a><span data-ttu-id="ddf0d-136">Pivotheader</span><span class="sxs-lookup"><span data-stu-id="ddf0d-136">Pivot headers</span></span>

<span data-ttu-id="ddf0d-137">Sie können die Eigenschaften [LeftHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.leftheader.aspx) und [RightHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.rightheader.aspx) verwenden, um weitere Steuerelemente zum Pivotheader hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-137">You can use the [LeftHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.leftheader.aspx) and [RightHeader](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.pivot.rightheader.aspx) properties to add other controls to the Pivot header.</span></span>

<span data-ttu-id="ddf0d-138">Sie können dem RightHeader des Pivot-Steuerelements z.B. eine [CommandBar](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/app-bars) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-138">For example, you can add a [CommandBar](https://docs.microsoft.com/en-us/windows/uwp/controls-and-patterns/app-bars) in the Pivot's RightHeader.</span></span>

```xaml
<Pivot>
    <Pivot.RightHeader>
        <CommandBar>
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

### <a name="pivot-interaction"></a><span data-ttu-id="ddf0d-139">Pivot-Interaktion</span><span class="sxs-lookup"><span data-stu-id="ddf0d-139">Pivot interaction</span></span>

<span data-ttu-id="ddf0d-140">Das Steuerelement erkennt die folgenden Touchgesteninteraktionen:</span><span class="sxs-lookup"><span data-stu-id="ddf0d-140">The control features these touch gesture interactions:</span></span>

- <span data-ttu-id="ddf0d-141">Durch Tippen auf den Header eines Pivotelements wird zum Abschnittsinhalt dieses Headers navigiert.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-141">Tapping on a pivot item header navigates to that header's section content.</span></span>
- <span data-ttu-id="ddf0d-142">Durch Wischen nach links oder rechts auf dem Header eines Pivotelements wird zum benachbarten Abschnitt navigiert.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-142">Swiping left or right on a pivot item header navigates to the adjacent section.</span></span>
- <span data-ttu-id="ddf0d-143">Durch Wischen nach links oder rechts auf einem Abschnittsinhalt wird zum benachbarten Abschnitt navigiert.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-143">Swiping left or right on section content navigates to the adjacent section.</span></span>

<span data-ttu-id="ddf0d-144">Das Steuerelement ist in zwei Modi verfügbar:</span><span class="sxs-lookup"><span data-stu-id="ddf0d-144">The control comes in two modes:</span></span>

**<span data-ttu-id="ddf0d-145">Stationär</span><span class="sxs-lookup"><span data-stu-id="ddf0d-145">Stationary</span></span>**

- <span data-ttu-id="ddf0d-146">Pivots werden nicht verschoben, wenn alle Pivotheader in den zulässigen Bereich passen.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-146">Pivots are stationary when all pivot headers fit within the allowed space.</span></span>
- <span data-ttu-id="ddf0d-147">Durch Tippen auf eine Pivotbeschriftung wird zur entsprechenden Seite navigiert. Das Pivot selbst wird jedoch nicht verschoben.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-147">Tapping on a pivot label navigates to the corresponding page, though the pivot itself will not move.</span></span> <span data-ttu-id="ddf0d-148">Das aktive Pivot wird hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-148">The active pivot is highlighted.</span></span>

**<span data-ttu-id="ddf0d-149">Karussell</span><span class="sxs-lookup"><span data-stu-id="ddf0d-149">Carousel</span></span>**

- <span data-ttu-id="ddf0d-150">Falls nicht alle Pivotheader in den verfügbaren Bereich passen, werden Pivots in einer Karussellansicht dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-150">Pivots carousel when all pivot headers don't fit within the allowed space.</span></span>
- <span data-ttu-id="ddf0d-151">Durch Tippen auf eine Pivotbeschriftung wird die entsprechende Seite aufgerufen, und die aktive Pivotbeschriftung rückt an die erste Position.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-151">Tapping a pivot label navigates to the corresponding page, and the active pivot label will carousel into the first position.</span></span>
- <span data-ttu-id="ddf0d-152">Pivotelemente in einer Karussellschleife wechseln vom letzten zum ersten Pivotabschnitt.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-152">Pivot items in a carousel loop from last to first pivot section.</span></span>

> <span data-ttu-id="ddf0d-153">**Hinweis** Pivotheader sollten in einer [10-Fuß-Umgebung](../devices/designing-for-tv.md) nicht in einer Karussellansicht dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-153">**Note** Pivot headers should not carousel in a [10ft environment](../devices/designing-for-tv.md).</span></span> <span data-ttu-id="ddf0d-154">Legen Sie die [IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot.IsHeaderItemsCarouselEnabled)-Eigenschaft auf **false** fest, wenn Ihre App auf der Xbox ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-154">Set the [IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot.IsHeaderItemsCarouselEnabled) property to **false** if your app will run on Xbox.</span></span>

## <a name="recommendations"></a><span data-ttu-id="ddf0d-155">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="ddf0d-155">Recommendations</span></span>

- <span data-ttu-id="ddf0d-156">Vermeiden Sie mehr als 5 Header bei Verwendung des Karussell-Modus (Roundtrip), da mehr als Schleifen verwirrend sein können.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-156">Avoid using more than 5 headers when using carousel (round-trip) mode, as looping more than 5 can become confusing.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="ddf0d-157">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="ddf0d-157">Get the sample code</span></span>

- <span data-ttu-id="ddf0d-158">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ddf0d-158">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="ddf0d-159">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ddf0d-159">Related topics</span></span>

- [<span data-ttu-id="ddf0d-160">Pivot-Klasse</span><span class="sxs-lookup"><span data-stu-id="ddf0d-160">Pivot class</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot)
- [<span data-ttu-id="ddf0d-161">Navigationsdesigngrundlagen</span><span class="sxs-lookup"><span data-stu-id="ddf0d-161">Navigation design basics</span></span>](../basics/navigation-basics.md)