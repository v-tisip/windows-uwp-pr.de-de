---
author: Jwmsft
Description: Search is one of the top ways users can find content in your app. The guidance in this article covers elements of the search experience, search scopes, implementation, and examples of search in context.
title: Suche und „Auf Seite suchen“
ms.assetid: C328FAA3-F6AE-4970-8372-B413F1290C39
label: Search
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: b506b439ff98da873823bd586bb5388fe360b2ba
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7425365"
---
# <a name="search-and-find-in-page"></a><span data-ttu-id="d9b2d-103">Suche und „Auf Seite suchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-103">Search and find-in-page</span></span>

 

<span data-ttu-id="d9b2d-104">Die Suche ist eine der besten Möglichkeiten, um Inhalte in Ihrer App zu finden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-104">Search is one of the top ways users can find content in your app.</span></span> <span data-ttu-id="d9b2d-105">In diesem Artikel werden Elemente der Suche sowie Suchbereiche, die Implementierung und Beispiele für die Suche im Kontext behandelt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-105">The guidance in this article covers elements of the search experience, search scopes, implementation, and examples of search in context.</span></span>

> <span data-ttu-id="d9b2d-106">**Wichtige APIs**: [AutoSuggestBox-Klasse](https://msdn.microsoft.com/library/windows/apps/dn633874)</span><span class="sxs-lookup"><span data-stu-id="d9b2d-106">**Important APIs**: [AutoSuggestBox class](https://msdn.microsoft.com/library/windows/apps/dn633874)</span></span>

## <a name="elements-of-the-search-experience"></a><span data-ttu-id="d9b2d-107">Elemente der Suchfunktionalität</span><span class="sxs-lookup"><span data-stu-id="d9b2d-107">Elements of the search experience</span></span>


<span data-ttu-id="d9b2d-108">**Eingabe.** Text ist der am häufigsten verwendete Suchmodus und steht daher bei diesem Leitfaden im Mittelpunkt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-108">**Input.** Text is the most common mode of search input and is the focus of this guidance.</span></span> <span data-ttu-id="d9b2d-109">Andere gängige Eingabemodi sind Spracheingabe und Kamera. Für diese sind jedoch in der Regel eine Verknüpfung mit der Gerätehardware sowie ggf. zusätzliche Steuerelemente oder benutzerdefinierte UI-Elemente in der App erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-109">Other common input modes include voice and camera, but these typically require the ability to interface with device hardware and may require additional controls or custom UI within the app.</span></span>

<span data-ttu-id="d9b2d-110">**Eingabe NULL.** Nachdem der Benutzer das Eingabefeld aktiviert hat, jedoch bevor der Benutzer Text eingegeben hat, können Sie anzeigen, die sogenannten "Nulleingabe-Canvas."</span><span class="sxs-lookup"><span data-stu-id="d9b2d-110">**Zero input.** Once the user has activated the input field, but before the user has entered text, you can display what's called a "zero input canvas."</span></span> <span data-ttu-id="d9b2d-111">Die Nulleingabe-Canvas wird häufig in der App-Canvas angezeigt, sodass der Inhalt durch [einen automatischen Vorschlag](auto-suggest-box.md) ersetzt wird, wenn der Benutzer mit der Eingabe der Abfrage beginnt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-111">The zero input canvas will commonly appear in the app canvas, so that [auto-suggest](auto-suggest-box.md) replaces this content when the user begins to input their query.</span></span> <span data-ttu-id="d9b2d-112">Für den Nulleingabezustand eignen sich beispielsweise der aktuelle Suchverlauf, populäre Suchabfragen, kontextbezogene Suchvorschläge sowie Hinweise und Tipps.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-112">Recent search history, trending searches, contextual search suggestions, hints and tips are all good candidates for the zero input state.</span></span>

![Beispiel für Cortana mit Nulleingabe-Canvas](images/search-cortana-example.png)

 

<span data-ttu-id="d9b2d-114">**Abfrageformulierung/automatischer Vorschlag.** Abfrage abfrageformulierung ersetzt nulleingabeinhalt, sobald der Benutzer mit der Eingabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-114">**Query formulation/auto-suggest.** Query formulation replaces zero input content as soon as the user begins to enter input.</span></span> <span data-ttu-id="d9b2d-115">Während der Eingabe einer Abfragezeichenfolge werden dem Benutzer kontinuierlich aktualisierte Abfragevorschläge oder Optionen zur Mehrdeutigkeitsvermeidung angezeigt, um die Eingabe zu beschleunigen und ihn bei der Formulierung einer geeigneten Abfrage zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-115">As the user enters a query string, they are provided with a continuously updated set of query suggestions or disambiguation options to help them expedite the input process and formulate an effective query.</span></span> <span data-ttu-id="d9b2d-116">Dieses Verhalten von Abfragevorschlägen ist in das [Steuerelement für automatische Vorschläge](auto-suggest-box.md) integriert und ermöglicht auch die Symbolanzeige innerhalb der Suche (beispielsweise ein Mikrofon oder ein Commit-Symbol).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-116">This behavior of query suggestions is built into the [auto-suggest control](auto-suggest-box.md), and is also a way to show the icon inside the search (like a microphone or a commit icon).</span></span> <span data-ttu-id="d9b2d-117">Jedes andere Verhalten muss von der App behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-117">Any behavior outside of this falls to the app.</span></span>

![example of query/formulation einen automatischen Vorschlag](images/search-autosuggest-example.png)

 

<span data-ttu-id="d9b2d-119">**Führt Satz.** Suchergebnisse häufig direkt unter dem Eingabefeld der Suche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-119">**Results set.** Search results commonly appear directly under the search input field.</span></span> <span data-ttu-id="d9b2d-120">Dies ist zwar nicht zwingend erforderlich, die Gegenüberstellung von Eingabe und Ergebnissen bewahrt jedoch den Kontext und ermöglicht dem Kunden eine direkte Bearbeitung der vorherigen Abfrage oder die Eingabe einer neuen Abfrage.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-120">While this isn't a requirement, the juxtaposition of input and results maintains context and provides the user with immediate access to edit the previous query or enter a new query.</span></span> <span data-ttu-id="d9b2d-121">Dieser Zusammenhang kann noch weiter verdeutlicht werden, indem der Hinweistext durch die Abfrage ersetzt wird, auf die der Ergebnissatz zurückzuführen ist.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-121">This connection can be further communicated by replacing the hint text with the query that created the results set.</span></span>

<span data-ttu-id="d9b2d-122">Eine Möglichkeit für eine wirksame Bearbeitung der vorherigen Abfrage oder die Eingabe einer neuen Abfrage besteht darin, bei Reaktivierung des Felds die vorherige Abfrage hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-122">One method to enable efficient access to both edit the previous query and enter a new query is to highlight the previous query when the field is reactivated.</span></span> <span data-ttu-id="d9b2d-123">In diesem Fall ersetzt jede Tastatureingabe die vorherige Zeichenfolge, die Zeichenfolge bleibt jedoch erhalten, sodass der Benutzer einen Cursor platzieren und die vorherige Zeichenfolge bearbeiten oder anhängen kann.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-123">This way, any keystroke will replace the previous string, but the string is maintained so that the user can position a cursor to edit or append the previous string.</span></span>

<span data-ttu-id="d9b2d-124">Der Ergebnissatz kann zur bestmöglichen Vermittlung des Inhalts in einem beliebigen Format angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-124">The results set can appear in any form that best communicates the content.</span></span> <span data-ttu-id="d9b2d-125">Eine [Listenansicht](lists.md) ist ziemlich flexibel und für die meisten Suchvorgänge geeignet.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-125">A [list view](lists.md) provides a good deal of flexibility and is well-suited to most searches.</span></span> <span data-ttu-id="d9b2d-126">Eine Rasteransicht eignet sich gut für Bilder oder andere Medien, und eine Karte gibt Aufschluss über räumliche Verteilung.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-126">A grid view works well for images or other media, and a map can be used to communicate spatial distribution.</span></span>

## <a name="search-scopes"></a><span data-ttu-id="d9b2d-127">Suchbereiche</span><span class="sxs-lookup"><span data-stu-id="d9b2d-127">Search scopes</span></span>


<span data-ttu-id="d9b2d-128">Die Suche ist ein gängiges Feature, und die entsprechenden UI-Elemente begegnen dem Benutzer sowohl in der Shell als auch in vielen Apps.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-128">Search is a common feature, and users will encounter search UI in the shell and within many apps.</span></span> <span data-ttu-id="d9b2d-129">Sucheinstiegspunkte werden zwar in der Regel auf ähnliche Weise visualisiert, können aber Zugriff auf verschiedene Ergebnisse bieten – von breit gefächerten (Web- oder Gerätesuche) bis hin zu spezifischen Ergebnissen (Kontaktliste eines Benutzers).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-129">Although search entry points tend to be similarly visualized, they can provide access to results that range from broad (web or device searches) to narrow (a user's contact list).</span></span> <span data-ttu-id="d9b2d-130">Der Sucheinstiegspunkt muss dem gesuchten Inhalt gegenübergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-130">The search entry point should be juxtaposed against the content being searched.</span></span>

<span data-ttu-id="d9b2d-131">Im Anschluss finden Sie einige gängige Suchbereiche:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-131">Some common search scopes include:</span></span>

<span data-ttu-id="d9b2d-132">**Global** und **Kontext/Eingrenzung**Übergreifende Suche für mehrere Quellen mit Cloud-basierten und lokalen Inhalten.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-132">**Global** and **contextual/refine.** Search across multiple sources of cloud and local content.</span></span> <span data-ttu-id="d9b2d-133">Zu den unterschiedlichen Ergebnisse zählen beispielsweise URLs, Dokumente, Medien, Aktionen und Apps.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-133">Varied results include URLs, documents, media, actions, apps, and more.</span></span>

<span data-ttu-id="d9b2d-134">**Web.** Suche nach einem Webindex.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-134">**Web.** Search a web index.</span></span> <span data-ttu-id="d9b2d-135">Die Ergebnisse können unter anderem Seiten, Entitäten und Antworten umfassen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-135">Results include pages, entities, and answers.</span></span>

<span data-ttu-id="d9b2d-136">**Eigene Inhalte.** Suche über Geräte, Cloud, soziogramme und mehr.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-136">**My stuff.** Search across device(s), cloud, social graphs, and more.</span></span> <span data-ttu-id="d9b2d-137">Die Ergebnisse können variieren, sind jedoch durch die Verbindung mit Benutzerkonten eingegrenzt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-137">Results are varied, but are constrained by the connection to user account(s).</span></span>

<span data-ttu-id="d9b2d-138">Verwenden Sie Hinweistext, um den Suchbereich zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-138">Use hint text to communicate search scope.</span></span> <span data-ttu-id="d9b2d-139">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-139">Examples include:</span></span>

<span data-ttu-id="d9b2d-140">„Windows und das Web durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-140">"Search Windows and the Web"</span></span>

<span data-ttu-id="d9b2d-141">„Kontaktliste durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-141">"Search contacts list"</span></span>

<span data-ttu-id="d9b2d-142">„Postfach durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-142">"Search mailbox"</span></span>

<span data-ttu-id="d9b2d-143">„Einstellungen durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-143">"Search settings"</span></span>

<span data-ttu-id="d9b2d-144">„Ort suchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-144">"Search for a place"</span></span>

![Hinweistextbeispiel für die Suche](images/search-windowsandweb.png)

 

<span data-ttu-id="d9b2d-146">Durch eine effektive Vermittlung des Bereichs für den Sucheingabepunkt können Sie sicherstellen, dass die Suchfunktionen die Erwartungen erfüllen, die der Benutzer an sie stellt, und dass er sich nicht über die Suche ärgert.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-146">By effectively communicating the scope of a search input point, you can help to ensure that the user expectation will be met by the capabilities of the search you are performing and reduce the possibility of frustration.</span></span>

## <a name="implementation"></a><span data-ttu-id="d9b2d-147">Implementierung</span><span class="sxs-lookup"><span data-stu-id="d9b2d-147">Implementation</span></span>


<span data-ttu-id="d9b2d-148">Bei den meisten Apps empfiehlt sich die Verwendung eines Textfelds als Sucheinstiegspunkt, da es sich hierbei um ein markantes visuelles Element handelt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-148">For most apps, it's best to have a text input field as the search entry point, which provides a prominent visual footprint.</span></span> <span data-ttu-id="d9b2d-149">Darüber hinaus können Sie mit Hinweistext dazu beitragen, dass die Suchfunktion leichter zu finden und der Benutzer über den Suchbereich informiert ist.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-149">In addition, hint text helps with discoverability and communicating the search scope.</span></span> <span data-ttu-id="d9b2d-150">Wenn es sich bei der Suche eher um eine sekundäre Aktion handelt oder nur wenig Platz zur Verfügung steht, kann das Suchsymbol auch ohne das dazugehörige Eingabefeld als Einstiegspunkt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-150">When search is a more secondary action, or when space is constrained, the search icon can serve as an entry point without the accompanying input field.</span></span> <span data-ttu-id="d9b2d-151">Achten Sie bei Verwendung eines Symbols darauf, dass genügend Platz für ein modales Suchfeld verfügbar ist, wie in den Beispielen weiter unten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-151">When visualized as an icon, be sure that there's room for a modal search box, as seen in the below examples.</span></span>

<span data-ttu-id="d9b2d-152">Vor dem Klicken auf das Suchsymbol:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-152">Before clicking search icon:</span></span>

![example of a search icon und collapsed search box](images/search-icon-collapsed.png)

 

<span data-ttu-id="d9b2d-154">Nach dem Klicken auf das Suchsymbol:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-154">After clicking search icon:</span></span>

![example of a search icon und expunded search box](images/search-icon-expanded.png)

 

<span data-ttu-id="d9b2d-156">Als Einstiegspunkt für die Suche wird immer ein nach rechts geneigtes Lupensymbol verwendet.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-156">Search always uses a right-pointing magnifying glass glyph for the entry point.</span></span> <span data-ttu-id="d9b2d-157">Dabei ist das Symbol mit dem Hexadezimalzeichencode0xE0094 (Segoe UI Symbol; üblicherweise mit einem Schriftgrad von 15Epx) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-157">The glyph to use is Segoe UI Symbol, hex character code 0xE0094, and usually at 15 epx font size.</span></span>

<span data-ttu-id="d9b2d-158">Der Sucheinstiegspunkt kann in verschiedenen Bereichen platziert werden und so Aufschluss über Suchbereich und -kontext geben.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-158">The search entry point can be placed in a number of different areas, and its placement communicates both search scope and context.</span></span> <span data-ttu-id="d9b2d-159">Suchfunktionen, die übergreifende Ergebnisse für eine Umgebung oder Ergebnisse außerhalb der App sammeln, befinden sich üblicherweise auf der höchsten App-Chromebene. Hierzu zählen beispielsweise globale Befehlsleisten oder Navigationselemente.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-159">Searches that gather results from across an experience or external to the app are typically located within top-level app chrome, such as global command bars or navigation.</span></span>

<span data-ttu-id="d9b2d-160">Mit zunehmender Eingrenzung oder zunehmendem Kontextbezug des Suchbereichs wird die Platzierung in der Regel direkter mit dem zu suchenden Inhalt assoziiert (beispielsweise auf einer Canvas, bei einer Listenüberschrift oder innerhalb kontextbezogener Befehlsleisten).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-160">As the search scope becomes more narrow or contextual, the placement will typically be more directly associated with the content to be searched, such as on a canvas, as a list header, or within contextual command bars.</span></span> <span data-ttu-id="d9b2d-161">In jedem Fall muss der Zusammenhang zwischen Sucheingabe und Ergebnissen oder gefilterten Inhalten optisch deutlich gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-161">In all cases, the connection between search input and results or filtered content should be visually clear.</span></span>

<span data-ttu-id="d9b2d-162">Bei bildlauffähigen Listen empfiehlt es sich, darauf zu achten, dass die Sucheingabe immer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-162">In the case of scrollable lists, it's helpful to always have search input be visible.</span></span> <span data-ttu-id="d9b2d-163">Wir empfehlen, die Sucheingabe zu verankern und so zu konfigurieren, dass der Bildlauf im Hintergrund stattfindet.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-163">We recommend making the search input sticky and have content scroll behind it.</span></span>

<span data-ttu-id="d9b2d-164">Die Funktion für Nulleingabe und Abfrageformulierung ist bei kontextbezogenen/eingegrenzten Suchvorgängen, bei denen die Liste in Echtzeit auf der Grundlage der Benutzereingabe gefiltert wird, optional.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-164">Zero input and query formulation functionality is optional for contextual/refine searches in which the list will be filtered in real-time by user input.</span></span> <span data-ttu-id="d9b2d-165">Hiervon ausgenommen sind Fälle, bei denen möglicherweise Abfrageformatierungsvorschläge verfügbar sind. Hierzu zählen beispielsweise Filteroptionen für den Posteingang (An:&lt;Eingabezeichenfolge&gt;, Von: &lt;Eingabezeichenfolge&gt;, Betreff: &lt;Eingabezeichenfolge&gt; usw.).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-165">Exceptions include cases where query formatting suggestions may be available, such as inbox filtering options (to:&lt;input string&gt;, from: &lt;input string&gt;, subject: &lt;input string&gt;, and so on).</span></span>

## <a name="example"></a><span data-ttu-id="d9b2d-166">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d9b2d-166">Example</span></span>


<span data-ttu-id="d9b2d-167">Die Beispiele in diesem Abschnitt zeigen die Suche im Kontext.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-167">The examples in this section show search placed in context.</span></span>

<span data-ttu-id="d9b2d-168">Suche als Aktion auf der Symbolleiste von Windows:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-168">Search as an action in the Windows tool bar:</span></span>

![Beispiel für die Suche als Aktion auf der Symbolleiste von Windows](images/search-toolbar-action.png)

 

<span data-ttu-id="d9b2d-170">Suche als Eingabe auf der App-Canvas:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-170">Search as an input on the app canvas:</span></span>

![Beispiel für die Suche auf der App-Canvas](images/search-canvas-contacts.png)

 

<span data-ttu-id="d9b2d-172">Suche in einem Navigationsbereich:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-172">Search in a navigation pane:</span></span>

![Beispiel für die Suche in einem Navigationsmenü](images/search-navmenu.png)

 

<span data-ttu-id="d9b2d-174">Inlinesuche eignet sich am besten für seltener verwendete oder stark kontextorientierte Suchvorgänge:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-174">Inline search is best reserved for cases where search is infrequently accessed or is highly contextual:</span></span>

![Beispiel für eine Inlinesuche](images/patterns-search-results-desktop.png)


## <a name="guidelines-for-find-in-page"></a><span data-ttu-id="d9b2d-176">Richtlinien für die Funktion „Auf Seite suchen“</span><span class="sxs-lookup"><span data-stu-id="d9b2d-176">Guidelines for find-in-page</span></span>


<span data-ttu-id="d9b2d-177">Die Funktion „Auf Seite suchen“ bietet Benutzern die Möglichkeit, im aktuellen Text nach Übereinstimmungen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-177">Find-in-page enables users to find text matches in the current body of text.</span></span> <span data-ttu-id="d9b2d-178">Dokumentviewer, Leser und Browser sind die typischsten Apps, die die Funktionalität „Auf Seite suchen“ bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-178">Document viewers, readers, and browsers are the most typical apps that provide find-in-page.</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="d9b2d-179">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="d9b2d-179">Do's and don'ts</span></span>


-   <span data-ttu-id="d9b2d-180">Platzieren Sie eine Befehlsleiste in Ihrer App mit der Funktionalität „Auf Seite suchen“, damit Benutzer Suchvorgänge für Texte auf einer Seite ausführen können.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-180">Place a command bar in your app with find-in-page functionality to let the user search for on-page text.</span></span> <span data-ttu-id="d9b2d-181">Platzierungsdetails dazu finden Sie im Abschnitt „Beispiele“.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-181">For placement details, see the Examples section.</span></span>

    -   <span data-ttu-id="d9b2d-182">In Apps, die die Funktion „Auf Seite suchen“ zur Verfügung stellen, sollten sich alle notwendigen Steuerelemente in einer Befehlsleiste befinden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-182">Apps that provide find-in-page should have all necessary controls in a command bar.</span></span>
    -   <span data-ttu-id="d9b2d-183">Wenn Ihre App eine große Anzahl an Funktionen bereitstellt, die über "Auf Seite suchen" hinausgehen, können Sie eine **Suchschaltfläche** in der Befehlsleiste oberster Ebene als Einstiegspunkt zu einer weiteren Befehlsleiste Verfügung stellen, die alle Steuerelemente enthält, die zur Funktion "Auf Seite suchen" gehören.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-183">If your app includes a lot of functionality beyond find-in-page, you can provide a **Find** button in the top-level command bar as an entry point to another command bar that contains all of your find-in-page controls.</span></span>
    -   <span data-ttu-id="d9b2d-184">Die Befehlsleiste für „Auf Seite suchen“ sollte während einer Interaktion des Benutzers mit der Bildschirmtastatur sichtbar bleiben.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-184">The find-in-page command bar should remain visible when the user is interacting with the touch keyboard.</span></span> <span data-ttu-id="d9b2d-185">Die Bildschirmtastatur wird angezeigt, wenn ein Benutzer auf das Eingabefeld tippt.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-185">The touch keyboard appears when a user taps the input box.</span></span> <span data-ttu-id="d9b2d-186">Die Befehlsleiste für „Auf Seite suchen“ sollte nach oben rücken, damit sie nicht von der Bildschirmtastatur verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-186">The find-in-page command bar should move up, so it's not obscured by the touch keyboard.</span></span>

    -   <span data-ttu-id="d9b2d-187">"Auf Seite suchen" sollte während einer Benutzerinteraktion mit der Ansicht verfügbar bleiben.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-187">Find-in-page should remain available while the user interacts with the view.</span></span> <span data-ttu-id="d9b2d-188">Benutzer müssen mit dem momentan angezeigten Text interagieren, während sie die Funktion "Auf Seite suchen" verwenden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-188">Users need to interact with the in-view text while using find-in-page.</span></span> <span data-ttu-id="d9b2d-189">Es sollte den Benutzern beispielsweise möglich sein, in ein Dokument hinein- oder herauszuzoomen oder die Ansicht zu verschieben, um den Text zu lesen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-189">For example, users may want to zoom in or out of a document or pan the view to read the text.</span></span> <span data-ttu-id="d9b2d-190">Sobald der Benutzer mit der Verwendung von „Auf Seite suchen“ beginnt, sollte die Befehlsleiste verfügbar bleiben und die Schaltfläche **Schließen** bereitstellen, damit die Funktion "Auf Seite suchen" beendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-190">Once the user starts using find-in-page, the command bar should remain available with a **Close** button to exit find-in-page.</span></span>

    -   <span data-ttu-id="d9b2d-191">Aktivieren Sie die Tastenkombination (STRG+F).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-191">Enable the keyboard shortcut (CTRL+F).</span></span> <span data-ttu-id="d9b2d-192">Implementieren Sie die Tastenkombination STRG+F, um das schnelle Öffnen der Befehlsleiste für „Auf Seite suchen“ zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-192">Implement the keyboard shortcut CTRL+F to enable the user to invoke the find-in-page command bar quickly.</span></span>

    -   <span data-ttu-id="d9b2d-193">Binden Sie die Basiselemente der Funktion "Auf Seite suchen" ein.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-193">Include the basics of find-in-page functionality.</span></span> <span data-ttu-id="d9b2d-194">Hierbei handelt es sich um die UI-Elemente, die benötigt werden, um "Auf Seite suchen" zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-194">These are the UI elements that you need in order to implement find-in-page:</span></span>

        -   <span data-ttu-id="d9b2d-195">Eingabefeld</span><span class="sxs-lookup"><span data-stu-id="d9b2d-195">Input box</span></span>
        -   <span data-ttu-id="d9b2d-196">Die Schaltflächen "Zurück" und "Weiter"</span><span class="sxs-lookup"><span data-stu-id="d9b2d-196">Previous and Next buttons</span></span>
        -   <span data-ttu-id="d9b2d-197">Übereinstimmungszähler</span><span class="sxs-lookup"><span data-stu-id="d9b2d-197">A match count</span></span>
        -   <span data-ttu-id="d9b2d-198">Schließen (nur Desktop)</span><span class="sxs-lookup"><span data-stu-id="d9b2d-198">Close (desktop-only)</span></span>
    -   <span data-ttu-id="d9b2d-199">In der Ansicht sollten Übereinstimmungen hervorgehoben werden, und es sollte ein Bildlauf erfolgen, sodass die nächste Übereinstimmung auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-199">The view should highlight matches and scroll to show the next match on screen.</span></span> <span data-ttu-id="d9b2d-200">Die Schaltflächen **Zurück** und **Weiter** sowie Bildlaufleisten oder die direkte Manipulation mittels Fingereingabe ermöglichen den Benutzern die schnelle Navigation innerhalb des Dokuments.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-200">Users can move quickly through the document by using the **Previous** and **Next** buttons and by using scroll bars or direct manipulation with touch.</span></span>

    -   <span data-ttu-id="d9b2d-201">Funktionalität zum Suchen und Ersetzen sollte mit den Basisfunktionen von "Auf Seite suchen" zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-201">Find-and-replace functionality should work alongside the basic find-in-page functionality.</span></span> <span data-ttu-id="d9b2d-202">Sorgen Sie bei Apps, die eine Funktion zum Suchen und Ersetzen bereitstellen, dafür, dass sich diese Funktion und „Auf Seite suchen“ nicht gegenseitig behindern.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-202">For apps that have find-and-replace, ensure that find-in-page doesn't interfere with find-and-replace functionality.</span></span>

-   <span data-ttu-id="d9b2d-203">Fügen Sie einen Übereinstimmungszähler ein, damit der Benutzer weiß, wie viele Textübereinstimmungen auf der Seite vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-203">Include a match counter to indicate to the user the number of text matches there are on the page.</span></span>
-   <span data-ttu-id="d9b2d-204">Aktivieren Sie die Tastenkombination (STRG+F).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-204">Enable the keyboard shortcut (CTRL+F).</span></span>

## <a name="examples"></a><span data-ttu-id="d9b2d-205">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d9b2d-205">Examples</span></span>


<span data-ttu-id="d9b2d-206">Stellen Sie eine einfache Möglichkeit zur Verfügung, um das Feature „Auf Seite suchen“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-206">Provide an easy way to access the find-in-page feature.</span></span> <span data-ttu-id="d9b2d-207">In diesem Beispiel auf einer mobilen Benutzeroberfläche wird „Auf Seite suchen“ hinter zwei „Hinzufügen zu…“-Befehlen in einem erweiterbarem Menü angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-207">In this example on a mobile UI, "Find on page" appears after two "Add to..." commands in an expandable menu:</span></span>

![„Auf Seite suchen“ (Beispiel 1)](images/findinpage-01.png)

 

<span data-ttu-id="d9b2d-209">Nach der Auswahl von „Auf Seite suchen“ gibt der Benutzer einen Suchbegriff ein.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-209">After selecting find-in-page, the user enters a search term.</span></span> <span data-ttu-id="d9b2d-210">Textvorschläge können angezeigt werden, wenn ein Suchbegriff eingegeben wird:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-210">Text suggestions can appear when a search term is being entered:</span></span>

![„Auf Seite suchen“ (Beispiel 2)](images/findinpage-02.png)

 

<span data-ttu-id="d9b2d-212">Wenn keine Textübereinstimmung in der Suche vorliegt, sollte die Textzeichenfolge „Keine Ergebnisse“ im Ergebnisfeld angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-212">If there isn't a text match in the search, a "No results" text string should appear in the results box:</span></span>

![„Auf Seite suchen“ (Beispiel 3)](images/findinpage-03.png)

 

<span data-ttu-id="d9b2d-214">Wenn eine Textübereinstimmung in der Suche vorliegt, sollte der erste Begriff in einer eindeutigen Farbe hervorgehoben werden, wobei die nachfolgenden Übereinstimmungen in einem dezenteren Ton derselben Farbpalette gehalten werden sollten, wie dies in diesem Beispiel ersichtlich ist:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-214">If there is a text match in the search, the first term should be highlighted in a distinct color, with succeeding matches in a more subtle tone of that same color palette, as seen in this example:</span></span>

![„Auf Seite suchen“ (Beispiel 4)](images/findinpage-04.png)

 

<span data-ttu-id="d9b2d-216">„Auf Seite suchen“ weist einen Übereinstimmungszähler auf:</span><span class="sxs-lookup"><span data-stu-id="d9b2d-216">Find-in-page has a match counter:</span></span>

![Beispiel des Suchindikators von „Auf Seite suchen“](images/findinpage-counter.png)




## **<a name="implementing-find-in-page"></a><span data-ttu-id="d9b2d-218">Implementieren von "Auf Seite suchen"</span><span class="sxs-lookup"><span data-stu-id="d9b2d-218">Implementing find-in-page</span></span>**

-   <span data-ttu-id="d9b2d-219">Bei Dokumentviewern, Lesern und Browsern handelt es sich um die wahrscheinlichsten App-Typen für die Bereitstellung von „Auf Seite suchen“, was Benutzern eine vollständige Bildschirmanzeige-/-leseerfahrung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-219">Document viewers, readers, and browsers are the likeliest app types to provide find-in-page, and enable the user to have a full screen viewing/reading experience.</span></span>
-   <span data-ttu-id="d9b2d-220">Die Funktion „Auf Seite suchen“ ist sekundär und sollte auf einer Befehlsleiste platziert werden.</span><span class="sxs-lookup"><span data-stu-id="d9b2d-220">Find-in-page functionality is secondary and should be located in a command bar.</span></span>

<span data-ttu-id="d9b2d-221">Weitere Informationen zum Hinzufügen von Befehlen zur Befehlsleiste finden Sie unter [Command bar](app-bars.md) (Befehlsleiste).</span><span class="sxs-lookup"><span data-stu-id="d9b2d-221">For more info about adding commands to your command bar, see [Command bar](app-bars.md).</span></span>

 


## <a name="related-articles"></a><span data-ttu-id="d9b2d-222">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="d9b2d-222">Related articles</span></span>

* [<span data-ttu-id="d9b2d-223">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="d9b2d-223">Auto-suggest box</span></span>](auto-suggest-box.md)


 

 
