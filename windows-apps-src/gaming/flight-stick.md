---
title: Steuerknüppel
description: Verwenden Sie die Windows.Gaming.Input-Steuerknüppel-APIs, um Eingaben von Steuerknüppeln zu lesen.
ms.assetid: DC633F6B-FDC9-4D6E-8401-305861F31192
ms.date: 03/06/2017
ms.topic: article
keywords: windows 10, uwp, Spiele, Eingabe, Steuerknüppel
ms.localizationpriority: medium
ms.openlocfilehash: 5eceb30c62f1e803397aff71d59b560c39736cf9
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7707535"
---
# <a name="flight-stick"></a><span data-ttu-id="2dc28-104">Steuerknüppel</span><span class="sxs-lookup"><span data-stu-id="2dc28-104">Flight stick</span></span>

<span data-ttu-id="2dc28-105">Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-zertifizierte Steuerknüppel mit [Windows.Gaming.Input.FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick) und verwandten APIs für die Universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2dc28-105">This page describes the basics of programming for Xbox One-certified flight sticks using [Windows.Gaming.Input.FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick) and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="2dc28-106">Auf dieser Seite erfahren Sie:</span><span class="sxs-lookup"><span data-stu-id="2dc28-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="2dc28-107">Wie Sie eine Liste der verbundenen Steuerknüppel und ihrer Benutzer erstellen</span><span class="sxs-lookup"><span data-stu-id="2dc28-107">how to gather a list of connected flight sticks and their users</span></span>
* <span data-ttu-id="2dc28-108">Wie Sie ermitteln, ob ein Steuerknüppel hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="2dc28-108">how to detect that a flight stick has been added or removed</span></span>
* <span data-ttu-id="2dc28-109">Wie Sie die Eingabe von einem oder mehreren Steuerknüppeln lesen</span><span class="sxs-lookup"><span data-stu-id="2dc28-109">how to read input from one or more flight sticks</span></span>
* <span data-ttu-id="2dc28-110">Wie sich Steuerknüppel als UI-Navigationsgeräte verhalten</span><span class="sxs-lookup"><span data-stu-id="2dc28-110">how flight sticks behave as UI navigation devices</span></span>

## <a name="overview"></a><span data-ttu-id="2dc28-111">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2dc28-111">Overview</span></span>

<span data-ttu-id="2dc28-112">Steuerknüppel sind Spieleingabegeräte, die das Gefühl eines Steuerknüppels reproduzieren, der in Flugzeugen oder Raumschiffen benutzt wird.</span><span class="sxs-lookup"><span data-stu-id="2dc28-112">Flight sticks are gaming input devices that are valued for reproducing the feel of flight sticks that would be found in a plane or spaceship's cockpit.</span></span> <span data-ttu-id="2dc28-113">Sie sind das perfekte Eingabegerät für die schnelle und genaue Steuerung von Fluggeräten.</span><span class="sxs-lookup"><span data-stu-id="2dc28-113">They're the perfect input device for quick and accurate control of flight.</span></span> <span data-ttu-id="2dc28-114">Steuerknüppel werden in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2dc28-114">Flight sticks are supported in Windows 10 and Xbox One UWP apps by the [Windows.Gaming.Input](https://docs.microsoft.com/uwp/api/windows.gaming.input) namespace.</span></span>

<span data-ttu-id="2dc28-115">Xbox One-Steuerknüppel sind mit den folgenden Steuerelementen ausgestattet:</span><span class="sxs-lookup"><span data-stu-id="2dc28-115">Xbox One flight sticks are equipped with the following controls:</span></span>

* <span data-ttu-id="2dc28-116">Einem drehbaren analogen Joystick, der Rollen, Nicken und Gieren ausführen kann</span><span class="sxs-lookup"><span data-stu-id="2dc28-116">A twistable analog joystick capable of roll, pitch, and yaw</span></span>
* <span data-ttu-id="2dc28-117">Einem analogen Schubregler</span><span class="sxs-lookup"><span data-stu-id="2dc28-117">An analog throttle</span></span>
* <span data-ttu-id="2dc28-118">Zwei Feuern-Tasten</span><span class="sxs-lookup"><span data-stu-id="2dc28-118">Two fire buttons</span></span>
* <span data-ttu-id="2dc28-119">Einem digitalen 8-Wegeschalter</span><span class="sxs-lookup"><span data-stu-id="2dc28-119">An 8-way digital hat switch</span></span>
* <span data-ttu-id="2dc28-120">**Ansicht**- und **Menü**-Tasten</span><span class="sxs-lookup"><span data-stu-id="2dc28-120">**View** and **Menu** buttons</span></span>

