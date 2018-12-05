---
title: Optimieren der Eingabelatenz für UWP-DirectX-Spiele
description: Die Eingabelatenz kann das Spielerlebnis erheblich beeinträchtigen. Spiele wirken professioneller, wenn in diesem Bereich eine Optimierung vorgenommen wird.
ms.assetid: e18cd1a8-860f-95fb-098d-29bf424de0c0
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Directx, Eingabelatenz
ms.localizationpriority: medium
ms.openlocfilehash: 537dd6e9d3f300666a0692b66f422ce00dd68460
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8737684"
---
#  <a name="optimize-input-latency-for-universal-windows-platform-uwp-directx-games"></a><span data-ttu-id="7f48f-104">Optimieren der Eingabelatenz für UWP-DirectX-Spiele (Universelle Windows-Plattform)</span><span class="sxs-lookup"><span data-stu-id="7f48f-104">Optimize input latency for Universal Windows Platform (UWP) DirectX games</span></span>



<span data-ttu-id="7f48f-105">Die Eingabelatenz kann das Spielerlebnis erheblich beeinträchtigen. Spiele wirken professioneller, wenn in diesem Bereich eine Optimierung vorgenommen wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-105">Input latency can significantly impact the experience of a game, and optimizing it can make a game feel more polished.</span></span> <span data-ttu-id="7f48f-106">Außerdem kann eine richtige Optimierung der Eingabeereignisse zu einer besseren Akkulaufzeit führen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-106">Additionally, proper input event optimization can improve battery life.</span></span> <span data-ttu-id="7f48f-107">Hier erfahren Sie, wie Sie die richtigen Verarbeitungsoptionen für CoreDispatcher-Eingabeereignisse auswählen, um sicherzustellen, dass die Eingaben im Spiel so reibungslos wie möglich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-107">Learn how to choose the right CoreDispatcher input event processing options to make sure your game handles input as smoothly as possible.</span></span>

## <a name="input-latency"></a><span data-ttu-id="7f48f-108">Eingabelatenz</span><span class="sxs-lookup"><span data-stu-id="7f48f-108">Input latency</span></span>


<span data-ttu-id="7f48f-109">Die Eingabelatenz ist der Zeitraum, den das System benötigt, um auf Benutzereingaben zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="7f48f-109">Input latency is the time it takes for the system to respond to user input.</span></span> <span data-ttu-id="7f48f-110">Die Reaktion ist häufig eine Änderung der Anzeige auf dem Bildschirm oder der Audioausgabe.</span><span class="sxs-lookup"><span data-stu-id="7f48f-110">The response is often a change in what's displayed on the screen, or what's heard through audio feedback.</span></span>

<span data-ttu-id="7f48f-111">Jedes Eingabeereignis – ob über einen Toucheingabezeiger, einen Mauszeiger oder eine Tastatur – generiert eine Nachricht, die von einem Ereignishandler bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-111">Every input event, whether it comes from a touch pointer, mouse pointer, or keyboard, generates a message to be processed by an event handler.</span></span> <span data-ttu-id="7f48f-112">Moderne Touchdigitalisierungsgeräte und Gaming-Peripheriegeräte melden Eingabeereignisse mit mindestens 100 Hz pro Zeiger. Dies bedeutet, dass Ihre App pro Sekunde pro Zeiger (oder Tastaturanschlag) mindestens 100 Ereignisse empfangen kann.</span><span class="sxs-lookup"><span data-stu-id="7f48f-112">Modern touch digitizers and gaming peripherals report input events at a minimum of 100 Hz per pointer, which means that apps can receive 100 events or more per second per pointer (or keystroke).</span></span> <span data-ttu-id="7f48f-113">Diese Aktualisierungsrate wird noch verstärkt, wenn mehrere Zeiger gleichzeitig oder ein Eingabegerät mit höherer Präzision (z. B. eine Gamingmaus) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-113">This rate of updates is amplified if multiple pointers are happening concurrently, or a higher precision input device is used (for example, a gaming mouse).</span></span> <span data-ttu-id="7f48f-114">Die Warteschlange für Ereignismeldungen kann sich also sehr schnell füllen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-114">The event message queue can fill up very quickly.</span></span>

<span data-ttu-id="7f48f-115">Es ist wichtig, dass Sie für Ihr Spiel die Anforderungen an die Eingabelatenz verstehen, damit Ereignisse für den jeweiligen Fall auf bestmögliche Weise verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-115">It's important to understand the input latency demands of your game so that events are processed in a way that is best for the scenario.</span></span> <span data-ttu-id="7f48f-116">Es gibt keine Standardlösung für alle Spiele.</span><span class="sxs-lookup"><span data-stu-id="7f48f-116">There is no one solution for all games.</span></span>

## <a name="power-efficiency"></a><span data-ttu-id="7f48f-117">Effiziente Nutzung der Energie</span><span class="sxs-lookup"><span data-stu-id="7f48f-117">Power efficiency</span></span>


