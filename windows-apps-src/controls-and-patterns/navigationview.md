---
author: Jwmsft
Description: "Steuerelement für die Navigation auf oberster Ebene, das gleichzeitig Platz auf dem Bildschirm spart."
title: Navigationsansicht
ms.assetid: 
label: Navigation view
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: tpaine
doc-status: Published
ms.openlocfilehash: 98ab8a95288e5a0225a2185f7ce037e16209d173
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="navigation-view"></a><span data-ttu-id="81309-104">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="81309-104">Navigation view</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

> [!IMPORTANT]
> <span data-ttu-id="81309-105">In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. grundlegend geändert werden.</span><span class="sxs-lookup"><span data-stu-id="81309-105">This article describes functionality that hasn’t been released yet and may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="81309-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="81309-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="81309-107">Das Navigationsansichts-Steuerelement bietet über ein reduzierbares Navigationsmenü ein allgemeines vertikales Layout für App-Bereiche auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="81309-107">The navigation view control provides a common vertical layout for top-level areas of your app via a collapsible navigation menu.</span></span> <span data-ttu-id="81309-108">Dieses Steuerelement dient der Implementierung des Navigationsbereichsmusters oder Hamburger-Menü-Musters, wobei die Anordnung automatisch an verschiedene Fenstergrößen angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="81309-108">This control is designed to implement the nav pane, or hamburger menu, pattern and automatically adapts its layout to different window sizes.</span></span>

> <span data-ttu-id="81309-109">**Wichtige APIs**: [NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode-Enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)</span><span class="sxs-lookup"><span data-stu-id="81309-109">**Important APIs**: [NavigationView class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview), [NavigationViewItem class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), [NavigationViewDisplayMode enumeration](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewdisplaymode)</span></span>

