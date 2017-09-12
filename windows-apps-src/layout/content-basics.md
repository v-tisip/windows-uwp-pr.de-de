---
author: mijacobs
Description: "Der Hauptzweck einer App besteht darin, den Zugriff auf Inhalte zu gewähren. In einer Fotobearbeitungs-App sind Fotos der Content, in einer Reise-App Karten und Informationen über die Reiseziele usw."
title: "Grundlagen des Inhaltsdesigns für UWP-Apps (Universelle Windows-Plattform)"
ms.assetid: 3102530A-E0D1-4C55-AEFF-99443D39D567
label: Content design basics
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 988fa8c4b0a9b0731fbe6976b5a71da06e77b559
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
#  <a name="content-design-basics-for-uwp-apps"></a><span data-ttu-id="2a8f7-105">Grundlagen des Inhaltsdesigns für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="2a8f7-105">Content design basics for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="2a8f7-106">Der Hauptzweck jeder App ist das Bereitstellen von Zugriff auf Content: In einer Fotobearbeitungs-App sind Fotos der Content, in einer Reise-App Karten und Informationen über die Reiseziele usw.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-106">The main purpose of any app is to provide access to content: in a photo-editing app, the photo is the content; in a travel app, maps and info about travel destinations is the content; and so on.</span></span> <span data-ttu-id="2a8f7-107">Navigationselemente bieten Zugriff auf Content; Befehlselemente ermöglichen dem Benutzer die Interaktion mit Content; Content-Elemente zeigen den tatsächlichen Content an.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-107">Navigation elements provide access to content; command elements enable the user to interact with content; content elements display the actual content.</span></span>

<span data-ttu-id="2a8f7-108">Dieser Artikel bietet Empfehlungen zum Content-Design für drei Content-Szenarien.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-108">This article provides content design recommendations for the three content scenarios.</span></span>

## <a name="design-for-the-right-content-scenario"></a><span data-ttu-id="2a8f7-109">Design für das richtige Content-Szenario</span><span class="sxs-lookup"><span data-stu-id="2a8f7-109">Design for the right content scenario</span></span>


<span data-ttu-id="2a8f7-110">Dies sind die drei wichtigsten Contentszenarien:</span><span class="sxs-lookup"><span data-stu-id="2a8f7-110">There are three main content scenarios:</span></span>

-   <span data-ttu-id="2a8f7-111">**Konsum**: Eine hauptsächlich einseitige Erfahrung, bei der der Content konsumiert wird.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-111">**Consumption**: A primarily one-way experience where content is consumed.</span></span> <span data-ttu-id="2a8f7-112">Beinhaltet Aufgaben wie Lesen, Musik hören, Videos, Fotos und Bilder ansehen.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-112">It includes tasks like reading, listening to music, watching videos, and photo and image viewing.</span></span>
-   <span data-ttu-id="2a8f7-113">**Erstellen**: Eine hauptsächlich einseitige Erfahrung, bei der der Schwerpunkt auf dem Erstellen von neuem Content liegt.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-113">**Creation**: A primarily one-way experience where the focus is creating new content.</span></span> <span data-ttu-id="2a8f7-114">Kann aufgeschlüsselt werden in das Erstellen von Dingen von Grund auf, wie etwa Aufnehmen eines Fotos oder Videos, das Erstellen eines neuen Bilds in einer Mal-App oder das Öffnen eines leeren Dokuments.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-114">It can be broken down into making things from scratch, like shooting a photo or video, creating a new image in a painting app, or opening a fresh document.</span></span>
-   <span data-ttu-id="2a8f7-115">**Interaktiv**: Eine bilaterale Content-Erfahrung, die den Konsum, die Erstellung und Überprüfung von Content umfasst.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-115">**Interactive**: A two-way content experience that includes consuming, creating, and revising content.</span></span>

## <a name="consumption-focused-apps"></a><span data-ttu-id="2a8f7-116">Konsumorientierte Apps</span><span class="sxs-lookup"><span data-stu-id="2a8f7-116">Consumption-focused apps</span></span>


