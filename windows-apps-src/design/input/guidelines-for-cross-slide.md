---
author: mijacobs
Description: Use cross-slide to support selection with the swipe gesture and drag (move) interactions with the slide gesture.
title: Richtlinien für Querziehen
ms.assetid: 897555e2-c567-4bbe-b600-553daeb223d5
ms.author: kbridge
ms.date: 10/25/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5c9234463ad011cc0b4d289bba9fe1ff1873ed46
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5986000"
---
# <a name="guidelines-for-cross-slide"></a><span data-ttu-id="6c0b8-103">Richtlinien für Querziehen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-103">Guidelines for cross-slide</span></span>




**<span data-ttu-id="6c0b8-104">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="6c0b8-104">Important APIs</span></span>**

-   [**<span data-ttu-id="6c0b8-105">CrossSliding</span><span class="sxs-lookup"><span data-stu-id="6c0b8-105">CrossSliding</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241942)
-   [**<span data-ttu-id="6c0b8-106">CrossSlideThresholds</span><span class="sxs-lookup"><span data-stu-id="6c0b8-106">CrossSlideThresholds</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241941)
-   [**<span data-ttu-id="6c0b8-107">Windows.UI.Input</span><span class="sxs-lookup"><span data-stu-id="6c0b8-107">Windows.UI.Input</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242084)

<span data-ttu-id="6c0b8-108">Verwenden Sie Querziehen, um Auswahlinteraktionen mit einer Streifbewegung und Ziehinteraktionen (Verschieben) mit einer Ziehbewegung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-108">Use cross-slide to support selection with the swipe gesture and drag (move) interactions with the slide gesture.</span></span>

## <a name="span-iddosanddontsspanspan-iddosanddontsspanspan-iddosanddontsspandos-and-donts"></a><span data-ttu-id="6c0b8-109"><span id="Dos_and_don_ts"></span><span id="dos_and_don_ts"></span><span id="DOS_AND_DON_TS"></span>Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-109"><span id="Dos_and_don_ts"></span><span id="dos_and_don_ts"></span><span id="DOS_AND_DON_TS"></span>Dos and don'ts</span></span>


-   <span data-ttu-id="6c0b8-110">Verwenden Sie das Querziehen für Listen oder Auflistungen, bei denen ein Bildlauf nur in eine Richtung möglich ist.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-110">Use cross-slide for lists or collections that scroll in a single direction.</span></span>
-   <span data-ttu-id="6c0b8-111">Verwenden Sie das Querziehen für die Elementauswahl, wenn die Tippinteraktion für andere Zwecke verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-111">Use cross-slide for item selection when the tap interaction is used for another purpose.</span></span>
-   <span data-ttu-id="6c0b8-112">Verwenden Sie das Querziehen nicht, um Elemente zu einer Warteschlange hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-112">Don't use cross-slide for adding items to a queue.</span></span>

## <a name="span-idadditionalusageguidancespanspan-idadditionalusageguidancespanspan-idadditionalusageguidancespanadditional-usage-guidance"></a><span data-ttu-id="6c0b8-113"><span id="Additional_usage_guidance"></span><span id="additional_usage_guidance"></span><span id="ADDITIONAL_USAGE_GUIDANCE"></span>Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="6c0b8-113"><span id="Additional_usage_guidance"></span><span id="additional_usage_guidance"></span><span id="ADDITIONAL_USAGE_GUIDANCE"></span>Additional usage guidance</span></span>


<span data-ttu-id="6c0b8-114">Auswahl und Ziehen sind nur in Inhaltsbereichen möglich, die in eine Richtung (vertikal oder horizontal) verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-114">Selection and drag are possible only within a content area that is pannable in one direction (vertical or horizontal).</span></span> <span data-ttu-id="6c0b8-115">Damit die Interaktion funktioniert, muss eine Verschiebungsrichtung arretiert sein, und die Bewegung muss senkrecht zur Verschiebungsrichtung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-115">For either interaction to work, one panning direction must be locked and the gesture must be performed in the direction perpendicular to the panning direction.</span></span>

