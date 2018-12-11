---
Description: Create Universal Windows Platform (UWP) apps with intuitive and distinctive user interaction experiences that are optimized for touchpad but are functionally consistent across input devices.
title: Touchpad-Interaktionen
ms.assetid: CEDEA30A-FE94-4553-A7FB-6C1FA44F06AB
label: Touchpad interactions
template: detail.hbs
keywords: Touchpad, PTP, Touch, Zeiger, Eingabe, Benutzerinteraktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 8dfc98127133790deba9274ddba7801bea34f9cd
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8885085"
---
# <a name="touchpad-design-guidelines"></a><span data-ttu-id="ef4a2-103">Touchpad-Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="ef4a2-103">Touchpad design guidelines</span></span>


<span data-ttu-id="ef4a2-104">Gestalten Sie Ihre App so, dass Benutzer über ein Touchpad mit ihr interagieren können.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-104">Design your app so that users can interact with it through a touchpad.</span></span> <span data-ttu-id="ef4a2-105">Ein Touchpad vereint die indirekte Multitoucheingabe mit der Präzisionseingabe eines Zeigergeräts (beispielsweise eine Maus).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-105">A touchpad combines both indirect multi-touch input with the precision input of a pointing device, such as a mouse.</span></span> <span data-ttu-id="ef4a2-106">Dadurch ist das Touchpad sowohl für eine toucheingabeoptimierte Benutzeroberfläche als auch die kleineren Ziele von Produktivitäts-Apps geeignet.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-106">This combination makes the touchpad suited to both a touch-optimized UI and the smaller targets of productivity apps.</span></span>

 

![Touchpad](images/input-patterns/input-touchpad.jpg)


<span data-ttu-id="ef4a2-108">Interaktionen per Touchpad erfordern drei Dinge:</span><span class="sxs-lookup"><span data-stu-id="ef4a2-108">Touchpad interactions require three things:</span></span>

-   <span data-ttu-id="ef4a2-109">Ein standardmäßiges Touchpad oder ein Windows-Präzisionstouchpad.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-109">A standard touchpad or a Windows Precision Touchpad.</span></span>

    <span data-ttu-id="ef4a2-110">Präzisionstouchpads sind für UWP-Geräte (Universelle Windows-Plattform) optimiert.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-110">Precision touchpads are optimized for Universal Windows Platform (UWP) devices.</span></span> <span data-ttu-id="ef4a2-111">Sie ermöglichen es dem System, bestimmte Aspekte der Touchpadverwendung (etwa die Fingerverfolgung und Handflächenerkennung) nativ zu behandeln, um geräteübergreifend eine konsistentere Umgebung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-111">They enable the system to handle certain aspects of the touchpad experience natively, such as finger tracking and palm detection, for a more consistent experience across devices.</span></span>

-   <span data-ttu-id="ef4a2-112">Der direkte Kontakt einzelner oder mehrerer Finger auf dem Touchpad.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-112">The direct contact of one or more fingers on the touchpad.</span></span>
-   <span data-ttu-id="ef4a2-113">Bewegung der Berührungskontakte (oder das Fehlen der Bewegung basierend auf einem Zeitschwellenwert).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-113">Movement of the touch contacts (or lack thereof, based on a time threshold).</span></span>

<span data-ttu-id="ef4a2-114">Mögliche Eingabedaten des Touchpadsensors:</span><span class="sxs-lookup"><span data-stu-id="ef4a2-114">The input data provided by the touchpad sensor can be:</span></span>

