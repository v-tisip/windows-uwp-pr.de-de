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
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3658715"
---
# <a name="navigation-design-basics-for-uwp-apps"></a>Navigationsdesigngrundlagen für UWP-Apps

![Navigationsgrundlagen-Header](images/nav/navigation-basics-header.jpg)

Wenn Sie sich eine App als eine Sammlung von Seiten vorstellen, beschreibt der Begriff *Navigation* den Wechselvorgang zwischen Seiten und innerhalb einer Seite. Die Navigation ist der Ausgangspunkt für die Benutzererfahrung und definiert die Art und Weise, in der Nutzer die Inhalte und Funktionen finden, an denen sie interessiert sind. Sie ist sehr wichtig, und es kann schwierig sein, sie richtig zu implementieren.

Es gibt eine große Anzahl von Navigationsmöglichkeiten. Wir könnten:

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

Es gibt zwar kein einheitliches Navigationsdesign, das für jede App funktioniert, aber es gibt Prinzipien und Richtlinien, die Ihnen helfen, das richtige Design für Ihre App zu finden.

## <a name="principles-of-good-navigation"></a>Grundsätze guter Navigation

Beginnen wir mit den Grundprinzipien eines guten Navigationsdesigns:

- **Konsistenz:** Erfüllen Sie die Erwartungen der Anwender.
- **Einfachheit:** Nicht mehr als notwendig.
- **Klarheit:** Bieten Sie klare Wege und Optionen.

### <a name="consistency"></a>Konsistenz

