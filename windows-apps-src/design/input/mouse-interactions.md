---
author: Karl-Bridge-Microsoft
Description: Respond to mouse input in your apps by handling the same basic pointer events that you use for touch and pen input.
title: Mausinteraktionen
ms.assetid: C8A158EF-70A9-4BA2-A270-7D08125700AC
label: Mouse
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b79edc5499343498801081dd00554128c3b57eae
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5970167"
---
# <a name="mouse-interactions"></a><span data-ttu-id="77250-103">Mausinteraktionen</span><span class="sxs-lookup"><span data-stu-id="77250-103">Mouse interactions</span></span>


<span data-ttu-id="77250-104">Optimieren Sie das Design Ihrer UWP-Apps für die Toucheingabe, und freuen Sie sich über die standardmäßige allgemeine Unterstützung von Mausgeräten.</span><span class="sxs-lookup"><span data-stu-id="77250-104">Optimize your Universal Windows Platform (UWP) app design for touch input and get basic mouse support by default.</span></span>

 

![Maus](images/input-patterns/input-mouse.jpg)



<span data-ttu-id="77250-106">Die Mauseingabe eignet sich am besten für Benutzerinteraktionen, die Präzision beim Zeigen und Klicken erfordern.</span><span class="sxs-lookup"><span data-stu-id="77250-106">Mouse input is best suited for user interactions that require precision when pointing and clicking.</span></span> <span data-ttu-id="77250-107">Naturgemäß unterstützt die Benutzeroberfläche von Windows diese Präzision, auch wenn sie für die ungenaue Toucheingabe optimiert wurde.</span><span class="sxs-lookup"><span data-stu-id="77250-107">This inherent precision is naturally supported by the UI of Windows, which is optimized for the imprecise nature of touch.</span></span>

