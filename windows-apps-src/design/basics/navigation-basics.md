---
author: serenaz
Description: Navigation in Universal Windows Platform (UWP) apps is based on a flexible model of navigation structures, navigation elements, and system-level features.
title: Navigationsgrundlagen für UWP-Apps
ms.assetid: B65D33BA-AAFE-434D-B6D5-1A0C49F59664
label: Navigation design basics
template: detail.hbs
op-migration-status: ready
ms.author: sezhen
ms.date: 11/27/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3edb7dc28561b5d316a908df951e3052eafc995b
ms.sourcegitcommit: 0ab8f6fac53a6811f977ddc24de039c46c9db0ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
ms.locfileid: "1654269"
---
# <a name="navigation-design-basics-for-uwp-apps"></a><span data-ttu-id="4ad7f-103">Navigationsdesigngrundlagen für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="4ad7f-103">Navigation design basics for UWP apps</span></span>

<span data-ttu-id="4ad7f-104">Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-104">If you think of an app as a collection of pages, *navigation* describes the act of moving between pages and within a page.</span></span> <span data-ttu-id="4ad7f-105">Sie ist der Ausgangspunkt der Benutzererfahrung, und es ist, wie Benutzer die Inhalte und Funktionen finden, die sie interessieren.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-105">It's the starting point of the user experience, and it's how users find the content and features they're interested in.</span></span> <span data-ttu-id="4ad7f-106">Sie ist sehr wichtig, und es kann schwierig sein, sie richtig einzustellen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-106">It's very important, and it can be difficult to get right.</span></span>

<span data-ttu-id="4ad7f-107">Es ist schwierig, weil wir als App-Designer eine Vielzahl von Entscheidungen treffen müssen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-107">It's difficult because as app designers, we have a huge number of choices to make.</span></span> <span data-ttu-id="4ad7f-108">Wir könnten vorgeben, dass der Benutzer eine Reihe von Seiten in der Reihenfolge durchläuft.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-108">We could require the user to go through a series of pages in order.</span></span> <span data-ttu-id="4ad7f-109">Oder wir könnten ein Menü anbieten, das es dem Benutzer erlaubt, direkt zu einer beliebigen Seite zu springen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-109">Or we could provide a menu that allows users to jump directly to any page.</span></span> <span data-ttu-id="4ad7f-110">Oder wir platzieren alle Elemente auf einer Seite und bieten Filtermechanismen zum Anzeigen der Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-110">Or we could put everything on a single page and provide filtering mechanisms for viewing content.</span></span>
 
<span data-ttu-id="4ad7f-111">Es gibt zwar kein einheitliches Navigationsdesign, das für jede App funktioniert, aber es gibt Prinzipien und Richtlinien, die Ihnen helfen, das richtige Design für Ihre App zu finden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-111">While there's no single navigation design that works for every app, there are principles and guidelines to help you decide the right design for your app.</span></span> 

<figure class="wdg-figure">
  <img alt="Navigation diagram for an app" src="images/navigation_diagram.png" />
  <figcaption><span data-ttu-id="4ad7f-112">Diagramm der Navigation einer App.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-112">Diagram of an app's navigation.</span></span></figcaption>
</figure> 

## <a name="principles-of-good-navigation"></a><span data-ttu-id="4ad7f-113">Grundsätze guter Navigation</span><span class="sxs-lookup"><span data-stu-id="4ad7f-113">Principles of good navigation</span></span>
<span data-ttu-id="4ad7f-114">Beginnen wir mit den Grundprinzipien eines guten Navigationsdesigns:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-114">Let's start with the basic principles of good navigation design:</span></span> 

* <span data-ttu-id="4ad7f-115">Konsistenz: Erfüllen Sie die Erwartungen der Anwender.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-115">Consistency: Meet user expectations.</span></span>
* <span data-ttu-id="4ad7f-116">Einfachheit: Nicht mehr als notwendig.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-116">Simplicity: Don't do more than you need to.</span></span>
* <span data-ttu-id="4ad7f-117">Klarheit: Bieten Sie klare Wege und Optionen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-117">Clarity: Provide clear paths and options.</span></span>

