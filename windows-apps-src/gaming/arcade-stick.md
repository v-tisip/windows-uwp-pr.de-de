---
title: Arcade-Joystick
description: Verwenden Sie die Windows.Gaming.Input-Arcade-Joystick-APIs zum Erkennen und Lesen von Arcade-Joysticks.
ms.assetid: 2E52232F-3014-4C8C-B39D-FAC478BA3E01
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Arcade-Joysticks, Eingabe
ms.localizationpriority: medium
ms.openlocfilehash: 6f9e3ff29dfb17b6e2a07df52153013b5266206e
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8872401"
---
# <a name="arcade-stick"></a><span data-ttu-id="f9edd-104">Arcade-Joystick</span><span class="sxs-lookup"><span data-stu-id="f9edd-104">Arcade stick</span></span>

<span data-ttu-id="f9edd-105">Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Arcade-Joysticks mittels [Windows.Gaming.Input.ArcadeStick][arcadestick] und verwandter APIs für die universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f9edd-105">This page describes the basics of programming for Xbox One arcade sticks using [Windows.Gaming.Input.ArcadeStick][arcadestick] and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="f9edd-106">Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:</span><span class="sxs-lookup"><span data-stu-id="f9edd-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="f9edd-107">Erstellen einer Liste der verbundenen Arcade-Joysticks und ihrer Benutzer</span><span class="sxs-lookup"><span data-stu-id="f9edd-107">how to gather a list of connected arcade sticks and their users</span></span>
* <span data-ttu-id="f9edd-108">Ermitteln, ob ein Arcade-Joystick hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="f9edd-108">how to detect that an arcade stick has been added or removed</span></span>
* <span data-ttu-id="f9edd-109">Lesen der Eingabe von einem oder mehreren Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-109">how to read input from one or more arcade sticks</span></span>
* <span data-ttu-id="f9edd-110">Verhalten von Arcade-Joysticks als Benutzeroberflächen-Navigationsgeräte</span><span class="sxs-lookup"><span data-stu-id="f9edd-110">how arcade sticks behave as UI navigation devices</span></span>

## <a name="arcade-stick-overview"></a><span data-ttu-id="f9edd-111">Übersicht über Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-111">Arcade stick overview</span></span>

<span data-ttu-id="f9edd-112">Bei Arcade-Joysticks handelt es sich um Eingabegeräte, die den Eindruck klassischer Arcade-Automaten vermitteln und aufgrund ihrer äußerst präzisen digitalen Steuerelemente geschätzt werden.</span><span class="sxs-lookup"><span data-stu-id="f9edd-112">Arcade sticks are input devices valued for reproducing the feel of stand-up arcade machines and for their high-precision digital controls.</span></span> <span data-ttu-id="f9edd-113">Arcade-Joysticks sind das ideale Eingabegerät für Kampfspiele und andere Spiele im Arcade-Stil und eignen sich für alle Spiele mit komplett digitaler Steuerung.</span><span class="sxs-lookup"><span data-stu-id="f9edd-113">Arcade sticks are the perfect input device for head-to-head-fighting and other arcade-style games, and are suitable for any game that works well with all-digital controls.</span></span> <span data-ttu-id="f9edd-114">Arcade-Joysticks werden in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input][] unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f9edd-114">Arcade sticks are supported in Windows 10 and Xbox One UWP apps by the [Windows.Gaming.Input][] namespace.</span></span>

<span data-ttu-id="f9edd-115">Xbox One-Arcade-Joysticks sind mit einem digitalen 8-Wege-Joystick, **sechs Aktionsschaltflächen (A1 a6 in der Abbildung unten dargestellt)** und zwei **spezielle** Schaltflächen (dargestellt als S1 und S2); ausgestattet. Sie sind reine digitale Eingabegeräte, die keine analoge Steuerung oder Vibration unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f9edd-115">Xbox One arcade sticks are equipped with an 8-way digital joystick, six **Action** buttons (represented as A1-A6 in the image below), and two **Special** buttons (represented as S1 and S2); they're all-digital input devices that don't support analog controls or vibration.</span></span> <span data-ttu-id="f9edd-116">Xbox One-Arcade-Joysticks sind auch mit \*\* **Ansichts-** und\*\* Schaltflächen zur Unterstützung der Benutzeroberflächennavigation ausgestattet, aber sie sind nicht für die Unterstützung von Befehlen im Spiel vorgesehen und können nicht ohne weiteres als Joystick-Tasten zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="f9edd-116">Xbox One arcade sticks are also equipped with **View** and **Menu** buttons used to support UI navigation but they're not intended to support gameplay commands and can't be readily accessed as joystick buttons.</span></span>