<span data-ttu-id="7f48f-118">Im Zusammenhang mit der Eingabelatenz geht es bei der effizienten Nutzung der Energie darum, wie stark die GPU vom Spiel genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-118">In the context of input latency, "power efficiency" refers to how much a game uses the GPU.</span></span> <span data-ttu-id="7f48f-119">Ein Spiel, bei dem weniger GPU-Ressourcen genutzt werden, ist energieeffizienter und ermöglicht eine längere Akkulaufzeit.</span><span class="sxs-lookup"><span data-stu-id="7f48f-119">A game that uses less GPU resources is more power efficient and allows for longer battery life.</span></span> <span data-ttu-id="7f48f-120">Dies gilt auch für die CPU.</span><span class="sxs-lookup"><span data-stu-id="7f48f-120">This also holds true for the CPU.</span></span>

<span data-ttu-id="7f48f-121">Wenn ein Spiel den gesamten Bildschirm mit weniger als 60Frames pro Sekunde zeichnen kann (derzeit die maximale Rendergeschwindigkeit der meisten Displays), ohne das Spielerlebnis zu beeinträchtigen, ist die Energieeffizienz höher, weil weniger oft gezeichnet werden muss.</span><span class="sxs-lookup"><span data-stu-id="7f48f-121">If a game can draw the whole screen at less than 60 frames per second (currently, the maximum rendering speed on most displays) without degrading the user's experience, it will be more power efficient by drawing less often.</span></span> <span data-ttu-id="7f48f-122">Bei einigen Spielen wird der Bildschirm nur als Reaktion auf Benutzereingaben aktualisiert, sodass die gleichen Inhalte nicht immer wieder mit 60Frames pro Sekunde gezeichnet werden müssen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-122">Some games only update the screen in response to user input, so those games should not draw the same content repeatedly at 60 frames per second.</span></span>

## <a name="choosing-what-to-optimize-for"></a><span data-ttu-id="7f48f-123">Auswählen der Optimierungsziele</span><span class="sxs-lookup"><span data-stu-id="7f48f-123">Choosing what to optimize for</span></span>


<span data-ttu-id="7f48f-124">Beim Entwerfen einer DirectX-App müssen Sie einige Entscheidungen treffen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-124">When designing a DirectX app, you need to make some choices.</span></span> <span data-ttu-id="7f48f-125">Müssen für die App 60Frames pro Sekunde gerendert werden, um eine reibungslose Animation zu gewährleisten, oder muss nur als Reaktion auf Eingaben gerendert werden?</span><span class="sxs-lookup"><span data-stu-id="7f48f-125">Does the app need to render 60 frames per second to present smooth animation, or does it only need to render in response to input?</span></span> <span data-ttu-id="7f48f-126">Muss die geringstmögliche Eingabelatenz verwendet werden, oder ist eine kurze Verzögerung tolerierbar?</span><span class="sxs-lookup"><span data-stu-id="7f48f-126">Does it need to have the lowest possible input latency, or can it tolerate a little bit of delay?</span></span> <span data-ttu-id="7f48f-127">Erwarten die Benutzer, dass bei der App auf die Akkunutzung geachtet wird?</span><span class="sxs-lookup"><span data-stu-id="7f48f-127">Will my users expect my app to be judicious about battery usage?</span></span>

<span data-ttu-id="7f48f-128">Die Antworten auf diese Fragen führen für die App in der Regel zu einem der folgenden Fälle:</span><span class="sxs-lookup"><span data-stu-id="7f48f-128">The answers to these questions will likely align your app with one of the following scenarios:</span></span>

