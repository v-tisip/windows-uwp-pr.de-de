---
Description: Respond to mouse input in your apps by handling the same basic pointer events that you use for touch and pen input.
title: Mausinteraktionen
ms.assetid: C8A158EF-70A9-4BA2-A270-7D08125700AC
label: Mouse
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f81634fdb0f9382b1f660394764e5555189783e4
ms.sourcegitcommit: 444fd387c55618f9afdac115264c85b14fd8b826
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "8999913"
---
# <a name="mouse-interactions"></a><span data-ttu-id="1ced5-103">Mausinteraktionen</span><span class="sxs-lookup"><span data-stu-id="1ced5-103">Mouse interactions</span></span>

<span data-ttu-id="1ced5-104">Optimieren Sie das Design Ihrer UWP-Apps für die Toucheingabe, und freuen Sie sich über die standardmäßige allgemeine Unterstützung von Mausgeräten.</span><span class="sxs-lookup"><span data-stu-id="1ced5-104">Optimize your Universal Windows Platform (UWP) app design for touch input and get basic mouse support by default.</span></span> 

![Maus](images/input-patterns/input-mouse.jpg)

<span data-ttu-id="1ced5-106">Die Mauseingabe eignet sich am besten für Benutzerinteraktionen, die Präzision beim Zeigen und Klicken erfordern.</span><span class="sxs-lookup"><span data-stu-id="1ced5-106">Mouse input is best suited for user interactions that require precision when pointing and clicking.</span></span> <span data-ttu-id="1ced5-107">Naturgemäß unterstützt die Benutzeroberfläche von Windows diese Präzision, auch wenn sie für die ungenaue Toucheingabe optimiert wurde.</span><span class="sxs-lookup"><span data-stu-id="1ced5-107">This inherent precision is naturally supported by the UI of Windows, which is optimized for the imprecise nature of touch.</span></span>

