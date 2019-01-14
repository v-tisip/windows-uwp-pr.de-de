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
ms.openlocfilehash: b2d85d97fa704b4fb79e93cf95fdd1bfcc41f8ca
ms.sourcegitcommit: 59f874b6667c3f639d8b0c7eeca886e71bf95614
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "9004606"
---
# <a name="content-design-basics-for-uwp-apps"></a><span data-ttu-id="6d544-103">Grundlagen des Inhaltsdesigns für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="6d544-103">Content design basics for UWP apps</span></span>

<span data-ttu-id="6d544-104">Der Hauptzweck einer App besteht darin, den Zugriff auf Inhalte zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="6d544-104">The main purpose of any app is to provide access to content.</span></span> <span data-ttu-id="6d544-105">Da es Apps für viele verschiedene Zwecke gibt, gibt es Inhalte in vielen Formen: In einer Fotobearbeitungs-App ist das Foto der Inhalt; in einer Reiseanwendung sind es Karten und Informationen über Reiseziele, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="6d544-105">Since apps exist for many different purposes, content comes in many forms: in a photo-editing app, the photo is the content; in a travel app, maps and information about travel destinations is the content; and so on.</span></span> 

<span data-ttu-id="6d544-106">Dieser Artikel gibt einen Überblick darüber, wie Sie Inhalte in Ihrer App präsentieren können.</span><span class="sxs-lookup"><span data-stu-id="6d544-106">This article provides an overview of how you can present content in your app.</span></span> <span data-ttu-id="6d544-107">Wir beschreiben gängige Seitenmuster und UI-Elemente, die Sie zur Darstellung Ihrer Inhalte verwenden können, egal in welcher Form.</span><span class="sxs-lookup"><span data-stu-id="6d544-107">We describe common page patterns and UI elements that you can use to display your content, whatever form it may be in.</span></span>

## <a name="common-page-patterns"></a><span data-ttu-id="6d544-108">Allgemeine Seitenmuster</span><span class="sxs-lookup"><span data-stu-id="6d544-108">Common page patterns</span></span>

<span data-ttu-id="6d544-109">Viele Apps verwenden einige oder alle dieser gängigen Seitenmuster, um verschiedene Arten von Inhalten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="6d544-109">Many apps use some, or all, of these common page patterns to display different types of content.</span></span> <span data-ttu-id="6d544-110">Sie können diese Muster kombinieren, um sie für den Inhalt Ihrer App zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="6d544-110">Likewise, feel free to mix and match these patterns to optimize for your app's content.</span></span>

### <a name="landing"></a><span data-ttu-id="6d544-111">Angebotsseite (Landing-Page)</span><span class="sxs-lookup"><span data-stu-id="6d544-111">Landing</span></span>

![Angebotsseite (Landing-Page)](images/content-basics/hero-screen.png)

<span data-ttu-id="6d544-113">Angebotsseiten werden auch Hero-Screens genannt und werden häufig auf der obersten Ebene einer App-Erfahrung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6d544-113">Landing pages, also known as hero screens, often appear at the top level of an app experience.</span></span> <span data-ttu-id="6d544-114">Die große Oberfläche dient als Bühne, um Inhalte hervorzuheben, die der Nutzer ansehen und nutzen möchte.</span><span class="sxs-lookup"><span data-stu-id="6d544-114">The large surface area serves as a stage for apps to highlight content that users may want to browse and consume.</span></span>

### <a name="collections"></a><span data-ttu-id="6d544-115">Sammlungen</span><span class="sxs-lookup"><span data-stu-id="6d544-115">Collections</span></span>

![Galerie](images/content-basics/gridview.png)

