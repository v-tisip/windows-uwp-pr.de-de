---
author: mithom
title: Arcade-Joystick
description: Verwenden Sie die Windows.Gaming.Input-Arcade-Joystick-APIs zum Erkennen und Lesen von Arcade-Joysticks.
ms.assetid: 2E52232F-3014-4C8C-B39D-FAC478BA3E01
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Arcade-Joysticks, Eingabe
ms.openlocfilehash: b0411dcf1fd75ec7dc31d29a39e95f5c26073953
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233742"
---
# <a name="arcade-stick"></a><span data-ttu-id="5d5b3-104">Arcade-Joystick</span><span class="sxs-lookup"><span data-stu-id="5d5b3-104">Arcade stick</span></span>

<span data-ttu-id="5d5b3-105">Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Arcade-Joysticks mittels [Windows.Gaming.Input.ArcadeStick][arcadestick] und verwandter APIs für die universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-105">This page describes the basics of programming for Xbox One arcade sticks using [Windows.Gaming.Input.ArcadeStick][arcadestick] and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="5d5b3-106">Auf dieser Seite erhalten Sie Informationen zu folgenden Vorgängen:</span><span class="sxs-lookup"><span data-stu-id="5d5b3-106">By reading this page, you'll learn:</span></span>
* <span data-ttu-id="5d5b3-107">Erstellen einer Liste der verbundenen Arcade-Joysticks und ihrer Benutzer</span><span class="sxs-lookup"><span data-stu-id="5d5b3-107">how to gather a list of connected arcade sticks and their users</span></span>
* <span data-ttu-id="5d5b3-108">Ermitteln, ob ein Arcade-Joystick hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="5d5b3-108">how to detect that an arcade stick has been added or removed</span></span>
* <span data-ttu-id="5d5b3-109">Lesen der Eingabe von einem oder mehreren Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-109">how to read input from one or more arcade sticks</span></span>
* <span data-ttu-id="5d5b3-110">Verhalten von Arcade-Joysticks als Navigationsgerät</span><span class="sxs-lookup"><span data-stu-id="5d5b3-110">how arcade sticks behave as a navigation device</span></span>


## <a name="arcade-stick-overview"></a><span data-ttu-id="5d5b3-111">Übersicht über Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-111">Arcade stick overview</span></span>

<span data-ttu-id="5d5b3-112">Bei Arcade-Joysticks handelt es sich um Eingabegeräte, die den Eindruck klassischer Arcade-Automaten vermitteln und aufgrund ihrer äußerst präzisen digitalen Steuerelemente geschätzt werden.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-112">Arcade sticks are input devices valued for reproducing the feel of stand-up arcade machines and for their high-precision digital controls.</span></span> <span data-ttu-id="5d5b3-113">Arcade-Joysticks sind das ideale Eingabegerät für Kampfspiele und andere Spiele im Arcade-Stil und eignen sich für alle Spiele mit komplett digitaler Steuerung.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-113">Arcade sticks are the perfect input device for head-to-head-fighting and other arcade-style games, and are suitable for any game that works well with all-digital controls.</span></span> <span data-ttu-id="5d5b3-114">Arcade-Joysticks werden in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input][] unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-114">Arcade sticks are supported in Windows 10 and Xbox One UWP apps by the [Windows.Gaming.Input][] namespace.</span></span>

<span data-ttu-id="5d5b3-115">Xbox One-Arcade-Joysticks sind mit einem digitalen 8-Wege-Joystick, sechs **Aktionstasten** und zwei **Sondertasten** ausgestattet. Es handelt sich bei ihnen um vollständig digitale Eingabegeräte, die keine analoge Steuerung oder Vibration unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-115">Xbox One arcade sticks are equipped with an 8-way digital joystick, six **action** buttons, and two **special** buttons; they're all-digital input devices that don't support analog controls or vibration.</span></span> <span data-ttu-id="5d5b3-116">Xbox One-Arcade-Joysticks verfügen außerdem über Tasten für **Ansicht** und **Menü**, um die Benutzeroberflächennavigation zu unterstützen. Diese Tasten sind jedoch nicht für die Unterstützung von Befehlen im Spiel vorgesehen und können nicht direkt als Joystick-Tasten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-116">Xbox One arcade sticks are also equipped with **view** and **menu** buttons used to support UI navigation but they're not intended to support gameplay commands and can't be readily accessed as joystick buttons.</span></span>

### <a name="ui-navigation"></a><span data-ttu-id="5d5b3-117">Benutzeroberflächennavigation</span><span class="sxs-lookup"><span data-stu-id="5d5b3-117">UI navigation</span></span>

