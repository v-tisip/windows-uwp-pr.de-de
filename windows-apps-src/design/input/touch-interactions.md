---
author: Karl-Bridge-Microsoft
Description: Create Universal Windows Platform (UWP) apps with intuitive and distinctive user interaction experiences that are optimized for touch but are functionally consistent across input devices.
title: Interaktionen per Toucheingabe
ms.assetid: DA6EBC88-EB18-4418-A98A-457EA1DEA88A
label: Touch interactions
template: detail.hbs
keywords: Touch, Zeiger, Eingabe, Benutzerinteraktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 1ef67c179e691d14f3636a663a24ebbb862c35f7
ms.sourcegitcommit: 2470c6596d67e1f5ca26b44fad56a2f89773e9cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
ms.locfileid: "1675187"
---
# <a name="touch-interactions"></a><span data-ttu-id="e0c86-103">Toucheingabe-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-103">Touch interactions</span></span>


<span data-ttu-id="e0c86-104">Gehen Sie beim Entwerfen Ihrer App davon aus, dass die Benutzer in erster Linie die Toucheingabe als Eingabemethode verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-104">Design your app with the expectation that touch will be the primary input method of your users.</span></span> <span data-ttu-id="e0c86-105">Wenn Sie UWP-Steuerelemente verwenden, ist keine zusätzliche Programmierung für die Unterstützung von Touchpad, Maus und Zeichen-/Eingabestift erforderlich, da sie in UWP-Apps standardmäßig bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-105">If you use UWP controls, support for touchpad, mouse, and pen/stylus requires no additional programming, because UWP apps provide this for free.</span></span>

<span data-ttu-id="e0c86-106">Bedenken Sie dabei jedoch, dass eine für Toucheingaben optimierte Benutzeroberfläche einer herkömmlichen Benutzeroberfläche nicht in jedem Fall überlegen ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-106">However, keep in mind that a UI optimized for touch is not always superior to a traditional UI.</span></span> <span data-ttu-id="e0c86-107">Beide haben Vor- und Nachteile, die je nach Technologie oder Anwendung unterschiedlich sein können.</span><span class="sxs-lookup"><span data-stu-id="e0c86-107">Both provide advantages and disadvantages that are unique to a technology and application.</span></span> <span data-ttu-id="e0c86-108">Sie müssen beim Übergang zu einer vorrangig auf Toucheingabe ausgelegten UI die wichtigsten Unterschiede zwischen Toucheingabe (einschließlich des Touchpads) und Eingabe über Maus, Zeichen- oder Eingabestift und Tastatur verstehen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-108">In the move to a touch-first UI, it is important to understand the core differences between touch (including touchpad), pen/stylus, mouse, and keyboard input.</span></span>

> <span data-ttu-id="e0c86-109">**Wichtige APIs**: [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)</span><span class="sxs-lookup"><span data-stu-id="e0c86-109">**Important APIs**: [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br227994), [**Windows.UI.Core**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)</span></span>


<span data-ttu-id="e0c86-110">Viele Geräte verfügen über Multitouch-Bildschirme, die eine Eingabe mit einem oder mehreren Fingern (oder Berührungskontakten) unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-110">Many devices have multi-touch screens that support using one or more fingers (or touch contacts) as input.</span></span> <span data-ttu-id="e0c86-111">Die Berührungskontakte und ihre Bewegung werden als Touchbewegungen und Manipulationen interpretiert, um verschiedene Benutzerinteraktionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-111">The touch contacts, and their movement, are interpreted as touch gestures and manipulations to support various user interactions.</span></span>

<span data-ttu-id="e0c86-112">Die universelle Windows-Plattform (UWP) bietet eine Reihe unterschiedlicher Mechanismen zur Behandlung von Toucheingaben, mit deren Hilfe Sie eine immersive, benutzerfreundliche Umgebung schaffen können.</span><span class="sxs-lookup"><span data-stu-id="e0c86-112">The Universal Windows Platform (UWP) includes a number of different mechanisms for handling touch input, enabling you to create an immersive experience that your users can explore with confidence.</span></span> <span data-ttu-id="e0c86-113">Im Folgenden behandeln wir die Grundlagen der Toucheingabe in einer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="e0c86-113">Here, we cover the basics of using touch input in a UWP app.</span></span>

<span data-ttu-id="e0c86-114">Interaktionen per Toucheingabe erfordern drei Dinge:</span><span class="sxs-lookup"><span data-stu-id="e0c86-114">Touch interactions require three things:</span></span>

-   <span data-ttu-id="e0c86-115">Einen berührungsempfindlichen Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e0c86-115">A touch-sensitive display.</span></span>
-   <span data-ttu-id="e0c86-116">Direkter Kontakt von einem oder mehreren Fingern auf dem Bildschirm (oder in der Nähe des Bildschirms, wenn er über Näherungssensoren verfügt und die Erkennung des Daraufzeigens unterstützt).</span><span class="sxs-lookup"><span data-stu-id="e0c86-116">The direct contact (or proximity to, if the display has proximity sensors and supports hover detection) of one or more fingers on that display.</span></span>
-   <span data-ttu-id="e0c86-117">Bewegung der Berührungskontakte (oder das Fehlen der Bewegung basierend auf einem Zeitschwellenwert).</span><span class="sxs-lookup"><span data-stu-id="e0c86-117">Movement of the touch contacts (or lack thereof, based on a time threshold).</span></span>

<span data-ttu-id="e0c86-118">Mögliche vom Berührungssensor bereitgestellte Eingabedaten:</span><span class="sxs-lookup"><span data-stu-id="e0c86-118">The input data provided by the touch sensor can be:</span></span>

-   <span data-ttu-id="e0c86-119">Interpretation als physische Geste für die direkte Manipulation von einem oder mehreren UI-Elementen (z.B. Schwenken, Drehen, Vergrößern/Verkleinern oder Verschieben).</span><span class="sxs-lookup"><span data-stu-id="e0c86-119">Interpreted as a physical gesture for direct manipulation of one or more UI elements (such as panning, rotating, resizing, or moving).</span></span> <span data-ttu-id="e0c86-120">Die Interaktion mit einem Element über das zugehörige Eigenschaftenfenster, Dialogfeld oder ein anderes UI-Angebot gilt dagegen als indirekte Manipulation.</span><span class="sxs-lookup"><span data-stu-id="e0c86-120">In contrast, interacting with an element through its properties window, dialog box, or other UI affordance is considered indirect manipulation.</span></span>
-   <span data-ttu-id="e0c86-121">Erkennung als alternative Eingabemethode, z.B. Maus oder Stift.</span><span class="sxs-lookup"><span data-stu-id="e0c86-121">Recognized as an alternative input method, such as mouse or pen.</span></span>
-   <span data-ttu-id="e0c86-122">Wird zum Ergänzen oder Ändern von Aspekten anderer Eingabemethoden verwendet, z.B. zum Verwischen eines mit einem Stift gezeichneten Freihandstrichs.</span><span class="sxs-lookup"><span data-stu-id="e0c86-122">Used to complement or modify aspects of other input methods, such as smudging an ink stroke drawn with a pen.</span></span>

<span data-ttu-id="e0c86-123">In der Regel beinhaltet die Toucheingabe die direkte Manipulation eines Elements auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e0c86-123">Touch input typically involves the direct manipulation of an element on the screen.</span></span> <span data-ttu-id="e0c86-124">Das Element reagiert sofort auf alle Berührungen in seinem Treffertestbereich und reagiert entsprechend auf alle nachfolgenden Bewegungen des Touchkontakts, einschließlich dessen Entfernung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-124">The element responds immediately to any touch contact within its hit test area, and reacts appropriately to any subsequent movement of the touch contacts, including removal.</span></span>

<span data-ttu-id="e0c86-125">Benutzerdefinierte Touchgesten und Interaktionen sollten sorgfältig entworfen werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-125">Custom touch gestures and interactions should be designed carefully.</span></span> <span data-ttu-id="e0c86-126">Sie sollten intuitiv, reaktionsfähig und leicht auffindbar sein und eine optimale Benutzererfahrung mit Ihrer App sicherstellen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-126">They should be intuitive, responsive, and discoverable, and they should let users explore your app with confidence.</span></span>

<span data-ttu-id="e0c86-127">Stellen Sie sicher, dass die App-Funktionen konsistent auf allen unterstützten Eingabegerätetypen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e0c86-127">Ensure that app functionality is exposed consistently across every supported input device type.</span></span> <span data-ttu-id="e0c86-128">Verwenden Sie bei Bedarf eine Form von indirektem Eingabemodus, z.B. die Texteingabe für Tastaturinteraktionen oder UI-Angebote für Maus und Stift.</span><span class="sxs-lookup"><span data-stu-id="e0c86-128">If necessary, use some form of indirect input mode, such as text input for keyboard interactions, or UI affordances for mouse and pen.</span></span>

<span data-ttu-id="e0c86-129">Bedenken Sie, dass herkömmliche Eingabegeräte (wie Maus und Tastatur) für viele Benutzer vertraut sind und gerne verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-129">Remember that traditional input devices (such as mouse and keyboard), are familiar and appealing to many users.</span></span> <span data-ttu-id="e0c86-130">Sie bieten häufig Faktoren wie Geschwindigkeit, Genauigkeit und klares Feedback, die bei der Toucheingabe unter Umständen nicht gegeben sind.</span><span class="sxs-lookup"><span data-stu-id="e0c86-130">They can offer speed, accuracy, and tactile feedback that touch might not.</span></span>

<span data-ttu-id="e0c86-131">Mit den einzigartigen und speziellen Interaktionserfahrungen für alle Eingabegeräte unterstützen Sie eine breite Palette an Funktionen und Einstellungen und wenden sich an eine möglichst breite Zielgruppe. Auf diese Weise gewinnen Sie mehr Kunden für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="e0c86-131">Providing unique and distinctive interaction experiences for all input devices will support the widest range of capabilities and preferences, appeal to the broadest possible audience, and attract more customers to your app.</span></span>

## <a name="compare-touch-interaction-requirements"></a><span data-ttu-id="e0c86-132">Vergleich der Anforderungen für Toucheingabe-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-132">Compare touch interaction requirements</span></span>

<span data-ttu-id="e0c86-133">In der folgenden Tabelle sind einige der Unterschiede zwischen den Eingabegeräten aufgeführt, die Sie berücksichtigen sollten, wenn Sie für die Toucheingabe optimierte UWP-Apps entwerfen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-133">The following table shows some of the differences between input devices that you should consider when you design touch-optimized UWP apps.</span></span>

