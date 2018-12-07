---
Description: An overview of common page patterns and UI elements for displaying content in your UWP app.
title: Grundlagen des Inhaltsdesigns für UWP-Apps (Universelle Windows-Plattform)
ms.assetid: 3102530A-E0D1-4C55-AEFF-99443D39D567
label: Content design basics
template: detail.hbs
op-migration-status: ready
ms.date: 12/1/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 56586e3c26c2adc07bad58e3ee072b4dc57db2ba
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8789924"
---
# <a name="content-design-basics-for-uwp-apps"></a><span data-ttu-id="0ac24-103">Grundlagen des Inhaltsdesigns für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="0ac24-103">Content design basics for UWP apps</span></span>

<span data-ttu-id="0ac24-104">Der Hauptzweck einer App besteht darin, den Zugriff auf Inhalte zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="0ac24-104">The main purpose of any app is to provide access to content.</span></span> <span data-ttu-id="0ac24-105">Da es Apps für viele verschiedene Zwecke gibt, gibt es Inhalte in vielen Formen: In einer Fotobearbeitungs-App ist das Foto der Inhalt; in einer Reiseanwendung sind es Karten und Informationen über Reiseziele, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="0ac24-105">Since apps exist for many different purposes, content comes in many forms: in a photo-editing app, the photo is the content; in a travel app, maps and information about travel destinations is the content; and so on.</span></span> 

<span data-ttu-id="0ac24-106">Dieser Artikel gibt einen Überblick darüber, wie Sie Inhalte in Ihrer App präsentieren können.</span><span class="sxs-lookup"><span data-stu-id="0ac24-106">This article provides an overview of how you can present content in your app.</span></span> <span data-ttu-id="0ac24-107">Wir beschreiben gängige Seitenmuster und UI-Elemente, die Sie zur Darstellung Ihrer Inhalte verwenden können, egal in welcher Form.</span><span class="sxs-lookup"><span data-stu-id="0ac24-107">We describe common page patterns and UI elements that you can use to display your content, whatever form it may be in.</span></span>

## <a name="common-page-patterns"></a><span data-ttu-id="0ac24-108">Allgemeine Seitenmuster</span><span class="sxs-lookup"><span data-stu-id="0ac24-108">Common page patterns</span></span>

<span data-ttu-id="0ac24-109">Viele Apps verwenden einige oder alle dieser gängigen Seitenmuster, um verschiedene Arten von Inhalten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0ac24-109">Many apps use some, or all, of these common page patterns to display different types of content.</span></span> <span data-ttu-id="0ac24-110">Sie können diese Muster kombinieren, um sie für den Inhalt Ihrer App zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="0ac24-110">Likewise, feel free to mix and match these patterns to optimize for your app's content.</span></span>

### <a name="landing"></a><span data-ttu-id="0ac24-111">Angebotsseite (Landing-Page)</span><span class="sxs-lookup"><span data-stu-id="0ac24-111">Landing</span></span>

![Angebotsseite (Landing-Page)](images/content-basics/hero-screen.png)

<span data-ttu-id="0ac24-113">Angebotsseiten werden auch Hero-Screens genannt und werden häufig auf der obersten Ebene einer App-Erfahrung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0ac24-113">Landing pages, also known as hero screens, often appear at the top level of an app experience.</span></span> <span data-ttu-id="0ac24-114">Die große Oberfläche dient als Bühne, um Inhalte hervorzuheben, die der Nutzer ansehen und nutzen möchte.</span><span class="sxs-lookup"><span data-stu-id="0ac24-114">The large surface area serves as a stage for apps to highlight content that users may want to browse and consume.</span></span>

### <a name="collections"></a><span data-ttu-id="0ac24-115">Sammlungen</span><span class="sxs-lookup"><span data-stu-id="0ac24-115">Collections</span></span>

![Galerie](images/content-basics/gridview.png)

<span data-ttu-id="0ac24-117">Über Sammlungen können Benutzer Gruppen von Inhalten oder Daten suchen.</span><span class="sxs-lookup"><span data-stu-id="0ac24-117">Collections allow users to browse groups of content or data.</span></span> <span data-ttu-id="0ac24-118">Die [Rasteransicht](../controls-and-patterns/item-templates-gridview.md) ist eine gute Option für Fotos oder medienzentrierte Inhalte, und die [Listenansicht](../controls-and-patterns/item-templates-listview.md) ist eine gute Option für textlastige Inhalte oder Daten.</span><span class="sxs-lookup"><span data-stu-id="0ac24-118">[Grid view](../controls-and-patterns/item-templates-gridview.md) is a good option for photos or media-centric content, and [list view](../controls-and-patterns/item-templates-listview.md) is a good option for text-heavy content or data.</span></span>