<span data-ttu-id="2a8f7-117">Content-Elemente erhalten die höchste Priorität in einer konsumorientierten App, gefolgt von den [Navigationselementen](navigation-basics.md), die erforderlich sind, damit die Benutzer den gewünschten Content finden.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-117">Content elements receive the highest priority in a consumption-focused app, followed by the [navigation elements](navigation-basics.md) needed to help users find the content they want.</span></span> <span data-ttu-id="2a8f7-118">Beispiele für konsumorientierte Apps sind Movie-Player, Lese-Apps, Musik-Apps und Foto-Viewer.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-118">Examples of consumption-focused apps include movie players, reading apps, music apps, and photo viewers.</span></span>

![Eine Nachrichten-App](images/news-reader/v2/newsreader-v2-tablet-phone.png)

<span data-ttu-id="2a8f7-120">Allgemeine Empfehlungen für konsumorientierte Apps:</span><span class="sxs-lookup"><span data-stu-id="2a8f7-120">General recommendations for consumption-focused apps:</span></span>

-   <span data-ttu-id="2a8f7-121">Erstellen Sie dedizierte [Navigationsseiten](navigation-basics.md) und Content-Seiten, sodass die Benutzer den gewünschten Content finden und auf einer dedizierten Seite ohne Ablenkung ansehen können.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-121">Consider creating dedicated [navigation](navigation-basics.md) pages and content-viewing pages, so that when users find the content they are looking for, they can view it on a dedicated page free of distractions.</span></span>
-   <span data-ttu-id="2a8f7-122">Erstellen Sie eine Vollbild-Anzeigeoption, die den Content auf den gesamten Bildschirm erweitert und alle anderen UI-Elemente ausblendet.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-122">Consider creating a full-screen view option that expands the content to fill the entire screen and hides all other UI elements.</span></span>

## <a name="creation-focused-apps"></a><span data-ttu-id="2a8f7-123">Erstellungsorientierte Apps</span><span class="sxs-lookup"><span data-stu-id="2a8f7-123">Creation-focused apps</span></span>


<span data-ttu-id="2a8f7-124">Content- und [Befehlselemente](commanding-basics.md) sind die wichtigsten UI-Elemente in einer erstellungsorientierten App. Befehlselemente ermöglichen dem Benutzer das Erstellen von neuem Content.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-124">Content and [command](commanding-basics.md) elements are the most import UI elements in a creation-focused app: command elements enable the user to create new content.</span></span> <span data-ttu-id="2a8f7-125">Zu den Beispielen gehören Mal-Apps, Fotobearbeitungs-Apps, Videobearbeitungs-Apps und Textverarbeitungs-Apps.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-125">Examples include painting apps, photo editing apps, video editing apps, and word processing apps.</span></span>

<span data-ttu-id="2a8f7-126">Als Beispiel finden Sie hier ein Design einer Foto-App, die Befehlszeilen zum Bereitstellen des Zugriffs auf Tools und Fotobearbeitungsoptionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-126">As an example, here's a design for a photo app that uses command bars to provide access to tools and photo manipulation options.</span></span> <span data-ttu-id="2a8f7-127">Da alle Befehle in der Befehlsleiste enthalten sind, kann die App den Großteil des Platzes auf dem Bildschirm dem Content widmen, also dem Foto, das bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-127">Because all the commands are in the command bar, the app can devote most of its screen space to its content, the photo being edited.</span></span>

![Beispiel für den Entwurf einer Fotobearbeitungs-App, die eine aktive Canvas verwendet](images/photo-editor/uap-photo-tabletphone-sbs.png)

<span data-ttu-id="2a8f7-129">Allgemeine Empfehlungen für erstellungsorientierte Apps:</span><span class="sxs-lookup"><span data-stu-id="2a8f7-129">General recommendations for creation-focused apps:</span></span>