1.  <span data-ttu-id="7f48f-129">Rendern bei Bedarf:</span><span class="sxs-lookup"><span data-stu-id="7f48f-129">Render on demand.</span></span> <span data-ttu-id="7f48f-130">Für Spiele dieser Kategorie muss der Bildschirm nur als Reaktion auf bestimmte Arten von Eingaben aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-130">Games in this category only need to update the screen in response to specific types of input.</span></span> <span data-ttu-id="7f48f-131">Die Energieeffizienz ist sehr gut, weil von der App identische Frames nicht immer wieder gerendert werden, und die Eingabelatenz ist niedrig, da die App die meiste Zeit mit dem Warten auf eine Eingabe verbringt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-131">Power efficiency is excellent because the app doesn’t render identical frames repeatedly, and input latency is low because the app spends most of its time waiting for input.</span></span> <span data-ttu-id="7f48f-132">Brettspiele und Newsreader sind Beispiele für Apps, die ggf. in diese Kategorie fallen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-132">Board games and news readers are examples of apps that might fall into this category.</span></span>
2.  <span data-ttu-id="7f48f-133">Rendern bei Bedarf mit kurzlebigen Animationen</span><span class="sxs-lookup"><span data-stu-id="7f48f-133">Render on demand with transient animations.</span></span> <span data-ttu-id="7f48f-134">Dieser Fall ähnelt dem ersten Fall, mit der Ausnahme, dass bestimmte Arten von Eingaben eine Animation auslösen, die nicht von Folgeeingaben des Benutzers abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="7f48f-134">This scenario is similar to the first scenario except that certain types of input will start an animation that isn’t dependent on subsequent input from the user.</span></span> <span data-ttu-id="7f48f-135">Die Energieeffizienz ist gut, weil identische Frames vom Spiel nicht immer wieder gerendert werden, und die Eingabelatenz ist niedrig, während im Spiel keine Animationen aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="7f48f-135">Power efficiency is good because the game doesn’t render identical frames repeatedly, and input latency is low while the game is not animating.</span></span> <span data-ttu-id="7f48f-136">Interaktive Spiele für Kinder und Brettspiele, bei denen jeder Zug animiert ist, sind Beispiele für Apps, die ggf. in diese Kategorie fallen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-136">Interactive children’s games and board games that animate each move are examples of apps that might fall into this category.</span></span>
3.  <span data-ttu-id="7f48f-137">Rendern von 60Frames pro Sekunde:</span><span class="sxs-lookup"><span data-stu-id="7f48f-137">Render 60 frames per second.</span></span> <span data-ttu-id="7f48f-138">In diesem Fall wird der Bildschirm vom Spiel ständig aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="7f48f-138">In this scenario, the game is constantly updating the screen.</span></span> <span data-ttu-id="7f48f-139">Die Energieeffizienz ist nicht gut, weil die maximale Anzahl Frames, die vom Display dargestellt werden kann, gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-139">Power efficiency is poor because it renders the maximum number of frames the display can present.</span></span> <span data-ttu-id="7f48f-140">Die Eingabelatenz ist hoch, da der Thread während der Darstellung der Inhalte von DirectX blockiert wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-140">Input latency is high because DirectX blocks the thread while content is being presented.</span></span> <span data-ttu-id="7f48f-141">So wird der Thread daran gehindert, mehr Frames an das Display zu senden, als dem Benutzer angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="7f48f-141">Doing so prevents the thread from sending more frames to the display than it can show to the user.</span></span> <span data-ttu-id="7f48f-142">Ego-Shooter, Echtzeit-Strategiespiele und Spiele auf physischer Basis sind Beispiele für Apps, die ggf. in diese Kategorie fallen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-142">First person shooters, real-time strategy games, and physics-based games are examples of apps that might fall into this category.</span></span>
4.  <span data-ttu-id="7f48f-143">Rendern von 60Frames pro Sekunde und Erzielen der geringstmöglichen Eingabelatenz</span><span class="sxs-lookup"><span data-stu-id="7f48f-143">Render 60 frames per second and achieve the lowest possible input latency.</span></span> <span data-ttu-id="7f48f-144">Die App aktualisiert den Bildschirm, ähnlich wie im dritten Fall, ständig, und die Energieeffizienz ist schlecht.</span><span class="sxs-lookup"><span data-stu-id="7f48f-144">Similar to scenario 3, the app is constantly updating the screen, so power efficiency will be poor.</span></span> <span data-ttu-id="7f48f-145">Der Unterschied besteht darin, dass das Spiel über einen separaten Thread auf Eingaben reagiert. Daher wird die Eingabeverarbeitung beim Darstellen von Grafiken auf dem Display nicht blockiert.</span><span class="sxs-lookup"><span data-stu-id="7f48f-145">The difference is that the game responds to input on a separate thread, so that input processing isn’t blocked by presenting graphics to the display.</span></span> <span data-ttu-id="7f48f-146">Onlinespiele mit mehreren Spielern, Kampfspiele oder Spiele auf Rhythmus- bzw. Zeitbasis fallen ggf. in diese Kategorie, da Eingaben innerhalb von extrem engen Ereignisfenstern unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-146">Online multiplayer games, fighting games, or rhythm/timing games might fall into this category because they support move inputs within extremely tight event windows.</span></span>

## <a name="implementation"></a><span data-ttu-id="7f48f-147">Implementierung</span><span class="sxs-lookup"><span data-stu-id="7f48f-147">Implementation</span></span>


<span data-ttu-id="7f48f-148">Die meisten DirectX-Spiele basieren auf der so genannten Spielschleife.</span><span class="sxs-lookup"><span data-stu-id="7f48f-148">Most DirectX games are driven by what is known as the game loop.</span></span> <span data-ttu-id="7f48f-149">Der grundlegende Algorithmus besteht darin, die folgenden Schritte auszuführen, bis der Benutzer das Spiel oder die App beendet:</span><span class="sxs-lookup"><span data-stu-id="7f48f-149">The basic algorithm is to perform these steps until the user quits the game or app:</span></span>