![Beispiel für NavigationView](images/navview_wireframe.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="81309-111">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="81309-111">Is this the right control?</span></span>

<span data-ttu-id="81309-112">NavigationView eignet sich gut für:</span><span class="sxs-lookup"><span data-stu-id="81309-112">NavigationView works well for:</span></span>

-  <span data-ttu-id="81309-113">Apps mit vielen Navigationselementen auf oberster Ebene, die einen ähnlichen Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="81309-113">Apps with many top-level navigation items that are of similar type.</span></span> <span data-ttu-id="81309-114">Dies kann beispielsweise eine Sport-App mit Kategorien wie Football, Baseball, Basketball, Fußball usw. sein.</span><span class="sxs-lookup"><span data-stu-id="81309-114">For example, a sports app with categories like Football, Baseball, Basketball, Soccer, and so on.</span></span>
-  <span data-ttu-id="81309-115">Bereitstellen einer konsistenten Navigationsumgebung über verschiedene Apps hinweg.</span><span class="sxs-lookup"><span data-stu-id="81309-115">Providing a consistent navigational experience across apps.</span></span> <span data-ttu-id="81309-116">Der Bereich sollte nur Navigationselemente, keine Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="81309-116">The pane should include only navigational elements, not actions.</span></span>
-  <span data-ttu-id="81309-117">Eine mittlere bis hohe Zahl (5-10) an Navigationskategorien der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="81309-117">A medium-to-high number (5-10) of top-level navigational categories.</span></span>
-  <span data-ttu-id="81309-118">Sparen von Platz auf dem Bildschirm von kleineren Fenstern.</span><span class="sxs-lookup"><span data-stu-id="81309-118">Preserving screen real estate of smaller windows.</span></span>

<span data-ttu-id="81309-119">Die Naviagationsansicht ist nur eine von mehreren Navigationselementen, die Ihnen zur Verfügung stehen. Weitere Informationen zu Navigationsmustern und anderen Navigationselementen finden Sie unter [Navigationsdesigngrundlagen für UWP-Apps (Universelle Windows-Plattform)](../layout/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="81309-119">Navigation view is just one of several navigation elements you can use; to learn more about navigation patterns and other navigation elements, see the [Navigation design basics for Universal Windows Platform (UWP) apps](../layout/navigation-basics.md).</span></span>

<span data-ttu-id="81309-120">Laden Sie die [XAML-Navigationslösung](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/XamlNavigation) von GitHub herunter, um ein Codebeispiel für das Erstellen eines Navigationsbereichsmusters mit SplitView und ListView zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="81309-120">For a code sample of how to build the nav pane pattern using SplitView and ListView, download the [XAML Navigation solution](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/XamlNavigation) from GitHub.</span></span>

## <a name="navigationview-parts"></a><span data-ttu-id="81309-121">Teile von NavigationView</span><span class="sxs-lookup"><span data-stu-id="81309-121">NavigationView parts</span></span>
<span data-ttu-id="81309-122">Das Steuerelement lässt sich allgemein in drei Abschnitte unterteilen: einen Bereich für die Navigation auf der linken Seite und einen Kopfzeilen- sowie einen Inhaltsbereich auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="81309-122">The control is broadly subdivided into three sections - a pane for navigation on the left, and header and content areas on the right.</span></span>

![Abschnitte von NavigationView](images/navview_sections.png)

### <a name="pane"></a><span data-ttu-id="81309-124">Bereich</span><span class="sxs-lookup"><span data-stu-id="81309-124">Pane</span></span>

<span data-ttu-id="81309-125">Der Navigationsbereich kann Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="81309-125">The navigation pane can contain:</span></span>

- <span data-ttu-id="81309-126">Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren</span><span class="sxs-lookup"><span data-stu-id="81309-126">Navigation items, in the form of [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), for navigating to specific pages</span></span>
- <span data-ttu-id="81309-127">Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren</span><span class="sxs-lookup"><span data-stu-id="81309-127">Separators, in the form of [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), for grouping navigation items</span></span>
- <span data-ttu-id="81309-128">Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen</span><span class="sxs-lookup"><span data-stu-id="81309-128">Headers, in the form of [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), for labeling groups of items</span></span>
- <span data-ttu-id="81309-129">Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md).</span><span class="sxs-lookup"><span data-stu-id="81309-129">An optional entry point for [app settings](../app-settings/app-settings-and-data.md).</span></span> <span data-ttu-id="81309-130">Verwenden Sie zum Ausblenden des Einstellungselements die Eigenschaft [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsSettingsVisible)</span><span class="sxs-lookup"><span data-stu-id="81309-130">To hide the settings item, use the [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsSettingsVisible) property</span></span>
- <span data-ttu-id="81309-131">Freier Inhalt in der Fußzeile des Bereichs, wenn es zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_PaneFooter)-Eigenschaft hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="81309-131">Free-form content in the pane’s footer, when added to the [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_PaneFooter) property</span></span>

<span data-ttu-id="81309-132">Mit der integrierten Navigationsschaltfläche („Hamburger“-Schaltfläche) können Benutzer den Bereich öffnen und schließen.</span><span class="sxs-lookup"><span data-stu-id="81309-132">The built-in navigation ("hamburger") button lets users open and close the pane.</span></span> <span data-ttu-id="81309-133">Sie können bei größeren Appfenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigneschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsPaneToggleButtonVisible) ausblenden.</span><span class="sxs-lookup"><span data-stu-id="81309-133">On larger app windows when the pane is open, you may choose to hide this button using the [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_IsPaneToggleButtonVisible) property.</span></span>

### <a name="header"></a><span data-ttu-id="81309-134">Header</span><span class="sxs-lookup"><span data-stu-id="81309-134">Header</span></span>

<span data-ttu-id="81309-135">Der Kopfzeilenbereich ist vertikal an der Navigationsschaltfläche ausgerichtet und hat eine feste Höhe.</span><span class="sxs-lookup"><span data-stu-id="81309-135">The header area is vertically aligned with the navigation button and has a fixed height.</span></span> <span data-ttu-id="81309-136">Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="81309-136">Its purpose is to hold the page title of the selected nav category.</span></span> <span data-ttu-id="81309-137">Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="81309-137">The header is docked to the top of the page and acts as a scroll clipping point for the content area.</span></span>

