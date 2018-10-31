---
author: Karl-Bridge-Microsoft
Description: Receive, process, and manage input data from pointing devices such as touch, mouse, pen/stylus, and touchpad, in your Universal Windows Platform (UWP) applications.
title: Behandeln von Zeigereingaben
ms.assetid: BDBC9E33-4037-4671-9596-471DCF855C82
label: Handle pointer input
template: detail.hbs
keywords: Stift, Maus, Touchpad, Toucheingabe, Zeiger, Eingabe, Benutzerinteraktionen
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ba685f30eb0cf94314996587073a82440cf6c951
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5833435"
---
# <a name="handle-pointer-input"></a><span data-ttu-id="16a96-103">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="16a96-103">Handle pointer input</span></span>

<span data-ttu-id="16a96-104">Empfangen, verarbeiten und verwalten Sie Eingabedaten von Zeigegeräten (z. B. Toucheingaben, Maus, Zeichen-/Eingabestift und Touchpad) in Anwendungen für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="16a96-104">Receive, process, and manage input data from pointing devices (such as touch, mouse, pen/stylus, and touchpad) in your Universal Windows Platform (UWP) applications.</span></span>

> [!Important]
> <span data-ttu-id="16a96-105">Erstellen Sie benutzerdefinierte Interaktionen nur dann, wenn ein eindeutiger, klar umrissener Bedarf besteht und die von den Plattformsteuerelementen unterstützten Interaktionen Ihr Szenario nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="16a96-105">Create custom interactions only if there is a clear, well-defined requirement and the interactions supported by the platform controls don't support your scenario.</span></span>  
> <span data-ttu-id="16a96-106">Wenn Sie die Interaktionserfahrungen in Ihrer Windows-Anwendung anpassen, erwarten Benutzer, dass sie konsistent, intuitiv und leicht auffindbar sind.</span><span class="sxs-lookup"><span data-stu-id="16a96-106">If you customize the interaction experiences in your Windows application, users expect them to be consistent, intuitive, and discoverable.</span></span> <span data-ttu-id="16a96-107">Aus diesen Gründen wird empfohlen, Ihre benutzerdefinierten Interaktionen nach denen zu modellieren, die von den [Plattformsteuerelementen](../controls-and-patterns/controls-by-function.md) unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="16a96-107">For these reasons, we recommend that you model your custom interactions on those supported by the [platform controls](../controls-and-patterns/controls-by-function.md).</span></span> <span data-ttu-id="16a96-108">Die Plattformsteuerelemente bieten umfassende Funktionen für UWP-Benutzerinteraktionen (Universelle Windows-Plattform) wie Standardinteraktionen, animierte Physikeffekte, visuelles Feedback und Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="16a96-108">The platform controls provide the full Universal Windows Platform (UWP) user interaction experience, including standard interactions, animated physics effects, visual feedback, and accessibility.</span></span> 