### <a name="hub"></a><span data-ttu-id="0ac24-119">Hub</span><span class="sxs-lookup"><span data-stu-id="0ac24-119">Hub</span></span>

![Hub](images/content-basics/hub.png)

<span data-ttu-id="0ac24-121">[Hubs](../controls-and-patterns/hub.md) wurden für den Einkauf entwickelt.</span><span class="sxs-lookup"><span data-stu-id="0ac24-121">[Hubs](../controls-and-patterns/hub.md) are designed for window shopping.</span></span> <span data-ttu-id="0ac24-122">Benutzer erhalten einen guten Einblick in die angebotenen Inhalte; es geht darum, eine große Vielfalt an Inhalten zu zeigen und gleichzeitig den Umfang gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="0ac24-122">Users get a good sneak peak at the content that's offered; it's all about showing a great diversity of content while keeping the amount brief.</span></span> <span data-ttu-id="0ac24-123">Zum Beispiel könnte Hub-Abschnitt 1 eine Hero-Screen sein, Hub-Abschnitt 2 könnte eine Sammlung enthalten, Hub-Abschnitt 3 könnte eine andere Sammlung enthalten, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="0ac24-123">For example, Hub section 1 could contain a hero screen, Hub section 2 could contain a collection, Hub section 3 could contain another collection, and so on.</span></span>

### <a name="masterdetail"></a><span data-ttu-id="0ac24-124">Master/Detail</span><span class="sxs-lookup"><span data-stu-id="0ac24-124">Master/detail</span></span>

![master details](images/content-basics/master-detail.png)

<span data-ttu-id="0ac24-126">Das [Master/Detail](../controls-and-patterns/master-details.md)-Modell besteht aus einer Listenansicht (Master) und einer Inhaltsansicht (Detail).</span><span class="sxs-lookup"><span data-stu-id="0ac24-126">The [master/details](../controls-and-patterns/master-details.md) model consists of a list view (master) and a content view (detail).</span></span> <span data-ttu-id="0ac24-127">Beide Bereiche sind festgelegt und bieten vertikales Scrollen.</span><span class="sxs-lookup"><span data-stu-id="0ac24-127">Both panes are fixed and have vertical scrolling.</span></span> <span data-ttu-id="0ac24-128">Zwischen dem Listenelement und der Inhaltsansicht besteht ein klarer Zusammenhang: Das Element in der Master-Ansicht ist markiert und die Detailansicht wird entsprechend aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0ac24-128">There is a clear relationship between the list item and the content view: the item in the master view is selected, and the detail view is correspondingly updated.</span></span> <span data-ttu-id="0ac24-129">Zusätzlich zur Navigation in der Detailansicht können Elemente in der Master-Ansicht hinzugefügt und entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="0ac24-129">In addition to providing detail view navigation, items in the master view can be added and removed.</span></span>

### <a name="details"></a><span data-ttu-id="0ac24-130">Details</span><span class="sxs-lookup"><span data-stu-id="0ac24-130">Details</span></span>

![Mehrere Views](images/multi-view.png)

<span data-ttu-id="0ac24-132">Wenn Benutzer den gesuchten Inhalt finden, sollten Sie eine eigene Seite zum Anzeigen von Inhalten erstellen, damit die Benutzer die Seite ohne Ablenkungen betrachten können.</span><span class="sxs-lookup"><span data-stu-id="0ac24-132">When users find the content they are looking for, consider creating a dedicated content-viewing page so that users can view the page free of distractions.</span></span> <span data-ttu-id="0ac24-133">Wenn möglich, [erstellen Sie eine Vollbildansicht](../layout/show-multiple-views.md), die den Inhalt auf den gesamten Bildschirm erweitert und alle anderen UI-Elemente ausblendet.</span><span class="sxs-lookup"><span data-stu-id="0ac24-133">If possible, [create a full-screen view option](../layout/show-multiple-views.md) that expands the content to fill the entire screen and hides all other UI elements.</span></span> 

