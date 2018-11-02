---
author: abbycar
title: Hinzufügen von Steuerelementen
description: In diesem Thema befassen wir uns damit, wie das Beispielspiel die Bewegungs-/Blicksteuerung in einem 3D-Spiel implementiert und wie einfache Steuerungen für Toucheingabe, Maus und Gamecontroller entwickelt werden.
ms.assetid: f9666abb-151a-74b4-ae0b-ef88f1f252f8
ms.author: abigailc
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Steuerelemente, Eingabe
ms.localizationpriority: medium
ms.openlocfilehash: 4aaacee011b3732b8d1456935239d7a4a5405a4d
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5944168"
---
# <a name="add-controls"></a><span data-ttu-id="aba84-104">Hinzufügen von Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="aba84-104">Add controls</span></span>


<span data-ttu-id="aba84-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="aba84-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="aba84-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].</span><span class="sxs-lookup"><span data-stu-id="aba84-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="aba84-107">Ein gutes universelles WindowsPlattform (UWP)-Spiel unterstützt viele unterschiedliche Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="aba84-107">A good Universal Windows Platform (UWP) game supports a wide variety of interfaces.</span></span> <span data-ttu-id="aba84-108">Ein potenzieller Spieler kann Windows 10 auf einem Tablet ohne physischen Tasten, einem PC mit Xbox-Controller, oder die neuesten desktop-Spiele-PC mit hochleistungsmaus ein High-End und Gaming-Tastatur.</span><span class="sxs-lookup"><span data-stu-id="aba84-108">A potential player might have Windows10 on a tablet with no physical buttons, a PC with an Xbox controller attached, or the latest desktop gaming rig with a high-performance mouse and gaming keyboard.</span></span> <span data-ttu-id="aba84-109">In unserem Spiel werden die Steuerelemente in der [**MoveLookController**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp)-Klasse implementiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-109">In our game the controls are implemented in the [**MoveLookController**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp) class.</span></span> <span data-ttu-id="aba84-110">Diese Klasse aggregiert alle drei Arten von Eingaben (Maus und Tastatur, Fingereingabe und Gamepad) in einem einzelnen Domänencontroller.</span><span class="sxs-lookup"><span data-stu-id="aba84-110">This class aggregates all three types of input (mouse and keyboard, touch, and gamepad) into a single controller.</span></span> <span data-ttu-id="aba84-111">Das Endergebnis ist ein First-Person-Shooter, der Standard-Bewegungs-/Blicksteuerungen des Genres verwendet, die mit mehreren Geräten funktionieren.</span><span class="sxs-lookup"><span data-stu-id="aba84-111">The end result is a first-person shooter that uses genre standard move-look controls that work with multiple devices.</span></span>

> [!NOTE]
> <span data-ttu-id="aba84-112">Weitere Informationen zu Steuerelementen finden Sie unter [Bewegungs-/Blicksteuerungen für Spiele](tutorial--adding-move-look-controls-to-your-directx-game.md) und [Toucheingabesteuerelemente für Spiele](tutorial--adding-touch-controls-to-your-directx-game.md).</span><span class="sxs-lookup"><span data-stu-id="aba84-112">For more info about controls, see [Move-look controls for games](tutorial--adding-move-look-controls-to-your-directx-game.md) and [Touch controls for games](tutorial--adding-touch-controls-to-your-directx-game.md).</span></span>


## <a name="objective"></a><span data-ttu-id="aba84-113">Ziel</span><span class="sxs-lookup"><span data-stu-id="aba84-113">Objective</span></span>

<span data-ttu-id="aba84-114">Wir haben jetzt ein Spiel, das gerendert wird, aber nicht den Spieler bewegt oder Ziele anvisiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-114">At this point we have a game that renders, but we can't move our player around or shoot the targets.</span></span> <span data-ttu-id="aba84-115">Wir werden sehen, wie unser Spiel First-Person-Shooter Bewegungs-/Blicksteuerungen für die folgenden Arten von Eingaben in unserem UWP-DirectX -Spiel implementiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-115">We'll take a look at how our game implements first person shooter move-look controls for the following types of input in our UWP DirectX game.</span></span>
- <span data-ttu-id="aba84-116">Tastatur und Maus</span><span class="sxs-lookup"><span data-stu-id="aba84-116">Mouse and keyboard</span></span>
- <span data-ttu-id="aba84-117">Touch</span><span class="sxs-lookup"><span data-stu-id="aba84-117">Touch</span></span>
- <span data-ttu-id="aba84-118">Gamepad</span><span class="sxs-lookup"><span data-stu-id="aba84-118">Gamepad</span></span>

>[!Note]
><span data-ttu-id="aba84-119">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="aba84-119">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="aba84-120">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="aba84-120">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="aba84-121">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="aba84-121">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="common-control-behaviors"></a><span data-ttu-id="aba84-122">Allgemeine Steuerungsverhalten</span><span class="sxs-lookup"><span data-stu-id="aba84-122">Common control behaviors</span></span>


<span data-ttu-id="aba84-123">Die Implementierung von Fingereingabesteuerungen und Maus-/Tastatursteuerungen ist im Grunde sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="aba84-123">Touch controls and mouse/keyboard controls have a very similar core implementation.</span></span> <span data-ttu-id="aba84-124">In einer UWP-App ist ein Zeiger einfach ein Punkt auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="aba84-124">In a UWP app, a pointer is simply a point on the screen.</span></span> <span data-ttu-id="aba84-125">Sie können ihn bewegen, indem Sie die Maus oder den Finger auf dem Touchscreen bewegen.</span><span class="sxs-lookup"><span data-stu-id="aba84-125">You can move it by sliding the mouse or sliding your finger on the touch screen.</span></span> <span data-ttu-id="aba84-126">Folglich können Sie einen einzelnen Satz von Ereignissen registrieren und müssen sich keine Gedanken darüber machen, ob der Spieler eine Maus oder einen Touchscreen zum Bewegen und Betätigen des Zeigers verwendet.</span><span class="sxs-lookup"><span data-stu-id="aba84-126">As a result, you can register for a single set of events, and not worry about whether the player is using a mouse or a touch screen to move and press the pointer.</span></span>

<span data-ttu-id="aba84-127">Beim Initialisieren der **MoveLookController**-Klasse im Beispielspiel werden vier zeigerspezifische Ereignisse und ein mausspezifisches Ereignis registriert:</span><span class="sxs-lookup"><span data-stu-id="aba84-127">When the **MoveLookController** class in the game sample is initialized, it registers for four pointer-specific events and one mouse-specific event:</span></span>

<span data-ttu-id="aba84-128">Ereignis</span><span class="sxs-lookup"><span data-stu-id="aba84-128">Event</span></span> | <span data-ttu-id="aba84-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aba84-129">Description</span></span>
:------ | :-------
[**<span data-ttu-id="aba84-130">CoreWindow::PointerPressed</span><span class="sxs-lookup"><span data-stu-id="aba84-130">CoreWindow::PointerPressed</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208278) | <span data-ttu-id="aba84-131">Die linke oder rechte Maustaste wurde gedrückt (und gedrückt gehalten), oder der Touchscreen wurde berührt.</span><span class="sxs-lookup"><span data-stu-id="aba84-131">The left or right mouse button was pressed (and held), or the touch surface was touched.</span></span>
[**<span data-ttu-id="aba84-132">CoreWindow::PointerMoved</span><span class="sxs-lookup"><span data-stu-id="aba84-132">CoreWindow::PointerMoved</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208276) |<span data-ttu-id="aba84-133">Die Maus wurde bewegt, oder eine Zieh-Aktion wurde auf dem Touchscreen ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="aba84-133">The mouse moved, or a drag action was made on the touch surface.</span></span>
[**<span data-ttu-id="aba84-134">CoreWindow::PointerReleased</span><span class="sxs-lookup"><span data-stu-id="aba84-134">CoreWindow::PointerReleased</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208279) |<span data-ttu-id="aba84-135">Die linke Maustaste wurde losgelassen, oder das Objekt, das den Touchscreen berührt, wurde angehoben.</span><span class="sxs-lookup"><span data-stu-id="aba84-135">The left mouse button was released, or the object contacting the touch surface was lifted.</span></span>
[**<span data-ttu-id="aba84-136">CoreWindow::PointerExited</span><span class="sxs-lookup"><span data-stu-id="aba84-136">CoreWindow::PointerExited</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208275) |<span data-ttu-id="aba84-137">Der Zeiger wurde aus dem Hauptfenster bewegt.</span><span class="sxs-lookup"><span data-stu-id="aba84-137">The pointer moved out of the main window.</span></span>
[**<span data-ttu-id="aba84-138">Windows::Devices::Input::MouseMoved</span><span class="sxs-lookup"><span data-stu-id="aba84-138">Windows::Devices::Input::MouseMoved</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh758356) | <span data-ttu-id="aba84-139">Die Maus wurde über eine bestimmte Distanz bewegt.</span><span class="sxs-lookup"><span data-stu-id="aba84-139">The mouse moved a certain distance.</span></span> <span data-ttu-id="aba84-140">Wir sind aber nur an Deltawerten der Mausbewegungen und nicht an der aktuellen x-y-Position interessiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-140">Be aware that we are only interested in mouse movement delta values, and not the current X-Y position.</span></span>


<span data-ttu-id="aba84-141">Diese Ereignishandler werden beim Starten der Überwachung für die Benutzereingabe festgelegt, sobald **MoveLookController** im Anwendungsfenster initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-141">These event handlers are set to start listening for user input as soon as the **MoveLookController** is initialized in the application window.</span></span>
```cpp
void MoveLookController::InitWindow(_In_ CoreWindow^ window)
{
    ResetState();

    window->PointerPressed +=
        ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerPressed);

    window->PointerMoved +=
        ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerMoved);

    window->PointerReleased +=
        ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerReleased);

    window->PointerExited +=
        ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerExited);

    // There is a separate handler for mouse only relative mouse movement events.
    MouseDevice::GetForCurrentView()->MouseMoved +=
        ref new TypedEventHandler<MouseDevice^, MouseEventArgs^>(this, &MoveLookController::OnMouseMoved);
    //
    // ...
    //
}
```

<span data-ttu-id="aba84-142">Der vollständige Code für [**InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L68-L92) wird auf GitHub angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aba84-142">Complete code for [**InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L68-L92) can be seen on GitHub.</span></span>


