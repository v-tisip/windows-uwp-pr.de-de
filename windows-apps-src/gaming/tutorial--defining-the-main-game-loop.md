---
author: mtoepke
title: Definieren des Hauptobjekts für das Spiel
description: In diesem Abschnitt widmen wir uns den Details des Hauptobjekts des Beispielspiels. Außerdem erfahren Sie, wie die implementierten Regeln in Interaktionen mit der Spielwelt übersetzt werden.
ms.assetid: 6afeef84-39d0-cb78-aa2e-2e42aef936c9
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Hauptobjekt
ms.openlocfilehash: f81b3eaa9b896295386232f99b789dc3857b3bad
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235657"
---
# <a name="define-the-main-game-object"></a><span data-ttu-id="3227b-104">Definieren des Hauptobjekts für das Spiel</span><span class="sxs-lookup"><span data-stu-id="3227b-104">Define the main game object</span></span>


<span data-ttu-id="3227b-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="3227b-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="3227b-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="3227b-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="3227b-107">Wir haben bislang das grundlegende Framework des Beispielspiels eingerichtet und einen Zustandsautomaten für die übergeordneten Benutzer- und Systemverhalten implementiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-107">At this point, we've laid out the basic framework of the sample game, and we implemented a state machine that handles the high-level user and system behaviors.</span></span> <span data-ttu-id="3227b-108">Was wir allerdings noch nicht behandelt haben, ist der Teil, der das Beispielspiel zu einem richtigen Spiel macht: die Regeln und die Spielmechanik sowie deren Implementierung.</span><span class="sxs-lookup"><span data-stu-id="3227b-108">But we haven't examined the part that makes the game sample an actual game: the rules and mechanics, and how they're implemented!</span></span> <span data-ttu-id="3227b-109">In diesem Abschnitt widmen wir uns den Details des Hauptobjekts des Beispielspiels. Außerdem erfahren Sie, wie die implementierten Regeln in Interaktionen mit der Spielwelt übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-109">Now, we look at the details of the game sample's main object and how the rules it implements translate into interactions with the game world.</span></span>

## <a name="objective"></a><span data-ttu-id="3227b-110">Ziel</span><span class="sxs-lookup"><span data-stu-id="3227b-110">Objective</span></span>


-   <span data-ttu-id="3227b-111">Anwendung grundlegender Entwicklungstechniken beim Implementieren der Regeln und Spielmechaniken eines einfachen UWP-Spiels (Universelle Windows-Plattform) unter Verwendung von DirectX.</span><span class="sxs-lookup"><span data-stu-id="3227b-111">To apply the basic development techniques when implementing the rules and mechanics of a simple Universal Windows Platform (UWP) game using DirectX.</span></span>

## <a name="considering-the-games-flow"></a><span data-ttu-id="3227b-112">Berücksichtigen des Spielflusses</span><span class="sxs-lookup"><span data-stu-id="3227b-112">Considering the game's flow</span></span>


<span data-ttu-id="3227b-113">Der Großteil der Grundstruktur des Spiels wird in den folgenden Dateien definiert:</span><span class="sxs-lookup"><span data-stu-id="3227b-113">The majority of the game's basic structure is defined in these files:</span></span>

-   **<span data-ttu-id="3227b-114">App.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-114">App.cpp</span></span>**
-   **<span data-ttu-id="3227b-115">Simple3DGame.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-115">Simple3DGame.cpp</span></span>**

<span data-ttu-id="3227b-116">In [Definieren des UWP-App-Frameworks für das Spiel](tutorial--building-the-games-metro-style-app-framework.md) haben wir das in **App.cpp** definierte Framework des Spiels behandelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-116">In [Defining the game's UWP app framework](tutorial--building-the-games-metro-style-app-framework.md), we reviewed the game framework defined in **App.cpp**.</span></span>

<span data-ttu-id="3227b-117">**Simple3DGame.cpp** stellt den Code für eine Klasse **Simple3DGame** bereit, die die Implementierung des eigentlichen Gameplays angibt.</span><span class="sxs-lookup"><span data-stu-id="3227b-117">**Simple3DGame.cpp** provides the code for a class, **Simple3DGame**, which specifies the implementation of the game play itself.</span></span> <span data-ttu-id="3227b-118">Zuvor haben wir die Behandlung des Beispielspiels als UWP-App beleuchtet.</span><span class="sxs-lookup"><span data-stu-id="3227b-118">Earlier, we considered the treatment of the sample game as a UWP app.</span></span> <span data-ttu-id="3227b-119">Nun widmen wir uns dem Code, der es zu einem Spiel macht.</span><span class="sxs-lookup"><span data-stu-id="3227b-119">Now, we look at the code that makes it a game.</span></span>