<span data-ttu-id="0ac24-134">Um sich an Änderungen in der Bildschirmgröße anzupassen, sollten Sie auch ein [dynamisches Design](design-and-ui-intro.md) erstellen, das UI-Elemente entsprechend ausblendet bzw. einblendet.</span><span class="sxs-lookup"><span data-stu-id="0ac24-134">To adjust for changes in screen size, also consider creating a [responsive design](design-and-ui-intro.md) that hides/shows UI elements as appropriate.</span></span>

### <a name="forms"></a><span data-ttu-id="0ac24-135">Formulare</span><span class="sxs-lookup"><span data-stu-id="0ac24-135">Forms</span></span>
![form](images/content-basics/forms.png)

<span data-ttu-id="0ac24-137">Ein [Formular](../controls-and-patterns/forms.md) ist eine Gruppe von Steuerelementen, die Daten von Benutzern sammeln und übermitteln.</span><span class="sxs-lookup"><span data-stu-id="0ac24-137">A [form](../controls-and-patterns/forms.md) is a group of controls that collect and submit data from users.</span></span> <span data-ttu-id="0ac24-138">Die meisten, wenn nicht alle Apps, verwenden eine Art Formular für Einstellungsseiten, Anmeldeportale, Feedback-Hubs, Kontoerstellung oder andere Zwecke.</span><span class="sxs-lookup"><span data-stu-id="0ac24-138">Most, if not all apps, use a form of some sort for settings pages, log in portals, feedback hubs, account creation, or other purposes.</span></span> 

## <a name="common-content-elements"></a><span data-ttu-id="0ac24-139">Grundlegende Inhaltselemente</span><span class="sxs-lookup"><span data-stu-id="0ac24-139">Common content elements</span></span>

