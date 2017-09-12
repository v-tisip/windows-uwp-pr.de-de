---
author: Jwmsft
title: Geteilte Darstellung
ms.assetid: E9E4537F-1160-4183-9A83-26602FCFDC9A
description: "Ein Steuerelement für die geteilte Ansicht verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich."
label: Split view
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
ms.openlocfilehash: 126fab3db9a0728626289788757f576648a43856
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="split-view-control"></a><span data-ttu-id="86e84-104">Steuerelement für geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="86e84-104">Split view control</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="86e84-105">Ein Steuerelement für die geteilte Darstellung verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="86e84-105">A split view control has an expandable/collapsible pane and a content area.</span></span>

> <span data-ttu-id="86e84-106">**Wichtige APIs**: [SplitView-Klasse](https://msdn.microsoft.com/library/windows/apps/dn864360)</span><span class="sxs-lookup"><span data-stu-id="86e84-106">**Important APIs**: [SplitView class](https://msdn.microsoft.com/library/windows/apps/dn864360)</span></span>

<span data-ttu-id="86e84-107">Dies ist ein Beispiel für die Verwendung von SplitView durch die Microsoft Edge-App, um den Hub anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="86e84-107">Here is an example of the Microsoft Edge app using SplitView to show its Hub.</span></span>

![Beispiel für die geteilte Ansicht in Microsoft Edge](images/split_view_Edge.png)


 <span data-ttu-id="86e84-109">Der Inhaltsbereich einer geteilten Ansicht wird stets angezeigt.</span><span class="sxs-lookup"><span data-stu-id="86e84-109">A split view's content area is always visible.</span></span> <span data-ttu-id="86e84-110">Der Bereich kann erweitert und reduziert werden oder geöffnet bleiben. Er kann vom linken oder rechten Rand eines App-Fensters aus eingeblendet werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-110">The pane can expand and collapse or remain in an open state, and can present itself from either the left side or right side of an app window.</span></span> <span data-ttu-id="86e84-111">Der Bereich verfügt über vier Modi:</span><span class="sxs-lookup"><span data-stu-id="86e84-111">The pane has four modes:</span></span>

-   **<span data-ttu-id="86e84-112">Überlagerung</span><span class="sxs-lookup"><span data-stu-id="86e84-112">Overlay</span></span>**

    <span data-ttu-id="86e84-113">Der Bereich ist ausgeblendet, bis er geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="86e84-113">The pane is hidden until opened.</span></span> <span data-ttu-id="86e84-114">Ist der Bereich geöffnet, überlagert er den Inhaltsbereich.</span><span class="sxs-lookup"><span data-stu-id="86e84-114">When open, the pane overlays the content area.</span></span>

-   **<span data-ttu-id="86e84-115">Inline</span><span class="sxs-lookup"><span data-stu-id="86e84-115">Inline</span></span>**

    <span data-ttu-id="86e84-116">Der Bereich ist immer sichtbar und überlagert den Inhaltsbereich nicht.</span><span class="sxs-lookup"><span data-stu-id="86e84-116">The pane is always visible and doesn't overlay the content area.</span></span> <span data-ttu-id="86e84-117">Der Bereich und der Inhaltsbereich teilen sich die verfügbare Bildschirmfläche.</span><span class="sxs-lookup"><span data-stu-id="86e84-117">The pane and content areas divide the available screen real estate.</span></span>

-   **<span data-ttu-id="86e84-118">CompactOverlay</span><span class="sxs-lookup"><span data-stu-id="86e84-118">CompactOverlay</span></span>**

    <span data-ttu-id="86e84-119">Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="86e84-119">A narrow portion of the pane is always visible in this mode, which is just wide enough to show icons.</span></span> <span data-ttu-id="86e84-120">Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-120">The default closed pane width is 48px, which can be modified with `CompactPaneLength`.</span></span> <span data-ttu-id="86e84-121">Wenn das Fenster geöffnet ist, wird den Inhaltsbereich überlagert werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-121">If the pane is opened, it will overlay the content area.</span></span>

-   **<span data-ttu-id="86e84-122">CompactInline</span><span class="sxs-lookup"><span data-stu-id="86e84-122">CompactInline</span></span>**

    <span data-ttu-id="86e84-123">Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="86e84-123">A narrow portion of the pane is always visible in this mode, which is just wide enough to show icons.</span></span> <span data-ttu-id="86e84-124">Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-124">The default closed pane width is 48px, which can be modified with `CompactPaneLength`.</span></span> <span data-ttu-id="86e84-125">Wenn das Fenster geöffnet ist, reduziert es den Platz für Inhalte, die weggeschoben werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-125">If the pane is opened, it will reduce the space available for content, pushing the content out of its way.</span></span>

## <a name="is-this-the-right-control"></a><span data-ttu-id="86e84-126">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="86e84-126">Is this the right control?</span></span>

<span data-ttu-id="86e84-127">Das Steuerelement für die geteilte Darstellung kann zum Erstellen eines [Navigationsbereichs](navigationview.md) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="86e84-127">The split view control can be used to make a [navigation pane](navigationview.md).</span></span> <span data-ttu-id="86e84-128">Zum Erstellen dieses Musters fügen Sie eine Schaltfläche zum Erweitern/Reduzieren (die „Hamburger“-Schaltfläche) sowie eine Listenansicht mit den Navigationselementen hinzu.</span><span class="sxs-lookup"><span data-stu-id="86e84-128">To build this pattern, add an expand/collapse button (the "hamburger" button) and a list view representing the nav items.</span></span>

<span data-ttu-id="86e84-129">Das Steuerelement für die geteilte Ansicht kann auch für eine Drawer-Ansicht verwendet werden, in der Benutzer den ergänzenden Bereich öffnen und schließen können.</span><span class="sxs-lookup"><span data-stu-id="86e84-129">The split view control can also be used to create any "drawer" experience where users can open and close the supplemental pane.</span></span>

## <a name="create-a-split-view"></a><span data-ttu-id="86e84-130">Erstellen einer geteilten Ansicht</span><span class="sxs-lookup"><span data-stu-id="86e84-130">Create a split view</span></span>

<span data-ttu-id="86e84-131">Dies ist ein SplitView-Steuerelement mit einem offenen Bereich, der inline neben dem Inhaltsbereich angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="86e84-131">Here's a SplitView control with an open Pane appearing inline next to the Content.</span></span>
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



## <a name="related-topics"></a><span data-ttu-id="86e84-132">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="86e84-132">Related topics</span></span>
* [<span data-ttu-id="86e84-133">Navigationsbereichsmuster</span><span class="sxs-lookup"><span data-stu-id="86e84-133">Nav pane pattern</span></span>](navigationview.md)
* [<span data-ttu-id="86e84-134">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="86e84-134">List view</span></span>](lists.md)
 

 
