---
author: Karl-Bridge-Microsoft
Description: This topic describes the new Windows UI for selecting and manipulating text, images, and controls and provides user experience guidelines that should be considered when using these new selection and manipulation mechanisms in your UWP app.
title: Auswählen von Text und Bildern
ms.assetid: d973ffd8-602e-47b5-ab0b-4b2a964ec53d
label: Selecting text and images
template: detail.hbs
keywords: Tastatur, Text, Eingabe, Benutzerinteraktionen
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 32d8e7d858ff28a6ef6a9af517e0a584c6106cd5
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6977211"
---
# <a name="selecting-text-and-images"></a><span data-ttu-id="36b3f-103">Auswählen von Text und Bildern</span><span class="sxs-lookup"><span data-stu-id="36b3f-103">Selecting text and images</span></span>


<span data-ttu-id="36b3f-104">In diesem Artikel wird das Auswählen und Bearbeiten von Text, Bildern und Steuerelementen beschrieben. Außerdem enthält er Richtlinien für die Benutzeroberfläche, die Sie bei der Verwendung dieser Mechanismen in Ihren Apps berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="36b3f-104">This article describes selecting and manipulating text, images, and controls and provides user experience guidelines that should be considered when using these mechanisms in your apps.</span></span>

> <span data-ttu-id="36b3f-105">**Wichtige APIs**: [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084)</span><span class="sxs-lookup"><span data-stu-id="36b3f-105">**Important APIs**: [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br242084)</span></span>
 


## <a name="dos-and-donts"></a><span data-ttu-id="36b3f-106">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="36b3f-106">Dos and don'ts</span></span>


-   <span data-ttu-id="36b3f-107">Verwenden Sie Schriftartglyphen, wenn Sie Ihre eigene Ziehelement-UI implementieren.</span><span class="sxs-lookup"><span data-stu-id="36b3f-107">Use font glyphs when implementing your own gripper UI.</span></span> <span data-ttu-id="36b3f-108">Das Ziehelement ist eine Kombination aus zwei systemweit verfügbaren SegoeUI-Schriftarten.</span><span class="sxs-lookup"><span data-stu-id="36b3f-108">The gripper is a combination of two Segoe UI fonts that are available system-wide.</span></span> <span data-ttu-id="36b3f-109">Die Verwendung von Schriftressourcen vereinfacht das Rendering bei unterschiedlichen DPI-Einstellungen und funktioniert gut mit den verschiedenen UI-Skalierungsebenen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-109">Using font resources simplifies rendering issues at different dpi and works well with the various UI scaling plateaus.</span></span> <span data-ttu-id="36b3f-110">Ihre Ziehelemente sollten alle die folgenden Benutzeroberflächenmerkmale aufweisen:</span><span class="sxs-lookup"><span data-stu-id="36b3f-110">When implementing your own grippers, they should share the following UI traits:</span></span>

    -   <span data-ttu-id="36b3f-111">Kreisform</span><span class="sxs-lookup"><span data-stu-id="36b3f-111">Circular shape</span></span>
    -   <span data-ttu-id="36b3f-112">Sichtbar auf jedem Hintergrund</span><span class="sxs-lookup"><span data-stu-id="36b3f-112">Visible against any background</span></span>
    -   <span data-ttu-id="36b3f-113">Einheitliche Größe</span><span class="sxs-lookup"><span data-stu-id="36b3f-113">Consistent size</span></span>