<span data-ttu-id="0ac24-140">Um diese Seitenmuster zu erstellen, müssen Sie eine Kombination aus einzelnen Inhaltselementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ac24-140">To create these page patterns, you'll need to use a combination of individual content elements.</span></span> <span data-ttu-id="0ac24-141">Hier sind einige UI-Elemente, die häufig zur Anzeige von Inhalten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0ac24-141">Here are some UI elements that are commonly used to display content.</span></span> <span data-ttu-id="0ac24-142">(Eine vollständige Liste der UI-Elemente finden Sie unter [Steuerelemente und Muster](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ac24-142">(For a complete list of UI elements, see [controls and patterns](../controls-and-patterns/index.md).</span></span>

<div class="mx-responsive-img">
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0ac24-143">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0ac24-143">Category</span></span></th>
<th align="left"><span data-ttu-id="0ac24-144">Elemente</span><span class="sxs-lookup"><span data-stu-id="0ac24-144">Elements</span></span></th>
<th align="left"><span data-ttu-id="0ac24-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0ac24-145">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0ac24-146">Audio und Video</span><span class="sxs-lookup"><span data-stu-id="0ac24-146">Audio and video</span></span><br/><br/>
    <img src="images/content-basics/media-transport.png" alt="media transport control" /></td>
<td align="left"><a href="../controls-and-patterns/media-playback.md"><span data-ttu-id="0ac24-147">Steuerelemente für Medienwiedergabe und -transport</span><span class="sxs-lookup"><span data-stu-id="0ac24-147">Media playback and transport controls</span></span></a></td>
<td align="left"><span data-ttu-id="0ac24-148">Gibt Audio- und Videoinhalte wieder.</span><span class="sxs-lookup"><span data-stu-id="0ac24-148">Plays audio and video.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0ac24-149">Bild-Viewer</span><span class="sxs-lookup"><span data-stu-id="0ac24-149">Image viewers</span></span><br/><br/>
    <img src="images/content-basics/flipview.jpg" alt="flip view" /></td>
<td align="left"><span data-ttu-id="0ac24-150"><a href="../controls-and-patterns/flipview.md">Flip-Ansicht</a>, <a href="../controls-and-patterns/images-imagebrushes.md">Bild</a></span><span class="sxs-lookup"><span data-stu-id="0ac24-150"><a href="../controls-and-patterns/flipview.md">Flip view</a>, <a href="../controls-and-patterns/images-imagebrushes.md">image</a></span></span></td>
<td align="left"><span data-ttu-id="0ac24-151">Zeigt Bilder an.</span><span class="sxs-lookup"><span data-stu-id="0ac24-151">Displays images.</span></span> <span data-ttu-id="0ac24-152">Die „Flip-Ansicht“ zeigt Bilder nacheinander in einer Sammlung an, wie etwa Fotos in einem Album oder Elemente auf einer Produktdetailseite.</span><span class="sxs-lookup"><span data-stu-id="0ac24-152">The flip view displays images in a collection, such as photos in an album or items in a product details page, one image at a time.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0ac24-153">Collections</span><span class="sxs-lookup"><span data-stu-id="0ac24-153">Collections</span></span> <br/><br/>
    <img src="images/content-basics/listview.png" alt="list view" /></td>
<td align="left"><a href="../controls-and-patterns/lists.md"><span data-ttu-id="0ac24-154">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="0ac24-154">List view and grid view</span></span></a></td>
<td align="left"><span data-ttu-id="0ac24-155">Stellt Elemente in einer interaktiven Liste oder einem Raster dar.</span><span class="sxs-lookup"><span data-stu-id="0ac24-155">Presents items in an interactive list or a grid.</span></span> <span data-ttu-id="0ac24-156">Verwenden Sie diese Elemente, um Benutzern die Auswahl eines Films aus einer Liste mit Neuerscheinungen oder die Verwaltung von Inventar zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="0ac24-156">Use these elements to let users select a movie from a list of new releases or manage an inventory.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0ac24-157">Text und Texteingabe</span><span class="sxs-lookup"><span data-stu-id="0ac24-157">Text and text input</span></span> <br/><br/>
    <img src="images/content-basics/textbox.png" alt="text box" /></td>
<td align="left"><p><span data-ttu-id="0ac24-158"><a href="../controls-and-patterns/text-block.md">Textblock</a>, <a href="../controls-and-patterns/text-box.md">Textfeld</a>, <a href="../controls-and-patterns/rich-edit-box.md">Rich-Edit-Feld</a></span><span class="sxs-lookup"><span data-stu-id="0ac24-158"><a href="../controls-and-patterns/text-block.md">Text block</a>, <a href="../controls-and-patterns/text-box.md">text box</a>, <a href="../controls-and-patterns/rich-edit-box.md">rich edit box</a></span></span></p>
</td>
<td align="left"><span data-ttu-id="0ac24-159">Zeigt Text an.</span><span class="sxs-lookup"><span data-stu-id="0ac24-159">Displays text.</span></span> <span data-ttu-id="0ac24-160">Einige Elemente ermöglichen dem Benutzer das Bearbeiten von Text.</span><span class="sxs-lookup"><span data-stu-id="0ac24-160">Some elements enable the user to edit text.</span></span> <span data-ttu-id="0ac24-161">Weitere Informationen finden Sie unter <a href="../controls-and-patterns/text-controls.md">Textsteuerelemente</a>.</span><span class="sxs-lookup"><span data-stu-id="0ac24-161">For more info, see <a href="../controls-and-patterns/text-controls.md">Text controls</a>.</span></span>
<p><span data-ttu-id="0ac24-162">Richtlinien zur Anzeige von Text finden Sie unter [Typografie](../style/typography.md).</span><span class="sxs-lookup"><span data-stu-id="0ac24-162">For guidelines on how to display text, see [Typography](../style/typography.md).</span></span></p>
</td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0ac24-163">Karten</span><span class="sxs-lookup"><span data-stu-id="0ac24-163">Maps</span></span><br/><br/>
    <img src="images/content-basics/mapcontrol.png" alt="map control" /></td>
<td align="left"><a href="../../maps-and-location/display-maps.md"><span data-ttu-id="0ac24-164">MapControl</span><span class="sxs-lookup"><span data-stu-id="0ac24-164">MapControl</span></span></a></td>
<td align="left"><span data-ttu-id="0ac24-165">Zeigt eine grafische oder fotorealistische Karte der Erde an.</span><span class="sxs-lookup"><span data-stu-id="0ac24-165">Displays a symbolic or photorealistic map of the Earth.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0ac24-166">WebView</span><span class="sxs-lookup"><span data-stu-id="0ac24-166">WebView</span></span></td>
<td align="left"><a href="../controls-and-patterns/web-view.md"><span data-ttu-id="0ac24-167">WebView</span><span class="sxs-lookup"><span data-stu-id="0ac24-167">WebView</span></span></a></td>
<td align="left"><span data-ttu-id="0ac24-168">Stellt HTML-Inhalte dar.</span><span class="sxs-lookup"><span data-stu-id="0ac24-168">Renders HTML content.</span></span></td>
</tr>
</tbody>
</table>
</div>
