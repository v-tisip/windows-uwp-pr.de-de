---
author: Jwmsft
Description: NavigationView is an adaptive control that implements top-level navigation patterns for your app.
title: Navigationsansicht
template: detail.hbs
ms.author: jimwalk
ms.date: 06/25/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: ''
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1c9f44f13df05aa408757a0766b2a652037707d1
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4567900"
---
# <a name="navigation-view-preview-version"></a><span data-ttu-id="5d5e0-103">Navigationsansicht (Preview-Version)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-103">Navigation view (Preview version)</span></span>

> <span data-ttu-id="5d5e0-104">**Dies ist eine Preview-Version**: in diesem Artikel wird beschrieben, eine neue Version des das NavigationView-Steuerelement, das noch in Entwicklung befindet.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-104">**This is a preview version**: This article describes a new version of the NavigationView control that's still in development.</span></span> <span data-ttu-id="5d5e0-105">Um es zu verwenden benötigen nun die [neuesten Windows-Insider-Builds und SDK](https://insider.windows.com/for-developers/) oder der [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="5d5e0-105">To use it now, you need the [latest Windows Insider build and SDK](https://insider.windows.com/for-developers/) or the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span>

<span data-ttu-id="5d5e0-106">Das NavigationView-Steuerelement bietet Navigation auf oberster Ebene für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-106">The NavigationView control provides top-level navigation for your app.</span></span> <span data-ttu-id="5d5e0-107">Sie passt sich eine Vielzahl von Bildschirmgrößen unterstützt mehrere Navigation Stile.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-107">It adapts to a variety of screen sizes supports multiple navigation styles.</span></span>

