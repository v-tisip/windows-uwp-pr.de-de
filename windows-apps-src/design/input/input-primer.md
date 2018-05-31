---
author: Karl-Bridge-Microsoft
Description: User interactions in the Universal Windows Platform (UWP) are a combination of input and output sources (such as mouse, keyboard, pen, touch, touchpad, speech, Cortana, controller, gesture, gaze, and so on), along with various modes or modifiers that enable extended experiences (including mouse wheel and buttons, pen eraser and barrel buttons, touch keyboard, and background app services).
title: Einführung in die Interaktion
ms.assetid: 73008F80-FE62-457D-BAEC-412ED6BAB0C8
label: Interaction primer
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 910920c1f5eb5bdc3e55b51d7886be1632559c14
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
ms.locfileid: "1396609"
---
# <a name="interaction-primer"></a><span data-ttu-id="93620-103">Einführung in die Interaktion</span><span class="sxs-lookup"><span data-stu-id="93620-103">Interaction primer</span></span>


![Windows-Eingabetypen](images/input-interactions/icons-inputdevices03.png)

<span data-ttu-id="93620-105">Benutzerinteraktionen in der Universellen Windows-Plattform (UWP) stellen eine Kombination von Eingabe- und Ausgabequellen dar (z. B. Maus, Tastatur, Stift, Toucheingabe, Touchpad, Spracherkennung, **Cortana**, Controller, Gesten, Mimik usw.), neben verschiedenen Modi oder Modifizierern, die erweiterte Funktionen ermöglichen (u. a. Mausrad und -tasten, Radierer- und Zeichenstift-Schaltflächen, Bildschirmtastatur sowie App-Dienste im Hintergrund).</span><span class="sxs-lookup"><span data-stu-id="93620-105">User interactions in the Universal Windows Platform (UWP) are a combination of input and output sources (such as mouse, keyboard, pen, touch, touchpad, speech, **Cortana**, controller, gesture, gaze, and so on), along with various modes or modifiers that enable extended experiences (including mouse wheel and buttons, pen eraser and barrel buttons, touch keyboard, and background app services).</span></span>

<span data-ttu-id="93620-106">Die UWP verwendet ein intelligentes, kontextbezogenes Interaktionssystem, mit dem in den meisten Fällen die von der App empfangenen eindeutigen Eingabetypen nicht individuell behandelt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="93620-106">The UWP uses a "smart" contextual interaction system that, in most cases, eliminates the need to individually handle the unique types of input received by your app.</span></span> <span data-ttu-id="93620-107">Dazu zählt das Behandeln von Toucheingabe, Touchpad, Maus und Stifteingabe als generischer Zeigertyp, um statische Gesten wie Tippen oder Gedrückthalten und Manipulationsgesten wie Ziehen zum Verschieben oder zum Rendern von Freihandeingabe zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="93620-107">This includes handling touch, touchpad, mouse, and pen input as a generic pointer type to support static gestures such as tap or press-and-hold, manipulation gestures such as slide for panning, or rendering digital ink.</span></span>

<span data-ttu-id="93620-108">Machen Sie sich mit den verschiedenen Arten von Eingabegeräten sowie ihren Verhaltensweisen, Möglichkeiten und Einschränkungen in Verbindung mit bestimmten Formfaktoren vertraut.</span><span class="sxs-lookup"><span data-stu-id="93620-108">Familiarize yourself with each input device type and its behaviors, capabilities, and limitations when paired with certain form factors.</span></span> <span data-ttu-id="93620-109">Dies erleichtert Ihnen die Entscheidung, ob die Steuerelemente und Angebote der Plattform für die App ausreichend sind oder ob Sie angepasste Funktionen für die Benutzerinteraktion bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="93620-109">This can help you decide whether the platform controls and affordances are sufficient for your app, or require you to provide customized interaction experiences.</span></span>

## <a name="surface-dial"></a><span data-ttu-id="93620-110">Surface Dial</span><span class="sxs-lookup"><span data-stu-id="93620-110">Surface Dial</span></span>

<span data-ttu-id="93620-111">Für das Windows10 Anniversary Update führen wir eine neue Kategorie von Eingabegeräten, Windows Wheel, ein.</span><span class="sxs-lookup"><span data-stu-id="93620-111">For Windows 10 Anniversary Update, we're introducing a new category of input device called Windows Wheel.</span></span> <span data-ttu-id="93620-112">Surface Dial ist das erste Angebot dieser Art.</span><span class="sxs-lookup"><span data-stu-id="93620-112">The Surface Dial is the first in this class of device.</span></span> 

### <a name="device-support"></a><span data-ttu-id="93620-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-113">Device support</span></span>

-   <span data-ttu-id="93620-114">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-114">Tablet</span></span>
-   <span data-ttu-id="93620-115">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-115">PCs and laptops</span></span>

### <a name="typical-usage"></a><span data-ttu-id="93620-116">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-116">Typical usage</span></span>

<span data-ttu-id="93620-117">Der Formfaktor von Surface Dial entspricht einer Drehaktion (oder -geste). Surface Dial soll als sekundäres, multimodales Eingabegerät genutzt werden, das Eingaben über ein primäres Gerät ergänzt oder modifiziert.</span><span class="sxs-lookup"><span data-stu-id="93620-117">With a form factor based on a rotate action (or gesture), the Surface Dial is intended as a secondary, multi-modal input device that complements or modifies input from a primary device.</span></span> <span data-ttu-id="93620-118">In den meisten Fällen wird das Gerät von einem Benutzer mit der nicht dominanten Hand bedient, während er mit seiner dominanten Hand eine Aufgabe ausführt (z.B. Freihandzeichnen mit einem Stift).</span><span class="sxs-lookup"><span data-stu-id="93620-118">In most cases, the device is manipulated by a user's non-dominant hand while they perform a task with their dominant hand (such as inking with a pen).</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-119">More info</span></span>

[<span data-ttu-id="93620-120">Surface Dial-Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="93620-120">Surface Dial design guidelines</span></span>](windows-wheel-interactions.md)


## <a name="cortana"></a><span data-ttu-id="93620-121">Cortana</span><span class="sxs-lookup"><span data-stu-id="93620-121">Cortana</span></span>