## <a name="important-apis"></a><span data-ttu-id="16a96-109">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="16a96-109">Important APIs</span></span>
- [<span data-ttu-id="16a96-110">Windows.Devices.Input</span><span class="sxs-lookup"><span data-stu-id="16a96-110">Windows.Devices.Input</span></span>](https://msdn.microsoft.com/library/windows/apps/br225648)
- [<span data-ttu-id="16a96-111">Windows.UI.Input</span><span class="sxs-lookup"><span data-stu-id="16a96-111">Windows.UI.Input</span></span>](https://msdn.microsoft.com/library/windows/apps/br208383)
- [<span data-ttu-id="16a96-112">Windows.UI.Xaml.Input</span><span class="sxs-lookup"><span data-stu-id="16a96-112">Windows.UI.Xaml.Input</span></span>](https://msdn.microsoft.com/library/windows/apps/br242084)

## <a name="pointers"></a><span data-ttu-id="16a96-113">Zeiger</span><span class="sxs-lookup"><span data-stu-id="16a96-113">Pointers</span></span>
<span data-ttu-id="16a96-114">Bei den meisten Interaktionsfunktionen ist typischerweise der Benutzer involviert, der das Objekt identifizieren muss, mit dem er interagieren möchte, indem er mithilfe von Eingabegeräten wie Toucheingabe, Maus, Zeichen-/Eingabestift und Touchpad darauf zeigt.</span><span class="sxs-lookup"><span data-stu-id="16a96-114">Most interaction experiences typically involve the user identifying the object they want to interact with by pointing at it through input devices such as touch, mouse, pen/stylus, and touchpad.</span></span> <span data-ttu-id="16a96-115">Da die von diesen Eingabegeräten bereitgestellten HID-Rohdaten (Human Interface Device) viele allgemeine Eigenschaften enthalten, werden die Daten an einen einheitlichen Eingabestapel weitergeleitet und in geräteunabhängigen Zeigerdaten konsolidiert und zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="16a96-115">Because the raw Human Interface Device (HID) data provided by these input devices includes many common properties, the data is promoted and consolidated into a unified input stack and exposed as device-agnostic pointer data.</span></span> <span data-ttu-id="16a96-116">Ihre UWP-Anwendungen können dann diese Daten ohne Rücksicht auf das verwendete Eingabegerät verwenden.</span><span class="sxs-lookup"><span data-stu-id="16a96-116">Your UWP applications can then consume this data without worrying about the input device being used.</span></span>

> [!NOTE]
> <span data-ttu-id="16a96-117">Gerätespezifische Informationen werden auch von den HID-Rohdaten weitergeleitet, falls dies für die App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="16a96-117">Device-specific info is also promoted from the raw HID data should your app require it.</span></span>
 

<span data-ttu-id="16a96-118">Jeder Eingabepunkt (oder Kontakt) in dem Eingabestapel wird durch ein [**Pointer**](https://msdn.microsoft.com/library/windows/apps/br227968)-Objekt dargestellt, das über den [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076)-Parameter in den verschiedenen Zeigerereignishandlern zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-118">Each input point (or contact) on the input stack is represented by a [**Pointer**](https://msdn.microsoft.com/library/windows/apps/br227968) object exposed through the [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076) parameter in the various pointer event handlers.</span></span> <span data-ttu-id="16a96-119">Bei Verwendung mehrerer Stifte oder der Mehrfingereingabe wird jeder Kontakt als separater Eingabezeiger behandelt.</span><span class="sxs-lookup"><span data-stu-id="16a96-119">In the case of multi-pen or multi-touch input, each contact is treated as a unique input pointer.</span></span>

## <a name="pointer-events"></a><span data-ttu-id="16a96-120">Zeigerereignisse</span><span class="sxs-lookup"><span data-stu-id="16a96-120">Pointer events</span></span>


<span data-ttu-id="16a96-121">Zeigerereignisse machen grundlegende Informationen wie den Typ des Eingabegeräts und den Erkennungszustand (im Bereich oder bei Kontakt) sowie erweiterte Informationen wie Position, Druck und Kontaktgeometrie verfügbar.</span><span class="sxs-lookup"><span data-stu-id="16a96-121">Pointer events expose basic info such as input device type and detection state (in range or in contact), and extended info such as location, pressure, and contact geometry.</span></span> <span data-ttu-id="16a96-122">Darüber hinaus sind auch bestimmte gerätespezifische Eigenschaften verfügbar, z. B. welche Maustaste ein Benutzer gedrückt hat oder ob die Radiergummispitze des Zeichenstifts verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-122">In addition, specific device properties such as which mouse button a user pressed or whether the pen eraser tip is being used are also available.</span></span> <span data-ttu-id="16a96-123">Wenn die App zwischen Eingabegeräten und ihren Funktionen unterscheiden muss, finden Sie entsprechende Informationen unter [Erkennen von Eingabegeräten](identify-input-devices.md).</span><span class="sxs-lookup"><span data-stu-id="16a96-123">If your app needs to differentiate between input devices and their capabilities, see [Identify input devices](identify-input-devices.md).</span></span>

<span data-ttu-id="16a96-124">UWP-Apps können die folgenden Zeigerereignisse überwachen:</span><span class="sxs-lookup"><span data-stu-id="16a96-124">UWP apps can listen for the following pointer events:</span></span>

> [!NOTE]
> <span data-ttu-id="16a96-125">Schränken Sie Zeigereingaben auf ein bestimmtes UI-Element ein, indem Sie [**CapturePointer**](https://msdn.microsoft.com/library/windows/apps/br208918) für dieses Element in einem Zeigerereignishandler aufrufen.</span><span class="sxs-lookup"><span data-stu-id="16a96-125">Constrain pointer input to a specific UI element by calling  [**CapturePointer**](https://msdn.microsoft.com/library/windows/apps/br208918) on that element within a pointer event handler.</span></span> <span data-ttu-id="16a96-126">Wenn ein Zeiger von einem Element erfasst wurde, empfängt nur dieses Objekt die Zeigereingabeereignisse, auch wenn sich der Mauszeiger aus dem Begrenzungsbereich des Objekts heraus bewegt.</span><span class="sxs-lookup"><span data-stu-id="16a96-126">When a pointer is captured by an element, only that object receives pointer input events, even when the pointer moves outside the bounding area of the object.</span></span> <span data-ttu-id="16a96-127">Die Option [**IsInContact**](https://msdn.microsoft.com/library/windows/apps/br227976) (gedrückte Maustaste, Touch oder Stift in Kontakt) muss „true“ sein, damit **CapturePointer** erfolgreich ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="16a96-127">The [**IsInContact**](https://msdn.microsoft.com/library/windows/apps/br227976) (mouse button pressed, touch or stylus in contact) must be true for **CapturePointer** to be successful.</span></span>
 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="16a96-128">Ereignis</span><span class="sxs-lookup"><span data-stu-id="16a96-128">Event</span></span></th>
<th align="left"><span data-ttu-id="16a96-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="16a96-129">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208964"><strong><span data-ttu-id="16a96-130">PointerCanceled</span><span class="sxs-lookup"><span data-stu-id="16a96-130">PointerCanceled</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-131">Tritt auf, wenn ein Zeiger von der Plattform abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-131">Occurs when a pointer is canceled by the platform.</span></span> <span data-ttu-id="16a96-132">Dies kann unter den folgenden Umständen auftreten.</span><span class="sxs-lookup"><span data-stu-id="16a96-132">This can occur in the following circumstances:</span></span></p>
<ul>
<li><span data-ttu-id="16a96-133">Touchzeiger werden abgebrochen, wenn ein Zeichenstift innerhalb des Bereichs der Eingabeoberfläche erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-133">Touch pointers are canceled when a pen is detected within range of the input surface.</span></span></li>
<li><span data-ttu-id="16a96-134">Für mehr als 100ms wird kein aktiver Kontakt erkannt.</span><span class="sxs-lookup"><span data-stu-id="16a96-134">An active contact is not detected for more than 100 ms.</span></span></li>
<li><span data-ttu-id="16a96-135">Monitor/Anzeige wird geändert (Auflösung, Einstellungen, Konfigurationen mit mehreren Bildschirmen).</span><span class="sxs-lookup"><span data-stu-id="16a96-135">Monitor/display is changed (resolution, settings, multi-mon configuration).</span></span></li>
<li><span data-ttu-id="16a96-136">Der Desktop ist gesperrt, oder der Benutzer hat sich abgemeldet.</span><span class="sxs-lookup"><span data-stu-id="16a96-136">The desktop is locked or the user has logged off.</span></span></li>
<li><span data-ttu-id="16a96-137">Die Anzahl gleichzeitiger Kontakte hat die vom Gerät unterstützte Anzahl überschritten.</span><span class="sxs-lookup"><span data-stu-id="16a96-137">The number of simultaneous contacts exceeded the number supported by the device.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208965"><strong><span data-ttu-id="16a96-138">PointerCaptureLost</span><span class="sxs-lookup"><span data-stu-id="16a96-138">PointerCaptureLost</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-139">Tritt auf, wenn ein anderes Benutzeroberflächenelement den Zeiger erfasst, der Zeiger freigegeben wurde oder ein anderer Zeiger programmgesteuert erfasst wurde.</span><span class="sxs-lookup"><span data-stu-id="16a96-139">Occurs when another UI element captures the pointer, the pointer was released, or another pointer was programmatically captured.</span></span></p>
<div class="alert"><span data-ttu-id="16a96-140">
<strong>Hinweis:</strong>es gibt kein entsprechendes zeigererfassungsereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-140">
<strong>Note</strong>There is no corresponding pointer capture event.</span></span>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208968"><strong><span data-ttu-id="16a96-141">PointerEntered</span><span class="sxs-lookup"><span data-stu-id="16a96-141">PointerEntered</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-142">Tritt auf, wenn der Zeiger in den Begrenzungsbereich eines Elements eintritt.</span><span class="sxs-lookup"><span data-stu-id="16a96-142">Occurs when a pointer enters the bounding area of an element.</span></span> <span data-ttu-id="16a96-143">Dies kann geringfügig anders für Touch-, Touchpad-, Maus- und Stifteingaben passieren.</span><span class="sxs-lookup"><span data-stu-id="16a96-143">This can happen in slightly different ways for touch, touchpad, mouse, and pen input.</span></span></p>
<ul>
<li><span data-ttu-id="16a96-144">Für Toucheingaben ist zur Auslösung dieses Ereignisses eine Fingerkontakt erforderlich, entweder über eine direkte Toucheingabe oder durch Bewegen in den Begrenzungsbereich des Elements.</span><span class="sxs-lookup"><span data-stu-id="16a96-144">Touch requires a finger contact to fire this event, either from a direct touch down on the element or from moving into the bounding area of the element.</span></span></li>
<li><span data-ttu-id="16a96-145">Maus und Touchpad haben beide einen Cursor auf dem Bildschirm, der immer sichtbar ist und dieses Ereignis auslöst, auch wenn keine Maus- oder Touchpadtaste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-145">Mouse and touchpad both have an on-screen cursor that is always visible and fires this event even if no mouse or touchpad button is pressed.</span></span></li>
<li><span data-ttu-id="16a96-146">Wie bei der Toucheingabe löst der Stift das Ereignis über eine direkte Stifteingabe oder durch Bewegen in den Begrenzungsbereich des Elements aus.</span><span class="sxs-lookup"><span data-stu-id="16a96-146">Like touch, pen fires this event with a direct pen down on the element or from moving into the bounding area of the element.</span></span> <span data-ttu-id="16a96-147">Der Stift verfügt jedoch auch über einen Hoverzustand ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)), der das Ereignis bei „true“ auslöst.</span><span class="sxs-lookup"><span data-stu-id="16a96-147">However, pen also has a hover state ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)) that, when true, fires this event.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208969"><strong><span data-ttu-id="16a96-148">PointerExited</span><span class="sxs-lookup"><span data-stu-id="16a96-148">PointerExited</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-149">Tritt auf, wenn der Zeiger den Begrenzungsbereich eines Elements verlässt.</span><span class="sxs-lookup"><span data-stu-id="16a96-149">Occurs when a pointer leaves the bounding area of an element.</span></span> <span data-ttu-id="16a96-150">Dies kann geringfügig anders für Touch-, Touchpad-, Maus- und Stifteingaben passieren.</span><span class="sxs-lookup"><span data-stu-id="16a96-150">This can happen in slightly different ways for touch, touchpad, mouse, and pen input.</span></span></p>
<ul>
<li><span data-ttu-id="16a96-151">Die Toucheingabe erfordert einen Fingerkontakt und löst dieses Ereignis aus, wenn sich der Mauszeiger aus dem Begrenzungsbereich des Elements heraus bewegt.</span><span class="sxs-lookup"><span data-stu-id="16a96-151">Touch requires a finger contact and fires this event when the pointer moves out of the bounding area of the element.</span></span></li>
<li><span data-ttu-id="16a96-152">Maus und Touchpad haben beide einen Cursor auf dem Bildschirm, der immer sichtbar ist und dieses Ereignis auslöst, auch wenn keine Maus- oder Touchpadtaste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-152">Mouse and touchpad both have an on-screen cursor that is always visible and fires this event even if no mouse or touchpad button is pressed.</span></span></li>
<li><span data-ttu-id="16a96-153">Wie bei der Toucheingabe löst der Stift dieses Ereignis beim Bewegen aus dem Begrenzungsbereich des Elements heraus aus.</span><span class="sxs-lookup"><span data-stu-id="16a96-153">Like touch, pen fires this event when moving out of the bounding area of the element.</span></span> <span data-ttu-id="16a96-154">Der Stift verfügt jedoch auch über einen Hoverzustand ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)), der das Ereignis auslöst, wenn sich der Zustand von „true“ in „false“ ändert.</span><span class="sxs-lookup"><span data-stu-id="16a96-154">However, pen also has a hover state ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)) that fires this event when the state changes from true to false.</span></span></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208970"><strong><span data-ttu-id="16a96-155">PointerMoved</span><span class="sxs-lookup"><span data-stu-id="16a96-155">PointerMoved</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-156">Tritt auf, wenn ein Zeiger Koordinaten, Schaltflächenzustand, Druck, Neigung oder Kontaktgeometrie (z. B. Breite und Höhe) innerhalb des Begrenzungsbereichs eines Elements ändert.</span><span class="sxs-lookup"><span data-stu-id="16a96-156">Occurs when a pointer changes coordinates, button state, pressure, tilt, or contact geometry (for example, width and height) within the bounding area of an element.</span></span> <span data-ttu-id="16a96-157">Dies kann geringfügig anders für Touch-, Touchpad-, Maus- und Stifteingaben passieren.</span><span class="sxs-lookup"><span data-stu-id="16a96-157">This can happen in slightly different ways for touch, touchpad, mouse, and pen input.</span></span></p>
<ul>
<li><span data-ttu-id="16a96-158">Die Toucheingabe erfordert einen Fingerkontakt und löst dieses Ereignis nur aus, wenn ein Kontakt innerhalb des Begrenzungsbereichs des Elements besteht.</span><span class="sxs-lookup"><span data-stu-id="16a96-158">Touch requires a finger contact and fires this event only when in contact within the bounding area of the element.</span></span></li>
<li><span data-ttu-id="16a96-159">Maus und Touchpad haben beide einen Cursor auf dem Bildschirm, der immer sichtbar ist und dieses Ereignis auslöst, auch wenn keine Maus- oder Touchpadtaste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-159">Mouse and touchpad both have an on-screen cursor that is always visible and fires this event even if no mouse or touchpad button is pressed.</span></span></li>
<li><span data-ttu-id="16a96-160">Wie bei der Toucheingabe löst der Stift dieses Ereignis aus, wenn ein Kontakt innerhalb des Begrenzungsbereichs des Elements besteht.</span><span class="sxs-lookup"><span data-stu-id="16a96-160">Like touch, pen fires this event when in contact within the bounding area of the element.</span></span> <span data-ttu-id="16a96-161">Der Stift verfügt jedoch auch über einen Hoverzustand ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)), der dieses Ereignis bei „true“ und innerhalb des Begrenzungsbereichs des Elements auslöst.</span><span class="sxs-lookup"><span data-stu-id="16a96-161">However, pen also has a hover state ([IsInRange](https://msdn.microsoft.com/library/windows/apps/br227977)) that, when true and within the bounding area of the element, fires this event.</span></span></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208971"><strong><span data-ttu-id="16a96-162">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="16a96-162">PointerPressed</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-163">Tritt auf, wenn der Zeiger eine Drückaktion (z. B. eine Fingereingabe, gedrückte Maustaste, Stifteingabe oder gedrückte Touchpadtaste) innerhalb des Begrenzungsbereichs eines Elements angibt.</span><span class="sxs-lookup"><span data-stu-id="16a96-163">Occurs when the pointer indicates a press action (such as a touch down, mouse button down, pen down, or touchpad button down) within the bounding area of an element.</span></span></p>
<p><span data-ttu-id="16a96-164">[CapturePointer](https://msdn.microsoft.com/library/windows/apps/br208918) muss aus dem Handler für dieses Ereignis aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="16a96-164">[CapturePointer](https://msdn.microsoft.com/library/windows/apps/br208918) must be called from the handler for this event.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208972"><strong><span data-ttu-id="16a96-165">PointerReleased</span><span class="sxs-lookup"><span data-stu-id="16a96-165">PointerReleased</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-166">Tritt auf, wenn der Zeiger eine Loslass-Aktion (z. B. ein Finger bewegt sich nach oben, Maustaste, Stift oder Touchpadtaste werden losgelassen) innerhalb des Begrenzungsbereichs eines Elements anzeigt, oder wenn der Zeiger außerhalb des Begrenzungsbereichs erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-166">Occurs when the pointer indicates a release action (such as a touch up, mouse button up, pen up, or touchpad button up) within the bounding area of an element or, if the pointer is captured, outside the bounding area.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="https://msdn.microsoft.com/library/windows/apps/br208973"><strong><span data-ttu-id="16a96-167">PointerWheelChanged</span><span class="sxs-lookup"><span data-stu-id="16a96-167">PointerWheelChanged</span></span></strong></a></p></td>
<td align="left"><p><span data-ttu-id="16a96-168">Tritt auf, wenn das Mausrad gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-168">Occurs when the mouse wheel is rotated.</span></span></p>
<p><span data-ttu-id="16a96-169">Die Mauseingabe wird einem einzelnen Zeiger zugeordnet, der bei der ersten Ermittlung einer Mauseingabe zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-169">Mouse input is associated with a single pointer assigned when mouse input is first detected.</span></span> <span data-ttu-id="16a96-170">Durch das Klicken auf eine Maustaste (links, Mausrad oder rechts) wird über das [PointerMoved](https://msdn.microsoft.com/library/windows/apps/br208970)-Ereignis eine zweite Zuordnung zwischen dem Zeiger und dieser Taste erstellt.</span><span class="sxs-lookup"><span data-stu-id="16a96-170">Clicking a mouse button (left, wheel, or right) creates a secondary association between the pointer and that button through the [PointerMoved](https://msdn.microsoft.com/library/windows/apps/br208970) event.</span></span></p></td>
</tr>
</tbody>
</table> 

## <a name="pointer-event-example"></a><span data-ttu-id="16a96-171">Beispiel für Zeigerereignis</span><span class="sxs-lookup"><span data-stu-id="16a96-171">Pointer event example</span></span>

<span data-ttu-id="16a96-172">Nachfolgend sehen Sie einige Codeausschnitt aus einer einfachen Zeigerverfolgungs-App, in denen gezeigt wird, wie Ereignisse für mehrere Zeiger überwacht und behandelt und verschiedene Eigenschaften für die verbundenen Zeiger abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="16a96-172">Here are some code snippets from a basic pointer tracking app that show how to listen for and handle events for multiple pointers, and get various properties for the associated pointers.</span></span>

![Benutzeroberfläche der Zeigeranwendung](images/pointers/pointers1.gif)

**<span data-ttu-id="16a96-174">Laden Sie dieses Beispiel aus [Beispiel für die Zeigereingabe (einfach)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="16a96-174">Download this sample from [Pointer input sample (basic)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers.zip)</span></span>**

### <a name="create-the-ui"></a><span data-ttu-id="16a96-175">Erstellen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="16a96-175">Create the UI</span></span>

<span data-ttu-id="16a96-176">In diesem Beispiel wird ein [Rechteck](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.shapes.rectangle) (`Target`) als Objekt verwendet, das Zeigereingaben nutzt.</span><span class="sxs-lookup"><span data-stu-id="16a96-176">For this example, we use a [Rectangle](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.shapes.rectangle) (`Target`) as the object consuming pointer input.</span></span> <span data-ttu-id="16a96-177">Die Farbe des Ziels ändert sich, wenn sich der Zeigerstatus ändert.</span><span class="sxs-lookup"><span data-stu-id="16a96-177">The color of the target changes when the pointer status changes.</span></span>

<span data-ttu-id="16a96-178">Details zu jedem Zeiger werden in einem schwebenden [TextBlock](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.TextBlock) angezeigt, der sich mit dem Mauszeiger bewegt.</span><span class="sxs-lookup"><span data-stu-id="16a96-178">Details for each pointer are displayed in a floating [TextBlock](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.TextBlock) that follows the pointer as it moves.</span></span> <span data-ttu-id="16a96-179">Die Zeigerereignisse selbst werden im [RichTextBlock](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichTextBlock) rechts neben dem Rechteck gemeldet.</span><span class="sxs-lookup"><span data-stu-id="16a96-179">The pointer events themselves are reported in the [RichTextBlock](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Xaml.Controls.RichTextBlock) to the right of the rectangle.</span></span>

<span data-ttu-id="16a96-180">Im Folgenden ist der XAML-Code (Extensible Application Markup Language) für die Benutzeroberfläche in diesem Beispiel aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="16a96-180">This is the Extensible Application Markup Language (XAML) for the UI in this example.</span></span> 

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="*" />
        <ColumnDefinition Width="250"/>
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="*" />
        <RowDefinition Height="320" />
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Canvas Name="Container" 
            Grid.Column="0"
            Grid.Row="1"
            HorizontalAlignment="Center" 
            VerticalAlignment="Center" 
            Margin="245,0" 
            Height="320"  Width="640">
        <Rectangle Name="Target" 
                    Fill="#FF0000" 
                    Stroke="Black" 
                    StrokeThickness="0"
                    Height="320" Width="640" />
    </Canvas>
    <Grid Grid.Column="1" Grid.Row="0" Grid.RowSpan="3">
        <Grid.RowDefinitions>
            <RowDefinition Height="50" />
            <RowDefinition Height="*" />
        </Grid.RowDefinitions>
        <Button Name="buttonClear" 
                Grid.Row="0"
                Content="Clear"
                Foreground="White"
                HorizontalAlignment="Stretch" 
                VerticalAlignment="Stretch">
        </Button>
        <ScrollViewer Name="eventLogScrollViewer" Grid.Row="1" 
                        VerticalScrollMode="Auto" 
                        Background="Black">                
            <RichTextBlock Name="eventLog"  
                        TextWrapping="Wrap" 
                        Foreground="#FFFFFF" 
                        ScrollViewer.VerticalScrollBarVisibility="Visible" 
                        ScrollViewer.HorizontalScrollBarVisibility="Disabled"
                        Grid.ColumnSpan="2">
            </RichTextBlock>
        </ScrollViewer>
    </Grid>
</Grid>
```

### <a name="listen-for-pointer-events"></a><span data-ttu-id="16a96-181">Lauschen auf Zeigerereignisse</span><span class="sxs-lookup"><span data-stu-id="16a96-181">Listen for pointer events</span></span>

<span data-ttu-id="16a96-182">In den meisten Fällen wird empfohlen, Zeigerinformationen über die [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076) des Ereignishandlers abzurufen.</span><span class="sxs-lookup"><span data-stu-id="16a96-182">In most cases, we recommend that you get pointer info through the [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076) of the event handler.</span></span>

<span data-ttu-id="16a96-183">Sollte das Ereignisargument die erforderlichen Zeigerdetails nicht liefern, können Sie über die Methoden [**GetCurrentPoint**](https://msdn.microsoft.com/library/windows/apps/hh943077) und [**GetIntermediatePoints**](https://msdn.microsoft.com/library/windows/apps/hh943078) von [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076) auf die von einem [**PointerPoint**](https://msdn.microsoft.com/library/windows/apps/br242038)-Objekt bereitgestellten erweiterten Zeigerdaten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="16a96-183">If the event argument doesn't expose the pointer details required, you can get access to extended [**PointerPoint**](https://msdn.microsoft.com/library/windows/apps/br242038) info exposed through the [**GetCurrentPoint**](https://msdn.microsoft.com/library/windows/apps/hh943077) and [**GetIntermediatePoints**](https://msdn.microsoft.com/library/windows/apps/hh943078) methods of [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076).</span></span>

<span data-ttu-id="16a96-184">Der folgende Code richtet das globale Verzeichnisobjekt für die Verfolgung jedes aktiven Zeigers ein und identifiziert die verschiedenen Zeigerereignislistener für das Zielobjekt.</span><span class="sxs-lookup"><span data-stu-id="16a96-184">The following code sets up the global dictionary object for tracking each active pointer, and identifies the various pointer event listeners for the target object.</span></span>

```CSharp
// Dictionary to maintain information about each active pointer. 
// An entry is added during PointerPressed/PointerEntered events and removed 
// during PointerReleased/PointerCaptureLost/PointerCanceled/PointerExited events.
Dictionary<uint, Windows.UI.Xaml.Input.Pointer> pointers;

public MainPage()
{
    this.InitializeComponent();

    // Initialize the dictionary.
    pointers = new Dictionary<uint, Windows.UI.Xaml.Input.Pointer>();

    // Declare the pointer event handlers.
    Target.PointerPressed += 
        new PointerEventHandler(Target_PointerPressed);
    Target.PointerEntered += 
        new PointerEventHandler(Target_PointerEntered);
    Target.PointerReleased += 
        new PointerEventHandler(Target_PointerReleased);
    Target.PointerExited += 
        new PointerEventHandler(Target_PointerExited);
    Target.PointerCanceled += 
        new PointerEventHandler(Target_PointerCanceled);
    Target.PointerCaptureLost += 
        new PointerEventHandler(Target_PointerCaptureLost);
    Target.PointerMoved += 
        new PointerEventHandler(Target_PointerMoved);
    Target.PointerWheelChanged += 
        new PointerEventHandler(Target_PointerWheelChanged);

    buttonClear.Click += 
        new RoutedEventHandler(ButtonClear_Click);
}
```

### <a name="handle-pointer-events"></a><span data-ttu-id="16a96-185">Behandeln von Zeigerereignissen</span><span class="sxs-lookup"><span data-stu-id="16a96-185">Handle pointer events</span></span>

<span data-ttu-id="16a96-186">Im nächsten Schritt wird UI-Feedback verwendet, um die Verwendung einfacher Zeigerereignishandler zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="16a96-186">Next, we use UI feedback to demonstrate basic pointer event handlers.</span></span>

-   <span data-ttu-id="16a96-187">Der folgende Handler kontrolliert das [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-187">This handler manages the [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) event.</span></span> <span data-ttu-id="16a96-188">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird zum aktiven Zeigerverzeichnis hinzugefügt, und die Zeigerdetails werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16a96-188">We add the event to the event log, add the pointer to the active pointer dictionary, and display the pointer details.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16a96-189">Die Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) und [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) treten nicht immer paarweise auf.</span><span class="sxs-lookup"><span data-stu-id="16a96-189">[**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) and [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) events do not always occur in pairs.</span></span> <span data-ttu-id="16a96-190">Die App sollte auf jedes Ereignis lauschen und dieses behandeln, das einen Zeiger nach unten beenden könnte (beispielsweise [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969), [**PointerCanceled**](https://msdn.microsoft.com/library/windows/apps/br208964) und [**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965)).</span><span class="sxs-lookup"><span data-stu-id="16a96-190">Your app should listen for and handle any event that might conclude a pointer down (such as [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969), [**PointerCanceled**](https://msdn.microsoft.com/library/windows/apps/br208964), and [**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965)).</span></span>      

```csharp
/// <summary>
/// The pointer pressed event handler.
/// PointerPressed and PointerReleased don't always occur in pairs. 
/// Your app should listen for and handle any event that can conclude 
/// a pointer down (PointerExited, PointerCanceled, PointerCaptureLost).
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
void Target_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Down: " + ptrPt.PointerId);

    // Lock the pointer to the target.
    Target.CapturePointer(e.Pointer);

    // Update event log.
    UpdateEventLog("Pointer captured: " + ptrPt.PointerId);

    // Check if pointer exists in dictionary (ie, enter occurred prior to press).
    if (!pointers.ContainsKey(ptrPt.PointerId))
    {
        // Add contact to dictionary.
        pointers[ptrPt.PointerId] = e.Pointer;
    }

    // Change background color of target when pointer contact detected.
    Target.Fill = new SolidColorBrush(Windows.UI.Colors.Green);

    // Display pointer details.
    CreateInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-191">Der folgende Handler kontrolliert das [**PointerEntered**](https://msdn.microsoft.com/library/windows/apps/br208968)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-191">This handler manages the [**PointerEntered**](https://msdn.microsoft.com/library/windows/apps/br208968) event.</span></span> <span data-ttu-id="16a96-192">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird zur Zeigerauflistung hinzugefügt, und die Zeigerdetails werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16a96-192">We add the event to the event log, add the pointer to the pointer collection, and display the pointer details.</span></span>

```csharp
/// <summary>
/// The pointer entered event handler.
/// We do not capture the pointer on this event.
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerEntered(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Entered: " + ptrPt.PointerId);

    // Check if pointer already exists (if enter occurred prior to down).
    if (!pointers.ContainsKey(ptrPt.PointerId))
    {
        // Add contact to dictionary.
        pointers[ptrPt.PointerId] = e.Pointer;
    }

    if (pointers.Count == 0)
    {
        // Change background color of target when pointer contact detected.
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Blue);
    }

    // Display pointer details.
    CreateInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-193">Der folgende Handler kontrolliert das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-193">This handler manages the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970) event.</span></span> <span data-ttu-id="16a96-194">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, und die Zeigerdetails werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="16a96-194">We add the event to the event log and update the pointer details.</span></span>

    > [!Important]
    > <span data-ttu-id="16a96-195">Die Mauseingabe wird einem einzelnen Zeiger zugeordnet, der bei der ersten Ermittlung einer Mauseingabe zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-195">Mouse input is associated with a single pointer assigned when mouse input is first detected.</span></span> <span data-ttu-id="16a96-196">Durch das Klicken auf eine Maustaste (links, Mausrad oder rechts) wird über das [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971)-Ereignis eine zweite Zuordnung zwischen dem Zeiger und dieser Taste erstellt.</span><span class="sxs-lookup"><span data-stu-id="16a96-196">Clicking a mouse button (left, wheel, or right) creates a secondary association between the pointer and that button through the [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) event.</span></span> <span data-ttu-id="16a96-197">Das [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972)-Ereignis wird nur ausgelöst, wenn dieselbe Maustaste losgelassen wird (dem Zeiger kann erst eine andere Taste zugeordnet werden, wenn dieses Ereignis abgeschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="16a96-197">The [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) event is fired only when that same mouse button is released (no other button can be associated with the pointer until this event is complete).</span></span> <span data-ttu-id="16a96-198">Aufgrund dieser exklusiven Zuordnung werden Klicks auf andere Maustasten über das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970)-Ereignis geleitet.</span><span class="sxs-lookup"><span data-stu-id="16a96-198">Because of this exclusive association, other mouse button clicks are routed through the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970) event.</span></span>     

```csharp
/// <summary>
/// The pointer moved event handler.
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerMoved(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Multiple, simultaneous mouse button inputs are processed here.
    // Mouse input is associated with a single pointer assigned when 
    // mouse input is first detected. 
    // Clicking additional mouse buttons (left, wheel, or right) during 
    // the interaction creates secondary associations between those buttons 
    // and the pointer through the pointer pressed event. 
    // The pointer released event is fired only when the last mouse button 
    // associated with the interaction (not necessarily the initial button) 
    // is released. 
    // Because of this exclusive association, other mouse button clicks are 
    // routed through the pointer move event.          
    if (ptrPt.PointerDevice.PointerDeviceType == Windows.Devices.Input.PointerDeviceType.Mouse)
    {
        if (ptrPt.Properties.IsLeftButtonPressed)
        {
            UpdateEventLog("Left button: " + ptrPt.PointerId);
        }
        if (ptrPt.Properties.IsMiddleButtonPressed)
        {
            UpdateEventLog("Wheel button: " + ptrPt.PointerId);
        }
        if (ptrPt.Properties.IsRightButtonPressed)
        {
            UpdateEventLog("Right button: " + ptrPt.PointerId);
        }
    }

    // Display pointer details.
    UpdateInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-199">Der folgende Handler kontrolliert das [**PointerWheelChanged**](https://msdn.microsoft.com/library/windows/apps/br208973)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-199">This handler manages the [**PointerWheelChanged**](https://msdn.microsoft.com/library/windows/apps/br208973) event.</span></span> <span data-ttu-id="16a96-200">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird zum Zeigerarray hinzugefügt (sofern erforderlich), und die Zeigerdetails werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16a96-200">We add the event to the event log, add the pointer to the pointer array (if necessary), and display the pointer details.</span></span>

```csharp
/// <summary>
/// The pointer wheel event handler.
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerWheelChanged(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Mouse wheel: " + ptrPt.PointerId);

    // Check if pointer already exists (for example, enter occurred prior to wheel).
    if (!pointers.ContainsKey(ptrPt.PointerId))
    {
        // Add contact to dictionary.
        pointers[ptrPt.PointerId] = e.Pointer;
    }

    // Display pointer details.
    CreateInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-201">Der folgende Handler kontrolliert das [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972)-Ereignis, bei dem der Kontakt mit dem Digitalisierungsgerät beendet wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-201">This handler manages the [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) event where contact with the digitizer is terminated.</span></span> <span data-ttu-id="16a96-202">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird aus der Zeigerauflistung entfernt, und die Zeigerdetails werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="16a96-202">We add the event to the event log, remove the pointer from the pointer collection, and update the pointer details.</span></span>

```csharp
/// <summary>
/// The pointer released event handler.
/// PointerPressed and PointerReleased don't always occur in pairs. 
/// Your app should listen for and handle any event that can conclude 
/// a pointer down (PointerExited, PointerCanceled, PointerCaptureLost).
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
void Target_PointerReleased(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Up: " + ptrPt.PointerId);

    // If event source is mouse or touchpad and the pointer is still 
    // over the target, retain pointer and pointer details.
    // Return without removing pointer from pointers dictionary.
    // For this example, we assume a maximum of one mouse pointer.
    if (ptrPt.PointerDevice.PointerDeviceType != Windows.Devices.Input.PointerDeviceType.Mouse)
    {
        // Update target UI.
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Red);

        DestroyInfoPop(ptrPt);

        // Remove contact from dictionary.
        if (pointers.ContainsKey(ptrPt.PointerId))
        {
            pointers[ptrPt.PointerId] = null;
            pointers.Remove(ptrPt.PointerId);
        }

        // Release the pointer from the target.
        Target.ReleasePointerCapture(e.Pointer);

        // Update event log.
        UpdateEventLog("Pointer released: " + ptrPt.PointerId);
    }
    else
    {
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Blue);
    }
}
```

-   <span data-ttu-id="16a96-203">Der folgende Handler kontrolliert das [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969)-Ereignis (wenn der Kontakt mit dem Digitizer beibehalten wird).</span><span class="sxs-lookup"><span data-stu-id="16a96-203">This handler manages the [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) event (when contact with the digitizer is maintained).</span></span> <span data-ttu-id="16a96-204">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird aus dem Zeigerarray entfernt, und die Zeigerdetails werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="16a96-204">We add the event to the event log, remove the pointer from the pointer array, and update the pointer details.</span></span>

```csharp
/// <summary>
/// The pointer exited event handler.
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerExited(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Pointer exited: " + ptrPt.PointerId);

    // Remove contact from dictionary.
    if (pointers.ContainsKey(ptrPt.PointerId))
    {
        pointers[ptrPt.PointerId] = null;
        pointers.Remove(ptrPt.PointerId);
    }

    if (pointers.Count == 0)
    {
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Red);
    }

    // Update the UI and pointer details.
    DestroyInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-205">Der folgende Handler kontrolliert das [**PointerCanceled**](https://msdn.microsoft.com/library/windows/apps/br208964)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-205">This handler manages the [**PointerCanceled**](https://msdn.microsoft.com/library/windows/apps/br208964) event.</span></span> <span data-ttu-id="16a96-206">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird aus dem Zeigerarray entfernt, und die Zeigerdetails werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="16a96-206">We add the event to the event log, remove the pointer from the pointer array, and update the pointer details.</span></span>

```csharp
/// <summary>
/// The pointer canceled event handler.
/// Fires for for various reasons, including: 
///    - Touch contact canceled by pen coming into range of the surface.
///    - The device doesn't report an active contact for more than 100ms.
///    - The desktop is locked or the user logged off. 
///    - The number of simultaneous contacts exceeded the number supported by the device.
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerCanceled(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Pointer canceled: " + ptrPt.PointerId);

    // Remove contact from dictionary.
    if (pointers.ContainsKey(ptrPt.PointerId))
    {
        pointers[ptrPt.PointerId] = null;
        pointers.Remove(ptrPt.PointerId);
    }

    if (pointers.Count == 0)
    {
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Black);
    }

    DestroyInfoPop(ptrPt);
}
```

-   <span data-ttu-id="16a96-207">Der folgende Handler kontrolliert das [**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="16a96-207">This handler manages the [**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965) event.</span></span> <span data-ttu-id="16a96-208">Das Ereignis wird zum Ereignisprotokoll hinzugefügt, der Zeiger wird aus dem Zeigerarray entfernt, und die Zeigerdetails werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="16a96-208">We add the event to the event log, remove the pointer from the pointer array, and update the pointer details.</span></span>

    > [!NOTE]
    > <span data-ttu-id="16a96-209">[**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965) kann anstelle von [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) eintreten.</span><span class="sxs-lookup"><span data-stu-id="16a96-209">[**PointerCaptureLost**](https://msdn.microsoft.com/library/windows/apps/br208965) can occur instead of [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972).</span></span> <span data-ttu-id="16a96-210">Die Zeigererfassung kann aus verschiedenen Gründen verloren gehen, darunter eine Benutzerinteraktion, die programmgesteuerte Erfassung von einem anderen Zeiger, das Aufrufen von [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972).</span><span class="sxs-lookup"><span data-stu-id="16a96-210">Pointer capture can be lost for various reasons including user interaction, programmatic capture of another pointer, calling [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972).</span></span>     

```csharp
/// <summary>
/// The pointer capture lost event handler.
/// Fires for various reasons, including: 
///    - User interactions
///    - Programmatic capture of another pointer
///    - Captured pointer was deliberately released
// PointerCaptureLost can fire instead of PointerReleased. 
/// </summary>
/// <param name="sender">Source of the pointer event.</param>
/// <param name="e">Event args for the pointer routed event.</param>
private void Target_PointerCaptureLost(object sender, PointerRoutedEventArgs e)
{
    // Prevent most handlers along the event route from handling the same event again.
    e.Handled = true;

    PointerPoint ptrPt = e.GetCurrentPoint(Target);

    // Update event log.
    UpdateEventLog("Pointer capture lost: " + ptrPt.PointerId);

    if (pointers.Count == 0)
    {
        Target.Fill = new SolidColorBrush(Windows.UI.Colors.Black);
    }

    // Remove contact from dictionary.
    if (pointers.ContainsKey(ptrPt.PointerId))
    {
        pointers[ptrPt.PointerId] = null;
        pointers.Remove(ptrPt.PointerId);
    }

    DestroyInfoPop(ptrPt);
}
```

### <a name="get-pointer-properties"></a><span data-ttu-id="16a96-211">Abrufen von Zeigereigenschaften</span><span class="sxs-lookup"><span data-stu-id="16a96-211">Get pointer properties</span></span>

<span data-ttu-id="16a96-212">Wie bereits erwähnt, müssen Sie die erweiterten Zeigerinformationen von einem [**Windows.UI.Input.PointerPoint**](https://msdn.microsoft.com/library/windows/apps/br242038)-Objekt abrufen, das über die Methoden [**GetCurrentPoint**](https://msdn.microsoft.com/library/windows/apps/hh943077) und [**GetIntermediatePoints**](https://msdn.microsoft.com/library/windows/apps/hh943078) von [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076) bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="16a96-212">As stated earlier, you must get most extended pointer info from a [**Windows.UI.Input.PointerPoint**](https://msdn.microsoft.com/library/windows/apps/br242038) object obtained through the [**GetCurrentPoint**](https://msdn.microsoft.com/library/windows/apps/hh943077) and [**GetIntermediatePoints**](https://msdn.microsoft.com/library/windows/apps/hh943078) methods of [**PointerRoutedEventArgs**](https://msdn.microsoft.com/library/windows/apps/hh943076).</span></span> <span data-ttu-id="16a96-213">Die folgenden Codeausschnitte zeigen, wie.</span><span class="sxs-lookup"><span data-stu-id="16a96-213">The following code snippets show how.</span></span>

-   <span data-ttu-id="16a96-214">Zuerst wird ein neues [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Objekt für jeden Zeiger erstellt.</span><span class="sxs-lookup"><span data-stu-id="16a96-214">First, we create a new [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) for each pointer.</span></span>

```csharp
/// <summary>
/// Create the pointer info popup.
/// </summary>
/// <param name="ptrPt">Reference to the input pointer.</param>
void CreateInfoPop(PointerPoint ptrPt)
{
    TextBlock pointerDetails = new TextBlock();
    pointerDetails.Name = ptrPt.PointerId.ToString();
    pointerDetails.Foreground = new SolidColorBrush(Windows.UI.Colors.White);
    pointerDetails.Text = QueryPointer(ptrPt);

    TranslateTransform x = new TranslateTransform();
    x.X = ptrPt.Position.X + 20;
    x.Y = ptrPt.Position.Y + 20;
    pointerDetails.RenderTransform = x;

    Container.Children.Add(pointerDetails);
}
```

-   <span data-ttu-id="16a96-215">Anschließend wird Funktionalität bereitgestellt, um die Zeigerinformationen in einem vorhandenen [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Objekt zu aktualisieren, das diesem Zeiger zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="16a96-215">Then we provide a way to update the pointer info in an existing [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) associated with that pointer.</span></span>

```csharp
/// <summary>
/// Update the pointer info popup.
/// </summary>
/// <param name="ptrPt">Reference to the input pointer.</param>
void UpdateInfoPop(PointerPoint ptrPt)
{
    foreach (var pointerDetails in Container.Children)
    {
        if (pointerDetails.GetType().ToString() == "Windows.UI.Xaml.Controls.TextBlock")
        {
            TextBlock textBlock = (TextBlock)pointerDetails;
            if (textBlock.Name == ptrPt.PointerId.ToString())
            {
                // To get pointer location details, we need extended pointer info.
                // We get the pointer info through the getCurrentPoint method
                // of the event argument. 
                TranslateTransform x = new TranslateTransform();
                x.X = ptrPt.Position.X + 20;
                x.Y = ptrPt.Position.Y + 20;
                pointerDetails.RenderTransform = x;
                textBlock.Text = QueryPointer(ptrPt);
            }
        }
    }
}
```

-   <span data-ttu-id="16a96-216">Abschließend werden verschiedene Zeigereigenschaften abgefragt.</span><span class="sxs-lookup"><span data-stu-id="16a96-216">Finally, we query various pointer properties.</span></span>

```csharp
/// <summary>
/// Get pointer details.
/// </summary>
/// <param name="ptrPt">Reference to the input pointer.</param>
/// <returns>A string composed of pointer details.</returns>
String QueryPointer(PointerPoint ptrPt)
{
    String details = "";

    switch (ptrPt.PointerDevice.PointerDeviceType)
    {
        case Windows.Devices.Input.PointerDeviceType.Mouse:
            details += "\nPointer type: mouse";
            break;
        case Windows.Devices.Input.PointerDeviceType.Pen:
            details += "\nPointer type: pen";
            if (ptrPt.IsInContact)
            {
                details += "\nPressure: " + ptrPt.Properties.Pressure;
                details += "\nrotation: " + ptrPt.Properties.Orientation;
                details += "\nTilt X: " + ptrPt.Properties.XTilt;
                details += "\nTilt Y: " + ptrPt.Properties.YTilt;
                details += "\nBarrel button pressed: " + ptrPt.Properties.IsBarrelButtonPressed;
            }
            break;
        case Windows.Devices.Input.PointerDeviceType.Touch:
            details += "\nPointer type: touch";
            details += "\nrotation: " + ptrPt.Properties.Orientation;
            details += "\nTilt X: " + ptrPt.Properties.XTilt;
            details += "\nTilt Y: " + ptrPt.Properties.YTilt;
            break;
        default:
            details += "\nPointer type: n/a";
            break;
    }

    GeneralTransform gt = Target.TransformToVisual(this);
    Point screenPoint;

    screenPoint = gt.TransformPoint(new Point(ptrPt.Position.X, ptrPt.Position.Y));
    details += "\nPointer Id: " + ptrPt.PointerId.ToString() +
        "\nPointer location (target): " + Math.Round(ptrPt.Position.X) + ", " + Math.Round(ptrPt.Position.Y) +
        "\nPointer location (container): " + Math.Round(screenPoint.X) + ", " + Math.Round(screenPoint.Y);

    return details;
}
```

## <a name="primary-pointer"></a><span data-ttu-id="16a96-217">Primärer Zeiger</span><span class="sxs-lookup"><span data-stu-id="16a96-217">Primary pointer</span></span>
<span data-ttu-id="16a96-218">Einige Geräte wie ein Touch-Digitizer oder Touchpad unterstützen mehr als der typische einzelne Zeiger einer Maus oder ein Stift (in den meisten Fällen, da der Surface Hub zwei Stifteingaben unterstützt).</span><span class="sxs-lookup"><span data-stu-id="16a96-218">Some input devices, such as a touch digitizer or touchpad, support more than the typical single pointer of a mouse or a pen (in most cases as the Surface Hub supports two pen inputs).</span></span> 

<span data-ttu-id="16a96-219">Verwenden Sie die schreibgeschützte Eigenschaft **[IsPrimary](https://docs.microsoft.com/uwp/api/windows.ui.input.pointerpointproperties.IsPrimary)** der **[PointerPointerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.pointerpointproperties)**-Klasse, um einen einzelnen primären Zeiger zu identifizieren und zu unterscheiden (der primäre Zeiger ist immer der erste Zeiger, der während einer Eingabesequenz erkannt wird).</span><span class="sxs-lookup"><span data-stu-id="16a96-219">Use the read-only **[IsPrimary](https://docs.microsoft.com/uwp/api/windows.ui.input.pointerpointproperties.IsPrimary)** property of the **[PointerPointerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.pointerpointproperties)** class to identify and differentiate a single primary pointer (the primary pointer is always the first pointer detected during an input sequence).</span></span> 

<span data-ttu-id="16a96-220">Durch die Identifizierung des primären Zeigers können Sie diesen verwenden, um Maus- oder Stifteingaben zu emulieren, Interaktionen anzupassen oder eine andere spezifische Funktion oder Benutzeroberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="16a96-220">By identifying the primary pointer, you can use it to emulate mouse or pen input, customize interactions, or provide some other specific functionality or UI.</span></span>

> [!NOTE]
> <span data-ttu-id="16a96-221">Wenn der primäre Zeiger während einer Eingabesequenz freigegeben oder abgebrochen wird bzw. verloren gegangen ist, wird erst ein primärer Eingabezeiger erstellt, wenn eine neue Eingabesequenz initiiert wird (eine Eingabesequenz endet, wenn alle Zeiger freigegeben oder abgebrochen wurden bzw. verloren gegangen sind).</span><span class="sxs-lookup"><span data-stu-id="16a96-221">If the primary pointer is released, canceled, or lost during an input sequence, a primary input pointer is not created until a new input sequence is initiated (an input sequence ends when all pointers have been released, canceled, or lost).</span></span>

## <a name="primary-pointer-animation-example"></a><span data-ttu-id="16a96-222">Beispiel für die Animation eines primären Zeigers</span><span class="sxs-lookup"><span data-stu-id="16a96-222">Primary pointer animation example</span></span>

<span data-ttu-id="16a96-223">Die folgenden Codeausschnitte zeigen, wie Sie spezielles visuelles Feedback bereitstellen können, damit ein Benutzer zwischen den Zeigereingaben in Ihrer Anwendung unterscheiden kann.</span><span class="sxs-lookup"><span data-stu-id="16a96-223">These code snippets show how you can provide special visual feedback to help a user differentiate between pointer inputs in your application.</span></span>

<span data-ttu-id="16a96-224">Diese bestimmte App verwendet Farbe und Animation, um den primären Zeiger hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="16a96-224">This particular app uses both color and animation to highlight the primary pointer.</span></span>

![Zeigeranwendung mit animiertem visuellem Feedback](images/pointers/pointers-usercontrol-animation.gif)

**<span data-ttu-id="16a96-226">Laden Sie dieses Beispiel aus [Beispiel für die Zeigereingabe (UserControl mit Animation)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers-animation.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="16a96-226">Download this sample from [Pointer input sample (UserControl with animation)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers-animation.zip)</span></span>**

### <a name="visual-feedback"></a><span data-ttu-id="16a96-227">Visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="16a96-227">Visual feedback</span></span>

<span data-ttu-id="16a96-228">Wir definieren eine **[UserControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol)** basierend auf einem XAML-**[Ellipse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.shapes.ellipse)**-Objekt, die hervorhebt, an welcher Stelle sich jeder Zeiger im Zeichenbereich befindet, und ein **[Storyboard](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.animation.storyboard)** verwendet, um die Ellipse zu animieren, die dem primären Zeiger entspricht.</span><span class="sxs-lookup"><span data-stu-id="16a96-228">We define a **[UserControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.usercontrol)**, based on a XAML **[Ellipse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.shapes.ellipse)** object, that highlights where each pointer is on the canvas and uses a **[Storyboard](https://docs.microsoft.com/en-us/uwp/api/windows.ui.xaml.media.animation.storyboard)** to animate the ellipse that corresponds to the primary pointer.</span></span>

**<span data-ttu-id="16a96-229">Im Folgenden sehen Sie die XAML:</span><span class="sxs-lookup"><span data-stu-id="16a96-229">Here's the XAML:</span></span>**

```xaml
<UserControl
    x:Class="UWP_Pointers.PointerEllipse"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:UWP_Pointers"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    d:DesignHeight="100"
    d:DesignWidth="100">

    <UserControl.Resources>
        <Style x:Key="EllipseStyle" TargetType="Ellipse">
            <Setter Property="Transitions">
                <Setter.Value>
                    <TransitionCollection>
                        <ContentThemeTransition/>
                    </TransitionCollection>
                </Setter.Value>
            </Setter>
        </Style>
        
        <Storyboard x:Name="myStoryboard">
            <!-- Animates the value of a Double property between 
            two target values using linear interpolation over the 
            specified Duration. -->
            <DoubleAnimation
              Storyboard.TargetName="ellipse"
              Storyboard.TargetProperty="(RenderTransform).(ScaleTransform.ScaleY)"  
              Duration="0:0:1" 
              AutoReverse="True" 
              RepeatBehavior="Forever" From="1.0" To="1.4">
            </DoubleAnimation>

            <!-- Animates the value of a Double property between 
            two target values using linear interpolation over the 
            specified Duration. -->
            <DoubleAnimation
              Storyboard.TargetName="ellipse"
              Storyboard.TargetProperty="(RenderTransform).(ScaleTransform.ScaleX)"  
              Duration="0:0:1" 
              AutoReverse="True" 
              RepeatBehavior="Forever" From="1.0" To="1.4">
            </DoubleAnimation>

            <!-- Animates the value of a Color property between 
            two target values using linear interpolation over the 
            specified Duration. -->
            <ColorAnimation 
                Storyboard.TargetName="ellipse" 
                EnableDependentAnimation="True" 
                Storyboard.TargetProperty="(Fill).(SolidColorBrush.Color)" 
                From="White" To="Red"  Duration="0:0:1" 
                AutoReverse="True" RepeatBehavior="Forever"/>
        </Storyboard>
    </UserControl.Resources>

    <Grid x:Name="CompositionContainer">
        <Ellipse Name="ellipse" 
        StrokeThickness="2" 
        Width="{x:Bind Diameter}" 
        Height="{x:Bind Diameter}"  
        Style="{StaticResource EllipseStyle}" />
    </Grid>
</UserControl>
```

<span data-ttu-id="16a96-230">Und hier die CodeBehind-Datei:</span><span class="sxs-lookup"><span data-stu-id="16a96-230">And here's the code-behind:</span></span>
```csharp
using Windows.Foundation;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Media;

// The User Control item template is documented at 
// https://go.microsoft.com/fwlink/?LinkId=234236

namespace UWP_Pointers
{
    /// <summary>
    /// Pointer feedback object.
    /// </summary>
    public sealed partial class PointerEllipse : UserControl
    {
        // Reference to the application canvas.
        Canvas canvas;

        /// <summary>
        /// Ellipse UI for pointer feedback.
        /// </summary>
        /// <param name="c">The drawing canvas.</param>
        public PointerEllipse(Canvas c)
        {
            this.InitializeComponent();
            canvas = c;
        }

        /// <summary>
        /// Gets or sets the pointer Id to associate with the PointerEllipse object.
        /// </summary>
        public uint PointerId
        {
            get { return (uint)GetValue(PointerIdProperty); }
            set { SetValue(PointerIdProperty, value); }
        }
        // Using a DependencyProperty as the backing store for PointerId.  
        // This enables animation, styling, binding, etc...
        public static readonly DependencyProperty PointerIdProperty =
            DependencyProperty.Register("PointerId", typeof(uint), 
                typeof(PointerEllipse), new PropertyMetadata(null));


        /// <summary>
        /// Gets or sets whether the associated pointer is Primary.
        /// </summary>
        public bool PrimaryPointer
        {
            get { return (bool)GetValue(PrimaryPointerProperty); }
            set
            {
                SetValue(PrimaryPointerProperty, value);
            }
        }
        // Using a DependencyProperty as the backing store for PrimaryPointer.  
        // This enables animation, styling, binding, etc...
        public static readonly DependencyProperty PrimaryPointerProperty =
            DependencyProperty.Register("PrimaryPointer", typeof(bool), 
                typeof(PointerEllipse), new PropertyMetadata(false));


        /// <summary>
        /// Gets or sets the ellipse style based on whether the pointer is Primary.
        /// </summary>
        public bool PrimaryEllipse 
        {
            get { return (bool)GetValue(PrimaryEllipseProperty); }
            set
            {
                SetValue(PrimaryEllipseProperty, value);
                if (value)
                {
                    SolidColorBrush fillBrush = 
                        (SolidColorBrush)Application.Current.Resources["PrimaryFillBrush"];
                    SolidColorBrush strokeBrush = 
                        (SolidColorBrush)Application.Current.Resources["PrimaryStrokeBrush"];

                    ellipse.Fill = fillBrush;
                    ellipse.Stroke = strokeBrush;
                    ellipse.RenderTransform = new CompositeTransform();
                    ellipse.RenderTransformOrigin = new Point(.5, .5);
                    myStoryboard.Begin();
                }
                else
                {
                    SolidColorBrush fillBrush = 
                        (SolidColorBrush)Application.Current.Resources["SecondaryFillBrush"];
                    SolidColorBrush strokeBrush = 
                        (SolidColorBrush)Application.Current.Resources["SecondaryStrokeBrush"];
                    ellipse.Fill = fillBrush;
                    ellipse.Stroke = strokeBrush;
                }
            }
        }
        // Using a DependencyProperty as the backing store for PrimaryEllipse.  
        // This enables animation, styling, binding, etc...
        public static readonly DependencyProperty PrimaryEllipseProperty =
            DependencyProperty.Register("PrimaryEllipse", 
                typeof(bool), typeof(PointerEllipse), new PropertyMetadata(false));


        /// <summary>
        /// Gets or sets the diameter of the PointerEllipse object.
        /// </summary>
        public int Diameter
        {
            get { return (int)GetValue(DiameterProperty); }
            set { SetValue(DiameterProperty, value); }
        }
        // Using a DependencyProperty as the backing store for Diameter.  This enables animation, styling, binding, etc...
        public static readonly DependencyProperty DiameterProperty =
            DependencyProperty.Register("Diameter", typeof(int), 
                typeof(PointerEllipse), new PropertyMetadata(120));
    }
}
```

### <a name="create-the-ui"></a><span data-ttu-id="16a96-231">Erstellen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="16a96-231">Create the UI</span></span>
<span data-ttu-id="16a96-232">Die Benutzeroberfläche in diesem Beispiel ist auf den **[Eingabezeichenbereich](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.canvas)** beschränkt, in dem wir alle Zeiger nachverfolgen und die Zeigerindikatoren sowie die primäre Zeigeranimation (falls zutreffend) zusammen mit einer Kopfzeilenleiste wiedergeben, die einen Zeigerzähler und einen primären Zeigerbezeichner enthält.</span><span class="sxs-lookup"><span data-stu-id="16a96-232">The UI in this example is limited to the input **[Canvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.canvas)** where we track any pointers and render the pointer indicators and primary pointer animation (if applicable), along with a header bar containing a pointer counter and a primary pointer identifier.</span></span>

<span data-ttu-id="16a96-233">Hier ist die MainPage.xaml-Datei:</span><span class="sxs-lookup"><span data-stu-id="16a96-233">Here's the MainPage.xaml:</span></span>

```xaml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <StackPanel x:Name="HeaderPanel" 
                Orientation="Horizontal" 
                Grid.Row="0">
        <StackPanel.Transitions>
            <TransitionCollection>
                <AddDeleteThemeTransition/>
            </TransitionCollection>
        </StackPanel.Transitions>
        <TextBlock x:Name="Header" 
                    Text="Basic pointer tracking sample - IsPrimary" 
                    Style="{ThemeResource HeaderTextBlockStyle}" 
                    Margin="10,0,0,0" />
        <TextBlock x:Name="PointerCounterLabel"
                    VerticalAlignment="Center"                 
                    Style="{ThemeResource BodyTextBlockStyle}"
                    Text="Number of pointers: " 
                    Margin="50,0,0,0"/>
        <TextBlock x:Name="PointerCounter"
                    VerticalAlignment="Center"                 
                    Style="{ThemeResource BodyTextBlockStyle}"
                    Text="0" 
                    Margin="10,0,0,0"/>
        <TextBlock x:Name="PointerPrimaryLabel"
                    VerticalAlignment="Center"                 
                    Style="{ThemeResource BodyTextBlockStyle}"
                    Text="Primary: " 
                    Margin="50,0,0,0"/>
        <TextBlock x:Name="PointerPrimary"
                    VerticalAlignment="Center"                 
                    Style="{ThemeResource BodyTextBlockStyle}"
                    Text="n/a" 
                    Margin="10,0,0,0"/>
    </StackPanel>
    
    <Grid Grid.Row="1">
        <!--The canvas where we render the pointer UI.-->
        <Canvas x:Name="pointerCanvas"/>
    </Grid>
</Grid>
```

### <a name="handle-pointer-events"></a><span data-ttu-id="16a96-234">Behandeln von Zeigerereignissen</span><span class="sxs-lookup"><span data-stu-id="16a96-234">Handle pointer events</span></span>

<span data-ttu-id="16a96-235">Schließlich definieren wir unsere einfachen Zeigerereignishandler in der CodeBehind-Datei MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="16a96-235">Finally, we define our basic pointer event handlers in the MainPage.xaml.cs code-behind.</span></span> <span data-ttu-id="16a96-236">Wir werden den Code hier nicht reproduzieren, da die Grundlagen im vorherigen Beispiel behandelt wurden, aber Sie können das Arbeitsbeispiel unter [Beispiel für Zeigereingabe (UserControl mit Animation)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers-animation.zip) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="16a96-236">We won't reproduce the code here as the basics were covered in the previous example, but you can download the working sample from [Pointer input sample (UserControl with animation)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers-animation.zip).</span></span>

## <a name="related-articles"></a><span data-ttu-id="16a96-237">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="16a96-237">Related articles</span></span>

**<span data-ttu-id="16a96-238">Themenbeispiele</span><span class="sxs-lookup"><span data-stu-id="16a96-238">Topic samples</span></span>**
* [<span data-ttu-id="16a96-239">Beispiel für Zeigereingabe (einfach)</span><span class="sxs-lookup"><span data-stu-id="16a96-239">Pointer input sample (basic)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers.zip)
* [<span data-ttu-id="16a96-240">Beispiel für Zeigereingabe (UserControl mit Animation)</span><span class="sxs-lookup"><span data-stu-id="16a96-240">Pointer input sample (UserControl with animation)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-pointers-animation.zip)

**<span data-ttu-id="16a96-241">Andere Beispiele</span><span class="sxs-lookup"><span data-stu-id="16a96-241">Other samples</span></span>**
* [<span data-ttu-id="16a96-242">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="16a96-242">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="16a96-243">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="16a96-243">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="16a96-244">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="16a96-244">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="16a96-245">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="16a96-245">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="16a96-246">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="16a96-246">Archive samples</span></span>**
* [<span data-ttu-id="16a96-247">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="16a96-247">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="16a96-248">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="16a96-248">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="16a96-249">Eingabe: Beispiel für Bearbeitungen und Bewegungen (C++)</span><span class="sxs-lookup"><span data-stu-id="16a96-249">Input: Manipulations and gestures (C++) sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231605)
* [<span data-ttu-id="16a96-250">Eingabe: Beispiel für Fingereingabe-Treffertests</span><span class="sxs-lookup"><span data-stu-id="16a96-250">Input: Touch hit testing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231590)
* [<span data-ttu-id="16a96-251">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="16a96-251">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="16a96-252">Eingabe: vereinfachtes Freihandbeispiel</span><span class="sxs-lookup"><span data-stu-id="16a96-252">Input: Simplified ink sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=246570)