<span data-ttu-id="81309-138">Die Kopfzeile muss sichtbar sein, wenn sich die Navigationsansicht im minimierten Modus befindet.</span><span class="sxs-lookup"><span data-stu-id="81309-138">The header must be visible when NavigationView is in Minimal mode.</span></span> <span data-ttu-id="81309-139">Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="81309-139">You may choose to hide the header in other modes, which are used on larger window widths.</span></span> <span data-ttu-id="81309-140">Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_AlwaysShowHeader) auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="81309-140">To do so, set the [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_AlwaysShowHeader) property to **false**.</span></span>

### <a name="content"></a><span data-ttu-id="81309-141">Inhalt</span><span class="sxs-lookup"><span data-stu-id="81309-141">Content</span></span>

<span data-ttu-id="81309-142">Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="81309-142">The content area is where most of the information for the selected nav category is displayed.</span></span> <span data-ttu-id="81309-143">Er kann ein oder mehrere Elemente enthalten und eignet sich gut für zusätzliche untergeordnete Navigationselemente wie [Pivot](tabs-pivot.md).</span><span class="sxs-lookup"><span data-stu-id="81309-143">It can contain one or more elements and is a good area for additional sub-level navigation such as [Pivot](tabs-pivot.md).</span></span>

<span data-ttu-id="81309-144">Wir empfehlen, Ränder auf Inhaltsseiten auf 12px festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24px.</span><span class="sxs-lookup"><span data-stu-id="81309-144">We recommend 12px margins on your content’s sides when NavigationView is in Minimal mode and 24px margins otherwise.</span></span>

## <a name="visual-style"></a><span data-ttu-id="81309-145">Visueller Stil</span><span class="sxs-lookup"><span data-stu-id="81309-145">Visual style</span></span>

