---
author: eliotcowley
title: Eingabemethoden für Spiele
description: Erfahren Sie mehr über Muster und Verfahren zur effizienten Verwendung von Eingabegeräten.
ms.assetid: CBAD3345-3333-4924-B6D8-705279F52676
ms.author: elcowle
ms.date: 11/20/2017
ms.topic: article
keywords: Windows 10, UWP, Spiele, Eingabe
ms.localizationpriority: medium
ms.openlocfilehash: ed0d611c761315e42decb89e1a5a5ad84f4b067a
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5872917"
---
# <a name="input-practices-for-games"></a><span data-ttu-id="69d99-104">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="69d99-104">Input practices for games</span></span>

<span data-ttu-id="69d99-105">Auf dieser Seite werden Muster und Verfahren zur effizienten Verwendung von Eingabegeräten in Spielen für die universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="69d99-105">This page describes patterns and techniques for effectively using input devices in Universal Windows Platform (UWP) games.</span></span>

<span data-ttu-id="69d99-106">Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:</span><span class="sxs-lookup"><span data-stu-id="69d99-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="69d99-107">Nachverfolgen von Spielern und den von ihnen aktuell verwendeten Eingabe- und Navigationsgeräten</span><span class="sxs-lookup"><span data-stu-id="69d99-107">how to track players and which input and navigation devices they're currently using</span></span>
* <span data-ttu-id="69d99-108">Erkennen von Tastenübergängen (von „Gedrückt“ zu „Losgelassen“ oder von „Losgelassen“ zu „Gedrückt“)</span><span class="sxs-lookup"><span data-stu-id="69d99-108">how to detect button transitions (pressed-to-released, released-to-pressed)</span></span>
* <span data-ttu-id="69d99-109">Erkennen komplexer Tastenanordnungen mit einem einzelnen Test</span><span class="sxs-lookup"><span data-stu-id="69d99-109">how to detect complex button arrangements with a single test</span></span>

## <a name="choosing-an-input-device-class"></a><span data-ttu-id="69d99-110">Auswählen einer Eingabegeräteklasse</span><span class="sxs-lookup"><span data-stu-id="69d99-110">Choosing an input device class</span></span>

<span data-ttu-id="69d99-111">Es sind viele verschiedene Arten von Eingabe-APIs verfügbar, z.B. [ArcadeStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick), und [Gamepad](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad).</span><span class="sxs-lookup"><span data-stu-id="69d99-111">There are many different types of input APIs available to you, such as [ArcadeStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick), and [Gamepad](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad).</span></span> <span data-ttu-id="69d99-112">Wie entscheiden Sie, welche API Sie für Ihr Spiel verwenden?</span><span class="sxs-lookup"><span data-stu-id="69d99-112">How do you decide which API to use for your game?</span></span>

<span data-ttu-id="69d99-113">Sie sollten die API wählen, die für Ihr Spiel die am besten geeigneten Eingaben bietet.</span><span class="sxs-lookup"><span data-stu-id="69d99-113">You should choose whichever API gives you the most appropriate input for your game.</span></span> <span data-ttu-id="69d99-114">Wenn Sie z. B. Spiele für 2D-Plattformen entwickeln, können Sie wahrscheinlich nur die **Gamepad**-Klasse verwenden, ohne die zusätzlichen Funktionalitäten anderer Klassen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="69d99-114">For example, if you're making a 2D platform game, you can probably just use the **Gamepad** class and not bother with the extra functionality available via other classes.</span></span> <span data-ttu-id="69d99-115">Das Spiel wäre damit auf die Unterstützung von Gamepads beschränkt; seine einheitliche Oberfläche würde aber mit vielen Gamepads funktionieren, ohne weiteren Code zu benötigen.</span><span class="sxs-lookup"><span data-stu-id="69d99-115">This would restrict the game to supporting gamepads only and provide a consistent interface that will work across many different gamepads with no need for additional code.</span></span>

<span data-ttu-id="69d99-116">Andererseits sollten Sie für komplexe Flug- und Renn-Simulationen alle [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller)-Objekte als Grundlage auflisten, um auch weniger bekannte Geräte zu unterstützen, die manche Spieler noch vereinzelt verwenden, z.B. separate Pedale, Drosselklappen usw.</span><span class="sxs-lookup"><span data-stu-id="69d99-116">On the other hand, for complex flight and racing simulations, you might want to enumerate all of the [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) objects as a baseline to make sure they support any niche device that enthusiast players might have, including devices such as separate pedals or throttle that are still used by a single player.</span></span> 