1.  <span data-ttu-id="7f48f-150">Eingabe verarbeiten</span><span class="sxs-lookup"><span data-stu-id="7f48f-150">Process input</span></span>
2.  <span data-ttu-id="7f48f-151">Spielzustand aktualisieren</span><span class="sxs-lookup"><span data-stu-id="7f48f-151">Update the game state</span></span>
3.  <span data-ttu-id="7f48f-152">Inhalte des Spiels zeichnen</span><span class="sxs-lookup"><span data-stu-id="7f48f-152">Draw the game content</span></span>

<span data-ttu-id="7f48f-153">Wenn die Inhalte eines DirectX-Spiels gerendert und bereit für die Darstellung auf dem Bildschirm sind, wartet die Spielschleife, bis die GPU einen neuen Frame empfangen kann, bevor erneut Eingaben verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-153">When the content of a DirectX game is rendered and ready to be presented to the screen, the game loop waits until the GPU is ready to receive a new frame before waking up to process input again.</span></span>

<span data-ttu-id="7f48f-154">Die Implementierung der Spielschleife wird unten für die einzelnen beschriebenen Fälle veranschaulicht, indem der Prozess eines einfachen Puzzlespiels durchlaufen wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-154">We’ll show the implementation of the game loop for each of the scenarios mentioned earlier by iterating on a simple jigsaw puzzle game.</span></span> <span data-ttu-id="7f48f-155">Die Entscheidungspunkte, Vorteile und Nachteile, die Teil jeder Implementierung sind, dienen Ihnen als Unterstützung beim Optimieren Ihrer Apps in Bezug auf eine niedrige Eingabelatenz und eine hohe Energieeffizienz.</span><span class="sxs-lookup"><span data-stu-id="7f48f-155">The decision points, benefits, and tradeoffs discussed with each implementation can serve as a guide to help you optimize your apps for low latency input and power efficiency.</span></span>

## <a name="scenario-1-render-on-demand"></a><span data-ttu-id="7f48f-156">Szenario1: Rendern bei Bedarf</span><span class="sxs-lookup"><span data-stu-id="7f48f-156">Scenario 1: Render on demand</span></span>


<span data-ttu-id="7f48f-157">Beim ersten Durchlauf des Puzzlespiels wird der Bildschirm nur aktualisiert, wenn ein Benutzer ein Puzzleteil verschiebt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-157">The first iteration of the jigsaw puzzle game only updates the screen when a user moves a puzzle piece.</span></span> <span data-ttu-id="7f48f-158">Benutzer können ein Puzzleteil entweder an seinen Platz ziehen oder das Teil auswählen und dann auf die richtige Position tippen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-158">A user can either drag a puzzle piece into place or snap it into place by selecting it and then touching the correct destination.</span></span> <span data-ttu-id="7f48f-159">Im letzteren Fall wird das Puzzleteil ohne Animation oder Effekte eingefügt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-159">In the second case, the puzzle piece will jump to the destination with no animation or effects.</span></span>

<span data-ttu-id="7f48f-160">Der Code umfasst eine Spielschleife mit einem einzelnen Thread in der [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505)-Methode, für die das **CoreProcessEventsOption::ProcessOneAndAllPending**-Element verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-160">The code has a single-threaded game loop within the [**IFrameworkView::Run**](https://msdn.microsoft.com/library/windows/apps/hh700505) method that uses **CoreProcessEventsOption::ProcessOneAndAllPending**.</span></span> <span data-ttu-id="7f48f-161">Mit dieser Option werden alle derzeit verfügbaren Ereignisse in der Warteschlange verteilt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-161">Using this option dispatches all currently available events in the queue.</span></span> <span data-ttu-id="7f48f-162">Falls keine Ereignisse ausstehen, wartet die Spielschleife, bis ein Ereignis vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7f48f-162">If no events are pending, the game loop waits until one appears.</span></span>

``` syntax
void App::Run()
{
    
    while (!m_windowClosed)
    {
        // Wait for system events or input from the user.
        // ProcessOneAndAllPending will block the thread until events appear and are processed.
        CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);

        // If any of the events processed resulted in a need to redraw the window contents, then we will re-render the
        // scene and present it to the display.
        if (m_updateWindow || m_state->StateChanged())
        {
            m_main->Render();
            m_deviceResources->Present();

            m_updateWindow = false;
            m_state->Validate();
        }
    }
}
```

## <a name="scenario-2-render-on-demand-with-transient-animations"></a><span data-ttu-id="7f48f-163">Szenario2: Rendern bei Bedarf mit kurzlebigen Animationen</span><span class="sxs-lookup"><span data-stu-id="7f48f-163">Scenario 2: Render on demand with transient animations</span></span>


<span data-ttu-id="7f48f-164">Beim zweiten Durchlauf wird das Spiel modifiziert. Wenn Benutzer ein Puzzleteil auswählen und dann auf die richtige Position für das Teil tippen, wird es auf dem Bildschirm per Animation an seine Zielposition verschoben.</span><span class="sxs-lookup"><span data-stu-id="7f48f-164">In the second iteration, the game is modified so that when a user selects a puzzle piece and then touches the correct destination for that piece, it animates across the screen until it reaches its destination.</span></span>

