---
author: QuinnRadich
Description: The hub control uses a hierarchical navigation pattern to support apps with a relational information architecture.
title: Hub-Steuerelemente
ms.assetid: F1319960-63C6-4A8B-8DA1-451D59A01AC2
label: Hub
template: detail.hbs
ms.author: quradic
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
pm-contact: yulikl
design-contact: kimsea
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 4fecff4fdd836f271b9fb066c58f159111c37772
ms.sourcegitcommit: 8e30651fd691378455ea1a57da10b2e4f50e66a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "4506891"
---
# <a name="hub-controlpattern"></a><span data-ttu-id="b63d9-103">Hub-Steuerelement/-Muster</span><span class="sxs-lookup"><span data-stu-id="b63d9-103">Hub control/pattern</span></span>

 


<span data-ttu-id="b63d9-104">Mit einem Hub-Steuerelement können Sie App-Inhalte in unterschiedlichen, jedoch zusammenhängenden Abschnitten oder Kategorien organisieren.</span><span class="sxs-lookup"><span data-stu-id="b63d9-104">A hub control lets you organize app content into distinct, yet related, sections or categories.</span></span> <span data-ttu-id="b63d9-105">Abschnitte in einem Hub sind für das Durchlaufen in einer bevorzugten Reihenfolge vorgesehen und können als Ausgangspunkt für den Zugriff auf detaillierte Inhalte dienen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-105">Sections in a hub are meant to be traversed in a preferred order, and can serve as the starting point for more detailed experiences.</span></span>

