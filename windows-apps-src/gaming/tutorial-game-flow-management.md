---
author: joannaleecy
title: Spielablaufverwaltung
description: Erfahren Sie, wie Sie Spielzustände initialisieren, Ereignisse behandeln und die Spielaktualisierungsschleife einrichten.
ms.assetid: 6c33bf09-b46a-4bb5-8a59-ca83ce257eb3
ms.author: joanlee
ms.date: 10/24/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, directx
ms.localizationpriority: medium
ms.openlocfilehash: 610b794c0ded6791e93c14d8960366132afd973b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5560437"
---
# <a name="game-flow-management"></a><span data-ttu-id="3052f-104">Spielablaufverwaltung</span><span class="sxs-lookup"><span data-stu-id="3052f-104">Game flow management</span></span>

<span data-ttu-id="3052f-105">Das Spiel hat nun ein Fenster, registriert einige Ereignishandler und lädt Assets asynchron.</span><span class="sxs-lookup"><span data-stu-id="3052f-105">The game now has a window, registered a couple event handlers, and loads assets asynchronously.</span></span> <span data-ttu-id="3052f-106">In diesem Abschnitt werden die Verwendung von Spielständen, die Verwaltung bestimmter wichtiger Spielzustände und die Erstellung einer Aktualisierungsschleife für die Spiel-Engine erläutert.</span><span class="sxs-lookup"><span data-stu-id="3052f-106">This section explains about the use of game states, how to manage specific key game states, and how to create an update loop for the game engine.</span></span> <span data-ttu-id="3052f-107">Dann wird der Ablauf in der Benutzeroberfläche erläutert, und schließlich werden die Event-Handler und Events vorgestellt, die für ein UWP-Spiel erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="3052f-107">Then we'll learn about the user interface flow and finally, understand more about event handlers and events that are needed for a UWP game.</span></span>

>[!Note]
><span data-ttu-id="3052f-108">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="3052f-108">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="3052f-109">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="3052f-109">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="3052f-110">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="3052f-110">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="game-states-used-to-manage-game-flow"></a><span data-ttu-id="3052f-111">Spielzustände zur Verwaltung des Spielablaufs</span><span class="sxs-lookup"><span data-stu-id="3052f-111">Game states used to manage game flow</span></span>

<span data-ttu-id="3052f-112">Wir verwalten den Spielablauf mithilfe von Spielzuständen.</span><span class="sxs-lookup"><span data-stu-id="3052f-112">We make use of game states to manage the flow of the game.</span></span> <span data-ttu-id="3052f-113">Wenn ein Benutzer eine UWP-Spiel-App aus einem angehaltenen Zustand fortsetzt, kann das Spiel eine beliebigen der möglichen Zustände besitzen.</span><span class="sxs-lookup"><span data-stu-id="3052f-113">Your game can have any number of possible states because a user can resume a UWP game app from a suspended state at any time.</span></span>

<span data-ttu-id="3052f-114">In diesem Beispiel kann sich das Spiel beim Start in einem von dreiZuständen befinden:</span><span class="sxs-lookup"><span data-stu-id="3052f-114">For this game sample, it can be in one of the three states when it starts:</span></span>
* <span data-ttu-id="3052f-115">Die Spielschleife wird mitten in einem Level ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3052f-115">The game loop is running and is in the middle of a level.</span></span>
* <span data-ttu-id="3052f-116">Die Spielschleife wird nicht ausgeführt, da gerade ein Spiel abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-116">The game loop is not running because a game had just been completed.</span></span> <span data-ttu-id="3052f-117">(Der Highscore ist festgelegt)</span><span class="sxs-lookup"><span data-stu-id="3052f-117">(The high score is set)</span></span>
* <span data-ttu-id="3052f-118">Es wurde kein Spiel gestartet, oder das Spiel befindet sich zwischen zwei Leveln.</span><span class="sxs-lookup"><span data-stu-id="3052f-118">No game has been started, or the game is between levels.</span></span> <span data-ttu-id="3052f-119">(Der Highscore ist 0)</span><span class="sxs-lookup"><span data-stu-id="3052f-119">(The high score is 0)</span></span>

<span data-ttu-id="3052f-120">Sie können die Anzahl der erforderlichen Zustände je nach den Bedürfnissen Ihres Spiels festlegen.</span><span class="sxs-lookup"><span data-stu-id="3052f-120">You can have define the number of states required depending on your game's needs.</span></span> <span data-ttu-id="3052f-121">Berücksichtigen Sie dabei (wie gesagt), dass Ihr UWP-Spiel jederzeit beendet werden kann. Beim Fortsetzen des Spiels erwartet der Spieler, dass sich das Spiel so verhält, als sei es nie unterbrochen worden.</span><span class="sxs-lookup"><span data-stu-id="3052f-121">Again, be aware that your UWP game can be terminated at any time, and when it resumes, the player expects the game to behave as though they had never stopped playing.</span></span>

## <a name="game-states-initialization"></a><span data-ttu-id="3052f-122">Initialisieren der Spielzustände</span><span class="sxs-lookup"><span data-stu-id="3052f-122">Game states initialization</span></span>

