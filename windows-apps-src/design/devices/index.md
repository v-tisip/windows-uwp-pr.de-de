---
Description: Getting to know the devices that support Universal Windows Platform (UWP) apps will help you offer the best user experience for each form factor.
title: Einführung der Geräte für UWP-Apps (Universelle Windows-Plattform)
ms.assetid: 7665044E-F007-495D-8D56-CE7C2361CDC4
label: Device primer
template: detail.hbs
keywords: Gerät, Eingabe, Interaktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: de67a61b4d5982675d32e0446b67d7cf70051923
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8214086"
---
#  <a name="device-primer-for-universal-windows-platform-uwp-apps"></a><span data-ttu-id="ab804-103">Einführung der Geräte für UWP-Apps (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="ab804-103">Device primer for Universal Windows Platform (UWP) apps</span></span>



![Windows-Geräte](images/device-primer/device-primer-ramp.png)

<span data-ttu-id="ab804-105">Wenn Sie sich mit den Geräten vertraut machen, die UWP-Apps (Universelle Windows-Plattform) unterstützen, können Sie für jeden Formfaktor die bestmögliche Benutzerfreundlichkeit bieten.</span><span class="sxs-lookup"><span data-stu-id="ab804-105">Getting to know the devices that support Universal Windows Platform (UWP) apps will help you offer the best user experience for each form factor.</span></span> <span data-ttu-id="ab804-106">Beim Entwickeln für ein bestimmtes Gerät sind die wichtigsten zu berücksichtigenden Punkte die Darstellung der App auf dem Gerät, wo, wann und wie die App auf dem Gerät genutzt wird und die Art der Interaktion der Benutzer mit dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="ab804-106">When designing for a particular device, the main considerations include how the app will appear on that device, where, when, and how the app will be used on that device, and how the user will interact with that device.</span></span>

## <a name="pcs-and-laptops"></a><span data-ttu-id="ab804-107">PCs und Laptops</span><span class="sxs-lookup"><span data-stu-id="ab804-107">PCs and laptops</span></span>


<span data-ttu-id="ab804-108">Mit PCs und Laptops von Windows wird eine breite Palette von Geräten und Bildschirmgrößen abgedeckt.</span><span class="sxs-lookup"><span data-stu-id="ab804-108">Windows PCs and laptops include a wide array of devices and screen sizes.</span></span> <span data-ttu-id="ab804-109">Im Allgemeinen können auf PCs und Laptops mehr Informationen als auf Smartphones oder Tablets angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ab804-109">In general, PCs and laptops can display more info than phone or tablets.</span></span>

<span data-ttu-id="ab804-110">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-110">Screen sizes</span></span>
-   <span data-ttu-id="ab804-111">13 Zoll und größer</span><span class="sxs-lookup"><span data-stu-id="ab804-111">13” and greater</span></span>

![PC](images/device-primer/device-primer-desktop.png)

<span data-ttu-id="ab804-113">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-113">Typical usage</span></span>
-   <span data-ttu-id="ab804-114">Apps werden auf Desktops und Laptops häufig gleichzeitig genutzt, aber nur von jeweils einem Benutzer und meist über längere Zeiträume hinweg.</span><span class="sxs-lookup"><span data-stu-id="ab804-114">Apps on desktops and laptops see shared use, but by one user at a time, and usually for longer periods.</span></span>

<span data-ttu-id="ab804-115">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-115">UI considerations</span></span>
-   <span data-ttu-id="ab804-116">Apps können in einer Fensteransicht angezeigt werden, deren Größe vom Benutzer bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="ab804-116">Apps can have a windowed view, the size of which is determined by the user.</span></span> <span data-ttu-id="ab804-117">Je nach Größe des Fensters können darin zwischen einem und drei Frames enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="ab804-117">Depending on window size, there can be between one and three frames.</span></span> <span data-ttu-id="ab804-118">Auf größeren Bildschirmen kann die App mehr als drei Frames haben.</span><span class="sxs-lookup"><span data-stu-id="ab804-118">On larger monitors, the app can have more than three frames.</span></span>

