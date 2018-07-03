---
author: serenaz
Description: Control that provides top-level app navigation with an automatically adapting, collapsible left navigation menu
title: Navigationsansicht
ms.assetid: ''
label: Navigation view
template: detail.hbs
ms.author: sezhen
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: vasriram
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: c7817bf7ff60a52ea48c988bdebd6d4d2eeacdb7
ms.sourcegitcommit: 618741673a26bd718962d4b8f859e632879f9d61
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "1992149"
---
# <a name="navigation-view"></a><span data-ttu-id="11ebe-103">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="11ebe-103">Navigation view</span></span>

<span data-ttu-id="11ebe-104">Das Navigationsansicht-Steuerelement bietet über ein reduzierbares Navigationsmenü ein allgemeines vertikales Layout für App-Bereiche auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="11ebe-104">The navigation view control provides a collapsible navigation menu for top-level navigation in your app.</span></span> <span data-ttu-id="11ebe-105">Dieses Steuerelement dient zur Implementierung des Navigationsbereichsmusters oder Hamburger-Menü-Musters, wobei die Anordnung automatisch an verschiedene Fenstergrößen des Bereichs angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-105">This control implements the nav pane, or hamburger menu, pattern and automatically adapts the pane's display mode to different window sizes.</span></span>

> <span data-ttu-id="11ebe-106">**Wichtige APIs**: [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode-Enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)</span><span class="sxs-lookup"><span data-stu-id="11ebe-106">**Important APIs**: [NavigationView class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)</span></span>

![Beispiel für NavigationView](images/navview_wireframe.png)

## <a name="video-summary"></a><span data-ttu-id="11ebe-108">Video-Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="11ebe-108">Video summary</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Windows/Windows-Developer-Day-Fall-Creators-Update/WinDev010/player]

## <a name="is-this-the-right-control"></a><span data-ttu-id="11ebe-109">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="11ebe-109">Is this the right control?</span></span>

<span data-ttu-id="11ebe-110">NavigationView eignet sich gut für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="11ebe-110">NavigationView works well for:</span></span>

-  <span data-ttu-id="11ebe-111">Viele Navigationselementen auf oberster Ebene, die einen ähnlichen Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-111">Many top-level navigation items of a similar type.</span></span> <span data-ttu-id="11ebe-112">(Dies kann beispielsweise eine Sport-App mit Kategorien wie Football, Baseball, Basketball, Fußball usw. sein.)</span><span class="sxs-lookup"><span data-stu-id="11ebe-112">(For example, a sports app with categories like Football, Baseball, Basketball, Soccer, and so on.)</span></span>
-  <span data-ttu-id="11ebe-113">Eine mittlere bis hohe Zahl (5-10) an Navigationskategorien der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="11ebe-113">A medium-to-high number (5-10) of top-level navigational categories.</span></span>
-  <span data-ttu-id="11ebe-114">Bereitstellen einer konsistenten Navigationsumgebung.</span><span class="sxs-lookup"><span data-stu-id="11ebe-114">Providing a consistent navigational experience.</span></span> <span data-ttu-id="11ebe-115">Der Bereich sollte nur Navigationselemente, keine Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="11ebe-115">The pane should include only navigational elements, not actions.</span></span>
-  <span data-ttu-id="11ebe-116">Sparen von Platz auf dem Bildschirm von kleineren Fenstern.</span><span class="sxs-lookup"><span data-stu-id="11ebe-116">Preserving screen real estate of smaller windows.</span></span>

<span data-ttu-id="11ebe-117">NavigationView ist nur eine von mehreren Navigationselementen, die Ihnen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-117">NavigationView is just one of several navigation elements you can use.</span></span> <span data-ttu-id="11ebe-118">Weitere Informationen zu anderen Navigationsmustern und -Elementen finden Sie unter [Navigationsdesigngrundlagen](../basics/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="11ebe-118">To learn more about other navigation patterns and elements, see [Navigation design basics](../basics/navigation-basics.md).</span></span>

<span data-ttu-id="11ebe-119">Das NavigationView-Steuerelement verfügt über viele integrierte Verhaltensweisen, die das einfache Navigationsbereichsmuster implementieren.</span><span class="sxs-lookup"><span data-stu-id="11ebe-119">The NavigationView control has many built-in behaviors that implement the simple nav pane pattern.</span></span> <span data-ttu-id="11ebe-120">Wenn die Navigation komplexeres Verhalten erfordert, das von NavigationView nicht unterstützt wird, können Sie stattdessen das [Master/Details](master-details.md)-Muster verwenden.</span><span class="sxs-lookup"><span data-stu-id="11ebe-120">If your navigation requires more complex behavior that is not supported by NavigationView, then you might want to consider the [Master/details](master-details.md) pattern instead.</span></span>

## <a name="examples"></a><span data-ttu-id="11ebe-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="11ebe-121">Examples</span></span>
<table>
<th align="left"><span data-ttu-id="11ebe-122">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="11ebe-122">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="11ebe-123">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die App zu öffnen und NavigationView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="11ebe-123">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/NavigationView">open the app and see the NavigationView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="11ebe-124">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="11ebe-124">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="11ebe-125">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="11ebe-125">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="navigationview-sections"></a><span data-ttu-id="11ebe-126">Abschnitte von NavigationView</span><span class="sxs-lookup"><span data-stu-id="11ebe-126">NavigationView sections</span></span>

![Abschnitte von NavigationView](images/navview_sections.png)

