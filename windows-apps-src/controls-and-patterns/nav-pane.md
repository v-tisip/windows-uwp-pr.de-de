---
author: Jwmsft
redirect_url: https://msdn.microsoft.com/windows/uwp/controls-and-patterns/navigationview
Description: Stellt die Navigation auf oberster Ebene bereit und spart gleichzeitig Platz auf dem Bildschirm.
title: "Richtlinien für Navigationsbereiche"
ms.assetid: 8FB52F5E-8E72-4604-9222-0B0EC6A97541
label: Nav pane
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: d5c838675eb8cb568f0dabd1c6b776a8a53d3bf4
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="nav-panes"></a><span data-ttu-id="6901b-104">Navigationsbereiche</span><span class="sxs-lookup"><span data-stu-id="6901b-104">Nav panes</span></span>

<span data-ttu-id="6901b-105">Dieser Artikel wurde hierher verschoben: [Navigationsansicht](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/navigationview).</span><span class="sxs-lookup"><span data-stu-id="6901b-105">This article has moved here: [Navigation view](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/navigationview).</span></span>

<span data-ttu-id="6901b-106">Ein Navigationsbereich ist ein Muster, das trotz Einsparung des Bildschirmbereichs viele Navigationselemente auf oberster Ebene ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="6901b-106">A navigation pane (or just "nav" pane) is a pattern that allows for many top-level navigation items while conserving screen real estate.</span></span> <span data-ttu-id="6901b-107">Der Navigationsbereich wird häufig für mobile Apps verwendet, eignet sich aber auch gut für größere Bildschirme.</span><span class="sxs-lookup"><span data-stu-id="6901b-107">The nav pane is widely used for mobile apps, but also works well on larger screens.</span></span> <span data-ttu-id="6901b-108">Wenn der Bereich als eine Überlagerung verwendet wird, bleibt er reduziert und damit im Hintergrund, bis der Benutzer die Schaltfläche drückt; dies eignet sich gut für kleinere Bildschirme.</span><span class="sxs-lookup"><span data-stu-id="6901b-108">When used as an overlay, the pane remains collapsed and out-of-the way until the user presses the button, which is handy for smaller screens.</span></span> <span data-ttu-id="6901b-109">Wenn der Bereich im angedockten Modus verwendet wird, bleibt er geöffnet. Dadurch kann er bei ausreichend vorhandenem Platz auf dem Bildschirm besser genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="6901b-109">When used in its docked mode, the pane remains open, which allows greater utility if there's enough screen real estate.</span></span>

![Beispiel für einen Navigationsbereich](images/navHero.png)


**<span data-ttu-id="6901b-111">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="6901b-111">Important APIs</span></span>**

* [<span data-ttu-id="6901b-112">SplitView-Klasse</span><span class="sxs-lookup"><span data-stu-id="6901b-112">SplitView class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn864360)

## <a name="is-this-the-right-pattern"></a><span data-ttu-id="6901b-113">Ist dies das richtige Muster?</span><span class="sxs-lookup"><span data-stu-id="6901b-113">Is this the right pattern?</span></span>

<span data-ttu-id="6901b-114">Der Navigationsbereich eignet sich gut für:</span><span class="sxs-lookup"><span data-stu-id="6901b-114">The nav pane works well for:</span></span>

-   <span data-ttu-id="6901b-115">Apps mit vielen Navigationselementen auf oberster Ebene, die einen ähnlichen Typ haben.</span><span class="sxs-lookup"><span data-stu-id="6901b-115">Apps with many top-level navigation items that are of similar type.</span></span> <span data-ttu-id="6901b-116">Dies kann beispielsweise eine Sport-App mit Kategorien wie Football, Baseball, Basketball, Fußball usw. sein.</span><span class="sxs-lookup"><span data-stu-id="6901b-116">For example, a sports app with categories like Football, Baseball, Basketball, Soccer, and so on.</span></span>
-   <span data-ttu-id="6901b-117">Bereitstellen einer konsistenten Navigationsumgebungen über verschiedene Apps hinweg.</span><span class="sxs-lookup"><span data-stu-id="6901b-117">Providing a consistent navigational experience across apps.</span></span> <span data-ttu-id="6901b-118">Der Navigationsbereich sollte nur Navigationselemente, keine Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="6901b-118">Nav pane should include only navigational elements, not actions.</span></span>
-   <span data-ttu-id="6901b-119">Eine mittlere bis hohe Zahl (5-10+) an Navigationskategorien der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="6901b-119">A medium-to-high number (5-10+) of top-level navigational categories.</span></span>
-   <span data-ttu-id="6901b-120">Sparen von Platz auf dem Bildschirm (als Overlay).</span><span class="sxs-lookup"><span data-stu-id="6901b-120">Preserving screen real estate (as an overlay).</span></span>
-   <span data-ttu-id="6901b-121">Navigationselemente, auf die selten zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="6901b-121">Navigation items that are infrequently accessed.</span></span> <span data-ttu-id="6901b-122">(als Overlay).</span><span class="sxs-lookup"><span data-stu-id="6901b-122">(as an overlay).</span></span>