-   <span data-ttu-id="ab804-119">Beim Nutzen einer App auf einem Desktop oder Laptop haben Benutzer die Kontrolle über App-Dateien.</span><span class="sxs-lookup"><span data-stu-id="ab804-119">When using an app on a desktop or laptop, the user has control over app files.</span></span> <span data-ttu-id="ab804-120">Achten Sie als App-Designer darauf, Verfahren einzubauen, die dem Verwalten der App-Inhalte dienen.</span><span class="sxs-lookup"><span data-stu-id="ab804-120">As an app designer, be sure to provide the mechanisms to manage your app’s content.</span></span> <span data-ttu-id="ab804-121">Erwägen Sie, Befehle und Features der Art „Speichern unter“, „Zuletzt verwendet“ usw. bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ab804-121">Consider including commands and features such as "Save As", "Recent files", and so on.</span></span>

-   <span data-ttu-id="ab804-122">Die Zurück-Schaltfläche des Systems ist optional.</span><span class="sxs-lookup"><span data-stu-id="ab804-122">System back is optional.</span></span> <span data-ttu-id="ab804-123">Wenn ein App-Entwickler diese anzeigen möchte, wird sie in der App-Titelleiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab804-123">When an app developer chooses to show it, it appears in the app title bar.</span></span>

<span data-ttu-id="ab804-124">Eingabemöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ab804-124">Inputs</span></span>
-   <span data-ttu-id="ab804-125">Maus</span><span class="sxs-lookup"><span data-stu-id="ab804-125">Mouse</span></span>
-   <span data-ttu-id="ab804-126">Tastatur</span><span class="sxs-lookup"><span data-stu-id="ab804-126">Keyboard</span></span>
-   <span data-ttu-id="ab804-127">Toucheingabe auf Laptops und All-in-One-Desktops.</span><span class="sxs-lookup"><span data-stu-id="ab804-127">Touch on laptops and all-in-one desktops.</span></span>
-   <span data-ttu-id="ab804-128">Es werden auch Gamepads verwendet, z.B. der Xbox-Controller.</span><span class="sxs-lookup"><span data-stu-id="ab804-128">Gamepads, such as the Xbox controller, are sometimes used.</span></span>

<span data-ttu-id="ab804-129">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-129">Typical device capabilities</span></span>
-   <span data-ttu-id="ab804-130">Kamera</span><span class="sxs-lookup"><span data-stu-id="ab804-130">Camera</span></span>
-   <span data-ttu-id="ab804-131">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="ab804-131">Microphone</span></span>

## <a name="tablets-and-2-in-1s"></a><span data-ttu-id="ab804-132">Tablets und 2-in-1-Geräte</span><span class="sxs-lookup"><span data-stu-id="ab804-132">Tablets and 2-in-1s</span></span>


<span data-ttu-id="ab804-133">Extrem leichte Tablet PCs sind mit Touchscreens, Kameras, Mikrofonen und Beschleunigungsmessern ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="ab804-133">Ultra-portable tablet computers are equipped with touchscreens, cameras, microphones, and accelerometers.</span></span> <span data-ttu-id="ab804-134">Die Größe der Bildschirme von Tablets reicht normalerweise von 7 bis 13,3 Zoll.</span><span class="sxs-lookup"><span data-stu-id="ab804-134">Tablet screen sizes usually range from 7” to 13.3”.</span></span> <span data-ttu-id="ab804-135">2-in-1-Geräte können abhängig von der Konfiguration als Tablet oder Laptop mit einer Tastatur und Maus verwendet werden (in der Regel wird hierzu der Bildschirm aufgestellt oder nach hinten geklappt).</span><span class="sxs-lookup"><span data-stu-id="ab804-135">2-in-1 devices can act like either a tablet or a laptop with a keyboard and mouse, depending on the configuration (usually involving folding the screen back or tilting it upright).</span></span>

<span data-ttu-id="ab804-136">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-136">Screen sizes</span></span>
- <span data-ttu-id="ab804-137">7 bis 13,3Zoll bei Tablets</span><span class="sxs-lookup"><span data-stu-id="ab804-137">7” to 13.3” for tablet</span></span>
- <span data-ttu-id="ab804-138">13,3Zoll und größer bei 2-in-1-Geräten</span><span class="sxs-lookup"><span data-stu-id="ab804-138">13.3" and greater for 2-in-1</span></span>

![Tabletgerät](images/device-primer/device-primer-tablet.png)

