---
author: QuinnRadich
Description: Navigation in Universal Windows Platform (UWP) apps is based on a flexible model of navigation structures, navigation elements, and system-level features.
title: Navigationsgrundlagen für UWP-Apps
ms.assetid: B65D33BA-AAFE-434D-B6D5-1A0C49F59664
label: Navigation design basics
template: detail.hbs
op-migration-status: ready
ms.author: quradic
ms.date: 7/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b731910f53a6152554b74e946374234b827f4a86
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3825470"
---
# <a name="navigation-design-basics-for-uwp-apps"></a><span data-ttu-id="c5bfb-103">Navigationsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="c5bfb-103">Navigation design basics for UWP apps</span></span>

![Navigationsgrundlagen-Header](images/nav/navigation-basics-header.jpg)

<span data-ttu-id="c5bfb-105">Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-105">If you think of an app as a collection of pages, *navigation* describes the act of moving between pages and within a page.</span></span> <span data-ttu-id="c5bfb-106">Die Navigation ist der Ausgangspunkt für die Benutzererfahrung und definiert die Art und Weise, in der Nutzer die Inhalte und Funktionen finden, an denen sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-106">It's the starting point of the user experience, and it's how users find the content and features they're interested in.</span></span> <span data-ttu-id="c5bfb-107">Sie ist sehr wichtig, und es kann schwierig sein, sie richtig zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-107">It's very important, and it can be difficult to get right.</span></span>

<span data-ttu-id="c5bfb-108">Es gibt eine große Anzahl von Navigationsmöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-108">We have a huge number of choices to make for navigation.</span></span> <span data-ttu-id="c5bfb-109">Wir könnten:</span><span class="sxs-lookup"><span data-stu-id="c5bfb-109">We could:</span></span>

:::row:::
    :::column:::
        ![navigationsbeispiel 1](images/nav/nav-1.svg)

        Require users to go through a series of pages in order.
    :::column-end:::
    :::column:::
        ![navigation example 2](images/nav/nav-2.svg)

        Provide a menu that allows users to jump directly to any page.
    :::column-end:::
    :::column:::
        ![navigation example 3](images/nav/nav-3.svg)

        Place everything on a single page and provide filtering mechanisms for viewing content.
    :::column-end:::
:::row-end:::

<span data-ttu-id="c5bfb-111">Es gibt zwar kein einheitliches Navigationsdesign, das für jede App funktioniert, aber es gibt Prinzipien und Richtlinien, die Ihnen helfen, das richtige Design für Ihre App zu finden.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-111">While there's no single navigation design that works for every app, there are principles and guidelines to help you decide the right design for your app.</span></span>

## <a name="principles-of-good-navigation"></a><span data-ttu-id="c5bfb-112">Grundsätze guter Navigation</span><span class="sxs-lookup"><span data-stu-id="c5bfb-112">Principles of good navigation</span></span>

<span data-ttu-id="c5bfb-113">Beginnen wir mit den Grundprinzipien eines guten Navigationsdesigns:</span><span class="sxs-lookup"><span data-stu-id="c5bfb-113">Let's start with the basic principles of good navigation design:</span></span>

- <span data-ttu-id="c5bfb-114">**Konsistenz:** Erfüllen Sie die Erwartungen der Anwender.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-114">**Consistency:** Meet user expectations.</span></span>
- <span data-ttu-id="c5bfb-115">**Einfachheit:** Nicht mehr als notwendig.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-115">**Simplicity:** Don't do more than you need to.</span></span>
- <span data-ttu-id="c5bfb-116">**Klarheit:** Bieten Sie klare Wege und Optionen.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-116">**Clarity:** Provide clear paths and options.</span></span>

### <a name="consistency"></a><span data-ttu-id="c5bfb-117">Konsistenz</span><span class="sxs-lookup"><span data-stu-id="c5bfb-117">Consistency</span></span>