### <a name="consistency"></a><span data-ttu-id="4ad7f-118">Konsistenz</span><span class="sxs-lookup"><span data-stu-id="4ad7f-118">Consistency</span></span>
<span data-ttu-id="4ad7f-119">Die Navigation sollte den Erwartungen der Benutzer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-119">Navigation should be consistent with user expectations.</span></span> <span data-ttu-id="4ad7f-120">Die Verwendung von [Standardsteuerelementen](#use-the-right-controls), mit denen die Benutzer vertraut sind, und der Einhaltung von Standardkonventionen für Symbole, Position und Stil wird die Navigation für die Benutzer vorhersehbar und intuitiv.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-120">Using [standard controls](#use-the-right-controls) that users are familiar with and following standard conventions for icons, location, and styling will make navigation predictable and intuative for users.</span></span>

<figure class="wdg-figure">
<img src="images/nav/nav-component-layout.png" alt="Preferred location for navigation elements"/>
  <figcaption><span data-ttu-id="4ad7f-121">Benutzer erwarten, gewisse UI-Elemente an Standardorten zu finden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-121">Users expect to find certain UI elements in standard locations.</span></span></figcaption>
</figure> 

### <a name="simplicity"></a><span data-ttu-id="4ad7f-122">Einfachheit</span><span class="sxs-lookup"><span data-stu-id="4ad7f-122">Simplicity</span></span>
<span data-ttu-id="4ad7f-123">Weniger Navigationselemente erleichtern den Anwendern die Entscheidungsfindung.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-123">Fewer navigation items simplify decision making for users.</span></span> <span data-ttu-id="4ad7f-124">Der einfache Zugriff auf wichtige Ziele und das Ausblenden weniger wichtiger Objekte hilft den Benutzern, schneller dorthin zu gelangen, wo sie wollen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-124">Providing easy access to important destinations and hiding less important items will help users get where they want, faster.</span></span>

<figure class="wdg-figure">
<img src="images/nav/nav-simple-menus.png" alt="A simple versus a complex menu"/>
  <figcaption> <span data-ttu-id="4ad7f-125">Das Menü auf der linken Seite ist das Verständnis und die Nutzung für Benutzer einfacher, da es weniger Elemente gibt.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-125">The menu on the left will be easier for users to understand and utilize because there are less items.</span></span>
</figcaption>
</figure> 

### <a name="clarity"></a><span data-ttu-id="4ad7f-126">Klarheit</span><span class="sxs-lookup"><span data-stu-id="4ad7f-126">Clarity</span></span>
<span data-ttu-id="4ad7f-127">Klare Pfade ermöglichen eine logische Navigation für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-127">Clear paths allow for logical navigation for users.</span></span> <span data-ttu-id="4ad7f-128">Navigationsmöglichkeiten sichtbar zu machen und Zusammenhänge zwischen den Seiten zu klären, soll verhindern, dass sich die Benutzer „verirren”.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-128">Making navigation options obvious and clarifying relationships between pages should prevent users from getting lost.</span></span>

<figure class="wdg-figure">
<img src="images/nav/nav-pages.png" alt="Clear paths and destinations"/>
  <figcaption> <span data-ttu-id="4ad7f-129">Die Ziele sind klar gekennzeichnet, so dass die Benutzer wissen, wo sie sich befinden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-129">Destinations are clearly labeled so users know where they are.</span></span>
</figcaption>
</figure> 

## <a name="general-recommendations"></a><span data-ttu-id="4ad7f-130">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="4ad7f-130">General recommendations</span></span>
<span data-ttu-id="4ad7f-131">Nehmen wir nun unsere Gestaltungsprinzipien – Konsistenz, Einfachheit und Klarheit – und verwenden wir sie, um einige allgemeine Empfehlungen zu formulieren.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-131">Now, let's take our design principles--consistency, simplicity, and clarity--and use them to come up with some general recommendations.</span></span>

1. <span data-ttu-id="4ad7f-132">Denken Sie an Ihre Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-132">Think about your users.</span></span> <span data-ttu-id="4ad7f-133">Verfolgen Sie typische Pfade, die sie durch Ihre App nehmen könnten, und überlegen Sie für jede Seite, warum der Benutzer dort ist und wohin er gehen möchte.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-133">Trace out typical paths they might take through your app, and for each page, think about why the user is there and where they might want to go.</span></span> 

2. <span data-ttu-id="4ad7f-134">Vermeiden Sie tiefe Navigationshierarchien.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-134">Avoid deep navigational hierarchies.</span></span> <span data-ttu-id="4ad7f-135">Wenn Sie über drei Navigationsebenen hinausgehen, riskieren Sie, Ihren Benutzer in einer tiefen Hierarchie zu verlieren, die er nur schwer verlassen kann.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-135">If you go beyond three levels of navigation, you risk stranding your user in a deep hierarchy that they will have difficulty leaving.</span></span>

3. <span data-ttu-id="4ad7f-136">Vermeiden Sie „Pogo Sticking”.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-136">Avoid "pogo-sticking."</span></span> <span data-ttu-id="4ad7f-137">Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-137">Pogo-sticking occurs when there is related content, but navigating to it requires the user to go up a level and then down again.</span></span>

## <a name="use-the-right-structure"></a><span data-ttu-id="4ad7f-138">Verwenden Sie die richtige Navigationsstruktur</span><span class="sxs-lookup"><span data-stu-id="4ad7f-138">Use the right structure</span></span> 
<span data-ttu-id="4ad7f-139">Nun, da Sie mit den allgemeinen Navigationsprinzipien vertraut sind, überlegen wir uns die Strukturierung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-139">Now that you're familiar with general navigation principles, how should you structure your app?</span></span> <span data-ttu-id="4ad7f-140">Es gibt zwei allgemeine Strukturen: flache und hierarchische.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-140">There are two general structures: flat and hierarchal.</span></span> 

### <a name="flatlateral"></a><span data-ttu-id="4ad7f-141">Flach/lateral</span><span class="sxs-lookup"><span data-stu-id="4ad7f-141">Flat/lateral</span></span>
![In einer flachen Struktur angeordnete Seiten](images/nav/nav-pages-peer.png)

<span data-ttu-id="4ad7f-143">In einer flachen/lateralen Struktur stehen die Seiten parallel zueinander.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-143">In a flat/lateral structure, pages exist side-by-side.</span></span> <span data-ttu-id="4ad7f-144">Sie können in beliebiger Reihenfolge von einer Seite zur nächsten wechseln.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-144">You can go from on page to another in any order.</span></span> 

<span data-ttu-id="4ad7f-145">Wir empfehlen die Verwendung einer flachen Struktur bei:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-145">We recommend using a flat structure when:</span></span> 
<ul>
<li><span data-ttu-id="4ad7f-146">Die Seiten können in beliebiger Reihenfolge angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-146">The pages can be viewed in any order.</span></span></li>
<li><span data-ttu-id="4ad7f-147">Die Seiten sind deutlich voneinander abgegrenzt und verfügen nicht über eine offensichtliche Beziehung zwischen über- und untergeordneten Elementen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-147">The pages are clearly distinct from each other and don't have an obvious parent/child relationship.</span></span></li>
<li><span data-ttu-id="4ad7f-148">Es gibt weniger als acht Seiten in der Gruppe.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-148">There are fewer than 8 pages in the group.</span></span><br/>
<span data-ttu-id="4ad7f-149">(Wenn eine Gruppe mehr Seiten enthält, wird es für Benutzer möglicherweise schwierig, zu verstehen, inwiefern sich die Seiten unterscheiden oder welche Position sie zurzeit in der Gruppe haben.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-149">(When there are more pages, it might be difficult for users to understand how the pages are unique or to understand their current location within the group.</span></span> <span data-ttu-id="4ad7f-150">Wenn Sie davon ausgehen, dass dies kein Problem für Ihre App ist, machen Sie aus den Seiten Peers.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-150">If you don't think that's an issue for your app, go ahead and make the pages peers.</span></span> <span data-ttu-id="4ad7f-151">Ziehen Sie andernfalls eine hierarchische Struktur in Betracht, um die Seiten in zwei oder mehr kleinere Gruppen zu unterteilen.)</span><span class="sxs-lookup"><span data-stu-id="4ad7f-151">Otherwise, consider using a hierarchical structure to break the pages into two or more smaller groups.)</span></span></li>
</ul>