-   <span data-ttu-id="36b3f-114">Fügen Sie um auswählbaren Inhalt einen Rand für die Ziehelement-UI hinzu.</span><span class="sxs-lookup"><span data-stu-id="36b3f-114">Provide a margin around the selectable content to accommodate the gripper UI.</span></span> <span data-ttu-id="36b3f-115">Falls Ihre App die Textauswahl in einem Bereich ohne Verschiebung/Bildlauf ermöglicht, sollten Sie einen Rand lassen, der an der linken und rechten Seite halb so groß ist wie das Ziehelement und an der oberen und unteren Seite so groß wie die Höhe des Zielelements (siehe folgende Abbildungen).</span><span class="sxs-lookup"><span data-stu-id="36b3f-115">If your app enables text selection in a region that doesn't pan/scroll, allow a 1/2 gripper margin on the left and right sides of the text area and 1 gripper height on the top and bottom sides of the text area (as shown in the following images).</span></span> <span data-ttu-id="36b3f-116">Dadurch wird sichergestellt, dass die gesamte Ziehelement-UI für den Benutzer sichtbar ist, und unbeabsichtigte Interaktionen mit anderen randbasierten Benutzeroberflächen werden minimiert.</span><span class="sxs-lookup"><span data-stu-id="36b3f-116">This ensures that the entire gripper UI is exposed to the user and minimizes unintended interactions with other edge-based UI.</span></span>

    ![Ränder des Textauswahlziehelements](images/textselection-gripper-margins.png)

-   <span data-ttu-id="36b3f-118">Blenden Sie die Ziehelement-UI während der Interaktion aus.</span><span class="sxs-lookup"><span data-stu-id="36b3f-118">Hide grippers UI during interaction.</span></span> <span data-ttu-id="36b3f-119">So können Sie verhindern, dass die Interaktion durch die Ziehelemente behindert wird.</span><span class="sxs-lookup"><span data-stu-id="36b3f-119">Eliminates occlusion by the grippers during the interaction.</span></span> <span data-ttu-id="36b3f-120">Dies ist hilfreich, wenn ein Ziehelement nicht vollständig vom Finger verdeckt wird oder mehrere Ziehelemente für die Textauswahl vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="36b3f-120">This is useful when a gripper isn't completely obscured by the finger or there are multiple text selection grippers.</span></span> <span data-ttu-id="36b3f-121">Dadurch werden visuelle Fehler beim Anzeigen untergeordneter Fenster verhindert.</span><span class="sxs-lookup"><span data-stu-id="36b3f-121">This eliminates visual artifacts when displaying child windows.</span></span>

-   <span data-ttu-id="36b3f-122">Die Auswahl von UI-Elementen wie Steuerelementen, Beschriftungen, Bildern, geschützten Inhalten usw. sollte nicht möglich sein.</span><span class="sxs-lookup"><span data-stu-id="36b3f-122">Don't allow selection of UI elements such as controls, labels, images, proprietary content, and so on.</span></span> <span data-ttu-id="36b3f-123">In Windows-Apps ist die Auswahl normalerweise nur in bestimmten Steuerelementen möglich.</span><span class="sxs-lookup"><span data-stu-id="36b3f-123">Typically, Windows applications allow selection only within specific controls.</span></span> <span data-ttu-id="36b3f-124">Steuerelemente wie Schaltflächen, Beschriftungen und Logos sind nicht auswählbar.</span><span class="sxs-lookup"><span data-stu-id="36b3f-124">Controls such as buttons, labels, and logos are not selectable.</span></span> <span data-ttu-id="36b3f-125">Beurteilen Sie, ob die Auswahl ein Problem für die App darstellt, und identifizieren Sie gegebenenfalls die Bereiche der UI, in denen keine Auswahl möglich sein sollte.</span><span class="sxs-lookup"><span data-stu-id="36b3f-125">Assess whether selection is an issue for your app and, if so, identify the areas of the UI where selection should be prohibited.</span></span> 

## <a name="additional-usage-guidance"></a><span data-ttu-id="36b3f-126">Weitere Hinweise zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="36b3f-126">Additional usage guidance</span></span>