<span data-ttu-id="aba84-143">Um festzulegen, ob das Spiel auf Eingabe warten soll, verfügt die **MoveLookController**-Klasse unabhängig vom Steuerungstyp über drei Controllerzustände:</span><span class="sxs-lookup"><span data-stu-id="aba84-143">To determine when the game should be listening for certain input, the **MoveLookController** class has three controller-specific states, regardless of the controller type:</span></span>

<span data-ttu-id="aba84-144">Status</span><span class="sxs-lookup"><span data-stu-id="aba84-144">State</span></span> | <span data-ttu-id="aba84-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aba84-145">Description</span></span>
:----- | :-------
**<span data-ttu-id="aba84-146">Keins</span><span class="sxs-lookup"><span data-stu-id="aba84-146">None</span></span>** | <span data-ttu-id="aba84-147">Dies ist der Initialisierungszustand für den Controller.</span><span class="sxs-lookup"><span data-stu-id="aba84-147">This is the initialized state for the controller.</span></span> <span data-ttu-id="aba84-148">Das Spiel erwartet keine Controllereingabe und die Eingabe wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="aba84-148">All input is ignored since the game is not anticipating any controller input.</span></span>
**<span data-ttu-id="aba84-149">WaitForInput</span><span class="sxs-lookup"><span data-stu-id="aba84-149">WaitForInput</span></span>** | <span data-ttu-id="aba84-150">Der Controller wartet auf die Bestätigung der Nachricht des Spielers über das Spiel, entweder mit einem Mausklick, einem Touchereignis oder der Menütaste auf einem Gamepad.</span><span class="sxs-lookup"><span data-stu-id="aba84-150">The controller is waiting for the player to acknowledge a message from the game by either using a left mouse click, a touch event, ot the menu button on a gamepad.</span></span>
**<span data-ttu-id="aba84-151">Aktiv</span><span class="sxs-lookup"><span data-stu-id="aba84-151">Active</span></span>** | <span data-ttu-id="aba84-152">Der Controller ist im aktiven Spiel-Modus.</span><span class="sxs-lookup"><span data-stu-id="aba84-152">The controller is in active game play mode.</span></span>



### <a name="waitforinput-state-and-pausing-the-game"></a><span data-ttu-id="aba84-153">WaitForInput-Status und Anhalten des Spiels</span><span class="sxs-lookup"><span data-stu-id="aba84-153">WaitForInput state and pausing the game</span></span>

<span data-ttu-id="aba84-154">Das Spiel wechselt in den **WaitForInput**-Zustand, wenn das Spiel angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-154">The game enters the **WaitForInput** state when the game has been paused.</span></span> <span data-ttu-id="aba84-155">Dies passiert, wenn der Spieler den Zeiger aus dem Hauptfenster des Spiels bewegt oder die Pause-Taste drückt (P-TASTE oder **Start**-Taste auf dem Gamepad), drückt.</span><span class="sxs-lookup"><span data-stu-id="aba84-155">This happens when the player moves the pointer outside the main window of the game, or presses the pause button (the P key or the gamepad **Start** button).</span></span> <span data-ttu-id="aba84-156">Die **MoveLookController-Instanz** registriert die Tastenbetätigung und informiert die Spielschleife, wenn sie die [**IsPauseRequested**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L107-L127)-Methode aufruft.</span><span class="sxs-lookup"><span data-stu-id="aba84-156">The **MoveLookController** registers the press, and informs the game loop when it calls the [**IsPauseRequested**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L107-L127) method.</span></span> <span data-ttu-id="aba84-157">Wenn **IsPauseRequested** jetzt **true** zurückgibt, ruft die Spielschleife **WaitForPress** für die **MoveLookController**-Instanz auf, um den Controller in den Zustand **WaitForInput** zu versetzen.</span><span class="sxs-lookup"><span data-stu-id="aba84-157">At that point if **IsPauseRequested** returns **true**, the game loop then calls **WaitForPress** on the **MoveLookController** to move the controller into the **WaitForInput** state.</span></span> 


<span data-ttu-id="aba84-158">Im **WaitForInput**-Zustand beendet das Spiel die Verarbeitung von fast allen Eingabeereignissen, bis der Controller wieder in den **Active**-Zustand übergeht.</span><span class="sxs-lookup"><span data-stu-id="aba84-158">Once in the **WaitForInput** state, the game stops processing almost all gameplay input events until it returns to the **Active** state.</span></span> <span data-ttu-id="aba84-159">Eine Ausnahme ist die Pause-Taste, da durch Drücken der Taste das Spiel zum aktiven Zustand zurückkehret.</span><span class="sxs-lookup"><span data-stu-id="aba84-159">The exception is the pause button, with a press of this causing the game to go back to the active state.</span></span> <span data-ttu-id="aba84-160">Außer der Pause-Taste muss in der Reihenfolge für das Spiel zum **aktiven** Zustand zurückkehren der Spieler ein Menüelement auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="aba84-160">Other than the pause button, in order for the game to go back to the **Active** state the player needs to select a menu item.</span></span> 



### <a name="the-active-state"></a><span data-ttu-id="aba84-161">Der aktive Zustand</span><span class="sxs-lookup"><span data-stu-id="aba84-161">The Active state</span></span>

<span data-ttu-id="aba84-162">Im **aktiven** Zustand verarbeitet die **MoveLookController**-Instanz Eingabeereignisse von allen aktivierten Eingabegeräten und interpretiert die Absichten des Spielers.</span><span class="sxs-lookup"><span data-stu-id="aba84-162">During the **Active** state, the **MoveLookController** instance is processing events from all enabled input devices and interpreting the player's intentions.</span></span> <span data-ttu-id="aba84-163">Dadurch aktualisiert sie die Geschwindigkeit und Blickrichtung der Spieleransicht und gibt die aktualisierten Daten an das Spiel weiter, nachdem **Update** in der Spielschleife aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-163">As a result, it updates the velocity and look direction of the player's view and shares the updated data with the game after **Update** is called from the game loop.</span></span>