<div class="microsoft-internal-note">
<span data-ttu-id="81309-146">Redlines für dieses Steuerelement sind verfügbar auf [UNI](http://uni/DesignDepot.FrontEnd/#/ProductNav?t=Fluent%20Design%20System%7CControls%20%26%20Patterns%7CNavigationView).</span><span class="sxs-lookup"><span data-stu-id="81309-146">Redlines for this control are available on [UNI](http://uni/DesignDepot.FrontEnd/#/ProductNav?t=Fluent%20Design%20System%7CControls%20%26%20Patterns%7CNavigationView).</span></span><br/><br/>
</div>

<span data-ttu-id="81309-147">Navigationselemente unterstützen die Ansichtszustände ausgewählt, deaktiviert, Zeiger über, gedrückt und fokussiert.</span><span class="sxs-lookup"><span data-stu-id="81309-147">Navigation items have support for selected, disabled, pointer over, pressed, and focused visual states.</span></span>

![Zustände von NavigationView-Elementen: deaktiviert, Zeiger über, gedrückt und fokussiert](images/navview_item-states.png)

<span data-ttu-id="81309-149">Wenn Hardware- und Softwareanforderungen erfüllt sind, verwendet NavigationView in seinem Bereich automatisch das neue [Acryl-Material](../style/acrylic.md) und [Reveal-highlight](../style/reveal.md).</span><span class="sxs-lookup"><span data-stu-id="81309-149">When hardware and software requirements are met, NavigationView automatically uses the new [Acrylic material](../style/acrylic.md) and [Reveal highlight](../style/reveal.md) in its pane.</span></span>


## <a name="navigationview-modes"></a><span data-ttu-id="81309-150">NavigationView-Modi</span><span class="sxs-lookup"><span data-stu-id="81309-150">NavigationView modes</span></span>
<span data-ttu-id="81309-151">Der Navigationsansichtsbereich kann offen oder geschlossen sein und verfügt über drei Optionen für Anzeigemodi:</span><span class="sxs-lookup"><span data-stu-id="81309-151">The NavigationView pane can be open or closed, and has three display mode options:</span></span>
-  <span data-ttu-id="81309-152">**Minimiert** Nur die „Hamburger“-Schaltfläche bleibt fest, während der Bereich nach Bedarf ein- und ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="81309-152">**Minimal** Only the hamburger button remains fixed while the pane shows and hides as needed.</span></span>
-  <span data-ttu-id="81309-153">**Kompakt** Der Bereich wird als schmaler Streifen angezeigt, der zur vollen Breite erweitert werden kann.</span><span class="sxs-lookup"><span data-stu-id="81309-153">**Compact** The pane always shows as a narrow sliver which can be opened to full width.</span></span>
-  <span data-ttu-id="81309-154">**Erweitert** Der Bereich wird neben dem Inhalt geöffnet.</span><span class="sxs-lookup"><span data-stu-id="81309-154">**Expanded** The pane is open alongside the content.</span></span> <span data-ttu-id="81309-155">Beim Schließen durch Aktivieren der „Hamburger“-Schaltfläche wird die Breite zu einem schmalen Streifen.</span><span class="sxs-lookup"><span data-stu-id="81309-155">When closed by activating the hamburger button, the pane's width becomes a narrow sliver.</span></span>

<span data-ttu-id="81309-156">In der Standardeinstellung wählt das System je nach Größe des Bildschirmbereichs, der für das Steuerelement verfügbar ist, automatisch den optimalen Anzeigemodus aus.</span><span class="sxs-lookup"><span data-stu-id="81309-156">By default, the system automatically selects the optimal display mode based on the amount of screen space available to the control.</span></span> <span data-ttu-id="81309-157">(Sie können diese Einstellung überschreiben. Nähere Informationen dazu finden Sie im nächsten Abschnitt.)</span><span class="sxs-lookup"><span data-stu-id="81309-157">(You can override this setting — see the next section for details.)</span></span>

### <a name="minimal"></a><span data-ttu-id="81309-158">Minimiert</span><span class="sxs-lookup"><span data-stu-id="81309-158">Minimal</span></span>

![NavigationView im minimierten Modus mit geschlossenem und geöffnetem Bereich](images/navview_minimal.png)

-  <span data-ttu-id="81309-160">Ist der Bereich geschlossen, wird er standardmäßig ausgeblendet, und es wird nur die Navigationsschaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="81309-160">When closed, the pane is hidden by default, with only the nav button visible.</span></span>
-  <span data-ttu-id="81309-161">Bietet On-Demand-Navigation, die Platz auf dem Bildschirm spart.</span><span class="sxs-lookup"><span data-stu-id="81309-161">Provides on-demand navigation that conserves screen real estate.</span></span> <span data-ttu-id="81309-162">Ideal für Apps auf Smartphones und Tablets.</span><span class="sxs-lookup"><span data-stu-id="81309-162">Ideal for apps on phones and phablets.</span></span>
-  <span data-ttu-id="81309-163">Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="81309-163">Pressing the nav button opens and closes the pane, which draws as an overlay above the header and content.</span></span> <span data-ttu-id="81309-164">Inhalt wird nicht dynamisch umgebrochen.</span><span class="sxs-lookup"><span data-stu-id="81309-164">Content does not reflow.</span></span>
-  <span data-ttu-id="81309-165">Im geöffneten Zustand stellt er einen vorübergehenden Bereich dar, der durch eine Geste zum einfachen Ausblenden wie Treffen einer Auswahl, Drücken der Zurück-Schaltfläche oder Tippen außerhalb des Bereichs geschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="81309-165">When open, the pane is transient and can be closed with a light dismiss gesture such as making a selection, pressing the back button, or tapping outside the pane.</span></span>
-  <span data-ttu-id="81309-166">Das ausgewählte Element wird angezeigt, wenn die Überlagerung des Bereichs geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="81309-166">The selected item becomes visible when the pane’s overlay opens.</span></span>
-  <span data-ttu-id="81309-167">Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des geöffneten Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).</span><span class="sxs-lookup"><span data-stu-id="81309-167">When requirements are met, the open pane’s background is [in-app acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="81309-168">NavigationView befindet sich standardmäßig im minimierten Modus, wenn die gesamte Breite kleiner oder gleich 640Pixel ist.</span><span class="sxs-lookup"><span data-stu-id="81309-168">By default, NavigationView is in Minimal mode when its overall width is less than or equal to 640px.</span></span>

### <a name="compact"></a><span data-ttu-id="81309-169">Kompakt</span><span class="sxs-lookup"><span data-stu-id="81309-169">Compact</span></span>

![NavigationView im kompakten Modus mit geschlossenem und geöffnetem Bereich](images/navview_compact.png)

-  <span data-ttu-id="81309-171">Ist der Bereich geschlossen, werden ein vertikaler Streifen des Bereichs nur mit Symbolen sowie die Navigationsschaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="81309-171">When closed, a vertical sliver of the pane showing only icons and the nav button is visible.</span></span>
-  <span data-ttu-id="81309-172">Zeigen die ausgewählte Position an, während sie nur wenig Platz auf dem Bildschirm belegen.</span><span class="sxs-lookup"><span data-stu-id="81309-172">Provides some indication of the selected location while using a small amount of screen real-estate.</span></span>
-  <span data-ttu-id="81309-173">Dieser Modus ist besser für mittelgroße Bildschirme wie Tablets und [10-Fuß-Umgebungen](../input-and-devices/designing-for-tv.md) geeignet.</span><span class="sxs-lookup"><span data-stu-id="81309-173">This mode is better suited for medium screens like tablets and [10-foot experiences](../input-and-devices/designing-for-tv.md).</span></span>
-  <span data-ttu-id="81309-174">Durch Drücken der Navigationsschaltfläche wird der Bereich geöffnet und geschlossen, der als eine Überlagerung über der Kopfzeile und dem Inhalt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="81309-174">Pressing the nav button opens and closes the pane, which draws as an overlay above the header and content.</span></span> <span data-ttu-id="81309-175">Inhalt wird nicht umgebrochen.</span><span class="sxs-lookup"><span data-stu-id="81309-175">Content does not reflow.</span></span>
-  <span data-ttu-id="81309-176">Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="81309-176">The Header is not required and can be hidden to give Content more vertical space.</span></span>
-  <span data-ttu-id="81309-177">Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich der Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="81309-177">The selected item shows a visual indicator to highlight where the user is in the navigation tree.</span></span>
-  <span data-ttu-id="81309-178">Wenn Anforderungen erfüllt sind, verwendet der Hintergrund des Bereichs [In-App-Acryl](../style/acrylic.md#acrylic-blend-types).</span><span class="sxs-lookup"><span data-stu-id="81309-178">When requirements are met, the pane’s background is [in-app acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="81309-179">NavigationView befindet sich standardmäßig im kompakten Modus, wenn die gesamte Breite zwischen 641 und 1007px aufweist.</span><span class="sxs-lookup"><span data-stu-id="81309-179">By default, NavigationView is in Compact mode when its overall width is between 641px and 1007px.</span></span>

### <a name="expanded"></a><span data-ttu-id="81309-180">Erweitert</span><span class="sxs-lookup"><span data-stu-id="81309-180">Expanded</span></span>

![NavigationView im erweiterten Modus mit geöffnetem Bereich](images/navview_expanded.png)

-  <span data-ttu-id="81309-182">Der Bereich bleibt standardmäßig geöffnet.</span><span class="sxs-lookup"><span data-stu-id="81309-182">By default, the pane remains open.</span></span> <span data-ttu-id="81309-183">Dieser Modus ist besser für größere Bildschirme geeignet.</span><span class="sxs-lookup"><span data-stu-id="81309-183">This mode is better suited for larger screens.</span></span>
-  <span data-ttu-id="81309-184">Der Bereich wird neben Kopfzeile und Inhalt angezeigt, der innerhalb des verfügbaren Platzes dynamisch umgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="81309-184">The pane draws side-by-side with the header and content, which reflows within its available space.</span></span>
-  <span data-ttu-id="81309-185">Wenn der Bereich mit der Navigationsschaltfläche geschlossen wird, wird der Bereich als ein schmaler Streifen neben dem Header und Inhalt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="81309-185">When the pane is closed using the nav button, the pane shows as a narrow sliver side-by-side with the header and content.</span></span>
-  <span data-ttu-id="81309-186">Die Kopfzeile ist nicht erforderlich und kann ausgeblendet werden, um Inhalt mehr vertikale Fläche zu bieten.</span><span class="sxs-lookup"><span data-stu-id="81309-186">The Header is not required and can be hidden to give Content more vertical space.</span></span>
-  <span data-ttu-id="81309-187">Das ausgewählte Element zeigt einen visuellen Hinweis an, um hervorzuheben, wo sich Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="81309-187">The selected item shows a visual indicator to highlight where the user is in the navigation tree.</span></span>
-  <span data-ttu-id="81309-188">Wenn Anforderungen erfüllt sind, wird der Hintergrund des Bereichs mit [Hintergrund-Acryl](../style/acrylic.md#acrylic-blend-types) gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="81309-188">When requirements are met, the pane’s background is painted using [background acrylic](../style/acrylic.md#acrylic-blend-types).</span></span>
-  <span data-ttu-id="81309-189">NavigationView befindet sich standardmäßig im erweiterten Modus, wenn die gesamte Breite mehr als 1007px umfasst.</span><span class="sxs-lookup"><span data-stu-id="81309-189">By default, NavigationView is in Expanded mode when its overall width is greater than 1007px.</span></span>

## <a name="overriding-the-default-adaptive-behavior"></a><span data-ttu-id="81309-190">Überschreiben des standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="81309-190">Overriding the default adaptive behavior</span></span>

<span data-ttu-id="81309-191">Die Navigationsansicht ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="81309-191">The navigation view automatically changes its display mode based on the amount of screen space available to it.</span></span>
[!NOTE] <span data-ttu-id="81309-192">NavigationView sollte als der Stammcontainer Ihrer App dienen. Dieses Steuerelement ist darauf ausgelegt, die volle Breite und Höhe des App-Fensters einzunehmen.</span><span class="sxs-lookup"><span data-stu-id="81309-192">NavigationView should serve as the root container of your app, this control is designed to span the full width and height of the app window.</span></span>
<span data-ttu-id="81309-193">Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_CompactModeThresholdWidth) und ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ExpandedModeThresholdWidth) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="81309-193">You can override the widths at which the navigation view changes display modes by using the [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_CompactModeThresholdWidth) and ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ExpandedModeThresholdWidth) properties.</span></span> <span data-ttu-id="81309-194">Berücksichtigen Sie die folgenden Szenarien, die veranschaulichen, wann Sie das Anzeigemodusverhalten ggf. anpassen sollten.</span><span class="sxs-lookup"><span data-stu-id="81309-194">Consider the following scenarios that illustrate when you might want to customize the display mode behavior.</span></span>