> <span data-ttu-id="5d5e0-108">**Windows-UI-Bibliothek-APIs**: [Microsoft.UI.Xaml.Controls.NavigationView-Klasse](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-108">**Windows UI Library APIs**: [Microsoft.UI.Xaml.Controls.NavigationView class](/uwp/api/microsoft.ui.xaml.controls.navigationview)</span></span>

> <span data-ttu-id="5d5e0-109">**Plattform-APIs**: [Windows.UI.Xaml.Controls.NavigationView-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-109">**Platform APIs**: [Windows.UI.Xaml.Controls.NavigationView class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)</span></span>

## <a name="get-the-windows-ui-library"></a><span data-ttu-id="5d5e0-110">Windows-UI-Bibliothek herunterladen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-110">Get the Windows UI Library</span></span>

<span data-ttu-id="5d5e0-111">Dieses Steuerelement ist Bestandteil der Windows-UI-Bibliothek, NuGet-Paket, das neue Steuerelemente und UI-Features für UWP-apps enthält.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-111">This control is included as part of the Windows UI Library, a NuGet package that contains new controls and UI features for UWP apps.</span></span> <span data-ttu-id="5d5e0-112">Weitere Informationen, einschließlich installationsanweisungen finden Sie unter der [Übersicht über die Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/).</span><span class="sxs-lookup"><span data-stu-id="5d5e0-112">For more info, including installation instructions, see the  [Windows UI Library overview](https://docs.microsoft.com/uwp/toolkits/winui/).</span></span> 

## <a name="navigation-styles"></a><span data-ttu-id="5d5e0-113">Navigation Stile</span><span class="sxs-lookup"><span data-stu-id="5d5e0-113">Navigation styles</span></span>

<span data-ttu-id="5d5e0-114">NavigationView unterstützt:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-114">NavigationView supports:</span></span>

**<span data-ttu-id="5d5e0-115">Linken Navigationsbereich oder dem Menü "</span><span class="sxs-lookup"><span data-stu-id="5d5e0-115">Left navigation pane or menu</span></span>**

![Navigationsbereich erweitert](images/displaymode-left.png)

**<span data-ttu-id="5d5e0-117">Oberer Navigationsbereich oder dem Menü "</span><span class="sxs-lookup"><span data-stu-id="5d5e0-117">Top navigation pane or menu</span></span>**

![oberen Navigationsleiste](images/displaymode-top.png)

## <a name="is-this-the-right-control"></a><span data-ttu-id="5d5e0-119">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="5d5e0-119">Is this the right control?</span></span>

<span data-ttu-id="5d5e0-120">NavigationView ist eine adaptive Navigationssteuerelement, das funktioniert gut für:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-120">NavigationView is an adaptive navigation control that works well for:</span></span>

- <span data-ttu-id="5d5e0-121">Bereitstellen einer konsistenten navigationsumgebungen in der gesamten app.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-121">Providing a consistent navigational experience throughout your app.</span></span>
- <span data-ttu-id="5d5e0-122">Sparen von Platz auf dem Bildschirm auf kleineren Fenstern.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-122">Preserving screen real estate on smaller windows.</span></span>
- <span data-ttu-id="5d5e0-123">Zugriff auf viele Navigationskategorien organisieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-123">Organizing access to many navigation categories.</span></span>

<span data-ttu-id="5d5e0-124">Andere Navigationssteuerelementen finden Sie unter [navigationsdesigngrundlagen](../basics/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5d5e0-124">For other navigation controls, see [Navigation design basics](../basics/navigation-basics.md).</span></span>

<span data-ttu-id="5d5e0-125">Wenn die Navigation komplexeres Verhalten erfordert, das von NavigationView nicht unterstützt wird, können Sie stattdessen das [Master/Details](master-details.md)-Muster verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-125">If your navigation requires more complex behavior that is not supported by NavigationView, then you might want to consider the [Master/details](master-details.md) pattern instead.</span></span>

:::row:::
    :::column:::
        ![Some image](images/XAML-controls-gallery-app-icon.png)
    :::column-end:::
    :::column span="2":::
        **XAML Controls Gallery**<br>
        If you have the XAML Controls Gallery app installed, click <a href="xamlcontrolsgallery:/item/NavigationView">here</a> to open the app and see NavigationView in action.

        <a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a><br>
        <a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a>
    :::column-end:::
:::row-end:::

## <a name="display-modes"></a><span data-ttu-id="5d5e0-126">Anzeigemodus</span><span class="sxs-lookup"><span data-stu-id="5d5e0-126">Display modes</span></span>

<span data-ttu-id="5d5e0-127">NavigationView kann auf unterschiedliche Anzeigemodi festgelegt werden, über die `PaneDisplayMode` Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-127">NavigationView can be set to different display modes, via the `PaneDisplayMode` property:</span></span>

:::row:::
    :::column:::
    ### <a name="left"></a><span data-ttu-id="5d5e0-128">Links</span><span class="sxs-lookup"><span data-stu-id="5d5e0-128">Left</span></span>
    <span data-ttu-id="5d5e0-129">Zeigt eine erweiterte linken positioniert Bereich an.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-129">Displays an expanded left positioned pane.</span></span>
    :::column-end:::
    :::column span="2":::
    ![linken Navigationsbereich erweitert](images/displaymode-left.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="5d5e0-131">Wir empfehlen die linke Navigation beim:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-131">We recommend left navigation when:</span></span>

- <span data-ttu-id="5d5e0-132">Sie haben eine mittlere bis hohe Anzahl (5-10) wichtiger Navigation auf oberster Ebene Kategorien.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-132">You have a medium-to-high number (5-10) of equally important top-level navigation categories.</span></span>
- <span data-ttu-id="5d5e0-133">Gewünschte sehr wichtigen Navigationskategorien mit weniger Speicherplatz für die anderen Inhalten der app.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-133">You desire very prominent navigation categories with less space for other app content.</span></span>

:::row:::
    :::column:::
    ### <a name="top"></a><span data-ttu-id="5d5e0-134">Oben</span><span class="sxs-lookup"><span data-stu-id="5d5e0-134">Top</span></span>
    <span data-ttu-id="5d5e0-135">Zeigt eine obere positioniert Bereich.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-135">Displays a top positioned pane.</span></span>
    :::column-end:::
    :::column span="2":::
    ![oberen Navigationsleiste](images/displaymode-top.png)
    :::column-end:::
:::row-end:::

<span data-ttu-id="5d5e0-137">Wir empfehlen oberen Navigationsleiste beim:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-137">We recommend top navigation when:</span></span>

- <span data-ttu-id="5d5e0-138">Sie haben 5 oder weniger wichtiger Navigationskategorien der obersten Ebene, zusätzliche Navigation auf oberster Ebene Kategorien, die in der Dropdownliste landen Überlauf Menü gelten als weniger wichtig.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-138">You have 5 or less equally important top-level navigation categories, such that any additional top-level navigation categories that end up in the dropdown overflow menu are considered less important.</span></span>
- <span data-ttu-id="5d5e0-139">Sie müssen alle Navigationsoptionen auf dem Bildschirm anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-139">You need to show all navigation options on screen.</span></span>
- <span data-ttu-id="5d5e0-140">Sie möchten mehr Platz für Ihre app-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-140">You desire more space for your app content.</span></span>
- <span data-ttu-id="5d5e0-141">Symbole können nicht klar Navigationskategorien Ihrer app beschreiben.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-141">Icons cannot clearly describe your app's navigation categories.</span></span>

:::row:::
    :::column:::
    ### <a name="leftcompact"></a><span data-ttu-id="5d5e0-142">LeftCompact</span><span class="sxs-lookup"><span data-stu-id="5d5e0-142">LeftCompact</span></span>
    <span data-ttu-id="5d5e0-143">Zeigt eine dünne Streifen mit Symbolen auf der linken Seite an.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-143">Displays a thin sliver with icons on the left.</span></span>
    :::column-end:::
    :::column span="2":::
    ![kompakte Navigationsbereich](images/displaymode-leftcompact.png)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
    ### <a name="leftminimal"></a><span data-ttu-id="5d5e0-145">LeftMinimal</span><span class="sxs-lookup"><span data-stu-id="5d5e0-145">LeftMinimal</span></span>
    <span data-ttu-id="5d5e0-146">Zeigt nur die Menüschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-146">Displays only the menu button.</span></span>
    :::column-end:::
    :::column span="2":::
    ![Minimale Navigationsbereich](images/displaymode-leftminimal.png)
    :::column-end:::
:::row-end:::

### <a name="auto"></a><span data-ttu-id="5d5e0-148">Auto</span><span class="sxs-lookup"><span data-stu-id="5d5e0-148">Auto</span></span>

![GIF Leftnav standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)

<span data-ttu-id="5d5e0-150">Passt zwischen LeftMinimal auf kleinen Bildschirmen, LeftCompact für mittelgroße Bildschirme und Links auf großen Bildschirmen an.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-150">Adapts between LeftMinimal on small screens, LeftCompact on medium screens, and Left on large screens.</span></span> <span data-ttu-id="5d5e0-151">Finden Sie im Abschnitt [adaptives Verhalten](#adaptive-behavior) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-151">See the [adaptive behavior](#adaptive-behavior) section for more information.</span></span>

## <a name="anatomy"></a><span data-ttu-id="5d5e0-152">Aufbau</span><span class="sxs-lookup"><span data-stu-id="5d5e0-152">Anatomy</span></span>

<b><span data-ttu-id="5d5e0-153">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-153">Left nav</span></span></b><br>

![linke Abschnitte von NavigationView](images/leftnav-anatomy.png)

<b><span data-ttu-id="5d5e0-155">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-155">Top nav</span></span></b><br>

![Top-Abschnitte von NavigationView](images/topnav-anatomy.png)

## <a name="pane"></a><span data-ttu-id="5d5e0-157">Bereich</span><span class="sxs-lookup"><span data-stu-id="5d5e0-157">Pane</span></span>

<span data-ttu-id="5d5e0-158">Der Bereich kann positioniert werden im Vordergrund oder links, über die `PanePosition` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-158">The pane can be positioned either on top or on left, via the `PanePosition` property.</span></span>

<span data-ttu-id="5d5e0-159">Hier ist der Aufbau detaillierte Bereich für die linken und oberen Bereich Positionen:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-159">Here is the detailed pane anatomy for the left and top pane positions:</span></span>

<b><span data-ttu-id="5d5e0-160">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-160">Left nav</span></span></b><br>

![NavigationView Anatomie](images/navview-pane-anatomy-vertical.png)

1. <span data-ttu-id="5d5e0-162">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-162">Menu button</span></span>
1. <span data-ttu-id="5d5e0-163">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="5d5e0-163">Navigation items</span></span>
1. <span data-ttu-id="5d5e0-164">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-164">Separators</span></span>
1. <span data-ttu-id="5d5e0-165">Header</span><span class="sxs-lookup"><span data-stu-id="5d5e0-165">Headers</span></span>
1. <span data-ttu-id="5d5e0-166">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-166">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="5d5e0-167">Schaltfläche "Einstellungen" (optional)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-167">Settings button (optional)</span></span>

<b><span data-ttu-id="5d5e0-168">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-168">Top nav</span></span></b><br>

![NavigationView Anatomie](images/navview-pane-anatomy-horizontal.png)

1. <span data-ttu-id="5d5e0-170">Header</span><span class="sxs-lookup"><span data-stu-id="5d5e0-170">Headers</span></span>
1. <span data-ttu-id="5d5e0-171">Navigationselemente</span><span class="sxs-lookup"><span data-stu-id="5d5e0-171">Navigation items</span></span>
1. <span data-ttu-id="5d5e0-172">Trennzeichen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-172">Separators</span></span>
1. <span data-ttu-id="5d5e0-173">AutoSuggestBox (optional)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-173">AutoSuggestBox (optional)</span></span>
1. <span data-ttu-id="5d5e0-174">Schaltfläche "Einstellungen" (optional)</span><span class="sxs-lookup"><span data-stu-id="5d5e0-174">Settings button (optional)</span></span>

<span data-ttu-id="5d5e0-175">Die Schaltfläche "zurück" angezeigt, in der oberen linken Ecke des Bereichs, aber NavigationView nicht automatisch Inhalte auf die zurück-Stapel hinzu.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-175">The back button appears in the top left-hand corner of the pane, but NavigationView does not automatically add content to the back stack.</span></span> <span data-ttu-id="5d5e0-176">Zum Aktivieren der Rückwärtsnavigation, finden Sie unter der [Rückwärts Navigation](#backwards-navigation) Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-176">To enable backwards navigation, see the [backwards navigation](#backwards-navigation) section.</span></span>

<span data-ttu-id="5d5e0-177">Der NavigationView-Bereich kann auch Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-177">The NavigationView pane can also contain:</span></span>

1. <span data-ttu-id="5d5e0-178">Navigationselemente in Form von [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), um zu bestimmten Seiten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-178">Navigation items, in the form of [NavigationViewItem](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitem), for navigating to specific pages.</span></span>
2. <span data-ttu-id="5d5e0-179">Trennzeichen in Form von [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), um Navigationselemente zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-179">Separators, in the form of [NavigationViewItemSeparator](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator), for grouping navigation items.</span></span> <span data-ttu-id="5d5e0-180">Legen Sie die [Opacity](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) -Eigenschaft auf 0 fest, um das Trennzeichen Platz nötig rendern.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-180">Set the [Opacity](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemseparator.opacity) property to 0 to render the separator as space.</span></span>
3. <span data-ttu-id="5d5e0-181">Header in Form von [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), zum Beschriften von Gruppen von Elementen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-181">Headers, in the form of [NavigationViewItemHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationviewitemheader), for labeling groups of items.</span></span>
4. <span data-ttu-id="5d5e0-182">Eine optionale [AutoSuggestBox](auto-suggest-box.md) für die app-Ebene Suche zulassen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-182">An optional [AutoSuggestBox](auto-suggest-box.md) to allow for app-level search.</span></span>
5. <span data-ttu-id="5d5e0-183">Ein optionaler Einstiegspunkt für [App-Einstellungen](../app-settings/app-settings-and-data.md).</span><span class="sxs-lookup"><span data-stu-id="5d5e0-183">An optional entry point for [app settings](../app-settings/app-settings-and-data.md).</span></span> <span data-ttu-id="5d5e0-184">Um das Einstellungen-Element zu verbergen, verwenden Sie die [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-184">To hide the settings item, use the [IsSettingsVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsSettingsVisible) property.</span></span>

<span data-ttu-id="5d5e0-185">Im linke Bereich enthält:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-185">The left pane contains:</span></span>

6. <span data-ttu-id="5d5e0-186">Menüschaltfläche, um den Bereich öffnen und schließen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-186">Menu button to toggle the pane open and close.</span></span> <span data-ttu-id="5d5e0-187">Sie können bei größeren App-Fenstern mit geöffnetem Bereich diese Schaltfläche mit der Eigenschaft [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) ausblenden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-187">On larger app windows when the pane is open, you may choose to hide this button using the [IsPaneToggleButtonVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsPaneToggleButtonVisible) property.</span></span>

### <a name="pane-footer"></a><span data-ttu-id="5d5e0-188">Fußzeile</span><span class="sxs-lookup"><span data-stu-id="5d5e0-188">Pane footer</span></span>

<span data-ttu-id="5d5e0-189">Freier Inhalt in der Fußzeile des Bereichs beim Hinzufügen zur [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter)-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5d5e0-189">Free-form content in the pane’s footer, when added to the [PaneFooter](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneFooter) property</span></span>

:::row:::
    :::column:::
    <b><span data-ttu-id="5d5e0-190">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-190">Left nav</span></span></b><br>
    ![Bereich Fußzeile linke Navigationsleiste](images/navview-freeform-footer-left.png)<br>
    :::column-end:::
    :::column:::
     <b><span data-ttu-id="5d5e0-192">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-192">Top nav</span></span></b><br>
    ![Bereich Header oben nav](images/navview-freeform-footer-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-header"></a><span data-ttu-id="5d5e0-194">Kopfdaten</span><span class="sxs-lookup"><span data-stu-id="5d5e0-194">Pane header</span></span>

<span data-ttu-id="5d5e0-195">Freier Inhalt in den Bereich Header, wenn die Eigenschaft [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="5d5e0-195">Free-form content in the pane's header, when added to the [PaneHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneHeader) property</span></span>

:::row:::
    :::column:::
    <b><span data-ttu-id="5d5e0-196">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-196">Left nav</span></span></b><br>
    ![Bereich Header linke Navigationsleiste](images/navview-freeform-header-left.png)<br>
    :::column-end:::
    :::column:::
     <b><span data-ttu-id="5d5e0-198">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-198">Top nav</span></span></b><br>
    ![Bereich Header oben nav](images/navview-freeform-header-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="pane-content"></a><span data-ttu-id="5d5e0-200">Inhalt</span><span class="sxs-lookup"><span data-stu-id="5d5e0-200">Pane content</span></span>

<span data-ttu-id="5d5e0-201">Freier Inhalt in den Bereich, wenn die Eigenschaft [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="5d5e0-201">Free-form content in the pane, when added to the [PaneCustomContent](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PaneCustomContent) property</span></span>

:::row:::
    :::column:::
    <b><span data-ttu-id="5d5e0-202">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-202">Left nav</span></span></b><br>
    ![Bereich benutzerdefinierte Contentleft nav](images/navview-freeform-pane-left.png)<br>
    :::column-end:::
    :::column:::
     <b><span data-ttu-id="5d5e0-204">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-204">Top nav</span></span></b><br>
    ![Bereich benutzerdefinierte Inhalte oben nav](images/navview-freeform-pane-top.png)<br>
    :::column-end:::
:::row-end:::

### <a name="visual-style"></a><span data-ttu-id="5d5e0-206">Visueller Stil</span><span class="sxs-lookup"><span data-stu-id="5d5e0-206">Visual style</span></span>

<span data-ttu-id="5d5e0-207">Wenn Hardware-und softwareanforderungen erfüllt sind, verwendet NavigationView automatisch das [Acryl-Material](../style/acrylic.md) in seinem Bereich und [Reveal-Highlight](../style/reveal.md) , nur in der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-207">When hardware and software requirements are met, NavigationView automatically uses the [Acrylic material](../style/acrylic.md) in its pane, and [Reveal highlight](../style/reveal.md) only in its left pane.</span></span>

## <a name="header"></a><span data-ttu-id="5d5e0-208">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="5d5e0-208">Header</span></span>

![Navview allgemeines Bild der Header-Bereich](images/nav-header.png)

<span data-ttu-id="5d5e0-210">Der Kopfzeilenbereich die Navigationsschaltfläche "in der linken Seite Position vertikal ausgerichtet ist, und unter dem Bereich in der oberen Bereich Position liegt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-210">The header area is vertically aligned with the navigation button in the left pane position, and lies below the pane in the top pane position.</span></span> <span data-ttu-id="5d5e0-211">Es hat eine feste Höhe von 52 Pixel.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-211">It has a fixed height of 52 px.</span></span> <span data-ttu-id="5d5e0-212">Er dient dazu, den Seitentitel der ausgewählten Navigationskategorie aufrechtzuerhalten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-212">Its purpose is to hold the page title of the selected nav category.</span></span> <span data-ttu-id="5d5e0-213">Die Kopfzeile ist an den oberen Rand der Seite angedockt und dient als Scroll-Clipping-Punkt für den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-213">The header is docked to the top of the page and acts as a scroll clipping point for the content area.</span></span>

<span data-ttu-id="5d5e0-214">Die Kopfzeile muss sichtbar sein, wenn sich NavigationView im minimierten Anzeigemodus befindet.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-214">The header must be visible when NavigationView is in Minimal display mode.</span></span> <span data-ttu-id="5d5e0-215">Sie können die Kopfzeile in anderen Modi ausblenden, die bei größeren Fensterbreiten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-215">You may choose to hide the header in other modes, which are used on larger window widths.</span></span> <span data-ttu-id="5d5e0-216">Legen Sie dazu die Eigenschaft [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) auf **false** fest.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-216">To do so, set the [AlwaysShowHeader](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.AlwaysShowHeader) property to **false**.</span></span>

## <a name="content"></a><span data-ttu-id="5d5e0-217">Inhalt</span><span class="sxs-lookup"><span data-stu-id="5d5e0-217">Content</span></span>

![Navview allgemeines Bild des Inhaltsbereichs](images/nav-content.png)

<span data-ttu-id="5d5e0-219">Im Inhaltsbereich werden die meisten Informationen für die ausgewählte Navigationskategorie angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-219">The content area is where most of the information for the selected nav category is displayed.</span></span>

<span data-ttu-id="5d5e0-220">Wir empfehlen, Ränder für Ihren Inhaltsbereich auf 12Pixel festzulegen, wenn sich NavigationView im minimierten Modus befindet. Verwenden Sie andernfalls 24Pixel.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-220">We recommend 12px margins for your content area when NavigationView is in Minimal mode and 24px margins otherwise.</span></span>

## <a name="adaptive-behavior"></a><span data-ttu-id="5d5e0-221">Adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="5d5e0-221">Adaptive behavior</span></span>

<span data-ttu-id="5d5e0-222">NavigationView ändert je nach verfügbarem Platz auf dem Bildschirm automatisch den Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-222">NavigationView automatically changes its display mode based on the amount of screen space available to it.</span></span> <span data-ttu-id="5d5e0-223">Möglicherweise möchten jedoch das adaptive anzeigemodusverhalten anpassen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-223">However, you might want to customize the adaptive display mode behavior.</span></span>

### <a name="default"></a><span data-ttu-id="5d5e0-224">Standard</span><span class="sxs-lookup"><span data-stu-id="5d5e0-224">Default</span></span>

<span data-ttu-id="5d5e0-225">Die standardmäßigen adaptiven Verhaltens von NavigationView ist zum Anzeigen einer erweiterten linken Bereich auf großen fensterbreiten, ein Symbol nur Navigationsbereich bei mittelgroßen fensterbreiten und eine Hamburger-Menü-Schaltfläche auf kleine fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-225">The default adaptive behavior of NavigationView is to show an expanded left pane on large window widths, a left icon-only nav pane on medium window widths, and a hamburger menu button on small window widths.</span></span> <span data-ttu-id="5d5e0-226">Weitere Informationen zu Fenstergrößen für adaptives Verhalten finden Sie unter [Bildschirmgrößen und Breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span><span class="sxs-lookup"><span data-stu-id="5d5e0-226">For more information about window sizes for adaptive behavior, see [Screen sizes and breakpoints](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

![GIF Leftnav standardmäßigen adaptiven Verhaltens](images/displaymode-auto.png)

```xaml
<NavigationView />
```

### <a name="minimal"></a><span data-ttu-id="5d5e0-228">Minimiert</span><span class="sxs-lookup"><span data-stu-id="5d5e0-228">Minimal</span></span>

<span data-ttu-id="5d5e0-229">Ein zweites Allgemeines adaptives Muster ist die Verwendung einen erweiterten linken Bereich auf großen fensterbreiten und ein Hamburger-Menü auf beide kleinen und mittelgroßen fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-229">A second common adaptive pattern is to use an expanded left pane on large window widths, and a hamburger menu on both medium and small window widths.</span></span>

![GIF Leftnav adaptives Verhalten 2](images/adaptive-behavior-minimal.png)

```xaml
<NavigationView CompactModeThresholdWidth="1008" ExpandedModeThresholdWidth="1007" />
```

<span data-ttu-id="5d5e0-231">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-231">We recommend this when:</span></span>

- <span data-ttu-id="5d5e0-232">Sie möchten mehr Platz für app-Inhalte auf kleinere fensterbreiten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-232">You desire more space for app content on smaller window widths.</span></span>
- <span data-ttu-id="5d5e0-233">Ihre Navigationskategorien werden nicht eindeutig mit Symbolen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-233">Your navigation categories cannot be clearly represented with icons.</span></span>

### <a name="compact"></a><span data-ttu-id="5d5e0-234">Kompakt</span><span class="sxs-lookup"><span data-stu-id="5d5e0-234">Compact</span></span>

<span data-ttu-id="5d5e0-235">Ein drittes Allgemeines adaptives Muster ist einen erweiterten linken Bereich auf großen fensterbreiten und ein Symbol nur Navigationsbereich auf beide kleinen und mittelgroßen fensterbreiten verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-235">A third common adaptive pattern is to use an expanded left pane on large window widths, and a left icon-only nav pane on both medium and small window widths.</span></span> <span data-ttu-id="5d5e0-236">Ein gutes Beispiel hierfür ist die Mail-app.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-236">A good example of this is the Mail app.</span></span>

![GIF Leftnav adaptives Verhalten 3](images/adaptive-behavior-compact.png)

```xaml
<NavigationView CompactModeThresholdWidth="0" ExpandedModeThresholdWidth="1007" />
```

<span data-ttu-id="5d5e0-238">Wir empfehlen diese Lösung, wenn:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-238">We recommend this when:</span></span>

- <span data-ttu-id="5d5e0-239">Es ist wichtig, immer alle Navigationsoptionen auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-239">It is important to always show all navigation options on screen.</span></span>
- <span data-ttu-id="5d5e0-240">Ihre Navigationskategorien können deutlich mit Symbolen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-240">your navigation categories can be clearly represented with icons.</span></span>

### <a name="no-adaptive-behavior"></a><span data-ttu-id="5d5e0-241">Keine adaptives Verhalten</span><span class="sxs-lookup"><span data-stu-id="5d5e0-241">No adaptive behavior</span></span>

<span data-ttu-id="5d5e0-242">In einigen Fällen möglicherweise keine adaptives Verhalten überhaupt gewünschte.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-242">Sometimes you may not desire any adaptive behavior at all.</span></span> <span data-ttu-id="5d5e0-243">Sie können den Bereich zu immer erweitert, immer compact oder immer minimale festlegen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-243">You can set the pane to be always expanded, always compact, or always minimal.</span></span>

![GIF Leftnav adaptives Verhalten 4](images/adaptive-behavior-none.png)

```xaml
<NavigationView PaneDisplayMode="LeftMinimal" />
```

### <a name="top-to-left-navigation"></a><span data-ttu-id="5d5e0-245">Von oben nach links</span><span class="sxs-lookup"><span data-stu-id="5d5e0-245">Top to left navigation</span></span>

<span data-ttu-id="5d5e0-246">Wir empfehlen die Verwendung der oberen Navigationsleiste auf großen Fenstergrößen und linken Navigationsbereich auf kleinen Fenster Größe wenn:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-246">We recommend using top navigation on large window sizes and left navigation on small window sizes when:</span></span>

- <span data-ttu-id="5d5e0-247">Sie haben eine Reihe von gleichermaßen wichtig Navigation auf oberster Ebene Kategorien zusammen angezeigt werden, wenn eine Kategorie in diesen auf dem Bildschirm passt, Sie die linke Navigation zu gleichbedeutend reduzieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-247">You have a set of equally important top-level navigation categories to be displayed together, such that if one category in this set doesn't fit on screen, you collapse to left navigation to give them equal importance.</span></span>
- <span data-ttu-id="5d5e0-248">Möchten Sie so viel Content Speicherplatz wie möglich in kleinen Fenstergrößen beibehalten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-248">You wish to preserve as much content space as possible in small window sizes.</span></span>

<span data-ttu-id="5d5e0-249">Hier ist ein Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-249">Here is an example:</span></span>

![GIF oberen oder linken Nav adaptives Verhalten 1](images/navigation-top-to-left.png)

```xaml
<Grid >
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState>
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                </VisualState.StateTriggers>

                <VisualState.Setters>
                    <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>

    <NavigationView x:Name="NavigationViewControl" >
        <NavigationView.MenuItems>
            <NavigationViewItem Content="A" x:Name="A" />
            <NavigationViewItem Content="B" x:Name="B" />
            <NavigationViewItem Content="C" x:Name="C" />
        </NavigationView.MenuItems>
    </NavigationView>
</Grid>

```

<span data-ttu-id="5d5e0-251">In einigen Fällen müssen apps unterschiedliche Daten an den oberen Bereich und Links zu binden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-251">Sometimes apps need to bind different data to the top pane and left pane.</span></span> <span data-ttu-id="5d5e0-252">Im linke Bereich umfasst häufig weitere Elemente für die Navigation.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-252">Often the left pane includes more navigation elements.</span></span>

<span data-ttu-id="5d5e0-253">Hier ist ein Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-253">Here is an example:</span></span>

![GIF oberen oder linken Nav adaptives Verhalten 2](images/navigation-top-to-left2.png)

```xaml
<Page >
    <Page.Resources>
        <DataTemplate x:name="navItem_top_temp" x:DataType="models:Item">
            <NavigationViewItem Background= Icon={x:Bind TopIcon}, Content={x:Bind TopContent}, Visibility={x:Bind TopVisibility} />
        </DataTemplate>

        <DataTemplate x:name="navItem_temp" x:DataType="models:Item">
            <NavigationViewItem Icon={x:Bind Icon}, Content={x:Bind Content}, Visibility={x:Bind Visibility} />
        </DataTemplate>
        
        <services:NavViewDataTemplateSelector x:Key="navview_selector" 
              NavItemTemplate="{StaticResource navItem_temp}" 
              NavItemTopTemplate="{StaticResource navItem_top_temp}" 
              NavPaneDisplayMode="{x:Bind NavigationViewControl.PaneDisplayMode}">
        </services:NavViewDataTemplateSelector>
    </Page.Resources>

    <Grid >
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup>
                <VisualState>
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="{x:Bind NavigationViewControl.CompactModeThresholdWidth}" />
                    </VisualState.StateTriggers>

                    <VisualState.Setters>
                        <Setter Target="NavigationViewControl.PaneDisplayMode" Value="Top"/>
                    </VisualState.Setters>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        <NavView x:Name='NavigationViewControl' MenuItemsSource={x:Bind items}   
                 PanePosition = "Top" MenuItemTemplateSelector="navview_selector" />
    </Grid>
</Page>

```

```csharp
ObservableCollection<Item> items = new ObservableCollection<Item>();
items.Add(new Item() {
    Content = "Aa",
    TopContent ="A",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});
items.Add(new Item() {
    Content = "Bb",
    TopContent = "B",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});
items.Add(new Item() {
    Content = "Cc",
    TopContent = "C",
    Icon = new BitmapIcon() { UriSource = new Uri("ms-appx:///testimage.jpg") },
    TopIcon = new BitmapIcon(),
    ItemVisibility = Visibility.Visible,
    TopItemVisiblity = Visibility.Visible 
});

public class NavViewDataTemplateSelector : DataTemplateSelector
{
    public DataTemplate NavItemTemplate { get; set; }

    public DataTemplate NavItemTopTemplate { get; set; }    

    public NavigationViewPaneDisplayMode NavPaneDisplayMode { get; set; }

    protected override DataTemplate SelectTemplateCore(object item)
    {
        Item currItem = item as Item;
        if (NavPaneDisplayMode == NavigationViewPanePosition.Top)
            return NavItemTopTemplate;
        else 
            return NavItemTemplate;
    }   

}

```

## <a name="interaction"></a><span data-ttu-id="5d5e0-255">Interaktion</span><span class="sxs-lookup"><span data-stu-id="5d5e0-255">Interaction</span></span>

<span data-ttu-id="5d5e0-256">Wenn Benutzer in dem Bereich auf ein Navigationselement tippen, zeigt NavigationView dieses Element als ausgewählt an und löst ein [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-256">When users tap on a navigation item in the Pane, NavigationView will show that item as selected and will raise an [ItemInvoked](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ItemInvoked) event.</span></span> <span data-ttu-id="5d5e0-257">Wenn durch das Tippen ein neues Element ausgewählt, löst NavigationView ebenfalls ein [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-257">If the tap results in a new item being selected, NavigationView will also raise a [SelectionChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.SelectionChanged) event.</span></span>

<span data-ttu-id="5d5e0-258">Es ist Aufgabe Ihrer App, die Kopfzeile und den Inhalt in Reaktion auf diese Benutzerinteraktion mit entsprechenden Informationen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-258">Your app is responsible for updating the Header and Content with appropriate information in response to this user interaction.</span></span> <span data-ttu-id="5d5e0-259">Darüber hinaus wird empfohlen, den [Fokus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.FocusState) programmgesteuert vom Navigationselement zum Inhalt zu verlagern.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-259">In addition, we recommend programmatically moving [focus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.control.FocusState) from the navigation item to the content.</span></span> <span data-ttu-id="5d5e0-260">Wenn Sie den anfänglichen Fokus auf das Laden festlegen, optimieren Sie den Benutzerfluss und verringern die Anzahl der Verschiebungen des Tastaturfokus.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-260">By setting initial focus on load, you streamline the user flow and minimize the expected number of keyboard focus moves.</span></span>

### <a name="tabs"></a><span data-ttu-id="5d5e0-261">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="5d5e0-261">Tabs</span></span>

<span data-ttu-id="5d5e0-262">In den Registerkarten-Modell sind Auswahl und Fokus gebunden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-262">In the tabs model, selection and focus are tied.</span></span> <span data-ttu-id="5d5e0-263">Eine Aktion, die normalerweise Schichten auch Auswahl Fokus würde.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-263">An action that normally shifts focus would also shift selection.</span></span> <span data-ttu-id="5d5e0-264">In dem Beispiel unten haben rechten Arrowing verschoben Marke für die Auswahl aus der Anzeige Bildschirmlupe.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-264">In the below example, right arrowing would move the selection indicator from Display to Magnifier.</span></span> <span data-ttu-id="5d5e0-265">Sie können dies erreichen, indem Sie die [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.selectionfollowsfocus) -Eigenschaft aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-265">You can achieve this by setting the [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.selectionfollowsfocus) property to Enabled.</span></span>

![Screenshot von nur-Text-oberen navview](images/nav-tabs.png)

<span data-ttu-id="5d5e0-267">Nachfolgend finden Sie im XAML-Beispiel für diese:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-267">Here is the example XAML for that:</span></span>

```xaml
<NavigationView PanePosition="Top" SelectionFollowsFocus="Enabled" >
   <NavigationView.MenuItems>
        <NavigationViewItem Content="Display" />
        <NavigationViewItem Content="Magnifier"  />
        <NavigationViewItem Content="Keyboard" />
    </NavigationView.MenuItems>
</NavigationView>

```

<span data-ttu-id="5d5e0-268">Um austauschen, um den Inhalt beim Registerkarte Auswahl zu ändern, können Sie Frames [NavigateWithOptions](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame.NavigateToType) Methode FrameNavigationOptions.IsNavigationStackEnabled auf "false" festgelegt, und NavigateOptions.TransitionInfoOverride festlegen, um die entsprechenden für nebeneinander Folienanimation.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-268">To swap out content when changing tab selection, you can use Frame's [NavigateWithOptions](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame.NavigateToType) method with FrameNavigationOptions.IsNavigationStackEnabled set to False, and NavigateOptions.TransitionInfoOverride set to the appropriate side-to-side slide animation.</span></span> <span data-ttu-id="5d5e0-269">Ein Beispiel finden Sie im [Codebeispiel](#code-example) unten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-269">For an example, see the [code example](#code-example) below.</span></span>

<span data-ttu-id="5d5e0-270">Wenn Sie den Standardstil ändern möchten, können Sie NavigationView [MenuItemContainerStyle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemcontainerstyle) Eigenschaft überschreiben.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-270">If you wish to change the default Style, you can override NavigationView's [MenuItemContainerStyle](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemcontainerstyle) property.</span></span> <span data-ttu-id="5d5e0-271">Sie können auch die [MenuItemTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemtemplate) -Eigenschaft an eine andere Datenvorlage festlegen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-271">You can also set the [MenuItemTemplate](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.menuitemtemplate) property to specify a different data template.</span></span>

## <a name="backwards-navigation"></a><span data-ttu-id="5d5e0-272">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="5d5e0-272">Backwards navigation</span></span>

<span data-ttu-id="5d5e0-273">NavigationView verfügt über eine integrierte Schaltfläche „Zurück“, die mit den folgenden Eigenschaften aktiviert werden kann:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-273">NavigationView has a built-in back button, which can be enabled with the following properties:</span></span>

- <span data-ttu-id="5d5e0-274">[**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) ist eine NavigationViewBackButtonVisible-Enumeration und standardmäßig auf "Auto" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-274">[**IsBackButtonVisible**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackButtonVisible) is a NavigationViewBackButtonVisible enum and "Auto" by default.</span></span> <span data-ttu-id="5d5e0-275">Sie dient zum Einblenden/Ausblenden der Schaltfläche „Zurück“.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-275">It is used to show/hide the back button.</span></span> <span data-ttu-id="5d5e0-276">Wenn die Schaltfläche nicht angezeigt wird, wird der Platz für die Darstellung der Schaltfläche „Zurück“ reduziert.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-276">When the button is not visible, the space for drawing the back button will be collapsed.</span></span>
- <span data-ttu-id="5d5e0-277">[**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) lautet standardmäßig „false“ und kann zum Umschalten des Status der Schaltfläche „Zurück“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-277">[**IsBackEnabled**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.IsBackEnabled) is false by default and can be used to toggle the back button states.</span></span>
- <span data-ttu-id="5d5e0-278">[**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) wird ausgelöst, wenn ein Benutzer auf die Schaltfläche „Zurück“ klickt.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-278">[**BackRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.BackRequested) is fired when a user clicks on the back button.</span></span>
    - <span data-ttu-id="5d5e0-279">Wenn im minimalen oder kompakten Modus der NavigationView.Pane als Flyout geöffnet ist und auf die Schaltfläche „Zurück“ geklickt wird, wird der Bereich geschlossen und stattdessen das **PaneClosing**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-279">In Minimal/Compact mode, when the NavigationView.Pane is open as a flyout, clicking the back button will close the Pane and fire **PaneClosing** event instead.</span></span>
    - <span data-ttu-id="5d5e0-280">Wenn IsBackEnabled auf „false“ festgelegt ist, wird es nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-280">Not fired if IsBackEnabled is false.</span></span>

:::row:::
    :::column:::
    <b><span data-ttu-id="5d5e0-281">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="5d5e0-281">Left nav</span></span></b><br>
    ![Zurück-Schaltfläche auf linke Navigationsleiste](images/leftnav-back.png)
    :::column-end:::
    :::column:::
     <b><span data-ttu-id="5d5e0-283">Oben nav</span><span class="sxs-lookup"><span data-stu-id="5d5e0-283">Top nav</span></span></b><br>
    ![Zurück-Schaltfläche auf oben nav](images/topnav-back.png)
    :::column-end:::
:::row-end:::

## <a name="code-example"></a><span data-ttu-id="5d5e0-285">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="5d5e0-285">Code example</span></span>

> [!NOTE]
> <span data-ttu-id="5d5e0-286">NavigationView sollte als der Stammcontainer Ihrer App dienen, da dieses Steuerelement darauf ausgelegt ist, die volle Breite und Höhe des App-Fensters einzunehmen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-286">NavigationView should serve as the root container of your app, as this control is designed to span the full width and height of the app window.</span></span>
<span data-ttu-id="5d5e0-287">Sie können die Breite der angezeigten Anzeigemodi in der Navigationsansicht mit den Eigenschaften [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) und [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-287">You can override the widths at which the navigation view changes display modes by using the [CompactModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.CompactModeThresholdWidth) and [ExpandedModeThresholdWidth](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ExpandedModeThresholdWidth) properties.</span></span>

<span data-ttu-id="5d5e0-288">Der folgende Code ist ein End-to-End-Beispiel dafür, wie Sie NavigationView mit ein oberer Navigationsbereich auf großen Fenstergrößen und einem linken Navigationsbereich auf kleinen Fenstergrößen integrieren können.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-288">The following is an end-to-end example of how you can incorporate NavigationView with both a top navigation pane on large window sizes and a left navigation pane on small window sizes.</span></span>

<span data-ttu-id="5d5e0-289">In diesem Beispiel werden wir davon ausgehen, dass Endbenutzer häufig neue Navigationskategorien auszuwählen, und wir:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-289">In this sample, we expect end users to frequently select new navigation categories, and so we:</span></span>

- <span data-ttu-id="5d5e0-290">Legen Sie die Eigenschaft [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) aktiviert</span><span class="sxs-lookup"><span data-stu-id="5d5e0-290">Set the [SelectionFollowsFocus](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) property to Enabled</span></span>
- <span data-ttu-id="5d5e0-291">Verwenden Sie die Frame-Navigation, die nicht Navigationsstapel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-291">Use Frame navigations that do not add to the navigation stack.</span></span>
- <span data-ttu-id="5d5e0-292">Behalten Sie den Standardwert für die [ShoulderNavigationEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) -Eigenschaft, die verwendet wird, um anzugeben, ob linker/rechter Bumper auf einem Gamepad die Navigation auf oberster Ebene Kategorien von Ihrer app navigieren.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-292">Keep the default value on the [ShoulderNavigationEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.PanePostion) property, which is used to indicate if left/right bumpers on a gamepad navigate the top-level navigation categories of your app.</span></span> <span data-ttu-id="5d5e0-293">Der Standardwert ist "WhenSelectionFollowsFocus".</span><span class="sxs-lookup"><span data-stu-id="5d5e0-293">The default is "WhenSelectionFollowsFocus".</span></span> <span data-ttu-id="5d5e0-294">Die andere mögliche Werte sind "Immer" und "Nie".</span><span class="sxs-lookup"><span data-stu-id="5d5e0-294">The other possible values are "Always" and "Never".</span></span>

<span data-ttu-id="5d5e0-295">Es wird veranschaulicht, wie die Rückwärtsnavigation mit Schaltfläche "zurück" der NavigationView implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-295">We also demonstrate how to implement backwards navigation with NavigationView's back button.</span></span>

<span data-ttu-id="5d5e0-296">Hier sehen Sie eine Aufzeichnung der Zweck des Beispiels:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-296">Here's a recording of what the sample demonstrates:</span></span>

![NavigationView-End-To-End-Beispiel](images/nav-code-example.gif)

<span data-ttu-id="5d5e0-298">Hier ist der Beispielcode:</span><span class="sxs-lookup"><span data-stu-id="5d5e0-298">Here's the sample code:</span></span>

> [!NOTE]
> <span data-ttu-id="5d5e0-299">Wenn Sie die [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, Sie müssen einen Verweis auf das Toolkit hinzufügen: `xmlns:controls="using:Microsoft.UI.Xaml.Controls"`.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-299">If you're using the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/), then you'll need to add a reference to the toolkit: `xmlns:controls="using:Microsoft.UI.Xaml.Controls"`.</span></span>

```xaml
<Page
    x:Class="NavigationViewSample.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:NavigationViewSample"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup>
                <VisualState>
                    <VisualState.StateTriggers>
                        <AdaptiveTrigger MinWindowWidth="{x:Bind NavView.CompactModeThresholdWidth}" />
                    </VisualState.StateTriggers>

                    <VisualState.Setters>
                        <Setter Target="NavView.PaneDisplayMode" Value="Top"/>
                    </VisualState.Setters>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        <NavigationView x:Name="NavView"
                    SelectionFollowsFocus="Enabled"
                    ItemInvoked="NavView_ItemInvoked"
                    IsSettingsVisible="True"
                    Loaded="NavView_Loaded"
                    BackRequested="NavView_BackRequested"
                    Header="Welcome">

            <NavigationView.MenuItems>
                <NavigationViewItem Content="Home" x:Name="home" Tag="home">
                    <NavigationViewItem.Icon>
                        <FontIcon Glyph="&#xE10F;"/>
                    </NavigationViewItem.Icon>
                </NavigationViewItem>
                <NavigationViewItemSeparator/>
                <NavigationViewItemHeader Content="Main pages"/>
                <NavigationViewItem Icon="AllApps" Content="Apps" x:Name="apps" Tag="apps"/>
                <NavigationViewItem Icon="Video" Content="Games" x:Name="games" Tag="games"/>
                <NavigationViewItem Icon="Audio" Content="Music" x:Name="music" Tag="music"/>
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

            <Frame x:Name="ContentFrame" Margin="24"/>

        </NavigationView>
    </Grid>
</Page>
```

> [!NOTE]
> <span data-ttu-id="5d5e0-300">Wenn Sie die [Windows-UI-Bibliothek](https://docs.microsoft.com/uwp/toolkits/winui/)verwenden, Sie müssen einen Verweis auf das Toolkit hinzufügen: `using MUXC = Microsoft.UI.Xaml.Controls;`.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-300">If you're using the [Windows UI Library](https://docs.microsoft.com/uwp/toolkits/winui/), then you'll need to add a reference to the toolkit: `using MUXC = Microsoft.UI.Xaml.Controls;`.</span></span>

```csharp
private Type currentPage;

// List of ValueTuple holding the Navigation Tag and the relative Navigation Page 
private readonly IList<(string Tag, Type Page)> _pages = new List<(string Tag, Type Page)>
{
    ("home", typeof(HomePage)),
    ("apps", typeof(AppsPage)),
    ("games", typeof(GamesPage)),
    ("music", typeof(MusicPage)),
};

private void NavView_Loaded(object sender, RoutedEventArgs e)
{
    // You can also add items in code behind
    NavView.MenuItems.Add(new NavigationViewItemSeparator());
    NavView.MenuItems.Add(new NavigationViewItem
    {
        Content = "My content",
        Icon = new SymbolIcon(Symbol.Folder),
        Tag = "content"
    });
    _pages.Add(("content", typeof(MyContentPage)));

    ContentFrame.Navigated += On_Navigated;

    // NavView doesn't load any page by default: you need to specify it
    NavView_Navigate("home");

    // Add keyboard accelerators for backwards navigation
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

private void NavView_ItemInvoked(NavigationView sender, NavigationViewItemInvokedEventArgs args)
{
    if (args.InvokedItem == null)
        return;

    if (args.IsSettingsInvoked)
        ContentFrame.Navigate(typeof(SettingsPage));
    else
    {
        // Getting the Tag from Content (args.InvokedItem is the content of NavigationViewItem)
        var navItemTag = NavView.MenuItems
            .OfType<NavigationViewItem>()
            .First(i => args.InvokedItem.Equals(i.Content))
            .Tag.ToString();

        NavView_Navigate(navItemTag);
    }
}

private void NavView_Navigate(string navItemTag)
{
    var item = _pages.First(p => p.Tag.Equals(navItemTag));
    if (currentPage == item.Page)
          return;
    ContentFrame.Navigate(item.Page);

    currentPage = item.Page;
}

private void NavView_BackRequested(NavigationView sender, NavigationViewBackRequestedEventArgs args) => On_BackRequested();

private void BackInvoked(KeyboardAccelerator sender, KeyboardAcceleratorInvokedEventArgs args)
{
    On_BackRequested();
    args.Handled = true;
}

private bool On_BackRequested()
{
    if (!ContentFrame.CanGoBack)
        return false;

    // Don't go back if the nav pane is overlayed
    if (NavView.IsPaneOpen &&
        (NavView.DisplayMode == NavigationViewDisplayMode.Compact ||
        NavView.DisplayMode == NavigationViewDisplayMode.Minimal))
        return false;

    ContentFrame.GoBack();
    return true;
}

private void On_Navigated(object sender, NavigationEventArgs e)
{
    NavView.IsBackEnabled = ContentFrame.CanGoBack;

    if (ContentFrame.SourcePageType == typeof(SettingsPage))
    {
        // SettingsItem is not part of NavView.MenuItems, and doesn't have a Tag
        NavView.SelectedItem = (NavigationViewItem)NavView.SettingsItem;
    }
    else
    {
        var item = _pages.First(p => p.Page == e.SourcePageType);

        NavView.SelectedItem = NavView.MenuItems
            .OfType<NavigationViewItem>()
            .First(n => n.Tag.Equals(item.Tag));
    }
}
```

## <a name="customizing-backgrounds"></a><span data-ttu-id="5d5e0-301">Anpassen von Hintergründen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-301">Customizing backgrounds</span></span>

<span data-ttu-id="5d5e0-302">Legen Sie zum Ändern des Hintergrunds des Hauptbereichs von NavigationView seine `Background`-Eigenschaft auf Ihren bevorzugten Pinsel.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-302">To change the background of NavigationView's main area, set its `Background` property to your preferred brush.</span></span>

<span data-ttu-id="5d5e0-303">Der Hintergrund des Bereichs zeigt in-app-Acryl, wenn sich NavigationView im Vordergrund, minimale oder kompakten Modus befindet.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-303">The Pane's background shows in-app acrylic when NavigationView is in Top, Minimal, or Compact mode.</span></span> <span data-ttu-id="5d5e0-304">Um dieses Verhalten zu aktualisieren oder die Darstellung des Acrylbereichs anzupassen, ändern Sie die zwei Designressourcen durch Überschreiben Ihrer App.xaml.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-304">To update this behavior or customize the appearance of your Pane's acrylic, modify the two theme resources by overwriting them in your App.xaml.</span></span>

```xaml
<Application.Resources>
    <ResourceDictionary>
        <AcrylicBrush x:Key="NavigationViewDefaultPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewTopPaneBackground"
        BackgroundSource="Backdrop" TintColor="Yellow" TintOpacity=".6"/>
        <AcrylicBrush x:Key="NavigationViewExpandedPaneBackground"
        BackgroundSource="HostBackdrop" TintColor="Orange" TintOpacity=".8"/>
    </ResourceDictionary>
</Application.Resources>
```

## <a name="scroll-content-under-top-pane"></a><span data-ttu-id="5d5e0-305">Scrollen Sie Inhalte unter oberen Bereich</span><span class="sxs-lookup"><span data-stu-id="5d5e0-305">Scroll content under top pane</span></span>

<span data-ttu-id="5d5e0-306">Für eine nahtlose aussehen + Gefühl empfohlen Wenn Ihre app hat Seiten, die eine ScrollViewer verwenden und im Navigationsbereich oben positioniert, müssen den Bildlauf unterhalb der oberen Navigationsbereich.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-306">For a seamless look+feel, if your app has pages that use a ScrollViewer and your navigation pane is top positioned, we recommend having the content scroll underneath the top nav pane.</span></span> <span data-ttu-id="5d5e0-307">Dies bietet eine Sticky Header Art von Verhalten der App.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-307">This gives a Sticky Header kind of behaviour to the app.</span></span>

<span data-ttu-id="5d5e0-308">Dies kann erfolgen, indem Sie die [CanContentRenderOutsideBounds](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer.cancontentrenderoutsidebounds) -Eigenschaft auf den entsprechenden ScrollViewer auf "true".</span><span class="sxs-lookup"><span data-stu-id="5d5e0-308">This can be achieved by setting the [CanContentRenderOutsideBounds](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer.cancontentrenderoutsidebounds) property on the relevant ScrollViewer to true.</span></span>

![Navview Scroll Navigationsbereich](images/nav-scroll-content.png)

<span data-ttu-id="5d5e0-310">Wenn Ihre app sehr lange Bildlauf in Inhalten, empfiehlt es sich, einbinden sticky Header, die an der oberen Navigationsbereich anhängen und bilden eine glatte Oberfläche zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-310">If your app has very long scrolling content, you may want to consider incorporating sticky headers that attach to the top nav pane and form a smooth surface.</span></span> 

![Navview Scroll sticky header](images/nav-scroll-stickyheader.png)

<span data-ttu-id="5d5e0-312">Sie können dies erreichen, indem Sie die [ContentOverlay](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) -Eigenschaft auf NavigationView.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-312">You can achieve this by setting the [ContentOverlay](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) property on NavigationView.</span></span> 

<span data-ttu-id="5d5e0-313">In einigen Fällen, wenn der Benutzer nach unten Bildläufe ist, können Sie den Navigationsbereich erreicht, indem Sie die [IsPaneVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) -Eigenschaft auf NavigationView auf "false" ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="5d5e0-313">Sometimes, if the user is scrolling down, you may want to hide the nav pane, achieved by setting the [IsPaneVisible](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview.ContentOverlay) property on NavigationView to false.</span></span>

![Navview Scroll ausblenden nav](images/nav-scroll-hidepane.png)

## <a name="related-topics"></a><span data-ttu-id="5d5e0-315">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-315">Related topics</span></span>

- [<span data-ttu-id="5d5e0-316">NavigationView-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d5e0-316">NavigationView class</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.navigationview)
- [<span data-ttu-id="5d5e0-317">Master/Details</span><span class="sxs-lookup"><span data-stu-id="5d5e0-317">Master/details</span></span>](master-details.md)
- [<span data-ttu-id="5d5e0-318">Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="5d5e0-318">Pivot control</span></span>](tabs-pivot.md)
- [<span data-ttu-id="5d5e0-319">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="5d5e0-319">Navigation basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="5d5e0-320">Übersicht über Fluent Design für UWP</span><span class="sxs-lookup"><span data-stu-id="5d5e0-320">Fluent Design for UWP overview</span></span>](../fluent-design-system/index.md)