<span data-ttu-id="ab804-140">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-140">Typical usage</span></span>
-   <span data-ttu-id="ab804-141">Tablets werden zu ca. 80 Prozent vom Besitzer und zu ca. 20 Prozent von anderen Personen genutzt.</span><span class="sxs-lookup"><span data-stu-id="ab804-141">About 80% of tablet use is by the owner, with the other 20% being shared use.</span></span>
-   <span data-ttu-id="ab804-142">Es wird meist zu Hause als Begleitgerät beim Fernsehen verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-142">It’s most commonly used at home as a companion device while watching TV.</span></span>
-   <span data-ttu-id="ab804-143">Es wird über längere Zeiträume hinweg als bei Smartphones und Phablets verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-143">It’s used for longer periods than phones and phablets.</span></span>
-   <span data-ttu-id="ab804-144">Text wird häufig und jeweils nur für kurze Zeit eingegeben.</span><span class="sxs-lookup"><span data-stu-id="ab804-144">Text is entered in short bursts.</span></span>

<span data-ttu-id="ab804-145">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-145">UI considerations</span></span>
-   <span data-ttu-id="ab804-146">Auf Tablets können sowohl im Querformat als auch im Hochformat jeweils zwei Frames angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ab804-146">In both landscape and portrait orientations, tablets allow two frames at a time.</span></span>
-   <span data-ttu-id="ab804-147">Die Zurück-Schaltfläche des Systems befindet sich in der Navigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="ab804-147">System back is located on the navigation bar.</span></span>

<span data-ttu-id="ab804-148">Eingabemöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ab804-148">Inputs</span></span>
-   <span data-ttu-id="ab804-149">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="ab804-149">Touch</span></span>
-   <span data-ttu-id="ab804-150">Eingabestift</span><span class="sxs-lookup"><span data-stu-id="ab804-150">Stylus</span></span>
-   <span data-ttu-id="ab804-151">Externe Tastatur (gelegentlich)</span><span class="sxs-lookup"><span data-stu-id="ab804-151">External keyboard (occasionally)</span></span>
-   <span data-ttu-id="ab804-152">Maus (gelegentlich)</span><span class="sxs-lookup"><span data-stu-id="ab804-152">Mouse (occasionally)</span></span>
-   <span data-ttu-id="ab804-153">Sprache (gelegentlich)</span><span class="sxs-lookup"><span data-stu-id="ab804-153">Voice (occasionally)</span></span>

<span data-ttu-id="ab804-154">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-154">Typical device capabilities</span></span>
-   <span data-ttu-id="ab804-155">Kamera</span><span class="sxs-lookup"><span data-stu-id="ab804-155">Camera</span></span>
-   <span data-ttu-id="ab804-156">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="ab804-156">Microphone</span></span>
-   <span data-ttu-id="ab804-157">Bewegungssensoren</span><span class="sxs-lookup"><span data-stu-id="ab804-157">Movement sensors</span></span>
-   <span data-ttu-id="ab804-158">Positionssensoren</span><span class="sxs-lookup"><span data-stu-id="ab804-158">Location sensors</span></span>

> [!NOTE]
> <span data-ttu-id="ab804-159">Die meisten Überlegungen zu PCs und Laptops gelten auch für 2-in-1-Geräte.</span><span class="sxs-lookup"><span data-stu-id="ab804-159">Most of the considerations for PCs and laptops apply to 2-in-1s as well.</span></span>

## <a name="xbox-and-tv"></a><span data-ttu-id="ab804-160">Xbox und Fernsehgeräte</span><span class="sxs-lookup"><span data-stu-id="ab804-160">Xbox and TV</span></span>

<span data-ttu-id="ab804-161">Die Erfahrung, die Sie machen, wenn Sie auf dem Sofa sitzen und mittels eines Gamepads oder einer Fernbedienung mit Ihrem Fernsehgerät interagieren, wird als **3-Meter-Erfahrung** (10-Fuß-Erfahrung) bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ab804-161">The experience of sitting on your couch across the room, using a gamepad or remote to interact with your TV, is called the **10-foot experience**.</span></span> <span data-ttu-id="ab804-162">Der Name kommt daher, dass sich der Benutzer im Allgemeinen ungefähr 3Meter (10Fuß) vom Bildschirm entfernt befindet.</span><span class="sxs-lookup"><span data-stu-id="ab804-162">It is so named because the user is generally sitting approximately 10 feet away from the screen.</span></span> <span data-ttu-id="ab804-163">Dies stellt eine besondere Herausforderung dar, die beispielsweise bei einer *50-cm-Erfahrung* (2-Fuß-Erfahrung) oder bei der Interaktion mit einem PC nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ab804-163">This provides unique challenges that aren't present in, say, the *2-foot* experience, or interacting with a PC.</span></span> <span data-ttu-id="ab804-164">Wenn Sie eine App für Xbox One oder ein anderes Gerät entwickeln, das an einen Fernsehbildschirm angeschlossen ist und unter Umständen ein Gamepad oder Fernbedienung für die Eingabe verwendet, sollten Sie dies stets bedenken.</span><span class="sxs-lookup"><span data-stu-id="ab804-164">If you are developing an app for Xbox One or any other device that's connected to a TV screen and might use a gamepad or remote for input, you should always keep this in mind.</span></span>

