---
Description: Navigation in Universal Windows Platform (UWP) apps is based on a flexible model of navigation structures, navigation elements, and system-level features.
title: Navigationsgrundlagen für UWP-Apps
ms.assetid: B65D33BA-AAFE-434D-B6D5-1A0C49F59664
label: Navigation design basics
template: detail.hbs
op-migration-status: ready
ms.date: 7/16/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 4eb31ed1f802b8827c124958438ceb6c5902aee1
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8877979"
---
# <a name="navigation-design-basics-for-uwp-apps"></a><span data-ttu-id="9dec7-103">Navigationsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="9dec7-103">Navigation design basics for UWP apps</span></span>

![Navigationsgrundlagen-Header](images/nav/navigation-basics-header.jpg)

<span data-ttu-id="9dec7-105">Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite.</span><span class="sxs-lookup"><span data-stu-id="9dec7-105">If you think of an app as a collection of pages, *navigation* describes the act of moving between pages and within a page.</span></span> <span data-ttu-id="9dec7-106">Die Navigation ist der Ausgangspunkt für die Benutzererfahrung und definiert die Art und Weise, in der Nutzer die Inhalte und Funktionen finden, an denen sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="9dec7-106">It's the starting point of the user experience, and it's how users find the content and features they're interested in.</span></span> <span data-ttu-id="9dec7-107">Sie ist sehr wichtig, und es kann schwierig sein, sie richtig zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="9dec7-107">It's very important, and it can be difficult to get right.</span></span>

<span data-ttu-id="9dec7-108">Es gibt eine große Anzahl von Navigationsmöglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="9dec7-108">We have a huge number of choices to make for navigation.</span></span> <span data-ttu-id="9dec7-109">Wir könnten:</span><span class="sxs-lookup"><span data-stu-id="9dec7-109">We could:</span></span>

:::row:::
    :::column:::
        ![navigation example 1](images/nav/nav-1.svg)

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

<span data-ttu-id="9dec7-110">Es gibt zwar kein einheitliches Navigationsdesign, das für jede App funktioniert, aber es gibt Prinzipien und Richtlinien, die Ihnen helfen, das richtige Design für Ihre App zu finden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-110">While there's no single navigation design that works for every app, there are principles and guidelines to help you decide the right design for your app.</span></span>

## <a name="principles-of-good-navigation"></a><span data-ttu-id="9dec7-111">Grundsätze guter Navigation</span><span class="sxs-lookup"><span data-stu-id="9dec7-111">Principles of good navigation</span></span>

<span data-ttu-id="9dec7-112">Beginnen wir mit den Grundprinzipien eines guten Navigationsdesigns:</span><span class="sxs-lookup"><span data-stu-id="9dec7-112">Let's start with the basic principles of good navigation design:</span></span>

- <span data-ttu-id="9dec7-113">**Konsistenz:** Erfüllen Sie die Erwartungen der Anwender.</span><span class="sxs-lookup"><span data-stu-id="9dec7-113">**Consistency:** Meet user expectations.</span></span>
- <span data-ttu-id="9dec7-114">**Einfachheit:** Nicht mehr als notwendig.</span><span class="sxs-lookup"><span data-stu-id="9dec7-114">**Simplicity:** Don't do more than you need to.</span></span>
- <span data-ttu-id="9dec7-115">**Klarheit:** Bieten Sie klare Wege und Optionen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-115">**Clarity:** Provide clear paths and options.</span></span>

### <a name="consistency"></a><span data-ttu-id="9dec7-116">Konsistenz</span><span class="sxs-lookup"><span data-stu-id="9dec7-116">Consistency</span></span>