### <a name="hierarchical"></a><span data-ttu-id="4ad7f-152">Hierarchisch</span><span class="sxs-lookup"><span data-stu-id="4ad7f-152">Hierarchical</span></span>
![In einer Hierarchie angeordnete Seiten](images/nav/nav-pages-hiearchy.png)

<span data-ttu-id="4ad7f-154">In einer hierarchischen Struktur werden Seiten in einer Baumstruktur organisiert.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-154">In a hierarchical structure, pages are organized into a tree-like structure.</span></span> <span data-ttu-id="4ad7f-155">Jede untergeordnete Seite hat ein übergeordnetes Element. Ein übergeordnetes Element kann jedoch eine oder mehrere untergeordnete Seiten haben.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-155">Each child page has one parent, but a parent can have one or more child pages.</span></span> <span data-ttu-id="4ad7f-156">Um eine untergeordnete Seite aufzurufen, durchlaufen Sie das übergeordnete Element.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-156">To reach a child page, you travel through the parent.</span></span>

<span data-ttu-id="4ad7f-157">Hierarchische Strukturen sind gut geeignet, um komplexe Inhalte, die sich über viele Seiten erstrecken, zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-157">Hierarchical structures are good for organizing complex content that spans lots of pages.</span></span> <span data-ttu-id="4ad7f-158">Der Nachteil besteht darin, dass hierarchische Seiten Navigationsmehraufwand verursachen: je tiefer die Struktur, desto mehr Klicks sind für das Wechseln der Seiten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-158">The downside is some navigation overhead: the deeper the structure, the more clicks it takes to get from page to page.</span></span> 