<span data-ttu-id="c5bfb-118">Die Navigation sollte den Erwartungen der Benutzer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-118">Navigation should be consistent with user expectations.</span></span> <span data-ttu-id="c5bfb-119">Verwenden [Standardsteuerelemente](#use-the-right-controls) , dass der Benutzer mit vertraut sind und folgenden Standardkonventionen für Symbole, nehmen Position und Formatierung Navigation vorhersehbar und intuitiv für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-119">Using [standard controls](#use-the-right-controls) that users are familiar with and following standard conventions for icons, location, and styling will make navigation predictable and intuitive for users.</span></span>

![Bild mit Seitenkomponenten](images/nav/page-components.svg)

> <span data-ttu-id="c5bfb-121">Benutzer erwarten einige UI-Elemente an Standardpositionen.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-121">Users expect to find certain UI elements in standard locations.</span></span>

### <a name="simplicity"></a><span data-ttu-id="c5bfb-122">Einfachheit</span><span class="sxs-lookup"><span data-stu-id="c5bfb-122">Simplicity</span></span>

<span data-ttu-id="c5bfb-123">Weniger Navigationselemente erleichtern den Anwendern die Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-123">Fewer navigation items simplify decision making for users.</span></span> <span data-ttu-id="c5bfb-124">Der einfache Zugriff auf wichtige Ziele und das Ausblenden weniger wichtiger Objekte hilft den Benutzern, schneller dorthin zu gelangen, wohin sie wollen.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-124">Providing easy access to important destinations and hiding less important items will help users get where they want, faster.</span></span>

:::row:::
    :::column:::
        ![Beispiel für „Richtig”](images/nav/do.svg)

        ![navview good](images/nav/navview-good.svg)

        Present navigation items in a familiar navigation menu.
    :::column-end:::
    :::column:::
        ![don't example](images/nav/dont.svg)

        ![navview bad](images/nav/navview-bad.svg)

        Overwhelm users with many navigation options.
    :::column-end:::
:::row-end:::

### <a name="clarity"></a><span data-ttu-id="c5bfb-126">Klarheit</span><span class="sxs-lookup"><span data-stu-id="c5bfb-126">Clarity</span></span>

<span data-ttu-id="c5bfb-127">Klare Pfade ermöglichen eine logische Navigation für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-127">Clear paths allow for logical navigation for users.</span></span> <span data-ttu-id="c5bfb-128">Navigationsmöglichkeiten sichtbar zu machen und Zusammenhänge zwischen den Seiten zu klären, soll verhindern, dass sich die Benutzer „verirren”.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-128">Making navigation options obvious and clarifying relationships between pages should prevent users from getting lost.</span></span>

![Beispiel für „Richtig”](images/nav/clarity-image.svg)

> <span data-ttu-id="c5bfb-130">Die Ziele sind klar gekennzeichnet, so dass die Benutzer wissen, wo sie sich befinden.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-130">Destinations are clearly labeled so users know where they are.</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="c5bfb-131">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="c5bfb-131">General recommendations</span></span>

<span data-ttu-id="c5bfb-132">Nehmen wir nun unsere Gestaltungsprinzipien – Konsistenz, Einfachheit und Klarheit – und verwenden wir sie, um einige allgemeine Empfehlungen zu formulieren.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-132">Now, let's take our design principles--consistency, simplicity, and clarity--and use them to come up with some general recommendations.</span></span>

1. <span data-ttu-id="c5bfb-133">Denken Sie an Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-133">Think about your users.</span></span> <span data-ttu-id="c5bfb-134">Verfolgen Sie typische Pfade, die sie durch Ihre App nehmen könnten, und überlegen Sie für jede Seite, warum der Benutzer dort ist und wohin er gehen möchte.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-134">Trace out typical paths they might take through your app, and for each page, think about why the user is there and where they might want to go.</span></span>

2. <span data-ttu-id="c5bfb-135">Vermeiden Sie Tiefe Navigationshierarchien.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-135">Avoid deep navigation hierarchies.</span></span> <span data-ttu-id="c5bfb-136">Wenn Sie über drei Navigationsebenen hinausgehen, riskieren Sie, Ihren Benutzer in einer tiefen Hierarchie zu verlieren, die er nur schwer verlassen kann.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-136">If you go beyond three levels of navigation, you risk stranding your user in a deep hierarchy that they will have difficulty leaving.</span></span>

3. <span data-ttu-id="c5bfb-137">Vermeiden Sie „Pogo Sticking”.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-137">Avoid "pogo-sticking."</span></span> <span data-ttu-id="c5bfb-138">Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-138">Pogo-sticking occurs when there is related content, but navigating to it requires the user to go up a level and then down again.</span></span>

## <a name="use-the-right-structure"></a><span data-ttu-id="c5bfb-139">Verwenden Sie die richtige Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="c5bfb-139">Use the right structure</span></span>

<span data-ttu-id="c5bfb-140">Nun, da Sie mit den allgemeinen Navigationsprinzipien vertraut sind, überlegen wir uns die Strukturierung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-140">Now that you're familiar with general navigation principles, how should you structure your app?</span></span> <span data-ttu-id="c5bfb-141">Es gibt zwei allgemeine Strukturen: Flache und hierarchische.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-141">There are two general structures: flat and hierarchal.</span></span>

:::row:::
    :::column:::
        ![In einer flachen Struktur angeordnete Seiten](images/nav/flat-lateral-structure.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-143">::: Column Span = "2":::</span><span class="sxs-lookup"><span data-stu-id="c5bfb-143">:::column span="2":::</span></span>
        ### Flat/lateral

        In a flat/lateral structure, pages exist side-by-side. You can go from one page to another in any order.

        We recommend using a flat structure when:

        - The pages can be viewed in any order.
        - The pages are clearly distinct from each other and don't have an obvious parent/child relationship.
        - There are less than 8 pages in the group. <br>
        (When there are more pages, it might be difficult for users to understand how the pages are unique or to understand their current location within the group. If you don't think that's an issue for your app, go ahead and make the pages peers. Otherwise, consider using a hierarchical structure to break the pages into two or more smaller groups.)

    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![In einer Hierarchie angeordnete Seiten](images/nav/hierarchical-structure.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-145">::: Column Span = "2":::</span><span class="sxs-lookup"><span data-stu-id="c5bfb-145">:::column span="2":::</span></span>
        ### Hierarchical

        In a hierarchical structure, pages are organized into a tree-like structure. Each child page has one parent, but a parent can have one or more child pages. To reach a child page, you travel through the parent.

        Hierarchical structures are good for organizing complex content that spans lots of pages. The downside is some navigation overhead: the deeper the structure, the more clicks it takes to get from page to page.

        We recommend a hierarchical structure when:
        
        - Pages should be traversed in a specific order.
        - There is a clear parent-child relationship between pages.
        - There are more than 7 pages in the group.
        
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![App mit einer Hybridstruktur](images/nav/combining-structures.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-147">::: Column Span = "2":::</span><span class="sxs-lookup"><span data-stu-id="c5bfb-147">:::column span="2":::</span></span>
        ### Combining structures

        You don't have choose to one structure or the other; many well-design apps use both. An app can use flat structures for top-level pages that can be viewed in any order, and hierarchical structures for pages that have more complex relationships.

        If your navigation structure has multiple levels, we recommend that peer-to-peer navigation elements only link to the peers within their current subtree. Consider the adjacent illustration, which shows a navigation structure that has two levels:

        - At level 1, the peer-to-peer navigation element should provide access to pages A, B, C, and D.
        - At level 2, the peer-to-peer navigation elements for the A2 pages should only link to the other A2 pages. They should not link to level 2 pages in the C subtree.
    :::column-end:::
:::row-end:::

## <a name="use-the-right-controls"></a><span data-ttu-id="c5bfb-148">Verwenden der richtigen Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c5bfb-148">Use the right controls</span></span>

<span data-ttu-id="c5bfb-149">Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-149">Once you've decided on a page structure, you need to decide how users navigate through those pages.</span></span> <span data-ttu-id="c5bfb-150">UWP bietet eine Vielzahl von Navigationssteuerelementen, um ein konsistentes und zuverlässiges Navigationserlebnis in Ihrer App zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-150">UWP provides a variety of navigation controls to help ensure a consistent, reliable navigation experience in your app.</span></span>

:::row:::
    :::column:::
        ![Frame-Bild](images/nav/thumbnail-frame.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-152">::: Column Span = "2"::: [ **Frame**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Frame)</span><span class="sxs-lookup"><span data-stu-id="c5bfb-152">:::column span="2"::: [**Frame**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Frame)</span></span>

        With few exceptions, any app that has multiple pages uses a frame. Typically, an app has a main page that contains the frame and a primary navigation element, such as a navigation view control. When the user selects a page, the frame loads and displays it.
:::row-end:::

:::row:::
    :::column:::
        ![Bild für Registerkarten und pivot](images/nav/thumbnail-tabs-pivot.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-154">::: Column Span = "2"::: [ **oberen Navigationsleiste und Registerkarten**](../controls-and-patterns/navigationview.md)</span><span class="sxs-lookup"><span data-stu-id="c5bfb-154">:::column span="2"::: [**Top navigation and tabs**](../controls-and-patterns/navigationview.md)</span></span>

        Displays a horizontal list of links to pages at the same level. The [NavigationView](../controls-and-patterns/navigationview.md) control implements the top navigation and tabs patterns.
        
        Use top navigation when:

        - You want to show all navigation options on the screen.
        - You desire more space for your app's content.
        - Icons cannot clearly describe your navigation categories.
        
        Use tabs when:

        - You want to preserve navigation history and page state.
        - You expect users to switch between tabs frequently.

:::row-end:::

:::row:::
    :::column:::
        ![Navview Bild](images/nav/thumbnail-navview.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-156">::: Column Span = "2"::: [ **linken Navigationsbereich**](../controls-and-patterns/navigationview.md)</span><span class="sxs-lookup"><span data-stu-id="c5bfb-156">:::column span="2"::: [**Left navigation**](../controls-and-patterns/navigationview.md)</span></span>

        Displays a vertical list of links to top-level pages. Use when:
        
        - The pages exist at the top level.
        - There are many navigation items (more than 5)
        - You don't expect users to switch between pages frequently.
        
:::row-end:::

:::row:::
    :::column:::
        ![Master / Details-Bild](images/nav/thumbnail-master-detail.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-158">::: Column Span = "2"::: [ **Master/Details**](../controls-and-patterns/master-details.md)</span><span class="sxs-lookup"><span data-stu-id="c5bfb-158">:::column span="2"::: [**Master/details**](../controls-and-patterns/master-details.md)</span></span>

        Displays a list (master view) of items. Selecting an item displays its corresponding page in the details section. Use when:
        
        - You expect users to switch between child items frequently.
        - You want to enable the user to perform high-level operations, such as deleting or sorting, on individual items or groups of items, and also want to enable the user to view or update the details for each item.

        Master/details is well suited for email inboxes, contact lists, and data entry.
:::row-end:::

:::row:::
    :::column:::
        ![Bild für Hyperlinks und Schaltflächen](images/nav/thumbnail-hyperlinks-buttons.svg)
    :::column-end:::
    <span data-ttu-id="c5bfb-160">::: Column Span = "2"::: [ **Hyperlinks**](../controls-and-patterns/hyperlinks.md)</span><span class="sxs-lookup"><span data-stu-id="c5bfb-160">:::column span="2"::: [**Hyperlinks**](../controls-and-patterns/hyperlinks.md)</span></span>

        Embedded navigation elements can appear in a page's content. Unlike other navigation elements, which should be consistent across the pages, content-embedded navigation elements are unique from page to page.
:::row-end:::

## <a name="next-add-navigation-code-to-your-app"></a><span data-ttu-id="c5bfb-161">Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c5bfb-161">Next: Add navigation code to your app</span></span>

<span data-ttu-id="c5bfb-162">Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), lernen Sie den Code kennen, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation zwischen zwei Seiten in Ihrer App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="c5bfb-162">The next article, [Implement basic navigation](navigate-between-two-pages.md), shows the code required to use a Frame control to enable basic navigation between two pages in your app.</span></span>