![Arcade-Joystick mit 4-Wege-Joystick, 6 Aktionsschaltflächen (A1 A6) und 2 spezielle Schaltflächen (S1 und S2)](images/arcade-stick-1.png)

### <a name="ui-navigation"></a><span data-ttu-id="f9edd-118">Benutzeroberflächennavigation</span><span class="sxs-lookup"><span data-stu-id="f9edd-118">UI navigation</span></span>

<span data-ttu-id="f9edd-119">Um den Aufwand für die Unterstützung vieler unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="f9edd-119">In order to ease the burden of supporting many different input devices for user interface navigation and to encourage consistency between games and devices, most _physical_ input devices simultaneously act as a separate _logical_ input device called a [UI navigation controller](ui-navigation-controller.md).</span></span> <span data-ttu-id="f9edd-120">Der Benutzeroberflächen-Navigationscontroller stellt über verschiedene Eingabegeräte hinweg ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle bereit.</span><span class="sxs-lookup"><span data-stu-id="f9edd-120">The UI navigation controller provides a common vocabulary for UI navigation commands across input devices.</span></span>

<span data-ttu-id="f9edd-121">Als Benutzeroberflächen-navigationscontroller ordnen Sie Arcade-Joysticks die [erforderlichen Satz](ui-navigation-controller.md#required-set) von Navigationsbefehlen dem Joystick und Schaltflächen **Ansicht**, **Menü**, **Aktion 1**und **2 Aktion** .</span><span class="sxs-lookup"><span data-stu-id="f9edd-121">As a UI navigation controller, arcade sticks map the [required set](ui-navigation-controller.md#required-set) of navigation commands to the joystick and **View**, **Menu**, **Action 1**, and **Action 2** buttons.</span></span>

| <span data-ttu-id="f9edd-122">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="f9edd-122">Navigation command</span></span> | <span data-ttu-id="f9edd-123">Eingabe des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-123">Arcade stick input</span></span>  |
| ------------------:| ------------------- |
|                 <span data-ttu-id="f9edd-124">Nach oben</span><span class="sxs-lookup"><span data-stu-id="f9edd-124">Up</span></span> | <span data-ttu-id="f9edd-125">Joystick nach oben</span><span class="sxs-lookup"><span data-stu-id="f9edd-125">Stick up</span></span>            |
|               <span data-ttu-id="f9edd-126">Nach unten</span><span class="sxs-lookup"><span data-stu-id="f9edd-126">Down</span></span> | <span data-ttu-id="f9edd-127">Joystick nach unten</span><span class="sxs-lookup"><span data-stu-id="f9edd-127">Stick down</span></span>          |
|               <span data-ttu-id="f9edd-128">Nach links</span><span class="sxs-lookup"><span data-stu-id="f9edd-128">Left</span></span> | <span data-ttu-id="f9edd-129">Joystick nach links</span><span class="sxs-lookup"><span data-stu-id="f9edd-129">Stick left</span></span>          |
|              <span data-ttu-id="f9edd-130">Nach rechts</span><span class="sxs-lookup"><span data-stu-id="f9edd-130">Right</span></span> | <span data-ttu-id="f9edd-131">Joystick nach rechts</span><span class="sxs-lookup"><span data-stu-id="f9edd-131">Stick right</span></span>         |
|               <span data-ttu-id="f9edd-132">Ansicht</span><span class="sxs-lookup"><span data-stu-id="f9edd-132">View</span></span> | <span data-ttu-id="f9edd-133">Ansicht-Taste</span><span class="sxs-lookup"><span data-stu-id="f9edd-133">View button</span></span>         |
|               <span data-ttu-id="f9edd-134">Menü</span><span class="sxs-lookup"><span data-stu-id="f9edd-134">Menu</span></span> | <span data-ttu-id="f9edd-135">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="f9edd-135">Menu button</span></span>         |
|             <span data-ttu-id="f9edd-136">Annehmen</span><span class="sxs-lookup"><span data-stu-id="f9edd-136">Accept</span></span> | <span data-ttu-id="f9edd-137">Taste für Aktion1</span><span class="sxs-lookup"><span data-stu-id="f9edd-137">Action 1 button</span></span>     |
|             <span data-ttu-id="f9edd-138">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="f9edd-138">Cancel</span></span> | <span data-ttu-id="f9edd-139">Taste für Aktion2</span><span class="sxs-lookup"><span data-stu-id="f9edd-139">Action 2 button</span></span>     |

<span data-ttu-id="f9edd-140">Arcade-Joysticks ordnen keines der [optionalen Sätze](ui-navigation-controller.md#optional-set) mit Navigationsbefehlen zu.</span><span class="sxs-lookup"><span data-stu-id="f9edd-140">Arcade sticks don't map any of the [optional set](ui-navigation-controller.md#optional-set) of navigation commands.</span></span>

## <a name="detect-and-track-arcade-sticks"></a><span data-ttu-id="f9edd-141">Ermitteln und Nachverfolgen von Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-141">Detect and track arcade sticks</span></span>

<span data-ttu-id="f9edd-142">Erkennen und Tracking Arcade Steuerknüppeln funktioniert auf genau die gleiche Weise wie für Gamepads, außer bei der [ArcadeStick][] -Klasse anstelle der [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f9edd-142">Detecting and tracking arcade sticks works in exactly the same way as it does for gamepads, except with the [ArcadeStick][] class instead of the [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad) class.</span></span> <span data-ttu-id="f9edd-143">Weitere Informationen finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).</span><span class="sxs-lookup"><span data-stu-id="f9edd-143">See [Gamepad and vibration](gamepad-and-vibration.md) for more information.</span></span>

<!-- Arcade sticks are managed by the system, therefore you don't have to create or initialize them. The system provides a list of connected arcades sticks and events to notify you when an arcade stick is added or removed.

### The arcade sticks list

The [ArcadeStick][] class provides a static property, [ArcadeSticks][], which is a read-only list of arcade sticks that are currently connected. Because you might only be interested in some of the connected arcade sticks, it's recommended that you maintain your own collection instead of accessing them through the `ArcadeSticks` property.

The following example copies all connected arcade sticks into a new collection. Note that because other threads in the background will be accessing this collection (in the [ArcadeStickAdded][] and [ArcadeStickRemoved][] events), you need to place a lock around any code that reads or updates the collection.

```cpp
auto myArcadeSticks = ref new Vector<ArcadeStick^>();
critical_section myLock{};

for (auto arcadeStick : ArcadeStick::ArcadeSticks)
{
    // Check if the arcade stick is already in myArcadeSticks; if it isn't, add
    // it.
    critical_section::scoped_lock lock{ myLock };
    auto it = std::find(begin(myArcadeSticks), end(myArcadeSticks), arcadeStick);

    if (it == end(myArcadeSticks))
    {
        // This code assumes that you're interested in all arcade sticks.
        myArcadeSticks->Append(arcadeStick);
    }
}
```

### Adding and removing arcade sticks

When an arcade stick is added or removed the [ArcadeStickAdded][] and [ArcadeStickRemoved][] events are raised. You can register handlers for these events to keep track of the arcade sticks that are currently connected.

The following example starts tracking an arcade stick that's been added.

```cpp
ArcadeStick::ArcadeStickAdded += ref new EventHandler<ArcadeStick^>(Platform::Object^, ArcadeStick^ args)
{
    // Check if the just-added arcade stick is already in myArcadeSticks; if it
    // isn't, add it.
    critical_section::scoped_lock lock{ myLock };
    auto it = std::find(begin(myGamepads), end(myGamepads), args);

    // This code assumes that you're interested in all new arcade sticks.
    myArcadeSticks->Append(args);
}
```

The following example stops tracking an arcade stick that's been removed.

```cpp
ArcadeStick::ArcadeStickRemoved += ref new EventHandler<ArcadeStick^>(Platform::Object^, ArcadeStick^ args)
{
    unsigned int indexRemoved;

    if(myArcadeSticks->IndexOf(args, &indexRemoved))
    {
        myArcadeSticks->RemoveAt(indexRemoved);
    }
}
```

### Users and headsets

Each arcade stick can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features. To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md). -->

## <a name="reading-the-arcade-stick"></a><span data-ttu-id="f9edd-144">Lesen des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-144">Reading the arcade stick</span></span>

<span data-ttu-id="f9edd-145">Nachdem Sie den Arcade-Joystick identifiziert haben, für den Sie sich interessieren, können Sie Eingaben von ihm erfassen.</span><span class="sxs-lookup"><span data-stu-id="f9edd-145">After you identify the arcade stick that you're interested in, you're ready to gather input from it.</span></span> <span data-ttu-id="f9edd-146">Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Arcade-Joysticks Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="f9edd-146">However, unlike some other kinds of input that you might be used to, arcade sticks don't communicate state-change by raising events.</span></span> <span data-ttu-id="f9edd-147">Stattdessen müssen Sie regelmäßig ihren aktuellen Status lesen, indem Sie sie _abfragen_.</span><span class="sxs-lookup"><span data-stu-id="f9edd-147">Instead, you take regular readings of their current state by _polling_ them.</span></span>

### <a name="polling-the-arcade-stick"></a><span data-ttu-id="f9edd-148">Abfragen des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="f9edd-148">Polling the arcade stick</span></span>

<span data-ttu-id="f9edd-149">Beim Abfragen wird ein Snapshot des Arcade-Joysticks zu einem bestimmten Zeitpunkt erstellt.</span><span class="sxs-lookup"><span data-stu-id="f9edd-149">Polling captures a snapshot of the arcade stick at a precise point in time.</span></span> <span data-ttu-id="f9edd-150">Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="f9edd-150">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven; it's also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="f9edd-151">Sie fragen einen Arcade-Joystick ab, indem Sie [GetCurrentReading][] aufrufen. Diese Funktion gibt ein [ArcadeStickReading][]-Element zurück, das den Zustand des Arcade-Joysticks enthält.</span><span class="sxs-lookup"><span data-stu-id="f9edd-151">You poll an arcade stick by calling [GetCurrentReading][]; this function returns an [ArcadeStickReading][] that contains the state of the arcade stick.</span></span>

<span data-ttu-id="f9edd-152">Im folgenden Beispiel wird der aktuelle Zustand eines Arcade-Joysticks abgefragt.</span><span class="sxs-lookup"><span data-stu-id="f9edd-152">The following example polls an arcade stick for its current state.</span></span>

```cpp
auto arcadestick = myArcadeSticks[0];

ArcadeStickReading reading = arcadestick->GetCurrentReading();
```

<span data-ttu-id="f9edd-153">Zusätzlich zum Zustand des Arcade-Joysticks enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="f9edd-153">In addition to the arcade stick state, each reading includes a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="f9edd-154">Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Werte oder zum Zeitpunkt der Spielsimulation herzustellen.</span><span class="sxs-lookup"><span data-stu-id="f9edd-154">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="reading-the-buttons"></a><span data-ttu-id="f9edd-155">Lesen der Tasten</span><span class="sxs-lookup"><span data-stu-id="f9edd-155">Reading the buttons</span></span>

<span data-ttu-id="f9edd-156">Die Schaltflächen für Arcade-Joystick&mdash;die vier Richtungen des der Joystick, **sechs Aktionsschaltflächen** und zwei **spezielle** Schaltflächen&mdash;liefert einen digitalen Wert, der angibt, ob sie gedrückt (unten) oder freigegeben (oben).</span><span class="sxs-lookup"><span data-stu-id="f9edd-156">Each of the arcade stick buttons&mdash;the four directions of the joystick, six **Action** buttons, and two **Special** buttons&mdash;provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="f9edd-157">Aus Effizienzgründen werden nicht Effizienzgründen als einzelne boolesche Werte dargestellt. Stattdessen können sie alle in einem einzelnen Bitfeld verpackt, die von der [ArcadeStickButtons][] -Enumeration dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="f9edd-157">For efficiency, button readings aren't represented as individual boolean values; instead, they're all packed into a single bitfield that's represented by the [ArcadeStickButtons][] enumeration.</span></span>

> [!NOTE]
> <span data-ttu-id="f9edd-158">Arcade-Joysticks besitzen zusätzliche Tasten für die Benutzeroberflächennavigation, z. B. die \*\* **Ansichts-** und\*\* Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f9edd-158">Arcade sticks are equipped with additional buttons used for UI navigation such as the **View** and **Menu** buttons.</span></span> <span data-ttu-id="f9edd-159">Diese Tasten sind nicht in der Enumeration `ArcadeStickButtons` enthalten und können nur gelesen werden, wenn auf den Arcade-Joystick als Benutzeroberflächen-Navigationsgerät zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="f9edd-159">These buttons are not a part of the `ArcadeStickButtons` enumeration and can only be read by accessing the arcade stick as a UI navigation device.</span></span> <span data-ttu-id="f9edd-160">Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationsgerät](ui-navigation-controller.md).</span><span class="sxs-lookup"><span data-stu-id="f9edd-160">For more information, see [UI Navigation Device](ui-navigation-controller.md).</span></span>

<span data-ttu-id="f9edd-161">Die Schaltflächenwerte werden von der `Buttons`-Eigenschaft der [ArcadeStickReading][]-Struktur gelesen.</span><span class="sxs-lookup"><span data-stu-id="f9edd-161">The button values are read from the `Buttons` property of the [ArcadeStickReading][] structure.</span></span> <span data-ttu-id="f9edd-162">Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind,</span><span class="sxs-lookup"><span data-stu-id="f9edd-162">Because this property is a bitfield, bitwise masking is used to isolate the value of the button that you're interested in.</span></span> <span data-ttu-id="f9edd-163">Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).</span><span class="sxs-lookup"><span data-stu-id="f9edd-163">The button is pressed (down) when the corresponding bit is set; otherwise, it's released (up).</span></span>

<span data-ttu-id="f9edd-164">Im folgenden Beispiel wird bestimmt, ob die Taste für **Aktion 1** gedrückt ist.</span><span class="sxs-lookup"><span data-stu-id="f9edd-164">The following example determines whether the **Action 1** button is pressed.</span></span>

```cpp
if (ArcadeStickButtons::Action1 == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is pressed
}
```

<span data-ttu-id="f9edd-165">Im folgenden Beispiel wird bestimmt, ob die Taste für **Aktion 1** losgelassen wurde.</span><span class="sxs-lookup"><span data-stu-id="f9edd-165">The following example determines whether the **Action 1** button is released.</span></span>

```cpp
if (ArcadeStickButtons::None == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is released (not pressed)
}
```

<span data-ttu-id="f9edd-166">In einigen Fällen möchten Sie vielleicht ermitteln, ob eine Taste von „gedrückt“ zu „nicht gedrückt“ bzw. umgekehrt wechselt, oder ob mehrere Tasten gedrückt bzw. nicht gedrückt oder in bestimmter Weise angeordnet sind&mdash;einige gedrückt, andere nicht.</span><span class="sxs-lookup"><span data-stu-id="f9edd-166">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="f9edd-167">Weitere Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) und [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="f9edd-167">For information on how to detect these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

## <a name="run-the-inputinterfacing-sample"></a><span data-ttu-id="f9edd-168">Ausführen des InputInterfacing-Beispiels</span><span class="sxs-lookup"><span data-stu-id="f9edd-168">Run the InputInterfacing sample</span></span>

<span data-ttu-id="f9edd-169">Das [InputInterfacingUWP-Beispiel _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) veranschaulicht, wie Arcade-Joysticks und verschiedene Arten von Eingabegeräten zusammen verwendet werden und wie diese Eingabegeräte sich bei der Verwendung als Benutzeroberflächen-Navigationcontrollern verhalten.</span><span class="sxs-lookup"><span data-stu-id="f9edd-169">The [InputInterfacingUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) demonstrates how to use arcade sticks and different kinds of input devices in tandem, as well as how these input devices behave as UI navigation controllers.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9edd-170">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f9edd-170">See also</span></span>

* [<span data-ttu-id="f9edd-171">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="f9edd-171">Windows.Gaming.Input.UINavigationController</span></span>][]
* [<span data-ttu-id="f9edd-172">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="f9edd-172">Windows.Gaming.Input.IGameController</span></span>][]
* [<span data-ttu-id="f9edd-173">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="f9edd-173">Input practices for games</span></span>](input-practices-for-games.md)

[<span data-ttu-id="f9edd-174">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="f9edd-174">Windows.Gaming.Input</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[<span data-ttu-id="f9edd-175">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="f9edd-175">Windows.Gaming.Input.IGameController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[<span data-ttu-id="f9edd-176">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="f9edd-176">Windows.Gaming.Input.UINavigationController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[<span data-ttu-id="f9edd-177">arcadestick</span><span class="sxs-lookup"><span data-stu-id="f9edd-177">arcadestick</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.aspx
[arcadesticks]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadesticks.aspx
[arcadestickadded]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickadded.aspx
[arcadestickremoved]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickremoved.aspx
[<span data-ttu-id="f9edd-178">getcurrentreading</span><span class="sxs-lookup"><span data-stu-id="f9edd-178">getcurrentreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.getcurrentreading.aspx
[<span data-ttu-id="f9edd-179">arcadestickreading</span><span class="sxs-lookup"><span data-stu-id="f9edd-179">arcadestickreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickreading.aspx
[<span data-ttu-id="f9edd-180">arcadestickbuttons</span><span class="sxs-lookup"><span data-stu-id="f9edd-180">arcadestickbuttons</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickbuttons.aspx