-   <span data-ttu-id="ef4a2-115">Interpretation als physische Geste für die direkte Manipulation von einem oder mehreren UI-Elementen (z.B. Schwenken, Drehen, Vergrößern/Verkleinern oder Verschieben).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-115">Interpreted as a physical gesture for direct manipulation of one or more UI elements (such as panning, rotating, resizing, or moving).</span></span> <span data-ttu-id="ef4a2-116">Die Interaktion mit einem Element über das zugehörige Eigenschaftenfenster oder ein anderes Dialogfeld gilt dagegen als indirekte Manipulation.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-116">In contrast, interacting with an element through its properties window or other dialog box is considered indirect manipulation.</span></span>
-   <span data-ttu-id="ef4a2-117">Erkennung als alternative Eingabemethode, z.B. Maus oder Stift.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-117">Recognized as an alternative input method, such as mouse or pen.</span></span>
-   <span data-ttu-id="ef4a2-118">Wird zum Ergänzen oder Ändern von Aspekten anderer Eingabemethoden verwendet, z.B. zum Verwischen eines mit einem Stift gezeichneten Freihandstrichs.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-118">Used to complement or modify aspects of other input methods, such as smudging an ink stroke drawn with a pen.</span></span>

<span data-ttu-id="ef4a2-119">Ein Touchpad vereint die indirekte Multitoucheingabe mit der Präzisionseingabe eines Zeigergeräts (etwa eine Maus).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-119">A touchpad combines indirect multi-touch input with the precision input of a pointing device, such as a mouse.</span></span> <span data-ttu-id="ef4a2-120">Dadurch ist das Touchpad sowohl für die berührungsoptimierte Benutzeroberfläche als auch die kleineren Ziele der Produktivitäts-Apps und der Desktopumgebung geeignet.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-120">This combination makes the touchpad suited to both touch-optimized UI and the typically smaller targets of productivity apps and the desktop environment.</span></span> <span data-ttu-id="ef4a2-121">Optimieren Sie das Design Ihrer UWP-App für die Toucheingabe, und profitieren Sie von der standardmäßigen Touchpad-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-121">Optimize your UWP app design for touch input and get touchpad support by default.</span></span>