<span data-ttu-id="5d5b3-118">Um den Aufwand für die Unterstützung vieler unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-118">In order to ease the burden of supporting many different input devices for user interface navigation and to encourage consistency between games and devices, most _physical_ input devices simultaneously act as a separate _logical_ input device called a [UI navigation controller](ui-navigation-controller.md).</span></span> <span data-ttu-id="5d5b3-119">Der Benutzeroberflächen-Navigationscontroller stellt über verschiedene Eingabegeräte hinweg ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle bereit.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-119">The UI navigation controller provides a common vocabulary for UI navigation commands across input devices.</span></span>

<span data-ttu-id="5d5b3-120">Als Benutzeroberflächen-Navigationscontroller weisen Arcade-Joysticks den [erforderlichen Satz](ui-navigation-controller.md#required-set) mit Navigationsbefehlen dem Joystick und den Tasten **Ansicht**, **Menü**, **Aktion 1** und **Aktion 2** zu.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-120">As a UI navigation controller, arcade sticks map the [required set](ui-navigation-controller.md#required-set) of navigation commands to the joystick and **view**, **menu**, **action 1**, and **action 2** buttons.</span></span>

| <span data-ttu-id="5d5b3-121">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="5d5b3-121">Navigation command</span></span> | <span data-ttu-id="5d5b3-122">Eingabe des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-122">Arcade stick input</span></span>  |
| ------------------:| ------------------- |
|                 <span data-ttu-id="5d5b3-123">Nach oben</span><span class="sxs-lookup"><span data-stu-id="5d5b3-123">Up</span></span> | <span data-ttu-id="5d5b3-124">Joystick nach oben</span><span class="sxs-lookup"><span data-stu-id="5d5b3-124">Stick up</span></span>            |
|               <span data-ttu-id="5d5b3-125">Nach unten</span><span class="sxs-lookup"><span data-stu-id="5d5b3-125">Down</span></span> | <span data-ttu-id="5d5b3-126">Joystick nach unten</span><span class="sxs-lookup"><span data-stu-id="5d5b3-126">Stick down</span></span>          |
|               <span data-ttu-id="5d5b3-127">Nach links</span><span class="sxs-lookup"><span data-stu-id="5d5b3-127">Left</span></span> | <span data-ttu-id="5d5b3-128">Joystick nach links</span><span class="sxs-lookup"><span data-stu-id="5d5b3-128">Stick left</span></span>          |
|              <span data-ttu-id="5d5b3-129">Nach rechts</span><span class="sxs-lookup"><span data-stu-id="5d5b3-129">Right</span></span> | <span data-ttu-id="5d5b3-130">Joystick nach rechts</span><span class="sxs-lookup"><span data-stu-id="5d5b3-130">Stick right</span></span>         |
|               <span data-ttu-id="5d5b3-131">Ansicht</span><span class="sxs-lookup"><span data-stu-id="5d5b3-131">View</span></span> | <span data-ttu-id="5d5b3-132">Ansicht-Taste</span><span class="sxs-lookup"><span data-stu-id="5d5b3-132">View button</span></span>         |
|               <span data-ttu-id="5d5b3-133">Menü</span><span class="sxs-lookup"><span data-stu-id="5d5b3-133">Menu</span></span> | <span data-ttu-id="5d5b3-134">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="5d5b3-134">Menu button</span></span>         |
|             <span data-ttu-id="5d5b3-135">Annehmen</span><span class="sxs-lookup"><span data-stu-id="5d5b3-135">Accept</span></span> | <span data-ttu-id="5d5b3-136">Taste für Aktion1</span><span class="sxs-lookup"><span data-stu-id="5d5b3-136">Action 1 button</span></span>     |
|             <span data-ttu-id="5d5b3-137">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="5d5b3-137">Cancel</span></span> | <span data-ttu-id="5d5b3-138">Taste für Aktion2</span><span class="sxs-lookup"><span data-stu-id="5d5b3-138">Action 2 button</span></span>     |

<span data-ttu-id="5d5b3-139">Arcade-Joysticks ordnen keines der [optionalen Sätze](ui-navigation-controller.md#optional-set) mit Navigationsbefehlen zu.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-139">Arcade sticks don't map any of the [optional set](ui-navigation-controller.md#optional-set) of navigation commands.</span></span>


## <a name="detect-and-track-arcade-sticks"></a><span data-ttu-id="5d5b3-140">Ermitteln und Nachverfolgen von Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-140">Detect and track arcade sticks</span></span>

<span data-ttu-id="5d5b3-141">Arcade-Joysticks werden vom System verwaltet. Daher müssen Sie diese nicht erstellen oder initialisieren.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-141">Arcade sticks are managed by the system, therefore you don't have to create or initialize them.</span></span> <span data-ttu-id="5d5b3-142">Das System stellt eine Liste der verbundenen Arcade-Joysticks und Ereignisse bereit, um Sie zu benachrichtigen, wenn ein Arcade-Joystick hinzugefügt oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-142">The system provides a list of connected arcades sticks and events to notify you when an arcade stick is added or removed.</span></span>

### <a name="the-arcade-sticks-list"></a><span data-ttu-id="5d5b3-143">Liste mit Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-143">The arcade sticks list</span></span>

<span data-ttu-id="5d5b3-144">Die [ArcadeStick][]-Klasse stellt die statische Eigenschaft [ArcadeSticks][] bereit. Dabei handelt es sich um eine schreibgeschützte Liste mit derzeit verbundenen Arcade-Joysticks.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-144">The [ArcadeStick][] class provides a static property, [ArcadeSticks][], which is a read-only list of arcade sticks that are currently connected.</span></span> <span data-ttu-id="5d5b3-145">Da Sie möglicherweise nur an einigen der verbundenen Arcade-Joysticks interessiert sind, wird empfohlen, dass Sie eine eigene Sammlung verwalten, statt über die Eigenschaft `ArcadeSticks` auf diese zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-145">Because you might only be interested in some of the connected arcade sticks, its recommended that you maintain your own collection instead of accessing them through the `ArcadeSticks` property.</span></span>

<span data-ttu-id="5d5b3-146">Im folgenden Beispiel werden alle verbundenen Arcade-Joysticks in eine neue Sammlung kopiert.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-146">The following example copies all connected arcade sticks into a new collection.</span></span>
```cpp
auto myArcadeSticks = ref new Vector<ArcadeStick^>();

for (auto arcadestick : ArcadeStick::ArcadeSticks)
{
    // This code assumes that you're interested in all arcade sticks.
    myArcadeSticks->Append(arcadestick);
}
```

### <a name="adding-and-removing-arcade-sticks"></a><span data-ttu-id="5d5b3-147">Hinzufügen und Entfernen von Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-147">Adding and removing arcade sticks</span></span>

<span data-ttu-id="5d5b3-148">Wenn ein Arcade-Joystick hinzugefügt oder entfernt wird, werden die Ereignisse [ArcadeStickAdded][] und [ArcadeStickRemoved][] ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-148">When an arcade stick is added or removed the [ArcadeStickAdded][] and [ArcadeStickRemoved][] events are raised.</span></span> <span data-ttu-id="5d5b3-149">Sie können Handler für diese Ereignisse registrieren, um die zurzeit verbundenen Arcade-Joysticks nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-149">You can register handlers for these events to keep track of the arcade sticks that are currently connected.</span></span>

<span data-ttu-id="5d5b3-150">Im folgenden Beispiel wird die Nachverfolgung eines hinzugefügten Arcade-Joysticks gestartet.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-150">The following example starts tracking an arcade stick that's been added.</span></span>
```cpp
ArcadeStick::ArcadeStickAdded += ref new EventHandler<ArcadeStick^>(Platform::Object^, ArcadeStick^ args)
{
    // This code assumes that you're interested in all new arcade sticks.
    myArcadeSticks->Append(args);
}
```

<span data-ttu-id="5d5b3-151">Im folgenden Beispiel wird die Nachverfolgung eines entfernen Arcade-Joysticks beendet.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-151">The following example stops tracking an arcade stick that's been removed.</span></span>
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

### <a name="users-and-headsets"></a><span data-ttu-id="5d5b3-152">Benutzer und Headsets</span><span class="sxs-lookup"><span data-stu-id="5d5b3-152">Users and headsets</span></span>

<span data-ttu-id="5d5b3-153">Jedes Arcade-Joystick kann mit einem Benutzerkonto verknüpft werden, um die Identität des Benutzers mit dem Spiel zu verknüpfen, und mit einem Headset verbunden werden, um Sprachchats oder Features im Spiel zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-153">Each arcade stick can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features.</span></span> <span data-ttu-id="5d5b3-154">Weitere Informationen zu Benutzern und Headsets finden Sie unter [Nachverfolgen von Benutzern und ihren Geräte](input-practices-for-games.md#tracking-users-and-their-devices) und [Headsets](headset.md).</span><span class="sxs-lookup"><span data-stu-id="5d5b3-154">To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md).</span></span>


## <a name="reading-the-arcade-stick"></a><span data-ttu-id="5d5b3-155">Lesen des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-155">Reading the arcade stick</span></span>

<span data-ttu-id="5d5b3-156">Nachdem Sie den Arcade-Joystick identifiziert haben, für den Sie sich interessieren, können Sie Eingaben von ihm erfassen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-156">After you identify the arcade stick that you're interested in, you're ready to gather input from it.</span></span> <span data-ttu-id="5d5b3-157">Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Arcade-Joysticks Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-157">However, unlike some other kinds of input that you might be used to, arcade sticks don't communicate state-change by raising events.</span></span> <span data-ttu-id="5d5b3-158">Stattdessen müssen Sie regelmäßig ihren aktuellen Status lesen, indem Sie sie _abfragen_.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-158">Instead, you take regular readings of their current state by _polling_ them.</span></span>

### <a name="polling-the-arcade-stick"></a><span data-ttu-id="5d5b3-159">Abfragen des Arcade-Joysticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-159">Polling the arcade stick</span></span>

<span data-ttu-id="5d5b3-160">Beim Abfragen wird ein Snapshot des Arcade-Joysticks zu einem bestimmten Zeitpunkt erstellt.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-160">Polling captures a snapshot of the arcade stick at a precise point in time.</span></span> <span data-ttu-id="5d5b3-161">Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-161">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven; its also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="5d5b3-162">Sie fragen einen Arcade-Joystick ab, indem Sie [GetCurrentReading][] aufrufen. Diese Funktion gibt ein [ArcadeStickReading][]-Element zurück, das den Zustand des Arcade-Joysticks enthält.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-162">You poll an arcade stick by calling [GetCurrentReading][]; this function returns an [ArcadeStickReading][] that contains the state of the arcade stick.</span></span>

<span data-ttu-id="5d5b3-163">Im folgenden Beispiel wird der aktuelle Zustand eines Arcade-Joysticks abgefragt.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-163">The following example polls an arcade stick for its current state.</span></span>
```cpp
auto arcadestick = myArcadeSticks[0];

ArcadeStickReading reading = arcadestick->GetCurrentReading();
```

<span data-ttu-id="5d5b3-164">Zusätzlich zum Zustand des Arcade-Joysticks enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, zu dem der Zustand abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-164">In addition to the arcade stick state, each reading includes a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="5d5b3-165">Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Werte oder zum Zeitpunkt der Spielsimulation herzustellen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-165">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="reading-the-buttons"></a><span data-ttu-id="5d5b3-166">Lesen der Tasten</span><span class="sxs-lookup"><span data-stu-id="5d5b3-166">Reading the buttons</span></span>

<span data-ttu-id="5d5b3-167">Jede Taste des Arcade-Joysticks (die vier Richtungen des Joysticks, sechs **Aktionstasten** und zwei **Sondertasten**) stellt einen digitalen Ablesewert bereit, der angibt, ob sie gedrückt (unten) oder nicht gedrückt (oben) ist.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-167">Each of the arcade stick buttons--the four directions of the joystick, six **action** buttons, and two **special** buttons--provide a digital reading that indicates whether its pressed (down), or released (up).</span></span> <span data-ttu-id="5d5b3-168">Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte dargestellt, sondern in einem einzelnen Bitfeld zusammengefasst, das durch die Enumeration [ArcadeStickButtons][] dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-168">For efficiency, button readings aren't represented as individual boolean values; instead they're all packed into a single bitfield that's represented by the [ArcadeStickButtons][] enumeration.</span></span>

> <span data-ttu-id="5d5b3-169">**Hinweis**    Arcade-Joysticks besitzen zusätzliche Tasten für die Benutzeroberflächennavigation, beispielsweise die **Ansicht**- und **Menü**-Taste.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-169">**Note**    Arcade sticks are equipped with additional buttons used for UI navigation such as the **view** and **menu** buttons.</span></span> <span data-ttu-id="5d5b3-170">Diese Tasten sind nicht in der Enumeration `ArcadeStickButtons` enthalten und können nur gelesen werden, wenn auf den Arcade-Joystick als Benutzeroberflächen-Navigationsgerät zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-170">These buttons are not a part of the `ArcadeStickButtons` enumeration and can only be read by accessing the arcade stick as a UI navigation device.</span></span> <span data-ttu-id="5d5b3-171">Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationsgerät](ui-navigation-controller.md).</span><span class="sxs-lookup"><span data-stu-id="5d5b3-171">For more information, see [UI Navigation Device](ui-navigation-controller.md).</span></span>

<span data-ttu-id="5d5b3-172">Die Schaltflächenwerte werden von der `Buttons`-Eigenschaft der [ArcadeStickReading][]-Struktur gelesen.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-172">The button values are read from the `Buttons` property of the [ArcadeStickReading][] structure.</span></span> <span data-ttu-id="5d5b3-173">Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-173">Because this property is a bitfield, bitwise masking is used to isolate the value of the button that you're interested in.</span></span> <span data-ttu-id="5d5b3-174">Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).</span><span class="sxs-lookup"><span data-stu-id="5d5b3-174">The button is pressed (down) when the corresponding bit is set; otherwise its released (up).</span></span>

<span data-ttu-id="5d5b3-175">Im folgenden Beispiel wird ermittelt, ob die Taste für Aktion 1 gedrückt ist.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-175">The following example determines whether the Action 1 button is pressed.</span></span>
```cpp
if (ArcadeStickButtons::Action1 == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is pressed
}
```

<span data-ttu-id="5d5b3-176">Im folgenden Beispiel wird ermittelt, ob die Taste für Aktion 1 losgelassen wurde.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-176">The following example determines whether the Action 1 button is released.</span></span>
```cpp
if (ArcadeStickButtons::None == (reading.Buttons & ArcadeStickButtons::Action1))
{
    // Action 1 is released (not pressed)
}
```

<span data-ttu-id="5d5b3-177">In einigen Fällen möchten Sie möglicherweise ermitteln, ob eine Taste von „Gedrückt“ zu „Losgelassen“ oder von „Losgelassen“ zu „Gedrückt“ wechselt, ob mehrere Tasten gedrückt oder losgelassen werden, oder ob verschiedene Tasten in einer bestimmten Weise angeordnet sind – einige gedrückt, andere nicht.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-177">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way--some pressed, some not.</span></span> <span data-ttu-id="5d5b3-178">Weitere Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) und [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="5d5b3-178">For information on how to detect these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

## <a name="run-the-inputinterfacing-sample"></a><span data-ttu-id="5d5b3-179">Ausführen des InputInterfacing-Beispiels</span><span class="sxs-lookup"><span data-stu-id="5d5b3-179">Run the InputInterfacing sample</span></span>

<span data-ttu-id="5d5b3-180">Das [InputInterfacingUWP-Beispiel _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) veranschaulicht, wie Arcade-Joysticks und verschiedene Arten von Eingabegeräten zusammen verwendet werden und wie diese Eingabegeräte sich bei der Verwendung als Benutzeroberflächen-Navigationcontrollern verhalten.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-180">The [InputInterfacingUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) demonstrates how to use arcade sticks and different kinds of input devices in tandem, as well as how these input devices behave as UI navigation controllers.</span></span>


## <a name="see-also"></a><span data-ttu-id="5d5b3-181">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5d5b3-181">See also</span></span>
<span data-ttu-id="5d5b3-182">[Windows.Gaming.Input.UINavigationController][]
[Windows.Gaming.Input.IGameController][]</span><span class="sxs-lookup"><span data-stu-id="5d5b3-182">[Windows.Gaming.Input.UINavigationController][]
[Windows.Gaming.Input.IGameController][]</span></span>

[<span data-ttu-id="5d5b3-183">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="5d5b3-183">Windows.Gaming.Input</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[<span data-ttu-id="5d5b3-184">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="5d5b3-184">Windows.Gaming.Input.IGameController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[<span data-ttu-id="5d5b3-185">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="5d5b3-185">Windows.Gaming.Input.UINavigationController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[<span data-ttu-id="5d5b3-186">arcadestick</span><span class="sxs-lookup"><span data-stu-id="5d5b3-186">arcadestick</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.aspx
[<span data-ttu-id="5d5b3-187">arcadesticks</span><span class="sxs-lookup"><span data-stu-id="5d5b3-187">arcadesticks</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadesticks.aspx
[<span data-ttu-id="5d5b3-188">arcadestickadded</span><span class="sxs-lookup"><span data-stu-id="5d5b3-188">arcadestickadded</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickadded.aspx
[<span data-ttu-id="5d5b3-189">arcadestickremoved</span><span class="sxs-lookup"><span data-stu-id="5d5b3-189">arcadestickremoved</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.arcadestickremoved.aspx
[<span data-ttu-id="5d5b3-190">getcurrentreading</span><span class="sxs-lookup"><span data-stu-id="5d5b3-190">getcurrentreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestick.getcurrentreading.aspx
[<span data-ttu-id="5d5b3-191">arcadestickreading</span><span class="sxs-lookup"><span data-stu-id="5d5b3-191">arcadestickreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickreading.aspx
[<span data-ttu-id="5d5b3-192">arcadestickbuttons</span><span class="sxs-lookup"><span data-stu-id="5d5b3-192">arcadestickbuttons</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.arcadestickbuttons.aspx