<span data-ttu-id="6c0b8-116">Im Folgenden wird das Auswählen und Ziehen eines Objekts durch Querziehen veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-116">Here we demonstrate selecting and dragging an object using a cross-slide.</span></span> <span data-ttu-id="6c0b8-117">Die linke Abbildung zeigt, wie ein Element ausgewählt wird, wenn eine Streifbewegung eine Distanzschwelle nicht überschreitet, bevor der Kontakt aufgehoben und das Objekt losgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-117">The image on the left shows how an item is selected if a swipe gesture doesn't cross a distance threshold before the contact is lifted and the object released.</span></span> <span data-ttu-id="6c0b8-118">Die rechte Abbildung zeigt eine Ziehbewegung, die eine Distanzschwelle überschreitet und zum Ziehen des Objekts führt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-118">The image on the right shows a sliding gesture that crosses a distance threshold and results in the object being dragged.</span></span>

![Diagramm, das die Prozesse für Auswahl und Drag & Drop veranschaulicht](images/crossslide-mechanism.png)

<span data-ttu-id="6c0b8-120">Das folgende Diagramm zeigt Distanzschwellen, die bei der Interaktion des Querziehens verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-120">The threshold distances used by the cross-slide interaction are shown in the following diagram.</span></span>

![Screenshot der Prozesse für Auswahl und Drag & Drop](images/crossslide-threshold.png)

<span data-ttu-id="6c0b8-122">Damit die Verschiebungsfunktion erhalten bleibt, muss eine niedrige Schwelle von 2,7mm (ca. 10Pixel bei Zielauflösung) überschritten werden, bevor eine Auswahl- oder Ziehinteraktion aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-122">To preserve panning functionality, a small threshold of 2.7mm (approximately 10 pixels at target resolution) must be crossed before either a select or drag interaction is activated.</span></span> <span data-ttu-id="6c0b8-123">Anhand dieser niedrigen Schwelle kann das System zwischen Querziehen und Verschieben unterscheiden. Außerdem kann so eine Tippbewegung von Querziehen und Verschieben unterschieden werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-123">This small threshold helps the system to differentiate cross-sliding from panning, and also helps ensure that a tap gesture is distinguished from both cross-sliding and panning.</span></span>

<span data-ttu-id="6c0b8-124">Die folgende Abbildung zeigt, wie der Benutzer ein UI-Element berührt, den Finger beim Kontakt aber leicht nach unten bewegt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-124">This image shows how a user touches an element in the UI, but moves their finger down slightly at contact.</span></span> <span data-ttu-id="6c0b8-125">Ohne Schwelle würde die Interaktion aufgrund der anfänglichen vertikalen Bewegung als Querziehen interpretiert.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-125">With no threshold, the interaction would be interpreted as a cross-slide because of the initial vertical movement.</span></span> <span data-ttu-id="6c0b8-126">Dank der Schwelle wird die Bewegung korrekt als horizontales Verschieben interpretiert.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-126">With the threshold, the movement is interpreted correctly as horizontal panning.</span></span>

![Screenshot der Mehrdeutigkeitsvermeidungsschwelle für Auswahl und Drag&Drop](images/crossslide-threshold2.png)

<span data-ttu-id="6c0b8-128">Beachten Sie die folgenden Richtlinien, wenn Sie eine Querziehfunktion in Ihrer App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-128">Here are some guidelines to consider when including cross-slide functionality in your app.</span></span>

<span data-ttu-id="6c0b8-129">Verwenden Sie das Querziehen für Listen oder Auflistungen, bei denen ein Bildlauf nur in eine Richtung möglich ist.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-129">Use cross-slide for lists or collections that scroll in a single direction.</span></span> <span data-ttu-id="6c0b8-130">Weitere Informationen finden Sie unter [Hinzufügen von ListView-Steuerelementen](https://msdn.microsoft.com/library/windows/apps/hh465382).</span><span class="sxs-lookup"><span data-stu-id="6c0b8-130">For more information, see [Adding ListView controls](https://msdn.microsoft.com/library/windows/apps/hh465382).</span></span>

<span data-ttu-id="6c0b8-131">**Hinweis:** In Fällen, in denen der Inhaltsbereich in zwei Richtungen, z. B. einem Webbrowser oder e-Reader verschoben werden kann, zeitlich festgelegte Interaktion des drücken und halten sollte verwendet werden, um das Kontextmenü für Objekte wie Bilder und Links aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-131">**Note**In cases where the content area can be panned in two directions, such as web browsers or e-readers, the press-and-hold timed interaction should be used to invoke the context menu for objects such as images and hyperlinks.</span></span>

 

