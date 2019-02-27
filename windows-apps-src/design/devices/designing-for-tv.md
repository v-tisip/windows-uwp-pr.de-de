---
Description: Design your app so that it looks good and functions well on your television.
title: Entwerfen für Xbox und Fernsehgeräte
ms.assetid: 780209cb-3e8a-4cf7-8f80-8b8f449580bf
label: Designing for Xbox and TV
template: detail.hbs
isNew: true
keywords: Xbox, TV, 10-Fuß-Erfahrung, Gamepad, Fernbedienung, Eingabe, Interaktion
ms.date: 11/13/2018
ms.topic: article
pm-contact: chigy
design-contact: jeffarn
dev-contact: niallm
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 788f47c1b29766cae1f437992aee8414580f3935
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9116492"
---
# <a name="designing-for-xbox-and-tv"></a><span data-ttu-id="10dab-103">Entwerfen für Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="10dab-103">Designing for Xbox and TV</span></span>

<span data-ttu-id="10dab-104">Entwerfen Sie Ihre App für die Universelle Windows-Plattform (UWP) so, dass sie auf Xbox One- und Fernsehbildschirmen gut aussieht und optimal funktioniert.</span><span class="sxs-lookup"><span data-stu-id="10dab-104">Design your Universal Windows Platform (UWP) app so that it looks good and functions well on Xbox One and television screens.</span></span>

<span data-ttu-id="10dab-105">Hinweise zur interaktionserfahrungen in UWP-Anwendungen in der *10-Fuß* -Erfahrung finden Sie unter [Interaktionen mit Gamepad und Fernbedienung zu erhalten](../input/gamepad-and-remote-interactions.md) .</span><span class="sxs-lookup"><span data-stu-id="10dab-105">See [Gamepad and remote control interactions](../input/gamepad-and-remote-interactions.md) for guidance on interaction experiences in UWP applications in the *10-foot* experience.</span></span>

## <a name="overview"></a><span data-ttu-id="10dab-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="10dab-106">Overview</span></span>

<span data-ttu-id="10dab-107">Dank der universellen Windows-Plattform können Sie großartige Benutzeroberflächen für verschiedene Windows10-Geräte erstellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-107">The Universal Windows Platform lets you create delightful experiences across multiple Windows 10 devices.</span></span>
<span data-ttu-id="10dab-108">Die Mehrzahl der durch das UWP Framework bereitgestellten Funktionen ermöglichen Apps, auf diesen Geräten ohne zusätzlichen Aufwand die gleiche Benutzeroberfläche (UI) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="10dab-108">Most of the functionality provided by the UWP framework enables apps to use the same user interface (UI) across these devices, without additional work.</span></span>
<span data-ttu-id="10dab-109">Das Anpassen und Optimieren Ihrer App an Xbox One- und Fernsehbildschirme erfordert jedoch besondere Überlegungen.</span><span class="sxs-lookup"><span data-stu-id="10dab-109">However, tailoring and optimizing your app to work great on Xbox One and TV screens requires special considerations.</span></span>

<span data-ttu-id="10dab-110">Die Erfahrung, die Sie machen, wenn Sie auf dem Sofa sitzen und mittels eines Gamepads oder einer Fernbedienung mit Ihrem Fernsehgerät interagieren, wird als **3-Meter-Erfahrung** (10-Fuß-Erfahrung) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="10dab-110">The experience of sitting on your couch across the room, using a gamepad or remote to interact with your TV, is called the **10-foot experience**.</span></span>
<span data-ttu-id="10dab-111">Der Name kommt daher, dass sich der Benutzer im Allgemeinen ungefähr 3Meter (10Fuß) vom Bildschirm entfernt befindet.</span><span class="sxs-lookup"><span data-stu-id="10dab-111">It is so named because the user is generally sitting approximately 10 feet away from the screen.</span></span>
<span data-ttu-id="10dab-112">Dies stellt eine besondere Herausforderung dar, die beispielsweise bei einer *50-cm-Erfahrung* (2-Fuß-Erfahrung) oder bei der Interaktion mit einem PC nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-112">This provides unique challenges that aren't present in, say, the *2-foot* experience, or interacting with a PC.</span></span>
<span data-ttu-id="10dab-113">Wenn Sie eine App für Xbox One oder ein anderes Gerät entwickeln, das Inhalte auf einem Fernsehbildschirm ausgibt und eine Steuerung verwendet, sollten Sie dies stets bedenken.</span><span class="sxs-lookup"><span data-stu-id="10dab-113">If you are developing an app for Xbox One or any other device that outputs to the TV screen and uses a controller for input, you should always keep this in mind.</span></span>

<span data-ttu-id="10dab-114">Nicht alle Schritte in diesem Artikel sind erforderlich, damit Ihre App gut in 10 Fuß-Umgebungen funktioniert. Wenn Sie diese jedoch kennen und für Ihre App die entsprechenden Entscheidungen treffen, führt dies zu einer besseren 10-Fuß-Erfahrung, die an die spezifischen Anforderungen Ihrer App angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-114">Not all of the steps in this article are required to make your app work well for 10-foot experiences, but understanding them and making the appropriate decisions for your app will result in a better 10-foot experience tailored for your app's specific needs.</span></span>
<span data-ttu-id="10dab-115">Berücksichtigen Sie die folgenden Designrichtlinien, wenn Sie eine App für eine 10-Fuß-Umgebung entwickeln.</span><span class="sxs-lookup"><span data-stu-id="10dab-115">As you bring your app to life in the 10-foot environment, consider the following design principles.</span></span>

### <a name="simple"></a><span data-ttu-id="10dab-116">Einfach</span><span class="sxs-lookup"><span data-stu-id="10dab-116">Simple</span></span>

<span data-ttu-id="10dab-117">Ein Entwurf für eine 10-Fuß-Umgebung bedeutet einen einzigartigen Satz von Herausforderungen.</span><span class="sxs-lookup"><span data-stu-id="10dab-117">Designing for the 10-foot environment presents a unique set of challenges.</span></span> <span data-ttu-id="10dab-118">Auflösung und Anzeigeabstand kann es Menschen schwer machen, zu viele Informationen zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="10dab-118">Resolution and viewing distance can make it difficult for people to process too much information.</span></span>
<span data-ttu-id="10dab-119">Versuchen Sie, Ihr Design klar zu halten und auf die einfachsten Komponenten zu reduzieren, die möglich sind.</span><span class="sxs-lookup"><span data-stu-id="10dab-119">Try to keep your design clean, reduced to the simplest possible components.</span></span> <span data-ttu-id="10dab-120">Die Menge der auf einem Fernseher angezeigten Informationen sollte mit der vergleichbar sein, die Ihnen auf einem Mobiltelefon angezeigt werden, nicht auf einem Desktop.</span><span class="sxs-lookup"><span data-stu-id="10dab-120">The amount of information displayed on a TV should be comparable to what you'd see on a mobile phone, rather than on a desktop.</span></span>

![Xbox One-Startseite](images/designing-for-tv/xbox-home-screen.png)

### <a name="coherent"></a><span data-ttu-id="10dab-122">Einheitlich</span><span class="sxs-lookup"><span data-stu-id="10dab-122">Coherent</span></span>

<span data-ttu-id="10dab-123">UWP-Apps in 10-Fuß-Umgebungen sollten intuitiv und benutzerfreundlich sein.</span><span class="sxs-lookup"><span data-stu-id="10dab-123">UWP apps in the 10-foot environment should be intuitive and easy to use.</span></span> <span data-ttu-id="10dab-124">Sorgen Sie für einen klaren und unverkennbaren Fokus.</span><span class="sxs-lookup"><span data-stu-id="10dab-124">Make the focus clear and unmistakable.</span></span>
<span data-ttu-id="10dab-125">Ordnen Sie Inhalte so an, dass Verschiebungen auf dem Bildschirm konsistent und vorhersagbar sind.</span><span class="sxs-lookup"><span data-stu-id="10dab-125">Arrange content so that movement across the space is consistent and predictable.</span></span> <span data-ttu-id="10dab-126">Stellen Sie Menschen den kürzesten Weg zu dem bereit, was sie tun möchten.</span><span class="sxs-lookup"><span data-stu-id="10dab-126">Give people the shortest path to what they want to do.</span></span>

![Xbox One-Film-App](images/designing-for-tv/xbox-movies-app.png)

_**<span data-ttu-id="10dab-128">Alle im Screenshot gezeigten Filme sind auf Microsoft Filme & TV verfügbar.</span><span class="sxs-lookup"><span data-stu-id="10dab-128">All movies shown in the screenshot are available on Microsoft Movies & TV.</span></span>**_  

### <a name="captivating"></a><span data-ttu-id="10dab-129">Fesselnd</span><span class="sxs-lookup"><span data-stu-id="10dab-129">Captivating</span></span>

<span data-ttu-id="10dab-130">Der große Bildschirm bietet äußerst faszinierende Erfahrungen, ähnlich wie ein Kino.</span><span class="sxs-lookup"><span data-stu-id="10dab-130">The most immersive, cinematic experiences take place on the big screen.</span></span> <span data-ttu-id="10dab-131">Rand-Rand-Design, elegante Bewegungen und brillante Farben und Typografien eröffnen Ihren Apps neue Dimensionen.</span><span class="sxs-lookup"><span data-stu-id="10dab-131">Edge-to-edge scenery, elegant motion, and vibrant use of color and typography take your apps to the next level.</span></span> <span data-ttu-id="10dab-132">Seien Sie mutig, und bieten Sie ein ansprechendes Design.</span><span class="sxs-lookup"><span data-stu-id="10dab-132">Be bold and beautiful.</span></span>

![Xbox One Avatar-App](images/designing-for-tv/xbox-avatar-app.png)

### <a name="optimizations-for-the-10-foot-experience"></a><span data-ttu-id="10dab-134">Optimierungen für die 10-Fuß-Erfahrung</span><span class="sxs-lookup"><span data-stu-id="10dab-134">Optimizations for the 10-foot experience</span></span>

<span data-ttu-id="10dab-135">Da Sie nun mit den Grundsätzen eines guten UWP-App-Designs für die 10-Fuß-Erfahrung vertraut sind, lesen Sie die folgenden Übersicht über die verschiedenen Arten, wie Sie Ihre App optimieren und eine hervorragende Benutzerumgebung bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="10dab-135">Now that you know the principles of good UWP app design for the 10-foot experience, read through the following overview of the specific ways you can optimize your app and make for a great user experience.</span></span>