<span data-ttu-id="7f48f-165">Wie im ersten Szenario verfügt der Code über eine Spielschleife mit einem einzelnen Thread, die mithilfe von **ProcessOneAndAllPending** die in der Warteschlange enthaltenen Eingabeereignisse verteilt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-165">As before, the code has a single-threaded game loop that uses **ProcessOneAndAllPending** to dispatch input events in the queue.</span></span> <span data-ttu-id="7f48f-166">Der Unterschied besteht jetzt darin, dass die Schleife während der Animation zu **CoreProcessEventsOption::ProcessAllIfPresent**, damit nicht auf neue Eingabeereignisse gewartet wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-166">The difference now is that during an animation, the loop changes to use **CoreProcessEventsOption::ProcessAllIfPresent** so that it doesn’t wait for new input events.</span></span> <span data-ttu-id="7f48f-167">Wenn keine Ereignisse ausstehen, erfolgt die Rückgabe für [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) sofort, und die App kann den nächsten Frame der Animation darstellen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-167">If no events are pending, [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) returns immediately and allows the app to present the next frame in the animation.</span></span> <span data-ttu-id="7f48f-168">Nachdem die Animation abgeschlossen ist, wechselt die Schleife zurück zu **ProcessOneAndAllPending**, um die Bildschirmaktualisierungen zu begrenzen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-168">When the animation is complete, the loop switches back to **ProcessOneAndAllPending** to limit screen updates.</span></span>

``` syntax
void App::Run()
{

    while (!m_windowClosed)
    {
        // 2. Switch to a continuous rendering loop during the animation.
        if (m_state->Animating())
        {
            // Process any system events or input from the user that is currently queued.
            // ProcessAllIfPresent will not block the thread to wait for events. This is the desired behavior when
            // you are trying to present a smooth animation to the user.
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            m_state->Update();
            m_main->Render();
            m_deviceResources->Present();
        }
        else
        {
            // Wait for system events or input from the user.
            // ProcessOneAndAllPending will block the thread until events appear and are processed.
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);

            // If any of the events processed resulted in a need to redraw the window contents, then we will re-render the
            // scene and present it to the display.
            if (m_updateWindow || m_state->StateChanged())
            {
                m_main->Render();
                m_deviceResources->Present();

                m_updateWindow = false;
                m_state->Validate();
            }
        }
    }
}
```

<span data-ttu-id="7f48f-169">Zur Unterstützung des Übergangs zwischen **ProcessOneAndAllPending** und **ProcessAllIfPresent** muss der Status von der App nachverfolgt werden, um ermitteln zu können, ob die Animation aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="7f48f-169">To support the transition between **ProcessOneAndAllPending** and **ProcessAllIfPresent**, the app must track state to know if it’s animating.</span></span> <span data-ttu-id="7f48f-170">In der Puzzle-App fügen Sie dazu eine neue Methode hinzu, die während der Spielschleife für die GameState-Klasse aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7f48f-170">In the jigsaw puzzle app, you do this by adding a new method that can be called during the game loop on the GameState class.</span></span> <span data-ttu-id="7f48f-171">Der Animationszweig der Spielschleife bewirkt die Aktualisierungen des Animationsstatus, indem die neue Update-Methode für GameState aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-171">The animation branch of the game loop drives updates in the state of the animation by calling GameState’s new Update method.</span></span>

## <a name="scenario-3-render-60-frames-per-second"></a><span data-ttu-id="7f48f-172">Szenario3: Rendern von 60Frames pro Sekunde</span><span class="sxs-lookup"><span data-stu-id="7f48f-172">Scenario 3: Render 60 frames per second</span></span>


<span data-ttu-id="7f48f-173">Beim dritten Durchlauf zeigt die App einen Zeitgeber an, um Benutzern mitzuteilen, wie lange sie bereits an der Lösung des Puzzles gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="7f48f-173">In the third iteration, the app displays a timer that shows the user how long they’ve been working on the puzzle.</span></span> <span data-ttu-id="7f48f-174">Da die verstrichene Dauer bis auf Millisekunden genau angegeben wird, müssen 60Frames pro Sekunde gerendert werden, um die Anzeige aktuell zu halten.</span><span class="sxs-lookup"><span data-stu-id="7f48f-174">Because it displays the elapsed time up to the millisecond, it must render 60 frames per second to keep the display up to date.</span></span>

