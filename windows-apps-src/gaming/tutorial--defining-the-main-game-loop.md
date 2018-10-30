---
author: joannaleecy
title: Definieren des Hauptobjekts für das Spiel
description: In diesem Abschnitt widmen wir uns den Details des Hauptobjekts des Beispielspiels. Außerdem erfahren Sie, wie die implementierten Regeln in Interaktionen mit der Spielwelt übersetzt werden.
ms.assetid: 6afeef84-39d0-cb78-aa2e-2e42aef936c9
ms.author: joanlee
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Hauptobjekt
ms.localizationpriority: medium
ms.openlocfilehash: b94d7139f35b3a18edd66af9959a0958d0bdcbc1
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5762216"
---
# <a name="define-the-main-game-object"></a>Definieren des Hauptobjekts für das Spiel

Nachdem Sie das grundlegende Framework des beispielspiels angeordnet und implementiert einen Zustandsautomaten, der den allgemeinen Benutzer- und Systemverhalten behandelt haben, sollten Sie untersuchen der Regeln und spielmechaniken, die das Spielbeispiel in einem Spiel zu verwandeln. Sehen wir uns die Details des Hauptobjekts für das Spielbeispiel, und wie Sie Spiele Regeln in Interaktionen mit der spielwelt übersetzt.

>[!Note]
>Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX). Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen. Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).

## <a name="objective"></a>Ziel

Hier erfahren Sie, wie Sie grundlegender Entwicklungstechniken zum Implementieren der Spielregeln und Mechanismen für ein UWP-DirectX-Spiel.

## <a name="main-game-object"></a>Hauptobjekt für das Spiel

In diesem Beispielspiel ist __Simple3DGame__ die hauptspielobjekts-Klasse. Eine Instanz des __Simple3DGame__ -Objekts wird in der __App:: Load__ -Methode konstruiert.

Das Klassenobjekt __Simple3DGame__ :
* Gibt an, das Gameplay-Logik implementiert
* Enthält Methoden, die kommunizieren:
    * Ändert sich der Spielzustand an den im app-Framework definierten Zustandsautomaten.
    * Ändert sich der Spielzustand von der app an das spielobjekt selbst.
    * Details zum Aktualisieren des Spiels UI (Overlay und Head-Up-Display), Animationen und Physik (Dynamik).

    >[!Note]
    >Aktualisierung von Grafiken erfolgt über die __GameRenderer__ -Klasse, die Methoden zum Abrufen und Verwenden von Grafikressourcen Gerät vom Spiel verwendeten enthält. Weitere Informationen finden Sie unter [Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md).

* Dient als Container für die Daten, die eine Ebene, spielsitzung, oder eine Lebensdauer ausmachen – je nachdem, wie Sie Ihr Spiel auf hoher Ebene definieren. In diesem Fall die spielzustandsdaten ist für die Lebensdauer des Spiels und einmal, wenn der Benutzer das Spiel startet, initialisiert werden.