## <a name="building-a-nav-pane"></a><span data-ttu-id="6901b-123">Erstellen eines Navigationsbereichs</span><span class="sxs-lookup"><span data-stu-id="6901b-123">Building a nav pane</span></span>

<span data-ttu-id="6901b-124">Das Navigationsbereichsmuster besteht aus einem Bereich für die Navigationskategorien, einem Inhaltsbereich und einer optionalen Schaltfläche zum Öffnen oder schließen des Bereichs.</span><span class="sxs-lookup"><span data-stu-id="6901b-124">The nav pane pattern consists of a pane for navigation categories, a content area, and an optional button to open or close the pane.</span></span> <span data-ttu-id="6901b-125">Am einfachsten erstellen Sie einen Navigationsleistenbereich mit einem [Steuerelement für die geteilte Ansicht](split-view.md). Diese verfügt über einen leeren Bereich und einen Inhaltsbereich, der stets angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6901b-125">The easiest way to build a nav pane is with a [split view control](split-view.md), which comes with an empty pane and a content area that's always visible.</span></span>

<span data-ttu-id="6901b-126">Um Code zu testen, der dieses Muster implementiert, laden Sie die [XAML-Navigationslösung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlNavigation) von GitHub herunter.</span><span class="sxs-lookup"><span data-stu-id="6901b-126">To try out code implementing this pattern, download the [XAML Navigation solution](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlNavigation) from GitHub.</span></span>


### <a name="pane"></a><span data-ttu-id="6901b-127">Bereich</span><span class="sxs-lookup"><span data-stu-id="6901b-127">Pane</span></span>

<span data-ttu-id="6901b-128">Überschriften für Navigationskategorien werden im Bereich platziert.</span><span class="sxs-lookup"><span data-stu-id="6901b-128">Headers for navigational categories go in the pane.</span></span> <span data-ttu-id="6901b-129">Einstiegspunkte für App-Einstellungen und Kontoverwaltung werden ebenfalls im Bereich platziert, wenn zutreffend.</span><span class="sxs-lookup"><span data-stu-id="6901b-129">Entry points to app settings and account management, if applicable, also go in the pane.</span></span> <span data-ttu-id="6901b-130">Die Navigationsüberschriften bilden in der Regel eine Liste von Elementen, aus denen der Benutzer auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="6901b-130">Navigation headers are usually a list of items for the user to choose from.</span></span>

![Beispiel für den Bereich des Navigationsbereichs](images/nav_pane_expanded.png)

### <a name="content-area"></a><span data-ttu-id="6901b-132">Inhaltsbereich</span><span class="sxs-lookup"><span data-stu-id="6901b-132">Content area</span></span>

<span data-ttu-id="6901b-133">Im Inhaltsbereich werden Informationen für den ausgewählten Navigationsspeicherort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6901b-133">The content area is where information for the selected nav location is displayed.</span></span> <span data-ttu-id="6901b-134">Er kann einzelne Elemente oder andere untergeordnete Navigationselemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="6901b-134">It can contain individual elements or other sub-level navigation.</span></span>

### <a name="button"></a><span data-ttu-id="6901b-135">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="6901b-135">Button</span></span>

<span data-ttu-id="6901b-136">Wenn vorhanden, ermöglicht die Schaltfläche den Benutzern, den Bereich zu öffnen und zu schließen.</span><span class="sxs-lookup"><span data-stu-id="6901b-136">When present, the button allows users to open and close the pane.</span></span> <span data-ttu-id="6901b-137">Die Schaltfläche wird in einer festen Position angezeigt und wird nicht mit dem Bereich verschoben.</span><span class="sxs-lookup"><span data-stu-id="6901b-137">The button remains visible in a fixed position and does not move with the pane.</span></span> <span data-ttu-id="6901b-138">Es wird empfohlen, die Schaltfläche in der oberen linken Ecke der App zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="6901b-138">We recommend placing the button in the upper-left corner of your app.</span></span> <span data-ttu-id="6901b-139">Die Schaltfläche des Navigationsbereichs wird standardmäßig in drei horizontalen Linien angeordnet und häufig als „Hamburger“-Schaltfläche bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-139">The nav pane button is visualized as three stacked horizontal lines and is commonly referred to as the "hamburger" button.</span></span>