<span data-ttu-id="6d544-117">Über Sammlungen können Benutzer Gruppen von Inhalten oder Daten suchen.</span><span class="sxs-lookup"><span data-stu-id="6d544-117">Collections allow users to browse groups of content or data.</span></span> <span data-ttu-id="6d544-118">Die [Rasteransicht](../controls-and-patterns/item-templates-gridview.md) ist eine gute Option für Fotos oder medienzentrierte Inhalte, und die [Listenansicht](../controls-and-patterns/item-templates-listview.md) ist eine gute Option für textlastige Inhalte oder Daten.</span><span class="sxs-lookup"><span data-stu-id="6d544-118">[Grid view](../controls-and-patterns/item-templates-gridview.md) is a good option for photos or media-centric content, and [list view](../controls-and-patterns/item-templates-listview.md) is a good option for text-heavy content or data.</span></span>


### <a name="masterdetail"></a><span data-ttu-id="6d544-119">Master/Detail</span><span class="sxs-lookup"><span data-stu-id="6d544-119">Master/detail</span></span>

![master details](images/content-basics/master-detail.png)

<span data-ttu-id="6d544-121">Das [Master/Detail](../controls-and-patterns/master-details.md)-Modell besteht aus einer Listenansicht (Master) und einer Inhaltsansicht (Detail).</span><span class="sxs-lookup"><span data-stu-id="6d544-121">The [master/details](../controls-and-patterns/master-details.md) model consists of a list view (master) and a content view (detail).</span></span> <span data-ttu-id="6d544-122">Beide Bereiche sind festgelegt und bieten vertikales Scrollen.</span><span class="sxs-lookup"><span data-stu-id="6d544-122">Both panes are fixed and have vertical scrolling.</span></span> <span data-ttu-id="6d544-123">Zwischen dem Listenelement und der Inhaltsansicht besteht ein klarer Zusammenhang: Das Element in der Master-Ansicht ist markiert und die Detailansicht wird entsprechend aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="6d544-123">There is a clear relationship between the list item and the content view: the item in the master view is selected, and the detail view is correspondingly updated.</span></span> <span data-ttu-id="6d544-124">Zusätzlich zur Navigation in der Detailansicht können Elemente in der Master-Ansicht hinzugefügt und entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="6d544-124">In addition to providing detail view navigation, items in the master view can be added and removed.</span></span>

### <a name="details"></a><span data-ttu-id="6d544-125">Details</span><span class="sxs-lookup"><span data-stu-id="6d544-125">Details</span></span>

![Mehrere Views](images/multi-view.png)

<span data-ttu-id="6d544-127">Wenn Benutzer den gesuchten Inhalt finden, sollten Sie eine eigene Seite zum Anzeigen von Inhalten erstellen, damit die Benutzer die Seite ohne Ablenkungen betrachten können.</span><span class="sxs-lookup"><span data-stu-id="6d544-127">When users find the content they are looking for, consider creating a dedicated content-viewing page so that users can view the page free of distractions.</span></span> <span data-ttu-id="6d544-128">Wenn möglich, [erstellen Sie eine Vollbildansicht](../layout/show-multiple-views.md), die den Inhalt auf den gesamten Bildschirm erweitert und alle anderen UI-Elemente ausblendet.</span><span class="sxs-lookup"><span data-stu-id="6d544-128">If possible, [create a full-screen view option](../layout/show-multiple-views.md) that expands the content to fill the entire screen and hides all other UI elements.</span></span> 

<span data-ttu-id="6d544-129">Um sich an Änderungen in der Bildschirmgröße anzupassen, sollten Sie auch ein [dynamisches Design](design-and-ui-intro.md) erstellen, das UI-Elemente entsprechend ausblendet bzw. einblendet.</span><span class="sxs-lookup"><span data-stu-id="6d544-129">To adjust for changes in screen size, also consider creating a [responsive design](design-and-ui-intro.md) that hides/shows UI elements as appropriate.</span></span>

### <a name="forms"></a><span data-ttu-id="6d544-130">Formulare</span><span class="sxs-lookup"><span data-stu-id="6d544-130">Forms</span></span>
![form](images/content-basics/forms.png)

