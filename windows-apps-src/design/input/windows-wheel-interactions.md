---
author: Karl-Bridge-Microsoft
Description: Incorporate speech into your apps using Cortana voice commands, speech recognition, and speech synthesis.
title: Surface Dial-Interaktionen
label: Surface Dial interactions
template: detail.hbs
keywords: Surface Dial, Windows-Radgeräte, RadialController, Radial-Controller, Benutzerinteraktion, Eingabe
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.assetid: e7deb1d6-feeb-471e-9a83-26386d1aaf37
ms.localizationpriority: medium
ms.openlocfilehash: a443dd7505ce399d82cbd33c5691ec9b35a18b93
ms.sourcegitcommit: ce45a2bc5ca6794e97d188166172f58590e2e434
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "1983697"
---
# <a name="surface-dial-interactions"></a><span data-ttu-id="b42b9-103">Surface Dial-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b42b9-103">Surface Dial interactions</span></span>

![Abbildung: Surface Dial mit Surface Studio](images/windows-wheel/dial-pen-studio-600px.png)  
<span data-ttu-id="b42b9-105">*Surface Dial mit Surface Studio und Stift* (im [Microsoft Store](https://aka.ms/purchasesurfacedial) käuflich erhältlich).</span><span class="sxs-lookup"><span data-stu-id="b42b9-105">*Surface Dial with Surface Studio and Pen* (available for purchase at the [Microsoft Store](https://aka.ms/purchasesurfacedial)).</span></span>

## <a name="overview"></a><span data-ttu-id="b42b9-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b42b9-106">Overview</span></span>

<span data-ttu-id="b42b9-107">Windows Wheel-Geräte wie das Surface Dial bilden eine neue Kategorie von Eingabegeräten, die eine Vielzahl attraktiver, innovativer Benutzerinteraktionen für Windows und Windows-Apps unterstützen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-107">Windows wheel devices, such as the Surface Dial, are a new category of input device that enable a host of compelling and unique user interaction experiences for Windows and Windows apps.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b42b9-108">In diesem Thema gehen wir speziell auf Interaktionen mit dem Surface Dial ein, die Informationen treffen jedoch auf alle Windows Wheel-Geräte zu.</span><span class="sxs-lookup"><span data-stu-id="b42b9-108">In this topic, we refer specifically to Surface Dial interactions, but the info is applicable to all Windows wheel devices.</span></span> 

| <span data-ttu-id="b42b9-109">Videos</span><span class="sxs-lookup"><span data-stu-id="b42b9-109">Videos</span></span> |   |
| --- | --- |
| <iframe src="https://www.youtube-nocookie.com/embed/WMklcdzcNcU" width="300" height="200" allowFullScreen="true" frameBorder="0"></iframe> | <iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Programming-the-Microsoft-Surface-Dial/player" width="300" height="200" allowFullScreen="true" frameBorder="0"></iframe> |
| *<span data-ttu-id="b42b9-110">App-Partner für Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-110">Surface Dial app partners</span></span>* | *<span data-ttu-id="b42b9-111">Surface Dial für Entwickler</span><span class="sxs-lookup"><span data-stu-id="b42b9-111">Surface Dial for devs</span></span>* |

<span data-ttu-id="b42b9-112">Der Formfaktor des Surface Dial entspricht einer *Dreh*-Aktion (oder -Geste). Das Surface Dial soll als sekundäres, multimodales Eingabegerät genutzt werden, das Eingaben über ein primäres Gerät ergänzt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-112">With a form factor based on a *rotate* action (or gesture), the Surface Dial is intended as a secondary, multi-modal input device that complements input from a primary device.</span></span> <span data-ttu-id="b42b9-113">In den meisten Fällen wird das Gerät von einem Benutzer mit der nicht dominanten Hand bedient, während er mit seiner dominanten Hand eine Aufgabe ausführt (z.B. Freihandzeichnen mit einem Stift).</span><span class="sxs-lookup"><span data-stu-id="b42b9-113">In most cases, the device is manipulated by a user's non-dominant hand while performing a task with their dominant hand (such as inking with a pen).</span></span> <span data-ttu-id="b42b9-114">Es wurde nicht für präzise Zeigereingaben konzipiert (wie Touch-, Stift- oder Mauseingaben).</span><span class="sxs-lookup"><span data-stu-id="b42b9-114">It is not designed for precision pointer input (like touch, pen, or mouse).</span></span> 

<span data-ttu-id="b42b9-115">Das Surface Dial unterstützt außerdem eine *Drücken-und-Halten*-Aktion und eine *Klick*-Aktion.</span><span class="sxs-lookup"><span data-stu-id="b42b9-115">The Surface Dial also supports both a *press and hold* action and a *click* action.</span></span> <span data-ttu-id="b42b9-116">„Drücken und Halten“ hat nur eine Funktion: die Anzeige eines Befehlsmenüs.</span><span class="sxs-lookup"><span data-stu-id="b42b9-116">Press and hold has a single function: display a menu of commands.</span></span> <span data-ttu-id="b42b9-117">Wenn das Menü aktiv ist, wird die Dreh- und Klickeingabe vom Menü verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-117">If the menu is active, the rotate and click input is processed by the menu.</span></span> <span data-ttu-id="b42b9-118">Andernfalls wird die Eingabe zur Verarbeitung an Ihre App übergeben.</span><span class="sxs-lookup"><span data-stu-id="b42b9-118">Otherwise, the input is passed to your app for processing.</span></span> 

**<span data-ttu-id="b42b9-119">Wie bei allen Windows-Eingabegeräten können die Interaktionen mit dem Surface Dial beliebig an die Funktionalität Ihrer Apps angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-119">As with all Windows input devices, you can customize and tailor the Surface Dial interaction experience to suit the functionality in your apps.</span></span>**

> [!TIP]
> <span data-ttu-id="b42b9-120">Im Zusammenspiel mit dem neuen Surface Studio bietet das Surface Dial Benutzern ein noch innovativeres Bedienerlebnis.</span><span class="sxs-lookup"><span data-stu-id="b42b9-120">Used together, the Surface Dial and the new Surface Studio can provide an even more distinctive user experience.</span></span>  
>
><span data-ttu-id="b42b9-121">Das Surface Dial unterstützt nicht nur die beschriebene Standardmenüaktion „Drücken und Halten“, sondern kann zusätzlich direkt auf dem Bildschirm des Surface Studio platziert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-121">In addition to the default press and hold menu experience described, the Surface Dial can also be placed directly on the screen of the Surface Studio.</span></span> <span data-ttu-id="b42b9-122">Dadurch wird ein spezielles Onscreen-Menü aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-122">This enables a special "on-screen" menu.</span></span> 
>
><span data-ttu-id="b42b9-123">Das System erkennt sowohl die Auflageposition als auch die Begrenzungen des Surface Dial, kann anhand dieser Informationen auf die durch das Gerät verursachte Okklusion reagieren und eine größere Menüversion darstellen, die außen um die Drehsteuerung herum angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-123">By detecting both the contact location and bounds of the Surface Dial, the system uses this info to handle occlusion by the device and display a larger version of the menu that wraps around the outside of the Dial.</span></span> <span data-ttu-id="b42b9-124">Auch die App kann diese Informationen nutzen, um die Benutzeroberfläche an das Vorhandensein des Geräts und dessen beabsichtigte Nutzung anzupassen, z.B. daran, wie der Benutzer seine Hand und seinen Arm platziert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-124">This same info can also be used by your app to adapt the UI for both the presence of the device and its anticipated usage, such as the placement of the user's hand and arm.</span></span>

| <span data-ttu-id="b42b9-125">Offscreen-Menü des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-125">Surface Dial off-screen menu</span></span> | | <span data-ttu-id="b42b9-126">Onscreen-Menü des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-126">Surface Dial on-screen menu</span></span> |
| --- | --- | --- |
| ![Offscreen-Menü des Surface Dial](images/windows-wheel/surface-dial-menu-offscreen.png) | | ![Onscreen-Menü des Surface Dial](images/windows-wheel/surface-dial-menu-onscreen.png) |

## <a name="system-integration"></a><span data-ttu-id="b42b9-129">Systemintegration</span><span class="sxs-lookup"><span data-stu-id="b42b9-129">System integration</span></span>

<span data-ttu-id="b42b9-130">Das Surface Dial ist eng in Windows integriert und unterstützt eine Reihe integrierter Menütools, wie Systemlautstärke, Scrollen, Vergrößern/Verkleinern und Rückgängigmachen/Wiederholen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-130">The Surface Dial is tightly integrated with Windows and supports a set of built-in tools on the menu: system volume, scroll, zoom in/out, and undo/redo.</span></span>

<span data-ttu-id="b42b9-131">Diese integrierten Tools passen sich an den aktuellen Systemkontext an und umfassen:</span><span class="sxs-lookup"><span data-stu-id="b42b9-131">This collection of built-in tools adapts to the current system context to include:</span></span>
- <span data-ttu-id="b42b9-132">Ein Tool für die Systemhelligkeit, wenn der Benutzer mit dem Windows-Desktop arbeitet</span><span class="sxs-lookup"><span data-stu-id="b42b9-132">A system brightness tool when the user is on the Windows Desktop</span></span>
- <span data-ttu-id="b42b9-133">Ein Tool für den vorherigen/nächsten Titel bei der Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="b42b9-133">A previous/next track tool when media is playing</span></span>

<span data-ttu-id="b42b9-134">Das Surface Dial bietet nicht nur allgemeine Plattformunterstützung, sondern ist auch nahtlos in die Windows Ink-Plattformsteuerelemente ([**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) und [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar)) integriert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-134">In addition to this general platform support, the Surface Dial is also tightly integrated with the Windows Ink platform controls ([**InkCanvas**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkCanvas) and [**InkToolbar**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.InkToolbar)).</span></span>

![Surface Dial mit Surface-Stift](images/windows-wheel/dial-and-pen-400px.png)  
*<span data-ttu-id="b42b9-136">Surface Dial mit Surface-Stift</span><span class="sxs-lookup"><span data-stu-id="b42b9-136">Surface Dial with Surface Pen</span></span>*

<span data-ttu-id="b42b9-137">Bei Verwendung mit dem Surface Dial bieten diese Steuerelemente zusätzliche Funktionen, mit denen Freihandattribute geändert und die Linealschablone der Freihandsymbolleiste gesteuert werden können.</span><span class="sxs-lookup"><span data-stu-id="b42b9-137">When used with the Surface Dial, these controls enable additional functionality for modifying ink attributes and controlling the ink toolbar’s ruler stencil.</span></span>

<span data-ttu-id="b42b9-138">Wenn Sie das Surface Dial-Menü in einer Freihandanwendung öffnen, die die Freihandsymbolleiste verwendet, enthält das Menü jetzt Tools zum Steuern des Stifttyps und der Pinselstärke.</span><span class="sxs-lookup"><span data-stu-id="b42b9-138">When you open the Surface Dial Menu in an inking application that uses the ink toolbar, the menu now includes tools for controlling pen type and brush thickness.</span></span> <span data-ttu-id="b42b9-139">Wenn das Lineal aktiviert ist, wird das Menü durch ein entsprechendes Tool ergänzt, durch das das Gerät die Position und den Winkel des Lineals steuern kann.</span><span class="sxs-lookup"><span data-stu-id="b42b9-139">When the ruler is enabled, a corresponding tool is added to the menu that lets the device control the position and angle of the ruler.</span></span>

![Surface Dial-Menü mit Stiftauswahltool für die Windows Ink-Symbolleiste](images/windows-wheel/surface-dial-menu-inktoolbar-pen.png)  
*<span data-ttu-id="b42b9-141">Surface Dial-Menü mit Stiftauswahltool für die Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="b42b9-141">Surface Dial menu with pen selection tool for the Windows Ink toolbar</span></span>*

![Surface Dial-Menü mit Strichgrößentool für die Windows Ink-Symbolleiste](images/windows-wheel/surface-dial-menu-inktoolbar-strokesize.png)  
*<span data-ttu-id="b42b9-143">Surface Dial-Menü mit Strichgrößentool für die Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="b42b9-143">Surface Dial menu with stroke size tool for the Windows Ink toolbar</span></span>*

![Surface Dial-Menü mit Linealtool für die Windows Ink-Symbolleiste](images/windows-wheel/surface-dial-menu-inktoolbar-ruler.png)  
*<span data-ttu-id="b42b9-145">Surface Dial-Menü mit Linealtool für die Windows Ink-Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="b42b9-145">Surface Dial menu with ruler tool for the Windows Ink toolbar</span></span>*

## <a name="user-customization"></a><span data-ttu-id="b42b9-146">Benutzeranpassung</span><span class="sxs-lookup"><span data-stu-id="b42b9-146">User customization</span></span>

<span data-ttu-id="b42b9-147">Benutzer können einige Aspekte der Surface Dial-Bedienung auf der Seite **Windows-Einstellungen -> Geräte -> Rad** anpassen, einschließlich Standardtools, Vibration (oder haptisches Feedback) und schreibende (oder dominante) Hand.</span><span class="sxs-lookup"><span data-stu-id="b42b9-147">Users can customize some aspects of their Dial experience through the **Windows Settings -> Devices -> Wheel** page, including default tools, vibration (or haptic feedback), and writing (or dominant) hand.</span></span> 

<span data-ttu-id="b42b9-148">Beim Anpassen der Benutzererfahrung mit dem Surface Dial sollten Sie immer sicherstellen, dass eine bestimmte Funktion oder ein bestimmtes Verhalten verfügbar ist und vom Benutzer aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-148">When customizing the Surface Dial user experience, you should always ensure that a particular function or behavior is available and enabled by the user.</span></span>

## <a name="custom-tools"></a><span data-ttu-id="b42b9-149">Benutzerdefinierte Tools</span><span class="sxs-lookup"><span data-stu-id="b42b9-149">Custom tools</span></span>

<span data-ttu-id="b42b9-150">Dieses Thema enthält sowohl Erläuterungen zur Benutzeroberfläche als auch Erläuterungen für Entwickler, die sich auf die Anpassung der Tools im Surface Dial-Menü beziehen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-150">Here we discuss both UX and developer guidance for customizing the tools exposed on the Surface Dial menu.</span></span>

### <a name="ux-guidance"></a><span data-ttu-id="b42b9-151">Erläuterungen zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="b42b9-151">UX guidance</span></span>

<span data-ttu-id="b42b9-152">**Achten Sie darauf, dass Ihre Tools dem aktuellen Kontext entsprechen.** Wenn die Funktionsweise eines Tools und die Interaktionsmöglichkeiten mit dem Surface Dial schnell und intuitiv vom Benutzer erfasst werden können, helfen Sie ihm, sich auf seine Arbeit zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-152">**Ensure your tools correspond to the current context** When you make it clear and intuitive what a tool does and how the Surface Dial interaction works, you help users learn quickly and stay focused on their task.</span></span>

**<span data-ttu-id="b42b9-153">Verringern Sie die Anzahl der App-Tools so weit wie möglich.</span><span class="sxs-lookup"><span data-stu-id="b42b9-153">Minimize the number of app tools as much as possible</span></span>**  
<span data-ttu-id="b42b9-154">Das Surface Dial-Menü bietet Platz für sieben Elemente.</span><span class="sxs-lookup"><span data-stu-id="b42b9-154">The Surface Dial menu has room for seven items.</span></span> <span data-ttu-id="b42b9-155">Bei acht oder mehr Elementen muss der Benutzer die Drehsteuerung bedienen, um die verfügbaren Tools in einem Erweiterungsflyout anzuzeigen. Das Navigieren im Menü wird schwieriger, und die verfügbaren Tools sind nicht mehr einfach zu erkennen und auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-155">If there are eight or more items, the user needs to turn the Dial to see which tools are available in an overflow flyout, making the menu difficult to navigate and tools difficult to discover and select.</span></span>

<span data-ttu-id="b42b9-156">Wir empfehlen, ein einzelnes benutzerdefiniertes Tool für Ihre App oder Ihren App-Kontext bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-156">We recommend providing a single custom tool for your app or app context.</span></span> <span data-ttu-id="b42b9-157">Dadurch können Sie das Tool auf Grundlage der aktuellen Benutzeraktion festlegen, ohne dass der Benutzer das Surface Dial-Menü aktivieren und ein Tool auswählen muss.</span><span class="sxs-lookup"><span data-stu-id="b42b9-157">Doing so enables you to set that tool based on what the user is doing without requiring them to activate the Surface Dial menu and select a tool.</span></span> 

**<span data-ttu-id="b42b9-158">Sie sollten die Toolsammlung dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-158">Dynamically update the collection of tools</span></span>**  
<span data-ttu-id="b42b9-159">Da Elemente im deaktivierten Zustand im Surface Dial-Menü nicht unterstützt werden, sollten Sie Tools (einschließlich integrierter Tools und Standardtools) basierend auf dem Benutzerkontext (aktuelle Ansicht oder Fenster im Fokus) dynamisch hinzufügen und entfernen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-159">Because Surface Dial menu items do not support a disabled state, you should dynamically add and remove tools (including built-in, default tools) based on user context (current view or focused window).</span></span> <span data-ttu-id="b42b9-160">Wenn ein Tool für die aktuelle Aktivität nicht relevant oder redundant ist, entfernen Sie es.</span><span class="sxs-lookup"><span data-stu-id="b42b9-160">If a tool is not relevant to the current activity or it’s redundant, remove it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b42b9-161">Wenn Sie dem Menü ein Element hinzufügen, vergewissern Sie sich, dass es nicht bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b42b9-161">When you add an item to the menu, ensure the item does not already exist.</span></span>

**<span data-ttu-id="b42b9-162">Das integrierte Tool zum Einstellen der Systemlautstärke sollte nicht entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-162">Don’t remove the built-in system volume setting tool</span></span>**  
<span data-ttu-id="b42b9-163">Normalerweise benötigt der Benutzer immer eine Lautstärkeregelung.</span><span class="sxs-lookup"><span data-stu-id="b42b9-163">Volume control is typically always required by user.</span></span> <span data-ttu-id="b42b9-164">Da er bei Verwendung Ihrer App u. U. Musik hört, sollten Tools zum Regeln der Lautstärke und zur Auswahl des nächsten Titels immer im Surface Dial-Menü verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="b42b9-164">They might be listening to music while using your app, so volume and next track tools should always be accessible from the Surface Dial menu.</span></span> <span data-ttu-id="b42b9-165">(Wenn Medien wiedergegeben werden, wird dem Menü automatisch das Tool zur Auswahl des nächsten Titels hinzugefügt.)</span><span class="sxs-lookup"><span data-stu-id="b42b9-165">(The next track tool is automatically added to the menu when media is playing.)</span></span>

**<span data-ttu-id="b42b9-166">Achten Sie auf eine einheitliche Menüanordnung.</span><span class="sxs-lookup"><span data-stu-id="b42b9-166">Be consistent with menu organization</span></span>**  
<span data-ttu-id="b42b9-167">Dadurch erkennen Benutzer bei Verwendung Ihrer App leichter, welche Tools verfügbar sind, und können effizienter zwischen Tools wechseln.</span><span class="sxs-lookup"><span data-stu-id="b42b9-167">This helps users with discovering and learning what tools are available when using your app, and helps improve their efficiency when switching tools.</span></span>

**<span data-ttu-id="b42b9-168">Stellen Sie hochwertige, mit den integrierten Symbolen konsistente Symbole bereit.</span><span class="sxs-lookup"><span data-stu-id="b42b9-168">Provide high-quality icons consistent with the built-in icons</span></span>**  
<span data-ttu-id="b42b9-169">Symbole können Benutzern Professionalität, Kompetenz und Vertrauenswürdigkeit vermitteln.</span><span class="sxs-lookup"><span data-stu-id="b42b9-169">Icons can convey professionalism and excellence, and inspire trust in users.</span></span>
- <span data-ttu-id="b42b9-170">Stellen Sie ein hochwertiges PNG-Bild von 64x64 Pixeln bereit (44x44 ist die kleinste unterstützte Größe)</span><span class="sxs-lookup"><span data-stu-id="b42b9-170">Provide a high-quality 64 x 64 pixel PNG image (44 x 44 is the smallest supported)</span></span>
- <span data-ttu-id="b42b9-171">Stellen Sie sicher, dass der Hintergrund transparent ist.</span><span class="sxs-lookup"><span data-stu-id="b42b9-171">Ensure the background is transparent</span></span>
- <span data-ttu-id="b42b9-172">Das Symbol sollte den größten Teil des Bilds ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-172">The icon should fill most of the image</span></span>
- <span data-ttu-id="b42b9-173">Ein weißes Symbol sollte über eine schwarze Kontur verfügen, damit es im Modus mit hohem Kontrast sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="b42b9-173">A white icon should have a black outline to be visible in high contrast mode</span></span>

|   |   |   |
| --- | --- | --- |
| ![Symbol mit Alphahintergrund](images/windows-wheel/surface-dial-menu-icon1.png) | ![Bei Verwendung des Standarddesigns im Radmenü angezeigtes Symbol](images/windows-wheel/surface-dial-menu-icon2.png) | ![Onscreen-Menü des Surface Dial](images/windows-wheel/surface-dial-menu-icon3.png) |
| *<span data-ttu-id="b42b9-177">Symbol mit Alphahintergrund</span><span class="sxs-lookup"><span data-stu-id="b42b9-177">Icon with alpha background</span></span>* | *<span data-ttu-id="b42b9-178">Bei Verwendung des Standarddesigns im Radmenü angezeigtes Symbol</span><span class="sxs-lookup"><span data-stu-id="b42b9-178">Icon displayed on wheel menu with default theme</span></span>* | *<span data-ttu-id="b42b9-179">Bei Verwendung des Designs „Hoher Kontrast (Weiß)“ im Radmenü angezeigtes Symbol</span><span class="sxs-lookup"><span data-stu-id="b42b9-179">Icon displayed on wheel menu with High Contrast White theme</span></span>* |

**<span data-ttu-id="b42b9-180">Verwenden Sie präzise und beschreibende Namen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-180">Use concise and descriptive names</span></span>**  
<span data-ttu-id="b42b9-181">Der Name des Tools wird im Toolmenü zusammen mit dem Toolsymbol angezeigt und auch von Sprachausgaben verwendet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-181">The tool name is displayed in the tool menu along with the tool icon and is also used by screen readers.</span></span> 
- <span data-ttu-id="b42b9-182">Namen sollten kurz sein und in den mittleren Kreis des Radmenüs passen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-182">Names should be short to fit inside the central circle of the wheel menu</span></span>
- <span data-ttu-id="b42b9-183">Namen sollten die primäre Aktion eindeutig identifizieren (eine ergänzende Aktion kann impliziert werden):</span><span class="sxs-lookup"><span data-stu-id="b42b9-183">Names should clearly identify the primary action (a complementary action can be implied):</span></span>
  - <span data-ttu-id="b42b9-184">„Scrollen“ gibt an, dass beide Drehrichtungen unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-184">Scroll indicates the effect of both rotation directions</span></span>
  - <span data-ttu-id="b42b9-185">„Rückgängigmachen“ gibt eine primäre Aktion an, „Wiederholen“ (die ergänzenden Aktion) kann vom Benutzer jedoch problemlos abgeleitet und identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-185">Undo specifies a primary action, but redo (the complementary action) can be inferred and easily discovered by the user</span></span>

### <a name="developer-guidance"></a><span data-ttu-id="b42b9-186">Erläuterungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="b42b9-186">Developer guidance</span></span>

<span data-ttu-id="b42b9-187">Sie können die Funktionsweise des Surface Dial mit einer umfassenden Reihe von [Windows-Runtime-APIs](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) anpassen, um die Funktionalität Ihrer Apps zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="b42b9-187">You can customize the Surface Dial experience to complement the functionality in your apps through a comprehensive set of [Windows Runtime APIs](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController).</span></span> 

<span data-ttu-id="b42b9-188">Wie erwähnt, verfügt das Standardmenü des Surface Dial bereits über mehrere integrierte Tools, die zahlreiche grundlegende Systemfeatures abdecken (Systemlautstärke, Systemhelligkeit, Scrollen, Zoomen, Rückgängigmachen sowie Mediensteuerung, wenn das System erkennt, dass Audio- oder Videomedien wiedergegeben werden).</span><span class="sxs-lookup"><span data-stu-id="b42b9-188">As previously mentioned, the default Surface Dial menu is pre-populated with a set of built-in tools covering a broad range of basic system features (system volume, system brightness, scroll, zoom, undo, and media control when the system detects ongoing audio or video playback).</span></span> <span data-ttu-id="b42b9-189">Möglicherweise stellen diese Standardtools aber nicht die für Ihre App erforderlichen Funktionen bereit.</span><span class="sxs-lookup"><span data-stu-id="b42b9-189">However, these default tools might not provide the functionality required by your app.</span></span> 

<span data-ttu-id="b42b9-190">In den folgenden Abschnitten wird beschrieben, wie Sie dem Surface Dial-Menü ein benutzerdefiniertes Tool hinzufügen und angeben, welche integrierten Tools verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-190">In the following sections, we describe how to add a custom tool to the Surface Dial menu and specify which built-in tools are exposed.</span></span>

**<span data-ttu-id="b42b9-191">Hinzufügen eines benutzerdefinierten Tools</span><span class="sxs-lookup"><span data-stu-id="b42b9-191">Add a custom tool</span></span>**

<span data-ttu-id="b42b9-192">In diesem Beispiel wird ein einfaches benutzerdefiniertes Tool hinzugefügt, das die Eingabedaten sowohl von Drehereignissen als auch von Klickereignissen an einige XAML-UI-Steuerelemente übergibt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-192">In this example, we add a basic custom tool that passes the input data from both the rotation and click events to some XAML UI controls.</span></span>

1. <span data-ttu-id="b42b9-193">Zunächst deklarieren wir unsere Benutzeroberfläche (lediglich ein Schieberegler und eine Umschaltfläche) in XAML.</span><span class="sxs-lookup"><span data-stu-id="b42b9-193">First, we declare our UI (just a slider and toggle button) in XAML.</span></span>

   ![Abbildung: Beispiel der App-UI](images/windows-wheel/surface-dial-snippet-customtool1.png)  
   *<span data-ttu-id="b42b9-195">Beispiel der App-UI</span><span class="sxs-lookup"><span data-stu-id="b42b9-195">The sample app UI</span></span>*

    ```Xaml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*"/>
      </Grid.RowDefinitions>
      <StackPanel x:Name="HeaderPanel" 
        Orientation="Horizontal" 
        Grid.Row="0">
          <TextBlock x:Name="Header"
            Text="RadialController customization sample"
            VerticalAlignment="Center"
            Style="{ThemeResource HeaderTextBlockStyle}"
            Margin="10,0,0,0" />
      </StackPanel>
      <StackPanel Orientation="Vertical" 
        VerticalAlignment="Center" 
        HorizontalAlignment="Center"
        Grid.Row="1">
          <!-- Slider for rotation input -->
          <Slider x:Name="RotationSlider"
            Width="300"
            HorizontalAlignment="Left"/>
          <!-- Switch for click input -->
          <ToggleSwitch x:Name="ButtonToggle"
            HorizontalAlignment="Left"/>
      </StackPanel>
    </Grid>
    ```

2. <span data-ttu-id="b42b9-196">Anschließend fügen wir in der CodeBehind-Datei dem Surface Dial-Menü ein benutzerdefiniertes Tool hinzu und deklarieren die [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController)-Eingabehandler.</span><span class="sxs-lookup"><span data-stu-id="b42b9-196">Then, in code-behind, we add a custom tool to the Surface Dial menu and declare the [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) input handlers.</span></span> 

   <span data-ttu-id="b42b9-197">Wir rufen [**CreateForCurrentView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.CreateForCurrentView) auf, um für das Surface Dial (myController) einen Verweis auf das [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController)-Objekt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b42b9-197">We get a reference to the [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) object for the Surface Dial (myController) by calling [**CreateForCurrentView**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.CreateForCurrentView).</span></span>

   <span data-ttu-id="b42b9-198">Anschließend erstellen wir eine [**RadialControllerMenuItem**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerMenuItem)-Instanz (myItem), indem wir [**RadialControllerMenuItem.CreateFromIcon**](https://msdn.microsoft.com/library/windows/apps/mt759255) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-198">We then create an instance of a [**RadialControllerMenuItem**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerMenuItem) (myItem) by calling [**RadialControllerMenuItem.CreateFromIcon**](https://msdn.microsoft.com/library/windows/apps/mt759255).</span></span> 

   <span data-ttu-id="b42b9-199">Als Nächstes fügen wir das Element an die Sammlung der Menüelemente an.</span><span class="sxs-lookup"><span data-stu-id="b42b9-199">Next, we append that item to the collection of menu items.</span></span>

   <span data-ttu-id="b42b9-200">Wir deklarieren die Eingabeereignishandler ([**ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked) und [**RotationChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationChanged)) für das [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-200">We declare the input event handlers ([**ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked) and [**RotationChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationChanged)) for the [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) object.</span></span>

   <span data-ttu-id="b42b9-201">Zuletzt definieren wir die Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="b42b9-201">Finally, we define the event handlers.</span></span>

    ```csharp
    public sealed partial class MainPage : Page
    {
        RadialController myController;

        public MainPage()
        {
            this.InitializeComponent();
            // Create a reference to the RadialController.
            myController = RadialController.CreateForCurrentView();

            // Create an icon for the custom tool.
            RandomAccessStreamReference icon =
              RandomAccessStreamReference.CreateFromUri(
                new Uri("ms-appx:///Assets/StoreLogo.png"));

            // Create a menu item for the custom tool.
            RadialControllerMenuItem myItem =
              RadialControllerMenuItem.CreateFromIcon("Sample", icon);

            // Add the custom tool to the RadialController menu.
            myController.Menu.Items.Add(myItem);

            // Declare input handlers for the RadialController.
            myController.ButtonClicked += MyController_ButtonClicked;
            myController.RotationChanged += MyController_RotationChanged;
        }

        // Handler for rotation input from the RadialController.
        private void MyController_RotationChanged(RadialController sender,
          RadialControllerRotationChangedEventArgs args)
        {
            if (RotationSlider.Value + args.RotationDeltaInDegrees > 100)
            {
                RotationSlider.Value = 100;
                return;
            }
            else if (RotationSlider.Value + args.RotationDeltaInDegrees < 0)
            {
                RotationSlider.Value = 0;
                return;
            }
            RotationSlider.Value += args.RotationDeltaInDegrees;
        }

        // Handler for click input from the RadialController.
        private void MyController_ButtonClicked(RadialController sender,
          RadialControllerButtonClickedEventArgs args)
        {
            ButtonToggle.IsOn = !ButtonToggle.IsOn;
        }
    }
    ```

<span data-ttu-id="b42b9-202">Wenn wird die App ausführen, verwenden wir das Surface Dial, um mit ihr zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-202">When we run the app, we use the Surface Dial to interact with it.</span></span> <span data-ttu-id="b42b9-203">Zuerst drücken und halten wird das Gerät, um das Menü zu öffnen und unser benutzerdefiniertes Tool auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-203">First, we press and hold to open the menu and select our custom tool.</span></span> <span data-ttu-id="b42b9-204">Sobald das benutzerdefinierte Tool aktiviert ist, kann das Schieberegler-Steuerelement durch Drehen des Surface Dial angepasst werden, und die Umschaltfläche kann durch Klicken mit dem Surface Dial umgeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-204">Once the custom tool is activated, the slider control can be adjusted by rotating the Dial and the switch can be toggled by clicking the Dial.</span></span>

![Abbildung: Beispiel der App-UI, aktiviert mit dem benutzerdefinierten Surface Dial-Tool](images/windows-wheel/surface-dial-snippet-customtool2.png)  
*<span data-ttu-id="b42b9-206">Beispiel der App-UI, aktiviert mit dem benutzerdefinierten Surface Dial-Tool</span><span class="sxs-lookup"><span data-stu-id="b42b9-206">The sample app UI activated using the Surface Dial custom tool</span></span>*

**<span data-ttu-id="b42b9-207">Angeben der integrierten Tools</span><span class="sxs-lookup"><span data-stu-id="b42b9-207">Specify the built-in tools</span></span>**

<span data-ttu-id="b42b9-208">Mit der [**RadialControllerConfiguration**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerConfiguration)-Klasse können Sie die Sammlung integrierter Menüelemente für Ihre App anpassen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-208">You can use the [**RadialControllerConfiguration**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerConfiguration) class to customize the collection of built-in menu items for your app.</span></span>

<span data-ttu-id="b42b9-209">Wenn Ihre App beispielsweise keine Scroll- oder Zoombereiche aufweist und keine Funktionen zum Rückgängigmachen/Wiederholen benötigt, können diese Tools aus dem Menü entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-209">For example, if your app doesn’t have any scrolling or zooming regions and doesn’t require undo/redo functionality, these tools can be removed from the menu.</span></span> <span data-ttu-id="b42b9-210">Dadurch bietet das Menü mehr Platz für benutzerdefinierte Tools in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b42b9-210">This opens space on the menu to add custom tools for your app.</span></span> 

> [!IMPORTANT] 
> <span data-ttu-id="b42b9-211">Das Surface Dial-Menü muss mindestens über ein Menüelement verfügen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-211">The Surface Dial menu must have at least one menu item.</span></span> <span data-ttu-id="b42b9-212">Wenn alle Standardtools entfernt werden, bevor Sie ein benutzerdefiniertes Tools hinzufügen, werden die Standardtools wiederhergestellt, und Ihr Tool wird an die Standardsammlung angefügt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-212">If all default tools are removed before you add one of your custom tools, the default tools are restored and your tool is appended to the default collection.</span></span>

<span data-ttu-id="b42b9-213">Laut Entwurfsrichtlinien wird davon abgeraten, Tools für die Mediensteuerung (Lautstärkeregelung und Wechsel zum nächsten bzw. vorherigen Titel) zu entfernen, da Benutzer häufig Musik im Hintergrund hören, während sie andere Aufgaben erledigen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-213">Per the design guidelines, we do not recommend removing the media control tools (volume and previous/next track) as users often have background music playing while they perform other tasks.</span></span>

<span data-ttu-id="b42b9-214">Hier wird veranschaulicht, wie Sie das Surface Dial-Menü so konfigurieren, dass es nur die Mediensteuerungen für die Lautstärke und den Wechsel zum nächsten bzw. vorherigen Titel enthält.</span><span class="sxs-lookup"><span data-stu-id="b42b9-214">Here, we show how to configure the Surface Dial menu to include only media controls for volume and next/previous track.</span></span>

```csharp
public MainPage()
{
  ...
  //Remove a subset of the default system tools
  RadialControllerConfiguration myConfiguration = 
  RadialControllerConfiguration.GetForCurrentView();
  myConfiguration.SetDefaultMenuItems(new[] 
  {
    RadialControllerSystemMenuItemKind.Volume,
      RadialControllerSystemMenuItemKind.NextPreviousTrack
  });
}
```

## <a name="custom-interactions"></a><span data-ttu-id="b42b9-215">Benutzerdefinierte Interaktionen</span><span class="sxs-lookup"><span data-stu-id="b42b9-215">Custom interactions</span></span>

<span data-ttu-id="b42b9-216">Wie bereits erwähnt, unterstützt das Surface Dial drei Bewegungen (Drücken und Halten, Drehen, Klicken) mit den zugehörigen Standardinteraktionen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-216">As mentioned, the Surface Dial supports three gestures (press and hold, rotate, click) with corresponding default interactions.</span></span> 

<span data-ttu-id="b42b9-217">Stellen Sie sicher, dass benutzerdefinierte Interaktionen, die auf diesen Bewegungen basieren, für die ausgewählte Aktion oder das ausgewählte Tool sinnvoll sind.</span><span class="sxs-lookup"><span data-stu-id="b42b9-217">Ensure any custom interactions based on these gestures make sense for the selected action or tool.</span></span> 

> [!NOTE]
> <span data-ttu-id="b42b9-218">Die Verarbeitung der Interaktionen richtet sich nach dem Zustand des Surface Dial-Menüs.</span><span class="sxs-lookup"><span data-stu-id="b42b9-218">The interaction experience is dependent on the state of the Surface Dial menu.</span></span> <span data-ttu-id="b42b9-219">Falls aktiv, wird die Eingabe vom Menü verarbeitet, andernfalls von Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b42b9-219">If the menu is active, it processes the input; otherwise, your app does.</span></span>

### <a name="press-and-hold"></a><span data-ttu-id="b42b9-220">Drücken und Halten</span><span class="sxs-lookup"><span data-stu-id="b42b9-220">Press and hold</span></span>

<span data-ttu-id="b42b9-221">Durch diese Bewegung wird das Surface Dial-Menü aktiviert und angezeigt. Dieser Bewegung ist keine App-Funktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-221">This gesture activates and shows the Surface Dial menu, there is no app functionality associated with this gesture.</span></span> 

<span data-ttu-id="b42b9-222">Das Menü wird standardmäßig mittig auf dem Bildschirms des Benutzers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-222">By default, the menu is displayed at the center of the user’s screen.</span></span> <span data-ttu-id="b42b9-223">Der Benutzer kann es jedoch an eine beliebige andere Stelle verschieben.</span><span class="sxs-lookup"><span data-stu-id="b42b9-223">However, the user can grab it and move it anywhere they choose.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-224">Wenn das Surface Dial auf dem Bildschirm des Surface Studio platziert wird, wird das Menü an der Onscreen-Position des Surface Dial zentriert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-224">When the Surface Dial is placed on the screen of the Surface Studio, the menu is centered at the on-screen location of the Surface Dial.</span></span>

### <a name="rotate"></a><span data-ttu-id="b42b9-225">Drehen</span><span class="sxs-lookup"><span data-stu-id="b42b9-225">Rotate</span></span>

<span data-ttu-id="b42b9-226">Die vom Surface Dial unterstützten Drehungen eignen sich hauptsächlich für Interaktionen, mit denen analoge Werte oder Steuerungen stufenlos inkrementiert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-226">The Surface Dial is primarily designed to support rotation for interactions that involve smooth, incremental adjustments to analog values or controls.</span></span>

<span data-ttu-id="b42b9-227">Das Gerät kann im Uhrzeigersinn und gegen den Uhrzeigersinn gedreht werden und mittels haptischem Feedback diskrete Entfernungen angeben.</span><span class="sxs-lookup"><span data-stu-id="b42b9-227">The device can be rotated both clockwise and counter-clockwise, and can also provide haptic feedback to indicate discrete distances.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-228">Haptisches Feedback kann vom Benutzer auf der Seite **Windows-Einstellungen -> Geräte -> Rad** deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-228">Haptic feedback can be disabled by the user in the **Windows Settings -> Devices -> Wheel** page.</span></span>

#### <a name="ux-guidance"></a><span data-ttu-id="b42b9-229">Erläuterungen zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="b42b9-229">UX guidance</span></span>

**<span data-ttu-id="b42b9-230">Für Tools mit kontinuierlicher oder hoher Drehempfindlichkeit sollte haptisches Feedback deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-230">Tools with continuous or high rotational sensitivity should disable haptic feedback</span></span>**

<span data-ttu-id="b42b9-231">Das haptische Feedback entspricht der Drehempfindlichkeit des aktiven Tools.</span><span class="sxs-lookup"><span data-stu-id="b42b9-231">Haptic feedback matches the rotational sensitivity of the active tool.</span></span> <span data-ttu-id="b42b9-232">Es wird empfohlen, haptisches Feedback für Tools mit kontinuierlicher oder hoher Drehempfindlichkeit zu deaktivieren, da andernfalls die Benutzerfreundlichkeit beeinträchtigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b42b9-232">We recommend disabling haptic feedback for tools with continuous or high rotational sensitivity as the user experience can get uncomfortable.</span></span> 

**<span data-ttu-id="b42b9-233">Interaktionen, die auf Drehungen basieren, sollten nicht durch die dominante Hand beeinflusst werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-233">Dominant hand should not affect rotation-based interactions</span></span>**

<span data-ttu-id="b42b9-234">Das Surface Dial erkennt nicht, welche Hand verwendet wird. Der Benutzer kann die schreibende (oder dominante) Hand jedoch unter **Windows-Einstellungen -> Gerät -> Stift & Windows Ink** festlegen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-234">The Surface Dial cannot detect which hand is being used, but the user can set the writing (or dominant hand) in **Windows Settings -> Device -> Pen & Windows Ink**.</span></span>

**<span data-ttu-id="b42b9-235">Bei allen Drehinteraktionen sollte das Gebietsschema berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-235">Locale should be considered for all rotation interactions</span></span>**

<span data-ttu-id="b42b9-236">Erhöhen Sie die Kundenzufriedenheit, indem Sie Interaktionen an das jeweilige Gebietsschema und Rechts-nach-links-Layouts anpassen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-236">Maximize customer satisfaction by accomodating and adapting your interactions to locale and right-to-left layouts.</span></span>

<span data-ttu-id="b42b9-237">Folgende Richtlinien für drehbasierte Aktionen gelten für die integrierten Tools und Befehle im Surface Dial-Menü:</span><span class="sxs-lookup"><span data-stu-id="b42b9-237">The built-in tools and commands on the Dial menu follow these guidelines for rotation-based interactions:</span></span>

|   |   |   |
| --- | --- | --- |
| <span data-ttu-id="b42b9-238">Links</span><span class="sxs-lookup"><span data-stu-id="b42b9-238">Left</span></span><br/><span data-ttu-id="b42b9-239">Oben</span><span class="sxs-lookup"><span data-stu-id="b42b9-239">Up</span></span><br/><span data-ttu-id="b42b9-240">Heraus</span><span class="sxs-lookup"><span data-stu-id="b42b9-240">Out</span></span> | ![Abbildung: Surface Dial](images/windows-wheel/surface-dial-rotate.png) | <span data-ttu-id="b42b9-242">Rechts</span><span class="sxs-lookup"><span data-stu-id="b42b9-242">Right</span></span><br/><span data-ttu-id="b42b9-243">Unten</span><span class="sxs-lookup"><span data-stu-id="b42b9-243">Down</span></span><br/><span data-ttu-id="b42b9-244">Hinein</span><span class="sxs-lookup"><span data-stu-id="b42b9-244">In</span></span> |
|   |   |   |

| <span data-ttu-id="b42b9-245">Konzeptionelle Richtung</span><span class="sxs-lookup"><span data-stu-id="b42b9-245">Conceptual direction</span></span> | <span data-ttu-id="b42b9-246">Zuordnung des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-246">Mapping to Surface Dial</span></span> | <span data-ttu-id="b42b9-247">Drehung im Uhrzeigersinn</span><span class="sxs-lookup"><span data-stu-id="b42b9-247">Clockwise rotation</span></span> | <span data-ttu-id="b42b9-248">Drehung gegen den Uhrzeigersinn</span><span class="sxs-lookup"><span data-stu-id="b42b9-248">Counter-clockwise rotation</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b42b9-249">Horizontal</span><span class="sxs-lookup"><span data-stu-id="b42b9-249">Horizontal</span></span> | <span data-ttu-id="b42b9-250">Links/Rechts-Zuordnung ausgehend von der Oberseite des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-250">Left and right mapping based on the top of the Surface Dial</span></span> | <span data-ttu-id="b42b9-251">Rechts</span><span class="sxs-lookup"><span data-stu-id="b42b9-251">Right</span></span> | <span data-ttu-id="b42b9-252">Links</span><span class="sxs-lookup"><span data-stu-id="b42b9-252">Left</span></span> |
| <span data-ttu-id="b42b9-253">Vertikal</span><span class="sxs-lookup"><span data-stu-id="b42b9-253">Vertical</span></span> | <span data-ttu-id="b42b9-254">Oben/Unten-Zuordnung ausgehend von der linken Seite des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-254">Up and down mapping based on the left side of the Surface Dial</span></span> | <span data-ttu-id="b42b9-255">Unten</span><span class="sxs-lookup"><span data-stu-id="b42b9-255">Down</span></span> | <span data-ttu-id="b42b9-256">Oben</span><span class="sxs-lookup"><span data-stu-id="b42b9-256">Up</span></span> |
| <span data-ttu-id="b42b9-257">Z-Achse</span><span class="sxs-lookup"><span data-stu-id="b42b9-257">Z-axis</span></span> | <span data-ttu-id="b42b9-258">Hinein (oder näher) wird Oben/Rechts zugeordnet</span><span class="sxs-lookup"><span data-stu-id="b42b9-258">In (or nearer) mapped to up/right</span></span><br/><span data-ttu-id="b42b9-259">Heraus (oder weiter) wird Unten/Links zugeordnet</span><span class="sxs-lookup"><span data-stu-id="b42b9-259">Out (or further) mapped to down/left</span></span> | <span data-ttu-id="b42b9-260">Hinein</span><span class="sxs-lookup"><span data-stu-id="b42b9-260">In</span></span> | <span data-ttu-id="b42b9-261">Heraus</span><span class="sxs-lookup"><span data-stu-id="b42b9-261">Out</span></span> |

#### <a name="developer-guidance"></a><span data-ttu-id="b42b9-262">Erläuterungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="b42b9-262">Developer guidance</span></span>

<span data-ttu-id="b42b9-263">Während der Benutzer das Gerät dreht, werden [**RadialController.RotationChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationChanged)-Ereignisse auf Grundlage eines Deltas([**RadialControllerRotationChangedEventArgs.RotationDeltaInDegrees**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerRotationChangedEventArgs.RotationDeltaInDegrees)) relativ zur Drehrichtung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b42b9-263">As the user rotates the device, [**RadialController.RotationChanged**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationChanged) events are fired based on a delta ([**RadialControllerRotationChangedEventArgs.RotationDeltaInDegrees**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerRotationChangedEventArgs.RotationDeltaInDegrees)) relative to the direction of rotation.</span></span> <span data-ttu-id="b42b9-264">Die Empfindlichkeit (oder Auflösung) der Daten kann mit der [**RadialController.RotationResolutionInDegrees**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationResolutionInDegrees)-Eigenschaft festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-264">The sensitivity (or resolution) of the data can be set with the [**RadialController.RotationResolutionInDegrees**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.RotationResolutionInDegrees) property.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-265">Ein Eingabeereignis für Drehungen wird standardmäßig nur an ein [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController)-Objekt übergeben, wenn das Gerät mindestens um 10Grad gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-265">By default, a rotational input event is delivered to a [**RadialController**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController) object only when the device is rotated a minimum of 10 degrees.</span></span> <span data-ttu-id="b42b9-266">Das Gerät vibriert bei jedem Eingabeereignis.</span><span class="sxs-lookup"><span data-stu-id="b42b9-266">Each input event causes the device to vibrate.</span></span>

<span data-ttu-id="b42b9-267">Im Allgemeinen wird empfohlen, haptisches Feedback zu deaktivieren, wenn die Drehauflösung auf weniger als 5Grad festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b42b9-267">In general, we recommend disabling haptic feedback when the rotation resolution is set to less than 5 degrees.</span></span> <span data-ttu-id="b42b9-268">Dadurch können kontinuierliche Interaktionen reibungsloser ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-268">This provides a smoother experience for continuous interactions.</span></span> 

<span data-ttu-id="b42b9-269">Sie können haptisches Feedback für benutzerdefinierte Tools aktivieren und deaktivieren, indem Sie die [**RadialController.UseAutomaticHapticFeedback**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.UseAutomaticHapticFeedback)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-269">You can enable and disable haptic feedback for custom tools by setting the [**RadialController.UseAutomaticHapticFeedback**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.UseAutomaticHapticFeedback) property.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-270">Für Systemtools wie die Lautstärkeregelung kann das haptische Verhalten nicht überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-270">You cannot override the haptic behavior for system tools such as the volume control.</span></span> <span data-ttu-id="b42b9-271">Für diese Tools kann das haptische Feedback nur durch den Benutzer über die Einstellungsseite „Rad“ deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-271">For these tools, haptic feedback can be disabled only by the user from the wheel settings page.</span></span>

<span data-ttu-id="b42b9-272">Das folgende Beispiel veranschaulicht, wie die Auflösung der Drehdaten angepasst und haptisches Feedback aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-272">Here’s an example of how to customize the resolution of the rotation data and enable or disable haptic feedback.</span></span>

```csharp
private void MyController_ButtonClicked(RadialController sender, 
  RadialControllerButtonClickedEventArgs args)
{
  ButtonToggle.IsOn = !ButtonToggle.IsOn;

  if(ButtonToggle.IsOn)
  {
    //high resolution mode
    RotationSlider.LargeChange = 1;
    myController.UseAutomaticHapticFeedback = false;
    myController.RotationResolutionInDegrees = 1;
  }
  else
  {
    //low resolution mode
    RotationSlider.LargeChange = 10;
    myController.UseAutomaticHapticFeedback = true;
    myController.RotationResolutionInDegrees = 10;
  }
}
```

### <a name="click"></a><span data-ttu-id="b42b9-273">Klicken</span><span class="sxs-lookup"><span data-stu-id="b42b9-273">Click</span></span>

<span data-ttu-id="b42b9-274">Das Klicken mit dem Surface Dial ähnelt dem Klicken mit der linken Maustaste (der Drehzustand des Geräts hat keinen Einfluss auf diese Aktion).</span><span class="sxs-lookup"><span data-stu-id="b42b9-274">Clicking the Surface Dial is similar to clicking the left mouse button (the rotation state of the device has no effect on this action).</span></span>

#### <a name="ux-guidance"></a><span data-ttu-id="b42b9-275">Erläuterungen zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="b42b9-275">UX guidance</span></span>

**<span data-ttu-id="b42b9-276">Dieser Bewegung dürfen keine Aktionen oder Befehle zugeordnet werden, die der Benutzer nicht problemlos rückgängig machen kann.</span><span class="sxs-lookup"><span data-stu-id="b42b9-276">Do not map an action or command to this gesture if the user cannot easily recover from the result</span></span>**

<span data-ttu-id="b42b9-277">Jede Aktion, die in der App ausgeführt wird, weil der Benutzer mit dem Surface Dial klickt, muss umkehrbar sein.</span><span class="sxs-lookup"><span data-stu-id="b42b9-277">Any action taken by your app based on the user clicking the Surface Dial must be reversible.</span></span> <span data-ttu-id="b42b9-278">Der Benutzer sollte den Back-Stapel der App immer problemlos durchlaufen und einen früheren App-Zustand wiederherstellen können.</span><span class="sxs-lookup"><span data-stu-id="b42b9-278">Always enable the user to easily traverse the app back stack and restore a previous app state.</span></span>

<span data-ttu-id="b42b9-279">Bei binären Vorgängen wie „Stummschalten/Stummschaltung aufheben“ oder „Ein-/Ausblenden“ funktioniert die Klickbewegung optimal.</span><span class="sxs-lookup"><span data-stu-id="b42b9-279">Binary operations such as mute/unmute or show/hide provide good user experiences with the click gesture.</span></span>

**<span data-ttu-id="b42b9-280">Modale Tools sollten nicht durch Klicken mit dem Surface Dial aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-280">Modal tools should not be enabled or disabled by clicking the Surface Dial</span></span>**

<span data-ttu-id="b42b9-281">Einige App-/Toolmodi können Konflikte mit Interaktionen verursachen, die auf Drehungen basieren, oder diese deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-281">Some app/tool modes can conflict with, or disable, interactions that rely on rotation.</span></span> <span data-ttu-id="b42b9-282">Tools wie das Lineal in der Windows Ink-Symbolleiste sollten durch andere UI-Angebote ein- oder ausgeblendet werden (die Freihandsymbolleiste bietet ein integriertes [**ToggleButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.Primitives.ToggleButton)-Steuerelement).</span><span class="sxs-lookup"><span data-stu-id="b42b9-282">Tools such as the ruler in the Windows Ink toolbar, should be toggled on or off through other UI affordances (the Ink Toolbar provides a built-in [**ToggleButton**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.Primitives.ToggleButton) control).</span></span>

<span data-ttu-id="b42b9-283">Ordnen Sie bei modalen Tools das aktive Surface Dial-Menüelement dem Zieltool oder dem zuvor ausgewählten Menüelement zu.</span><span class="sxs-lookup"><span data-stu-id="b42b9-283">For modal tools, map the active Surface Dial menu item to the target tool or to the previously selected menu item.</span></span>

#### <a name="developer-guidance"></a><span data-ttu-id="b42b9-284">Erläuterungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="b42b9-284">Developer guidance</span></span>

<span data-ttu-id="b42b9-285">Beim Klicken mit dem Surface Dial wird ein [**RadialController.ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked)-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b42b9-285">When the Surface Dial is clicked, a [**RadialController.ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked) event is fired.</span></span> <span data-ttu-id="b42b9-286">[**RadialControllerButtonClickedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs) umfassen eine [**Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs.Contact)-Eigenschaft, die die Position und den Begrenzungsbereich der Surface Dial-Auflagefläche auf dem Surface Studio-Bildschirm enthält.</span><span class="sxs-lookup"><span data-stu-id="b42b9-286">The [**RadialControllerButtonClickedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs) include a [**Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs.Contact) property that contains the location and bounding area of the Surface Dial contact on the Surface Studio screen.</span></span> <span data-ttu-id="b42b9-287">Wenn das Surface Dial keinen Kontakt mit dem Bildschirm hat, ist diese Eigenschaft NULL.</span><span class="sxs-lookup"><span data-stu-id="b42b9-287">If the Surface Dial is not in contact with the screen, this property is null.</span></span> 

### <a name="on-screen"></a><span data-ttu-id="b42b9-288">Onscreen-Modus</span><span class="sxs-lookup"><span data-stu-id="b42b9-288">On-screen</span></span>

<span data-ttu-id="b42b9-289">Wie oben beschrieben, kann das Surface Dial in Verbindung mit dem Surface Studio verwendet werden, um das Surface Dial-Menü in einem speziellen Onscreen-Modus anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-289">As described earlier, the Surface Dial can be used in conjunction with the Surface Studio to display the Surface Dial menu in a special on-screen mode.</span></span> 

<span data-ttu-id="b42b9-290">In diesem Modus können die Interaktionsfunktionen zwischen Surface Dial und Ihren Apps noch weiter integriert und angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-290">When in this mode, you can integrate and customize your Dial interaction experiences with your apps even further.</span></span> <span data-ttu-id="b42b9-291">Beispiele für einzigartige Funktionen, die nur durch das Surface Dial in Kombination mit dem Surface Studio ermöglicht werden:</span><span class="sxs-lookup"><span data-stu-id="b42b9-291">Examples of unique experiences only possible with the Surface Dial and Surface Studio include:</span></span>
- <span data-ttu-id="b42b9-292">Anzeigen kontextbezogener Tools (z.B. einer Farbpalette) abhängig von der Position des Surface Dial, wodurch die Tools leichter zu finden und zu verwenden sind</span><span class="sxs-lookup"><span data-stu-id="b42b9-292">Displaying contextual tools (such as a color palette) based on the position of the Surface Dial, which makes them easier to find and use</span></span>
- <span data-ttu-id="b42b9-293">Festlegen des aktiven Tools auf Grundlage der Benutzeroberfläche, auf der das Surface Dial platziert wird</span><span class="sxs-lookup"><span data-stu-id="b42b9-293">Setting the active tool based on the UI the Surface Dial is placed on</span></span>
- <span data-ttu-id="b42b9-294">Vergrößern eines Bildschirmbereichs basierend auf der Position des Surface Dial</span><span class="sxs-lookup"><span data-stu-id="b42b9-294">Magnifying a screen area based on location of the Surface Dial</span></span>
- <span data-ttu-id="b42b9-295">Einzigartige Spielinteraktionen basierend auf der Position auf dem Bildschirm</span><span class="sxs-lookup"><span data-stu-id="b42b9-295">Unique game interactions based on screen location</span></span>

#### <a name="ux-guidance"></a><span data-ttu-id="b42b9-296">Erläuterungen zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="b42b9-296">UX guidance</span></span>

**<span data-ttu-id="b42b9-297">Apps sollten reagieren, wenn das Surface Dial auf dem Bildschirm erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-297">Apps should respond when the Surface Dial is detected on-screen</span></span>**

<span data-ttu-id="b42b9-298">Visuelles Feedback weist Benutzer darauf hin, dass das Gerät auf dem Bildschirm des Surface Studio von Ihrer App erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="b42b9-298">Visual feedback helps indicate to users that your app has detected the device on the screen of the Surface Studio.</span></span>

**<span data-ttu-id="b42b9-299">Passen Sie UI-Elemente, die sich auf das Surface Dial beziehen, basierend auf der Geräteposition an.</span><span class="sxs-lookup"><span data-stu-id="b42b9-299">Adjust Surface Dial-related UI based on device location</span></span>**

<span data-ttu-id="b42b9-300">Je nachdem, wo das Gerät platziert wird, können wichtige UI-Elemente durch das Gerät selbst (oder durch den Benutzer) verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-300">The device (and the user's body) can occlude critical UI depending on where the user places it.</span></span>

**<span data-ttu-id="b42b9-301">Passen Sie UI-Elemente, die sich auf das Surface Dial beziehen, basierend auf der Benutzerinteraktion an.</span><span class="sxs-lookup"><span data-stu-id="b42b9-301">Adjust Surface Dial-related UI based on user interaction</span></span>**

<span data-ttu-id="b42b9-302">Bei Verwendung des Geräts können Teile des Bildschirms nicht nur durch die Hardware, sondern auch durch die Hand und den Arm des Benutzers verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-302">In addition to hardware occlusion, a user’s hand and arm can occlude part of the screen when using the device.</span></span> 

<span data-ttu-id="b42b9-303">Welcher Bereich verdeckt wird, hängt davon ab, mit welcher Hand das Gerät bedient wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-303">The occluded area depends on which hand is being used with the device.</span></span> <span data-ttu-id="b42b9-304">Da das Gerät hauptsächlich mit der nicht dominanten Hand bedient werden soll, müssen Surface Dial-bezogene UI-Elemente für die vom Benutzer angegebene entgegengesetzte Hand angepasst werden (Einstellung unter **Windows-Einstellungen > Geräte > Stift & Windows Ink > Schreibhand auswählen**).</span><span class="sxs-lookup"><span data-stu-id="b42b9-304">As the device is designed to be used primarily with the non-dominant hand, Surface Dial-related UI should adjust for the opposite hand specified by the user (**Windows Settings > Devices > Pen & Windows Ink > Choose which hand you write with** setting).</span></span>

**<span data-ttu-id="b42b9-305">Interaktionen sollten auf die Position und nicht auf das Verschieben des Surface Dial reagieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-305">Interactions should respond to Surface Dial position rather than movement</span></span>**

<span data-ttu-id="b42b9-306">Der Gerätefuß ist so konzipiert, dass er auf dem Bildschirm haftet anstatt zu gleiten, da es sich nicht um ein Präzisionszeigegerät handelt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-306">The foot of the device is designed to stick to the screen rather than slide, as it is not a precision pointing device.</span></span> <span data-ttu-id="b42b9-307">Aus diesem Grund erwarten wir, dass Benutzer das Surface Dial eher anheben und an einer anderen Stelle platzieren, anstatt es über den Bildschirm zu ziehen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-307">Therefore, we expect it to be more common for users to lift and place the Surface Dial rather than drag it across the screen.</span></span>

**<span data-ttu-id="b42b9-308">Nutzen Sie die Bildschirmposition, um zu bestimmen, was der Benutzer beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-308">Use screen position to determine user intent</span></span>**

<span data-ttu-id="b42b9-309">Wenn Sie das aktive Tool in Abhängigkeit vom UI-Kontext festlegen, z.B. von der Nähe zu einem Steuerelement, Zeichenbereich oder Fenster, können Sie die Benutzerfreundlichkeit verbessern, da sich die zum Ausführen einer Aufgabe erforderlichen Schritte verringern.</span><span class="sxs-lookup"><span data-stu-id="b42b9-309">Setting the active tool based on UI context, such as proximity to a control, canvas, or window, can improve the user experience by reducing the steps required to perform a task.</span></span>

#### <a name="developer-guidance"></a><span data-ttu-id="b42b9-310">Erläuterungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="b42b9-310">Developer guidance</span></span>

<span data-ttu-id="b42b9-311">Wenn das Surface Dial auf der Digitalisiereroberfläche des Surface Studio platziert wird, wird ein [**RadialController.ScreenContactStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ScreenContactStarted)-Ereignis ausgelöst, und die Informationen zum Bildschirmkontakt([**RadialControllerScreenContactStartedEventArgs.Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContactStartedEventArgs.Contact)) werden an die App übermittelt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-311">When the Surface Dial is placed onto the digitizer surface of the Surface Studio, a [**RadialController.ScreenContactStarted**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ScreenContactStarted) event is fired and the contact info ([**RadialControllerScreenContactStartedEventArgs.Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContactStartedEventArgs.Contact)) is provided to your app.</span></span>

<span data-ttu-id="b42b9-312">Auch, wenn mit dem Surface Dial geklickt wird, während es sich auf der Digitalisiereroberfläche des Surface Studio befindet, wird ein [**RadialController.ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked)-Ereignis ausgelöst, und die Informationen zum Bildschirmkontakt ([**RadialControllerButtonClickedEventArgs.Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs.Contact)) werden an die App übermittelt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-312">Similarly, if the Surface Dial is clicked when in contact with the digitizer surface of the Surface Studio, a [**RadialController.ButtonClicked**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController.ButtonClicked) event is fired and the contact info ([**RadialControllerButtonClickedEventArgs.Contact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs.Contact)) is provided to your app.</span></span> 

<span data-ttu-id="b42b9-313">Die Informationen zum Bildschirmkontakt ([**RadialControllerScreenContact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact)) enthalten die X/Y-Koordinate für die Mitte des Surface Dial im Koordinatenbereich der App ([**RadialControllerScreenContact.Position**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact.Position)) und das umgebende Rechteck ([**RadialControllerScreenContact.Bounds**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact.Bounds)) in geräteunabhängigen Pixeln (DIPs).</span><span class="sxs-lookup"><span data-stu-id="b42b9-313">The contact info ([**RadialControllerScreenContact**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact)) includes the X/Y coordinate of the center of the Surface Dial in the coordinate space of the app ([**RadialControllerScreenContact.Position**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact.Position)), as well as the bounding rectangle ([**RadialControllerScreenContact.Bounds**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact.Bounds)) in Device Independent Pixels (DIPs).</span></span> <span data-ttu-id="b42b9-314">Diese Informationen sind sehr hilfreich, wenn es darum geht, Kontext für das aktive Tool bereitzustellen und dem Benutzer gerätebezogenes visuelles Feedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="b42b9-314">This info is very useful for providing context to the active tool and providing device-related visual feedback to the user.</span></span>

<span data-ttu-id="b42b9-315">Im folgenden Beispiel haben wir eine grundlegende App mit vier verschiedenen Abschnitten erstellt. Jeder Abschnitt enthält einen Schieberegler und eine Umschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="b42b9-315">In the following example, we’ve created a basic app with four different sections, each of which includes one slider and one toggle.</span></span> <span data-ttu-id="b42b9-316">Anschließend bestimmen wir ausgehend von der Bildschirmposition des Surface Dial, welche Gruppe von Schieberegler und Umschaltfläche durch das Surface Dial gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-316">We then use the onscreen position of the Surface Dial to dictate which set of sliders and toggles are controlled by the Surface Dial.</span></span>

1. <span data-ttu-id="b42b9-317">Zunächst deklarieren wir die Benutzeroberfläche (vier Abschnitte, die jeweils einen Schieberegler und eine Umschaltfläche enthalten) in XAML.</span><span class="sxs-lookup"><span data-stu-id="b42b9-317">First, we declare our UI (four sections, each with a slider and toggle button) in XAML.</span></span>

   ![Abbildung: Beispiel der App-UI](images/windows-wheel/surface-dial-snippet-customtool3.png)  
   *<span data-ttu-id="b42b9-319">Beispiel der App-UI</span><span class="sxs-lookup"><span data-stu-id="b42b9-319">The sample app UI</span></span>*

   ```xaml 
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
  <Grid.RowDefinitions>
    <RowDefinition Height="Auto"/>
    <RowDefinition Height="*"/>
  </Grid.RowDefinitions>
  <StackPanel x:Name="HeaderPanel" 
        Orientation="Horizontal" 
        Grid.Row="0">
    <TextBlock x:Name="Header"
      Text="RadialController customization sample"
      VerticalAlignment="Center"
      Style="{ThemeResource HeaderTextBlockStyle}"
      Margin="10,0,0,0" />
  </StackPanel>
  <Grid Grid.Row="1" x:Name="RootGrid">
    <Grid.RowDefinitions>
      <RowDefinition Height="*"/>
      <RowDefinition Height="*"/>
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
      <ColumnDefinition Width="*"/>
      <ColumnDefinition Width="*"/>
    </Grid.ColumnDefinitions>
    <Grid x:Name="Grid0"
      Grid.Row="0"
      Grid.Column="0">
      <StackPanel Orientation="Vertical" 
        VerticalAlignment="Center" 
        HorizontalAlignment="Center">
        <!-- Slider for rotational input -->
        <Slider x:Name="RotationSlider0"
          Width="300"
          HorizontalAlignment="Left"/>
        <!-- Switch for button input -->
        <ToggleSwitch x:Name="ButtonToggle0"
            HorizontalAlignment="Left"/>
      </StackPanel>
    </Grid>
    <Grid x:Name="Grid1"
      Grid.Row="0"
      Grid.Column="1">
      <StackPanel Orientation="Vertical" 
        VerticalAlignment="Center" 
        HorizontalAlignment="Center">
        <!-- Slider for rotational input -->
        <Slider x:Name="RotationSlider1"
          Width="300"
          HorizontalAlignment="Left"/>
        <!-- Switch for button input -->
        <ToggleSwitch x:Name="ButtonToggle1"
            HorizontalAlignment="Left"/>
      </StackPanel>
    </Grid>
    <Grid x:Name="Grid2"
      Grid.Row="1"
      Grid.Column="0">
      <StackPanel Orientation="Vertical" 
        VerticalAlignment="Center" 
        HorizontalAlignment="Center">
        <!-- Slider for rotational input -->
        <Slider x:Name="RotationSlider2"
          Width="300"
          HorizontalAlignment="Left"/>
        <!-- Switch for button input -->
        <ToggleSwitch x:Name="ButtonToggle2"
            HorizontalAlignment="Left"/>
      </StackPanel>
    </Grid>
    <Grid x:Name="Grid3"
      Grid.Row="1"
      Grid.Column="1">
      <StackPanel Orientation="Vertical" 
        VerticalAlignment="Center" 
        HorizontalAlignment="Center">
        <!-- Slider for rotational input -->
        <Slider x:Name="RotationSlider3"
          Width="300"
          HorizontalAlignment="Left"/>
        <!-- Switch for button input -->
        <ToggleSwitch x:Name="ButtonToggle3"
            HorizontalAlignment="Left"/>
      </StackPanel>
    </Grid>
  </Grid>
</Grid>
   ```

2. <span data-ttu-id="b42b9-320">Hier der CodeBehind mit definierten Handlern für die Bildschirmposition des Surface Dial.</span><span class="sxs-lookup"><span data-stu-id="b42b9-320">Here's the code-behind with handlers defined for Surface Dial screen position.</span></span>

```csharp
Slider ActiveSlider;
ToggleSwitch ActiveSwitch;
Grid ActiveGrid;

public MainPage()
{
  ...

  myController.ScreenContactStarted += 
    MyController_ScreenContactStarted;
  myController.ScreenContactContinued += 
    MyController_ScreenContactContinued;
  myController.ScreenContactEnded += 
    MyController_ScreenContactEnded;
  myController.ControlLost += MyController_ControlLost;

  //Set initial grid for Surface Dial input.
  ActiveGrid = Grid0;
  ActiveSlider = RotationSlider0;
  ActiveSwitch = ButtonToggle0;
}

private void MyController_ScreenContactStarted(RadialController sender, 
  RadialControllerScreenContactStartedEventArgs args)
{
  //find grid at contact location, update visuals, selection
  ActivateGridAtLocation(args.Contact.Position);
}

private void MyController_ScreenContactContinued(RadialController sender, 
  RadialControllerScreenContactContinuedEventArgs args)
{
  //if a new grid is under contact location, update visuals, selection
  if (!VisualTreeHelper.FindElementsInHostCoordinates(
    args.Contact.Position, RootGrid).Contains(ActiveGrid))
  {
    ActiveGrid.Background = new 
      SolidColorBrush(Windows.UI.Colors.White);
    ActivateGridAtLocation(args.Contact.Position);
  }
}

private void MyController_ScreenContactEnded(RadialController sender, object args)
{
  //return grid color to normal when contact leaves screen
  ActiveGrid.Background = new 
  SolidColorBrush(Windows.UI.Colors.White);
}

private void MyController_ControlLost(RadialController sender, object args)
{
  //return grid color to normal when focus lost
  ActiveGrid.Background = new 
    SolidColorBrush(Windows.UI.Colors.White);
}

private void ActivateGridAtLocation(Point Location)
{
  var elementsAtContactLocation = 
    VisualTreeHelper.FindElementsInHostCoordinates(Location, 
      RootGrid);

  foreach (UIElement element in elementsAtContactLocation)
  {
    if (element as Grid == Grid0)
    {
      ActiveSlider = RotationSlider0;
      ActiveSwitch = ButtonToggle0;
      ActiveGrid = Grid0;
      ActiveGrid.Background = new SolidColorBrush( 
        Windows.UI.Colors.LightGoldenrodYellow);
      return;
    }
    else if (element as Grid == Grid1)
    {
      ActiveSlider = RotationSlider1;
      ActiveSwitch = ButtonToggle1;
      ActiveGrid = Grid1;
      ActiveGrid.Background = new SolidColorBrush( 
        Windows.UI.Colors.LightGoldenrodYellow);
      return;
    }
    else if (element as Grid == Grid2)
    {
      ActiveSlider = RotationSlider2;
      ActiveSwitch = ButtonToggle2;
      ActiveGrid = Grid2;
      ActiveGrid.Background = new SolidColorBrush( 
        Windows.UI.Colors.LightGoldenrodYellow);
      return;
    }
    else if (element as Grid == Grid3)
    {
      ActiveSlider = RotationSlider3;
      ActiveSwitch = ButtonToggle3;
      ActiveGrid = Grid3;
      ActiveGrid.Background = new SolidColorBrush( 
        Windows.UI.Colors.LightGoldenrodYellow);
      return;
    }
  }
}
```

<span data-ttu-id="b42b9-321">Wenn wird die App ausführen, verwenden wir das Surface Dial, um mit ihr zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-321">When we run the app, we use the Surface Dial to interact with it.</span></span> <span data-ttu-id="b42b9-322">Zunächst platzieren wir das Gerät auf dem Surface Studio-Bildschirm. Es wird von der App erkannt und dem unteren rechten Abschnitt zugeordnet (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="b42b9-322">First, we place the device on the Surface Studio screen, which the app detects and associates with the lower right section (see image).</span></span> <span data-ttu-id="b42b9-323">Anschließend drücken und halten wir das Surface Dial, um das Menü zu öffnen und das benutzerdefinierte Tool auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-323">We then press and hold the Surface Dial to open the menu and select our custom tool.</span></span> <span data-ttu-id="b42b9-324">Sobald das benutzerdefinierte Tool aktiviert ist, kann das Schieberegler-Steuerelement durch Drehen des Surface Dial angepasst werden, und die Umschaltfläche kann durch Klicken mit dem Surface Dial umgeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-324">Once the custom tool is activated, the slider control can be adjusted by rotating the Surface Dial and the switch can be toggled by clicking the Surface Dial.</span></span>

![Abbildung: Beispiel der App-UI, aktiviert mit dem benutzerdefinierten Surface Dial-Tool](images/windows-wheel/surface-dial-snippet-customtool4.png)  
*<span data-ttu-id="b42b9-326">Beispiel der App-UI, aktiviert mit dem benutzerdefinierten Surface Dial-Tool</span><span class="sxs-lookup"><span data-stu-id="b42b9-326">The sample app UI activated using the Surface Dial custom tool</span></span>*

## <a name="summary"></a><span data-ttu-id="b42b9-327">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="b42b9-327">Summary</span></span>

<span data-ttu-id="b42b9-328">Dieses Thema bietet eine Übersicht über das Eingabegerät Surface Dial, enthält Erläuterungen zur Benutzeroberfläche und für Entwickler und veranschaulicht die Anpassung der Benutzerumgebung sowohl für Offscreen-Szenarien als auch für Onscreen-Szenarien bei Verwendung mit dem Surface Studio.</span><span class="sxs-lookup"><span data-stu-id="b42b9-328">This topic provides an overview of the Surface Dial input device with UX and developer guidance on how to customize the user experience for off-screen scenarios as well as on-screen scenarios when used with Surface Studio.</span></span>

## <a name="feedback"></a><span data-ttu-id="b42b9-329">Feedback</span><span class="sxs-lookup"><span data-stu-id="b42b9-329">Feedback</span></span>

<span data-ttu-id="b42b9-330">Bitte senden Sie Fragen, Vorschläge und Feedback an [radialcontroller@microsoft.com](mailto:radialcontroller@microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="b42b9-330">Please send your questions, suggestions, and feedback to [radialcontroller@microsoft.com](mailto:radialcontroller@microsoft.com).</span></span>

## <a name="related-articles"></a><span data-ttu-id="b42b9-331">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="b42b9-331">Related articles</span></span>

### <a name="api-reference"></a><span data-ttu-id="b42b9-332">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="b42b9-332">API reference</span></span>

- [<span data-ttu-id="b42b9-333">**RadialController**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-333">**RadialController** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialController)
- [<span data-ttu-id="b42b9-334">**RadialControllerButtonClickedEventArgs**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-334">**RadialControllerButtonClickedEventArgs** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerButtonClickedEventArgs)
- [<span data-ttu-id="b42b9-335">**RadialControllerConfiguration**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-335">**RadialControllerConfiguration** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerConfiguration) 
- [<span data-ttu-id="b42b9-336">**RadialControllerControlAcquiredEventArgs**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-336">**RadialControllerControlAcquiredEventArgs** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerControlAcquiredEventArgs) 
- [<span data-ttu-id="b42b9-337">**RadialControllerMenu**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-337">**RadialControllerMenu** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerMenu) 
- [<span data-ttu-id="b42b9-338">**RadialControllerMenuItem**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-338">**RadialControllerMenuItem** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerMenuItem) 
- [<span data-ttu-id="b42b9-339">**RadialControllerRotationChangedEventArgs**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-339">**RadialControllerRotationChangedEventArgs** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerRotationChangedEventArgs) 
- [<span data-ttu-id="b42b9-340">**RadialControllerScreenContact**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-340">**RadialControllerScreenContact** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContact) 
- [<span data-ttu-id="b42b9-341">**RadialControllerScreenContactContinuedEventArgs**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-341">**RadialControllerScreenContactContinuedEventArgs** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContactContinuedEventArgs) 
- [<span data-ttu-id="b42b9-342">**RadialControllerScreenContactStartedEventArgs**-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b9-342">**RadialControllerScreenContactStartedEventArgs** class</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerScreenContactStartedEventArgs)
- [<span data-ttu-id="b42b9-343">**RadialControllerMenuKnownIcon**-Enumeration</span><span class="sxs-lookup"><span data-stu-id="b42b9-343">**RadialControllerMenuKnownIcon** enum</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerMenuKnownIcon) 
- [<span data-ttu-id="b42b9-344">**RadialControllerSystemMenuItemKind**-Enumeration</span><span class="sxs-lookup"><span data-stu-id="b42b9-344">**RadialControllerSystemMenuItemKind** enum</span></span>](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Input.RadialControllerSystemMenuItemKind) 

### <a name="samples"></a><span data-ttu-id="b42b9-345">Beispiele</span><span class="sxs-lookup"><span data-stu-id="b42b9-345">Samples</span></span>

[<span data-ttu-id="b42b9-346">Universelle Windows-Plattform – Beispiele (C# und C++)</span><span class="sxs-lookup"><span data-stu-id="b42b9-346">Universal Windows Platform samples (C# and C++)</span></span>](https://go.microsoft.com/fwlink/?linkid=832713)

[<span data-ttu-id="b42b9-347">Klassischer Windows-Desktop – Beispiel</span><span class="sxs-lookup"><span data-stu-id="b42b9-347">Windows classic desktop sample</span></span>](https://aka.ms/radialcontrollerclassicsample)