<table>
<tbody><tr><th><span data-ttu-id="e0c86-134">Merkmal</span><span class="sxs-lookup"><span data-stu-id="e0c86-134">Factor</span></span></th><th><span data-ttu-id="e0c86-135">Toucheingabe-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-135">Touch interactions</span></span></th><th><span data-ttu-id="e0c86-136">Interaktionen über Maus, Tastatur oder Zeichen- bzw. Eingabestift</span><span class="sxs-lookup"><span data-stu-id="e0c86-136">Mouse, keyboard, pen/stylus interactions</span></span></th><th><span data-ttu-id="e0c86-137">Touchpad</span><span class="sxs-lookup"><span data-stu-id="e0c86-137">Touchpad</span></span></th></tr>
<tr><td rowspan="3"><span data-ttu-id="e0c86-138">Präzision</span><span class="sxs-lookup"><span data-stu-id="e0c86-138">Precision</span></span></td><td><span data-ttu-id="e0c86-139">Der Kontaktbereich einer Fingerspitze ist größer als eine einzige xy-Koordinate. Dadurch erhöht sich die Wahrscheinlichkeit, dass Befehle unbeabsichtigt aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-139">The contact area of a fingertip is greater than a single x-y coordinate, which increases the chances of unintended command activations.</span></span></td><td><span data-ttu-id="e0c86-140">Maus und Zeichen- oder Eingabestift liefern eine präzise xy-Koordinate.</span><span class="sxs-lookup"><span data-stu-id="e0c86-140">The mouse and pen/stylus supply a precise x-y coordinate.</span></span></td><td><span data-ttu-id="e0c86-141">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-141">Same as mouse.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-142">Die Form des Kontaktbereichs ändert sich während der Bewegung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-142">The shape  of the contact area changes throughout the movement.</span></span>  </td><td><span data-ttu-id="e0c86-143">Mausbewegungen und Striche mit Zeichen- oder Eingabestift liefern eine präzise xy-Koordinate.</span><span class="sxs-lookup"><span data-stu-id="e0c86-143">Mouse movements and pen/stylus strokes supply precise x-y coordinates.</span></span> <span data-ttu-id="e0c86-144">Die Tastatur hat einen expliziten Fokus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-144">Keyboard focus is explicit.</span></span></td><td><span data-ttu-id="e0c86-145">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-145">Same as mouse.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-146">Es gibt keinen Mauscursor, der die Zielbestimmung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-146">There is no mouse cursor to assist with targeting.</span></span></td><td><span data-ttu-id="e0c86-147">Der Fokus von Mauscursor, Zeichen- oder Eingabestiftcursor und Tastatur unterstützt die Zielbestimmung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-147">The mouse cursor, pen/stylus cursor, and keyboard focus all assist with targeting.</span></span></td><td><span data-ttu-id="e0c86-148">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-148">Same as mouse.</span></span></td></tr>
<tr><td rowspan="3"><span data-ttu-id="e0c86-149">Menschliche Anatomie</span><span class="sxs-lookup"><span data-stu-id="e0c86-149">Human anatomy</span></span></td><td><span data-ttu-id="e0c86-150">Bewegungen mit den Fingerspitzen sind ungenau, da es schwierig ist, mit den Fingern eine lineare Bewegung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-150">Fingertip movements are imprecise, because a straight-line motion with one or more fingers is difficult.</span></span> <span data-ttu-id="e0c86-151">Dies liegt an der Krümmung der Handgelenke und der Anzahl der an der Bewegung beteiligten Gelenke.</span><span class="sxs-lookup"><span data-stu-id="e0c86-151">This is due to the curvature of hand joints and the number of joints involved in the motion.</span></span></td><td><span data-ttu-id="e0c86-152">Es ist leichter, mit der Maus oder mit einem Zeichen- oder Eingabestift eine Bewegung in gerader Linie auszuführen, da die Hand, die diese Geräte steuert, eine kürzere physische Strecke zurücklegen muss als der Cursor auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e0c86-152">It's easier to perform a straight-line motion with the mouse or pen/stylus because the hand that controls them travels a shorter physical distance than the cursor on the screen.</span></span></td><td><span data-ttu-id="e0c86-153">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-153">Same as mouse.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-154">Manche Bereiche der für die Fingereingabe vorgesehenen Oberfläche eines Anzeigegeräts sind aufgrund der Fingerhaltung und der Tatsache, dass der Benutzer das Gerät halten muss, möglicherweise schwer zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-154">Some areas on the touch surface of a display device can be difficult to reach due to finger posture and the user's grip on the device.</span></span></td><td><span data-ttu-id="e0c86-155">Maus und Zeichen- oder Eingabestift können alle Bereiche des Bildschirms erreichen, während über die Aktivierreihenfolge der Zugriff auf alle Steuerelemente möglich sein sollte.</span><span class="sxs-lookup"><span data-stu-id="e0c86-155">The mouse and pen/stylus can reach any part of the screen while any control should be accessible by the keyboard through tab order.</span></span> </td><td><span data-ttu-id="e0c86-156">Haltung und Druck der Finger spielen dabei eventuell auch eine Rolle.</span><span class="sxs-lookup"><span data-stu-id="e0c86-156">Finger posture and grip can be an issue.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-157">Objekte werden möglicherweise durch mindestens eine Fingerspitze oder die Hand des Benutzers verdeckt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-157">Objects might be obscured by one or more fingertips or the user's hand.</span></span> <span data-ttu-id="e0c86-158">Dies wird als Okklusion bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e0c86-158">This is known as occlusion.</span></span></td><td><span data-ttu-id="e0c86-159">Indirekte Eingabegeräte verursachen keine Okklusion.</span><span class="sxs-lookup"><span data-stu-id="e0c86-159">Indirect input devices do not cause  occlusion.</span></span></td><td><span data-ttu-id="e0c86-160">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-160">Same as mouse.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-161">Objektzustand</span><span class="sxs-lookup"><span data-stu-id="e0c86-161">Object state</span></span></td><td><span data-ttu-id="e0c86-162">Bei der Fingereingabe wird ein Modell mit zwei Zuständen verwendet: Die für die Fingereingabe vorgesehene Oberfläche eines Anzeigegeräts wird entweder berührt (ein) oder nicht berührt (aus).</span><span class="sxs-lookup"><span data-stu-id="e0c86-162">Touch uses a two-state model: the touch surface of a display device  is either touched (on) or not (off).</span></span> <span data-ttu-id="e0c86-163">Es gibt keinen Zeigezustand, der zusätzliches visuelles Feedback auslösen kann.</span><span class="sxs-lookup"><span data-stu-id="e0c86-163">There is no hover state that can trigger additional visual feedback.</span></span></td><td>
<p><span data-ttu-id="e0c86-164">Maus, Zeichen- oder Eingabestift und Tastatur machen ein Modell mit drei Zuständen verfügbar: oben (aus), unten (ein) und Zeigen (Fokus).</span><span class="sxs-lookup"><span data-stu-id="e0c86-164">A mouse, pen/stylus, and keyboard all expose a three-state model: up (off), down (on), and hover (focus).</span></span></p>
<p><span data-ttu-id="e0c86-165">Mit Zeigen können Benutzer QuickInfos zu UI-Elementen erforschen und kennenlernen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-165">Hover lets users explore and learn through tooltips  associated with UI elements.</span></span> <span data-ttu-id="e0c86-166">Zeigen und Fokus können vermitteln, welche Objekte interaktiv sind, und außerdem die Zielbestimmung erleichtern.</span><span class="sxs-lookup"><span data-stu-id="e0c86-166">Hover and focus effects  can relay which objects are interactive and also help with targeting.</span></span> 
</p>
</td><td><span data-ttu-id="e0c86-167">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-167">Same as mouse.</span></span></td></tr>
<tr><td rowspan="2"><span data-ttu-id="e0c86-168">Umfangreiche Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-168">Rich interaction</span></span></td><td><span data-ttu-id="e0c86-169">Unterstützt die Mehrfingereingabe: mehrere Eingabepunkte (Fingerspitzen) auf einer für die Fingereingabe vorgesehenen Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="e0c86-169">Supports multi-touch: multiple input points (fingertips) on a touch surface.</span></span></td><td><span data-ttu-id="e0c86-170">Unterstützt einen einzigen Eingabepunkt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-170">Supports a single input point.</span></span></td><td><span data-ttu-id="e0c86-171">Identisch mit der Fingereingabe.</span><span class="sxs-lookup"><span data-stu-id="e0c86-171">Same as touch.</span></span></td></tr>
<tr><td><span data-ttu-id="e0c86-172">Unterstützt die direkte Manipulation von Objekten durch Bewegungen wie beispielsweise Tippen, Ziehen, Zusammendrücken und Drehen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-172">Supports direct manipulation of objects through gestures such as tapping, dragging, sliding, pinching, and rotating.</span></span></td><td><span data-ttu-id="e0c86-173">Keine Unterstützung für die direkte Manipulation, da Maus, Zeichen- oder Eingabestift und Tastatur indirekte Eingabegeräte sind.</span><span class="sxs-lookup"><span data-stu-id="e0c86-173">No support for direct manipulation as mouse, pen/stylus, and keyboard are indirect input devices.</span></span></td><td><span data-ttu-id="e0c86-174">Identisch mit der Maus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-174">Same as mouse.</span></span></td></tr>
</tbody></table>



**<span data-ttu-id="e0c86-175">Hinweis</span><span class="sxs-lookup"><span data-stu-id="e0c86-175">Note</span></span>**  
<span data-ttu-id="e0c86-176">Die indirekte Eingabe hat den Vorteil, dass sie über 25Jahre optimiert wurde.</span><span class="sxs-lookup"><span data-stu-id="e0c86-176">Indirect input has had the benefit of more than 25 years of refinement.</span></span> <span data-ttu-id="e0c86-177">Features wie durch Zeigen ausgelöste QuickInfos wurden als Lösung für die Erforschung der UI speziell für die Eingabe über Touchpad, Maus, Zeichen- oder Eingabestift und Tastatur entworfen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-177">Features such as hover-triggered tooltips have been designed to solve UI exploration specifically for touchpad, mouse, pen/stylus, and keyboard input.</span></span> <span data-ttu-id="e0c86-178">Solche UI-Funktionen wurden neu entworfen, um der umfassenden Toucheingabefunktion gerecht zu werden, ohne die Benutzererfahrung auf den anderen Geräten zu beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-178">UI features like this have been re-designed for the rich experience provided by touch input, without compromising the user experience for these other devices.</span></span>

 