> <span data-ttu-id="b63d9-106">**Wichtige APIs**: [Hub-Klasse](https://msdn.microsoft.com/library/windows/apps/dn251843), [HubSection-Klasse](https://msdn.microsoft.com/library/windows/apps/dn251845)</span><span class="sxs-lookup"><span data-stu-id="b63d9-106">**Important APIs**: [Hub class](https://msdn.microsoft.com/library/windows/apps/dn251843), [HubSection class](https://msdn.microsoft.com/library/windows/apps/dn251845)</span></span>

![Beispiel für einen Hub](images/hub_example_tablet.png)

<span data-ttu-id="b63d9-108">Inhalte in einem Hub können in einer Panoramaansicht dargestellt werden, die Benutzern einen schnellen Überblick über Neuigkeiten sowie verfügbare und wichtige Inhalte bietet.</span><span class="sxs-lookup"><span data-stu-id="b63d9-108">Content in a hub can be displayed in a panoramic view that allows users to get a glimpse of what's new, what's available, and what's relevant.</span></span> <span data-ttu-id="b63d9-109">Hubs verfügen in der Regel über eine Seitenüberschrift. Die einzelnen Inhaltsabschnitte erhalten jeweils eine Abschnittsüberschrift.</span><span class="sxs-lookup"><span data-stu-id="b63d9-109">Hubs typically have a page header, and content sections each get a section header.</span></span>


## <a name="is-this-the-right-control"></a><span data-ttu-id="b63d9-110">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="b63d9-110">Is this the right control?</span></span>

<span data-ttu-id="b63d9-111">Das Hub-Steuerelement eignet sich gut zum Anzeigen großer Mengen von Inhalten, die in einer Hierarchie angeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="b63d9-111">The hub control works well for displaying large amounts of content that is arranged in a hierarchy.</span></span> <span data-ttu-id="b63d9-112">Hubs wenden beim Durchsuchen und Entdecken neuer Inhalte eine Priorität an und sind daher nützlich zum Anzeigen von Elementen in einem Store oder einer Mediensammlung.</span><span class="sxs-lookup"><span data-stu-id="b63d9-112">Hubs prioritize the browsing and discovery of new content, making them useful for displaying items in a store or a media collection.</span></span>

<span data-ttu-id="b63d9-113">Das Hub-Steuerelement verfügt über verschiedene Funktionen, durch die es gut für die Erstellung eines Inhaltsnavigationsmustern geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="b63d9-113">The hub control has several features that make it work well for building a content navigation pattern.</span></span>

-   **<span data-ttu-id="b63d9-114">Visuelle Navigation</span><span class="sxs-lookup"><span data-stu-id="b63d9-114">Visual navigation</span></span>**

    <span data-ttu-id="b63d9-115">Ein Hub ermöglicht das Anzeigen von Inhalten in einem vielseitigen, kurzen, übersichtlichen Array.</span><span class="sxs-lookup"><span data-stu-id="b63d9-115">A hub allows content to be displayed in a diverse, brief, easy-to-scan array.</span></span>

-   **<span data-ttu-id="b63d9-116">Kategorisierung</span><span class="sxs-lookup"><span data-stu-id="b63d9-116">Categorization</span></span>**

    <span data-ttu-id="b63d9-117">Jeder Hub-Abschnitt ermöglicht die Anordnung seiner Inhalte in einer logischen Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="b63d9-117">Each hub section allows for its content to be arranged in a logical order.</span></span>

-   **<span data-ttu-id="b63d9-118">Gemischte Inhaltstypen</span><span class="sxs-lookup"><span data-stu-id="b63d9-118">Mixed content types</span></span>**

    <span data-ttu-id="b63d9-119">Bei gemischten Inhaltstypen sind variable Ressourcengrößen und -verhältnisse üblich.</span><span class="sxs-lookup"><span data-stu-id="b63d9-119">With mixed content types, variable asset sizes and ratios are common.</span></span> <span data-ttu-id="b63d9-120">Ein Hub ermöglicht das individuelle und feinsäuberliche Anordnen jedes Inhaltstyps in den einzelnen Hub-Abschnitten.</span><span class="sxs-lookup"><span data-stu-id="b63d9-120">A hub allows each content type to be uniquely and neatly laid out in each hub section.</span></span>

-   **<span data-ttu-id="b63d9-121">Variable Breite für Seiten und Inhalte</span><span class="sxs-lookup"><span data-stu-id="b63d9-121">Variable page and content widths</span></span>**

    <span data-ttu-id="b63d9-122">Da es sich um ein Panoramamodell handelt, ermöglicht der Hub variable Abschnittsbreiten.</span><span class="sxs-lookup"><span data-stu-id="b63d9-122">Being a panoramic model, the hub allows for variability in its section widths.</span></span> <span data-ttu-id="b63d9-123">Dies ist ideal für Inhalte mit unterschiedlichen Tiefen oder Mengen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-123">This is great for content of different depths or quantities.</span></span>

-   **<span data-ttu-id="b63d9-124">Flexible Architektur</span><span class="sxs-lookup"><span data-stu-id="b63d9-124">Flexible architecture</span></span>**

    <span data-ttu-id="b63d9-125">Wenn Sie eine flache App-Architektur beibehalten möchten, können Sie alle Kanalinhalte in eine Hub-Abschnittszusammenfassung einfügen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-125">If you'd prefer to keep your app architecture shallow, you can fit all channel content into a hub section summary.</span></span>

<span data-ttu-id="b63d9-126">Ein Hub ist nur eines von mehreren Navigationselementen, die Ihnen zur Verfügung stehen. Weitere Informationen zu Navigationsmustern und anderen Navigationselementen finden Sie unter [Navigationsdesigngrundlagen für UWP-Apps (Universelle Windows-Plattform)](../basics/navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b63d9-126">A hub is just one of several navigation elements you can use; to learn more about navigation patterns and the other navigation elements, see the [Navigation design basics for Universal Windows Platform (UWP) apps](../basics/navigation-basics.md).</span></span>

## <a name="hub-architecture"></a><span data-ttu-id="b63d9-127">Hub-Architektur</span><span class="sxs-lookup"><span data-stu-id="b63d9-127">Hub architecture</span></span>

<span data-ttu-id="b63d9-128">Das Hub-Steuerelement verfügt über ein hierarchisches Navigationsmuster zur Unterstützung von Apps, die eine relationale Informationsarchitektur erfordern.</span><span class="sxs-lookup"><span data-stu-id="b63d9-128">The hub control has a hierarchical navigation pattern that support apps with a relational information architecture.</span></span> <span data-ttu-id="b63d9-129">Ein Hub besteht aus verschiedenen Inhaltskategorien, die den einzelnen Bereichsseiten der App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="b63d9-129">A hub consists of different categories of content, each of which maps to the app's section pages.</span></span> <span data-ttu-id="b63d9-130">Bereichsseiten können in jeder beliebigen Form dargestellt werden, die dem jeweiligen Szenario und den Inhalten des Bereichs am besten entspricht.</span><span class="sxs-lookup"><span data-stu-id="b63d9-130">Section pages can be displayed in any form that best represents the scenario and content that the section contains.</span></span>

![Drahtmodell der hierarchischen App „Essen mit Freunden“](images/navigation_diagram_food_with_friends_app_new.png)

## <a name="layouts-and-panningscrolling"></a><span data-ttu-id="b63d9-132">Layouts und Schwenken/Bildlauf</span><span class="sxs-lookup"><span data-stu-id="b63d9-132">Layouts and panning/scrolling</span></span>

<span data-ttu-id="b63d9-133">Es gibt eine Reihe von Möglichkeiten zum Erstellens eines Layouts und zum Navigieren von Inhalten in einem Hub, stellen Sie nur sicher, dass Inhaltslisten in einem Hub immer senkrecht zur Richtung schwenken, in die der Bildlauf des Hubs erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b63d9-133">There are a number of ways to lay out and navigate content in a hub; just be sure that content lists in a hub always pan in a direction perpendicular to the direction in which the hub scrolls.</span></span>

**<span data-ttu-id="b63d9-134">Horizontale Verschiebung</span><span class="sxs-lookup"><span data-stu-id="b63d9-134">Horizontal panning</span></span>**

![<span data-ttu-id="b63d9-135">Beispiel für einen horizontal verschobenen Hub](images/controls_hub_horizontal_pan.png)
**Vertikale Verschiebung**</span><span class="sxs-lookup"><span data-stu-id="b63d9-135">Example of a horizontally panning hub](images/controls_hub_horizontal_pan.png)
**Vertical panning**</span></span>

![<span data-ttu-id="b63d9-136">Beispiel für einen vertikal verschobenen Hub](images/controls_hub_vertical_pan.png)
**Horizontale Verschiebung mit vertikalem Bildlauf der Liste/des Rasters**</span><span class="sxs-lookup"><span data-stu-id="b63d9-136">Example of a vertically panning hub](images/controls_hub_vertical_pan.png)
**Horizontal panning with vertically scrolling list/grid**</span></span>

