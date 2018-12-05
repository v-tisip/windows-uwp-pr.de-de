---
title: Geteilte Darstellung
ms.assetid: E9E4537F-1160-4183-9A83-26602FCFDC9A
description: Ein Steuerelement für die geteilte Ansicht verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich.
label: Split view
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: yulikl
design-contact: kimsea
dev-contact: tpaine
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 826b408135b85b1903ce345c480015797b814255
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8758330"
---
# <a name="split-view-control"></a><span data-ttu-id="c06c2-104">Steuerelement für geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="c06c2-104">Split view control</span></span>

<span data-ttu-id="c06c2-105">Ein Steuerelement für die geteilte Darstellung verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="c06c2-105">A split view control has an expandable/collapsible pane and a content area.</span></span>

> <span data-ttu-id="c06c2-106">**Wichtige APIs**: [SplitView-Klasse](https://msdn.microsoft.com/library/windows/apps/dn864360)</span><span class="sxs-lookup"><span data-stu-id="c06c2-106">**Important APIs**: [SplitView class](https://msdn.microsoft.com/library/windows/apps/dn864360)</span></span>

<span data-ttu-id="c06c2-107">Dies ist ein Beispiel für die Verwendung von SplitView durch die Microsoft Edge-App, um den Hub anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c06c2-107">Here is an example of the Microsoft Edge app using SplitView to show its Hub.</span></span>

![Beispiel für die geteilte Ansicht in Microsoft Edge](images/split_view_Edge.png)


 <span data-ttu-id="c06c2-109">Der Inhaltsbereich einer geteilten Ansicht wird stets angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c06c2-109">A split view's content area is always visible.</span></span> <span data-ttu-id="c06c2-110">Der Bereich kann erweitert und reduziert werden oder geöffnet bleiben. Er kann vom linken oder rechten Rand eines App-Fensters aus eingeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="c06c2-110">The pane can expand and collapse or remain in an open state, and can present itself from either the left side or right side of an app window.</span></span> <span data-ttu-id="c06c2-111">Der Bereich verfügt über vier Modi:</span><span class="sxs-lookup"><span data-stu-id="c06c2-111">The pane has four modes:</span></span>

-   **<span data-ttu-id="c06c2-112">Überlagerung</span><span class="sxs-lookup"><span data-stu-id="c06c2-112">Overlay</span></span>**

    <span data-ttu-id="c06c2-113">Der Bereich ist ausgeblendet, bis er geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="c06c2-113">The pane is hidden until opened.</span></span> <span data-ttu-id="c06c2-114">Ist der Bereich geöffnet, überlagert er den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="c06c2-114">When open, the pane overlays the content area.</span></span>

-   **<span data-ttu-id="c06c2-115">Inline</span><span class="sxs-lookup"><span data-stu-id="c06c2-115">Inline</span></span>**

    <span data-ttu-id="c06c2-116">Der Bereich ist immer sichtbar und überlagert den Inhaltsbereich nicht.</span><span class="sxs-lookup"><span data-stu-id="c06c2-116">The pane is always visible and doesn't overlay the content area.</span></span> <span data-ttu-id="c06c2-117">Der Bereich und der Inhaltsbereich teilen sich die verfügbare Bildschirmfläche.</span><span class="sxs-lookup"><span data-stu-id="c06c2-117">The pane and content areas divide the available screen real estate.</span></span>

-   **<span data-ttu-id="c06c2-118">CompactOverlay</span><span class="sxs-lookup"><span data-stu-id="c06c2-118">CompactOverlay</span></span>**

    <span data-ttu-id="c06c2-119">Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c06c2-119">A narrow portion of the pane is always visible in this mode, which is just wide enough to show icons.</span></span> <span data-ttu-id="c06c2-120">Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden.</span><span class="sxs-lookup"><span data-stu-id="c06c2-120">The default closed pane width is 48px, which can be modified with `CompactPaneLength`.</span></span> <span data-ttu-id="c06c2-121">Wenn das Fenster geöffnet ist, wird den Inhaltsbereich überlagert werden.</span><span class="sxs-lookup"><span data-stu-id="c06c2-121">If the pane is opened, it will overlay the content area.</span></span>

-   **<span data-ttu-id="c06c2-122">CompactInline</span><span class="sxs-lookup"><span data-stu-id="c06c2-122">CompactInline</span></span>**

    <span data-ttu-id="c06c2-123">Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="c06c2-123">A narrow portion of the pane is always visible in this mode, which is just wide enough to show icons.</span></span> <span data-ttu-id="c06c2-124">Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden.</span><span class="sxs-lookup"><span data-stu-id="c06c2-124">The default closed pane width is 48px, which can be modified with `CompactPaneLength`.</span></span> <span data-ttu-id="c06c2-125">Wenn das Fenster geöffnet ist, reduziert es den Platz für Inhalte, die weggeschoben werden.</span><span class="sxs-lookup"><span data-stu-id="c06c2-125">If the pane is opened, it will reduce the space available for content, pushing the content out of its way.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="c06c2-126">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="c06c2-126">Is this the right control?</span></span>

<span data-ttu-id="c06c2-127">Das Steuerelement für die geteilte Ansicht kann für eine Drawer-Ansicht verwendet werden, in der Benutzer den ergänzenden Bereich öffnen und schließen können.</span><span class="sxs-lookup"><span data-stu-id="c06c2-127">The split view control can be used to create any "drawer" experience where users can open and close the supplemental pane.</span></span> <span data-ttu-id="c06c2-128">Sie können z.B. SplitView verwenden, um das [Master/Details-](master-details.md)-Muster zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c06c2-128">For example, you can use SplitView to build the [master/details](master-details.md) pattern.</span></span>

<span data-ttu-id="c06c2-129">Wenn Sie ein Navigationsmenü mit einer Schaltfläche zum Erweitern/Reduzieren und eine Liste mit Navigationselementen erstellen möchten, verwenden Sie das [NavigationView](navigationview.md)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="c06c2-129">If you'd like to build a navigation menu with an expand/collapse button and a list of navigation items, then use the [NavigationView](navigationview.md) control.</span></span>

## <a name="examples"></a><span data-ttu-id="c06c2-130">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c06c2-130">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="c06c2-131">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="c06c2-131">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="c06c2-132">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/SplitView">die App zu öffnen und SplitView in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="c06c2-132">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/SplitView">open the app and see the SplitView in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="c06c2-133">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="c06c2-133">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="c06c2-134">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c06c2-134">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="create-a-split-view"></a><span data-ttu-id="c06c2-135">Erstellen einer geteilten Ansicht</span><span class="sxs-lookup"><span data-stu-id="c06c2-135">Create a split view</span></span>

<span data-ttu-id="c06c2-136">Dies ist ein SplitView-Steuerelement mit einem offenen Bereich, der inline neben dem Inhaltsbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c06c2-136">Here's a SplitView control with an open Pane appearing inline next to the Content.</span></span>
```xaml
<SplitView IsPaneOpen="True"
           DisplayMode="Inline"
           OpenPaneLength="296">
    <SplitView.Pane>
        <TextBlock Text="Pane"
                   FontSize="24"
                   VerticalAlignment="Center"
                   HorizontalAlignment="Center"/>
    </SplitView.Pane>

    <Grid>
        <TextBlock Text="Content"
                   FontSize="24"
                   VerticalAlignment="Center"
                   HorizontalAlignment="Center"/>
    </Grid>
</SplitView>
```

## <a name="get-the-sample-code"></a><span data-ttu-id="c06c2-137">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="c06c2-137">Get the sample code</span></span>

- <span data-ttu-id="c06c2-138">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c06c2-138">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c06c2-139">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c06c2-139">Related topics</span></span>
- [<span data-ttu-id="c06c2-140">Navigationsbereichsmuster</span><span class="sxs-lookup"><span data-stu-id="c06c2-140">Nav pane pattern</span></span>](navigationview.md)
- [<span data-ttu-id="c06c2-141">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="c06c2-141">List view</span></span>](lists.md)
- [<span data-ttu-id="c06c2-142">Master/Details</span><span class="sxs-lookup"><span data-stu-id="c06c2-142">Master/details</span></span>](master-details.md)