## <a name="use-touch-feedback"></a><span data-ttu-id="e0c86-179">Verwenden von Feedback für die Fingereingabe</span><span class="sxs-lookup"><span data-stu-id="e0c86-179">Use touch feedback</span></span>

<span data-ttu-id="e0c86-180">Durch entsprechendes visuelles Feedback bei Interaktionen mit der App helfen Sie den Benutzern, zu erkennen und zu lernen, wie ihre Interaktionen von der App und der Windows-Plattform interpretiert werden, und sich daran anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-180">Appropriate visual feedback during interactions with your app helps users recognize, learn, and adapt to how their interactions are interpreted by both the app and the Windows platform.</span></span> <span data-ttu-id="e0c86-181">Visuelles Feedback kann auf erfolgreiche Interaktionen hinweisen, über den Systemstatus informieren, das Gefühl der Kontrolle verstärken, Fehler verringern, Benutzern das Verständnis des Systems und des Eingabegeräts erleichtern und zu Interaktionen ermutigen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-181">Visual feedback can indicate successful interactions, relay system status, improve the sense of control, reduce errors, help users understand the system and input device, and encourage interaction.</span></span>

<span data-ttu-id="e0c86-182">Visuelles Feedback ist wichtig, wenn der Benutzer die Fingereingabe für Aktivitäten verwendet, bei denen Positionsgenauigkeit gefragt ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-182">Visual feedback is critical when the user relies on touch input for activities that require accuracy and precision based on location.</span></span> <span data-ttu-id="e0c86-183">Zeigen Sie immer Feedback an, wenn Toucheingabe erkannt wird, damit der Benutzer die von der App und den Steuerelementen definierten angepassten Zielbestimmungsregeln versteht.</span><span class="sxs-lookup"><span data-stu-id="e0c86-183">Display feedback whenever and wherever touch input is detected, to help the user understand any custom targeting rules that are defined by your app and its controls.</span></span>


## <a name="targeting"></a><span data-ttu-id="e0c86-184">Zielbestimmung</span><span class="sxs-lookup"><span data-stu-id="e0c86-184">Targeting</span></span>

<span data-ttu-id="e0c86-185">Die Zielbestimmung wird durch Folgendes optimiert:</span><span class="sxs-lookup"><span data-stu-id="e0c86-185">Targeting is optimized through:</span></span>

-   <span data-ttu-id="e0c86-186">Größe der Toucheingabeziele</span><span class="sxs-lookup"><span data-stu-id="e0c86-186">Touch target sizes</span></span>

    <span data-ttu-id="e0c86-187">Klare Richtlinien für die Größe gewährleisten, dass Anwendungen eine angenehme UI bereitstellen, die Objekte und Steuerelemente enthält, die als Ziele einfach und sicher zu erreichen sind.</span><span class="sxs-lookup"><span data-stu-id="e0c86-187">Clear size guidelines ensure that applications provide a comfortable UI that contains objects and controls that are easy and safe to target.</span></span>

-   <span data-ttu-id="e0c86-188">Kontaktgeometrie</span><span class="sxs-lookup"><span data-stu-id="e0c86-188">Contact geometry</span></span>

    <span data-ttu-id="e0c86-189">Der gesamte Kontaktbereich des Fingers wird verwendet, um das wahrscheinlichste Zielobjekt zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e0c86-189">The entire contact area of the finger determines the most likely target object.</span></span>

-   <span data-ttu-id="e0c86-190">Scrubbing</span><span class="sxs-lookup"><span data-stu-id="e0c86-190">Scrubbing</span></span>

    <span data-ttu-id="e0c86-191">Elemente in einer Gruppe können leicht erneut als Ziele bestimmt werden, indem der Finger zwischen ihnen gezogen wird (beispielsweise Optionsfelder).</span><span class="sxs-lookup"><span data-stu-id="e0c86-191">Items within a group are easily re-targeted by dragging the finger between them (for example, radio buttons).</span></span> <span data-ttu-id="e0c86-192">Das aktuelle Element wird aktiviert, wenn der Finger gehoben wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-192">The current item is activated when the touch is released.</span></span>

-   <span data-ttu-id="e0c86-193">Wackeln</span><span class="sxs-lookup"><span data-stu-id="e0c86-193">Rocking</span></span>

    <span data-ttu-id="e0c86-194">Eng angeordnete Elemente (beispielsweise Hyperlinks) können leicht erneut als Ziel bestimmt werden, indem Sie mit dem Finger auf das Element drücken und ohne Ziehen mit dem Finger leicht über den Elementen hin- und herwackeln.</span><span class="sxs-lookup"><span data-stu-id="e0c86-194">Densely packed items (for example, hyperlinks) are easily re-targeted by pressing the finger down and, without sliding, rocking it back and forth over the items.</span></span> <span data-ttu-id="e0c86-195">Aufgrund von Okklusion wird das aktuelle Element durch eine QuickInfo oder die Statusleiste identifiziert und aktiviert, wenn der Finger gehoben wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-195">Due to occlusion, the current item is identified through a tooltip or the status bar and is activated when the touch is released.</span></span>

## <a name="accuracy"></a><span data-ttu-id="e0c86-196">Genauigkeit</span><span class="sxs-lookup"><span data-stu-id="e0c86-196">Accuracy</span></span>

<span data-ttu-id="e0c86-197">Berücksichtigen Sie beim Design ungenaue Interaktionen, indem Sie Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="e0c86-197">Design for sloppy interactions by using:</span></span>

-   <span data-ttu-id="e0c86-198">Andockpunkte, die bei Interaktionen der Benutzer mit dem Inhalt das Anhalten an der gewünschten Position erleichtern.</span><span class="sxs-lookup"><span data-stu-id="e0c86-198">Snap-points that can make it easier to stop at desired locations when users interact with content.</span></span>
-   <span data-ttu-id="e0c86-199">Führungsschienen für die Richtung, die beim vertikalen oder horizontalen Verschieben unterstützen, auch wenn die Hand in einem leichten Bogen bewegt wird. Weitere Informationen finden Sie unter [Anleitungen für das Verschieben](guidelines-for-panning.md).</span><span class="sxs-lookup"><span data-stu-id="e0c86-199">Directional "rails" that can assist with vertical or horizontal panning, even when the hand moves in a slight arc. For more information, see [Guidelines for panning](guidelines-for-panning.md).</span></span>

## <a name="occlusion"></a><span data-ttu-id="e0c86-200">Okklusion</span><span class="sxs-lookup"><span data-stu-id="e0c86-200">Occlusion</span></span>

<span data-ttu-id="e0c86-201">Okklusion durch Finger und Hand können Sie durch Folgendes vermeiden:</span><span class="sxs-lookup"><span data-stu-id="e0c86-201">Finger and hand occlusion is avoided through:</span></span>

-   <span data-ttu-id="e0c86-202">Größe und Positionierung der UI</span><span class="sxs-lookup"><span data-stu-id="e0c86-202">Size and positioning of UI</span></span>

    <span data-ttu-id="e0c86-203">Machen Sie die UI-Elemente groß genug, damit sie nicht vollständig von einem Fingerspitzen-Kontaktbereich verdeckt werden können.</span><span class="sxs-lookup"><span data-stu-id="e0c86-203">Make UI elements big enough so that they cannot be completely covered by a fingertip contact area.</span></span>

    <span data-ttu-id="e0c86-204">Positionieren Sie Menüs und Popups möglichst immer über dem Kontaktbereich.</span><span class="sxs-lookup"><span data-stu-id="e0c86-204">Position menus and pop-ups above the contact area whenever possible.</span></span>

-   <span data-ttu-id="e0c86-205">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="e0c86-205">Tooltips</span></span>

    <span data-ttu-id="e0c86-206">Wenn der Benutzer den Finger auf einem Objekt liegen lässt, sollten QuickInfos angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-206">Show tooltips when a user maintains finger contact on an object.</span></span> <span data-ttu-id="e0c86-207">Dies dient der Beschreibung der Objektfunktionen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-207">This is useful for describing object functionality.</span></span> <span data-ttu-id="e0c86-208">Der Benutzer kann verhindern, dass die QickInfo angezeigt wird, wenn er die Fingerspitze von Objekt herunterzieht.</span><span class="sxs-lookup"><span data-stu-id="e0c86-208">The user can drag the fingertip off the object to avoid invoking the tooltip.</span></span>

    <span data-ttu-id="e0c86-209">Versetzen Sie bei kleinen Objekten die QuickInfos, damit sie nicht vom Fingerspitzen-Kontaktbereich verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-209">For small objects, offset tooltips so they are not covered by the fingertip contact area.</span></span> <span data-ttu-id="e0c86-210">Dies ist hilfreich für die Zielbestimmung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-210">This is helpful for targeting.</span></span>

-   <span data-ttu-id="e0c86-211">Präzision durch Ziehpunkte</span><span class="sxs-lookup"><span data-stu-id="e0c86-211">Handles for precision</span></span>

    <span data-ttu-id="e0c86-212">Wenn Präzision erforderlich ist (beispielsweise bei der Textauswahl), stellen Sie versetzte Auswahlziehpunkte bereit, um die Genauigkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e0c86-212">Where precision is required (for example, text selection), provide selection handles that are offset to improve accuracy.</span></span> <span data-ttu-id="e0c86-213">Weitere Informationen finden Sie unter [Richtlinien für die Text- und Bildauswahl (Windows-Runtime-Apps)](guidelines-for-textselection.md).</span><span class="sxs-lookup"><span data-stu-id="e0c86-213">For more information, see [Guidelines for selecting text and images (Windows Runtime apps)](guidelines-for-textselection.md).</span></span>

## <a name="timing"></a><span data-ttu-id="e0c86-214">Zeitliche Steuerung</span><span class="sxs-lookup"><span data-stu-id="e0c86-214">Timing</span></span>

<span data-ttu-id="e0c86-215">Vermeiden Sie zeitlich festgelegte Modusänderungen und verwenden Sie stattdessen direkte Manipulation.</span><span class="sxs-lookup"><span data-stu-id="e0c86-215">Avoid timed mode changes in favor of direct manipulation.</span></span> <span data-ttu-id="e0c86-216">Bei der direkten Manipulation wird die direkte physische Handhabung eines Objekts in Echtzeit simuliert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-216">Direct manipulation simulates the direct, real-time physical handling of an object.</span></span> <span data-ttu-id="e0c86-217">Das Objekt reagiert, wenn die Finger bewegt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-217">The object responds as the fingers are moved.</span></span>