<span data-ttu-id="ab804-165">Die Schritte beim Entwickeln einer UWP-App für die 3-Meter-Erfahrung unterscheiden sich stark von der Entwicklung für eine der hier aufgeführten Gerätekategorien.</span><span class="sxs-lookup"><span data-stu-id="ab804-165">Designing your UWP app for the 10-foot experience is very different from designing for any of the other device categories listed here.</span></span> <span data-ttu-id="ab804-166">Weitere Informationen finden Sie unter [Entwerfen für Xbox und Fernsehgeräte](designing-for-tv.md).</span><span class="sxs-lookup"><span data-stu-id="ab804-166">For more information, see [Designing for Xbox and TV](designing-for-tv.md).</span></span>

<span data-ttu-id="ab804-167">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-167">Screen sizes</span></span>
- <span data-ttu-id="ab804-168">24Zoll und größer</span><span class="sxs-lookup"><span data-stu-id="ab804-168">24" and up</span></span>

![Xbox und Fernsehgeräte](images/device-primer/device-primer-tv-and-xbox.png)

<span data-ttu-id="ab804-170">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-170">Typical usage</span></span>
- <span data-ttu-id="ab804-171">Wird häufig von mehreren Personen, aber auch häufig nur von einer Person verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-171">Often shared among several people, though is also often used by just one person.</span></span>
- <span data-ttu-id="ab804-172">Wird in der Regel über längere Zeiträume hinweg verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-172">Usually used for longer periods.</span></span>
- <span data-ttu-id="ab804-173">Wird meist zu Hause, also an einem Ort, verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-173">Most commonly used at home, staying in one place.</span></span>
- <span data-ttu-id="ab804-174">Texteingabe ist selten erforderlich, da diese mit einem Gamepad oder einer Fernbedienung zeitaufwendiger ist.</span><span class="sxs-lookup"><span data-stu-id="ab804-174">Rarely asks for text input because it takes longer with a gamepad or remote.</span></span>
- <span data-ttu-id="ab804-175">Die Ausrichtung des Bildschirms ist fest.</span><span class="sxs-lookup"><span data-stu-id="ab804-175">Orientation of the screen is fixed.</span></span>
- <span data-ttu-id="ab804-176">In der Regel wird jeweils nur eine App ausgeführt. Unter Umständen ist das Andocken von Apps an der Seite möglich (etwa bei Xbox).</span><span class="sxs-lookup"><span data-stu-id="ab804-176">Usually only runs one app at a time, but it may be possible to snap apps to the side (such as on Xbox).</span></span>

<span data-ttu-id="ab804-177">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-177">UI considerations</span></span>
- <span data-ttu-id="ab804-178">Apps behalten in der Regel die gleiche Größe, es sei denn, eine andere App ist an der Seite angedockt.</span><span class="sxs-lookup"><span data-stu-id="ab804-178">Apps usually stay the same size, unless another app is snapped to the side.</span></span>
- <span data-ttu-id="ab804-179">Die Zurück-Schaltfläche des Systems ist eine nützliche Funktion, die in den meisten Xbox-Apps zur Verfügung steht und auf die mit der B-Taste auf dem Gamepad zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="ab804-179">System back is useful functionality that is offered in most Xbox apps, accessed using the B button on the gamepad.</span></span>
- <span data-ttu-id="ab804-180">Da der Kunde etwa 3Meter (10 Fuß) vom Bildschirm entfernt sitzt, stellen Sie sicher, dass die Benutzeroberfläche groß genug und klar sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="ab804-180">Since the customer is sitting approximately 10 feet away from the screen, make sure that UI is large and clear enough to be visible.</span></span>

<span data-ttu-id="ab804-181">Eingaben</span><span class="sxs-lookup"><span data-stu-id="ab804-181">Inputs</span></span>
- <span data-ttu-id="ab804-182">Gamepad (z.B. Xbox-Controller)</span><span class="sxs-lookup"><span data-stu-id="ab804-182">Gamepad (such as an Xbox controller)</span></span>
- <span data-ttu-id="ab804-183">Fernbedienung</span><span class="sxs-lookup"><span data-stu-id="ab804-183">Remote</span></span>
- <span data-ttu-id="ab804-184">Sprache (gelegentlich, falls der Kunde Kinect oder ein Headset besitzt)</span><span class="sxs-lookup"><span data-stu-id="ab804-184">Voice (occasionally, if the customer has a Kinect or headset)</span></span>