### <a name="pane"></a><span data-ttu-id="11ebe-128">Bereich</span><span class="sxs-lookup"><span data-stu-id="11ebe-128">Pane</span></span>

<span data-ttu-id="11ebe-129">Mit der integrierten Navigationsschaltfläche („Hamburger“-Schaltfläche) können Benutzer den Bereich öffnen und schließen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-129">The built-in navigation ("hamburger") button lets users open and close the pane.</span></span> <span data-ttu-id="11ebe-130">Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.</span><span class="sxs-lookup"><span data-stu-id="11ebe-130">On larger app windows when the pane is open, you may choose to hide this button using the [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) property.</span></span> <span data-ttu-id="11ebe-131">Bei der Beschriftung neben der Hamburger-Schaltfläche handelt es sich um die [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="11ebe-131">The text label adjacent to the hamburger is the [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) property.</span></span>

<span data-ttu-id="11ebe-132">Die integrierte Schaltfläche „Zurück“ wird in der oberen linken Ecke des Bereichs angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-132">The built-in back button appears in the top left-hand corner in the pane.</span></span> <span data-ttu-id="11ebe-133">Das NavigationView-Steuerelement fügt dem Zurück-Stapel nicht automatisch Inhalte hinzu, weitere Informationen zum Aktivieren der Rückwärtsnavigation finden Sie jedoch im Abschnitt [rückwärts Navigation](#backwards-navigation).</span><span class="sxs-lookup"><span data-stu-id="11ebe-133">The NavigationView control does not automatically add content to the back stack, but to enable backwards navigation, see the [backwards navigation](#backwards-navigation) section.</span></span>

<span data-ttu-id="11ebe-134">Der NavigationView-Bereich kann auch Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="11ebe-134">The NavigationView pane also can contain:</span></span>

- <span data-ttu-id="11ebe-135">Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren</span><span class="sxs-lookup"><span data-stu-id="11ebe-135">Navigation items, in the form of [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), for navigating to specific pages</span></span>
- <span data-ttu-id="11ebe-136">Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren</span><span class="sxs-lookup"><span data-stu-id="11ebe-136">Separators, in the form of [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), for grouping navigation items</span></span>
- <span data-ttu-id="11ebe-137">Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen</span><span class="sxs-lookup"><span data-stu-id="11ebe-137">Headers, in the form of [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), for labeling groups of items</span></span>
- <span data-ttu-id="11ebe-138">Eine optionale [AutoSuggestBox](auto-suggest-box.md) für die Suche auf App-Ebene</span><span class="sxs-lookup"><span data-stu-id="11ebe-138">An optional [AutoSuggestBox](auto-suggest-box.md) to allow for app-level search</span></span>
- <span data-ttu-id="11ebe-139">Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md).</span><span class="sxs-lookup"><span data-stu-id="11ebe-139">An optional entry point for [app settings](../app-settings/app-settings-and-data.md).</span></span> <span data-ttu-id="11ebe-140">Verwenden Sie zum Ausblenden des Einstellungselements die Eigenschaft [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible)</span><span class="sxs-lookup"><span data-stu-id="11ebe-140">To hide the settings item, use the [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) property</span></span>
- <span data-ttu-id="11ebe-141">Freier Inhalt in der Fußzeile des Bereichs beim Hinzufügen zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter)-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11ebe-141">Free-form content in the pane’s footer, when added to the [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) property</span></span>

#### <a name="visual-style"></a><span data-ttu-id="11ebe-142">Visueller Stil</span><span class="sxs-lookup"><span data-stu-id="11ebe-142">Visual style</span></span>

<span data-ttu-id="11ebe-143">NavigationView-Elemente unterstützen die Ansichtszustände „Ausgewählt“, „Deaktiviert“, „Zeiger über“, „Gedrückt“ und „Fokussiert“.</span><span class="sxs-lookup"><span data-stu-id="11ebe-143">NavigationView items have support for selected, disabled, pointer over, pressed, and focused visual states.</span></span>

![Zustände von NavigationView-Elementen: deaktiviert, Zeiger über, gedrückt und fokussiert](images/navview_item-states.png)

<span data-ttu-id="11ebe-145">Wenn Hardware- und Softwareanforderungen erfüllt sind, verwendet NavigationView in seinem Bereich automatisch das neue [Acryl-Material](../style/acrylic.md) und [Reveal-highlight](../style/reveal.md).</span><span class="sxs-lookup"><span data-stu-id="11ebe-145">When hardware and software requirements are met, NavigationView automatically uses the new [Acrylic material](../style/acrylic.md) and [Reveal highlight](../style/reveal.md) in its pane.</span></span>

### <a name="header"></a><span data-ttu-id="11ebe-146">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="11ebe-146">Header</span></span>

<span data-ttu-id="11ebe-147">Der Kopfzeilenbereich ist vertikal an der Navigationsschaltfläche ausgerichtet und hat eine feste Höhe von 52Pixel.</span><span class="sxs-lookup"><span data-stu-id="11ebe-147">The header area is vertically aligned with the navigation button and has a fixed height of 52 px.</span></span> <span data-ttu-id="11ebe-148">Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="11ebe-148">Its purpose is to hold the page title of the selected nav category.</span></span> <span data-ttu-id="11ebe-149">Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="11ebe-149">The header is docked to the top of the page and acts as a scroll clipping point for the content area.</span></span>