<span data-ttu-id="9dec7-117">Die Navigation sollte den Erwartungen der Benutzer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-117">Navigation should be consistent with user expectations.</span></span> <span data-ttu-id="9dec7-118">Verwenden [Standardsteuerelemente](#use-the-right-controls) , dass der Benutzer mit vertraut sind und die folgenden Standardkonventionen für Symbole, nehmen Position und Stil Navigation vorhersehbar und intuitiv für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9dec7-118">Using [standard controls](#use-the-right-controls) that users are familiar with and following standard conventions for icons, location, and styling will make navigation predictable and intuitive for users.</span></span>

![Bild mit Seitenkomponenten](images/nav/page-components.svg)

> <span data-ttu-id="9dec7-120">Benutzer erwarten einige UI-Elemente an Standardpositionen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-120">Users expect to find certain UI elements in standard locations.</span></span>

### <a name="simplicity"></a><span data-ttu-id="9dec7-121">Einfachheit</span><span class="sxs-lookup"><span data-stu-id="9dec7-121">Simplicity</span></span>

<span data-ttu-id="9dec7-122">Weniger Navigationselemente erleichtern den Anwendern die Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="9dec7-122">Fewer navigation items simplify decision making for users.</span></span> <span data-ttu-id="9dec7-123">Der einfache Zugriff auf wichtige Ziele und das Ausblenden weniger wichtiger Objekte hilft den Benutzern, schneller dorthin zu gelangen, wohin sie wollen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-123">Providing easy access to important destinations and hiding less important items will help users get where they want, faster.</span></span>

:::row:::
    :::column:::
        ![do example](images/nav/do.svg)

        ![navview good](images/nav/navview-good.svg)

        Present navigation items in a familiar navigation menu.
    :::column-end:::
    :::column:::
        ![don't example](images/nav/dont.svg)

        ![navview bad](images/nav/navview-bad.svg)

        Overwhelm users with many navigation options.
    :::column-end:::
:::row-end:::

### <a name="clarity"></a><span data-ttu-id="9dec7-124">Klarheit</span><span class="sxs-lookup"><span data-stu-id="9dec7-124">Clarity</span></span>

<span data-ttu-id="9dec7-125">Klare Pfade ermöglichen eine logische Navigation für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9dec7-125">Clear paths allow for logical navigation for users.</span></span> <span data-ttu-id="9dec7-126">Navigationsmöglichkeiten sichtbar zu machen und Zusammenhänge zwischen den Seiten zu klären, soll verhindern, dass sich die Benutzer „verirren”.</span><span class="sxs-lookup"><span data-stu-id="9dec7-126">Making navigation options obvious and clarifying relationships between pages should prevent users from getting lost.</span></span>

![Beispiel für „Richtig”](images/nav/clarity-image.svg)

> <span data-ttu-id="9dec7-128">Die Ziele sind klar gekennzeichnet, so dass die Benutzer wissen, wo sie sich befinden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-128">Destinations are clearly labeled so users know where they are.</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="9dec7-129">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="9dec7-129">General recommendations</span></span>

<span data-ttu-id="9dec7-130">Nehmen wir nun unsere Gestaltungsprinzipien – Konsistenz, Einfachheit und Klarheit – und verwenden wir sie, um einige allgemeine Empfehlungen zu formulieren.</span><span class="sxs-lookup"><span data-stu-id="9dec7-130">Now, let's take our design principles--consistency, simplicity, and clarity--and use them to come up with some general recommendations.</span></span>

1. <span data-ttu-id="9dec7-131">Denken Sie an Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9dec7-131">Think about your users.</span></span> <span data-ttu-id="9dec7-132">Verfolgen Sie typische Pfade, die sie durch Ihre App nehmen könnten, und überlegen Sie für jede Seite, warum der Benutzer dort ist und wohin er gehen möchte.</span><span class="sxs-lookup"><span data-stu-id="9dec7-132">Trace out typical paths they might take through your app, and for each page, think about why the user is there and where they might want to go.</span></span>

2. <span data-ttu-id="9dec7-133">Vermeiden Sie Tiefe Navigationshierarchien.</span><span class="sxs-lookup"><span data-stu-id="9dec7-133">Avoid deep navigation hierarchies.</span></span> <span data-ttu-id="9dec7-134">Wenn Sie über drei Navigationsebenen hinausgehen, riskieren Sie, Ihren Benutzer in einer tiefen Hierarchie zu verlieren, die er nur schwer verlassen kann.</span><span class="sxs-lookup"><span data-stu-id="9dec7-134">If you go beyond three levels of navigation, you risk stranding your user in a deep hierarchy that they will have difficulty leaving.</span></span>

3. <span data-ttu-id="9dec7-135">Vermeiden Sie „Pogo Sticking”.</span><span class="sxs-lookup"><span data-stu-id="9dec7-135">Avoid "pogo-sticking."</span></span> <span data-ttu-id="9dec7-136">Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss.</span><span class="sxs-lookup"><span data-stu-id="9dec7-136">Pogo-sticking occurs when there is related content, but navigating to it requires the user to go up a level and then down again.</span></span>

## <a name="use-the-right-structure"></a><span data-ttu-id="9dec7-137">Verwenden Sie die richtige Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="9dec7-137">Use the right structure</span></span>

<span data-ttu-id="9dec7-138">Nun, da Sie mit den allgemeinen Navigationsprinzipien vertraut sind, überlegen wir uns die Strukturierung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="9dec7-138">Now that you're familiar with general navigation principles, how should you structure your app?</span></span> <span data-ttu-id="9dec7-139">Es gibt zwei allgemeine Strukturen: Flache und hierarchische.</span><span class="sxs-lookup"><span data-stu-id="9dec7-139">There are two general structures: flat and hierarchal.</span></span>

:::row:::
    :::column:::
        ![Pages arranged in a flat structure](images/nav/flat-lateral-structure.svg)
    :::column-end:::
    :::column span="2":::
        ### Flat/lateral

        In a flat/lateral structure, pages exist side-by-side. You can go from one page to another in any order.

        We recommend using a flat structure when:

        - <span data-ttu-id="9dec7-140">Die Seiten können in beliebiger Reihenfolge angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-140">The pages can be viewed in any order.</span></span>
        - <span data-ttu-id="9dec7-141">Die Seiten sind deutlich voneinander abgegrenzt und verfügen nicht über eine offensichtliche Beziehung zwischen über- und untergeordneten Elementen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-141">The pages are clearly distinct from each other and don't have an obvious parent/child relationship.</span></span>
        - <span data-ttu-id="9dec7-142">Es gibt weniger als 8 Seiten in der Gruppe.</span><span class="sxs-lookup"><span data-stu-id="9dec7-142">There are less than 8 pages in the group.</span></span> <br>
        <span data-ttu-id="9dec7-143">(Wenn eine Gruppe mehr Seiten enthält, wird es für Benutzer möglicherweise schwierig, zu verstehen, inwiefern sich die Seiten unterscheiden oder welche Position sie zurzeit in der Gruppe haben.</span><span class="sxs-lookup"><span data-stu-id="9dec7-143">(When there are more pages, it might be difficult for users to understand how the pages are unique or to understand their current location within the group.</span></span> <span data-ttu-id="9dec7-144">Wenn Sie davon ausgehen, dass dies kein Problem für Ihre App ist, machen Sie aus den Seiten Peers.</span><span class="sxs-lookup"><span data-stu-id="9dec7-144">If you don't think that's an issue for your app, go ahead and make the pages peers.</span></span> <span data-ttu-id="9dec7-145">Ziehen Sie andernfalls eine hierarchische Struktur in Betracht, um die Seiten in zwei oder mehr kleinere Gruppen zu unterteilen.)</span><span class="sxs-lookup"><span data-stu-id="9dec7-145">Otherwise, consider using a hierarchical structure to break the pages into two or more smaller groups.)</span></span>

    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Pages arranged in a hierarchy](images/nav/hierarchical-structure.svg)
    :::column-end:::
    :::column span="2":::
        ### Hierarchical

        In a hierarchical structure, pages are organized into a tree-like structure. Each child page has one parent, but a parent can have one or more child pages. To reach a child page, you travel through the parent.

        Hierarchical structures are good for organizing complex content that spans lots of pages. The downside is some navigation overhead: the deeper the structure, the more clicks it takes to get from page to page.

        We recommend a hierarchical structure when:
        
        - <span data-ttu-id="9dec7-146">Seiten, die in einer bestimmten Reihenfolge durchlaufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-146">Pages should be traversed in a specific order.</span></span>
        - <span data-ttu-id="9dec7-147">Es gibt eine klare Beziehung zwischen übergeordneten und untergeordneten Seiten.</span><span class="sxs-lookup"><span data-stu-id="9dec7-147">There is a clear parent-child relationship between pages.</span></span>
        - <span data-ttu-id="9dec7-148">In der Gruppe gibt es mehr als 7 Seiten.</span><span class="sxs-lookup"><span data-stu-id="9dec7-148">There are more than 7 pages in the group.</span></span>
        
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![an app with a hybrid structure](images/nav/combining-structures.svg)
    :::column-end:::
    :::column span="2":::
        ### Combining structures

        You don't have choose to one structure or the other; many well-design apps use both. An app can use flat structures for top-level pages that can be viewed in any order, and hierarchical structures for pages that have more complex relationships.

        If your navigation structure has multiple levels, we recommend that peer-to-peer navigation elements only link to the peers within their current subtree. Consider the adjacent illustration, which shows a navigation structure that has two levels:

        - <span data-ttu-id="9dec7-149">Auf Ebene 1 sollte das Peer-to-Peer-Navigationselement Zugriff auf die Seiten A, B, C und D ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-149">At level 1, the peer-to-peer navigation element should provide access to pages A, B, C, and D.</span></span>
        - <span data-ttu-id="9dec7-150">Auf Ebene 2 sollten die Peer-to-Peer Navigationselemente für die A2-Seiten nur mit den anderen A2-Seiten verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-150">At level 2, the peer-to-peer navigation elements for the A2 pages should only link to the other A2 pages.</span></span> <span data-ttu-id="9dec7-151">Sie sollten nicht mit Seiten auf Ebene 2 in der C-Unterstruktur verknüpft sein.</span><span class="sxs-lookup"><span data-stu-id="9dec7-151">They should not link to level 2 pages in the C subtree.</span></span>
    :::column-end:::
:::row-end:::

## <a name="use-the-right-controls"></a><span data-ttu-id="9dec7-152">Verwenden der richtigen Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="9dec7-152">Use the right controls</span></span>

<span data-ttu-id="9dec7-153">Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll.</span><span class="sxs-lookup"><span data-stu-id="9dec7-153">Once you've decided on a page structure, you need to decide how users navigate through those pages.</span></span> <span data-ttu-id="9dec7-154">UWP bietet eine Vielzahl von Navigationssteuerelementen, um ein konsistentes und zuverlässiges Navigationserlebnis in Ihrer App zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="9dec7-154">UWP provides a variety of navigation controls to help ensure a consistent, reliable navigation experience in your app.</span></span>

:::row:::
    :::column:::
        ![Frame image](images/nav/thumbnail-frame.svg)
    :::column-end:::
    :::column span="2":::
        [**Frame**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Frame)

        With few exceptions, any app that has multiple pages uses a frame. Typically, an app has a main page that contains the frame and a primary navigation element, such as a navigation view control. When the user selects a page, the frame loads and displays it.
:::row-end:::

:::row:::
    :::column:::
        ![tabs and pivot image](images/nav/thumbnail-tabs-pivot.svg)
    :::column-end:::
    :::column span="2":::
        [**Top navigation and tabs**](../controls-and-patterns/navigationview.md)

        Displays a horizontal list of links to pages at the same level. The [NavigationView](../controls-and-patterns/navigationview.md) control implements the top navigation and tabs patterns.
        
        Use top navigation when:

        - <span data-ttu-id="9dec7-155">Möchten Sie alle Navigationsoptionen auf dem Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9dec7-155">You want to show all navigation options on the screen.</span></span>
        - <span data-ttu-id="9dec7-156">Sie möchten mehr Platz für den Inhalt Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="9dec7-156">You desire more space for your app's content.</span></span>
        - <span data-ttu-id="9dec7-157">Symbole können nicht die Navigationskategorien beschreiben.</span><span class="sxs-lookup"><span data-stu-id="9dec7-157">Icons cannot clearly describe your navigation categories.</span></span>
        
        <span data-ttu-id="9dec7-158">Verwendung Registerkarten, wenn:</span><span class="sxs-lookup"><span data-stu-id="9dec7-158">Use tabs when:</span></span>

        - <span data-ttu-id="9dec7-159">Navigation auf der Seite und Verlauf Zustand beibehalten werden soll.</span><span class="sxs-lookup"><span data-stu-id="9dec7-159">You want to preserve navigation history and page state.</span></span>
        - <span data-ttu-id="9dec7-160">Sie erwarten, dass Benutzer zwischen Registerkarten häufig zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="9dec7-160">You expect users to switch between tabs frequently.</span></span>

:::row-end:::

:::row:::
    :::column:::
        ![navview image](images/nav/thumbnail-navview.svg)
    :::column-end:::
    :::column span="2":::
        [**Left navigation**](../controls-and-patterns/navigationview.md)

        Displays a vertical list of links to top-level pages. Use when:
        
        - <span data-ttu-id="9dec7-161">Die Seiten befinden sich auf der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="9dec7-161">The pages exist at the top level.</span></span>
        - <span data-ttu-id="9dec7-162">Es gibt viele Navigationselemente (mehr als 5)</span><span class="sxs-lookup"><span data-stu-id="9dec7-162">There are many navigation items (more than 5)</span></span>
        - <span data-ttu-id="9dec7-163">Sie erwarten nicht, dass Benutzer häufig zwischen Seiten wechseln werden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-163">You don't expect users to switch between pages frequently.</span></span>
        
:::row-end:::

:::row:::
    :::column:::
        ![Master details image](images/nav/thumbnail-master-detail.svg)
    :::column-end:::
    :::column span="2":::
        [**Master/details**](../controls-and-patterns/master-details.md)

        Displays a list (master view) of items. Selecting an item displays its corresponding page in the details section. Use when:
        
        - <span data-ttu-id="9dec7-164">Sie erwarten, dass Benutzer häufig zwischen untergeordneten Elementen wechseln werden.</span><span class="sxs-lookup"><span data-stu-id="9dec7-164">You expect users to switch between child items frequently.</span></span>
        - <span data-ttu-id="9dec7-165">Sie möchten es dem Benutzer ermöglichen, Vorgänge auf hoher Ebene, z. B. Löschen oder Sortieren, für einzelne Elemente oder Gruppen von Elementen durchzuführen, und Sie möchten es dem Benutzer ermöglichen, Details für jedes Element anzuzeigen oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9dec7-165">You want to enable the user to perform high-level operations, such as deleting or sorting, on individual items or groups of items, and also want to enable the user to view or update the details for each item.</span></span>

        <span data-ttu-id="9dec7-166">Master/Details eignet sich gut für E-Mail-Posteingänge, Kontaktlisten und die Dateneingabe.</span><span class="sxs-lookup"><span data-stu-id="9dec7-166">Master/details is well suited for email inboxes, contact lists, and data entry.</span></span>
:::row-end:::

:::row:::
    :::column:::
        ![Hyperlinks and buttons image](images/nav/thumbnail-hyperlinks-buttons.svg)
    :::column-end:::
    :::column span="2":::
        [**Hyperlinks**](../controls-and-patterns/hyperlinks.md)

        Embedded navigation elements can appear in a page's content. Unlike other navigation elements, which should be consistent across the pages, content-embedded navigation elements are unique from page to page.
:::row-end:::

## <a name="next-add-navigation-code-to-your-app"></a><span data-ttu-id="9dec7-167">Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="9dec7-167">Next: Add navigation code to your app</span></span>

<span data-ttu-id="9dec7-168">Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), lernen Sie den Code kennen, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation zwischen zwei Seiten in Ihrer App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9dec7-168">The next article, [Implement basic navigation](navigate-between-two-pages.md), shows the code required to use a Frame control to enable basic navigation between two pages in your app.</span></span>