![Beispiel für die Schaltfläche des Navigationsbereichs](images/nav_button.png)

<span data-ttu-id="6901b-141">Die Schaltfläche wird in der Regel einer Textzeichenfolge zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-141">The button is usually associated with a text string.</span></span> <span data-ttu-id="6901b-142">Auf der obersten Ebene der App kann der App-Titel neben der Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6901b-142">At the top level of the app, the app title can be displayed next to the button.</span></span> <span data-ttu-id="6901b-143">Auf niedrigeren Ebenen der App kann die Textzeichenfolge der Titel oder die Seite sein, die dem Benutzer gerade angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6901b-143">At lower levels of the app, the text string may be the title of the page that the user is currently on.</span></span>

## <a name="nav-pane-variations"></a><span data-ttu-id="6901b-144">Navigationsbereichsvarianten</span><span class="sxs-lookup"><span data-stu-id="6901b-144">Nav pane variations</span></span>

<span data-ttu-id="6901b-145">Der Navigationsbereich verfügt über drei Modi: überlagert, kompakt und inline.</span><span class="sxs-lookup"><span data-stu-id="6901b-145">The nav pane has three modes: overlay, compact and inline.</span></span> <span data-ttu-id="6901b-146">Eine Überlagerung wird je nach Bedarf reduziert und erweitert.</span><span class="sxs-lookup"><span data-stu-id="6901b-146">An overlay collapses and expands as needed.</span></span> <span data-ttu-id="6901b-147">Im kompakten Modus wird der Bereich stets als schmaler Streifen angezeigt, der erweitert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6901b-147">When compact, the pane always shows as a narrow sliver which can be expanded.</span></span> <span data-ttu-id="6901b-148">Ein Bereich im Inlinemodus bleibt standardmäßig geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-148">An inline pane remains open by default.</span></span>

### <a name="overlay"></a><span data-ttu-id="6901b-149">Überlagerung</span><span class="sxs-lookup"><span data-stu-id="6901b-149">Overlay</span></span>

-   <span data-ttu-id="6901b-150">Eine Überlagerung kann für jede Bildschirmgröße und im Hoch- oder Querformat verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6901b-150">An overlay can be used on any screen size and in either portrait or landscape orientation.</span></span> <span data-ttu-id="6901b-151">Im Standardzustand (minimiert) beansprucht die Überlagerung keinen Platz auf dem Bildschirm, da nur die Schaltfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6901b-151">In its default (collapsed) state, the overlay takes up no real-estate, with only the button shown.</span></span>
-   <span data-ttu-id="6901b-152">Bietet ein On-Demand-Navigationssystem, das Platz auf dem Bildschirm spart.</span><span class="sxs-lookup"><span data-stu-id="6901b-152">Provides on-demand navigation that conserves screen real estate.</span></span> <span data-ttu-id="6901b-153">Ideal für Apps auf Smartphones und Tablets</span><span class="sxs-lookup"><span data-stu-id="6901b-153">Ideal for apps on phones and phablets.</span></span>
-   <span data-ttu-id="6901b-154">Der Bereich ist standardmäßig ausgeblendet, nur die Schaltfläche ist sichtbar.</span><span class="sxs-lookup"><span data-stu-id="6901b-154">The pane is hidden by default, with only the button visible.</span></span>
-   <span data-ttu-id="6901b-155">Durch Drücken der Schaltfläche des Navigationsbereichs wird der Bereich geöffnet und geschlossen.</span><span class="sxs-lookup"><span data-stu-id="6901b-155">Pressing the nav pane button opens and closes the overlay.</span></span>
-   <span data-ttu-id="6901b-156">Der erweiterte Zustand ist flüchtig und wird beendet, wenn eine Auswahl getroffen wird, wenn die Zurück-Schaltfläche verwendet wird, oder wenn der Benutzer außerhalb des Bereichs tippt.</span><span class="sxs-lookup"><span data-stu-id="6901b-156">The expanded state is transient and is dismissed when a selection is made, when the back button is used, or when the user taps outside of the pane.</span></span>
-   <span data-ttu-id="6901b-157">Die Überlagerung wird im Vordergrund des Inhalts gezeichnet und formatiert den Inhalt nicht neu.</span><span class="sxs-lookup"><span data-stu-id="6901b-157">The overlay draws over the top of content and does not reflow content.</span></span>