<span data-ttu-id="aba84-164">Mauseingaben werden im Zustand **Active** mit verschiedenen Zeiger-IDs für die unterschiedlichen Zeigeraktionen nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="aba84-164">All pointer input is tracked in the **Active** state, with different pointer IDs corresponding to different pointer actions.</span></span>
<span data-ttu-id="aba84-165">Wenn ein [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208278)-Ereignis empfangen wird, ruft die **MoveLookController**-Instanz den vom Fenster erstellten Wert der Zeiger-ID ab.</span><span class="sxs-lookup"><span data-stu-id="aba84-165">When a [**PointerPressed**](https://msdn.microsoft.com/library/windows/apps/br208278) event is received, the **MoveLookController** obtains the pointer ID value created by the window.</span></span> <span data-ttu-id="aba84-166">Die Zeiger-ID stellt einen bestimmten Eingabetyp dar.</span><span class="sxs-lookup"><span data-stu-id="aba84-166">The pointer ID represents a specific type of input.</span></span> <span data-ttu-id="aba84-167">Bei einem Multitouchgerät sind etwa gleichzeitig mehrere unterschiedliche aktive Eingaben möglich.</span><span class="sxs-lookup"><span data-stu-id="aba84-167">For example, on a multi-touch device, there may be several different active inputs at the same time.</span></span> <span data-ttu-id="aba84-168">Die IDs werden verwendet, um den vom Spieler verwendeten Eingabetyp nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="aba84-168">The IDs are used to keep track of which input the player is using.</span></span> <span data-ttu-id="aba84-169">Wenn ein Ereignis im Bewegungsrechteck des Touchscreens stattfindet, wird eine Zeiger-ID zugewiesen, um alle Zeigerereignisse im Bewegungsrechteck nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="aba84-169">If one event is in the move rectangle of the touch screen, a pointer ID is assigned to track any pointer events in the move rectangle.</span></span> <span data-ttu-id="aba84-170">Andere Zeigerereignisse im Schießrechteck werden separat mit einer anderen Zeiger-ID nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="aba84-170">Other pointer events in the fire rectangle are tracked separately, with a separate pointer ID.</span></span>


> [!NOTE]
> <span data-ttu-id="aba84-171">Eingaben von Maus und dem rechten Ministick auf einem Gamepad verfügen auch über die IDs, die separat behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-171">Input from the mouse and right thumbstick of a gamepad also have IDs that are handled separately.</span></span>

<span data-ttu-id="aba84-172">Nachdem die Zeigerereignisse einer bestimmten Spielaktion zugeordnet wurden, müssen die Daten aktualisiert werden, die das **MoveLookController**-Objekt an die Hauptspielschleife weitergibt.</span><span class="sxs-lookup"><span data-stu-id="aba84-172">After the pointer events have been mapped to a specific game action, it's time to update the data the **MoveLookController** object shares with the main game loop.</span></span>

<span data-ttu-id="aba84-173">Wenn die [**Update**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1005-L1096)-Methode im Beispielspiel aufgerufen wird, verarbeitet sie die Daten und aktualisiert die Geschwindigkeits- und Blickrichtungsvariablen (**m\_velocity** and **m\_lookdirection**), die dann von der Spielschleife durch Aufrufen der öffentlichen Methoden [**Velocity**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L906-L909) und [**LookDirection**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L913-L923)-Methode abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-173">When called, the [**Update**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1005-L1096) method in the game sample processes the input and updates the velocity and look direction variables (**m\_velocity** and **m\_lookdirection**), which the game loop then retrieves by calling the public [**Velocity**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L906-L909) and [**LookDirection**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L913-L923) methods.</span></span>

> [!NOTE]
> <span data-ttu-id="aba84-174">Weitere Informationen zur [**Update**](#the-update-method)-Methode finden Sie später auf dieser Seite.</span><span class="sxs-lookup"><span data-stu-id="aba84-174">More details about the [**Update**](#the-update-method) method can be seen later on this page.</span></span>




<span data-ttu-id="aba84-175">Die Spielschleife kann prüfen, ob der Spieler schießt, indem sie die **IsFiring**-Methode der **MoveLookController**-Instanz aufruft.</span><span class="sxs-lookup"><span data-stu-id="aba84-175">The game loop can test to see if the player is firing by calling the **IsFiring** method on the **MoveLookController** instance.</span></span> <span data-ttu-id="aba84-176">Die **MoveLookController**-Instanz überprüft, ob der Spieler über einen der drei Eingabetypen die Schießtaste betätigt hat.</span><span class="sxs-lookup"><span data-stu-id="aba84-176">The **MoveLookController** checks to see if the player has pressed the fire button on one of the three input types.</span></span>

```cpp
bool MoveLookController::IsFiring()
{
    if (m_state == MoveLookControllerState::Active)
    {
        if (m_autoFire)
        {
            return (m_fireInUse || (m_mouseInUse && m_mouseLeftInUse) || PollingFireInUse());
        }
        else
        {
            if (m_firePressed)
            {
                m_firePressed = false;
                return true;
            }
        }
    }
    return false;
}
```









<span data-ttu-id="aba84-177">Jetzt wollen wir uns etwas ausführlicher mit der Implementierung der drei Steuerungstypen beschäftigen.</span><span class="sxs-lookup"><span data-stu-id="aba84-177">Now, let's look at the implementation of each of the three control types in a little more detail.</span></span>

## <a name="adding-relative-mouse-controls"></a><span data-ttu-id="aba84-178">Hinzufügen relativer Maussteuerungen</span><span class="sxs-lookup"><span data-stu-id="aba84-178">Adding relative mouse controls</span></span>


<span data-ttu-id="aba84-179">Wenn Mausbewegungen erkannt werden, sollen diese Bewegungen zum Ermitteln des neuen Neigungs- und Schwenkwinkels der Kamera verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-179">If mouse movement is detected, we want to use that movement to determine the new pitch and yaw of the camera.</span></span> <span data-ttu-id="aba84-180">Hierzu implementieren wir relative Maussteuerungen, bei denen nicht die absoluten x-y-Pixelkoordinaten der Bewegung aufgezeichnet werden, sondern die relative Distanz der Mausbewegung (also das Delta zwischen Start und Ende der Bewegung) erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-180">We do that by implementing relative mouse controls, where we handle the relative distance the mouse has moved—the delta between the start of the movement and the stop—as opposed to recording the absolute x-y pixel coordinates of the motion.</span></span>

<span data-ttu-id="aba84-181">Dazu ermitteln wir die Änderung der X-Koordinate (horizontale Bewegung) und der Y-Koordinate (vertikale Bewegung), indem wir die Felder [**MouseDelta::X**](https://msdn.microsoft.com/library/windows/apps/hh758353) und **MouseDelta::Y** für das vom [**MouseMoved**](https://msdn.microsoft.com/library/windows/apps/hh758356)-Ereignis zurückgegebene [**Windows::Device::Input::MouseEventArgs::MouseDelta**](https://msdn.microsoft.com/library/windows/apps/hh758358)-Argumentobjekt überprüfen.</span><span class="sxs-lookup"><span data-stu-id="aba84-181">To do that, we obtain the changes in the X (the horizontal motion) and the Y (the vertical motion) coordinates by examining the [**MouseDelta::X**](https://msdn.microsoft.com/library/windows/apps/hh758353) and **MouseDelta::Y** fields on the [**Windows::Device::Input::MouseEventArgs::MouseDelta**](https://msdn.microsoft.com/library/windows/apps/hh758358) argument object returned by the [**MouseMoved**](https://msdn.microsoft.com/library/windows/apps/hh758356) event.</span></span>

```cpp
void MoveLookController::OnMouseMoved(
    _In_ MouseDevice^ /* mouseDevice */,
    _In_ MouseEventArgs^ args
    )
{
    // Handle Mouse Input via dedicated relative movement handler.

    switch (m_state)
    {
    case MoveLookControllerState::Active:
        XMFLOAT2 mouseDelta;
        mouseDelta.x = static_cast<float>(args->MouseDelta.X);
        mouseDelta.y = static_cast<float>(args->MouseDelta.Y);

        XMFLOAT2 rotationDelta;
        rotationDelta.x  = mouseDelta.x * MoveLookConstants::RotationGain;   // scale for control sensitivity
        rotationDelta.y  = mouseDelta.y * MoveLookConstants::RotationGain;

        // Update our orientation based on the command.
        m_pitch -= rotationDelta.y;
        m_yaw   += rotationDelta.x;

        // Limit pitch to straight up or straight down.
        float limit = XM_PI / 2.0f - 0.01f;
        m_pitch = __max(-limit, m_pitch);
        m_pitch = __min(+limit, m_pitch);

        // Keep longitude in same range by wrapping.
        if (m_yaw >  XM_PI)
        {
            m_yaw -= XM_PI * 2.0f;
        }
        else if (m_yaw < -XM_PI)
        {
            m_yaw += XM_PI * 2.0f;
        }
        break;
    }
}
```

## <a name="adding-touch-support"></a><span data-ttu-id="aba84-182">Hinzufügen der Toucheingabeunterstützung</span><span class="sxs-lookup"><span data-stu-id="aba84-182">Adding touch support</span></span>

<span data-ttu-id="aba84-183">Toucheingabesteuerungen sind ideal für Benutzer mit Tablets.</span><span class="sxs-lookup"><span data-stu-id="aba84-183">Touch controls are great for supporting users with tablets.</span></span> <span data-ttu-id="aba84-184">Dieses Spiel sammelt Toucheingaben durch die Zonenzuweisung bestimmter Bereiche des Bildschirms mit jeder Ausrichtung für bestimmte in-Spieleaktionen.</span><span class="sxs-lookup"><span data-stu-id="aba84-184">This game gathers touch input by zoning off certain areas of the screen with each aligning to specific in-game actions.</span></span>
<span data-ttu-id="aba84-185">Die Toucheingabe des Spiels verwendet drei Zonen.</span><span class="sxs-lookup"><span data-stu-id="aba84-185">This game's touch input uses three zones.</span></span>

![Bewegung Ansicht Toucheingabe - Layout](images/simple-dx-game-controls-touchzones.png)

<span data-ttu-id="aba84-187">Die folgenden Befehle fassen unser Verhalten für die Toucheingabesteuerelement zusammen.</span><span class="sxs-lookup"><span data-stu-id="aba84-187">The following commands summarize our touch control behavior.</span></span>
<span data-ttu-id="aba84-188">Benutzereingabe</span><span class="sxs-lookup"><span data-stu-id="aba84-188">User input</span></span> | <span data-ttu-id="aba84-189">Aktion</span><span class="sxs-lookup"><span data-stu-id="aba84-189">Action</span></span>
:------- | :--------
<span data-ttu-id="aba84-190">Bewegungsrechteck</span><span class="sxs-lookup"><span data-stu-id="aba84-190">Move rectangle</span></span> | <span data-ttu-id="aba84-191">Die Toucheingabe wird in einen virtuellen Joystick konvertiert, in dem die vertikale Bewegung in die Bewegung zur Vorwärts- und Rückwärtsbewegung übersetzt wird und die horizontale Bewegung in Bewegungen nach links/rechts übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-191">Touch input is converted into a virtual joystick where the vertical motion will be translated into forward/backward position motion and horizontal motion will be translated into left/right position motion.</span></span>
<span data-ttu-id="aba84-192">Schießrechtecke</span><span class="sxs-lookup"><span data-stu-id="aba84-192">Fire rectangle</span></span> | <span data-ttu-id="aba84-193">Mit der Maustaste schießen</span><span class="sxs-lookup"><span data-stu-id="aba84-193">Fire a sphere.</span></span>
<span data-ttu-id="aba84-194">Touch außerhalb der Bewegungs- und Schießrechtecke</span><span class="sxs-lookup"><span data-stu-id="aba84-194">Touch outside of move and fire rectangle</span></span> | <span data-ttu-id="aba84-195">Ändern Sie die Drehung (Neigungs- und Schwenkwinkel) der Kameraansicht.</span><span class="sxs-lookup"><span data-stu-id="aba84-195">Change the rotation (the pitch and yaw) of the camera view.</span></span>

<span data-ttu-id="aba84-196">Die **MoveLookController**-Instanz überprüft anhand der Zeiger-ID, wo das Ereignis aufgetreten ist, und führt eine der folgenden Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="aba84-196">The **MoveLookController** checks the pointer ID to determine where the event occurred, and takes one of the following actions:</span></span>

-   <span data-ttu-id="aba84-197">Wenn das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276)-Ereignis im Bewegungs- oder Schießrechteck aufgetreten ist, wird die Zeigerposition für den Controller aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-197">If the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276) event occurred in the move or fire rectangle, update the pointer position for the controller.</span></span>
-   <span data-ttu-id="aba84-198">Wenn das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276)-Ereignis an einer anderen Stelle des Bildschirms (definiert als Blicksteuerung) aufgetreten ist, werden die Änderungen des Nick- und Gierwinkels des Blickrichtungsvektors berechnet.</span><span class="sxs-lookup"><span data-stu-id="aba84-198">If the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276) event occurred somewhere in the rest of the screen (defined as the look controls), calculate the change in pitch and yaw of the look direction vector.</span></span>


<span data-ttu-id="aba84-199">Nachdem wir unsere Toucheingabesteuerungen implementiert haben, werden die Rechtecke, die wir zuvor mithilfe von Direct2D gezeichnet haben dem Spieler anzeigen, wo er sich in den Bereichen bewegen, schießen und hinsehen soll.</span><span class="sxs-lookup"><span data-stu-id="aba84-199">Once we've implemented our touch controls, the rectangles we drew earlier using Direct2D will indicate to players where the move, fire, and look zones are.</span></span>


![Toucheingabesteuerungen](images/simple-dx-game-controls-showzones.png)


<span data-ttu-id="aba84-201">Sehen wir uns an, wie jedes Steuerelement implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-201">Now let's take a look at how we implement each control.</span></span>


### <a name="move-and-fire-controller"></a><span data-ttu-id="aba84-202">Bewegungs- und Schieß-Controller</span><span class="sxs-lookup"><span data-stu-id="aba84-202">Move and fire controller</span></span>
<span data-ttu-id="aba84-203">Das Bewegungsrechteck des Controllers im unteren linken Quadranten des Bildschirms wird als Steuerkreuz verwendet.</span><span class="sxs-lookup"><span data-stu-id="aba84-203">The move controller rectangle in the lower left quadrant of the screen is used as a directional pad.</span></span> <span data-ttu-id="aba84-204">Wenn Sie den Daumen nach links und rechts auf dieser Fläche bewegen, wird der Spieler nach links und rechts bewegt, und eine Bewegung nach oben oder unten bewegt die Kamera vorwärts und rückwärts.</span><span class="sxs-lookup"><span data-stu-id="aba84-204">Sliding your thumb left and right within this space moves the player left and right, while up and down moves the camera forward and backward.</span></span>
<span data-ttu-id="aba84-205">Nach dem Einrichten wird durch das Tippen auf den Schieß-Controller im unteren rechten Quadrant des Bildschirms geschossen.</span><span class="sxs-lookup"><span data-stu-id="aba84-205">After setting this up, tapping the fire controller in the lower right quadrant of the screen fires a sphere.</span></span>