<span data-ttu-id="11ebe-150">Die Kopfzeile muss sichtbar sein, wenn sich die Navigationsansicht im minimierten Modus befindet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-150">The header must be visible when NavigationView is in Minimal mode.</span></span> <span data-ttu-id="11ebe-151">Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="11ebe-151">You may choose to hide the header in other modes, which are used on larger window widths.</span></span> <span data-ttu-id="11ebe-152">Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="11ebe-152">To do so, set the [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) property to **false**.</span></span>

### <a name="content"></a><span data-ttu-id="11ebe-153">Inhalt</span><span class="sxs-lookup"><span data-stu-id="11ebe-153">Content</span></span>

<span data-ttu-id="11ebe-154">Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-154">The content area is where most of the information for the selected nav category is displayed.</span></span> 

<span data-ttu-id="11ebe-155">Wir empfehlen, Ränder für Ihren Inhaltsbereich auf 12Pixel festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24Pixel.</span><span class="sxs-lookup"><span data-stu-id="11ebe-155">We recommend 12px margins for your content area when NavigationView is in Minimal mode and 24px margins otherwise.</span></span>

## <a name="navigationview-display-modes"></a><span data-ttu-id="11ebe-156">Anzeigemodi für NavigationView</span><span class="sxs-lookup"><span data-stu-id="11ebe-156">NavigationView display modes</span></span>
<span data-ttu-id="11ebe-157">Der Navigationsansichtsbereich kann offen oder geschlossen sein und verfügt über drei Optionen für Anzeigemodi:</span><span class="sxs-lookup"><span data-stu-id="11ebe-157">The NavigationView pane can be open or closed, and has three display mode options:</span></span>
-  <span data-ttu-id="11ebe-158">**Minimiert** Nur die „Hamburger“-Schaltfläche bleibt fest, während der Bereich nach Bedarf ein- und ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-158">**Minimal** Only the hamburger button remains fixed while the pane shows and hides as needed.</span></span>
-  <span data-ttu-id="11ebe-159">**Kompakt** Der Bereich wird als schmaler Streifen angezeigt, der zur vollen Breite erweitert werden kann.</span><span class="sxs-lookup"><span data-stu-id="11ebe-159">**Compact** The pane always shows as a narrow sliver which can be opened to full width.</span></span>
-  <span data-ttu-id="11ebe-160">**Erweitert** Der Bereich wird neben dem Inhalt geöffnet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-160">**Expanded** The pane is open alongside the content.</span></span> <span data-ttu-id="11ebe-161">Beim Schließen durch Aktivieren der „Hamburger“-Schaltfläche wird die Breite zu einem schmalen Streifen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-161">When closed by activating the hamburger button, the pane's width becomes a narrow sliver.</span></span>

<span data-ttu-id="11ebe-162">In der Standardeinstellung wählt das System je nach Größe des Bildschirmbereichs, der für das Steuerelement verfügbar ist, automatisch den optimalen Anzeigemodus aus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-162">By default, the system automatically selects the optimal display mode based on the amount of screen space available to the control.</span></span> <span data-ttu-id="11ebe-163">(Sie können diese Einstellung [überschreiben](#overriding-the-default-adaptive-behavior).)</span><span class="sxs-lookup"><span data-stu-id="11ebe-163">(You can [override](#overriding-the-default-adaptive-behavior) this setting.)</span></span>

### <a name="minimal"></a><span data-ttu-id="11ebe-164">Minimiert</span><span class="sxs-lookup"><span data-stu-id="11ebe-164">Minimal</span></span>

![NavigationView im minimierten Modus mit geschlossenem und geöffnetem Bereich](images/navview_minimal.png)