### <a name="compact"></a><span data-ttu-id="6901b-158">Kompakt</span><span class="sxs-lookup"><span data-stu-id="6901b-158">Compact</span></span>

-   <span data-ttu-id="6901b-159">Der kompakte Modus kann als `CompactOverlay` angegeben werden und überlagert dann Inhalte, wenn er geöffnet ist, oder als `CompactInline`, der dann Inhalte verschiebt.</span><span class="sxs-lookup"><span data-stu-id="6901b-159">Compact mode can be specified as `CompactOverlay`, which overlays content when opened, or `CompactInline`, which pushes content out of its way.</span></span> <span data-ttu-id="6901b-160">Wir empfehlen die Verwendung von CompactOverlay.</span><span class="sxs-lookup"><span data-stu-id="6901b-160">We recommend using CompactOverlay.</span></span>
-   <span data-ttu-id="6901b-161">Kompakte Bereiche zeigen die ausgewählte Position an, während sie nur eine kleine Menge des Bildschirminventars belegen.</span><span class="sxs-lookup"><span data-stu-id="6901b-161">Compact panes provide some indication of the selected location while using a small amount of screen real-estate.</span></span>
-   <span data-ttu-id="6901b-162">Dieser Modus ist besser für mittelgroße Bildschirme wie Tablets geeignet.</span><span class="sxs-lookup"><span data-stu-id="6901b-162">This mode is better suited for medium screens like tablets.</span></span>
-   <span data-ttu-id="6901b-163">Standardmäßig wird der Bereich geschlossen, sodass nur Navigationssymbole und die Schaltfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6901b-163">By default, the pane is closed with only navigation icons and the button visible.</span></span>
-   <span data-ttu-id="6901b-164">Durch Klicken auf die Schaltfläche des Navigationsbereichs wird der Bereich geöffnet und geschlossen. Das Verhalten entspricht dem Überlagerungs- oder Inlinemodus, abhängig vom angegebenen Anzeigemodus.</span><span class="sxs-lookup"><span data-stu-id="6901b-164">Pressing the nav pane button opens and closes the pane, which behaves like overlay or inline depending on the specified display mode.</span></span>
-   <span data-ttu-id="6901b-165">Die Auswahl sollte für die Listensymbole angezeigt werden, um hervorzuheben, wo sich der Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="6901b-165">The selection should be shown on the list icons to highlight where the user is in the navigation tree.</span></span>

### <a name="inline"></a><span data-ttu-id="6901b-166">Inline</span><span class="sxs-lookup"><span data-stu-id="6901b-166">Inline</span></span>

-   <span data-ttu-id="6901b-167">Der Navigationsbereich bleibt geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-167">The navigation pane remains open.</span></span> <span data-ttu-id="6901b-168">Dieser Modus ist besser für größere Bildschirme geeignet.</span><span class="sxs-lookup"><span data-stu-id="6901b-168">This mode is better suited for larger screens.</span></span>
-   <span data-ttu-id="6901b-169">Er unterstützt Drag & Drop-Szenarien in und aus dem Bereich.</span><span class="sxs-lookup"><span data-stu-id="6901b-169">Supports drag-and-drop scenarios to and from the pane.</span></span>
-   <span data-ttu-id="6901b-170">Die Schaltfläche des Navigationsbereichs ist für diesen Zustand nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6901b-170">The nav pane button is not required for this state.</span></span> <span data-ttu-id="6901b-171">Wenn die Schaltfläche verwendet wird, wird der Inhaltsbereich nach außen verschoben, und der Inhalt in diesem Bereich wird neu angeordnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-171">If the button is used, then the content area is pushed out and the content within that area will reflow.</span></span>
-   <span data-ttu-id="6901b-172">Die Auswahl sollte für die Listenelemente angezeigt werden, um hervorzuheben, wo sich der Benutzer in der Navigationsstruktur befindet.</span><span class="sxs-lookup"><span data-stu-id="6901b-172">The selection should be shown on the list items to highlight where the user is in the navigation tree.</span></span>

## <a name="adaptability"></a><span data-ttu-id="6901b-173">Anpassungsfähigkeit</span><span class="sxs-lookup"><span data-stu-id="6901b-173">Adaptability</span></span>