<span data-ttu-id="ef4a2-122">Aufgrund der Konvergenz der Interaktionsformen, die von Touchpads unterstützt werden, empfehlen wir die Verwendung des [**PointerEntered**](https://msdn.microsoft.com/library/windows/apps/br208968)-Ereignisses, um zusätzlich zur integrierten Unterstützung für die Toucheingabe Benutzeroberflächenbefehle für die Mauseingabe bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-122">Because of the convergence of interaction experiences supported by touchpads, we recommend using the [**PointerEntered**](https://msdn.microsoft.com/library/windows/apps/br208968) event to provide mouse-style UI commands in addition to the built-in support for touch input.</span></span> <span data-ttu-id="ef4a2-123">Verwenden Sie beispielsweise Zurück- und Weiter-Schaltflächen, mit denen Benutzer sowohl Inhaltsseiten durchblättern als auch Inhalte verschieben können.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-123">For example, use previous and next buttons to let users flip through pages of content as well as pan through the content.</span></span>

<span data-ttu-id="ef4a2-124">Die in diesem Thema beschriebenen Gesten und Richtlinien können dabei helfen, die Unterstützung der Touchpadeingabe nahtlos und mit minimalem Programmieraufwand in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-124">The gestures and guidelines discussed in this topic can help to ensure that your app supports touchpad input seamlessly and with minimal code.</span></span>

## <a name="the-touchpad-language"></a><span data-ttu-id="ef4a2-125">Sprache für Eingabe per Touchpad</span><span class="sxs-lookup"><span data-stu-id="ef4a2-125">The touchpad language</span></span>


<span data-ttu-id="ef4a2-126">Ein kompakter Satz von Touchpadinteraktionen wird durchgängig im ganzen System verwendet.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-126">A concise set of touchpad interactions are used consistently throughout the system.</span></span> <span data-ttu-id="ef4a2-127">Indem Sie Ihre App für die Touch- und Mauseingabe optimieren, sorgen Sie dafür, dass sich Benutzer sofort in Ihrer App zurechtfinden. So erleichtern Sie Benutzern den Einstieg und die Verwendung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-127">Optimize your app for touch and mouse input and this language makes your app feel instantly familiar for your users, increasing their confidence and making your app easier to learn and use.</span></span>

<span data-ttu-id="ef4a2-128">Benutzer können viel mehr Gesten und Interaktionsverhalten für Präzisionstouchpads festlegen als für ein standardmäßiges Touchpad.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-128">Users can set far more Precision Touchpad gestures and interaction behaviors than they can for a standard touchpad.</span></span> <span data-ttu-id="ef4a2-129">Diese beiden Bilder zeigen die verschiedenen Touchpad-Einstellungsseiten (unter Einstellungen &gt; Geräte &gt; Maus und Touchpad) für ein standardmäßiges Touchpad und ein Präzisionstouchpad.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-129">These two images show the different touchpad settings pages from Settings &gt; Devices &gt; Mouse & touchpad for a standard touchpad and a Precision Touchpad, respectively.</span></span>

![Einstellungen für ein standardmäßiges Touchpad](images/mouse-touchpad-settings-standard.png)

<sup><span data-ttu-id="ef4a2-131">Einstellungen\\ für ein standardmäßiges\\ Touchpad</span><span class="sxs-lookup"><span data-stu-id="ef4a2-131">Standard\\ touchpad\\ settings</span></span></sup>

![Einstellungen für ein Windows-Präzisionstouchpad](images/mouse-touchpad-settings-ptp.png)

<sup><span data-ttu-id="ef4a2-133">Einstellungen\\ für ein\\ Windows-Präzisionstouchpad</span><span class="sxs-lookup"><span data-stu-id="ef4a2-133">Windows\\ Precision\\ Touchpad\\ settings</span></span></sup>

<span data-ttu-id="ef4a2-134">Im Anschluss folgen einige Beispiele für touchpadoptimierte Gesten zum Ausführen allgemeiner Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-134">Here are some examples of touchpad-optimized gestures for performing common tasks.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="ef4a2-135">Begriff</span><span class="sxs-lookup"><span data-stu-id="ef4a2-135">Term</span></span></th>
<th align="left"><span data-ttu-id="ef4a2-136">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ef4a2-136">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="ef4a2-137">Tippen mit drei Fingern</span><span class="sxs-lookup"><span data-stu-id="ef4a2-137">Three-finger tap</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-138">Benutzereinstellung für die Suche mit <strong>Cortana</strong> oder die Anzeige des Info-Centers<strong></strong>.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-138">User preference to search with <strong>Cortana</strong> or show <strong>Action Center</strong>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="ef4a2-139">Ziehbewegung mit drei Fingern</span><span class="sxs-lookup"><span data-stu-id="ef4a2-139">Three finger slide</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-140">Benutzereinstellung zum Öffnen der Aufgabenansicht des virtuellen Desktops, zum Anzeigen des Desktops oder zum Wechseln zwischen geöffneten Apps.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-140">User preference to open the virtual desktop Task View, show Desktop, or switch between open apps.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="ef4a2-141">Tippen mit einem Finger: Aufrufen der primären Aktion</span><span class="sxs-lookup"><span data-stu-id="ef4a2-141">Single finger tap for primary action</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-142">Durch Tippen mit einem Finger auf ein Element wird dessen primäre Aktion aufgerufen (z.B. das Starten einer App oder das Ausführen eines Befehls).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-142">Use a single finger to tap an element and invoke its primary action (such as launching an app or executing a command).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="ef4a2-143">Tippen mit zwei Fingern: Ausführen eines Rechtsklicks</span><span class="sxs-lookup"><span data-stu-id="ef4a2-143">Two finger tap to right-click</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-144">Tippen Sie mit zwei Fingern gleichzeitig auf ein Element, um es auszuwählen und Kontextbefehle anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-144">Tap with two fingers simultaneously on an element to select it and display contextual commands.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="ef4a2-145">Ziehen mit zwei Fingern: Verschieben</span><span class="sxs-lookup"><span data-stu-id="ef4a2-145">Two finger slide to pan</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-146">Das Ziehen wird in erster Linie für Verschiebungen verwendet, kann jedoch auch zum Schieben, Zeichnen oder Schreiben genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-146">Slide is used primarily for panning interactions but can also be used for moving, drawing, or writing.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="ef4a2-147">Zusammendrücken/Aufziehen: Zoom</span><span class="sxs-lookup"><span data-stu-id="ef4a2-147">Pinch and stretch to zoom</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-148">Die Zusammendrück- und Aufziehbewegungen werden üblicherweise für Größenänderungen und zum Ausführen des semantischen Zooms verwendet.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-148">The pinch and stretch gestures are commonly used for resizing and Semantic Zoom.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="ef4a2-149">Drücken und Ziehen mit einem Finger: Neuanordnen</span><span class="sxs-lookup"><span data-stu-id="ef4a2-149">Single finger press and slide to rearrange</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-150">Ziehen eines Elements.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-150">Drag an element.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="ef4a2-151">Drücken und Ziehen mit einem Finger: Textauswahl</span><span class="sxs-lookup"><span data-stu-id="ef4a2-151">Single finger press and slide to select text</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-152">Durch Drücken und Ziehen in auswählbarem Text wird Text ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-152">Press within selectable text and slide to select it.</span></span> <span data-ttu-id="ef4a2-153">Durch Doppeltippen wird ein einzelnes Wort ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-153">Double-tap to select a word.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="ef4a2-154">Zonen für Links- und Rechtsklick</span><span class="sxs-lookup"><span data-stu-id="ef4a2-154">Left and right click zone</span></span></p></td>
<td align="left"><p><span data-ttu-id="ef4a2-155">Mit diesen Zonen emulieren Sie die Links- und Rechtsklickfunktion einer Maus.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-155">Emulate the left and right button functionality of a mouse device.</span></span></p></td>
</tr>
</tbody>
</table>

 

## <a name="hardware"></a><span data-ttu-id="ef4a2-156">Hardware</span><span class="sxs-lookup"><span data-stu-id="ef4a2-156">Hardware</span></span>


<span data-ttu-id="ef4a2-157">Fragen Sie die Funktionen des Mausgeräts ([**MouseCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225626)) ab, um zu ermitteln, auf welche Elemente der Benutzeroberfläche Ihrer App die Touchpad-Hardware direkt zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-157">Query the mouse device capabilities ([**MouseCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225626)) to identify what aspects of your app UI the touchpad hardware can access directly.</span></span> <span data-ttu-id="ef4a2-158">Wir empfehlen die Bereitstellung einer Benutzeroberfläche, die sowohl Touch- als auch Mauseingabe ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-158">We recommend providing UI for both touch and mouse input.</span></span>

<span data-ttu-id="ef4a2-159">Weitere Informationen zum Abfragen von Gerätefunktionen finden Sie unter [Identifizieren von Eingabegeräten](identify-input-devices.md).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-159">For more info about querying device capabilities, see [Identify input devices](identify-input-devices.md).</span></span>

## <a name="visual-feedback"></a><span data-ttu-id="ef4a2-160">Visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="ef4a2-160">Visual feedback</span></span>


-   <span data-ttu-id="ef4a2-161">Blenden Sie die für Touchpadinteraktionen spezifische Benutzeroberfläche ein, sobald ein Touchpad-Cursor erkannt wird (durch Bewegungs- oder Zeigeereignisse), um die Funktionalität des Elements verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-161">When a touchpad cursor is detected (through move or hover events), show mouse-specific UI to indicate functionality exposed by the element.</span></span> <span data-ttu-id="ef4a2-162">Wenn der Touchpad-Cursor für eine bestimmte Zeit nicht bewegt wird oder der Benutzer eine Toucheingabeinteraktion auslöst, blenden Sie die für Touchpad-Interaktionen spezifische Benutzeroberfläche schrittweise aus.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-162">If the touchpad cursor doesn't move for a certain amount of time, or if the user initiates a touch interaction, make the touchpad UI gradually fade away.</span></span> <span data-ttu-id="ef4a2-163">Somit bleibt die Benutzeroberfläche sauber und aufgeräumt.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-163">This keeps the UI clean and uncluttered.</span></span>
-   <span data-ttu-id="ef4a2-164">Verwenden Sie nicht den Cursor für Zeigefeedback, das Feedback des Elements reicht aus (siehe Abschnitt „Cursor“ unten).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-164">Don't use the cursor for hover feedback, the feedback provided by the element is sufficient (see the Cursors section below).</span></span>
-   <span data-ttu-id="ef4a2-165">Zeigen Sie kein visuelles Feedback an, wenn ein Element keine Interaktionen unterstützt (z.B. statischer Text).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-165">Don't display visual feedback if an element doesn't support interaction (such as static text).</span></span>
-   <span data-ttu-id="ef4a2-166">Verwenden Sie keine Fokusrechtecke für Interaktionen per Touchpad.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-166">Don't use focus rectangles with touchpad interactions.</span></span> <span data-ttu-id="ef4a2-167">Diese sind ausschließlich für Tastaturinteraktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-167">Reserve these for keyboard interactions.</span></span>
-   <span data-ttu-id="ef4a2-168">Zeigen Sie für alle Elemente, die das gleiche Eingabeziel darstellen, das gleiche visuelle Feedback an.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-168">Display visual feedback concurrently for all elements that represent the same input target.</span></span>

<span data-ttu-id="ef4a2-169">Allgemeine Informationen zum visuellen Feedback finden Sie unter [Richtlinien für visuelles Feedback](https://msdn.microsoft.com/library/windows/apps/hh465342).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-169">For more general guidance about visual feedback, see [Guidelines for visual feedback](https://msdn.microsoft.com/library/windows/apps/hh465342).</span></span>

## <a name="cursors"></a><span data-ttu-id="ef4a2-170">Cursor</span><span class="sxs-lookup"><span data-stu-id="ef4a2-170">Cursors</span></span>


<span data-ttu-id="ef4a2-171">In Windows Store-Apps sind einige Standardcursor verfügbar, die als Touchpad-Zeiger verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-171">A set of standard cursors is available for a touchpad pointer.</span></span> <span data-ttu-id="ef4a2-172">Diese Cursor werden verwendet, um die primäre Aktion eines Elements anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-172">These are used to indicate the primary action of an element.</span></span>

<span data-ttu-id="ef4a2-173">Jedem Standardcursor ist ein entsprechendes Standardbild zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-173">Each standard cursor has a corresponding default image associated with it.</span></span> <span data-ttu-id="ef4a2-174">Benutzer einer App können das Standardbild, das einem Standardcursor zugewiesen ist, jederzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-174">The user or an app can replace the default image associated with any standard cursor at any time.</span></span> <span data-ttu-id="ef4a2-175">UWP-Apps geben über die [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273)-Funktion ein Cursorbild an.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-175">UWP apps specify a cursor image through the [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273) function.</span></span>

<span data-ttu-id="ef4a2-176">Beachten Sie beim Anpassen des Mauszeigers Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ef4a2-176">If you need to customize the mouse cursor:</span></span>

-   <span data-ttu-id="ef4a2-177">Verwenden Sie immer den Pfeilcursor (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-177">Always use the arrow cursor (</span></span>![Pfeilcursor](images/cursor-arrow.png)<span data-ttu-id="ef4a2-179">) für klickbare Elemente.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-179">) for clickable elements.</span></span> <span data-ttu-id="ef4a2-180">Verwenden Sie den Zeigefingercursor (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-180">don't use the pointing hand cursor (</span></span>![Zeigefingercursor](images/cursor-pointinghand.png)<span data-ttu-id="ef4a2-182">) nicht für Links oder andere interaktive Elemente.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-182">) for links or other interactive elements.</span></span> <span data-ttu-id="ef4a2-183">Verwenden Sie stattdessen Zeigeeffekte (wie bereits beschrieben).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-183">Instead, use hover effects (described earlier).</span></span>
-   <span data-ttu-id="ef4a2-184">Verwenden Sie den Textcursor (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-184">Use the text cursor (</span></span>![Textcursor](images/cursor-text.png)<span data-ttu-id="ef4a2-186">) für auswählbaren Text.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-186">) for selectable text.</span></span>
-   <span data-ttu-id="ef4a2-187">Verwenden Sie den Bewegungscursor (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-187">Use the move cursor (</span></span>![Bewegungscursor](images/cursor-move.png)<span data-ttu-id="ef4a2-189">), wenn die primäre Aktion eine Bewegung ist (etwa beim Ziehen oder Zuschneiden).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-189">) when moving is the primary action (such as dragging or cropping).</span></span> <span data-ttu-id="ef4a2-190">Verwenden Sie den Bewegungscursor nicht, wenn die primäre Aktion eine Navigationsaktion ist (etwa bei Start-Kacheln).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-190">Don't use the move cursor for elements where the primary action is navigation (such as Start tiles).</span></span>
-   <span data-ttu-id="ef4a2-191">Verwenden Sie die Cursor für horizontale, vertikale und diagonale Größenänderung (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-191">Use the horizontal, vertical and diagonal resize cursors (</span></span>![Cursor für vertikale Größenänderung](images/cursor-vertical.png)<span data-ttu-id="ef4a2-193">,</span><span class="sxs-lookup"><span data-stu-id="ef4a2-193">,</span></span> ![Cursor für horizontale Größenänderung](images/cursor-horizontal.png)<span data-ttu-id="ef4a2-195">,</span><span class="sxs-lookup"><span data-stu-id="ef4a2-195">,</span></span> ![Cursor für diagonale Größenänderung (unten links, oben rechts)](images/cursor-diagonal2.png)<span data-ttu-id="ef4a2-197">,</span><span class="sxs-lookup"><span data-stu-id="ef4a2-197">,</span></span> ![Cursor für diagonale Größenänderung (oben links, unten rechts)](images/cursor-diagonal1.png)<span data-ttu-id="ef4a2-199">), wenn die Größe eines Objekts geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ef4a2-199">), when an object is resizable.</span></span>
-   <span data-ttu-id="ef4a2-200">Verwenden Sie den Handcursor (</span><span class="sxs-lookup"><span data-stu-id="ef4a2-200">Use the grasping hand cursors (</span></span>![Handcursor (offen)](images/cursor-pan1.png)<span data-ttu-id="ef4a2-202">,</span><span class="sxs-lookup"><span data-stu-id="ef4a2-202">,</span></span> ![Handcursor (geschlossen)](images/cursor-pan2.png)<span data-ttu-id="ef4a2-204">) beim Verschieben von Inhalt innerhalb einer Canvas (etwa bei einer Karte).</span><span class="sxs-lookup"><span data-stu-id="ef4a2-204">) when panning content within a fixed canvas (such as a map).</span></span>

## <a name="related-articles"></a><span data-ttu-id="ef4a2-205">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="ef4a2-205">Related articles</span></span>


* [<span data-ttu-id="ef4a2-206">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="ef4a2-206">Handle pointer input</span></span>](handle-pointer-input.md)
* <span data-ttu-id="ef4a2-207">[Identifizieren von Eingabegeräten](identify-input-devices.md)
**Beispiele**</span><span class="sxs-lookup"><span data-stu-id="ef4a2-207">[Identify input devices](identify-input-devices.md)
**Samples**</span></span>
* [<span data-ttu-id="ef4a2-208">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="ef4a2-208">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="ef4a2-209">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="ef4a2-209">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="ef4a2-210">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="ef4a2-210">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* <span data-ttu-id="ef4a2-211">[Beispiel für Focus-Visuals](http://go.microsoft.com/fwlink/p/?LinkID=619895)
**Archivbeispiele**</span><span class="sxs-lookup"><span data-stu-id="ef4a2-211">[Focus visuals sample](http://go.microsoft.com/fwlink/p/?LinkID=619895)
**Archive Samples**</span></span>
* [<span data-ttu-id="ef4a2-212">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ef4a2-212">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="ef4a2-213">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="ef4a2-213">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="ef4a2-214">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="ef4a2-214">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="ef4a2-215">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="ef4a2-215">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231605)
 