Die Navigation sollte den Erwartungen der Benutzer entsprechen. Verwenden [Standardsteuerelemente](#use-the-right-controls) , dass der Benutzer mit vertraut sind und folgenden Standardkonventionen für Symbole, nehmen Position und Formatierung Navigation vorhersehbar und intuitiv für Benutzer.

![Bild mit Seitenkomponenten](images/nav/page-components.svg)

> Benutzer erwarten einige UI-Elemente an Standardpositionen.

### <a name="simplicity"></a>Einfachheit

Weniger Navigationselemente erleichtern den Anwendern die Entscheidungsfindung. Der einfache Zugriff auf wichtige Ziele und das Ausblenden weniger wichtiger Objekte hilft den Benutzern, schneller dorthin zu gelangen, wohin sie wollen.

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

### <a name="clarity"></a>Klarheit

Klare Pfade ermöglichen eine logische Navigation für den Benutzer. Navigationsmöglichkeiten sichtbar zu machen und Zusammenhänge zwischen den Seiten zu klären, soll verhindern, dass sich die Benutzer „verirren”.

![Beispiel für „Richtig”](images/nav/clarity-image.svg)

> Die Ziele sind klar gekennzeichnet, so dass die Benutzer wissen, wo sie sich befinden.

## <a name="general-recommendations"></a>Allgemeine Empfehlungen

Nehmen wir nun unsere Gestaltungsprinzipien – Konsistenz, Einfachheit und Klarheit – und verwenden wir sie, um einige allgemeine Empfehlungen zu formulieren.

1. Denken Sie an Ihre Benutzer. Verfolgen Sie typische Pfade, die sie durch Ihre App nehmen könnten, und überlegen Sie für jede Seite, warum der Benutzer dort ist und wohin er gehen möchte.

2. Vermeiden Sie Tiefe Navigationshierarchien. Wenn Sie über drei Navigationsebenen hinausgehen, riskieren Sie, Ihren Benutzer in einer tiefen Hierarchie zu verlieren, die er nur schwer verlassen kann.

3. Vermeiden Sie „Pogo Sticking”. Pogo Sticking tritt auf, wenn der Benutzer für die Navigation zu zugehörigen Inhalten eine Ebene nach oben und erneut eine nach unten navigieren muss.

## <a name="use-the-right-structure"></a>Verwenden Sie die richtige Navigationsstruktur

Nun, da Sie mit den allgemeinen Navigationsprinzipien vertraut sind, überlegen wir uns die Strukturierung Ihrer App. Es gibt zwei allgemeine Strukturen: Flache und hierarchische.

:::row:::
    :::column:::
        ![In einer flachen Struktur angeordnete Seiten](images/nav/flat-lateral-structure.svg)
    :::column-end:::
    ::: Column Span = "2":::
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
    ::: Column Span = "2":::
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
    ::: Column Span = "2":::
        ### Combining structures

        You don't have choose to one structure or the other; many well-design apps use both. An app can use flat structures for top-level pages that can be viewed in any order, and hierarchical structures for pages that have more complex relationships.

        If your navigation structure has multiple levels, we recommend that peer-to-peer navigation elements only link to the peers within their current subtree. Consider the adjacent illustration, which shows a navigation structure that has two levels:

        - At level 1, the peer-to-peer navigation element should provide access to pages A, B, C, and D.
        - At level 2, the peer-to-peer navigation elements for the A2 pages should only link to the other A2 pages. They should not link to level 2 pages in the C subtree.
    :::column-end:::
:::row-end:::

## <a name="use-the-right-controls"></a>Verwenden der richtigen Steuerelemente

Sobald Sie sich für eine Seitenstruktur entschieden haben, müssen Sie entscheiden, wie der Benutzer durch die Seiten navigieren soll. UWP bietet eine Vielzahl von Navigationssteuerelementen, um ein konsistentes und zuverlässiges Navigationserlebnis in Ihrer App zu gewährleisten.

:::row:::
    :::column:::
        ![Frame-Bild](images/nav/thumbnail-frame.svg)
    :::column-end:::
    ::: Column Span = "2"::: [ **Frame**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Frame)

        With few exceptions, any app that has multiple pages uses a frame. Typically, an app has a main page that contains the frame and a primary navigation element, such as a navigation view control. When the user selects a page, the frame loads and displays it.
:::row-end:::

:::row:::
    :::column:::
        ![Bild für Registerkarten und pivot](images/nav/thumbnail-tabs-pivot.svg)
    :::column-end:::
    ::: Column Span = "2"::: [ **oberen Navigationsleiste und Registerkarten**](../controls-and-patterns/navigationview.md)

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
    ::: Column Span = "2"::: [ **linken Navigationsbereich**](../controls-and-patterns/navigationview.md)

        Displays a vertical list of links to top-level pages. Use when:
        
        - The pages exist at the top level.
        - There are many navigation items (more than 5)
        - You don't expect users to switch between pages frequently.
        
:::row-end:::

:::row:::
    :::column:::
        ![Master / Details-Bild](images/nav/thumbnail-master-detail.svg)
    :::column-end:::
    ::: Column Span = "2"::: [ **Master/Details**](../controls-and-patterns/master-details.md)

        Displays a list (master view) of items. Selecting an item displays its corresponding page in the details section. Use when:
        
        - You expect users to switch between child items frequently.
        - You want to enable the user to perform high-level operations, such as deleting or sorting, on individual items or groups of items, and also want to enable the user to view or update the details for each item.

        Master/details is well suited for email inboxes, contact lists, and data entry.
:::row-end:::

:::row:::
    :::column:::
        ![Bild für Hyperlinks und Schaltflächen](images/nav/thumbnail-hyperlinks-buttons.svg)
    :::column-end:::
    ::: Column Span = "2"::: [ **Hyperlinks**](../controls-and-patterns/hyperlinks.md)

        Embedded navigation elements can appear in a page's content. Unlike other navigation elements, which should be consistent across the pages, content-embedded navigation elements are unique from page to page.
:::row-end:::

## <a name="next-add-navigation-code-to-your-app"></a>Nächster Schritt: Hinzufügen von Navigationscode zu Ihrer App

Im nächsten Artikel, [Implementierung grundlegender Navigation,](navigate-between-two-pages.md), lernen Sie den Code kennen, die für die Verwendung von Frame-Steuerelementen zur Bereitstellung einer grundlegenden Navigation zwischen zwei Seiten in Ihrer App erforderlich ist.