<span data-ttu-id="4ad7f-159">Wir empfehlen eine hierarchische Struktur bei:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-159">We recommend a hiearchical structure when:</span></span> 
<ul>
<li><span data-ttu-id="4ad7f-160">Seiten, die in einer bestimmten Reihenfolge durchlaufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-160">Pages should be traversed in a specific order.</span></span></li>
<li><span data-ttu-id="4ad7f-161">Es gibt eine klare Beziehung zwischen übergeordneten und untergeordneten Seiten.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-161">There is a clear parent-child relationship between pages.</span></span></li>
<li><span data-ttu-id="4ad7f-162">In der Gruppe gibt es mehr als 7 Seiten.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-162">There are more than 7 pages in the group.</span></span></li>
</ul>

### <a name="combining-structures"></a><span data-ttu-id="4ad7f-163">Kombinieren von Strukturen</span><span class="sxs-lookup"><span data-stu-id="4ad7f-163">Combining structures</span></span>
![App mit einer Hybridstruktur](images/nav/nav-hybridstructure.png.png)

<span data-ttu-id="4ad7f-165">Sie haben müssen nicht die eine oder andere Struktur wählen; viele durchdachte Apps verwenden beide Strukturen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-165">You don't have choose one structure or the other; many well-design apps use both.</span></span> <span data-ttu-id="4ad7f-166">Eine App verwendet flache Strukturen für Seiten auf obersten Ebenen, die in beliebiger Reihenfolge angezeigt werden können, und hierarchische Strukturen für Seiten, die komplexere Beziehungen haben.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-166">An app can use flat structures for top-level pages that can be viewed in any order, and hierarchical structures for pages that have more complex relationships.</span></span> 