<span data-ttu-id="36b3f-127">Für die Auswahl und Manipulation von Text ergeben sich durch Fingereingabeinteraktionen besonders leicht Probleme für die Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="36b3f-127">Text selection and manipulation is particularly susceptible to user experience challenges introduced by touch interactions.</span></span> <span data-ttu-id="36b3f-128">Eingaben über Maus, Zeichen-/Tablettstift und Tastatur sind sehr präzise: Ein Mausklick oder ein Kontakt mit dem Zeichen- bzw. Tablettstift ist in der Regel einem einzigen Pixel zugeordnet, und eine Taste wird gedrückt oder nicht gedrückt.</span><span class="sxs-lookup"><span data-stu-id="36b3f-128">Mouse, pen/stylus, and keyboard input are highly granular: a mouse click or pen/stylus contact is typically mapped to a single pixel, and a key is pressed or not pressed.</span></span> <span data-ttu-id="36b3f-129">Die Fingereingabe ist weniger präzise. Es ist schwierig, die gesamte Oberfläche einer Fingerspitze einer bestimmten x-y-Position auf dem Bildschirm zuzuordnen, um ein Caretzeichen exakt im Text zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="36b3f-129">Touch input is not granular; it's difficult to map the entire surface of a fingertip to a specific x-y location on the screen to place a text caret accurately.</span></span>

**<span data-ttu-id="36b3f-130">Überlegungen und Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="36b3f-130">Considerations and recommendations</span></span>**

<span data-ttu-id="36b3f-131">Verwenden Sie die integrierten Steuerelemente der sprachframeworks in Windowsto-Build-apps, die die vollständige Plattform interaktionsmöglichkeiten für Benutzer, einschließlich Auswahl- und manipulationsverhalten – zu bieten.</span><span class="sxs-lookup"><span data-stu-id="36b3f-131">Use the built-in controls exposed through the language frameworks in Windowsto build apps that provide the full platform user interaction experience, including selection and manipulation behaviors.</span></span> <span data-ttu-id="36b3f-132">Die Interaktionsfunktionen der integrierten Steuerelemente sollten daher für die meisten UWP-Apps ausreichen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-132">You'll find the interaction functionality of the built-in controls sufficient for the majority of UWP apps.</span></span>

<span data-ttu-id="36b3f-133">Bei Verwendung der standardmäßigen UWP-Textsteuerelemente können die in diesem Thema beschriebenen Auswahlverhalten und visuellen Elemente nicht angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="36b3f-133">When using standard UWP text controls, the selection behaviors and visuals described in this topic cannot be customized.</span></span>

**<span data-ttu-id="36b3f-134">Textauswahl</span><span class="sxs-lookup"><span data-stu-id="36b3f-134">Text selection</span></span>**

<span data-ttu-id="36b3f-135">Wenn Ihre app eine benutzerdefinierte Benutzeroberfläche, die die Textauswahl unterstützt erfordert, wird empfohlen, dass die Windowsselection hier beschriebenen Auswahlverhalten.</span><span class="sxs-lookup"><span data-stu-id="36b3f-135">If your app requires a custom UI that supports text selection, we recommend that you follow the Windowsselection behaviors described here.</span></span>

**<span data-ttu-id="36b3f-136">Bearbeitbare und nicht bearbeitbare Inhalte</span><span class="sxs-lookup"><span data-stu-id="36b3f-136">Editable and non-editable content</span></span>**


<span data-ttu-id="36b3f-137">Bei der Fingereingabe werden Auswahlinteraktionen hauptsächlich durch Bewegungen ausgeführt, z.B. Tippen, um einen Einfügecursor zu setzen oder ein Wort auszuwählen, und Ziehen, um eine Auswahl zu ändern.</span><span class="sxs-lookup"><span data-stu-id="36b3f-137">With touch, selection interactions are performed primarily through gestures such as a tap to set an insertion cursor or select a word, and a slide to modify a selection.</span></span> <span data-ttu-id="36b3f-138">Wie bei anderen Interaktionen Windowstouch zeitlich festgelegte Interaktionen sind beschränkt auf das Drücken und Gedrückthaltebewegung Anzeigen einer informationsbenutzeroberfläche auf.</span><span class="sxs-lookup"><span data-stu-id="36b3f-138">As with other Windowstouch interactions, timed interactions are limited to the press and hold gesture to display informational UI.</span></span> <span data-ttu-id="36b3f-139">Weitere Informationen finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="36b3f-139">For more information, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>