<span data-ttu-id="77250-108">Die Maus- und Toucheingabe unterscheiden sich dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (z.B. Streifen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="77250-108">Where mouse and touch input diverge is the ability for touch to more closely emulate the direct manipulation of UI elements through physical gestures performed directly on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span> <span data-ttu-id="77250-109">Manipulationen mit der Maus erfordern in der Regel einigen UI-Aufwand, wie z. B. die Verwendung von Handles für das Anpassen der Größe oder Drehen eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="77250-109">Manipulations with a mouse typically require some other UI affordance, such as the use of handles to resize or rotate an object.</span></span>

<span data-ttu-id="77250-110">In diesem Thema werden Designüberlegungen für Mausinteraktionen behandelt.</span><span class="sxs-lookup"><span data-stu-id="77250-110">This topic describes design considerations for mouse interactions.</span></span>

## <a name="the-uwp-app-mouse-language"></a><span data-ttu-id="77250-111">Die UWP-App-Sprache für Mauseingaben</span><span class="sxs-lookup"><span data-stu-id="77250-111">The UWP app mouse language</span></span>


<span data-ttu-id="77250-112">Ein kompakter Satz von Mausinteraktionen wird durchgängig im ganzen System verwendet.</span><span class="sxs-lookup"><span data-stu-id="77250-112">A concise set of mouse interactions are used consistently throughout the system.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="77250-113">Benennung</span><span class="sxs-lookup"><span data-stu-id="77250-113">Term</span></span></th>
<th align="left"><span data-ttu-id="77250-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77250-114">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="77250-115">Lernen durch Zeigen</span><span class="sxs-lookup"><span data-stu-id="77250-115">Hover to learn</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-116">Zeigen Sie auf ein Element, um weitere Informationen oder visuelle Hinweise (wie etwa QuickInfos) aufzurufen, ohne eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="77250-116">Hover over an element to display more detailed info or teaching visuals (such as a tooltip) without a commitment to an action.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="77250-117">Linksklick, um primäre Aktion auszuführen</span><span class="sxs-lookup"><span data-stu-id="77250-117">Left-click for primary action</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-118">Klicken Sie mit der linken Maustaste auf ein Element, um dessen primäre Aktion aufzurufen (z.B. das Starten einer App oder das Ausführen eines Befehls).</span><span class="sxs-lookup"><span data-stu-id="77250-118">Left-click an element to invoke its primary action (such as launching an app or executing a command).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="77250-119">Bildlauf, um Ansicht zu ändern</span><span class="sxs-lookup"><span data-stu-id="77250-119">Scroll to change view</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-120">Zeigen Sie Bildlaufleisten an, damit Benutzer in einem Inhaltsbereich nach oben, unten, links und rechts navigieren können.</span><span class="sxs-lookup"><span data-stu-id="77250-120">Display scroll bars to move up, down, left, and right within a content area.</span></span> <span data-ttu-id="77250-121">Benutzer können durch Klicken auf Bildlaufleisten oder Drehen des Mausrads einen Bildlauf durchführen.</span><span class="sxs-lookup"><span data-stu-id="77250-121">Users can scroll by clicking scroll bars or rotating the mouse wheel.</span></span> <span data-ttu-id="77250-122">Auf Bildlaufleisten kann die Position der aktuellen Ansicht innerhalb des Inhaltsbereichs angezeigt werden (durch das Schwenken bei der Fingereingabe wird eine ähnliche Benutzeroberfläche angezeigt).</span><span class="sxs-lookup"><span data-stu-id="77250-122">Scroll bars can indicate the location of the current view within the content area (panning with touch displays a similar UI).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="77250-123">Rechtsklick, um Auswahl zu treffen und Befehl auszuwählen</span><span class="sxs-lookup"><span data-stu-id="77250-123">Right-click to select and command</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-124">Klicken Sie mit der rechten Maustaste, um die Navigationsleiste (sofern verfügbar) und die App-Leiste mit globalen Befehlen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="77250-124">Right-click to display the navigation bar (if available) and the app bar with global commands.</span></span> <span data-ttu-id="77250-125">Klicken Sie mit der rechten Maustaste auf ein Element, um es auszuwählen und die App-Leiste mit Kontextbefehlen für das ausgewählte Element anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="77250-125">Right-click an element to select it and display the app bar with contextual commands for the selected element.</span></span></p>
<div class="alert"><span data-ttu-id="77250-126">
<strong>Hinweis:</strong>mit der rechten Maustaste, um ein Kontextmenü anzuzeigen, wenn die Auswahl oder der app-Leiste verfügbaren Befehle nicht gewünschte Benutzeroberflächenverhalten.</span><span class="sxs-lookup"><span data-stu-id="77250-126">
<strong>Note</strong>Right-click to display a context menu if selection or app bar commands are not appropriate UI behaviors.</span></span> <span data-ttu-id="77250-127">Wir empfehlen jedoch ausdrücklich, die App-Leiste für alle Befehlsverhalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="77250-127">But we strongly recommend that you use the app bar for all command behaviors.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="77250-128">Benutzeroberflächenbefehle zum Zoomen</span><span class="sxs-lookup"><span data-stu-id="77250-128">UI commands to zoom</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-129">Zeigen Sie Benutzeroberflächenbefehle auf der App-Leiste an (z.B. "+" und "-"), oder drücken Sie STRG und drehen Sie das Mausrad, um Zusammendrück- und Aufziehbewegungen zum Zoomen zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="77250-129">Display UI commands in the app bar (such as + and -), or press Ctrl and rotate mouse wheel, to emulate pinch and stretch gestures for zooming.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="77250-130">Benutzeroberflächenbefehle zum Drehen</span><span class="sxs-lookup"><span data-stu-id="77250-130">UI commands to rotate</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-131">Zeigen Sie Benutzeroberflächenbefehle auf der App-Leiste an, oder drücken Sie STRG+UMSCHALTTASTE, und drehen Sie das Mausrad, um die Drehbewegung zum Drehen zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="77250-131">Display UI commands in the app bar, or press Ctrl+Shift and rotate mouse wheel, to emulate the turn gesture for rotating.</span></span> <span data-ttu-id="77250-132">Drehen Sie das Gerät selbst, um den ganzen Bildschirm zu drehen.</span><span class="sxs-lookup"><span data-stu-id="77250-132">Rotate the device itself to rotate the entire screen.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="77250-133">Linksklick und ziehen, um neu anzuordnen</span><span class="sxs-lookup"><span data-stu-id="77250-133">Left-click and drag to rearrange</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-134">Klicken Sie mit der linken Maustaste auf ein Element, und ziehen Sie, um es zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="77250-134">Left-click and drag an element to move it.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="77250-135">Linksklick und ziehen, um Text auszuwählen</span><span class="sxs-lookup"><span data-stu-id="77250-135">Left-click and drag to select text</span></span></p></td>
<td align="left"><p><span data-ttu-id="77250-136">Klicken Sie mit der linken Maustaste auf auswählbaren Text, und ziehen Sie, um Text auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="77250-136">Left-click within selectable text and drag to select it.</span></span> <span data-ttu-id="77250-137">Doppelklicken Sie, um ein Wort auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="77250-137">Double-click to select a word.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="mouse-events"></a><span data-ttu-id="77250-138">Mausereignisse</span><span class="sxs-lookup"><span data-stu-id="77250-138">Mouse events</span></span>

<span data-ttu-id="77250-139">Reagieren Sie in Ihren Apps auf Mauseingaben, indem Sie die gleichen einfachen Zeigerereignisse behandeln, die Sie für Touch- und Stifteingaben verwenden.</span><span class="sxs-lookup"><span data-stu-id="77250-139">Respond to mouse input in your apps by handling the same basic pointer events that you use for touch and pen input.</span></span>

<span data-ttu-id="77250-140">Verwenden Sie [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911)-Ereignisse, um grundlegende Eingabefunktionen zu implementieren, ohne separaten Code für jedes Zeigereingabegerät schreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="77250-140">Use [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) events to implement basic input functionality without having to write code for each pointer input device.</span></span> <span data-ttu-id="77250-141">Sie können aber trotzdem die speziellen Funktionen jedes Geräts nutzen (z. B. die Ereignisse des Mausrads), indem Sie die Zeiger-, Gestik- und Manipulationsereignisse dieses Objekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="77250-141">However, you can still take advantage of the special capabilities of each device (such as mouse wheel events) using the pointer, gesture, and manipulation events of this object.</span></span>

<span data-ttu-id="77250-142">**Beispiele:** Diese Funktionalität in Aktion zu sehen in unserer [Beispiele](http://go.microsoft.com/fwlink/p/?LinkID=264996)wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="77250-142">**Samples:** See this functionality in action in our [app samples](http://go.microsoft.com/fwlink/p/?LinkID=264996).</span></span>


- [<span data-ttu-id="77250-143">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="77250-143">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)

- [<span data-ttu-id="77250-144">Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="77250-144">Input sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)

- [<span data-ttu-id="77250-145">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="77250-145">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231605)

## <a name="guidelines-for-visual-feedback"></a><span data-ttu-id="77250-146">Richtlinien für visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="77250-146">Guidelines for visual feedback</span></span>


-   <span data-ttu-id="77250-147">Wenn eine Maus erkannt wird (durch Bewegungs- oder Daraufzeigen-Ereignisse), zeigen Sie eine für Mausinteraktionen spezifische Benutzeroberfläche an, um auf vom Element verfügbar gemachte Funktionen hinzuweisen.</span><span class="sxs-lookup"><span data-stu-id="77250-147">When a mouse is detected (through move or hover events), show mouse-specific UI to indicate functionality exposed by the element.</span></span> <span data-ttu-id="77250-148">Wenn die Maus für eine bestimmte Zeit nicht bewegt wird oder der Benutzer eine Fingereingabeinteraktion auslöst, blenden Sie die für Mausinteraktionen spezifische Benutzeroberfläche schrittweise aus.</span><span class="sxs-lookup"><span data-stu-id="77250-148">If the mouse doesn't move for a certain amount of time, or if the user initiates a touch interaction, make the mouse UI gradually fade away.</span></span> <span data-ttu-id="77250-149">Somit bleibt die Benutzeroberfläche sauber und aufgeräumt.</span><span class="sxs-lookup"><span data-stu-id="77250-149">This keeps the UI clean and uncluttered.</span></span>
-   <span data-ttu-id="77250-150">Verwenden Sie nicht den Cursor für Zeigefeedback, das Feedback des Elements reicht aus (siehe Cursor unten).</span><span class="sxs-lookup"><span data-stu-id="77250-150">Don't use the cursor for hover feedback, the feedback provided by the element is sufficient (see Cursors below).</span></span>
-   <span data-ttu-id="77250-151">Zeigen Sie kein visuelles Feedback an, wenn ein Element keine Interaktionen unterstützt (z.B. statischer Text).</span><span class="sxs-lookup"><span data-stu-id="77250-151">Don't display visual feedback if an element doesn't support interaction (such as static text).</span></span>
-   <span data-ttu-id="77250-152">Verwenden Sie keine Fokusrechtecke für Mausinteraktionen.</span><span class="sxs-lookup"><span data-stu-id="77250-152">Don't use focus rectangles with mouse interactions.</span></span> <span data-ttu-id="77250-153">Diese sind ausschließlich für Tastaturinteraktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="77250-153">Reserve these for keyboard interactions.</span></span>
-   <span data-ttu-id="77250-154">Zeigen Sie für alle Elemente, die das gleiche Eingabeziel darstellen, das gleiche visuelle Feedback an.</span><span class="sxs-lookup"><span data-stu-id="77250-154">Display visual feedback concurrently for all elements that represent the same input target.</span></span>
-   <span data-ttu-id="77250-155">Stellen Sie Schaltflächen (z. B. „+“ und „-“) zur Verfügung, um fingereingabebasierte Manipulationen wie etwa Schwenken, Drehen, Zoomen usw. zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="77250-155">Provide buttons (such as + and -) for emulating touch-based manipulations such as panning, rotating, zooming, and so on.</span></span>

<span data-ttu-id="77250-156">Allgemeine Informationen zum visuellen Feedback finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="77250-156">For more general guidance on visual feedback, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>


## <a name="cursors"></a><span data-ttu-id="77250-157">Cursor</span><span class="sxs-lookup"><span data-stu-id="77250-157">Cursors</span></span>


<span data-ttu-id="77250-158">Für einen Mauszeiger ist eine Reihe von Standardcursor verfügbar.</span><span class="sxs-lookup"><span data-stu-id="77250-158">A set of standard cursors is available for a mouse pointer.</span></span> <span data-ttu-id="77250-159">Diese geben die primäre Aktion eines Elements an.</span><span class="sxs-lookup"><span data-stu-id="77250-159">These are used to indicate the primary action of an element.</span></span>

<span data-ttu-id="77250-160">Jedem Standardcursor ist ein entsprechendes Standardbild zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="77250-160">Each standard cursor has a corresponding default image associated with it.</span></span> <span data-ttu-id="77250-161">Benutzer einer App können das Standardbild, das einem Standardcursor zugewiesen ist, jederzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="77250-161">The user or an app can replace the default image associated with any standard cursor at any time.</span></span> <span data-ttu-id="77250-162">Geben Sie über die [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273)-Funktion die Abbildung eines Cursors an.</span><span class="sxs-lookup"><span data-stu-id="77250-162">Specify a cursor image through the [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273) function.</span></span>

<span data-ttu-id="77250-163">Beachten Sie beim Anpassen des Mauszeigers Folgendes:</span><span class="sxs-lookup"><span data-stu-id="77250-163">If you need to customize the mouse cursor:</span></span>

-   <span data-ttu-id="77250-164">Verwenden Sie immer den Pfeilcursor (</span><span class="sxs-lookup"><span data-stu-id="77250-164">Always use the arrow cursor (</span></span>![Pfeilcursor](images/cursor-arrow.png)<span data-ttu-id="77250-166">) für klickbare Elemente.</span><span class="sxs-lookup"><span data-stu-id="77250-166">) for clickable elements.</span></span> <span data-ttu-id="77250-167">Verwenden Sie den Zeigefingercursor (</span><span class="sxs-lookup"><span data-stu-id="77250-167">don't use the pointing hand cursor (</span></span>![Zeigefingercursor](images/cursor-pointinghand.png)<span data-ttu-id="77250-169">) nicht für Links oder andere interaktive Elemente.</span><span class="sxs-lookup"><span data-stu-id="77250-169">) for links or other interactive elements.</span></span> <span data-ttu-id="77250-170">Verwenden Sie stattdessen Zeigeeffekte (wie bereits beschrieben).</span><span class="sxs-lookup"><span data-stu-id="77250-170">Instead, use hover effects (described earlier).</span></span>
-   <span data-ttu-id="77250-171">Verwenden Sie den Textcursor (</span><span class="sxs-lookup"><span data-stu-id="77250-171">Use the text cursor (</span></span>![Textcursor](images/cursor-text.png)<span data-ttu-id="77250-173">) für auswählbaren Text.</span><span class="sxs-lookup"><span data-stu-id="77250-173">) for selectable text.</span></span>
-   <span data-ttu-id="77250-174">Verwenden Sie den Bewegungscursor (</span><span class="sxs-lookup"><span data-stu-id="77250-174">Use the move cursor (</span></span>![Bewegungscursor](images/cursor-move.png)<span data-ttu-id="77250-176">), wenn die primäre Aktion eine Bewegung ist (etwa beim Ziehen oder Zuschneiden).</span><span class="sxs-lookup"><span data-stu-id="77250-176">) when moving is the primary action (such as dragging or cropping).</span></span> <span data-ttu-id="77250-177">Verwenden Sie den Bewegungscursor nicht, wenn die primäre Aktion eine Navigationsaktion ist (etwa bei Start-Kacheln).</span><span class="sxs-lookup"><span data-stu-id="77250-177">Don't use the move cursor for elements where the primary action is navigation (such as Start tiles).</span></span>
-   <span data-ttu-id="77250-178">Verwenden Sie die Cursor für horizontale, vertikale und diagonale Größenänderung (</span><span class="sxs-lookup"><span data-stu-id="77250-178">Use the horizontal, vertical and diagonal resize cursors (</span></span>![Cursor für vertikale Größenänderung](images/cursor-vertical.png)<span data-ttu-id="77250-180">,</span><span class="sxs-lookup"><span data-stu-id="77250-180">,</span></span> ![Cursor für horizontale Größenänderung](images/cursor-horizontal.png)<span data-ttu-id="77250-182">,</span><span class="sxs-lookup"><span data-stu-id="77250-182">,</span></span> ![Cursor für diagonale Größenänderung (unten links, oben rechts)](images/cursor-diagonal2.png)<span data-ttu-id="77250-184">,</span><span class="sxs-lookup"><span data-stu-id="77250-184">,</span></span> ![Cursor für diagonale Größenänderung (oben links, unten rechts)](images/cursor-diagonal1.png)<span data-ttu-id="77250-186">), wenn die Größe eines Objekts geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="77250-186">), when an object is resizable.</span></span>
-   <span data-ttu-id="77250-187">Verwenden Sie den Handcursor (</span><span class="sxs-lookup"><span data-stu-id="77250-187">Use the grasping hand cursors (</span></span>![Handcursor (offen)](images/cursor-pan1.png)<span data-ttu-id="77250-189">,</span><span class="sxs-lookup"><span data-stu-id="77250-189">,</span></span> ![Handcursor (geschlossen)](images/cursor-pan2.png)<span data-ttu-id="77250-191">) beim Verschieben von Inhalt innerhalb einer Canvas (etwa bei einer Karte).</span><span class="sxs-lookup"><span data-stu-id="77250-191">) when panning content within a fixed canvas (such as a map).</span></span>

## <a name="related-articles"></a><span data-ttu-id="77250-192">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="77250-192">Related articles</span></span>

* [<span data-ttu-id="77250-193">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="77250-193">Handle pointer input</span></span>](handle-pointer-input.md)
* [<span data-ttu-id="77250-194">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="77250-194">Identify input devices</span></span>](identify-input-devices.md)

**<span data-ttu-id="77250-195">Beispiele</span><span class="sxs-lookup"><span data-stu-id="77250-195">Samples</span></span>**
* [<span data-ttu-id="77250-196">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="77250-196">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="77250-197">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="77250-197">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="77250-198">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="77250-198">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="77250-199">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="77250-199">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="77250-200">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="77250-200">Archive Samples</span></span>**
* [<span data-ttu-id="77250-201">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="77250-201">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="77250-202">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="77250-202">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="77250-203">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="77250-203">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="77250-204">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="77250-204">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231605)
 
 

 