|                                                                                         |                                                                                         |
|-----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| ![Horizontal verschiebbare zweidimensionale Liste](images/groupedlistview1.png)                | ![Vertikal verschiebbare eindimensionale Liste](images/listviewlistlayout.png)                |
| <span data-ttu-id="6c0b8-134">Hier sehen Sie eine horizontal verschiebbare zweidimensionale Liste.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-134">A horizontally panning two-dimensional list.</span></span> <span data-ttu-id="6c0b8-135">Ziehen Sie vertikal, um ein Element auszuwählen oder zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-135">Drag vertically to select or move an item.</span></span> | <span data-ttu-id="6c0b8-136">Hier sehen Sie eine vertikal verschiebbare eindimensionale Liste.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-136">A vertically panning one-dimensional list.</span></span> <span data-ttu-id="6c0b8-137">Ziehen Sie horizontal, um ein Element auszuwählen oder zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-137">Drag horizontally to select or move an item.</span></span> |

 

### <span id="selection"></span><span id="SELECTION"></span>

**<span data-ttu-id="6c0b8-138">Auswählen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-138">Selecting</span></span>**

<span data-ttu-id="6c0b8-139">Beim Auswählen wird mindestens ein Objekt markiert, ohne es zu starten oder zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-139">Selection is the marking, without launching or activating, of one or more objects.</span></span> <span data-ttu-id="6c0b8-140">Diese Aktion entspricht einem einfachen Mausklick oder einem Mausklick mit gedrückter UMSCHALTTASTE auf mindestens ein Objekt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-140">This action is analogous to a single mouse click, or Shift key and mouse click, on one or more objects.</span></span>

<span data-ttu-id="6c0b8-141">Zum Auswählen durch Querziehen wird ein Element berührt und nach einer kurzen Interaktion des Ziehens wieder losgelassen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-141">Cross-slide selection is achieved by touching an element and releasing it after a short dragging interaction.</span></span> <span data-ttu-id="6c0b8-142">Bei dieser Methode entfallen sowohl der dedizierte Auswahlmodus als auch die zeitlich festgelegte Interaktion des Gedrückthaltens, die bei anderen Schnittstellen für die Fingereingabe erforderlich sind. Sie steht nicht in Konflikt mit der für die Aktivierung verwendeten Interaktion des Tippens.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-142">This method of selection dispenses with both the dedicated selection mode and the press-and-hold timed interaction required by other touch interfaces and does not conflict with the tap interaction for activation.</span></span>

<span data-ttu-id="6c0b8-143">Neben der Distanzschwelle gilt für das Auswählen durch Querziehen auch eine Beschränkung auf einen Schwellenbereich von 90°, wie im folgenden Diagramm veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-143">In addition to the distance threshold, cross-slide selection is constrained to a 90° threshold area, as shown in the following diagram.</span></span> <span data-ttu-id="6c0b8-144">Wenn das Objekt außerhalb dieses Bereichs gezogen wird, wird es nicht ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-144">If the object is dragged outside of this area, it is not selected.</span></span>

![Diagramm, das den Schwellenbereich für die Auswahl zeigt](images/crossslide-selection.png)

<span data-ttu-id="6c0b8-146">Die Interaktion des Querziehens wird durch eine zeitlich festgelegte Interaktion des Gedrückthaltens, auch als „Interaktion mit automatischem Einblenden“ bezeichnet, ergänzt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-146">The cross-slide interaction is supplemented by a press-and-hold timed interaction, also referred to as a "self-revealing" interaction.</span></span> <span data-ttu-id="6c0b8-147">Durch diese zusätzliche Interaktion wird eine Animation aktiviert, die zeigt, welche Aktion für das Objekt ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-147">This supplemental interaction activates an animation that indicates what action can be performed on the object.</span></span> <span data-ttu-id="6c0b8-148">Weitere Informationen zur Mehrdeutigkeitsvermeidungs-UI finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="6c0b8-148">For more information on disambiguation UI, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>

<span data-ttu-id="6c0b8-149">In den folgenden Screenshots wird die Funktionsweise der Animation mit automatischem Einblenden verdeutlicht.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-149">The following screen shots demonstrate how the self-revealing animation works.</span></span>

1.  <span data-ttu-id="6c0b8-150">Halten Sie das Element gedrückt, um die Animation für die Interaktion mit automatischem Einblenden auszulösen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-150">Press and hold to initiate the animation for the self-revealing interaction.</span></span> <span data-ttu-id="6c0b8-151">Der ausgewählte Zustand des Elements hat direkten Einfluss auf die durch die Animation eingeblendeten Inhalte: ein Häkchen bei aufgehobener Auswahl und kein Häkchen bei erfolgter Auswahl.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-151">The selected state of the item affects what is revealed by the animation: a check mark if unselected and no check mark if selected.</span></span>

    ![Screenshot eines Zustands ohne Auswahl](images/crossslide-selfreveal1.png)