![<span data-ttu-id="b63d9-137">Beispiel für einen horizontal verschobenen Hub mit einer Liste mit vertikalem Bildlauf](images/controls_hub_horizontal_vertical_scroll.png)
**Vertikale Verschiebung mit horizontalem Bildlauf der Liste/des Rasters**</span><span class="sxs-lookup"><span data-stu-id="b63d9-137">Example of a horizontally panning hub with a vertically scrolling list](images/controls_hub_horizontal_vertical_scroll.png)
**Vertical panning with horizontally scrolling list/grid**</span></span>

![Beispiel für einen horizontal verschobenen Hub](images/controls_hub_vertical_horizontal_scroll.png)

## <a name="examples"></a><span data-ttu-id="b63d9-139">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b63d9-139">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="b63d9-140">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="b63d9-140">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="b63d9-141">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/Hub">die App zu öffnen und Hub in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="b63d9-141">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/Hub">open the app and see the Hub in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="b63d9-142">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="b63d9-142">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="b63d9-143">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b63d9-143">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

<span data-ttu-id="b63d9-144">Der Hub bietet eine hohe Flexibilität beim Entwerfen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-144">The hub provides a great deal of design flexibility.</span></span> <span data-ttu-id="b63d9-145">Dadurch können Sie Apps mit einer großen Auswahl an attraktiven und visuell komplexen UI-Elementen entwerfen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-145">This lets you design apps that have a wide variety of compelling and visually rich experiences.</span></span> <span data-ttu-id="b63d9-146">Sie können für die erste Gruppe ein Favoritenbild oder einen Inhaltsabschnitt verwenden. Ein großes Favoritenbild kann sowohl vertikal als auch horizontal zugeschnitten werden, ohne dass der Interessenschwerpunkt verloren geht.</span><span class="sxs-lookup"><span data-stu-id="b63d9-146">You can use a hero image or content section for the first group; a large image for the hero can be cropped both vertically and horizontally without losing the center of interest.</span></span> <span data-ttu-id="b63d9-147">Hier sehen Sie ein Beispiel für ein einzelnes Favoritenbild und für seinen Zuschnitt in das Quer- und Hochformat und auf eine schmale Breite.</span><span class="sxs-lookup"><span data-stu-id="b63d9-147">Here is an example of a single hero image and how that image may be cropped for landscape, portrait, and narrow width.</span></span>