<span data-ttu-id="36b3f-140">Windowsrecognizes zwei möglichen Zustände für Auswahl Interaktionen, bearbeitbare und nicht bearbeitbare und Auswahl-UI, Feedback und Funktionalität entsprechend angepasst.</span><span class="sxs-lookup"><span data-stu-id="36b3f-140">Windowsrecognizes two possible states for selection interactions, editable and non-editable, and adjusts selection UI, feedback, and functionality accordingly.</span></span>

**<span data-ttu-id="36b3f-141">Bearbeitbare Inhalte</span><span class="sxs-lookup"><span data-stu-id="36b3f-141">Editable content</span></span>**

<span data-ttu-id="36b3f-142">Durch Tippen in der linken Hälfte eines Worts wird der Cursor links neben dem Wort platziert, durch Tippen in der rechten Hälfte wird er rechts neben dem Wort platziert.</span><span class="sxs-lookup"><span data-stu-id="36b3f-142">Tapping within the left half of a word places the cursor to the immediate left of the word, while tapping within the right half places the cursor to the immediate right of the word.</span></span>

<span data-ttu-id="36b3f-143">Im folgenden Bild wird veranschaulicht, wie Sie einen anfänglichen Einfügecursor mit Ziehelement platzieren, indem Sie in die Nähe des Anfangs oder Endes eines Worts tippen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-143">The following image demonstrates how to place an initial insertion cursor with gripper by tapping near the beginning or ending of a word.</span></span>

![Tippen (oder drücken und halten) Sie links neben ein Wort, um ein Caretzeichen und ein Ziehelement am Anfang des Worts zu platzieren.](images/textselection-place-caret.png)

<span data-ttu-id="36b3f-146">Im folgenden Bild wird veranschaulicht, wie Sie eine Auswahl durch Ziehen des Ziehelements anpassen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-146">The following image demonstrates how to adjust a selection by dragging the gripper.</span></span>

![Ziehen Sie das Ziehelement in eine beliebige Richtung, um die Auswahl anzupassen (das erste Ziehelement bleibt verankert, und ein zweites Ziehelement wird angezeigt).](images/adjust-selection.png)

<span data-ttu-id="36b3f-149">Im folgenden Bild wird veranschaulicht, wie Sie das Kontextmenü aufrufen, indem Sie in die Auswahl oder auf ein Ziehelement tippen (Sie können auch Drücken und Halten verwenden).</span><span class="sxs-lookup"><span data-stu-id="36b3f-149">The following images demonstrate how to invoke the context menu by tapping within the selection or on a gripper (press and hold can also be used).</span></span>

![Tippen (oder drücken und halten) Sie in die Auswahl oder auf ein Ziehelement, um das Kontextmenü aufzurufen.](images/textselection-show-context.png)

<span data-ttu-id="36b3f-151">**Hinweis:** weichen diese Interaktionen etwas im Falle einer falsch geschriebenen Wort.</span><span class="sxs-lookup"><span data-stu-id="36b3f-151">**Note**These interactions vary somewhat in the case of a misspelled word.</span></span> <span data-ttu-id="36b3f-152">Wenn Sie auf ein Wort tippen, das als falsch geschrieben gekennzeichnet ist, wird das gesamte Wort hervorgehoben. Außerdem wird das Kontextmenü mit der vorgeschlagenen Schreibweise aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-152">Tapping a word that is marked as misspelled will both highlight the entire word and invoke the suggested spelling context menu.</span></span>

 

**<span data-ttu-id="36b3f-153">Nicht bearbeitbare Inhalte</span><span class="sxs-lookup"><span data-stu-id="36b3f-153">Non-editable content</span></span>**

<span data-ttu-id="36b3f-154">Im folgenden Bild wird veranschaulicht, wie Sie ein Wort auswählen, indem Sie in das Wort tippen (die anfängliche Auswahl enthält keine Leerzeichen).</span><span class="sxs-lookup"><span data-stu-id="36b3f-154">The following image demonstrates how to select a word by tapping within the word (no spaces are included in the initial selection).</span></span>

![Tippen Sie in ein Wort, um es auszuwählen (die anfängliche Auswahl enthält keine Leerzeichen).](images/select-word.png)