<span data-ttu-id="69d99-117">Anschließend können Sie mithilfe einer Eingabeklasse-Methode wie **FromGameController** bzw. [Gamepad.FromGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.fromgamecontroller) feststellen, ob aktuelle Ansichten für das Gerät verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="69d99-117">From there, you can use an input class's **FromGameController** method, such as [Gamepad.FromGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.fromgamecontroller), to see if each device has a more curated view.</span></span> <span data-ttu-id="69d99-118">Wenn das Gerät z. B. auch ein **Gamepad** ist, können Sie die Schaltflächenzuordnungen der Benutzeroberfläche entsprechend anpassen, um die Standardtasten sinnvoller zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="69d99-118">For example, if the device is also a **Gamepad**, then you might want to adjust the button mapping UI to reflect that, and provide some sensible default button mappings to choose from.</span></span> <span data-ttu-id="69d99-119">(Wenn Sie im Gegensatz dazu nur **RawGameController** verwenden, muss der Spieler seine Gamepad-Eingaben manuell konfigurieren.)</span><span class="sxs-lookup"><span data-stu-id="69d99-119">(This is in contrast to requiring the player to manually configure the gamepad inputs if you're only using **RawGameController**.)</span></span> 

<span data-ttu-id="69d99-120">Alternativ können Sie auch die Anbieter-ID (VID) und Produkt-ID (PID) des **RawGameController** vergleichen (jeweils durch [HardwareVendorId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareVendorId) und [HardwareProductId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareProductId)), um vorgeschlagene Tastenzuordnungen für bekannte Geräte anzubieten, die trotzdem kompatibel sind mit unbekannten Geräten, die aus manuellen Zuordnungen von Spielern stammen.</span><span class="sxs-lookup"><span data-stu-id="69d99-120">Alternatively, you can look at the vendor ID (VID) and product ID (PID) of a **RawGameController** (using [HardwareVendorId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareVendorId) and [HardwareProductId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareProductId), respectively) and provide suggested button mappings for popular devices while still remaining compatible with unknown devices that come out in the future via manual mappings by the player.</span></span>

## <a name="keeping-track-of-connected-controllers"></a><span data-ttu-id="69d99-121">Nachverfolgen von angeschlossenen Controllern</span><span class="sxs-lookup"><span data-stu-id="69d99-121">Keeping track of connected controllers</span></span>