<span data-ttu-id="7f48f-175">Wie in den Szenarien1 und2 auch, verfügt die App über eine Spielschleife mit einem einzelnen Thread.</span><span class="sxs-lookup"><span data-stu-id="7f48f-175">As in scenarios 1 and 2, the app has a single-threaded game loop.</span></span> <span data-ttu-id="7f48f-176">Bei diesem Szenario besteht der Unterschied darin, dass aufgrund des ständigen Renderns keine Änderungen des Spielstatus mehr nachverfolgt werden müssen, wie dies bei den ersten beiden Szenarien der Fall war.</span><span class="sxs-lookup"><span data-stu-id="7f48f-176">The difference with this scenario is that because it’s always rendering, it no longer needs to track changes in the game state as was done in the first two scenarios.</span></span> <span data-ttu-id="7f48f-177">Daher kann für die Verarbeitung von Ereignissen standardmäßig **ProcessAllIfPresent** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7f48f-177">As a result, it can default to use **ProcessAllIfPresent** for processing events.</span></span> <span data-ttu-id="7f48f-178">Wenn keine Ereignisse ausstehen, erfolgt die Rückgabe für **ProcessEvents** sofort, und es wird mit dem Rendern des nächsten Frames fortgefahren.</span><span class="sxs-lookup"><span data-stu-id="7f48f-178">If no events are pending, **ProcessEvents** returns immediately and proceeds to render the next frame.</span></span>

``` syntax
void App::Run()
{

    while (!m_windowClosed)
    {
        if (m_windowVisible)
        {
            // 3. Continuously render frames and process system events and input as they appear in the queue.
            // ProcessAllIfPresent will not block the thread to wait for events. This is the desired behavior when
            // trying to present smooth animations to the user.
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);

            m_state->Update();
            m_main->Render();
            m_deviceResources->Present();
        }
        else
        {
            // 3. If the window isn't visible, there is no need to continuously render.
            // Process events as they appear until the window becomes visible again.
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
}
```

<span data-ttu-id="7f48f-179">Dieser Ansatz ist die einfachste Möglichkeit, ein Spiel zu schreiben, da für die Ermittlung des Renderzeitpunkts kein weiterer Status nachverfolgt werden muss.</span><span class="sxs-lookup"><span data-stu-id="7f48f-179">This approach is the easiest way to write a game because there’s no need to track additional state to determine when to render.</span></span> <span data-ttu-id="7f48f-180">Dabei werden die kürzestmöglichen Renderzeiträume und eine angemessene Reaktionsfähigkeit auf Eingaben pro Timerintervall erzielt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-180">It achieves the fastest rendering possible along with reasonable input responsiveness on a timer interval.</span></span>

<span data-ttu-id="7f48f-181">Die Einfachheit dieses Entwicklungsansatzes hat aber auch einen Nachteil.</span><span class="sxs-lookup"><span data-stu-id="7f48f-181">However, this ease of development comes with a price.</span></span> <span data-ttu-id="7f48f-182">Beim Rendern mit 60 Frames pro Sekunde wird mehr Energie als beim Rendern bei Bedarf verbraucht.</span><span class="sxs-lookup"><span data-stu-id="7f48f-182">Rendering at 60 frames per second uses more power than rendering on demand.</span></span> <span data-ttu-id="7f48f-183">Am besten eignet sich **ProcessAllIfPresent**, wenn die Anzeige vom Spiel für jeden Frame geändert wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-183">It’s best to use **ProcessAllIfPresent** when the game is changing what is displayed every frame.</span></span> <span data-ttu-id="7f48f-184">Außerdem wird damit die Eingabelatenz um bis zu 16,7 ms erhöht, da die App die Spielschleife nun während des Synchronisierungsintervalls des Displays und nicht bei **ProcessEvents** blockiert.</span><span class="sxs-lookup"><span data-stu-id="7f48f-184">It also increases input latency by as much as 16.7 ms because the app is now blocking the game loop on the display’s sync interval instead of on **ProcessEvents**.</span></span> <span data-ttu-id="7f48f-185">Unter Umständen werden einige Eingabeereignisse verworfen, da die Warteschlange nur einmal pro Frame (60 Hz) verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-185">Some input events might be dropped because the queue is only processed once per frame (60 Hz).</span></span>

## <a name="scenario-4-render-60-frames-per-second-and-achieve-the-lowest-possible-input-latency"></a><span data-ttu-id="7f48f-186">Szenario4: Rendern von 60Frames pro Sekunde und Erzielen der geringstmöglichen Eingabelatenz</span><span class="sxs-lookup"><span data-stu-id="7f48f-186">Scenario 4: Render 60 frames per second and achieve the lowest possible input latency</span></span>


<span data-ttu-id="7f48f-187">Bei einigen Spielen kann es möglich sein, den Anstieg der Eingabelatenz aus Szenario3 zu ignorieren oder auszugleichen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-187">Some games may be able to ignore or compensate for the increase in input latency seen in scenario 3.</span></span> <span data-ttu-id="7f48f-188">Wenn eine geringe Eingabelatenz für das Spielerlebnis und die Spielerrückmeldungen aber von entscheidender Bedeutung ist, müssen Spiele, die 60Frames pro Sekunde rendern, die Eingabe in einem separaten Thread verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7f48f-188">However, if low input latency is critical to the game’s experience and sense of player feedback, games that render 60 frames per second need to process input on a separate thread.</span></span>