<span data-ttu-id="e0c86-218">Eine zeitlich festgelegte Interaktion dagegen tritt nach einer Fingereingabeinteraktion auf.</span><span class="sxs-lookup"><span data-stu-id="e0c86-218">A timed interaction, on the other hand, occurs after a touch interaction.</span></span> <span data-ttu-id="e0c86-219">Zeitlich festgelegte Interaktionen bestimmen normalerweise abhängig von unsichtbaren Schwellenwerten wie Zeit, Entfernung oder Geschwindigkeit, welcher Befehl ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e0c86-219">Timed interactions typically depend on invisible thresholds like time, distance, or speed to determine what command to perform.</span></span> <span data-ttu-id="e0c86-220">Bei zeitlich festgelegten Interaktionen erfolgt visuelles Feedback erst, wenn das System die Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-220">Timed interactions have no visual feedback until the system performs the action.</span></span>

<span data-ttu-id="e0c86-221">Die direkte Manipulation bietet gegenüber zeitlich festgelegten Interaktionen eine Reihe von Vorteilen:</span><span class="sxs-lookup"><span data-stu-id="e0c86-221">Direct manipulation provides a number of benefits over timed interactions:</span></span>

-   <span data-ttu-id="e0c86-222">Sofortiges visuelles Feedback bei Interaktionen weckt die Aufmerksamkeit der Benutzer und vermittelt ihnen ein Gefühl von Sicherheit und Kontrolle.</span><span class="sxs-lookup"><span data-stu-id="e0c86-222">Instant visual feedback during interactions make users feel more engaged, confident, and in control.</span></span>
-   <span data-ttu-id="e0c86-223">Direkte Manipulationen sorgen für mehr Sicherheit beim Erforschen eines Systems, da sie umkehrbar sind, das heißt, Benutzer können ihre Aktionen leicht auf logische und intuitive Weise Schritt für Schritt rückgängig machen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-223">Direct manipulations make it safer to explore a system because they are reversible—users can easily step back through their actions in a logical and intuitive manner.</span></span>
-   <span data-ttu-id="e0c86-224">Interaktionen, die direkte Auswirkungen auf Objekte haben und reale Interaktionen nachahmen, sind intuitiver und leichter zu finden und zu merken.</span><span class="sxs-lookup"><span data-stu-id="e0c86-224">Interactions that directly affect objects and mimic real world interactions are more intuitive, discoverable, and memorable.</span></span> <span data-ttu-id="e0c86-225">Sie sind nicht auf schwer verständliche oder abstrakte Interaktionen angewiesen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-225">They don't rely on obscure or abstract interactions.</span></span>
-   <span data-ttu-id="e0c86-226">Zeitlich festgelegte Interaktionen können schwer auszuführen sein, da die Benutzer willkürliche und unsichtbare Schwellenwerte erreichen müssen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-226">Timed interactions can be difficult to perform, as users must reach arbitrary and invisible thresholds.</span></span>

<span data-ttu-id="e0c86-227">Darüber hinaus wird Folgendes dringend empfohlen:</span><span class="sxs-lookup"><span data-stu-id="e0c86-227">In addition, the following are strongly recommended:</span></span>

-   <span data-ttu-id="e0c86-228">Manipulationen sollten nicht anhand der Anzahl der verwendeten Finger unterschieden werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-228">Manipulations should not be distinguished by the number of fingers used.</span></span>
-   <span data-ttu-id="e0c86-229">Die Interaktionen sollten zusammengesetzte Manipulationen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-229">Interactions should support compound manipulations.</span></span> <span data-ttu-id="e0c86-230">Beispiel: Zoomen durch Zusammendrücken und gleichzeitiges Ziehen der Finger, um etwas zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="e0c86-230">For example, pinch to zoom while dragging the fingers to pan.</span></span>
-   <span data-ttu-id="e0c86-231">Die Interaktionen sollten nicht anhand der Zeit unterschieden werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-231">Interactions should not be distinguished by time.</span></span> <span data-ttu-id="e0c86-232">Eine Interaktion sollte unabhängig von der Ausführungsdauer immer zum gleichen Ergebnis führen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-232">The same interaction should have the same outcome regardless of the time taken to perform it.</span></span> <span data-ttu-id="e0c86-233">Zeitbasierte Aktivierungen führen zu obligatorischen Verzögerungen für Benutzer und beeinträchtigen die immersive Natur der direkten Manipulation und die Wahrnehmung der Reaktion des Systems.</span><span class="sxs-lookup"><span data-stu-id="e0c86-233">Time-based activations introduce mandatory delays for users and detract from both the immersive nature of direct manipulation and the perception of system responsiveness.</span></span>

    <span data-ttu-id="e0c86-234">**Hinweis**  Eine Ausnahme ist die Verwendung bestimmter zeitlich festgelegter Interaktionen zur Unterstützung beim Testen und Erkunden (z.B. Drücken und Halten).</span><span class="sxs-lookup"><span data-stu-id="e0c86-234">**Note**  An exception to this is where you use specific timed interactions to assist in learning and exploration (for example, press and hold).</span></span>

     

-   <span data-ttu-id="e0c86-235">Entsprechende Beschreibungen und visuelle Hinweise haben einen großen Einfluss auf die Verwendung erweiterter Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-235">Appropriate descriptions and visual cues have a great effect on the use of advanced interactions.</span></span>


## <a name="app-views"></a><span data-ttu-id="e0c86-236">App-Ansichten</span><span class="sxs-lookup"><span data-stu-id="e0c86-236">App views</span></span>


<span data-ttu-id="e0c86-237">Mithilfe der Einstellungen für Bewegungen/Bildläufe und Zoomstufen können Sie die Interaktionsmöglichkeiten für Benutzer Ihrer App-Ansichten optimieren.</span><span class="sxs-lookup"><span data-stu-id="e0c86-237">Tweak the user interaction experience through the pan/scroll and zoom settings of your app views.</span></span> <span data-ttu-id="e0c86-238">Die App-Ansicht bestimmt, wie ein Benutzer auf Ihre App und deren Inhalte zugreift und diese manipuliert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-238">An app view dictates how a user accesses and manipulates your app and its content.</span></span> <span data-ttu-id="e0c86-239">Ansichten stellen außerdem bestimmte Verhaltensweisen bereit, beispielsweise das Trägheitsverhalten, das „Springen“ an Inhaltsgrenzen und die Andockpunkte.</span><span class="sxs-lookup"><span data-stu-id="e0c86-239">Views also provide behaviors such as inertia, content boundary bounce, and snap points.</span></span>

<span data-ttu-id="e0c86-240">Die Einstellungen für Verschieben und Scrollen des [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527)-Steuerelements legen fest, wie Benutzer in einer Ansicht navigieren können, wenn der Inhalt der Ansicht über den Viewport hinausgeht.</span><span class="sxs-lookup"><span data-stu-id="e0c86-240">Pan and scroll settings of the [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527) control dictate how users navigate within a single view, when the content of the view doesn't fit within the viewport.</span></span> <span data-ttu-id="e0c86-241">Eine Einzelansicht kann beispielsweise eine Seite in einem Magazin oder Buch, die Ordnerstruktur eines Computers, eine Dokumentbibliothek oder ein Fotoalbum sein.</span><span class="sxs-lookup"><span data-stu-id="e0c86-241">A single view can be, for example, a page of a magazine or book, the folder structure of a computer, a library of documents, or a photo album.</span></span>