<span data-ttu-id="3227b-120">Den vollständigen Code für **Simple3DGame.h/.cpp** finden Sie unter [Vollständiger Beispielcode für diesen Abschnitt](#complete-code-sample-for-this-section).</span><span class="sxs-lookup"><span data-stu-id="3227b-120">The complete code for **Simple3DGame.h/.cpp** is provided in [Complete sample code for this section](#complete-code-sample-for-this-section).</span></span>

<span data-ttu-id="3227b-121">Sehen wir uns einmal die Definition der **Simple3DGame**-Klasse an.</span><span class="sxs-lookup"><span data-stu-id="3227b-121">Let's take a look at the definition of the **Simple3DGame** class.</span></span>

## <a name="defining-the-core-game-object"></a><span data-ttu-id="3227b-122">Definieren des Kernobjekts für das Spiel</span><span class="sxs-lookup"><span data-stu-id="3227b-122">Defining the core game object</span></span>


<span data-ttu-id="3227b-123">Beim Start des App-Singletons erstellt die **Initialize**-Methode des Ansichtsanbieters eine Instanz der Hauptklasse des Spiels: das **Simple3DGame**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="3227b-123">When the app singleton starts, the view provider's **Initialize** method creates an instance of the main game class, the **Simple3DGame** object.</span></span> <span data-ttu-id="3227b-124">Dieses Objekt enthält die Methoden, die Änderungen am Spielzustand an den im App-Framework definierten Zustandsautomaten (oder von der App an das Spielobjekt selbst) weitergeben.</span><span class="sxs-lookup"><span data-stu-id="3227b-124">This object contains the methods that communicate changes in game state to the state machine defined in the app framework, or from the app to the game object itself.</span></span> <span data-ttu-id="3227b-125">Es enthält auch Methoden, die Infos zum Aktualisieren der Overlaybitmap und des Head-up-Display des Spiels sowie zum Aktualisieren der Animationen und der Physik (Dynamik) im Spiel zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="3227b-125">It also contains methods that return info for updating the game's overlay bitmap and heads-up display, and for updating the animations and physics (the dynamics) in the game.</span></span> <span data-ttu-id="3227b-126">Der Code für die vom Spiel verwendeten Grafikgerätressourcen befindet sich in „GameRenderer.cpp“. Darauf gehen wir in [Zusammensetzen des Renderingframeworks](tutorial--assembling-the-rendering-pipeline.md) noch näher ein.</span><span class="sxs-lookup"><span data-stu-id="3227b-126">The code for obtaining the graphics device resources used by the game is found in GameRenderer.cpp, which we discuss next in [Assembling the rendering framework](tutorial--assembling-the-rendering-pipeline.md).</span></span>

<span data-ttu-id="3227b-127">Der Code für **Simple3DGame** sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3227b-127">The code for **Simple3DGame** looks like this:</span></span>

```cpp
ref class GameRenderer;

ref class Simple3DGame
{
internal:
    Simple3DGame();

    void Initialize(
        _In_ MoveLookController^ controller,
        _In_ GameRenderer^ renderer
        );

    void LoadGame();
    concurrency::task<void> LoadLevelAsync();
    void FinalizeLoadLevel();
    void StartLevel();
    void PauseGame();
    void ContinueGame();
    GameState RunGame();

    void OnSuspending();
    void OnResuming();

    // ... Global variable retrieval methods are defined here ...

private:
    void LoadState();
    void SaveState();
    void SaveHighScore();
    void LoadHighScore();
    void InitializeAmmo();
    void UpdateDynamics();

    // ...
                // ... Global variables are defined here.
    // ...
};
```

<span data-ttu-id="3227b-128">Werfen wir zunächst einen Blick auf die internen Methoden, die für **Simple3DGame** definiert sind.</span><span class="sxs-lookup"><span data-stu-id="3227b-128">First, let's review the internal methods defined on **Simple3DGame**.</span></span>

-   <span data-ttu-id="3227b-129">**Initialize**.</span><span class="sxs-lookup"><span data-stu-id="3227b-129">**Initialize**.</span></span> <span data-ttu-id="3227b-130">Legt die Anfangswerte der globalen Variablen fest und initialisiert die Spielobjekte.</span><span class="sxs-lookup"><span data-stu-id="3227b-130">Sets the starting values of the global variables and initializes the game objects.</span></span>
-   <span data-ttu-id="3227b-131">**LoadGame**.</span><span class="sxs-lookup"><span data-stu-id="3227b-131">**LoadGame**.</span></span> <span data-ttu-id="3227b-132">Initialisiert ein neues Level und startet den entsprechenden Ladevorgang.</span><span class="sxs-lookup"><span data-stu-id="3227b-132">Initializes a new level and starts loading it.</span></span>
-   <span data-ttu-id="3227b-133">**LoadLevelAsync**.</span><span class="sxs-lookup"><span data-stu-id="3227b-133">**LoadLevelAsync**.</span></span> <span data-ttu-id="3227b-134">Startet eine asynchrone Aufgabe (weitere Details finden Sie unter [Parallel Patterns Library](https://msdn.microsoft.com/library/windows/apps/dd492418.aspx)) zum Initialisieren des Levels und ruft dann eine asynchrone Aufgabe für den Renderer auf, um die gerätespezifischen Ressourcen für das Level zu laden.</span><span class="sxs-lookup"><span data-stu-id="3227b-134">Starts an async task (see the [Parallel Patterns Library](https://msdn.microsoft.com/library/windows/apps/dd492418.aspx) for more details) to initialize the level and then invoke an async task on the renderer to load the device specific level resources.</span></span> <span data-ttu-id="3227b-135">Diese Methode wird in einem gesonderten Thread ausgeführt. Daher können in diesem Thread nur [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379)-Methoden (und keine [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)-Methoden) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-135">This method runs in a separate thread; as a result, only [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379) methods (as opposed to [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385) methods) can be called from this thread.</span></span> <span data-ttu-id="3227b-136">Alle Gerätekontextmethoden werden in der **FinalizeLoadLevel**-Methode aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3227b-136">Any device context methods are called in the **FinalizeLoadLevel** method.</span></span>
-   <span data-ttu-id="3227b-137">**FinalizeLoadLevel**.</span><span class="sxs-lookup"><span data-stu-id="3227b-137">**FinalizeLoadLevel**.</span></span> <span data-ttu-id="3227b-138">Führt alle Aktionen zum Laden des Levels aus, die im Hauptthread durchgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="3227b-138">Completes any work for level loading that needs to be done on the main thread.</span></span> <span data-ttu-id="3227b-139">Dies schließt alle Aufrufe von Direct3D11-Gerätekontextmethoden ([**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)) ein.</span><span class="sxs-lookup"><span data-stu-id="3227b-139">This includes any calls to Direct3D 11 device context ([**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)) methods.</span></span>
-   <span data-ttu-id="3227b-140">**StartLevel**.</span><span class="sxs-lookup"><span data-stu-id="3227b-140">**StartLevel**.</span></span> <span data-ttu-id="3227b-141">Startet das Gameplay für ein neues Level.</span><span class="sxs-lookup"><span data-stu-id="3227b-141">Starts the game play for a new level.</span></span>
-   <span data-ttu-id="3227b-142">**PauseGame**.</span><span class="sxs-lookup"><span data-stu-id="3227b-142">**PauseGame**.</span></span> <span data-ttu-id="3227b-143">Hält das Spiel an.</span><span class="sxs-lookup"><span data-stu-id="3227b-143">Pauses the game.</span></span>
-   <span data-ttu-id="3227b-144">**RunGame**.</span><span class="sxs-lookup"><span data-stu-id="3227b-144">**RunGame**.</span></span> <span data-ttu-id="3227b-145">Führt eine Iteration der Spielschleife aus.</span><span class="sxs-lookup"><span data-stu-id="3227b-145">Runs an iteration of the game loop.</span></span> <span data-ttu-id="3227b-146">Wird jeweils einmal pro Iteration der Spielschleife von **App::Update** aufgerufen, sofern sich das Spiel im Zustand **Active** befindet.</span><span class="sxs-lookup"><span data-stu-id="3227b-146">It's called from **App::Update** one time every iteration of the game loop if the game state is **Active**.</span></span>
-   <span data-ttu-id="3227b-147">**OnSuspending** und **OnResuming**.</span><span class="sxs-lookup"><span data-stu-id="3227b-147">**OnSuspending** and **OnResuming**.</span></span> <span data-ttu-id="3227b-148">Hält die Audiowiedergabe des Spiels an bzw. setzt sie fort.</span><span class="sxs-lookup"><span data-stu-id="3227b-148">Suspends and resumes the game's audio, respectively.</span></span>

<span data-ttu-id="3227b-149">Und die privaten Methoden:</span><span class="sxs-lookup"><span data-stu-id="3227b-149">And the private methods:</span></span>

-   <span data-ttu-id="3227b-150">**LoadSavedState** und **SaveState**.</span><span class="sxs-lookup"><span data-stu-id="3227b-150">**LoadSavedState** and **SaveState**.</span></span> <span data-ttu-id="3227b-151">Lädt bzw. speichert den aktuellen Zustand des Spiels.</span><span class="sxs-lookup"><span data-stu-id="3227b-151">Loads and saves the current state of the game, respectively.</span></span>
-   <span data-ttu-id="3227b-152">**SaveHighScore** und **LoadHighScore**.</span><span class="sxs-lookup"><span data-stu-id="3227b-152">**SaveHighScore** and **LoadHighScore**.</span></span> <span data-ttu-id="3227b-153">Speichert bzw. lädt den spielübergreifenden Highscore.</span><span class="sxs-lookup"><span data-stu-id="3227b-153">Saves and loads the high score across games, respectively.</span></span>
-   <span data-ttu-id="3227b-154">**InitializeAmmo**.</span><span class="sxs-lookup"><span data-stu-id="3227b-154">**InitializeAmmo**.</span></span> <span data-ttu-id="3227b-155">Setzt den Zustand der als Munition verwendeten Kugelobjekte in den Originalzustand für den Beginn einer neuen Runde zurück.</span><span class="sxs-lookup"><span data-stu-id="3227b-155">Resets the state of each sphere object used as ammunition back to its original state for the beginning of each round.</span></span>
-   <span data-ttu-id="3227b-156">**UpdateDynamics**.</span><span class="sxs-lookup"><span data-stu-id="3227b-156">**UpdateDynamics**.</span></span> <span data-ttu-id="3227b-157">Diese Methode ist sehr wichtig, da sie alle Spielobjekte auf der Grundlage vordefinierter Animationsroutinen, Physikeffekte und Steuerungseingaben aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-157">This is an important method, because it updates all the game objects based on canned animation routines, physics, and control input.</span></span> <span data-ttu-id="3227b-158">Hierbei handelt es sich gewissermaßen um das Herzstück der Interaktivität, die das Spiel ausmacht.</span><span class="sxs-lookup"><span data-stu-id="3227b-158">This is the heart of the interactivity that defines the game.</span></span> <span data-ttu-id="3227b-159">Hiermit beschäftigen wir uns im Abschnitt [Aktualisieren des Spiels](#updating-the-game-world) noch ausführlicher.</span><span class="sxs-lookup"><span data-stu-id="3227b-159">We talk about it more in the [Updating the game](#updating-the-game-world) section.</span></span>

<span data-ttu-id="3227b-160">Die anderen öffentlichen Methoden dienen zum Abrufen von Eigenschaften und geben Gameplay- und Overlay-spezifische Informationen an das App-Framework zurück, um diese anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3227b-160">The other public methods are property getters that return game play and overlay specific information to the app framework for display.</span></span>

## <a name="defining-the-game-state-variables"></a><span data-ttu-id="3227b-161">Definieren der Spielzustandsvariablen</span><span class="sxs-lookup"><span data-stu-id="3227b-161">Defining the game state variables</span></span>


<span data-ttu-id="3227b-162">Das Spielobjekt fungiert u.a. als Container für die Daten, die eine Spielsitzung, ein Level oder eine Lebensdauer ausmachen – je nachdem, wie Sie Ihr Spiel auf einer übergeordneten Ebene definieren.</span><span class="sxs-lookup"><span data-stu-id="3227b-162">One function of the game object is to serve as a container for the data that defines a game session, level, or lifetime, depending on how you define your game at a high level.</span></span> <span data-ttu-id="3227b-163">Im aktuellen Fall beziehen sich die Spielzustandsdaten auf die Lebensdauer des Spiels und werden ein Mal initialisiert, wenn der Benutzer das Spiel startet.</span><span class="sxs-lookup"><span data-stu-id="3227b-163">In this case, the game state data is for the lifetime of the game, initialized one time when a user launches the game.</span></span>

<span data-ttu-id="3227b-164">Im Anschluss finden Sie alle Definitionen für die Zustandsvariablen des Spielobjekts.</span><span class="sxs-lookup"><span data-stu-id="3227b-164">Here's the complete set of definitions for the game object's state variables.</span></span>

```cpp
private:
    MoveLookController^                                 m_controller;
    GameRenderer^                                       m_renderer;
    Camera^                                             m_camera;

    Audio^                                              m_audioController;

    std::vector<Sphere^>                                m_ammo;
    uint32                                              m_ammoCount;
    uint32                                              m_ammoNext;

    HighScoreEntry                                      m_topScore;
    PersistentState^                                    m_savedState;

    GameTimer^                                          m_timer;
    bool                                                m_gameActive;
    bool                                                m_levelActive;
    int                                                 m_totalHits;
    int                                                 m_totalShots;
    float                                               m_levelDuration;
    float                                               m_levelBonusTime;
    float                                               m_levelTimeRemaining;
    std::vector<Level^>                                 m_level;
    uint32                                              m_levelCount;
    uint32                                              m_currentLevel;

    Sphere^                                             m_player;
    std::vector<GameObject^>                            m_object;           // object list for intersections
    std::vector<GameObject^>                            m_renderObject;     // all objects to be rendered

    DirectX::XMFLOAT3                                   m_minBound;
    DirectX::XMFLOAT3                                   m_maxBound;
```

<span data-ttu-id="3227b-165">Am Anfang des Codebeispiels befinden sich vier Objekte, deren Instanzen während der Ausführung der Spielschleife aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-165">At the top of the code example, there are four objects whose instances are updated as the game loop runs.</span></span>

-   <span data-ttu-id="3227b-166">Das **MoveLookController**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="3227b-166">The **MoveLookController** object.</span></span> <span data-ttu-id="3227b-167">Dieses Objekt stellt die Eingaben des Spielers dar.</span><span class="sxs-lookup"><span data-stu-id="3227b-167">This object represents the player input.</span></span> <span data-ttu-id="3227b-168">(Ausführlichere Informationen zum **MoveLookController**-Objekt finden Sie unter [Hinzufügen von Steuerelementen](tutorial--adding-controls.md).)</span><span class="sxs-lookup"><span data-stu-id="3227b-168">(For more info about the **MoveLookController** object, see [Adding controls](tutorial--adding-controls.md).)</span></span>
-   <span data-ttu-id="3227b-169">Das **GameRenderer**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="3227b-169">The **GameRenderer** object.</span></span> <span data-ttu-id="3227b-170">Dieses Objekt stellt den von der **DirectXBase**-Klasse abgeleiteten Direct3D11-Renderer dar, der alle gerätespezifischen Objekte und deren Rendering verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="3227b-170">This object represents the Direct3D 11 renderer derived from the **DirectXBase** class that handles all the device-specific objects and their rendering.</span></span> <span data-ttu-id="3227b-171">(Weitere Informationen finden Sie unter [Zusammensetzen der Renderingpipeline](tutorial--assembling-the-rendering-pipeline.md).)</span><span class="sxs-lookup"><span data-stu-id="3227b-171">(For more info, see [Assembling the rendering pipeline](tutorial--assembling-the-rendering-pipeline.md)).</span></span>
-   <span data-ttu-id="3227b-172">Das **Camera**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="3227b-172">The **Camera** object.</span></span> <span data-ttu-id="3227b-173">Dieses Objekt stellt die Sicht des Spielers auf die Spielwelt aus der Ich-Perspektive dar.</span><span class="sxs-lookup"><span data-stu-id="3227b-173">This object represents the player's first-person view of the game world.</span></span> <span data-ttu-id="3227b-174">(Ausführlichere Informationen zum **Camera**-Objekt finden Sie unter [Zusammensetzen der Renderingpipeline](tutorial--assembling-the-rendering-pipeline.md).)</span><span class="sxs-lookup"><span data-stu-id="3227b-174">(For more info about the **Camera** object, see [Assembling the rendering pipeline](tutorial--assembling-the-rendering-pipeline.md).)</span></span>
-   <span data-ttu-id="3227b-175">Das **Audio**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="3227b-175">The **Audio** object.</span></span> <span data-ttu-id="3227b-176">Dieses Objekt steuert die Audiowiedergabe für das Spiel.</span><span class="sxs-lookup"><span data-stu-id="3227b-176">This object controls the audio playback for the game.</span></span> <span data-ttu-id="3227b-177">(Ausführlichere Informationen zum **Audio**-Objekt finden Sie unter [Hinzufügen von Sound](tutorial--adding-sound.md).)</span><span class="sxs-lookup"><span data-stu-id="3227b-177">(For more info about the **Audio** object, see [Adding sound](tutorial--adding-sound.md).)</span></span>

<span data-ttu-id="3227b-178">Die restlichen Spielvariablen enthalten die Listen mit den Grundtypen und die entsprechenden spielinternen Werte sowie Gameplay-spezifische Daten und Beschränkungen.</span><span class="sxs-lookup"><span data-stu-id="3227b-178">The rest of the game variables contain the lists of the primitives and their respective in-game amounts, and game play specific data and constraints.</span></span> <span data-ttu-id="3227b-179">Im Anschluss sehen Sie, wie das Beispiel diese Variablen beim Initialisieren des Spiels konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="3227b-179">Let's see how the sample configures these variables when the game is initialized.</span></span>

## <a name="initializing-and-starting-the-game"></a><span data-ttu-id="3227b-180">Initialisieren und Starten des Spiels</span><span class="sxs-lookup"><span data-stu-id="3227b-180">Initializing and starting the game</span></span>


<span data-ttu-id="3227b-181">Wenn ein Spieler das Spiel startet, muss das Spielobjekt den eigenen Zustand initialisieren, das Overlay erstellen und hinzufügen, die Variablen zur Nachverfolgung der Erfolge des Spielers festlegen und die Objekte instanziieren, die zum Erstellen der Level benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-181">When a player starts the game, the game object must initialize its state, create and add the overlay, set the variables that track the player's performance, and instantiate the objects that it will use to build the levels.</span></span>

```cpp
void Simple3DGame::Initialize(
    _In_ MoveLookController^ controller,
    _In_ GameRenderer^ renderer
    )
{
    // This method is expected to be called as an asynchronous task.
    // Make sure that you don't call rendering methods on the
    // m_renderer as this would result in the D3D Context being
    // used in multiple threads, which is not allowed.

    m_controller = controller;
    m_renderer = renderer;

    m_audioController = ref new Audio;
    m_audioController->CreateDeviceIndependentResources();

    m_ammo = std::vector<Sphere^>(GameConstants::MaxAmmo);
    m_object = std::vector<GameObject^>();
    m_renderObject = std::vector<GameObject^>();
    m_level = std::vector<Level^>();

    m_savedState = ref new PersistentState();
    m_savedState->Initialize(ApplicationData::Current->LocalSettings->Values, "Game");

    m_timer = ref new GameTimer();

    // Create a sphere primitive to represent the player.
    // The sphere is used to handle collisions and constrain the player in the world.
    // It's not rendered, so it's not added to the list of render objects.
    m_player = ref new Sphere(XMFLOAT3(0.0f, -1.3f, 4.0f), 0.2f);

    m_camera = ref new Camera;
    m_camera->SetProjParams(XM_PI / 2, 1.0f, 0.01f, 100.0f);
    m_camera->SetViewParams(
        m_player->Position(),            // Eye point in world coordinates.
        XMFLOAT3 (0.0f, 0.7f, 0.0f),     // Look at point in world coordinates.
        XMFLOAT3 (0.0f, 1.0f, 0.0f)      // The Up vector for the camera.
        );

    m_controller->Pitch(m_camera->Pitch());
    m_controller->Yaw(m_camera->Yaw());

    // Add the m_player object to the object list to do intersection calculations.
    m_object.push_back(m_player);
    m_player->Active(true);

    // Instantiate the world primitive.  This object maintains the geometry and
    // material properties of the walls, floor, and ceiling of the enclosing world.
    // The TargetId is used to identify the world objects so that the right geometry
    // and textures can be associated with them later after those resources have
    // been created.
    GameObject^ world = ref new GameObject();
    world->TargetId(GameConstants::WorldFloorId);
    world->Active(true);
    m_renderObject.push_back(world);

    world = ref new GameObject();
    world->TargetId(GameConstants::WorldCeilingId);
    world->Active(true);
    m_renderObject.push_back(world);

    world = ref new GameObject();
    world->TargetId(GameConstants::WorldWallsId);
    world->Active(true);
    m_renderObject.push_back(world);

    // Min and max Bound are defining the world space of the game.
    // All camera motion and dynamics are confined to this space.
    m_minBound = XMFLOAT3(-4.0f, -3.0f, -6.0f);
    m_maxBound = XMFLOAT3(4.0f, 3.0f, 6.0f);

    // Instantiate the cylinders for use in the various game levels.
    // Each cylinder has a different initial position, radius, and direction vector,
    // but share a common set of material properties.
    for (int a = 0; a < GameConstants::MaxCylinders; a++)
    {
        Cylinder^ cylinder;
        switch (a)
        {
        case 0:
            cylinder = ref new Cylinder(XMFLOAT3(-2.0f, -3.0f, 0.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 1:
            cylinder = ref new Cylinder(XMFLOAT3(2.0f, -3.0f, 0.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 2:
            cylinder = ref new Cylinder(XMFLOAT3(0.0f, -3.0f, -2.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 3:
            cylinder = ref new Cylinder(XMFLOAT3(-1.5f, -3.0f, -4.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 4:
            cylinder = ref new Cylinder(XMFLOAT3(1.5f, -3.0f, -4.0f), 0.50f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        }
        cylinder->Active(true);
        m_object.push_back(cylinder);
        m_renderObject.push_back(cylinder);
    }

    MediaReader^ mediaReader = ref new MediaReader;
    auto targetHitSound = mediaReader->LoadMedia("hit.wav");

    // Instantiate the targets for use in the game.
    // Each target has a different initial position, size, and orientation,
    // but share a common set of material properties.
    // The target is defined by a position and two vectors that define both
    // the plane of the target in world space and the size of the parallelogram
    // based on the lengths of the vectors.
    // Each target is assigned a number for identification purposes.
    // The Target ID number is 1 based.
    // All targets have the same material properties.
    for (int a = 1; a < GameConstants::MaxTargets; a++)
    {
        Face^ target;
        switch (a)
        {
        case 1:
            target = ref new Face(XMFLOAT3(-2.5f, -1.0f, -1.5f), XMFLOAT3(-1.5f, -1.0f, -2.0f), XMFLOAT3(-2.5f, 1.0f, -1.5f));
            break;
        case 2:
            target = ref new Face(XMFLOAT3(-1.0f, 1.0f, -3.0f), XMFLOAT3(0.0f, 1.0f, -3.0f), XMFLOAT3(-1.0f, 2.0f, -3.0f));
            break;
        case 3:
            target = ref new Face(XMFLOAT3(1.5f, 0.0f, -3.0f), XMFLOAT3(2.5f, 0.0f, -2.0f), XMFLOAT3(1.5f, 2.0f, -3.0f));
            break;
        case 4:
            target = ref new Face(XMFLOAT3(-2.5f, -1.0f, -5.5f), XMFLOAT3(-0.5f, -1.0f, -5.5f), XMFLOAT3(-2.5f, 1.0f, -5.5f));
            break;
        case 5:
            target = ref new Face(XMFLOAT3(0.5f, -2.0f, -5.0f), XMFLOAT3(1.5f, -2.0f, -5.0f), XMFLOAT3(0.5f, 0.0f, -5.0f));
            break;
        case 6:
            target = ref new Face(XMFLOAT3(1.5f, -2.0f, -5.5f), XMFLOAT3(2.5f, -2.0f, -5.0f), XMFLOAT3(1.5f, 0.0f, -5.5f));
            break;
        case 7:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        case 8:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        case 9:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        }

        target->Target(true);
        target->TargetId(a);
        target->Active(true);
        target->HitSound(ref new SoundEffect());
        target->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            targetHitSound);

        m_object.push_back(target);
        m_renderObject.push_back(target);
    }

    // Instantiate a set of spheres to be used as ammunition for the game
    // and set the material properties of the spheres.
    auto ammoHitSound = mediaReader->LoadMedia("bounce.wav");

    for (int a = 0; a < GameConstants::MaxAmmo; a++)
    {
        m_ammo[a] = ref new Sphere;
        m_ammo[a]->Radius(GameConstants::AmmoRadius);
        m_ammo[a]->HitSound(ref new SoundEffect());
        m_ammo[a]->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            ammoHitSound);
        m_ammo[a]->Active(false);
        m_renderObject.push_back(m_ammo[a]);
    }

    // Instantiate each of the game levels.  The Level class contains methods
    // that initialize the objects in the world for the given level and also
    // define any motion paths for the objects in that level.

    m_level.push_back(ref new Level1);
    m_level.push_back(ref new Level2);
    m_level.push_back(ref new Level3);
    m_level.push_back(ref new Level4);
    m_level.push_back(ref new Level5);
    m_level.push_back(ref new Level6);
    m_levelCount = static_cast<uint32>(m_level.size());

    // Load the top score from disk if it exists.
    LoadHighScore();

    // Load the currentScore for saved state.
    LoadState();

    m_controller->Active(false);
}
```

<span data-ttu-id="3227b-182">Das Beispielspiel richtet die Komponenten des Spieleobjekts in dieser Reihenfolge ein:</span><span class="sxs-lookup"><span data-stu-id="3227b-182">The sample game sets up the components of the game object in this order:</span></span>

1.  <span data-ttu-id="3227b-183">Ein neues Audiowiedergabeobjekt wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-183">A new audio playback object is created.</span></span>
2.  <span data-ttu-id="3227b-184">Arrays für die Grafikgrundtypen des Spiels werden erstellt (einschließlich Arrays für die Levelgrundtypen, Munition und Hindernisse).</span><span class="sxs-lookup"><span data-stu-id="3227b-184">Arrays for the game's graphic primitives are created, including arrays for the level primitives, ammo, and obstacles.</span></span>
3.  <span data-ttu-id="3227b-185">Ein Speicherort für die Spielzustandsdaten mit der Bezeichnung *Game* wird erstellt und am durch [**ApplicationData::Current**](https://msdn.microsoft.com/library/windows/apps/br241619) festgelegten Speicherort der App-Dateneinstellungen platziert.</span><span class="sxs-lookup"><span data-stu-id="3227b-185">A location for saving game state data is created, named *Game*, and placed in the app data settings storage location specified by [**ApplicationData::Current**](https://msdn.microsoft.com/library/windows/apps/br241619).</span></span>
4.  <span data-ttu-id="3227b-186">Ein Spieltimer und die anfängliche spielinterne Overlaybitmap werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-186">A game timer and the initial in-game overlay bitmap are created.</span></span>
5.  <span data-ttu-id="3227b-187">Eine neue Kamera mit einem spezifischen Satz von Ansichts- und Projektionsparametern wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-187">A new camera is created with a specific set of view and projection parameters.</span></span>
6.  <span data-ttu-id="3227b-188">Das Eingabegerät (Controller) wird auf die gleiche Ausgangsausrichtung festgelegt wie die Kamera, sodass die Ausgangsposition der Steuerung exakt der Kameraposition entspricht.</span><span class="sxs-lookup"><span data-stu-id="3227b-188">The input device (the controller) is set to the same starting pitch and yaw as the camera, so the player has a 1-to-1 correspondence between the starting control position and the camera position.</span></span>
7.  <span data-ttu-id="3227b-189">Das Spielerobjekt wird erstellt und aktiviert.</span><span class="sxs-lookup"><span data-stu-id="3227b-189">The player object is created and set to active.</span></span> <span data-ttu-id="3227b-190">Wir verwenden ein Kugelobjekt, um die Nähe des Spielers zu Wänden und Hindernissen zu ermitteln. So wird dafür gesorgt, dass die Kamera nur so positioniert werden kann, dass der Immersionseffekt nicht beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="3227b-190">We use a sphere object to detect the player's proximity to walls and obstacles and to keep the camera from getting put in a position that might break immersion.</span></span>
8.  <span data-ttu-id="3227b-191">Der Spielweltgrundtyp wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-191">The game world primitive is created.</span></span>
9.  <span data-ttu-id="3227b-192">Die Zylinderhindernisse werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-192">The cylinder obstacles are created.</span></span>
10. <span data-ttu-id="3227b-193">Die Ziele (**Face**-Objekte) werden erstellt und nummeriert.</span><span class="sxs-lookup"><span data-stu-id="3227b-193">The targets (**Face** objects) are created and numbered.</span></span>
11. <span data-ttu-id="3227b-194">Die Munitionskugeln werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-194">The ammo spheres are created.</span></span>
12. <span data-ttu-id="3227b-195">Die Level werden erstellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-195">The levels are created.</span></span>
13. <span data-ttu-id="3227b-196">Der Highscore wird geladen.</span><span class="sxs-lookup"><span data-stu-id="3227b-196">The high score is loaded.</span></span>
14. <span data-ttu-id="3227b-197">Alle ggf. zuvor gespeicherten Spielzustände werden geladen.</span><span class="sxs-lookup"><span data-stu-id="3227b-197">Any prior saved game state is loaded.</span></span>

<span data-ttu-id="3227b-198">Das Spiel besitzt nun Instanzen aller wichtigen Komponenten: Spielwelt, Spieler, Hindernisse, Ziele und Munitionskugeln.</span><span class="sxs-lookup"><span data-stu-id="3227b-198">The game now has instances of all the key components: the world, the player, the obstacles, the targets, and the ammo spheres.</span></span> <span data-ttu-id="3227b-199">Außerdem besitzt es Instanzen der Level. Diese stehen für Konfigurationen aller oben genannten Komponenten und ihrer Verhalten für die einzelnen spezifischen Level.</span><span class="sxs-lookup"><span data-stu-id="3227b-199">It also has instances of the levels, which represent configurations of all of the above components and their behaviors for each specific level.</span></span> <span data-ttu-id="3227b-200">Im nächsten Abschnitt widmen wir uns der Levelerstellung des Spiels.</span><span class="sxs-lookup"><span data-stu-id="3227b-200">Let's see how the game builds the levels.</span></span>

## <a name="building-and-loading-the-games-levels"></a><span data-ttu-id="3227b-201">Erstellen und Laden der Level des Spiels</span><span class="sxs-lookup"><span data-stu-id="3227b-201">Building and loading the game's levels</span></span>


<span data-ttu-id="3227b-202">Der Hauptteil der Levelkonstruktion wird in der Datei **Level.h/.cpp** erledigt. Darauf gehen wir an dieser Stelle aber nicht näher ein, da es sich hierbei um eine sehr spezifische Implementierung handelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-202">Most of the heavy lifting for the level construction is done in the **Level.h/.cpp** file, which we won't delve into, because it focuses on a very specific implementation.</span></span> <span data-ttu-id="3227b-203">Entscheidend ist in diesem Zusammenhang, dass der Code für die einzelnen Levels jeweils als separates **LevelN**-Objekt ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3227b-203">The important thing is that the code for each level is run as a separate **LevelN** object.</span></span> <span data-ttu-id="3227b-204">Falls Sie das Spiel erweitern möchten, können Sie ein **Level**-Objekt erstellen, das eine zugewiesene Nummer als Parameter annimmt und die Hindernisse und Ziele nach dem Zufallsprinzip verteilt.</span><span class="sxs-lookup"><span data-stu-id="3227b-204">If you'd like to extend the game, you can create a **Level** object that took an assigned number as a parameter and randomly placed the obstacles and targets.</span></span> <span data-ttu-id="3227b-205">Alternativ können Sie festlegen, dass Levelkonfigurationsdaten aus einer Ressourcendatei oder sogar aus dem Internet geladen werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-205">Or, you can have it load level configuration data from a resource file, or even the Internet!</span></span>

<span data-ttu-id="3227b-206">Den vollständigen Code für **Level.h/.cpp** finden Sie unter [Vollständiger Beispielcode für diesen Abschnitt](#complete-code-sample-for-this-section).</span><span class="sxs-lookup"><span data-stu-id="3227b-206">The complete code for **Level.h/.cpp** is provided in [Complete sample code for this section](#complete-code-sample-for-this-section).</span></span>

## <a name="defining-the-game-play"></a><span data-ttu-id="3227b-207">Definieren des Gameplays</span><span class="sxs-lookup"><span data-stu-id="3227b-207">Defining the game play</span></span>


<span data-ttu-id="3227b-208">Wir verfügen nun über alle Komponenten, die wir benötigen, um das Spiel zusammenzufügen.</span><span class="sxs-lookup"><span data-stu-id="3227b-208">At this point, we have all the components we need to assemble the game.</span></span> <span data-ttu-id="3227b-209">Die Level wurden auf der Grundlage der Grundtypen im Speicher konstruiert und sind bereit für die Interaktion des Spielers.</span><span class="sxs-lookup"><span data-stu-id="3227b-209">The levels have been constructed in memory from the primitives, and are ready for the player to start interacting with them in some fashion.</span></span>

<span data-ttu-id="3227b-210">Faustregel: Wirklich gute Spiele reagieren ohne Verzögerung auf Spielereingaben und liefern umgehend Feedback.</span><span class="sxs-lookup"><span data-stu-id="3227b-210">Now, the best games react instantly to player input, and provide immediate feedback.</span></span> <span data-ttu-id="3227b-211">Dies gilt für jede Art von Spiel – ob actionlastiger Echtzeitshooter oder eher gemächliches rundenbasiertes Strategiespiel.</span><span class="sxs-lookup"><span data-stu-id="3227b-211">This is true for any type of a game, from twitch-action, real-time shoot-em-ups to thoughtful, turn-based strategy games.</span></span>

<span data-ttu-id="3227b-212">In [Definieren des UWP-App-Frameworks für das Spiel](tutorial--building-the-games-metro-style-app-framework.md)haben wir uns mit dem Zustandsautomaten beschäftigt, der den Spielfluss steuert.</span><span class="sxs-lookup"><span data-stu-id="3227b-212">In [Defining the game's UWP framework](tutorial--building-the-games-metro-style-app-framework.md), we looked at the overall state machine that governs the flow of the game.</span></span> <span data-ttu-id="3227b-213">Nochmal zur Erinnerung: Das Beispiel implementiert diesen Fluss als Schleife in der [**Run**](https://msdn.microsoft.com/library/windows/apps/hh702093)-Methode der **App**-Klasse, die selbst eine Implementierung eines DirectX-Ansichtsanbieters ist.</span><span class="sxs-lookup"><span data-stu-id="3227b-213">Remember, the sample implements this flow as a loop inside the [**Run**](https://msdn.microsoft.com/library/windows/apps/hh702093) method of the **App** class, which itself is an implementation of a DirectX view provider.</span></span> <span data-ttu-id="3227b-214">Die wichtigen Zustandsübergänge müssen vom Spieler gesteuert werden und eindeutiges Feedback geben.</span><span class="sxs-lookup"><span data-stu-id="3227b-214">The important state transitions must be controlled by the player, and must provide clear feedback.</span></span> <span data-ttu-id="3227b-215">Jegliche Verzögerung beim Feedback stört das Immersionsgefühl.</span><span class="sxs-lookup"><span data-stu-id="3227b-215">Any delay in this feedback breaks the sense of immersion.</span></span>

<span data-ttu-id="3227b-216">Im Anschluss finden Sie ein Diagramm mit dem grundlegenden Spielfluss und den übergeordneten Zuständen.</span><span class="sxs-lookup"><span data-stu-id="3227b-216">Here is a diagram representing the basic flow of the game and its high-level states.</span></span>

![Diagramm mit dem Hauptzustandsautomaten für unser Spiel](images/simple3dgame-mainstatemachine.png)

<span data-ttu-id="3227b-218">Beim Start des Beispielspiels kann sich das Spielobjekt in einem von drei Zuständen befinden:</span><span class="sxs-lookup"><span data-stu-id="3227b-218">When the sample game starts play, the game object can be in one of three states:</span></span>

-   <span data-ttu-id="3227b-219">**Waiting for resources**.</span><span class="sxs-lookup"><span data-stu-id="3227b-219">**Waiting for resources**.</span></span> <span data-ttu-id="3227b-220">Dieser Zustand wird aktiviert, wenn das Spielobjekt initialisiert wird oder die Komponenten eines Levels geladen werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-220">This state is activated when the game object is initialized or when the components of a level are being loaded.</span></span> <span data-ttu-id="3227b-221">Wird dieser Zustand durch eine Anforderung zum Laden eines vorherigen Spiels ausgelöst, wird das Overlay mit der Spielstatistik angezeigt. Wird es durch eine Anforderung zum Spielen eines Levels ausgelöst, wird das Overlay für den Levelstart angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3227b-221">If this state was triggered by a request to load a prior game, the game stats overlay is displayed; if it was triggered by a request to play a level, the level start overlay is displayed.</span></span> <span data-ttu-id="3227b-222">Ausgelöst durch den abgeschlossenen Ladevorgang der Ressourcen durchläuft das Spiel den Zustand **Resources loaded** und geht dann in den Zustand **Waiting for press** über.</span><span class="sxs-lookup"><span data-stu-id="3227b-222">The completion of resource loading causes the game to pass through the **Resources loaded** state and then transition into the **Waiting for press** state.</span></span>
-   <span data-ttu-id="3227b-223">**Waiting for press**.</span><span class="sxs-lookup"><span data-stu-id="3227b-223">**Waiting for press**.</span></span> <span data-ttu-id="3227b-224">Dieser Zustand wird aktiviert, wenn das Spiel angehalten wird. Dabei spielt es keine Rolle, ob dies durch den Spieler oder durch das System (beispielsweise nach dem Laden von Ressourcen) geschieht.</span><span class="sxs-lookup"><span data-stu-id="3227b-224">This state is activated when the game is paused, either by the player or by the system (after, say, loading resources).</span></span> <span data-ttu-id="3227b-225">Wenn der Spieler diesen Zustand verlassen möchte, wird er aufgefordert, einen neuen Spielzustand zu laden (LoadGame), das geladene Level zu starten oder neu zu starten (StartLevel) oder das aktuelle Level fortzusetzen (ContinueGame).</span><span class="sxs-lookup"><span data-stu-id="3227b-225">When the player is ready to exit this state, the player is prompted to load a new game state (LoadGame), start or restart the loaded level (StartLevel), or continue the current level (ContinueGame).</span></span>
-   <span data-ttu-id="3227b-226">**Dynamics**.</span><span class="sxs-lookup"><span data-stu-id="3227b-226">**Dynamics**.</span></span> <span data-ttu-id="3227b-227">Wenn die Eingabe eines Spielers abgeschlossen und die Folgeaktion der Start oder die Fortsetzung eines Levels ist, wechselt das Spielobjekt in den Zustand *Dynamics*.</span><span class="sxs-lookup"><span data-stu-id="3227b-227">If a player's press input is completed and the resulting action is to start or continue a level, the game object transitions into the *Dynamics* state.</span></span> <span data-ttu-id="3227b-228">In diesem Zustand wird das Spiel gespielt, und die Spielwelt sowie die Spielerobjekte werden auf der Grundlage der Animationsroutinen und der Spielereingaben aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-228">The game is played in this state, and the game world and player objects are updated here based on animation routines and player input.</span></span> <span data-ttu-id="3227b-229">Dieser Zustand endet, wenn der Spieler ein Pausenereignis auslöst – entweder durch Drücken der P-TASTE, durch eine Aktion, die das Hauptfenster deaktiviert, oder durch Abschließen eines Levels oder des Spiels.</span><span class="sxs-lookup"><span data-stu-id="3227b-229">This state is left when the player triggers a pause event, either by pressing P, by taking an action that deactivates the main window, or by completing a level or the game.</span></span>

<span data-ttu-id="3227b-230">Werfen wir nun einen Blick auf spezifischen Code in der **App**-Klasse (siehe [Definieren des UWP-App-Frameworks für das Spiel](tutorial--building-the-games-metro-style-app-framework.md)) für die **Update**-Methode, die diesen Zustandsautomaten implementiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-230">Now, let's look at specific code in the **App** class (see: [Defining the game's UWP framework](tutorial--building-the-games-metro-style-app-framework.md)) for the **Update** method that implements this state machine.</span></span>

```cpp
void App::Update()
{
    static uint32 loadCount = 0;

    m_controller->Update();

    switch (m_updateState)
    {
    case UpdateEngineState::WaitingForResources:
        // Waiting for initial load.  Display an update one time per 60 updates.
        loadCount++;
        if ((loadCount % 60) == 0)
        {
            m_loadingCount++;
            SetGameInfoOverlay(m_gameInfoOverlayState);
        }
        break;

    case UpdateEngineState::ResourcesLoaded:
        switch (m_pressResult)
        {
        case PressResultState::LoadGame:
            SetGameInfoOverlay(GameInfoOverlayState::GameStats);
            break;

        case PressResultState::PlayLevel:
            SetGameInfoOverlay(GameInfoOverlayState::LevelStart);
            break;

        case PressResultState::ContinueLevel:
            SetGameInfoOverlay(GameInfoOverlayState::Pause);
            break;
        }
        m_updateState = UpdateEngineState::WaitingForPress;
        SetAction(GameInfoOverlayCommand::TapToContinue);
        m_controller->WaitForPress(m_renderer->GameInfoOverlayUpperLeft(), m_renderer->GameInfoOverlayLowerRight());
        ShowGameInfoOverlay();
        m_renderNeeded = true;
        break;

    case UpdateEngineState::WaitingForPress:
        if (m_controller->IsPressComplete())
        {
            switch (m_pressResult)
            {
            case PressResultState::LoadGame:
                m_updateState = UpdateEngineState::WaitingForResources;
                m_pressResult = PressResultState::PlayLevel;
                m_controller->Active(false);
                m_game->LoadGame();
                SetAction(GameInfoOverlayCommand::PleaseWait);
                SetGameInfoOverlay(GameInfoOverlayState::LevelStart);
                ShowGameInfoOverlay();

                m_game->LoadLevelAsync().then([this]()
                {
                    m_game->FinalizeLoadLevel();
                    m_updateState = UpdateEngineState::ResourcesLoaded;

                }, task_continuation_context::use_current());
                break;

            case PressResultState::PlayLevel:
                m_updateState = UpdateEngineState::Dynamics;
                HideGameInfoOverlay();
                m_controller->Active(true);
                m_game->StartLevel();
                break;

            case PressResultState::ContinueLevel:
                m_updateState = UpdateEngineState::Dynamics;
                HideGameInfoOverlay();
                m_controller->Active(true);
                m_game->ContinueGame();
                break;
            }
        }
        break;

    case UpdateEngineState::Dynamics:
        if (m_controller->IsPauseRequested())
        {
            m_game->PauseGame();
            SetGameInfoOverlay(GameInfoOverlayState::Pause);
            SetAction(GameInfoOverlayCommand::TapToContinue);
            m_updateState = UpdateEngineState::WaitingForPress;
            m_pressResult = PressResultState::ContinueLevel;
            ShowGameInfoOverlay();
        }
        else
        {
            GameState runState = m_game->RunGame();
            switch (runState)
            {
            case GameState::TimeExpired:
                SetAction(GameInfoOverlayCommand::TapToContinue);
                SetGameInfoOverlay(GameInfoOverlayState::GameOverExpired);
                ShowGameInfoOverlay();
                m_updateState = UpdateEngineState::WaitingForPress;
                m_pressResult = PressResultState::LoadGame;
                break;

            case GameState::LevelComplete:
                SetAction(GameInfoOverlayCommand::PleaseWait);
                SetGameInfoOverlay(GameInfoOverlayState::LevelStart);
                ShowGameInfoOverlay();
                m_updateState = UpdateEngineState::WaitingForResources;
                m_pressResult = PressResultState::PlayLevel;

                m_game->LoadLevelAsync().then([this]()
                {
                    m_game->FinalizeLoadLevel();
                    m_updateState = UpdateEngineState::ResourcesLoaded;

                }, task_continuation_context::use_current());
                break;

            case GameState::GameComplete:
                SetAction(GameInfoOverlayCommand::TapToContinue);
                SetGameInfoOverlay(GameInfoOverlayState::GameOverCompleted);
                ShowGameInfoOverlay();
                m_updateState  = UpdateEngineState::WaitingForPress;
                m_pressResult = PressResultState::LoadGame;
                break;
            }
        }

        if (m_updateState == UpdateEngineState::WaitingForPress)
        {
            // Transitioning state, so enable waiting for the press event.
            m_controller->WaitForPress(m_renderer->GameInfoOverlayUpperLeft(), m_renderer->GameInfoOverlayLowerRight());
        }
        if (m_updateState == UpdateEngineState::WaitingForResources)
        {
            // Transitioning state, so shut down the input controller until resources are loaded.
            m_controller->Active(false);
        }
        break;
    }
}
```

<span data-ttu-id="3227b-231">Zunächst ruft diese Methode die **Update**-Methode der [MoveLookController](tutorial--adding-controls.md)-Instanz auf, die die Daten des Controllers aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-231">The first thing this method does is call the [MoveLookController](tutorial--adding-controls.md) instance's own **Update** method, which updates the data from the controller.</span></span> <span data-ttu-id="3227b-232">Zu diesen Daten gehören die Blickrichtung des Spielers (die Kamera) sowie die Geschwindigkeit der Spielerbewegung.</span><span class="sxs-lookup"><span data-stu-id="3227b-232">This data includes the direction the player's view (the camera) is facing and the velocity of the player's movement.</span></span>

<span data-ttu-id="3227b-233">Wenn sich das Spiel im Zustand „Dynamics“ befindet (der Spieler also spielt), wird die Arbeit in der **RunGame**-Methode mit dem folgenden Aufruf behandelt:</span><span class="sxs-lookup"><span data-stu-id="3227b-233">When the game is in the Dynamics state, that is, when the player is playing, the work is handled in the **RunGame** method, with this call:</span></span>

`GameState runState = m_game->RunGame();`

<span data-ttu-id="3227b-234">**RunGame** behandelt die Gruppe von Daten, die den aktuellen Zustand des Gameplays für die aktuelle Iteration der Spielschleife definieren.</span><span class="sxs-lookup"><span data-stu-id="3227b-234">**RunGame** handles the set of data that defines the current state of the game play for the current iteration of the game loop.</span></span> <span data-ttu-id="3227b-235">Der Fluss sieht so aus:</span><span class="sxs-lookup"><span data-stu-id="3227b-235">It flows like this:</span></span>

1.  <span data-ttu-id="3227b-236">Die Methode aktualisiert den Zeitgeber, der die Sekunden bis zum Levelabschluss herunterzählt, und überprüft, ob die Zeit für den Level abgelaufen ist.</span><span class="sxs-lookup"><span data-stu-id="3227b-236">The method updates the timer that counts down the seconds until the level is completed, and tests to see if the level's time has expired.</span></span> <span data-ttu-id="3227b-237">Dies ist eine der Spielregeln: Wurden vor Ablauf der Zeit nicht alle Ziele getroffen, ist das Spiel vorbei.</span><span class="sxs-lookup"><span data-stu-id="3227b-237">This is one of the rules of the game: when time runs out without all the targets getting shot, the game is over.</span></span>
2.  <span data-ttu-id="3227b-238">Ist die Zeit abgelaufen, legt die Methode den Spielzustand **TimeExpired** fest und kehrt zur **Update**-Methode im vorherigen Code zurück.</span><span class="sxs-lookup"><span data-stu-id="3227b-238">If time has run out, the method sets the **TimeExpired** game state, and returns to the **Update** method in the previous code.</span></span>
3.  <span data-ttu-id="3227b-239">Ist die Zeit noch nicht abgelaufen, wird für den Bewegungs- und Blickrichtungscontroller eine aktualisierte Kameraposition abgefragt. Genauer gesagt: eine Aktualisierung des Blickwinkels – ausgehend von der Kameraebene (Blickrichtung des Spielers) – und des Abstands, um den sich der Blickwinkel seit der letzten Controllerabfrage bewegt hat.</span><span class="sxs-lookup"><span data-stu-id="3227b-239">If time remains, the move-look controller is polled for an update to the camera position; specifically, an update to the angle of the view normal projecting from the camera plane (where the player is looking), and the distance that angle has moved from the previous time the controller was polled.</span></span>
4.  <span data-ttu-id="3227b-240">Die Kamera wird auf der Grundlage der neuen Daten des Bewegungs- und Blickrichtungscontrollers aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-240">The camera is updated based on the new data from the move-look controller.</span></span>
5.  <span data-ttu-id="3227b-241">Die Dynamik (also die Animationen und das Verhalten von Objekten in der Spielwelt, die nicht vom Spieler gesteuert werden) wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-241">The dynamics, or the animations and behaviors of objects in the game world independent of player control, are updated.</span></span> <span data-ttu-id="3227b-242">Im Beispielspiel sind das die Kugeln für die abgefeuerte Munition, die Animationen der Säulenhindernisse und die Bewegung der Ziele.</span><span class="sxs-lookup"><span data-stu-id="3227b-242">In the game sample, this is the motion of the ammo spheres that have been fired, the animation of the pillar obstacles and the movement of the targets.</span></span>
6.  <span data-ttu-id="3227b-243">Die Methode überprüft, ob die Kriterien für den erfolgreichen Abschluss eines Levels erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="3227b-243">The method checks to see if the criteria for the successful completion of a level have been met.</span></span> <span data-ttu-id="3227b-244">Ist dies der Fall, wird der endgültige Punktestand für das Level festgelegt und überprüft, ob es sich um das letzte Level (von sechs) handelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-244">If so, it finalizes the score for the level and checks to see if this is the last level (of 6).</span></span> <span data-ttu-id="3227b-245">Ist dies der Fall, gibt die Methode den Spielzustand **GameComplete** zurück. Andernfalls gibt sie den Spielzustand **LevelComplete** zurück.</span><span class="sxs-lookup"><span data-stu-id="3227b-245">If it's the last level, the method returns the **GameComplete** game state; otherwise, it returns the **LevelComplete** game state.</span></span>
7.  <span data-ttu-id="3227b-246">Wurde das Level nicht abgeschlossen, legt die Methode den Spielzustand auf **Active** fest und springt zurück.</span><span class="sxs-lookup"><span data-stu-id="3227b-246">If the level isn't complete, the method sets the game state to **Active** and returns.</span></span>

<span data-ttu-id="3227b-247">Der Code für **RunGame** (in **Simple3DGame.cpp**) sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3227b-247">Here's what **RunGame**, found in **Simple3DGame.cpp**, looks like in code.</span></span>

```cpp
GameState Simple3DGame::RunGame()
{
    m_timer->Update();

    m_levelTimeRemaining = m_levelDuration - m_timer->PlayingTime();

    if (m_levelTimeRemaining <= 0.0f)
    {
        // Time expired, so the game is over.
        m_levelTimeRemaining = 0.0f;
        InitializeAmmo();
        m_timer->Reset();
        m_gameActive = false;
        m_levelActive = false;
        SaveState();

        if (m_totalHits > m_topScore.totalHits)
        {
            m_topScore.totalHits = m_totalHits;
            m_topScore.totalShots = m_totalShots;
            m_topScore.levelCompleted = m_currentLevel;

            SaveHighScore();
        }
        return GameState::TimeExpired;
    }
    else
    {
        // Time has not expired, so run one frame of game play.
        m_player->Velocity(m_controller->Velocity());
        m_camera->LookDirection(m_controller->LookDirection());

        UpdateDynamics();

        // Update the camera with the player position updates from the dynamics calculations.
        m_camera->Eye(m_player->Position());
        m_camera->LookDirection(m_controller->LookDirection());

        if (m_level[m_currentLevel]->Update(m_timer->PlayingTime(), m_timer->DeltaTime(), m_levelTimeRemaining, m_object))
        {
            // The level has been completed.
            m_levelActive = false;
            InitializeAmmo();

            if (m_currentLevel < m_levelCount-1)
            {
                // More levels to go so increment the level number.
                // Actual level loading will occur in the LoadLevelAsync / FinalizeLoadLevel
                // methods.
                m_timer->Reset();
                m_currentLevel++;
                m_levelBonusTime = m_levelTimeRemaining;
                SaveState();
                return GameState::LevelComplete;
            }
            else
            {
                // All levels have been completed.
                m_timer->Reset();
                m_gameActive = false;
                m_levelActive = false;
                SaveState();

                if (m_totalHits > m_topScore.totalHits)
                {
                    m_topScore.totalHits = m_totalHits;
                    m_topScore.totalShots = m_totalShots;
                    m_topScore.levelCompleted = m_currentLevel;

                    SaveHighScore();
                }
                return GameState::GameComplete;
            }
        }
    }
    return GameState::Active;
}}
```

<span data-ttu-id="3227b-248">Dabei ist besonders der folgende Aufruf interessant: `UpdateDynamics()`.</span><span class="sxs-lookup"><span data-stu-id="3227b-248">Here's the key call: `UpdateDynamics()`.</span></span> <span data-ttu-id="3227b-249">Er sorgt dafür, dass die Spielwelt lebendig wird.</span><span class="sxs-lookup"><span data-stu-id="3227b-249">It's what brings the game world to life.</span></span> <span data-ttu-id="3227b-250">Ausführlichere Infos gibt's im nächsten Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="3227b-250">Let's review it!</span></span>

## <a name="updating-the-game-world"></a><span data-ttu-id="3227b-251">Aktualisieren der Spielwelt</span><span class="sxs-lookup"><span data-stu-id="3227b-251">Updating the game world</span></span>


<span data-ttu-id="3227b-252">Bei einem schnellen und flüssigen Spielablauf entsteht das Gefühl einer *lebendigen* Spielwelt, die auch ohne Interaktion des Spielers in Bewegung ist.</span><span class="sxs-lookup"><span data-stu-id="3227b-252">A fast and fluid game experience is one where the world feels *alive*, where the game itself is in motion independent of player input.</span></span> <span data-ttu-id="3227b-253">Bäume wiegen sich im Wind, Wellen brechen sich an einer Küste, Maschinen qualmen und glänzen, und außerirdische Monster geifern.</span><span class="sxs-lookup"><span data-stu-id="3227b-253">Trees wave in the wind, waves crest along shore lines, machinery smokes and shines, and alien monsters stretch and salivate.</span></span> <span data-ttu-id="3227b-254">Stellen Sie sich im Gegensatz dazu eine Spielwelt vor, in der alles wie erstarrt ist und sich die Grafik nur als Reaktion auf eine Spielereingabe bewegt.</span><span class="sxs-lookup"><span data-stu-id="3227b-254">Imagine what a game would be like if everything was frozen, with the graphics only moving when the player provided input.</span></span> <span data-ttu-id="3227b-255">Das wäre nicht nur merkwürdig, sondern auch so ziemlich das Gegenteil von immersiv.</span><span class="sxs-lookup"><span data-stu-id="3227b-255">It'd be weird and not very, well, immersive.</span></span> <span data-ttu-id="3227b-256">Der Effekt der Immersion entsteht für den Spieler durch das Gefühl, Bestandteil einer lebenden, atmenden Welt zu sein.</span><span class="sxs-lookup"><span data-stu-id="3227b-256">Immersion, for the player, comes from the feeling of being an agent in a living, breathing world.</span></span>

<span data-ttu-id="3227b-257">Solange das Spiel nicht explizit angehalten wurde, sollte die Spielschleife die Spielwelt stetig aktualisieren und die Animationsroutinen ausführen – ganz gleich, ob diese vordefiniert sind oder auf Physikalgorithmen oder einfach nur auf dem Zufallsprinzip beruhen.</span><span class="sxs-lookup"><span data-stu-id="3227b-257">The game loop should always keep updating the game world and running the animation routines, be they canned or based on physical algorithms or just plain random, except when the game is specifically paused.</span></span> <span data-ttu-id="3227b-258">Im Beispielspiel wird dieses Prinzip als *Dynamik* bezeichnet. Es umfasst das Verhalten der Säulenhindernisse sowie die Bewegung und das physikalische Verhalten abgefeuerter Munitionskugeln.</span><span class="sxs-lookup"><span data-stu-id="3227b-258">In the game sample, this principle is called *dynamics*, and it encompasses the rise and fall of the pillar obstacles, and the motion and physical behaviors of the ammo spheres as they are fired.</span></span> <span data-ttu-id="3227b-259">Hierzu gehört auch die Interaktion zwischen Objekten (beispielsweise Kollisionen zwischen der Spielerkugel und der Welt oder zwischen der Munition und den Hindernissen oder Zielen).</span><span class="sxs-lookup"><span data-stu-id="3227b-259">It also encompasses the interaction between objects, including collisions between the player sphere and the world, or between the ammo and the obstacles and targets.</span></span>

<span data-ttu-id="3227b-260">Im Anschluss sehen Sie den Code, der diese Dynamik implementiert:</span><span class="sxs-lookup"><span data-stu-id="3227b-260">The code that implements these dynamics looks like this:</span></span>

```cpp
void Simple3DGame::UpdateDynamics()
{
    float timeTotal = m_timer->PlayingTime();
    float timeFrame = m_timer->DeltaTime();
    bool fire = m_controller->IsFiring();

#pragma region Shoot Ammo
    // Shoot ammo.
    if (fire)
    {
        static float lastFired;  // Timestamp of the last ammo fired.

        if (timeTotal < lastFired)
        {
            // timeTotal is not guarenteed to be monotomically increasing because it is
            // reset at each level.
            lastFired = timeTotal - GameConstants::Physics::AutoFireDelay;
        }

        if (timeTotal - lastFired >= GameConstants::Physics::AutoFireDelay)
        {
           // Compute the ammo firing behavior.
        }
    }
#pragma endregion

#pragma region Animate Objects
    for (uint32 i = 0; i < m_object.size(); i++)
    {
        if (m_object[i]->AnimatePosition())
        {
            // Animate targets and cylinders based on level parameters and global constants.
        }
    }
#pragma endregion

    // If the elapsed time is too long, we slice up the time and
    // handle physics over several passes.
    float timeLeft = timeFrame;
    float elapsedFrameTime;
    while (timeLeft > 0.0f)
    {
        elapsedFrameTime = min(timeLeft, GameConstants::Physics::FrameLength);
        timeLeft -= elapsedFrameTime;

        // Update the player position.
        m_player->Position(m_player->VectorPosition() + m_player->VectorVelocity() * elapsedFrameTime);

        // Do m_player / object intersections.
        for (uint32 a = 0; a < m_object.size(); a++)
        {
            if (m_object[a]->Active() && m_object[a] != m_player)
            {
                XMFLOAT3 contact;
                XMFLOAT3 normal;

                if (m_object[a]->IsTouching(m_player->Position(), m_player->Radius(), &contact, &normal))
                {
                    XMVECTOR oneToTwo;
                    oneToTwo = -XMLoadFloat3(&normal);

                    // The player is in contact with Object
                    float impact;
                    impact = XMVectorGetX(
                        XMVector3Dot (oneToTwo, m_player->VectorVelocity())
                        );
                    // Make sure that the player is actually headed towards the object at grazing angles; there
                    // could appear to be an impact when the player is actually already hit and moving away.
                    if (impact > 0.0f)
                    {
                        // Compute the normal and tangential components of the player's velocity.
                        XMVECTOR velocityOneNormal = XMVector3Dot(oneToTwo, m_player->VectorVelocity()) * oneToTwo;
                        XMVECTOR velocityOneTangent = m_player->VectorVelocity() - velocityOneNormal;

                        // Compute the post-collision velocity.
                        m_player->Velocity(velocityOneTangent - velocityOneNormal);

                        // Fix the positions so that the ball is exactly GameConstants::AmmoRadius from target.
                        float distanceToMove = m_player->Radius();
                        m_player->Position(XMLoadFloat3(&contact) - (oneToTwo * distanceToMove));
                    }
                }
            }
        }
        {
            // Do collision detection of the player with the bounding world.
            XMFLOAT3 position = m_player->Position();
            XMFLOAT3 velocity = m_player->Velocity();
            float radius = m_player->Radius();

            // Check for player collisions with the walls, floor, or ceiling
            // and adjust the position.

            float limit = m_minBound.x + radius;
            if (position.x < limit)
            {
                position.x = limit;
                velocity.x = -velocity.x * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.x - radius;
            if (position.x > limit)
            {
                position.x = limit;
                velocity.x = -velocity.x + GameConstants::Physics::GroundRestitution;
            }
            limit = m_minBound.y + radius;
            if (position.y < limit)
            {
                position.y = limit;
                velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.y - radius;
            if (position.y > limit)
            {
                position.y = limit;
                velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;
            }
            limit = m_minBound.z + radius;
            if (position.z < limit)
            {
                position.z = limit;
                velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.z - radius;
            if (position.z > limit)
            {
                position.z = limit;
                velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
            }
            m_player->Position(position);
            m_player->Velocity(velocity);
        }

        // Animate the ammo.
        if (m_ammoCount > 0)
        {
            // Check for inter-ammo collision.
#pragma region inter-ammo collision detection
            if (m_ammoCount > 1)
            {
                for (uint32 one = 0; one < m_ammoCount; one++)
                {
                    for (uint32 two = (one + 1); two < m_ammoCount; two++)
                    {
                        // Compute checks for collisions for each ammo object with the other active ammo objects.
                    }
                }
            }
#pragma endregion

#pragma region Ammo-Object intersections
            // Check for intersections with Objects.
            for (uint32 one = 0; one < m_ammoCount; one++)
            {
                // Compute ammo collisions with game objects (targets, cylinders, walls).
            }
#pragma endregion

#pragma region Apply Gravity and world intersection
            // Apply gravity and check for collision against ground and walls.
            for (uint32 i = 0; i < m_ammoCount; i++)
            {
                                                      // Compute the effect of gravity on the ammo, and any ammo collisions with the world objects (walls, floor).
            }
        }
    }

}
```

<span data-ttu-id="3227b-261">(Dieses Codebeispiel wurde zur einfacheren Lesbarkeit gekürzt.</span><span class="sxs-lookup"><span data-stu-id="3227b-261">(This code example has been abbreviated for readability.</span></span> <span data-ttu-id="3227b-262">Der vollständige Code ist im vollständigen Codebeispiel am Ende dieses Themas enthalten.)</span><span class="sxs-lookup"><span data-stu-id="3227b-262">The full working code is found in the complete code sample at the bottom of this topic.)</span></span>

<span data-ttu-id="3227b-263">Diese Methode behandelt vierBerechnungssätze:</span><span class="sxs-lookup"><span data-stu-id="3227b-263">This method deals with four sets of computations:</span></span>

-   <span data-ttu-id="3227b-264">Die Positionen der Kugeln für die abgefeuerte Munition in der Spielwelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-264">The positions of the fired ammo spheres in the world.</span></span>
-   <span data-ttu-id="3227b-265">Die Animation der Säulenhindernisse.</span><span class="sxs-lookup"><span data-stu-id="3227b-265">The animation of the pillar obstacles.</span></span>
-   <span data-ttu-id="3227b-266">Die Überschneidung des Spielers mit den Begrenzungen der Spielwelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-266">The intersection of the player and the world boundaries.</span></span>
-   <span data-ttu-id="3227b-267">Die Kollisionen von Munitionskugeln mit den Hindernissen, den Zielen, anderen Munitionskugeln und der Spielwelt.</span><span class="sxs-lookup"><span data-stu-id="3227b-267">The collisions of the ammo spheres with the obstacles, the targets, other ammo spheres, and the world.</span></span>

<span data-ttu-id="3227b-268">Bei der Animation der Hindernisse handelt es sich um eine in **Animate.h/.cpp** definierte Schleife.</span><span class="sxs-lookup"><span data-stu-id="3227b-268">The animation of the obstacles is a loop defined in **Animate.h/.cpp**.</span></span> <span data-ttu-id="3227b-269">Das Verhalten der Munition und sämtlicher Kollisionen wird mithilfe vereinfachter Physikalgorithmen definiert. Diese werden im vorherigen Code angegeben und durch einen Satz von globalen Konstanten für die Spielwelt (wie Schwerkraft und Materialeigenschaften) parametrisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-269">The behavior of the ammo and any collisions are defined by simplified physics algorithms, supplied in the previous code and parameterized by a set of global constants for the game world, including gravity and material properties.</span></span> <span data-ttu-id="3227b-270">All dies wird im Koordinatenbereich der Spielwelt berechnet.</span><span class="sxs-lookup"><span data-stu-id="3227b-270">This is all computed in the game world coordinate space.</span></span>

<span data-ttu-id="3227b-271">Nachdem wir nun alle Objekte in der Szene aktualisiert und sämtliche Kollisionen berechnet haben, müssen wir die entsprechenden sichtbaren Veränderungen unter Berücksichtigung dieser neuen Infos zeichnen.</span><span class="sxs-lookup"><span data-stu-id="3227b-271">Now that we've updated all the objects in the scene and calculated any collisions, we need to use that info to draw the corresponding visual changes.</span></span> <span data-ttu-id="3227b-272">Unmittelbar nach Abschluss der Aktualisierung in der aktuellen Iteration der Spielschleife wird **Render** aufgerufen, um mithilfe der aktualisierten Objektdaten eine neue Szene zu generieren und dem Spieler zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="3227b-272">After Update completes in the current iteration of the game loop, the sample immediately calls **Render** to take the updated object data and generate a new scene to present to the player.</span></span>

<span data-ttu-id="3227b-273">Werfen wir doch gleich einmal einen Blick auf die Rendermethode.</span><span class="sxs-lookup"><span data-stu-id="3227b-273">Let's look at the render method now.</span></span>

## <a name="rendering-the-game-worlds-graphics"></a><span data-ttu-id="3227b-274">Rendern der Spielweltgrafik</span><span class="sxs-lookup"><span data-stu-id="3227b-274">Rendering the game world's graphics</span></span>


<span data-ttu-id="3227b-275">Wir empfehlen, die Grafik in einem Spiel so oft wie möglich (im Höchstfall also bei jeder Iteration der Hauptschleife des Spiels) zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3227b-275">We recommend that the graphics in a game update as often as possible, which, at maximum, is every time the main game loop iterates.</span></span> <span data-ttu-id="3227b-276">Im Zuge der Schleifeniteration wird das Spiel unabhängig von einer Spielereingabe aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3227b-276">As the loop iterates, the game is updated, with or without player input.</span></span> <span data-ttu-id="3227b-277">Dies ermöglicht eine flüssige Darstellung der berechneten Animationen und Verhalten.</span><span class="sxs-lookup"><span data-stu-id="3227b-277">This allows the animations and behaviors that are calculated to be displayed smoothly.</span></span> <span data-ttu-id="3227b-278">Stellen Sie sich nur einmal eine einfache Szene mit Wasser vor, das sich nur bewegt, wenn der Spieler eine Taste drückt.</span><span class="sxs-lookup"><span data-stu-id="3227b-278">Imagine if we had a simple scene of water that only moved when the player pressed a button.</span></span> <span data-ttu-id="3227b-279">Das Ergebnis wäre eine schrecklich langweilige Grafik.</span><span class="sxs-lookup"><span data-stu-id="3227b-279">That would make for terribly boring visuals.</span></span> <span data-ttu-id="3227b-280">Ein gutes Spiel wird ruckelfrei und flüssig dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3227b-280">A good game looks smooth and fluid.</span></span>

<span data-ttu-id="3227b-281">Rufen Sie erneut die Schleife des Beispielspiels auf, wie im Anschluss zu sehen.</span><span class="sxs-lookup"><span data-stu-id="3227b-281">Recall the sample game's loop, as shown here.</span></span> <span data-ttu-id="3227b-282">Ist das Hauptfenster des Spiels sichtbar und nicht angedockt oder deaktiviert, werden weiterhin Updates für das Spiel ausgeführt und die Ergebnisse gerendert.</span><span class="sxs-lookup"><span data-stu-id="3227b-282">If the game's main window is visible, and isn't snapped or deactivated, the game continues to update and render the results of that update.</span></span>

```cpp
void App::Run()
{
    while (!m_windowClosed)
    {
        if (m_visible)
        {
            switch (m_updateState)
            {
            case UpdateEngineState::Deactivated:
            case UpdateEngineState::Snapped:
                if (!m_renderNeeded)
                {
                    // The App is not currently the active window, so just wait for events.
                    CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
                    break;
                }
                // Otherwise, fall through and do normal processing to get the rendering handled.
            default:
                CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);
                Update();
                m_renderer->Render();
                m_renderNeeded = false;
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
    m_game->OnSuspending();  // Exiting due to window close.  Make sure to save state.
}
```

<span data-ttu-id="3227b-283">Die Methode, mit der wir uns jetzt beschäftigen, rendert eine Darstellung dieses Zustands umgehend nach der Aktualisierung des Zustands in **Run** mit einem Aufruf von **Update** (siehe vorheriger Abschnitt).</span><span class="sxs-lookup"><span data-stu-id="3227b-283">The method we examine now renders a representation of that state immediately after the state is updated in **Run** with a call to **Update**, which we discussed in the previous section.</span></span>

```cpp
void GameRenderer::Render()
{
    int renderingPasses = 1;
    if (m_stereoEnabled)
    {
        renderingPasses = 2;
    }

    for (int i = 0; i < renderingPasses; i++)
    {
        if (m_stereoEnabled && i > 0)
        {
            // Doing the Right Eye View
            m_d3dContext->OMSetRenderTargets(1, m_renderTargetViewRight.GetAddressOf(), m_depthStencilView.Get());
            m_d3dContext->ClearDepthStencilView(m_depthStencilView.Get(), D3D11_CLEAR_DEPTH, 1.0f, 0);
            m_d2dContext->SetTarget(m_d2dTargetBitmapRight.Get());
        }
        else
        {
            // Doing the Mono or Left Eye View
            m_d3dContext->OMSetRenderTargets(1, m_renderTargetView.GetAddressOf(), m_depthStencilView.Get());
            m_d3dContext->ClearDepthStencilView(m_depthStencilView.Get(), D3D11_CLEAR_DEPTH, 1.0f, 0);
            m_d2dContext->SetTarget(m_d2dTargetBitmap.Get());
        }

        if (m_game != nullptr && m_gameResourcesLoaded && m_levelResourcesLoaded)
        {
            // This section is only used after the game state has been initialized and all device
            // resources needed for the game have been created and associated with the game objects.
            if (m_stereoEnabled)
            {
                ConstantBufferChangeOnResize changesOnResize;
                XMStoreFloat4x4(
                    &changesOnResize.projection,
                    XMMatrixMultiply(
                        XMMatrixTranspose(
                            i == 0 ?
                            m_game->GameCamera()->LeftEyeProjection() :
                            m_game->GameCamera()->RightEyeProjection()
                            ),
                        XMMatrixTranspose(XMLoadFloat4x4(&m_rotationTransform3D))
                        )
                    );

                m_d3dContext->UpdateSubresource(
                    m_constantBufferChangeOnResize.Get(),
                    0,
                    nullptr,
                    &changesOnResize,
                    0,
                    0
                    );
            }
            // Update variables that change one time per frame.

            ConstantBufferChangesEveryFrame constantBufferChangesEveryFrame;
            XMStoreFloat4x4(
                &constantBufferChangesEveryFrame.view,
                XMMatrixTranspose(m_game->GameCamera()->View())
                );
            m_d3dContext->UpdateSubresource(
                m_constantBufferChangesEveryFrame.Get(),
                0,
                nullptr,
                &constantBufferChangesEveryFrame,
                0,
                0
                );

            // Set up the Pipeline.

            m_d3dContext->IASetInputLayout(m_vertexLayout.Get());
            m_d3dContext->VSSetConstantBuffers(0, 1, m_constantBufferNeverChanges.GetAddressOf());
            m_d3dContext->VSSetConstantBuffers(1, 1, m_constantBufferChangeOnResize.GetAddressOf());
            m_d3dContext->VSSetConstantBuffers(2, 1, m_constantBufferChangesEveryFrame.GetAddressOf());
            m_d3dContext->VSSetConstantBuffers(3, 1, m_constantBufferChangesEveryPrim.GetAddressOf());

            m_d3dContext->PSSetConstantBuffers(2, 1, m_constantBufferChangesEveryFrame.GetAddressOf());
            m_d3dContext->PSSetConstantBuffers(3, 1, m_constantBufferChangesEveryPrim.GetAddressOf());
            m_d3dContext->PSSetSamplers(0, 1, m_samplerLinear.GetAddressOf());

            // Get all the objects to render from the Game state.
            auto objects = m_game->RenderObjects();
            for (auto object = objects.begin(); object != objects.end(); object++)
            {
                (*object)->Render(m_d3dContext.Get(), m_constantBufferChangesEveryPrim.Get());
            }
        }
        else
        {
            const float ClearColor[4] = {0.1f, 0.1f, 0.1f, 1.0f};

            // Only need to clear the background when not rendering the full 3D scene because
            // the 3D world is a fully enclosed box, and the dynamics prevents the camera from
            // moving outside this space.
            if (m_stereoEnabled && i > 0)
            {
                // Doing the Right Eye View.
                m_d3dContext->ClearRenderTargetView(m_renderTargetViewRight.Get(), ClearColor);
            }
            else
            {
                // Doing the Mono or Left Eye View.
                m_d3dContext->ClearRenderTargetView(m_renderTargetView.Get(), ClearColor);
            }
        }

        m_d2dContext->BeginDraw();

        // To handle the swapchain being pre-rotated, set the D2D transformation to include it.
        m_d2dContext->SetTransform(m_rotationTransform2D);

        if (m_game != nullptr && m_gameResourcesLoaded)
        {
            // This is only used after the game state has been initialized.
            m_gameHud->Render(m_game, m_d2dContext.Get(), m_windowBounds);
        }

        if (m_gameInfoOverlay->Visible())
        {
            m_d2dContext->DrawBitmap(
                m_gameInfoOverlay->Bitmap(),
                D2D1::RectF(
                    (m_windowBounds.Width - GameInfoOverlayConstant::Width)/2.0f,
                    (m_windowBounds.Height - GameInfoOverlayConstant::Height)/2.0f,
                    (m_windowBounds.Width - GameInfoOverlayConstant::Width)/2.0f + GameInfoOverlayConstant::Width,
                    (m_windowBounds.Height - GameInfoOverlayConstant::Height)/2.0f + GameInfoOverlayConstant::Height
                    )
                );
        }

        HRESULT hr = m_d2dContext->EndDraw();
        if (hr != D2DERR_RECREATE_TARGET)
        {
            // The D2DERR_RECREATE_TARGET indicates there has been a problem with the underlying
            // D3D device.  All subsequent rendering will be ignored until the device is recreated.
            // This error will be propagated and the appropriate D3D error will be returned from the
            // swapchain->Present(...) call.   At that point, the sample will recreate the device
            // and all associated resources.  As a result the D2DERR_RECREATE_TARGET doesn't
            // need to be handled here.
            DX::ThrowIfFailed(hr);
        }
    }
    Present();
}
```

<span data-ttu-id="3227b-284">Den vollständigen Code für diese Methode finden Sie in [Zusammensetzen des Renderingframeworks](tutorial--assembling-the-rendering-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="3227b-284">The complete code for this method is in [Assembling the rendering framework](tutorial--assembling-the-rendering-pipeline.md).</span></span>

<span data-ttu-id="3227b-285">Diese Methode zeichnet die Projektion der dreidimensionalen Welt und legt anschließend das Direct2D-Overlay darüber.</span><span class="sxs-lookup"><span data-stu-id="3227b-285">This method draws the projection of the 3D world, and then draws the Direct2D overlay on top of it.</span></span> <span data-ttu-id="3227b-286">Nach Abschluss des Vorgangs zeigt sie die finale Swapchain mit den kombinierten Puffern an.</span><span class="sxs-lookup"><span data-stu-id="3227b-286">When completed, it presents the final swap chain with the combined buffers for display.</span></span>

<span data-ttu-id="3227b-287">Beachten Sie, dass für das Direct2D-Overlay zwei Zustände möglich sind: In einem Zustand zeigt das Spiel das Overlay mit den Spielinfos an, das die Bitmap für das Pausenmenü enthält. Im anderen Zustand zeigt das Spiel das Fadenkreuz sowie die Rechtecke für den Bewegungs- und Blickrichtungscontroller auf dem Touchscreen an.</span><span class="sxs-lookup"><span data-stu-id="3227b-287">Be aware that there are two states for the sample game's Direct2D overlay: one where the game displays the game info overlay that contains the bitmap for the pause menu, and one where the game displays the cross hairs along with the rectangles for the touchscreen move-look controller.</span></span> <span data-ttu-id="3227b-288">Der Text mit dem Spielstand wird in beiden Zuständen gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3227b-288">The score text is drawn in both states.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3227b-289">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="3227b-289">Next steps</span></span>


<span data-ttu-id="3227b-290">Inzwischen sind Sie sicher schon gespannt auf die eigentliche Rendering-Engine und möchten wissen, wie die Aufrufe der **Render**-Methoden für die aktualisierten Grundtypen in Bildschirmpixel verwandelt werden.</span><span class="sxs-lookup"><span data-stu-id="3227b-290">By now, you're probably curious about the actual rendering engine: how those calls to the **Render** methods on the updated primitives get turned into pixels on your screen.</span></span> <span data-ttu-id="3227b-291">Darauf gehen wir in [Zusammensetzen des Renderingframeworks](tutorial--assembling-the-rendering-pipeline.md) genauer ein.</span><span class="sxs-lookup"><span data-stu-id="3227b-291">We cover that in detail in [Assembling the rendering framework](tutorial--assembling-the-rendering-pipeline.md).</span></span> <span data-ttu-id="3227b-292">Sollten Sie sich dagegen mehr für die Aktualisierung des Spielzustands durch die Spielersteuerung interessieren, finden Sie entsprechende Informationen unter [Hinzufügen von Steuerelementen](tutorial--adding-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3227b-292">If you're more interested in how the player controls update the game state, then check out [Adding controls](tutorial--adding-controls.md).</span></span>

## <a name="complete-code-sample-for-this-section"></a><span data-ttu-id="3227b-293">Vollständiges Codebeispiel für diesen Abschnitt</span><span class="sxs-lookup"><span data-stu-id="3227b-293">Complete code sample for this section</span></span>


<span data-ttu-id="3227b-294">Simple3DGame.h</span><span class="sxs-lookup"><span data-stu-id="3227b-294">Simple3DGame.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Game specific Classes
#include "GameConstants.h"
#include "Audio.h"
#include "Camera.h"
#include "Level.h"
#include "GameObject.h"
#include "GameTimer.h"
#include "MoveLookController.h"
#include "PersistentState.h"
#include "Sphere.h"
#include "GameRenderer.h"

//--------------------------------------------------------------------------------------

enum class GameState
{
    Waiting,
    Active,
    LevelComplete,
    TimeExpired,
    GameComplete,
};

typedef struct
{
    Platform::String^ tag;
    int totalHits;
    int totalShots;
    int levelCompleted;
} HighScoreEntry;

typedef std::vector<HighScoreEntry> HighScoreEntries;

//--------------------------------------------------------------------------------------

ref class GameRenderer;

ref class Simple3DGame
{
internal:
    Simple3DGame();

    void Initialize(
        _In_ MoveLookController^ controller,
        _In_ GameRenderer^ renderer
        );

    void LoadGame();
    concurrency::task<void> LoadLevelAsync();
    void FinalizeLoadLevel();
    void StartLevel();
    void PauseGame();
    void ContinueGame();
    GameState RunGame();

    void OnSuspending();
    void OnResuming();

    bool IsActivePlay()                         { return m_timer->Active(); }
    int LevelCompleted()                        { return m_currentLevel; };
    int TotalShots()                            { return m_totalShots; };
    int TotalHits()                             { return m_totalHits; };
    float BonusTime()                           { return m_levelBonusTime; };
    bool GameActive()                           { return m_gameActive; };
    bool LevelActive()                          { return m_levelActive; };
    HighScoreEntry HighScore()                  { return m_topScore; };
    Level^ CurrentLevel()                       { return m_level[m_currentLevel]; };
    float TimeRemaining()                       { return m_levelTimeRemaining; };
    Camera^ GameCamera()                        { return m_camera; };
    std::vector<GameObject^> RenderObjects()    { return m_renderObject; };

private:
    void LoadState();
    void SaveState();
    void SaveHighScore();
    void LoadHighScore();
    void InitializeAmmo();
    void UpdateDynamics();

    MoveLookController^                                 m_controller;
    GameRenderer^                                       m_renderer;
    Camera^                                             m_camera;

    Audio^                                              m_audioController;

    std::vector<Sphere^>                                m_ammo;
    uint32                                              m_ammoCount;
    uint32                                              m_ammoNext;

    HighScoreEntry                                      m_topScore;
    PersistentState^                                    m_savedState;

    GameTimer^                                          m_timer;
    bool                                                m_gameActive;
    bool                                                m_levelActive;
    int                                                 m_totalHits;
    int                                                 m_totalShots;
    float                                               m_levelDuration;
    float                                               m_levelBonusTime;
    float                                               m_levelTimeRemaining;
    std::vector<Level^>                                 m_level;
    uint32                                              m_levelCount;
    uint32                                              m_currentLevel;

    Sphere^                                             m_player;
    std::vector<GameObject^>                            m_object;           // Object list for intersections
    std::vector<GameObject^>                            m_renderObject;     // All objects to be rendered

    DirectX::XMFLOAT3                                   m_minBound;
    DirectX::XMFLOAT3                                   m_maxBound;
};
```

<span data-ttu-id="3227b-295">Simple3DGame.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-295">Simple3DGame.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "GameRenderer.h"

#include "DirectXSample.h"
#include "Level1.h"
#include "Level2.h"
#include "Level3.h"
#include "Level4.h"
#include "Level5.h"
#include "Level6.h"
#include "Animate.h"
#include "Sphere.h"
#include "Cylinder.h"
#include "Face.h"
#include "MediaReader.h"

using namespace concurrency;
using namespace DirectX;
using namespace Microsoft::WRL;
using namespace Windows::Storage;
using namespace Windows::UI::Core;

//----------------------------------------------------------------------

Simple3DGame::Simple3DGame():
    m_ammoCount(0),
    m_ammoNext(0),
    m_gameActive(false),
    m_levelActive(false),
    m_totalHits(0),
    m_totalShots(0),
    m_levelBonusTime(0.0),
    m_levelTimeRemaining(0.0),
    m_levelCount(0),
    m_currentLevel(0)
{
    m_topScore.totalHits = 0;
    m_topScore.totalShots = 0;
    m_topScore.levelCompleted = 0;
}

//----------------------------------------------------------------------

void Simple3DGame::Initialize(
    _In_ MoveLookController^ controller,
    _In_ GameRenderer^ renderer
    )
{
    // This method is expected to be called as an asynchronous task.
    // Make sure that you don't call rendering methods on the
    // m_renderer, as this would result in the D3D Context being
    // used in multiple threads, which is not allowed.

    m_controller = controller;
    m_renderer = renderer;

    m_audioController = ref new Audio;
    m_audioController->CreateDeviceIndependentResources();

    m_ammo = std::vector<Sphere^>(GameConstants::MaxAmmo);
    m_object = std::vector<GameObject^>();
    m_renderObject = std::vector<GameObject^>();
    m_level = std::vector<Level^>();

    m_savedState = ref new PersistentState();
    m_savedState->Initialize(ApplicationData::Current->LocalSettings->Values, "Game");

    m_timer = ref new GameTimer();

    // Create a sphere primitive to represent the player.
    // The sphere will be used to handle collisions and constrain the player in the world.
    // It is not rendered, so it is not added to the list of render objects.
    m_player = ref new Sphere(XMFLOAT3(0.0f, -1.3f, 4.0f), 0.2f);

    m_camera = ref new Camera;
    m_camera->SetProjParams(XM_PI / 2, 1.0f, 0.01f, 100.0f);
    m_camera->SetViewParams(
        m_player->Position(),            // Eye point in world coordinates.
        XMFLOAT3 (0.0f, 0.7f, 0.0f),     // Look at point in world coordinates.
        XMFLOAT3 (0.0f, 1.0f, 0.0f)      // The Up vector for the camera.
        );

    m_controller->Pitch(m_camera->Pitch());
    m_controller->Yaw(m_camera->Yaw());

    // Add the m_player object to the object list to do intersection calculations.
    m_object.push_back(m_player);
    m_player->Active(true);

    // Instantiate the world primitive.  This object maintains the geometry and
    // material properties of the walls, floor, and ceiling of the enclosing world.
    // The TargetId is used to identify the world objects, so that the right geometry
    // and textures can be associated with them later after those resources have
    // been created.
    GameObject^ world = ref new GameObject();
    world->TargetId(GameConstants::WorldFloorId);
    world->Active(true);
    m_renderObject.push_back(world);

    world = ref new GameObject();
    world->TargetId(GameConstants::WorldCeilingId);
    world->Active(true);
    m_renderObject.push_back(world);

    world = ref new GameObject();
    world->TargetId(GameConstants::WorldWallsId);
    world->Active(true);
    m_renderObject.push_back(world);

    // Min and max Bound are defining the world space of the game.
    // All camera motion and dynamics are confined to this space.
    m_minBound = XMFLOAT3(-4.0f, -3.0f, -6.0f);
    m_maxBound = XMFLOAT3(4.0f, 3.0f, 6.0f);

    // Instantiate the Cylinders for use in the various game levels.
    // Each cylinder has a different initial position, radius and direction vector,
    // but share a common set of material properties.
    for (int a = 0; a < GameConstants::MaxCylinders; a++)
    {
        Cylinder^ cylinder;
        switch (a)
        {
        case 0:
            cylinder = ref new Cylinder(XMFLOAT3(-2.0f, -3.0f, 0.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 1:
            cylinder = ref new Cylinder(XMFLOAT3(2.0f, -3.0f, 0.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 2:
            cylinder = ref new Cylinder(XMFLOAT3(0.0f, -3.0f, -2.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 3:
            cylinder = ref new Cylinder(XMFLOAT3(-1.5f, -3.0f, -4.0f), 0.25f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        case 4:
            cylinder = ref new Cylinder(XMFLOAT3(1.5f, -3.0f, -4.0f), 0.50f, XMFLOAT3(0.0f, 6.0f, 0.0f));
            break;
        }
        cylinder->Active(true);
        m_object.push_back(cylinder);
        m_renderObject.push_back(cylinder);
    }

    MediaReader^ mediaReader = ref new MediaReader;
    auto targetHitSound = mediaReader->LoadMedia("hit.wav");

    // Instantiate the targets for use in the game.
    // Each target has a different initial position, size and orientation,
    // but share a common set of material properties.
    // The target is defined by a position and two vectors that define both
    // the plane of the target in world space and the size of the parallelogram
    // based on the lengths of the vectors.
    // Each target is assigned a number for identification purposes.
    // The Target ID number is 1 based.
    // All targets has the same material properties.
    for (int a = 1; a < GameConstants::MaxTargets; a++)
    {
        Face^ target;
        switch (a)
        {
        case 1:
            target = ref new Face(XMFLOAT3(-2.5f, -1.0f, -1.5f), XMFLOAT3(-1.5f, -1.0f, -2.0f), XMFLOAT3(-2.5f, 1.0f, -1.5f));
            break;
        case 2:
            target = ref new Face(XMFLOAT3(-1.0f, 1.0f, -3.0f), XMFLOAT3(0.0f, 1.0f, -3.0f), XMFLOAT3(-1.0f, 2.0f, -3.0f));
            break;
        case 3:
            target = ref new Face(XMFLOAT3(1.5f, 0.0f, -3.0f), XMFLOAT3(2.5f, 0.0f, -2.0f), XMFLOAT3(1.5f, 2.0f, -3.0f));
            break;
        case 4:
            target = ref new Face(XMFLOAT3(-2.5f, -1.0f, -5.5f), XMFLOAT3(-0.5f, -1.0f, -5.5f), XMFLOAT3(-2.5f, 1.0f, -5.5f));
            break;
        case 5:
            target = ref new Face(XMFLOAT3(0.5f, -2.0f, -5.0f), XMFLOAT3(1.5f, -2.0f, -5.0f), XMFLOAT3(0.5f, 0.0f, -5.0f));
            break;
        case 6:
            target = ref new Face(XMFLOAT3(1.5f, -2.0f, -5.5f), XMFLOAT3(2.5f, -2.0f, -5.0f), XMFLOAT3(1.5f, 0.0f, -5.5f));
            break;
        case 7:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        case 8:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        case 9:
            target = ref new Face(XMFLOAT3(0.0f, 0.0f, 0.0f), XMFLOAT3(0.5f, 0.0f, 0.0f), XMFLOAT3(0.0f, 0.5f, 0.0f));
            break;
        }

        target->Target(true);
        target->TargetId(a);
        target->Active(true);
        target->HitSound(ref new SoundEffect());
        target->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            targetHitSound);

        m_object.push_back(target);
        m_renderObject.push_back(target);
    }

    // Instantiate a set of spheres to be used as ammunition for the game
    // and set the material properties of the spheres.
    auto ammoHitSound = mediaReader->LoadMedia("bounce.wav");

    for (int a = 0; a < GameConstants::MaxAmmo; a++)
    {
        m_ammo[a] = ref new Sphere;
        m_ammo[a]->Radius(GameConstants::AmmoRadius);
        m_ammo[a]->HitSound(ref new SoundEffect());
        m_ammo[a]->HitSound()->Initialize(
            m_audioController->SoundEffectEngine(),
            mediaReader->GetOutputWaveFormatEx(),
            ammoHitSound);
        m_ammo[a]->Active(false);
        m_renderObject.push_back(m_ammo[a]);
    }

    // Instantiate each of the game levels.  The Level class contains methods
    // that initialize the objects in the world for the given level and also
    // define any motion paths for the objects in that level.

    m_level.push_back(ref new Level1);
    m_level.push_back(ref new Level2);
    m_level.push_back(ref new Level3);
    m_level.push_back(ref new Level4);
    m_level.push_back(ref new Level5);
    m_level.push_back(ref new Level6);
    m_levelCount = static_cast<uint32>(m_level.size());

    // Load the top score from disk if it exists.
    LoadHighScore();

    // Load the currentScore for saved state.
    LoadState();

    m_controller->Active(false);
}

//----------------------------------------------------------------------

void Simple3DGame::LoadGame()
{
    m_player->Position(XMFLOAT3 (0.0f, -1.3f, 4.0f));

    m_camera->SetViewParams(
        m_player->Position(),             // Eye point in world coordinates.
        XMFLOAT3 (0.0f, 0.7f, 0.0f),     // Look at point in world coordinates.
        XMFLOAT3 (0.0f, 1.0f, 0.0f)      // The Up vector for the camera.
        );

    m_controller->Pitch(m_camera->Pitch());
    m_controller->Yaw(m_camera->Yaw());
    m_currentLevel = 0;
    m_levelTimeRemaining = 0.0f;
    m_levelBonusTime = m_levelTimeRemaining;
    m_levelDuration = m_level[m_currentLevel]->TimeLimit() + m_levelBonusTime;
    InitializeAmmo();
    m_totalHits = 0;
    m_totalShots = 0;
    m_gameActive = false;
    m_levelActive = false;
    m_timer->Reset();
}

//----------------------------------------------------------------------

task<void> Simple3DGame::LoadLevelAsync()
{
    // Initialize the level and spin up the async loading of the rendering
    // resources for the level.
    // This will run in a separate thread, so for Direct3D 11, only Device
    // methods are allowed.  Any DeviceContext method calls need to be 
    // done in FinalizeLoadLevel.

    m_level[m_currentLevel]->Initialize(m_object);
    m_levelDuration = m_level[m_currentLevel]->TimeLimit() + m_levelBonusTime;

    return m_renderer->LoadLevelResourcesAsync();
}

//----------------------------------------------------------------------

void Simple3DGame::FinalizeLoadLevel()
{
    // This method is called on the main thread, so Direct3D 11 DeviceContext
    // method calls are allowable here.

    SaveState();

    // Finalize the Level loading.
    m_renderer->FinalizeLoadLevelResources();
}

//----------------------------------------------------------------------

void Simple3DGame::StartLevel()
{
    m_timer->Reset();
    m_timer->Start();
    if (m_currentLevel == 0)
    {
        m_gameActive = true;
    }
    m_levelActive = true;
    m_controller->Active(true);
}

//----------------------------------------------------------------------

void Simple3DGame::PauseGame()
{
    m_timer->Stop();
    SaveState();
}

//----------------------------------------------------------------------

void Simple3DGame::ContinueGame()
{
    m_timer->Start();
    m_controller->Active(true);
}

//----------------------------------------------------------------------

GameState Simple3DGame::RunGame()
{
    m_timer->Update();

    m_levelTimeRemaining = m_levelDuration - m_timer->PlayingTime();

    if (m_levelTimeRemaining <= 0.0f)
    {
        // Time expired, so the game is over.
        m_levelTimeRemaining = 0.0f;
        InitializeAmmo();
        m_timer->Reset();
        m_gameActive = false;
        m_levelActive = false;
        SaveState();

        if (m_totalHits > m_topScore.totalHits)
        {
            m_topScore.totalHits = m_totalHits;
            m_topScore.totalShots = m_totalShots;
            m_topScore.levelCompleted = m_currentLevel;

            SaveHighScore();
        }
        return GameState::TimeExpired;
    }
    else
    {
        // Time has not expired, so run one frame of game play.
        m_player->Velocity(m_controller->Velocity());
        m_camera->LookDirection(m_controller->LookDirection());

        UpdateDynamics();

        // Update the Camera with the player position updates from the dynamics calculations.
        m_camera->Eye(m_player->Position());
        m_camera->LookDirection(m_controller->LookDirection());

        if (m_level[m_currentLevel]->Update(m_timer->PlayingTime(), m_timer->DeltaTime(), m_levelTimeRemaining, m_object))
        {
            // The level has been completed.
            m_levelActive = false;
            InitializeAmmo();

            if (m_currentLevel < m_levelCount-1)
            {
                // More levels to go so increment the level number.
                // Actual level loading will occur in the LoadLevelAsync / FinalizeLoadLevel
                // methods.
                m_timer->Reset();
                m_currentLevel++;
                m_levelBonusTime = m_levelTimeRemaining;
                SaveState();
                return GameState::LevelComplete;
            }
            else
            {
                // All levels have been completed.
                m_timer->Reset();
                m_gameActive = false;
                m_levelActive = false;
                SaveState();

                if (m_totalHits > m_topScore.totalHits)
                {
                    m_topScore.totalHits = m_totalHits;
                    m_topScore.totalShots = m_totalShots;
                    m_topScore.levelCompleted = m_currentLevel;

                    SaveHighScore();
                }
                return GameState::GameComplete;
            }
        }
    }
    return GameState::Active;
}

//----------------------------------------------------------------------

void Simple3DGame::OnSuspending()
{
    m_audioController->SuspendAudio();
}

//----------------------------------------------------------------------

void Simple3DGame::OnResuming()
{
    m_audioController->ResumeAudio();
}

//--------------------------------------------------------------------------------------

void Simple3DGame::UpdateDynamics()
{
    float timeTotal = m_timer->PlayingTime();
    float timeFrame = m_timer->DeltaTime();
    bool fire = m_controller->IsFiring();

#pragma region Shoot Ammo
    // Shoot ammo.
    if (fire)
    {
        static float lastFired;  // Timestamp of the last ammo fired.

        if (timeTotal < lastFired)
        {
            // timeTotal is not guarenteed to be monotomically increasing because it is
            // reset at each level.
            lastFired = timeTotal - GameConstants::Physics::AutoFireDelay;
        }

        if (timeTotal - lastFired >= GameConstants::Physics::AutoFireDelay)
        {
            // Get the inverse view matrix.
            XMMATRIX invView;
            XMVECTOR det;
            invView = XMMatrixInverse(&det, m_camera->View());

            // Compute the initial velocity in world space from camera space.
            XMFLOAT4 initialVelocity(0.0f, 0.0f, 15.0f, 0.0f);
            m_ammo[m_ammoNext]->Velocity(XMVector4Transform(XMLoadFloat4(&initialVelocity), invView));

            // Populate the position.
            // Offset from the player to avoid an initial collision with the player object.
            XMFLOAT4 initialPosition(0.0f, -0.15f, m_player->Radius() + GameConstants::AmmoSize, 1.0f);
            m_ammo[m_ammoNext]->Position(XMVector4Transform(XMLoadFloat4(&initialPosition), invView));

            // Initially not laying on the ground.
            m_ammo[m_ammoNext]->OnGround(false);
            m_ammo[m_ammoNext]->Active(true);

            // Set the position in the array of the next Ammo to use.
            // We will reuse ammo taking the least recently used after we've hit the
            // MaxAmmo in use.
            m_ammoNext = (m_ammoNext + 1) % GameConstants::MaxAmmo;
            m_ammoCount = min(m_ammoCount + 1, GameConstants::MaxAmmo);

            lastFired = timeTotal;
            m_totalShots++;
        }
    }
#pragma endregion

#pragma region Animate Objects
    for (uint32 i = 0; i < m_object.size(); i++)
    {
        if (m_object[i]->AnimatePosition())
        {
            m_object[i]->Position(m_object[i]->AnimatePosition()->Evaluate(timeTotal));
            if (m_object[i]->AnimatePosition()->IsFinished(timeTotal))
            {
                m_object[i]->AnimatePosition(nullptr);
            }
        }
    }
#pragma endregion

    // If the elapsed time is too long, we slice up the time and
    // handle physics over several passes.
    float timeLeft = timeFrame;
    float elapsedFrameTime;
    while (timeLeft > 0.0f)
    {
        elapsedFrameTime = min(timeLeft, GameConstants::Physics::FrameLength);
        timeLeft -= elapsedFrameTime;

        // Update the player position.
        m_player->Position(m_player->VectorPosition() + m_player->VectorVelocity() * elapsedFrameTime);

        // Do m_player / object intersections.
        for (uint32 a = 0; a < m_object.size(); a++)
        {
            if (m_object[a]->Active() && m_object[a] != m_player)
            {
                XMFLOAT3 contact;
                XMFLOAT3 normal;

                if (m_object[a]->IsTouching(m_player->Position(), m_player->Radius(), &contact, &normal))
                {
                    XMVECTOR oneToTwo;
                    oneToTwo = -XMLoadFloat3(&normal);

                    // The player is in contact with Object.
                    float impact;
                    impact = XMVectorGetX(
                        XMVector3Dot (oneToTwo, m_player->VectorVelocity())
                        );
                    // Make sure that the player is actually headed towards the object at grazing angles 
                    // could appear to be an impact when the player is actually already hit and moving away
                    if (impact > 0.0f)
                    {
                        // Compute the normal and tangential components of the player's velocity.
                        XMVECTOR velocityOneNormal = XMVector3Dot(oneToTwo, m_player->VectorVelocity()) * oneToTwo;
                        XMVECTOR velocityOneTangent = m_player->VectorVelocity() - velocityOneNormal;

                        // Compute the post-collision velocity.
                        m_player->Velocity(velocityOneTangent - velocityOneNormal);

                        // Fix the positions so that the ball is exactly GameConstants::AmmoRadius from target.
                        float distanceToMove = m_player->Radius();
                        m_player->Position(XMLoadFloat3(&contact) - (oneToTwo * distanceToMove));
                    }
                }
            }
        }
        {
            // Do collision detection of the player with the bounding world.
            XMFLOAT3 position = m_player->Position();
            XMFLOAT3 velocity = m_player->Velocity();
            float radius = m_player->Radius();

            // Check for player collisions with the walls, floor, or ceiling
            // and adjust the position.

            float limit = m_minBound.x + radius;
            if (position.x < limit)
            {
                position.x = limit;
                velocity.x = -velocity.x * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.x - radius;
            if (position.x > limit)
            {
                position.x = limit;
                velocity.x = -velocity.x + GameConstants::Physics::GroundRestitution;
            }
            limit = m_minBound.y + radius;
            if (position.y < limit)
            {
                position.y = limit;
                velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.y - radius;
            if (position.y > limit)
            {
                position.y = limit;
                velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;
            }
            limit = m_minBound.z + radius;
            if (position.z < limit)
            {
                position.z = limit;
                velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
            }
            limit = m_maxBound.z - radius;
            if (position.z > limit)
            {
                position.z = limit;
                velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
            }
            m_player->Position(position);
            m_player->Velocity(velocity);
        }

        // Animate the ammo.
        if (m_ammoCount > 0)
        {
            // Check for inter-ammo collision.
#pragma region inter-ammo collision detection
            if (m_ammoCount > 1)
            {
                for (uint32 one = 0; one < m_ammoCount; one++)
                {
                    for (uint32 two = (one + 1); two < m_ammoCount; two++)
                    {
                        // Check for collision between instances One and Two.
                        // vOneToTwo is the collision normal vector.
                        XMVECTOR oneToTwo;
                        oneToTwo = m_ammo[two]->VectorPosition() - m_ammo[one]->VectorPosition();
                        float distanceSquared;
                        distanceSquared = XMVectorGetX(
                            XMVector3LengthSq(oneToTwo)
                            );
                        if (distanceSquared < (GameConstants::AmmoSize * GameConstants::AmmoSize))
                        {
                            oneToTwo = XMVector3Normalize(oneToTwo);

                            // Check if the two instances are already moving away from each other.
                            // If so, skip the collision.  This can happen when a lot of instances are
                            // bunched up next to each other.
                            float impact;
                            impact = XMVectorGetX(
                                XMVector3Dot(oneToTwo, m_ammo[one]->VectorVelocity()) -
                                XMVector3Dot(oneToTwo, m_ammo[two]->VectorVelocity())
                                );
                            if (impact > 0.0f)
                            {
                                // Compute the normal and tangential components of One's velocity.
                                XMVECTOR velocityOneNormal = (1 - GameConstants::Physics::BounceLost) *
                                    XMVector3Dot(oneToTwo, m_ammo[one]->VectorVelocity()) * oneToTwo;
                                XMVECTOR velocityOneTangent = (1 - GameConstants::Physics::BounceLost) *
                                    m_ammo[one]->VectorVelocity() - velocityOneNormal;
                                // Compute the normal and tangential components of Two's velocity.
                                XMVECTOR velocityTwoN = (1 - GameConstants::Physics::BounceLost) *
                                    XMVector3Dot(oneToTwo, m_ammo[two]->VectorVelocity()) * oneToTwo;
                                XMVECTOR velocityTwoT = (1 - GameConstants::Physics::BounceLost) *
                                    m_ammo[two]->VectorVelocity() - velocityTwoN;

                                // Compute the post-collision velocity.
                                m_ammo[one]->Velocity(velocityOneTangent - velocityOneNormal * (1 - GameConstants::Physics::BounceTransfer) +
                                    velocityTwoN * GameConstants::Physics::BounceTransfer);
                                m_ammo[two]->Velocity(velocityTwoT - velocityTwoN * (1 - GameConstants::Physics::BounceTransfer) +
                                    velocityOneNormal * GameConstants::Physics::BounceTransfer);

                                // Fix the positions so that the two balls are exactly GameConstants::AmmoSize apart.
                                float distanceToMove = (GameConstants::AmmoSize - sqrtf(distanceSquared)) * 0.5f;
                                m_ammo[one]->Position(m_ammo[one]->VectorPosition() - (oneToTwo * distanceToMove));
                                m_ammo[two]->Position(m_ammo[two]->VectorPosition() + (oneToTwo * distanceToMove));

                                // Flag the two instances so that they are not laying on ground.
                                m_ammo[one]->OnGround(false);
                                m_ammo[two]->OnGround(false);

                                m_ammo[one]->PlaySound(impact, m_player->Position());
                                m_ammo[two]->PlaySound(impact, m_player->Position());
                            }
                        }
                    }
                }
            }
#pragma endregion

#pragma region Ammo-Object intersections
            // Check for intersections with Objects.
            for (uint32 one = 0; one < m_ammoCount; one++)
            {
                if (m_object.size() > 0)
                {
                    if (!m_ammo[one]->OnGround())
                    {
                        for (uint32 i = 0; i < m_object.size(); i++)
                        {
                            if (m_object[i]->Active())
                            {
                                XMFLOAT3 contact;
                                XMFLOAT3 normal;

                                if (m_object[i]->IsTouching(m_ammo[one]->Position(), GameConstants::AmmoRadius, &contact, &normal))
                                {
                                    XMVECTOR oneToTwo;
                                    oneToTwo = -XMLoadFloat3(&normal);

                                    // Ball is in contact with the Object.
                                    float impact;
                                    impact = XMVectorGetX(
                                        XMVector3Dot (oneToTwo, m_ammo[one]->VectorVelocity())
                                        );
                                    // Make sure that the ball is actually headed towards the object at grazing angles. There
                                    // could appear to be an impact when the ball is actually already hit and moving away.
                                    if (impact > 0.0f)
                                    {
                                        // Compute the normal and tangential components of One's velocity.
                                        XMVECTOR velocityOneNormal = (1 - GameConstants::Physics::BounceLost) * XMVector3Dot(oneToTwo, m_ammo[one]->VectorVelocity()) * oneToTwo;
                                        XMVECTOR velocityOneTangent = (1 - GameConstants::Physics::BounceLost) * m_ammo[one]->VectorVelocity() - velocityOneNormal;

                                        // Compute the post-collision velocity.
                                        m_ammo[one]->Velocity(velocityOneTangent - velocityOneNormal * (1 - GameConstants::Physics::BounceTransfer));

                                        // Fix the positions so that the ball is exactly GameConstants::AmmoRadius from target.
                                        float distanceToMove = GameConstants::AmmoSize;
                                        m_ammo[one]->Position(XMLoadFloat3(&contact) - (oneToTwo * distanceToMove));

                                        // Flag the Ammo as not laying on the ground and mark the object as hit if it is a target.
                                        m_ammo[one]->OnGround(false);

                                        // Play the sound associated with the Ammo hitting something.
                                        m_ammo[one]->PlaySound(impact, m_player->Position());

                                        if (m_object[i]->Target() && !m_object[i]->Hit())
                                        {
                                            m_object[i]->Hit(true);
                                            m_object[i]->HitTime(timeTotal);
                                            m_totalHits++;

                                            // Only play target sound if it was an active hit.
                                            m_object[i]->PlaySound(impact, m_player->Position());
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
#pragma endregion

#pragma region Apply Gravity and world intersection
            // Apply gravity and check for collision against the ground and walls.
            for (uint32 i = 0; i < m_ammoCount; i++)
            {
                m_ammo[i]->Position(m_ammo[i]->VectorPosition() + m_ammo[i]->VectorVelocity() * elapsedFrameTime);

                XMFLOAT3 velocity = m_ammo[i]->Velocity();
                XMFLOAT3 position = m_ammo[i]->Position();

                velocity.x -= velocity.x * 0.1f * elapsedFrameTime;
                velocity.z -= velocity.z * 0.1f * elapsedFrameTime;
                // Apply gravity if the ball is not resting on the ground.
                if (!m_ammo[i]->OnGround())
                {
                    velocity.y -= GameConstants::Physics::Gravity * elapsedFrameTime;
                }

                // Check the bounce on the ground.
                if (!m_ammo[i]->OnGround())
                {
                    float limit = m_minBound.y + GameConstants::AmmoRadius;
                    if (position.y < limit)
                    {
                        // Align the ball with the ground.
                        position.y = limit;

                        // Play the sound for impact.
                        m_ammo[i]->PlaySound(-velocity.y, m_player->Position());

                        // Invert the Y velocity.
                        velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;

                        // X and Z velocity are reduced because of friction.
                        velocity.x *= GameConstants::Physics::Friction;
                        velocity.z *= GameConstants::Physics::Friction;
                    }
                }
                else
                {
                    // Ball is resting or rolling on the ground.
                    // X and Z velocity are reduced because of friction.
                    velocity.x *= GameConstants::Physics::Friction;
                    velocity.z *= GameConstants::Physics::Friction;
                }

                // Check the bounce on the ceiling.
                float limit = m_maxBound.y - GameConstants::AmmoRadius;
                if (position.y > limit)
                {
                    // Align the ball with the ground.
                    position.y = limit;

                    // Play the sound for impact.
                    m_ammo[i]->PlaySound(-velocity.y, m_player->Position());

                    // Invert the Y velocity.
                    velocity.y = -velocity.y * GameConstants::Physics::GroundRestitution;

                    // X and Z velocity are reduced because of friction.
                    velocity.x *= GameConstants::Physics::Friction;
                    velocity.z *= GameConstants::Physics::Friction;
                }

                // If the Y direction motion is below a certain threshold, flag the instance as
                // laying on the ground.
                limit = m_minBound.y + GameConstants::AmmoRadius;
                if ((GameConstants::Physics::Gravity * (position.y - limit) + 0.5f * velocity.y * velocity.y) < GameConstants::Physics::RestThreshold)
                {
                    // Align the ball with the ground.
                    position.y = limit;

                    // Y direction velocity becomes 0.
                    velocity.y = 0.0f;

                    // Flag it.
                    m_ammo[i]->OnGround(true);
                }

                // Check the bounce on the front and back walls.
                limit = m_minBound.z + GameConstants::AmmoRadius;
                if (position.z < limit)
                {
                    // Align the ball with the wall.
                    position.z = limit;

                    // Play the sound for impact.
                    m_ammo[i]->PlaySound(-velocity.z, m_player->Position());

                    // Invert the Z velocity.
                    velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
                }
                limit = m_maxBound.z - GameConstants::AmmoRadius;
                if (position.z > limit)
                {
                    // Align the ball with the wall.
                    position.z = limit;

                    // Play the sound for impact.
                    m_ammo[i]->PlaySound(-velocity.z, m_player->Position());

                    // Invert the Z velocity.
                    velocity.z = -velocity.z * GameConstants::Physics::GroundRestitution;
                }

                // Check the bounce on the left and right walls.
                limit = m_minBound.x + GameConstants::AmmoRadius;
                if (position.x < limit)
                {
                    // Align the ball with the wall.
                    position.x = limit;

                    // Play the sound for impact.
                    m_ammo[i]->PlaySound(-velocity.x, m_player->Position());

                    // Invert the X velocity.
                    velocity.x = -velocity.x * GameConstants::Physics::GroundRestitution;
                }
                limit = m_maxBound.x - GameConstants::AmmoRadius;
                if (position.x > limit)
                {
                    // Align the ball with the wall.
                    position.x = limit;

                    m_ammo[i]->PlaySound(-velocity.x, m_player->Position());

                    // Invert the X velocity.
                    velocity.x = -velocity.x * GameConstants::Physics::GroundRestitution;
                }
                m_ammo[i]->Velocity(velocity);
                m_ammo[i]->Position(position);
            }
        }
    }
#pragma endregion
}

//----------------------------------------------------------------------

void Simple3DGame::SaveState()
{
    // Save basic state of the game.
    m_savedState->SaveBool(":GameActive", m_gameActive);
    m_savedState->SaveBool(":LevelActive", m_levelActive);
    m_savedState->SaveInt32(":LevelCompleted", m_currentLevel);
    m_savedState->SaveInt32(":TotalShots", m_totalShots);
    m_savedState->SaveInt32(":TotalHits", m_totalHits);
    m_savedState->SaveSingle(":BonusRoundTime", m_levelBonusTime);
    m_savedState->SaveXMFLOAT3(":PlayerPosition", m_player->Position());
    m_savedState->SaveXMFLOAT3(":PlayerLookDirection", m_controller->LookDirection());

    // Save the extended state of the game because it is currently in the middle of a level.
    if (m_levelActive)
    {
        m_savedState->SaveSingle(":LevelDuration", m_levelDuration);
        m_savedState->SaveSingle(":LevelPlayingTime", m_timer->PlayingTime());

        m_savedState->SaveInt32(":AmmoCount", m_ammoCount);
        m_savedState->SaveInt32(":AmmoNext", m_ammoNext);

        const int bufferLength = 16;
        char16 str[bufferLength];

        for (uint32 i = 0; i < m_ammoCount; i++)
        {
            int len = swprintf_s(str, bufferLength, L"%d", i);
            Platform::String^ string = ref new Platform::String(str, len);

            m_savedState->SaveBool(Platform::String::Concat(":AmmoActive", string), m_ammo[i]->Active());
            m_savedState->SaveXMFLOAT3(Platform::String::Concat(":AmmoPosition", string), m_ammo[i]->Position());
            m_savedState->SaveXMFLOAT3(Platform::String::Concat(":AmmoVelocity", string), m_ammo[i]->Velocity());
        }

        m_savedState->SaveInt32(":ObjectCount", static_cast<int>(m_object.size()));

        for (uint32 i = 0; i < m_object.size(); i++)
        {
            int len = swprintf_s(str, bufferLength, L"%d", i);
            Platform::String^ string = ref new Platform::String(str, len);

            m_savedState->SaveBool(Platform::String::Concat(":ObjectActive", string), m_object[i]->Active());
            m_savedState->SaveBool(Platform::String::Concat(":ObjectTarget", string), m_object[i]->Target());
            m_savedState->SaveXMFLOAT3(Platform::String::Concat(":ObjectPosition", string), m_object[i]->Position());
        }

        m_level[m_currentLevel]->SaveState(m_savedState);
    }
}

//----------------------------------------------------------------------

void Simple3DGame::LoadState()
{
    m_gameActive = m_savedState->LoadBool(":GameActive", m_gameActive);
    m_levelActive = m_savedState->LoadBool(":LevelActive", m_levelActive);

    if (m_gameActive)
    {
        // Loading from the last known state means the Game wasn't finished when it was last played,
        // so set the current level.

        m_totalShots = m_savedState->LoadInt32(":TotalShots", 0);
        m_totalHits = m_savedState->LoadInt32(":TotalHits", 0);
        m_currentLevel = m_savedState->LoadInt32(":LevelCompleted", 0);
        m_levelBonusTime = m_savedState->LoadSingle(":BonusRoundTime", 0.0f);

        m_levelTimeRemaining = m_levelBonusTime;

        // Reload the current player position and set both the camera and the controller
        // with the current Look Direction.
        m_player->Position(
            m_savedState->LoadXMFLOAT3(":PlayerPosition", XMFLOAT3(0.0f, 0.0f, 0.0f))
            );
        m_camera->Eye(m_player->Position());
        m_camera->LookDirection(
            m_savedState->LoadXMFLOAT3(":PlayerLookDirection", XMFLOAT3(0.0f, 0.0f, 1.0f))
            );
        m_controller->Pitch(m_camera->Pitch());
        m_controller->Yaw(m_camera->Yaw());
    }
    else
    {
        // Initialize to the beginning.
        m_currentLevel = 0;
        m_levelBonusTime = 0;
    }

    // Initialize the state of the Update and Render engines and load the current level.
    m_level[m_currentLevel]->Initialize(m_object);

    m_levelDuration = m_level[m_currentLevel]->TimeLimit() + m_levelBonusTime;

    if (m_gameActive)
    {
        if (m_levelActive)
        {
            // Middle of a level so restart where left off.
            m_levelDuration = m_savedState->LoadSingle(":LevelDuration", 0.0f);

            m_timer->Reset();
            m_timer->PlayingTime(m_savedState->LoadSingle(":LevelPlayingTime", 0.0f));

            m_ammoCount = m_savedState->LoadInt32(":AmmoCount", 0);

            m_ammoNext = m_savedState->LoadInt32(":AmmoNext", 0);

            const int bufferLength = 16;
            char16 str[bufferLength];

            for (uint32 i = 0; i < m_ammoCount; i++)
            {
                int len = swprintf_s(str, bufferLength, L"%d", i);
                Platform::String^ string = ref new Platform::String(str, len);

                m_ammo[i]->Active(
                    m_savedState->LoadBool(
                        Platform::String::Concat(":AmmoActive", string),
                        m_ammo[i]->Active()
                        )
                    );
                if (m_ammo[i]->Active())
                {
                    m_ammo[i]->OnGround(false);
                }

                m_ammo[i]->Position(
                    m_savedState->LoadXMFLOAT3(
                        Platform::String::Concat(":AmmoPosition", string),
                        m_ammo[i]->Position()
                        )
                    );

                m_ammo[i]->Velocity(
                    m_savedState->LoadXMFLOAT3(
                        Platform::String::Concat(":AmmoVelocity", string),
                        m_ammo[i]->Velocity()
                        )
                    );
            }

            int storedObjectCount = 0;
            storedObjectCount = m_savedState->LoadInt32(":ObjectCount", 0);

            storedObjectCount = min(storedObjectCount, static_cast<int>(m_object.size()));

            for (int i = 0; i < storedObjectCount; i++)
            {
                int len = swprintf_s(str, bufferLength, L"%d", i);
                Platform::String^ string = ref new Platform::String(str, len);

                m_object[i]->Active(
                    m_savedState->LoadBool(
                        Platform::String::Concat(":ObjectActive", string),
                        m_object[i]->Active()
                        )
                    );

                m_object[i]->Target(
                    m_savedState->LoadBool(
                        Platform::String::Concat(":ObjectTarget", string),
                        m_object[i]->Target()
                        )
                    );

                m_object[i]->Position(
                    m_savedState->LoadXMFLOAT3(
                        Platform::String::Concat(":ObjectPosition", string),
                        m_object[i]->Position()
                        )
                    );
            }

            m_level[m_currentLevel]->LoadState(m_savedState);
            m_levelTimeRemaining = m_level[m_currentLevel]->TimeLimit() + m_levelBonusTime - m_timer->PlayingTime();
        }
    }
}

//----------------------------------------------------------------------

void Simple3DGame::SaveHighScore()
{
    m_savedState->SaveInt32(":HighScore:LevelCompleted", m_topScore.levelCompleted);
    m_savedState->SaveInt32(":HighScore:TotalShots", m_topScore.totalShots);
    m_savedState->SaveInt32(":HighScore:TotalHits", m_topScore.totalHits);
}

//----------------------------------------------------------------------

void Simple3DGame::LoadHighScore()
{
    m_topScore.levelCompleted = m_savedState->LoadInt32(":HighScore:LevelCompleted", 0);
    m_topScore.totalShots = m_savedState->LoadInt32(":HighScore:TotalShots", 0);
    m_topScore.totalHits = m_savedState->LoadInt32(":HighScore:TotalHits", 0);
}

//----------------------------------------------------------------------

void Simple3DGame::InitializeAmmo()
{
    m_ammoCount = 0;
    m_ammoNext = 0;
    for (uint32 i = 0; i < GameConstants::MaxAmmo; i++)
    {
        m_ammo[i]->Active(false);
    }
}
```

<span data-ttu-id="3227b-296">Level.h</span><span class="sxs-lookup"><span data-stu-id="3227b-296">Level.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level:
// This is an abstract class from which all of the levels of the game are derived.
// Each level potentially overrides up to four methods:
//     Initialize - (required) takes a list of objects and enables the objects that
//         are active for the level as well as setting their positions and
//         any animations associated with the objects.
//     Update - this method is called once per time step and is expected to
//         determine if the level has been completed.  The Level class provides
//         a 'standard' Update method which checks each object that is a target
//         and disables any active targets that have been hit.  It returns true
//         once there are no active targets remaining.
//     SaveState - method to save any Level specific state.  Default is defined as
//         not saving any state.
//     LoadState - method to restore any Level specific state.  Default is defined
//         as not restoring any state.

#include "GameObject.h"
#include "PersistentState.h"

ref class Level abstract
{
internal:
    virtual void Initialize(
        std::vector<GameObject^> objects
        ) = 0;

    virtual bool Update(
        float time,
        float elapsedTime,
        float timeRemaining,
        std::vector<GameObject^> objects
        );

    virtual void SaveState(PersistentState^ state);
    virtual void LoadState(PersistentState^ state);

    Platform::String^ Objective();
    float TimeLimit();

protected private:
    Platform::String^ m_objective;
    float             m_timeLimit;
};
            
            
```

<span data-ttu-id="3227b-297">Level.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-297">Level.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level.h"

//----------------------------------------------------------------------

bool Level::Update(
    float /* time */,
    float /* elapsedTime */,
    float /* timeRemaining*/,
    std::vector<GameObject^> objects
    )
{
    int left = 0;

    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if ((*object)->Active() && (*object)->Target())
        {
            if ((*object)->Hit())
            {
                (*object)->Active(false);
            }
            else
            {
                left++;
            }
        }
    }
    return (left == 0);
}

//----------------------------------------------------------------------

void Level::SaveState(PersistentState^ /* state */)
{
}

//----------------------------------------------------------------------

void Level::LoadState(PersistentState^ /* state */)
{
}

//----------------------------------------------------------------------

Platform::String^ Level::Objective()
{
    return m_objective;
}

//----------------------------------------------------------------------

float Level::TimeLimit()
{
    return m_timeLimit;
}

//----------------------------------------------------------------------            
            
```

<span data-ttu-id="3227b-298">Level1.h</span><span class="sxs-lookup"><span data-stu-id="3227b-298">Level1.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level1:
// This class defines the first level of the game.  There are nine active targets.
// Each of the targets is stationary and can be hit in any order.

#include "Level.h"

ref class Level1: public Level
{
internal:
    Level1();
    virtual void Initialize(std::vector<GameObject^> objects) override;
};
            
```

<span data-ttu-id="3227b-299">Level1.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-299">Level1.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level1.h"
#include "Face.h"

using namespace DirectX;

//----------------------------------------------------------------------

Level1::Level1()
{
    m_timeLimit = 20.0f;
    m_objective =  "Hit each of the targets before time runs out.\nTouch to aim.  Tap in right box to fire.  Drag in left box to move.";
}

//----------------------------------------------------------------------

void Level1::Initialize(std::vector<GameObject^> objects)
{
    XMFLOAT3 position[] =
    {
        XMFLOAT3(-2.5f, -1.0f, -1.5f),
        XMFLOAT3(-1.0f,  1.0f, -3.0f),
        XMFLOAT3( 1.5f,  0.0f, -3.0f),
        XMFLOAT3(-2.5f, -1.0f, -5.5f),
        XMFLOAT3( 0.5f, -2.0f, -5.0f),
        XMFLOAT3( 1.5f, -2.0f, -5.5f),
        XMFLOAT3( 2.0f,  0.0f,  0.0f),
        XMFLOAT3( 0.0f,  0.0f,  0.0f),
        XMFLOAT3(-2.0f,  0.0f,  0.0f)
    };

    int targetCount = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if (Face^ target = dynamic_cast<Face^>(*object))
        {
            if (targetCount < 9)
            {
                target->Active(true);
                target->Target(true);
                target->Hit(false);
                target->AnimatePosition(nullptr);
                target->Position(position[targetCount]);
                targetCount++;
            }
            else
            {
                (*object)->Active(false);
            }
        }
        else
        {
            (*object)->Active(false);
        }
    }
}

//----------------------------------------------------------------------
            
            
```

<span data-ttu-id="3227b-300">Level2.h</span><span class="sxs-lookup"><span data-stu-id="3227b-300">Level2.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level2:
// This class defines the second level of the game.  It derives from the
// first level.  In this level, the targets must be hit in numeric order.

#include "Level1.h"

ref class Level2: public Level1
{
internal:
    Level2();
    virtual void Initialize(std::vector<GameObject^> objects) override;

    virtual bool Update(
        float time,
        float elapsedTime,
        float timeRemaining,
        std::vector<GameObject^> objects
        ) override;

    virtual void SaveState(PersistentState^ state) override;
    virtual void LoadState(PersistentState^ state) override;

private:
    int m_nextId;
};
            
            
```

<span data-ttu-id="3227b-301">Level2.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-301">Level2.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level2.h"
#include "Face.h"

//----------------------------------------------------------------------

Level2::Level2()
{
    m_timeLimit = 30.0f;
    m_objective = "Hit each of the targets in ORDER before time runs out.";
}

//----------------------------------------------------------------------

void Level2::Initialize(std::vector<GameObject^> objects)
{
    Level1::Initialize(objects);

    int targetCount = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if (Face^ target = dynamic_cast<Face^>(*object))
        {
            if (targetCount < 9)
            {
                target->Target(targetCount == 0 ? true : false);
                targetCount++;
            }
        }
    }
    m_nextId = 1;
}

//----------------------------------------------------------------------

bool Level2::Update(
    float /* time */,
    float /* elapsedTime */,
    float /* timeRemaining */,
    std::vector<GameObject^> objects
    )
{
    int left = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if ((*object)->Active() && ((*object)->TargetId() > 0))
        {
            if ((*object)->Hit()  && ((*object)->TargetId() == m_nextId))
            {
                (*object)->Active(false);
                m_nextId++;
            }
            else
            {
                left++;
            }
        }
        if ((*object)->Active() && ((*object)->TargetId() == m_nextId))
        {
            (*object)->Target(true);
        }
    }
    return (left == 0);
}

//----------------------------------------------------------------------

void Level2::SaveState(PersistentState^ state)
{
    state->SaveInt32(":NextTarget", m_nextId);
}

//----------------------------------------------------------------------

void Level2::LoadState(PersistentState^ state)
{
    m_nextId = state->LoadInt32(":NextTarget", 1);
}

//----------------------------------------------------------------------            
            
```

<span data-ttu-id="3227b-302">Level3.h</span><span class="sxs-lookup"><span data-stu-id="3227b-302">Level3.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level3:
// This class defines the third level of the game.  In this level, each of the
// nine targets is moving along closed paths and can be hit
// in any order.

#include "Level.h"

ref class Level3: public Level
{
internal:
    Level3();
    virtual void Initialize(std::vector<GameObject^> objects) override;
};
            
            
```

<span data-ttu-id="3227b-303">Level3.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-303">Level3.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level3.h"
#include "Face.h"
#include "Animate.h"

using namespace DirectX;

//----------------------------------------------------------------------

Level3::Level3()
{
    m_timeLimit = 30.0f;
    m_objective = "Hit each of the moving targets before time runs out.";
}

//----------------------------------------------------------------------

void Level3::Initialize(std::vector<GameObject^> objects)
{
    XMFLOAT3 position[] =
    {
        XMFLOAT3(-2.5f, -1.0f, -1.5f),
        XMFLOAT3(-1.0f,  1.0f, -3.0f),
        XMFLOAT3( 1.5f,  0.0f, -5.5f),
        XMFLOAT3(-2.5f, -1.0f, -5.5f),
        XMFLOAT3( 0.5f, -2.0f, -5.0f),
        XMFLOAT3( 1.5f, -2.0f, -5.5f),
        XMFLOAT3( 0.0f, -3.6f,  0.0f),
        XMFLOAT3( 0.0f, -3.6f,  0.0f),
        XMFLOAT3( 0.0f, -3.6f,  0.0f)
    };
    XMFLOAT3 LineList1[] =
    {
        XMFLOAT3(-2.5f, -1.0f, -1.5f),
        XMFLOAT3(-0.5f,  1.0f,  1.0f),
        XMFLOAT3(-0.5f, -2.5f,  1.0f),
        XMFLOAT3(-2.5f, -1.0f, -1.5f),
    };
    XMFLOAT3 LineList2[] =
    {
        XMFLOAT3(-1.0f,  1.0f, -3.0f),
        XMFLOAT3(-2.0f,  2.0f, -1.5f),
        XMFLOAT3(-2.0f, -2.5f, -1.5f),
        XMFLOAT3( 1.5f, -2.5f, -1.5f),
        XMFLOAT3( 1.5f, -2.5f, -3.0f),
        XMFLOAT3(-1.0f,  1.0f, -3.0f),
    };
    XMFLOAT3 LineList3[] =
    {
        XMFLOAT3(1.5f,  0.0f, -5.5f),
        XMFLOAT3(1.5f,  1.0f, -5.5f),
        XMFLOAT3(1.5f, -2.5f, -5.5f),
        XMFLOAT3(1.5f,  0.0f, -5.5f),
    };
    XMFLOAT3 LineList4[] =
    {
        XMFLOAT3(-2.5f, -1.0f, -5.5f),
        XMFLOAT3( 1.0f, -1.0f, -5.5f),
        XMFLOAT3( 1.0f,  1.0f, -5.5f),
        XMFLOAT3(-2.5f,  1.0f, -5.5f),
        XMFLOAT3(-2.5f, -1.0f, -5.5f),
    };
    XMFLOAT3 LineList5[] =
    {
        XMFLOAT3( 0.5f, -2.0f, -5.0f),
        XMFLOAT3( 2.0f, -2.0f, -5.0f),
        XMFLOAT3( 2.0f,  1.0f, -5.0f),
        XMFLOAT3(-2.5f,  1.0f, -5.0f),
        XMFLOAT3(-2.5f, -2.0f, -5.0f),
        XMFLOAT3( 0.5f, -2.0f, -5.0f),
    };
    XMFLOAT3 LineList6[] =
    {
        XMFLOAT3( 1.5f, -2.0f, -5.5f),
        XMFLOAT3(-2.5f, -2.0f, -5.5f),
        XMFLOAT3(-2.5f,  1.0f, -5.5f),
        XMFLOAT3( 1.5f,  1.0f, -5.5f),
        XMFLOAT3( 1.5f, -2.0f, -5.5f),
    };

    int targetCount = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if (Face^ target = dynamic_cast<Face^>(*object))
        {
            if (targetCount < 9)
            {
                target->Active(true);
                target->Target(true);
                target->Hit(false);
                target->Position(position[targetCount]);
                switch (targetCount)
                {
                case 0:
                    target->AnimatePosition(ref new AnimateLineListPosition(4, LineList1, 10.0f, true));
                    break;
                case 1:
                    target->AnimatePosition(ref new AnimateLineListPosition(6, LineList2, 15.0f, true));
                    break;
                case 2:
                    target->AnimatePosition(ref new AnimateLineListPosition(4, LineList3, 15.0f, true));
                    break;
                case 3:
                    target->AnimatePosition(ref new AnimateLineListPosition(5, LineList4, 15.0f, true));
                    break;
                case 4:
                    target->AnimatePosition(ref new AnimateLineListPosition(6, LineList5, 15.0f, true));
                    break;
                case 5:
                    target->AnimatePosition(ref new AnimateLineListPosition(5, LineList6, 15.0f, true));
                    break;
                case 6:
                    target->AnimatePosition(
                        ref new AnimateCirclePosition(
                            XMFLOAT3(0.0f, -2.5f, 0.0f),
                            XMFLOAT3(0.0f, -3.6f, 0.0f),
                            XMFLOAT3(0.0f,  0.0f, 1.0f),
                            9.0f,
                            true,
                            true
                            )
                        );
                    break;
                case 7:
                    target->AnimatePosition(
                        ref new AnimateCirclePosition(
                            XMFLOAT3(0.0f, -2.5f, 0.0f),
                            XMFLOAT3(0.0f, -3.6f, 0.0f),
                            XMFLOAT3(0.0f,  0.0f, 1.0f),
                            9.0f,
                            true,
                            true
                            )
                        );
                    target->AnimatePosition()->Start(3.0f);
                    break;
                case 8:
                    target->AnimatePosition(
                        ref new AnimateCirclePosition(
                            XMFLOAT3(0.0f, -2.5f, 0.0f),
                            XMFLOAT3(0.0f, -3.6f, 0.0f),
                            XMFLOAT3(0.0f,  0.0f, 1.0f),
                            9.0f,
                            true,
                            true
                            )
                        );
                    target->AnimatePosition()->Start(6.0f);
                    break;
                }
                targetCount++;
            }
            else
            {
                target->Active(false);
            }
        }
        else
        {
            (*object)->Active(false);
        }
    }
}

//----------------------------------------------------------------------
            
            
```

<span data-ttu-id="3227b-304">Level4.h</span><span class="sxs-lookup"><span data-stu-id="3227b-304">Level4.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level4:
// This class defines the fourth level of the game.  It derives from the
// third level.  The targets must be hit in numeric order.

#include "Level3.h"

ref class Level4: public Level3
{
internal:
    Level4();
    virtual void Initialize(std::vector<GameObject^> objects) override;

    virtual bool Update(
        float time,
        float elapsedTime,
        float timeRemaining,
        std::vector<GameObject^> objects
        ) override;

    virtual void SaveState(PersistentState^ state) override;
    virtual void LoadState(PersistentState^ state) override;

private:
    int m_nextId;
};
            
            
```

<span data-ttu-id="3227b-305">Level4.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-305">Level4.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level4.h"
#include "Face.h"

//----------------------------------------------------------------------

Level4::Level4()
{
    m_timeLimit = 30.0f;
    m_objective = "Hit each of the moving targets in ORDER before time runs out.";
}

//----------------------------------------------------------------------

void Level4::Initialize(std::vector<GameObject^> objects)
{
    Level3::Initialize(objects);

    int targetCount = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if (Face^ target = dynamic_cast<Face^>(*object))
        {
            if (targetCount < 9)
            {
                target->Target(targetCount == 0 ? true : false);
                targetCount++;
            }
        }
    }
    m_nextId = 1;
}

//----------------------------------------------------------------------

bool Level4::Update(
    float /* time */,
    float /* elapsedTime */,
    float /* timeRemaining */,
    std::vector<GameObject^> objects
    )
{
    int left = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if ((*object)->Active() && ((*object)->TargetId() > 0))
        {
            if ((*object)->Hit() && ((*object)->TargetId() == m_nextId))
            {
                (*object)->Active(false);
                m_nextId++;
            }
            else
            {
                left++;
            }
        }
        if ((*object)->Active() && ((*object)->TargetId() == m_nextId))
        {
            (*object)->Target(true);
        }
    }
    return (left == 0);
}

//----------------------------------------------------------------------

void Level4::SaveState(PersistentState^ state)
{
    state->SaveInt32(":NextTarget", m_nextId);
}

//----------------------------------------------------------------------

void Level4::LoadState(PersistentState^ state)
{
    m_nextId = state->LoadInt32(":NextTarget", 1);
}

//----------------------------------------------------------------------
            
            
```

<span data-ttu-id="3227b-306">Level5.h</span><span class="sxs-lookup"><span data-stu-id="3227b-306">Level5.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level5:
// This class defines the fifth level of the game.  It derives from the
// third level.  This level introduces obstacles that move into place
// during game play.  The targets may be hit in any order.

#include "Level3.h"

ref class Level5: public Level3
{
internal:
    Level5();
    virtual void Initialize(std::vector<GameObject^> objects) override;
};
            
            
```

<span data-ttu-id="3227b-307">Level5.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-307">Level5.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level5.h"
#include "Cylinder.h"
#include "Animate.h"

using namespace DirectX;

//----------------------------------------------------------------------

Level5::Level5()
{
    m_timeLimit = 30.0f;
    m_objective = "Hit each of the moving targets while avoiding the obstacles before time runs out.";
}

//----------------------------------------------------------------------

void Level5::Initialize(std::vector<GameObject^> objects)
{
    Level3::Initialize(objects);

    XMFLOAT3 obstacleStartPosition[] =
    {
        XMFLOAT3(-4.5f, -3.0f, 0.0f),
        XMFLOAT3(4.5f, -3.0f, 0.0f),
        XMFLOAT3(0.0f, 3.01f, -2.0f),
        XMFLOAT3(-1.5f, -3.0f, -6.5f),
        XMFLOAT3(1.5f, -3.0f, -6.5f)
    };
    XMFLOAT3 obstacleEndPosition[] =
    {
        XMFLOAT3(-2.0f, -3.0f, 0.0f),
        XMFLOAT3(2.0f, -3.0f, 0.0f),
        XMFLOAT3(0.0f, -3.0f, -2.0f),
        XMFLOAT3(-1.5f, -3.0f, -4.0f),
        XMFLOAT3(1.5f, -3.0f, -4.0f)
    };
    float obstacleStartTime[] =
    {
        2.0f,
        5.0f,
        8.0f,
        11.0f,
        14.0f
    };

    int obstacleCount = 0;
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if (Cylinder^ obstacle = dynamic_cast<Cylinder^>(*object))
        {
            if (obstacleCount < 5)
            {
                obstacle->Active(true);
                obstacle->Position(obstacleStartPosition[obstacleCount]);
                obstacle->AnimatePosition(
                    ref new AnimateLinePosition(
                        obstacleStartPosition[obstacleCount],
                        obstacleEndPosition[obstacleCount],
                        10.0,
                        false
                        )
                    );
                obstacle->AnimatePosition()->Start(obstacleStartTime[obstacleCount]);
                obstacleCount ++;
            }
        }
    }
}

//----------------------------------------------------------------------            
            
```

<span data-ttu-id="3227b-308">Level6.h</span><span class="sxs-lookup"><span data-stu-id="3227b-308">Level6.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Level6:
// This class defines the sixth and final level of the game.  It derives from the
// fifth level.  In this level, the targets do not disappear when they are hit.
// The target will stay highlighted for two seconds.  As this is the last level,
// the only criteria for completion is time expiring.

#include "Level5.h"

ref class Level6: public Level5
{
internal:
    Level6();
    virtual bool Update(
        float time,
        float elapsedTime,
        float timeRemaining,
        std::vector<GameObject^> objects
        ) override;
};
            
            
```

<span data-ttu-id="3227b-309">Level6.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-309">Level6.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Level6.h"

//----------------------------------------------------------------------

Level6::Level6()
{
    m_timeLimit = 20.0f;
    m_objective = "Hit as many moving targets as possible while avoiding the obstacles before time runs out.";
}

//----------------------------------------------------------------------

bool Level6::Update(
    float time,
    float elapsedTime,
    float timeRemaining,
    std::vector<GameObject^> objects
    )
{
    for (auto object = objects.begin(); object != objects.end(); object++)
    {
        if ((*object)->Active() && (*object)->Target())
        {
            if ((*object)->Hit() && ((*object)->HitTime() < (time - 2.0f)))
            {
                (*object)->Hit(false);
            }
        }
    }
    return ((timeRemaining - elapsedTime) <= 0.0f);
}

//----------------------------------------------------------------------            
            
```

<span data-ttu-id="3227b-310">Animate.h</span><span class="sxs-lookup"><span data-stu-id="3227b-310">Animate.h</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#pragma once

// Animate:
// This is an abstract class for animations.  It defines a set of
// capabilities for animating XMFLOAT3 variables.  An animation has the following
// characteristics:
//     Start - the time for the animation to start.
//     Duration - the length of time the animation is to run.
//     Continuous - whether the animation loops after duration is reached or just
//         stops.
// There are two query functions:
//     IsActive - determines if the animation is active at time t.
//     IsFinished - determines if the animation is done at time t.
// It is expected that each derived class will provide an Evaluate method for the
// specific kind of animation.

ref class Animate abstract
{
internal:
    Animate();

    virtual DirectX::XMFLOAT3 Evaluate (_In_ float t) = 0;

    bool  IsActive(_In_ float t) { return ((t >= m_startTime) && (m_continuous || (t < (m_startTime + m_duration)))); };
    bool  IsFinished(_In_ float t) { return (!m_continuous && (t >= (m_startTime + m_duration))); }
    float Start();
    void  Start(_In_ float start);
    float Duration();
    void  Duration(_In_ float duration);
    bool  Continuous();
    void  Continuous(_In_ bool continuous);

protected private:
    bool  m_continuous;      // if true means at end cycle back to beginning
    float m_startTime;       // time at which animation begins
    float m_duration;        // for continuous, this is the duration of 1 cycle through path
};

//----------------------------------------------------------------------

// AnimateLinePosition:
// This class is a specialization of Animate that defines an animation of a position vector
// along a straight line defined in world coordinates from startPosition to endPosition.

ref class AnimateLinePosition: public Animate
{
internal:
    AnimateLinePosition(
        _In_ DirectX::XMFLOAT3 startPosition,
        _In_ DirectX::XMFLOAT3 endPosition,
        _In_ float duration,
        _In_ bool continuous
        );
    virtual DirectX::XMFLOAT3 Evaluate(_In_ float t) override;

private:
    DirectX::XMFLOAT3 m_startPosition;
    DirectX::XMFLOAT3 m_endPosition;
    float             m_length;
};

//----------------------------------------------------------------------

struct LineSegment
{
    DirectX::XMFLOAT3 position;
    float             length;
    float             uStart;
    float             uLength;
};

// AnimateLineListPosition:
// This class is a specialization of Animate that defines an animation of a position vector
// along a set of line segments defined by a set of points.  The animation along the path is
// such that the evaluation of the position along the path will be uniform independent of
// the length of each of the line segments.  A continuous loop can be achieved by having the
// first and last points of the list be the same.

ref class AnimateLineListPosition: public Animate
{
internal:
    AnimateLineListPosition(
        _In_ unsigned int count,
        _In_reads_(count) DirectX::XMFLOAT3 position[],
        _In_ float duration,
        _In_ bool continuous
        );
    virtual DirectX::XMFLOAT3 Evaluate(_In_ float t) override;

private:
    unsigned int             m_count;
    float                    m_totalLength;
    std::vector<LineSegment> m_segment;
};

//----------------------------------------------------------------------

// AnimateCirclePosition:
// This class is a specialization of Animate that defines an animation of a position vector
// along a circular path centered at 'center' with a starting point of 'startPosition'.  The
// distance between 'center' and 'startPosition' defines the radius of the circle.  The plane
// of the circle will pass through 'center' and 'startPosition' and have a normal of 'planeNormal'.
// The direction of the animation can be either clockwise or counterclockwise based
// on the 'clockwise' parameter.

ref class AnimateCirclePosition: public Animate
{
internal:
    AnimateCirclePosition(
        _In_ DirectX::XMFLOAT3 center,
        _In_ DirectX::XMFLOAT3 startPosition,
        _In_ DirectX::XMFLOAT3 planeNormal,
        _In_ float duration,
        _In_ bool continuous,
        _In_ bool clockwise
        );
    virtual DirectX::XMFLOAT3 Evaluate(_In_ float t) override;

private:
    DirectX::XMFLOAT4X4 m_rotationMatrix;
    DirectX::XMFLOAT3   m_center;
    DirectX::XMFLOAT3   m_planeNormal;
    DirectX::XMFLOAT3   m_startPosition;
    float               m_radius;
    bool                m_clockwise;
};

//----------------------------------------------------------------------
            
            
```

<span data-ttu-id="3227b-311">Animate.cpp</span><span class="sxs-lookup"><span data-stu-id="3227b-311">Animate.cpp</span></span>

```cpp
//// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
//// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
//// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
//// PARTICULAR PURPOSE.
////
//// Copyright (c) Microsoft Corporation. All rights reserved

#include "pch.h"
#include "Animate.h"

using namespace DirectX;

//----------------------------------------------------------------------

Animate::Animate():
    m_continuous(false),
    m_startTime(0.0f),
    m_duration(10.0f)
{
}

//----------------------------------------------------------------------

float Animate::Start()
{
    return m_startTime;
}

//----------------------------------------------------------------------

void Animate::Start(_In_ float start)
{
    m_startTime = start;
}

//----------------------------------------------------------------------

float Animate::Duration()
{
    return m_duration;
}

//----------------------------------------------------------------------

void Animate::Duration(_In_ float duration)
{
    m_duration = duration;
}

//----------------------------------------------------------------------

bool Animate::Continuous()
{
    return m_continuous;
}

//----------------------------------------------------------------------

void Animate::Continuous(_In_ bool continuous)
{
    m_continuous = continuous;
}

//----------------------------------------------------------------------

AnimateLinePosition::AnimateLinePosition(
    _In_ XMFLOAT3 startPosition,
    _In_ XMFLOAT3 endPosition,
    _In_ float duration,
    _In_ bool continuous)
{
    m_startPosition = startPosition;
    m_endPosition = endPosition;
    m_duration = duration;
    m_continuous = continuous;

    m_length = XMVectorGetX(
        XMVector3Length(XMLoadFloat3(&endPosition) - XMLoadFloat3(&startPosition))
        );
}

//----------------------------------------------------------------------

XMFLOAT3 AnimateLinePosition::Evaluate(_In_ float t)
{
    if (t <= m_startTime)
    {
        return m_startPosition;
    }

    if ((t >= (m_startTime + m_duration)) && !m_continuous)
    {
        return m_endPosition;
    }

    float startTime = m_startTime;
    if (m_continuous)
    {
        // For continuous operation, move the start time forward to
        // eliminate previous iterations.
        startTime += ((int)((t - m_startTime) / m_duration)) * m_duration;
    }

    float u = (t - startTime) / m_duration;
    XMFLOAT3 currentPosition;
    currentPosition.x = m_startPosition.x + (m_endPosition.x - m_startPosition.x)*u;
    currentPosition.y = m_startPosition.y + (m_endPosition.y - m_startPosition.y)*u;
    currentPosition.z = m_startPosition.z + (m_endPosition.z - m_startPosition.z)*u;

    return currentPosition;
}

//----------------------------------------------------------------------

AnimateLineListPosition::AnimateLineListPosition(
    _In_ unsigned int count,
    _In_reads_(count) XMFLOAT3 position[],
    _In_ float duration,
    _In_ bool continuous)
{
    m_duration = duration;
    m_continuous = continuous;
    m_count = count;

    std::vector<LineSegment> segment(m_count);
    m_segment = segment;
    m_totalLength = 0.0f;

    m_segment[0].position = position[0];
    for (unsigned int i = 1; i < count; i++)
    {
        m_segment[i].position = position[i];
        m_segment[i - 1].length = XMVectorGetX(
            XMVector3Length(
                XMLoadFloat3(&m_segment[i].position) -
                XMLoadFloat3(&m_segment[i - 1].position)
                )
            );
        m_totalLength += m_segment[i - 1].length;
    }

    // Parameterize the segments to ensure uniform evaluation along the path.
    float u = 0.0f;
    for (unsigned int i = 0; i < (count - 1); i++)
    {
        m_segment[i].uStart = u;
        m_segment[i].uLength = (m_segment[i].length / m_totalLength);
        u += m_segment[i].uLength;
    }
    m_segment[count-1].uStart = 1.0f;
}

//----------------------------------------------------------------------

XMFLOAT3 AnimateLineListPosition::Evaluate(_In_ float t)
{
    if (t <= m_startTime)
    {
        return m_segment[0].position;
    }

    if ((t >= (m_startTime + m_duration)) && !m_continuous)
    {
        return m_segment[m_count-1].position;
    }

    float startTime = m_startTime;
    if (m_continuous)
    {
        // For continuous operation, move the start time forward to
        // eliminate previous iterations.
        startTime += ((int)((t - m_startTime) / m_duration)) * m_duration;
    }

    float u = (t - startTime) / m_duration;
    // Find the right segment.
    unsigned int i = 0;
    while (u > m_segment[i + 1].uStart)
    {
        i++;
    }

    u -= m_segment[i].uStart;
    u /= m_segment[i].uLength;

    XMFLOAT3 currentPosition;
    currentPosition.x = m_segment[i].position.x + (m_segment[i + 1].position.x - m_segment[i].position.x)*u;
    currentPosition.y = m_segment[i].position.y + (m_segment[i + 1].position.y - m_segment[i].position.y)*u;
    currentPosition.z = m_segment[i].position.z + (m_segment[i + 1].position.z - m_segment[i].position.z)*u;

    return currentPosition;
}

//----------------------------------------------------------------------

AnimateCirclePosition:: AnimateCirclePosition(
    _In_ XMFLOAT3 center,
    _In_ XMFLOAT3 startPosition,
    _In_ XMFLOAT3 planeNormal,
    _In_ float duration,
    _In_ bool continuous,
    _In_ bool clockwise)
{
    m_center = center;
    m_planeNormal = planeNormal;
    m_startPosition = startPosition;
    m_duration = duration;
    m_continuous = continuous;
    m_clockwise = clockwise;

    XMVECTOR coordX = XMLoadFloat3(&m_startPosition) - XMLoadFloat3(&m_center);
    m_radius = XMVectorGetX(XMVector3Length(coordX));

    XMVector3Normalize(coordX);

    XMVECTOR coordZ = XMLoadFloat3(&m_planeNormal);
    XMVector3Normalize(coordZ);

    XMVECTOR coordY;
    if (m_clockwise)
    {
        coordY = XMVector3Cross(coordZ, coordX);
    }
    else
    {
        coordY = XMVector3Cross(coordX, coordZ);
    }

    XMVECTOR vectorX = XMVectorSet(1.0f, 0.0f, 0.0f, 1.0f);
    XMVECTOR vectorY = XMVectorSet(0.0f, 1.0f, 0.0f, 1.0f);
    XMMATRIX mat1 = XMMatrixIdentity();
    XMMATRIX mat2 = XMMatrixIdentity();

    if (!XMVector3Equal(coordX, vectorX))
    {
        float angle;
        angle = XMVectorGetX(
            XMVector3AngleBetweenVectors(vectorX, coordX)
            );
        if ((angle * angle) > 0.025)
        {
            XMVECTOR axis1 = XMVector3Cross(vectorX, coordX);

            mat1 = XMMatrixRotationAxis(axis1, angle);
            vectorY = XMVector3TransformCoord(vectorY, mat1);
        }
    }
    if (!XMVector3Equal(vectorY, coordY))
    {
        float angle;
        angle = XMVectorGetX(
            XMVector3AngleBetweenVectors(vectorY, coordY)
            );
        if ((angle * angle) > 0.025)
        {
            XMVECTOR axis2 = XMVector3Cross(vectorY, coordY);
            mat2 = XMMatrixRotationAxis(axis2, angle);
        }
    }
    XMStoreFloat4x4(
        &m_rotationMatrix,
        mat1 *
        mat2 *
        XMMatrixTranslation(m_center.x, m_center.y, m_center.z)
        );
}

//----------------------------------------------------------------------

XMFLOAT3 AnimateCirclePosition::Evaluate(_In_ float t)
{
    if (t <= m_startTime)
    {
        return m_startPosition;
    }

    if ((t >= (m_startTime + m_duration)) && !m_continuous)
    {
        return m_startPosition;
    }

    float startTime = m_startTime;
    if (m_continuous)
    {
        // For continuous operation move the start time forward to
        // eliminate previous iterations.
        startTime += ((int)((t - m_startTime) / m_duration)) * m_duration;
    }

    float u = (t - startTime) / m_duration * XM_2PI;

    XMFLOAT3 currentPosition;
    currentPosition.x = m_radius * cos(u);
    currentPosition.y = m_radius * sin(u);
    currentPosition.z = 0.0f;

    XMStoreFloat3(
        &currentPosition,
        XMVector3TransformCoord(
            XMLoadFloat3(&currentPosition),
            XMLoadFloat4x4(&m_rotationMatrix)
            )
        );

    return currentPosition;
}

//----------------------------------------------------------------------
            
            
```

> **<span data-ttu-id="3227b-312">Hinweis</span><span class="sxs-lookup"><span data-stu-id="3227b-312">Note</span></span>**  
<span data-ttu-id="3227b-313">Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben.</span><span class="sxs-lookup"><span data-stu-id="3227b-313">This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="3227b-314">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, finden Sie Informationen dazu in der [archivierten Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span><span class="sxs-lookup"><span data-stu-id="3227b-314">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

 

## <a name="related-topics"></a><span data-ttu-id="3227b-315">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3227b-315">Related topics</span></span>


[<span data-ttu-id="3227b-316">Erstellen eines einfachen UWP-Spiels mit DirectX</span><span class="sxs-lookup"><span data-stu-id="3227b-316">Create a simple UWP game with DirectX</span></span>](tutorial--create-your-first-metro-style-directx-game.md)

 

 