> [!NOTE]
> <span data-ttu-id="2dc28-121">Die **Ansicht**- und **Menü**-Tasten werden zur Unterstützung der Benutzeroberflächennavigation, nicht der Spielverlaufsbefehle verwendet. Daher kann auf diese Tasten nicht ohne Weiteres als Joystick-Tasten zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="2dc28-121">The **View** and **Menu** buttons are used to support UI navigation, not gameplay commands, and therefore can't be readily accessed as joystick buttons.</span></span>

### <a name="ui-navigation"></a><span data-ttu-id="2dc28-122">Benutzeroberflächennavigation</span><span class="sxs-lookup"><span data-stu-id="2dc28-122">UI navigation</span></span>

<span data-ttu-id="2dc28-123">Um den Aufwand für die Unterstützung unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="2dc28-123">In order to ease the burden of supporting the different input devices for user interface navigation and to encourage consistency between games and devices, most _physical_ input devices simultaneously act as separate _logical_ input devices called [UI navigation controllers](ui-navigation-controller.md).</span></span> <span data-ttu-id="2dc28-124">Der Benutzeroberflächen-Navigationscontroller stellt über verschiedene Eingabegeräte hinweg ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle bereit.</span><span class="sxs-lookup"><span data-stu-id="2dc28-124">The UI navigation controller provides a common vocabulary for UI navigation commands across input devices.</span></span>

