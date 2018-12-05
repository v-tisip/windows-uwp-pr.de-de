---
title: Unformatierter Gamecontroller
description: Mithilfe der Windows.Gaming.Input-APIs für unformatierte Gamecontroller können Sie die Eingaben von fast jedem Gamecontrollertyp lesen.
ms.assetid: 2A466C16-1F51-4D8D-AD13-704B6D3C7BEC
ms.date: 03/08/2017
ms.topic: article
keywords: Windows10, Uwp, Spiele, Eingabe, unformatierter Gamecontroller
ms.localizationpriority: medium
ms.openlocfilehash: 7b5f4d49ad49cf9f9065fe17788456e9dd2a4a4e
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8693709"
---
# <a name="raw-game-controller"></a><span data-ttu-id="b9506-104">Unformatierter Gamecontroller</span><span class="sxs-lookup"><span data-stu-id="b9506-104">Raw game controller</span></span>

<span data-ttu-id="b9506-105">Diese Seite beschreibt die Grundlagen der Programmierung für fast jeden Gamecontrollertyp mithilfe von [Windows.Gaming.Input.RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) und weiterer APIs für die Universelle Windows-Plattform (UWP).</span><span class="sxs-lookup"><span data-stu-id="b9506-105">This page describes the basics of programming for nearly any type of game controller using [Windows.Gaming.Input.RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="b9506-106">Auf dieser Seite lernen Sie:</span><span class="sxs-lookup"><span data-stu-id="b9506-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="b9506-107">Eine Liste der verbundenen unformatierten Gamecontroller und ihrer Benutzer zu erstellen</span><span class="sxs-lookup"><span data-stu-id="b9506-107">how to gather a list of connected raw game controllers and their users</span></span>
* <span data-ttu-id="b9506-108">Zu ermitteln, ob ein unformatierter Gamecontroller hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="b9506-108">how to detect that a raw game controller has been added or removed</span></span>
* <span data-ttu-id="b9506-109">Die Funktionen eines unformatierten Gamecontrollers abzurufen</span><span class="sxs-lookup"><span data-stu-id="b9506-109">how to get the capabilities of a raw game controller</span></span>
* <span data-ttu-id="b9506-110">Die Eingaben eines unformatierten Gamecontrollers zu lesen</span><span class="sxs-lookup"><span data-stu-id="b9506-110">how to read input from a raw game controller</span></span>

## <a name="overview"></a><span data-ttu-id="b9506-111">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b9506-111">Overview</span></span>

<span data-ttu-id="b9506-112">Ein unformatierter Gamecontroller bietet eine generische Darstellung mit den typischen allgemeinen Eingaben eines Gamecontrollers.</span><span class="sxs-lookup"><span data-stu-id="b9506-112">A raw game controller is a generic representation of a game controller, with inputs found on many different kinds of common game controllers.</span></span> <span data-ttu-id="b9506-113">Diese Eingaben sind als einfache Arrays von unbenannten Schaltflächen, Hebeln und Knöpfen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b9506-113">These inputs are exposed as simple arrays of unnamed buttons, switches, and axes.</span></span> <span data-ttu-id="b9506-114">Mit einem unformatierten Gamecontroller kann ein Kunde benutzerdefinierte Eingabe-Zuordnungen erstellen, unabhängig von seinem verwendeten Controllertyp.</span><span class="sxs-lookup"><span data-stu-id="b9506-114">Using a raw game controller, you can allow customers to create custom input mappings no matter what type of controller they're using.</span></span>

<span data-ttu-id="b9506-115">Die [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller)-Klasse ist eigentlich für Fälle gedacht, wo andere Eingabeklassen (wie  [ArcadeStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick) usw.) nicht Ihren allgemeinen Anforderungen entsprechen. Diese Klasse ist geeignet, wenn Ihre Kunden voraussichtlich viele verschiedene Gamecontrollertypen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b9506-115">The [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) class is really meant for scenarios when the other input classes ([ArcadeStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.arcadestick), [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick), and so on) don't meet your needs&mdash;if you want something more generic, anticipating that customers will use many different types of game controllers, then this class is for you.</span></span>

## <a name="detect-and-track-raw-game-controllers"></a><span data-ttu-id="b9506-116">Ermitteln und Nachverfolgen unformatierter Gamecontroller</span><span class="sxs-lookup"><span data-stu-id="b9506-116">Detect and track raw game controllers</span></span>

<span data-ttu-id="b9506-117">Ermitteln und Nachverfolgen von unformatierten Gamecontrollern funktioniert auf genau die gleiche Weise wie für Gamepads, außer bei der [Unformatierte Gamecontroller](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller)-Klasse anstelle der [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b9506-117">Detecting and tracking raw game controllers works in exactly the same way as it does for gamepads, except with the [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) class instead of the [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad) class.</span></span> <span data-ttu-id="b9506-118">Weitere Informationen finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).</span><span class="sxs-lookup"><span data-stu-id="b9506-118">See [Gamepad and vibration](gamepad-and-vibration.md) for more information.</span></span>

<!-- Raw game controllers are managed by the system, therefore you don't have to create or initialize them. The system provides a list of connected raw game controllers and events to notify you when a raw game controller is added or removed.

### The raw game controller list

The [RawGameController](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller) class provides a static property, [RawGameControllers](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_RawGameControllers), which is a read-only list of raw game controllers that are currently connected. Because you might only be interested in some of the connected raw game controllers, we recommend that you maintain your own collection instead of accessing them through the **RawGameControllers** property.

The following example copies all connected raw game controllers into a new collection:

```cpp
auto myRawGameControllers = ref new Vector<RawGameController^>();

for (auto rawGameController : RawGameController::RawGameControllers)
{
    // This code assumes that you're interested in all raw game controllers.
    myRawGameControllers->Append(rawGameController);
}
```

### Adding and removing raw game controllers

When a raw game controller is added or removed, the [RawGameControllerAdded](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_RawGameControllerAdded) and [RawGameControllerRemoved](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_RawGameControllerRemoved) events are raised. You can register handlers for these events to keep track of the raw game controllers that are currently connected.

The following example starts tracking a raw game controller that's been added:

```cpp
RawGameController::RawGameControllerAdded += 
    ref new EventHandler<RawGameController^>(
        [] (Platform::Object^, RawGameController^ args)
{
    // This code assumes that you're interested in all new raw game controllers.
    myRawGameControllers->Append(args);
});
```

The following example stops tracking a raw game controller that's been removed:

```cpp
RawGameController::RawGameControllerRemoved +=
    ref new EventHandler<RawGameController^>(
        [] (Platform::Object^, RawGameController^ args)
{
    unsigned int indexRemoved;

    if (myRawGameControllers->IndexOf(args, &indexRemoved))
    {
        myRawGameControllers->RemoveAt(indexRemoved);
    }
});
```

### Users and headsets

Each raw game controller can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features. To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md). -->

## <a name="get-the-capabilities-of-a-raw-game-controller"></a><span data-ttu-id="b9506-119">Abrufen der Funktionen eines unformatierten Gamecontrollers</span><span class="sxs-lookup"><span data-stu-id="b9506-119">Get the capabilities of a raw game controller</span></span>

<span data-ttu-id="b9506-120">Wenn Sie einen für Sie interessanten unformatierten Gamecontroller gefunden haben, können Sie Informationen zu seinen Funktionen einholen.</span><span class="sxs-lookup"><span data-stu-id="b9506-120">After you identify the raw game controller that you're interested in, you can gather information on the capabilities of the controller.</span></span> <span data-ttu-id="b9506-121">Sie können mit [RawGameController.ButtonCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.ButtonCount) die Anzahl der Schaltflächen des unformatierten Gamecontrollers, mit [RawGameController.AxisCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.AxisCount) die Anzahl seiner analogen Achsen und mit [RawGameController.SwitchCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.SwitchCount) die Anzahl seiner Schalter abrufen.</span><span class="sxs-lookup"><span data-stu-id="b9506-121">You can get the number of buttons on the raw game controller with [RawGameController.ButtonCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.ButtonCount), the number of analog axes with [RawGameController.AxisCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.AxisCount), and the number of switches with [RawGameController.SwitchCount](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.SwitchCount).</span></span> <span data-ttu-id="b9506-122">Außerdem können Sie mit [RawGameController.GetSwitchKind](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetSwitchKind_System_Int32_) den Typ eines Schalters abrufen.</span><span class="sxs-lookup"><span data-stu-id="b9506-122">Additionally, you can get the type of a switch using [RawGameController.GetSwitchKind](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetSwitchKind_System_Int32_).</span></span>

<span data-ttu-id="b9506-123">Das folgende Beispiel ruft den Eingabezähler eines unformatierten Gamecontrollers ab:</span><span class="sxs-lookup"><span data-stu-id="b9506-123">The following example gets the input counts of a raw game controller:</span></span>

```cpp
auto rawGameController = myRawGameControllers->GetAt(0);
int buttonCount = rawGameController->ButtonCount;
int axisCount = rawGameController->AxisCount;
int switchCount = rawGameController->SwitchCount;
```

<span data-ttu-id="b9506-124">Das folgende Beispiel bestimmt den Typ jedes Schalters:</span><span class="sxs-lookup"><span data-stu-id="b9506-124">The following example determines the type of each switch:</span></span>

```cpp
for (uint32_t i = 0; i < switchCount; i++)
{
    GameControllerSwitchKind mySwitch = rawGameController->GetSwitchKind(i);
}
```

## <a name="reading-the-raw-game-controller"></a><span data-ttu-id="b9506-125">Lesen des unformatierten Gamecontrollers</span><span class="sxs-lookup"><span data-stu-id="b9506-125">Reading the raw game controller</span></span>

<span data-ttu-id="b9506-126">Sobald Sie die Anzahl der Eingaben auf einem unformatierten Gamecontroller kennen, können Sie beginnen die Eingaben zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="b9506-126">After you know the number of inputs on a raw game controller, you're ready to gather input from it.</span></span> <span data-ttu-id="b9506-127">Im Unterschied zu anderen Eingaben, die Sie vielleicht kennen, teilen unformatierte Gamecontroller keine Zustandsänderungen durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="b9506-127">However, unlike some other kinds of input that you might be used to, a raw game controller doesn't communicate state-change by raising events.</span></span> <span data-ttu-id="b9506-128">Sie müssen seinen Zustand daher regelmäßig durch _Abrufe_ auslesen.</span><span class="sxs-lookup"><span data-stu-id="b9506-128">Instead, you take regular readings of its current state by _polling_ it.</span></span>

### <a name="polling-the-raw-game-controller"></a><span data-ttu-id="b9506-129">Abrufen des unformatierten Gamecontrollers</span><span class="sxs-lookup"><span data-stu-id="b9506-129">Polling the raw game controller</span></span>

<span data-ttu-id="b9506-130">Jeder Abruf erstellt eine Momentaufnahme des unformatierten Gamecontrollers zu einem bestimmten Zeitpunkt.</span><span class="sxs-lookup"><span data-stu-id="b9506-130">Polling captures a snapshot of the raw game controller at a precise point in time.</span></span> <span data-ttu-id="b9506-131">Dieser Ansatz zur Eingabeerfassung ist für die meisten Spiele geeignet, da deren Logik normalerweise als deterministische Schleife, nicht ereignisgesteuert ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b9506-131">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven.</span></span> <span data-ttu-id="b9506-132">Außerdem lassen sich Spielbefehle aus erfassten Eingaben einfacher interpretieren als aus vielen einzelnen Eingaben, die im Laufe der Zeit erfasst wurden.</span><span class="sxs-lookup"><span data-stu-id="b9506-132">It's also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="b9506-133">Sie erfassen einen unformatierten Gamecontroller durch den Aufruf [RawGameController.GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetCurrentReading_System_Boolean___Windows_Gaming_Input_GameControllerSwitchPosition___System_Double___).</span><span class="sxs-lookup"><span data-stu-id="b9506-133">You poll a raw game controller by calling [RawGameController.GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetCurrentReading_System_Boolean___Windows_Gaming_Input_GameControllerSwitchPosition___System_Double___).</span></span> <span data-ttu-id="b9506-134">Diese Funktion füllt Arrays für Schaltflächen, Schalter und Achsen, die den Zustand des unformatierten Gamecontrollers enthalten.</span><span class="sxs-lookup"><span data-stu-id="b9506-134">This function populates arrays for buttons, switches, and axes that contain the state of the raw game controller.</span></span>

<span data-ttu-id="b9506-135">Das folgende Beispiel ruft den aktuellen Zustand eines unformatierten Gamecontrollers ab.</span><span class="sxs-lookup"><span data-stu-id="b9506-135">The following example polls a raw game controller for its current state:</span></span>

```cpp
Platform::Array<bool>^ currentButtonReading =
    ref new Platform::Array<bool>(buttonCount);

Platform::Array<GameControllerSwitchPosition>^ currentSwitchReading =
    ref new Platform::Array<GameControllerSwitchPosition>(switchCount);

Platform::Array<double>^ currentAxisReading = ref new Platform::Array<double>(axisCount);

rawGameController->GetCurrentReading(
    currentButtonReading,
    currentSwitchReading,
    currentAxisReading);
```

<span data-ttu-id="b9506-136">Da nicht für jeden Controllertyp garantiert werden kann, welche Position in den Arrays welchen Eingabewert enthält, müssen diese Werte durch die Methoden [RawGameController.GetButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetButtonLabel_System_Int32_) und [RawGameController.GetSwitchKind](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetSwitchKind_System_Int32_) ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="b9506-136">There is no guarantee of which position in each array will hold which input value among different types of controllers, so you'll need to check which input is which using the methods [RawGameController.GetButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetButtonLabel_System_Int32_) and [RawGameController.GetSwitchKind](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetSwitchKind_System_Int32_).</span></span>

<span data-ttu-id="b9506-137">**GetButtonLabel** gibt den Text oder das Symbol auf einer physischen Taste an, nicht ihre Funktion und sollte daher nur als Hilfe genutzt werden, falls Sie dem Spieler auf der Benutzeroberfläche zeigen möchten, welche Taste welche Funktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="b9506-137">**GetButtonLabel** will tell you the text or symbol that's printed on the physical button, rather than the button's function&mdash;therefore, it's best used as an aid for UI for cases where you want to give the player hints about which buttons perform which functions.</span></span> <span data-ttu-id="b9506-138">**GetSwitchKind** gibt die Art eines Schalters an (d.h. wie viele Positionen er hat), nicht seinen Namen.</span><span class="sxs-lookup"><span data-stu-id="b9506-138">**GetSwitchKind** will tell you the type of switch (that is, how many positions it has), but not the name.</span></span>

<span data-ttu-id="b9506-139">Da es keine standardisierte Methode gibt, um die Bezeichnungen von Achsen oder Schaltern abzurufen, müssen Sie diese durch Eingaben selbst ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b9506-139">There is no standardized way to get the label of an axis or switch, so you'll need to test these yourself to determine which input is which.</span></span>

<span data-ttu-id="b9506-140">Wenn Sie einen bestimmten Controller unterstützen möchten, können Sie durch die Aufrufe [RawGameController.HardwareProductId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareProductId) und [RawGameController.HardwareVendorId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareVendorId) ermitteln, ob er unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="b9506-140">If you have a specific controller that you want to support, you can get the [RawGameController.HardwareProductId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareProductId) and [RawGameController.HardwareVendorId](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller.HardwareVendorId) and check if they match that controller.</span></span> <span data-ttu-id="b9506-141">Da die Position jeder Eingabe in einem Array für alle Controller mit gleicher **HardwareProductId** und **HardwareVendorId** gilt, müssen Sie nicht befürchten, dass Ihre Logik möglicherweise nicht zu den verschiedenen Controllern eines Typs passt.</span><span class="sxs-lookup"><span data-stu-id="b9506-141">The position of each input in each array is the same for every controller with the same **HardwareProductId** and **HardwareVendorId**, so you don't have to worry about your logic potentially being inconsistent among different controllers of the same type.</span></span>

<span data-ttu-id="b9506-142">Jeder Abruf des Zustands eines unformatierten Gamecontrollers gibt auch einen Zeitstempel zurück, der den genauen Zeitpunkt des Abrufs angibt.</span><span class="sxs-lookup"><span data-stu-id="b9506-142">In addition to the raw game controller state, each reading returns a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="b9506-143">Dieser Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten früherer Abrufe oder Spielsimulationen herzustellen.</span><span class="sxs-lookup"><span data-stu-id="b9506-143">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="reading-the-buttons-and-switches"></a><span data-ttu-id="b9506-144">Lesen von Schaltflächen und Tasten</span><span class="sxs-lookup"><span data-stu-id="b9506-144">Reading the buttons and switches</span></span>

<span data-ttu-id="b9506-145">Jede Schaltfläche eines unformatierten Gamecontrollers liefert einen digitalen Wert, der den gedrückten (unten) oder losgelassenen (oben) Zustand angibt.</span><span class="sxs-lookup"><span data-stu-id="b9506-145">Each of the raw game controller's buttons provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="b9506-146">Schaltflächenwerte werden als einzelne boolesche Werte in einem Array dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b9506-146">Button readings are represented as individual Boolean values in a single array.</span></span> <span data-ttu-id="b9506-147">Die Bezeichnung jeder Schaltfläche ermitteln Sie durch [RawGameController.GetButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetButtonLabel_System_Int32_) und den Index des booleschen Werts im Array.</span><span class="sxs-lookup"><span data-stu-id="b9506-147">The label for each button can be found using [RawGameController.GetButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller#Windows_Gaming_Input_RawGameController_GetButtonLabel_System_Int32_) with the index of the Boolean value in the array.</span></span> <span data-ttu-id="b9506-148">Jeder Wert wird als [GameControllerButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b9506-148">Each value is represented as a [GameControllerButtonLabel](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerbuttonlabel).</span></span>

<span data-ttu-id="b9506-149">Im folgenden Beispiel wird ermittelt, ob die Taste **XboxA** gedrückt ist:</span><span class="sxs-lookup"><span data-stu-id="b9506-149">The following example determines whether the **XboxA** button is pressed:</span></span>

```cpp
for (uint32_t i = 0; i < buttonCount; i++)
{
    if (currentButtonReading[i])
    {
        GameControllerButtonLabel buttonLabel = rawGameController->GetButtonLabel(i);

        if (buttonLabel == GameControllerButtonLabel::XboxA)
        {
            // XboxA is pressed.
        }
    }
}
```

<span data-ttu-id="b9506-150">In einigen Fällen möchten Sie vielleicht ermitteln, ob eine Taste von „gedrückt“ zu „nicht gedrückt“ bzw. umgekehrt wechselt, oder ob mehrere Tasten gedrückt/ nicht gedrückt bzw. in bestimmter Weise angeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="b9506-150">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="b9506-151">Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) sowie unter [Erkennen komplexer Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="b9506-151">For information on how to detect each of these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

<span data-ttu-id="b9506-152">Schalterwerte werden als Array mit [GameControllerSwitchPosition](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerswitchposition) angegeben.</span><span class="sxs-lookup"><span data-stu-id="b9506-152">Switch values are provided as an array of [GameControllerSwitchPosition](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerswitchposition).</span></span> <span data-ttu-id="b9506-153">Diese Eigenschaft ist ein Bitfeld und wird deshalb bitweise maskiert, um die Richtung des Schalters zu isolieren.</span><span class="sxs-lookup"><span data-stu-id="b9506-153">Because this property is a bitfield, bitwise masking is used to isolate the direction of the switch.</span></span>

<span data-ttu-id="b9506-154">Das folgende Beispiel ermittelt, ob sich alle Schalter in der Stellung „oben” befinden:</span><span class="sxs-lookup"><span data-stu-id="b9506-154">The following example determines whether each switch is in the up position:</span></span>

```cpp
for (uint32_t i = 0; i < switchCount; i++)
{
    if (GameControllerSwitchPosition::Up ==
        (currentSwitchReading[i] & GameControllerSwitchPosition::Up))
    {
        // The switch is in the up position.
    }
}
```

### <a name="reading-the-analog-inputs-sticks-triggers-throttles-and-so-on"></a><span data-ttu-id="b9506-155">Ablesen von analogen Eingaben (Sticks, Trigger, Drosselungen usw.)</span><span class="sxs-lookup"><span data-stu-id="b9506-155">Reading the analog inputs (sticks, triggers, throttles, and so on)</span></span>

<span data-ttu-id="b9506-156">Eine analoge Achse liefert Werte zwischen 0,0 und 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9506-156">An analog axis provides a reading between 0.0 and 1.0.</span></span> <span data-ttu-id="b9506-157">Dazu gehören die einzelnen Dimensionen auf einem Stick, z.B. X und Y für Standardsticks, oder auch X-, Y- und Z-Achsen (für Rollen, Neigen und Schwenken) für Steuerknüppel.</span><span class="sxs-lookup"><span data-stu-id="b9506-157">This includes each dimension on a stick such as X and Y for standard sticks or even X, Y, and Z axes (roll, pitch, and yaw, respectively) for flight sticks.</span></span>

<span data-ttu-id="b9506-158">Die Werte können jeden analogen Eingabetyp wie Trigger, Drosselungen usw. darstellen.</span><span class="sxs-lookup"><span data-stu-id="b9506-158">The values can represent analog triggers, throttles, or any other type of analog input.</span></span> <span data-ttu-id="b9506-159">Da für diese Werte keine Bezeichnungen angegeben werden, empfehlen wir Ihren Code auf verschiedenen Eingabegeräten zu testen, um sicherzustellen, dass er wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b9506-159">These values are not provided with labels, so we suggest that your code is tested with a variety of input devices to ensure that they match correctly with your assumptions.</span></span>

<span data-ttu-id="b9506-160">Wenn sich der Stick in der Mittelposition befindet, ist der Wert auf allen Achsen ca. 0,5; es ist jedoch normal, wenn der genaue Wert variiert, auch zwischen nachfolgend erfassten Werten. Strategien zur Minimierung dieser Abweichung werden später in diesem Abschnitt erläutert.</span><span class="sxs-lookup"><span data-stu-id="b9506-160">In all axes, the value is approximately 0.5 for a stick when it is in the center position, but it's normal for the precise value to vary, even between subsequent readings; strategies for mitigating this variation are discussed later in this section.</span></span>

<span data-ttu-id="b9506-161">Das folgende Beispiel zeigt, wie die analogen Werte eines Xbox-Controllers gelesen werden:</span><span class="sxs-lookup"><span data-stu-id="b9506-161">The following example shows how to read the analog values from an Xbox controller:</span></span>

```cpp
// Xbox controllers have 6 axes: 2 for each stick and one for each trigger.
float leftStickX = currentAxisReading[0];
float leftStickY = currentAxisReading[1];
float rightStickX = currentAxisReading[2];
float rightStickY = currentAxisReading[3];
float leftTrigger = currentAxisReading[4];
float rightTrigger = currentAxisReading[5];
```

<span data-ttu-id="b9506-162">Sie bemerken, dass die gelesenen Werte nicht zuverlässig den neutralen Wert 0,5 liefern, wenn sich der Stick in der ruhenden Mittelstellung befindet, sondern verschiedene Näherungswerte bei 0,5, sobald der Stick bewegt wurde und in die Mittelstellung zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="b9506-162">When reading the stick values, you'll notice that they don't reliably produce a neutral reading of 0.5 when at rest in the center position; instead, they'll produce different values near 0.5 each time the stick is moved and returned to the center position.</span></span> <span data-ttu-id="b9506-163">Zur Kompensierung dieser Abweichungen können Sie einen kleinen _inaktiven Bereich_ implementieren (also einen zu ignorieRendern Wertebereich nahe der idealen Mittelposition).</span><span class="sxs-lookup"><span data-stu-id="b9506-163">To mitigate these variations, you can implement a small _deadzone_, which is a range of values near the ideal center position that are ignored.</span></span>

<span data-ttu-id="b9506-164">Um inaktive Bereiche zu implementieren, können Sie beispielsweise festlegen, wie weit der Stick von der Mittelstellung bewegt wird, und die Werte unterhalb der gewählten Entfernung ignorieren.</span><span class="sxs-lookup"><span data-stu-id="b9506-164">One way to implement a deadzone is to determine how far the stick has moved from the center, and ignore readings that are nearer than some distance you choose.</span></span> <span data-ttu-id="b9506-165">Die grobe Entfernung kann nach dem Satz des Pythagoras berechnet werden; diese Methode ist allerdings nicht exakt, da die Werte von Sticks nicht planar, sondern polar sind.</span><span class="sxs-lookup"><span data-stu-id="b9506-165">You can compute the distance roughly&mdash;it's not exact because stick readings are essentially polar, not planar, values&mdash;just by using the Pythagorean theorem.</span></span> <span data-ttu-id="b9506-166">Dadurch entsteht ein radialer inaktiver Bereich.</span><span class="sxs-lookup"><span data-stu-id="b9506-166">This produces a radial deadzone.</span></span>

<span data-ttu-id="b9506-167">Das folgende Beispiel zeigt einen radialen inaktiven Bereich, berechnet nach dem Satz des Pythagoras:</span><span class="sxs-lookup"><span data-stu-id="b9506-167">The following example demonstrates a basic radial deadzone using the Pythagorean theorem:</span></span>

```cpp
// Choose a deadzone. Readings inside this radius are ignored.
const float deadzoneRadius = 0.1f;
const float deadzoneSquared = deadzoneRadius * deadzoneRadius;

// Pythagorean theorem: For a right triangle, hypotenuse^2 = (opposite side)^2 + (adjacent side)^2
float oppositeSquared = leftStickY * leftStickY;
float adjacentSquared = leftStickX * leftStickX;

// Accept and process input if true; otherwise, reject and ignore it.
if ((oppositeSquared + adjacentSquared) < deadzoneSquared)
{
    // Input accepted, process it.
}
```

<!--## Run the RawGameControllerUWP sample

The [RawGameControllerUWP sample (GitHub)](TODO: Link) demonstrates how to use raw game controllers. TODO: More information-->

## <a name="see-also"></a><span data-ttu-id="b9506-168">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="b9506-168">See also</span></span>

* [<span data-ttu-id="b9506-169">Eingaben für Spiele</span><span class="sxs-lookup"><span data-stu-id="b9506-169">Input for games</span></span>](input-for-games.md)
* [<span data-ttu-id="b9506-170">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="b9506-170">Input practices for games</span></span>](input-practices-for-games.md)
* [<span data-ttu-id="b9506-171">Windows.Gaming.Input-Namespace</span><span class="sxs-lookup"><span data-stu-id="b9506-171">Windows.Gaming.Input namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input)
* [<span data-ttu-id="b9506-172">Windows.Gaming.Input.RawGameController-Klasse</span><span class="sxs-lookup"><span data-stu-id="b9506-172">Windows.Gaming.Input.RawGameController class</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.rawgamecontroller)
* [<span data-ttu-id="b9506-173">Windows.Gaming.Input.IGameController-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="b9506-173">Windows.Gaming.Input.IGameController interface</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller)
* [<span data-ttu-id="b9506-174">Windows.Gaming.Input.IGameControllerBatteryInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="b9506-174">Windows.Gaming.Input.IGameControllerBatteryInfo interface</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontrollerbatteryinfo)