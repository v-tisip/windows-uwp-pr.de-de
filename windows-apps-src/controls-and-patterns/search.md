---
author: Jwmsft
Description: "Die Suche ist eine der besten Möglichkeiten, um Inhalte in Ihrer App zu finden. In diesem Artikel werden Elemente der Suche sowie Suchbereiche, die Implementierung und Beispiele für die Suche im Kontext behandelt."
title: "Suche und „Auf Seite suchen“"
ms.assetid: C328FAA3-F6AE-4970-8372-B413F1290C39
label: Search
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.openlocfilehash: 9a12e7490cc1cf7bd1aa65b694a3aeb345ba1128
ms.sourcegitcommit: 45490bd85e6f8d247a041841d547ecac2ff48250
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2017
---
# <a name="search-and-find-in-page"></a><span data-ttu-id="7ac1f-105">Suche und „Auf Seite suchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-105">Search and find-in-page</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="7ac1f-106">Die Suche ist eine der besten Möglichkeiten, um Inhalte in Ihrer App zu finden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-106">Search is one of the top ways users can find content in your app.</span></span> <span data-ttu-id="7ac1f-107">In diesem Artikel werden Elemente der Suche sowie Suchbereiche, die Implementierung und Beispiele für die Suche im Kontext behandelt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-107">The guidance in this article covers elements of the search experience, search scopes, implementation, and examples of search in context.</span></span>