<span data-ttu-id="e0c86-242">Zoomeinstellungen gelten sowohl für den optischen Zoom (unterstützt vom [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527)-Steuerelement) als auch für das [**Semantic Zoom**](https://msdn.microsoft.com/library/windows/apps/hh702601)-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="e0c86-242">Zoom settings apply to both optical zoom (supported by the [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527) control) and the [**Semantic Zoom**](https://msdn.microsoft.com/library/windows/apps/hh702601) control.</span></span> <span data-ttu-id="e0c86-243">Der semantische Zoom ist eine für Toucheingaben optimierte Technik, um große Bestände verwandter Daten oder Inhalte in einer einzelnen Ansicht darzustellen und in diesen zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="e0c86-243">Semantic Zoom is a touch-optimized technique for presenting and navigating large sets of related data or content within a single view.</span></span> <span data-ttu-id="e0c86-244">Dabei werden zwei unterschiedliche Klassifizierungsmodi (oder Zoomstufen) verwendet.</span><span class="sxs-lookup"><span data-stu-id="e0c86-244">It works by using two distinct modes of classification, or zoom levels.</span></span> <span data-ttu-id="e0c86-245">Dies ist mit dem Verschieben und dem Durchführen von Bildläufen innerhalb einer einzelnen Ansicht vergleichbar.</span><span class="sxs-lookup"><span data-stu-id="e0c86-245">This is analogous to panning and scrolling within a single view.</span></span> <span data-ttu-id="e0c86-246">Verschieben und Bildläufe können in Verbindung mit dem semantischen Zoom verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-246">Panning and scrolling can be used in conjunction with Semantic Zoom.</span></span>

<span data-ttu-id="e0c86-247">Verwenden Sie App-Ansichten und -Ereignisse zum Ändern des Verhaltens für Schwenken/Bildlauf und Zoom.</span><span class="sxs-lookup"><span data-stu-id="e0c86-247">Use app views and events to modify the pan/scroll and zoom behaviors.</span></span> <span data-ttu-id="e0c86-248">Dies kann für eine flüssigere Interaktion sorgen, als dies mit der Behandlung von Zeiger- und Gestikereignissen möglich ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-248">This can provide a smoother interaction experience than is possible through the handling of pointer and gesture events.</span></span>

<span data-ttu-id="e0c86-249">Weitere Informationen zu App-Ansichten finden Sie unter [Steuerelemente, Layouts und Text](https://msdn.microsoft.com/library/windows/apps/mt228348).</span><span class="sxs-lookup"><span data-stu-id="e0c86-249">For more info about app views, see [Controls, layouts, and text](https://msdn.microsoft.com/library/windows/apps/mt228348).</span></span>

## <a name="custom-touch-interactions"></a><span data-ttu-id="e0c86-250">Benutzerdefinierte Touchinteraktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-250">Custom touch interactions</span></span>


<span data-ttu-id="e0c86-251">Wenn Sie eine eigene Interaktionsunterstützung implementieren, sollten Sie daran denken, dass die Benutzer eine intuitive Umgebung erwarten, die die direkte Interaktion mit den UI-Elementen der App beinhaltet.</span><span class="sxs-lookup"><span data-stu-id="e0c86-251">If you implement your own interaction support, keep in mind that users expect an intuitive experience involving direct interaction with the UI elements in your app.</span></span> <span data-ttu-id="e0c86-252">Es empfiehlt sich, die benutzerdefinierten Interaktionen auf der Basis der Plattformsteuerelementbibliotheken zu modellieren, um auf diese Weise für eine konsistente und intuitive Benutzerumgebung zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-252">We recommend that you model your custom interactions on the platform control libraries to keep things consistent and discoverable.</span></span> <span data-ttu-id="e0c86-253">Die Steuerelemente in diesen Bibliotheken bieten umfassende Funktionen für Benutzerinteraktionen wie Standardinteraktionen, animierte Bewegungseffekte, visuelles Feedback und Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-253">The controls in these libraries provide the full user interaction experience, including standard interactions, animated physics effects, visual feedback, and accessibility.</span></span> <span data-ttu-id="e0c86-254">Erstellen Sie benutzerdefinierte Interaktionen nur dann, wenn ein eindeutiger, klar umrissener Bedarf besteht und es keine Basisinteraktion gibt, die das gewünschte Szenario unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-254">Create custom interactions only if there is a clear, well-defined requirement and basic interactions don't support your scenario.</span></span>

<span data-ttu-id="e0c86-255">Zum Bereitstellen von angepasster Toucheingabeunterstützung können Sie verschiedene [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911)-Ereignisse behandeln.</span><span class="sxs-lookup"><span data-stu-id="e0c86-255">To provide customized touch support, you can handle various [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) events.</span></span> <span data-ttu-id="e0c86-256">Diese Ereignisse sind in drei verschiedene Abstraktionsschichten gruppiert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-256">These events are grouped into three levels of abstraction.</span></span>

-   <span data-ttu-id="e0c86-257">Statische Gestikereignisse werden ausgelöst, wenn eine Interaktion abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-257">Static gesture events are triggered after an interaction is complete.</span></span> <span data-ttu-id="e0c86-258">Zu den Gestikereignissen zählen [**Tapped**](https://msdn.microsoft.com/library/windows/apps/br208985), [**DoubleTapped**](https://msdn.microsoft.com/library/windows/apps/br208922), [**RightTapped**](https://msdn.microsoft.com/library/windows/apps/br208984) und [**Holding**](https://msdn.microsoft.com/library/windows/apps/br208928).</span><span class="sxs-lookup"><span data-stu-id="e0c86-258">Gesture events include [**Tapped**](https://msdn.microsoft.com/library/windows/apps/br208985), [**DoubleTapped**](https://msdn.microsoft.com/library/windows/apps/br208922), [**RightTapped**](https://msdn.microsoft.com/library/windows/apps/br208984), and [**Holding**](https://msdn.microsoft.com/library/windows/apps/br208928).</span></span>

    <span data-ttu-id="e0c86-259">Sie können Gestikereignisse für bestimmte Elemente deaktivieren, indem Sie [**IsTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208939), [**IsDoubleTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208931), [**IsRightTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208937) und [**IsHoldingEnabled**](https://msdn.microsoft.com/library/windows/apps/br208935) auf **false** festlegen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-259">You can disable gesture events on specific elements by setting [**IsTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208939), [**IsDoubleTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208931), [**IsRightTapEnabled**](https://msdn.microsoft.com/library/windows/apps/br208937), and [**IsHoldingEnabled**](https://msdn.microsoft.com/library/windows/apps/br208935) to **false**.</span></span>

-   <span data-ttu-id="e0c86-260">Zeigerereignisse wie [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) und [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970) bieten Details auf unterer Ebene für jeden Touchkontakt, einschließlich Zeigerbewegung, und die Möglichkeit, Ereignisse des Drückens und Loslassens zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-260">Pointer events such as [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) and [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208970) provide low-level details for each touch contact, including pointer motion and the ability to distinguish press and release events.</span></span>

    <span data-ttu-id="e0c86-261">Bei einem Zeiger handelt es sich um eine generische Eingabeart mit einem vereinheitlichten Ereignismechanismus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-261">A pointer is a generic input type with a unified event mechanism.</span></span> <span data-ttu-id="e0c86-262">Er stellt grundlegende Informationen (wie die Bildschirmposition) für die aktive Eingabequelle (Touch, Touchpad, Maus oder Stift) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-262">It exposes basic info, such as screen position, on the active input source, which can be touch, touchpad, mouse, or pen.</span></span>

-   <span data-ttu-id="e0c86-263">Manipulationsgestikereignisse wie [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950) weisen auf eine fortlaufende Interaktion hin.</span><span class="sxs-lookup"><span data-stu-id="e0c86-263">Manipulation gesture events, such as [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950), indicate an ongoing interaction.</span></span> <span data-ttu-id="e0c86-264">Sie werden ausgelöst, wenn der Benutzer ein Element berührt, und bleiben so lange aktiv, bis der Benutzer den bzw. die Finger vom Element hebt oder die Manipulation abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-264">They start firing when the user touches an element and continue until the user lifts their finger(s), or the manipulation is canceled.</span></span>

    <span data-ttu-id="e0c86-265">Manipulationsereignisse umfassen Multitouchinteraktionen wie Zoomen, Schwenken und Drehen sowie Interaktionen, die Trägheits- und Geschwindigkeitsdaten nutzen (z.B. Ziehen).</span><span class="sxs-lookup"><span data-stu-id="e0c86-265">Manipulation events include multi-touch interactions such as zooming, panning, or rotating, and interactions that use inertia and velocity data such as dragging.</span></span> <span data-ttu-id="e0c86-266">Die von den Bearbeitungsereignissen bereitgestellten Informationen identifizieren nicht die Form der ausgeführten Interaktion. Stattdessen enthalten sie Daten, z.B. zu Position, Übersetzungsdelta und Geschwindigkeit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-266">The information provided by the manipulation events doesn't identify the form of the interaction that was performed, but rather includes data such as position, translation delta, and velocity.</span></span> <span data-ttu-id="e0c86-267">Mit diesen Touchdaten können Sie die Art der auszuführenden Interaktion ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e0c86-267">You can use this touch data to determine the type of interaction that should be performed.</span></span>

<span data-ttu-id="e0c86-268">Hier sehen Sie den grundlegenden Satz von Touchgesten, die von der UWP unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-268">Here is the basic set of touch gestures supported by the UWP.</span></span>

| <span data-ttu-id="e0c86-269">Name</span><span class="sxs-lookup"><span data-stu-id="e0c86-269">Name</span></span>           | <span data-ttu-id="e0c86-270">Typ</span><span class="sxs-lookup"><span data-stu-id="e0c86-270">Type</span></span>                 | <span data-ttu-id="e0c86-271">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0c86-271">Description</span></span>                                                                            |
|----------------|----------------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="e0c86-272">Tippen</span><span class="sxs-lookup"><span data-stu-id="e0c86-272">Tap</span></span>            | <span data-ttu-id="e0c86-273">Statische Geste</span><span class="sxs-lookup"><span data-stu-id="e0c86-273">Static gesture</span></span>       | <span data-ttu-id="e0c86-274">Der Bildschirm wird mit einem Finger berührt, und der Finger wird wieder angehoben.</span><span class="sxs-lookup"><span data-stu-id="e0c86-274">One finger touches the screen and lifts up.</span></span>                                            |
| <span data-ttu-id="e0c86-275">Gedrückt halten</span><span class="sxs-lookup"><span data-stu-id="e0c86-275">Press and hold</span></span> | <span data-ttu-id="e0c86-276">Statische Geste</span><span class="sxs-lookup"><span data-stu-id="e0c86-276">Static gesture</span></span>       | <span data-ttu-id="e0c86-277">Ein Finger berührt den Bildschirm und bleibt auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e0c86-277">One finger touches the screen and stays in place.</span></span>                                      |
| <span data-ttu-id="e0c86-278">Ziehen</span><span class="sxs-lookup"><span data-stu-id="e0c86-278">Slide</span></span>          | <span data-ttu-id="e0c86-279">Manipulationsgeste</span><span class="sxs-lookup"><span data-stu-id="e0c86-279">Manipulation gesture</span></span> | <span data-ttu-id="e0c86-280">Mindestens ein Finger berührt den Bildschirm und bewegt sich in die gleiche Richtung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-280">One or more fingers touch the screen and move in the same direction.</span></span>                   |
| <span data-ttu-id="e0c86-281">Streifen</span><span class="sxs-lookup"><span data-stu-id="e0c86-281">Swipe</span></span>          | <span data-ttu-id="e0c86-282">Manipulationsgeste</span><span class="sxs-lookup"><span data-stu-id="e0c86-282">Manipulation gesture</span></span> | <span data-ttu-id="e0c86-283">Mindestens ein Finger berührt den Bildschirm und bewegt sich um eine kurze Distanz in die gleiche Richtung.</span><span class="sxs-lookup"><span data-stu-id="e0c86-283">One or more fingers touch the screen and move a short distance in the same direction.</span></span>  |
| <span data-ttu-id="e0c86-284">Drehen</span><span class="sxs-lookup"><span data-stu-id="e0c86-284">Turn</span></span>           | <span data-ttu-id="e0c86-285">Manipulationsgeste</span><span class="sxs-lookup"><span data-stu-id="e0c86-285">Manipulation gesture</span></span> | <span data-ttu-id="e0c86-286">Mindestens zwei Finger berühren den Bildschirm und führen eine Kreisbewegung im oder gegen den Uhrzeigersinn aus.</span><span class="sxs-lookup"><span data-stu-id="e0c86-286">Two or more fingers touch the screen and move in a clockwise or counter-clockwise arc.</span></span> |
| <span data-ttu-id="e0c86-287">Zusammendrücken</span><span class="sxs-lookup"><span data-stu-id="e0c86-287">Pinch</span></span>          | <span data-ttu-id="e0c86-288">Manipulationsgeste</span><span class="sxs-lookup"><span data-stu-id="e0c86-288">Manipulation gesture</span></span> | <span data-ttu-id="e0c86-289">Mindestens zwei Finger berühren den Bildschirm und bewegen sich dichter zusammen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-289">Two or more fingers touch the screen and move closer together.</span></span>                         |
| <span data-ttu-id="e0c86-290">Aufziehen</span><span class="sxs-lookup"><span data-stu-id="e0c86-290">Stretch</span></span>        | <span data-ttu-id="e0c86-291">Manipulationsgeste</span><span class="sxs-lookup"><span data-stu-id="e0c86-291">Manipulation gesture</span></span> | <span data-ttu-id="e0c86-292">Mindestens zwei Finger berühren den Bildschirm und bewegen sich weiter auseinander.</span><span class="sxs-lookup"><span data-stu-id="e0c86-292">Two or more fingers touch the screen and move farther apart.</span></span>                           |

 

<!-- mijacobs: Removing for now. We don't have a real page to link to yet. 
For more info about gestures, manipulations, and interactions, see [Custom user interactions](custom-user-input-portal.md).
-->

## <a name="gesture-events"></a><span data-ttu-id="e0c86-293">Gestikereignisse</span><span class="sxs-lookup"><span data-stu-id="e0c86-293">Gesture events</span></span>


<span data-ttu-id="e0c86-294">In der [Steuerelementliste](https://msdn.microsoft.com/library/windows/apps/mt185406) finden Sie ausführliche Informationen zu einzelnen Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-294">For details about individual controls, see [Controls list](https://msdn.microsoft.com/library/windows/apps/mt185406).</span></span>

## <a name="pointer-events"></a><span data-ttu-id="e0c86-295">Zeigerereignisse</span><span class="sxs-lookup"><span data-stu-id="e0c86-295">Pointer events</span></span>


<span data-ttu-id="e0c86-296">Zeigerereignisse werden durch eine Vielzahl von aktiven Eingabequellen ausgelöst, darunter Toucheingabe, Touchpad, Stift und Maus (sie ersetzen herkömmliche Mausereignisse.)</span><span class="sxs-lookup"><span data-stu-id="e0c86-296">Pointer events are raised by a variety of active input sources, including touch, touchpad, pen, and mouse (they replace traditional mouse events.)</span></span>

<span data-ttu-id="e0c86-297">Zeigerereignisse basieren auf einen einzigen Eingabepunkt (Finger, Stiftspitze, Mauszeiger) und unterstützen keine geschwindigkeitsbasierten Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-297">Pointer events are based on a single input point (finger, pen tip, mouse cursor) and do not support velocity-based interactions.</span></span>

<span data-ttu-id="e0c86-298">Nachfolgend finden Sie eine Liste der Zeigerereignisse und der jeweiligen Ereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="e0c86-298">Here is a list of pointer events and their related event argument.</span></span>

| <span data-ttu-id="e0c86-299">Ereignis oder Klasse</span><span class="sxs-lookup"><span data-stu-id="e0c86-299">Event or class</span></span>                                                       | <span data-ttu-id="e0c86-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0c86-300">Description</span></span>                                                   |
|----------------------------------------------------------------------|---------------------------------------------------------------|
| [**<span data-ttu-id="e0c86-301">PointerPressed</span><span class="sxs-lookup"><span data-stu-id="e0c86-301">PointerPressed</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208971)             | <span data-ttu-id="e0c86-302">Tritt auf, wenn ein Finger den Bildschirm berührt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-302">Occurs when a single finger touches the screen.</span></span>               |
| [**<span data-ttu-id="e0c86-303">PointerReleased</span><span class="sxs-lookup"><span data-stu-id="e0c86-303">PointerReleased</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208972)           | <span data-ttu-id="e0c86-304">Tritt auf, wenn dieser Berührungskontakt gelöst wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-304">Occurs when that same touch contact is lifted.</span></span>                |
| [**<span data-ttu-id="e0c86-305">PointerMoved</span><span class="sxs-lookup"><span data-stu-id="e0c86-305">PointerMoved</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208970)                 | <span data-ttu-id="e0c86-306">Tritt auf, wenn der Mauszeiger über den Bildschirm gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-306">Occurs when the pointer is dragged across the screen.</span></span>         |
| [**<span data-ttu-id="e0c86-307">PointerEntered</span><span class="sxs-lookup"><span data-stu-id="e0c86-307">PointerEntered</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208968)             | <span data-ttu-id="e0c86-308">Tritt auf, wenn der Zeiger in den Treffertestbereich eines Elements eintritt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-308">Occurs when a pointer enters the hit test area of an element.</span></span> |
| [**<span data-ttu-id="e0c86-309">PointerExited</span><span class="sxs-lookup"><span data-stu-id="e0c86-309">PointerExited</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208969)               | <span data-ttu-id="e0c86-310">Tritt auf, wenn der Zeiger aus dem Treffertestbereich eines Elements austritt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-310">Occurs when a pointer exits the hit test area of an element.</span></span>  |
| [**<span data-ttu-id="e0c86-311">PointerCanceled</span><span class="sxs-lookup"><span data-stu-id="e0c86-311">PointerCanceled</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208964)           | <span data-ttu-id="e0c86-312">Tritt auf, wenn ein Touchkontakt nicht normal verloren geht.</span><span class="sxs-lookup"><span data-stu-id="e0c86-312">Occurs when a touch contact is abnormally lost.</span></span>               |
| [**<span data-ttu-id="e0c86-313">PointerCaptureLost</span><span class="sxs-lookup"><span data-stu-id="e0c86-313">PointerCaptureLost</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208965)     | <span data-ttu-id="e0c86-314">Tritt auf, wenn ein Zeiger durch ein anderes Element erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-314">Occurs when a pointer capture is taken by another element.</span></span>    |
| [**<span data-ttu-id="e0c86-315">PointerWheelChanged</span><span class="sxs-lookup"><span data-stu-id="e0c86-315">PointerWheelChanged</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208973)   | <span data-ttu-id="e0c86-316">Tritt auf, wenn sich der Deltawert eines Mausrads ändert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-316">Occurs when the delta value of a mouse wheel changes.</span></span>         |
| [**<span data-ttu-id="e0c86-317">PointerRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-317">PointerRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh943076) | <span data-ttu-id="e0c86-318">Stellt Daten für alle Zeigerereignisse bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-318">Provides data for all pointer events.</span></span>                         |

 

<span data-ttu-id="e0c86-319">Das folgende Beispiel zeigt, wie die Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971), [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) und [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) verwendet werden, um eine Tippinteraktion für ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)-Objekt zu behandeln ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-319">The following example shows how to use the [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971), [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972), and [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) events to handle a tap interaction on a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) object.</span></span>

<span data-ttu-id="e0c86-320">Zuerst wird ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) mit dem Namen `touchRectangle` in Extensible Application Markup Language (XAML) erstellt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-320">First, a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) named `touchRectangle` is created in Extensible Application Markup Language (XAML).</span></span>

```XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Rectangle Name="touchRectangle"
           Height="100" Width="200" Fill="Blue" />
</Grid>
```
<span data-ttu-id="e0c86-321">Als Nächstes werden Listener für die Ereignisse [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971), [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) und [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-321">Next, listeners for the [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971), [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972), and [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) events are specified.</span></span>

```cpp
MainPage::MainPage()
{
    InitializeComponent();

    // Pointer event listeners.
    touchRectangle->PointerPressed += ref new PointerEventHandler(this, &MainPage::touchRectangle_PointerPressed);
    touchRectangle->PointerReleased += ref new PointerEventHandler(this, &MainPage::touchRectangle_PointerReleased);
    touchRectangle->PointerExited += ref new PointerEventHandler(this, &MainPage::touchRectangle_PointerExited);
}
```

```cs
public MainPage()
{
    this.InitializeComponent();

    // Pointer event listeners.
    touchRectangle.PointerPressed += touchRectangle_PointerPressed;
    touchRectangle.PointerReleased += touchRectangle_PointerReleased;
    touchRectangle.PointerExited += touchRectangle_PointerExited;
}
```

```vb
Public Sub New()

    ' This call is required by the designer.
    InitializeComponent()

    ' Pointer event listeners.
    AddHandler touchRectangle.PointerPressed, AddressOf touchRectangle_PointerPressed
    AddHandler touchRectangle.PointerReleased, AddressOf Me.touchRectangle_PointerReleased
    AddHandler touchRectangle.PointerExited, AddressOf touchRectangle_PointerExited

End Sub
```

<span data-ttu-id="e0c86-322">Schließlich vergrößert der [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971)-Ereignishandler die [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) und [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) des [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), während die [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) und [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969)-Ereignishandler die **Höhe** und die **Breite** wieder auf ihre Anfangswerte zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-322">Finally, the [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208971) event handler increases the [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) and [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) of the [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle), while the [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208972) and [**PointerExited**](https://msdn.microsoft.com/library/windows/apps/br208969) event handlers set the **Height** and **Width** back to their starting values.</span></span>

```cpp
// Handler for pointer exited event.
void MainPage::touchRectangle_PointerExited(Object^ sender, PointerRoutedEventArgs^ e)
{
    Rectangle^ rect = (Rectangle^)sender;

    // Pointer moved outside Rectangle hit test area.
    // Reset the dimensions of the Rectangle.
    if (nullptr != rect)
    {
        rect->Width = 200;
        rect->Height = 100;
    }
}

// Handler for pointer released event.
void MainPage::touchRectangle_PointerReleased(Object^ sender, PointerRoutedEventArgs^ e)
{
    Rectangle^ rect = (Rectangle^)sender;

    // Reset the dimensions of the Rectangle.
    if (nullptr != rect)
    {
        rect->Width = 200;
        rect->Height = 100;
    }
}

// Handler for pointer pressed event.
void MainPage::touchRectangle_PointerPressed(Object^ sender, PointerRoutedEventArgs^ e)
{
    Rectangle^ rect = (Rectangle^)sender;

    // Change the dimensions of the Rectangle.
    if (nullptr != rect)
    {
        rect->Width = 250;
        rect->Height = 150;
    }
}
```

```cs
// Handler for pointer exited event.
private void touchRectangle_PointerExited(object sender, PointerRoutedEventArgs e)
{
    Rectangle rect = sender as Rectangle;

    // Pointer moved outside Rectangle hit test area.
    // Reset the dimensions of the Rectangle.
    if (null != rect)
    {
        rect.Width = 200;
        rect.Height = 100;
    }
}
// Handler for pointer released event.
private void touchRectangle_PointerReleased(object sender, PointerRoutedEventArgs e)
{
    Rectangle rect = sender as Rectangle;

    // Reset the dimensions of the Rectangle.
    if (null != rect)
    {
        rect.Width = 200;
        rect.Height = 100;
    }
}

// Handler for pointer pressed event.
private void touchRectangle_PointerPressed(object sender, PointerRoutedEventArgs e)
{
    Rectangle rect = sender as Rectangle;

    // Change the dimensions of the Rectangle.
    if (null != rect)
    {
        rect.Width = 250;
        rect.Height = 150;
    }
}
```

```vb
' Handler for pointer exited event.
Private Sub touchRectangle_PointerExited(sender As Object, e As PointerRoutedEventArgs)
    Dim rect As Rectangle = CType(sender, Rectangle)

    ' Pointer moved outside Rectangle hit test area.
    ' Reset the dimensions of the Rectangle.
    If (rect IsNot Nothing) Then
        rect.Width = 200
        rect.Height = 100
    End If
End Sub

' Handler for pointer released event.
Private Sub touchRectangle_PointerReleased(sender As Object, e As PointerRoutedEventArgs)
    Dim rect As Rectangle = CType(sender, Rectangle)

    ' Reset the dimensions of the Rectangle.
    If (rect IsNot Nothing) Then
        rect.Width = 200
        rect.Height = 100
    End If
End Sub

' Handler for pointer pressed event.
Private Sub touchRectangle_PointerPressed(sender As Object, e As PointerRoutedEventArgs)
    Dim rect As Rectangle = CType(sender, Rectangle)

    ' Change the dimensions of the Rectangle.
    If (rect IsNot Nothing) Then
        rect.Width = 250
        rect.Height = 150
    End If
End Sub
```

## <a name="manipulation-events"></a><span data-ttu-id="e0c86-323">Manipulationsereignisse</span><span class="sxs-lookup"><span data-stu-id="e0c86-323">Manipulation events</span></span>


<span data-ttu-id="e0c86-324">Verwenden Sie Manipulationsereignisse, wenn Sie in Ihrer App Mehrfingereingabe-Interaktionen oder Interaktionen unterstützen müssen, die Geschwindigkeitsdaten erfordern.</span><span class="sxs-lookup"><span data-stu-id="e0c86-324">Use manipulation events if you need to support multiple finger interactions in your app, or interactions that require velocity data.</span></span>

<span data-ttu-id="e0c86-325">Mithilfe von Manipulationsereignissen können Sie Interaktionen wie Ziehen, Zoomen und Halten erkennen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-325">You can use manipulation events to detect interactions such as drag, zoom, and hold.</span></span>

<span data-ttu-id="e0c86-326">Nachfolgend finden Sie eine Liste der Manipulationsereignisse und der jeweiligen Ereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="e0c86-326">Here is a list of manipulation events and related event arguments.</span></span>

| <span data-ttu-id="e0c86-327">Ereignis oder Klasse</span><span class="sxs-lookup"><span data-stu-id="e0c86-327">Event or class</span></span>                                                                                               | <span data-ttu-id="e0c86-328">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e0c86-328">Description</span></span>                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| [**<span data-ttu-id="e0c86-329">ManipulationStarting-Ereignis</span><span class="sxs-lookup"><span data-stu-id="e0c86-329">ManipulationStarting event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208951)                                   | <span data-ttu-id="e0c86-330">Tritt auf, wenn der Bearbeitungsprozessor zuerst erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-330">Occurs when the manipulation processor is first created.</span></span>                                                                                  |
| [**<span data-ttu-id="e0c86-331">ManipulationStarted-Ereignis</span><span class="sxs-lookup"><span data-stu-id="e0c86-331">ManipulationStarted event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208950)                                     | <span data-ttu-id="e0c86-332">Tritt auf, wenn ein Eingabegerät mit der Bearbeitung für das [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) beginnt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-332">Occurs when an input device begins a manipulation on the [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911).</span></span>                                            |
| [**<span data-ttu-id="e0c86-333">ManipulationDelta-Ereignis</span><span class="sxs-lookup"><span data-stu-id="e0c86-333">ManipulationDelta event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208946)                                         | <span data-ttu-id="e0c86-334">Tritt auf, wenn ein Eingabegerät bei der Bearbeitung die Position ändert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-334">Occurs when the input device changes position during a manipulation.</span></span>                                                                      |
| [**<span data-ttu-id="e0c86-335">ManipulationInertiaStarting-Ereignis</span><span class="sxs-lookup"><span data-stu-id="e0c86-335">ManipulationInertiaStarting event</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702425)                | <span data-ttu-id="e0c86-336">Tritt auf, wenn das Eingabegerät während einer Bearbeitung Kontakt mit dem [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911)-Objekt verliert und die Trägheit beginnt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-336">Occurs when the input device loses contact with the [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) object during a manipulation and inertia begins.</span></span> |
| [**<span data-ttu-id="e0c86-337">ManipulationCompleted-Ereignis</span><span class="sxs-lookup"><span data-stu-id="e0c86-337">ManipulationCompleted event</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208945)                                 | <span data-ttu-id="e0c86-338">Tritt auf, wenn Bearbeitung und Trägheit für das [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="e0c86-338">Occurs when a manipulation and inertia on the [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) are complete.</span></span>                                          |
| [**<span data-ttu-id="e0c86-339">ManipulationStartingRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-339">ManipulationStartingRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702132)               | <span data-ttu-id="e0c86-340">Stelle Daten für das [**ManipulationStarting**](https://msdn.microsoft.com/library/windows/apps/br208951)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-340">Provides data for the [**ManipulationStarting**](https://msdn.microsoft.com/library/windows/apps/br208951) event.</span></span>                                         |
| [**<span data-ttu-id="e0c86-341">ManipulationStartedRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-341">ManipulationStartedRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702101)                 | <span data-ttu-id="e0c86-342">Stellt Daten für das [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-342">Provides data for the [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950) event.</span></span>                                           |
| [**<span data-ttu-id="e0c86-343">ManipulationDeltaRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-343">ManipulationDeltaRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702051)                     | <span data-ttu-id="e0c86-344">Stellt Daten für das [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-344">Provides data for the [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946) event.</span></span>                                               |
| [**<span data-ttu-id="e0c86-345">ManipulationInertiaStartingRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-345">ManipulationInertiaStartingRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702074) | <span data-ttu-id="e0c86-346">Stellt Daten für das [**ManipulationInertiaStarting**](https://msdn.microsoft.com/library/windows/apps/br208947)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-346">Provides data for the [**ManipulationInertiaStarting**](https://msdn.microsoft.com/library/windows/apps/br208947) event.</span></span>                           |
| [**<span data-ttu-id="e0c86-347">ManipulationVelocities</span><span class="sxs-lookup"><span data-stu-id="e0c86-347">ManipulationVelocities</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242032)                                              | <span data-ttu-id="e0c86-348">Beschreibt die Geschwindigkeit, mit der die Bearbeitung stattfindet.</span><span class="sxs-lookup"><span data-stu-id="e0c86-348">Describes the speed at which manipulations occur.</span></span>                                                                                         |
| [**<span data-ttu-id="e0c86-349">ManipulationCompletedRoutedEventArgs</span><span class="sxs-lookup"><span data-stu-id="e0c86-349">ManipulationCompletedRoutedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh702035)             | <span data-ttu-id="e0c86-350">Stellt Daten für das [**ManipulationCompleted**](https://msdn.microsoft.com/library/windows/apps/br208945)-Ereignis bereit.</span><span class="sxs-lookup"><span data-stu-id="e0c86-350">Provides data for the [**ManipulationCompleted**](https://msdn.microsoft.com/library/windows/apps/br208945) event.</span></span>                                       |

 

<span data-ttu-id="e0c86-351">Eine Bewegung setzt sich aus einer Reihe von Bearbeitungsereignissen zusammen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-351">A gesture consists of a series of manipulation events.</span></span> <span data-ttu-id="e0c86-352">Jede Geste beginnt mit einem [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950) (z.B., wenn ein Benutzer den Bildschirm berührt).</span><span class="sxs-lookup"><span data-stu-id="e0c86-352">Each gesture starts with a [**ManipulationStarted**](https://msdn.microsoft.com/library/windows/apps/br208950) event, such as when a user touches the screen.</span></span>

<span data-ttu-id="e0c86-353">Anschließend wird mindestens ein [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946)-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="e0c86-353">Next, one or more [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946) events are fired.</span></span> <span data-ttu-id="e0c86-354">Beispielsweise, wenn Sie den Bildschirm berühren und dann den Finger über den Bildschirm ziehen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-354">For example, if you touch the screen and then drag your finger across the screen.</span></span> <span data-ttu-id="e0c86-355">Schließlich wird ein [**ManipulationCompleted**](https://msdn.microsoft.com/library/windows/apps/br208945)-Ereignis ausgelöst, wenn die Interaktion beendet ist.</span><span class="sxs-lookup"><span data-stu-id="e0c86-355">Finally, a [**ManipulationCompleted**](https://msdn.microsoft.com/library/windows/apps/br208945) event is raised when the interaction finishes.</span></span>

<span data-ttu-id="e0c86-356">**Hinweis**  Wenn Sie keinen Touchscreen besitzen, können Sie Ihren Manipulationsereigniscode in der Simulation mithilfe einer Maus- und Mausradschnittstelle testen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-356">**Note**  If you don't have a touch-screen monitor, you can test your manipulation event code in the simulator using a mouse and mouse wheel interface.</span></span>

 

<span data-ttu-id="e0c86-357">Das folgende Beispiel zeigt, wie die [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946)-Ereignisse verwendet werden, um eine Ziehen-Interaktion für ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) zu behandeln und es über den Bildschirm zu bewegen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-357">The following example shows how to use the [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946) events to handle a slide interaction on a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) and move it across the screen.</span></span>

<span data-ttu-id="e0c86-358">Zuerst wird ein [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) mit dem Namen `touchRectangle` mit einer [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) und [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) von 200 in XAML erstellt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-358">First, a [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) named `touchRectangle` is created in XAML with a [**Height**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Height) and [**Width**](/uwp/api/Windows.UI.Xaml.FrameworkElement.Width) of 200.</span></span>

```XAML
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Rectangle Name="touchRectangle"
               Width="200" Height="200" Fill="Blue" 
               ManipulationMode="All"/>
</Grid>
```

<span data-ttu-id="e0c86-359">Anschließend wird ein globales [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/br243027)-Element mit dem Namen `dragTranslation` erstellt, mit dem das [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)-Element übersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="e0c86-359">Next, a global [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/br243027) named `dragTranslation` is created for translating the [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle).</span></span> <span data-ttu-id="e0c86-360">Ein [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946)-Ereignislistener wird für das **Rechteck** angegeben, und `dragTranslation` wird zum [**RenderTransform**](https://msdn.microsoft.com/library/windows/apps/br208980)-Element des **Rechtecks** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e0c86-360">A [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946) event listener is specified on the **Rectangle**, and `dragTranslation` is added to the [**RenderTransform**](https://msdn.microsoft.com/library/windows/apps/br208980) of the **Rectangle**.</span></span>

```cpp
// Global translation transform used for changing the position of 
// the Rectangle based on input data from the touch contact.
Windows::UI::Xaml::Media::TranslateTransform^ dragTranslation;
```

```cs
// Global translation transform used for changing the position of 
// the Rectangle based on input data from the touch contact.
private TranslateTransform dragTranslation;
```

```vb
' Global translation transform used for changing the position of 
' the Rectangle based on input data from the touch contact.
Private dragTranslation As TranslateTransform
```

```cpp
MainPage::MainPage()
{
    InitializeComponent();

    // Listener for the ManipulationDelta event.
    touchRectangle->ManipulationDelta += 
        ref new ManipulationDeltaEventHandler(
            this, 
            &MainPage::touchRectangle_ManipulationDelta);
    // New translation transform populated in 
    // the ManipulationDelta handler.
    dragTranslation = ref new TranslateTransform();
    // Apply the translation to the Rectangle.
    touchRectangle->RenderTransform = dragTranslation;
}
```

```cs
public MainPage()
{
    this.InitializeComponent();

    // Listener for the ManipulationDelta event.
    touchRectangle.ManipulationDelta += touchRectangle_ManipulationDelta;
    // New translation transform populated in 
    // the ManipulationDelta handler.
    dragTranslation = new TranslateTransform();
    // Apply the translation to the Rectangle.
    touchRectangle.RenderTransform = this.dragTranslation;
}
```

```vb
Public Sub New()

    ' This call is required by the designer.
    InitializeComponent()

    ' Listener for the ManipulationDelta event.
    AddHandler touchRectangle.ManipulationDelta,
        AddressOf testRectangle_ManipulationDelta
    ' New translation transform populated in 
    ' the ManipulationDelta handler.
    dragTranslation = New TranslateTransform()
    ' Apply the translation to the Rectangle.
    touchRectangle.RenderTransform = dragTranslation

End Sub
```

<span data-ttu-id="e0c86-361">Schließlich wird im [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946)-Ereignishandler die Position des [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) mit der [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/br243027)-Eigenschaft für die [**Delta**](https://msdn.microsoft.com/library/windows/apps/hh702058)-Eigenschaft aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-361">Finally, in the [**ManipulationDelta**](https://msdn.microsoft.com/library/windows/apps/br208946) event handler, the position of the [**Rectangle**](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle) is updated by using the [**TranslateTransform**](https://msdn.microsoft.com/library/windows/apps/br243027) on the [**Delta**](https://msdn.microsoft.com/library/windows/apps/hh702058) property.</span></span>

```cpp
// Handler for the ManipulationDelta event.
// ManipulationDelta data is loaded into the
// translation transform and applied to the Rectangle.
void MainPage::touchRectangle_ManipulationDelta(Object^ sender,
    ManipulationDeltaRoutedEventArgs^ e)
{
    // Move the rectangle.
    dragTranslation->X += e->Delta.Translation.X;
    dragTranslation->Y += e->Delta.Translation.Y;
    
}
```

```cs
// Handler for the ManipulationDelta event.
// ManipulationDelta data is loaded into the
// translation transform and applied to the Rectangle.
void touchRectangle_ManipulationDelta(object sender,
    ManipulationDeltaRoutedEventArgs e)
{
    // Move the rectangle.
    dragTranslation.X += e.Delta.Translation.X;
    dragTranslation.Y += e.Delta.Translation.Y;
}
```

```vb
' Handler for the ManipulationDelta event.
' ManipulationDelta data Is loaded into the
' translation transform And applied to the Rectangle.
Private Sub testRectangle_ManipulationDelta(
    sender As Object,
    e As ManipulationDeltaRoutedEventArgs)

    ' Move the rectangle.
    dragTranslation.X = (dragTranslation.X + e.Delta.Translation.X)
    dragTranslation.Y = (dragTranslation.Y + e.Delta.Translation.Y)

End Sub
```

## <a name="routed-events"></a><span data-ttu-id="e0c86-362">Routingereignisse</span><span class="sxs-lookup"><span data-stu-id="e0c86-362">Routed events</span></span>


<span data-ttu-id="e0c86-363">Alle hier erwähnten Zeiger-, Gestik- und Manipulationsereignisse werden als *Routingereignisse* implementiert.</span><span class="sxs-lookup"><span data-stu-id="e0c86-363">All of the pointer events, gesture events and manipulation events mentioned here are implemented as *routed events*.</span></span> <span data-ttu-id="e0c86-364">Folglich kann das Ereignis potenziell auch von Objekten behandelt werden, bei denen es sich nicht um das Objekt handelt, von dem das Ereignis ursprünglich ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="e0c86-364">This means that the event can potentially be handled by objects other than the one that originally raised the event.</span></span> <span data-ttu-id="e0c86-365">Von aufeinander folgenden übergeordneten Elementen in einer Objektstruktur (wie etwa den übergeordneten Containern eines [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911)-Elements oder dem [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503)-Stammelement Ihrer App) können diese Ereignisse auch dann behandelt werden, wenn sie vom ursprünglichen Element nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-365">Successive parents in an object tree, such as the parent containers of a [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) or the root [**Page**](https://msdn.microsoft.com/library/windows/apps/br227503) of your app, can choose to handle these events even if the original element does not.</span></span> <span data-ttu-id="e0c86-366">Umgekehrt gilt: Ein Objekt, von dem das Ereignis nicht behandelt wird, kann das Ereignis als behandelt markieren, damit es keine übergeordneten Elemente mehr erreicht.</span><span class="sxs-lookup"><span data-stu-id="e0c86-366">Conversely, any object that does handle the event can mark the event handled so that it no longer reaches any parent element.</span></span> <span data-ttu-id="e0c86-367">Weitere Informationen zum Konzept der Routingereignisse sowie zu den Auswirkungen auf die Erstellung von Handlern für Routingereignisse finden Sie unter [Übersicht über Ereignisse und Routingereignisse](https://msdn.microsoft.com/library/windows/apps/hh758286).</span><span class="sxs-lookup"><span data-stu-id="e0c86-367">For more info about the routed event concept and how it affects how you write handlers for routed events, see [Events and routed events overview](https://msdn.microsoft.com/library/windows/apps/hh758286).</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="e0c86-368">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="e0c86-368">Dos and don'ts</span></span>


-   <span data-ttu-id="e0c86-369">Entwerfen Sie Apps mit Toucheingabe als primär erwartete Eingabemethode.</span><span class="sxs-lookup"><span data-stu-id="e0c86-369">Design applications with touch interaction as the primary expected input method.</span></span>
-   <span data-ttu-id="e0c86-370">Bieten Sie visuelles Feedback für alle Arten von Interaktionen (Berühren, Zeichenstift, Eingabestift, Maus usw.).</span><span class="sxs-lookup"><span data-stu-id="e0c86-370">Provide visual feedback for interactions of all types (touch, pen, stylus, mouse, etc.)</span></span>
-   <span data-ttu-id="e0c86-371">Optimieren Sie die Zielbestimmung, indem Sie die Größe des Toucheingabeziels, die Kontaktgeometrie, das Scrubbing und das Wackeln anpassen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-371">Optimize targeting by adjusting touch target size, contact geometry, scrubbing and rocking.</span></span>
-   <span data-ttu-id="e0c86-372">Optimieren Sie die Genauigkeit durch Verwendung von Andockpunkten und Führungsschienen.</span><span class="sxs-lookup"><span data-stu-id="e0c86-372">Optimize accuracy through the use of snap points and directional "rails".</span></span>
-   <span data-ttu-id="e0c86-373">Stellen Sie QuickInfos und Handles bereit, um die Genauigkeit der Toucheingabe für eng aneinanderliegende UI-Elemente zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e0c86-373">Provide tooltips and handles to help improve touch accuracy for tightly packed UI items.</span></span>
-   <span data-ttu-id="e0c86-374">Verwenden Sie nach Möglichkeit keine zeitlich festgelegten Interaktionen (Beispiel für eine richtige Verwendung: Berühren und Halten).</span><span class="sxs-lookup"><span data-stu-id="e0c86-374">Don't use timed interactions whenever possible (example of appropriate use: touch and hold).</span></span>
-   <span data-ttu-id="e0c86-375">Verwenden Sie nach Möglichkeit nicht die Anzahl der zu verwendenden Finger, um zwischen den Manipulationen zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="e0c86-375">Don't use the number of fingers used to distinguish the manipulation whenever possible.</span></span>


## <a name="related-articles"></a><span data-ttu-id="e0c86-376">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="e0c86-376">Related articles</span></span>

* [<span data-ttu-id="e0c86-377">Behandeln von Zeigereingaben</span><span class="sxs-lookup"><span data-stu-id="e0c86-377">Handle pointer input</span></span>](handle-pointer-input.md)
* [<span data-ttu-id="e0c86-378">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="e0c86-378">Identify input devices</span></span>](identify-input-devices.md)

**<span data-ttu-id="e0c86-379">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e0c86-379">Samples</span></span>**

* [<span data-ttu-id="e0c86-380">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="e0c86-380">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="e0c86-381">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="e0c86-381">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="e0c86-382">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="e0c86-382">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)
* [<span data-ttu-id="e0c86-383">Beispiel für visuelle Fokuselemente</span><span class="sxs-lookup"><span data-stu-id="e0c86-383">Focus visuals sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619895)

**<span data-ttu-id="e0c86-384">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="e0c86-384">Archive Samples</span></span>**

* [<span data-ttu-id="e0c86-385">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="e0c86-385">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
* [<span data-ttu-id="e0c86-386">Eingabe: Beispiel für XAML-Benutzereingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="e0c86-386">Input: XAML user input events sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=226855)
* [<span data-ttu-id="e0c86-387">Beispiel für XAML-Bildlauf, -Verschiebung und -Zoom</span><span class="sxs-lookup"><span data-stu-id="e0c86-387">XAML scrolling, panning, and zooming sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=251717)
* [<span data-ttu-id="e0c86-388">Eingabe: Gesten und Manipulationen mit GestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="e0c86-388">Input: Gestures and manipulations with GestureRecognizer</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231605)
 

 




