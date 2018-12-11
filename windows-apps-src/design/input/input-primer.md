---
Description: User interactions in the Universal Windows Platform (UWP) are a combination of input and output sources (such as mouse, keyboard, pen, touch, touchpad, speech, Cortana, controller, gesture, gaze, and so on), along with various modes or modifiers that enable extended experiences (including mouse wheel and buttons, pen eraser and barrel buttons, touch keyboard, and background app services).
title: Einführung in die Interaktion
ms.assetid: 73008F80-FE62-457D-BAEC-412ED6BAB0C8
label: Interaction primer
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d9b2a894746cc9f26a0ebb3df90c967a73914c3c
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8947802"
---
# <a name="interaction-primer"></a><span data-ttu-id="5f6c4-103">Einführung in die Interaktion</span><span class="sxs-lookup"><span data-stu-id="5f6c4-103">Interaction primer</span></span>

![Windows-Eingabetypen](images/input-interactions/icons-inputdevices03.png)

<span data-ttu-id="5f6c4-105">Benutzerinteraktionen in der Universellen Windows-Plattform (UWP) stellen eine Kombination von Eingabe- und Ausgabequellen dar (z. B. Maus, Tastatur, Stift, Toucheingabe, Touchpad, Spracherkennung, **Cortana**, Controller, Gesten, Mimik usw.), neben verschiedenen Modi oder Modifizierern, die erweiterte Funktionen ermöglichen (u. a. Mausrad und -tasten, Radierer- und Zeichenstift-Schaltflächen, Bildschirmtastatur sowie App-Dienste im Hintergrund).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-105">User interactions in the Universal Windows Platform (UWP) are a combination of input and output sources (such as mouse, keyboard, pen, touch, touchpad, speech, **Cortana**, controller, gesture, gaze, and so on), along with various modes or modifiers that enable extended experiences (including mouse wheel and buttons, pen eraser and barrel buttons, touch keyboard, and background app services).</span></span>

<span data-ttu-id="5f6c4-106">Die UWP verwendet ein intelligentes, kontextbezogenes Interaktionssystem, mit dem in den meisten Fällen die von der App empfangenen eindeutigen Eingabetypen nicht individuell behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-106">The UWP uses a "smart" contextual interaction system that, in most cases, eliminates the need to individually handle the unique types of input received by your app.</span></span> <span data-ttu-id="5f6c4-107">Dazu zählt das Behandeln von Toucheingabe, Touchpad, Maus und Stifteingabe als generischer Zeigertyp, um statische Gesten wie Tippen oder Gedrückthalten und Manipulationsgesten wie Ziehen zum Verschieben oder zum Rendern von Freihandeingabe zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-107">This includes handling touch, touchpad, mouse, and pen input as a generic pointer type to support static gestures such as tap or press-and-hold, manipulation gestures such as slide for panning, or rendering digital ink.</span></span>

<span data-ttu-id="5f6c4-108">Machen Sie sich mit den verschiedenen Arten von Eingabegeräten sowie ihren Verhaltensweisen, Möglichkeiten und Einschränkungen in Verbindung mit bestimmten Formfaktoren vertraut.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-108">Familiarize yourself with each input device type and its behaviors, capabilities, and limitations when paired with certain form factors.</span></span> <span data-ttu-id="5f6c4-109">Dies erleichtert Ihnen die Entscheidung, ob die Steuerelemente und Angebote der Plattform für die App ausreichend sind oder ob Sie angepasste Funktionen für die Benutzerinteraktion bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-109">This can help you decide whether the platform controls and affordances are sufficient for your app, or require you to provide customized interaction experiences.</span></span>

## <a name="gaze"></a><span data-ttu-id="5f6c4-110">Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="5f6c4-110">Gaze</span></span>