![zugeschnittenes Favoritenbild für unterschiedliche Fenstergrößen](images/hub_hero_cropped2.png)

<span data-ttu-id="b63d9-149">Auf mobilen Geräten ist jeweils ein Hub-Abschnitt sichtbar.</span><span class="sxs-lookup"><span data-stu-id="b63d9-149">On mobile devices, one hub section is visible at a time.</span></span>

![Beispiel für ein Hubmuster auf einem kleinen Bildschirm](images/phone_hub_example.png)

## <a name="recommendations"></a><span data-ttu-id="b63d9-151">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="b63d9-151">Recommendations</span></span>

-   <span data-ttu-id="b63d9-152">Wir empfehlen, den Inhalt zu beschneiden, sodass ein bestimmter Teil davon verkürzt eingeblendet wird, um Benutzern mitzuteilen, dass weitere Inhalte in einem Hub-Abschnitt vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b63d9-152">To let users know that there's more content in a hub section, we recommend clipping the content so that a certain amount of it peeks.</span></span>
-   <span data-ttu-id="b63d9-153">Je nach den Anforderungen Ihrer App können Sie dem Hub-Steuerelement mehrere Hub-Abschnitte hinzufügen, wobei jedes Steuerelement eine bestimmte Funktion erfüllt.</span><span class="sxs-lookup"><span data-stu-id="b63d9-153">Based on the needs of your app, you can add several hub sections to the hub control, with each one offering its own functional purpose.</span></span> <span data-ttu-id="b63d9-154">Ein Abschnitt kann beispielsweise eine Reihe von Links und Steuerelementen enthalten, während ein anderer Abschnitt als Repository für Miniaturansichten dient.</span><span class="sxs-lookup"><span data-stu-id="b63d9-154">For example, one section could contain a series of links and controls, while another could be a repository for thumbnails.</span></span> <span data-ttu-id="b63d9-155">Benutzer können zwischen diesen Abschnitten mit der Geste wechseln, die von dem Hub-Steuerelement unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="b63d9-155">A user can pan between these sections using the gesture support built into the hub control.</span></span>
-   <span data-ttu-id="b63d9-156">Das dynamische Umbrechen von Inhalt ist die beste Methode, um verschiedene Fenstergrößen einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-156">Having content dynamically reflow is the best way to accommodate different window sizes.</span></span>
-   <span data-ttu-id="b63d9-157">Wenn Sie viele Hub-Abschnitte haben, sollten Sie das Hinzufügen des semantischen Zooms in Erwägung ziehen.</span><span class="sxs-lookup"><span data-stu-id="b63d9-157">If you have many hub sections, consider adding semantic zoom.</span></span> <span data-ttu-id="b63d9-158">Dadurch können die Abschnitte auch leichter gefunden werden, wenn die App-Größe in eine schmale Breite geändert wird.</span><span class="sxs-lookup"><span data-stu-id="b63d9-158">This also makes it easier to find sections when the app is resized to a narrow width.</span></span>
-   <span data-ttu-id="b63d9-159">Es wird empfohlen, dass ein Element in einem Hub-Abschnitt nicht zu einem anderen Hub führt. Stattdessen können Sie interaktive Überschriften für die Navigation zu einem anderen Hub-Abschnitt oder einer anderen Seite verwenden.</span><span class="sxs-lookup"><span data-stu-id="b63d9-159">We recommend not having an item in a hub section lead to another hub; instead, you can use interactive headers to navigate to another hub section or page.</span></span>
-   <span data-ttu-id="b63d9-160">Der Hub dient als Ausgangspunkt und sollte an die Anforderungen Ihrer App angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="b63d9-160">The hub is a starting point and is meant to be customized to fit the needs of your app.</span></span> <span data-ttu-id="b63d9-161">Sie können die folgenden Aspekte eines Hubs ändern:</span><span class="sxs-lookup"><span data-stu-id="b63d9-161">You can change the following aspects of a hub:</span></span>
    -   <span data-ttu-id="b63d9-162">Anzahl Abschnitte</span><span class="sxs-lookup"><span data-stu-id="b63d9-162">Number of sections</span></span>
    -   <span data-ttu-id="b63d9-163">Inhaltstyp in den einzelnen Abschnitten</span><span class="sxs-lookup"><span data-stu-id="b63d9-163">Type of content in each section</span></span>
    -   <span data-ttu-id="b63d9-164">Positionierung und Reihenfolge von Abschnitten</span><span class="sxs-lookup"><span data-stu-id="b63d9-164">Placement and order of sections</span></span>
    -   <span data-ttu-id="b63d9-165">Größe von Abschnitten</span><span class="sxs-lookup"><span data-stu-id="b63d9-165">Size of sections</span></span>
    -   <span data-ttu-id="b63d9-166">Abstand zwischen Abschnitten</span><span class="sxs-lookup"><span data-stu-id="b63d9-166">Spacing between sections</span></span>
    -   <span data-ttu-id="b63d9-167">Abstand zwischen einem Abschnitt und dem oberen oder unteren Rand des Hubs</span><span class="sxs-lookup"><span data-stu-id="b63d9-167">Spacing between a section and the top or bottom of the hub</span></span>
    -   <span data-ttu-id="b63d9-168">Textstil und -größe in Überschriften und Inhalt</span><span class="sxs-lookup"><span data-stu-id="b63d9-168">Text style and size in headers and content</span></span>
    -   <span data-ttu-id="b63d9-169">Farbe des Hintergrunds, der Abschnitte, Abschnittsüberschriften und Abschnittsinhalte</span><span class="sxs-lookup"><span data-stu-id="b63d9-169">Color of the background, sections, section headers, and section content</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="b63d9-170">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="b63d9-170">Get the sample code</span></span>

- <span data-ttu-id="b63d9-171">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b63d9-171">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="b63d9-172">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="b63d9-172">Related articles</span></span>

- [<span data-ttu-id="b63d9-173">Hub-Klasse</span><span class="sxs-lookup"><span data-stu-id="b63d9-173">Hub class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn251843)
- [<span data-ttu-id="b63d9-174">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="b63d9-174">Navigation basics</span></span>](../basics/navigation-basics.md)
- [<span data-ttu-id="b63d9-175">Verwenden von Hubs</span><span class="sxs-lookup"><span data-stu-id="b63d9-175">Using a hub</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/dn308518)
- [<span data-ttu-id="b63d9-176">Beispiel für ein XAML-Hub-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="b63d9-176">XAML Hub control sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=310072)