Um die Methoden und in dieses Klassenobjekt definierte Daten anzuzeigen, wechseln Sie zu [Simple3DGame-Objekts](#simple3dgame-object).

## <a name="initialize-and-start-the-game"></a>Initialisieren und Starten des Spiels

Wenn ein Spieler das Spiel startet, muss das Spielobjekt den eigenen Zustand initialisieren, das Overlay erstellen und hinzufügen, die Variablen zur Nachverfolgung der Erfolge des Spielers festlegen und die Objekte instanziieren, die zum Erstellen der Level benötigt werden. In diesem Beispiel geschieht dies, wenn die neue __GameMain__ -Instanz in [__App:: Load__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/App.cpp#L115-L123)erstellt wird. 

Das spielobjekt __Simple3DGame__, wird im __GameMain__ -Konstruktor erstellt. Es wird mithilfe der [__Simple3DGame::Initialize__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L54-L250) Methode während der [asynchronen erstellen Aufgabe im __GameMain__ -Konstruktor](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L65-L74)initialisiert.

### <a name="simple3dgameinitialize-method"></a>Simple3DGame::Initialize-Methode

Das Beispielspiel richtet die folgenden Komponenten in das spielobjekt:

* Ein neues Audiowiedergabeobjekt wird erstellt.
* Arrays für die Grafikgrundtypen des Spiels werden erstellt (einschließlich Arrays für die Levelgrundtypen, Munition und Hindernisse).
* Ein Speicherort für die Spielzustandsdaten mit der Bezeichnung *Game* wird erstellt und am durch [**ApplicationData::Current**](https://msdn.microsoft.com/library/windows/apps/br241619) festgelegten Speicherort der App-Dateneinstellungen platziert.
* Ein Spieltimer und die anfängliche spielinterne Overlaybitmap werden erstellt.
* Eine neue Kamera mit einem spezifischen Satz von Ansichts- und Projektionsparametern wird erstellt.
* Das Eingabegerät (Controller) wird auf die gleiche Ausgangsausrichtung festgelegt wie die Kamera, sodass die Ausgangsposition der Steuerung exakt der Kameraposition entspricht.
* Das Spielerobjekt wird erstellt und aktiviert. Wir verwenden ein kugelobjekt, die Nähe des Spielers zu Wänden und Hindernissen zu ermitteln und um zu verhindern, dass die Kamera in der Lage, die immersionseffekt nicht beeinträchtigt wird möglicherweise platziert abrufen.
* Der Spielweltgrundtyp wird erstellt.
* Die Zylinderhindernisse werden erstellt.
* Die Ziele (**Face**-Objekte) werden erstellt und nummeriert.
* Die Munitionskugeln werden erstellt.
* Die Level werden erstellt.
* Der Highscore wird geladen.
* Alle ggf. zuvor gespeicherten Spielzustände werden geladen.

Das Spiel besitzt nun Instanzen aller wichtigen Komponenten: Spielwelt, Spieler, Hindernisse, Ziele und Munitionskugeln. Außerdem besitzt es Instanzen der Level. Diese stehen für Konfigurationen aller oben genannten Komponenten und ihrer Verhalten für die einzelnen spezifischen Level. Im nächsten Abschnitt widmen wir uns der Levelerstellung des Spiels.

## <a name="build-and-load-game-levels"></a>Erstellen und Laden von spiellevels

Die meisten die schwere Aufgabe für den Level Bau erfolgt in den __Level.h/.cpp__ -Dateien im Ordner " __GameLevels__ " der Beispiel-Lösung gefunden. Da es auf eine sehr spezifische Implementierung konzentriert, wird nicht wir ihnen hier behandelt. Entscheidend ist in diesem Zusammenhang, dass der Code für die einzelnen Levels jeweils als separates __LevelN__-Objekt ausgeführt wird. Wenn Sie das Spiel erweitern möchten, können Sie ein Objekt **Ebene** erstellen, die eine zugewiesene Nummer als Parameter annimmt und nach dem Zufallsprinzip platziert die Hindernisse und Ziele. Oder Sie können es levelkonfigurationsdaten aus einer Ressourcendatei oder sogar aus dem Internet geladen haben.

## <a name="define-the-game-play"></a>Definieren Sie das Spiel

Wir verfügen nun über alle Komponenten, die wir benötigen, um das Spiel zusammenzufügen. Die Level wurden auf Grundlage der Grundtypen im Speicher konstruiert und sind bereit für die Interaktion des Spielers.

Codedateien gute Spiele reagieren sofort spielereingaben und liefern umgehend Feedback. Dies gilt für jede Art von Spiel von Twitch-Aktion, in Echtzeit First-Person-Shooter- rundenbasiertes Strategiespiel.

### <a name="simple3dgamerungame-method"></a>Simple3DGame::RunGame-Methode

Wenn Sie eine Ebene wiedergeben, ist das Spiel im Zustand " __Dynamics__ ". 

[__GameMain::Update__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L261-L329) ist die wichtigsten Update-Schleife, die den Status der Anwendung einmal pro Frame aktualisiert, wie unten dargestellt. In der Update-Schleife ruft es die [__Simple3DGame::RunGame__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L337-L418) -Methode, um die Arbeit behandelt werden, wenn das Spiel im Zustand " __Dynamics__ " befindet.

```cpp
// Updates the application state once per frame.
void GameMain::Update()
{
    m_controller->Update(); //the controller instance has its own update loop.

    switch (m_updateState)
    {
        //...

    case UpdateEngineState::Dynamics:
        if (m_controller->IsPauseRequested())
        {
            //...
        }
        else
        {
            GameState runState = m_game->RunGame(); //when playing a level, the game is in the Dynamics state. Work is handled by Simple3DGame::RunGame method.
            switch (runState)
            {
                
      //...
```
          
[__Simple3DGame::RunGame__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L337-L418) verarbeitet den Satz von Daten, die den aktuellen Zustand des das Spiel für die aktuelle Iteration der spielschleife definiert.

Spielablauf Logik im __RunGame__:
*  Die Methode aktualisiert den Zeitgeber, der die Sekunden bis zum Levelabschluss herunterzählt, und überprüft, ob die Zeit für den Level abgelaufen ist. Dies ist eine der Regeln des Spiels: beim Zeit abläuft, und alle Ziele haben nicht aufgenommen wurde, ist es Spiels entspannt zurücklehnen.
*  Ist die Zeit abgelaufen, legt die Methode den Spielzustand **TimeExpired** fest und kehrt zur **Update**-Methode im vorherigen Code zurück.
*  Ist die Zeit noch nicht abgelaufen, wird für den Bewegungs- und Blickrichtungscontroller eine aktualisierte Kameraposition abgefragt. Genauer gesagt: eine Aktualisierung des Blickwinkels – ausgehend von der Kameraebene (Blickrichtung des Spielers) – und des Abstands, um den sich der Blickwinkel seit der letzten Controllerabfrage bewegt hat.
*  Die Kamera wird auf der Grundlage der neuen Daten des Bewegungs- und Blickrichtungscontrollers aktualisiert.
*  Die Dynamik (also die Animationen und das Verhalten von Objekten in der Spielwelt, die nicht vom Spieler gesteuert werden) wird aktualisiert. In diesem Beispielspiel wird die [__UpdateDynamics()__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L436-L856) -Methode aufgerufen, um die Bewegung die Munition, die ausgelöst wurde, die Animation der säulenhindernisse und die Bewegung der Ziele zu aktualisieren. Weitere Informationen finden Sie unter [Aktualisieren die spielwelt](#update-the-game-world).
*  Die Methode überprüft, ob die Kriterien für den erfolgreichen Abschluss eines Levels erfüllt sind. Ist dies der Fall, wird der endgültige Punktestand für das Level festgelegt und überprüft, ob es sich um das letzte Level (von sechs) handelt. Ist dies der Fall, gibt die Methode den Spielzustand **GameComplete** zurück. Andernfalls gibt sie den Spielzustand __LevelComplete__ zurück.
*  Wurde das Level nicht abgeschlossen, legt die Methode den Spielzustand auf __Active__ fest und springt zurück.

## <a name="update-the-game-world"></a>Aktualisieren der spielwelt

In diesem Beispiel wenn das Spiel ausgeführt wird, wird die [__Simple3DGame::UpdateDynamics()__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L436-L856) -Methode aufgerufen von der [__Simple3DGame::RunGame__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Simple3DGame.cpp#L337-L418) -Methode (die [__GameMain::Update__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L261-L329)aufgerufen wird) zum Aktualisieren von Objekten, die in einem Spiel Szene gerendert werden.

In der Schleife __UpdateDynamics__ Aufrufen von Methoden, mit denen die spielwelt in Bewegung, unabhängig von der Spieler setzen Eingabe Erstellen einer immersiven Spielerlebnis und stellen die Ebene *Fotosequenz*. Dazu gehören Grafiken, die gerendert werden müssen, und durch die Animation ausgeführt, zu einer lebenden, Welt befinden, auch wenn es keine Eingaben des Spielers ist anzuzeigen. Beispielsweise Bäume weichen sich im Wind, Wellen cresting Küste, Maschinen Rauchen und Außerirdische Monster Strecken und bewegen. Hierzu gehört auch die Interaktion zwischen Objekten (beispielsweise Kollisionen zwischen der Spielerkugel und der Welt oder zwischen der Munition und den Hindernissen oder Zielen).

Die spielschleife sollten immer eine regelmäßige Aktualisierung der spielwelt, ob Spiellogik, physischen Algorithmen abhängig ist oder ob es einfach ist zufällige, außer wenn das Spiel nicht explizit angehalten wurde. 

Im Beispielspiel wird dieses Prinzip als *Dynamik* bezeichnet. Es umfasst das Verhalten der Säulenhindernisse sowie die Bewegung und das physikalische Verhalten abgefeuerter Munitionskugeln. 

### <a name="simple3dgameupdatedynamics-method"></a>Simple3DGame::UpdateDynamics-Methode 

Diese Methode behandelt vierBerechnungssätze:

* Die Positionen der Kugeln für die abgefeuerte Munition in der Spielwelt.
* Die Animation der Säulenhindernisse.
* Die Überschneidung des Spielers mit den Begrenzungen der Spielwelt.
* Die Kollisionen von Munitionskugeln mit den Hindernissen, den Zielen, anderen Munitionskugeln und der Spielwelt.

Bei der Animation der Hindernisse handelt es sich um eine in **Animate.h/.cpp** definierte Schleife. Das Verhalten der Munition und sämtlicher Kollisionen sind durch vereinfachte Physik Algorithmen definiert, im Code angegeben und durch eine Reihe von globalen Konstanten für die spielwelt, einschließlich der Schwerkraft und Materialeigenschaften parametrisiert. All dies wird im Koordinatenbereich der Spielwelt berechnet.

### <a name="review-the-flow"></a>Überprüfen Sie den Fluss

Nun, da wir alle Objekte in der Szene aktualisiert und sämtlicher Kollisionen berechnet haben, müssen wir diese Informationen verwenden, um die entsprechenden sichtbaren Veränderungen zu zeichnen. 

Nach Abschluss die aktuelle Iteration der spielschleife der __GameMain::Update()__ Ruft das Beispiel sofort __Render()__ um mithilfe der aktualisierten Objektdaten und generieren eine neue Szene zu der Spieler zu präsentieren, wie hier gezeigt. Als Nächstes werfen wir einen Blick auf das Rendering.

```cpp
void GameMain::Run()
{
    while (!m_windowClosed)
    {
        if (m_visible)
        {
            switch (m_updateState)
            {
            case UpdateEngineState::Deactivated:
            case UpdateEngineState::TooSmall:
                // ...
                // otherwise fall through and do normal processing to get the rendering handled.
            default:
                CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessAllIfPresent);
                Update(); // GameMain::Update calls Simple3DGame::RunGame() if game is in Dynamics state, uses Simple3DGame::UpdateDynamics() to update game world.
                m_renderer->Render(); //Render() is called immediately after the Update() loop
                m_deviceResources->Present();
                m_renderNeeded = false;
            }
        }
        else
        {
            CoreWindow::GetForCurrentThread()->Dispatcher->ProcessEvents(CoreProcessEventsOption::ProcessOneAndAllPending);
        }
    }
    m_game->OnSuspending();  // exiting due to window close.  Make sure to save state.
}
```

## <a name="render-the-game-worlds-graphics"></a>Rendern der spielweltgrafik

Wir empfehlen, die Grafik in einem Spiel so oft wie möglich (im Höchstfall also bei jeder Iteration der Hauptschleife des Spiels) zu aktualisieren. Im Zuge der Schleifeniteration wird das Spiel unabhängig von einer Spielereingabe aktualisiert. Dies ermöglicht eine flüssige Darstellung der berechneten Animationen und Verhalten. Stellen Sie sich nur einmal eine einfache Szene mit Wasser vor, das sich nur bewegt, wenn der Spieler eine Taste drückt. Das Ergebnis wäre eine schrecklich langweilige Grafik. Ein gutes Spiel wird ruckelfrei und flüssig dargestellt.

Erinnern Sie Schleife des beispielspiels auf, wie oben in [__gamemain:: Run__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameMain.cpp#L143-L202)dargestellt. Ist das Hauptfenster des Spiels sichtbar und nicht angedockt oder deaktiviert, werden weiterhin Updates für das Spiel ausgeführt und die Ergebnisse gerendert. [__Rendern__](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameRenderer.cpp#L474-L624) Methode, die wir untersuchen sind rendert jetzt eine Darstellung dieses Zustands. Dies erfolgt sofort nach dem Aufrufen von zu **Aktualisieren**, einschließlich **RunGame** um Zustände zu aktualisieren, das im vorherigen Abschnitt beschrieben wurde.

Diese Methode zeichnet die Projektion der dreidimensionalen Welt und legt anschließend das Direct2D-Overlay darüber. Nach Abschluss des Vorgangs zeigt sie die finale Swapchain mit den kombinierten Puffern an.

>[!Note]
>Es gibt für das Direct2D Overlay zwei Zustände: eines, in dem das Spiel die Überlagerung von Spieledaten, das die Bitmap für das pausenmenü und, wo zeigt das Spiel das Fadenkreuz sowie die Rechtecke für den bewegungs-/ Touchscreen enthält anzeigt, Controller. Der Text mit dem Spielstand wird in beiden Zuständen gezeichnet. Weitere Informationen finden Sie unter [Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md).

### <a name="gamerendererrender-method"></a>GameRenderer::Render-Methode

```cpp
void GameRenderer::Render()
{
    bool stereoEnabled = m_deviceResources->GetStereoState();

    auto d3dContext = m_deviceResources->GetD3DDeviceContext();
    auto d2dContext = m_deviceResources->GetD2DDeviceContext();
   
        // ...
        if (m_game != nullptr && m_gameResourcesLoaded && m_levelResourcesLoaded)
        {
            // This section is only used after the game state has been initialized and all device
            // resources needed for the game have been created and associated with the game objects.
            //...
            auto objects = m_game->RenderObjects();
            for (auto object = objects.begin(); object != objects.end(); object++)
            {
                (*object)->Render(d3dContext, m_constantBufferChangesEveryPrim.Get()); // Renders the 3D objects
            }

        //...
        d3dContext->BeginEventInt(L"D2D BeginDraw", 1);
        d2dContext->BeginDraw(); //Start drawing the overlays
        
        // To handle the swapchain being pre-rotated, set the D2D transformation to include it.
        d2dContext->SetTransform(m_deviceResources->GetOrientationTransform2D());

        if (m_game != nullptr && m_gameResourcesLoaded)
        {
            // This is only used after the game state has been initialized.
            m_gameHud->Render(m_game); // Renders number of hits, shots, and time
        }

        if (m_gameInfoOverlay->Visible())
        {
            d2dContext->DrawBitmap(     // Renders the game overlay
                m_gameInfoOverlay->Bitmap(),
                m_gameInfoOverlayRect
                );
        }
        //...
    }
}
```

## <a name="simple3dgame-object"></a>Simple3DGame-Objekts

Dies sind die Methoden und Daten, die in der Klasse __Simple3DGame__ Objekt definiert sind.

### <a name="methods"></a>Methoden

Die internen Methoden auf **Simple3DGame** definiert:

-   **Initialisieren**: Legt die Anfangswerte der globalen Variablen fest und initialisiert die Spielobjekte. Dies wird im Abschnitt [zu initialisieren und Starten des Spiels](#initialize-and-start-the-game) behandelt.
-   **LoadGame**: Initialisiert ein neues Level und startet den entsprechenden Ladevorgang.
-   **LoadLevelAsync**: Startet eine asynchrone Aufgabe (Wenn Sie mit asynchronen Aufgaben nicht vertraut sind, finden Sie unter [Parallel Patterns Library](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)) zum Initialisieren des Levels und ruft dann eine asynchrone Aufgabe für den Renderer auf die gerätespezifischen Ebene Ressourcen geladen. Diese Methode wird in einem gesonderten Thread ausgeführt. Daher können in diesem Thread nur [**ID3D11Device**](https://msdn.microsoft.com/library/windows/desktop/ff476379)-Methoden (und keine [**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)-Methoden) aufgerufen werden. Alle Gerätekontextmethoden werden in der **FinalizeLoadLevel**-Methode aufgerufen.
-   **FinalizeLoadLevel**: führt alle Aktionen zum Laden des Levels, die im Hauptthread ausgeführt werden soll. Dies schließt alle Aufrufe von Direct3D11-Gerätekontextmethoden ([**ID3D11DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/ff476385)) ein.
-   **StartLevel**: das Gameplay für ein neues Level startet.
-   **PauseGame**: hält das Spiel an.
-   **RunGame**: führt eine Iteration der spielschleife. Wird jeweils einmal pro Iteration der Spielschleife von **App::Update** aufgerufen, sofern sich das Spiel im Zustand **Active** befindet.
-   **OnSuspending** und **OnResuming**: anhält und fortsetzt Audiowiedergabe des Spiels bzw..

Und die privaten Methoden:

-   **LoadSavedState** und **SaveState**: lädt bzw. speichert den aktuellen Zustand des Spiels.
-   **SaveHighScore** und **LoadHighScore**: speichert und lädt den spielübergreifenden Highscore Spiele, bzw..
-   **InitializeAmmo**: setzt den Zustand der als Munition wieder auf den ursprünglichen Zustand für die am Anfang jeder Runde Munition verwendeten.
-   **UpdateDynamics**: Dies ist eine wichtige Methode, da sie alle Spielobjekte Grundlage vordefinierter animationsroutinen, physikeffekte und steuerungseingaben aktualisiert. Hierbei handelt es sich gewissermaßen um das Herzstück der Interaktivität, die das Spiel ausmacht. Dies wird im Abschnitt [Aktualisieren die spielwelt](#update-the-game-world) behandelt.

Die anderen öffentlichen Methoden dienen zum Abrufen von Eigenschaften und geben Gameplay- und Overlay-spezifische Informationen an das App-Framework zurück, um diese anzuzeigen.

### <a name="data"></a>Daten

Am Anfang des Codebeispiels befinden sich vier Objekte, deren Instanzen während der Ausführung der Spielschleife aktualisiert werden.

-   **MoveLookController** Objekt: stellt die Eingaben des Spielers dar. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen](tutorial--adding-controls.md).
-   **GameRenderer** Objekt: stellt der Direct3D 11-Renderer abgeleitet aus der **DirectXBase** -Klasse, die alle gerätespezifischen Objekte und deren Rendering verarbeitet. Weitere Informationen finden Sie unter [Rendering-Framework I](tutorial--assembling-the-rendering-pipeline.md).
-   **Audio** -Objekt: steuert die Audiowiedergabe für das Spiel. Weitere Informationen finden Sie unter [Hinzufügen von sound](tutorial--adding-sound.md).

Die restlichen Spielvariablen enthalten die Listen mit den Grundtypen und die entsprechenden spielinternen Werte sowie Gameplay-spezifische Daten und Beschränkungen.

## <a name="next-steps"></a>Nächste Schritte

Jetzt sind Sie gespannt auf die tatsächliche Rendering-Engine: wie Aufrufe der __Render__ -Methoden für die aktualisierten Grundtypen in Pixel auf dem Bildschirm aktiviert abrufen. Dies wird in zwei Teile behandelt &mdash; [Rendering-Framework I: Einführung in das Rendering](tutorial--assembling-the-rendering-pipeline.md) und [Rendering-Framework II: Spiel-Rendering](tutorial-game-rendering.md). Sollten Sie sich dagegen mehr für die Aktualisierung des Spielzustands durch die Spielersteuerung interessieren, finden Sie entsprechende Informationen unter [Hinzufügen von Steuerelementen](tutorial--adding-controls.md).