<span data-ttu-id="aba84-206">Mit den [**SetMoveRect**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L843-L853) und [**SetFireRect**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L857-L867)-Methoden werden die Eingaberechtecke mit zwei Methoden erstellt, indem zwei 2D-Vektoren an jedem Rechtecke oben links und unten rechts unten auf dem Bildschirm positioniert werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-206">The [**SetMoveRect**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L843-L853) and [**SetFireRect**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L857-L867) methods create our input rectangles, taking two, 2D vectors to specify each rectangles' upper left and lower right corner positions on the screen.</span></span> 


<span data-ttu-id="aba84-207">Die Parameter werden dann auf **m\_fireUpperLeft** und **m\_fireLowerRight** zugewiesen, was uns hilft, zu bestimmen, ob der Benutzer innerhalb der Rechtecke ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-207">The parameters are then assigned to **m\_fireUpperLeft** and **m\_fireLowerRight** that will help us determine if the user is touching within on of the rectangles.</span></span> 
```cpp
m_fireUpperLeft  = upperLeft;
m_fireLowerRight = lowerRight;
```

<span data-ttu-id="aba84-208">Wenn die Bildschirmgröße geändert wird, werden die Rechtecke neu auf die Größe angepasst.</span><span class="sxs-lookup"><span data-stu-id="aba84-208">If the screen is resized, these rectangles are redrawn to the approperiate size.</span></span>


<span data-ttu-id="aba84-209">Nun, da wir unsere Steuerelemente in Zonen haben, ist es Zeit zu bestimmen, ob ein Benutzer diese tatsächlich verwendet.</span><span class="sxs-lookup"><span data-stu-id="aba84-209">Now that we've zoned off our controls, it's time to determine when a user is actually using them.</span></span>
<span data-ttu-id="aba84-210">Hierzu legen wir einige Ereignishandler in der **MoveLookController::InitWindow**-Methode fest, wenn der Benutzer den Mauszeiger drückt, verschiebt oder freigibt.</span><span class="sxs-lookup"><span data-stu-id="aba84-210">To do this, we set up some event handlers in the **MoveLookController::InitWindow** method for when the user presses, moves, or releases their pointer.</span></span>

```cpp
window->PointerPressed +=
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerPressed);

window->PointerMoved +=
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerMoved);

window->PointerReleased +=
    ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &MoveLookController::OnPointerReleased);
```


<span data-ttu-id="aba84-211">Wir ermitteln, was geschieht, wenn der Benutzer zunächst auf die Bewegungs- oder Schießrechtecke drückt, mithilfe der [**OnPointerPressed**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L179-L313)-Methode.</span><span class="sxs-lookup"><span data-stu-id="aba84-211">We'll first determine what happens when the user first presses within the move or fire rectangles using the [**OnPointerPressed**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L179-L313) method.</span></span>
<span data-ttu-id="aba84-212">Hier überprüfen wir, wo ein Steuerelement berührt wird und ob ein Zeiger bereits in diesem Controller vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-212">Here we check where they're touching a control and if a pointer is already in that controller.</span></span> <span data-ttu-id="aba84-213">Wenn dies der erste Finger ist. der das spezifische Steuerelement berührt, gehen wir wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="aba84-213">If this is the first finger to touch the specific control, we do the following.</span></span>
- <span data-ttu-id="aba84-214">Speichern Sie den Ort des Bereichs in **m\_moveFirstDown** oder **m\_fireFirstDown** als 2D-Vektor.</span><span class="sxs-lookup"><span data-stu-id="aba84-214">Store the location of the touchdown in **m\_moveFirstDown** or **m\_fireFirstDown** as a 2D vector.</span></span>
- <span data-ttu-id="aba84-215">Weisen Sie die Zeiger-ID **m\_movePointerID** oder **m\_firePointerID**.</span><span class="sxs-lookup"><span data-stu-id="aba84-215">Assign the pointer ID to **m\_movePointerID** or **m\_firePointerID**.</span></span>
- <span data-ttu-id="aba84-216">Legen Sie das richtige **InUse**-Kennzeichen (**m\_moveInUse** oder **m\_fireInUse**) auf `true` fest, da wir nun einen aktiven Zeiger für das Steuerelement haben.</span><span class="sxs-lookup"><span data-stu-id="aba84-216">Set the proper **InUse** flag (**m\_moveInUse** or **m\_fireInUse**) to `true` since we now have an active pointer for that control.</span></span>


```cpp
    PointerPoint^ point = args->CurrentPoint;
    uint32 pointerID = point->PointerId;
    Point pointerPosition = point->Position;
    PointerPointProperties^ pointProperties = point->Properties;
    auto pointerDevice = point->PointerDevice;
    auto pointerDeviceType = pointerDevice->PointerDeviceType;

    XMFLOAT2 position = XMFLOAT2(pointerPosition.X, pointerPosition.Y);

    case MoveLookControllerState::Active:
        switch (pointerDeviceType)
        {
        case Windows::Devices::Input::PointerDeviceType::Touch:
            // Check to see if this pointer is in the move control.
            if (position.x > m_moveUpperLeft.x &&
                position.x < m_moveLowerRight.x &&
                position.y > m_moveUpperLeft.y &&
                position.y < m_moveLowerRight.y)
            {
                if (!m_moveInUse)         // If no pointer is in this control yet:
                {
                    // Process a DPad touch down event.
                    m_moveFirstDown = position;                 // Save the location of the initial contact
                    m_movePointerID = pointerID;                // Store the pointer using this control
                    m_moveInUse = true;                         // Set InUse flag to signal there is an active move pointer
                }
            }
            // Check to see if this pointer is in the fire control.
            else if (position.x > m_fireUpperLeft.x &&
                position.x < m_fireLowerRight.x &&
                position.y > m_fireUpperLeft.y &&
                position.y < m_fireLowerRight.y)
            {
                if (!m_fireInUse)
                {
                    m_fireLastPoint = position;     // Save the location of the initial contact
                    m_firePointerID = pointerID;    // Store the pointer using this control
                    m_fireInUse = true;             // Set InUse flag to signal there is an active fire pointer
                }
            }
            ...
```


<span data-ttu-id="aba84-217">Nachdem wir ermittelt haben, ob der Benutzer ein Steuerelement verschiebt oder schießt, sehen wir, ob der Spieler alle Bewegungen mit dem Finger macht.</span><span class="sxs-lookup"><span data-stu-id="aba84-217">Now that we've determined whether the user is touching a move or fire control, we see if the player is making any movements with their pressed finger.</span></span>
<span data-ttu-id="aba84-218">Mithilfe der [**MoveLookController::OnPointerMoved**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L317-L395)-Methode überprüfen wir, welche Zeiger verschoben wurden, und speichern dann die neue Position als 2D-Vektor.</span><span class="sxs-lookup"><span data-stu-id="aba84-218">Using the [**MoveLookController::OnPointerMoved**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L317-L395) method, we check what pointer has moved and then store its new position as a 2D vector.</span></span>  


```cpp
    PointerPoint^ point = args->CurrentPoint;
    uint32 pointerID = point->PointerId;
    Point pointerPosition = point->Position;
    PointerPointProperties^ pointProperties = point->Properties;
    auto pointerDevice = point->PointerDevice;

    XMFLOAT2 position = XMFLOAT2(pointerPosition.X, pointerPosition.Y);     // convert to allow math
    
    switch (m_state)
    {
    case MoveLookControllerState::Active:
        // Decide which control this pointer is operating.
        
        // Move control
        if (pointerID == m_movePointerID)
        {
            m_movePointerPosition = position;       // Save the current position.
        }
        // Look control
        else if (pointerID == m_lookPointerID)
        {
            // ...
        }
        // Fire control
        else if (pointerID == m_firePointerID)
        {
            m_fireLastPoint = position;
        }
```


<span data-ttu-id="aba84-219">Nachdem der Benutzer seine Gesten in den Steuerelementen vorgenommen hat, lassen sie den Zeiger los.</span><span class="sxs-lookup"><span data-stu-id="aba84-219">Once the user has made their gestures within the controls, they'll release the pointer.</span></span> <span data-ttu-id="aba84-220">Mithilfe der [**MoveLookController::OnPointerReleased**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500)-Methode ermitteln wir, welche Zeiger freigegeben wurden und führen eine Reihe von Zurücksetzungen durch.</span><span class="sxs-lookup"><span data-stu-id="aba84-220">Using the [**MoveLookController::OnPointerReleased**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500) method, we determine which pointer has been released and do a series of resets.</span></span>


<span data-ttu-id="aba84-221">Wenn das Steuerelement freigegeben wurde, gehen wir wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="aba84-221">If the move control has been released, we do the following.</span></span>
- <span data-ttu-id="aba84-222">Legen Sie die Geschwindigkeit des Players auf `0` in alle Richtungen fest, um zu verhindern, dass Sie im Spiel verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-222">Set the velocity of the player to `0` in all directions to prevent them from moving in the game.</span></span>
- <span data-ttu-id="aba84-223">Legen Sie **m\_moveInUse** auf `false` fest, da der Benutzer den Bewegungscontrollers nicht mehr berührt.</span><span class="sxs-lookup"><span data-stu-id="aba84-223">Switch **m\_moveInUse** to `false` since the user is no longer touching the move controller.</span></span>
- <span data-ttu-id="aba84-224">Legen Sie die Bewegungszeiger-ID auf `0` fest, da der Bewegungscontroller keinen Zeiger mehr hat.</span><span class="sxs-lookup"><span data-stu-id="aba84-224">Set the move pointer ID to `0` since there's no longer a pointer in the move controller.</span></span>

```cpp
       if (pointerID == m_movePointerID)
        {
            m_velocity = XMFLOAT3(0, 0, 0);      // Stop on release.
            m_moveInUse = false;
            m_movePointerID = 0;
        }
```


<span data-ttu-id="aba84-225">Wenn das Schießsteuerelement ausgelöst wird, legen wir lediglich die **M_fireInUse**-Kennzeichnung auf `false` fest und die Schießzeiger-ID auf `0`, da im Schießsteuerelement kein Zeiger mehr vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-225">For the fire control, if it has been released all we do is switch the **m_fireInUse** flag to `false` and the fire pointer ID to `0` since there's no longer a pointer in the fire control.</span></span>
```cpp
        else if (pointerID == m_firePointerID)
        {
            m_fireInUse = false;
            m_firePointerID = 0;
        }
```

