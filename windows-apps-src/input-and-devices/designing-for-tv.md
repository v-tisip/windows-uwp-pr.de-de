---
author: eliotcowley
Description: "Entwerfen Sie Ihre App so, dass sie auf Fernsehgeräten gut aussieht und ordnungsgemäß funktioniert."
title: "Entwerfen für Xbox und Fernsehgeräte"
ms.assetid: 780209cb-3e8a-4cf7-8f80-8b8f449580bf
label: Designing for Xbox and TV
template: detail.hbs
isNew: True
keywords: "Xbox, TV, 10-Fuß-Erfahrung, Gamepad, Fernbedienung, Eingabe, Interaktion"
ms.author: elcowle
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
design-contact: jeffarn
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: afc51f977d8e94977fa7ec47fad3b96ddac26197
ms.sourcegitcommit: a2908889b3566882c7494dc81fa9ece7d1d19580
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2017
---
# <a name="designing-for-xbox-and-tv"></a><span data-ttu-id="c1179-104">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="c1179-104">Designing for Xbox and TV</span></span>

<span data-ttu-id="c1179-105">Entwerfen Sie Ihre App für die Universelle Windows-Plattform (UWP) so, dass sie auf Xbox One- und Fernsehbildschirmen gut aussieht und optimal funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c1179-105">Design your Universal Windows Platform (UWP) app so that it looks good and functions well on Xbox One and television screens.</span></span>

## <a name="overview"></a><span data-ttu-id="c1179-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c1179-106">Overview</span></span>

<span data-ttu-id="c1179-107">Dank der universellen Windows-Plattform können Sie großartige Benutzeroberflächen für verschiedene Windows10-Geräte erstellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-107">The Universal Windows Platform lets you create delightful experiences across multiple Windows 10 devices.</span></span>
<span data-ttu-id="c1179-108">Die Mehrzahl der durch das UWP Framework bereitgestellten Funktionen ermöglichen Apps, auf diesen Geräten ohne zusätzlichen Aufwand die gleiche Benutzeroberfläche (UI) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1179-108">Most of the functionality provided by the UWP framework enables apps to use the same user interface (UI) across these devices, without additional work.</span></span>
<span data-ttu-id="c1179-109">Das Anpassen und Optimieren Ihrer App an Xbox One- und Fernsehbildschirme erfordert jedoch besondere Überlegungen.</span><span class="sxs-lookup"><span data-stu-id="c1179-109">However, tailoring and optimizing your app to work great on Xbox One and TV screens requires special considerations.</span></span>

<span data-ttu-id="c1179-110">Die Erfahrung, die Sie machen, wenn Sie auf dem Sofa sitzen und mittels eines Gamepads oder einer Fernbedienung mit Ihrem Fernsehgerät interagieren, wird als **3-Meter-Erfahrung** (10-Fuß-Erfahrung) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1179-110">The experience of sitting on your couch across the room, using a gamepad or remote to interact with your TV, is called the **10-foot experience**.</span></span>
<span data-ttu-id="c1179-111">Der Name kommt daher, dass sich der Benutzer im Allgemeinen ungefähr 3Meter (10Fuß) vom Bildschirm entfernt befindet.</span><span class="sxs-lookup"><span data-stu-id="c1179-111">It is so named because the user is generally sitting approximately 10 feet away from the screen.</span></span>
<span data-ttu-id="c1179-112">Dies stellt eine besondere Herausforderung dar, die beispielsweise bei einer *50-cm-Erfahrung* (2-Fuß-Erfahrung) oder bei der Interaktion mit einem PC nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-112">This provides unique challenges that aren't present in, say, the *2-foot* experience, or interacting with a PC.</span></span>
<span data-ttu-id="c1179-113">Wenn Sie eine App für Xbox One oder ein anderes Gerät entwickeln, das Inhalte auf einem Fernsehbildschirm ausgibt und eine Steuerung verwendet, sollten Sie dies stets bedenken.</span><span class="sxs-lookup"><span data-stu-id="c1179-113">If you are developing an app for Xbox One or any other device that outputs to the TV screen and uses a controller for input, you should always keep this in mind.</span></span>

<span data-ttu-id="c1179-114">Nicht alle Schritte in diesem Artikel sind erforderlich, damit Ihre App gut in 10 Fuß-Umgebungen funktioniert. Wenn Sie diese jedoch kennen und für Ihre App die entsprechenden Entscheidungen treffen, führt dies zu einer besseren 10-Fuß-Erfahrung, die an die spezifischen Anforderungen Ihrer App angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-114">Not all of the steps in this article are required to make your app work well for 10-foot experiences, but understanding them and making the appropriate decisions for your app will result in a better 10-foot experience tailored for your app's specific needs.</span></span>
<span data-ttu-id="c1179-115">Berücksichtigen Sie die folgenden Designrichtlinien, wenn Sie eine App für eine 10-Fuß-Umgebung entwickeln.</span><span class="sxs-lookup"><span data-stu-id="c1179-115">As you bring your app to life in the 10-foot environment, consider the following design principles.</span></span>

### <a name="simple"></a><span data-ttu-id="c1179-116">Einfach</span><span class="sxs-lookup"><span data-stu-id="c1179-116">Simple</span></span>

<span data-ttu-id="c1179-117">Ein Entwurf für eine 10-Fuß-Umgebung bedeutet einen einzigartigen Satz von Herausforderungen.</span><span class="sxs-lookup"><span data-stu-id="c1179-117">Designing for the 10-foot environment presents a unique set of challenges.</span></span> <span data-ttu-id="c1179-118">Auflösung und Anzeigeabstand kann es Menschen schwer machen, zu viele Informationen zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1179-118">Resolution and viewing distance can make it difficult for people to process too much information.</span></span>
<span data-ttu-id="c1179-119">Versuchen Sie, Ihr Design klar zu halten und auf die einfachsten Komponenten zu reduzieren, die möglich sind.</span><span class="sxs-lookup"><span data-stu-id="c1179-119">Try to keep your design clean, reduced to the simplest possible components.</span></span> <span data-ttu-id="c1179-120">Die Menge der auf einem Fernseher angezeigten Informationen sollte mit der vergleichbar sein, die Ihnen auf einem Mobiltelefon angezeigt werden, nicht auf einem Desktop.</span><span class="sxs-lookup"><span data-stu-id="c1179-120">The amount of information displayed on a TV should be comparable to what you'd see on a mobile phone, rather than on a desktop.</span></span>

![Xbox One-Startseite](images/designing-for-tv/xbox-home-screen.png)

### <a name="coherent"></a><span data-ttu-id="c1179-122">Einheitlich</span><span class="sxs-lookup"><span data-stu-id="c1179-122">Coherent</span></span>

<span data-ttu-id="c1179-123">UWP-Apps in 10-Fuß-Umgebungen sollten intuitiv und benutzerfreundlich sein.</span><span class="sxs-lookup"><span data-stu-id="c1179-123">UWP apps in the 10-foot environment should be intuitive and easy to use.</span></span> <span data-ttu-id="c1179-124">Sorgen Sie für einen klaren und unverkennbaren Fokus.</span><span class="sxs-lookup"><span data-stu-id="c1179-124">Make the focus clear and unmistakable.</span></span>
<span data-ttu-id="c1179-125">Ordnen Sie Inhalte so an, dass Verschiebungen auf dem Bildschirm konsistent und vorhersagbar sind.</span><span class="sxs-lookup"><span data-stu-id="c1179-125">Arrange content so that movement across the space is consistent and predictable.</span></span> <span data-ttu-id="c1179-126">Stellen Sie Menschen den kürzesten Weg zu dem bereit, was sie tun möchten.</span><span class="sxs-lookup"><span data-stu-id="c1179-126">Give people the shortest path to what they want to do.</span></span>

![Xbox One-Film-App](images/designing-for-tv/xbox-movies-app.png)

_**<span data-ttu-id="c1179-128">Alle im Screenshot gezeigten Filme sind auf Microsoft Filme & TV verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c1179-128">All movies shown in the screenshot are available on Microsoft Movies & TV.</span></span>**_  

### <a name="captivating"></a><span data-ttu-id="c1179-129">Fesselnd</span><span class="sxs-lookup"><span data-stu-id="c1179-129">Captivating</span></span>

<span data-ttu-id="c1179-130">Der große Bildschirm bietet äußerst faszinierende Erfahrungen, ähnlich wie ein Kino.</span><span class="sxs-lookup"><span data-stu-id="c1179-130">The most immersive, cinematic experiences take place on the big screen.</span></span> <span data-ttu-id="c1179-131">Rand-Rand-Design, elegante Bewegungen und brillante Farben und Typografien eröffnen Ihren Apps neue Dimensionen.</span><span class="sxs-lookup"><span data-stu-id="c1179-131">Edge-to-edge scenery, elegant motion, and vibrant use of color and typography take your apps to the next level.</span></span> <span data-ttu-id="c1179-132">Seien Sie mutig, und bieten Sie ein ansprechendes Design.</span><span class="sxs-lookup"><span data-stu-id="c1179-132">Be bold and beautiful.</span></span>

![Xbox One Avatar-App](images/designing-for-tv/xbox-avatar-app.png)

### <a name="optimizations-for-the-10-foot-experience"></a><span data-ttu-id="c1179-134">Optimierungen für die 10-Fuß-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="c1179-134">Optimizations for the 10-foot experience</span></span>

<span data-ttu-id="c1179-135">Da Sie nun mit den Grundsätzen eines guten UWP-App-Designs für die 10-Fuß-Erfahrung vertraut sind, lesen Sie die folgenden Übersicht über die verschiedenen Arten, wie Sie Ihre App optimieren und eine hervorragende Benutzerumgebung bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-135">Now that you know the principles of good UWP app design for the 10-foot experience, read through the following overview of the specific ways you can optimize your app and make for a great user experience.</span></span>