<span data-ttu-id="6d544-132">Ein [Formular](../controls-and-patterns/forms.md) ist eine Gruppe von Steuerelementen, die Daten von Benutzern sammeln und übermitteln.</span><span class="sxs-lookup"><span data-stu-id="6d544-132">A [form](../controls-and-patterns/forms.md) is a group of controls that collect and submit data from users.</span></span> <span data-ttu-id="6d544-133">Die meisten, wenn nicht alle Apps, verwenden eine Art Formular für Einstellungsseiten, Anmeldeportale, Feedback-Hubs, Kontoerstellung oder andere Zwecke.</span><span class="sxs-lookup"><span data-stu-id="6d544-133">Most, if not all apps, use a form of some sort for settings pages, log in portals, feedback hubs, account creation, or other purposes.</span></span> 

## <a name="common-content-elements"></a><span data-ttu-id="6d544-134">Grundlegende Inhaltselemente</span><span class="sxs-lookup"><span data-stu-id="6d544-134">Common content elements</span></span>

<span data-ttu-id="6d544-135">Um diese Seitenmuster zu erstellen, müssen Sie eine Kombination aus einzelnen Inhaltselementen verwenden.</span><span class="sxs-lookup"><span data-stu-id="6d544-135">To create these page patterns, you'll need to use a combination of individual content elements.</span></span> <span data-ttu-id="6d544-136">Hier sind einige UI-Elemente, die häufig zur Anzeige von Inhalten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6d544-136">Here are some UI elements that are commonly used to display content.</span></span> <span data-ttu-id="6d544-137">(Eine vollständige Liste der UI-Elemente finden Sie unter [Steuerelemente und Muster](../controls-and-patterns/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d544-137">(For a complete list of UI elements, see [controls and patterns](../controls-and-patterns/index.md).</span></span>

<div class="mx-responsive-img">
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6d544-138">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6d544-138">Category</span></span></th>
<th align="left"><span data-ttu-id="6d544-139">Elemente</span><span class="sxs-lookup"><span data-stu-id="6d544-139">Elements</span></span></th>
<th align="left"><span data-ttu-id="6d544-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d544-140">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="6d544-141">Audio und Video</span><span class="sxs-lookup"><span data-stu-id="6d544-141">Audio and video</span></span><br/><br/>
    <img src="images/content-basics/media-transport.png" alt="media transport control" /></td>
<td align="left"><a href="../controls-and-patterns/media-playback.md"><span data-ttu-id="6d544-142">Steuerelemente für Medienwiedergabe und -transport</span><span class="sxs-lookup"><span data-stu-id="6d544-142">Media playback and transport controls</span></span></a></td>
<td align="left"><span data-ttu-id="6d544-143">Gibt Audio- und Videoinhalte wieder.</span><span class="sxs-lookup"><span data-stu-id="6d544-143">Plays audio and video.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d544-144">Bild-Viewer</span><span class="sxs-lookup"><span data-stu-id="6d544-144">Image viewers</span></span><br/><br/>
    <img src="images/content-basics/flipview.jpg" alt="flip view" /></td>
<td align="left"><span data-ttu-id="6d544-145"><a href="../controls-and-patterns/flipview.md">Flip-Ansicht</a>, <a href="../controls-and-patterns/images-imagebrushes.md">Bild</a></span><span class="sxs-lookup"><span data-stu-id="6d544-145"><a href="../controls-and-patterns/flipview.md">Flip view</a>, <a href="../controls-and-patterns/images-imagebrushes.md">image</a></span></span></td>
<td align="left"><span data-ttu-id="6d544-146">Zeigt Bilder an.</span><span class="sxs-lookup"><span data-stu-id="6d544-146">Displays images.</span></span> <span data-ttu-id="6d544-147">Die „Flip-Ansicht“ zeigt Bilder nacheinander in einer Sammlung an, wie etwa Fotos in einem Album oder Elemente auf einer Produktdetailseite.</span><span class="sxs-lookup"><span data-stu-id="6d544-147">The flip view displays images in a collection, such as photos in an album or items in a product details page, one image at a time.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6d544-148">Collections</span><span class="sxs-lookup"><span data-stu-id="6d544-148">Collections</span></span> <br/><br/>
    <img src="images/content-basics/listview.png" alt="list view" /></td>
