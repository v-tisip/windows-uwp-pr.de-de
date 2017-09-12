---
author: Jwmsft
Description: "Listen zeigen und ermöglichen die Interaktion mit sammlungsbasierten Inhalten."
title: Listen
ms.assetid: C73125E8-3768-46A5-B078-FDDF42AB1077
label: Lists
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: predavid
design-contact: kimsea
dev-contact: ranjeshj
doc-status: Published
ms.openlocfilehash: 0249132942cbb15a009c85c929185bffcba23cd9
ms.sourcegitcommit: 690320e6cbfc16ed9e935a136fecc44d68e95719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="lists"></a><span data-ttu-id="87686-104">Listen</span><span class="sxs-lookup"><span data-stu-id="87686-104">Lists</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">


<span data-ttu-id="87686-105">Listen zeigen und ermöglichen die Interaktion mit sammlungsbasierten Inhalten.</span><span class="sxs-lookup"><span data-stu-id="87686-105">Lists display and enable interactions with collection-based content.</span></span> <span data-ttu-id="87686-106">Zu den in diesem Artikel behandelten vier Listenmustern gehören:</span><span class="sxs-lookup"><span data-stu-id="87686-106">The four list patterns covered in this article include:</span></span>

-   <span data-ttu-id="87686-107">Listenansichten, die in erster Linie zum Anzeigen von textlastigen Inhaltssammlungen verwendet werden</span><span class="sxs-lookup"><span data-stu-id="87686-107">List views, which are primarily used to display text-heavy content collections</span></span>
-   <span data-ttu-id="87686-108">Rasteransichten, die in erster Linie zum Anzeigen von bildlastigen Inhaltssammlungen verwendet werden</span><span class="sxs-lookup"><span data-stu-id="87686-108">Grid views, which are primarily used to display image-heavy content collections</span></span>
-   <span data-ttu-id="87686-109">Dropdownlisten, aus denen Benutzer ein Element aus einer erweiterten Liste auswählen können</span><span class="sxs-lookup"><span data-stu-id="87686-109">Drop-down lists, which let users choose one item from an expanding list</span></span>
-   <span data-ttu-id="87686-110">Listenfelder, in denen Benutzer ein einzelnes Element oder mehrere Elemente aus einem Feld auswählen können, in dem gescrollt werden kann</span><span class="sxs-lookup"><span data-stu-id="87686-110">List boxes, which let users choose one item or multiple items from a box that can be scrolled</span></span>

<span data-ttu-id="87686-111">Für jedes Listenmuster sind Entwurfsrichtlinien, Features und Beispiele aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="87686-111">Design guidelines, features, and examples are given for each list pattern.</span></span>