| <span data-ttu-id="c1179-136">Feature</span><span class="sxs-lookup"><span data-stu-id="c1179-136">Feature</span></span>        | <span data-ttu-id="c1179-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1179-137">Description</span></span>           |
| -------------------------------------------------------------- |--------------------------------|
| [<span data-ttu-id="c1179-138">Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="c1179-138">Gamepad and remote control</span></span>](#gamepad-and-remote-control)      | <span data-ttu-id="c1179-139">Der wichtigste Schritt bei der Optimierung für 10-Fuß-Umgebungen besteht darin, sicherzustellen, dass Ihre App gut mit Gamepads und Fernbedienungen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c1179-139">Making sure that your app works well with gamepad and remote is the most important step in optimizing for 10-foot experiences.</span></span> <span data-ttu-id="c1179-140">Es gibt spezifische Verbesserungen für Gamepads und Fernbedienungen, mit denen Sie die Interaktionserfahrungen von Benutzern auf Geräten optimieren können, auf denen ihre Aktionen eher eingeschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="c1179-140">There are several gamepad and remote-specific improvements that you can make to optimize the user interaction experience on a device where their actions are somewhat limited.</span></span> |
| [<span data-ttu-id="c1179-141">XY-Fokusnavigation und -interaktion</span><span class="sxs-lookup"><span data-stu-id="c1179-141">XY focus navigation and interaction</span></span>](#xy-focus-navigation-and-interaction) | <span data-ttu-id="c1179-142">Die UWP stellt eine **XY Fokusnavigation** bereit, mit deren Hilfe Benutzer in der Benutzeroberfläche Ihrer App navigieren können.</span><span class="sxs-lookup"><span data-stu-id="c1179-142">The UWP provides **XY focus navigation** that allows the user to navigate around your app's UI.</span></span> <span data-ttu-id="c1179-143">Dies begrenzt Benutzer jedoch auf eine Navigation nach oben, unten, links und rechts.</span><span class="sxs-lookup"><span data-stu-id="c1179-143">However, this limits the user to navigating up, down, left, and right.</span></span> <span data-ttu-id="c1179-144">In diesem Abschnitt finden Sie Empfehlungen für den Umgang mit diesen und anderen Überlegungen.</span><span class="sxs-lookup"><span data-stu-id="c1179-144">Recommendations for dealing with this and other considerations are outlined in this section.</span></span> |
| [<span data-ttu-id="c1179-145">Mausmodus</span><span class="sxs-lookup"><span data-stu-id="c1179-145">Mouse mode</span></span>](#mouse-mode)|<span data-ttu-id="c1179-146">In einigen Benutzeroberflächen, beispielsweise Karten und Zeichenoberflächen, ist es nicht möglich oder praktisch, eine XY-Fokusnavigation zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1179-146">In some user interfaces, such as maps and drawing surfaces, it is not possible or practical to use XY focus navigation.</span></span> <span data-ttu-id="c1179-147">Für diese Schnittstellen stellt die UWP den **Mausmodus** bereit, damit das Gamepad/die Fernbedienung ähnlich einer Maus auf einem Desktopcomputer frei navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-147">For these interfaces, the UWP provides **mouse mode** to let the gamepad/remote navigate freely, like a mouse on a desktop computer.</span></span>|
| [<span data-ttu-id="c1179-148">Fokusanzeige</span><span class="sxs-lookup"><span data-stu-id="c1179-148">Focus visual</span></span>](#focus-visual)  | <span data-ttu-id="c1179-149">Die Fokusanzeige ist der Rahmen um das Benutzeroberflächenelement, das zurzeit den Fokus besitzt.</span><span class="sxs-lookup"><span data-stu-id="c1179-149">The focus visual is the border around the UI element that currently has focus.</span></span> <span data-ttu-id="c1179-150">Dies hilft Benutzern, sich zu orientieren, damit sie in Ihrer Benutzeroberfläche einfach navigieren können, ohne die Orientierung zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-150">This helps orient the user so that they can easily navigate your UI without getting lost.</span></span> <span data-ttu-id="c1179-151">Wenn der Fokus nicht klar erkennbar ist, könnten Benutzer in der Benutzeroberfläche die Orientierung verlieren und keine gute Erfahrung mit Ihrer App machen.</span><span class="sxs-lookup"><span data-stu-id="c1179-151">If the focus is not clearly visible, the user could get lost in your UI and not have a great experience.</span></span>  |
| [<span data-ttu-id="c1179-152">Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="c1179-152">Focus engagement</span></span>](#focus-engagement) | <span data-ttu-id="c1179-153">Das Einrichten der Fokusaktivierung für ein Benutzeroberflächenelement erfordert, dass der Benutzer die **A/Auswahl**-Taste drückt, um mit diesem zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-153">Setting focus engagement on a UI element requires the user to press the **A/Select** button in order to interact with it.</span></span> <span data-ttu-id="c1179-154">Dies kann helfen, eine bessere Erfahrung für den Benutzer beim Navigieren in der Benutzeroberfläche der App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c1179-154">This can help create a better experience for the user when navigating your app's UI.</span></span>
| [<span data-ttu-id="c1179-155">Anpassen von Benutzeroberflächenelementen</span><span class="sxs-lookup"><span data-stu-id="c1179-155">UI element sizing</span></span>](#ui-element-sizing)  | <span data-ttu-id="c1179-156">Die Universelle Windows-Plattform verwendet [Skalierung und effektive Pixel](..\layout\design-and-ui-intro.md#effective-pixels-and-scaling), um die Benutzeroberfläche gemäß dem Anzeigeabstand zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-156">The Universal Windows Platform uses [scaling and effective pixels](..\layout\design-and-ui-intro.md#effective-pixels-and-scaling) to scale the UI according to the viewing distance.</span></span> <span data-ttu-id="c1179-157">Wenn Sie verstehen, wie Sie Größen anpassen und auf Ihre Benutzeroberfläche anwenden, hilft Ihnen dies, Ihre App für die 10-Fuß-Umgebung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-157">Understanding sizing and applying it across your UI will help optimize your app for the 10-foot environment.</span></span>  |
|  [<span data-ttu-id="c1179-158">Fernsehsicherer Bereich</span><span class="sxs-lookup"><span data-stu-id="c1179-158">TV-safe area</span></span>](#tv-safe-area) | <span data-ttu-id="c1179-159">Die UWP vermeidet automatisch und standardmäßig die Anzeige von Benutzeroberflächenelementen in nicht fernsehsicheren Bereichen (nahe dem Bildschirmrand).</span><span class="sxs-lookup"><span data-stu-id="c1179-159">The UWP will automatically avoid displaying any UI in TV-unsafe areas (areas close to the edges of the screen) by default.</span></span> <span data-ttu-id="c1179-160">Dies führt jedoch zu einem „Schachteleffekt“, so dass die Benutzeroberfläche einem Briefkastenschlitz ähnelt.</span><span class="sxs-lookup"><span data-stu-id="c1179-160">However, this creates a "boxed-in" effect in which the UI looks letterboxed.</span></span> <span data-ttu-id="c1179-161">Damit Ihre App auf Fernsehgeräten wirklich immersiv ist, müssen Sie diese so anpassen, dass sie sich auf Fernsehgeräten, die dies unterstützen, bis zu den Rändern erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-161">For your app to be truly immersive on TV, you will want to modify it so that it extends to the edges of the screen on TVs that support it.</span></span> |
| [<span data-ttu-id="c1179-162">Farben</span><span class="sxs-lookup"><span data-stu-id="c1179-162">Colors</span></span>](#colors)  |  <span data-ttu-id="c1179-163">Die UWP unterstützt Farbdesigns. Daher wird eine App, die das Systemdesign berücksichtigt, auf Xbox One standardmäßig auf **dark** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c1179-163">The UWP supports color themes, and an app that respects the system theme will default to **dark** on Xbox One.</span></span> <span data-ttu-id="c1179-164">Wenn Ihre App ein bestimmtes Farbdesign verwendet, sollten Sie daran denken, dass sich einige Farben nicht gut für Fernsehbildschirme eignen und daher vermieden werden sollten.</span><span class="sxs-lookup"><span data-stu-id="c1179-164">If your app has a specific color theme, you should consider that some colors don't work well for TV and should be avoided.</span></span> |
| [<span data-ttu-id="c1179-165">Sound</span><span class="sxs-lookup"><span data-stu-id="c1179-165">Sound</span></span>](../style/sound.md)    | <span data-ttu-id="c1179-166">Sounds spielen bei der 10 Fuß-Erfahrung eine wichtige Rolle. Sie helfen den Benutzern sich zu vertiefen und liefern Feedback.</span><span class="sxs-lookup"><span data-stu-id="c1179-166">Sounds play a key role in the 10-foot experience, helping to immerse and give feedback to the user.</span></span> <span data-ttu-id="c1179-167">Die UWP bietet Funktionen, mit denen Sounds für allgemeine Steuerelemente automatisch aktiviert werden, wenn die App auf Xbox One ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-167">The UWP provides functionality that automatically turns on sounds for common controls when the app is running on Xbox One.</span></span> <span data-ttu-id="c1179-168">Erfahren Sie mehr über die in der Universellen Windows-Plattform integrierte Unterstützung von Sound, und erfahren Sie, wie Sie davon profitieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-168">Find out more about the sound support built into the UWP and learn how to take advantage of it.</span></span>    |
| [<span data-ttu-id="c1179-169">Richtlinien für Benutzeroberflächensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1179-169">Guidelines for UI controls</span></span>](#guidelines-for-ui-controls)  |  <span data-ttu-id="c1179-170">Es gibt mehrere Benutzeroberflächen-Steuerelemente, die auf mehreren Geräten gut funktionieren. Wenn diese jedoch auf Fernsehgeräten verwendet werden, müssen bestimmte Aspekte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-170">There are several UI controls that work well across multiple devices, but have certain considerations when used on TV.</span></span> <span data-ttu-id="c1179-171">Informieren Sie sich über einige bewährte Methoden für die Verwendung dieser Steuerelemente beim Entwerfen für die 10 Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="c1179-171">Read about some best practices for using these controls when designing for the 10-foot experience.</span></span> |
| [<span data-ttu-id="c1179-172">Benutzerdefinierter visueller Zustandsauslöser für Xbox</span><span class="sxs-lookup"><span data-stu-id="c1179-172">Custom visual state trigger for Xbox</span></span>](#custom-visual-state-trigger-for-xbox) | <span data-ttu-id="c1179-173">Um Ihre UWP-App an die 10-Fuß-Erfahrung anzupassen, empfehlen wir Ihnen, einen benutzerdefinierten *visuellen Zustandsauslöser* zu verwenden, um das Layout zu ändern, wenn die App erkennt, dass sie auf einer Xbox-Konsole gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c1179-173">To tailor your UWP app for the 10-foot experience, we recommend that you use a custom *visual state trigger* to make layout changes when the app detects that it has been launched on an Xbox console.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-174">Die meisten Codeausschnitte in diesem Thema wurden in XAML/C# verfasst. Die Grundsätze und Konzepte gelten jedoch für alle UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="c1179-174">Most of the code snippets in this topic are in XAML/C#; however, the principles and concepts apply to all UWP apps.</span></span> <span data-ttu-id="c1179-175">Wenn Sie eine HTML/JavaScript-UWP-App für Xbox entwickeln, steht Ihnen die hervorragende [TVHelpers](https://github.com/Microsoft/TVHelpers/wiki)-Bibliothek auf GitHub zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c1179-175">If you're developing an HTML/JavaScript UWP app for Xbox, check out the excellent [TVHelpers](https://github.com/Microsoft/TVHelpers/wiki) library on GitHub.</span></span>

## <a name="gamepad-and-remote-control"></a><span data-ttu-id="c1179-176">Gamepad und Remotesteuerung</span><span class="sxs-lookup"><span data-stu-id="c1179-176">Gamepad and remote control</span></span>

<span data-ttu-id="c1179-177">Gamepads und Remotesteuerungen sind die Haupteingabegeräte für die 10-Fuß-Erfahrung (vergleichbar Tastatur und Maus bei PCs und Toucheingabe bei Smartphones und Tablets).</span><span class="sxs-lookup"><span data-stu-id="c1179-177">Just like keyboard and mouse are for PC, and touch is for phone and tablet, gamepad and remote control are the main input devices for the 10-foot experience.</span></span>
<span data-ttu-id="c1179-178">In diesem Abschnitt werden die Hardwaretasten und ihre Funktionen vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="c1179-178">This section introduces what the hardware buttons are and what they do.</span></span>
<span data-ttu-id="c1179-179">In [XY-Fokusnavigation und -interaktion](#xy-focus-navigation-and-interaction) und [Mausmodus](#mouse-mode) erfahren Sie, wie Sie Ihre App für die Verwendung dieser Eingabegeräte optimieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-179">In [XY focus navigation and interaction](#xy-focus-navigation-and-interaction) and [Mouse mode](#mouse-mode), you will learn how to optimize your app when using these input devices.</span></span>

<span data-ttu-id="c1179-180">Die Qualität des Gamepad- und Fernbedienungsverhaltens, das Sie direkt erhalten, ist davon abhängig, wie gut die Tastatur in Ihrer App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-180">The quality of gamepad and remote behavior that you get out-of-the-box depends on how well keyboard is supported in your app.</span></span> <span data-ttu-id="c1179-181">Eine gute Möglichkeit, um sicherzustellen, dass Ihre App gut mit Gamepads/Fernbedienungen funktioniert, besteht darin, sicherzustellen, dass sie gut mit PC-Tastaturen funktioniert, und sie anschließend mit Gamepads/Fernbedienungen zu testen, um die Schwachstellen in der Benutzeroberfläche zu finden.</span><span class="sxs-lookup"><span data-stu-id="c1179-181">A good way to ensure that your app will work well with gamepad/remote is to make sure that it works well with keyboard on PC, and then test with gamepad/remote to find weak spots in your UI.</span></span>

### <a name="hardware-buttons"></a><span data-ttu-id="c1179-182">Hardwaretasten</span><span class="sxs-lookup"><span data-stu-id="c1179-182">Hardware buttons</span></span>

<span data-ttu-id="c1179-183">In diesem Dokument werden Schaltflächen mit den Namen bezeichnet, die im folgenden Diagramm angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-183">Throughout this document, buttons will be referred to by the names given in the following diagram.</span></span>

![Diagramm für Gamepad- und Fernbedienungstasten](images/designing-for-tv/hardware-buttons-gamepad-remote.png)

<span data-ttu-id="c1179-185">Wie Sie im Diagramm erkennen können, werden einige Schaltflächen auf Gamepads unterstützt, die nicht auf Fernbedienungen unterstützt werden, und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="c1179-185">As you can see from the diagram, there are some buttons that are supported on gamepad that are not supported on remote control, and vice versa.</span></span> <span data-ttu-id="c1179-186">Sie können zwar Tasten verwenden, die nur auf einer Art von Eingabegerät unterstützt werden, um die Navigation in der Benutzeroberfläche zu beschleunigen. Denken Sie jedoch daran, dass deren Verwendung für kritische Interaktionen zu Situationen führen kann, in den der Benutzer nicht mit bestimmten Teilen der Benutzeroberfläche interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-186">While you can use buttons that are only supported on one input device to make navigating the UI faster, be aware that using them for critical interactions may create a situation where the user is unable to interact with certain parts of the UI.</span></span>

<span data-ttu-id="c1179-187">Die folgende Tabelle enthält eine Liste aller Hardwaretasten, die von UWP-Apps unterstützt werden, sowie Angaben dazu, welche Eingabegeräte diese unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c1179-187">The following table lists all of the hardware buttons supported by UWP apps, and which input device supports them.</span></span>

| <span data-ttu-id="c1179-188">Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-188">Button</span></span>                    | <span data-ttu-id="c1179-189">Gamepad</span><span class="sxs-lookup"><span data-stu-id="c1179-189">Gamepad</span></span>   | <span data-ttu-id="c1179-190">Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="c1179-190">Remote control</span></span>    |
|---------------------------|-----------|-------------------|
| <span data-ttu-id="c1179-191">A/Auswahl-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-191">A/Select button</span></span>           | <span data-ttu-id="c1179-192">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-192">Yes</span></span>       | <span data-ttu-id="c1179-193">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-193">Yes</span></span>               |
| <span data-ttu-id="c1179-194">B/Zurück-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-194">B/Back button</span></span>             | <span data-ttu-id="c1179-195">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-195">Yes</span></span>       | <span data-ttu-id="c1179-196">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-196">Yes</span></span>               |
| <span data-ttu-id="c1179-197">Steuerkreuz (D-Pad)</span><span class="sxs-lookup"><span data-stu-id="c1179-197">Directional pad (D-pad)</span></span>   | <span data-ttu-id="c1179-198">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-198">Yes</span></span>       | <span data-ttu-id="c1179-199">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-199">Yes</span></span>               |
| <span data-ttu-id="c1179-200">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-200">Menu button</span></span>               | <span data-ttu-id="c1179-201">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-201">Yes</span></span>       | <span data-ttu-id="c1179-202">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-202">Yes</span></span>               |
| <span data-ttu-id="c1179-203">Ansicht-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-203">View button</span></span>               | <span data-ttu-id="c1179-204">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-204">Yes</span></span>       | <span data-ttu-id="c1179-205">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-205">Yes</span></span>               |
| <span data-ttu-id="c1179-206">X- und Y-Tasten</span><span class="sxs-lookup"><span data-stu-id="c1179-206">X and Y buttons</span></span>           | <span data-ttu-id="c1179-207">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-207">Yes</span></span>       | <span data-ttu-id="c1179-208">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-208">No</span></span>                |
| <span data-ttu-id="c1179-209">Linker Stick</span><span class="sxs-lookup"><span data-stu-id="c1179-209">Left stick</span></span>                | <span data-ttu-id="c1179-210">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-210">Yes</span></span>       | <span data-ttu-id="c1179-211">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-211">No</span></span>                |
| <span data-ttu-id="c1179-212">Rechter Stick</span><span class="sxs-lookup"><span data-stu-id="c1179-212">Right stick</span></span>               | <span data-ttu-id="c1179-213">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-213">Yes</span></span>       | <span data-ttu-id="c1179-214">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-214">No</span></span>                |
| <span data-ttu-id="c1179-215">Linke und rechte Schalter</span><span class="sxs-lookup"><span data-stu-id="c1179-215">Left and right triggers</span></span>   | <span data-ttu-id="c1179-216">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-216">Yes</span></span>       | <span data-ttu-id="c1179-217">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-217">No</span></span>                |
| <span data-ttu-id="c1179-218">Linke und rechte Bumper</span><span class="sxs-lookup"><span data-stu-id="c1179-218">Left and right bumpers</span></span>    | <span data-ttu-id="c1179-219">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-219">Yes</span></span>       | <span data-ttu-id="c1179-220">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-220">No</span></span>                |
| <span data-ttu-id="c1179-221">OneGuide-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-221">OneGuide button</span></span>           | <span data-ttu-id="c1179-222">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-222">No</span></span>        | <span data-ttu-id="c1179-223">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-223">Yes</span></span>               |
| <span data-ttu-id="c1179-224">Lautstärke-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-224">Volume button</span></span>             | <span data-ttu-id="c1179-225">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-225">No</span></span>        | <span data-ttu-id="c1179-226">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-226">Yes</span></span>               |
| <span data-ttu-id="c1179-227">Kanal-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-227">Channel button</span></span>            | <span data-ttu-id="c1179-228">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-228">No</span></span>        | <span data-ttu-id="c1179-229">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-229">Yes</span></span>               |
| <span data-ttu-id="c1179-230">Mediensteuerungs-Tasten</span><span class="sxs-lookup"><span data-stu-id="c1179-230">Media control buttons</span></span>     | <span data-ttu-id="c1179-231">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-231">No</span></span>        | <span data-ttu-id="c1179-232">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-232">Yes</span></span>               |
| <span data-ttu-id="c1179-233">Stumm-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-233">Mute button</span></span>               | <span data-ttu-id="c1179-234">Nein</span><span class="sxs-lookup"><span data-stu-id="c1179-234">No</span></span>        | <span data-ttu-id="c1179-235">Ja</span><span class="sxs-lookup"><span data-stu-id="c1179-235">Yes</span></span>               |

### <a name="built-in-button-support"></a><span data-ttu-id="c1179-236">Integrierte Tastenunterstützung</span><span class="sxs-lookup"><span data-stu-id="c1179-236">Built-in button support</span></span>

<span data-ttu-id="c1179-237">Die UWP ordnet automatisch das vorhandene Tastatureingabeverhalten den Gamepad- und Fernbedienungseingaben zu.</span><span class="sxs-lookup"><span data-stu-id="c1179-237">The UWP automatically maps existing keyboard input behavior to gamepad and remote control input.</span></span> <span data-ttu-id="c1179-238">Die folgende Tabelle zeigt diese integrierten Zuordnungen.</span><span class="sxs-lookup"><span data-stu-id="c1179-238">The following table lists these built-in mappings.</span></span>

| <span data-ttu-id="c1179-239">Tastatur</span><span class="sxs-lookup"><span data-stu-id="c1179-239">Keyboard</span></span>              | <span data-ttu-id="c1179-240">Gamepad/Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="c1179-240">Gamepad/remote</span></span>                        |
|-----------------------|---------------------------------------|
| <span data-ttu-id="c1179-241">Pfeiltasten</span><span class="sxs-lookup"><span data-stu-id="c1179-241">Arrow keys</span></span>            | <span data-ttu-id="c1179-242">Steuerkreuz (D-Pad; auch linker Stick auf Gamepads)</span><span class="sxs-lookup"><span data-stu-id="c1179-242">D-pad (also left stick on gamepad)</span></span>    |
| <span data-ttu-id="c1179-243">Leertaste</span><span class="sxs-lookup"><span data-stu-id="c1179-243">Spacebar</span></span>              | <span data-ttu-id="c1179-244">A/Auswahl-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-244">A/Select button</span></span>                       |
| <span data-ttu-id="c1179-245">Eingabe</span><span class="sxs-lookup"><span data-stu-id="c1179-245">Enter</span></span>                 | <span data-ttu-id="c1179-246">A/Auswahl-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-246">A/Select button</span></span>                       |
| <span data-ttu-id="c1179-247">Escape</span><span class="sxs-lookup"><span data-stu-id="c1179-247">Escape</span></span>                | <span data-ttu-id="c1179-248">B/Zurück-Taste*</span><span class="sxs-lookup"><span data-stu-id="c1179-248">B/Back button*</span></span>                        |

<span data-ttu-id="c1179-249">\*Wenn für die B-Taste weder das [KeyDown](https://msdn.microsoft.com/library/windows/apps/br208941.aspx)- noch das [KeyUp](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.keyup.aspx)-Ereignis von der App behandelt werden, wird das [SystemNavigationManager.BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)-Ereignis ausgelöst, das zu einer Rückwärtsnavigation innerhalb der App führen sollte.</span><span class="sxs-lookup"><span data-stu-id="c1179-249">\*When neither the [KeyDown](https://msdn.microsoft.com/library/windows/apps/br208941.aspx) nor [KeyUp](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.keyup.aspx) events for the B button are handled by the app, the [SystemNavigationManager.BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx) event will be fired, which should result in back navigation within the app.</span></span> <span data-ttu-id="c1179-250">Dieses Verhalten müssen Sie allerdings selbst implementieren, wie im folgenden Codeausschnitt gezeigt:</span><span class="sxs-lookup"><span data-stu-id="c1179-250">However, you have to implement this yourself, as in the following code snippet:</span></span>

```csharp
// This code goes in the MainPage class

public MainPage()
{
    this.InitializeComponent();

    // Handling Page Back navigation behaviors
    SystemNavigationManager.GetForCurrentView().BackRequested +=
        SystemNavigationManager_BackRequested;
}

private void SystemNavigationManager_BackRequested(
    object sender,
    BackRequestedEventArgs e)
{
    if (!e.Handled)
    {
        e.Handled = this.BackRequested();
    }
}

public Frame AppFrame { get { return this.Frame; } }

private bool BackRequested()
{
    // Get a hold of the current frame so that we can inspect the app back stack
    if (this.AppFrame == null)
        return false;

    // Check to see if this is the top-most page on the app back stack
    if (this.AppFrame.CanGoBack)
    {
        // If not, set the event to handled and go back to the previous page in the
        // app.
        this.AppFrame.GoBack();
        return true;
    }
    return false;
}
```

<span data-ttu-id="c1179-251">UWP-Apps auf Xbox One unterstützen außerdem das Öffnen des Kontextmenüs durch Drücken der **Menü**-Taste.</span><span class="sxs-lookup"><span data-stu-id="c1179-251">UWP apps on Xbox One also support pressing the **Menu** button to open context menus.</span></span> <span data-ttu-id="c1179-252">Weitere Informationen finden Sie unter [CommandBar und ContextFlyout](#commandbar-and-contextflyout).</span><span class="sxs-lookup"><span data-stu-id="c1179-252">For more information, see [CommandBar and ContextFlyout](#commandbar-and-contextflyout).</span></span>

### <a name="accelerator-support"></a><span data-ttu-id="c1179-253">Unterstützung von Beschleunigertasten</span><span class="sxs-lookup"><span data-stu-id="c1179-253">Accelerator support</span></span>

<span data-ttu-id="c1179-254">Beschleunigertasten sind Tasten, die für die schnellere Navigation in einer Benutzeroberfläche verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c1179-254">Accelerator buttons are buttons that can be used to speed up navigation through a UI.</span></span> <span data-ttu-id="c1179-255">Diese Tasten sind jedoch möglicherweise für ein bestimmtes Eingabegerät spezifisch. Denken Sie daher daran, dass nicht alle Benutzer diese Funktionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c1179-255">However, these buttons may be unique to a certain input device, so keep in mind that not all users will be able to use these functions.</span></span> <span data-ttu-id="c1179-256">Tatsächlich sind zurzeit Gamepads die einzigen Eingabegeräte, die Beschleunigerfunktionen für UWP-Apps auf Xbox One unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c1179-256">In fact, gamepad is currently the only input device that supports accelerator functions for UWP apps on Xbox One.</span></span>

<span data-ttu-id="c1179-257">Die folgende Tabelle zeigt die in die UWP integrierte Beschleunigerunterstützung sowie die Unterstützung, die von Ihnen selbst implementiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-257">The following table lists the accelerator support built into the UWP, as well as that which you can implement on your own.</span></span> <span data-ttu-id="c1179-258">Nutzen Sie diese Verhaltensweisen in Ihrer benutzerdefinierten Benutzeroberfläche, um eine konsistente und benutzerfreundliche Benutzeroberfläche bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-258">Utilize these behaviors in your custom UI to provide a consistent and friendly user experience.</span></span>

| <span data-ttu-id="c1179-259">Interaktion</span><span class="sxs-lookup"><span data-stu-id="c1179-259">Interaction</span></span>   | <span data-ttu-id="c1179-260">Tastatur/Maus</span><span class="sxs-lookup"><span data-stu-id="c1179-260">Keyboard/Mouse</span></span>   | <span data-ttu-id="c1179-261">Gamepad</span><span class="sxs-lookup"><span data-stu-id="c1179-261">Gamepad</span></span>      | <span data-ttu-id="c1179-262">Integriert für:</span><span class="sxs-lookup"><span data-stu-id="c1179-262">Built-in for:</span></span>  | <span data-ttu-id="c1179-263">Empfohlen für:</span><span class="sxs-lookup"><span data-stu-id="c1179-263">Recommended for:</span></span> |
|---------------|------------|--------------|----------------|------------------|
| <span data-ttu-id="c1179-264">Bild auf/Bild ab</span><span class="sxs-lookup"><span data-stu-id="c1179-264">Page up/down</span></span>  | <span data-ttu-id="c1179-265">Bild auf/Bild ab</span><span class="sxs-lookup"><span data-stu-id="c1179-265">Page up/down</span></span> | <span data-ttu-id="c1179-266">Linker/rechter Trigger</span><span class="sxs-lookup"><span data-stu-id="c1179-266">Left/right triggers</span></span> | <span data-ttu-id="c1179-267">[CalendarView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.calendarview.aspx), [ListBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listbox.aspx), [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx), [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), `ScrollViewer`, [Selector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.aspx), [LoopingSelector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.loopingselector.aspx), [ComboBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.combobox.aspx), [FlipView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx)</span><span class="sxs-lookup"><span data-stu-id="c1179-267">[CalendarView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.calendarview.aspx), [ListBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listbox.aspx), [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx), [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), `ScrollViewer`, [Selector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.aspx), [LoopingSelector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.loopingselector.aspx), [ComboBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.combobox.aspx), [FlipView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx)</span></span> | <span data-ttu-id="c1179-268">Ansichten, die den vertikalen Bildlauf unterstützen</span><span class="sxs-lookup"><span data-stu-id="c1179-268">Views that support vertical scrolling</span></span>
| <span data-ttu-id="c1179-269">Seite nach links/rechts</span><span class="sxs-lookup"><span data-stu-id="c1179-269">Page left/right</span></span> | <span data-ttu-id="c1179-270">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-270">None</span></span> | <span data-ttu-id="c1179-271">Linker/rechter Bumper</span><span class="sxs-lookup"><span data-stu-id="c1179-271">Left/right bumpers</span></span> | <span data-ttu-id="c1179-272">[Pivot](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.aspx), [ListBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listbox.aspx), [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx), [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), `ScrollViewer`, [Selector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.aspx), [LoopingSelector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.loopingselector.aspx), [FlipView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx)</span><span class="sxs-lookup"><span data-stu-id="c1179-272">[Pivot](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.aspx), [ListBox](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listbox.aspx), [ListViewBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listviewbase.aspx), [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), `ScrollViewer`, [Selector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.selector.aspx), [LoopingSelector](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.loopingselector.aspx), [FlipView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flipview.aspx)</span></span> | <span data-ttu-id="c1179-273">Ansichten, die den horizontalen Bildlauf unterstützen</span><span class="sxs-lookup"><span data-stu-id="c1179-273">Views that support horizontal scrolling</span></span>
| <span data-ttu-id="c1179-274">Vergrößern/Verkleinern</span><span class="sxs-lookup"><span data-stu-id="c1179-274">Zoom in/out</span></span>        | <span data-ttu-id="c1179-275">STRG +/-</span><span class="sxs-lookup"><span data-stu-id="c1179-275">Ctrl +/-</span></span> | <span data-ttu-id="c1179-276">Linker/rechter Trigger</span><span class="sxs-lookup"><span data-stu-id="c1179-276">Left/right triggers</span></span> | <span data-ttu-id="c1179-277">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-277">None</span></span> | `ScrollViewer`<span data-ttu-id="c1179-278">, Ansichten, die das Vergrößern/Verkleinern unterstützen</span><span class="sxs-lookup"><span data-stu-id="c1179-278">, views that support zooming in and out</span></span> |
| <span data-ttu-id="c1179-279">Navigationsbereich öffnen/schließen</span><span class="sxs-lookup"><span data-stu-id="c1179-279">Open/close nav pane</span></span> | <span data-ttu-id="c1179-280">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-280">None</span></span> | <span data-ttu-id="c1179-281">Ansicht</span><span class="sxs-lookup"><span data-stu-id="c1179-281">View</span></span> | <span data-ttu-id="c1179-282">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-282">None</span></span> | <span data-ttu-id="c1179-283">Navigationsbereiche</span><span class="sxs-lookup"><span data-stu-id="c1179-283">Navigation panes</span></span> |
| [<span data-ttu-id="c1179-284">Suche</span><span class="sxs-lookup"><span data-stu-id="c1179-284">Search</span></span>](#search-experience) | <span data-ttu-id="c1179-285">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-285">None</span></span> | <span data-ttu-id="c1179-286">Y-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-286">Y button</span></span> | <span data-ttu-id="c1179-287">Keine</span><span class="sxs-lookup"><span data-stu-id="c1179-287">None</span></span> | <span data-ttu-id="c1179-288">Verknüpfung mit der Hauptsuchfunktion in der App</span><span class="sxs-lookup"><span data-stu-id="c1179-288">Shortcut to the main search function in the app</span></span> |
| [<span data-ttu-id="c1179-289">Öffnen Sie das Kontextmenü</span><span class="sxs-lookup"><span data-stu-id="c1179-289">Open context menu</span></span>](#commandbar-and-contextflyout) | <span data-ttu-id="c1179-290">Klicken Sie mit der rechten Maustaste auf</span><span class="sxs-lookup"><span data-stu-id="c1179-290">Right-click</span></span> | <span data-ttu-id="c1179-291">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="c1179-291">Menu button</span></span> | [<span data-ttu-id="c1179-292">ContextFlyout</span><span class="sxs-lookup"><span data-stu-id="c1179-292">ContextFlyout</span></span>](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.UIElement#Windows_UI_Xaml_UIElement_ContextFlyout) | <span data-ttu-id="c1179-293">Kontextmenüs</span><span class="sxs-lookup"><span data-stu-id="c1179-293">Context menus</span></span> |

## <a name="xy-focus-navigation-and-interaction"></a><span data-ttu-id="c1179-294">XY-Fokusnavigation und -interaktion</span><span class="sxs-lookup"><span data-stu-id="c1179-294">XY focus navigation and interaction</span></span>

<span data-ttu-id="c1179-295">Wenn Ihre App die korrekte Fokusnavigation für Tastaturen unterstützt, wird dies gut auf Gamepads und Fernbedienungen übertragen.</span><span class="sxs-lookup"><span data-stu-id="c1179-295">If your app supports proper focus navigation for keyboard, this will translate well to gamepad and remote control.</span></span>
<span data-ttu-id="c1179-296">Die Pfeiltastennavigation ist dem **Steuerkreuz** und dem **linken Stick** auf Gamepads zugeordnet. Interaktionen mit Benutzeroberflächenelementen sind der Taste **Eingabe/Auswahl** zugeordnet (siehe [Gamepad und Fernbedienung](#gamepad-and-remote-control)).</span><span class="sxs-lookup"><span data-stu-id="c1179-296">Navigation with the arrow keys is mapped to the **D-pad** (as well as the **left stick** on gamepad), and interaction with UI elements is mapped to the **Enter/Select** key (see [Gamepad and remote control](#gamepad-and-remote-control)).</span></span>

<span data-ttu-id="c1179-297">Viele Ereignisse und Eigenschaften werden von der Tastatur und dem Gamepad verwendet. Beide lösen die Ereignisse `KeyDown` und `KeyUp` aus, und beide navigieren nur zu Steuerelementen mit den Eigenschaften `IsTabStop="True"` und `Visibility="Visible"`.</span><span class="sxs-lookup"><span data-stu-id="c1179-297">Many events and properties are used by both keyboard and gamepad&mdash;they both fire `KeyDown` and `KeyUp` events, and they both will only navigate to controls that have the properties `IsTabStop="True"` and `Visibility="Visible"`.</span></span> <span data-ttu-id="c1179-298">Designanleitungen für die Tastaturnutzung finden Sie unter [Tastaturinteraktionen](keyboard-interactions.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-298">For keyboard design guidance, see [Keyboard interactions](keyboard-interactions.md).</span></span>

<span data-ttu-id="c1179-299">Wenn die Tastaturunterstützung ordnungsgemäß implementiert ist, wird Ihre App angemessen funktionieren. Es sind jedoch möglicherweise zusätzliche Arbeiten erforderlich, um jedes Szenario zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c1179-299">If keyboard support is implemented properly, your app will work reasonably well; however, there may be some extra work required to support every scenario.</span></span> <span data-ttu-id="c1179-300">Bedenken Sie die spezifischen Anforderungen Ihrer App, um die bestmögliche Benutzererfahrung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-300">Think about your app's specific needs to provide the best user experience possible.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1179-301">Der Mausmodus ist bei UWP-Apps auf Xbox One standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c1179-301">Mouse mode is enabled by default for UWP apps running on Xbox One.</span></span> <span data-ttu-id="c1179-302">Um den Mausmodus zu deaktivieren und die XY-Fokusnavigation zu aktivieren, legen Sie `Application.RequiresPointerMode=WhenRequested` fest.</span><span class="sxs-lookup"><span data-stu-id="c1179-302">To disable mouse mode and enable XY focus navigation, set `Application.RequiresPointerMode=WhenRequested`.</span></span>

### <a name="debugging-focus-issues"></a><span data-ttu-id="c1179-303">Debuggen von Fokusproblemen</span><span class="sxs-lookup"><span data-stu-id="c1179-303">Debugging focus issues</span></span>

<span data-ttu-id="c1179-304">Die Methode [FocusManager.GetFocusedElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.input.focusmanager.getfocusedelement.aspx) informiert Sie darüber, welches Element gerade den Fokus besitzt.</span><span class="sxs-lookup"><span data-stu-id="c1179-304">The [FocusManager.GetFocusedElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.input.focusmanager.getfocusedelement.aspx) method will tell you which element currently has focus.</span></span> <span data-ttu-id="c1179-305">Dies ist in Situationen hilfreich, in denen die Fokusanzeige nicht direkt sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-305">This is useful for situations where the location of the focus visual may not be obvious.</span></span> <span data-ttu-id="c1179-306">Mit dem folgenden Code können Sie die entsprechenden Informationen im Visual Studio-Ausgabefenster protokollieren:</span><span class="sxs-lookup"><span data-stu-id="c1179-306">You can log this information to the Visual Studio output window like so:</span></span>

```csharp
page.GotFocus += (object sender, RoutedEventArgs e) =>
{
    FrameworkElement focus = FocusManager.GetFocusedElement() as FrameworkElement;
    if (focus != null)
    {
        Debug.WriteLine("got focus: " + focus.Name + " (" +
            focus.GetType().ToString() + ")");
    }
};
```

<span data-ttu-id="c1179-307">Es gibt drei Hauptursachen für die fehlerhafte Funktion der XY-Navigation:</span><span class="sxs-lookup"><span data-stu-id="c1179-307">There are three common reasons why XY navigation might not work the way you expect:</span></span>

* <span data-ttu-id="c1179-308">Die [IsTabStop](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.istabstop.aspx)- oder [Visibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.visibility.aspx)-Eigenschaft ist falsch festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c1179-308">The [IsTabStop](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.istabstop.aspx) or [Visibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.visibility.aspx) property is set wrong.</span></span>
* <span data-ttu-id="c1179-309">Das Steuerelement mit dem Fokus ist größer, als Sie denken. Die XY-Navigation arbeitet mit der Gesamtgröße des Steuerelements ([ActualWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.actualwidth.aspx) und [ActualHeight](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.actualheight.aspx)) und nicht nur mit dem Teil des Steuerelements, das etwas darstellt.</span><span class="sxs-lookup"><span data-stu-id="c1179-309">The control getting focus is actually bigger than you think&mdash;XY navigation looks at the total size of the control ([ActualWidth](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.actualwidth.aspx) and [ActualHeight](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.actualheight.aspx)), not just the portion of the control that renders something interesting.</span></span>
* <span data-ttu-id="c1179-310">Ein Steuerelement, das den Fokus erhalten kann, befindet sich über einem anderen Steuerelement. Die XY-Navigation unterstützt keine überlappenden Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="c1179-310">One focusable control is on top of another&mdash;XY navigation doesn't support controls that are overlapped.</span></span>

<span data-ttu-id="c1179-311">Wenn die XY-Navigation nach dem Beheben dieser drei Probleme noch immer nicht wie erwartet funktioniert, kann das Element, das den Fokus erhalten soll, mit der in [Überschreiben der Standardnavigation](#overriding-the-default-navigation) beschriebenen Methode manuell festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-311">If XY navigation is still not working the way you expect after fixing these issues, you can manually point to the element that you want to get focus using the method described in [Overriding the default navigation](#overriding-the-default-navigation).</span></span>

<span data-ttu-id="c1179-312">Wenn die XY-Navigation wie beabsichtigt funktioniert, die Fokusanzeige jedoch nicht sichtbar ist, kann dies von einem der folgenden Probleme verursacht werden:</span><span class="sxs-lookup"><span data-stu-id="c1179-312">If XY navigation is working as intended but no focus visual is displayed, one of the following issues may be the cause:</span></span>

* <span data-ttu-id="c1179-313">Sie haben eine neue Vorlage auf das Steuerelement angewendet und keine Fokusanzeige einbezogen.</span><span class="sxs-lookup"><span data-stu-id="c1179-313">You re-templated the control and didn't include a focus visual.</span></span> <span data-ttu-id="c1179-314">Legen Sie die Eigenschaft `UseSystemFocusVisuals="True"` fest, oder fügen Sie manuell eine Fokusanzeige hinzu.</span><span class="sxs-lookup"><span data-stu-id="c1179-314">Set `UseSystemFocusVisuals="True"` or add a focus visual manually.</span></span>
* <span data-ttu-id="c1179-315">Sie haben den Fokus über den Aufruf von `Focus(FocusState.Pointer)` verschoben.</span><span class="sxs-lookup"><span data-stu-id="c1179-315">You moved the focus by calling `Focus(FocusState.Pointer)`.</span></span> <span data-ttu-id="c1179-316">Der [FocusState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.focusstate.aspx)-Parameter steuert, was mit der Fokusanzeige geschieht.</span><span class="sxs-lookup"><span data-stu-id="c1179-316">The [FocusState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.focusstate.aspx) parameter controls what happens to the focus visual.</span></span> <span data-ttu-id="c1179-317">Im Allgemeinen sollten Sie den Parameter auf `FocusState.Programmatic` festlegen. So bleibt die Fokusanzeige sichtbar, wenn sie vorher sichtbar war, und wird ausgeblendet, wenn sie vorher ausgeblendet war.</span><span class="sxs-lookup"><span data-stu-id="c1179-317">Generally you should set this to `FocusState.Programmatic`, which keeps the focus visual visible if it was visible before, and hidden if it was hidden before.</span></span>

<span data-ttu-id="c1179-318">Im Rest dieses Abschnitts werden allgemeine Designprobleme bei der XY-Navigation sowie verschiedene Lösungswege besprochen.</span><span class="sxs-lookup"><span data-stu-id="c1179-318">The rest of this section goes into detail about common design challenges when using XY navigation, and offers several ways to solve them.</span></span>

### <a name="inaccessible-ui"></a><span data-ttu-id="c1179-319">Nicht zugängliche Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="c1179-319">Inaccessible UI</span></span>

<span data-ttu-id="c1179-320">Da die XY-Fokusnavigation den Benutzer auf die Navigation nach oben, unten, links und rechts einschränkt, gibt es möglicherweise Szenarien, in denen auf Teile der Benutzeroberfläche nicht zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-320">Because XY focus navigation limits the user to moving up, down, left, and right, you may end up with scenarios where parts of the UI are inaccessible.</span></span>
<span data-ttu-id="c1179-321">Das folgende Diagramm zeigt ein Beispiel für die Art von Benutzeroberflächenlayout, das die XY-Fokusnavigation nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1179-321">The following diagram illustrates an example of the kind of UI layout that XY focus navigation doesn't support.</span></span>
<span data-ttu-id="c1179-322">Beachten Sie, dass das Element in der Mitte bei Verwendung von Gamepads/Fernbedienungen nicht zugänglich ist, da die vertikale und horizontale Navigation Priorität erhält und die Priorität des mittleren Elements nie hoch genug sein wird, um den Fokus erhalten.</span><span class="sxs-lookup"><span data-stu-id="c1179-322">Note that the element in the middle is not accessible by using gamepad/remote because the vertical and horizontal navigation will be prioritized and the middle element will never be high enough priority to get focus.</span></span>

![Elemente in vier Ecken mit nicht zugänglichem Element in der Mitte](images/designing-for-tv/2d-navigation-best-practices-ui-layout-to-avoid.png)

<span data-ttu-id="c1179-324">Wenn die Elemente auf der Benutzeroberfläche aus irgendeinem Grund nicht neu angeordnet werden können, verwenden Sie eine der im nächsten Abschnitt erläuterten Techniken, um das Standardfokusverhalten zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="c1179-324">If for some reason rearranging the UI is not possible, use one of the techniques discussed in the next section to override the default focus behavior.</span></span>

### <a name="overriding-the-default-navigation"></a><span data-ttu-id="c1179-325">Überschreiben der Standardnavigation</span><span class="sxs-lookup"><span data-stu-id="c1179-325">Overriding the default navigation</span></span>

<span data-ttu-id="c1179-326">Die universelle Windows-Plattform versucht zwar, dem Benutzer eine sinnvolle Navigation mit dem Steuerkreuz (D-Pad)/linken Stick zu bieten, sie kann jedoch kein optimales Verhalten für die Ziele Ihrer App garantieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-326">While the Universal Windows Platform tries to ensure that D-pad/left stick navigation makes sense to the user, it cannot guarantee behavior that is optimized for your app's intentions.</span></span>
<span data-ttu-id="c1179-327">Die beste Möglichkeit, um sicherzustellen, dass die Navigation für Ihre App optimiert ist, besteht im Testen mit einem Gamepad. So können Sie überprüfen, ob Benutzer auf alle Benutzeroberflächenelemente auf eine Weise zugreifen können, die für die Szenarien Ihrer App sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-327">The best way to ensure that navigation is optimized for your app is to test it with a gamepad and confirm that every UI element can be accessed by the user in a manner that makes sense for your app's scenarios.</span></span> <span data-ttu-id="c1179-328">Wenn die Szenarien Ihrer App Verhaltensweisen erfordern, die durch die vorhandene XY-Fokusnavigation nicht bereitgestellt werden können, ziehen Sie die Empfehlungen in den folgenden Abschnitten in Betracht und/oder überschreiben das Verhalten, um den Fokus auf ein logisches Element zu setzen.</span><span class="sxs-lookup"><span data-stu-id="c1179-328">In case your app's scenarios call for a behavior not achieved through the XY focus navigation provided, consider following the recommendations in the following sections and/or overriding the behavior to place the focus on a logical item.</span></span>

<span data-ttu-id="c1179-329">Der folgende Codeausschnitt zeigt, wie Sie das Verhalten der XY-Fokusnavigation überschreiben können:</span><span class="sxs-lookup"><span data-stu-id="c1179-329">The following code snippet shows how you might override the XY focus navigation behavior:</span></span>

```xml
<StackPanel>
    <Button x:Name="MyBtnLeft"
            Content="Search" />
    <Button x:Name="MyBtnRight"
            Content="Delete"/>
    <Button x:Name="MyBtnTop"
            Content="Update" />
    <Button x:Name="MyBtnDown"
            Content="Undo" />
    <Button Content="Home"  
            XYFocusLeft="{x:Bind MyBtnLeft}"
            XYFocusRight="{x:Bind MyBtnRight}"
            XYFocusDown="{x:Bind MyBtnDown}"
            XYFocusUp="{x:Bind MyBtnTop}" />
</StackPanel>
```

<span data-ttu-id="c1179-330">Wenn sich der Fokus auf der `Home`-Schaltfläche und der Benutzer nach links navigiert, wird der Fokus zur `MyBtnLeft`-Schaltfläche verschoben. Wenn der Benutzer nach rechts navigiert, wird der Fokus zur `MyBtnRight`-Schaltfläche verschoben usw.</span><span class="sxs-lookup"><span data-stu-id="c1179-330">In this case, when focus is on the `Home` button and the user navigates to the left, focus will move to the `MyBtnLeft` button; if the user navigates to the right, focus will move to the `MyBtnRight` button; and so on.</span></span>

<span data-ttu-id="c1179-331">Um zu verhindern, dass der Fokus von einem Steuerelement in eine bestimmten Richtung verschoben wird, verwenden Sie die `XYFocus*`-Eigenschaft, um auf das gleiche Steuerelement zu zeigen:</span><span class="sxs-lookup"><span data-stu-id="c1179-331">To prevent the focus from moving from a control in a certain direction, use the `XYFocus*` property to point it at the same control:</span></span>

```xml
<Button Name="HomeButton"  
        Content="Home"  
        XYFocusLeft ="{x:Bind HomeButton}" />
```

<span data-ttu-id="c1179-332">Mithilfe dieser `XYFocus`-Eigenschaften kann ein übergeordnetes Steuerelement auch die Navigation der untergeordneten Elemente erzwingen, wenn sich der nächste Fokuskandidat außerhalb der visuellen Struktur befindet – es sei denn, das untergeordnete Element, das den Fokus besitzt, verwendet die gleiche `XYFocus`-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="c1179-332">Using these `XYFocus` properties, a control parent can also force the navigation of its children when the next focus candidate is out of its visual tree, unless the child who has the focus uses the same `XYFocus` property.</span></span>

```xml
<StackPanel Orientation="Horizontal" Margin="300,300">
    <UserControl XYFocusRight="{x:Bind ButtonThree}">
        <StackPanel>
            <Button Content="One"/>
            <Button Content="Two"/>
        </StackPanel>
    </UserControl>
    <StackPanel>
        <Button x:Name="ButtonThree" Content="Three"/>
        <Button Content="Four"/>
    </StackPanel>
</StackPanel>
```

<span data-ttu-id="c1179-333">Im obigen Beispiel gilt: Wenn `Button`2 den Fokus besitzt und der Benutzer nach rechts navigiert, ist `Button`4 der beste Fokuskandidat. Der Fokus wechselt jedoch zu `Button`3, da das übergeordnete `UserControl`-Element dies erzwingt, wenn die visuelle Struktur verlassen wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-333">In the sample above, if the focus is on `Button` Two and the user navigates to the right, the best focus candidate is `Button` Four; however, the focus is moved to `Button` Three because the parent `UserControl` forces it to navigate there when it is out of its visual tree.</span></span>

### <a name="path-of-least-clicks"></a><span data-ttu-id="c1179-334">Pfad der wenigsten Klicks</span><span class="sxs-lookup"><span data-stu-id="c1179-334">Path of least clicks</span></span>

<span data-ttu-id="c1179-335">Ermöglichen Sie Benutzern, häufig ausgeführte Aktionen mit möglichst wenigen Klicks auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c1179-335">Try to allow the user to perform the most common tasks in the least number of clicks.</span></span> <span data-ttu-id="c1179-336">Im folgenden Beispiel befindet sich [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) zwischen der **Play**-Schaltfläche (die zunächst den Fokus erhält) und einem häufig verwendeten Element, sodass sich zwischen zwei Aktionen mit Priorität ein nicht notwendiges Element befindet.</span><span class="sxs-lookup"><span data-stu-id="c1179-336">In the following example, the [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) is placed between the **Play** button (which initially gets focus) and a commonly used element, so that an unnecessary element is placed in between priority tasks.</span></span>

![Bewährte Methoden für die Navigation stellen den Pfad der wenigsten Klicks bereit](images/designing-for-tv/2d-navigation-best-practices-provide-path-with-least-clicks.png)

<span data-ttu-id="c1179-338">Im folgenden Beispiel befindet sich [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) stattdessen oberhalb der **Play**-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="c1179-338">In the following example, the [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) is placed above the **Play** button instead.</span></span>
<span data-ttu-id="c1179-339">Durch das einfache Neuanordnen der Benutzeroberfläche, sodass sich nicht notwendige Elemente nicht zwischen Aktionen mit Priorität befinden, wird die Verwendbarkeit Ihrer App erheblich verbessert.</span><span class="sxs-lookup"><span data-stu-id="c1179-339">Simply rearranging the UI so that unnecessary elements are not placed in between priority tasks will greatly improve your app's usability.</span></span>

![TextBlock an eine Stelle oberhalb der Play-Schaltfläche verschoben, sodass sie sich nicht mehr zwischen Aktionen mit Priorität befindet](images/designing-for-tv/2d-navigation-best-practices-provide-path-with-least-clicks-2.png)

### <a name="commandbar-and-contextflyout"></a><span data-ttu-id="c1179-341">CommandBar und ContextFlyout</span><span class="sxs-lookup"><span data-stu-id="c1179-341">CommandBar and ContextFlyout</span></span>

<span data-ttu-id="c1179-342">Bei Verwendung einer [CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx) müssen Sie das Problem hinsichtlich Bildläufen durch Listen berücksichtigen, wie in [Problem: Benutzeroberflächenelemente nach langen bildlauffähigen Listen/Rastern](#problem-ui-elements-located-after-long-scrolling-list-grid) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c1179-342">When using a [CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx), keep in mind the issue of scrolling through a list as mentioned in [Problem: UI elements located after long scrolling list/grid](#problem-ui-elements-located-after-long-scrolling-list-grid).</span></span> <span data-ttu-id="c1179-343">Die folgende Abbildung zeigt ein Benutzeroberflächenlayout mit `CommandBar` am Ende einer Liste/eines Rasters.</span><span class="sxs-lookup"><span data-stu-id="c1179-343">The following image shows a UI layout with the `CommandBar` on the bottom of a list/grid.</span></span> <span data-ttu-id="c1179-344">Der Benutzer müsste einen Bildlauf ganz nach unten durch die Liste/das Rasters ausführen, um zu `CommandBar` zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="c1179-344">The user would need to scroll all the way down through the list/grid to reach the `CommandBar`.</span></span>

![CommandBar am unteren Ende einer Liste/eines Rasters](images/designing-for-tv/2d-navigation-best-practices-commandbar-and-contextflyout.png)

<span data-ttu-id="c1179-346">Was geschieht, wenn Sie `CommandBar` an einer Stelle *oberhalb* der Liste/des Rasters platzieren?</span><span class="sxs-lookup"><span data-stu-id="c1179-346">What if you put the `CommandBar` *above* the list/grid?</span></span> <span data-ttu-id="c1179-347">Auch wenn ein Benutzer, der einen Bildlauf nach unten durch die Liste/das Raster ausführt, einen Bildlauf zurück nach oben ausführen müsste, um zu `CommandBar` zu gelangen, bedeutet dies etwas weniger Navigationsaufwand als bei der vorherigen Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c1179-347">While a user who scrolled down the list/grid would have to scroll back up to reach the `CommandBar`, it is slightly less navigation than the previous configuration.</span></span> <span data-ttu-id="c1179-348">Beachten Sie, dass dies voraussetzt, dass sich der anfängliche Fokus Ihrer App neben oder oberhalb von `CommandBar` befindet. Dieser Ansatz funktioniert weniger gut, wenn sich der anfängliche Fokus unterhalb der Liste/des Rasters befindet.</span><span class="sxs-lookup"><span data-stu-id="c1179-348">Note that this is assuming that your app's initial focus is placed next to or above the `CommandBar`; this approach won't work as well if the initial focus is below the list/grid.</span></span> <span data-ttu-id="c1179-349">Wenn diese `CommandBar`-Elemente globale Aktionselemente sind, auf die nicht sehr häufig zugegriffen werden muss (beispielsweise eine **Sync**-Schaltfläche), ist es möglicherweise zulässig, diese oberhalb der Liste/des Rasters zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-349">If these `CommandBar` items are global action items that don't have to be accessed very often (such as a **Sync** button), it may be acceptable to have them above the list/grid.</span></span>

<span data-ttu-id="c1179-350">Zwar ist das vertikale Stapeln der `CommandBar`-Elemente nicht möglich, die Platzierung gegen die Bildlaufrichtung (etwa links oder rechts von einer vertikal laufenden Liste oder über/unter einer horizontal laufenden Liste) ist eine weitere Option, die Sie nutzen können, wenn dies gut zu Ihrem Benutzeroberflächenlayout passt.</span><span class="sxs-lookup"><span data-stu-id="c1179-350">While you can't stack a `CommandBar`'s items vertically, placing them against the scroll direction (for example, to the left or right of a vertically scrolling list, or the top or bottom of a horizontally scrolling list) is another option you may want to consider if it works well for your UI layout.</span></span>

<span data-ttu-id="c1179-351">Wenn Ihre App eine `CommandBar` umfasst, auf deren Elemente die Benutzer zugreifen müssen, sollten Sie diese Elemente möglicherweise innerhalb einer [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx)-Eigenschaft platzieren und sie aus der `CommandBar` entfernen.</span><span class="sxs-lookup"><span data-stu-id="c1179-351">If your app has a `CommandBar` whose items need to be readily accessible by users, you may want to consider placing these items inside a [ContextFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextflyout.aspx) and removing them from the `CommandBar`.</span></span> `ContextFlyout` <span data-ttu-id="c1179-352">ist eine Eigenschaft von [UIElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.aspx) und stellt das dem Element zugeordnete [Kontextmenü](../controls-and-patterns/dialogs-popups-menus.md) dar.</span><span class="sxs-lookup"><span data-stu-id="c1179-352">is a property of [UIElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.aspx) and is the [context menu](../controls-and-patterns/dialogs-popups-menus.md) associated with that element.</span></span> <span data-ttu-id="c1179-353">Wenn Sie auf einem PC mit der rechten Maustaste auf ein Element mit einem `ContextFlyout` klicken, wird das Kontextmenü eingeblendet.</span><span class="sxs-lookup"><span data-stu-id="c1179-353">On PC, when you right-click on an element with a `ContextFlyout`, that context menu will pop up.</span></span> <span data-ttu-id="c1179-354">Auf Xbox One geschieht dies beim Drücken der **Menü**-Taste, während ein entsprechendes Element den Fokus hat.</span><span class="sxs-lookup"><span data-stu-id="c1179-354">On Xbox One, this will happen when you press the **Menu** button while the focus is on such an element.</span></span>

<!--The following XAML code demonstrates a simple `ContextFlyout`:

```xml
<Button HorizontalAlignment="Center"
        Content="Context Flyout">
    <Button.ContextFlyout>
        <MenuFlyout>
            <MenuFlyoutItem Text="Item 1"/>
        </MenuFlyout>
    </Button.ContextFlyout>
</Button>
```

In the above example, when you press the **Menu** button while the [Button](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx) has focus, the context menu appears with the menu item labeled **Item 1**.

`ContextFlyout` takes any element of type [FlyoutBase](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.aspx); however, most of the time you will likely use [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.aspx) or [MenuFlyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.menuflyout.aspx).

Alternatively, you can listen for the [ContextRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.contextrequested.aspx) event, which occurs when the user has completed a context input gesture (pressing the **Menu** button). In this case you can, in the code-behind, create the context menu, attach it to the **UIElement**, and show the flyout when the event is raised.

The following C# code demonstrates a simple example of this:

```csharp
MenuFlyout myFlyout = new MenuFlyout();
MenuFlyoutItem item1 = new MenuFlyoutItem();
item1.Text = "Item 1";
myFlyout.Items.Add(item1);
MyButton.ContextFlyout = myFlyout;

private void MyButton_ContextRequested(UIElement sender, ContextRequestedEventArgs args)
{
    Point point = new Point(0, 0);
    if (args.TryGetPosition(sender, out point)
    {
        myFlyout.ShowAt(sender, point);
    }
    else
    {
        myFlyout.ShowAt(sender as FrameworkElement);
    }
}
```
> **Note** Don't use both of these options, as `ContextFlyout` already handles the `ContextRequested` event.-->

### <a name="ui-layout-challenges"></a><span data-ttu-id="c1179-355">Herausforderungen beim UI-Layout</span><span class="sxs-lookup"><span data-stu-id="c1179-355">UI layout challenges</span></span>

<span data-ttu-id="c1179-356">Einige UI-Layouts sind aufgrund der Natur der XY-Fokusnavigation anspruchsvoller und sollten jeweils einzeln für sich beurteilt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-356">Some UI layouts are more challenging due to the nature of XY focus navigation, and should be evaluated on a case-by-case basis.</span></span> <span data-ttu-id="c1179-357">Es gibt zwar keine einzige „richtige“ Lösung, und Ihre Entscheidung muss auf den Anforderungen Ihrer App basieren, es stehen jedoch einige Techniken zur Verfügung, die Ihnen dabei helfen können, ein hervorragendes TV-Erlebnis bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-357">While there is no single "right" way, and which solution you choose is up to your app's specific needs, there are some techniques that you can employ to make a great TV experience.</span></span>

<span data-ttu-id="c1179-358">Um dies zu verdeutlichen, sehen wir uns eine imaginäre App an, die einige dieser Herausforderungen sowie die entsprechenden Techniken zur Behebung illustriert.</span><span class="sxs-lookup"><span data-stu-id="c1179-358">To understand this better, let's look at an imaginary app that illustrates some of these issues and techniques to overcome them.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-359">Diese fiktive App dient dazu, UI-Probleme und mögliche Lösungen zu veranschaulichen. Die Benutzerfreundlichkeit wird dabei nicht berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-359">This fake app is meant to illustrate UI problems and potential solutions to them, and is not intended to show the best user experience for your particular app.</span></span>

<span data-ttu-id="c1179-360">Nachfolgend sehen Sie eine fiktive Immobilien-App, die eine Liste zum Verkauf stehender Häuser, eine Karte, Beschreibungen von Immobilien sowie weitere Informationen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-360">The following is an imaginary real estate app which shows a list of houses available for sale, a map, a description of a property, and other information.</span></span> <span data-ttu-id="c1179-361">Diese App stellt Sie vor drei Herausforderungen, denen Sie mit den folgenden Techniken begegnen können:</span><span class="sxs-lookup"><span data-stu-id="c1179-361">This app poses three challenges that you can overcome by using the following techniques:</span></span>

- [<span data-ttu-id="c1179-362">Neuanordnung der UI</span><span class="sxs-lookup"><span data-stu-id="c1179-362">UI rearrange</span></span>](#ui-rearrange)
- [<span data-ttu-id="c1179-363">Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="c1179-363">Focus engagement</span></span>](#engagement)
- [<span data-ttu-id="c1179-364">Mausmodus</span><span class="sxs-lookup"><span data-stu-id="c1179-364">Mouse mode</span></span>](#mouse-mode)

![Fiktive Immobilien-App](images/designing-for-tv/2d-focus-navigation-and-interaction-real-estate-app.png)

#### <span data-ttu-id="c1179-366">Problem: UI-Elemente, die sich hinter einer langen Bildlaufliste oder einem Raster befinden <a name="problem-ui-elements-located-after-long-scrolling-list-grid"></a></span><span class="sxs-lookup"><span data-stu-id="c1179-366">Problem: UI elements located after long scrolling list/grid <a name="problem-ui-elements-located-after-long-scrolling-list-grid"></a></span></span>

<span data-ttu-id="c1179-367">Die [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) der Eigenschaften in der folgenden Abbildung ist eine sehr lange Bildlaufliste.</span><span class="sxs-lookup"><span data-stu-id="c1179-367">The [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) of properties shown in the following image is a very long scrolling list.</span></span> <span data-ttu-id="c1179-368">Wenn [Engagement](#focus-engagement) *nicht* für die `ListView` erforderlich ist, wenn der Benutzer zu der Liste navigiert, wird der Fokus auf das erste Element in der Liste gesetzt.</span><span class="sxs-lookup"><span data-stu-id="c1179-368">If [engagement](#focus-engagement) is *not* required on the `ListView`, when the user navigates to the list, focus will be placed on the first item in the list.</span></span> <span data-ttu-id="c1179-369">Damit der Benutzer zur Schaltfläche **Zurück** oder **Weiter** gelangen kann, muss er alle Elemente der Liste durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="c1179-369">For the user to reach the **Previous** or **Next** button, they must go through all the items in the list.</span></span> <span data-ttu-id="c1179-370">In Fällen wie diese, bei denen der Benutzer die gesamte Liste mühsam durchlaufen muss – d.h. wenn die Liste ganz einfach zu lang ist, um noch akzeptablen Benutzerkomfort zu ermöglichen – sollten Sie andere Optionen erwägen.</span><span class="sxs-lookup"><span data-stu-id="c1179-370">In cases like this where requiring the user to traverse the entire list is painful&mdash;that is, when the list is not short enough for this experience to be acceptable&mdash;you may want to consider other options.</span></span>

![Immobilien-App: Eine Liste mit 50 Elementen erfordert 51 Klicks, bis die Schaltflächen am Ende erreicht sind](images/designing-for-tv/2d-focus-navigation-and-interaction-real-estate-app-list.png)

#### <a name="solutions"></a><span data-ttu-id="c1179-372">Lösungen</span><span class="sxs-lookup"><span data-stu-id="c1179-372">Solutions</span></span>

**<span data-ttu-id="c1179-373">Neuanordnung der UI <a name="ui-rearrange"></a></span><span class="sxs-lookup"><span data-stu-id="c1179-373">UI rearrange <a name="ui-rearrange"></a></span></span>**

<span data-ttu-id="c1179-374">Sofern nicht der anfängliche Fokus auf das Ende der Seite gesetzt ist, sind über einer langen Bildlaufliste platzierte UI-Elemente typischerweise einfacher erreichbar, als solche unterhalb einer solchen Liste.</span><span class="sxs-lookup"><span data-stu-id="c1179-374">Unless your initial focus is placed at the bottom of the page, UI elements placed above a long scrolling list are typically more easily accessible than if placed below.</span></span>
<span data-ttu-id="c1179-375">Wenn dieses neue Layout für andere Geräte funktioniert, kann das Ändern des Layouts für alle Gerätefamilien kostengünstiger sein als das Vornehmen spezieller UI-Änderungen nur für die Xbox One.</span><span class="sxs-lookup"><span data-stu-id="c1179-375">If this new layout works for other devices, changing the layout for all device families instead of doing special UI changes just for Xbox One might be a less costly approach.</span></span>
<span data-ttu-id="c1179-376">Weiterhin gilt, dass die Platzierung von UI-Elementen gegen die Bildlaufrichtung (d.h. horizontal bei einer vertikal laufenden Liste oder vertikal bei einer horizontal laufenden Liste) den Benutzerkomfort noch weiter erhöht.</span><span class="sxs-lookup"><span data-stu-id="c1179-376">Additionally, placing UI elements against the scrolling direction (that is, horizontally to a vertically scrolling list, or vertically to a horizontally scrolling list) will make for even better accessibility.</span></span>

![Immobilien-App: Platzieren von Schaltflächen oberhalb einer langen Bildlaufliste](images/designing-for-tv/2d-focus-navigation-and-interaction-ui-rearrange.png)

**<span data-ttu-id="c1179-378">Fokusaktivierung <a name="engagement"></a></span><span class="sxs-lookup"><span data-stu-id="c1179-378">Focus engagement <a name="engagement"></a></span></span>**

<span data-ttu-id="c1179-379">Ist die Aktivierung *erforderlich*, wird die gesamte `ListView` zu einem einzigen Fokusziel.</span><span class="sxs-lookup"><span data-stu-id="c1179-379">When engagement is *required*, the entire `ListView` becomes a single focus target.</span></span> <span data-ttu-id="c1179-380">Der Benutzer kann die Inhalte der Liste übergehen, um zum nächsten fokussierbaren Element zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="c1179-380">The user will be able to bypass the contents of the list to get to the next focusable element.</span></span> <span data-ttu-id="c1179-381">Erfahren Sie mehr darüber, welche Steuerelemente die Aktivierung unterstützen, und wie Sie sie in der [Fokusaktivierung](#focus-engagement) verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c1179-381">Read more about what controls support engagement and how to use them in [Focus engagement](#focus-engagement).</span></span>

![Immobilien-App: Einstellen der Aktivierung als erforderlich, damit die Schaltflächen „Zurück/Weiter“ mit nur einem Klick erreicht werden können](images/designing-for-tv/2d-focus-navigation-and-interaction-engagement.png)

#### <a name="problem-scrollviewer-without-any-focusable-elements"></a><span data-ttu-id="c1179-383">Problem: ScrollViewer ohne fokussierbare Elemente</span><span class="sxs-lookup"><span data-stu-id="c1179-383">Problem: ScrollViewer without any focusable elements</span></span>

<span data-ttu-id="c1179-384">Da die XY-Fokusnavigation darauf basiert, dass jeweils zu einem fokussierbaren UI-Element navigiert wird, kann ein [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) ohne fokussierbare Elemente (etwa einer, der, wie der in diesem Beispiel, nur Text enthält) ein Szenario verursachen, in dem der Benutzer nicht alle Inhalte in dem `ScrollViewer` anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-384">Because XY focus navigation relies on navigating to one focusable UI element at a time, a [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) that doesn't contain any focusable elements (such as one with only text, as in this example) may cause a scenario where the user isn't able to view all of the content in the `ScrollViewer`.</span></span>
<span data-ttu-id="c1179-385">Lösungen für dieses und ähnliche Szenarien finden Sie unter [Fokusaktivierung](#focus-engagement).</span><span class="sxs-lookup"><span data-stu-id="c1179-385">For solutions to this and other related scenarios, see [Focus engagement](#focus-engagement).</span></span>

![Immobilien-App: ScrollViewer mit lediglich Text](images/designing-for-tv/2d-focus-navigation-and-interaction-scrollviewer.png)

#### <a name="problem-free-scrolling-ui"></a><span data-ttu-id="c1179-387">Problem: UI mit freiem Bildlauf</span><span class="sxs-lookup"><span data-stu-id="c1179-387">Problem: Free-scrolling UI</span></span>

<span data-ttu-id="c1179-388">Wenn Ihre App eine UI mit freiem Bildlauf benötigt, etwa eine Zeichenoberfläche oder, wie in diesem Beispiel, eine Karte, ist die XY-Fokus-Navigation ganz einfach nicht geeignet.</span><span class="sxs-lookup"><span data-stu-id="c1179-388">When your app requires a freely scrolling UI, such as a drawing surface or, in this example, a map, XY focus navigation simply doesn't work.</span></span>
<span data-ttu-id="c1179-389">In solchen Fällen können Sie den [Mausmodus](#mouse-mode) aktivieren, damit der Benutzer in einem UI-Element frei navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-389">In such cases, you can turn on [mouse mode](#mouse-mode) to allow the user to navigate freely inside a UI element.</span></span>

![Karten-UI-Element im Mausmodus](images/designing-for-tv/map-mouse-mode.png)

## <a name="mouse-mode"></a><span data-ttu-id="c1179-391">Mausmodus</span><span class="sxs-lookup"><span data-stu-id="c1179-391">Mouse mode</span></span>

<span data-ttu-id="c1179-392">Wie in [XY-Fokusnavigation und -interaktion](#xy-focus-navigation-and-interaction) beschrieben, wird der Fokus auf Xbox One mittels eines XY-Navigationssystems verschoben, sodass Benutzer den Fokus von Steuerelement zu Steuerelement verschieben können, indem sie nach oben, unten, links und rechts navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-392">As described in [XY focus navigation and interaction](#xy-focus-navigation-and-interaction), on Xbox One the focus is moved by using an XY navigation system, allowing the user to shift the focus from control to control by moving up, down, left, and right.</span></span>
<span data-ttu-id="c1179-393">Einige Steuerelemente wie [WebView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.aspx) und [MapControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.maps.mapcontrol.aspx) erfordern jedoch eine mausähnliche Interaktion, bei der Benutzer mit dem Zeiger auf eine beliebige Stelle innerhalb der Grenzen des Steuerelements zeigen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-393">However, some controls, such as [WebView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.aspx) and [MapControl](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.maps.mapcontrol.aspx), require a mouse-like interaction where users can freely move the pointer inside the boundaries of the control.</span></span>
<span data-ttu-id="c1179-394">Es gibt auch einige Apps, für die es sinnvoll ist, wenn Benutzer den Zeiger über die gesamte Seite bewegen können, sodass sie mit Gamepads/Fernbedienungen eine Erfahrung ähnlich wie am PC mit einer Maus haben.</span><span class="sxs-lookup"><span data-stu-id="c1179-394">There are also some apps where it makes sense for the user to be able to move the pointer across the entire page, having an experience with gamepad/remote similar to what users can find on a PC with a mouse.</span></span>

<span data-ttu-id="c1179-395">Für diese Szenarien sollten Sie einen Zeiger (Mausmodus) für die gesamte Seite oder ein Steuerelement auf einer Seite anfordern.</span><span class="sxs-lookup"><span data-stu-id="c1179-395">For these scenarios, you should request a pointer (mouse mode) for the entire page, or on a control inside a page.</span></span>
<span data-ttu-id="c1179-396">Ihre App könnte beispielsweise eine Seite mit einem `WebView`-Steuerelement haben, das den Mausmodus nur innerhalb des Steuerelements und überall sonst eine XY-Fokusnavigation verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1179-396">For example, your app could have a page that has a `WebView` control that uses mouse mode only while inside the control, and XY focus navigation everywhere else.</span></span>
<span data-ttu-id="c1179-397">Um einen Zeiger anzufordern, können Sie angeben, ob er verwendet werden soll, **wenn ein Steuerelement oder eine Seite aktiviert ist** oder **wenn eine Seite den Fokus hat**.</span><span class="sxs-lookup"><span data-stu-id="c1179-397">To request a pointer, you can specify whether you want it **when a control or page is engaged** or **when a page has focus**.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-398">Das Anfordern eines Zeigers, wenn ein Steuerelement den Fokus erhält, wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1179-398">Requesting a pointer when a control gets focus is not supported.</span></span>

<span data-ttu-id="c1179-399">Bei XAML und bei gehosteten Web-Apps, die auf Xbox One ausgeführt werden, ist der Mausmodus standardmäßig für die gesamte App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c1179-399">For both XAML and hosted web apps running on Xbox One, mouse mode is turned on by default for the entire app.</span></span> <span data-ttu-id="c1179-400">Es wird dringend empfohlen, den Mausmodus zu deaktivieren und die App für die XY-Navigation zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-400">It is highly recommended that you turn this off and optimize your app for XY navigation.</span></span> <span data-ttu-id="c1179-401">Legen Sie dazu die `Application.RequiresPointerMode`-Eigenschaft auf `WhenRequested` fest. So können Sie den Mausmodus nur dann aktivieren, wenn ein Steuerelement oder eine Seite diesen erfordert.</span><span class="sxs-lookup"><span data-stu-id="c1179-401">To do this, set the `Application.RequiresPointerMode` property to `WhenRequested` so that you only enable mouse mode when a control or page calls for it.</span></span>

<span data-ttu-id="c1179-402">Nutzen Sie in Ihrer XAML-App hierfür den folgenden Code in Ihrer `App`-Klasse:</span><span class="sxs-lookup"><span data-stu-id="c1179-402">To do this in a XAML app, use the following code in your `App` class:</span></span>

```csharp
public App()
{
    this.InitializeComponent();
    this.RequiresPointerMode =
        Windows.UI.Xaml.ApplicationRequiresPointerMode.WhenRequested;
    this.Suspending += OnSuspending;
}
```

<span data-ttu-id="c1179-403">Weitere Informationen, einschließlich HTML/JavaScript-Beispielcode, finden Sie unter [So deaktivieren Sie den Mausmodus](../xbox-apps/how-to-disable-mouse-mode.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-403">For more information, including sample code for HTML/JavaScript, see [How to disable mouse mode](../xbox-apps/how-to-disable-mouse-mode.md).</span></span>

<span data-ttu-id="c1179-404">Das folgende Diagramm zeigt die Tastenzuordnungen für Gamepads/Remotesteuerungen im Mausmodus.</span><span class="sxs-lookup"><span data-stu-id="c1179-404">The following diagram shows the button mappings for gamepad/remote in mouse mode.</span></span>

![Tastenzuordnungen für Gamepads/Fernbedienungen im Mausmodus](images/designing-for-tv/10ft_infographics_mouse-mode.png)

> [!NOTE]
> <span data-ttu-id="c1179-406">Der Mausmodus wird nur auf Xbox One mit Gamepad/Fernbedienung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1179-406">Mouse mode is only supported on Xbox One with gamepad/remote.</span></span> <span data-ttu-id="c1179-407">Bei anderen Gerätefamilien und Eingabetypen wird er stillschweigend ignoriert.</span><span class="sxs-lookup"><span data-stu-id="c1179-407">On other device families and input types it is silently ignored.</span></span>

<span data-ttu-id="c1179-408">Verwenden Sie die `RequiresPointer`-Eigenschaft für ein Steuerelement oder eine Seite, um den Mausmodus zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-408">Use the `RequiresPointer` property on a control or page to activate mouse mode on it.</span></span> `RequiresPointer` <span data-ttu-id="c1179-409">hat drei mögliche Werte: `Never` (Standardwert), `WhenEngaged` und `WhenFocused`.</span><span class="sxs-lookup"><span data-stu-id="c1179-409">has three possible values: `Never` (the default value), `WhenEngaged`, and `WhenFocused`.</span></span>

> [!NOTE]
> `RequiresPointer` <span data-ttu-id="c1179-410">ist eine neue API, die noch nicht dokumentiert ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-410">is a new API and not yet documented.</span></span>

<!--TODO: Link to doc-->

### <a name="activating-mouse-mode-on-a-control"></a><span data-ttu-id="c1179-411">Aktivieren des Mausmodus für ein Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c1179-411">Activating mouse mode on a control</span></span>

<span data-ttu-id="c1179-412">Wenn der Benutzer ein Steuerelement mit `RequiresPointer="WhenEngaged"` verwendet, wird der Mausmodus für das Steuerelement aktiviert, bis der Benutzer es nicht mehr verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1179-412">When the user engages a control with `RequiresPointer="WhenEngaged"`, mouse mode is activated on the control until the user disengages it.</span></span> <span data-ttu-id="c1179-413">Der folgende Codeausschnitt zeigt ein einfaches `MapControl`-Steuerelement, das den Mausmodus aktiviert, wenn es verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="c1179-413">The following code snippet demonstrates a simple `MapControl` that activates mouse mode when engaged:</span></span>

```xml
<Page>
    <Grid>
        <MapControl IsEngagementRequired="true"
                    RequiresPointer="WhenEngaged"/>
    </Grid>
</Page>
```

> [!NOTE]
> <span data-ttu-id="c1179-414">Wenn ein Steuerelement bei Verwendung den Mausmodus aktiviert, muss es auch über `IsEngagementRequired="true"` eine Interaktion erfordern. Andernfalls wird der Mausmodus nie aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c1179-414">If a control activates mouse mode when engaged, it must also require engagement with `IsEngagementRequired="true"`; otherwise, mouse mode will never be activated.</span></span>

<span data-ttu-id="c1179-415">Wenn sich ein Steuerelement im Mausmodus befindet, befinden sich dessen verschachtelte Steuerelemente ebenfalls im Mausmodus.</span><span class="sxs-lookup"><span data-stu-id="c1179-415">When a control is in mouse mode, its nested controls will be in mouse mode as well.</span></span> <span data-ttu-id="c1179-416">Der angeforderte Modus der untergeordneten Elemente wird ignoriert; es ist nicht möglich, dass sich ein übergeordnetes Element im Mausmodus befindet, jedoch nicht dessen untergeordnete Elemente.</span><span class="sxs-lookup"><span data-stu-id="c1179-416">The requested mode of its children will be ignored&mdash;it's impossible for a parent to be in mouse mode but a child not to be.</span></span>

<span data-ttu-id="c1179-417">Darüber hinaus wird der angeforderte Modus eines Steuerelements nur untersucht, wenn es den Fokus erhält. Daher kann der Modus nicht dynamisch geändert werden, während es den Fokus besitzt.</span><span class="sxs-lookup"><span data-stu-id="c1179-417">Additionally, the requested mode of a control is only inspected when it gets focus, so the mode won't change dynamically while it has focus.</span></span>

### <a name="activating-mouse-mode-on-a-page"></a><span data-ttu-id="c1179-418">Aktivieren des Mausmodus auf einer Seite</span><span class="sxs-lookup"><span data-stu-id="c1179-418">Activating mouse mode on a page</span></span>

<span data-ttu-id="c1179-419">Wenn eine Seite die Eigenschaft `RequiresPointer="WhenFocused"` besitzt, wird der Mausmodus für die gesamte Seite aktiviert, wenn sie den Fokus erhält.</span><span class="sxs-lookup"><span data-stu-id="c1179-419">When a page has the property `RequiresPointer="WhenFocused"`, mouse mode will be activated for the whole page when it gets focus.</span></span> <span data-ttu-id="c1179-420">Der folgende Codeausschnitt zeigt, wie Sie einer Seite diese Eigenschaft zuweisen:</span><span class="sxs-lookup"><span data-stu-id="c1179-420">The following code snippet demonstrates giving a page this property:</span></span>

```xml
<Page RequiresPointer="WhenFocused">
    ...
</Page>
```

> [!NOTE]
> <span data-ttu-id="c1179-421">Der Wert `WhenFocused` wird nur für [Page](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx)-Objekte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1179-421">The `WhenFocused` value is only supported on [Page](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.page.aspx) objects.</span></span> <span data-ttu-id="c1179-422">Wenn Sie versuchen, diesen Wert für ein Steuerelement festzulegen, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c1179-422">If you try to set this value on a control, an exception will be thrown.</span></span>

### <a name="disabling-mouse-mode-for-full-screen-content"></a><span data-ttu-id="c1179-423">Deaktivieren des Mausmodus für Vollbildinhalte</span><span class="sxs-lookup"><span data-stu-id="c1179-423">Disabling mouse mode for full screen content</span></span>

<span data-ttu-id="c1179-424">Beim Anzeigen von Videos oder anderen Arten von Vollbildinhalten empfiehlt es sich in der Regel, den Cursor auszublenden, um den Benutzer nicht abzulenken.</span><span class="sxs-lookup"><span data-stu-id="c1179-424">Usually when displaying video or other types of content in full screen, you will want to hide the cursor because it can distract the user.</span></span> <span data-ttu-id="c1179-425">Dieses Szenario liegt vor, wenn der Rest der App den Mausmodus verwendet, dieser aber beim Anzeigen von Vollbildinhalten deaktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="c1179-425">This scenario occurs when the rest of the app uses mouse mode, but you want to turn it off when showing full screen content.</span></span> <span data-ttu-id="c1179-426">Platzieren Sie hierzu den Vollbildinhalt in einem eigenen `Page`-Objekt, und führen Sie die folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="c1179-426">To accomplish this, put the full screen content on its own `Page`, and follow the steps below.</span></span>

1. <span data-ttu-id="c1179-427">Legen Sie im `App`-Objekt Folgendes fest: `RequiresPointerMode="WhenRequested"`.</span><span class="sxs-lookup"><span data-stu-id="c1179-427">In the `App` object, set `RequiresPointerMode="WhenRequested"`.</span></span>
2. <span data-ttu-id="c1179-428">Legen Sie in jedem `Page`-Objekt (*mit Ausnahme des Vollbild-`Page`-Objekts*) Folgendes fest: `RequiresPointer="WhenFocused"`.</span><span class="sxs-lookup"><span data-stu-id="c1179-428">In every `Page` object *except* for the full screen `Page`, set `RequiresPointer="WhenFocused"`.</span></span>
3. <span data-ttu-id="c1179-429">Legen Sie für das Vollbild-`Page`-Objekt Folgendes fest: `RequiresPointer="Never"`.</span><span class="sxs-lookup"><span data-stu-id="c1179-429">For the full screen `Page`, set `RequiresPointer="Never"`.</span></span>

<span data-ttu-id="c1179-430">Dadurch wird der Cursor nicht angezeigt, wenn Inhalte im Vollbildmodus angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-430">This way, the cursor will never appear when showing full screen content.</span></span>

## <a name="focus-visual"></a><span data-ttu-id="c1179-431">Fokusanzeige</span><span class="sxs-lookup"><span data-stu-id="c1179-431">Focus visual</span></span>

<span data-ttu-id="c1179-432">Die Fokusanzeige ist der Rahmen um das Benutzeroberflächenelement, das zurzeit den Fokus besitzt.</span><span class="sxs-lookup"><span data-stu-id="c1179-432">The focus visual is the border around the UI element that currently has focus.</span></span> <span data-ttu-id="c1179-433">Dies hilft Benutzern, sich zu orientieren, damit sie in Ihrer Benutzeroberfläche einfach navigieren können, ohne die Orientierung zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-433">This helps orient the user so that they can easily navigate your UI without getting lost.</span></span>

<span data-ttu-id="c1179-434">Dank der Hinzufügung einer Anzeigenaktualisierung und zahlreicher Anpassungsoptionen zur Fokusanzeige können Entwickler darauf vertrauen, dass eine einzelne Fokusanzeige gut auf PCs und Xbox One und allen anderen Windows10-Geräten funktioniert, die Tastaturen und/oder Gamepads/Fernbedienungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c1179-434">With a visual update and numerous customization options added to focus visual, developers can trust that a single focus visual will work well on PCs and Xbox One, as well as on any other Windows 10 devices that support keyboard and/or gamepad/remote.</span></span>

<span data-ttu-id="c1179-435">Während die gleiche Fokusanzeige auf verschiedenen Plattformen verwendet werden kann, unterscheidet sich der Kontext, in dem der Benutzer diese antrifft, für die 10-Fuß-Erfahrung etwas.</span><span class="sxs-lookup"><span data-stu-id="c1179-435">While the same focus visual can be used across different platforms, the context in which the user encounters it is slightly different for the 10-foot experience.</span></span> <span data-ttu-id="c1179-436">Sie sollten davon ausgehen, dass der Benutzer nicht dem gesamten Fernsehbildschirm seine volle Aufmerksamkeit schenkt und es daher wichtig ist, dass das aktuell fokussierte Element für den Benutzer jederzeit deutlich erkennbar ist, um eine frustrierende Suche nach der Anzeige zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-436">You should assume that the user is not paying full attention to the entire TV screen, and therefore it is important that the currently focused element is clearly visible to the user at all times to avoid the frustration of searching for the visual.</span></span>

<span data-ttu-id="c1179-437">Darüber hinaus ist es wichtig, zu beachten, dass die Fokusanzeige standardmäßig angezeigt wird, wenn ein Gamepad oder eine Fernbedienung verwendet wird, jedoch *nicht*, wenn eine Tastatur verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-437">It is also important to keep in mind that the focus visual is displayed by default when using a gamepad or remote control, but *not* a keyboard.</span></span> <span data-ttu-id="c1179-438">Auch wenn Sie keine Fokusanzeige implementieren, wird sie daher angezeigt, wenn Sie Ihre App auf Xbox One ausführen.</span><span class="sxs-lookup"><span data-stu-id="c1179-438">Thus, even if you don't implement it, it will appear when you run your app on Xbox One.</span></span>

### <a name="initial-focus-visual-placement"></a><span data-ttu-id="c1179-439">Anfängliche Platzierung der Fokusanzeige</span><span class="sxs-lookup"><span data-stu-id="c1179-439">Initial focus visual placement</span></span>

<span data-ttu-id="c1179-440">Platzieren Sie beim Starten einer App oder Navigieren zu einer Seite den Fokus auf einem Benutzeroberflächenelement, das sinnvollerweise als erstes Element betrachtet werden kann, für das Benutzer eine Aktion ausführen würden.</span><span class="sxs-lookup"><span data-stu-id="c1179-440">When launching an app or navigating to a page, place the focus on a UI element that makes sense as the first element on which the user would take action.</span></span> <span data-ttu-id="c1179-441">Beispielsweise könnte eine Foto-App den Fokus auf das erste Element im Katalog platzieren, und eine Musik-App, in der zur detaillierten Ansicht eines Musiktitels navigiert wurde, könnte den Fokus auf die Abspieltaste setzen, um eine einfache Wiedergabe der Musik zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c1179-441">For example, a photo app may place focus on the first item in the gallery, and a music app navigated to a detailed view of a song might place focus on the play button for ease of playing music.</span></span>

<span data-ttu-id="c1179-442">Platzieren Sie den anfänglichen Fokus in Ihrer App möglichst in den Bereich oben links (oder oben rechts bei einem Lesefluss von rechts nach links).</span><span class="sxs-lookup"><span data-stu-id="c1179-442">Try to put initial focus in the top left region of your app (or top right for a right-to-left flow).</span></span> <span data-ttu-id="c1179-443">Die meisten Benutzer neigen dazu, sich zunächst auf diesen Bereich zu konzentrieren, da der Inhaltsfluss einer App im Allgemeinen dort beginnt.</span><span class="sxs-lookup"><span data-stu-id="c1179-443">Most users tend to focus on that corner first because that's where app content flow generally begins.</span></span>

### <a name="making-focus-clearly-visible"></a><span data-ttu-id="c1179-444">Klare Erkennbarkeit des Fokus</span><span class="sxs-lookup"><span data-stu-id="c1179-444">Making focus clearly visible</span></span>

<span data-ttu-id="c1179-445">Eine Fokusanzeige sollte stets auf dem Bildschirm sichtbar sein, damit Benutzer Vorgänge an der Stelle fortsetzen können, an der sie aufgehört haben, ohne nach dem Fokus suchen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="c1179-445">One focus visual should always be visible on the screen so that the user can pick up where they left off without searching for the focus.</span></span> <span data-ttu-id="c1179-446">Entsprechend sollte sich stets ein fokussierbares Element auf dem Bildschirm befinden. Verwenden Sie beispielsweise keine Popups, die nur Text und keine fokussierbaren Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="c1179-446">Similarly, there should be a focusable item onscreen at all times&mdash;for example, don't use pop-ups with only text and no focusable elements.</span></span>

<span data-ttu-id="c1179-447">Eine Ausnahme von dieser Regel wären die Vollbild-Funktionen wie das Abspielen von Videos oder das Anzeigen von Bildern. In diesen Fällen sollte die Fokusanzeige nicht sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="c1179-447">An exception to this rule would be for full-screen experiences, such as watching videos or viewing images, in which cases it would not be appropriate to show the focus visual.</span></span>

### <a name="customizing-the-focus-visual"></a><span data-ttu-id="c1179-448">Anpassen der Fokusanzeige</span><span class="sxs-lookup"><span data-stu-id="c1179-448">Customizing the focus visual</span></span>

<span data-ttu-id="c1179-449">Wenn Sie die Fokusanzeige anpassen möchten, können Sie hierzu die Eigenschaften für die Fokusanzeige in den einzelnen Steuerelementen bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1179-449">If you'd like to customize the focus visual, you can do so by modifying the properties related to the focus visual for each control.</span></span> <span data-ttu-id="c1179-450">Es gibt mehrere entsprechende Eigenschaften, über die Sie die App personalisieren können.</span><span class="sxs-lookup"><span data-stu-id="c1179-450">There are several such properties that you can take advantage of to personalize your app.</span></span>

<span data-ttu-id="c1179-451">Sie können sogar die systemeigenen Fokusanzeigen deaktivieren und eigene Fokusanzeigen darstellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-451">You can even opt out of the system-provided focus visuals by drawing your own using visual states.</span></span> <span data-ttu-id="c1179-452">Weitere Informationen finden Sie unter [VisualState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.visualstate.Aspx).</span><span class="sxs-lookup"><span data-stu-id="c1179-452">To learn more, see [VisualState](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.visualstate.Aspx).</span></span>

### <a name="light-dismiss-overlay"></a><span data-ttu-id="c1179-453">Overlay für einfaches Ausblenden</span><span class="sxs-lookup"><span data-stu-id="c1179-453">Light dismiss overlay</span></span>

<span data-ttu-id="c1179-454">Um die Aufmerksamkeit der Benutzer auf die Benutzeroberflächenelemente zu lenken, die sie gerade mit dem Gamecontroller oder der Fernbedienung bearbeiten, fügt UWP automatisch eine „Ausblendschicht“ ein, die Bereiche außerhalb der Popup-Benutzeroberfläche abdeckt, wenn die App auf Xbox One ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-454">To call the user's attention to the UI elements that the user is currently manipulating with the game controller or remote control, the UWP automatically adds a "smoke" layer that covers areas outside of the popup UI when the app is running on Xbox One.</span></span> <span data-ttu-id="c1179-455">Dies erfordert keinen zusätzlichen Aufwand. Sie sollten diese Funktionalität jedoch während der Entwicklung Ihrer Benutzeroberfläche berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="c1179-455">This requires no extra work, but is something to keep in mind when designing your UI.</span></span> <span data-ttu-id="c1179-456">Über die `LightDismissOverlayMode`-Eigenschaft können Sie die Ausblendschicht für jedes `FlyoutBase`-Element aktivieren oder deaktivieren. Der Standardwert `Auto` bedeutet, dass sie auf Xbox aktiviert und auf allen anderen Plattformen deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-456">You can set the `LightDismissOverlayMode` property on any `FlyoutBase` to enable or disable the smoke layer; it defaults to `Auto`, meaning that it is enabled on Xbox and disabled elsewhere.</span></span> <span data-ttu-id="c1179-457">Weitere Informationen finden Sie unter [Modales Ausblenden im Vergleich zu einfachem Ausblenden](../controls-and-patterns/menus.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-457">For more information, see [Modal vs light dismiss](../controls-and-patterns/menus.md).</span></span>

## <a name="focus-engagement"></a><span data-ttu-id="c1179-458">Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="c1179-458">Focus engagement</span></span>

<span data-ttu-id="c1179-459">Die Fokusaktivierung soll die Verwendung eines Gamepads oder einer Fernbedienung für Interaktionen mit einer App vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c1179-459">Focus engagement is intended to make it easier to use a gamepad or remote to interact with an app.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-460">Das Einrichten der Fokusaktivierung wirkt sich nicht auf Tastaturen oder andere Eingabegeräte aus.</span><span class="sxs-lookup"><span data-stu-id="c1179-460">Setting focus engagement does not impact keyboard or other input devices.</span></span>

<span data-ttu-id="c1179-461">Wenn die Eigenschaft `IsFocusEngagementEnabled` für ein [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.aspx) -Objekt auf `True` festgelegt wird, zeigt dies an, dass das Steuerelement Fokusaktivierung erfordert.</span><span class="sxs-lookup"><span data-stu-id="c1179-461">When the property `IsFocusEngagementEnabled` on a [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.aspx) object is set to `True`, it marks the control as requiring focus engagement.</span></span> <span data-ttu-id="c1179-462">Das bedeutet, dass der Benutzer die **A/Select**-Taste (Auswahl-Taste) drücken muss, um das Steuerelement zu „aktivieren“ und mit diesem zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-462">This means that the user must press the **A/Select** button to "engage" the control and interact with it.</span></span> <span data-ttu-id="c1179-463">Anschließend können sie die **B/Zurück**-Taste drücken, um das Steuerelement zu deaktivieren und von diesem weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-463">When they are finished, they can press the **B/Back** button to disengage the control and navigate out of it.</span></span>

> [!NOTE]
> `IsFocusEngagementEnabled` <span data-ttu-id="c1179-464">ist eine neue API, die noch nicht dokumentiert ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-464">is a new API and not yet documented.</span></span>

### <a name="focus-trapping"></a><span data-ttu-id="c1179-465">Fokustrapping</span><span class="sxs-lookup"><span data-stu-id="c1179-465">Focus trapping</span></span>

<span data-ttu-id="c1179-466">Fokustrapping bedeutet, dass ein Benutzer versucht, in der Benutzeroberfläche einer App zu navigieren, jedoch innerhalb eines Steuerelements „gefangen“ ist, wodurch es schwer oder sogar unmöglich wird, von diesem Steuerelement weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-466">Focus trapping is what happens when a user attempts to navigate an app's UI but becomes "trapped" within a control, making it difficult or even impossible to move outside of that control.</span></span>

<span data-ttu-id="c1179-467">Das folgende Beispiel zeigt eine Benutzeroberfläche, die ein Fokustrapping verursacht.</span><span class="sxs-lookup"><span data-stu-id="c1179-467">The following example shows UI that creates focus trapping.</span></span>

![Schaltflächen links und rechts neben einem horizontalen Schieberegler](images/designing-for-tv/focus-engagement-focus-trapping.png)

<span data-ttu-id="c1179-469">Wenn der Benutzer von der linken zur rechten Schaltfläche navigieren möchte, wäre es logisch, anzunehmen, dass er hierzu auf dem Steuerkreuz (D-Pad) oder linken Stick lediglich zweimal rechts drücken muss.</span><span class="sxs-lookup"><span data-stu-id="c1179-469">If the user wants to navigate from the left button to the right button, it would be logical to assume that all they'd have to do is press right on the D-pad/left stick twice.</span></span>
<span data-ttu-id="c1179-470">Wenn das [Slider](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx)-Steuerelement jedoch keine Aktivierung erfordert, würde das folgende Verhalten eintreten; Wenn der Benutzer das erste Mal rechts drückt, würde der Fokus zum `Slider` verschoben. Wenn er das zweite Mal rechts drückt, würde der Ziehpunkt des `Slider` nach rechts verschoben.</span><span class="sxs-lookup"><span data-stu-id="c1179-470">However, if the [Slider](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx) doesn't require engagement, the following behavior would occur: when the user presses right the first time, focus would shift to the `Slider`, and when they press right again, the `Slider`'s handle would move to the right.</span></span> <span data-ttu-id="c1179-471">Der Benutzer würde den Ziehpunkt immer weiter nach rechts verschieben und könnte nicht zur Schaltfläche gelangen.</span><span class="sxs-lookup"><span data-stu-id="c1179-471">The user would keep moving the handle to the right and wouldn't be able to get to the button.</span></span>

<span data-ttu-id="c1179-472">Es gibt verschiedene Methoden, um dieses Problem zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="c1179-472">There are several approaches to getting around this issue.</span></span> <span data-ttu-id="c1179-473">Eine Möglichkeit besteht darin, ein anderes Layout ähnlich wie im Beispiel für eine Immobilien-App in [XY-Fokusnavigation und -interaktion](#xy-focus-navigation-and-interaction) zu entwerfen. Dort wurden die Schaltflächen **Zurück** und **Weiter** oberhalb der `ListView` platziert.</span><span class="sxs-lookup"><span data-stu-id="c1179-473">One is to design a different layout, similar to the real estate app example in [XY focus navigation and interaction](#xy-focus-navigation-and-interaction) where we relocated the **Previous** and **Next** buttons above the `ListView`.</span></span> <span data-ttu-id="c1179-474">Eine vertikale anstelle einer horizontalen Anordnung der Steuerelemente wie in der folgenden Abbildung würde das Problem lösen.</span><span class="sxs-lookup"><span data-stu-id="c1179-474">Stacking the controls vertically instead of horizontally as in the following image would solve the problem.</span></span>

![Schaltflächen ober- und unterhalb eines horizontalen Schiebereglers](images/designing-for-tv/focus-engagement-focus-trapping-2.png)

<span data-ttu-id="c1179-476">Nun kann der Benutzer zu jedem der Steuerelemente navigieren, indem er auf dem Steuerkreuz (D-Pad/linken Stick) nach oben und nach unten drückt. Wenn der `Slider` den Fokus hat, kann er links und rechts drücken, um den Ziehpunkt des `Slider` zu verschieben, wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="c1179-476">Now the user can navigate to each of the controls by pressing up and down on the D-pad/left stick, and when the `Slider` has focus, they can press left and right to move the `Slider` handle, as expected.</span></span>

<span data-ttu-id="c1179-477">Ein anderer Ansatz zur Lösung dieses Problems besteht darin, für den `Slider` Aktivierung zu erfordern.</span><span class="sxs-lookup"><span data-stu-id="c1179-477">Another approach to solving this problem is to require engagement on the `Slider`.</span></span> <span data-ttu-id="c1179-478">Wenn Sie `IsFocusEngagementEnabled="True"` festlegen, führt dies zum folgenden Verhalten.</span><span class="sxs-lookup"><span data-stu-id="c1179-478">If you set `IsFocusEngagementEnabled="True"`, this will result in the following behavior.</span></span>

![Anfordern einer Fokusaktivierung für den Schieberegler, damit Benutzer zur Schaltfläche auf der rechten Seite navigieren können](images/designing-for-tv/focus-engagement-slider.png)

<span data-ttu-id="c1179-480">Wenn der `Slider` Fokusaktivierung erfordert, kann der Benutzer einfach zur Schaltfläche auf der rechten Seite gelangen, indem er auf dem Steuerkreuz (D-Pad)/dem linken Stick zweimal rechts drückt.</span><span class="sxs-lookup"><span data-stu-id="c1179-480">When the `Slider` requires focus engagement, the user can get to the button on the right simply by pressing right on the D-pad/left stick twice.</span></span> <span data-ttu-id="c1179-481">Diese Lösung ist hervorragend geeignet, da sie keine Benutzeroberflächenanpassung erfordert und das erwartete Verhalten erzeugt.</span><span class="sxs-lookup"><span data-stu-id="c1179-481">This solution is great because it requires no UI adjustment and produces the expected behavior.</span></span>

### <a name="items-controls"></a><span data-ttu-id="c1179-482">Elementsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1179-482">Items controls</span></span>

<span data-ttu-id="c1179-483">Abgesehen vom [Slider](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx)-Steuerelement gibt es weitere Steuerelemente, für die Sie möglicherweise eine Aktivierung anfordern sollten, wie beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="c1179-483">Aside from the [Slider](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.slider.aspx) control, there are other controls which you may want to require engagement, such as:</span></span>

- [<span data-ttu-id="c1179-484">ListBox</span><span class="sxs-lookup"><span data-stu-id="c1179-484">ListBox</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listbox.aspx)
- [<span data-ttu-id="c1179-485">ListView</span><span class="sxs-lookup"><span data-stu-id="c1179-485">ListView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx)
- [<span data-ttu-id="c1179-486">GridView</span><span class="sxs-lookup"><span data-stu-id="c1179-486">GridView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)
- [<span data-ttu-id="c1179-487">FlipView</span><span class="sxs-lookup"><span data-stu-id="c1179-487">FlipView</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.flipview)

<span data-ttu-id="c1179-488">Im Gegensatz zum `Slider`-Steuerelement, fangen diese Steuerelemente den Fokus nicht innerhalb ihrer selbst. Sie können jedoch Probleme hinsichtlich der Verwendbarkeit verursachen, wenn sie große Mengen an Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="c1179-488">Unlike the `Slider` control, these controls don't trap focus within themselves; however, they can cause usability issues when they contain large amounts of data.</span></span> <span data-ttu-id="c1179-489">Im Folgenden finden Sie ein Beispiel für eine `ListView`, die eine große Menge an Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="c1179-489">The following is an example of a `ListView` that contains a large amount of data.</span></span>

![ListView mit einer großen Menge an Daten und Schaltflächen ober- und unterhalb](images/designing-for-tv/focus-engagement-list-and-grid-controls.png)

<span data-ttu-id="c1179-491">Versuchen wir, ähnlich wie im Beispiel für das `Slider`-Steuerelement mit einem Gamepad/einer Fernbedienung von der Schaltfläche oben zur Schaltfläche unten zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-491">Similar to the `Slider` example, let's try to navigate from the button at the top to the button at the bottom with a gamepad/remote.</span></span>
<span data-ttu-id="c1179-492">Zunächst hat die Schaltfläche oben den Fokus. Wenn wir auf dem Steuerkreuz (D-Pad)/dem Stick nach unten drücken, wird der Fokus auf das erste Element in der `ListView` („Element 1“) platziert.</span><span class="sxs-lookup"><span data-stu-id="c1179-492">Starting with focus on the top button, pressing down on the D-pad/stick will place the focus on the first item in the `ListView` ("Item 1").</span></span>
<span data-ttu-id="c1179-493">Wenn der Benutzer erneut nach unten drückt, erhält das nächste Element in der Liste den Fokus, nicht die Schaltfläche unten.</span><span class="sxs-lookup"><span data-stu-id="c1179-493">When the user presses down again, the next item in the list gets focus, not the button on the bottom.</span></span>
<span data-ttu-id="c1179-494">Um zur Schaltfläche zu gelangen, muss der Benutzer zunächst durch jedes Element in der `ListView` navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-494">To get to the button, the user must navigate through every item in the `ListView` first.</span></span>
<span data-ttu-id="c1179-495">Wenn die `ListView` eine große Menge an Daten enthält, kann dies umständlich sein und stellt keine optimale Benutzererfahrung dar.</span><span class="sxs-lookup"><span data-stu-id="c1179-495">If the `ListView` contains a large amount of data, this could be inconvenient and not an optimal user experience.</span></span>

<span data-ttu-id="c1179-496">Um dieses Problem zu lösen, legen Sie die Eigenschaft `IsFocusEngagementEnabled="True"` für `ListView` fest, um Aktivierung zu erfordern.</span><span class="sxs-lookup"><span data-stu-id="c1179-496">To solve this problem, set the property `IsFocusEngagementEnabled="True"` on the `ListView` to require engagement on it.</span></span>
<span data-ttu-id="c1179-497">Dadurch können Benutzer die `ListView` schnell überspringen, indem sie einfach nach unten drücken.</span><span class="sxs-lookup"><span data-stu-id="c1179-497">This will allow the user to quickly skip over the `ListView` by simply pressing down.</span></span> <span data-ttu-id="c1179-498">Sie können jedoch keinen Bildlauf durch die Liste ausführen oder ein Element aus der Liste auswählen, wenn sie diese nicht durch Drücken der **A/Auswahl**-Taste aktivieren, wenn die Liste den Fokus hat. Anschließend können sie die **B/Zurück**-Taste drücken, um die Liste zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-498">However, they will not be able to scroll through the list or choose an item from it unless they engage it by pressing the **A/Select** button when it has focus, and then pressing the **B/Back** button to disengage.</span></span>

![ListView mit erforderlicher Aktivierung](images/designing-for-tv/focus-engagement-list-and-grid-controls-2.png)

#### <a name="scrollviewer"></a><span data-ttu-id="c1179-500">ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c1179-500">ScrollViewer</span></span>

<span data-ttu-id="c1179-501">[ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx) unterscheidet sich etwas von diesen Steuerelementen. Es weist spezifische Besonderheiten auf, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1179-501">Slightly different from these controls is the [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx), which has its own quirks to consider.</span></span> <span data-ttu-id="c1179-502">Wenn Sie ein `ScrollViewer`-Steuerelement mit fokussierbarem Inhalt besitzen, können Sie standardmäßig durch Navigieren zum `ScrollViewer`-Steuerelement durch dessen fokussierbare Elemente navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-502">If you have a `ScrollViewer` with focusable content, by default navigating to the `ScrollViewer` will allow you to move through its focusable elements.</span></span> <span data-ttu-id="c1179-503">Wie in einer `ListView`, müssen Sie einen Bildlauf über alle Elemente ausführen, um von `ScrollViewer` weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-503">Like in a `ListView`, you must scroll through each item to navigate outside of the `ScrollViewer`.</span></span>

<span data-ttu-id="c1179-504">Wenn `ScrollViewer` *keine* fokussierbaren Inhalte besitzt, also beispielsweise lediglich Text enthält, können Sie `IsFocusEngagementEnabled="True"` festlegen, sodass Benutzer `ScrollViewer` mithilfe der **A/Auswahl**-Taste aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="c1179-504">If the `ScrollViewer` has *no* focusable content&mdash;for example, if it only contains text&mdash;you can set `IsFocusEngagementEnabled="True"` so the user can engage the `ScrollViewer` by using the **A/Select** button.</span></span> <span data-ttu-id="c1179-505">Nach der Aktivierung können sie mit dem **Steuerkreuz (D-Pad)/linken Stick** einen Bildlauf durch den Text ausführen und anschließend die **B/Back**-Taste (Zurück-Taste) drücken, um das Steuerelement zu deaktivieren, wenn sie den Vorgang abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="c1179-505">After they have engaged, they can scroll through the text by using the **D-pad/left stick**, and then press the **B/Back** button to disengage when they're finished.</span></span>

<span data-ttu-id="c1179-506">Ein weiterer Ansatz besteht darin, `IsTabStop="True"` für `ScrollViewer` festzulegen, damit der Benutzer das Steuerelement nicht aktivieren muss. Er kann in diesem Fall einfach den Fokus auf das Steuerelement setzen und anschließend mit dem **Steuerkreuz (D-Pad)/linken Stick** einen Bildlauf ausführen, wenn es innerhalb von `ScrollViewer` keine fokussierbaren Elemente gibt..</span><span class="sxs-lookup"><span data-stu-id="c1179-506">Another approach would be to set `IsTabStop="True"` on the `ScrollViewer` so that the user doesn't have to engage the control&mdash;they can simply place focus on it and then scroll by using the **D-pad/left stick** when there are no focusable elements within the `ScrollViewer`.</span></span>

### <a name="focus-engagement-defaults"></a><span data-ttu-id="c1179-507">Standardeinstellungen in Bezug auf die Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="c1179-507">Focus engagement defaults</span></span>

<span data-ttu-id="c1179-508">Einige Steuerelemente führen häufig genug dazu, dass Benutzer in einem Steuerelement gefangen werden, um die Fokusaktivierung als Standardeinstellung zu rechtfertigen. Im Fall anderer Steuerelemente, für die die Fokusaktivierung standardmäßig deaktiviert ist, kann es nützlich sein, die Fokusaktivierung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-508">Some controls cause focus trapping commonly enough to warrant their default settings to require focus engagement, while others have focus engagement turned off by default but can benefit from turning it on.</span></span> <span data-ttu-id="c1179-509">Die folgende Tabelle listet diese Steuerelemente und deren Standardverhalten in Bezug auf die Fokusaktivierung auf.</span><span class="sxs-lookup"><span data-stu-id="c1179-509">The following table lists these controls and their default focus engagement behaviors.</span></span>

| <span data-ttu-id="c1179-510">Steuerelement</span><span class="sxs-lookup"><span data-stu-id="c1179-510">Control</span></span>               | <span data-ttu-id="c1179-511">Standardeinstellung in Bezug auf die Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="c1179-511">Focus engagement default</span></span>  |
|-----------------------|---------------------------|
| <span data-ttu-id="c1179-512">CalendarDatePicker</span><span class="sxs-lookup"><span data-stu-id="c1179-512">CalendarDatePicker</span></span>    | <span data-ttu-id="c1179-513">Ein</span><span class="sxs-lookup"><span data-stu-id="c1179-513">On</span></span>                        |
| <span data-ttu-id="c1179-514">FlipView</span><span class="sxs-lookup"><span data-stu-id="c1179-514">FlipView</span></span>              | <span data-ttu-id="c1179-515">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-515">Off</span></span>                       |
| <span data-ttu-id="c1179-516">GridView</span><span class="sxs-lookup"><span data-stu-id="c1179-516">GridView</span></span>              | <span data-ttu-id="c1179-517">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-517">Off</span></span>                       |
| <span data-ttu-id="c1179-518">ListBox</span><span class="sxs-lookup"><span data-stu-id="c1179-518">ListBox</span></span>               | <span data-ttu-id="c1179-519">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-519">Off</span></span>                       |
| <span data-ttu-id="c1179-520">ListView</span><span class="sxs-lookup"><span data-stu-id="c1179-520">ListView</span></span>              | <span data-ttu-id="c1179-521">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-521">Off</span></span>                       |
| <span data-ttu-id="c1179-522">ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c1179-522">ScrollViewer</span></span>          | <span data-ttu-id="c1179-523">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-523">Off</span></span>                       |
| <span data-ttu-id="c1179-524">SemanticZoom</span><span class="sxs-lookup"><span data-stu-id="c1179-524">SemanticZoom</span></span>          | <span data-ttu-id="c1179-525">Aus</span><span class="sxs-lookup"><span data-stu-id="c1179-525">Off</span></span>                       |
| <span data-ttu-id="c1179-526">Slider</span><span class="sxs-lookup"><span data-stu-id="c1179-526">Slider</span></span>                | <span data-ttu-id="c1179-527">Ein</span><span class="sxs-lookup"><span data-stu-id="c1179-527">On</span></span>                        |

<span data-ttu-id="c1179-528">Alle anderen UWP-Steuerelemente zeigen keine Änderungen in Bezug auf Verhalten oder Anzeige, wenn `IsFocusEngagementEnabled="True"` festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-528">All other UWP controls will result in no behavioral or visual changes when `IsFocusEngagementEnabled="True"`.</span></span>

## <a name="ui-element-sizing"></a><span data-ttu-id="c1179-529">Anpassen von Benutzeroberflächenelementen</span><span class="sxs-lookup"><span data-stu-id="c1179-529">UI element sizing</span></span>

<span data-ttu-id="c1179-530">Da Benutzer von Apps in 10-Fuß-Umgebungen Fernbedienungen oder Gamepads verwenden und sich mehrere Meter vom Bildschirm entfernt befinden, gibt es einige Überlegungen in Bezug auf die Benutzeroberfläche, die Sie für Ihren Entwurf berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1179-530">Because the user of an app in the 10-foot environment is using a remote control or gamepad and is sitting several feet away from the screen, there are some UI considerations that need to be factored into your design.</span></span>
<span data-ttu-id="c1179-531">Stellen Sie sicher, dass die Benutzeroberfläche über eine geeignete Inhaltsdichte verfügt und nicht zu überladen ist, damit Benutzer einfach navigieren und Elemente auswählen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-531">Make sure that the UI has an appropriate content density and is not too cluttered so that the user can easily navigate and select elements.</span></span> <span data-ttu-id="c1179-532">Denken Sie daran: Einfachheit ist der Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="c1179-532">Remember: simplicity is key.</span></span>

### <a name="scale-factor-and-adaptive-layout"></a><span data-ttu-id="c1179-533">Skalierungsfaktor und adaptives Layout</span><span class="sxs-lookup"><span data-stu-id="c1179-533">Scale factor and adaptive layout</span></span>

<span data-ttu-id="c1179-534">Der **Skalierungsfaktor** trägt dazu bei, dass Benutzeroberflächenelemente in der richtigen Größe für das Gerät angezeigt werden, auf dem die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-534">**Scale factor** helps with ensuring that UI elements are displayed with the right sizing for the device on which the app is running.</span></span>
<span data-ttu-id="c1179-535">Auf Desktops befindet sich diese Einstellung in **Einstellungen > System > Anzeige** als gleitender Wert.</span><span class="sxs-lookup"><span data-stu-id="c1179-535">On desktop, this setting can be found in **Settings > System > Display** as a sliding value.</span></span>
<span data-ttu-id="c1179-536">Diese Einstellung ist auch auf Mobiltelefonen vorhanden, wenn das Gerät diese unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c1179-536">This same setting exists on phone as well if the device supports it.</span></span>

![Ändern der Größe von Text, Apps und anderen Elementen](images/designing-for-tv/ui-scaling.png)

<span data-ttu-id="c1179-538">Auf Xbox One gibt es diese Systemeinstellung nicht. UWP-UI-Elemente, die für Fernsehgeräte angepasst werden, werden jedoch standardmäßig auf **200%** für XAML-Apps und **150%** für HTML-Apps skaliert.</span><span class="sxs-lookup"><span data-stu-id="c1179-538">On Xbox One, there is no such system setting; however, for UWP UI elements to be sized appropriately for TV, they are scaled at a default of **200%** for XAML apps and **150%** for HTML apps.</span></span>
<span data-ttu-id="c1179-539">Solange Benutzeroberflächenelemente für andere Geräte korrekt angepasst werden, werden sie auch für Fernsehgeräte angepasst.</span><span class="sxs-lookup"><span data-stu-id="c1179-539">As long as UI elements are appropriately sized for other devices, they will be appropriately sized for TV.</span></span>
<span data-ttu-id="c1179-540">Xbox One rendert Ihre App mit 1080p (1920 x 1080 Pixel).</span><span class="sxs-lookup"><span data-stu-id="c1179-540">Xbox One renders your app at 1080p (1920 x 1080 pixels).</span></span> <span data-ttu-id="c1179-541">Stellen Sie daher mittels [adaptiver Techniken](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) sicher, dass die UI bei 960x540px und einer Skalierung von 100% (oder bei 1280x720px und einer Skalierung von 100% für HTML-Apps) gut aussieht, wenn Sie eine App von anderen Geräten wie PCs übertragen.</span><span class="sxs-lookup"><span data-stu-id="c1179-541">Therefore, when bringing an app from other devices such as PC, ensure that the UI looks great at 960 x 540 px at 100% scale (or 1280 x 720 px at 100% scale for HTML apps) utilizing [adaptive techniques](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

<span data-ttu-id="c1179-542">Das Entwerfen für Xbox unterscheidet sich etwas vom Entwerfen für PCs, da Sie lediglich eine Auflösung von 1920x1080 berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="c1179-542">Designing for Xbox is a little different from designing for PC because you only need to worry about one resolution, 1920 x 1080.</span></span>
<span data-ttu-id="c1179-543">Es spielt keine Rolle, ob der Benutzer ein Fernsehgerät mit einer besseren Auflösung besitzt&mdash;UWP-Apps werden stets auf 1080p skaliert.</span><span class="sxs-lookup"><span data-stu-id="c1179-543">It doesn't matter if the user has a TV that has better resolution&mdash;UWP apps will always scale to 1080p.</span></span>

<span data-ttu-id="c1179-544">Bei der Ausführung auf Xbox One werden darüber hinaus korrekte Ressourcengrößen aus dem Satz mit 200% (oder 150% für HTML-Apps) für Ihre App aufgerufen, unabhängig von der Auflösung des Fernsehgeräts.</span><span class="sxs-lookup"><span data-stu-id="c1179-544">Correct asset sizes from the 200% (or 150% for HTML apps) set will also be pulled in for your app when running on Xbox One, regardless of TV resolution.</span></span>

### <a name="content-density"></a><span data-ttu-id="c1179-545">Inhaltsdichte</span><span class="sxs-lookup"><span data-stu-id="c1179-545">Content density</span></span>

<span data-ttu-id="c1179-546">Denken Sie beim Entwerfen Ihrer App daran, dass Benutzer die Benutzeroberfläche aus der Entfernung sieht und mittels einer Fernbedienung oder einem Gamecontroller mit dieser interagiert. Dies dauert länger als die Verwendung von Maus- oder Toucheingaben.</span><span class="sxs-lookup"><span data-stu-id="c1179-546">When designing your app, remember that the user will be viewing the UI from a distance and interacting with it by using a remote or game controller, which takes more time to navigate than using mouse or touch input.</span></span>

#### <a name="sizes-of-ui-controls"></a><span data-ttu-id="c1179-547">Größen von Benutzeroberflächensteuerelementen</span><span class="sxs-lookup"><span data-stu-id="c1179-547">Sizes of UI controls</span></span>

<span data-ttu-id="c1179-548">Interaktive Benutzeroberflächenelemente sollten eine Mindesthöhe von 32epx (effektive Pixel) besitzen.</span><span class="sxs-lookup"><span data-stu-id="c1179-548">Interactive UI elements should be sized at a minimum height of 32 epx (effective pixels).</span></span> <span data-ttu-id="c1179-549">Dies ist die Standardeinstellung für allgemeine UWP-Steuerelemente. Wenn diese bei einer Skalierung von 200% verwendet wird, ist sichergestellt, dass Benutzeroberflächenelemente aus der Entfernung erkennbar sind. Darüber hinaus trägt dies zur Reduzierung der Inhaltsdichte bei.</span><span class="sxs-lookup"><span data-stu-id="c1179-549">This is the default for common UWP controls, and when used at 200% scale, it ensures that UI elements are visible from a distance and helps reduce content density.</span></span>

![UWP-Schaltfläche bei einer Skalierung von 100% und 200%](images/designing-for-tv/button-100-200.png)

#### <a name="number-of-clicks"></a><span data-ttu-id="c1179-551">Anzahl der Klicks</span><span class="sxs-lookup"><span data-stu-id="c1179-551">Number of clicks</span></span>

<span data-ttu-id="c1179-552">Um Ihre Benutzeroberfläche zu vereinfachen, sollten Benutzer nicht mehr als **sechs Klicks** benötigen, wenn sie von einem Rand des Fernsehbildschirms zum anderen navigieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-552">When the user is navigating from one edge of the TV screen to the other, it should take no more than **six clicks** to simplify your UI.</span></span> <span data-ttu-id="c1179-553">Auch hier gilt der Grundsatz der **Einfachheit**.</span><span class="sxs-lookup"><span data-stu-id="c1179-553">Again, the principle of **simplicity** applies here.</span></span> <span data-ttu-id="c1179-554">Weitere Informationen finden Sie unter [Pfad der wenigsten Klicks](#path-of-least-clicks).</span><span class="sxs-lookup"><span data-stu-id="c1179-554">For more details, see [Path of least clicks](#path-of-least-clicks).</span></span>

![6Symbole insgesamt](images/designing-for-tv/six-clicks.png)

### <a name="text-sizes"></a><span data-ttu-id="c1179-556">Textgrößen</span><span class="sxs-lookup"><span data-stu-id="c1179-556">Text sizes</span></span>

<span data-ttu-id="c1179-557">Wenden Sie die folgenden Faustregeln an, damit Ihre Benutzeroberfläche aus der Entfernung erkennbar ist:</span><span class="sxs-lookup"><span data-stu-id="c1179-557">To make your UI visible from a distance, use the following rules of thumb:</span></span>

* <span data-ttu-id="c1179-558">Haupttext und Lesen von Inhalten: mindestens 15epx</span><span class="sxs-lookup"><span data-stu-id="c1179-558">Main text and reading content: 15 epx minimum</span></span>
* <span data-ttu-id="c1179-559">Nicht kritische Texte und ergänzende Inhalte: mindestens 12epx</span><span class="sxs-lookup"><span data-stu-id="c1179-559">Non-critical text and supplemental content: 12 epx minimum</span></span>

<span data-ttu-id="c1179-560">Wenn Sie in der Benutzeroberfläche einen größeren Text verwenden, sollten Sie eine Größe wählen, die die verfügbare Bildschirmfläche nicht zu sehr begrenzt, indem sie Platz beansprucht, der potenziell von anderen Inhalten ausgefüllt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-560">When using larger text in your UI, pick a size that does not limit screen real estate too much, taking up space that other content could potentially fill.</span></span>

### <a name="opting-out-of-scale-factor"></a><span data-ttu-id="c1179-561">Deaktivieren des Skalierungsfaktors</span><span class="sxs-lookup"><span data-stu-id="c1179-561">Opting out of scale factor</span></span>

<span data-ttu-id="c1179-562">Wir empfehlen Ihnen, für Ihre App die Vorteile der Skalierungsfaktorunterstützung zu nutzen. Dies trägt dazu bei, dass sie auf allen Geräten korrekt ausgeführt wird, indem sie für jeden Gerätetyp skaliert wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-562">We recommend that your app take advantage of scale factor support, which will help it run appropriately on all devices by scaling for each device type.</span></span>
<span data-ttu-id="c1179-563">Es ist jedoch möglich, dieses Verhalten zu deaktivieren und alle Benutzeroberflächenelemente für eine Skalierung von 100 % zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="c1179-563">However, it is possible to opt out of this behavior and design all of your UI at 100% scale.</span></span> <span data-ttu-id="c1179-564">Beachten Sie, dass Sie den Skalierungsfaktor nicht in einen anderen Wert als 100% ändern können.</span><span class="sxs-lookup"><span data-stu-id="c1179-564">Note that you cannot change the scale factor to anything other than 100%.</span></span>

<span data-ttu-id="c1179-565">Sie können den Skalierungsfaktor für HTML-Apps deaktivieren, indem Sie den folgenden Codeausschnitt verwenden:</span><span class="sxs-lookup"><span data-stu-id="c1179-565">For XAML apps, you can opt out of scale factor by using the following code snippet:</span></span>

```csharp
bool result =
    Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);
```

`result` <span data-ttu-id="c1179-566">informiert Sie, ob die Deaktivierung erfolgreich ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="c1179-566">will inform you whether you successfully opted out.</span></span>

<span data-ttu-id="c1179-567">Weitere Informationen, einschließlich HTML/JavaScript-Beispielcode, finden Sie unter [So deaktivieren Sie die Skalierung](../xbox-apps/disable-scaling.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-567">For more information, including sample code for HTML/JavaScript, see [How to turn off scaling](../xbox-apps/disable-scaling.md).</span></span>

<span data-ttu-id="c1179-568">Stellen Sie sicher, dass Sie entsprechenden Größen der Benutzeroberflächenelemente berechnen, indem Sie die in diesem Thema genannten *effektiven* Pixelwerte auf die *tatsächlichen* Pixelwerte verdoppeln (oder für HTML-Apps mit 1,5 multiplizieren).</span><span class="sxs-lookup"><span data-stu-id="c1179-568">Please be sure to calculate the appropriate sizes of UI elements by doubling the *effective* pixel values mentioned in this topic to *actual* pixel values (or multiplying by 1.5 for HTML apps).</span></span>

## <a name="tv-safe-area"></a><span data-ttu-id="c1179-569">Fernsehsicherer Bereich</span><span class="sxs-lookup"><span data-stu-id="c1179-569">TV-safe area</span></span>

<span data-ttu-id="c1179-570">Nicht alle Fernsehgeräte zeigen die Inhalte von Rand zu Rand an. Dies hat historische und technische Gründe.</span><span class="sxs-lookup"><span data-stu-id="c1179-570">Not all TVs display content all the way to the edges of the screen due to historical and technological reasons.</span></span> <span data-ttu-id="c1179-571">Standardmäßig vermeidet die UWP die Anzeige von Benutzeroberflächeninhalten in nicht fernsehsicheren Bereichen und zeichnet stattdessen lediglich den Seitenhintergrund.</span><span class="sxs-lookup"><span data-stu-id="c1179-571">By default, the UWP will avoid displaying any UI content in TV-unsafe areas and instead will only draw the page background.</span></span>

<span data-ttu-id="c1179-572">Der nicht fernsehsichere Bereich wird in der folgenden Abbildung durch den blauen Bereich dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c1179-572">The TV-unsafe area is represented by the blue area in the following image.</span></span>

![Nicht fernsehsicherer Bereich](images/designing-for-tv/tv-unsafe-area.png)

<span data-ttu-id="c1179-574">Sie können für den Hintergrund eine statische Farbe, eine Designfarbe oder ein Bild verwenden, wie in den folgenden Codeausschnitten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-574">You can set the background to a static or themed color, or to an image, as the following code snippets demonstrate.</span></span>

### <a name="theme-color"></a><span data-ttu-id="c1179-575">Designfarbe</span><span class="sxs-lookup"><span data-stu-id="c1179-575">Theme color</span></span>

```xml
<Page x:Class="Sample.MainPage"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"/>
```

### <a name="image"></a><span data-ttu-id="c1179-576">Bild</span><span class="sxs-lookup"><span data-stu-id="c1179-576">Image</span></span>

```xml
<Page x:Class="Sample.MainPage"
      Background="\Assets\Background.png"/>
```

<span data-ttu-id="c1179-577">So sieht Ihre App ohne zusätzlichen Aufwand aus.</span><span class="sxs-lookup"><span data-stu-id="c1179-577">This is what your app will look like without additional work.</span></span>

![Fernsehsicherer Bereich](images/designing-for-tv/tv-safe-area.png)

<span data-ttu-id="c1179-579">Dies ist nicht optimal, da dies der App einen „Schachteleffekt“ verleiht. Teile der Benutzeroberfläche werden scheinbar abgeschnitten, beispielsweise der Navigationsbereich und das Raster.</span><span class="sxs-lookup"><span data-stu-id="c1179-579">This is not optimal because it gives the app a "boxed-in" effect, with parts of the UI such as the nav pane and grid seemingly cut off.</span></span> <span data-ttu-id="c1179-580">Sie können jedoch Optimierungen durchführen, um Teile der Benutzeroberfläche bis an die Ränder des Bildschirms zu erweitern, um der App einen kinofilmähnlicheren Effekt zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="c1179-580">However, you can make optimizations to extend parts of the UI to the edges of the screen to give the app a more cinematic effect.</span></span>

### <a name="drawing-ui-to-the-edge"></a><span data-ttu-id="c1179-581">Zeichnen der Benutzeroberfläche bis zum Rand</span><span class="sxs-lookup"><span data-stu-id="c1179-581">Drawing UI to the edge</span></span>

<span data-ttu-id="c1179-582">Wir empfehlen Ihnen, bestimmte Benutzeroberflächenelemente zu verwenden, um die Benutzeroberfläche bis an die Ränder des Bildschirms zu erweitern und Benutzern eine immersivere Umgebung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c1179-582">We recommend that you use certain UI elements to extend to the edges of the screen to provide more immersion to the user.</span></span> <span data-ttu-id="c1179-583">Dazu gehören [ScrollViewers](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx), [Navigationsbereiche](../controls-and-patterns/navigationview.md) und [CommandBars](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx).</span><span class="sxs-lookup"><span data-stu-id="c1179-583">These include [ScrollViewers](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.scrollviewer.aspx), [nav panes](../controls-and-patterns/navigationview.md), and [CommandBars](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx).</span></span>

<span data-ttu-id="c1179-584">Es ist jedoch auch wichtig, dass interaktive Elemente und Texte stets die Bildschirmränder vermeiden, um sicherzustellen, dass sie auf bestimmten Fernsehgeräten nicht abgeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-584">On the other hand, it's also important that interactive elements and text always avoid the screen edges to ensure that they won't be cut off on some TVs.</span></span> <span data-ttu-id="c1179-585">Wir empfehlen Ihnen, nur nicht essentielle visuelle Elemente bis zu 5% von den Rändern des Bildschirms entfernt zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="c1179-585">We recommend that you draw only non-essential visuals within 5% of the screen edges.</span></span> <span data-ttu-id="c1179-586">Wie in [Anpassen von Benutzeroberflächenelementen](#ui-element-sizing) bereits erwähnt, nutzt eine UWP-App, die den Xbox One-Standardskalierungsfaktor von 200% verwendet, einen Bereich von 960 x 540epx. Sie sollten es daher vermeiden, in der Benutzeroberfläche Ihrer App essentielle Benutzerflächenelemente in den folgenden Bereichen zu platzieren:</span><span class="sxs-lookup"><span data-stu-id="c1179-586">As mentioned in [UI element sizing](#ui-element-sizing), a UWP app following the Xbox One console's default scale factor of 200% will utilize an area of 960 x 540 epx, so in your app's UI, you should avoid putting essential UI in the following areas:</span></span>

- <span data-ttu-id="c1179-587">27epx vom oberen und unteren Rand</span><span class="sxs-lookup"><span data-stu-id="c1179-587">27 epx from the top and bottom</span></span>
- <span data-ttu-id="c1179-588">48epx vom linken und rechten Rand</span><span class="sxs-lookup"><span data-stu-id="c1179-588">48 epx from the left and right sides</span></span>

<span data-ttu-id="c1179-589">In den folgenden Abschnitten wird beschrieben, wie Sie Ihr UI bis an die Ränder des Bildschirms erweitern.</span><span class="sxs-lookup"><span data-stu-id="c1179-589">The following sections describe how to make your UI extend to the screen edges.</span></span>

#### <a name="core-window-bounds"></a><span data-ttu-id="c1179-590">Kernfenstergrenzen</span><span class="sxs-lookup"><span data-stu-id="c1179-590">Core window bounds</span></span>

<span data-ttu-id="c1179-591">Im Fall von UWP-Apps, die ausschließlich für die 10-Fuß-Erfahrung entwickelt werden, stellt die Verwendung von Kernfenstergrenzen die einfachere Option dar.</span><span class="sxs-lookup"><span data-stu-id="c1179-591">For UWP apps targeting only the 10-foot experience, using core window bounds is a more straightforward option.</span></span>

<span data-ttu-id="c1179-592">Fügen Sie in der `OnLaunched`-Methode von `App.xaml.cs` den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="c1179-592">In the `OnLaunched` method of `App.xaml.cs`, add the following code:</span></span>

```csharp
Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode
    (Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);
```

<span data-ttu-id="c1179-593">Mit dieser Codezeile wird das App-Fenster bis zu den Rändern des Bildschirms erweitert. Daher müssen Sie alle interaktiven und essentiellen Benutzeroberflächenelemente in den bereits beschriebenen fernsehsicheren Bereich verschieben.</span><span class="sxs-lookup"><span data-stu-id="c1179-593">With this line of code, the app window will extend to the edges of the screen, so you will need to move all interactive and essential UI into the TV-safe area described earlier.</span></span> <span data-ttu-id="c1179-594">Kurzlebige Benutzeroberflächenelemente wie Kontextmenüs und geöffnete [Kombinationsfelder](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.combobox.aspx) bleiben automatisch im fernsehsicheren Bereich.</span><span class="sxs-lookup"><span data-stu-id="c1179-594">Transient UI, such as context menus and opened [ComboBoxes](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.combobox.aspx), will automatically remain inside the TV-safe area.</span></span>

![Kernfenstergrenzen](images/designing-for-tv/core-window-bounds.png)

#### <a name="pane-backgrounds"></a><span data-ttu-id="c1179-596">Bereichshintergründe</span><span class="sxs-lookup"><span data-stu-id="c1179-596">Pane backgrounds</span></span>

<span data-ttu-id="c1179-597">Navigationsbereiche werden in der Regel nahe am Rand des Bildschirms dargestellt. Daher sollte sich der Hintergrund in den nicht fernsehsicheren Bereich erstrecken, um hässliche Lücken zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-597">Navigation panes are typically drawn near the edge of the screen, so the background should extend into the TV-unsafe area so as not to introduce awkward gaps.</span></span> <span data-ttu-id="c1179-598">Hierzu können Sie einfach die Hintergrundfarbe des Navigationsbereichs in der Hintergrundfarbe der App ändern.</span><span class="sxs-lookup"><span data-stu-id="c1179-598">You can do this by simply changing the color of the nav pane's background to the color of the app's background.</span></span>

<span data-ttu-id="c1179-599">Mithilfe der oben beschriebenen Kernfenstergrenzen können Sie Ihr UI an den Rändern des Bildschirms darstellen. Sie sollten dann jedoch positive Ränder für die [SplitView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.splitview.aspx)-Inhalte nutzen, um diese innerhalb des fernsehsicheren Bereichs zu halten.</span><span class="sxs-lookup"><span data-stu-id="c1179-599">Using the core window bounds as previously described will allow you to draw your UI to the edges of the screen, but you should then use positive margins on the [SplitView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.splitview.aspx)'s content to keep it within the TV-safe area.</span></span>

![Navigationsbereich bis an die Ränder des Bildschirms erweitert](images/designing-for-tv/tv-safe-areas-2.png)

<span data-ttu-id="c1179-601">Hier wurde der Hintergrund des Navigationsbereichs bis an die Ränder des Bildschirms erweitert, während die Navigationselemente weiterhin im fernsehsicheren Bereich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-601">Here, the nav pane's background has been extended to the edges of the screen, while its navigation items are kept in the TV-safe area.</span></span>
<span data-ttu-id="c1179-602">Der Inhalt des `SplitView`-Elements (in diesem Fall ein Raster mit Elementen) wurde bis an den unteren Rand des Bildschirms erweitert. So sieht es aus, als würde es fortgesetzt und nicht abgeschnitten. Der obere Bereich des Rasters befindet sich nach wie vor im fernsehsicheren Bereich.</span><span class="sxs-lookup"><span data-stu-id="c1179-602">The content of the `SplitView` (in this case, a grid of items) has been extended to the bottom of the screen so that it looks like it continues and isn't cut off, while the top of the grid is still within the TV-safe area.</span></span> <span data-ttu-id="c1179-603">(Weitere Informationen hierzu finden Sie unter [Bildlaufenden von Listen und Rastern](#scrolling-ends-of-lists-and-grids)).</span><span class="sxs-lookup"><span data-stu-id="c1179-603">(Learn more about how to do this in [Scrolling ends of lists and grids](#scrolling-ends-of-lists-and-grids)).</span></span>

<span data-ttu-id="c1179-604">Mit dem folgenden Codeausschnitt wird dieser Effekt erzielt:</span><span class="sxs-lookup"><span data-stu-id="c1179-604">The following code snippet achieves this effect:</span></span>

```xml
<SplitView x:Name="RootSplitView"
           Margin="48,0,48,0">
    <SplitView.Pane>
        <ListView x:Name="NavMenuList"
                  ContainerContentChanging="NavMenuItemContainerContentChanging"
                  ItemContainerStyle="{StaticResource NavMenuItemContainerStyle}"
                  ItemTemplate="{StaticResource NavMenuItemTemplate}"
                  ItemInvoked="NavMenuList_ItemInvoked"
                  ItemsSource="{Binding NavMenuListItems}"/>
    </SplitView.Pane>
    <Frame x:Name="frame"
           Navigating="OnNavigatingToPage"
           Navigated="OnNavigatedToPage"/>
</SplitView>
```

<span data-ttu-id="c1179-605">[CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx) ist ein weiteres Beispiel für einen Bereich, der häufig in der Nähe eines oder mehrerer Ränder der App positioniert ist. Daher sollte dessen Hintergrund auf Fernsehbildschirmen bis an die Ränder des Bildschirms erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-605">[CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx) is another example of a pane that is commonly positioned near one or more edges of the app, and as such on TV its background should extend to the edges of the screen.</span></span> <span data-ttu-id="c1179-606">In der Regel gibt es auf der rechten Seite die Schaltfläche **Mehr** (dargestellt durch „...“), die weiter im fernsehsicheren Bereich angezeigt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="c1179-606">It also usually contains a **More** button, represented by "..." on the right side, which should remain in the TV-safe area.</span></span> <span data-ttu-id="c1179-607">Im Folgenden finden Sie einige unterschiedliche Strategien, um die gewünschten Interaktionen und visuellen Effekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="c1179-607">The following are a few different strategies to achieve the desired interactions and visual effects.</span></span>

<span data-ttu-id="c1179-608">**Option1**: Festlegen der `CommandBar`-Hintergrundfarbe auf transparent oder auf die Farbe des Seitenhintergrunds:</span><span class="sxs-lookup"><span data-stu-id="c1179-608">**Option 1**: Change the `CommandBar` background color to either transparent or the same color as the page background:</span></span>

```xml
<CommandBar x:Name="topbar"
            Background="{ThemeResource SystemControlBackgroundAltHighBrush}">
            ...
</CommandBar>
```

<span data-ttu-id="c1179-609">Hierdurch sieht die `CommandBar` aus, als ob sie auf dem gleichen Hintergrund wie der Rest der Seite angezeigt wird, sodass sich der Hintergrund nahtlos bis an den Rand des Bildschirms erstreckt.</span><span class="sxs-lookup"><span data-stu-id="c1179-609">Doing this will make the `CommandBar` look like it is on top of the same background as the rest of the page, so the background seamlessly flows to the edge of the screen.</span></span>

<span data-ttu-id="c1179-610">**Option2**: Hinzufügen eines Hintergrundrechtecks, dessen Füllung die gleiche Farbe wie der `CommandBar`-Hintergrund hat und das unter der `CommandBar` und über dem Rest der Seite liegt:</span><span class="sxs-lookup"><span data-stu-id="c1179-610">**Option 2**: Add a background rectangle whose fill is the same color as the `CommandBar` background, and have it lie below the `CommandBar` and across the rest of the page:</span></span>

```xml
<Rectangle VerticalAlignment="Top"
            HorizontalAlignment="Stretch"      
            Fill="{ThemeResource SystemControlBackgroundChromeMediumBrush}"/>
<CommandBar x:Name="topbar"
            VerticalAlignment="Top"
            HorizontalContentAlignment="Stretch">
            ...
</CommandBar>
```

> [!NOTE]
> <span data-ttu-id="c1179-611">Wenn Sie sich für diesen Ansatz entscheiden, sollten Sie berücksichtigen, dass die Schaltfläche **Mehr** wenn notwendig die Höhe der geöffneten `CommandBar` ändert, um die Beschriftungen der `AppBarButton`-Schaltflächen unterhalb der Symbole anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1179-611">If using this approach, be aware that the **More** button changes the height of the opened `CommandBar` if necessary, in order to show the labels of the `AppBarButton`s below their icons.</span></span> <span data-ttu-id="c1179-612">Wir empfehlen Ihnen, die Beschriftungen *rechts* neben ihren Symbolen anzuzeigen, um diese Größenanpassung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-612">We recommend that you move the labels to the *right* of their icons to avoid this resizing.</span></span> <span data-ttu-id="c1179-613">Weitere Informationen finden Sie unter [CommandBar-Beschriftungen](#commandbar-labels).</span><span class="sxs-lookup"><span data-stu-id="c1179-613">For more information, see [CommandBar labels](#commandbar-labels).</span></span>

<span data-ttu-id="c1179-614">Beide Vorgehensweisen gelten auch für die anderen in diesem Abschnitt aufgeführten Arten von Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="c1179-614">Both of these approaches also apply to the other types of controls listed in this section.</span></span>

#### <a name="scrolling-ends-of-lists-and-grids"></a><span data-ttu-id="c1179-615">Bildlaufenden von Listen und Rastern</span><span class="sxs-lookup"><span data-stu-id="c1179-615">Scrolling ends of lists and grids</span></span>

<span data-ttu-id="c1179-616">Meist enthalten Listen und Raster mehr Elemente, als gleichzeitig auf den Bildschirm passen.</span><span class="sxs-lookup"><span data-stu-id="c1179-616">It's common for lists and grids to contain more items than can fit onscreen at the same time.</span></span> <span data-ttu-id="c1179-617">Wenn dies der Fall ist, sollten Sie die Liste oder das Raster bis zum Rand des Bildschirms erweitern.</span><span class="sxs-lookup"><span data-stu-id="c1179-617">When this is the case, we recommend that you extend the list or grid to the edge of the screen.</span></span> <span data-ttu-id="c1179-618">Listen und Raster mit horizontalem Bildlauf sollten bis zum rechten Rand erweitert werden. Listen und Raster mit vertikalem Bildlauf sollten bis zum unteren Rand erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-618">Horizontally scrolling lists and grids should extend to the right edge, and vertically scrolling ones should extend to the bottom.</span></span>

![Abschneiden eines Rasters im fernsehsicheren Bereich](images/designing-for-tv/tv-safe-area-grid-cutoff.png)

<span data-ttu-id="c1179-620">Wenn eine Liste oder ein Raster wie hier beschrieben erweitert wird, ist es wichtig, dass die Fokusanzeige und das mit dieser verknüpfte Element weiter im fernsehsicheren Bereich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-620">While a list or grid is extended like this, it's important to keep the focus visual and its associated item inside the TV-safe area.</span></span>

![Bildlauffokus sollte weiter im fernsehsicheren Bereich angezeigt werden](images/designing-for-tv/scrolling-grid-focus.png)

<span data-ttu-id="c1179-622">Die UWP verfügt über Funktionen, die dafür sorgen, dass die Fokusanzeige weiter innerhalb der [VisibleBounds](https://msdn.microsoft.com/library/windows/apps/windows.ui.viewmanagement.applicationview.visiblebounds.aspx) angezeigt wird. Sie müssen jedoch Abstand hinzufügen, um sicherzustellen, dass für die Listen-/Rasterelemente ein Bildlauf in den Anzeigebereich des sicheren Bereichs durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-622">The UWP has functionality that will keep the focus visual inside the [VisibleBounds](https://msdn.microsoft.com/library/windows/apps/windows.ui.viewmanagement.applicationview.visiblebounds.aspx), but you need to add padding to ensure that the list/grid items can scroll into view of the safe area.</span></span> <span data-ttu-id="c1179-623">Genauer gesagt, müssen Sie für [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) oder [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx) deren [ItemsPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemspresenter.aspx) einen positiven Rand hinzufügen, wie im folgenden Codeausschnitt gezeigt:</span><span class="sxs-lookup"><span data-stu-id="c1179-623">Specifically, you add a positive margin to the [ListView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx) or [GridView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.gridview.aspx)'s [ItemsPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemspresenter.aspx), as in the following code snippet:</span></span>

```xml
<Style x:Key="TitleSafeListViewStyle"
       TargetType="ListView">
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="ListView">
                <Border BorderBrush="{TemplateBinding BorderBrush}"
                        Background="{TemplateBinding Background}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                    <ScrollViewer x:Name="ScrollViewer"
                                  TabNavigation="{TemplateBinding TabNavigation}"
                                  HorizontalScrollMode="{TemplateBinding ScrollViewer.HorizontalScrollMode}"
                                  HorizontalScrollBarVisibility="{TemplateBinding ScrollViewer.HorizontalScrollBarVisibility}"
                                  IsHorizontalScrollChainingEnabled="{TemplateBinding ScrollViewer.IsHorizontalScrollChainingEnabled}"
                                  VerticalScrollMode="{TemplateBinding ScrollViewer.VerticalScrollMode}"
                                  VerticalScrollBarVisibility="{TemplateBinding ScrollViewer.VerticalScrollBarVisibility}"
                                  IsVerticalScrollChainingEnabled="{TemplateBinding ScrollViewer.IsVerticalScrollChainingEnabled}"
                                  IsHorizontalRailEnabled="{TemplateBinding ScrollViewer.IsHorizontalRailEnabled}"
                                  IsVerticalRailEnabled="{TemplateBinding ScrollViewer.IsVerticalRailEnabled}"
                                  ZoomMode="{TemplateBinding ScrollViewer.ZoomMode}"
                                  IsDeferredScrollingEnabled="{TemplateBinding ScrollViewer.IsDeferredScrollingEnabled}"
                                  BringIntoViewOnFocusChange="{TemplateBinding ScrollViewer.BringIntoViewOnFocusChange}"
                                  AutomationProperties.AccessibilityView="Raw">
                        <ItemsPresenter Header="{TemplateBinding Header}"
                                        HeaderTemplate="{TemplateBinding HeaderTemplate}"
                                        HeaderTransitions="{TemplateBinding HeaderTransitions}"
                                        Footer="{TemplateBinding Footer}"
                                        FooterTemplate="{TemplateBinding FooterTemplate}"
                                        FooterTransitions="{TemplateBinding FooterTransitions}"
                                        Padding="{TemplateBinding Padding}"
                                        Margin="0,27,0,27"/>
                    </ScrollViewer>
                </Border>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
```

<span data-ttu-id="c1179-624">Sie platzieren den zuvor angezeigten Codeausschnitt entweder in die Seitenressourcen oder in den App-Ressourcen und greifen anschließend wie folgt auf diesen zu:</span><span class="sxs-lookup"><span data-stu-id="c1179-624">You would put the previous code snippet in either the page or app resources, and then access it in the following way:</span></span>

```xml
<Page>
    <Grid>
        <ListView Style="{StaticResource TitleSafeListViewStyle}"
                  ... />
```

> [!NOTE]
> <span data-ttu-id="c1179-625">Dieser Codeausschnitt gilt speziell für `ListView`-Elemente. Legen Sie bei einem `GridView`-Stil das [TargetType](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.targettype.aspx)-Attribut für [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) und [Style](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) auf `GridView` fest.</span><span class="sxs-lookup"><span data-stu-id="c1179-625">This code snippet is specifically for `ListView`s; for a `GridView` style, set the [TargetType](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.targettype.aspx) attribute for both the [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) and the [Style](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) to `GridView`.</span></span>

## <a name="colors"></a><span data-ttu-id="c1179-626">Farben</span><span class="sxs-lookup"><span data-stu-id="c1179-626">Colors</span></span>

<span data-ttu-id="c1179-627">Standardmäßig verändert die Universelle Windows-Plattform keine Farben in Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="c1179-627">By default, the Universal Windows Platform doesn't do anything to alter your app's colors.</span></span> <span data-ttu-id="c1179-628">Es gibt jedoch Verbesserungen, die für den Satz der von Ihrer App verwendeten Farben durchführen können, um die visuelle Erfahrung auf Fernsehgeräten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c1179-628">That said, there are improvements that you can make to the set of colors your app uses to improve the visual experience on TV.</span></span>

### <a name="application-theme"></a><span data-ttu-id="c1179-629">Anwendungsdesign</span><span class="sxs-lookup"><span data-stu-id="c1179-629">Application theme</span></span>

<span data-ttu-id="c1179-630">Sie können ein **Anwendungsdesign** (dunkel oder hell) wählen, je nach Ihrer App, oder Designs deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="c1179-630">You can choose an **Application theme** (dark or light) according to what is right for your app, or you can opt out of theming.</span></span> <span data-ttu-id="c1179-631">Weitere allgemeine Empfehlungen für Designs finden Sie in [Farbdesigns](../style/color.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-631">Read more about general recommendations for themes in [Color themes](../style/color.md).</span></span>

<span data-ttu-id="c1179-632">Die UWP ermöglicht Apps darüber hinaus, das Design dynamisch festzulegen, basierend auf den Systemeinstellungen, die von den Geräten bereitgestellt werden, auf denen sie ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-632">The UWP also allows apps to dynamically set the theme based on the system settings provided by the devices on which they run.</span></span>
<span data-ttu-id="c1179-633">Während die UWP stets die vom Benutzer angegebenen Designeinstellungen beachtet, stellt jedes Gerät auch ein entsprechendes Standarddesign bereit.</span><span class="sxs-lookup"><span data-stu-id="c1179-633">While the UWP always respects the theme settings specified by the user, each device also provides an appropriate default theme.</span></span>
<span data-ttu-id="c1179-634">Aufgrund des Zwecks der Xbox One, die eher eine *Medien*- als eine *Produktivitäts*umgebung bereitstellen soll, ist das Systemdesign standardmäßig dunkel.</span><span class="sxs-lookup"><span data-stu-id="c1179-634">Because of the nature of Xbox One, which is expected to have more *media* experiences than *productivity* experiences, it defaults to a dark system theme.</span></span>
<span data-ttu-id="c1179-635">Wenn das Design Ihrer App auf den Systemeinstellungen basiert, sollten Sie berücksichtigen, dass es auf Xbox One standardmäßig dunkel ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-635">If your app's theme is based on the system settings, expect it to default to dark on Xbox One.</span></span>

### <a name="accent-color"></a><span data-ttu-id="c1179-636">Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="c1179-636">Accent color</span></span>

<span data-ttu-id="c1179-637">Die UWP bietet eine bequeme Möglichkeit, die **Akzentfarbe** verfügbar zu machen, die der Benutzer aus den Systemeinstellungen ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="c1179-637">The UWP provides a convenient way to expose the **accent color** that the user has selected from their system settings.</span></span>

<span data-ttu-id="c1179-638">Auf Xbox One können Benutzer eine Benutzerfarbe auswählen – genauso, wie sie auf einem PC eine Akzentfarbe auswählen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-638">On Xbox One, the user is able to select a user color, just as they can select an accent color on a PC.</span></span>
<span data-ttu-id="c1179-639">Solange Ihre App diese Akzentfarben über Pinsel oder Farbressourcen aufruft, wird die vom jeweiligen Benutzer in den Systemeinstellungen ausgewählte Farbe verwendet.</span><span class="sxs-lookup"><span data-stu-id="c1179-639">As long as your app calls these accent colors through brushes or color resources, the color that the user selected in the system settings will be used.</span></span> <span data-ttu-id="c1179-640">Beachten Sie, dass Akzentfarben auf Xbox One benutzerbasiert und nicht systembasiert angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-640">Note that accent colors on Xbox One are per user, not per system.</span></span>

<span data-ttu-id="c1179-641">Beachten Sie auch, dass der Benutzerfarbensatz auf Xbox One nicht identisch mit dem Benutzerfarbensatz auf PCs, Smartphones und anderen Geräten ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-641">Please also note that the set of user colors on Xbox One is not the same as that on PCs, phones, and other devices.</span></span>
<span data-ttu-id="c1179-642">Dies liegt zum Teil daran, dass diese Farben vor allem im Hinblick auf eine optimale 10-Fuß-Erfahrung auf Xbox One ausgewählt wurden, basierend auf in diesem Artikel erklärten Methoden und Strategien.</span><span class="sxs-lookup"><span data-stu-id="c1179-642">This is partly due to the fact that these colors are hand-picked to make for the best 10-foot experience on Xbox One, following the same methodologies and strategies explained in this article.</span></span>

<span data-ttu-id="c1179-643">Solange Ihre App eine Pinselressource wie **SystemControlForegroundAccentBrush** oder eine Farbressource (**SystemAccentColor**) verwendet oder stattdessen Akzentfarben direkt über die [UIColorType.Accent*](https://msdn.microsoft.com/library/windows/apps/windows.ui.viewmanagement.uicolortype.aspx)-API aufruft, werden diese Farben durch Akzentfarben ersetzt, die für Fernsehgeräte geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="c1179-643">As long as your app uses a brush resource such as **SystemControlForegroundAccentBrush**, or a color resource (**SystemAccentColor**), or instead calls accent colors directly through the [UIColorType.Accent*](https://msdn.microsoft.com/library/windows/apps/windows.ui.viewmanagement.uicolortype.aspx) API, those colors are replaced with accent colors appropriate for TV.</span></span> <span data-ttu-id="c1179-644">Pinselfarben mit hohem Kontrast werden wie im Fall von PCs und Telefonen aus dem System abgerufen, jedoch mit Farben, die für Fernsehgeräte geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="c1179-644">High contrast brush colors are also pulled in from the system the same way as on a PC and phone, but with TV-appropriate colors.</span></span>

<span data-ttu-id="c1179-645">Weitere Informationen zu Akzentfarben im Allgemeinen finden Sie unter [Akzentfarbe](../style/color.md#accent-color).</span><span class="sxs-lookup"><span data-stu-id="c1179-645">To learn more about accent color in general, see [Accent color](../style/color.md#accent-color).</span></span>

### <a name="color-variance-among-tvs"></a><span data-ttu-id="c1179-646">Farbabweichungen zwischen Fernsehgeräten</span><span class="sxs-lookup"><span data-stu-id="c1179-646">Color variance among TVs</span></span>

<span data-ttu-id="c1179-647">Beachten Sie bei der Entwicklung von Apps für Fernsehgeräte, dass Farben sehr unterschiedlich dargestellt werden, abhängig von dem Fernsehgerät, auf dem sie gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-647">When designing for TV, note that colors display quite differently depending on the TV on which they are rendered.</span></span> <span data-ttu-id="c1179-648">Gehen Sie nicht davon aus, dass die Farben genau wie auf Ihrem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-648">Don't assume colors will look exactly as they do on your monitor.</span></span> <span data-ttu-id="c1179-649">Wenn Ihre App geringfügige Farbunterschiede nutzt, um Teile der Benutzeroberfläche zu unterscheiden, könnten sich die Farben mischen und die Benutzer könnten verwirrt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-649">If your app relies on subtle differences in color to differentiate parts of the UI, colors could blend together and users could get confused.</span></span> <span data-ttu-id="c1179-650">Verwenden Sie Farben, die unterschiedlich genug sind, dass Benutzer sie unabhängig vom verwendeten Fernsehgerät deutlich unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="c1179-650">Try to use colors that are different enough that users will be able to clearly differentiate them, regardless of the TV they are using.</span></span>

### <a name="tv-safe-colors"></a><span data-ttu-id="c1179-651">Fernsehsichere Farben</span><span class="sxs-lookup"><span data-stu-id="c1179-651">TV-safe colors</span></span>

<span data-ttu-id="c1179-652">Die RGB-Werte einer Farbe stellen die Intensität für Rot, Grün und Blau dar.</span><span class="sxs-lookup"><span data-stu-id="c1179-652">A color's RGB values represent intensities for red, green, and blue.</span></span> <span data-ttu-id="c1179-653">Fernsehgeräte behandeln extreme Intensitätsgrade nicht sehr gut. Daher sollten Sie diese Farben bei der Entwicklung für die 10-Fuß-Erfahrung vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-653">TVs don't handle extreme intensities very well; therefore, you should avoid using these colors when designing for the 10-foot experience.</span></span> <span data-ttu-id="c1179-654">Sie können einen merkwürdigen Bändereffekt hervorrufen oder auf bestimmten Fernsehgeräten verwaschen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-654">They can produce an odd banded effect, or appear washed out on certain TVs.</span></span> <span data-ttu-id="c1179-655">Darüber hinaus verursachen Farben mit hoher Intensität möglicherweise ein „Blooming“, d.h., Pixel in der Nähe beginnen, die gleichen Farben aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="c1179-655">Additionally, high-intensity colors may cause blooming (nearby pixels start drawing the same colors).</span></span>

<span data-ttu-id="c1179-656">Die Ansichten darüber, was als fernsehsichere Farben gelten kann, gehen zwar auseinander. Im Allgemeinen können Farben mit RGB-Werten zwischen 16 und 235 (oder 10-EB hexadezimal) jedoch sicher für Fernsehgeräte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-656">While there are different schools of thought in what are considered TV-safe colors, colors within the RGB values of 16-235 (or 10-EB in hexadecimal) are generally safe to use for TV.</span></span>

![Fernsehsicherer Farbbereich](images/designing-for-tv/tv-safe-colors.png)

### <a name="fixing-tv-unsafe-colors"></a><span data-ttu-id="c1179-658">Korrigieren nicht fernsehsicherer Farben</span><span class="sxs-lookup"><span data-stu-id="c1179-658">Fixing TV-unsafe colors</span></span>

<span data-ttu-id="c1179-659">Das Korrigieren nicht fernsehsicherer Farben durch die Anpassung ihrer RGB-Werte, sodass sich diese innerhalb des fernsehsicheren Bereichs befinden, wird in der Regel als **Farbklammerung** (Color Clamping) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c1179-659">Fixing TV-unsafe colors individually by adjusting their RGB values to be within the TV-safe range is typically referred to as **color clamping**.</span></span> <span data-ttu-id="c1179-660">Diese Methode ist vielleicht für Apps geeignet, die keine umfassenden Farbpaletten verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1179-660">This method may be appropriate for an app that doesn't use a rich color palette.</span></span> <span data-ttu-id="c1179-661">Wenn Farben auf diese Weise korrigiert werden, kann dies jedoch dazu führen, dass sie miteinander kollidieren. Dies resultiert in einer nicht optimalen 10-Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="c1179-661">However, fixing colors using only this method may cause colors to collide with each other, which doesn't provide for the best 10-foot experience.</span></span>

<span data-ttu-id="c1179-662">Stattdessen empfehlen wir Ihnen, zur Optimierung Ihrer Farbpalette für Fernsehgeräte zunächst mittels eines Verfahrens wie der Farbklammerung sicherzustellen, dass Ihre Farben fernsehsicher sind, und dann eine **Skalierung** anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c1179-662">To optimize your color palette for TV, we recommend that you first ensure that your colors are TV-safe through a method such as color clamping, then use a method called **scaling**.</span></span>

<span data-ttu-id="c1179-663">Dies bedeutet, dass alle RGB-Werte Ihrer Farben um einen bestimmten Faktor skaliert werden, damit sich diese innerhalb des fernsehsicheren Bereichs befinden.</span><span class="sxs-lookup"><span data-stu-id="c1179-663">This involves scaling all of your colors' RGB values by a certain factor to get them within the TV-safe range.</span></span> <span data-ttu-id="c1179-664">Die Skalierung aller Farben Ihrer App verhindert, dass Farben kollidieren, und sorgt für eine bessere 10-Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="c1179-664">Scaling all of your app's colors helps prevent color collision and makes for a better 10-foot experience.</span></span>

![Vergleich von Klammerung und Skalierung](images/designing-for-tv/clamping-vs-scaling.png)

### <a name="assets"></a><span data-ttu-id="c1179-666">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c1179-666">Assets</span></span>

<span data-ttu-id="c1179-667">Stellen Sie sicher, dass Sie auch die Ressourcen entsprechend aktualisieren, wenn Sie Farben ändern.</span><span class="sxs-lookup"><span data-stu-id="c1179-667">When making changes to colors, make sure to also update assets accordingly.</span></span> <span data-ttu-id="c1179-668">Wenn Ihre App in XAML eine Farbe verwendet, die identisch mit einer Ressourcenfarbe sein soll, Sie jedoch lediglich den XAML-Code aktualisieren, werden die Farben Ihrer Ressourcen abweichen.</span><span class="sxs-lookup"><span data-stu-id="c1179-668">If your app uses a color in XAML that is supposed to look the same as an asset color, but you only update the XAML code, your assets will look off-color.</span></span>

### <a name="uwp-color-sample"></a><span data-ttu-id="c1179-669">Beispiel für UWP-Farbe</span><span class="sxs-lookup"><span data-stu-id="c1179-669">UWP color sample</span></span>

<span data-ttu-id="c1179-670">[UWP-Farbdesigns](../style/color.md) wurden auf der Grundlage eines **schwarzen** Hintergrunds für das dunkle Design oder eines **weißen** Hintergrunds für das helle Design Ihrer App entwickelt.</span><span class="sxs-lookup"><span data-stu-id="c1179-670">[UWP color themes](../style/color.md) are designed around the app's background being either **black** for the dark theme or **white** for the light theme.</span></span> <span data-ttu-id="c1179-671">Da weder Schwarz noch Weiß fernsehsicher sind, müssen diese Farben mittels *Klammerung* korrigiert werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-671">Because neither black nor white are TV-safe, these colors needed to be fixed by using *clamping*.</span></span> <span data-ttu-id="c1179-672">Nach ihrer Korrektur müssen alle anderen Farben mittels *Skalierung* angepasst werden, um den erforderlichen Kontrast zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c1179-672">After they were fixed, all the other colors needed to be adjusted through *scaling* to retain the necessary contrast.</span></span>

<!--[v-lcap to eliot]why is the above paragraph in the past tense?-->
<!--[elcowle] Because this is something that Microsoft had to do to the UWP color themes to accommodate TV-safe colors for Xbox. These themes are then provided in the below code sample.-->

<span data-ttu-id="c1179-673">Der folgende Beispielcode stellt ein Farbdesign bereit, das für die Verwendung auf Fernsehgeräten optimiert wurde:</span><span class="sxs-lookup"><span data-stu-id="c1179-673">The following sample code provides a color theme that has been optimized for TV use:</span></span>

```xml
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.ThemeDictionaries>
            <ResourceDictionary x:Key="Default">
                <SolidColorBrush x:Key="ApplicationPageBackgroundThemeBrush"
                                 Color="#FF101010"/>
                <Color x:Key="SystemAltHighColor">#FF101010</Color>
                <Color x:Key="SystemAltLowColor">#33101010</Color>
                <Color x:Key="SystemAltMediumColor">#99101010</Color>
                <Color x:Key="SystemAltMediumHighColor">#CC101010</Color>
                <Color x:Key="SystemAltMediumLowColor">#66101010</Color>
                <Color x:Key="SystemBaseHighColor">#FFEBEBEB</Color>
                <Color x:Key="SystemBaseLowColor">#33EBEBEB</Color>
                <Color x:Key="SystemBaseMediumColor">#99EBEBEB</Color>
                <Color x:Key="SystemBaseMediumHighColor">#CCEBEBEB</Color>
                <Color x:Key="SystemBaseMediumLowColor">#66EBEBEB</Color>
                <Color x:Key="SystemChromeAltLowColor">#FFDDDDDD</Color>
                <Color x:Key="SystemChromeBlackHighColor">#FF101010</Color>
                <Color x:Key="SystemChromeBlackLowColor">#33101010</Color>
                <Color x:Key="SystemChromeBlackMediumLowColor">#66101010</Color>
                <Color x:Key="SystemChromeBlackMediumColor">#CC101010</Color>
                <Color x:Key="SystemChromeDisabledHighColor">#FF333333</Color>
                <Color x:Key="SystemChromeDisabledLowColor">#FF858585</Color>
                <Color x:Key="SystemChromeHighColor">#FF767676</Color>
                <Color x:Key="SystemChromeLowColor">#FF1F1F1F</Color>
                <Color x:Key="SystemChromeMediumColor">#FF262626</Color>
                <Color x:Key="SystemChromeMediumLowColor">#FF2B2B2B</Color>
                <Color x:Key="SystemChromeWhiteColor">#FFEBEBEB</Color>
                <Color x:Key="SystemListLowColor">#19EBEBEB</Color>
                <Color x:Key="SystemListMediumColor">#33EBEBEB</Color>
            </ResourceDictionary>
            <ResourceDictionary x:Key="Light">
                <SolidColorBrush x:Key="ApplicationPageBackgroundThemeBrush"
                                 Color="#FFEBEBEB" /> 
                <Color x:Key="SystemAltHighColor">#FFEBEBEB</Color>
                <Color x:Key="SystemAltLowColor">#33EBEBEB</Color>
                <Color x:Key="SystemAltMediumColor">#99EBEBEB</Color>
                <Color x:Key="SystemAltMediumHighColor">#CCEBEBEB</Color>
                <Color x:Key="SystemAltMediumLowColor">#66EBEBEB</Color>
                <Color x:Key="SystemBaseHighColor">#FF101010</Color>
                <Color x:Key="SystemBaseLowColor">#33101010</Color>
                <Color x:Key="SystemBaseMediumColor">#99101010</Color>
                <Color x:Key="SystemBaseMediumHighColor">#CC101010</Color>
                <Color x:Key="SystemBaseMediumLowColor">#66101010</Color>
                <Color x:Key="SystemChromeAltLowColor">#FF1F1F1F</Color>
                <Color x:Key="SystemChromeBlackHighColor">#FF101010</Color>
                <Color x:Key="SystemChromeBlackLowColor">#33101010</Color>
                <Color x:Key="SystemChromeBlackMediumLowColor">#66101010</Color>
                <Color x:Key="SystemChromeBlackMediumColor">#CC101010</Color>
                <Color x:Key="SystemChromeDisabledHighColor">#FFCCCCCC</Color>
                <Color x:Key="SystemChromeDisabledLowColor">#FF7A7A7A</Color>
                <Color x:Key="SystemChromeHighColor">#FFB2B2B2</Color>
                <Color x:Key="SystemChromeLowColor">#FFDDDDDD</Color>
                <Color x:Key="SystemChromeMediumColor">#FFCCCCCC</Color>
                <Color x:Key="SystemChromeMediumLowColor">#FFDDDDDD</Color>
                <Color x:Key="SystemChromeWhiteColor">#FFEBEBEB</Color>
                <Color x:Key="SystemListLowColor">#19101010</Color>
                <Color x:Key="SystemListMediumColor">#33101010</Color>
            </ResourceDictionary> 
        </ResourceDictionary.ThemeDictionaries>
    </ResourceDictionary>
</Application.Resources>
```

> [!NOTE]
> <span data-ttu-id="c1179-674">Die hellen Designs **SystemChromeMediumLowColor** und **SystemChromeMediumLowColor** haben absichtlich die gleiche Farbe. Dies liegt nicht an der Klammerung.</span><span class="sxs-lookup"><span data-stu-id="c1179-674">The light theme **SystemChromeMediumLowColor** and **SystemChromeMediumLowColor** are the same color on purpose and not caused as a result of clamping.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-675">Hexadezimale Farben werden in **ARGB** (Alpha, Rot, Grün, Blau) angegeben.</span><span class="sxs-lookup"><span data-stu-id="c1179-675">Hexadecimal colors are specified in **ARGB** (Alpha Red Green Blue).</span></span>

<span data-ttu-id="c1179-676">Es wird nicht empfohlen, fernsehsichere Farben ohne Klammerung auf einem Monitor zu verwenden, der die gesamte Palette anzeigen kann, da die Farben in diesem Fall verwaschen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-676">We don't recommend using TV-safe colors on a monitor able to display the full range without clamping because the colors will look washed out.</span></span> <span data-ttu-id="c1179-677">Laden Sie stattdessen das Ressourcenverzeichnis (aus dem vorherigen Beispiel), wenn Ihre App auf Xbox ausgeführt wird, jedoch *nicht* auf anderen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="c1179-677">Instead, load the resource dictionary (previous sample) when your app is running on Xbox but *not* other platforms.</span></span> <span data-ttu-id="c1179-678">Fügen Sie in der `OnLaunched`-Methode aus `App.xaml.cs` die folgende Prüfung hinzu:</span><span class="sxs-lookup"><span data-stu-id="c1179-678">In the `OnLaunched` method of `App.xaml.cs`, add the following check:</span></span>

```csharp
if (IsTenFoot)
{ 
    this.Resources.MergedDictionaries.Add(new ResourceDictionary
    {
        Source = new Uri("ms-appx:///TenFootStylesheet.xaml")
    }); 
}
```

> [!NOTE]
> <span data-ttu-id="c1179-679">Die `IsTenFoot`-Variable wird in [Benutzerdefinierter visueller Zustandsauslöser für Xbox One](#custom-visual-state-trigger-for-xbox) definiert.</span><span class="sxs-lookup"><span data-stu-id="c1179-679">The `IsTenFoot` variable is defined in [Custom visual state trigger for Xbox](#custom-visual-state-trigger-for-xbox).</span></span>

<span data-ttu-id="c1179-680">Dadurch wird sichergestellt, dass unabhängig von dem Gerät, auf dem die App ausgeführt wird, die richtigen Farben angezeigt werden. Dem Benutzer wird so eine bessere und ästhetisch ansprechendere Umgebung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="c1179-680">This will ensure that the correct colors will display on whichever device the app is running, providing the user with a better, more aesthetically pleasing experience.</span></span>

## <a name="guidelines-for-ui-controls"></a><span data-ttu-id="c1179-681">Richtlinien für Benutzeroberflächensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="c1179-681">Guidelines for UI controls</span></span>

<span data-ttu-id="c1179-682">Es gibt mehrere Benutzeroberflächen-Steuerelemente, die auf mehreren Geräten gut funktionieren. Wenn diese jedoch auf Fernsehgeräten verwendet werden, müssen bestimmte Aspekte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-682">There are several UI controls that work well across multiple devices, but have certain considerations when used on TV.</span></span> <span data-ttu-id="c1179-683">Informieren Sie sich über einige bewährte Methoden für die Verwendung dieser Steuerelemente beim Entwerfen für die 10 Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="c1179-683">Read about some best practices for using these controls when designing for the 10-foot experience.</span></span>

### <a name="pivot-control"></a><span data-ttu-id="c1179-684">Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="c1179-684">Pivot control</span></span>

<span data-ttu-id="c1179-685">Ein [Pivot](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.aspx) ermöglicht über verschiedene Header oder Registerkarten eine schnelle Navigation für Ansichten in einer App.</span><span class="sxs-lookup"><span data-stu-id="c1179-685">A [Pivot](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.aspx) provides quick navigation of views within an app through selecting different headers or tabs.</span></span> <span data-ttu-id="c1179-686">Das Steuerelement unterstreicht jeweils den Header, der den Fokus hat. So wird bei der Nutzung von Gamepads/Remotesteuerungen deutlicher, welcher Header zurzeit ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-686">The control underlines whichever header has focus, making it more obvious which header is currently selected when using gamepad/remote.</span></span>

![Pivotunterstreichung](images/designing-for-tv/pivot-underline.png)

<!--By default, when you navigate to a `Pivot`, one of the [PivotItem](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivotitem.aspx)s will get focus. However, you can show focus around all the headers by setting `Pivot.HeaderFocusVisualPlacement="ItemHeaders"`.

![Pivot focus around headers](images/designing-for-tv/pivot-headers-focus.png)-->

<span data-ttu-id="c1179-688">Sie können die [Pivot.IsHeaderItemsCarouselEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.isheaderitemscarouselenabled.aspx)-Eigenschaft auf `true` festlegen, damit Pivots stets die gleiche Position haben und die Kopfzeile des ausgewählten Pivots nicht stets an die erste Position verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-688">You can set the [Pivot.IsHeaderItemsCarouselEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.pivot.isheaderitemscarouselenabled.aspx) property to `true` so that pivots always keep the same position, rather than having the selected pivot header always move to the first position.</span></span> <span data-ttu-id="c1179-689">Dies ist besser für große Geräte mit großen Bildschirmanzeigen wie Fernsehgeräte geeignet, da Kopfzeilenumbrüche Benutzer stark ablenken können.</span><span class="sxs-lookup"><span data-stu-id="c1179-689">This is a better experience for large-screen displays such as TV, because header wrapping can be distracting to users.</span></span> <span data-ttu-id="c1179-690">Wenn nicht alle Pivotkopfzeilen gleichzeitig auf den Bildschirm passen, wird eine Bildlaufleiste angezeigt, damit Kunden die restlichen Kopfzeilen sehen. Sie sollten jedoch sicherstellen, dass alle Kopfzeilen auf den Bildschirm passen, um eine optimale Erfahrung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-690">If all of the pivot headers don't fit onscreen at once, there will be a scrollbar to let customers see the other headers; however, you should make sure that they all fit on the screen to provide the best experience.</span></span> <span data-ttu-id="c1179-691">Weitere Informationen finden Sie unter [Registerkarten und Pivots](../controls-and-patterns/tabs-pivot.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-691">For more information, see [Tabs and pivots](../controls-and-patterns/tabs-pivot.md).</span></span>

<!--If you find it necessary to wrap headers, you can set it so that it doesn't show the selected header in the left-most position, like it does by default. When you set `Pivot.IsHeaderItemsCarouselEnabled="False"`, the selected header will move left by the minimal amount required to become fully visible. This is the recommended approach for 10-foot design.

![Pivot headers carousel disabled](images/designing-for-tv/pivot-headers-carousel.png)-->

### <a name="navigation-pane-a-namenavigation-pane"></a><span data-ttu-id="c1179-692">Navigationsbereich <a name="navigation-pane"></span><span class="sxs-lookup"><span data-stu-id="c1179-692">Navigation pane <a name="navigation-pane"></span></span>

<span data-ttu-id="c1179-693">Ein Navigationsbereich (auch *Hamburger-Menü* genannt) ist ein Navigationssteuerelement, das häufig in UWP-Apps verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-693">A navigation pane (also known as a *hamburger menu*) is a navigation control commonly used in UWP apps.</span></span> <span data-ttu-id="c1179-694">In der Regel handelt es sich um einen Bereich mit mehreren Optionen im Stil eine Liste, mit denen die Benutzer zu anderen Seiten wechseln können.</span><span class="sxs-lookup"><span data-stu-id="c1179-694">Typically it is a pane with several options to choose from in a list style menu that will take the user to different pages.</span></span> <span data-ttu-id="c1179-695">Im Allgemeinen ist dieser Bereich zu Beginn reduziert, um Platz zu sparen. Der Benutzer kann ihn durch Klicken auf eine Schaltfläche öffnen.</span><span class="sxs-lookup"><span data-stu-id="c1179-695">Generally this pane starts out collapsed to save space, and the user can open it by clicking on a button.</span></span>

<span data-ttu-id="c1179-696">Während Nav-Bereiche leicht über die Maus- und Touch-Bedienung genutzt werden können, ist die Bedienung über Gamepads/Fernbedienungen weniger praktisch. Der Benutzer muss hier immer erst zu einer Schaltfläche navigieren, um den jeweiligen Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c1179-696">While nav panes are very accessible with mouse and touch, gamepad/remote makes them less accessible since the user has to navigate to a button to open the pane.</span></span> <span data-ttu-id="c1179-697">Aus diesem Grund empfiehlt es sich, den Navigationsbereich über die **Ansicht**-Schaltfläche zu öffnen und dem Benutzer das Öffnen über das Navigieren zum linken Rand der Seite zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c1179-697">Therefore, a good practice is to have the **View** button open the nav pane, as well as allow the user to open it by navigating all the way to the left of the page.</span></span> <span data-ttu-id="c1179-698">Ein Codebeispiel zum Implementieren dieses Entwurfsmusters finden Sie im Dokument [Verwalten der Fokusnavigation](managing-focus-navigation.md#split-view-code-sample) .</span><span class="sxs-lookup"><span data-stu-id="c1179-698">Code sample on how to implement this design pattern can be found in [Managing focus navigation](managing-focus-navigation.md#split-view-code-sample) document.</span></span> <span data-ttu-id="c1179-699">So steht dem Benutzer ein sehr einfacher Zugriff auf die Inhalte des Bereichs zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c1179-699">This will provide the user with very easy access to the contents of the pane.</span></span> <span data-ttu-id="c1179-700">Weitere Informationen zum Verhalten von Navigationsbereichen auf unterschiedlichen Bildschirmgrößen sowie zu bewährten Vorgehensweisen für die Navigation mit Gamepads/Fernbedienungen finden Sie unter [Navigationsbereiche](../controls-and-patterns/navigationview.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-700">For more information about how nav panes behave in different screen sizes as well as best practices for gamepad/remote navigation, see [Nav panes](../controls-and-patterns/navigationview.md).</span></span>

### <a name="commandbar-labels"></a><span data-ttu-id="c1179-701">CommandBar-Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="c1179-701">CommandBar labels</span></span>

<span data-ttu-id="c1179-702">Es empfiehlt sich, die Beschriftungen rechts neben den Symbolen auf einer [CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx) zu platzieren. So bleibt dessen Höhe minimiert und konsistent.</span><span class="sxs-lookup"><span data-stu-id="c1179-702">It is a good idea to have the labels placed to the right of the icons on a [CommandBar](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.aspx) so that its height is minimized and stays consistent.</span></span> <span data-ttu-id="c1179-703">Sie erreichen dies, indem Sie die Eigenschaft [CommandBar.DefaultLabelPosition](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.defaultlabelposition.aspx) auf `CommandBarDefaultLabelPosition.Right` festlegen.</span><span class="sxs-lookup"><span data-stu-id="c1179-703">You can do this by setting the [CommandBar.DefaultLabelPosition](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.commandbar.defaultlabelposition.aspx) property to `CommandBarDefaultLabelPosition.Right`.</span></span>

![CommandBar Beschriftungen rechts von Symbolen](images/designing-for-tv/commandbar.png)

<span data-ttu-id="c1179-705">Durch das Festlegen dieser Eigenschaft werden die Beschriftungen immer angezeigt. Dies ist bei einer 10-Fuß-Erfahrung vorteilhaft, denn es minimiert die Anzahl der durch den Benutzer erforderlichen Klicks.</span><span class="sxs-lookup"><span data-stu-id="c1179-705">Setting this property will also cause the labels to always be displayed, which works well for the 10-foot experience because it minimizes the number of clicks for the user.</span></span> <span data-ttu-id="c1179-706">Auch für andere Gerätetypen ist dies ein hervorragendes Konzept.</span><span class="sxs-lookup"><span data-stu-id="c1179-706">This is also a great model for other device types to follow.</span></span>

<!--When there isn't enough space in the window to fit all of the `AppBarButton`s, buttons move into an overflow menu, which is accessed by selecting the "..." button. This happens dynamically as the screen resizes. This generally shouldn't be a problem for TV because the screen size is so large, but if you find that you have overflow buttons, you can specify which appear first using the `AppBarButton.DynamicOverflowOrder` property.

![CommandBar with overflow commands](images/designing-for-tv/commandbar-overflow.png)-->

### <a name="tooltip"></a><span data-ttu-id="c1179-707">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="c1179-707">Tooltip</span></span>

<span data-ttu-id="c1179-708">Das Steuerelement [QuickInfo](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltip.aspx) wurde eingeführt, um zusätzliche Informationen in der Benutzeroberfläche anzeigen zu können, wenn der Benutzer mit der Maus auf ein Element zeigt oder mit dem Finger auf ein Element tippt und den Finger darauf hält.</span><span class="sxs-lookup"><span data-stu-id="c1179-708">The [Tooltip](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.tooltip.aspx) control was introduced as a way to provide more information in the UI when the user hovers the mouse over, or taps and holds their figure on, an element.</span></span> <span data-ttu-id="c1179-709">Für Gamepad und Remote wird `Tooltip` kurz nachdem das Element den Fokus erhält angezeigt, bleibt für einen kurzen Zeitraum auf dem Bildschirm und verschwindet dann.</span><span class="sxs-lookup"><span data-stu-id="c1179-709">For gamepad and remote, `Tooltip` appears after a brief moment when the element gets focus, stays onscreen for a short time, and then disappears.</span></span> <span data-ttu-id="c1179-710">Dieses Verhalten könnte ablenkend wirken, wenn zu viele `Tooltip`-Elemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-710">This behavior could be distracting if too many `Tooltip`s are used.</span></span> <span data-ttu-id="c1179-711">Versuchen Sie, `Tooltip`-Elemente bei Entwürfen für Fernsehgeräte zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-711">Try to avoid using `Tooltip` when designing for TV.</span></span>

### <a name="button-styles"></a><span data-ttu-id="c1179-712">Schaltflächenstile</span><span class="sxs-lookup"><span data-stu-id="c1179-712">Button styles</span></span>

<span data-ttu-id="c1179-713">Zwar funktionieren die Standard-UWP-Schaltflächen sehr gut auf TV-Bildschirmen, es gibt jedoch einige visuelle Stile für Schaltflächen, die noch besser auf die Benutzeroberfläche aufmerksam machen. Sie sollten diese für alle Plattformen in Erwägung ziehen, besonders für die 10-Fuß-Umgebung, bei der es sehr vorteilhaft ist, die Fokusposition klar und deutlich darzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-713">While the standard UWP buttons work well on TV, some visual styles of buttons call attention to the UI better, which you may want to consider for all platforms, particularly in the 10-foot experience, which benefits from clearly communicating where the focus is located.</span></span> <span data-ttu-id="c1179-714">Weitere Informationen zu diesen Stilen finden Sie unter [Schaltflächen](../controls-and-patterns/buttons.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-714">To read more about these styles, see [Buttons](../controls-and-patterns/buttons.md).</span></span>

### <a name="nested-ui-elements"></a><span data-ttu-id="c1179-715">Geschachtelte UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="c1179-715">Nested UI elements</span></span>

<span data-ttu-id="c1179-716">Eine geschachtelte Benutzeroberfläche (User Interface, UI) verfügt über geschachtelte Elemente mit ausführbaren Aktionen, die in einem Container eingeschlossen sind, sodass sowohl die geschachtelten Elemente als auch die Container unabhängig voneinander den Fokus erhalten können.</span><span class="sxs-lookup"><span data-stu-id="c1179-716">Nested UI exposes nested actionable items enclosed inside a container UI element where both the nested item as well as the container item can take independent focus from each other.</span></span>

<span data-ttu-id="c1179-717">Geschachtelte UI eignet sich für einige Eingabetypen, jedoch nicht immer für Gamepads und Fernbedienungen, da diese eine XY-Navigation erfordern.</span><span class="sxs-lookup"><span data-stu-id="c1179-717">Nested UI works well for some input types, but not always for gamepad and remote, which rely on XY navigation.</span></span> <span data-ttu-id="c1179-718">Beachten Sie die unter diesem Thema angeführten Richtlinien, um sicherzustellen, dass die Benutzeroberfläche für die 10-Fuß-Umgebung optimiert ist, und dass die Benutzer mühelos auf alle interaktiven Elemente zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-718">Be sure to follow the guidance in this topic to ensure that your UI is optimized for the 10-foot environment, and that the user can access all interactable elements easily.</span></span> <span data-ttu-id="c1179-719">Eine gängige Lösung besteht darin, geschachtelte UI-Elemente in einem `ContextFlyout` zu platzieren (siehe [CommandBar und ContextFlyout](#commandbar-and-contextflyout)).</span><span class="sxs-lookup"><span data-stu-id="c1179-719">One common solution is to place nested UI elements in a `ContextFlyout` (see [CommandBar and ContextFlyout](#commandbar-and-contextflyout)).</span></span>

<span data-ttu-id="c1179-720">Weitere Informationen zur geschachtelten UI finden Sie unter [Geschachtelte UI bei Listenelementen](../controls-and-patterns/nested-ui.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-720">For more information on nested UI, see [Nested UI in list items](../controls-and-patterns/nested-ui.md).</span></span>

### <a name="mediatransportcontrols"></a><span data-ttu-id="c1179-721">MediaTransportControls</span><span class="sxs-lookup"><span data-stu-id="c1179-721">MediaTransportControls</span></span>

<span data-ttu-id="c1179-722">Das [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediatransportcontrols.aspx)-Element ermöglicht Benutzern die Interaktion mit ihren Medien. Hierzu stellt es eine standardmäßige Wiedergabeumgebung bereit, in der Benutzer unter anderem die Wiedergabe starten und anhalten sowie Untertitel aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="c1179-722">The [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediatransportcontrols.aspx) element lets users interact with their media by providing a default playback experience that allows them to play, pause, turn on closed captions, and more.</span></span> <span data-ttu-id="c1179-723">Dieses Steuerelement ist eine Eigenschaft von [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.MediaPlayerElement.aspx) und unterstützt zwei Layoutoptionen: *einzeilig* und *zweizeilig*.</span><span class="sxs-lookup"><span data-stu-id="c1179-723">This control is a property of [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.MediaPlayerElement.aspx) and supports two layout options: *single-row* and *double-row*.</span></span> <span data-ttu-id="c1179-724">Beim einzeiligen Layout befinden sich der Schieberegler und die Wiedergabeschaltflächen alle in einer Zeile, und die Schaltfläche für Wiedergabe/Pause wird links neben dem Schieberegler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-724">In the single-row layout, the slider and playback buttons are all located in one row, with the play/pause button located to the left of the slider.</span></span> <span data-ttu-id="c1179-725">Beim zweizeiligen Layout befindet sich der Schieberegler in einer eigenen Zeile, und die Wiedergabeschaltflächen werden in einer Zeile darunter angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-725">In the double-row layout, the slider occupies its own row, with the playback buttons on a separate lower row.</span></span> <span data-ttu-id="c1179-726">Bei Designs für die 10-Fuß-Erfahrung empfiehlt sich die Verwendung des zweizeiligen Layouts, da es eine bessere Gamepadnavigation ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c1179-726">When designing for the 10-foot experience, the double-row layout should be used, as it provides better navigation for gamepad.</span></span> <span data-ttu-id="c1179-727">Wenn Sie das zweizeilige Layout aktivieren möchten, legen Sie in der [TransportControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.transportcontrols.aspx)-Eigenschaft von `MediaPlayerElement` für das `MediaTransportControls`-Element Folgendes fest: `IsCompact="False"`.</span><span class="sxs-lookup"><span data-stu-id="c1179-727">To enable the double-row layout, set `IsCompact="False"` on the `MediaTransportControls` element in the [TransportControls](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.transportcontrols.aspx) property of the `MediaPlayerElement`.</span></span>

```xml
<MediaPlayerElement x:Name="mediaPlayerElement1"  
                    Source="Assets/video.mp4"
                    AreTransportControlsEnabled="True">
    <MediaPlayerElement.TransportControls>
        <MediaTransportControls IsCompact="False"/>
    </MediaPlayerElement.TransportControls>
</MediaPlayerElement>
```  

<span data-ttu-id="c1179-728">Weitere Informationen zum Hinzufügen von Medien zu Ihrer App finden Sie unter [Medienwiedergabe](../controls-and-patterns/media-playback.md).</span><span class="sxs-lookup"><span data-stu-id="c1179-728">Visit [Media playback](../controls-and-patterns/media-playback.md) to learn more about adding media to your app.</span></span>

> <span data-ttu-id="c1179-729">![HINWEIS:] `MediaPlayerElement` steht erst ab der Windows10-Version1607 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c1179-729">![NOTE] `MediaPlayerElement` is only available in Windows 10, version 1607 and later.</span></span> <span data-ttu-id="c1179-730">Bei Apps für niedrigere Windows10-Versionen muss stattdessen [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1179-730">If you're developing an app for an earlier version of Windows 10, you'll need to use [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926) instead.</span></span> <span data-ttu-id="c1179-731">Die hier angegebenen Empfehlungen gelten auch für `MediaElement`, und der Zugriff auf die `TransportControls`-Eigenschaft erfolgt auf die gleiche Weise.</span><span class="sxs-lookup"><span data-stu-id="c1179-731">The recommendations above apply to `MediaElement` as well, and the `TransportControls` property is accessed in the same way.</span></span>

### <a name="search-experience"></a><span data-ttu-id="c1179-732">Suchvorgang</span><span class="sxs-lookup"><span data-stu-id="c1179-732">Search experience</span></span>

<span data-ttu-id="c1179-733">Die Suche nach Inhalten ist eine der am häufigsten ausgeführten Funktionen in der 10-Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="c1179-733">Searching for content is one of the most commonly performed functions in the 10-foot experience.</span></span> <span data-ttu-id="c1179-734">Wenn Ihre App eine Suchfunktion zur Verfügung stellt, sollte der Benutzer auf diese schnell über die **Y**-Taste auf dem Gamepad zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="c1179-734">If your app provides a search experience, it is helpful for the user to have quick access to it by using the **Y** button on the gamepad as an accelerator.</span></span>

<span data-ttu-id="c1179-735">Die meisten Kunden sollten mit dieser Beschleunigungsfunktion bereits vertraut sein. Sie können aber auch der Benutzeroberfläche eine visuelle **Y**-Glyphe hinzufügen, um anzuzeigen, dass der Benutzer mit dieser Taste auf die Suchfunktion zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="c1179-735">Most customers should already be familiar with this accelerator, but if you like you can add a visual **Y** glyph to the UI to indicate that the customer can use the button to access search functionality.</span></span> <span data-ttu-id="c1179-736">In diesem Fall müssen Sie das Symbol aus der Schriftart **Segoe Xbox MDL2 Symbol** (`&#xE3CC;` für XAML-Apps, `\E426` für HTML-Apps) verwenden, um die Konsistenz sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-736">If you do add this cue, be sure to use the symbol from the **Segoe Xbox MDL2 Symbol** font (`&#xE3CC;` for XAML apps, `\E426` for HTML apps) to provide consistency with the Xbox shell and other apps.</span></span>

> [!NOTE]
> <span data-ttu-id="c1179-737">Da die Schriftart **Segoe Xbox MDL2 Symbol** nur auf Xbox verfügbar ist, wird das Symbol auf Ihrem PC nicht ordnungsgemäß angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c1179-737">Because the **Segoe Xbox MDL2 Symbol** font is only available on Xbox, the symbol won't appear correctly on your PC.</span></span> <span data-ttu-id="c1179-738">Es wird jedoch auf dem Fernseher angezeigt, nachdem Sie auf Xbox bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c1179-738">However, it will show up on the TV once you deploy to Xbox.</span></span>

<span data-ttu-id="c1179-739">Da die **Y**-Taste nur auf dem Gamepad verfügbar ist, müssen Sie auch andere Möglichkeiten für den Zugriff auf die Suche zur Verfügung stellen, wie Schaltflächen in der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="c1179-739">Since the **Y** button is only available on gamepad, make sure to provide other methods of access to search, such as buttons in the UI.</span></span> <span data-ttu-id="c1179-740">Andernfalls können einige Kunden möglicherweise nicht auf diese Funktion zugreifen.</span><span class="sxs-lookup"><span data-stu-id="c1179-740">Otherwise, some customers may not be able to access the functionality.</span></span>

<span data-ttu-id="c1179-741">In der 10-Fuß-Erfahrung ist es für Kunden oft einfacher, eine Vollbildschirm-Suche durchzuführen, da der Platz auf dem Display begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="c1179-741">In the 10-foot experience, it is often easier for customers to use a full screen search experience because there is limited room on the display.</span></span> <span data-ttu-id="c1179-742">Unabhängig davon, ob Sie eine Voll- oder Teilbildschirm-Direktsuche haben, empfehlen wir, dass die Bildschirmtastatur bereits geöffnet ist, wenn der Benutzer die Suchfunktion öffnet, damit sofort Suchbegriffe eingegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="c1179-742">Whether you have full screen or partial-screen, "in-place" search, we recommend that when the user opens the search experience, the onscreen keyboard appears already opened, ready for the customer to enter search terms.</span></span>

## <a name="custom-visual-state-trigger-for-xbox"></a><span data-ttu-id="c1179-743">Benutzerdefinierter visueller Zustandsauslöser für Xbox</span><span class="sxs-lookup"><span data-stu-id="c1179-743">Custom visual state trigger for Xbox</span></span>

<span data-ttu-id="c1179-744">Um Ihre UWP-App an die 10-Fuß-Erfahrung anzupassen, empfehlen wir Ihnen, das Layout zu ändern, wenn die App erkennt, dass sie auf einer Xbox-Konsole gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="c1179-744">To tailor your UWP app for the 10-foot experience, we recommend that you make layout changes when the app detects that it has been launched on an Xbox console.</span></span> <span data-ttu-id="c1179-745">Eine Möglichkeit, um dies zu erreichen ist die Verwendung eines benutzerdefinierten *visuellen Zustandsauslösers*.</span><span class="sxs-lookup"><span data-stu-id="c1179-745">One way to do this is by using a custom *visual state trigger*.</span></span> <span data-ttu-id="c1179-746">Visuelle Zustandsauslöser sind besonders dann nützlich, wenn Sie in **Blend für Visual Studio** arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="c1179-746">Visual state triggers are most useful when you want to edit in **Blend for Visual Studio**.</span></span> <span data-ttu-id="c1179-747">Der folgende Codeausschnitt zeigt, wie ein visueller Zustandsauslöser für Xbox erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="c1179-747">The following code snippet shows how to create a visual state trigger for Xbox:</span></span>

```xml
<VisualStateManager.VisualStateGroups>
    <VisualStateGroup>
        <VisualState>
            <VisualState.StateTriggers>
                <triggers:DeviceFamilyTrigger DeviceFamily="Windows.Xbox"/>
            </VisualState.StateTriggers>
            <VisualState.Setters>
                <Setter Target="RootSplitView.OpenPaneLength"
                        Value="368"/>
                <Setter Target="RootSplitView.CompactPaneLength"
                        Value="96"/>
                <Setter Target="NavMenuList.Margin"
                        Value="0,75,0,27"/>
                <Setter Target="Frame.Margin"
                        Value="0,27,48,27"/>
                <Setter Target="NavMenuList.ItemContainerStyle"
                        Value="{StaticResource NavMenuItemContainerXboxStyle}"/>
            </VisualState.Setters>
        </VisualState>
    </VisualStateGroup>
</VisualStateManager.VisualStateGroups>
```

<span data-ttu-id="c1179-748">Um den Auslöser zu erstellen, fügen Sie Ihrer App die folgende Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="c1179-748">To create the trigger, add the following class to your app.</span></span> <span data-ttu-id="c1179-749">Dies ist die Klasse, die in dem XAML-Code oben referenziert wird:</span><span class="sxs-lookup"><span data-stu-id="c1179-749">This is the class that is referenced by the XAML code above:</span></span>

```csharp
class DeviceFamilyTrigger : StateTriggerBase
{
    private string _currentDeviceFamily, _queriedDeviceFamily;

    public string DeviceFamily
    {
        get
        {
            return _queriedDeviceFamily;
        }

        set
        {
            _queriedDeviceFamily = value;
            _currentDeviceFamily = AnalyticsInfo.VersionInfo.DeviceFamily;
            SetActive(_queriedDeviceFamily == _currentDeviceFamily);
        }
    }
}
```

<span data-ttu-id="c1179-750">Nachdem Sie den benutzerdefinierten Auslöser hinzugefügt haben, wird Ihre App automatisch die Layoutänderungen ausführen, die Sie im XAML-Code angegeben haben, wenn sie erkennt, dass sie auf einer Xbox One-Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c1179-750">After you've added your custom trigger, your app will automatically make the layout modifications you specified in your XAML code whenever it detects that it is running on an Xbox One console.</span></span>

<span data-ttu-id="c1179-751">Sie können außerdem über Programmcode erkennen, ob die App auf Xbox ausgeführt wird, und dann entsprechende Anpassungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="c1179-751">Another way you can check whether your app is running on Xbox and then make the appropriate adjustments is through code.</span></span> <span data-ttu-id="c1179-752">Mit der folgenden einfachen Variable können Sie überprüfen, ob Ihre App auf Xbox ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="c1179-752">You can use the following simple variable to check if your app is running on Xbox:</span></span>

```csharp
bool IsTenFoot = (Windows.System.Profile.AnaylticsInfo.VersionInfo.DeviceFamily ==
                    "Windows.Xbox");
```

<span data-ttu-id="c1179-753">Anschließend können Sie im Codeblock nach der Überprüfung die entsprechenden Anpassungen für Ihr UI vornehmen.</span><span class="sxs-lookup"><span data-stu-id="c1179-753">Then, you can make the appropriate adjustments to your UI in the code block following this check.</span></span> <span data-ttu-id="c1179-754">Ein Beispiel hierfür finden Sie im [Beispiel für UWP-Farbe](#uwp-color-sample).</span><span class="sxs-lookup"><span data-stu-id="c1179-754">An example of this is shown in [UWP color sample](#uwp-color-sample).</span></span>

## <a name="summary"></a><span data-ttu-id="c1179-755">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="c1179-755">Summary</span></span>

<span data-ttu-id="c1179-756">Beim Entwerfen für die 10 Fuß-Erfahrung müssen einige besondere Punkte berücksichtigt werden, die sich vom Entwerfen für andere Plattformen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="c1179-756">Designing for the 10-foot experience has special considerations to take into account that make it different from designing for any other platform.</span></span> <span data-ttu-id="c1179-757">Sie können durchaus Ihre UWP-App einfach zu Xbox One portieren, dies funktioniert. Die App wird jedoch nicht unbedingt für die 10-Fuß-Erfahrung optimiert und kann für den Benutzer mit Frustration verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="c1179-757">While you can certainly do a straight port of your UWP app to Xbox One and it will work, it won't necessarily be optimized for the 10-foot experience and can lead to user frustration.</span></span> <span data-ttu-id="c1179-758">Wenn Sie die Richtlinien in diesem Artikel befolgen, stellen Sie so sicher, dass Ihre App genauso gut auf Fernsehgeräten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c1179-758">Following the guidelines in this article will make sure that your app is as good as it can be on TV.</span></span>

## <a name="related-articles"></a><span data-ttu-id="c1179-759">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c1179-759">Related articles</span></span>

- [<span data-ttu-id="c1179-760">Einführung der Geräte für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="c1179-760">Device primer for Universal Windows Platform (UWP) apps</span></span>](device-primer.md)
- [<span data-ttu-id="c1179-761">Interaktionen mit Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="c1179-761">Gamepad and remote control interactions</span></span>](gamepad-and-remote-interactions.md)
- [<span data-ttu-id="c1179-762">Sound in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="c1179-762">Sound in UWP apps</span></span>](../style/sound.md)