<td align="left"><a href="../controls-and-patterns/lists.md"><span data-ttu-id="6d544-149">Listenansicht und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="6d544-149">List view and grid view</span></span></a></td>
<td align="left"><span data-ttu-id="6d544-150">Stellt Elemente in einer interaktiven Liste oder einem Raster dar.</span><span class="sxs-lookup"><span data-stu-id="6d544-150">Presents items in an interactive list or a grid.</span></span> <span data-ttu-id="6d544-151">Verwenden Sie diese Elemente, um Benutzern die Auswahl eines Films aus einer Liste mit Neuerscheinungen oder die Verwaltung von Inventar zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6d544-151">Use these elements to let users select a movie from a list of new releases or manage an inventory.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d544-152">Text und Texteingabe</span><span class="sxs-lookup"><span data-stu-id="6d544-152">Text and text input</span></span> <br/><br/>
    <img src="images/content-basics/textbox.png" alt="text box" /></td>
<td align="left"><p><span data-ttu-id="6d544-153"><a href="../controls-and-patterns/text-block.md">Textblock</a>, <a href="../controls-and-patterns/text-box.md">Textfeld</a>, <a href="../controls-and-patterns/rich-edit-box.md">Rich-Edit-Feld</a></span><span class="sxs-lookup"><span data-stu-id="6d544-153"><a href="../controls-and-patterns/text-block.md">Text block</a>, <a href="../controls-and-patterns/text-box.md">text box</a>, <a href="../controls-and-patterns/rich-edit-box.md">rich edit box</a></span></span></p>
</td>
<td align="left"><span data-ttu-id="6d544-154">Zeigt Text an.</span><span class="sxs-lookup"><span data-stu-id="6d544-154">Displays text.</span></span> <span data-ttu-id="6d544-155">Einige Elemente ermöglichen dem Benutzer das Bearbeiten von Text.</span><span class="sxs-lookup"><span data-stu-id="6d544-155">Some elements enable the user to edit text.</span></span> <span data-ttu-id="6d544-156">Weitere Informationen finden Sie unter <a href="../controls-and-patterns/text-controls.md">Textsteuerelemente</a>.</span><span class="sxs-lookup"><span data-stu-id="6d544-156">For more info, see <a href="../controls-and-patterns/text-controls.md">Text controls</a>.</span></span>
<p><span data-ttu-id="6d544-157">Richtlinien zur Anzeige von Text finden Sie unter <a href="../style/typography.md">Typografie</a>.</span><span class="sxs-lookup"><span data-stu-id="6d544-157">For guidelines on how to display text, see <a href="../style/typography.md">Typography</a>.</span></span></p>
</td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6d544-158">Karten</span><span class="sxs-lookup"><span data-stu-id="6d544-158">Maps</span></span><br/><br/>
    <img src="images/content-basics/mapcontrol.png" alt="map control" /></td>
<td align="left"><a href="../../maps-and-location/display-maps.md"><span data-ttu-id="6d544-159">MapControl</span><span class="sxs-lookup"><span data-stu-id="6d544-159">MapControl</span></span></a></td>
<td align="left"><span data-ttu-id="6d544-160">Zeigt eine grafische oder fotorealistische Karte der Erde an.</span><span class="sxs-lookup"><span data-stu-id="6d544-160">Displays a symbolic or photorealistic map of the Earth.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6d544-161">WebView</span><span class="sxs-lookup"><span data-stu-id="6d544-161">WebView</span></span></td>
<td align="left"><a href="../controls-and-patterns/web-view.md"><span data-ttu-id="6d544-162">WebView</span><span class="sxs-lookup"><span data-stu-id="6d544-162">WebView</span></span></a></td>
<td align="left"><span data-ttu-id="6d544-163">Stellt HTML-Inhalte dar.</span><span class="sxs-lookup"><span data-stu-id="6d544-163">Renders HTML content.</span></span></td>
</tr>
</tbody>
</table>
</div>