<span data-ttu-id="1ced5-108">Die Maus- und Toucheingabe unterscheiden sich dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (z.B. Streifen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1ced5-108">Where mouse and touch input diverge is the ability for touch to more closely emulate the direct manipulation of UI elements through physical gestures performed directly on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span> <span data-ttu-id="1ced5-109">Manipulationen mit der Maus erfordern in der Regel einigen UI-Aufwand, wie z. B. die Verwendung von Handles für das Anpassen der Größe oder Drehen eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="1ced5-109">Manipulations with a mouse typically require some other UI affordance, such as the use of handles to resize or rotate an object.</span></span>

<span data-ttu-id="1ced5-110">In diesem Thema werden Designüberlegungen für Mausinteraktionen behandelt.</span><span class="sxs-lookup"><span data-stu-id="1ced5-110">This topic describes design considerations for mouse interactions.</span></span>

## <a name="the-uwp-app-mouse-language"></a><span data-ttu-id="1ced5-111">Die UWP-App-Sprache für Mauseingaben</span><span class="sxs-lookup"><span data-stu-id="1ced5-111">The UWP app mouse language</span></span>

<span data-ttu-id="1ced5-112">Ein kompakter Satz von Mausinteraktionen wird durchgängig im ganzen System verwendet.</span><span class="sxs-lookup"><span data-stu-id="1ced5-112">A concise set of mouse interactions are used consistently throughout the system.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1ced5-113">Benennung</span><span class="sxs-lookup"><span data-stu-id="1ced5-113">Term</span></span></th>
<th align="left"><span data-ttu-id="1ced5-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1ced5-114">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="1ced5-115">Lernen durch Zeigen</span><span class="sxs-lookup"><span data-stu-id="1ced5-115">Hover to learn</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-116">Zeigen Sie auf ein Element, um weitere Informationen oder visuelle Hinweise (wie etwa QuickInfos) aufzurufen, ohne eine Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-116">Hover over an element to display more detailed info or teaching visuals (such as a tooltip) without a commitment to an action.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="1ced5-117">Linksklick, um primäre Aktion auszuführen</span><span class="sxs-lookup"><span data-stu-id="1ced5-117">Left-click for primary action</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-118">Klicken Sie mit der linken Maustaste auf ein Element, um dessen primäre Aktion aufzurufen (z.B. das Starten einer App oder das Ausführen eines Befehls).</span><span class="sxs-lookup"><span data-stu-id="1ced5-118">Left-click an element to invoke its primary action (such as launching an app or executing a command).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="1ced5-119">Bildlauf, um Ansicht zu ändern</span><span class="sxs-lookup"><span data-stu-id="1ced5-119">Scroll to change view</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-120">Zeigen Sie Bildlaufleisten an, damit Benutzer in einem Inhaltsbereich nach oben, unten, links und rechts navigieren können.</span><span class="sxs-lookup"><span data-stu-id="1ced5-120">Display scroll bars to move up, down, left, and right within a content area.</span></span> <span data-ttu-id="1ced5-121">Benutzer können durch Klicken auf Bildlaufleisten oder Drehen des Mausrads einen Bildlauf durchführen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-121">Users can scroll by clicking scroll bars or rotating the mouse wheel.</span></span> <span data-ttu-id="1ced5-122">Auf Bildlaufleisten kann die Position der aktuellen Ansicht innerhalb des Inhaltsbereichs angezeigt werden (durch das Schwenken bei der Fingereingabe wird eine ähnliche Benutzeroberfläche angezeigt).</span><span class="sxs-lookup"><span data-stu-id="1ced5-122">Scroll bars can indicate the location of the current view within the content area (panning with touch displays a similar UI).</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="1ced5-123">Rechtsklick, um Auswahl zu treffen und Befehl auszuwählen</span><span class="sxs-lookup"><span data-stu-id="1ced5-123">Right-click to select and command</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-124">Klicken Sie mit der rechten Maustaste, um die Navigationsleiste (sofern verfügbar) und die App-Leiste mit globalen Befehlen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-124">Right-click to display the navigation bar (if available) and the app bar with global commands.</span></span> <span data-ttu-id="1ced5-125">Klicken Sie mit der rechten Maustaste auf ein Element, um es auszuwählen und die App-Leiste mit Kontextbefehlen für das ausgewählte Element anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-125">Right-click an element to select it and display the app bar with contextual commands for the selected element.</span></span></p>
<div class="alert"><span data-ttu-id="1ced5-126">
<strong>Hinweis:</strong>mit der rechten Maustaste, um ein Kontextmenü anzuzeigen, wenn die Auswahl oder der app-Leiste verfügbaren Befehle nicht gewünschte Benutzeroberflächenverhalten.</span><span class="sxs-lookup"><span data-stu-id="1ced5-126">
<strong>Note</strong>Right-click to display a context menu if selection or app bar commands are not appropriate UI behaviors.</span></span> <span data-ttu-id="1ced5-127">Wir empfehlen jedoch ausdrücklich, die App-Leiste für alle Befehlsverhalten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1ced5-127">But we strongly recommend that you use the app bar for all command behaviors.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="1ced5-128">Benutzeroberflächenbefehle zum Zoomen</span><span class="sxs-lookup"><span data-stu-id="1ced5-128">UI commands to zoom</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-129">Zeigen Sie Benutzeroberflächenbefehle auf der App-Leiste an (z.B. "+" und "-"), oder drücken Sie STRG und drehen Sie das Mausrad, um Zusammendrück- und Aufziehbewegungen zum Zoomen zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="1ced5-129">Display UI commands in the app bar (such as + and -), or press Ctrl and rotate mouse wheel, to emulate pinch and stretch gestures for zooming.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="1ced5-130">Benutzeroberflächenbefehle zum Drehen</span><span class="sxs-lookup"><span data-stu-id="1ced5-130">UI commands to rotate</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-131">Zeigen Sie Benutzeroberflächenbefehle auf der App-Leiste an, oder drücken Sie STRG+UMSCHALTTASTE, und drehen Sie das Mausrad, um die Drehbewegung zum Drehen zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="1ced5-131">Display UI commands in the app bar, or press Ctrl+Shift and rotate mouse wheel, to emulate the turn gesture for rotating.</span></span> <span data-ttu-id="1ced5-132">Drehen Sie das Gerät selbst, um den ganzen Bildschirm zu drehen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-132">Rotate the device itself to rotate the entire screen.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="1ced5-133">Linksklick und ziehen, um neu anzuordnen</span><span class="sxs-lookup"><span data-stu-id="1ced5-133">Left-click and drag to rearrange</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-134">Klicken Sie mit der linken Maustaste auf ein Element, und ziehen Sie, um es zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-134">Left-click and drag an element to move it.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="1ced5-135">Linksklick und ziehen, um Text auszuwählen</span><span class="sxs-lookup"><span data-stu-id="1ced5-135">Left-click and drag to select text</span></span></p></td>
<td align="left"><p><span data-ttu-id="1ced5-136">Klicken Sie mit der linken Maustaste auf auswählbaren Text, und ziehen Sie, um Text auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-136">Left-click within selectable text and drag to select it.</span></span> <span data-ttu-id="1ced5-137">Doppelklicken Sie, um ein Wort auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-137">Double-click to select a word.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="mouse-input-events"></a><span data-ttu-id="1ced5-138">Mauseingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="1ced5-138">Mouse input events</span></span>

<span data-ttu-id="1ced5-139">Die meisten Mauseingabe kann über die allgemeine Routingereignisse Eingabeereignisse von allen [**UIElement**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) -Objekten unterstützt behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="1ced5-139">Most mouse input can be handled through the common routed input events supported by all [**UIElement**](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement) objects.</span></span> <span data-ttu-id="1ced5-140">Dazu zählen:</span><span class="sxs-lookup"><span data-stu-id="1ced5-140">These include:</span></span>

- [**<span data-ttu-id="1ced5-141">BringIntoViewRequested</span><span class="sxs-lookup"><span data-stu-id="1ced5-141">BringIntoViewRequested</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.bringintoviewrequested)
- [**<span data-ttu-id="1ced5-142">CharacterReceived</span><span class="sxs-lookup"><span data-stu-id="1ced5-142">CharacterReceived</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.characterreceived)
- [**<span data-ttu-id="1ced5-143">ContextCanceled</span><span class="sxs-lookup"><span data-stu-id="1ced5-143">ContextCanceled</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.contextcanceled)
- [**<span data-ttu-id="1ced5-144">ContextRequested</span><span class="sxs-lookup"><span data-stu-id="1ced5-144">ContextRequested</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.contextrequested)
- [**<span data-ttu-id="1ced5-145">DoubleTapped</span><span class="sxs-lookup"><span data-stu-id="1ced5-145">DoubleTapped</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.doubletapped)
- [**<span data-ttu-id="1ced5-146">DragEnter</span><span class="sxs-lookup"><span data-stu-id="1ced5-146">DragEnter</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.dragenter)
- [**<span data-ttu-id="1ced5-147">DragLeave</span><span class="sxs-lookup"><span data-stu-id="1ced5-147">DragLeave</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.dragleave)
- [**<span data-ttu-id="1ced5-148">DragOver</span><span class="sxs-lookup"><span data-stu-id="1ced5-148">DragOver</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.dragover)
- [**<span data-ttu-id="1ced5-149">DragStarting</span><span class="sxs-lookup"><span data-stu-id="1ced5-149">DragStarting</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.dragstarting)
- [**<span data-ttu-id="1ced5-150">Drop</span><span class="sxs-lookup"><span data-stu-id="1ced5-150">Drop</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.drop)
- [**<span data-ttu-id="1ced5-151">DropCompleted</span><span class="sxs-lookup"><span data-stu-id="1ced5-151">DropCompleted</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.dropcompleted)
- [**<span data-ttu-id="1ced5-152">GettingFocus</span><span class="sxs-lookup"><span data-stu-id="1ced5-152">GettingFocus</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.gettingfocus)
- [**<span data-ttu-id="1ced5-153">GotFocus</span><span class="sxs-lookup"><span data-stu-id="1ced5-153">GotFocus</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.gotfocus)
- [**<span data-ttu-id="1ced5-154">Holding</span><span class="sxs-lookup"><span data-stu-id="1ced5-154">Holding</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.holding)
- [**<span data-ttu-id="1ced5-155">KeyDown</span><span class="sxs-lookup"><span data-stu-id="1ced5-155">KeyDown</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.keydown)
- [**<span data-ttu-id="1ced5-156">KeyUp</span><span class="sxs-lookup"><span data-stu-id="1ced5-156">KeyUp</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.keyup)
- [**<span data-ttu-id="1ced5-157">LosingFocus</span><span class="sxs-lookup"><span data-stu-id="1ced5-157">LosingFocus</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.losingfocus)
- [**<span data-ttu-id="1ced5-158">LostFocus</span><span class="sxs-lookup"><span data-stu-id="1ced5-158">LostFocus</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.lostfocus)
- [**<span data-ttu-id="1ced5-159">ManipulationCompleted</span><span class="sxs-lookup"><span data-stu-id="1ced5-159">ManipulationCompleted</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.manipulationcompleted)
- [**<span data-ttu-id="1ced5-160">ManipulationDelta</span><span class="sxs-lookup"><span data-stu-id="1ced5-160">ManipulationDelta</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.manipulationdelta)
- [**<span data-ttu-id="1ced5-161">ManipulationInertiaStarting</span><span class="sxs-lookup"><span data-stu-id="1ced5-161">ManipulationInertiaStarting</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.manipulationinertiastarting)
- [**<span data-ttu-id="1ced5-162">ManipulationStarted</span><span class="sxs-lookup"><span data-stu-id="1ced5-162">ManipulationStarted</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.manipulationstarted)
- [**<span data-ttu-id="1ced5-163">ManipulationStarting</span><span class="sxs-lookup"><span data-stu-id="1ced5-163">ManipulationStarting</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.manipulationstarting)
- [**<span data-ttu-id="1ced5-164">NoFocusCandidateFound</span><span class="sxs-lookup"><span data-stu-id="1ced5-164">NoFocusCandidateFound</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.nofocuscandidatefoundeventargs)
- [**<span data-ttu-id="1ced5-165">PointerCanceled</span><span class="sxs-lookup"><span data-stu-id="1ced5-165">PointerCanceled</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointercanceled)
- [**<span data-ttu-id="1ced5-166">PointerCaptureLost</span><span class="sxs-lookup"><span data-stu-id="1ced5-166">PointerCaptureLost</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointercapturelost)
- [**<span data-ttu-id="1ced5-167">PointerEntered</span><span class="sxs-lookup"><span data-stu-id="1ced5-167">PointerEntered</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerentered)
- [**<span data-ttu-id="1ced5-168">PointerExited</span><span class="sxs-lookup"><span data-stu-id="1ced5-168">PointerExited</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerexited)
- [**<span data-ttu-id="1ced5-169">PointerMoved</span><span class="sxs-lookup"><span data-stu-id="1ced5-169">PointerMoved</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointermoved)
- [**<span data-ttu-id="1ced5-170">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="1ced5-170">PointerPressed</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerpressed)
- [**<span data-ttu-id="1ced5-171">PointerReleased</span><span class="sxs-lookup"><span data-stu-id="1ced5-171">PointerReleased</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerreleased)
- [**<span data-ttu-id="1ced5-172">PointerWheelChanged</span><span class="sxs-lookup"><span data-stu-id="1ced5-172">PointerWheelChanged</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerwheelchanged)
- [**<span data-ttu-id="1ced5-173">PreviewKeyDown</span><span class="sxs-lookup"><span data-stu-id="1ced5-173">PreviewKeyDown</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.previewkeydown.md)
- [**<span data-ttu-id="1ced5-174">PreviewKeyUp</span><span class="sxs-lookup"><span data-stu-id="1ced5-174">PreviewKeyUp</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.previewkeyup.md)
- [**<span data-ttu-id="1ced5-175">PointerWheelChanged</span><span class="sxs-lookup"><span data-stu-id="1ced5-175">PointerWheelChanged</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.pointerwheelchanged)
- [**<span data-ttu-id="1ced5-176">RightTapped</span><span class="sxs-lookup"><span data-stu-id="1ced5-176">RightTapped</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.righttapped)
- [**<span data-ttu-id="1ced5-177">Tapped</span><span class="sxs-lookup"><span data-stu-id="1ced5-177">Tapped</span></span>**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.tapped)

<span data-ttu-id="1ced5-178">Allerdings können Sie die Funktionen der einzelnen Geräte (z. B. die Ereignisse rad) mit dem Zeiger, Bewegung, Manipulationsereignisse in [Windows.UI.Input](https://docs.microsoft.com/uwp/api/windows.ui.input)nutzen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-178">However, you can take advantage of the specific capabilities of each device (such as mouse wheel events) using the pointer, gesture, and manipulation events in [Windows.UI.Input](https://docs.microsoft.com/uwp/api/windows.ui.input).</span></span>

<span data-ttu-id="1ced5-179">**Beispiele:** Finden Sie unsere [BasicInput Beispiel](https://go.microsoft.com/fwlink/p/?LinkID=620302).</span><span class="sxs-lookup"><span data-stu-id="1ced5-179">**Samples:** See our [BasicInput sample](https://go.microsoft.com/fwlink/p/?LinkID=620302), for .</span></span>

## <a name="guidelines-for-visual-feedback"></a><span data-ttu-id="1ced5-180">Richtlinien für visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="1ced5-180">Guidelines for visual feedback</span></span>

- <span data-ttu-id="1ced5-181">Wenn eine Maus erkannt wird (durch Bewegungs- oder Daraufzeigen-Ereignisse), zeigen Sie eine für Mausinteraktionen spezifische Benutzeroberfläche an, um auf vom Element verfügbar gemachte Funktionen hinzuweisen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-181">When a mouse is detected (through move or hover events), show mouse-specific UI to indicate functionality exposed by the element.</span></span> <span data-ttu-id="1ced5-182">Wenn die Maus für eine bestimmte Zeit nicht bewegt wird oder der Benutzer eine Fingereingabeinteraktion auslöst, blenden Sie die für Mausinteraktionen spezifische Benutzeroberfläche schrittweise aus.</span><span class="sxs-lookup"><span data-stu-id="1ced5-182">If the mouse doesn't move for a certain amount of time, or if the user initiates a touch interaction, make the mouse UI gradually fade away.</span></span> <span data-ttu-id="1ced5-183">Somit bleibt die Benutzeroberfläche sauber und aufgeräumt.</span><span class="sxs-lookup"><span data-stu-id="1ced5-183">This keeps the UI clean and uncluttered.</span></span>
- <span data-ttu-id="1ced5-184">Verwenden Sie nicht den Cursor für Zeigefeedback, das Feedback des Elements reicht aus (siehe Cursor unten).</span><span class="sxs-lookup"><span data-stu-id="1ced5-184">Don't use the cursor for hover feedback, the feedback provided by the element is sufficient (see Cursors below).</span></span>
- <span data-ttu-id="1ced5-185">Zeigen Sie kein visuelles Feedback an, wenn ein Element keine Interaktionen unterstützt (z.B. statischer Text).</span><span class="sxs-lookup"><span data-stu-id="1ced5-185">Don't display visual feedback if an element doesn't support interaction (such as static text).</span></span>
- <span data-ttu-id="1ced5-186">Verwenden Sie keine Fokusrechtecke für Mausinteraktionen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-186">Don't use focus rectangles with mouse interactions.</span></span> <span data-ttu-id="1ced5-187">Diese sind ausschließlich für Tastaturinteraktionen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-187">Reserve these for keyboard interactions.</span></span>
- <span data-ttu-id="1ced5-188">Zeigen Sie für alle Elemente, die das gleiche Eingabeziel darstellen, das gleiche visuelle Feedback an.</span><span class="sxs-lookup"><span data-stu-id="1ced5-188">Display visual feedback concurrently for all elements that represent the same input target.</span></span>
- <span data-ttu-id="1ced5-189">Stellen Sie Schaltflächen (z. B. „+“ und „-“) zur Verfügung, um fingereingabebasierte Manipulationen wie etwa Schwenken, Drehen, Zoomen usw. zu emulieren.</span><span class="sxs-lookup"><span data-stu-id="1ced5-189">Provide buttons (such as + and -) for emulating touch-based manipulations such as panning, rotating, zooming, and so on.</span></span>

<span data-ttu-id="1ced5-190">Allgemeine Informationen zum visuellen Feedback finden Sie unter [Richtlinien für visuelles Feedback](guidelines-for-visualfeedback.md).</span><span class="sxs-lookup"><span data-stu-id="1ced5-190">For more general guidance on visual feedback, see [Guidelines for visual feedback](guidelines-for-visualfeedback.md).</span></span>

## <a name="cursors"></a><span data-ttu-id="1ced5-191">Cursor</span><span class="sxs-lookup"><span data-stu-id="1ced5-191">Cursors</span></span>

<span data-ttu-id="1ced5-192">Für einen Mauszeiger ist eine Reihe von Standardcursor verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1ced5-192">A set of standard cursors is available for a mouse pointer.</span></span> <span data-ttu-id="1ced5-193">Diese geben die primäre Aktion eines Elements an.</span><span class="sxs-lookup"><span data-stu-id="1ced5-193">These are used to indicate the primary action of an element.</span></span>

<span data-ttu-id="1ced5-194">Jedem Standardcursor ist ein entsprechendes Standardbild zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="1ced5-194">Each standard cursor has a corresponding default image associated with it.</span></span> <span data-ttu-id="1ced5-195">Benutzer einer App können das Standardbild, das einem Standardcursor zugewiesen ist, jederzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="1ced5-195">The user or an app can replace the default image associated with any standard cursor at any time.</span></span> <span data-ttu-id="1ced5-196">Geben Sie über die [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273)-Funktion die Abbildung eines Cursors an.</span><span class="sxs-lookup"><span data-stu-id="1ced5-196">Specify a cursor image through the [**PointerCursor**](https://msdn.microsoft.com/library/windows/apps/br208273) function.</span></span>

<span data-ttu-id="1ced5-197">Beachten Sie beim Anpassen des Mauszeigers Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1ced5-197">If you need to customize the mouse cursor:</span></span>

- <span data-ttu-id="1ced5-198">Verwenden Sie immer den Pfeilcursor (</span><span class="sxs-lookup"><span data-stu-id="1ced5-198">Always use the arrow cursor (</span></span>![Pfeilcursor](images/cursor-arrow.png)<span data-ttu-id="1ced5-200">) für klickbare Elemente.</span><span class="sxs-lookup"><span data-stu-id="1ced5-200">) for clickable elements.</span></span> <span data-ttu-id="1ced5-201">Verwenden Sie den Zeigefingercursor (</span><span class="sxs-lookup"><span data-stu-id="1ced5-201">don't use the pointing hand cursor (</span></span>![Zeigefingercursor](images/cursor-pointinghand.png)<span data-ttu-id="1ced5-203">) nicht für Links oder andere interaktive Elemente.</span><span class="sxs-lookup"><span data-stu-id="1ced5-203">) for links or other interactive elements.</span></span> <span data-ttu-id="1ced5-204">Verwenden Sie stattdessen Zeigeeffekte (wie bereits beschrieben).</span><span class="sxs-lookup"><span data-stu-id="1ced5-204">Instead, use hover effects (described earlier).</span></span>
- <span data-ttu-id="1ced5-205">Verwenden Sie den Textcursor (</span><span class="sxs-lookup"><span data-stu-id="1ced5-205">Use the text cursor (</span></span>![Textcursor](images/cursor-text.png)<span data-ttu-id="1ced5-207">) für auswählbaren Text.</span><span class="sxs-lookup"><span data-stu-id="1ced5-207">) for selectable text.</span></span>
- <span data-ttu-id="1ced5-208">Verwenden Sie den Bewegungscursor (</span><span class="sxs-lookup"><span data-stu-id="1ced5-208">Use the move cursor (</span></span>![Bewegungscursor](images/cursor-move.png)<span data-ttu-id="1ced5-210">), wenn die primäre Aktion eine Bewegung ist (etwa beim Ziehen oder Zuschneiden).</span><span class="sxs-lookup"><span data-stu-id="1ced5-210">) when moving is the primary action (such as dragging or cropping).</span></span> <span data-ttu-id="1ced5-211">Verwenden Sie den Bewegungscursor nicht, wenn die primäre Aktion eine Navigationsaktion ist (etwa bei Start-Kacheln).</span><span class="sxs-lookup"><span data-stu-id="1ced5-211">Don't use the move cursor for elements where the primary action is navigation (such as Start tiles).</span></span>
- <span data-ttu-id="1ced5-212">Verwenden Sie die Cursor für horizontale, vertikale und diagonale Größenänderung (</span><span class="sxs-lookup"><span data-stu-id="1ced5-212">Use the horizontal, vertical and diagonal resize cursors (</span></span>![Cursor für vertikale Größenänderung](images/cursor-vertical.png)<span data-ttu-id="1ced5-214">,</span><span class="sxs-lookup"><span data-stu-id="1ced5-214">,</span></span> ![Cursor für horizontale Größenänderung](images/cursor-horizontal.png)<span data-ttu-id="1ced5-216">,</span><span class="sxs-lookup"><span data-stu-id="1ced5-216">,</span></span> ![Cursor für diagonale Größenänderung (unten links, oben rechts)](images/cursor-diagonal2.png)<span data-ttu-id="1ced5-218">,</span><span class="sxs-lookup"><span data-stu-id="1ced5-218">,</span></span> ![Cursor für diagonale Größenänderung (oben links, unten rechts)](images/cursor-diagonal1.png)<span data-ttu-id="1ced5-220">), wenn die Größe eines Objekts geändert werden kann.</span><span class="sxs-lookup"><span data-stu-id="1ced5-220">), when an object is resizable.</span></span>
- <span data-ttu-id="1ced5-221">Verwenden Sie den Handcursor (</span><span class="sxs-lookup"><span data-stu-id="1ced5-221">Use the grasping hand cursors (</span></span>![Handcursor (offen)](images/cursor-pan1.png)<span data-ttu-id="1ced5-223">,</span><span class="sxs-lookup"><span data-stu-id="1ced5-223">,</span></span> ![Handcursor (geschlossen)](images/cursor-pan2.png)<span data-ttu-id="1ced5-225">) beim Verschieben von Inhalt innerhalb einer Canvas (etwa bei einer Karte).</span><span class="sxs-lookup"><span data-stu-id="1ced5-225">) when panning content within a fixed canvas (such as a map).</span></span>

## <a name="related-articles"></a><span data-ttu-id="1ced5-226">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="1ced5-226">Related articles</span></span>

- [<span data-ttu-id="1ced5-227">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="1ced5-227">Handle pointer input</span></span>](handle-pointer-input.md)
- [<span data-ttu-id="1ced5-228">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="1ced5-228">Identify input devices</span></span>](identify-input-devices.md)
- [<span data-ttu-id="1ced5-229">Übersicht über Ereignisse und Routingereignisse</span><span class="sxs-lookup"><span data-stu-id="1ced5-229">Events and routed events overview</span></span>](https://docs.microsoft.com/windows/uwp/xaml-platform/events-and-routed-events-overview)

### <a name="samples"></a><span data-ttu-id="1ced5-230">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1ced5-230">Samples</span></span>

- [<span data-ttu-id="1ced5-231">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="1ced5-231">Basic input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620302)
- [<span data-ttu-id="1ced5-232">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="1ced5-232">Low latency input sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=620304)
- [<span data-ttu-id="1ced5-233">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="1ced5-233">User interaction mode sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619894)
- [<span data-ttu-id="1ced5-234">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="1ced5-234">Focus visuals sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619895)