> <span data-ttu-id="7ac1f-108">**Wichtige APIs**: [AutoSuggestBox-Klasse](https://msdn.microsoft.com/library/windows/apps/dn633874)</span><span class="sxs-lookup"><span data-stu-id="7ac1f-108">**Important APIs**: [AutoSuggestBox class](https://msdn.microsoft.com/library/windows/apps/dn633874)</span></span>

## <a name="elements-of-the-search-experience"></a><span data-ttu-id="7ac1f-109">Elemente der Suchfunktionalität</span><span class="sxs-lookup"><span data-stu-id="7ac1f-109">Elements of the search experience</span></span>


**<span data-ttu-id="7ac1f-110">Eingabe.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-110">Input.</span></span>**  <span data-ttu-id="7ac1f-111">Die Texteingabe ist der am häufigsten verwendete Suchmodus und steht daher bei diesem Leitfaden im Mittelpunkt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-111">Text is the most common mode of search input and is the focus of this guidance.</span></span> <span data-ttu-id="7ac1f-112">Andere gängige Eingabemodi sind Spracheingabe und Kamera. Für diese sind jedoch in der Regel eine Verknüpfung mit der Gerätehardware sowie ggf. zusätzliche Steuerelemente oder benutzerdefinierte UI-Elemente in der App erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-112">Other common input modes include voice and camera, but these typically require the ability to interface with device hardware and may require additional controls or custom UI within the app.</span></span>

**<span data-ttu-id="7ac1f-113">Nulleingabe.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-113">Zero input.</span></span>**  <span data-ttu-id="7ac1f-114">Nach der Aktivierung des Eingabefelds durch den Benutzer (aber noch vor der Texteingabe) können Sie eine sogenannte Nulleingabe-Canvas anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-114">Once the user has activated the input field, but before the user has entered text, you can display what's called a "zero input canvas."</span></span> <span data-ttu-id="7ac1f-115">Die Nulleingabe-Canvas wird häufig in der App-Canvas angezeigt, sodass der Inhalt durch [einen automatischen Vorschlag](auto-suggest-box.md) ersetzt wird, wenn der Benutzer mit der Eingabe der Abfrage beginnt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-115">The zero input canvas will commonly appear in the app canvas, so that [auto-suggest](auto-suggest-box.md) replaces this content when the user begins to input their query.</span></span> <span data-ttu-id="7ac1f-116">Für den Nulleingabezustand eignen sich beispielsweise der aktuelle Suchverlauf, populäre Suchabfragen, kontextbezogene Suchvorschläge sowie Hinweise und Tipps.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-116">Recent search history, trending searches, contextual search suggestions, hints and tips are all good candidates for the zero input state.</span></span>

![Beispiel für Cortana mit Nulleingabe-Canvas](images/search-cortana-example.png)

 

**<span data-ttu-id="7ac1f-118">Abfrageformulierung/automatischer Vorschlag.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-118">Query formulation/auto-suggest.</span></span>**  <span data-ttu-id="7ac1f-119">Die Abfrageformulierung ersetzt den Nulleingabeinhalt, sobald der Benutzer mit der Eingabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-119">Query formulation replaces zero input content as soon as the user begins to enter input.</span></span> <span data-ttu-id="7ac1f-120">Während der Eingabe einer Abfragezeichenfolge werden dem Benutzer kontinuierlich aktualisierte Abfragevorschläge oder Optionen zur Mehrdeutigkeitsvermeidung angezeigt, um die Eingabe zu beschleunigen und ihn bei der Formulierung einer geeigneten Abfrage zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-120">As the user enters a query string, they are provided with a continuously updated set of query suggestions or disambiguation options to help them expedite the input process and formulate an effective query.</span></span> <span data-ttu-id="7ac1f-121">Dieses Verhalten von Abfragevorschlägen ist in das [Steuerelement für automatische Vorschläge](auto-suggest-box.md) integriert und ermöglicht auch die Symbolanzeige innerhalb der Suche (beispielsweise ein Mikrofon oder ein Commit-Symbol).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-121">This behavior of query suggestions is built into the [auto-suggest control](auto-suggest-box.md), and is also a way to show the icon inside the search (like a microphone or a commit icon).</span></span> <span data-ttu-id="7ac1f-122">Jedes andere Verhalten muss von der App behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-122">Any behavior outside of this falls to the app.</span></span>

![example of query/formulation einen automatischen Vorschlag](images/search-autosuggest-example.png)

 

**<span data-ttu-id="7ac1f-124">Ergebnissatz.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-124">Results set.</span></span>**  <span data-ttu-id="7ac1f-125">Suchergebnisse werden üblicherweise direkt unter dem Eingabefeld der Suche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-125">Search results commonly appear directly under the search input field.</span></span> <span data-ttu-id="7ac1f-126">Dies ist zwar nicht zwingend erforderlich, die Gegenüberstellung von Eingabe und Ergebnissen bewahrt jedoch den Kontext und ermöglicht dem Kunden eine direkte Bearbeitung der vorherigen Abfrage oder die Eingabe einer neuen Abfrage.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-126">While this isn't a requirement, the juxtaposition of input and results maintains context and provides the user with immediate access to edit the previous query or enter a new query.</span></span> <span data-ttu-id="7ac1f-127">Dieser Zusammenhang kann noch weiter verdeutlicht werden, indem der Hinweistext durch die Abfrage ersetzt wird, auf die der Ergebnissatz zurückzuführen ist.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-127">This connection can be further communicated by replacing the hint text with the query that created the results set.</span></span>

<span data-ttu-id="7ac1f-128">Eine Möglichkeit für eine wirksame Bearbeitung der vorherigen Abfrage oder die Eingabe einer neuen Abfrage besteht darin, bei Reaktivierung des Felds die vorherige Abfrage hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-128">One method to enable efficient access to both edit the previous query and enter a new query is to highlight the previous query when the field is reactivated.</span></span> <span data-ttu-id="7ac1f-129">In diesem Fall ersetzt jede Tastatureingabe die vorherige Zeichenfolge, die Zeichenfolge bleibt jedoch erhalten, sodass der Benutzer einen Cursor platzieren und die vorherige Zeichenfolge bearbeiten oder anhängen kann.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-129">This way, any keystroke will replace the previous string, but the string is maintained so that the user can position a cursor to edit or append the previous string.</span></span>

<span data-ttu-id="7ac1f-130">Der Ergebnissatz kann zur bestmöglichen Vermittlung des Inhalts in einem beliebigen Format angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-130">The results set can appear in any form that best communicates the content.</span></span> <span data-ttu-id="7ac1f-131">Eine [Listenansicht](lists.md) ist ziemlich flexibel und für die meisten Suchvorgänge geeignet.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-131">A [list view](lists.md) provides a good deal of flexibility and is well-suited to most searches.</span></span> <span data-ttu-id="7ac1f-132">Eine Rasteransicht eignet sich gut für Bilder oder andere Medien, und eine Karte gibt Aufschluss über räumliche Verteilung.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-132">A grid view works well for images or other media, and a map can be used to communicate spatial distribution.</span></span>

## <a name="search-scopes"></a><span data-ttu-id="7ac1f-133">Suchbereiche</span><span class="sxs-lookup"><span data-stu-id="7ac1f-133">Search scopes</span></span>


<span data-ttu-id="7ac1f-134">Die Suche ist ein gängiges Feature, und die entsprechenden UI-Elemente begegnen dem Benutzer sowohl in der Shell als auch in vielen Apps.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-134">Search is a common feature, and users will encounter search UI in the shell and within many apps.</span></span> <span data-ttu-id="7ac1f-135">Sucheinstiegspunkte werden zwar in der Regel auf ähnliche Weise visualisiert, können aber Zugriff auf verschiedene Ergebnisse bieten – von breit gefächerten (Web- oder Gerätesuche) bis hin zu spezifischen Ergebnissen (Kontaktliste eines Benutzers).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-135">Although search entry points tend to be similarly visualized, they can provide access to results that range from broad (web or device searches) to narrow (a user's contact list).</span></span> <span data-ttu-id="7ac1f-136">Der Sucheinstiegspunkt muss dem gesuchten Inhalt gegenübergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-136">The search entry point should be juxtaposed against the content being searched.</span></span>

<span data-ttu-id="7ac1f-137">Im Anschluss finden Sie einige gängige Suchbereiche:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-137">Some common search scopes include:</span></span>

<span data-ttu-id="7ac1f-138">**Global** und **Kontext/Eingrenzung**</span><span class="sxs-lookup"><span data-stu-id="7ac1f-138">**Global** and **contextual/refine.**</span></span>  <span data-ttu-id="7ac1f-139">Übergreifende Suche für mehrere Quellen mit Cloud-basierten und lokalen Inhalten.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-139">Search across multiple sources of cloud and local content.</span></span> <span data-ttu-id="7ac1f-140">Zu den unterschiedlichen Ergebnisse zählen beispielsweise URLs, Dokumente, Medien, Aktionen und Apps.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-140">Varied results include URLs, documents, media, actions, apps, and more.</span></span>

**<span data-ttu-id="7ac1f-141">Web.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-141">Web.</span></span>**  <span data-ttu-id="7ac1f-142">Suche nach einem Webindex.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-142">Search a web index.</span></span> <span data-ttu-id="7ac1f-143">Die Ergebnisse können unter anderem Seiten, Entitäten und Antworten umfassen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-143">Results include pages, entities, and answers.</span></span>

**<span data-ttu-id="7ac1f-144">Eigene Inhalte.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-144">My stuff.</span></span>**  <span data-ttu-id="7ac1f-145">Übergreifende Suche für Geräte, Cloud, Soziogramme und mehr.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-145">Search across device(s), cloud, social graphs, and more.</span></span> <span data-ttu-id="7ac1f-146">Die Ergebnisse können variieren, sind jedoch durch die Verbindung mit Benutzerkonten eingegrenzt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-146">Results are varied, but are constrained by the connection to user account(s).</span></span>

<span data-ttu-id="7ac1f-147">Verwenden Sie Hinweistext, um den Suchbereich zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-147">Use hint text to communicate search scope.</span></span> <span data-ttu-id="7ac1f-148">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-148">Examples include:</span></span>

<span data-ttu-id="7ac1f-149">„Windows und das Web durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-149">"Search Windows and the Web"</span></span>

<span data-ttu-id="7ac1f-150">„Kontaktliste durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-150">"Search contacts list"</span></span>

<span data-ttu-id="7ac1f-151">„Postfach durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-151">"Search mailbox"</span></span>

<span data-ttu-id="7ac1f-152">„Einstellungen durchsuchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-152">"Search settings"</span></span>

<span data-ttu-id="7ac1f-153">„Ort suchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-153">"Search for a place"</span></span>

![Hinweistextbeispiel für die Suche](images/search-windowsandweb.png)

 

<span data-ttu-id="7ac1f-155">Durch eine effektive Vermittlung des Bereichs für den Sucheingabepunkt können Sie sicherstellen, dass die Suchfunktionen die Erwartungen erfüllen, die der Benutzer an sie stellt, und dass er sich nicht über die Suche ärgert.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-155">By effectively communicating the scope of a search input point, you can help to ensure that the user expectation will be met by the capabilities of the search you are performing and reduce the possibility of frustration.</span></span>

## <a name="implementation"></a><span data-ttu-id="7ac1f-156">Implementierung</span><span class="sxs-lookup"><span data-stu-id="7ac1f-156">Implementation</span></span>


<span data-ttu-id="7ac1f-157">Bei den meisten Apps empfiehlt sich die Verwendung eines Textfelds als Sucheinstiegspunkt, da es sich hierbei um ein markantes visuelles Element handelt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-157">For most apps, it's best to have a text input field as the search entry point, which provides a prominent visual footprint.</span></span> <span data-ttu-id="7ac1f-158">Darüber hinaus können Sie mit Hinweistext dazu beitragen, dass die Suchfunktion leichter zu finden und der Benutzer über den Suchbereich informiert ist.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-158">In addition, hint text helps with discoverability and communicating the search scope.</span></span> <span data-ttu-id="7ac1f-159">Wenn es sich bei der Suche eher um eine sekundäre Aktion handelt oder nur wenig Platz zur Verfügung steht, kann das Suchsymbol auch ohne das dazugehörige Eingabefeld als Einstiegspunkt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-159">When search is a more secondary action, or when space is constrained, the search icon can serve as an entry point without the accompanying input field.</span></span> <span data-ttu-id="7ac1f-160">Achten Sie bei Verwendung eines Symbols darauf, dass genügend Platz für ein modales Suchfeld verfügbar ist, wie in den Beispielen weiter unten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-160">When visualized as an icon, be sure that there's room for a modal search box, as seen in the below examples.</span></span>

<span data-ttu-id="7ac1f-161">Vor dem Klicken auf das Suchsymbol:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-161">Before clicking search icon:</span></span>

![example of a search icon und collapsed search box](images/search-icon-collapsed.png)

 

<span data-ttu-id="7ac1f-163">Nach dem Klicken auf das Suchsymbol:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-163">After clicking search icon:</span></span>

![example of a search icon und expunded search box](images/search-icon-expanded.png)

 

<span data-ttu-id="7ac1f-165">Als Einstiegspunkt für die Suche wird immer ein nach rechts geneigtes Lupensymbol verwendet.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-165">Search always uses a right-pointing magnifying glass glyph for the entry point.</span></span> <span data-ttu-id="7ac1f-166">Dabei ist das Symbol mit dem Hexadezimalzeichencode0xE0094 (Segoe UI Symbol; üblicherweise mit einem Schriftgrad von 15Epx) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-166">The glyph to use is Segoe UI Symbol, hex character code 0xE0094, and usually at 15 epx font size.</span></span>

<span data-ttu-id="7ac1f-167">Der Sucheinstiegspunkt kann in verschiedenen Bereichen platziert werden und so Aufschluss über Suchbereich und -kontext geben.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-167">The search entry point can be placed in a number of different areas, and its placement communicates both search scope and context.</span></span> <span data-ttu-id="7ac1f-168">Suchfunktionen, die übergreifende Ergebnisse für eine Umgebung oder Ergebnisse außerhalb der App sammeln, befinden sich üblicherweise auf der höchsten App-Chromebene. Hierzu zählen beispielsweise globale Befehlsleisten oder Navigationselemente.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-168">Searches that gather results from across an experience or external to the app are typically located within top-level app chrome, such as global command bars or navigation.</span></span>

<span data-ttu-id="7ac1f-169">Mit zunehmender Eingrenzung oder zunehmendem Kontextbezug des Suchbereichs wird die Platzierung in der Regel direkter mit dem zu suchenden Inhalt assoziiert (beispielsweise auf einer Canvas, bei einer Listenüberschrift oder innerhalb kontextbezogener Befehlsleisten).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-169">As the search scope becomes more narrow or contextual, the placement will typically be more directly associated with the content to be searched, such as on a canvas, as a list header, or within contextual command bars.</span></span> <span data-ttu-id="7ac1f-170">In jedem Fall muss der Zusammenhang zwischen Sucheingabe und Ergebnissen oder gefilterten Inhalten optisch deutlich gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-170">In all cases, the connection between search input and results or filtered content should be visually clear.</span></span>

<span data-ttu-id="7ac1f-171">Bei bildlauffähigen Listen empfiehlt es sich, darauf zu achten, dass die Sucheingabe immer sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-171">In the case of scrollable lists, it's helpful to always have search input be visible.</span></span> <span data-ttu-id="7ac1f-172">Wir empfehlen, die Sucheingabe zu verankern und so zu konfigurieren, dass der Bildlauf im Hintergrund stattfindet.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-172">We recommend making the search input sticky and have content scroll behind it.</span></span>

<span data-ttu-id="7ac1f-173">Die Funktion für Nulleingabe und Abfrageformulierung ist bei kontextbezogenen/eingegrenzten Suchvorgängen, bei denen die Liste in Echtzeit auf der Grundlage der Benutzereingabe gefiltert wird, optional.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-173">Zero input and query formulation functionality is optional for contextual/refine searches in which the list will be filtered in real-time by user input.</span></span> <span data-ttu-id="7ac1f-174">Hiervon ausgenommen sind Fälle, bei denen möglicherweise Abfrageformatierungsvorschläge verfügbar sind. Hierzu zählen beispielsweise Filteroptionen für den Posteingang (An:&lt;Eingabezeichenfolge&gt;, Von: &lt;Eingabezeichenfolge&gt;, Betreff: &lt;Eingabezeichenfolge&gt; usw.).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-174">Exceptions include cases where query formatting suggestions may be available, such as inbox filtering options (to:&lt;input string&gt;, from: &lt;input string&gt;, subject: &lt;input string&gt;, and so on).</span></span>

## <a name="example"></a><span data-ttu-id="7ac1f-175">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7ac1f-175">Example</span></span>


<span data-ttu-id="7ac1f-176">Die Beispiele in diesem Abschnitt zeigen die Suche im Kontext.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-176">The examples in this section show search placed in context.</span></span>

<span data-ttu-id="7ac1f-177">Suche als Aktion auf der Symbolleiste von Windows:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-177">Search as an action in the Windows tool bar:</span></span>

![Beispiel für die Suche als Aktion auf der Symbolleiste von Windows](images/search-toolbar-action.png)

 

<span data-ttu-id="7ac1f-179">Suche als Eingabe auf der App-Canvas:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-179">Search as an input on the app canvas:</span></span>

![Beispiel für die Suche auf der App-Canvas](images/search-canvas-contacts.png)

 

<span data-ttu-id="7ac1f-181">Suche in einem Navigationsbereich:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-181">Search in a navigation pane:</span></span>

![Beispiel für die Suche in einem Navigationsmenü](images/search-navmenu.png)

 

<span data-ttu-id="7ac1f-183">Inlinesuche eignet sich am besten für seltener verwendete oder stark kontextorientierte Suchvorgänge:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-183">Inline search is best reserved for cases where search is infrequently accessed or is highly contextual:</span></span>

![Beispiel für eine Inlinesuche](images/patterns-search-results-desktop.png)


## <a name="guidelines-for-find-in-page"></a><span data-ttu-id="7ac1f-185">Richtlinien für die Funktion „Auf Seite suchen“</span><span class="sxs-lookup"><span data-stu-id="7ac1f-185">Guidelines for find-in-page</span></span>


<span data-ttu-id="7ac1f-186">Die Funktion „Auf Seite suchen“ bietet Benutzern die Möglichkeit, im aktuellen Text nach Übereinstimmungen zu suchen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-186">Find-in-page enables users to find text matches in the current body of text.</span></span> <span data-ttu-id="7ac1f-187">Dokumentviewer, Leser und Browser sind die typischsten Apps, die die Funktionalität „Auf Seite suchen“ bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-187">Document viewers, readers, and browsers are the most typical apps that provide find-in-page.</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="7ac1f-188">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="7ac1f-188">Do's and don'ts</span></span>


-   <span data-ttu-id="7ac1f-189">Platzieren Sie eine Befehlsleiste in Ihrer App mit der Funktionalität „Auf Seite suchen“, damit Benutzer Suchvorgänge für Texte auf einer Seite ausführen können.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-189">Place a command bar in your app with find-in-page functionality to let the user search for on-page text.</span></span> <span data-ttu-id="7ac1f-190">Platzierungsdetails dazu finden Sie im Abschnitt „Beispiele“.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-190">For placement details, see the Examples section.</span></span>

    -   <span data-ttu-id="7ac1f-191">In Apps, die die Funktion „Auf Seite suchen“ zur Verfügung stellen, sollten sich alle notwendigen Steuerelemente in einer Befehlsleiste befinden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-191">Apps that provide find-in-page should have all necessary controls in a command bar.</span></span>
    -   <span data-ttu-id="7ac1f-192">Wenn Ihre App eine große Anzahl an Funktionen bereitstellt, die über "Auf Seite suchen" hinausgehen, können Sie eine **Suchschaltfläche** in der Befehlsleiste oberster Ebene als Einstiegspunkt zu einer weiteren Befehlsleiste Verfügung stellen, die alle Steuerelemente enthält, die zur Funktion "Auf Seite suchen" gehören.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-192">If your app includes a lot of functionality beyond find-in-page, you can provide a **Find** button in the top-level command bar as an entry point to another command bar that contains all of your find-in-page controls.</span></span>
    -   <span data-ttu-id="7ac1f-193">Die Befehlsleiste für „Auf Seite suchen“ sollte während einer Interaktion des Benutzers mit der Bildschirmtastatur sichtbar bleiben.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-193">The find-in-page command bar should remain visible when the user is interacting with the touch keyboard.</span></span> <span data-ttu-id="7ac1f-194">Die Bildschirmtastatur wird angezeigt, wenn ein Benutzer auf das Eingabefeld tippt.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-194">The touch keyboard appears when a user taps the input box.</span></span> <span data-ttu-id="7ac1f-195">Die Befehlsleiste für „Auf Seite suchen“ sollte nach oben rücken, damit sie nicht von der Bildschirmtastatur verdeckt wird.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-195">The find-in-page command bar should move up, so it's not obscured by the touch keyboard.</span></span>

    -   <span data-ttu-id="7ac1f-196">"Auf Seite suche" sollte während einer Benutzerinteraktion mit der Ansicht verfügbar bleiben.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-196">Find-in-page should remain available while the user interacts with the view.</span></span> <span data-ttu-id="7ac1f-197">Benutzer müssen mit dem momentan angezeigten Text interagieren, während sie die Funktion "Auf Seite suchen" verwenden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-197">Users need to interact with the in-view text while using find-in-page.</span></span> <span data-ttu-id="7ac1f-198">Es sollte den Benutzern beispielsweise möglich sein, in ein Dokument hinein- oder herauszuzoomen oder die Ansicht zu verschieben, um den Text zu lesen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-198">For example, users may want to zoom in or out of a document or pan the view to read the text.</span></span> <span data-ttu-id="7ac1f-199">Sobald der Benutzer mit der Verwendung von „Auf Seite suchen“ beginnt, sollte die Befehlsleiste verfügbar bleiben und die Schaltfläche **Schließen** bereitstellen, damit die Funktion "Auf Seite suchen" beendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-199">Once the user starts using find-in-page, the command bar should remain available with a **Close** button to exit find-in-page.</span></span>

    -   <span data-ttu-id="7ac1f-200">Aktivieren Sie die Tastenkombination (STRG+F).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-200">Enable the keyboard shortcut (CTRL+F).</span></span> <span data-ttu-id="7ac1f-201">Implementieren Sie die Tastenkombination STRG+F, um das schnelle Öffnen der Befehlsleiste für „Auf Seite suchen“ zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-201">Implement the keyboard shortcut CTRL+F to enable the user to invoke the find-in-page command bar quickly.</span></span>

    -   <span data-ttu-id="7ac1f-202">Binden Sie die Basiselemente der Funktion "Auf Seite suchen" ein.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-202">Include the basics of find-in-page functionality.</span></span> <span data-ttu-id="7ac1f-203">Hierbei handelt es sich um die UI-Elemente, die benötigt werden, um "Auf Seite suchen" zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-203">These are the UI elements that you need in order to implement find-in-page:</span></span>

        -   <span data-ttu-id="7ac1f-204">Eingabefeld</span><span class="sxs-lookup"><span data-stu-id="7ac1f-204">Input box</span></span>
        -   <span data-ttu-id="7ac1f-205">Die Schaltflächen "Zurück" und "Weiter"</span><span class="sxs-lookup"><span data-stu-id="7ac1f-205">Previous and Next buttons</span></span>
        -   <span data-ttu-id="7ac1f-206">Übereinstimmungszähler</span><span class="sxs-lookup"><span data-stu-id="7ac1f-206">A match count</span></span>
        -   <span data-ttu-id="7ac1f-207">Schließen (nur Desktop)</span><span class="sxs-lookup"><span data-stu-id="7ac1f-207">Close (desktop-only)</span></span>
    -   <span data-ttu-id="7ac1f-208">In der Ansicht sollten Übereinstimmungen hervorgehoben werden, und es sollte ein Bildlauf erfolgen, sodass die nächste Übereinstimmung auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-208">The view should highlight matches and scroll to show the next match on screen.</span></span> <span data-ttu-id="7ac1f-209">Die Schaltflächen **Zurück** und **Weiter** sowie Bildlaufleisten oder die direkte Manipulation mittels Fingereingabe ermöglichen den Benutzern die schnelle Navigation innerhalb des Dokuments.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-209">Users can move quickly through the document by using the **Previous** and **Next** buttons and by using scroll bars or direct manipulation with touch.</span></span>

    -   <span data-ttu-id="7ac1f-210">Funktionalität zum Suchen und Ersetzen sollte mit den Basisfunktionen von "Auf Seite suchen" zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-210">Find-and-replace functionality should work alongside the basic find-in-page functionality.</span></span> <span data-ttu-id="7ac1f-211">Sorgen Sie bei Apps, die eine Funktion zum Suchen und Ersetzen bereitstellen, dafür, dass sich diese Funktion und „Auf Seite suchen“ nicht gegenseitig behindern.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-211">For apps that have find-and-replace, ensure that find-in-page doesn't interfere with find-and-replace functionality.</span></span>

-   <span data-ttu-id="7ac1f-212">Fügen Sie einen Übereinstimmungszähler ein, damit der Benutzer weiß, wie viele Textübereinstimmungen auf der Seite vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-212">Include a match counter to indicate to the user the number of text matches there are on the page.</span></span>
-   <span data-ttu-id="7ac1f-213">Aktivieren Sie die Tastenkombination (STRG+F).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-213">Enable the keyboard shortcut (CTRL+F).</span></span>

## <a name="examples"></a><span data-ttu-id="7ac1f-214">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7ac1f-214">Examples</span></span>


<span data-ttu-id="7ac1f-215">Stellen Sie eine einfache Möglichkeit zur Verfügung, um das Feature „Auf Seite suchen“ zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-215">Provide an easy way to access the find-in-page feature.</span></span> <span data-ttu-id="7ac1f-216">In diesem Beispiel auf einer mobilen Benutzeroberfläche wird „Auf Seite suchen“ hinter zwei „Hinzufügen zu…“-Befehlen in einem erweiterbarem Menü angezeigt:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-216">In this example on a mobile UI, "Find on page" appears after two "Add to..." commands in an expandable menu:</span></span>

![„Auf Seite suchen“ (Beispiel 1)](images/findinpage-01.png)

 

<span data-ttu-id="7ac1f-218">Nach der Auswahl von „Auf Seite suchen“ gibt der Benutzer einen Suchbegriff ein.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-218">After selecting find-in-page, the user enters a search term.</span></span> <span data-ttu-id="7ac1f-219">Textvorschläge können angezeigt werden, wenn ein Suchbegriff eingegeben wird:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-219">Text suggestions can appear when a search term is being entered:</span></span>

![„Auf Seite suchen“ (Beispiel 2)](images/findinpage-02.png)

 

<span data-ttu-id="7ac1f-221">Wenn keine Textübereinstimmung in der Suche vorliegt, sollte die Textzeichenfolge „Keine Ergebnisse“ im Ergebnisfeld angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-221">If there isn't a text match in the search, a "No results" text string should appear in the results box:</span></span>

![„Auf Seite suchen“ (Beispiel 3)](images/findinpage-03.png)

 

<span data-ttu-id="7ac1f-223">Wenn eine Textübereinstimmung in der Suche vorliegt, sollte der erste Begriff in einer eindeutigen Farbe hervorgehoben werden, wobei die nachfolgenden Übereinstimmungen in einem dezenteren Ton derselben Farbpalette gehalten werden sollten, wie dies in diesem Beispiel ersichtlich ist:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-223">If there is a text match in the search, the first term should be highlighted in a distinct color, with succeeding matches in a more subtle tone of that same color palette, as seen in this example:</span></span>

![„Auf Seite suchen“ (Beispiel 4)](images/findinpage-04.png)

 

<span data-ttu-id="7ac1f-225">„Auf Seite suchen“ weist einen Übereinstimmungszähler auf:</span><span class="sxs-lookup"><span data-stu-id="7ac1f-225">Find-in-page has a match counter:</span></span>

![Beispiel des Suchindikators von „Auf Seite suchen“](images/findinpage-counter.png)




## **<a name="implementing-find-in-page"></a><span data-ttu-id="7ac1f-227">Implementieren von "Auf Seite suchen"</span><span class="sxs-lookup"><span data-stu-id="7ac1f-227">Implementing find-in-page</span></span>**

-   <span data-ttu-id="7ac1f-228">Bei Dokumentviewern, Lesern und Browsern handelt es sich um die wahrscheinlichsten App-Typen für die Bereitstellung von „Auf Seite suchen“, was Benutzern eine vollständige Bildschirmanzeige-/-leseerfahrung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-228">Document viewers, readers, and browsers are the likeliest app types to provide find-in-page, and enable the user to have a full screen viewing/reading experience.</span></span>
-   <span data-ttu-id="7ac1f-229">Die Funktion „Auf Seite suchen“ ist sekundär und sollte auf einer Befehlsleiste platziert werden.</span><span class="sxs-lookup"><span data-stu-id="7ac1f-229">Find-in-page functionality is secondary and should be located in a command bar.</span></span>

<span data-ttu-id="7ac1f-230">Weitere Informationen zum Hinzufügen von Befehlen zur Befehlsleiste finden Sie unter [Command bar](app-bars.md) (Befehlsleiste).</span><span class="sxs-lookup"><span data-stu-id="7ac1f-230">For more info about adding commands to your command bar, see [Command bar](app-bars.md).</span></span>

 


## <a name="related-articles"></a><span data-ttu-id="7ac1f-231">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="7ac1f-231">Related articles</span></span>

* [<span data-ttu-id="7ac1f-232">Feld mit automatischen Vorschlägen</span><span class="sxs-lookup"><span data-stu-id="7ac1f-232">Auto-suggest box</span></span>](auto-suggest-box.md)


 

 