### <a name="look-controller"></a><span data-ttu-id="aba84-226">Blickrichtungscontroller</span><span class="sxs-lookup"><span data-stu-id="aba84-226">Look controller</span></span>
<span data-ttu-id="aba84-227">Zeigerereignisse von Fingereingabegeräten für die offene Bildschirmbereiche werden als Blickrichtungscontroller behandelt.</span><span class="sxs-lookup"><span data-stu-id="aba84-227">We treat touch device pointer events for the unused regions of the screen as the look controller.</span></span> <span data-ttu-id="aba84-228">Das Bewegen Ihrer Finger über diese Zone ändert den Neigungswinkel und Schwenkwinkel (Drehung) der Spieler-Kamera.</span><span class="sxs-lookup"><span data-stu-id="aba84-228">Sliding your finger around this zone changes the pitch and yaw (rotation) of the player camera.</span></span>


<span data-ttu-id="aba84-229">Wird in einem dieser Bereiche ein **MoveLookController::OnPointerPressed**-Ereignis von einem Toucheingabegerät ausgelöst, während sich das Spiel im Zustand **Active** befindet, wird ihm wie zuvor erläutert eine Zeiger-ID zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="aba84-229">If the **MoveLookController::OnPointerPressed** event is raised on a touch device in this region and the game state is set to **Active**, it's assigned a pointer ID.</span></span>

```cpp
    if (!m_lookInUse)   // If no pointer is in this control yet:
    {
        m_lookLastPoint = position;                   // Save the pointer for a later move.
        m_lookPointerID = pointerID;                  // Store the pointer using this control.
        m_lookLastDelta.x = m_lookLastDelta.y = 0;    // These are for smoothing.
        m_lookInUse = true;
    }
```
<span data-ttu-id="aba84-230">Sehen Sie den vollständigen Code für die **MoveLookController::OnPointerPressed**-Methode auf [GitHub](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L252-L259).</span><span class="sxs-lookup"><span data-stu-id="aba84-230">You can see the complete code for the **MoveLookController::OnPointerPressed** method on [GitHub](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L252-L259).</span></span>




<span data-ttu-id="aba84-231">Hier weist **MoveLookController** die Zeiger-ID für den Zeiger zu, der das Ereignis für eine bestimmte Variable ausgelöst hat, die dem Blickbereich entspricht.</span><span class="sxs-lookup"><span data-stu-id="aba84-231">Here the **MoveLookController** assigns the pointer ID for the pointer that fired the event to a specific variable that corresponds to the look region.</span></span> <span data-ttu-id="aba84-232">Bei einem Touchereignis im Blickwinkelbereich wird z.B. die **m\_lookPointerID**-Variable auf die Zeiger-ID festgelegt, von der das Ereignis ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-232">In the case of a touch occuring in the look region, the **m\_lookPointerID** variable is set to the pointer ID that fired the event.</span></span> <span data-ttu-id="aba84-233">Außerdem wird die boolesche Verwendungsvariable **m\_lookInUse** festgelegt, um anzugeben, dass die Steuerung noch nicht freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-233">A boolean variable, **m\_lookInUse**, is also set to indicate that the control has not yet been released.</span></span>

<span data-ttu-id="aba84-234">Im nächsten Schritt erfahren Sie, wie das Beispielspiel das [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276)-Touchscreenereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="aba84-234">Now, let's look at how the game sample handles the [**PointerMoved**](https://msdn.microsoft.com/library/windows/apps/br208276) touch screen event.</span></span>


<span data-ttu-id="aba84-235">In der **MoveLookController::OnPointerMoved**-Methode überprüfen wir, welche Art von Zeiger-ID dem Ereignis zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-235">Within the **MoveLookController::OnPointerMoved** method, we check to see what kind of pointer ID has been assigned to the event.</span></span> <span data-ttu-id="aba84-236">Ist es **m_lookPointerID**, berechnen wir die Änderung an der Position des Zeigers.</span><span class="sxs-lookup"><span data-stu-id="aba84-236">If it's **m_lookPointerID**, we calculate the change in position of the pointer.</span></span>
<span data-ttu-id="aba84-237">Wir verwenden dann Deltas, um zu berechnen, wie die Drehung geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="aba84-237">We then use this delta to calculate how much the rotation should change.</span></span> <span data-ttu-id="aba84-238">Schließlich können wir **m\_pitch** und **m\_yaw** im Spiel aktualisieren, um im Spiel die Player-Drehung zu ändern.</span><span class="sxs-lookup"><span data-stu-id="aba84-238">Finally we're at a point where we can update the **m\_pitch** and **m\_yaw** to be used in the game to change the player rotation.</span></span> 

```cpp
    else if (pointerID == m_lookPointerID)     // This is the look pointer.
    {
        // Look control
        XMFLOAT2 pointerDelta;
        pointerDelta.x = position.x - m_lookLastPoint.x;        // How far did the pointer move.
        pointerDelta.y = position.y - m_lookLastPoint.y;

        XMFLOAT2 rotationDelta;
        rotationDelta.x = pointerDelta.x * MoveLookConstants::RotationGain;       // Scale for control sensitivity.
        rotationDelta.y = pointerDelta.y * MoveLookConstants::RotationGain;
        m_lookLastPoint = position;                             // Save for the next time through.

        // Update our orientation based on the command.
        m_pitch -= rotationDelta.y;
        m_yaw   += rotationDelta.x;

        // Limit pitch to straight up or straight down.
        float limit = XM_PI / 2.0f - 0.01f;
        m_pitch = __max(-limit, m_pitch);
        m_pitch = __min(+limit, m_pitch);M_PI / 2.0f, m_pitch);
        }
```