<span data-ttu-id="4ad7f-167">Wenn die Navigationsstruktur über mehrere Ebenen verfügt, empfehlen wir, dass Peer-to-Peer-Navigationselemente nur mit den Peers innerhalb der aktuellen Unterstruktur verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-167">If your navigation structure has multiple levels, we recommend that peer-to-peer navigation elements only link to the peers within their current subtree.</span></span> <span data-ttu-id="4ad7f-168">Beachten Sie die folgende Abbildung, die eine Navigationsstruktur mit drei Ebenen zeigt:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-168">Consider the following illustration, which shows a navigation structure that has three levels:</span></span>

![App mit zwei Unterstrukturen](images/nav/nav-subtrees.png)
- <span data-ttu-id="4ad7f-170">Auf Ebene 1 sollte das Peer-to-Peer-Navigationselement Zugriff auf die Seiten A, B, C und D ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-170">At level 1, the peer-to-peer navigation element should provide access to pages A, B, C, and D.</span></span>
- <span data-ttu-id="4ad7f-171">Auf Ebene 2 sollten die Peer-to-Peer Navigationselemente für die A2-Seiten nur mit den anderen A2-Seiten verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-171">At level 2, the peer-to-peer navigation elements for the A2 pages should only link to the other A2 pages.</span></span> <span data-ttu-id="4ad7f-172">Sie sollten nicht mit Seiten auf Ebene 2 in der C-Unterstruktur verknüpft sein.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-172">They should not link to level 2 pages in the C subtree.</span></span>

![App mit zwei Unterstrukturen](images/nav/nav-subtrees2.png)

## <a name="use-the-right-controls"></a><span data-ttu-id="4ad7f-174">Verwenden Sie die richtigen Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="4ad7f-174">Use the right controls</span></span>
<span data-ttu-id="4ad7f-175">Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-175">Once you've decided on a page structure, you need to decide how users navigate through those pages.</span></span> <span data-ttu-id="4ad7f-176">UWP bietet eine Vielzahl von Navigationssteuerelementen, um ein konsistentes und zuverlässiges Navigationserlebnis in Ihrer App zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-176">UWP provides a variety of navigation controls to help ensure a consistent, reliable navigation experience in your app.</span></span> 

<span data-ttu-id="4ad7f-177">Wir empfehlen die Auswahl eines Navigationssteuerelements anhand der Anzahl der Navigationselemente in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-177">We recommend selecting a navigation control based on the number of navigation elements in your app.</span></span> <span data-ttu-id="4ad7f-178">Wenn Sie fünf oder weniger Navigationselemente haben, dann verwenden Sie die Einstiegsnavigation (z. B. [Registerkarten und Pivot](../controls-and-patterns/tabs-pivot.md)).</span><span class="sxs-lookup"><span data-stu-id="4ad7f-178">If you have five or less navigation items, then use top-level navigation, like [tabs and pivot](../controls-and-patterns/tabs-pivot.md).</span></span> <span data-ttu-id="4ad7f-179">Wenn Sie sechs oder mehr Navigationspunkte haben, dann verwenden Sie die linke Navigation, wie z. B. die [Navigationsansicht](../controls-and-patterns/navigationview.md) oder [Master/Details](../controls-and-patterns/master-details.md).</span><span class="sxs-lookup"><span data-stu-id="4ad7f-179">If you have six or more navigation items, then use left navigation, like [navigation view](../controls-and-patterns/navigationview.md) or [master/details](../controls-and-patterns/master-details.md).</span></span>

<div class="mx-responsive-img">

<table>
<tr>
    <th><span data-ttu-id="4ad7f-180">Steuerelement</span><span class="sxs-lookup"><span data-stu-id="4ad7f-180">Control</span></span></th>
    <th><span data-ttu-id="4ad7f-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4ad7f-181">Description</span></span></th>
