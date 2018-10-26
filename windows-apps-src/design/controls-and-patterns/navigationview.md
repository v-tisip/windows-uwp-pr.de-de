---
author: jwmsft
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.author: jimwalk
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 8503c8cde942129c4e7ad6994afb6cd9b29f19a1
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5562061"
---
# <a name="navigation-view"></a><span data-ttu-id="52c10-103">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="52c10-103">Navigation view</span></span>

<span data-ttu-id="52c10-104">Das NavigationView-Steuerelement bietet Navigation auf oberster Ebene für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="52c10-104">The NavigationView control provides top-level navigation for your app.</span></span> <span data-ttu-id="52c10-105">Es mit einer Vielzahl von Bildschirmgrößen anpasst und _oberen_ und _linken_ Navigationsbereich Formate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="52c10-105">It adapts to a variety of screen sizes and supports both _top_ and _left_ navigation styles.</span></span>

![oberen Navigationsleiste](images/nav-view-header.png)<br/>
_<span data-ttu-id="52c10-107">Navigationsansicht unterstützt sowohl am oberen und linken Navigationsbereich oder Menü</span><span class="sxs-lookup"><span data-stu-id="52c10-107">Navigation view supports both top and left navigation pane or menu</span></span>_

> <span data-ttu-id="52c10-108">**Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/windows.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="52c10-108">**Platform APIs**: [Windows.UI.Xaml.Controls.NavigationView class](/uwp/api/windows.ui.xaml.controls.navigationview)</span></span>
>
> <span data-ttu-id="52c10-109">**Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="52c10-109">**Windows UI Library APIs**: [Microsoft.UI.Xaml.Controls.NavigationView class](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span></span>
>
> <span data-ttu-id="52c10-110">Einige Features von NavigationView, z. B. _Top_ -Navigation erfordern Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="52c10-110">Some features of NavigationView, such as _top_ navigation, require Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="52c10-111">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="52c10-111">Is this the right control?</span></span>

<span data-ttu-id="52c10-112">NavigationView ist eine adaptive Navigationssteuerelement, das funktioniert gut für:</span><span class="sxs-lookup"><span data-stu-id="52c10-112">NavigationView is an adaptive navigation control that works well for:</span></span>

- <span data-ttu-id="52c10-113">Bereitstellen einer konsistenten navigationsumgebungen in der gesamten app.</span><span class="sxs-lookup"><span data-stu-id="52c10-113">Providing a consistent navigational experience throughout your app.</span></span>
- <span data-ttu-id="52c10-114">Sparen von Platz auf dem Bildschirm auf kleineren Fenstern.</span><span class="sxs-lookup"><span data-stu-id="52c10-114">Preserving screen real estate on smaller windows.</span></span>
- <span data-ttu-id="52c10-115">Organisieren von Zugriff auf viele Navigationskategorien.</span><span class="sxs-lookup"><span data-stu-id="52c10-115">Organizing access to many navigation categories.</span></span>

<span data-ttu-id="52c10-116">Andere navigationsmuster finden Sie unter [navigationsdesigngrundlagen](../basics/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="52c10-116">For other navigation patterns, see [Navigation design basics](../basics/navigation-basics.md).</span></span>

## <a name="examples"></a><span data-ttu-id="52c10-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="52c10-117">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="52c10-118">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="52c10-118">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/XAML-controls-gallery-app-icon.png" alt="XAML controls gallery" width="168"></img></td>
<td>
    <p><span data-ttu-id="52c10-119">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die App zu öffnen und NavigationView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="52c10-119">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/NavigationView">open the app and see the NavigationView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="52c10-120">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="52c10-120">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="52c10-121">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="52c10-121">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="display-modes"></a><span data-ttu-id="52c10-122">Anzeigemodi</span><span class="sxs-lookup"><span data-stu-id="52c10-122">Display modes</span></span>

> <span data-ttu-id="52c10-123">Die Eigenschaft PaneDisplayMode erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="52c10-123">The PaneDisplayMode property requires Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="52c10-124">Sie können mit der Eigenschaft PaneDisplayMode können verschiedene Navigation Stilen konfigurieren oder Anzeigemodi für die NavigationView.</span><span class="sxs-lookup"><span data-stu-id="52c10-124">You can use the PaneDisplayMode property to configure different navigation styles, or display modes, for the NavigationView.</span></span>

:::row:::
    :::column:::
    ### <a name="top"></a><span data-ttu-id="52c10-125">Oben</span><span class="sxs-lookup"><span data-stu-id="52c10-125">Top</span></span>
    <span data-ttu-id="52c10-126">Der Bereich wird oberhalb des Inhalts positioniert.</span><span class="sxs-lookup"><span data-stu-id="52c10-126">The pane is positioned above the content.</span></span></br>
    `PaneDisplayMode="Top"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die Navigation oben](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="52c10-128">Wir empfehlen _oberen_ Navigationsbereich beim:</span><span class="sxs-lookup"><span data-stu-id="52c10-128">We recommend _top_ navigation when:</span></span>

- <span data-ttu-id="52c10-129">Sie haben 5 oder weniger Navigation auf oberster Ebene Kategorien, die ebenso wichtig sind, und alle zusätzlichen Navigation auf oberster Ebene, die Kategorien, zu denen in der Dropdownliste Überlaufmenü landen weniger wichtig eingestuft werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-129">You have 5 or fewer top-level navigation categories that are equally important, and any additional top-level navigation categories that end up in the dropdown overflow menu are considered less important.</span></span>
- <span data-ttu-id="52c10-130">Sie müssen alle Navigationsoptionen auf dem Bildschirm anzeigen.</span><span class="sxs-lookup"><span data-stu-id="52c10-130">You need to show all navigation options on screen.</span></span>
- <span data-ttu-id="52c10-131">Sie möchten mehr Platz für app-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="52c10-131">You want more space for your app content.</span></span>
- <span data-ttu-id="52c10-132">Symbole können nicht klar Navigationskategorien Ihrer app beschreiben.</span><span class="sxs-lookup"><span data-stu-id="52c10-132">Icons cannot clearly describe your app's navigation categories.</span></span>

:::row:::
    :::column:::
    ### <a name="left"></a><span data-ttu-id="52c10-133">Links</span><span class="sxs-lookup"><span data-stu-id="52c10-133">Left</span></span>
    <span data-ttu-id="52c10-134">Der Bereich erweitert und auf der linken Seite des Inhalts positioniert.</span><span class="sxs-lookup"><span data-stu-id="52c10-134">The pane is expanded and positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="Left"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für erweiterte linken Navigationsbereich](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="52c10-136">Wir empfehlen die _linke_ Navigation bei:</span><span class="sxs-lookup"><span data-stu-id="52c10-136">We recommend _left_ navigation when:</span></span>

- <span data-ttu-id="52c10-137">Sie haben 5 bis 10 ebenso wichtig Navigation auf oberster Ebene Kategorien.</span><span class="sxs-lookup"><span data-stu-id="52c10-137">You have 5-10 equally important top-level navigation categories.</span></span>
- <span data-ttu-id="52c10-138">Navigationskategorien mit weniger Speicherplatz für anderen Inhalten der app sehr hervorgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="52c10-138">You want navigation categories to be very prominent, with less space for other app content.</span></span>

:::row:::
    :::column:::
    ### <a name="leftcompact"></a><span data-ttu-id="52c10-139">LeftCompact</span><span class="sxs-lookup"><span data-stu-id="52c10-139">LeftCompact</span></span>
    <span data-ttu-id="52c10-140">Der Bereich zeigt nur Symbole bis geöffnet, und auf der linken Seite des Inhalts positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-140">The pane shows only icons until opened and is positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="LeftCompact"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für compact linken Navigationsbereich](images/displaymode-leftcompact.png)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ### <a name="leftminimal"></a><span data-ttu-id="52c10-142">LeftMinimal</span><span class="sxs-lookup"><span data-stu-id="52c10-142">LeftMinimal</span></span>
    <span data-ttu-id="52c10-143">Nur die Schaltfläche "Menü" wird angezeigt, bis das Fenster geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-143">Only the menu button is shown until the pane is opened.</span></span> <span data-ttu-id="52c10-144">Beim Öffnen, wird es auf der linken Seite des Inhalts positioniert.</span><span class="sxs-lookup"><span data-stu-id="52c10-144">When opened, it's positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="LeftMinimal"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die minimale linken Navigationsbereich](images/displaymode-leftminimal.png)
    :::column-end:::
:::row-end:::

### <a name="auto"></a><span data-ttu-id="52c10-146">Auto</span><span class="sxs-lookup"><span data-stu-id="52c10-146">Auto</span></span>

<span data-ttu-id="52c10-147">Standardmäßig ist PaneDisplayMode auf Auto festgelegt. Im Auto-Modus die Navigationsansicht anpasst zwischen LeftMinimal, wenn das Fenster schmaler, um LeftCompact ist, und dann von links im Fenster vergrößert wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-147">By default, PaneDisplayMode is set to Auto. In Auto mode, the navigation view adapts between LeftMinimal when the window is narrow, to LeftCompact, and then Left as the window gets wider.</span></span> <span data-ttu-id="52c10-148">Weitere Informationen finden Sie im Abschnitt [adaptives Verhalten](#adaptive-behavior) .</span><span class="sxs-lookup"><span data-stu-id="52c10-148">For more info, see the [adaptive behavior](#adaptive-behavior) section.</span></span>

![Linken Navigationsbereich standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_<span data-ttu-id="52c10-150">Navigation Ansicht standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="52c10-150">Navigation view default adaptive behavior</span></span>_

## <a name="anatomy"></a><span data-ttu-id="52c10-151">Aufbau</span><span class="sxs-lookup"><span data-stu-id="52c10-151">Anatomy</span></span>

<span data-ttu-id="52c10-152">Diese Bilder zeigen das Layout der Bereich, Header und Inhaltsbereiche des Steuerelements für die _oberen_ oder _linken_ Navigationsbereich konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="52c10-152">These images show the layout of the pane, header, and content areas of the control when configured for _top_ or _left_ navigation.</span></span>

![Layout der oberen Navigationsleiste anzeigen](images/topnav-anatomy.png)<br/>
_<span data-ttu-id="52c10-154">Layout der oberen Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="52c10-154">Top navigation layout</span></span>_

![Layout des linken Navigationsbereich anzeigen](images/leftnav-anatomy.png)<br/>
_<span data-ttu-id="52c10-156">Linken Navigationsbereich layout</span><span class="sxs-lookup"><span data-stu-id="52c10-156">Left navigation layout</span></span>_

### <a name="pane"></a><span data-ttu-id="52c10-157">Bereich</span><span class="sxs-lookup"><span data-stu-id="52c10-157">Pane</span></span>

<span data-ttu-id="52c10-158">Die Eigenschaft PaneDisplayMode können Sie um den Bereich über dem Inhalt oder auf der linken Seite des Inhalts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-158">You can use the PaneDisplayMode property to position the pane above the content or to the left of the content.</span></span>

<span data-ttu-id="52c10-159">Der NavigationView-Bereich kann Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="52c10-159">The NavigationView pane can contain:</span></span>

- <span data-ttu-id="52c10-160">[NavigationViewItem](/uwp/api/windows.ui.xaml.controls.navigationviewitem) -Objekte.</span><span class="sxs-lookup"><span data-stu-id="52c10-160">[NavigationViewItem](/uwp/api/windows.ui.xaml.controls.navigationviewitem) objects.</span></span> <span data-ttu-id="52c10-161">Navigationselemente zu bestimmten Seiten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-161">Navigation items for navigating to specific pages.</span></span>
- <span data-ttu-id="52c10-162">[NavigationViewItemSeparator](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator) Objekte.</span><span class="sxs-lookup"><span data-stu-id="52c10-162">[NavigationViewItemSeparator](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator) objects.</span></span> <span data-ttu-id="52c10-163">Trennzeichen Navigationselemente zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-163">Separators for grouping navigation items.</span></span> <span data-ttu-id="52c10-164">Legen Sie die [Opacity](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0 fest, um das Trennzeichen Platz nötig rendern.</span><span class="sxs-lookup"><span data-stu-id="52c10-164">Set the [Opacity](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) property to 0 to render the separator as space.</span></span>
- <span data-ttu-id="52c10-165">[NavigationViewItemHeader](/uwp/api/windows.ui.xaml.controls.navigationviewitemheader) Objekte.</span><span class="sxs-lookup"><span data-stu-id="52c10-165">[NavigationViewItemHeader](/uwp/api/windows.ui.xaml.controls.navigationviewitemheader) objects.</span></span> <span data-ttu-id="52c10-166">Header zum Beschriften von Gruppen von Elementen.</span><span class="sxs-lookup"><span data-stu-id="52c10-166">Headers for labeling groups of items.</span></span>
- <span data-ttu-id="52c10-167">Ein optionales [AutoSuggestBox](auto-suggest-box.md) -Steuerelement für die app-Ebene Suche zulassen.</span><span class="sxs-lookup"><span data-stu-id="52c10-167">An optional [AutoSuggestBox](auto-suggest-box.md) control to allow for app-level search.</span></span> <span data-ttu-id="52c10-168">Weisen Sie das Steuerelement an die [NavigationView.AutoSuggestBox](/uwp/api/windows.ui.xaml.controls.navigationview.autosuggestbox) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="52c10-168">Assign the control to the [NavigationView.AutoSuggestBox](/uwp/api/windows.ui.xaml.controls.navigationview.autosuggestbox) property.</span></span>
- <span data-ttu-id="52c10-169">Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md).</span><span class="sxs-lookup"><span data-stu-id="52c10-169">An optional entry point for [app settings](../app-settings/app-settings-and-data.md).</span></span> <span data-ttu-id="52c10-170">Um die Einstellungen Element auszublenden, die [IsSettingsVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft auf **"false"** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="52c10-170">To hide the settings item, set the [IsSettingsVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) property to **false**.</span></span>

<span data-ttu-id="52c10-171">Der linke Bereich enthält auch:</span><span class="sxs-lookup"><span data-stu-id="52c10-171">The left pane also contains:</span></span>

- <span data-ttu-id="52c10-172">Eine Schaltfläche zum Umschalten des Bereichs geöffnet und geschlossen.</span><span class="sxs-lookup"><span data-stu-id="52c10-172">A menu button to toggle the pane opened and closed.</span></span> <span data-ttu-id="52c10-173">Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.</span><span class="sxs-lookup"><span data-stu-id="52c10-173">On larger app windows when the pane is open, you may choose to hide this button using the [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) property.</span></span>

<span data-ttu-id="52c10-174">Die Navigationsansicht hat eine zurück-Schaltfläche, die sich in der oberen linken Ecke des Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="52c10-174">The navigation view has a back button that is placed in the top left-hand corner of the pane.</span></span> <span data-ttu-id="52c10-175">Es jedoch nicht automatisch behandeln rückwärts Navigation und Hinzufügen von Inhalten zu dem zurück-Stapel.</span><span class="sxs-lookup"><span data-stu-id="52c10-175">However, it does not automatically handle backwards navigation and add content to the back stack.</span></span> <span data-ttu-id="52c10-176">Zum Aktivieren der Rückwärtsnavigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="52c10-176">To enable backwards navigation, see the [backwards navigation](#backwards-navigation) section.</span></span>

<span data-ttu-id="52c10-177">Hier ist der Aufbau detaillierte Bereich für die Positionen oberen und linken Bereich.</span><span class="sxs-lookup"><span data-stu-id="52c10-177">Here is the detailed pane anatomy for the top and left pane positions.</span></span>

#### <a name="top-navigation-pane"></a><span data-ttu-id="52c10-178">Im oberen Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="52c10-178">Top navigation pane</span></span>

![Navigation Ansicht oberen Bereich Anatomie](images/navview-pane-anatomy-horizontal.png)

1. <span data-ttu-id="52c10-180">Header</span><span class="sxs-lookup"><span data-stu-id="52c10-180">Headers</span></span>
1. <span data-ttu-id="52c10-181">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="52c10-181">Navigation items</span></span>
1. <span data-ttu-id="52c10-182">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="52c10-182">Separators</span></span>
1. <span data-ttu-id="52c10-183">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="52c10-183">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="52c10-184">Schaltfläche "Einstellungen" (optional)</span><span class="sxs-lookup"><span data-stu-id="52c10-184">Settings button (optional)</span></span>

#### <a name="left-navigation-pane"></a><span data-ttu-id="52c10-185">Linken Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="52c10-185">Left navigation pane</span></span>

![Links Bereich Anatomie Navigationsansicht](images/navview-pane-anatomy-vertical.png)

1. <span data-ttu-id="52c10-187">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="52c10-187">Menu button</span></span>
1. <span data-ttu-id="52c10-188">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="52c10-188">Navigation items</span></span>
1. <span data-ttu-id="52c10-189">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="52c10-189">Separators</span></span>
1. <span data-ttu-id="52c10-190">Header</span><span class="sxs-lookup"><span data-stu-id="52c10-190">Headers</span></span>
1. <span data-ttu-id="52c10-191">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="52c10-191">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="52c10-192">Schaltfläche "Einstellungen" (optional)</span><span class="sxs-lookup"><span data-stu-id="52c10-192">Settings button (optional)</span></span>

#### <a name="pane-footer"></a><span data-ttu-id="52c10-193">Fußzeile</span><span class="sxs-lookup"><span data-stu-id="52c10-193">Pane footer</span></span>

<span data-ttu-id="52c10-194">Sie können frei formulierte Inhalte in der Fußzeile des platzieren, indem Sie es an die Eigenschaft [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="52c10-194">You can place free-form content in the pane's footer by adding it to the [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) property.</span></span>

:::row:::
    :::column:::
    ![Bereich Fußzeile oben nav](images/navview-freeform-footer-top.png)<br>
     _<span data-ttu-id="52c10-196">Oberen Bereich Fußzeile</span><span class="sxs-lookup"><span data-stu-id="52c10-196">Top pane footer</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    _<span data-ttu-id="52c10-198">Linke Fußzeile</span><span class="sxs-lookup"><span data-stu-id="52c10-198">Left pane footer</span></span>_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-title-and-header"></a><span data-ttu-id="52c10-199">Bereich Titel und header</span><span class="sxs-lookup"><span data-stu-id="52c10-199">Pane title and header</span></span>

<span data-ttu-id="52c10-200">Sie können durch Festlegen der Eigenschaft [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) Textinhalt im Headerbereich platzieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-200">You can place text content in the pane header area by setting the [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) property.</span></span> <span data-ttu-id="52c10-201">Sie akzeptiert eine Zeichenfolge und zeigt den Text neben der Schaltfläche "Menü".</span><span class="sxs-lookup"><span data-stu-id="52c10-201">It takes a string and shows the text next to the menu button.</span></span>

<span data-ttu-id="52c10-202">Zum Hinzufügen von nicht-Text-Inhalt, z. B. ein Bild oder ein Logo, können Sie jedes Element im Header des Bereichs platzieren, indem Sie es an die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="52c10-202">To add non-text content, such as an image or logo, you can place any element in the pane's header by adding it to the [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) property.</span></span>

<span data-ttu-id="52c10-203">Wenn PaneTitle und PaneHeader festgelegt sind, wird der Inhalt horizontal neben die Menütaste, mit der PaneTitle, die Menütaste am nächsten gestapelt.</span><span class="sxs-lookup"><span data-stu-id="52c10-203">If both PaneTitle and PaneHeader are set, the content is stacked horizontally next to the menu button, with the PaneTitle closest to the menu button.</span></span>

:::row:::
    :::column:::
    ![Bereich Header oben nav](images/navview-freeform-header-top.png)<br>
     _<span data-ttu-id="52c10-205">Oberen Bereich header</span><span class="sxs-lookup"><span data-stu-id="52c10-205">Top pane header</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich Header linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    _<span data-ttu-id="52c10-207">Linken Bereich header</span><span class="sxs-lookup"><span data-stu-id="52c10-207">Left pane header</span></span>_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-content"></a><span data-ttu-id="52c10-208">Bereich Inhalt</span><span class="sxs-lookup"><span data-stu-id="52c10-208">Pane content</span></span>

<span data-ttu-id="52c10-209">Sie können frei formulierte Inhalte im Bereich platzieren, indem Sie es an die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="52c10-209">You can place free-form content in the pane by adding it to the [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) property.</span></span>

:::row:::
    :::column:::
    ![Bereich benutzerdefinierte Inhalte oben nav](images/navview-freeform-pane-top.png)<br>
     _<span data-ttu-id="52c10-211">Oberen Bereich benutzerdefiniertem Inhalt</span><span class="sxs-lookup"><span data-stu-id="52c10-211">Top pane custom content</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich Benutzerinhalte linke Navigationsleiste](images/navview-freeform-pane-left.png)<br>
    _<span data-ttu-id="52c10-213">Linken Bereich benutzerdefiniertem Inhalt</span><span class="sxs-lookup"><span data-stu-id="52c10-213">Left pane custom content</span></span>_<br>
    :::column-end:::
:::row-end:::

### <a name="header"></a><span data-ttu-id="52c10-214">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="52c10-214">Header</span></span>

<span data-ttu-id="52c10-215">Sie können einen Seitentitel hinzufügen, durch das Festlegen der [Header](/uwp/api/windows.ui.xaml.controls.navigationview.header) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="52c10-215">You can add a page title by setting the [Header](/uwp/api/windows.ui.xaml.controls.navigationview.header) property.</span></span>

![Beispiel für die Navigation Ansichtsbereich header](images/nav-header.png)<br/>
_<span data-ttu-id="52c10-217">Navigation Ansicht header</span><span class="sxs-lookup"><span data-stu-id="52c10-217">Navigation view header</span></span>_

<span data-ttu-id="52c10-218">Der Kopfzeilenbereich die Navigationsschaltfläche "in der linken Seite Position vertikal ausgerichtet ist, und unter dem Bereich in der oberen Bereich Position liegt.</span><span class="sxs-lookup"><span data-stu-id="52c10-218">The header area is vertically aligned with the navigation button in the left pane position, and lies below the pane in the top pane position.</span></span> <span data-ttu-id="52c10-219">Es hat eine feste Höhe von 52 Pixel.</span><span class="sxs-lookup"><span data-stu-id="52c10-219">It has a fixed height of 52 px.</span></span> <span data-ttu-id="52c10-220">Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="52c10-220">Its purpose is to hold the page title of the selected nav category.</span></span> <span data-ttu-id="52c10-221">Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="52c10-221">The header is docked to the top of the page and acts as a scroll clipping point for the content area.</span></span>

<span data-ttu-id="52c10-222">Die Kopfzeile ist jedes Mal, wenn der NavigationView im minimierten Anzeigemodus ist sichtbar.</span><span class="sxs-lookup"><span data-stu-id="52c10-222">The header is visible any time the NavigationView is in Minimal display mode.</span></span> <span data-ttu-id="52c10-223">Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-223">You may choose to hide the header in other modes, which are used on larger window widths.</span></span> <span data-ttu-id="52c10-224">Um die Kopfzeile auszublenden, die [AlwaysShowHeader](/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) -Eigenschaft auf **"false"** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="52c10-224">To hide the header, set the [AlwaysShowHeader](/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) property to **false**.</span></span>

### <a name="content"></a><span data-ttu-id="52c10-225">Inhalt</span><span class="sxs-lookup"><span data-stu-id="52c10-225">Content</span></span>

![Beispiel für die Navigation Ansicht Inhaltsbereich](images/nav-content.png)<br/>
_<span data-ttu-id="52c10-227">Inhalt der Navigation anzeigen</span><span class="sxs-lookup"><span data-stu-id="52c10-227">Navigation view content</span></span>_

<span data-ttu-id="52c10-228">Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="52c10-228">The content area is where most of the information for the selected nav category is displayed.</span></span>

<span data-ttu-id="52c10-229">Wir empfehlen 12px Ränder für Ihren Inhaltsbereich, wenn sich NavigationView im **minimierten** Modus befindet und 24 Ränder andernfalls.</span><span class="sxs-lookup"><span data-stu-id="52c10-229">We recommend 12px margins for your content area when NavigationView is in **Minimal** mode and 24px margins otherwise.</span></span>

## <a name="adaptive-behavior"></a><span data-ttu-id="52c10-230">Adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="52c10-230">Adaptive behavior</span></span>

<span data-ttu-id="52c10-231">In der Standardeinstellung ändert die Navigationsansicht automatisch den Anzeigemodus basierend auf der Größe des Bildschirmbereichs verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="52c10-231">By default, the navigation view automatically changes its display mode based on the amount of screen space available to it.</span></span> <span data-ttu-id="52c10-232">Die Eigenschaften [CompactModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.compactmodethresholdwidth) und [ExpandedModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.expandedmodethresholdwidth) geben die Haltepunkte, an denen der Anzeigemodus ändert.</span><span class="sxs-lookup"><span data-stu-id="52c10-232">The [CompactModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.compactmodethresholdwidth) and [ExpandedModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.expandedmodethresholdwidth) properties specify the breakpoints at which the display mode changes.</span></span> <span data-ttu-id="52c10-233">Sie können diese Werte angepasst werden, das adaptive anzeigemodusverhalten ändern.</span><span class="sxs-lookup"><span data-stu-id="52c10-233">You can modify these values to customize the adaptive display mode behavior.</span></span>

### <a name="default"></a><span data-ttu-id="52c10-234">Standard</span><span class="sxs-lookup"><span data-stu-id="52c10-234">Default</span></span>

<span data-ttu-id="52c10-235">Wenn PaneDisplayMode auf den Standardwert **Auto**festgelegt ist, ist das adaptive Verhalten anzeigen:</span><span class="sxs-lookup"><span data-stu-id="52c10-235">When PaneDisplayMode is set to its default value of **Auto**, the adaptive behavior is to show:</span></span>

- <span data-ttu-id="52c10-236">Eine erweiterte linken Bereich auf großen fensterbreiten (1008 Pixel oder größer).</span><span class="sxs-lookup"><span data-stu-id="52c10-236">An expanded left pane on large window widths (1008px or greater).</span></span>
- <span data-ttu-id="52c10-237">Ein Linker, nur Symbol, Navigationsbereich (LeftCompact) bei mittelgroßen fensterbreiten (641 Pixel bis 1007 Pixel).</span><span class="sxs-lookup"><span data-stu-id="52c10-237">A left, icon-only, nav pane (LeftCompact) on medium window widths (641px to 1007px).</span></span>
- <span data-ttu-id="52c10-238">Nur eine Menüschaltfläche (LeftMinimal) für kleine fensterbreiten (640 Pixel oder weniger).</span><span class="sxs-lookup"><span data-stu-id="52c10-238">Only a menu button (LeftMinimal) on small window widths (640px or less).</span></span>

<span data-ttu-id="52c10-239">Weitere Informationen zu Fenstergrößen für adaptives Verhalten finden Sie unter [Bildschirmgrößen und Haltepunkte](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="52c10-239">For more information about window sizes for adaptive behavior, see [Screen sizes and breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

![Linken Navigationsbereich standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_<span data-ttu-id="52c10-241">Navigation Ansicht standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="52c10-241">Navigation view default adaptive behavior</span></span>_

### <a name="minimal"></a><span data-ttu-id="52c10-242">Minimiert</span><span class="sxs-lookup"><span data-stu-id="52c10-242">Minimal</span></span>

<span data-ttu-id="52c10-243">Ein zweites Allgemeines adaptives Muster ist die Verwendung einen erweiterten linken Bereich auf großen fensterbreiten und nur eine Schaltfläche auf beiden kleinen und mittelgroßen fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="52c10-243">A second common adaptive pattern is to use an expanded left pane on large window widths, and only a menu button on both medium and small window widths.</span></span>

<span data-ttu-id="52c10-244">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="52c10-244">We recommend this when:</span></span>

- <span data-ttu-id="52c10-245">Sie möchten mehr Platz für app-Inhalte auf kleinere fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="52c10-245">You want more space for app content on smaller window widths.</span></span>
- <span data-ttu-id="52c10-246">Ihre Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="52c10-246">Your navigation categories cannot be clearly represented with icons.</span></span>

![Minimale adaptives Verhalten linken Navigationsbereich](images/adaptive-behavior-minimal.png)<br/>
_<span data-ttu-id="52c10-248">Navigation Ansicht "minimal" adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="52c10-248">Navigation view "minimal" adaptive behavior</span></span>_

<span data-ttu-id="52c10-249">Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf die Breite, die den Bereich zu reduzieren soll.</span><span class="sxs-lookup"><span data-stu-id="52c10-249">To configure this behavior, set CompactModeThresholdWidth to the width at which you want the pane to collapse.</span></span> <span data-ttu-id="52c10-250">Hier wird dieser vom Standardwert 640, 1007 geändert.</span><span class="sxs-lookup"><span data-stu-id="52c10-250">Here, it's changed from the default of 640 to 1007.</span></span> <span data-ttu-id="52c10-251">Sie sollten auch ExpandedModeThresholdWidth, um sicherzustellen, dass die Werte nicht zu Konflikten festlegen.</span><span class="sxs-lookup"><span data-stu-id="52c10-251">You should also set ExpandedModeThresholdWidth to ensure the values don't conflict.</span></span>

```xaml
<NavigationView CompactModeThresholdWidth="1007" ExpandedModeThresholdWidth="1007"/>
```

### <a name="compact"></a><span data-ttu-id="52c10-252">Kompakt</span><span class="sxs-lookup"><span data-stu-id="52c10-252">Compact</span></span>

<span data-ttu-id="52c10-253">Eine dritte häufiges adaptive Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und eine LeftCompact, nur Symbol, Navigationsbereich auf beiden kleinen und mittelgroßen fensterbreiten verwenden.</span><span class="sxs-lookup"><span data-stu-id="52c10-253">A third common adaptive pattern is to use an expanded left pane on large window widths, and a LeftCompact, icon-only, nav pane on both medium and small window widths.</span></span>

<span data-ttu-id="52c10-254">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="52c10-254">We recommend this when:</span></span>

- <span data-ttu-id="52c10-255">Es ist wichtig, immer alle Navigationsoptionen auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-255">It is important to always show all navigation options on screen.</span></span>
- <span data-ttu-id="52c10-256">Ihre Navigationskategorien können deutlich mit Symbolen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-256">Your navigation categories can be clearly represented with icons.</span></span>

![Linken Navigationsbereich compact adaptives Verhalten](images/adaptive-behavior-compact.png)<br/>
_<span data-ttu-id="52c10-258">Navigation Ansicht "compact" adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="52c10-258">Navigation view "compact" adaptive behavior</span></span>_

<span data-ttu-id="52c10-259">Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf 0 fest.</span><span class="sxs-lookup"><span data-stu-id="52c10-259">To configure this behavior, set CompactModeThresholdWidth to 0.</span></span>

```xaml
<NavigationView CompactModeThresholdWidth="0"/>
```

### <a name="no-adaptive-behavior"></a><span data-ttu-id="52c10-260">Keine adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="52c10-260">No adaptive behavior</span></span>

<span data-ttu-id="52c10-261">Legen Sie zum Deaktivieren des automatischen adaptiven Verhaltens PaneDisplayMode auf einen anderen Wert als Auto. Hier wird es festgelegt LeftMinimal, sodass nur die Menütaste unabhängig von der Breite des Fensters angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-261">To disable the automatic adaptive behavior, set PaneDisplayMode to a value other than Auto. Here, it's set to LeftMinimal, so only the menu button is shown regardless of the window width.</span></span>

![Linke Navigationsleiste keine adaptives Verhalten](images/adaptive-behavior-none.png)<br/>
_<span data-ttu-id="52c10-263">Navigationsansicht mit PaneDisplayMode auf LeftMinimal festgelegt</span><span class="sxs-lookup"><span data-stu-id="52c10-263">Navigation view with PaneDisplayMode set to LeftMinimal</span></span>_

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

<span data-ttu-id="52c10-264">Wie zuvor im Abschnitt _Anzeigemodi_ beschrieben, können Sie den Bereich immer am oberen, immer erweiterten, immer compact oder immer minimale ist festlegen.</span><span class="sxs-lookup"><span data-stu-id="52c10-264">As described previously in the _Display modes_ section, you can set the pane to be always on top, always expanded, always compact, or always minimal.</span></span> <span data-ttu-id="52c10-265">Sie können auch die Anzeigemodi selbst im app-Code verwalten.</span><span class="sxs-lookup"><span data-stu-id="52c10-265">You can also manage the display modes yourself in your app code.</span></span> <span data-ttu-id="52c10-266">Ein Beispiel hierfür wird im nächsten Abschnitt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="52c10-266">An example of this is shown in the next section.</span></span>

### <a name="top-to-left-navigation"></a><span data-ttu-id="52c10-267">Oberen, linken Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="52c10-267">Top to left navigation</span></span>

<span data-ttu-id="52c10-268">Wenn Sie oberen Navigationsleiste in Ihrer app verwenden, reduzieren Navigationselemente in ein Überlaufmenü das Fenster Breite verringert.</span><span class="sxs-lookup"><span data-stu-id="52c10-268">When you use top navigation in your app, navigation items collapse into an overflow menu as the window width decreases.</span></span> <span data-ttu-id="52c10-269">Wenn Ihre app-Fenster schmaler ist, können sie ein besseres Benutzererlebnis, um die PaneDisplayMode von oben LeftMinimal Navigation, statt alles, was die Elemente in das Überlaufmenü reduzieren Hinweisen zu wechseln bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="52c10-269">When your app window is narrow, it can provide a better user experience to switch the PaneDisplayMode from Top to LeftMinimal navigation, rather than letting all the items collapse into the overflow menu.</span></span>

<span data-ttu-id="52c10-270">Wir empfehlen die Verwendung der oberen Navigationsleiste auf großen Fenstergrößen und linken Navigationsbereich auf kleinen Fenster die Größe bei:</span><span class="sxs-lookup"><span data-stu-id="52c10-270">We recommend using top navigation on large window sizes and left navigation on small window sizes when:</span></span>

- <span data-ttu-id="52c10-271">Sie haben eine Reihe von gleichermaßen wichtig Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in diesen auf dem Bildschirm passt, die linke Navigation, damit sie genauso wichtig wie erhalten Sie reduzieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-271">You have a set of equally important top-level navigation categories to be displayed together, such that if one category in this set doesn't fit on screen, you collapse to left navigation to give them equal importance.</span></span>
- <span data-ttu-id="52c10-272">Möchten Sie so viel Content Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten.</span><span class="sxs-lookup"><span data-stu-id="52c10-272">You wish to preserve as much content space as possible in small window sizes.</span></span>

<span data-ttu-id="52c10-273">Dieses Beispiel zeigt, wie Sie eine Eigenschaft [VisualStateManager](/uwp/api/Windows.UI.Xaml.VisualStateManager) und [AdaptiveTrigger.MinWindowWidth](/uwp/api/windows.ui.xaml.adaptivetrigger.minwindowwidth) verwenden, um zwischen den oberen und LeftMinimal Navigation wechseln.</span><span class="sxs-lookup"><span data-stu-id="52c10-273">This example shows how to use a [VisualStateManager](/uwp/api/Windows.UI.Xaml.VisualStateManager) and [AdaptiveTrigger.MinWindowWidth](/uwp/api/windows.ui.xaml.adaptivetrigger.minwindowwidth) property to switch between Top and LeftMinimal navigation.</span></span>

![Beispiel für oberen oder linken adaptives Verhalten 1](images/navigation-top-to-left.png)

```xaml
<Grid >
    <NavigationView x:Name="NavigationViewControl" >
        <NavigationView.MenuItems>
            <NavigationViewItem Content="A" x:Name="A" />
            <NavigationViewItem Content="B" x:Name="B" />
            <NavigationViewItem Content="C" x:Name="C" />
        </NavigationView.MenuItems>
    </NavigationView>

    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger
                        MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                </VisualState.StateTriggers>

                <VisualState.Setters>
                    <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>

```

> [!TIP]
> <span data-ttu-id="52c10-275">Wenn Sie AdaptiveTrigger.MinWindowWidth verwenden, wird der visuelle Zustand ausgelöst, wenn das Fenster breiter als die angegebene minimale Breite ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-275">When you use AdaptiveTrigger.MinWindowWidth, the visual state is triggered when the window is wider than the specified minimum width.</span></span> <span data-ttu-id="52c10-276">Dies bedeutet, dass der standardmäßigen XAML-Code definiert das schmale Fenster, und der VisualState definiert die Änderungen, die angewendet werden, wenn das Fenster vergrößert wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-276">This means the default XAML defines the narrow window, and the VisualState defines the modifications that are applied when the window gets wider.</span></span> <span data-ttu-id="52c10-277">Der Standardwert PaneDisplayMode Navigationsansicht Auto ist, sodass kleiner oder gleich CompactModeThresholdWidth, wird die Breite des Fensters LeftMinimal Navigation verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-277">The default PaneDisplayMode for the navigation view is Auto, so when the window width is less than or equal to CompactModeThresholdWidth, LeftMinimal navigation is used.</span></span> <span data-ttu-id="52c10-278">Wenn das Fenster vergrößert wird, der VisualState überschreibt die standardmäßige und oberen Navigationsleiste dient.</span><span class="sxs-lookup"><span data-stu-id="52c10-278">When the window gets wider, the VisualState overrides the default, and Top navigation is used.</span></span>

## <a name="navigation"></a><span data-ttu-id="52c10-279">Navigation</span><span class="sxs-lookup"><span data-stu-id="52c10-279">Navigation</span></span>

<span data-ttu-id="52c10-280">Die Navigationsansicht ausführen nicht automatisch alle Navigationsaufgaben.</span><span class="sxs-lookup"><span data-stu-id="52c10-280">The navigation view doesn't perform any navigation tasks automatically.</span></span> <span data-ttu-id="52c10-281">Wenn der Benutzer auf ein Navigationselement tippen, wird die Navigationsansicht zeigt dieses Element als ausgewählt und löst ein [ItemInvoked](/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="52c10-281">When the user taps on a navigation item, the navigation view shows that item as selected and raises an [ItemInvoked](/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) event.</span></span> <span data-ttu-id="52c10-282">Wenn das Tippen ein neues Element ausgewählt wird, wird ein [SelectionChanged](/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) -Ereignis auch ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="52c10-282">If the tap results in a new item being selected, a [SelectionChanged](/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) event is also raised.</span></span>

<span data-ttu-id="52c10-283">Sie können entweder-Ereignis, um Aufgaben im Zusammenhang mit der gewünschten Navigation behandeln.</span><span class="sxs-lookup"><span data-stu-id="52c10-283">You can handle either event to perform tasks related to the requested navigation.</span></span> <span data-ttu-id="52c10-284">Sie behandeln soll, hängt das Verhalten, die, das Sie für Ihre app verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="52c10-284">Which one you should handle depends on the behavior you want for your app.</span></span> <span data-ttu-id="52c10-285">In der Regel für die angeforderte Seite navigieren und den Navigation Ansicht Header in Reaktion auf diese Ereignisse zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="52c10-285">Typically, you navigate to the requested page and update the navigation view header in response to these events.</span></span>

<span data-ttu-id="52c10-286">**ItemInvoked** wird jedes Mal, die der Benutzer auf ein Navigationselement tippt ausgelöst, auch wenn es bereits aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-286">**ItemInvoked** is raised any time the user taps a navigation item, even if it's already selected.</span></span> <span data-ttu-id="52c10-287">(Das Element kann auch mit einer entsprechenden Aktion mit Maus, Tastatur oder anderer Eingaben aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-287">(The item can also be invoked with an equivalent action using mouse, keyboard, or other input.</span></span> <span data-ttu-id="52c10-288">Weitere Informationen finden Sie unter [Eingabe und Interaktionen](../input/index.md).) Wenn Sie in den ItemInvoked-Ereignishandler navigieren, wird standardmäßig die Seite geladen werden, und ein doppelter Eintrag Navigationsstapel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-288">For more info, see [Input and interactions](../input/index.md).) If you navigate in the ItemInvoked handler, by default, the page will be reloaded, and a duplicate entry is added to the navigation stack.</span></span> <span data-ttu-id="52c10-289">Wenn Sie navigieren, wenn ein Element aufgerufen wird, sollten Sie verbieten Neuladen der Seite oder stellen Sie sicher, dass ein doppelter Eintrag nicht in der navigationsbackstack erstellt wird, wenn die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-289">If you navigate when an item is invoked, you should disallow reloading the page, or ensure that a duplicate entry is not created in the navigation backstack when the page is reloaded.</span></span> <span data-ttu-id="52c10-290">(Siehe Codebeispiele.)</span><span class="sxs-lookup"><span data-stu-id="52c10-290">(See code examples.)</span></span>

<span data-ttu-id="52c10-291">**SelectionChanged** kann von einem Benutzer Aufrufen eines Elements, das derzeit ausgewählte ist oder programmgesteuert ändern das ausgewählte Element ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-291">**SelectionChanged** can be raised by a user invoking an item that isn't currently selected, or by programmatically changing the selected item.</span></span> <span data-ttu-id="52c10-292">Wenn die Änderung der Auswahl tritt auf, da ein Benutzer ein Element aufgerufen wird, tritt das ItemInvoked-Ereignis zuerst.</span><span class="sxs-lookup"><span data-stu-id="52c10-292">If the selection change occurs because a user invoked an item, the ItemInvoked event occurs first.</span></span> <span data-ttu-id="52c10-293">Wenn die Änderung der Auswahl programmgesteuerten ist, wird die ItemInvoked nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="52c10-293">If the selection change is programmatic, ItemInvoked is not raised.</span></span>

### <a name="backwards-navigation"></a><span data-ttu-id="52c10-294">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="52c10-294">Backwards navigation</span></span>

<span data-ttu-id="52c10-295">NavigationView verfügt über eine integrierte Schaltfläche "zurück". wie bei Vorwärtsnavigation, sie jedoch nicht ausführen, rückwärts Navigation automatisch.</span><span class="sxs-lookup"><span data-stu-id="52c10-295">NavigationView has a built-in back button; but, as with forward navigation, it doesn't perform backwards navigation automatically.</span></span> <span data-ttu-id="52c10-296">Wenn der Benutzer die zurück-Schaltfläche tippt, wird das [BackRequested](/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) -Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="52c10-296">When the user taps the back button, the [BackRequested](/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) event is raised.</span></span> <span data-ttu-id="52c10-297">Sie behandeln dieses Ereignis, um rückwärts Navigation durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="52c10-297">You handle this event to perform backwards navigation.</span></span> <span data-ttu-id="52c10-298">Weitere Informationen und Codebeispiele finden Sie unter [Navigationsverlauf und Rückwärtsnavigation Navigation](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="52c10-298">For more info and code examples, see [Navigation history and backwards navigation](../basics/navigation-history-and-backwards-navigation.md).</span></span>

<span data-ttu-id="52c10-299">Im minimalen oder kompakten Modus ist als Flyout geöffnet die Navigationsansicht Bereich.</span><span class="sxs-lookup"><span data-stu-id="52c10-299">In Minimal or Compact mode, the navigation view Pane is open as a flyout.</span></span> <span data-ttu-id="52c10-300">In diesem Fall, wird Klicken Sie auf die Schaltfläche "zurück" Schließen des Bereichs und stattdessen das **PaneClosing** -Ereignis auslösen.</span><span class="sxs-lookup"><span data-stu-id="52c10-300">In this case, clicking the back button will close the Pane and raise the **PaneClosing** event instead.</span></span>

<span data-ttu-id="52c10-301">Sie können ausblenden oder deaktivieren die Schaltfläche "zurück" durch Festlegen dieser Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="52c10-301">You can hide or disable the back button by setting these properties:</span></span>

- <span data-ttu-id="52c10-302">[IsBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible): Verwenden Sie zum ein- und Ausblenden der Schaltfläche "zurück".</span><span class="sxs-lookup"><span data-stu-id="52c10-302">[IsBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible): use to show and hide the back button.</span></span> <span data-ttu-id="52c10-303">Diese Eigenschaft akzeptiert einen Wert von der [NavigationViewBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationviewbackbuttonvisible) -Enumeration und standardmäßig auf **Auto** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-303">This property takes a value of the [NavigationViewBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationviewbackbuttonvisible) enumeration, and is set to **Auto** by default.</span></span> <span data-ttu-id="52c10-304">Wenn die Schaltfläche "Collapsed" ist, ist es auch keinen Platz im Layout dafür reserviert.</span><span class="sxs-lookup"><span data-stu-id="52c10-304">When the button is collapsed, no space is reserved for it in the layout.</span></span>
- <span data-ttu-id="52c10-305">[IsBackEnabled](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled): Verwenden Sie zum Aktivieren oder deaktivieren die Schaltfläche "zurück".</span><span class="sxs-lookup"><span data-stu-id="52c10-305">[IsBackEnabled](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled): use to enable or disable the back button.</span></span> <span data-ttu-id="52c10-306">Diese Eigenschaft der Eigenschaft [CanGoBack](/uwp/api/windows.ui.xaml.controls.frame.cangoback) Navigations-Frame können Sie Daten gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="52c10-306">You can data bind this property to the [CanGoBack](/uwp/api/windows.ui.xaml.controls.frame.cangoback) property of your navigation frame.</span></span> <span data-ttu-id="52c10-307">**BackRequested** wird nicht ausgelöst, wenn **IsBackEnabled** auf **"false"** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-307">**BackRequested** is not raised if **IsBackEnabled** is **false**.</span></span>

:::row:::
    :::column:::
        ![Navigation view back button in the left navigation pane](images/leftnav-back.png)<br/>
        _The back button in the left navigation pane_
    :::column-end:::
    :::column:::
        ![Navigation view back button in the top navigation pane](images/topnav-back.png)<br/>
        _The back button in the top navigation pane_
    :::column-end:::
:::row-end:::

## <a name="code-example"></a><span data-ttu-id="52c10-308">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="52c10-308">Code example</span></span>

<span data-ttu-id="52c10-309">Dieses Beispiel zeigt, wie Sie NavigationView mit ein oberer Navigationsbereich auf großen Fenstergrößen und einem linken Navigationsbereich auf kleinen Fenstergrößen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="52c10-309">This example shows how you can use NavigationView with both a top navigation pane on large window sizes and a left navigation pane on small window sizes.</span></span> <span data-ttu-id="52c10-310">Es kann an Navigation mit Links angepasst werden, indem Sie die _oberen_ Navigationsbereich Einstellungen im VisualStateManager entfernen.</span><span class="sxs-lookup"><span data-stu-id="52c10-310">It can be adapted to left-only navigation by removing the _top_ navigation settings in the VisualStateManager.</span></span>

<span data-ttu-id="52c10-311">Das Beispiel zeigt eine empfohlene Vorgehensweise zur Navigationsdaten einrichten, das für viele häufige Szenarien geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="52c10-311">The example demonstrates a recommended way to set up navigation data that will work for many common scenarios.</span></span> <span data-ttu-id="52c10-312">Es wird veranschaulicht, wie die Rückwärtsnavigation mit der zurück-Schaltfläche und Tastatur Navigation NavigationView implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="52c10-312">It also demonstrates how to implement backwards navigation with NavigationView's back button and keyboard navigation.</span></span>

<span data-ttu-id="52c10-313">In diesem Code wird davon ausgegangen, dass Ihre app Seiten mit den folgenden Namen zu navigieren enthält: _HomePage_, _AppsPage_, _GamesPage_, _MusicPage_, _MyContentPage_und _DruckerÄndernDruckereinstellungenSeite_.</span><span class="sxs-lookup"><span data-stu-id="52c10-313">This code assumes that your app contains pages with the following names to navigate to: _HomePage_, _AppsPage_, _GamesPage_, _MusicPage_, _MyContentPage_, and _SettingsPage_.</span></span> <span data-ttu-id="52c10-314">Code für diese Seiten wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="52c10-314">Code for these pages is not shown.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52c10-315">Informationen zu app Seiten wird in einem [ValueTuple](https://docs.microsoft.com/dotnet/api/system.valuetuple)gespeichert.</span><span class="sxs-lookup"><span data-stu-id="52c10-315">Information about the app's pages is stored in a [ValueTuple](https://docs.microsoft.com/dotnet/api/system.valuetuple).</span></span> <span data-ttu-id="52c10-316">Diese Struktur erfordert, dass die Mindestversion für Ihre app-Projekt SDK 17763 oder größer sein muss.</span><span class="sxs-lookup"><span data-stu-id="52c10-316">This struct requires that the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="52c10-317">Wenn Sie die WinUI Version von NavigationView für frühere Versionen von Windows 10 verwenden, können Sie stattdessen das [System.ValueTuple NuGet-Paket](https://www.nuget.org/packages/System.ValueTuple/) .</span><span class="sxs-lookup"><span data-stu-id="52c10-317">If you use the WinUI version of NavigationView to target earlier versions of Windows 10, you can use the [System.ValueTuple NuGet package](https://www.nuget.org/packages/System.ValueTuple/) instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52c10-318">Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden.</span><span class="sxs-lookup"><span data-stu-id="52c10-318">This code shows how to use the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/) version of NavigationView.</span></span> <span data-ttu-id="52c10-319">Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="52c10-319">If you use the platform version of NavigationView instead, the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="52c10-320">Wenn die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc:`.</span><span class="sxs-lookup"><span data-stu-id="52c10-320">To use the platform version, remove all references to `muxc:`.</span></span>

```xaml
<!-- xmlns:muxc="using:Microsoft.UI.Xaml.Controls" -->
<Grid>
    <muxc:NavigationView x:Name="NavView"
                         Loaded="NavView_Loaded"
                         ItemInvoked="NavView_ItemInvoked"
                         BackRequested="NavView_BackRequested">
        <muxc:NavigationView.MenuItems>
            <muxc:NavigationViewItem Tag="home" Icon="Home" Content="Home"/>
            <muxc:NavigationViewItemSeparator/>
            <muxc:NavigationViewItemHeader x:Name="MainPagesHeader"
                                           Content="Main pages"/>
            <muxc:NavigationViewItem Tag="apps" Content="Apps">
                <muxc:NavigationViewItem.Icon>
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xEB3C;"/>
                </muxc:NavigationViewItem.Icon>
            </muxc:NavigationViewItem>
            <muxc:NavigationViewItem Tag="games" Content="Games">
                <muxc:NavigationViewItem.Icon>
                    <FontIcon FontFamily="Segoe MDL2 Assets" Glyph="&#xE7FC;"/>
                </muxc:NavigationViewItem.Icon>
            </muxc:NavigationViewItem>
            <muxc:NavigationViewItem Tag="music" Icon="Audio" Content="Music"/>
        </muxc:NavigationView.MenuItems>

        <muxc:NavigationView.AutoSuggestBox>
            <!-- See AutoSuggestBox documentation for
                 more info about how to implement search. -->
            <AutoSuggestBox x:Name="NavViewSearchBox" QueryIcon="Find"/>
        </muxc:NavigationView.AutoSuggestBox>

        <ScrollViewer>
            <Frame x:Name="ContentFrame" Padding="12,0,12,24" IsTabStop="True"
                   NavigationFailed="ContentFrame_NavigationFailed"/>
        </ScrollViewer>
    </muxc:NavigationView>

    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger
                        MinWindowWidth="{x:Bind NavView.CompactModeThresholdWidth}"/>
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <!-- Remove the next 3 lines for left-only navigation. -->
                    <Setter Target="NavView.PaneDisplayMode" Value="Top"/>
                    <Setter Target="NavViewSearchBox.Width" Value="200"/>
                    <Setter Target="MainPagesHeader.Visibility" Value="Collapsed"/>
                    <!-- Leave the next line for left-only navigation. -->
                    <Setter Target="ContentFrame.Padding" Value="24,0,24,24"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
</Grid>
```

> [!IMPORTANT]
> <span data-ttu-id="52c10-321">Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden.</span><span class="sxs-lookup"><span data-stu-id="52c10-321">This code shows how to use the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/) version of NavigationView.</span></span> <span data-ttu-id="52c10-322">Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="52c10-322">If you use the platform version of NavigationView instead, the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="52c10-323">Wenn die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc`.</span><span class="sxs-lookup"><span data-stu-id="52c10-323">To use the platform version, remove all references to `muxc`.</span></span>

```csharp
// Add "using" for WinUI controls.
// using muxc = Microsoft.UI.Xaml.Controls;

private void ContentFrame_NavigationFailed(object sender, NavigationFailedEventArgs e)
{
    throw new Exception("Failed to load Page " + e.SourcePageType.FullName);
}

// List of ValueTuple holding the Navigation Tag and the relative Navigation Page 
private readonly List<(string Tag, Type Page)> _pages = new List<(string Tag, Type Page)>
{
    ("home", typeof(HomePage)),
    ("apps", typeof(AppsPage)),
    ("games", typeof(GamesPage)),
    ("music", typeof(MusicPage)),
};

private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // You can also add items in code.
    NavView.MenuItems.Add(new muxc.NavigationViewItemSeparator());
    NavView.MenuItems.Add(new muxc.NavigationViewItem
    {
        Content = "My content",
        Icon = new SymbolIcon((Symbol)0xF1AD),
        Tag = "content"
    });
    _pages.Add(("content", typeof(MyContentPage)));

    // Add handler for ContentFrame navigation.
    ContentFrame.Navigated += On_Navigated;

    // NavView doesn't load any page by default, so load home page.
    NavView.SelectedItem = NavView.MenuItems[0];
    // If navigation occurs on SelectionChanged, this isn't needed.
    // Because we use ItemInvoked to navigate, we need to call Navigate
    // here to load the home page.
    NavView_Navigate("home", new EntranceNavigationTransitionInfo());

    // Add keyboard accelerators for backwards navigation.
    var goBack = new KeyboardAccelerator { Key = VirtualKey.GoBack };
    goBack.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(goBack);

    // ALT routes here
    var altLeft = new KeyboardAccelerator
    {
        Key = VirtualKey.Left,
        Modifiers = VirtualKeyModifiers.Menu
    };
    altLeft.Invoked += BackInvoked;
    this.KeyboardAccelerators.Add(altLeft);
}