-  <span data-ttu-id="81309-195">**Häufiges Navigieren** Wenn Sie davon ausgehen, dass Benutzer relativ häufig zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei geringeren Fensterbreiten eingeblendet zu lassen.</span><span class="sxs-lookup"><span data-stu-id="81309-195">**Frequent navigation** If you expect users to navigate between app areas somewhat frequently, consider keeping the pane in view at narrower window widths.</span></span> <span data-ttu-id="81309-196">Eine Musik-App mit Navigationsbereichen für Songs/Alben/Künstler kann eine Bereichsbreite von 280px verwenden und den erweiterten Modus beibehalten, wenn das App-Fenster breiter als 560px ist.</span><span class="sxs-lookup"><span data-stu-id="81309-196">A music app with Songs / Albums / Artists navigation areas may opt for a 280px pane width and remain in Expanded mode while the app window is wider than 560px.</span></span>
```xaml
<NavigationView OpenPaneLength=”280” CompactModeThresholdWidth="560" ExpandedModeThresholdWidth=”560”/>
```
-    <span data-ttu-id="81309-197">**Seltenes Navigieren** Wenn Sie davon ausgehen, dass Benutzer sehr selten zwischen App-Bereichen navigieren, sollten Sie überlegen, den Bereich bei größeren Fensterbreiten ausgeblendet zu lassen.</span><span class="sxs-lookup"><span data-stu-id="81309-197">**Rare navigation** If you expect users to navigate between app areas very infrequently, consider keeping the pane hidden at wider window widths.</span></span> <span data-ttu-id="81309-198">Eine Rechner-App mit mehreren Layouts behält möglicherweise auch dann den minimierten Modus bei, wenn die App auf einem 1080p-Display maximiert ist.</span><span class="sxs-lookup"><span data-stu-id="81309-198">A calculator app with multiple layouts may opt to remain in Minimal mode even when the app is maximized on a 1080p display.</span></span>
```xaml
<NavigationView CompactModeThresholdWidth=”1920” ExpandedModeThresholdWidth=”1920”/>
```
-    <span data-ttu-id="81309-199">**Mehrdeutigkeit** von Symbolen Wenn sich die Navigationsbereiche Ihrer App nicht für aussagekräftige Symbole eignen, vermeiden Sie die Verwendung des kompakten Modus.</span><span class="sxs-lookup"><span data-stu-id="81309-199">**Icon disambiguation** If your app’s navigation areas don’t lend themselves to meaningful icons, avoid using Compact mode.</span></span> <span data-ttu-id="81309-200">Eine Bildanzeige-App mit Navigationsbereichen für Sammlungen/Alben/Ordner zeigt NavigationView bei geringen und mittleren Breiten möglicherweise im minimierten Modus und bei großer Breite im erweiterten Modus an.</span><span class="sxs-lookup"><span data-stu-id="81309-200">An image viewing app with Collections / Albums / Folders navigation areas may opt for showing NavigationView in Minimal mode at narrow and medium widths, and in Expanded mode at wide width.</span></span>
```xaml
<NavigationView CompactModeThresholdWidth=”1008”/>
```