<span data-ttu-id="ab804-185">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-185">Typical device capabilities</span></span>
- <span data-ttu-id="ab804-186">Kamera (gelegentlich, falls der Kunde Kinect besitzt)</span><span class="sxs-lookup"><span data-stu-id="ab804-186">Camera (occasionally, if the customer has a Kinect)</span></span>
- <span data-ttu-id="ab804-187">Mikrofon (gelegentlich, falls der Kunde Kinect oder ein Headset besitzt)</span><span class="sxs-lookup"><span data-stu-id="ab804-187">Microphone (occasionally, if the customer has a Kinect or headset)</span></span>
- <span data-ttu-id="ab804-188">Bewegungssensoren (gelegentlich, falls der Kunde Kinect besitzt)</span><span class="sxs-lookup"><span data-stu-id="ab804-188">Movement sensors (occasionally, if the customer has a Kinect)</span></span>

## <a name="phones-and-phablets"></a><span data-ttu-id="ab804-189">Smartphones und Phablets</span><span class="sxs-lookup"><span data-stu-id="ab804-189">Phones and phablets</span></span>


<span data-ttu-id="ab804-190">Smartphones sind mittlerweile die am häufigsten genutzten Geräte und bieten auch bei begrenzter Bildschirmfläche und eingeschränkten Eingabeverfahren viele Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="ab804-190">The most widely-used of all computing devices, phones can do a lot with limited screen real estate and basic inputs.</span></span> <span data-ttu-id="ab804-191">Smartphones sind in zahlreichen verschiedenen Größen verfügbar. Größere Handys werden als Phablets bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ab804-191">Phones are available in a variety of sizes; larger phones are called phablets.</span></span> <span data-ttu-id="ab804-192">App-Benutzeroberflächen auf Phablets ähneln den Benutzeroberflächen auf Smartphones, aber die größere Bildschirmfläche von Phablets ermöglicht einige wichtige Änderungen bei der Nutzung von Inhalten.</span><span class="sxs-lookup"><span data-stu-id="ab804-192">App experiences on phablets are similar to those on phones, but the increased screen real estate of phablets enable some key changes in content consumption.</span></span>