<span data-ttu-id="93620-122">In Windows10 können Sie mit der Erweiterung **Cortana** Sprachbefehle von einem Benutzer behandeln und die Anwendung zum Ausführen einer einzelnen Aktion starten.</span><span class="sxs-lookup"><span data-stu-id="93620-122">In Windows 10, **Cortana** extensibility lets you handle voice commands from a user and launch your application to carry out a single action.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-123">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-123">Device support</span></span>

-   <span data-ttu-id="93620-124">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-124">Phones and phablets</span></span>
-   <span data-ttu-id="93620-125">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-125">Tablet</span></span>
-   <span data-ttu-id="93620-126">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-126">PCs and laptops</span></span>
-   <span data-ttu-id="93620-127">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-127">Surface Hub</span></span>
-   <span data-ttu-id="93620-128">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-128">IoT</span></span>
-   <span data-ttu-id="93620-129">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-129">Xbox</span></span>
-   <span data-ttu-id="93620-130">HoloLens</span><span class="sxs-lookup"><span data-stu-id="93620-130">HoloLens</span></span>

![Cortana](images/input-interactions/icons-cortana01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-132">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-132">Typical usage</span></span>

<span data-ttu-id="93620-133">Ein Sprachbefehl ist eine einzelne, in einer Sprachbefehldefinitions-Datei (VCD-Datei) definierte Äußerung, die über **Cortana** an eine installierte App weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="93620-133">A voice command is a single utterance, defined in a Voice Command Definition (VCD) file, directed at an installed app through **Cortana**.</span></span> <span data-ttu-id="93620-134">Die App kann im Vordergrund oder im Hintergrund gestartet werden, je nach Ebene und Komplexität der Interaktion.</span><span class="sxs-lookup"><span data-stu-id="93620-134">The app can be launched in the foreground or background, depending on the level and complexity of the interaction.</span></span> <span data-ttu-id="93620-135">Sprachbefehle, die zusätzlichen Kontext oder Benutzereingaben erfordern, werden beispielsweise am besten im Vordergrund ausgeführt, während grundlegende Befehle im Hintergrund behandelt werden können.</span><span class="sxs-lookup"><span data-stu-id="93620-135">For instance, voice commands that require additional context or user input are best handled in the foreground, while basic commands can be handled in the background.</span></span>

<span data-ttu-id="93620-136">**Cortana** integriert die grundlegenden Funktionen Ihrer App, bietet einen zentralen Einstiegspunkt, über den der Benutzer die meisten Aufgaben ohne Öffnen der App ausführen kann, und wird somit zum Bindeglied zwischen Ihrer App und dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="93620-136">Integrating the basic functionality of your app, and providing a central entry point for the user to accomplish most of the tasks without opening your app directly, lets **Cortana** become a liaison between your app and the user.</span></span> <span data-ttu-id="93620-137">In vielen Fällen spart der Benutzer dadurch viel Zeit und Mühe.</span><span class="sxs-lookup"><span data-stu-id="93620-137">In many cases, this can save the user significant time and effort.</span></span> <span data-ttu-id="93620-138">Weitere Informationen finden Sie unter [Cortana-Entwurfsrichtlinien](https://msdn.microsoft.com/library/windows/apps/dn974233).</span><span class="sxs-lookup"><span data-stu-id="93620-138">For more info, see [Cortana design guidelines](https://msdn.microsoft.com/library/windows/apps/dn974233).</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-139">More info</span></span>

[<span data-ttu-id="93620-140">Cortana-Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="93620-140">Cortana design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn974233)
 

## <a name="speech"></a><span data-ttu-id="93620-141">Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="93620-141">Speech</span></span>

<span data-ttu-id="93620-142">Die Spracherkennung ist eine effektive und natürliche Möglichkeit, mit Apps zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="93620-142">Speech is an effective and natural way for people to interact with applications.</span></span> <span data-ttu-id="93620-143">Sie bietet eine unkomplizierte und präzise Möglichkeit der Kommunikation mit Apps; damit können Benutzer in einer Vielzahl von Situationen produktiv arbeiten und auf dem Laufenden bleiben.</span><span class="sxs-lookup"><span data-stu-id="93620-143">It's an easy and accurate way to communicate with applications, and lets people be productive and stay informed in a variety of situations.</span></span>

<span data-ttu-id="93620-144">Die Spracherkennung kann den Haupteingabetyp je nach Gerät in vielen Fällen ergänzen oder sogar an dessen Stelle treten.</span><span class="sxs-lookup"><span data-stu-id="93620-144">Speech can complement or, in many cases, be the primary input type, depending on the user's device.</span></span> <span data-ttu-id="93620-145">Beispielsweise unterstützen Geräte wie HoloLens und Xbox keine herkömmlichen Eingabetypen (abgesehen von einer Softwaretastatur in bestimmten Szenarien).</span><span class="sxs-lookup"><span data-stu-id="93620-145">For example, devices such as HoloLens and Xbox do not support traditional input types (aside from a software keyboard in specific scenarios).</span></span> <span data-ttu-id="93620-146">Stattdessen verwenden sie für die meisten Benutzerinteraktionen Spracheingabe und -ausgabe (häufig zusammen mit anderen modernen Eingabetypen wie Gestik und Mimik).</span><span class="sxs-lookup"><span data-stu-id="93620-146">Instead, they rely on speech input and output (often combined with other non-traditional input types such as gaze and gesture) for most user interactions.</span></span>

<span data-ttu-id="93620-147">Mit Text-zu-Sprache (auch als TTS oder Sprachsynthese bezeichnet) werden Informationen oder Anweisungen an den Benutzer ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="93620-147">Text-to-speech (also known as TTS, or speech synthesis) is used to inform or direct the user.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-148">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-148">Device support</span></span>

-   <span data-ttu-id="93620-149">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-149">Phones and phablets</span></span>
-   <span data-ttu-id="93620-150">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-150">Tablet</span></span>
-   <span data-ttu-id="93620-151">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-151">PCs and laptops</span></span>
-   <span data-ttu-id="93620-152">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-152">Surface Hub</span></span>
-   <span data-ttu-id="93620-153">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-153">IoT</span></span>
-   <span data-ttu-id="93620-154">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-154">Xbox</span></span>
-   <span data-ttu-id="93620-155">HoloLens</span><span class="sxs-lookup"><span data-stu-id="93620-155">HoloLens</span></span>

![Spracherkennung](images/input-interactions/icons-speech01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-157">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-157">Typical usage</span></span>

<span data-ttu-id="93620-158">Es gibt drei Modi der Sprachinteraktion:</span><span class="sxs-lookup"><span data-stu-id="93620-158">There are three modes of Speech interaction:</span></span>

**<span data-ttu-id="93620-159">Natürliche Sprache</span><span class="sxs-lookup"><span data-stu-id="93620-159">Natural language</span></span>**

<span data-ttu-id="93620-160">Mit natürlicher Sprache kommunizieren wir laufend mündlich mit anderen Personen.</span><span class="sxs-lookup"><span data-stu-id="93620-160">Natural language is how we verbally interact with people on a regular basis.</span></span> <span data-ttu-id="93620-161">Unsere Sprache variiert in Abhängigkeit von der jeweiligen Person oder Situation, sie wird jedoch generell verstanden.</span><span class="sxs-lookup"><span data-stu-id="93620-161">Our speech varies from person to person and situation to situation, and is generally understood.</span></span> <span data-ttu-id="93620-162">Wenn dies nicht der Fall ist, verwenden wir häufig andere Wörter oder eine abweichende Wortreihenfolge, um die gleichen Gedanken zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="93620-162">When it's not, we often use different words and word order to get the same idea across.</span></span>

<span data-ttu-id="93620-163">Die Kommunikation über natürliche Sprache mit einer App verläuft ähnlich: Wir sprechen über unser Gerät mit der App wie mit einer Person und erwarten, dass sie uns versteht und entsprechend reagiert.</span><span class="sxs-lookup"><span data-stu-id="93620-163">Natural language interactions with an app are similar: we speak to the app through our device as if it were a person and expect it to understand and react accordingly.</span></span>

<span data-ttu-id="93620-164">Die natürliche Sprache ist der fortgeschrittenste Modus der Sprachinteraktion, der über **Cortana** implementiert und verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="93620-164">Natural language is the most advanced mode of speech interaction, and can be implemented and exposed through **Cortana**.</span></span>

**<span data-ttu-id="93620-165">Befehl und Steuerung</span><span class="sxs-lookup"><span data-stu-id="93620-165">Command and control</span></span>**

<span data-ttu-id="93620-166">Unter Befehl und Steuerung wird die Verwendung von Sprachbefehlen zum Aktivieren von Steuerelementen und Funktionen verstanden, z. B. zum Klicken auf eine Schaltfläche oder zum Auswählen eines Menüelements.</span><span class="sxs-lookup"><span data-stu-id="93620-166">Command and control is the use of verbal commands to activate controls and functionality such as clicking a button or selecting a menu item.</span></span>

<span data-ttu-id="93620-167">Da Befehl und Steuerung entscheidend für eine erfolgreiche Benutzeroberfläche ist, wird ein einzelner Eingabetyp im Allgemeinen nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="93620-167">As command and control is critical to a successful user experience, a single input type is generally not recommended.</span></span> <span data-ttu-id="93620-168">Die Spracherkennung ist in der Regel eine von mehreren Eingabeoptionen für einen Benutzer, die von seinen Vorlieben und Hardwarefunktionen abhängen.</span><span class="sxs-lookup"><span data-stu-id="93620-168">Speech is typically one of several input options for a user based on their preferences or hardware capabilities.</span></span>

**<span data-ttu-id="93620-169">Diktieren</span><span class="sxs-lookup"><span data-stu-id="93620-169">Dictation</span></span>**

<span data-ttu-id="93620-170">Die einfachste Methode der Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="93620-170">The most basic speech input method.</span></span> <span data-ttu-id="93620-171">Jede Äußerung wird in Text umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="93620-171">Each utterance is converted to text.</span></span>

<span data-ttu-id="93620-172">Das Diktieren wird in der Regel verwendet, wenn eine App die Bedeutung oder die Absicht nicht verstehen muss.</span><span class="sxs-lookup"><span data-stu-id="93620-172">Dictation is typically used when an app doesn’t need to understand meaning or intent.</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-173">More info</span></span>

[<span data-ttu-id="93620-174">Richtlinien für den Sprachentwurf</span><span class="sxs-lookup"><span data-stu-id="93620-174">Speech design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596121)
 

## <a name="pen"></a><span data-ttu-id="93620-175">Stift</span><span class="sxs-lookup"><span data-stu-id="93620-175">Pen</span></span>

<span data-ttu-id="93620-176">Ein (Eingabe-)Stift kann ähnlich wie eine Maus als pixelgenaues Zeigegerät verwendet werden, und er eignet sich optimal für die Freihandeingabe.</span><span class="sxs-lookup"><span data-stu-id="93620-176">A pen (or stylus) can serve as a pixel precise pointing device, like a mouse, and is the optimal device for digital ink input.</span></span>

<span data-ttu-id="93620-177">**Hinweis**  Es gibt zwei Arten von Stiften: aktive und passive.</span><span class="sxs-lookup"><span data-stu-id="93620-177">**Note**  There are two types of pen devices: active and passive.</span></span>
  -   <span data-ttu-id="93620-178">Passive Stifte enthalten keine Elektronik, und sie emulieren effektiv die Toucheingabe über einen Finger.</span><span class="sxs-lookup"><span data-stu-id="93620-178">Passive pens do not contain electronics, and effectively emulate touch input from a finger.</span></span> <span data-ttu-id="93620-179">Sie benötigen eine Basisgerätanzeige, welche die Eingabe basierend auf dem Berührungsdruck erkennt.</span><span class="sxs-lookup"><span data-stu-id="93620-179">They require a basic device display that recognizes input based on contact pressure.</span></span> <span data-ttu-id="93620-180">Da Benutzer beim Schreiben auf der Eingabeoberfläche häufig die Hand ablegen, können Eingabedaten wegen des nicht erfolgreichen Ablehnens der Handfläche verzerrt werden.</span><span class="sxs-lookup"><span data-stu-id="93620-180">Because users often rest their hand as they write on the input surface, input data can become polluted due to unsuccessful palm rejection.</span></span>
  -   <span data-ttu-id="93620-181">Aktive Stifte enthalten Elektronik und können mit komplexen Gerätedisplays zusammenwirken und viel umfassendere Eingabedaten (u.a. Daten bei Daraufzeigen oder Näherung) für das System und die App liefern.</span><span class="sxs-lookup"><span data-stu-id="93620-181">Active pens contain electronics and can work with complex device displays to provide much more extensive input data (including hover, or proximity data) to the system and your app.</span></span> <span data-ttu-id="93620-182">Die Handflächenablehnung ist sehr viel robuster.</span><span class="sxs-lookup"><span data-stu-id="93620-182">Palm rejection is much more robust.</span></span>

<span data-ttu-id="93620-183">In diesem Text beziehen wir uns auf aktive Stifte, die umfangreiche Eingabedaten liefern und in erster Linie für präzise Freihandeingaben und für zeigebasierte Interaktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="93620-183">When we refer to pen devices here, we are referring to active pens that provide rich input data and are used primarily for precise ink and pointing interactions.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-184">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-184">Device support</span></span>

-   <span data-ttu-id="93620-185">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-185">Phones and phablets</span></span>
-   <span data-ttu-id="93620-186">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-186">Tablet</span></span>
-   <span data-ttu-id="93620-187">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-187">PCs and laptops</span></span>
-   <span data-ttu-id="93620-188">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-188">Surface Hub</span></span>
-   <span data-ttu-id="93620-189">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-189">IoT</span></span>

![Stift](images/input-interactions/icons-pen01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-191">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-191">Typical usage</span></span>

<span data-ttu-id="93620-192">In Kombination mit einem Stift ermöglicht die Windows-Freihandplattform die natürliche Erstellung von handschriftlichen Notizen, Zeichnungen und Anmerkungen.</span><span class="sxs-lookup"><span data-stu-id="93620-192">The Windows ink platform, together with a pen, provides a natural way to create handwritten notes, drawings, and annotations.</span></span> <span data-ttu-id="93620-193">Die Plattform unterstützt das Erfassen von Freihanddaten aus einem Eingabedigitalisierungsgerät, das Generieren von Freihanddaten, das Ausgeben von Daten und das Rendern von Freihandstrichen auf dem Ausgabegerät sowie das Verwalten von Daten und das Ausführen einer Schrifterkennung.</span><span class="sxs-lookup"><span data-stu-id="93620-193">The platform supports capturing ink data from digitizer input, generating ink data, rendering that data as ink strokes on the output device, managing the ink data, and performing handwriting recognition.</span></span> <span data-ttu-id="93620-194">Ihre App kann nicht nur die räumlichen Bewegungen des Stifts beim Schreiben oder Zeichnen erfassen. Sie kann auch Informationen zu Druck, Form, Farbe und Deckkraft sammeln und ermöglicht so eine Arbeitsweise, die der Verwendung eines Stifts, Bleistifts oder Pinsels auf Papier schon sehr nahe kommt.</span><span class="sxs-lookup"><span data-stu-id="93620-194">In addition to capturing the spatial movements of the pen as the user writes or draws, your app can also collect info such as pressure, shape, color, and opacity, to offer user experiences that closely resemble drawing on paper with a pen, pencil, or brush.</span></span>

<span data-ttu-id="93620-195">Die Stift- und die Toucheingabe unterscheiden sich dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (wie Wischen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="93620-195">Where pen and touch input diverge is the ability for touch to emulate direct manipulation of UI elements on the screen through physical gestures performed on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span>

<span data-ttu-id="93620-196">Sie müssen stiftspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="93620-196">You should provide pen-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="93620-197">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="93620-197">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-198">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-198">More info</span></span>

[<span data-ttu-id="93620-199">Zeichenstift-Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="93620-199">Pen design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456352)
 

## <a name="touch"></a><span data-ttu-id="93620-200">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="93620-200">Touch</span></span>

<span data-ttu-id="93620-201">Bei der Toucheingabe können mit einem oder mehreren Fingern ausgeführte Gesten verwendet werden, um die direkte Manipulation von UI-Elementen (wie etwa Verschieben, Drehen, Ändern der Größe oder Bewegen) zu emulieren. Außerdem können die Gesten auch als alternative Eingabemethode (ähnlich einer Maus- oder Stifteingabe) oder als ergänzende Eingabemethode (zum Modifizieren anderer Eingaben; also beispielsweise zum Verwischen eines mit einem Stift gezeichneten Freihandstrichs) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="93620-201">With touch, physical gestures from one or more fingers can be used to either emulate the direct manipulation of UI elements (such as panning, rotating, resizing, or moving), as an alternative input method (similar to mouse or pen), or as a complementary input method (to modify aspects of other input, such as smudging an ink stroke drawn with a pen).</span></span> <span data-ttu-id="93620-202">Diese berührungsbasierte Bedienung wird von Benutzern unter Umständen als natürlicher wahrgenommen als die symbolbasierte Interaktion auf einem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="93620-202">Tactile experiences such as this can provide more natural, real-world sensations for users as they interact with elements on a screen.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-203">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-203">Device support</span></span>

-   <span data-ttu-id="93620-204">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-204">Phones and phablets</span></span>
-   <span data-ttu-id="93620-205">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-205">Tablet</span></span>
-   <span data-ttu-id="93620-206">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-206">PCs and laptops</span></span>
-   <span data-ttu-id="93620-207">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-207">Surface Hub</span></span>
-   <span data-ttu-id="93620-208">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-208">IoT</span></span>

![Toucheingabe](images/input-interactions/icons-touch01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-210">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-210">Typical usage</span></span>

<span data-ttu-id="93620-211">Die Unterstützung für die Toucheingabe kann je nach Gerät stark variieren.</span><span class="sxs-lookup"><span data-stu-id="93620-211">Support for touch input can vary significantly, depending on the device.</span></span>

<span data-ttu-id="93620-212">Einige Geräte unterstützen keinerlei Toucheingabe, einige unterstützen einen einzelnen Touchkontakt, während wiederum andere Multitouchinteraktionen (zwei oder mehr Kontakte) unterstützen.</span><span class="sxs-lookup"><span data-stu-id="93620-212">Some devices don't support touch at all, some devices support a single touch contact, while others support multi-touch (two or more contacts).</span></span>

<span data-ttu-id="93620-213">Die meisten Geräte mit Unterstützung von Multitouchinteraktionen erkennen zehn eindeutige gleichzeitige Kontakte.</span><span class="sxs-lookup"><span data-stu-id="93620-213">Most devices that support multi-touch input, typically recognize ten unique, concurrent contacts.</span></span>

<span data-ttu-id="93620-214">Surface Hub-Geräte erkennen 100 eindeutige, gleichzeitige Berührungskontakte.</span><span class="sxs-lookup"><span data-stu-id="93620-214">Surface Hub devices recognize 100 unique, concurrent touch contacts.</span></span>

<span data-ttu-id="93620-215">Im Allgemeinen weist die Toucheingabe folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="93620-215">In general, touch is:</span></span>

-   <span data-ttu-id="93620-216">Einzelner Benutzer, es sei denn, sie kommt mit einem Microsoft-Team-Gerät wie Surface-Hub zur Anwendung, bei dem der Schwerpunkt auf der Zusammenarbeit liegt.</span><span class="sxs-lookup"><span data-stu-id="93620-216">Single user, unless being used with a Microsoft Team device like Surface Hub, where collaboration is emphasized.</span></span>
-   <span data-ttu-id="93620-217">Keine Beschränkung hinsichtlich der Geräteausrichtung.</span><span class="sxs-lookup"><span data-stu-id="93620-217">Not constrained to device orientation.</span></span>
-   <span data-ttu-id="93620-218">Wird für alle Interaktionen, u.a. Texteingabe (Bildschirmtastatur) und Freihandeingabe (für die App konfiguriert) verwendet.</span><span class="sxs-lookup"><span data-stu-id="93620-218">Used for all interactions, including text input (touch keyboard) and inking (app-configured).</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-219">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-219">More info</span></span>

[<span data-ttu-id="93620-220">Richtlinien für die Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="93620-220">Touch design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465370)
 

## <a name="touchpad"></a><span data-ttu-id="93620-221">Touchpad</span><span class="sxs-lookup"><span data-stu-id="93620-221">Touchpad</span></span>

<span data-ttu-id="93620-222">Ein Touchpad vereint die indirekte Multitoucheingabe mit der Präzisionseingabe eines Zeigergeräts (beispielsweise eine Maus).</span><span class="sxs-lookup"><span data-stu-id="93620-222">A touchpad combines both indirect multi-touch input with the precision input of a pointing device, such as a mouse.</span></span> <span data-ttu-id="93620-223">Durch diese Kombination ist das Touchpad sowohl für eine toucheingabeoptimierte Benutzeroberfläche als auch für die kleineren Ziele von Produktivitäts-Apps geeignet.</span><span class="sxs-lookup"><span data-stu-id="93620-223">This combination makes the touchpad suited to both a touch-optimized UI and the smaller targets of productivity apps.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-224">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-224">Device support</span></span>

-   <span data-ttu-id="93620-225">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-225">PCs and laptops</span></span>
-   <span data-ttu-id="93620-226">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-226">IoT</span></span>

![Touchpad](images/input-interactions/icons-touchpad01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-228">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-228">Typical usage</span></span>

<span data-ttu-id="93620-229">Touchpads unterstützen in der Regel eine Reihe von Touchgesten, die für die direkte Manipulation von Objekten und Benutzeroberflächenelementen eine ähnliche Unterstützung bieten wie die Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="93620-229">Touchpads typically support a set of touch gestures that provide support similar to touch for direct manipulation of objects and UI.</span></span>

<span data-ttu-id="93620-230">Aufgrund dieser Konvergenz bei der von Touchpads unterstützten Interaktion empfiehlt es sich, sich nicht allein auf die Unterstützung der Toucheingabe zu verlassen, sondern auch Benutzeroberflächenbefehle oder Angebote für die Mauseingabe bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="93620-230">Because of this convergence of interaction experiences supported by touchpads, we recommend also providing mouse-style UI commands or affordances rather than relying solely on support for touch input.</span></span> <span data-ttu-id="93620-231">Stellen Sie Touchpad-spezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="93620-231">Provide touchpad-specific UI commands, or affordances, to support these interactions.</span></span>

<span data-ttu-id="93620-232">Sie müssen mausspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="93620-232">You should provide mouse-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="93620-233">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="93620-233">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-234">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-234">More info</span></span>

[<span data-ttu-id="93620-235">Touchpad-Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="93620-235">Touchpad design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456353)
 

## <a name="keyboard"></a><span data-ttu-id="93620-236">Tastatur</span><span class="sxs-lookup"><span data-stu-id="93620-236">Keyboard</span></span>

<span data-ttu-id="93620-237">Eine Tastatur ist das Haupteingabegerät für Text und häufig unentbehrlich für Personen mit bestimmten körperlichen Beeinträchtigungen oder für Benutzer, die die Tastatur als schnellere und effizientere Interaktionsmethode betrachten.</span><span class="sxs-lookup"><span data-stu-id="93620-237">A keyboard is the primary input device for text, and is often indispensable to people with certain disabilities or users who consider it a faster and more efficient way to interact with an app.</span></span>

<span data-ttu-id="93620-238">Mit [Continuum für Smartphones](http://go.microsoft.com/fwlink/p/?LinkID=699431), einer neuen Funktion für kompatible Windows 10-Mobilgeräte können Benutzer ihre Smartphones mit einer Maus und einer Tastatur verbinden und damit Ihr Gerät wie einen Laptop nutzen.</span><span class="sxs-lookup"><span data-stu-id="93620-238">With [Continuum for Phone](http://go.microsoft.com/fwlink/p/?LinkID=699431), a new experience for compatible Windows 10 mobile devices, users can connect their phones to a mouse and keyboard to make their phones work like a laptop.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-239">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-239">Device support</span></span>

-   <span data-ttu-id="93620-240">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-240">Phones and phablets</span></span>
-   <span data-ttu-id="93620-241">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-241">Tablet</span></span>
-   <span data-ttu-id="93620-242">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-242">PCs and laptops</span></span>
-   <span data-ttu-id="93620-243">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-243">Surface Hub</span></span>
-   <span data-ttu-id="93620-244">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-244">IoT</span></span>
-   <span data-ttu-id="93620-245">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-245">Xbox</span></span>
-   <span data-ttu-id="93620-246">HoloLens</span><span class="sxs-lookup"><span data-stu-id="93620-246">HoloLens</span></span>

![Tastatur](images/input-interactions/icons-keyboard01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-248">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-248">Typical usage</span></span>

<span data-ttu-id="93620-249">Benutzer können mit Universellen Windows-Apps über eine Hardwaretastatur und zwei Softwaretastaturen (Bildschirmtastatur oder Touchtastatur) interagieren.</span><span class="sxs-lookup"><span data-stu-id="93620-249">Users can interact with Universal Windows apps through a hardware keyboard and two software keyboards: the On-Screen Keyboard (OSK) and the touch keyboard.</span></span>

<span data-ttu-id="93620-250">Bei der Bildschirmtastatur handelt es sich um eine visuelle Softwaretastatur, die Sie anstelle der physischen Tastatur zum Eingeben von Daten per Touch, Maus, (Eingabe-)Stift oder anderen Zeigegeräten verwenden können. Ein Touchscreen ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="93620-250">The OSK is a visual, software keyboard that you can use instead of the physical keyboard to type and enter data using touch, mouse, pen/stylus or other pointing device (a touch screen is not required).</span></span> <span data-ttu-id="93620-251">Die Bildschirmtastatur ist für Systeme ohne physische Tastatur oder für Benutzer vorgesehen, deren Mobilitätseinschränkungen die Verwendung herkömmlicher physischer Eingabegeräte verhindern.</span><span class="sxs-lookup"><span data-stu-id="93620-251">The OSK is provided for systems that don't have a physical keyboard, or for users whose mobility impairments prevent them from using traditional physical input devices.</span></span> <span data-ttu-id="93620-252">Die Bildschirmtastatur emuliert nahezu alle Funktionen der Hardwaretastatur.</span><span class="sxs-lookup"><span data-stu-id="93620-252">The OSK emulates most, if not all, the functionality of a hardware keyboard.</span></span>

<span data-ttu-id="93620-253">Bei der Bildschirmtastatur handelt es sich um eine visuelle Softwaretastatur für die Texteingabe per Touchscreen.</span><span class="sxs-lookup"><span data-stu-id="93620-253">The touch keyboard is a visual, software keyboard used for text entry with touch input.</span></span> <span data-ttu-id="93620-254">Die Touchtastatur ist kein Ersatz für die Bildschirmtastatur. Sie wird nur für die Texteingabe (ohne Emulierung der Hardwaretastatur) verwendet und nur angezeigt, wenn der Fokus auf einem Textfeld oder einem anderen bearbeitbaren Textsteuerelement liegt.</span><span class="sxs-lookup"><span data-stu-id="93620-254">The touch keyboard is not a replacement for the OSK as it is used for text input only (it doesn't emulate the hardware keyboard) and appears only when a text field or other editable text control gets focus.</span></span> <span data-ttu-id="93620-255">Die Bildschirmtastatur unterstützt keine App- oder Systembefehle.</span><span class="sxs-lookup"><span data-stu-id="93620-255">The touch keyboard does not support app or system commands.</span></span>

<span data-ttu-id="93620-256">**Hinweis**  Die Bildschirmtastatur hat Vorrang vor der Touchtastatur. Ist die Bildschirmtastatur vorhanden, wird die Touchtastatur nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93620-256">**Note**  The OSK has priority over the touch keyboard, which won't be shown if the OSK is present.</span></span>

<span data-ttu-id="93620-257">Im Allgemeinen weist eine Tastatur folgende Merkmale auf:</span><span class="sxs-lookup"><span data-stu-id="93620-257">In general, a keyboard is:</span></span>

-   <span data-ttu-id="93620-258">Einzelner Benutzer.</span><span class="sxs-lookup"><span data-stu-id="93620-258">Single user.</span></span>
-   <span data-ttu-id="93620-259">Keine Beschränkung hinsichtlich der Geräteausrichtung.</span><span class="sxs-lookup"><span data-stu-id="93620-259">Not constrained to device orientation.</span></span>
-   <span data-ttu-id="93620-260">Wird für Texteingabe, Navigation, Spiele und Eingabehilfen verwendet.</span><span class="sxs-lookup"><span data-stu-id="93620-260">Used for text input, navigation, gameplay, and accessibility.</span></span>
-   <span data-ttu-id="93620-261">Immer verfügbar, entweder proaktiv oder reaktiv.</span><span class="sxs-lookup"><span data-stu-id="93620-261">Always available, either proactively or reactively.</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-262">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-262">More info</span></span>

[<span data-ttu-id="93620-263">Tastaturentwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="93620-263">Keyboard design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/hh972345)
 

## <a name="mouse"></a><span data-ttu-id="93620-264">Maus</span><span class="sxs-lookup"><span data-stu-id="93620-264">Mouse</span></span>

<span data-ttu-id="93620-265">Eine Maus eignet sich am besten für Produktivitäts-Apps und Benutzeroberflächen mit hoher Dichte, bei denen Benutzerinteraktionen beim Zielen und bei der Befehlseingabe Pixelgenauigkeit erfordern.</span><span class="sxs-lookup"><span data-stu-id="93620-265">A mouse is best suited for productivity apps and high-density UI where user interactions require pixel-level precision for targeting and commanding.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-266">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-266">Device support</span></span>

-   <span data-ttu-id="93620-267">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-267">Phones and phablets</span></span>
-   <span data-ttu-id="93620-268">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-268">Tablet</span></span>
-   <span data-ttu-id="93620-269">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-269">PCs and laptops</span></span>
-   <span data-ttu-id="93620-270">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-270">Surface Hub</span></span>
-   <span data-ttu-id="93620-271">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-271">IoT</span></span>

![Maus](images/input-interactions/icons-mouse01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-273">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-273">Typical usage</span></span>

<span data-ttu-id="93620-274">Die Mauseingabe kann über verschiedene Tasten der Tastatur (STRG, UMSCHALTTASTE, ALT usw.) geändert werden.</span><span class="sxs-lookup"><span data-stu-id="93620-274">Mouse input can be modified with the addition of various keyboard keys (Ctrl, Shift, Alt, and so on).</span></span> <span data-ttu-id="93620-275">Diese Tasten können mit der linken Maustaste, der rechten Maustaste, der Radtaste und den X-Tasten zu einem erweiterten, mausoptimierten Befehlssatz kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="93620-275">These keys can be combined with the left mouse button, the right mouse button, the wheel button, and the X buttons for an expanded mouse-optimized command set.</span></span> <span data-ttu-id="93620-276">(Einige Microsoft-Mausgeräte verfügen über zwei weitere Schaltflächen, die als X-Tasten bezeichnet werden. Diese dienen gewöhnlich dazu, in Webbrowsern zurück und vorwärts zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="93620-276">(Some Microsoft mouse devices have two additional buttons, referred to as X buttons, typically used to navigate back and forward in Web browsers).</span></span>

<span data-ttu-id="93620-277">Ähnlich wie bei der Stifteingabe unterscheiden sich Maus- und Toucheingabe dahingehend, dass bei der Toucheingabe die direkte Manipulation von UI-Elementen auf dem Bildschirm durch physische Gesten für diese Objekte (z.B. Wischen, Ziehen, Drehen usw.) emuliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="93620-277">Similar to pen, where mouse and touch input diverge is the ability for touch to emulate direct manipulation of UI elements on the screen through physical gestures performed on those objects (such as swiping, sliding, dragging, rotating, and so on).</span></span>

<span data-ttu-id="93620-278">Sie müssen mausspezifische Benutzeroberflächenbefehle (oder Angebote) zur Unterstützung dieser Interaktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="93620-278">You should provide mouse-specific UI commands, or affordances, to support these interactions.</span></span> <span data-ttu-id="93620-279">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="93620-279">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>

### <a name="more-info"></a><span data-ttu-id="93620-280">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="93620-280">More info</span></span>

[<span data-ttu-id="93620-281">Richtlinien für die Mausinteraktion</span><span class="sxs-lookup"><span data-stu-id="93620-281">Mouse design guidelines</span></span>](https://msdn.microsoft.com/library/windows/apps/dn456351)
 

## <a name="gesture"></a><span data-ttu-id="93620-282">Geste</span><span class="sxs-lookup"><span data-stu-id="93620-282">Gesture</span></span>

<span data-ttu-id="93620-283">Eine Geste ist jede Art von Benutzerbewegung, die als Steuerungs- oder Interaktionseingabe für eine Anwendung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="93620-283">A gesture is any form of user movement that is recognized as input for controlling or interacting with an application.</span></span> <span data-ttu-id="93620-284">Es gibt verschiedene Arten von Gesten – von der einfachen Geste, die dazu dient, mit der Hand etwas auf dem Bildschirm zu verwenden, über spezifische, erlernte Bewegungsmuster bis hin zu langen Bewegungsabläufen des gesamten Körpers.</span><span class="sxs-lookup"><span data-stu-id="93620-284">Gestures take many forms, from simply using a hand to target something on the screen, to specific, learned patterns of movement, to long stretches of continuous movement using the entire body.</span></span> <span data-ttu-id="93620-285">Beachten Sie beim Entwerfen benutzerdefinierter Gesten, dass diese in anderen Regionen/Kulturkreisen unter Umständen eine andere Bedeutung haben.</span><span class="sxs-lookup"><span data-stu-id="93620-285">Be careful when designing custom gestures, as their meaning can vary depending on locale and culture.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-286">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-286">Device support</span></span>

-   <span data-ttu-id="93620-287">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-287">PCs and laptops</span></span>
-   <span data-ttu-id="93620-288">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-288">IoT</span></span>
-   <span data-ttu-id="93620-289">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-289">Xbox</span></span>
-   <span data-ttu-id="93620-290">HoloLens</span><span class="sxs-lookup"><span data-stu-id="93620-290">HoloLens</span></span>

![Geste](images/input-interactions/icons-gesture01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-292">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-292">Typical usage</span></span>

<span data-ttu-id="93620-293">Statische Gestenereignisse werden ausgelöst, wenn eine Interaktion abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="93620-293">Static gesture events are fired after an interaction is complete.</span></span>

- <span data-ttu-id="93620-294">Zu den statischen Gestenereignissen zählen Tapped, DoubleTapped, RightTapped und Holding.</span><span class="sxs-lookup"><span data-stu-id="93620-294">Static gesture events include Tapped, DoubleTapped, RightTapped, and Holding.</span></span>

<span data-ttu-id="93620-295">Manipulationsgestenereignisse weisen auf eine andauernde Interaktion hin.</span><span class="sxs-lookup"><span data-stu-id="93620-295">Manipulation gesture events indicate an ongoing interaction.</span></span> <span data-ttu-id="93620-296">Sie werden ausgelöst, wenn der Benutzer ein Element berührt, und bleiben so lange aktiv, bis der Benutzer den bzw. die Finger vom Element hebt oder die Manipulation abgebrochen wird.</span><span class="sxs-lookup"><span data-stu-id="93620-296">They start firing when the user touches an element and continue until the user lifts their finger(s), or the manipulation is canceled.</span></span>

- <span data-ttu-id="93620-297">Manipulationsereignisse umfassen Multi-Touch-Interaktionen wie Zoomen, Schwenken und Drehen sowie Interaktionen, die Trägheits- und Geschwindigkeitsdaten nutzen (z.B. Ziehen).</span><span class="sxs-lookup"><span data-stu-id="93620-297">Manipulation events include multi-touch interactions such as zooming, panning, or rotating, and interactions that use inertia and velocity data such as dragging.</span></span> <span data-ttu-id="93620-298">(Die von den Manipulationsereignissen bereitgestellten Informationen identifizieren nicht die Interaktion, sondern stellen Daten wie Position, Übersetzungsdelta und Geschwindigkeit bereit.)</span><span class="sxs-lookup"><span data-stu-id="93620-298">(The information provided by the manipulation events doesn't identify the interaction, but rather provides data such as position, translation delta, and velocity.)</span></span>

- <span data-ttu-id="93620-299">Zeigerereignisse wie PointerPressed und PointerMoved bieten Details auf unterer Ebene für alle Touchkontakte einschließlich Zeigerbewegungen und die Möglichkeit, zwischen Drück- und Freigabeereignissen zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="93620-299">Pointer events such as PointerPressed and PointerMoved provide low-level details for each touch contact, including pointer motion and the ability to distinguish press and release events.</span></span>

<span data-ttu-id="93620-300">Aufgrund der Konvergenz von durch Windows unterstützten Interaktionsumgebungen wird empfohlen, sich nicht nur auf die Unterstützung für Toucheingaben zu verlassen, sondern auch Benutzeroberflächenbefehle oder Angebote für Mauseingaben bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="93620-300">Because of the convergence of interaction experiences supported by Windows, we recommend also providing mouse-style UI commands or affordances rather than relying solely on support for touch input.</span></span> <span data-ttu-id="93620-301">Verwenden Sie beispielsweise Schaltflächen für „Zurück“ und „Weiter“ (oder „+“ und „-“), um dem Benutzer das Blättern durch Seiten bzw. das Drehen, Vergrößern/Verkleinern und Zoomen von Objekten zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="93620-301">For example, use previous and next (or + and -) buttons to let users flip through pages of content, or rotate, resize, and zoom objects.</span></span>


## <a name="gamepadcontroller"></a><span data-ttu-id="93620-302">Gamepad/Controller</span><span class="sxs-lookup"><span data-stu-id="93620-302">Gamepad/Controller</span></span>

<span data-ttu-id="93620-303">Ein Gamepad/Controller ist ein sehr spezielles Gerät und kommt in der Regel bei Spielen zum Einsatz.</span><span class="sxs-lookup"><span data-stu-id="93620-303">The gamepad/controller is a highly specialized device typically dedicated to playing games.</span></span> <span data-ttu-id="93620-304">Es wird jedoch auch zum Emulieren einfacher Tastatureingaben sowie für eine tastaturähnliche UI-Navigation verwendet.</span><span class="sxs-lookup"><span data-stu-id="93620-304">However, it is also used for to emulate basic keyboard input and provides a UI navigation experience very similar to the keyboard.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-305">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-305">Device support</span></span>

-   <span data-ttu-id="93620-306">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-306">PCs and laptops</span></span>
-   <span data-ttu-id="93620-307">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-307">IoT</span></span>
-   <span data-ttu-id="93620-308">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-308">Xbox</span></span>

![Controller](images/input-interactions/icons-controller01.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-310">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-310">Typical usage</span></span>

<span data-ttu-id="93620-311">Spielen und Interaktionen mit einer speziellen Konsole.</span><span class="sxs-lookup"><span data-stu-id="93620-311">Playing games and interacting with a specialized console.</span></span>


## <a name="multiple-inputs"></a><span data-ttu-id="93620-312">Mehrfacheingaben</span><span class="sxs-lookup"><span data-stu-id="93620-312">Multiple inputs</span></span>

<span data-ttu-id="93620-313">Durch die Berücksichtigung so vieler Benutzer und Geräte wie möglich und den Entwurf Ihrer App für die Kompatibilität mit möglichst vielen Eingabearten (Gesten, Spracherkennung, Toucheingabe, Touchpad, Maus und Tastatur) maximieren Sie die Flexibilität, Benutzerfreundlichkeit und Barrierefreiheit Ihrer Apps.</span><span class="sxs-lookup"><span data-stu-id="93620-313">Accommodating as many users and devices as possible and designing your apps to work with as many input types (gesture, speech, touch, touchpad, mouse, and keyboard) as possible maximizes flexibility, usability, and accessibility.</span></span>

### <a name="device-support"></a><span data-ttu-id="93620-314">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="93620-314">Device support</span></span>

-   <span data-ttu-id="93620-315">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="93620-315">Phones and phablets</span></span>
-   <span data-ttu-id="93620-316">Tablet</span><span class="sxs-lookup"><span data-stu-id="93620-316">Tablet</span></span>
-   <span data-ttu-id="93620-317">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="93620-317">PCs and laptops</span></span>
-   <span data-ttu-id="93620-318">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="93620-318">Surface Hub</span></span>
-   <span data-ttu-id="93620-319">IoT</span><span class="sxs-lookup"><span data-stu-id="93620-319">IoT</span></span>
-   <span data-ttu-id="93620-320">Xbox</span><span class="sxs-lookup"><span data-stu-id="93620-320">Xbox</span></span>
-   <span data-ttu-id="93620-321">HoloLens</span><span class="sxs-lookup"><span data-stu-id="93620-321">HoloLens</span></span>

![Mehrfacheingaben](images/input-interactions/icons-inputdevices03-vertical.png)

### <a name="typical-usage"></a><span data-ttu-id="93620-323">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="93620-323">Typical usage</span></span>

<span data-ttu-id="93620-324">Personen kommunizieren untereinander mit einer Mischung aus Sprache und Gesten, und auch bei der Interaktion mit einer App kann sich die Verwendung mehrerer Eingabearten und -modi als hilfreich erweisen.</span><span class="sxs-lookup"><span data-stu-id="93620-324">Just as people use a combination of voice and gesture when communicating with each other, multiple types and modes of input can also be useful when interacting with an app.</span></span> <span data-ttu-id="93620-325">Diese kombinierten Interaktionen müssen jedoch möglichst intuitiv und natürlich gestaltet sein, da sie andernfalls zu Verwirrung führen können.</span><span class="sxs-lookup"><span data-stu-id="93620-325">However, these combined interactions need to be as intuitive and natural as possible as they can also create a very confusing experience.</span></span>





 

 