| <span data-ttu-id="10dab-136">Feature</span><span class="sxs-lookup"><span data-stu-id="10dab-136">Feature</span></span>        | <span data-ttu-id="10dab-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="10dab-137">Description</span></span>           |
| -------------------------------------------------------------- |--------------------------------|
| [<span data-ttu-id="10dab-138">Anpassen von Benutzeroberflächenelementen</span><span class="sxs-lookup"><span data-stu-id="10dab-138">UI element sizing</span></span>](#ui-element-sizing)  | <span data-ttu-id="10dab-139">Die Universelle Windows-Plattform verwendet [Skalierung und effektive Pixel](../basics/design-and-ui-intro.md#effective-pixels-and-scaling), um die Benutzeroberfläche gemäß dem Anzeigeabstand zu skalieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-139">The Universal Windows Platform uses [scaling and effective pixels](../basics/design-and-ui-intro.md#effective-pixels-and-scaling) to scale the UI according to the viewing distance.</span></span> <span data-ttu-id="10dab-140">Wenn Sie verstehen, wie Sie Größen anpassen und auf Ihre Benutzeroberfläche anwenden, hilft Ihnen dies, Ihre App für die 10-Fuß-Umgebung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-140">Understanding sizing and applying it across your UI will help optimize your app for the 10-foot environment.</span></span>  |
|  [<span data-ttu-id="10dab-141">Fernsehsicherer Bereich</span><span class="sxs-lookup"><span data-stu-id="10dab-141">TV-safe area</span></span>](#tv-safe-area) | <span data-ttu-id="10dab-142">Die UWP vermeidet automatisch und standardmäßig die Anzeige von Benutzeroberflächenelementen in nicht fernsehsicheren Bereichen (nahe dem Bildschirmrand).</span><span class="sxs-lookup"><span data-stu-id="10dab-142">The UWP will automatically avoid displaying any UI in TV-unsafe areas (areas close to the edges of the screen) by default.</span></span> <span data-ttu-id="10dab-143">Dies führt jedoch zu einem „Schachteleffekt“, so dass die Benutzeroberfläche einem Briefkastenschlitz ähnelt.</span><span class="sxs-lookup"><span data-stu-id="10dab-143">However, this creates a "boxed-in" effect in which the UI looks letterboxed.</span></span> <span data-ttu-id="10dab-144">Damit Ihre App auf Fernsehgeräten wirklich immersiv ist, müssen Sie diese so anpassen, dass sie sich auf Fernsehgeräten, die dies unterstützen, bis zu den Rändern erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-144">For your app to be truly immersive on TV, you will want to modify it so that it extends to the edges of the screen on TVs that support it.</span></span> |
| [<span data-ttu-id="10dab-145">Farben</span><span class="sxs-lookup"><span data-stu-id="10dab-145">Colors</span></span>](#colors)  |  <span data-ttu-id="10dab-146">Die UWP unterstützt Farbdesigns. Daher wird eine App, die das Systemdesign berücksichtigt, auf Xbox One standardmäßig auf **dark** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="10dab-146">The UWP supports color themes, and an app that respects the system theme will default to **dark** on Xbox One.</span></span> <span data-ttu-id="10dab-147">Wenn Ihre App ein bestimmtes Farbdesign verwendet, sollten Sie daran denken, dass sich einige Farben nicht gut für Fernsehbildschirme eignen und daher vermieden werden sollten.</span><span class="sxs-lookup"><span data-stu-id="10dab-147">If your app has a specific color theme, you should consider that some colors don't work well for TV and should be avoided.</span></span> |
| [<span data-ttu-id="10dab-148">Sound</span><span class="sxs-lookup"><span data-stu-id="10dab-148">Sound</span></span>](../style/sound.md)    | <span data-ttu-id="10dab-149">Sounds spielen bei der 10 Fuß-Erfahrung eine wichtige Rolle. Sie helfen den Benutzern sich zu vertiefen und liefern Feedback.</span><span class="sxs-lookup"><span data-stu-id="10dab-149">Sounds play a key role in the 10-foot experience, helping to immerse and give feedback to the user.</span></span> <span data-ttu-id="10dab-150">Die UWP bietet Funktionen, mit denen Sounds für allgemeine Steuerelemente automatisch aktiviert werden, wenn die App auf Xbox One ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-150">The UWP provides functionality that automatically turns on sounds for common controls when the app is running on Xbox One.</span></span> <span data-ttu-id="10dab-151">Erfahren Sie mehr über die in der Universellen Windows-Plattform integrierte Unterstützung von Sound, und erfahren Sie, wie Sie davon profitieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-151">Find out more about the sound support built into the UWP and learn how to take advantage of it.</span></span>    |
| [<span data-ttu-id="10dab-152">Richtlinien für Benutzeroberflächensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="10dab-152">Guidelines for UI controls</span></span>](#guidelines-for-ui-controls)  |  <span data-ttu-id="10dab-153">Es gibt mehrere Benutzeroberflächen-Steuerelemente, die auf mehreren Geräten gut funktionieren. Wenn diese jedoch auf Fernsehgeräten verwendet werden, müssen bestimmte Aspekte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-153">There are several UI controls that work well across multiple devices, but have certain considerations when used on TV.</span></span> <span data-ttu-id="10dab-154">Informieren Sie sich über einige bewährte Methoden für die Verwendung dieser Steuerelemente beim Entwerfen für die 10 Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="10dab-154">Read about some best practices for using these controls when designing for the 10-foot experience.</span></span> |
| [<span data-ttu-id="10dab-155">Benutzerdefinierter visueller Zustandsauslöser für Xbox</span><span class="sxs-lookup"><span data-stu-id="10dab-155">Custom visual state trigger for Xbox</span></span>](#custom-visual-state-trigger-for-xbox) | <span data-ttu-id="10dab-156">Um Ihre UWP-App an die 10-Fuß-Erfahrung anzupassen, empfehlen wir Ihnen, einen benutzerdefinierten *visuellen Zustandsauslöser* zu verwenden, um das Layout zu ändern, wenn die App erkennt, dass sie auf einer Xbox-Konsole gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="10dab-156">To tailor your UWP app for the 10-foot experience, we recommend that you use a custom *visual state trigger* to make layout changes when the app detects that it has been launched on an Xbox console.</span></span> |

<span data-ttu-id="10dab-157">Zusätzlich zu den vorherigen Entwurf und Layout Aspekte gibt es eine Reihe von [Gamepad und Fernbedienung Interaktion](../input/gamepad-and-remote-interactions.md) Optimierungen, die Sie berücksichtigen sollten, wenn Sie Ihre app zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-157">In addition to the preceding design and layout considerations, there are a number of [gamepad and remote control interaction](../input/gamepad-and-remote-interactions.md) optimizations you should consider when building your app.</span></span>

| <span data-ttu-id="10dab-158">Feature</span><span class="sxs-lookup"><span data-stu-id="10dab-158">Feature</span></span>        | <span data-ttu-id="10dab-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="10dab-159">Description</span></span>           |
| -------------------------------------------------------------- |--------------------------------|
| [<span data-ttu-id="10dab-160">XY-Fokusnavigation und -interaktion</span><span class="sxs-lookup"><span data-stu-id="10dab-160">XY focus navigation and interaction</span></span>](../input/gamepad-and-remote-interactions.md#xy-focus-navigation-and-interaction) | <span data-ttu-id="10dab-161">**XY-Fokusnavigation** können die Benutzer auf Benutzeroberfläches Ihrer app navigieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-161">**XY focus navigation** enables the user to navigate around your app's UI.</span></span> <span data-ttu-id="10dab-162">Dies begrenzt Benutzer jedoch auf eine Navigation nach oben, unten, links und rechts.</span><span class="sxs-lookup"><span data-stu-id="10dab-162">However, this limits the user to navigating up, down, left, and right.</span></span> <span data-ttu-id="10dab-163">In diesem Abschnitt finden Sie Empfehlungen für den Umgang mit diesen und anderen Überlegungen.</span><span class="sxs-lookup"><span data-stu-id="10dab-163">Recommendations for dealing with this and other considerations are outlined in this section.</span></span> |
| [<span data-ttu-id="10dab-164">Mausmodus</span><span class="sxs-lookup"><span data-stu-id="10dab-164">Mouse mode</span></span>](../input/gamepad-and-remote-interactions.md#mouse-mode)|<span data-ttu-id="10dab-165">XY-Fokusnavigation ist nicht praktisch, oder auch möglich, für einige Arten von Anwendungen, z. B. Karten oder Zeichnen und Zeichnen von apps.</span><span class="sxs-lookup"><span data-stu-id="10dab-165">XY focus navigation isn't practical, or even possible, for some types of applications, such as maps or drawing and painting apps.</span></span> <span data-ttu-id="10dab-166">In diesen Fällen können **mausmodus** Benutzer, die mit einem Gamepad oder Fernbedienung zu erhalten, wie eine Maus auf einem PC frei navigieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-166">In these cases, **mouse mode** lets users navigate freely with a gamepad or remote control, just like a mouse on a PC.</span></span>|
| [<span data-ttu-id="10dab-167">Fokusanzeige</span><span class="sxs-lookup"><span data-stu-id="10dab-167">Focus visual</span></span>](../input/gamepad-and-remote-interactions.md#focus-visual)  | <span data-ttu-id="10dab-168">Die Fokusanzeige ist ein Rahmen, der das aktuell fokussierte Element der Benutzeroberfläche hervorhebt.</span><span class="sxs-lookup"><span data-stu-id="10dab-168">The focus visual is a border that highlights the currently focused UI element.</span></span> <span data-ttu-id="10dab-169">Dadurch wird den Benutzer die Benutzeroberfläche schnell zu erkennen, sie zu navigieren oder interagieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-169">This helps the user quickly identify the UI they are navigating through or interacting with.</span></span>  |
| [<span data-ttu-id="10dab-170">Fokusaktivierung</span><span class="sxs-lookup"><span data-stu-id="10dab-170">Focus engagement</span></span>](../input/gamepad-and-remote-interactions.md#focus-engagement) | <span data-ttu-id="10dab-171">Fokusaktivierung erfordert, dass den Benutzer, drücken die Schaltfläche " **A" oder "Select** " auf einem Gamepad oder Fernbedienung zu erhalten, wenn ein UI-Element den Fokus hat, um mit ihm zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-171">Focus engagement requires the user to press the **A/Select** button on a gamepad or remote control when a UI element has focus in order to interact with it.</span></span> |
| [<span data-ttu-id="10dab-172">Hardwaretasten</span><span class="sxs-lookup"><span data-stu-id="10dab-172">Hardware buttons</span></span>](../input/gamepad-and-remote-interactions.md#hardware-buttons) | <span data-ttu-id="10dab-173">Bieten das Gamepad und Fernbedienung unterscheiden sich Tasten und Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="10dab-173">The gamepad and remote control provide very different buttons and configurations.</span></span> |

> [!NOTE]
> <span data-ttu-id="10dab-174">Die meisten Codeausschnitte in diesem Thema wurden in XAML/C# verfasst. Die Grundsätze und Konzepte gelten jedoch für alle UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="10dab-174">Most of the code snippets in this topic are in XAML/C#; however, the principles and concepts apply to all UWP apps.</span></span> <span data-ttu-id="10dab-175">Wenn Sie eine HTML/JavaScript-UWP-App für Xbox entwickeln, steht Ihnen die hervorragende [TVHelpers](https://github.com/Microsoft/TVHelpers/wiki)-Bibliothek auf GitHub zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="10dab-175">If you're developing an HTML/JavaScript UWP app for Xbox, check out the excellent [TVHelpers](https://github.com/Microsoft/TVHelpers/wiki) library on GitHub.</span></span>

## <a name="ui-element-sizing"></a><span data-ttu-id="10dab-176">Anpassen von Benutzeroberflächenelementen</span><span class="sxs-lookup"><span data-stu-id="10dab-176">UI element sizing</span></span>

<span data-ttu-id="10dab-177">Da Benutzer von Apps in 10-Fuß-Umgebungen Fernbedienungen oder Gamepads verwenden und sich mehrere Meter vom Bildschirm entfernt befinden, gibt es einige Überlegungen in Bezug auf die Benutzeroberfläche, die Sie für Ihren Entwurf berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="10dab-177">Because the user of an app in the 10-foot environment is using a remote control or gamepad and is sitting several feet away from the screen, there are some UI considerations that need to be factored into your design.</span></span>
<span data-ttu-id="10dab-178">Stellen Sie sicher, dass die Benutzeroberfläche über eine geeignete Inhaltsdichte verfügt und nicht zu überladen ist, damit Benutzer einfach navigieren und Elemente auswählen können.</span><span class="sxs-lookup"><span data-stu-id="10dab-178">Make sure that the UI has an appropriate content density and is not too cluttered so that the user can easily navigate and select elements.</span></span> <span data-ttu-id="10dab-179">Denken Sie daran: Einfachheit ist der Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="10dab-179">Remember: simplicity is key.</span></span>

### <a name="scale-factor-and-adaptive-layout"></a><span data-ttu-id="10dab-180">Skalierungsfaktor und adaptives Layout</span><span class="sxs-lookup"><span data-stu-id="10dab-180">Scale factor and adaptive layout</span></span>

<span data-ttu-id="10dab-181">Der **Skalierungsfaktor** trägt dazu bei, dass Benutzeroberflächenelemente in der richtigen Größe für das Gerät angezeigt werden, auf dem die App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-181">**Scale factor** helps with ensuring that UI elements are displayed with the right sizing for the device on which the app is running.</span></span>
<span data-ttu-id="10dab-182">Auf Desktops befindet sich diese Einstellung in **Einstellungen > System > Anzeige** als gleitender Wert.</span><span class="sxs-lookup"><span data-stu-id="10dab-182">On desktop, this setting can be found in **Settings > System > Display** as a sliding value.</span></span>
<span data-ttu-id="10dab-183">Diese Einstellung ist auch auf Mobiltelefonen vorhanden, wenn das Gerät diese unterstützt.</span><span class="sxs-lookup"><span data-stu-id="10dab-183">This same setting exists on phone as well if the device supports it.</span></span>

![Ändern der Größe von Text, Apps und anderen Elementen](images/designing-for-tv/ui-scaling.png)

<span data-ttu-id="10dab-185">Auf Xbox One gibt es diese Systemeinstellung nicht. UWP-UI-Elemente, die für Fernsehgeräte angepasst werden, werden jedoch standardmäßig auf **200%** für XAML-Apps und **150%** für HTML-Apps skaliert.</span><span class="sxs-lookup"><span data-stu-id="10dab-185">On Xbox One, there is no such system setting; however, for UWP UI elements to be sized appropriately for TV, they are scaled at a default of **200%** for XAML apps and **150%** for HTML apps.</span></span>
<span data-ttu-id="10dab-186">Solange Benutzeroberflächenelemente für andere Geräte korrekt angepasst werden, werden sie auch für Fernsehgeräte angepasst.</span><span class="sxs-lookup"><span data-stu-id="10dab-186">As long as UI elements are appropriately sized for other devices, they will be appropriately sized for TV.</span></span>
<span data-ttu-id="10dab-187">Xbox One rendert Ihre App mit 1080p (1920 x 1080 Pixel).</span><span class="sxs-lookup"><span data-stu-id="10dab-187">Xbox One renders your app at 1080p (1920 x 1080 pixels).</span></span> <span data-ttu-id="10dab-188">Stellen Sie daher mittels [adaptiver Techniken](../layout/screen-sizes-and-breakpoints-for-responsive-design.md) sicher, dass die UI bei 960x540px und einer Skalierung von 100% (oder bei 1280x720px und einer Skalierung von 100% für HTML-Apps) gut aussieht, wenn Sie eine App von anderen Geräten wie PCs übertragen.</span><span class="sxs-lookup"><span data-stu-id="10dab-188">Therefore, when bringing an app from other devices such as PC, ensure that the UI looks great at 960 x 540 px at 100% scale (or 1280 x 720 px at 100% scale for HTML apps) utilizing [adaptive techniques](../layout/screen-sizes-and-breakpoints-for-responsive-design.md).</span></span>

<span data-ttu-id="10dab-189">Das Entwerfen für Xbox unterscheidet sich etwas vom Entwerfen für PCs, da Sie lediglich eine Auflösung von 1920x1080 berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="10dab-189">Designing for Xbox is a little different from designing for PC because you only need to worry about one resolution, 1920 x 1080.</span></span>
<span data-ttu-id="10dab-190">Es spielt keine Rolle, ob der Benutzer ein Fernsehgerät mit einer besseren Auflösung besitzt&mdash;UWP-Apps werden stets auf 1080p skaliert.</span><span class="sxs-lookup"><span data-stu-id="10dab-190">It doesn't matter if the user has a TV that has better resolution&mdash;UWP apps will always scale to 1080p.</span></span>

<span data-ttu-id="10dab-191">Bei der Ausführung auf Xbox One werden darüber hinaus korrekte Ressourcengrößen aus dem Satz mit 200% (oder 150% für HTML-Apps) für Ihre App aufgerufen, unabhängig von der Auflösung des Fernsehgeräts.</span><span class="sxs-lookup"><span data-stu-id="10dab-191">Correct asset sizes from the 200% (or 150% for HTML apps) set will also be pulled in for your app when running on Xbox One, regardless of TV resolution.</span></span>

### <a name="content-density"></a><span data-ttu-id="10dab-192">Inhaltsdichte</span><span class="sxs-lookup"><span data-stu-id="10dab-192">Content density</span></span>

<span data-ttu-id="10dab-193">Denken Sie beim Entwerfen Ihrer App daran, dass Benutzer die Benutzeroberfläche aus der Entfernung sieht und mittels einer Fernbedienung oder einem Gamecontroller mit dieser interagiert. Dies dauert länger als die Verwendung von Maus- oder Toucheingaben.</span><span class="sxs-lookup"><span data-stu-id="10dab-193">When designing your app, remember that the user will be viewing the UI from a distance and interacting with it by using a remote or game controller, which takes more time to navigate than using mouse or touch input.</span></span>

#### <a name="sizes-of-ui-controls"></a><span data-ttu-id="10dab-194">Größen von Benutzeroberflächensteuerelementen</span><span class="sxs-lookup"><span data-stu-id="10dab-194">Sizes of UI controls</span></span>

<span data-ttu-id="10dab-195">Interaktive Benutzeroberflächenelemente sollten eine Mindesthöhe von 32epx (effektive Pixel) besitzen.</span><span class="sxs-lookup"><span data-stu-id="10dab-195">Interactive UI elements should be sized at a minimum height of 32 epx (effective pixels).</span></span> <span data-ttu-id="10dab-196">Dies ist die Standardeinstellung für allgemeine UWP-Steuerelemente. Wenn diese bei einer Skalierung von 200% verwendet wird, ist sichergestellt, dass Benutzeroberflächenelemente aus der Entfernung erkennbar sind. Darüber hinaus trägt dies zur Reduzierung der Inhaltsdichte bei.</span><span class="sxs-lookup"><span data-stu-id="10dab-196">This is the default for common UWP controls, and when used at 200% scale, it ensures that UI elements are visible from a distance and helps reduce content density.</span></span>

![UWP-Schaltfläche bei einer Skalierung von 100% und 200%](images/designing-for-tv/button-100-200.png)

#### <a name="number-of-clicks"></a><span data-ttu-id="10dab-198">Anzahl der Klicks</span><span class="sxs-lookup"><span data-stu-id="10dab-198">Number of clicks</span></span>

<span data-ttu-id="10dab-199">Um Ihre Benutzeroberfläche zu vereinfachen, sollten Benutzer nicht mehr als **sechs Klicks** benötigen, wenn sie von einem Rand des Fernsehbildschirms zum anderen navigieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-199">When the user is navigating from one edge of the TV screen to the other, it should take no more than **six clicks** to simplify your UI.</span></span> <span data-ttu-id="10dab-200">Auch hier gilt der Grundsatz der **Einfachheit**.</span><span class="sxs-lookup"><span data-stu-id="10dab-200">Again, the principle of **simplicity** applies here.</span></span> <span data-ttu-id="10dab-201">Weitere Informationen finden Sie unter [Pfad der wenigsten Klicks](#path-of-least-clicks).</span><span class="sxs-lookup"><span data-stu-id="10dab-201">For more details, see [Path of least clicks](#path-of-least-clicks).</span></span>

![6Symbole insgesamt](images/designing-for-tv/six-clicks.png)

### <a name="text-sizes"></a><span data-ttu-id="10dab-203">Textgrößen</span><span class="sxs-lookup"><span data-stu-id="10dab-203">Text sizes</span></span>

<span data-ttu-id="10dab-204">Wenden Sie die folgenden Faustregeln an, damit Ihre Benutzeroberfläche aus der Entfernung erkennbar ist:</span><span class="sxs-lookup"><span data-stu-id="10dab-204">To make your UI visible from a distance, use the following rules of thumb:</span></span>

* <span data-ttu-id="10dab-205">Haupttext und Lesen von Inhalten: mindestens 15epx</span><span class="sxs-lookup"><span data-stu-id="10dab-205">Main text and reading content: 15 epx minimum</span></span>
* <span data-ttu-id="10dab-206">Nicht kritische Texte und ergänzende Inhalte: mindestens 12epx</span><span class="sxs-lookup"><span data-stu-id="10dab-206">Non-critical text and supplemental content: 12 epx minimum</span></span>

<span data-ttu-id="10dab-207">Wenn Sie in der Benutzeroberfläche einen größeren Text verwenden, sollten Sie eine Größe wählen, die die verfügbare Bildschirmfläche nicht zu sehr begrenzt, indem sie Platz beansprucht, der potenziell von anderen Inhalten ausgefüllt werden kann.</span><span class="sxs-lookup"><span data-stu-id="10dab-207">When using larger text in your UI, pick a size that does not limit screen real estate too much, taking up space that other content could potentially fill.</span></span>

### <a name="opting-out-of-scale-factor"></a><span data-ttu-id="10dab-208">Deaktivieren des Skalierungsfaktors</span><span class="sxs-lookup"><span data-stu-id="10dab-208">Opting out of scale factor</span></span>

<span data-ttu-id="10dab-209">Wir empfehlen Ihnen, für Ihre App die Vorteile der Skalierungsfaktorunterstützung zu nutzen. Dies trägt dazu bei, dass sie auf allen Geräten korrekt ausgeführt wird, indem sie für jeden Gerätetyp skaliert wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-209">We recommend that your app take advantage of scale factor support, which will help it run appropriately on all devices by scaling for each device type.</span></span>
<span data-ttu-id="10dab-210">Es ist jedoch möglich, dieses Verhalten zu deaktivieren und alle Benutzeroberflächenelemente für eine Skalierung von 100 % zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="10dab-210">However, it is possible to opt out of this behavior and design all of your UI at 100% scale.</span></span> <span data-ttu-id="10dab-211">Beachten Sie, dass Sie den Skalierungsfaktor nicht in einen anderen Wert als 100% ändern können.</span><span class="sxs-lookup"><span data-stu-id="10dab-211">Note that you cannot change the scale factor to anything other than 100%.</span></span>

<span data-ttu-id="10dab-212">Sie können den Skalierungsfaktor für HTML-Apps deaktivieren, indem Sie den folgenden Codeausschnitt verwenden:</span><span class="sxs-lookup"><span data-stu-id="10dab-212">For XAML apps, you can opt out of scale factor by using the following code snippet:</span></span>

```csharp
bool result =
    Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);
```

`result` <span data-ttu-id="10dab-213">informiert Sie, ob die Deaktivierung erfolgreich ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="10dab-213">will inform you whether you successfully opted out.</span></span>

<span data-ttu-id="10dab-214">Weitere Informationen, einschließlich HTML/JavaScript-Beispielcode, finden Sie unter [So deaktivieren Sie die Skalierung](../../xbox-apps/disable-scaling.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-214">For more information, including sample code for HTML/JavaScript, see [How to turn off scaling](../../xbox-apps/disable-scaling.md).</span></span>

<span data-ttu-id="10dab-215">Stellen Sie sicher, dass Sie entsprechenden Größen der Benutzeroberflächenelemente berechnen, indem Sie die in diesem Thema genannten *effektiven* Pixelwerte auf die *tatsächlichen* Pixelwerte verdoppeln (oder für HTML-Apps mit 1,5 multiplizieren).</span><span class="sxs-lookup"><span data-stu-id="10dab-215">Please be sure to calculate the appropriate sizes of UI elements by doubling the *effective* pixel values mentioned in this topic to *actual* pixel values (or multiplying by 1.5 for HTML apps).</span></span>

## <a name="tv-safe-area"></a><span data-ttu-id="10dab-216">Fernsehsicherer Bereich</span><span class="sxs-lookup"><span data-stu-id="10dab-216">TV-safe area</span></span>

<span data-ttu-id="10dab-217">Nicht alle Fernsehgeräte zeigen die Inhalte von Rand zu Rand an. Dies hat historische und technische Gründe.</span><span class="sxs-lookup"><span data-stu-id="10dab-217">Not all TVs display content all the way to the edges of the screen due to historical and technological reasons.</span></span> <span data-ttu-id="10dab-218">Standardmäßig vermeidet die UWP die Anzeige von Benutzeroberflächeninhalten in nicht fernsehsicheren Bereichen und zeichnet stattdessen lediglich den Seitenhintergrund.</span><span class="sxs-lookup"><span data-stu-id="10dab-218">By default, the UWP will avoid displaying any UI content in TV-unsafe areas and instead will only draw the page background.</span></span>

<span data-ttu-id="10dab-219">Der nicht fernsehsichere Bereich wird in der folgenden Abbildung durch den blauen Bereich dargestellt.</span><span class="sxs-lookup"><span data-stu-id="10dab-219">The TV-unsafe area is represented by the blue area in the following image.</span></span>

![Nicht fernsehsicherer Bereich](images/designing-for-tv/tv-unsafe-area.png)

<span data-ttu-id="10dab-221">Sie können für den Hintergrund eine statische Farbe, eine Designfarbe oder ein Bild verwenden, wie in den folgenden Codeausschnitten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="10dab-221">You can set the background to a static or themed color, or to an image, as the following code snippets demonstrate.</span></span>

### <a name="theme-color"></a><span data-ttu-id="10dab-222">Designfarbe</span><span class="sxs-lookup"><span data-stu-id="10dab-222">Theme color</span></span>

```xml
<Page x:Class="Sample.MainPage"
      Background="{ThemeResource ApplicationPageBackgroundThemeBrush}"/>
```

### <a name="image"></a><span data-ttu-id="10dab-223">Bild</span><span class="sxs-lookup"><span data-stu-id="10dab-223">Image</span></span>

```xml
<Page x:Class="Sample.MainPage"
      Background="\Assets\Background.png"/>
```

<span data-ttu-id="10dab-224">So sieht Ihre App ohne zusätzlichen Aufwand aus.</span><span class="sxs-lookup"><span data-stu-id="10dab-224">This is what your app will look like without additional work.</span></span>

![Fernsehsicherer Bereich](images/designing-for-tv/tv-safe-area.png)

<span data-ttu-id="10dab-226">Dies ist nicht optimal, da dies der App einen „Schachteleffekt“ verleiht. Teile der Benutzeroberfläche werden scheinbar abgeschnitten, beispielsweise der Navigationsbereich und das Raster.</span><span class="sxs-lookup"><span data-stu-id="10dab-226">This is not optimal because it gives the app a "boxed-in" effect, with parts of the UI such as the nav pane and grid seemingly cut off.</span></span> <span data-ttu-id="10dab-227">Sie können jedoch Optimierungen durchführen, um Teile der Benutzeroberfläche bis an die Ränder des Bildschirms zu erweitern, um der App einen kinofilmähnlicheren Effekt zu verleihen.</span><span class="sxs-lookup"><span data-stu-id="10dab-227">However, you can make optimizations to extend parts of the UI to the edges of the screen to give the app a more cinematic effect.</span></span>

### <a name="drawing-ui-to-the-edge"></a><span data-ttu-id="10dab-228">Zeichnen der Benutzeroberfläche bis zum Rand</span><span class="sxs-lookup"><span data-stu-id="10dab-228">Drawing UI to the edge</span></span>

<span data-ttu-id="10dab-229">Wir empfehlen Ihnen, bestimmte Benutzeroberflächenelemente zu verwenden, um die Benutzeroberfläche bis an die Ränder des Bildschirms zu erweitern und Benutzern eine immersivere Umgebung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="10dab-229">We recommend that you use certain UI elements to extend to the edges of the screen to provide more immersion to the user.</span></span> <span data-ttu-id="10dab-230">Dazu gehören [ScrollViewers](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer), [Navigationsbereiche](../controls-and-patterns/navigationview.md) und [CommandBars](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar).</span><span class="sxs-lookup"><span data-stu-id="10dab-230">These include [ScrollViewers](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ScrollViewer), [nav panes](../controls-and-patterns/navigationview.md), and [CommandBars](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar).</span></span>

<span data-ttu-id="10dab-231">Es ist jedoch auch wichtig, dass interaktive Elemente und Texte stets die Bildschirmränder vermeiden, um sicherzustellen, dass sie auf bestimmten Fernsehgeräten nicht abgeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-231">On the other hand, it's also important that interactive elements and text always avoid the screen edges to ensure that they won't be cut off on some TVs.</span></span> <span data-ttu-id="10dab-232">Wir empfehlen Ihnen, nur nicht essentielle visuelle Elemente bis zu 5% von den Rändern des Bildschirms entfernt zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="10dab-232">We recommend that you draw only non-essential visuals within 5% of the screen edges.</span></span> <span data-ttu-id="10dab-233">Wie in [Anpassen von Benutzeroberflächenelementen](#ui-element-sizing) bereits erwähnt, nutzt eine UWP-App, die den Xbox One-Standardskalierungsfaktor von 200% verwendet, einen Bereich von 960 x 540epx. Sie sollten es daher vermeiden, in der Benutzeroberfläche Ihrer App essentielle Benutzerflächenelemente in den folgenden Bereichen zu platzieren:</span><span class="sxs-lookup"><span data-stu-id="10dab-233">As mentioned in [UI element sizing](#ui-element-sizing), a UWP app following the Xbox One console's default scale factor of 200% will utilize an area of 960 x 540 epx, so in your app's UI, you should avoid putting essential UI in the following areas:</span></span>

- <span data-ttu-id="10dab-234">27epx vom oberen und unteren Rand</span><span class="sxs-lookup"><span data-stu-id="10dab-234">27 epx from the top and bottom</span></span>
- <span data-ttu-id="10dab-235">48epx vom linken und rechten Rand</span><span class="sxs-lookup"><span data-stu-id="10dab-235">48 epx from the left and right sides</span></span>

<span data-ttu-id="10dab-236">In den folgenden Abschnitten wird beschrieben, wie Sie Ihr UI bis an die Ränder des Bildschirms erweitern.</span><span class="sxs-lookup"><span data-stu-id="10dab-236">The following sections describe how to make your UI extend to the screen edges.</span></span>

#### <a name="core-window-bounds"></a><span data-ttu-id="10dab-237">Kernfenstergrenzen</span><span class="sxs-lookup"><span data-stu-id="10dab-237">Core window bounds</span></span>

<span data-ttu-id="10dab-238">Im Fall von UWP-Apps, die ausschließlich für die 10-Fuß-Erfahrung entwickelt werden, stellt die Verwendung von Kernfenstergrenzen die einfachere Option dar.</span><span class="sxs-lookup"><span data-stu-id="10dab-238">For UWP apps targeting only the 10-foot experience, using core window bounds is a more straightforward option.</span></span>

<span data-ttu-id="10dab-239">Fügen Sie in der `OnLaunched`-Methode von `App.xaml.cs` den folgenden Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="10dab-239">In the `OnLaunched` method of `App.xaml.cs`, add the following code:</span></span>

```csharp
Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode
    (Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);
```

<span data-ttu-id="10dab-240">Mit dieser Codezeile wird das App-Fenster bis zu den Rändern des Bildschirms erweitert. Daher müssen Sie alle interaktiven und essentiellen Benutzeroberflächenelemente in den bereits beschriebenen fernsehsicheren Bereich verschieben.</span><span class="sxs-lookup"><span data-stu-id="10dab-240">With this line of code, the app window will extend to the edges of the screen, so you will need to move all interactive and essential UI into the TV-safe area described earlier.</span></span> <span data-ttu-id="10dab-241">Kurzlebige Benutzeroberflächenelemente wie Kontextmenüs und geöffnete [Kombinationsfelder](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ComboBox) bleiben automatisch im fernsehsicheren Bereich.</span><span class="sxs-lookup"><span data-stu-id="10dab-241">Transient UI, such as context menus and opened [ComboBoxes](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ComboBox), will automatically remain inside the TV-safe area.</span></span>

![Kernfenstergrenzen](images/designing-for-tv/core-window-bounds.png)

#### <a name="pane-backgrounds"></a><span data-ttu-id="10dab-243">Bereichshintergründe</span><span class="sxs-lookup"><span data-stu-id="10dab-243">Pane backgrounds</span></span>

<span data-ttu-id="10dab-244">Navigationsbereiche werden in der Regel nahe am Rand des Bildschirms dargestellt. Daher sollte sich der Hintergrund in den nicht fernsehsicheren Bereich erstrecken, um hässliche Lücken zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="10dab-244">Navigation panes are typically drawn near the edge of the screen, so the background should extend into the TV-unsafe area so as not to introduce awkward gaps.</span></span> <span data-ttu-id="10dab-245">Hierzu können Sie einfach die Hintergrundfarbe des Navigationsbereichs in der Hintergrundfarbe der App ändern.</span><span class="sxs-lookup"><span data-stu-id="10dab-245">You can do this by simply changing the color of the nav pane's background to the color of the app's background.</span></span>

<span data-ttu-id="10dab-246">Mithilfe der oben beschriebenen Kernfenstergrenzen können Sie Ihr UI an den Rändern des Bildschirms darstellen. Sie sollten dann jedoch positive Ränder für die [SplitView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SplitView)-Inhalte nutzen, um diese innerhalb des fernsehsicheren Bereichs zu halten.</span><span class="sxs-lookup"><span data-stu-id="10dab-246">Using the core window bounds as previously described will allow you to draw your UI to the edges of the screen, but you should then use positive margins on the [SplitView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.SplitView)'s content to keep it within the TV-safe area.</span></span>

![Navigationsbereich bis an die Ränder des Bildschirms erweitert](images/designing-for-tv/tv-safe-areas-2.png)

<span data-ttu-id="10dab-248">Hier wurde der Hintergrund des Navigationsbereichs bis an die Ränder des Bildschirms erweitert, während die Navigationselemente weiterhin im fernsehsicheren Bereich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-248">Here, the nav pane's background has been extended to the edges of the screen, while its navigation items are kept in the TV-safe area.</span></span>
<span data-ttu-id="10dab-249">Der Inhalt des `SplitView`-Elements (in diesem Fall ein Raster mit Elementen) wurde bis an den unteren Rand des Bildschirms erweitert. So sieht es aus, als würde es fortgesetzt und nicht abgeschnitten. Der obere Bereich des Rasters befindet sich nach wie vor im fernsehsicheren Bereich.</span><span class="sxs-lookup"><span data-stu-id="10dab-249">The content of the `SplitView` (in this case, a grid of items) has been extended to the bottom of the screen so that it looks like it continues and isn't cut off, while the top of the grid is still within the TV-safe area.</span></span> <span data-ttu-id="10dab-250">(Weitere Informationen hierzu finden Sie unter [Bildlaufenden von Listen und Rastern](#scrolling-ends-of-lists-and-grids)).</span><span class="sxs-lookup"><span data-stu-id="10dab-250">(Learn more about how to do this in [Scrolling ends of lists and grids](#scrolling-ends-of-lists-and-grids)).</span></span>

<span data-ttu-id="10dab-251">Mit dem folgenden Codeausschnitt wird dieser Effekt erzielt:</span><span class="sxs-lookup"><span data-stu-id="10dab-251">The following code snippet achieves this effect:</span></span>

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

<span data-ttu-id="10dab-252">[CommandBar](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar) ist ein weiteres Beispiel für einen Bereich, der häufig in der Nähe eines oder mehrerer Ränder der App positioniert ist. Daher sollte dessen Hintergrund auf Fernsehbildschirmen bis an die Ränder des Bildschirms erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-252">[CommandBar](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar) is another example of a pane that is commonly positioned near one or more edges of the app, and as such on TV its background should extend to the edges of the screen.</span></span> <span data-ttu-id="10dab-253">In der Regel gibt es auf der rechten Seite die Schaltfläche **Mehr** (dargestellt durch „...“), die weiter im fernsehsicheren Bereich angezeigt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="10dab-253">It also usually contains a **More** button, represented by "..." on the right side, which should remain in the TV-safe area.</span></span> <span data-ttu-id="10dab-254">Im Folgenden finden Sie einige unterschiedliche Strategien, um die gewünschten Interaktionen und visuellen Effekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="10dab-254">The following are a few different strategies to achieve the desired interactions and visual effects.</span></span>

<span data-ttu-id="10dab-255">**Option1**: Festlegen der `CommandBar`-Hintergrundfarbe auf transparent oder auf die Farbe des Seitenhintergrunds:</span><span class="sxs-lookup"><span data-stu-id="10dab-255">**Option 1**: Change the `CommandBar` background color to either transparent or the same color as the page background:</span></span>

```xml
<CommandBar x:Name="topbar"
            Background="{ThemeResource SystemControlBackgroundAltHighBrush}">
            ...
</CommandBar>
```

<span data-ttu-id="10dab-256">Hierdurch sieht die `CommandBar` aus, als ob sie auf dem gleichen Hintergrund wie der Rest der Seite angezeigt wird, sodass sich der Hintergrund nahtlos bis an den Rand des Bildschirms erstreckt.</span><span class="sxs-lookup"><span data-stu-id="10dab-256">Doing this will make the `CommandBar` look like it is on top of the same background as the rest of the page, so the background seamlessly flows to the edge of the screen.</span></span>

<span data-ttu-id="10dab-257">**Option2**: Hinzufügen eines Hintergrundrechtecks, dessen Füllung die gleiche Farbe wie der `CommandBar`-Hintergrund hat und das unter der `CommandBar` und über dem Rest der Seite liegt:</span><span class="sxs-lookup"><span data-stu-id="10dab-257">**Option 2**: Add a background rectangle whose fill is the same color as the `CommandBar` background, and have it lie below the `CommandBar` and across the rest of the page:</span></span>

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
> <span data-ttu-id="10dab-258">Wenn Sie sich für diesen Ansatz entscheiden, sollten Sie berücksichtigen, dass die Schaltfläche **Mehr** wenn notwendig die Höhe der geöffneten `CommandBar` ändert, um die Beschriftungen der `AppBarButton`-Schaltflächen unterhalb der Symbole anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="10dab-258">If using this approach, be aware that the **More** button changes the height of the opened `CommandBar` if necessary, in order to show the labels of the `AppBarButton`s below their icons.</span></span> <span data-ttu-id="10dab-259">Wir empfehlen Ihnen, die Beschriftungen *rechts* neben ihren Symbolen anzuzeigen, um diese Größenanpassung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="10dab-259">We recommend that you move the labels to the *right* of their icons to avoid this resizing.</span></span> <span data-ttu-id="10dab-260">Weitere Informationen finden Sie unter [CommandBar-Beschriftungen](#commandbar-labels).</span><span class="sxs-lookup"><span data-stu-id="10dab-260">For more information, see [CommandBar labels](#commandbar-labels).</span></span>

<span data-ttu-id="10dab-261">Beide Vorgehensweisen gelten auch für die anderen in diesem Abschnitt aufgeführten Arten von Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="10dab-261">Both of these approaches also apply to the other types of controls listed in this section.</span></span>

#### <a name="scrolling-ends-of-lists-and-grids"></a><span data-ttu-id="10dab-262">Bildlaufenden von Listen und Rastern</span><span class="sxs-lookup"><span data-stu-id="10dab-262">Scrolling ends of lists and grids</span></span>

<span data-ttu-id="10dab-263">Meist enthalten Listen und Raster mehr Elemente, als gleichzeitig auf den Bildschirm passen.</span><span class="sxs-lookup"><span data-stu-id="10dab-263">It's common for lists and grids to contain more items than can fit onscreen at the same time.</span></span> <span data-ttu-id="10dab-264">Wenn dies der Fall ist, sollten Sie die Liste oder das Raster bis zum Rand des Bildschirms erweitern.</span><span class="sxs-lookup"><span data-stu-id="10dab-264">When this is the case, we recommend that you extend the list or grid to the edge of the screen.</span></span> <span data-ttu-id="10dab-265">Listen und Raster mit horizontalem Bildlauf sollten bis zum rechten Rand erweitert werden. Listen und Raster mit vertikalem Bildlauf sollten bis zum unteren Rand erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-265">Horizontally scrolling lists and grids should extend to the right edge, and vertically scrolling ones should extend to the bottom.</span></span>

![Abschneiden eines Rasters im fernsehsicheren Bereich](images/designing-for-tv/tv-safe-area-grid-cutoff.png)

<span data-ttu-id="10dab-267">Wenn eine Liste oder ein Raster wie hier beschrieben erweitert wird, ist es wichtig, dass die Fokusanzeige und das mit dieser verknüpfte Element weiter im fernsehsicheren Bereich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-267">While a list or grid is extended like this, it's important to keep the focus visual and its associated item inside the TV-safe area.</span></span>

![Bildlauffokus sollte weiter im fernsehsicheren Bereich angezeigt werden](images/designing-for-tv/scrolling-grid-focus.png)

<span data-ttu-id="10dab-269">Die UWP verfügt über Funktionen, die dafür sorgen, dass die Fokusanzeige weiter innerhalb der [VisibleBounds](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.visiblebounds) angezeigt wird. Sie müssen jedoch Abstand hinzufügen, um sicherzustellen, dass für die Listen-/Rasterelemente ein Bildlauf in den Anzeigebereich des sicheren Bereichs durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="10dab-269">The UWP has functionality that will keep the focus visual inside the [VisibleBounds](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.visiblebounds), but you need to add padding to ensure that the list/grid items can scroll into view of the safe area.</span></span> <span data-ttu-id="10dab-270">Genauer gesagt, müssen Sie für [ListView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) oder [GridView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.GridView) deren [ItemsPresenter](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ItemsPresenter) einen positiven Rand hinzufügen, wie im folgenden Codeausschnitt gezeigt:</span><span class="sxs-lookup"><span data-stu-id="10dab-270">Specifically, you add a positive margin to the [ListView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ListView) or [GridView](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.GridView)'s [ItemsPresenter](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ItemsPresenter), as in the following code snippet:</span></span>

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

<span data-ttu-id="10dab-271">Sie platzieren den zuvor angezeigten Codeausschnitt entweder in die Seitenressourcen oder in den App-Ressourcen und greifen anschließend wie folgt auf diesen zu:</span><span class="sxs-lookup"><span data-stu-id="10dab-271">You would put the previous code snippet in either the page or app resources, and then access it in the following way:</span></span>

```xml
<Page>
    <Grid>
        <ListView Style="{StaticResource TitleSafeListViewStyle}"
                  ... />
```

> [!NOTE]
> <span data-ttu-id="10dab-272">Dieser Codeausschnitt gilt speziell für `ListView`-Elemente. Legen Sie bei einem `GridView`-Stil das [TargetType](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate.targettype)-Attribut für [ControlTemplate](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ControlTemplate) und [Style](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Style) auf `GridView` fest.</span><span class="sxs-lookup"><span data-stu-id="10dab-272">This code snippet is specifically for `ListView`s; for a `GridView` style, set the [TargetType](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.controltemplate.targettype) attribute for both the [ControlTemplate](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ControlTemplate) and the [Style](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Style) to `GridView`.</span></span>

<span data-ttu-id="10dab-273">Für eine genauere Kontrolle über das sind Elemente eingeblendet, wenn die Anwendung, Version 1803 abzielt oder höher, können Sie das [Ereignis UIElement.BringIntoViewRequested](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.bringintoviewrequested)verwenden.</span><span class="sxs-lookup"><span data-stu-id="10dab-273">For more fine-grained control over how items are brought into view, if your application targets version 1803 or later, you can use the [UIElement.BringIntoViewRequested event](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.bringintoviewrequested).</span></span> <span data-ttu-id="10dab-274">Sie können es auf [ItemsPanel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.itemscontrol.itemspanel) platzieren, für die **ListView**/**GridView** abzufangen, bevor die internen **ScrollViewer** , wie in den folgenden Codeausschnitten ist:</span><span class="sxs-lookup"><span data-stu-id="10dab-274">You can put it on the [ItemsPanel](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.itemscontrol.itemspanel) for the **ListView**/**GridView** to catch it before the internal **ScrollViewer** does, as in the following code snippets:</span></span>

```xaml
<GridView x:Name="gridView">
    <GridView.ItemsPanel>
        <ItemsPanelTemplate>
            <ItemsWrapGrid Orientation="Horizontal"
                           BringIntoViewRequested="ItemsWrapGrid_BringIntoViewRequested"/>
        </ItemsPanelTemplate>
    </GridView.ItemsPanel>
</GridView>
```

```cs
// The BringIntoViewRequested event is raised by the framework when items receive keyboard (or Narrator) focus or 
// someone triggers it with a call to UIElement.StartBringIntoView.
private void ItemsWrapGrid_BringIntoViewRequested(UIElement sender, BringIntoViewRequestedEventArgs args)
{
    if (args.VerticalAlignmentRatio != 0.5)  // Guard against our own request
    {
        args.Handled = true;
        // Swallow this request and restart it with a request to center the item.  We could instead have chosen
        // to adjust the TargetRect’s Y and Height values to add a specific amount of padding as it bubbles up, 
        // but if we just want to center it then this is easier.

        // (Optional) Account for sticky headers if they exist
        var headerOffset = 0.0;
        var itemsWrapGrid = sender as ItemsWrapGrid;
        if (gridView.IsGrouping && itemsWrapGrid.AreStickyGroupHeadersEnabled)
        {
            var header = gridView.GroupHeaderContainerFromItemContainer(args.TargetElement as GridViewItem);
            if (header != null)
            {
                headerOffset = ((FrameworkElement)header).ActualHeight;
            }
        }

        // Issue a new request
        args.TargetElement.StartBringIntoView(new BringIntoViewOptions()
        {
            AnimationDesired = true,
            VerticalAlignmentRatio = 0.5, // a normalized alignment position (0 for the top, 1 for the bottom)
            VerticalOffset = headerOffset, // applied after meeting the alignment ratio request
        });
    }
}
```

## <a name="colors"></a><span data-ttu-id="10dab-275">Farben</span><span class="sxs-lookup"><span data-stu-id="10dab-275">Colors</span></span>

<span data-ttu-id="10dab-276">Standardmäßig skaliert die Universelle Windows-Plattform die Farben Ihrer Anwendung auf den TV-sicheren Bereich (siehe [TV-sichere Farben](#tv-safe-colors) für weitere Informationen), so dass Ihre App auf jedem Fernseher gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="10dab-276">By default, the Universal Windows Platform scales your app's colors to the TV-safe range (see [TV-safe colors](#tv-safe-colors) for more information) so that your app looks good on any TV.</span></span> <span data-ttu-id="10dab-277">Zusätzlich gibt es jedoch Verbesserungen, die für den Satz der von Ihrer App verwendeten Farben durchführen können, um die visuelle Erfahrung auf Fernsehgeräten zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="10dab-277">In addition, there are improvements that you can make to the set of colors your app uses to improve the visual experience on TV.</span></span>

### <a name="application-theme"></a><span data-ttu-id="10dab-278">Anwendungsdesign</span><span class="sxs-lookup"><span data-stu-id="10dab-278">Application theme</span></span>

<span data-ttu-id="10dab-279">Sie können ein **Anwendungsdesign** (dunkel oder hell) wählen, je nach Ihrer App, oder Designs deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="10dab-279">You can choose an **Application theme** (dark or light) according to what is right for your app, or you can opt out of theming.</span></span> <span data-ttu-id="10dab-280">Weitere allgemeine Empfehlungen für Designs finden Sie in [Farbdesigns](../style/color.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-280">Read more about general recommendations for themes in [Color themes](../style/color.md).</span></span>

<span data-ttu-id="10dab-281">Die UWP ermöglicht Apps darüber hinaus, das Design dynamisch festzulegen, basierend auf den Systemeinstellungen, die von den Geräten bereitgestellt werden, auf denen sie ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-281">The UWP also allows apps to dynamically set the theme based on the system settings provided by the devices on which they run.</span></span>
<span data-ttu-id="10dab-282">Während die UWP stets die vom Benutzer angegebenen Designeinstellungen beachtet, stellt jedes Gerät auch ein entsprechendes Standarddesign bereit.</span><span class="sxs-lookup"><span data-stu-id="10dab-282">While the UWP always respects the theme settings specified by the user, each device also provides an appropriate default theme.</span></span>
<span data-ttu-id="10dab-283">Aufgrund des Zwecks der Xbox One, die eher eine *Medien*- als eine *Produktivitäts*umgebung bereitstellen soll, ist das Systemdesign standardmäßig dunkel.</span><span class="sxs-lookup"><span data-stu-id="10dab-283">Because of the nature of Xbox One, which is expected to have more *media* experiences than *productivity* experiences, it defaults to a dark system theme.</span></span>
<span data-ttu-id="10dab-284">Wenn das Design Ihrer App auf den Systemeinstellungen basiert, sollten Sie berücksichtigen, dass es auf Xbox One standardmäßig dunkel ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-284">If your app's theme is based on the system settings, expect it to default to dark on Xbox One.</span></span>

### <a name="accent-color"></a><span data-ttu-id="10dab-285">Akzentfarbe</span><span class="sxs-lookup"><span data-stu-id="10dab-285">Accent color</span></span>

<span data-ttu-id="10dab-286">Die UWP bietet eine bequeme Möglichkeit, die **Akzentfarbe** verfügbar zu machen, die der Benutzer aus den Systemeinstellungen ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="10dab-286">The UWP provides a convenient way to expose the **accent color** that the user has selected from their system settings.</span></span>

<span data-ttu-id="10dab-287">Auf Xbox One können Benutzer eine Benutzerfarbe auswählen – genauso, wie sie auf einem PC eine Akzentfarbe auswählen können.</span><span class="sxs-lookup"><span data-stu-id="10dab-287">On Xbox One, the user is able to select a user color, just as they can select an accent color on a PC.</span></span>
<span data-ttu-id="10dab-288">Solange Ihre App diese Akzentfarben über Pinsel oder Farbressourcen aufruft, wird die vom jeweiligen Benutzer in den Systemeinstellungen ausgewählte Farbe verwendet.</span><span class="sxs-lookup"><span data-stu-id="10dab-288">As long as your app calls these accent colors through brushes or color resources, the color that the user selected in the system settings will be used.</span></span> <span data-ttu-id="10dab-289">Beachten Sie, dass Akzentfarben auf Xbox One benutzerbasiert und nicht systembasiert angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-289">Note that accent colors on Xbox One are per user, not per system.</span></span>

<span data-ttu-id="10dab-290">Beachten Sie auch, dass der Benutzerfarbensatz auf Xbox One nicht identisch mit dem Benutzerfarbensatz auf PCs, Smartphones und anderen Geräten ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-290">Please also note that the set of user colors on Xbox One is not the same as that on PCs, phones, and other devices.</span></span>

<span data-ttu-id="10dab-291">Solange Ihre App eine Pinselressource wie **SystemControlForegroundAccentBrush** oder eine Farbressource (**SystemAccentColor**) verwendet oder stattdessen Akzentfarben direkt über die [UIColorType.Accent\*](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType)-API aufruft, werden diese Farben durch Akzentfarben ersetzt, die für Xbox One geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="10dab-291">As long as your app uses a brush resource such as **SystemControlForegroundAccentBrush**, or a color resource (**SystemAccentColor**), or instead calls accent colors directly through the [UIColorType.Accent\*](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.UIColorType) API, those colors are replaced with accent colors available on Xbox One.</span></span> <span data-ttu-id="10dab-292">Pinselfarben mit hohem Kontrast werden wie im Fall von PCs und Telefonen aus dem System abgerufen.</span><span class="sxs-lookup"><span data-stu-id="10dab-292">High contrast brush colors are also pulled in from the system the same way as on a PC and phone.</span></span>

<span data-ttu-id="10dab-293">Weitere Informationen zu Akzentfarben im Allgemeinen finden Sie unter [Akzentfarbe](../style/color.md#accent-color).</span><span class="sxs-lookup"><span data-stu-id="10dab-293">To learn more about accent color in general, see [Accent color](../style/color.md#accent-color).</span></span>

### <a name="color-variance-among-tvs"></a><span data-ttu-id="10dab-294">Farbabweichungen zwischen Fernsehgeräten</span><span class="sxs-lookup"><span data-stu-id="10dab-294">Color variance among TVs</span></span>

<span data-ttu-id="10dab-295">Beachten Sie bei der Entwicklung von Apps für Fernsehgeräte, dass Farben sehr unterschiedlich dargestellt werden, abhängig von dem Fernsehgerät, auf dem sie gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-295">When designing for TV, note that colors display quite differently depending on the TV on which they are rendered.</span></span> <span data-ttu-id="10dab-296">Gehen Sie nicht davon aus, dass die Farben genau wie auf Ihrem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-296">Don't assume colors will look exactly as they do on your monitor.</span></span> <span data-ttu-id="10dab-297">Wenn Ihre App geringfügige Farbunterschiede nutzt, um Teile der Benutzeroberfläche zu unterscheiden, könnten sich die Farben mischen und die Benutzer könnten verwirrt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-297">If your app relies on subtle differences in color to differentiate parts of the UI, colors could blend together and users could get confused.</span></span> <span data-ttu-id="10dab-298">Verwenden Sie Farben, die unterschiedlich genug sind, dass Benutzer sie unabhängig vom verwendeten Fernsehgerät deutlich unterscheiden können.</span><span class="sxs-lookup"><span data-stu-id="10dab-298">Try to use colors that are different enough that users will be able to clearly differentiate them, regardless of the TV they are using.</span></span>

### <a name="tv-safe-colors"></a><span data-ttu-id="10dab-299">Fernsehsichere Farben</span><span class="sxs-lookup"><span data-stu-id="10dab-299">TV-safe colors</span></span>

<span data-ttu-id="10dab-300">Die RGB-Werte einer Farbe stellen die Intensität für Rot, Grün und Blau dar.</span><span class="sxs-lookup"><span data-stu-id="10dab-300">A color's RGB values represent intensities for red, green, and blue.</span></span> <span data-ttu-id="10dab-301">Fernseher kommen mit extremen Intensitäten nicht sehr gut zurecht. Sie können einen seltsamen Bandeffekt erzeugen oder auf bestimmten Fernsehern verwaschen erscheinen.</span><span class="sxs-lookup"><span data-stu-id="10dab-301">TVs don't handle extreme intensities very well&mdash;they can produce an odd banded effect, or appear washed out on certain TVs.</span></span> <span data-ttu-id="10dab-302">Darüber hinaus verursachen Farben mit hoher Intensität möglicherweise ein „Blooming“, d.h., Pixel in der Nähe beginnen, die gleichen Farben aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="10dab-302">Additionally, high-intensity colors may cause blooming (nearby pixels start drawing the same colors).</span></span> <span data-ttu-id="10dab-303">Die Ansichten darüber, was als fernsehsichere Farben gelten kann, gehen zwar auseinander. Im Allgemeinen können Farben mit RGB-Werten zwischen 16 und 235 (oder 10-EB hexadezimal) jedoch sicher für Fernsehgeräte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-303">While there are different schools of thought in what are considered TV-safe colors, colors within the RGB values of 16-235 (or 10-EB in hexadecimal) are generally safe to use for TV.</span></span>

![Fernsehsicherer Farbbereich](images/designing-for-tv/tv-safe-colors-2.png)

<span data-ttu-id="10dab-305">In der Vergangenheit mussten Apps auf der Xbox ihre Farben so anpassen, dass sie in diesen „TV-sicheren” Farbbereich fallen. Ab dem Fall Creators Update skaliert Xbox One jedoch automatisch alle Inhalte in den TV-sicheren Bereich.</span><span class="sxs-lookup"><span data-stu-id="10dab-305">Historically, apps on Xbox had to tailor their colors to fall within this "TV-safe" color range; however, starting with the Fall Creators Update, Xbox One automatically scales full range content into the TV-safe range.</span></span> <span data-ttu-id="10dab-306">Das bedeutet, dass sich die meisten App-Entwickler nicht mehr um TV-sichere Farben kümmern müssen.</span><span class="sxs-lookup"><span data-stu-id="10dab-306">This means that most app developers no longer have to worry about TV-safe colors.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10dab-307">Videoinhalte, die sich bereits im TV-sicheren Farbbereich befinden, haben diesen Farbskalierungseffekt bei der Wiedergabe mit [Media Foundation](https://docs.microsoft.com/windows/desktop/medfound/microsoft-media-foundation-sdk) nicht.</span><span class="sxs-lookup"><span data-stu-id="10dab-307">Video content that's already in the TV-safe color range doesn't have this color scaling effect applied when played back using [Media Foundation](https://docs.microsoft.com/windows/desktop/medfound/microsoft-media-foundation-sdk).</span></span>

<span data-ttu-id="10dab-308">Wenn Sie eine App mit DirectX 11 oder DirectX 12 entwickeln und eine eigene Swap-Kette zum Rendern von UI- oder Video-Inhalten erstellen, können Sie den verwendeten Farbraum angeben, indem Sie [IDXGISwapChain3::SetColorSpace1](https://docs.microsoft.com/windows/desktop/api/dxgi1_4/nf-dxgi1_4-idxgiswapchain3-setcolorspace1) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="10dab-308">If you're developing an app using DirectX 11 or DirectX 12 and creating your own swap chain to render UI or video, you can specify the color space you use by calling [IDXGISwapChain3::SetColorSpace1](https://docs.microsoft.com/windows/desktop/api/dxgi1_4/nf-dxgi1_4-idxgiswapchain3-setcolorspace1), which will let the system know if it needs to scale colors or not.</span></span>

## <a name="guidelines-for-ui-controls"></a><span data-ttu-id="10dab-309">Richtlinien für Benutzeroberflächensteuerelemente</span><span class="sxs-lookup"><span data-stu-id="10dab-309">Guidelines for UI controls</span></span>

<span data-ttu-id="10dab-310">Es gibt mehrere Benutzeroberflächen-Steuerelemente, die auf mehreren Geräten gut funktionieren. Wenn diese jedoch auf Fernsehgeräten verwendet werden, müssen bestimmte Aspekte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-310">There are several UI controls that work well across multiple devices, but have certain considerations when used on TV.</span></span> <span data-ttu-id="10dab-311">Informieren Sie sich über einige bewährte Methoden für die Verwendung dieser Steuerelemente beim Entwerfen für die 10 Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="10dab-311">Read about some best practices for using these controls when designing for the 10-foot experience.</span></span>

### <a name="pivot-control"></a><span data-ttu-id="10dab-312">Pivotsteuerelement</span><span class="sxs-lookup"><span data-stu-id="10dab-312">Pivot control</span></span>

<span data-ttu-id="10dab-313">Ein [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot) ermöglicht über verschiedene Header oder Registerkarten eine schnelle Navigation für Ansichten in einer App.</span><span class="sxs-lookup"><span data-stu-id="10dab-313">A [Pivot](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.Pivot) provides quick navigation of views within an app through selecting different headers or tabs.</span></span> <span data-ttu-id="10dab-314">Das Steuerelement unterstreicht jeweils den Header, der den Fokus hat. So wird bei der Nutzung von Gamepads/Remotesteuerungen deutlicher, welcher Header zurzeit ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-314">The control underlines whichever header has focus, making it more obvious which header is currently selected when using gamepad/remote.</span></span>

![Pivotunterstreichung](images/designing-for-tv/pivot-underline.png)

<span data-ttu-id="10dab-316">Sie können die [Pivot.IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pivot.isheaderitemscarouselenabledproperty)-Eigenschaft auf `true` festlegen, damit Pivots stets die gleiche Position haben und die Kopfzeile des ausgewählten Pivots nicht stets an die erste Position verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-316">You can set the [Pivot.IsHeaderItemsCarouselEnabled](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.pivot.isheaderitemscarouselenabledproperty) property to `true` so that pivots always keep the same position, rather than having the selected pivot header always move to the first position.</span></span> <span data-ttu-id="10dab-317">Dies ist besser für große Geräte mit großen Bildschirmanzeigen wie Fernsehgeräte geeignet, da Kopfzeilenumbrüche Benutzer stark ablenken können.</span><span class="sxs-lookup"><span data-stu-id="10dab-317">This is a better experience for large-screen displays such as TV, because header wrapping can be distracting to users.</span></span> <span data-ttu-id="10dab-318">Wenn nicht alle Pivotkopfzeilen gleichzeitig auf den Bildschirm passen, wird eine Bildlaufleiste angezeigt, damit Kunden die restlichen Kopfzeilen sehen. Sie sollten jedoch sicherstellen, dass alle Kopfzeilen auf den Bildschirm passen, um eine optimale Erfahrung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-318">If all of the pivot headers don't fit onscreen at once, there will be a scrollbar to let customers see the other headers; however, you should make sure that they all fit on the screen to provide the best experience.</span></span> <span data-ttu-id="10dab-319">Weitere Informationen finden Sie unter [Registerkarten und Pivots](/windows/uwp/design/controls-and-patterns/pivot).</span><span class="sxs-lookup"><span data-stu-id="10dab-319">For more information, see [Tabs and pivots](/windows/uwp/design/controls-and-patterns/pivot).</span></span>

### <a name="navigation-pane-a-namenavigation-pane-"></a><span data-ttu-id="10dab-320">Navigationsbereich <a name="navigation-pane" /></span><span class="sxs-lookup"><span data-stu-id="10dab-320">Navigation pane <a name="navigation-pane" /></span></span>

<span data-ttu-id="10dab-321">Ein Navigationsbereich (auch *Hamburger-Menü* genannt) ist ein Navigationssteuerelement, das häufig in UWP-Apps verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-321">A navigation pane (also known as a *hamburger menu*) is a navigation control commonly used in UWP apps.</span></span> <span data-ttu-id="10dab-322">In der Regel handelt es sich um einen Bereich mit mehreren Optionen im Stil eine Liste, mit denen die Benutzer zu anderen Seiten wechseln können.</span><span class="sxs-lookup"><span data-stu-id="10dab-322">Typically it is a pane with several options to choose from in a list style menu that will take the user to different pages.</span></span> <span data-ttu-id="10dab-323">Im Allgemeinen ist dieser Bereich zu Beginn reduziert, um Platz zu sparen. Der Benutzer kann ihn durch Klicken auf eine Schaltfläche öffnen.</span><span class="sxs-lookup"><span data-stu-id="10dab-323">Generally this pane starts out collapsed to save space, and the user can open it by clicking on a button.</span></span>

<span data-ttu-id="10dab-324">Während Nav-Bereiche leicht über die Maus- und Touch-Bedienung genutzt werden können, ist die Bedienung über Gamepads/Fernbedienungen weniger praktisch. Der Benutzer muss hier immer erst zu einer Schaltfläche navigieren, um den jeweiligen Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="10dab-324">While nav panes are very accessible with mouse and touch, gamepad/remote makes them less accessible since the user has to navigate to a button to open the pane.</span></span> <span data-ttu-id="10dab-325">Aus diesem Grund empfiehlt es sich, den Navigationsbereich über die **Ansicht**-Schaltfläche zu öffnen und dem Benutzer das Öffnen über das Navigieren zum linken Rand der Seite zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="10dab-325">Therefore, a good practice is to have the **View** button open the nav pane, as well as allow the user to open it by navigating all the way to the left of the page.</span></span> <span data-ttu-id="10dab-326">Ein Codebeispiel zum Implementieren dieses Entwurfsmusters finden Sie im Dokument [Programmgesteuerte Fokusnavigation](../input/focus-navigation-programmatic.md#split-view-code-sample).</span><span class="sxs-lookup"><span data-stu-id="10dab-326">Code sample on how to implement this design pattern can be found in [Programmatic focus navigation](../input/focus-navigation-programmatic.md#split-view-code-sample) document.</span></span> <span data-ttu-id="10dab-327">So steht dem Benutzer ein sehr einfacher Zugriff auf die Inhalte des Bereichs zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="10dab-327">This will provide the user with very easy access to the contents of the pane.</span></span> <span data-ttu-id="10dab-328">Weitere Informationen zum Verhalten von Navigationsbereichen auf unterschiedlichen Bildschirmgrößen sowie zu bewährten Vorgehensweisen für die Navigation mit Gamepads/Fernbedienungen finden Sie unter [Navigationsbereiche](../controls-and-patterns/navigationview.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-328">For more information about how nav panes behave in different screen sizes as well as best practices for gamepad/remote navigation, see [Nav panes](../controls-and-patterns/navigationview.md).</span></span>

### <a name="commandbar-labels"></a><span data-ttu-id="10dab-329">CommandBar-Beschriftungen</span><span class="sxs-lookup"><span data-stu-id="10dab-329">CommandBar labels</span></span>

<span data-ttu-id="10dab-330">Es empfiehlt sich, die Beschriftungen rechts neben den Symbolen auf einer [CommandBar](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar) zu platzieren. So bleibt dessen Höhe minimiert und konsistent.</span><span class="sxs-lookup"><span data-stu-id="10dab-330">It is a good idea to have the labels placed to the right of the icons on a [CommandBar](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.CommandBar) so that its height is minimized and stays consistent.</span></span> <span data-ttu-id="10dab-331">Sie erreichen dies, indem Sie die Eigenschaft [CommandBar.DefaultLabelPosition](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar.defaultlabelpositionproperty) auf `CommandBarDefaultLabelPosition.Right` festlegen.</span><span class="sxs-lookup"><span data-stu-id="10dab-331">You can do this by setting the [CommandBar.DefaultLabelPosition](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.commandbar.defaultlabelpositionproperty) property to `CommandBarDefaultLabelPosition.Right`.</span></span>

![CommandBar Beschriftungen rechts von Symbolen](images/designing-for-tv/commandbar.png)

<span data-ttu-id="10dab-333">Durch das Festlegen dieser Eigenschaft werden die Beschriftungen immer angezeigt. Dies ist bei einer 10-Fuß-Erfahrung vorteilhaft, denn es minimiert die Anzahl der durch den Benutzer erforderlichen Klicks.</span><span class="sxs-lookup"><span data-stu-id="10dab-333">Setting this property will also cause the labels to always be displayed, which works well for the 10-foot experience because it minimizes the number of clicks for the user.</span></span> <span data-ttu-id="10dab-334">Auch für andere Gerätetypen ist dies ein hervorragendes Konzept.</span><span class="sxs-lookup"><span data-stu-id="10dab-334">This is also a great model for other device types to follow.</span></span>

### <a name="tooltip"></a><span data-ttu-id="10dab-335">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="10dab-335">Tooltip</span></span>

<span data-ttu-id="10dab-336">Das Steuerelement [QuickInfo](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ToolTip) wurde eingeführt, um zusätzliche Informationen in der Benutzeroberfläche anzeigen zu können, wenn der Benutzer mit der Maus auf ein Element zeigt oder mit dem Finger auf ein Element tippt und den Finger darauf hält.</span><span class="sxs-lookup"><span data-stu-id="10dab-336">The [Tooltip](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.ToolTip) control was introduced as a way to provide more information in the UI when the user hovers the mouse over, or taps and holds their figure on, an element.</span></span> <span data-ttu-id="10dab-337">Für Gamepad und Remote wird `Tooltip` kurz nachdem das Element den Fokus erhält angezeigt, bleibt für einen kurzen Zeitraum auf dem Bildschirm und verschwindet dann.</span><span class="sxs-lookup"><span data-stu-id="10dab-337">For gamepad and remote, `Tooltip` appears after a brief moment when the element gets focus, stays onscreen for a short time, and then disappears.</span></span> <span data-ttu-id="10dab-338">Dieses Verhalten könnte ablenkend wirken, wenn zu viele `Tooltip`-Elemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-338">This behavior could be distracting if too many `Tooltip`s are used.</span></span> <span data-ttu-id="10dab-339">Versuchen Sie, `Tooltip`-Elemente bei Entwürfen für Fernsehgeräte zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="10dab-339">Try to avoid using `Tooltip` when designing for TV.</span></span>

### <a name="button-styles"></a><span data-ttu-id="10dab-340">Schaltflächenstile</span><span class="sxs-lookup"><span data-stu-id="10dab-340">Button styles</span></span>

<span data-ttu-id="10dab-341">Zwar funktionieren die Standard-UWP-Schaltflächen sehr gut auf TV-Bildschirmen, es gibt jedoch einige visuelle Stile für Schaltflächen, die noch besser auf die Benutzeroberfläche aufmerksam machen. Sie sollten diese für alle Plattformen in Erwägung ziehen, besonders für die 10-Fuß-Umgebung, bei der es sehr vorteilhaft ist, die Fokusposition klar und deutlich darzustellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-341">While the standard UWP buttons work well on TV, some visual styles of buttons call attention to the UI better, which you may want to consider for all platforms, particularly in the 10-foot experience, which benefits from clearly communicating where the focus is located.</span></span> <span data-ttu-id="10dab-342">Weitere Informationen zu diesen Stilen finden Sie unter [Schaltflächen](../controls-and-patterns/buttons.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-342">To read more about these styles, see [Buttons](../controls-and-patterns/buttons.md).</span></span>

### <a name="nested-ui-elements"></a><span data-ttu-id="10dab-343">Geschachtelte UI-Elemente</span><span class="sxs-lookup"><span data-stu-id="10dab-343">Nested UI elements</span></span>

<span data-ttu-id="10dab-344">Eine geschachtelte Benutzeroberfläche (User Interface, UI) verfügt über geschachtelte Elemente mit ausführbaren Aktionen, die in einem Container eingeschlossen sind, sodass sowohl die geschachtelten Elemente als auch die Container unabhängig voneinander den Fokus erhalten können.</span><span class="sxs-lookup"><span data-stu-id="10dab-344">Nested UI exposes nested actionable items enclosed inside a container UI element where both the nested item as well as the container item can take independent focus from each other.</span></span>

<span data-ttu-id="10dab-345">Geschachtelte UI eignet sich für einige Eingabetypen, jedoch nicht immer für Gamepads und Fernbedienungen, da diese eine XY-Navigation erfordern.</span><span class="sxs-lookup"><span data-stu-id="10dab-345">Nested UI works well for some input types, but not always for gamepad and remote, which rely on XY navigation.</span></span> <span data-ttu-id="10dab-346">Beachten Sie die unter diesem Thema angeführten Richtlinien, um sicherzustellen, dass die Benutzeroberfläche für die 10-Fuß-Umgebung optimiert ist, und dass die Benutzer mühelos auf alle interaktiven Elemente zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="10dab-346">Be sure to follow the guidance in this topic to ensure that your UI is optimized for the 10-foot environment, and that the user can access all interactable elements easily.</span></span> <span data-ttu-id="10dab-347">Eine gängige Lösung besteht darin, geschachtelte UI-Elemente in einem `ContextFlyout` zu platzieren (siehe [CommandBar und ContextFlyout](#commandbar-and-contextflyout)).</span><span class="sxs-lookup"><span data-stu-id="10dab-347">One common solution is to place nested UI elements in a `ContextFlyout` (see [CommandBar and ContextFlyout](#commandbar-and-contextflyout)).</span></span>

<span data-ttu-id="10dab-348">Weitere Informationen zur geschachtelten UI finden Sie unter [Geschachtelte UI bei Listenelementen](../controls-and-patterns/nested-ui.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-348">For more information on nested UI, see [Nested UI in list items](../controls-and-patterns/nested-ui.md).</span></span>

### <a name="mediatransportcontrols"></a><span data-ttu-id="10dab-349">MediaTransportControls</span><span class="sxs-lookup"><span data-stu-id="10dab-349">MediaTransportControls</span></span>

<span data-ttu-id="10dab-350">Das [MediaTransportControls](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaTransportControls)-Element ermöglicht Benutzern die Interaktion mit ihren Medien. Hierzu stellt es eine standardmäßige Wiedergabeumgebung bereit, in der Benutzer unter anderem die Wiedergabe starten und anhalten sowie Untertitel aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="10dab-350">The [MediaTransportControls](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaTransportControls) element lets users interact with their media by providing a default playback experience that allows them to play, pause, turn on closed captions, and more.</span></span> <span data-ttu-id="10dab-351">Dieses Steuerelement ist eine Eigenschaft von [MediaPlayerElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaPlayerElement) und unterstützt zwei Layoutoptionen: *einzeilig* und *zweizeilig*.</span><span class="sxs-lookup"><span data-stu-id="10dab-351">This control is a property of [MediaPlayerElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaPlayerElement) and supports two layout options: *single-row* and *double-row*.</span></span> <span data-ttu-id="10dab-352">Beim einzeiligen Layout befinden sich der Schieberegler und die Wiedergabeschaltflächen alle in einer Zeile, und die Schaltfläche für Wiedergabe/Pause wird links neben dem Schieberegler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="10dab-352">In the single-row layout, the slider and playback buttons are all located in one row, with the play/pause button located to the left of the slider.</span></span> <span data-ttu-id="10dab-353">Beim zweizeiligen Layout befindet sich der Schieberegler in einer eigenen Zeile, und die Wiedergabeschaltflächen werden in einer Zeile darunter angezeigt.</span><span class="sxs-lookup"><span data-stu-id="10dab-353">In the double-row layout, the slider occupies its own row, with the playback buttons on a separate lower row.</span></span> <span data-ttu-id="10dab-354">Bei Designs für die 10-Fuß-Erfahrung empfiehlt sich die Verwendung des zweizeiligen Layouts, da es eine bessere Gamepadnavigation ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="10dab-354">When designing for the 10-foot experience, the double-row layout should be used, as it provides better navigation for gamepad.</span></span> <span data-ttu-id="10dab-355">Wenn Sie das zweizeilige Layout aktivieren möchten, legen Sie in der [TransportControls](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.mediaplayerelement.transportcontrols)-Eigenschaft von `MediaPlayerElement` für das `MediaTransportControls`-Element Folgendes fest: `IsCompact="False"`.</span><span class="sxs-lookup"><span data-stu-id="10dab-355">To enable the double-row layout, set `IsCompact="False"` on the `MediaTransportControls` element in the [TransportControls](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.mediaplayerelement.transportcontrols) property of the `MediaPlayerElement`.</span></span>

```xml
<MediaPlayerElement x:Name="mediaPlayerElement1"  
                    Source="Assets/video.mp4"
                    AreTransportControlsEnabled="True">
    <MediaPlayerElement.TransportControls>
        <MediaTransportControls IsCompact="False"/>
    </MediaPlayerElement.TransportControls>
</MediaPlayerElement>
```  

<span data-ttu-id="10dab-356">Weitere Informationen zum Hinzufügen von Medien zu Ihrer App finden Sie unter [Medienwiedergabe](../controls-and-patterns/media-playback.md).</span><span class="sxs-lookup"><span data-stu-id="10dab-356">Visit [Media playback](../controls-and-patterns/media-playback.md) to learn more about adding media to your app.</span></span>

> <span data-ttu-id="10dab-357">![HINWEIS:] `MediaPlayerElement` steht erst ab der Windows10-Version1607 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="10dab-357">![NOTE] `MediaPlayerElement` is only available in Windows 10, version 1607 and later.</span></span> <span data-ttu-id="10dab-358">Bei Apps für niedrigere Windows10-Versionen muss stattdessen [MediaElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaElement) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="10dab-358">If you're developing an app for an earlier version of Windows 10, you'll need to use [MediaElement](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Controls.MediaElement) instead.</span></span> <span data-ttu-id="10dab-359">Die hier angegebenen Empfehlungen gelten auch für `MediaElement`, und der Zugriff auf die `TransportControls`-Eigenschaft erfolgt auf die gleiche Weise.</span><span class="sxs-lookup"><span data-stu-id="10dab-359">The recommendations above apply to `MediaElement` as well, and the `TransportControls` property is accessed in the same way.</span></span>

### <a name="search-experience"></a><span data-ttu-id="10dab-360">Suchvorgang</span><span class="sxs-lookup"><span data-stu-id="10dab-360">Search experience</span></span>

<span data-ttu-id="10dab-361">Die Suche nach Inhalten ist eine der am häufigsten ausgeführten Funktionen in der 10-Fuß-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="10dab-361">Searching for content is one of the most commonly performed functions in the 10-foot experience.</span></span> <span data-ttu-id="10dab-362">Wenn Ihre App eine Suchfunktion zur Verfügung stellt, sollte der Benutzer auf diese schnell über die **Y**-Taste auf dem Gamepad zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="10dab-362">If your app provides a search experience, it is helpful for the user to have quick access to it by using the **Y** button on the gamepad as an accelerator.</span></span>

<span data-ttu-id="10dab-363">Die meisten Kunden sollten mit dieser Beschleunigungsfunktion bereits vertraut sein. Sie können aber auch der Benutzeroberfläche eine visuelle **Y**-Glyphe hinzufügen, um anzuzeigen, dass der Benutzer mit dieser Taste auf die Suchfunktion zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="10dab-363">Most customers should already be familiar with this accelerator, but if you like you can add a visual **Y** glyph to the UI to indicate that the customer can use the button to access search functionality.</span></span> <span data-ttu-id="10dab-364">In diesem Fall müssen Sie das Symbol aus der Schriftart **Segoe Xbox MDL2 Symbol** (`&#xE3CC;` für XAML-Apps, `\E426` für HTML-Apps) verwenden, um die Konsistenz sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-364">If you do add this cue, be sure to use the symbol from the **Segoe Xbox MDL2 Symbol** font (`&#xE3CC;` for XAML apps, `\E426` for HTML apps) to provide consistency with the Xbox shell and other apps.</span></span>

> [!NOTE]
> <span data-ttu-id="10dab-365">Da die Schriftart **Segoe Xbox MDL2 Symbol** nur auf Xbox verfügbar ist, wird das Symbol auf Ihrem PC nicht ordnungsgemäß angezeigt.</span><span class="sxs-lookup"><span data-stu-id="10dab-365">Because the **Segoe Xbox MDL2 Symbol** font is only available on Xbox, the symbol won't appear correctly on your PC.</span></span> <span data-ttu-id="10dab-366">Es wird jedoch auf dem Fernseher angezeigt, nachdem Sie auf Xbox bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="10dab-366">However, it will show up on the TV once you deploy to Xbox.</span></span>

<span data-ttu-id="10dab-367">Da die **Y**-Taste nur auf dem Gamepad verfügbar ist, müssen Sie auch andere Möglichkeiten für den Zugriff auf die Suche zur Verfügung stellen, wie Schaltflächen in der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="10dab-367">Since the **Y** button is only available on gamepad, make sure to provide other methods of access to search, such as buttons in the UI.</span></span> <span data-ttu-id="10dab-368">Andernfalls können einige Kunden möglicherweise nicht auf diese Funktion zugreifen.</span><span class="sxs-lookup"><span data-stu-id="10dab-368">Otherwise, some customers may not be able to access the functionality.</span></span>

<span data-ttu-id="10dab-369">In der 10-Fuß-Erfahrung ist es für Kunden oft einfacher, eine Vollbildschirm-Suche durchzuführen, da der Platz auf dem Display begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="10dab-369">In the 10-foot experience, it is often easier for customers to use a full screen search experience because there is limited room on the display.</span></span> <span data-ttu-id="10dab-370">Unabhängig davon, ob Sie eine Voll- oder Teilbildschirm-Direktsuche haben, empfehlen wir, dass die Bildschirmtastatur bereits geöffnet ist, wenn der Benutzer die Suchfunktion öffnet, damit sofort Suchbegriffe eingegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="10dab-370">Whether you have full screen or partial-screen, "in-place" search, we recommend that when the user opens the search experience, the onscreen keyboard appears already opened, ready for the customer to enter search terms.</span></span>

## <a name="custom-visual-state-trigger-for-xbox"></a><span data-ttu-id="10dab-371">Benutzerdefinierter visueller Zustandsauslöser für Xbox</span><span class="sxs-lookup"><span data-stu-id="10dab-371">Custom visual state trigger for Xbox</span></span>

<span data-ttu-id="10dab-372">Um Ihre UWP-App an die 10-Fuß-Erfahrung anzupassen, empfehlen wir Ihnen, das Layout zu ändern, wenn die App erkennt, dass sie auf einer Xbox-Konsole gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="10dab-372">To tailor your UWP app for the 10-foot experience, we recommend that you make layout changes when the app detects that it has been launched on an Xbox console.</span></span> <span data-ttu-id="10dab-373">Eine Möglichkeit, um dies zu erreichen ist die Verwendung eines benutzerdefinierten *visuellen Zustandsauslösers*.</span><span class="sxs-lookup"><span data-stu-id="10dab-373">One way to do this is by using a custom *visual state trigger*.</span></span> <span data-ttu-id="10dab-374">Visuelle Zustandsauslöser sind besonders dann nützlich, wenn Sie in **Blend für Visual Studio** arbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="10dab-374">Visual state triggers are most useful when you want to edit in **Blend for Visual Studio**.</span></span> <span data-ttu-id="10dab-375">Der folgende Codeausschnitt zeigt, wie ein visueller Zustandsauslöser für Xbox erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="10dab-375">The following code snippet shows how to create a visual state trigger for Xbox:</span></span>

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

<span data-ttu-id="10dab-376">Um den Auslöser zu erstellen, fügen Sie Ihrer App die folgende Klasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="10dab-376">To create the trigger, add the following class to your app.</span></span> <span data-ttu-id="10dab-377">Dies ist die Klasse, die in dem XAML-Code oben referenziert wird:</span><span class="sxs-lookup"><span data-stu-id="10dab-377">This is the class that is referenced by the XAML code above:</span></span>

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

<span data-ttu-id="10dab-378">Nachdem Sie den benutzerdefinierten Auslöser hinzugefügt haben, wird Ihre App automatisch die Layoutänderungen ausführen, die Sie im XAML-Code angegeben haben, wenn sie erkennt, dass sie auf einer Xbox One-Konsole ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="10dab-378">After you've added your custom trigger, your app will automatically make the layout modifications you specified in your XAML code whenever it detects that it is running on an Xbox One console.</span></span>

<span data-ttu-id="10dab-379">Sie können außerdem über Programmcode erkennen, ob die App auf Xbox ausgeführt wird, und dann entsprechende Anpassungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="10dab-379">Another way you can check whether your app is running on Xbox and then make the appropriate adjustments is through code.</span></span> <span data-ttu-id="10dab-380">Mit der folgenden einfachen Variable können Sie überprüfen, ob Ihre App auf Xbox ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="10dab-380">You can use the following simple variable to check if your app is running on Xbox:</span></span>

```csharp
bool IsTenFoot = (Windows.System.Profile.AnalyticsInfo.VersionInfo.DeviceFamily ==
                    "Windows.Xbox");
```

<span data-ttu-id="10dab-381">Anschließend können Sie im Codeblock nach der Überprüfung die entsprechenden Anpassungen für Ihr UI vornehmen.</span><span class="sxs-lookup"><span data-stu-id="10dab-381">Then, you can make the appropriate adjustments to your UI in the code block following this check.</span></span> <span data-ttu-id="10dab-382">Ein Beispiel hierfür finden Sie im [Beispiel für UWP-Farbe](#uwp-color-sample).</span><span class="sxs-lookup"><span data-stu-id="10dab-382">An example of this is shown in [UWP color sample](#uwp-color-sample).</span></span>

## <a name="summary"></a><span data-ttu-id="10dab-383">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="10dab-383">Summary</span></span>

<span data-ttu-id="10dab-384">Beim Entwerfen für die 10 Fuß-Erfahrung müssen einige besondere Punkte berücksichtigt werden, die sich vom Entwerfen für andere Plattformen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="10dab-384">Designing for the 10-foot experience has special considerations to take into account that make it different from designing for any other platform.</span></span> <span data-ttu-id="10dab-385">Sie können durchaus Ihre UWP-App einfach zu Xbox One portieren, dies funktioniert. Die App wird jedoch nicht unbedingt für die 10-Fuß-Erfahrung optimiert und kann für den Benutzer mit Frustration verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="10dab-385">While you can certainly do a straight port of your UWP app to Xbox One and it will work, it won't necessarily be optimized for the 10-foot experience and can lead to user frustration.</span></span> <span data-ttu-id="10dab-386">Wenn Sie die Richtlinien in diesem Artikel befolgen, stellen Sie so sicher, dass Ihre App genauso gut auf Fernsehgeräten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="10dab-386">Following the guidelines in this article will make sure that your app is as good as it can be on TV.</span></span>

## <a name="related-articles"></a><span data-ttu-id="10dab-387">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="10dab-387">Related articles</span></span>

- [<span data-ttu-id="10dab-388">Einführung der Geräte für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="10dab-388">Device primer for Universal Windows Platform (UWP) apps</span></span>](index.md)
- [<span data-ttu-id="10dab-389">Interaktionen mit Gamepad und Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="10dab-389">Gamepad and remote control interactions</span></span>](../input/gamepad-and-remote-interactions.md)
- [<span data-ttu-id="10dab-390">Sound in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="10dab-390">Sound in UWP apps</span></span>](../style/sound.md)