<span data-ttu-id="7f48f-189">Der vierte Durchlauf des Puzzlespiels baut auf Szenario3 auf, indem die Eingabeverarbeitung und das Rendern der Grafiken aus der Spielschleife in separate Threads unterteilt wird.</span><span class="sxs-lookup"><span data-stu-id="7f48f-189">The fourth iteration of the jigsaw puzzle game builds on scenario 3 by splitting the input processing and graphics rendering from the game loop into separate threads.</span></span> <span data-ttu-id="7f48f-190">Mit der Nutzung separater Threads wird sichergestellt, dass die Eingabe durch die Grafikausgabe nicht verzögert werden kann. Der Code wird dadurch aber komplexer.</span><span class="sxs-lookup"><span data-stu-id="7f48f-190">Having separate threads for each ensures that input is never delayed by graphics output; however, the code becomes more complex as a result.</span></span> <span data-ttu-id="7f48f-191">In Szenario 4 ruft der Eingabethread [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) mit [**CoreProcessEventsOption::ProcessUntilQuit**](https://msdn.microsoft.com/library/windows/apps/br208217) auf. Damit wird auf neue Ereignisse gewartet, und alle verfügbaren Ereignisse werden verteilt.</span><span class="sxs-lookup"><span data-stu-id="7f48f-191">In scenario 4, the input thread calls [**ProcessEvents**](https://msdn.microsoft.com/library/windows/apps/br208215) with [**CoreProcessEventsOption::ProcessUntilQuit**](https://msdn.microsoft.com/library/windows/apps/br208217), which waits for new events and dispatches all available events.</span></span> <span data-ttu-id="7f48f-192">Dieses Verhalten wird beibehalten, bis das Fenster geschlossen wird oder das Spiel [**CoreWindow::Close**](https://msdn.microsoft.com/library/windows/apps/br208260) aufruft.</span><span class="sxs-lookup"><span data-stu-id="7f48f-192">It continues this behavior until the window is closed or the game calls [**CoreWindow::Close**](https://msdn.microsoft.com/library/windows/apps/br208260).</span></span>

``` syntax
void App::Run()
{
    // 4. Start a thread dedicated to rendering and dedicate the UI thread to input processing.
    m_main->StartRenderThread();

    // ProcessUntilQuit will block the thread and process events as they appear until the App terminates.
    CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessUntilQuit);
}

void JigsawPuzzleMain::StartRenderThread()
{
    // If the render thread is already running, then do not start another one.
    if (IsRendering())
    {
        return;
    }

    // Create a task that will be run on a background thread.
    auto workItemHandler = ref new WorkItemHandler([this](IAsyncAction^ action)
    {
        // Notify the swap chain that this app intends to render each frame faster
        // than the display's vertical refresh rate (typically 60 Hz). Apps that cannot
        // deliver frames this quickly should set this to 2.
        m_deviceResources->SetMaximumFrameLatency(1);

        // Calculate the updated frame and render once per vertical blanking interval.
        while (action->Status == AsyncStatus::Started)
        {
            // Execute any work items that have been queued by the input thread.
            ProcessPendingWork();

            // Take a snapshot of the current game state. This allows the renderers to work with a
            // set of values that won't be changed while the input thread continues to process events.
            m_state->SnapState();

            m_sceneRenderer->Render();
            m_deviceResources->Present();
        }

        // Ensure that all pending work items have been processed before terminating the thread.
        ProcessPendingWork();
    });

    // Run the task on a dedicated high priority background thread.
    m_renderLoopWorker = ThreadPool::RunAsync(workItemHandler, WorkItemPriority::High, WorkItemOptions::TimeSliced);
}
```

<span data-ttu-id="7f48f-193">Die Vorlage " **DirectX 11- und XAML-App (Universal Windows)** " in Microsoft Visual Studio2015 teilt die spielschleife in mehreren Threads auf ähnliche Weise.</span><span class="sxs-lookup"><span data-stu-id="7f48f-193">The **DirectX 11 and XAML App (Universal Windows)** template in Microsoft Visual Studio2015 splits the game loop into multiple threads in a similar fashion.</span></span> <span data-ttu-id="7f48f-194">Dabei wird das [**Windows::UI::Core::CoreIndependentInputSource**](https://msdn.microsoft.com/library/windows/apps/dn298460)-Objekt verwendet, um einen Thread für die Behandlung der Eingabe zu starten. Außerdem wird ein Renderthread erstellt, der unabhängig vom XAML-UI-Thread ist.</span><span class="sxs-lookup"><span data-stu-id="7f48f-194">It uses the [**Windows::UI::Core::CoreIndependentInputSource**](https://msdn.microsoft.com/library/windows/apps/dn298460) object to start a thread dedicated to handling input and also creates a rendering thread independent of the XAML UI thread.</span></span> <span data-ttu-id="7f48f-195">Weitere Informationen zu diesen Vorlagen finden Sie unter [Erstellen eines UWP- und eines DirectX-Spieleprojekts aus einer Vorlage](user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7f48f-195">For more details on these templates, read [Create a Universal Windows Platform and DirectX game project from a template](user-interface.md).</span></span>

## <a name="additional-ways-to-reduce-input-latency"></a><span data-ttu-id="7f48f-196">Weitere Möglichkeiten zur Reduzierung der Eingabelatenz</span><span class="sxs-lookup"><span data-stu-id="7f48f-196">Additional ways to reduce input latency</span></span>


### <a name="use-waitable-swap-chains"></a><span data-ttu-id="7f48f-197">Verwenden von Swapchains mit Wartemöglichkeit</span><span class="sxs-lookup"><span data-stu-id="7f48f-197">Use waitable swap chains</span></span>

<span data-ttu-id="7f48f-198">DirectX-Spiele reagieren auf Benutzereingaben mit der Aktualisierung der Inhalte, die Benutzer auf dem Bildschirm sehen.</span><span class="sxs-lookup"><span data-stu-id="7f48f-198">DirectX games respond to user input by updating what the user sees on-screen.</span></span> <span data-ttu-id="7f48f-199">Bei einem 60Hz-Display wird der Bildschirm alle 16,7ms (1Sekunde/60Frames) aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="7f48f-199">On a 60 Hz display, the screen refreshes every 16.7 ms (1 second/60 frames).</span></span> <span data-ttu-id="7f48f-200">In Abbildung1 sind der ungefähre Lebenszyklus und die Reaktion auf ein Eingabeereignis relativ zum Aktualisierungssignal nach 16,7ms (VBlank) für eine App dargestellt, die mit 60Frames pro Sekunde gerendert wird:</span><span class="sxs-lookup"><span data-stu-id="7f48f-200">Figure 1 shows the approximate life cycle and response to an input event relative to the 16.7 ms refresh signal (VBlank) for an app that renders 60 frames per second:</span></span>

<span data-ttu-id="7f48f-201">Abbildung1</span><span class="sxs-lookup"><span data-stu-id="7f48f-201">Figure 1</span></span>

![<span data-ttu-id="7f48f-202">Abbildung 1: Eingabelatenz in DirectX</span><span class="sxs-lookup"><span data-stu-id="7f48f-202">figure 1 input latency in directx</span></span> ](images/input-latency1.png)

<span data-ttu-id="7f48f-203">Windows8.1 eingeführt DXGI das **DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT** -Flag für die SwapChain, damit können apps diese Latenz leicht reduzieren, ohne dass diese die vorhandene Warteschlange leer gehalten implementieren.</span><span class="sxs-lookup"><span data-stu-id="7f48f-203">In Windows8.1, DXGI introduced the **DXGI\_SWAP\_CHAIN\_FLAG\_FRAME\_LATENCY\_WAITABLE\_OBJECT** flag for the swap chain, which allows apps to easily reduce this latency without requiring them to implement heuristics to keep the Present queue empty.</span></span> <span data-ttu-id="7f48f-204">Mit diesem Flag erstellte Swapchains werden als Swapchains mit Wartemöglichkeit bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7f48f-204">Swap chains created with this flag are referred to as waitable swap chains.</span></span> <span data-ttu-id="7f48f-205">Abbildung2 zeigt den ungefähren Lebenszyklus und die Reaktion auf ein Eingabeereignis bei Verwendung von Swapchains mit Wartemöglichkeit:</span><span class="sxs-lookup"><span data-stu-id="7f48f-205">Figure 2 shows the approximate life cycle and response to an input event when using waitable swap chains:</span></span>

<span data-ttu-id="7f48f-206">Abbildung2</span><span class="sxs-lookup"><span data-stu-id="7f48f-206">Figure 2</span></span>

![Abbildung 2: Eingabelatenz in DirectX mit Wartemöglichkeit](images/input-latency2.png)

<span data-ttu-id="7f48f-208">Diese Abbildungen zeigen, dass die Eingabelatenz bei Spielen um zwei volle Frames reduziert werden kann, wenn das Rendern und Darstellen der einzelnen Frames innerhalb des Zeitraums von 16,7 ms durchgeführt werden kann, der durch die Aktualisierungsrate des Displays vorgegeben ist.</span><span class="sxs-lookup"><span data-stu-id="7f48f-208">What we see from these diagrams is that games can potentially reduce input latency by two full frames if they are capable of rendering and presenting each frame within the 16.7 ms budget defined by the display’s refresh rate.</span></span> <span data-ttu-id="7f48f-209">Im Beispiel mit dem Puzzle werden Swapchains mit Wartemöglichkeit verwendet, und das Limit der Present-Warteschlange wird per Aufruf des folgenden Elements gesteuert:</span><span class="sxs-lookup"><span data-stu-id="7f48f-209">The jigsaw puzzle sample uses waitable swap chains and controls the Present queue limit by calling:</span></span>` m_deviceResources->SetMaximumFrameLatency(1);`

 

 