<span data-ttu-id="2dc28-125">Ein Steuerknüppel als Benutzeroberflächen-Navigationscontroller ordnet den [erforderlichen Satz](ui-navigation-controller.md#required-set) an Navigationsbefehlen dem Joystick und den Tasten **Ansicht**, **Menü**, **FirePrimary** und **FireSecondary** zu.</span><span class="sxs-lookup"><span data-stu-id="2dc28-125">As a UI navigation controller, a flight stick maps the [required set](ui-navigation-controller.md#required-set) of navigation commands to the joystick and **View**, **Menu**, **FirePrimary**, and **FireSecondary** buttons.</span></span>

| <span data-ttu-id="2dc28-126">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="2dc28-126">Navigation command</span></span> | <span data-ttu-id="2dc28-127">Steuerknüppeleingabe</span><span class="sxs-lookup"><span data-stu-id="2dc28-127">Flight stick input</span></span>                  |
| ------------------:| ----------------------------------- |
|                 <span data-ttu-id="2dc28-128">Nach oben</span><span class="sxs-lookup"><span data-stu-id="2dc28-128">Up</span></span> | <span data-ttu-id="2dc28-129">Joystick nach oben</span><span class="sxs-lookup"><span data-stu-id="2dc28-129">Joystick up</span></span>                         |
|               <span data-ttu-id="2dc28-130">Nach unten</span><span class="sxs-lookup"><span data-stu-id="2dc28-130">Down</span></span> | <span data-ttu-id="2dc28-131">Joystick nach-unten</span><span class="sxs-lookup"><span data-stu-id="2dc28-131">Joystick down</span></span>                       |
|               <span data-ttu-id="2dc28-132">Links</span><span class="sxs-lookup"><span data-stu-id="2dc28-132">Left</span></span> | <span data-ttu-id="2dc28-133">Joystick nach links</span><span class="sxs-lookup"><span data-stu-id="2dc28-133">Joystick left</span></span>                       |
|              <span data-ttu-id="2dc28-134">Rechts</span><span class="sxs-lookup"><span data-stu-id="2dc28-134">Right</span></span> | <span data-ttu-id="2dc28-135">Joystick nach rechts</span><span class="sxs-lookup"><span data-stu-id="2dc28-135">Joystick right</span></span>                      |
|               <span data-ttu-id="2dc28-136">Ansicht</span><span class="sxs-lookup"><span data-stu-id="2dc28-136">View</span></span> | <span data-ttu-id="2dc28-137">**Ansicht**-Taste</span><span class="sxs-lookup"><span data-stu-id="2dc28-137">**View** button</span></span>                     |
|               <span data-ttu-id="2dc28-138">Menü</span><span class="sxs-lookup"><span data-stu-id="2dc28-138">Menu</span></span> | <span data-ttu-id="2dc28-139">**Menü**-Taste</span><span class="sxs-lookup"><span data-stu-id="2dc28-139">**Menu** button</span></span>                     |
|             <span data-ttu-id="2dc28-140">Annehmen</span><span class="sxs-lookup"><span data-stu-id="2dc28-140">Accept</span></span> | <span data-ttu-id="2dc28-141">**FirePrimary**-Taste</span><span class="sxs-lookup"><span data-stu-id="2dc28-141">**FirePrimary** button</span></span>              |
|             <span data-ttu-id="2dc28-142">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="2dc28-142">Cancel</span></span> | <span data-ttu-id="2dc28-143">**FireSecondary**-Taste</span><span class="sxs-lookup"><span data-stu-id="2dc28-143">**FireSecondary** button</span></span>            |

<span data-ttu-id="2dc28-144">Steuerknüppel ordnen keinen der [optionalen Sätze](ui-navigation-controller.md#optional-set) an Navigationsbefehlen zu.</span><span class="sxs-lookup"><span data-stu-id="2dc28-144">Flight sticks don't map any of the [optional set](ui-navigation-controller.md#optional-set) of navigation commands.</span></span>

## <a name="detect-and-track-flight-sticks"></a><span data-ttu-id="2dc28-145">Ermitteln und Nachverfolgen von Steuerknüppeln</span><span class="sxs-lookup"><span data-stu-id="2dc28-145">Detect and track flight sticks</span></span>

<span data-ttu-id="2dc28-146">Ermitteln und Nachverfolgen von Steuerknüppeln funktioniert auf genau die gleiche Weise wie für Gamepads, außer bei der [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick)-Klasse anstelle der [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="2dc28-146">Detecting and tracking flight sticks works in exactly the same way as it does for gamepads, except with the [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick) class instead of the [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad) class.</span></span> <span data-ttu-id="2dc28-147">Weitere Informationen finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).</span><span class="sxs-lookup"><span data-stu-id="2dc28-147">See [Gamepad and vibration](gamepad-and-vibration.md) for more information.</span></span>

<!-- Flight sticks are managed by the system, therefore you don't have to create or initialize them. The system provides a list of connected flight sticks and events to notify you when a flight stick is added or removed.

### The flight stick list

The [FlightStick](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick) class provides a static property, [FlightSticks](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick#Windows_Gaming_Input_FlightStick_FlightSticks), which is a read-only list of flight sticks that are currently connected. Because you might only be interested in some of the connected flight sticks, we recommend that you maintain your own collection instead of accessing them through the `FlightSticks` property.

The following example copies all connected flight sticks into a new collection:

```cpp
auto myFlightSticks = ref new Vector<FlightStick^>();

for (auto flightStick : FlightStick::FlightSticks)
{
    // This code assumes that you're interested in all flight sticks.
    myFlightSticks->Append(flightStick);
}
```

### Adding and removing flight sticks

When a flight stick is added or removed, the [FlightStickAdded](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick#Windows_Gaming_Input_FlightStick_FlightStickAdded) and [FlightStickRemoved](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick#Windows_Gaming_Input_FlightStick_FlightStickRemoved) events are raised. You can register handlers for these events to keep track of the flight sticks that are currently connected.

The following example starts tracking a flight stick that's been added:

```cpp
FlightStick::FlightStickAdded += 
    ref new EventHandler<FlightStick^>([] (Platform::Object^, FlightStick^ args)
{
    // This code assumes that you're interested in all new flight sticks.
    myFlightSticks->Append(args);
});
```

The following example stops tracking a flight stick that's been removed:

```cpp
FlightStick::FlightStickRemoved += 
    ref new EventHandler<FlightStick^>([] (Platform::Object^, FlightStick^ args)
{
    unsigned int indexRemoved;

    if (myFlightSticks->IndexOf(args, &indexRemoved))
    {
        myFlightSticks->RemoveAt(indexRemoved);
    }
});
```

### Users and headsets

Each flight stick can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features. To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md). -->

## <a name="reading-the-flight-stick"></a><span data-ttu-id="2dc28-148">Lesen von Steuerknüppeleingaben</span><span class="sxs-lookup"><span data-stu-id="2dc28-148">Reading the flight stick</span></span>

<span data-ttu-id="2dc28-149">Nachdem Sie den Steuerknüppel identifiziert haben, für den Sie sich interessieren, können Sie Eingaben von ihm erfassen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-149">After you identify the flight stick that you're interested in, you're ready to gather input from it.</span></span> <span data-ttu-id="2dc28-150">Im Gegensatz zu anderen Eingaben, die Sie möglicherweise kennen, teilen Steuerknüppel Zustandsänderungen nicht durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="2dc28-150">However, unlike some other kinds of input that you might be used to, flight sticks don't communicate state-change by raising events.</span></span> <span data-ttu-id="2dc28-151">Stattdessen müssen Sie den aktuellen Zustand regelmäßig lesen, indem Sie ihn _abrufen_.</span><span class="sxs-lookup"><span data-stu-id="2dc28-151">Instead, you take regular readings of their current state by _polling_ them.</span></span>

### <a name="polling-the-flight-stick"></a><span data-ttu-id="2dc28-152">Abrufen des Zustands von Steuerknüppeln</span><span class="sxs-lookup"><span data-stu-id="2dc28-152">Polling the flight stick</span></span>

<span data-ttu-id="2dc28-153">Beim Abrufen wird ein Snapshot des Steuerknüppels zu einem bestimmten Zeitpunkt erstellt.</span><span class="sxs-lookup"><span data-stu-id="2dc28-153">Polling captures a snapshot of the flight stick at a precise point in time.</span></span> <span data-ttu-id="2dc28-154">Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik in der Regel in einer deterministischer Schleife, anstatt ereignisgesteuert ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2dc28-154">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven.</span></span> <span data-ttu-id="2dc28-155">Im Allgemeinen lassen sich Spielbefehle auch aus erfassten Eingaben zusammen einfacher interpretieren, als aus vielen einzelnen Eingaben, die im Laufe der Zeit erfasst wurden.</span><span class="sxs-lookup"><span data-stu-id="2dc28-155">It's also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="2dc28-156">Sie rufen den Zustand eines Steuerknüppels ab, indem Sie [FlightStick.GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick.GetCurrentReading) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-156">You poll a flight stick by calling [FlightStick.GetCurrentReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstick.GetCurrentReading).</span></span> <span data-ttu-id="2dc28-157">Diese Funktion gibt eine [FlightStickReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading)-Struktur zurück, die den Zustand des Steuerknüppels enthält.</span><span class="sxs-lookup"><span data-stu-id="2dc28-157">This function returns a [FlightStickReading](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading) that contains the state of the flight stick.</span></span>

<span data-ttu-id="2dc28-158">Im folgenden Beispiel wird der aktuelle Zustand eines Steuerknüppels abgerufen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-158">The following example polls a flight stick for its current state:</span></span>

```cpp
auto flightStick = myFlightSticks->GetAt(0);
FlightStickReading reading = flightStick->GetCurrentReading();
```

<span data-ttu-id="2dc28-159">Zusätzlich zum Zustand des Steuerknüppels enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="2dc28-159">In addition to the flight stick state, each reading includes a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="2dc28-160">Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Ablesungen oder zum Zeitpunkt der Spielsimulation herzustellen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-160">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="reading-the-joystick-and-throttle-input"></a><span data-ttu-id="2dc28-161">Lesen der Joystick- und Schubreglereingabe</span><span class="sxs-lookup"><span data-stu-id="2dc28-161">Reading the joystick and throttle input</span></span>

<span data-ttu-id="2dc28-162">Der Joystick liefert analoge Werte zwischen -1,0 und 1,0 in der X-, Y- und Z-Achse ( Rollen, Nicken bzw. Gieren).</span><span class="sxs-lookup"><span data-stu-id="2dc28-162">The joystick provides an analog reading between -1.0 and 1.0 in the X, Y, and Z axes (roll, pitch, and yaw, respectively).</span></span> <span data-ttu-id="2dc28-163">Beim Rollen entspricht der Wert -1,0 auf der X-Achse der äußerst linken Joystickposition und der Wert 1,0 der äußerst rechten Position.</span><span class="sxs-lookup"><span data-stu-id="2dc28-163">For roll, a value of -1.0 corresponds to the left-most joystick position, while a value of 1.0 corresponds to the right-most position.</span></span> <span data-ttu-id="2dc28-164">Beim Nicken entspricht der Wert -1,0 der untersten Joystickposition und der Wert 1,0 der obersten Position.</span><span class="sxs-lookup"><span data-stu-id="2dc28-164">For pitch, a value of -1.0 corresponds to the bottom-most joystick position, while a value of 1.0 corresponds to the top-most position.</span></span> <span data-ttu-id="2dc28-165">Beim Gieren entspricht der Wert -1,0 der äußersten gegen den Uhrzeigersinn gedrehten Position und der Wert 1,0 der äußersten im Uhrzeigersinn gedrehten Position.</span><span class="sxs-lookup"><span data-stu-id="2dc28-165">For yaw, a value of -1.0 corresponds to the most counterclockwise, twisted position, while a value of 1.0 corresponds to the most clockwise position.</span></span>

<span data-ttu-id="2dc28-166">Auf allen Achsen ist der Wert ungefähr 0,0, wenn sich der Joystick in der Mittelstellung befindet, aber normalerwiese weicht der genaue Wert etwas davon ab, sogar in aufeinanderfolgenden Messwerten.</span><span class="sxs-lookup"><span data-stu-id="2dc28-166">In all axes, the value is approximately 0.0 when the joystick is in the center position, but it's normal for the precise value to vary, even between subsequent readings.</span></span> <span data-ttu-id="2dc28-167">Strategien zur Minimierung dieser Abweichung werden weiter unten in diesem Abschnitt behandelt.</span><span class="sxs-lookup"><span data-stu-id="2dc28-167">Strategies for mitigating this variation are discussed later in this section.</span></span>

<span data-ttu-id="2dc28-168">Der Wert beim Rollen des Joysticks wird aus der [FlightStickReading.Roll](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Roll)-Eigenschaft gelesen, der Wert beim Nicken aus der [FlightStickReading.Pitch](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Pitch)-Eigenschaft und der Wert beim Gieren aus der [FlightStickReading.Yaw](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Yaw)-Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="2dc28-168">The value of the joystick's roll is read from the [FlightStickReading.Roll](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Roll) property, the value of the pitch is read from the [FlightStickReading.Pitch](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Pitch) property, and the value of the yaw is read from the [FlightStickReading.Yaw](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Yaw) property:</span></span>

```cpp
// Each variable will contain a value between -1.0 and 1.0.
float roll = reading.Roll;
float pitch = reading.Pitch;
float yaw = reading.Yaw;
```

<span data-ttu-id="2dc28-169">Sie werden feststellen, dass die gelesenen Joystickwerte nicht zuverlässig einen neutralen 0,0-Wert liefern, wenn sich der Joystick in der Mittelstellung (und damit im Ruhezustand) befindet. Stattdessen erhalten Sie verschiedene Näherungswerte für 0,0, wann immer der Joystick bewegt wurde und wieder in die Mittelstellung zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="2dc28-169">When reading the joystick values, you'll notice that they don't reliably produce a neutral reading of 0.0 when the joystick is at rest in the center position; instead, they'll produce different values near 0.0 each time the joystick is moved and returned to the center position.</span></span> <span data-ttu-id="2dc28-170">Zur Kompensierung dieser Abweichungen können Sie einen kleinen _inaktiven Bereich_ implementieren (also einen zu ignorieRendern Wertebereich nahe der idealen Mittelposition).</span><span class="sxs-lookup"><span data-stu-id="2dc28-170">To mitigate these variations, you can implement a small _deadzone_, which is a range of values near the ideal center position that are ignored.</span></span>

<span data-ttu-id="2dc28-171">Zur Implementierung eines inaktiven Bereichs können Sie beispielsweise ermitteln, wie weit sich der Joystick von der Mittelposition entfernt hat, und dabei die Werte ignorieren, die eine bestimmte, von Ihnen gewählte Entfernung unterschreiten.</span><span class="sxs-lookup"><span data-stu-id="2dc28-171">One way to implement a deadzone is to determine how far the joystick has moved from the center, and ignore readings that are nearer than some distance you choose.</span></span> <span data-ttu-id="2dc28-172">Die grobe Entfernung kann mit dem Satz des Pythagoras berechnet werden. Die Berechnung ist allerdings nicht exakt, da die Joystickwerte im Grunde polar und nicht planar sind.</span><span class="sxs-lookup"><span data-stu-id="2dc28-172">You can compute the distance roughly&mdash;it's not exact because joystick readings are essentially polar, not planar, values&mdash;just by using the Pythagorean theorem.</span></span> <span data-ttu-id="2dc28-173">Dadurch entsteht ein radialer inaktiver Bereich.</span><span class="sxs-lookup"><span data-stu-id="2dc28-173">This produces a radial deadzone.</span></span>

<span data-ttu-id="2dc28-174">Das folgende Beispiel veranschaulicht einen einfachen radialen inaktiven Bereich mit dem Satz des Pythagoras:</span><span class="sxs-lookup"><span data-stu-id="2dc28-174">The following example demonstrates a basic radial deadzone using the Pythagorean theorem:</span></span>

```cpp
// Choose a deadzone. Readings inside this radius are ignored.
const float deadzoneRadius = 0.1f;
const float deadzoneSquared = deadzoneRadius * deadzoneRadius;

// Pythagorean theorem: For a right triangle, hypotenuse^2 = (opposite side)^2 + (adjacent side)^2
float oppositeSquared = pitch * pitch;
float adjacentSquared = roll * roll;

// Accept and process input if true; otherwise, reject and ignore it.
if ((oppositeSquared + adjacentSquared) < deadzoneSquared)
{
    // Input accepted, process it.
}
```

### <a name="reading-the-buttons-and-hat-switch"></a><span data-ttu-id="2dc28-175">Lesen der Tasten und des Mehrwegeschalters</span><span class="sxs-lookup"><span data-stu-id="2dc28-175">Reading the buttons and hat switch</span></span>

<span data-ttu-id="2dc28-176">Jede der beiden Feuern-Tasten des Steuerknüppels liefert einen digitalen Wert, der angibt, ob die Taste gedrückt ist (unten) oder nicht gedrückt (oben) ist.</span><span class="sxs-lookup"><span data-stu-id="2dc28-176">Each of the flight stick's two fire buttons provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="2dc28-177">Aus Effizienzgründen werden die Werte der Tasten nicht als einzelne boolesche Werte dargestellt, sondern in einem einzelnen Bitfeld zusammengefasst, das durch die Enumeration [FlightStickButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickbuttons) dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="2dc28-177">For efficiency, button readings aren't represented as individual boolean values&mdash;instead, they're all packed into a single bitfield that's represented by the [FlightStickButtons](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickbuttons) enumeration.</span></span> <span data-ttu-id="2dc28-178">Darüber hinaus bietet der 8-Wegeschalter eine in einem einzelnen Bitfeld zusammengefasste Richtung, die durch die Enumeration [GameControllerSwitchPosition](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerswitchposition) dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="2dc28-178">In addition, the 8-way hat switch provides a direction packed into a single bitfield that's represented by the [GameControllerSwitchPosition](https://docs.microsoft.com/uwp/api/windows.gaming.input.gamecontrollerswitchposition) enumeration.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc28-179">Steuerknüppel sind mit zusätzlichen Tasten für die Benutzeroberflächennavigation ausgestattet, zum Beispiel mit den Tasten **Ansicht** und **Menü**.</span><span class="sxs-lookup"><span data-stu-id="2dc28-179">Flight sticks are equipped with additional buttons used for UI navigation such as the **View** and **Menu** buttons.</span></span> <span data-ttu-id="2dc28-180">Diese Tasten sind nicht in der Enumeration `FlightStickButtons` enthalten und können nur gelesen werden, wenn auf den Steuerknüppel als Benutzeroberflächen-Navigationsgerät zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="2dc28-180">These buttons are not part of the `FlightStickButtons` enumeration and can only be read by accessing the flight stick as a UI navigation device.</span></span> <span data-ttu-id="2dc28-181">Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md).</span><span class="sxs-lookup"><span data-stu-id="2dc28-181">For more information, see [UI navigation controller](ui-navigation-controller.md).</span></span>

<span data-ttu-id="2dc28-182">Die Tastenwerte werden aus der [FlightStickReading.Buttons](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Buttons)-Eigenschaft gelesen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-182">The button values are read from the [FlightStickReading.Buttons](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.Buttons) property.</span></span> <span data-ttu-id="2dc28-183">Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind,</span><span class="sxs-lookup"><span data-stu-id="2dc28-183">Because this property is a bitfield, bitwise masking is used to isolate the value of the button that you're interested in.</span></span> <span data-ttu-id="2dc28-184">Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).</span><span class="sxs-lookup"><span data-stu-id="2dc28-184">The button is pressed (down) when the corresponding bit is set; otherwise, it's released (up).</span></span>

<span data-ttu-id="2dc28-185">Im folgenden Beispiel wird ermittelt, ob die Taste **FirePrimary** gedrückt ist:</span><span class="sxs-lookup"><span data-stu-id="2dc28-185">The following example determines whether the **FirePrimary** button is pressed:</span></span>

```cpp
if (FlightStickButtons::FirePrimary == (reading.Buttons & FlightStickButtons::FirePrimary))
{
    // FirePrimary is pressed.
}
```

<span data-ttu-id="2dc28-186">Im folgenden Beispiel wird ermittelt, ob die Taste **FirePrimary** nicht gedrückt ist:</span><span class="sxs-lookup"><span data-stu-id="2dc28-186">The following example determines whether the **FirePrimary** button is released:</span></span>

```cpp
if (FlightStickButtons::None == (reading.Buttons & FlightStickButtons::FirePrimary))
{
    // FirePrimary is released (not pressed).
}
```

<span data-ttu-id="2dc28-187">In einigen Fällen möchten Sie möglicherweise ermitteln, ob eine Taste von „Gedrückt“ zu „Nicht gedrückt“ oder von „Nicht gedrückt“ zu „Gedrückt“ wechselt, ob mehrere Tasten gedrückt oder nicht gedrückt werden oder ob verschiedene Tasten in einer bestimmten Weise angeordnet sind – einige sind gedrückt, andere nicht.</span><span class="sxs-lookup"><span data-stu-id="2dc28-187">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="2dc28-188">Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) sowie unter [Erkennen komplexer Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="2dc28-188">For information on how to detect each of these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

<span data-ttu-id="2dc28-189">Der Wert des Mehrwegeschalters wird aus der [FlightStickReading.HatSwitch](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.HatSwitch)-Eigenschaft gelesen.</span><span class="sxs-lookup"><span data-stu-id="2dc28-189">The hat switch value is read from the [FlightStickReading.HatSwitch](https://docs.microsoft.com/uwp/api/windows.gaming.input.flightstickreading.HatSwitch) property.</span></span> <span data-ttu-id="2dc28-190">Da diese Eigenschaft ebenfalls ein Bitfeld ist, wird erneut die bitweise Maskierung verwendet, um die Position des Mehrwegeschalters zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="2dc28-190">Because this property is also a bitfield, bitwise masking is again used to isolate the position of the hat switch.</span></span>

<span data-ttu-id="2dc28-191">Im folgenden Beispiel wird ermittelt, ob sich der Mehrwegeschalter in der oberen Stellung befindet:</span><span class="sxs-lookup"><span data-stu-id="2dc28-191">The following example determines whether the hat switch is in the up position:</span></span>

```cpp
if (GameControllerSwitchPosition::Up == (reading.HatSwitch & GameControllerSwitchPosition::Up))
{
    // The hat switch is in the up position.
}
```

<span data-ttu-id="2dc28-192">Im folgenden Beispiel wird ermittelt, ob sich der Mehrwegeschalter in der Mittelstellung befindet:</span><span class="sxs-lookup"><span data-stu-id="2dc28-192">The following example determines if the hat switch is in the center position:</span></span>

```cpp
if (GameControllerSwitchPosition::Center == (reading.HatSwitch & GameControllerSwitchPosition::Center))
{
    // The hat switch is in the center position.
}
```

<!--## Run the InputInterfacingUWP sample

The [InputInterfacingUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) demonstrates how to use flight sticks and different kinds of input devices in tandem, as well as how these input devices behave as UI navigation controllers.-->

## <a name="see-also"></a><span data-ttu-id="2dc28-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2dc28-193">See also</span></span>

* [<span data-ttu-id="2dc28-194">Windows.Gaming.Input.UINavigationController-Klasse</span><span class="sxs-lookup"><span data-stu-id="2dc28-194">Windows.Gaming.Input.UINavigationController class</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.uinavigationcontroller)
* [<span data-ttu-id="2dc28-195">Windows.Gaming.Input.IGameController-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="2dc28-195">Windows.Gaming.Input.IGameController interface</span></span>](https://docs.microsoft.com/uwp/api/windows.gaming.input.igamecontroller)
* [<span data-ttu-id="2dc28-196">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="2dc28-196">Input practices for games</span></span>](input-practices-for-games.md)