<span data-ttu-id="6901b-174">Um die Anwendbarkeit einer Vielzahl von Geräten zu maximieren, wird die Nutzung von [Haltepunkten](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) und die Anpassung des Navigationsbereichmodus an die Breite des App-Fensters empfohlen.</span><span class="sxs-lookup"><span data-stu-id="6901b-174">To maximize usability on a variety of devices, we recommend utilizing [break points](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) and adjusting nav pane's mode based on the width of its app window.</span></span>
-   <span data-ttu-id="6901b-175">Kleines Fenster</span><span class="sxs-lookup"><span data-stu-id="6901b-175">Small window</span></span>
   -   <span data-ttu-id="6901b-176">Kleiner als oder gleich 640 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="6901b-176">Less than or equal to 640px wide.</span></span>
   -   <span data-ttu-id="6901b-177">Der Navigationsbereich sollte den Überlagerungsmodus verwenden, standardmäßig geschlossen.</span><span class="sxs-lookup"><span data-stu-id="6901b-177">Nav pane should be in overlay mode, closed by default.</span></span>
-   <span data-ttu-id="6901b-178">Mittelgroßes Fenster</span><span class="sxs-lookup"><span data-stu-id="6901b-178">Medium window</span></span>
   -   <span data-ttu-id="6901b-179">Größer als 640 Pixel mit einer Breite, die kleiner als oder gleich 1007Pixeln ist.</span><span class="sxs-lookup"><span data-stu-id="6901b-179">Greater than 640px and less than or equal to 1007px wide.</span></span>
   -   <span data-ttu-id="6901b-180">Der Navigationsbereich sollte den Streifenmodus verwenden, standardmäßig geschlossen.</span><span class="sxs-lookup"><span data-stu-id="6901b-180">Nav pane should be in sliver mode, closed by default.</span></span>
-   <span data-ttu-id="6901b-181">Großes Fenster</span><span class="sxs-lookup"><span data-stu-id="6901b-181">Large window</span></span>
   -   <span data-ttu-id="6901b-182">Breite größer als 1007Pixel.</span><span class="sxs-lookup"><span data-stu-id="6901b-182">Greater than 1007px wide.</span></span>
   -   <span data-ttu-id="6901b-183">Der Navigationsbereich sollte den Andockmodus verwenden, standardmäßig geöffnet.</span><span class="sxs-lookup"><span data-stu-id="6901b-183">Nav pane should be in docked mode, opened by default.</span></span>

## <a name="tailoring"></a><span data-ttu-id="6901b-184">Anpassung</span><span class="sxs-lookup"><span data-stu-id="6901b-184">Tailoring</span></span>

<span data-ttu-id="6901b-185">Um die [10-Fuß-Erfahrung](http://go.microsoft.com/fwlink/?LinkId=760736) Ihrer App zu optimieren, sollten Sie die Anpassung des Navigationsbereichs durch Ändern der visuellen Darstellung der Navigationselemente in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="6901b-185">To optimize your app's [10ft experience](http://go.microsoft.com/fwlink/?LinkId=760736), consider tailoring nav pane by altering the visual appearance of its navigational elements.</span></span> <span data-ttu-id="6901b-186">Je nach Interaktionskontext ist es möglicherweise wichtiger, die Aufmerksamkeit des Benutzers auf das ausgewählte Navigationselement oder das fokussierte Navigationselement zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="6901b-186">Depending on the interaction context, it may be more important to call the user's attention to either the selected nav item or to the focused nav item.</span></span> <span data-ttu-id="6901b-187">Im Fall von 10-Fuß-Umgebungen, in denen Gamepads die häufigsten Eingabegeräte sind, ist es besonders wichtig, sicherzustellen, dass der Benutzer die Position des zurzeit fokussierten Element auf dem Bildschirm verfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="6901b-187">For 10ft experience, where gamepad is the most common input device, ensuring that the user can easily keep track of the currently focused item's location on screen is particularly important.</span></span>

![Beispiel für angepasste Navigationselemente](images/nav_item_states.png)

## <a name="related-topics"></a><span data-ttu-id="6901b-189">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6901b-189">Related topics</span></span>

* [<span data-ttu-id="6901b-190">Steuerelement für geteilte Ansicht</span><span class="sxs-lookup"><span data-stu-id="6901b-190">Split view control</span></span>](split-view.md)
* [<span data-ttu-id="6901b-191">Master/Details</span><span class="sxs-lookup"><span data-stu-id="6901b-191">Master/details</span></span>](master-details.md)
* [<span data-ttu-id="6901b-192">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="6901b-192">Navigation basics</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958438)