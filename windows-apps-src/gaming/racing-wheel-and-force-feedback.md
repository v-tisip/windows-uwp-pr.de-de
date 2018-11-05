---
author: eliotcowley
title: Rennlenkräder und Kraftrückmeldung
description: Verwenden Sie die Windows.Gaming.Input-APIs für Rennlenkräder, um Funktionen zu erkennen und zu ermitteln sowie Kraftrückmeldungsbefehle zu lesen und an Rennlenkräder zu senden.
ms.assetid: 6287D87F-6F2E-4B67-9E82-3D6E51CBAFF9
ms.author: wdg-dev-content
ms.date: 05/09/2018
ms.topic: article
keywords: Windows 10, UWP, Spiele, Rennlenkrad, Kraftrückmeldung
ms.localizationpriority: medium
ms.openlocfilehash: 20b4b35bb729ee49dbfd3f2b2b2a029a4319521c
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6029936"
---
# <a name="racing-wheel-and-force-feedback"></a><span data-ttu-id="91ee3-104">Rennlenkräder und Kraftrückmeldung</span><span class="sxs-lookup"><span data-stu-id="91ee3-104">Racing wheel and force feedback</span></span>

<span data-ttu-id="91ee3-105">Auf dieser Seite werden die Grundlagen der Programmierung für Xbox One-Renklenkräder mittels [Windows.Gaming.Input.RacingWheel][Racingwheel] und verwandter APIs für die Universelle Windows-Plattform (UWP) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="91ee3-105">This page describes the basics of programming for Xbox One racing wheels using [Windows.Gaming.Input.RacingWheel][racingwheel] and related APIs for the Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="91ee3-106">Auf dieser Seite erfahren Sie:</span><span class="sxs-lookup"><span data-stu-id="91ee3-106">By reading this page, you'll learn:</span></span>

* <span data-ttu-id="91ee3-107">Wie Sie eine Liste der verbundenen Rennlenkräder und ihrer Benutzer erstellen</span><span class="sxs-lookup"><span data-stu-id="91ee3-107">how to gather a list of connected racing wheels and their users</span></span>
* <span data-ttu-id="91ee3-108">Wie Sie feststellen, dass ein Rennlenkrad hinzugefügt oder entfernt wurde</span><span class="sxs-lookup"><span data-stu-id="91ee3-108">how to detect that a racing wheel has been added or removed</span></span>
* <span data-ttu-id="91ee3-109">Wie Sie die Eingabe eines oder mehrerer Rennlenkräder auslesen</span><span class="sxs-lookup"><span data-stu-id="91ee3-109">how to read input from one or more racing wheels</span></span>
* <span data-ttu-id="91ee3-110">Wie Sie Kraftrückmeldungsbefehle senden</span><span class="sxs-lookup"><span data-stu-id="91ee3-110">how to send force feedback commands</span></span>
* <span data-ttu-id="91ee3-111">Wie sich Rennlenkräder als UI-Navigationsgerät verhalten</span><span class="sxs-lookup"><span data-stu-id="91ee3-111">how racing wheels behave as UI navigation devices</span></span>

## <a name="racing-wheel-overview"></a><span data-ttu-id="91ee3-112">Übersicht über Rennlenkräder</span><span class="sxs-lookup"><span data-stu-id="91ee3-112">Racing wheel overview</span></span>

<span data-ttu-id="91ee3-113">Rennlenkräder sind Eingabegeräte, die Benutzern das Gefühl vermitteln, in einem echten Rennwagencockpit zu sitzen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-113">Racing wheels are input devices that resemble the feel of a real racecar cockpit.</span></span> <span data-ttu-id="91ee3-114">Rennlenkräder sind das ideale Eingabegerät für Rennsportspiele im Arcade- und Simulationsstil, die Autos oder Trucks enthalten.</span><span class="sxs-lookup"><span data-stu-id="91ee3-114">Racing wheels are the perfect input device for both arcade-style and simulation-style racing games that feature cars or trucks.</span></span> <span data-ttu-id="91ee3-115">Rennlenkräder werden in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input][] unterstützt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-115">Racing wheels are supported in Windows 10 and Xbox One UWP apps by the [Windows.Gaming.Input][] namespace.</span></span>

<span data-ttu-id="91ee3-116">Xbox One-Rennlenkräder werden zu verschiedenen Preisen angeboten. In der Regel verfügen Rennlenkräder über mehr und bessere Eingabe- und Kraftrückmeldungsfunktionen, je höher ihr Preis liegt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-116">Xbox One racing wheels are offered at a variety of price points, generally having more and better input and force feedback capabilities as their price points rise.</span></span> <span data-ttu-id="91ee3-117">Alle Rennlenkräder besitzen ein analoges Lenkrad, analoge Gas- und Bremsensteuerelemente sowie einige Lenkradtasten.</span><span class="sxs-lookup"><span data-stu-id="91ee3-117">All racing wheels are equipped with an analog steering wheel, analog throttle and brake controls, and some on-wheel buttons.</span></span> <span data-ttu-id="91ee3-118">Einige Rennlenkräder sind zusätzlich mit analogen Kupplungs- und Handbremsensteuerelementen, einer analogen Gangschaltung sowie Kraftrückmeldungsfunktionen ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="91ee3-118">Some racing wheels are additionally equipped with analog clutch and handbrake controls, pattern shifters, and force feedback capabilities.</span></span> <span data-ttu-id="91ee3-119">Nicht alle Rennlenkräder besitzen die gleichen Features. Darüber hinaus unterscheiden sie sich möglicherweise hinsichtlich der Unterstützung für bestimmte Features. Beispielsweise können Lenkräder unterschiedliche Drehbereiche und Gangschaltungen eine unterschiedliche Zahl von Gängen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-119">Not all racing wheels are equipped with the same sets of features, and may also vary in their support for certain features&mdash;for example, steering wheels might support different ranges of rotation and pattern shifters might support different numbers of gears.</span></span>

### <a name="device-capabilities"></a><span data-ttu-id="91ee3-120">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="91ee3-120">Device capabilities</span></span>

<span data-ttu-id="91ee3-121">Die verschiedenen Xbox One-Rennlenkräder bieten unterschiedliche optionale Gerätefunktionen und einen unterschiedlichen Grad an Unterstützung für diese Funktionen. Dieser Grad an Abweichungen für ein einzelnes Eingabegerät ist unter den Geräten, die von den [Windows.Gaming.Input][]-APIs unterstützt werden, einzigartig.</span><span class="sxs-lookup"><span data-stu-id="91ee3-121">Different Xbox One racing wheels offer different sets of optional device capabilities and varying levels of support for those capabilities; this level of variation between a single kind of input device is unique among the devices supported by the [Windows.Gaming.Input][] APIs.</span></span> <span data-ttu-id="91ee3-122">Darüber hinaus unterstützen die meisten Geräte, denen Sie begegnen werden, zumindest einige optionale Funktionen oder andere Abweichungen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-122">Furthermore, most devices you'll encounter will support at least some optional capabilities or other variations.</span></span> <span data-ttu-id="91ee3-123">Daher ist es wichtig, die Funktionen der verbundenen Rennlenkräder einzeln zu ermitteln und die gesamte Bandbreite der für Ihr Spiel sinnvollen Funktionen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-123">Because of this, it's important to determine the capabilities of each connected racing wheel individually and to support the full variation of capabilities that makes sense for your game.</span></span>