private void NavView_ItemInvoked(muxc.NavigationView sender,
                                 muxc.NavigationViewItemInvokedEventArgs args)
{
    if (args.IsSettingsInvoked == true)
    {
        NavView_Navigate("settings", args.RecommendedNavigationTransitionInfo);
    }
    else if (args.InvokedItemContainer != null)
    {
        var navItemTag = args.InvokedItemContainer.Tag.ToString();
        NavView_Navigate(navItemTag, args.RecommendedNavigationTransitionInfo);
    }
}

<!-- NavView_SelectionChanged is not used in this example, but is shown for completeness.
     You will typically handle either ItemInvoked or SelectionChanged to perform navigation,
     but not both. -->
private void NavView_SelectionChanged(muxc.NavigationView sender,
                                      muxc.NavigationViewSelectionChangedEventArgs args)
{
    if (args.IsSettingsSelected == true)
    {
        NavView_Navigate("settings", args.RecommendedNavigationTransitionInfo);
    }
    else if (args.SelectedItemContainer != null)
    {
        var navItemTag = args.SelectedItemContainer.Tag.ToString();
        NavView_Navigate(navItemTag, args.RecommendedNavigationTransitionInfo);
    }
}

private void NavView_Navigate(string navItemTag, NavigationTransitionInfo transitionInfo)
{
    Type _page = null;
    if (navItemTag == "settings")
    {
        _page = typeof(SettingsPage);
    }
    else
    {
        var item = _pages.FirstOrDefault(p => p.Tag.Equals(navItemTag));
        _page = item.Page;
    }
    // Get the page type before navigation so you can prevent duplicate
    // entries in the backstack.
    var preNavPageType = ContentFrame.CurrentSourcePageType;

    // Only navigate if the selected page isn't currently loaded.
    if (!(_page is null) && !Type.Equals(preNavPageType, _page))
    {
        ContentFrame.Navigate(_page, null, transitionInfo);
    }
}