## <a name="interaction"></a><span data-ttu-id="81309-201">Interaktion</span><span class="sxs-lookup"><span data-stu-id="81309-201">Interaction</span></span>

<span data-ttu-id="81309-202">Wenn Benutzer auf eine Navigationskategorie im Bereich tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ItemInvoked)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="81309-202">When users tap on a navigation category in the Pane, NavigationView will show that item as selected and will raise an [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_ItemInvoked) event.</span></span> <span data-ttu-id="81309-203">Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_SelectionChanged)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="81309-203">If the tap results in a new item being selected, NavigationView will also raise a [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview#Windows_UI_Xaml_Controls_NavigationView_SelectionChanged) event.</span></span> <span data-ttu-id="81309-204">Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="81309-204">Your app is responsible for updating the Header and Content with appropriate information in response to this user interaction.</span></span> <span data-ttu-id="81309-205">Darüber hinaus wird empfohlen, den Fokus programmgesteuert vom Navigationselement zum Inhalt zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="81309-205">In addition, we recommend programmatically moving focus from the navigation item to the content.</span></span> <span data-ttu-id="81309-206">Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.</span><span class="sxs-lookup"><span data-stu-id="81309-206">By setting initial focus on load, you streamline the user flow and minimize the expected number of keyboard focus moves.</span></span>

## <a name="how-to-use-navigationview"></a><span data-ttu-id="81309-207">Verwenden von NavigationView</span><span class="sxs-lookup"><span data-stu-id="81309-207">How to use NavigationView</span></span>

<span data-ttu-id="81309-208">Es folgt ein einfaches Beispiel dafür, wie Sie NavigationView in Ihre App integrieren können.</span><span class="sxs-lookup"><span data-stu-id="81309-208">The following is a simple example of how you can incorporate NavigationView into your app.</span></span>

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
                    Loaded="NavView_Loaded">
    <!-- Load NavigationViewItems in NavView_Loaded. -->

        <NavigationView.HeaderTemplate>
            <DataTemplate>
                <Grid>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition/>
                    </Grid.ColumnDefinitions>
                    <TextBlock Style="{StaticResource TitleTextBlockStyle}"
                           FontSize="28"
                           VerticalAlignment="Center"
                           Margin="12,0"
                           Text="Welcome"/>
                    <CommandBar Grid.Column="1"
                            HorizontalAlignment="Right"
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

        <Frame x:Name="ContentFrame">
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
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Apps", Icon = new SymbolIcon(Symbol.AllApps), Tag = "apps" });
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Games", Icon = new SymbolIcon(Symbol.Video), Tag = "games" });
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "Music", Icon = new SymbolIcon(Symbol.Audio), Tag = "music" });
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem()
        { Text = "My content", Icon = new SymbolIcon(Symbol.Folder), Tag = "content" });

    foreach (NavigationViewItem item in NavView.MenuItems)
    {
        if (item.Tag.ToString() == "play")
        {
            NavView.SelectedItem = item;
            break;
        }
    }
}

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{
    if (args.IsSettingsInvoked == true)
    {
        ContentFrame.Navigate(typeof(SettingsPage));
    }
    else
    {
        switch ((args.InvokedItem as NavigationViewItem).Tag)
        {
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
}
```

## <a name="navigation"></a><span data-ttu-id="81309-209">Navigation</span><span class="sxs-lookup"><span data-stu-id="81309-209">Navigation</span></span>

<span data-ttu-id="81309-210">NavigationView zeigt in der Titelleiste Ihrer App nicht automatisch die Zurück-Schaltfläche an und fügt dem Zurück-Stapel auch keinen Inhalt hinzu.</span><span class="sxs-lookup"><span data-stu-id="81309-210">NavigationView does not automatically show the back button in your app’s title bar nor add content to the back stack.</span></span> <span data-ttu-id="81309-211">Das Steuerelement reagiert nicht automatisch auf Drücken der Zurück-Schaltfläche bzw. -Taste von Software oder Hardware.</span><span class="sxs-lookup"><span data-stu-id="81309-211">The control does not automatically respond to software or hardware back button presses.</span></span> <span data-ttu-id="81309-212">Im Abschnitt [Navigationsverlauf und Rückwärtsnavigation](../layout/navigation-history-and-backwards-navigation.md) finden Sie weitere Informationen zu diesem Thema und zum Hinzufügen von Unterstützung für die Navigation zu Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="81309-212">Please see the [history and backwards navigation](../layout/navigation-history-and-backwards-navigation.md) section for more information about this topic and how to add support for navigation to your app.</span></span>


## <a name="related-topics"></a><span data-ttu-id="81309-213">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="81309-213">Related topics</span></span>

* [<span data-ttu-id="81309-214">NavigationView-Klasse</span><span class="sxs-lookup"><span data-stu-id="81309-214">NavigationView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
* [<span data-ttu-id="81309-215">Master/Details</span><span class="sxs-lookup"><span data-stu-id="81309-215">Master/details</span></span>](master-details.md)
* [<span data-ttu-id="81309-216">Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="81309-216">Pivot control</span></span>](tabs-pivot.md)
* [<span data-ttu-id="81309-217">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="81309-217">Navigation basics</span></span>](../layout/navigation-basics.md)
 

 