<span data-ttu-id="3052f-123">Bei der Spielinitialisierung müssen Sie sich nicht nur den erstmaligen Start des Spiel berücksichtigen, sondern auch einen Neustart, nachdem es angehalten oder beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-123">In game initialization, you are not just focused on cold starting the game but also restarting after it has been paused or terminated.</span></span> <span data-ttu-id="3052f-124">Das Beispielspiel speichert stets den Zustand, sodass der Eindruck entsteht, als würde es ohne Unterbrechung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3052f-124">The sample game always saves the game state giving it the appearance that it has stayed running.</span></span> 

<span data-ttu-id="3052f-125">Im angehaltenen Zustand ist der Spielablauf unterbrochen, aber die Ressourcen des Spiels befinden sich aber nach wie vor im Speicher.</span><span class="sxs-lookup"><span data-stu-id="3052f-125">In a suspended state, game play is suspended but the resources of the game are still in memory.</span></span> 

<span data-ttu-id="3052f-126">Dementsprechend stellt das Fortsetzungsereignis sicher, dass das Beispielspiel an der Stelle fortgesetzt wird, an der es zuletzt angehalten oder beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-126">Likewise, the resume event is to ensure that the sample game picks up where it was last suspended or terminated.</span></span> <span data-ttu-id="3052f-127">Wird das Beispielspiel neu gestartet, nachdem es beendet wurde, startet das Spiel ganz normal und ermittelt dann den letzten bekannten Zustand, sodass der Spieler sofort weiterspielen kann.</span><span class="sxs-lookup"><span data-stu-id="3052f-127">When the sample game restarts after termination, it starts up normally and then determines the last known state so the player can immediately continue playing.</span></span>

<span data-ttu-id="3052f-128">Je nach Zustand hat der Spieler unterschiedliche Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="3052f-128">Depending on the state, different options are presented to the player.</span></span> 

* <span data-ttu-id="3052f-129">Wird das Spiel mitten in einem Level fortgesetzt, entsteht der Eindruck, es sei angehalten, und auf dem Overlay steht eine Fortsetzungsoption zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3052f-129">If the game resumes mid-level, it appears as paused, and the overlay presents a continue option.</span></span>
* <span data-ttu-id="3052f-130">Wenn das Spiel in einem Zustand fortgesetzt wird, in dem es abgeschlossen ist, zeigt es die Highscores und eine Option zum Starten eines neuen Spiels an.</span><span class="sxs-lookup"><span data-stu-id="3052f-130">If the game resumes in a state where the game is completed, it displays the high scores and an option to play a new game.</span></span>
* <span data-ttu-id="3052f-131">Wird das Spiel dagegen vor dem Start eines Levels fortgesetzt, sieht der Spieler eine Startoption auf dem Overlay.</span><span class="sxs-lookup"><span data-stu-id="3052f-131">Lastly, if the game resumes before a level has started, the overlay presents a start option to the user.</span></span>

<span data-ttu-id="3052f-132">Das Spielbeispiel unterscheidet nicht zwischen einem Kaltstart des Spiels (also einem Spiel, das zum ersten Mal und ohne Anhalteereignis gestartet wird) und der Fortsetzung eines angehaltenen Spiels.</span><span class="sxs-lookup"><span data-stu-id="3052f-132">The game sample doesn't distinguish whether the game is cold starting, launching for the first time without a suspend event, or resuming from a suspended state.</span></span> <span data-ttu-id="3052f-133">Dieses Design wird bei jeder UWP-App erwartet.</span><span class="sxs-lookup"><span data-stu-id="3052f-133">This is the proper design for any UWP app.</span></span>