> <span data-ttu-id="87686-112">**Wichtige APIs**: [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/br242878), [GridView-Klasse](https://msdn.microsoft.com/library/windows/apps/br242705), [ComboBox-Klasse](https://msdn.microsoft.com/library/windows/apps/br209348)</span><span class="sxs-lookup"><span data-stu-id="87686-112">**Important APIs**: [ListView class](https://msdn.microsoft.com/library/windows/apps/br242878), [GridView class](https://msdn.microsoft.com/library/windows/apps/br242705), [ComboBox class](https://msdn.microsoft.com/library/windows/apps/br209348)</span></span>

> <div id="main">
> <strong><span class="uwpd-prelease"><span data-ttu-id="87686-113">Vorabversion.</span><span class="sxs-lookup"><span data-stu-id="87686-113">Prerelease.</span></span></span> <span data-ttu-id="87686-114">Fall Creators Update (Windows10 Insider Preview-Build 16215 und höher) - Abweichende Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="87686-114">Fall Creators Update (Windows 10 Insider Preview Build 16215 and later) - Behavior change</span></span></strong>
> </div>
> <span data-ttu-id="87686-115">Beim Schwenken/Bildlauf in der Liste der UWP-Apps wird jetzt standardmäßig anstelle des Ausführens der Auswahl ein aktiver Stifts verwendet (z.B. Toucheingabe, Touchpad und passiver Stift).</span><span class="sxs-lookup"><span data-stu-id="87686-115">By default, instead of performing selection, an active pen now scrolls/pans a list in UWP apps (like touch, touchpad, and passive pen).</span></span>
> <span data-ttu-id="87686-116">Wenn Ihre App vom vorherigen Verhalten abhängig ist, können Sie die Stift-Bildlaufaktionen außer Kraft setzen und auf das vorherige Verhalten zurückzusetzen.</span><span class="sxs-lookup"><span data-stu-id="87686-116">If your app depends on the previous behavior, you can override pen scrolling and revert to the previous behavior.</span></span> <span data-ttu-id="87686-117">Weitere Details finden Sie im API-Referenzthema unter [ScrollViewer-Klasse] (https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer).</span><span class="sxs-lookup"><span data-stu-id="87686-117">See the [ScrollViewer Class] (https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.scrollviewer) API reference topic for details.</span></span>

## <a name="list-views"></a><span data-ttu-id="87686-118">Listenansichten</span><span class="sxs-lookup"><span data-stu-id="87686-118">List views</span></span>

<span data-ttu-id="87686-119">Mit Listenansichten können Sie Elemente kategorisieren und Gruppenüberschriften zuweisen, Elemente per Drag & Drop verschieben, Inhalt überprüfen und Elemente neu anordnen.</span><span class="sxs-lookup"><span data-stu-id="87686-119">List views let you categorize items and assign group headers, drag and drop items, curate content, and reorder items.</span></span>

### <a name="is-this-the-right-control"></a><span data-ttu-id="87686-120">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="87686-120">Is this the right control?</span></span>

<span data-ttu-id="87686-121">Mit einer Listenansicht können Sie:</span><span class="sxs-lookup"><span data-stu-id="87686-121">Use a list view to:</span></span>

-   <span data-ttu-id="87686-122">Inhaltssammlungen anzeigen, die in erster Linie aus Text bestehen.</span><span class="sxs-lookup"><span data-stu-id="87686-122">Display a content collection that primarily consists of text.</span></span>
-   <span data-ttu-id="87686-123">Durch eine einzelne oder kategorisierte Inhaltssammlung navigieren.</span><span class="sxs-lookup"><span data-stu-id="87686-123">Navigate a single or categorized collection of content.</span></span>
-   <span data-ttu-id="87686-124">Den Masterbereich mit dem [Master-/Detailmuster](master-details.md) erstellen.</span><span class="sxs-lookup"><span data-stu-id="87686-124">Create the master pane in the [master/details pattern](master-details.md).</span></span> <span data-ttu-id="87686-125">Ein Master-/Detailmuster wird häufig in E-Mail-Apps verwendet, in denen ein Bereich (der Masterbereich) eine Liste auswählbarer Elemente enthält, während im anderen eine detaillierte Ansicht des ausgewählten Elements enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="87686-125">A master/details pattern is often used in email apps, in which one pane (the master) has a list of selectable items while the other pane (details) has a detailed view of the selected item.</span></span>

### <a name="examples"></a><span data-ttu-id="87686-126">Beispiele</span><span class="sxs-lookup"><span data-stu-id="87686-126">Examples</span></span>

<span data-ttu-id="87686-127">Dies ist eine einfache Listenansicht mit gruppierten Daten auf einem Telefon.</span><span class="sxs-lookup"><span data-stu-id="87686-127">Here's a simple list view showing grouped data on a phone.</span></span>

![Eine Listenansicht mit gruppierten Daten](images/simple-list-view-phone.png)

### <a name="recommendations"></a><span data-ttu-id="87686-129">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="87686-129">Recommendations</span></span>

-   <span data-ttu-id="87686-130">Elemente in einer Liste sollten das gleiche Verhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="87686-130">Items within a list should have the same behavior.</span></span>
-   <span data-ttu-id="87686-131">Wenn Ihre Liste in Gruppen unterteilt ist, verwenden Sie den [semantischen Zoom](semantic-zoom.md), mit dem Benutzern die Navigation in gruppierten Inhalten erleichtert wird.</span><span class="sxs-lookup"><span data-stu-id="87686-131">If your list is divided into groups, you can use [semantic zoom](semantic-zoom.md) to make it easier for users to navigate through grouped content.</span></span>

### <a name="list-view-articles"></a><span data-ttu-id="87686-132">Artikel zur Listenansicht</span><span class="sxs-lookup"><span data-stu-id="87686-132">List view articles</span></span>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87686-133">Thema</span><span class="sxs-lookup"><span data-stu-id="87686-133">Topic</span></span></th>
<th align="left"><span data-ttu-id="87686-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87686-134">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="87686-135">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="87686-135">List view and grid view</span></span>](listview-and-gridview.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-136">Lernen Sie die Grundlagen der Verwendung einer Listen- oder Rasteransicht in Ihrer App kennen.</span><span class="sxs-lookup"><span data-stu-id="87686-136">Learn the essentials of using a list view or grid view in your app.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="87686-137">Vorlagen für Listenansichtselemente</span><span class="sxs-lookup"><span data-stu-id="87686-137">List view item templates</span></span>](listview-item-templates.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-138">Die Elemente, die Sie in einer Liste oder Raster anzeigen, können eine wichtige Rolle für das Gesamtdesign Ihrer App spielen.</span><span class="sxs-lookup"><span data-stu-id="87686-138">The items you display in a list or grid can play a major role in the overall look of your app.</span></span> <span data-ttu-id="87686-139">Ändern Sie Steuerelementvorlagen und Datenvorlagen, um das Erscheinungsbild der Elemente zu definieren, damit Ihre App gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="87686-139">Modify control templates and data templates to define the look of the items and make your app look great.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="87686-140">Invertierte Listen</span><span class="sxs-lookup"><span data-stu-id="87686-140">Inverted lists</span></span>](inverted-lists.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-141">Bei invertierten Listen werden neue Elemente am Ende hinzugefügt, z.B. bei einer Chat-App.</span><span class="sxs-lookup"><span data-stu-id="87686-141">Inverted lists have new items added at the bottom, like in a chat app.</span></span> <span data-ttu-id="87686-142">Befolgen Sie diese Richtlinien, um in Ihrer App eine invertierte Liste zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="87686-142">Follow this guidance to use an inverted list in your app.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="87686-143">Aktualisieren durch Ziehen</span><span class="sxs-lookup"><span data-stu-id="87686-143">Pull-to-refresh</span></span>](pull-to-refresh.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-144">Dank des Musters „Aktualisieren durch Ziehen“ können Benutzer aktuelle Daten in einer Liste durch das Ausführen einer Ziehbewegung von oben nach unten auf der Liste abrufen.</span><span class="sxs-lookup"><span data-stu-id="87686-144">The pull-to-refresh pattern lets a user pull down on a list of data using touch in order to retrieve more data.</span></span> <span data-ttu-id="87686-145">Verwenden Sie diese Anleitung, um „Aktualisieren durch Ziehen“ in der Listenansicht zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="87686-145">Use this guidance to implement pull-to-refresh in your list view.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="87686-146">Geschachtelte UI</span><span class="sxs-lookup"><span data-stu-id="87686-146">Nested UI</span></span>](nested-ui.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-147">Eine geschachtelte UI ist eine Benutzeroberfläche (User Interface, UI) mit geschachtelten Steuerelementen, die in einem Container eingeschlossen sind, die ein Benutzer ebenfalls aktivieren kann.</span><span class="sxs-lookup"><span data-stu-id="87686-147">Nested UI is a user interface (UI) that exposes actionable controls enclosed inside a container that a user can also take action on.</span></span> <span data-ttu-id="87686-148">Beispielsweise gibt es möglicherweise ein Listenansichtelement, das eine Schaltfläche enthält. Benutzer können das Listenelement auswählen oder die Schaltfläche verwenden, die darin geschachtelt ist.</span><span class="sxs-lookup"><span data-stu-id="87686-148">For example, you might have list view item that contains a button, and the user can select the list item, or press the button nested within it.</span></span> <span data-ttu-id="87686-149">Befolgen Sie diese bewährten Methoden, um eine optimal geschachtelte Benutzeroberfläche (UI) für Ihre Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="87686-149">Follow these best practices to provide the best nested UI experience for your users.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="grid-views"></a><span data-ttu-id="87686-150">Rasteransichten</span><span class="sxs-lookup"><span data-stu-id="87686-150">Grid views</span></span>

<span data-ttu-id="87686-151">Rasteransichten eignen sich zum Anordnen und Durchsuchen bildbasierter Inhaltssammlungen.</span><span class="sxs-lookup"><span data-stu-id="87686-151">Grid views are suited for arranging and browsing image-based content collections.</span></span> <span data-ttu-id="87686-152">Ein Rasteransichtslayout wird vertikal gescrollt und horizontal bewegt.</span><span class="sxs-lookup"><span data-stu-id="87686-152">A grid view layout scrolls vertically and pans horizontally.</span></span> <span data-ttu-id="87686-153">Elemente werden von links nach rechts und anschließend von oben nach unten in Leserichtung angeordnet.</span><span class="sxs-lookup"><span data-stu-id="87686-153">Items are laid out in a left-to-right, then top-to-bottom reading order.</span></span>

### <a name="is-this-the-right-control"></a><span data-ttu-id="87686-154">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="87686-154">Is this the right control?</span></span>

<span data-ttu-id="87686-155">Mit einer Listenansicht können Sie:</span><span class="sxs-lookup"><span data-stu-id="87686-155">Use a list view to:</span></span>

-   <span data-ttu-id="87686-156">Eine Inhaltssammlung anzeigen, die in erster Linie aus Bildern besteht.</span><span class="sxs-lookup"><span data-stu-id="87686-156">Display a content collection that primarily consists of images.</span></span>
-   <span data-ttu-id="87686-157">Inhaltsbibliotheken anzeigen.</span><span class="sxs-lookup"><span data-stu-id="87686-157">Display content libraries.</span></span>
-   <span data-ttu-id="87686-158">Die zwei Inhaltsansichten formatieren, die dem [semantischen Zoom](semantic-zoom.md) zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="87686-158">Format the two content views associated with [semantic zoom](semantic-zoom.md).</span></span>

### <a name="examples"></a><span data-ttu-id="87686-159">Beispiele</span><span class="sxs-lookup"><span data-stu-id="87686-159">Examples</span></span>

<span data-ttu-id="87686-160">Dieses Beispiel zeigt ein typisches Rasteransichtslayout, in diesem Fall zum Durchsuchen von Apps.</span><span class="sxs-lookup"><span data-stu-id="87686-160">This example shows a typical grid view layout, in this case for browsing apps.</span></span> <span data-ttu-id="87686-161">Metadaten für Rasteransichtselemente sind in der Regel auf wenige Textzeilen und eine Bewertung des Elements beschränkt.</span><span class="sxs-lookup"><span data-stu-id="87686-161">Metadata for grid view items is usually restricted to a few lines of text and an item rating.</span></span>

![Beispiel eines Rasteransichtslayouts](images/controls_gridview_example02.png)

<span data-ttu-id="87686-163">Eine Rasteransicht eignet sich ideal für eine Inhaltsbibliothek, die häufig verwendet wird, um Medien wie Bilder und Videos darzustellen.</span><span class="sxs-lookup"><span data-stu-id="87686-163">A grid view is an ideal solution for a content library, which is often used to present media such as pictures and videos.</span></span> <span data-ttu-id="87686-164">In einer Inhaltsbibliothek erwarten Benutzer, dass sie auf ein Element tippen können, um eine Aktion aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="87686-164">In a content library, users expect to be able to tap an item to invoke an action.</span></span>

![Beispiel einer Inhaltsbibliothek](images/controls_list_contentlibrary.png)

### <a name="recommendations"></a><span data-ttu-id="87686-166">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="87686-166">Recommendations</span></span>

-   <span data-ttu-id="87686-167">Elemente in einer Liste sollten das gleiche Verhalten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="87686-167">Items within a list should have the same behavior.</span></span>
-   <span data-ttu-id="87686-168">Wenn Ihre Liste in Gruppen unterteilt ist, verwenden Sie den [semantischen Zoom](semantic-zoom.md), mit dem Benutzern die Navigation in gruppierten Inhalten erleichtert wird.</span><span class="sxs-lookup"><span data-stu-id="87686-168">If your list is divided into groups, you can use [semantic zoom](semantic-zoom.md) to make it easier for users to navigate through grouped content.</span></span>

### <a name="grid-view-articles"></a><span data-ttu-id="87686-169">Artikel zur Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="87686-169">Grid view articles</span></span>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="87686-170">Thema</span><span class="sxs-lookup"><span data-stu-id="87686-170">Topic</span></span></th>
<th align="left"><span data-ttu-id="87686-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="87686-171">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="87686-172">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="87686-172">List view and grid view</span></span>](listview-and-gridview.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-173">Lernen Sie die Grundlagen der Verwendung einer Listen- oder Rasteransicht in Ihrer App kennen.</span><span class="sxs-lookup"><span data-stu-id="87686-173">Learn the essentials of using a list view or grid view in your app.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p>[<span data-ttu-id="87686-174">Vorlagen für Listenansichtselemente</span><span class="sxs-lookup"><span data-stu-id="87686-174">List view item templates</span></span>](listview-item-templates.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-175">Die Elemente, die Sie in einer Liste oder Raster anzeigen, können eine wichtige Rolle für das Gesamtdesign Ihrer App spielen.</span><span class="sxs-lookup"><span data-stu-id="87686-175">The items you display in a list or grid can play a major role in the overall look of your app.</span></span> <span data-ttu-id="87686-176">Ändern Sie Steuerelementvorlagen und Datenvorlagen, um das Erscheinungsbild der Elemente zu definieren, damit Ihre App gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="87686-176">Modify control templates and data templates to define the look of the items and make your app look great.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p>[<span data-ttu-id="87686-177">Geschachtelte UI</span><span class="sxs-lookup"><span data-stu-id="87686-177">Nested UI</span></span>](nested-ui.md)</p></td>
<td align="left"><p><span data-ttu-id="87686-178">Eine geschachtelte UI ist eine Benutzeroberfläche (User Interface, UI) mit geschachtelten Steuerelementen, die in einem Container eingeschlossen sind, die ein Benutzer ebenfalls aktivieren kann.</span><span class="sxs-lookup"><span data-stu-id="87686-178">Nested UI is a user interface (UI) that exposes actionable controls enclosed inside a container that a user can also take action on.</span></span> <span data-ttu-id="87686-179">Beispielsweise gibt es möglicherweise ein Listenansichtelement, das eine Schaltfläche enthält. Benutzer können das Listenelement auswählen oder die Schaltfläche verwenden, die darin geschachtelt ist.</span><span class="sxs-lookup"><span data-stu-id="87686-179">For example, you might have list view item that contains a button, and the user can select the list item, or press the button nested within it.</span></span> <span data-ttu-id="87686-180">Befolgen Sie diese bewährten Methoden, um eine optimal geschachtelte Benutzeroberfläche (UI) für Ihre Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="87686-180">Follow these best practices to provide the best nested UI experience for your users.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="drop-down-lists"></a><span data-ttu-id="87686-181">Dropdownlisten</span><span class="sxs-lookup"><span data-stu-id="87686-181">Drop-down lists</span></span>

<span data-ttu-id="87686-182">Dropdownlisten, auch als Kombinationsfelder bezeichnet, werden in einem kompakten Zustand gestartet und erweitert, um eine Liste mit auswählbaren Elementen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="87686-182">Drop-down lists, also known as combo boxes, start in a compact state and expand to show a list of selectable items.</span></span> <span data-ttu-id="87686-183">Das ausgewählte Element ist stets sichtbar. Nicht sichtbare Elemente können eingeblendet werden, wenn der Benutzer auf das Kombinationsfeld tippt, um es zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="87686-183">The selected item is always visible, and non-visible items can be brought into view when the user taps the combo box to expand it.</span></span>

### <a name="is-this-the-right-control"></a><span data-ttu-id="87686-184">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="87686-184">Is this the right control?</span></span>

-   <span data-ttu-id="87686-185">Mit einer Dropdownliste können Benutzer einen einzelnen Wert aus einer Reihe von Elementen auswählen, die mit einzelnen Textzeilen angemessen dargestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="87686-185">Use a drop-down list to let users select a single value from a set of items that can be adequately represented with single lines of text.</span></span>
-   <span data-ttu-id="87686-186">Verwenden Sie eine Liste oder eine Rasteransicht anstelle eines Kombinationsfelds, um Elemente anzuzeigen, die mehrere Textzeilen oder Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="87686-186">Use a list or grid view instead of a combo box to display items that contain multiple lines of text or images.</span></span>
-   <span data-ttu-id="87686-187">Wenn weniger als fünf Elemente vorhanden sind, können Sie stattdessen die Verwendung von [Optionsfeldern](radio-button.md) (wenn nur ein Element ausgewählt werden kann) oder [Kontrollkästchen](checkbox.md) (wenn mehrere Elemente ausgewählt werden können) in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="87686-187">When there are fewer than five items, consider using [radio buttons](radio-button.md) (if only one item can be selected) or [check boxes](checkbox.md) (if multiple items can be selected).</span></span>
-   <span data-ttu-id="87686-188">Verwenden Sie ein Kombinationsfeld, wenn die Auswahlelemente für den Fluss der App weniger wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="87686-188">Use a combo box when the selection items are of secondary importance in the flow of your app.</span></span> <span data-ttu-id="87686-189">Wenn für die Mehrzahl der Benutzer in der Mehrzahl der Situationen die Standardoption empfohlen wird, kann die Anzeige aller Elemente in einer Listenansicht mehr Aufmerksamkeit auf die Optionen ziehen als nötig.</span><span class="sxs-lookup"><span data-stu-id="87686-189">If the default option is recommended for most users in most situations, showing all the items by using a list view might draw more attention to the options than necessary.</span></span> <span data-ttu-id="87686-190">Sie können Platz sparen und Ablenkungen reduzieren, indem Sie ein Kombinationsfeld verwenden.</span><span class="sxs-lookup"><span data-stu-id="87686-190">You can save space and minimize distraction by using a combo box.</span></span>

### <a name="examples"></a><span data-ttu-id="87686-191">Beispiele</span><span class="sxs-lookup"><span data-stu-id="87686-191">Examples</span></span>

<span data-ttu-id="87686-192">Ein Kombinationsfeld im kompakten Zustand kann eine Kopfzeile anzeigen.</span><span class="sxs-lookup"><span data-stu-id="87686-192">A combo box in its compact state can show a header.</span></span>

![Beispiel für eine Dropdownliste im kompakten Zustand](images/combo_box_collapsed.png)

<span data-ttu-id="87686-194">Obwohl Kombinationsfelder erweitert werden, um längere Zeichenfolgen zu unterstützen, sollten Sie extrem lange Zeichenfolgen vermeiden, die nur schwer lesbar sind.</span><span class="sxs-lookup"><span data-stu-id="87686-194">Although combo boxes expand to support longer string lengths, avoid excessively long strings that are difficult to read.</span></span>

![Beispiel einer Dropdownliste mit einer langen Textzeichenfolge](images/combo_box_listitemstate.png)

<span data-ttu-id="87686-196">Wenn die Liste in einem Kombinationsfeld lang genug ist, wird eine Bildlaufleiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87686-196">If the collection in a combo box is long enough, a scroll bar will appear to accommodate it.</span></span> <span data-ttu-id="87686-197">Gruppieren Sie die Elemente in der Liste logisch.</span><span class="sxs-lookup"><span data-stu-id="87686-197">Group items logically in the list.</span></span>

![Beispiel einer Bildlaufleiste in einer Dropdownliste](images/combo_box_scroll.png)

### <a name="recommendations"></a><span data-ttu-id="87686-199">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="87686-199">Recommendations</span></span>

-   <span data-ttu-id="87686-200">Schränken Sie den Textinhalt von Kombinationsfeldelementen auf eine einzelne Zeile ein.</span><span class="sxs-lookup"><span data-stu-id="87686-200">Limit the text content of combo box items to a single line.</span></span>
-   <span data-ttu-id="87686-201">Sortieren Sie die Elemente in einem Kombinationsfeld in der logischsten Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="87686-201">Sort items in a combo box in the most logical order.</span></span> <span data-ttu-id="87686-202">Gruppieren Sie verwandte Optionen, und platzieren Sie die am häufigsten verwendeten Optionen oben in der Liste.</span><span class="sxs-lookup"><span data-stu-id="87686-202">Group together related options and place the most common options at the top.</span></span> <span data-ttu-id="87686-203">Sortieren Sie Namen in alphabetischer Reihenfolge, Zahlen in numerischer Reihenfolge und Datumsangaben in chronologischer Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="87686-203">Sort names in alphabetical order, numbers in numerical order, and dates in chronological order.</span></span>
-   <span data-ttu-id="87686-204">Um ein Kombinationsfeld zu erstellen, das live aktualisiert wird, wenn der Benutzer die Pfeiltasten (z.B. eine Dropdown-Liste für die Schriftauswahl) verwendet, müssen Sie SelectionChangedTrigger auf „Immer“ einstellen.</span><span class="sxs-lookup"><span data-stu-id="87686-204">To make a combo box that live updates while the user is using the arrow keys (like a Font selection drop-down), set SelectionChangedTrigger to “Always”.</span></span>  

### <a name="text-search"></a><span data-ttu-id="87686-205">Textsuche</span><span class="sxs-lookup"><span data-stu-id="87686-205">Text Search</span></span>

<span data-ttu-id="87686-206">Kombinationsfelder unterstützen automatisch die Suche in ihren Sammlungen.</span><span class="sxs-lookup"><span data-stu-id="87686-206">Combo boxes automatically support search within their collections.</span></span> <span data-ttu-id="87686-207">Wenn ein Benutzer über eine physische Tastatur Zeichen eingibt, während sich der Fokus auf einem geöffneten oder geschlossenen Kombinationsfeld befindet, werden Vorschläge angezeigt, die der vom Benutzer eingegebenen Zeichenfolge entsprechen.</span><span class="sxs-lookup"><span data-stu-id="87686-207">As users type characters on a physical keyboard while focused on an open or closed combo box, candidates matching the user's string are brought into view.</span></span> <span data-ttu-id="87686-208">Diese Funktionalität ist besonders bei der Navigation durch eine lange Liste nützlich.</span><span class="sxs-lookup"><span data-stu-id="87686-208">This functionality is especially helpful when navigating a long list.</span></span> <span data-ttu-id="87686-209">Beispielsweise können Benutzer bei der Interaktion mit einer Dropdownliste, die eine Liste von Bundesstaaten enthält, die Taste „w“ drücken, um „Washington“ anzuzeigen und diesen Bundesstaat schnell auswählen zu können.</span><span class="sxs-lookup"><span data-stu-id="87686-209">For example, when interacting with a drop-down containing a list of states, users can press the “w” key to bring “Washington” into view for quick selection.</span></span>


## <a name="list-boxes"></a><span data-ttu-id="87686-210">Listenfelder</span><span class="sxs-lookup"><span data-stu-id="87686-210">List boxes</span></span>

<span data-ttu-id="87686-211">In einem Listenfeld kann der Benutzer ein einzelnes Element oder mehrere Elemente aus einer Auflistung auswählen.</span><span class="sxs-lookup"><span data-stu-id="87686-211">A list box allows the user to choose either a single item or multiple items from a collection.</span></span> <span data-ttu-id="87686-212">Listenfelder ähneln Dropdownlisten, abgesehen davon, dass Listenfelder immer geöffnet sind; für ein Listenfeld gibt es keinen kompakten Zustand (nicht erweitert).</span><span class="sxs-lookup"><span data-stu-id="87686-212">List boxes are similar to drop-down lists, except that list boxes are always open—there is no compact (non-expanded) state for a list box.</span></span> <span data-ttu-id="87686-213">Elemente in einem Listenfeld können gescrollt werden, wenn der Platz nicht ausreicht, um alle Elemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="87686-213">Items in the list can be scrolled if there isn't space to show everything.</span></span>

### <a name="is-this-the-right-control"></a><span data-ttu-id="87686-214">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="87686-214">Is this the right control?</span></span>

-   <span data-ttu-id="87686-215">Ein Listenfeld kann nützlich sein, wenn Elemente in der Liste so relevant sind, dass sie auffälliger dargestellt werden sollten, und genügend Platz auf dem Bildschirm zum Anzeigen der vollständigen Liste vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="87686-215">A list box can be useful when items in the list are important enough to prominently display, and when there's enough screen real estate, to show the full list.</span></span>
-   <span data-ttu-id="87686-216">Ein Listenfeld sollte den Benutzer bei einer wichtigen Entscheidung bzw. Auswahl auf alle Alternativen aufmerksam machen.</span><span class="sxs-lookup"><span data-stu-id="87686-216">A list box should draw the user's attention to the full set of alternatives in an important choice.</span></span> <span data-ttu-id="87686-217">Im Gegensatz dazu lenkt eine Dropdownliste die Aufmerksamkeit des Benutzers zunächst auf das ausgewählte Element.</span><span class="sxs-lookup"><span data-stu-id="87686-217">By contrast, a drop-down list initially draws the user's attention to the selected item.</span></span>
-   <span data-ttu-id="87686-218">Vermeiden Sie die Verwendung eines Listenfelds in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="87686-218">Avoid using a list box if:</span></span>
    -   <span data-ttu-id="87686-219">Es gibt eine sehr kleine Anzahl von Elementen für die Liste.</span><span class="sxs-lookup"><span data-stu-id="87686-219">There is a very small number of items for the list.</span></span> <span data-ttu-id="87686-220">Ein Einzelauswahl-Listenfeld, das immer zwei identische Optionen enthält, sollte besser in Form von [Optionsfeldern](radio-button.md) dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="87686-220">A single-select list box that always has the same 2 options might be better presented as [radio buttons](radio-button.md).</span></span> <span data-ttu-id="87686-221">Ziehen Sie die Verwendung von Optionsfeldern ebenfalls in Erwägung, wenn die Liste drei oder vier statische Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="87686-221">Also consider using radio buttons when there are 3 or 4 static items in the list.</span></span>
    -   <span data-ttu-id="87686-222">Das Listenfeld ist eine Einzelauswahl und enthält immer die gleichen zwei Optionen, wobei eine als „nicht die andere Option“ impliziert werden kann (beispielsweise „Ein“ und „Aus“).</span><span class="sxs-lookup"><span data-stu-id="87686-222">The list box is single-select and it always has the same 2 options where one can be implied as not the other, such as "on" and "off."</span></span> <span data-ttu-id="87686-223">Verwenden Sie ein einzelnes Kontrollkästchen oder einen Umschalter.</span><span class="sxs-lookup"><span data-stu-id="87686-223">Use a single check box or a toggle switch.</span></span>
    -   <span data-ttu-id="87686-224">Die Anzahl von Elementen ist sehr hoch.</span><span class="sxs-lookup"><span data-stu-id="87686-224">There is a very large number of items.</span></span> <span data-ttu-id="87686-225">Bessere Optionen für lange Listen sind Rasteransicht und Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="87686-225">A better choice for long lists are grid view and list view.</span></span> <span data-ttu-id="87686-226">Für sehr lange Listen mit gruppierten Daten wir der semantische Zoom bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="87686-226">For very long lists of grouped data, semantic zoom is preferred.</span></span>
    -   <span data-ttu-id="87686-227">Bei den Elementen handelt es sich um zusammenhängende numerische Werte.</span><span class="sxs-lookup"><span data-stu-id="87686-227">The items are contiguous numerical values.</span></span> <span data-ttu-id="87686-228">Wenn dies der Fall ist, sollten Sie einen [Schieberegler](slider.md) in Erwägung ziehen.</span><span class="sxs-lookup"><span data-stu-id="87686-228">If that's the case, consider using a [slider](slider.md).</span></span>
    -   <span data-ttu-id="87686-229">Die Auswahlelemente sind im Fluss Ihrer App von sekundärer Bedeutung, oder für die meisten Benutzer wird in den meisten Situationen die Standardoption empfohlen.</span><span class="sxs-lookup"><span data-stu-id="87686-229">The selection items are of secondary importance in the flow of your app or the default option is recommended for most users in most situations.</span></span> <span data-ttu-id="87686-230">Verwenden Sie stattdessen eine Dropdownliste.</span><span class="sxs-lookup"><span data-stu-id="87686-230">Use a drop-down list instead.</span></span>

### <a name="recommendations"></a><span data-ttu-id="87686-231">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="87686-231">Recommendations</span></span>

-   <span data-ttu-id="87686-232">Der ideale Bereich von Elementen in einem Listenfeld beträgt 3 bis 9.</span><span class="sxs-lookup"><span data-stu-id="87686-232">The ideal range of items in a list box is 3 to 9.</span></span>
-   <span data-ttu-id="87686-233">Ein Listenfeld funktioniert gut, wenn die Elemente darin dynamisch variieren können.</span><span class="sxs-lookup"><span data-stu-id="87686-233">A list box works well when its items can dynamically vary.</span></span>
-   <span data-ttu-id="87686-234">Legen Sie die Größe eines Listenfelds möglichst so fest, dass für die Liste der zugehörigen Elemente keine Verschiebung und kein Scrollen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="87686-234">If possible, set the size of a list box so that its list of items don't need to be panned or scrolled.</span></span>
-   <span data-ttu-id="87686-235">Stellen Sie sicher, dass der Zweck des Listenfelds und die momentan ausgewählten Elemente klar sind.</span><span class="sxs-lookup"><span data-stu-id="87686-235">Verify that the purpose of the list box, and which items are currently selected, is clear.</span></span>
-   <span data-ttu-id="87686-236">Reservieren Sie visuelle Effekte und Animationen für das Feedback für die Fingereingabe und für den ausgewählten Zustand von Elementen.</span><span class="sxs-lookup"><span data-stu-id="87686-236">Reserve visual effects and animations for touch feedback, and for the selected state of items.</span></span>
-   <span data-ttu-id="87686-237">Beschränken Sie den Text von Listenfeldelementen auf eine einzelne Zeile.</span><span class="sxs-lookup"><span data-stu-id="87686-237">Limit the list box item's text content to a single line.</span></span> <span data-ttu-id="87686-238">Wenn es sich bei den Elementen um visuelle Objekte handelt, können Sie die Größe anpassen.</span><span class="sxs-lookup"><span data-stu-id="87686-238">If the items are visuals, you can customize the size.</span></span> <span data-ttu-id="87686-239">Wenn ein Element mehrere Textzeilen oder Bilder enthält, verwenden Sie stattdessen eine Raster- oder Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="87686-239">If an item contains multiple lines of text or images, instead use a grid view or list view.</span></span>
-   <span data-ttu-id="87686-240">Verwenden Sie die standardmäßige Schriftart, sofern Sie gemäß Ihren Markenrichtlinien keine andere verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="87686-240">Use the default font unless your brand guidelines indicate to use another.</span></span>
-   <span data-ttu-id="87686-241">Verwenden Sie ein Listenfeld nicht zum Ausführen von Befehlen oder zum dynamischen Anzeigen oder Ausblenden anderer Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="87686-241">Don't use a list box to perform commands or to dynamically show or hide other controls.</span></span>

## <a name="selection-mode"></a><span data-ttu-id="87686-242">Auswahlmodus</span><span class="sxs-lookup"><span data-stu-id="87686-242">Selection mode</span></span>

<span data-ttu-id="87686-243">Mit dem Auswahlmodus können Benutzer ein einzelnes oder mehrere Elemente auswählen und dafür Aktionen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="87686-243">Selection mode lets users select and take action on a single item or on multiple items.</span></span> <span data-ttu-id="87686-244">Er kann über ein Kontextmenü aufgerufen werden, indem Sie bei gedrückter STRG- oder UMSCHALTTASTE auf ein Element klicken oder in einer Fotogalerieansicht bei einem Element auf ein Ziel zeigen.</span><span class="sxs-lookup"><span data-stu-id="87686-244">It can be invoked through a context menu, by using CTRL+click or SHIFT+click on an item, or by rolling-over a target on an item in a gallery view.</span></span> <span data-ttu-id="87686-245">Wenn der Auswahlmodus aktiviert ist, werden Kontrollkästchen neben jedem Listenelement angezeigt, und Aktionen können am oberen oder unteren Bildschirmrand angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87686-245">When selection mode is active, check boxes appear next to each list item, and actions can appear at the top or the bottom of the screen.</span></span>

<span data-ttu-id="87686-246">Es gibt drei verschiedene Auswahlmodi:</span><span class="sxs-lookup"><span data-stu-id="87686-246">There are three selection modes:</span></span>

-   <span data-ttu-id="87686-247">Einzeln: Dabei kann der Benutzer jeweils nur ein Element auswählen.</span><span class="sxs-lookup"><span data-stu-id="87686-247">Single: The user can select only one item at a time.</span></span>
-   <span data-ttu-id="87686-248">Mehrfach: Der Benutzer kann mehrere Elemente ohne Modifizierer auswählen.</span><span class="sxs-lookup"><span data-stu-id="87686-248">Multiple: The user can select multiple items without using a modifier.</span></span>
-   <span data-ttu-id="87686-249">Erweitert: Dabei kann der Benutzer mit Zusatztasten mehrere Elemente auswählen, z.B. durch Gedrückthalten der UMSCHALTTASTE.</span><span class="sxs-lookup"><span data-stu-id="87686-249">Extended: The user can select multiple items with a modifier, such as holding down the SHIFT key.</span></span>

<span data-ttu-id="87686-250">Durch Tippen auf ein Element wird es ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="87686-250">Tapping anywhere on an item selects it.</span></span> <span data-ttu-id="87686-251">Das Tippen auf die Aktion auf der Befehlsleiste wirkt sich auf alle ausgewählten Elemente aus.</span><span class="sxs-lookup"><span data-stu-id="87686-251">Tapping on the command bar action affects all selected items.</span></span> <span data-ttu-id="87686-252">Wenn kein Element ausgewählt ist, sind die Aktionen auf der Befehlsleiste mit Ausnahme von „Alle auswählen“ in der Regel inaktiv.</span><span class="sxs-lookup"><span data-stu-id="87686-252">If no item is selected, command bar actions should be inactive, except for "Select All".</span></span>

<span data-ttu-id="87686-253">Im Auswahlmodus funktioniert das einfache Ausblenden nicht. Wenn Sie außerhalb des Frames tippen, in dem der Auswahlmodus aktiv ist, wird der Modus nicht beendet.</span><span class="sxs-lookup"><span data-stu-id="87686-253">Selection mode doesn't have a light dismiss model; tapping outside of the frame in which selection mode is active won't cancel the mode.</span></span> <span data-ttu-id="87686-254">Dadurch wird die unbeabsichtigte Deaktivierung des Modus verhindert.</span><span class="sxs-lookup"><span data-stu-id="87686-254">This is to prevent accidental deactivation of the mode.</span></span> <span data-ttu-id="87686-255">Per Klick auf die Zurück-Schaltfläche wird der Mehrfachauswahlmodus beendet.</span><span class="sxs-lookup"><span data-stu-id="87686-255">Clicking the back button dismisses the multi-select mode.</span></span>

<span data-ttu-id="87686-256">Wenn eine Aktion ausgewählt wurde, wird eine visuelle Bestätigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87686-256">Show a visual confirmation when an action is selected.</span></span> <span data-ttu-id="87686-257">Ziehen Sie die Anzeige eines Bestätigungsdialogfelds für bestimmte Aktionen in Erwägung, insbesondere bei destruktiven Aktionen wie Löschen.</span><span class="sxs-lookup"><span data-stu-id="87686-257">Consider displaying a confirmation dialog for certain actions, especially destructive actions such as delete.</span></span>

<span data-ttu-id="87686-258">Der Auswahlmodus ist auf die Seite beschränkt, auf der er aktiv ist. Er wirkt sich nicht auf Elemente außerhalb dieser Seite aus.</span><span class="sxs-lookup"><span data-stu-id="87686-258">Selection mode is confined to the page in which it is active, and can't affect any items outside of that page.</span></span>

<span data-ttu-id="87686-259">Der Einstiegspunkt für den Auswahlmodus sollte neben dem Inhalt platziert werden, auf den er sich auswirkt.</span><span class="sxs-lookup"><span data-stu-id="87686-259">The entry point to selection mode should be juxtaposed against the content it affects.</span></span>

<span data-ttu-id="87686-260">Empfehlungen für die Befehlsleiste finden Sie unter [Richtlinien für Befehlsleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="87686-260">For command bar recommendations, see [guidelines for command bars](app-bars.md).</span></span>

## <a name="globalization-and-localization-checklist"></a><span data-ttu-id="87686-261">Prüfliste für Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="87686-261">Globalization and localization checklist</span></span>

<table>
<tr>
<th><span data-ttu-id="87686-262">Umbruch</span><span class="sxs-lookup"><span data-stu-id="87686-262">Wrapping</span></span></th><td><span data-ttu-id="87686-263">Zwei Zeilen für die Listenbeschriftung zulassen.</span><span class="sxs-lookup"><span data-stu-id="87686-263">Allow two lines for the list label.</span></span></td>
</tr>
<tr>
<th><span data-ttu-id="87686-264">Horizontale Erweiterung</span><span class="sxs-lookup"><span data-stu-id="87686-264">Horizontal expansion</span></span></th><td><span data-ttu-id="87686-265">Stellen Sie sicher, dass die Felder sich an Texte unterschiedlicher Längen anpassen können und stets ein Bildlauf möglich ist.</span><span class="sxs-lookup"><span data-stu-id="87686-265">Make sure fields can accomdation text expension and are scrollable.</span></span></td>
</tr>
<tr>
<th><span data-ttu-id="87686-266">Vertikaler Abstand</span><span class="sxs-lookup"><span data-stu-id="87686-266">Vertical spacing</span></span></th><td><span data-ttu-id="87686-267">Verwenden Sie nicht lateinische Zeichen für vertikalen Abstand, um sicherzustellen, dass nicht lateinische Schriften richtig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="87686-267">Use non-Latin chracters for vertical spacing to ensure non-Latin scripts will display properly.</span></span></td>
</tr>
</table>


## <a name="related-articles"></a><span data-ttu-id="87686-268">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="87686-268">Related articles</span></span>

- [<span data-ttu-id="87686-269">Hub</span><span class="sxs-lookup"><span data-stu-id="87686-269">Hub</span></span>](hub.md)
- [<span data-ttu-id="87686-270">Master/Details</span><span class="sxs-lookup"><span data-stu-id="87686-270">Master/details</span></span>](master-details.md)
- [<span data-ttu-id="87686-271">Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="87686-271">Nav pane</span></span>](navigationview.md)
- [<span data-ttu-id="87686-272">Semantischer Zoom</span><span class="sxs-lookup"><span data-stu-id="87686-272">Semantic zoom</span></span>](semantic-zoom.md)
- [<span data-ttu-id="87686-273">Drag & Drop</span><span class="sxs-lookup"><span data-stu-id="87686-273">Drag and drop</span></span>](https://msdn.microsoft.com/windows/uwp/app-to-app/drag-and-drop)

**<span data-ttu-id="87686-274">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="87686-274">For developers</span></span>**
- [<span data-ttu-id="87686-275">ListView-Klasse</span><span class="sxs-lookup"><span data-stu-id="87686-275">ListView class</span></span>](https://msdn.microsoft.com/library/windows/apps/br242878)
- [<span data-ttu-id="87686-276">GridView-Klasse</span><span class="sxs-lookup"><span data-stu-id="87686-276">GridView class</span></span>](https://msdn.microsoft.com/library/windows/apps/br242705)
- [<span data-ttu-id="87686-277">ComboBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="87686-277">ComboBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209348)
- [<span data-ttu-id="87686-278">ListBox-Klasse</span><span class="sxs-lookup"><span data-stu-id="87686-278">ListBox class</span></span>](https://msdn.microsoft.com/library/windows/apps/br242868)