<span data-ttu-id="aba84-239">Zum Schluss sehen wir uns an, wie das Beispielspiel das [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279)-Touchscreenereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="aba84-239">The last piece we'll look at is how the game sample handles the [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) touch screen event.</span></span>
<span data-ttu-id="aba84-240">Nachdem der Benutzer die Geste abgeschlossen und den Finger vom Bildschirm entfernt hat, wird [**MoveLookController::OnPointerReleased**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500) initiiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-240">Once the user has finished the touch gesture and removed their finger from the screen, [**MoveLookController::OnPointerReleased**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500) is initiated.</span></span>
<span data-ttu-id="aba84-241">Wenn die ID des Zeigers, von dem das [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279)-Ereignis ausgelöst wurde, die ID des zuvor erfassten Mauszeigers ist, legt die **MoveLookController**-Instanz die Geschwindigkeit auf `0` fest, da der Spieler den Blickbereich nicht mehr berührt.</span><span class="sxs-lookup"><span data-stu-id="aba84-241">If the ID of the pointer that fired the [**PointerReleased**](https://msdn.microsoft.com/library/windows/apps/br208279) event is the ID of the previously recorded move pointer, the **MoveLookController** sets the velocity to `0` because the player has stopped touching the look area.</span></span>

```cpp
    else if (pointerID == m_lookPointerID)
    {
        m_lookInUse = false;
        m_lookPointerID = 0;
    }
```





## <a name="adding-mouse-and-keyboard-support"></a><span data-ttu-id="aba84-242">Hinzufügen von Tastatur- und Mausunterstützung</span><span class="sxs-lookup"><span data-stu-id="aba84-242">Adding mouse and keyboard support</span></span>


<span data-ttu-id="aba84-243">Dieses Spiel hat das folgende Steuerelementlayout für Tastatur und Maus.</span><span class="sxs-lookup"><span data-stu-id="aba84-243">This game has the following control layout for keyboard and mouse.</span></span>

<span data-ttu-id="aba84-244">Benutzereingabe</span><span class="sxs-lookup"><span data-stu-id="aba84-244">User input</span></span> | <span data-ttu-id="aba84-245">Aktion</span><span class="sxs-lookup"><span data-stu-id="aba84-245">Action</span></span>
:------- | :--------
<span data-ttu-id="aba84-246">W</span><span class="sxs-lookup"><span data-stu-id="aba84-246">W</span></span> | <span data-ttu-id="aba84-247">Spieler vorwärts</span><span class="sxs-lookup"><span data-stu-id="aba84-247">Move player forward</span></span>
<span data-ttu-id="aba84-248">A</span><span class="sxs-lookup"><span data-stu-id="aba84-248">A</span></span> | <span data-ttu-id="aba84-249">Spieler nach links</span><span class="sxs-lookup"><span data-stu-id="aba84-249">Move player left</span></span>
<span data-ttu-id="aba84-250">S</span><span class="sxs-lookup"><span data-stu-id="aba84-250">S</span></span> | <span data-ttu-id="aba84-251">Spieler rückwärts</span><span class="sxs-lookup"><span data-stu-id="aba84-251">Move player backward</span></span>
<span data-ttu-id="aba84-252">D</span><span class="sxs-lookup"><span data-stu-id="aba84-252">D</span></span> | <span data-ttu-id="aba84-253">Spieler nach rechts</span><span class="sxs-lookup"><span data-stu-id="aba84-253">Move player right</span></span>
<span data-ttu-id="aba84-254">X</span><span class="sxs-lookup"><span data-stu-id="aba84-254">X</span></span> | <span data-ttu-id="aba84-255">Ansicht nach oben</span><span class="sxs-lookup"><span data-stu-id="aba84-255">Move view up</span></span>
<span data-ttu-id="aba84-256">Leertaste</span><span class="sxs-lookup"><span data-stu-id="aba84-256">Space bar</span></span> | <span data-ttu-id="aba84-257">Ansicht nach unten</span><span class="sxs-lookup"><span data-stu-id="aba84-257">Move view down</span></span>
<span data-ttu-id="aba84-258">P</span><span class="sxs-lookup"><span data-stu-id="aba84-258">P</span></span> | <span data-ttu-id="aba84-259">Hält das Spiel an</span><span class="sxs-lookup"><span data-stu-id="aba84-259">Pause the game</span></span>
<span data-ttu-id="aba84-260">Mausbewegung</span><span class="sxs-lookup"><span data-stu-id="aba84-260">Mouse movement</span></span> | <span data-ttu-id="aba84-261">Ändern Sie die Drehung (Neigungs- und Schwenkwinkel) der Kameraansicht</span><span class="sxs-lookup"><span data-stu-id="aba84-261">Change the rotation (the pitch and yaw) of the camera view</span></span>
<span data-ttu-id="aba84-262">Linke Maustaste</span><span class="sxs-lookup"><span data-stu-id="aba84-262">Left mouse button</span></span> | <span data-ttu-id="aba84-263">Mit der Maustaste schießen</span><span class="sxs-lookup"><span data-stu-id="aba84-263">Fire a sphere</span></span>


<span data-ttu-id="aba84-264">Um die Tastatur zu verwenden, registriert das Beispielspiel zwei neue Ereignisse, [**CoreWindow: KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208271) und [**CoreWindow:: KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208270) in der [**MoveLookController::InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L84-L88)-Methode.</span><span class="sxs-lookup"><span data-stu-id="aba84-264">To use the keyboard, the game sample registers two new events, [**CoreWindow::KeyUp**](https://msdn.microsoft.com/library/windows/apps/br208271) and [**CoreWindow::KeyDown**](https://msdn.microsoft.com/library/windows/apps/br208270), within the [**MoveLookController::InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L84-L88) method.</span></span> <span data-ttu-id="aba84-265">Diese Ereignisse behandeln das Drücken und Loslassen einer Taste.</span><span class="sxs-lookup"><span data-stu-id="aba84-265">These events handle the press and release of a key.</span></span>

```cpp
window->KeyDown +=
        ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &MoveLookController::OnKeyDown);

window->KeyUp +=
        ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &MoveLookController::OnKeyUp);
```

<span data-ttu-id="aba84-266">Die Behandlung der Maus unterscheidet sich etwas von der der Fingereingabesteuerung, obwohl sie einen Zeiger verwendet.</span><span class="sxs-lookup"><span data-stu-id="aba84-266">The mouse is treated a little differently from the touch controls even though it uses a pointer.</span></span> <span data-ttu-id="aba84-267">Um unsere Steuerelementlayout anzupassen, dreht der **MoveLookController** die Kamera, wenn die Maus bewegt wird, und schießt, wenn die linke Maustaste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-267">To align with our control layout, the **MoveLookController** rotates the camera whenever the mouse is moved, and fires when the left mouse button is pressed.</span></span>


<span data-ttu-id="aba84-268">Dies erfolgt in der [**OnPointerPressed**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L179-L313)-Methode des **MoveLookController**.</span><span class="sxs-lookup"><span data-stu-id="aba84-268">This is handled in the [**OnPointerPressed**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L179-L313) method of the **MoveLookController**.</span></span>

<span data-ttu-id="aba84-269">In dieser Methode überprüfen wir, welche Art von Zeigegerät verwendet wird durch Verwendung der [`Windows::Devices::Input::PointerDeviceType`](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Input.PointerDeviceType)-Enumeration.</span><span class="sxs-lookup"><span data-stu-id="aba84-269">In this method we check to see what type of pointer device is being used with the [`Windows::Devices::Input::PointerDeviceType`](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Input.PointerDeviceType) enum.</span></span> <span data-ttu-id="aba84-270">Wenn das Spiel **aktiv** ist und **PointerDeviceType** nicht **Touch** ist, ist dies die Mauseingabe.</span><span class="sxs-lookup"><span data-stu-id="aba84-270">If the game is **Active** and the **PointerDeviceType** isn't **Touch**, we assume it's mouse input.</span></span>

```cpp
    case MoveLookControllerState::Active:
        switch (pointerDeviceType)
        {
        case Windows::Devices::Input::PointerDeviceType::Touch:
            // Behavior for touch controls
        
        default:
        // Behavior for mouse controls
            bool rightButton = pointProperties->IsRightButtonPressed;
            bool leftButton = pointProperties->IsLeftButtonPressed;

            if (!m_autoFire && (!m_mouseLeftInUse && leftButton))
            {
                m_firePressed = true;
            }

            if (!m_mouseInUse)
            {
                m_mouseInUse = true;
                m_mouseLastPoint = position;
                m_mousePointerID = pointerID;
                m_mouseLeftInUse = leftButton;
                m_mouseRightInUse = rightButton;
                m_lookLastDelta.x = m_lookLastDelta.y = 0;          // These are for smoothing.
            }
            break;
        }
```

<span data-ttu-id="aba84-271">Wenn der Spieler aufhört, eine der Maustasten zu drücken, wird das [CoreWindow::PointerReleased](https://docs.microsoft.com/uwp/api/Windows.UI.Core.CoreWindow.PointerReleased)-Mausereignis aufgerufen, indem die [MoveLookController::OnPointerReleased](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500)-Methode aufgerufen wird. Die Eingabe ist dann abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="aba84-271">When the player stops pressing one of the mouse buttons, the [CoreWindow::PointerReleased](https://docs.microsoft.com/uwp/api/Windows.UI.Core.CoreWindow.PointerReleased) mouse event is raised, calling the [MoveLookController::OnPointerReleased](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L441-L500) method, and the input is complete.</span></span> <span data-ttu-id="aba84-272">An diesem Punkt werden keine Kugeln mehr ausgelöst, wenn die linke Maustaste gedrückt und freigegeben wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-272">At this point, spheres will stop firing if the left mouse button was being pressed and is now released.</span></span> <span data-ttu-id="aba84-273">Da die Blicksteuerung immer aktiviert ist, verwendet das Spiel weiter den gleichen Mauszeiger, um die Blickereignisse nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="aba84-273">Because look is always enabled, the game continues to use the same mouse pointer to track the ongoing look events.</span></span>

```cpp
    case MoveLookControllerState::Active:
        // Touch points
        if (pointerID == m_movePointerID)
        {
            // Stop movement
        }
        else if (pointerID == m_lookPointerID)
        {
            // Stop look rotation
        }
        // Fire button has been released
        else if (pointerID == m_firePointerID)
        {
            // Stop firing
        }
        // Mouse point
        else if (pointerID == m_mousePointerID)
        {
            bool rightButton = pointProperties->IsRightButtonPressed;
            bool leftButton = pointProperties->IsLeftButtonPressed;

            // Mouse no longer in use so stop firing
            m_mouseInUse = false;

            // Don't clear the mouse pointer ID so that Move events still result in Look changes.
            // m_mousePointerID = 0;
            m_mouseLeftInUse = leftButton;
            m_mouseRightInUse = rightButton;
        }
        break;
    }
}
```



<span data-ttu-id="aba84-274">Jetzt sehen wir uns den letzten unterstützen Steuerelementtyp an: Gamepads.</span><span class="sxs-lookup"><span data-stu-id="aba84-274">Now let's look at the last control type we'll be supporting: gamepads.</span></span> <span data-ttu-id="aba84-275">Gamepads werden getrennt von den Fingereingabe- und Maussteuerungen behandelt, da sie kein Zeigerobjekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="aba84-275">Gamepads are handled separately from the touch and mouse controls since they doesn't use the pointer object.</span></span> <span data-ttu-id="aba84-276">Aus diesem Grund müssen ein paar neue Ereignishandler und Methoden hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="aba84-276">Because of this, a few new event handlers and methods will need to be added.</span></span>

## <a name="adding-gamepad-support"></a><span data-ttu-id="aba84-277">Hinzufügen von Gamepad-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="aba84-277">Adding gamepad support</span></span>


<span data-ttu-id="aba84-278">Für dieses Spiel wird die Gamepad-Unterstützung durch Aufrufen der [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input)-APIs hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="aba84-278">For this game, gamepad support is added by calls to the [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input) APIs.</span></span> <span data-ttu-id="aba84-279">Dieser Satz von APIs bietet Zugriff auf Gamecontrollereingaben, wie Rennlenkräder und Flight-Sticks.</span><span class="sxs-lookup"><span data-stu-id="aba84-279">This set of APIs provides access to game controller inputs like racing wheels and flight sticks.</span></span> 


<span data-ttu-id="aba84-280">Hier sind unsere Gamepad-Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="aba84-280">The following will be our gamepad controls.</span></span>

<span data-ttu-id="aba84-281">Benutzereingabe</span><span class="sxs-lookup"><span data-stu-id="aba84-281">User input</span></span> | <span data-ttu-id="aba84-282">Aktion</span><span class="sxs-lookup"><span data-stu-id="aba84-282">Action</span></span>
:------- | :--------
<span data-ttu-id="aba84-283">Linker Joystick</span><span class="sxs-lookup"><span data-stu-id="aba84-283">Left analog stick</span></span> | <span data-ttu-id="aba84-284">Spieler bewegen</span><span class="sxs-lookup"><span data-stu-id="aba84-284">Move player</span></span>
<span data-ttu-id="aba84-285">Rechter Joystick</span><span class="sxs-lookup"><span data-stu-id="aba84-285">Right analog stick</span></span> | <span data-ttu-id="aba84-286">Ändern Sie die Drehung (Neigungs- und Schwenkwinkel) der Kameraansicht</span><span class="sxs-lookup"><span data-stu-id="aba84-286">Change the rotation (the pitch and yaw) of the camera view</span></span>
<span data-ttu-id="aba84-287">Rechter Trigger</span><span class="sxs-lookup"><span data-stu-id="aba84-287">Right trigger</span></span> | <span data-ttu-id="aba84-288">Mit der Maustaste schießen</span><span class="sxs-lookup"><span data-stu-id="aba84-288">Fire a sphere</span></span>
<span data-ttu-id="aba84-289">Ein-/Aus-Menütaste</span><span class="sxs-lookup"><span data-stu-id="aba84-289">Start/Menu button</span></span> | <span data-ttu-id="aba84-290">Anhalten oder Fortsetzen des Spiels</span><span class="sxs-lookup"><span data-stu-id="aba84-290">Pause or resume the game</span></span>




<span data-ttu-id="aba84-291">In der [**InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L68-L103)-Methode fügen wir zwei neue Ereignisse hinzu, um festzustellen, ob ein Gamepad [hinzugefügt](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1100-L1105) oder [entfernt](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1109-L1114) wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-291">In the [**InitWindow**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L68-L103) method, we add two new events to determine if a gamepad has been [added](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1100-L1105) or [removed](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1109-L1114).</span></span> <span data-ttu-id="aba84-292">Diese Ereignisse aktualisieren die **m_gamepadsChanged**-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="aba84-292">These events update the **m_gamepadsChanged** property.</span></span> <span data-ttu-id="aba84-293">In der **UpdatePollingDevices** -Methode wird verwendet, um zu überprüfen, ob die Liste der bekannten Gamepads geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="aba84-293">This is used in the **UpdatePollingDevices** method to check if the list of known gamepads has changed.</span></span> 

```cpp
    // Detect gamepad connection and disconnection events.
    Gamepad::GamepadAdded +=
        ref new EventHandler<Gamepad^>(this, &MoveLookController::OnGamepadAdded);

    Gamepad::GamepadRemoved +=
        ref new EventHandler<Gamepad^>(this, &MoveLookController::OnGamepadRemoved);
```

### <a name="the-updatepollingdevices-method"></a><span data-ttu-id="aba84-294">Die UpdatePollingDevices-Methode</span><span class="sxs-lookup"><span data-stu-id="aba84-294">The UpdatePollingDevices method</span></span>

<span data-ttu-id="aba84-295">Die [**UpdatePollingDevices**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L654-L782)-Methode der **MoveLookController**-Instanz sofort überprüft, ob ein Gamepad verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-295">The [**UpdatePollingDevices**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L654-L782) method of the **MoveLookController** instance immediately checks to see if a gamepad is connected.</span></span> <span data-ttu-id="aba84-296">Wenn ja, beginnen wir den Zustand mit [**Gamepad.GetCurrentReading**](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.GetCurrentReading) zu lesen.</span><span class="sxs-lookup"><span data-stu-id="aba84-296">If one is, we'll start reading its state with [**Gamepad.GetCurrentReading**](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.GetCurrentReading).</span></span> <span data-ttu-id="aba84-297">Dies gibt die [**GamepadReading**](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.GamepadReading)-Struktur zurück, um zu überprüfen, welche Schaltflächen aktiviert oder Ministicks verschoben wurden.</span><span class="sxs-lookup"><span data-stu-id="aba84-297">This returns the [**GamepadReading**](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.GamepadReading) struct, allowing us to check what buttons have been clicked or thumbsticks moved.</span></span>


<span data-ttu-id="aba84-298">Wenn der Zustand des Spiels **WaitForInput** ist, warten wir auf die Ein-/Aus-Menütaste des Controllers, damit das Spiel fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="aba84-298">If the state of the game is **WaitForInput**, we only listen for the Start/Menu button of the controller so that the game can be resumed.</span></span>


<span data-ttu-id="aba84-299">Ist es **aktiv**, überprüfen wir die Eingabe des Benutzers und bestimmen, welche Aktion im Spiel erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="aba84-299">If it's **Active**, we check the user's input and determine what in-game action needs to happen.</span></span>
<span data-ttu-id="aba84-300">Wenn der Benutzer den linken Joystick in eine bestimmte Richtung verschiebt, weiß das Spiel z.B., dass wir den Spieler in die Richtung zu verschieben müssen, in die der Stick verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-300">For instance, if the user moved the left analog stick in a specific direction, this lets the game know we need to move the player in the direction the stick is being moved.</span></span> <span data-ttu-id="aba84-301">Die Bewegung des Sticks in eine Richtung muss aber größer sein als der Radius des **inaktiven Bereichs**. Andernfalls passiert nichts.</span><span class="sxs-lookup"><span data-stu-id="aba84-301">The movement of the stick in a specific direction must register as larger than the radius of the **dead zone**; otherwise, nothing will happen.</span></span> <span data-ttu-id="aba84-302">Dieser Radius des inaktiven Bereichs ist erforderlich, um "Drifting" zu vermeiden, d.h. vom Controller erkannte winzige Bewegungen des Daumens, wenn dieser auf dem Stick liegt.</span><span class="sxs-lookup"><span data-stu-id="aba84-302">This dead zone radius is necessary to prevent "drifting," which is when the controller picks up small movements from the player's thumb as it rests on the stick.</span></span> <span data-ttu-id="aba84-303">Ohne inaktive Zonen können die Steuerelemente für den Benutzer zu sensibel sein.</span><span class="sxs-lookup"><span data-stu-id="aba84-303">Without dead zones, the controls can appear too sensitive to the user.</span></span>


<span data-ttu-id="aba84-304">Ministick-Eingabe ist zwischen-1 und 1 für die x- und y-Achse.</span><span class="sxs-lookup"><span data-stu-id="aba84-304">Thumbstick input is between -1 and 1 for both the x and y axis.</span></span> <span data-ttu-id="aba84-305">Die folgenden Konstanten geben den Radius des inaktiven Ministicks an.</span><span class="sxs-lookup"><span data-stu-id="aba84-305">The following consant specifies the radius of the thumbstick dead zone.</span></span>

```cpp
#define THUMBSTICK_DEADZONE 0.25f
```

<span data-ttu-id="aba84-306">Mit dem Verwenden dieser Variable werden wir dann mit der Verarbeitung der Eingaben des relevanten Ministicks beginnen.</span><span class="sxs-lookup"><span data-stu-id="aba84-306">Using this variable, we'll then begin processing actionable thumbstick input.</span></span> <span data-ttu-id="aba84-307">Die Bewegung tritt bei einem Wert von [-1, 0,26] oder [0,26, 1] auf jeder Achse auf.</span><span class="sxs-lookup"><span data-stu-id="aba84-307">Movement would occur with a value from [-1, -.26] or [.26, 1] on either axis.</span></span>

![Inaktive Zonen für Ministicks](images/simple-dx-game-controls-deadzone.png)

<span data-ttu-id="aba84-309">Dieser Teil der **UpdatePollingDevices**-Methode behandelt den linken und rechten Ministick.</span><span class="sxs-lookup"><span data-stu-id="aba84-309">This piece of the **UpdatePollingDevices** method handles the left and right thumbsticks.</span></span>
<span data-ttu-id="aba84-310">Jede X- und Y-Wert des Sticks wird überprüft, um festzustellen, ob er außerhalb des inaktiven Bereichs ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-310">Each stick's X and Y values are checked to see if they are outside of the dead zone.</span></span> <span data-ttu-id="aba84-311">Wenn einer oder beide inaktiv sind, aktualisieren wir die entsprechende Komponente.</span><span class="sxs-lookup"><span data-stu-id="aba84-311">If one or both are, we'll update the corresponding component.</span></span>
<span data-ttu-id="aba84-312">Wenn beispielsweise der linke Ministick nach links entlang der x-Achse verschoben wird, wird -1 der **x**-Komponente des **m_moveCommand**-Vektors hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="aba84-312">For example, if the left thumbstick is being moved left along the X axis, we'll add -1 to the **x** component of the **m_moveCommand** vector.</span></span> <span data-ttu-id="aba84-313">Dieser Vektor wird verwendet, um alle Eingänge auf allen Geräten zu aggregieren und wird später verwendet, um zu berechnen, wo der Spieler sich hin bewegen soll.</span><span class="sxs-lookup"><span data-stu-id="aba84-313">This vector is what will be used to aggregate all movements across all devices and will later be used to calculate where the player should move.</span></span> 


```cpp
        // Use the left thumbstick to control the eye point position (position of the player)

        // Check if left thumbstick is outside of dead zone on x axis
        if (reading.LeftThumbstickX > THUMBSTICK_DEADZONE ||
            reading.LeftThumbstickX < -THUMBSTICK_DEADZONE)
        {
            // Get value of left thumbstick's position on x axis
            float x = static_cast<float>(reading.LeftThumbstickX);
            // Set the x of the move vector to 1 if the stick is being moved right.
            // Set to -1 if moved left. 
            m_moveCommand.x -= (x > 0) ? 1 : -1;
        }

        // Check if left thumbstick is outside of dead zone on y axis
        if (reading.LeftThumbstickY > THUMBSTICK_DEADZONE ||
            reading.LeftThumbstickY < -THUMBSTICK_DEADZONE)
        {
            // Get value of left thumbstick's position on y axis
            float y = static_cast<float>(reading.LeftThumbstickY);
            // Set the y of the move vector to 1 if the stick is being moved forward.
            // Set to -1 if moved backwards. 
            m_moveCommand.y += (y > 0) ? 1 : -1;
        }

```

<span data-ttu-id="aba84-314">Ähnlich wie der linke Stick, der die Bewegung kontrolliert, steuert der rechte Stick die Drehung der Kamera.</span><span class="sxs-lookup"><span data-stu-id="aba84-314">Similar to how the left stick controls movement, the right stick controls the rotation of the camera.</span></span>


<span data-ttu-id="aba84-315">Das Verhalten des rechten Sticks wird dem Verhalten der Mausbewegung im Steuerelement-Setup von Maus und Tastatur ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="aba84-315">The right thumb stick behavior aligns with the behavior of mouse movement in our mouse and keyboard control setup.</span></span>
<span data-ttu-id="aba84-316">Wenn der Stick außerhalb des inaktiven Bereichs ist, berechnen wir die Differenz zwischen der aktuellen Zeigerposition und der Blickposition des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="aba84-316">If the stick is outside of the dead zone, we calculate the difference between the current pointer position and where the user is now trying to look.</span></span>
<span data-ttu-id="aba84-317">Diese Änderung der Zeigerposition (**PointerDelta**) wird zum Upgrade des Neigungs- und Schwenkwinkels der Kameradrehung verwendet, die zu einem späteren Zeitpunkt auf die **aktualisierte** Methode angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-317">This change in pointer position (**pointerDelta**) is then used to update the pitch and yaw of the camera rotation that later get applied in our **Update** method.</span></span>
<span data-ttu-id="aba84-318">Der **PointerDelta**-Vektor sieht vertraut aus, da er auch in der [MoveLookController::OnPointerMoved](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L318-L395)-Methode zum Nachverfolgen verwendet wird, um Änderung der Zeigerposition für unsere Maus und Toucheingaben nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="aba84-318">The **pointerDelta** vector may look familiar because it's also used in the [MoveLookController::OnPointerMoved](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L318-L395) method to keep track of change in pointer position for our mouse and touch inputs.</span></span>


```cpp
        // Use the right thumbstick to control the look at position

        XMFLOAT2 pointerDelta;

        // Check if right thumbstick is outside of deadzone on x axis
        if (reading.RightThumbstickX > THUMBSTICK_DEADZONE ||
            reading.RightThumbstickX < -THUMBSTICK_DEADZONE)
        {
            float x = static_cast<float>(reading.RightThumbstickX);
            // Register the change in the pointer along the x axis
            pointerDelta.x = x * x * x; 
        }
        // No actionable thumbstick movement. Register no change in pointer.
        else
        {
            pointerDelta.x = 0.0f;
        }
        // Check if right thumbstick is outside of deadzone on y axis
        if (reading.RightThumbstickY > THUMBSTICK_DEADZONE ||
            reading.RightThumbstickY < -THUMBSTICK_DEADZONE)
        {
            float y = static_cast<float>(reading.RightThumbstickY);
            // Register the change in the pointer along the y axis
            pointerDelta.y = y * y * y;
        }
        else
        {
            pointerDelta.y = 0.0f;
        }

        XMFLOAT2 rotationDelta;
        rotationDelta.x = pointerDelta.x *  0.08f;       // Scale for control sensitivity.
        rotationDelta.y = pointerDelta.y *  0.08f;

        // Update our orientation based on the command.
        m_pitch += rotationDelta.y;
        m_yaw += rotationDelta.x;

        // Limit pitch to straight up or straight down.
        m_pitch = __max(-XM_PI / 2.0f, m_pitch);
        m_pitch = __min(+XM_PI / 2.0f, m_pitch);
```

<span data-ttu-id="aba84-319">Das Steuerelemente des Spiels wären nicht ohne die Möglichkeit zu Schießen abgeschlossen!</span><span class="sxs-lookup"><span data-stu-id="aba84-319">The game's controls wouldn't be complete without the ability to fire spheres!</span></span>


<span data-ttu-id="aba84-320">Diese **UpdatePollingDevices**-Methode überprüft auch, ob der rechte Trigger gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="aba84-320">This **UpdatePollingDevices** method also checks if the right trigger is being pressed.</span></span> <span data-ttu-id="aba84-321">Wenn dies der Fall ist, wird unsere **m_firePressed**-Eigenschaft auf "Wahr" festgelegt, um dem Spiel anzuzeigen, dass Kugeln ausgelöst werden sollen.</span><span class="sxs-lookup"><span data-stu-id="aba84-321">If it is, our **m_firePressed** property is flipped to true, signaling to the game that spheres should start firing.</span></span>
```cpp
    if (reading.RightTrigger > TRIGGER_DEADZONE)
    {
        if (!m_autoFire && !m_gamepadTriggerInUse)
        {
            m_firePressed = true;
        }

        m_gamepadTriggerInUse = true;
    }
    else
    {
        m_gamepadTriggerInUse = false;
    }
```


## <a name="the-update-method"></a><span data-ttu-id="aba84-322">Die Update-Methode</span><span class="sxs-lookup"><span data-stu-id="aba84-322">The Update method</span></span>

<span data-ttu-id="aba84-323">Zum Abschluss befassen wir uns tiefer mit der [**Update**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1005-L1096)-Methode.</span><span class="sxs-lookup"><span data-stu-id="aba84-323">To wrap things up, let's dig deeper into the [**Update**](https://github.com/Microsoft/Windows-universal-samples/blob/ef073ed8a2007d113af1d88eddace479e3bf0e07/SharedContent/cpp/GameContent/MoveLookController.cpp#L1005-L1096) method.</span></span>
<span data-ttu-id="aba84-324">Diese Methode führt alle Bewegungen oder Drehungen aus, die der Spieler bei allen unterstützten Eingaben ausführt, um den Geschwindigkeitsvektor zu generieren und unsere Schusshöhe zu aktualisieren, und Werte für den Zugriff auf die Spielschleife vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="aba84-324">This method merges any movements or rotations that the player made with any supported input to generate a velocity vector and update our pitch and yaw values for our game loop to access.</span></span>


<span data-ttu-id="aba84-325">Die **Update**-Methode startet Elemente durch Aufrufen von [**UpdatePollingDevices**](#the-updatepollingdevices-method), um den Status des Controllers zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="aba84-325">The **Update** method kicks things off by calling [**UpdatePollingDevices**](#the-updatepollingdevices-method) to update the state of the controller.</span></span> <span data-ttu-id="aba84-326">Diese Methode sammelt auch alle Eingaben von einem Gamepad und fügt die Bewegungen dem **m_moveCommand**-Vektor hinzu.</span><span class="sxs-lookup"><span data-stu-id="aba84-326">This method also gathers any input from a gamepad and adds its movements to the **m_moveCommand** vector.</span></span> 

<span data-ttu-id="aba84-327">In unserer **Update**-Methode überprüfen wir dann die folgende Eingabe.</span><span class="sxs-lookup"><span data-stu-id="aba84-327">In our **Update** method we then perform the following input checks.</span></span>
- <span data-ttu-id="aba84-328">Wenn der Spieler das Bewegungsrechteck des Controllers verwendet, wird die Änderung der Zeigerposition ermittelt und wir verwenden diese, um zu berechnen, ob der Benutzer den Mauszeiger aus dem inaktiven Bereich des Controller entfernt hat.</span><span class="sxs-lookup"><span data-stu-id="aba84-328">If the player is using the move controller rectangle, we'll then determine the change in pointer position and use that to calculate if the user has moved the pointer out of the controller's dead zone.</span></span> <span data-ttu-id="aba84-329">Wenn sich der Mauszeiger außerhalb des inaktiven Bereichs befindet, wird die **m_moveCommand**-Vektoreigenschaft mit dem virtuellen Joystick-Wert aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="aba84-329">If outside of the dead zone, the **m_moveCommand** vector property is then updated with the virtual joystick value.</span></span>
- <span data-ttu-id="aba84-330">Wenn eine der Bewegungstastatureingaben gedrückt werden, wird ein Wert von `1.0f`oder `-1.0f` der entsprechenden Komponente des **m_moveCommand**-Vektors &mdash; hinzugefügt, `1.0f` für Vorwärts, und `-1.0f` für Rückwärts.</span><span class="sxs-lookup"><span data-stu-id="aba84-330">If any of the movement keyboard inputs are pressed, a value of `1.0f` or `-1.0f` are added in the corresponding component of the **m_moveCommand** vector &mdash; `1.0f` for forward, and `-1.0f` for backward.</span></span>


<span data-ttu-id="aba84-331">Nachdem alle Bewegungseingaben berücksichtigt wurden, führen wird den **m_moveCommand**-Vektor über einige Berechnungen aus, um einen neuen Vektor zu generieren, der die Richtung des Spielers in der Spielwelt darstellt.</span><span class="sxs-lookup"><span data-stu-id="aba84-331">Once all movement input has been taken into account, we then run the **m_moveCommand** vector through some calculations to generate a new vector that represents the direction of the player with regards to the game world.</span></span>
<span data-ttu-id="aba84-332">Wir berechnen unsere Bewegungen in Bezug auf die ganze Welt und wenden sie auf den Spieler als Geschwindigkeit in die entsprechende Richtung an.</span><span class="sxs-lookup"><span data-stu-id="aba84-332">We then take our movements in relation to the world and apply them to the player as velocity in that direction.</span></span>
<span data-ttu-id="aba84-333">Schließlich setzen wir den **m_moveCommand**-Vektor auf `(0.0f, 0.0f, 0.0f)` zurück, damit alles für den nächsten Frame des Spiels bereit ist.</span><span class="sxs-lookup"><span data-stu-id="aba84-333">Finally we reset the **m_moveCommand** vector to `(0.0f, 0.0f, 0.0f)` so that everything is ready for the next game frame.</span></span>


```cpp
void MoveLookController::Update()
{
    // Get any gamepad input and update state
    UpdatePollingDevices();

    // Get change in 
    if (m_moveInUse)
    {
        XMFLOAT2 pointerDelta;

        pointerDelta.x = m_movePointerPosition.x - m_moveFirstDown.x;
        pointerDelta.y = m_movePointerPosition.y - m_moveFirstDown.y;

        // Figure out the command from the virtual joystick.
        XMFLOAT3 commandDirection = XMFLOAT3(0.0f, 0.0f, 0.0f);
        if (fabsf(pointerDelta.x) > 16.0f)         // Leave 32 pixel-wide dead spot for being still.
            m_moveCommand.x -= pointerDelta.x/fabsf(pointerDelta.x);

        if (fabsf(pointerDelta.y) > 16.0f)
            m_moveCommand.y -= pointerDelta.y/fabsf(pointerDelta.y);
    }

    // Poll our state bits set by the keyboard input events.
    if (m_forward)
    {
        m_moveCommand.y += 1.0f;
    }
    if (m_back)
    {
        m_moveCommand.y -= 1.0f;
    }
    if (m_left)
    {
        m_moveCommand.x += 1.0f;
    }
    if (m_right)
    {
        m_moveCommand.x -= 1.0f;
    }
    if (m_up)
    {
        m_moveCommand.z += 1.0f;
    }
    if (m_down)
    {
        m_moveCommand.z -= 1.0f;
    }

    // Make sure that 45deg cases are not faster.
    if (fabsf(m_moveCommand.x) > 0.1f ||
        fabsf(m_moveCommand.y) > 0.1f ||
        fabsf(m_moveCommand.z) > 0.1f)
    {
        XMStoreFloat3(&m_moveCommand, XMVector3Normalize(XMLoadFloat3(&m_moveCommand)));
    }

    // Rotate command to align with our direction (world coordinates).
    XMFLOAT3 wCommand;
    wCommand.x =  m_moveCommand.x * cosf(m_yaw) - m_moveCommand.y * sinf(m_yaw);
    wCommand.y =  m_moveCommand.x * sinf(m_yaw) + m_moveCommand.y * cosf(m_yaw);
    wCommand.z =  m_moveCommand.z;

    // Scale for sensitivity adjustment.
    // Our velocity is based on the command. Y is up.
    m_velocity.x = -wCommand.x * MoveLookConstants::MovementGain;
    m_velocity.z =  wCommand.y * MoveLookConstants::MovementGain;
    m_velocity.y =  wCommand.z * MoveLookConstants::MovementGain;

    // Clear movement input accumulator for use during next frame.
    m_moveCommand = XMFLOAT3(0.0f, 0.0f, 0.0f);
}
```


## <a name="next-steps"></a><span data-ttu-id="aba84-334">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="aba84-334">Next steps</span></span>

<span data-ttu-id="aba84-335">Nachdem wir unsere Steuerelemente hinzugefügt haben, gibt es eine weitere Funktion, die wir hinzufügen müssen, um ein immersives Spiel zu erstellen: Sound!</span><span class="sxs-lookup"><span data-stu-id="aba84-335">Now that we have added our controls, there's another feature we need to add to create an immersive game: sound!</span></span>
<span data-ttu-id="aba84-336">Musik und Soundeffekte sind bei jedem Spiel wichtig. Befassen wir uns also mit dem [Hinzufügen von Sound](tutorial--adding-sound.md).</span><span class="sxs-lookup"><span data-stu-id="aba84-336">Music and sound effects are important to any game, so let's discuss [adding sound](tutorial--adding-sound.md) next.</span></span>
 

 

 