<span data-ttu-id="69d99-122">Während jeder Controllertyp eine Liste der verbundenen Domänencontroller enthält (z.B. [Gamepad.Gamepads](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.Gamepads)), empfiehlt es sich, Ihre eigene Liste von Domänencontrollern zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="69d99-122">While each controller type includes a list of connected controllers (such as [Gamepad.Gamepads](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepad.Gamepads)), it is a good idea to maintain your own list of controllers.</span></span> <span data-ttu-id="69d99-123">Weitere Informationen finden Sie unter [die Gamepadliste](gamepad-and-vibration.md#the-gamepads-list) (jeder Controllertyp hat einen ähnlichen Namensabschnittfür sein eigenes Thema).</span><span class="sxs-lookup"><span data-stu-id="69d99-123">See [The gamepads list](gamepad-and-vibration.md#the-gamepads-list) for more information (each controller type has a similarly named section on its own topic).</span></span>

<span data-ttu-id="69d99-124">Was geschieht jedoch, wenn der Spieler den Controller trennt oder einen neuen installiert?</span><span class="sxs-lookup"><span data-stu-id="69d99-124">However, what happens when the player unplugs their controller, or plugs in a new one?</span></span> <span data-ttu-id="69d99-125">Sie müssen diese Ereignisse behandeln, und die Liste entsprechend zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="69d99-125">You need to handle these events, and update your list accordingly.</span></span> <span data-ttu-id="69d99-126">Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Gamepads](gamepad-and-vibration.md#adding-and-removing-gamepads) (jeder Controllertyp hat einen ähnlichen Namensabschnittfür sein eigenes Thema).</span><span class="sxs-lookup"><span data-stu-id="69d99-126">See [Adding and removing gamepads](gamepad-and-vibration.md#adding-and-removing-gamepads) for more information (again, each controller type has a similarly named section on its own topic).</span></span>

<span data-ttu-id="69d99-127">Da die hinzugefügten und entfernten Ereignisse asynchron ausgelöst werden, könnten Sie beim Umgang mit der Liste der Domänencontroller falsche Ergebnisse erhalten.</span><span class="sxs-lookup"><span data-stu-id="69d99-127">Because the added and removed events are raised asynchronously, you could get incorrect results when dealing with your list of controllers.</span></span> <span data-ttu-id="69d99-128">Wenn Sie daher auf die Liste der Domänencontroller zugreifen, sperren Sie diese, damit nur ein Thread zu jedem Zeitpunkt darauf zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="69d99-128">Therefore, anytime you access your list of controllers, you should put a lock around it so that only one thread can access it at a time.</span></span> <span data-ttu-id="69d99-129">Dies kann mit [Concurrency Runtime](https://docs.microsoft.com/cpp/parallel/concrt/concurrency-runtime) geschehen, insbesondere der [Critical_section-Klasse](https://docs.microsoft.com/cpp/parallel/concrt/reference/critical-section-class)im **&lt;ppl.h&gt;**.</span><span class="sxs-lookup"><span data-stu-id="69d99-129">This can be done with the [Concurrency Runtime](https://docs.microsoft.com/cpp/parallel/concrt/concurrency-runtime), specifically the [critical_section class](https://docs.microsoft.com/cpp/parallel/concrt/reference/critical-section-class), in **&lt;ppl.h&gt;**.</span></span>

<span data-ttu-id="69d99-130">Die Liste der angeschlossenen Controller ist anfänglich leer, und dauert ein oder zwei Sekunden zum Auffüllen.</span><span class="sxs-lookup"><span data-stu-id="69d99-130">Another thing to think about is that the list of connected controllers will initially be empty, and takes a second or two to populate.</span></span> <span data-ttu-id="69d99-131">Wenn Sie daher nur den aktuellen Gamepad der Startmethode zuweisen, ist dieser **null**!</span><span class="sxs-lookup"><span data-stu-id="69d99-131">So if you only assign the current gamepad in the start method, it will be **null**!</span></span>

<span data-ttu-id="69d99-132">Um dieses Problem zu beheben, müssen Sie eine Methode durchführen, die den wichtigsten Gamepad "aktualisiert" (in einem Spiel mit Einzelspieler; Multiplayer-Spiele erfordern anspruchsvollere Lösungen).</span><span class="sxs-lookup"><span data-stu-id="69d99-132">To rectify this, you should have a method that "refreshes" the main gamepad (in a single-player game; multiplayer games will require more sophisticated solutions).</span></span> <span data-ttu-id="69d99-133">Sie sollten diese Methode von beiden Controller-Ereignishandlern aufrufen, dem hinzugefügten und dem entfernten Controller oder in der Update-Methode.</span><span class="sxs-lookup"><span data-stu-id="69d99-133">You should then call this method in both your controller added and controller removed event handlers, or in your update method.</span></span>

<span data-ttu-id="69d99-134">Die folgende Methode gibt den ersten Gamepad der Liste zurück (oder **nullptr**, wenn die Liste leer ist).</span><span class="sxs-lookup"><span data-stu-id="69d99-134">The following method simply returns the first gamepad in the list (or **nullptr** if the list is empty).</span></span> <span data-ttu-id="69d99-135">Denken Sie daran, **nullptr** jedes Mal zu überprüfen, wenn Sie mit dem Controller eine Aktion durchführen.</span><span class="sxs-lookup"><span data-stu-id="69d99-135">Then you just need to remember to check for **nullptr** anytime you do anything with the controller.</span></span> <span data-ttu-id="69d99-136">Es liegt an Ihnen, ob Sie Spiele blockieren, wenn es kein Domänencontroller verbunden ist (z.B. durch das Anhalten des Spiels) oder einfach Spiele weiter spielen und die Eingabe ignorieren.</span><span class="sxs-lookup"><span data-stu-id="69d99-136">It's up to you whether you want to block gameplay when there's no controller connected (for example, by pausing the game) or simply have gameplay continue, while ignoring input.</span></span>

```cpp
#include <ppl.h>

using namespace Platform::Collections;
using namespace Windows::Gaming::Input;
using namespace concurrency;

Vector<Gamepad^>^ m_myGamepads = ref new Vector<Gamepad^>();

Gamepad^ GetFirstGamepad()
{
    Gamepad^ gamepad = nullptr;
    critical_section::scoped_lock{ m_lock };

    if (m_myGamepads->Size > 0)
    {
        gamepad = m_myGamepads->GetAt(0);
    }

    return gamepad;
}
```

<span data-ttu-id="69d99-137">Hier ein Beispiel zum Behandeln von Eingaben von einem Gamepad:</span><span class="sxs-lookup"><span data-stu-id="69d99-137">Putting it all together, here is an example of how to handle input from a gamepad:</span></span>

```cpp
#include <algorithm>
#include <ppl.h>

using namespace Platform::Collections;
using namespace Windows::Foundation;
using namespace Windows::Gaming::Input;
using namespace concurrency;

static Vector<Gamepad^>^ m_myGamepads = ref new Vector<Gamepad^>();
static Gamepad^          m_gamepad = nullptr;
static critical_section  m_lock{};

void Start()
{
    // Register for gamepad added and removed events.
    Gamepad::GamepadAdded += ref new EventHandler<Gamepad^>(&OnGamepadAdded);
    Gamepad::GamepadRemoved += ref new EventHandler<Gamepad^>(&OnGamepadRemoved);

    // Add connected gamepads to m_myGamepads.
    for (auto gamepad : Gamepad::Gamepads)
    {
        OnGamepadAdded(nullptr, gamepad);
    }
}

void Update()
{
    // Update the current gamepad if necessary.
    if (m_gamepad == nullptr)
    {
        auto gamepad = GetFirstGamepad();

        if (m_gamepad != gamepad)
        {
            m_gamepad = gamepad;
        }
    }

    if (m_gamepad != nullptr)
    {
        // Gather gamepad reading.
    }
}

// Get the first gamepad in the list.
Gamepad^ GetFirstGamepad()
{
    Gamepad^ gamepad = nullptr;
    critical_section::scoped_lock{ m_lock };

    if (m_myGamepads->Size > 0)
    {
        gamepad = m_myGamepads->GetAt(0);
    }

    return gamepad;
}

void OnGamepadAdded(Platform::Object^ sender, Gamepad^ args)
{
    // Check if the just-added gamepad is already in m_myGamepads; if it isn't, 
    // add it.
    critical_section::scoped_lock lock{ m_lock };
    auto it = std::find(begin(m_myGamepads), end(m_myGamepads), args);

    if (it == end(m_myGamepads))
    {
        m_myGamepads->Append(args);
    }
}

void OnGamepadRemoved(Platform::Object^ sender, Gamepad^ args)
{
    // Remove the gamepad that was just disconnected from m_myGamepads.
    unsigned int indexRemoved;
    critical_section::scoped_lock lock{ m_lock };

    if (m_myGamepads->IndexOf(args, &indexRemoved))
    {
        if (m_gamepad == m_myGamepads->GetAt(indexRemoved))
        {
            m_gamepad = nullptr;
        }

        m_myGamepads->RemoveAt(indexRemoved);
    }
}
```

## <a name="tracking-users-and-their-devices"></a><span data-ttu-id="69d99-138">Nachverfolgen von Benutzern und Geräten</span><span class="sxs-lookup"><span data-stu-id="69d99-138">Tracking users and their devices</span></span>

<span data-ttu-id="69d99-139">Alle Eingabegeräte sind einem [Benutzer](https://docs.microsoft.com/uwp/api/windows.system.user) zugeordnet, damit seine Identität mit seinem Spiel, seinen Erfolgen, geänderten Einstellungen und anderen Aktivitäten verknüpft werden kann.</span><span class="sxs-lookup"><span data-stu-id="69d99-139">All input devices are associated with a [User](https://docs.microsoft.com/uwp/api/windows.system.user) so that their identity can be linked to their gameplay, achievements, settings changes, and other activities.</span></span> <span data-ttu-id="69d99-140">Da sich Benutzer nach Belieben an- und abmelden können, ist es normal, dass sich andere Benutzer auf einem mit dem System verbundenen Eingabegerät anmelden, nachdem sich ein vorheriger Benutzer abgemeldet hat. Wenn sich ein Benutzer an- oder abmeldet, wird das [IGameController.UserChanged](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller.UserChanged)-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="69d99-140">Users can sign in or sign out at will, and it's common for a different user to sign in on an input device that remains connected to the system after the previous user has signed out. When a user signs in or out, the [IGameController.UserChanged](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller.UserChanged) event is raised.</span></span> <span data-ttu-id="69d99-141">Sie können für diesen Fall einen Ereignishandler registrieren, um die Spieler und von ihnen verwendeten Geräte nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="69d99-141">You can register an event handler for this event to keep track of players and the devices they're using.</span></span>

<span data-ttu-id="69d99-142">Die Benutzeridentität dient auch dazu, Eingabegeräte einem [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="69d99-142">User identity is also the way that an input device is associated with its corresponding [UI navigation controller](ui-navigation-controller.md).</span></span>

<span data-ttu-id="69d99-143">Aus diesen Gründen sollten Spielereingaben mithilfe der [User](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller.User)-Eigenschaft der Geräteklasse (geerbt von der [IGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller)-Schnittstelle) nachverfolgt und korreliert werden.</span><span class="sxs-lookup"><span data-stu-id="69d99-143">For these reasons, player input should be tracked and correlated with the [User](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller.User) property of the device class (inherited from the [IGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller) interface).</span></span>

<span data-ttu-id="69d99-144">Das Beispiel [UserGamepadPairingUWP (GitHub)](
https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/UserGamepadPairingUWP) zeigt, wie Benutzer und von ihnen verwendete Geräte nachverfolgt werden können.</span><span class="sxs-lookup"><span data-stu-id="69d99-144">The [UserGamepadPairingUWP (GitHub)](
https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/UserGamepadPairingUWP) sample demonstrates how you can keep track of users and the devices they're using.</span></span>

## <a name="detecting-button-transitions"></a><span data-ttu-id="69d99-145">Erkennen von Tastenübergängen</span><span class="sxs-lookup"><span data-stu-id="69d99-145">Detecting button transitions</span></span>

<span data-ttu-id="69d99-146">In einigen Fällen möchten Sie wissen, wann eine Taste zuerst gedrückt oder losgelassen wird, also genau, wann der Zustand der Taste von „Losgelassen“ in „Gedrückt“ oder von „Gedrückt“ in „Losgelassen“ übergegangen ist.</span><span class="sxs-lookup"><span data-stu-id="69d99-146">Sometimes you want to know when a button is first pressed or released; that is, precisely when the button state transitions from released to pressed or from pressed to released.</span></span> <span data-ttu-id="69d99-147">Um dies zu ermitteln und herauszufinden, was sich geändert hat, müssen Sie den vorherigen Geräte-Ablesewert beibehalten und mit dem aktuellen Ablesewert vergleichen.</span><span class="sxs-lookup"><span data-stu-id="69d99-147">To determine this, you need to remember the previous device reading and compare the current reading against it to see what's changed.</span></span>

<span data-ttu-id="69d99-148">Das folgende Beispiel zeigt anhand eines Gamepads, wie zuvor erhaltene Werte beibehalten werden können; das gleiche Prinzip gilt ebenso für andere Eingabegerätetypen wie Arcade-Joysticks, Rennlenkräder usw.</span><span class="sxs-lookup"><span data-stu-id="69d99-148">The following example demonstrates a basic approach for remembering the previous reading; gamepads are shown here, but the principles are the same for arcade stick, racing wheel, and the other input device types.</span></span>

```cpp
Gamepad gamepad;
GamepadReading newReading();
GamepadReading oldReading();

// Called at the start of the game.
void Game::Start()
{
    gamepad = Gamepad::Gamepads[0];
}

// Game::Loop represents one iteration of a typical game loop
void Game::Loop()
{
    // move previous newReading into oldReading before getting next newReading
    oldReading = newReading, newReading = gamepad.GetCurrentReading();

    // process device readings using buttonJustPressed/buttonJustReleased (see below)
}
```

<span data-ttu-id="69d99-149">Als Erstes verschiebt `Game::Loop` den vorhandenen Wert von `newReading` (den Gamepad-Ablesewert aus der vorherigen Schleifeniteration) in `oldReading` und fügt dann einen neuen Gamepad-Ablesewert für die aktuelle Iteration in `newReading` ein.</span><span class="sxs-lookup"><span data-stu-id="69d99-149">Before doing anything else, `Game::Loop` moves the existing value of `newReading` (the gamepad reading from the previous loop iteration) into `oldReading`, then fills `newReading` with a fresh gamepad reading for the current iteration.</span></span> <span data-ttu-id="69d99-150">Mithilfe dieser Informationen können Sie den Übergang von Tasten erkennen.</span><span class="sxs-lookup"><span data-stu-id="69d99-150">This gives you the information you need to detect button transitions.</span></span>

<span data-ttu-id="69d99-151">Das folgende Beispiel zeigt eine einfache Möglichkeit, um Tastenzustandswechsel zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="69d99-151">The following example demonstrates a basic approach for detecting button transitions:</span></span>

```cpp
bool ButtonJustPressed(const GamepadButtons selection)
{
    bool newSelectionPressed = (selection == (newReading.Buttons & selection));
    bool oldSelectionPressed = (selection == (oldReading.Buttons & selection));

    return newSelectionPressed && !oldSelectionPressed;
}

bool ButtonJustReleased(GamepadButtons selection)
{
    bool newSelectionReleased =
        (GamepadButtons.None == (newReading.Buttons & selection));

    bool oldSelectionReleased =
        (GamepadButtons.None == (oldReading.Buttons & selection));

    return newSelectionReleased && !oldSelectionReleased;
}
```

<span data-ttu-id="69d99-152">Diese beiden Funktionen leiten zuerst den booleschen Zustand der Tastenauswahl von `newReading` und `oldReading` ab und stellen dann durch boolesche Logik fest, ob der Übergang in den Zielzustand erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="69d99-152">These two functions first derive the Boolean state of the button selection from `newReading` and `oldReading`, then perform Boolean logic to determine whether the target transition has occurred.</span></span> <span data-ttu-id="69d99-153">Diese Funktionen geben nur **true** zurück, wenn der neue Ablesewert den Zielzustand enthält („Gedrückt“ bzw. „Losgelassen“) *und* der alte Ablesewert nicht auch den Zielzustand enthält. Andernfalls geben sie **false** zurück.</span><span class="sxs-lookup"><span data-stu-id="69d99-153">These functions return **true** only if the new reading contains the target state (pressed or released, respectively) *and* the old reading does not also contain the target state; otherwise, they return **false**.</span></span>

## <a name="detecting-complex-button-arrangements"></a><span data-ttu-id="69d99-154">Erkennen komplexer Tastenanordnungen</span><span class="sxs-lookup"><span data-stu-id="69d99-154">Detecting complex button arrangements</span></span>

<span data-ttu-id="69d99-155">Jede Taste eines Eingabegeräts liefert einen digitalen Wert, der angibt, ob sie im gedrückten Zustand (unten) oder losgelassenen Zustand (oben) ist.</span><span class="sxs-lookup"><span data-stu-id="69d99-155">Each button of an input device provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="69d99-156">Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte dargestellt, sondern in Bitfeldern zusammengefasst, die durch gerätespezifische Enumerationen wie [GamepadButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadbuttons) dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="69d99-156">For efficiency, button readings aren't represented as individual boolean values; instead, they're all packed into bitfields represented by device-specific enumerations such as [GamepadButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadbuttons).</span></span> <span data-ttu-id="69d99-157">Zum Ablesen bestimmter Tasten wird eine bitweise Maskierung verwendet, um die relevanten Werte zu isolieren.</span><span class="sxs-lookup"><span data-stu-id="69d99-157">To read specific buttons, bitwise masking is used to isolate the values that you're interested in.</span></span> <span data-ttu-id="69d99-158">Eine Taste ist gedrückt (unten), wenn ihr Bit entsprechend festgelegt ist, andernfalls ist sie losgelassen (oben).</span><span class="sxs-lookup"><span data-stu-id="69d99-158">A button is pressed (down) when its corresponding bit is set; otherwise, it's released (up).</span></span>

<span data-ttu-id="69d99-159">So wird der Gedrückt- oder Losgelassen-Zustand für einzelne Tasten bestimmt; hier anhand von Gamepads, aber das gleiche Prinzip gilt ebenso für andere Eingabegeräte wie Arcade-Joysticks, Rennlenkräder usw.</span><span class="sxs-lookup"><span data-stu-id="69d99-159">Recall how single buttons are determined to be pressed or released; gamepads are shown here, but the principles are the same for arcade stick, racing wheel, and the other input device types.</span></span>

```cpp
GamepadReading reading = gamepad.GetCurrentReading();

// Determines whether gamepad button A is pressed.
if (GamepadButtons::A == (reading.Buttons & GamepadButtons::A))
{
    // The A button is pressed.
}

// Determines whether gamepad button A is released.
if (GamepadButtons::None == (reading.Buttons & GamepadButtons::A))
{
    // The A button is released (not pressed).
}
```

<span data-ttu-id="69d99-160">Wie man sieht, ist der Zustand einzelner Tasten leicht zu bestimmen; manchmal müssen Sie aber feststellen, ob mehrere oder verschiedene, in bestimmter Weise angeordnete Tasten gedrückt bzw. losgelassen sind.</span><span class="sxs-lookup"><span data-stu-id="69d99-160">As you can see, determining the state of a single button is straight-forward, but sometimes you might want to determine whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="69d99-161">Mehrere Tasten sind komplexer zu testen als einzelne Tasten&mdash;, insbesondere bei gemischten Tastenzuständen&mdash;; es gibt jedoch eine einfache Formel, um sowohl einzelne als auch mehrere Tasten zu testen.</span><span class="sxs-lookup"><span data-stu-id="69d99-161">Testing multiple buttons is more complex than testing single buttons&mdash;especially with the potential of mixed button state&mdash;but there's a simple formula for these tests that applies to single and multiple button tests alike.</span></span>

<span data-ttu-id="69d99-162">Im folgenden Beispiel wird festgestellt, ob die beiden Gamepad-Tasten A und B gedrückt sind.</span><span class="sxs-lookup"><span data-stu-id="69d99-162">The following example determines whether gamepad buttons A and B are both pressed:</span></span>

```cpp
if ((GamepadButtons::A | GamepadButtons::B) == (reading.Buttons & (GamepadButtons::A | GamepadButtons::B))
{
    // The A and B buttons are both pressed.
}
```

<span data-ttu-id="69d99-163">Im folgenden Beispiel wird festgestellt, ob die beiden Gamepad-Tasten A und B losgelassen sind.</span><span class="sxs-lookup"><span data-stu-id="69d99-163">The following example determines whether gamepad buttons A and B are both released:</span></span>

```cpp
if ((GamepadButtons::None == (reading.Buttons & GamepadButtons::A | GamepadButtons::B))
{
    // The A and B buttons are both released (not pressed).
}
```

<span data-ttu-id="69d99-164">Im folgenden Beispiel wird festgestellt, ob Gamepad-Taste A gedrückt und Taste B losgelassen ist.</span><span class="sxs-lookup"><span data-stu-id="69d99-164">The following example determines whether gamepad button A is pressed while button B is released:</span></span>

```cpp
if (GamepadButtons::A == (reading.Buttons & (GamepadButtons::A | GamepadButtons::B))
{
    // The A button is pressed and the B button is released (B is not pressed).
}
```

<span data-ttu-id="69d99-165">Die Formel, die in allen fünf Beispielen verwendet wird, ist wie folgt aufgebaut: Die Anordnung der zu überprüfenden Tasten wird durch den Ausdruck auf der linken Seite des Gleichheitsoperators angegeben, während die Tasten, die berücksichtigt werden sollen, durch den Maskierungsausdruck auf der rechten Seite ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="69d99-165">The formula that all five of these examples have in common is that the arrangement of buttons to be tested for is specified by the expression on the left-hand side of the equality operator while the buttons to be considered are selected by the masking expression on the right-hand side.</span></span>

<span data-ttu-id="69d99-166">Das folgende Beispiel zeigt die Formel noch deutlicher, da das vorherige Beispiel umgeschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="69d99-166">The following example demonstrates this formula more clearly by rewriting the previous example:</span></span>

```cpp
auto buttonArrangement = GamepadButtons::A;
auto buttonSelection = (reading.Buttons & (GamepadButtons::A | GamepadButtons::B));

if (buttonArrangement == buttonSelection)
{
    // The A button is pressed and the B button is released (B is not pressed).
}
```

<span data-ttu-id="69d99-167">Diese Formel kann zum Testen beliebig vieler Tasten, Anordnungen und Zustände verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="69d99-167">This formula can be applied to test any number of buttons in any arrangement of their states.</span></span>

## <a name="get-the-state-of-the-battery"></a><span data-ttu-id="69d99-168">Abrufen des Akkustatus</span><span class="sxs-lookup"><span data-stu-id="69d99-168">Get the state of the battery</span></span>

<span data-ttu-id="69d99-169">Für alle Gamecontroller, die die [IGameControllerBatteryInfo](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontrollerbatteryinfo)-Benutzeroberfläche implementieren, rufen Sie [TryGetBatteryReport](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontrollerbatteryinfo.TryGetBatteryReport) auf der Controllerinstanz auf, um ein [BatteryReport](https://docs.microsoft.com/uwp/api/windows.devices.power.batteryreport)-Objekt mit Informationen zum Akku im Controller zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="69d99-169">For any game controller that implements the [IGameControllerBatteryInfo](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontrollerbatteryinfo) interface, you can call [TryGetBatteryReport](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontrollerbatteryinfo.TryGetBatteryReport) on the controller instance to get a [BatteryReport](https://docs.microsoft.com/uwp/api/windows.devices.power.batteryreport) object that provides information about the battery in the controller.</span></span> <span data-ttu-id="69d99-170">Sie erhalten Eigenschaften wie die Rate, mit der der Akku geladen wird ([ChargeRateInMilliwatts](https://docs.microsoft.com/uwp/api/windows.devices.power.batteryreport.ChargeRateInMilliwatts)), die geschätzte Energiekapazität eines neuen Akkus ([DesignCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.DesignCapacityInMilliwattHours)), und die vollständige Energieeffizienz des aufgeladenen aktuellen Akkus ([FullChargeCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.FullChargeCapacityInMilliwattHours)).</span><span class="sxs-lookup"><span data-stu-id="69d99-170">You can get properties like the rate that the battery is charging ([ChargeRateInMilliwatts](https://docs.microsoft.com/uwp/api/windows.devices.power.batteryreport.ChargeRateInMilliwatts)), the estimated energy capacity of a new battery ([DesignCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.DesignCapacityInMilliwattHours)), and the fully-charged energy capacity of the current battery ([FullChargeCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.FullChargeCapacityInMilliwattHours)).</span></span>

<span data-ttu-id="69d99-171">Für Gamecontroller, die detaillierte Berichte für den Akku unterstützen, erhalten Sie diese und weitere Informationen zum Akku, wie unter [Abrufen von Akkuinformationen](../devices-sensors/get-battery-info.md) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="69d99-171">For game controllers that support detailed battery reporting, you can get this and more information about the battery, as detailed in [Get battery information](../devices-sensors/get-battery-info.md).</span></span> <span data-ttu-id="69d99-172">Die meisten Gamecontroller unterstützen jedoch nicht die Akkuberichtsstufe und verwenden kostengünstige Hardware.</span><span class="sxs-lookup"><span data-stu-id="69d99-172">However, most game controllers don't support that level of battery reporting, and instead use low-cost hardware.</span></span> <span data-ttu-id="69d99-173">Für diese Domänencontroller müssen Sie Folgendes bedenken:</span><span class="sxs-lookup"><span data-stu-id="69d99-173">For these controllers, you'll need to keep the following considerations in mind:</span></span>

* <span data-ttu-id="69d99-174">**ChargeRateInMilliwatts** und **DesignCapacityInMilliwattHours** müssen immer **NULL** sein.</span><span class="sxs-lookup"><span data-stu-id="69d99-174">**ChargeRateInMilliwatts** and **DesignCapacityInMilliwattHours** will always be **NULL**.</span></span>

* <span data-ttu-id="69d99-175">Sie erhalten den Prozentsatz des Akkus durch die Berechnung von [RemainingCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.RemainingCapacityInMilliwattHours) / **FullChargeCapacityInMilliwattHours**.</span><span class="sxs-lookup"><span data-stu-id="69d99-175">You can get the battery percentage by calculating [RemainingCapacityInMilliwattHours](https://docs.microsoft.com/en-us/uwp/api/windows.devices.power.batteryreport.RemainingCapacityInMilliwattHours) / **FullChargeCapacityInMilliwattHours**.</span></span> <span data-ttu-id="69d99-176">Sollten Sie die Werte dieser Eigenschaften ignorieren und nur mit den berechneten Prozentsätzen arbeiten.</span><span class="sxs-lookup"><span data-stu-id="69d99-176">You should ignore the values of these properties and only deal with the calculated percentage.</span></span>

* <span data-ttu-id="69d99-177">Der Prozentsatz der vorherigen Aufzählungszeichen ist immer einer der folgenden:</span><span class="sxs-lookup"><span data-stu-id="69d99-177">The percentage from the previous bullet point will always be one of the following:</span></span>

    * <span data-ttu-id="69d99-178">100 % (Voll)</span><span class="sxs-lookup"><span data-stu-id="69d99-178">100% (Full)</span></span>
    * <span data-ttu-id="69d99-179">70 % (Mittel)</span><span class="sxs-lookup"><span data-stu-id="69d99-179">70% (Medium)</span></span>
    * <span data-ttu-id="69d99-180">40 % (Niedrig)</span><span class="sxs-lookup"><span data-stu-id="69d99-180">40% (Low)</span></span>
    * <span data-ttu-id="69d99-181">10 % (Kritisch)</span><span class="sxs-lookup"><span data-stu-id="69d99-181">10% (Critical)</span></span>

<span data-ttu-id="69d99-182">Wenn Ihr Code eine Aktion (z.B. das Zeichnen der UI) basierend auf dem Prozentsatz der verbleibende Akkulebensdauer ausführt, stellen Sie sicher, dass er den oben genannten Werten entspricht.</span><span class="sxs-lookup"><span data-stu-id="69d99-182">If your code performs some action (like drawing UI) based on the percentage of battery life remaining, make sure that it conforms to the values above.</span></span> <span data-ttu-id="69d99-183">Wenn Sie beispielsweise den Spieler warnen möchten, dass der Controller-Akku fast leer ist, wenn dieser 10% erreicht.</span><span class="sxs-lookup"><span data-stu-id="69d99-183">For example, if you want to warn the player when the controller's battery is low, do so when it reaches 10%.</span></span>

## <a name="see-also"></a><span data-ttu-id="69d99-184">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="69d99-184">See also</span></span>

* [<span data-ttu-id="69d99-185">Windows.System.User-Klasse</span><span class="sxs-lookup"><span data-stu-id="69d99-185">Windows.System.User class</span></span>](https://docs.microsoft.com/uwp/api/windows.system.user)
* [<span data-ttu-id="69d99-186">Windows.Gaming.Input.IGameController-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="69d99-186">Windows.Gaming.Input.IGameController interface</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller)
* [<span data-ttu-id="69d99-187">Windows.Gaming.Input.GamepadButtons-Enum.</span><span class="sxs-lookup"><span data-stu-id="69d99-187">Windows.Gaming.Input.GamepadButtons enum</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamepadbuttons)