<span data-ttu-id="91ee3-124">Weitere Informationen finden Sie unter [Ermitteln von Rennlenkradfunktionen](#determining-racing-wheel-capabilities).</span><span class="sxs-lookup"><span data-stu-id="91ee3-124">For more information, see [Determining racing wheel capabilities](#determining-racing-wheel-capabilities).</span></span>

### <a name="force-feedback"></a><span data-ttu-id="91ee3-125">Kraftrückmeldung</span><span class="sxs-lookup"><span data-stu-id="91ee3-125">Force feedback</span></span>

<span data-ttu-id="91ee3-126">Einige Xbox One-Rennlenkräder stellen eine echte Kraftrückmeldung und nicht einfach nur Vibrationen bereit, d.h., sie können echte Kräfte auf eine Steuerungsachse wie das Lenkrad ausüben.</span><span class="sxs-lookup"><span data-stu-id="91ee3-126">Some Xbox One racing wheels offer true force feedback&mdash;that is, they can apply actual forces on an axis of control such as their steering wheel&mdash;not just simple vibration.</span></span> <span data-ttu-id="91ee3-127">Spiele verwenden diese Fähigkeit, um ein besseres Spielerlebnis zu vermitteln (_simulierte Unfallschäden_, „Gefühl für die Straße“) und die Anforderungen in Bezug auf gutes Fahren zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-127">Games use this ability to create a greater sense of immersion (_simulated crash damage_, "road feel") and to increase the challenge of driving well.</span></span>

<span data-ttu-id="91ee3-128">Weitere Informationen finden Sie unter [Übersicht über die Kraftrückmeldung](#force-feedback-overview).</span><span class="sxs-lookup"><span data-stu-id="91ee3-128">For more information, see [Force feedback overview](#force-feedback-overview).</span></span>

### <a name="ui-navigation"></a><span data-ttu-id="91ee3-129">Benutzeroberflächennavigation</span><span class="sxs-lookup"><span data-stu-id="91ee3-129">UI navigation</span></span>

<span data-ttu-id="91ee3-130">Um den Aufwand für die Unterstützung unterschiedlicher Eingabegeräte für die Benutzeroberflächennavigation zu verringern und die Konsistenz zwischen Spielen und Geräten zu fördern, dienen die meisten _physischen_ Eingabegeräte gleichzeitig als getrennte _logische_ Eingabegeräte, die als [Benutzeroberflächen-Navigationscontroller](ui-navigation-controller.md) bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-130">In order to ease the burden of supporting the different input devices for user interface navigation and to encourage consistency between games and devices, most _physical_ input devices simultaneously act as a separate _logical_ input device called a [UI navigation controller](ui-navigation-controller.md).</span></span> <span data-ttu-id="91ee3-131">Der Benutzeroberflächen-Navigationscontroller stellt ein gemeinsames Vokabular für Benutzeroberflächen-Navigationsbefehle über verschiedene Eingabegeräte hinweg bereit.</span><span class="sxs-lookup"><span data-stu-id="91ee3-131">The UI navigation controller provides a common vocabulary for UI navigation commands across input devices.</span></span>

<span data-ttu-id="91ee3-132">Aufgrund der spezifischen Ausrichtung auf analoge Steuerungen und des Umfangs der Abweichungen zwischen den verschiedenen Rennlenkrädern verfügen diese in der Regel über Steuerkreuz, **Ansicht** **Menü** und die Tasten **A**, **B**, **X** und **Y**, die den Tasten eines [Gamepad](gamepad-and-vibration.md) ähnlich sind. Diese Tasten sind jedoch nicht für die Unterstützung von Befehlen im Spiel vorgesehen und können nicht direkt als Rennlenkradtasten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-132">Due to their unique focus on analog controls and the degree of variation between different racing wheels, they're typically equipped with a digital D-pad, **View**, **Menu**, **A**, **B**, **X**, and **Y** buttons that resemble those of a [gamepad](gamepad-and-vibration.md); these buttons aren't intended to support gameplay commands and can't be readily accessed as racing wheel buttons.</span></span>

<span data-ttu-id="91ee3-133">Als Benutzeroberflächen-Navigationscontroller ordnen Rennlenkräder den [erforderlichen Satz](ui-navigation-controller.md#required-set) von Navigationsbefehlen dem linken Ministick, dem Steuerkreuz, der **Ansicht**, dem **Menü** sowie den Tasten **A** und **B** zu.</span><span class="sxs-lookup"><span data-stu-id="91ee3-133">As a UI navigation controller, racing wheels map the [required set](ui-navigation-controller.md#required-set) of navigation commands to the left thumbstick, D-pad, **View**, **Menu**, **A**, and **B** buttons.</span></span>

| <span data-ttu-id="91ee3-134">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="91ee3-134">Navigation command</span></span> | <span data-ttu-id="91ee3-135">Rennlenkradeingabe</span><span class="sxs-lookup"><span data-stu-id="91ee3-135">Racing wheel input</span></span> |
| ------------------:| ------------------ |
|                 <span data-ttu-id="91ee3-136">Nach oben</span><span class="sxs-lookup"><span data-stu-id="91ee3-136">Up</span></span> | <span data-ttu-id="91ee3-137">Steuerkreuz nach oben</span><span class="sxs-lookup"><span data-stu-id="91ee3-137">D-pad up</span></span>           |
|               <span data-ttu-id="91ee3-138">Nach unten</span><span class="sxs-lookup"><span data-stu-id="91ee3-138">Down</span></span> | <span data-ttu-id="91ee3-139">Steuerkreuz nach unten</span><span class="sxs-lookup"><span data-stu-id="91ee3-139">D-pad down</span></span>         |
|               <span data-ttu-id="91ee3-140">Links</span><span class="sxs-lookup"><span data-stu-id="91ee3-140">Left</span></span> | <span data-ttu-id="91ee3-141">Steuerkreuz nach links</span><span class="sxs-lookup"><span data-stu-id="91ee3-141">D-pad left</span></span>         |
|              <span data-ttu-id="91ee3-142">Rechts</span><span class="sxs-lookup"><span data-stu-id="91ee3-142">Right</span></span> | <span data-ttu-id="91ee3-143">Steuerkreuz nach rechts</span><span class="sxs-lookup"><span data-stu-id="91ee3-143">D-pad right</span></span>        |
|               <span data-ttu-id="91ee3-144">Ansicht</span><span class="sxs-lookup"><span data-stu-id="91ee3-144">View</span></span> | <span data-ttu-id="91ee3-145">Ansicht-Taste</span><span class="sxs-lookup"><span data-stu-id="91ee3-145">View button</span></span>        |
|               <span data-ttu-id="91ee3-146">Menü</span><span class="sxs-lookup"><span data-stu-id="91ee3-146">Menu</span></span> | <span data-ttu-id="91ee3-147">Menü-Taste</span><span class="sxs-lookup"><span data-stu-id="91ee3-147">Menu button</span></span>        |
|             <span data-ttu-id="91ee3-148">Annehmen</span><span class="sxs-lookup"><span data-stu-id="91ee3-148">Accept</span></span> | <span data-ttu-id="91ee3-149">A-Taste</span><span class="sxs-lookup"><span data-stu-id="91ee3-149">A button</span></span>           |
|             <span data-ttu-id="91ee3-150">Abbrechen</span><span class="sxs-lookup"><span data-stu-id="91ee3-150">Cancel</span></span> | <span data-ttu-id="91ee3-151">B-Taste</span><span class="sxs-lookup"><span data-stu-id="91ee3-151">B button</span></span>           |

<span data-ttu-id="91ee3-152">Darüber hinaus ordnen einige Rennlenkräder möglicherweise einige [optionale](ui-navigation-controller.md#optional-set) Navigationsbefehle anderen von ihnen unterstützten Eingaben zu. Die Befehlszuordnungen können sich jedoch von Gerät zu Gerät unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-152">Additionally, some racing wheels might map some of the [optional set](ui-navigation-controller.md#optional-set) of navigation commands to other inputs they support, but command mappings can vary from device to device.</span></span> <span data-ttu-id="91ee3-153">Sie sollten die Unterstützung dieser Befehle ebenfalls in Betracht ziehen, dabei jedoch sicherstellen, dass diese Befehle für die Navigation in der Benutzeroberfläche Ihres Spiels nicht notwendig sind.</span><span class="sxs-lookup"><span data-stu-id="91ee3-153">Consider supporting these commands as well, but make sure that these commands are not essential to navigating your game's interface.</span></span>

| <span data-ttu-id="91ee3-154">Navigationsbefehl</span><span class="sxs-lookup"><span data-stu-id="91ee3-154">Navigation command</span></span> | <span data-ttu-id="91ee3-155">Rennlenkradeingabe</span><span class="sxs-lookup"><span data-stu-id="91ee3-155">Racing wheel input</span></span>    |
| ------------------:| --------------------- |
|            <span data-ttu-id="91ee3-156">Seite nach oben</span><span class="sxs-lookup"><span data-stu-id="91ee3-156">Page Up</span></span> | _<span data-ttu-id="91ee3-157">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-157">varies</span></span>_              |
|          <span data-ttu-id="91ee3-158">Seite nach unten</span><span class="sxs-lookup"><span data-stu-id="91ee3-158">Page Down</span></span> | _<span data-ttu-id="91ee3-159">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-159">varies</span></span>_              |
|          <span data-ttu-id="91ee3-160">Seite nach links</span><span class="sxs-lookup"><span data-stu-id="91ee3-160">Page Left</span></span> | _<span data-ttu-id="91ee3-161">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-161">varies</span></span>_              |
|         <span data-ttu-id="91ee3-162">Seite nach rechts</span><span class="sxs-lookup"><span data-stu-id="91ee3-162">Page Right</span></span> | _<span data-ttu-id="91ee3-163">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-163">varies</span></span>_              |
|          <span data-ttu-id="91ee3-164">Bildlauf nach oben</span><span class="sxs-lookup"><span data-stu-id="91ee3-164">Scroll Up</span></span> | _<span data-ttu-id="91ee3-165">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-165">varies</span></span>_              |
|        <span data-ttu-id="91ee3-166">Bildlauf nach unten</span><span class="sxs-lookup"><span data-stu-id="91ee3-166">Scroll Down</span></span> | _<span data-ttu-id="91ee3-167">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-167">varies</span></span>_              |
|        <span data-ttu-id="91ee3-168">Bildlauf nach links</span><span class="sxs-lookup"><span data-stu-id="91ee3-168">Scroll Left</span></span> | _<span data-ttu-id="91ee3-169">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-169">varies</span></span>_              |
|       <span data-ttu-id="91ee3-170">Bildlauf nach rechts</span><span class="sxs-lookup"><span data-stu-id="91ee3-170">Scroll Right</span></span> | _<span data-ttu-id="91ee3-171">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-171">varies</span></span>_              |
|          <span data-ttu-id="91ee3-172">Kontext 1</span><span class="sxs-lookup"><span data-stu-id="91ee3-172">Context 1</span></span> | <span data-ttu-id="91ee3-173">X-Taste (_in der Regel_)</span><span class="sxs-lookup"><span data-stu-id="91ee3-173">X Button (_commonly_)</span></span> |
|          <span data-ttu-id="91ee3-174">Kontext 2</span><span class="sxs-lookup"><span data-stu-id="91ee3-174">Context 2</span></span> | <span data-ttu-id="91ee3-175">Y-Taste (_in der Regel_)</span><span class="sxs-lookup"><span data-stu-id="91ee3-175">Y Button (_commonly_)</span></span> |
|          <span data-ttu-id="91ee3-176">Kontext 3</span><span class="sxs-lookup"><span data-stu-id="91ee3-176">Context 3</span></span> | _<span data-ttu-id="91ee3-177">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-177">varies</span></span>_              |
|          <span data-ttu-id="91ee3-178">Kontext 4</span><span class="sxs-lookup"><span data-stu-id="91ee3-178">Context 4</span></span> | _<span data-ttu-id="91ee3-179">Unterschiedlich</span><span class="sxs-lookup"><span data-stu-id="91ee3-179">varies</span></span>_              |

## <a name="detect-and-track-racing-wheels"></a><span data-ttu-id="91ee3-180">Erkennen und Nachverfolgen von Rennlenkrädern</span><span class="sxs-lookup"><span data-stu-id="91ee3-180">Detect and track racing wheels</span></span>

<span data-ttu-id="91ee3-181">Ermitteln und Nachverfolgen von Rennlenkrädern funktioniert auf genau die gleiche Weise wie für Gamepads, nur mit der [RacingWheel][]-Klasse anstelle der [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="91ee3-181">Detecting and tracking racing wheels works in exactly the same way as it does for gamepads, except with the [RacingWheel][] class instead of the [Gamepad](https://docs.microsoft.com/uwp/api/Windows.Gaming.Input.Gamepad) class.</span></span> <span data-ttu-id="91ee3-182">Weitere Informationen finden Sie unter [Gamepad und Vibration](gamepad-and-vibration.md).</span><span class="sxs-lookup"><span data-stu-id="91ee3-182">See [Gamepad and vibration](gamepad-and-vibration.md) for more information.</span></span>

<!-- Racing wheels are managed by the system, therefore you don't have to create or initialize them. The system provides a list of connected racing wheels and events to notify you when a racing wheel is added or removed.

### The racing wheels list

The [RacingWheel][] class provides a static property, [RacingWheels][], which is a read-only list of racing wheels that are currently connected. Because you might only be interested in some of the connected racing wheels, it's recommended that you maintain your own collection instead of accessing them through the `RacingWheels` property.

The following example copies all connected racing wheels into a new collection.
```cpp
auto myRacingWheels = ref new Vector<RacingWheel^>();

for (auto racingwheel : RacingWheel::RacingWheels)
{
    // This code assumes that you're interested in all racing wheels.
    myRacingWheels->Append(racingwheel);
}
```

### Adding and removing racing wheels

When a racing wheel is added or removed the [RacingWheelAdded][] and [RacingWheelRemoved][] events are raised. You can register handlers for these events to keep track of the racing wheels that are currently connected.

The following example starts tracking an racing wheels that's been added.
```cpp
RacingWheel::RacingWheelAdded += ref new EventHandler<RacingWheel^>(Platform::Object^, RacingWheel^ args)
{
    // This code assumes that you're interested in all new racing wheels.
    myRacingWheels->Append(args);
}
```

The following example stops tracking a racing wheel that's been removed.
```cpp
RacingWheel::RacingWheelRemoved += ref new EventHandler<RacingWheel^>(Platform::Object^, RacingWheel^ args)
{
    unsigned int indexRemoved;

    if(myRacingWheels->IndexOf(args, &indexRemoved))
    {
        myRacingWheels->RemoveAt(indexRemoved);
    }
}
```

### Users and headsets

Each racing wheel can be associated with a user account to link their identity to their gameplay, and can have a headset attached to facilitate voice chat or in-game features. To learn more about working with users and headsets, see [Tracking users and their devices](input-practices-for-games.md#tracking-users-and-their-devices) and [Headset](headset.md). -->

## <a name="reading-the-racing-wheel"></a><span data-ttu-id="91ee3-183">Auslesen der Rennlenkradwerte</span><span class="sxs-lookup"><span data-stu-id="91ee3-183">Reading the racing wheel</span></span>

<span data-ttu-id="91ee3-184">Nachdem Sie die Rennlenkräder identifiziert haben, für die Sie sich interessieren, können Sie Eingaben von diesen erfassen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-184">After you identify the racing wheels that you're interested in, you're ready to gather input from them.</span></span> <span data-ttu-id="91ee3-185">Anders als im Fall anderer Eingaben, die Sie möglicherweise kennen, teilen Rennlenkräder Zustandsänderungen jedoch nicht durch das Auslösen von Ereignissen mit.</span><span class="sxs-lookup"><span data-stu-id="91ee3-185">However, unlike some other kinds of input that you might be used to, racing wheels don't communicate state-change by raising events.</span></span> <span data-ttu-id="91ee3-186">Stattdessen müssen Sie die aktuellen Zustände regelmäßig _auslesen_ (Polling).</span><span class="sxs-lookup"><span data-stu-id="91ee3-186">Instead, you take regular readings of their current states by _polling_ them.</span></span>

### <a name="polling-the-racing-wheel"></a><span data-ttu-id="91ee3-187">Abrufen von Rennlenkrad-Daten</span><span class="sxs-lookup"><span data-stu-id="91ee3-187">Polling the racing wheel</span></span>

<span data-ttu-id="91ee3-188">Durch den Abruf wird eine Momentaufnahme des Rennlenkrads zu einem genau festgelegten Zeitpunkt erfasst.</span><span class="sxs-lookup"><span data-stu-id="91ee3-188">Polling captures a snapshot of the racing wheel at a precise point in time.</span></span> <span data-ttu-id="91ee3-189">Dieser Ansatz zum Erfassen von Eingaben ist für die meisten Spiele geeignet, da deren Logik üblicherweise in einer deterministischen Schleife ausgeführt wird und nicht ereignisgesteuert ist. Es ist in der Regel auch einfacher, Befehle in Spielen anhand von Eingaben zu interpretieren, die alle gemeinsam erfasst werden, als anhand zahlreicher Eingaben, die im Laufe der Zeit erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-189">This approach to input gathering is a good fit for most games because their logic typically runs in a deterministic loop rather than being event-driven; it's also typically simpler to interpret game commands from input gathered all at once than it is from many single inputs gathered over time.</span></span>

<span data-ttu-id="91ee3-190">Sie rufen Rennlenkradwerte durch Aufruf von [GetCurrentReading][] ab. Diese Funktion gibt einen [RacingWheelReading][]-Wert zurück, der den Zustand des Rennlenkrads enthält.</span><span class="sxs-lookup"><span data-stu-id="91ee3-190">You poll a racing wheel by calling [GetCurrentReading][]; this function returns a [RacingWheelReading][] that contains the state of the racing wheel.</span></span>

<span data-ttu-id="91ee3-191">Im folgenden Beispiel wird der aktuelle Zustand eines Rennlenkrads abgerufen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-191">The following example polls a racing wheel for its current state.</span></span>

```cpp
auto racingwheel = myRacingWheels[0];

RacingWheelReading reading = racingwheel->GetCurrentReading();
```

<span data-ttu-id="91ee3-192">Zusätzlich zum Zustand des Rennlenkrads enthält jede Ablesung einen Zeitstempel, der den genauen Zeitpunkt angibt, an dem der Zustand abgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="91ee3-192">In addition to the racing wheel state, each reading includes a timestamp that indicates precisely when the state was retrieved.</span></span> <span data-ttu-id="91ee3-193">Der Zeitstempel ist nützlich, um einen Bezug zu den Zeitpunkten vorheriger Ablesungen oder zum Zeitpunkt der Spielsimulation herzustellen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-193">The timestamp is useful for relating to the timing of previous readings or to the timing of the game simulation.</span></span>

### <a name="determining-racing-wheel-capabilities"></a><span data-ttu-id="91ee3-194">Ermitteln der Rennlenkradfunktionalität</span><span class="sxs-lookup"><span data-stu-id="91ee3-194">Determining racing wheel capabilities</span></span>

<span data-ttu-id="91ee3-195">Viele Steuerelemente eines Rennlenkrads sind optional oder unterstützen verschiedene Varianten. Da dies auch für erforderliche Steuerelemente gilt, müssen Sie die Funktionalität jedes Rennlenkrads einzeln ermitteln, bevor Sie die Eingaben verarbeiten können, die mit den Ablesungen des Rennlenkrads erfasst wurden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-195">Many of the racing wheel controls are optional or support different variations even in the required controls, so you have to determine the capabilities of each racing wheel individually before you can process the input gathered in each reading of the racing wheel.</span></span>

<span data-ttu-id="91ee3-196">Optionale Steuerelemente sind Handbremse, Kupplung und Gangschaltung. Sie können ermitteln, ob ein verbundenes Rennlenkrad diese Steuerelemente unterstützt, indem Sie die Eigenschaften [HasHandbrake][], [HasClutch][] bzw. [HasPatternShifter][] des Rennlenkrads lesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-196">The optional controls are the handbrake, clutch, and pattern shifter; you can determine whether a connected racing wheel supports these controls by reading the [HasHandbrake][], [HasClutch][], and [HasPatternShifter][] properties of the racing wheel, respectively.</span></span> <span data-ttu-id="91ee3-197">Das Steuerelement wird unterstützt, wenn der Wert der Eigenschaft **true** ist. Andernfalls wird es nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-197">The control is supported if the value of the property is **true**; otherwise it's not supported.</span></span>

```cpp
if (racingwheel->HasHandbrake)
{
    // the handbrake is supported
}

if (racingwheel->HasClutch)
{
    // the clutch is supported
}

if (racingwheel->HasPatternShifter)
{
    // the pattern shifter is supported
}
```

<span data-ttu-id="91ee3-198">Die Steuerelemente, deren Funktionalität variieren kann, sind das Lenkrad und die Gangschaltung.</span><span class="sxs-lookup"><span data-stu-id="91ee3-198">Additionally, the controls that may vary are the steering wheel and pattern shifter.</span></span> <span data-ttu-id="91ee3-199">Das Lenkrad kann hinsichtlich des Umfangs der physischen Drehung variieren, die durch das tatsächliche Lenkrad unterstützt wird. Die Gangschaltung kann hinsichtlich der Zahl der einzelnen Vorwärtsgänge variieren, die unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-199">The steering wheel can vary by the degree of physical rotation that the actual wheel can support, while the pattern shifter can vary by the number of distinct forward gears it supports.</span></span> <span data-ttu-id="91ee3-200">Sie können den größten, durch das tatsächliche Lenkrad unterstützten Drehwinkel ermitteln, indem Sie die Eigenschaft `MaxWheelAngle` des Rennlenkrads lesen. Dessen Wert entspricht dem maximal unterstützten physischen Winkel im Uhrzeigersinn, ausgedrückt in Grad (positive Gradangabe). Der gleiche Drehwinkel wird in der dem Uhrzeigersinn entgegengesetzten Richtung unterstützt (negative Gradangabe).</span><span class="sxs-lookup"><span data-stu-id="91ee3-200">You can determine the greatest angle of rotation the actual wheel supports by reading the `MaxWheelAngle` property of the racing wheel; its value is the maximum supported physical angle in degrees clock-wise (positive) which is likewise supported in the counter-clock-wise direction (negative degrees).</span></span> <span data-ttu-id="91ee3-201">Sie können den höchsten, durch die Gangschaltung unterstützten Vorwärtsgang ermitteln, indem Sie die Eigenschaft des Rennlenkrads lesen. Dessen Wert entspricht dem höchsten unterstützten Vorwärtsgang (einschließlich): Wenn der Wert 4 ist, unterstützt die Gangschaltung einen Rückwärtsgang, einen Leerlaufgang sowie einen ersten, zweiten, dritten und vierten Gang.</span><span class="sxs-lookup"><span data-stu-id="91ee3-201">You can determine the greatest forward gear the pattern shifter supports by reading the `MaxPatternShifterGear` property of the racing wheel; its value is the highest forward gear supported, inclusive&mdash;that is, if its value is 4, then the pattern shifter supports reverse, neutral, first, second, third, and fourth gears.</span></span>

```cpp
auto maxWheelDegrees = racingwheel->MaxWheelAngle;
auto maxShifterGears = racingwheel->MaxPatternShifterGear;
```

<span data-ttu-id="91ee3-202">Schließlich unterstützen einige Rennlenkräder die Kraftrückmeldung über das Lenkrad.</span><span class="sxs-lookup"><span data-stu-id="91ee3-202">Finally, some racing wheels support force feedback through the steering wheel.</span></span> <span data-ttu-id="91ee3-203">Sie können ermitteln, ob ein verbundenes Rennlenkrad die Kraftrückmeldung unterstützt, indem Sie die Eigenschaft [WheelMotor][] des Rennlenkrads lesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-203">You can determine whether a connected racing wheel supports force feedback by reading the [WheelMotor][] property of the racing wheel.</span></span> <span data-ttu-id="91ee3-204">Die Kraftrückmeldung wird unterstützt, wenn `WheelMotor` nicht **null** ist. Andernfalls wird sie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-204">Force feedback is supported if `WheelMotor` is not **null**; otherwise it's not supported.</span></span>

```cpp
if (racingwheel->WheelMotor != nullptr)
{
    // force feedback is supported
}
```

<span data-ttu-id="91ee3-205">Weitere Informationen dazu, wie Sie die Kraftrückmeldungsfunktion der Rennlenkräder verwenden, die dies unterstützen, finden Sie unter [Übersicht über die Kraftrückmeldung](#force-feedback-overview).</span><span class="sxs-lookup"><span data-stu-id="91ee3-205">For information on how to use the force feedback capability of racing wheels that support it, see [Force feedback overview](#force-feedback-overview).</span></span>

### <a name="reading-the-buttons"></a><span data-ttu-id="91ee3-206">Auslesen der Tasten</span><span class="sxs-lookup"><span data-stu-id="91ee3-206">Reading the buttons</span></span>

<span data-ttu-id="91ee3-207">Jede Rennlenkradtaste&mdash;die vier Richtungen des Steuerkreuzes, die Tasten **Vorheriger Gang** und **Nächster Gang** und 16 zusätzliche Tasten&mdash;stellt eine digitalen Wert bereit, der angibt, ob sie gedrückt (unten) oder freigegeben (oben) ist.</span><span class="sxs-lookup"><span data-stu-id="91ee3-207">Each of the racing wheel buttons&mdash;the four directions of the D-pad, the **Previous Gear** and **Next Gear** buttons, and 16 additional buttons&mdash;provides a digital reading that indicates whether it's pressed (down) or released (up).</span></span> <span data-ttu-id="91ee3-208">Aus Effizienzgründen werden die Ablesewerte der Tasten nicht als einzelne boolesche Werte angezeigt, sondern in einem einzelnen Bitfeld zusammengefasst, dargestellt durch die Enumeration [RacingWheelButtons][].</span><span class="sxs-lookup"><span data-stu-id="91ee3-208">For efficiency, button readings aren't represented as individual boolean values; instead they're all packed into a single bitfield that's represented by the [RacingWheelButtons][] enumeration.</span></span>

> [!NOTE]
> <span data-ttu-id="91ee3-209">Rennlenkräder besitzen zusätzliche Tasten für die Benutzeroberflächennavigation, beispielsweise die Tasten **Ansicht** und **Menü**.</span><span class="sxs-lookup"><span data-stu-id="91ee3-209">Racing wheels are equipped with additional buttons used for UI navigation such as the **View** and **Menu** buttons.</span></span> <span data-ttu-id="91ee3-210">Diese Tasten sind nicht in der Enumeration `RacingWheelButtons` enthalten und können nur gelesen werden, wenn auf das Rennlenkrad als Benutzeroberflächen-Navigationsgerät zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="91ee3-210">These buttons are not a part of the `RacingWheelButtons` enumeration and can only be read by accessing the racing wheel as a UI navigation device.</span></span> <span data-ttu-id="91ee3-211">Weitere Informationen finden Sie unter [Benutzeroberflächen-Navigationsgerät](ui-navigation-controller.md).</span><span class="sxs-lookup"><span data-stu-id="91ee3-211">For more information, see [UI Navigation Device](ui-navigation-controller.md).</span></span>

<span data-ttu-id="91ee3-212">Die Tastenwerte werden aus der Eigenschaft `Buttons` der Struktur [RacingWheelReading][] gelesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-212">The button values are read from the `Buttons` property of the [RacingWheelReading][] structure.</span></span> <span data-ttu-id="91ee3-213">Da diese Eigenschaft ein Bitfeld ist, wird eine bitweise Maskierung verwendet, um den Wert der Taste zu isolieren, an der Sie interessiert sind,</span><span class="sxs-lookup"><span data-stu-id="91ee3-213">Because this property is a bitfield, bitwise masking is used to isolate the value of the button that you're interested in.</span></span> <span data-ttu-id="91ee3-214">Die Taste ist gedrückt (unten), wenn das entsprechende Bit festgelegt ist. Andernfalls ist sie nicht gedrückt (oben).</span><span class="sxs-lookup"><span data-stu-id="91ee3-214">The button is pressed (down) when the corresponding bit is set; otherwise, it's released (up).</span></span>

<span data-ttu-id="91ee3-215">Im folgenden Beispiel wird ermittelt, ob die Taste **Nächster Gang** gedrückt ist.</span><span class="sxs-lookup"><span data-stu-id="91ee3-215">The following example determines whether the **Next Gear** button is pressed.</span></span>

```cpp
if (RacingWheelButtons::NextGear == (reading.Buttons & RacingWheelButtons::NextGear))
{
    // Next Gear is pressed
}
```

<span data-ttu-id="91ee3-216">Im folgenden Beispiel wird ermittelt, ob die Taste „Nächster Gang“ freigegeben ist.</span><span class="sxs-lookup"><span data-stu-id="91ee3-216">The following example determines whether the Next Gear button is released.</span></span>

```cpp
if (RacingWheelButtons::None == (reading.Buttons & RacingWheelButtons::NextGear))
{
    // Next Gear is released (not pressed)
}
```

<span data-ttu-id="91ee3-217">In einigen Fällen möchten Sie vielleicht ermitteln, ob eine Taste von „gedrückt“ zu „nicht gedrückt“ bzw. umgekehrt wechselt, oder ob mehrere Tasten gedrückt bzw. nicht gedrückt oder in bestimmter Weise angeordnet sind&mdash;einige gedrückt, andere nicht.</span><span class="sxs-lookup"><span data-stu-id="91ee3-217">Sometimes you might want to determine when a button transitions from pressed to released or released to pressed, whether multiple buttons are pressed or released, or if a set of buttons are arranged in a particular way&mdash;some pressed, some not.</span></span> <span data-ttu-id="91ee3-218">Weitere Informationen zum Ermitteln dieser Bedingungen finden Sie unter [Erkennen von Tastenübergängen](input-practices-for-games.md#detecting-button-transitions) und [Erkennen von komplexen Tastenanordnungen](input-practices-for-games.md#detecting-complex-button-arrangements).</span><span class="sxs-lookup"><span data-stu-id="91ee3-218">For information on how to detect these conditions, see [Detecting button transitions](input-practices-for-games.md#detecting-button-transitions) and [Detecting complex button arrangements](input-practices-for-games.md#detecting-complex-button-arrangements).</span></span>

### <a name="reading-the-wheel"></a><span data-ttu-id="91ee3-219">Lesen der Lenkradwerte</span><span class="sxs-lookup"><span data-stu-id="91ee3-219">Reading the wheel</span></span>

<span data-ttu-id="91ee3-220">Das Lenkrad ist ein erforderliches Steuerelement, das einen analogen Ablesewert zwischen -1,0 und +1,0 bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-220">The steering wheel is a required control that provides an analog reading between -1.0 and +1.0.</span></span> <span data-ttu-id="91ee3-221">Der Wert -1,0 entspricht der äußersten linken Lenkradposition. Der Wert +1,0 entspricht der äußersten rechten Lenkradposition.</span><span class="sxs-lookup"><span data-stu-id="91ee3-221">A value of -1.0 corresponds to the left-most wheel position; a value of +1.0 corresponds to the right-most position.</span></span> <span data-ttu-id="91ee3-222">Der Wert für das Lenkrad wird aus der Eigenschaft `Wheel` der Struktur [RacingWheelReading][] gelesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-222">The value of the steering wheel is read from the `Wheel` property of the [RacingWheelReading][] structure.</span></span>

```cpp
float wheel = reading.Wheel;  // returns a value between -1.0 and +1.0.
```

<span data-ttu-id="91ee3-223">Auch wenn die Lenkradwerte dem Grad der physischen Drehung des tatsächlichen Lenkrads entsprechen, abhängig vom durch das physische Rennlenkrad unterstützten Drehbereich, sollten Sie die Lenkradwerte nicht skalieren. Lenkräder, die einen größeren Drehbereich unterstützen, bieten lediglich eine größere Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="91ee3-223">Although wheel readings correspond to different degrees of physical rotation in the actual wheel depending on the range of rotation supported by the physical racing wheel, you don't usually want to scale the wheel readings; wheels that support greater degrees of rotation just provide greater precision.</span></span>

### <a name="reading-the-throttle-and-brake"></a><span data-ttu-id="91ee3-224">Auslesen der Gas- und Bremsensteuerelementwerte</span><span class="sxs-lookup"><span data-stu-id="91ee3-224">Reading the throttle and brake</span></span>

<span data-ttu-id="91ee3-225">Die Gas- und Bremsensteuerelemente sind erforderliche Steuerelemente, die jeweils analoge Ablesewerte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) bereitstellen, dargestellt als Gleitkommawerte.</span><span class="sxs-lookup"><span data-stu-id="91ee3-225">The throttle and brake are required controls that each provide analog readings between 0.0 (fully released) and 1.0 (fully pressed) represented as floating-point values.</span></span> <span data-ttu-id="91ee3-226">Der Wert für das Gassteuerelement wird aus der Eigenschaft `Throttle` der Struktur [RacingWheelReading][] gelesen. Der Wert für das Bremsensteuerelement wird aus der Eigenschaft `Brake` gelesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-226">The value of the throttle control is read from the `Throttle` property of the [RacingWheelReading][] struct; the value of the brake control is read from the `Brake` property.</span></span>

```cpp
float throttle = reading.Throttle;  // returns a value between 0.0 and 1.0
float brake    = reading.Brake;     // returns a value between 0.0 and 1.0
```

### <a name="reading-the-handbrake-and-clutch"></a><span data-ttu-id="91ee3-227">Lesen der Handbremsen- und Kupplungswerte</span><span class="sxs-lookup"><span data-stu-id="91ee3-227">Reading the handbrake and clutch</span></span>

<span data-ttu-id="91ee3-228">Die Handbremsen- und Kupplungssteuerelemente sind optionale Steuerelemente, die jeweils analoge Ablesewerte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) bereitstellen, dargestellt als Gleitkommawerte.</span><span class="sxs-lookup"><span data-stu-id="91ee3-228">The handbrake and clutch are optional controls that each provide analog readings between 0.0 (fully released) and 1.0 (fully engaged) represented as floating-point values.</span></span> <span data-ttu-id="91ee3-229">Der Wert für das Handbremsensteuerelement wird aus der Eigenschaft `Handbrake` der Struktur [RacingWheelReading][] gelesen. Der Wert für das Kupplungssteuerelement wird aus der Eigenschaft `Clutch` gelesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-229">The value of the handbrake control is read from the `Handbrake` property of the [RacingWheelReading][] struct; the value of the clutch control is read from the `Clutch` property.</span></span>

```cpp
float handbrake = 0.0;
float clutch = 0.0;

if(racingwheel->HasHandbrake)
{
    handbrake = reading.Handbrake;  // returns a value between 0.0 and 1.0
}

if(racingwheel->HasClutch)
{
    clutch = reading.Clutch;        // returns a value between 0.0 and 1.0
}
```

### <a name="reading-the-pattern-shifter"></a><span data-ttu-id="91ee3-230">Lesen der Gangschaltungswerte</span><span class="sxs-lookup"><span data-stu-id="91ee3-230">Reading the pattern shifter</span></span>

<span data-ttu-id="91ee3-231">Die Gangschaltung ist ein optionales Steuerelement, das einen digitalen Wert zwischen -1 und [MaxPatternShifterGear][] bereitstellt, dargestellt als ganze Zahl mit Vorzeichen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-231">The pattern shifter is an optional control that provides a digital reading between -1 and [MaxPatternShifterGear][] represented as a signed integer value.</span></span> <span data-ttu-id="91ee3-232">Der Wert -1 bzw. 0 entspricht dem _Rückwärtsgang_ bzw. dem _Leerlaufgang_. Aufsteigende positive Werte entsprechen den jeweiligen höheren Vorwärtsgängen bis einschließlich [MaxPatternShifterGear][].</span><span class="sxs-lookup"><span data-stu-id="91ee3-232">A value of -1 or 0 correspond to the _reverse_ and _neutral_ gears, respectively; increasingly positive values correspond to greater forward gears up to [MaxPatternShifterGear][], inclusive.</span></span> <span data-ttu-id="91ee3-233">Der Wert für die Gangschaltung wird aus der Eigenschaft `PatternShifterGear` der Struktur [RacingWheelReading][] gelesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-233">The value of the pattern shifter is read from the `PatternShifterGear` property of the [RacingWheelReading][] struct.</span></span>

```cpp
if (racingwheel->HasPatternShifter)
{
    gear = reading.PatternShifterGear;
}
```

> [!NOTE]
> <span data-ttu-id="91ee3-234">Hinweis    Wenn unterstützt, ist die Gangschaltung zusätzlich zu den erforderlichen Tasten für den **vorherigen Gang** und den **nächsten Gang** vorhanden, die sich ebenfalls auf den aktuellen Gang des Autos des Spielers auswirken.</span><span class="sxs-lookup"><span data-stu-id="91ee3-234">The pattern shifter, where supported, exists alongside the required **Previous Gear** and **Next Gear** buttons which also affect the current gear of the player's car.</span></span> <span data-ttu-id="91ee3-235">Wenn beides vorhanden ist, besteht eine einfache Strategie für die Zusammenführung dieser Eingaben im Ignorieren von Gangschaltung (und Kupplung), wenn sich ein Spieler für ein Automatikgetriebe entscheidet, und im Ignorieren der Tasten für den **vorherigen Gang** und den **nächsten Gang**, wenn sich ein Spieler für ein manuelles Getriebe entscheidet (nur möglich, wenn das Rennlenkrad über ein Gangschaltungssteuerelement verfügt).</span><span class="sxs-lookup"><span data-stu-id="91ee3-235">A simple strategy for unifying these inputs where both are present is to ignore the pattern shifter (and clutch) when a player chooses an automatic transmission for their car, and to ignore the **Previous** and **Next Gear** buttons when a player chooses a manual transmission for their car only if their racing wheel is equipped with a pattern shifter control.</span></span> <span data-ttu-id="91ee3-236">Wenn dies für Ihr Spiel nicht geeignet ist, können Sie eine andere Strategie für die Zusammenführung implementieren.</span><span class="sxs-lookup"><span data-stu-id="91ee3-236">You can implement a different unification strategy if this isn't suitable for your game.</span></span>

## <a name="run-the-inputinterfacing-sample"></a><span data-ttu-id="91ee3-237">Ausführen des InputInterfacing-Beispiels</span><span class="sxs-lookup"><span data-stu-id="91ee3-237">Run the InputInterfacing sample</span></span>

<span data-ttu-id="91ee3-238">Das [InputInterfacingUWP-Beispiel _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) zeigt, wie Rennlenkräder und verschiedene Arten von Eingabegeräten zusammen verwendet werden und wie sich diese Eingabegeräte bei Verwendung als Benutzeroberflächen-Navigationscontroller verhalten.</span><span class="sxs-lookup"><span data-stu-id="91ee3-238">The [InputInterfacingUWP sample _(github)_](https://github.com/Microsoft/Xbox-ATG-Samples/tree/master/Samples/System/InputInterfacingUWP) demonstrates how to use racing wheels and different kinds of input devices in tandem, as well as how these input devices behave as UI navigation controllers.</span></span>

## <a name="force-feedback-overview"></a><span data-ttu-id="91ee3-239">Übersicht über die Kraftrückmeldung</span><span class="sxs-lookup"><span data-stu-id="91ee3-239">Force feedback overview</span></span>

<span data-ttu-id="91ee3-240">Viele Rennlenkräder besitzen eine Kraftrückmeldungsfunktion, um ein umfassenderes und stärker herausforderndes Fahrerlebnis bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-240">Many racing wheels have force feedback capability to provide a more immersive and challenging driving experience.</span></span> <span data-ttu-id="91ee3-241">Rennlenkräder, die die Kraftrückmeldung unterstützen, besitzen in der Regel einen einzelnen Motor, der entlang einer einzelnen Achse (der Achse der Lenkraddrehung) Kraft auf das Lenkrad ausübt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-241">Racing wheels that support force feedback are typically equipped with a single motor that applies force to the steering wheel along a single axis, the axis of wheel rotation.</span></span> <span data-ttu-id="91ee3-242">Die Kraftrückmeldung wird in Windows10- und Xbox One-UWP-Apps durch den Namespace [Windows.Gaming.Input.ForceFeedback] unterstützt.</span><span class="sxs-lookup"><span data-stu-id="91ee3-242">Force feedback is supported in Windows 10 and Xbox One UWP apps by the [Windows.Gaming.Input.ForceFeedback][] namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="91ee3-243">Die Kraftrückmeldungs-APIs können mehrere Krafteinwirkungsachsen unterstützen. Xbox One-Rennlenkräder unterstützen zurzeit jedoch nur die Lenkraddrehungsachse als Kraftrückmeldungsachse.</span><span class="sxs-lookup"><span data-stu-id="91ee3-243">The force feedback APIs are capable of supporting several axes of force, but no Xbox One racing wheel currently supports any feedback axis other than that of wheel rotation.</span></span>

## <a name="using-force-feedback"></a><span data-ttu-id="91ee3-244">Verwenden der Kraftrückmeldung</span><span class="sxs-lookup"><span data-stu-id="91ee3-244">Using force feedback</span></span>

<span data-ttu-id="91ee3-245">In den folgenden Abschnitten werden die Grundlagen der Programmierung von Kraftrückmeldungseffekten für Xbox One-Rennlenkräder beschrieben.</span><span class="sxs-lookup"><span data-stu-id="91ee3-245">These sections describe the basics of programming force feedback effects for Xbox One racing wheels.</span></span> <span data-ttu-id="91ee3-246">Die Rückmeldung wird mithilfe von Effekten angewendet, die zuerst in das Rückmeldungsgerät geladen und anschließend gestartet, angehalten, fortgesetzt und gestoppt werden können, ähnlich wie Soundeffekte. Sie müssen jedoch zunächst die Rückmeldungsfunktionalität des Rennlenkrads ermitteln.</span><span class="sxs-lookup"><span data-stu-id="91ee3-246">Feedback is applied using effects, which are first loaded onto the force feedback device and then can be started, paused, resumed, and stopped in a manner similar to sound effects; however, you must first determine the feedback capabilities of the racing wheel.</span></span>

### <a name="determining-force-feedback-capabilities"></a><span data-ttu-id="91ee3-247">Ermitteln der Kraftrückmeldungsfunktionalität</span><span class="sxs-lookup"><span data-stu-id="91ee3-247">Determining force feedback capabilities</span></span>

<span data-ttu-id="91ee3-248">Sie können ermitteln, ob ein verbundenes Rennlenkrad die Kraftrückmeldung unterstützt, indem Sie die Eigenschaft [WheelMotor][] des Rennlenkrads lesen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-248">You can determine whether a connected racing wheel supports force feedback by reading the [WheelMotor][] property of the racing wheel.</span></span> <span data-ttu-id="91ee3-249">Die Kraftrückmeldung wird nicht unterstützt, wenn `WheelMotor` **null** ist. Andernfalls wird die Kraftrückmeldung unterstützt, und Sie können mit der Ermittlung der spezifischen Kraftrückmeldungsfunktionalität des Motors fortfahren, beispielsweise der Achsen, auf die Kraft ausgeübt werden kann.</span><span class="sxs-lookup"><span data-stu-id="91ee3-249">Force feedback isn't supported if `WheelMotor` is **null**; otherwise, force feedback is supported and you can proceed to determine the specific feedback capabilities of the motor, such as the axes it can affect.</span></span>

```cpp
if (racingwheel->WheelMotor != nullptr)
{
    auto axes = racingwheel->WheelMotor->SupportedAxes;

    if(ForceFeedbackEffectAxes::X == (axes & ForceFeedbackEffectAxes::X))
    {
        // Force can be applied through the X axis
    }

    if(ForceFeedbackEffectAxes::Y == (axes & ForceFeedbackEffectAxes::Y))
    {
        // Force can be applied through the Y axis
    }

    if(ForceFeedbackEffectAxes::Z == (axes & ForceFeedbackEffectAxes::Z))
    {
        // Force can be applied through the Z axis
    }
}
```

### <a name="loading-force-feedback-effects"></a><span data-ttu-id="91ee3-250">Laden der Kraftrückmeldungseffekte</span><span class="sxs-lookup"><span data-stu-id="91ee3-250">Loading force feedback effects</span></span>

<span data-ttu-id="91ee3-251">Die Kraftrückmeldungseffekte werden in das Rückmeldungsgerät geladen, auf dem sie autonom nach den Regeln Ihres Spiels „gespielt“ werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-251">Force feedback effects are loaded onto the feedback device where they are "played" autonomously at the command of your game.</span></span> <span data-ttu-id="91ee3-252">Es wird eine Reihe von Basiseffekten bereitgestellt. Benutzerdefinierte Effekte können über eine Klasse erstellt werden, die die [IForceFeedbackEffect][]-Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="91ee3-252">A number of basic effects are provided; custom effects can be created through a class that implements the [IForceFeedbackEffect][] interface.</span></span>

| <span data-ttu-id="91ee3-253">Effektklasse</span><span class="sxs-lookup"><span data-stu-id="91ee3-253">Effect class</span></span>         | <span data-ttu-id="91ee3-254">Effektbeschreibung</span><span class="sxs-lookup"><span data-stu-id="91ee3-254">Effect description</span></span>                                                                     |
| -------------------- | -------------------------------------------------------------------------------------- |
| <span data-ttu-id="91ee3-255">ConditionForceEffect</span><span class="sxs-lookup"><span data-stu-id="91ee3-255">ConditionForceEffect</span></span> | <span data-ttu-id="91ee3-256">Ein Effekt, der als Reaktion auf den aktuellen Sensor im Gerät unterschiedliche Kraft anwendet.</span><span class="sxs-lookup"><span data-stu-id="91ee3-256">An effect that applies variable force in response to current sensor within the device.</span></span> |
| <span data-ttu-id="91ee3-257">ConstantForceEffect</span><span class="sxs-lookup"><span data-stu-id="91ee3-257">ConstantForceEffect</span></span>  | <span data-ttu-id="91ee3-258">Ein Effekt, der eine konstante Kraft entlang eines Vektors anwendet.</span><span class="sxs-lookup"><span data-stu-id="91ee3-258">An effect that applies constant force along a vector.</span></span>                                  |
| <span data-ttu-id="91ee3-259">PeriodicForceEffect</span><span class="sxs-lookup"><span data-stu-id="91ee3-259">PeriodicForceEffect</span></span>  | <span data-ttu-id="91ee3-260">Ein Effekt, der entlang eines Vektors unterschiedliche Kraft anwendet, definiert durch eine Waveform.</span><span class="sxs-lookup"><span data-stu-id="91ee3-260">An effect that applies variable force defined by a waveform, along a vector.</span></span>           |
| <span data-ttu-id="91ee3-261">RampForceEffect</span><span class="sxs-lookup"><span data-stu-id="91ee3-261">RampForceEffect</span></span>      | <span data-ttu-id="91ee3-262">Ein Effekt, der eine linear zunehmende/abnehmende Kraft entlang eines Vektors anwendet.</span><span class="sxs-lookup"><span data-stu-id="91ee3-262">An effect that applies a linearly increasing/decreasing force along a vector.</span></span>          |

```cpp
using FFLoadEffectResult = ForceFeedback::ForceFeedbackLoadEffectResult;

auto effect = ref new Windows.Gaming::Input::ForceFeedback::ConstantForceEffect();
auto time = TimeSpan(10000);

effect->SetParameters(Windows::Foundation::Numerics::float3(1.0f, 0.0f, 0.0f), time);

// Here, we assume 'racingwheel' is valid and supports force feedback

IAsyncOperation<FFLoadEffectResult>^ request
    = racingwheel->WheelMotor->LoadEffectAsync(effect);

auto loadEffectTask = Concurrency::create_task(request);

loadEffectTask.then([this](FFLoadEffectResult result)
{
    if (FFLoadEffectResult::Succeeded == result)
    {
        // effect successfully loaded
    }
    else
    {
        // effect failed to load
    }
}).wait();
```

### <a name="using-force-feedback-effects"></a><span data-ttu-id="91ee3-263">Verwenden von Kraftrückmeldungseffekten</span><span class="sxs-lookup"><span data-stu-id="91ee3-263">Using force feedback effects</span></span>

<span data-ttu-id="91ee3-264">Nach dem Laden können alle Effekte synchron durch das Aufrufen von Funktionen in der Eigenschaft `WheelMotor` des Rennlenkrads oder einzeln durch das Aufrufen von Funktionen im Rückmeldungseffekt selbst gestartet, angehalten, fortgesetzt und gestoppt werden.</span><span class="sxs-lookup"><span data-stu-id="91ee3-264">Once loaded, effects can all be started, paused, resumed, and stopped synchronously by calling functions on the `WheelMotor` property of the racing wheel, or individually by calling functions on the feedback effect itself.</span></span> <span data-ttu-id="91ee3-265">In der Regel sollten Sie alle Effekte, die Sie verwenden möchten, vor Beginn des Spiels in das Rückmeldungsgerät laden und anschließend die jeweiligen `SetParameters`-Funktionen verwenden,, um die Effekte im Verlauf des Spiels zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="91ee3-265">Typically, you should load all the effects that you want to use onto the feedback device before gameplay begins and then use their respective `SetParameters` functions to update the effects as gameplay progresses.</span></span>

```cpp
if (ForceFeedbackEffectState::Running == effect->State)
{
    effect->Stop();
}
else
{
    effect->Start();
}
```

<span data-ttu-id="91ee3-266">Sie können das gesamte Kraftrückmeldungssystem auf einem bestimmten Rennlenkrad jederzeit asynchron aktivieren, deaktivieren oder zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="91ee3-266">Finally, you can asynchronously enable, disable, or reset the entire force feedback system on a particular racing wheel whenever you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="91ee3-267">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="91ee3-267">See also</span></span>

* [<span data-ttu-id="91ee3-268">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="91ee3-268">Windows.Gaming.Input.UINavigationController</span></span>][]
* [<span data-ttu-id="91ee3-269">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="91ee3-269">Windows.Gaming.Input.IGameController</span></span>][]
* [<span data-ttu-id="91ee3-270">Eingabemethoden für Spiele</span><span class="sxs-lookup"><span data-stu-id="91ee3-270">Input practices for games</span></span>](input-practices-for-games.md)

[<span data-ttu-id="91ee3-271">Windows.Gaming.Input</span><span class="sxs-lookup"><span data-stu-id="91ee3-271">Windows.Gaming.Input</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx
[<span data-ttu-id="91ee3-272">Windows.Gaming.Input.UINavigationController</span><span class="sxs-lookup"><span data-stu-id="91ee3-272">Windows.Gaming.Input.UINavigationController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.uinavigationcontroller.aspx
[<span data-ttu-id="91ee3-273">Windows.Gaming.Input.IGameController</span><span class="sxs-lookup"><span data-stu-id="91ee3-273">Windows.Gaming.Input.IGameController</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.igamecontroller.aspx
[<span data-ttu-id="91ee3-274">racingwheel</span><span class="sxs-lookup"><span data-stu-id="91ee3-274">racingwheel</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.aspx
[racingwheels]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheels.aspx
[racingwheeladded]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheeladded.aspx
[racingwheelremoved]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.racingwheelremoved.aspx
[<span data-ttu-id="91ee3-275">haspatternshifter</span><span class="sxs-lookup"><span data-stu-id="91ee3-275">haspatternshifter</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.haspatternshifter.aspx
[<span data-ttu-id="91ee3-276">hashandbrake</span><span class="sxs-lookup"><span data-stu-id="91ee3-276">hashandbrake</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.hashandbrake.aspx
[<span data-ttu-id="91ee3-277">hasclutch</span><span class="sxs-lookup"><span data-stu-id="91ee3-277">hasclutch</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.hasclutch.aspx
[<span data-ttu-id="91ee3-278">maxpatternshiftergear</span><span class="sxs-lookup"><span data-stu-id="91ee3-278">maxpatternshiftergear</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.maxpatternshiftergear.aspx
[maxwheelangle]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.maxwheelangle.aspx
[<span data-ttu-id="91ee3-279">getcurrentreading</span><span class="sxs-lookup"><span data-stu-id="91ee3-279">getcurrentreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.getcurrentreading.aspx
[<span data-ttu-id="91ee3-280">wheelmotor</span><span class="sxs-lookup"><span data-stu-id="91ee3-280">wheelmotor</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheel.wheelmotor.aspx
[<span data-ttu-id="91ee3-281">racingwheelreading</span><span class="sxs-lookup"><span data-stu-id="91ee3-281">racingwheelreading</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheelreading.aspx
[<span data-ttu-id="91ee3-282">racingwheelbuttons</span><span class="sxs-lookup"><span data-stu-id="91ee3-282">racingwheelbuttons</span></span>]: https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.racingwheelbuttons.aspx