-  <span data-ttu-id="11ebe-166">Ist der Bereich geschlossen, wird er standardmäßig ausgeblendet, und es wird nur die Navigationsschaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-166">When closed, the pane is hidden by default, with only the nav button visible.</span></span>
-  <span data-ttu-id="11ebe-167">Bietet On-Demand-Navigation, die Platz auf dem Bildschirm spart.</span><span class="sxs-lookup"><span data-stu-id="11ebe-167">Provides on-demand navigation that conserves screen real estate.</span></span> <span data-ttu-id="11ebe-168">Ideal für Apps auf Smartphones und Tablets.</span><span class="sxs-lookup"><span data-stu-id="11ebe-168">Ideal for apps on phones and phablets.</span></span>
-  <span data-ttu-id="11ebe-169">Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-169">Pressing the nav button opens and closes the pane, which draws as an overlay above the header and content.</span></span> <span data-ttu-id="11ebe-170">Inhalt wird nicht dynamisch umgebrochen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-170">Content does not reflow.</span></span>
-  <span data-ttu-id="11ebe-171">Im geöffneten Zustand stellt er einen vorübergehenden Bereich dar, der durch eine Geste zum einfachen Ausblenden wie Treffen einer Auswahl, Drücken der Zurück-Schaltfläche oder Tippen außerhalb des Bereichs geschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="11ebe-171">When open, the pane is transient and can be closed with a light dismiss gesture such as making a selection, pressing the back button, or tapping outside the pane.</span></span>
-  <span data-ttu-id="11ebe-172">Das ausgewählte Element wird angezeigt, wenn die Überlagerung des Bereichs geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-172">The selected item becomes visible when the pane’s overlay opens.</span></span>
-  <span data-ttu-id="11ebe-173">Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des geöffneten Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).</span><span class="sxs-lookup"><span data-stu-id="11ebe-173">When requirements are met, the open pane’s background is [in-app acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="11ebe-174">NavigationView befindet sich standardmäßig im minimierten Modus, wenn die gesamte Breite kleiner oder gleich 640Pixel ist.</span><span class="sxs-lookup"><span data-stu-id="11ebe-174">By default, NavigationView is in Minimal mode when its overall width is less than or equal to 640px.</span></span>

### <a name="compact"></a><span data-ttu-id="11ebe-175">Kompakt</span><span class="sxs-lookup"><span data-stu-id="11ebe-175">Compact</span></span>

![NavigationView im kompakten Modus mit geschlossenem und geöffnetem Bereich](images/navview_compact.png)

-  <span data-ttu-id="11ebe-177">Ist der Bereich geschlossen, werden ein vertikaler Streifen des Bereichs nur mit Symbolen sowie die Navigationsschaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-177">When closed, a vertical sliver of the pane showing only icons and the nav button is visible.</span></span>
-  <span data-ttu-id="11ebe-178">Zeigen die ausgewählte Position an, während sie nur wenig Platz auf dem Bildschirm belegen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-178">Provides some indication of the selected location while using a small amount of screen real estate.</span></span>
-  <span data-ttu-id="11ebe-179">Dieser Modus ist besser für mittelgroße Bildschirme wie Tablets und [10-Fuß-Umgebungen](../devices/designing-for-tv.md) geeignet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-179">This mode is better suited for medium screens like tablets and [10-foot experiences](../devices/designing-for-tv.md).</span></span>
-  <span data-ttu-id="11ebe-180">Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-180">Pressing the nav button opens and closes the pane, which draws as an overlay above the header and content.</span></span> <span data-ttu-id="11ebe-181">Inhalt wird nicht umgebrochen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-181">Content does not reflow.</span></span>
-  <span data-ttu-id="11ebe-182">Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="11ebe-182">The Header is not required and can be hidden to give Content more vertical space.</span></span>
-  <span data-ttu-id="11ebe-183">Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich der Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-183">The selected item shows a visual indicator to highlight where the user is in the navigation tree.</span></span>
-  <span data-ttu-id="11ebe-184">Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).</span><span class="sxs-lookup"><span data-stu-id="11ebe-184">When requirements are met, the pane’s background is [in-app acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="11ebe-185">NavigationView befindet sich standardmäßig im kompakten Modus, wenn die gesamte Breite zwischen 641 und 1007px aufweist.</span><span class="sxs-lookup"><span data-stu-id="11ebe-185">By default, NavigationView is in Compact mode when its overall width is between 641px and 1007px.</span></span>

### <a name="expanded"></a><span data-ttu-id="11ebe-186">Erweitert</span><span class="sxs-lookup"><span data-stu-id="11ebe-186">Expanded</span></span>

![NavigationView im erweiterten Modus mit geöffnetem Bereich](images/navview_expanded.png)

-  <span data-ttu-id="11ebe-188">Der Bereich bleibt standardmäßig geöffnet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-188">By default, the pane remains open.</span></span> <span data-ttu-id="11ebe-189">Dieser Modus ist besser für größere Bildschirme geeignet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-189">This mode is better suited for larger screens.</span></span>
-  <span data-ttu-id="11ebe-190">Der Bereich wird neben Kopfzeile und Inhalt angezeigt, der innerhalb des verfügbaren Platzes dynamisch umgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-190">The pane draws side-by-side with the header and content, which reflows within its available space.</span></span>
-  <span data-ttu-id="11ebe-191">Wenn der Bereich mit der Navigationsschaltfläche geschlossen wird, wird der Bereich als ein schmaler Streifen neben dem Header und Inhalt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-191">When the pane is closed using the nav button, the pane shows as a narrow sliver side-by-side with the header and content.</span></span>
-  <span data-ttu-id="11ebe-192">Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="11ebe-192">The Header is not required and can be hidden to give Content more vertical space.</span></span>
-  <span data-ttu-id="11ebe-193">Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-193">The selected item shows a visual indicator to highlight where the user is in the navigation tree.</span></span>
-  <span data-ttu-id="11ebe-194">Wenn Anforderungen erfüllt sind, wird der Hintergrund des Bereichs mit [Hintergrund-Acryl](../style/acrylic.md#acrylic-blend-types) gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="11ebe-194">When requirements are met, the pane’s background is painted using [background acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="11ebe-195">NavigationView befindet sich standardmäßig im erweiterten Modus, wenn die gesamte Breite mehr als 1007px umfasst.</span><span class="sxs-lookup"><span data-stu-id="11ebe-195">By default, NavigationView is in Expanded mode when its overall width is greater than 1007px.</span></span>

### <a name="overriding-the-default-adaptive-behavior"></a><span data-ttu-id="11ebe-196">Überschreiben des standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="11ebe-196">Overriding the default adaptive behavior</span></span>

<span data-ttu-id="11ebe-197">NavigationView ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-197">NavigationView automatically changes its display mode based on the amount of screen space available to it.</span></span>

> [!NOTE]
> <span data-ttu-id="11ebe-198">NavigationView sollte als der Stammcontainer Ihrer App dienen, da dieses Steuerelement darauf ausgelegt ist, die volle Breite und Höhe des App-Fensters einzunehmen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-198">NavigationView should serve as the root container of your app, as this control is designed to span the full width and height of the app window.</span></span>
<span data-ttu-id="11ebe-199">Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) und [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="11ebe-199">You can override the widths at which the navigation view changes display modes by using the [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) and [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) properties.</span></span>

<span data-ttu-id="11ebe-200">Berücksichtigen Sie die folgenden Szenarien, die veranschaulichen, wann Sie das Anzeigemodusverhalten ggf. anpassen sollten.</span><span class="sxs-lookup"><span data-stu-id="11ebe-200">Consider the following scenarios that illustrate when you might want to customize the display mode behavior.</span></span>

- <span data-ttu-id="11ebe-201">**Häufiges Navigieren** Wenn Sie davon ausgehen, dass Benutzer relativ häufig zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei geringeren Fensterbreiten eingeblendet zu lassen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-201">**Frequent navigation** If you expect users to navigate between app areas somewhat frequently, consider keeping the pane in view at narrower window widths.</span></span> <span data-ttu-id="11ebe-202">Eine Musik-App mit Navigationsbereichen für Songs/Alben/Künstler kann eine Bereichsbreite von 280px verwenden und den erweiterten Modus beibehalten, wenn das App-Fenster breiter als 560px ist.</span><span class="sxs-lookup"><span data-stu-id="11ebe-202">A music app with Songs / Albums / Artists navigation areas may opt for a 280px pane width and remain in Expanded mode while the app window is wider than 560px.</span></span>
```xaml
<NavigationView OpenPaneLength="280" CompactModeThresholdWidth="560" ExpandedModeThresholdWidth="560"/>
```

- <span data-ttu-id="11ebe-203">**Seltenes Navigieren** Wenn Sie davon ausgehen, dass Benutzer sehr selten zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei größeren Fensterbreiten ausgeblendet zu lassen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-203">**Rare navigation** If you expect users to navigate between app areas very infrequently, consider keeping the pane hidden at wider window widths.</span></span> <span data-ttu-id="11ebe-204">Eine Rechner-App mit mehreren Layouts behält möglicherweise auch dann den minimierten Modus bei, wenn die App auf einem 1080p-Display maximiert ist.</span><span class="sxs-lookup"><span data-stu-id="11ebe-204">A calculator app with multiple layouts may opt to remain in Minimal mode even when the app is maximized on a 1080p display.</span></span>
```xaml
<NavigationView CompactModeThresholdWidth="1920" ExpandedModeThresholdWidth="1920"/>
```

- <span data-ttu-id="11ebe-205">**Mehrdeutigkeit** von Symbolen Wenn sich die Navigationsbereiche Ihrer App nicht für aussagekräftige Symbole eignen, vermeiden Sie die Verwendung des kompakten Modus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-205">**Icon disambiguation** If your app’s navigation areas don’t lend themselves to meaningful icons, avoid using Compact mode.</span></span> <span data-ttu-id="11ebe-206">Eine Bildanzeige-App mit Navigationsbereichen für Sammlungen/Alben/Ordner zeigt NavigationView bei geringen und mittleren Breiten möglicherweise im minimierten Modus und bei großer Breite im erweiterten Modus an.</span><span class="sxs-lookup"><span data-stu-id="11ebe-206">An image viewing app with Collections / Albums / Folders navigation areas may opt for showing NavigationView in Minimal mode at narrow and medium widths, and in Expanded mode at wide width.</span></span>
```xaml
<NavigationView CompactModeThresholdWidth="1008"/>
```

## <a name="interaction"></a><span data-ttu-id="11ebe-207">Interaktion</span><span class="sxs-lookup"><span data-stu-id="11ebe-207">Interaction</span></span>

<span data-ttu-id="11ebe-208">Wenn Benutzer in dem Bereich auf ein Navigationselement tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-208">When users tap on a navigation item in the Pane, NavigationView will show that item as selected and will raise an [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) event.</span></span> <span data-ttu-id="11ebe-209">Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-209">If the tap results in a new item being selected, NavigationView will also raise a [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) event.</span></span> 

<span data-ttu-id="11ebe-210">Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="11ebe-210">Your app is responsible for updating the Header and Content with appropriate information in response to this user interaction.</span></span> <span data-ttu-id="11ebe-211">Darüber hinaus wird empfohlen, den [Fokus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.FocusState) programmgesteuert vom Navigationselement zum Inhalt zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="11ebe-211">In addition, we recommend programmatically moving [focus](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.controls.control.FocusState) from the navigation item to the content.</span></span> <span data-ttu-id="11ebe-212">Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.</span><span class="sxs-lookup"><span data-stu-id="11ebe-212">By setting initial focus on load, you streamline the user flow and minimize the expected number of keyboard focus moves.</span></span>

## <a name="backwards-navigation"></a><span data-ttu-id="11ebe-213">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="11ebe-213">Backwards navigation</span></span>
<span data-ttu-id="11ebe-214">NavigationView verfügt über eine integrierte Schaltfläche „Zurück“, die mit den folgenden Eigenschaften aktiviert werden kann:</span><span class="sxs-lookup"><span data-stu-id="11ebe-214">NavigationView has a built-in back button, which can be enabled with the following properties:</span></span>
- <span data-ttu-id="11ebe-215">[**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) ist eine NavigationViewBackButtonVisible-Enumeration und standardmäßig auf "Auto" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-215">[**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) is a NavigationViewBackButtonVisible enum and "Auto" by default.</span></span> <span data-ttu-id="11ebe-216">Sie dient zum Einblenden/Ausblenden der Schaltfläche „Zurück“.</span><span class="sxs-lookup"><span data-stu-id="11ebe-216">It is used to show/hide the back button.</span></span> <span data-ttu-id="11ebe-217">Wenn die Schaltfläche nicht angezeigt wird, wird der Platz für die Darstellung der Schaltfläche „Zurück“ reduziert.</span><span class="sxs-lookup"><span data-stu-id="11ebe-217">When the button is not visible, the space for drawing the back button will be collapsed.</span></span>
- <span data-ttu-id="11ebe-218">[**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) lautet standardmäßig „false“ und kann zum Umschalten des Status der Schaltfläche „Zurück“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="11ebe-218">[**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) is false by default and can be used to toggle the back button states.</span></span>
- <span data-ttu-id="11ebe-219">[**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) wird ausgelöst, wenn ein Benutzer auf die Schaltfläche „Zurück“ klickt.</span><span class="sxs-lookup"><span data-stu-id="11ebe-219">[**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) is fired when a user clicks on the back button.</span></span>
    - <span data-ttu-id="11ebe-220">Wenn im minimalen oder kompakten Modus der NavigationView.Pane als Flyout geöffnet ist und auf die Schaltfläche „Zurück“ geklickt wird, wird der Bereich geschlossen und stattdessen das **PaneClosing**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="11ebe-220">In Minimal/Compact mode, when the NavigationView.Pane is open as a flyout, clicking the back button will close the Pane and fire **PaneClosing** event instead.</span></span>
    - <span data-ttu-id="11ebe-221">Wenn IsBackEnabled auf „false“ festgelegt ist, wird es nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="11ebe-221">Not fired if IsBackEnabled is false.</span></span>

![Schaltfläche „Zurück“ der NavigationView](../basics/images/back-nav/NavView.png)

## <a name="code-example"></a><span data-ttu-id="11ebe-223">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="11ebe-223">Code example</span></span>

<span data-ttu-id="11ebe-224">Es folgt ein einfaches Beispiel dafür, wie Sie NavigationView in Ihre App integrieren können.</span><span class="sxs-lookup"><span data-stu-id="11ebe-224">The following is a simple example of how you can incorporate NavigationView into your app.</span></span> 

<span data-ttu-id="11ebe-225">Es wird veranschaulicht, wie die Rückwärtsnavigation mit der Schaltfläche „Zurück“ der NavigationView implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-225">We demonstrate how to implement backwards navigation with NavigationView's back button.</span></span> <span data-ttu-id="11ebe-226">Beachten Sie, dass Sie für die Verwendung der Eigenschaften für die Rückwärtsnavigation [Windows10 Insider Preview (in v10.0.17110.0 eingeführt)](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) benötigen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-226">Note that to use NavigationView's back navigation properties, you'll need the [Windows 10 Insider Preview (introduced v10.0.17110.0)](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK).</span></span>

<span data-ttu-id="11ebe-227">Außerdem wird die Lokalisierung von Inhaltszeichenfolgen für Navigationselemente mit `x:Uid` veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="11ebe-227">We also demonstrate localization of nav item content strings with `x:Uid`.</span></span> <span data-ttu-id="11ebe-228">Weitere Informationen zur Lokalisierung finden Sie unter [Lokalisieren von Zeichenfolgen in der Benutzeroberfläche](../../app-resources/localize-strings-ui-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="11ebe-228">For more information on localization, see [Localize strings in your UI](../../app-resources/localize-strings-ui-manifest.md).</span></span>

```xaml
<Page
    x:Class="NavigationViewSample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:NavigationViewSample"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <NavigationView x:Name="NavView"
                    ItemInvoked="NavView_ItemInvoked"
                    Loaded="NavView_Loaded"
                    BackRequested="NavView_BackRequested">

        <NavigationView.MenuItems>
            <NavigationViewItem x:Uid="HomeNavItem" Content="Home" Tag="home">
                <NavigationViewItem.Icon>
                    <FontIcon Glyph="&#xE10F;"/>
                </NavigationViewItem.Icon>
            </NavigationViewItem>
            <NavigationViewItemSeparator/>
            <NavigationViewItemHeader Content="Main pages"/>
            <NavigationViewItem x:Uid="AppsNavItem" Icon="AllApps" Content="Apps" Tag="apps"/>
            <NavigationViewItem x:Uid="GamesNavItem" Icon="Video" Content="Games" Tag="games"/>
            <NavigationViewItem x:Uid="MusicNavItem" Icon="Audio" Content="Music" Tag="music"/>
        </NavigationView.MenuItems>

        <NavigationView.AutoSuggestBox>
            <AutoSuggestBox x:Name="ASB" QueryIcon="Find"/>
        </NavigationView.AutoSuggestBox>

        <NavigationView.HeaderTemplate>
            <DataTemplate>
                <Grid Margin="24,10,0,0">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition/>
                    </Grid.ColumnDefinitions>
                    <TextBlock Style="{StaticResource TitleTextBlockStyle}"
                           FontSize="28"
                           VerticalAlignment="Center"
                           Text="Welcome"/>
                    <CommandBar Grid.Column="1"
                            HorizontalAlignment="Right"
                            VerticalAlignment="Top"
                            DefaultLabelPosition="Right"
                            Background="{ThemeResource SystemControlBackgroundAltHighBrush}">
                        <AppBarButton Label="Refresh" Icon="Refresh"/>
                        <AppBarButton Label="Import" Icon="Import"/>
                    </CommandBar>
                </Grid>
            </DataTemplate>
        </NavigationView.HeaderTemplate>

        <NavigationView.PaneFooter>
            <HyperlinkButton x:Name="MoreInfoBtn"
                             Content="More info"
                             Click="More_Click"
                             Margin="12,0"/>
        </NavigationView.PaneFooter>

        <Frame x:Name="ContentFrame" Margin="24">
            <Frame.ContentTransitions>
                <TransitionCollection>
                    <NavigationThemeTransition/>
                </TransitionCollection>
            </Frame.ContentTransitions>
        </Frame>

    </NavigationView>
</Page>
```

```csharp
private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // you can also add items in code behind
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem()
    { Content = "My content", Icon = new SymbolIcon(Symbol.Folder), Tag = "content" });

    // set the initial SelectedItem 
    foreach (NavigationViewItemBase item in NavView.MenuItems)
    {
        if (item is NavigationViewItem && item.Tag.ToString() == "home")
        {
            NavView.SelectedItem = item;
            break;
        }
    }
            
    ContentFrame.Navigated += On_Navigated;

    // add keyboard accelerators for backwards navigation
    KeyboardAccelerator GoBack = new KeyboardAccelerator();
    GoBack.Key = VirtualKey.GoBack;
    GoBack.Invoked += BackInvoked;
    KeyboardAccelerator AltLeft = new KeyboardAccelerator();
    AltLeft.Key = VirtualKey.Left;
    AltLeft.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(GoBack);
    this.KeyboardAccelerators.Add(AltLeft);
    // ALT routes here
    AltLeft.Modifiers = VirtualKeyModifiers.Menu;
    
}

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{  
    if (args.IsSettingsInvoked)
    {
        ContentFrame.Navigate(typeof(SettingsPage));
    }
    else
    {
        // find NavigationViewItem with Content that equals InvokedItem
        var item = sender.MenuItems.OfType<NavigationViewItem>().First(x => (string)x.Content == (string)args.InvokedItem);
        NavView_Navigate(item as NavigationViewItem);
    }
}

private void NavView_Navigate(NavigationViewItem item)
{
    switch (item.Tag)
    {
        case "home":
            ContentFrame.Navigate(typeof(HomePage));
            break;

        case "apps":
            ContentFrame.Navigate(typeof(AppsPage));
            break;

        case "games":
            ContentFrame.Navigate(typeof(GamesPage));
            break;

        case "music":
            ContentFrame.Navigate(typeof(MusicPage));
            break;

        case "content":
            ContentFrame.Navigate(typeof(MyContentPage));
            break;
    }           
}

private void NavView_BackRequested(NavigationView sender, NavigationViewBackRequestedEventArgs args)
{
    On_BackRequested();
}

private void BackInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}

private bool On_BackRequested()
{
    bool navigated = false;

    // don't go back if the nav pane is overlayed
    if (NavView.IsPaneOpen && (NavView.DisplayMode == NavigationViewDisplayMode.Compact || NavView.DisplayMode == NavigationViewDisplayMode.Minimal))
    {
        return false;
    }
    else
    {
        if (ContentFrame.CanGoBack)
        {
            ContentFrame.GoBack();
            navigated = true;
        }
    }
    return navigated;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        NavView.SelectedItem = NavView.SettingsItem as NavigationViewItem;
    }
    else 
    {
        Dictionary<Type, string> lookup = new Dictionary<Type, string>()
        {
            {typeof(HomePage), "home"},
            {typeof(AppsPage), "apps"},
            {typeof(GamesPage), "games"},
            {typeof(MusicPage), "music"},
            {typeof(MyContentPage), "content"}    
        };

        String stringTag = lookup[ContentFrame.SourcePageType];

        // set the new SelectedItem  
        foreach (NavigationViewItemBase item in NavView.MenuItems)
        {
            if (item is NavigationViewItem && item.Tag.Equals(stringTag))
            {
                item.IsSelected = true;
                break;
            }
        }        
    }
}
```

## <a name="customizing-backgrounds"></a><span data-ttu-id="11ebe-229">Anpassen von Hintergründen</span><span class="sxs-lookup"><span data-stu-id="11ebe-229">Customizing backgrounds</span></span>

<span data-ttu-id="11ebe-230">Legen Sie zum Ändern des Hintergrunds des Hauptbereichs von NavigationView seine `Background`-Eigenschaft auf Ihren bevorzugten Pinsel.</span><span class="sxs-lookup"><span data-stu-id="11ebe-230">To change the background of NavigationView's main area, set its `Background` property to your preferred brush.</span></span>

<span data-ttu-id="11ebe-231">Der Hintergrundbereich verwendet In-App-Acryl, wenn NavigationView im minimalen oder kompakten Modus und das Hintergrund-Acryl im erweiterten Modus ist.</span><span class="sxs-lookup"><span data-stu-id="11ebe-231">The Pane's background shows in-app acrylic when NavigationView is in Minimal or Compact mode, and background acrylic in Expanded mode.</span></span> <span data-ttu-id="11ebe-232">Um dieses Verhalten zu aktualisieren oder die Darstellung des Acrylbereichs anzupassen, ändern Sie die zwei Designressourcen durch Überschreiben Ihrer App.xaml.</span><span class="sxs-lookup"><span data-stu-id="11ebe-232">To update this behavior or customize the appearance of your Pane's acrylic, modify the two theme resources by overwriting them in your App.xaml.</span></span>

```xaml
<Application.Resources>
    <ResourceDictionary>
        <AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewExpandedPaneBackground"
        BackgroundSource="HostBackdrop" TintColor="Orange" TintOpacity=".8"/>
    </ResourceDictionary>
</Application.Resources>
```

## <a name="extending-your-app-into-the-title-bar"></a><span data-ttu-id="11ebe-233">Erweitern Ihrer App auf die Titelleiste</span><span class="sxs-lookup"><span data-stu-id="11ebe-233">Extending your app into the title bar</span></span>

<span data-ttu-id="11ebe-234">Für eine nahtlose, fließende Darstellung im Fenster Ihrer App wird empfohlen, die NavigationView und deren Acrylbereich auf den Bereich der Titelleiste Ihrer App zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="11ebe-234">For a seamless, flowing look within your app's window, we recommend extending NavigationView and its acrylic pane up into your app's title bar area.</span></span> <span data-ttu-id="11ebe-235">Dadurch werden die visuell unattraktive Form, die durch die Titelleiste erzeugt wird, die einfarbigen NavigationView-Inhalte und der Acrylbereich der NavigationView vermieden.</span><span class="sxs-lookup"><span data-stu-id="11ebe-235">This avoids the visually unattractive shape created by the title bar, the solid-colored NavigationView Content, and the acrylic of NavigationView's pane.</span></span>

<span data-ttu-id="11ebe-236">Fügen Sie dazu den folgenden Code in der Datei App.xaml.cs hinzu.</span><span class="sxs-lookup"><span data-stu-id="11ebe-236">To do so, add the following code to your App.xaml.cs.</span></span>

```csharp
//draw into the title bar
var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
coreTitleBar.ExtendViewIntoTitleBar = true;

//remove the solid-colored backgrounds behind the caption controls and system back button
var viewTitleBar = ApplicationView.GetForCurrentView().TitleBar;
viewTitleBar.ButtonBackgroundColor = Colors.Transparent;
viewTitleBar.ButtonInactiveBackgroundColor = Colors.Transparent;
viewTitleBar.ButtonForegroundColor = (Color)Resources["SystemBaseHighColor"];
```

<span data-ttu-id="11ebe-237">Das Zeichnen in die Titelleiste hat den Nebeneffekt, dass der App-Titel ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="11ebe-237">Drawing into the title bar has the side-effect of hiding your app's title.</span></span> <span data-ttu-id="11ebe-238">Stellen Sie zur Unterstützung der Benutzer den Titel wieder her, indem Sie einen eigenen TextBlock hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-238">To help users, restore the title by adding your own TextBlock.</span></span> <span data-ttu-id="11ebe-239">Fügen Sie der Stammseite, die Ihre NavigationView enthält, das folgende Markup hinzu.</span><span class="sxs-lookup"><span data-stu-id="11ebe-239">Add the following markup to the root page containing your NavigationView.</span></span>

```xaml
<Grid>
    <TextBlock x:Name="AppTitle"
        xmlns:appmodel="using:Windows.ApplicationModel"
        Text="{x:Bind appmodel:Package.Current.DisplayName}"
        Style="{StaticResource CaptionTextBlockStyle}"
        IsHitTestVisible="False"
        Canvas.ZIndex="1"/>
    

    <NavigationView Canvas.ZIndex="0" ... />

</Grid>
```

<span data-ttu-id="11ebe-240">Je nach Sichtbarkeit der Schaltfläche „Zurück“ müssen Sie auch die AppTitle-Ränder anpassen.</span><span class="sxs-lookup"><span data-stu-id="11ebe-240">You'll also need to adjust AppTitle's margins depending on back button's visibility.</span></span> <span data-ttu-id="11ebe-241">Und wenn sich die App im FullScreenMode befindet, müssen Sie den Abstand für die Zurück-Pfeil auch dann entfernen, wenn die TitleBar Platz für sie reserviert.</span><span class="sxs-lookup"><span data-stu-id="11ebe-241">And, when the app is in FullScreenMode, you'll need to remove the spacing for the back arrow, even if the TitleBar reserves space for it.</span></span>

```csharp
var coreTitleBar = CoreApplication.GetCurrentView().TitleBar;
Window.Current.SetTitleBar(AppTitle);
coreTitleBar.ExtendViewIntoTitleBar = true;

void UpdateAppTitle()
{
    var full = (ApplicationView.GetForCurrentView().IsFullScreenMode);
    var left = 12 + (full ? 0 : CoreApplication.GetCurrentView().TitleBar.SystemOverlayLeftInset);
    AppTitle.Margin = new Thickness(left, 8, 0, 0);
}

Window.Current.CoreWindow.SizeChanged += (s, e) => UpdateAppTitle();
coreTitleBar.LayoutMetricsChanged += (s, e) => UpdateAppTitle();
```

<span data-ttu-id="11ebe-242">Weitere Informationen zum Anpassen von Titelleisten, finden Sie unter [Anpassung der Titelleiste](../shell/title-bar.md).</span><span class="sxs-lookup"><span data-stu-id="11ebe-242">For more information about customizing title bars, see [title bar customization](../shell/title-bar.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="11ebe-243">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11ebe-243">Related topics</span></span>

- [<span data-ttu-id="11ebe-244">NavigationView-Klasse</span><span class="sxs-lookup"><span data-stu-id="11ebe-244">NavigationView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [<span data-ttu-id="11ebe-245">Master/Details</span><span class="sxs-lookup"><span data-stu-id="11ebe-245">Master/details</span></span>](master-details.md)
- [<span data-ttu-id="11ebe-246">Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="11ebe-246">Pivot control</span></span>](tabs-pivot.md)
- [<span data-ttu-id="11ebe-247">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="11ebe-247">Navigation basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="11ebe-248">Übersicht über Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="11ebe-248">Fluent Design for UWP overview</span></span>](../fluent-design-system/index.md)