<span data-ttu-id="36b3f-156">Gehen Sie für bearbeitbaren Test genauso vor, um die Auswahl anzupassen und das Kontextmenü anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-156">Follow the same procedures as for editable text to adjust the selection and display the context menu.</span></span>

**<span data-ttu-id="36b3f-157">Objektmanipulation</span><span class="sxs-lookup"><span data-stu-id="36b3f-157">Object manipulation</span></span>**

<span data-ttu-id="36b3f-158">Verwenden Sie beim Implementieren einer benutzerdefinierten Objektmanipulation in einer UWP-App nach Möglichkeit die gleichen (oder ähnliche) Ziehelementressourcen wie für die Textauswahl.</span><span class="sxs-lookup"><span data-stu-id="36b3f-158">Wherever possible, use the same (or similar) gripper resources as text selection when implementing custom object manipulation in a UWP app.</span></span> <span data-ttu-id="36b3f-159">Auf diese Weise kann ein einheitliches Interaktionsverhalten für die gesamte Plattform bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="36b3f-159">This helps provide a consistent interaction experience across the platform.</span></span>

<span data-ttu-id="36b3f-160">Zielelemente können wie in den folgenden Abbildungen dargestellt z.B. auch in Bildverarbeitungs-Apps verwendet werden, die Größenänderungen und Zuschneiden unterstützen, oder in Media-Player-Apps mit anpassbaren Statusanzeigen.</span><span class="sxs-lookup"><span data-stu-id="36b3f-160">For example, grippers can also be used in image processing apps that support resizing and cropping or media player apps that provide adjustable progress bars, as shown in the following images.</span></span>

![Media-Player mit Statusziehelement](images/gripper-mediaplayer.png)

*<span data-ttu-id="36b3f-162">Media-Player mit anpassbarer Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="36b3f-162">Media player with adjustable progress bar.</span></span>*

![Bild mit Ziehelementen zum Zuschneiden](images/gripper-imagemanip.png)

*<span data-ttu-id="36b3f-164">Bild-Editor mit Ziehelementen zum Zuschneiden</span><span class="sxs-lookup"><span data-stu-id="36b3f-164">Image editor with cropping grippers.</span></span>*

## <a name="related-articles"></a><span data-ttu-id="36b3f-165">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="36b3f-165">Related articles</span></span>



**<span data-ttu-id="36b3f-166">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="36b3f-166">For developers</span></span>**
* [<span data-ttu-id="36b3f-167">Benutzerdefinierte Benutzerinteraktionen</span><span class="sxs-lookup"><span data-stu-id="36b3f-167">Custom user interactions</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185599)

**<span data-ttu-id="36b3f-168">Beispiele</span><span class="sxs-lookup"><span data-stu-id="36b3f-168">Samples</span></span>**
* [<span data-ttu-id="36b3f-169">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="36b3f-169">Basic input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="36b3f-170">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="36b3f-170">Low latency input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="36b3f-171">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="36b3f-171">User interaction mode sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="36b3f-172">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="36b3f-172">Focus visuals sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="36b3f-173">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="36b3f-173">Archive samples</span></span>**
* [<span data-ttu-id="36b3f-174">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="36b3f-174">Input: XAML user input events sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="36b3f-175">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="36b3f-175">Input: Device capabilities sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="36b3f-176">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="36b3f-176">Input: Touch hit testing sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="36b3f-177">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="36b3f-177">XAML scrolling, panning, and zooming sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="36b3f-178">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="36b3f-178">Input: Simplified ink sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=246570)
* [<span data-ttu-id="36b3f-179">Eingabe: Beispiel für Windows8-Bewegungen</span><span class="sxs-lookup"><span data-stu-id="36b3f-179">Input: Windows 8 gestures sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=264995)
* [<span data-ttu-id="36b3f-180">Eingabe: Beispiel für Manipulationen und Gesten (C++)</span><span class="sxs-lookup"><span data-stu-id="36b3f-180">Input: Manipulations and gestures (C++) sample</span></span>](https://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="36b3f-181">Beispiel für die DirectX-Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="36b3f-181">DirectX touch input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=231627)
 

 




