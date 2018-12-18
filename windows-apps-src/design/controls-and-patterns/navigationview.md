---
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: c86ddee3558da23cd8bea5e0f16c6a8695babf84
ms.sourcegitcommit: 3433d0c7e70e00df0418887f71c2d094e9c30476
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "8973951"
---
# <a name="navigation-view"></a><span data-ttu-id="8225a-103">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="8225a-103">Navigation view</span></span>

<span data-ttu-id="8225a-104">Das NavigationView-Steuerelement enthält die Navigation auf oberster Ebene für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="8225a-104">The NavigationView control provides top-level navigation for your app.</span></span> <span data-ttu-id="8225a-105">Es mit einer Vielzahl von Bildschirmgrößen anpasst und _oberen_ und _linken_ Navigationsbereich Formate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8225a-105">It adapts to a variety of screen sizes and supports both _top_ and _left_ navigation styles.</span></span>

![oberen Navigationsleiste](images/nav-view-header.png)<br/>
_<span data-ttu-id="8225a-107">Navigationsansicht unterstützt und am oberen, linken Navigationsbereich oder im Menü</span><span class="sxs-lookup"><span data-stu-id="8225a-107">Navigation view supports both top and left navigation pane or menu</span></span>_

> <span data-ttu-id="8225a-108">**Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/windows.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="8225a-108">**Platform APIs**: [Windows.UI.Xaml.Controls.NavigationView class](/uwp/api/windows.ui.xaml.controls.navigationview)</span></span>
>
> <span data-ttu-id="8225a-109">**Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="8225a-109">**Windows UI Library APIs**: [Microsoft.UI.Xaml.Controls.NavigationView class](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span></span>
>
> <span data-ttu-id="8225a-110">Einige Features von NavigationView, z. B. _Top_ -Navigation erfordern Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="8225a-110">Some features of NavigationView, such as _top_ navigation, require Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="8225a-111">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="8225a-111">Is this the right control?</span></span>

<span data-ttu-id="8225a-112">NavigationView ist eine adaptive Navigationssteuerelement, das funktioniert gut für:</span><span class="sxs-lookup"><span data-stu-id="8225a-112">NavigationView is an adaptive navigation control that works well for:</span></span>

- <span data-ttu-id="8225a-113">Bereitstellen einer konsistenten navigationsumgebungen in der gesamten app.</span><span class="sxs-lookup"><span data-stu-id="8225a-113">Providing a consistent navigational experience throughout your app.</span></span>
- <span data-ttu-id="8225a-114">Sparen von Platz auf dem Bildschirm auf kleineren Fenstern.</span><span class="sxs-lookup"><span data-stu-id="8225a-114">Preserving screen real estate on smaller windows.</span></span>
- <span data-ttu-id="8225a-115">Organisieren von Zugriff auf viele Navigationskategorien.</span><span class="sxs-lookup"><span data-stu-id="8225a-115">Organizing access to many navigation categories.</span></span>

<span data-ttu-id="8225a-116">Andere navigationsmuster finden Sie unter [navigationsdesigngrundlagen](../basics/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8225a-116">For other navigation patterns, see [Navigation design basics](../basics/navigation-basics.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8225a-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8225a-117">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="8225a-118">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="8225a-118">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/XAML-controls-gallery-app-icon.png" alt="XAML controls gallery" width="168"></img></td>
<td>
    <p><span data-ttu-id="8225a-119">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/NavigationView">die App zu öffnen und NavigationView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="8225a-119">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/NavigationView">open the app and see the NavigationView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="8225a-120">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="8225a-120">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="8225a-121">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="8225a-121">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="display-modes"></a><span data-ttu-id="8225a-122">Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="8225a-122">Display modes</span></span>

> <span data-ttu-id="8225a-123">Die Eigenschaft PaneDisplayMode erfordert Windows 10, Version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) oder höher, oder in der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="8225a-123">The PaneDisplayMode property requires Windows 10, version 1809 ([SDK 17763](https://developer.microsoft.com/windows/downloads/windows-10-sdk)) or later, or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="8225a-124">Sie können die PaneDisplayMode-Eigenschaft verwenden, um verschiedene Navigation Stilen zu konfigurieren oder Anzeigemodi für die NavigationView.</span><span class="sxs-lookup"><span data-stu-id="8225a-124">You can use the PaneDisplayMode property to configure different navigation styles, or display modes, for the NavigationView.</span></span>

:::row:::
    :::column:::
    ### <a name="top"></a><span data-ttu-id="8225a-125">Oben</span><span class="sxs-lookup"><span data-stu-id="8225a-125">Top</span></span>
    <span data-ttu-id="8225a-126">Der Bereich wird oberhalb der Inhalt positioniert.</span><span class="sxs-lookup"><span data-stu-id="8225a-126">The pane is positioned above the content.</span></span></br>
    `PaneDisplayMode="Top"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die Navigation oben](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="8225a-128">Wir empfehlen _oberen_ Navigationsbereich wenn:</span><span class="sxs-lookup"><span data-stu-id="8225a-128">We recommend _top_ navigation when:</span></span>

- <span data-ttu-id="8225a-129">Sie haben 5 oder weniger Kategorien von Navigation auf oberster Ebene, die ebenso wichtig sind und alle zusätzlichen Navigation auf oberster Ebene, die Kategorien, die im Überlaufmenü Dropdownliste am Ende weniger wichtig eingestuft werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-129">You have 5 or fewer top-level navigation categories that are equally important, and any additional top-level navigation categories that end up in the dropdown overflow menu are considered less important.</span></span>
- <span data-ttu-id="8225a-130">Sie müssen alle Navigationsoptionen auf dem Bildschirm anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8225a-130">You need to show all navigation options on screen.</span></span>
- <span data-ttu-id="8225a-131">Sie möchten mehr Platz für app-Inhalt.</span><span class="sxs-lookup"><span data-stu-id="8225a-131">You want more space for your app content.</span></span>
- <span data-ttu-id="8225a-132">Symbole können nicht klar Navigationskategorien für Ihre app beschreiben.</span><span class="sxs-lookup"><span data-stu-id="8225a-132">Icons cannot clearly describe your app's navigation categories.</span></span>

:::row:::
    :::column:::
    ### <a name="left"></a><span data-ttu-id="8225a-133">Links</span><span class="sxs-lookup"><span data-stu-id="8225a-133">Left</span></span>
    <span data-ttu-id="8225a-134">Der Bereich erweitert und auf der linken Seite des Inhalts positioniert.</span><span class="sxs-lookup"><span data-stu-id="8225a-134">The pane is expanded and positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="Left"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für erweiterte linken Navigationsbereich](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="8225a-136">Wir empfehlen die _linke_ Navigation bei:</span><span class="sxs-lookup"><span data-stu-id="8225a-136">We recommend _left_ navigation when:</span></span>

- <span data-ttu-id="8225a-137">Sie haben Kategorien von 5 bis 10 wichtiger Navigation auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="8225a-137">You have 5-10 equally important top-level navigation categories.</span></span>
- <span data-ttu-id="8225a-138">Navigationskategorien mit weniger Speicherplatz für die anderen Inhalten der app sehr hervorgehoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="8225a-138">You want navigation categories to be very prominent, with less space for other app content.</span></span>

:::row:::
    :::column:::
    ### <a name="leftcompact"></a><span data-ttu-id="8225a-139">LeftCompact</span><span class="sxs-lookup"><span data-stu-id="8225a-139">LeftCompact</span></span>
    <span data-ttu-id="8225a-140">Im Bereich wird nur Symbole bis geöffnet, und auf der linken Seite des Inhalts positioniert wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-140">The pane shows only icons until opened and is positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="LeftCompact"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für compact linken Navigationsbereich](images/displaymode-leftcompact.png)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ### <a name="leftminimal"></a><span data-ttu-id="8225a-142">LeftMinimal</span><span class="sxs-lookup"><span data-stu-id="8225a-142">LeftMinimal</span></span>
    <span data-ttu-id="8225a-143">Nur die Schaltfläche wird angezeigt, bis das Fenster geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-143">Only the menu button is shown until the pane is opened.</span></span> <span data-ttu-id="8225a-144">Beim Öffnen, wird es auf der linken Seite des Inhalts positioniert.</span><span class="sxs-lookup"><span data-stu-id="8225a-144">When opened, it's positioned to the left of the content.</span></span></br>
    `PaneDisplayMode="LeftMinimal"`
    :::column-end:::
    :::column span="2":::
    ![Beispiel für die minimale linken Navigationsbereich](images/displaymode-leftminimal.png)
    :::column-end:::
:::row-end:::

### <a name="auto"></a><span data-ttu-id="8225a-146">Auto</span><span class="sxs-lookup"><span data-stu-id="8225a-146">Auto</span></span>

<span data-ttu-id="8225a-147">Standardmäßig ist PaneDisplayMode auf Auto festgelegt. Im Auto-Modus die Navigationsansicht anpasst zwischen LeftMinimal, wenn das Fenster schmaler, um LeftCompact ist, und dann von links im Fenster vergrößert wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-147">By default, PaneDisplayMode is set to Auto. In Auto mode, the navigation view adapts between LeftMinimal when the window is narrow, to LeftCompact, and then Left as the window gets wider.</span></span> <span data-ttu-id="8225a-148">Weitere Informationen finden Sie im Abschnitt [adaptives Verhalten](#adaptive-behavior) .</span><span class="sxs-lookup"><span data-stu-id="8225a-148">For more info, see the [adaptive behavior](#adaptive-behavior) section.</span></span>

![Linken Navigationsbereich standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_<span data-ttu-id="8225a-150">Navigation Ansicht standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="8225a-150">Navigation view default adaptive behavior</span></span>_

## <a name="anatomy"></a><span data-ttu-id="8225a-151">Aufbau</span><span class="sxs-lookup"><span data-stu-id="8225a-151">Anatomy</span></span>

<span data-ttu-id="8225a-152">Diese Bilder zeigen das Layout der Bereich, Header und Inhalt Bereiche des Steuerelements für die _am oberen_ oder _linken_ Navigationsbereich konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="8225a-152">These images show the layout of the pane, header, and content areas of the control when configured for _top_ or _left_ navigation.</span></span>

![Layout der oberen Navigationsleiste anzeigen](images/topnav-anatomy.png)<br/>
_<span data-ttu-id="8225a-154">Layout der oberen Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="8225a-154">Top navigation layout</span></span>_

![Layout des linken Navigationsbereich anzeigen](images/leftnav-anatomy.png)<br/>
_<span data-ttu-id="8225a-156">Linken Navigationsbereich layout</span><span class="sxs-lookup"><span data-stu-id="8225a-156">Left navigation layout</span></span>_

### <a name="pane"></a><span data-ttu-id="8225a-157">Bereich</span><span class="sxs-lookup"><span data-stu-id="8225a-157">Pane</span></span>

<span data-ttu-id="8225a-158">Die Eigenschaft PaneDisplayMode können Sie um den Bereich über dem Inhalt oder auf der linken Seite des Inhalts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-158">You can use the PaneDisplayMode property to position the pane above the content or to the left of the content.</span></span>

<span data-ttu-id="8225a-159">Der NavigationView-Bereich kann Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="8225a-159">The NavigationView pane can contain:</span></span>

- <span data-ttu-id="8225a-160">[NavigationViewItem](/uwp/api/windows.ui.xaml.controls.navigationviewitem) -Objekte.</span><span class="sxs-lookup"><span data-stu-id="8225a-160">[NavigationViewItem](/uwp/api/windows.ui.xaml.controls.navigationviewitem) objects.</span></span> <span data-ttu-id="8225a-161">Navigationselemente zu bestimmten Seiten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-161">Navigation items for navigating to specific pages.</span></span>
- <span data-ttu-id="8225a-162">[NavigationViewItemSeparator](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator) -Objekte.</span><span class="sxs-lookup"><span data-stu-id="8225a-162">[NavigationViewItemSeparator](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator) objects.</span></span> <span data-ttu-id="8225a-163">Trennzeichen Navigationselemente zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-163">Separators for grouping navigation items.</span></span> <span data-ttu-id="8225a-164">Legen Sie die [Opacity](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0, um das Trennzeichen als Leerzeichen gerendert.</span><span class="sxs-lookup"><span data-stu-id="8225a-164">Set the [Opacity](/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) property to 0 to render the separator as space.</span></span>
- <span data-ttu-id="8225a-165">[NavigationViewItemHeader](/uwp/api/windows.ui.xaml.controls.navigationviewitemheader) -Objekte.</span><span class="sxs-lookup"><span data-stu-id="8225a-165">[NavigationViewItemHeader](/uwp/api/windows.ui.xaml.controls.navigationviewitemheader) objects.</span></span> <span data-ttu-id="8225a-166">Header zum Beschriften von Gruppen von Elementen.</span><span class="sxs-lookup"><span data-stu-id="8225a-166">Headers for labeling groups of items.</span></span>
- <span data-ttu-id="8225a-167">Ein optionales [AutoSuggestBox](auto-suggest-box.md) -Steuerelement, das für die Suche auf app-Ebene zulassen.</span><span class="sxs-lookup"><span data-stu-id="8225a-167">An optional [AutoSuggestBox](auto-suggest-box.md) control to allow for app-level search.</span></span> <span data-ttu-id="8225a-168">Weisen Sie das Steuerelement, um die [NavigationView.AutoSuggestBox](/uwp/api/windows.ui.xaml.controls.navigationview.autosuggestbox) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8225a-168">Assign the control to the [NavigationView.AutoSuggestBox](/uwp/api/windows.ui.xaml.controls.navigationview.autosuggestbox) property.</span></span>
- <span data-ttu-id="8225a-169">Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md).</span><span class="sxs-lookup"><span data-stu-id="8225a-169">An optional entry point for [app settings](../app-settings/app-settings-and-data.md).</span></span> <span data-ttu-id="8225a-170">Um das Einstellungen-Element zu verbergen, wird festlegen Sie die [IsSettingsVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft auf **"false"**.</span><span class="sxs-lookup"><span data-stu-id="8225a-170">To hide the settings item, set the [IsSettingsVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) property to **false**.</span></span>

<span data-ttu-id="8225a-171">Es enthält auch Links:</span><span class="sxs-lookup"><span data-stu-id="8225a-171">The left pane also contains:</span></span>

- <span data-ttu-id="8225a-172">Eine Schaltfläche zum Umschalten des Bereichs geöffnet und geschlossen.</span><span class="sxs-lookup"><span data-stu-id="8225a-172">A menu button to toggle the pane opened and closed.</span></span> <span data-ttu-id="8225a-173">Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-173">On larger app windows when the pane is open, you may choose to hide this button using the [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) property.</span></span>

<span data-ttu-id="8225a-174">Die Navigationsansicht verfügt über eine zurück-Schaltfläche, die in der oberen linken Ecke des Bereichs befindet.</span><span class="sxs-lookup"><span data-stu-id="8225a-174">The navigation view has a back button that is placed in the top left-hand corner of the pane.</span></span> <span data-ttu-id="8225a-175">Es jedoch nicht automatisch behandeln rückwärts Navigation und Hinzufügen von Inhalten zu dem zurück-Stapel.</span><span class="sxs-lookup"><span data-stu-id="8225a-175">However, it does not automatically handle backwards navigation and add content to the back stack.</span></span> <span data-ttu-id="8225a-176">Zum Aktivieren der Rückwärtsnavigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="8225a-176">To enable backwards navigation, see the [backwards navigation](#backwards-navigation) section.</span></span>

<span data-ttu-id="8225a-177">Hier ist der Aufbau detaillierte Bereich für die Positionen oberen und linken Bereich.</span><span class="sxs-lookup"><span data-stu-id="8225a-177">Here is the detailed pane anatomy for the top and left pane positions.</span></span>

#### <a name="top-navigation-pane"></a><span data-ttu-id="8225a-178">Im oberen Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="8225a-178">Top navigation pane</span></span>

![Navigation Ansicht im oberen Bereich Anatomie](images/navview-pane-anatomy-horizontal.png)

1. <span data-ttu-id="8225a-180">Header</span><span class="sxs-lookup"><span data-stu-id="8225a-180">Headers</span></span>
1. <span data-ttu-id="8225a-181">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="8225a-181">Navigation items</span></span>
1. <span data-ttu-id="8225a-182">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="8225a-182">Separators</span></span>
1. <span data-ttu-id="8225a-183">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="8225a-183">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="8225a-184">Schaltfläche (optional)</span><span class="sxs-lookup"><span data-stu-id="8225a-184">Settings button (optional)</span></span>

#### <a name="left-navigation-pane"></a><span data-ttu-id="8225a-185">Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="8225a-185">Left navigation pane</span></span>

![Links Bereich Anatomie Navigationsansicht](images/navview-pane-anatomy-vertical.png)

1. <span data-ttu-id="8225a-187">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="8225a-187">Menu button</span></span>
1. <span data-ttu-id="8225a-188">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="8225a-188">Navigation items</span></span>
1. <span data-ttu-id="8225a-189">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="8225a-189">Separators</span></span>
1. <span data-ttu-id="8225a-190">Header</span><span class="sxs-lookup"><span data-stu-id="8225a-190">Headers</span></span>
1. <span data-ttu-id="8225a-191">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="8225a-191">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="8225a-192">Schaltfläche (optional)</span><span class="sxs-lookup"><span data-stu-id="8225a-192">Settings button (optional)</span></span>

#### <a name="pane-footer"></a><span data-ttu-id="8225a-193">Fußzeile</span><span class="sxs-lookup"><span data-stu-id="8225a-193">Pane footer</span></span>

<span data-ttu-id="8225a-194">Sie können freier Inhalt in der Fußzeile des platzieren, indem Sie die [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) Eigenschaft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8225a-194">You can place free-form content in the pane's footer by adding it to the [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) property.</span></span>

:::row:::
    :::column:::
    ![Bereich Fußzeile oben nav](images/navview-freeform-footer-top.png)<br>
     _<span data-ttu-id="8225a-196">Oberen Fußzeile</span><span class="sxs-lookup"><span data-stu-id="8225a-196">Top pane footer</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    _<span data-ttu-id="8225a-198">Linken Fußzeile</span><span class="sxs-lookup"><span data-stu-id="8225a-198">Left pane footer</span></span>_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-title-and-header"></a><span data-ttu-id="8225a-199">Bereich Titel und header</span><span class="sxs-lookup"><span data-stu-id="8225a-199">Pane title and header</span></span>

<span data-ttu-id="8225a-200">Sie können Textinhalt im Headerbereich platzieren, durch Festlegen der [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8225a-200">You can place text content in the pane header area by setting the [PaneTitle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneTitle) property.</span></span> <span data-ttu-id="8225a-201">Sie akzeptiert eine Zeichenfolge und zeigt den Text neben der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="8225a-201">It takes a string and shows the text next to the menu button.</span></span>

<span data-ttu-id="8225a-202">Zum Hinzufügen von nicht-Text-Inhalt, z. B. ein Bild oder ein Logo, können Sie jedes Element in den Bereich Header platzieren, durch die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8225a-202">To add non-text content, such as an image or logo, you can place any element in the pane's header by adding it to the [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) property.</span></span>

<span data-ttu-id="8225a-203">Wenn PaneTitle und PaneHeader festgelegt sind, wird der Inhalt horizontal neben der Schaltfläche, mit der die Menütaste am nächsten PaneTitle hat.</span><span class="sxs-lookup"><span data-stu-id="8225a-203">If both PaneTitle and PaneHeader are set, the content is stacked horizontally next to the menu button, with the PaneTitle closest to the menu button.</span></span>

:::row:::
    :::column:::
    ![Bereich Header oben nav](images/navview-freeform-header-top.png)<br>
     _<span data-ttu-id="8225a-205">Im oberen Bereich-header</span><span class="sxs-lookup"><span data-stu-id="8225a-205">Top pane header</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich Header linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    _<span data-ttu-id="8225a-207">Linken Bereich-header</span><span class="sxs-lookup"><span data-stu-id="8225a-207">Left pane header</span></span>_<br>
    :::column-end:::
:::row-end:::

#### <a name="pane-content"></a><span data-ttu-id="8225a-208">Inhalt</span><span class="sxs-lookup"><span data-stu-id="8225a-208">Pane content</span></span>

<span data-ttu-id="8225a-209">Die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzugefügt, um freier Inhalt im Bereich zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-209">You can place free-form content in the pane by adding it to the [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) property.</span></span>

:::row:::
    :::column:::
    ![Bereich benutzerdefinierte Inhalte oben nav](images/navview-freeform-pane-top.png)<br>
     _<span data-ttu-id="8225a-211">Benutzerdefinierte Inhalte oberen Bereich</span><span class="sxs-lookup"><span data-stu-id="8225a-211">Top pane custom content</span></span>_<br>
    :::column-end:::
    :::column:::
    ![Bereich benutzerdefinierte Inhalte linke Navigationsleiste](images/navview-freeform-pane-left.png)<br>
    _<span data-ttu-id="8225a-213">Benutzerdefinierte Inhalte linken Bereich</span><span class="sxs-lookup"><span data-stu-id="8225a-213">Left pane custom content</span></span>_<br>
    :::column-end:::
:::row-end:::

### <a name="header"></a><span data-ttu-id="8225a-214">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="8225a-214">Header</span></span>

<span data-ttu-id="8225a-215">Sie können einen Seitentitel hinzufügen, durch das Festlegen der [Header](/uwp/api/windows.ui.xaml.controls.navigationview.header) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="8225a-215">You can add a page title by setting the [Header](/uwp/api/windows.ui.xaml.controls.navigationview.header) property.</span></span>

![Beispiel für die Navigation Ansichtsbereich header](images/nav-header.png)<br/>
_<span data-ttu-id="8225a-217">Navigation Ansicht header</span><span class="sxs-lookup"><span data-stu-id="8225a-217">Navigation view header</span></span>_

<span data-ttu-id="8225a-218">Der in der linken Seite Position der Navigationsschaltfläche vertikal ausgerichtet ist, und unter den Bereich an der Position des oberen Bereich befindet.</span><span class="sxs-lookup"><span data-stu-id="8225a-218">The header area is vertically aligned with the navigation button in the left pane position, and lies below the pane in the top pane position.</span></span> <span data-ttu-id="8225a-219">Es verfügt über eine feste Höhe von 52 Pixel.</span><span class="sxs-lookup"><span data-stu-id="8225a-219">It has a fixed height of 52 px.</span></span> <span data-ttu-id="8225a-220">Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="8225a-220">Its purpose is to hold the page title of the selected nav category.</span></span> <span data-ttu-id="8225a-221">Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="8225a-221">The header is docked to the top of the page and acts as a scroll clipping point for the content area.</span></span>

<span data-ttu-id="8225a-222">Der Header ist sichtbar jedes Mal, wenn der NavigationView im minimierten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-222">The header is visible any time the NavigationView is in Minimal display mode.</span></span> <span data-ttu-id="8225a-223">Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-223">You may choose to hide the header in other modes, which are used on larger window widths.</span></span> <span data-ttu-id="8225a-224">Um die Kopfzeile auszublenden, wird festlegen Sie die [AlwaysShowHeader](/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) -Eigenschaft auf **"false"**.</span><span class="sxs-lookup"><span data-stu-id="8225a-224">To hide the header, set the [AlwaysShowHeader](/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) property to **false**.</span></span>

### <a name="content"></a><span data-ttu-id="8225a-225">Inhalt</span><span class="sxs-lookup"><span data-stu-id="8225a-225">Content</span></span>

![Beispiel für die Navigation Ansicht Inhaltsbereich](images/nav-content.png)<br/>
_<span data-ttu-id="8225a-227">Inhalt der Navigation</span><span class="sxs-lookup"><span data-stu-id="8225a-227">Navigation view content</span></span>_

<span data-ttu-id="8225a-228">Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8225a-228">The content area is where most of the information for the selected nav category is displayed.</span></span>

<span data-ttu-id="8225a-229">Wir empfehlen 12px Ränder für Ihren Inhaltsbereich, wenn sich NavigationView im **minimierten** Modus befindet 24 Sie andernfalls.</span><span class="sxs-lookup"><span data-stu-id="8225a-229">We recommend 12px margins for your content area when NavigationView is in **Minimal** mode and 24px margins otherwise.</span></span>

## <a name="adaptive-behavior"></a><span data-ttu-id="8225a-230">Adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="8225a-230">Adaptive behavior</span></span>

<span data-ttu-id="8225a-231">Standardmäßig wird die Navigationsansicht automatisch den Anzeigemodus basierend auf der Größe des Bildschirmbereichs, die verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8225a-231">By default, the navigation view automatically changes its display mode based on the amount of screen space available to it.</span></span> <span data-ttu-id="8225a-232">Die [CompactModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.compactmodethresholdwidth) und [ExpandedModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.expandedmodethresholdwidth) -Eigenschaften geben die Haltepunkte, an denen der Anzeigemodus ändert.</span><span class="sxs-lookup"><span data-stu-id="8225a-232">The [CompactModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.compactmodethresholdwidth) and [ExpandedModeThresholdWidth](/uwp/api/windows.ui.xaml.controls.navigationview.expandedmodethresholdwidth) properties specify the breakpoints at which the display mode changes.</span></span> <span data-ttu-id="8225a-233">Sie können diese Werte, um das adaptive anzeigemodusverhalten anzupassen, ändern.</span><span class="sxs-lookup"><span data-stu-id="8225a-233">You can modify these values to customize the adaptive display mode behavior.</span></span>

### <a name="default"></a><span data-ttu-id="8225a-234">Standard</span><span class="sxs-lookup"><span data-stu-id="8225a-234">Default</span></span>

<span data-ttu-id="8225a-235">Wenn PaneDisplayMode auf den Standardwert **Auto**festgelegt ist, ist das adaptive Verhalten angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8225a-235">When PaneDisplayMode is set to its default value of **Auto**, the adaptive behavior is to show:</span></span>

- <span data-ttu-id="8225a-236">Eine erweiterte linken Bereich auf großen fensterbreiten (1008 Pixel oder größer).</span><span class="sxs-lookup"><span data-stu-id="8225a-236">An expanded left pane on large window widths (1008px or greater).</span></span>
- <span data-ttu-id="8225a-237">Links, nur Symbol, ein Navigationsbereich (LeftCompact) bei mittelgroßen fensterbreiten (641 Pixel bis 1007 Pixel).</span><span class="sxs-lookup"><span data-stu-id="8225a-237">A left, icon-only, nav pane (LeftCompact) on medium window widths (641px to 1007px).</span></span>
- <span data-ttu-id="8225a-238">Nur eine Schaltfläche (LeftMinimal) für kleine fensterbreiten (640 Pixel oder weniger).</span><span class="sxs-lookup"><span data-stu-id="8225a-238">Only a menu button (LeftMinimal) on small window widths (640px or less).</span></span>

<span data-ttu-id="8225a-239">Weitere Informationen zu Fenstergrößen für adaptives Verhalten finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="8225a-239">For more information about window sizes for adaptive behavior, see [Screen sizes and breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

![Linken Navigationsbereich standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)<br/>
_<span data-ttu-id="8225a-241">Navigation Ansicht standardmäßigen adaptiven Verhaltens</span><span class="sxs-lookup"><span data-stu-id="8225a-241">Navigation view default adaptive behavior</span></span>_

### <a name="minimal"></a><span data-ttu-id="8225a-242">Minimiert</span><span class="sxs-lookup"><span data-stu-id="8225a-242">Minimal</span></span>

<span data-ttu-id="8225a-243">Ein zweites Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und nur eine Schaltfläche auf beiden kleinen und mittelgroßen fensterbreiten verwenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-243">A second common adaptive pattern is to use an expanded left pane on large window widths, and only a menu button on both medium and small window widths.</span></span>

<span data-ttu-id="8225a-244">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="8225a-244">We recommend this when:</span></span>

- <span data-ttu-id="8225a-245">Sie möchten mehr Platz für app-Inhalte auf kleinere fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="8225a-245">You want more space for app content on smaller window widths.</span></span>
- <span data-ttu-id="8225a-246">Die Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8225a-246">Your navigation categories cannot be clearly represented with icons.</span></span>

![Minimale adaptives Verhalten linken Navigationsbereich](images/adaptive-behavior-minimal.png)<br/>
_<span data-ttu-id="8225a-248">Ansicht "minimal" adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="8225a-248">Navigation view "minimal" adaptive behavior</span></span>_

<span data-ttu-id="8225a-249">Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf die Breite, die den Bereich zu reduzieren soll.</span><span class="sxs-lookup"><span data-stu-id="8225a-249">To configure this behavior, set CompactModeThresholdWidth to the width at which you want the pane to collapse.</span></span> <span data-ttu-id="8225a-250">Hier ist der Standardwert der 640, 1007 geändert.</span><span class="sxs-lookup"><span data-stu-id="8225a-250">Here, it's changed from the default of 640 to 1007.</span></span> <span data-ttu-id="8225a-251">Sie sollten auch ExpandedModeThresholdWidth, um sicherzustellen, dass die Werte nicht zu Konflikten festlegen.</span><span class="sxs-lookup"><span data-stu-id="8225a-251">You should also set ExpandedModeThresholdWidth to ensure the values don't conflict.</span></span>

```xaml
<NavigationView CompactModeThresholdWidth="1007" ExpandedModeThresholdWidth="1007"/>
```

### <a name="compact"></a><span data-ttu-id="8225a-252">Kompakt</span><span class="sxs-lookup"><span data-stu-id="8225a-252">Compact</span></span>

<span data-ttu-id="8225a-253">Ein drittes Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und eine LeftCompact, nur Symbol, Navigationsbereich auf beiden kleinen und mittelgroßen fensterbreiten verwenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-253">A third common adaptive pattern is to use an expanded left pane on large window widths, and a LeftCompact, icon-only, nav pane on both medium and small window widths.</span></span>

<span data-ttu-id="8225a-254">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="8225a-254">We recommend this when:</span></span>

- <span data-ttu-id="8225a-255">Es ist wichtig, immer alle Navigationsoptionen auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-255">It is important to always show all navigation options on screen.</span></span>
- <span data-ttu-id="8225a-256">Die Navigationskategorien können deutlich mit Symbolen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-256">Your navigation categories can be clearly represented with icons.</span></span>

![Linken Navigationsbereich compact adaptives Verhalten](images/adaptive-behavior-compact.png)<br/>
_<span data-ttu-id="8225a-258">Navigation Ansicht "compact" adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="8225a-258">Navigation view "compact" adaptive behavior</span></span>_

<span data-ttu-id="8225a-259">Um dieses Verhalten zu konfigurieren, legen Sie CompactModeThresholdWidth auf 0 fest.</span><span class="sxs-lookup"><span data-stu-id="8225a-259">To configure this behavior, set CompactModeThresholdWidth to 0.</span></span>

```xaml
<NavigationView CompactModeThresholdWidth="0"/>
```

### <a name="no-adaptive-behavior"></a><span data-ttu-id="8225a-260">Keine adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="8225a-260">No adaptive behavior</span></span>

<span data-ttu-id="8225a-261">Um die automatische adaptives Verhalten zu deaktivieren, legen Sie PaneDisplayMode nicht automatisch auf den Wert. Hier wird festgelegt LeftMinimal, sodass nur die Menütaste unabhängig von der Breite des Fensters angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-261">To disable the automatic adaptive behavior, set PaneDisplayMode to a value other than Auto. Here, it's set to LeftMinimal, so only the menu button is shown regardless of the window width.</span></span>

![Linke Navigationsleiste keine adaptives Verhalten](images/adaptive-behavior-none.png)<br/>
_<span data-ttu-id="8225a-263">Navigationsansicht mit PaneDisplayMode als LeftMinimal</span><span class="sxs-lookup"><span data-stu-id="8225a-263">Navigation view with PaneDisplayMode set to LeftMinimal</span></span>_

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

<span data-ttu-id="8225a-264">Wie zuvor im Abschnitt _Anzeigemodi_ beschrieben wird, können Sie den Bereich immer am oberen, immer erweiterten, immer compact oder immer minimale werden festlegen.</span><span class="sxs-lookup"><span data-stu-id="8225a-264">As described previously in the _Display modes_ section, you can set the pane to be always on top, always expanded, always compact, or always minimal.</span></span> <span data-ttu-id="8225a-265">Sie können auch die Anzeigemodi selbst im app-Code verwalten.</span><span class="sxs-lookup"><span data-stu-id="8225a-265">You can also manage the display modes yourself in your app code.</span></span> <span data-ttu-id="8225a-266">Ein Beispiel hierfür wird im nächsten Abschnitt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8225a-266">An example of this is shown in the next section.</span></span>

### <a name="top-to-left-navigation"></a><span data-ttu-id="8225a-267">Oben links</span><span class="sxs-lookup"><span data-stu-id="8225a-267">Top to left navigation</span></span>

<span data-ttu-id="8225a-268">Bei der Verwendung der oberen Navigationsleiste in Ihrer app reduzieren Navigationselemente in ein Überlaufmenü der Fenster Breite verringert.</span><span class="sxs-lookup"><span data-stu-id="8225a-268">When you use top navigation in your app, navigation items collapse into an overflow menu as the window width decreases.</span></span> <span data-ttu-id="8225a-269">Wenn Ihre app-Fenster schmaler ist, können sie ein besseres Benutzererlebnis, um die PaneDisplayMode von oben LeftMinimal Navigation, sondern können alles, was die Elemente in das Überlaufmenü reduzieren wechseln bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8225a-269">When your app window is narrow, it can provide a better user experience to switch the PaneDisplayMode from Top to LeftMinimal navigation, rather than letting all the items collapse into the overflow menu.</span></span>

<span data-ttu-id="8225a-270">Wir empfehlen die Verwendung der oberen Navigationsleiste auf großen Fenstergrößen und linken Navigationsbereich auf kleinen Fenster Größe bei:</span><span class="sxs-lookup"><span data-stu-id="8225a-270">We recommend using top navigation on large window sizes and left navigation on small window sizes when:</span></span>

- <span data-ttu-id="8225a-271">Sie haben eine Reihe von gleichmäßig wichtige Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in diesen auf dem Bildschirm passt, Sie die linke Navigation, damit sie genauso wichtig wie erhalten reduzieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-271">You have a set of equally important top-level navigation categories to be displayed together, such that if one category in this set doesn't fit on screen, you collapse to left navigation to give them equal importance.</span></span>
- <span data-ttu-id="8225a-272">Möchten Sie so viel Inhalt Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten.</span><span class="sxs-lookup"><span data-stu-id="8225a-272">You wish to preserve as much content space as possible in small window sizes.</span></span>

<span data-ttu-id="8225a-273">Dieses Beispiel zeigt, wie Sie eine [VisualStateManager](/uwp/api/Windows.UI.Xaml.VisualStateManager) und [AdaptiveTrigger.MinWindowWidth](/uwp/api/windows.ui.xaml.adaptivetrigger.minwindowwidth) -Eigenschaft verwenden, um zwischen den oberen und LeftMinimal Navigation zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="8225a-273">This example shows how to use a [VisualStateManager](/uwp/api/Windows.UI.Xaml.VisualStateManager) and [AdaptiveTrigger.MinWindowWidth](/uwp/api/windows.ui.xaml.adaptivetrigger.minwindowwidth) property to switch between Top and LeftMinimal navigation.</span></span>

![Beispiel für den oberen oder linken adaptives Verhalten 1](images/navigation-top-to-left.png)

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
> <span data-ttu-id="8225a-275">Wenn Sie AdaptiveTrigger.MinWindowWidth verwenden, wird der visuelle Zustand ausgelöst, wenn das Fenster breiter als die angegebene minimale Breite ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-275">When you use AdaptiveTrigger.MinWindowWidth, the visual state is triggered when the window is wider than the specified minimum width.</span></span> <span data-ttu-id="8225a-276">Dies bedeutet, dass die standardmäßigen XAML-Code definiert das schmale Fenster, und die VisualState definiert die Änderungen, die angewendet werden, wenn das Fenster vergrößert wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-276">This means the default XAML defines the narrow window, and the VisualState defines the modifications that are applied when the window gets wider.</span></span> <span data-ttu-id="8225a-277">Der Standardwert PaneDisplayMode Navigationsansicht automatisch ist, sodass, wenn die Fensterbreite kleiner oder gleich CompactModeThresholdWidth ist, LeftMinimal Navigation verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-277">The default PaneDisplayMode for the navigation view is Auto, so when the window width is less than or equal to CompactModeThresholdWidth, LeftMinimal navigation is used.</span></span> <span data-ttu-id="8225a-278">Wenn das Fenster vergrößert wird, die VisualState überschreibt die und oberen Navigationsleiste wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="8225a-278">When the window gets wider, the VisualState overrides the default, and Top navigation is used.</span></span>

## <a name="navigation"></a><span data-ttu-id="8225a-279">Navigation</span><span class="sxs-lookup"><span data-stu-id="8225a-279">Navigation</span></span>

<span data-ttu-id="8225a-280">Die Navigationsansicht ausführen keine Navigationsaufgaben automatisch.</span><span class="sxs-lookup"><span data-stu-id="8225a-280">The navigation view doesn't perform any navigation tasks automatically.</span></span> <span data-ttu-id="8225a-281">Wenn der Benutzer auf ein Navigationselement tippen, wird die Navigationsansicht zeigt dieses Element als ausgewählt und löst ein [ItemInvoked](/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) -Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8225a-281">When the user taps on a navigation item, the navigation view shows that item as selected and raises an [ItemInvoked](/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) event.</span></span> <span data-ttu-id="8225a-282">Wenn das Tippen ein neues Element ausgewählt wird, wird ein [SelectionChanged](/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) -Ereignis auch ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="8225a-282">If the tap results in a new item being selected, a [SelectionChanged](/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) event is also raised.</span></span>

<span data-ttu-id="8225a-283">Sie können entweder-Ereignis, um Aufgaben im Zusammenhang mit der gewünschten Navigation behandeln.</span><span class="sxs-lookup"><span data-stu-id="8225a-283">You can handle either event to perform tasks related to the requested navigation.</span></span> <span data-ttu-id="8225a-284">Sie behandeln soll, hängt das Verhalten, die, das Sie für Ihre app verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8225a-284">Which one you should handle depends on the behavior you want for your app.</span></span> <span data-ttu-id="8225a-285">In der Regel für die angeforderte Seite navigieren und die Navigation Ansicht Header in Reaktion auf diese Ereignisse aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-285">Typically, you navigate to the requested page and update the navigation view header in response to these events.</span></span>

<span data-ttu-id="8225a-286">**ItemInvoked** wird jedes Mal, die der Benutzer auf ein Navigationselement tippt ausgelöst, auch wenn es bereits aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-286">**ItemInvoked** is raised any time the user taps a navigation item, even if it's already selected.</span></span> <span data-ttu-id="8225a-287">(Das Element kann auch mit einer entsprechenden Aktion, die mit der Maus, Tastatur oder andere Eingabetypen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-287">(The item can also be invoked with an equivalent action using mouse, keyboard, or other input.</span></span> <span data-ttu-id="8225a-288">Weitere Informationen finden Sie unter [Eingabe und Interaktionen](../input/index.md).) Wenn Sie in der ItemInvoked-Ereignishandler navigieren, wird standardmäßig die Seite geladen werden, und dieser Eintrag ist Navigationsstapel hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8225a-288">For more info, see [Input and interactions](../input/index.md).) If you navigate in the ItemInvoked handler, by default, the page will be reloaded, and a duplicate entry is added to the navigation stack.</span></span> <span data-ttu-id="8225a-289">Wenn Sie navigieren, wenn ein Element aufgerufen wird, sollten Sie verbieten Neuladen der Seite, oder stellen Sie sicher, dass dieser Eintrag nicht in der navigationsbackstack erstellt wird, wenn die Seite geladen wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-289">If you navigate when an item is invoked, you should disallow reloading the page, or ensure that a duplicate entry is not created in the navigation backstack when the page is reloaded.</span></span> <span data-ttu-id="8225a-290">(Siehe Codebeispiel).</span><span class="sxs-lookup"><span data-stu-id="8225a-290">(See code examples.)</span></span>

<span data-ttu-id="8225a-291">**SelectionChanged** kann von einem Benutzer Aufrufen eines Elements, das derzeit ausgewählte ist oder ändern das ausgewählte Element programmgesteuert ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-291">**SelectionChanged** can be raised by a user invoking an item that isn't currently selected, or by programmatically changing the selected item.</span></span> <span data-ttu-id="8225a-292">Wenn die Änderung der Auswahl tritt auf, da ein Benutzer ein Element aufgerufen wird, tritt ein, zuerst das ItemInvoked-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8225a-292">If the selection change occurs because a user invoked an item, the ItemInvoked event occurs first.</span></span> <span data-ttu-id="8225a-293">Wenn die Änderung der Auswahl programmgesteuerten ist, wird die ItemInvoked nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="8225a-293">If the selection change is programmatic, ItemInvoked is not raised.</span></span>

### <a name="backwards-navigation"></a><span data-ttu-id="8225a-294">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="8225a-294">Backwards navigation</span></span>

<span data-ttu-id="8225a-295">NavigationView verfügt über eine integrierte Schaltfläche "zurück". wie bei der Navigation vor, sie jedoch nicht ausführen, rückwärts Navigation automatisch.</span><span class="sxs-lookup"><span data-stu-id="8225a-295">NavigationView has a built-in back button; but, as with forward navigation, it doesn't perform backwards navigation automatically.</span></span> <span data-ttu-id="8225a-296">Wenn der Benutzer die zurück-Schaltfläche tippt, wird das [BackRequested](/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) -Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="8225a-296">When the user taps the back button, the [BackRequested](/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) event is raised.</span></span> <span data-ttu-id="8225a-297">Sie behandeln dieses Ereignis, um rückwärts Navigation durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="8225a-297">You handle this event to perform backwards navigation.</span></span> <span data-ttu-id="8225a-298">Weitere Informationen und Codebeispiele finden Sie unter [Navigationsverlauf und Rückwärtsnavigation Navigation](../basics/navigation-history-and-backwards-navigation.md).</span><span class="sxs-lookup"><span data-stu-id="8225a-298">For more info and code examples, see [Navigation history and backwards navigation](../basics/navigation-history-and-backwards-navigation.md).</span></span>

<span data-ttu-id="8225a-299">Im minimalen oder kompakten Modus ist als Flyout geöffnet die Navigationsansicht Bereich.</span><span class="sxs-lookup"><span data-stu-id="8225a-299">In Minimal or Compact mode, the navigation view Pane is open as a flyout.</span></span> <span data-ttu-id="8225a-300">In diesem Fall, wird Klicken Sie auf die zurück-Schaltfläche Schließen des Bereichs und stattdessen das **PaneClosing** -Ereignis auslösen.</span><span class="sxs-lookup"><span data-stu-id="8225a-300">In this case, clicking the back button will close the Pane and raise the **PaneClosing** event instead.</span></span>

<span data-ttu-id="8225a-301">Sie können ausblenden oder deaktivieren die zurück-Schaltfläche durch Festlegen dieser Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8225a-301">You can hide or disable the back button by setting these properties:</span></span>

- <span data-ttu-id="8225a-302">[IsBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible): Verwenden Sie zum ein- und Ausblenden der Schaltfläche "zurück".</span><span class="sxs-lookup"><span data-stu-id="8225a-302">[IsBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible): use to show and hide the back button.</span></span> <span data-ttu-id="8225a-303">Diese Eigenschaft akzeptiert einen Wert von der [NavigationViewBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationviewbackbuttonvisible) -Enumeration und standardmäßig auf **Auto** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-303">This property takes a value of the [NavigationViewBackButtonVisible](/uwp/api/windows.ui.xaml.controls.navigationviewbackbuttonvisible) enumeration, and is set to **Auto** by default.</span></span> <span data-ttu-id="8225a-304">Wenn die Schaltfläche reduziert wird, ist es auch keinen Platz im Layout für sie reserviert.</span><span class="sxs-lookup"><span data-stu-id="8225a-304">When the button is collapsed, no space is reserved for it in the layout.</span></span>
- <span data-ttu-id="8225a-305">[IsBackEnabled](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled): Verwenden Sie zum Aktivieren oder deaktivieren die zurück-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="8225a-305">[IsBackEnabled](/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled): use to enable or disable the back button.</span></span> <span data-ttu-id="8225a-306">Diese Eigenschaft der Eigenschaft [CanGoBack](/uwp/api/windows.ui.xaml.controls.frame.cangoback) Navigations-Frame können Sie Daten gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-306">You can data bind this property to the [CanGoBack](/uwp/api/windows.ui.xaml.controls.frame.cangoback) property of your navigation frame.</span></span> <span data-ttu-id="8225a-307">**BackRequested** wird nicht ausgelöst, wenn **IsBackEnabled** auf **"false"** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-307">**BackRequested** is not raised if **IsBackEnabled** is **false**.</span></span>

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

## <a name="code-example"></a><span data-ttu-id="8225a-308">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8225a-308">Code example</span></span>

<span data-ttu-id="8225a-309">Dieses Beispiel zeigt, wie Sie NavigationView mit einem oberen Navigationsbereich auf großen Fenstergrößen und einem linken Navigationsbereich auf kleinen Fenstergrößen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="8225a-309">This example shows how you can use NavigationView with both a top navigation pane on large window sizes and a left navigation pane on small window sizes.</span></span> <span data-ttu-id="8225a-310">Sie können auf die linke Navigation durch das Entfernen der _oberen_ Navigationsbereich Einstellungen in der VisualStateManager angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="8225a-310">It can be adapted to left-only navigation by removing the _top_ navigation settings in the VisualStateManager.</span></span>

<span data-ttu-id="8225a-311">Das Beispiel zeigt eine empfohlene Vorgehensweise zur Navigation richten, das für viele häufige Szenarien geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="8225a-311">The example demonstrates a recommended way to set up navigation data that will work for many common scenarios.</span></span> <span data-ttu-id="8225a-312">Es wird veranschaulicht, wie die Rückwärtsnavigation mit der zurück-Schaltfläche und Tastatur-Navigation NavigationView implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-312">It also demonstrates how to implement backwards navigation with NavigationView's back button and keyboard navigation.</span></span>

<span data-ttu-id="8225a-313">Dieser Code wird davon ausgegangen, dass die app Seiten mit den folgenden Namen zu navigieren enthält: _HomePage_, _AppsPage_, _GamesPage_, _MusicPage_, _MyContentPage_und _SettingsPage_.</span><span class="sxs-lookup"><span data-stu-id="8225a-313">This code assumes that your app contains pages with the following names to navigate to: _HomePage_, _AppsPage_, _GamesPage_, _MusicPage_, _MyContentPage_, and _SettingsPage_.</span></span> <span data-ttu-id="8225a-314">Code für diese Seiten wird nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8225a-314">Code for these pages is not shown.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8225a-315">Informationen zu app Seiten wird in einem [ValueTuple](https://docs.microsoft.com/dotnet/api/system.valuetuple)gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8225a-315">Information about the app's pages is stored in a [ValueTuple](https://docs.microsoft.com/dotnet/api/system.valuetuple).</span></span> <span data-ttu-id="8225a-316">Diese Struktur erfordert, dass die Mindestversion für Ihre app-Projekt SDK 17763 oder größer sein muss.</span><span class="sxs-lookup"><span data-stu-id="8225a-316">This struct requires that the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="8225a-317">Wenn Sie die WinUI-Version von NavigationView für frühere Versionen von Windows 10 verwenden, können Sie stattdessen das [System.ValueTuple NuGet-Paket](https://www.nuget.org/packages/System.ValueTuple/) .</span><span class="sxs-lookup"><span data-stu-id="8225a-317">If you use the WinUI version of NavigationView to target earlier versions of Windows 10, you can use the [System.ValueTuple NuGet package](https://www.nuget.org/packages/System.ValueTuple/) instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8225a-318">Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-318">This code shows how to use the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/) version of NavigationView.</span></span> <span data-ttu-id="8225a-319">Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="8225a-319">If you use the platform version of NavigationView instead, the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="8225a-320">Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc:`.</span><span class="sxs-lookup"><span data-stu-id="8225a-320">To use the platform version, remove all references to `muxc:`.</span></span>

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
> <span data-ttu-id="8225a-321">Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version von NavigationView verwenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-321">This code shows how to use the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/) version of NavigationView.</span></span> <span data-ttu-id="8225a-322">Wenn Sie stattdessen die Plattformversion von NavigationView verwenden, muss die Mindestversion für Ihre app-Projekt SDK 17763 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="8225a-322">If you use the platform version of NavigationView instead, the minimum version for your app project must be SDK 17763 or greater.</span></span> <span data-ttu-id="8225a-323">Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxc`.</span><span class="sxs-lookup"><span data-stu-id="8225a-323">To use the platform version, remove all references to `muxc`.</span></span>

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

<span data-ttu-id="8225a-324">Im folgenden wird ein [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/index) Version des Handlers **NavView_ItemInvoked** aus dem C#-Codebeispiel oben.</span><span class="sxs-lookup"><span data-stu-id="8225a-324">Below is a [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index) version of the **NavView_ItemInvoked** handler from the C# code example above.</span></span> <span data-ttu-id="8225a-325">Die Technik in C++ / WinRT-Handler müssen Sie zunächst speichern (in der [**NavigationViewItem**](/uwp/api/windows.ui.xaml.controls.navigationviewitem)-Tag) der vollständige Name der Seite, die Sie wechseln möchten.</span><span class="sxs-lookup"><span data-stu-id="8225a-325">The technique in the C++/WinRT handler involves you first storing (in the tag of the [**NavigationViewItem**](/uwp/api/windows.ui.xaml.controls.navigationviewitem)) the full type name of the page to which you want to navigate.</span></span> <span data-ttu-id="8225a-326">Im Ereignishandler Unboxing diesen Wert, schalten Sie es in ein Objekt [**Windows::UI::Xaml::Interop::TypeName**](/uwp/api/windows.ui.xaml.interop.typename) und verwenden diese, um zur Seite "Ziel" zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="8225a-326">In the handler, you unbox that value, turn it into a [**Windows::UI::Xaml::Interop::TypeName**](/uwp/api/windows.ui.xaml.interop.typename) object, and use that to navigate to the destination page.</span></span> <span data-ttu-id="8225a-327">Es ist nicht erforderlich für die Zuordnung-Variable, die mit dem Namen `_pages` , die Sie in der C#-Beispiel; finden Sie unter und zu bestätigen, dass die Werte in die Tags eines gültigen Typs sind Komponententests erstellen können.</span><span class="sxs-lookup"><span data-stu-id="8225a-327">There's no need for the mapping variable named `_pages` that you see in the C# example; and you'll be able to create unit tests confirming that the values inside your tags are of a valid type.</span></span> <span data-ttu-id="8225a-328">Weitere Informationen finden Sie [Boxing und unboxing von Einzelwerten für IInspectable mit C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/boxing).</span><span class="sxs-lookup"><span data-stu-id="8225a-328">Also see [Boxing and unboxing scalar values to IInspectable with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/boxing).</span></span>

```cppwinrt
void MainPage::NavView_ItemInvoked(Windows::Foundation::IInspectable const & /* sender */, Windows::UI::Xaml::Controls::NavigationViewItemInvokedEventArgs const & args)
{
    if (args.IsSettingsInvoked())
    {
        // Navigate to Settings.
    }
    else if (args.InvokedItemContainer())
    {
        Windows::UI::Xaml::Interop::TypeName pageTypeName;
        pageTypeName.Name = unbox_value<hstring>(args.InvokedItemContainer().Tag());
        pageTypeName.Kind = Windows::UI::Xaml::Interop::TypeKind::Primitive;
        ContentFrame().Navigate(pageTypeName, nullptr);
    }
}
```

## <a name="navigation-view-customization"></a><span data-ttu-id="8225a-329">Anpassung der Navigation Ansicht</span><span class="sxs-lookup"><span data-stu-id="8225a-329">Navigation view customization</span></span>

### <a name="pane-backgrounds"></a><span data-ttu-id="8225a-330">Bereichshintergründe</span><span class="sxs-lookup"><span data-stu-id="8225a-330">Pane Backgrounds</span></span>

<span data-ttu-id="8225a-331">Standardmäßig verwendet der NavigationView-Bereich einen anderen Hintergrund abhängig vom Anzeigemodus:</span><span class="sxs-lookup"><span data-stu-id="8225a-331">By default, the NavigationView pane uses a different background depending on the display mode:</span></span>

- <span data-ttu-id="8225a-332">der Bereich ist eine graue Volltonfarbe wird auf der linken Seite, Side-by-Side mit dem Inhalt (im linken Modus) erweitert.</span><span class="sxs-lookup"><span data-stu-id="8225a-332">the pane is a solid grey color when expanded on the left, side-by-side with the content (in Left mode).</span></span>
- <span data-ttu-id="8225a-333">im Bereich wird in-app-Acryl geöffneten als Overlay Inhalt (im oberen, minimalen oder kompakten Modus).</span><span class="sxs-lookup"><span data-stu-id="8225a-333">the pane uses in-app acrylic when open as an overlay on top of content (in Top, Minimal, or Compact mode).</span></span>

<span data-ttu-id="8225a-334">Um den Hintergrund des Bereichs zu ändern, können Sie die XAML-Designressourcen verwendet, um den Hintergrund in jedem Modus Rendern überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8225a-334">To modify the pane background, you can override the XAML theme resources used to render the background in each mode.</span></span> <span data-ttu-id="8225a-335">(Diese Technik ist anstatt eine einzelne PaneBackground Eigenschaft verwendet um die verschiedene Hintergründen für unterschiedliche Anzeigemodi zu unterstützen.)</span><span class="sxs-lookup"><span data-stu-id="8225a-335">(This technique is used rather than a single PaneBackground property in order to support different backgrounds for different display modes.)</span></span>

<span data-ttu-id="8225a-336">Diese Tabelle zeigt die Designressource in jedem Anzeigemodus verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-336">This table shows which theme resource is used in each display mode.</span></span>

| <span data-ttu-id="8225a-337">Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="8225a-337">Display mode</span></span> | <span data-ttu-id="8225a-338">Designressource</span><span class="sxs-lookup"><span data-stu-id="8225a-338">Theme resource</span></span> |
| ------------ | -------------- |
| <span data-ttu-id="8225a-339">Links</span><span class="sxs-lookup"><span data-stu-id="8225a-339">Left</span></span> | <span data-ttu-id="8225a-340">NavigationViewExpandedPaneBackground</span><span class="sxs-lookup"><span data-stu-id="8225a-340">NavigationViewExpandedPaneBackground</span></span> |
| <span data-ttu-id="8225a-341">LeftCompact</span><span class="sxs-lookup"><span data-stu-id="8225a-341">LeftCompact</span></span><br/><span data-ttu-id="8225a-342">LeftMinimal</span><span class="sxs-lookup"><span data-stu-id="8225a-342">LeftMinimal</span></span> | <span data-ttu-id="8225a-343">NavigationViewDefaultPaneBackground</span><span class="sxs-lookup"><span data-stu-id="8225a-343">NavigationViewDefaultPaneBackground</span></span> |
| <span data-ttu-id="8225a-344">Oben</span><span class="sxs-lookup"><span data-stu-id="8225a-344">Top</span></span> | <span data-ttu-id="8225a-345">NavigationViewTopPaneBackground</span><span class="sxs-lookup"><span data-stu-id="8225a-345">NavigationViewTopPaneBackground</span></span> |

<span data-ttu-id="8225a-346">Dieses Beispiel zeigt, wie die Designressourcen in "App.xaml" außer Kraft gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="8225a-346">This example shows how to override the theme resources in App.xaml.</span></span> <span data-ttu-id="8225a-347">Wenn Sie Designressourcen überschreiben, sollten Sie immer "Default" und "HighContrast" Ressourcenwörterbücher mindestens und Wörterbücher für "Light" oder "Dark" Ressourcen bereitstellen nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="8225a-347">When you override theme resources, you should always provide "Default" and "HighContrast" resource dictionaries at a minimum, and dictionaries for "Light" or "Dark" resources as needed.</span></span> <span data-ttu-id="8225a-348">Weitere Informationen finden Sie unter [ResourceDictionary.ThemeDictionaries](/uwp/api/windows.ui.xaml.resourcedictionary.themedictionaries).</span><span class="sxs-lookup"><span data-stu-id="8225a-348">For more info, see [ResourceDictionary.ThemeDictionaries](/uwp/api/windows.ui.xaml.resourcedictionary.themedictionaries).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8225a-349">Dieser Code zeigt, wie Sie die [UI-Bibliothek für Windows](https://docs.microsoft.com/uwp/toolkits/winui/) -Version des AcrylicBrush zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8225a-349">This code shows how to use the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/) version of AcrylicBrush.</span></span> <span data-ttu-id="8225a-350">Wenn Sie stattdessen die Plattformversion des AcrylicBrush verwenden, muss die Mindestversion für Ihre app-Projekt SDK 16299 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="8225a-350">If you use the platform version of AcrylicBrush instead, the minimum version for your app project must be SDK 16299 or greater.</span></span> <span data-ttu-id="8225a-351">Um die Plattformversion verwenden möchten, entfernen Sie alle Verweise auf `muxm:`.</span><span class="sxs-lookup"><span data-stu-id="8225a-351">To use the platform version, remove all references to `muxm:`.</span></span>

```xaml
<Application
    <!-- ... -->
    xmlns:muxm="using:Microsoft.UI.Xaml.Media">
    <Application.Resources>
        <ResourceDictionary>
            <ResourceDictionary.MergedDictionaries>
                <XamlControlsResources xmlns="using:Microsoft.UI.Xaml.Controls"/>
                <ResourceDictionary>
                    <ResourceDictionary.ThemeDictionaries>
                        <ResourceDictionary x:Key="Default">
                            <!-- The "Default" theme dictionary is used unless a specific
                                 light, dark, or high contrast dictionary is provided. These
                                 resources should be tested with both the light and dark themes,
                                 and specific light or dark resources provided as needed. -->
                            <muxm:AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
                                   BackgroundSource="Backdrop"
                                   TintColor="LightSlateGray"
                                   TintOpacity=".6"/>
                            <muxm:AcrylicBrush x:Key="NavigationViewTopPaneBackground"
                                   BackgroundSource="Backdrop"
                                   TintColor="{ThemeResource SystemAccentColor}"
                                   TintOpacity=".6"/>
                            <LinearGradientBrush x:Key="NavigationViewExpandedPaneBackground"
                                     StartPoint="0.5,0" EndPoint="0.5,1">
                                <GradientStop Color="LightSlateGray" Offset="0.0" />
                                <GradientStop Color="White" Offset="1.0" />
                            </LinearGradientBrush>
                        </ResourceDictionary>
                        <ResourceDictionary x:Key="HighContrast">
                            <!-- Always include a "HighContrast" dictionary when you override
                                 theme resources. This empty dictionary ensures that the 
                                 default high contrast resources are used when the user
                                 turns on high contrast mode. -->
                        </ResourceDictionary>
                    </ResourceDictionary.ThemeDictionaries>
                </ResourceDictionary>
            </ResourceDictionary.MergedDictionaries>
        </ResourceDictionary>
    </Application.Resources>
</Application>
```

## <a name="related-topics"></a><span data-ttu-id="8225a-352">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8225a-352">Related topics</span></span>

- [<span data-ttu-id="8225a-353">NavigationView-Klasse</span><span class="sxs-lookup"><span data-stu-id="8225a-353">NavigationView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [<span data-ttu-id="8225a-354">Master/Details</span><span class="sxs-lookup"><span data-stu-id="8225a-354">Master/details</span></span>](master-details.md)
- [<span data-ttu-id="8225a-355">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="8225a-355">Navigation basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="8225a-356">Übersicht über Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="8225a-356">Fluent Design for UWP overview</span></span>](../fluent-design-system/index.md)