<span data-ttu-id="ab804-193">Mit Continuum für Smartphones, einem neuen Angebot für kompatible Windows 10-Mobilgeräte, können Benutzer ihre Smartphones an einen Bildschirm anschließen und sogar Maus und Tastatur verwenden, damit ihr Gerät wie einen Laptop.</span><span class="sxs-lookup"><span data-stu-id="ab804-193">With Continuum for Phones, a new experience for compatible Windows10 mobile devices, users can connect their phones to a monitor and even use a mouse and keyboard to make their phones work like a laptop.</span></span> <span data-ttu-id="ab804-194">(Weitere Informationen finden Sie im [Artikel zu Continuum für Smartphones](http://go.microsoft.com/fwlink/p/?LinkID=699431).)</span><span class="sxs-lookup"><span data-stu-id="ab804-194">(For more info, see the [Continuum for Phone article](http://go.microsoft.com/fwlink/p/?LinkID=699431).)</span></span>

<span data-ttu-id="ab804-195">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-195">Screen sizes</span></span>
-   <span data-ttu-id="ab804-196">4 bis 5 Zoll bei Smartphones</span><span class="sxs-lookup"><span data-stu-id="ab804-196">4'' to 5'' for phone</span></span>
-   <span data-ttu-id="ab804-197">5,5 bis 7 Zoll bei Phablets</span><span class="sxs-lookup"><span data-stu-id="ab804-197">5.5'' to 7'' for phablet</span></span>

![Windows Phone](images/device-primer/device-primer-phablet.png)

<span data-ttu-id="ab804-199">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-199">Typical usage</span></span>
-   <span data-ttu-id="ab804-200">Smartphones werden meist im Hochformat bedient, weil es am einfachsten ist, das Gerät in einer Hand zu halten und so alle Interaktionsmöglichkeiten zu nutzen. In manchen Fällen funktioniert jedoch das Querformat sehr gut, beispielsweise beim Anzeigen von Fotos und Videos, beim Lesen eines Buchs oder beim Verfassen von Text.</span><span class="sxs-lookup"><span data-stu-id="ab804-200">Primarily used in portrait orientation, mostly due to the ease of holding the phone with one hand and being able to fully interact with it that way, but there are some experiences that work well in landscape, such as viewing photos and video, reading a book, and composing text.</span></span>
-   <span data-ttu-id="ab804-201">Ein Smartphone wird meist nur von einer Person, also dem Besitzer des Geräts, verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-201">Mostly used by just one person, the owner of the device.</span></span>
-   <span data-ttu-id="ab804-202">Es ist immer in Reichweite und wird in der Regel in der Hosentasche oder einer Tasche verstaut.</span><span class="sxs-lookup"><span data-stu-id="ab804-202">Always within reach, usually stashed in a pocket or a bag.</span></span>
-   <span data-ttu-id="ab804-203">Es wird eher über kürzere Zeiträume verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-203">Used for brief periods of time.</span></span>
-   <span data-ttu-id="ab804-204">Das Smartphone wird vom Benutzer häufig zum Multitasking verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab804-204">Users are often multitasking when using the phone.</span></span>
-   <span data-ttu-id="ab804-205">Text wird häufig und jeweils nur für kurze Zeit eingegeben.</span><span class="sxs-lookup"><span data-stu-id="ab804-205">Text is entered in short bursts.</span></span>

<span data-ttu-id="ab804-206">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-206">UI considerations</span></span>
-   <span data-ttu-id="ab804-207">Auf dem Smartphone kann aufgrund der geringen Bildschirmgröße sowohl im Hochformat als auch im Querformat jeweils nur ein Frame angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ab804-207">The small size of a phone's screen allows only one frame at a time to be viewed in both portrait and landscape orientations.</span></span> <span data-ttu-id="ab804-208">Für alle hierarchischen Navigationsmuster auf einem Smartphone wird das Drilldown-Modell verwendet, bei dem Benutzer durch UI-Ebenen mit einzelnen Frames navigieren.</span><span class="sxs-lookup"><span data-stu-id="ab804-208">All hierarchical navigation patterns on a phone use the "drill" model, with the user navigating through single-frame UI layers.</span></span>

-   <span data-ttu-id="ab804-209">Bei Phablets ist es ähnlich wie bei Smartphones, denn im Hochformat kann auch hier nur jeweils ein Frame angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ab804-209">Similar to phones, phablets in portrait mode can view only one frame at a time.</span></span> <span data-ttu-id="ab804-210">Da auf einem Phablet eine größere Bildschirmfläche verfügbar ist, können Benutzer ins Querformat wechseln und dieses Format beibehalten, damit gleichzeitig zwei App-Frames angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="ab804-210">But with the greater screen real estate available on a phablet, users have the ability to rotate to landscape orientation and stay there, so two app frames can be visible at a time.</span></span>

-   <span data-ttu-id="ab804-211">Achten Sie darauf, dass sowohl im Querformat als auch im Hochformat genügend Bildschirmfläche für die App-Leiste vorhanden ist, wenn die Bildschirmtastatur aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ab804-211">In both landscape and portrait orientations, be sure that there's enough screen real estate for the app bar when the on-screen keyboard is up.</span></span>

<span data-ttu-id="ab804-212">Eingabemöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ab804-212">Inputs</span></span>
-   <span data-ttu-id="ab804-213">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="ab804-213">Touch</span></span>
-   <span data-ttu-id="ab804-214">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="ab804-214">Voice</span></span>

<span data-ttu-id="ab804-215">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-215">Typical device capabilities</span></span>
-   <span data-ttu-id="ab804-216">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="ab804-216">Microphone</span></span>
-   <span data-ttu-id="ab804-217">Kamera</span><span class="sxs-lookup"><span data-stu-id="ab804-217">Camera</span></span>
-   <span data-ttu-id="ab804-218">Bewegungssensoren</span><span class="sxs-lookup"><span data-stu-id="ab804-218">Movement sensors</span></span>
-   <span data-ttu-id="ab804-219">Positionssensoren</span><span class="sxs-lookup"><span data-stu-id="ab804-219">Location sensors</span></span>

 

## <a name="surface-hub-devices"></a><span data-ttu-id="ab804-220">SurfaceHub-Geräte</span><span class="sxs-lookup"><span data-stu-id="ab804-220">Surface Hub devices</span></span>


<span data-ttu-id="ab804-221">Microsoft Surface Hub ist ein Gerät für die Zusammenarbeit mit großem Bildschirm, der für die gleichzeitige Verwendung durch mehrere Benutzer konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="ab804-221">Microsoft Surface Hub is a large-screen team collaboration device designed for simultaneous use by multiple users.</span></span>

<span data-ttu-id="ab804-222">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-222">Screen sizes</span></span>
-   <span data-ttu-id="ab804-223">55 und 84 Zoll</span><span class="sxs-lookup"><span data-stu-id="ab804-223">55” and 84''</span></span>

![Surface Hub](images/device-primer/device-primer-surfacehub3.png)

<span data-ttu-id="ab804-225">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-225">Typical usage</span></span>
-   <span data-ttu-id="ab804-226">Apps auf dem Surface Hub dienen der gemeinsamen Nutzung für kurze Zeit, z. B. bei Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="ab804-226">Apps on Surface Hub see shared use for short periods of time, such as in meetings.</span></span>

-   <span data-ttu-id="ab804-227">Surface Hub-Geräte befinden sich überwiegend an einem Ort und werden nur selten bewegt.</span><span class="sxs-lookup"><span data-stu-id="ab804-227">Surface Hub devices are mostly stationary and rarely moved.</span></span>

<span data-ttu-id="ab804-228">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-228">UI considerations</span></span>
-   <span data-ttu-id="ab804-229">Apps auf dem Surface Hub können in vier Zuständen angezeigt werden: Vollbild (standardmäßige Vollbildansicht), Hintergrund (ausgeblendet, während die App weiterhin ausgeführt wird, verfügbar über die Aufgabenumschaltfunktion), Füllen (feststehende Ansicht, die den verfügbaren Aktionsbereich belegt) und Angedockt (Ansicht mit variablem Seitenverhältnis, die die rechte oder linke Seite des Aktionsbereichs belegt).</span><span class="sxs-lookup"><span data-stu-id="ab804-229">Apps on Surface Hub can appear in one of four states - full (standard full-screen view), background (hidden from view while the app is still running, available in task switcher), fill (a fixed view that occupies the available stage area), and snapped (variable view that occupies the right or left sides of the stage).</span></span>
-   <span data-ttu-id="ab804-230">Im angedockten Modus oder Füllmodus zeigt das System die Skype-Randleiste an und verkleinert die App horizontal.</span><span class="sxs-lookup"><span data-stu-id="ab804-230">In snapped mode or fill modes, the system displays the Skype sidebar and shrinks the app horizontally.</span></span>
-   <span data-ttu-id="ab804-231">Die Zurück-Schaltfläche des Systems ist optional.</span><span class="sxs-lookup"><span data-stu-id="ab804-231">System back is optional.</span></span> <span data-ttu-id="ab804-232">Wenn ein App-Entwickler diese anzeigen möchte, wird sie in der App-Titelleiste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab804-232">When an app developer chooses to show it, it appears in the app title bar.</span></span>

<span data-ttu-id="ab804-233">Eingabemöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ab804-233">Inputs</span></span>
-   <span data-ttu-id="ab804-234">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="ab804-234">Touch</span></span>
-   <span data-ttu-id="ab804-235">Stift</span><span class="sxs-lookup"><span data-stu-id="ab804-235">Pen</span></span>
-   <span data-ttu-id="ab804-236">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="ab804-236">Voice</span></span>
-   <span data-ttu-id="ab804-237">Tastatur (Bildschirm-/Remotetastatur)</span><span class="sxs-lookup"><span data-stu-id="ab804-237">Keyboard (on-screen/remote)</span></span>
-   <span data-ttu-id="ab804-238">Touchpad (Remote)</span><span class="sxs-lookup"><span data-stu-id="ab804-238">Touchpad (remote)</span></span>

<span data-ttu-id="ab804-239">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-239">Typical device capabilities</span></span>
-   <span data-ttu-id="ab804-240">Kamera</span><span class="sxs-lookup"><span data-stu-id="ab804-240">Camera</span></span>
-   <span data-ttu-id="ab804-241">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="ab804-241">Microphone</span></span>

 

## <a name="windows-iot-devices"></a><span data-ttu-id="ab804-242">WindowsIoT-Geräte</span><span class="sxs-lookup"><span data-stu-id="ab804-242">Windows IoT devices</span></span>


<span data-ttu-id="ab804-243">Bei WindowsIoT-Geräten handelt es sich um eine neue Klasse von Geräten, bei denen das Einbetten von kleinen elektronischen Geräten, Sensoren und Verbindungen in physische Objekte im Mittelpunkt steht.</span><span class="sxs-lookup"><span data-stu-id="ab804-243">Windows IoT devices are an emerging class of devices centered around embedding small electronics, sensors, and connectivity within physical objects.</span></span> <span data-ttu-id="ab804-244">Diese Geräte sind in der Regel über ein Netzwerk oder das Internet verbunden, um die erfassten realen Daten zu melden und in manchen Fällen auf diese Daten zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="ab804-244">These devices are usually connected through a network or the Internet to report on the real-world data they sense, and in some cases act on it.</span></span> <span data-ttu-id="ab804-245">Geräte können entweder keinen Bildschirm besitzen („monitorlose“ Geräte) oder an einen kleinen Bildschirm mit maximal 3,5 Zoll angeschlossen sein (Geräte mit Monitor).</span><span class="sxs-lookup"><span data-stu-id="ab804-245">Devices can either have no screen (also known as “headless” devices) or are connected to a small screen (known as “headed” devices) with a screen size usually 3.5” or smaller.</span></span>

<span data-ttu-id="ab804-246">Bildschirmgrößen</span><span class="sxs-lookup"><span data-stu-id="ab804-246">Screen sizes</span></span>
-   <span data-ttu-id="ab804-247">3,5 Zoll oder kleiner</span><span class="sxs-lookup"><span data-stu-id="ab804-247">3.5'' or smaller</span></span>
-   <span data-ttu-id="ab804-248">Manche Geräte verfügen über keinen Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="ab804-248">Some devices have no screen</span></span>

![IoT-Gerät](images/device-primer/device-primer-iot-device.png)

<span data-ttu-id="ab804-250">Typische Verwendung</span><span class="sxs-lookup"><span data-stu-id="ab804-250">Typical usage</span></span>
-   <span data-ttu-id="ab804-251">Diese Geräte sind in der Regel über ein Netzwerk oder das Internet verbunden, um die erfassten realen Daten zu melden und in manchen Fällen auf diese Daten zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="ab804-251">Usually connected through a network or the Internet to report on the real-world data they sense, and in some cases act on it.</span></span>
-   <span data-ttu-id="ab804-252">Auf diesen Geräten kann im Gegensatz zu Smartphones oder anderen größeren Geräten nur jeweils eine Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ab804-252">These devices can only run one application at a time unlike phones or other larger devices.</span></span>
-   <span data-ttu-id="ab804-253">Mit diesen Geräten wird nicht ständig interagiert, sie stehen bei Bedarf aber jederzeit zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ab804-253">It isn’t something that is interacted with all the time, but instead is available when you need it, out of the way when you don’t.</span></span>
-   <span data-ttu-id="ab804-254">Die App besitzt keinen dedizierten Zurück-Befehl, dafür ist der Entwickler zuständig.</span><span class="sxs-lookup"><span data-stu-id="ab804-254">App doesn’t have a dedicated back affordance, that is the developers responsibility.</span></span>

<span data-ttu-id="ab804-255">Hinweise zur Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ab804-255">UI considerations</span></span>
-   <span data-ttu-id="ab804-256">Monitorlose Geräte besitzen keinen Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="ab804-256">"headless" devices have no screen.</span></span>
-   <span data-ttu-id="ab804-257">Die Anzeige bei Geräten mit Monitor ist sehr klein. Aufgrund der begrenzten Bildschirmfläche und der eingeschränkten Funktionen werden nur notwendige Inhalte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab804-257">Display for “headed” devices is minimal, only showing what is necessary due to limited screen real estate and functionality.</span></span>
-   <span data-ttu-id="ab804-258">Die Ausrichtung ist in den meisten Fällen gesperrt, sodass Sie bei Ihrer App nur eine Anzeigerichtung berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="ab804-258">Orientation is most times locked, so your app only needs to consider one display direction.</span></span>

<span data-ttu-id="ab804-259">Eingabemöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="ab804-259">Inputs</span></span>
-   <span data-ttu-id="ab804-260">Variabel, abhängig vom Gerät</span><span class="sxs-lookup"><span data-stu-id="ab804-260">Variable, depending on the device</span></span>

<span data-ttu-id="ab804-261">Typische Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="ab804-261">Typical device capabilities</span></span>
-   <span data-ttu-id="ab804-262">Variabel, abhängig vom Gerät</span><span class="sxs-lookup"><span data-stu-id="ab804-262">Variable, depending on the device</span></span>