</tr>
<tr>
    <td><a href="https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.Frame"><span data-ttu-id="4ad7f-182">Frame</span><span class="sxs-lookup"><span data-stu-id="4ad7f-182">Frame</span></span></a><br/><br/>
    <img src="images/frame.png" alt="Frame" /></td>
    <td><span data-ttu-id="4ad7f-183">Zeigt Seiten an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-183">Displays pages.</span></span> <p><span data-ttu-id="4ad7f-184">Mit wenigen Ausnahmen verwendet jede App mit mehrere Seiten den Frame.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-184">With few exceptions, any app that has multiple pages uses a frame.</span></span> <span data-ttu-id="4ad7f-185">In einem typischen Szenario hat die App eine Hauptseite, die den Frame und ein primäres Navigationselement beinhaltet, z.B. ein Navigationssteuerelement.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-185">Typically, an app has a main page that contains the frame and a primary navigation element, such as a navigation view control.</span></span> <span data-ttu-id="4ad7f-186">Wählt der Benutzer eine Seite, wird sie durch den Frame geladen und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-186">When the user selects a page, the frame loads and displays it.</span></span></p></td>
</tr>
<tr>
    <td><a href="../controls-and-patterns/tabs-pivot.md"><span data-ttu-id="4ad7f-187">Registerkarten und Pivot</span><span class="sxs-lookup"><span data-stu-id="4ad7f-187">Tabs and pivot</span></span></a><br/><br/>
    <img src="images/nav/nav-tabs-sm-300.png" alt="Tab-based navigation" /></td>
    <td><span data-ttu-id="4ad7f-188">Zeigt eine horizontale Liste mit Links zu Seiten auf derselben Ebene an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-188">Displays a horizontal list of links to pages at the same level.</span></span>
<p><span data-ttu-id="4ad7f-189">Zu verwenden in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-189">Use when:</span></span></p>
<ul>
<li><span data-ttu-id="4ad7f-190">Es sind 2 bis 5 Seiten vorhanden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-190">There are 2-5 pages.</span></span> <span data-ttu-id="4ad7f-191">(Sie können Registerkarten/Pivots bei mehr als fünf Seiten verwenden, es kann aber schwierig sein, alle Registerkarten/Pivots auf dem Bildschirm anzuzeigen.)</span><span class="sxs-lookup"><span data-stu-id="4ad7f-191">(You can use tabs/pivots when there are more than 5 pages, but it might be difficult to fit all the tabs/pivots on the screen.)</span></span></li>
<li><span data-ttu-id="4ad7f-192">Sie erwarten, dass Benutzer häufig zwischen Seiten wechseln werden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-192">You expect users to switch between pages frequently.</span></span></li>
</ul></td>
</tr>
<tr>
    <td><a href="../controls-and-patterns/navigationview.md"><span data-ttu-id="4ad7f-193">Navigationsansicht</span><span class="sxs-lookup"><span data-stu-id="4ad7f-193">Navigation view</span></span></a><br/><br/>
    <img src="images/nav/nav-navpane-4page-thumb.png" alt="A navigation pane" /></td>
    <td><span data-ttu-id="4ad7f-194">Zeigt eine vertikale Liste mit Links zu den übergeordneten Seiten an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-194">Displays a vertical list of links to top-level pages.</span></span>
<p><span data-ttu-id="4ad7f-195">Zu verwenden in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-195">Use when:</span></span></p>
<ul>
<li><span data-ttu-id="4ad7f-196">Die Seiten befinden sich auf der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-196">The pages exist at the top level.</span></span></li>
<li><span data-ttu-id="4ad7f-197">Es gibt viele Navigationselemente (mehr als 5).</span><span class="sxs-lookup"><span data-stu-id="4ad7f-197">There are many navigational items (more than 5).</span></span></li>
<li><span data-ttu-id="4ad7f-198">Sie erwarten nicht, dass Benutzer häufig zwischen Seiten wechseln werden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-198">You don't expect users to switch between pages frequently.</span></span></li>