-   <span data-ttu-id="2a8f7-130">Minimieren Sie die Verwendung von [Navigationselementen](navigation-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2a8f7-130">Minimize the use of [navigation](navigation-basics.md) elements.</span></span>
-   <span data-ttu-id="2a8f7-131">[Befehlselemente](commanding-basics.md) sind insbesondere bei erstellungsorientierten Apps wichtig.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-131">[Command](commanding-basics.md) elements are especially important in creation-focused apps.</span></span> <span data-ttu-id="2a8f7-132">Da Benutzer zahlreiche Befehle ausführen, empfehlen wir die Bereitstellung eines Befehlsverlaufs/einer Rückgängig-Funktion.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-132">Since users will be executing a lot of commands, we recommend providing a command history/undo functionality.</span></span>

## <a name="apps-with-interactive-content"></a><span data-ttu-id="2a8f7-133">Apps mit interaktivem Content</span><span class="sxs-lookup"><span data-stu-id="2a8f7-133">Apps with interactive content</span></span>


<span data-ttu-id="2a8f7-134">In einer App mit interaktivem Content erstellen die Benutzer Content, zeigen ihn an und bearbeiten ihn. Viele Apps passen in diese Kategorie.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-134">In an app with interactive content, users create, view, and edit content; many apps fit into this category.</span></span> <span data-ttu-id="2a8f7-135">Zu den Beispielen dieser Typen von Apps gehören Branchen-Apps, Bestandsverwaltungs-Apps, Koch-Apps, die dem Benutzer des Erstellen oder Bearbeiten von Rezepten ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-135">Examples of these types of apps include line of business apps, inventory management apps, cooking apps that enable the user to create or modify recipes.</span></span>

![Ein Design für ein Zusammenarbeitstool, eine App mit interaktivem Content](images/collaboration-tool/uap-collaboration-tabphone-700.png)

<span data-ttu-id="2a8f7-137">Diese Art Apps muss ein Gleichgewicht aller drei UI-Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="2a8f7-137">These sort of apps need to balance all three UI elements:</span></span>

-   <span data-ttu-id="2a8f7-138">[Navigationselemente](navigation-basics.md) helfen Benutzern beim Suchen und Anzeigen von Content.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-138">[Navigation](navigation-basics.md) elements help users find and view content.</span></span> <span data-ttu-id="2a8f7-139">Falls Sie Content anzeigen und suchen, ist das wichtigste Szenario, Navigationselemente zu priorisieren, zu filtern, zu sortieren und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-139">If viewing and finding content is the most important scenario, prioritize navigation elements, filtering and sorting, and search.</span></span>
-   <span data-ttu-id="2a8f7-140">[Befehlselemente](commanding-basics.md) lassen den Benutzer Content erstellen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-140">[Command](commanding-basics.md) elements let the user create, edit, and manipulate content.</span></span>

<span data-ttu-id="2a8f7-141">Allgemeine Empfehlungen für Apps mit interaktivem Content:</span><span class="sxs-lookup"><span data-stu-id="2a8f7-141">General recommendations for apps with interactive content:</span></span>

-   <span data-ttu-id="2a8f7-142">Es kann schwierig sein, ein Gleichgewicht aus Navigations-, Content- und Befehlselementen zu finden, wenn alle drei wichtig sind.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-142">It can be difficult to balance navigation, content, and command elements when all three are important.</span></span> <span data-ttu-id="2a8f7-143">Stellen Sie möglichst separate Bildschirme zum Durchsuchen, Erstellen und Bearbeiten von Content oder zum Wechseln des Modus bereit.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-143">If possible, consider creating separate screens for browsing, creating, and editing content, or providing mode switches.</span></span>

## <a name="commonly-used-content-elements"></a><span data-ttu-id="2a8f7-144">Häufig verwendete Content-Elemente</span><span class="sxs-lookup"><span data-stu-id="2a8f7-144">Commonly used content elements</span></span>


<span data-ttu-id="2a8f7-145">Häufig zum Anzeigen von Content verwendete UI-Elemente.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-145">Here are some UI elements commonly used to display content.</span></span> <span data-ttu-id="2a8f7-146">(Eine vollständige Liste der UI-Elemente finden Sie unter [Steuerelemente und Muster](https://msdn.microsoft.com/library/windows/apps/dn611856).)</span><span class="sxs-lookup"><span data-stu-id="2a8f7-146">(For a complete list of UI elements, see [Controls and UI elements](https://msdn.microsoft.com/library/windows/apps/dn611856).)</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2a8f7-147">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2a8f7-147">Category</span></span></th>
<th align="left"><span data-ttu-id="2a8f7-148">Elemente</span><span class="sxs-lookup"><span data-stu-id="2a8f7-148">Elements</span></span></th>
<th align="left"><span data-ttu-id="2a8f7-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a8f7-149">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="2a8f7-150">Audio und Video</span><span class="sxs-lookup"><span data-stu-id="2a8f7-150">Audio and video</span></span></td>
<td align="left">[<span data-ttu-id="2a8f7-151">Steuerelemente für Medienwiedergabe und -transport</span><span class="sxs-lookup"><span data-stu-id="2a8f7-151">Media playback and transport controls</span></span>](../controls-and-patterns/media-playback.md)</td>
<td align="left"><span data-ttu-id="2a8f7-152">Gibt Audio- und Videoinhalte wieder.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-152">Plays audio and video.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2a8f7-153">Bild-Viewer</span><span class="sxs-lookup"><span data-stu-id="2a8f7-153">Image viewers</span></span></td>
<td align="left"><span data-ttu-id="2a8f7-154">[Flip-Ansicht](../controls-and-patterns/flipview.md), [Bild](../controls-and-patterns/images-imagebrushes.md)</span><span class="sxs-lookup"><span data-stu-id="2a8f7-154">[Flip view](../controls-and-patterns/flipview.md), [image](../controls-and-patterns/images-imagebrushes.md)</span></span></td>
<td align="left"><span data-ttu-id="2a8f7-155">Zeigt Bilder an.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-155">Displays images.</span></span> <span data-ttu-id="2a8f7-156">Die „Flip-Ansicht“ zeigt Bilder nacheinander in einer Sammlung an, wie etwa Fotos in einem Album oder Elemente auf einer Produktdetailseite.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-156">The flip view displays images in a collection, such as photos in an album or items in a product details page, one image at a time.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="2a8f7-157">Listen</span><span class="sxs-lookup"><span data-stu-id="2a8f7-157">Lists</span></span></td>
<td align="left">[<span data-ttu-id="2a8f7-158">Dropdownliste, Listenfeld, Listen- und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="2a8f7-158">drop-down list, list box, list view and grid view</span></span>](../controls-and-patterns/lists.md)</td>
<td align="left"><span data-ttu-id="2a8f7-159">Stellt Elemente in einer interaktiven Liste oder einem Raster dar.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-159">Presents items in an interactive list or a grid.</span></span> <span data-ttu-id="2a8f7-160">Verwenden Sie diese Elemente, um Benutzern die Auswahl eines Films aus einer Liste mit Neuerscheinungen oder die Verwaltung von Inventar zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-160">Use these elements to let users select a movie from a list of new releases or manage an inventory.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="2a8f7-161">Text und Texteingabe</span><span class="sxs-lookup"><span data-stu-id="2a8f7-161">Text and text input</span></span></td>
<td align="left"><p><span data-ttu-id="2a8f7-162">[Textblock](../controls-and-patterns/text-block.md), [Textfeld](../controls-and-patterns/text-box.md), [Rich-Edit-Feld](../controls-and-patterns/rich-edit-box.md)</span><span class="sxs-lookup"><span data-stu-id="2a8f7-162">[Text block](../controls-and-patterns/text-block.md), [text box](../controls-and-patterns/text-box.md), [rich edit box](../controls-and-patterns/rich-edit-box.md)</span></span></p>
</td>
<td align="left"><span data-ttu-id="2a8f7-163">Zeigt Text an.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-163">Displays text.</span></span> <span data-ttu-id="2a8f7-164">Einige Elemente ermöglichen dem Benutzer das Bearbeiten von Text.</span><span class="sxs-lookup"><span data-stu-id="2a8f7-164">Some elements enable the user to edit text.</span></span> <span data-ttu-id="2a8f7-165">Weitere Informationen finden Sie unter [Textsteuerelemente](../controls-and-patterns/text-controls.md)</span><span class="sxs-lookup"><span data-stu-id="2a8f7-165">For more info, see [Text controls](../controls-and-patterns/text-controls.md)</span></span></td>
</tr>
</tbody>
</table>



 

 