<span data-ttu-id="3052f-134">In diesem Beispiel erfolgt die Initialisierung der Spielzustände in [__GameMain::InitializeGameState__](#gamemaininitializegamestate-method).</span><span class="sxs-lookup"><span data-stu-id="3052f-134">In this sample, initialization of the game states occurs in [__GameMain::InitializeGameState__](#gamemaininitializegamestate-method).</span></span>

<span data-ttu-id="3052f-135">Im folgenden Flussdiagramm können Sie den Ablauf nachverfolgen. Dargestellt sind sowohl Initialisierung- als auch Aktualisierungsschleife.</span><span class="sxs-lookup"><span data-stu-id="3052f-135">This is a flowchart to help you visualize the flow, it covers both initialization and the update loop.</span></span>

* <span data-ttu-id="3052f-136">Die Initialisierung beginnt am Knoten __Start__ bei der Überprüfung des aktuellen Spielzustands.</span><span class="sxs-lookup"><span data-stu-id="3052f-136">Initialization begins at the __Start__ node when you check for the current game state.</span></span> <span data-ttu-id="3052f-137">Den Spielcode finden Sie unter [__GameMain::InitializeGameState__](#gamemaininitializegamestate-method).</span><span class="sxs-lookup"><span data-stu-id="3052f-137">For game code, go to [__GameMain::InitializeGameState__](#gamemaininitializegamestate-method).</span></span>
* <span data-ttu-id="3052f-138">Weitere Informationen über die Aktualisierungsschleife finden Sie unter [Aktualisieren der Spiel-Engine](#update-game-engine).</span><span class="sxs-lookup"><span data-stu-id="3052f-138">For more info about the update loop, go to [Update game engine](#update-game-engine).</span></span> <span data-ttu-id="3052f-139">Den Code des Spiels finden Sie unter [__App:: Update__](#appupdate-method).</span><span class="sxs-lookup"><span data-stu-id="3052f-139">For game code, go to [__App::Update__](#appupdate-method).</span></span>

![Hauptzustandsautomat für unser Spiel](images/simple-dx-game-flow-statemachine.png)

### <a name="gamemaininitializegamestate-method"></a><span data-ttu-id="3052f-141">GameMain::InitializeGameState method</span><span class="sxs-lookup"><span data-stu-id="3052f-141">GameMain::InitializeGameState method</span></span>

<span data-ttu-id="3052f-142">Die Methode __InitializeGameState__ wird von der Konstruktorklasse [__GameMain__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L32-L131) aufgerufen, die aufgerufen wird, wenn das Klassenobjekt __GameMain__ in der Methode [__App::Load__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/App.cpp#L115-L123) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="3052f-142">The __InitializeGameState__ method is called from the [__GameMain__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L32-L131) constructor class, which is called when the  __GameMain__ class object is created in the [__App::Load__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/App.cpp#L115-L123) method.</span></span>

```cpp

GameMain::GameMain(...)
{
    m_deviceResources->RegisterDeviceNotify(this);
    ...

    create_task([this]()
    {
        ...

    }).then([this]()
    {
        // The finalize code needs to run in the same thread context
        // as the m_renderer object was created because the D3D device context
        // can ONLY be accessed on a single thread.
        m_renderer->FinalizeCreateGameDeviceResources();

        InitializeGameState(); //Initialization of game states occurs here.
        
        ...
    
    }, task_continuation_context::use_current()).then([this]()
    {
        ...
        
    }, task_continuation_context::use_current());
}

```

```cpp

void GameMain::InitializeGameState()
{
    // Set up the initial state machine for handling Game playing state.
    if (m_game->GameActive() && m_game->LevelActive())
    {
        // The last time the game terminated it was in the middle of a level.
        // We are waiting for the user to continue the game.
        //...
    }
    else if (!m_game->GameActive() && (m_game->HighScore().totalHits > 0))
    {
        // The last time the game terminated the game had been completed.
        // Show the high score.
        // We are waiting for the user to acknowledge the high score and start a new game.
        // The level resources for the first level will be loaded later.
        //...
    }
    else
    {
        // This is either the first time the game has run or
        // the last time the game terminated the level was completed.
        // We are waiting for the user to begin the next level.
        m_updateState = UpdateEngineState::WaitingForResources;
        m_pressResult = PressResultState::PlayLevel;
        SetGameInfoOverlay(GameInfoOverlayState::LevelStart);
        m_uiControl->SetAction(GameInfoOverlayCommand::PleaseWait);
    }
    m_uiControl->ShowGameInfoOverlay();
}

```

## <a name="update-game-engine"></a><span data-ttu-id="3052f-143">Aktualisieren der Spiele-Engine</span><span class="sxs-lookup"><span data-stu-id="3052f-143">Update game engine</span></span>

<span data-ttu-id="3052f-144">In der Methode [__App::Run__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/App.cpp#L127-L130) ruft sie [__GameMain::Run__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L143-L202) auf.</span><span class="sxs-lookup"><span data-stu-id="3052f-144">In the [__App::Run__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/App.cpp#L127-L130) method, it calls [__GameMain::Run__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L143-L202).</span></span> <span data-ttu-id="3052f-145">In dieser Methode wird innerhalb der Spielschleife des Beispiels ein einfacher Zustandsautomat zur Behandlung aller wichtigen Aktionen implementiert, die der Spieler ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="3052f-145">Within this method, the sample has implemented a basic state machine for handling all the major actions the player can take.</span></span> <span data-ttu-id="3052f-146">Die höchste Ebene dieses Zustandsautomats behandelt das Laden eines Spiels, das Spielen eines bestimmten Levels oder das Fortsetzen eines Levels, nachdem das Spiel (vom System oder vom Spieler) angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-146">The highest level of this state machine deals with loading a game, playing a specific level, or continuing a level after the game has been paused (by the system or the player).</span></span>

<span data-ttu-id="3052f-147">Im Spielbeispiel kann sich das Spiel in drei Hauptzuständen (__UpdateEngineState__) befinden:</span><span class="sxs-lookup"><span data-stu-id="3052f-147">In the game sample, there are 3 major states (__UpdateEngineState__) the game can be:</span></span>

1. <span data-ttu-id="3052f-148">__Waiting for resources__: Die Spielschleife wird durchlaufen, und ein Übergang ist erst möglich, wenn Ressourcen (insbesondere Grafikressourcen) verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="3052f-148">__Waiting for resources__: The game loop is cycling, unable to transition until resources (specifically graphics resources) are available.</span></span> <span data-ttu-id="3052f-149">Nach Abschluss der asynchronen Aufgaben zum Laden der Ressourcen wird der Zustand zu __ResourcesLoaded__ aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3052f-149">When the async tasks for loading resources completes, it updates the state to __ResourcesLoaded__.</span></span> <span data-ttu-id="3052f-150">Dieser Fall tritt üblicherweise zwischen Leveln ein, wenn ein Level neue Ressourcen von einem Datenträger, einem Spieleserver oder Cloudbackend lädt.</span><span class="sxs-lookup"><span data-stu-id="3052f-150">This usually happens between levels when the level is loading new resources from disk, game server, or cloud backend.</span></span> <span data-ttu-id="3052f-151">Im Spielbeispiel simulieren wir dieses Verhalten, da an dieser Stelle keine zusätzlichen levelspezifischen Ressourcen für das Spiel geladen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="3052f-151">In the game sample, we simulate this behavior because the sample doesn't need any additional per-level resources at that time.</span></span>
2. <span data-ttu-id="3052f-152">__Waiting for press__: Die Spielschleife wird durchlaufen, bis eine bestimmte Benutzereingabe erfolgt.</span><span class="sxs-lookup"><span data-stu-id="3052f-152">__Waiting for press__: The game loop is cycling, waiting for specific user input.</span></span> <span data-ttu-id="3052f-153">Bei der Eingabe handelt es sich um eine Spieleraktion zum Laden eines Spiels, zum Starten eines Levels oder zum Fortsetzen eines Levels.</span><span class="sxs-lookup"><span data-stu-id="3052f-153">This input is a player action to load a game, start a level, or continue a level.</span></span> <span data-ttu-id="3052f-154">Der Beispielcode bezieht sich auf diese Unterzustände als __PressResultState__-Aufzählungswerte.</span><span class="sxs-lookup"><span data-stu-id="3052f-154">The sample code refers to these sub-states as __PressResultState__ enumeration values.</span></span>
3. <span data-ttu-id="3052f-155">In __Dynamics__: Die Spielschleife wird ausgeführt, während der Spieler spielt.</span><span class="sxs-lookup"><span data-stu-id="3052f-155">In __Dynamics__: The game loop is running with the user playing.</span></span> <span data-ttu-id="3052f-156">Während der Spieler spielt, sucht das Spiel nach drei Bedingungen, auf die es reagieren kann:</span><span class="sxs-lookup"><span data-stu-id="3052f-156">While the user is playing, the game checks for 3 conditions that it can transition on:</span></span> 
    * <span data-ttu-id="3052f-157">__TimeExpired__: Ablauf des Zeitlimits für einen Level</span><span class="sxs-lookup"><span data-stu-id="3052f-157">__TimeExpired__: expiration of the set time for a level</span></span>
    * <span data-ttu-id="3052f-158">__LevelComplete__: Abschluss eines Levels durch den Spieler</span><span class="sxs-lookup"><span data-stu-id="3052f-158">__LevelComplete__: completion of a level by the player</span></span> 
    * <span data-ttu-id="3052f-159">__GameComplete__: Abschluss aller Level durch den Spieler</span><span class="sxs-lookup"><span data-stu-id="3052f-159">__GameComplete__: completion of all levels by the player</span></span>

<span data-ttu-id="3052f-160">Ihr Spiel ist einfach ein Zustandsautomat, der mehrere kleinere Zustandsautomaten enthält.</span><span class="sxs-lookup"><span data-stu-id="3052f-160">Your game is simply a state machine containing multiple smaller state machines.</span></span> <span data-ttu-id="3052f-161">Für jeden spezifischen Zustand muss es durch sehr spezifische Kriterien definiert werden.</span><span class="sxs-lookup"><span data-stu-id="3052f-161">For each specific state, it must be defined by a very specific criteria.</span></span> <span data-ttu-id="3052f-162">Wie es von einem Zustand in einen anderen übergeht, muss auf diskreten Benutzereingaben oder Systemaktionen beruhen (wie dem Laden von Grafikressourcen) basieren.</span><span class="sxs-lookup"><span data-stu-id="3052f-162">How it transitions from one state to another must be based on discrete user input or system actions (such as graphics resource loading).</span></span> <span data-ttu-id="3052f-163">Bedenken Sie bei der Planung Ihres Spiels den gesamten Spielablauf, um sicherzustellen, dass Sie alle möglichen Aktionen berücksichtigt haben, die Benutzer oder System ausführen können.</span><span class="sxs-lookup"><span data-stu-id="3052f-163">While planning for your game, consider drawing out the entire game flow, to ensure that you've addressed all possible actions the user or the system can take.</span></span> <span data-ttu-id="3052f-164">Spiele können sehr kompliziert sein, und der Zustandsautomat ist ein wirksames Tool, um diese Komplexität darzustellen und den Umgang damit deutlich zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="3052f-164">Games can be very complicated so a state machine is a powerful tool to help visualize this complexity and make it more manageable.</span></span>

<span data-ttu-id="3052f-165">Betrachten wir nun den Code für die Aktualisierungsschleife unten.</span><span class="sxs-lookup"><span data-stu-id="3052f-165">Let's take a look at the codes for the update loop below.</span></span>

### <a name="appupdate-method"></a><span data-ttu-id="3052f-166">App::Update method</span><span class="sxs-lookup"><span data-stu-id="3052f-166">App::Update method</span></span>

<span data-ttu-id="3052f-167">Die Struktur des Zustandsautomaten zur Aktualisierung der Spiele-Engine</span><span class="sxs-lookup"><span data-stu-id="3052f-167">The structure of the state machine used to update the game engine</span></span>

```cpp
void GameMain::Update()
{
    m_controller->Update(); //the controller instance has its own update loop.

    switch (m_updateState)
    {
    case UpdateEngineState::WaitingForResources:
        //...
        break;

    case UpdateEngineState::ResourcesLoaded:
        //...
        break;

    case UpdateEngineState::WaitingForPress:
        if (m_controller->IsPressComplete())
        {
            //...
        }
        break;

    case UpdateEngineState::Dynamics:
        if (m_controller->IsPauseRequested())
        {
            //...
        }
        else
        {
            GameState runState = m_game->RunGame(); //when the player is playing, the work is handled by this Simple3DGame::RunGame method.
            switch (runState)
            {
            case GameState::TimeExpired:
                //...
                break;

            case GameState::LevelComplete:
                //...
                break;

            case GameState::GameComplete:
                //...
                break;
            }
        }

        if (m_updateState == UpdateEngineState::WaitingForPress)
        {
            // Transitioning state, so enable waiting for the press event
            m_controller->WaitForPress(m_renderer->GameInfoOverlayUpperLeft(), m_renderer->GameInfoOverlayLowerRight());
        }
        if (m_updateState == UpdateEngineState::WaitingForResources)
        {
            // Transitioning state, so shut down the input controller until resources are loaded
            m_controller->Active(false);
        }
        break;
    }
}
```

## <a name="update-user-interface"></a><span data-ttu-id="3052f-168">Aktualisierung der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="3052f-168">Update user interface</span></span>

<span data-ttu-id="3052f-169">Wir müssen den Spieler über den Status des Systems auf dem Laufenden halten und den Spielstatus ändern, abhängig von den Aktionen des Spielers und den Regeln, die das Spiel definieren.</span><span class="sxs-lookup"><span data-stu-id="3052f-169">We need to keep the player apprised of the state of the system, and allow the game state to change depending on the player's actions and the rules that define the game.</span></span> <span data-ttu-id="3052f-170">Viele Spiele, einschließlich dieses Beispiels, verwenden Elemente der Benutzeroberfläche (UI), um dem Spieler diese Informationen mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="3052f-170">Many games, including this game sample, commonly use user interface (UI) elements to present this info to the player.</span></span> <span data-ttu-id="3052f-171">Die Benutzeroberfläche enthält Darstellungen des Spielzustands und andere spielspezifische Informationen wie Punktestand, Munitionsbestand oder die Anzahl verbleibender Chancen.</span><span class="sxs-lookup"><span data-stu-id="3052f-171">The UI contains representations of game state, and other play-specific info such as score, or ammo, or the number of chances remaining.</span></span> <span data-ttu-id="3052f-172">Die UI wird auch als Overlay bezeichnet, da sie separat von der Hauptgrafikpipeline gerendert und über der 3D-Projektion dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="3052f-172">UI is also called the overlay because it is rendered separately from the main graphics pipeline and placed on top the 3D projection.</span></span> <span data-ttu-id="3052f-173">Einige UI-Informationen werden auch als Heads-Up-Display (HUD) präsentiert, damit Nutzer diese Informationen verfolgen kann, ohne den Hauptspielbereich aus den Augen zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="3052f-173">Some UI info is also presented as a heads-up display (HUD) to allow users to get these info without taking their eyes off the main gameplay area.</span></span> <span data-ttu-id="3052f-174">Im Beispielspiel erstellen wir dieses Overlay mithilfe der Direct2D-APIs.</span><span class="sxs-lookup"><span data-stu-id="3052f-174">In the sample game, we create this overlay using the Direct2D APIs.</span></span> <span data-ttu-id="3052f-175">Wir können das Overlay allerdings auch per XAML erstellen. Informationen hierzu finden Sie unter [Erweitern des Spielbeispiels](tutorial-resources.md).</span><span class="sxs-lookup"><span data-stu-id="3052f-175">We can also create this overlay using XAML, which we discuss in [Extending the game sample](tutorial-resources.md).</span></span>

<span data-ttu-id="3052f-176">Die Benutzeroberfläche umfasst zwei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="3052f-176">There are two components to the user interface:</span></span>

-   <span data-ttu-id="3052f-177">Das HUD mit dem Punktestand und Infos zum aktuellen Zustand des Spielverlaufs.</span><span class="sxs-lookup"><span data-stu-id="3052f-177">The HUD that contains the score and info about the current state of game play.</span></span>
-   <span data-ttu-id="3052f-178">Die Bitmap für den Pausenmodus – ein schwarzes Rechteck mit Text, das im angehaltenen/unterbrochenen Zustand des Spiels im Vordergrund angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3052f-178">The pause bitmap, which is a black rectangle with text overlaid during the paused/suspended state of the game.</span></span> <span data-ttu-id="3052f-179">Dies ist die Spielüberlagerung.</span><span class="sxs-lookup"><span data-stu-id="3052f-179">This is the game overlay.</span></span> <span data-ttu-id="3052f-180">Ausführlichere Informationen hierzu finden Sie unter [Hinzufügen einer Benutzeroberfläche](tutorial--adding-a-user-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3052f-180">We discuss it further in [Adding a user interface](tutorial--adding-a-user-interface.md).</span></span>

<span data-ttu-id="3052f-181">Wie nicht anders zu erwarten, besitzt auch das Overlay einen Zustandsautomaten.</span><span class="sxs-lookup"><span data-stu-id="3052f-181">Unsurprisingly, the overlay has a state machine too.</span></span> <span data-ttu-id="3052f-182">Das Overlay kann eine Meldung für den Levelstart oder eine Meldung mit dem Hinweis anzeigen, dass das Spiel vorbei ist.</span><span class="sxs-lookup"><span data-stu-id="3052f-182">The overlay can display a level start or game over message.</span></span> <span data-ttu-id="3052f-183">Es ist im Grunde ein Canvas-Element, mit dem Sie beliebige Infos zum Spielzustand  dem Spieler anzeigen können, wenn das Spiel unterbrochen oder angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-183">It is essentially a canvas to output any info about game state that we display to the player when the game is paused or suspended.</span></span>

<span data-ttu-id="3052f-184">Das gerenderte Overlay kann einer der sechs Bildschirme sein, entsprechend einem der Spielzustände:</span><span class="sxs-lookup"><span data-stu-id="3052f-184">Overlay rendered can be one of the six screens, depending on the state of the game:</span></span> 
1. <span data-ttu-id="3052f-185">Bildschirm zu Beginn des Spiels, wenn Ressourcen geladen werden</span><span class="sxs-lookup"><span data-stu-id="3052f-185">Resources loading screen at the start of the game</span></span>
2. <span data-ttu-id="3052f-186">Bildschirm mit Spielstatistik</span><span class="sxs-lookup"><span data-stu-id="3052f-186">Game stats play screen</span></span>
3. <span data-ttu-id="3052f-187">Bildschirm mit Nachricht über Levelstart</span><span class="sxs-lookup"><span data-stu-id="3052f-187">Level start message screen</span></span>
4. <span data-ttu-id="3052f-188">Bildschirm am Spielende, wenn alle Ebenen ohne Timeout abgeschlossen wurden</span><span class="sxs-lookup"><span data-stu-id="3052f-188">Game over screen when all of the levels are completed without time running out</span></span>
5. <span data-ttu-id="3052f-189">Bildschirm am Spielende, wenn ein Timeout aufgetreten ist</span><span class="sxs-lookup"><span data-stu-id="3052f-189">Game over screen when time runs out</span></span>
6. <span data-ttu-id="3052f-190">Bildschirm mit Unterbrechungsmenü</span><span class="sxs-lookup"><span data-stu-id="3052f-190">Pause menu screen</span></span>

<span data-ttu-id="3052f-191">Dank der getrennten Behandlung von Benutzeroberfläche und Spielgrafikpipeline können Sie Arbeiten an der Benutzeroberfläche unabhängig von der Grafikengine des Spiels vornehmen. Außerdem wird der Code Ihres Spiels dadurch deutlich übersichtlicher.</span><span class="sxs-lookup"><span data-stu-id="3052f-191">Separating your user interface from your game's graphics pipeline allows you to work on it independent of the game's graphics rendering engine and decreases the complexity of your game's code significantly.</span></span>

<span data-ttu-id="3052f-192">Hier sehen Sie die Struktur des Overlay-Zustandsautomaten für das Spielbeispiel:</span><span class="sxs-lookup"><span data-stu-id="3052f-192">Here's how the game sample structures the overlay's state machine.</span></span>

```cpp
void GameMain::SetGameInfoOverlay(GameInfoOverlayState state)
{
    m_gameInfoOverlayState = state;
    switch (state)
    {
    case GameInfoOverlayState::Loading:
        m_uiControl->SetGameLoading(m_loadingCount);
        break;

    case GameInfoOverlayState::GameStats:
        //...
        break;

    case GameInfoOverlayState::LevelStart:
        //...
        break;

    case GameInfoOverlayState::GameOverCompleted:
        //...
        break;

    case GameInfoOverlayState::GameOverExpired:
        //...
        break;

    case GameInfoOverlayState::Pause:
        //...
        break;
    }
}
```

## <a name="events-handling"></a><span data-ttu-id="3052f-193">Behandeln von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="3052f-193">Events handling</span></span>

<span data-ttu-id="3052f-194">Unser Beispielcode hat eine Reihe von Handlern für bestimmte Ereignisse in **Initialize**, **SetWindow** und **Load** in App.ccp registriert.</span><span class="sxs-lookup"><span data-stu-id="3052f-194">Our sample code registered a number of handlers for specific events in **Initialize**, **SetWindow**, and **Load** in the App.cpp.</span></span> <span data-ttu-id="3052f-195">Dies sind wichtige Ereignisse, die funktionieren müssen, bevor wir Spielmechaniken hinzufügen oder die Grafikentwicklung starten können.</span><span class="sxs-lookup"><span data-stu-id="3052f-195">These are important events that needs to work before we can add game mechanics or start graphics development.</span></span> <span data-ttu-id="3052f-196">Diese Ereignisse sind für eine ordnungsgemäße UWP-App-Erfahrung von grundlegender Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="3052f-196">These events are fundamental to a proper UWP app experience.</span></span> <span data-ttu-id="3052f-197">Da eine UWP-App jederzeit aktiviert, deaktiviert, vergrößert, verkleinert, angedockt, abgedockt oder fortgesetzt werden kann, müssen diese Ereignisse so früh wie möglich registriert und so behandelt werden, dass der Spieler keine Unterbrechungen oder Überraschungen erlebt.</span><span class="sxs-lookup"><span data-stu-id="3052f-197">Because a UWP app can be activated, deactivated, resized, snapped, unsnapped, suspended, or resumed at any time, the game must register for these events as soon as it can, and handle them in a way that keeps the experience smooth and predictable for the player.</span></span>

<span data-ttu-id="3052f-198">Dies sind die in diesem Beispiel verwendeten Ereignishandler sowie die jeweils behandelten Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="3052f-198">These are the event handlers used in this sample and the events they handle.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3052f-199">Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="3052f-199">Event handler</span></span></th>
<th align="left"><span data-ttu-id="3052f-200">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3052f-200">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3052f-201">OnActivated</span><span class="sxs-lookup"><span data-stu-id="3052f-201">OnActivated</span></span></td>
<td align="left"><span data-ttu-id="3052f-202">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br225018"><strong>CoreApplicationView::Activated</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-202">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br225018"><strong>CoreApplicationView::Activated</strong></a>.</span></span> <span data-ttu-id="3052f-203">Die Spiele-App befindet sich im Vordergrund, weshalb das Hauptfenster aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="3052f-203">The game app has been brought to the foreground, so the main window is activated.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3052f-204">OnDpiChanged</span><span class="sxs-lookup"><span data-stu-id="3052f-204">OnDpiChanged</span></span></td>
<td align="left"><span data-ttu-id="3052f-205">Behandelt <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_DpiChanged"><strong>Graphics::Display::DisplayInformation::DpiChanged</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-205">Handles <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_DpiChanged"><strong>Graphics::Display::DisplayInformation::DpiChanged</strong></a>.</span></span> <span data-ttu-id="3052f-206">Der DPI-Wert der Anzeige hat sich geändert, und das Spiel passt seine Ressourcen entsprechend an.</span><span class="sxs-lookup"><span data-stu-id="3052f-206">The DPI of the display has changed and the game adjusts its resources accordingly.</span></span>
<div class="alert"><span data-ttu-id="3052f-207">
<strong>Hinweis:</strong>[<strong>CoreWindow</strong>] (https://msdn.microsoft.com/library/windows/desktop/hh404559) -Koordinaten werden in DIPs (Device Independent Pixels) für [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370987).</span><span class="sxs-lookup"><span data-stu-id="3052f-207">
<strong>Note</strong>[<strong>CoreWindow</strong>](https://msdn.microsoft.com/library/windows/desktop/hh404559) coordinates are in DIPs (Device Independent Pixels) for [Direct2D](https://msdn.microsoft.com/library/windows/desktop/dd370987).</span></span> <span data-ttu-id="3052f-208">Daher müssen Sie Direct2D über die DPI-Änderung informieren, damit die 2D-Ressourcen oder -Grundtypen korrekt angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3052f-208">As a result, you must notify Direct2D of the change in DPI to display any 2D assets or primitives correctly.</span></span>
</div>
<div>
</div></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3052f-209">OnOrientationChanged</span><span class="sxs-lookup"><span data-stu-id="3052f-209">OnOrientationChanged</span></span></td>
<td align="left"><span data-ttu-id="3052f-210">Behandelt <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_OrientationChanged"><strong>Graphics::Display::DisplayInformation::OrientationChanged</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-210">Handles <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_OrientationChanged"><strong>Graphics::Display::DisplayInformation::OrientationChanged</strong></a>.</span></span> <span data-ttu-id="3052f-211">Die Ausrichtung der Anzeige ändert sich, und das Rendern muss aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3052f-211">The orientation of the display changes and rendering needs to be updated.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3052f-212">OnDisplayContentsInvalidated</span><span class="sxs-lookup"><span data-stu-id="3052f-212">OnDisplayContentsInvalidated</span></span></td>
<td align="left"><span data-ttu-id="3052f-213">Behandelt <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_DisplayContentsInvalidated"><strong>Graphics::Display::DisplayInformation::DisplayContentsInvalidated</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-213">Handles <a href="https://docs.microsoft.com/uwp/api/windows.graphics.display.displayinformation#Windows_Graphics_Display_DisplayInformation_DisplayContentsInvalidated"><strong>Graphics::Display::DisplayInformation::DisplayContentsInvalidated</strong></a>.</span></span> <span data-ttu-id="3052f-214">Die Anzeige muss neu aufgebaut und das Spiel erneut gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="3052f-214">The display requires redrawing and your game needs to be rendered again.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3052f-215">OnResuming</span><span class="sxs-lookup"><span data-stu-id="3052f-215">OnResuming</span></span></td>
<td align="left"><span data-ttu-id="3052f-216">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br205859"><strong>CoreApplication::Resuming</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-216">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br205859"><strong>CoreApplication::Resuming</strong></a>.</span></span> <span data-ttu-id="3052f-217">Die Spiele-App stellt das Spiel aus einem Anhaltezustand wieder her.</span><span class="sxs-lookup"><span data-stu-id="3052f-217">The game app restores the game from a suspended state.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3052f-218">OnSuspending</span><span class="sxs-lookup"><span data-stu-id="3052f-218">OnSuspending</span></span></td>
<td align="left"><span data-ttu-id="3052f-219">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br205860"><strong>CoreApplication::Suspending</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-219">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br205860"><strong>CoreApplication::Suspending</strong></a>.</span></span> <span data-ttu-id="3052f-220">Die Spiele-App speichert den eigenen Zustand auf einem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="3052f-220">The game app saves its state to disk.</span></span> <span data-ttu-id="3052f-221">Der Speichervorgang für den Zustand darf maximal fünf Sekunden dauern.</span><span class="sxs-lookup"><span data-stu-id="3052f-221">It has 5 seconds to save state to storage.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3052f-222">OnVisibilityChanged</span><span class="sxs-lookup"><span data-stu-id="3052f-222">OnVisibilityChanged</span></span></td>
<td align="left"><span data-ttu-id="3052f-223">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/hh701591"><strong>CoreWindow::VisibilityChanged</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-223">Handles <a href="https://msdn.microsoft.com/library/windows/apps/hh701591"><strong>CoreWindow::VisibilityChanged</strong></a>.</span></span> <span data-ttu-id="3052f-224">Die Sichtbarkeit der Spiele-App hat sich geändert: Die App wurde entweder sichtbar, oder sie wurde durch eine andere sichtbar gewordene App unsichtbar.</span><span class="sxs-lookup"><span data-stu-id="3052f-224">The game app has changed visibility, and has either become visible or been made invisible by another app becoming visible.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3052f-225">OnWindowActivationChanged</span><span class="sxs-lookup"><span data-stu-id="3052f-225">OnWindowActivationChanged</span></span></td>
<td align="left"><span data-ttu-id="3052f-226">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br208255"><strong>CoreWindow::Activated</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-226">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br208255"><strong>CoreWindow::Activated</strong></a>.</span></span> <span data-ttu-id="3052f-227">Das Hauptfenster der Spiele-App wurde deaktiviert oder aktiviert, weshalb der Fokus entfernt und das Spiel angehalten oder der Fokus wiedererlangt werden muss.</span><span class="sxs-lookup"><span data-stu-id="3052f-227">The game app's main window has been deactivated or activated, so it must remove focus and pause the game, or regain focus.</span></span> <span data-ttu-id="3052f-228">In beiden Fällen gibt das Overlay an, dass das Spiel angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="3052f-228">In both cases, the overlay indicates that the game is paused.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3052f-229">OnWindowClosed</span><span class="sxs-lookup"><span data-stu-id="3052f-229">OnWindowClosed</span></span></td>
<td align="left"><span data-ttu-id="3052f-230">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br208261"><strong>CoreWindow:: Closed</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-230">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br208261"><strong>CoreWindow::Closed</strong></a>.</span></span> <span data-ttu-id="3052f-231">Die Spiele-App schließt das Hauptfenster und hält das Spiel an.</span><span class="sxs-lookup"><span data-stu-id="3052f-231">The game app closes the main window and suspends the game.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3052f-232">OnWindowSizeChanged</span><span class="sxs-lookup"><span data-stu-id="3052f-232">OnWindowSizeChanged</span></span></td>
<td align="left"><span data-ttu-id="3052f-233">Behandelt <a href="https://msdn.microsoft.com/library/windows/apps/br208283"><strong>CoreWindow::SizeChanged</strong></a>.</span><span class="sxs-lookup"><span data-stu-id="3052f-233">Handles <a href="https://msdn.microsoft.com/library/windows/apps/br208283"><strong>CoreWindow::SizeChanged</strong></a>.</span></span> <span data-ttu-id="3052f-234">Die Spiele-App ordnet die Grafikressourcen und das Overlay neu zu, um die Größenänderung umzusetzen, und aktualisiert anschließend das Renderziel.</span><span class="sxs-lookup"><span data-stu-id="3052f-234">The game app reallocates the graphics resources and overlay to accommodate the size change, and then updates the render target.</span></span></td>
</tr>
</tbody>
</table>

## <a name="next-steps"></a><span data-ttu-id="3052f-235">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3052f-235">Next steps</span></span>

<span data-ttu-id="3052f-236">In diesem Thema haben wir erläutert, wie der allgemeine Spielablauf mithilfe von Spielzuständen verwaltet wird, und dass ein Spiel aus mehreren verschiedenen Zustandsautomaten besteht.</span><span class="sxs-lookup"><span data-stu-id="3052f-236">In this topic, we've covered how the overall game flow is managed using game states and that a game is made up of multiple different state machines.</span></span> <span data-ttu-id="3052f-237">Wir haben zudem gezeigt, wie Sie die UI aktualisieren und wichtige App-Ereignishandler verwalten können.</span><span class="sxs-lookup"><span data-stu-id="3052f-237">We've also learnt about how to update the UI and manage key app event handlers.</span></span> <span data-ttu-id="3052f-238">Nun können wir uns mit der Renderingschleife, dem Spiel und seinen Mechanismen befassen.</span><span class="sxs-lookup"><span data-stu-id="3052f-238">Now we are ready to dive into the rendering loop, the game, and its mechanics.</span></span>
 
<span data-ttu-id="3052f-239">Sie können die anderen Komponenten, aus denen dieses Spiel besteht, in beliebiger Reihenfolge durcharbeiten:</span><span class="sxs-lookup"><span data-stu-id="3052f-239">You can go through the other components that make up this game in any order:</span></span>
* [<span data-ttu-id="3052f-240">Definieren des Hauptobjekts für das Spiel</span><span class="sxs-lookup"><span data-stu-id="3052f-240">Define the main game object</span></span>](tutorial--defining-the-main-game-loop.md)
* [<span data-ttu-id="3052f-241">Rendering-Framework I: Einführung in das Rendering</span><span class="sxs-lookup"><span data-stu-id="3052f-241">Rendering framework I: Intro to rendering</span></span>](tutorial--assembling-the-rendering-pipeline.md)
* [<span data-ttu-id="3052f-242">Rendering-Framework II: Spiel-Rendering</span><span class="sxs-lookup"><span data-stu-id="3052f-242">Rendering framework II: Game rendering</span></span>](tutorial-game-rendering.md)
* [<span data-ttu-id="3052f-243">Hinzufügen einer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="3052f-243">Add a user interface</span></span>](tutorial--adding-a-user-interface.md)
* [<span data-ttu-id="3052f-244">Hinzufügen von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="3052f-244">Add controls</span></span>](tutorial--adding-controls.md)
* [<span data-ttu-id="3052f-245">Hinzufügen von Sound</span><span class="sxs-lookup"><span data-stu-id="3052f-245">Add sound</span></span>](tutorial--adding-sound.md)