</ul></td>
</tr>
<tr>
<td><a href="../controls-and-patterns/master-details.md"><span data-ttu-id="4ad7f-199">Master/Details</span><span class="sxs-lookup"><span data-stu-id="4ad7f-199">Master/details</span></span></a><br/><br/>
<img src="images/higsecone-masterdetail-thumb.png" alt="Master/details" /></td>
<td><span data-ttu-id="4ad7f-200">Zeigt eine Liste (Masteransicht) der Elemente an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-200">Displays a list (master view) of items.</span></span> <span data-ttu-id="4ad7f-201">Durch Auswahl eines Elements wird die entsprechende Seite im Detailbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-201">Selecting an item displays its corresponding page in the details section.</span></span>
<p><span data-ttu-id="4ad7f-202">Zu verwenden in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-202">Use when:</span></span></p>
<ul>
<li><span data-ttu-id="4ad7f-203">Sie erwarten, dass Benutzer häufig zwischen untergeordneten Elementen wechseln werden.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-203">You expect users to switch between child items frequently.</span></span></li>
<li><span data-ttu-id="4ad7f-204">Sie möchten es dem Benutzer ermöglichen, Vorgänge auf hoher Ebene, z. B. Löschen oder Sortieren, für einzelne Elemente oder Gruppen von Elementen durchzuführen, und Sie möchten es dem Benutzer ermöglichen, Details für jedes Element anzuzeigen oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-204">You want to enable the user to perform high-level operations, such as deleting or sorting, on individual items or groups of items, and also want to enable the user to view or update the details for each item.</span></span></li>
</ul>
<p><span data-ttu-id="4ad7f-205">Master/Details eignet sich gut für E-Mail-Posteingänge, Kontaktlisten und die Dateneingabe.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-205">Master/details is well suited for email inboxes, contact lists, and data entry.</span></span></p>
</td>
<tr>
<td><a href="../controls-and-patterns/hub.md"><span data-ttu-id="4ad7f-206">Hub</span><span class="sxs-lookup"><span data-stu-id="4ad7f-206">Hub</span></span></a><br/><br/>
<img src="images/hub.png" alt="Hub" /></td>
<td> <span data-ttu-id="4ad7f-207">Zeigt Abschnitte von bestellten Artikeln in Rastern an.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-207">Displays sections of ordered items in grids.</span></span> 
<p><span data-ttu-id="4ad7f-208">Zu verwenden in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="4ad7f-208">Use when:</span></span></p>
<ul>
<li><span data-ttu-id="4ad7f-209">Sie möchten eine visuelle Navigation mit Hero-Images erstellen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-209">You want to create visual navigation with hero images.</span></span></li>
</ul>
<p><span data-ttu-id="4ad7f-210">Hubs eignen sich gut zum Durchblättern, Ansehen oder Kaufen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-210">Hubs are well suited for browsing, viewing, or purchasing experiences.</span></span></p>
</td>
</tr>
<tr>
<td><span data-ttu-id="4ad7f-211"><a href="../controls-and-patterns/hyperlinks.md">Hyperlinks</a> und <a href="../controls-and-patterns/buttons.md">Schaltflächen</a></span><span class="sxs-lookup"><span data-stu-id="4ad7f-211"><a href="../controls-and-patterns/hyperlinks.md">Hyperlinks</a> and <a href="../controls-and-patterns/buttons.md">buttons</a></span></span></td>
<td> <span data-ttu-id="4ad7f-212">Eingebettete Navigationselemente können im Inhalt einer Seite erscheinen.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-212">Embedded navigation elements can appear in a page's content.</span></span> <span data-ttu-id="4ad7f-213">Im Gegensatz zu anderen Navigationselementen, die für alle Seiten konsistent sein sollten, sind im Inhalt eingebettete Navigationselemente auf jeder Seite einzigartig.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-213">Unlike other navigation elements, which should be consistent across the pages, content-embedded navigation elements are unique from page to page.</span></span></td>
</tr>
</table>
</div>

## <a name="next-add-navigation-code-to-your-app"></a><span data-ttu-id="4ad7f-214">Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="4ad7f-214">Next: Add navigation code to your app</span></span>
<span data-ttu-id="4ad7f-215">Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), erfahren Sie den Code, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation zwischen zwei Seiten in Ihrer App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="4ad7f-215">The next article, [Implement basic navigation](navigate-between-two-pages.md), shows the code required to use a Frame control to enable basic navigation between two pages in your app.</span></span> 