2.  <span data-ttu-id="6c0b8-153">Wählen Sie das Element mit einer Streifbewegung (nach oben oder unten) aus.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-153">Select the item using the swipe gesture (up or down).</span></span>

    ![Screenshot der Animation für die Auswahl](images/crossslide-selfreveal2.png)

3.  <span data-ttu-id="6c0b8-155">Das Element ist nun ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-155">The item is now selected.</span></span> <span data-ttu-id="6c0b8-156">Setzen Sie das Auswahlverhalten mit der Streifbewegung zum Verschieben des Elements außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-156">Override the selection behavior using the slide gesture to move the item.</span></span>

    ![Screenshot der Animation für Drag & Drop](images/crossslide-selfreveal3.png)

<span data-ttu-id="6c0b8-158">Verwenden Sie in Apps, in denen das Auswählen die einzige Hauptaktion ist, einfaches Tippen für die Auswahl.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-158">Use a single tap for selection in applications where it is the only primary action.</span></span> <span data-ttu-id="6c0b8-159">Die Querziehanimation mit automatischem Einblenden wird angezeigt, um diese Funktion von der standardmäßigen Tippinteraktion für Aktivierung und Navigation zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-159">The cross-slide self-revealing animation is displayed to disambiguate this functionality from the standard tap interaction for activation and navigation.</span></span>

**<span data-ttu-id="6c0b8-160">Auswahlkorb</span><span class="sxs-lookup"><span data-stu-id="6c0b8-160">Selection basket</span></span>**

<span data-ttu-id="6c0b8-161">Der Auswahlkorb ist eine visuell unverwechselbare, dynamische Darstellung von Elementen, die aus der primären Liste oder Auflistung in der Anwendung ausgewählt wurden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-161">The selection basket is a visually distinct and dynamic representation of items that have been selected from the primary list or collection in the application.</span></span> <span data-ttu-id="6c0b8-162">Dieses Feature ist hilfreich, um den Überblick über ausgewählte Elemente zu behalten, und es sollte in Anwendungen verwendet werden, auf die Folgendes zutrifft:</span><span class="sxs-lookup"><span data-stu-id="6c0b8-162">This feature is useful for tracking selected items and should be used by applications where:</span></span>

-   <span data-ttu-id="6c0b8-163">Elemente können an mehreren Orten ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-163">Items can be selected from multiple locations.</span></span>
-   <span data-ttu-id="6c0b8-164">Es können mehrere Elemente ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-164">Many items can be selected.</span></span>
-   <span data-ttu-id="6c0b8-165">Einer Aktion oder einem Befehl wird die Auswahlliste zugrunde gelegt.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-165">An action or command relies upon the selection list.</span></span>

<span data-ttu-id="6c0b8-166">Der Inhalt des Auswahlkorbs bleibt über Aktionen und Befehle hinweg erhalten.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-166">The content of the selection basket persists across actions and commands.</span></span> <span data-ttu-id="6c0b8-167">Wenn Sie z.B. eine Serie von Fotos aus einer Galerie auswählen, in jedem Foto eine Farbkorrektur durchführen und die Fotos auf irgendeine Weise mit anderen teilen, bleibt die Auswahl der Elemente erhalten.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-167">For example, if you select a series of photographs from a gallery, apply a color correction to each photograph, and share the photographs in some fashion, the items remain selected.</span></span>

<span data-ttu-id="6c0b8-168">Wenn in einer Anwendung kein Auswahlkorb verwendet wird, sollte die aktuelle Auswahl nach einer Aktion oder einem Befehl gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-168">If no selection basket is used in an application, the current selection should be cleared after an action or command.</span></span> <span data-ttu-id="6c0b8-169">Wenn Sie z.B. einen Musiktitel in einer Wiedergabeliste auswählen und bewerten, sollte die Auswahl gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-169">For example, if you select a song from a play list and rate it, the selection should be cleared.</span></span>

<span data-ttu-id="6c0b8-170">Auch wenn kein Auswahlkorb verwendet und ein anderes Element in der Liste oder Auflistung aktiviert wird, sollte die aktuelle Auswahl gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-170">The current selection should also be cleared when no selection basket is used and another item in the list or collection is activated.</span></span> <span data-ttu-id="6c0b8-171">Wenn Sie z.B. eine Nachricht im Posteingang auswählen, wird das Vorschaufenster aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-171">For example, if you select an inbox message, the preview pane is updated.</span></span> <span data-ttu-id="6c0b8-172">Wählen Sie anschließend eine zweite Nachricht im Posteingang aus, wird die Auswahl der vorherigen Nachricht aufgehoben und das Vorschaufenster erneut aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-172">Then, if you select a second inbox message, the selection of the previous message is canceled and the preview pane is updated.</span></span>