<span data-ttu-id="5f6c4-111">Mit dem **Windows 10-Update April 2018** haben wir die Unterstützung für die Blickeingabe mit Eye- und Head-Tracking-Eingabegeräten eingeführt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-111">For **Windows 10 April 2018 Update**, we introduced support for Gaze input using eye and head tracking input devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="5f6c4-112">Die Unterstützung für Eye Tracking-Hardware wurde mit dem **Windows10 Fall Creators Update** zusammen mit der [Augensteuerung](https://support.microsoft.com/en-us/help/4043921/windows-10-get-started-eye-control) eingeführt, einem integrierten Feature, mit dem Sie Ihre Augen verwenden können, um den Bildschirmzeiger zu steuern, Text über die Bildschirmtastatur einzugeben und mit Personen über Text-zu-Sprache zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-112">Support for eye tracking hardware was introduced in **Windows 10 Fall Creators Update** along with [Eye control](https://support.microsoft.com/en-us/help/4043921/windows-10-get-started-eye-control), a built-in feature that lets you use your eyes to control the on-screen pointer, type with the on-screen keyboard, and communicate with people using text-to-speech.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-113">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-113">Device support</span></span>

- <span data-ttu-id="5f6c4-114">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-114">Tablet</span></span>
- <span data-ttu-id="5f6c4-115">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-115">PCs and laptops</span></span>

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-116">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-116">Typical usage</span></span>

<span data-ttu-id="5f6c4-117">Verfolgen Sie den Blick, die Aufmerksamkeit und die Präsenz eines Benutzers anhand der Position und Bewegung seiner Augen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-117">Track a user's gaze, attention, and presence based on the location and movement of their eyes.</span></span> <span data-ttu-id="5f6c4-118">Diese leistungsstarke neue Methode zur Verwendung und Interaktion mit Ihren UWP-Apps ist besonders hilfreich als unterstützende Technologie für Benutzer mit neuromuskulären Erkrankungen (wie ALS) und anderen Behinderungen mit beeinträchtigten Muskel- oder Nervenfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-118">This powerful new way to use and interact with your UWP apps is especially useful as an assistive technology for users with neuro-muscular diseases (such as ALS) and other disabilities involving impaired muscle or nerve functions.</span></span> <span data-ttu-id="5f6c4-119">Die Blickeingabe bietet zudem überzeugende Möglichkeiten für Spiele (einschließlich Zielerfassung und -verfolgung) und traditionelle Produktivitätsanwendungen, Kioske und andere interaktive Szenarien, in denen herkömmliche Eingabegeräte (Tastatur, Maus, Touch) nicht verfügbar sind oder in denen es nützlich/hilfreich sein kann, wenn die Hände des Benutzers für andere Aufgaben (z. B. das Halten von Einkaufstaschen) frei bleiben.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-119">Gaze input also provides compelling opportunities for both gaming (including target acquisition and tracking) and traditional productivity applications, kiosks, and other interactive scenarios where traditional input devices (keyboard, mouse, touch) are not available, or where it might be useful/helpful to free up the user's hands for other tasks (such as holding shopping bags).</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-120">More info</span></span>

[<span data-ttu-id="5f6c4-121">Blickinteraktionen und Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="5f6c4-121">Gaze interactions and eye tracking</span></span>](gaze-interactions.md)

## <a name="surface-dial"></a><span data-ttu-id="5f6c4-122">Surface Dial</span><span class="sxs-lookup"><span data-stu-id="5f6c4-122">Surface Dial</span></span>

<span data-ttu-id="5f6c4-123">Mit dem **Windows 10 Anniversary Update** haben wir eine neue Kategorie von Eingabegeräten eingeführt: Windows Wheel.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-123">For **Windows 10 Anniversary Update**, we introduced the Windows Wheel category of input device.</span></span> <span data-ttu-id="5f6c4-124">Surface Dial ist das erste Angebot dieser Art.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-124">The Surface Dial is the first in this class of device.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-125">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-125">Device support</span></span>

- <span data-ttu-id="5f6c4-126">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-126">Tablet</span></span>
- <span data-ttu-id="5f6c4-127">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-127">PCs and laptops</span></span>

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-128">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-128">Typical usage</span></span>

<span data-ttu-id="5f6c4-129">Der Formfaktor von Surface Dial entspricht einer Drehaktion (oder -geste). Surface Dial soll als sekundäres, multimodales Eingabegerät genutzt werden, das Eingaben über ein primäres Gerät ergänzt oder modifiziert.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-129">With a form factor based on a rotate action (or gesture), the Surface Dial is intended as a secondary, multi-modal input device that complements or modifies input from a primary device.</span></span> <span data-ttu-id="5f6c4-130">In den meisten Fällen wird das Gerät von einem Benutzer mit der nicht dominanten Hand bedient, während er mit seiner dominanten Hand eine Aufgabe ausführt (z.B. Freihandzeichnen mit einem Stift).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-130">In most cases, the device is manipulated by a user's non-dominant hand while they perform a task with their dominant hand (such as inking with a pen).</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-131">More info</span></span>

[<span data-ttu-id="5f6c4-132">Surface Dial-Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5f6c4-132">Surface Dial design guidelines</span></span>](windows-wheel-interactions.md)

## <a name="cortana"></a><span data-ttu-id="5f6c4-133">Cortana</span><span class="sxs-lookup"><span data-stu-id="5f6c4-133">Cortana</span></span>

<span data-ttu-id="5f6c4-134">In Windows 10 können Sie **die Cortana** -Erweiterbarkeit Sprachbefehle von einem Benutzer behandeln und die Anwendung auf eine einzelne Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-134">In Windows10, **Cortana** extensibility lets you handle voice commands from a user and launch your application to carry out a single action.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-135">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-135">Device support</span></span>

-   <span data-ttu-id="5f6c4-136">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-136">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-137">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-137">Tablet</span></span>
-   <span data-ttu-id="5f6c4-138">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-138">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-139">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-139">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-140">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-140">IoT</span></span>
-   <span data-ttu-id="5f6c4-141">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-141">Xbox</span></span>
-   <span data-ttu-id="5f6c4-142">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5f6c4-142">HoloLens</span></span>

![Cortana](images/input-interactions/icons-cortana01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-144">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-144">Typical usage</span></span>

<span data-ttu-id="5f6c4-145">Ein Sprachbefehl ist eine einzelne, in einer Sprachbefehldefinitions-Datei (VCD-Datei) definierte Äußerung, die über **Cortana** an eine installierte App weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-145">A voice command is a single utterance, defined in a Voice Command Definition (VCD) file, directed at an installed app through **Cortana**.</span></span> <span data-ttu-id="5f6c4-146">Die App kann im Vordergrund oder im Hintergrund gestartet werden, je nach Ebene und Komplexität der Interaktion.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-146">The app can be launched in the foreground or background, depending on the level and complexity of the interaction.</span></span> <span data-ttu-id="5f6c4-147">Sprachbefehle, die zusätzlichen Kontext oder Benutzereingaben erfordern, werden beispielsweise am besten im Vordergrund ausgeführt, während grundlegende Befehle im Hintergrund behandelt werden können.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-147">For instance, voice commands that require additional context or user input are best handled in the foreground, while basic commands can be handled in the background.</span></span>

<span data-ttu-id="5f6c4-148">**Cortana** integriert die grundlegenden Funktionen Ihrer App, bietet einen zentralen Einstiegspunkt, über den der Benutzer die meisten Aufgaben ohne Öffnen der App ausführen kann, und wird somit zum Bindeglied zwischen Ihrer App und dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-148">Integrating the basic functionality of your app, and providing a central entry point for the user to accomplish most of the tasks without opening your app directly, lets **Cortana** become a liaison between your app and the user.</span></span> <span data-ttu-id="5f6c4-149">In vielen Fällen spart der Benutzer dadurch viel Zeit und Mühe.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-149">In many cases, this can save the user significant time and effort.</span></span> <span data-ttu-id="5f6c4-150">Weitere Informationen finden Sie unter [Cortana-Entwurfsrichtlinien](https://msdn.microsoft.com/library/windows/apps/dn974233).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-150">For more info, see [Cortana design guidelines](https://msdn.microsoft.com/library/windows/apps/dn974233).</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-151">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-151">More info</span></span>

[<span data-ttu-id="5f6c4-152">Cortana-Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5f6c4-152">Cortana design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn974233)
 

## <a name="speech"></a><span data-ttu-id="5f6c4-153">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-153">Speech</span></span>

<span data-ttu-id="5f6c4-154">Die Spracherkennung ist eine effektive und natürliche Möglichkeit, mit Apps zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-154">Speech is an effective and natural way for people to interact with applications.</span></span> <span data-ttu-id="5f6c4-155">Sie bietet eine unkomplizierte und präzise Möglichkeit der Kommunikation mit Apps; damit können Benutzer in einer Vielzahl von Situationen produktiv arbeiten und auf dem Laufenden bleiben.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-155">It's an easy and accurate way to communicate with applications, and lets people be productive and stay informed in a variety of situations.</span></span>

<span data-ttu-id="5f6c4-156">Die Spracherkennung kann den Haupteingabetyp je nach Gerät in vielen Fällen ergänzen oder sogar an dessen Stelle treten.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-156">Speech can complement or, in many cases, be the primary input type, depending on the user's device.</span></span> <span data-ttu-id="5f6c4-157">Beispielsweise unterstützen Geräte wie HoloLens und Xbox keine herkömmlichen Eingabetypen (abgesehen von einer Softwaretastatur in bestimmten Szenarien).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-157">For example, devices such as HoloLens and Xbox do not support traditional input types (aside from a software keyboard in specific scenarios).</span></span> <span data-ttu-id="5f6c4-158">Stattdessen verwenden sie für die meisten Benutzerinteraktionen Spracheingabe und -ausgabe (häufig zusammen mit anderen modernen Eingabetypen wie Gestik und Mimik).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-158">Instead, they rely on speech input and output (often combined with other non-traditional input types such as gaze and gesture) for most user interactions.</span></span>

<span data-ttu-id="5f6c4-159">Mit Text-zu-Sprache (auch als TTS oder Sprachsynthese bezeichnet) werden Informationen oder Anweisungen an den Benutzer ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-159">Text-to-speech (also known as TTS, or speech synthesis) is used to inform or direct the user.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-160">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-160">Device support</span></span>

-   <span data-ttu-id="5f6c4-161">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-161">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-162">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-162">Tablet</span></span>
-   <span data-ttu-id="5f6c4-163">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-163">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-164">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-164">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-165">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-165">IoT</span></span>
-   <span data-ttu-id="5f6c4-166">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-166">Xbox</span></span>
-   <span data-ttu-id="5f6c4-167">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5f6c4-167">HoloLens</span></span>

![Spracherkennung](images/input-interactions/icons-speech01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-169">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-169">Typical usage</span></span>

<span data-ttu-id="5f6c4-170">Es gibt drei Modi der Sprachinteraktion:</span><span class="sxs-lookup"><span data-stu-id="5f6c4-170">There are three modes of Speech interaction:</span></span>

**<span data-ttu-id="5f6c4-171">Natürliche Sprache</span><span class="sxs-lookup"><span data-stu-id="5f6c4-171">Natural language</span></span>**

<span data-ttu-id="5f6c4-172">Mit natürlicher Sprache kommunizieren wir laufend mündlich mit anderen Personen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-172">Natural language is how we verbally interact with people on a regular basis.</span></span> <span data-ttu-id="5f6c4-173">Unsere Sprache variiert in Abhängigkeit von der jeweiligen Person oder Situation, sie wird jedoch generell verstanden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-173">Our speech varies from person to person and situation to situation, and is generally understood.</span></span> <span data-ttu-id="5f6c4-174">Wenn dies nicht der Fall ist, verwenden wir häufig andere Wörter oder eine abweichende Wortreihenfolge, um die gleichen Gedanken zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-174">When it's not, we often use different words and word order to get the same idea across.</span></span>

<span data-ttu-id="5f6c4-175">Die Kommunikation über natürliche Sprache mit einer App verläuft ähnlich: Wir sprechen über unser Gerät mit der App wie mit einer Person und erwarten, dass sie uns versteht und entsprechend reagiert.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-175">Natural language interactions with an app are similar: we speak to the app through our device as if it were a person and expect it to understand and react accordingly.</span></span>

<span data-ttu-id="5f6c4-176">Die natürliche Sprache ist der fortgeschrittenste Modus der Sprachinteraktion, der über **Cortana** implementiert und verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-176">Natural language is the most advanced mode of speech interaction, and can be implemented and exposed through **Cortana**.</span></span>

**<span data-ttu-id="5f6c4-177">Befehl und Steuerung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-177">Command and control</span></span>**

<span data-ttu-id="5f6c4-178">Unter Befehl und Steuerung wird die Verwendung von Sprachbefehlen zum Aktivieren von Steuerelementen und Funktionen verstanden, z. B. zum Klicken auf eine Schaltfläche oder zum Auswählen eines Menüelements.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-178">Command and control is the use of verbal commands to activate controls and functionality such as clicking a button or selecting a menu item.</span></span>

<span data-ttu-id="5f6c4-179">Da Befehl und Steuerung entscheidend für eine erfolgreiche Benutzeroberfläche ist, wird ein einzelner Eingabetyp im Allgemeinen nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-179">As command and control is critical to a successful user experience, a single input type is generally not recommended.</span></span> <span data-ttu-id="5f6c4-180">Die Spracherkennung ist in der Regel eine von mehreren Eingabeoptionen für einen Benutzer, die von seinen Vorlieben und Hardwarefunktionen abhängen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-180">Speech is typically one of several input options for a user based on their preferences or hardware capabilities.</span></span>

**<span data-ttu-id="5f6c4-181">Diktieren</span><span class="sxs-lookup"><span data-stu-id="5f6c4-181">Dictation</span></span>**

<span data-ttu-id="5f6c4-182">Die einfachste Methode der Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-182">The most basic speech input method.</span></span> <span data-ttu-id="5f6c4-183">Jede Äußerung wird in Text umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-183">Each utterance is converted to text.</span></span>

<span data-ttu-id="5f6c4-184">Das Diktieren wird in der Regel verwendet, wenn eine App die Bedeutung oder die Absicht nicht verstehen muss.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-184">Dictation is typically used when an app doesn’t need to understand meaning or intent.</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-185">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-185">More info</span></span>

[<span data-ttu-id="5f6c4-186">Richtlinien für den Sprachentwurf</span><span class="sxs-lookup"><span data-stu-id="5f6c4-186">Speech design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596121)
 

## <a name="pen"></a><span data-ttu-id="5f6c4-187">Stift</span><span class="sxs-lookup"><span data-stu-id="5f6c4-187">Pen</span></span>

<span data-ttu-id="5f6c4-188">Ein (Eingabe-)Stift kann ähnlich wie eine Maus als pixelgenaues Zeigegerät verwendet werden, und er eignet sich optimal für die Freihandeingabe.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-188">A pen (or stylus) can serve as a pixel precise pointing device, like a mouse, and is the optimal device for digital ink input.</span></span>

<span data-ttu-id="5f6c4-189">**Hinweis:** es gibt zwei Arten von Stiften: aktive und passive.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-189">**Note**There are two types of pen devices: active and passive.</span></span>
  -   <span data-ttu-id="5f6c4-190">Passive Stifte enthalten keine Elektronik, und sie emulieren effektiv die Toucheingabe über einen Finger.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-190">Passive pens do not contain electronics, and effectively emulate touch input from a finger.</span></span> <span data-ttu-id="5f6c4-191">Sie benötigen eine Basisgerätanzeige, welche die Eingabe basierend auf dem Berührungsdruck erkennt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-191">They require a basic device display that recognizes input based on contact pressure.</span></span> <span data-ttu-id="5f6c4-192">Da Benutzer beim Schreiben auf der Eingabeoberfläche häufig die Hand ablegen, können Eingabedaten wegen des nicht erfolgreichen Ablehnens der Handfläche verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-192">Because users often rest their hand as they write on the input surface, input data can become polluted due to unsuccessful palm rejection.</span></span>
  -   <span data-ttu-id="5f6c4-193">Aktive Stifte enthalten Elektronik und können mit komplexen Gerätedisplays zusammenwirken und viel umfassendere Eingabedaten (u.a. Daten bei Daraufzeigen oder Näherung) für das System und die App liefern.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-193">Active pens contain electronics and can work with complex device displays to provide much more extensive input data (including hover, or proximity data) to the system and your app.</span></span> <span data-ttu-id="5f6c4-194">Die Handflächenablehnung ist sehr viel robuster.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-194">Palm rejection is much more robust.</span></span>

<span data-ttu-id="5f6c4-195">In diesem Text beziehen wir uns auf aktive Stifte, die umfangreiche Eingabedaten liefern und in erster Linie für präzise Freihandeingaben und für zeigebasierte Interaktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-195">When we refer to pen devices here, we are referring to active pens that provide rich input data and are used primarily for precise ink and pointing interactions.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-196">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-196">Device support</span></span>

-   <span data-ttu-id="5f6c4-197">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-197">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-198">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-198">Tablet</span></span>
-   <span data-ttu-id="5f6c4-199">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-199">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-200">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-200">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-201">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-201">IoT</span></span>

![Stift](images/input-interactions/icons-pen01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-203">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-203">Typical usage</span></span>

<span data-ttu-id="5f6c4-204">In Kombination mit einem Stift ermöglicht die Windows-Freihandplattform die natürliche Erstellung von handschriftlichen Notizen, Zeichnungen und Anmerkungen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-204">The Windows ink platform, together with a pen, provides a natural way to create handwritten notes, drawings, and annotations.</span></span> <span data-ttu-id="5f6c4-205">Die Plattform unterstützt das Erfassen von Freihanddaten aus einem Eingabedigitalisierungsgerät, das Generieren von Freihanddaten, das Ausgeben von Daten und das Rendern von Freihandstrichen auf dem Ausgabegerät sowie das Verwalten von Daten und das Ausführen einer Schrifterkennung.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-205">The platform supports capturing ink data from digitizer input, generating ink data, rendering that data as ink strokes on the output device, managing the ink data, and performing handwriting recognition.</span></span> <span data-ttu-id="5f6c4-206">Ihre App kann nicht nur die räumlichen Bewegungen des Stifts beim Schreiben oder Zeichnen erfassen. Sie kann auch Informationen zu Druck, Form, Farbe und Deckkraft sammeln und ermöglicht so eine Arbeitsweise, die der Verwendung eines Stifts, Bleistifts oder Pinsels auf Papier schon sehr nahe kommt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-206">In addition to capturing the spatial movements of the pen as the user writes or draws, your app can also collect info such as pressure, shape, color, and opacity, to offer user experiences that closely resemble drawing on paper with a pen, pencil, or brush.</span></span>

<span data-ttu-id="5f6c4-207">Die Stift- und die Toucheingabe unterscheiden sich dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (wie Wischen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-207">Where pen and touch input diverge is the ability for touch to emulate direct manipulation of UI elements on the screen through physical gestures performed on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span>

<span data-ttu-id="5f6c4-208">Sie müssen stiftspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-208">You should provide pen-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="5f6c4-209">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-209">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-210">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-210">More info</span></span>

[<span data-ttu-id="5f6c4-211">Zeichenstift-Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5f6c4-211">Pen design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456352)
 

## <a name="touch"></a><span data-ttu-id="5f6c4-212">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="5f6c4-212">Touch</span></span>

<span data-ttu-id="5f6c4-213">Bei der Toucheingabe können mit einem oder mehreren Fingern ausgeführte Gesten verwendet werden, um die direkte Manipulation von UI-Elementen (wie etwa Verschieben, Drehen, Ändern der Größe oder Bewegen) zu emulieren. Außerdem können die Gesten auch als alternative Eingabemethode (ähnlich einer Maus- oder Stifteingabe) oder als ergänzende Eingabemethode (zum Modifizieren anderer Eingaben; also beispielsweise zum Verwischen eines mit einem Stift gezeichneten Freihandstrichs) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-213">With touch, physical gestures from one or more fingers can be used to either emulate the direct manipulation of UI elements (such as panning, rotating, resizing, or moving), as an alternative input method (similar to mouse or pen), or as a complementary input method (to modify aspects of other input, such as smudging an ink stroke drawn with a pen).</span></span> <span data-ttu-id="5f6c4-214">Diese berührungsbasierte Bedienung wird von Benutzern unter Umständen als natürlicher wahrgenommen als die symbolbasierte Interaktion auf einem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-214">Tactile experiences such as this can provide more natural, real-world sensations for users as they interact with elements on a screen.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-215">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-215">Device support</span></span>

-   <span data-ttu-id="5f6c4-216">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-216">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-217">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-217">Tablet</span></span>
-   <span data-ttu-id="5f6c4-218">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-218">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-219">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-219">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-220">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-220">IoT</span></span>

![Toucheingabe](images/input-interactions/icons-touch01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-222">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-222">Typical usage</span></span>

<span data-ttu-id="5f6c4-223">Die Unterstützung für die Toucheingabe kann je nach Gerät stark variieren.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-223">Support for touch input can vary significantly, depending on the device.</span></span>

<span data-ttu-id="5f6c4-224">Einige Geräte unterstützen keinerlei Toucheingabe, einige unterstützen einen einzelnen Touchkontakt, während wiederum andere Multitouchinteraktionen (zwei oder mehr Kontakte) unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-224">Some devices don't support touch at all, some devices support a single touch contact, while others support multi-touch (two or more contacts).</span></span>

<span data-ttu-id="5f6c4-225">Die meisten Geräte mit Unterstützung von Multitouchinteraktionen erkennen zehn eindeutige gleichzeitige Kontakte.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-225">Most devices that support multi-touch input, typically recognize ten unique, concurrent contacts.</span></span>

<span data-ttu-id="5f6c4-226">Surface Hub-Geräte erkennen 100 eindeutige, gleichzeitige Berührungskontakte.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-226">Surface Hub devices recognize 100 unique, concurrent touch contacts.</span></span>

<span data-ttu-id="5f6c4-227">Im Allgemeinen weist die Toucheingabe folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="5f6c4-227">In general, touch is:</span></span>

-   <span data-ttu-id="5f6c4-228">Einzelner Benutzer, es sei denn, sie kommt mit einem Microsoft-Team-Gerät wie Surface-Hub zur Anwendung, bei dem der Schwerpunkt auf der Zusammenarbeit liegt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-228">Single user, unless being used with a Microsoft Team device like Surface Hub, where collaboration is emphasized.</span></span>
-   <span data-ttu-id="5f6c4-229">Keine Beschränkung hinsichtlich der Geräteausrichtung.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-229">Not constrained to device orientation.</span></span>
-   <span data-ttu-id="5f6c4-230">Wird für alle Interaktionen, u.a. Texteingabe (Bildschirmtastatur) und Freihandeingabe (für die App konfiguriert) verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-230">Used for all interactions, including text input (touch keyboard) and inking (app-configured).</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-231">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-231">More info</span></span>

[<span data-ttu-id="5f6c4-232">Richtlinien für die Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="5f6c4-232">Touch design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465370)
 

## <a name="touchpad"></a><span data-ttu-id="5f6c4-233">Touchpad</span><span class="sxs-lookup"><span data-stu-id="5f6c4-233">Touchpad</span></span>

<span data-ttu-id="5f6c4-234">Ein Touchpad vereint die indirekte Multitoucheingabe mit der Präzisionseingabe eines Zeigergeräts (beispielsweise eine Maus).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-234">A touchpad combines both indirect multi-touch input with the precision input of a pointing device, such as a mouse.</span></span> <span data-ttu-id="5f6c4-235">Durch diese Kombination ist das Touchpad sowohl für eine toucheingabeoptimierte Benutzeroberfläche als auch für die kleineren Ziele von Produktivitäts-Apps geeignet.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-235">This combination makes the touchpad suited to both a touch-optimized UI and the smaller targets of productivity apps.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-236">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-236">Device support</span></span>

-   <span data-ttu-id="5f6c4-237">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-237">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-238">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-238">IoT</span></span>

![Touchpad](images/input-interactions/icons-touchpad01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-240">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-240">Typical usage</span></span>

<span data-ttu-id="5f6c4-241">Touchpads unterstützen in der Regel eine Reihe von Touchgesten, die für die direkte Manipulation von Objekten und Benutzeroberflächenelementen eine ähnliche Unterstützung bieten wie die Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-241">Touchpads typically support a set of touch gestures that provide support similar to touch for direct manipulation of objects and UI.</span></span>

<span data-ttu-id="5f6c4-242">Aufgrund dieser Konvergenz bei der von Touchpads unterstützten Interaktion empfiehlt es sich, sich nicht allein auf die Unterstützung der Toucheingabe zu verlassen, sondern auch Benutzeroberflächenbefehle oder Angebote für die Mauseingabe bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-242">Because of this convergence of interaction experiences supported by touchpads, we recommend also providing mouse-style UI commands or affordances rather than relying solely on support for touch input.</span></span> <span data-ttu-id="5f6c4-243">Stellen Sie Touchpad-spezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-243">Provide touchpad-specific UI commands, or affordances, to support these interactions.</span></span>

<span data-ttu-id="5f6c4-244">Sie müssen mausspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-244">You should provide mouse-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="5f6c4-245">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-245">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-246">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-246">More info</span></span>

[<span data-ttu-id="5f6c4-247">Touchpad-Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5f6c4-247">Touchpad design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456353)
 

## <a name="keyboard"></a><span data-ttu-id="5f6c4-248">Tastatur</span><span class="sxs-lookup"><span data-stu-id="5f6c4-248">Keyboard</span></span>

<span data-ttu-id="5f6c4-249">Eine Tastatur ist das Haupteingabegerät für Text und häufig unentbehrlich für Personen mit bestimmten körperlichen Beeinträchtigungen oder für Benutzer, die die Tastatur als schnellere und effizientere Interaktionsmethode betrachten.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-249">A keyboard is the primary input device for text, and is often indispensable to people with certain disabilities or users who consider it a faster and more efficient way to interact with an app.</span></span>

<span data-ttu-id="5f6c4-250">Mit [Continuum für Smartphones](http://go.microsoft.com/fwlink/p/?LinkID=699431), einer neuen Funktion für kompatible Windows 10 mobile Geräte, können Benutzer ihre Smartphones mit einer Maus und Tastatur, damit ihr Gerät wie einen Laptop verbinden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-250">With [Continuum for Phone](http://go.microsoft.com/fwlink/p/?LinkID=699431), a new experience for compatible Windows10 mobile devices, users can connect their phones to a mouse and keyboard to make their phones work like a laptop.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-251">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-251">Device support</span></span>

-   <span data-ttu-id="5f6c4-252">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-252">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-253">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-253">Tablet</span></span>
-   <span data-ttu-id="5f6c4-254">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-254">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-255">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-255">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-256">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-256">IoT</span></span>
-   <span data-ttu-id="5f6c4-257">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-257">Xbox</span></span>
-   <span data-ttu-id="5f6c4-258">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5f6c4-258">HoloLens</span></span>

![Tastatur](images/input-interactions/icons-keyboard01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-260">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-260">Typical usage</span></span>

<span data-ttu-id="5f6c4-261">Benutzer können mit Universellen Windows-Apps über eine Hardwaretastatur und zwei Softwaretastaturen (Bildschirmtastatur oder Touchtastatur) interagieren.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-261">Users can interact with Universal Windows apps through a hardware keyboard and two software keyboards: the On-Screen Keyboard (OSK) and the touch keyboard.</span></span>

<span data-ttu-id="5f6c4-262">Bei der Bildschirmtastatur handelt es sich um eine visuelle Softwaretastatur, die Sie anstelle der physischen Tastatur zum Eingeben von Daten per Touch, Maus, (Eingabe-)Stift oder anderen Zeigegeräten verwenden können. Ein Touchscreen ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-262">The OSK is a visual, software keyboard that you can use instead of the physical keyboard to type and enter data using touch, mouse, pen/stylus or other pointing device (a touch screen is not required).</span></span> <span data-ttu-id="5f6c4-263">Die Bildschirmtastatur ist für Systeme ohne physische Tastatur oder für Benutzer vorgesehen, deren Mobilitätseinschränkungen die Verwendung herkömmlicher physischer Eingabegeräte verhindern.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-263">The OSK is provided for systems that don't have a physical keyboard, or for users whose mobility impairments prevent them from using traditional physical input devices.</span></span> <span data-ttu-id="5f6c4-264">Die Bildschirmtastatur emuliert nahezu alle Funktionen der Hardwaretastatur.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-264">The OSK emulates most, if not all, the functionality of a hardware keyboard.</span></span>

<span data-ttu-id="5f6c4-265">Bei der Bildschirmtastatur handelt es sich um eine visuelle Softwaretastatur für die Texteingabe per Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-265">The touch keyboard is a visual, software keyboard used for text entry with touch input.</span></span> <span data-ttu-id="5f6c4-266">Die Touchtastatur ist kein Ersatz für die Bildschirmtastatur. Sie wird nur für die Texteingabe (ohne Emulierung der Hardwaretastatur) verwendet und nur angezeigt, wenn der Fokus auf einem Textfeld oder einem anderen bearbeitbaren Textsteuerelement liegt.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-266">The touch keyboard is not a replacement for the OSK as it is used for text input only (it doesn't emulate the hardware keyboard) and appears only when a text field or other editable text control gets focus.</span></span> <span data-ttu-id="5f6c4-267">Die Bildschirmtastatur unterstützt keine App- oder Systembefehle.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-267">The touch keyboard does not support app or system commands.</span></span>

<span data-ttu-id="5f6c4-268">**Hinweis:** die Bildschirmtastatur hat Priorität gegenüber der Touch-Bildschirmtastatur, die nicht angezeigt, wenn die Bildschirmtastatur vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-268">**Note**The OSK has priority over the touch keyboard, which won't be shown if the OSK is present.</span></span>

<span data-ttu-id="5f6c4-269">Im Allgemeinen weist eine Tastatur folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="5f6c4-269">In general, a keyboard is:</span></span>

-   <span data-ttu-id="5f6c4-270">Einzelner Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-270">Single user.</span></span>
-   <span data-ttu-id="5f6c4-271">Keine Beschränkung hinsichtlich der Geräteausrichtung.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-271">Not constrained to device orientation.</span></span>
-   <span data-ttu-id="5f6c4-272">Wird für Texteingabe, Navigation, Spiele und Eingabehilfen verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-272">Used for text input, navigation, gameplay, and accessibility.</span></span>
-   <span data-ttu-id="5f6c4-273">Immer verfügbar, entweder proaktiv oder reaktiv.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-273">Always available, either proactively or reactively.</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-274">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-274">More info</span></span>

[<span data-ttu-id="5f6c4-275">Tastaturentwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="5f6c4-275">Keyboard design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/hh972345)
 

## <a name="mouse"></a><span data-ttu-id="5f6c4-276">Maus</span><span class="sxs-lookup"><span data-stu-id="5f6c4-276">Mouse</span></span>

<span data-ttu-id="5f6c4-277">Eine Maus eignet sich am besten für Produktivitäts-Apps und Benutzeroberflächen mit hoher Dichte, bei denen Benutzerinteraktionen beim Zielen und bei der Befehlseingabe Pixelgenauigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-277">A mouse is best suited for productivity apps and high-density UI where user interactions require pixel-level precision for targeting and commanding.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-278">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-278">Device support</span></span>

-   <span data-ttu-id="5f6c4-279">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-279">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-280">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-280">Tablet</span></span>
-   <span data-ttu-id="5f6c4-281">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-281">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-282">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-282">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-283">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-283">IoT</span></span>

![Maus](images/input-interactions/icons-mouse01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-285">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-285">Typical usage</span></span>

<span data-ttu-id="5f6c4-286">Die Mauseingabe kann über verschiedene Tasten der Tastatur (STRG, UMSCHALTTASTE, ALT usw.) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-286">Mouse input can be modified with the addition of various keyboard keys (Ctrl, Shift, Alt, and so on).</span></span> <span data-ttu-id="5f6c4-287">Diese Tasten können mit der linken Maustaste, der rechten Maustaste, der Radtaste und den X-Tasten zu einem erweiterten, mausoptimierten Befehlssatz kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-287">These keys can be combined with the left mouse button, the right mouse button, the wheel button, and the X buttons for an expanded mouse-optimized command set.</span></span> <span data-ttu-id="5f6c4-288">(Einige Microsoft-Mausgeräte verfügen über zwei weitere Schaltflächen, die als X-Tasten bezeichnet werden. Diese dienen gewöhnlich dazu, in Webbrowsern zurück und vorwärts zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-288">(Some Microsoft mouse devices have two additional buttons, referred to as X buttons, typically used to navigate back and forward in Web browsers).</span></span>

<span data-ttu-id="5f6c4-289">Ähnlich wie bei der Stifteingabe unterscheiden sich Maus- und Toucheingabe dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (z.B. Wischen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-289">Similar to pen, where mouse and touch input diverge is the ability for touch to emulate direct manipulation of UI elements on the screen through physical gestures performed on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span>

<span data-ttu-id="5f6c4-290">Sie müssen mausspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-290">You should provide mouse-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="5f6c4-291">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-291">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="5f6c4-292">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f6c4-292">More info</span></span>

[<span data-ttu-id="5f6c4-293">Richtlinien für die Mausinteraktion</span><span class="sxs-lookup"><span data-stu-id="5f6c4-293">Mouse design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456351)
 

## <a name="gesture"></a><span data-ttu-id="5f6c4-294">Geste</span><span class="sxs-lookup"><span data-stu-id="5f6c4-294">Gesture</span></span>

<span data-ttu-id="5f6c4-295">Eine Geste ist jede Art von Benutzerbewegung, die als Steuerungs- oder Interaktionseingabe für eine Anwendung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-295">A gesture is any form of user movement that is recognized as input for controlling or interacting with an application.</span></span> <span data-ttu-id="5f6c4-296">Es gibt verschiedene Arten von Gesten – von der einfachen Geste, die dazu dient, mit der Hand etwas auf dem Bildschirm zu verwenden, über spezifische, erlernte Bewegungsmuster bis hin zu langen Bewegungsabläufen des gesamten Körpers.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-296">Gestures take many forms, from simply using a hand to target something on the screen, to specific, learned patterns of movement, to long stretches of continuous movement using the entire body.</span></span> <span data-ttu-id="5f6c4-297">Beachten Sie beim Entwerfen benutzerdefinierter Gesten, dass diese in anderen Regionen/Kulturkreisen unter Umständen eine andere Bedeutung haben.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-297">Be careful when designing custom gestures, as their meaning can vary depending on locale and culture.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-298">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-298">Device support</span></span>

-   <span data-ttu-id="5f6c4-299">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-299">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-300">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-300">IoT</span></span>
-   <span data-ttu-id="5f6c4-301">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-301">Xbox</span></span>
-   <span data-ttu-id="5f6c4-302">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5f6c4-302">HoloLens</span></span>

![Geste](images/input-interactions/icons-gesture01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-304">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-304">Typical usage</span></span>

<span data-ttu-id="5f6c4-305">Statische Gestenereignisse werden ausgelöst, wenn eine Interaktion abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-305">Static gesture events are fired after an interaction is complete.</span></span>

- <span data-ttu-id="5f6c4-306">Zu den statischen Gestenereignissen zählen Tapped, DoubleTapped, RightTapped und Holding.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-306">Static gesture events include Tapped, DoubleTapped, RightTapped, and Holding.</span></span>

<span data-ttu-id="5f6c4-307">Manipulationsgestenereignisse weisen auf eine andauernde Interaktion hin.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-307">Manipulation gesture events indicate an ongoing interaction.</span></span> <span data-ttu-id="5f6c4-308">Sie werden ausgelöst, wenn der Benutzer ein Element berührt, und bleiben so lange aktiv, bis der Benutzer den bzw. die Finger vom Element hebt oder die Manipulation abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-308">They start firing when the user touches an element and continue until the user lifts their finger(s), or the manipulation is canceled.</span></span>

- <span data-ttu-id="5f6c4-309">Manipulationsereignisse umfassen Multi-Touch-Interaktionen wie Zoomen, Schwenken und Drehen sowie Interaktionen, die Trägheits- und Geschwindigkeitsdaten nutzen (z.B. Ziehen).</span><span class="sxs-lookup"><span data-stu-id="5f6c4-309">Manipulation events include multi-touch interactions such as zooming, panning, or rotating, and interactions that use inertia and velocity data such as dragging.</span></span> <span data-ttu-id="5f6c4-310">(Die von den Manipulationsereignissen bereitgestellten Informationen identifizieren nicht die Interaktion, sondern stellen Daten wie Position, Übersetzungsdelta und Geschwindigkeit bereit.)</span><span class="sxs-lookup"><span data-stu-id="5f6c4-310">(The information provided by the manipulation events doesn't identify the interaction, but rather provides data such as position, translation delta, and velocity.)</span></span>

- <span data-ttu-id="5f6c4-311">Zeigerereignisse wie PointerPressed und PointerMoved bieten Details auf unterer Ebene für alle Touchkontakte einschließlich Zeigerbewegungen und die Möglichkeit, zwischen Drück- und Freigabeereignissen zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-311">Pointer events such as PointerPressed and PointerMoved provide low-level details for each touch contact, including pointer motion and the ability to distinguish press and release events.</span></span>

<span data-ttu-id="5f6c4-312">Aufgrund der Konvergenz von durch Windows unterstützten Interaktionsumgebungen wird empfohlen, sich nicht nur auf die Unterstützung für Toucheingaben zu verlassen, sondern auch Benutzeroberflächenbefehle oder Angebote für Mauseingaben bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-312">Because of the convergence of interaction experiences supported by Windows, we recommend also providing mouse-style UI commands or affordances rather than relying solely on support for touch input.</span></span> <span data-ttu-id="5f6c4-313">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-313">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>


## <a name="gamepadcontroller"></a><span data-ttu-id="5f6c4-314">Gamepad/Controller</span><span class="sxs-lookup"><span data-stu-id="5f6c4-314">Gamepad/Controller</span></span>

<span data-ttu-id="5f6c4-315">Ein Gamepad/Controller ist ein sehr spezielles Gerät und kommt in der Regel bei Spielen zum Einsatz.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-315">The gamepad/controller is a highly specialized device typically dedicated to playing games.</span></span> <span data-ttu-id="5f6c4-316">Es wird jedoch auch zum Emulieren einfacher Tastatureingaben sowie für eine tastaturähnliche UI-Navigation verwendet.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-316">However, it is also used for to emulate basic keyboard input and provides a UI navigation experience very similar to the keyboard.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-317">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-317">Device support</span></span>

-   <span data-ttu-id="5f6c4-318">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-318">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-319">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-319">IoT</span></span>
-   <span data-ttu-id="5f6c4-320">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-320">Xbox</span></span>

![Controller](images/input-interactions/icons-controller01.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-322">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-322">Typical usage</span></span>

<span data-ttu-id="5f6c4-323">Spielen und Interaktionen mit einer speziellen Konsole.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-323">Playing games and interacting with a specialized console.</span></span>


## <a name="multiple-inputs"></a><span data-ttu-id="5f6c4-324">Mehrfacheingaben</span><span class="sxs-lookup"><span data-stu-id="5f6c4-324">Multiple inputs</span></span>

<span data-ttu-id="5f6c4-325">Durch die Berücksichtigung so vieler Benutzer und Geräte wie möglich und den Entwurf Ihrer App für die Kompatibilität mit möglichst vielen Eingabearten (Gesten, Spracherkennung, Toucheingabe, Touchpad, Maus und Tastatur) maximieren Sie die Flexibilität, Benutzerfreundlichkeit und Barrierefreiheit Ihrer Apps.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-325">Accommodating as many users and devices as possible and designing your apps to work with as many input types (gesture, speech, touch, touchpad, mouse, and keyboard) as possible maximizes flexibility, usability, and accessibility.</span></span>

### <a name="device-support"></a><span data-ttu-id="5f6c4-326">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5f6c4-326">Device support</span></span>

-   <span data-ttu-id="5f6c4-327">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="5f6c4-327">Phones and phablets</span></span>
-   <span data-ttu-id="5f6c4-328">Tablet</span><span class="sxs-lookup"><span data-stu-id="5f6c4-328">Tablet</span></span>
-   <span data-ttu-id="5f6c4-329">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="5f6c4-329">PCs and laptops</span></span>
-   <span data-ttu-id="5f6c4-330">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5f6c4-330">Surface Hub</span></span>
-   <span data-ttu-id="5f6c4-331">IoT</span><span class="sxs-lookup"><span data-stu-id="5f6c4-331">IoT</span></span>
-   <span data-ttu-id="5f6c4-332">Xbox</span><span class="sxs-lookup"><span data-stu-id="5f6c4-332">Xbox</span></span>
-   <span data-ttu-id="5f6c4-333">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5f6c4-333">HoloLens</span></span>

![Mehrfacheingaben](images/input-interactions/icons-inputdevices03-vertical.png)

### <a name="typical-usage"></a><span data-ttu-id="5f6c4-335">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="5f6c4-335">Typical usage</span></span>

<span data-ttu-id="5f6c4-336">Personen kommunizieren untereinander mit einer Mischung aus Sprache und Gesten, und auch bei der Interaktion mit einer App kann sich die Verwendung mehrerer Eingabearten und -modi als hilfreich erweisen.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-336">Just as people use a combination of voice and gesture when communicating with each other, multiple types and modes of input can also be useful when interacting with an app.</span></span> <span data-ttu-id="5f6c4-337">Diese kombinierten Interaktionen müssen jedoch möglichst intuitiv und natürlich gestaltet sein, da sie andernfalls zu Verwirrung führen können.</span><span class="sxs-lookup"><span data-stu-id="5f6c4-337">However, these combined interactions need to be as intuitive and natural as possible as they can also create a very confusing experience.</span></span>





 

 