private void NavView_BackRequested(muxc.NavigationView sender,
                                   muxc.NavigationViewBackRequestedEventArgs args)
{
    On_BackRequested();
}

private void BackInvoked(KeyboardAccelerator sender,
                         KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}

private bool On_BackRequested()
{
    if (!ContentFrame.CanGoBack)
        return false;

    // Don't go back if the nav pane is overlayed.
    if (NavView.IsPaneOpen &&
        (NavView.DisplayMode == muxc.NavigationViewDisplayMode.Compact ||
         NavView.DisplayMode == muxc.NavigationViewDisplayMode.Minimal))
        return false;

    ContentFrame.GoBack();
    return true;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        // SettingsItem is not part of NavView.MenuItems, and doesn't have a Tag.
        NavView.SelectedItem = (muxc.NavigationViewItem)NavView.SettingsItem;
        NavView.Header = "Settings";
    }
    else if (ContentFrame.SourcePageType != null)
    {
        var item = _pages.FirstOrDefault(p => p.Page == e.SourcePageType);

        NavView.SelectedItem = NavView.MenuItems
            .OfType<muxc.NavigationViewItem>()
            .First(n => n.Tag.Equals(item.Tag));

        NavView.Header =
            ((muxc.NavigationViewItem)NavView.SelectedItem)?.Content?.ToString();
    }
}
```

## <a name="related-topics"></a><span data-ttu-id="52c10-324">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="52c10-324">Related topics</span></span>

- [<span data-ttu-id="52c10-325">NavigationView-Klasse</span><span class="sxs-lookup"><span data-stu-id="52c10-325">NavigationView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [<span data-ttu-id="52c10-326">Master/Details</span><span class="sxs-lookup"><span data-stu-id="52c10-326">Master/details</span></span>](master-details.md)
- [<span data-ttu-id="52c10-327">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="52c10-327">Navigation basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="52c10-328">Übersicht über Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="52c10-328">Fluent Design for UWP overview</span></span>](../fluent-design-system/index.md)