**<span data-ttu-id="6c0b8-173">Warteschlangen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-173">Queues</span></span>**

<span data-ttu-id="6c0b8-174">Eine Warteschlange ist nicht mit der Liste im Auswahlkorb gleichzusetzen und sollte auch nicht so behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-174">A queue is not equivalent to the selection basket list and should not be treated as such.</span></span> <span data-ttu-id="6c0b8-175">Hier die wichtigsten Unterschiede:</span><span class="sxs-lookup"><span data-stu-id="6c0b8-175">The primary distinctions include:</span></span>

-   <span data-ttu-id="6c0b8-176">Die Liste der Elemente im Auswahlkorb ist nur eine visuelle Darstellung, während die Elemente in einer Warteschlange im Hinblick auf eine bestimmte Aktion zusammengestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-176">The list of items in the selection basket is only a visual representation; the items in a queue are assembled with a specific action in mind.</span></span>
-   <span data-ttu-id="6c0b8-177">Elemente können im Auswahlkorb nur einmal dargestellt werden, in einer Warteschlange hingegen mehrmals.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-177">Items can be represented only once in the selection basket but multiple times in a queue.</span></span>
-   <span data-ttu-id="6c0b8-178">Die Reihenfolge der Elemente im Auswahlkorb entspricht der Reihenfolge, in der sie ausgewählt wurden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-178">The order of items in the selection basket represents the order of selection.</span></span> <span data-ttu-id="6c0b8-179">Die Reihenfolge der Elemente in einer Warteschlange hängt unmittelbar mit der Funktion zusammen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-179">The order of items in a queue is directly related to functionality.</span></span>

<span data-ttu-id="6c0b8-180">Aus diesen Gründen sollte die Auswahlinteraktion durch Querziehen nicht verwendet werden, um Elemente zu einer Warteschlange hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-180">For these reasons, the cross-slide selection interaction should not be used to add items to a queue.</span></span> <span data-ttu-id="6c0b8-181">Zum Hinzufügen von Elementen zu einer Warteschlange sollte eine Ziehaktion ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-181">Instead, items should be added to a queue through a drag action.</span></span>

### <span id="draganddrop"></span><span id="DRAGANDDROP"></span>

**<span data-ttu-id="6c0b8-182">Ziehen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-182">Drag</span></span>**

<span data-ttu-id="6c0b8-183">Verwenden Sie eine Ziehbewegung, um Objekte von einer Position an eine andere zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-183">Use drag to move one or more objects from one location to another.</span></span>

<span data-ttu-id="6c0b8-184">Wenn mehrere Objekte verschoben werden müssen, geben Sie dem Benutzer die Möglichkeit, mehrere Elemente auszuwählen und anschließend gleichzeitig zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="6c0b8-184">If more than one object needs to be moved, let users select multiple items and then drag all at one time.</span></span>

## <a name="span-idrelatedtopicsspanrelated-articles"></a><span data-ttu-id="6c0b8-185"><span id="related_topics"></span>Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="6c0b8-185"><span id="related_topics"></span>Related articles</span></span>


**<span data-ttu-id="6c0b8-186">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6c0b8-186">Samples</span></span>**
* [<span data-ttu-id="6c0b8-187">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="6c0b8-187">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="6c0b8-188">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="6c0b8-188">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="6c0b8-189">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="6c0b8-189">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* <span data-ttu-id="6c0b8-190">[Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895)
**Archivbeispiele**</span><span class="sxs-lookup"><span data-stu-id="6c0b8-190">[Focus visuals sample](http://go.microsoft.com/fwlink/p/?LinkID=619895)
**Archive samples**</span></span>
* [<span data-ttu-id="6c0b8-191">Eingabe: Beispiel XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="6c0b8-191">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="6c0b8-192">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-192">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="6c0b8-193">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="6c0b8-193">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="6c0b8-194">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="6c0b8-194">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="6c0b8-195">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="6c0b8-195">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="6c0b8-196">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="6c0b8-196">Input: Windows 8 gestures sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="6c0b8-197">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="6c0b8-197">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="6c0b8-198">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="6c0b8-198">DirectX touch input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




